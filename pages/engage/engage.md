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

### Business Requirements ###

<table>
<tr><th></th><th>Step</th><th>Description</th><th>Formal Output</th></tr>
<tr><td>1</td><td>Client's Context</td><td>Give a brief description of the client we are engaging with and what led them to the business need for interoperability.</td>Short Textual Statement<td></td></tr>
<tr><td>2</td><td>Case Overview</td><td>Description of the client's business needs and expectations.</td><td>Short Textual Statement</td></tr>
<tr><td>3</td><td>Problem Statement</td><td>Describe the current ineroperability issues.</td><ul><li>Problem Statement Diagram</li></ul><td></td></tr>
<tr><td>4</td><td>Business Requirements</td><td>Visually represent the business case to confirm understanding of the problem with the client.</td><ul><li>Business Process Model</li><li>Use Case Diagrams</li><li>User Stories</li></ul><td></td></tr>
<tr><td>5</td><td>Identify Dataset</td><td>Given that the solution is likely to be implemented against existing systems it should be straightforward to identify which data items the client wants to send or receive between those systems. Get XML representation of the data structure if possible.</td><ul><li>Data Set</li><li>Data Structure</li></ul><td></td></tr>
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
