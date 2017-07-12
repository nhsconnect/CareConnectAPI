---
title: Entities | Organisation
keywords: usecase, Organization
tags: [rest, fhir, identification,api]
sidebar: accessrecord_rest_sidebar
permalink: api_entity_organisation.html
summary: A formally or informally recognized grouping of people or organizations formed for the purpose of achieving some form of collective action. Includes companies, institutions, corporations, departments, community groups, healthcare practice groups, etc.
---
{% include custom/search.warnbanner.html %}

{% include custom/fhir.reference.html resource="Organization" page="CareConnect-Organization-1" fhirlink="[Organization](https://www.hl7.org/fhir/DSTU2/organization.html)" content="User Stories" userlink="engage_michaelsstory.html" %}

## 1. Read ##

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/Organization/[id]</div>

{% include custom/read.response.html resource="Organization" content="" %}

## 2. Search ##

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/Organization?[searchParameters]</div>

Fetches a bundle of all `Organization` resources for the specified search criteria.

{% include custom/search.header.html resource="Organization" %}

### 2.1. Search Parameters ###

{% include custom/search.parameters.html resource="Organization"     link="https://www.hl7.org/fhir/DSTU2/organization.html#search)" %}


<table style="min-width:100%;width:100%">
<tr id="clinical">
    <th style="width:15%;">Name</th>
    <th style="width:10%;">Type</th>
    <th style="width:40%;">Description</th>
    <th style="width:5%;">Conformance</th>
    <th style="width:30%;">Path</th>
</tr>
<tr>
    <td><code class="highlighter-rouge">identifier</code></td>
    <td><code class="highlighter-rouge">token</code></td>
    <td>Any identifier for the organization (e.g. SDS/ODS code)</td>
    <td>MAY</td>
    <td>Organization.identifier</td>
</tr>
<tr>
    <td><code class="highlighter-rouge">name</code></td>
    <td><code class="highlighter-rouge">string</code></td>
    <td>A portion of the organization's name</td>
    <td>MAY</td>
    <td>Organization.name</td>
</tr>
</table>

{% include custom/search.nopat.identifier.html para="2.1.1." resource="Organization" content="identifier" subtext="SDS/ODS Code" example="https://fhir.nhs.uk/Id/ods-organization-code|RTG" text1="NHS Organisation" text2="RTG (Derby Teaching Hospitals NHS Trust)" %}

{% include custom/search.nopat.string.html para="2.1.2." resource="Organization" content="name"  example="Derby%20Teaching%20Hospitals%20NHS%20Trust" text1="Name" text2="Derby Teaching Hospitals NHS Trust" %}


{% include custom/search.response.html resource="Organization" %}

## 3. Example ##

### 3.1 Request Query ###

Return all Organization resources with a ODS Code of C81010, the format of the response body will be xml. Replace 'baseUrl' with the actual base Url of the FHIR Server.

#### 3.1.1. cURL ####

{% include custom/embedcurl.html title="Search Organization" command="curl -H 'Accept: application/xml+fhir' -H 'Authorization: BEARER [token]' -X GET  '[baseUrl]/Organization?identifier=https://fhir.nhs.uk/Id/ods-organization-code|C81010'" %}

{% include custom/search.response.headers.html resource="Organization" %}

#### 3.2.2 Http Body ####

<script src="https://gist.github.com/KevinMayfield/db3d55a9087f924fc712a89c872d33f1.js"></script>
