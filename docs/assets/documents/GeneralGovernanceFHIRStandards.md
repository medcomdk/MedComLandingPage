[Return](../../index.md)

# General Governance for MedCom FHIR Standards

**Table of contents**
* [1 Introduction to General Governance for MedCom FHIR Standards](#1-introduction-to-general-governance-for-medcom-fhir-standards)
* [2 Special terms used in the general Governance for MedCom FHIR Standards](#2-special-terms-used-in-the-general-governance-for-medcom-fhir-standards)
* [3 MedCom FHIR standards](#3-medcom-fhir-standards)
* [4 MustSupport](#4-mustsupport)
  + [4.1 MustSupport Rules](#41-mustsupport-rules)
  + [4.2 MustSupport Links](#42-mustsupport-links)
* [5 Implementation Requirements for Narrative Texts](#5-implementation-requirements-for-narrative-texts)
  + [5.1 The Importance of Narrative Text in MedCom’s FHIR Standards](#51-the-importance-of-narrative-text-in-medcoms-fhir-standards)
  + [5.2 Requirements for the Narratives](#52-requirements-for-the-narratives)
    - [5.2.1 The status element](#521-the-status-element)
    - [5.2.2 The div element](#522-the-div-element)
    - [5.2.3 General Narrative Text Rules](#523-general-narrative-text-rules)
  + [5.3 Links for Narrative Text](#53-links-for-narrative-text)
* [6 Governance for narrative content in MedCom FHIR standards](#6-governance-for-narrative-content-in-medcom-fhir-standards)
  + [6.1 Elements that must be included in the narrative text](#61-elements-that-must-be-included-in-the-narrative-text)
  + [6.2 Elements that shall not be included in the narrative text](#62-elements-that-shall-not-be-included-in-the-narrative-text)
* [7 Governance for MedCom FHIR Terminology](#7-governance-for-medcom-fhir-terminology)
* [8 Governance for concrete MedCom FHIR Standards](#8-governance-for-concrete-medcom-fhir-standards)
  + [8.1 Versions of MedCom FHIR Standards](#81-versions-of-medcom-fhir-standards)

<br>

## 1 Introduction to General Governance for MedCom FHIR Standards

On this page, you can find information about how MedCom has profiled FHIR standards to work in a Danish context.
Governance for MedCom HL7 FHIR describes the basic ruleset of how MedCom standards must be implemented in the Danish Healthcare System.

<br>

These general MedCom FHIR Governance rules are intended to clarify the use of MedCom’s FHIR standards for the health and social area.

It is the intention that the general MedCom FHIR Governance rules together with MedCom’s individual FHIR standards form the full and sufficient basis for implementing MedCom’s healthcare FHIR standards. Thus, the governance rules must be able to function as “a chief judge”, where there is doubt about the practical application of MedCom’s FHIR standards.


### 2 Special terms used in the general Governance for MedCom FHIR Standards

MedCom adopts the normative words defined in IETF Best Current Practice 14: Key words for use in RFCs to Indicate Requirement Levels (BCP-14) (currently RFC 2119 and RFC 8174), certain words indicate whether a specific content of the Technical Framework is normative: either required (e.g., “must”, “required”, “shall”) or optional (e.g., “may”, “recommended”). Informative content does not contain these key words.

<a href="https://www.rfc-editor.org/info/rfc2119" target="_blank">RFC 2119</a> specifies common key words that may be used in protocol specifications, where <a href="https://www.rfc-editor.org/info/rfc8174" target="_blank">RFC 8174</a> aims to reduce the ambiguity by clarifying that only UPPERCASE usage of the key words have the defined special meanings.

This specification uses the conformance verbs SHALL, SHOULD, and MAY as defined in RFC 2119. Unlike RFC 2119, however, this specification allows that different applications might not be able to interoperate because of how they use optional features. In particular:

* **SHALL**: (or “REQUIRED” or “MUST”) an absolute requirement for all implementations
* **SHALL NOT**: (or "MUST NOT") an absolute prohibition against inclusion for all implementations
* **SHOULD/SHOULD NOT**: (or “RECOMMENDED”/“NOT RECOMMENDED”) A best practice or recommendation to be considered by implementers within the context of their particular implementation; there may be valid reasons to ignore an item, but the full implications must be understood and carefully weighed before choosing a different course
* **MAY**: (or "OPTIONAL") This is truly optional language for an implementation; can be included or omitted as the implementer decides with no implications

<br>

This convention is in compliance with HL7 FHIR use of the terms, which is described by <a href="http://www.hl7.org/fhir/conformance-rules.html#conflang" target="_blank">HL7 FHIR under conformance language</a>.


## 3 MedCom FHIR standards

An implementer of a MedCom FHIR  Standard **SHALL** be compliant with all parts of the documentation (both the standard documentation and the relevant governance).


## 4 MustSupport

Unless otherwise stated, the following criteria apply to elements marked as “Must Support” in MedCom's Implementation Guides:

Labeling an element MustSupport (S or SO red markings) means that implementations that produce or consume resources **SHALL** provide "support" for the element in a meaningful way, and is therefore a part of a standard. Because the base FHIR specification is intended to be independent of any particular implementation context, no elements are flagged as mustSupport=true as part of the base specification. This flag is intended for use in profiles that have a defined implementation context.

<br>

#### 4.1 MustSupport Rules

In MedCom FHIR Messaging MustSupport requires that a system provides "support" for the element in some meaningful way. A meaningful way depends on the type of information, which will be expressed for each standard.

**For technical profiles**

Systems receiving or consuming a resource instance:

**MUST** be able to process the field’s content when it is present.
**MUST** process the content according to the rules defined for the profile.
**MUST NOT** fail when the value is not present if it has a cardinality of minimum 1.

Systems sending or creating a resource instance:

**SHOULD** populate the element when the information is available.
**MUST** populate the element according to the rules defined for the profile.

For Logical Models:

Functional Analysis **MUST** consider the data element as defined.

“Must Support” elements that are used in an implementation **MUST** inherit the behaviour and constraints defined for the data element.
“Must Support” elements not needed in a particular implementation **MAY** be excluded from implementation but such exclusion **MUST** be described.
Derived implementations **SHOULD** inherit the field’s “Must Support” flag.

#### 4.2 MustSupport Links

| Links for MustSupport|
|:---|
| <a href="https://www.hl7.org/FHIR/conformance-rules.html#mustSupport" target="_blank">Detailed specification for MustSupport in FHIR R4</a> |

<br>

### 5 Implementation Requirements for Narrative Texts

This section is aimed at vendors/implementers and describes the concrete requirements for how to implement and represent narrative text in MedCom FHIR resources.

#### 5.1 The Importance of Narrative Text in MedCom’s FHIR Standards
In MedCom’s FHIR standards, it is required that all FHIR resources include a narrative text. The narrative serves an essential purpose: It ensures that the clinical or administrative content of the resource can be understood by healthcare professionals without the need for specialized technical tools. While the structured elements of a FHIR resource are designed for system-to-system communication, the narrative provides a human-readable summary that makes the information accessible to human interpretation in a simple XHTML view.

The narrative text plays a critical role in supporting robustness and patient safety across the healthcare system. First, it allows the content of a message to be read even if the recipient system fails to process the structured data. Second, when narrative text is displayed across multiple versions of a standard, it increases patient safety by ensuring that as much information as possible remains visible, and it enables healthcare professionals to review historical messages in the future. Third, it makes additional elements beyond those defined in the MedCom standard transparent, since FHIR allows resources to include more data than the standard strictly requires. Fourth, including a narrative is considered best practice in FHIR and aligns MedCom’s work with international recommendations. Finally, the presence of a narrative ensures that even if a system receives a FHIR Bundle it is not fully equipped to handle, the content can still be displayed and understood when necessary.

#### 5.2 Requirements for the Narratives

The narrative text **SHALL** include a human-readable representation of every data element marked with the Obligation code **SHALL:in-narrative**.

Obligations in FHIR define actor-specific requirements in an Implementation Guide to express conformance expectations. The code “SHALL:in-narrative” indicates that the referenced data element must be represented in the human-readable narrative of the resource. An Actor represents a defined role in an exchange, and obligations are applied to actors to indicate their specific responsibilities. The narrative **SHALL** provide a human-readable summary of the essential elements and **SHALL NOT** replicate the full structured content.

All MedCom FHIR resources **SHALL** include a narrative in the `[resource].text`-element (even though it is not marked with 1..1 cardinality in the Implementation Guide), except the Bundle resources. Since the Bundle itself does not carry clinical meaning, its content must be understood by reviewing the individual resources inside the Bundle.

Narratives contain two sub elements, text.status and text.div.

##### 5.2.1 The status element

In MedCom FHIR resources the text.status element **SHALL** always use the code "generated" or "extension". The status "generated" **SHALL** be used when the resource contains only standard, generated content. The status "extension" **SHALL** be used when the resource includes additional elements provided through extensions.

A narrative in MedCom FHIR resources **SHALL NEVER** be of code: empty.

##### 5.2.2 The div element

The contents of the text.div element are XHTML fragments that **SHALL** contain only the basic HTML formatting elements described in chapters 7-11 (except section 4 of chapter 9) and 15 of the HTML 4.0 standard, '<a>' elements (either name or href), images and internally contained style attributes.

The XHTML content **SHALL NOT** contain a head, a body element, external stylesheet references, deprecated elements, scripts, forms, base/link/xlink, frames, iframes, objects or event related attributes (e.g. onClick). 

If a resource includes a base-64-encoded attachment, this **SHALL NOT** be included in the narrative text, as it will cause the size of the message to increase rapidly.

##### 5.2.3 General Narrative Text Rules

* All resources **SHALL** contain a narrative text defined by the `[resource].text` element (Except Bundles).
* The Narrative Text **SHALL** have a status with value "generated" or "extensions".
* The Narrative Text **SHALL** include the ID for each resource (Resource.id).
* The Narrative Text **SHALL** include references to other resources as the ID for each resource (Resource.id).
* The Narrative Text **SHALL** include elements marked with the Obligation code **SHALL:in-narrative**.
* The Narrative Text **SHALL NOT** include base-64-encoded attachments.
* If a resource contains extra information beyond the MedCom standard, this **SHALL** be included in the narrative.
* The narrative **SHALL** use Danish clinical terminology or recognized Danish display texts if such exist, and it **SHALL** also include the corresponding English text to ensure international readability.

#### 5.3 Links for Narrative Text

|Additional information can be found in the following links for narrative texts in FHIR|
|:---|
|<a href="http://hl7.org/fhir/R4/narrative.html#Narrative" target ="_blank">Narrative Text description in FHIR R4</a>|
|<a href="http://hl7.org/fhir/R4/codesystem-narrative-status.html#4.3.14.424.2" target="_blank">NarrativeStatus in FHIR R4</a>|
|<a href ="http://hl7.org/fhir/R4/narrative.html#css" target="_blank">Styling the XHTML in FHIR R4</a>|

### 6 Governance for narrative content in MedCom FHIR standards
This section serves as background information for vendors to understand the rationale behind the setup of the requirements.

This governance is applied by MedCom to define which elements **SHALL** be included in the narrative and assigned the Obligation code **SHALL:in-narrative** found in the MedCom FHIR standard profiles. The purpose of this governance is to ensure a consistent use of narrative texts across MedCom’s FHIR profiles. The governance defines which types of elements that **SHALL** be included in the human-readable narrative and which should be excluded, based on best practice and patient safety considerations. The same type of element **SHOULD** always be treated consistently across MedCom profiles to support predictable implementation.

##### 6.1 Elements that must be included in the narrative text

Clinically and administratively relevant information, including diagnoses, observations, procedures, and other content directly relevant to patient care or administration **SHALL** be included in the narrative text.

Clinically and administratively relevant information includes:

* Elements representing relevant person and organization information (e.g., Patient, Practitioner, Organization), including e.g. name, role, CPR-number, birthdate, and contact information.
* Codes and corresponding systems with human meaning. When coded values are used (e.g., LOINC, SNOMED CT, MedCom codes), their display text (the human-readable term) must appear in the narrative.
* Relevant values (e.g., observation results, medication names and dosages, diagnostic conclusions).
* Relevant elements from extension.
* Identifiers when they have human relevance (e.g., SOR-ID, municipality codes, episode-of-care identifiers).
* The resource ID.
* References to other resources by including the ID of the referenced resource.
* Relevant dates and times.

##### 6.2 Elements that shall not be included in the narrative text

Elements that are NOT clinically or administratively relevant and that do not contribute to human readability **SHALL NOT** be included in the narrative text.

Elements that shall not be included are:

* Machine-oriented content and technical or system-specific identifiers without clinical or administrative relevance (except resource.id).
* Base-64-encoded content, including documents or binary attachments.
* System metadata or technical extensions not relevant to clinical or administrative use.

## 7 Governance for MedCom FHIR Terminology

[Click here to get more information about the governance for MedCom FHIR Terminology](assets/documents/GovernanceTerminology.md).

## 8 Governance for concrete MedCom FHIR Standards

Each MedCom FHIR standard will potentially add some specific Governance Rules to the mix of overall Governance Rules. These are handled separately, to which the specific standard will link to.

### 8.1 Versions of MedCom FHIR Standards
Vendors **SHOULD** be prepared to handle multiple versions of a MedCom FHIR standard.
The version of the standard is not explicitly stated in a Bundle.

When receiving a MedCom FHIR Bundle, it **SHOULD** be validated against the rules and constraints defined in the associated Implementation guide of the same version. With breaking changes, MedCom will provide specific guidelines for the scenario.