---
title: Identification | Organisation
keywords: usecase, Organization
tags:
- structured
- patient
sidebar: accessrecord_rest_sidebar
permalink: restfulapis_identification_organisation.html
summary: Identification Organization
---

## Organization ##

{% include profile.html content="[Care Connect Organization](http://www.interopen.org/candidate-profiles/care-connect/CareConnect-Organization-1.html)" %}

## Read Operation ##

Return a single `Organization` for the specified id

```http
GET /Organization/:id
```

```http
GET /Organization?_id=:id
```

