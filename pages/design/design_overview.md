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
	<td>A “pattern” is a formal way of documenting a solution to a design problem in a particular field of expertise. For example, in the case of an API sharing clinical information between systems, an agreed pattern can guide the application of the standard. This may help to reduce the time to implementation and resolve ambiguity. This section highlights the patterns for information sharing between systems as outlined within <a href="https://developer.nhs.uk/library/architecture/integration-patterns/information-sharing-patterns-summary/">[developer.nhs.uk]</a>. This provides the basic framework in which to apply a variety of data exchange paradigms supported by the FHIR standard.</td>
</tr>
<tr id="step2">
	<td>Exchange Paradigms</td>
	<td>The choice of exchange paradigm can influence the format of the data, the choice of resources to include and how those resources are constructed. For example, if the content is exchanged as an attachment in an email, the attachment will typically require the complete set of the resources that make up the bundle. So this approach to data exchange will drive the need for the complete response to be returned from a single request (if there is a request at all) and the consumer may not be able to resolve any referenced data in the body of the message. In fact it would most likely drive the requirement for a FHIR Document to be created. This section describes access patterns and their influence on the access, security and use of APIs. The relationship between the requestor and responder influences the choice of access mechanism, security of payload and access adopted by the solution.</td>
</tr>
<tr id="step2">
	<td>Access</td>
	<td>The access mechanism and of requesting system is influenced by many factors. This section demonstrates the design decisions to consider when getting records of any type to support an agreed exchange paradigms and pattern. Beyond this, there may be further security, business and information governance restrictions.</td>
</tr>
<tr id="step3">
	<td>Security</td>
	<td>The security of the FHIR payload, access and data at rest are all important design decisions while building an API. Granular requests are generally easier to manage from a security perspective.</td>
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
