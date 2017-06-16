---
title: PCC | Medication
keywords: development
tags: [design,development]
sidebar: overview_sidebar
permalink: design_pcc_medication.html
summary: "Guidance on FHIR Medication resources and DM+D"
---

{% include custom/search.warnbanner.html %}

{% include custom/ihe.reference.html apicontent="[Medication](restfulapis_clinical_medication.html) <br> [MedicationOrder](restfulapis_clinical_medicationorder.html) <br>  [MedicationStatement](restfulapis_clinical_medicationstatement.html)" %}

## 1. Overview ##

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
