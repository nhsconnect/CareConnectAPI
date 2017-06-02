---
title: Design | Patient Search (PDQ)
keywords: development
tags: [design,development]
sidebar: overview_sidebar
permalink: design_patient_search.html
summary: "How to use FHIR Patient resources to perform Patient Searches"
---

{% include custom/search.warnbanner.html %}

{% include custom/apilink.html content="[Patient](restfulapis_identification_patient.html)"  %}

{% include custom/ihelink.html content="[IHE Patient Demographic Query Mobile (IHE PDQM)](http://www.ihe.net/uploadedFiles/Documents/ITI/IHE_ITI_Suppl_PDQm.pdf)" %}

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

Care Connect API uses a [RESTful](https://en.wikipedia.org/wiki/Representational_state_transfer) [resource API pattern](http://www.servicedesignpatterns.com/WebServiceAPIStyles/ResourceAPI) to provide access to the central Patient repository which is particularly suited to:
* A health portal securely exposing demographics data to browser based plugins
* Medical devices which need to access patient demographic information
* Mobile devices used by physicians (example bedside eCharts) which need to establish
patient context by scanning a bracelet
* Web based EPR/EHR applications which wish to provide dynamic updates of patient
demographic information such as a non-postback search, additional demographic detail,
etc.
* Any low resource application which exposes patient demographic search functionality

## 2. Basic Patient Search ##

{% include image.html
max-width="200px" file="design/PDQ Actor Diagram.jpg" alt="Patient Search Actor Diagram"
caption="Patient Search Actor Diagram" %}

The patient search can use any of the search parameters defined in the [Patient](restfulapis_identification_patient.html) API. For example if the patient informs the nurse of their date of birth, first name (19th Mar 1998 Bernie Kanfeld) and surname the query would be.

```
GET http://[baseUrl]/Patient?birthdate=1998-03-19&given=bernie&family=kanfeld
```

`[baseUrl]` needs to be replaced with an actual url, in the example below this is `http://127.0.0.1:8181/Dstu2/`. The url would work within a web browser but a better tool to work with RESTful is [Postman](https://www.getpostman.com/)

```
http://127.0.0.1:8181/Dstu2/Patient?birthdate=1998-03-19&given=bernie&family=kanfeld
```

A sample response is shown below

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
        <url value="http://127.0.0.1:8181/Dstu2/Patient?birthdate=1998-03-19&amp;family=kanfeld&amp;given=bernie"/>
    </link>
    <entry>
        <fullUrl value="http://127.0.0.1:8181/Dstu2/Patient/24966"/>
        <resource>
            <Patient xmlns="http://hl7.org/fhir">
                <id value="24966"/>
                <meta>
                    <versionId value="1"/>
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
                <managingOrganization>
                    <reference value="https://sds.proxy.nhs.uk/Organization/C81010"/>
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

What we have just described is shown in the diagram below. When entered the url we did a Patient Demographic Query and the response is called Patient Demographic Query Response.

{% include image.html
max-width="200px" file="design/Basic Process Flow PDQm.jpg" alt="Basic Process Flow PDQ FHIR" caption="Basic Process Flow PDQ FHIR" %}

If your familiar with NHS SDS/ODS Codes you may have noticed the ODS Code as the managing organisation.

```xml
<managingOrganization>
    <reference value="https://sds.proxy.nhs.uk/Organization/C81010"/>
    <display value="Moir Medical Centre"/>
</managingOrganization>
```

If you wish to know more details about this organisation, you will need to follow the reference (the example reference is a logical reference and does not currently exist). References can be relative, the previous section be re-written as (this is the way of referring to local resources):

```xml
<managingOrganization>
    <reference value="Organization/24965"/>
    <display value="Moir Medical Centre"/>
</managingOrganization>
```

Notice the SDS/ODS code has been replaced with a number, this is the logical id of the organisation and to get the ods we will need to request that resource, e.g.

```
http://127.0.0.1:8181/Dstu2/Organization/24965
```

The response from this request is shown below, it is not returned in a FHIR [Bundle](http://www.hl7.org/fhir/dstu2/bundle.html) as we haven't performed a search and requested the resource by it's Id. The ODS code can be found in the identifier section.

```xml
<Organization xmlns="http://hl7.org/fhir">
    <id value="24965"/>
    <meta>
        <versionId value="1"/>
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

### 2.1 identifier ###

To find a patient by NHS number, Hospital number, etc we use the identifier

## 3. National (NHS) Patient Search ##

{% include image.html
max-width="200px" file="design/National PDQ Actor Diagram.jpg" alt="National NHS Patient Search Actor Diagram"
caption="National NHS Patient Search Actor Diagram" %}

{% include image.html
max-width="200px" file="design/National Basic Process Flow PDQm.jpg" alt="National NHS Process Flow PDQ FHIR" caption="National NHS Process Flow PDQ FHIR" %}

## 4. Patient Search Gateway ##

Patient searches using FHIR can be used with other patient search systems such NHS Spine Mini Services Provider (SMSP), HL7v2 Patient queries, etc. In this way the Patient Demographics
Consumer can choose the technology stack that best fits.
The Patient Demographics Supplier may act as a proxy to an existing HL7v2 PDQ, FHIR PDQ or ITK SMSP environment as shown in the diagrams below.

{% include image.html
max-width="200px" file="design/Gateway PDQ Actor Diagram.jpg" alt="National NHS Patient Search Actor Diagram"
caption=" Implementing PDQ FHIR as a gateway" %}

{% include image.html
max-width="200px" file="design/Gateway Process Flow PDQm.jpg" alt="Gateway Process Flow PDQ FHIR" caption="Sample PDQ FHIR gateway process flow" %}
