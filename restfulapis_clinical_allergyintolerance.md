---
title: Clinical | Allergy Intolerance
keywords: getcarerecord, structured, rest, allergy, intolerance
tags:
- structured
- getcarerecord
sidebar: accessrecord_rest_sidebar
permalink: restfulapis_clinical_allergyintolerance.html
summary: Clinical Allergy Intolerance
---

## Allergy Intolerance ##

{% include profile.html content="[Care Connect Allergy Intolerence](http://www.interopen.org/candidate-profiles/care-connect/CareConnect-AllergyIntolerance-1.html)" %}

## Read ##

Return a single `AllergyIntolerance` for the specified id

```http
GET /AllergyIntolerence/[id]
```

## Search Parameters ##

Search for all allergies for a patient. Fetches a bundle of all `AllergyIntolerance` resources for the specified patient.

```http
GET /AllergyIntollerence?[searchParameters]
```

{% include optional.html content="[AllergyIntolerance](https://www.hl7.org/fhir/DSTU2/allergyintolerance.html#search)" %}

Provider systems MAY implement the following search parameters (unless indicated with a SHALL):

| Name | Type | Description | SHALL |
| `category` | `token` | Category of Substance ||
| `date` | `date` | When recorded || 
| `patient` | `reference` | Who the sensitivity is for | Y | 
| `status` | `token` | Status of AllergyIntolerance	| Y |
| `type` | `token` | Underlying mechanism (if known) ||

### patient ###

TODO

### status ###

TODO

