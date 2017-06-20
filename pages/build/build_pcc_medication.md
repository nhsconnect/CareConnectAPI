---
title: Care Coordination | Medication
keywords: development
tags: [design,development]
sidebar: overview_sidebar
permalink: build_pcc_medication.html
summary: "Guidance on FHIR Medication resources and DM+D"
---

{% include custom/search.warnbanner.html %}

{% include custom/ihe.reference.html apicontent="[Medication](restfulapis_clinical_medication.html) <br> [MedicationOrder](restfulapis_clinical_medicationorder.html) <br>  [MedicationStatement](restfulapis_clinical_medicationstatement.html)" ihecontent="[IHE Community Medication Prescription and Dispense (CMPD)](http://www.ihe.net/uploadedFiles/Documents/Pharmacy/IHE_Pharmacy_Suppl_CMPD.pdf)<br>[IHE Patient Care Coordination (PCC) - A Data Access Framework using IHE Profiles](http://www.ihe.net/uploadedFiles/Documents/PCC/IHE_PCC_White_Paper_DAF_Rev1.0_2014-03-28.pdf)" patterncontent="[Portal](https://developer.nhs.uk/library/architecture/integration-patterns/portal/)" %}

## 1. Overview ##

{% include custom/usecase.html content="[Bristol Connecting Care](engage_poc_bristolcc.html)" %}

The Care Connect Medication profiles and relationships with other profiles are shown below:

<p style="text-align:center;"><img src="images/engage/casestudies/bristolcc/ERD.png" alt="Entity Relationship Diagram showing the applied profiles." title="Entity Relationship Diagram showing the applied profiles." style="width:75%"></p>
<br><br>

[MedicationStatement](restfulapis_clinical_medicationstatement.html) is a record of Medication that is being consumed by a patient. It is related to `MedicationAdministration` (record of the event where a Patient consumes or otherwise a medication) but is less detailed. [MedicationOrder](restfulapis_clinical_medicationorder.html) is a record of prescription issues, which provides detailed information and could be used with the [MedicationStatement](restfulapis_clinical_medicationstatement.html) which provides summary information.

<p style="text-align:center;"><img src="images/engage/casestudies/bristolcc/TechnicalArchitecture.jpg" alt="Diagram showing an overview of the solution's architecture." title="Diagram showing an overview of the solution's architecture." style="width:75%"></p>
<br><br>

[TODO - Introduce Example and data]

Server contains three tables of interest, MedicationIssues plus Patient and Practitioner that MedicationIssues reference. The tables below show extracts from all three tables which show three issues of two drugs for one Patient.

#### Medication Issues ####

| IssueId | Drug Name | Drug Code (SNOMED CT) | PatientId | PractitionerId | IssueDate | Dosage | Quantity | Quantity Units | Method | Issue Type | Duration Of Issue | Private | Cancelled |
|----|-----------|-----------|-----------|-----------|--------|----------|----------------|-----------|------------|------------|
|6bf79485-cee5-4a20-8e4a-4bf13aba33e6|Temazepam  Tablets  20 mg|321153009|6a7d31db-0bb8-4afa-bf4c-c32d5d4b8487|651dfe43-26d6-49b3-b493-8955415912c7|1999-05-18T00:00:00|1on|60|tablets|P|R|0|false|false|
|6bf71646-75e4-4b1c-8066-266a0af44adb|Temazepam  Tablets  20 mg|321153009|6a7d31db-0bb8-4afa-bf4c-c32d5d4b8487|651dfe43-26d6-49b3-b493-8955415912c7|1999-02-27T00:00:00|1on|60|tablets|P|R|0|false|false|
|6bd48152-2249-430b-90d9-7b88031a1476|Cefaclor 375mg modified-release tablets|323803009|6a7d31db-0bb8-4afa-bf4c-c32d5d4b8487|651dfe43-26d6-49b3-b493-8955415912c7|1997-06-09T00:00:00|ONE TO BE TAKEN TWICE A DAY|14|tablets|P|A|0|false|false|

#### Patient ####

| PatientId | NHSNumber | Forename | Surname |
|-----------|-----------|----------|---------|
| 6a7d31db-0bb8-4afa-bf4c-c32d5d4b8487 | 9439676165 | Karen | Samson |

#### Practitioner ####

| PractitionerId | GMP Code | Forename | Surname |
|-----------|----------|----------|---------|
| 651dfe43-26d6-49b3-b493-8955415912c7 | G8650149 | Kevin | Swamp |

The Code below shows how to build MedicationOrder using Java, the comments show where each field from the the MedicationIssues table has been used.

<script src="https://gist.github.com/KevinMayfield/e841cf9ae2504d22e372ca51379f1160.js"></script>

Executing the code results in the following XML

<script src="https://gist.github.com/KevinMayfield/a84b28075b571f7537a256b7bcdf9979.js"></script>

[TODO - Explain with code examples how a MedicationStatement would be returned]

[TODO - Explain with code examples how a MedicationOrder would be returned. Do we query on code?]



<!--
A search on MedicationOrder without the '_Revinclude=*' would return a FHIR [Bundle](https://www.hl7.org/fhir/DSTU2/bundle.html) would return only MedicationOrder resources. This is useful if you already have Patient, Medication and Practitioner data but in most case the calling system or web application won't be. In this case it is useful for all the referenced resources to be returned with the search results.
This is done using the '_Revinclude=*' parameter and the returned search results now include the referenced parameters. The convention is to list the referenced resources before they are referenced (so they can be processed first).

{% include image.html
max-width="200px" file="Bristol/Bristol.searchResults.includeReferenced.bmp" alt="Bristol ERD"
caption="MedicationOrder Search Results" %}
-->
