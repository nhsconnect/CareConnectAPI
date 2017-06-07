---
title: Clinical | Medication Order
keywords: usecase, medication, order
tags: [fhir, rest, clinical, medication]
sidebar: foundations_sidebar
permalink: restfulapis_clinical_medicationorder.html
summary: An order for both supply of the medication and the instructions for administration of the medication to a patient. The resource is called "MedicationOrder" rather than "MedicationPrescription" to generalize the use across inpatient and outpatient settings as well as for care plans, etc.
---
{% include custom/search.warnbanner.html %}

{% include custom/profile.html content="Medication Order" page="CareConnect-MedicationOrder-1" %}

{% include custom/fhir.resource.html content="[MedicationOrder](https://www.hl7.org/fhir/DSTU2/medicationorder.html#search)" %}

## 1. Read ##

<div markdown="span" class="alert alert-success" role="alert">
GET /MedicationOrder/[id]</div>

Return a single `MedicationOrder` for the specified id

## 2. Search ##

<div markdown="span" class="alert alert-success" role="alert">
GET /MedicationOrder?[searchParameters]]</div>

Fetches a bundle of all `MedicationOrder` resources for the specified patient.

{% include custom/search.header.html resource="MedicationOrder" %}

### 2.1. Search Parameters ###

{% include custom/moscow.html content="[MedicationOrder](https://www.hl7.org/fhir/DSTU2/medicationorder.html#search)" %}

| Name    | Type   | Description    | Conformance        | Path |
|---------|--------|----------------|--------------------|------|
| `date` | `date` | Returns medication request to be administered on a specific date | SHOULD | MedicationOrder.dosageInstruction.timing.event |
| `patient` | `reference` | The identity of a patient to list orders for | SHALL | MedicationOrder.patient<br>(Patient) |
| `status` | `token` | Status of the prescription | SHOULD | MedicationOrder.status |

<!--
| `datewritten` | `date` | Return prescriptions written on this date |  | MedicationOrder.dateWritten |
| `identifier` | `token` | The source system of the prescriptions for  |  | MedicationOrder.identifier |
{% include custom/search.date.plus.html content="MedicationOrder" name="datewritten"  %}

{% include custom/search.identifier.html resource="MedicationOrder" content="identifier" subtext="System Filter" example="https://theccg.systemsupplier.co.uk/MedicationOrder|" text1="The CCG System Supplier" text2="not specified" %}
-->
{% include custom/search.date.plus.html para="2.1.1." content="MedicationOrder" name="date"  %}

{% include custom/search.patient.html para="2.1.2." content="MedicationOrder" %}

{% include custom/search.status.html para="2.1.3." content="MedicationOrder" options="active | on-hold | completed | entered-in-error | stopped | draft" selected="active"  %}

## 3. Example ##

### 3.1 Request Query ###

Return all MedciationOrder resources for Patient with a NHS Number of 9876543210, the format of the response body will be xml. Replace 'baseUrl' with the actual base Url of the FHIR Server.

#### 3.1.1. cURL ####

{% include custom/embedcurl.html title="Search MedicationOrder" command="curl -X GET  'http://[baseUrl]/MedicationOrder?patient.identifier=https://fhir.nhs.uk/Id/nhs-number|9876543210&_format=xml'" %}

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
    <id value="58ef1cb1-bbc4-482c-a469-8a0d338bb02b"/>
    <meta>
        <lastUpdated value="2017-06-02T09:15:15.163+01:00"/>
    </meta>
    <type value="searchset"/>
    <total value="1"/>
    <link>
        <relation value="self"/>
        <url value="http://127.0.0.1:8181/Dstu2/MedicationOrder?patient=https%3A%2F%2Fpds.proxy.nhs.uk%2FPatient%2F9876543210"/>
    </link>
    <entry>
        <fullUrl value="http://127.0.0.1:8181/Dstu2/MedicationOrder/24961"/>
        <resource>
            <MedicationOrder xmlns="http://hl7.org/fhir">
                <id value="24961"/>
                <meta>
                    <versionId value="1"/>
                    <lastUpdated value="2017-06-02T09:14:56.728+01:00"/>
                    <profile value="https://fhir.hl7.org.uk/StructureDefinition/CareConnect-MedicationOrder-1"/>
                </meta>
                <extension url="https://fhir.hl7.org.uk/StructureDefinition/Extension-CareConnect-MedicationSupplyType-1">
                    <valueCodeableConcept>
                        <coding>
                            <system value="http://snomed.info/sct"/>
                            <code value="394823007"/>
                            <display value="NHS Prescription"/>
                        </coding>
                    </valueCodeableConcept>
                </extension>
                <dateWritten value="2017-05-25T00:00:00+01:00"/>
                <status value="active"/>
                <patient>
                    <reference value="https://pds.proxy.nhs.uk/Patient/9876543210"/>
                    <display value="Bernie Kanfeld"/>
                </patient>
                <prescriber>
                    <reference value="https://sds.proxy.nhs.uk/Practitioner/G8133438"/>
                    <display value="Dr AA Bhatia"/>
                </prescriber>
                <note value="Please explain to Bernie how to use injector."/>
                <medicationCodeableConcept>
                    <coding>
                        <system value="http://snomed.info/sct"/>
                        <code value="10097211000001102"/>
                        <display value="Insulin glulisine 100units/ml solution for injection 3ml pre-filled disposable devices"/>
                    </coding>
                </medicationCodeableConcept>
                <dosageInstruction>
                    <text value="Three times a day"/>
                    <additionalInstructions>
                        <coding>
                            <system value="http://snomed.info/sct"/>
                            <code value="1521000175104"/>
                            <display value="After dinner"/>
                        </coding>
                    </additionalInstructions>
                    <timing>
                        <code>
                            <coding>
                                <system value="http://hl7.org/fhir/v3/GTSAbbreviation"/>
                                <code value="TID"/>
                            </coding>
                        </code>
                    </timing>
                </dosageInstruction>
                <dispenseRequest>
                    <numberOfRepeatsAllowed value="5"/>
                </dispenseRequest>
            </MedicationOrder>
        </resource>
        <search>
            <mode value="match"/>
        </search>
    </entry>
</Bundle>
```
