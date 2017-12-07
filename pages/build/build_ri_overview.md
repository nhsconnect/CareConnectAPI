---
title: Reference Implementation | Reference Implementation
keywords: design, build, access, security, overview
tags: [design, overview]
sidebar: foundations_sidebar
permalink: build_ri_overview.html
summary: "Provides an overview and background to the Reference Implementation and where this fits into the overall Care Connect API journey."
---

{% include important.html content="All information provided below is indicative and subject to on-going review." %}

# Reference Implementation #

The Reference Implementation allows developers to interact with Care Connect API profiles through server calls and an interactive website overlay. The Reference Implementation profiles exposed match the [Care Connect profiles](https://github.com/nhsconnect/CareConnect-profiles/tree/feature/stu3){:target="_blank"}. The Reference Implementation shows how these profiles can be completed with synthetic Reference Implementation data. The use of the Reference Implementation is to aid the process of designing and building Care Connect APIs by:
- providing a code base as a Reference Implementation for a Care Connect FHIR API;
- exposing the Care Connect API – in order that calls can be made; 
- providing clinically sensible search results (test data), based on predefined search parameters;
- providing a Care Connect API interface, that in its response includes Care Connect defined value sets; and
- providing valid responses and report codes where appropriate.

## Created for DEVELOPERS ##

The reference implementation has been designed for <b>DEVELOPERS</b> to interact, use and help in building Care Connect APIs.

# Context #

The Reference Implementation sits alongside a wider API delivery that INTEROPen (including NHS Digital and other supporting members) aims to produce and popularise. The Reference Implementation specified in this document sits in the following wider process.

<img src="images/reference_implementation/Ref_Impl_Overall.png" style="width:100%;max-width: 100%;">

Therefore the Reference Implementation is seen as a key way of enabling the successful and consistent use of Care Connect API profiles across all care settings. The Reference Implementation is also a key transition between the theory of the Care Connect FHIR APIs and the practicality of implementing and demonstrating the API profiles in live systems.


# Feedback #

For feedback and comments on the Reference Implementation please message the team on [INTEROPen Ryver CareConnect API](https://interopen.ryver.com/index.html#forums/1093815/chat){:target="_blank"}, or get in touch with <b><apilabs@nhs.uk></b>

For an issues with the Reference Implementation please see [Use of RI](build_ri_use.html). 

# Providing an API #

The following diagram explains the elements of APIs allowing the development of APIs:

{% include custom/provide_api.svg %}

NHS Digital is contributing to progressing the profile development (see Overview section). Invitations are open for the INTEROPen community to get involved and progress the wider developer ecosystem as defined above. 


# Contribute #

This site is structured around Care Connect stakeholders including API users, developers and architects. Please get involved in the journey.

{% include custom/api_overview.svg %}

{% include custom/contribute.html content=""%}
