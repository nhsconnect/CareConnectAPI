---
title: Resources Overview
keywords: getcarerecord, structured, rest, resource
tags: [rest,fhir,api]
sidebar: foundations_sidebar
permalink: explore.html
summary: "Overview of the Resources section"
---

{% include custom/search.warnbanner.html %}

{% include custom/api_overview.svg %}

## 1. Pre-Requisites for FHIR Servers ##

### 1.1 CareConnectAPI Requirements ###

- SHALL support HL7 FHIR DSTU2 version 1.0.2.
- SHALL support the CareConnect Patient resource profile.
- SHALL support at least one additional resource profile from the list of CareConnect Profiles
- SHALL Implement REST behavior according to the [FHIR specification](http://www.hl7.org/fhir/dstu2/http.html)
- Resources SHALL identify the CareConnect profile supported as part of the [FHIR Base Resource](https://hl7.org/fhir/DSTU2/resource-definitions.html#Resource.meta)
- SHALL support XML **or** JSON formats for all CareConnectAPI interactions and SHOULD support both formats.


### 1.2 FHIR Conformance ###

SHALL declare a Conformance identifying the list of profiles, operations, search parameter supported.

In order to be a compliant FHIR server, client systems need to expose a valid FHIR [Conformance](https://www.hl7.org/fhir/DSTU2/conformance.html) profile. See also [Care Connect API FHIR conformance profile](api_foundation_conformance.html).

### 1.3 NHS Number ###

Only verified NHS Number SHALL be used with CareConnect profiles. This can be achieved using a spine accredited system, a [Demographics Batch Service (DBS)](https://developer.nhs.uk/library/systems/demographic-batch-service-dbs/) batch-traced record (CSV), or using a [Spine Mini Services Provider (HL7v3)](https://nhsconnect.github.io/spine-smsp/) to verify the NHS Number.

{% include custom/contribute.html content="Get in touch with careconnect@interopen.org to improve the Prerequisites." %}

## 2. Resource API Structure ##
The FHIR Care Connect profile API's described in the Explore section of this implementation guide have been structured consistently in the following way:
- `0.` References
- `1.` Read
- `2.` Search Parameters
- `3.` Example

### 2.1 Resource API Structure Details ###

<table style="min-width:100%;width:100%">
<tr id="clinical">
<th style="width:20%;">General</th>
<th style="width:80%;">Description </th>
</tr>
<tr>
<td>0. References</td>
<td>Links to other parts of the implementation guide which might help with context and understanding the API's described</td>
</tr>
<tr>
<td>1. Read</td>
<td>A description of how to get the API</td>
</tr>
<tr>
<td>2. Search Parameters</td>
<td>List of search parameters for the profile being described, including any tips for searching. This section shows examples of how to search using the provided search parameters</td>
</tr>
<tr>
<td>3. Example</td>
<td>Description of of the Request & Response headers, example of how to search on a server and the expected response body as an example</td>
</tr>
</table>

## 3. Resource API's ##
This section looks at the Care Connect profile API's covered within this implementation guide.


<table style="min-width:100%;width:100%">
<tr id="clinical">
<th style="width:33%;">Clinical</th>
<th style="width:33%;">&nbsp;</th>
<th style="width:33%;">&nbsp;</th>
</tr>
<tr id="clinicald">
<th>Summary</th>
<th>Diagnostics</th>
<th>Medications</th>
</tr>
<tr>
<td><a href="api_clinical_allergyintolerance.html">AllergyIntolerance</a></td>
<td><a href="api_diagnostics_observation.html">Observation</a></td>
<td><a href="api_medication_medication.html">Medication</a></td>
</tr>
<tr>
<td><a href="api_clinical_condition.html">Condition</a> (Problem)</td>
<td>&nbsp;</td>
<td><a href="api_medication_medicationorder.html">MedicationOrder</a></td>
</tr>
<tr>
<td><a href="api_clinical_procedure.html">Procedure</a></td>
<td>&nbsp;</td>
<td><a href="api_medication_medicationstatement.html">MedicationStatement</a></td>
</tr>
<tr>
<td>&nbsp;</td>
<td>&nbsp;</td>
<td><a href="api_medication_immunization.html">Immunization</a></td>
</tr>
</table>

<table style="min-width:100%;width:100%">
<tr id="base">
<th style="width:33%;">Base</th>
<th style="width:33%;">&nbsp;</th>
<th style="width:33%;">&nbsp;</th>
</tr>
<tr id="based">
<th>Individuals</th>
<th>Entities</th>
<th>Workflow</th>
</tr>
<tr>
<td><a href="api_entity_patient.html">Patient</a></td>
<td><a href="api_entity_organisation.html">Organization</a></td>
<td><a href="api_workflow_encounter.html">Encounter</a></td><td></td>
</tr>
<tr>
<td><a href="api_entity_practitioner.html">Practitioner</a> (Problem)</td>
<td><a href="api_entity_location.html">Location</a></td>
<td>&nbsp;</td>
</tr>
</table>


<table style="min-width:100%;width:100%">
<tr id="conformance">
<th style="width:33%;">Foundation</th>
<th style="width:33%;"></th>
<th style="width:33%;"></th>
</tr>
<tr id="conformanced">
<th>Conformance</th>
<th>Terminology</th>
<th>&nbsp;</th>
</tr>
<tr>
<td><a href="api_foundation_conformance.html">Conformance</a></td>
<td><a href="api_foundation_valueset.html">ValueSet</a></td>
<td>&nbsp;</td>
</tr>
</table>
