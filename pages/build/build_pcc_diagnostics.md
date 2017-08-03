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

Many [DiagnosticReport](http://hl7.org/fhir/DSTU2/diagnosticreport.html) will be generated from HL7v2 ORU messages and similarly [DiagnosticOrder](http://hl7.org/fhir/DSTU2/diagnosticorder.html) will be HLv2 ORM messages. Details on how they can be converted to [FHIR Messaging](design_exchange_patterns.html#3-messaging) can be found on this blog by [HL7 Message examples: version 2 and FHIR](http://ringholm.com/docs/04350_mapping_HL7v2_FHIR.htm). A java example which  converts a sample HL7v2 ORU^R01 message to FHIR resources calls can be found on [GitHub](https://github.com/nhsconnect/careconnect-java-examples/tree/master/UHSH7v2Diagnostics)

The diagram below is a simplified representation of the FHIR Diagnostic resources and how they link together. Note that although Observation is linked to DiagnosticReport, the link is held in the DiagnosticReport, not the Observation.

<p style="text-align:center;"><img src="images/build/Diagnostics Relationship Diagram DSTU2.jpg" alt="Entity Relationship Diagram showing abstract profiles." title="Entity Relationship Diagram of Diagnostics." style="width:75%"></p>
<br><br>

## 2. Sending Diagnostic Orders and Diagnostic Reports ##

This guide does not cover how reports and orders are sent from system to system. In FHIR this is [FHIR Messaging](design_exchange_patterns.html#3-messaging) and part of NHS Digital [Digital Diagnostics Services (Pathology)](https://nhsconnect.github.io/NHS-FHIR-DDS/Generated/). This guide covers how a mobile(/other) system would access the orders and reports via [RESTful API](design_exchange_patterns.html#2-restful-api).

Messaging may use an RESTful API call by sending the `Bundle` to a server. E.g.

```
POST [baseUrl]/Bundle
```

## 3. Retrieving Diagnostic Orders ##

To find DiagnosticReports for a Patient we first need to find the patient, this is discussed in the [Patient Search](build_patient_search.html) section.

After finding the Patient we can use the patient id to search for [DiagnosticOrders](api_diagnostics_diagnosticorder.html#patient) for the Patient.

```
GET [baseUrl]/DiagnosticOrder?patient=32898
```

Which results in

<script src="https://gist.github.com/KevinMayfield/0d227ba79b2edec0dd0de36042885071.js"></script>

## 4. Retrieving Diagnostic Reports ##

We can also use patient id to search for [DiagnosticReports for the Patient](api_diagnostics_diagnosticreport.html#patient)

```
GET [baseUrl]/DiagnosticReport?patient=32898
```

Which returns the following response

<script src="https://gist.github.com/KevinMayfield/f0fabda1a3464cdc940ca29b61cda41e.js"></script>

The first report is from a radiology system and contains a textual description of the report and the other is a pathology report.

## 5. Retrieving Observations ##

The DiagnosticReport in the previous section contains a result list of Observations, these can be used to retrieve the individual entries (See also [Observation](api_diagnostics_observation.html)). E.g.

```
GET [baseUrl]/Observation?39917
```

Which returns the following response

<script src="https://gist.github.com/KevinMayfield/30b192d3dc590ade1e4b21a840ad7eb2.js"></script>

This call would need to be repeated for each entry in the DiagnosticReport which may not be ideal. Observation doesn't have a link to the DiagnosticReport and so it doesn't have a search parameter to do this. Alternative approaches could use combination's of other CareConnectAPI search parameters e.g.
- category
  - Observations linked to DiagnosticReports will have a category code of 'laboratory'
- date range
  - Observations will have a similar effectiveDateTime/effectivePeriod to the effectiveDateTime/effectivePeriod values in the DiagnosticReport.

E.g.

```
GET [baseUrl]/Observation?patient=32898&category=laboratory
```

```
GET [baseUrl]/Observation?patient=32898&category=laboratorydate=ge2017-04-24&date=le2017-04-26
```

These are not ideal and may return other laboratory Observation's not related to the DiagnosticReport we are interested in but the result list in the DiagnosticReport can be used to filter out extraneous observations.

## 6. HL7 FHIR STU3 ##

On the STU3 version of FHIR the DiagnosticOrder has become ProcedureRequest and Observation now has a 'basedOn' property which allows the Observations to be linked to the ProcedureRequest.

<p style="text-align:center;"><img src="images/build/Diagnostics Relationship Diagram STU3.jpg" alt="Entity Relationship Diagram showing abstract profiles." title="Entity Relationship Diagram of Diagnostics." style="width:75%"></p>
<br><br>

This link allows us to search Observations based on the order that generated them.

```
GET [baseUrl]/STU3/Observation?patient=32898&basedOn=ProcedureRequest/39928
```

This may still return more Observations than we need as we may have several DiagnosticReports. (DiagnosticReports may be generated at various stages e.g. preliminary, partial, final, etc). [TODO Get feedback, this may be ok]

{% include note.html content="This `basedOn` functionality could be added to DSTU2 CareConnect Observation by using an extension." %}

## 7. Observation Results (OBR Segments) ##

HL7v2 DiagnosticReport messages have the ability to split the reports into sections. In the screen shot below, the Observations from the DiagnosticReport has been split into tests from the original DiagnosticOrder.  

[TODO OBR relates to DiagnosticOrder.items, items do not exist in STU3 and they become separate ProcedureRequests]

<p style="text-align:center;"><img src="images/build/DiagnosticReportUI.png" alt="View Results Screen" title="View Results Screen" style="width:75%"></p>
<br><br>  
