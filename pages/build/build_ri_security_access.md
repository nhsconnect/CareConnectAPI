---
title: CCRI | Security Authorisation
keywords: design, build, access, security, overview
tags: [design, overview]
sidebar: foundations_sidebar
permalink: build_ri_security_access.html
summary: "Secure Authorisation to the Reference Implementation"
---

{% include important.html content="All information provided below is indicative and subject to on-going review." %}

{% include warning.html content="all connections have an expiry time of 90 mins. Please referesh your OAuth2 tokens at the start of every interaction period to ensure you can connect with the Care Connect Reference Implementation." %}

## Security Authentication

Security Authentication will eventually allow a Care Connect API to be deployed into a live environment where data is hosted and shared across system and organisational boundaries. Two step by step guides have been included in the Security Authentication section which demonstrate OAuth2 :
1. Assigned Token - Access via Postman 
2. Negotiated Token - Access via an OAuth2 negotiated server

Please click on [Security](build_ri_security.html) for background and understanding of the security considerations when creating your own implementation.


## Assigned Token

To Authenticate and connect with the CCRI via Postman emulates how a backend server might establish a secure connection. The following screenshots show how to use the Care Connect Reference Implementation via Postman. The 7 steps shown below are:
1. Access Secure Endpoint
1. Select OAuth2
1. Get New Access Token
1. Request Token - please use list of [Security Scopes](build_ri_security_scopes.html){:target="_blank"}
1. Use Access Token
1. Send Secure Request


### Get new access token

Access Secure Endpoint & Select OAuth2

<p style="text-align:center;"><img src="images/build/Security_Access_1.JPG" alt="Access Secure Endpoint" title="Access Secure Endpoint" style="width:100%"></p>
<br>

<br>

### Use Access Token

{% include note.html content="In the example below we are using a pre-defined client using `client-credentials` grant. Please check OAuth2 documentation for the most appropriate grant for your setting." %}

Please click the [Security Scopes](build_ri_security_scopes.html){:target="_blank"} for a list of example scopes and access tokens.

Get New Access Token (expiry 90 mins), copy the details below this screenshot.
<p style="text-align:center;"><img src="images/build/Security_3.JPG" alt="Get New Access Token" title="Get New Access Token" style="width:80%"></p>
<br>

Create Access Token example for Patient only access, please see [Security Scopes](build_ri_security_scopes.html){:target="_blank"} for more example scopes:

| Credentials | Details (Please copy all details) |
| ------------- |----------------|
| Grant Type | Client Credentials |
| Token name (example) | OAuth2-PatientAccess |
| Access Token URL | {{ site.fhir_ref_impl_sec }}token |
| Client ID | medication-access |
| Client Secret | IShTVi8mRSV7bVREuU1freiDo79y_8fLX3BBw2nf2eIpv9A_r91VlVuF2LOiK_zLZAkBQCusEXLp_o6DEIgvaQ |
| Client Authentication | 'Send as Basic Auth header' |


{% include warning.html content="all connections have an expiry time of 90 mins. Please referesh your OAuth2 tokens at the start of every interaction period to ensure you can connect with the Care Connect Reference Implementation." %}

There are three steps the first time you use the token with the Reference Implementation:
1. Get new access token
1. Ensure you only have one active token (expiry every 90 mins)
1. Use the access token in a Request (The URL is the same as before but with the https:// prefix)

<p style="text-align:center;"><img src="images/build/Security_4.JPG" alt="Use Access Token" title="Use Access Token" style="width:100%"></p>
<br>

### Send Request

Send Secure Request
<p style="text-align:center;"><img src="images/build/Security_5.JPG" alt="Send Secure Request" title="Send Secure Request" style="width:100%"></p>
<br>

{% include note.html content="Although the access and exchange of information is secure the contents requested, transfered and ultimately exchanged require auditing and monitoring as described in the overall API approach." %}


## Negotiated Token - OAuth2 Client ##

Access via an OAuth2 client demonstrates how a website / mobile app could interact with an end user. The starting point for this lies in the Capability Statement of a FHIR Server which indicates the location of the Authorisation Server.

<p style="text-align:center;"><img src="images/build/Security_Capability_Statement.JPG" alt="Retrieve Capability Statement" title="Retrieve Capability Statement" style="width:80%"></p>

The <b>CapabilityStatement</b> indicates secure access can be obtained by registering the client at <b>https://yellow.testlab.nhs.uk/auth/register</b>. 
As a demonstration of how this can be achieved using an Authorisation Server user interface, please follow this link below and log into the OAuth2 server using a Google Id by clicking on `Log In` (top right hand corner).
[CareConnect Authorisation Server](https://yellow.testlab.nhs.uk/auth/){:target="_blank"} 

<p style="text-align:center;"><img src="images/build/Security_OAuth2_Main.JPG" alt="OAuth2 Login" title="OAuth2 Login" style="width:80%"></p>

{% include note.html content="This provides a demonstration of a delegated authority Authorisation server using OAuth2. The information captured using the login will be used for monitoring purposes only." %}

### Register to the OAuth2 Client ###

Select 'Self-service client registration' from the menu and then select '+ New Client'.

<p style="text-align:center;"><img src="images/build/Security_OAuth2_Register1.JPG" alt="OAuth2 Register Client" title="OAuth2 Register Client" style="width:80%"></p>
Complete your details, for details on Access Scopes please see [SMART on FHIR - Scopes and Launch Context](http://docs.smarthealthit.org/authorization/scopes-and-launch-context/).

<p style="text-align:center;"><img src="images/build/Security_OAuth2_Register2.JPG" alt="OAuth2 Client Main" title="OAuth2 Client Main" style="width:50%"></p>

<p style="text-align:center;"><img src="images/build/Security_OAuth2_Register3.JPG" alt="OAuth2 Client Access" title="OAuth2 Client Access" style="width:50%"></p>

Take a note of the `client_id` and `client_secret` they will be used to establish the secure connection. The diagram below shows a redacted screenshot of a access token.

<p style="text-align:center;"><img src="images/build/Security_OAuth2_Register4.png" alt="OAuth2 Client Secret" title="OAuth2 Client Secret" style="width:80%"></p>

{% include note.html content="Record `client_id` and `client_secret` to establish the secure connection." %}


# Current Version #

{% include version.html %}

Check out [Versions](build_ri_version.html) for more information about the current released version, downloading options, use and future verions.


# Contribute #

This site is structured around Care Connect stakeholders including API users, developers and architects. Please get involved in the journey.

{% include custom/api_overview.svg %}

{% include custom/contribute.html content=""%}
