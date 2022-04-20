# Welcome to MedCom FHIR Messaging

- [Welcom to MedCom FHIR Messaging](#welcom-to-medcom-fhir-messaging)
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

Here you will find the information you need to get started with MedCom's FHIR standards. To get more information about each standard, please click on the pages below. All webpages are in English, unless other specified.

| Name in English | Name in Danish |                            Short description                      |
|:---------------:|:--------------:|:-----------------------------------------------------------------:|
| Core | Kerneprofiler  | Core profiles that are static and used across standards.             |
| Messaging | Medddelsesprofiler | Messaging profiles used across all messaging-based standards.             |
| Acknowledgement | Kvittering  | When a message is received an acknowledgement message shall be returned to the sender, stating if the message was received properly.             |
| [HospitalNotification](https://tmsmedcom.github.io/GitHubPagesTest/) | [Sygehusadvis](https://tmsmedcom.github.io/GitHubPagesTest/) | Used to inform municipalities about hospitalization of a patient             |
| CareCommunication | Korrespondancemeddelelse | Used in all parts of the Danish health care sector to communicate between parties.             |

## 1 Clinical Introduction to FHIR

[Fast Healthcare Interoperability Resources (FHIR&reg;&copy;)](https://www.hl7.org/fhir/) is developed by the international organization Health Level 7 (HL7) and is an open-source standard developed to exchange healthcare related information. <br> 
This introduction is amied for people with limited insigth into FHIR. First, the most common _FHIR-words_ are presented followed by a short introduction to a MedCom Implementation Guide (IG). 

### 1.1 Glossary

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
    <td class="tg-fspy"><span style="font-weight:bold">Must Support:</span></td>
    <td class="tg-t6hh">Indicates which information which shall be included in a MedCom standard if available in the sender systemer and which information the receiver system shall be able to handle. Read more in "Syn&amp;Kom..."</td>
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


### 1.2 How to Read a MedCom Implementation Guide

This guide takes its starting point in [MedComCore IG](https://build.fhir.org/ig/hl7dk/dk-medcom-core/). 

* Go to [MedComCore IG](https://build.fhir.org/ig/hl7dk/dk-medcom-core/).
* On the landingpage you'll find a short introduction to the IG, in this case the MedComCore profiles. 
    * The topbar on the page includes multiple options: 
    ![Content](/assets/images/IG-content.png)
* Click on the tab [Profiles](https://build.fhir.org/ig/hl7dk/dk-medcom-core/profiles.html) you'll get an overview of the profiles in the IG. 
    * Choose [MedComCorePatient](https://build.fhir.org/ig/hl7dk/dk-medcom-core/StructureDefinition-medcom-core-patient.html). _Please notice: a MedComCorePatient describes both a patient and a citizen._ Here you'll find a short introduction to the profile and a table including five tabs, where three are of special interest: 
    ![Profile Content](/assets/images/ProfileContent.png)
        * Click on the tab 'Snapshot Table (MustSupport)'. Here is all required content for the profil gathered. The table contains five headlines
            * Name
                * The element name.
            * Cardinality (Card):
                * Given the minimum cardinality of 1 for Patient.identifier and Patient.name the information for these elements shall always be included when exchanging a MedCom standard. Not only shall a Patient.name be included, it shall always be the patients offical name, indicated by Patient.name:Official. Information about Patient.telecom, Patient.deceased, Patient.address and Patient.managingOrganization shall be included if the information is available in the sender system, given the minimum cardinality of 0. 
                * Given the maximum cardinality of * for Patient.identifier, Patient.name, Patient.telecom and Patient.address it is allowed to slice the element. For the element Patient.deceased it is only allowed to include the information once. 
            * Flags: 
                * I = a rule, which can be seen further down the page.
                * &sum; = if the element shall be included in the narrativ. 
                * ?! = modifier element, an element which potentially can modify the understanding of an entire message
            * Type: 
                * Describes the datatype of the element. Click on them for more information about the datatype. 
                * One migth notice the type at the top of the elements says _DKCorePatient_, which means that the MedComCorePatient inherits from a Patient profile developed by the Danish HL7 affiliate. You can read more about the work under '[How does Inheritance work and what is DKCorePatient?](#how-does-inheritance-work-and-what-is-dk-core-profiles)'.
            * Description and Constraints
                * A short description of the element as well as rules associated with the element. 
    * Now, try choosing the profile [MedComCoreEncounter](https://build.fhir.org/ig/hl7dk/dk-medcom-core/StructureDefinition-medcom-core-encounter.html)
        * Here you'll see the type Reference(...) at the element Encounter.subject. This means that the element references the MedComCorePatient profile, and that an encounter always shall be associated with a patient. 
        * For the elements Encounter.status and Encounter.class the type is code or coding, meaning that a predefined, structured code shall be selected from a ValueSet. which can be seen in the column 'Description & Constraints'.  
* The tab [Extensions](https://build.fhir.org/ig/hl7dk/dk-medcom-core/extensions.html) shows the extensions made for the IG. 
* The tab [Terminology](https://build.fhir.org/ig/hl7dk/dk-medcom-core/terminology.html) shows the CodeSystems and ValueSets used in the IG.
* The tab [Artifacts](https://build.fhir.org/ig/hl7dk/dk-medcom-core/artifacts.html) shows entire content of the IG.


#### 1.2.1 Why are there Multiple Implementation Guides?

FHIR allows for a great deal of reuse. When creating a MedCom message, profiles from the MedComCore and MedComMessaging IG are used, as illustrated on the figure below. ![Overview](/assets/images/Overview-IGs.png)
Keeping the IGs seperat allow to versioning each one of them, so updates in the MedComHospitalNotification IG won't affect the version of the MedComCareCommunication IG.  However an update in the MedComMessaging IG will affect all standards that uses profiles or inherit profiles from this IG. 
For more information about versioning see HERE.. (is coming.)

#### 1.2.2 How does Inheritance work and what is DKCorePatient? 

Just like profiling of resources, it is possible to take a generic profile and specify it to a given context. For example is a [MedComCoreOrganization](https://build.fhir.org/ig/hl7dk/dk-medcom-core/StructureDefinition-medcom-core-organization.html) determined to include a SOR-code and possible a name of the organization. When using an organization in a messaging context, it is determined that a [MedComMessagingOrganization](https://build.fhir.org/ig/hl7dk/dk-medcom-messaging/StructureDefinition-medcom-messaging-organization.html) further shall include an EAN/GLN-number. However, MedComMessagingOrganization is based on the profiling of MedComCoreOrganization and is therefore said to inherit from this profile. <br>
In Denmark there is a national HL7 affiliate, called HL7-DK. A special FHIR-interest group develops what is called DK-core profiles, generic FHIR profiles which can be used freely for FHIR project in Denmark. MedComCorePatient inherits from [DKCorePatient](https://hl7.dk/fhir/core/1.1.0/StructureDefinition-dk-core-patient.html). This means that when a MedCom standard uses a CPR-number from DKCorePatient, it is defined in the same way as when other projects inherit from DK-core and uses a CPR-number, securing consistentcy across projects. You can read more about the work of HL7-DK [here](https://www.medcom.dk/standarder/moderniseringsnyheder/nyhedsbrev-29-november-2021). 

### 1.3 Relevant pages

Is coming...

## 2 Information about the Transportation Layer

See [here](/assets/documents/MedComs_FHIR-meddelelser_og_forsendelseskuvert.md)


## 3 Test and Certification

Link to MedCom testCenter. 

Link to FHIR validator 

Link to GettingStarted with TouchStone 

## 4 Release Notes

Updates in the latest release. 

## 5 Support or Contact

[MedCom](https://www.medcom.dk/) is responsible for this page.  
For any question regaring the standard, please contact <fhir@medcom.dk>