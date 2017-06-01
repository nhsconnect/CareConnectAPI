---
title: Clinical | Condition
keywords: getcarerecord, structured, rest, condition
tags: [rest,fhir,condition,clinical]
sidebar: accessrecord_rest_sidebar
permalink: restfulapis_clinical_condition.html
summary: Use to record detailed information about conditions, problems or diagnoses recognized by a clinician. There are many uses e.g. recording a diagnosis during an encounter; populating a problem list or a summary statement, such as a discharge summary.
---
{% include custom/search.warnbanner.html %}

{% include custom/profile.html content="Condition" page="CareConnect-Condition-1.html" %}

{% include custom/fhir.resource.html content="[Condition](https://www.hl7.org/fhir/DSTU2/condition.html#search)" %}


## 1. Read Operation ##

<div markdown="span" class="alert alert-success" role="alert">
GET /Condition/[id]</div>

Return a single `Condition` for the specified id

## 2. Search Parameters ##

<div markdown="span" class="alert alert-success" role="alert">
GET /Condition?[searchParameters]</div>

Search for all problems and health concerns for a patient. Fetches a bundle of all `Condition` resources for the specified patient.

{% include custom/moscow.html content="[Condition](https://www.hl7.org/fhir/DSTU2/condition.html#search)" %}

| Name | Type | Description | Conformance  | Path |
|------|------|-------------|-------|------|
| `category` | `token` | The category of the condition | SHOULD| Condition.category |
| `clinicalstatus` | `token` | The clinical status of the condition | SHOULD | 	Condition.clinicalStatus |
| `date-recorded` | `date` | A date, when the Condition statement was documented | MAY  | Condition.dateRecorded |
| `patient` | `reference` | Who has the condition? | SHALL | Condition.patient<br>(Patient) |

{% include custom/search.status.plus.html para="2.1." content="Condition" options="
complaint | symptom | finding | diagnosis | problem | need" selected="symptom" name="category" %}

{% include custom/search.status.plus.html para="2.2." content="Condition" options="active | inactive | relapse | remission | resolved" selected="relapse" name="clinicalstatus" %}

{% include custom/search.date.plus.html para="2.3." content="Condition" name="date-recorded" %}

{% include custom/search.patient.html para="2.4." content="Condition" %}

## 3. Example ##

### 3.1 Request Query ###

Return all Condition resources for Patient with a NHS Number of 9876543210, the format of the response body will be xml. Replace 'baseUrl' with the actual base Url of the FHIR Server.

#### 3.1.1. cURL ####

{% include custom/embedcurl.html title="Search Condition" command="curl -X GET  'http://[baseUrl]/Condition?patient.identifier=https://fhir.nhs.uk/Id/nhs-number|9876543210&_format=xml'" %}

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
    <id value="b924f866-c8c5-4726-8efa-9535d35c3875"/>
    <meta>
        <lastUpdated value="2017-05-24T11:01:15.643-04:00"/>
    </meta>
    <type value="searchset"/>
    <total value="1"/>
    <link>
        <relation value="self"/>
        <url value="http://fhirtest.uhn.ca/baseDstu2/Condition?patient=https%3A%2F%2Fpds.proxy.nhs.uk%2FPatient%2F9876543210"/>
    </link>
    <entry>
        <fullUrl value="http://fhirtest.uhn.ca/baseDstu2/Condition/32475"/>
        <resource>
            <Condition xmlns="http://hl7.org/fhir">
                <id value="32475"/>
                <meta>
                    <versionId value="1"/>
                    <lastUpdated value="2017-05-24T11:00:50.173-04:00"/>
                    <profile value="https://fhir.nhs.uk/StructureDefinition/CareConnect-Condition-1"/>
                </meta>
                <patient>
                    <reference value="https://pds.proxy.nhs.uk/Patient/9876543210"/>
                </patient>
                <asserter>
                    <reference value="https://sds.proxy.nhs.uk/Practitioner/C5206458"/>
                </asserter>
                <code>
                    <coding>
                        <system value="http://snomed.info/sct"/>
                        <code value="44054006"/>
                        <display value="Type 2 diabetes mellitus"/>
                    </coding>
                </code>
                <clinicalStatus value="active"/>
                <verificationStatus value="confirmed"/>
                <onsetDateTime value="2003-01-06T17:11:19-05:00"/>
            </Condition>
        </resource>
        <search>
            <mode value="match"/>
        </search>
    </entry>
</Bundle>
```
