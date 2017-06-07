---
title: Clinical | Medication Statement
keywords: usecase, clinical
tags: [fhir, rest, clinical, medication]
sidebar: foundations_sidebar
permalink: restfulapis_clinical_medicationstatement.html
summary: A record of a medication that is being consumed by a patient. A MedicationStatement may indicate that the patient may be taking the medication now, or has taken the medication in the past or will be taking the medication in the future.
---
{% include custom/search.warnbanner.html %}

{% include custom/profile.html content="Medication Statement" page="CareConnect-MedicationStatement-1" %}

{% include custom/fhir.resource.html content="[MedicationStatement](https://www.hl7.org/fhir/DSTU2/medicationstatement.html#search)" %}

## 1. Read ##

<div markdown="span" class="alert alert-success" role="alert">
GET /MedicationStatement/[id]</div>
Return a single `Medication Statement` for the specified id.

## 2. Search ##

<div markdown="span" class="alert alert-success" role="alert">
GET /MedicationStatement?[searchParameters]</div>

Fetches a bundle of all `MedicationStatement` resources for the specified patient.

{% include custom/search.header.html resource="MedicationStatement" %}

### 2.1. Search Parameters ###

{% include custom/moscow.html content="[MedicationStatement](https://www.hl7.org/fhir/DSTU2/medicationstatement.html#search)" %}

| Name | Type | Description | Conformance  | Path |
|------|------|-------------|-------|------|
| `effectivedate` | `date` | Date when patient was taking (or not taking) the medication | SHOULD | MedicationStatement.effective[x] |
| `patient` | `reference` | The identity of a patient to list statements for | SHALL | MedicationStatement.patient<br>(Patient) |
| `status` | `token` | Return statements that match the given status | SHOULD | MedicationStatement.status |

{% include custom/search.date.plus.html para="2.1.1." content="MedicationStatement" name="effectivedate" %}

{% include custom/search.patient.html para="2.1.2" content="MedicationStatement" %}

{% include custom/search.status.html para="2.1.3." content="MedicationStatement" options="active | completed | entered-in-error | intended" selected="active" %}

{% include custom/search.response.html resource="MedicationStatement" %}

## 3. Example ##

### 3.1 Request Query ###

Return all MedciationStatement resources for Patient with a NHS Number of 9876543210, the format of the response body will be xml. Replace 'baseUrl' with the actual base Url of the FHIR Server.

#### 3.1.1. cURL ####

{% include custom/embedcurl.html title="Search MedicationStatement" command="curl -X GET  'http://[baseUrl]/MedicationStatement?patient.identifier=https://fhir.nhs.uk/Id/nhs-number|9876543210&_format=xml'" %}

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
    <id value="6097e823-f4dd-4713-9e48-88a06c68e258"/>
    <meta>
        <lastUpdated value="2017-06-02T09:18:44.898+01:00"/>
    </meta>
    <type value="searchset"/>
    <total value="1"/>
    <link>
        <relation value="self"/>
        <url value="http://127.0.0.1:8181/Dstu2/MedicationStatement?patient=https%3A%2F%2Fpds.proxy.nhs.uk%2FPatient%2F9876543210"/>
    </link>
    <entry>
        <fullUrl value="http://127.0.0.1:8181/Dstu2/MedicationStatement/24963"/>
        <resource>
            <MedicationStatement xmlns="http://hl7.org/fhir">
                <id value="24963"/>
                <meta>
                    <versionId value="1"/>
                    <lastUpdated value="2017-06-02T09:18:21.553+01:00"/>
                    <profile value="https://fhir.hl7.org.uk/StructureDefinition/CareConnect-MedicationStatement-1"/>
                </meta>
                <extension url="https://fhir.hl7.org.uk/StructureDefinition/Extension-CareConnect-MedicationStatementLastIssueDate-1">
                    <valueDateTime value="2017-03-27T00:00:00+01:00"/>
                </extension>
                <extension url="https://fhir.hl7.org.uk/StructureDefinition/Extension-CareConnect-MedicationRepeatInformation-1">
                    <extension url="reviewDate">
                        <valueDateTime value="2017-05-27T00:00:00+01:00"/>
                    </extension>
                    <extension url="numberOfRepeatsIssued">
                        <valueInteger value="1"/>
                    </extension>
                </extension>
                <patient>
                    <reference value="https://pds.proxy.nhs.uk/Patient/9876543210"/>
                    <display value="Bernie Kanfeld"/>
                </patient>
                <informationSource>
                    <reference value="https://sds.proxy.nhs.uk/Practitioner/G8040738"/>
                    <display value="Dr AD Jordan"/>
                </informationSource>
                <dateAsserted value="2017-05-29T00:00:00+01:00"/>
                <status value="active"/>
                <supportingInformation>
                    <reference value="MedicationOrder/1710523"/>
                </supportingInformation>
                <supportingInformation>
                    <reference value="MedicationOrder/1232131123"/>
                </supportingInformation>
                <medicationCodeableConcept>
                    <coding>
                        <system value="http://snomed.info/sct"/>
                        <code value="10097211000001102"/>
                        <display value="Insulin glulisine 100units/ml solution for injection 3ml pre-filled disposable devices"/>
                    </coding>
                </medicationCodeableConcept>
                <dosage>
                    <text value="Three times a day"/>
                    <timing>
                        <code>
                            <coding>
                                <system value="http://hl7.org/fhir/v3/GTSAbbreviation"/>
                                <code value="TID"/>
                            </coding>
                        </code>
                    </timing>
                </dosage>
            </MedicationStatement>
        </resource>
        <search>
            <mode value="match"/>
        </search>
    </entry>
</Bundle>
```
