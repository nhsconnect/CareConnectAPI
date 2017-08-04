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

The UHS Proof of Concept asked for some key information to be sent from the `viewer` to the 'OrderComms/LIS' system.

| OrderID | Order id of the result |
| NHS Number | NHS number of the patient |
| Hospital Number | Hospital number of the patient |
| Surname | Last name of the patient |
| DOB | Date of birth of the patient |
| UserID | User Id of the person who acknowledged the result |
| Acknowledgement date | Date the order result was acknowledged by the clinician |
| OrderStatus | acknowledged or ignored |

Within FHIR DSTU2 these fields are found within a number of resources.

| OrderID | Order id of the result | `Order.identifier` |
| NHS Number | NHS number of the patient | `Patient.identifier` |
| Hospital Number | Hospital number of the patient | `Patient.identifier` |
| Surname | Last name of the patient | `Patient.name.family` |
| DOB | Date of birth of the patient | `Patient.birthDate` |
| UserID | User Id of the person who acknowledged the result | `Practitioner.identifier` |
| Acknowledgement date | Date the order result was acknowledged by the clinician | `OrderResponse.date` |
| OrderStatus | acknowledged or ignored | `OrderResponse.status` |


# FHIR Messaging #

## 2. Task Completed (acknowledge test results) ##

Send the `OrderResponse` via FHIR Messaging is similar.

| Bundle |
|--------|
| MessageHeader |
| OrderResponse |
| Order |
| Patient |
| Practitioner (who requested the task) |
| Practitioner (who completed the task) |
| Organization |
| DiagnosticReport |

This message is also sent to:

```
POST [baseUrl]/Bundle
```

<script src="https://gist.github.com/KevinMayfield/469b22b8b8440150158157f3dbc0db17.js"></script>

## 2. Task Create using FHIR Messaging ##

As noted in the Task create section, the `Order` contains many references. For example the Patient is referred to as 'http://[baseUrl]/Patient/32898' which is fine if the baseUrl is the receiving system but if it isn't this system will need to look this up by following the reference.

This is not ideal in a number of scenarios but with FHIR Messaging we can resolve this by using a [FHIR Bundle](http://hl7.org/fhir/dstu2/bundle.html). The Bundle will be a list of resources, the first resource being a [MessageHeader](http://hl7.org/fhir/dstu2/messageheader.html), the second resource the [Order](http://hl7.org/fhir/dstu2/order.html) and then the resources the Order referenced. So for our example (from Task Amendment) this will be:

| Bundle |
|--------|
| MessageHeader |
| Order |
| Patient |
| Practitioner |
| Organization |
| DiagnosticReport |

These orders may have references themselves but in the example below these have been removed if they are not immediately relevant. Put another way we aim to supply enough information to the receiver to handle the `Order` such as the Patients NHS number, Consultant/Organisation names, DiagnosticOrder id's.

The Bundle is sent to the recipient via:

```
POST [baseUrl]/Bundle
```

<script src="https://gist.github.com/KevinMayfield/2bd323a9b25e7a2fe97cfb27a46ebf58.js"></script>


# FHIR RESTful API #

## 4. Task Create ##

The UHS proof of concept only required the confirmation that a task was completed. It could be said the initiating task was implied when the DiagnosticReport was received. Before we go into detail on the proof of concept we will look out how a task would be started using FHIR.

The task we are going to start is to 'Review of patient laboratory test report' which has a SNOMED CT of `324861000000109`, from a Consultant Dr Riley for the GP Dr Bhatia to carry out. The API the sender would use is:

```
POST [baseUrl]/Order
```

with this payload:

<script src="https://gist.github.com/KevinMayfield/f9e19566b9e4ad6e577f973d75b35c3c.js"></script>

The FHIR resource in the payload is very short, it's not very clear who the patient or practitioners are without following the links and retrieving the referenced resources. This is not desirable when sending Orders across system boundaries but would be an option for a mobile application working to a single FHIR server. We will cover other options in section [TODO]
We have sent a request from one practitioner to another about a patient, the report we have asked to be reviewed is referenced.

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

| OrderID | Order id of the result | From the `Order` referenced in OrderRespone.request |
| NHS Number | NHS number of the patient | From the `Patient` referenced in the `Order` |
| Hospital Number | Hospital number of the patient | From the `Patient` referenced in the `Order` |
| Surname | Last name of the patient | From the `Patient` referenced in the `Order` |
| DOB | Date of birth of the patient | From the `Patient` referenced in the `Order` |
| UserID | User Id of the person who acknowledged the result | From the `Practitioner` referenced by `OrderResponse.who`  |
| Acknowledgement date | Date the order result was acknowledged by the clinician | `OrderResponse.who` |
| OrderStatus | acknowledged or ignored | `OrderResponse.status` [completed or rejected]  |

```
POST [baseUrl]/OrderResponse
```

<script src="https://gist.github.com/KevinMayfield/4e8d70f2638fe79f6de4602e3e0b400b.js"></script>
