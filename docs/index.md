# Welcome to MedComs FHIR standards

Here you will find the nessecary information you'll need to get started with MedCom's FHIR standards. Standards found on this page will in time replace existing EDIFACT and OIOXML standards, you can read more about why MedCom is modernizing standards on [medcom.dk](https://www.medcom.dk/). 

<style>
  ol {
    counter-reset: item
    }
  li {
    display: block
    }
  li:before {
    content: counters(item, ".")" ";
    counter-increment: item
  }
</style>

<ol>
  <li> <a href="#welcome-to-medcoms-fhir-standards">Welcome to MedComs FHIR standards</a>  </li>
  <li> <a href="#1-medcoms-fhir-standards"> MedComs FHIR standards</a>
  <li> <a href="#2-implementing-a-medcom-fhir-standard"> Implementing a MedCom FHIR standard</a>
    <ol>
      <li> <a href="#standard-documentation">Standard Documentation</a></li>
      <li> <a href="#terminology">Terminology</a> </li>
      <li> <a href="#communication-rules">Communication Rules</a></li>
      <li> <a href="#network-layer">Network Layer</a> </li>
    </ol>
  </li>
  <li> <a href="#3-test-and-certification">Test and Certification</a>
  <li> <a href="#4-governance">Governance</a>
    <ol>
      <li> <a href="#versioning-of-fhir-standard">Versioning of FHIR</a> </li>
      <li> <a href="#change-requests-and-improvements">Change Requests and Improvements</a> </li>
    </ol>
  </li>
   <li> <a href="#5-new-to-fhir">New to FHIR</a>
   <li> <a href="#6-release-notes">Release Notes</a>
</ol>



<!--- [Welcome to MedComs FHIR standards](#welcome-to-medcoms-fhir-standards)
  * [1 MedComs FHIR standards](#1-medcoms-fhir-standards)
  * [2 Implementing a MedCom FHIR standard](#2-implementing-a-medcom-fhir-standard)
    * [Standard Documentation](#standard-documentation)
    * [Terminology](#terminology)
    * [Communication Rules](#communication-rules)
    * [Network Layer](#network-layer)
  * [3 Test and Certification](#3-test-and-certification)
  * [4 Governance](#4-governance)
    * [Versioning of FHIR standard](#versioning-of-fhir-standard)
    * [Change Requests and Improvements](#change-requests-and-improvements)
  * [5 New to FHIR](#5-new-to-fhir)
  * [6 Release Notes](#6-release-notes)
-->
> Note: Clinical guidelines and use case documents are in both Danish and English. All the remaining documentation will be in English.

## 1 MedComs FHIR standards

In the table below is a short description of each MedCom FHIR standard as well as a link to obtain more information about the specific standard. The table is divided in two parts, the upper representing the core profiles that creates a foundation for reuse of the profiles that are used across the standards and the lower representing profiles special to the standard. A MedCom FHIR standard is composed by both core profiles and specialized profiles. 

<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;max-width:65%;}
.tg td{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  overflow:hidden;padding:10px 5px;word-break:normal;}
.tg th{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  font-weight:normal;overflow:hidden;padding:10px 5px;word-break:normal;}
.tg .tg-life{background-color:#FFF;border-color:inherit;color:#727272;text-align:center;vertical-align:middle}
.tg .tg-yapu{background-color:#FFF;border-color:inherit;color:#444;font-weight:bold;text-align:center;vertical-align:middle}
.tg .tg-etep{background-color:#FFF;border-color:#656565;color:#727272;text-align:left;vertical-align:middle}
.tg .tg-b8lo{background-color:#FFF;border-color:inherit;color:#444;font-weight:bold;text-align:left;vertical-align:middle}
.tg .tg-0lax{text-align:left;vertical-align:top}
.tg .tg-y698{background-color:#efefef;border-color:inherit;text-align:left;vertical-align:top}
.tg .tg-2bev{border-color:#656565;text-align:left;vertical-align:top}
.tg .tg-xlqk{background-color:#FFF;border-color:inherit;color:#267CB9;text-align:center;vertical-align:middle}
</style>
<table class="tg">
<thead>
  <tr>
    <th class="tg-yapu"><span style="color:#444">English</span></th>
    <th class="tg-yapu"><span style="color:#444">Danish</span></th>
    <th class="tg-b8lo"><span style="color:#444">Short description</span></th>
    <th class="tg-0lax"><span style="font-weight:bold">Replaces</span></th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-y698" colspan="4">Generic profiles used across standards</td>
  </tr>
  <tr>
    <td class="tg-life"><a href="https://medcomdk.github.io/dk-medcom-core/" target="_blank"><span style="text-decoration:none;color:#267CB9">Core</span></a></td>
    <td class="tg-life">Kerneprofiler</td>
    <td class="tg-etep">Core profiles that are static and used across standards.</td>
    <td class="tg-2bev"></td>
  </tr>
  <tr>
    <td class="tg-life"><a href="https://medcomdk.github.io/dk-medcom-messaging/" target="_blank"><span style="text-decoration:none;color:#267CB9">Messaging</span></a></td>
    <td class="tg-life">Medddelsesprofiler</td>
    <td class="tg-etep">Messaging profiles used across all messaging-based standards.</td>
    <td class="tg-2bev"></td>
  </tr>
  <tr>
    <td class="tg-y698" colspan="4">Current MedCom FHIR standards</td>
  </tr>
  <tr>
    <td class="tg-life">Acknowledgement</td>
    <td class="tg-life">Kvittering</td>
    <td class="tg-etep">When a message is received an acknowledgement message shall be returned to the sender, stating if the message was received properly.</td>
    <td class="tg-2bev"></td>
  </tr>
  <tr>
    <td class="tg-xlqk"><a href="https://medcomdk.github.io/dk-medcom-hospitalnotification/" target="_blank"><span style="text-decoration:none;color:#267CB9">HospitalNotification</span></a></td>
    <td class="tg-life">Sygehusadvis</td>
    <td class="tg-etep">Used to inform municipalities about hospitalization of a patient</td>
    <td class="tg-2bev">XDIS17 <br>XDIS20</td>
  </tr>
  <tr>
    <td class="tg-life">CareCommunication</td>
    <td class="tg-life">Korrespondancemeddelelse</td>
    <td class="tg-etep">Used in all parts of the Danish health care sector to communicate between parties.</td>
    <td class="tg-2bev">XDIS91</td>
  </tr>
</tbody>
</table>

## 2 Implementing a MedCom FHIR standard

When implementing a MedCom FHIR standard the documentation below is fundamental to ensure uniform use and implementation of the standards. 

### Standard Documentation

This is found in under each standard, as mentioned in [section 1](#1-medcoms-fhir-messaging-standards). Standard documentation consists of: 
* Clinical documentation: the clinical consideration behind the modernization.
* Use cases: the intended use of the standard.
* Implementation Guide: the technical specifications of the standard.
* Mapping document: the mapping from the previous OIOXML standard to FHIR.
* Testprotocol: used during test and certification to document that the vendor implementation fulfills the standard. 

### Terminology

All CodeSystem, ValueSet and ConceptMaps developed by MedCom can be found on HERE [INSERT LINK!]

### Communication Rules

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

The purpose of this section is to give a brief introduction to MedComs FHIR standards to stakeholders with limited knowledge about FHIR, who wants to know more.

[Tab here to get an short introduction to FHIR and how to read an Implementation Guide.](assets/documents/NewToFHIR.md)

## 6 Release Notes

[The latest changes of this page can be found here.](assets/documents/ReleaseNotes.md)
