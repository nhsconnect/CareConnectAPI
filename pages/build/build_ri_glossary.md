---
title: Reference Implementation |  Install glossary
keywords: design, build, access, security, overview
tags: [design, overview]
sidebar: foundations_sidebar
permalink: build_ri_glossary.html
summary: "Provides a list of links for developers on the technologies used within the Reference Implementation"
---

{% include important.html content="All information provided below is indicative and subject to on-going review." %}

## Introduction
The Care Connect Reference Implementation (CCRI) is a web application that provides a working example of a FHIR Interface to key Care Connect profiles.  CCRI provides a public interface of FHIR, HAPI-FHIR, and JSON and has been implemented using Java and the Spring Framework with persistence provided by a MySQL database.

CCRI has been published as a set of Docker images which can be started as a set of containers to provide an example FHIR

Docker has been chosen as it provides an industry standard environment which can be run on a wide variety of platforms (Windows, MacOS, Linux, etc).  The Docker images can also be deployed on Cloud environments.

## Glossary overview
The instructions provide a technical introduction to the architecture of Care Connect Reference Implementation (CCRI).  The aim being to provide sufficient information so that the application can be downloaded and run in a local Docker environment.

The instructions are intended to be read alongside access to the source code for CCRI which can be found in GitHub at <http://github.com/nhsconnect/careconnect-reference-implementation>.  The application can be deployed from this source code or by installing the pre-packaged Docker images.  This reference implementation can be used either as a foundation for your own implementation of a FHIR API Service accessing information stored in a variety of repositories or just as a source of reference to understand how to develop a FHIR API Service.


## Glossary

The high level architectural view of the Reference Implementation.

<div style="text-align:center;"><img src="images/build/Tech_arch_R4.png" alt="High level architectural view" title="Technical view and docker containers" style="width:100%"></div>
<br>

|Term|Description|
|------|------|
|Docker| Docker is an open platform for developing, shipping, and running applications. It allows applications to be packaged into `images` which can then be downloaded and run on a variety of operating environments. See <https://www.docker.com/> |
|Docker Compose|  Tool for combining suites of docker containers to form an application.</br>Docker Compose is used to configure each of the services to be started and to define the relationship between the services.  See <https://docs.docker.com/compose/> |
|Elasticsearch|Elasticsearch is a distributed, RESTful search engine. We use it to store the details of the log messages & it provides a rich query and analytical engine to allow us to generate dashboards and track issues.  See <https://www.elastic.co/products>|
|ELK|The ELK Stack is an industry-standard combination of Elasticsearch, LogStash & Kibana (ELK) which together provides the ability to extract information from the log files to be stored in a database which can then be accessed via a browser to view the dashboards and search for information.  See <https://www.elastic.co/products> |
|FHIR|Fast Healthcare Interoperability Resources (FHIR) - specification for the interchange of healthcare data.  Provides an industry standard definition for the discovery and exchange of healthcare information using XML/JSON over a RESTful API.  See <http://hl7.org/implement/standards/fhir/>|
|FileBeat|Log file monitor which uploads the log records to LogStash.  See <https://www.elastic.co/products/beats/filebeat>|
|HAPI-FHIR|Open Source implementation of the FHIR specification which runs on a Java server.  This provides the REST interface to the underlying database and a web interface provided by the HAPI Overlay.</br>This implementation forms the base of CCRI.  See <http://hapifhir.io/>|
|Kibana|Provides a query and visualisation tool over the Elasticsearch repository.  This allows the creation of dashboards & alerts provide performance monitoring and the ability to perform adhoc queries against the captured logging information.  See <https://www.elastic.co/products/kibana>|
|LogStash|Pipeline to process the raw log entries before they are inserted into the Elasticsearch database.  This allows the log entries to be cleaned and augmented before being written to the database of log entries.  See <https://www.elastic.co/products/logstash]>|
|MySQL|A relational database that has been used to hold the data associated with the various record types in CCRI.  This acts as the core repository of the Patient, Medication, ... records.  Alternative databases can be used to supply the details of the various profiles by implementing the appropriate Data Access Object (DAOs) interfaces in a custom implementation of the FHIR Service.  See <https://www.mysql.com/>|




# Current Version #

{% include version.html %}

Check out [Versions](build_ri_version.html) for more information about the current released version, downloading options, use and future verions.


# Contribute #

This site is structured around Care Connect stakeholders including API users, developers and architects. Please get involved in the journey.

{% include custom/api_overview.svg %}

{% include custom/contribute.html content=""%}
