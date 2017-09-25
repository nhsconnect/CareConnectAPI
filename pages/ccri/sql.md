---
title: Sql
keywords: deployment
tags: [deployment]
sidebar: overview_sidebar
permalink: ccri_docker.html
summary: "How to run a local copy of Care Connect Reference Implementation"
---


## 1. MySQL ##

```
SELECT @@GLOBAL.tx_isolation, @@tx_isolation;

SET GLOBAL tx_isolation='READ-UNCOMMITTED';

show variables like 'innodb_lock_wait_timeout';

SET GLOBAL innodb_lock_wait_timeout = 300;
```
