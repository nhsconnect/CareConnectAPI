---
title: Clinical | Medication
keywords: usecase, medication
tags: [fhir, rest, clinical, medication]
sidebar: foundations_sidebar
permalink: restfulapis_clinical_medication.html
summary: This resource is primarily used for the identification and definition of a medication. It covers the ingredients and the packaging for a medication.
---
{% include custom/search.warnbanner.html %}

{% include custom/profile.html content="Medication" page="CareConnect-Medication-1.html" %}

{% include custom/fhir.resource.html content="[Medication](https://www.hl7.org/fhir/DSTU2/medication.html#search)" %}

## 1. Read ##

<div markdown="span" class="alert alert-success" role="alert">
GET /Medication/[id]</div>

Return a single `Medication` for the specified id.

## 2. Search Parameters ##

<div markdown="span" class="alert alert-success" role="alert">
GET /Medication?[searchparameters]</div>
Search for all flag resources for a patient. Fetches a bundle of all `Medication` resources for the specified patient.

{% include custom/moscow.html content="[Medication](https://www.hl7.org/fhir/DSTU2/medication.html#search)" %}

| Name | Type | Description | Conformance | Path |
|------|------|-------------|-------|------|
| `code` | `token` | 	Codes that identify this medication | MAY | Medication.code |

{% include custom/search.code.medication.html para="2.1." content="Medication" %}

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
   <id value="48496"/>
   <meta>
      <profile value="https://fhir.nhs.uk/StructureDefinition/CareConnect-Medication-1"/>
   </meta>
   <code>
      <coding>
         <system value="http://snomed.info/sct"/>
         <code value="10097211000001102"/>
         <display value="Insulin glulisine 100units/ml solution for injection 3ml pre-filled disposable devices"/>
      </coding>
   </code>
   <product>
      <form>
         <coding>
            <system value="http://snomed.info/sct"/>
            <code value="385219001"/>
            <display value="Solution for injection"/>
         </coding>
      </form>
   </product>
</Medication>
```
