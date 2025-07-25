### Clinical Reasoning
[FHIR's Clinical Reasoning module](http://www.hl7.org/fhir/clinicalreasoning-module.html) describes in general what is covered under this framework. This guide relies on the framework’s measure model to define peri-natal populations of interest (POI). From this POI, measure cohort definitions will be used to define the POI for a given research question. With a target population identified, clinical information related to a group of patients found to be in-scope for a given population of patients can be aggregated.

### Defining Measure Populations
Two cohort populations are in scope for the initial release of this guide. These measure definitions are expressed in CQL and are found base64 encoded within Library.content examples. Future use cases will each warrant distinct CQL expressions, associated terminologies (ValueSets), and measure definitions. 

<b><i>Note:</i></b> Not all future research study populations of interest will necessitate the updating of this published FHIR guide.

### Architecture and Implementation
These guides are both built upon FHIR’s Clinical Quality Framework (CQF) and therefore share many design patterns. SANER’s representation of various CQF components apply to this guide. Specifically, SANER’s Measure Definition server, and Compute Measure Actors and roles apply to systems implementing all or components of this guide. Where SANER is focused on reporting to a public health agency (PHA), this guide is analogously focused on reporting to a maternal health researcher. 

[See: Security, Architecture and Implementation from the SANER guide](http://hl7.org/fhir/uv/saner/).