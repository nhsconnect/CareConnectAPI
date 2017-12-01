---
title: Entities | Organisation
keywords: usecase, Organization
tags: [rest, fhir, identification,api]
sidebar: accessrecord_rest_sidebar
permalink: api_entity_organisation.html
summary: A formally or informally recognized grouping of people or organizations formed for the purpose of achieving some form of collective action. Includes companies, institutions, corporations, departments, community groups, healthcare practice groups, etc.
---
{% include custom/search.warnbanner.html %}

{% include custom/fhir.reference.html resource="Organization" page="CareConnect-Organization-1" fhirname="Organization" fhirlink="organization.html" content="User Stories" userlink="engage_michaelsstory.html" %}

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

{% include custom/search.parameters.html resource="Organization" link="organization.html#search)" %}


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

<h3 id="32-response-headers">3.1 cURL</h3>

Return all Organization resources for Patient with a NHS Number of 9876543210, the format of the response body will be xml. Replace 'baseUrl' with the actual base Url of the FHIR Server.

{% include custom/embedcurl.html title="Search Organization" command="curl -X GET -H 'Accept: application/xml+fhir' -H 'Authorisation: BEARER [token]' -v 'http://yellow.testlab.nhs.uk/careconnect-ri/STU3/Organization?patient.identifier=https://fhir.nhs.uk/Id/nhs-number%7C9876543210'" %}


<h3 id="32-response-headers">3.2 Explore the Response</h3>

Explore the response in XML & JSON on the Reference Implementation below
<div class="language-http highlighter-rouge">
<pre class="highlight">
<p style="font-size: 110%;">Reference Implementation</p>
XML <a target="_blank" href="{{ site.fhir_ref_impl }}search?serverId=home&pretty=true&resource=Organization&param.0.qualifier=&param.0.0=https%3A%2F%2Ffhir.nhs.uk%2FId%2Fnhs-number&param.0.1=9876543210&param.0.name=identifier&param.0.type=token&sort_by=&sort_direction=&resource-search-limit=&encoding=xml">Patient NHS number search RI viewer</a>
JSON <a target="_blank" href="{{ site.fhir_ref_impl }}search?serverId=home&pretty=true&resource=Organization&param.0.qualifier=&param.0.0=https%3A%2F%2Ffhir.nhs.uk%2FId%2Fnhs-number&param.0.1=9876543210&param.0.name=identifier&param.0.type=token&sort_by=&sort_direction=&resource-search-limit=&encoding=json">Patient NHS number search RI viewer</a>
</pre>
</div>
