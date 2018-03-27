---
title: Get Record
keywords: design, get record, record, getting records, complete record, get complete record, access
tags: [design]
sidebar: foundations_sidebar
permalink: design_get_record.html
summary: "Getting records is dependant the providing systems access and the consuming systems request mechanisms and agreements"
---

{% include important.html content="This section provides an overview of how records can be requested using FHIR including APIs, API operations, messages, documents and extended operations" %}

FHIR is designed to support a wide variety of contexts and architectures, the most modern and granular being a RESTful API model. A RESTful API model is based on exposing operations such as create, read, update, delete (CRUD) and stateless access. This access is typically a granular way to access content and helps testing, security and monitoring of the exposed data. An important consideration of the RESTful model is that interactions are driven by the consumer of the data who will pull data by making requests to the provider when they need it. Small requests are expected from the consumer which the provider answers immediately while the consumer maintains state. This makes it possible for the consumer to provide richer experiences for end users.

```
A 'consumer' refers to either a client system or a person that has a need to retrieve data from a provider.
```

The default paradigm of FHIR often appears to be RESTful as the interactions are typically granular and suited to a 'chatty' API. However, FHIR can also be implemented with more 'chunky' interactions, traditional messaging and document exchanges. While this typically means bundling up a variety of resources into bundles for transfer, either as a message or attachment, there is often a practical desire to do the same in response to a single API query. Amongst other reasons, this could be for the convenience of the requester by simplifying the requesting code, or to improve the performance of the the supplying system due to constraints that may exist around the architecture and manner of accessing the stored information. This does start to move away from a solution that can be considered purely RESTful to a more coarse grained approach typical of Service Oriented Architectures (SOA) or Remote Procedure Calls (RPC).


# Architecture considerations #

Using CareConnect FHIR profiles to access multiple resources from a patient’s history requires the implementer (both consumer and provider) to carefully consider the following factors described in this Implementation Guide:

1. [Topologies / Patterns](design_patterns.html)  -  A “pattern” is a formal way of documenting a solution to a design problem in a particular field of expertise. For example, in the case of an API sharing clinical information between systems, an agreed pattern can guide the application of the standard. This may help to reduce the time to implementation and resolve ambiguity.
1. [Exchange Paradigms](design_exchange_patterns.html) - The choice of exchange paradigm can influence the format of the data, the choice of resources to include and how those resources are constructed. For example, if the content is exchanged as an attachment in an email, the attachment will typically require the complete set of the resources that make up the bundle. So this approach to data exchange will drive the need for the complete response to be returned from a single request (if there is a request at all) and the consumer may not be able to resolve any referenced data in the body of the message. In fact it would most likely drive the requirement for a FHIR Document to be created.
1. [Access](design_access.html) - Getting records of any type, to support an agreed exchange paradigms and pattern, may have security and information governance restrictions. Granular requests are generally easier to manage from a security perspective.

FHIR supports four exchange paradigms when accessing resources:

<table width="100%">
    <tr>
        <td width="20%">
            <b>REST</b>
        </td>
        <td width="40%">
            Small, light-weight and loosely coupled.
        </td>
        <td width="40%">
            <a target="_blank" href="https://www.hl7.org/fhir/http.html">https://www.hl7.org/fhir/http.html</a>
        </td>
    </tr>
    <tr>
        <td>
            <b>Messages</b>
        </td>
        <td>
            Multiple resources in a single exchange.
        </td>
        <td>
            <a target="_blank" href="https://www.hl7.org/fhir/messaging.html">https://www.hl7.org/fhir/messaging.html</a>
        </td>
    </tr>
    <tr>
        <td>
            <b>Documents</b>
        </td>
        <td>
            Multiple resources bundled to support data persistence and maximum compatibility.
        </td>
        <td>
            <a target="_blank" href="https://www.hl7.org/fhir/documents.html">https://www.hl7.org/fhir/documents.html</a>
        </td>
    </tr>
    <tr>
        <td>
            <b>Services</b>
        </td>
        <td>
            Custom support to address specific requirements that aren’t fully supported by other paradigms.
        </td>
        <td>
            <a target="_blank" href="https://www.hl7.org/fhir/services.html">https://www.hl7.org/fhir/services.html</a>
        </td>
    </tr>
