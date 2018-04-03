---
title: Design | Patient Server
keywords: development
tags: [design,development]
sidebar: overview_sidebar
permalink: build_patient_server.html
summary: "How to create a basic FHIR Patient server using open source"
---

{% include custom/search.warnbanner.html %}

## 1. Overview ##

Initially you’ll more than likely want to explore FHIR. You have several open source FHIR Servers options, all of these can be installed locally:

HAPI FHIR JPA Server - http://hapifhir.io/doc_jpa.html

Firely - http://vonk.fire.ly/

Care Connect Reference Implementation - https://nhsconnect.github.io/CareConnectAPI/build_ri_install.html


The next stage is to configure your own server. You could reuse CCRI as it’s internal SQL  structure is similar to a number of PAS and EPR systems in common use today but this would mean keeping PAS/EPR and separate FHIR server in step.

What you would probably want to do instead is build a FHIR API on top of your EPR/PAS. This is what we did with the CCRI, we put a Care Connect FHIR API on top of our SQL database.

Marko will be covering this next but in this section I will demonstrate the basics of how we built the FHIR server.


## 2. Store Patient resource ##

For this I have already downloaded and installed a default instance of MongoDb. [Show mongo + compass]. Next on github I will download the fhirStarter package. [https://github.com/nhsconnect/careconnect-examples].

Open up this repo in my IDE, I’m using Intellij Ultimate for this but the steps on the community version are similar. [Import project]
Now I select [mvn spring-boot:run]

4.

Now we have a FHIR Server up and running. We can see the conformance statement [POSTMan  http://127.0.0.1:8183/STU3/metadata]


5.  Add Patient (POST)

We have a conformance statement but it’s not serving any resources.

To do this we need to configure the HAPI Restful server which is in the fhirStarterRestfulServer
Class. This is where you can add in security, set default the server to use XML or JSON as defaults. More details are on the hapi fhir site.

For demonstration purposes I’ve already created a Patient provider and will add that to the server [uncomment line and restart server]

Going back to postman we can now see the changes to the conformance statement [show] and post in a Patient resource [use ccri and show also show mongo database]


## 3. Retrieve Patient resource ##

How do we retrieve? [Uncomment the read section and do get call within postman. Change Accept to xml/json. Mention this is all built in]

## 4. Search Patient resource ##

How do we do a search? [explain PatientProvider search options. Uncomment section, build another option]
