---
title: Clinical | Condition
keywords: getcarerecord, structured, rest, condition
tags: [rest,fhir,condition,clinical,api]
sidebar: accessrecord_rest_sidebar
permalink: api_clinical_condition.html
summary: Use to record detailed information about conditions, problems or diagnoses recognized by a clinician. There are many uses e.g. recording a diagnosis during an encounter; populating a problem list or a summary statement, such as a discharge summary.
---
{% include custom/search.warnbanner.html %}

{% include custom/fhir.reference.html resource="Condition" page="CareConnect-Condition-1" fhirlink="[Condition](https://www.hl7.org/fhir/DSTU2/condition.html)" content="User Stories" userlink="engage_michaelsstory.html" %}


## 1. Read ##

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/Condition/[id]</div>

{% include custom/read.response.html resource="Condition" content="" %}

## 2. Search ##

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/Condition?[searchParameters]</div>

Search for all problems and health concerns for a patient. Fetches a bundle of all `Condition` resources for the specified patient.

{% include custom/search.header.html resource="Condition" %}

### 2.1. Search Parameters ###

{% include custom/search.parameters.html resource="Condition"     link="https://www.hl7.org/fhir/DSTU2/condition.html#search" %}

<table style="min-width:100%;width:100%">
<tr id="clinical">
    <th style="width:15%;">Name</th>
    <th style="width:15%;">Type</th>
    <th style="width:35%;">Description</th>
    <th style="width:5%;">Conformance</th>
    <th style="width:30%;">Path</th>
</tr>
<tr>
    <td><code class="highlighter-rouge">category</code></td>
    <td><code class="highlighter-rouge">token</code></td>
    <td>The category of the condition</td>
    <td>SHOULD</td>
    <td>Condition.category</td>
</tr>
<tr>
    <td><code class="highlighter-rouge">clinicalstatus</code></td>
    <td><code class="highlighter-rouge">token</code></td>
    <td>The clinical status of the condition</td>
    <td>SHOULD</td>
    <td>Condition.clinicalStatus</td>
</tr>
<tr>
    <td><code class="highlighter-rouge">date-recorded</code></td>
    <td><code class="highlighter-rouge">date</code></td>
    <td>A date, when the Condition statement was documented</td>
    <td>MAY</td>
    <td>Condition.dateRecorded</td>
</tr>
<tr>
    <td><code class="highlighter-rouge">patient</code></td>
    <td><code class="highlighter-rouge">reference</code></td>
    <td>Who has the condition?</td>
    <td>SHALL</td>
    <td>Condition.patient<br>(Patient)</td>
</tr>
</table>

Systems SHOULD support the following search combinations:

* patient + clinicalstatus
* patient + category

{% include custom/search.status.plus.html para="2.1.1." content="Condition" options="
complaint | symptom | finding | diagnosis | problem | need" selected="symptom" name="category" %}

{% include custom/search.status.plus.html para="2.1.2." content="Condition" options="active | inactive | relapse | remission | resolved" selected="relapse" name="clinicalstatus" %}

{% include custom/search.date.plus.html para="2.1.3." content="Condition" name="date-recorded" %}

{% include custom/search.patient.html para="2.1.4." content="Condition" %}

{% include custom/search.response.html resource="Condition" %}

## 3. Example ##

### 3.1 Request Query ###

Return all Condition resources for Patient with a NHS Number of 9876543210, the format of the response body will be xml. Replace 'baseUrl' with the actual base Url of the FHIR Server.

#### 3.1.1. cURL ####

{% include custom/embedcurl.html title="Search Condition" command="curl -H 'Accept: application/xml+fhir' -H 'Authorization: BEARER [token]' -X GET  '[baseUrl]/Condition?patient.identifier=https://fhir.nhs.uk/Id/nhs-number|9876543210'" %}

{% include custom/search.response.headers.html resource="Condition" %}

#### 3.2.2 Http Body ####

<script src="https://gist.github.com/KevinMayfield/4ecacc1d28bc22efbf630119207c70c0.js"></script>
