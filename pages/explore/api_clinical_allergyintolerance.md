---
title: Clinical | Allergy Intolerance
keywords: getcarerecord, structured, rest, allergy, intolerance
tags: [fhir, clinical, allergyintolerance, rest, api]
sidebar: accessrecord_rest_sidebar
permalink: api_clinical_allergyintolerance.html
summary: Risk of harmful or undesirable, physiological response which is unique to an individual and associated with exposure to a substance.
---
{% include custom/search.warnbanner.html %}

{% include custom/fhir.reference.html resource="Allergy Intolerance" page="CareConnect-AllergyIntolerance-1" fhirlink="[AllergyIntolerance](https://www.hl7.org/fhir/DSTU2/allergyintolerance.html)" content="User Stories" userlink="engage_michaelsstory.html" %}

## 1. Read ##

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/AllergyIntollerence/[id]</div>

{% include custom/read.response.html resource="AllergyIntolerance" content="" %}

## 2. Search ##

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/AllergyIntollerence?[searchParameters]</div>

Search for all allergies for a patient. Fetches a bundle of all `AllergyIntolerance` resources for the specified patient.

{% include custom/search.header.html resource="Allergy Intolerance" %}

### 2.1. Search Parameters ###

{% include custom/search.parameters.html resource="AllergyIntolerance"     link="https://www.hl7.org/fhir/DSTU2/allergyintolerance.html#search" %}

<table style="min-width:100%;width:100%">
<tr id="clinical">
    <th style="width:10%;">Name</th>
    <th style="width:15%;">Type</th>
    <th style="width:30%;">Description</th>
    <th style="width:5%;">Conformance</th>
    <th style="width:40%;">Path</th>
</tr>
<tr>
    <td><code class="highlighter-rouge">date</code></td>
    <td><code class="highlighter-rouge">date</code></td>
    <td>When recorded</td>
    <td>MAY</td>
    <td>AllergyIntolerance.recordedDate</td>
</tr>
<tr>
    <td><code class="highlighter-rouge">patient</code></td>
    <td><code class="highlighter-rouge">reference</code></td>
    <td>Who the sensitivity is for</td>
    <td>SHALL</td>
    <td>AllergyIntolerance.patient<br>(Patient)</td>
</tr>
<tr>
    <td><code class="highlighter-rouge">status</code></td>
    <td><code class="highlighter-rouge">token</code></td>
    <td>Status of AllergyIntolerance</td>
    <td>MAY</td>
    <td>AllergyIntolerance.status</td>
</tr>
</table>

<!--
Systems SHALL support the following search combinations:

* patient
-->

{% include custom/search.date.plus.html para="2.1.1." content="AllergyIntolerance" name="date" %}

{% include custom/search.patient.html para="2.1.2." content="AllergyIntolerance" %}

{% include custom/search.status.html para="2.1.3." content="AllergyIntolerance" options="active | unconfirmed | confirmed | inactive | resolved | refuted | entered-in-error" selected="refuted" %}

{% include custom/search.response.html resource="AllergyIntolerance" %}

## 3. Example ##

### 3.1 Request Query ###

Return all AllergyIntolerance resources for Patient with a NHS Number of 9876543210, the format of the response body will be xml. Replace 'baseUrl' with the actual base Url of the FHIR Server.

#### 3.1.1. cURL ####

{% include custom/embedcurl.html title="Search AllergyIntolerance" command="curl -X GET -H 'Accept: application/xml+fhir' -H 'Authorization: BEARER [token]'  '[baseUrl]/AllergyIntolerance?patient.identifier=https://fhir.nhs.uk/Id/nhs-number|9876543210'"  %}

{% include custom/search.response.headers.html resource="AllergyIntolerance" %}

#### 3.2.2 Http Body ####

<script src="https://gist.github.com/KevinMayfield/03827faae7031ca963dcc2b15fce450b.js"></script>
