---
title: Clinical | Medication
keywords: usecase, medication
tags: [fhir, rest, clinical, medication]
sidebar: foundations_sidebar
permalink: restfulapis_clinical_medication.html
summary: This resource is primarily used for the identification and definition of a medication. It covers the ingredients and the packaging for a medication.
---
{% include custom/search.warnbanner.html %}
{% include custom/profile.html content="[Care Connect Medication](http://www.interopen.org/candidate-profiles/care-connect/CareConnect-Medication-1.html)" %}

## 1. Read ##

<div markdown="span" class="alert alert-success" role="alert">
GET /Medication/[id]</div>

Return a single `Medication` for the specified id.

## 2. Search Parameters ##

TODO

## 3. Example ##

### 3.1 Request Operation ###

Return Medication resource with a logical id of 48496. Replace 'baseUrl' with the actual base Url of the FHIR Server.

#### 3.1.1. cURL ####

{% include custom/embedcurl.html title="Get Medication" command="curl -X GET  'http://[baseUrl]/Medication/48496'" %}

### 3.2 Response Headers ###

| Status Code |
|----------------|
|200 |

| Header | Value |
|-----------------|---------|
| Content-Type  | application/xml+fhir;charset=UTF-8 |

### 3.3 Response Body ###

```xml
<Medication xmlns="http://hl7.org/fhir">
  <meta>
    <profile value="https://fhir.nhs.uk/StructureDefinition/CareConnect-Medication-1"/>
  </meta>
  <id value="48496"/>
  <code>
    <coding>
      <system value="http://snomed.info/sct"/>
      <code value="134623009"/>
      <display value="Capecitabine 150mg tablet (product)"/>
    </coding>
  </code>
  <isBrand value="false"/>
  <product>
    <form>
      <coding>
        <system value="http://snomed.info/sct"/>
        <code value="440131009"/>
        <display value="Oral dosage form product"/>
      </coding>
    </form>
  </product>
</Medication>
```
