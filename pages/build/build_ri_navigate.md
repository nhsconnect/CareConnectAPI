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

The Reference Implementation has been created based on clinically meaningful data.

## Mandatory links between resources
As such the mandatory links between the resources has been considered while constructing the data that supports the Ref Impl. This is shown in the diagram below.

<object style="width:100%;max-width: 100%;" type="image/svg+xml" data="images/build/Resource Dependencies (Waterfall).svg">
  <p style="text-align:center;"><img src="images/build/Resource Dependencies (Waterfall).svg" alt="The mandatory data links within the Care Connect resources." title="Mandatory data linkages within the Reference Implementation" style="width:100%;max-width: 100%;"></p>
</object>


## Data links between resources in the RI
To extend the mandatory use to provide testable (by developers) and clinically sensible information the following diagram shows the linkage of the data contained within the Reference Implementation.

<object style="width:100%;max-width: 100%;" type="image/svg+xml" data="images/build/Data Mapping.svg">
  <p style="text-align:center;"><img src="images/build/Data Mapping.svg" alt="How the data links the Care Connect resources together." title="Data linkages within the Reference Implementation" style="width:100%;max-width: 100%;"></p>
</object>

These links do not define scenarios by themselves. As such the Reference Implementation design has tried to consider a acute care setting. The data contained and linkages have **not** been clinically verified. To aid in using the logic contained within the data the following short description shows how to use the Reference Implementation to:
1. find data,
2. find connections between resources contained within the data, and
3. to explore national datasets within FHIR.


## Foundation provides the starting point
### Patient centred

Many systems support searching for Patients.

<p style="text-align:center;"><img src="images/build/Patient Search.PNG" alt="Tasks" title="View Results Screen" style="width:75%"></p>
<br><br>

To explore the CareConnect Patient search options use this link [Care Connect Reference Implementation](http://purple.testlab.nhs.uk/careconnect-ri/resource?serverId=home&pretty=false&resource=Patient)
In the example below, the screen shows two ways of calling a FHIR Server:
* Client - Code Java using HAPI libraries
* Request - A GET http request

<p style="text-align:center;"><img src="images/build/Patient Search Example.PNG" alt="Tasks" title="View Results Screen" style="width:75%"></p>
<br><br>

It is easier to stick with the web front end when initially exploring FHIR but tools such as [POSTMAN](https://www.getpostman.com/) allow much more control.

<p style="text-align:center;"><img src="images/build/PatientSearchPostman.PNG" alt="Tasks" title="View Results Screen" style="width:75%"></p>
<br><br>



[insert links to CCRI for patient ] - take example from profiles

### Practitioner provided
A national data set of practitioners available and uploaded as a demonstration.
### Treated at an identifiable organisation
Use of national datasets to provide an up to date view of a treated org.

## Care provided through

Nouns of health

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
