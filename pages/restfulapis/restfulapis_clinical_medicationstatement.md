---
title: Clinical | Medication Statement
keywords: usecase, clinical
tags: [fhir, rest, clinical, medication]
sidebar: foundations_sidebar
permalink: restfulapis_clinical_medicationstatement.html
summary: Clinical Medication Statement
---
{% include search.warnbanner.html %}
{% include profile.html content="[Care Connect Medication Statement](http://www.interopen.org/candidate-profiles/care-connect/CareConnect-MedicationStatement-1.html)" %}

## 1. Read ##

<div markdown="span" class="alert alert-success" role="alert">
GET /MedicationStatement/[id]</div>
Return a single `Medication Statement` for the specified id.

## 2. Search Parameters ##

<div markdown="span" class="alert alert-success" role="alert">
GET /MedicationStatement?[searchParameters]</div>
Medication Statement resource contains current medication information for a patient. Fetches a bundle of all `MedicationStatement` resources for the specified patient.

{% include moscow.html content="[MedicationStatement](https://www.hl7.org/fhir/DSTU2/medicationstatement.html#search)" %}

| Name | Type | Description | SHALL | Path |
|------|------|-------------|-------|------|
| `effectivedate` | `date` | Date when patient was taking (or not taking) the medication |  | MedicationStatement.effective[x] |
| `patient` | `reference` | The identity of a patient to list statements for | Y | MedicationStatement.patient<br>(Patient) |
| `status` | `token` | Return statements that match the given status | Y | MedicationStatement.status |

{% include search.date.plus.html para="2.1." content="MedicationStatement" name="effectivedate" %}

{% include search.patient.html para="2.2" content="MedicationStatement" %}

{% include search.status.html para="2.3." content="MedicationStatement" options="active | completed | entered-in-error | intended" selected="active" %}
