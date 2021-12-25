---
layout: interface
category: Interface
title: IWICBitmapScaler
TOC:
  - name: Inheritance
  - name: Remarks
  - name: Initialize
code:
  - key: IWICBitmapSource
  - key: WICBitmapInterpolationMode
---

Represents a resized version of the input bitmap using a resampling or filtering algorithm.

## Inheritance

The **IWICBitmapScaler** interface inherits from IWICBitmapSource.
**IWICBitmapScaler** also has these types of members:

## Remarks

Images can be scaled to larger sizes;
however, even with sophisticated scaling algorithms, there is only so much information in the image and artifacts tend to worsen the more you scale up.

The scaler will reapply the resampling algorithm every time CopyPixels is called.
If the scaled image is to be animated, the scaled image should be created once and cached in a new bitmap, after which the **IWICBitmapScaler** may be released.
In this way the scaling algorithm - which may be computationally expensive relative to drawing - is performed only once and the result displayed many times.

The scaler is optimized to use the minimum amount of memory required to scale the image correctly.
The scaler may be used to produce parts of the image incrementally (banding) by calling CopyPixels with different rectangles representing the output bands of the image.
Resampling typically requires overlapping rectangles from the source image and thus may need to request the same pixels from the source bitmap multiple times.
Requesting scanlines out-of-order from some image decoders can have a significant performance penalty.
Because of this reason, the scaler is optimized to handle consecutive horizontal bands of scanlines (rectangle width equal to the bitmap width).
In this case the accumulator from the previous vertically adjacent rectangle is re-used to avoid duplicate scanline requests from the source.
This implies that banded output from the scaler may have better performance if the bands are requested sequentially.
Of course if the scaler is simply used to produce a single rectangle output, this concern is eliminated because the scaler will internally request scanlines in the correct order.

## Initialize

Initializes the bitmap scaler with the provided parameters.

```cpp
HRESULT Initialize(
   IWICBitmapSource           *pISource, // [in]
   UINT                       uiWidth,   // [in]
   UINT                       uiHeight,  // [in]
   WICBitmapInterpolationMode mode       // [in]
);
```

### Initialize - Parameter

1. *pISource* - The input bitmap source.
2. *uiWidth* - The destination width.
3. *uiHeight* - The destination height.
4. *mode* - The [WICBitmapInterpolationMode][wbim] to use when scaling.

[wbim]: WICBitmapInterpolationMode

### Initialize - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### Initialize - Remarks

**IWICBitmapScaler** can't be initialized multiple times.
For example, when scaling every frame in a multi-frame image, a new **IWICBitmapScaler** must be created and initialized for each frame.
