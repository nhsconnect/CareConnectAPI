---
title: Entities | Location
keywords: usecase, location, order
tags: [rest, fhir, identification,api]
sidebar: accessrecord_rest_sidebar
permalink: api_entity_location.html
summary: Details and position information for a physical place where services are provided and resources and participants may be stored, found, contained or accommodated.
---
{% include custom/search.warnbanner.html %}

{% include custom/fhir.STU3.reference.html resource="Location" page="CareConnect-Location-1" fhirname="Location" fhirlink="location.html" content="User Stories" userlink="engage_michaelsstory.html" %}

## 1. Read ##

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/Location/[id]</div>

{% include custom/read.response.html resource="Location" content="" %}

## 2. Search ##

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/Location?[searchParameters]</div>
Fetches a bundle of all `Location` resources for the specified search criteria.

{% include custom/search.header.html resource="Location" %}

### 2.1. Search Parameters ###

{% include custom/search.parameters.html resource="Location" link="location.html#search" %}

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
    <td>Location.address.postalCode</td>
</tr>
<tr>
    <td><code class="highlighter-rouge">identifier</code></td>
    <td><code class="highlighter-rouge">token</code></td>
    <td>Any identifier for the location (e.g. SDS/ODS code)</td>
    <td>MAY</td>
    <td>Location.identifier</td>
</tr>
</table>

{% include custom/search.nopat.string.html para="2.1.1." resource="Location" content="address-postcode"  example="NG10%201RY" text1="Post Code" text2="NG10 1RY" %}

{% include custom/search.nopat.identifier.html para="2.1.2." resource="Location" content="identifier" subtext="SDS/ODS Code" example="https://fhir.nhs.uk/Id/ods-site-code|RTG08" text1="NHS Trust Site" text2="RTG08 (Long Eaton Clinic)" %}

{% include custom/search.response.html resource="Location" %}


## 3. Example ##

<h3 id="32-response-headers">3.1 cURL</h3>

Return all Location resources with a Trust Site code of RTG08, the format of the response body will be xml. Replace 'baseUrl' with the actual base Url of the FHIR Server.

{% include custom/embedcurl.html title="Search Location" command="curl -X GET -H 'Accept: application/xml+fhir' -H 'Authorisation: BEARER [token]' -v 'http://yellow.testlab.nhs.uk/careconnect-ri/STU3/Location?identifier=RTG08'" %}


<h3 id="32-response-headers">3.2 Explore the Response</h3>

Explore the response in XML & JSON on the Reference Implementation below
<div class="language-http highlighter-rouge">
<pre class="highlight">
<p style="font-size: 110%;">Reference Implementation</p>
XML <a target="_blank" href="{{ site.fhir_ref_impl }}search?serverId=home&pretty=true&resource=Location&param.0.qualifier=&param.0.0=&param.0.1=RTG08&param.0.name=identifier&param.0.type=token&resource-search-limit=&encoding=xml">ODS Code search RI viewer</a>
JSON <a target="_blank" href="{{ site.fhir_ref_impl }}search?serverId=home&pretty=true&resource=Location&param.0.qualifier=&param.0.0=&param.0.1=RTG08&param.0.name=identifier&param.0.type=token&resource-search-limit=&encoding=json">ODS Code search RI viewer</a>
</pre>
</div>
