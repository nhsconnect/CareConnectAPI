---
title: Security
keywords: test, pattern, security
tags: [test, security]
sidebar: foundations_sidebar
permalink: test_security.html
summary: "The security page shows how to establish initial security credentials (where necessary) with the API provided"
---

{% include important.html content="The API security described in this section is not meant to be complete but a starting point to understand some design considerations to consider when implementing APIs." %}

# Security within Test #

Security starts to be a key element of the design and process for testing at this point. The following four key principles should be considered:

- Authentication
- Authorisation
- Encryption
- Signatures

# Security examples #

The following non-exhaustive list describes common security patterns and links to example cases where they are used:

- Basic Auth
- OAuth2
- Certifications/SSL
- JWT - GP Connect
- OpenId
- NHS Verify (UK only)
- Citizen Id (UK only)
- SmartCards (UK only)

Depending on the chosen end usage, channel and network will influence the chosen security choice.


# API Considerations #

Other API consideration are shown below. Please click on the parts of the API process to continue your API creation journey.

{% include custom/provide_api.svg %}

{% include custom/contribute.html content="Get in involved and contribute to the above API considerations careconnect@interopen.org"%}
