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


<img src="images/use_cases/michaels_story-epic_1.jpg" style="width:100%;max-width: 100%;"> 


{% include callout.html content="<b>Further Conversations:</b><br>
This example refers to the reconciliation being performed by the doctor. The stories reflect this scenario and don’t explore the other cases where the reconciliation is performed by a technician or a pharmacist. This could be significant given that reconciliation by a technician when not validated by a pharmacist would include additional workflow for review." %}


### FEATURE: Reconcile the patient’s drug chart for discharge ###

<table style="width:100%;max-width: 100%;"><tr><th>User Story</th><th>Profile</th></tr>
<tr><td>As a clinician (hospital services) I want to ‘stop’ medication that is present on the patient’s drug chart because a drug is no longer being taken by the patient or I do not consider it necessary to 'take out'.</td><td><a href="restfulapis_clinical_medicationorder.html">POST MedicationRequest</a></td></tr>
<tr><td>As a clinician (hospital services) I want to add additional drugs that the patient may be taking to their drug chart because the patient declares that they are taking a drug that is not currently listed.</td><td><a href="restfulapis_clinical_medicationorder.html">POST MedicationRequest</a></td></tr>
<tr><td>As a clinician (hospital services) I want to continue medication that may have been put on hold during medicines reconciliation stage 1 on admission because the reasons that the drug were put on hold during the patient's admission are no longer relevant and the patient requires the medication for their ongoing condition.</td><td><a href="restfulapis_clinical_medicationorder.html">POST MedicationRequest</a></td></tr>
<tr><td>As a clinician (hospital services) I may wish to add additional information in the form of a note or comment against each medication change that I make so when I am unable to resolve unintentional discrepancies there will be a notification to the the GP that some further consideration may be required.</td><td><a href="restfulapis_clinical_medicationorder.html">POST MedicationRequest</a></td></tr>
<tr><td>As hospital services I want to send the complete list of patient medication to the patient's GP so that the GP can compare the information with their own records and amend accordingly.</td><td><a href="restfulapis_clinical_medicationstatement.html">POST MedicationStatement</a></td></tr>
</table>


### FEATURE: Create a discharge summary ###


<table><th>User Story</th><th>Profile</th>
<tr><td>As a clinician (hospital Services) I want to include the patient's TTO medications in the discharge summary to provide a complete and accurate list of the patient's medication to the GP.</td><td><a href="restfulapis_clinical_medicationstatement.html#2-search-parameters">GET MedicationStatement</a></td></tr>
</table>


## Dispensing / Repeat prescriptions ##

{% include callout.html content="<b>Scenario:</b><br>The hospital pharmacist reviews this medication list and after clarifying with Michael which ones he already has, dispenses the appropriate medications. The hospital pharmacist counsels Michael on his new medications and prepares a patient-friendly medication schedule to help Michael understand what, why, when and how to take his medications. "%}


<img src="images/use_cases/michaels_story-epic_2a.jpg" style="width:49%;display:inline;"> 
<img src="images/use_cases/michaels_story-epic_2b.jpg" style="width:49%;display:inline;"> 


### FEATURE: Dispensing of TTO medication ###

<table><th>User Story</th><th>Profile</th>
<tr><td>As a pharmacist (hospital services) I want to validate the medications prescribed, with the patient, so that i can provide the patient with the necessary medication that supplements what they currently have, ensuring they have enough medication to last at least two weeks (or a locally agreed amount).</td><td><a href="restfulapis_clinical_medicationstatement.html#2-search-parameters">GET MedicationStatement</a></td></tr>
<tr><td>As a pharmacist (hospital services) I want to know if the patient requires a compliance aid to ensure that the medication is correctly packaged for the patient's needs.</td><td><a href="restfulapis_clinical_medicationstatement.html#2-search-parameters">GET MedicationStatement</a></td></tr>
<tr><td>As a pharmacist (hospital services) I want to dispense at least a two weeks supply of medication (or locally agreed amount) to the patient based on their final list of medication at discharge to provide the patient with the correct medication as prescribed until their GP has had enough time to reconcile the patient's TTO meds with their own record and the patient has had sufficient chance to arrange a follow-up appointment if necessary.</td><td>POST <br> MedicationDispense</td></tr>
<tr><td>As a pharmacist (hospital services) I want to counsel the patient to help them understand what, why, when and how to take their medications.</td><td>POST <br> Encounter</td></tr>
<tr><td>As a pharmacist (hospital services) I want to prepare a "patient friendly" medication schedule to help the patient understand what, why and how to use their medication.</td><td><a href="restfulapis_clinical_medicationstatement.html#2-search-parameters">GET MedicationStatement</a></td></tr>
</table>

## Patient Facing Services ##

{% include callout.html content="The \"medication manager\" app on Michael's mobile phone is updated with the latest changes to his medications. Michael can view his new medication list, with any medication changes highlighted." %}

<img src="images/engage/MichaelsStoryPicture4.jpg" style="width:100%;max-width: 100%;"> 

### FEATURE: Patient Facing Medication list ###

<table><th>User Story</th><th>Profile</th>
<tr><td>As a patient I want to manage my medications from various care settings (and their administration) in one place. so that i can ensure that I don't run out of my meds as well as having a record that can be shown to another care provider if necessary.</td><td><a href="restfulapis_clinical_medicationstatement.html#2-search-parameters">GET MedicationStatement</a></td></tr>
<tr><td>As a patient I want medication changes to be highlighted when viewing my medication summary so I am less likely to miss that dosages have changed on medication I was previously taking.</td><td></td></tr>
</table>
