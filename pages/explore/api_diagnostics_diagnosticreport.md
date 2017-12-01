---
title: Diagnostics | DiagnosticReport
keywords: getcarerecord, structured, rest, DiagnosticReport
tags: [rest,fhir,diagnostics,api,noccprofile]
sidebar: accessrecord_rest_sidebar
permalink: api_diagnostics_diagnosticreport.html
summary: The findings and interpretation of diagnostic tests performed on patients, groups of patients, devices, and locations, and/or specimens derived from these. The report includes clinical context such as requesting and provider information, and some mix of atomic results, images, textual and coded interpretations, and formatted representation of diagnostic reports.
---
{% include custom/search.warnbanner.html %}

{% include custom/fhir.reference.nonecc.html resource="DiagnosticReport" resourceurl="https://nhsconnect.github.io/NHS-FHIR-DDS/Generated/Profile.DDS-Report/dds-report-1.html" page="" fhirname="DiagnosticReport" fhirlink="diagnosticreport.html" content="User Stories" userlink="engage_michaelsstory.html" %}

[SKETCH profile. Not official]

## 1. Read Operation ##

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/DiagnosticReport/[id]</div>

{% include custom/read.response.html resource="DiagnosticReport" content="" %}

## 2. Search ##

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/DiagnosticReport?[searchParameters]</div>

Search for all problems and health concerns for a patient. Fetches a bundle of all `DiagnosticReport` resources for the specified patient.

{% include custom/search.header.html resource="DiagnosticReport" %}

### 2.1. Search Parameters ###

{% include custom/search.parameters.html resource="DiagnosticReport" link="DiagnosticReport.html#search" %}

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
    <td>DiagnosticReport.category</td>
</tr>
<tr>
    <td><code class="highlighter-rouge">code</code></td>
    <td><code class="highlighter-rouge">token</code></td>
    <td>The code for the report as a whole, as opposed to codes for the atomic <br> results, which are the names on the observation resource referred to from <br> the result</td>
    <td>SHALL</td>
    <td>DiagnosticReport.code</td>
</tr>
<tr>
    <td><code class="highlighter-rouge">date</code></td>
    <td><code class="highlighter-rouge">date</code></td>
    <td>The clinically relevant time of the report</td>
    <td>SHALL</td>
    <td>DiagnosticReport.effective[x]</td>
</tr>
<tr>
    <td><code class="highlighter-rouge">patient</code></td>
    <td><code class="highlighter-rouge">reference</code></td>
    <td>The subject of the report</td>
    <td>SHALL</td>
    <td>DiagnosticReport.subject <br> (Patient)</td>
</tr>
</table>

Systems SHOULD support the following search combinations:

* patient + category
* patient + category + date
* patient + category + code
* patient + category + code + date

{% include custom/search.status.plus.html para="2.1.1." content="DiagnosticReport" options="see profile/valueset for codes" selected="final" name="category" %}

{% include custom/search.code.html para="2.1.2." content="DiagnosticReport" %}

{% include custom/search.date.html para="2.1.3." content="DiagnosticReport" %}

{% include custom/search.patient.html para="2.1.4." content="DiagnosticReport" %}

{% include custom/search.response.html resource="DiagnosticReport" %}



## 3. Example ##

<h3 id="32-response-headers">3.1 cURL</h3>

Return all DiagnosticReport resources for Patient with a NHS Number of 9876543210, the format of the response body will be xml. Replace 'baseUrl' with the actual base Url of the FHIR Server.

{% include custom/embedcurl.html title="Search DiagnosticReport" command="curl -X GET -H 'Accept: application/xml+fhir' -H 'Authorisation: BEARER [token]' -v 'http://yellow.testlab.nhs.uk/careconnect-ri/STU3/Condition?patient.identifier=https://fhir.nhs.uk/Id/nhs-number%7C9876543210'" %}


<h3 id="32-response-headers">3.2 Explore the Response</h3>

Explore the response in XML & JSON on the Reference Implementation below
<div class="language-http highlighter-rouge">
<pre class="highlight">
<p style="font-size: 110%;">Reference Implementation</p>
XML <a target="_blank" href="{{ site.fhir_ref_impl }}search?serverId=home&pretty=true&resource=Patient&param.0.qualifier=&param.0.0=https%3A%2F%2Ffhir.nhs.uk%2FId%2Fnhs-number&param.0.1=9876543210&param.0.name=identifier&param.0.type=token&sort_by=&sort_direction=&resource-search-limit=&encoding=xml">Patient NHS number search RI viewer</a>
JSON <a target="_blank" href="{{ site.fhir_ref_impl }}search?serverId=home&pretty=true&resource=Patient&param.0.qualifier=&param.0.0=https%3A%2F%2Ffhir.nhs.uk%2FId%2Fnhs-number&param.0.1=9876543210&param.0.name=identifier&param.0.type=token&sort_by=&sort_direction=&resource-search-limit=&encoding=json">Patient NHS number search RI viewer</a>
</pre>
</div>

