---
title: Security
keywords: design, build, access, security
tags: [design]
sidebar: foundations_sidebar
permalink: design_security.html
summary: "The security page shows how to establish initial security credentials (where necessary) with the API provided"
---

{% include important.html content="The API security described in this section is not meant to be complete but a starting point to understand some design considerations to consider when implementing APIs." %}

# What is API Security? #
API Security often encapsulates authentication and encryption. However, various concepts requiring diverse expertise and approaches need to be considered especially concerning testing and quality:

- Authentication: reliably identify end user
- Authorisation: identified user access to correct resources/data 
- Encryption: hide information from unauthorized access
- Signatures: ensure information integrity

Two common ways of accessing and managing API use within API security based on the need to balance access to APIs with the permissions to access the API include:

- Federation: reusing Credentials & Spreading Resources
- Delegation: access and rights can be given to authorized users


## Authentication and Authorisation ###

Authentication and authorisation are commonly used together:

- Authentication: reliably identify end user
- Authorisation: identified user access to correct resources/data 

Authentication is most often implemented with a username and password. To increase the security this can be suplemented by adding 

- software certificates, 
- hardware keys and 
- external devices. 

Authorisation occurs once the user is authenticated, the system decides which resources or data to allow access to. For APIs this is often some kind of access token, either obtained through an external process (e.g. when signing up for the API) or through a separate mechanism (e.g. OAuth). This token is then passed with each request to an API and is validated by the API before processing the request. 


## Encryption and Signatures ##

A brief description of encryption and signatures is shown below:

- Encryption secures information from those not authorized to view that information, often with SSL used to encrypt the HTTP messages between API clients. SSL only applies to the transport layer and therefore the data at rest also needs protection. 
- Signatures are used to ensure that API requests or response have not been tampered with in transit. The message itself might be unencrypted, but must be protected against modification and arrive intact.

Encryption and Signatures are used together i.e.:

- The signature could be encrypted to only allow certain parties to validate if a signature is valid, or 
- The encrypted data could be signed to further ensure that data is neither seen or modified by unwanted parties.


# Security and Care Connect APIs #

Security is a key consideration when establishing API projects and should be considered within the design from the start of any project. The four key principles to consider are:

- Authentication
- Authorisation
- Encryption
- Signatures

As an API project gets closer to live please ensure you have thought through the implications of the design decisions while setting up the API between systems and over the provided network/channel of communication. Please see the sections [Test](/test.html), [Assure](/assure.html), [Deploy](/deploy.html) for further descriptions of security considerations at each phase.

For more information on the wider design decisions involved in providing safe access to information please see: 

- [Safe, legal and secure](https://developer.nhs.uk/library/save-legal-secure/) guide from developer.nhs.uk provides an overview of some design decisions and considerations to consider when implementing APIs. 
- [Case Studies](/engage_case_studies.html) illustrates design and security decisions used to solve the challenges faced within the context and design pattern encountered.


## Reference Implementation - Security Example ##

The Care Connect Reference Implementation (CCRI) provides an example API security mechanism using OAuth2. The CCRI has been designed as an example to show Access and Security for a Care Connect API implementation. The CCRI is <b>not</b> intended to be an offical version to follow all of the methods and principles, however, it can be used as an example of the architectural pieces required to deploy a functional Care Connect API. Each element has been described at a high level within the [Care Connect Reference Implementation Guide](/build_ri_overview.html). Also to aid developers quickly test the main components have been placed in containers (Docker instances using Docker Compose) to allow for minimal configuration. 

The design of the Care Connect Reference Implementation shows how to manage and maintain valid and consistant APIs through automated testing, example data and continuous integration and deployment. The design CCRI has taken the Access considerations above to provide accessible API and resilient example API.

{% include note.html content="See how the [Care Connect Reference Implementation](/build_ri_security.html) provides Security OAuth2 based examples for Authentication, Authorisation, Encryption and Signatures"%}

{% include custom/contribute.html content="Provide design patterns and API usage case studies by getting in touch with careconnect@interopen.org "%}

# API Considerations #

Other API consideration are shown below. Please click on the parts of the API process to continue your API creation journey.

{% include custom/provide_api.svg %}

{% include custom/contribute.html content="Get in involved and contribute to the above API considerations "%}
