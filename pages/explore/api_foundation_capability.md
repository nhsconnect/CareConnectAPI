---
title: Foundation | Capability Statement
keywords: foundations, fhir
tags: [rest,fhir,use_case,api,foundation,noccprofile]
sidebar: accessrecord_rest_sidebar
permalink: api_foundation_capability.html
summary: A capability statement is a set of capabilities of a FHIR Server that may be used as a statement of actual server functionality or a statement of required or desired server implementation.
---

{% include custom/search.warnbanner.html %}

{% include custom/fhir.reference.html resource="" page="" fhirname="Capability Statement"  fhirlink="capabilitystatement.html" content="-" userlink="-" %}


## 1. Read ##

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/metadata</div>

The /metadata path on the root of the FHIR server will return the Capability statement for the FHIR server:

Alternatively, a HTTP OPTIONS request against the root of the FHIR server will also return the capability profile:

<div markdown="span" class="alert alert-success" role="alert">
OPTIONS [baseUrl]/</div>

For details of this interaction - see the [HL7 FHIR STU3 RESTful API](http.html#capabilities){:target="_blank"}

All requests SHALL contain a valid ‘Authorization’ header and SHALL contain an ‘Accept’ header with at least one of the following application/json+fhir or application/xml+fhir.

## 2. Example ##

### 2.1 Request Query ###

Retrieve the Capability statement from the FHIR Server, the format of the response body will be xml. Replace 'baseUrl' with the actual base Url of the FHIR Server.

#### 2.1.1. cURL ####

{% include custom/embedcurl.html title="Search Patient" command="curl -X GET -H 'Accept: application/xml+fhir' -H 'Authorization: BEARER [token]' -v 'http://yellow.testlab.nhs.uk/careconnect/STU3/metadata?'" %}

### 2.2 Response Body ###

{% include important.html content="The following capability statement is provided by the Reference Implementation" %}

<div class="language-http highlighter-rouge">
<pre class="highlight">
<h4>Reference Implementation</h4>
XML <a target="_blank" href="http://yellow.testlab.nhs.uk/careconnect/conformance?serverId=home&pretty=false&encoding=xml">Capability Statement RI viewer</a>
JSON <a target="_blank" href="http://yellow.testlab.nhs.uk/careconnect/conformance?serverId=home&pretty=false&encoding=json">Capability Statement RI viewer</a>
</pre>
</div>

{% include important.html content="The following draft conformance statement will move as the implementation guide moves on." %}


### 2.3 C# ###

{% include tip.html content="C# code snippets utilise Ewout Kramer's [fhir-net-api](https://github.com/ewoutkramer/fhir-net-api) library which is the official .NET API for HL7&reg; FHIR&reg;." %}

```csharp
var client = new FhirClient("http://[fhir_base]/");
client.PreferredFormat = ResourceFormat.Json;
var resource = client.Conformance();
FhirSerializer.SerializeResourceToXml(resource).Dump();
```
