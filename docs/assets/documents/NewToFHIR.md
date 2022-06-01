# New to FHIR?

The purpose of this section is to give a brief introduction to MedComs FHIR standards to stakeholders with limited knowledge about FHIR, who wants to know more.
<a href="https://www.hl7.org/fhir/" target="_blank">Fast Healthcare Interoperability Resources (FHIR&reg;&copy;)</a> is developed by the international organization Health Level 7 (HL7) and is an open-source standard developed to exchange healthcare related information.

**Table of Content**
- [FHIR Glossary](#fhir-glossary)
- [How to Read a MedCom Implementation Guide](#how-to-read-a-medcom-implementation-guide)
- [Why are there Multiple Implementation Guides](#why-are-there-multiple-implementation-guides)
- [How does Inheritance Work and What is DKCore](#how-does-inheritance-work-and-what-is-dkcore)
- [More information](#more-information)
  * [Webinars](#webinars)
  * [HL7 FHIR Documentation](#hl7-fhir-documentation)
  
## FHIR Glossary

In the table below you'll find the most common words and associated descriptions, and examples. These words all describes a fundamental feature in FHIR, and they make the foundation to understand FHIR, why they are presented initially. 

> Note: the table below uses FHIR-paths to describe exactly which element that is refered to. E.g Patient.name referres to the name-element in the Patient resource.

<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;max-width:80%;}
.tg td{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  overflow:hidden;padding:10px 5px;word-break:normal;}
.tg th{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  font-weight:normal;overflow:hidden;padding:10px 5px;word-break:normal;}
.tg .tg-4py2{border-color:#343434;color:#343434;text-align:left;vertical-align:top}
.tg .tg-ltzd{border-color:#343434;color:#343434;font-weight:bold;text-align:left;vertical-align:top}
.tg .tg-z1n8{background-color:#FFF;border-color:#343434;color:#343434;font-weight:bold;text-align:center;vertical-align:top}
.tg .tg-c75y{background-color:#FFF;border-color:#343434;color:#343434;font-weight:bold;text-align:left;vertical-align:top}
.tg .tg-pkxh{background-color:#FFF;border-color:#343434;color:#343434;text-align:left;vertical-align:top}
</style>
<table class="tg">
<thead>
  <tr>
    <th class="tg-z1n8"><span style="font-weight:bold">Word</span></th>
    <th class="tg-c75y"><span style="font-weight:bold">Describtion</span></th>
    <th class="tg-4py2"><span style="font-weight:bold">Example</span></th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-c75y"><span style="font-weight:bold">Resources:</span></td>
    <td class="tg-pkxh"><span style="background-color:#FFF">FHIR consists of generic resources, each describing a clinically delimited area. Resources are 'building blocks' defined by HL7.</span></td>
    <td class="tg-4py2">A Patient resource, an Allergy resource, an Observation resource, an Encounter resource ect. </td>
  </tr>
  <tr>
    <td class="tg-c75y"><span style="font-weight:bold">Element:</span></td>
    <td class="tg-pkxh"><span style="background-color:#FFF">A resource consists of multiple elements each describing a specific part of the content.</span></td>
    <td class="tg-4py2">Patient.name or Patient.address.</td>
  </tr>
  <tr>
    <td class="tg-c75y"><span style="font-weight:bold">Cardinality:</span></td>
    <td class="tg-pkxh"><span style="background-color:#FFF">Each element is described with a minimum and maximum cardinality, describing how many times an element may or shall appear.</span><br><span style="background-color:#FFF">If the minimum cardinality is 0, the element may appear and if it is 1 or more the element shall at least appear the number of times stated.</span><br><span style="background-color:#FFF">If the maximum cardinality is 0 the element must not appear, 1 the element may not appear more than once and if it is * the element may appear several times.</span><br></td>
    <td class="tg-4py2">In the generic resource Patient.name has the cardinality 0..*, meaning a patient may have zero or more names.<br>In the generic resource Encounter.status has the cardinality 1..1, meaning that a status always shall appear, and in may only appear once.</td>
  </tr>
  <tr>
    <td class="tg-c75y"><span style="font-weight:bold">Profiling:</span></td>
    <td class="tg-pkxh"><span style="background-color:#FFF">To fit a resource to a given context. It is widely recognized that when exchanging data it is impossible to make a</span> <span style="font-style:italic">one size fits all</span> <span style="background-color:#FFF">within healthcare worldwide.</span><br><span style="background-color:#FFF">To accommodate this, the resources made generic with the possibility to be profiled to fit a specific context, such as exchanging a CareCommunication message between Danish healthcare parties.</span></td>
    <td class="tg-4py2">Profiling could be to require a lastname and an identifier of a patient or citizen when exchanging information about the person.</td>
  </tr>
  <tr>
    <td class="tg-c75y"><span style="font-weight:bold">Extensions:</span></td>
    <td class="tg-pkxh"><span style="background-color:#FFF">To extend a resource to include additional information than defined by HL7. Defining extensions are usually a part of the profiling. </span></td>
    <td class="tg-4py2">Extending the Patient resource with a CPR-number. As this is unique in Denmark, the generic Patient resource does not include it as a patient identifier.</td>
  </tr>
  <tr>
    <td class="tg-c75y"><span style="font-weight:bold">CodeSystem:</span></td>
    <td class="tg-pkxh"><span style="background-color:#FFF">A collection of codes, which can be predetermined by HL7, from a international terminology or defined by the developer of the IG.</span></td>
    <td class="tg-4py2">Predetermined by HL7 e.g. gender, from a international terminology e.g. SNOMED CT or defined by the developer of the IG e.g. categories in a CareCommunication message.</td>
  </tr>
  <tr>
    <td class="tg-c75y"><span style="font-weight:bold;background-color:#FFF">ValueSet:</span></td>
    <td class="tg-pkxh"><span style="background-color:#FFF">A collection of codes from one or more CodeSystems. ValueSets can either include all codes from a CodeSystem or only some codes. </span></td>
    <td class="tg-4py2">A ValueSet defined by MedCom is <a href="https://build.fhir.org/ig/hl7dk/dk-medcom-messaging/ValueSet-medcom-messaging-messageTypes.html" target="_blank">MedComMessagingMessageTypes</a>, which includes all codes from the CodeSystem called <a href="https://build.fhir.org/ig/hl7dk/dk-medcom-messaging/CodeSystem-medcom-messaging-eventCodes.html" target="_blank">MedComMessagingEvents</a>.</td>
  </tr>
  <tr>
    <td class="tg-c75y"><span style="font-weight:bold">MustSupport:</span></td>
    <td class="tg-pkxh"><span style="background-color:#FFF">Indicates which information which shall be included in a MedCom standard if available in the sender systemer and which information the receiver system shall be able to handle. MustSupport is defined during profiling of the resource.</span></td>
    <td class="tg-4py2">The elements Patient.identifier, Patient.name and Patient.address does all have the flag MustSupport in the MedComCorePatient profile.</td>
  </tr>
  <tr>
    <td class="tg-c75y"><span style="font-weight:bold">Narrative:</span></td>
    <td class="tg-pkxh"><span style="background-color:#FFF">A summary of the most important information in a standard. All elements with a SUMMARITION symbol in a resource or profile will be automatically included in the narrative. SUMMARARIOn can be defined in the generic resource or during the profiling.</span></td>
    <td class="tg-4py2">In the generic Patient resource Patient.identifier and Patient.name are both included in the narrative.</td>
  </tr>
  <tr>
    <td class="tg-ltzd">Modifier:</td>
    <td class="tg-4py2">An element which modifies or changes the understanding of the resource. All modifier elements are indicates with '!?', which can be defines in the generic resource or during the profiling.</td>
    <td class="tg-4py2">Patient.deceased is a modifier element, since is modifies the way the content of the profile should be understood, if the patient is deceased. </td>
  </tr>
  <tr>
    <td class="tg-c75y"><span style="font-weight:bold">Implementation Guide (IG):</span></td>
    <td class="tg-pkxh"><span style="background-color:#FFF">The technical specification of a MedCom FHIR standard. A set of rules and associated documentation describing, how FHIR profiles should be implemented to accommodate a given standard and requirements.</span></td>
    <td class="tg-4py2">All IG's are available in <a href="#1-medcoms-fhir-messaging-standards">section 1</a>. </td>
  </tr>
</tbody>
</table>

## How to Read a MedCom Implementation Guide

If you are interested in understanding the basic content and the composition of an IG, you can follow this [step-by-step guide](/docs/assets/documents/FHIRImplementationGuide.md).


## Why are there Multiple Implementation Guides

FHIR allows for a great deal of reuse. When creating a MedCom message, profiles from the MedComCore and MedComMessaging IG are used, as illustrated on the figure below. 
![MD](../images/MultipleIGs.png)

Keeping the IGs seperat allow to versioning each one of them, so updates in the MedComHospitalNotification IG won't affect the version of the MedComCareCommunication IG.  However an update in the MedComMessaging IG will affect all standards that uses profiles or inherit profiles from this IG. 

## How does Inheritance Work and What is DKCore

In Denmark there is a national HL7 affiliate, called <a href="https://hl7.dk/" target="_blank">HL7-DK</a>. A special FHIR-interest group develops what is called DK-core profiles, generic FHIR profiles which can be used freely for FHIR project in Denmark. MedComCorePatient inherits from <a href="https://hl7.dk/fhir/core/1.1.0/StructureDefinition-dk-core-patient.html" target="_blank">DKCorePatient</a>. This means that when a MedCom standard uses a CPR-number from DKCorePatient, it is defined in the same way as when other projects inherit from DK-core and uses a CPR-number, securing consistentcy across projects. DKCorePatient is the foundation of MedComCorePatient, why MedComCorePatient is said to inherit from DKCorePatient.

<a href="https://www.medcom.dk/standarder/moderniseringsnyheder/nyhedsbrev-29-november-2021" target="_blank">You can read more about the work of HL7-DK here</a>. 

## More information

### Webinars
In 2022 MedCom has held a two webinars concerning the modernization of MedCom standards. Both webinars freely available and in Danish:
* <a href="https://www.youtube.com/watch?v=8doBKskz3J8" target="_blank">FHIR-introduktionswebinar (17. maj 2022)</a>
* <a href="https://www.youtube.com/watch?v=bfzx7U2Suug" target="_blank">FHIR demo-webinar med MedCom, Mjølner og Trifork (10 . februar 2022)</a>

### HL7 FHIR Documentation

All FHIR documentation can be found at <a href="https://www.hl7.org/fhir/" target="_blank">www.hl7.org/fhir/</a>. Here you will find detailed describtions about basic principles, presentation to all resources and much more. 