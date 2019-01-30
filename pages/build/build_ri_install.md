---
title: CCRI | Installation instructions
keywords: design, build, access, security, overview
tags: [design, overview]
sidebar: foundations_sidebar
permalink: build_ri_install.html
summary: "Reference Implementation installation instructions"
---

{% include important.html content="All information provided below is indicative and subject to on-going review." %}

# Installation instructions #
This document is intended to provide a technical introduction to the architecture of CCRI.  It aims to provide sufficient information so that the application can be downloaded and run in a local Docker environment.

### Prerequisites

1. Installation of Docker & Docker Compose.
1. Creation of a docker-compose file.  
Sample `docker-compose` files is below.  
1. Definition of environment variables
1. Upload Sample Data

These instructions have been tested on Apple Mac Mojave and Windows 10. On Windows 10 ensure you are using:

1. Docker: Version 18.06.1-ce or above
1. Docker Compose: Version 1.22.0 or above

This is an example of the `docker-compose.yml` file which defines several services in the core CCRI application.


`docker-compose.yml`
```YAML
version: '2.1'
services:

# Care Connect Query API

  ccrisql:
    container_name: ccrisql
    image: thorlogic/ccri-sql${IMAGE_TAG}
    environment:
     - POSTGRES_DB=careconnect
     - POSTGRES_USER=${MYSQL_DB_USER}
     - POSTGRES_PASSWORD=${MYSQL_DB_PASSWORD}
    ports:
     - 5434:5432
    networks:
     - ccri_net

  ccriserver:
    container_name: ccriserver
    image: thorlogic/ccri-fhirserver${IMAGE_TAG}
    depends_on:
      - ccrisql
    links:
      - ccrisql
    environment:
      - datasource.username=${MYSQL_DB_USER}
      - datasource.password=${MYSQL_DB_PASSWORD}
      - datasource.host=//ccrisql
      - datasource.driver=org.postgresql.Driver
      - datasource.path=5432/careconnect
      - datasource.vendor=postgresql
      - datasource.showSql=false
      - datasource.showDdl=false
      - datasource.cleardown.cron=0 19 21 * * *
      - datasource.dialect=org.hibernate.dialect.PostgreSQL9Dialect
      - ccri.implementation.description=Care Connect Reference Implementation
      - ccri.software.version=3.7.1
      - ccri.software.name=CCRI-Server
      - ccri.server=Care Connect API (unsecured)
      - ccri.server.base=http://${FHIR_SERVER_BASE_HOST}/ccri-fhir/STU3
      - ccri.guide=https://nhsconnect.github.io/CareConnectAPI/
      - ccri.CRUD_create=true
      - ccri.oauth2=false
    ports:
      - 8186:8186
    extra_hosts:
      # Define an alias to loop back for REST Connections
      - "${FHIR_SERVER_BASE_HOST}:127.0.0.1"
    volumes:
      - tomcat-log-volume:/usr/local/tomcat/logs
    networks:
      - ccri_net

# Data Load imports a set of sample data into the reference implementation (optional)

  ccridataload:
    container_name: ccridataload
    image: thorlogic/ccri-dataload${IMAGE_TAG}
    depends_on:
    - ccriserver
    environment:
    - FHIR_SERVER=http://ccriserver:8186/ccri-fhir/STU3
    - POSTGRES_JDBC=postgresql://ccrisql:5432/careconnect
    - POSTGRES_USER=${MYSQL_DB_USER}
    - POSTGRES_USERNAME=${MYSQL_DB_USER}
    - POSTGRES_PASSWORD=${MYSQL_DB_PASSWORD}
    networks:
    - ccri_net

# Care Connect (Unstructured) Document API implementation

  ccrimongo:
      container_name: ccrimongo
      image: mongo:4.0.3
      ports:
        - 27107:27107
      networks:
        - ccri_net

  ccridocument:
     container_name: ccridocument
     image: thorlogic/ccri-document${IMAGE_TAG}
     depends_on:
       - ccrimongo
     links:
       - ccrimongo
     environment:
       - ccri.server.base=https://data.developer.nhs.uk/ccri-document/STU3
       - ccri.software.version=3.7.1
       - ccri.software.name=CCRI Document
       - ccri.server=CCRI Document FHIR Server
       - ccri.validate_flag=false
       - ccri.guide=https://nhsconnect.github.io/CareConnectAPI/
       - spring.data.mongodb.uri=mongodb://ccrimongo:27017/careconnect-nosql
       - spring.data.mongodb.database=careconnect-nosql
     ports:
       - 8181:8181
     volumes:
       - mongo-log-volume:/usr/local/tomcat/logs
     networks:
       - ccri_net

# Care Connect Get Record API and Transfer of Care Endpoint

  ccrimessaging:
    container_name: ccrimessaging
    image: thorlogic/ccri-messaging${IMAGE_TAG}
    depends_on:
    - ccriserver
    environment:
    - ccri.server.base=http://data.developer.nhs.uk/ccri-messaging/STU3
    - ccri.edms.server.base=http://localhost:8181/ccri-document/STU3
    - ccri.software.version=3.7
    - ccri.software.name=CCRI Messaging
    - ccri.server=CCRI Messaging FHIR Server
    - ccri.validate_flag=false
    - ccri.guide=https://nhsconnect.github.io/CareConnectAPI/
    - fhir.restserver.eprBase=http4://ccriserver:8186/ccri-fhir/STU3?throwExceptionOnFailure=false&bridgeEndpoint=true
    - fhir.restserver.edmsBase=http4://ccridocument:8181/ccri-document/STU3?throwExceptionOnFailure=false&bridgeEndpoint=true
    - fhir.restserver.tkwBase=http4://192.168.128.36?throwExceptionOnFailure=true&bridgeEndpoint=true
    - org.slf4j.simpleLogger.defaultLogLevel=info
    ports:
    - 8182:8182
    volumes:
    - tie-log-volume:/usr/local/tomcat/logs
    networks:
      - ccri_net

# App to allow keycloak login to the apps
  logon:
    container_name: ccrilogon
    image: thorlogic/ccri-logon${IMAGE_TAG}
    ports:
      - 4200:4200

# Renders (Transfer Of Care) FHIR Documents and provides a FHIR document import

  documentviewer:
    container_name: ccridocumentviewer
    image: thorlogic/ccri-documentviewer${IMAGE_TAG}
    environment:
    - fhir.resource.serverBase=http://localhost:8186/ccri-fhir/STU3
    - fhir.messaging.serverBase=http://localhost:8182/ccri-messaging/STU3
    depends_on:
    - ccriserver
    - ccrimessaging
    ports:
    - 8080:4201
    extra_hosts:
    # Define an alias to the CCRI Container to ensure that the correct Server Base is displayed by HAPI
    - "${FHIR_SERVER_BASE_HOST}:172.168.250.14"
    networks:
    - ccri_net

# provides technical demonstration of the Care Connect API

  fhirexplorer:
    container_name: fhirexplorer
    image: thorlogic/ccri-fhirexplorer${IMAGE_TAG}
    environment:
      - fhir.resource.serverBase=http://localhost:8186/ccri-fhir/STU3
      - fhir.messaging.serverBase=http://localhost:8182/ccri-messaging/STU3
    depends_on:
      - ccriserver
    ports:
      - 8081:8188
    extra_hosts:
      # Define an alias to the CCRI Container to ensure that the correct Server Base is displayed by HAPI
      - "${FHIR_SERVER_BASE_HOST}:172.168.250.14"
    networks:
      - ccri_net

volumes:
  tomcat-log-volume:
  tie-log-volume:
  mongo-log-volume:
  sqlvol:

networks:
  ccri_net:
    driver: bridge



```

