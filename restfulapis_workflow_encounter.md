---
title: Workflow | Encounter
keywords: usecase, encounter
tags:
- restful_api
- use_case
sidebar: foundations_sidebar
permalink: restfulapis_workflow_encounter.html
summary: restfulapis_workflow_encounter
---

## Encounter ##

{% include profile.html content="[Care Connect Encounter](http://www.interopen.org/candidate-profiles/care-connect/CareConnect-Encounter-1.html)" %}

## Read Operation ##

Return a single `Encounter` for the specified id

```http
GET /Encounter/:id
```

```http
GET /Encounter?_id=:id
```


## Search Parameters ##

Procedure resource contains encounter information for a patient. Fetches a bundle of all `Encounter` resources for the specified patient.

```http
GET /Encounter?:searchParameters
```

{% include optional.html content="[Encounter](https://www.hl7.org/fhir/DSTU2/encounter.html#search)" %}

Provider systems SHOULD implement the following search parameters:

| Name | Type | Description | Recommended |
| `patient` | `reference` | The identity of a patient to list encounters for | Y |
| `date` | `date` | A date within the period the Encounter lasted | |
| `_count` | `number` | The maximum number of results per page. |  |

In order to manage the number of search results returned, the server may choose to return the results in a series of pages. The search result set contains the URLs that the client uses to request additional pages from the search set. For a simple RESTful search, the page links are contained in the returned bundle as links. Please refer to [Paged Search](https://www.hl7.org/fhir/DSTU2/search.html#count){:target="_blank"} for further details.

### patient ###

```TODO```

### date ###

```TODO```



