---
title: Conformance | Conformance
keywords: foundations, fhir
tags: [foundations,use_case,fhir]
sidebar: accessrecord_rest_sidebar
permalink: restfulapis_conformance_conformance.html
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

```xml
<Conformance xmlns="http://hl7.org/fhir">
	<version value="0.4.0-alpha.0"/>
	<name value="Care Connect"/>
	<status value="draft"/>
	<experimental value="true"/>
	<publisher value="HL7 UK"/>
	<date value="2017-06-09"/>
	<description value="This server implements the Care Connect FHIR APIs"/>
	<copyright value="Copyright © 2017 HL7 UK"/>
	<fhirVersion value="1.0.2"/>
	<acceptUnknown value="both"/>
	<format value="application/xml+fhir"/>
	<format value="application/json+fhir"/>
	<profile>
		<reference value="https://fhir.hl7.org.uk/StructureDefinition/CareConnect-AllergyIntolerance-1"/>
		<reference value="https://fhir.hl7.org.uk/StructureDefinition/CareConnect-Condition-1"/>
		<reference value="https://fhir.hl7.org.uk/StructureDefinition/CareConnect-Encounter-1"/>
		<reference value="https://fhir.hl7.org.uk/StructureDefinition/CareConnect-Immunization-1"/>
		<reference value="https://fhir.hl7.org.uk/StructureDefinition/CareConnect-Location-1"/>
		<reference value="https://fhir.hl7.org.uk/StructureDefinition/CareConnect-Medication-1"/>
		<reference value="https://fhir.hl7.org.uk/StructureDefinition/CareConnect-MedicationOrder-1"/>
		<reference value="https://fhir.hl7.org.uk/StructureDefinition/CareConnect-MedicationStatement-1"/>
		<reference value="https://fhir.hl7.org.uk/StructureDefinition/CareConnect-Observation-1"/>
		<reference value="https://fhir.hl7.org.uk/StructureDefinition/CareConnect-Organization-1"/>
		<reference value="https://fhir.hl7.org.uk/StructureDefinition/CareConnect-Patient-1"/>
		<reference value="https://fhir.hl7.org.uk/StructureDefinition/CareConnect-Practitioner-1"/>
		<reference value="https://fhir.hl7.org.uk/StructureDefinition/CareConnect-Procedure-1"/>
	</profile>
	<rest>
		<mode value="server"/>
		<security>
			<cors value="true"/>
			<certificate>
				<type value="application/x-pem-file"/>
				<blob/>
			</certificate>
		</security>
		<resource>
			<type value="Patient"/>
			<profile>
				<reference value="https://fhir.hl7.org.uk/StructureDefinition/CareConnect-Patient-1"/>
			</profile>
			<interaction>
				<code value="read"/>
				<documentation value="Read allows clients to read the current state of the Patient resource"/>
			</interaction>
			<interaction>
				<code value="search-type"/>
				<documentation value="Search allows clients to search for the Patient resource using the specified criteria"/>
			</interaction>
			<versioning value="versioned"/>
			<readHistory value="false"/>
			<updateCreate value="false"/>
			<searchParam>
				<name value="birthdate"/>
				<definition value="The patient’s date of birth"/>
				<type value="date"/>
			</searchParam>
			<searchParam>
				<name value="family"/>
				<definition value="A portion of the family name of the patientt"/>
				<type value="string"/>
			</searchParam>
			<searchParam>
				<name value="gender"/>
				<definition value="Gender of the patient"/>
				<type value="token"/>
			</searchParam>
			<searchParam>
				<name value="given"/>
				<definition value="A portion of the given name of the patient"/>
				<type value="string"/>
			</searchParam>
			<searchParam>
				<name value="identifier"/>
				<definition value="A patient identifier (NHS Number, Hospital Number, etc)"/>
				<type value="token"/>
				<documentation value="NHS Number (i.e. http://fhir.nhs.uk/Id/nhs-number|1234567890)"/>
				<searchParam>
					<name value="name"/>
					<definition value="A portion of either family or given name of the patient"/>
					<type value="token"/>
				</searchParam>
			</searchParam>
		</resource>
	</rest>
</Conformance>
```

### C# ###

{% include tip.html content="C# code snippets utilise Ewout Kramer's [fhir-net-api](https://github.com/ewoutkramer/fhir-net-api) library which is the official .NET API for HL7&reg; FHIR&reg;." %}

```csharp
var client = new FhirClient("http://[fhir_base]/");
client.PreferredFormat = ResourceFormat.Json;
var resource = client.Conformance();
FhirSerializer.SerializeResourceToXml(resource).Dump();
```
