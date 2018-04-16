---
title: Exchange Paradigms
keywords: design, build
tags: [design, build]
sidebar: foundations_sidebar
permalink: design_exchange_patterns.html
summary: "The Exchange Paradigms introduce ways of implementing FHIR Resources using RESTful API, messaging and documents."
---

{% include custom/search.warnbanner.html %}

FHIR is designed to support a wide variety of contexts and architectures which are explored here as Exchange Paradigms for the various Information Sharing Patterns. The most modern and granular paradigm is the RESTful API model. A RESTful API model is based on exposing operations such as create, read, update, delete (CRUD) and stateless access. This access is typically a granular way to access content and helps testing, security and monitoring of the exposed data. An important consideration of the RESTful model is that interactions are driven by the consumer of the data who will pull data by making requests to the provider when they need it. Small requests are expected from the consumer which the provider answers immediately while the consumer maintains state. This makes it possible for the consumer to provide richer experiences for end users.

```
A 'consumer' refers to either a client system or a person that has a need to retrieve data from a provider.
```

The Exchange Paradigms are complimentary, each having it's strengths and weaknesses. A solution may combine Information Sharing Patterns or Exchange Paradigms.  

## RESTful API ##

<div markdown="span" class="alert alert-danger" role="alert"><i class="fa fa-fire"></i>  <b><a href="{{ site.hl7_baseurl.stu3 }}http.html"><b>FHIR RESTful API</b></div>

```
Retrieve data held in a remote system while avoiding direct coupling to remote procedures.
```

<p style="text-align:center;"><img src="images/build/FHIR RESTfulAPI.jpg" alt="View Results Screen" title="View Results Screen" style="width:75%"></p>
<br><br>  

Many web services use messages to form their own domain-specific APIs. These messages incorporate common logical commands like Create, Read (i.e. Get), Update, or Delete (CRUD). Also across the health and social care domain, we have many common entities such as Patient, Practitioner, Organisation, etc. For example, many systems will implement an API that allows you to search for Patients by their NHS Number, maybe called GetPatient, QueryPatient, CreatePatient, etc.

Rather than implementing a system specific API, we could utilise standards defined in the HTTP specification (i.e. GET, POST, etc) and standarise how we return the payload.

So rather than a wide variety of GetPatient, QueryPatient we have:

<table style="width:60%;margin-left:auto;margin-right:auto">
    <col width="50%">
    <tr>
        <td>
            <b>GET Request</b>
        </td>
        <td>
            <b>Response (server)</b>
        </td>
    </tr>
    <tr>
        <td>
            URI
        </td>
        <td>
            FHIR Resource <br> E.g. Patient
        </td>
    </tr>
</table>

<table style="width:60%;margin-left:auto;margin-right:auto">
    <col width="50%">
    <tr>
        <td>
            <b>POST/PUT Request</b>
        </td>
        <td>
            <b>Response (server)</b>
        </td>
    </tr>
    <tr>
        <td>
            URI + FHIR Resource <br> Patient
        </td>
        <td>
            FHIR Resource <br> E.g. OperationOutcome
        </td>
    </tr>
</table>

<table style="width:60%;margin-left:auto;margin-right:auto">
    <col width="50%">
    <tr>
        <td>
            <b>DELETE Request</b>
        </td>
        <td>
            <b>Response (server)</b>
        </td>
    </tr>
    <tr>
        <td>
            URI
        </td>
        <td>
            FHIR Resource <br> E.g. OperationOutcome
        </td>
    </tr>
</table>


This type of interface may also be called as **ResourceAPI** and is useful for real time applications and mobile/web based access.

