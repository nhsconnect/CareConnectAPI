---
title: Release Notes
keywords: development, versioning
tags: [development]
sidebar: overview_sidebar
permalink: overview_release_notes.html
summary: Summary release notes of the versions released in Care Connect API Implementation Guide
---

{% include important.html content="This site is under active development by NHS Digital on behalf of INTEROPen and is intended to provide all the technical resources you need to successfully develop the Care Connect APIs. This project is being developed using an agile methodology so iterative updates to content will be added on a regular basis." %}

## 0.6.0-alpha.0 ##

Added
  - Initial sections of University Hospital Southampton POC included
  - Added section on how [search parameters](search_parameters.html) were selected
  - Added core CareConnectAPI [prerequisites](explore.html)

Updated
  - Updates to Bristol Connecting Care POC (user stories)
  - Corrections to the glossary
  - Corrected broken links in the engagement approach
  - Removed national NHS Number guidance
  - Altered Accept http header notes
  - Moved xml and code examples to gitHub gist
  - Converted markdown to html tables for better display of parameters

## 0.5.0-alpha.0 ##

Added
- Community and FHIR Tools sections to Help & Support sections
- Diagram to support the engagement process
- Foundation API definitions
- Profile links to HL7 UK FHIR Reference Server (test version)

Updated
- Communication Channels (Help & Support) revised to reference the Care Connect Inbox and the INTEROpen website.
- Clinical API definitions
- Individuals and Entities API definitions
- Workflow API definitions
- All Explore section pages to similar layout
- Communication Channels (Help & Support) revised to reference the Care Connect Inbox and the INTEROpen website
- Corrected some styling issues
- Design & Build section template added as a process
- Test section example added of end to end process
- Assure section added to provide overview of end to end process
- Deploy section added to provide overview of end to end process
- Major changes to underlying folder structure to support use and updating of information
- Conformance profile updates to current alpha state
- Glossary
- Provide APIs with a clickable diagram used throughout later stages
- Linking to developer.nhs.uk
- Engagement approach with look and feel and linking


## 0.4.0-alpha.0 ##

Added
- Description of providing an API process
- Standard definition of a API definition
- Started Test explanation section
- Engagement Process
- Bristol Connecting Care Case Study

Defined Patient definition adding :
- References section - starting to link to user stories
- HTTP headers
- Response codes - Also added a non exhaustive API Codes page to describe all of the codes
- Search parameters - added section to include guidance on how a search can happen in practice localised on the NHS

Multiple updates to glossary

Restructured 'Engage' navigation to rationalise content showing the engagement process and case studies. Pages explaining what user stories are and how we use them have been moved off the sidebar to be accessed within the pages as necessary.

## 0.3.0-alpha.0 ##

Examples resources conforming to the CareConnect Profiles

Mandatory and optional API Parameters defined for the following resources
  - Clinical    
   - AllergyIntollerance
    - Condition
    - Immunization
    - Medication
    - MediationOrder
    - MedicationStatement
    - Observation
- Identification
    - Location
    - Organization
    - Patient
    - Practitioner
- Workflow
    - Encounter
(please comment via https://interopen.ryver.com or email careconnect@interopen.org)

Engage
- Added Overview explanation
- Added Michael's Stories showing the example user stories
- Linked Michael's Stories to APIs currently available and defined above
