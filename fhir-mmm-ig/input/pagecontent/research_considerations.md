### Implementation Considerations
This guide is intended as a specification for implementers of tooling to support researchers working to analyze clinical information related to maternal and child health. Implementing systems of this specification may likely have several existing available tools to store, transport, and transform clinical information. This guide is intended to allow implementers to use existing tooling and empower participation in sharing and analyzing maternal and child clinical information in scope of defined populations.

### Master Patient Index
A Master Patient Index (MPI) is a system that uses a set of rules (policies) to assign unique patient identifiers (Patient IDs) if it determines two or more sets of clinical data pertain to the same patient. For example, if two patient records show care was received in different care settings and they have demographic records with identical first and last name, gender, birth date, and contact information, an MPI system rule may conclude that these patient records pertain to the same person and would assign both a single MPI ID. However, in a scenario where Patient 3 and 4 have only the same first name, gender, birth date, and some contact information, one MPI system may determine these are different Patients, while another MPI system may determine these are the same Patient who might have gotten married and changed last name and address in between care delivery settings. 

Use of an MPI system is a common function of health information exchange (HIE) networks. It could also be applicable to other inter-organization or multi-care-delivery areas, such as an insurance organization. 

Maternal/child patient populations are crucial to manage across multiple source clinical information systems (i.e., EHRs). This IG will leverage current and developing standards to link mother to child data, including those that accommodate for entities using a Master Patient Index (MPI) system, which is a common method in health care for assigning and managing unique individuals across various source systems. Access to data from a clinical aggregator system that has an MPI will allow researchers to potentially investigate the clinical information associated with mothers and their children across a broader geographical dataset and over a longer period. 

