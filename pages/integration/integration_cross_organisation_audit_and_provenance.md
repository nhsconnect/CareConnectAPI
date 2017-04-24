---
title: Cross Organisation Audit & Provenance
keywords: spine, ssp, integration, audit, provenance
tags: [integration]
sidebar: overview_sidebar
permalink: integration_cross_organisation_audit_and_provenance.html
summary: "Overview of how audit and provenance data is expected to be transported over the Visitors and Migrants FHIR interfaces."
---

## Cross Organisation Audit & Provenance ##

Consumer systems SHALL provided audit and provenance details in the HTTP authorization header as an oAuth bearer token (as outlined in [RFC 6749](https://tools.ietf.org/html/rfc6749){:target="_blank"}) in the form of a JSON Web Token (JWT) as defined in [RFC 7519](https://tools.ietf.org/html/rfc7519){:target="_blank"}.

### JSON Web Tokens (JWT) ###

Consumer system SHALL generate a new JWT for each API request.

| Claim | Priority | Description | Fixed Value | Dynamic Value | Specification / Example |
|-------|----------|-------------|-------------|---------------|-------------------------|
| iss | R | Client systems issuer URI | No | Yes | |
| sub | R | ID for the user on whose behalf this request is being made. Matches `requesting_practitioner.identifier.value` | No | Yes | |
| aud | R | Authorization server's `token_URL` | `https://authorize.fhir.nhs.uk/token` | No | |
| exp | R | Expiration time integer after which this authorization MUST be considered invalid. | `exp` | (now + 5 minutes) UTC time in seconds | |
| iat | R | The UTC time the JWT was created by the requesting system | `iat` | now UTC time in seconds | |
| reason_for_request | R | Purpose for which access is being requested | `directcare` | No | |
| requested_record | R | The FHIR patient resource being requested (i.e. NHS Number identifier details) | No | FHIR Patient<sup>1</sup> | Audit-Patient-1 [(Rendered)](https://fhir-test.nhs.uk/StructureDefinition/audit-patient-1) [(json)](Audit/StructureDefinitions/Audit-Patient-1.json) [(Example)](Audit/Examples/Patient.json) |
| requested_scopes | R | Data being requested | `patient/Observation.read` | No | |
| requesting_device | R | FHIR device resource making the request | No | FHIR Device<sup>1</sup> | Audit-Device-1 [(Rendered)](https://fhir-test.nhs.uk/StructureDefinition/audit-device-1) [(json)](Audit/StructureDefinitions/Audit-Device-1.json) [(Example)](Audit/Examples/Device.json) |
| requesting_organization | R | FHIR organisation resource making the request | No | FHIR Organization<sup>1</sup> | Audit-Organization-1 [(Rendered)](https://fhir-test.nhs.uk/StructureDefinition/audit-organization-1) [(json)](Audit/StructureDefinitions/Audit-Organization-1.json) [(Example)](Audit/Examples/Organization.json) |
| requesting_practitioner | R | FHIR practitioner resource making the request | No | FHIR Practitioner<sup>2</sup> | Audit-Practitioner-1 [(Rendered)](https://fhir-test.nhs.uk/StructureDefinition/audit-practitioner-1) [(json)](Audit/StructureDefinitions/Audit-Practitioner-1.json) [(Example - smartcard)](Audit/Examples/Practitioner1a.json) <br /> [(Example - non-smartcard)](Audit/Examples/Practitioner1b.json)|

<sup>1</sup> Minimal FHIR resource to include any relevant business identifier(s).

<sup>2</sup> To contain the practitioners SDS Role profile ID (taken from their SAML assertion, linked to their Smartcard session).

## JWT Example ##

```json
{
	"iss": "https://[ConsumerSystemURL]",
	"sub": "[PractitionerID]",
	"aud": "https://authorize.fhir.nhs.uk/token",
	"exp": 1469436987,
	"iat": 1469436687,
	"reason_for_request": "directcare",
	"requested_record": {
		"resourceType": "Patient",
		"identifier": [{
			"system": "https://fhir.nhs.uk/Id/nhs-number",
			"value": "[NHSNumber]"
		}]
	},
	"requested_scopes": "patient/*.read",
	"requesting_device": {
		"resourceType": "Device",
		"id": "[DeviceID]",
		"identifier": [{
			"system": "[DeviceSystem]",
			"value": "[DeviceID]"
		}],
		"type": "[SNOMEDCTCodeForTypeOfDevice]",
		"model": "[SoftwareName]",
		"version": "[SoftwareVersion]"
	},
	"requesting_organization": {
		"resourceType": "Organization",
		"id": "[OrganizationID]",
		"identifier": [{
			"system": "https://fhir.nhs.uk/Id/ods-organization-code",
			"value": "[ODSCode]"
		}],
		"name": "Requesting Organisation Name"
	},
	"requesting_practitioner": {
		"resourceType": "Practitioner",
		"id": "[PractitionerID]",
		"identifier": [{
			"system": "https://fhir.nhs.uk/sds-role-profile-id",
			"value": "[SDSRoleProfileID]"
		}]
	}
}
```

{% include important.html content="Whilst the use of a JWT and the claims naming is inspired by the [SMART on FHIR](https://github.com/smart-on-fhir/smart-on-fhir.github.io/wiki/cross-organizational-auth) NHS Digital hasn't commited to using the SMART on FHIR specification." %}

### Example Code ###

#### C# ####

{% include tip.html content="The following code snippet utilise the [Microsoft Identity Model JWT Token Nuget Package](https://www.nuget.org/packages/System.IdentityModel.Tokens.Jwt/) for creating, serializing and validating JWT tokens." %}

{% gist michaelmeasures/d6a75e52acdbee93c4c30d23e639fb1a %}

