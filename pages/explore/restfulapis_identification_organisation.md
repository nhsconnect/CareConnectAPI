---
title: Identification | Organisation
keywords: usecase, Organization
tags: [rest, fhir, identification]
sidebar: accessrecord_rest_sidebar
permalink: restfulapis_identification_organisation.html
summary: A formally or informally recognized grouping of people or organizations formed for the purpose of achieving some form of collective action. Includes companies, institutions, corporations, departments, community groups, healthcare practice groups, etc.
---
{% include custom/search.warnbanner.html %}

{% include custom/profile.html content="Organization" page="CareConnect-Organization-1" %}

{% include custom/fhir.resource.html content="[Organization](https://www.hl7.org/fhir/DSTU2/organization.html)" %}

## 1. Read ##

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/Organization/[id]</div>

{% include custom/read.response.html resource="Organization" content="" %}

## 2. Search ##

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/Organization?[searchParameters]</div>

Fetches a bundle of all `Organization` resources for the specified search criteria.

{% include custom/search.header.html resource="Organization" %}

### 2.1. Search Parameters ###

{% include custom/search.parameters.html resource="Organization"     link="https://www.hl7.org/fhir/DSTU2/organization.html#search)" %}

| Name | Type | Description | Conformance  | Path |
|------|------|-------------|-------|------|
| `adddress-postcode` | `string` | A postalCode specified in an address | MAY | Organization.address.postalCode |
| `identifier` | `token` | 	Any identifier for the organization (e.g. SDS/ODS code) | MAY | Organization.identifier |

<!--
| `name` | `string` | A portion of the name of the organisation | | Organization.name |
-->

{% include custom/search.nopat.string.html para="2.1.1." resource="Organization" content="address-postcode"  example="DE22%203NE" text1="Post Code" text2="DE22 3NE" %}

{% include custom/search.nopat.identifier.html para="2.1.2." resource="Organization" content="identifier" subtext="SDS/ODS Code" example="https://fhir.nhs.uk/Id/ods-organization-code|RTG" text1="NHS Organisation" text2="RTG (Derby Teaching Hospitals NHS Trust)" %}

{% include custom/search.response.html resource="Organization" %}

## 3. Example ##

### 3.1 Request Query ###

Return all Organization resources with a ODS Code of C81010, the format of the response body will be xml. Replace 'baseUrl' with the actual base Url of the FHIR Server.

#### 3.1.1. cURL ####

{% include custom/embedcurl.html title="Search Organization" command="curl -H 'Accept: application/xml+fhir' -H 'Authorization: BEARER [token]' -X GET  '[baseUrl]/Organization?identifier=https://fhir.nhs.uk/Id/ods-organization-code|C81010'" %}

{% include custom/search.response.headers.html resource="Organization" %}

### 3.3 Response Body ###

```xml
<Bundle xmlns="http://hl7.org/fhir">
    <id value="19d78778-5e6e-4866-9bd3-6376f863f307"/>
    <meta>
        <lastUpdated value="2017-06-02T09:29:08.195+01:00"/>
    </meta>
    <type value="searchset"/>
    <total value="1"/>
    <link>
        <relation value="self"/>
        <url value="[baseUrl]/Organization?identifier=C81010"/>
    </link>
    <entry>
        <fullUrl value="[baseUrl]/Organization/24965"/>
        <resource>
            <Organization xmlns="http://hl7.org/fhir">
                <id value="24965"/>
                <meta>
                    <lastUpdated value="2017-06-02T09:27:43.366+01:00"/>
                    <profile value="https://fhir.hl7.org.uk/StructureDefinition/CareConnect-Organization-1"/>
                </meta>
                <identifier>
                    <system value="https://fhir.nhs.uk/Id/ods-organization-code"/>
                    <value value="C81010"/>
                </identifier>
                <type>
                    <coding>
                        <system value="https://fhir.hl7.org.uk/ValueSet/organisation-type-1"/>
                        <code value="prov"/>
                        <display value="Healthcare Provider"/>
                    </coding>
                </type>
                <name value="The Moir Medical Centre"/>
                <telecom>
                    <system value="phone"/>
                    <value value="0115 9737320"/>
                    <use value="work"/>
                </telecom>
                <address>
                    <use value="work"/>
                    <type value="both"/>
                    <line value="Regent Street"/>
                    <line value="Long Eaton"/>
                    <city value="Nottingham"/>
                    <postalCode value="NG10 1QQ"/>
                </address>
            </Organization>
        </resource>
        <search>
            <mode value="match"/>
        </search>
    </entry>
</Bundle>
```
