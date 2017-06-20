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

`MedicationStatement` is a record of Medication that is being consumed by a patient. It is related to `MedicationAdministration` (record of the event where a Patient consumes or otherwise a medication) but is less detailed. `MedicationOrder` is a record of prescription issues, which provides detailed information and could be used with the `MedicationStatement` which provides summary information.

<p style="text-align:center;"><img src="images/engage/casestudies/bristolcc/TechnicalArchitecture.jpg" alt="Diagram showing an overview of the solution's architecture." title="Diagram showing an overview of the solution's architecture." style="width:75%"></p>
<br><br>

[TODO - Introduce Example and data]

[TODO - Explain with code examples how a MedicationStatement would be returned]

[TODO - Explain with code examples how a MedicationOrder would be returned. Do we query on code?]

<!--
A search on MedicationOrder without the '_Revinclude=*' would return a FHIR [Bundle](https://www.hl7.org/fhir/DSTU2/bundle.html) would return only MedicationOrder resources. This is useful if you already have Patient, Medication and Practitioner data but in most case the calling system or web application won't be. In this case it is useful for all the referenced resources to be returned with the search results.
This is done using the '_Revinclude=*' parameter and the returned search results now include the referenced parameters. The convention is to list the referenced resources before they are referenced (so they can be processed first).

{% include image.html
max-width="200px" file="Bristol/Bristol.searchResults.includeReferenced.bmp" alt="Bristol ERD"
caption="MedicationOrder Search Results" %}
-->
