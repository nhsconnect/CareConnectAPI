---
title: Documents | Binary
keywords: getcarerecord, structured, rest, binary
tags: [rest,fhir,documents,api,noccprofile]
sidebar: accessrecord_rest_sidebar
permalink: api_documents_binary.html
summary: A binary resource can contain any content, whether text, image, pdf, zip archive, etc.
---
{% include custom/search.warnbanner.html %}

{% include custom/fhir.reference.nonecc.html resource="Binary" resourceurl= "https://data.developer.nhs.uk/fhir/nrls-v1-draft-a/Profile.RecordLocator/nrls-documentreference-1-0.html" page="" fhirname="Binary" fhirlink="binary.html" content="User Stories" userlink="engage_michaelsstory.html" %}


## 1. Read Operation ##

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/DocumentReference/[id]</div>

{% include custom/read.response.html resource="Binary" content="" %}
