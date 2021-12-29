---
layout: interface
category: Interface
title: IWICFormatConverter
TOC:
  - name: Inheritance
  - name: CanConvert
  - name: Initialize
  - name: Related
code:
  - key: WICBitmapDitherType
  - key: IWICPalette
  - key: WICBitmapPaletteType
---

[wbs]: IWICBitmapSource

Represents an [IWICBitmapSource][wbs] that converts the image data from one pixel format to another, handling dithering and halftoning to indexed formats, palette translation and alpha thresholding.

## Inheritance

The **IWICFormatConverter** interface inherits from [IWICBitmapSource][wbs].
**IWICFormatConverter** also has these types of members:

- [CanConvert](#canconvert)
- [Initialize](#initialize)

## CanConvert

Determines if the source pixel format can be converted to the destination pixel format.

```cpp
HRESULT CanConvert(
   REFWICPixelFormatGUID srcPixelFormat, // [in]
   REFWICPixelFormatGUID dstPixelFormat, // [in]
   BOOL                  *pfCanConvert   // [out]
);
```

### CanConvert - Parameter

1. *srcPixelFormat* - The source pixel format.
2. *dstPixelFormat* - The destination pixel format.
3. *pfCanConvert* - A pointer that receives a value indicating whether the source pixel format can be converted to the destination pixel format.

### CanConvert - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## Initialize

Initializes the format converter.

```cpp
HRESULT Initialize(
    IWICBitmapSource      *pISource,             // [in]
    REFWICPixelFormatGUID dstFormat,             // [in]
    WICBitmapDitherType   dither,                // [in]
    IWICPalette           *pIPalette,            // [in]
    double                alphaThresholdPercent, // [in]
    WICBitmapPaletteType  paletteTranslate       // [in]
);
```

### Initialize - Parameter

1. *pISource* - The input bitmap to convert
2. *dstFormat* - The destination pixel format GUID.
3. *dither* - The WICBitmapDitherType used for conversion.
4. *pIPalette* - The palette to use for conversion.
5. *alphaThresholdPercent* - The alpha threshold to use for conversion.
6. *paletteTranslate* - The palette translation type to use for conversion.

### Initialize - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### Initialize - Remarks

If you do not have a predefined palette, you must first create one.
Use InitializeFromBitmap to create the palette object, then pass it in along with your other parameters.

[wbdt]: WICBitmapDitherType
[wbpt]: WICBitmapPaletteType

*dither*, *pIPalette*, *alphaThresholdPercent*, and *paletteTranslate* are used to mitigate color loss when converting to a reduced bit-depth format.
For conversions that do not need these settings, the following parameters values should be used: dither set to [WICBitmapDitherTypeNone][wbdt], *pIPalette* set to **NULL**, *alphaThresholdPercent* set to 0.0f, and *paletteTranslate* set to [WICBitmapPaletteTypeCustom][wbpt].

The basic algorithm involved when using an ordered dither requires a fixed palette, found in the [WICBitmapPaletteType][wbpt] enumeration, in a specific order.

Often, the actual palette provided for the output may have a different ordering or some slight variation in the actual colors.
This is the case when using the Microsoft Windows palette which has slight differences among versions of Windows.
To provide for this, a palette and a palette translation are given to the format converter.
The *pIPalette* is the actual destination palette to be used and the *paletteTranslate* is a fixed palette.
Once the conversion is complete, the colors are mapped from the fixed palette to the actual colors in *pIPalette* using a nearest color matching algorithm.

If colors in pIPalette do not closely match those in *paletteTranslate*, the mapping may produce undesirable results.

[WICBitmapDitherTypeOrdered4x4][wbdt] can be useful in format conversions from 8-bit formats to 5- or 6-bit formats as there is no way to accurately convert color data.

[WICBitmapDitherTypeErrorDiffusion][wbdt] selects the error diffusion algorithm and may be used with any palette.
If an arbitrary palette is provided, [WICBitmapPaletteCustom][wbpt] should be passed in as the *paletteTranslate*.
Error diffusion often provides superior results compared to the ordered dithering algorithms especially when combined with the optimized palette generation functionality on the [IWICPalette][wp].

[wp]: IWICPalette

When converting a bitmap which has an alpha channel, such as a Portable Network Graphics (**PNG**), to 8bpp, the alpha channel is normally ignored.
Any pixels which were transparent in the original bitmap show up as black in the final output because both transparent and black have pixel values of zero in the respective formats.

Some 8bpp content can contains an alpha color;
for instance, the Graphics Interchange Format (**GIF**) format allows for a single palette entry to be used as a transparent color.
For this type of content, *alphaThresholdPercent* specifies what percentage of transparency should map to the transparent color.
Because the alpha value is directly proportional to the opacity (not transparency) of a pixel, the *alphaThresholdPercent* indicates what level of opacity is mapped to the fully transparent color.

For instance, 9.8% implies that any pixel with an alpha value of less than 25 will be mapped to the transparent color.
A value of 100% maps all pixels which are not fully opaque to the transparent color.
Note that the palette should provide a transparent color.
If it does not, the 'transparent' color will be the one closest to zero - often black.

## Related

- [IWICImagingFactory::CreateFormatConverter](IWICImagingFactory#createformatconverter)
- [IWICFormatConverterInfo::CreateInstance](IWICFormatConverterInfo#createinstance)
