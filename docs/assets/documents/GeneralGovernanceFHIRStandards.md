[Return](../../index.md)

# General Governance for MedCom FHIR Standards

**Table of contents**
* [1 Introduction to General Governance for MedCom FHIR Standards](#1-introduction-to-general-governance-for-medcom-fhir-standards)
* [2 Special terms used in the general Governance for MedCom FHIR Standards](#2-special-terms-used-in-the-general-governance-for-medcom-fhir-standards)
* [3 MedCom FHIR standards](#3-medcom-fhir-standards)
* [4 Governance for concrete MedCom FHIR Standards](#4-governance-for-concrete-medcom-fhir-standards)
  + [4.1 Versions of MedCom FHIR Standards](#41-versions-of-medcom-fhir-standards)

<br>

## 1 Introduction to General Governance for MedCom FHIR Standards

On this page, you can find information about how MedCom has profiled FHIR standards to work in a Danish context.
Governance for MedCom HL7 FHIR  describes the basic ruleset of how MedCom standards must be implemented in the Danish Healthcare System.

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

This convention is in compliance with HL7 FHIR use of the terms, which is descibed by <a href="http://www.hl7.org/fhir/conformance-rules.html#conflang" target="_blank">HL7 FHIR under conformance language</a>.


## 3 MedCom FHIR standards

An implementer of a MedCom FHIR  Standard **SHALL** be compliant with all parts of the documentation (both the standard documentation and the relevant governance).

## 4 Governance for concrete MedCom FHIR Standards

Each MedCom FHIR standard will potentially add some specific Governance Rules to the mix of overall Governance Rules. These are handled separately, to which the specific standard will link to.

### 4.1 Versions of MedCom FHIR Standards
Vendors should be prepared to handle multiple versions of a MedCom FHIR standard.
The version of the standard is not explicitly stated in a bundle.

MedCom is, as of 2025, starting to introduce references in the MessageHeader to MessageDefinitions via the `definition` element. This means that future releases containing MessageHeaders will have an associated MessageDefinition linked. You can find the Implementation Guide for MessageDefinitions [here](https://medcomfhir.dk/ig/messagedefinitions/).

When receiving a MedCom FHIR Bundle, it should be validated against the rules and contraints defined in the associtated Implementation guide of the same version. With breaking changes, MedCom will provide specific guidelines for the scenario.