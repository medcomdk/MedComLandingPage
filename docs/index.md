# Welcome to MedComs FHIR standards

MedComs modernization project involves both rethinking business requirements and technical improvement. The modernization is done in collaboration with MedComs central partners. 

On <a href="https://www.medcom.dk/" target="_blank">medcom.dk </a> are the political and strategical aspects of the modernization described. These aspects involve the initial wave of modernizations including HospitalNotification (Dansk: Sygehusadvis), CareCommunication (Dansk: Korrespondancemeddelelse), and Acknowledgement (Dansk: Kvittering). The out phasing of existing standards and implementation plan for the initial wave is described and the following modernization waves will also be described there.

The purpose of these pages is to describe both the business requirement and technical implementation of the requirements for each standard. This page guides you to find more information about each standard. 

 [Welcome to MedComs FHIR standards](#welcome-to-medcoms-fhir-standards)
  * [1 MedComs FHIR standards](#1-medcoms-fhir-standards)
  * [2 Implementing a MedCom FHIR standard](#2-implementing-a-medcom-fhir-standard)
    * [Standard Documentation](#standard-documentation)
    * [Communication Rules](#communication-rules)
    * [Network Layer](#network-layer)
  * [3 Test and Certification](#3-test-and-certification)
  * [4 Governance](#4-governance)
    * [Versioning of FHIR standard](#versioning-of-fhir-standard)
    * [Change Requests and Improvements](#change-requests-and-improvements)
  * [5 New to FHIR](#5-new-to-fhir)
  * [6 Release Notes](#6-release-notes)

> Note: Clinical guidelines and use case documents are in both Danish and English. All the remaining documentation will be in English.

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
<a href="https://svn.medcom.dk/svn/releases/Standarder/Den%20gode%20korrespondance/EDI/Dokumentation/DIS91.pdf" target="_blank">DIS91 </a> & <a href="https://svn.medcom.dk/svn/releases/Standarder/Den%20gode%20korrespondance/XML/Dokumentation/XDIS91.pdf" target="_blank">XDIS91 </a>, and Acknowledgement replaced <a href="https://svn.medcom.dk/svn/releases/Standarder/Den%20gode%20CONTRL/EDI/Dokumentation/CTL01.pdf" target="_blank">XCTL01 </a>
& <a href="https://svn.medcom.dk/svn/releases/Standarder/Den%20gode%20CONTRL/XML/Dokumentation/XCTL01.pdf" target="_blank">XCTL01 </a>.

Links to the webpage presentations of the standards can be found in the table below. On the webpages is links to the IG and other relevant information.”

<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:65%;}
.tg td{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  overflow:hidden;padding:10px 5px;word-break:normal;}
.tg th{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  font-weight:normal;overflow:hidden;padding:10px 5px;word-break:normal;}
.tg .tg-mx33{background-color:#9dbad7;border-color:inherit;color:#2c415c;font-style:italic;text-align:left;vertical-align:top}
.tg .tg-o5v9{background-color:#ffffff;border-color:inherit;color:#333333;text-align:left;vertical-align:top}
.tg .tg-67v1{border-color:inherit;color:#2c415c;font-weight:bold;text-align:left;vertical-align:top}
.tg .tg-i91a{border-color:inherit;color:#333333;text-align:left;vertical-align:top}
.tg .tg-63yy{background-color:#9dbad7;font-style:italic;text-align:left;vertical-align:top}
.tg .tg-0lax{text-align:left;vertical-align:top}
</style>
<table class="tg">
<thead>
  <tr>
    <th class="tg-67v1">English</th>
    <th class="tg-67v1">Danish</th>
    <th class="tg-67v1">Short description</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-mx33" colspan="3">Generic profiles used across standards</td>
  </tr>
  <tr>
    <td class="tg-life"><a href="https://medcomdk.github.io/dk-medcom-core/" target="_blank"><span style="text-decoration:none;color:#267CB9">Core</span></a></td>
    <td class="tg-i91a">Kerneprofiler</td>
    <td class="tg-i91a">Core profiles that are static and used across standards.</td>
  </tr>
  <tr>
    <td class="tg-life"><a href="https://medcomdk.github.io/dk-medcom-messaging/" target="_blank"><span style="text-decoration:none;color:#267CB9">Messaging</span></a></td>
    <td class="tg-i91a">Medddelsesprofiler</td>
    <td class="tg-i91a">Messaging profiles used across all messaging-based standards.</td>
  </tr>
  <tr>
    <td class="tg-mx33" colspan="3">MedComs FHIR standards</td>
  </tr>
  <tr>
    <td class="tg-o5v9">Acknowledgement</td>
    <td class="tg-o5v9">Kvittering</td>
    <td class="tg-o5v9">When a message is received an acknowledgement message shall be returned to the sender, stating if the message was received properly.</td>
  </tr>
  <tr>
    <td class="tg-xlqk"><a href="https://medcomdk.github.io/dk-medcom-hospitalnotification/" target="_blank"><span style="text-decoration:none;color:#267CB9">HospitalNotification</span></a></td>
    <td class="tg-o5v9">Sygehusadvis</td>
    <td class="tg-o5v9">Used to inform municipalities about hospitalization of a patient</td>
  </tr>
  <tr>
    <td class="tg-o5v9">CareCommunication</td>
    <td class="tg-o5v9">Korrespondancemeddelelse</td>
    <td class="tg-o5v9">Used in all parts of the Danish health care sector to communicate between parties.</td>
  </tr>
  <tr>
    <td class="tg-63yy" colspan="3">Terminology&nbsp;&nbsp;explanation </td>
  </tr>
  <tr>
    <td class="tg-0lax">Terminology</td>
    <td class="tg-0lax">Terminologi </td>
    <td class="tg-0lax">Includes CodeSystem, ValueSet and ConceptMaps developed by MedCom used in the standards</td>
  </tr>
</tbody>
</table>

## 2 Implementing a MedCom FHIR standard
When implementing a MedCom FHIR standard, it is fundamental to understand in which context the standard shall be used to ensure that the implementation fulfill the business requirements. Therefore, it is important to understand the standard documentation for the given standard. 
Furthermore it is important to understand the messaging framework and the possibilities of the VANS Network, since FHIR standards defines the process for how information is packaged and send from one part to another over the VANS Network.
The messaging framework and the VANS Network are described as [governance](#4-governance), previously known as the “Syntax and Communication Rules"


### Standard Documentation
The purpose of the standard documentation is to describe the context in which a standard shall be used and which requirements the standard shall fulfill. Implementation guide, use cases, clinical guidelines, and testprotocols will be available for all standards and some additional documents might be available as well to support implementation, such as the mapping document. Standard documentation is only provided for the standards, HospitalNotification, CareCommunication and Acknowledgement and not for the generic core or messaging IG’s.” 
Efterfulgt af listen med standard doc i følgende rækkefølge: 
•	Implementation Guide
•	Clinical guidelines
•	Use cases
•	Testprotocols 
•	Mapping doc. 








This is found in under each standard, as mentioned in [section 1](#1-medcoms-fhir-messaging-standards). Standard documentation consists of: 
* Clinical documentation: the clinical consideration behind the modernization.
* Use cases: the intended use of the standard.
* Implementation Guide: the technical specifications of the standard.
* Mapping document: the mapping from the previous OIOXML standard to FHIR.
* Testprotocol: used during test and certification to document that the vendor implementation fulfills the standard. 

### Communication Rules
The governance is important to understand before implementing a MedCom FHIR standard, as it describes the Danish profiling of the FHIR messaging framework and the network layer, which is the VANS network at present. Since the existing VANS network is used to deliver messages, shall messages be sent in a VANSenvelope unless otherwise specified. Receipt may be send in an VANSenvelope or another receipt envelope, eg. KOMBITs BeskedFordeler envelope. 

 + links til Governance siden

Describes how MedCom has profilled HL7 FHIR messaging framework to a Danish context. This framework is fundamental to be able to send and receive MedCom FHIR messages.

> Note: In Danish communication rules are often known as 'Syn&Kom' or 'Syntaks og Kommunikationsregler'. 

<a href="https://medcomdk.github.io/MedCom-FHIR-Communication/" target="_blank">Tab here to get more information about the Communication Rules.</a>

### Network Layer

Describes how a MedCom FHIR message shall be handled in an envelope. At present, the existing VANS network is used to deliver messages, why messages shall be sent in a VANSenvelope unless otherwise specified under the individual standard. Receipt can either be in VANSenvelope or another receipt envelope, eg. KOMBITs BeskedFordeler envelope. 

<a href="https://medcomdk.github.io/MedCom-FHIR-Communication/#network-layer" target="_blank">Here you can read more about the Network Layer and Network Envelope.</a>

## 3 Test and Certification

Before using the implemented standard in production environment to exchange patient data, it must be tested and certified by MedCom to ensure it fulfills the requirements. In addition to the usual <a href="https://www.medcom.dk/standarder/testcenter" target="_blank">MedCom test setup</a> with a selftest and live test, <a href="https://touchstone.aegis.net/touchstone/" target="_blank">TouchStone</a> is used as a tool to validate FHIR messages send in different use cases.

TouchStone describes an infrastructure that allows for automated test against HL7 FHIR. For each FHIR standard MedCom will develope testsuits, which is helpfull to automate the testing, both during implementation and as a part of test and certification.

[To get started with TouchStone please take a look here](assets/documents/TouchStoneGettingStarted.md)

## 4 Governance 

### Versioning of FHIR standard

MedComs FHIR standards follow <a href="https://semver.org/" target="_blank">semantic versioning version 2.0</a>, adjusted to the workflow in MedCom. Each document such as clinical guidelines, use cases or other documentation will each have a version and a releasenote, to keep track of the changes in the document. The Implementation Guide will have one version that covers all the artifacts in the Implementation Guide. 

Semantic versioning includes three numbers, seperated by dot, eg. 2.1.4. The numbers are called major.minor.patch, representing different degrees of changes. The major and minor versions will represented in Det Rådgivende Udvalg for Standarder og Arkitekturer (RUSA). If a document or IG has an extra number eg. 2.1.4-a.1 it means that it is a prerelease, and therefore not for implementation yet. In this Standard Operating Procedure (SOP) [INSERT LINK!] you can read more about the use of semantic versioning in MedCom and what it means for changes the FHIR standards. 

### Change Requests and Improvements

Stakeholders and vendors are alway welcome to submit requests for changes or improvements of the IG or other documentation. 
* If the request concerns the IG, it is possible to 
  1. submit an issue to the relevant GitHub repository
  2. write an email to <a href="mailto:fhir@medcom.dk">fhir@medcom.dk</a> describing the request
* If the request concerns other documentation, please write an email to <a href="mailto:fhir@medcom.dk">fhir@medcom.dk</a> 

Based on an analysis of the severity of the request, MedCom decide if the changes shall be implemented and change the version of the artifact or IG to reflect the changes.  

## 5 New to FHIR
This section gives a brief introduction to MedComs FHIR Universe. The introduction is for stakeholders with no or limited knowledge about FHIR. It will take you through the most common terminology used throughout the FHIR pages. Additionally, it introduces a step-by-step guide which guides one through an implementation guide (IG) and can be used as a starting point to understand an IG and its structure. Further some of the frequent asked questions are addressed. If more questions appear you are more than welcome to contact MedCom. Contact information is in the bottom of the page. Further, the introduction includes links to HL7 FHIR pages describing much more thoroughly what FHIR is and how it can be used, and links to previous webinars by MedCom.
[Tab here to get an short introduction to FHIR and how to read an Implementation Guide.](assets/documents/NewToFHIR.md)

## 6 Release Notes

[The latest changes of this page can be found here.](assets/documents/ReleaseNotes.md)
