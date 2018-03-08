---
title: Medication | Medication Statement
keywords: usecase, clinical
tags: [fhir, rest, medication, api]
sidebar: foundations_sidebar
permalink: api_medication_medicationstatement.html
summary: A record of a medication that is being consumed by a patient. A MedicationStatement may indicate that the patient may be taking the medication now, or has taken the medication in the past or will be taking the medication in the future.
---
{% include custom/search.warnbanner.html %}

{% include custom/fhir.STU3.reference.html resource="Medication Statement" page="CareConnect-MedicationStatement-1" fhirname="MedicationStatement" fhirlink="medicationstatement.html" content="Bristol Connecting Care POC" userlink="engage_poc_bristolcc.html" %}

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

{% include custom/search.parameters.html resource="MedicationStatement" link="medicationstatement.html#search" %}

<table style="min-width:100%;width:100%">
<tr id="clinical">
    <th style="width:15%;">Name</th>
    <th style="width:10%;">Type</th>
    <th style="width:40%;">Description</th>
    <th style="width:5%;">Conformance</th>
    <th style="width:30%;">Path</th>
</tr>
<tr>
    <td><code class="highlighter-rouge">effective</code></td>
    <td><code class="highlighter-rouge">date</code></td>
    <td>Date when patient was taking (or not taking) the medication</td>
    <td>SHOULD</td>
    <td>MedicationStatement.effective</td>
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

{% include custom/search.date.plus.html para="2.1.1." content="MedicationStatement" name="effective" %}

{% include custom/search.patient.html para="2.1.2" content="MedicationStatement" %}

{% include custom/search.status.html para="2.1.3." content="MedicationStatement" options="active | completed | entered-in-error | intended" selected="active" %}

{% include custom/search.response.html resource="MedicationStatement" %}


## 3. Example ##

### 3.1 Request Query ###

<h3 id="32-response-headers">3.1 cURL</h3>

Return all MedicationStatement resources with an id of 1, the format of the response body will be xml. The Reference Implementation is hosted at '{{ site.fhir_ref_impl }}'.

{% include custom/embedcurl.html title="Search Patient" command="curl -X GET -H 'Accept: application/xml+fhir' -H 'Authorisation: BEARER [token]' -v 'http://yellow.testlab.nhs.uk/careconnect-ri/STU3/MedicationStatement?patient=1'" %}

<h3 id="32-response-headers">3.2 Explore the Response</h3>

Explore the response in XML & JSON on the Reference Implementation below
<div class="language-http highlighter-rouge">
<pre class="highlight">
<p style="font-size: 110%;">Reference Implementation</p>
XML <a target="_blank" href="{{ site.fhir_ref_impl }}search?serverId=home&pretty=true&resource=MedicationStatement&param.0.0=&param.0.1=1&param.0.name=patient&param.0.type=reference&resource-search-limit=&encoding=xml">Patient id search RI viewer</a>
JSON <a target="_blank" href="{{ site.fhir_ref_impl }}search?serverId=home&pretty=true&resource=MedicationStatement&param.0.0=&param.0.1=1&param.0.name=patient&param.0.type=reference&resource-search-limit=&encoding=json">Patient id search RI viewer</a>
</pre>
</div>