### HL7 Patient Matching
[The Interoperable Digital Identity and Patient Matching Capabilities project](https://confluence.hl7.org/display/PA/Interoperable+Digital+Identity+and+Patient+Matching+Capabilities) plans to develop artifacts to profile the Patient match operation for use across organizations, incorporating elements of identity verification and the use of digital identities in workflows. Such profiles may be useful to researchers to match pregnancy-related information between systems that are in-scope for a given study and a given MPI system. 

If research studies do not require the researcher to manage identities between systems or researchers collect only de-identified clinical data, patient matching and MPIs may not be needed for aggregation of clinical data for research. 

<b><i>Note</i></b>: The Patient Matching project assumes that all entities (requestor and requesting) are abiding by all federal, state, and jurisdictional laws/policies and have obtained any additional necessary agreements that allow for the disclosure of clinical information following the matching of patient records.

### Maternal-Child Linkage
FHIR’s Patient resource provides a foundation for the appropriate method and structure for linking mother and child information. Maternal/child record linkage could occur before the data leaves the EHR system or after the researcher receives data from multiple sources. This section describes how to structure the data in an EHR systems to relate a mother and child before the information is sent to the researcher and not about how a researcher would associate the mother and child retrospectively. 

The appropriate structure to link a mother with her child through use of Patient/RelatedPerson referencing is defined in FHIR’s base [Patient](http://hl7.org/fhir/2018Sep/patient.html#maternity) resource. It is reinforced and exemplified through the [US Vital Records Common Profiles Library FHIR Implementation Guide](http://hl7.org/fhir/us/vr-common-library/STU1). This guide relies on this existing linkage structure to accurately provide relevant data to researchers. 

The RelatedPerson.relationship code diagram shows ‘MTH’ for a general ‘mother’. However, more specific relationship types are allowable within Vital Records Common Profiles: RelatedPerson – Mother profile. In short, the mother is represented twice, first as a Patient resource with a link to another representation of herself as a RelatedPerson resource, which then points to the Child as a Patient resource.

<table><tr><td><img src="mother-child-linkage.png"/></td></tr></table>

FHIR outlines the use of [three linkage techniques](https://www.hl7.org/fhir/patient.html#maternity): 
*	Use of Patient/RelatedPerson. During a pregnancy within a given EHR system (i.e., an Ob/Gyn EHR), the mother’s record exists associated with a Patient record (i.e., Patient – Mother). Depending on the clinical setting and timing, a new Patient record for the child will be created (i.e., Patient – Child). At this point, a linkage resource between the two Patient resources should also be created: RelatedPerson. The RelatedPerson resource will convey the mother’s relationship to the newborn child through a .name element representing the Mother’s name (and possibly the mother’s contact information and date of birth), a reference to the Child Patient resource, and a .relationship code of MTH (for Mother), NMTH (for Natural Mother) or possibly GESTM (for Gestational Mother).
*	Use of Encounter.partOf. This linkage structure is expected to be found within the EHR system of a delivery setting. At the start of a delivery encounter, an Encounter resource conforming to the Encounter – Maternity profile is created. When the delivery is documented, a new Encounter is created to represent the newborn’s encounter conforming to the Encounter – Birth profile. This Encounter – Birth uses the .partOf element within Encounter – Birth to reference the Encounter – Maternal Encounter.
*	Use of FamilyMemberHistory. FHIR defines a FamilyMemberHistory resource for systems to capture and share pertinent information related to a given patient’s family, such as a family member’s relationship to the patient, when the family member was born, gender, and known diagnoses of the family member.


### De-identification for Research
Clinical data can be used for research in accordance with the many applicable laws, regulations, and public and private policies that stipulate appropriate/authorized use. A key consideration of appropriate use of clinical information for research depends on whether the clinical information in question is identifiable or de-identified. 

At the federal level in the US, [HIPAA's Research section](https://www.hhs.gov/hipaa/for-professionals/special-topics/research/index.html) provides a foundation upon which state, local and private/organization rules can be built and the [Revised Common Rule](https://www.hhs.gov/ohrp/regulations-and-policy/regulations/finalized-revisions-common-rule/index.html) has clear statutes on how health research should be conducted. This specification does not provide any additional guidance on matters of obtaining consent or the appropriate use of clinical information for research and assumes matters of consent or adherence to [Health Insurance Portability and Accountability Act of 1996 (HIPAA)](https://www.cdc.gov/phlp/publications/topic/hipaa.html) and Common Rule regulations are navigated by the institutions implementing this guide for research purposes. 

While this IG does not provide guidance on the use of clinical information for the purposes of clinical trials, some of the components/processes in this guide may be applicable for a clinical trial facilitator.


### Expected Timing / Research Frequency
Researchers may want to query for maternal and associated child clinical information once or several times over an extended period. Researchers may also desire to query for existing information spanning backwards over any length of specified time. This guide does not specify timing considerations beyond what is supported by the [Clinical Reasoning Module](http://hl7.org/fhir/r4/clinicalreasoning-module.html). 

Note: When the Clinical Quality Framework(CQF) is used in Quality Reporting, a Measurement Period must be specified for accurate reporting; this Measurement Period should be a key consideration both when defining measures and when researchers are executing said measure logic.

### Relationship to other Standards

Several existing HL7 FHIR, C-CDA, and Integrating the Healthcare Enterprise (IHE) standards have been published that specify perinatal clinical information. This guide specifies how maternal health researchers can quantify clinical information related to this population which may exist, or be transmitted between systems, in accordance with any of the below standards:

[US Core FHIR IG](https://www.hl7.org/fhir/us/core/)

[Vital Records Common Profiles Library](http://hl7.org/fhir/us/vrdr/)

[Vital Records Birth and Fetal Death Reporting FHIR IG](https://build.fhir.org/ig/HL7/fhir-bfdr/)

[Vital Records Mortality and Morbidity Reporting FHIR IG](http://hl7.org/fhir/us/vrdr/)

[CDA Supplemental Pregnancy Templates for C-CDA](https://www.hl7.org/implement/standards/product_brief.cfm?product_id=494)

[Birth Reporting Domain Analysis Model (DAM - extension of VR DAM)](https://www.hl7.org/implement/standards/product_brief.cfm?product_id=559)

[Birth Defects Domain Analysis Model and FHIR IG](https://confluence.hl7.org/display/PHWG/Birth+Defects+DAM+and+FHIR+IG)

[Occupational Data for Health](http://hl7.org/fhir/us/odh/)