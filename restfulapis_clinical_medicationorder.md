---
title: Clinical | Medication Order
keywords: usecase, medication, order
tags:
- restful_api
- clinical
- profile
sidebar: foundations_sidebar
permalink: restfulapis_clinical_medicationorder.html
summary: Clinical Medication Order
---

## Medication Order ##

{% include tip.html content=" [Care Connect Medication Order](https://fhir-test.nhs.uk/StructureDefinition/careconnect-gpc-medicationorder-1
) Resource." %}

## Read ##

Return a single `MedicationOrder` for the specified id

```http
GET /MedicationOrder/[id]
```

## Search Parameters ##

Medication order resource contains prescription information for a patient. Fetches a bundle of all `MedicationOrder` resources for the specified patient.

```http
GET /MedicationOrder?[searchParameters]
```

{% include moscow.html content="[MedicationOrder](https://www.hl7.org/fhir/DSTU2/medicationorder.html#search)" %}


| Name | Type | Description | SHALL |
|---------|--------|----------------|--------------------|
| `datewritten` | `date` | Return prescriptions written on this date |  |
| `period.[start|end]` | `date` | Return prescriptions issued in this date range | Y |
| `status` | `token` | Status of the prescription | Y |
| `identifier` | `token` | The source system of the prescriptions for  |  |
| `patient` | `reference` | The identity of a patient to list orders for | Y |


{% include search.patient.html content="MedicationOrder" %}

{% include search.status.html content="MedicationOrder" options="active | on-hold | completed | entered-in-error | stopped | draft" selected="active"  %}

### identifier ###

To filter to this list to a specific supplier, we can search for their system identifiers only.

```http
GET /MedicationOrder?patient.identifier=https://fhir.nhs.uk/Id/nhs-number|9876543210&identifier=https://theccg.systemsupplier.co.uk/MedicationOrder|
```

{% include search.date.plus.html content="MedicationOrder" name="datewritten"  %}

{% include search.date.plus.html content="MedicationOrder" name="period.start"  %}

{% include search.date.plus.html content="MedicationOrder" name="period.end]"  %}

### Example ###

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


