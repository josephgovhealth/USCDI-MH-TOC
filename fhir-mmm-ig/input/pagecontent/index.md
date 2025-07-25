### Overview

### Scope
The Longitudinal Maternal & Child Health Information for Research FHIR R4 implementation guide (IG) defines a framework to enable maternal health researchers to aggregate, calculate, and analyze clinical information of research populations to explore the root causes for maternal and child morbidity and mortality. It uses Clinical Quality Language (CQL) expressions to assist researchers in capturing clinical data based on population study cohort criteria. This IG focuses on information relevant to longitudinal maternal care, which includes antepartum (including pre-pregnancy), intrapartum, and postpartum care of a pregnant woman. It includes how to link maternal longitudinal record with associated child/children records. 

This US Realm IG supports the use of US Core profiles where possible, as well as base FHIR and Vital Records Common Profiles FHIR IG data model for the structural linkage of mother and child clinical records. 


### Background
The rates of maternal mortality have been rising in the United States since 1987. Clinical data relevant to understanding this trend are not standardized, and data exchange is not interoperable across many relevant settings. Maternal health and associated child health are inextricably linked – what happens during gestation, delivery, and after informs health outcomes of both mother and child – but relevant data is often held in separate, unconnected records. These issues impede research on maternal morbidity and longitudinal maternal care and associated impacts to infant health. Research on root causes of maternal mortality, pediatric developmental problems, and effective treatments requires exchange of information stored in disparate sources, such as electronic health record (EHR) systems, registries, and public health agencies (PHAs).

The types of information needed to research maternal health and morbidity include social determinants of health (SDOH) and associated clinical data such as antepartum, intrapartum, and postpartum care of a pregnant woman; pregnancy-related conditions and outcomes; maternal co-morbidities; child health data; and procedures. The goal of this FHIR IG is to define a model to support data exchange for predictive analysis, risk assessment, and retrospective maternal health research across the spectrum and duration of care. 

Future users may include health departments using EHR data to inform public health interventions (e.g., case identification for reportable conditions, identifying persons lost to care, etc.) and maternal and child health researchers. The standards development effort will also examine options for data exchange mechanisms, including point-in-time query (data pull) and research population creation, i.e., patient enrollment in a study.

### Maternal Research Use Cases

This IG will eventually support mapping maternal data across health records from specialty care and linking mother and child data harmonized across a broad set of use cases. This will support researchers in identifying root causes of maternal mortality and pediatric developmental problems, including SDOH such as limited income, poor nutrition, lack of medical coverage, etc. The goal of the project is to create a method to standardize data capture for comparative analysis over time to improve health outcomes and define a framework for studying additional research populations in the future.

Initial use cases of this IG focus on hypertensive disorders of pregnancy pre, ante, and postpartum and pregnancy and subsequent death within a specific timeframe. The intent is to specify the consistent capture of clinical data of interest to maternal health researchers and outline implementing FHIR resources for that capture. Currently, the IG defines two initial, separate research use case populations: 

*	Pregnancy and subsequent death within a specific time frame: This cohort includes women who died within a year (365 days) of a pregnancy regardless of cause of death or pregnancy outcome.
*	Hypertensive Disorders of pregnancy: This use case focuses on individuals with a diagnosis of pregnancy-induced hypertension, gestational hypertension and/or post-partum hypertension diagnoses within 6 weeks of delivery.

In both instances, the IG will establish linkages via the US Core Related Person profile to collect associated child health data that may inform maternal health research outcomes. 

