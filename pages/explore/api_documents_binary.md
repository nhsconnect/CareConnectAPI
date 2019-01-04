---
title: Documents | Binary
keywords: getcarerecord, structured, rest, binary
tags: [rest,fhir,documents,api,noccprofile]
sidebar: accessrecord_rest_sidebar
permalink: api_documents_binary.html
summary: A binary resource can contain any content, whether text, image, pdf, zip archive, etc.
---
{% include custom/search.warnbanner.html %}

{% include custom/fhir.referencemin.html resource="Binary" page="" fhirname="Binary" fhirlink="binary.html" content="" userlink="" %}

There are situations where it is useful or required to handle pure binary content using the same framework as other resources. Typically, this is when the binary content is referred to from other FHIR Resources. Using the same framework means that the existing servers, security arrangements, code libraries etc. can handle additional related content. Typically, Binary resources are used for handling content such as:

- PDF Documents
- Images
- HL7 Structured Documents (e.g. CDA or FHIR Documents)

Binary resources behave slightly differently to all other resources on the RESTful API. Specifically, when a read request is made for the binary resource that doesn't explicitly specify the FHIR content types "application/fhir+xml" or "application/fhir+json", then the content should be returned using the content type stated in the resource. e.g. if the content type in the resource is "application/pdf", then the content should be returned as a PDF directly.

The HL7 specification states that "the intent is that unless specifically requested, the FHIR XML/JSON representation is not returned". This behaviour is implemented in the Reference Implementation and would be expected of any standard implementation.

## 1. Read ##

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/Binary/[id]</div>

<p>Return a single <code class="highlighter-rouge">Binary</code> for the specified id.</p>


<p>All requests SHALL contain a valid ‘Authorization’ header and SHALL contain an ‘Accept’ header. The `Accept` header indicates the format of the response the client is able to understand, this maybe be one of the following <code class="highlighter-rouge">application/json+fhir</code> or <code class="highlighter-rouge">application/xml+fhir</code>, this will return the requested resource as FHIR <code class="highlighter-rouge">Binary</code> resource.</p>

<p>The <code class="highlighter-rouge">Binary</code> will be returned in a native format (i.e. not contained within a FHIR resource) if no MIME type is not specified, an appropriate MIME type is included or a wild card (<code class="highlighter-rouge">*/*</code>) is included within the request header.</p>

Common health related MIME types are listed below:

<table>
  <thead>
    <tr>
       <th>Image/Document Type</th>
       <th>MIME Type</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>html</td>
      <td>text/html</td>
    </tr>
    <tr>
      <td>pdf</td>
      <td>application/pdf</td>
    </tr>
    <tr>
      <td>dicom</td>
      <td>application/dicom</td>
    </tr>
    <tr>
      <td>png</td>
      <td>image/png</td>
    </tr>
    <tr>
      <td>jpg</td>
      <td>image/jpeg</td>
    </tr>
    <tr>
      <td>FHIR Documents</td>
      <td>application/xml+fhir or application/json+fhir</td>
    </tr>
  <!--  <tr>
      <td>openEHR</td>
      <td>application/vnd.openehr+json</td>
    </tr> -->
  </tbody>
</table>

<p>Although this page is describing a FHIR Binary endpoint, a Binary resource can be retrieved from any url. If a FHIR Binary endpoint is used then the resource SHALL be available as both a <code class="highlighter-rouge">Binary</code> resource and as a standard URL resource. The default behaviour is that of a URL resource</p>

For Binary resources, the result of a query are different when compared to the rest of FHIR. There are specific ways to indicate the format of the response expected by the server. This is via the client specifying the format of the response either via a <code class="highlighter-rouge">&#95;format</code> override on the query parameter of by using a “content-type” HTTP header in the request.


<h3 id="readresponse">1.1. Query 1 - Default Query</h3>

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/Binary/[id]   with no HTTP content-type header</div>

MUST be supported.

Server returns the document using the native mime type of the document – No FHIR resources are returned.

<h3 id="readresponse">1.2. Query 2 - Format Override 1</h3>

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/Binary/[id]?&#95;format=[format] 	with no HTTP Accept header   with no HTTP content-type header</div>

MUST be supported.

Server returns a FHIR Binary resource in the requested format with the “document” BASE64 encoded within the content element.

<h3 id="readresponse">1.3. Query 3 - Format Override 2</h3>

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/Binary/[id] 	with a HTTP Accept header of [format]</div>

SHOULD be supported.

Server returns a FHIR Binary resource in the requested format with the “document” BASE64 encoded within the content element

<h3 id="readresponse">1.4. Query 4 - Format Override 3</h3>

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/Binary/[id]?&#95;format=[format_1]	with a HTTP Accept header of [format_2]</div>

SHOULD be supported.

Server returns a FHIR Binary resource in the as per format_1 as <code class="highlighter-rouge">&#95;format</code> overrides the HTTP Accept headers. The “document” is BASE64 encoded within the content element

<h3 id="readresponse">1.5. Response</h3>

<p>A full set of response codes can be found here <a href="profiles_api_codes.html">API Response Codes</a>. FHIR Servers SHALL support the following response codes:</p>

<table>
  <tbody>
    <tr>
      <td>200</td>
      <td>successful operation</td>
    </tr>
    <tr>
      <td>404</td>
      <td>resource not found</td>
    </tr>
    <tr>
      <td>410</td>
      <td>resource deleted</td>
    </tr>
  </tbody>
</table>

## 2. Search ##

The binary is not searchable as the other API resources are, however, please refer to [DocumentReference](api_documents_documentreference.html){:target="_blank"} for a mechanism to gain access to Binary information through a API.

## 3. Example ##

<h3 id="32-response-headers">3.1 cURL</h3>

Return a Binary resource, the format of the response body will be xml. Replace 'baseUrl' with the actual base Url of the FHIR Server.

{% include custom/embedcurl.html title="Get Binary" command="curl -X GET -H 'Accept: application/json+fhir' -H 'Authorisation: BEARER [token]' -v 'https://data.developer.nhs.uk/ccri/STU3/Binary/5b1e91f0ccf84d0001fffe6d'" %}


<h3 id="32-response-headers">3.2 Explore the Response</h3>

Explore the response in XML & JSON on the Reference Implementation below
<div class="language-http highlighter-rouge">
<pre class="highlight">
<p style="font-size: 110%;">Reference Implementation</p>
Direct link <a target="_blank" href="https://data.developer.nhs.uk/ccri-fhir/STU3/Binary/5b1e91f0ccf84d0001fffe6d">Binary unstructured document download</a>
</pre>
</div>
