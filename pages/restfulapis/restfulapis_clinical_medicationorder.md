---
title: Clinical | Medication Order
keywords: usecase, medication, order
tags: [fhir, rest, clinical, medication]
sidebar: foundations_sidebar
permalink: restfulapis_clinical_medicationorder.html
summary: An order for both supply of the medication and the instructions for administration of the medication to a patient. The resource is called "MedicationOrder" rather than "MedicationPrescription" to generalize the use across inpatient and outpatient settings as well as for care plans, etc.
---
{% include custom/search.warnbanner.html %}

{% include custom/profile.html content=" [Care Connect Medication Order](http://www.interopen.org/candidate-profiles/care-connect/CareConnect-MedicationOrder-1.html)" %}

{% include custom/fhir.resource.html content="[MedicationOrder](https://www.hl7.org/fhir/DSTU2/medicationorder.html#search)" %}

## 1. Read ##

<div markdown="span" class="alert alert-success" role="alert">
GET /MedicationOrder/[id]</div>

Return a single `MedicationOrder` for the specified id

## 2. Search Parameters ##

<div markdown="span" class="alert alert-success" role="alert">
GET /MedicationOrder?[searchParameters]]</div>

Medication order resource contains prescription information for a patient. Fetches a bundle of all `MedicationOrder` resources for the specified patient.

{% include custom/moscow.html content="[MedicationOrder](https://www.hl7.org/fhir/DSTU2/medicationorder.html#search)" %}

| Name    | Type   | Description    | Conformance        | Path |
|---------|--------|----------------|--------------------|------|
| `date` | `date` | Returns medication request to be administered on a specific date | Y | MedicationOrder.dosageInstruction.timing.event |
| `patient` | `reference` | The identity of a patient to list orders for | Y | MedicationOrder.patient<br>(Patient) |
| `status` | `token` | Status of the prescription | Y | MedicationOrder.status |

<!--
| `datewritten` | `date` | Return prescriptions written on this date |  | MedicationOrder.dateWritten |
| `identifier` | `token` | The source system of the prescriptions for  |  | MedicationOrder.identifier |
{% include custom/search.date.plus.html content="MedicationOrder" name="datewritten"  %}

{% include custom/search.identifier.html resource="MedicationOrder" content="identifier" subtext="System Filter" example="https://theccg.systemsupplier.co.uk/MedicationOrder|" text1="The CCG System Supplier" text2="not specified" %}
-->
{% include custom/search.date.plus.html para="2.1." content="MedicationOrder" name="date"  %}

{% include custom/search.patient.html para="2.2." content="MedicationOrder" %}

{% include custom/search.status.html para="2.3." content="MedicationOrder" options="active | on-hold | completed | entered-in-error | stopped | draft" selected="active"  %}

### 3. Example ###