In the future, the IG will expand this framework to a range of use cases including:
*	Risks for children related to maternal exposure to medications taken during pregnancy
*	Potential adverse maternal obstetric history impacts on child outcomes
*	Access to relevant sensitive health information
*	Retrospective population-based analysis of inherited disorders
*	[The impacts of work activities and environment to pregnancy, maternal, and infant health.](http://hl7.org/fhir/us/odh/)

This guide fundamentally relies on creating structural relationships between:
*	Maternal and child records to effectively diagnose and treat otherwise fatal child outcomes
*	Maternal and child birth records and/or maternal and child death records
*	Maternal and child records in multiple disparate systems

### Audience 
The audience for this IG includes EHR vendors, developers of software tooling researchers, and associated information management systems. Researchers, business analysts, and policy managers can also benefit from a basic understanding of the use of this guide to support measure calculation for research purposes.

### Authors & Project Team
This table lists the authors, subject matter experts, and the affiliations which contributed to this standard. 

<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;}
.tg td{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  overflow:hidden;padding:10px 5px;word-break:normal;}
.tg th{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  font-weight:normal;overflow:hidden;padding:10px 5px;word-break:normal;}
.tg .tg-4erg{border-color:inherit;font-style:italic;font-weight:bold;text-align:left;vertical-align:top}
.tg .tg-0r4h{border-color:inherit;font-family:serif !important;font-weight:bold;text-align:left;vertical-align:top}
.tg .tg-fymr{border-color:inherit;font-weight:bold;text-align:left;vertical-align:top}
.tg .tg-0pky{border-color:inherit;text-align:left;vertical-align:top}
</style>
<table class="tg">
<thead>
  <tr>
    <th class="tg-fymr">Name &amp; Affiliation</th>
    <th class="tg-0r4h">Role</th>
    <th class="tg-fymr">Contact</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-4erg">Lantana Consulting Group</td>
    <td class="tg-0pky"> </td>
    <td class="tg-0pky"> </td>
  </tr>
  <tr>
    <td class="tg-0pky">Courtney Panaia-Rodi </td>
    <td class="tg-0pky">Project Executive</td>
    <td class="tg-0pky">courtney.panaia-rodi@lantanagroup.com</td>
  </tr>
  <tr>
    <td class="tg-0pky">Wendy Wise</td>
    <td class="tg-0pky">Project Manager</td>
    <td class="tg-0pky">wendy.wise@lantanagroup.com</td>
  </tr>
  <tr>
    <td class="tg-0pky">Lani Johnson</td>
    <td class="tg-0pky">Associate Project Manager</td>
    <td class="tg-0pky">lani.johnson@lantanagroup.com</td>
  </tr>
  <tr>
    <td class="tg-0pky">Rick Geimer</td>
    <td class="tg-0pky">FHIR Subject Matter Expert</td>
    <td class="tg-0pky">rick.geimer@lantanagroup.com</td>
  </tr>
  <tr>
    <td class="tg-0pky">Zabrina Gonzaga</td>
    <td class="tg-0pky">Terminology Subject Matter Expert</td>
    <td class="tg-0pky">zabrina.gonzaga@lantanagroup.com</td>
  </tr>
  <tr>
    <td class="tg-0pky">Sarah Gaunt</td>
    <td class="tg-0pky">Senior FHIR/CDA Analyst</td>
    <td class="tg-0pky">sarah.gaunt@lantanagroup.com</td>
  </tr>
  <tr>
    <td class="tg-0pky">Dave deRoode</td>
    <td class="tg-0pky">FHIR/CDA Analyst</td>
    <td class="tg-0pky">david.deroode@lantanagroup.com</td>
  </tr>
  <tr>
    <td class="tg-0pky">Ming Dunajick</td>
    <td class="tg-0pky">FHIR/CDA Analyst</td>
    <td class="tg-0pky">ming.dunajick@lantanagroup.com</td>
  </tr>
  <tr>
    <td class="tg-0pky">Ruby Nash</td>
    <td class="tg-0pky">FHIR Analyst</td>
    <td class="tg-0pky">ruby.nash@lantanagroup.com</td>
  </tr>
  <tr>
    <td class="tg-4erg">Office of the Assistant Secretary for Planning and Evaluation (ASPE)</td>
    <td class="tg-0pky"> </td>
    <td class="tg-0pky"> </td>
  </tr>
  <tr>
    <td class="tg-0pky">Violanda Grigorescu, MD, MSPH</td>
    <td class="tg-0pky">Senior Health Scientist <br>Division of Healthcare Quality and Outcomes, Office of Health Policy</td>
    <td class="tg-0pky">violanda.grigorescu@hhs.gov</td>
  </tr>
  <tr>
    <td class="tg-4erg">Centers for Disease Control and Prevention (CDC)</td>
    <td class="tg-0pky"> </td>
    <td class="tg-0pky"> </td>
  </tr>
  <tr>
    <td class="tg-0pky">Margaret Lampe, RN, MPH</td>
    <td class="tg-0pky">Nurse Epidemiologist &amp; Project Officer <br>Perinatal HIV Prevention Program</td>
    <td class="tg-0pky">mol0@cdc.gov</td>
  </tr>
  <tr>
    <td class="tg-0pky">Lisa Romero, DrPH</td>
    <td class="tg-0pky">Health Scientist <br>Division of Adolescent School Health</td>
    <td class="tg-0pky">eon1@cdc.gov</td>
  </tr>
  <tr>
    <td class="tg-4erg">National Institutes of Health (NIH) <br>Eunice Kennedy Shriver National Institute of Child Health and Human Development (NICHD) <br>National Information Center on Health Services Research and Health Care Technology (NICHSR)</td>
    <td class="tg-0pky"> </td>
    <td class="tg-0pky"> </td>
  </tr>
  <tr>
    <td class="tg-0pky">Alison Cernich</td>
    <td class="tg-0pky">NICHD Deputy Director</td>
    <td class="tg-0pky">alison.cernich@nih.hhs.gov</td>
  </tr>
  <tr>
    <td class="tg-0pky">John (Jack) Moye, Jr., MD</td>
    <td class="tg-0pky">Acting Director - National Children's Study <br>NICHD Medical Officer - Maternal &amp; Pediatric Infectious Disease Branch</td>
    <td class="tg-0pky">moyej@exchange.nih.gov</td>
  </tr>
  <tr>
    <td class="tg-0pky">Nahida Chakhtoura, MD, MsGH</td>
    <td class="tg-0pky">NICHD Medical Officer <br>Maternal and Pediatric Infectious Disease Branch</td>
    <td class="tg-0pky">nahida.chakhtoura@nih.gov</td>
  </tr>
  <tr>
    <td class="tg-0pky">Juanita Chinn, PhD</td>
    <td class="tg-0pky">NICHD Program Director <br>Population Dynamics Branch</td>
    <td class="tg-0pky">juanita.chinn@nih.gov</td>
  </tr>
  <tr>
    <td class="tg-0pky">Valerie Cotton</td>
    <td class="tg-0pky">NICHD Deputy Director <br>Office of Data Science and Sharing</td>
    <td class="tg-0pky">valerie.cotton@nih.gov</td>
  </tr>
  <tr>
    <td class="tg-0pky">Liz Amos, MLIS</td>
    <td class="tg-0pky">Special Assistant to the Chief Health Data Standards Officer <br>National Library of Medicine</td>
    <td class="tg-0pky">liz.amos@nih.gov</td>
  </tr>
  <tr>
    <td class="tg-4erg">Office of the National Coordinator for Health IT (ONC)</td>
    <td class="tg-0pky"> </td>
    <td class="tg-0pky"> </td>
  </tr>
  <tr>
    <td class="tg-0pky">Carmen Smiley</td>
    <td class="tg-0pky">IT Specialist (Systems Analysis)</td>
    <td class="tg-0pky">carmen.smiley@hhs.gov</td>
  </tr>
  <tr>
    <td class="tg-0pky">Rachel Abbey</td>
    <td class="tg-0pky">Public Health Analyst &amp; Program Officer</td>
    <td class="tg-0pky">rachel.abbey@hhs.gov</td>
  </tr>
  <tr>
    <td class="tg-0pky">Stephanie Garcia</td>
    <td class="tg-0pky">Senior Program Analyst</td>
    <td class="tg-0pky">stephanie.garcia@hhs.gov</td>
  </tr>
  <tr>
    <td class="tg-0pky">Brittney Boakye, MPH</td>
    <td class="tg-0pky">Program Assistant <br>Scientific Advancement Branch</td>
    <td class="tg-0pky">brittney.boakye@hhs.gov<br></td>
  </tr>
  <tr>
    <td class="tg-0pky">Alan Taylor</td>
    <td class="tg-0pky">Medical Informatics Officer, Standards and Terminology</td>
    <td class="tg-0pky">albert.taylor@hhs.gov</td>
  </tr>
