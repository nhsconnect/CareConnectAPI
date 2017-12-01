---
title: Reference Implementation | Navigate around the data in the RI
keywords: design, build, access, security, overview
tags: [design, overview]
sidebar: foundations_sidebar
permalink: build_ri_navigate.html
summary: "Navigate the data contained within Reference Implementation"
---

{% include important.html content="All information provided below is indicative and subject to on-going review." %}


# How to use the Reference Implementation #

The Reference Implementation has been created based on clinically meaningful data. As such the mandatory links between the resources has been considered while constructing the data that supports the Ref Impl. This is shown in the diagram below.

[Insert Mand link picture]

To extend the mandatory use to provide testable (by developers) and clinically sensible information the following diagram shows the linkage of the data contained within the Reference Implementation.

[Insert diagram of actual data linkage with in the CCRI]

These links do not define scenarios by themselves. As such the Reference Implementation design has tried to consider a acute care setting. The data contained and linkages have **not** been clinically verified. To aid in using the logic contained within the data the following short description shows how to use the Reference Implementation to:
1. find data, 
2. find connections between resources contained within the data, and 
3. to explore national datasets within FHIR.


## Foundation provides the starting point
### Patient centred

[insert links to CCRI for patient ] - take example from profiles

### Practitioner provided
A national data set of practitioners available and uploaded as a demonstration.
### Treated at an identifiable organisation 
Use of national datasets to provide an up to date view of a treated org.

## Care provided through
### Observations

### Medications

### Prevention

## Monitored and managed
Care management within an organisation, by a practitioner on a patient are important artefacts of care. These touch points create


# Current Version #

{% include version.html version="2" function="Six Care Connect profiles with example data for one specific care setting with audit functionality" deliver="10th November 2017" %}

Check out [Versions](build_ri_version.html) for more information about the current released version, downloading options, use and future verions.


# Contribute #

This site is structured around Care Connect stakeholders including API users, developers and architects. Please get involved in the journey.

{% include custom/api_overview.svg %}

{% include custom/contribute.html content="If you want to get involved in any part of this then please get in touch with careconnect@interopen.org "%}
