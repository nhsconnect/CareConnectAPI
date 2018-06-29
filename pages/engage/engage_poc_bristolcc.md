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
The pharmacists and technicians within secondary care would like to retrieve a patient's medications history to prepare a list or reconciled medications. While the pharmacist's need is around medication reconciliation, the requirement for interoperability is to obtain a list of "current" medications from external systems such as the GP systems.
## Problem Statement ##
The Pharmacist does not have a consolidated view of a patient's medications because the information is distributed across a number of systems.
## Business Process ##
<p style="text-align:center;"><img src="images/engage/casestudies/bristolcc/BCC Business Process.svg" alt="High level business process diagram showing the requirement to display medication from either a specific system or all systems." title="High level business process diagram showing the requirement to display medication from either a specific system or all systems." style="width:75%"></p>
## Use Case Diagram ##
<p style="text-align:center;"><img src="images/engage/casestudies/bristolcc/BCC Sequence Diagram.svg" alt="Use Case Diagram showing the Pharamacists use cases being explored." title="Use Case Diagram showing the Pharamacists use cases being explored." style="width:75%"></p>
## User Stories ##
While the scope is initially demonstrated in the use case diagram, it is possible to refine the scope further within user stories that originate from conversations with the user. For example, from the perspective of the current Care Connect specification, security is outside of the scope of profile definition and further discussions would be required within the trust to clarify where responsibility lies.

<table style="width:100%;max-width:100%"><thead><tr><th style="min-width:10em;">Feature</th><th>User Story</th></tr></thead>
<tr><td style="vertical-align: middle;">Medication List (View)</td><td>As a Pharmacist (Hospital Services) I want to retrieve a patient's medications using their NHS Number so that I can find prescribed medications for a patient when I know the 'Traced' and 'Verified' NHS Number.</td></tr>
<tr><td style="vertical-align: middle;">Medication List (View)</td><td>As a Pharmacist (Hospital Services) I want to retrieve a patient's medications using a local system number (e.g an MRN) so that I can find medications for a patient when I don't know the traced and verified NHS Number.</td></tr>
<tr><td style="vertical-align: middle;">Medication List (View)</td><td>As a Pharmacist (Hospital Services) I want retrieve all of a patient's medications from one or more specific system so I can build an accurate list of reconciled medications.</td></tr>
<tr><td style="vertical-align: middle;">Medication List (View)</td><td>As a Pharmacist (Hospital Services) I want to know the first issue of a prescription of medication for the patient so that I know how long the patient has been on a particular medication and I can see if this has changed over time.</td></tr>
<tr><td style="vertical-align: middle;">Medication List (View)</td><td>As a Pharmacist (Hospital Services) know the current issue of a prescription of medication for the patient so that I can include this in my reconciliation and I can identify how this have changed since the initial issue.</td></tr>
<tr><td style="vertical-align: middle;">Medication List (View)</td><td>As a Pharmacist (Hospital Services) I want to know know the last issue of a prescription of medication for the patient so that I know how long the patient was expected to be issued with that medication.</td></tr>
<tr><td style="vertical-align:middle;">Medication List (View)</td><td>As a Pharmacist (Hospital Services) I want to display patient medications from different sources in a single consolidated view so I can more easily reconcile them into a single list.</td></tr>
<tr><td style="vertical-align:middle;">Medication List (View)</td><td>As a Pharmacist (Hospital Services) I want to know if results have not been returned due to a error so that I can consider the impact of missing information on my reconciliation.</td></tr>
</table>
## FHIR Resource Mapping ##
An initial dataset was extracted from the initial requirements and these can be mapped to various FHIR Resources. It is possible to see that the required data items are spread across a number of different (but related) resources.
<table style="font-size:small; width:100%; max-width:100%">
  <tr><th>Data Item</th><th>Medication</th><th>MedicationRequest</th><th>MedicationStatement</th></tr>
  <tr><td>Additional instructions</td><td></td><td>dosageInstruction.additionalInstruction</td><td>dosage.additionalInstruction</td></tr>
  <tr><td>Cancellation reason</td><td></td><td>extension.statusReason</td><td></td></tr>
  <tr><td>Date authorised until</td><td></td><td>dispenseRequest.validityPeriod.end</td><td></td></tr>
  <tr><td>Date of first issue</td><td></td><td></td><td></td></tr>
  <tr><td>Date of last issue</td><td></td><td></td><td></td></tr>
  <tr><td>Drug name (Brand) if applicable</td><td>code</td><td></td><td></td></tr>
  <tr><td>Drug name (generic)</td><td>code, isBrand</td><td></td><td></td></tr>
  <tr><td>History of courses for same ingredient</td><td></td><td></td><td></td></tr>
  <tr><td>Issue date</td><td></td><td></td><td></td></tr>
  <tr><td>Issue notes</td><td></td><td></td><td></td></tr>
  <tr><td>Issue quantity</td><td></td><td></td><td></td></tr>
  <tr><td>Issue status (either a date of issue or 'Not yet issued')</td><td></td><td></td><td></td></tr>
  <tr><td>Issue type (acute, repeat, repeat dispensing or automatic)</td><td></td><td></td><td></td></tr>
  <tr><td>Number of authorised issues</td><td></td><td>dispenseRequest.numberOfRepeatsAllowed</td><td></td></tr>
  <tr><td>Number of issues</td><td></td><td></td><td></td></tr>
  <tr><td>Person recorded</td><td></td><td>requester</td><td></td></tr>
  <tr><td>Prescribed dose</td><td></td><td>dose</td><td>dose</td></tr>
  <tr><td>Prescribed frequency</td><td></td><td>rate</td><td>rate</td></tr>
  <tr><td>Prescription delivery method</td><td></td><td>method</td><td>method</td></tr>
  <tr><td>Product form</td><td></td><td></td><td></td></tr>
  <tr><td>Product strength</td><td></td><td></td><td></td></tr>
  <tr><td>Role of person</td><td></td><td></td><td></td></tr>
  <tr><td>Source system identity</td><td></td><td></td><td></td></tr>
  <tr><td>Status of medication</td><td></td><td>status</td><td>status</td></tr>
