---
title: Identification | Organisation
keywords: usecase, Organization
tags: [rest, fhir, identification]
sidebar: accessrecord_rest_sidebar
permalink: restfulapis_identification_organisation.html
summary: A formally or informally recognized grouping of people or organizations formed for the purpose of achieving some form of collective action. Includes companies, institutions, corporations, departments, community groups, healthcare practice groups, etc.
---
{% include custom/search.warnbanner.html %}

{% include custom/profile.html content="Organization" page="CareConnect-Organization-1.html" %}

{% include custom/fhir.resource.html content="[Organization](https://www.hl7.org/fhir/DSTU2/organization.html#search)" %}

## 1. Read ##

<div markdown="span" class="alert alert-success" role="alert">
GET /Organizatio/[id]</div>
Return a single `Organization` for the specified id.

## 2. Search Parameters ##

<div markdown="span" class="alert alert-success" role="alert">
GET /Organization?[searchParameters]</div>
Organization contains the demographics for the organisation. Fetches a bundle of all `Organization` resources for the specified search criteria.

{% include custom/moscow.html content="[Organization](https://www.hl7.org/fhir/DSTU2/organization.html#search)" %}

| Name | Type | Description | Conformance  | Path |
|------|------|-------------|-------|------|
| `adddress-postcode` | `string` | A postalCode specified in an address | MAY | Organization.address.postalCode |
| `identifier` | `token` | 	Any identifier for the organization (e.g. SDS/ODS code) | MAY | Organization.identifier |

<!--
| `name` | `string` | A portion of the name of the organisation | | Organization.name |
-->

{% include custom/search.string.html para="2.1." resource="Organization" content="address-postcode"  example="DE22%203NE" text1="Post Code" text2="DE22 3NE" %}

{% include custom/search.identifier.html para="2.2." resource="Organization" content="identifier" subtext="SDS/ODS Code" example="https://fhir.nhs.uk/Id/ods-organization-code|RTG" text1="NHS Organisation" text2="RTG (Derby Teaching Hospitals NHS Trust)" %}

## 3. Example ##

### 3.1 Request Query ###

Return all Organization resources with a ODS Code of C81010, the format of the response body will be xml. Replace 'baseUrl' with the actual base Url of the FHIR Server.

#### 3.1.1. cURL ####

{% include custom/embedcurl.html title="Search Organization" command="curl -X GET  'http://[baseUrl]/Organization?identifier=https://fhir.nhs.uk/Id/ods-organization-code|C81010&_format=xml'" %}

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
    <id value="63d0c5d3-a8ed-4da9-a711-26d686952cc8"/>
    <meta>
        <lastUpdated value="2017-05-23T11:09:28.625-04:00"/>
    </meta>
    <type value="searchset"/>
    <total value="1"/>
    <link>
        <relation value="self"/>
        <url value="http://fhirtest.uhn.ca/baseDstu2/Organization?identifier=https%3A%2F%2Ffhir.nhs.uk%2FId%2Fods-organization-code%7CC81010"/>
    </link>
    <entry>
        <fullUrl value="http://fhirtest.uhn.ca/baseDstu2/Organization/32369"/>
        <resource>
            <Organization xmlns="http://hl7.org/fhir">
                <id value="32369"/>
                <meta>
                    <versionId value="1"/>
                    <lastUpdated value="2017-05-23T11:08:30.692-04:00"/>
                    <profile value="https://fhir.nhs.uk/StructureDefinition/CareConnect-Organization-1"/>
                </meta>
                <identifier>
                    <system value="https://fhir.nhs.uk/Id/ods-organization-code"/>
                    <value value="C81010"/>
                </identifier>
                <type>
                    <coding>
                        <system value="https://fhir.nhs.uk/ValueSet/organisation-type-1"/>
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
