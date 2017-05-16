---
title: Clinical | Immunization
keywords: getcarerecord, structured, rest, immunization
tags: [structured,getcarerecord]
sidebar: accessrecord_rest_sidebar
permalink: restfulapis_clinical_immunization.html
summary: "Clinical Immunization"
---

## Prerequisites ##




## Immunization ##

Search for all immunization resources for a patient. Fetches a bundle of all `Immunization` resources for the specified patient.

This specification describes a single use cases. For complete details and background please see the [Access Record REST Capability Bundle](accessrecord_rest.html).


## Search Parameters ##

Provider systems SHOULD implement all [search parameters for the `Immunization` resource](https://www.hl7.org/fhir/DSTU2/immunization.html#search){:target="_blank"}

Provider systems SHALL implement the following search parameters:

| Name | Type | Description | Paths |
| `date` | `date` | Vaccination (non)-Administration Date | `Immunization.date` |
| `notgiven` | `token` | Administrations which were not given | `Immunization.wasNotGiven` |
| `patient` | `reference` | The patient for the vaccination record | `Immunization.patient (Patient)` |
| `status` | `token` | Immunization event status | `Immunization.status` |
| `vaccine-code` | `token` | Vaccine Product Administered | `Immunization.vaccineCode` |

In order to manage the number of search results returned, the server may choose to return the results in a series of pages. The search result set contains the URLs that the client uses to request additional pages from the search set. For a simple RESTful search, the page links are contained in the returned bundle as links. Please refer to [Paged Search](https://www.hl7.org/fhir/DSTU2/search.html#count){:target="_blank"} for further details.

Provider systems SHALL return an error for any unknown or unsupported parameter inline with the `Prefer: handling=strict` search behavior.

## Prerequisites ##

### Consumer ###

The Consumer system:

- SHALL have previously traced the patient's NHS Number using PDS or an equivalent service.
- SHALL have resolved the patient's logical id on the server using the patient's NHS Number.

## API Usage ##

### Request Operation ###

#### FHIR Relative Request ####

```http
GET /Immunization?patient=[id]{&other search parameters}
```

#### FHIR Absolute Request ####

```http
GET https://[proxy_server]/https://[provider_server]/[fhir_base]/Immunization?patient=[id]{&other search parameters}
```



