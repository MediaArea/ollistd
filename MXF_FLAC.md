# Mapping FLAC into the MXF Generic Container

Proposal, "(TBD") and "(To be defined)" must be replaced by real values.

## Foreword

(Same as is SMPTE ST 2037 document)

## Intellectual Property

Remark: this is the technical proposal, based on SMPTE ST 2037 document (VC-1 in MXF). We have tried to remove any generic SMPTE boilerplate that is not different for FLAC and tried to keep only sentences relevant for having a good technical document to define use of FLAC in MXF without reinventing the wheel. We believe there there are no copyright issues with using basic technical sentences from SMPTE ST 2037 as a basis for the language here, but please contact [info@mediaarea.net](mailto:info@mediaarea.net) if you are a copyright holder and disagree so that we may remove this document immediately.

(Same as is SMPTE ST 2037 document)

## 1 Scope

This standard defines how FLAC bitstreams shall be mapped in the MXF Generic Container (SMPTE 379M).

This standard maps the FLAC encoded Audio packets as either frame-wrapped or clip-wrapped using the mechanisms defined in SMPTE 379M.

This standard defines the KLV coding, the Essence Container Universal Label, the Essence Compression Universal Label and the Essence Descriptor to be used when wrapping FLAC bitstreams in the MXF Generic Container.

## 2 Conformance Notation

(Same as is SMPTE ST 2037 document)

## 3 Normative References

(Same as is SMPTE ST 2037 document)