</table>
The elements of this requirement focus around medication resources so the process of determining the best solution can begin with the <a href="https://www.hl7.org/fhir/medications-module.html">FHIR Medications Module</a>. This provides a list of medication and describes their relation to each other. The pharmicist is ultimately looking for 'current' medications from any of the supplying systems. There are two resources that are appropriate to obtain a list of medications: <a href="api_medication_medicationrequest.html">MedicationRequest</a> and <a href="api_medication_medicationstatement.html">MedicationStatement</a>. The process to determine what is considered "current" is not defined at this stage because the first proof of concepts will retrieve all prescriptions from one system leaving the pharmacist to make a judgement about the relevance of each during reconciliation. This will however need revisiting in future stages as a wider gamut of systems are brought into the solution.

While a <a href="api_medication_medicationstatement.html">MedicationStatement</a> is a resource that is designed to indicate the medication that is currently being taken by the patient, it has a broad scope when compared to a <a href="api_medication_medicationrequest.html">MedicationRequest</a>. A <a href="api_medication_medicationstatement.html">MedicationStatement</a> can include medications currently being taken, previously taken, and knowledge that could be sourced from the patient directly, or somebody that has a relationship with the patient. Once the medications are reconciled, a <a href="api_medication_medicationstatement.html">MedicationStatement</a> is the only way to share current medications in their entirety.

Supplying systems may not have sufficient data to create a <a href="api_medication_medicationstatement.html">MedicationStatement</a>, but may have a history of prescriptions that have been created for a patient. This is common amongst Primary Care systems. In this situation, it is possible to list prescriptions as a way of determining medication history. This leaves the Pharmacist's reconcilliation process to determine which of these prescriptions are "current". This could be challenging if the patient has an extensive history recorded by the providing system.

