---
title: Information Sharing Patterns
keywords: design, build, access, security, pattern, topology
tags: [design,toplogy]
sidebar: foundations_sidebar
permalink: design_patterns.html
summary: "Information Sharing Patterns (Topologies) demonstrate and describe how various design patterns can influence access, security and use of APIs"
---

{% include important.html content="All phases outlined below are indicative and subject to on-going review." %}

# Patterns #

This section has been included to emphasise the importance of understanding the associated Information Sharing Pattern when deciding how to use Care Connect APIs within solutions. The information has been taken from [developer.nhs.uk](https://developer.nhs.uk/library/architecture/integration-patterns/information-sharing-patterns-summary/).

## Overview ##

A “pattern” is a formal way of documenting a solution to a design problem in a particular field of expertise for example in the case of an API sharing clinical information between systems. The information in this section has been reproduced and shortened from [developer.nhs.uk](https://developer.nhs.uk/library/architecture/integration-patterns/information-sharing-patterns-summary/)
- Patterns are not mutually exclusive: many real solutions will use more than one pattern.
- Solutions may evolve from simpler to more complex patterns over time.
- Some patterns will be better for specific sharing needs than others – there is no “one size fits all”.
- Some patterns will scale better to larger populations.
- Some patterns require additional capabilities or services to be in place.

## List of patterns ##

Below is a list of the more commonly used patterns that can be supported by one or more of FHIR's defined exchange paradigms. If you require more detail please go to [developer.nhs.uk](https://developer.nhs.uk/library/architecture/integration-patterns/information-sharing-patterns-summary/) and click on the pattern for more information.

- Single Shared Application
- Portal
- Click Through
- Store and Notify
- Broadcast (Point to Point Sharing)
- Shared Repository
- Message Broker
- Registry Repository
- Publish Subscribe

# Patterns and Care Connect APIs #

The Care Connect standard doesn't mandate a specific exchange paradigm so this will need to be decided upon when a Care Connect API is designed. The Information Sharing Pattern may have an influence how Care Connect APIs can be used and work within a solution. This implementation guide also offers [Case Studies](/engage_case_studies.html) to expose and demonstrate how Care Connect APIs can or have been used to interoperate with other systems, patterns, and level of digital maturity within and between organisations.

{% include note.html content="The [Care Connect Reference Implementation](/build_ri_overview.html) can be used for all of the exchange patterns listed above. Further configuration and extension would be necessary broadcast, message broker, registry repository and publish subscribe models. Please see the process and components described in the RESTful API Care Connect Reference Implementation and try using it for yourself."%}


{% include custom/contribute.html content="Provide design patterns and API usage case studies by getting in touch with careconnect@interopen.org "%}

# API Considerations #

Other API consideration are shown below. Please click on the parts of the API process to continue your API creation journey.

<div style="text-align:center">{% include custom/provide_api.svg %}

{% include custom/contribute.html content="Get in involved and contribute to the above API considerations "%}</div>
