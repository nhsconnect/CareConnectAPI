---
title: Bristol Connecting Care
keywords: case studies, usecase, user stories, epics, scenarios, business analaysis, technical architecture, context
tags: [foundations,user stories, epics, scenarios, casestudy]
sidebar: engage_sidebar
permalink: engage_poc_bristolcc.html
summary: "A case study showing the proposed adoption of FHIR to address needs of Bristol Connecting Care during medication reconcilliation."
---
<!--
{% include important.html content="Please write up your own Case Studies of Care Connect Profiles you have used in the wild. If possible please use the Care Connect Engagement Approach" %}
INTEROPen is working with health care providers and system vendors to prove the profiles defined within Care Connect. Please get in touch with INTEROPen to become help improve the community and fulfill the potential of Care Connect.
-->
## Client's Context ##

Connecting Care is a local electronic patient record that allows health and social care professionals directly involved in your care, to share a summary of your medical record.

## Case Overview ##

The pharmacists would like to retrieve medications history of the patient to prepare a list or reconciled medications. They want to know the patient's medications journey.


<p style="text-align:center;"><img src="images/engage/casestudies/bristolcc/BristolCC_POC_Case_Overview.svg" alt="The patient's medication journey demonstrating questions than are asked during medication reconciliation." style="width:90%"></p>



## Problem Statement ##

The Pharmacist does not have a consolidated view of a patient's medications because the information is distributed across a number of systems.

## Business Process ##

<p style="text-align:center;"><img src="images/engage/casestudies/bristolcc/BristolPharmacistsHighLevel.png" alt="High level business process diagram showing the requirement to display medication from either a specific system or all systems." style="width:90%"></p>

## Use Case Diagram ##

<p style="text-align:center;"><img src="images/engage/casestudies/bristolcc/BristolUseCaseDiagram.png" alt="Use Case Diagram showing the Pharamacists use cases being explored." style="width:90%"></p>

## User Stories ##

<table style="width:100%;"><tr><th style="min-width:10em;">Feature</th><th>User Story</th></tr>
<tr><td style="vertical-align: middle;">Medication List (View)</td><td>As a Pharmacist (Hospital Services) I want to retreive a patient's prescriptions using their NHS Number so that I can find prescribed medications for a patient when I know the 'Traced' and 'Verfied' NHS Number.</td></tr>
<tr><td style="vertical-align: middle;">Medication List (View)</td><td>As a Pharmacist (Hospital Services) I want to retreive a patient's prescriptions using a local system number (e.g an MRN) so that I can find medications for a patient when I don't know the traced and verified NHS Number.</td></tr>
<tr><td style="vertical-align: middle;">Medication List (View)</td><td>As a Pharmacist (Hospital Services) I want to view a combined list of the patient's prescriptions recorded across all care settings so that I can see all of a patient's prescriptions in one place to facilitate a quick overview of the patient's medication history or to facilitate meds reconsiliation.</td></tr>
<tr><td style="vertical-align: middle;">Medication List (View)</td><td>As a Pharmacist (Hospital Services) I want to retrieve all prescriptions from all available systems for a specific patient so I can build a complete list of reconciled medications for the patient.</td></tr>
<tr><td style="vertical-align: middle;">Medication List (View)</td><td>As a Pharmacist (Hospital Services) I want retrieve all of a patient's prescriptions from a specific system so I can find out which medications an organisation has prescribed to the patient.</td></tr>
<tr><td style="vertical-align: middle;">Medication List (View)</td><td>As a Pharmacist (Hospital Services) I want to know on which system a medication was prescribed so that I can make informed judgements about the reason the medication was originally prescribed.</td></tr>
<tr><td style="vertical-align: middle;">Medication List (View)</td><td>As a Pharmacist (Hospital Services) I want the patient's record displayed to indicate the trace status of an NHS Number used to lookup data so I can be confident that the system has retrieved data for the correct patient.</td></tr>
<tr><td style="vertical-align: middle;">Medication List (View)</td><td>As a Pharmacist (Hospital Services) I want to know if medications were not available from a specific source so I can know that there may be gaps in the data I have.</td></tr>
<tr><td style="vertical-align: middle;">Role Based Access Control (RBAC)</td><td>As a Information Governance Officer (Hospital Services) I want the interface to only return data to an authenticated user so I can be sure that only known users are accessing the data.</td></tr>
</table>


{% include custom/contribute.html content="Get in touch with careconnect@interopen.org to help with Case Studies of Care Connect Profiles"%}
