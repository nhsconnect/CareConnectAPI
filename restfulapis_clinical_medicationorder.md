---
title: Clinical | Medication Order
keywords: usecase, medication, order
tags:
- restful_api
- clinical
- profile
sidebar: foundations_sidebar
permalink: restfulapis_clinical_medicationorder.html
summary: Clinical Observation
---

## Medication Order ##

{% include tip.html content=" [Care Connect Medication Order](https://fhir-test.nhs.uk/StructureDefinition/careconnect-gpc-medicationorder-1
) Resource." %}

## Read Operation ##

Return a single `MedicationOrder` for the specified id

```http
GET /MedicationOrder/:id
```

```http
GET /MedicationOrder?_id=:id
```

## Search Parameters ##

Medication order resource contains prescription information for a patient. Fetches a bundle of all `MedicationOrder` resources for the specified patient.

```http
GET /MedicationOrder?:searchParameters
```

{% include optional.html content="[MedicationOrder](https://www.hl7.org/fhir/DSTU2/medicationorder.html#search)" %}

Provider systems SHOULD implement the following search parameters:

| Name | Type | Description | Recommended |
|---------|--------|----------------|--------------------|
| `datewritten` | `date` | Return prescriptions written on this date |  |
| `period.[start|end]` | `date` | Return prescriptions issued in this date range | Y |
| `status` | `token` | Status of the prescription | Y |
| `identifier` | `token` | The source system of the prescriptions for  |  |
| `patient` | `reference` | The identity of a patient to list orders for | Y |
| `_revinclude` | `string` | Include referenced resources.  |  |
| `_list` | `string` | Return prescriptions in the list |  |
| `_count` | `number` | The maximum number of results per page. |  |

In order to manage the number of search results returned, the server may choose to return the results in a series of pages. The search result set contains the URLs that the client uses to request additional pages from the search set. For a simple RESTful search, the page links are contained in the returned bundle as links. Please refer to [Paged Search](https://www.hl7.org/fhir/DSTU2/search.html#count){:target="_blank"} for further details.

Provider systems SHALL return an error for any unknown or unsupported parameter inline with the `Prefer: handling=strict` search behavior.

{% include note.html content="Provider systems SHALL NOT represent the medication with an external reference to a 'Medication' resource but SHALL reference the 'Medication' within the Bundle search results." %}


### patient ###

The recommended search parameters would include:

- Patient.identifier on NHSNumber, HIE or Hospital Number.
- a filter to limit the search results either using status = current, $current_medication list, period (issue date) or dateWritten
- _revinclude=* to return all referenced resources.

```http
GET /MedicationOrder?patient.identifier=http://fhir.nhs.net/Id/nhs-number|[NHSNumber]
```

### status ###

To filter on current prescriptions, change the Relative Request to  

```http
GET /MedicationOrder?patient.identifier=http://fhir.nhs.net/Id/nhs-number|9876543210&status=active
```

### identifier ###

To filter to this list to a specific supplier, we can search for their system identifiers only.

```http
GET /MedicationOrder?patient.identifier=http://fhir.nhs.net/Id/nhs-number|9876543210&identifier=https://theccg.systemsupplier.co.uk/MedicationOrder|
```

### datewritten ###

If wish to filter the results on the data of prescription. The example below returns all prescriptions for Patient with NHS Number of 9876543210 written after 14/Mar/2017 (gt = greater than)

```http
GET /MedicationOrder?patient.identifier=http://fhir.nhs.net/Id/nhs-number|9876543210&datewritten=gt2017-03-14
```

### __list ###

Provider systems SHOULD implement [_list](https://www.hl7.org/fhir/DSTU2/search.html#list) search mechanism.

Provider systems SHALL implement the standard [current resource list](https://www.hl7.org/fhir/lifecycle.html#current) for the `MedicationOrder` resource:

- `$current-medications` A list of all medications that the patient is taking.

On the RESTful API, this is done using the [list search mechanism](https://www.hl7.org/fhir/DSTU2/search.html#list) as follows:

```http
GET /MedicationOrder?patient=[id]]&_list=$current-medications
```

### __revinclude ###

The example searches will only return MedicationOrder resources, it will not return any referenced resources such drugs (Medications) or clinicians (Practitioner). To return referenced resources add the parameter '_revinclude=*', specific resources can be selected (see https://www.hl7.org/fhir for details)
 
```http
GET /MedicationOrder?patient.identifier=http://fhir.nhs.net/Id/nhs-number|9876543210&datewritten=gt2017-03-14&_revinclude=*
```


### Search Response ###

The search parameters are based around a logical model which is shown below:

{% include image.html 
max-width="200px" file="Bristol/Bristol.EntityRelationship.Resource.bmp" alt="Bristol ERD"
caption="MedicationOrder Logical Model" %} 

A search on MedicationOrder without the '_Revinclude=*' would return a FHIR [Bundle](https://www.hl7.org/fhir/DSTU2/bundle.html) would return only MedicationOrder resources. This is useful if you already have Patient, Medication and Practitioner data but in most case the calling system or web application won't be. In this case it is useful for all the referenced resources to be returned with the search results.
This is done using the '_Revinclude=*' parameter and the returned search results now include the referenced parameters. The convention is to list the referenced resources before they are referenced (so they can be processed first).

{% include image.html 
max-width="200px" file="Bristol/Bristol.searchResults.includeReferenced.bmp" alt="Bristol ERD"
caption="MedicationOrder Search Results" %} 

Provider systems:

- SHALL return a `200` **OK** HTTP status code on successful execution of the operation.

```json
TODO
```

#### Error Handling ####

The Provider system SHALL return an error if:

- the `id` is invalid (i.e. no `Patient` resource with that logical id exists on the server).

Provider systems SHALL return an [OperationOutcome](http://www.hl7.org/fhir/operationoutcome.html) resource that provides additional detail when one or more data fields are corrupt or a specific business rule/constraint is breached.

Refer to [Development - FHIR Guidance - Error Handling](development_fhir_error_handling_guidance.html) for details of error codes.


## Examples ##

### C# ###

{% include tip.html content="C# code snippets utilise Ewout Kramer's [fhir-net-api](https://github.com/ewoutkramer/fhir-net-api) library which is the official .NET API for HL7&reg; FHIR&reg;." %}

#### Example 1. Retrieve all medication orders for a patient ####

```csharp
var client = new FhirClient("https://fhirtest.uhn.ca/baseDstu2");
client.PreferredFormat = ResourceFormat.Json;
var query = new string[] { "patient=42" };
var bundle = client.Search<MedicationOrder>(query);
bundle.Entry.Count().Dump();
FhirSerializer.SerializeResourceToJson(bundle).Dump();
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


