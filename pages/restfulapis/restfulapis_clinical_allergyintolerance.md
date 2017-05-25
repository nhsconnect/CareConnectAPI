---
title: Clinical | Allergy Intolerance
keywords: getcarerecord, structured, rest, allergy, intolerance
tags: [fhir, clinical, rest, allergyintolerance]
sidebar: accessrecord_rest_sidebar
permalink: restfulapis_clinical_allergyintolerance.html
summary: Clinical Allergy Intolerance
---
{% include search.warnbanner.html %}
{% include profile.html content="[Care Connect Allergy Intolerence](http://www.interopen.org/candidate-profiles/care-connect/CareConnect-AllergyIntolerance-1.html)" %}

## 1. Read ##

<div markdown="span" class="alert alert-success" role="alert">
GET /AllergyIntollerence/[id]</div>

Return a single `AllergyIntolerance` for the specified id.

## 2. Search Parameters ##

<div markdown="span" class="alert alert-success" role="alert">
GET /AllergyIntollerence?[searchParameters]</div>

Search for all allergies for a patient. Fetches a bundle of all `AllergyIntolerance` resources for the specified patient.

{% include moscow.html content="[AllergyIntolerance](https://www.hl7.org/fhir/DSTU2/allergyintolerance.html#search)" %}

| Name | Type | Description | Conformance | Path |
|------|------|-------------|-------------|------|
| `patient` | `reference` | Who the sensitivity is for | SHALL | AllergyIntolerance.patient<br>(Patient) |
| `status` | `token` | Status of AllergyIntolerance	| Y | AllergyIntolerance.status |

{% include search.patient.html para="2.1." content="AllergyIntolerance" %}

{% include search.status.html para="2.2." content="AllergyIntolerance" options="active | unconfirmed | confirmed | inactive | resolved | refuted | entered-in-error" selected="refuted" %}

## 3. Example ##

### 3.1 Request Query ###

Return all AllergyIntolerance resources for Patient with a NHS Number of 9876543210, the format of the response body will be xml. Replace 'baseUrl' with the actual base Url of the FHIR Server.

#### 3.1.1. cURL ####

{% include embedcurl.html title="Search AllergyIntolerance" command="curl -X GET  'http://[baseUrl]/AllergyIntolerance?patient.identifier=https://fhir.nhs.uk/Id/nhs-number|9876543210&_format=xml'" %}

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
    <id value="d29a6ee3-f1dc-490f-9fc0-e9e6643f84b5"/>
    <meta>
        <lastUpdated value="2017-05-25T09:05:33.538-04:00"/>
    </meta>
    <type value="searchset"/>
    <total value="1"/>
    <link>
        <relation value="self"/>
        <url value="http://fhirtest.uhn.ca/baseDstu2/AllergyIntolerance?_format=xml&amp;patient=https%3A%2F%2Fpds.proxy.nhs.uk%2FPatient%2F9876543210"/>
    </link>
    <entry>
        <fullUrl value="http://fhirtest.uhn.ca/baseDstu2/AllergyIntolerance/32503"/>
        <resource>
            <AllergyIntolerance xmlns="http://hl7.org/fhir">
                <id value="32503"/>
                <meta>
                    <versionId value="1"/>
                    <lastUpdated value="2017-05-25T09:01:25.409-04:00"/>
                    <profile value="https://fhir.nhs.uk/StructureDefinition/CareConnect-AllergyIntolerance-1"/>
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
                    <severity value="severe"/>
                </reaction>
            </AllergyIntolerance>
        </resource>
        <search>
            <mode value="match"/>
        </search>
    </entry>
</Bundle>
```
