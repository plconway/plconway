PCORnet_Table|PCORnet_Field|FHIR_PATH|Raw_or_Codable|Logic
-|-|-|-|-
Demographic|PATID|Patient.identifier|Raw|Patient ID serves as an identifer for the patient in the record.
Demographic|BIRTH_DATE|Patient.birthDate|Raw|Birthdate of the patient is recognized in both.
Demographic|SEX|Patient.gender|Codable|"PCORnet accounts for Sex assigned at birth, current gender identity, and sexual orientation. FHIR only accounts for ""gender for record-keeping purposes"". CAMPFHIR pulls from DEMOGRAPHIC_SEX for simplicity purposes."
Demographic|HISPANIC||Codable|This is part of a FHIR Ethnicity extension.
Demographic|RACE||Codable|This is part of a FHIR Ethnicity extension.
Demographic|PAT_PREF_LANGUAGE_SPOKEN|Patient.communication.language|Codable|Preferred language of the patient is recognized in both PCORnet CDM and FHIR.
Encounter|ENCOUNTERID|Encounter.idenftifier / Procedure.encounter.refrence|Raw|Encounter is referenced throughout the FHIR specifications.
Encounter|PATID|Encounter.subject.reference|Raw|Within an encounter resource, the identifier of the patient is recorded.
Encounter|ADMIT_DATE|Encounter.participant.period.start|Codable|"FHIR stores the ""period of time during the encounter that the participant participated""."
Encounter|DISCHARGE_DATE|Encounter.participant.period.end|Codable|See above.
Encounter|ENC_TYPE|Encounter.class|Codeable|"PCORnet has types of encounters (ambulatory, emergency department, etc.). FHIR treats these as a ""Class"" of encounter. The vocabulary is similar."
Encounter|FACILITYID|Encounter.serviceprovider.reference|Raw|Reference to the facility where the encounter took place.
Encounter|DISCHARGE_STATUS|Encounter.hospitalization.dischargedisposition|Codable|Type of location where the patient was discharged.
Diagnosis|DIAGNOSISID|Condition.identifier.value|Raw|ID of the condition.
Diagnosis|PATID|Condidtion.subject|Raw|Reference to the patient who has the condition.
Diagnosis|ENCOUNTERID|Condition.encounter|Raw|Encounter where the diagnosis of condition happened.
Diagnosis|PROVIDERID|Condition.asserter|Raw|Reference to the person who asserted the condition.
Diagnosis|DX|Condition.code|Raw|The medical code of the diagnosis/condition.
Diagnosis|DX_TYPE|Condition.code|Codable|The coding system that accompanies the medical code.
Diagnosis|RAW_DX|Condition.note|Raw|"PCORnet stores textual descriptions of diagnosis in the raw field. FHIR has space for a ""note"" for additional information."
Procedures|PROCEDURESID|Procedure.identifier|Raw|The identifier of the proceudre that took place.
Procedures|PATID|Procedure.subject|Raw|Reference to the person who recieved the procedure.
Procedures|ENCOUNTERID|Procedure.encounter|Raw|Reference to the encounter in which the procedure took place.
Procedures|ENC_TYPE|Procedure.category|Raw|"PCORnet has types of encounters (ambulatory, emergency department, etc.). FHIR treats these as a ""Class"" of encounter. The vocabulary is similar."
Procedures|ADMIT_DATE|Procedure.performeddatetime|Raw|Date of the encounter in which the procedure took place.
Procedures|PROVIDERID|Procedure.performer.actor|Raw|Reference to the provider who performed the procedure.
Procedures|PX|Procedure.code|Raw|The medical code corresponding to the procedure.
Procedures|PX_TYPE|Procedure.code|The coding systems that accompanies the medical code.|
Condition|CONDITIONID|Condition.identifier|Raw|ID of the condition record.
Condition|PATID|Condition.subject|Raw|Reference to the patient who has the condition.
Condition|ENCOUNTERID|Condition.encounter|Raw|Reference to the encounter where the condition was recorded.
Condition|REPORT_DATE|Condition.recordedDate|Raw|Date that the condition was recorded.
Condition|RESOLVE_DATE|Condition.abatementDateTime|Raw|Date that the condition was resolved.
Condition|ONSET_DATE|Condition.onsetDateTime|Raw|Date that the condition started for the patient.
Condition|CONDITION_STATUS|Condition.clinicalStatus|Codable|Current status of the condition.
Condition|CONDITION|Condition.code|Raw|The medical code corresponding to the condition.
Condition|CONDITION_TYPE|Condition.code|Codable|the coding system that accompanies the condition.
Condition|RAW_CONDITION|Condition.note|Raw|PCORnet uses this to store the textual description of the condition.
Death|DEATH_DATE|Patient.deceasedDateTime|Raw|Recorded date of patient death.
