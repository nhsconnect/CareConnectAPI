---
title: Workflow | Encounter
keywords: usecase, encounter
tags: [rest, fhir, workflow,api]
sidebar: foundations_sidebar
permalink: api_workflow_encounter.html
summary: An interaction between a patient and healthcare provider(s) for the purpose of providing healthcare service(s) or assessing the health status of a patient.
---
{% include custom/search.warnbanner.html %}

{% include custom/fhir.reference.html resource="Encounter" page="CareConnect-Encounter-1" fhirlink="[Encounter](https://www.hl7.org/fhir/DSTU2/encounter.html)" content="User Stories" userlink="engage_michaelsstory.html" %}

## 1. Read ##

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/Encounter/[id]</div>

{% include custom/read.response.html resource="Encounter" content="" %}

## 2. Search ##

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/Encounter?[searchParameters]</div>

Fetches a bundle of all `Encounter` resources for the specified patient.

{% include custom/search.header.html resource="Encounter" %}

### 2.1. Search Parameters ###

{% include custom/search.parameters.html resource="Encounter"     link="https://www.hl7.org/fhir/DSTU2/encounter.html#search" %}


<table style="min-width:100%;width:100%">
<tr id="clinical">
    <th style="width:10%;">Name</th>
    <th style="width:15%;">Type</th>
    <th style="width:40%;">Description</th>
    <th style="width:5%;">Conformance</th>
    <th style="width:30%;">Path</th>
</tr>
<tr>
    <td><code class="highlighter-rouge">date</code></td>
    <td><code class="highlighter-rouge">date</code></td>
    <td>A date within the period the Encounter lasted</td>
    <td>MAY</td>
    <td>Encounter.period</td>
</tr>
<tr>
    <td><code class="highlighter-rouge">patient</code></td>
    <td><code class="highlighter-rouge">reference</code></td>
    <td>The identity of a patient to list encounters for</td>
    <td>MAY</td>
    <td>Encounter.patient <br>(Patient)</td>
</tr>
</table>

<!--
Systems SHOULD support the following search combinations:

 * patient
 -->

{% include custom/search.date.html para="2.1.1." content="Encounter" %}

{% include custom/search.patient.html para="2.1.2." content="Encounter" %}

{% include custom/search.response.html resource="Encounter" %}

## 3. Example ##

### 3.1 Query ###
Return all Encounter resources for Patient with a NHS Number of 9876543210, the format of the response body will be xml. Replace 'baseUrl' with the actual base Url of the FHIR Server.

#### cURL ####

{% include custom/embedcurl.html title="Search Encounter" command="curl -H 'Accept: application/xml+fhir' -H 'Authorization: BEARER [token]' -X GET  '[baseUrl]/Encounter?patient.identifier=https://fhir.nhs.uk/Id/nhs-number|9876543210'" %}

{% include custom/search.response.headers.html resource="Encounter" %}

#### 3.2.2 Http Body ####

<script src="https://gist.github.com/KevinMayfield/cee6d67c0cd3289b22d3e299c77b85f1.js"></script>
