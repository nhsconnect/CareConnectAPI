---
title: Diagnostics | DiagnosticOrder
keywords: getcarerecord, structured, rest, DiagnosticOrder
tags: [rest,fhir,diagnostics,api, diagnosticorder, noccprofile]
sidebar: accessrecord_rest_sidebar
permalink: api_diagnostics_diagnosticorder.html
summary: A record of a request for a diagnostic investigation service to be performed.
---
{% include custom/search.warnbanner.html %}

{% include custom/fhir.reference.nonecc.html resource="DiagnosticOrder" resourceurl="https://nhsconnect.github.io/NHS-FHIR-DDS/Generated/Profile.DDS-Request/dds-request-1.html" page="" fhirname="DiagnosticOrder" fhirlink="DiagnosticOrder.html" content="User Stories" userlink="engage_michaelsstory.html" %}

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

{% include custom/search.parameters.html resource="DiagnosticOrder" link="DiagnosticOrder.html#search" %}

<table style="min-width:100%;width:100%">
<tr id="clinical">
    <th style="width:15%;">Name</th>
    <th style="width:15%;">Type</th>
    <th style="width:40%;">Description</th>
    <th style="width:5%;">Conformance</th>
    <th style="width:25%;">Path</th>
</tr>

<tr>
    <td><code class="highlighter-rouge">patient</code></td>
    <td><code class="highlighter-rouge">reference</code></td>
    <td>Who and/or what test is about</td>
    <td>SHALL</td>
    <td>DiagnosticOrder.subject <br> (Patient)</td>
</tr>
</table>


{% include custom/search.patient.html para="2.1.1." content="DiagnosticOrder" %}

{% include custom/search.response.html resource="DiagnosticOrder" %}


## 3. Example ##

<h3 id="32-response-headers">3.1 cURL</h3>

Return all DiagnosticOrder resources for Patient with a NHS Number of 9876543210, the format of the response body will be xml. Replace 'baseUrl' with the actual base Url of the FHIR Server.

{% include custom/embedcurl.html title="Search DiagnosticOrder" command="curl -X GET -H 'Accept: application/xml+fhir' -H 'Authorisation: BEARER [token]' -v 'http://yellow.testlab.nhs.uk/careconnect-ri/STU3/Condition?patient.identifier=https://fhir.nhs.uk/Id/nhs-number%7C9876543210'" %}


<h3 id="32-response-headers">3.2 Explore the Response</h3>

Explore the response in XML & JSON on the Reference Implementation below
<div class="language-http highlighter-rouge">
<pre class="highlight">
<p style="font-size: 110%;">Reference Implementation</p>
XML <a target="_blank" href="{{ site.fhir_ref_impl }}search?serverId=home&pretty=true&resource=Patient&param.0.qualifier=&param.0.0=https%3A%2F%2Ffhir.nhs.uk%2FId%2Fnhs-number&param.0.1=9876543210&param.0.name=identifier&param.0.type=token&sort_by=&sort_direction=&resource-search-limit=&encoding=xml">Patient NHS number search RI viewer</a>
JSON <a target="_blank" href="{{ site.fhir_ref_impl }}search?serverId=home&pretty=true&resource=Patient&param.0.qualifier=&param.0.0=https%3A%2F%2Ffhir.nhs.uk%2FId%2Fnhs-number&param.0.1=9876543210&param.0.name=identifier&param.0.type=token&sort_by=&sort_direction=&resource-search-limit=&encoding=json">Patient NHS number search RI viewer</a>
</pre>
</div>


