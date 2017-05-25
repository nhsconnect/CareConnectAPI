---
title: Clinical | Medication
keywords: usecase, medication
tags: [fhir, rest, clinical, medication]
sidebar: foundations_sidebar
permalink: restfulapis_clinical_medication.html
summary: This resource is primarily used for the identification and definition of a medication. It covers the ingredients and the packaging for a medication.
---
{% include custom/search.warnbanner.html %}
{% include custom/profile.html content="[Care Connect Medication](http://www.interopen.org/candidate-profiles/care-connect/CareConnect-Medication-1.html)" %}

## Read ##

<div markdown="span" class="alert alert-success" role="alert">
GET /Medication/[id]</div>

Return a single `Medication` for the specified id.
