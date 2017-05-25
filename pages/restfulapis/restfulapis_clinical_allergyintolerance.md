---
title: Clinical | Allergy Intolerance
keywords: getcarerecord, structured, rest, allergy, intolerance
tags: [fhir, clinical, rest, allergyintolerance]
sidebar: accessrecord_rest_sidebar
permalink: restfulapis_clinical_allergyintolerance.html
summary: Clinical Allergy Intolerance
---
{% include search.warnbanner.html %}
{% include profile.html content="[Care Connect Allergy Intolerence](http://www.interopen.org/candidate-profiles/care-connect/CareConnect-AllergyIntolerance-1.html)" %}

## 1. Read ##

<div markdown="span" class="alert alert-success" role="alert">
GET /AllergyIntollerence/[id]</div>

Return a single `AllergyIntolerance` for the specified id.

## 2. Search Parameters ##

<div markdown="span" class="alert alert-success" role="alert">
GET /AllergyIntollerence?[searchParameters]</div>

Search for all allergies for a patient. Fetches a bundle of all `AllergyIntolerance` resources for the specified patient.

{% include moscow.html content="[AllergyIntolerance](https://www.hl7.org/fhir/DSTU2/allergyintolerance.html#search)" %}

| Name | Type | Description | Conformance | Path |
|------|------|-------------|-------------|------|
| `patient` | `reference` | Who the sensitivity is for | SHALL | AllergyIntolerance.patient<br>(Patient) |
| `status` | `token` | Status of AllergyIntolerance	| Y | AllergyIntolerance.status |

{% include search.patient.html para="2.1." content="AllergyIntolerance" %}

{% include search.status.html para="2.2." content="AllergyIntolerance" options="active | unconfirmed | confirmed | inactive | resolved | refuted | entered-in-error" selected="refuted" %}
