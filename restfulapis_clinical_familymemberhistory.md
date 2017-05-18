---
title: Clinical | Family Member History
keywords: usecase, familymemberhistory
tags:
- restful_api
- use_case
sidebar: foundations_sidebar
permalink: restfulapis_clinical_familymemberhistory.html
summary: Clinical Family Member History
---

## Family Member History ##

{% include profile.html content="[Care Connect Family Member History](http://www.interopen.org/candidate-profiles/care-connect/CareConnect-FamilyMemberHistory-1.html)" %}

## Read Operation ##

Return a single `FamilyMemberHistory` for the specified id

```http
GET /FamilyMemberHistory/:id
```

```http
GET /FamilyMemberHistory?_id=:id
```


## Search Parameters ##

FamilyMemberHistory resource contains family member history for a patient. Fetches a bundle of all `FamilyMemberHistory` resources for the specified patient.

```http
GET /FamilyMemberHistory?:searchParameters
```

{% include optional.html content="[FamilyMemberHistory](https://www.hl7.org/fhir/DSTU2/familymemberhistory.html#search)" %}

Provider systems SHOULD implement the following search parameters:

| Name | Type | Description | Recommended |
| `patient` | `reference` | The identity of a subject to list family member history items for | Y |
| `date` | `date` | Obtained date/time. If the obtained element is a period, a date that falls in the period | Y |
| `gender` | `token` | A search by a gender code of a family member |  |
| `_count` | `number` | The maximum number of results per page. |  |

In order to manage the number of search results returned, the server may choose to return the results in a series of pages. The search result set contains the URLs that the client uses to request additional pages from the search set. For a simple RESTful search, the page links are contained in the returned bundle as links. Please refer to [Paged Search](https://www.hl7.org/fhir/DSTU2/search.html#count){:target="_blank"} for further details.

### patient ###

```TODO```

### date ###

```TODO```


