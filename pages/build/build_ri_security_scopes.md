---
title: Reference Implementation | Security Scopes
keywords: design, build, access, security, overview
tags: [design, overview]
sidebar: foundations_sidebar
permalink: build_ri_security_scopes.html
summary: "Reference Implementation installation instructions"
---

{% include important.html content="All information provided below is indicative and subject to on-going review." %}

{% include warning.html content="all connections have an expiry time of 90 mins. Please referesh your OAuth2 tokens at the start of every interaction period to ensure you can connect with the Care Connect Reference Implementation." %}


## HTTP Request to Get An OAuthToken
The Reference Implementation REST APIs are secured as an example using the OAuth 2.0 protocol to authorise and authenticate calls. OAuth2 is an industry open standard for authorisation, providing secure access to protected resources thereby reducing the hassle of asking for a username and password every time a user logs in. The OAuth2 Token is described below:

```
URL: {{ site.fhir_ref_impl_sec }}token?grant_type=client_credentials&client_id={Client_Id}
Method: POST
Headers:
  Accept: application/json
  Content-Type: application/x-www-form-urlencoded
  Authorization: Basic {ClientID}:{Client Secret}
```

An OAuth2 response example is shown below:

```
Expected Response:
Status Code: 200
Headers:
   Content-Type: application/json
Response Body:
{
    "access_token": "eyJhbGciOiJSUzI1NiJ9.eyJhdWQiOiI0MTNjMWZjYi0yMzVmLTQ4ZWQtYmIyOC01YzgwZTMwYjVlODQiLCJpc3MiOiJodHRwOlwvXC9wdXJwbGUudGVzdGxhYi5uaHMudWs6MjAwODBcLyIsImV4cCI6MTUxMzA5NjU3NywiaWF0IjoxNTEzMDkyOTc3LCJqdGkiOiJkNWE2MWM4Ny1iMjI5LTQ5ODctOTk3ZS01ZTJlOGZlNmIwNGQifQ.UthMhHtWWJFRFhrYV33AqJtL0nn6-Ca97-caTETRZkPZcO5quU2q5alP9Z1yJq1oSryl8lScrwScvxAOnHBWAA4tY-ViBq0m2sXjP-Gps2M_bCOmxjDV7aWOv_gou28QBus6cUHr-cocDtQXwYdzhoVMoFNmASG21ZvhDd15U6xUKHgL5J1sPGFsMmozJeI6EX99o1pwKCWLyBFHXtRp02fyXfC-IXy6EwDgZa5Vwqgwn_r9AbJ-IMQmCckQl2opQo6cD0Xn44H4jMC1iSsMhtr3PfGBoJuuWQ8aeU61hAB2XUPbH9uYHav-i8-lpE98WF088wu62qGAOTcCeGdCuQ",
    "token_type": "Bearer",
    "expires_in": 3599,
    "scope": "patient/Patient.read patient/Patient.write"
}
```

## Authorisation Header

The value in the access token element of this response will then be passed in the Authorisation Header of subsequent requests. For Example:

```
URL:  https://purple.testlab.nhs.uk/careconnect-ri/STU3/Patient/4
Method: GET
Headers:
  Authorization: "Bearer eyJhbGciOiJSUzI1NiJ9.eyJhdWQiOiI0MTNjM...88wu62qGAOTcCeGdCuQ"
```


# OAuth2 Scopes 

The following users can access Profiles within the Care Connect Reference Implementation. As such these OAuth2 users allows for the Mapping of Scopes to Profiles

| Credentials | Details (Please copy all details) |
| ------------- |----------------|
| Grant Type | Client Credentials | 
| Token name (example) | OAuth2-PatientAccess |
| Access Token URL | {{ site.fhir_ref_impl_sec }}token |
| Client Authentication | 'Send as Basic Auth header' |


## Patient Access

Can only access the patient profiles.

| Credentials | Details (Please copy all details) |
| ------------- |----------------|
| Client ID | a24a4d9f-c264-4af7-a8e5-248c24a6b707 |
| Client Secret | MMpAOGBljYcEzBfn7q9-xgJqBlmR0BSiEyCrCjNNOUpR78kZtzqgKKU_4FgGRFNWbtc6jPIErLwoYwRgnlvijA |

A full list of scopes is described below:

| Scopes | profile patient/Patient.read  user/Patient.read |

## Patient, Condition & Medication Access

Can only access a combination of patient, condition and medication profiles.

| Credentials | Details |
| ------------- |----------------|
| Client Id | ed73b2cb-abd0-4f75-b9a2-5f9c0535b82c |
| Client Secret | QOm0VcqJqa9stA1R0MJzHjCN_uYdo0PkY8OT68UCk2XDFxFrAUjajuqOvIom5dISjKshx2YiU51mXtx7W5UOwQ |


A full list of scopes is described below:

| Scopes | user/MedicationStatement.read patient/Immunization.read user/Patient.read patient/Condition.read user/MedicationOrder.read user/Condition.read user/Encounter.read profile patient/MedicationOrder.read patient/Patient.read patient/Observation.read patient/Encounter.read |

## Limited Access

Can only access Publicly Available Information.

| Credentials | Details |
| ------------- |----------------|
| Client ID | 256fcc31-97bd-47d4-acbf-12409676ad5a |
| Client Secret | AI8OGCYWjvnj-NY0zaP0H2e6_El_yO2pq43wK4YKk8UnBR_JZ5ivkmkXFtlkiL6LKWsL8H7ksab0V_Hk9c4OeMI |


A full list of scopes is described below:

| Scopes | profile |



# Current Version #

{% include version.html %}

Check out [Versions](build_ri_version.html) for more information about the current released version, downloading options, use and future verions.


# Contribute #

This site is structured around Care Connect stakeholders including API users, developers and architects. Please get involved in the journey.

{% include custom/api_overview.svg %}

{% include custom/contribute.html content=""%}
