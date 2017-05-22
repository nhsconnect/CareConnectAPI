---
title: Identification | Location
keywords: usecase, location, order
tags: [rest, fhir, identification]
sidebar: accessrecord_rest_sidebar
permalink: restfulapis_identification_location.html
summary: Identification Location
---

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

{% include moscow.html content=" [Location](https://www.hl7.org/fhir/DSTU2/location.html#search)" %}

| Name | Type | Description | SHALL | Path |
|------|------|-------------|-------|------|
| `adddress-postcode` | `string` | A postalCode specified in an address | Y | Location.address.postalCode |
| `identifier` | `token` | 	Any identifier for the location (e.g. SDS/ODS code) | Y | 	Location.identifier |
| `name` | `string` | A portion of the name of the location | | Location.name |


{% include search.string.html resource="Location" content="address-postcode"  example="NG10%201RY" text1="Post Code" text2="NG10 1RY" %}

{% include search.identifier.html resource="Location" content="identifier" subtext="SDS/ODS Code" example="https://fhir.nhs.uk/Id/????|RTG08" text1="NHS Trust Site" text2="RTG08 (Long Eaton Clinic)" %}
