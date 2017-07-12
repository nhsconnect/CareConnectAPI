---
title: Foundation | ValueSet
keywords: foundations, fhir
tags: [foundation,use_case,fhir,rest,api,noccprofile]
sidebar: accessrecord_rest_sidebar
permalink: api_foundation_valueset.html
summary: A value set specifies a set of codes drawn from one or more code systems.
---

{% include custom/search.warnbanner.html %}

{% include custom/fhir.referencemin.html resource="" page="" fhirlink="[ValueSet](http://www.hl7.org/fhir/dstu2/valueset.html)" content="User Stories" userlink="" %}


## 1. Read ##

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/ValueSet/[id]</div>

{% include custom/read.response.html resource="ValueSet" content="" %}

## 2. Example ##

### 2.1 Request Query ###

Return the ValueSet for Care Connect Administrative Gender. Replace 'baseUrl' with the actual base Url of the FHIR Server.

#### 2.1.1. cURL ####

{% include custom/embedcurl.html title="Read Care Connect Administrative Gender ValueSet" command="curl -H 'Accept: application/xml+fhir' -H 'Authorization: BEARER [token]' -X GET  '[baseUrl]/ValueSet/CareConnect-AdministrativeGender-1'" %}

{% include custom/search.response.headers.html resource="ValueSet"  %}

### 2.3 Response Body ###

```xml
<ValueSet xmlns="http://hl7.org/fhir">
   <id value="CareConnect-AdministrativeGender-1"/>
   <meta>
      <lastUpdated value="2016-08-03T00:00:00+01:00"/>
   </meta>
   <text>
      <status value="generated"/>
   </text>
   <contained>
      <ConceptMap xmlns="http://hl7.org/fhir">
         <id value="map"/>
         <name value="NHS Data Model and Dictionary Mapping"/>
         <status value="active"/>
         <sourceReference>
            <reference value="https://fhir-test.hl7.org.uk/ValueSet/CareConnect-AdministrativeGender-1"/>
         </sourceReference>
         <targetReference>
            <reference value="https://fhir-test.hl7.org.uk/ValueSet/CareConnect-PersonStatedGender-DDMAP-1"/>
         </targetReference>
         <element>
            <code value="male"/>
            <target>
               <code value="1"/>
               <equivalence value="equivalent"/>
            </target>
         </element>
         <element>
            <code value="female"/>
            <target>
               <code value="2"/>
               <equivalence value="equivalent"/>
            </target>
         </element>
         <element>
            <code value="other"/>
            <target>
               <code value="9"/>
               <equivalence value="equivalent"/>
            </target>
         </element>
         <element>
            <code value="unknown"/>
            <target>
               <code value="X"/>
               <equivalence value="equivalent"/>
            </target>
         </element>
      </ConceptMap>
   </contained>
   <extension url="http://hl7.org/fhir/StructureDefinition/valueset-map">
      <valueReference>
         <reference value="#map"/>
      </valueReference>
   </extension>
   <extension url="http://hl7.org/fhir/StructureDefinition/valueset-oid">
      <valueUri value="urn:oid:2.16.840.1.113883.4.642.2.1"/>
   </extension>
   <extension url="http://hl7.org/fhir/StructureDefinition/structuredefinition-fmm">
      <valueInteger value="1"/>
   </extension>
   <url value="https://fhir-test.hl7.org.uk/ValueSet/CareConnect-AdministrativeGender-1"/>
   <version value="1.0.0"/>
   <name value="Care Connect Administrative Gender"/>
   <status value="active"/>
   <publisher value="HL7 UK"/>
   <description value="The gender of a person used for administrative purposes."/>
   <requirements value="The codes listed in this FHIR ValueSet have a 'Required' binding; for conformance the Administrative Gender element SHALL include a code listed below."/>
   <copyright value="Copyright � 2016 HL7 UK

Licensed under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with the License. You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.

HL7� FHIR� standard Copyright � 2011+ HL7

The HL7� FHIR� standard is used under the FHIR license. You may obtain a copy of the FHIR license at

https://www.hl7.org/fhir/license.html"/>
   <codeSystem>
      <system value="http://hl7.org/fhir/administrative-gender"/>
      <concept>
         <code value="male"/>
         <display value="Male"/>
         <definition value="Male"/>
      </concept>
      <concept>
         <code value="female"/>
         <display value="Female"/>
         <definition value="Female"/>
      </concept>
      <concept>
         <code value="other"/>
         <display value="Other"/>
         <definition value="Other"/>
      </concept>
      <concept>
         <code value="unknown"/>
         <display value="Unknown"/>
         <definition value="Unknown"/>
      </concept>
   </codeSystem>
</ValueSet>
```
