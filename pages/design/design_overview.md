---
title: Overview | Design 
keywords: design, build, access, security, overview
tags: [design, overview]
sidebar: foundations_sidebar
permalink: design_overview.html
summary: "Describes the steps required to design & build an API using the Care Connect profiles described in Explore"
---

{% include important.html content="All information provided below is indicative and subject to on-going review." %}

The Design & Build section contains descriptions of approaches and suggestions for building APIs.

<table style="min-width:100%;width:100%">
<thead><tr>
	<th style="width:11em;">Page</th>
	<th>Description</th>
	</tr></thead>
<tr id="step1">
	<td>Information Sharing Patterns</td>
	<td>Describes the approaches to information sharing between systems as outlined within <a href="https://developer.nhs.uk/library/architecture/integration-patterns/information-sharing-patterns-summary/">[developer.nhs.uk]</a>. This provides the basic framework in which to apply a variety of data exchange paradigms supported by the FHIR standard.</td>
</tr>
<tr id="step2">
	<td>Exchange Paradigms</td>
	<td>Describes access patterns necessary which influence the access, security and use of APIs. Depending on the Information Sharing Pattern or topology of the requesting (consuming) and responding (providing) system. The relationship between the requestor and responder influences the choice of access mechanism, security of payload and access adopted by the solution.</td>
</tr>
<tr id="step2">
	<td>Access</td>
	<td>The access mechanism and of requesting system is influenced by many factors. This section demonstrates the design decisions to consider.</td>
</tr>
<tr id="step3">
	<td>Security</td>
	<td>The security of the FHIR payload, access and data at rest are all important design decisions while building an API.</td>
</tr>
<tr id="step4">
	<td>Get Record</td>
	<td>Discussion around an extended operation implemented to simplify the need to retreive mulitple resources for a patient, providing a full history in a single request.</td>
</tr>
</table>


Please see or contribute to INTEROPen to support the wider community efforts of providing a completely defined API service.


# Providing an API #

The following diagram explains the elements of APIs allowing the development of APIs:

<div style="text-align:center">{% include custom/provide_api.svg %}

{% include custom/contribute.html content="Get in involved and contribute to the above API considerations "%}</div>
