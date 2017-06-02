---
title: User Stories | Care Connect API | FHIR&reg; 
keywords: usecase,use case, user stories, epics, scenarios, nhsnumber
tags: [foundations,use_case,userstories, epics, scenarios]
sidebar: engage_sidebar
permalink: engage_user_stories.html
summary: "User stories to search for a Care Connect FHIR&reg; Profile."
---

{% include important.html content="This page has been added to promote discussion in INTEROPen of the use cases and scenarios. This project is being developed using an agile methodology so iterative updates to content will be added on a regular basis." %}


# Introduction #

[Michael's story](http://www.interopen.org/content/IO4%20-%20Proposed%20project%20(Michael's%20story).pdf) has been widely developed, clinical assured and demonstrated at the [INTEROPen summit](https://docs.google.com/document/d/1j1ZKQjXAAxz-Arn9lKQXuwpmlv7kMoo_0jEmqgKQKOg/edit#). The following Epics, Scenario's and User Stories attempt to describe how Care Connect FHIR resources can be used to support Michael's story. The images have been taken from the [Interop Summit](https://drive.google.com/file/d/0Bwn8CEFskNi-anUzU3BQaWRoRlk/edit).

## Hospital discharge/encounter ##

{% include callout.html content="<b>Scenario:</b><br>'Michael is to be discharged from hospital, with a care plan, and Dr. Hospital prepares his discharge summary. Dr. Hospital reconciles and reviews Michael’s discharge medications and produces a reconciled list of discharge medications. This includes hospital managed medication, new medications commenced during the hospital admission, Michael’s own over-the-counter medication, ongoing medication from the GP or other sectors.' "%}


<p style="text-align:center;"><img src="images/use_cases/michaels_story-epic_1.jpg" style="width:50%;max-width: 50%;"></p>


{% include callout.html content="<b>Further Conversations:</b><br>
This example refers to the reconciliation being performed by the doctor. The stories reflect this scenario and don’t explore the other cases where the reconciliation is performed by a technician or a pharmacist. This could be significant given that reconciliation by a technician when not validated by a pharmacist would include additional workflow for review." %}


### FEATURE: Medication (Reconciliation - Discharge) ###

<table style="width:100%;max-width: 100%;"><tr><th>User Story</th><th>Profile</th></tr>
<tr><td>As a clinician (hospital services) I want to ‘stop’ medication that is present on the patient’s drug chart because a drug is no longer being taken by the patient or I do not consider it necessary to 'take out'.</td><td><a href="restfulapis_clinical_medicationorder.html">PUT MedicationOrder</a></td></tr>
<tr><td>As a clinician (hospital services) I want to add additional drugs that the patient may be taking to their drug chart because the patient declares that they are taking a drug that is not currently listed.</td><td><a href="restfulapis_clinical_medicationstatement.html">POST MedicationStatement</a></td></tr>
<tr><td>As a clinician (hospital services) I want to continue medication that may have been put on hold during medicines reconciliation stage 1 on admission because the reasons that the drug were put on hold during the patient's admission are no longer relevant and the patient requires the medication for their ongoing condition.</td><td><a href="restfulapis_clinical_medicationorder.html">PUT MedicationOrder</a></td></tr>
<tr><td>As a clinician (hospital services) I may wish to add additional information in the form of a note or comment against each medication change that I make so when I am unable to resolve unintentional discrepancies there will be a notification to the the GP that some further consideration may be required.</td><td><a href="restfulapis_clinical_medicationorder.html">PUT MedicationOrder</a></td></tr>
<tr><td>As hospital services I want to send the complete list of patient medication to the patient's GP so that the GP can compare the information with their own records and amend accordingly.</td><td><a href="restfulapis_clinical_medicationstatement.html">POST MedicationStatement</a></td></tr>
</table>


### FEATURE: Discharge Summary (Create) ###


<table style="width:100%;max-width: 100%;"><th>User Story</th><th>Profile</th>
<tr><td>As a clinician (hospital Services) I want to include the patient's TTO medications in the discharge summary to provide a complete and accurate list of the patient's medication to the GP.</td><td>Refer to Bundle (Transfer of Care) <a href="restfulapis_clinical_medicationstatement.html#2-search-parameters">MedicationStatement</a></td></tr>
</table>


## Dispensing / Repeat prescriptions ##

{% include callout.html content="<b>Scenario:</b><br>The hospital pharmacist reviews this medication list and after clarifying with Michael which ones he already has, dispenses the appropriate medications. The hospital pharmacist counsels Michael on his new medications and prepares a patient-friendly medication schedule to help Michael understand what, why, when and how to take his medications. "%}


<img src="images/use_cases/michaels_story-epic_2a.jpg" style="width:49%;display:inline;"> 
<img src="images/use_cases/michaels_story-epic_2b.jpg" style="width:49%;display:inline;"> 


### FEATURE: Dispensing of TTO medication ###

<table style="width:100%;max-width: 100%;"><th>User Story</th><th>Profile</th>
<tr><td>As a pharmacist (hospital services) I want to validate the medications prescribed, with the patient, so that i can provide the patient with the necessary medication that supplements what they currently have, ensuring they have enough medication to last at least two weeks (or a locally agreed amount).</td><td><a href="restfulapis_clinical_medicationstatement.html#2-search-parameters">GET MedicationStatement</a></td></tr>
<tr><td>As a pharmacist (hospital services) I want to know if the patient requires a compliance aid to ensure that the medication is correctly packaged for the patient's needs.</td><td><a href="restfulapis_clinical_medicationstatement.html#2-search-parameters">GET MedicationStatement</a></td></tr>
<tr><td>As a pharmacist (hospital services) I want to dispense at least a two weeks supply of medication (or locally agreed amount) to the patient based on their final list of medication at discharge to provide the patient with the correct medication as prescribed until their GP has had enough time to reconcile the patient's TTO meds with their own record and the patient has had sufficient chance to arrange a follow-up appointment if necessary.</td><td><a href="restfulapis_clinical_medicationdispense.html">POST MedicationDispense</a></td></tr>
<tr><td>As a pharmacist (hospital services) I want to counsel the patient to help them understand what, why, when and how to take their medications.</td><td><a href="restfulapis_clinical_encounter">POST Encounter</a></td></tr>
<tr><td>As a pharmacist (hospital services) I want to prepare a "patient friendly" medication schedule to help the patient understand what, why and how to use their medication.</td><td><a href="restfulapis_clinical_medicationstatement.html#2-search-parameters">GET MedicationStatement</a></td></tr>
</table>

## Patient Facing Services ##

{% include callout.html content="The \"medication manager\" app on Michael's mobile phone is updated with the latest changes to his medications. Michael can view his new medication list, with any medication changes highlighted." %}

<img src="images/engage/MichaelsStoryPicture4.jpg" style="width:100%;max-width: 100%;"> 

### FEATURE: Patient Facing Medication list ###

<table style="width:100%;max-width: 100%;"><th>User Story</th><th>Profile</th>
<tr><td>As a patient I want to manage my medications from various care settings (and their administration) in one place. so that i can ensure that I don't run out of my meds as well as having a record that can be shown to another care provider if necessary.</td><td><a href="restfulapis_clinical_medicationstatement.html#2-search-parameters">GET MedicationStatement</a></td></tr>
<tr><td>As a patient I want medication changes to be highlighted when viewing my medication summary so I am less likely to miss that dosages have changed on medication I was previously taking.</td><td></td></tr>
</table>

## General Practice ##

{% include callout.html content="Michael's GP receives a discharge summary from the hospital and the GP system uses this to update Michael's GP medication and problem list." %}

<img src="images/engage/MichaelsStory5.png" style="width:100%;max-width: 100%;">

### FEATURE: Discharge Summary ###

<table style="width:100%;max-width: 100%;"><th>User Story</th><th>Profile</th>
<tr><td>As a general practitioner (Primary Care, General Practice) I want to review the discharge summary created as a result of my patient's stay in hospital so I can update my records with the most recent and accurate patient information.</td><td></td></tr>
<tr><td>As a general practitioner (Primary Care, General Practice) I want to to update my patient's medications with the latest reconciled list from the hospital to ensure I have the most complete list of medications and reduce the chance of duplicating prescribed medications or prescribing conflicting medication.</td><td><a href="restfulapis_clinical_medicationstatement.html#patient">GET MedicationStatement</a></td></tr>
<tr><td>As a general practitioner (Primary Care, General Practice) I want to update my patient's list of problems with the latest problems added during my patient's stay in hospital to ensure I have the most complete patient history possible, better informing future contacts with the patient and providing more accurate patient care.</td><td><a href="restfulapis_clinical_condition.html#patient">GET Condition</a></td></tr>
</table>

## Patient Facing Services ##

{% include callout.html content="Michael's \"medication manager\" app provides prompts when each medication is due. Michael can record his adherence at the end of each day by responding to questions from his \"medication manager\" app, as well as record any questions he has to discuss with his care team." %}

<img src="images/engage/MichaelsStory6.png" style="width:100%;max-width: 100%;">

### FEATURE: Medication Reminder ###

<table style="width:100%;max-width: 100%;"><th>User Story</th><th>Profile</th>
<tr><td>As a patient I want to be reminded when my medications are due to be taken so that I can ensure that I don't forget to take my meds when they are due.</td><td><a href="restfulapis_clinical_medicationstatement.html#patient">GET MedicationStatement</a></td></tr>
</table>

### FEATURE: Medication Administration ###

<table style="width:100%;max-width: 100%;"><th>User Story</th><th>Profile</th>
<tr><td>As a patient I want to record the actual medication I have taken so that I have a complete record of how well I have adhered to my medicatication regimen and my care team can review this, contacting me if there are any concerns.</td><td>PUT MedicationAdministration</td></tr>
<tr><td>As a patient I want to make notes against my medications to discuss with my Care Team so if I have any concerns over my medication this can be reviewed and discussed further.</td><td>PUT MedicationAdministration</td></tr>
</table>

{% include callout.html content="Michael gets a cold and visits his pharmacy to buy something to help. He scans the over-the-counter (OTC) medication purchase using the GTIN bar code. He purchases a codeine+paracetamol combination. The dosage is 8/500mg, two tablets up to 4 times a day. His application checks for interactions and contraindications and warns him if there are any potential interactions before add the medication to his \"medication manager\" app." %}

<img src="images/engage/MichaelsStory7.png" style="width:100%;max-width: 100%;">

### FEATURE: Medication List (Manage) ###

<table style="width:100%;max-width: 100%;"><th>User Story</th><th>Profile</th>
<tr><td>As a Patient I want to add any additional medicines that I purchase (such as over-the-counter, vitamins, natural remedies) so that I can maintain an accurate list of my medication for myself and my care team to review.</td><td>PUT MedicationStatement</td></tr>
<tr><td>As a patient I want to scan the bar code of a drug to add that to my medications list to facilitate a rapid update of my medications list without having to type in the medication details and reducing the chance or error.</td><td>PUT MedicationStatement</td></tr>
</table>

### FEATURE: Drug Interaction Checking ###

<table style="width:100%;max-width: 100%;"><th>User Story</th><th>Profile</th>
<tr><td>As a Patient I want any additional medicines that I add to my medications list to be checked for interactions and contraindications to improve the effectiveness of my medication and offer increased safety.</td><td></td></tr>
</table>
