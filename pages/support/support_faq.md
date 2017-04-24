---
title: Frequently Asked Questions (FAQ)
keywords: support, faq, questions
tags: [support]
toc: false
sidebar: overview_sidebar
permalink: support_faq.html
summary: "Frequently Asked Questions (FAQ)."
---

#### Why are you not using the latest version of FHIR (DSTU3)? ####

As DSTU3 hasn’t yet been balloted the current version of FHIR is still DSTU2 and will be until later this year. Grahame Grieve has recently posted an update on his [OnFHIR blog](https://onfhir.hl7.org) around the next version of FHIR being a STU3 release with a tentative target release date of March 31st 2017.

As outlined in the [FHIR Timelines](development_fhir_api_guidance.html#fhir-timelineshttphl7orgfhirtimelineshtml) section uplifting to newer versions of the FHIR standard is expected (in the sense that in principle it shouldn’t come as a surprise to anyone, as we’re utilising what is currently still a draft standard after all). The mechanism and timing of uplifts will be agreed by the INTEROPen&reg; Community.

#### Why are you mandating support for both XML and JSON formats? ####

Both JSON and XML serialisation formats are in scope for a number of reasons. After surveying the existing major FHIR implementations they almost all support both JSON and XML. As a FHIR back-end service it is important to enable ‘low impedance’ integration with both traditional server/desktop applications (which often use XML) and mobile/web applications (which are largely JSON). Obviously, when establishing a new open API ecosystem we want to be as open and inclusive as possible and hence feel that excluding either format would be a divisive move. 
Several existing open source FHIR libraries exist which already supports both serialization formats (such as Java HAPI or Furore FHIR .NET) which should minimise development overhead for implementers.

To ensure maximum accessibility, the Care Connect FHIR&reg; APIs will expect clients to support both formats. However since XML is on average 30% larger on the wire there is a preference towards use of JSON.

#### Why is resource versioning included as a mandatory requirement? ####

It is a key principle of the FHIR RESTful APIs that all resources are versioned; without this support no updates to data can ever be safely performed. This is explained in the “Lost Updates” section and “Transactional Integrity” sections of the FHIR standard. Whilst we recognise that it is not necessary to persist versioned access to historical records, it is important that the latest record version can be ascertained. David Hay (Product Strategist at Orion Health) has a blog post on how systems that don’t fully support versions can handle this requirement in a simple and straight forward way.

[https://fhirblog.com/2013/11/21/fhir-versioning-with-a-non-version-capable-back-end/](https://fhirblog.com/2013/11/21/fhir-versioning-with-a-non-version-capable-back-end/)

#### Will it be necessary in all cases to use an NHS service to look up staff/organisation/location information when a supplier may have their own index of this information? ####

You are welcome to use your own ODS index (i.e. to find an organisation by name/address etc.). However, you will need to perform an SDS lookup using the ODS code to resolve the FHIR endpoint that represents that ODS code for the purpose of using the Care Connect APIs.

#### Why is oAuth2 not used? ####

Authentication will be via mutual TLS/SSL authentication. The JWT web token has been proposed to allow the easy bundling of related authentication details and to eliminate the need for many separate customer headers, or a bespoke bundling formats to be defined, implemented and maintained.

#### Why are JSON Web Tokens (JWT) required? ####

Extra HTTP headers are needed for sending provenance/audit details. Sending this data in a JWT Bearer token (which is simply a fragment of JSON) is an easy way of achieving the communication of this data and various libraries exist to make authoring this content trivial.

#### Why is there to be a centrally-held list of error codes in addition to the standard HTTP response codes? ####

The list of error codes is really intended to allow consumer applications to make sense of errors that the human operator could potentially do something about. We recognise there is a cost-benefit trade-off in this space and will look to only introduce error codes (above that of the base FHIR specification) when they add sufficient value. For example a 400 - Bad Request error code in isolation doesn’t help you determine which input parameter(s) are malformed and similarly a 422 -  Unprocessable Entity doesn’t in isolation help you determine which business rule (or integrity constraint) has caused an operation to fail. 

Defining a small number of supplementary error codes to be included in the Operation Outcome entity allows sense to be made of these failing interactions.
