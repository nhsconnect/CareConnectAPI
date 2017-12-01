---
title: Diagnostics | Observation
keywords: usecase, observation
tags: [observation,fhir,rest,diagnostics,api]
sidebar: foundations_sidebar
permalink: api_diagnostics_observation.html
summary: Measurements and simple assertions made about a patient, device or other subject.
---

{% include custom/search.warnbanner.html %}

{% include custom/fhir.reference.html resource="Observation" page="CareConnect-Observation-1" fhirname="Observation" fhirlink="observation.html" content="User Stories" userlink="engage_michaelsstory.html" %}

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

{% include custom/search.parameters.html resource="Observation" link="observation.html#search" %}

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

<h3 id="32-response-headers">3.1 cURL</h3>

Return all Observation resources for Patient with an id of 1002, the format of the response body will be xml. Replace 'baseUrl' with the actual base Url of the FHIR Server.

{% include custom/embedcurl.html title="Search Observation" command="curl -X GET -H 'Accept: application/xml+fhir' -H 'Authorisation: BEARER [token]' -v 'http://yellow.testlab.nhs.uk/careconnect-ri/STU3/Observation?patient=1002'" %}


<h3 id="32-response-headers">3.2 Explore the Response</h3>

Explore the response in XML & JSON on the Reference Implementation below
<div class="language-http highlighter-rouge">
<pre class="highlight">
<p style="font-size: 110%;">Reference Implementation</p>
XML <a target="_blank" href="{{ site.fhir_ref_impl }}search?serverId=home&pretty=true&resource=Observation&param.0.0=&param.0.1=1002&param.0.name=patient&param.0.type=reference&sort_by=&sort_direction=&resource-search-limit=&encoding=xml">Patient id search RI viewer</a>
JSON <a target="_blank" href="{{ site.fhir_ref_impl }}search?serverId=home&pretty=true&resource=Observation&param.0.0=&param.0.1=1002&param.0.name=patient&param.0.type=reference&sort_by=&sort_direction=&resource-search-limit=&encoding=json">Patient id search RI viewer</a>
</pre>
</div>
