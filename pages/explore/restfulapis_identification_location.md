---
title: Identification | Location
keywords: usecase, location, order
tags: [rest, fhir, identification]
sidebar: accessrecord_rest_sidebar
permalink: restfulapis_identification_location.html
summary: Details and position information for a physical place where services are provided and resources and participants may be stored, found, contained or accommodated.
---
{% include custom/search.warnbanner.html %}

{% include custom/profile.html content="Location" page="CareConnect-Location-1" %}

{% include custom/fhir.resource.html content=" [Location](https://www.hl7.org/fhir/DSTU2/location.html)" %}

## 1. Read ##

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/Location/[id]</div>

{% include custom/read.response.html resource="Location" content="" %}

## 2. Search ##

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/Location?[searchParameters]</div>
Fetches a bundle of all `Location` resources for the specified search criteria.

{% include custom/search.header.html resource="Location" %}

### 2.1. Search Parameters ###

{% include custom/search.parameters.html resource="Location"     link="https://www.hl7.org/fhir/DSTU2/location.html#search" %}

| Name | Type | Description | Conformance  | Path |
|------|------|-------------|-------|------|
| `adddress-postcode` | `string` | A postalCode specified in an address | MAY | Location.address.postalCode |
| `identifier` | `token` | 	Any identifier for the location (e.g. SDS/ODS code) |  MAY | Location.identifier |

{% include custom/search.nopat.string.html para="2.1.1." resource="Location" content="address-postcode"  example="NG10%201RY" text1="Post Code" text2="NG10 1RY" %}

{% include custom/search.nopat.identifier.html para="2.1.2." resource="Location" content="identifier" subtext="SDS/ODS Code" example="https://fhir.nhs.uk/Id/ods-site-code|RTG08" text1="NHS Trust Site" text2="RTG08 (Long Eaton Clinic)" %}

{% include custom/search.response.html resource="Location" %}

## 3. Example ##

### 3.1 Request Query ###

Return all Location resources with a Trust Site code of RTG08, the format of the response body will be xml. Replace 'baseUrl' with the actual base Url of the FHIR Server.

#### 3.1.1. cURL ####

{% include custom/embedcurl.html title="Search Location" command="curl -H 'Accept: application/xml+fhir' -H 'Authorization: BEARER cn389ncoiwuencr' -X GET  '[baseUrl]/Location?identifier=https://fhir.nhs.uk/Id/ods-site-code|RTG08'" %}

{% include custom/search.response.headers.html resource="Location" %}

### 3.3 Response Body ###

```xml
<Bundle xmlns="http://hl7.org/fhir">
    <id value="1b7d5b72-727f-4211-bc84-ecaf1ccdb459"/>
    <meta>
        <lastUpdated value="2017-06-02T09:09:12.219+01:00"/>
    </meta>
    <type value="searchset"/>
    <total value="1"/>
    <link>
        <relation value="self"/>
        <url value="[baseUrl]/Location?identifier=RTG08"/>
    </link>
    <entry>
        <fullUrl value="[baseUrl]/Location/24959"/>
        <resource>
            <Location xmlns="http://hl7.org/fhir">
                <id value="24959"/>
                <meta>
                    <lastUpdated value="2017-06-02T09:09:10.339+01:00"/>
                    <profile value="https://fhir.hl7.org.uk/StructureDefinition/CareConnect-Location-1"/>
                </meta>
                <identifier>
                    <use value="official"/>
                    <system value="https://fhir.nhs.uk/Id/ods-site-code"/>
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
