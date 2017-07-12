---
title: Individuals | Patient
keywords: getcarerecord, structured, rest, patient
tags: [rest, fhir, identification,api]
sidebar: accessrecord_rest_sidebar
permalink: api_entity_patient.html
summary: Demographics and other administrative information about an individual receiving care or other health-related services.
---

{% include custom/search.warnbanner.html %}

{% include custom/fhir.reference.html resource="Patient" page="CareConnect-Patient-1" fhirlink="[Patient](https://www.hl7.org/fhir/DSTU2/patient.html)" content="Bristol Connecting Care POC" userlink="engage_poc_bristolcc.html" %}

## 1. Read ##

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/Patient/[id]</div>

{% include custom/read.response.html resource="Patient" content="" %}


## 2. Search Parameters ##

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/Patient?[searchParameters]</div>
Fetches a bundle of all `Patient` resources for the specified patient or search criteria.

{% include custom/search.header.html resource="Patient" %}

### 2.1. Search Parameters ###

{% include custom/search.parameters.html resource="Patient"     link="https://www.hl7.org/fhir/DSTU2/patient.html#search" %}

<!--
<table style="min-width:100%;width:100%">
<tr id="clinical">
    <th style="width:15%;">Name</th>
    <th style="width:10%;">Type</th>
    <th style="width:40%;">Description</th>
    <th style="width:5%;">Conformance</th>
    <th style="width:30%;">Path</th>
</tr>
<tr>
    <td><code class="highlighter-rouge"></code></td>
    <td><code class="highlighter-rouge"></code></td>
    <td></td>
    <td></td>
    <td></td>
</tr>
<tr>
    <td><code class="highlighter-rouge"></code></td>
    <td><code class="highlighter-rouge"></code></td>
    <td></td>
    <td></td>
    <td></td>
</tr>
</table>
-->

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
<td>Patient.address.postalCode </td>
</tr>
<tr>
<td><code class="highlighter-rouge">birthdate</code></td>
<td><code class="highlighter-rouge">date</code></td>
<td>The patient's date of birth</td>
<td>SHALL</td>
<td>Patient.birthDate</td>
</tr>
<tr>
<td><code class="highlighter-rouge">email</code></td>
<td><code class="highlighter-rouge">token</code></td>
<td>A value in an email contact</td>
<td>MAY</td>
<td>Patient.telecom <br>(system=email)</td>
</tr>
<tr>
<td><code class="highlighter-rouge">family</code></td>
<td><code class="highlighter-rouge">string</code></td>
<td>A portion of the family name of the patient</td>
<td>SHALL</td>
<td>Patient.name.family</td>
</tr>
<tr>
<td><code class="highlighter-rouge">gender</code></td>
<td><code class="highlighter-rouge">token </code></td>
<td>Gender of the patient</td>
<td>SHALL</td>
<td>Patient.gender</td>
</tr>
<tr>
<td><code class="highlighter-rouge">given</code></td>
<td><code class="highlighter-rouge">string</code></td>
<td>A portion of the given name of the patient</td>
<td>SHALL</td>
<td>Patient.name.given</td>
</tr>
<tr>
<td><code class="highlighter-rouge">identifier</code></td>
<td><code class="highlighter-rouge">token</code></td>
<td>A patient identifier (NHS Number, Hospital Number, etc)</td>
<td>SHALL</td>
<td>Patient.identifier</td>
</tr>
<tr>
<td><code class="highlighter-rouge">name </code></td>
<td><code class="highlighter-rouge">string </code></td>
<td>A portion of either family or given name of the patient</td>
<td>SHALL</td>
<td>Patient.name</td>
</tr>
<tr>
<td><code class="highlighter-rouge">phone </code></td>
<td><code class="highlighter-rouge">token </code></td>
<td>A value in a phone contact</td>
<td>MAY</td>
<td>Patient.telecom(system=phone)</td>
</tr>
</table>

Client systems SHALL provide at least two parameters of differing types, unless searching on identifier where one parameter is permitted. Systems SHALL support the following search combinations:

* name + gender
* name + birthdate
* family + gender
* given + gender


<!--
| `address` | `string` | An address in any kind of address/part of the patient |  | Practitioner.address |
| `careprovider` | `reference` | Patient's nominated GP | | Patient.careProvider <br>(Practitioner) |
| `organization` | `reference` | The practice at which this person is a patient | | Patient.managingOrganization <br>(Organization) |
| `telecom` | `token` | The value in any kind of telecom details of the patient |  | Patient.telecom |
-->

{% include custom/search.nopat.string.html para="2.1.1." resource="Patient" content="address-postcode"  example="NG10%201ZZ" text1="Post Code" text2="NG10 1ZZ" %}

{% include custom/search.nopat.date.plus.html para="2.1.2." content="Patient" name="birthdate" %}

{% include custom/search.nopat.string.html para="2.1.3." resource="Patient" content="email"  example="bernie.kanfeld@chumhum.com" text1="email address" text2="bernie.kanfeld@chumhum.com" %}

{% include custom/search.nopat.string.html para="2.1.4." resource="Patient" content="family"  example="kanfeld" text1="surname" text2="Kanfeld" %}

{% include custom/search.nopat.token.html para="2.1.5." resource="Patient" content="gender"  example="female" text1="Administrative Sex" text2="female" %}

{% include custom/search.nopat.string.html para="2.1.6." resource="Patient" content="given"  example="bernie" text1="forename" text2="Bernie" %}

{% include custom/search.nopat.identifier.html para="2.1.7." resource="Patient" content="identifier" subtext="NHS Number, Hospital Number, etc" example="https://fhir.nhs.uk/Id/nhs-number|9876543210" text1="NHS Number" text2="9876543210" %}

{% include custom/search.nopat.string.html para="2.1.8." resource="Patient" content="name"  example="bernie%20kanfeld" text1="name" text2="Bernie Kanfeld" %}

{% include custom/search.nopat.string.html para="2.1.9." resource="Patient" content="phone"  example="07999123456" text1="phone number" text2="07999 123456" %}

{% include custom/search.response.html resource="Patient"  %}

## 3. Example ##

### 3.1 Request Query ###

Return all Patient resources with a NHS Number 9876543210, the format of the response body will be xml. Replace 'baseUrl' with the actual base Url of the FHIR Server.

#### 3.1.1. cURL ####

{% include custom/embedcurl.html title="Search Patient" command="curl -X GET -H 'Accept: application/xml+fhir' -H 'Authorization: BEARER [token]' -v '[baseUrl]/Patient?identifier=https://fhir.nhs.uk/Id/nhs-number|9876543210'" %}

{% include custom/search.response.headers.html resource="Patient"  %}

#### 3.2.2 Http Body ####

<script src="https://gist.github.com/KevinMayfield/93fcc2d0568c92477bafa1fd7ba753f1.js"></script>
