---
title: Identification | Location
keywords: usecase, location, order
tags: [rest, fhir, identification]
sidebar: accessrecord_rest_sidebar
permalink: restfulapis_identification_location.html
summary: Identification Location
---
{% include search.warnbanner.html %}
{% include profile.html content="[Care Connect Location](http://www.interopen.org/candidate-profiles/care-connect/CareConnect-Location-1.html)" %}

## 1. Read ##

<div markdown="span" class="alert alert-success" role="alert">
GET /Location/[id]</div>
Return a single `Location` for the specified id

## 2. Search Parameters ##

<div markdown="span" class="alert alert-success" role="alert">
GET /Location?[searchParameters]</div>
Location contains the details for the location. Fetches a bundle of all `Location` resources for the specified search criteria.

{% include moscow.html content=" [Location](https://www.hl7.org/fhir/DSTU2/location.html#search)" %}

| Name | Type | Description | SHALL | Path |
|------|------|-------------|-------|------|
| `adddress-postcode` | `string` | A postalCode specified in an address | Y | Location.address.postalCode |
| `identifier` | `token` | 	Any identifier for the location (e.g. SDS/ODS code) | Y | 	Location.identifier |
| `name` | `string` | A portion of the name of the location | | Location.name |


{% include search.string.html para="2.1." resource="Location" content="address-postcode"  example="NG10%201RY" text1="Post Code" text2="NG10 1RY" %}

{% include search.identifier.html para="2.2." resource="Location" content="identifier" subtext="SDS/ODS Code" example="https://fhir.nhs.uk/Id/????|RTG08" text1="NHS Trust Site" text2="RTG08 (Long Eaton Clinic)" %}

### 3.1 Query ###
Return all Location resources with a Trust Site code of RTG08, the format of the response body will be xml. Replace 'baseUrl' with the actual base Url of the FHIR Server.

```curl
curl --get http://[baseUrl]/Location?identifier=http://fhir.nhs.net/Id/ods-site-code|RTG08&_format=xml
```

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
    <id value="cf053adf-8b96-483c-8864-808b87c5610f"/>
    <meta>
        <lastUpdated value="2017-05-23T11:28:41.165-04:00"/>
    </meta>
    <type value="searchset"/>
    <total value="1"/>
    <link>
        <relation value="self"/>
        <url value="http://fhirtest.uhn.ca/baseDstu2/Location?identifier=http%3A%2F%2Ffhir.nhs.net%2FId%2Fods-site-code%7CRTG08"/>
    </link>
    <entry>
        <fullUrl value="http://fhirtest.uhn.ca/baseDstu2/Location/32370"/>
        <resource>
            <Location xmlns="http://hl7.org/fhir">
                <id value="32370"/>
                <meta>
                    <versionId value="1"/>
                    <lastUpdated value="2017-05-23T11:27:01.266-04:00"/>
                    <profile value="https://fhir.nhs.uk/StructureDefinition/CareConnect-Location-1"/>
                </meta>
                <identifier>
                    <use value="official"/>
                    <system value="http://fhir.nhs.net/Id/ods-site-code"/>
                    <value value="RTG08"/>
                </identifier>
                <name value="Long Eaton Clinic"/>
                <type>
                    <coding>
                        <system value="http://hl7.org/fhir/ValueSet/v3-ServiceDeliveryLocationRoleType"/>
                        <code value="CSC"/>
                        <display value="Community Service Centre"/>
                    </coding>
                </type>
                <telecom>
                    <system value="phone"/>
                    <value value="0115 855 4034"/>
                    <use value="work"/>
                </telecom>
                <telecom>
                    <system value="fax"/>
                    <value value="0532 123 4567"/>
                    <use value="work"/>
                </telecom>
                <address>
                    <use value="work"/>
                    <line value="Midland Street"/>
                    <line value="Long Eaton"/>
                    <city value="Nottingham"/>
                    <postalCode value="NG10 1RY"/>
                    <country value="GBR"/>
                </address>
                <physicalType>
                    <coding>
                        <system value="http://snomed.info/sct"/>
                        <code value="310390009"/>
                        <display value="Hospital clinic"/>
                    </coding>
                </physicalType>
                <managingOrganization>
                    <reference value="https://sds.proxy.nhs.uk/Organization/Organization/RTG"/>
                    <display value="Derby Teaching Hospitals NHS Foundation Trust"/>
                </managingOrganization>
            </Location>
        </resource>
        <search>
            <mode value="match"/>
        </search>
    </entry>
</Bundle>
```
