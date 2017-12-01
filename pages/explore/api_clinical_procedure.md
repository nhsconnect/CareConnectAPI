---
title: Clinical | Procedure
keywords: usecase, procedure
tags: [fhir, rest, clinical,api]
sidebar: foundations_sidebar
permalink: api_clinical_procedure.html
summary: An action that is or was performed on a patient. This can be a physical intervention like an operation, or less invasive like counseling or hypnotherapy.
---
{% include custom/search.warnbanner.html %}

{% include custom/fhir.reference.html resource="Procedure" page="CareConnect-Procedure-1" fhirname="Procedure" fhirlink="procedure.html" content="User Stories" userlink="engage_michaelsstory.html" %}


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

{% include custom/search.parameters.html resource="Procedure" link="procedure.html#search" %}

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

<h3 id="32-response-headers">3.1 cURL</h3>

Return all Procedure resources with an id of 1, the format of the response body will be xml. The Reference Implementation is hosted at '{{ site.fhir_ref_impl }}'.

{% include custom/embedcurl.html title="Search Patient" command="curl -X GET -H 'Accept: application/xml+fhir' -H 'Authorisation: BEARER [token]' -v 'http://yellow.testlab.nhs.uk/careconnect-ri/STU3/Procedure?patient=1'" %}

<h3 id="32-response-headers">3.2 Explore the Response</h3>

Explore the response in XML & JSON on the Reference Implementation below
<div class="language-http highlighter-rouge">
<pre class="highlight">
<p style="font-size: 110%;">Reference Implementation</p>
XML <a target="_blank" href="{{ site.fhir_ref_impl }}search?serverId=home&pretty=true&resource=Procedure&param.0.0=&param.0.1=1&param.0.name=patient&param.0.type=reference&resource-search-limit=&encoding=xml">Patient id search RI viewer</a>
JSON <a target="_blank" href="{{ site.fhir_ref_impl }}search?serverId=home&pretty=true&resource=Procedure&param.0.0=&param.0.1=1&param.0.name=patient&param.0.type=reference&resource-search-limit=&encoding=json">Patient id search RI viewer</a>
</pre>
</div>
