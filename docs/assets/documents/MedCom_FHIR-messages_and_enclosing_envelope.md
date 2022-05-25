
# MedCom FHIR Messages and Enclosing Envelope

```
The document describes how MedCom's FHIR messages are to be handled in the transmittal envelope for the specific
message type.
```

- • •

## MedCom’s FHIR messages and enclosing

## envelope

Version 1.

### Table of contents

1 Introduction ................................................................................................................................ 2

2 Enclosing envelopes .................................................................................................................. 2

```
2.1 VANSenvelope ........................................................................................................................................................................................
2.1.1 Format .............................................................................................................................................................................................
2.1.2 Name ...............................................................................................................................................................................................
2.1.3 Version .............................................................................................................................................................................................
```
3 FHIR message types .................................................................................................................. 4

```
3.1 CareCommunication................................................................................................................................................................................
3.2 HospitalNotification .................................................................................................................................................................................
```

- • •

##### 1 Introduction

In the mode of transport, MedCom's FHIR messages will be packaged and appear in various envelope formats.

At present, messages are sent in the existing VANS network and therefore in a VANSenvelope unless otherwise specified under the individual
standard. Receipt can either be in VANSenvelope or another receipt envelope, ig. KOMBITs BeskedFordeler envelope.

NB: When the modernised infrastructure is implemented, it will use new transmittal envelope that will replace the VANSenvelope. This means
that this document will be updated with the new envelope format at that time. In the transition period, both the VANSenvelope and the new
envelope will be used. It will be clearly explained how this should be handled.

##### 2 Enclosing envelopes

###### 2.1 VANSenvelope

In relation to MedCom's new FHIR messages, VANSenvelope contains 3 elements (fields) which are influenced by FHIR as a new message
type. These are contained in the following enclosing element: “VANSEnvelope/Message/MetaInformation/Document/”.

The elements are:

- Format
- Name
- Version

MedCom's FHIR messages are handled like all other messages in VANSenvelope by encoding the message base-64 in the element
"VANSEnvelope/Message/Data/"

In the Transport element, "VANSEnvelope/Message/MetaInformation/Transport", the element "TransformMessage" is handled as usual, while
"ServiceTag" with the attribute name = "MCM:MIME" can be specified with the following values:

- text/fhir+xml
- text/fhir+json

depending on the format the FHIR message is formatted in.

_2.1.1 Format_
The format will be the same as "Standard type" in MedCom's standard catalogue and is defined for all FHIR standards for "HL7".


- • •

_2.1.2 Name_
Name will be the same as "Type no." in MedCom's standard catalogue and will thus vary from message type to message type. Name will be
prefixed with MCM: and it will, in addition, be possible to postfix it with statistical variants of a given message type. As in the GGOP standard,
you can select for example GGOP1, GGOP2 and GGOP3. Similar solutions will occur as long as the FHIR messages are transported in the
VANSenvelope.

_2.1.3 Version_
Version will be the same as "Version" in MedCom's standard catalogue and will thus vary from message version to message version.


- • •

##### 3 FHIR message types

Specifically, the above-mentioned means the following for MedCom's FHIR messages

###### 3.1 CareCommunication

Envelope: VANSenvelope

Format: ”HL7”
Name: ”MCM:FDIS91#<postfix value>”
Version: ”1.0”

Postfix values for Name will be within this code outcome space, which is taken from CareCommunication’s ValueSet for categories:

https://build.fhir.org/ig/hl7dk/dk-medcom/ValueSet-medcom-careCommunication-categories.html

Name can explicitly be taken from the following Valueset: https://build.fhir.org/ig/hl7dk/dk-medcom/ValueSet-medcom-messaging-
vansStatisticalCodeCombinations.html

###### 3.2 HospitalNotification

Envelope: VANSenvelope for sending, KOMBITs BeskedFordeler (Message distribution system) envelope in reception at the Electronic
Homecare Records (“EOJ” systems).

Format: ”HL7”
Name: ”MCM:FDIS20#<postfix value>”
Version: ”1.0”

Postfix values for Name will be within this code outcome space, which is taken from HospitalNotification’s ValueSet: MedCom Hospital
Notification Message Activity Codes: https://build.fhir.org/ig/hl7dk/dk-medcom/ValueSet-medcom-hospitalNotification-messageActivities.html

Name can explicitly be taken from the following Valueset: https://build.fhir.org/ig/hl7dk/dk-medcom/ValueSet-medcom-messaging-
vansStatisticalCodeCombinations.html



This is a offline tool, your data stays locally and is not send to any server!
Feedback & Bug Reports