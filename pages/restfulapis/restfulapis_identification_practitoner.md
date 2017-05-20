---
title: Identification | Practitioner
keywords: usecase, Practitioner
tags: [rest, fhir, identification]
sidebar: accessrecord_rest_sidebar
permalink: restfulapis_identification_practitoner.html
summary: Practitioner
---

## Practitioner ##

{% include profile.html content="[Care Connect Practitioner](http://www.interopen.org/candidate-profiles/care-connect/CareConnect-Practitioner-1.html)" %}

## Read ##

Return a single `Practitioner` for the specified id

```http
GET /Practitioner/[id]
```

## Search Parameters ##

Practitioner contains the demographics of the clinician. Fetches a bundle of all `Practitioner` resources for the specified search criteria.

```http
GET /Practitioner?[searchParameters]
```

{% include moscow.html content="[Practitioner](https://www.hl7.org/fhir/DSTU2/practitioner.html#search)" %}

| Name | Type | Description | SHALL |
|------|------|-------------|-------|
| `adddress-postcode` | `string` | A postalCode specified in an address |  |
| `identifier` | `token` | 	Any identifier for the practitioner (e.g. GMP/GMC code) | Y |
| `name` | `string` | A portion of the name of the practitioner | |
| `partof` | `reference` | An organization of which this practitioner forms a part | |


### identifier (GMP/GMC Code) ###

```
TODO
```

### address-postcode

```
TODO
```

### name ###

```
TODO
```
