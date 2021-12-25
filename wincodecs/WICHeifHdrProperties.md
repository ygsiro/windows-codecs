---
layout: interface
category: ENUMERATIONS
title: WICHeifHdrProperties
---

Specifies the HDR properties of a High Efficiency Image Format (**HEIF**) image.

```cpp
typedef enum WICHeifHdrProperties {
  WICHeifHdrMaximumLuminanceLevel,
  WICHeifHdrMaximumFrameAverageLuminanceLevel,
  WICHeifHdrMinimumMasteringDisplayLuminanceLevel,
  WICHeifHdrMaximumMasteringDisplayLuminanceLevel,
  WICHeifHdrCustomVideoPrimaries,
  WICHeifHdrProperties_FORCE_DWORD
};
```

## WICHeifHdrMaximumLuminanceLevel

Specifies the maximum luminance level of the content in Nits.

## WICHeifHdrMaximumFrameAverageLuminanceLevel

Specifies the maximum average per-frame luminance level of the content in Nits.

## WICHeifHdrMinimumMasteringDisplayLuminanceLevel

Specifies the maximum luminance of the display on which the content was authored, in Nits.

## WICHeifHdrMaximumMasteringDisplayLuminanceLevel

Specifies the maximum luminance of the display on which the content was authored, in Nits.

## WICHeifHdrCustomVideoPrimaries

Specifies custom color primaries for a video media type. The value of this property is a **MT_CUSTOM_VIDEO_PRIMARIESstructure**, returned as an array of bytes (VT_BLOB).

## Remarks

[wmr]: IWicMetadataReader
[wmr-gv]: IWicMetadataReader#getvalue
[wmr-gmf]: IWicMetadataReader#getmetadataformat

Use [IWicMetadataReader][wmr]::[GetValue][wmr-gv] to retrieve the value of the properties specified with this enumeration. Instantiate the [IWicMetadataReader][wmr] instance using the GUID **CLSID_WICMetadataReader**.
Call [IWicMetadataReader][wmr]::[GetMetadataFormat][wmr-gmf] and confirm that the value is **GUID_MetadataFormatHeifHDR** to verify that the metadata format is HEIF HDR metadata.

Not all HEIF HDR images will have all of these properties present in the file, so only those properties that are available will be exposed by the metadata reader.
