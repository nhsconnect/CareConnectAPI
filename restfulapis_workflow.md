---
title: Workflow Overview
keywords: getcarerecord, structured, rest, allergy, intolerance
tags: [structured,getcarerecord]
sidebar: accessrecord_rest_sidebar
permalink: restfulapis_workflow.html
summary: "Workflow Overview"
---

## Workflow Overview ##

Search for all allergies for a patient. Fetches a bundle of all `AllergyIntolerance` resources for the specified patient.

This specification describes a single use cases. For complete details and background please see the [Access Record REST Capability Bundle](accessrecord_rest.html).


## Search Parameters ##

Provider systems SHOULD implement all [search parameters for the `AllergyIntolerance` resource](https://www.hl7.org/fhir/DSTU2/allergyintolerance.html#search){:target="_blank"}

Provider systems SHALL implement the following search parameters:

| Name | Type | Description | Paths |
| `category` | `token` | Category of Substance | `AllergyIntolerance.category` |
| `date` | `date` | When recorded | `AllergyIntolerance.recordedDate` |
| `patient` | `reference` | Who the sensitivity is for | `AllergyIntolerance.patient` |
| `status` | `token` | Status of AllergyIntolerance	| `AllergyIntolerance.status` |
| `type` | `token` | Underlying mechanism (if known) | `AllergyIntolerance.type` |

In order to manage the number of search results returned, the server may choose to return the results in a series of pages. The search result set contains the URLs that the client uses to request additional pages from the search set. For a simple RESTful search, the page links are contained in the returned bundle as links. Please refer to [Paged Search](https://www.hl7.org/fhir/DSTU2/search.html#count){:target="_blank"} for further details.

Provider systems SHALL return an error for any unknown or unsupported parameter inline with the `Prefer: handling=strict` search behavior.

### List Search Mechanism ###

Provider systems SHALL implement [_list](https://www.hl7.org/fhir/DSTU2/search.html#list) search mechanism.

Provider systems SHALL implement the standard [current resource list](https://www.hl7.org/fhir/lifecycle.html#current) for the `AllergyIntolerance` resource:

- `$current-allergies` A list of known or suspected propensities to medications, foods, or environmental agents that is provided to help prevent reactions while care is occurring.
- `$current-drug-allergies` A list of known or suspected propensities to medications that is provided to help prevent reactions while care is occurring. This list is a subset of the full allergies list.

On the RESTful API, this is done using the [list search mechanism](https://www.hl7.org/fhir/DSTU2/search.html#list) as follows:

```http
GET [base]/AllergyIntolerance?patient=[id]&_list=$current-allergies
```

## Prerequisites ##

### Consumer ###

The Consumer system:

- SHALL have previously traced the patient's NHS Number using PDS or an equivalent service.
- SHALL have resolved the patient's logical id on the server using the patient's NHS Number.

## API Usage ##

### Request Operation ###

#### FHIR Relative Request ####

```http
GET /AllergyIntolerance?patient=[id]{&other search parameters}
```

#### FHIR Absolute Request ####

```http
GET https://[proxy_server]/https://[provider_server]/[fhir_base]/AllergyIntolerance?patient=[id]{&other search parameters}
```



