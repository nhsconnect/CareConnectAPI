---
title: Clinical | Medication
keywords: usecase, medication
tags:
- restful_api
- clinical
- profile
sidebar: foundations_sidebar
permalink: restfulapis_clinical_medication.html
summary: Clinical Medication
---

## Medication ##

{% include profile.html content="[Care Connect Medication](http://www.interopen.org/candidate-profiles/care-connect/CareConnect-Medication-1.html)" %}

## Read Operation ##

Return a single `Medication` for the specified id

```http
GET /Medication/:id
```

```http
GET /Medication?_id=:id
```


