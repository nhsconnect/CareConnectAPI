---
title: Design | Patient Search
keywords: development
tags: [design,development]
sidebar: overview_sidebar
permalink: design_patient_search.html
summary: "How to use FHIR Patient resources to perform Patient Searches"
---

{% include custom/search.warnbanner.html %}

{% include custom/ihe.reference.html apicontent="[Patient](restfulapis_identification_patient.html) <br>  [Practitioner](restfulapis_identification_practitioner.html) <br> [Organization](restfulapis_identification_organisation.html) "  ihecontent="[IHE Patient Demographic Query Mobile (IHE PDQM)](http://www.ihe.net/uploadedFiles/Documents/ITI/IHE_ITI_Suppl_PDQm.pdf)"  patterncontent="[Shared Repository](https://developer.nhs.uk/library/architecture/integration-patterns/shared-repository/)" %}

## 1. Overview ##

{% include custom/usecase.html content="A patient visits a emergency department for the first time. The nurse needs to register the patient; in
doing so, it is desired to record the patient’s demographic data in the emergency departments management
information system (ED MIS). The emergency department is connected to a hospital trust’s central
patient registry (typically the Patient Administration System (PAS) or Master Patient Index (MPI)). <br><br>  The nurse issues a patient query request to the central patient registry acting as a
Patient Demographics Supplier, with some basic patient demographics data as search criteria. In the returned patient list, she picks an appropriate record for the patient, including the hospital’s
Patient ID, to enter into the ED MIS. (Note the ED MIS uses a different Patient ID domain than that
of the central patient registry.)" %}

Most NHS trusts will typically have one central system  called the Patient Administration System (PAS) thats holds a master Patient registry of all patients who have had care with the trust. In order to reduce patient administration and improve data quality, all  other MIS within the trusts will be kept in sync with the central registry (PAS) via HL7v2 [messaging](http://www.enterpriseintegrationpatterns.com/patterns/messaging/Messaging.html). Alongside these messages will be patient encounter messages as shown in the diagram below:

{% include image.html
max-width="200px" file="IHE/Iti_pam_ip.jpg" alt="Patient Identity Feeds"
caption="Patient Identity Feeds" %}

HL7v2 is a mature and widely used standard but it is not suitable for querying patient demographic details (see HL7v2 Patient Demographics Query below). Mostly because it is a messaging standard and not an API. Care Connect API gives an API using [RESTful](https://en.wikipedia.org/wiki/Representational_state_transfer) interface following a {% include custom/patterns.inline.html content="[resource API pattern](http://www.servicedesignpatterns.com/WebServiceAPIStyles/ResourceAPI)" %} to provide access to the central Patient repository.
This is particularly suited to:
* A health portal securely exposing demographics data to browser based plugins
* Medical devices which need to access patient demographic information
* Mobile devices used by physicians (example bedside eCharts) which need to establish
patient context by scanning a bracelet
* Web based EPR/EHR applications which wish to provide dynamic updates of patient
demographic information such as a non-postback search, additional demographic detail,
etc.
* Any low resource application which exposes patient demographic search functionality
* A facade providing a simple API to a complex interface

## 2. Client Patient Search ##

### 2.1 Foundation ###

{% include image.html
max-width="200px" file="design/PDQ Actor Diagram.jpg" alt="Patient Search FHIR Actor Diagram"
caption="Patient Search FHIR Actor Diagram" %}

The patient search can use any of the search parameters defined in the [Patient](restfulapis_identification_patient.html) API. For example if the patient informs the nurse of their date of birth, first name (19th Mar 1998 Bernie Kanfeld) and surname the query would be.

```
GET http://[baseUrl]/Patient?birthdate=1998-03-19&name=bernie%20kanfeld
```

`[baseUrl]` needs to be replaced with an actual url, in the example below this is `http://127.0.0.1:8181/Dstu2/`. The url would work within a web browser but a better tool to work with RESTful is [Postman](https://www.getpostman.com/)

```
http://127.0.0.1:8181/Dstu2/Patient?birthdate=1998-03-19&name=bernie%20kanfeld
```

A sample response is shown below

#### XML Example 1 - Bundle Patient ####

```xml
<Bundle xmlns="http://hl7.org/fhir">
    <id value="e25d430b-e238-44a3-95cb-2c048496a448"/>
    <meta>
        <lastUpdated value="2017-06-02T15:18:24.874+01:00"/>
    </meta>
    <type value="searchset"/>
    <total value="1"/>
    <link>
        <relation value="self"/>
        <url value="[baseUrl]/Patient?birthdate=1998-03-19&amp;name=bernie%20kanfeld"/>
    </link>
    <entry>
        <fullUrl value="[baseUrl]/Patient/24966"/>
        <resource>
            <Patient xmlns="http://hl7.org/fhir">
                <id value="24966"/>
                <meta>
                    <lastUpdated value="2017-06-02T09:30:21.875+01:00"/>
                    <profile value="https://fhir.hl7.org.uk/StructureDefinition/CareConnect-Patient-1"/>
                </meta>
                <extension url="https://fhir.hl7.org.uk/StructureDefinition/Extension-CareConnect-EthnicCategory-1">
                    <valueCodeableConcept>
                        <coding>
                            <system value="https://fhir.hl7.org.uk/CareConnect-EthnicCategory-1"/>
                            <code value="01"/>
                            <display value="British, Mixed British"/>
                        </coding>
                    </valueCodeableConcept>
                </extension>
                <identifier>
                    <extension url="https://fhir.hl7.org.uk/StructureDefinition/Extension-CareConnect-NHSNumberVerificationStatus-1">
                        <valueCodeableConcept>
                            <coding>
                                <system value="https://fhir.hl7.org.uk/CareConnect-NHSNumberVerificationStatus-1"/>
                                <code value="01"/>
                                <display value="Number present and verified"/>
                            </coding>
                        </valueCodeableConcept>
                    </extension>
                    <system value="https://fhir.nhs.uk/Id/nhs-number"/>
                    <value value="9876543210"/>
                </identifier>
                <identifier>
                    <system value="https://fhir.jorvik.nhs.uk/PAS/Patient"/>
                    <value value="123345"/>
                </identifier>
                <active value="true"/>
                <name>
                    <use value="usual"/>
                    <family value="Kanfeld"/>
                    <given value="Bernie"/>
                    <prefix value="Miss"/>
                </name>
                <gender value="female"/>
                <birthDate value="1998-03-19"/>
                <address>
                    <use value="home"/>
                    <line value="10, Field Jardin"/>
                    <line value="Long Eaton"/>
                    <city value="Nottingham"/>
                    <postalCode value="NG10 1ZZ"/>
                </address>
                <maritalStatus>
                    <coding>
                        <system value="http://hl7.org/fhir/v3/MaritalStatus"/>
                        <code value="S"/>
                        <display value="Never Married"/>
                    </coding>
                </maritalStatus>
                <careProvider>
                    <reference value="Practitioner/24967"/>
                    <display value="Dr AA Bhatia"/>
                </careProvider>
                <managingOrganization>
                    <reference value="Organization/24965"/>
                    <display value="Moir Medical Centre"/>
                </managingOrganization>
            </Patient>
        </resource>
        <search>
            <mode value="match"/>
        </search>
    </entry>
</Bundle>
```

What we have just described is shown in the diagram below. When entered the url we did a Patient Search FHIR Query and the response is called Patient Search FHIR Query Response.

{% include image.html
max-width="200px" file="design/Basic Process Flow PDQm.jpg" alt="Basic Process Flow Patient Search FHIR" caption="Basic Process Flow" %}

ManagagingOrganisation, the patients GP Practice is given as a reference (Organization/24965)

```xml
<managingOrganization>
    <reference value="Organization/24965"/>
    <display value="Moir Medical Centre"/>
</managingOrganization>
```

If you wish to know more details about this organisation, you will need to follow the reference. The Reference used in the the example is relative, they can also point to external servers, e.g.:

```xml
<managingOrganization>
    <reference value="https://fhirserver.trust.nhs.uk/DSTU2/Organization/65"/>
    <display value="Moir Medical Centre"/>
</managingOrganization>
```

We retrieve the Organization resource in the similar manner to searching for the Patient but as we know the `Id` of the resource we can access it directly.

```
GET [baseUrl]/Organization/24965
```

The response from this request is shown below, it is not returned in a FHIR [Bundle](http://www.hl7.org/fhir/dstu2/bundle.html) as we haven't performed a search and requested the resource by it's Id. The SDS/ODS code can be found in the identifier section.

#### XML Example 2 - Organization ####

```xml
<Organization xmlns="http://hl7.org/fhir">
    <id value="24965"/>
    <meta>
        <lastUpdated value="2017-06-02T09:27:43.366+01:00"/>
        <profile value="https://fhir.hl7.org.uk/StructureDefinition/CareConnect-Organization-1"/>
    </meta>
    <identifier>
        <system value="https://fhir.nhs.uk/Id/ods-organization-code"/>
        <value value="C81010"/>
    </identifier>
    <type>
        <coding>
            <system value="https://fhir.hl7.org.uk/ValueSet/organisation-type-1"/>
            <code value="prov"/>
            <display value="Healthcare Provider"/>
        </coding>
    </type>
    <name value="The Moir Medical Centre"/>
    <telecom>
        <system value="phone"/>
        <value value="0115 9737320"/>
        <use value="work"/>
    </telecom>
    <address>
        <use value="work"/>
        <type value="both"/>
        <line value="Regent Street"/>
        <line value="Long Eaton"/>
        <city value="Nottingham"/>
        <postalCode value="NG10 1QQ"/>
    </address>
</Organization>
```

The method for returning Practitioner is the similar and an example is shown below in section 2.2

### 2.1 identifier ###

To find a patient by NHS number, Hospital number, etc we use the identifier. The earlier example contained an NHS number, the number 9876543210 belongs to the system `https://fhir.nhs.uk/Id/nhs-number`, which is identifier for the NHS Number in England and Wales.

```xml
<identifier>
    <extension url="https://fhir.hl7.org.uk/StructureDefinition/Extension-CareConnect-NHSNumberVerificationStatus-1">
        ... snip ...
    </extension>
    <system value="https://fhir.nhs.uk/Id/nhs-number"/>
    <value value="9876543210"/>
</identifier>
```

To search for Patients by NHS number, use the following query:

```
GET [baseUrl]/Patient?identifier=[system]|[code]
```

The system is `https://fhir.nhs.uk/Id/nhs-number` and the code is `9876543210`, e.g.

```
GET [baseUrl]/Patient?identifier=https://fhir.nhs.uk/Id/nhs-number|9876543210
```

This will return all Patient resources with a NHS number of 9876543210 (this may be more than one). NHS Number may not be the main patient identifier within a NHS Organisation or Health Enterprise, this is for a number of reasons:
* Patient doesn't currently have a NHS Number (foreign visitor or from another home nation in the UK)
* Patient's NHS number hasn't been validated (and so can not be used for interoperability/communication)
* Patient has not been identified accurately.

For these reasons the trust/health organisation will use it's own primary identifier, often referred to as Hospital or District number. Organisation's will need to create their own system for the identifier, in the example Example NHS Trust have used 'https://fhir.example.nhs.uk/PAS/Patient' to indicate PAS Hospital Number. They use this with the API as shown below:

```
GET [baseUrl]/Patient?identifier=https://fhir.example.nhs.uk/PAS/Patient|123345
```

{% include note.html content="Trust or Organisation can choose to use their main identifier as the logical Id. [TODO add notes about national NHS systems using NHS Number this way.]" %}

### 2.2. Java Example ###

The examples are built using [HAPI FHIR](http://hapifhir.io/) which is an open source implementation of the HL7 FHIR specification by the University Health Network, Canada. Source code can be found on [NHSConnect GitHub](https://github.com/nhsconnect/careconnect-java-examples/blob/master/careconnect-client/src/main/java/uk/nhs/careconnect/examples/clientExampleApp.java)

The first example uses the same search parameters we used earlier, we are searching for patients with a surname of Kanfeld, forename of Bernie and date of birth 19/Mar/1998. The first couple of lines setup a Dstu2 FHIR context and set the baseUrl to be `http://127.0.0.1:8181/Dstu2/`. The output from running this code is shown earlier in this guide.

#### Java Example 1 - Patient Search ####

```java
       // Create a FHIR Context
       FhirContext ctx = FhirContext.forDstu2();
       IParser parser = ctx.newXmlParser();

       // Create a client and post the transaction to the server
       IGenericClient client = ctx.newRestfulGenericClient("http://127.0.0.1:8181/Dstu2/");

       System.out.println("GET http://127.0.0.1:8181/Dstu2/Patient?birthdate=1998-03-19&given=bernie&family=kanfeld");
       Bundle results = client
               .search()
               .forResource(Patient.class)
               .where(Patient.FAMILY.matches().value("kanfeld"))
               .and(Patient.GIVEN.matches().value("bernie"))
               .and(Patient.BIRTHDATE.exactly().day("1998-03-19"))
               .returnBundle(ca.uhn.fhir.model.dstu2.resource.Bundle.class)
               .execute();
       System.out.println(parser.setPrettyPrint(true).encodeResourceToString(results));
```

In this example we have omitted the context and client setup. This shows how a search on NHS Number would be executed, the resulting XML out would be the same as the previous listing.

#### Java Example 2 - Patient Search NHS Number ####

```java
       System.out.println("GET http://127.0.0.1:8181/Dstu2/Patient?identifier=https://fhir.nhs.uk/Id/nhs-number|9876543210");
       results = client
               .search()
               .forResource(Patient.class)
               .where(Patient.IDENTIFIER.exactly().systemAndCode("https://fhir.nhs.uk/Id/nhs-number", "9876543210"))
               .returnBundle(ca.uhn.fhir.model.dstu2.resource.Bundle.class)
               .execute();
       System.out.println(parser.setPrettyPrint(true).encodeResourceToString(results));
```

The examples have used a logical reference to SDS codes, this means we can't simply call Organization or Practitioner by using their Id's we must do a search on identifier

```
GET http://[baseUrl]/Organization?identifier=https://fhir.nhs.uk/Id/ods-organization-code|C81010
```

```
GET http://[baseUrl]/Practitoner?identifier=https://fhir.nhs.uk/Id/sds-user-id|G8133438
```

#### Java Example 3 - Organization and Practitioner Search ####

```java
    if (results.getEntry().size() > 0) {
          // Process first patient only.
          Patient patient = (Patient) results.getEntry().get(0).getResource();
          System.out.println();

          // Assume Organisation Id is SDS/ODS Code
          Bundle organisationResults = client
                  .search()
                  .forResource(Organization.class)
                  .where(Organization.IDENTIFIER.exactly().systemAndCode("https://fhir.nhs.uk/Id/ods-organization-code",patient.getManagingOrganization().getReference().getIdPart()))
                  .returnBundle(ca.uhn.fhir.model.dstu2.resource.Bundle.class)
                  .execute();
          System.out.println(parser.setPrettyPrint(true).encodeResourceToString(organisationResults));

          if (patient.getCareProvider().size() > 0) {
              Bundle gpResults = client
                      .search()
                      .forResource(Practitioner.class)
                      .where(Practitioner.IDENTIFIER.exactly().systemAndCode("https://fhir.nhs.uk/Id/sds-user-id", patient.getCareProvider().get(0).getReference().getIdPart()))
                      .returnBundle(ca.uhn.fhir.model.dstu2.resource.Bundle.class)
                      .execute();
              System.out.println(parser.setPrettyPrint(true).encodeResourceToString(gpResults));
          }
      }
```

If we did have the logical Id's returned in the Patient resources we could have retrieved the Organization (or Practitioner) resources directly. In the example below the Patients organisation Id is `24965` (this is the Id of the Organization in XML Example 2 )

#### Java Example 4 - Organization Read ####

```java
            Organization gpPractice = (Organization) client.read().resource(Organization.class).withId("24965").execute();
            System.out.println(parser.setPrettyPrint(true).encodeResourceToString(gpPractice));
```

<!--

This is referring to a draft NHS Digital policy

## 3. National (NHS) Patient Search ##

{% include image.html
max-width="200px" file="design/National PDQ Actor Diagram.jpg" alt="National NHS Patient Search Actor Diagram"
caption="National NHS Patient Search Actor Diagram" %}

National systems in England may use the logical Id as the business identiferEnglish NHS will use the NHS Number as the logical Id.  

Currently, the only national resources this would apply to are:
•	Organisation (ODS Code)
•	Patient (NHS Number)
•	Prescription (Prescription ID)
•	Practitioner (SDS ID)


{% include image.html
max-width="200px" file="design/National Basic Process Flow PDQm.jpg" alt="National NHS Process Flow PDQ FHIR" caption="National NHS Process Flow Patient Search FHIR" %}
-->
## 3. Server(/Gateway) Patient Search  ##

<!-- This section is introducing the facade pattern. This may not sound useful but is probably the most common patterns with FHIR in the UK -->
In practice many FHIR Servers will be facades or gateways. [Facades](https://en.wikipedia.org/wiki/Facade_pattern) will provide a standardised CareConnect interface to the underlying a SQL database or provide a CareConnectAPI gateway to other patient search systems such NHS Spine Mini Services Provider (SMSP) or HL7v2 Patient queries. In both cases the CareConnect client is insulated away from the interfacing technology or technology stack.

{% include image.html
max-width="200px" file="design/Gateway PDQ Actor Diagram.jpg" alt="National NHS Patient Search Actor Diagram"
caption=" Implementing Patient Search FHIR as a gateway" %}

The {% include custom/patterns.inline.html content="[Service Connector(/Gateway) Pattern ](http://www.servicedesignpatterns.com/webserviceinfrastructures/serviceconnector)" %} can insulate client applications from complex processing which is especially useful for web applications. This would typically be done in a Trust Integration Engine or other middleware products such as Apache Camel. Advantages include:
* Insulates clients from the complexities of interoperability.
* Transforms external calls into internal formats (e.g. HL7v2 / HL7v3 XML to FHIR JSON/XML)
* Allows the different security models to work with each other (e.g. OAuth2 based environment working with FHIR API using certificate based authentication)
* Simplifies client access. API Gateway can retrieve demographics from multiple sources with a single query.

Consider the HL7v2 Example below:

#### HL7 version 2 Example 1 - Patient Demographics Query ####

```
MSH|^~\&|TEST_HARNESS|TEST|CR1|MOH_CAAT|20090226131520-0600||QBP^Q22^QBP_Q21|TEST-CR-15-20|P|2.5
QPD|Q22^Find Candidates^HL7|Q1520|@PID.8^F~@PID.5.1^JONES
RCP|I|10^RD
```

This is searching for female patients with a surname of Jones. It is not clear from the message this is a search query and also the parameters `@PID.8^F~@PID.5.1^JONES` means a female called Jones. Also it's difficult to call from a web browser based application.
Using a FHIR API Gateway hides this complexity from the client web developer allowing them to use the $http service as shown in the example below:

#### AngularJS Example 1 - Web App Client Search ####

```js
angular.module('App').controller('PatientDetailsController', function ($scope, $http) {
  $scope.search = function()
  {
    $http({
        method : 'GET',
            url : 'http://127.0.0.1:8181/Dstu2/Patient?family=jones&gender=female'
      })
          .success(function (bundleddata) {
      $scope.bundle = bundleddata;
    }).error(function (err) {     
    })
  }
});
```

<!--
| SMSP Request | FHIR Patient Search |
|--------------|---------------------|
| getPatientDetailsByNHSNumber| `GET http://[proxyUrl]/Patient?identifier=https://fhir.nhs.uk/Id/nhs-number|[NHSNumber]&birthdate=[DateOfBirth]` |
| getPatientDetailsBySearch | `GET http://[proxyUrl]/Patient?birthdate=[DateOfBirth]&given=[Forename]&family=[Surname]&gender=[Gender]&adddress-postcode=[Postcode]` |
| getPatientDetails| `GET http://[proxyUrl]/Patient?identifier=https://fhir.nhs.uk/Id/nhs-number|[NHSNumber]&birthdate=[DateOfBirth]&given=[Forename]&family=[Surname]&gender=[Gender]&adddress-postcode=[Postcode]` |
-->

{% include image.html
max-width="200px" file="design/Gateway Process Flow PDQm.jpg" alt="Gateway Process Flow Patient Search FHIR" caption="Sample Patient Search FHIR gateway process flow" %}
