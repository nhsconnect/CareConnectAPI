---
title: Exchange Patterns
keywords: design, build
tags: [design, build]
sidebar: foundations_sidebar
permalink: design_exchange_patterns.html
summary: "The Exchange Patterns introduce the three ways of exchanging FHIR Resources using RESTful API, messaging and documents."
---

{% include custom/search.warnbanner.html %}

## 1. Exchange Paradigms ##

This section has been included to show how CareConnectAPI fits in traditional messaging and document exchanges. Also how these ways of exchanging FHIR resoources relates to Information Sharing Patterns.

## 2. RESTful API

<div markdown="span" class="alert alert-danger" role="alert"><i class="fa fa-fire"></i>  <b><a href="https://www.hl7.org/fhir/DSTU2/http.html"><b>RESTful API</b></div>

[TODO]

FHIR is described as a 'RESTful' specification based on common industry level use of the term REST. In practice, FHIR only supports Level 2 of the REST Maturity model  as part of the core specification, though full Level 3 conformance is possible through the use of extensions. Because FHIR is a standard, it relies on the standardization of resource structures and interfaces. This may be considered a violation of REST principles but is key to ensuring consistent interoperability across diverse systems.

Each "resource type" has the same set of interactions defined that can be used to manage the resources in a highly granular fashion.

Note that in this RESTful framework, transactions are performed directly on the server resource using an HTTP request/response.

### 2.1. Information Sharing Patterns ###

<table>
<tr>
<td>
 <br>Mobile / <br>Web Browser
</td>
<td></td>
</tr>
<tr>
<td>
  <a href="http://developer.nhs.uk/library/architecture/integration-patterns/portal/"><img class="alignnone size-full wp-image-9872" src="http://developer.nhs.uk/wp-content/uploads/2015/02/tn-Portal-e1422958326475.jpg" alt="tn_Portal" width="251" height="72" /></a>
</td>
<td></td>
</tr>
<tr>
<td>
<a href="http://developer.nhs.uk/library/architecture/integration-patterns/registry-repository/"><img class="alignnone size-full wp-image-9922" src="http://developer.nhs.uk/wp-content/uploads/2015/02/tn-RegistryRepository-e1422959886826.jpg" alt="tn_RegistryRepository" width="250" height="72" /></a>
</td>
<td></td>
</tr>
<tr>
<td>
<a href="http://developer.nhs.uk/library/architecture/integration-patterns/shared-repository/"><img class="alignnone size-full wp-image-9912" src="http://developer.nhs.uk/wp-content/uploads/2015/02/tn-Repository-e1422959862898.jpg" alt="tn_Repository" width="250" height="72" /></a>
</td>
<td></td>
</tr>
<tr>
<td>
 <a href="http://developer.nhs.uk/library/architecture/integration-patterns/store-and-notify/"><img class="alignnone size-full wp-image-9832" src="http://developer.nhs.uk/wp-content/uploads/2015/02/tn-StoreAndNotify-e1422958493685.jpg" alt="tn_StoreAndNotify" width="251" height="72" /></a>
</td>
<td></td>
</tr>
<tr>
<td><a href="http://developer.nhs.uk/library/architecture/integration-patterns/publish-subscribe/"><img class="alignnone size-full wp-image-16992" src="http://developer.nhs.uk/wp-content/uploads/2015/02/tn_PubSub_250.jpg" alt="tn_PubSub_250" width="250" height="72" /></a></td>
<td></td>
</tr>
</table>

### 2.2. Examples ###

