---
title: Design | Patient Search
keywords: development
tags: [design,development]
sidebar: overview_sidebar
permalink: design_patient_search.html
summary: "How to use FHIR Patient resources to perform Patient Searches"
---

{% include custom/search.warnbanner.html %}

{% include custom/apilink.html content="[Patient](restfulapis_identification_patient.html) [Practitioner](restfulapis_identification_practitoner.html)" %}

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

Care Connect API uses a [RESTful](https://en.wikipedia.org/wiki/Representational_state_transfer) [resource API pattern](http://www.servicedesignpatterns.com/WebServiceAPIStyles/ResourceAPI) to provide access to the central Patient repository which is particularly suited to mobile applications and organisations not wanting multiple copies of potentially sensitive patient data.  

## 2. Basic Patient Search ##

{% include image.html
max-width="200px" file="design/PDQ Actor Diagram.jpg" alt="Patient Search Actor Diagram"
caption="Patient Search Actor Diagram" %}

{% include image.html
max-width="200px" file="design/Basic Process Flow PDQm.jpg" alt="Basic Process Flow PDQm" caption="Basic Process Flow PDQm" %}

## 3. National (NHS) Patient Search ##

## 4. Federated Patient Search ##
