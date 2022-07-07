# New to FHIR ?

[Return to frontpage](../../index.md)

The purpose of this section is to give a introduction to MedComs FHIR standards to stakeholders with no or limited knowledge about FHIR. On this page you will find a brief introduction, most frequently used terms, descriptions that addresses some often asked questions and guiding to more information about FHIR and MedComs FHIR standards. 


**Table of Content**
- [FHIR Glossary](#fhir-glossary)
- [Frequently asked questions]()
- [How to Read a MedCom Implementation Guide](#how-to-read-a-medcom-implementation-guide)
- [Why are there Multiple Implementation Guides](#why-are-there-multiple-implementation-guides)
- [How does Inheritance Work and What is DKCore](#how-does-inheritance-work-and-what-is-dkcore)
- [More information](#more-information)
  * [Webinars](#webinars)
  * [HL7 FHIR Documentation](#hl7-fhir-documentation)
<p>&nbsp;</p> 

## FHIR Glossary
<a href="https://www.hl7.org/fhir/" target="_blank">Fast Healthcare Interoperability Resources (FHIR&reg;&copy;)</a> is developed by the international organization Health Level 7 (HL7) and is an open-source standard developed to exchange healthcare-related information. FHIR defines several resources, often referred to as ‘building blocks’, each describing a delimited area within healthcare e.g., a Patient or an Encounter. These resources are generic and can therefore be used across the world. However, when using the resources in a specific context, such as communication between Danish healthcare parties, the resources need to be profiled to accommodate the use. The profiling could be to require at last name of a Patient. In some cases, it is necessary to extend the generic resources to fit the context e.g., to add a CPR-number as a patient identifier.

When creating a MedCom FHIR standard, multiple profiles are assembled to include the information necessary to support the business requirements. Under the auspices of MedCom, these profiles will most often come from multiple Implementation Guides (IG). This decision is further addressed in the section [Why does Multiple Implementation Guides Exists?](#why-are-there-multiple-implementation-guides). 

The first wave of MedComs modernization only includes messages, which means that there always shall be a sender and a receiver. However, the optimal format for a standard will be considered when modernizing the next wave of MedCom standards. Another relevant format could be to upload data as services or as documents where multiple receivers can get access to data or documents. If another exchange format is to be used, it is possible to reuse the profiles from the Core IG. This is an example of FHIRs reusability across. 

In the table below you’ll find the most common terms and associated descriptions, and examples. These terms all describe a fundamental feature in FHIR, and they make the foundation to understand FHIR, and why they are presented initially.

> Note: the table below uses FHIR-paths to describe exactly which element that is refered to. E.g Patient.name referres to the name-element in the Patient resource.

<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;}
.tg td{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  overflow:hidden;padding:10px 5px;word-break:normal;}
.tg th{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  font-weight:normal;overflow:hidden;padding:10px 5px;word-break:normal;}
.tg .tg-l3yj{background-color:#FFF;border-color:#000000;color:#333333;text-align:left;vertical-align:top}
.tg .tg-ztr9{border-color:#000000;color:#2c415c;font-weight:bold;text-align:left;vertical-align:top}
.tg .tg-7j3r{border-color:#000000;color:#333333;font-weight:bold;text-align:left;vertical-align:top}
.tg .tg-on52{border-color:#000000;color:#333333;text-align:left;vertical-align:top}
</style>
<table class="tg">
<thead>
  <tr>
    <th class="tg-14zz">Term</th>
    <th class="tg-14zz">Description</th>
    <th class="tg-14zz">Example</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-mxcs"><span style="font-weight:bold">Implementation Guide (IG)</span></td>
    <td class="tg-acii">The technical specification of a MedCom FHIR standard. A set of rules and associated documentation describing, how FHIR profiles should be implemented to accommodate a given standard and requirements.</td>
    <td class="tg-tg7p">All IG's are available in <a href="https://medcomdk.github.io/MedComLandingPage/assets/documents/NewToFHIR.html#1-medcoms-fhir-messaging-standards" target="_blank" rel="noopener noreferrer"><span style="text-decoration:none">MedComs FHIR standards</span></a>.</td>
  </tr>
  <tr>
    <td class="tg-i91a"><span style="font-weight:bold">Resources</span></td>
    <td class="tg-i91a">FHIR consists of generic resources, each describing a clinically delimited area. Resources are 'building blocks' defined by HL7.</td>
    <td class="tg-i91a">A Patient resource, an Allergy resource, an Observation resource, an Encounter resource ect.</td>
  </tr>
  <tr>
    <td class="tg-i91a"><span style="font-weight:bold">Element</span></td>
    <td class="tg-i91a">A resource consists of multiple elements each describing a specific part of the content.</td>
    <td class="tg-i91a">Patient.name or Patient.address.</td>
  </tr>
  <tr>
    <td class="tg-i91a"><span style="font-weight:bold">Cardinality</span></td>
    <td class="tg-i91a">Each element is described with a minimum and maximum cardinality, describing how many times an element may or shall appear.<br>If the minimum cardinality is 0, the element may appear and if it is 1 or more the element shall at least appear the number of times stated.<br>If the maximum cardinality is 0 the element must not appear, 1 the element may not appear more than once and if it is * the element may appear several times.<br></td>
    <td class="tg-i91a">In the generic resource Patient.name has the cardinality 0..*, meaning a patient may have zero or more names.<br>In the generic resource Encounter.status has the cardinality 1..1, meaning that a status always shall appear, and in may only appear once.</td>
  </tr>
  <tr>
    <td class="tg-i91a"><span style="font-weight:bold">Profiling</span></td>
    <td class="tg-i91a">To fit a resource to a given context. It is widely recognized that when exchanging data it is impossible to make a one size fits all within healthcare worldwide.<br>To accommodate this, the resources made generic with the possibility to be profiled to fit a specific context, such as exchanging a CareCommunication message between Danish healthcare parties.</td>
    <td class="tg-i91a">Profiling could be to require a lastname and an identifier of a patient or citizen when exchanging information about the person.</td>
  </tr>
  <tr>
    <td class="tg-i91a"><span style="font-weight:bold">Extensions</span></td>
    <td class="tg-i91a">To extend a resource to include additional information than defined by HL7. </td>
    <td class="tg-i91a">Extending the Patient resource with a CPR-number. As this is unique in Denmark, the generic Patient resource does not include it as a patient identifier.</td>
  </tr>
  <tr>
    <td class="tg-i91a"><span style="font-weight:bold">CodeSystem</span></td>
    <td class="tg-i91a">A collection of codes, which can be predetermined by HL7, from a international terminology or defined by the developer of the IG.</td>
    <td class="tg-i91a">Predetermined by HL7 e.g. <a href="http://hl7.org/fhir/valueset-administrative-gender.html" target="_blank" rel="noopener noreferrer"><span style="text-decoration:none">gender</span></a>, from a international terminology e.g. <a href="https://browser.ihtsdotools.org/?" target="_blank" rel="noopener noreferrer"><span style="text-decoration:none">SNOMED CT </span></a>,or defined by the developer of the IG e.g. <a href="https://build.fhir.org/ig/medcomdk/dk-medcom-carecommunication/CodeSystem-medcom-careCommunication-categoryCodes.html" target="_blank" rel="noopener noreferrer"><span style="text-decoration:none">categories </span></a>categories in a CareCommunication message.</td>
  </tr>
  <tr>
    <td class="tg-i91a"><span style="font-weight:bold;background-color:#FFF">ValueSet</span></td>
    <td class="tg-i91a">A collection of codes from one or more CodeSystems. ValueSets can either include all codes from a CodeSystem or only some codes.</td>
    <td class="tg-i91a"><a href="https://build.fhir.org/ig/hl7dk/dk-medcom-messaging/ValueSet-medcom-messaging-messageTypes.html" target="_blank" rel="noopener noreferrer"><span style="text-decoration:none">MedComMessagingMessageTypes</span></a>    is a ValueSet that includes all codes from the <a href="https://build.fhir.org/ig/hl7dk/dk-medcom-messaging/CodeSystem-medcom-messaging-eventCodes.html" target="_blank" rel="noopener noreferrer"><span style="text-decoration:none">MedComMessagingEvents</span></a> CodeSystem. The ValueSet includes the codes for MedComs FHIR standards</td>
  </tr>
  <tr>
    <td class="tg-i91a"><span style="font-weight:bold">MustSupport</span></td>
    <td class="tg-i91a">Indicates which information which shall be included in a MedCom standard if available in the sender systemer and which information the receiver system shall be able to handle. MustSupport is defined during profiling of the resource.</td>
    <td class="tg-i91a">The elements Patient.identifier, Patient.name and Patient.address does all have the flag MustSupport in the MedComCorePatient profile.</td>
  </tr>
  <tr>
    <td class="tg-osjb"><span style="font-weight:bold">Modifier</span></td>
    <td class="tg-ujx6">An element which modifies or changes the understanding of the resource. '!?' indicates in the IG that the element is a modifier element, which is often defined in the generic resource or in developed extensions</td>
    <td class="tg-ujx6">Patient.deceased is a modifier element, since is modifies the way the content of the profile should be understood, if the patient is deceased.</td>
  </tr>
  <tr>
    <td class="tg-i91a"><span style="font-weight:bold">Narrative</span></td>
    <td class="tg-i91a"> A textual summary of the information   in a message which can be   used to display information if the structured data cannot be displayed. All   information in a message shall be included in the summary. <br>Description:    </td>
    <td class="tg-i91a">All content from a message, including the patients name or CPR-number and the written correspondence in a CareCommunication message.</td>
  </tr>
</tbody>
</table>




## How to Read a MedCom Implementation Guide

If you are interested in understanding the basic content and the composition of an IG, you can follow this [step-by-step guide](FHIRImplementationGuide.md).

## Frequentlyasked qestions
### Why are there Multiple Implementation Guides

FHIR allows for a great deal of reuse. When creating a MedCom FHIR message, profiles from the MedComCore and MedComMessaging IG are used to create a complete understanding. Currently, there are three FHIR standards: HospitalNotification, CareCommunication and Acknowledgement, which all are composed of profiles from the Core -, and Messaging-IG as well as the IG for the specific standard, and codes from the Terminology IG. 

Keeping the IGs seperat allows to version them individually, so updates in the MedComHospitalNotification IG won’t affect the version of the MedComCareCommunication IG. However, an update in the MedComMessaging IG will affect all standards that uses profiles or inherit profiles from this IG. 
Additionally, it makes it possible to reuse the profiles from the Core IG in different MedCom standard and in different exchange formats. 

The figure below illustrates that the messaging standard use multiple of the profiles from the Core and Messaging IG and uses some profiles that are specific for the given standard. 
![MD](../images/MultipleIGs.png)

 

### How does Inheritance Work and What is DKCore
In Denmark we have a national HL7 affiliate, called <a href="https://hl7.dk/" target="_blank">HL7-DK</a>. The affiliate works on development of international HL7 standards that supports healthcare. HL7-DK has focus on profiling the international standard to Danish context to provide a common foundation in Denmark.  HL7-DK develops DK-core which is generic FHIR profiles that can be used freely for FHIR project in Denmark. At present DK-core includes the following profiles: DkCorePatient, DkCorePractitioner and DkCoreOrganization. The profile MedComCorePatient inherits from <a href="https://hl7.dk/fhir/core/1.1.0/StructureDefinition-dk-core-patient.html" target="_blank">DKCorePatient</a>. This means that when a MedCom standard uses a CPR-number from DKCorePatient, it is defined in the same way as when other projects inherit from DK-core and uses a CPR-number, securing consistency across projects. DKCorePatient is the foundation of MedComCorePatient, why MedComCorePatient is said to inherit from DKCorePatient.
The figure below illustrates the inheritance of profiles. 
![MD](../images/WhatisDKCore.png)

The figure also illustrates that there is a dependency between the IGs and the FHIR resources defined by HL7. <a href="https://www.medcom.dk/standarder/moderniseringsnyheder/nyhedsbrev-29-november-2021" target="_blank">You can read more about the work of HL7-DK here</a>. 


## More information

### Webinars
In 2022 MedCom has held a two webinars concerning the modernization of MedCom standards. Both webinars freely available and in Danish:
* <a href="https://www.youtube.com/watch?v=8doBKskz3J8" target="_blank">FHIR-introduktionswebinar (17. maj 2022)</a>
* <a href="https://www.youtube.com/watch?v=bfzx7U2Suug" target="_blank">FHIR demo-webinar med MedCom, Mjølner og Trifork (10 . februar 2022)</a>

### HL7 FHIR Documentation

All FHIR documentation can be found at <a href="https://www.hl7.org/fhir/" target="_blank">www.hl7.org/fhir/</a>. Here you will find detailed describtions about basic principles, presentation to all resources and much more. 