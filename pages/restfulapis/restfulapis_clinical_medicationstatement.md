---
title: Clinical | Medication Statement
keywords: usecase, clinical
tags: [fhir, rest, clinical, medication]
sidebar: foundations_sidebar
permalink: restfulapis_clinical_medicationstatement.html
summary: A record of a medication that is being consumed by a patient. A MedicationStatement may indicate that the patient may be taking the medication now, or has taken the medication in the past or will be taking the medication in the future.
---
{% include custom/search.warnbanner.html %}

{% include custom/profile.html content="[Care Connect Medication Statement](http://www.interopen.org/candidate-profiles/care-connect/CareConnect-MedicationStatement-1.html)" %}

{% include custom/fhir.resource.html content="[MedicationStatement](https://www.hl7.org/fhir/DSTU2/medicationstatement.html#search)" %}

## 1. Read ##

<div markdown="span" class="alert alert-success" role="alert">
GET /MedicationStatement/[id]</div>
Return a single `Medication Statement` for the specified id.

## 2. Search Parameters ##

<div markdown="span" class="alert alert-success" role="alert">
GET /MedicationStatement?[searchParameters]</div>
Medication Statement resource contains current medication information for a patient. Fetches a bundle of all `MedicationStatement` resources for the specified patient.

{% include custom/moscow.html content="[MedicationStatement](https://www.hl7.org/fhir/DSTU2/medicationstatement.html#search)" %}

| Name | Type | Description | Conformance  | Path |
|------|------|-------------|-------|------|
| `effectivedate` | `date` | Date when patient was taking (or not taking) the medication |  | MedicationStatement.effective[x] |
| `patient` | `reference` | The identity of a patient to list statements for | Y | MedicationStatement.patient<br>(Patient) |
| `status` | `token` | Return statements that match the given status | Y | MedicationStatement.status |

{% include custom/search.date.plus.html para="2.1." content="MedicationStatement" name="effectivedate" %}

{% include custom/search.patient.html para="2.2" content="MedicationStatement" %}

{% include custom/search.status.html para="2.3." content="MedicationStatement" options="active | completed | entered-in-error | intended" selected="active" %}

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
    <id value="6d428483-b147-4f0a-8fe8-0071edf0b5e6"/>
    <meta>
        <lastUpdated value="2017-05-30T09:57:25.499+01:00"/>
    </meta>
    <type value="searchset"/>
    <total value="1"/>
    <link>
        <relation value="self"/>
        <url value="http://127.0.0.1:8181/Dstu2/MedicationStatement?patient=https%3A%2F%2Fpds.proxy.nhs.uk%2FPatient%2F9876543210"/>
    </link>
    <entry>
        <fullUrl value="http://127.0.0.1:8181/Dstu2/MedicationStatement/14953"/>
        <resource>
            <MedicationStatement xmlns="http://hl7.org/fhir">
                <id value="14953"/>
                <meta>
                    <versionId value="1"/>
                    <lastUpdated value="2017-05-30T09:57:11.153+01:00"/>
                    <profile value="https://fhir.nhs.uk/StructureDefinition/CareConnect-MedicationStatement-1"/>
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
