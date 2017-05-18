---
title: Clinical | Medication Statement
keywords: usecase, clinical
tags:
- restful_api
- clinical
- profile
sidebar: foundations_sidebar
permalink: restfulapis_clinical_medicationstatement.html
summary: Clinical Medication Statement
---

## Medication Statement ##

{% include profile.html content="[Care Connect Medication Statement](http://www.interopen.org/candidate-profiles/care-connect/CareConnect-MedicationStatement-1.html)" %}

## Read Operation ##

Return a single `Medication Statement` for the specified id

```http
GET /MedicationStatement/:id
```

```http
GET /MedicationStatement?_id=:id
```


## Search Parameters ##

Medication Statement resource contains current medication information for a patient. Fetches a bundle of all `MedicationStatement` resources for the specified patient.

```http
GET /MedicationStatement?:searchParameters
```

{% include optional.html content="[MedicationStatement](https://www.hl7.org/fhir/DSTU2/medicationstatement.html#search)" %}

Provider systems SHOULD implement the following search parameters:

| Name | Type | Description | Recommended |
| `effectivedate` | `date` | Date when patient was taking (or not taking) the medication | |
| `patient` | `reference` | The identity of a patient to list statements for | Y |
| `status` | `token` | Return statements that match the given status | Y |
| `_revinclude` | `string` | Include referenced resources.  |  |
| `_count` | `number` | The maximum number of results per page. |  |

In order to manage the number of search results returned, the server may choose to return the results in a series of pages. The search result set contains the URLs that the client uses to request additional pages from the search set. For a simple RESTful search, the page links are contained in the returned bundle as links. Please refer to [Paged Search](https://www.hl7.org/fhir/DSTU2/search.html#count){:target="_blank"} for further details.

### patient ###

```TODO```

### active ###

```TODO```

### effectivedate ###

```TODO```