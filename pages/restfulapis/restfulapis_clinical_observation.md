---
title: Clinical | Observation
keywords: usecase, observation
tags: [observation,fhir,rest,clinical]
sidebar: foundations_sidebar
permalink: restfulapis_clinical_observation.html
summary: Clinical Observation
---

{% include search.warnbanner.html %}
{% include profile.html content="[Care Connect Observation](http://www.interopen.org/candidate-profiles/care-connect/CareConnect-Observation-1.html)" %}

## 1. Read ##

<div markdown="span" class="alert alert-success" role="alert">
GET /Observation/[id]</div>

Return a single `Observation` for the specified id

## 2. Search Parameters ##

<div markdown="span" class="alert alert-success" role="alert">
GET /Observation?[searchParameters]</div>

Observation resource contains observation or event information for a patient. Fetches a bundle of all `Observation` resources for the specified patient.

{% include moscow.html content="[Observation](https://www.hl7.org/fhir/DSTU2/observation.html#search)" %}


| Name | Type | Description | Conformance | Path |
|------|------|-------------|-------|------|
| `category` | `token` | The classification of the type of observation | SHALL | Observation.category |
| `code` | `token` | The code of the observation type | SHALL | Observation.code |
| `date` | `date` | Obtained date/time.<br>If the obtained element is a period, a date that falls in the period | SHALL | Observation.effective[x] |
| `patient` | `reference` | The subject that the observation is about (if patient) | SHALL | Observation.subject (Patient) |


<!-- | `subject` | `reference` | The subject that the observation is about| | Observation.subject (Patient) |
-->

{% include search.status.plus.html para="2.1." content="Observation" options="see profile/valueset" selected="exam" name="category" %}

{% include search.code.html para="2.2." content="Observation" %}

{% include search.date.html para="2.3." content="Observation" %}

{% include search.patient.html para="2.4." content="Observation" %}
<!--
{% include search.subject.html para="2.5." content="Observation" %}
-->
## 3. Example ##

### 3.1. Request Query ###

Return all Observation resources for Patient with NHS Number of 9876543210, the format of the response body will be xml. Replace 'baseUrl' with the actual base Url of the FHIR Server.

#### 3.1.1. cURL ####

{% include embedcurl.html title="Search Observation" command="curl -X GET  'http://[baseUrl]/Observation?patient.identifier=https://fhir.nhs.uk/Id/nhs-number|9876543210&_format=xml'" %}

### 3.2. Response Headers ###

| Status Code |
|----------------|
|200 |

| Header | Value |
|-----------------|---------|
| Content-Type  | application/xml+fhir;charset=UTF-8 |

### 3.3. Response Body ###

```xml
<Bundle xmlns="http://hl7.org/fhir">
    <id value="ab49bf8e-a805-4b4c-871e-ff7cec75bcb5"/>
    <meta>
        <lastUpdated value="2017-05-18T12:06:52.948+01:00"/>
    </meta>
    <type value="searchset"/>
    <total value="1"/>
    <link>
        <relation value="self"/>
        <url value="http://127.0.0.1:8080/careconnect-dstu2-hapi-ui/Dstu2/Observation?patient=1"/>
    </link>
    <entry>
        <fullUrl value="http://127.0.0.1:8080/careconnect-dstu2-hapi-ui/Dstu2/Observation/4953"/>
        <resource>
            <Observation xmlns="http://hl7.org/fhir">
                <id value="4953"/>
                <meta>
                    <versionId value="1"/>
                    <lastUpdated value="2017-05-18T12:06:03.140+01:00"/>
                    <profile value="https://fhir.nhs.uk/StructureDefinition/CareConnect-Observation-1"/>
                </meta>
                <identifier>
                    <system value="http://fhir.jorvik.nhs.uk/EPR/Observation"/>
                    <value value="878281"/>
                </identifier>
                <status value="final"/>
                <code>
                    <coding>
                        <system value="http://snomed.info/sct"/>
                        <code value="162864005"/>
                        <display value="Body mass index 30+ - obesity"/>
                    </coding>
                </code>
                <subject>
                    <reference value="https://pds.proxy.nhs.uk/Patient/9876543210"/>
                </subject>
                <effectiveDateTime value="2012-09-17"/>
                <performer>
                    <reference value="https://sds.proxy.nhs.uk/Practitioner/G8133438" />
                </performer>
            </Observation>
        </resource>
        <search>
            <mode value="match"/>
        </search>
    </entry>
</Bundle>
```
