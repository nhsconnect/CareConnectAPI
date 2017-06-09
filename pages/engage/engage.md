---
title: Engage with Care Connect
keywords: engage, care connect process, process, introduction
tags: [userstories,casestudies]
sidebar: foundations_sidebar
permalink: engage.html
summary: "These pages assist with requirements gathering and mapping stages of a FHIR API development process."
---

## Approach to Engagement ##

This process lays down steps of engagement with the client to analyse their business requirements for interoperability in a way that it supports mapping your requirements to CareConnect Profiles (that user HL7 INTEROPen FHIR standards) and enable the development of a live interface (apis) to read or exchange information/data.

It has been cited that it’s very difficult to exchange information between various business units in health care sector as most of them follow their own data structures to exchange information. This causes lot of interoperability issues and rework. Implementing this process gives us the opportunity to demonstrate and guide the business units as to how these issues can be resolved using standards- FHIR (Fast Health Information Resources) and Care Connect Profiles which adhere to interoperability standards defined by INTEROPen community (INTEROPen.org). A standardised approach will provide a common language for engagement and will more easily support a framework for sharing knowledge that can continue to assist future projects and possibly become self sustaining within the community.

## Business Benefit ##

This process will add business value by enabling businesses to easily exchange information in a common format as defined by FHIR and Profiles which is easily understood by rest of the organisation.

## The Process ##

### Agree Business Requirements ###

<table style="min-width:100%;width:100%">
<tr><th></th><th>Step</th><th>Description</th><th style="min-width:11em;">Formal Output</th></tr>
<tr><td>1</td><td>Document Client's Context</td><td>Give a brief description of the client we are engaging with and what led them to the business need for interoperability.</td><td><ul style="padding-left:1em;padding-top:0"><li style="margin:0;">Short Textual Statement</li></ul></td></tr>
<tr><td>2</td><td>Document Case Overview</td><td>Description of the client's business needs and expectations.</td><td><ul style="padding-left:1em;"><li style="margin:0;">Short Textual Statement</li></ul></td></tr>
<tr><td>3</td><td>Document Problem Statement</td><td>Describe the current ineroperability issues.</td><td><ul style="padding-left:1em;"><li style="margin:0;">Problem Statement Diagram</li></ul></td></tr>
<tr><td>4</td><td>Identify Business Requirements</td><td>Visually represent the business case to confirm understanding of the problem with the client.</td><td><ul style="padding-left:1em;"><li style="margin:0;">Business Process Model</li><li>Use Case Diagrams</li><li>User Stories</li></ul></td></tr>
<tr><td>5</td><td>Identify Dataset</td><td>Given that the solution is likely to be implemented against existing systems it should be straightforward to identify which data items the client wants to send or receive between those systems. Get XML representation of the data structure if possible.</td><td><ul style="padding-left:1em;"><li style="margin:0;">Data Set</li><li>Data Structure</li></ul></td></tr>
</table>

### Define the Solution ###

<table style="min-width:100%;width:100%">
<tr><th></th><th>Step</th><th>Description</th><th style="min-width:10em;">Formal Output</th></tr>
<tr><td>6</td><td>Identify Care Connect Profiles and FHIR Resources</td><td>Identify which Care Connect profiles and FHIR resources can be used to meet the requirement. An entity relationship diagram can help to describe the profiles.</td><td><ul style="padding-left:1em;"><li style="margin:0;">Entity Relationship Diagram</li></ul></td></tr>
<tr><td>7</td><td>Map Dataset</td><td>Map the dataset to the profile.</td><td><ul style="padding-left:1em;"><li style="margin:0;">Dataset Mapping</li></ul></td></tr>
<tr><td>8</td><td>Obtain Approval</td><td>Get Profile to Dataset Mapping reviewed and approved by the client.</td><td></td></tr>
<tr><td>9</td><td>Design API</td><td>Define API Signatures and use of Search Parameters</td><td><ul style="padding-left:1em;"><li style="margin:0;">API Signature</li><li>Search Parameters</li><li>Search Results</li></ul></td></tr>
<tr><td>10</td><td>Document Interaction Flow</td><td>Define the sequence of interactions expected including the function, input parameters, output parameters etc.</td><td><ul style="padding-left:1em;"><li style="margin:0;">API Sequence Diagram</li></ul></td></tr>
<tr><td>11</td><td>Document Additional Technical Context</td><td>Identify any further techincal considerations to aid understanding.</td><td><ul style="padding-left:1em;"><li style="margin:0;">System Diagrams</li><li>Acceptance Criteria</li></ul></td></tr>
<tr><td>12</td><td>Resolve Curation Requirements</td><td>Feedback to INTEROpen any necessary changes to Profile definitions.</td><td><ul style="padding-left:1em;"><li style="margin:0;">Updated Care Connect Standards</li></ul></td></tr>
</table>

