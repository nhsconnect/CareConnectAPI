---
title: Identification | Organisation
keywords: usecase, Organization
tags: [rest, fhir, identification]
sidebar: accessrecord_rest_sidebar
permalink: restfulapis_identification_organisation.html
summary: Identification Organization
---

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

{% include moscow.html content="[Organization](https://www.hl7.org/fhir/DSTU2/organization.html#search)" %}

| Name | Type | Description | SHALL | Path |
|------|------|-------------|-------|------|
| `adddress-postcode` | `string` | A postalCode specified in an address | Y | Organization.address.postalCode |
| `identifier` | `token` | 	Any identifier for the organization (e.g. SDS/ODS code) | Y | Organization.identifier |
| `name` | `string` | A portion of the name of the organisation | | Organization.name |

{% include search.string.html resource="Organization" content="address-postcode"  example="DE22%203NE" text1="Post Code" text2="DE22 3NE" %}

{% include search.identifier.html resource="Organization" content="identifier" subtext="SDS/ODS Code" example="https://fhir.nhs.uk/Id/ods-organization-code|RTG" text1="NHS Organisation" text2="RTG (Derby Teaching Hospitals NHS Trust)" %}
