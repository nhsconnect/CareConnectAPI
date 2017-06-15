---
title: Clinical | Observation
keywords: usecase, observation
tags: [observation,fhir,rest,clinical,development]
sidebar: foundations_sidebar
permalink: restfulapis_clinical_observation.html
summary: Measurements and simple assertions made about a patient, device or other subject.
---

{% include custom/search.warnbanner.html %}

{% include custom/profile.html content="Observation" page="CareConnect-Observation-1" %}

{% include custom/fhir.resource.html content="[Observation](https://www.hl7.org/fhir/DSTU2/observation.html)" %}

## 1. Read ##

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/Observation/[id]</div>

{% include custom/read.response.html resource="Observation" content="" %}

## 2. Search ##

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/Observation?[searchParameters]</div>

Fetches a bundle of all `Observation` resources for the specified patient.

{% include custom/search.header.html resource="Observation" %}

### 2.1. Search Parameters ###

{% include custom/search.parameters.html resource="Observation"     link="https://www.hl7.org/fhir/DSTU2/observation.html#search" %}


| Name | Type | Description | Conformance | Path |
|------|------|-------------|-------|------|
| `category` | `token` | The classification of the type of observation | SHOULD | Observation.category |
| `code` | `token` | The code of the observation type | SHOULD| Observation.code |
| `date` | `date` | Obtained date/time.<br>If the obtained element is a period, a date that falls in the period | SHALL | Observation.effective[x] |
| `patient` | `reference` | The subject that the observation is about (if patient) | SHALL | Observation.subject (Patient) |

Systems SHALL support the following search combinations:

* patient + clinicalstatus
* patient + category


<!-- | `subject` | `reference` | The subject that the observation is about| | Observation.subject (Patient) |
-->

{% include custom/search.status.plus.html para="2.1.1." content="Observation" options="see profile/valueset for codes" selected="exam" name="category" %}

{% include custom/search.code.html para="2.1.2." content="Observation" %}

{% include custom/search.date.html para="2.1.3." content="Observation" %}

{% include custom/search.patient.html para="2.1.4." content="Observation" %}
<!--
{% include custom/search.subject.html para="2.5." content="Observation" %}
-->

{% include custom/search.response.html resource="Observation" %}

## 3. Example ##

### 3.1. Request Query ###

Return all Observation resources for Patient with NHS Number of 9876543210, the format of the response body will be xml. Replace 'baseUrl' with the actual base Url of the FHIR Server.

#### 3.1.1. cURL ####

{% include custom/embedcurl.html title="Search Observation" command="curl -H 'Accept: application/xml+fhir' -H 'Authorization: BEARER [token]' -X GET  '[baseUrl]/Observation?patient.identifier=https://fhir.nhs.uk/Id/nhs-number|9876543210'" %}

{% include custom/search.response.headers.html resource="Observation" %}

### 3.3. Response Body ###

```xml
<Bundle xmlns="http://hl7.org/fhir">
    <id value="2ec19aad-e619-42c7-a32e-3f0d39c5e7ac"/>
    <meta>
        <lastUpdated value="2017-06-02T09:22:07.888+01:00"/>
    </meta>
    <type value="searchset"/>
    <total value="1"/>
    <link>
        <relation value="self"/>
        <url value="[baseUrl]/Observation?patient=https%3A%2F%2Fpds.proxy.nhs.uk%2FPatient%2F9876543210"/>
    </link>
    <entry>
        <fullUrl value="[baseUrl]/Observation/24964"/>
        <resource>
            <Observation xmlns="http://hl7.org/fhir">
                <id value="24964"/>
                <meta>
                    <lastUpdated value="2017-06-02T09:20:13.289+01:00"/>
                    <profile value="https://fhir.hl7.org.uk/StructureDefinition/CareConnect-Observation-1"/>
                </meta>
                <status value="final"/>
                <code>
                    <coding>
                        <system value="http://snomed.info/sct"/>
                        <code value="162864005"/>
                        <display value="Body mass index 30+ - obesity"/>
                    </coding>
                </code>
                <subject>
                    <reference value="Patient/24966"/>
                </subject>
                <effectiveDateTime value="2012-09-17"/>
                <performer>
                    <reference value="Practitioner/24967"/>
                </performer>
            </Observation>
        </resource>
        <search>
            <mode value="match"/>
        </search>
    </entry>
</Bundle>
```