</table>


# FHIR exchange paradigms #

The <a target="_blank" href="{{ site.fhir_ref_impl }}">CareConnect Reference Implementation (CCRI)</a> currently supports RESTful APIs as a demonstration of a FHIR API implementation. To configure the CareConnect Reference Implementation to provide complete patient records requires an examination of <a target="_blank" href="https://www.hl7.org/fhir/STU3/overview-clinical.html#2.13.4">Exchange Paradigms</a>. The choice of exchange paradigm influences the way messages are structured and can impact the choices consumers and providers make when defining a solution. Providers and consumers should have an implementation guide that describes how they have implemented their solution, equivalent to this CCIG. While this may seem obvious, when implementing API’s that are not definitive in their use it becomes increasingly important to have accessible guidance. Within the CCRI, the team is currently investigating how to configure the CCRI to provide more convenient access to a ‘complete’ patient history, the exact scope of which is not defined at this stage.
At a high-level a 'complete record' can be achieved by using one or more of the following requests in FHIR:

- RESTful APIs Standard Operation (_revinclude)
- FHIR Document request (Bundle, Composition, Binary, $document)
- Extended Operation ($getALL)

The response would then be made up of a FHIR Bundle of one of the following types, designed to present multiple Resources in a single response:
- <b>document</b> - set of immutable resources with a fixed presentation in response to a document request or extended operation
- <b>collection</b> - set of resources collected into a single bundle in response to a standard operation or an extended operation



## RESTful FHIR APIs ##

Many web services use messages to form their own domain-specific APIs. These messages incorporate common logical commands like Create, Read (i.e. Get), Update, or Delete (CRUD). Also across the health and social care domain, we have many common entities such as Patient, Practitioner, Organisation etc. For example, many systems will implement an API that allows you to search for Patients by their NHS Number, maybe called GetPatient or QueryPatient.

Because FHIR standardises the common entities of a healthcare domain, the syntax of the API and associated patterns can also be agreed and standardised. With broad adoption, and granular access to resources, a patient’s history can be compiled by the consumer to suit their own specific needs. Further to this, data does not have to be central to the provider’s system or aggregated by an intermediate solution. By using multiple requests to obtain the necessary history, each request can be targeted at a different end point (provider).

Starting with an initial query to obtain a specific resource reference:

```
GET http://yellow.testlab.nhs.uk/careconnect-ri/STU3/Patient?family=Delgado&birthdate=1942-01-30
```

A patient resource can be retrieved which contains pointers to other resources:
```
GET http://yellow.testlab.nhs.uk/careconnect-ri/STU3/Patient/1010
```

Those pointers can be any end point which is accessible to the consumer (this is an example and won’t resolve):
```
...
   "generalPractitioner": [
        {
            "reference": "https://fhir.nhs.uk/Id/G0110615",
            "display": "AYNSWORTH SH"
        }
    ],
...
```

While this may seem onerous to the end user, it would in fact be largely transparent and managed by the consuming system. A single page of the UI may send several API calls to collect all the data that it requires to function.

While accessing links from a resource that are “1 to 1” is relatively straightforward, accessing “1 to many” relationships can be more complex. While links to resources such as Practitioner are easily accessible from the Patient resource in the context of “generalPractitioner”, other contexts or resources do not link in this way. Instead, the ‘many’ side of the relationship references back to the ‘1’. For example, a Patient resource does not link to its allergies, instead AllergyIntolerance resources have a link back to the patient. Therefore, to obtain a list of allergies for a patient, all AllergyIntolerance resources must be queried for those that are related to the patient.

```
http://yellow.testlab.nhs.uk/careconnect-ri/STU3/AllergyIntolerance?patient=1010
```

So, to get a typical summary, the consumer might send the following sequence of requests…

