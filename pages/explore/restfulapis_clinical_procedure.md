---
title: Clinical | Procedure
keywords: usecase, procedure
tags: [fhir, rest, clinical,development]
sidebar: foundations_sidebar
permalink: restfulapis_clinical_procedure.html
summary: An action that is or was performed on a patient. This can be a physical intervention like an operation, or less invasive like counseling or hypnotherapy.
---
{% include custom/search.warnbanner.html %}

{% include custom/profile.html content="Procedure" page="CareConnect-Procedure-1" %}

{% include custom/fhir.resource.html content="[Procedure](https://www.hl7.org/fhir/DSTU2/procedure.html)" %}


## 1. Read ##

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/Procedure/[id]</div>

{% include custom/read.response.html resource="Procedure" content="" %}

## 2. Search ##

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/Procedure?[searchParameters]</div>

Fetches a bundle of all `Procedure` resources for the specified patient.

{% include custom/search.header.html resource="Procedure" %}

### 2.1. Search Parameters ###

{% include custom/search.parameters.html resource="Procedure"     link="https://www.hl7.org/fhir/DSTU2/procedure.html#search" %}

| Name | Type | Description | Conformance  | Path |
|------|------|-------------|-------|------|
| `date` | `date` | Obtained date/time. If the obtained element is a period, a date that falls in the period | SHALL | Procedure.performed[x] |
| `patient` | `reference` | Search by subject - a patient | SHALL | Procedure.subject <br>(Patient) |
| `subject` | `reference` | Search by subject | MAY | Procedure.subject <br>(Patient) |

Systems SHALL support the following search combinations:

* patient + category
* patient + category + date
* patient + category + code
* patient + category + code + date

{% include custom/search.date.html para="2.1.1." content="Procedure" %}

{% include custom/search.patient.html para="2.1.2." content="Procedure" %}

{% include custom/search.subject.html para="2.1.3." content="Procedure" %}

{% include custom/search.response.html resource="Procedure" %}

## 3. Example ##

### 3.1 Request Query ###

Return all Procedure resources for Patient with NHS Number of 9876543210, the format of the response body will be xml. Replace 'baseUrl' with the actual base Url of the FHIR Server.

#### 3.1.1. cURL ####

{% include custom/embedcurl.html title="Search Procedure" command="curl -H 'Accept: application/xml+fhir' -H 'Authorization: BEARER [token]' -X GET  '[baseUrl]/Procedure?patient.identifier=https://fhir.nhs.uk/Id/nhs-number|9876543210'" %}

{% include custom/search.response.headers.html resource="Procedure" %}

### 3.3 Response Body ###

```xml
<Bundle xmlns="http://hl7.org/fhir">
    <id value="194901ab-76e2-419f-a33f-ac0ce205410c"/>
    <meta>
        <lastUpdated value="2017-06-02T09:38:26.183+01:00"/>
    </meta>
    <type value="searchset"/>
    <total value="1"/>
    <link>
        <relation value="self"/>
        <url value="[baseUrl]/Procedure?patient=https%3A%2F%2Fpds.proxy.nhs.uk%2FPatient%2F9876543210"/>
    </link>
    <entry>
        <fullUrl value="[baseUrl]/Procedure/24968"/>
        <resource>
            <Procedure xmlns="http://hl7.org/fhir">
                <id value="24968"/>
                <meta>
                    <lastUpdated value="2017-06-02T09:36:55.159+01:00"/>
                    <profile value="https://fhir.hl7.org.uk/StructureDefinition/CareConnect-Procedure-1"/>
                </meta>
                <subject>
                    <reference value="Patient/24966"/>
                    <display value="Bernie Kanfeld"/>
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
                        <reference value="Organization/RY8"/>
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
