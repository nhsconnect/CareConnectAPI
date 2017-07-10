---
title: Diagnostics | DiagnosticOrder
keywords: getcarerecord, structured, rest, DiagnosticOrder
tags: [rest,fhir,diagnostics,api, diagnosticorder, noccprofile]
sidebar: accessrecord_rest_sidebar
permalink: api_diagnostics_diagnosticorder.html
summary: A record of a request for a diagnostic investigation service to be performed.
---
{% include custom/search.warnbanner.html %}

{% include custom/fhir.reference.nonecc.html resource="DiagnosticOrder" resourceurl="https://nhsconnect.github.io/NHS-FHIR-DDS/Generated/Profile.DDS-Request/dds-request-1.html" page="" fhirlink="[DiagnosticOrder](https://www.hl7.org/fhir/DSTU2/DiagnosticOrder.html)" content="User Stories" userlink="engage_michaelsstory.html" %}

[SKETCH profile. Not official]

## 1. Read Operation ##

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/DiagnosticOrder/[id]</div>

{% include custom/read.response.html resource="DiagnosticOrder" content="" %}

## 2. Search ##

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/DiagnosticOrder?[searchParameters]</div>

Search for all problems and health concerns for a patient. Fetches a bundle of all `DiagnosticOrder` resources for the specified patient.

{% include custom/search.header.html resource="DiagnosticOrder" %}

### 2.1. Search Parameters ###

{% include custom/search.parameters.html resource="DiagnosticOrder"     link="https://www.hl7.org/fhir/DSTU2/DiagnosticOrder.html#search" %}

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
    <td>Which diagnostic discipline/department created the report</td>
    <td>SHALL</td>
    <td>DiagnosticOrder.category</td>
</tr>
<tr>
    <td><code class="highlighter-rouge">code</code></td>
    <td><code class="highlighter-rouge">token</code></td>
    <td>The code for the report as a whole, as opposed to codes for the atomic <br> results, which are the names on the observation resource referred to from <br> the result</td>
    <td>SHALL</td>
    <td>DiagnosticOrder.code</td>
</tr>
<tr>
    <td><code class="highlighter-rouge">date</code></td>
    <td><code class="highlighter-rouge">date</code></td>
    <td>The clinically relevant time of the report</td>
    <td>SHALL</td>
    <td>DiagnosticOrder.effective[x]</td>
</tr>
<tr>
    <td><code class="highlighter-rouge">patient</code></td>
    <td><code class="highlighter-rouge">reference</code></td>
    <td>The subject of the report</td>
    <td>SHALL</td>
    <td>DiagnosticOrder.subject <br> (Patient)</td>
</tr>
</table>

Systems SHOULD support the following search combinations:

* patient + category
* patient + category + date
* patient + category + code
* patient + category + code + date

{% include custom/search.status.plus.html para="2.1.1." content="DiagnosticOrder" options="see profile/valueset for codes" selected="final" name="category" %}

{% include custom/search.code.html para="2.1.2." content="DiagnosticOrder" %}

{% include custom/search.date.html para="2.1.3." content="DiagnosticOrder" %}

{% include custom/search.patient.html para="2.1.4." content="DiagnosticOrder" %}


{% include custom/search.response.html resource="DiagnosticOrder" %}

## 3. Example ##

### 3.1 Request Query ###

Return all DiagnosticOrder resources for Patient with a NHS Number of 9876543210, the format of the response body will be xml. Replace 'baseUrl' with the actual base Url of the FHIR Server.

#### 3.1.1. cURL ####

{% include custom/embedcurl.html title="Search DiagnosticOrder" command="curl -H 'Accept: application/xml+fhir' -H 'Authorization: BEARER [token]' -X GET  '[baseUrl]/DiagnosticOrder?patient.identifier=https://fhir.nhs.uk/Id/nhs-number|9876543210'" %}

{% include custom/search.response.headers.html resource="DiagnosticOrder" %}

[TODO Response]
