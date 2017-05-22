---
title: Clinical | Condition
keywords: getcarerecord, structured, rest, condition
tags: [rest,fhir,condition,clinical]
sidebar: accessrecord_rest_sidebar
permalink: restfulapis_clinical_condition.html
summary: Clinical Condition
---

{% include profile.html content="[Care Connect Condition](http://www.interopen.org/candidate-profiles/care-connect/CareConnect-Condition-1.html)" %}

## Read Operation ##

Return a single `Condition` for the specified id

```http
GET /Condition/[id]
```

## Search Parameters ##

Search for all problems and health concerns for a patient. Fetches a bundle of all `Condition` resources for the specified patient.

```http
GET /Condition?[searchParameters]
```

{% include moscow.html content="[Condition](https://www.hl7.org/fhir/DSTU2/condition.html#search)" %}

| Name | Type | Description | SHALL |
|------|------|-------------|-------|
| `category` | `token` | The category of the condition | Y |
| `clinicalstatus` | `token` | The clinical status of the condition | Y |
| `code` | `token` | Code for the condition |  |
| `date-recorded` | `date` | A date, when the Condition statement was documented |  |
| `encounter` | `reference` | Encounter when condition first asserted |  |
| `onset` | `date` | Date related onsets (dateTime and Period) |  |
| `patient` | `reference` | Who has the condition? | Y |
| `severity` | `token` | The severity of the condition |  |

{% include search.patient.html content="Condition" %}

{% include search.code.html content="Condition" %}

### category ###

TODO

{% include search.status.plus.html content="Condition" options="active | inactive | relapse | remission | resolved" selected="relapse" name="clinicalstatus" %}
