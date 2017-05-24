---
title: Identification | Practitioner
keywords: usecase, Practitioner
tags: [rest, fhir, identification]
sidebar: accessrecord_rest_sidebar
permalink: restfulapis_identification_practitoner.html
summary: Practitioner
---

{% include search.warnbanner.html %}
{% include profile.html content="[Care Connect Practitioner](http://www.interopen.org/candidate-profiles/care-connect/CareConnect-Practitioner-1.html)" %}

## 1. Read ##

<div markdown="span" class="alert alert-success" role="alert">
GET /Practitioner/[id]</div>
Return a single `Practitioner` for the specified id

## 2. Search Parameters ##

<div markdown="span" class="alert alert-success" role="alert">
GET /Practitioner?[searchParameters]</div>
Practitioner contains the demographics of the clinician. Fetches a bundle of all `Practitioner` resources for the specified search criteria.

{% include moscow.html content="[Practitioner](https://www.hl7.org/fhir/DSTU2/practitioner.html#search)" %}

| Name | Type | Description | SHALL | Path |
|------|------|-------------|-------|------|
| `adddress-postcode` | `string` | A postalCode specified in an address |  | Practitioner.address.postalCode |
| `identifier` | `token` | 	Any identifier for the practitioner (e.g. GMP/GMC code) |  | 	Practitioner.identifier |

<!--
| `name` | `string` | A portion of the name of the practitioner | | Practitioner.name |
| `organization` | `reference` | The identity of the organization the practitioner represents / acts on behalf of | | Practitioner.practitionerRole.managingOrganization <br>(Organization) |
-->

{% include search.string.html para="2.1." resource="Practitioner" content="address-postcode"  example="NG10%201QQ" text1="Post Code" text2="NG10 1QQ" %}

{% include search.identifier.html para="2.2." resource="Practitioner" content="identifier" subtext="SDS Id or ODS Code" example="https://fhir.nhs.uk/Id/sds-user-id|123456" text1="SDS User ID" text2="123456" %}

<div class="language-http highlighter-rouge">
<pre class="highlight"><code><span class="err">GET /Practitioner?identifier=https://fhir.nhs.uk/Id/????????|G8133438
</span></code>
Return all Practitioner resources that have a ODS Practitioner/Consultant of G8133438 </pre>
</div>

## 3. Example ##

### 3.1 Request Query ###
Return all Practitioner resources with a GP Code of G8133438, the format of the response body will be xml. Replace 'baseUrl' with the actual base Url of the FHIR Server.

#### 3.1.1. cURL ####

{% include embedcurl.html title="Search Practitioner" command="curl -X GET  'http://[baseUrl]/Practitioner?identifier=https://fhir.nhs.uk/Id/sds-user-id|G8133438&_format=xml'" %}

### 3.2 Response Headers ###

| Status Code |
|----------------|
|200 |

| Header | Value |
|-----------------|---------|
| Content-Type  | application/xml+fhir;charset=UTF-8 |

### 3.3 Response Body ###

```xml
<Bundle xmlns="http://hl7.org/fhir">
    <id value="da90d3ec-29ba-42a2-8af4-3b0f3e2b2d3d"/>
    <meta>
        <lastUpdated value="2017-05-23T10:54:09.885-04:00"/>
    </meta>
    <type value="searchset"/>
    <total value="1"/>
    <link>
        <relation value="self"/>
        <url value="http://fhirtest.uhn.ca/baseDstu2/Practitioner?identifier=https%3A%2F%2Ffhir.nhs.uk%2FId%2Fsds-user-id%7CG8133438"/>
    </link>
    <entry>
        <fullUrl value="http://fhirtest.uhn.ca/baseDstu2/Practitioner/32368"/>
        <resource>
            <Practitioner xmlns="http://hl7.org/fhir">
                <id value="32368"/>
                <meta>
                    <versionId value="1"/>
                    <lastUpdated value="2017-05-23T10:52:43.717-04:00"/>
                    <profile value="https://fhir.nhs.uk/StructureDefinition/CareConnect-Practitioner-1"/>
                </meta>
                <identifier>
                    <system value="https://fhir.nhs.uk/Id/sds-user-id"/>
                    <value value="G8133438"/>
                </identifier>
                <name>
                    <family value="Bhatia"/>
                    <given value="AA"/>
                    <prefix value="Dr."/>
                </name>
                <telecom>
                    <system value="phone"/>
                    <value value="0115 9737320"/>
                    <use value="work"/>
                </telecom>
                <address>
                    <use value="work"/>
                    <line value="Regent Street"/>
                    <line value="Long Eaton"/>
                    <city value="Nottingham"/>
                    <postalCode value="NG10 1QQ"/>
                    <country value="GBR"/>
                </address>
                <gender value="male"/>
                <practitionerRole>
                    <managingOrganization>
                        <reference value="https://sds.proxy.nhs.uk/Organization/C81010"/>
                        <display value="The Moir Medcial Centre"/>
                    </managingOrganization>
                    <role>
                        <coding>
                            <system value="https://fhir.nhs.uk/ValueSet/sds-job-role-name-1"/>
                            <code value="R0260"/>
                            <display value="General Medical Practitioner"/>
                        </coding>
                    </role>
                </practitionerRole>
                <communication>
                    <coding>
                        <system value="https://fhir.nhs.uk/ValueSet/human-language-1"/>
                        <code value="en"/>
                        <display value="English"/>
                    </coding>
                </communication>
            </Practitioner>
        </resource>
        <search>
            <mode value="match"/>
        </search>
    </entry>
</Bundle>
```
