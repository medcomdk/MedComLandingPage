# Welcom to MedCom FHIR Messaging

1. [1 Clinical Introduction to FHIR](#1-clinical-introduction-to-fhir)
    1. [1.1 Glossary](#11-glossary)
    2. [1.2 How to Read a MedCom Implementation Guide](#12-how-to-read-a-medcom-implementation-guide)
        1. [1.2.1 Why have MedCom made Multiple Implementation Guides?](#121-why-have-medcom-made-multiple-implementation-guides)
    3. [1.3 Relevant pages](#13-relevant-pages)

Here you will find the information you need to get started with MedCom's FHIR standards. 

| Name in English | Name in Danish |                            Short description                      |
|:---------------:|:--------------:|:-----------------------------------------------------------------:|
| Core | Kerneprofiler  | Core profiles that are static and used across standards.             |
| Messaging | Medddelsesprofiler | Messaging profiles used across all messaging-based standards.             |
| Acknowledgement | Kvittering  | When a message is received an acknowledgement message shall be returned to the sender, stating if the message was received properly.             |
| [HospitalNotification](https://tmsmedcom.github.io/GitHubPagesTest/) | [Sygehusadvis](https://tmsmedcom.github.io/GitHubPagesTest/) | Used to inform municipalities about hospitalization of a patient             |
| CareCommunication | Korrespondancemeddelelse | Used in all parts of the Danish health care sector to communicate between parties.             |

## 1 Clinical Introduction to FHIR

[Fast Healthcare Interoperability Resources (FHIR)](https://www.hl7.org/fhir/) is an open-source standard developed to exchange healthcare-related information and is developed by the international organization Health Level 7 (HL7). <br> 
This introduction is amied for people with limited insigth into FHIR. First the most common _FHIR-words_ are presented followed by a short introduction to an Implementation GUide (IG). 

### 1.1 Glossary

|  Word  |  Describtion  |
|:------:|:-------------:|
|  Resources:  | FHIR consists of generic resources, each describing a clinically delimited area, e.g. a Patient, an Allergy, an Observation, an Encounter, ect. The resouces are generic and can be used all over the world. |
|  Profiling:  | Means to fit the resources to a given context. It is widely recognized that when exchanging data it is impossible to make a _one size fits all_ within the healthcare worldwide. Therefore are the resources made generic with the possibility to be profiled to a given context, such as exchanging a CareCommunication message between Danish healthcare parties. An example of profiling could be to require a lastname and an identifier (Danish: "Det Centrale Personregister" (CPR)-number) of a patient/citizen when exchanging information about the person. |
|  Extensions:  | To extend a profile means to include additional information. For example is a cpr-number of a citizen only relevant in Denmark and is therefore not a part of the genieric Patient resource. To include a CPR-number, an extension must be made. |
|  Element:  | A resource, hence a profile consists of multiple elements each describing a specific part of the content, like a patient name og adress. |
|  Cardinality:  | Each element is describes with a minimum and maximum cardinality. If the minimum cardinality is 0, the element may appear and if it is 1 or more the element shall appear the number of times stated. If the maximum cardinality is 0 the element must not appear, 1 the element may not appear more than once and if the maximum cardinality is * the element may appear several times. Changing the cardinality within the predefined limits is a part of the profilling.|
|  Must Support:  | Indicates which information which shall be included in a MedCom standard if available in the sender systemer and which information the receiver system shall be able to handle. Read more in "Syn&Kom..." + Henvisning |
|  CodeSystem:  | A collection of codes, which can be predetermined by HL7 e.g. [gender](http://hl7.org/fhir/R4/valueset-administrative-gender.html), from a international terminology e.g. [SNOMED CT](https://browser.ihtsdotools.org/?) or defined by the developer of the IG e.g. [categories in a CareCommunication message](https://build.fhir.org/ig/hl7dk/dk-medcom-carecommunication/CodeSystem-medcom-careCommunication-categoryCodes.html).  |
|  ValueSet:  | A collection of codes from one or more CodeSystems. ValueSet are referenced from elements in IG. |
|  Narrative:  | A summary of the most important information in a standard.  |
|  Implementation Guide (IG):  | A set of rules and associated documentation describing how FHIR profiles should be used to accommodate a given standard. |
<!-- 
__Resources:__ FHIR consists of generic resources, each describing a clinically delimited area, e.g. a Patient, an Allergy, an Observation, an Encounter, ect. The resouces are generic and can be used all over the world.<br>
__Profiling:__ Means to fit the resources to a given context. It is widely recognized that when exchaning data it is impossible to make a _one size fits all_ within healthcare worldwide. Therefore are the resources made generic with the possibility to be profiled to fit a given context, such as exchanging a CareCommunication message between Danish healthcare parties. An example of profiling could be to require a lastname and an identifier (a cpr.-number) of a patient when exchanging information about the person.<br>
To create a MedCom FHIR standard it is nessecary to select multiple relevant resources and profile these to the context. <br>
__Extensions:__ To extend a profile to include additional information. For example is cpr-number of a citizen only relevant in Denmark and is therefore not a part of the genieric Patient resource. To include a cpr-number, an extension must be made. <br>
__Must Support:__ Indicates which information which shall be included in a MedCom standard if available in the sender systemer and which information the receiver system shall be able to handle. Read more in "Syn&Kom..."<br>
__Element:__ A resource, hence a profile consists of multiple elements each describing a specific part of the content, like a patient name og adress.  <br>
__Cardinality:__ Each element is describes with a minimum and maximum cardinality (abreviation in the IG: Card). If the minimum cardinality is 0, the element may appear and if it is 1 or more the element shall appear the number of times stated. If the maximum cardinality is 0 the element must not appear, 1 the element not not appear more than once and if it is * the element may appear several times. <br>
__Implementation Guide (IG):__ A set of rules and associated documentation describing how FHIR profiles should be used to accommodate a given standard.  -->

### 1.2 How to Read a MedCom Implementation Guide

This guide is founded in the [MedComCore IG](https://build.fhir.org/ig/hl7dk/dk-medcom-core/). 

* On the [landingpage of the IG](https://build.fhir.org/ig/hl7dk/dk-medcom-core/) you'll find a short introduction to IG, in this case the MedComCore profiles. 
    * The topbar on the page includes multiple options: 
    ![Content](/assets/images/IG-content.png)
* Click on the tab [Profiles](https://build.fhir.org/ig/hl7dk/dk-medcom-core/profiles.html) you'll get an overview of the profiles in the IG. 
    * Choose [MedComCorePatient](https://build.fhir.org/ig/hl7dk/dk-medcom-core/StructureDefinition-medcom-core-patient.html). Here you'll find a short introduction and a table including four tabs: 
    ![Profile Content](/assets/images/ProfileContent.png)
    * Under the tab 'Snapshot Table (MustSupport)' all the required content is gathered. 
        * Cardinality (Card):
            * Given the minimum cardinality of 1 for Patient.identifier and Patient.name the information for these elements shall always be included when exchanging a MedCom standard. Information about Patient.telecom, Patient.deceased, Patient.address and Patient.managingOrganization shall be included if the information is available in the sender system, given the minimum cardinality of 0. 
            * Given the maximum cardinality of * for Patient.identifier, Patient.name, Patient.telecom and Patient.address it is allowed to include more than one instance of the element, e.g. a home number and celphone number or an official name and a nickname. For the element Patient.deceased it is only allowed to include the information once. 
        * Flags: 
            * I = a rule, which can be seen further down the page
            * &sum; = information in the element shall be included in the narrative
            * ?! = modifier element, an element which potentially can modify the understanding of an entire message
        * Type: 
            * Describes the datatype of the element. Click on them for more information about the datatype. 
            * One migth notice the type at the top of the elements says _DKCorePatient_, which means that the MedComCorePatient inherits from a Patient profile developed by the Danish HL7 affiliate. You can read more about the work under '[How does Inheritance work and what is DKCorePatient?](#how-does-inheritance-work-and-what-is-dk-core-profiles)'.
    * Now, try choosing the [MedComCoreEncounter](https://build.fhir.org/ig/hl7dk/dk-medcom-core/StructureDefinition-medcom-core-encounter.html)
        * Here you'll see the type Reference(...) at the element subject. This means that the element references the MedComCorePatient profile, and that an encounter always shall be associated with a patient or citizen. 
        * For the elements Encounter.status and Encounter.class the type is code or coding, meaning that a predefined, structured code shall be selected from a value set, which can be seen in the column 'Description & Constraints'.  
* The tab [Extensions](https://build.fhir.org/ig/hl7dk/dk-medcom-core/extensions.html) shows the extensions made for the IG. 
* The tab [Terminology](https://build.fhir.org/ig/hl7dk/dk-medcom-core/terminology.html) shows the CodeSystems and ValueSets used in the IG.
* The tab [Artifacts](https://build.fhir.org/ig/hl7dk/dk-medcom-core/artifacts.html) shows entire content of the IG.


#### 1.2.1 Why have MedCom made Multiple Implementation Guides?

![Overview](/assets/images/Overview-IGs.png)

#### 1.2.2 How does Inheritance work and what is DKCorePatient? 

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