Forming an API request for MedicationRequest that only returns 'current' MedicationRequests is a complex requirement. Alternatively, FHIR does have provision for a dedicated operation that allows the provider to serve a list of current MedicationRequests (or MedicationStatements). This is achieved with a "<a href="https://www.hl7.org/fhir/lifecycle.html#current">Current Resource List</a>"; more specifically by adopting the <a href="https://www.hl7.org/fhir/search.html#current">list search mechanism</a> $current-medication.

The following diagram shows an Entity Relationship containing the FHIR Medications Module. It also includes the Resource List which is the most appropriate method for accessing the current medications in this instance.
<p style="text-align:center;"><img src="images/engage/casestudies/bristolcc/BristolCC Entity Relationship.svg" alt="Entity relationship showing the FHIR Medications Module including the Resource List." title="Entity relationship showing the FHIR Medications Module including the Resource List." style="width:75%"></p>

This diagram also highlights where most of the required dataset resides within the FHIR Medication Module. Some of the required data will also require additional resources to fully satisfy and may also have to be derived.

Bristol are initially retreiving medication history from a system which only records the prescription of controlled drugs. This means that the expected medication history for one patient held on the system is likely to be small. For this reason, the initial requests being implemented will be for <a href="api_medication_medicationrequest.html">MedicationRequest</a> using the following API signature.
~~~
GET [baseUlr]/MedicationRequest?patient=[id]
~~~
## POC Architectural Overview ##
<p style="text-align:center;"><img src="images/engage/casestudies/bristolcc/HighLevelMeds.svg" alt="Architectural overview showing the scope of the POC." title="Architectural overview showing the scope of the POC." style="width:75%"></p>
While the intention at Bristol if to retreive prescription information from a variety of systems, initially the plan is only to retreive prescription information from the Theseus system which will only have information about the prescription of controlled drugs. The number of records expected against for patient is expected to be small. For this reason, the first proof of concept will demonstrate MedicationRequests being returned from an appropriate query for patient, directly against the MedicationRequest resource.
## API Signature Examples ##
### Initial POC ###
The initial POC proposal only requires all MedicationRequests to be returned from a single source.
<br>
<b>As a</b> Pharmacist (Hospital Services) <b>I want</b> to retrieve a patient's medications using their NHS Number <b>so</b> that I can find prescribed medications for a patient when I know the 'Traced' and 'Verified' NHS Number.
<br>
The following example is the simplest form of the request and does require the client to have retreived the patient identifier with a previous query against patient. All supplying systems that support MedicationRequest will support this approach.
~~~
GET [baseUrl]/MedicationRequest?patient=[id]
~~~
An alternative approach to building the full request in a single call is possible but the support of this is not mandated.
~~~
GET [baseUrl]/MedicationRequest?patient.identifier=https://fhir.nhs.uk/Id/nhs-number|9876543210
~~~
<br>
<b>As a</b> Pharmacist (Hospital Services) <b>I want</b> to retrieve a patient's medications using a local system number (e.g an Trust/Hospital Number or Master Patient ID (MPI)) <b>so</b> that I can find medications for a patient when I don't know the traced and verified NHS Number.
~~~
GET [baseUrl]/MedicationRequest?patient=[id]
~~~
or
~~~
GET [baseUrl]/MedicationRequest?patient.identifier=https://fhir.example.nhs.uk/PAS/Patient|123345
~~~
<br>
### For Future Consideration ###
<b>As a</b> Pharmacist (Hospital Services) <b>I want</b> to retrieve all of a patient's medications from one or more specific systems <b>so</b> I can build an accurate list of reconciled medications.
~~~
GET [baseUrl]
/MedicationRequest?patient.identifier=https://fhir.nhs.uk/Id/nhs-number|9876543210&identifier=https://theccg.systemsupplier.co.uk/Sys1|
~~~
<br>
<b>As a</b> Pharmacist (Hospital Services) <b>I want</b> to know the first issue of a prescription of medication for the patient <b>so</b> that I know how long the patient has been on a particular medication and I can see if this has changed over time.
~~~
GET [baseUrl]/MedicationStatement?patient.identifier=https://fhir.nhs.uk/Id/nhs-number|9876543210&code=http://snomed.info/sct|[SNOMED ConceptID of Drug]
~~~
<i>The first issue of a prescription can be deduced from the results.</i>
<br><br><br>
<b>As a</b> Pharmacist (Hospital Services) <b>I want</b> to know the current issue of a prescription of medication for the patient <b>so</b> that I can include this in my reconciliation and I can identify how this have changed since the initial issue.
~~~
GET [baseUrl]/MedicationRequest?patient.identifier=https://fhir.nhs.uk/Id/nhs-number|9876543210&code=http://snomed.info/sct|[SNOMED ConceptID of Drug]
~~~
<i>The current issue of a prescription can be deduced from the list if issues by identifying the most recent in the returned list.</i>
<br><br><br>
<b>As a</b> Pharmacist (Hospital Services) <b>I want</b> to know the last issue of a prescription of medication for the patient <b>so</b> that I know how long the patient was expected to be issued with that medication.
~~~
GET [baseUrl]/MedicationRequest?patient.identifier=https://fhir.nhs.uk/Id/nhs-number|9876543210&code=http://snomed.info/sct|[SNOMED ConceptID of Drug]
~~~
<i>The last issue of a prescription can be deduced by ordering the returned medications</i>
<br><br><br>
<b>As a</b> Pharmacist (Hospital Services) <b>I want</b> to display patient medications from different sources in a single consolidated view <b>so</b> I can more easily reconcile them into a single list.
<br><br>
<i>CC profiles - MedicationStatement and it’s containing profiles are structured and can be returned in Json, Xml or any other format.</i>
<br><br><br>
<b>As a</b> Pharmacist (Hospital Services) <b>I want</b> to know if results have not been returned due to a error <b>so</b> that I can consider the impact of missing information on my reconciliation.

