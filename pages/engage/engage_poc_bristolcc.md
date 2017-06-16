---
title: Bristol Connecting Care
keywords: case studies, usecase, user stories, epics, scenarios, business analaysis, technical architecture, context, Bristol, Connecting Care
tags: [userstories,casestudy]
sidebar: engage_sidebar
permalink: engage_poc_bristolcc.html
summary: "A case study showing the proposed adoption of FHIR to address needs of Bristol Connecting Care during medication reconcilliation. (Currently not implemented)"
---
<!--
{% include important.html content="Please write up your own Case Studies of Care Connect Profiles you have used in the wild. If possible please use the Care Connect Engagement Approach" %}
INTEROPen is working with health care providers and system vendors to prove the profiles defined within Care Connect. Please get in touch with INTEROPen to become help improve the community and fulfill the potential of Care Connect.
-->
## Client's Context ##

Connecting Care is a local electronic patient record that allows health and social care professionals directly involved in your care, to share a summary of your medical record.

## Case Overview ##

The pharmacists would like to retrieve medications history of the patient to prepare a list or reconciled medications. They want to know the patient's medications journey. While the initial scenario seemed to be around medication reconciliation, what becomes clear is that it's really around the creation of a consolidated view of medication.

<p style="text-align:center;"><img src="images/engage/casestudies/bristolcc/BristolCC_POC_Case_Overview.svg" alt="The patient's medication journey demonstrating questions than are asked during medication reconciliation." title="The patient's medication journey demonstrating questions than are asked during medication reconciliation." style="width:90%"></p>

## Problem Statement ##

The Pharmacist does not have a consolidated view of a patient's medications because the information is distributed across a number of systems.

## Business Process ##

<p style="text-align:center;"><img src="images/engage/casestudies/bristolcc/BristolPharmacistsHighLevel.png" alt="High level business process diagram showing the requirement to display medication from either a specific system or all systems." title="High level business process diagram showing the requirement to display medication from either a specific system or all systems." style="width:90%"></p>

## Use Case Diagram ##

<p style="text-align:center;"><img src="images/engage/casestudies/bristolcc/BristolUseCaseDiagram.png" alt="Use Case Diagram showing the Pharamacists use cases being explored." title="Use Case Diagram showing the Pharamacists use cases being explored." style="width:90%"></p>

## User Stories ##

While the scope is initially demonstrated in the use case diagram, it is possible to refine the scope further within user stories that originate from conversations with the user. For example, from the perspective of the current Care Connect specification, security is outside of the scope of profile definition and further discussions would be required within the trust to clarify where responsibility lies.

<table style="width:100%;max-width:100%"><tr><th style="min-width:10em;">Feature</th><th>User Story</th></tr>
<tr><td colspan="2">In Scope</td></tr>
<tr><td style="vertical-align: middle;">Medication List (View)</td><td>As a Pharmacist (Hospital Services) I want to retrieve a patient's medications using their NHS Number so that I can find prescribed medications for a patient when I know the 'Traced' and 'Verfied' NHS Number.</td></tr>
<tr><td style="vertical-align: middle;">Medication List (View)</td><td>As a Pharmacist (Hospital Services) I want to retrieve a patient's medications using a local system number (e.g an MRN) so that I can find medications for a patient when I don't know the traced and verified NHS Number.</td></tr>
<tr><td style="vertical-align: middle;">Medication List (View)</td><td>As a Pharmacist (Hospital Services) I want retrieve all of a patient's medications from one or more specific system so I can build an accurate list of reconciled medications.</td></tr>
<tr><td style="vertical-align: middle;">Medication List (View)</td><td>As a Pharmacist (Hospital Services) I want to view a combined list of the patient's medications recorded across all care settings so that I can see all of a patient's medications in one place to facilitate a quick overview of the patient's medication history or to facilitate meds reconciliation.</td></tr>
<tr><td style="vertical-align: middle;">Medication List (View)</td><td>As a Pharmacist (Hospital Services) I want to retrieve all medications from all available systems for a specific patient so I can build a complete list of reconciled medications for the patient.</td></tr>
<tr><td style="vertical-align: middle;">Medication List (View)</td><td>As a Pharmacist (Hospital Services) I want to know on which system a medication was prescribed so that I can make informed judgements about the reason the medication was originally prescribed.</td></tr>
<tr><td colspan="2">Out of Scope <i>(Behaviour that is not addressed within the API directly.)</i></td></tr>
<tr><td style="vertical-align: middle;">Medication List (View)</td><td>As a Pharmacist (Hospital Services) I want the patient's record displayed to indicate the trace status of an NHS Number used to lookup data so I can be confident that the system has retrieved data for the correct patient.</td></tr>
<tr><td style="vertical-align: middle;">Medication List (View)</td><td>As a Pharmacist (Hospital Services) I want to know if medications were not available from a specific source so I can know that there may be gaps in the data I have.</td></tr>
<tr><td style="vertical-align: middle;">Role Based Access Control (RBAC)</td><td>As a Information Governance Officer (Hospital Services) I want the interface to only return data to an authenticated user so I can be sure that only known users are accessing the data.</td></tr>
</table>

