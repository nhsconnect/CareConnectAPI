---
title: Medication | Medication Request
keywords: usecase, medication, order, request, medication request
tags: [fhir, rest,medication,api]
sidebar: foundations_sidebar
permalink: api_medication_medicationrequest.html
summary: An order for both supply of the medication and the instructions for administration of the medication to a patient. The resource is called "MedicationRequest" rather than "MedicationPrescription" to generalize the use across inpatient and outpatient settings as well as for care plans, etc.
---
{% include custom/search.warnbanner.html %}

{% include custom/fhir.STU3.reference.html resource="Medication Request" page="CareConnect-MedicationRequest-1" fhirname="MedicationRequest" fhirlink="medicationrequest.html" content="Bristol Connecting Care" userlink="engage_poc_bristolcc.html" %}


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
    <td><code class="highlighter-rouge">authoredon</code></td>
    <td><code class="highlighter-rouge">date</code></td>
    <td>Return prescriptions written on this date</td>
    <td>MAY</td>
    <td>MedicationRequest.authoredOn</td>
</tr>
<!--
<tr>
    <td><code class="highlighter-rouge">code</code></td>
    <td><code class="highlighter-rouge">token</code></td>
    <td>Return administrations of this medication code</td>
    <td>MAY</td>
    <td>MedicationRequest.medicationCodeableConcept</td>
</tr> -->

<tr>
    <td><code class="highlighter-rouge">medication</code></td>
    <td><code class="highlighter-rouge">reference</code></td>
    <td>Return prescriptions of this medication reference</td>
    <td>SHALL</td>
    <td>MedicationRequest.medicationReference</td>
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


{% include custom/search.date.plus.html para="2.1.1." content="MedicationRequest" name="authoredon"  %}

<!-- {% include custom/search.code.medicationRequest.html para="2.1.2." content="MedicationRequest" name="code"  %} -->

{% include custom/search.reference.html para="2.1.2." content="medication" resource="MedicationRequest" example="1" text1="id" text2="1" %}

{% include custom/search.patient.html para="2.1.3." content="MedicationRequest" %}

{% include custom/search.status.html para="2.1.4." content="MedicationRequest" options="active | on-hold | completed | entered-in-error | stopped | draft" selected="active"  %}

{% include custom/search.response.html resource="MedicationRequest" %}


## 3. Example ##

### 3.1 Request Query ###

<h3 id="32-response-headers">3.1 cURL</h3>

Return all MedicationRequest resources with an id of 1, the format of the response body will be xml. The Reference Implementation is hosted at '{{ site.fhir_ref_impl }}'.

{% include custom/embedcurl.html title="Search MedicationRequest" command="curl -X GET -H 'Accept: application/xml+fhir' -H 'Authorisation: BEARER [token]' -v 'http://yellow.testlab.nhs.uk/careconnect-ri/STU3/MedicationRequest?patient=1'" %}

<h3 id="32-response-headers">3.2 Explore the Response</h3>

Explore the response in XML & JSON on the Reference Implementation below
<div class="language-http highlighter-rouge">
<pre class="highlight">
<p style="font-size: 110%;">Reference Implementation</p>
XML <a target="_blank" href="{{ site.fhir_ref_impl }}search?serverId=home&pretty=true&resource=MedicationRequest&param.0.0=&param.0.1=1&param.0.name=patient&param.0.type=reference&resource-search-limit=&encoding=xml">Patient id search RI viewer</a>
JSON <a target="_blank" href="{{ site.fhir_ref_impl }}search?serverId=home&pretty=true&resource=MedicationRequest&param.0.0=&param.0.1=1&param.0.name=patient&param.0.type=reference&resource-search-limit=&encoding=json">Patient id search RI viewer</a>
</pre>
</div>
