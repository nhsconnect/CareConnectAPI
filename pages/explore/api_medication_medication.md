---
title: Medication | Medication
keywords: usecase, medication
tags: [fhir, rest, medication, api]
sidebar: foundations_sidebar
permalink: api_medication_medication.html
summary: This resource is primarily used for the identification and definition of a medication. It covers the ingredients and the packaging for a medication.
---
{% include custom/search.warnbanner.html %}

{% include custom/fhir.reference.html resource="Medication" page="CareConnect-Medication-1" fhirlink="[Medication](https://www.hl7.org/fhir/DSTU2/medication.html)" content="User Stories" userlink="engage_michaelsstory.html" %}

## 1. Read ##

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/Medication/[id]</div>

{% include custom/read.response.html resource="Medication" content="" %}

## 2. Search ##

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/Medication?[searchparameters]</div>
Search Medication resources. Returns a bundle of all `Medication` resources for the specified search criteria.

{% include custom/search.header.html resource="Medication" %}

### 2.1. Search Parameters ###

{% include custom/search.parameters.html resource="Medication"     link="https://www.hl7.org/fhir/DSTU2/medication.html#search" %}

<table style="min-width:100%;width:100%">
<tr id="clinical">
    <th style="width:15%;">Name</th>
    <th style="width:10%;">Type</th>
    <th style="width:40%;">Description</th>
    <th style="width:5%;">Conformance</th>
    <th style="width:30%;">Path</th>
</tr>
<tr>
    <td><code class="highlighter-rouge">code</code></td>
    <td><code class="highlighter-rouge">token</code></td>
    <td>Codes that identify this medication</td>
    <td>MAY</td>
    <td>Medication.code</td>
</tr>
</table>

{% include custom/search.code.medication.html para="2.1.1." content="Medication" %}

{% include custom/search.response.html resource="Medication" %}

## 3. Example ##

### 3.1 Request Operation ###

Return Medication resource with a logical id of 48496. Replace 'baseUrl' with the actual base Url of the FHIR Server.

#### 3.1.1. cURL ####

{% include custom/embedcurl.html title="Get Medication" command="curl -H 'Accept: application/xml+fhir' -H 'Authorization: BEARER [token]' -X GET  '[baseUrl]/Medication/48496'" %}

{% include custom/search.response.headers.html resource="Immunization" %}

#### 3.2.2 Http Body ####

<script src="https://gist.github.com/KevinMayfield/b2dce41df4ffb395eef568f7769fd086.js"></script>
