[Return](../../index.md)

# Governance for FHIR Validation Using MedCom FHIR Standards

**Table of contents**
* [1 Introduction](#1-introduction)
* [2 Validation in Vendor Systems](#2-validation-in-vendor-systems)
  * [2.1 FHIR Messaging - Validation Governance](#21-fhir-messaging---validation-governance)
    * [2.1.1 Sender-side validation](#211-sender-side-validation)
    * [2.1.2 Receiver-side validation](#212-receiver-side-validation)
  * [2.2 FHIR Documents - Validation Governance](#22-fhir-documents---validation-governance)
    * [2.2.1 Document source validation](#221-document-source-validation)
    * [2.2.2 Document consumer validation](#222-document-consumer-validation)
    * [2.2.3 Transition to future FHIR-based infrastructure](#223-transition-to-future-fhir-based-infrastructure)
    * [2.2.4 More information](#224-more-information)
* [3 Validation in MedCom FHIR test validation tool](#3-validation-in-medcom-fhir-test-validation-tool)


**Note:**

1) For sharing MedCom FHIR messages via the messaging infrastructure, this governance is mandatory.

2) For sharing MedCom FHIR documents via DDS (the National Document Sharing Service), this governance is currently advisory, as both the governance framework and infrastructure are still being developed and adapted to FHIR. MedCom strongly recommends early implementation, as FHIR’s built-in tools improve document quality and will support readiness when this governance becomes mandatory.

## 1 Introduction

To ensure interoperability and robustness in FHIR-based exchanges within the Danish healthcare domain, MedCom defines the following governance for validation. The governance ensures that exchanged FHIR content is syntactically valid, semantically conformant, and fully compliant with the relevant profiles.

Notice that the governance principles for MedCom FHIR Messaging differ from those for MedCom FHIR Documents, and vendors **SHALL** ensure that the appropriate rules are applied depending on the communication method.
You can read more about FHIR validation in general on HL7 FHIR’s official web page: [Validating Resources](https://hl7.org/fhir/R4/validation.html).

## 2 Validation in Vendor Systems

Vendors **SHALL** implement FHIR validation as part of their own solutions and apply it in production environments to ensure continuous conformance with MedCom’s FHIR standards.

Vendors **SHALL** use a FHIR validator that is based on an officially maintained HL7 FHIR implementation. The selected validator **SHALL** be capable of validating resources against all required Implementation Guides, including profiles, extensions, and terminology bindings. MedCom does not recommend a specific solution.

The list below shows examples of FHIR validators commonly used in the international community. The list is provided for guidance only, to help vendors identify tools suitable for their own technical environment. MedCom has not tested these validators and cannot guarantee their behaviour. MedCom encourages vendors to contact FHIR@medcom.dk with comments or suggestions regarding the list.

Notice that the validation behaviour may show minor variations between different validator implementations and programming languages - for example between C# and Java. In case of disagreement about validation results, MedCom **SHALL** be contacted via email (FHIR@medcom.dk) to clarify.

Vendors **SHALL** maintain logs for troubleshooting.

**Examples overview of Potential FHIR Validator Options**

- [Firely](https://www.nuget.org/packages/Firely.Fhir.Validation.R4)
- [HL7 International – FHIR Validator](https://confluence.hl7.org/spaces/FHIR/pages/35718580/Using+the+FHIR+Validator)
- [HAPI FHIR – Instance Validator](https://hapifhir.io/hapi-fhir/docs/validation/instance_validator.html)
- [SMILE Digital Health](https://smilecdr.com/docs/smileutil/validate.html)
- [LinuxForHealth](https://linuxforhealth.github.io/FHIR/guides/FHIRValidationGuide/)
- [AidBox – FHIR Schema Validator](https://www.health-samurai.io/docs/aidbox/modules/profiling-and-validation/fhir-schema-validator)


### 2.1 FHIR Messaging - Validation Governance

This governance applies specifically to MedCom FHIR Messaging and aligns with MedCom’s general principles for [Reliable Messaging](https://medcomdk.github.io/MedCom-FHIR-Communication/assets/documents/020_Governance-for-Reliable-Messaging-in-general.html).


#### 2.1.1 Sender-side validation

* The sender **SHALL** provide valid outgoing FHIR messages according to the relevant FHIR Implementation Guide(s) (IG) before transmission. This includes Acknowledgements.
* Messages with validation errors **SHALL NOT** be sent unless explicitly approved by the responsible authority within the sending organization.

#### 2.1.2 Receiver-side validation

* The receiver **SHALL** ensure the validity of the received incoming messages according to the relevant FHIR Implementation Guide(s) (IG) before further processing.
* Receivers **SHALL** accept non-critical warnings but **SHALL** reject messages that violate mandatory constraints and rules.
* The sender **SHALL** ensure the validity of the received incoming acknowledgements and ensure that they correctly reference the original message. If an Acknowledgement is not valid, the receiver **SHALL** contact the sending system through alternative communication channels to inform them that their acknowledgement messages are not conformant.

### 2.2 FHIR Documents - Validation Governance

This governance applies to MedCom FHIR Documents exchanged through the current national document-sharing infrastructure, which is based on IHE XDS.
The existing infrastructure does not perform FHIR validation today. Until the infrastructure is updated to support FHIR-native operations in the future, vendors **SHALL** ensure that all FHIR documents are valid.

#### 2.2.1 Document source validation

* The document source SHALL provide valid FHIR documents according to the relevant FHIR Implementation Guide(s) (IG) to the national infrastructure.
* Documents that are not valid **SHALL NOT** be submitted. 
  * In cases where the document source is unable to produce a conformant FHIR document, the document source **SHALL** prevent transmission, **SHALL** log the validation failure, **SHALL** perform internal escalation and troubleshooting, and can seek guidance from MedCom if the issue cannot be resolved locally.
  * On-demand documents: If the document source is unable to produce a conformant document, the document source **SHALL** return an error response. In the current IHE XDS-based infrastructure, the document source **SHALL** return an IHE-compliant error response structured in accordance with ITI-43 Retrieve Document Set (IHE ITI Technical Framework, Volume 3).

#### 2.2.2 Document consumer validation

* The document consumer **SHALL** ensure the validity of the received document according to the relevant FHIR Implementation Guide(s) (IG) prior to presenting it to the user.
* The document consumer **SHOULD**, as far as possible, display documents that contain validation errors. In such cases, the document consumer **SHALL** present a disclaimer indicating that the document contains error(s). The document consumer **MAY** present a clear, user-friendly explanation of the document’s contained error(s) understandable to non-technical users.
* If the document cannot be processed, the document consumer **MUST** provide an error message to the user. The document consumer **MAY** still display the narrative content to ensure that essential clinical information remains accessible to the user if possible.
* If identifiable, the relevant document source organization **SHALL** be notified, and MedCom **MAY** be notified.

#### 2.2.3 Transition to future FHIR-based infrastructure
The national infrastructure is expected to transition to a more FHIR-based architecture in the future. Work on this architecture is ongoing, and the specific design— including whether the infrastructure will perform central validation of metadata and document content, and how validation responsibilities will be shared between participants—has not yet been decided.

Until a future governance model is formally established, document source and document consumer validation remains required.

Regardless of the final architectural decisions, experiences from international FHIR implementations show that vendors will continue to need local validation capabilities for development, testing, debugging, and quality assurance. For this reason, implementing validation now is not a redundant investment, even in a scenario where future infrastructure-level validation is introduced.

#### 2.2.4 More information
[Domæneregler for patientindeks for dokumentdeling](https://sundhedsdatastyrelsen.dk/digitale-loesninger/referencearkitektur-og-standarder/domaeneregler-patientindeks)

## 3 Validation in MedCom FHIR test validation tool

**NB: The MedCom FHIR test server is currently not working correctly.** You can use the validator at [validator.fhir.medcom](https://validator.fhir.medcom.p1.hosting.kitkube.dk/) in the meantime, as the newest Implementation Guides for CareCommunication and it's dependencies are uploaded to this validator.

**How to use [MedComs FHIR validator](https://validator.fhir.medcom.dk/)**

1. Open the drop down menu named: Common Validation Options: Select the MedCom FHIR standard you would like to validate aginst. 

2. Paste your FHIR Bundle into the text field or upload your Bundle as a file.

3. Click the “Validate” button and see the result.