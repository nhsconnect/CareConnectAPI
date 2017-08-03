---
title: Workflow
keywords: development
tags: [design,development,workflow]
sidebar: overview_sidebar
permalink: build_pcc_workflow.html
summary: "Guidance on using FHIR with Workflow"
---

{% include custom/search.warnbanner.html %}

{% include custom/ihe.reference.html apicontent="[Order](api_diagnostics_order.html) <br> [OrderResponse](api_diagnostics_orderresponse.html) " ihecontent="" patterncontent="[Workflow (STU3)](https://www.hl7.org/fhir/workflow-module.html)" %}

## 1. Overview ##

{% include custom/usecase.html content="[University Hospital Southampton](engage_poc_uhscc.html)" %}

TODO

## 2. Task Create ##

TODO

```
POST [baseUrl]/Order
```

## 3. Task Amendment ##

TODO

```
PUT [baseUrl]/Order
```

## 4. Task Completed ##

TODO

```
POST [baseUrl]/OrderResponse
```

<script src="https://gist.github.com/KevinMayfield/5ce742eb62ab167657320d0579cfd127.js"></script>

## 5. FHIR STU3 Task ##
