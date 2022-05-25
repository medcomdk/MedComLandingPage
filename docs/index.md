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
.tg  {border-collapse:collapse;border-spacing:0;max-width:60%;}
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

[Table 1 - overview of MedComs FHIR Standards][overview]

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

Before using the implemented standard in production environment, it must be tested and certified by MedCom.  

## 4 Governance 

OPdateringer, versionering, 

## 5 New to FHIR?

[Fast Healthcare Interoperability Resources (FHIR&reg;&copy;)](https://www.hl7.org/fhir/) is developed by the international organization Health Level 7 (HL7) and is an open-source standard developed to exchange healthcare related information. <br> 
This introduction is amied for people with limited insigth into FHIR. First, the most common _FHIR-words_ are presented followed by a short introduction to a MedCom Implementation Guide (IG). 

### 2.1 Glossary

Below you'll find the most common words and associated descriptions used in FHIR-regi. 

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


### 2.2 How to Read a MedCom Implementation Guide

This step-by-step guide takes its starting point in [MedComCore IG](https://build.fhir.org/ig/hl7dk/dk-medcom-core/). 

* Go to [MedComCore IG](https://build.fhir.org/ig/hl7dk/dk-medcom-core/).
* On the landingpage you'll find a short introduction to the IG, in this case the MedComCore profiles. 
    * The topbar on the page includes multiple options: 
    ![Content](/assets/images/IG-content.png)
* Click on the tab [Profiles](https://build.fhir.org/ig/hl7dk/dk-medcom-core/profiles.html) you'll get an overview of the profiles in the IG. 
    * Choose [MedComCorePatient](https://build.fhir.org/ig/hl7dk/dk-medcom-core/StructureDefinition-medcom-core-patient.html) and you will get to the frontpage of MedComCorePatient, called 'Content'. _Please notice: a MedComCorePatient describes both a patient and a citizen._ Here you'll find a short introduction to the profile and a table including five tabs, where three are of special interest: 
    ![Profile Content](/assets/images/ProfileContent.png)
      * Click on the tab 'Snapshot Table (MustSupport)'. Here is all required content for the profil gathered. The table contains five headlines
          * Name
                * The element name.
            * Flags: 
                * I = a rule, which can be seen further down the page.
                * &sum; = if the element shall be included in the narrativ. 
                * ?! = modifier element, an element which potentially can modify the understanding of an entire message
            * Cardinality (Card):
                * Given the minimum cardinality of 1 for Patient.identifier and Patient.name the information for these elements shall always be included when exchanging a MedCom standard. Not only shall a Patient.name be included, it shall always be the patients offical name, indicated by Patient.name:Official. Information about Patient.telecom, Patient.deceased, Patient.address and Patient.managingOrganization shall be included if the information is available in the sender system, given the minimum cardinality of 0. 
                * Given the maximum cardinality of * for Patient.identifier, Patient.name, Patient.telecom and Patient.address it is allowed to slice the element. For the element Patient.deceased it is only allowed to include the information once. 
            * Type: 
                * Describes the datatype of the element. Click on them for more information about the datatype. 
                * One migth notice the type at the top of the elements says _DKCorePatient_, which means that the MedComCorePatient inherits from a Patient profile developed by the Danish HL7 affiliate. You can read more about the work under '[How does Inheritance work and what is DKCorePatient?](#how-does-inheritance-work-and-what-is-dk-core-profiles)'.
            * Description and Constraints
                * A short description of the element as well as rules associated with the element.
      * If you click on [Detailed Descriptions](https://build.fhir.org/ig/hl7dk/dk-medcom-core/StructureDefinition-medcom-core-patient-definitions.html) yuo'll get a more detailed description of all the elements in the profile. 
      * Click on [Mappings](https://build.fhir.org/ig/hl7dk/dk-medcom-core/StructureDefinition-medcom-core-patient-mappings.html) you'll find mapping to other HL7 standards, but not the previuos MedCom standards. To get this information you must look under each standard. 
      * Click on [Examples](https://build.fhir.org/ig/hl7dk/dk-medcom-core/StructureDefinition-medcom-core-patient-examples.html) and you'll find examples for the profile. For MedComCorePatient the example is quite simple, but for MedComHospitalNotificationMessage it contains a lot more information.
          *  If you select one of the examples you will be presented for the content of the narrative text. If you instead select the tabs XML, JSON or TTL you will see the entire content of the MedComCorePatient. 
      * If you click on XML, JSON og TTL you see StructureDefinition of the profile, which reflects the content. 
    * Now, try choosing the profile [MedComCoreEncounter](https://build.fhir.org/ig/hl7dk/dk-medcom-core/StructureDefinition-medcom-core-encounter.html)
        * Here you'll see the type Reference(...) at the element Encounter.subject. This means that the element references the MedComCorePatient profile, and that an encounter always shall be associated with a patient. 
        * For the elements Encounter.status and Encounter.class the type is code or coding, meaning that a predefined, structured code shall be selected from a ValueSet. which can be seen in the column 'Description & Constraints'.  
* The tab [Extensions](https://build.fhir.org/ig/hl7dk/dk-medcom-core/extensions.html) shows the extensions made for the IG. 
* The tab [Terminology](https://build.fhir.org/ig/hl7dk/dk-medcom-core/terminology.html) shows the CodeSystems and ValueSets used in the IG.
* The tab [Artifacts](https://build.fhir.org/ig/hl7dk/dk-medcom-core/artifacts.html) shows entire content of the IG.


#### 2.2.1 Why are there Multiple Implementation Guides?

FHIR allows for a great deal of reuse. When creating a MedCom message, profiles from the MedComCore and MedComMessaging IG are used, as illustrated on the figure below. ![Overview](/assets/images/Overview-IGs.png)
Keeping the IGs seperat allow to versioning each one of them, so updates in the MedComHospitalNotification IG won't affect the version of the MedComCareCommunication IG.  However an update in the MedComMessaging IG will affect all standards that uses profiles or inherit profiles from this IG. 
For more information about versioning see HERE.. (is coming.)

#### 2.2.2 How does Inheritance work and what is DKCorePatient? 

Just like profiling of resources, it is possible to take a generic profile and specify it to a given context. For example is a [MedComCoreOrganization](https://build.fhir.org/ig/hl7dk/dk-medcom-core/StructureDefinition-medcom-core-organization.html) determined to include a SOR-code and possible a name of the organization. When using an organization in a messaging context, it is determined that a [MedComMessagingOrganization](https://build.fhir.org/ig/hl7dk/dk-medcom-messaging/StructureDefinition-medcom-messaging-organization.html) further shall include an EAN/GLN-number. However, MedComMessagingOrganization is based on the profiling of MedComCoreOrganization and is therefore said to inherit from this profile. <br>
In Denmark there is a national HL7 affiliate, called HL7-DK. A special FHIR-interest group develops what is called DK-core profiles, generic FHIR profiles which can be used freely for FHIR project in Denmark. MedComCorePatient inherits from [DKCorePatient](https://hl7.dk/fhir/core/1.1.0/StructureDefinition-dk-core-patient.html). This means that when a MedCom standard uses a CPR-number from DKCorePatient, it is defined in the same way as when other projects inherit from DK-core and uses a CPR-number, securing consistentcy across projects. You can read more about the work of HL7-DK [here](https://www.medcom.dk/standarder/moderniseringsnyheder/nyhedsbrev-29-november-2021). 

### 2.3 Relevant pages

Is coming...

## 3 Information about the Transportation Layer

See [here](/assets/documents/MedComs_FHIR-meddelelser_og_forsendelseskuvert.md)


## 4 Test and Certification

Link to MedCom testCenter. 

Link to FHIR validator 

Link to GettingStarted with TouchStone 

## 5 Release Notes

Updates in the latest release. 

## 6 Support or Contact

[MedCom](https://www.medcom.dk/) is responsible for this page.  
For any question regaring the standard, please contact <fhir@medcom.dk>