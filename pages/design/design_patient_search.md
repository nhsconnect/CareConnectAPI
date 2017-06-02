---
title: Design | Patient Search (PDQ)
keywords: development
tags: [design,development]
sidebar: overview_sidebar
permalink: design_patient_search.html
summary: "How to use FHIR Patient resources to perform Patient Searches"
---

{% include custom/search.warnbanner.html %}

{% include custom/apilink.html content="[Patient](restfulapis_identification_patient.html)"  %}

{% include custom/ihelink.html content="[IHE Patient Demographic Query Mobile (IHE PDQM)](http://www.ihe.net/uploadedFiles/Documents/ITI/IHE_ITI_Suppl_PDQm.pdf)" %}

## 1. Overview ##

{% include custom/usecase.html content="A patient visits a emergency department for the first time. The nurse needs to register the patient; in
doing so, it is desired to record the patient’s demographic data in the emergency departments management
information system (ED MIS). The emergency department is connected to a hospital trust’s central
patient registry (typically the Patient Administration System (PAS) or Master Patient Index (MPI)). <br><br>  The nurse issues a patient query request to the central patient registry acting as a
Patient Demographics Supplier, with some basic patient demographics data as search criteria. In the returned patient list, she picks an appropriate record for the patient, including the hospital’s
Patient ID, to enter into the ED MIS. (Note the ED MIS uses a different Patient ID domain than that
of the central patient registry.)" %}

Most NHS trusts will typically have one central system  called the Patient Administration System (PAS) thats holds a master Patient registry of all patients who have had care with the trust. In order to reduce patient administration and improve data quality, all  other MIS within the trusts will be kept in sync with the central registry (PAS) via HL7v2 [messaging](http://www.enterpriseintegrationpatterns.com/patterns/messaging/Messaging.html). Alongside these messages will be patient encounter messages as shown in the diagram below:

{% include image.html
max-width="200px" file="IHE/Iti_pam_ip.jpg" alt="Patient Identity Feeds"
caption="Patient Identity Feeds" %}

Care Connect API uses a [RESTful](https://en.wikipedia.org/wiki/Representational_state_transfer) [resource API pattern](http://www.servicedesignpatterns.com/WebServiceAPIStyles/ResourceAPI) to provide access to the central Patient repository which is particularly suited:
* A health portal securely exposing demographics data to browser based plugins
* Medical devices which need to access patient demographic information
* Mobile devices used by physicians (example bedside eCharts) which need to establish
patient context by scanning a bracelet
* Web based EPR/EHR applications which wish to provide dynamic updates of patient
demographic information such as a non-postback search, additional demographic detail,
etc.
* Any low resource application which exposes patient demographic search functionality

## 2. Basic Patient Search ##

{% include image.html
max-width="200px" file="design/PDQ Actor Diagram.jpg" alt="Patient Search Actor Diagram"
caption="Patient Search Actor Diagram" %}

{% include image.html
max-width="200px" file="design/Basic Process Flow PDQm.jpg" alt="Basic Process Flow PDQ FHIR" caption="Basic Process Flow PDQ FHIR" %}

The patient search can use any of the search parameters defined in the [Patient](restfulapis_identification_patient.html) API. For example if the patient informs the nurse of their date of birth, first name (19th Mar 1998 Bernie Kanfeld) and surname the query would be.

```
GET /Patient?birthdate=1998-03-19
```

## 3. National (NHS) Patient Search ##

{% include image.html
max-width="200px" file="design/National PDQ Actor Diagram.jpg" alt="National NHS Patient Search Actor Diagram"
caption="National NHS Patient Search Actor Diagram" %}

{% include image.html
max-width="200px" file="design/National Basic Process Flow PDQm.jpg" alt="National NHS Process Flow PDQ FHIR" caption="National NHS Process Flow PDQ FHIR" %}

## 4. Patient Search Gateway ##

Patient searches using FHIR can be used with other patient search systems such NHS Spine Mini Services Provider (SMSP), HL7v2 Patient queries, etc. In this way the Patient Demographics
Consumer can choose the technology stack that best fits.
The Patient Demographics Supplier may act as a proxy to an existing HL7v2 PDQ, FHIR PDQ or ITK SMSP environment as shown in the diagrams below.

{% include image.html
max-width="200px" file="design/Gateway PDQ Actor Diagram.jpg" alt="National NHS Patient Search Actor Diagram"
caption=" Implementing PDQ FHIR as a gateway" %}


{% include image.html
max-width="200px" file="design/Gateway Process Flow PDQm.jpg" alt="Gateway Process Flow PDQ FHIR" caption="Sample PDQ FHIR gateway process flow" %}
