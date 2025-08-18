# Welcome to MedCom's FHIR®© standards
**Table of contents**
* [1 MedComs FHIR standards](#1-medcoms-fhir-standards)
* [2 Implementing a MedCom FHIR standard](#2-implementing-a-medcom-fhir-standard)
  * [2.1 Standard documentation](#21-standard-documentation)
  * [2.2 General goverance for MedCom FHIR standards](#22-general-goverance-for-medcom-fhir-standards)
  * [2.3 Governance for MedCom HL7 FHIR®© Messaging](#23-governance-for-medcom-hl7-fhir-messaging) 
* [3 Test and certification](#3-test-and-certification)
  * [3.1 Test of FHIR messages](#31-test-of-fhir-messages)
* [4 Change management and versioning](#4-change-management-and-versioning)
  * [4.1 Versioning of FHIR standard](#41-versioning-of-fhir-standard)
  * [4.2 Change requests and improvements](#42-change-requests-and-improvements)
* [5 Want to stay updated?](#Want-to-stay-updated)
* [6 New to FHIR?](#New-to-fhir)
* [7 Frequently asked questions](#7-frequently-asked-questions)

> Note: Clinical guidelines are available in both Danish and English. All the remaining documentation will be in English.
<p>&nbsp;</p>

MedCom's modernisation project involves both rethinking business requirements and technical improvement. The modernisation is done in collaboration with MedCom's central partners. 

On our website <a href="https://www.medcom.dk/standarder/modernisering-af-medcom-standarder/" target="_blank">medcom.dk </a>, the political and strategical aspects of the modernisation are described. These aspects involve the initial wave of modernisation including HospitalNotification (Danish: Advis om sygehusophold), CareCommunication (Danish: Korrespondancemeddelelse), and Acknowledgement (Danish: Kvittering) standards. Furthermore, you can find descriptions of the gradual phase-out of the existing standard formats (EDIFACT and OIOXML), the implementation plan for the initial wave and descriptions of the upcoming waves of modernisation.

The purpose of this site is to guide you to find both the business and technical implementation of the requirements for each standard.
<p>&nbsp;</p>

## 1 MedCom's FHIR standards
The business requirements describe the context in which a standard should be used, and they are presented on a webpage for each standard.
For a MedCom FHIR standard, the technical implementation is presented in an Implementation Guide (IG). An IG includes several rules, extensions, profiles and more. Each profile describes a delimited area within healthcare e.g., a patient, an organisation, or an encounter.
Some of the profiles are often used across standards. An example is the Patient profile which includes the most central information about a patient or citizen, such as the civil registration number (Danish: CPR-nummer) or name. These types of profiles are called core profiles (Danish: kerneprofiler) and are gathered in the Core IG. Additionally, some profiles are often used when defining a message. These profiles are called messaging profiles (Danish: meddelelsesprofiler) and are gathered in the Messaging IG. The same applies to MedCom FHIR documents.
Some profiles are specific for a standard, which is why they are gathered in the respective IG. 
Lastly, the terminology codes (Danish: terminologi), including all CodeSystems, ValueSet, and ConceptMaps are gathered in the Terminology IG.

Due to the above mentioned, the <a href="#Tab1"> Table 1</a> is divided into three parts: 
1. MedCom's FHIR standards describes the MedCom FHIR standards and their business requirements.  
2. Terminology describes the terminology used in the MedCom FHIR standards.
3. Generic profiles describes the profiles used across MedCom FHIR standards. 

<br>
Over time, the modernised FHIR standards will replace the existing MedCom standards. For example, HospitalNotification replaces 
<a href="https://svn.medcom.dk/svn/releases/Standarder/Det%20gode%20kommuneadvis/EDI/Dokumentation/" target="_blank">DIS17</a>/
<a href="https://svn.medcom.dk/svn/releases/Standarder/Det%20gode%20kommuneadvis/XDIS17/Dokumentation/" target="_blank">XDIS17</a> and
<a href="https://svn.medcom.dk/svn/releases/Standarder/Det%20gode%20kommuneadvis/EDI/Dokumentation/" target="_blank">DIS20</a>/
<a href="https://svn.medcom.dk/svn/releases/Standarder/Det%20gode%20kommuneadvis/XDIS20/Dokumentation/" target="_blank">XDIS20</a>. CareCommunication replaces 
<a href="https://svn.medcom.dk/svn/releases/Standarder/Den%20gode%20korrespondance/EDI/Dokumentation/" target="_blank">DIS91</a>/ <a href="https://svn.medcom.dk/svn/releases/Standarder/Den%20gode%20korrespondance/XML/Dokumentation/" target="_blank">XDIS91 </a> and Acknowledgement replaces <a href="https://svn.medcom.dk/svn/releases/Standarder/Den%20gode%20CONTRL/EDI/Dokumentation/" target="_blank">CTL01-03</a>/<a href="https://svn.medcom.dk/svn/releases/Standarder/Den%20gode%20CONTRL/XML/Dokumentation/" target="_blank">XCTL01-03 </a>.

<br>
The links to the webpage presentations of the standards can be found in the <a href="#Tab1"> Table 1</a>. On the webpages, you can find the links to the IG and other relevant information that is essential for the individual standard.

<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0; width:50%;}
.tg td{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  overflow:hidden;padding:10px 5px;word-break:normal;}
.tg th{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  font-weight:normal;overflow:hidden;padding:10px 5px;word-break:normal;}
.tg .tg-ippy{border-color:#000000;color:#2c415c;text-align:left;vertical-align:top}
.tg .tg-ztr9{border-color:#000000;color:#2c415c;font-weight:bold;text-align:left;vertical-align:top}
.tg .tg-1ady{background-color:#9dbad7;border-color:#000000;color:#333333;text-align:left;vertical-align:top}
.tg .tg-on52{border-color:#000000;color:#333333;text-align:left;vertical-align:top}
</style>
<div style="overflow-x:auto;">
<table class="tg" style="undefined;table-layout: fixed; width: 942px" id="Tab1">
<caption style="color:#2c415c;font-weight:bold"> Table 1: Overview of the modernised FHIR standards </caption>
<colgroup>
<col style="width: 200.88889px">
<col style="width: 184.88889px">
<col style="width: 409.88889px">
<col style="width: 207.88889px">
</colgroup>
<thead>
  <tr>
    <th class="tg-ippy"><span style="font-weight:bold">English</span></th>
    <th class="tg-ippy"><span style="font-weight:bold">Danish</span></th>
    <th class="tg-ippy"><span style="font-weight:bold">Short description</span></th>
    <th class="tg-ztr9">Version approved by RUSA</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-1ady" colspan="4"><span style="font-style:italic">MedCom's FHIR standards</span></td>
  </tr>
  <tr>
    <td class="tg-on52"><a href="https://medcomdk.github.io/dk-medcom-hospitalnotification/" rel="noopener noreferrer"><span style="text-decoration:none">HospitalNotification</span></a></td>
    <td class="tg-on52"><span style="background-color:#FFF">Advis om sygehusophold</span></td>
    <td class="tg-on52"><span style="background-color:#FFF">Used to inform municipalities about hospitalization of a patient</span></td>
    <td class="tg-on52"> Version 3.0</td>
  </tr>
  <tr>
    <td class="tg-on52"><span style="background-color:#FFF"><a href="https://medcomdk.github.io/dk-medcom-carecommunication/" rel="noopener noreferrer"><span style="text-decoration:none">CareCommunication </span></a></span></td>
    <td class="tg-on52"><span style="background-color:#FFF">Korrespondancemeddelelse</span></td>
    <td class="tg-on52"><span style="background-color:#FFF">Used in all parts of the Danish health care sector to communicate between parties.</span></td>
    <td class="tg-on52"> Version 4.0</td>
  </tr>
  <tr>
    <td class="tg-on52"><span style="background-color:#FFF"> <a href="https://medcomdk.github.io/dk-medcom-acknowledgement/" rel="noopener noreferrer"><span style="text-decoration:none">Acknowledgement </span></a></span></td>
    <td class="tg-on52"><span style="background-color:#FFF">Kvittering</span></td>
    <td class="tg-on52"><span style="background-color:#FFF">When a message is received, an acknowledgement message shall be returned to the sender, which states whether the message was valid and the transportation went good.</span></td>
    <td class="tg-on52"> Version 2.0</td>
  </tr>
    <tr>
    <td class="tg-on52"><span style="background-color:#FFF"> <a href="https://medcomdk.github.io/dk_HomeCareObservations/" rel="noopener noreferrer"><span style="text-decoration:none">HomeCareObservation </span></a></span></td>
    <td class="tg-on52"><span style="background-color:#FFF">Kommunale Prøvesvar</span></td>
    <td class="tg-on52"><span style="background-color:#FFF">This standard is developed to be part of a production trial of the communication between the general practitioner and municipal acute care team. Used to exchange results and observations performed and produced by the municipal acute care team. </span></td>
    <td class="tg-on52"> Version 1.0</td>
  </tr>
  </tr>
    <tr>
    <td class="tg-on52"><span style="background-color:#FFF"> <a href="https://medcomdk.github.io/dk-medcom-conditionlist/" rel="noopener noreferrer"><span style="text-decoration:none">ConditionList</span></a></span></td>
    <td class="tg-on52"><span style="background-color:#FFF">Deling af diagnoser</span></td>
    <td class="tg-on52"><span style="background-color:#FFF">This document based standard is developed to support sharing of a citizens diagnoses selected by the citizens general practitioner to the citizen and healthcare providers</span></td>
    <td class="tg-on52"> Version 1.0</td>
  </tr>
  <tr>
    <td class="tg-1ady" colspan="4"><span style="font-style:italic">Terminology</span></td>
  </tr>
  <tr>
    <td class="tg-on52"><a href="https://medcomdk.github.io/dk-medcom-terminology/" rel="noopener noreferrer"><span style="text-decoration:none">Terminology </span></a></td>
    <td class="tg-on52">Terminologi</td>
    <td class="tg-on52">Includes CodeSystem, ValueSet and ConceptMaps developed by MedCom used in the standards</td>
    <td class="tg-on52"></td>
  </tr>
  <tr>
    <td class="tg-on52"><a href="https://medcomfhir.dk/ig/xdsmetadata/" rel="noopener noreferrer"><span style="text-decoration:none">XDS-metadata </span></a></td>
    <td class="tg-on52">XDS-metadata</td>
    <td class="tg-on52">Includes CodeSystem, and ValueSet for use as metadata in document-based exchange. Please notice, the <a href="https://svn.medcom.dk/svn/releases/Standarder/IHE/OID/" target="_blank">ValueSets in defined in the IHE-XDS metadata (.xslx)</a> is currently the valid representation.</td>
</td>
    <td class="tg-on52"></td>
  </tr>
   <tr>
    <td class="tg-1ady" colspan="4"><span style="font-style:italic">Generic profiles</span></td>
  </tr>
  <tr>
    <td class="tg-on52"><a href="https://medcomdk.github.io/dk-medcom-core/" rel="noopener noreferrer"><span style="text-decoration:none">Core</span></a></td>
    <td class="tg-on52">Kerneprofiler</td>
    <td class="tg-on52">Core profiles that are static and used across standards.</td>
    <td class="tg-on52"></td>
  </tr>
  <tr>
    <td class="tg-on52"><a href="https://medcomdk.github.io/dk-medcom-messaging/" rel="noopener noreferrer"><span style="text-decoration:none">Messaging</span></a></td>
    <td class="tg-on52">Meddelsesprofiler</td>
    <td class="tg-on52">Messaging profiles used across all messaging-based standards.</td>
    <td class="tg-on52"></td>
  </tr>
  <tr>
    <td class="tg-on52"><a href="https://medcomdk.github.io/dk-medcom-document/" rel="noopener noreferrer"><span style="text-decoration:none">Document</span></a></td>
    <td class="tg-on52">Dokumentprofiler</td>
    <td class="tg-on52">Document profiles used across document-based standards.</td>
    <td class="tg-on52"></td>
  </tr>
</tbody>
</table>
</div>
<br><br>


## 2 Implementing a MedCom FHIR standard
When implementing a MedCom FHIR standard, it is fundamental to understand in which context the standard should be used to ensure that the implementation fulfils the business requirements. Therefore, it is important to understand the standard documentation for the given standard. 
Furthermore, it is essential to understand the governance, as it defines the process for how information is packaged and sent.
<br>
<p>&nbsp;</p>

### 2.1 Standard documentation
The purpose of the standard documentation is to describe the context in which a standard should be used and which requirements the standard should fulfil. Standard documentation is only provided for Medcom's FHIR standards and thus not for the generic Core or, Document or Messaging Profiles. The content of the standard documentation can vary between the standards.

<!-- An implementation guide, use cases, clinical guidelines for application and testprotocols will be available for all standards -->

<!-- .Furthermore, some additional documents might be available to support implementation, such as a mapping document.  -->
The standard documentation can consist of: 
* **Implementation Guide**: the technical specifications of the standard.
* **Clinical guidelines for application**: the clinical consideration behind the modernisation.
* **Use cases**: the intended use of the standard.
* **Testprotocol**: used during test and certification to document that the vendor implementation fulfils the standard. 
* **Mapping document**: the mapping from the previous OIOXML standard to FHIR.
<p>&nbsp;</p>

### 2.2 General goverance for MedCom FHIR standards
The general governance is important to understand before implementing a MedCom FHIR standard, as it describes the general governance for both MedCom FHIR document and messaging standards. Governance for the individual standard types can be found below.
[Click here to get more information about the general governance for MedCom FHIR standards.](assets/documents/GeneralGovernanceFHIRStandards.md)
<p>&nbsp;</p>

### 2.2 Governance for MedCom HL7 FHIR Messaging
The messaging governance is important to understand before implementing a MedCom FHIR messaging standard, as it describes the Danish profiling of the FHIR messaging framework and the network layer, which is the VANS network at present. Since the existing VANS network is used to deliver messages, messages must be sent in a VANSenvelope unless otherwise specified. <br>
<a href="https://medcomdk.github.io/MedCom-FHIR-Communication/#network-layer" target="_blank"> Click here to get more information about messaging governance.</a>  
<p>&nbsp;</p>

## 3 Test and certification
Before using the implemented standard in a production environment to exchange patient data, it must be tested and certified by MedCom to ensure it fulfils the standard and business requirements. In addition to the usual <a href="https://medcom.dk/standarder/test-og-certificering/" target="_blank">MedCom test setup</a> with a self test and live test, <a href="https://touchstone.aegis.net/touchstone/" target="_blank">TouchStone</a> is used as a tool to validate FHIR messages sent in different use cases.

TouchStone is an infrastructure that allows for automated tests against implementations of HL7 FHIR. For each FHIR standard MedCom will develope test scripts, that will be available in TouchStone. These test scripts can be used both during implementation/development and as a part of the test and certification. <br>
[Click here to get started with TouchStone](assets/documents/TouchStoneGettingStarted.md)
<p>&nbsp;</p>

### 3.1 Test of FHIR Messages and Documents
Since MedCom's FHIR messages are sent over the VANS network, vendors implementing messaging standards must to be abel to include the message in a VANSenvelope before sending the message.<br>
Vendors implementing MedCom's FHIR document standards must be able to share documents in the relevant infrastructure.<br>
Vendors should expect to demonstrate this as a part of test and certification.

## 4 Change management and versioning  

### 4.1 Versioning of Medcom FHIR standards
MedComs FHIR standards follow the <a href="https://semver.org/" target="_blank">semantic versioning, version 2.0</a>, which is adjusted to the workflow in MedCom. Each document, such as the clinical guidelines, use cases or other documentation, will have a version and a release note, to keep track of the changes in the document. The IG will have one version that covers all the included artefacts. Versioning of the clinical guidelines, use cases, test material, and more will follow the major and minor version of the technical specifications in the IG, but may have a patch version that is different from the IG’s patch-version.

Semantic versioning includes three numbers, which are separated by a dot, e.g. 2.1.4. The numbers are called <i>major.minor.patch</i>,which represent different degrees of changes: 
* MAJOR version changes when you make incompatible API changes
* MINOR version changed when you add functionality in a backwards compatible manner
* PATCH version changed when you make backwards compatible bug fixes

The major and minor versions are  recorded  in  <a href="https://sundhedsdatastyrelsen.dk/da/rammer-og-retningslinjer/om-referencearkitektur-og-standarder/udvalg" target="_blank">Det Rådgivende Udvalg for Standarder og Arkitekturer (RUSA)</a>.
RUSA is a Danish advisory committee for standards and architecture. RUSA is working to ensure coherence and interoperability in digital solutions in the healthcare field. 
If a document or an IG has an extra number eg. 2.1.4-a.1 it is a prerelease and therefore not ready for implementation. In this Standard Operating Procedure (SOP) 4.1 you can read more about the use of semantic versioning in MedCom and what it means for changes in the FHIR standards. 
<a href="https://svn.medcom.dk/svn/qms/Offentlig/SOPer/" target="_blank">Click here to read SOP-4.1.</a> 
<p>&nbsp;</p>

### 4.2 Governance of Medcom FHIR Terminology
Governance of MedCom FHIR Terminology covers change management and versioning of the Terminology IG and corresponding affected standards. It specificlally adresses Codesystems, Valuesets and ConceptMaps, which are published through the MedCom FHIR Terminology IG.
[Click here to get more information about the governance for MedCom FHIR Terminology](assets/documents/GovernanceTerminology.md)
<p>&nbsp;</p>

### 4.3 Change requests and improvements
Stakeholders and vendors are alway welcome to submit requests for changes or improvements to the IG or other documentation. 
* If the request concerns the IG, it is possible to: 
  1. submit an issue to the relevant <a href="https://github.com/medcomdk" target="_blank">MedCom GitHub repository</a>
  2. write an email to <a href="mailto:fhir@medcom.dk">fhir@medcom.dk</a> describing the request
* If the request concerns other documentation, please write an email to <a href="mailto:fhir@medcom.dk">fhir@medcom.dk</a>. 
<br>
Based on an analysis of the severity of the request, MedCom decides if the changes should be implemented and thus change the version of the artefact or IG to reflect the changes.  
<p>&nbsp;</p>


## 5 Want to stay updated? {#Want-to-stay-updated}
It is possible to be notified about the latest changes in the standard documentation.
Here is what to do:
1. Go to the <a href="https://github.com/medcomdk" target="_blank">MedCom GitHub repository</a>
2. Choose the repository that you want to receive information about 
3. Choose the “watch” button in the right upper corner.  
<br>

> Please notice that you must have a GitHub account to be able to "watch" the repository. If you don't have a GitHub account, you can create one at <a href="https://github.com/signup?ref_cta=Sign+up&ref_loc=header+logged+out&ref_page=%2F%3Corg-login%3E&source=header"> GitHub</a>

## 6 New to FHIR? {#New-to-fhir}
This section aims to give a brief introduction to MedCom's FHIR universe. The introduction is aimed at stakeholders with no or limited knowledge about FHIR. The section will take you through the most commonly used expressions used throughout the FHIR pages. Additionally, it introduces a step-by-step guide which guides you through an IG and can be used as a starting point to understand an IG and its structure. Furthermore some of the frequently asked questions are addressed. If more questions appear you are more than welcome to contact MedCom. You can find contact information at the bottom of the page. Lastly, the introduction includes links to HL7 FHIR pages describing, in more detail, what FHIR is and how it can be used. Here, you can also find, previous webinars held by MedCom. <br>
[Click here to get a short introduction to FHIR and how to read an Implementation Guide.](assets/documents/NewToFHIR.md) 
<p>&nbsp;</p>

## 7 Frequently asked questions
In this section you will find descriptions that addresses some often asked questions about MedCom's FHIR universe.  
[Click here to read frequently asked questions](assets/documents/FAQ.md)

