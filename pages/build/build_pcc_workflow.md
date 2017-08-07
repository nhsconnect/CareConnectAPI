---
title: Diagnostics | Workflow
keywords: development
tags: [design,development,workflow,diagnostics]
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
| Acknowledgement date | Date the `DiagnosticResult` was acknowledged by the clinician | `OrderResponse.date` |
| OrderStatus | acknowledged or ignored | `OrderResponse.status` |

The relationship between the resources is shown in the diagram below:

<p style="text-align:center;"><img src="images/build/Diagnostic Task Relationship Diagram DSTU2.jpg" alt="Tasks" title="View Results Screen" style="width:75%"></p>
<br><br>

Notice the resource that indicates a task has been completed (`OrderResponse`) has no direct relationship to the Patient resource.

FHIR has a number of [exchange patterns](design_exchange_patterns.html), first we will look at Messaging approach to the solution (which resembles HL7v2 messaging) and lastly we will look at RESTful API.

{% include note.html content="The resources used will be based on CareConnect and Digital Diagnostics Services (Pathology) profiles. Order and OrderResponse are used un-profiled." %}

## FHIR Messaging ##

## 2. Task Completed (acknowledge test results) ##

As shown below the `OrderResponse` follows an `Order` but this is not present in the UHS scenario as a physical FHIR resource. It is part of the business process and found within applications. We need to have an `Order` to respond to and so we create one.

<p style="text-align:center;"><img src="images/build/UHS BPMN Basic.jpg" alt="Tasks" title="View Results Screen" style="width:75%"></p>
<br><br>

The `Order` details what action is to be done, from the UHS scenario this is `Acknowledge test results`. This is a bit ambiguous to match to a term to a code in a CodeSystem, so instead we used the action that is being performed 'Review of patient laboratory test report' which has a SNOMED CT of `324861000000109` (other more  codes can be used if required).