## Dataset ##

<table style="width:100%;max-width:100%">
<tr><td style="width:50%">Drug name (generic)</td><td>Issue date</td></tr>
<tr><td>Drug name (Brand) if applicable</td><td>Number of issues</td></tr>
<tr><td>Product form</td><td>Number of authorised issues</td></tr>
<tr><td>Product strength</td><td>Source system identity</td></tr>
<tr><td>Prescribed dose</td><td>History of courses for same ingredient</td></tr>
<tr><td>Prescribed frequency</td><td>Issue type (acute, repeat, repeat dispensing or automatic)</td></tr>
<tr><td>Prescription data</td><td>Issue notes</td></tr>
<tr><td>Additional instructions</td><td>Prescription delivery method</td></tr>
<tr><td>Status of medication</td><td>Date of first issue</td></tr>
<tr><td>Cancellation reason</td><td>Date of last issue</td></tr>
<tr><td>Person recorded</td><td>Issue quantity</td></tr>
<tr><td>Role of person</td><td>Issue status (either a date of issue or 'Not yet issued')</td></tr>
<tr><td>Date authorised until</td><td></td></tr>
</table>

## FHIR Resources ##

<div style="display:flex;flex-wrap:wrap;">
<div style="flex:3;min-width:30em;"><p style="text-align:center;"><img src="images/engage/casestudies/bristolcc/FHIRResourcesUpdated.png" alt="Diagram showing that the resources MedicationOrder, MedicationStatement, Patient and Practitioner have been identified as necessary profiles to support a solution for Bristol Connecting Care." title="Diagram showing that the resources MedicationOrder, MedicationStatement, Patient and Practitioner have been identified as necessary profiles to support a solution for Bristol Connecting Care." style="width:90%"></p></div>
<div style="flex:1;min-width:20em;max-width:25em;border-style:solid;border-width:thin;border-color:#005eb8;border-radius:5px;padding:1em;margin-left:auto;margin-right:0px">
<p style="text-align:center;"><img src="images/engage/casestudies/bristolcc/FHIRResourcesOriginal.png" alt="Diagram showing the first proposal which didn't include the use of MedicationOrder" style="width:90%"></p>
<p><small><i>The first approach considered didn't include the MedicalStatement resource but simply proposed the use of MedicalOrder. Following clinical review it was highlighted that this would assume that all medications are prescribed which is not the case. Therefore, this was extended to include both MedicationStatement and MedicationOrder.</i></small></p>
</div>
</div>

## Profiles ##

<p style="text-align:center;"><img src="images/engage/casestudies/bristolcc/ERD.png" alt="Entity Relationship Diagram showing the applied profiles." title="Entity Relationship Diagram showing the applied profiles." style="width:90%"></p>

## API Signatures ##

As a Pharmacist (Hospital Services) I want to retrieve a patient's medications using their NHS Number so that I can find prescribed medications for a patient when I know the 'Traced' and 'Verified' NHS Number.
~~~
GET [baseUrl]/MedicationStatement?patient.identifier=https://fhir.nhs.uk/Id/nhs-number|9876543210
~~~

