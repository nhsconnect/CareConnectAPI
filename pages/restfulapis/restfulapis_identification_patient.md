---
title: Identification | Patient
keywords: getcarerecord, structured, rest, patient
tags: [rest, fhir, identification]
sidebar: accessrecord_rest_sidebar
permalink: restfulapis_identification_patient.html
summary: Patient
---

{% include search.warnbanner.html %}
{% include profile.html content="[Care Connect Patient](http://www.interopen.org/candidate-profiles/care-connect/CareConnect-Patient-1.html)" %}

## 1. Read ##

<div markdown="span" class="alert alert-success" role="alert">
GET /Patient/[id]</div>
Return a single `Patient` for the specified id (not the NHS Number).

## 2. Search Parameters ##

<div markdown="span" class="alert alert-success" role="alert">
GET /Patient?[searchParameters]</div>
Patient contains the demographics for the patient. Fetches a bundle of all `Patient` resources for the specified patient or search criteria.

{% include moscow.html content="[Patient](https://www.hl7.org/fhir/DSTU2/patient.html#search)" %}

| Name | Type | Description | SHALL | Path |
|------|------|-------------|-------|------|
| `adddress-postcode` | `string` | A postalCode specified in an address |  | Practitioner.address.postalCode |
| `birthdate` | `date` | The patient's date of birth | Y | Patient.birthDate |
| `email` | `token` | A value in an email contact |  | Patient.telecom <br>(system=email) |
| `family` | `string` | A portion of the family name of the patient | Y | Patient.name.family |
| `gender` | `token` | Gender of the patient | Y | Patient.gender |
| `given` | `string` | A portion of the given name of the patient | Y | Patient.name.given |
| `identifier` | `token` | A patient identifier (NHS Number, Hospital Number, etc) | Y | Patient.identifier |
| `name` | `string` | A portion of either family or given name of the patient | | 	Patient.name |
| `phone` | `token` | A value in a phone contact | | Patient.telecom(system=phone) |


<!--
| `address` | `string` | An address in any kind of address/part of the patient |  | Practitioner.address |
| `careprovider` | `reference` | Patient's nominated GP | | Patient.careProvider <br>(Practitioner) |
| `organization` | `reference` | The practice at which this person is a patient | | Patient.managingOrganization <br>(Organization) |
| `telecom` | `token` | The value in any kind of telecom details of the patient |  | Patient.telecom |
-->

{% include search.string.html para="2.1." resource="Patient" content="address-postcode"  example="NG10%201ZZ" text1="Post Code" text2="NG10 1ZZ" %}

{% include search.date.plus.html para="2.2." content="Patient" name="birthdate" %}

{% include search.string.html para="2.3." resource="Patient" content="email"  example="bernie.kanfeld@chumhum.com" text1="email address" text2="bernie.kanfeld@chumhum.com" %}

{% include search.string.html para="2.4." resource="Patient" content="family"  example="kanfeld" text1="surname" text2="Kanfeld" %}

{% include search.token.html para="2.5." resource="Patient" content="gender"  example="female" text1="Administrative Sex" text2="female" %}

{% include search.string.html para="2.6." resource="Patient" content="given"  example="bernie" text1="forename" text2="Bernie" %}

{% include search.identifier.html para="2.7." resource="Patient" content="identifier" subtext="NHS Number, Hospital Number, etc" example="https://fhir.nhs.uk/Id/nhs-number|9876543210" text1="NHS Number" text2="9876543210" %}

{% include search.string.html para="2.8." resource="Patient" content="name"  example="bernie%20kanfeld" text1="name" text2="Bernie Kanfeld" %}

{% include search.string.html para="2.9." resource="Patient" content="phone"  example="07999 123456" text1="phone number" text2="07999 123456" %}

## 3. Example ##

### 3.1 Query ###
Return all Patient resources with a NHS Number 9876543210, the format of the response body will be xml. Replace 'baseUrl' with the actual base Url of the FHIR Server.

#### cURL ####

{% include embedcurl.html title="Search Patient" command="curl -X GET  'http://[baseUrl]/Patient?identifier=https://fhir.nhs.uk/Id/nhs-number|9876543210&_format=xml'" %}

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
    <id value="f0566028-976e-4d4f-8e5e-f4209b29f52e"/>
    <meta>
        <lastUpdated value="2017-05-21T12:00:48.832-04:00"/>
    </meta>
    <type value="searchset"/>
    <total value="1"/>
    <link>
        <relation value="self"/>
        <url value="http://fhirtest.uhn.ca/baseDstu2/Patient?_format=xml&amp;identifier=https%3A%2F%2Ffhir.nhs.uk%2FId%2Fnhs-number%7C9876543210"/>
    </link>
    <entry>
        <fullUrl value="http://fhirtest.uhn.ca/baseDstu2/Patient/31936"/>
        <resource>
            <Patient xmlns="http://hl7.org/fhir">
                <id value="31936"/>
                <meta>
                    <versionId value="1"/>
                    <lastUpdated value="2017-05-21T11:55:59.532-04:00"/>
                    <profile value="https://fhir.nhs.uk/StructureDefinition/CareConnect-Patient-1"/>
                </meta>
                <identifier>
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
                        <system value="http://hl7.org/fhir/marital-status"/>
                        <code value="S"/>
                        <display value="Single"/>
                    </coding>
                </maritalStatus>
                <careProvider>
                    <reference value="https://sds.proxy.nhs.uk/Organization/C81010"/>
                    <display value="Moir Medical Centre"/>
                </careProvider>
            </Patient>
        </resource>
        <search>
            <mode value="match"/>
        </search>
    </entry>
</Bundle>
```
