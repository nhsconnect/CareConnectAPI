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

If you are just after a FHIR Server you have several open source FHIR Servers options, all of these can be installed locally:

[Care Connect Reference Implementation](https://nhsconnect.github.io/CareConnectAPI/build_ri_install.html)

[HAPI FHIR JPA Server](http://hapifhir.io/doc_jpa.html)

[Firely Vonk](http://vonk.fire.ly/)

If you want to populate these servers with your own data then it becomes more complex. For HAPI and Vonk you can create FHIR resources and then POST them into the server. The Care Connect Reference Implementation (CCRI) can be used this way but its internal database structure is similar to many PAS and EPR systems. This allows the use of tools like Microsoft SQL Server Integration Service (SSIS) to import the data.

{% include note.html content="The CCRI uses Hibernate to connect to the MySQL database. Hibernate supports many database systems such as Microsoft SQL Server and Intersystems Cache, it has not been tested with these databases but in theory it should work." %}

Having to perform [extract, transform and load (ETL)](https://en.wikipedia.org/wiki/Extract,_transform,_load) is not ideal, the ETL stage can take time and the FHIR server will not be current. To get around this you can implement a FHIR Server to your existing datasource. This is what we did with the CCRI, we put a Care Connect FHIR API on top of our SQL database using a HAPI RESTful Server. This is detailed in the Design & Build->Reference Implementation section of this guide.

This is quite involved and to illustrate some of the key features in the CCRI we will show how to build a simple FHIR Server providing a FHIR Patient API with a MongoDb backend database.

## 2. Pre-Requisites ##

Install the following software:

*  	[Postman](https://www.getpostman.com/) - we will use this to add a FHIR Patient to the server and perform a few queries.
*   [Mongo](https://docs.mongodb.com/manual/installation) - accept the default installation (port 27017 with no security). If you have docker installed you can alternatively use the [Mongo image](https://hub.docker.com/_/mongo/) from docker instead. In addition you may wish to install [Mongo Compass](https://www.mongodb.com/products/compass) to explore the data.
*   Java IDE. Either:
    *    [Intellij Community](https://www.jetbrains.com/idea/download) (The screen shots below use Intellij)
    *    [Eclipse](http://www.eclipse.org/downloads/packages/eclipse-ide-java-developers/oxygen2)


## 3. Store Patient resource ##

Ensure the MongoDb has been started. In your browser navigate to the [Care Connect Examples project](https://github.com/nhsconnect/careconnect-examples), which contains the FHIRStarter module and then `Clone or download` the project.

<p style="text-align:center;"><img src="images/nosql/GitHub.PNG" style="width:90%;max-width: 90%;"></p>

Within your IDE (Intellij or Eclipse) import the project. On Intellij (windows) select File->New->Project from existing sources. On Eclipse see http://help.eclipse.org/kepler/index.jsp?topic=%2Forg.eclipse.platform.doc.user%2Ftasks%2Ftasks-importproject.htm

 <p style="text-align:center;"><img src="images/nosql/ImportProject.PNG" style="width:30%;max-width: 30%;"></p>

In the screenshot above we've chosen just to import the FHIRStarter project. On the next screen we imported the module as a Maven project and then accepted the defaults in the remaining screens.

On Intellij select spring-boot:run from the Maven Projects menu.

<p style="text-align:center;"><img src="images/nosql/SpringBootRun.PNG" style="width:100%;max-width: 100%;"></p>

For Eclipse, in eclipse Project Explorer, right click the project name -> select "Run As" -> "Maven Build..."
In the goals, enter `spring-boot:run` then click Run button.

A basic FHIR server will now be up and running. To confirm, start POSTMan and GET http://127.0.0.1:8183/STU3/metadata
You will see a FHIR ConformanceStatement returned from the server.

<p style="text-align:center;"><img src="images/nosql/POSTMANmeta.PNG" style="width:100%;max-width: 100%;"></p>

Looking at the return ConformanceStatement you will notice the server supports FHIR Patient and the Create operation.

```xml
      <resource>
           <type value="Patient"></type>
           <profile>
               <reference value="http://hl7.org/fhir/Profile/Patient"></reference>
           </profile>
           <interaction>
               <code value="read"></code>
           </interaction>
       </resource>
```

We will now add a Patient to our server. In POSTMAN the url is http://127.0.0.1:8183/STU3/Patient, the action is POST, under Headers add a `Content-Type` key with a value of `application/fhir+xml`. (If your example is in JSON format set the value to be 'application/fhir+json')

<div markdown="span" class="alert alert-success" role="alert">
POST http://127.0.0.1:8183/STU3/Patient</div>

<p style="text-align:center;"><img src="images/nosql/POSTMANpatientHeaders.PNG" style="width:50%;max-width: 50%;"></p>

Then copy a FHIR Patient into the Body section (We used Patient/1 from the CCRI server in the image below) and then click 'Send'.

<p style="text-align:center;"><img src="images/nosql/POSTMANpatientCreate.PNG" style="width:100%;max-width: 100%;"></p>

The response Status should be `201 Created` which indicates the Patient has been added to the server.

If you installed MongoDb Compass you will be able to view the Patient that was just added. You should notice the patient document is very similar to the FHIR Patient we posted into the database. It's not the same for two reasons, firstly MongoDb uses [BSON](https://en.wikipedia.org/wiki/BSON) although this is very similar to JSON it has a few differences. Secondly we've not just converted the XML/JSON FHIR Patient to BSON, we have used [Spring Data](https://projects.spring.io/spring-data-mongodb/) JPA Entities which will allow us to simplify the search operations will we add later.

<p style="text-align:center;"><img src="images/nosql/POSTMANpatientCompass.PNG" style="width:100%;max-width: 100%;"></p>

That is most of the installation and configuration completed. We have created a FHIR Server using a NoSQL Document database that supports FHIR Patient.


## 4. Retrieve Patient resource ##

We have mentioned the CCRI and this example project are using different database technologies, MongDb a NoSQL database rather than a MySQL a SQL database and also [Spring Data](https://projects.spring.io/spring-data-mongodb/) instead of [Hibernate ORM](http://hibernate.org/). The main reason is we wanted to simplify the description of the FHIR Server components used in the CCRI, both projects are composed in a similar way as shown in the diagram below:


<p style="text-align:center;"><img src="images/nosql/ccri-nosql.jpg" style="width:60%;max-width: 60%;"></p>

As can be seen the HAPI RESTful Server is common to both projects. The configuration of this server can be found in the `fhirStarterRestfulServer.java` shown in the diagram below, configuration is described on the [HAPI Server - REST Server](http://hapifhir.io/doc_rest_server.html) website. The highlighted section shows the PatientProvider which is used to tell the HAPI Server that we support Patient and also where the implementation is. This is also where you can add in security, set default the server to use XML or JSON as default and many other options.

{% include tip.html content="CCRI contains several FHIR Servers using a variety of different configurations including security ([SMART on FHIR](http://docs.smarthealthit.org/)) and interceptors." %}

<p style="text-align:center;"><img src="images/nosql/fhirStarterConfig.PNG" style="width:100%;max-width: 100%;"></p>

The Patient provider is where we configure the FHIR Patient behaviour. HAPI uses annotations to indicate what service the procedures provide. The procedure createPatient in the diagram is annotated with `@Create` which indicates it handles `POST` or create. This procedure then uses a PatientDAO class which uses Spring Data to store the Patient resource in the MongoDb. We will not be covering the DAO class as this is specific to the implementation but an example is provided for you to explore, this is the area where you would need to code your own implementation.

<p style="text-align:center;"><img src="images/nosql/patientProvider.PNG" style="width:100%;max-width: 100%;"></p>

We have now explained some of the workings of the demonstration and have a FHIR server which accepts FHIR Patient resources. Next we will add reading of the Patient resource. The DOA and code for `@Read` is provided, to enable this we need to stop the Server, uncomment the `@Read` procedure and restart the server (`mvn spring-boot:run`).

```java
/*
@Read
public Patient readPatient(HttpServletRequest request, @IdParam IdType internalId) {

    Patient patient = patientDao.read(ctx,internalId);

    return patient;
}
*/
```
Remove the comments.
```java
@Read
public Patient readPatient(HttpServletRequest request, @IdParam IdType internalId) {

    Patient patient = patientDao.read(ctx,internalId);

    return patient;
}
```

Once the server has restarted we can check the metadata to see the changes to the ConformanceStatement (use POSTMan).

<div markdown="span" class="alert alert-success" role="alert">
GET http://127.0.0.1:8183/STU3/metadata</div>

```xml
      <resource>
           <type value="Patient"></type>
           <profile>
               <reference value="http://hl7.org/fhir/Profile/Patient"></reference>
           </profile>
           <interaction>
               <code value="read"></code>
           </interaction>
           <interaction>
               <code value="create"></code>
           </interaction>
       </resource>
```
{% include note.html content="We have an error here. The profile being returned is the base FHIR Patient profile, for Care Connect this should be https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1 but we are using the default ConformanceStatement from the HAPI server. We do override this in the CCRI server." %}

To retrieve the Patient we first need to get the id of the Patient used in the MongoDb. In MongoDb this is the `_id`, which can be found either using MongoDb (see the earlier screenshot)

```json
_id : ObjectId("5ac47fd723598f6af80ff1fe")
```

or from the POST we did earlier in POSTMan in the Location header from POST response.

<p style="text-align:center;"><img src="images/nosql/POSTMANheaders.PNG" style="width:100%;max-width: 100%;"></p>

This gives us the following request in POSTMan

<div markdown="span" class="alert alert-success" role="alert">
GET http://127.0.0.1:8183/STU3/Patient/5ac47fd723598f6af80ff1fe</div>

The response is in JSON format but if we wanted XML we can use the `_format=xml` parameter, e.g.

<div markdown="span" class="alert alert-success" role="alert">
GET http://127.0.0.1:8183/STU3/Patient/5ac47fd723598f6af80ff1fe?_format=xml</div>

This is supported out of the box by the HAPI RESTful Server.


## 5. Search Patient resource ##

We have also provided a `@Search` method, locate plus uncomment this and restart the server.

```java
@Search
public List<Resource> searchPatient(HttpServletRequest request,
                                    @OptionalParam(name= Patient.SP_BIRTHDATE) DateRangeParam birthDate,
                                    @OptionalParam(name = Patient.SP_FAMILY) StringParam familyName,
                                    @OptionalParam(name= Patient.SP_GENDER) StringParam gender ,
                                    @OptionalParam(name= Patient.SP_GIVEN) StringParam givenName ,
                                    @OptionalParam(name = Patient.SP_IDENTIFIER) TokenParam identifier,
                                    @OptionalParam(name= Patient.SP_NAME) StringParam name
        , @OptionalParam(name = Patient.SP_RES_ID) TokenParam resid

) {
    List<Resource> results = patientDao.search(ctx,birthDate,familyName,gender,givenName,identifier,name);

    return results;
}
```

Accessing the ConformanceStatement statement now gives:

<div markdown="span" class="alert alert-success" role="alert">
GET http://127.0.0.1:8183/STU3/metadata?_format=xml</div>

```xml
<resource>
     <type value="Patient"></type>
     <profile>
         <reference value="http://hl7.org/fhir/Profile/Patient"></reference>
     </profile>
     <interaction>
         <code value="read"></code>
     </interaction>
     <interaction>
         <code value="create"></code>
     </interaction>
     <interaction>
         <code value="search-type"></code>
     </interaction>
     <searchParam>
         <name value="_id"></name>
         <type value="token"></type>
         <documentation value="The ID of the resource"></documentation>
     </searchParam>
     <searchParam>
         <name value="birthdate"></name>
         <type value="date"></type>
         <documentation value="The patient's date of birth"></documentation>
     </searchParam>
     <searchParam>
         <name value="family"></name>
         <type value="string"></type>
         <documentation value="A portion of the family name of the patient"></documentation>
     </searchParam>
     <searchParam>
         <name value="gender"></name>
         <type value="string"></type>
         <documentation value="Gender of the patient"></documentation>
     </searchParam>
     <searchParam>
         <name value="given"></name>
         <type value="string"></type>
         <documentation value="A portion of the given name of the patient"></documentation>
     </searchParam>
     <searchParam>
         <name value="identifier"></name>
         <type value="token"></type>
         <documentation value="A patient identifier"></documentation>
     </searchParam>
     <searchParam>
         <name value="name"></name>
         <type value="string"></type>
         <documentation value="A server defined search that may match any of the string fields in the HumanName, including family, give, prefix, suffix, suffix, and/or text"></documentation>
     </searchParam>
 </resource>
```

You will notice that all the `@OptionalParam` have become searchParam's in the ConformanceStatement. We have only included the mandatory search parameters from the [CareConnectAPI](api_entity_patient.html#21-search-parameters). HAPI has built in support for all standard parameters, see below:

<p style="text-align:center;"><img src="images/nosql/OtherSearchOptions.png" style="width:80%;max-width: 80%;"></p>

Patient searches are now supported, for example to search for Patients on NHS Number we could do:

<div markdown="span" class="alert alert-success" role="alert">
GET http://127.0.0.1:8183/STU3/Patient?identifier=https://fhir.nhs.uk/Id/nhs-number|9876543210</div>

This has been an overview of the HAPI RESTful server and was kept basic in order to show key aspects. A more detailed version of this project can be found in [careconnect-document](https://github.com/nhsconnect/careconnect-document/tree/master/ccri-document-server) which is a basic repository for storing FHIR Documents, the Patient element provides a Patient index complemented with a document index, the documents are stored as raw FHIR Bundles.   
