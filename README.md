# Open LossLess in Standards

## Foreword

In cases where digital loss is not acceptable, lossless data compression has been changing the way the world stores and transmits its data. Nowadays most digital office documents use lossless compression (.docx, .xlsx, .odt, .pages) and lossless images are more ubiquitous (.png). Although uncompressed digital storage is an option, uncompressed data generally contains no fixity mechanisms and requires a generation of e-waste at a much faster rate than lossless formats. When the preservation of quality is a requirement, lossless compression is the green option.

Although lossless formats have been well adopted for images, documents and other media types; the adoption of lossless formats for audiovisual recordings has been much slower. Given the opportunity for lossless compression in audiovisual media, we also propose a focus on open formats, meaning:

- freedom to read, write, and use the format (NO PATENT)
- freedom to read, understand, and share the format's specification (NO PAYWALL)
- freedom to modify and distribute the format

We propose accelerating the implementation of lossless audiovisual formats with the following coordinated efforts:

- coordinated registration efforts for lossless formats with the principle audiovisual standards organizations (at least IANA, IETF, ISO, SMPTE)
- open documentation efforts of open, lossless audiovisual formats for relevant communities
- advocacy and promotion of open, lossless audiovisual formats to media application developers (both proprietary and open source)

Following with the work of the PREFORMA Project we are focused on 3 open lossless formats:

- Matroska, a file container able to transport different media stream
- FFV1, a lossless video coding format
- FLAC, a lossless audio coding format

This focus is not specific to the arrangement of these formats but regards their use in other contents as well, such as FFV1 in MXF or FLAC in QuickTime.

This page lists a summary about what we are doing about the registering of these formats in standard bodies used by open lossless formats people.  
Note: standardization of formats themselves is excluded of this summary (it is part of the [PREFORMA project](http://preforma-project.eu/)).

## Proposed Actions

### Matroska

- FFV1: currently using the AVI compatibility layer (similar to early version of AVC support), discussion to have a dedicated codec identifier for avoiding it (similar to current version of AVC support).  
If we decide to move, we need to do a PR on the [Matroska public repository](https://github.com/Matroska-Org/matroska-specification).

- FLAC: already done ("A_FLAC" identifier), [source](https://matroska.org/technical/specs/codecid/index.html).

### IANA

For HTTP(S) servers, RTP...  
Similar to [MIME Type Registration for MPEG-4](https://tools.ietf.org/html/rfc4337).  
We need to fill a [IANA form for media-types](https://www.iana.org/form/media-types).

- Matroska: registering video/matroska (1+ video), audio/matroska (0 video 1+ audio), application/matroska (0 video 0 audio 1+ other)
- FFV1: registering "video/FFV1".
- FLAC: registering "audio/FLAC".

### MP4/QuickTime

- FFV1: registering "FFV1".
- FLAC: registering "FLAC".

### MXF  

Standardize the implementation of FFV1 and FLAC within the MXF container. Standard subscriber fees have already been provided by Jérôme Martinez.  
Attend physical SMPTE meetings in support of work to standardize FLAC and FFV1 in MXF.

References:  
[Discussion on Twitter](https://twitter.com/MrMXF/status/824535480314265601)  
[Blog by Bruce Devlin on the process](http://mrmxf.com/blog/how-to-put-a-new-codec-into-mxf/)

We have a [Proposal](https://github.com/MediaArea/ollistd/blob/master/MXF_FFV1.md).

### FFmpeg  

FFmpeg is a reference open source, cross-platform solution to record, convert and stream audio and video.  
After/during registering, we need to update FFmpeg in order to have a reference tool for the new codec identifiers. 

## Status

| Entity    | Format   | Begin         | In specs      | In FFmpeg     | Remarks                                |
|-----------|----------|---------------|---------------|---------------|----------------------------------------|
| Matroska  | FFV1     | 2017-02-04    | 2017-02-05    | 2017-02-05    |                                        |
| Matroska  | FLAC     | N/A           | Already done  | Already done? |                                        |
| IANA      | Matroska |               |               |               |                                        |
| IANA      | FFV1     |               |               |               |                                        |
| IANA      | FLAC     |               |               |               |                                        |
| MP4       | FFV1     |               |               |               |                                        |
| MP4       | FLAC     |               |               |               |                                        |
| QuickTime | FFV1     |               |               |               |                                        |
| QuickTime | FLAC     |               |               |               |                                        |
| MXF       | FFV1     | 2017-01-27    |               |               | [Proposal](https://github.com/MediaArea/ollistd/blob/master/MXF_FFV1.md)                                       |
| MXF       | FLAC     |               |               |               |                                        |

## Timeline

- 2017-01-27 MXF, [discussion with MrMXF](https://twitter.com/MrMXF/status/824535480314265601).
- 2017-02-04 Matroska, [proposal of V\_FFV1 (FFV1 in Matroska) on CELLAR](https://mailarchive.ietf.org/arch/search/?email_list=cellar&gbt=1&index=Kir-8JdOl6DTZFPrxy4XM-iRP7Q).
- 2017-02-05 Matroska, [FFV1 in Matroska PR](https://github.com/Matroska-Org/matroska-specification/pull/94) is accepted.
- 2017-02-10 Global, public communication about this page

## Costs

Based on $100/hour labor

- Matroska: expected $100 labor for discussion about V\_FFV1 and PR + $400 labor if decision to register V\_FFV1 for FFmpeg patch.
- IANA: expected $400 labor for filling forms
- MP4/QuickTime: expected $200 labor for sending emails
- MXF: expected few k$ to several 10k$ SMPTE (writing, travels) + FFmpeg patch (to be defined)

## Sponsoring

- [PREFORMA](http://www.preforma-project.eu/), project co-funded by the [European Commission](http://europa.eu/) is focused on Matroska and FFV1 standardization; Matroska and IANA registration is included in the sponsorship of [MediaConch](https://mediaarea.net/MediaConch).
- Other: [NeedSponsor](mailto:info@mediaarea.net).

## Keep in touch!

You can modify this page: [source of this page](https://github.com/MediaArea/ollistd).  
