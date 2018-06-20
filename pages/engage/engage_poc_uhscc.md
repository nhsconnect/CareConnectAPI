---
title: University Hospital Southampton
keywords: case studies, usecase, user stories, epics, scenarios, business analaysis, technical architecture, context, southampton, Connecting Care, acknowledge, results
tags: [userstories,casestudy]
sidebar: engage_sidebar
permalink: engage_poc_uhscc.html
summary: "A case study showing the proposed adoption of FHIR to address needs of University Hospital Southampton NHS Foundation Trust. (Currently not implemented)"
---
## Case Overview ##

This case study explores the acknowledgement of test results. A clinician would want to acknowledge that he has read the order results so that everyone involved in the patient’s care is aware that an action has been taken based on order results.

The results are available to all those involved in a patient’s care, clearly marked with who ordered them, who currently has responsibility for them, who has looked at/ignored them and who has acknowledged them.

Currently UHS support the acknowledgement of results directly within their EMIS eQuest Order Comms system. With the introduction of a mobile app for clinicians (MedXNote) clinicians will be able to view new results and acknowledge more flexibly, from and location without having to log into the eQuest.

MedXNote will be serviced by the Intersystems Ensemble - the Trust’s Integration Engine (TIE). MedXNote will handle the receipt of results from the TIE. The requirement is to describe how a FHIR Request/Response can be used to send the acknowledgement from MedXNote to Ensemble through to eQuest.
<br><br>

## Client's Context ##

University Hospital Southampton NHS Foundation Trust provides services to some 1.9 million people living in Southampton and South Hampshire, plus specialist services such as neurosciences, cardiac services and children's intensive care to more than 3.7 million people in central southern England and the Channel Islands.

The Trust is also a major centre for teaching and research in association with the University of Southampton and partners including the Medical Research Council and Wellcome Trust.
<br><br>

## User Stories ##
<b>As a</b> Clinician<br>
<b>I want to</b> review any new results (for my duty of care) while away from my desk or workstation<br>
<b>So that</b> I can act on those results as quickly as possible.<br>
<br>
<b>As a Clinician</b><br>
<b>I want to</b> acknowledge that I have reviewed a patient’s test results<br>
<b>So that</b> all other underlying systems can be updated with this information increasing the quality of care to a patient and improving efficiency amongst care teams.<br>

## Business Process ##

<p style="text-align:center;"><img src="images/engage/casestudies/southamptoncc/UHSBPMShowingScope.png" alt="High level business process diagram showing the requirement to acknowledge the receipt of results." title="High level business process diagram showing the requirement to acknowledge the receipt of results." style="width:75%"></p>
<br>

## Sequence (As Is) ##

<ol>
<li>A User creates an order in eQuest.</li>
<li>The Order is sent from eQuest to LabCentre.</li>
<li>Results are returned from LabCentre to eQuest.</li>
<li>eQuest sends results to Ensemble.</li>
<li>Ensemble sends the results to 3rd party systems.</li>
<li>User acknowledges results in eQuest.</li>
</ol>

## Sequence (To Be)

<ol>
<li>A User creates an order in eQuest.</li>
<li>The Order is sent from eQuest to LabCentre.</li>
<li>Results are returned from LabCentre to eQuest.</li>
<li>eQuest sends the results to Ensemble.</li>
<li>Ensemble sends results to 3rd party systems <b>(which includes MedXNotes if the user has subscribed)</b>.</li>
<li>User acknowledges results in eQuest <b>or MedXNotes</b>.</li>
<li>User acknowledges results in eQuest <b>or MedXNotes</b>.</li>
<li><b>If the user acknowledges results in MedXNotes, the App will send the acknowledgement to Ensemble which will forward that back to eQuest.</b></li>
<li><b>The FHIR response from eQuest will indicate if the post has been successful. The user may not have acknowledgement permissions or the result may have already been acknowledged by another user; in which case the response will indicate a failure.</b></li>
</ol>



