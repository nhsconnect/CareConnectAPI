---
title: Reference Profiles
keywords: development deliverables
tags: [development]
sidebar: overview_sidebar
permalink: development_deliverables.html
summary: "Developer Cheat Sheet shortcuts for the <br/>technical build of Care Connect API."
---

```
TODO: Insert a picture here to show the overall process (e.g. TLS, Setting Audit headers, etc)]
```

# Care Connect Profiles:

| Profile | ValueSets | 
| :--------- |:-------- |
| [CareConnect-AllergyIntolerance-1](StructureDefinitions/CareConnect-AllergyIntolerance-1.xml) | [CareConnect-AllergyCertainty-1](ValueSets/CareConnect-AllergyCertainty-1.xml) <br /> [CareConnect-AllergySeverity-1](ValueSets/CareConnect-AllergySeverity-1.xml) | 
| [CareConnect-Condition-1](StructureDefinitions/CareConnect-Condition-1.xml) | [CareConnect-ConditionEpisodisity-1](ValueSets/CareConnect-ConditionEpisodisity-1.xml) <br /> [CareConnect-ConditionCategory-1](ValueSets/CareConnect-ConditionCategory-1.xml) <br /> [CareConnect-ConditionClinicalStatus-1](ValueSets/CareConnect-ConditionClinicalStatus-1.xml) | 
| [CareConnect-Encounter-1](StructureDefinitions/CareConnect-Encounter-1.xml) | [CareConnect-EncounterType-1](ValueSets/CareConnect-EncounterType-1.xml) | 
| [CareConnect-Immunization-1](StructureDefinitions/CareConnect-Immunization-1.xml) | | 
| [CareConnect-Location-1](StructureDefinitions/CareConnect-Location-1.xml) | | 
| [CareConnect-Medication-1](StructureDefinitions/CareConnect-Medication-1.xml) | | 
| [CareConnect-MedicationFlag-1](StructureDefinitions/CareConnect-MedicationFlag-1.xml) | [CareConnect-MedicationFlag-1](ValueSets/CareConnect-MedicationFlag-1) | 
| [CareConnect-MedicationOrder-1](StructureDefinitions/CareConnect-MedicationOrder-1.xml) | [CareConnect-ManufacturedMaterialSnCT-1](ValueSets/CareConnect-ManufacturedMaterialSnCT-1.xml) <br /> [CareConnect-MedicationDosageRoute-1](ValueSets/CareConnect-MedicationDosageRoute-1.xml) <br /> [CareConnect-MedicationDosageMethod-1](ValueSets/CareConnect-MedicationDosageMethod-1.xml) | 
| [CareConnect-MedicationStatement-1](StructureDefinitions/CareConnect-MedicationStatement-1.xml) | [CareConnect-ManufacturedMaterialSnCT-1](ValueSets/CareConnect-ManufacturedMaterialSnCT-1.xml) <br /> [CareConnect-MedicationDosageRoute-1](ValueSets/CareConnect-MedicationDosageRoute-1.xml) <br /> [CareConnect-MedicationDosageMethod-1](ValueSets/CareConnect-MedicationDosageMethod-1.xml)  | 
| [CareConnect-Observation-1](StructureDefinitions/CareConnect-Observation-1.xml) | [CareConnect-AllergyCertainty-1](ValueSets/CareConnect-AllergyCertainty-1.xml) <br /> [CareConnect-AllergySeverity-1](ValueSets/CareConnect-AllergySeverity-1.xml) | 
| [CareConnect-Patient-1](StructureDefinitions/CareConnect-Patient-1.xml) | [CareConnect-RegistrationType-1](ValueSets/CareConnect-RegistrationType-1.xml) <br /> [CareConnect-RegistrationStatus-1](ValueSets/CareConnect-RegistrationStatus-1.xml) <br /> [CareConnect-CareConnect-ResidentialStatus-1](ValueSets/CareConnect-ResidentialStatus-1.xml) <br /> [CareConnect-TreatmentCategory-1](ValueSets/CareConnect-TreatmentCategory-1.xml) <br /> [CareConnect-HumanLanguage-1](ValueSets/CareConnect-HumanLanguage-1.xml) <br /> [CareConnect-LanguageAbilityMode-1](ValueSets/CareConnect-LanguageAbilityMode-1.xml) <br /> [CareConnect-LanguageAbilityProficiency-1](ValueSets/CareConnect-LanguageAbilityProficiency-1.xml) <br /> [CareConnect-AdministrativeGender-1](ValueSets/CareConnect-AdministrativeGender-1.xml) <br /> [CareConnect-MaritalStatus-1](ValueSets/CareConnect-MaritalStatus-1.xml) <br />[CareConnect-PersonRelationshipType-1](ValueSets/CareConnect-PersonRelationshipType-1.xml) <br /> | 
| [CareConnect-Practitioner-1](StructureDefinitions/CareConnect-Practitioner-1.xml) | [CareConnect-HumanLanguage-1](ValueSets/CareConnect-HumanLanguage-1.xml) <br /> [CareConnect-LanguageAbilityMode-1](ValueSets/CareConnect-LanguageAbilityMode-1.xml) <br /> [CareConnect-LanguageAbilityProficiency-1](ValueSets/CareConnect-LanguageAbilityProficiency-1.xml) <br /> [CareConnect-AdministrativeGender-1](ValueSets/CareConnect-AdministrativeGender-1.xml) <br /> [CareConnect-SDSJobRoleName-1](ValueSets/CareConnect-SDSJobRoleName-1.xml) | 
| [CareConnect-Procedure-1](StructureDefinitions/CareConnect-Procedure-1.xml) | | 


# Audit Profiles:

| Profile | ValueSets |
| :--------- |:------- |
| [Audit-Patient-1](http://fhir-test.nhs.uk/StructureDefinition/Audit-Patient-1) | Patient ([json](Audit/Examples/Patient.json)/[xml](Audit/Examples/Patient.xml)) |  | 
| [Audit-Device-1](http://fhir-test.nhs.uk/StructureDefinition/Audit-Device-1) | Device ([json](Audit/Examples/Device.json)/[xml](Audit/Examples/Device.xml)) | [device-type-codes-snct-1](http://fhir-test.nhs.uk/ValueSet/device-type-codes-snct-1) | |
| [Audit-Organization-1](http://fhir-test.nhs.uk/StructureDefinition/Audit-Organization-1) | Organisation ([json](Audit/Examples/Organization.json)/[xml](Audit/Examples/Organization.xml)) | | |
| [Audit-Practitioner-1](http://fhir-test.nhs.uk/StructureDefinition/Audit-Practitioner-1) | Practitioner ([json](Audit/Examples/Practitioner.json)/[xml](Audit/Examples/Practitioner.xml)) | | |