A FHIR Message centres around a [FHIR Bundle](https://hl7.org/fhir/DSTU2/bundle.html), the  Bundle contains a list of resources. The first resource being a MessageHeader, this has a code - the message event - that identifies the nature of the request. The other resources depend on the nature of the request with the main resource normally being the second resource in the `Bundle`, for Task Completed this is an `OrderResponse`, i.e.

| Bundle ||
|--------|-|
| MessageHeader | code = task-completed|
| OrderResponse | |
| Order | |
| Patient | |
| Practitioner [0..n] | |
| Organization [0..n]| |
| DiagnosticReport | |

This message is sent to the receiving system via a RESTful call:

```
POST [baseUrl]/Bundle
```

Example Bundle (/http payload):

<script src="https://gist.github.com/KevinMayfield/469b22b8b8440150158157f3dbc0db17.js"></script>

The `Bundle` is self contained so the receiving has enough information to process the `OrderReponse`. The resources are linked by references, e.g. the OrderResponse resource has a link to the Order request

```xml
<request>
   <reference value="#order"/>
</request>
```

The # is used to indicate this is an internal reference and within the Bundle we will find a resource with an id of `order` - which is the Order resource. Every reference in the `OrderResponse` is to an internal reference within the bundle. Other resources within the bundle may also contain references, such as the `DiagonosticReport` to results (Observations). If they we're present we would have left them as external references and not included them in the Bundle as our aim is to support handling the `OrderResponse` (and `Order`) not the `DiagnosticReport`.


## 3. Task Create (create acknowledge results) ##

The message for creating the task is similar to the task completed message with `Order` as the main resource and a different MessageHeader code.

| Bundle ||
|--------|-|
| MessageHeader | code = task-create |
| Order ||
| Patient ||
| Practitioner [0..n] ||
| Organization [0..n]||
| DiagnosticReport ||

The Message Bundle is sent using the same API but to a different system:

```
POST [baseUrl]/Bundle
```

Example Bundle (/http payload):

<script src="https://gist.github.com/KevinMayfield/2bd323a9b25e7a2fe97cfb27a46ebf58.js"></script>


## FHIR RESTful API ##

You will have noticed the FHIR Message is rather large compared to the initial UHS scenario data set. We could follow [Resource  API](https://en.wikipedia.org/wiki/Resource-oriented_architecture) for which FHIR RESTful API is well suited.

The answer is you can use either but which one depends on the scenario, if your building a web application working with a FHIR Server then FHIR RESTful API would be ideal but sending an `OrderResponse` across boundaries maybe better suited to FHIR Messaging.


## 4. Task Create ##

To create a task we use the same `Order` resource we used in the previous section and swap the internal references, to references on a FHIR Server. E.g. Within the `Order` resource our reference to the Patient was:

```xml
<subject>
   <reference value="#pat"/>
</subject>
```

With #pat referring to a Patient resource within the Bundle. With the RESTful API approach we would put in a reference to the Patient resource on a FHIR Server:

```xml
<subject>
   <reference value="https://fhir.uhs.nhs.uk/DSTU2//Patient/32898"/>
</subject>
```

`32898` is the logical Id of the Patient resource on the server.

The `Order` resource would be sent to using this API:

```
POST [baseUrl]/Order
```

Example Resource (/http payload):

<script src="https://gist.github.com/KevinMayfield/f9e19566b9e4ad6e577f973d75b35c3c.js"></script>


## 5. Task Amendment ##

We created an Order in the last step but now we wish the Patients practice to be assigned the task rather than the patients GP. Who is responsible in the Order is held in the `target` reference.

```xml
<target>
   <reference value="http://fhirtest.uhn.ca/baseDstu2/Practitioner/32368"/>
</target>
```

We change the from a Practitioner reference to the Organisation resource representing the patient's Practice.

```xml
<target>
    <reference value="http://fhirtest.uhn.ca/baseDstu2/Organization/39563"/>
</target>
```

The API we need to send this amended order is:

```
PUT [baseUrl]/Order/{Id}
```

Which uses the http PUT (Update) instead of POST used in the Create. This API has a parameter of Id (the logical Id of the resource we had previously send). If we didn't know what this was we would need to search for it, e.g. using the identifier of the original `Order`:

```
GET [baseUrl]/Order?identifier=https://fhir.uhs.nhs.uk/OrderComms/Order|ABCDE
```

This should return the id of the resource we wish to amend which we can use to update the `Order` e.g.

```
PUT [baseUrl]/Order/56443
```

Example Resource (/http payload):

<script src="https://gist.github.com/KevinMayfield/7cda2922f9aa182c4df6564cdc8ab575.js"></script>


## 6. Task Completed (/Rejected) ##

To complete a task we use `OrderResponse`, we indicate we have completed the task by giving the orderStatus a `completed` code.

```xml
<orderStatus value="completed"/>
```  

If we wished to reject the order we use the `rejected` code.

```xml
<orderStatus value="rejected"/>
```

The resource is sent to:

```
POST [baseUrl]/OrderResponse
```

Example Resource (/http payload):

<script src="https://gist.github.com/KevinMayfield/4e8d70f2638fe79f6de4602e3e0b400b.js"></script>

## 7. Task Completed (/Rejected) - UHS Scenario ##

This solution wouldn't have worked with the UHS scenario because the referenced `Order` was implied and so isn't a resource that can be referred to. This is a problem as we have been using the `Order` to link the `OrderResponse` to other resources, with messaging this wasn't a problem as the generated resource was included within the Bundle.

We can use a similar approach by using contained resources within the `OrderResponse`  

<script src="https://gist.github.com/KevinMayfield/ceb8afccd694b11889416ad30409f44a.js"></script>

We're again using `#order` to indicate a self reference in the OrderResponse like we would do in FHIR Messaging and the Order is added to the OrderResponse as a contained resource. We could add more contained resources but those resources can stand by themselves, i.e. they are complete resource.

{% include note.html content="[Guidance on contained resources](http://hl7.org/fhir/DSTU2/references.html#contained)" %}
