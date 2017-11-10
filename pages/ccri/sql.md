---
title: Sql
keywords: deployment
tags: [deployment]
sidebar: overview_sidebar
permalink: ccri_sql.html
summary: "How to run a local copy of Care Connect Reference Implementation"
---


## 1. MySQL ##

```
SELECT @@GLOBAL.tx_isolation, @@tx_isolation;

SET GLOBAL tx_isolation='READ-UNCOMMITTED';

show variables like 'innodb_lock_wait_timeout';

SET GLOBAL innodb_lock_wait_timeout = 300;
```


## 2. SSH / Remote Connection ##

Establish a SSH connection

```
ssh -L 3307:purple.testlab.nhs.uk:43306 dev01@purple.testlab.nhs.uk
```

3307 is the port locally and 43306 is the port on the vm

Leave this connection running.

MySQL needs a user with correct permissions. To add user do (note the IP address % and localhost didn't work)

```
CREATE USER 'jeffrey'@'194.189.27.194' IDENTIFIED BY 'password';
```

```
GRANT ALL PRIVILEGES ON *.* TO 'jeffrey'@'194.189.27.194';
```

Use MySQL client as per normal but use the user just created and port is 3307 and host is 127.0.0.1 (not localhost or other)
