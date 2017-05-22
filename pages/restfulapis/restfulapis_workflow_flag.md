---
title: Workflow | Flag
keywords: usecase, flag
tags: [rest, fhir, workflow]
sidebar: foundations_sidebar
permalink: restfulapis_workflow_flag.html
summary: Workflow Flag
---

{% include search.warnbanner.html %}
{% include profile.html content="[Care Connect Medication Flag](http://www.interopen.org/candidate-profiles/care-connect/CareConnect-Medication-Flag-1.html)" %}

## Read ##

<div markdown="span" class="alert alert-success" role="alert">
GET /Flag/[id]</div>

Return a single `Flag` for the specified id


## Search Parameters ##

<div markdown="span" class="alert alert-success" role="alert">
GET /Flag?[searchParameters]</div>

Search for all flag (alert) resources for a patient. Fetches a bundle of all `Flag` resources for the specified patient.

{% include moscow.html content="[Flag](https://www.hl7.org/fhir/DSTU2/flag.html#search)" %}

Provider systems MAY implement the following search parameters (unless indicated with a SHALL):

| Name | Type | Description | SHALL |
|------|------|-------------|-------|
| `patient` | `reference` | The patient for the vaccination record | Y |
| `status` | `token` | Flag status: active, inactive or entered-in-error | Y |
| `date` | `date` | Time period when flag is active |  |

{% include search.patient.html content="Flag" %}

{% include search.status.html content="Flag" options="active | inactive | entered-in-error" selected="active" %}
