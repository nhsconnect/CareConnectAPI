---
title: Clinical | Condition
keywords: getcarerecord, structured, rest, condition
tags: [rest,fhir,condition,clinical,api]
sidebar: accessrecord_rest_sidebar
permalink: api_clinical_condition.html
summary: Use to record detailed information about conditions, problems or diagnoses recognized by a clinician. There are many uses e.g. recording a diagnosis during an encounter; populating a problem list or a summary statement, such as a discharge summary.
---
{% include custom/search.warnbanner.html %}

{% include custom/fhir.STU3.reference.html resource="Condition" page="CareConnect-Condition-1" fhirname="Condition" fhirlink="condition.html" content="User Stories" userlink="engage_michaelsstory.html" %}


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

{% include custom/search.parameters.html resource="Condition" link="condition.html#search" %}

<table style="min-width:100%;width:100%">
<tr id="clinical">
    <th style="width:15%;">Name</th>
    <th style="width:15%;">Type</th>
    <th style="width:35%;">Description</th>
    <th style="width:5%;">Conformance</th>
    <th style="width:30%;">Path</th>
</tr>
<tr>
    <td><code class="highlighter-rouge">asserted-date</code></td>
    <td><code class="highlighter-rouge">date</code></td>
    <td>Date record was believed accurate</td>
    <td>MAY</td>
    <td>Condition.assertedDate</td>
</tr>
<tr>
    <td><code class="highlighter-rouge">category</code></td>
    <td><code class="highlighter-rouge">token</code></td>
    <td>The category of the condition</td>
    <td>SHOULD</td>
    <td>Condition.category</td>
</tr>
<tr>
    <td><code class="highlighter-rouge">clinical-status</code></td>
    <td><code class="highlighter-rouge">token</code></td>
    <td>The clinical status of the condition</td>
    <td>SHOULD</td>
    <td>Condition.clinicalStatus</td>
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

* patient + clinical-status
* patient + category

{% include custom/search.date.plus.html para="2.1.1." content="Condition" name="asserted-date" %}

{% include custom/search.status.plus.html para="2.1.2." content="Condition" options="
complaint | symptom | finding | diagnosis | problem | need" selected="symptom" name="category" %}

{% include custom/search.status.plus.html para="2.1.3." content="Condition" options="active | inactive | relapse | remission | resolved" selected="relapse" name="clinical-status" %}


{% include custom/search.patient.html para="2.1.4." content="Condition" %}

{% include custom/search.response.html resource="Condition" %}


## 3. Example ##

<h3 id="32-response-headers">3.1 cURL</h3>

Return all Condition resources for Patient with an id of 1, the format of the response body will be xml. Replace 'baseUrl' with the actual base Url of the FHIR Server.

{% include custom/embedcurl.html title="Search Condition" command="curl -X GET -H 'Accept: application/xml+fhir' -H 'Authorisation: BEARER [token]' -v 'http://yellow.testlab.nhs.uk/careconnect-ri/STU3/Condition?patient=1'" %}


<h3 id="32-response-headers">3.2 Explore the Response</h3>

Explore the response in XML & JSON on the Reference Implementation below
<div class="language-http highlighter-rouge">
<pre class="highlight">
<p style="font-size: 110%;">Reference Implementation</p>
XML <a target="_blank" href="{{ site.fhir_ref_impl }}search?serverId=home&pretty=true&resource=Condition&param.0.0=&param.0.1=1&param.0.name=patient&param.0.type=reference&resource-search-limit=&encoding=xml">Patient id search RI viewer</a>
JSON <a target="_blank" href="{{ site.fhir_ref_impl }}search?serverId=home&pretty=true&resource=Condition&param.0.0=&param.0.1=1&param.0.name=patient&param.0.type=reference&resource-search-limit=&encoding=json">Patient id search RI viewer</a>
</pre>
</div>
