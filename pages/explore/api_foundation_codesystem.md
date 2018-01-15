---
title: Foundation | CodeSystem
keywords: foundations, fhir
tags: [foundation,use_case,fhir,rest,api,noccprofile,codesystem]
sidebar: accessrecord_rest_sidebar
permalink: api_foundation_codesystem.html
summary: A code system resource specifies a set of codes drawn from one or more code systems.
---

{% include custom/search.warnbanner.html %}

{% include custom/fhir.reference.html resource="" page="" fhirname="CodeSystem" fhirlink="codesystem.html" content="-" userlink="-" %}

## 1. Read ##

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/CodeSystem/[id]</div>

{% include custom/read.response.html resource="CodeSystem" content="" %}

## 2. Example ##

{% include custom/search.warn_ri_banner.html %}

### 2.1 Request Query ###

Return the CodeSystem for Care Connect NSH Verification Status. Replace 'baseUrl' with the actual base Url of the FHIR Server.

#### 2.1.1. cURL ####

{% include custom/embedcurl.html title="Read Care Connect NHS Verification Status CodeSystem" command="curl -H 'Accept: application/xml+fhir' -H 'Authorization: BEARER [token]' -X GET  '[baseUrl]/CodeSystem/CareConnect-NHSNumberVerificationStatus-1'" %}

### 2.2 Response Body ###

```xml
<CodeSystem xmlns="http://hl7.org/fhir">
	<id value="CareConnect-NHSNumberVerificationStatus-1"/>
	<extension url="http://hl7.org/fhir/StructureDefinition/codesystem-sourceReference">
		<valueUri value="http://www.datadictionary.nhs.uk/data_dictionary/data_field_notes/n/nhs/nhs_number_status_indicator_code_de.asp?shownav=1"/>
	</extension>
	<url value="https://fhir.hl7.org.uk/STU3/CodeSystem/CareConnect-NHSNumberVerificationStatus-1"/>
	<version value="1.0.0"/>
	<name value="Care Connect NHS Number Verification Status"/>
	<status value="active"/>
	<date value="2017-08-01T00:00:00+00:00"/>
	<publisher value="HL7 UK"/>
	<description value="A CodeSystem that identifies the trace status of the NHS number.  This CodeSystem is comprised of codes from the NHS Data Model and Dictionary: NHS Number Status Indicator Code."/>
	<copyright value="Copyright © 2016 HL7 UK"/>
	<caseSensitive value="true"/>
	<content value="complete"/>
	<concept>
		<code value="01"/>
		<display value="Number present and verified"/>
	</concept>
	<concept>
		<code value="02"/>
		<display value="Number present but not traced"/>
	</concept>
	<concept>
		<code value="03"/>
		<display value="Trace required"/>
	</concept>
	<concept>
		<code value="04"/>
		<display value="Trace attempted - No match or multiple match found"/>
	</concept>
	<concept>
		<code value="05"/>
		<display value="Trace needs to be resolved - (NHS number or patient detail conflict)"/>
	</concept>
	<concept>
		<code value="06"/>
		<display value="Trace in progress"/>
	</concept>
	<concept>
		<code value="07"/>
		<display value="Number not present and trace not required"/>
	</concept>
	<concept>
		<code value="08"/>
		<display value="Trace postponed (baby under six weeks old)"/>
	</concept>
</CodeSystem>
```
