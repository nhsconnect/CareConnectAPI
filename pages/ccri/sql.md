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

## 2. Export data files ##

Export using (note use of the folder specified by secure-file priv setting)

```
select * into outfile '/mysql_exp/tempDescription.txt' from careconnect.tempDescription
```

Copy files from local machine to development box:

```
scp tempDescription.txt dev01@purple.testlab.nhs.uk:~/
```

Move from server to docker container. The folder is defined in the @@secure-privs variable in mysql.

```
docker cp tempDescription.txt ccrisql:/var/lib/mysql-files/tempDescription.txt
```

Import using this to log into mysql

```
mysql -uroot -pmypassword -h127.0.0.1 --port=43306 careconnect
```

then

```
LOAD DATA local INFILE 'tempDescription.txt' into table tempDescription;
```

GRANT FILE ON *.* to 'fhirjpa'@'%';
