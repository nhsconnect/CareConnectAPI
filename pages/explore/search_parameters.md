---
title: Search Parameters
keywords: foundations
tags: [fhir,rest]
sidebar: foundations_sidebar
permalink: search_parameters.html
summary: "Describes the process of creating the search parameters"
---

{% include custom/search.warnbanner.html %}

## 1. How they were created? ##

The search parameters have been created by amalgamating the thinking and search parameter definitions from public facing projects who have spent time looking, investigating and implementing API search parameters:


- [US Argonaut Data Query Implementation Guide](http://www.fhir.org/guides/argonaut/r2/Conformance-server.html)
- [GP Connect](https://nhsconnect.github.io/gpconnect/accessrecord_rest.html)
- [Cerner](http://fhir.cerner.com/millennium/dstu2/)
- [AllScripts](https://developer.allscripts.com/)
- [EPIC](https://open.epic.com/Interface/FHIR)
- NHS Scotland
- [NHS Digital - GP Connect](https://nhsconnect.github.io/gpconnect/accessrecord_rest.html)

The search parameters were created as a starting point for discussion as such a process to improve the search parameters and make them applicable and complete.

## 2. MAY Parameters ##

The parameters have been selected using a scoring system based usage frequency. Parameters with a high score have been given SHALL conformance status and the others a SHOULD. A number of low scoring parameters have been included with a MAY status, this is to cover differences between UK and international usage.

E.g. [Practitioner](restfulapis_identification_practitoner.html) has a MAY conformance status for `identifier`, in the UK have a national codeSystems for Consultants and GP's it is anticipated we would want to query Practitioner using these codes. If feedback from suppliers and consumers indicates this is the case then the conformance for `identifier` would be increased to SHALL or SHOULD. <br>

The same logic will be applied to other parameters such as `adddress-postcode`, however if feedback indicates the conformance shouldn't be a SHALL or a SHOULD then this parameter will be classed in the same way as the other optional (MAY) FHIR parameters and the explicit entry will be removed from this implementation guide.

No MAY parameters will be listed in the final version of this Implementation Guide.

## 3. Improvement process ##

An improvement process needs to be developed to improve the search parameters and validate the ones already suggested. Please contact the careconnect team if you have any suggestions.

{% include note.html content="Provided as a suggestion" %}
