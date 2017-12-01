---
title: Medication | Immunization
keywords: getcarerecord, structured, rest, immunization
tags: [fhir, rest, medication, familymemberhistory,api]
sidebar: accessrecord_rest_sidebar
permalink: api_medication_immunization.html
summary: Describes the event of a patient being administered a vaccination or a record of a vaccination as reported by a patient, a clinician or another party and may include vaccine reaction information and what vaccination protocol was followed.
---
{% include custom/search.warnbanner.html %}

{% include custom/fhir.reference.html resource="Immunization" page="CareConnect-Immunization-1" fhirname="Immunization" fhirlink="immunization.html" content="User Stories" userlink="engage_michaelsstory.html" %}

## 1. Read ##

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/Immunization/[id]</div>

{% include custom/read.response.html resource="Immunization" content="" %}

## 2. Search ##

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/Immunization?[searchParameters]</div>

Search for all immunization resources for a patient. Fetches a bundle of all `Immunization` resources for the specified patient.

{% include custom/search.header.html resource="Immunization" %}

### 2.1. Search Parameters ###

{% include custom/search.parameters.html resource="Immunization" link="immunization.html#search" %}

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
    <td>Vaccination (non)-Administration Date</td>
    <td>SHOULD</td>
    <td>Immunization.date</td>
</tr>
<tr>
    <td><code class="highlighter-rouge">patient</code></td>
    <td><code class="highlighter-rouge">reference</code></td>
    <td>The patient for the vaccination record</td>
    <td>SHALL</td>
    <td>Immunization.patient<br>(Patient)</td>
</tr>
<tr>
    <td><code class="highlighter-rouge">status</code></td>
    <td><code class="highlighter-rouge">token</code></td>
    <td>Immunization event status</td>
    <td>MAY</td>
    <td>Immunization.status</td>
</tr>
</table>

<!--
Systems SHOULD support the following search combinations:

 * patient
-->


<!--
| `dose-sequence` | `number` | Dose number within series |  | 	Immunization.vaccinationProtocol.doseSequence |
| `notgiven` | `token` | Administrations which were not given | | Immunization.wasNotGiven |
| `lot-number` | `string` | Vaccine Batch Number |  | Immunization.lotNumber |
| `vaccine-code` | `token` | Vaccine Product Administered |  | Immunization.vaccineCode |
-->
{% include custom/search.date.html para="2.1.1." content="Immunization" %}

{% include custom/search.patient.html para="2.1.2." content="Immunization" %}

{% include custom/search.status.html para="2.1.3." content="Immunization" options="in-progress | on-hold | completed | entered-in-error | stopped" selected="on-hold" %}

{% include custom/search.response.html resource="Immunization" %}


## 3. Example ##

### 3.1 Request Query ###

<h3 id="32-response-headers">3.1 cURL</h3>

Return all Immunization resources with a NHS Number 9876543210, the format of the response body will be xml. The Reference Implementation is hosted at '{{ site.fhir_ref_impl }}'.

{% include custom/embedcurl.html title="Search Immunization" command="curl -X GET -H 'Accept: application/xml+fhir' -H 'Authorisation: BEARER [token]' -v 'http://yellow.testlab.nhs.uk/careconnect-ri/STU3/Immunization?identifier=https://fhir.nhs.uk/Id/nhs-number%7C9876543210'" %}

<h3 id="32-response-headers">3.2 Explore the Response</h3>

Explore the response in XML & JSON on the Reference Implementation below
<div class="language-http highlighter-rouge">
<pre class="highlight">
<p style="font-size: 110%;">Reference Implementation</p>
XML <a target="_blank" href="{{ site.fhir_ref_impl }}search?serverId=home&pretty=true&resource=Immunization&param.0.qualifier=&param.0.0=https%3A%2F%2Ffhir.nhs.uk%2FId%2Fnhs-number&param.0.1=9876543210&param.0.name=identifier&param.0.type=token&sort_by=&sort_direction=&resource-search-limit=&encoding=xml">Patient NHS number search RI viewer</a>
JSON <a target="_blank" href="{{ site.fhir_ref_impl }}search?serverId=home&pretty=true&resource=Immunization&param.0.qualifier=&param.0.0=https%3A%2F%2Ffhir.nhs.uk%2FId%2Fnhs-number&param.0.1=9876543210&param.0.name=identifier&param.0.type=token&sort_by=&sort_direction=&resource-search-limit=&encoding=json">Patient NHS number search RI viewer</a>
</pre>
</div>

