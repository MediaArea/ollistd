# Mapping FFV1 into the MXF Generic Container

Proposal, "(TBD") and "(To be defined)" must be replaced by real values.

## Foreword

(Same as is SMPTE ST 2037 document)

## Intellectual Property

Remark: this is the technical proposal, based on SMPTE ST 2037 document (VC-1 in MXF). We have tried to remove any generic SMPTE boilerplate that is not different for FFV1 and tried to keep only sentences relevant for having a good technical document to define use of FFV1 in MXF without reinventing the wheel. We believe there there are no copyright issues with using basic technical sentences from SMPTE ST 2037 as a basis for the language here, but please contact [info@mediaarea.net](mailto:info@mediaarea.net) if you are a copyright holder and disagree so that we may remove this document immediately.

(Same as is SMPTE ST 2037 document)

## 1 Scope

This standard defines how FFV1 bitstreams shall be mapped in the MXF Generic Container (SMPTE 379M).

FFV1 defines three possible versions for compliant bitstreams: 0, 1, 3. All of these versions are supported by this standard.

FFV1 bitstreams comprise FFV1 encoded Pictures and both intra-coding and inter-coding mechanisms can be used. Both coding mechanisms are supported in this standard.

FFV1 bitstreams comprise FFV1 encoded Pictures in both CDCI or RGB color spaces. Both colors spaces are supported in this standard.

This standard maps the FFV1 encoded Pictures as either frame-wrapped or clip-wrapped using the mechanisms defined in SMPTE 379M, and both progressive and interlaced Picture representations are supported in this standard.

This standard defines the KLV coding, the Essence Container Universal Label, the Essence Compression Universal Label and the Essence Descriptor to be used when wrapping FFV1 bitstreams in the MXF Generic Container.

## 2 Conformance Notation

(Same as is SMPTE ST 2037 document)

## 3 Normative References

(Same as is SMPTE ST 2037 document)

IETF RFC (to be defined) — FFV1 Compressed Video Bitstream Format and Decoding Process

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

The values of the first 12 bytes of the essence element Key are defined in SMPTE 379M. The version (byte 8) shall be set to 0x01. The values of the last four bytes of the Picture Element Key are given in Table 1.

Table 1 – Key Value for the FFV1 Picture Element

| Byte No. | Description                    | Value | Meaning                                                                      |
|----------|--------------------------------|-------|------------------------------------------------------------------------------|
| 1~12     | Defined in SMPTE 379M          |       | See SMPTE 379M                                                               |
| 13       | Item Type Identifier           | 15h   | GC Picture Item (as defined in SMPTE 379M)                                   |
| 14       | Essence Element Count          | kkh   | Count of Picture Elements in the Picture item                                |
| 15       | Essence Element Type           | (TBD) | Frame-wrapped FFV1 Picture Element                                           |
|          |                                | (TBD) | Clip-wrapped FFV1 Picture Element                                            |
| 16       | Essence Element Number         | Nnh   | The Number (used as an Index) of this Picture Element in the Picture Item    |

#### 8.1.1   Essence Element Count – Byte 14

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

## 9   SMPTE Universal Labels for FFV1

### 9.1   Essence Container UL

The values for the Essence Container UL are given in Table 2.

Table 2 – Specification of the Essence Container Label

| Byte No. | Description                    | Value | Meaning                                                                      |
|----------|--------------------------------|-------|------------------------------------------------------------------------------|
| 1~12     | Defined by Generic Container   |       | As defined in SMPTE 379M                                                     |
| 13       | Essence Container Kind         | 02h   | MXF Generic Container                                                        |
| 14       | Mapping Kind                   | (TBD) | FFV1 Picture Element                                                         |
| 15       | Content Kind                   | 01h   | Frame-wrapped Picture Element                                                |
|          |                                | 02h   | Clip-wrapped Picture Element                                                 |
| 16       | Reserved                       | 00h   |                                                                              |

(Same as is SMPTE ST 2037 document)

### 9.2   Picture Essence Coding UL

Values for the Picture Essence coding UL are given in Table 3.

Table 3 – Specification of the Picture Essence Compression Label

| Byte No. | Description                    | Value | Meaning                                                                      |
|----------|--------------------------------|-------|------------------------------------------------------------------------------|
| 1~8      | Registry Designator            |       | Designator value is defined in  SMPTE 400M                                   |
| 9        | Parametric                     | 04h   | Node used to define parametric data                                          |
| 10       | Picture Essence                | 01h   | Identifies picture essence coding                                            |
| 11       | Picture Coding Characteristics | 02h   | Identifies picture coding characteristics                                    |
| 12       | Compressed Picture Coding      | 02h   | Identifies specialized compression                                           |
| 13       |                                | (TBD) | Identifies FFV1 picture coding                                               |
| 14       |                                | xxh   | Identifies FFV1 version according to the table below                         |
| 15       |                                | 00h   | Unused                                                                       |
| 16       |                                | 00h   | Unused                                                                       |

