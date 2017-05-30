---
title: Clinical | Procedure
keywords: usecase, procedure
tags: [fhir, rest, clinical]
sidebar: foundations_sidebar
permalink: restfulapis_clinical_procedure.html
summary: An action that is or was performed on a patient. This can be a physical intervention like an operation, or less invasive like counseling or hypnotherapy.
---
{% include custom/search.warnbanner.html %}

{% include custom/profile.html content="[Care Connect Procedure](http://www.interopen.org/candidate-profiles/care-connect/CareConnect-Procedure-1.html)" %}

{% include custom/fhir.resource.html content="[Procedure](https://www.hl7.org/fhir/DSTU2/procedure.html#search)" %}


## 1. Read ##

<div markdown="span" class="alert alert-success" role="alert">
GET /Procedure/[id]</div>
Return a single `Procedure` for the specified id

## 2. Search Parameters ##

<div markdown="span" class="alert alert-success" role="alert">
GET /Procedure?[searchParameters]</div>

Procedure resource contains procedure information for a patient. Fetches a bundle of all `Procedure` resources for the specified patient.

{% include custom/moscow.html content="[Procedure](https://www.hl7.org/fhir/DSTU2/procedure.html#search)" %}

| Name | Type | Description | Conformance  | Path |
|------|------|-------------|-------|------|
| `date` | `date` | Obtained date/time. If the obtained element is a period, a date that falls in the period | Y | Procedure.performed[x] |
| `patient` | `reference` | Search by subject - a patient | Y | Procedure.subject <br>(Patient) |
| `subject` | `reference` | Search by subject |  | Procedure.subject <br>(Patient) |

{% include custom/search.date.html para="2.1." content="Procedure" %}

{% include custom/search.patient.html para="2.2." content="Procedure" %}

{% include custom/search.subject.html para="2.3." content="Procedure" %}

## 3. Example ##

### 3.1 Request Query ###

Return all Procedure resources for Patient with NHS Number of 9876543210, the format of the response body will be xml. Replace 'baseUrl' with the actual base Url of the FHIR Server.

#### 3.1.1. cURL ####

{% include custom/embedcurl.html title="Search Procedure" command="curl -X GET  'http://[baseUrl]/Procedure?patient.identifier=https://fhir.nhs.uk/Id/nhs-number|9876543210&_format=xml'" %}

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
    <id value="b312fad7-8fcb-4a9c-a95e-b709401937c4"/>
    <meta>
        <lastUpdated value="2017-05-24T07:51:46.008-04:00"/>
    </meta>
    <type value="searchset"/>
    <total value="1"/>
    <link>
        <relation value="self"/>
        <url value="http://fhirtest.uhn.ca/baseDstu2/Procedure?patient=https%3A%2F%2Fpds.proxy.nhs.uk%2FPatient%2F9876543210"/>
    </link>
    <entry>
        <fullUrl value="http://fhirtest.uhn.ca/baseDstu2/Procedure/32449"/>
        <resource>
            <Procedure xmlns="http://hl7.org/fhir">
                <id value="32449"/>
                <meta>
                    <versionId value="1"/>
                    <lastUpdated value="2017-05-24T07:51:33.166-04:00"/>
                    <profile value="https://fhir.nhs.uk/StructureDefinition/CareConnect-Procedure-1"/>
                </meta>
                <subject>
                    <reference value="https://pds.proxy.nhs.uk/Patient/9876543210"/>
                    <display value="Bernie Manfeld"/>
                </subject>
                <status value="completed"/>
                <code>
                    <coding>
                        <system value="http://snomed.info/sct"/>
                        <code value="923461000000103"/>
                        <display value="Lifestyle education for diabetes"/>
                    </coding>
                </code>
                <performer>
                    <actor>
                        <reference value="https://sds.proxy.nhs.uk/Organization/Organization/RY8"/>
                        <display value="Derbyshire Community Health Services NHS Foundation Trust"/>
                    </actor>
                </performer>
                <performedPeriod>
                    <start value="2017-03-22T09:30:10+01:00"/>
                    <end value="2017-03-22T10:30:10+01:00"/>
                </performedPeriod>
                <followUp>
                    <text value="described in care plan"/>
                </followUp>
            </Procedure>
        </resource>
        <search>
            <mode value="match"/>
        </search>
    </entry>
</Bundle>
```
