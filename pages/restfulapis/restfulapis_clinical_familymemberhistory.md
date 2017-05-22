---
title: Clinical | Family Member History
keywords: usecase, familymemberhistory
tags: [familymemberhistory,fhir,rest,clinical]
sidebar: foundations_sidebar
permalink: restfulapis_clinical_familymemberhistory.html
summary: Clinical Family Member History
---

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

{% include moscow.html content="[FamilyMemberHistory](https://www.hl7.org/fhir/DSTU2/familymemberhistory.html#search)" %}

| Name | Type | Description | SHALL |
|------|------|-------------|-------|
| `patient` | `reference` | The identity of a subject to list family member history items for | Y |
| `date` | `date` | Obtained date/time. If the obtained element is a period, a date that falls in the period | Y |
| `gender` | `token` | A search by a gender code of a family member |  |

{% include search.patient.html content="FamilyMemberHistory" %}

{% include search.date.html content="FamilyMemberHistory" %}