</tbody>
</table>

###	Acknowledgements
This guide was developed and produced through the efforts of Health Level Seven (HL7) and created using the Trifolia-on-FHIR tool, provided by Lantana Consulting Group. The HL7 Project Insight reference number for this project is 1736.
The editors appreciate the support and sponsorship of the HL7 Public Health Workgroup, and all volunteers and staff associated with the creation of this document. This guide would not have been possible without the support of the following groups.
Health Level Seven, HL7, CDA, CCD, FHIR and the [FLAME DESIGN] are registered trademarks of Health Level Seven International, registered in the US Trademark Office.

This IG includes content from SNOMED CT, which is copyright © 2002+ International Health Terminology Standards Development Organisation (IHTSDO), and distributed by agreement between IHTSDO and HL7. Implementer use of SNOMED CT is not covered by this agreement.

This material contains content from [LOINC](http://loinc.org). LOINC is copyright © 1995-2021, Regenstrief Institute, Inc. and the Logical Observation Identifiers Names and Codes (LOINC) Committee and is available at no cost under the license at https://loinc.org/kb/license/. LOINC® is a registered United States trademark of Regenstrief Institute, Inc.



### Authors

<table>
<thead>
<tr>
<th>Name</th>
<th>Email/URL</th>
</tr>
</thead>
<tbody>
<tr>
<td>HL7 International - Public Health</td>
<td><a href="http://www.hl7.org/Special/committees/pher" target="_new">http://www.hl7.org/Special/committees/pher</a></td>
</tr>
</tbody>
</table>