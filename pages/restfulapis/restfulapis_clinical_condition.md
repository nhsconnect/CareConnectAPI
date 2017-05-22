---
title: Clinical | Condition
keywords: getcarerecord, structured, rest, condition
tags: [rest,fhir,condition,clinical]
sidebar: accessrecord_rest_sidebar
permalink: restfulapis_clinical_condition.html
summary: Clinical Condition
---
{% include search.warnbanner.html %}
{% include profile.html content="[Care Connect Condition](http://www.interopen.org/candidate-profiles/care-connect/CareConnect-Condition-1.html)" %}

## Read Operation ##

<div markdown="span" class="alert alert-success" role="alert">
GET /Condition/[id]</div>

Return a single `Condition` for the specified id

## Search Parameters ##

<div markdown="span" class="alert alert-success" role="alert">
GET /Condition?[searchParameters]</div>

Search for all problems and health concerns for a patient. Fetches a bundle of all `Condition` resources for the specified patient.

{% include moscow.html content="[Condition](https://www.hl7.org/fhir/DSTU2/condition.html#search)" %}

| Name | Type | Description | SHALL | Path |
|------|------|-------------|-------|------|
| `category` | `token` | The category of the condition | Y | Condition.category |
| `clinicalstatus` | `token` | The clinical status of the condition | Y | 	Condition.clinicalStatus |
| `code` | `token` | Code for the condition |  | 	Condition.code |
| `date-recorded` | `date` | A date, when the Condition statement was documented |  | Condition.dateRecorded |
| `encounter` | `reference` | Encounter when condition first asserted |  | Condition.encounter<br>(Encounter) |
| `onset` | `date` | Date related onsets (dateTime and Period) |  | Condition.onset[x] |
| `patient` | `reference` | Who has the condition? | Y | Condition.patient<br>(Patient) |
| `severity` | `token` | The severity of the condition |  | Condition.severity |

{% include search.status.plus.html content="Condition" options="active | inactive | relapse | remission | resolved" selected="relapse" name="clinicalstatus" %}

{% include search.code.html content="Condition" %}

{% include search.token.html resource="Condition" content="category"  example="symptom" text1="Category Type" text2="Symptom" %}

{% include search.patient.html content="Condition" %}
