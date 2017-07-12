---
title: Care Coordination | Clinical
keywords: development
tags: [design,development]
sidebar: overview_sidebar
permalink: build_pcc_clinical.html
summary: "Guidance using FHIR Observation with Vital Signs"
---

{% include custom/search.warnbanner.html %}


{% include custom/ihe.reference.html apicontent="[Observation](api_diagnostics_observation.html)" ihecontent="[IHE Patient Care Coordination (PCC) - A Data Access Framework using IHE Profiles](http://www.ihe.net/uploadedFiles/Documents/PCC/IHE_PCC_White_Paper_DAF_Rev1.0_2014-03-28.pdf)" patterncontent="[Portal](https://developer.nhs.uk/library/architecture/integration-patterns/portal/)" %}

## 1. Overview ##

{% include custom/usecase.html content="A Primary Care Doctor (GP) at Jorvik Health Centre (JHC) recently ordered
an HbA1c test for a new patient with established Diabetes Type 1 diagnosis. The patient had
been to JHC several times before, but just recently switched her GP internally at JHC. The
GP received the test results for a specimen drawn on 7/5/2013 in her GP system indicating
that the patient’s HbA1c was 8.3%. Her GP would like to determine her patient’s glucose level
trend over the past 12 months.
<br><br> The GP formulates a query in her GP system to retrieve all
HbA1c results where the patient’s levels were above 7% at JHC. The GP receives a single
response of available results from one or more responding application(s) where this data was
documented. The GP is able to obtain all of the results requested from the responding
application(s). Upon receiving the results, the GP confirms that the patient’s glucose levels
have been progressively increasing based on available results for each visit since 7/5/2012. The
GP then schedules a set of diagnostic tests to aid her in developing an effective rehabilitation
plan to proactively manage her patient’s health condition. " %}

[TODO]
