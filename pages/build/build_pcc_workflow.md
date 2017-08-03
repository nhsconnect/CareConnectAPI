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

## 1. Overview ##

{% include custom/usecase.html content="[University Hospital Southampton](engage_poc_uhscc.html)" %}

TODO

## 2. Task Create ##

The UHS proof of concept only required the confirmation that a task was completed. It could be said the initiating task was implied when the DiagnosticReport was received. Before we go into detail on the proof of concept we will look out how a task would be started using FHIR.

The task we are going to start is to 'Review of patient laboratory test report' which has a SNOMED CT of `324861000000109`, from a Consultant Dr Riley for the GP Dr Bhatia to carry out. The API the sender would use is:

```
POST [baseUrl]/Order
```

with this payload:

<script src="https://gist.github.com/KevinMayfield/f9e19566b9e4ad6e577f973d75b35c3c.js"></script>

The FHIR resource in the payload is very short, it's not very clear who the patient or practitioners are without following the links and retrieving the referenced resources. This is not desirable when sending Orders across system boundaries but would be an option for a mobile application working to a single FHIR server. We will cover other options in section [TODO]
We have sent a request from one practitioner to another about a patient, the report we have asked to be reviewed is referenced.

## 3. Task Amendment ##

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


## 4. Task Completed ##

TODO

```
POST [baseUrl]/OrderResponse
```

<script src="https://gist.github.com/KevinMayfield/4e8d70f2638fe79f6de4602e3e0b400b.js"></script>


Change this into a message bundle.

<script src="https://gist.github.com/KevinMayfield/5ce742eb62ab167657320d0579cfd127.js"></script>

## 5. FHIR STU3 Task ##