**Benefits**
- Mobile and web application friendly, can be reused for messaging simplifying interfacing.
- Quick to develop
- Real Time Systems
- Uses modern web technologies
- Can be used with modern security and consent technologies ([OAuth2](https://oauth.net/2/), [OpenID](http://openid.net/what-is-openid/), [SMART on FHIR](http://docs.smarthealthit.org/))

**Concerns**
- Less suitable for large transfers of data between organisations and large systems.

{% include note.html content="Please click on [Care Connect Reference Implementation](/build_ri_overview.html) which describes the RESTful API Care Connect Reference Implementaion and try using, deveoping and improving the CCRI."%}


### Information Sharing Patterns ###

The following table highlights a number of information sharing patterns as described in the NHS Developer network.

<table style="width:80%;margin-left:auto;margin-right:auto">
<tr>
<td>
<a target='_blank' href="http://developer.nhs.uk/library/architecture/integration-patterns/portal/"><img class="alignnone size-full wp-image-9872" src="http://developer.nhs.uk/wp-content/uploads/2015/02/tn-Portal-e1422958326475.jpg" alt="tn_Portal" width="251" height="72" /></a>
</td>
<td></td>
</tr>
<tr>
<td>
<a target='_blank' href="http://developer.nhs.uk/library/architecture/integration-patterns/registry-repository/"><img class="alignnone size-full wp-image-9922" src="http://developer.nhs.uk/wp-content/uploads/2015/02/tn-RegistryRepository-e1422959886826.jpg" alt="tn_RegistryRepository" width="250" height="72" /></a>
</td>
<td style="vertical-align:middle">Consider using Messaging to populate the Repository</td>
</tr>
<tr>
<td>
<a target='_blank' href="http://developer.nhs.uk/library/architecture/integration-patterns/shared-repository/"><img class="alignnone size-full wp-image-9912" src="http://developer.nhs.uk/wp-content/uploads/2015/02/tn-Repository-e1422959862898.jpg" alt="tn_Repository" width="250" height="72" /></a>
</td>
<td style="vertical-align:middle">Consider using Messaging to populate the Repository</td>
</tr>
<tr>
<td>
 <a target='_blank' href="http://developer.nhs.uk/library/architecture/integration-patterns/store-and-notify/"><img class="alignnone size-full wp-image-9832" src="http://developer.nhs.uk/wp-content/uploads/2015/02/tn-StoreAndNotify-e1422958493685.jpg" alt="tn_StoreAndNotify" width="251" height="72" /></a>
</td>
<td></td>
</tr>
<tr>
<td><a target='_blank' href="http://developer.nhs.uk/library/architecture/integration-patterns/publish-subscribe/"><img class="alignnone size-full wp-image-16992" src="http://developer.nhs.uk/wp-content/uploads/2015/02/tn_PubSub_250.jpg" alt="tn_PubSub_250" width="250" height="72" /></a></td>
<td></td>
</tr>
</table>

### NHS FHIR Examples (RESTful) ###

- [CareConnectAPI](explore.html)
- [GP Connect]({{ site.nhsd.gpconnectmain }})
  - [Tranche 1-3](https://nhsconnect.github.io/gpconnect/accessrecord_rest.html)
  - [Appointment](https://www.simplifier.net/GPConnect/gpconnect-appointment-1)
  - [Order (Task)](https://data.developer.nhs.uk/fhir/candidaterelease-170816-tasks/Profile.TaskManagement/gpconnect-task-order-1.html)
  - [Slot (Appointment)](https://www.simplifier.net/GPConnect/gpconnect-slot-1)
- [Vistors and Migrants](https://nhsconnect.github.io/visitor-and-migrants/index.html)
- [NHS e-Referral Service](https://nhsconnect.github.io/NHS-FHIR-eRS-Integration/Generated/)
- [NHS National Record Locator Service](https://data.developer.nhs.uk/fhir/nrls-v1-draft-a/Chapter.1.About/index.html)

## Messaging ##

<div markdown="span" class="alert alert-danger" role="alert"><i class="fa fa-fire"></i>  <b><a href="{{ site.hl7_baseurl.stu3 }}messaging.html"><b>FHIR Messaging</b></div>

```
Send notifications and other information to remote systems while avoiding direct coupling to remote procedures.
```
<p style="text-align:center;"><img src="images/build/FHIR Messaging.jpg" alt="View Results Screen" title="View Results Screen" style="width:75%"></p>
<br><br>  

There are many scenarios where messaging can't be driven entirely by the consumer. This is especially true in large organisations or in scenarios where health and social care organisations need to exchange data. In these situations we need an API that recognises a set of related resources but does not tie them into specific procedures, this may also be called a **MessagingAPI**.

For example a Referral Request will typically contain supporting information such as a referral letter, images/scans, or other resources relevant to the referral. While the requester determines the makeup of the Referral Request and other resources, the receiving service will determine how this is handled. The requester may block (synchronous) traffic while waiting for a response but typically the response will be generated later (asynchronously).


<table style="width:30%;margin-left:auto;margin-right:auto">
    <tr>
        <td>
            <b>Request (FHIR Bundle)</b>
        </td>
    </tr>
    <tr>
        <td>
            FHIR MessageHeader
        </td>
    </tr>
    <tr>
        <td>
            Main FHIR Resource <br> (e.g. ReferralRequest)
        </td>
    </tr>
    <tr>
        <td>
            Other FHIR Resources
        </td>
    </tr>
</table>


**Benefits**
- Established and mature pattern in Health and Social Care domain
- Process isolation, useful for communication between organisations and large systems.

**Concerns**
- Not suitable mobile or browser use
- Information Governance concerns especially when used with broadcast pattern.
- Messages need handling, this may be unnecessary for small transactions

### Information Sharing Patterns ###

<table style="width:80%; margin-left:auto; margin-right:auto">
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
<a href="http://developer.nhs.uk/library/architecture/integration-patterns/registry-repository/"><img class="alignnone size-full wp-image-9922" src="http://developer.nhs.uk/wp-content/uploads/2015/02/tn-RegistryRepository-e1422959886826.jpg" alt="tn_RegistryRepository" width="250" height="72" /></a>
</td>
<td style="vertical-align:middle">
To store resources in the Repository
<br>Use API to retrieve the resources
</td>
</tr>
<tr>
<td>
<a href="http://developer.nhs.uk/library/architecture/integration-patterns/shared-repository/"><img class="alignnone size-full wp-image-9912" src="http://developer.nhs.uk/wp-content/uploads/2015/02/tn-Repository-e1422959862898.jpg" alt="tn_Repository" width="250" height="72" /></a>
</td>
<td style="vertical-align:middle">To store resources in the Repository
<br>Use API to retrieve the resources
</td>
</tr>
<tr>
<td>
 <a href="http://developer.nhs.uk/library/architecture/integration-patterns/store-and-notify/"><img class="alignnone size-full wp-image-9832" src="http://developer.nhs.uk/wp-content/uploads/2015/02/tn-StoreAndNotify-e1422958493685.jpg" alt="tn_StoreAndNotify" width="251" height="72" /></a>
</td>
<td style="vertical-align:middle">To store resources in the repository
<br>and provide Notification
<br>Use API to retrieve the resources</td>
</tr>
<tr>
<td><a href="http://developer.nhs.uk/library/architecture/integration-patterns/publish-subscribe/"><img class="alignnone size-full wp-image-16992" src="http://developer.nhs.uk/wp-content/uploads/2015/02/tn_PubSub_250.jpg" alt="tn_PubSub_250" width="250" height="72" /></a></td>
<td></td>
</tr>
</table>


### NHS FHIR Examples (Messaging)###

- [NHS FGM Service]({{ site.nhsd.fgm }})
- [Social Care Assessment, Discharge and Withdrawal]({{ site.nhsd.scadw }})
- [Child Health]({{ site.nhsd.child_health }})
- [Digital Diagnostics Services (Pathology)]({{ site.nhsd.dds_link }})
- [Transfer of Care eDischarge]({{ site.nhsd.toc }})

## Documents ##

<div markdown="span" class="alert alert-danger" role="alert"><i class="fa fa-fire"></i>  <b><a href="{{ site.hl7_baseurl.stu3 }}documents.html"><b>FHIR Documents</b></div>

```
Send documents to remote systems while avoiding direct coupling to remote procedures.
```

<p style="text-align:center;"><img src="images/build/FHIR Documents.jpg" alt="View Results Screen" title="View Results Screen" style="width:75%"></p>
<br><br>  

A FHIR Document may be sent as the payload of a RESTful Response, Message or any Exchange Paradigm or Information Sharing Pattern. It provides a set of coherent information that is a statement of healthcare information, including clinical observations and services. A document is an immutable set of resources with a fixed presentation that can be authored and/or attested by humans, organizations and devices.

<table style="width:30%;margin-left:auto;margin-right:auto">
    <tr>
        <td>
            <b>Request (FHIR Bundle)</b>
        </td>
    </tr>
    <tr>
        <td>
            FHIR Composition
        </td>
    </tr>
    <tr>
        <td>
            Other FHIR Resources
        </td>
    </tr>
</table>


**Benefits**
- Formatted for human readability using structured headings [PRSB](http://theprsb.org/)
- Static coherent statement of health care at fixed point in time.
- Can be generated on demand to provide a current statement of Patient care.

**Concerns**
- More complex to develop

### Information Sharing Patterns ###

<table style="width:80%;margin-left:auto;margin-right:auto">
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
<td style="vertical-align:middle">To populate the repository. <br>Use Message or API for the notification<br>Use API to retrieve the document
</td>
</tr>
</table>

### NHS FHIR Examples (Documents)###

- [GP Connect](/gpconnect/)
  - [Composition](https://data.developer.nhs.uk/fhir/candidaterelease-170816-getrecord/Profile.GetRecordQueryResponse-HTMLView/gpconnect-carerecord-composition-1.html)
- [Transfer of Care eDischarge]({{ site.nhsd.toc }})

## Operations ##
<div markdown="span" class="alert alert-danger" role="alert"><i class="fa fa-fire"></i>  <b><a href="{{ site.hl7_baseurl.stu3 }}operations.html"><b>Operations</b></div>

```
Execute a procedure on a remote system while avoiding direct coupling.
```

When providing a API, a number of operations may be available to support needs such as create, read, update, delete etc. These are widely documented in the form of POST, GET, PUT, DELETE etc. and provider and consumer are expected to understand these and simply declare which operations are supported by their API.

It is possible also possible to extend these basic interactions with a custom defined operation. HL7 describe the need to add operations as being:
- “Where the server needs to play an active role in formulating the content of the response, not merely return existing information.”
- “Where the intended purpose is to cause side effects such as the modification of existing resources, or creation of new resources.”

HL7 suggest that an operation has the following properties:
- Each operation has a name
- Each operation has a list of 'in' and 'out' parameters
- Parameters are either resources, data types, or search parameters
- Operations are subject to the same security constraints and requirements as the RESTful API
- The URIs for the operation end-points are based on the existing RESTful API address scheme
- Operations may make use of the existing repository of resources in their definitions
- Operations may be performed on a specific resource, a resource type, or a whole system

Using an extended operation to support the retrieval of a predefined set of resources as discussed above, there is an inherent risk of making a provider’s API more tightly coupled to specific consumers, requiring that they have a previously agreed contract and an understanding of these specific operations. Operations designed to meet one consumer’s needs may not be appropriate for subsequent consumers.

### NHS FHIR Examples (Extended Operations)###

- [GP Connect ($getAll)](/gpconnect/)
