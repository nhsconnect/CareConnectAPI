---
title: Workflow | Flag
keywords: usecase, flag
tags: [rest, fhir, workflow,api]
sidebar: foundations_sidebar
permalink: restfulapis_workflow_flag.html
summary: Workflow Flag
---

{% include custom/search.warnbanner.html %}


{% include custom/fhir.referencemin.html resource="Flag" page="CareConnect-Flag-1" fhirlink="[Flag](https://www.hl7.org/fhir/DSTU2/flag.html#search)" content="User Stories" userlink="" %}

## 1. Read ##

<div markdown="span" class="alert alert-success" role="alert">
GET /Flag/[id]</div>

Return a single `Flag` for the specified id


## 2. Search Parameters ##

<div markdown="span" class="alert alert-success" role="alert">
GET /Flag?[searchParameters]</div>

Search for all flag (alert) resources for a patient. Fetches a bundle of all `Flag` resources for the specified patient.

{% include custom/search.parameters.html resource="Flag"     link="https://www.hl7.org/fhir/DSTU2/flag.html#search" %}


| Name | Type | Description | SHALL | Path |
|------|------|-------------|-------|------|
| `date` | `date` | Time period when flag is active |  | Flag.period |
| `patient` | `reference` | The patient for the vaccination record | Y | Flag.subject <br>(Patient) |
| `status` | `token` | Flag status: active, inactive or entered-in-error | Y | Flag.status |


{% include custom/search.patient.html para="2.1." content="Flag" %}

{% include custom/search.status.html para="2.2." content="Flag" options="active | inactive | entered-in-error" selected="active" %}
