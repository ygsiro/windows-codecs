---
layout: interface
category: ENUMERATIONS
title: WICTiffCompressionOption
---

Specifies the Tagged Image File Format (**TIFF**) compression options.

```cpp
typedef enum WICTiffCompressionOption {
  WICTiffCompressionDontCare,
  WICTiffCompressionNone,
  WICTiffCompressionCCITT3,
  WICTiffCompressionCCITT4,
  WICTiffCompressionLZW,
  WICTiffCompressionRLE,
  WICTiffCompressionZIP,
  WICTiffCompressionLZWHDifferencing,
  WICTIFFCOMPRESSIONOPTION_FORCE_DWORD
};
```

## WICTiffCompressionDontCare

Indicates a suitable compression algorithm based on the image and pixel format.

## WICTiffCompressionNone

Indicates no compression.

## WICTiffCompressionCCITT3

Indicates a CCITT3 compression algorithm. This algorithm is only valid for 1bpp pixel formats.

## WICTiffCompressionCCITT4

Indicates a CCITT4 compression algorithm. This algorithm is only valid for 1bpp pixel formats.

## WICTiffCompressionLZW

Indicates a LZW compression algorithm.

## WICTiffCompressionRLE

Indicates a RLE compression algorithm. This algorithm is only valid for 1bpp pixel formats.

## WICTiffCompressionZIP

Indicates a ZIP compression algorithm.

## WICTiffCompressionLZWHDifferencing

Indicates an LZWH differencing algorithm.
