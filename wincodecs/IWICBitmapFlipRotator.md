---
layout: interface
category: Interface
title: IWICBitmapFlipRotator
code:
  - key: IWICBitmapSource
  - key: WICBitmapTransformOptions
TOC:
  - name: Inheritance
  - name: Initialize
  - name: Related
---

Exposes methods that produce a flipped (horizontal or vertical) and/or rotated (by 90 degree increments) bitmap source.
The flip is done before the rotation.

## Inheritance

The **IWICBitmapFlipRotator** interface inherits from [IWICBitmapSource][wbs].
**IWICBitmapFlipRotator** also has these types of members:

- [Initialize](#initialize)

## Remarks

**IWICBitmapFipRotator** requests data on a per-pixel basis, while WIC codecs provide data on a per-scanline basis.
This causes the fliprotator object to exhibit n² behavior if there is no buffering.
This occurs because each pixel in the transformed image requires an entire scanline to be decoded in the file.
It is recommended that you buffer the image using [IWICBitmap][wb], or flip/rotate the image using Direct2D.

## Initialize

Initializes the bitmap flip rotator with the provided parameters.

```cpp
HRESULT Initialize(
  IWICBitmapSource          *pISource, // [in]
  WICBitmapTransformOptions options    // [in]
);
```

### Initialize - Parameters

1. _pISource_ - The input bitmap source.
2. _options_ - The [WICBitmapTransformOptions][wbtfo] to flip or rotate the image.

### Initialize - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

[wbtfo]: WICBitmapTransformOptions
[wb]: IWICBitmap
[wbs]: IWICBitmapSource

## Related

- [IWICImagingFactory::CreateBitmapFlipRotator](IWICImagingFactory#createbitmapfliprotator)
