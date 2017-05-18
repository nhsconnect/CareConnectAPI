---
title: Clinical | Observation
keywords: usecase, observation
tags:
- restful_api
- clinical
- profile
sidebar: foundations_sidebar
permalink: restfulapis_clinical_observation.html
summary: Clinical Observation
---

## Observation ##

{% include profile.html content="[Care Connect Observation](http://www.interopen.org/candidate-profiles/care-connect/CareConnect-Observation-1.html)" %}

## Read Operation ##

Return a single `Observation` for the specified id

```http
GET /Observation/:id
```

```http
GET /Observation?_id=:id
```


## Search Parameters ##

Observation resource contains observation or event information for a patient. Fetches a bundle of all `Observation` resources for the specified patient.

```http
GET /Observation?:searchParameters
```

{% include optional.html content="[Observation](https://www.hl7.org/fhir/DSTU2/observation.html#search)" %}

Provider systems SHOULD implement the following search parameters:

| Name | Type | Description | Recommended |
| `code` | `token` | The code of the observation type | Y |
| `patient` | `reference` | The identity of a patient to list observations for | Y |
| `date` | `date` | Obtained date/time. If the obtained element is a period, a date that falls in the period | Y |
| `_count` | `number` | The maximum number of results per page. |  |

In order to manage the number of search results returned, the server may choose to return the results in a series of pages. The search result set contains the URLs that the client uses to request additional pages from the search set. For a simple RESTful search, the page links are contained in the returned bundle as links. Please refer to [Paged Search](https://www.hl7.org/fhir/DSTU2/search.html#count){:target="_blank"} for further details.

### patient ###

```TODO```

### code ###

```TODO```

### date ###

```TODO```


