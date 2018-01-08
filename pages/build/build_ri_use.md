---
title: Reference Implementation | Use of the RI
keywords: design, build, access, security, overview
tags: [design, overview]
sidebar: foundations_sidebar
permalink: build_ri_use.html
summary: "Describes how to use the Reference Implementation while creating a Care Connect API consumer"
---

{% include important.html content="All information provided below is indicative and subject to on-going review." %}


# Use of the Reference Implementation #

The initial version of the Reference Implementation, while based on the [Resources]() contained in this Implementation Guide, is intended to support the needs of the <b>developer</b> rather than the business user. Initially these principles are considered with this focus, but if the intended audience of the Reference Implementation expands, the solution may require further development. For example, the Reference Implementation exposes an API end point that can accept a variety of http commands and a web front end overlay. There is no other form of interface to access the synthetic test data.

# In Scope #

The following is a list of what is in scope for the Reference Implementation:
- Implemented using HTTP1.1 API standards
- Use FHIR standard STU3
- Use Care Connect profiles published on the Implementation Guide alpha v1.8
- Use a HAPI RESTful server v3.0
- Use a OAuth2 security solution

The diagram below provides a high level view of the functional roles the Reference Implementation covers.
<img src="images/reference_implementation/Ref_Impl_Context.png" style="width:100%;max-width: 100%;">

# Out of Scope #

The following is a short list of out of scope:
- To provide clinically verified data.
- To provide clinically viewable Care Connect FHIR resources
- To demonstrate functionality to clinicians and other business stakeholders. The scope is restricted to being a tool for developers, to simplify the creation of reference implementaiton data.
- To start API message testing and the conformance process.
- To engage formal assurance and conformance testing based on the specification.


# Current Version #

{% include version.html %}

Check out [Versions](build_ri_version.html) for more information about the current released version, downloading options, use and future verions.


# Issues #

Are recorded in the Care Connect Reference Implementation which can be found:
[Issues](https://github.com/nhsconnect/careconnect-reference-implementation/issues){:target="_blank"}

# Contribute #

This site is structured around Care Connect stakeholders including API users, developers and architects. Please get involved in the journey.

{% include custom/api_overview.svg %}

{% include custom/contribute.html content=""%}
