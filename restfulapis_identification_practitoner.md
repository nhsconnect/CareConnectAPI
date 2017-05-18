---
title: Identification | Practitioner
keywords: usecase, Practitioner
tags:
- structured
- patient
sidebar: accessrecord_rest_sidebar
permalink: restfulapis_identification_practitoner.html
summary: Practitioner
---

## Practitioner ##

{% include profile.html content="[Care Connect Practitioner](http://www.interopen.org/candidate-profiles/care-connect/CareConnect-Practitioner-1.html)" %}

## Read Operation ##

Return a single `Practitioner` for the specified id

```http
GET /Practitioner/:id
```

```http
GET /Practitioner?_id=:id
```

## Search Parameters ##

Practitioner contains the demographics of the clinician. Fetches a bundle of all `Practitioner` resources for the specified search criteria.

```http
GET /Practitioner?:searchParameters
```

{% include optional.html content="[Practitioner](https://www.hl7.org/fhir/DSTU2/practitioner.html#search)" %}

Provider systems SHOULD implement the following search parameters:

| Name | Type | Description | Recommended |
| `adddress-postcode` | `string` | A postalCode specified in an address |  |
| `identifier` | `token` | 	Any identifier for the practitioner (e.g. GMP/GMC code) | Y |
| `name` | `string` | A portion of the name of the practitioner | |
| `partof` | `reference` | An organization of which this practitioner forms a part | |


In order to manage the number of search results returned, the server may choose to return the results in a series of pages. The search result set contains the URLs that the client uses to request additional pages from the search set. For a simple RESTful search, the page links are contained in the returned bundle as links. Please refer to [Paged Search](https://www.hl7.org/fhir/DSTU2/search.html#count){:target="_blank"} for further details.



### identifier (GMP/GMC Code) ###

```
TODO
```

### address-postcode

```
TODO
```

### name ###

```
TODO
```