---
title: Clinical | Allergy Intolerance
keywords: getcarerecord, structured, rest, allergy, intolerance
tags: [fhir, clinical, rest, allergyintolerance]
sidebar: accessrecord_rest_sidebar
permalink: restfulapis_clinical_allergyintolerance.html
summary: Risk of harmful or undesirable, physiological response which is unique to an individual and associated with exposure to a substance.
---
{% include custom/search.warnbanner.html %}

{% include custom/profile.html content="Allergy Intolerance" page="CareConnect-AllergyIntolerance-1" %}

{% include custom/fhir.resource.html content="[AllergyIntolerance](https://www.hl7.org/fhir/DSTU2/allergyintolerance.html#search)" %}

## 1. Read ##

<div markdown="span" class="alert alert-success" role="alert">
GET /AllergyIntollerence/[id]</div>

{% include custom/read.response.html resource="AllergyIntolerance" content="" %}

## 2. Search ##

<div markdown="span" class="alert alert-success" role="alert">
GET /AllergyIntollerence?[searchParameters]</div>

Search for all allergies for a patient. Fetches a bundle of all `AllergyIntolerance` resources for the specified patient.

### 2.1. Search Parameters ###

{% include custom/moscow.html content="[AllergyIntolerance](https://www.hl7.org/fhir/DSTU2/allergyintolerance.html#search)" %}

| Name | Type | Description | Conformance | Path |
|------|------|-------------|-------------|------|
| `patient` | `reference` | Who the sensitivity is for | SHALL | AllergyIntolerance.patient<br>(Patient) |
| `status` | `token` | Status of AllergyIntolerance	| MAY | AllergyIntolerance.status |



{% include custom/search.patient.html para="2.1.1." content="AllergyIntolerance" %}

{% include custom/search.status.html para="2.1.2." content="AllergyIntolerance" options="active | unconfirmed | confirmed | inactive | resolved | refuted | entered-in-error" selected="refuted" %}

{% include custom/search.response.html resource="Location" %}

## 3. Example ##

### 3.1 Request Query ###

Return all AllergyIntolerance resources for Patient with a NHS Number of 9876543210, the format of the response body will be xml. Replace 'baseUrl' with the actual base Url of the FHIR Server.

#### 3.1.1. cURL ####

{% include custom/embedcurl.html title="Search AllergyIntolerance" command="curl -X GET  'http://[baseUrl]/AllergyIntolerance?patient.identifier=https://fhir.nhs.uk/Id/nhs-number|9876543210&_format=xml'" %}

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
    <id value="77a4ee23-696f-4d7e-b8d9-9cdd8dc69a4d"/>
    <meta>
        <lastUpdated value="2017-06-02T08:25:54.191+01:00"/>
    </meta>
    <type value="searchset"/>
    <total value="1"/>
    <link>
        <relation value="self"/>
        <url value="http://127.0.0.1:8181/Dstu2/AllergyIntolerance?patient=https%3A%2F%2Fpds.proxy.nhs.uk%2FPatient%2F9876543210"/>
    </link>
    <entry>
        <fullUrl value="http://127.0.0.1:8181/Dstu2/AllergyIntolerance/24953"/>
        <resource>
            <AllergyIntolerance xmlns="http://hl7.org/fhir">
                <id value="24953"/>
                <meta>
                    <versionId value="1"/>
                    <lastUpdated value="2017-06-02T08:25:01.686+01:00"/>
                    <profile value="https://fhir.hl7.org.uk/StructureDefinition/CareConnect-AllergyIntolerance-1"/>
                </meta>
                <identifier>
                    <system value="https://epr.jorvik.nhk.uk/AllergyIntolerance "/>
                    <value value="49476534"/>
                </identifier>
                <recordedDate value="2014-10-09T14:58:00+11:00"/>
                <recorder>
                    <reference value="https://sds.proxy.nhs.uk/Practitioner/G8133438"/>
                </recorder>
                <patient>
                    <reference value="https://pds.proxy.nhs.uk/Patient/9876543210"/>
                </patient>
                <substance>
                    <coding>
                        <system value="http://snomed.info/sct"/>
                        <code value="226017009"/>
                        <display value="Bombay mix"/>
                    </coding>
                </substance>
                <status value="confirmed"/>
                <criticality value="CRITH"/>
                <type value="allergy"/>
                <category value="food"/>
                <lastOccurence value="2012-06"/>
                <reaction>
                    <manifestation>
                        <coding>
                            <system value="http://snomed.info/sct"/>
                            <code value="39579001"/>
                            <display value="Anaphylactic reaction"/>
                        </coding>
                    </manifestation>
                    <onset value="2012-06-12"/>
                </reaction>
            </AllergyIntolerance>
        </resource>
        <search>
            <mode value="match"/>
        </search>
    </entry>
</Bundle>
```
