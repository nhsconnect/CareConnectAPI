---
title: Clinical | Procedure
keywords: usecase, procedure
tags:
- restful_api
- use_case
sidebar: foundations_sidebar
permalink: restfulapis_clinical_procedure.html
summary: Clinical Procedure
---

## Procedure ##

{% include profile.html content="[Care Connect Procedure](http://www.interopen.org/candidate-profiles/care-connect/CareConnect-Procedure-1.html)" %}

## Read ##

Return a single `Procedure` for the specified id

```http
GET /Procedure/[id]
```

## Search Parameters ##

Procedure resource contains procedure information for a patient. Fetches a bundle of all `Procedure` resources for the specified patient.

```http
GET /Procedure?[searchParameters]
```

{% include moscow.html content="[Procedure](https://www.hl7.org/fhir/DSTU2/procedure.html#search)" %}

| Name | Type | Description | SHALL |
|------|------|-------------|-------|
| `patient` | `reference` | The identity of a patient to list observations for | Y |
| `date` | `date` | Obtained date/time. If the obtained element is a period, a date that falls in the period | Y |


{% include search.patient.html content="Procedure" %}

{% include search.date.html content="Procedure" %}


