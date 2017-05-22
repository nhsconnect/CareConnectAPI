---
title: Clinical | Medication Statement
keywords: usecase, clinical
tags: [fhir, rest, clinical, medication]
sidebar: foundations_sidebar
permalink: restfulapis_clinical_medicationstatement.html
summary: Clinical Medication Statement
---

{% include profile.html content="[Care Connect Medication Statement](http://www.interopen.org/candidate-profiles/care-connect/CareConnect-MedicationStatement-1.html)" %}

## Read ##

Return a single `Medication Statement` for the specified id

```http
GET /MedicationStatement/[id]
```

## Search Parameters ##

Medication Statement resource contains current medication information for a patient. Fetches a bundle of all `MedicationStatement` resources for the specified patient.

```http
GET /MedicationStatement?[searchParameters]
```

{% include moscow.html content="[MedicationStatement](https://www.hl7.org/fhir/DSTU2/medicationstatement.html#search)" %}

| Name | Type | Description | SHALL |
|------|------|-------------|-------|
| `effectivedate` | `date` | Date when patient was taking (or not taking) the medication | |
| `patient` | `reference` | The identity of a patient to list statements for | Y |
| `status` | `token` | Return statements that match the given status | Y |

{% include search.patient.html content="MedicationStatement" %}

{% include search.status.html content="MedicationStatement" options="active | completed | entered-in-error | intended" selected="active" %}

{% include search.date.plus.html content="MedicationStatement" name="effectivedate" %}
