---
layout: interface
category: Interface
title: IWICColorTransform
TOC:
  - name: Inheritance
  - name: Remarks
  - name: Initialize
  - name: Related
code:
  - key: IWICBitmapSource
  - key: IWICColorContext
---

Exposes methods that transforms an [IWICBitmapSource][wbs] from one color context to another.

[wbs]: IWICBitmapSource

## Inheritance

The **IWICColorTransform** interface inherits from [IWICBitmapSource][wbs].
**IWICColorTransform** also has these types of members:

- [Initialize](#initialize)

## Remarks

A **IWICColorTransform** is an imaging pipeline component that knows how to pull pixels obtained from a given [IWICBitmapSource][wbs] through a color transform.
The color transform is defined by mapping colors from the source color context to the destination color context in a given output pixel format.

Once initialized, a color transform cannot be reinitialized.
Because of this, a color transform cannot be used with multiple sources or varying parameters.

## Initialize

[wcc]: IWICColorContext

Initializes an **IWICColorTransform** with a [IWICBitmapSource][wbs] and transforms it from one [IWICColorContext][wcc] to another.

```cpp
HRESULT Initialize(
   IWICBitmapSource      *pIBitmapSource,  // [in]
   IWICColorContext      *pIContextSource, // [in]
   IWICColorContext      *pIContextDest,   // [in]
   REFWICPixelFormatGUID pixelFmtDest      // [in]
);
```

### Initialize - Parameter

1. _pIBitmapSource_ - The bitmap source used to initialize the color transform.
2. _pIContextSource_ - The color context source.
3. _pIContextDest_ - The color context destination.
4. _pixelFmtDest_ - The GUID of the desired pixel format.
   This parameter is limited to a subset of the native WIC pixel formats, see Remarks for a list.

### Initialize - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### Initialize - Remarks

The currently supported formats for the _pIContextSource_ and _pixelFmtDest_ parameters are:

- **GUID_WICPixelFormat8bppGray**
- **GUID_WICPixelFormat16bppGray**
- **GUID_WICPixelFormat16bppBGR555**
- **GUID_WICPixelFormat16bppBGR565**
- **GUID_WICPixelFormat24bppBGR**
- **GUID_WICPixelFormat24bppRGB**
- **GUID_WICPixelFormat32bppBGR**
- **GUID_WICPixelFormat32bppBGRA**
- **GUID_WICPixelFormat32bppPBGRA**
- **GUID_WICPixelFormat32bppPRGBA** (Windows 8 and later)
- **GUID_WICPixelFormat32bppRGBA**
- **GUID_WICPixelFormat32bppBGR101010**
- **GUID_WICPixelFormat32bppCMYK**
- **GUID_WICPixelFormat48bppBGR**
- **GUID_WICPixelFormat64bppBGRA** (Windows 8 and later)
- **GUID_WICPixelFormat64bppPBGRA** (Windows 8 and later)
- **GUID_WICPixelFormat64bppPRGBA** (Windows 8 and later)
- **GUID_WICPixelFormat64bppRGBA** (Windows 8 and later)

In order to get correct behavior from a color transform, the input and output pixel formats must be compatible with the source and destination color profiles.
For example, an sRGB destination color profile will produce incorrect results when used with a CMYK destination pixel format.

## Related

- [IWICImagingFactory::CreateColorTransformer](IWICImagingFactory#createcolortransformer)
