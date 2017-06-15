---
title: Workflow | OrderResponse
keywords: usecase, orderresponse
tags: [rest, fhir, workflow,development]
sidebar: foundations_sidebar
permalink: restfulapis_workflow_orderresponse.html
summary: A response to an order.
---

{% include custom/search.warnbanner.html %}

## 0. Reference ##

{% include custom/fhir.resource.html content="[OrderResponse](https://hl7.org/fhir/DSTU2/orderresponse.html)" %}

## 1. Create ##

<div markdown="span" class="alert alert-success" role="alert">
POST [baseUrl]/OrderResponse</div>

Returns either the created `OrderResponse` or an `OperationOutcome` resource.

## 2. Update ##

<div markdown="span" class="alert alert-success" role="alert">
PUT [baseUrl]/OrderResponse/[id]</div>

Updates the specified `OrderResponse`
