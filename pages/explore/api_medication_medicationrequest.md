---
title: Medication | Medication Request
keywords: usecase, medication, order, request, medication request
tags: [fhir, rest,medication,api]
sidebar: foundations_sidebar
permalink: api_medication_medicationrequest.html
summary: An order for both supply of the medication and the instructions for administration of the medication to a patient. The resource is called "MedicationRequest" rather than "MedicationPrescription" to generalize the use across inpatient and outpatient settings as well as for care plans, etc.
---
{% include custom/search.warnbanner.html %}

{% include custom/fhir.reference.html resource="Medication Request" page="CareConnect-MedicationRequest-1" fhirname="MedicationRequest" fhirlink="medicationrequest.html" content="Bristol Connecting Care" userlink="engage_poc_bristolcc.html" %}


## 1. Read ##

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/MedicationRequest/[id]</div>

{% include custom/read.response.html resource="MedicationRequest" content="" %}

## 2. Search ##

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/MedicationRequest?[searchParameters]]</div>

Fetches a bundle of all `MedicationRequest` resources for the specified patient.

{% include custom/search.header.html resource="MedicationRequest" %}

### 2.1. Search Parameters ###

{% include custom/search.parameters.html resource="MedicationRequest" link="medicationrequest.html#search" %}

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
    <td>Return administrations of this medication code</td>
    <td>MAY</td>
    <td>MedicationRequest.medicationCodeableConcept</td>
</tr>
<tr>
    <td><code class="highlighter-rouge">dateWritten</code></td>
    <td><code class="highlighter-rouge">date</code></td>
    <td>Return prescriptions written on this date</td>
    <td>MAY</td>
    <td>MedicationRequest.dateWritten</td>
</tr>
<tr>
    <td><code class="highlighter-rouge">patient</code></td>
    <td><code class="highlighter-rouge">reference</code></td>
    <td>The identity of a patient to list orders for</td>
    <td>SHALL</td>
    <td>MedicationRequest.patient<br>(Patient)</td>
</tr>
<tr>
    <td><code class="highlighter-rouge">status</code></td>
    <td><code class="highlighter-rouge">token</code></td>
    <td>Status of the prescription</td>
    <td>SHOULD</td>
    <td>MedicationRequest.status</td>
</tr>
</table>

Systems SHOULD support the following search combinations:

 * patient + code


{% include custom/search.code.MedicationRequest.html para="2.1.1." content="MedicationRequest" name="code"  %}

{% include custom/search.date.plus.html para="2.1.2." content="MedicationRequest" name="dateWritten"  %}

{% include custom/search.patient.html para="2.1.3." content="MedicationRequest" %}

{% include custom/search.status.html para="2.1.4." content="MedicationRequest" options="active | on-hold | completed | entered-in-error | stopped | draft" selected="active"  %}

{% include custom/search.response.html resource="MedicationRequest" %}

## 3. Example ##

{% include custom/search.warn_ri_banner.html %}


### 3.1 Request Query ###

Return all MedciationOrder resources for Patient with a NHS Number of 9876543210, the format of the response body will be xml. Replace 'baseUrl' with the actual base Url of the FHIR Server.

#### 3.1.1. cURL ####

{% include custom/embedcurl.html title="Search MedicationRequest" command="curl -H 'Accept: application/xml+fhir' -H 'Authorization: BEARER [token]' -X GET  '[baseUrl]/MedicationRequest?patient.identifier=https://fhir.nhs.uk/Id/nhs-number|9876543210'" %}

{% include custom/search.response.headers.html resource="MedicationRequest" %}

#### 3.2.2 Http Body ####

<script src="https://gist.github.com/KevinMayfield/794cc83ac2497bc65d26004cb250fb51.js"></script>
