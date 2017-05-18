---
title: Identification | Patient
keywords: getcarerecord, structured, rest, patient
tags:
- structured
- patient
sidebar: accessrecord_rest_sidebar
permalink: restfulapis_identification_patient.html
summary: Patient
---

## Patient ##

{% include profile.html content="[Care Connect Patient](http://www.interopen.org/candidate-profiles/care-connect/CareConnect-Patient-1.html)" %}

## Read Operations ##

Return a single `Patient` for the specified id. Not the NHS Number

```http
GET /Patient/:id}
```
```http
GET /Patient?_id=:id}
```

## Search Parameters ##

Patient contains the demographics for the patient. Fetches a bundle of all `Patient` resources for the specified patient or search criteria.

```http
GET /Patient?:searchParameters
```

{% include optional.html content="[Patient](https://www.hl7.org/fhir/DSTU2/patient.html#search)" %}

Provider systems SHOULD implement the following search parameters:

| Name | Type | Description | Recommended |
|---------|--------|----------------|--------------------|
| `address` | `string` | An address in any kind of address/part of the patient |  |
| `adddress-postcode` | `string` | A postalCode specified in an address | Y |
| `birthdate` | `date` | The patient's date of birth | Y |
| `careprovider` | `reference` | Patient's nominated GP | |
| `email` | `token` | A value in an email contact | Y |
| `family` | `string` | A portion of the family name of the patient | Y |
| `gender` | `token` | Gender of the patient | Y |
| `given` | `string` | A portion of the given name of the patient | Y |
| `identifier` | `token` | A patient identifier (NHS Number, Hospital Number, etc) | Y |
| `name` | `string` | A portion of either family or given name of the patient | |
| `organization` | `reference` | The practice at which this person is a patient | |
| `phone` | `token` | A value in a phone contact | Y |
| `telecom` | `token` | The value in any kind of telecom details of the patient |  |
| `_count` | `number` | The maximum number of results per page. |  |

In order to manage the number of search results returned, the server may choose to return the results in a series of pages. The search result set contains the URLs that the client uses to request additional pages from the search set. For a simple RESTful search, the page links are contained in the returned bundle as links. Please refer to [Paged Search](https://www.hl7.org/fhir/DSTU2/search.html#count){:target="_blank"} for further details.



### identifier (NHS Number, Hospital Number, etc) ###

The recommended search parameters would include:

- Patient.identifier on NHSNumber, HIE or Hospital Number.
- a filter to limit the search results either using status = current, $current_medication list, period (issue date) or dateWritten
- _revinclude=* to return all referenced resources.

### family and given ###

TODO

### birthdate ###

TODO

### Multiple Parameters ###

```
TODO
```

## Examples ##

### C# ###

{% include tip.html content="C# code snippets utilise Ewout Kramer's [fhir-net-api](https://github.com/ewoutkramer/fhir-net-api) library which is the official .NET API for HL7&reg; FHIR&reg;." %}

#### Example 1. Retrieve all medication orders for a patient ####

```csharp
TODO
```

### Java ###

{% include tip.html content="Java code snippets utilise James Agnew's [hapi-fhir](https://github.com/jamesagnew/hapi-fhir/
) library." %}

```java
TODO
```

### Curl ###



```curl
TODO
```




