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

## Business Process ##

<p style="text-align:center;"><img src="images/engage/casestudies/southamptoncc/SouthamptonUHSBPM.png" alt="High level business process diagram showing the requirement to acknowledge the receipt of results." title="High level business process diagram showing the requirement to acknowledge the receipt of results." style="width:75%"></p>
<br><br>
## Use Case Diagram ##

<p style="text-align:center;"><img src="images/engage/casestudies/southamptoncc/SouthamptonUHSUseCase.png" alt="Use Case Diagram showing the acknowlegement use cases being explored." title="Use Case Diagram showing the acknowlegement use cases being explored." style="width:75%"></p>
<br><br>
