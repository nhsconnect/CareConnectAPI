---
title: Reference Implementation | Security Guide & Examples
keywords: design, build, access, security, overview
tags: [design, overview]
sidebar: foundations_sidebar
permalink: build_ri_security.html
summary: "Security guidance to use the CCRI"
---

{% include important.html content="All information provided below is indicative and subject to on-going review." %}

{% include warning.html content="all connections have an expiry time of 90 mins. Please referesh your OAuth2 tokens at the start of every interaction period to ensure you can connect with the Care Connect Reference Implementation." %}


## Security guide

This page provides an overview of the security guidance and access mechanisms to the Care Connect Reference Implementation (CCRI).

<p style="text-align:center;"><img src="images/build/security.png" alt="Security architecture" title="Security architecture" style="width:100%"></p>

<br>
The OAuth2 Secured resource endpoint is located at *{{ site.fhir_ref_impl_resource | xml_escape}}*

<br>
A brief summary of the Notes on secured CCRI access:
<br>
1. The data exposed by the secure Requests are identical to the standard REST Requests of the FHIR Care Connect API. The scopes demonstrated within the security demonstrate profile restriction on the HTTP REST API of a specific user/system/role. This will depend on specific systems.

2. The CCRI provides examples based on restricted Users. Each User has a set of Scopes and in order to access certain Profiles the user requires a specific Scope on their profile.

3. The security is managed by a OAuth2 Server. The OAuth2 Server is currently configured on a separate server or you can follow the instructions provided by the Care Access Service (coming soon).

Before your application can access secured CCRI API data, it must obtain an access token that grants access to that API. A single access token can grant varying degrees of access to multiple APIs. A variable parameter called scope controls the set of resources and operations that an access token permits. During the access-token request, your application sends one or more values in the scope parameter. 

If you know how to access an OAuth2 secured endpoint via tokens (server based interaction) or OAuth2 (web/app hosted interaction). There are currently two examples listed for secure access mechanisms provided within the CCRI, these are:
- [Security Authentication](build_ri_security_access.html)
- [Security Authorisation](build_ri_security_scopes.html)

Security requires a combination of [Authentication & Authorisation](design_security.html){:target="_blank"} to ensure correct access to FHIR APIs. 


## Security Authentication

Security Authentication will eventually allow a Care Connect API to be deployed into a live environment where data is hosted and shared across system and organisational boundaries. Two step by step guides have been included in the Security Authentication section which demonstrate OAuth2 :
1. Access via Postman to Authenticate and connect with the Care Connect Reference Implementation. This access mechanism would often be found between systems
2. Access via an OAuth2 negotiated server. This access mechanism would often be found between a website / mobile app and an end user


## Security Authorisation 

Security Authorisation can be managed in different ways inside Care Connect and FHIR. Within the RESTful version scopes can be defined which restrict access to profiles depending on the defined system or end user. Currently the Security Authorisation provides an example of restricting access to certain profiles. However, in the future it might be possible to dynamically create Scopes on profiles. The CCRI provides a demonstration of OAuth2 Users & Scopes.


## Resource scopes
To access any resource when security is enabled requires the definition of Resource scopes. Within FHIR the following list provides the starting point to access the CCRI.

| Resource name | Permitted scopes |
| ------------- |----------------|
| Patient | user/Patient.read |
| Observation | user/Observation.read |
| Encounter | user/Encounter.read |
| Condition | user/Condition.read |
| Procedure | user/Observation.read |
| AllergyIntolerance | user/AllergyIntolerance.read |
| MedicationRequest | user/MedicationPrescription.read |
| MedicationStatement | user/MedicationStatement.read |
| Immunization | user/Immunization.read |
| DocumentReference | user/DocumentReference |
| Binary | user/Binary |


{% include note.html content="The security described within the CCRI is a starting point to demonstrate some of the possibilities of securing a Care Connect API." %}

# Current Version #

{% include version.html %}

Check out [Versions](build_ri_version.html) for more information about the current released version, downloading options, use and future verions.


# Contribute #

This site is structured around Care Connect stakeholders including API users, developers and architects. Please get involved in the journey.

{% include custom/api_overview.svg %}

{% include custom/contribute.html content=""%}
