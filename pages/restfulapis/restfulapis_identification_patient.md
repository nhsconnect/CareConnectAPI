---
title: Identification | Patient
keywords: getcarerecord, structured, rest, patient
tags: [rest, fhir, identification]
sidebar: accessrecord_rest_sidebar
permalink: restfulapis_identification_patient.html
summary: Demographics and other administrative information about an individual or animal receiving care or other health-related services.
---

{% include custom/search.warnbanner.html %}

{% include custom/profile.html content="[Care Connect Patient](http://www.interopen.org/candidate-profiles/care-connect/CareConnect-Patient-1.html)" %}

{% include custom/fhir.resource.html content="[Patient](https://www.hl7.org/fhir/DSTU2/patient.html#search)" %}

## 1. Read ##

<div markdown="span" class="alert alert-success" role="alert">
GET /Patient/[id]</div>
Return a single `Patient` for the specified id (not the NHS Number).

## 2. Search Parameters ##

<div markdown="span" class="alert alert-success" role="alert">
GET /Patient?[searchParameters]</div>
Patient contains the demographics for the patient. Fetches a bundle of all `Patient` resources for the specified patient or search criteria.

{% include custom/moscow.html content="[Patient](https://www.hl7.org/fhir/DSTU2/patient.html#search)" %}

| Name | Type | Description | Conformance | Path |
|------|------|-------------|-------|------|
| `adddress-postcode` | `string` | A postalCode specified in an address | SHOULD | Practitioner.address.postalCode |
| `birthdate` | `date` | The patient's date of birth | SHALL | Patient.birthDate |
| `email` | `token` | A value in an email contact | SHOULD | Patient.telecom <br>(system=email) |
| `family` | `string` | A portion of the family name of the patient | SHALL | Patient.name.family |
| `gender` | `token` | Gender of the patient | SHALL | Patient.gender |
| `given` | `string` | A portion of the given name of the patient | SHALL | Patient.name.given |
| `identifier` | `token` | A patient identifier (NHS Number, Hospital Number, etc) | SHALL | Patient.identifier |
| `name` | `string` | A portion of either family or given name of the patient | SHALL | 	Patient.name |
| `phone` | `token` | A value in a phone contact | SHOULD | Patient.telecom(system=phone) |


<!--
| `address` | `string` | An address in any kind of address/part of the patient |  | Practitioner.address |
| `careprovider` | `reference` | Patient's nominated GP | | Patient.careProvider <br>(Practitioner) |
| `organization` | `reference` | The practice at which this person is a patient | | Patient.managingOrganization <br>(Organization) |
| `telecom` | `token` | The value in any kind of telecom details of the patient |  | Patient.telecom |
-->

{% include custom/search.string.html para="2.1." resource="Patient" content="address-postcode"  example="NG10%201ZZ" text1="Post Code" text2="NG10 1ZZ" %}

{% include custom/search.date.plus.html para="2.2." content="Patient" name="birthdate" %}

{% include custom/search.string.html para="2.3." resource="Patient" content="email"  example="bernie.kanfeld@chumhum.com" text1="email address" text2="bernie.kanfeld@chumhum.com" %}

{% include custom/search.string.html para="2.4." resource="Patient" content="family"  example="kanfeld" text1="surname" text2="Kanfeld" %}

{% include custom/search.token.html para="2.5." resource="Patient" content="gender"  example="female" text1="Administrative Sex" text2="female" %}

{% include custom/search.string.html para="2.6." resource="Patient" content="given"  example="bernie" text1="forename" text2="Bernie" %}

{% include custom/search.identifier.html para="2.7." resource="Patient" content="identifier" subtext="NHS Number, Hospital Number, etc" example="https://fhir.nhs.uk/Id/nhs-number|9876543210" text1="NHS Number" text2="9876543210" %}

{% include custom/search.string.html para="2.8." resource="Patient" content="name"  example="bernie%20kanfeld" text1="name" text2="Bernie Kanfeld" %}

{% include custom/search.string.html para="2.9." resource="Patient" content="phone"  example="07999 123456" text1="phone number" text2="07999 123456" %}

## 3. Example ##

### 3.1 Request Query ###
Return all Patient resources with a NHS Number 9876543210, the format of the response body will be xml. Replace 'baseUrl' with the actual base Url of the FHIR Server.

#### 3.1.1. cURL ####

{% include custom/embedcurl.html title="Search Patient" command="curl -X GET  'http://[baseUrl]/Patient?identifier=https://fhir.nhs.uk/Id/nhs-number|9876543210&_format=xml'" %}

### 3.2 Response Headers ###

| Status Code |
|----------------|
|200 |

| Header | Value |
|-----------------|---------|
| Content-Type  | application/xml+fhir;charset=UTF-8 |

### 3.3 Response Body ###

```xml
<Bundle xmlns="http://hl7.org/fhir">
    <id value="aa167489-c554-42f6-bfdd-53227ff1faad"/>
    <meta>
        <lastUpdated value="2017-05-26T05:39:27.492-04:00"/>
    </meta>
    <type value="searchset"/>
    <total value="1"/>
    <link>
        <relation value="self"/>
        <url value="http://fhirtest.uhn.ca/baseDstu2/Patient?_format=xml&amp;identifier=https%3A%2F%2Ffhir.nhs.uk%2FId%2Fnhs-number%7C9876543210"/>
    </link>
    <entry>
        <fullUrl value="http://fhirtest.uhn.ca/baseDstu2/Patient/32898"/>
        <resource>
            <Patient xmlns="http://hl7.org/fhir">
                <id value="32898"/>
                <meta>
                    <versionId value="1"/>
                    <lastUpdated value="2017-05-26T05:39:03.280-04:00"/>
                    <profile value="https://fhir.nhs.uk/StructureDefinition/CareConnect-Patient-1"/>
                </meta>
                <extension url="https://fhir.nhs.uk/StructureDefinition/Extension-CareConnect-EthnicCategory-1">
                    <valueCodeableConcept>
                        <coding>
                            <system value="https://fhir.hl7.org.uk/CareConnect-EthnicCategory-1"/>
                            <code value="01"/>
                            <display value="British, Mixed British"/>
                        </coding>
                    </valueCodeableConcept>
                </extension>
                <identifier>
                    <extension url="https://fhir.nhs.uk/StructureDefinition/Extension-CareConnect-NHSNumberVerificationStatus-1">
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
