---
title: Diagnostics | Observation
keywords: usecase, observation
tags: [observation,fhir,rest,diagnostics,api]
sidebar: foundations_sidebar
permalink: api_diagnostics_observation.html
summary: Measurements and simple assertions made about a patient, device or other subject.
---

{% include custom/search.warnbanner.html %}

{% include custom/fhir.reference.html resource="Observation" page="CareConnect-Observation-1" fhirlink="[Observation](https://www.hl7.org/fhir/DSTU2/observation.html)" content="User Stories" userlink="engage_michaelsstory.html" %}

## 1. Read ##

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/Observation/[id]</div>

{% include custom/read.response.html resource="Observation" content="" %}

## 2. Search ##

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/Observation?[searchParameters]</div>

Fetches a bundle of all `Observation` resources for the specified patient.

{% include custom/search.header.html resource="Observation" %}

### 2.1. Search Parameters ###

{% include custom/search.parameters.html resource="Observation"     link="https://www.hl7.org/fhir/DSTU2/observation.html#search" %}

<table style="min-width:100%;width:100%">
<tr id="clinical">
    <th style="width:15%;">Name</th>
    <th style="width:15%;">Type</th>
    <th style="width:40%;">Description</th>
    <th style="width:5%;">Conformance</th>
    <th style="width:25%;">Path</th>
</tr>
<tr>
    <td><code class="highlighter-rouge">category</code></td>
    <td><code class="highlighter-rouge">token</code></td>
    <td>The classification of the type of observation</td>
    <td>SHOULD</td>
    <td>Observation.category</td>
</tr>
<tr>
    <td><code class="highlighter-rouge">code</code></td>
    <td><code class="highlighter-rouge">token</code></td>
    <td>The code of the observation type</td>
    <td>SHOULD</td>
    <td>Observation.code</td>
</tr>
<tr>
    <td><code class="highlighter-rouge">date</code></td>
    <td><code class="highlighter-rouge">date</code></td>
    <td>Obtained date/time.<br>If the obtained element is a period, a date that falls in the period</td>
    <td>SHALL</td>
    <td>Observation.effective[x]</td>
</tr>
<tr>
    <td><code class="highlighter-rouge">patient</code></td>
    <td><code class="highlighter-rouge">reference</code></td>
    <td>The subject that the observation is about (if patient) </td>
    <td>SHALL</td>
    <td>Observation.subject (Patient)</td>
</tr>
</table>

Systems SHOULD support the following search combinations:

 * patient + category
 * patient + category + date
 * patient + category + code
 * patient + category + code + date


<!-- | `subject` | `reference` | The subject that the observation is about| | Observation.subject (Patient) |
-->

{% include custom/search.status.plus.html para="2.1.1." content="Observation" options="see profile/valueset for codes" selected="exam" name="category" %}

{% include custom/search.code.html para="2.1.2." content="Observation" %}

{% include custom/search.date.html para="2.1.3." content="Observation" %}

{% include custom/search.patient.html para="2.1.4." content="Observation" %}
<!--
{% include custom/search.subject.html para="2.5." content="Observation" %}
-->

{% include custom/search.response.html resource="Observation" %}

## 3. Example ##

### 3.1. Request Query ###

Return all Observation resources for Patient with NHS Number of 9876543210, the format of the response body will be xml. Replace 'baseUrl' with the actual base Url of the FHIR Server.

#### 3.1.1. cURL ####

{% include custom/embedcurl.html title="Search Observation" command="curl -H 'Accept: application/xml+fhir' -H 'Authorization: BEARER [token]' -X GET  '[baseUrl]/Observation?patient.identifier=https://fhir.nhs.uk/Id/nhs-number|9876543210'" %}

 {% include custom/search.response.headers.html resource="Observation" %}

#### 3.2.2. Http Body ###

<script src="https://gist.github.com/KevinMayfield/699d645252f12fb1e48ad5b61d9f6daa.js"></script>
