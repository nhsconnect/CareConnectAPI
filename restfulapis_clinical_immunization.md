---
title: Clinical | Immunization
keywords: getcarerecord, structured, rest, immunization
tags:
- structured
- getcarerecord
sidebar: accessrecord_rest_sidebar
permalink: restfulapis_clinical_immunization.html
summary: Clinical Immunization
---

## Immunization ##

{% include profile.html content="[Care Connect Immunization](http://www.interopen.org/candidate-profiles/care-connect/CareConnect-Immunization-1.html)" %}

## Read Operation ##

Return a single `Immunization` for the specified id

```http
GET /Immunization/:id
```

```http
GET /Immunization?_id=:id
```

## Search Parameters ##

Search for all immunization resources for a patient. Fetches a bundle of all `Immunization` resources for the specified patient.

```http
GET /Immunization?:searchparameters
```

{% include optional.html content="[Immunization](https://www.hl7.org/fhir/DSTU2/immunization.html#search)" %}

Provider systems SHOULD implement the following search parameters:

| Name | Type | Description | Recommended |
| `date` | `date` | Vaccination (non)-Administration Date | Y |
| `dose-sequence` | `number` | Dose number within series |  |
| `notgiven` | `token` | Administrations which were not given |  |
| `lot-number` | `string` | Vaccine Batch Number | |
| `patient` | `reference` | The patient for the vaccination record | Y |
| `status` | `token` | Immunization event status | |
| `vaccine-code` | `token` | Vaccine Product Administered |  |

In order to manage the number of search results returned, the server may choose to return the results in a series of pages. The search result set contains the URLs that the client uses to request additional pages from the search set. For a simple RESTful search, the page links are contained in the returned bundle as links. Please refer to [Paged Search](https://www.hl7.org/fhir/DSTU2/search.html#count){:target="_blank"} for further details.

### patient ###

```
TODO
```

### date ###

```
TODO
```

### Multiple Parameters ###

```
TODO
```