<table width="100%">
    <tr>
        <td>
            <b>1</b>
        </td>
        <td>
            Perform search against the Patient resource to retrieve a Patient UID.
        </td>
    </tr>
    <tr>
        <td>
            <b>2</b>
        </td>
        <td>
            Request the Patient resource information using a Patient UID.
        </td>
    </tr>
    <tr>
        <td>
            <b>3</b>
        </td>
        <td>
            Search the AllergyIntolerance resource using the Patient UID.
        </td>
    </tr>
    <tr>
        <td>
            <b>4</b>
        </td>
        <td>
            Search the MedicationStatement resource using the Patient UUID.
        </td>
    </tr>
    <tr>
        <td>
            <b>5</b>
        </td>
        <td>
            Search the Condition resource using the Patient UUID and an active status.
        </td>
    </tr>
    <tr>
        <td>
            <b>6</b>
        </td>
        <td>
            Search the Encounter resource using the Patient UUID and a date range.
        </td>
    </tr>
</table>

Obtaining information in this way can be counter-intuitive to some consumers when they are used to a service based interface or a messaging solution which off up a specific way of retrieving this content in one request. Providers may also find implementing solutions this way to be very inefficient their systems depending on how they map their data and index their data.

There is nothing preventing a provider from offering extended operations to return resources bundled up in a more convenient way, while still exposing the granular, RESTful API. Further discussion around the use of extended operations is included below.


## RESTful APIs Standard Operation ##

An alternative to providing an extended operation would be to include support for the search parameters “_include” and “_revinclude” which are defined as part of the FHIR standard. Whereas a typical search will return a list of resources which are all of the type being searched, adding “_include” or “_revinclude” will return a list of matching resources and any related resources that reference the query results (which may be a different type). This allows a consumer to request a more complete bundle with a reduced number of API calls, specifying exactly what they need. The disadvantage is that the consumer could make requests to the provider which are expensive to fulfill, overloading the provider if not suitably constrained.

Appending the “_include” parameter to a request indicates to the provider that the specified resources that are related to the retrieved resources are to be included in the response. The following example returns MedicationRequests for a patient but the returned results will also include any related Patient resources.

```
GET http://yellow.testlab.nhs.uk/careconnect-ri/STU3/MedicationRequest?_include=MedicationRequest:patient&patient=1010
```

Appending the “_revinclude” parameter to a request indicates to the provider that all matching resources are returned and all other resources that refer to them.

```
GET http://yellow.testlab.nhs.uk/careconnect-ri/STU3/Encounter?_id=487&_revinclude=*
```

Consumers and providers need to take care not to request or return too many resources when using “_include” and “_revinclude”. Using recursive inclusions might lead to the retrieval of the full patient's record, or even more: resources are organized into an interlinked network and broad “_include” paths may eventually traverse all possible paths on the server. For providers, these recursive and wildcard _includes are demanding and may slow the search response time significantly.

It is at the provider’s discretion how deep to recursively evaluate the inclusions. Providers are expected to limit the number of iterations done to an appropriate level and are not obliged to honor requests to include additional resources in the search results. However, restricting returned results may bring into question the safety of the response.

## FHIR Messaging ##

While a RESTful API typically relies on the exchange of individual resources, a messaging approach would normally pull together a collection of related content (or resources) with a specific context. This collection would then be transferred in its entirety. This has the potential to reduce the number of individual transactions necessary to exchange multiple resources.

Messaging allows a service to more easily detach the message handling from the message processing and is also more prevalent in existing systems whose architecture has evolved to support message queues rather than interactive APIs. While messaging can be implemented over a variety of transport mechanisms (such as serial connections and websockets), the discussion here is focussed on frameworks claiming to be “FHIR messaging conformant” that is supported over HTTP as an API. This is in support of a vision for widespread connectivity across multiple organisations and decentralised data. 

In large organisations or in scenarios where care settings need to exchange a large quantity of data in fewer transactions, messaging might be the prefered mechanism. In these situations an API that recognises a set of related resources but does not tie them into specific procedures could be referred to as a Messaging API.

FHIR messaging still relies on a “request” being initiated, but in this case it is the provider of the information that initiates the request following an event rather than the consumer. The transfer mechanism would not be limited to HTTP but extends to any transfer protocol. Unlike FHIR over REST, a FHIR message sends a request as a “bundle” of type “message” containing a message header (MessageHeader resource). The MessageHeader describes the associated event that triggered the request and it also contains a unique identifier. MessageHeaders also have elements pointing to other MessageHeaders that they are responding to, which potentially provides a stream of messages.

