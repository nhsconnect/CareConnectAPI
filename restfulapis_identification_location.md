---
title: Identification | Location
keywords: usecase, location, order
tags:
- structured
- patient
sidebar: accessrecord_rest_sidebar
permalink: restfulapis_identification_location.html
summary: Clinical Location
---

## Location ##

{% include profile.html content="[Care Connect Location](http://www.interopen.org/candidate-profiles/care-connect/CareConnect-Location-1.html)" %}

## Read Operation ##

Return a single `Location` for the specified id

```http
GET /Location/:id
```

```http
GET /Location?_id=:id
```
