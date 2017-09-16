---
title: Docker Image
keywords: deployment
tags: [deployment]
sidebar: overview_sidebar
permalink: ccri_docker.html
summary: "How to run a local copy of Care Connect Reference Implementation"
---


## 1. Install Docker + Kitematic ##
Docker install of Community edition
https://docs.docker.com/engine/installation/
Create a Docker account and login to the account to use Kitematic

Kitematic install
https://kitematic.com/

## 2. Run Docker ##

Using command line pull the images:

```
docker pull thorlogic/ccri
```
```
docker pull mysql
```

Then start mysql image [Note: this exposes 43306 on the local, so mysql workbench can connect on this port]

```
docker run -detach --name=ccrisql --env="MYSQL_ROOT_PASSWORD=mypassword" --env="MYSQL_DATABASE=careconnect" --env="MYSQL_USER=fhirjpa" --env="MYSQL_PASSWORD=fhirjpa" -p 43306:3306 mysql --character-set-server=utf8 --collation-server=utf8_bin
```

Within Kitematic the image should be visible. Screen shot of settings below:

<p style="text-align:center;"><img src="images/deploy/MYSQLConfig.png" alt="Docker Config" title="Docker Config" style="width:75%"></p>
<br><br>

Now start the Care Connect Reference Implemenation

```
docker run --detach --name=ccri -p 80:80 -e datasource.username=fhirjpa -e datasource.password=fhirjpa -e datasource.host=//ccrisql -e datasource.driver=com.mysql.jdbc.Driver -e datasource.path=3306/careconnect -e datasource.vendor=mysql -e datasource.showSql=true -e datasource.showDdl=true -e datasource.cleardown.cron="0 19 21 * * *" -e datasource.dialect=org.hibernate.dialect.MySQL57Dialect --link ccrisql thorlogic/ccri
```

<p style="text-align:center;"><img src="images/deploy/CCRIConfig.png" alt="Docker Config" title="Docker Config" style="width:75%"></p>
<br><br>

Care Connect Reference Implementation should be availabe at http://127.0.0.1/careconnect-ri/






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
