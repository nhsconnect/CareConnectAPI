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

## 1. Read Operation ##

<div markdown="span" class="alert alert-success" role="alert">
GET /Condition/[id]</div>

Return a single `Condition` for the specified id

## 2. Search Parameters ##

<div markdown="span" class="alert alert-success" role="alert">
GET /Condition?[searchParameters]</div>

Search for all problems and health concerns for a patient. Fetches a bundle of all `Condition` resources for the specified patient.

{% include moscow.html content="[Condition](https://www.hl7.org/fhir/DSTU2/condition.html#search)" %}

| Name | Type | Description | SHALL | Path |
|------|------|-------------|-------|------|
| `category` | `token` | The category of the condition | Y | Condition.category |
| `clinicalstatus` | `token` | The clinical status of the condition | Y | 	Condition.clinicalStatus |
| `date-recorded` | `date` | A date, when the Condition statement was documented |  | Condition.dateRecorded |
| `patient` | `reference` | Who has the condition? | Y | Condition.patient<br>(Patient) |

{% include search.status.plus.html para="2.1." content="Condition" options="
complaint | symptom | finding | diagnosis | problem | need" selected="symptom" name="category" %}

{% include search.status.plus.html para="2.2." content="Condition" options="active | inactive | relapse | remission | resolved" selected="relapse" name="clinicalstatus" %}

{% include search.date.plus.html para="2.3." content="Condition" name="date-recorded" %}

{% include search.patient.html para="2.4." content="Condition" %}
