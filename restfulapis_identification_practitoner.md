---
title: Identification | Practioner
keywords: getcarerecord, structured, rest, patient
tags: [structured,patient]
sidebar: accessrecord_rest_sidebar
permalink: restfulapis_identification_practitoner.html
summary: "Practioner"
---

## Patient ##

{% include tip.html content=" [Care Connect Patient](https://fhir-test.nhs.uk/StructureDefinition/gpconnect-patient-1) Resource." %}

Patient contains the demographics for the patient. Fetches a bundle of all `Patient` resources for the specified patient or search criteria.

## Search Parameters ##

Provider systems COULD implement all [search parameters for the `Patient` resource](https://www.hl7.org/fhir/DSTU2/patient.html#search){:target="_blank"}

Provider systems SHOULD implement the following search parameters:

| Name | Type | Description | Paths |
| `address` | `string` | An address in any kind of address/part of the patient | `Patient.address` |
| `adddress-postcode` | `string` | A postalCode specified in an address | `Patient.address.postalCode` |
| `birthdate` | `date` | The patient's date of birth | `Patient.birthDate` |
| `careprovider` | `reference` | Patient's nominated GP | `Patient.careProvider (Practitioner)` |
| `email` | `token` | A value in an email contact | `Patient.telecom(system=email)` |
| `family` | `string` | A portion of the family name of the patient | `Patient.name.family` |
| `gender` | `token` | Gender of the patient | `Patient.gender` |
| `given` | `string` | A portion of the given name of the patient | `Patient.name.given` |
| `identifier` | `token` | A patient identifier | `Patient.identifier` |
| `name` | `string` | A portion of either family or given name of the patient | `Patient.name` |
| `organization` | `reference` | The practice at which this person is a patient | `Patient.managingOrganization (Organization)` |
| `phone` | `token` | A value in a phone contact | `Patient.telecom(system=(phone)` |
| `telecom` | `token` | The value in any kind of telecom details of the patient | `Patient.telecom` |
| `_revinclude` | `string` | Include referenced resources.  |  |
| `_list` | `string` | Return patients in the list |  |

In order to manage the number of search results returned, the server may choose to return the results in a series of pages. The search result set contains the URLs that the client uses to request additional pages from the search set. For a simple RESTful search, the page links are contained in the returned bundle as links. Please refer to [Paged Search](https://www.hl7.org/fhir/DSTU2/search.html#count){:target="_blank"} for further details.



## API Usage ##

The recommended search parameters would include:

- Patient.identifier on NHSNumber, HIE or Hospital Number.
- a filter to limit the search results either using status = current, $current_medication list, period (issue date) or dateWritten
- _revinclude=* to return all referenced resources.

### Request Operation ###

#### FHIR Relative Request ####

```http
GET /Dstu2/Patient?identifier=http://fhir.nhs.net/Id/nhs-number|[NHSNumber]{&other search parameters}
```

#### FHIR Absolute Request ####

```http
GET https://[proxy_server]/https://[provider_server]/[fhir_base]/Patient?identifier=http://fhir.nhs.net/Id/nhs-number|[NHSNumber]{&other search parameters}
```

#### Multiple Parameter Requests ####

TODO

### Request Response ###

#### Payload Response Body ####


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




