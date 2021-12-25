---
layout: interface
category: ENUMERATIONS
title: WICPlanarOptions
---

Specifies additional options to an IWICPlanarBitmapSourceTransform implementation.

```cpp
typedef enum WICPlanarOptions {
  WICPlanarOptionsDefault,
  WICPlanarOptionsPreserveSubsampling,
  WICPLANAROPTIONS_FORCE_DWORD
} ;
```

## WICPlanarOptionsDefault

No options specified.

WIC JPEG Decoder: The default behavior for iDCT scaling is to preserve quality when downscaling by downscaling only the Y plane in some cases, and the image may change to 4:4:4 chroma subsampling.

## WICPlanarOptionsPreserveSubsampling

Asks the source to preserve the size ratio between planes when scaling.

WIC JPEG Decoder: Specifying this option causes the JPEG decoder to scale luma and chroma planes by the same amount, so a 4:2:0 chroma subsampled image outputs 4:2:0 data when downscaling by 2x, 4x, or 8x.
