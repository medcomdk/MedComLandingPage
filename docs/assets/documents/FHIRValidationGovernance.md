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
* [3 Validation in MedCom FHIR test server](#3-validation-in-medcom-fhir-test-server)
  * [3.1 Guide: how to post JSON and XML to MedCom’s FHIR test server](#31-guide-how-to-post-json-and-xml-to-medcoms-fhir-test-server)
    * [3.1.1 JSON](#311-json)
    * [3.1.2 XML](#312-xml)

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

* The sender **SHALL** validate outgoing FHIR messages against the relevant FHIR Implementation Guide(s) (IG) before transmission. This includes Acknowledgements.
* Messages with validation errors **SHALL NOT** be sent unless explicitly approved by the responsible authority within the sending organization.

#### 2.1.2 Receiver-side validation

* The receiver **SHALL** validate all incoming messages before further processing.
* Receivers **SHALL** accept non-critical warnings but **SHALL** reject messages that violate mandatory constraints and rules.
* The sender **SHALL** validate received acknowledgements and ensure that they correctly reference the original message. If an Acknowledgement fails validation, the receiver **SHALL** contact the sending system through alternative communication channels to inform them that their acknowledgement messages are not conformant.

### 2.2 FHIR Documents - Validation Governance

This governance applies to MedCom FHIR Documents exchanged through the current national document-sharing infrastructure, which is based on IHE XDS.
The existing infrastructure does not perform FHIR validation today. Until the infrastructure is updated to support FHIR-native operations in the future, vendors **SHALL** ensure that all FHIR documents are valid.

#### 2.2.1 Document source validation

* The document source SHALL provide valid FHIR documents to the national infrastructure.
* Documents that are not valid **SHALL NOT** be submitted. 
  * In cases where the document source is unable to produce a conformant FHIR document, the document source **SHALL** prevent transmission, **SHALL** log the validation failure, **SHALL** perform internal escalation and troubleshooting, and can seek guidance from MedCom if the issue cannot be resolved locally.
  * On-demand documents: If the document source is unable to produce a conformant document, the document source **SHALL** return an error response. In the current IHE XDS-based infrastructure, the document source **SHALL** return an IHE-compliant error response structured in accordance with ITI-43 Retrieve Document Set (IHE ITI Technical Framework, Volume 3).

#### 2.2.2 Document source validation

* The document consumer **SHALL** ensure the validity of the received document prior to presenting it to the user.
* The document consumer **SHOULD**, as far as possible, display documents that contain validation errors. In such cases, the document consumer **SHALL** present a disclaimer indicating that the document contains error(s). The document consumer **MAY** present a clear, user-friendly explanation of the document’s contained error(s) understandable to non-technical users.
* If the document cannot be processed, the document consumer **MUST** provide an error message to the user. The document consumer **MAY** still display the narrative content to ensure that essential clinical information remains accessible to the user if possible.
* If identifiable, the relevant document source organization **SHALL** be notified, and MedCom **MAY** be notified.

#### 2.2.3 Transition to future FHIR-based infrastructure
The national infrastructure is expected to transition to a more FHIR-based architecture in the future. Work on this architecture is ongoing, and the specific design— including whether the infrastructure will perform central validation of metadata and document content, and how validation responsibilities will be shared between participants—has not yet been decided.

Until a future governance model is formally established, document source and document consumer validation remains required.

Regardless of the final architectural decisions, experiences from international FHIR implementations show that vendors will continue to need local validation capabilities for development, testing, debugging, and quality assurance. For this reason, implementing validation now is not a redundant investment, even in a scenario where future infrastructure-level validation is introduced.

#### 2.2.4 More information
[Domæneregler for patientindeks for dokumentdeling](https://sundhedsdatastyrelsen.dk/digitale-loesninger/referencearkitektur-og-standarder/domaeneregler-patientindeks)

## 3 Validation in MedCom FHIR test server

**NB: The MedCom FHIR test server is currently not working correctly.** You can use the validator at [validator.fhir.org](validator.fhir.org) in the meantime, as the newest Implementation Guides for CareCommunication and it's dependencies are uploaded to this validator.

**How to use [validator.fhir.org](validator.fhir.org)**

1. Select FHIR version: Click the “Options” tab. Find the section labeled “FHIR version” and select 4.0.1.

2. Go to the Validate tab. Paste your FHIR Bundle into the text field or upload your Bundle as a file.

3. Click the “Validate” button and see the result.

**How to use the [MedCom FHIR server](https://medcomfhir.dk)**

MedCom provides a [FHIR server](https://medcomfhir.dk) that can be used to validate implementations against MedCom’s FHIR standards. This server is intended for testing only and **SHALL NOT** be used for production transactions, nor contain any real-world or personally identifiable data.

There is a limit to how many times a vendor can execute test scripts in Touchstone. Therefore, MedCom recommends using the test server first to perform general validation before running the tests in Touchstone. The test server cannot validate the specific use case covered by the test script, but it can be used to identify and correct general issues. Read more about [how to use Touchstone here](TouchStoneGettingStarted.md).

Some MedCom Implementation Guides exist in multiple versions on the test server to cover all MedCom standards. The validation server always uses the latest profile version by default. If your implementation is based on an earlier version, specify it by appending the version number to the canonical URL in resource.meta.profile using the format `|n.n.n`.

Example:

~~~json
"profile" : [
    "http://medcomfhir.dk/ig/core/StructureDefinition/medcom-core-patient|3.0.1"
]
~~~

Notice that JSON resources can be validated directly in the browser, while XML resources must be submitted using a client tool such as Postman. You can find a guide on how to post JSON and XML below.


### 3.1 Guide: how to post JSON and XML to MedCom’s FHIR test server

If you do not have a user account for MedCom's FHIR test server, contact FHIR@medcom.dk and request access. Include the names and email addresses of the people who need access.

There are two ways to validate using MedCom’s FHIR test server:

1.	By posting JSON directly through a web browser.
2.	By posting XML (or JSON) using a client tool such as Postman.

This section provides a step-by-step guide for both the browser-based and Postman-based validation methods. Other client tools may also be used.

#### 3.1.1 JSON

1)	Go to https://medcomfhir.dk and log in.

2)	Select the “Bundle” section to get access to the Bundle operations.

3)	Choose the POST /Bundle/%Validate operation and click “Try it out”.

4)	Paste your FHIR Bundle (JSON format) into the request body and click “Execute”. 

5)	Review the validation result (OperationOutcome) under the “Responses” section.

#### 3.1.2 XML

**Part 1: Setup in Postman**

1.	Install Postman.
2.	Create a new workspace and import these three files (WILL BE AVAILALBE SOON) by clicking Import in Postman.
3.	Open the MedCom FHIR collection.
4.	Go to the Authorization tab and select Auth Type: OAuth 2.0.
5.	Under Configure New Token, fill in:

        Token name: token
        Grant type: Password Credentials
        Access Token URL: https://keycloak.hosting.kitkube.dk/auth/realms/
        medcom/protocol/openid-connect/token
        Client ID: hapifhir-userclient
        Username and password: Your MedCom FHIR server login
        Scope: openid
        Client authentication: Send as Basic Auth header

6.	Click Get New Access Token, then Proceed and Use Token.
7.	The token appears under Current Token and expires after a short time. Click Refresh to renew it or click Get New Token if it has expired.

**Part 2: Post Bundle to the Server**

1.	In the MedCom FHIR collection, select the POST request.
2.	Enter the following endpoint in the request URL field: https://fhir.medcom.dk/fhir/Bundle/$validate
3.	Under Headers, add:

        Content-Type: application/fhir+xml
        Accept: application/fhir+xml
4.	Under Body, choose Raw, select XML, and paste your FHIR Bundle.
5.	Click Send to execute the request.
6.	Review the validation result (OperationOutcome) in the response. 
