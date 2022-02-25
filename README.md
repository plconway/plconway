# CAMPFHIR Field Mapping Documentation

This document serves as a guide the the field mapping logic for mapping PCORnet Common Data Model (CDM) version 6.0 to FHIR version 4.0.

Currently, CAMPFHIR supports value set mapping for 44 PCORnet CDM fields. Of those, 7 are codeable concepts. The rest take the raw PCORnet value and map it to the corresponding CAMPFHIR column. This document explains the process taken to reach the conclusion that they are corresponding concepts. This

## PCORNET CDM

The current specifications for the PCORnet CDM are located [here](https://pcornet.org/data/).

## FHIR Resources

The list of resources available in the current release of FHIR are located [here](https://www.hl7.org/fhir/resourcelist.html).

## Mapping Logic from PCORnet CDM to FHIR Resources

| PCORnet Table Name | PCORNET Field Name | FHIR PATH | CAMPFHIR Column | Raw or Codeable | Logic |
|--------------------|--------------------|-----------|-----------------|-----------------|-------|
|Demographic         |PATID | Patient.identifier ||Raw | Patient ID serves as an identifer for the patient in the record. |
|Demographic         |BIRTH_DATE | Patient.birthDate ||Raw | Birthdate of the patient is recognized in both. |
|Demographic         |SEX | Patient.gender ||Codable |PCORnet accounts for Sex assigned at birth, current gender identity, and sexual orientation. FHIR only accounts for 'gender for record-keeping purposes'. CAMPFHIR pulls from DEMOGRAPHIC_SEX for simplicity purposes. |
|Demographic         |HISPANIC |||Codable |This is part of a FHIR Ethnicity extension.|
|Demographic         |RACE |||Codable | This is part of a FHIR Ethnicity extension. |
|Demographic         |PAT_PREF_LANGUAGE_SPOKEN | Patient.communication.language ||Codable | Preferred language of the patient is recognized in both PCORnet CDM and FHIR. |
|Encounter           |ENCOUNTERID | Encounter.idenftifier / Procedure.encounter.refrence ||Raw | Encounter is referenced throughout the FHIR specifications.|
|Encounter           |PATID | Encounter.subject.reference ||Raw | Within an encounter resource, the identifier of the patient is recorded. |
|Encounter           |ADMIT_DATE | Encounter.participant.period.start||Codable | FHIR stores the 'period of time during the encounter that the participant participated'.  |
|Encounter           |DISCHARGE_DATE | Encounter.participant.period.end ||Codable | See above.|
|Encounter           |ENC_TYPE | Encounter.class ||Codeable |PCORnet has types of encounters (ambulatory, emergency department, etc.). FHIR treats these as a 'Class' of encounter. The vocabulary is similar. |
|Encounter           |FACILITYID | Encounter.serviceprovider.reference||Raw |Reference to the facility where the encounter took place. |
|Encounter           |DISCHARGE_STATUS | Encounter.hospitalization.dischargedisposition ||Codable |Type of location where the patient was discharged.|
|Diagnosis           |DIAGNOSISID      | Condition.identifier.value||Raw |ID of the condition. |
|Diagnosis           |PATID | Condidtion.subject||Raw |Reference to the patient who has the condition. |
|Diagnosis           |ENCOUNTERID | Encounter.hospitalization.dischargedisposition ||Codable |Type of location where the patient was discharged.|
|Diagnosis           |ADMI_DATE | Encounter.hospitalization.dischargedisposition ||Codable |Type of location where the patient was discharged.|
|Diagnosis           |PROVIDERID | Encounter.hospitalization.dischargedisposition ||Codable |Type of location where the patient was discharged.|
|Diagnosis           |DX | Encounter.hospitalization.dischargedisposition ||Codable |Type of location where the patient was discharged.|
|Diagnosis           |DX_TYPE | Encounter.hospitalization.dischargedisposition ||Codable |Type of location where the patient was discharged.|
|Diagnosis           |RAW_DX | Encounter.hospitalization.dischargedisposition ||Codable |Type of location where the patient was discharged.|


## Notes
- FHIR defines a condition as: 'A clinical condition, problem, diagnosis, or other event, situation, issue, or clinical concept that has risen to a level of concern'. Therefore, diagnosis values from PCORnet map to encounters.
