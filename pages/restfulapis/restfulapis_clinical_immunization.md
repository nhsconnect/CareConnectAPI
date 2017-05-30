---
title: Clinical | Immunization
keywords: getcarerecord, structured, rest, immunization
tags: [fhir, rest, clinical, familymemberhistory]
sidebar: accessrecord_rest_sidebar
permalink: restfulapis_clinical_immunization.html
summary: Describes the event of a patient being administered a vaccination or a record of a vaccination as reported by a patient, a clinician or another party and may include vaccine reaction information and what vaccination protocol was followed.
---
{% include custom/search.warnbanner.html %}

{% include custom/profile.html content="[Care Connect Immunization](http://www.interopen.org/candidate-profiles/care-connect/CareConnect-Immunization-1.html)" %}

{% include custom/fhir.resource.html content="[Immunization](https://www.hl7.org/fhir/DSTU2/immunization.html#search)" %}

## 1. Read ##

<div markdown="span" class="alert alert-success" role="alert">
GET /Immunization/[id]</div>
Return a single `Immunization` for the specified id

## 2. Search Parameters ##

<div markdown="span" class="alert alert-success" role="alert">
GET /Immunization?[searchParameters]</div>

Search for all immunization resources for a patient. Fetches a bundle of all `Immunization` resources for the specified patient.

{% include custom/moscow.html content="[Immunization](https://www.hl7.org/fhir/DSTU2/immunization.html#search)" %}

| Name | Type | Description | Conformance  | Post |
|------|------|-------------|-------|------|
| `date` | `date` | Vaccination (non)-Administration Date | SHALL | Immunization.date |
| `patient` | `reference` | The patient for the vaccination record |  | 	Immunization.patient<br>(Patient) |
| `status` | `token` | Immunization event status | | Immunization.status |

<!--
| `dose-sequence` | `number` | Dose number within series |  | 	Immunization.vaccinationProtocol.doseSequence |
| `notgiven` | `token` | Administrations which were not given | | Immunization.wasNotGiven |
| `lot-number` | `string` | Vaccine Batch Number |  | Immunization.lotNumber |
| `vaccine-code` | `token` | Vaccine Product Administered |  | Immunization.vaccineCode |
-->
{% include custom/search.date.html para="2.1." content="Immunization" %}

{% include custom/search.patient.html para="2.2." content="Immunization" %}

{% include custom/search.status.html para="2.3." content="Immunization" options="in-progress | on-hold | completed | entered-in-error | stopped" selected="on-hold" %}

## 3. Example ##

### 3.1 Request Query ###

Return all Immunization resources for Patient with a NHS Number of 9876543210, the format of the response body will be xml. Replace 'baseUrl' with the actual base Url of the FHIR Server.

#### 3.1.1. cURL ####

{% include custom/embedcurl.html title="Search Immunization" command="curl -X GET  'http://[baseUrl]/Immunization?patient.identifier=https://fhir.nhs.uk/Id/nhs-number|9876543210&_format=xml'" %}

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
    <id value="db7b6433-5e28-4c66-a9dc-d2b8ed048496"/>
    <meta>
        <lastUpdated value="2017-05-25T07:43:23.057-04:00"/>
    </meta>
    <type value="searchset"/>
    <total value="1"/>
    <link>
        <relation value="self"/>
        <url value="http://fhirtest.uhn.ca/baseDstu2/Immunization?_format=xml&amp;patient=https%3A%2F%2Fpds.proxy.nhs.uk%2FPatient%2F9876543210"/>
    </link>
    <entry>
        <fullUrl value="http://fhirtest.uhn.ca/baseDstu2/Immunization/32502"/>
        <resource>
            <Immunization xmlns="http://hl7.org/fhir">
                <id value="32502"/>
                <meta>
                    <versionId value="1"/>
                    <lastUpdated value="2017-05-25T07:38:43.382-04:00"/>
                    <profile value="https://fhir.nhs.uk/StructureDefinition/CareConnect-Immunization-1"/>
                </meta>
                <extension url="https://fhir.nhs.uk/StructureDefinition/Extension-CareConnect-DateRecorded-1">
                    <valueDateTime value="2016-03-01T09:30:00+00:00"/>
                </extension>
                <status value="in-progress"/>
                <date value="2016-03-01T09:30:00+00:00"/>
                <vaccineCode>
                    <coding>
                        <system value="http://snomed.info/sct"/>
                        <code value="396429000"/>
                        <display value="Measles, mumps and rubella vaccine (substance)"/>
                    </coding>
                </vaccineCode>
                <patient>
                    <reference value="https://pds.proxy.nhs.uk/Patient/9876543210"/>
                    <display value="Bernie Kanfeld"/>
                </patient>
                <wasNotGiven value="false"/>
                <reported value="false"/>
                <performer>
                    <reference value="https://sds.proxy.nhs.uk/Practitioner/G8133438"/>
                    <display value="Dr Bhatia"/>
                </performer>
                <lotNumber value="63259874"/>
                <expirationDate value="2020-01-01"/>
                <vaccinationProtocol>
                    <doseSequence value="1"/>
                    <doseStatus>
                        <coding>
                            <system value="http://hl7.org/fhir/vaccination-protocol-dose-status"/>
                            <code value="count"/>
                            <display value="Counts"/>
                        </coding>
                    </doseStatus>
                </vaccinationProtocol>
            </Immunization>
        </resource>
        <search>
            <mode value="match"/>
        </search>
    </entry>
</Bundle>
```
