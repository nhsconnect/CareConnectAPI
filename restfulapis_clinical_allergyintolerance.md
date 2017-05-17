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

## Read Operation ##

Return a single `AllergyIntolerance` for the specified id

```http
GET /AllergyIntolerence/:id
```

```http
GET /AllergyIntolerence?_id=:id
```

## Search Parameters ##

Search for all allergies for a patient. Fetches a bundle of all `AllergyIntolerance` resources for the specified patient.

```http
GET /AllergyIntollerence?:searchParameters
```

{% include optional.html content="[AllergyIntolerance](https://www.hl7.org/fhir/DSTU2/allergyintolerance.html#search)" %}

Provider systems SHOULD implement the following search parameters:

| Name | Type | Description | Recommended |
| `category` | `token` | Category of Substance ||
| `date` | `date` | When recorded || 
| `patient` | `reference` | Who the sensitivity is for | Y | 
| `status` | `token` | Status of AllergyIntolerance	| Y |
| `type` | `token` | Underlying mechanism (if known) ||

In order to manage the number of search results returned, the server may choose to return the results in a series of pages. The search result set contains the URLs that the client uses to request additional pages from the search set. For a simple RESTful search, the page links are contained in the returned bundle as links. Please refer to [Paged Search](https://www.hl7.org/fhir/DSTU2/search.html#count){:target="_blank"} for further details.

### patient ###

TODO

### status ###

TODO

### Multiple Parameters ###

```
TODO
```