---
title: Search Parameters
keywords: foundations
tags: [fhir,rest]
sidebar: foundations_sidebar
permalink: explore_search_parameters.html
summary: "Describes the process of creating the search parameters"
---

{% include custom/search.warnbanner.html %}

## 1. How they were created? ##

The search parameters have been created by amalgamating the thinking behind search parameter definitions from public facing projects who have spent time looking, investigating and implementing API search parameters:


- [NHS Digital - GP Connect](https://nhsconnect.github.io/gpconnect/accessrecord_rest.html)
- [US Argonaut Data Query Implementation Guide](http://www.fhir.org/guides/argonaut/r2/Conformance-server.html)
  - [Cerner](http://fhir.cerner.com/millennium/dstu2/)
  - [AllScripts](https://developer.allscripts.com/)
  - [EPIC](https://open.epic.com/Interface/FHIR)
- NHS Scotland Clinical Portal (API) and [SCI Store](http://www.sci.scot.nhs.uk/products/store/store_main.htm)

The search parameters were created as a starting point for discussion as such a process to improve the search parameters and make them applicable and complete.

## 2. MAY Parameters ##

The parameters have been selected on usage frequency. Frequently used parameters have been given SHALL conformance requirement and slightly less common parameters a SHOULD requirement. A number of search parameters fell outside of this criteria were identified as being useful in   in the U.K., these are listed in the `2.2 Search` section with a MAY conformance requirement.

<div markdown="span" class="alert alert-info" role="alert"><i class="fa fa-info-circle"></i> <b><a href="https://digital.nhs.uk/organisation-data-service">Organization Data Service</a></b> is responsible for <a href="api_entity_organisation.html">Organisation</a>, <a href="api_entity_location.html">Location</a> (Organisation Site) and <a href="api_entity_practitoner.html">Practitioner</a> codes used within the NHS. The requirement to search for these using  `identifier` is anticipated, `identifier` is listed in the search parameters section of these resources with a MAY conformance requirement. </div>

It is believed this MAY conformance is not enough in a U.K. setting and this should be increased to SHALL or SHOULD. MAY parameters are no different to other optional standard FHIR search parameters. If feedback indicates they should remain optional (MAY), they will be treated as such and the references removed from the `2.2 Search` section of the resources.

Feedback is requested from suppliers and consumers to confirm the conformance level for all parameters in the section `2.2 Search` for all resources.


## 3. Improvement process ##

An improvement process needs to be developed to improve the search parameters and validate the ones already suggested. Please contact the careconnect team if you have any suggestions.

{% include custom/contribute.html content="Get in touch with careconnect@interopen.org to improve the Search Parameters" %}
