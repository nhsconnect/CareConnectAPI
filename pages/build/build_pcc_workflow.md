---
title: Workflow
keywords: development
tags: [design,development,workflow]
sidebar: overview_sidebar
permalink: build_pcc_workflow.html
summary: "Guidance on using FHIR with Workflow"
---

{% include custom/search.warnbanner.html %}

{% include custom/ihe.reference.html apicontent="[Order](api_diagnostics_order.html) <br> [OrderResponse](api_diagnostics_orderresponse.html) " ihecontent="" patterncontent="[Workflow (STU3)](https://www.hl7.org/fhir/workflow-module.html)" %}

## 1. Introduction ##

{% include custom/usecase.html content="[University Hospital Southampton](engage_poc_uhscc.html)" %}

The UHS Proof of Concept asked for some key information to be sent from the `viewer` to the 'OrderComms/LIS' system. The table below lists these items and which FHIR DSTU2 resources these fields would be found.

| OrderID | Order id of the result | `Order.identifier` |
| NHS Number | NHS number of the patient | `Patient.identifier` |
| Hospital Number | Hospital number of the patient | `Patient.identifier` |
| Surname | Last name of the patient | `Patient.name.family` |
| DOB | Date of birth of the patient | `Patient.birthDate` |
| UserID | User Id of the person who acknowledged the result | `Practitioner.identifier` |
| Acknowledgement date | Date the order result was acknowledged by the clinician | `OrderResponse.date` |
| OrderStatus | acknowledged or ignored | `OrderResponse.status` |

The relationship between the resources is shown in the diagram below:

<p style="text-align:center;"><img src="images/build/Diagnostic Task Relationship Diagram DSTU2.jpg" alt="Tasks" title="View Results Screen" style="width:75%"></p>
<br><br>

Notice the resource that indicates a task has been completed (`OrderResponse`) has no direct relationship to the Patient resource.

FHIR has a number of [exchange patterns](design_exchange_patterns.html), first we will look at Messaging approach to the solution (this resembles HL7v2 messaging) and lastly we will look at RESTful API.

{% include note.html content="The resources used will be based on CareConnect and PMIP profiles. Order and OrderResponse are used un-profiled." %}

## FHIR Messaging ##

## 2. Task Completed (acknowledge test results) ##

A FHIR Message centres around a [FHIR Bundle](https://hl7.org/fhir/DSTU2/bundle.html), the  Bundle contains a list of resources. The first resource being a MessageHeader, the second resource is the main resource which in the case of a task being completed is an `OrderResponse`, this is followed by the resources this main resource references, i.e.


| Bundle |
|--------|
| MessageHeader |
| OrderResponse |
| Order |
| Patient |
| Practitioner [0..n] |
| Organization [0..n]|
| DiagnosticReport |

What we are responding to is contained within the `Order` as a code. In this poc we have matched Acknowledge test results to 'Review of patient laboratory test report' which has a SNOMED CT of `324861000000109` (other more relevant codes can be used).

This message is sent to the recieving system via a RESTful call:

```
POST [baseUrl]/Bundle
```
with the payload being the FHIR Bundle, e.g.

<script src="https://gist.github.com/KevinMayfield/469b22b8b8440150158157f3dbc0db17.js"></script>

A number of the resources conform to CareConnect or PMIP profiles. These resources can contain references to other resources but we've avoided this not immediately relevant. Put another way we aim to supply enough information to the receiver to handle the `OrderResponse` without having to resolved these references. So the resources include information such as the Patients NHS number, Consultant/Organisation names, DiagnosticOrder id's.

## 3. Task Create (create acknowledge results) ##

Ideally an OrderResponse would have followed an Order request, in the scenario it has been implied the task exists (or is part of local business procedure's). The message for creating the task is similar to the task completed message with `Order` as the main resource.

| Bundle |
|--------|
| MessageHeader |
| Order |
| Patient |
| Practitioner [0..n] |
| Organization [0..n]|
| DiagnosticReport |

The Message Bundle is sent to the same API but to a different recieving system:

```
POST [baseUrl]/Bundle
```

<script src="https://gist.github.com/KevinMayfield/2bd323a9b25e7a2fe97cfb27a46ebf58.js"></script>


## FHIR RESTful API ##

You will have noticed the FHIR Message contained more data than was asked for in the UHS proof of concept. You may have also questioned why seeing as FHIR supports a RESTful Resource API (as specified in the Care Connect API) why didn't we go down that route.
The answer is these interactions are likely to cross organisatonal or system boundaries, so a messaging approach is deemed easier to implement.

## 4. Task Create ##

To create a task we use the same `Order` resource we used in the previous and swap the references from being self referential within the bundle to refer to references on an actual (Care Connect FHIR Server.

The API this resource would use is:

```
POST [baseUrl]/Order
```

with this payload:

<script src="https://gist.github.com/KevinMayfield/f9e19566b9e4ad6e577f973d75b35c3c.js"></script>

The FHIR resource in the payload is very short, it's not very clear who the patient or practitioners are without following the links and retrieving the referenced resources. This is not desirable when sending Orders across system boundaries.

On some systems the references may contain main identifiers such as NHS Number or ODS codes, e.g. the number 9876543210 is a NHS Number

```xml
<subject>
      <reference value="http://fhir.uhs.nhs.uk/Server/NHSNumber/Dstu2/Patient/9876543210"/>   
</subject>
```

The reference MUST be resolvable, so if the reference link was followed a single `Patient` would be returned with an id of 9876543210 (and also have a NHS number identifier with the same number).


## 5. Task Amendment ##

We created an Order in the last step but now we wish the Patients practice to be assigned the task rather than the patients GP. To do this we must first the order we created, e.g.

```
GET [baseUrl]/Order?identifier=https://fhir.uhs.nhs.uk/OrderComms/Order|ABCDE
```

This should return the id of the resource we wish to amend. This will be done via a HTTP PUT e.g.

```
PUT [baseUrl]/Order/56443
```

and payload of:

<script src="https://gist.github.com/KevinMayfield/7cda2922f9aa182c4df6564cdc8ab575.js"></script>


## 6. Task Completed (/Rejected) ##



```
POST [baseUrl]/OrderResponse
```

<script src="https://gist.github.com/KevinMayfield/4e8d70f2638fe79f6de4602e3e0b400b.js"></script>
