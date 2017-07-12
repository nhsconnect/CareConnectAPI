---
title: Foundation | Conformance
keywords: foundations, fhir
tags: [rest,fhir,use_case,api,foundation,noccprofile]
sidebar: accessrecord_rest_sidebar
permalink: api_foundation_conformance.html
summary: A conformance statement is a set of capabilities of a FHIR Server that may be used as a statement of actual server functionality or a statement of required or desired server implementation.
---

{% include custom/search.warnbanner.html %}

{% include custom/fhir.referencemin.html resource="" page="" fhirlink="[Conformance](http://www.hl7.org/fhir/dstu2/conformance.html)" content="User Stories" userlink="" %}


## 1. Read ##

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/metadata</div>

The /metadata path on the root of the FHIR server will return the Conformance statement for the FHIR server:

Alternatively, a HTTP OPTIONS request against the root of the FHIR server will also return the conformance profile:

<div markdown="span" class="alert alert-success" role="alert">
OPTIONS [baseUrl]/</div>

For details of this interaction - see the [HL7 FHIR DSTU2 RESTful API](https://www.hl7.org/fhir/DSTU2/http.html#conformance)

All requests SHALL contain a valid ‘Authorization’ header and SHALL contain an ‘Accept’ header with at least one of the following application/json+fhir or application/xml+fhir.

## 2. Example ##

### 2.1 Request Query ###

Retrieve the Conformance statement from the FHIR Server, the format of the response body will be xml. Replace 'baseUrl' with the actual base Url of the FHIR Server.

#### 2.1.1. cURL ####

{% include custom/embedcurl.html title="Read Server Conformance Statement" command="curl -H 'Accept: application/xml+fhir' -H 'Authorization: BEARER [token]' -X GET '[baseUrl]/metadata'" %}

{% include custom/search.response.headers.html resource="Conformance"  %}

### 2.3 Response Body ###

{% include important.html content="The following draft conformance statement will move as the implementation guide moves on." %}

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
				<definition value="A portion of the family name of the patient"/>
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

{% include important.html content="The following draft conformance statement will move as the implementation guide moves on." %}


### 2.4 C# ###

{% include tip.html content="C# code snippets utilise Ewout Kramer's [fhir-net-api](https://github.com/ewoutkramer/fhir-net-api) library which is the official .NET API for HL7&reg; FHIR&reg;." %}

```csharp
var client = new FhirClient("http://[fhir_base]/");
client.PreferredFormat = ResourceFormat.Json;
var resource = client.Conformance();
FhirSerializer.SerializeResourceToXml(resource).Dump();
```