<i>
404- Resource not found<br>
410- Resource deleted
</i>
<br>
## Search Query Parameters ##

This can be found on the API page depending on which resource you are searching:

<table style="min-width:100%;width:100%">
<tr id="clinical">
<th style="width:50%;">Medication</th>
<th style="width:50%;">Individuals</th>
</tr>
<tr>
<td><a href="api_medication_medicationorder.html">MedicationOrder</a></td>
<td><a href="api_entity_patient.html">Patient</a></td>
</tr>
<tr>
<td><a href="api_medication_medicationstatement.html">MedicationStatement</a></td>
<td></td>
</tr>
</table>
## POC Sequence Diagram ##
<p style="text-align:center;"><img src="images/engage/casestudies/bristolcc/Bristol CC Sequence Diagram.svg" alt="Sequence diagram showing the flow of information between actors" title="Sequence diagram showing the flow of information between actors" style="width:100%"></p>
<br><br>
## Acceptance Criteria ##

While the acceptance criteria is not fully developed, below is an example of some possible criteria that could be defined.

<table style="width:100%;max-width:100%"><thead><tr><th style="min-width:10em;">Feature</th><th>User Story</th></tr></thead>
<tr><td style="vertical-align: middle;">Medication List (View)</td><td>As a Pharmacist (Hospital Services) I want to retrieve all prescriptions from all available systems for a specific patient so I can build a complete list of reconciled medications for the patient.</td></tr>
<tr><td colspan="2">
<ul>
<li>I am able to call an API with the URL: GET /MedicationOrder?patient.identifier=https://fhir/nhs.net/Id/nhs-number|9876543210.</li>
<li>I am able to pass NHS number as an input parameter</li>
<li>The API returns profile "MedicationOrder" with medications information about patient as a populated JSON object in the following format: &lt;&lt;Json Object&gt;&gt;</li>
</ul>
</td></tr>
</table>


{% include custom/contribute.html content="Get in touch with to help with Case Studies of Care Connect Profiles"%}
