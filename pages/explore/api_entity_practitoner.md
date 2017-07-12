---
title: Individuals | Practitioner
keywords: usecase, Practitioner
tags: [rest, fhir, identification,api]
sidebar: accessrecord_rest_sidebar
permalink: api_entity_practitoner.html
summary: A person who is directly or indirectly involved in the provisioning of healthcare.
---

{% include custom/search.warnbanner.html %}

{% include custom/fhir.reference.html resource="Practitioner" page="CareConnect-Practitioner-1" fhirlink="[Practitioner](https://www.hl7.org/fhir/DSTU2/practitioner.html)" content="User Stories" userlink="engage_michaelsstory.html" %}


## 1. Read ##

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/Practitioner/[id]</div>

{% include custom/read.response.html resource="Practitioner" content="" %}

## 2. Search ##

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/Practitioner?[searchParameters]</div>
Fetches a bundle of all `Practitioner` resources for the specified search criteria.

{% include custom/search.header.html resource="Practitioner" %}

### 2.1. Search Parameters ###

{% include custom/search.parameters.html resource="Practitioner"     link="https://www.hl7.org/fhir/DSTU2/practitioner.html#search" %}

<table style="min-width:100%;width:100%">
<tr id="clinical">
    <th style="width:15%;">Name</th>
    <th style="width:10%;">Type</th>
    <th style="width:40%;">Description</th>
    <th style="width:5%;">Conformance</th>
    <th style="width:30%;">Path</th>
</tr>
<tr>
    <td><code class="highlighter-rouge">adddress-postcode</code></td>
    <td><code class="highlighter-rouge">string</code></td>
    <td>A postalCode specified in an address</td>
    <td>MAY</td>
    <td>Practitioner.address.postalCode</td>
</tr>
<tr>
    <td><code class="highlighter-rouge">identifier</code></td>
    <td><code class="highlighter-rouge">token</code></td>
    <td>Any identifier for the practitioner (e.g. GMP/GMC code)</td>
    <td>MAY</td>
    <td>Practitioner.identifier</td>
</tr>
</table>

<!--
| `name` | `string` | A portion of the name of the practitioner | | Practitioner.name |
| `organization` | `reference` | The identity of the organization the practitioner represents / acts on behalf of | | Practitioner.practitionerRole.managingOrganization <br>(Organization) |
-->

{% include custom/search.nopat.string.html para="2.1.1." resource="Practitioner" content="address-postcode"  example="NG10%201QQ" text1="Post Code" text2="NG10 1QQ" %}

{% include custom/search.nopat.identifier.html para="2.1.2." resource="Practitioner" content="identifier" subtext="SDS Id or ODS Code" example="https://fhir.nhs.uk/Id/sds-user-id|123456" text1="SDS User ID" text2="123456" %}

<div class="language-http highlighter-rouge">
<pre class="highlight"><code><span class="err">GET [baseUrl]/Practitioner?identifier=https://fhir.nhs.uk/Id/????????|G8133438
</span></code>
Return all Practitioner resources that have a ODS Practitioner/Consultant of G8133438 </pre>
</div>

{% include custom/search.response.html resource="Practitioner" %}

## 3. Example ##

### 3.1 Request Query ###
Return all Practitioner resources with a GP Code of G8133438, the format of the response body will be xml. Replace 'baseUrl' with the actual base Url of the FHIR Server.

#### 3.1.1. cURL ####

{% include custom/embedcurl.html title="Search Practitioner" command="curl -H 'Accept: application/xml+fhir' -H 'Authorization: BEARER [token]' -X GET  '[baseUrl]/Practitioner?identifier=https://fhir.nhs.uk/Id/sds-user-id|G8133438'" %}

{% include custom/search.response.headers.html resource="Practitioner" %}

#### 3.2.2 Http Body ####

<script src="https://gist.github.com/KevinMayfield/742a6c3536c240a3a75c4dd57517d2c9.js"></script>
