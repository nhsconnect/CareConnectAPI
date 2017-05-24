---
title: Clinical | Medication Order
keywords: usecase, medication, order
tags: [fhir, rest, clinical, medication]
sidebar: foundations_sidebar
permalink: restfulapis_clinical_medicationorder.html
summary: Clinical Medication Order
---
{% include search.warnbanner.html %}
{% include tip.html content=" [Care Connect Medication Order](https://fhir-test.nhs.uk/StructureDefinition/careconnect-gpc-medicationorder-1
) Resource." %}

## 1. Read ##

<div markdown="span" class="alert alert-success" role="alert">
GET /MedicationOrder/[id]</div>

Return a single `MedicationOrder` for the specified id

## 2. Search Parameters ##

<div markdown="span" class="alert alert-success" role="alert">
GET /MedicationOrder?[searchParameters]]</div>

Medication order resource contains prescription information for a patient. Fetches a bundle of all `MedicationOrder` resources for the specified patient.

{% include moscow.html content="[MedicationOrder](https://www.hl7.org/fhir/DSTU2/medicationorder.html#search)" %}

| Name    | Type   | Description    | SHALL              | Path |
|---------|--------|----------------|--------------------|------|
| `date` | `date` | Returns medication request to be administered on a specific date | Y | MedicationOrder.dosageInstruction.timing.event |
| `patient` | `reference` | The identity of a patient to list orders for | Y | MedicationOrder.patient<br>(Patient) |
| `status` | `token` | Status of the prescription | Y | MedicationOrder.status |

<!--
| `datewritten` | `date` | Return prescriptions written on this date |  | MedicationOrder.dateWritten |
| `identifier` | `token` | The source system of the prescriptions for  |  | MedicationOrder.identifier |
{% include search.date.plus.html content="MedicationOrder" name="datewritten"  %}

{% include search.identifier.html resource="MedicationOrder" content="identifier" subtext="System Filter" example="https://theccg.systemsupplier.co.uk/MedicationOrder|" text1="The CCG System Supplier" text2="not specified" %}
-->
{% include search.date.plus.html para="2.1." content="MedicationOrder" name="date"  %}

{% include search.patient.html para="2.2." content="MedicationOrder" %}

{% include search.status.html para="2.3." content="MedicationOrder" options="active | on-hold | completed | entered-in-error | stopped | draft" selected="active"  %}

### 3. Example ###

The search parameters are based around a logical model which is shown below:

{% include image.html
max-width="200px" file="Bristol/Bristol.EntityRelationship.Resource.bmp" alt="Bristol ERD"
caption="MedicationOrder Logical Model" %}

A search on MedicationOrder without the '_Revinclude=*' would return a FHIR [Bundle](https://www.hl7.org/fhir/DSTU2/bundle.html) would return only MedicationOrder resources. This is useful if you already have Patient, Medication and Practitioner data but in most case the calling system or web application won't be. In this case it is useful for all the referenced resources to be returned with the search results.
This is done using the '_Revinclude=*' parameter and the returned search results now include the referenced parameters. The convention is to list the referenced resources before they are referenced (so they can be processed first).

{% include image.html
max-width="200px" file="Bristol/Bristol.searchResults.includeReferenced.bmp" alt="Bristol ERD"
caption="MedicationOrder Search Results" %}

Provider systems:

- SHALL return a `200` **OK** HTTP status code on successful execution of the operation.

```json
TODO
```
