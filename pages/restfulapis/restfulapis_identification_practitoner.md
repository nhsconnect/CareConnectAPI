---
title: Identification | Practitioner
keywords: usecase, Practitioner
tags: [rest, fhir, identification]
sidebar: accessrecord_rest_sidebar
permalink: restfulapis_identification_practitoner.html
summary: Practitioner
---

{% include search.warnbanner.html %}
{% include profile.html content="[Care Connect Practitioner](http://www.interopen.org/candidate-profiles/care-connect/CareConnect-Practitioner-1.html)" %}

## Read ##

<div markdown="span" class="alert alert-success" role="alert">
GET /Practitioner/[id]</div>
Return a single `Practitioner` for the specified id

## Search Parameters ##

<div markdown="span" class="alert alert-success" role="alert">
GET /Practitioner?[searchParameters]</div>
Practitioner contains the demographics of the clinician. Fetches a bundle of all `Practitioner` resources for the specified search criteria.

{% include moscow.html content="[Practitioner](https://www.hl7.org/fhir/DSTU2/practitioner.html#search)" %}

| Name | Type | Description | SHALL | Path |
|------|------|-------------|-------|------|
| `adddress-postcode` | `string` | A postalCode specified in an address |  | Practitioner.address.postalCode |
| `identifier` | `token` | 	Any identifier for the practitioner (e.g. GMP/GMC code) | Y | 	Practitioner.identifier |
| `name` | `string` | A portion of the name of the practitioner | | Practitioner.name |
| `organization` | `reference` | The identity of the organization the practitioner represents / acts on behalf of | | Practitioner.practitionerRole.managingOrganization <br>(Organization) |


{% include search.identifier.html resource="Practitioner" content="identifier" subtext="SDS Id or ODS Code" example="https://fhir.nhs.uk/Id/sds-user-id|123456" text1="SDS User ID" text2="123456" %}

<div class="language-http highlighter-rouge">
<pre class="highlight"><code><span class="err">GET /Practitioner?identifier=https://fhir.nhs.uk/Id/????????|G8133438
</span></code>
Return all Practitioner resources that have a ODS Practitioner/Consultant of G8133438 </pre>
</div>
