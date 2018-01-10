---
title: Overview | Design & Build 
keywords: design, build, access, security, overview
tags: [design, overview]
sidebar: foundations_sidebar
permalink: design_overview.html
summary: "Describes the steps required to design & build an API using the Care Connect profiles described in Explore"
---

{% include important.html content="All information provided below is indicative and subject to on-going review." %}

The Design & Build section contains descriptions of approaches and suggestions for building APIs.

<table style="min-width:100%;width:100%">
<thead><tr id="step1">
	<th style="width:11em;">Page</th>
	<th>Description</th>
	</tr></thead>
<tr id="step2">
	<td>Design Patterns / Topology</td>
	<td>Describes access patterns necessary which influence the access, security and use of APIs. Depending on the pattern or topology of the requesting and responding system. The relationship between the requestor and responder influences the choice of access mechanism, security of payload and access finally build of the system </td>
</tr>
<tr id="step2">
	<td>Access</td>
	<td>The access mechanism and of requesting system is influenced by many factors. This section demonstrates the design decisions to consider</td>
</tr>
<tr id="step3">
	<td>Security</td>
	<td>The security of the FHIR payload, access and data at rest are all important design decisions while building an API. </td>
</tr>
<tr id="step4">
	<td>Build</td>
	<td>A look at some tools and techniques to help build APIs using the Resources defined in Explore.</td>
</tr>
</table>


Please see or contribute to INTEROPen to support the wider community efforts of providing a completely defined API service.


# Providing an API #

The following diagram explains the elements of APIs allowing the development of APIs:

{% include custom/provide_api.svg %}

NHS Digital is contributing to progressing the profile development (see Overview section). Invitations are open for the INTEROPen community to get involved and progress the wider developer ecosystem as defined above. 


# Contribute #

This site is structured around Care Connect stakeholders including API users, developers and architects. Please get involved in the journey.

{% include custom/api_overview.svg %}

{% include custom/contribute.html content=""%}
