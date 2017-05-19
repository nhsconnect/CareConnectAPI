---
title: Identification | Organisation
keywords: usecase, Organization
tags:
- structured
- patient
sidebar: accessrecord_rest_sidebar
permalink: restfulapis_identification_organisation.html
summary: Identification Organization
---

## Organization ##

{% include profile.html content="[Care Connect Organization](http://www.interopen.org/candidate-profiles/care-connect/CareConnect-Organization-1.html)" %}

## Read ##

Return a single `Organization` for the specified id

```http
GET /Organization/[id]
```

## Search Parameters ##

Organization contains the demographics for the organisation. Fetches a bundle of all `Organization` resources for the specified search criteria.

```http
GET /Organization?[searchParameters]
```

{% include optional.html content="[Organization](https://www.hl7.org/fhir/DSTU2/organization.html#search)" %}

Provider systems MAY implement the following search parameters (unless indicated with a SHALL):

| Name | Type | Description | SHALL |
| `adddress-postcode` | `string` | A postalCode specified in an address | Y |
| `identifier` | `token` | 	Any identifier for the organization (e.g. SDS/ODS code) | Y |
| `name` | `string` | A portion of the name of the organisation | |


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