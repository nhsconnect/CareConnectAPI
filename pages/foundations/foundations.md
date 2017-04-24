---
title: Foundations
keywords: foundations
tags: [fhir]
sidebar: foundations_sidebar
permalink: foundations.html
summary: "All about the common foundation capabilities."
---

[<i class="fa fa-arrow-left" aria-hidden="true"/> Back to Care Connect API - Introduction.](index.html)

## Purpose ##

The foundations capability cover the basic API requirements and prerequisites to utilise the Care Connect API.

{% include important.html content="In order to successfully make us of the Care Connect APIs, initially a level of pre-existing accredited Spine connectivity will be required along with some FHIR foundation API capabilities." %}

{% include roadmap.html content="Over time the necessity to have access to pre-existing spine services (i.e. PDS and SDS integration) is likely to be replaced by FHIR based equivalents." %}

## Prerequisites ##

### PDS ###

You'll need to be able to provide a verified NHS Number to use an API. This can be achieved using a spine accredited system, a DBs batch-traced record (CSV), or using a Spine Mini Services Provider (HL7v3).

### FHIR ###

In order to be a compliant FHIR server, client systems need to expose a valid FHIR [Conformance](https://www.hl7.org/fhir/DSTU2/conformance.html) profile.

Please also refer to [Development Guidance - FHIR API Guidance - Common API Guidance](development_fhir_api_guidance.html) for full details on the common FHIR API patterns.

### API Use Cases ###

- [Care Connect API use cases](foundations_use_case_api.html)
- [Get the FHIR conformance profile](foundations_use_case_get_the_fhir_conformance_profile.html)

