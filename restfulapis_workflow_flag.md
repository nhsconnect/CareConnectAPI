---
title: Workflow | Flag
keywords: usecase, flag
tags:
- restful_api
- clinical
- profile
sidebar: foundations_sidebar
permalink: restfulapis_workflow_flag.html
summary: Workflow Flag
---

## Flag ##

{% include profile.html content="[Care Connect Medication Flag](http://www.interopen.org/candidate-profiles/care-connect/CareConnect-Medication-Flag-1.html)" %}

## Read Operation ##

Return a single `Flag` for the specified id

```http
GET /Flag/:id
```

```http
GET /Flag?_id=:id
```

## Search Parameters ##

Search for all flag (alert) resources for a patient. Fetches a bundle of all `Flag` resources for the specified patient.

```http
GET /Flag?:searchparameters
```

{% include optional.html content="[Flag](https://www.hl7.org/fhir/DSTU2/flag.html#search)" %}

Provider systems SHOULD implement the following search parameters:

| Name | Type | Description | Recommended |
| `patient` | `reference` | The patient for the vaccination record | Y |
| `status` | `token` | Flag status: active, inactive or entered-in-error | Y |
| `date` | `date` | Time period when flag is active |  |

In order to manage the number of search results returned, the server may choose to return the results in a series of pages. The search result set contains the URLs that the client uses to request additional pages from the search set. For a simple RESTful search, the page links are contained in the returned bundle as links. Please refer to [Paged Search](https://www.hl7.org/fhir/DSTU2/search.html#count){:target="_blank"} for further details.

### patient ###

```
TODO
```

### status ###

```
TODO
```



