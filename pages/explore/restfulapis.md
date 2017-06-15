---
title: Overview | Profiles
keywords: getcarerecord, structured, rest, resource
tags: [rest,fhir]
sidebar: accessrecord_rest_sidebar
permalink: restfulapis.html
summary: Overview
---

{% include custom/search.warnbanner.html %}

## 1. Profile Structure ##
The FHIR Care Connect profiles described in the Explore section of this implementation guide have been structured consistantly in the following way:
0. References
1. Read
2. Search Parameters
3. Example

### 1.1 Profile Structure Details ###

| General              |  Medication &amp; Immunisation    |
|+---------------------+|+--------------------------------+|
| 0. References  | Links to other parts of the implementation guide which might help with context and understanding the profiles described |
| 1. Read | A description of how to get the API |
| 2. Search Parameters          | List of search parameters for the profile being described, including any tips for searching. This section shows examples of how to search using the provided search parameters       |
| 3. Example | Description of of the Request & Response headers, example of how to search on a server and the expected response body as an example   |


## 2. Profiles ##
This section looks at the Care Connect profiles covered within this implementation guide.

### 2.1 Clinical ###

| General             |  Medication &amp; Immunisation |
|---------------------|--------------------------------|
| [AllergyIntolerance](restfulapis_clinical_allergyintolerance.html)  |[ Medication](restfulapis_clinical_medication.html)                     |
| [Condition](restfulapis_clinical_condition.html) (Problem) | [MedicationOrder ](restfulapis_clinical_medicationorder.html)               |
| [Procedure](restfulapis_clinical_procedure.html)           | [MedicationStatement ](restfulapis_clinical_medicationstatement.html)           |
| [Observation](restfulapis_clinical_observation.html) | [Immunization](restfulapis_clinical_immunization.html)                   |

<!--- |   |  [Flag ](restfulapis_clinical_medicationflag.html)(Medication)  | --->

### 2.2. Identification ###

| Individuals  | Groups &amp; Entities       |
|--------------|--------------|
| [Patient ](restfulapis_identification_patient.html)     | [Organization](restfulapis_identification_organisation.html) |   
| [Practitioner](restfulapis_identification_practitioner.html) | [Location](restfulapis_identification_location.html)     |  

### 2.3. Workflow ###

| Patient Management |
|--------------------|
| [Encounter](restfulapis_workflow_encounter.html)          |

### 3.4 Conformance ###

| Terminology | Operations Control |
|-------------|--------------------|
| [ValueSet](restfulapis_conformance_valueset.html)    | [Conformance](restfulapis_conformance_conformance.html)          |
