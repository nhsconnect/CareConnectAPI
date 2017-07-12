---
title: API Codes
keywords: development
tags: [rest,fhir,api]
sidebar: overview_sidebar
permalink: explore_api_codes.html
summary: "Details of the API Codes used in the responses."
---
{% include custom/search.warnbanner.html %}

## 1. API Codes ##

### 1.1. 2xx Http Success ###

#### 200 OK ####
Successful Operation

#### 201 Created ####
The resource was created.

### 1.2. 4xx Http Client Errors ###

#### 400 Bad Request ####
Failing to send a required query parameter will result in a 400 Bad Request response.

#### 401 Unauthorized ####
Requesting the secure endpoint (non-open) without valid credentials will result in a 401 Unauthorized response.

#### 403 Forbidden ####
Requesting data from an unknown instance or an instance where the application is not authorized will result in a 403 Forbidden response.

#### 404 Not Found ####
Requesting a resource which does not exist will resule in a 404 Not Found response.

#### 406 Not Acceptable ####
Requested a media type other than JSON will result in a 406 Not Acceptable response.

#### 409 Conflict Error ####
Performing an update with an out-of-date version id will result in a 409 Conflict Error response.

#### 422 Unprocessable Entity ####
Performing an add or update with syntactically correct JSON body which is invalid according to business rules will result in a 422 Unprocessable Entity response.

### 1.3. 5xx Http Server Errors ###
