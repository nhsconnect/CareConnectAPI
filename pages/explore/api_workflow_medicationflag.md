---
title: Workflow | Medication Flag
keywords: usecase, medication, flag
tags: [fhir, rest, medication, workflow, api]
sidebar: foundations_sidebar
permalink: api_medication_medicationflag.html
summary: Prospective warnings of potential medication issues when providing care to the patient.
---
{% include custom/search.warnbanner.html %}

{% include custom/fhir.reference.html resource="Medication Flag" page="CareConnect-Medication-Flag-1" fhirlink="[Flag](https://www.hl7.org/fhir/DSTU2/flag.html)" content="User Stories" userlink="engage_michaelsstory.html" %}



{% include note.html content="The API for Medication Flag is the same as Flag" %}

## 1. Read ##

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/Flag/[id]</div>

{% include custom/read.response.html resource="Flag" content="" %}

## 2. Search ##

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/Flag?[searchparameters]</div>
Search for all flag resources for a patient. Fetches a bundle of all `Flag` resources for the specified patient.

{% include custom/search.header.html resource="Flag" %}

### 2.1. Search Parameters ###

{% include custom/search.parameters.html resource="Flag"     link="https://www.hl7.org/fhir/DSTU2/flag.html#search" %}


| Name | Type | Description | Conformance | Path |
|------|------|-------------|-------|------|
| `patient` | `reference` | The patient for the vaccination record | SHOULD | Flag.subject <br>(Patient) |
| `status` | `token` | Flag status: active, inactive or entered-in-error | MAY | Flag.status

<!--
| `date` | `date` | Time period when flag is active |  | Flag.period|
-->

{% include custom/search.patient.html para="2.1.1." content="Flag" %}

{% include custom/search.status.html para="2.1.2." content="Flag" options="active | inactive | entered-in-error" selected="active" %}

{% include custom/search.response.html resource="Flag" %}
