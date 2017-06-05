---
title: Clinical | Family Member History
keywords: usecase, familymemberhistory
tags: [familymemberhistory,fhir,rest,clinical]
sidebar: foundations_sidebar
permalink: restfulapis_clinical_familymemberhistory.html
summary: Significant health events and conditions for a person related to the patient relevant in the context of care for the patient.
---
{% include custom/search.warnbanner.html %}

{% include custom/profile.html content="Family Member History" page="CareConnect-FamilyMemberHistory-1" %}

{% include custom/fhir.resource.html content="[FamilyMemberHistory](https://www.hl7.org/fhir/DSTU2/familymemberhistory.html#search)" %}

## Read ##

<div markdown="span" class="alert alert-success" role="alert">
GET /FamilyMemberHistory/[id]</div>

Return a single `FamilyMemberHistory` for the specified id

## Search Parameters ##

<div markdown="span" class="alert alert-success" role="alert">
GET /FamilyMemberHistory?[searchParameters]</div>

FamilyMemberHistory resource contains family member history for a patient. Fetches a bundle of all `FamilyMemberHistory` resources for the specified patient.

{% include custom/moscow.html content="[FamilyMemberHistory](https://www.hl7.org/fhir/DSTU2/familymemberhistory.html#search)" %}

| Name | Type | Description | Conformance | Path |
|------|------|-------------|-------|------|
| `date` | `date` | Obtained date/time. If the obtained element is a period, a date that falls in the period | Y | FamilyMemberHistory.date |
| `gender` | `token` | A search by a gender code of a family member |  | FamilyMemberHistory.gender |
| `patient` | `reference` | The identity of a subject to list family member history items for | Y | FamilyMemberHistory.patient<br>(Patient) |

{% include custom/search.date.html content="FamilyMemberHistory" %}

{% include custom/search.patient.html content="FamilyMemberHistory" %}
