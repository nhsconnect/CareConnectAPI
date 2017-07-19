---
title: Care Coordination | Diagnostics
keywords: development
tags: [design,development,diagnostics]
sidebar: overview_sidebar
permalink: build_pcc_diagnostics.html
summary: "Guidance on using FHIR with Laboratory and Radiology"
---

{% include custom/search.warnbanner.html %}

{% include custom/ihe.reference.html apicontent="[Observation](api_diagnostics_observation.html)" ihecontent="[IHE Laboratory (LAB) - Laboratory Testing Workflow](http://www.ihe.net/uploadedFiles/Documents/Laboratory/IHE_LAB_TF_Vol1.pdf)" patterncontent="[Message Broker](https://developer.nhs.uk/library/architecture/integration-patterns/message-broker/)" %}

## 1. Overview ##

{% include custom/usecase.html content="[University Hospital Southampton](engage_poc_uhscc.html)" %}

[Work In Progress]

Many [DiagnosticReports](http://hl7.org/fhir/DSTU2/diagnosticreport.html) will be generated from HL7v2 messages. Details on how they can be converted to [FHIR Messaging](design_exchange_patterns.html#3-messaging) can be found on this blog by [HL7 Message examples: version 2 and FHIR](http://ringholm.com/docs/04350_mapping_HL7v2_FHIR.htm). An java based example that converts HL7v2 ORU^R01 to [FHIR RESTful](design_exchange_patterns.html#2-restful-api) calls can be found on [GitHub](https://github.com/nhsconnect/careconnect-java-examples/tree/master/UHSH7v2Diagnostics)

## 2. Results ##

To find DiagnosticReports for a Patient we first need to find the patient, this is discussed in the [Patient Search](build_patient_search.html) section.

After finding the Patient we can now search for [DiagnosticReports for the Patient](api_diagnostics_diagnosticreport.html#patient)

```
GET [baseUrl]/DiagnosticReport?patient=32898
```

Which returns the following response

<script src="https://gist.github.com/KevinMayfield/f0fabda1a3464cdc940ca29b61cda41e.js"></script>

The first report is from a radiology system and contains a textual description of the report and the other is a pathology report.

## 3. Observations ##

The pathology report contains a list of Observations which can be retrieved using the guidance in [Observation](api_diagnostics_observation.html)

```
GET [baseUrl]/DiagnosticReport?patient=32898
```

Which returns the following response

<script src="https://gist.github.com/KevinMayfield/30b192d3dc590ade1e4b21a840ad7eb2.js"></script>

This may result in a large number of calls to the Observation API. Their is not a direct way of returning Observations related to the DiagnosticReport but it is possible to search on date ranges and category of Observation. So we could search for Observations with a laboratory category for that patient.

```
GET [baseUrl]/Observation?patient=32898&category=laboratory
```

This may return other laboratory Observation's not related to the DiagnosticReport we are interested in but can be filtered out by using the result list in the DiagnosticReport. Also consider applying a date range to the search.

```
GET [baseUrl]/Observation?patient=32898&category=laboratorydate=ge2017-04-24&date=le2017-04-26
```


## 4. Orders ##

The original order is referred to by the DiagnosticReports, they can also be search in a similar manner to the DiagnosticReports.

```
GET [baseUrl]/DiagnosticOrder?patient=32898
```

Which results in

<script src="https://gist.github.com/KevinMayfield/0d227ba79b2edec0dd0de36042885071.js"></script>
