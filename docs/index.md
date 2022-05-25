# Welcome to MedCom FHIR Messaging

Here you will find the nessecary information you'll need to get started with MedCom's FHIR messaging standards. Messaging standard found on this page will in time replace existing EDIFACT and OIOXML standards, you can read more about why MedCom is modernizing standards on [medcom.dk](https://www.medcom.dk/). 

  * [1 MedCom's FHIR Messaging standard](#1-medcoms-fhir-messaging-standard)
  * [1 Clinical Introduction to FHIR](#1-clinical-introduction-to-fhir)
    + [1.1 Glossary](#11-glossary)
    + [1.2 How to Read a MedCom Implementation Guide](#12-how-to-read-a-medcom-implementation-guide)
      - [1.2.1 Why are there Multiple Implementation Guides?](#121-why-are-there-multiple-implementation-guides-)
      - [1.2.2 How does Inheritance work and what is DKCorePatient?](#122-how-does-inheritance-work-and-what-is-dkcorepatient-)
    + [1.3 Relevant pages](#13-relevant-pages)
  * [2 Information about the Transportation Layer](#2-information-about-the-transportation-layer)
  * [3 Test and Certification](#3-test-and-certification)
  * [4 Release Notes](#4-release-notes)
  * [5 Support or Contact](#5-support-or-contact)

> Note: Clinical guidelines and use case documents are in both Danish and English. All the remaining documentation will be in English.

## 1 MedComs FHIR Messaging standards

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
    <td class="tg-life">Core</td>
    <td class="tg-life">Kerneprofiler</td>
    <td class="tg-etep">Core profiles that are static and used across standards.</td>
    <td class="tg-2bev"></td>
  </tr>
  <tr>
    <td class="tg-life">Messaging</td>
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
    <td class="tg-xlqk"><a href="https://tmsmedcom.github.io/GitHubPagesTest/"><span style="text-decoration:none;color:#267CB9">HospitalNotification</span></a></td>
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

When implementing a MedCom FHIR standard the documentation below is fundamental to ensure uniform use of the standards. 

### Standard Documentation

This is found in under each standard, as mentioned in [section 1](#1-medcoms-fhir-messaging-standards). Standard documentation consists of: 
* Clinical documentation: the clinical consideration behind the modernization.
* Use cases: the intended use of the standard.
* Implementation Guide: the technical specifications of the standard.
* Mapping document: the mapping from the previous OIOXML standard to FHIR.
* Testprotocol: used during test and certification to document that the vendor implementation fulfills the standard. 

### Terminology

Almost every profile uses a CodeSystem or ValueSet to structure the data using codes. All CodeSystem and ValueSet developed by MedCom can be found on the same server to enable... 

### Communication Rules

Describes how MedCom has profilled HL7 FHIR messaging framework to a Danish context. This framework is fundamental to be able to send and receive MedCom FHIR messages.

> Note: In Danish communication rules are often known as 'Syn&Kom' or 'Syntaks og Kommunikationsregler. 

<a href="https://medcomdk.github.io/MedCom-FHIR-Communication/" target="_blank">Tab here to get more information about the Communication Rules.</a>

### Transportation layer

Describes how a MedCom FHIR message shall be handled in an envelope. At present, the existing VANS network is used to deliver messages, why messages shall be sent in a VANSenvelope unless otherwise specified under the individual standard. Receipt can either be in VANSenvelope or another receipt envelope, eg. KOMBITs BeskedFordeler envelope. 

<a href="\assets\documents\MedCom_FHIR-messages_and_enclosing_envelope.md" target="_blank">Tab here to see requirements for the VANSenvelope</a>

## 3 Test and Certification

Before using the implemented standard in production environment, it must be tested and certified by MedCom to ensure it fulfills the requirements. In addition to he usual <a href="https://www.medcom.dk/standarder/testcenter" target="_blank">MedCom test setup</a> with a selftest and live test, <a href="https://touchstone.aegis.net/touchstone/" target="_blank">TouchStone</a> is used as a tool to validate FHIR messages send in different use cases.

### TouchStone

TouchStone describes an infrastructure that allows for automated test against HL7 FHIR. For each FHIR standard MedCom will develope testsuits, which is helpfull to automatisize the testing.
<a href="assets/documents/TouchStoneGettingStarted.md" target="_blank">To get started with TouchStone please take a look here.</a> 

## 4 Governance 

OPdateringer, versionering, change management

## 5 New to FHIR?

The purpose of this section is to give a brief introduction to MedComs FHIR standards to people who have heard about FHIR or now a little who wants to know more. </br> 
<a href="https://www.hl7.org/fhir/" target="_blank">Fast Healthcare Interoperability Resources (FHIR&reg;&copy;)</a> is developed by the international organization Health Level 7 (HL7) and is an open-source standard developed to exchange healthcare related information. <br> 

### FHIR-glossary

In the table below you'll find the most common words and associated descriptions, and an example. These words all describes a fundamental feature in FHIR, and they make the foundation to understand FHIR, why they are presented initially. 

<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;}
.tg td{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  overflow:hidden;padding:10px 5px;word-break:normal;}
.tg th{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  font-weight:normal;overflow:hidden;padding:10px 5px;word-break:normal;}
.tg .tg-kxdg{background-color:#FFF;border-color:#746f6c;color:#746f6c;font-weight:bold;text-align:center;vertical-align:top}
.tg .tg-fspy{background-color:#FFF;border-color:#746f6c;color:#746f6c;font-weight:bold;text-align:left;vertical-align:top}
.tg .tg-t6hh{background-color:#FFF;border-color:#746f6c;color:#746f6c;text-align:left;vertical-align:top}
</style>
<table class="tg">
<thead>
  <tr>
    <th class="tg-kxdg"><span style="font-weight:bold">Word</span></th>
    <th class="tg-fspy"><span style="font-weight:bold">Describtion</span></th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-fspy"><span style="font-weight:bold">Resources:</span></td>
    <td class="tg-t6hh">FHIR consists of generic resources, each describing a clinically delimited area, e.g. a Patient, an Allergy, an Observation, an Encounter, ect. The resouces are generic and can be used all over the world.</td>
  </tr>
  <tr>
    <td class="tg-fspy"><span style="font-weight:bold">Profiling:</span></td>
    <td class="tg-t6hh">Means to fit the resources to a given context. It is widely recognized that when exchanging data it is impossible to make a <span style="font-style:italic">one size fits all</span> within healthcare worldwide.<br>Therefore are the resources made generic with the possibility to be profiled to fit a given context, such as exchanging a CareCommunication message between Danish healthcare parties.<br>An example of profiling could be to require a lastname and an identifier (a CPR-number) of a patient when exchanging information about the person.</td>
  </tr>
  <tr>
    <td class="tg-fspy"><span style="font-weight:bold">Extensions:</span></td>
    <td class="tg-t6hh">To extend a profile to include additional information. For example is CPR-number of a citizen only relevant in Denmark and is therefore not a part of the generic Patient resource. To include a CPR-number, an extension must be made.</td>
  </tr>
  <tr>
    <td class="tg-fspy"><span style="font-weight:bold">Element:</span></td>
    <td class="tg-t6hh">A resource, hence a profile consists of multiple elements each describing a specific part of the content, like a patient name og adress.</td>
  </tr>
  <tr>
    <td class="tg-fspy"><span style="font-weight:bold">Cardinality:</span></td>
    <td class="tg-t6hh">Each element is describes with a minimum and maximum cardinality (abreviation in the IG: Card).<br>If the minimum cardinality is 0, the element may appear and if it is 1 or more the element shall appear the number of times stated.<br>If the maximum cardinality is 0 the element must not appear, 1 the element not not appear more than once and if it is * the element may appear several times.</td>
  </tr>
  <tr>
    <td class="tg-fspy"><span style="font-weight:bold">MustSupport:</span></td>
    <td class="tg-t6hh">Indicates which information which shall be included in a MedCom standard if available in the sender systemer and which information the receiver system shall be able to handle. Read more in “Syn&amp;Kom…” + Henvisning</td>
  </tr>
  <tr>
    <td class="tg-fspy"><span style="font-weight:bold">CodeSystem:</span></td>
    <td class="tg-t6hh">A collection of codes, which can be predetermined by HL7 e.g. <a href="http://hl7.org/fhir/R4/valueset-administrative-gender.html" target="_blank" rel="noopener noreferrer">gender</a>, from a international terminology e.g. <a href="https://browser.ihtsdotools.org/?" target="_blank" rel="noopener noreferrer">SNOMED CT</a> or defined by the developer of the IG e.g. <a href="https://browser.ihtsdotools.org/?" target="_blank" rel="noopener noreferrer">categories in a CareCommunication message</a>.</td>
  </tr>
  <tr>
    <td class="tg-fspy">ValueSet:</td>
    <td class="tg-t6hh">A collection of codes from one or more CodeSystems. ValueSet are referenced from elements in IG.</td>
  </tr>
  <tr>
    <td class="tg-fspy"><span style="font-weight:bold">Narrative:</span></td>
    <td class="tg-t6hh">A summary of the most important information in a standard.</td>
  </tr>
  <tr>
    <td class="tg-fspy"><span style="font-weight:bold">Implementation Guide (IG):</span></td>
    <td class="tg-t6hh">A set of rules and associated documentation describing how FHIR profiles should be used to accommodate a given standard.</td>
  </tr>
</tbody>
</table>


### How to Read a MedCom Implementation Guide

If you are interested in understanding the basics of a IG, you can follow this <a href="assets\documents\FHIRImplementationGuide.md" target="_blank">step-by-step guide</a>. It will guide you around in an IG and describe the composition. 


### Why are there Multiple Implementation Guides?

FHIR allows for a great deal of reuse. When creating a MedCom message, profiles from the MedComCore and MedComMessaging IG are used, as illustrated on the figure below. ![Overview](/assets/images/Overview-IGs.png)
Keeping the IGs seperat allow to versioning each one of them, so updates in the MedComHospitalNotification IG won't affect the version of the MedComCareCommunication IG.  However an update in the MedComMessaging IG will affect all standards that uses profiles or inherit profiles from this IG. 

### How does Inheritance Work and What is DKCore? 

In Denmark there is a national HL7 affiliate, called <a href="https://hl7.dk/" target="_blank">HL7-DK</a>. A special FHIR-interest group develops what is called DK-core profiles, generic FHIR profiles which can be used freely for FHIR project in Denmark. MedComCorePatient inherits from <a href="https://hl7.dk/fhir/core/1.1.0/StructureDefinition-dk-core-patient.html" target="_blank">DKCorePatient</a>. This means that when a MedCom standard uses a CPR-number from DKCorePatient, it is defined in the same way as when other projects inherit from DK-core and uses a CPR-number, securing consistentcy across projects. DKCorePatient is the foundation of MedComCorePatient, why MedComCorePatient is said to inherit from DKCorePatient. </br> 
<a href="https://www.medcom.dk/standarder/moderniseringsnyheder/nyhedsbrev-29-november-2021" target="_blank">You can read more about the work of HL7-DK here</a>. 

### More information

#### Webinars
In 2022 MedCom has held a two webinars concerning the modernization of MedCom standards. Both webinars freely available and in Danish. The latter is very technical oriented: 
* <a href="FHIR-introduktionswebinar (17. maj 2022)" target="_blank">FHIR-introduktionswebinar (17. maj 2022)</a>
* <a href="https://www.youtube.com/watch?v=bfzx7U2Suug" target="_blank">FHIR demo-webinar med MedCom, Mjølner og Trifork (10 . februar 2022)</a>

#### HL7 FHIR Documentation

All FHIR documentation can be found at <a href="https://www.hl7.org/fhir/" target="_blank">www.hl7.org/fhir/</a>. Here you will find detailed describtions about basic principles, presentation to all resources and much more. 

## 5 Release Notes

Updates in the latest release. 

## 6 Support or Contact

[MedCom](https://www.medcom.dk/) is responsible for this page.  
For any question regaring the standard, please contact <fhir@medcom.dk>.