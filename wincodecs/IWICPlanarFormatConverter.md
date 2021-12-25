---
layout: interface
category: Interface
title: IWICPlanarFormatConverter
TOC:
  - name: Inheritance
  - name: CanConvert
  - name: Initialize
code:
  - key: WICBitmapDitherType
  - key: IWICBitmapSource
  - key: IWICPalette
  - key: WICBitmapPaletteType
---

Allows a format converter to be initialized with a planar source.

## Inheritance

The **IWICPlanarFormatConverter** interface inherits from [IWICBitmapSource][wbs].
**IWICPlanarFormatConverter** also has these types of members:

- [CanConvert](#canconvert)
- [Initialize](#initialize)

[wbs]: IWICBitmapSource

## CanConvert

Query if the format converter can convert from one format to another.

```cpp
HRESULT CanConvert(
    const WICPixelFormatGUID *pSrcPixelFormats, // [in]
    UINT                     cSrcPlanes,        // [in]
    REFWICPixelFormatGUID    dstPixelFormat,    // [in]
    BOOL                     *pfCanConvert      // [out]
);
```

### CanConvert - Parameter

1. _pSrcPixelFormats_ - An array of WIC pixel formats that represents source image planes.
2. _cSrcPlanes_ - The number of source pixel formats specified by the _pSrcFormats_ parameter.
3. _dstPixelFormat_ - The destination interleaved pixel format.
4. _pfCanConvert_ - True if the conversion is supported.

### CanConvert - Return value

If the conversion is not supported, this method returns **S_OK**, but \*_pfCanConvert_ is set to **FALSE**.

If this method fails, the out parameter pfCanConvert is invalid.

### CanConvert - Remarks

To specify an interleaved input pixel format, provide a length 1 array to *pSrcPixelFormats*.

## Initialize

Initializes a format converter with a planar source, and specifies the interleaved output pixel format.

```cpp
HRESULT Initialize(
    IWICBitmapSource      **ppPlanes,            // [in]
    UINT                  cPlanes,               // [in]
    REFWICPixelFormatGUID dstFormat,             // [in]
    WICBitmapDitherType   dither,                // [in]
    IWICPalette           *pIPalette,            // [in]
    double                alphaThresholdPercent, // [in]
    WICBitmapPaletteType  paletteTranslate       // [in]
);
```

### Initialize - Parameter

1. _ppPlanes_ - An array of [IWICBitmapSource][wbs] that represents image planes.
2. _cPlanes_ - The number of component planes specified by the planes parameter.
3. _dstFormat_ - The destination interleaved pixel format.
4. _dither_ - The [WICBitmapDitherType][wbdt] used for conversion.
5. _pIPalette_ - The palette to use for conversion.
6. _alphaThresholdPercent_ - The alpha threshold to use for conversion.
7. _paletteTranslate_ - The palette translation type to use for conversion.

[wbdt]: WICBitmapDitherType

### Initialize - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.
