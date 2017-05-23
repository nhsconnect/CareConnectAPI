---
title: Identification | Organisation
keywords: usecase, Organization
tags: [rest, fhir, identification]
sidebar: accessrecord_rest_sidebar
permalink: restfulapis_identification_organisation.html
summary: Identification Organization
---
{% include search.warnbanner.html %}
{% include profile.html content="[Care Connect Organization](http://www.interopen.org/candidate-profiles/care-connect/CareConnect-Organization-1.html)" %}

## 1. Read ##

<div markdown="span" class="alert alert-success" role="alert">
GET /Organizatio/[id]</div>
Return a single `Organization` for the specified id.

## 2. Search Parameters ##

<div markdown="span" class="alert alert-success" role="alert">
GET /Organization?[searchParameters]</div>
Organization contains the demographics for the organisation. Fetches a bundle of all `Organization` resources for the specified search criteria.

{% include moscow.html content="[Organization](https://www.hl7.org/fhir/DSTU2/organization.html#search)" %}

| Name | Type | Description | SHALL | Path |
|------|------|-------------|-------|------|
| `adddress-postcode` | `string` | A postalCode specified in an address | Y | Organization.address.postalCode |
| `identifier` | `token` | 	Any identifier for the organization (e.g. SDS/ODS code) | Y | Organization.identifier |
| `name` | `string` | A portion of the name of the organisation | | Organization.name |

{% include search.string.html para="2.1." resource="Organization" content="address-postcode"  example="DE22%203NE" text1="Post Code" text2="DE22 3NE" %}

{% include search.identifier.html para="2.2." resource="Organization" content="identifier" subtext="SDS/ODS Code" example="https://fhir.nhs.uk/Id/ods-organization-code|RTG" text1="NHS Organisation" text2="RTG (Derby Teaching Hospitals NHS Trust)" %}

### 3.1 Query ###
Return all Practitioner resources with a GP Code of G8133438, the format of the response body will be xml. Replace 'baseUrl' to the actual base Url of the FHIR Server.

```curl
curl --get http://[baseUrl]/Organization?identifier=http://fhir.nhs.net/Id/ods-organization-code|C81010&_format=xml
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
    <id value="63d0c5d3-a8ed-4da9-a711-26d686952cc8"/>
    <meta>
        <lastUpdated value="2017-05-23T11:09:28.625-04:00"/>
    </meta>
    <type value="searchset"/>
    <total value="1"/>
    <link>
        <relation value="self"/>
        <url value="http://fhirtest.uhn.ca/baseDstu2/Organization?identifier=http%3A%2F%2Ffhir.nhs.net%2FId%2Fods-organization-code%7CC81010"/>
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
                    <system value="http://fhir.nhs.net/Id/ods-organization-code"/>
                    <value value="C81010"/>
                </identifier>
                <type>
                    <coding>
                        <system value="http://fhir.nhs.net/ValueSet/organisation-type-1"/>
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
