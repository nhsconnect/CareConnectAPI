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

## Read ##

Return a single `FamilyMemberHistory` for the specified id

```http
GET /FamilyMemberHistory/[id]
```

## Search Parameters ##

FamilyMemberHistory resource contains family member history for a patient. Fetches a bundle of all `FamilyMemberHistory` resources for the specified patient.

```http
GET /FamilyMemberHistory?[searchParameters]
```

{% include optional.html content="[FamilyMemberHistory](https://www.hl7.org/fhir/DSTU2/familymemberhistory.html#search)" %}

Provider systems MAY implement the following search parameters (unless indicated with a SHALL):

| Name | Type | Description | SHALL |
| `patient` | `reference` | The identity of a subject to list family member history items for | Y |
| `date` | `date` | Obtained date/time. If the obtained element is a period, a date that falls in the period | Y |
| `gender` | `token` | A search by a gender code of a family member |  |

### patient ###

```TODO```

### date ###

```TODO```


