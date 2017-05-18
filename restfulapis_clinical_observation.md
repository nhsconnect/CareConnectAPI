---
title: Clinical | Observation
keywords: usecase, observation
tags:
- restful_api
- clinical
- profile
sidebar: foundations_sidebar
permalink: restfulapis_clinical_observation.html
summary: Clinical Observation
---

## Observation ##

{% include profile.html content="[Care Connect Observation](http://www.interopen.org/candidate-profiles/care-connect/CareConnect-Observation-1.html)" %}

## Read Operation ##

Return a single `Observation` for the specified id

```http
GET /Observation/[id]
```

```http
GET /Observation?_id=[id]
```


## Search Parameters ##

Observation resource contains observation or event information for a patient. Fetches a bundle of all `Observation` resources for the specified patient.

```http
GET /Observation?[searchParameters]
```

{% include optional.html content="[Observation](https://www.hl7.org/fhir/DSTU2/observation.html#search)" %}

Provider systems SHOULD implement the following search parameters:

| Name | Type | Description | Recommended |
| `code` | `token` | The code of the observation type | Y |
| `patient` | `reference` | The identity of a patient to list observations for | Y |
| `date` | `date` | Obtained date/time. If the obtained element is a period, a date that falls in the period | Y |
| `_count` | `number` | The maximum number of results per page. |  |

In order to manage the number of search results returned, the server may choose to return the results in a series of pages. The search result set contains the URLs that the client uses to request additional pages from the search set. For a simple RESTful search, the page links are contained in the returned bundle as links. Please refer to [Paged Search](https://www.hl7.org/fhir/DSTU2/search.html#count){:target="_blank"} for further details.

### patient ###

The patient parameter can be used two ways:

#### patient= [id] ####

`id` is the logical id of the patient on the server which is obtained by a [Patient ](restfulapis_identification_patient.html) resource query.

```http
GET /Observation?patient=42
```

#### patient.identifier={systemUri}|[identifier] ####

`:systemUri` is a uniform resource identifier which defines which system the identifer belongs to. For NHS Number this would be `http://fhir.nhs.net/Id/nhs-number` and `:identifier` would be the NHS Number. Suppliers and organisations can create their own systemUri's, e.g. the fictional Jorvik NHS Trust could use `http://fhir.jorvik.nhs.uk/Patient` and the identifier could be the hospital number.

```http
GET /Observation?patient.identifier=http://fhir.nhs.net/Id/nhs-number|9876543210
```

```http
GET /Observation?patient.identifier=http://fhir.jorvik.nhs.uk/Patient|12345678
```

### code ###

#### code={systemUri}|[code] ####

#### code=[code] ####

`:systemUri` is a uniform resource identifier which defines which system the code belongs to. This is optional and if not present all matching codes will be returned regardles of CodeSystems. 

To search for Observations with `Baseline body mass index` using SNOMED CT

```http
GET /Observation?code=http://snomed.info/sct|846931000000101
```

To search for all resources with 'Body composition measure' codes using SNOMED CT 

```http
GET /Observation?code:below=http://snomed.info/sct|363810004
```

The modifier `:below` is a modifier which returns all resources with codes that are subsumed by the specified search code and includes the specified code. 

### date ###

See [date](https://www.hl7.org/fhir/DSTU2/search.html#date) for details on this parameter. 'date' can be used multiple times as a search parameter 

```http
GET [base]/Observation?date=ge2010-01-01&date=le2011-12-31
```

## Search Response ##
```
curl --get http://127.0.0.1:8080/careconnect-dstu2-hapi-uiDstu2/Observation?patient=1
```

| Http Header | Value |
|-----------------|---------|
| ResponseCode | 200 |


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
                    <profile value="http://hl7.org/fhir/StructureDefinition/careconnect-observation-1"/>
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
                    <reference value="Patient/1"/>
                </subject>
                <effectiveDateTime value="2012-09-17"/>
                <performer>
                    <reference value="Practitioner/4952"/>
                </performer>
            </Observation>
        </resource>
        <search>
            <mode value="match"/>
        </search>
    </entry>
</Bundle>
```
