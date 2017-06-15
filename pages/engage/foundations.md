---
title: Foundations
keywords: foundations
tags: [fhir,rest]
sidebar: foundations_sidebar
permalink: foundations.html
summary: "All about the common foundation capabilities."
---

{% include custom/search.warnbanner.html %}

## 1. Purpose ##

The foundations capability cover the basic API requirements and prerequisites to utilise the Care Connect API.

## 2. Prerequisites ##

### 2.1 NHS Number ###

Any use of NHS Number must only be with verified numbers. This can be achieved using a spine accredited system, a [Demographics Batch Service (DBS)](https://developer.nhs.uk/library/systems/demographic-batch-service-dbs/) batch-traced record (CSV), or using a [Spine Mini Services Provider (HL7v3)](https://nhsconnect.github.io/spine-smsp/) to verify the NHS Number.

### 2.2 FHIR Conformance ###

In order to be a compliant FHIR server, client systems need to expose a valid FHIR [Conformance](https://www.hl7.org/fhir/DSTU2/conformance.html) profile. See also [Care Connect API FHIR conformance profile](restfulapis_conformance_conformance.html)

Please also refer to [Development Guidance - FHIR API Guidance - Common API Guidance](design_patterns.html) for full details on the common FHIR API patterns.
