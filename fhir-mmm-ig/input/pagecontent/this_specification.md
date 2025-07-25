This IG defines a data source (i.e., Source) as well as a data consumer (i.e., Consumer). Sources may be traditional EHRs, aggregating systems such as HIEs, public health reporting agencies such as the National Vital Statistics Agency or state's Electronic Death Registration System (EDRS). 
Tooling used by Maternal Health Researchers to facilitate measure evaluation and data analysis are the expected Consumers.
Data consumers will select a Population definition defined in this guide as well as a reporting period.
The Source will provide a list of Patients (ie a census/roster of pregnant patients) for evaluation. The Source is expected to reference mothers and children via RelatedPerson and Patient.link. 

If a data soruce is unable to link Patients (mothers and children) according to the standard model, an association between the two sets of Patients (i.e., an association map between Mothers/potential Mothers and children) will be rquired. 
Consumers will query a data source for all known existing clinical information by Patient identifiers. If a Source's data are not natively available in FHIR format, ClinicalDocuments may also be queried and used as the mechanism to produce and convey Source data to Consumers.
Once target data from Sources has been aggregated and transformed into standard FHIR, an $evaluate-measure operation will be performed on the respective FHIR server [see SANER Computer Measure](https://build.fhir.org/ig/HL7/fhir-saner/transaction-4.html). 
The Output of $evaluate-measure operation will be a MeasureReport consisting of all Patient Mothers (1) found to be within the defined cohort population. 
Clinical information of the mothers determined to be within the measure population can subsequently be aggregated and provided alongside the Patient resource in the form of Supplemental Data. 
Records for the children of all mothers found to be in-cohort can be aggregated using the mother/child mapping list provided by the data source. 
Data consumers expect that mother/child relationship linkages will follow FHIR’s mother/child Linkage via RelatedPerson guidance. 


### Dataflows
<b><i>Consumer initiates dataflow through selection of Measure:</i></b>
1.	Retrieve the current research measure population Bundle (example provided in this guide) from a pre-defined measure definition server. The Bundle contains the FHIR Measure resource, the measure Library containing the applicable CQL defining the measure population, any applicable FHIR Libraries, and all ValueSets needed for measure calculation. 
2.	Place the research measure population Bundle onto a Measure Evaluation FHIR server
3.	Retrieve of all available clinical information for the provided census of Patient identifiers from a pre-defined FHIR data source
Note: if Source data is available in C-CDA format, an XDS Document Query/Retrieve can serve as the foundation document to be transformed into appropriate FHIR resources
4.	Place of all available clinical information onto the Measure Evaluation FHIR Server in step 2
5.	Execute $evaluate-measure FHIR operation on the Measure Evaluation Server in step 2
6.	Patients found in the cohort are aggregated by Identifiers of known Children (Patients) for the in-cohort mothers (from a list provided by the Source).
7.	Aggregate of all clinical information related to the children from step 6
8.	Compile of a MeasureReport Bundle for all FHIR data contained in steps 5-7

### Must Support and Missing Data
Systems claiming to conform to a profile SHALL support the elements in a profile as defined below. This guide adopts the following definitions of MustSupport for all direct transactions between the data source systems and data consumer systems.

<b>Data Source Systems</b>
*	The data source system SHALL be capable of returning elements defined in the profiles that have a MustSupport flag and SHALL populate all elements with a MustSupport flag if the information exists.
*	In situations where information on a particular data element is not present, the data source system SHALL NOT include the data element in the resource instance if the cardinality is 0..n.
*	If the information does not exist and the cardinality of the element is >= 1..*, the data source system SHALL use the dataAbsentReason extension where it is defined. 

<b><i>Note:</i></b> Populating the element with the value set absent reason or using the dataAbsent Reason SHOULD be handled by the data source system and not require provider action.

<b>Data Consumer Systems</b> 
*	data consumer systems SHALL be capable of processing resource instances containing required and allowed data elements without generating an error or causing the application to fail.
*	data consumer systems SHOULD be capable of processing (display, store, etc.) the data elements based on the utility of the specific element to the receiver.
*	When receiving a transaction from a data source system, the data consumer system SHALL interpret missing data elements within resource instances as data not present in the data source system.
*	data consumer systems SHALL be able to process resource instances containing data elements asserting missing information without generating an error or causing the application to fail.

### Search
This specification uses the same Search Syntax rule as [US Core](https://www.hl7.org/fhir/us/core/searchparameters.html). This guide does not define any additional Search Parameters.

### Privacy and Security
The methods by which data sources and data consumers agree upon the scope of clinical information to be exchanged for maternal health research should occur prior to implementation of this guide. Both data sources and data consumers must consider all applicable laws, policies, and organizational.
 
<b><i>Note:</i></b> The scope of information exchange needed by maternal health researchers may include de-identification for and identity management; while both concepts of de-identification and identity management methods are outside of the scope of this guide, they should be considered and agreed upon between data sources and consumers prior to implementation.