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

## Read Operation ##

Return a single `Organization` for the specified id

```http
GET /Organization/:id
```

```http
GET /Organization?_id=:id
```

## Search Parameters ##

Organization contains the demographics for the organisation. Fetches a bundle of all `Organization` resources for the specified search criteria.

```http
GET /Organization?:searchParameters
```

{% include optional.html content="[Organization](https://www.hl7.org/fhir/DSTU2/organization.html#search)" %}

Provider systems SHOULD implement the following search parameters:

| Name | Type | Description | Recommended |
| `adddress-postcode` | `string` | A postalCode specified in an address | Y |
| `identifier` | `token` | 	Any identifier for the organization (e.g. SDS/ODS code) | Y |
| `name` | `string` | A portion of the name of the organisation | |


In order to manage the number of search results returned, the server may choose to return the results in a series of pages. The search result set contains the URLs that the client uses to request additional pages from the search set. For a simple RESTful search, the page links are contained in the returned bundle as links. Please refer to [Paged Search](https://www.hl7.org/fhir/DSTU2/search.html#count){:target="_blank"} for further details.



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