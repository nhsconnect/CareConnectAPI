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


## 1. Read Operation ##

<div markdown="span" class="alert alert-success" role="alert">
GET [baseUrl]/Binary/[id]</div>

<p>Return a single <code class="highlighter-rouge">Binary</code> for the specified id.</p>

<p>All requests SHALL contain a valid ‘Authorization’ header and SHALL contain an ‘Accept’ header. The `Accept` header indicates the format of the response the client is able to understand, this maybe be one of the following <code class="highlighter-rouge">application/json+fhir</code> or <code class="highlighter-rouge">application/xml+fhir</code>.</p>, this will return the requested resource as <code class="highlighter-rouge">Binary</code> resource. The <code class="highlighter-rouge">Binary</code> can be returned in native format, this is achieved by adding the relevant mime type the Accept header (or use wild card <code class="highlighter-rouge">*/*</code>)


<h3 id="readresponse">1.1. Response</h3>

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
