---
title: Identification | Practitioner
keywords: usecase, Practitioner
tags:
- structured
- patient
sidebar: accessrecord_rest_sidebar
permalink: restfulapis_identification_practitioner.html
summary: Identification Practitioner
---


## Practitioner ##

{% include profile.html content="[Care Connect Practitioner](http://www.interopen.org/candidate-profiles/care-connect/CareConnect-Practitioner-1.html)" %}

## Read Operation ##

Return a single `Practitioner` for the specified id

```http
GET /Practitioner/:id
```

```http
GET /Practitioner?_id=:id
```