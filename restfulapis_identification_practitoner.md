---
title: Identification | Practitioner
keywords: usecase, Practitioner
tags:
- structured
- patient
sidebar: accessrecord_rest_sidebar
<<<<<<< HEAD:restfulapis_identification_practitoner.md
permalink: restfulapis_identification_practitoner.html
summary: "Practioner"
=======
permalink: restfulapis_identification_practitioner.html
summary: Identification Practitioner
>>>>>>> 49ffc78622be5179f374ca91e41bf9232ec23ade:restfulapis_identification_practioner.md
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