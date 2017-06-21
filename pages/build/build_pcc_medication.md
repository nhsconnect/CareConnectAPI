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

The diagram below shows the technical architecture of the Bristol scenario overlaid with Enterprise Integration Patterns [EIP](http://www.enterpriseintegrationpatterns.com/). The Trust Integration Engine (TIE) is collecting the patients prescriptions from a number of sources.
- The GP source is provided by GP Connect which selects a reply from the Patients GP Practice system supplier, the response conforms to a FHIR CareConnect-GPC profile.
- The EPR system supports CareConnect API and the response conforms to the CareConnect profiles.
- The e-Prescribing system has an API but the response isn't in the correct format so the TIE transforms response to CareConnect FHIR format.
- The datawarehouse doesn't have an API but is accessed by SQL ODBC queries, the TIE transforms the data into CareCorrect FHIR format.

Once all the data has been collated the TIE will send one response back to the Client system by aggregating all the responses. We have simplified the process of aggregation by converting all the responses to the same format.

<p style="text-align:center;"><img src="images/design/Bristol Technical Architecture with EIP.jpg" alt="Diagram showing an overview of the solution's architecture." title="Diagram showing an overview of the solution's architecture." style="width:100%"></p>
<br><br>


## 2. Working with FHIR CareConnect Medication ##

Most of the data servers involved within the Bristol Medication scenario will be storing data on a SQL database server. To illustrate working with FHIR Medication resources we have listed extracts from four tables which simulate how these servers would store the data:
-MedicationPatient stores the master Patient Medication record and corresponds to the CareConnect Medication Statement resource.
-MedicationIssues stores the issues and is related to CareConnect MedicationOrder
-Patient stores Patient demographics
-Practitioner stores Practitioner information.

**MedicationPatient**

| MedicationId | Drug Name | Drug Code (SNOMED CT) | PatientId | FirstIssue | LastIssue |
|--------------|-----------|-----------------------|-----------|------------|-----------|
|6b980ed2-2dc6-48e4-886d-745862fc9529|Cefaclor 375mg modified-release tablets|323803009|6a7d31db-0bb8-4afa-bf4c-c32d5d4b8487|1997-06-09|1997-06-09|
|6b9c746e-4cce-4f5c-a2a7-0fd156dd57ac|Temazepam 20mg tablets|321153009|6a7d31db-0bb8-4afa-bf4c-c32d5d4b8487|1995-09-02|2001-08-20|

**MedicationIssues**

| IssueId | Drug Name | Drug Code (SNOMED CT) | PatientId | PractitionerId | IssueDate | Dosage | Quantity | Quantity Units | Method | Issue Type | Duration Of Issue | Private | Cancelled |
|----|-----------|-----------|-----------|-----------|--------|----------|----------------|-----------|------------|------------|
|6bf79485-cee5-4a20-8e4a-4bf13aba33e6|Temazepam  Tablets  20 mg|321153009|6a7d31db-0bb8-4afa-bf4c-c32d5d4b8487|651dfe43-26d6-49b3-b493-8955415912c7|1999-05-18T00:00:00|1on|60|tablets|P|R|0|false|false|
|6bf71646-75e4-4b1c-8066-266a0af44adb|Temazepam  Tablets  20 mg|321153009|6a7d31db-0bb8-4afa-bf4c-c32d5d4b8487|651dfe43-26d6-49b3-b493-8955415912c7|1999-02-27T00:00:00|1on|60|tablets|P|R|0|false|false|
|6bd48152-2249-430b-90d9-7b88031a1476|Cefaclor 375mg modified-release tablets|323803009|6a7d31db-0bb8-4afa-bf4c-c32d5d4b8487|651dfe43-26d6-49b3-b493-8955415912c7|1997-06-09T00:00:00|ONE TO BE TAKEN TWICE A DAY|14|tablets|P|A|0|false|false|

**Patient**

| PatientId | NHSNumber | Forename | Surname |
|-----------|-----------|----------|---------|
| 6a7d31db-0bb8-4afa-bf4c-c32d5d4b8487 | 9439676165 | Karen | Samson |

**Practitioner**

| PractitionerId | GMP Code | Forename | Surname |
|-----------|----------|----------|---------|
| 651dfe43-26d6-49b3-b493-8955415912c7 | G8650149 | Kevin | Swamp |

A client system wanting to access data in the MedicationPatient table will first need to obtain the logical Id of the patient. This is achieved by querying the Patient table, we will use the Patient NHS number to do this.

```
GET [baseUrl]\Patient?identifier=https://fhir.nhs.uk/Id/nhs-number|9439676165
```

This would return a FHIR Bundle with one Patient resource, from the Patient resource we will extract the logicalId of `6a7d31db-0bb8-4afa-bf4c-c32d5d4b8487`. We can now query the MedicationPatient table using this logical Id.

```
GET [baseUrl]\MedicationStatement?patient=6a7d31db-0bb8-4afa-bf4c-c32d5d4b8487
```

This returns a FHIR Bundle containing two `MedicationStatement`. This may be enough for a summary screen but if we need to look in detail at a particular drug we can then query the issues using the drug code, for Temazepam  Tablets  20 mg the code (SNOMED Concept Id) is 321153009. We already have the logical Id of the Patient and including the code the query is:

```
GET [baseUrl]\MedicationOrder?patient=6a7d31db-0bb8-4afa-bf4c-c32d5d4b8487&code=http://snomed.info/sct|321153009
```  

This results in a FHIR Bundle which contains two `MedicationOrder`. Note: consider including a date parameter to limit the amount of results returned.

The code below shows how the same three queries can be done in java.

[TODO Validate code]

<script src="https://gist.github.com/KevinMayfield/0b68a287b764a18eebcde9431aec7f7b.js"></script>

## 3. Creating FHIR CareConnect MedicationOrder ##

The Code below shows how to build MedicationOrder using Java, the comments show where each field from the the MedicationIssues table has been used.

Java examples based on entries in the MedicationIssues table can be found on [GitHub](https://github.com/nhsconnect/careconnect-java-examples/blob/master/ImplementationGuideExplore/src/main/java/uk/nhs/careconnect/examples/fhir/ExampleMedicationOrderDb.java). This code generates the following XML. Note how Patient (line 18) and Practitioner (line 22) are referencing Patient and Practitioner tables, the details are not included but can be retrieved via the CareConnect API if required.

<script src="https://gist.github.com/KevinMayfield/a84b28075b571f7537a256b7bcdf9979.js"></script>
