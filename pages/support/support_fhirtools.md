---
title: FHIR Tools
keywords: support, communications, community, tools 
tags: [support]
toc: true
sidebar: overview_sidebar
permalink: support_fhirtools.html
summary: "A range of open source and commercial tools that can assist in the design and development of FHIR API's."
---

There is no affiliation between INTEROPen and any of the suppliers listed below. Inclusion in this list does not constitute an endorsement of the tool.
<br><br>
## [ClinFHIR](http://clinfhir.com/)

<div style="display:flex;flex-wrap:wrap">
  <div style="flex:3 1 60%;padding:0 0 1em 0;">
    <p>Developed by David Hay as a result of the HL7 FHIR workshops, ClinFHIR is aimed at helping Clinicians understand HL7 FHIR, and contribute to its development, especially in respect to profiling.</p>
    <p>The tools offered within ClinFHIR include a Patient Viewer, Scenario Builder, Logical Modeller, CodeSystem builder, Extension Definition builder and a Query Tool. The tools make use of three predefined servers and they can be extended to use other DSTU-2 or STU3 servers.</p>
  </div>
  <div style="flex:1 6 40%;padding:0 1em 0 1em;min-width:15em;">
    <img src="images/support/clinfhirlauncher.png" alt="ClinFHIR Launcher Screenshot" style="width:100%; max-width:100%; float:right; margin-left:3%; margin-bottom:3%;">
  </div>
</div>
<br><br>
### [ClinFHIR CodeSystem Editor](http://clinfhir.com/codeSystem.html)

<div style="display:flex;flex-wrap:wrap">
  <div style="flex:3 1 60%;padding:0 0 1em 0;">
    <p>The CodeSystem defines the set of possible values for a resource element. The actual 'binding' between CodeSystem and element is done by the ValueSet. This component allows you to build (and edit) a CodeSystem, and optionally builds the ValueSet as well. Once created, the created extensions are stored on the conformance server.</p>
  </div>
  <div style="flex:1 6 40%;padding:0 1em 0 1em;min-width:15em;">
    <img  src="images/support/clinfhircodesystemeditor.png" alt="ClinFHIR CodeSystem Editor Screenshot"  style="width:100%; max-width:100%; float:right; margin-left:3%; margin-bottom:3%;">
  </div>
</div>
<br><br>
### [ClinFHIR Extension Builder](http://clinfhir.com/EDBuilder.html)

The ClinFHIR extension builder is designed to view and build extension definitions. These can be defined and applied to the Logical Model, which will allow them to be included in the generated Profile.
<br><br>
### [ClinFHIR Logical Modeller](http://clinfhir.com/logicalModeller.html)

<div style="display:flex;flex-wrap:wrap">
  <div style="flex:3 1 60%;padding:0 0 1em 0;">
    <p>The Logical modeller allows the creation of a model that represents a particular interoperability requirement in a format that is easy to use. It uses FHIR data types, and can be based on an existing resource type or completely 'ad hoc'. It is intended to act as a 'bridge' between Modeller and User, and can act as the basis for the generation of the profiling components required by FHIR.</p>
  </div>
  <div style="flex:1 6 40%;padding:0 1em 0 1em;min-width:15em;">
    <img src="images/support/clinfhirlogicalmodeller.png" alt="ClinFHIR Logical Modeller Screenshot" style="width:100%; max-width:100%; float:right; margin-left:3%; margin-bottom:3%;">
  </div>
</div>
<br><br>
### [ClinFHIR Query](http://clinfhir.com/query.html)

<div style="display:flex;flex-wrap:wrap">
  <div style="flex:3 1 60%;padding:0 0 1em 0;">
    <p>ClinFHIR Query allows ad hoc queries to be sent to a FHIR server. This tool duplicates the key feature of tools like Postman and the FHIR Plugin for Notepad++ however it is dedicated to FHIR (unlike Postman which is a generic tool) and it’s far simpler to use than the Notepad++ plugin.</p>
  </div>
  <div style="flex:1 6 40%;padding:0 1em 0 1em;min-width:15em;">
    <img src="images/support/clinfhirquery.png" alt="ClinFHIR Query Screenshot" style="width:100%; max-width:100%; float:right; margin-left:3%; margin-bottom:3%;">
  </div>
</div>
<br><br>
### [ClinFHIR Scenario Builder](http://clinfhir.com/builder.html)

<img src="images/support/clinfhirscenariobuilder.png" alt="ClinFHIR Scenario Builder Screenshot" style="width:40%; float:right; margin-left:3%; margin-bottom:3%;">The Scenario Builder is used to join together the resources needed to represent a specific clinical scenario. It can use Core Resource types, Profiles and Logical models as it does this. The intention is to help people understand how resources can tell a clinical story, and to validate that the resource types available (including profiles) are sufficient.

Patient information is on the Data Server. Profiles on the Conformance server. ValueSets on the Terminology server.
<br><br>
### [ClinFHIR ValueSet Editor](http://clinfhir.com/valuesetCreator.html)

