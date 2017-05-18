---
title: Clinical | Condition
keywords: getcarerecord, structured, rest, condition
tags:
- structured
- getcarerecord
sidebar: accessrecord_rest_sidebar
permalink: restfulapis_clinical_condition.html
summary: Clinical Condition
---

## Condition ##

{% include profile.html content="[Care Connect Condition](http://www.interopen.org/candidate-profiles/care-connect/CareConnect-Condition-1.html)" %}

## Read Operation ##

Return a single `Condition` for the specified id

```http
GET /Condition/:id
```

```http
GET /Condition?_id=:id
```

## Search Parameters ##

Search for all problems and health concerns for a patient. Fetches a bundle of all `Condition` resources for the specified patient.

```http
GET /Condition?:searchParameters
```

{% include optional.html content="[Condition](https://www.hl7.org/fhir/DSTU2/condition.html#search)" %}

Provider systems SHOULD implement the following search parameters:

| Name | Type | Description | Recommended |
| `category` | `token` | The category of the condition | Y |
| `clinicalstatus` | `token` | The clinical status of the condition | Y |
| `code` | `token` | Code for the condition |  |
| `date-recorded` | `date` | A date, when the Condition statement was documented |  |
| `encounter` | `reference` | Encounter when condition first asserted |  |
| `onset` | `date` | Date related onsets (dateTime and Period) |  |
| `patient` | `reference` | Who has the condition? | Y |
| `severity` | `token` | The severity of the condition |  |

In order to manage the number of search results returned, the server may choose to return the results in a series of pages. The search result set contains the URLs that the client uses to request additional pages from the search set. For a simple RESTful search, the page links are contained in the returned bundle as links. Please refer to [Paged Search](https://www.hl7.org/fhir/DSTU2/search.html#count){:target="_blank"} for further details.

Provider systems SHALL return an error for any unknown or unsupported parameter inline with the `Prefer: handling=strict` search behavior.

### patient ###

TODO

### category ###

TODO

### clinicalstatus ###

TODO

### Multiple Parameters ###

```
TODO
```