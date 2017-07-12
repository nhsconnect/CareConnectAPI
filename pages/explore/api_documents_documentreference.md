---
title: Documents | DocumentReference
keywords: getcarerecord, structured, rest, documentreference
tags: [rest,fhir,documents,api,noccprofile]
sidebar: accessrecord_rest_sidebar
permalink: api_documents_documentreference.html
summary: A DocumentReference resource is used to describe a document that is made available to a healthcare system. A document is some sequence of bytes that is identifiable, establishes its own context (e.g., what subject, author, etc. can be displayed to the user), and has defined update management. The DocumentReference resource can be used with any document format that has a recognized mime type and that conforms to this definition.
---
{% include custom/search.warnbanner.html %}

{% include custom/fhir.reference.nonecc.html resource="DocumentReference" resourceurl= "https://data.developer.nhs.uk/fhir/nrls-v1-draft-a/Profile.RecordLocator/nrls-documentreference-1-0.html" page="" fhirlink="[DocumentReference](https://www.hl7.org/fhir/DSTU2/documentreference.html)" content="User Stories" userlink="engage_michaelsstory.html" %}

[SKETCH profile. Not official]

## 1. Read Operation ##

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/DocumentReference/[id]</div>

{% include custom/read.response.html resource="DocumentReference" content="" %}

## 2. Search ##

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/DocumentReference?[searchParameters]</div>

Search for all problems and health concerns for a patient. Fetches a bundle of all `DocumentReference` resources for the specified patient.

{% include custom/search.header.html resource="DocumentReference" %}

### 2.1. Search Parameters ###

{% include custom/search.parameters.html resource="DocumentReference"     link="https://www.hl7.org/fhir/DSTU2/documentreference.html#search" %}

<table style="min-width:100%;width:100%">
<tr id="clinical">
    <th style="width:15%;">Name</th>
    <th style="width:15%;">Type</th>
    <th style="width:30%;">Description</th>
    <th style="width:5%;">Conformance</th>
    <th style="width:35%;">Path</th>
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
    <td><code class="highlighter-rouge">type</code></td>
    <td><code class="highlighter-rouge">token</code></td>
    <td>Kind of document (SNOMED CT if possible)</td>
    <td>SHOULD</td>
    <td>DocumentReference.type</td>
</tr>
</table>

Systems SHOULD support the following search combinations:

* patient + type + period

{% include custom/search.patient.html para="2.1.1." content="DocumentReference" %}

{% include custom/search.date.plus.html para="2.1.2." content="DocumentReference" name="period" %}

{% include custom/search.token.html para="2.1.3." content="type" resource="DocumentReference" text1="type" text2="'End of Life Care Coordination Summary'" example="http://snomed.info/sct|861421000000109" %}


{% include custom/search.response.html resource="DocumentReference" %}

## 3. Example ##

### 3.1 Request Query ###

Return all DocumentReference resources for Patient with a NHS Number of 9876543210, the format of the response body will be xml. Replace 'baseUrl' with the actual base Url of the FHIR Server.

#### 3.1.1. cURL ####

{% include custom/embedcurl.html title="Search DocumentReference" command="curl -H 'Accept: application/xml+fhir' -H 'Authorization: BEARER [token]' -X GET  '[baseUrl]/DocumentReference?patient.identifier=https://fhir.nhs.uk/Id/nhs-number|9876543210'" %}

{% include custom/search.response.headers.html resource="DocumentReference" %}

[TODO Response]
