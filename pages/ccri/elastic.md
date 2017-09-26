---
title: Elastic
keywords: deployment
tags: [deployment]
sidebar: overview_sidebar
permalink: ccri_elastic.html
summary: "How to run a local copy of Care Connect Reference Implementation"
---


## 1. Overview ##

We use elasticsearch (NoSQL index), kibana (dashboards), filebeats (reading log files for elastic search). See https://www.elastic.co/products/

Followed intructions from https://www.elastic.co/guide/en/beats/libbeat/5.6/getting-started.html

=Versions=

elasticsearch 5.6.1
kibana 5.6.1
filebeat 5.6.1
logstash 5.6.1

## 2. elasticsearch ##

Start command

```
.\elasticsearch
```

## 3. logstash

Start command

```
./bin/logstash -f logstash.conf
```

The logstash.conf needs to be created (this is copied from the beats install instructions)

```
input {
  beats {
    port => 5044
  }
}

# The filter part of this file is commented out to indicate that it is
# optional.
# filter {
#
# }

output {
  elasticsearch {
    hosts => "localhost:9200"
    manage_template => false
    index => "%{[@metadata][beat]}-%{+YYYY.MM.dd}"
    document_type => "%{[@metadata][type]}"
  }
}
```


No config changes at present

## 4. kibana ##

Start command

```
.\kibana
```

In kibana.yml
```
elasticsearch.url: "http://localhost:9200"
```

## 5. filebeat ##

Start commmand

```
sudo ./filebeat -e -c filebeat.yml
```

In filebeat.yml

```
paths:
    - /Library/Tomcat/logs/catlina*.*
```
