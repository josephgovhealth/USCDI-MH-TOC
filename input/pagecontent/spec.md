

|Data Class|Postpartum TOC Data Element|FHIR Profile|FHIR Profile Data Element|
|---|---|---|---|
|Allergies and Intolerances|Substance (Drug Class)||AllergyIntolerance.category|
|Allergies and Intolerances|Substance (Medication)||AllergyIntolerance.category|
|Allergies and Intolerances|Substance (Non-Medication)||AllergyIntolerance.category|
|Care Team Member(s)|Care Team Member Name||CareTeam.participant|
|Care Team Member(s)|Care Team Member Role||CareTeam.participant.role|
|Clinical Notes|Consultation Note|||
|Clinical Notes|Discharge Summary Note||DocumentReference.type|
|Clinical Notes|History & Physical||DocumentReference.type|
|Clinical Notes|Procedure Note|||
|Clinical Notes|Progress Note||DocumentReference.code|
|Clinical Tests|Clinical Test||DocumentReference.type|
|Clinical Tests|Clinical Test Result/Report||DocumentReference.type|
|Diagnostic Imaging|Diagnostic Imaging Report||Observation.code|
|Diagnostic Imaging|Diagnostic Imaging Test||DiagnosticReport.result|
|Encounter Information|Encounter Diagnosis||Condition.code|
|Encounter Information|Encounter Location||Encounter.location|
|Encounter Information|Encounter Type||Encounter.type|
|Facility Information|Facility Name||Organization.name|
|Facility Information|Facility Type||Organization.identifier.system|
|Family Health History|Family Health History||FamilyMemberHistory|
|Health Status Assessment|Alcohol Use|[US Core Observation Screening Assessment Profile](http://hl7.org/fhir/us/core/StructureDefinition/us-core-observation-screening-assessment)|observation.code|
|Health Status Assessments|Clinical Risk Assessment Results|||
|Health Status Assessments|Mental / Cognitive Status||Observation.code|
|Health Status Assessment|Pregnancy Status|[US Core Observation Pregnancy Status Profile](http://hl7.org/fhir/us/core/StructureDefinition/us-core-observation-pregnancystatus)|observation.code|
|Health Status Assessments|Smoking Status||Observation.code|
|Health Status Assessments|Substance Use||Observation.value[x]|
|Immunizations|Immunization Status||Immunization.status|
|Immunizations|Immunizations||Immunization.vaccinecode|
|Immunizations|Reason Immunization Not Performed||Immunization.statusreason|
|Laboratory|Result Reference Range||Observation.referenceRange|
|Laboratory|Result Status||DiagnosticReport.status|
|Laboratory|Specimen Identifier||Specimen.identifier|
|Laboratory|Specimen Source Site||Specimen.collection.bodySite|
|Laboratory|Specimen Type||Specimen.type|
|Laboratory|Tests||DiagnosticReport.code|
|Laboratory|Values/Results||DiagnosticReport.result|
|Medications|Discharge Medications|||
|Medications|Dose||MedicationRequest.dosageInstruction|
|Medications|Dose Unit of Measure||MedicationRequest.dosageInstruction|
|Medications|Medications||MedicationRequest.medication[x]|
|Newborn's Delivery Information|APGAR Score||Obvervation.code|
|Newborn's Delivery Information|Birth Weight||Observation.component.?|
|Newborn's Delivery Information|Multiple Birth Order||patient.multiplebirth[x]  
patient.multipleBirthInteger|
|Patient Demographics|Current Address||Patient.address|
|Patient Demographics|Date of Birth||Patient.birthDate|
|Patient Demographics|Email Address||Patient.telecom|
|Patient Demographics|Ethnicity||Extension.extension:ombCategory.value[x]|
|Patient Demographics|First Name||Patient.name|
|Patient Demographics|Gender Identity||Patient.gender|
|Patient Demographics|Last Name||Patient.name|
|Patient Demographics|Middle Name  
(Including middle initial)||Patient.name|
|Patient Demographics|Name Suffix||Patient.name|
|Patient Demographics|Phone Number||Patient.telecom|
|Patient Demographics|Phone Number Type||Patient.telecom|
|Patient Demographics|Preferred Language||Patient.communication|
|Patient Demographics|Previous Address||Patient.address|
|Patient Demographics|Previous Name||Patient.name|
|Patient Demographics|Race||Extension.extension:ombCategory.value[x]|
|Patient Demographics|Related Person's Name||RelatedPerson.name|
|Patient Demographics|Relationship Type||RelatedPerson.relationship|
|Patient Demographics|Sex||Patient.gender|
|Patient Demographics|Tribal Affiliation||Patient.extension:tribalAffiliation|
|Patient Summary and Plan|Assessment and Plan of Treatment||CarePlan.text|
|Pregnancy Information|Estimated Date of Delivery||Observation.code|
|Pregnancy Information|Gestational Age||Obversation.code|
|Pregnancy Information|Last Menstrual Period (LMP)||Observation.code|
|Pregnancy Information|Pregnancy Outcome||Observation.code|
|Problems|Date of Diagnosis||Condition.onset[x]|
|Problems|Date of Resolution||Condition.abatement[x]|
|Problems|Problems||Condition.code|
|Problems|SDOH Problems/Health Concerns||Condition.code|
|Procedures|Performance Time||Procedure.performed[x]|
|Procedures|Procedure Status||Procedure.status|
|Procedures|Procedures||Procedure.code|
|Procedures|Reason for Referral||ServiceRequest.reasonReference|
|Provenance|Author Organization||Provenance.agent|
|Provenance|Author Time Stamp||Provenance.occured[x]|
|Vital Signs|Average Blood Pressure||Observation.?|
|Vital Signs|BMI||Observation.code|
|Vital Signs|Body Height||Observation.code|
|Vital Signs|Body Temperature||Observation.code|
|Vital Signs|Body Weight||Observation.code|
|Vital Signs|Diastolic Blood Pressure||Observation.component:diastolic.code|
|Vital Signs|Head Occipital-frontal Circumference Percentile (Birth - 36 Months)||Observation.code|
|Vital Signs|Heart Rate||Observation.code|
|Vital Signs|Inhaled Oxygen Concentration||Observation.code|
|Vital Signs|Pulse Oximetry||Observation.component:systolic.code|
|Vital Signs|Respiratory Rate||Observation.code|
|Vital Signs|Systolic Blood Pressure||Observation.component:systolic.code|
|Vital Signs|Weight-for-length Percentile (Birth - 36 Months)||Observation.code|
|Name of class|Data Element Name||FHIR Resource Mapping|
|Name of class|Data Element Name||FHIR Resource Mapping|
|Name of class|Data Element Name||FHIR Resource Mapping|
|Name of class|Data Element Name||FHIR Resource Mapping|
|Name of class|Data Element Name||FHIR Resource Mapping|
|Name of class|Data Element Name||FHIR Resource Mapping|
|Name of class|Data Element Name||FHIR Resource Mapping|
