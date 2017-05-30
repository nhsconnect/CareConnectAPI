---
title: Clinical | Medication Statement
keywords: usecase, clinical
tags: [fhir, rest, clinical, medication]
sidebar: foundations_sidebar
permalink: restfulapis_clinical_medicationstatement.html
summary: A record of a medication that is being consumed by a patient. A MedicationStatement may indicate that the patient may be taking the medication now, or has taken the medication in the past or will be taking the medication in the future.
---
{% include custom/search.warnbanner.html %}

{% include custom/profile.html content="[Care Connect Medication Statement](http://www.interopen.org/candidate-profiles/care-connect/CareConnect-MedicationStatement-1.html)" %}

{% include custom/fhir.resource.html content="[MedicationStatement](https://www.hl7.org/fhir/DSTU2/medicationstatement.html#search)" %}

## 1. Read ##

<div markdown="span" class="alert alert-success" role="alert">
GET /MedicationStatement/[id]</div>
Return a single `Medication Statement` for the specified id.

## 2. Search Parameters ##

<div markdown="span" class="alert alert-success" role="alert">
GET /MedicationStatement?[searchParameters]</div>
Medication Statement resource contains current medication information for a patient. Fetches a bundle of all `MedicationStatement` resources for the specified patient.

{% include custom/moscow.html content="[MedicationStatement](https://www.hl7.org/fhir/DSTU2/medicationstatement.html#search)" %}

| Name | Type | Description | Conformance  | Path |
|------|------|-------------|-------|------|
| `effectivedate` | `date` | Date when patient was taking (or not taking) the medication |  | MedicationStatement.effective[x] |
| `patient` | `reference` | The identity of a patient to list statements for | Y | MedicationStatement.patient<br>(Patient) |
| `status` | `token` | Return statements that match the given status | Y | MedicationStatement.status |

{% include custom/search.date.plus.html para="2.1." content="MedicationStatement" name="effectivedate" %}

{% include custom/search.patient.html para="2.2" content="MedicationStatement" %}

{% include custom/search.status.html para="2.3." content="MedicationStatement" options="active | completed | entered-in-error | intended" selected="active" %}
