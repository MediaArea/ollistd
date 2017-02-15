# Mapping FFV1 into the MP4

This document represents preparation notes for a request to mp4ra.org to register FFV1 for use in MP4, following the instructions at the [mp4ra.org request page](http://www.mp4ra.org/request.html).

## Email Request

Draft of email.

### For registration with ISO
to: mp4reg@group.apple.com
subject: mp4reg FFV1

### For registration with QuickTime
to: qtfourcc@group.apple.com
subject: qtreg FFV1

### Email Message

Dave Rice of Chemin du Vernay, Curienne, France 73190 at MediaArea SARL requests the registration of an identifier for a lossless video encoding, FFV1, which is presently under standardization within the IETF [cellar working group](https://datatracker.ietf.org/wg/cellar/charter/).

This request is for a codec kind of codepoint with a video stream type. The recommended identifier is "FFV1". The specification was initially published by FFmpeg at http://ffmpeg.org/~michael/ffv1.html. Presently the specification is under development by the IETF cellar working group and the most up-to-date copies of the specification are available at https://datatracker.ietf.org/doc/draft-niedermayer-cellar-ffv1/ (possibly changing to https://datatracker.ietf.org/doc/draft-ietf-cellar-ffv1/ later). Development work on the specification may be viewed at https://github.com/FFmpeg/FFV1.

FFV1's specification defines several versions of FFV1, currently version 0, 1, and 3. Versions 3 and higher of FFV1 require storage of a "ConfigurationRecord" to initialize the decoding. This ConfigurationRecord is defined in the FFV1 specification draft at https://datatracker.ietf.org/doc/draft-niedermayer-cellar-ffv1/. The ConfigurationRecord extends the sample description box ("moov", "trak", "mdia", "minf", "stbl", "stsd") with a "glbl" box which contains the ConfigurationRecord bitstream.

The codec could be briefly described as: "FFV1, an open lossless intra-frame video codec".

An authorized representation for the code-point may be contacted at:
Dave Rice
dave .at. dericed.com
MediaArea SARL
Chemin du Vernay
Curienne
France
73190

Inquiries about FFV1 may also be directed to the ffmpeg-devel listserv at https://ffmpeg.org/mailman/listinfo/ffmpeg-devel or the IETF cellar working group at https://datatracker.ietf.org/wg/cellar/email/.

The date of the definition or implementation could be set to June 9, 2003 when FFV1 was initially released. Or August 3, 2013 when the latest version of FFV1 was released. A date for the official release of the specification for FFV1 from the IETF is not yet known, though earlier version of the specification were released by FFmpeg as recently as 2013.

There are currently at least two FFV1 encoders, in libav and ffmpeg, and both utilize the "FFV1" codec id and storage of the ConfigurationRecord in the glbl atom as specified above.

Please feel welcome to contact us with any questions, comments, or recommendations about this request. Thanks much.
