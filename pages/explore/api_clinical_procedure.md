---
title: Clinical | Procedure
keywords: usecase, procedure
tags: [fhir, rest, clinical,api]
sidebar: foundations_sidebar
permalink: api_clinical_procedure.html
summary: An action that is or was performed on a patient. This can be a physical intervention like an operation, or less invasive like counseling or hypnotherapy.
---
{% include custom/search.warnbanner.html %}

{% include custom/fhir.reference.html resource="Procedure" page="CareConnect-Procedure-1" fhirlink="[Procedure](https://www.hl7.org/fhir/DSTU2/procedure.html)" content="User Stories" userlink="engage_michaelsstory.html" %}


## 1. Read ##

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/Procedure/[id]</div>

{% include custom/read.response.html resource="Procedure" content="" %}

## 2. Search ##

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/Procedure?[searchParameters]</div>

Fetches a bundle of all `Procedure` resources for the specified patient.

{% include custom/search.header.html resource="Procedure" %}

### 2.1. Search Parameters ###

{% include custom/search.parameters.html resource="Procedure"     link="https://www.hl7.org/fhir/DSTU2/procedure.html#search" %}

<table style="min-width:100%;width:100%">
<tr id="clinical">
    <th style="width:15%;">Name</th>
    <th style="width:10%;">Type</th>
    <th style="width:40%;">Description</th>
    <th style="width:5%;">Conformance</th>
    <th style="width:30%;">Path</th>
</tr>
<tr>
    <td><code class="highlighter-rouge">date</code></td>
    <td><code class="highlighter-rouge">date</code></td>
    <td>Obtained date/time. If the obtained element is a period, a date that falls in the period</td>
    <td>SHALL</td>
    <td>Procedure.performed[x]</td>
</tr>
<tr>
    <td><code class="highlighter-rouge">patient</code></td>
    <td><code class="highlighter-rouge">reference</code></td>
    <td>Search by subject - a patient</td>
    <td>SHALL</td>
    <td>Procedure.subject <br>(Patient)</td>
</tr>
<tr>
    <td><code class="highlighter-rouge">subject</code></td>
    <td><code class="highlighter-rouge">reference</code></td>
    <td>Search by subject</td>
    <td>MAY</td>
    <td>Procedure.subject<br>(Patient)</td>
</tr>
</table>

Systems SHALL support the following search combinations:

* patient + date


{% include custom/search.date.html para="2.1.1." content="Procedure" %}

{% include custom/search.patient.html para="2.1.2." content="Procedure" %}

{% include custom/search.subject.html para="2.1.3." content="Procedure" %}

{% include custom/search.response.html resource="Procedure" %}

## 3. Example ##

### 3.1 Request Query ###

Return all Procedure resources for Patient with NHS Number of 9876543210, the format of the response body will be xml. Replace 'baseUrl' with the actual base Url of the FHIR Server.

#### 3.1.1. cURL ####

{% include custom/embedcurl.html title="Search Procedure" command="curl -H 'Accept: application/xml+fhir' -H 'Authorization: BEARER [token]' -X GET  '[baseUrl]/Procedure?patient.identifier=https://fhir.nhs.uk/Id/nhs-number|9876543210'" %}

{% include custom/search.response.headers.html resource="Procedure" %}

#### 3.2.2. Http Body ###

<script src="https://gist.github.com/KevinMayfield/767fb7ad59e68d5c94aaf6163993fc11.js"></script>
