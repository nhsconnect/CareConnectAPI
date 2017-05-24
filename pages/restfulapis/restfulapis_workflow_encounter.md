---
title: Workflow | Encounter
keywords: usecase, encounter
tags: [rest, fhir, workflow]
sidebar: foundations_sidebar
permalink: restfulapis_workflow_encounter.html
summary: Workflow Encounter
---
{% include search.warnbanner.html %}
{% include profile.html content="[Care Connect Encounter](http://www.interopen.org/candidate-profiles/care-connect/CareConnect-Encounter-1.html)" %}

## 1. Read ##

<div markdown="span" class="alert alert-success" role="alert">
GET /Encounter/[id]</div>
Return a single `Encounter` for the specified id

## 2. Search Parameters ##

<div markdown="span" class="alert alert-success" role="alert">
GET /Encounter?[searchParameters]</div>

Procedure resource contains encounter information for a patient. Fetches a bundle of all `Encounter` resources for the specified patient.

{% include moscow.html content="[Encounter](https://www.hl7.org/fhir/DSTU2/encounter.html#search)" %}

| Name | Type | Description | SHALL | Path |
|------|------|-------------|-------|------|
| `date` | `date` | A date within the period the Encounter lasted | | Encounter.period |
| `patient` | `reference` | The identity of a patient to list encounters for | Y | Encounter.patient <br>(Patient) |

{% include search.date.html para="2.1." content="Encounter" %}

{% include search.patient.html para="2.2." content="Encounter" %}
