---
title: Clinical | Immunization
keywords: getcarerecord, structured, rest, immunization
tags: [fhir, rest, clinical, familymemberhistory]
sidebar: accessrecord_rest_sidebar
permalink: restfulapis_clinical_immunization.html
summary: Clinical Immunization
---

## Immunization ##

{% include profile.html content="[Care Connect Immunization](http://www.interopen.org/candidate-profiles/care-connect/CareConnect-Immunization-1.html)" %}

## Read ##

Return a single `Immunization` for the specified id

```http
GET /Immunization/[id]
```

## Search Parameters ##

Search for all immunization resources for a patient. Fetches a bundle of all `Immunization` resources for the specified patient.

```http
GET /Immunization?[searchparameters]
```

{% include moscow.html content="[Immunization](https://www.hl7.org/fhir/DSTU2/immunization.html#search)" %}

| Name | Type | Description | SHALL |
|------|------|-------------|-------|
| `date` | `date` | Vaccination (non)-Administration Date | Y |
| `dose-sequence` | `number` | Dose number within series |  |
| `notgiven` | `token` | Administrations which were not given |  |
| `lot-number` | `string` | Vaccine Batch Number | |
| `patient` | `reference` | The patient for the vaccination record | Y |
| `status` | `token` | Immunization event status | |
| `vaccine-code` | `token` | Vaccine Product Administered |  |

{% include search.patient.html content="Immunization" %}

{% include search.date.html content="Immunization" %}

{% include search.status.html content="Immunization" options="in-progress | on-hold | completed | entered-in-error | stopped" selected="on-hold" %}
