---
title: Identification | Patient
keywords: getcarerecord, structured, rest, patient
tags: [rest, fhir, identification]
sidebar: accessrecord_rest_sidebar
permalink: restfulapis_identification_patient.html
summary: Demographics and other administrative information about an individual or animal receiving care or other health-related services.
---

{% include custom/search.warnbanner.html %}

## 0. References ##

{% include custom/profile.html content="Patient" page="CareConnect-Patient-1" %}

{% include custom/fhir.resource.html content="[Patient](https://www.hl7.org/fhir/DSTU2/patient.html#search)" %}

{% include custom/apicontext.userstories.html content="User Stories" page="engage_user_stories.html" %}

## 1. Read ##

<div markdown="span" class="alert alert-success" role="alert">
GET /Patient/[id]</div>

{% include custom/read.response.html resource="Patient" content=" (not the NHS Number)" %}


## 2. Search Parameters ##

<div markdown="span" class="alert alert-success" role="alert">
GET /Patient?[searchParameters]</div>
Fetches a bundle of all `Patient` resources for the specified patient or search criteria.

{% include custom/search.header.html resource="Patient" %}

### 2.1. Search Parameters ###

{% include custom/moscow.html content="[Patient](https://www.hl7.org/fhir/DSTU2/patient.html#search)" %}

| Name | Type | Description | Conformance | Path |
|------|------|-------------|-------|------|
| `adddress-postcode` | `string` | A postalCode specified in an address | MAY | Practitioner.address.postalCode |
| `birthdate` | `date` | The patient's date of birth | SHALL | Patient.birthDate |
| `email` | `token` | A value in an email contact | MAY | Patient.telecom <br>(system=email) |
| `family` | `string` | A portion of the family name of the patient | SHALL | Patient.name.family |
| `gender` | `token` | Gender of the patient | SHALL | Patient.gender |
| `given` | `string` | A portion of the given name of the patient | SHALL | Patient.name.given |
| `identifier` | `token` | A patient identifier (NHS Number, Hospital Number, etc) | SHALL | Patient.identifier |
| `name` | `string` | A portion of either family or given name of the patient | SHALL | 	Patient.name |
| `phone` | `token` | A value in a phone contact | MAY | Patient.telecom(system=phone) |

Systems SHALL support the following search combinations:

* name + gender
* name + birthdate
* family + gender
* given + gender


<!--
| `address` | `string` | An address in any kind of address/part of the patient |  | Practitioner.address |
| `careprovider` | `reference` | Patient's nominated GP | | Patient.careProvider <br>(Practitioner) |
| `organization` | `reference` | The practice at which this person is a patient | | Patient.managingOrganization <br>(Organization) |
| `telecom` | `token` | The value in any kind of telecom details of the patient |  | Patient.telecom |
-->

{% include custom/search.nopat.string.html para="2.1.1." resource="Patient" content="address-postcode"  example="NG10%201ZZ" text1="Post Code" text2="NG10 1ZZ" %}

{% include custom/search.nopat.date.plus.html para="2.1.2." content="Patient" name="birthdate" %}

{% include custom/search.nopat.string.html para="2.1.3." resource="Patient" content="email"  example="bernie.kanfeld@chumhum.com" text1="email address" text2="bernie.kanfeld@chumhum.com" %}

{% include custom/search.nopat.string.html para="2.1.4." resource="Patient" content="family"  example="kanfeld" text1="surname" text2="Kanfeld" %}

{% include custom/search.nopat.token.html para="2.1.5." resource="Patient" content="gender"  example="female" text1="Administrative Sex" text2="female" %}

{% include custom/search.nopat.string.html para="2.1.6." resource="Patient" content="given"  example="bernie" text1="forename" text2="Bernie" %}

{% include custom/search.nopat.identifier.html para="2.1.7." resource="Patient" content="identifier" subtext="NHS Number, Hospital Number, etc" example="https://fhir.nhs.uk/Id/nhs-number|9876543210" text1="NHS Number" text2="9876543210" %}

{% include custom/search.nopat.string.html para="2.1.8." resource="Patient" content="name"  example="bernie%20kanfeld" text1="name" text2="Bernie Kanfeld" %}

{% include custom/search.nopat.string.html para="2.1.9." resource="Patient" content="phone"  example="07999 123456" text1="phone number" text2="07999 123456" %}

{% include custom/search.response.html resource="Patient"  %}

## 3. Example ##

### 3.1 Request Query ###

Return all Patient resources with a NHS Number 9876543210, the format of the response body will be xml. Replace 'baseUrl' with the actual base Url of the FHIR Server.

#### 3.1.1. cURL ####

{% include custom/embedcurl.html title="Search Patient" command="curl -X GET  'http://[baseUrl]/Patient?identifier=https://fhir.nhs.uk/Id/nhs-number|9876543210&_format=xml'" %}

{% include custom/search.response.headers.html resource="Patient"  %}

### 3.3 Response Body ###

```xml
<Bundle xmlns="http://hl7.org/fhir">
    <id value="78682a2e-2541-4b1b-b06c-f0ab310a1ca4"/>
    <meta>
        <lastUpdated value="2017-06-02T09:32:09.352+01:00"/>
    </meta>
    <type value="searchset"/>
    <total value="1"/>
    <link>
        <relation value="self"/>
        <url value="http://127.0.0.1:8181/Dstu2/Patient?identifier=9876543210"/>
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
                    <reference value="https://sds.proxy.nhs.uk/Practitioner/G8133438"/>
                    <display value="Dr AA Bhatia"/>
                </careProvider>
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