- [CareConnectAPI](explore.html)
  - [GP Connect Access Record REST](https://nhsconnect.github.io/gpconnect/accessrecord_rest.html)
- [Vistors and Migrants](https://nhsconnect.github.io/visitor-and-migrants/index.html)
- [NHS e-Referral Service](https://nhsconnect.github.io/NHS-FHIR-eRS-Integration/Generated/)

## 3. Messaging ##

<div markdown="span" class="alert alert-danger" role="alert"><i class="fa fa-fire"></i>  <b><a href="https://www.hl7.org/fhir/DSTU2/messaging.html"><b>Messaging</b></div>

[TODO]

FHIR Resources can be used in a traditional messaging context, much like HL7 v2 (see [detailed comparison](https://www.hl7.org/fhir/comparison-v2.html)).

### 3.1. Information Sharing Patterns ###

<table>
<tr>
<td>
<a href="http://developer.nhs.uk/library/architecture/integration-patterns/message-broker/"><img class="alignnone size-full wp-image-9902" src="http://developer.nhs.uk/wp-content/uploads/2015/02/tn-Broker-e1422958425684.jpg" alt="tn_Broker" width="250" height="72" /></a>
</td>
<td></td>
</tr>
<tr>
<td>
<a href="http://developer.nhs.uk/library/architecture/integration-patterns/registry-repository/"><img class="alignnone size-full wp-image-9922" src="http://developer.nhs.uk/wp-content/uploads/2015/02/tn-RegistryRepository-e1422959886826.jpg" alt="tn_RegistryRepository" width="250" height="72" /></a>
</td>
<td>
To store resources in the Repository
<br>Use API to retrieve the resources
</td>
</tr>
<tr>
<td>
<a href="http://developer.nhs.uk/library/architecture/integration-patterns/shared-repository/"><img class="alignnone size-full wp-image-9912" src="http://developer.nhs.uk/wp-content/uploads/2015/02/tn-Repository-e1422959862898.jpg" alt="tn_Repository" width="250" height="72" /></a>
</td>
<td>To store resources in the Repository
<br>Use API to retrieve the resources
</td>
</tr>
<tr>
<td>
 <a href="http://developer.nhs.uk/library/architecture/integration-patterns/store-and-notify/"><img class="alignnone size-full wp-image-9832" src="http://developer.nhs.uk/wp-content/uploads/2015/02/tn-StoreAndNotify-e1422958493685.jpg" alt="tn_StoreAndNotify" width="251" height="72" /></a>
</td>
<td>To store resources in the repository
<br>and provide Notification
<br>Use API to retrieve the resources</td>
</tr>
<tr>
<td><a href="http://developer.nhs.uk/library/architecture/integration-patterns/publish-subscribe/"><img class="alignnone size-full wp-image-16992" src="http://developer.nhs.uk/wp-content/uploads/2015/02/tn_PubSub_250.jpg" alt="tn_PubSub_250" width="250" height="72" /></a></td>
<td></td>
</tr>
</table>


### 3.2. Examples ###

- [NHS FGM Service](https://nhsconnect.github.io/fgm-risk-indication-service/)
- [Social Care Assessment, Discharge and Withdrawal](https://nhsconnect.github.io/FHIR-ADW-Messaging/Generated)
- [Child Health](https://nhsconnect.github.io/Digital-Child-Health/Generated)

## 4. Documents ##

<div markdown="span" class="alert alert-danger" role="alert"><i class="fa fa-fire"></i>  <b><a href="https://www.hl7.org/fhir/DSTU2/documents.html"><b>Documents</b></div>

[TODO - Add notes about ITK/CDA]

A set of coherent information that is a statement of healthcare information, including clinical observations and services. A document is an immutable set of resources with a fixed presentation that is authored and/or attested by humans, organizations and devices.

### 4.1. Information Sharing Patterns ###

<table>
<tr>
<td>
<a href="http://developer.nhs.uk/library/architecture/integration-patterns/message-broker/"><img class="alignnone size-full wp-image-9902" src="http://developer.nhs.uk/wp-content/uploads/2015/02/tn-Broker-e1422958425684.jpg" alt="tn_Broker" width="250" height="72" /></a>
</td>
<td></td>
</tr>
<tr>
<td>
<a href="http://developer.nhs.uk/library/architecture/integration-patterns/broadcast-point-to-point-sharing/"><img  src="http://developer.nhs.uk/wp-content/uploads/2015/02/tn-PointToPoint-e1422958448799.jpg" alt="tn_PointToPoint" width="249" height="72" /></a>
</td>
<td>
</td>
</tr>
<tr>
<td>
 <a href="http://developer.nhs.uk/library/architecture/integration-patterns/store-and-notify/"><img class="alignnone size-full wp-image-9832" src="http://developer.nhs.uk/wp-content/uploads/2015/02/tn-StoreAndNotify-e1422958493685.jpg" alt="tn_StoreAndNotify" width="251" height="72" /></a>
</td>
<td>To populate the repository. <br>Use Message or API for the notification<br>Use API to retrieve the document
</td>
</tr>
</table>

### 4.2. Examples ###

- [GP Connect Composition](https://data.developer.nhs.uk/fhir/candidaterelease-170816-getrecord/Profile.GetRecordQueryResponse-HTMLView/gpconnect-carerecord-composition-1.html)
- [Transfer of Care eDischarge](https://nhsconnect.github.io/NHS-FHIR-Doc-eDischarge/Generated/)
