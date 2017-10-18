---
title: Reference Implementation | Current Version of RI
keywords: design, build, access, security, overview
tags: [design, overview]
sidebar: foundations_sidebar
permalink: build_ri_version.html
summary: "Describes the current version of the Reference Implementation"
---

{% include important.html content="All information provided below is indicative and subject to on-going review." %}


# Current Version #


{% include version.html version="1" function="Provided a single read-only working Care Connect profile with demo data on a live server accessible by the public. This is also referred to as the MVP." deliver="14th October 2017" %}

To download and run the code please follow the following links.
<br/>
Code: [Download the source for Version 1](https://github.com/nhsconnect/careconnect-reference-implementation/tree/v3.1){:target="_blank"}
<br/>
Install instructions: [Deploy instructions](ccri_docker.html)

## In Scope ##

The following is a list of what is in scope for this released version of the Reference Implementation:
- Implemented using HTTP1.1 API standards
- FHIR standard STU3
- Care Connect Patient profile published on the Implementation Guide alpha v1.6
- HAPI server v2.5
- Synthetic RI data generated to complete the profile information


## Out of Scope ##

The following is a short list of out of scope:
- No clinical oversight of the information contained in the responses

# Issues #

Are recorded in the Care Connect Reference Implementation which can be found:
[Issues](https://github.com/nhsconnect/careconnect-reference-implementation/issues){:target="_blank"}

# Version Plan #

The Reference Implementation is being delivered in staged versions based on an agile approach. The Implementation Guide and these sections will be updated shortly after a Version has passed the acceptance criteria of a release. This allows the understanding of the problem and the solution to evolve while product is delivered in stages which align to 3 “Versions”. The Reference Implementation is designed to follow a typical implementation approach and as such:

| Version              |  Description    |
|+---------------------|+--------------------------------+|
| 1 | Provide a single read-only working Care Connect profile with demo data on a live server accessible by the public. This is also referred to as the MVP. |
| 2 |  Provide multiple read-only working Care Connect profiles with demo data on a live server accessible by the public. |
| 3 | Provide 14 Care Connect profiles with example data for one care setting with audit of use and accessible by both unsecure and secure API interaction. |


# Contribute #

This site is structured around Care Connect stakeholders including API users, developers and architects. Please get involved in the journey.

{% include custom/api_overview.svg %}

{% include custom/contribute.html content="If you want to get involved in any part of this then please get in touch with careconnect@interopen.org "%}
