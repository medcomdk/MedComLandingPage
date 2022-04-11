# Welcom to MedCom FHIR Messaging

Here you will find the information you need to get started with MedCom's FHIR standards. 

| Name in English | Name in Danish |                            Short description                      |
|:---------------:|:--------------:|:-----------------------------------------------------------------:|
| Core | Kerneprofiler  | Core profiles that are static and used across standards.             |
| Messaging | Medddelsesprofiler | Messaging profiles used across all messaging-based standards.             |
| Acknowledgement | Kvittering  | When a message is received an acknowledgement message shall be returned to the sender, stating if the message was received properly.             |
| [HospitalNotification](https://tmsmedcom.github.io/GitHubPagesTest/) | [Sygehusadvis](https://tmsmedcom.github.io/GitHubPagesTest/) | Used to inform municipalities about hospitalization of a patient             |
| CareCommunication | Korrespondancemeddelelse | Used in all parts of the Danish health care sector to communicate between parties.             |

## Clinical introduction to FHIR
[Fast Healthcare Interoperability Resources (FHIR)](https://www.hl7.org/fhir/) is an open-source standard developed to exchange healthcare-related information and is developed by the international organization Health Level 7 (HL7). 

### Glossary
__Resources:__ FHIR consists of generic resources, each describing a clinically delimited area, e.g. a Patient, an Allergy, an Observation, an Encounter, ect. The resouces are generic and can be used all over the world.<br>
__Profiling:__ Means to fit the resources to a given context. It is widely recognized that when exchaning data it is impossible to make a _one size fits all_ within healthcare worldwide. Therefore are the resources made generic with the possibility to be profiled to fit a given context, such as exchanging a CareCommunication message between Danish healthcare parties. An example of profiling could be to require a lastname and an identifier (a cpr.-number) of a patient when exchanging information about the person.<br>
To create a MedCom FHIR standard it is nessecary to select multiple relevant resources and profile these to the context. <br>
__Extensions:__ To extend a profile to include additional information. For example is cpr-number of a citizen only relevant in Denmark and is therefore not a part of the genieric Patient resource. To include a cpr-number, an extension must be made. <br>
__Must Support:__ Indicates which information which shall be included in a MedCom standard if available in the sender systemer and which information the receiver system shall be able to handle. Read more in "Syn&Kom..."<br>
__Element:__ A resource, hence a profile consists of multiple elements each describing a specific part of the content, like a patient name og adress.  <br>
__Cardinality:__ Each element is describes with a minimum and maximum cardinality (abreviation in the IG: Card). If the minimum cardinality is 0, the element may appear and if it is 1 or more the element shall appear the number of times stated. If the maximum cardinality is 0 the element must not appear, 1 the element not not appear more than once and if it is * the element may appear several times. <br>
__Implementation Guide (IG):__ A set of rules and associated documentation describing how FHIR profiles should be used to accommodate a given standard. 

### How to Read a MedCom Implementation Guide
This guide is founded in the MedComCore IG. 

* On the [landingpage of the IG](https://build.fhir.org/ig/hl7dk/dk-medcom-core/) you will find a short introduction to standard, in this case the MedComCore profiles. 
    * The topbar on the page includes multiple options: 
    ![Content](/assets/images/IG-content.png)
* Click on the tab ['Profiles'](https://build.fhir.org/ig/hl7dk/dk-medcom-core/profiles.html) you'll get an overview of the profiles in the IG. 
    * Choose e.g. [MedComCorePatient](https://build.fhir.org/ig/hl7dk/dk-medcom-core/StructureDefinition-medcom-core-patient.html). Here you'll find a short introduction and a table including four tabs: 
    ![Profile Content](/assets/images/ProfileContent.png)
    * 

#### Why have MedCom made Multiple Implementation Guides?
![Overview](/assets/images/Overview-IGs.png)

#### How does inheritance work and what is DK-Core-Profiles? 

### Relevant pages

## Information about the Transportation Layer

See [here](/assets/documents/MedComs_FHIR-meddelelser_og_forsendelseskuvert.md)


## Test and Certification

Link to FHIR validator 

Link to GettingStarted with TouchStone 

## Release Notes

Updates in the latest release. 

## Support or Contact

[MedCom](https://www.medcom.dk/) is responsible for this page.  
For any question regaring the standard, please contact <fhir@medcom.dk>