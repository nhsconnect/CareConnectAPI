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


## Data links between resources in the RI ##
To extend the mandatory use to provide testable (by developers) and clinically sensible information the following diagram shows the linkage of the data contained within the Reference Implementation.

<object style="width:100%;max-width: 100%;" type="image/svg+xml" data="images/build/Data Mapping.svg">
  <p style="text-align:center;"><img src="images/build/Data Mapping.svg" alt="How the data links the Care Connect resources together." title="Data linkages within the Reference Implementation" style="width:100%;max-width: 100%;"></p>
</object>

These links do not define scenarios by themselves. As such the Reference Implementation design has tried to consider a acute care setting. The data contained and linkages have **not** been clinically verified. To aid in using the logic contained within the data the following short description shows how to use the Reference Implementation to:
1. find data,
2. find connections between resources contained within the data, and
3. to explore national datasets within FHIR.

## Sample linked data - Patient Identifiers ##

The table below shows a sample list of Patient identifiers which you can use to explore some of the data links contained within the Reference Implementation

<p style="text-align:center;"><img src="images/build/Sample_data_patient_id.png" alt="Sample linked data" title="Sample linked data - Patient Identifiers" style="width:100%"></p>
<br>

## Demonstration of using the Reference Implementation ##

The diagram below provides a suggested approach to explore the Reference Implementation CareConnect FHIR profiles and data contained provided with the Reference Implementation.

<p style="text-align:center;"><img src="images/build/Ref_impl_webex_demo.png" alt="Suggested demonstration of the Reference Implementation" title="A suggested approach to explore the Care Connect FHIR profiles and the data contained within the Reference Implementation. " style="width:100%"></p>
<br>

1. To begin with there is a web front end to initially explore the profiles and the data contained.
2. Using tools such as [POSTMAN](https://www.getpostman.com/){:target="_blank"} allow more control of accessing APIs

The following example shows:
1. Patient Search on a name (Name="Smith")
2. Encounter Id Request (Id=4)
3. Condition Id Request (Id=4)

To explore the CareConnect profiles using the web user interface [CareConnect Reference Implementation]({{ site.fhir_ref_impl }}resource?serverId=home&pretty=false&resource=Patient){:target="_blank"} provides a simple way to access the profile searches and can be shown simply and quickly to many audiences. As development progresses switching to a tool like [POSTMAN](https://www.getpostman.com/){:target="_blank"} can help with more detailed request and respone API inspection. In the examples below both mechanisms are demonstrated to request information from the CareConnect Reference Implementation:
* [Client - Code Java using HAPI libraries]({{ site.fhir_ref_impl }}resource?serverId=home&pretty=false&resource=Patient){:target="_blank"}
* Request - A GET http request

### 1. Patient Search ###

To explore the CareConnect Patient search options use [CareConnect Reference Implementation]({{ site.fhir_ref_impl }}resource?serverId=home&pretty=false&resource=Patient){:target="_blank"}

<p style="text-align:center;"><img src="images/build/Patient Search Example.PNG" alt="Patient Search" title="Patient Search using user interface" style="width:90%"></p>
<br>

### 2. Encounter Id Request ###

Following the logic of the data contained within the Reference Implementation the following example shows how [POSTMAN](https://www.getpostman.com/){:target="_blank"} can be used to request an encounter. API development environments like Postman allow finer control and inspection of the responses from the API. As such the diagram below shows the same patient search within Postman.

<p style="text-align:center;"><img src="images/build/PatientSearchPostman.PNG" alt="Encounter" title="View Encounter response in Postman" style="width:90%"></p>
<br>

### 3. Condition Id Request ###

Using [POSTMAN](https://www.getpostman.com/){:target="_blank"} we can easily alter the search to another resource such as Condition.

<p style="text-align:center;"><img src="images/build/PatientSearchPostmanCondition.PNG" alt="Condition" title="View Condition response in Postman" style="width:90%"></p>
<br>


# Current Version #

{% include version.html %}

Check out [Versions](build_ri_version.html) for more information about the current released version, downloading options, use and future verions.


# Contribute #

This site is structured around Care Connect stakeholders including API users, developers and architects. Please get involved in the journey.

{% include custom/api_overview.svg %}

{% include custom/contribute.html content=""%}
