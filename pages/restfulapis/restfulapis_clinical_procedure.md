---
title: Clinical | Procedure
keywords: usecase, procedure
tags: [fhir, rest, clinical]
sidebar: foundations_sidebar
permalink: restfulapis_clinical_procedure.html
summary: Clinical Procedure
---
{% include search.warnbanner.html %}
{% include profile.html content="[Care Connect Procedure](http://www.interopen.org/candidate-profiles/care-connect/CareConnect-Procedure-1.html)" %}

## Read ##

<div markdown="span" class="alert alert-success" role="alert">
GET /Procedure/[id]</div>
Return a single `Procedure` for the specified id

## Search Parameters ##

<div markdown="span" class="alert alert-success" role="alert">
GET /Procedure?[searchParameters]</div>

Procedure resource contains procedure information for a patient. Fetches a bundle of all `Procedure` resources for the specified patient.

{% include moscow.html content="[Procedure](https://www.hl7.org/fhir/DSTU2/procedure.html#search)" %}

| Name | Type | Description | SHALL | Path |
|------|------|-------------|-------|------|
| `date` | `date` | Obtained date/time. If the obtained element is a period, a date that falls in the period | Y | Procedure.performed[x] |
| `patient` | `reference` | The identity of a patient to list observations for | Y | Procedure.subject <br>(Patient) |

{% include search.date.html content="Procedure" %}

{% include search.patient.html content="Procedure" %}
