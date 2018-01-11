---
title: Reference Implementation | Installation instructions of RI
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
Sample `docker-compose` files are shown in [Administration Scripts].  
1. Definition of environment variables
1. Upload Sample Data


### Installation of Docker & Docker Compose

Follow the instructions for the appropriate operating system on https://docs.docker.com/engine/installation/ to install Docker (minimum version 17.06.0) on the computer which will act as the CCRI Server.  Docker Community Edition (CE) is sufficient for our requirements.  

Docker Compose will be automatically installed as part of Docker for Mac, and Docker for Windows.  Docker Compose will needed to be installed independently on Linux, (see https://docs.docker.com/compose/install/ )


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
* `docker-compose.yaml` - the definition of the services which form the core of the CCRI Server application.
* `docker-compose-elk.yaml` (optional) - This file defines the services which provide the log searching and monitoring using the ELK Stack.  This is only required if you are intending to view the activity on the server using Kibana.
* `.env` - A configuration file which contains the environment settings specific to the installation.  These environment settings can be used to override the defaults defined in the `docker-compose` files.


### Define Environment Variables
Edit the `.env` file to define the environment specific properties.

Example `.env` file:
```Ini
CRRI_VERSION=latest
FHIR_SERVER_BASE_HOST=test.myserver.nhs.uk
MYSQL_DB_USER=fhirjpa
MYSQL_DB_PASSWORD=fhirjpa
ELASTIC_SEARCH_USER=elasticsearch
ELASTIC_SEARCH_PASSWORD=changeme
```

NB - The details of the Elasticsearch User & Password are only required in the ELK Stack is being deployed.

The name of the FHIR_SERVER_BASE_HOST will be be the host & domain which will be used to access the FHIR Gateway Server.  The client applications/browsers who access the FHIR Gateway must be able to resolve this address and so it should be added to the client's host file if this is not a public address.

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

Note: There is a known issue which may cause the CCRI Server to fail to start on the first attempt.  The MySQL service will takes a considerable amount of time (~1 min) to initialise it's database the first time that it is started and this will prevent the CCRI Server making a connection to the database.  This can be resolved by either restarting all the services or by just restarting the CCRI Server once the MySQL database has been initialised.

```Bash
# Restart the CCRI Server
docker-compose restart ccri
```


(See Administration Scripts for more information)

### Load Sample data
The sample data which has been used to populate the database can be requested from <apilabs@nhs.uk>

## Installation of Sample Log Monitoring (Optional)
The ELK Monitoring stack is defined in the `docker-compose-elk.yaml` file, this is an optional part of the installation and alternative log monitoring can be utilised.

### ELK, Logstash & Kibana (ELK) Stack
1. ELK - Supplied by the `sebp/elk` Docker Image
We are using a single Docker image which combines Elasticsearch, Logstash, & Kibana into a single image.  This can be configured via the docker compose file and external configuration files.  For example, we are configuring the Logstash filters which parse the incoming log lines, extract specific fields and add additional tags.
2. FileBeat
Filebeat is used to collect the lines from the physical log files and then forward them to Logstash so that they can be parsed.  Filebeat's connection to the log files is the only physical connection between the 2 modules.


## Sample Docker Compose Files
### Docker Compose File for CCRI

The Docker Compose file for CCRI defines the following services:-
* ccri - The CCRI Server
* ccrigateway - The Gateway provides the public facing interface of the CCRI application.  It provides a HAPI-FHIR web interface and a REST interface.
* ccrisql - The MySQL database which provides the data persistence for the FHIR Profiles.  This is only sample data to provide

This is an example of the `docker-compose.yaml` file which defines the 3 services in the core CCRI application.


`docker-compose.yaml`
```YAML
version: '3'
services:
  ccri:
    container_name: ccri
    build: ccri-fhirserver
    image: thorlogic/ccri-fhirserver:${CRRI_VERSION}
    depends_on:
      - ccrisql
    links:
      - ccrisql
    environment:
      - datasource.username=${MYSQL_DB_USER}
      - datasource.password=${MYSQL_DB_PASSWORD}
      - datasource.host=//ccrisql
      - datasource.driver=com.mysql.jdbc.Driver
      - datasource.path=3306/careconnect?autoReconnect=true
      - datasource.vendor=mysql
      - datasource.showSql=true
      - datasource.showDdl=true
      - datasource.cleardown.cron=0 19 21 * * *
      - datasource.dialect=org.hibernate.dialect.MySQL57Dialect
      - datasource.ui.serverBase=http://${FHIR_SERVER_BASE_HOST}/careconnect-ri/STU3
      - datasource.serverBase=http://${FHIR_SERVER_BASE_HOST}/careconnect-ri/STU3
    ports:
      - 8080:8080
    extra_hosts:
      # Define an alias to loop back for REST Connections
      - "${FHIR_SERVER_BASE_HOST}:127.0.0.1"
    volumes:
      - tomcat-log-volume:/usr/local/tomcat/logs
    networks:
      ccri_net:
        ipv4_address: 172.168.240.10

  ccrisql:
    container_name: ccrisql
    image: mysql:5.7.20
    environment:
      - MYSQL_ROOT_PASSWORD=mypassword
      - MYSQL_DATABASE=careconnect
      - MYSQL_USER=${MYSQL_DB_USER}
      - MYSQL_PASSWORD=${MYSQL_DB_PASSWORD}
    ports:
      - 43306:3306
    networks:
      - ccri_net
    command: mysqld --character-set-server=utf8 --collation-server=utf8_bin --innodb_lock_wait_timeout=300 --transaction-isolation=READ-UNCOMMITTED
    healthcheck:
      test: ["CMD", "mysqladmin" ,"ping", "-h", "localhost"]
      timeout: 20s
      retries: 10

  ccrigateway:
    container_name: ccrigateway
    build: ccri-fhirgateway
    image: thorlogic/ccri-fhirgateway:${CRRI_VERSION}
    environment:
      - datasource.ui.serverBase=http://${FHIR_SERVER_BASE_HOST}/careconnect-ri/STU3
      - fhir.resource.serverBase=http://${FHIR_SERVER_BASE_HOST}/careconnect-ri/STU3
      - fhir.restserver.serverBase=http4://${FHIR_SERVER_BASE_HOST}/careconnect-ri/STU3?throwExceptionOnFailure=false&bridgeEndpoint=true
    depends_on:
      - ccri
    ports:
      - 80:80
    extra_hosts:
      # Define an alias to the CCRI Container to ensure that the correct Server Base is displayed by HAPI
      - "${FHIR_SERVER_BASE_HOST}:172.168.240.10"
    volumes:
      - gateway-log-volume:/usr/local/tomcat/logs
    networks:
      - ccri_net

volumes:
  tomcat-log-volume:
  gateway-log-volume:

networks:
  ccri_net:
    driver: bridge
    ipam:
      driver: default
      config:
      - subnet: 172.168.240.0/24

```

### Docker Compose File for Sample Log Monitoring

`docker-compose-elk.yaml`
```YAML
version: '3'
services:
  elk:
    image: sebp/elk:562
    volumes:
      - ./elk/logstash/conf/20-filter.conf:/etc/logstash/conf.d/20-filter.conf:ro
    ports:
      - "5601:5601"
      - "9200:9200"
      - "5044:5044"
    networks:
      - elknet

  filebeat:
    image: docker.elastic.co/beats/filebeat:5.6.2
    volumes:
      - tomcat-log-volume:/var/log/tomcat:ro
      - gateway-log-volume:/var/log/gateway:ro
      - ./filebeat/filebeat.yml:/usr/share/filebeat/filebeat.yml:ro
      - ./elk/certs/logstash-beats.crt:/etc/pki/tls/certs/logstash-beats.crt:ro
    depends_on:
      - elk
    links:
      - elk
    networks:
      - elknet

  nginx:
    image: nginx
    depends_on:
      - elk
    volumes:
      - ./nginx/conf.d/default.conf:/etc/nginx/conf.d/default.conf:ro
      - ./nginx/conf.d/.htpasswd:/etc/nginx/.htpasswd:ro
    ports:
      - 20001:20001
    networks:
      - elknet

volumes:
  tomcat-log-volume:
  gateway-log-volume:

networks:
  elknet:
    driver: bridge

```

## Administration Scripts

#### Start Server
`startServer.sh`
```Bash
#!/usr/bin/env bash
docker-compose up -d
```

#### Start Server with ELK Log Monitoring
`startServerWithElk.sh`
```Bash
#!/usr/bin/env bash
docker-compose -f docker-compose.yml -f docker-compose-elk.yml start
```

#### Stop Server
`stopServer.sh`
```Bash
#!/usr/bin/env bash
docker-compose -f docker-compose.yml -f docker-compose-elk.yml stop
```

#### View Details of Running Docker Containers
`serverStatus.sh`
```Bash
#!/usr/bin/env bash
docker-compose -f docker-compose.yml -f docker-compose-elk.yml ps
```

#### View the Logs for the CCRI Service
```Bash
#!/usr/bin/env bash
docker-compose logs ccri
```


# Current Version #

{% include version.html version="3" function="Provide 14 STU3 (PractionerRole added in STU3) Care Connect profiles with example data for one care setting with audit of use and accessible by unsecure API interaction
" deliver="8th December 2017" %}

Check out [Versions](build_ri_version.html) for more information about the current released version, downloading options, use and future verions.


# Contribute #

This site is structured around Care Connect stakeholders including API users, developers and architects. Please get involved in the journey.

{% include custom/api_overview.svg %}

{% include custom/contribute.html content=""%}
