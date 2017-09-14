---
title: Docker Image
keywords: development
tags: [development]
sidebar: overview_sidebar
permalink: ccri_docker.html
summary: "How to run a local copy of Care Connect Reference Implementation"
---


## 1. Install Docker ##

## 2. Run Docker ##

```
docker pull thorlogic/ccri
docker pull mysql
```

```
docker run --name=ccrisql --env="MYSQL_ROOT_PASSWORD=mypassword" --env="MYSQL_DATABASE=careconnect" --env="MYSQL_USER=fhirjpa" --env="MYSQL_PASSWORD=fhirjpa" -p 43306:3306 mysql
```


```
docker run --detach --name=ccri -p 80:80 -e datasource.username=fhirjpa -e datasource.password=fhirjpa -e datasource.host=//ccrisql -e datasource.driver=com.mysql.jdbc.Driver -e datasource.path=3306/careconnect -e datasource.vendor=mysql -e datasource.showSql=true -e datasource.showDdl=true -e datasource.cleardown.cron="0 19 21 * * *" -e datasource.dialect=org.hibernate.dialect.MySQL57Dialect --link ccrisql ccri
```

Config mysql

<p style="text-align:center;"><img src="images/deploy/MYSQLConfig.png" alt="Docker Config" title="Docker Config" style="width:75%"></p>
<br><br>

## 3. Putting Docker Image to DockerHub ##

For Administraton only

In the ccri-fhirserver project in the ccri github project

```
docker build -t ccri .
```

```
docker login
```

```
docker tag ccri thorlogic/ccri
```

```
docker push thorlogic/ccri
```
