---
title: Identification | Practitioner
keywords: usecase, Practitioner
tags: [rest, fhir, identification]
sidebar: accessrecord_rest_sidebar
permalink: restfulapis_identification_practitoner.html
summary: A person who is directly or indirectly involved in the provisioning of healthcare.
---

{% include custom/search.warnbanner.html %}

{% include custom/profile.html content="Practitioner" page="CareConnect-Practitioner-1" %}

{% include custom/fhir.resource.html content="[Practitioner](https://www.hl7.org/fhir/DSTU2/practitioner.html)" %}


## 1. Read ##

<div markdown="span" class="alert alert-success" role="alert">
GET /Practitioner/[id]</div>

{% include custom/read.response.html resource="Practitioner" content="" %}

## 2. Search ##

<div markdown="span" class="alert alert-success" role="alert">
GET /Practitioner?[searchParameters]</div>
Fetches a bundle of all `Practitioner` resources for the specified search criteria.

{% include custom/search.header.html resource="Practitioner" %}

### 2.1. Search Parameters ###

{% include custom/search.parameters.html resource="Practitioner"     link="https://www.hl7.org/fhir/DSTU2/practitioner.html#search" %}

| Name | Type | Description | Conformance  | Path |
|------|------|-------------|-------|------|
| `adddress-postcode` | `string` | A postalCode specified in an address | MAY | Practitioner.address.postalCode |
| `identifier` | `token` | 	Any identifier for the practitioner (e.g. GMP/GMC code) | MAY | 	Practitioner.identifier |

<!--
| `name` | `string` | A portion of the name of the practitioner | | Practitioner.name |
| `organization` | `reference` | The identity of the organization the practitioner represents / acts on behalf of | | Practitioner.practitionerRole.managingOrganization <br>(Organization) |
-->

{% include custom/search.nopat.string.html para="2.1.1." resource="Practitioner" content="address-postcode"  example="NG10%201QQ" text1="Post Code" text2="NG10 1QQ" %}

{% include custom/search.nopat.identifier.html para="2.1.2." resource="Practitioner" content="identifier" subtext="SDS Id or ODS Code" example="https://fhir.nhs.uk/Id/sds-user-id|123456" text1="SDS User ID" text2="123456" %}

<div class="language-http highlighter-rouge">
<pre class="highlight"><code><span class="err">GET /Practitioner?identifier=https://fhir.nhs.uk/Id/????????|G8133438
</span></code>
Return all Practitioner resources that have a ODS Practitioner/Consultant of G8133438 </pre>
</div>

{% include custom/search.response.html resource="Practitioner" %}

## 3. Example ##

### 3.1 Request Query ###
Return all Practitioner resources with a GP Code of G8133438, the format of the response body will be xml. Replace 'baseUrl' with the actual base Url of the FHIR Server.

#### 3.1.1. cURL ####

{% include custom/embedcurl.html title="Search Practitioner" command="curl -X GET  'http://[baseUrl]/Practitioner?identifier=https://fhir.nhs.uk/Id/sds-user-id|G8133438&_format=xml'" %}

{% include custom/search.response.headers.html resource="Practitioner" %}

### 3.3 Response Body ###

```xml
<Bundle xmlns="http://hl7.org/fhir">
    <id value="4b552491-8e39-43da-8967-a2210536cd81"/>
    <meta>
        <lastUpdated value="2017-06-02T09:35:18.459+01:00"/>
    </meta>
    <type value="searchset"/>
    <total value="1"/>
    <link>
        <relation value="self"/>
        <url value="http://127.0.0.1:8181/Dstu2/Practitioner?identifier=G8133438"/>
    </link>
    <entry>
        <fullUrl value="http://127.0.0.1:8181/Dstu2/Practitioner/24967"/>
        <resource>
            <Practitioner xmlns="http://hl7.org/fhir">
                <id value="24967"/>
                <meta>
                    <versionId value="1"/>
                    <lastUpdated value="2017-06-02T09:33:47.072+01:00"/>
                    <profile value="https://fhir.hl7.org.uk/StructureDefinition/CareConnect-Practitioner-1"/>
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
                            <system value="https://fhir.hl7.org.uk/ValueSet/sds-job-role-name-1"/>
                            <code value="R0260"/>
                            <display value="General Medical Practitioner"/>
                        </coding>
                    </role>
                </practitionerRole>
            </Practitioner>
        </resource>
        <search>
            <mode value="match"/>
        </search>
    </entry>
</Bundle>
```
