# Welcome to MedComs FHIR®© standards
<hr/>

**Table of Content**
* [1 MedComs FHIR standards](#1-medcoms-fhir-standards)
* [2 Implementing a MedCom FHIR standard](#2-implementing-a-medcom-fhir-standard)
  * [2.1 Standard Documentation](#21-standard-documentation)
  * [2.2 Governance for MedCom HL7 FHIR®© Messaging](#22-governance-for-medcom-hl7-fhir-messaging) 
* [3 Test and Certification](#3-test-and-certification)
* [4 Change Management and Versioning](#4-change-management-and-versioning)
  * [4.1 Versioning of FHIR standard](#41-versioning-of-fhir-standard)
  * [4.2 Change Requests and Improvements](#42-change-requests-and-improvements)
* [5 New to FHIR?](#New-to-fhir)
* [6 Release Notes](#6-release-notes)
<hr/>

> Note: Clinical guidelines and use case documents are in both Danish and English. All the remaining documentation will be in English.
<p>&nbsp;</p>

MedComs modernization project involves both rethinking business requirements and technical improvement. The modernization is done in collaboration with MedComs central partners. 

On <a href="https://www.medcom.dk/" target="_blank">medcom.dk </a> are the political and strategical aspects of the modernization described. These aspects involve the initial wave of modernizations including HospitalNotification (Dansk: Sygehusadvis), CareCommunication (Dansk: Korrespondancemeddelelse), and Acknowledgement (Dansk: Kvittering). The out phasing of existing  standards (EDIFACT and OIOXML), and implementation plan for the initial wave is described and the following modernization waves will also be described there.

The purpose of these pages is to describe both the business requirement and technical implementation of the requirements for each standard. This page guides you to find more information about each standard. 
<p>&nbsp;</p>

## 1 MedComs FHIR standards
The business requirements describe the context in which a standard shall be used, and they are presented on a webpage for each standard.
For a MedCom FHIR standard, the technical implementation is presented in an Implementation Guide (IG). An IG includes several rules, extensions, profiles, and more. Each profile describes a delimited area within healthcare e.g., a patient, an organization, or an encounter.
Some of the profiles are often used across standards. An example could be the Patient profile which includes the most central information about a patient or citizen such as the CPR-number or name. These types of profiles are called core profiles (Dansk: kerneprofiler) and are gathered in the Core IG. Additionally, some profiles are often used when defining a message. These profiles are called messaging profiles and are gathered in the Messaging IG. 
Some profiles are specific for a standard, why these are gathered in the respective IG. 
Lastly, the terminology codes including all CodeSystems, ValueSet, and ConceptMaps are gathered in the Terminology IG.
Currently, there are three FHIR standards: HospitalNotification, CareCommunication, and Acknowledgement, which all are composed of profiles from the Core, and Messaging IG as well as the IG for the specific standard, and codes from the Terminology IG. 

Due to the above mentioned, the table below is divided into three parts: the upper part describing the profiles used across standards and the middle part describing the profiles specific for a standard as well as the business requirements for a standard, and the lower part describing the terminology used in the standards. 

The modernized FHIR standards will in time replace existing MedCom standards. HospitalNotification replaces 
<a href="https://svn.medcom.dk/svn/releases/Standarder/Det%20gode%20kommuneadvis/XDIS17/Dokumentation/XDIS17.pdf" target="_blank">XDIS17</a> &
<a href="https://svn.medcom.dk/svn/releases/Standarder/Det%20gode%20kommuneadvis/XDIS20/Dokumentation/XDIS20.pdf" target="_blank">XDIS20</a>, CareCommunication replaces 
<a href="https://svn.medcom.dk/svn/releases/Standarder/Den%20gode%20korrespondance/EDI/Dokumentation/DIS91.pdf" target="_blank">DIS91 </a> & <a href="https://svn.medcom.dk/svn/releases/Standarder/Den%20gode%20korrespondance/XML/Dokumentation/XDIS91.pdf" target="_blank">XDIS91 </a>, and Acknowledgement replaces <a href="https://svn.medcom.dk/svn/releases/Standarder/Den%20gode%20CONTRL/EDI/Dokumentation/CTL01.pdf" target="_blank">XCTL01 </a>
& <a href="https://svn.medcom.dk/svn/releases/Standarder/Den%20gode%20CONTRL/XML/Dokumentation/XCTL01.pdf" target="_blank">XCTL01 </a>.

Links to the webpage presentations of the standards can be found in the table below. On the webpages is links to the IG and other relevant information.

<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0; width:75%;}
.tg td{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  overflow:hidden;padding:10px 5px;word-break:normal;}
.tg th{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  font-weight:normal;overflow:hidden;padding:10px 5px;word-break:normal;}
.tg .tg-ippy{border-color:#000000;color:#2c415c;text-align:left;vertical-align:top}
.tg .tg-ztr9{border-color:#000000;color:#2c415c;font-weight:bold;text-align:left;vertical-align:top}
.tg .tg-1ady{background-color:#9dbad7;border-color:#000000;color:#333333;text-align:left;vertical-align:top}
.tg .tg-on52{border-color:#000000;color:#333333;text-align:left;vertical-align:top}
</style>
<table class="tg" style="undefined;table-layout: fixed; width: 942px">
<caption style="color:#2c415c;font-weight:bold"> Table 1: Overview of the modernized FHIR standards </caption>
<colgroup>
<col style="width: 138.88889px">
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
    <td class="tg-1ady" colspan="4"><span style="font-style:italic">Generic profiles used across standards</span></td>
  </tr>
  <tr>
    <td class="tg-on52"><a href="https://medcomdk.github.io/dk-medcom-core/" rel="noopener noreferrer"><span style="text-decoration:none">Core</span></a></td>
    <td class="tg-on52">Kerneprofiler</td>
    <td class="tg-on52">Core profiles that are static and used across standards.</td>
    <td class="tg-on52"></td>
  </tr>
  <tr>
    <td class="tg-on52"><a href="https://medcomdk.github.io/dk-medcom-messaging/" rel="noopener noreferrer"><span style="text-decoration:none">Messaging</span></a></td>
    <td class="tg-on52">Medddelsesprofiler</td>
    <td class="tg-on52">Messaging profiles used across all messaging-based standards.</td>
    <td class="tg-on52"></td>
  </tr>
  <tr>
    <td class="tg-1ady" colspan="4"><span style="font-style:italic">MedComs FHIR standards</span></td>
  </tr>
  <tr>
    <td class="tg-on52"><span style="background-color:#FFF"> <a href="https://medcomdk.github.io/dk-medcom-acknowledgement/" rel="noopener noreferrer"><span style="text-decoration:none">Acknowledgement </span></a></span></td>
    <td class="tg-on52"><span style="background-color:#FFF">Kvittering</span></td>
    <td class="tg-on52"><span style="background-color:#FFF">When a message is received an acknowledgement message shall be returned to the sender, stating if the message was received properly.</span></td>
    <td class="tg-on52"></td>
  </tr>
  <tr>
    <td class="tg-on52"><a href="https://medcomdk.github.io/dk-medcom-hospitalnotification/" rel="noopener noreferrer"><span style="text-decoration:none">HospitalNotification</span></a></td>
    <td class="tg-on52"><span style="background-color:#FFF">Sygehusadvis</span></td>
    <td class="tg-on52"><span style="background-color:#FFF">Used to inform municipalities about hospitalization of a patient</span></td>
    <td class="tg-on52"> Version 1.0</td>
  </tr>
  <tr>
    <td class="tg-on52"><span style="background-color:#FFF"><a href="https://medcomdk.github.io/dk-medcom-carecommunication/" rel="noopener noreferrer"><span style="text-decoration:none">CareCommunication </span></a></span></td>
    <td class="tg-on52"><span style="background-color:#FFF">Korrespondancemeddelelse</span></td>
    <td class="tg-on52"><span style="background-color:#FFF">Used in all parts of the Danish health care sector to communicate between parties.</span></td>
    <td class="tg-on52"> Version 1.0</td>
  </tr>
  <tr>
    <td class="tg-1ady" colspan="4"><span style="font-style:italic">Terminology  explanation</span></td>
  </tr>
  <tr>
    <td class="tg-on52"><a href="https://medcomdk.github.io/dk-medcom-terminology/" rel="noopener noreferrer"><span style="text-decoration:none">Terminology </span></a></td>
    <td class="tg-on52">Terminologi</td>
    <td class="tg-on52">Includes CodeSystem, ValueSet and ConceptMaps developed by MedCom used in the standards</td>
    <td class="tg-on52"></td>
  </tr>
</tbody>
</table>
<br><br>


## 2 Implementing a MedCom FHIR standard
When implementing a MedCom FHIR standard, it is fundamental to understand in which context the standard shall be used to ensure that the implementation fulfill the business requirements. Therefore, it is important to understand the standard documentation for the given standard. 
Furthermore it is important to understand the messaging framework and the possibilities of the VANS Network, since FHIR standards defines the process for how information is packaged and send from one part to another over the VANS Network.
The messaging framework and the VANS Network are described as governance, previously known as the “Syntax and Communication Rules". <br>
<a href="https://medcomdk.github.io/MedCom-FHIR-Communication/#network-layer" target="_blank"> Tab here to get more information about the govenance.</a>  
<br>

### 2.1 Standard Documentation
The purpose of the standard documentation is to describe the context in which a standard shall be used and which requirements the standard shall fulfill. Implementation guide, use cases, clinical guidelines, and testprotocols will be available for all standards and some additional documents might be available as well to support implementation, such as the mapping document. Standard documentation is only provided for the standards, HospitalNotification, CareCommunication and Acknowledgement and not for the generic core or messaging IG’s.
Standard documentation consists of: 
* **Implementation Guide**: the technical specifications of the standard.
* **Clinical guidelines**: the clinical consideration behind the modernization.
* **Use cases**: the intended use of the standard.
* **Testprotocol**: used during test and certification to document that the vendor implementation fulfills the standard. 
* **Mapping document**: the mapping from the previous OIOXML standard to FHIR.
<p>&nbsp;</p>

### 2.2 Governance for MedCom HL7 FHIR Messaging
The governance is important to understand before implementing a MedCom FHIR standard, as it describes the Danish profiling of the FHIR messaging framework and the network layer, which is the VANS network at present. Since the existing VANS network is used to deliver messages, shall messages be sent in a VANSenvelope unless otherwise specified. Receipt may be send in an VANSenvelope or another receipt envelope, eg. KOMBITs BeskedFordeler envelope. <br>
<a href="https://medcomdk.github.io/MedCom-FHIR-Communication/#network-layer" target="_blank"> Tab here to get more information about the govenance.</a>  
<p>&nbsp;</p>

## 3 Test and Certification
Before using the implemented standard in production environment to exchange patient data, it must be tested and certified by MedCom to ensure it fulfills the requirements. In addition to the usual <a href="https://www.medcom.dk/standarder/testcenter" target="_blank">MedCom test setup</a> with a selftest and live test, <a href="https://touchstone.aegis.net/touchstone/" target="_blank">TouchStone</a> is used as a tool to validate FHIR messages send in different use cases.

TouchStone describes an infrastructure that allows for automated test against HL7 FHIR. For each FHIR standard MedCom will develope testsuits, which is helpfull to automate the testing, both during implementation and as a part of test and certification. <br>
[Tab here to get started with TouchStone](assets/documents/TouchStoneGettingStarted.md)
<p>&nbsp;</p>

## 4 Change Management and Versioning  

### 4.1 Versioning of FHIR standard
MedComs FHIR standards follow <a href="https://semver.org/" target="_blank">semantic versioning, version 2.0</a>, adjusted to the workflow in MedCom. Each document such as clinical guidelines, use cases or other documentation will each have a version and a releasenote, to keep track of the changes in the document. The Implementation Guide will have one version that covers all the artifacts in the Implementation Guide. 

Semantic versioning includes three numbers, seperated by dot, eg. 2.1.4. The numbers are called major.minor.patch, representing different degrees of changes. The major and minor versions will represented in  <a href="https://sundhedsdatastyrelsen.dk/da/rammer-og-retningslinjer/om-referencearkitektur-og-standarder/udvalg" target="_blank">Det Rådgivende Udvalg for Standarder og Arkitekturer (RUSA)</a>. If a document or IG has an extra number eg. 2.1.4-a.1 it means that it is a prerelease, and therefore not for implementation yet. In this Standard Operating Procedure (SOP) **(The LINK Is Coming Soon)** you can read more about the use of semantic versioning in MedCom and what it means for changes the FHIR standards. 
<p>&nbsp;</p>

### 4.2 Change Requests and Improvements
Stakeholders and vendors are alway welcome to submit requests for changes or improvements of the IG or other documentation. 
* If the request concerns the IG, it is possible to 
  1. submit an issue to the relevant GitHub repository
  2. write an email to <a href="mailto:fhir@medcom.dk">fhir@medcom.dk</a> describing the request
* If the request concerns other documentation, please write an email to <a href="mailto:fhir@medcom.dk">fhir@medcom.dk</a> 
<br>
Based on an analysis of the severity of the request, MedCom decide if the changes shall be implemented and change the version of the artifact or IG to reflect the changes.  
<p>&nbsp;</p>

## 5 New to FHIR? {#New-to-fhir}
This section gives a brief introduction to MedComs FHIR Universe. The introduction is for stakeholders with no or limited knowledge about FHIR. It will take you through the most common terminology used throughout the FHIR pages. Additionally, it introduces a step-by-step guide which guides one through an implementation guide (IG) and can be used as a starting point to understand an IG and its structure. Further some of the frequent asked questions are addressed. If more questions appear you are more than welcome to contact MedCom. Contact information is in the bottom of the page. Further, the introduction includes links to HL7 FHIR pages describing much more thoroughly what FHIR is and how it can be used, and links to previous webinars by MedCom. <br>
[Tab here to get an short introduction to FHIR and how to read an Implementation Guide.](assets/documents/NewToFHIR.md) 
<p>&nbsp;</p>

<!-- ## 6 Release Notes

[The latest changes of this page](assets/documents/ReleaseNotes.md) can be found here. -->