### Installation of Docker & Docker Compose

Follow the instructions for the appropriate operating system on https://docs.docker.com/engine/installation/ to install Docker (minimum version 17.06.0) on the computer which will act as the CCRI Server.  Docker Community Edition (CE) is sufficient for our requirements.  

Docker Compose will be automatically installed as part of Docker for Mac, and Docker for Windows.  Docker Compose will need to be installed independently on Linux, (see https://docs.docker.com/compose/install/ )


##### Install Docker Compose on Linux
```Bash
# Install Docker Compose on Linux
sudo curl -L https://github.com/docker/compose/releases/download/1.17.0/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
```

##### Check Installation of Docker & Docker Compose
```Bash
# Check that docker is installed
docker --version
docker-compose --version
```
```
Docker version 17.09.0-ce, build afdb6d4
docker-compose version 1.16.1, build 6d1ac21
```
Ensure that the reported Docker version is 17.06+ and that the Docker Compose version is 1.14+

### Creation of Service Definitions
Create a new folder that will be the home directory for the CCRI Server installation, e.g. `ccri-server`.  All subsequent instructions will be applied in this folder.

```Bash
mkdir ccri-server
cd ccri-server
```

In this folder we will need to create the following files:
* `docker-compose.yml` - the definition of the services which form the core of the CCRI Server application.
* `.env` - A configuration file which contains the environment settings specific to the installation.  These environment settings can be used to override the defaults defined in the `docker-compose` files.


### Define Environment Variables
Edit the `.env` file to define the environment specific properties. Previous versions of the CCRI used MySql, the current PostgreSql version reuses the same environment variables.

Example `.env` file:
```Ini
IMAGE_TAG=:latest
FHIR_SERVER_BASE_HOST=localhost
MYSQL_DB_USER=fhirjpa
MYSQL_DB_PASSWORD=fhirjpa
```

The name of the FHIR_SERVER_BASE_HOST will be the host and domain that will be used to access the FHIR Gateway Server. The client applications/browsers who access the FHIR Gateway must be able to resolve this address and so it should be added to the client's host file if this is not a public address.

`\etc\hosts`
```
##
# Host Database
#
# localhost is used to configure the loopback interface
# when the system is booting.  Do not change this entry.
##
127.0.0.1       test.myserver.nhs.uk
```


### Starting the CCRI Application

For the command line in the root folder (e.g. `ccri-server`) of your installation:

```Bash
# Start CCRI Services
docker-compose up -d
```

```Bash
# Restart the CCRI Server
docker-compose restart
```


(See Administration Scripts for more information)

### Load Sample data

A small set of sample data is provided.


## Sample Docker Compose Files
### Docker Compose File for CCRI

The Docker Compose file for CCRI defines the following services:-
<br>
<br>
Core FHIR Server Functionality
<br>
<br>
* **ccriserver** - The core CCRI FHIR Server which simulates an Electronic Patient Record (EPR)
* **ccridataload** - This loads a set of sample data into the CCRI FHIR Server
* **ccrisql** - The PostgreSql database which provides the data persistence for the FHIR Resources.

<br>
Additional FHIR Server (document storage) - Optional
<br>
<br>
* **ccridocument** - A FHIR Server simulating an Electronic Document Management System (EDMS)
* **ccrimongo** - A MongoDb which provides persistence for FHIR Documents and traditional documents (e.g. PDF)

<br>
Other FHIR components - Optional
<br>
<br>
* **fhirexplorer** - FHIR Explorer application which provides access to the CCRI FHIR Server via a user interface.
* **documentviewer** - Application that provides 'Transfer of Care' FHIR Document rendering.
* **ccrimessaging** - This provides support for extended operations and support for FHIR Messaging.
<br>
<br>



<table style="min-width:100%;width:100%">

    <tr id="clinical">
        <th style="width:15%;">Service</th>
        <th style="width:15%;">Type</th>
        <th style="width:40%;">Base access URL</th>
    </tr>
    <tr>
        <td>ccriserver</td>
        <td>FHIR Server</td>
        <td>http://127.0.0.1:8186/ccri-fhir/STU3/</td>    
    </tr>
    <tr>
        <td>ccrimessaging</td>
        <td>FHIR Server</td>
        <td>http://127.0.0.1:8182/ccri-messaging/STU3/</td>    
    </tr>
    <tr>
        <td>ccridocument</td>
        <td>FHIR Server</td>
        <td>http://127.0.0.1:8181/ccri-document/STU3/</td>    
    </tr>
    <tr>
        <td>fhirexplorer</td>
        <td>FHIR Explorer Application</td>
        <td>http://127.0.0.1:8081/ccri/</td>    
    </tr>
    <tr>
        <td>documentviewer</td>
        <td>FHIR Document Viewer Application</td>
        <td>http://127.0.0.1:8080/document-viewer/</td>    
    </tr>
</table>


## Administration Scripts

#### Start Server
`startServer.sh`
```Bash
#!/usr/bin/env bash
docker-compose up -d
```


#### Stop Server
`stopServer.sh`
```Bash
#!/usr/bin/env bash
docker-compose -f docker-compose.yml stop
```

#### View Details of Running Docker Containers
`serverStatus.sh`
```Bash
#!/usr/bin/env bash
docker-compose -f docker-compose.yml ps
```

#### View the Logs for the CCRI Service
```Bash
#!/usr/bin/env bash
docker-compose logs ccriserver
```


# Current Version #

{% include version.html %}

Check out [Versions](build_ri_version.html) for more information about the current released version, downloading options, use and future verions.


# Contribute #

This site is structured around Care Connect stakeholders including API users, developers and architects. Please get involved in the journey.

{% include custom/api_overview.svg %}

{% include custom/contribute.html content=""%}
