---
title: Reference Implementation | Security API example
keywords: design, build, access, security, overview
tags: [design, overview]
sidebar: foundations_sidebar
permalink: build_ri_security.html
summary: "Reference Implementation installation instructions"
---

{% include important.html content="All information provided below is indicative and subject to on-going review." %}

{% include warning.html content="all connections have an expiry time of 90 mins. Please referesh your OAuth2 tokens at the start of every interaction period to ensure you can connect with the Care Connect Reference Implementation." %}


## Security guide 
The following descriptions provide a high level overview of what can be accessed with the security access provided to access the Care Connect Reference Implementation. 

<p style="text-align:center;"><img src="images/build/security.png" alt="Security architecture" title="Security architecture" style="width:100%"></p>
<br>

1. The data exposed by the secure Requests are identical to the standard REST Requests of the FHIR Care Connect API. The scopes demonstrated within the security demonstrate profile restriction on the HTTP REST API of a specific user/system/role. This will depend on specific systems.

2. The Reference Implementation provides examples based on restricted Users. Each User has a set of Scopes and in order to access certain Profiles the user requires a specific Scope on their profile.


3. The security is managed by a OAuth2 Server. We have setup ours on a separate box or you can follow the instructions provided by  the Care Access Service (coming soon).
Before your application can access secured Reference Implementation API data, it must obtain an access token that grants access to that API. A single access token can grant varying degrees of access to multiple APIs. A variable parameter called scope controls the set of resources and operations that an access token permits. During the access-token request, your application sends one or more values in the scope parameter.


4. At the moment these scopes are restricted to the examples shown. In future it might be possible to dynamically create Scopes on profiles. The Reference Implementation provides a demonstration of OAuth2 Users & Scopes.

5. To aid in the use of OAuth2 with the Reference Implementation we have provided a step by step guide on using Postman to Authentice and connect with the Care Connect Reference Implementation.

## Resource scopes
Resource scope required to access (at least 1 of)

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

## Postman usage examples

The following screenshots show how to use the Care Connect Reference Implementation via Postman. The 6 steps shown below are:
1. Access Secure Endpoint
1. Select OAuth2
1. Get New Access Token
1. Request Token - please use list of [Security Scopes](build_ri_security_scopes.html){:target="_blank"}
1. Use Access Token
1. Send Secure Request

### Get new access token

Access Secure Endpoint & Select OAuth2

<p style="text-align:center;"><img src="images/build/security_1.png" alt="Access Secure Endpoint" title="Access Secure Endpoint" style="width:100%"></p>
<br>

<p style="text-align:center;"><img src="images/build/security_2.png" alt="Create Access Token" title="Create Access Token" style="width:100%"></p>
<br>

### Use Access Token

Please click the [Security Scopes](build_ri_security_scopes.html){:target="_blank"} for a list of example scopes and access tokens.

Get New Access Token (expiry 90 mins), copy the details below this screenshot.
<p style="text-align:center;"><img src="images/build/security_3.png" alt="Get New Access Token" title="Get New Access Token" style="width:80%"></p>
<br>

Create Access Token example for Patient only access, please see [Security Scopes](build_ri_security_scopes.html){:target="_blank"} for more example scopes:

| Credentials | Details (Please copy all details) |
| ------------- |----------------|
| Grant Type | Client Credentials | 
| Token name (example) | OAuth2-PatientAccess |
| Access Token URL | {{ site.fhir_ref_impl_sec }}token |
| Client ID | a24a4d9f-c264-4af7-a8e5-248c24a6b707 |
| Client Secret | MMpAOGBljYcEzBfn7q9-xgJqBlmR0BSiEyCrCjNNOUpR78kZtzqgKKU_4FgGRFNWbtc6jPIErLwoYwRgnlvijA |
| Client Authentication | 'Send as Basic Auth header' |


{% include warning.html content="all connections have an expiry time of 90 mins. Please referesh your OAuth2 tokens at the start of every interaction period to ensure you can connect with the Care Connect Reference Implementation." %}

There are three steps the first time you use the token with the Reference Implementation:
1. Get new access token
1. Ensure you only have one active token (expiry every 90 mins)
1. Use the access token in a Request (The URL is the same as before but with the https:// prefix)

<p style="text-align:center;"><img src="images/build/security_4.png" alt="Use Access Token" title="Use Access Token" style="width:100%"></p>
<br>

### Send Request

Send Secure Request
<p style="text-align:center;"><img src="images/build/security_5.png" alt="Send Secure Request" title="Send Secure Request" style="width:100%"></p>
<br>


# Current Version #

{% include version.html %}

Check out [Versions](build_ri_version.html) for more information about the current released version, downloading options, use and future verions.


# Contribute #

This site is structured around Care Connect stakeholders including API users, developers and architects. Please get involved in the journey.

{% include custom/api_overview.svg %}

{% include custom/contribute.html content=""%}
