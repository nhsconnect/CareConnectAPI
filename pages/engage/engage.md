---
title: Engage with Care Connect
keywords: engage, care connect process, process, introduction
tags: [userstories,casestudies]
sidebar: foundations_sidebar
permalink: engage.html
summary: "These pages assist with requirements gathering and mapping stages of a FHIR API development process."
---

## Approach to Engagement ##

This process lays down steps of engagement with the client to analyse their business requirements for interoperability in a way that it supports mapping your requirements to CareConnect Profiles (that user HL7 INTEROPen FHIR standards) and enable the development of a live API (Application Programming Interface) to read or exchange information/data.

It has been cited that it’s very difficult to exchange information between various business units in health care sector as most of them follow their own data structures to exchange information. This causes lot of interoperability issues and rework. Implementing this process gives us the opportunity to demonstrate and guide the business units as to how these issues can be resolved using standards- FHIR (Fast Health Information Resources) and Care Connect Profiles which adhere to interoperability standards defined by INTEROPen community (INTEROPen.org). A standardised approach will provide a common language for engagement and will more easily support a framework for sharing knowledge that can continue to assist future projects and possibly become self sustaining within the community.
<br><br>
## Business Benefit ##

This process will add business value by enabling businesses to easily exchange information in a common format as defined by FHIR and Profiles which is easily understood by rest of the organisation.
<br><br>
## The Process ##

The process is broken down into 15 discrete steps that are broadly organised onto three stages: Agree Business Requirements, Define the Solution, and Deliver the Solution.

<br>
<object style="width:100%;max-width: 100%;" type="image/svg+xml" data="images/engage/EngagementApproach.svg">
  <p style="text-align:center;"><img src="images/engage/EngagementApproach.svg" alt="Diagram showing the process stages for agreeing business requirements, then defining and delivering the solution" title="Diagram showing the process stages for agreeing business requirements, then defining and delivering the solution" style="width:100%;max-width: 100%;"></p>
</object>
<br><br>
### Agree Business Requirements ###

<table style="min-width:100%;width:100%">
<thead><tr id="step1"><th style="width:3em;"></th><th style="width:11em;">Step</th><th>Description</th><th style="width:11em;">Formal Output</th></tr></thead>
<tr id="step2"><td>1</td><td>Document Client's Context</td><td>Give a brief description of the client we are engaging with and what led them to the business need for interoperability.</td><td><ul style="padding-left:1em;padding-top:0"><li style="margin:0;">Short Textual Statement</li></ul></td></tr>
<tr id="step3"><td>2</td><td>Document Case Overview</td><td>Description of the client's business needs and expectations.</td><td><ul style="padding-left:1em;"><li style="margin:0;">Short Textual Statement</li></ul></td></tr>
<tr id="step4"><td>3</td><td>Document Problem Statement</td><td>Describe the current ineroperability issues.</td><td><ul style="padding-left:1em;"><li style="margin:0;">Problem Statement Diagram</li></ul></td></tr>
<tr id="step5"><td>4</td><td>Identify Business Requirements</td><td>Visually represent the business case to confirm understanding of the problem with the client.</td><td><ul style="padding-left:1em;"><li style="margin:0;">Business Process Model</li><li>Use Case Diagrams</li><li><a href="./engage_userstories.html">User Stories</a></li></ul></td></tr>
<tr><td>5</td><td>Identify Dataset</td><td>Given that the solution is likely to be implemented against existing systems it should be straightforward to identify which data items the client wants to send or receive between those systems. Get XML representation of the data structure if possible.</td><td><ul style="padding-left:1em;"><li style="margin:0;">Data Set</li><li>Data Structure</li></ul></td></tr>
</table>
<br><br>
### Define the Solution ###

<table style="min-width:100%;width:100%">
<thead><tr id="step6"><th style="width:3em;"></th><th style="width:11em;">Step</th><th>Description</th><th style="width:11em;">Formal Output</th></tr></thead>
<tr id="step7"><td>6</td><td>Identify Care Connect Profiles and FHIR Resources</td><td>Identify which Care Connect profiles and FHIR resources can be used to meet the requirement. An entity relationship diagram can help to describe the profiles.</td><td><ul style="padding-left:1em;"><li style="margin:0;">Entity Relationship Diagram</li></ul></td></tr>
<tr id="step8"><td>7</td><td>Map Dataset</td><td>Map the dataset to the profile.</td><td><ul style="padding-left:1em;"><li style="margin:0;">Dataset Mapping</li></ul></td></tr>
<tr id="step9"><td>8</td><td>Obtain Approval</td><td>Get Profile to Dataset Mapping reviewed and approved by the client.</td><td></td></tr>
<tr id="step10"><td>9</td><td>Design API</td><td>Define API Signatures and use of Search Parameters</td><td><ul style="padding-left:1em;"><li style="margin:0;">API Signature</li><li>Search Parameters</li><li>Search Results</li></ul></td></tr>
<tr id="step11"><td>10</td><td>Document Interaction Flow</td><td>Define the sequence of interactions expected including the function, input parameters, output parameters etc.</td><td><ul style="padding-left:1em;"><li style="margin:0;">API Sequence Diagram</li></ul></td></tr>
<tr id="step12"><td>11</td><td>Document Additional Technical Context</td><td>Identify any further techincal considerations to aid understanding.</td><td><ul style="padding-left:1em;"><li style="margin:0;">System Diagrams</li><li>Acceptance Criteria</li></ul></td></tr>
<tr><td>12</td><td>Resolve Curation Requirements</td><td>Feedback to INTEROpen any necessary changes to Profile definitions.</td><td><ul style="padding-left:1em;"><li style="margin:0;">Updated Care Connect Standards</li></ul></td></tr>
</table>
<br><br>
### Deliver the Solution ###

<table style="min-width:100%;width:100%">
<thead><tr id="step13"><th style="width:3em;"></th><th style="width:11em;">Step</th><th>Description</th><th style="width:11em;">Formal Output</th></tr></thead>
<tr id="step14"><td>13</td><td>Present <a href="./engage_case_studies.html">Case Study</a></td><td>Present final case study to stakeholders and include it into the implementation guide.</td><td><ul style="padding-left:1em;"><li style="margin:0;">Presentation</li><li>Updated Implementation Guide</li></ul></td></tr>
<tr id="step15"><td>14</td><td>Implement Solution</td><td>Client implements solution, tests and provides feedback.</td><td></td></tr>
<tr><td>15</td><td>Learning</td><td>Identify failures and successes of the project.</td><td><ul style="padding-left:1em;"><li style="margin:0;">Plan to improve processes, preventing a repeat of failure and improving success rate.</li></ul></td></tr>
</table>
<br><br>
{% include custom/contribute.html content="Get in touch with careconnect@interopen.org to help with Case Studies of Care Connect Profiles"%}
