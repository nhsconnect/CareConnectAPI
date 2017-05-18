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

## Read Operation ##

Return a single `Location` for the specified id

```http
GET /Location/:id
```

```http
GET /Location?_id=:id
```

## Search Parameters ##

Location contains the details for the location. Fetches a bundle of all `Location` resources for the specified search criteria.

```http
GET /Location?:searchParameters
```

{% include optional.html content=" [Location](https://www.hl7.org/fhir/DSTU2/location.html#search)" %}

Provider systems SHOULD implement the following search parameters:

| Name | Type | Description | Recommended |
| `adddress-postcode` | `string` | A postalCode specified in an address | Y |
| `identifier` | `token` | 	Any identifier for the location (e.g. SDS/ODS code) | Y |
| `name` | `string` | A portion of the name of the location | |


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