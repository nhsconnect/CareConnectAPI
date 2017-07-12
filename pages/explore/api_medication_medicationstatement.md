---
title: Medication | Medication Statement
keywords: usecase, clinical
tags: [fhir, rest, medication, api]
sidebar: foundations_sidebar
permalink: api_medication_medicationstatement.html
summary: A record of a medication that is being consumed by a patient. A MedicationStatement may indicate that the patient may be taking the medication now, or has taken the medication in the past or will be taking the medication in the future.
---
{% include custom/search.warnbanner.html %}

{% include custom/fhir.reference.html resource="Medication Statement" page="CareConnect-MedicationStatement-1" fhirlink="[MedicationStatement](https://www.hl7.org/fhir/DSTU2/medicationstatement.html)" content="Bristol Connecting Care POC" userlink="engage_poc_bristolcc.html" %}

## 1. Read ##

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/MedicationStatement/[id]</div>

{% include custom/read.response.html resource="MedicationStatement" content="" %}

## 2. Search ##

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/MedicationStatement?[searchParameters]</div>

Fetches a bundle of all `MedicationStatement` resources for the specified patient.

{% include custom/search.header.html resource="MedicationStatement" %}

### 2.1. Search Parameters ###

{% include custom/search.parameters.html resource="MedicationStatement"     link="https://www.hl7.org/fhir/DSTU2/medicationstatement.html#search" %}

<table style="min-width:100%;width:100%">
<tr id="clinical">
    <th style="width:15%;">Name</th>
    <th style="width:10%;">Type</th>
    <th style="width:40%;">Description</th>
    <th style="width:5%;">Conformance</th>
    <th style="width:30%;">Path</th>
</tr>
<tr>
    <td><code class="highlighter-rouge">effectivedate</code></td>
    <td><code class="highlighter-rouge">date</code></td>
    <td>Date when patient was taking (or not taking) the medication</td>
    <td>SHOULD</td>
    <td>MedicationStatement.effective[x]</td>
</tr>
<tr>
    <td><code class="highlighter-rouge">patient</code></td>
    <td><code class="highlighter-rouge">reference</code></td>
    <td>The identity of a patient to list statements for</td>
    <td>SHALL</td>
    <td>MedicationStatement.patient<br>(Patient)</td>
</tr>
<tr>
    <td><code class="highlighter-rouge">status</code></td>
    <td><code class="highlighter-rouge">token</code></td>
    <td>Return statements that match the given status</td>
    <td>SHOULD</td>
    <td>MedicationStatement.status</td>
</tr>
</table>

<!--
Systems SHOULD support the following search combinations:

* patient

-->

{% include custom/search.date.plus.html para="2.1.1." content="MedicationStatement" name="effectivedate" %}

{% include custom/search.patient.html para="2.1.2" content="MedicationStatement" %}

{% include custom/search.status.html para="2.1.3." content="MedicationStatement" options="active | completed | entered-in-error | intended" selected="active" %}

{% include custom/search.response.html resource="MedicationStatement" %}

## 3. Example ##

### 3.1 Request Query ###

Return all MedciationStatement resources for Patient with a NHS Number of 9876543210, the format of the response body will be xml. Replace 'baseUrl' with the actual base Url of the FHIR Server.

#### 3.1.1. cURL ####

{% include custom/embedcurl.html title="Search MedicationStatement" command="curl -H 'Accept: application/xml+fhir' -H 'Authorization: BEARER [token]' -X GET  '[baseUrl]/MedicationStatement?patient.identifier=https://fhir.nhs.uk/Id/nhs-number|9876543210'" %}

{% include custom/search.response.headers.html resource="MedicationStatement" %}

#### 3.2.2 Http Body ####

<script src="https://gist.github.com/KevinMayfield/9ab94408ef84f46606dbdf236cb9e272.js"></script>
