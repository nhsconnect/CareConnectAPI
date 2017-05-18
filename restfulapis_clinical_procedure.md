---
title: Clinical | Procedure
keywords: usecase, procedure
tags:
- restful_api
- use_case
sidebar: foundations_sidebar
permalink: restfulapis_clinical_procedure.html
summary: Clinical Procedure
---

## Procedure ##

{% include profile.html content="[Care Connect Procedure](http://www.interopen.org/candidate-profiles/care-connect/CareConnect-Procedure-1.html)" %}

## Read Operation ##

Return a single `Procedure` for the specified id

```http
GET /Procedure/:id
```

```http
GET /Procedure?_id=:id
```


## Search Parameters ##

Procedure resource contains procedure information for a patient. Fetches a bundle of all `Procedure` resources for the specified patient.

```http
GET /Procedure?:searchParameters
```

{% include optional.html content="[Procedure](https://www.hl7.org/fhir/DSTU2/procedure.html#search)" %}

Provider systems SHOULD implement the following search parameters:

| Name | Type | Description | Recommended |
| `patient` | `reference` | The identity of a patient to list observations for | Y |
| `date` | `date` | Obtained date/time. If the obtained element is a period, a date that falls in the period | Y |
| `_count` | `number` | The maximum number of results per page. |  |

In order to manage the number of search results returned, the server may choose to return the results in a series of pages. The search result set contains the URLs that the client uses to request additional pages from the search set. For a simple RESTful search, the page links are contained in the returned bundle as links. Please refer to [Paged Search](https://www.hl7.org/fhir/DSTU2/search.html#count){:target="_blank"} for further details.

### patient ###

```TODO```

### date ###

```TODO```


