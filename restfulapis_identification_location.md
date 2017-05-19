---
title: Identification | Location
keywords: usecase, location, order
tags:
- structured
- patient
sidebar: accessrecord_rest_sidebar
permalink: restfulapis_identification_location.html
summary: Clinical Location
---

## Location ##

{% include profile.html content="[Care Connect Location](http://www.interopen.org/candidate-profiles/care-connect/CareConnect-Location-1.html)" %}

## Read ##

Return a single `Location` for the specified id

```http
GET /Location/[id]
```

## Search Parameters ##

Location contains the details for the location. Fetches a bundle of all `Location` resources for the specified search criteria.

```http
GET /Location?[searchParameters]
```

{% include optional.html content=" [Location](https://www.hl7.org/fhir/DSTU2/location.html#search)" %}

Provider systems MAY implement the following search parameters (unless indicated with a SHALL):

| Name | Type | Description | SHALL |
| `adddress-postcode` | `string` | A postalCode specified in an address | Y |
| `identifier` | `token` | 	Any identifier for the location (e.g. SDS/ODS code) | Y |
| `name` | `string` | A portion of the name of the location | |


### identifier (SDS/ODS Code) ###

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