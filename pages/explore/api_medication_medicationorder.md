---
title: Medication | Medication Order
keywords: usecase, medication, order
tags: [fhir, rest,medication,api]
sidebar: foundations_sidebar
permalink: api_medication_medicationorder.html
summary: An order for both supply of the medication and the instructions for administration of the medication to a patient. The resource is called "MedicationOrder" rather than "MedicationPrescription" to generalize the use across inpatient and outpatient settings as well as for care plans, etc.
---
{% include custom/search.warnbanner.html %}

{% include custom/fhir.reference.html resource="Medication Order" page="CareConnect-MedicationOrder-1" fhirlink="[MedicationOrder](https://www.hl7.org/fhir/DSTU2/medicationorder.html)" content="Bristol Connecting Care" userlink="engage_poc_bristolcc.html" %}


## 1. Read ##

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/MedicationOrder/[id]</div>

{% include custom/read.response.html resource="MedicationOrder" content="" %}

## 2. Search ##

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/MedicationOrder?[searchParameters]]</div>

Fetches a bundle of all `MedicationOrder` resources for the specified patient.

{% include custom/search.header.html resource="MedicationOrder" %}

### 2.1. Search Parameters ###

{% include custom/search.parameters.html resource="MedicationOrder"     link="https://www.hl7.org/fhir/DSTU2/medicationorder.html#search" %}

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
    <td>MedicationOrder.medicationCodeableConcept</td>
</tr>
<tr>
    <td><code class="highlighter-rouge">dateWritten</code></td>
    <td><code class="highlighter-rouge">date</code></td>
    <td>Return prescriptions written on this date</td>
    <td>MAY</td>
    <td>MedicationOrder.dateWritten</td>
</tr>
<tr>
    <td><code class="highlighter-rouge">patient</code></td>
    <td><code class="highlighter-rouge">reference</code></td>
    <td>The identity of a patient to list orders for</td>
    <td>SHALL</td>
    <td>MedicationOrder.patient<br>(Patient)</td>
</tr>
<tr>
    <td><code class="highlighter-rouge">status</code></td>
    <td><code class="highlighter-rouge">token</code></td>
    <td>Status of the prescription</td>
    <td>SHOULD</td>
    <td>MedicationOrder.status</td>
</tr>
</table>

Systems SHOULD support the following search combinations:

 * patient + code


{% include custom/search.code.medicationOrder.html para="2.1.1." content="MedicationOrder" name="code"  %}

{% include custom/search.date.plus.html para="2.1.2." content="MedicationOrder" name="dateWritten"  %}

{% include custom/search.patient.html para="2.1.3." content="MedicationOrder" %}

{% include custom/search.status.html para="2.1.4." content="MedicationOrder" options="active | on-hold | completed | entered-in-error | stopped | draft" selected="active"  %}

{% include custom/search.response.html resource="MedicationOrder" %}

## 3. Example ##

### 3.1 Request Query ###

Return all MedciationOrder resources for Patient with a NHS Number of 9876543210, the format of the response body will be xml. Replace 'baseUrl' with the actual base Url of the FHIR Server.

#### 3.1.1. cURL ####

{% include custom/embedcurl.html title="Search MedicationOrder" command="curl -H 'Accept: application/xml+fhir' -H 'Authorization: BEARER [token]' -X GET  '[baseUrl]/MedicationOrder?patient.identifier=https://fhir.nhs.uk/Id/nhs-number|9876543210'" %}

{% include custom/search.response.headers.html resource="MedicationOrder" %}

#### 3.2.2 Http Body ####

<script src="https://gist.github.com/KevinMayfield/794cc83ac2497bc65d26004cb250fb51.js"></script>
