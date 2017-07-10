---
title: Workflow | OrderResponse
keywords: usecase, orderresponse
tags: [rest, fhir, workflow,api, noccprofile]
sidebar: foundations_sidebar
permalink: restfulapis_workflow_orderresponse.html
summary: A response to an order.
---

{% include custom/search.warnbanner.html %}

{% include custom/fhir.referencemin.html resource="" page="" fhirlink="[OrderResponse](https://hl7.org/fhir/DSTU2/orderresponse.html)" content="User Stories" userlink="" %}


## 1. Read ##

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/OrderResponse/[id]</div>

`TODO`

## 2. Search ##

None

## 3. Create ##

<div markdown="span" class="alert alert-success" role="alert">
POST [baseUrl]/OrderResponse</div>

Returns either the created `OrderResponse` or an `OperationOutcome` resource.

## 4. Update ##

<div markdown="span" class="alert alert-success" role="alert">
PUT [baseUrl]/OrderResponse/[id]</div>

Updates the specified `OrderResponse`

## 5. Example ##

### 5.1 Query ###

Post a OrderResponse to conform the completion of the Read Laboratory task.

#### cURL ####

{% include custom/embedcurl.html title="Create OrderResponse" command="curl -H 'Content-Type: application/xml+fhir' -H 'Authorization: BEARER [token]' -X POST  '[baseUrl]/OrderResponse' -d '*** Removed for clarity, see below ***'" %}

#### Request Body ####

```xml
<OrderResponse xmlns="http://hl7.org/fhir">
   <contained>
      <Order xmlns="http://hl7.org/fhir">
         <id value="order"/>
         <subject>
            <reference value="#pat"/>
         </subject>
         <reasonCodeableConcept>
            <coding>
               <system value="http://snomed.info/sct"/>
               <code value="324861000000109"/>
               <display value="Review of patient laboratory test report"/>
            </coding>
         </reasonCodeableConcept>
         <detail>
            <reference value="https://fhir.uhs.nhs.uk/OrderComms/DiagnosticReport/12345ReportId"/>
         </detail>
      </Order>
   </contained>
   <contained>
      <Patient xmlns="http://hl7.org/fhir">
         <id value="pat"/>
         <meta>
            <profile value="https://fhir-test.hl7.org.uk/StructureDefinition/CareConnect-Patient-1"/>
         </meta>
         <identifier>
            <system value="https://fhir.uhs.nhs.uk/PAS/Patient/"/>
            <value value="1234DEF"/>
         </identifier>
         <name>
            <family value="Kanfeld"/>
         </name>
         <gender value="female"/>
         <birthDate value="1998-03-19"/>
      </Patient>
   </contained>
   <contained>
      <Practitioner xmlns="http://hl7.org/fhir">
         <id value="prac"/>
         <meta>
            <profile value="https://fhir-test.hl7.org.uk/StructureDefinition/CareConnect-Practitioner-1"/>
         </meta>
         <identifier>
            <system value="https://fhir.nhs.uk/Id/sds-user-id"/>
            <value value="123455"/>
         </identifier>
         <name>
            <family value="Example"/>
         </name>
      </Practitioner>
   </contained>
   <request>
      <reference value="#order"/>
   </request>
   <date value="2017-06-15T14:57:54+01:00"/>
   <who>
      <reference value="#prac"/>
   </who>
   <orderStatus value="completed"/>
</OrderResponse>
```

{% include custom/search.response.headers.create.html resource="Encounter" %}

### 5.3 Response Body ###

```xml
<OperationOutcome xmlns="http://hl7.org/fhir">
    <text>
        <status value="generated"/>
        <div xmlns="http://www.w3.org/1999/xhtml">
            <h1>Operation Outcome</h1>
            <table border="0">
                <tr>
                    <td style="font-weight: bold;">information</td>
                    <td>[]</td>
                    <td>
                        <pre>Successfully created resource &quot;OrderResponse/1/_history/1&quot; in 141ms</pre>
                    </td>
                </tr>
            </table>
        </div>
    </text>
    <issue>
        <severity value="information"/>
        <code value="informational"/>
        <diagnostics value="Successfully created resource &quot;OrderResponse/1/_history/1&quot; in 141ms"/>
    </issue>
</OperationOutcome>
```
