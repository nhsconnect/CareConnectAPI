---
title: Clinical | Medication Flag
keywords: usecase, medication, flag
tags: [fhir, rest, clinical, medication, workflow]
sidebar: foundations_sidebar
permalink: restfulapis_clinical_medicationflag.html
summary: Workflow Medication Flag
---
{% include search.warnbanner.html %}
{% include profile.html content="[Care Connect Medication Flag](http://www.interopen.org/candidate-profiles/care-connect/CareConnect-Medication-Flag-1.html)" %}

{% include note.html content="The API for Medication Flag is the same as Flag" %}

## 1. Read ##

<div markdown="span" class="alert alert-success" role="alert">
GET /Flag/[id]</div>
Return a single `Flag` for the specified id

## 2. Search Parameters ##

<div markdown="span" class="alert alert-success" role="alert">
GET /Flag?[searchparameters]</div>
Search for all flag resources for a patient. Fetches a bundle of all `Flag` resources for the specified patient.

{% include moscow.html content="[Flag](https://www.hl7.org/fhir/DSTU2/flag.html#search)" %}


| Name | Type | Description | SHALL | Path |
|------|------|-------------|-------|------|
| `patient` | `reference` | The patient for the vaccination record | Y | Flag.subject <br>(Patient) |
| `status` | `token` | Flag status: active, inactive or entered-in-error |  | Flag.status

<!--
| `date` | `date` | Time period when flag is active |  | Flag.period|
-->

{% include search.patient.html para="2.1." content="Flag" %}

{% include search.status.html para="2.2." content="Flag" options="active | inactive | entered-in-error" selected="active" %}
