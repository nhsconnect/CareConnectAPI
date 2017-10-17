---
title: Care Connect | Reference
keywords: development Reference
tags: [development,fhir,profiles]
sidebar: overview_sidebar
permalink: explore_reference.html
summary: "Developer Cheat Sheet shortcuts for the <br/>technical build of Care Connect API."
---

{% include custom/search.warnbanner.html %}

## 1. Care Connect Profiles: ##

| Profile | ValueSets |
| :--------- |:-------- |
| [CareConnect-AllergyIntolerance-1](STU3/constraints/CareConnect-AllergyIntolerance-1.xml) | [CareConnect-AllergyCertainty-1](STU3/valuesets/ValueSet-CareConnect-AllergyCertainty-1.xml) <br /> [CareConnect-AllergySeverity-1](STU3/valuesets/ValueSet-CareConnect-AllergySeverity-1.xml) |
| [CareConnect-Condition-1](STU3/constraints/CareConnect-Condition-1.xml) | [CareConnect-ConditionEpisodisity-1](STU3/valuesets/ValueSet-CareConnect-ConditionEpisodisity-1.xml) <br /> [CareConnect-ConditionCategory-1](STU3/valuesets/ValueSet-CareConnect-ConditionCategory-1.xml) <br /> [CareConnect-ConditionClinicalStatus-1](STU3/valuesets/ValueSet-CareConnect-ConditionClinicalStatus-1.xml) |
| [CareConnect-Encounter-1](STU3/constraints/CareConnect-Encounter-1.xml) | [CareConnect-EncounterType-1](STU3/valuesets/ValueSet-CareConnect-EncounterType-1.xml) |
| [CareConnect-Immunization-1](STU3/constraints/CareConnect-Immunization-1.xml) | |
| [CareConnect-Location-1](STU3/constraints/CareConnect-Location-1.xml) | |
| [CareConnect-Medication-1](STU3/constraints/CareConnect-Medication-1.xml) | |
| [CareConnect-MedicationFlag-1](STU3/constraints/CareConnect-MedicationFlag-1.xml) | [CareConnect-MedicationFlag-1](STU3/valuesets/ValueSet-CareConnect-MedicationFlag-1) |
| [CareConnect-MedicationRequest-1](STU3/constraints/CareConnect-MedicationRequest-1.xml) | [CareConnect-ManufacturedMaterialSnCT-1](STU3/valuesets/ValueSet-CareConnect-ManufacturedMaterialSnCT-1.xml) <br /> [CareConnect-MedicationDosageRoute-1](STU3/valuesets/ValueSet-CareConnect-MedicationDosageRoute-1.xml) <br /> [CareConnect-MedicationDosageMethod-1](STU3/valuesets/ValueSet-CareConnect-MedicationDosageMethod-1.xml) |
| [CareConnect-MedicationStatement-1](STU3/constraints/CareConnect-MedicationStatement-1.xml) | [CareConnect-ManufacturedMaterialSnCT-1](STU3/valuesets/ValueSet-CareConnect-ManufacturedMaterialSnCT-1.xml) <br /> [CareConnect-MedicationDosageRoute-1](STU3/valuesets/ValueSet-CareConnect-MedicationDosageRoute-1.xml) <br /> [CareConnect-MedicationDosageMethod-1](STU3/valuesets/ValueSet-CareConnect-MedicationDosageMethod-1.xml)  |
| [CareConnect-Observation-1](STU3/constraints/CareConnect-Observation-1.xml) | [CareConnect-AllergyCertainty-1](STU3/valuesets/ValueSet-CareConnect-AllergyCertainty-1.xml) <br /> [CareConnect-AllergySeverity-1](STU3/valuesets/ValueSet-CareConnect-AllergySeverity-1.xml) |
| [CareConnect-Patient-1](STU3/constraints/CareConnect-Patient-1.xml) | [CareConnect-RegistrationType-1](STU3/valuesets/ValueSet-CareConnect-RegistrationType-1.xml) <br /> [CareConnect-RegistrationStatus-1](STU3/valuesets/ValueSet-CareConnect-RegistrationStatus-1.xml) <br /> [CareConnect-CareConnect-ResidentialStatus-1](STU3/valuesets/ValueSet-CareConnect-ResidentialStatus-1.xml) <br /> [CareConnect-TreatmentCategory-1](STU3/valuesets/ValueSet-CareConnect-TreatmentCategory-1.xml) <br /> [CareConnect-HumanLanguage-1](STU3/valuesets/ValueSet-CareConnect-HumanLanguage-1.xml) <br /> [CareConnect-LanguageAbilityMode-1](STU3/valuesets/ValueSet-CareConnect-LanguageAbilityMode-1.xml) <br /> [CareConnect-LanguageAbilityProficiency-1](STU3/valuesets/ValueSet-CareConnect-LanguageAbilityProficiency-1.xml) <br /> [CareConnect-AdministrativeGender-1](STU3/valuesets/ValueSet-CareConnect-AdministrativeGender-1.xml) <br /> [CareConnect-MaritalStatus-1](STU3/valuesets/ValueSet-CareConnect-MaritalStatus-1.xml) <br />[CareConnect-PersonRelationshipType-1](STU3/valuesets/ValueSet-CareConnect-PersonRelationshipType-1.xml) <br /> |
| [CareConnect-Practitioner-1](STU3/constraints/CareConnect-Practitioner-1.xml) | [CareConnect-HumanLanguage-1](STU3/valuesets/ValueSet-CareConnect-HumanLanguage-1.xml) <br /> [CareConnect-LanguageAbilityMode-1](STU3/valuesets/ValueSet-CareConnect-LanguageAbilityMode-1.xml) <br /> [CareConnect-LanguageAbilityProficiency-1](STU3/valuesets/ValueSet-CareConnect-LanguageAbilityProficiency-1.xml) <br /> [CareConnect-AdministrativeGender-1](STU3/valuesets/ValueSet-CareConnect-AdministrativeGender-1.xml) <br /> [CareConnect-SDSJobRoleName-1](STU3/valuesets/ValueSet-CareConnect-SDSJobRoleName-1.xml) |
| [CareConnect-Procedure-1](STU3/constraints/CareConnect-Procedure-1.xml) | |


## 2. Identifiers ##

| identifier | URI | Comment |
|--------------------------------------------|----------|----|
| NHS Number | https://fhir.nhs.uk/Id/nhs-number | Patient - England and Wales |
| SDS User Id/ Practitioner Code | https://fhir.nhs.uk/Id/sds-user-id | Practitioner |
| SDS/ODS Organisation Code | https://fhir.nhs.uk/Id/ods-organization-code | Organization |
| SDS/ODS Site Code | https://fhir.nhs.uk/Id/ods-site-code | Location |

```
TODO: Insert a picture here to show the overall process (e.g. TLS, Setting Audit headers, etc)]
```
