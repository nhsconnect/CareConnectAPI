---
title: Documents | DocumentReference
keywords: getcarerecord, structured, rest, documentreference
tags: [rest,fhir,documents,api,noccprofile]
sidebar: accessrecord_rest_sidebar
permalink: api_documents_documentreference.html
summary: A DocumentReference resource is used to describe a document that is made available to a healthcare system. A document is some sequence of bytes that is identifiable, establishes its own context (e.g., what subject, author, etc. can be displayed to the user), and has defined update management. The DocumentReference resource can be used with any document format that has a recognized mime type and that conforms to this definition.
---
{% include custom/search.warnbanner.html %}

{% include custom/fhir.referencemin.html resource="DocumentReference" resourceurl= "" page="" fhirname="DocumentReference" fhirlink="documentreference.html" content="User Stories" userlink="" %}

## 1. Read ##

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/DocumentReference/[id]</div>

{% include custom/read.response.html resource="DocumentReference" content="" %}

## 2. Search ##

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/DocumentReference?[searchParameters]</div>

Search for all problems and health concerns for a patient. Fetches a bundle of all `DocumentReference` resources for the specified patient.

{% include custom/search.header.html resource="DocumentReference" %}

### 2.1. Search Parameters ###

{% include custom/search.parameters.html resource="DocumentReference" link="documentreference.html#search" %}

<table style="min-width:100%;width:100%">
<tr id="clinical">
    <th style="width:15%;">Name</th>
    <th style="width:15%;">Type</th>
    <th style="width:30%;">Description</th>
    <th style="width:5%;">Conformance</th>
    <th style="width:35%;">Path</th>
</tr>
<tr>
    <td><code class="highlighter-rouge">created</code></td>
    <td><code class="highlighter-rouge">date</code></td>
    <td>Document creation time</td>
    <td>SHOULD</td>
    <td>DocumentReference.created</td>
</tr>
<tr>
    <td><code class="highlighter-rouge">patient</code></td>
    <td><code class="highlighter-rouge">reference</code></td>
    <td>Who/what is the subject of the document</td>
    <td>SHOULD</td>
    <td>DocumentReference.subject<br>(Patient)</td>
</tr>
<tr>
    <td><code class="highlighter-rouge">period</code></td>
    <td><code class="highlighter-rouge">date</code></td>
    <td>Time of service that is being documented</td>
    <td>SHOULD</td>
    <td>DocumentReference.context.period</td>
</tr>
<tr>
    <td><code class="highlighter-rouge">setting</code></td>
    <td><code class="highlighter-rouge">token</code></td>
    <td>Additional details about where the content was created (e.g. clinical specialty)</td>
    <td>SHOULD</td>
    <td>DocumentReference.context.practiceSetting</td>
</tr>
<tr>
    <td><code class="highlighter-rouge">type</code></td>
    <td><code class="highlighter-rouge">token</code></td>
    <td>Kind of document (SNOMED CT preferred)</td>
    <td>SHOULD</td>
    <td>DocumentReference.type</td>
</tr>
</table>

Systems SHOULD support the following search combinations:

* patient + type + period

{% include custom/search.date.html para="2.1.1." content="DocumentReference" %}

{% include custom/search.patient.html para="2.1.2." content="DocumentReference" %}

{% include custom/search.date.plus.html para="2.1.3." content="DocumentReference" name="period" %}

{% include custom/search.token.html para="2.1.4." content="setting" resource="DocumentReference" text1="type" text2="'Cardiology service (qualifier value)'" example="http://snomed.info/sct|893061000000109" %}

{% include custom/search.token.html para="2.1.5." content="type" resource="DocumentReference" text1="type" text2="'Discharge summary (qualifier value)'" example="http://snomed.info/sct|373942005" %}


{% include custom/search.response.html resource="DocumentReference" %}


## 3. Example ##

<h3 id="32-response-headers">3.1 cURL</h3>

Return all DocumentReference resources for Patient with an id of 1173, the format of the response body will be xml. Replace 'baseUrl' with the actual base Url of the FHIR Server.

{% include custom/embedcurl.html title="Search DocumentReference" command="curl -X GET -H 'Accept: application/xml+fhir' -H 'Authorisation: BEARER [token]' -v 'https://data.developer.nhs.uk/ccri/STU3/DocumentReference?patient=1173'" %}


<h3 id="32-response-headers">3.2 Explore the Response</h3>

Explore the response in XML & JSON on the Reference Implementation below
<div class="language-http highlighter-rouge">
<pre class="highlight">
<p style="font-size: 110%;">Reference Implementation</p>
XML <a target="_blank" href="{{ site.fhir_ref_impl }}search?serverId=home&pretty=true&resource=DocumentReference&param.0.0=&param.0.1=1173&param.0.name=patient&param.0.type=reference&sort_by=&sort_direction=&resource-search-limit=&encoding=xml">Patient id search RI viewer</a>
JSON <a target="_blank" href="{{ site.fhir_ref_impl }}search?serverId=home&pretty=true&resource=DocumentReference&param.0.0=&param.0.1=1173&param.0.name=patient&param.0.type=reference&sort_by=&sort_direction=&resource-search-limit=&encoding=json">Patient id search RI viewer</a>
</pre>
</div>
