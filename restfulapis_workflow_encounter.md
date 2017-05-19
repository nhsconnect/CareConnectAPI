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

## Read ##

Return a single `Encounter` for the specified id

```http
GET /Encounter/[id]
```

## Search Parameters ##

Procedure resource contains encounter information for a patient. Fetches a bundle of all `Encounter` resources for the specified patient.

```http
GET /Encounter?[searchParameters]
```

{% include optional.html content="[Encounter](https://www.hl7.org/fhir/DSTU2/encounter.html#search)" %}

Provider systems MAY implement the following search parameters (unless indicated with a SHALL):

| Name | Type | Description | SHALL |
| `patient` | `reference` | The identity of a patient to list encounters for | Y |
| `date` | `date` | A date within the period the Encounter lasted | |

### patient ###

```TODO```

### date ###

```TODO```



