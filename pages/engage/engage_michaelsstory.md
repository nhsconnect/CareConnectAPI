---
title: "Michael's Story"
keywords: user stories, epics, scenarios, nhsnumber
tags: [foundations,userstories, epics, scenarios]
sidebar: engage_sidebar
permalink: engage_michaelsstory.html
summary: "An example of Michael's Story, translated to user stories with links to profiles"
---

{% include important.html content="This page has been added to promote discussion in INTEROPen of the use cases and scenarios. This project is being developed using an agile methodology so iterative updates to content will be added on a regular basis." %}


# Introduction #

[Michael's story](http://www.interopen.org/content/IO4%20-%20Proposed%20project%20(Michael's%20story).pdf) has been widely developed, clinical assured and demonstrated at the [INTEROPen summit](https://docs.google.com/document/d/1j1ZKQjXAAxz-Arn9lKQXuwpmlv7kMoo_0jEmqgKQKOg/edit#). The following Scenarios, Features and User Stories attempt to describe how Care Connect FHIR resources could be used to support Michael's story. While each scenario can support a number of user stories, these are expressed in a far simpler form to a real world counterpart. Also, these examples refer to a solution that is underpinned with some form of interoperability requirement. The translation into user stories doesn't attempt to describe the systems that would be required to support each definition. Currently, this page provides a simple association to a relevant profile that has been documented within this implementation guide. If no hyperlink exists then the resource is currently beyond the immediate Care Connect scope.

The images have been taken from the [Interop Summit](https://drive.google.com/file/d/0Bwn8CEFskNi-anUzU3BQaWRoRlk/edit).

## Hospital Services - Discharge ##

{% include callout.html content="<b>Scenario:</b><br>'Michael is to be discharged from hospital, with a care plan, and Dr. Hospital prepares his discharge summary. Dr. Hospital reconciles and reviews Michael’s discharge medications and produces a reconciled list of discharge medications. This includes hospital managed medication, new medications commenced during the hospital admission, Michael’s own over-the-counter medication, ongoing medication from the GP or other sectors.' "%}


<p style="text-align:center;"><img src="images/use_cases/michaels_story-epic_1.jpg" style="width:50%;max-width: 50%;"></p>


{% include callout.html content="<b>Further Conversations:</b><br>
This example refers to the reconciliation being performed by the doctor. The stories reflect this scenario and don’t explore the other cases where the reconciliation is performed by a technician or a pharmacist. This could be significant given that reconciliation by a technician when not validated by a pharmacist would include additional workflow for review." %}


**FEATURE: Medication (Reconciliation - Discharge)**

<table style="width:100%;max-width:100%;"><thead><tr><th>User Story</th><th style="max-width:18em;min-width:10em;width:25%">Resource</th></tr></thead>
<tr><td>As a clinician (hospital services) I want to ‘stop’ medication that is present on the patient’s drug chart because a drug is no longer being taken by the patient or I do not consider it necessary to 'take out'.</td><td style="vertical-align: middle;"><a href="api_medication_medicationorder.html">PUT MedicationOrder</a></td></tr>
<tr><td>As a clinician (hospital services) I want to add additional drugs that the patient may be taking to their drug chart because the patient declares that they are taking a drug that is not currently listed.</td><td style="vertical-align: middle;"><a href="api_medication_medicationstatement.html">POST MedicationStatement</a></td></tr>
<tr><td>As a clinician (hospital services) I want to continue medication that may have been put on hold during medicines reconciliation stage 1 on admission because the reasons that the drug were put on hold during the patient's admission are no longer relevant and the patient requires the medication for their ongoing condition.</td><td style="vertical-align: middle;"><a href="api_medication_medicationorder.html">PUT MedicationOrder</a></td></tr>
<tr><td>As a clinician (hospital services) I may wish to add additional information in the form of a note or comment against each medication change that I make so when I am unable to resolve unintentional discrepancies there will be a notification to the the GP that some further consideration may be required.</td><td style="vertical-align: middle;"><a href="api_medication_medicationorder.html">PUT MedicationOrder</a></td></tr>
<tr><td>As hospital services I want to send the complete list of patient medication to the patient's GP so that the GP can compare the information with their own records and amend accordingly.</td><td style="vertical-align:middle;"><a href="api_medication_medicationstatement.html">POST MedicationStatement</a></td></tr>
</table>

**FEATURE: Discharge Summary (Create)**

<table style="width:100%;max-width:100%;"><thead><tr><th>User Story</th><th style="max-width:18em;min-width:10em;width:25%">Resource</th></tr></thead>
<tr><td>As a clinician (hospital Services) I want to include the patient's TTO medications in the discharge summary to provide a complete and accurate list of the patient's medication to the GP.</td><td style="vertical-align: middle;">Refer to the Transfer or Care eDischarge Bundle (<a href="api_medication_medicationstatement.html">MedicationStatement</a>)</td></tr>
</table>


## Hospital Services - Dispensing / Repeat prescriptions ##

{% include callout.html content="<b>Scenario:</b><br>The hospital pharmacist reviews this medication list and after clarifying with Michael which ones he already has, dispenses the appropriate medications. The hospital pharmacist counsels Michael on his new medications and prepares a patient-friendly medication schedule to help Michael understand what, why, when and how to take his medications. "%}

<img src="images/use_cases/michaels_story-epic_2a.jpg" style="width:49%;display:inline;">
<img src="images/use_cases/michaels_story-epic_2b.jpg" style="width:49%;display:inline;">

**FEATURE: Dispensing of TTO medication**

<table style="width:100%;max-width:100%;"><thead><tr><th>User Story</th><th style="max-width:18em;min-width:10em;width:25%">Resource</th></tr></thead>
<tr><td>As a pharmacist (hospital services) I want to validate the medications prescribed, with the patient, so that I can provide the patient with the necessary medication that supplements what they currently have, ensuring they have enough medication to last at least two weeks (or a locally agreed amount).</td><td style="vertical-align:middle;"><a href="api_medication_medicationstatement.html#2-search-parameters">GET MedicationStatement</a></td></tr>
<tr><td>As a pharmacist (hospital services) I want to know if the patient requires a compliance aid to ensure that the medication is correctly packaged for the patient's needs.</td><td style="vertical-align:middle;"></td></tr>
<tr><td>As a pharmacist (hospital services) I want to dispense at least a two weeks supply of medication (or locally agreed amount) to the patient based on their final list of medication at discharge to provide the patient with the correct medication as prescribed until their GP has had enough time to reconcile the patient's TTO meds with their own record and the patient has had sufficient chance to arrange a follow-up appointment if necessary.</td><td style="vertical-align:middle;"><a href="api_medication_medicationdispense.html">POST MedicationDispense</a></td></tr>
<tr><td>As a pharmacist (hospital services) I want to counsel the patient to help them understand what, why, when and how to take their medications.</td><td><a href="api_clinical_procedure">POST Procedure</a></td></tr>
<tr><td>As a pharmacist (hospital services) I want to prepare a "patient friendly" medication schedule to help the patient understand what, why and how to use their medication.</td><td style="vertical-align:middle;"><a href="api_medication_medicationstatement.html#2-search-parameters">GET MedicationStatement</a></td></tr>
</table>

## Patient Facing Services ##

{% include callout.html content="The \"medication manager\" app on Michael's mobile phone is updated with the latest changes to his medications. Michael can view his new medication list, with any medication changes highlighted." %}

<p style="text-align:center;"><img src="images/engage/MichaelsStoryPicture4.jpg" style="width:50%;max-width: 50%;"></p>

**FEATURE: Medication list - Patient Facing (View)**

<table style="width:100%;max-width:100%;"><thead><tr><th>User Story</th><th style="max-width:18em;min-width:10em;width:25%">Resource</th></tr></thead>
<tr><td>As a patient I want to manage my medications from various care settings (and their administration) in one place so I can ensure that I don't run out of my meds as well as having a record that can be shown to another care provider if necessary.</td><td style="vertical-align:middle;"><a href="api_medication_medicationstatement.html#2-search-parameters">GET MedicationStatement</a></td></tr>
<tr><td>As a patient I want medication changes to be highlighted when viewing my medication summary so I am less likely to miss that dosages have changed on medication I was previously taking.</td><td style="vertical-align:middle;"></td></tr>
</table>

## Primary Care - General Practice ##

{% include callout.html content="Michael's GP receives a discharge summary from the hospital and the GP system uses this to update Michael's GP medication and problem list." %}

<p style="text-align:center;"><img src="images/engage/MichaelsStory5.png" style="width:50%;max-width: 50%;"></p>

**FEATURE: Discharge Summary**

<table style="width:100%;max-width:100%;"><thead><tr><th>User Story</th><th style="max-width:18em;min-width:10em;width:25%">Resource</th></tr></thead>
<tr><td>As a general practitioner (Primary Care, General Practice) I want to review the discharge summary created as a result of my patient's stay in hospital so I can update my records with the most recent and accurate patient information.</td><td style="vertical-align:middle;">Refer to the Transfer or Care eDischarge Bundle</td></tr>
<tr><td>As a general practitioner (Primary Care, General Practice) I want to to update my patient's medications with the latest reconciled list from the hospital to ensure I have the most complete list of medications and reduce the chance of duplicating prescribed medications or prescribing conflicting medication.</td><td style="vertical-align:middle;">Refer to the Transfer or Care eDischarge Bundle (<a href="api_medication_medicationstatement.html">MedicationStatement</a>)</td></tr>
<tr><td>As a general practitioner (Primary Care, General Practice) I want to update my patient's list of problems with the latest problems added during my patient's stay in hospital to ensure I have the most complete patient history possible, better informing future contacts with the patient and providing more accurate patient care.</td><td style="vertical-align:middle;">Refer to the Transfer or Care eDischarge Bundle (<a href="api_clinical_condition.html">Condition</a>)</td></tr>
</table>

## Patient Facing Services ##

{% include callout.html content="Michael's \"medication manager\" app provides prompts when each medication is due. Michael can record his adherence at the end of each day by responding to questions from his \"medication manager\" app, as well as record any questions he has to discuss with his care team." %}

<p style="text-align:center;"><img src="images/engage/MichaelsStory6.png" style="width:50%;max-width: 50%;"></p>

**FEATURE: Medication Reminder**

<table style="width:100%;max-width:100%;"><thead><tr><th>User Story</th><th style="max-width:18em;min-width:10em;width:25%">Resource</th></tr></thead>
<tr><td>As a patient I want to be reminded when my medications are due to be taken so that I can ensure that I don't forget to take my meds when they are due.</td><td style="vertical-align:middle;"><a href="api_medication_medicationstatement.html#patient">GET MedicationStatement</a></td></tr>
</table>

**FEATURE: Medication Administration**

<table style="width:100%;max-width:100%;"><thead><tr><th>User Story</th><th style="max-width:18em;min-width:10em;width:25%">Resource</th></tr></thead>
<tr><td>As a patient I want to record the actual medication I have taken so that I have a complete record of how well I have adhered to my medication regimen and my care team can review this, contacting me if there are any concerns.</td><td style="vertical-align:middle;">POST MedicationAdministration</td></tr>
<tr><td>As a patient I want to make notes against my medications to discuss with my Care Team so if I have any concerns over my medication this can be reviewed and discussed further.</td><td style="vertical-align:middle;">POST MedicationAdministration</td></tr>
</table>

{% include callout.html content="Michael gets a cold and visits his pharmacy to buy something to help. He scans the over-the-counter (OTC) medication purchase using the GTIN bar code. He purchases a codeine+paracetamol combination. The dosage is 8/500mg, two tablets up to 4 times a day. His application checks for interactions and contraindications and warns him if there are any potential interactions before add the medication to his \"medication manager\" app." %}

<p style="text-align:center;"><img src="images/engage/MichaelsStory7.png" style="width:50%;max-width: 50%;"></p>

**FEATURE: Medication List (Manage)**

<table style="width:100%;max-width:100%;"><thead><tr><th>User Story</th><th style="max-width:18em;min-width:10em;width:25%">Resource</th></tr></thead>
<tr><td>As a Patient I want to add any additional medicines that I purchase (such as over-the-counter, vitamins, natural remedies) so that I can maintain an accurate list of my medication for myself and my care team to review.</td><td style="vertical-align:middle;"><a href="api_medication_medicationstatement.html">POST MedicationStatement</a></td></tr>
<tr><td>As a patient I want to scan the bar code of a drug to add that to my medications list to facilitate a rapid update of my medications list without having to type in the medication details and reducing the chance or error.</td><td style="vertical-align:middle;"></td></tr>
</table>

**FEATURE: Drug Interaction Checking**

<table style="width:100%;max-width:100%;"><thead><tr><th>User Story</th><th style="max-width:18em;min-width:10em;width:25%">Resource</th></tr></thead>
<tr><td>As a Patient I want any additional medicines that I add to my medications list to be checked for interactions and contraindications to improve the effectiveness of my medication and offer increased safety.</td><td style="vertical-align:middle;"></td></tr>
</table>

## Primary Care - NHS 111 ##

{% include callout.html content="That evening Michael thinks that his OTC medication, co-codamol, has caused a rash. He calls 111 who can see his updated medication list with the recent purchase. 111 advises Michael to stop taking the medication and they send a prescription request to a local chemist for an antihistamine. 111 book an appointment for Michael to see his GP the next day to review the possible allergy" %}

<p style="text-align:center;"><img src="images/engage/MichaelsStory8.png" style="width:50%;max-width: 50%;"></p>

**FEATURE: Patient Record (Search)**

<table style="width:100%;max-width:100%;"><thead><tr><th>User Story</th><th style="max-width:18em;min-width:10em;width:25%">Resource</th></tr></thead>
<tr><td>As a health advisor (Primary Care, NHS 111) I want to retrieve a patient's record based on the information they provide over phone to review the current patient information in order to offer the best possible advice.</td><td style="vertical-align:middle;"><a href="api_entity_patient.html#2-search-parameters">GET Patient</a></td></tr>
</table>

**FEATURE: Medication List (View)**

<table style="width:100%;max-width:100%;"><thead><tr><th>User Story</th><th style="max-width:18em;min-width:10em;width:25%">Resource</th></tr></thead>
<tr><td>As a health advisor (Primary Care, NHS 111) I want to review a caller's current medication from Primary Care to ensure I have the most complete list of medications to help diagnose a condition, reduce the chance of duplicating prescribed medications or prescribing conflicting medication.</td><td style="vertical-align:middle;"><a href="api_medication_medicationstatement.html#2-search-parameters">GET MedicationStatement</a></td></tr>
</table>

**FEATURE: Allergy, Intolerance and Adverse Reaction List (Manage)**

<table style="width:100%;max-width:100%;"><thead><tr><th>User Story</th><th style="max-width:18em;min-width:10em;width:25%">Resource</th></tr></thead>
<tr><td>As a health advisor (Primary Care, NHS 111) I want to add a suspected allergy to a patient's record to alert other clinicians treating this patient that there is possibility of a reaction even though it still requires confirmation.</td><td style="vertical-align:middle;"><a href="api_clinical_allergyintollerance.html">POST AllergyIntolerance</a></td></tr>
</table>

**FEATURE: Medication List (Manage)**

<table style="width:100%;max-width:100%;"><thead><tr><th>User Story</th><th style="max-width:18em;min-width:10em;width:25%">Resource</th></tr></thead>
<tr><td>As a health advisor (Primary Care, NHS 111) I want to stop a medication on the patient's medication list that the patient has recorded themself using a patient facing solution because I think the patient is allergic to the medication.</td><td style="vertical-align:middle;"><a href="api_medication_medicationstatement.html#2-search-parameters">PUT MedicationStatement</a></td></tr>
</table>

**FEATURE: Resource (Search)**

<table style="width:100%;max-width:100%;"><thead><tr><th>User Story</th><th style="max-width:18em;min-width:10em;width:25%">Resource</th></tr></thead>
<tr><td>As a health advisor (Primary Care, NHS 111) I want to find a community pharmacy near to a patient's current location to provide the patient with the most convenient chemist to collect their prescription.</td><td style="vertical-align:middle;"><a href="api_entity_location.html#2-search-parameters">GET Location</a></td></tr>
</table>

**FEATURE: Medication Order (Create)**

<table style="width:100%;max-width:100%;"><thead><tr><th>User Story</th><th style="max-width:18em;min-width:10em;width:25%">Resource</th></tr></thead>
<tr><td>As a health advisor (Primary Care, NHS 111) I want to send a prescription for a calling patient to a pharmacy which is local to them to reduce the need for paper prescriptions, reduce interpretation errors and offer greater convenience for the patient.</td><td style="vertical-align:middle;"><a href="api_medication_medicationorder.html">POST MedicationOrder</a></td></tr>
</table>

**FEATURE: Appointment Booking**

<table style="width:100%;max-width:100%;"><thead><tr><th>User Story</th><th style="max-width:18em;min-width:10em;width:25%">Resource</th></tr></thead>
<tr><td>As a health advisor (Primary Care, NHS 111) I want to make an appointment with a GP for a calling patient to offer the most suitable care to the patient given the condition presented with, in the most convenient way for them.</td><td style="vertical-align:middle;">POST Appointment</td></tr>
</table>

## Primary Care - General Practice ##

{% include callout.html content="Michael visits his GP the next day. Michael's GP can see the updated medication list, including other medications he is taking (e.g. private services from abroad during illness, OTC/pharmacist supervised/online purchases, unconnected NHS services). They both discuss the medication allergy and Michael's allergy record is updated. The GP reviews the treatment, changes doses and prescribes a new medication and then generates prescriptions for Michael's ongoing/repeat medications." %}

<p style="text-align:center;"><img src="images/engage/MichaelsStory9.png" style="width:50%;max-width: 50%;"></p>

**FEATURE: Medication List (View)**

<table style="width:100%;max-width:100%;"><thead><tr><th>User Story</th><th style="max-width:18em;min-width:10em;width:25%">Resource</th></tr></thead>
<tr><td>As a general practitioner (Primary Care, General Practice) I want to see medications bought over the counter to ensure I have the most complete list of medications to help diagnose a condition and reduce the chance of duplicating prescribed medications or prescribing conflicting medication.</td><td style="vertical-align:middle;"><a href="api_medication_medicationstatement.html#2-search-parameters">GET MedicationStatement</a></td></tr>
<tr><td>As a general practitioner (Primary Care, General Practice) I want to see medications obtained by the patient online to ensure I have the most complete list of medications to help diagnose a condition and reduce the chance of duplicating prescribed medications or prescribing conflicting medication.</td><td style="vertical-align:middle;"><a href="api_medication_medicationstatement.html#2-search-parameters">GET MedicationStatement</a></td></tr>
<tr><td>As a general practitioner (Primary Care, General Practice) I want to see medications prescribed to a patient while abroad to ensure I have the most complete list of medications to help diagnose a condition and reduce the chance of duplicating prescribed medications or prescribing conflicting medication.</td><td style="vertical-align:middle;"><a href="api_medication_medicationstatement.html#2-search-parameters">GET MedicationStatement</a></td></tr>
<tr><td>As a general practitioner (Primary Care, General Practice) I want to see medications obtained by the patient under the guidance of a Pharmacist to ensure I have the most complete list of medications to help diagnose a condition, reduce the chance of duplicating prescribed medications or prescribing conflicting medication.</td><td style="vertical-align:middle;"><a href="api_medication_medicationstatement.html#2-search-parameters">GET MedicationStatement</a></td></tr>
</table>

**FEATURE: Allergy, Intolerance and Adverse Reaction List (Manage)**

<table style="width:100%;max-width:100%;"><thead><tr><th>User Story</th><th style="max-width:18em;min-width:10em;width:25%">Resource</th></tr></thead>
<tr><td>I want to confirm a patient's suspected allergy to ensure that the patient is not prescribed drugs or exposed to anything during their healthcare encounters that may cause an adverse reaction.</td><td style="vertical-align:middle;"><a href="api_clinical_allergyintollerance.html">PUT AllergyIntolerance</a></td></tr>
</table>

**FEATURE: Medication Order (Create)**

<table style="width:100%;max-width:100%;"><thead><tr><th>User Story</th><th style="max-width:18em;min-width:10em;width:25%">Resource</th></tr></thead>
<tr><td>As a general practitioner (Primary Care, General Practice) I want to prescribe new medication for the patient to provide a remedy to a diagnosed condition.</td><td style="vertical-align:middle;"><a href="api_medication_medicationorder.html">POST MedicationOrder</a></td></tr>
</table>

## Patient Facing Services ##

{% include callout.html content="That week, Michael is running low on one of his medications and requests a repeat prescription on his \"medication manager\" app" %}

<p style="text-align:center;"><img src="images/engage/MichaelsStory10.png" style="width:50%;max-width: 50%;"></p>

**FEATURE: Medication Order (Create)**

<table style="width:100%;max-width:100%;"><thead><tr><th>User Story</th><th style="max-width:18em;min-width:10em;width:25%">Resource</th></tr></thead>
<tr><td>As a Patient I want to request a repeat prescription without having to visit my GP to reduce the number of trips I make to the surgery.</td><td style="vertical-align:middle;"><a href="api_medication_medicationorder.html">POST MedicationOrder</a></td></tr>
</table>

## Community Pharmacy ##

{% include callout.html content="Michael's pharmacy receives the repeat prescription request and notifies Michael on his \"medication manager\" app that it is ready to collect." %}

<p style="text-align:center;"><img src="images/engage/MichaelsStory11.png" style="width:50%;max-width: 50%;"></p>

**FEATURE: Medication Order (Manage)**

<table style="width:100%;max-width:100%;"><thead><tr><th>User Story</th><th style="max-width:18em;min-width:10em;width:25%">Resource</th></tr></thead>
<tr><td>As a Pharmacist (Primary Care, Pharmaceutical Services) I want to receive prescriptions directly so that I can prepare the medication before the patient arrives to collect it.</td><td style="vertical-align:middle;"><a href="api_medication_medicationorder.html">POST MedicationOrder</a></td></tr>
<tr><td>As a Pharmacist (Primary Care, Pharmaceutical Services) I want to inform a patient that their prescription is available for collection so they can arrange for collection.</td><td style="vertical-align:middle;"><a href="api_medication_medicationorder.html">PUT MedicationOrder</a></td></tr>
</table>

{% include callout.html content="On Michael's care plan it states he needs a medication review with his hospital specialist for a particular specialist medication which is arranged via a virtual consultation." %}

<p style="text-align:center;"><img src="images/engage/MichaelsStory12.png" style="width:50%;max-width: 50%;"></p>

**FEATURE: Referral (Create)**

<table style="width:100%;max-width:100%;"><thead><tr><th>User Story</th><th style="max-width:18em;min-width:10em;width:25%">Resource</th></tr></thead>
<tr><td>As a Specialty Doctor (Hospital Services) I want to refer a patient for physiotherapy  to provide the patient with the most appropriate care.</td><td style="vertical-align:middle;">POST ReferralRequest</td></tr>
</table>

**FEATURE: Appointment Booking**

<table style="width:100%;max-width:100%;"><thead><tr><th>User Story</th><th style="max-width:18em;min-width:10em;width:25%">Resource</th></tr></thead>
<tr><td>As a Patient  I want to book an appointment with a GP for a medication review so that I can ensure that I am on the most suitable regimen of medication.</td><td style="vertical-align:middle;">POST Appointment</td></tr>
</table>

## Patient Facing Services ##

{% include callout.html content="Following the virtual consultation, the specialist refers Michael to the physiotherapist; Michael requests a particular medication is made private. After discussion with the specialist, Michael adds a privacy flag to his \"medication manager\" app which restricts viewing to all care professionals expect doctors and nurses." %}

<p style="text-align:center;"><img src="images/engage/MichaelsStory13.png" style="width:50%;max-width: 50%;"></p>

**FEATURE: Referral (Create)**

<table style="width:100%;max-width:100%;"><thead><tr><th>User Story</th><th style="max-width:18em;min-width:10em;width:25%">Resource</th></tr></thead>
<tr><td>As a Specialty Doctor (Hospital Services) I want to refer a patient for physiotherapy to provide the patient with the most appropriate care.</td><td style="vertical-align:middle;">POST ReferralRequest</td></tr>
</table>

**FEATURE: Information Governance (Sealing)**

<table style="width:100%;max-width:100%;"><thead><tr><th>User Story</th><th style="max-width:18em;min-width:10em;width:25%">Resource</th></tr></thead>
<tr><td>As a Patient I want to restrict access to my medication record so that it can only be seen by doctors and nurses. so that I can protect my privacy.</td><td style="vertical-align:middle;">POST Flag</td></tr>
</table>

## Community Services ##

{% include callout.html content="Michael's care plan is designed to support him to live independently through a self-funding domicillary care package that helps him to get up, wash and prepare for the day. His carers can also relay information about his medication compliance or side effects through the \"medication manager\" app, as well as requesting repeat prescriptions on his behalf." %}

<p style="text-align:center;"><img src="images/engage/MichaelsStory14.png" style="width:50%;max-width: 50%;"></p>

**FEATURE: Care Plans, Treatment Plans, Guidelines and Protocols**

<table style="width:100%;max-width:100%;"><thead><tr><th>User Story</th><th style="max-width:18em;min-width:10em;width:25%">Resource</th></tr></thead>
<tr><td>As a Domicilary Care Worker (Community Services, Home Care) I want to review my patient's care plan to understand their needs and expectations</td><td style="vertical-align:middle;">GET CarePlan</td></tr>
</table>

**FEATURE: Medication Administration**

<table style="width:100%;max-width:100%;"><thead><tr><th>User Story</th><th style="max-width:18em;min-width:10em;width:25%">Resource</th></tr></thead>
<tr><td>As a Domicilary Care Worker (Community Services, Home Care) I want to record actual medication that my client has taken to provide a record of the client's adherence to their medication regimen.</td><td style="vertical-align:middle;">POST MedicationAdministration</td></tr>
</table>

**FEATURE: Medication Order (Create)**

<table style="width:100%;max-width:100%;"><thead><tr><th>User Story</th><th style="max-width:18em;min-width:10em;width:25%">Resource</th></tr></thead>
<tr><td>As a Domicilary Care Worker (Community Services, Home Care) I want to request a repeat prescription for my client to reduce the number of trips they make to the surgery.</td><td style="vertical-align:middle;"><a href="api_medication_medicationorder.html">POST MedicationOrder</a></td></tr>
</table>
