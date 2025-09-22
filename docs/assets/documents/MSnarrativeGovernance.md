* [1 Narrative texts](#6-narrative-texts)
    * [1.1 The status element](#61-the-status-element)
    * [1.2 The div element](#62-the-div-element)
    * [1.3 General narrative text rules](#63-general-narrative-text-rules)
    * [1.4 Links for narrative text](#64-links-for-narrative-text)

### 1 Narrative Texts
**OBS:** MedCom is currently transitioning between two approaches for defining narrative text in its profiles. If a profile has not yet implemented Obligations, the governance on this page must be followed. If a profile includes Obligations, use the governance described on [this page instead](GeneralGovernanceFHIRStandards.md).

The narrative text contains sufficient detail to make it "clinically safe" for a human to just read the narrative. 

The narrative text **SHALL** encode all the structured data pointed out by the ∑-symbol in combination with MustSupport. Elements only marked with the ∑-symbol, and not MustSupport are not expected to be a part of the narrative text. 

Each resource, beside the MedComMessagingMessage, **SHALL** contain a narrative text in the element text, eventhough this element is not marked with MS or has a minimum cardinality of 1.

Narratives contain two sub elements, status and div.

#### 1.1 The status element

In MedCom FHIR Messages the status **SHALL** always be "generated" meaning that the narrative is generated from elements with ∑-symbol and MustSupport, or "extension" meaning that in addition to "generated", it is including extensions.

A narrative in MedCom FHIR Messages **SHALL NEVER** be of code: empty.

#### 1.2 The div element

The contents of the div element are XHTML fragments that **SHALL** contain only the basic HTML formatting elements described in chapters 7-11 (except section 4 of chapter 9) and 15 of the HTML 4.0 standard, '<a>' elements (either name or href), images and internally contained style attributes.

The XHTML content **SHALL NOT** contain a head, a body element, external stylesheet references, deprecated elements, scripts, forms, base/link/xlink, frames, iframes, objects or event related attributes (e.g. onClick). 

If a resource includes a base-64-encoded attachment, this **SHALL NOT** be included in the narrative text, as it will cause the size of the message to increase rapidly.

#### 1.3 General Narrative Text Rules

* All resources in a MedComMessagingMessage **SHALL** contain a Narrative Text defined by the [resource].text element.
* The Narrative Text **SHALL** have a status with value "generated" or "extensions". 
* The Narrative Text **SHALL** include elements marked with ∑-symbol in combination with MustSupport. 
* The Narrative Text **SHALL NOT** include base-64-encoded attachments.


#### 1.4 Links for Narrative Text

| Links for Narrative Text|
|:---|
|<a href="http://hl7.org/fhir/R4/narrative.html#Narrative" target ="_blank">Narrative Text description in FHIR R4</a>|
|<a href="http://hl7.org/fhir/R4/codesystem-narrative-status.html#4.3.14.424.2" target="_blank">NarrativeStatus in FHIR R4</a>|
|<a href ="http://hl7.org/fhir/R4/narrative.html#css" target="_blank">Styling the XHTML in FHIR R4</a>|
