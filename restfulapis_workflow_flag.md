---
title: Workflow | Flag
keywords: usecase, flag
tags:
- restful_api
- clinical
- profile
sidebar: foundations_sidebar
permalink: restfulapis_workflow_flag.html
summary: Workflow Flag
---

## Flag ##

{% include profile.html content="[Care Connect Medication Flag](http://www.interopen.org/candidate-profiles/care-connect/CareConnect-Medication-Flag-1.html)" %}

## Read ##

Return a single `Flag` for the specified id

```http
GET /Flag/[id]
```

## Search Parameters ##

Search for all flag (alert) resources for a patient. Fetches a bundle of all `Flag` resources for the specified patient.

```http
GET /Flag?[searchParameters]
```

{% include optional.html content="[Flag](https://www.hl7.org/fhir/DSTU2/flag.html#search)" %}

Provider systems MAY implement the following search parameters (unless indicated with a SHALL):

| Name | Type | Description | SHALL |
| `patient` | `reference` | The patient for the vaccination record | Y |
| `status` | `token` | Flag status: active, inactive or entered-in-error | Y |
| `date` | `date` | Time period when flag is active |  |

### patient ###

```
TODO
```

### status ###

```
TODO
```



