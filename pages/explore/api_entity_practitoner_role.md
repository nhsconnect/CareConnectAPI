---
title: Individuals | Practitioner Role
keywords: usecase, Practitioner, PractionerRole, Role
tags: [rest, fhir, identification,api]
sidebar: accessrecord_rest_sidebar
permalink: api_entity_practitioner_role.html
summary: A specific set of Roles/Locations/specialties/services that a practitioner may perform at an organisation for a period of time.
---

{% include custom/search.warnbanner.html %}

{% include custom/fhir.reference.html resource="" page="" fhirname="Practitioner Role" fhirlink="practitionerrole.html" content="" userlink="" %}


## 1. Read ##

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/PractitionerRole/[id]</div>

{% include custom/read.response.html resource="PractitionerRole" content="" %}

## 2. Search ##

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/PractitionerRole?[searchParameters]</div>
Fetches a bundle of all `PractitionerRole` resources for the specified search criteria.

{% include custom/search.header.html resource="PractitionerRole" %}

### 2.1. Search Parameters ###

{% include custom/search.parameters.html resource="Practitioner Role"  link="practitionerrole.html#search" %}

<table style="min-width:100%;width:100%">
<tr id="clinical">
    <th style="width:15%;">Name</th>
    <th style="width:10%;">Type</th>
    <th style="width:40%;">Description</th>
    <th style="width:5%;">Conformance</th>
    <th style="width:30%;">Path</th>
</tr>
<tr>
    <td><code class="highlighter-rouge">organization</code></td>
    <td><code class="highlighter-rouge">reference</code></td>
    <td>The identity of the organisation the practitioner represents / acts on behalf of</td>
    <td>SHALL</td>
    <td>PractitionerRole.organization (Organization)</td>
</tr>
<tr>
    <td><code class="highlighter-rouge">practitioner</code></td>
    <td><code class="highlighter-rouge">reference</code></td>
    <td>Practitioner that is able to provide the defined services for the organisation</td>
    <td>SHALL</td>
    <td>PractitionerRole.practitioner (Practitioner)</td>
</tr>
</table>


{% include custom/search.reference.html para="2.1.1." resource="PractitionerRole" content="organization"  example="1" text1="Organization Id" text2="1" %}

{% include custom/search.reference.html para="2.1.2." resource="PractitionerRole" content="practitioner"  example="1" text1="Practitioner Id" text2="1" %}

{% include custom/search.response.html resource="Practitioner" %}

## 3. Example ##

{% include custom/search.warn_ri_banner.html %}

### 3.1 Request Query ###
Return all PractitionerRole resources with a Practioner Id of 1, the format of the response body will be xml. Replace 'baseUrl' with the actual base Url of the FHIR Server.

#### 3.1.1. cURL ####

{% include custom/embedcurl.html title="Search Practitioner" command="curl -H 'Accept: application/xml+fhir' -H 'Authorization: BEARER [token]' -X GET  '[baseUrl]/PractitionerRole?practitioner=1'" %}

{% include custom/search.response.headers.html resource="Practitioner" %}

#### 3.2.2 Http Body ####

<script src="https://gist.github.com/KevinMayfield/a5325e43f99cd323c3b16f3c87a67de8.js"></script>
