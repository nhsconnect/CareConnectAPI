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


{% include custom/contribute.html content="Provide design patterns and API usage case studies by getting in touch with careconnect@interopen.org "%}

# API Considerations #

Other API consideration are shown below. Please click on the parts of the API process to continue your API creation journey.

{% include custom/provide_api.svg %}

{% include custom/contribute.html content="Get in involved and contribute to the above API considerations careconnect@interopen.org"%}
