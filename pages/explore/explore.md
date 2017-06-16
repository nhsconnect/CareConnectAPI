---
title: Explore Overview
keywords: getcarerecord, structured, rest, resource
tags: [rest,fhir]
sidebar: foundations_sidebar
permalink: explore.html
summary: "Overview of the Explore section"
---

{% include custom/search.warnbanner.html %}

{% include custom/api_overview.svg %}


## 1. Profile Structure ##
The FHIR Care Connect profiles described in the Explore section of this implementation guide have been structured consistently in the following way:
0. References
1. Read
2. Search Parameters
3. Example

### 1.1 Profile Structure Details ###

| General              |  Medication &amp; Immunisation    |
|+---------------------|+--------------------------------+|
| 0. References  | Links to other parts of the implementation guide which might help with context and understanding the profiles described |
| 1. Read | A description of how to get the API |
| 2. Search Parameters          | List of search parameters for the profile being described, including any tips for searching. This section shows examples of how to search using the provided search parameters       |
| 3. Example | Description of of the Request & Response headers, example of how to search on a server and the expected response body as an example   |


## 2. Profiles ##
This section looks at the Care Connect profiles covered within this implementation guide.


<table style="min-width:100%;width:100%">
<tr id="clinical"><th style="width:50%;">Clinical</th><th style="width:50%;"></th></tr>
<tr id="clinicald"><th>Summary</th><th>Medication</th></tr>
<tr><td><a href="restfulapis_clinical_allergyintolerance.html">AllergyIntolerance</a></td><td><a href="restfulapis_clinical_medication.html">Medication</a></td></tr>
<tr><td><a href="restfulapis_clinical_condition.html">Condition</a> (Problem)</td><td><a href="restfulapis_clinical_medicationorder.html">MedicationOrder</a></td></tr>
<tr><td><a href="restfulapis_clinical_procedure.html">Procedure</a></td><td><a href="restfulapis_clinical_medicationstatement.html">MedicationStatement</a></td></tr>
<tr><td><a href="restfulapis_clinical_observation.html">Observation</a></td><td><a href="restfulapis_clinical_immunization.html">Immunization</a></td></tr>
</table>

<table style="min-width:100%;width:100%">
<tr id="identification"><th style="width:50%;">Identification</th><th style="width:50%;"></th></tr>
<tr id="identificationd"><th>Individuals </th><th>Groups &amp; Entities</th></tr>
<tr><td><a href="restfulapis_identification_patient.html">Patient</a></td><td><a href="restfulapis_identification_organisation.html">Organization</a></td></tr>
<tr><td><a href="restfulapis_identification_practitioner.html">Practitioner</a> (Problem)</td><td><a href="restfulapis_identification_location.html">Location</a></td></tr>
</table>

<table style="min-width:100%;width:100%">
<tr id="workflow"><th style="width:50%;">Workflow</th><th style="width:50%;"></th></tr>
<tr id="workflowdd"><th>Patient Management</th><th></th></tr>
<tr><td><a href="restfulapis_workflow_encounter.html">Encounter</a></td><td></td></tr>
</table>

<table style="min-width:100%;width:100%">
<tr id="conformance"><th style="width:50%;">Conformance</th><th style="width:50%;"></th></tr>
<tr id="conformanced"><th>Terminology</th><th>Operations Control</th></tr>
<tr><td><a href="restfulapis_conformance_valueset.html">ValueSet</a></td><td><a href="restfulapis_conformance_conformance.html">Conformance</a></td></tr>
</table>
