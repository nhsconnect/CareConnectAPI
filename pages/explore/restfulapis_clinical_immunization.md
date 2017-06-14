---
title: Clinical | Immunization
keywords: getcarerecord, structured, rest, immunization
tags: [fhir, rest, clinical, familymemberhistory]
sidebar: accessrecord_rest_sidebar
permalink: restfulapis_clinical_immunization.html
summary: Describes the event of a patient being administered a vaccination or a record of a vaccination as reported by a patient, a clinician or another party and may include vaccine reaction information and what vaccination protocol was followed.
---
{% include custom/search.warnbanner.html %}

{% include custom/profile.html content="Immunization" page="CareConnect-Immunization-1" %}

{% include custom/fhir.resource.html content="[Immunization](https://www.hl7.org/fhir/DSTU2/immunization.html)" %}

## 1. Read ##

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/Immunization/[id]</div>

{% include custom/read.response.html resource="Immunization" content="" %}

## 2. Search ##

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/Immunization?[searchParameters]</div>

Search for all immunization resources for a patient. Fetches a bundle of all `Immunization` resources for the specified patient.

{% include custom/search.header.html resource="Immunization" %}

### 2.1. Search Parameters ###

{% include custom/search.parameters.html resource="Immunization"     link="https://www.hl7.org/fhir/DSTU2/immunization.html#search" %}

| Name | Type | Description | Conformance  | Post |
|------|------|-------------|-------|------|
| `date` | `date` | Vaccination (non)-Administration Date | SHOULD | Immunization.date |
| `patient` | `reference` | The patient for the vaccination record | SHALL | 	Immunization.patient<br>(Patient) |
| `status` | `token` | Immunization event status | MAY | Immunization.status |

<!--
| `dose-sequence` | `number` | Dose number within series |  | 	Immunization.vaccinationProtocol.doseSequence |
| `notgiven` | `token` | Administrations which were not given | | Immunization.wasNotGiven |
| `lot-number` | `string` | Vaccine Batch Number |  | Immunization.lotNumber |
| `vaccine-code` | `token` | Vaccine Product Administered |  | Immunization.vaccineCode |
-->
{% include custom/search.date.html para="2.1.1." content="Immunization" %}

{% include custom/search.patient.html para="2.1.2." content="Immunization" %}

{% include custom/search.status.html para="2.1.3." content="Immunization" options="in-progress | on-hold | completed | entered-in-error | stopped" selected="on-hold" %}

{% include custom/search.response.html resource="Immunization" %}

## 3. Example ##

### 3.1 Request Query ###

Return all Immunization resources for Patient with a NHS Number of 9876543210, the format of the response body will be xml. Replace 'baseUrl' with the actual base Url of the FHIR Server.

#### 3.1.1. cURL ####

{% include custom/embedcurl.html title="Search Immunization" command="curl -H 'Accept: application/xml+fhir' -X GET  '[baseUrl]/Immunization?patient.identifier=https://fhir.nhs.uk/Id/nhs-number|9876543210'" %}

{% include custom/search.response.headers.html resource="Immunization" %}

### 3.3 Response Body ###

```xml
<Bundle xmlns="http://hl7.org/fhir">
    <id value="6aed30c2-dcbe-460a-8738-a5f60a4248ff"/>
    <meta>
        <lastUpdated value="2017-06-02T08:51:27.827+01:00"/>
    </meta>
    <type value="searchset"/>
    <total value="1"/>
    <link>
        <relation value="self"/>
        <url value="http://127.0.0.1:8181/Dstu2/Immunization?patient=https%3A%2F%2Fpds.proxy.nhs.uk%2FPatient%2F9876543210"/>
    </link>
    <entry>
        <fullUrl value="http://127.0.0.1:8181/Dstu2/Immunization/24956"/>
        <resource>
            <Immunization xmlns="http://hl7.org/fhir">
                <id value="24956"/>
                <meta>
                    <versionId value="1"/>
                    <lastUpdated value="2017-06-02T08:48:28.340+01:00"/>
                    <profile value="https://fhir.hl7.org.uk/StructureDefinition/CareConnect-Immunization-1"/>
                </meta>
                <extension url="https://fhir.hl7.org.uk/StructureDefinition/Extension-CareConnect-DateRecorded-1">
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
                    <targetDisease>
                        <coding>
                            <system value="http://snomed.info/sct"/>
                            <code value="14189004"/>
                        </coding>
                        <coding>
                            <system value="http://snomed.info/sct"/>
                            <code value="36653000"/>
                        </coding>
                        <coding>
                            <system value="http://snomed.info/sct"/>
                            <code value="36989005"/>
                        </coding>
                    </targetDisease>
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
