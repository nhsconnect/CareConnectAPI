---
title: Workflow | Encounter
keywords: usecase, encounter
tags: [rest, fhir, workflow,api]
sidebar: foundations_sidebar
permalink: api_workflow_encounter.html
summary: An interaction between a patient and healthcare provider(s) for the purpose of providing healthcare service(s) or assessing the health status of a patient.
---
{% include custom/search.warnbanner.html %}

{% include custom/fhir.STU3.reference.html resource="Encounter" page="CareConnect-Encounter-1" fhirname="Encounter" fhirlink="encounter.html" content="User Stories" userlink="engage_michaelsstory.html" %}

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

{% include custom/search.parameters.html resource="Encounter" link="encounter.html#search" %}


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

### 3.1 Request Query ###

<h3 id="32-response-headers">3.1 cURL</h3>

Return all Encounter resources with an id of 4, the format of the response body will be xml. The Reference Implementation is hosted at '{{ site.fhir_ref_impl }}'.

{% include custom/embedcurl.html title="Search Patient" command="curl -X GET -H 'Accept: application/xml+fhir' -H 'Authorisation: BEARER [token]' -v 'http://yellow.testlab.nhs.uk/careconnect-ri/STU3/Encounter?patient=4'" %}

<h3 id="32-response-headers">3.2 Explore the Response</h3>

Explore the response in XML & JSON on the Reference Implementation below
<div class="language-http highlighter-rouge">
<pre class="highlight">
<p style="font-size: 110%;">Reference Implementation</p>
XML <a target="_blank" href="{{ site.fhir_ref_impl }}search?serverId=home&pretty=true&resource=Encounter&param.0.0=&param.0.1=4&param.0.name=patient&param.0.type=reference&resource-search-limit=&encoding=xml">Patient id search RI viewer</a>
JSON <a target="_blank" href="{{ site.fhir_ref_impl }}search?serverId=home&pretty=true&resource=Encounter&param.0.0=&param.0.1=4&param.0.name=patient&param.0.type=reference&resource-search-limit=&encoding=json">Patient id search RI viewer</a>
</pre>
</div>
