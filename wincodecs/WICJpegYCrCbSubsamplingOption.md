---
layout: interface
category: ENUMERATIONS
title: WICJpegYCrCbSubsamplingOption
---

Specifies the JPEG `YCrCB` subsampling options.

```cpp
typedef enum WICJpegYCrCbSubsamplingOption {
  WICJpegYCrCbSubsamplingDefault,
  WICJpegYCrCbSubsampling420,
  WICJpegYCrCbSubsampling422,
  WICJpegYCrCbSubsampling444,
  WICJpegYCrCbSubsampling440,
  WICJPEGYCRCBSUBSAMPLING_FORCE_DWORD
} ;
```

## WICJpegYCrCbSubsamplingDefault

The default subsampling option.

## WICJpegYCrCbSubsampling420

Subsampling option that uses both horizontal and vertical decimation.

## WICJpegYCrCbSubsampling422

Subsampling option that uses both horizontal and vertical decimation.

## WICJpegYCrCbSubsampling444

Subsampling option that uses no decimation.

## WICJpegYCrCbSubsampling440

Subsampling option that uses 2x vertical downsampling only. This option is only available in Windows 8.1 and later.

## Remarks

The native JPEG encoder uses **WICJpegYCrCbSubsampling420**.
