---
layout: interface
category: ENUMERATIONS
title: WICJpegScanType
---

Specifies the memory layout of pixel data in a JPEG image scan.

```cpp
typedef enum WICJpegScanType {
  WICJpegScanTypeInterleaved,
  WICJpegScanTypePlanarComponents,
  WICJpegScanTypeProgressive,
  WICJpegScanType_FORCE_DWORD
} ;
```

## WICJpegScanTypeInterleaved

The pixel data is stored in an interleaved memory layout.

## WICJpegScanTypePlanarComponents

The pixel data is stored in a planar memory layout.

## WICJpegScanTypeProgressive

The pixel data is stored in a progressive layout.
