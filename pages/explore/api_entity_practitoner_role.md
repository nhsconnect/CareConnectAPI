---
title: Individuals | Practitioner Role
keywords: usecase, Practitioner, PractionerRole, Role
tags: [rest, fhir, identification,api]
sidebar: accessrecord_rest_sidebar
permalink: api_entity_practitioner_role.html
summary: A specific set of Roles/Locations/specialties/services that a practitioner may perform at an organisation for a period of time.
---

{% include custom/search.warnbanner.html %}

{% include custom/fhir.STU3.reference.html resource="PractitionerRole" page="CareConnect-PractitionerRole-1" fhirname="Practitioner Role" fhirlink="practitionerrole.html" content="" userlink="" %}


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
    <td><code class="highlighter-rouge">identifier</code></td>
    <td><code class="highlighter-rouge">token</code></td>
    <td>A practitioner's Identifier</td>
    <td>SHOULD</td>
    <td>PractitionerRole.identifier</td>
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

{% include custom/search.nopat.identifier.html para="2.1.1." resource="PractitionerRole" content="identifier" subtext="SDS Id or ODS Code" example="https://fhir.nhs.uk/Id/sds-user-id|123456" text1="SDS User ID" text2="123456" %}

{% include custom/search.reference.html para="2.1.2." resource="PractitionerRole" content="organization"  example="1" text1="Organization Id" text2="1" %}

{% include custom/search.reference.html para="2.1.3." resource="PractitionerRole" content="practitioner"  example="1" text1="Practitioner Id" text2="1" %}

{% include custom/search.response.html resource="Practitioner" %}

## 3. Example ##

<h3 id="32-response-headers">3.1 cURL</h3>

Return all PractitionerRole resources for Practitioner with an id of 1, the format of the response body will be xml. Replace 'baseUrl' with the actual base Url of the FHIR Server.

{% include custom/embedcurl.html title="Search PractitionerRole" command="curl -X GET -H 'Accept: application/xml+fhir' -H 'Authorisation: BEARER [token]' -v 'http://yellow.testlab.nhs.uk/careconnect-ri/STU3/PractitionerRole?practitioner=1'" %}


<h3 id="32-response-headers">3.2 Explore the Response</h3>

Explore the response in XML & JSON on the Reference Implementation below
<div class="language-http highlighter-rouge">
<pre class="highlight">
<p style="font-size: 110%;">Reference Implementation</p>
XML <a target="_blank" href="{{ site.fhir_ref_impl }}search?serverId=home&pretty=true&resource=PractitionerRole&param.0.0=&param.0.1=1&param.0.name=practitioner&param.0.type=reference&resource-search-limit=&encoding=xml">Practitioner id search RI viewer</a>
JSON <a target="_blank" href="{{ site.fhir_ref_impl }}search?serverId=home&pretty=true&resource=PractitionerRole&param.0.0=&param.0.1=1&param.0.name=practitioner&param.0.type=reference&resource-search-limit=&encoding=json">Practitioner id search RI viewer</a>
</pre>
</div>