(Same as is SMPTE ST 2037 document)

The correspondence between byte 14 and the FFV1 version described in IETF RFC (to be defined) is shown in Table 4.

Table 4 – Correspondence Between Byte 14 and FFV1 version

| Profile   | Value of Byte 14 |
|-----------|------------------|
| 0         | 01h              |
| 1         | 02h              |
| 3         | 03h              |

## 10   FFV1 Picture Essence Descriptor

This section defines the FFV1PictureEssenceDescriptor that extends the CDCI Picture Essence Descriptor and RGB Picture Essence Descriptor defined in SMPTE 377-1 with additional properties specific to FFV1.

All FFV1 bitstreams wrapped in the MXF Essence Container according to this standard shall be described in the MXF Header Metadata with a FFV1PictureEssenceDescriptor according to the rules defined in SMPTE 377-1 on how to link such descriptors with the Essence Container, and as shown in Table 5.

Table 5 – FFV1 Picture Essence Descriptor

| Item Name                | Type       | Len | UL Value     | Req ? | Meaning                                         | Default |
|--------------------------|------------|-----|--------------|-------|-------------------------------------------------|---------|
| FFV1 Picture Essence Descriptor | Set UL     | 16  | See table below | Req   | Defines the FFV1 Picture Essence Descriptor Set |         |
| Length                   | BER Length | 4   |                                                 | Req   | Set length   |         |
| <td colspan=5>All items from the MXF Format CDCI Descriptor</td>|
| FFV1InitializationMetadata | Datastream | 16  | 06 0e 2b 34 <br> (TBD) <br> (TBD)<br> (TBD) | D/Req | See Section 10.1.  |         |
| FFV1IdenticalGOP         | Boolean    | 1   | 06 0e 2b 34 <br> (TBD) <br> (TBD)<br> (TBD) | Opt   | TRUE if every GOP in the sequence is constructed the same. | FALSE |
| FFV1MaxGOP               | UInt16     | 2   | 06 0e 2b 34 <br> (TBD) <br> (TBD)<br> (TBD) | Opt   | Specifies the maximum occurring spacing between I frames. <br> A value of 0 or the absence of this property implies no limit to the maximum GOP | no limit |
| FFV1MaximumBitRate       | UInt32     | 4   | 06 0e 2b 34 <br> (TBD) <br> (TBD)<br> (TBD) | Opt   | Maximum bit rate of FFV1 video elementary stream in bit/s. |   |
| FFV1Version              | UInt8      | 1   | 06 0e 2b 34 <br> (TBD) <br> (TBD)<br> (TBD) | Opt   | Specifies the FFV1 video version. <br> Coded as per IETF RFC (to be defined)  |   |
| FFV1MicroVersion         | UInt8      | 1   | 06 0e 2b 34 <br> (TBD) <br> (TBD)<br> (TBD) | Opt   | Specifies the FFV1 video microversion. <br> Coded as per IETF RFC (to be defined) |   |

### 10.1   FFV1InitializationMetadata

This property encodes the Metadata defined in IETF RFC (to be defined) and shall be present for version 3 bitstreams. The value of the property shall consist of the content of ConfigurationRecord as defined in IETF RFC (to be defined).

### 10.2   Key Value

The set Key of the FFV1 Picture Descriptor shall be as defined in Table 6.

Table 6 – Key Value for the FFV1 Picture Essence Descriptor

| Byte No. | Description                    | Value | Meaning                                                                      |
|----------|--------------------------------|-------|------------------------------------------------------------------------------|
| 1~13     | As defined in SMPTE 377-1, Common Key Value for Structural Metadata (Table 13) |       | Values for all MXF structural metadata sets |
| 14~15    | Set Kind                       | (TBD) | Defines the Key value for the FFV1 Picture Essence Descriptor                |
| 16       | Reserved                       | 00h   | Reserved value                                                               |

### 10.3   Length Value

(Same as is SMPTE ST 2037 document)

## 11   Pre-Change

(Same as is SMPTE ST 2037 document)

## 12   Index Tables

(Same as is SMPTE ST 2037 document)

## Annex A  (Informative)

### Bibliography

FFV1 specification: IETF RFC (to be defined) 
(Same as is SMPTE ST 2037 document)