IETF RFC (to be defined) — FLAC Compressed Audio Bitstream Format and Decoding Process  
Temporary: [FLAC format information on Xiph website](https://xiph.org/flac/format.html)

## 4 Glossary of Acronyms, Terms and Data Types

(Same as is SMPTE ST 2037 document)

## 5 Overview

(Same as is SMPTE ST 2037 document)

## 6 MXF Encoders — Locating Data Access Units

(Same as is SMPTE ST 2037 document)

## 7 Data Access Units in the MXF Generic Container

(Same as is SMPTE ST 2037 document)

### 7.1   Frame Wrapping

(Same as is SMPTE ST 2037 document)

### 7.2   Clip Wrapping

(Same as is SMPTE ST 2037 document)

## 8   Key-Length-Value Coding

### 8.1   Essence Element Key

The values of the first 12 bytes of the essence element Key are defined in SMPTE 379M. The version (byte 8) shall be set to 0x01. The values of the last four bytes of the Audio Element Key are given in Table 1.

Table 1 – Key Value for the FLAC Sound Element

| Byte No. | Description                    | Value | Meaning                                                                      |
|----------|--------------------------------|-------|------------------------------------------------------------------------------|
| 1~12     | Defined in SMPTE 379M          |       | See SMPTE 379M                                                               |
| 13       | Item Type Identifier           | 16h   | GC Sound Item (as defined in SMPTE 379M)                                     |
| 14       | Essence Element Count          | kkh   | Count of Sound Elements in the Sound item                                    |
| 15       | Essence Element Type           | (TBD) | Frame-wrapped FLAC Sound Element                                             |
|          |                                | (TBD) | Clip-wrapped FLAC Sound Element                                              |
| 16       | Essence Element Number         | Nnh   | The Number (used as an Index) of this Sound Element in the Sound Item        |

###8.1.1   Essence Element Count – Byte 14

(Same as is SMPTE ST 2037 document)

#### 8.1.2   Essence Element Type – Byte 15

(Same as is SMPTE ST 2037 document)

#### 8.1.3   Essence Element Number – Byte 16

(Same as is SMPTE ST 2037 document)

### 8.2   Length

(Same as is SMPTE ST 2037 document)

### 8.3   Value

#### 8.3.1   Frame-wrapped

(Same as is SMPTE ST 2037 document)

#### 8.3.2   Clip-wrapped

(Same as is SMPTE ST 2037 document)

## 9   SMPTE Universal Labels for FLAC

### 9.1   Essence Container UL

The values for the Essence Container UL are given in Table 2.

Table 2 – Specification of the Essence Container Label

| Byte No. | Description                    | Value | Meaning                                                                      |
|----------|--------------------------------|-------|------------------------------------------------------------------------------|
| 1~12     | Defined by Generic Container   |       | As defined in SMPTE 379M                                                     |
| 13       | Essence Container Kind         | 02h   | MXF Generic Container                                                        |
| 14       | Mapping Kind                   | (TBD) | FLAC Sound Element                                                           |
| 15       | Content Kind                   | 01h   | Frame-wrapped Sound Element                                                  |
|          |                                | 02h   | Clip-wrapped Sound Element                                                   |
| 16       | Reserved                       | 00h   |                                                                              |

(Same as is SMPTE ST 2037 document)

### 9.2   Sound Essence Coding UL

Values for the Sound Essence coding UL are given in Table 3.

Table 3 – Specification of the Sound Essence Compression Label

| Byte No. | Description                    | Value | Meaning                                                                      |
|----------|--------------------------------|-------|------------------------------------------------------------------------------|
| 1~8      | Registry Designator            |       | Designator value is defined in  SMPTE 400M                                   |
| 9        | Parametric                     | 04h   | Node used to define parametric data                                          |
| 10       | Sound Essence                  | 02h   | Identifies Sound essence coding                                              |
| 11       | Sound Coding Characteristics   | 02h   | Identifies Sound coding characteristics                                      |
| 12       | Compressed Sound Coding        | 02h   | Identifies specialized compression                                           |
| 13       |                                | (TBD) | Identifies FLAC Sound coding                                                 |
| 14       |                                | 00h   | Unused                                                                       |
| 15       |                                | 00h   | Unused                                                                       |
| 16       |                                | 00h   | Unused                                                                       |

(Same as is SMPTE ST 2037 document)


## 10   FLAC Sound Essence Descriptor

This section defines the FLACSoundEssenceDescriptor that extends the CDCI Sound Essence Descriptor and RGB Sound Essence Descriptor defined in SMPTE 377-1 with additional properties specific to FLAC.

All FLAC bitstreams wrapped in the MXF Essence Container according to this standard shall be described in the MXF Header Metadata with a FLACSoundEssenceDescriptor according to the rules defined in SMPTE 377-1 on how to link such descriptors with the Essence Container, and as shown in Table 5.

Table 5 – FLAC Sound Essence Descriptor

| Item Name                | Type       | Len | UL Value     | Req ? | Meaning                                         | Default |
|--------------------------|------------|-----|--------------|-------|-------------------------------------------------|---------|
| FLAC Sound Essence Descriptor | Set UL     | 16  | See table below | Req   | Defines the FLAC Sound Essence Descriptor Set |         |
| Length                   | BER Length | 4   |                                                 | Req   | Set length   |         |
| <td colspan=5>All items from the MXF Format Generic Sound Essence Descriptor</td>|
| FLACInitializationMetadata | Datastream | 16  | 06 0e 2b 34 <br/> (TBD) <br/> (TBD)<br/> (TBD) | Req | See Section 10.1.  |         |

### 10.1   FLACInitializationMetadata

This property encodes the Metadata defined in IETF RFC (to be defined) and shall be present. The value of the property shall consist of all the header/metadata packets before the first data packet. These include the first header packet containing only the word fLaC as well as all metadata packets as defined in IETF RFC (to be defined).

### 10.2   Key Value

The set Key of the FLAC Sound Descriptor shall be as defined in Table 6.

Table 6 – Key Value for the FLAC Sound Essence Descriptor

| Byte No. | Description                    | Value | Meaning                                                                      |
|----------|--------------------------------|-------|------------------------------------------------------------------------------|
| 1~13     | As defined in SMPTE 377-1, Common Key Value for Structural Metadata (Table 13) |       | Values for all MXF structural metadata sets |
| 14~15    | Set Kind                       | (TBD) | Defines the Key value for the FLAC Sound Essence Descriptor                |
| 16       | Reserved                       | 00h   | Reserved value                                                               |

### 10.3   Length Value

(Same as is SMPTE ST 2037 document)

## 11   Pre-Change

(Same as is SMPTE ST 2037 document)

## 12   Index Tables

(Same as is SMPTE ST 2037 document)

## Annex A  (Informative)

### Bibliography

FLAC specification: IETF RFC (to be defined) 
(Same as is SMPTE ST 2037 document)

