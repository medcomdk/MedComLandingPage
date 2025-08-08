[Return](../../index.md)

# Governance for Medcom FHIR Terminology

**Table of contents**
* [1 Introduction to Governance for MedCom FHIR Terminology](#1-introduction-to-governance-for-medcom-fhir-terminology)
* [2 Versioning of individual artefacts in the MedCom Terminology IG](#2-versioning-of-individual-artefacts-in-the-medcom-terminology-ig)
  + [2.1 Major version](#21-major-version)
  + [2.2 Minor version](#22-minor-version)
  + [2.3 Patch version](#23-patch-version)
* [3 Versioning of MedCom Terminology IG](#3-versioning-of-medcom-terminology-ig)
  + [3.1 Major version](#31-major-version)
  + [3.2 Minor version](#32-minor-version)
  + [3.3 Patch version](#33-patch-version)
* [4 Governance for Terminology artefact dates](#4-governance-for-terminology-artefact-dates)

<br>

## 1 Introduction to Governance for MedCom FHIR Terminology

Governance for MedCom FHIR Terminology covers version management and dates Codesystems, Valuesets and ConceptMaps, which are published through the MedCom FHIR Terminology IG.

<br>

MedCom defines a separation between versioning of the overall MedCom Terminology Implementation Guide (IG) and the individual terminology artefacts, such as CodeSystems, ValueSets, and ConceptMaps. While the Terminology IG is versioned as a whole, each terminology artefact is versioned independently to ensure precise tracking of changes and stable references across MedCom standards.

## 2 Versioning of individual artefacts in the MedCom Terminology IG

MedCom applies a versioning model to manage updates to individual MedCom FHIR Terminology artefacts (CodeSystems, ValueSets, ConceptMaps), using the format Major.Minor.Patch. 

Each component of the version number signals the type and impact of a change. Any MedCom standards affected by changes of individual terminology artefacts in the MedCom Terminology IG will reflect the same version change level as the artefact it incorporates that has the highest level of change (major > minor > patch). MedCom will communicate changes at the major and minor version levels to affected vendors. Vendors must be able to handle patch level changes without being notified by MedCom.

<br>

Examples:

* A minor change in a ValueSet will result in a minor version change in the standards that incorporate it. 
* MedCom releases a new major version of multiple terminology artefacts not used in MedCom standard A. Standard A’s version is then not affected on any level.

### 2.1 Major version

The major version (X.0.0) is incremented when changes are introduced that may break backward compatibility or significantly alter the structure or meaning of the individual terminology artefact. 

Examples include:

* Structural changes to existing terminology artefacts. 
* Changing or deprecating existing codes. 
* Embedding a group from one terminology artefact into another terminology artefact. 
* Adding, deprecating or changing a code in a way that impacts functionality in systems using the terminology.

### 2.2 Minor version

The minor version (X.Y.0) is incremented when new content is added in a way that is fully backward compatible and does not alter the structure or semantics of existing terminology artefacts. 

Examples include: 

* Addition of one or more new codes to existing terminology artefacts (e.g. a new category). 
* Changes that do not affect functionality but still require updated documentation or user guidance – e.g. clarifying a code definition or providing new usage instructions. 

### 2.3 Patch version

The patch version (X.Y.Z) is incremented for small changes that are backward compatible and do not affect the meaning or structure of existing content in individual terminology artefacts. 

Examples include: 

* Corrections to display names or definitions that do not affect semantic meaning. 
* Making small technical or editorial updates or fixing bugs that do not affect system behaviour or require changes by users. 

## 3 Versioning of MedCom Terminology IG

MedCom applies a versioning model to manage updates to MedCom FHIR Terminology (https://medcomfhir.dk/ig/terminology/), using the format Major.Minor.Patch. 

Changes to individual terminology artefacts do not automatically result in the same level of version change in the Terminology IG. The IG version is determined based on the overall impact of the update. 

For instance, a minor change to a ValueSet may be reflected as a patch version in the MedCom Terminology IG. 

Changes are documented in the Directory of published versions (https://medcomfhir.dk/ig/terminology/history.html) of the Terminology IG. 

Examples: 

* A new version of MedCom Terminology has been released as a major version which includes changes to artefacts (e.g. ValueSets and CodeSystems) not used in MedCom standard A. Standard A’s version is not affected at any level. 
* A new version of MedCom Terminology has been released. ValueSet A’s version is changed at the minor level and the MedCom Terminology is changed at the patch level. Standard A, which incorporates ValueSet A, is updated on the major level. 
* A new version of MedCom Terminology has been released, and it includes changes to multiple artefacts (e.g. ValueSets and CodeSystems) used in MedCom standard A. The IG of MedCom standard A will be updated to match the highest version change level (major > minor > patch) among the individual terminology artefacts it incorporates and not the version of the MedCom Terminology IG itself. 

### 3.1 Major version

The major version (X.0.0) is incremented when changes are introduced that may break backward compatibility or significantly alter the structure or meaning of one or more artefacts (e.g. Codesystems and ValueSets) in the MedCom Terminology IG. 

Examples include: 

* Major terminology structural changes to existing artefacts, such as CodeSystems or ValueSets. 

### 3.2 Minor version

The minor version (X.Y.0) is incremented when individual terminology artefacts (e.g. CodeSystems, ValueSets) are added, changed, or deprecated in a way that may impact core functionality in consuming systems, without changing the overall structure or methodology of the MedCom Terminology IG. Larger changes to existing artefacts, as well as the addition of entirely new artefacts, are managed through minor version updates as well. These changes are considered backward compatible at the Terminology IG framework level, but may require attention from implementers using affected artefacts. 

Examples include: 

* Addition of entirely new CodeSystems or ValueSets. 
* Addition of a new group of codes (e.g. a new domain or category within an existing CodeSystem). 
* Adding, deprecating or changing a code in a way that impacts functionality in systems using the terminology. 

Changes that do not affect terminology functionality but still require updated documentation or user guidance. 

### 3.3 Patch version

The patch version (X.Y.Z) is incremented for small changes that are backward compatible and do not affect the meaning or structure of existing content in existing artefacts (e.g. Codesystems and ValueSets) in the MedCom Terminology IG. 

Examples include: 

* Addition of new individual codes to an existing artefact that do not affect system functionality. 
* Corrections to display names or definitions that do not affect semantic meaning. 
* Small technical or editorial updates (like contact info or version notes) that do not affect system behavior or require changes by users. 

## 4 Governance for Terminology artefact dates

The individual MedCom Terminology artefacts (such as CodeSystems) contain two types of dates that support version control and usage guidance. One applies to the entire artefact, while the other applies to individual codes or values within it. Dates in CodeSystems and ConceptMaps apply only to the artefact as a whole. CodeSystems contain both types of dates. The following outlines how these dates are used and interpreted. 

**Date for the entire artifact:** 

This date applies to the whole artifact and indicates the date of the most recent change. 

**Date for each individual code in the CodeSystem:** 

This date indicates the most recent status change date for the individual value/code. 

There are four different statuses: 

* Experimental: The code is recommended for trial use only. 
* Active: The code is actively in use and recommended. 
* Deprecated: Use is discouraged. It is expected to be retired in a future release. 
* Retired: The code must no longer be used. 

If a code or artifact does not have an associated date, it is because dates were not implemented in the terminology at the time of creation; they will be added the next time the element is updated.