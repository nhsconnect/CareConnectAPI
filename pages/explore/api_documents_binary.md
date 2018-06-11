---
title: Documents | Binary
keywords: getcarerecord, structured, rest, binary
tags: [rest,fhir,documents,api,noccprofile]
sidebar: accessrecord_rest_sidebar
permalink: api_documents_binary.html
summary: A binary resource can contain any content, whether text, image, pdf, zip archive, etc.
---
{% include custom/search.warnbanner.html %}

{% include custom/fhir.referencemin.html resource="Binary" page="" fhirname="Binary" fhirlink="binary.html" content="" userlink="" %}


## 1. Read Operation ##

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/Binary/[id]</div>

{% include custom/read.response.html resource="Binary" content="" %}