<div style="display:flex;flex-wrap:wrap">
  <div style="flex:3 1 60%;padding 0 0 1em 0;">A tool to support the creation of ValueSet’s. Predominantly works with SNOMED-CT.</div>
  <div style="flex:1 6 40%;padding 0 1em 0 1em;min-width:15em;">
    <img style="max-width:100%;width:100%" src="images/support/clinfhirvalueseteditor.png" alt="ClinFHIR Valueset Editor Screenshot">
  </div>
</div>
<br><br>
## [FHIR Plugin for Notepad++](http://www.healthintersections.com.au/FhirServer/fhirnpp.htm)
<img src="images/support/notepadplugin.png" alt="FHIR Plugin for Notepad++ Screenshot" style="width:40%; float:right; margin-left:3%; margin-bottom:3%;">The FHIR plugin for Notepad++ is provided by Graham Grieves Health Intersections. It is delivering functionality that overlaps with Postman.

Current features for this tool are listed in the associated [Wiki documentation](http://wiki.hl7.org/index.php?title=FHIR_Notepad%2B%2B_Plugin_Documentation) as:
* Conversion between JSON and XML formats
* Instance validation
* Narrative generation
* FHIR Path analysis
* Connect to a server (including Smart on FHIR login)
* Fetch resource from server (driven by conformance statement)
* Post/put a resource to the server

The roadmap for the product is documented as:
* Intellisense (maybe)
* Background validation (maybe)
* Code lookup

The plug-in is aimed very squarely at FHIR (unlike Postman which is a more generic API development tool).
<br><br>
## [Forge](https://fhir.furore.com/forge/)

<img src="images/support/forge.png" alt="Forge Screenshot" style="width:40%; float:right; margin-left:3%; margin-bottom:3%;">Forge is a desktop application used for FHIR profiling. It has been created by Furore (free to download with paid plans offering SLA level support) and is fully integrated with Simplifier.net. It is promoted as the official profile editor for HL7 FHIR.

Forge supports the following features:
* Create and edit FHIR Profiles
* Create and edit FHIR extension definitions
* Create and edit FHIR conformance packages (Introduced v0.9.2.15)
* Validate FHIR profiles
* Fetch and publish profiles from/to a FHIR server
* Fetch and publish profiles from/to a FHIR registry
* Define formal constraints
* Define slices
* Define value set bindings
* Define mappings
* Derived profiles (“profiles on profiles”)

<br><br>
## [HL7 FHIR Converter](http://hapifhir.io/doc_converter.html)
This tool is under development but it is intended to offer the following tools for structure definition conversions:
* Converting from DSTU2 to DSTU3
* Converting from DSTU2.1 to DSTU3
The tool is strictly targeted at a technical audience because it requires importing into a ‘Project Object Model’ or POM.
<br><br>
## [Postman](https://www.getpostman.com/)
<img src="images/support/postman.png" alt="Postman Screenshot" style="width:40%; float:right; margin-left:3%; margin-bottom:3%;">Postman is a tool to support the creation of APIs; available on MacOS, Windows, Linux or as a plug-in for the Chrome browser. While the basic version of Postman is free, there are ‘professional’ and ‘enterprise’ versions which come at a cost.

Postman provides an easy interface to interact with APIs over HTTP and provides the following features:

<em>Free Version</em>
* Downloadable Chrome, Mac, Linux & Windows App
* Saved History of API requests
<em>Professional</em>
* Unlimited Collections, Environments, Tests and Sharing
* Team Library of Collections
* Extensive team collaboration tools
* Extended documentation & monitoring features
* Customisable API Documentation
* API Monitoring for uptime, performance & accuracy
* Multi-timezone email support
<em>Enterprise Version (Beta)</em>
* Phone support & extended support options
* Additional invoicing & billing options
* Enterprise level security, encryption & governance

Postman is used in many tutorials as an easily accessible route to working with FHIR servers and testing operations without the need to create and code.
<br><br>
## [Simplifier.net](https://simplifier.net/)

<img src="images/support/simplifier.png" alt="Simplifier Screenshot" style="width:40%; float:right; margin-left:3%; margin-bottom:3%;">Simplifier.net is a FHIR registry, a website for managing, sharing and finding FHIR profiles and Implementation Guides.

The Simplifier.net FHIR registry supports the following functions:
* Uploading profiles
* Downloading profiles
* Finding profiles
* Viewing FHIR Conformance Resources
* Simplifier.net also offers functionality for management of FHIR Resources and collaboration within teams.

Simplifier.net distinguishes between free (personal) plans and paid plans. Anyone can find and download Resources in this Registry, with or without an account. Creating Resources requires an account. Paid plans are targeted at professional users and organisations.
The registry contains both projects and resources, and a quick scan can reveal hundreds of profiles that have been defined although they do range quite significantly in quality.