### Deliver the Solution ###

<table style="min-width:100%;width:100%">
<tr><th></th><th>Step</th><th>Description</th><th style="min-width:10em;">Formal Output</th></tr>
<tr><td>13</td><td>Present Case Study</td><td>Present final case study to stakeholders and include it into the implementation guide.</td><td><ul style="padding-left:1em;"><li style="margin:0;">Presentation</li><li>Updated Implementation Guide</li></ul></td></tr>
<tr><td>14</td><td>Implement Solution</td><td>Client implements solution, tests and provides feedback.</td><td></td></tr>
<tr><td>15</td><td>Learning</td><td>Identify failures and successes of the project.</td><td><ul style="padding-left:1em;"><li style="margin:0;">Plan to improve processes, preventing a repeat of failure and improving success rate.</li></ul></td></tr>
</table>

## User Stories

<img src="images/engage/Interoperability Process.svg" style="width:100%;max-width: 100%;" alt="Diagram showing the project stages that would benefit most from exploring user stories and case studies." title="Diagram showing the project stages that would benefit most from exploring user stories and case studies.">

It is recommended that user stories are created to identify and document requirements. This implementation guide uses non-technical stories as the foundation for identifying requirements and mapping to Care Connect profiles. This provides a reference point to help with the identification of requirements and profiles.
Within the initial phase of the Care Connect API roadmap, on behalf of INTEROPen, NHS Digital are building a catalogue of user stories to support proof of concept work. The vision for this catalogue is that it can be opened up for direct contributions from the community providing a referenceable catalogue, linking requirements, solutions and case studies providing further education back to the community.
### Why User Stories?
User stories provide the following benefits when considering the clinical needs being addresses by the interface:
- User stories have an **emphasis on verbal communication** which removes the expectation that a detailed description is required, **deferring detail**, relying instead on a continual conversation between the customer and the provider to clarify details. This results in a lightweight (but iterative) mechanism that can be more easily understood by the clinician; ultimately making it easier for them to contribute directly. User stories are **comprehensible to everyone**, from the developer to the clinician.
- Given that it is now more readily acknowledged that we cannot identify all requirements up front, user stories support a more **opportunistic approach to development** that doesn’t rely on the clinician being able to define the exact needs in advance, and not reliant of developers fully comprehending the need from a written statement. Continual discussion of the requirements by the team also encourage **a more participatory design** approach, that **promotes the accumulation of knowledge** amongst the team, as the story is refined and elaborated throughout a development process. Ensuring a feedback loop within the Care Connect Interoperability process is essential to this approach.

The accessibility of user stories over more complex and solution specific approaches to requirements gathering that make them an ideal tool to support ongoing engagement from community.  As knowledge develops and the library of user stories grow, it will accelerate the delivery of FHIR based solutions by providing an extensive and reusable mapping. Given the suitability of user stories for planning and as a basis for an iterative development process they will also offer an asset for consumers at a management level working in an agile environment.

[Click Here](howtouserstory.html) for more information on how we create user stories for Care Connect.

[Care Connect User Stories](engage_user_stories.html)

## Case Studies

Care Connect case studies provide examples of how real world problems have been solved using Care Connect. Following a process that shows how the project evolved from gathering business requirements through to the final creation of a solution, case studies offer insight and education from the experience of other trusts and service providers.

<img src="images/engage/EngagementModel.svg" style="width:100%;max-width: 100%;" alt="Diagram showing high level stages that are discussed in each case study." title="Diagram showing high level stages that are discussed in each case study.">

The development of the Care Connect standard relies on community engagement curated by INTEROPen. Contributions can be made, either by joining the INTEROPen or simply contacting INTEROPen using the email address careconnect@interopen.org.

[Care Connect Case Studies](engage_case_studies.html)