As a Pharmacist (Hospital Services) I want to retrieve a patient's medications using a local system number (e.g an Trust/Hospital Number or Master Patient Id (MPI)) so that I can find medications for a patient when I don't know the traced and verified NHS Number.

~~~
GET [baseUrl]/MedicationStatement?patient.identifier=https://fhir.example.nhs.uk/PAS/Patient|123345
~~~

As a Pharmacist (Hospital Services) I want retrieve all of a patient's medications from one or more specific system so I can build an accurate list of reconciled medications.
~~~
GET [baseUrl]/MedicationStatement?patient.identifier=https://fhir.nhs.uk/Id/nhs-number|9876543210&identifier=https://theccg.systemsupplier.co.uk/Sys1|
~~~

## Search Query Parameters ##

<table style="width:100%;max-width:100%">
<tr><th>Name</th><th>Type</th><th>Description</th><th>Conformance</th><th>Path</th></tr>
<tr><td>effective-date</td><td>date</td><td>Date when patient was taking (or not taking) the medication</td><td>SHOULD</td><td>MedicationStatement.effective[x]</td></tr>
<tr><td>patient</td><td>reference</td><td>The identity of a patient to list statements for</td><td>SHALL</td><td>MedicationStatement.patient (Patient)</td></tr>
<tr><td>status</td><td>token</td><td>Return statements that match the given status</td><td>SHOULD</td><td>MedicationStatement.status</td></tr>
<tr><td>code</td><td>token</td><td>Return administrations of this medication code</td><td>MAY</td><td>MedicationStatement.medicationCodeableConcept</td></tr>
<tr><td>identifier</td><td>token</td><td>Return statements with this external identifier</td><td>MAY</td><td>MedicationStatement.identifier</td></tr>
<tr><td>medication</td><td>reference</td><td>Return administrations of this medication reference</td><td>MAY</td><td>MedicationStatement.medicationReference (Medication)</td></tr>
<tr><td>source</td><td>reference</td><td>Who the information in the statement came from</td><td>MAY</td><td>MedicationStatement.informationSource (Patient, Practitioner, RelatedPerson))</td></tr>
<tr><td>status</td><td>token</td><td>Return statements that match the given status</td><td>MAY</td><td>MedicationStatement.status</td></tr>
</table>

## Search Results ##

<p style="text-align:center;"><img src="images/engage/casestudies/bristolcc/FHIRBundle.png" alt="Diagram showing the bundle that is returned following a search" title="Diagram showing the bundle that is returned following a search"></p>

## API Sequence Diagrams ##

<p style="text-align:center;"><img src="images/engage/casestudies/bristolcc/BristolCCSequenceDiagram.png" alt="Sequence diagram showing the flow of information between actors" title="Sequence diagram showing the flow of information between actors" style="width:90%"></p>

## Technical Architecture ##

<p style="text-align:center;"><img src="images/engage/casestudies/bristolcc/TechnicalArchitecture.jpg" alt="Diagram showing an overview of the solution's architecture." title="Diagram showing an overview of the solution's architecture." style="width:90%"></p>

## Acceptance Criteria ##

While the acceptance criteria is not fully developed, below is an example of some possible criteria that could be defined.

<table style="width:100%;max-width:100%"><tr><th style="min-width:10em;">Feature</th><th>User Story</th></tr>
<tr><td style="vertical-align: middle;">Medication List (View)</td><td>As a Pharmacist (Hospital Services) I want to retrieve all prescriptions from all available systems for a specific patient so I can build a complete list of reconciled medications for the patient.</td></tr>
<tr><td colspan="2">
<ul>
<li>I am able to call an API with the URL: GET /MedicationOrder?patient.identifier=https://fhir/nhs.net/Id/nhs-number|9876543210.</li>
<li>I am able to pass NHS number as an input parameter</li>
<li>The API returns profile "MedicationOrder" with medications information about patient as a populated JSON object in the following format: &lt;&lt;Json Object&gt;&gt;</li>
</ul>
</td></tr>
</table>


{% include custom/contribute.html content="Get in touch with careconnect@interopen.org to help with Case Studies of Care Connect Profiles"%}