HL7 define a list of 12 supported message events (<a target="_blank" href="https://www.hl7.org/fhir/STU3/valueset-message-events.html">STU3/valueset-message-events</a>) such as reporting the administration of a medicine, providing a diagnostic report etc. It is possible to define further message events (such as a Transfer of Care) using the MessageDefinition resource.
A FHIR message will have one or more of the following impacts on the receiving system:
- A change that needs to be applied to the consuming system’s data.
- A response to a query.
- A notification of an event.

If the transport mechanism for the FHIR message does not have some support for reliable messaging, there are also features within the FHIR message to assure the correct receipt of a message.
It is possible for a server to support both RESTful requests and messaging requests with the addition of the operation ‘$process-message’. The following example from the HL7 specification demonstrates a POST request which has an operation to process as an asynchronous message.

```
POST /ehr/fhir/$process-message?async=true&response-url=http://example.org/clients/ehr-lite
```

While this example returns an 200 response immediately, once processed, the consumer would be able to send a message response back to the indicated service with confirmation that the content had been processed correctly (or not).


## FHIR Documents ##

A ‘FHIR Document’ is intended to provide a statement of healthcare information, including clinical observations and services which is an immutable set of resources with a fixed presentation that is authored and/or attested by humans, organizations and devices. It is possible for a service to be conformant to ‘FHIR Documents’ if the <a target="_blank" href="https://www.hl7.org/fhir/STU3/documents.html">specific HL7 standard </a> is followed.

FHIR Documents are appealing to many organisations because they can be built around existing paper based workflows exchanging information as an Outpatient letter, Discharge Summary etc.

FHIR Documents are exchanged as FHIR Bundles of type “document”. It is expected that the first resource in the bundle will be a Composition resource followed by various other resources. Further to the supporting evidence in the Composition, resources will contain human-readable and machine-readable (structured) content. It is also possible for a FHIR Document to contain signatures, stylesheets and provenance statements.

While any FHIR resource can contain human-readable text blocks, a FHIR document is the only way a provider can apply any layout rules to the content. Technically the content will still be re-rendered by the consumer and the provider will still be dependant on how the consumer interprets any given layout expectations.

A RESTful FHIR API will normally handle a bundle as a FHIR Document when it identifies the bundle as a type ‘document’. It can also process it as:
- A Composition, which breaks up the document into its various component parts;
- Binary, which stores the entire document ‘as is’;
- A normal transaction, which processes the document as a set of resources.

An important consideration when using FHIR Documents is that all the necessary content to build the associated view should be contained within the Bundle rather than referred to with a URI.
Any FHIR request can be requested as a FHIR document using the operation ‘$document’.



## FHIR Extended Operations ##

It is possible to extend the basic interactions of a RESTful API (Create, Read, Update, Delete) with the ability to execute any custom defined operation. HL7 describe the need to add operations as being:
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

The example below (for demonstration and will not resolve) shows how a request could be created to execute an operation called getAll, which is intended to return a patient’s history.

```
GET http://yellow.testlab.nhs.uk/careconnect-ri/STU3/Patient/1010/$getAll
```

These extended operations can be applied to the base FHIR endpoint, a resource type, a resource instance or a specific version of a resource.

In the example above, we are suggesting that the $getAll operation will return the entire patient history which is likely to be undesirable (especially from the point of view of a provider or a consumer using a mobile device). It may be more likely that some parameterisation is desired so that the consumer can specify what they consider to be useful. This is supported by the extended operation in the form of <key,value> pairs in the body of the request (or appended to the URL when performing a HTTP GET).

```
GET http://yellow.testlab.nhs.uk/careconnect-ri/STU3/Patient/$getAll?subject=1010&recentEncounters=5
```

In the fabricated example above, an operation to $getAll could be qualified with parameters that restrict the returned history to a specific number of encounters. In this example, the $getAll operation may still return active allergies, conditions and current medications etc.

# Care Connect Considerations #

Other API consideration are shown below. Please click on the parts of the API process to continue your API creation journey.

<div style="text-align:center">{% include custom/provide_api.svg %}

{% include custom/contribute.html content="Get in involved and contribute to the above API considerations "%}</div>
