---
title: Medication | Immunization
keywords: getcarerecord, structured, rest, immunization
tags: [fhir, rest, medication, familymemberhistory,api]
sidebar: accessrecord_rest_sidebar
permalink: api_medication_immunization.html
summary: Describes the event of a patient being administered a vaccination or a record of a vaccination as reported by a patient, a clinician or another party and may include vaccine reaction information and what vaccination protocol was followed.
---
{% include custom/search.warnbanner.html %}

{% include custom/fhir.reference.html resource="Immunization" page="CareConnect-Immunization-1" fhirlink="[Immunization](https://www.hl7.org/fhir/DSTU2/immunization.html)" content="User Stories" userlink="engage_michaelsstory.html" %}

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

{% include custom/search.parameters.html resource="Immunization"     link="https://www.hl7.org/fhir/DSTU2/immunization.html#search" %}

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

Return all Immunization resources for Patient with a NHS Number of 9876543210, the format of the response body will be xml. Replace 'baseUrl' with the actual base Url of the FHIR Server.

#### 3.1.1. cURL ####

{% include custom/embedcurl.html title="Search Immunization" command="curl -H 'Accept: application/xml+fhir' -H 'Authorization: BEARER [token]' -X GET  '[baseUrl]/Immunization?patient.identifier=https://fhir.nhs.uk/Id/nhs-number|9876543210'" %}

{% include custom/search.response.headers.html resource="Immunization" %}

#### 3.2.2 Http Body ####

<script src="https://gist.github.com/KevinMayfield/06b11df3b6e5dac08d0c00155ed01c79.js"></script>
