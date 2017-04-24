---
title: Get the FHIR Conformance Profile
keywords: foundations, fhir
tags: [foundations,use_case,fhir]
sidebar: foundations_sidebar
permalink: foundations_use_case_get_the_fhir_conformance_profile.html
summary: "Use case for getting the FHIR server's conformance profile."
---

## API Usage ##

### Request Operation ###

#### FHIR Conformance Request ####

The /metadata path on the root of the FHIR server will return the Conformance statement for the FHIR server:

```http
GET https://[fhir_base]/metadata
```

Alternatively, a HTTP OPTIONS request against the root of the FHIR server will also return the conformance profile:

```http
OPTIONS https://[fhir_base]/
```

- For details of this interaction - see the [HL7 FHIR specification](https://www.hl7.org/fhir/http.html#conformance)
- Note: The mime-type can be specified to request either XML or JSON using another URL parameter `?_format=[mime-type]`, or a `Content-Type` HTTP header as per the [FHIR specification](https://www.hl7.org/fhir/http.html#mime-type).


#### Request Headers ####

Consumers SHALL include the following additional HTTP request headers:

| Header               | Value |
|----------------------|-------|
| `Ssp-TraceID`        | Consumer's TraceID (i.e. GUID/UUID) |
| `Ssp-From`           | Consumer's ASID |
| `Ssp-To`             | Provider's ASID |
| `Ssp-InteractionID`  | `urn:nhs:names:services:visitorsandmigrants:fhir:rest:read:metadata`|
| `Authorization`      | This will carry the base64 encoded JSON web token required for audit - see [Cross Organisation Audit and Provenance](integration_cross_organisation_audit_and_provenance.html) for details. |

#### Payload Request Body ####

N/A

#### Error Handling ####

The Spine will always return a valid conformance statement.

### Request Response ###

#### Response Headers ####

No additional headers expected beyond those described in the HTTP and FHIR&reg; standards.

#### Payload Response Body ####

- The Spine will return a `200` **OK** HTTP status code on successful retrival of the conformance profile.

An example Conformance profile is available [here](Conformance/Spine-VM-ConformanceStatement-1.xml) - client systems should always use the Conformance profile from the above URL as the authoritative conformance statement - this is provided as an example for reference only.

### C# ###

{% include tip.html content="C# code snippets utilise Ewout Kramer's [fhir-net-api](https://github.com/ewoutkramer/fhir-net-api) library which is the official .NET API for HL7&reg; FHIR&reg;." %}

```csharp
var client = new FhirClient("http://[fhir_base]/");
client.PreferredFormat = ResourceFormat.Json;
var resource = client.Conformance();
FhirSerializer.SerializeResourceToXml(resource).Dump();
```

