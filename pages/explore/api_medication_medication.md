---
title: Medication | Medication
keywords: usecase, medication
tags: [fhir, rest, medication, api]
sidebar: foundations_sidebar
permalink: api_medication_medication.html
summary: This resource is primarily used for the identification and definition of a medication. It covers the ingredients and the packaging for a medication.
---
{% include custom/search.warnbanner.html %}

{% include custom/fhir.STU3.reference.html resource="Medication" page="CareConnect-Medication-1" fhirname="Medication" fhirlink="medication.html" content="User Stories" userlink="engage_michaelsstory.html" %}

## 1. Read ##

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/Medication/[id]</div>

{% include custom/read.response.html resource="Medication" content="" %}

## 2. Search ##

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/Medication?[searchparameters]</div>
Search Medication resources. Returns a bundle of all `Medication` resources for the specified search criteria.

{% include custom/search.header.html resource="Medication" %}

### 2.1. Search Parameters ###

{% include custom/search.parameters.html resource="Medication" link="medication.html#search" %}

<table style="min-width:100%;width:100%">
<tr id="clinical">
    <th style="width:15%;">Name</th>
    <th style="width:10%;">Type</th>
    <th style="width:40%;">Description</th>
    <th style="width:5%;">Conformance</th>
    <th style="width:30%;">Path</th>
</tr>
<tr>
    <td><code class="highlighter-rouge">code</code></td>
    <td><code class="highlighter-rouge">token</code></td>
    <td>Codes that identify this medication</td>
    <td>SHALL</td>
    <td>Medication.code</td>
</tr>
</table>

{% include custom/search.code.medication.html para="2.1.1." content="Medication" %}

{% include custom/search.response.html resource="Medication" %}


## 3. Example ##

### 3.1 Request Query ###

<h3 id="32-response-headers">3.1 cURL</h3>

Return all Medication resources with an SNOMED CT code of 320141001, the format of the response body will be xml. The Reference Implementation is hosted at '{{ site.fhir_ref_impl }}'.

{% include custom/embedcurl.html title="Search Medication" command="curl -X GET -H 'Accept: application/xml+fhir' -H 'Authorisation: BEARER [token]' -v 'http://yellow.testlab.nhs.uk/careconnect-ri/STU3/Medication?code=320141001'" %}

<h3 id="32-response-headers">3.2 Explore the Response</h3>

Explore the response in XML & JSON on the Reference Implementation below
<div class="language-http highlighter-rouge">
<pre class="highlight">
<p style="font-size: 110%;">Reference Implementation</p>
XML <a target="_blank" href="{{ site.fhir_ref_impl }}search?serverId=home&encoding=xml&pretty=true&resource=Medication&param.0.qualifier=&param.0.0=&param.0.1=320141001&param.0.name=code&param.0.type=token&resource-search-limit=&encoding=xml">Mediciation code search RI viewer</a>
JSON <a target="_blank" href="{{ site.fhir_ref_impl }}search?serverId=home&encoding=xml&pretty=true&resource=Medication&param.0.qualifier=&param.0.0=&param.0.1=320141001&param.0.name=code&param.0.type=token&resource-search-limit=&encoding=json">Medication code search RI viewer</a>
</pre>
</div>
