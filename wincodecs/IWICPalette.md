---
layout: interface
category: Interface
title: IWICPalette
TOC:
  - name: Inheritance
  - name: Remarks
  - name: GetColorCount
  - name: GetColors
  - name: GetType
  - name: HasAlpha
  - name: InitializeCustom
  - name: InitializeFromBitmap
  - name: InitializeFromPalette
  - name: InitializePredefined
  - name: IsBlackWhite
  - name: IsGrayscale
  - name: Related
code:
  - key: WICColor
---

Exposes methods for accessing and building a color table, primarily for indexed pixel formats.

## Inheritance

The **IWICPalette** interface inherits from the IUnknown interface.
**IWICPalette** also has these types of members:

- [GetColorCount](#getcolorcount)
- [GetColors](#getcolors)
- [GetType](#gettype)
- [HasAlpha](#hasalpha)
- [InitializeCustom](#initializecustom)
- [InitializeFromBitmap](#initializefrombitmap)
- [InitializeFromPalette](#initializefrompalette)
- [InitializePredefined](#initializepredefined)
- [IsBlackWhite](#isblackwhite)
- [IsGrayscale](#isgrayscale)

## Remarks

[wbpc]: WICBitmapPaletteType

If the [WICBitmapPaletteType][wbpc] is not [WICBitmapPaletteCustom][wbpc], then the colors are automatically generated based on the table above.
If the user subsequently changes a color palette entry the [WICBitmapPalette][wbpc] is set to Custom by that action.

InitializeFromBitmap's fAddTransparentColor parameter will add a transparent color to the end of the color collection if its size if less than 256, otherwise index 255 will be replaced with the transparent color.
If a pre-defined palette type is used, it will change to BitmapPaletteTypeCustom since it no longer matches the predefined palette.

The palette interface is an auxiliary imaging interface in that it does not directly concern bitmaps and pixels;
rather it provides indexed color translation for indexed bitmaps.
For an indexed pixel format with M bits per pixels: (The number of colors in the palette) greater than 2^M.

Traditionally the basic operation of the palette is to provide a translation from a byte (or smaller) index into a 32bpp color value. This is often accomplished by a 256 entry table of color values.

## GetColorCount

Retrieves the number of colors in the color table.

```cpp
HRESULT GetColorCount(
    UINT *pcCount // [out]
);
```

### GetColorCount - Parameter

1. *pcCount* - Pointer that receives the number of colors in the color table.

### GetColorCount - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## GetColors

Fills out the supplied color array with the colors from the internal color table.
The color array should be sized according to the return results from GetColorCount.

```cpp
HRESULT GetColors(
    UINT     cCount, // [in]
    WICColor *pColors, // [out]
    UINT     *pcActualColors // [out]
);
```

### GetColors - Parameter

1. *cCount* - The size of the pColors array.
2. *pColors* - Pointer that receives the colors of the palette.
3. *pcActualColors* - The actual size needed to obtain the palette colors.

### GetColors - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## GetType

Retrieves the [WICBitmapPaletteType][wbpc] that describes the palette.

```cpp
HRESULT GetType(
    WICBitmapPaletteType *pePaletteType // [out]
);
```

### GetType - Parameter

1. *pePaletteType* - Pointer that receives the palette type of the bimtap.

### GetType - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### GetType - Remarks

[WICBitmapPaletteCustom][wbpc] is used for palettes initialized from both [InitializeCustom](#initializecustom) and [InitializeFromBitmap](#initializefrombitmap).
There is no distinction is made between optimized and custom palettes.

## HasAlpha

Indicates whether the palette contains an entry that is non-opaque (that is, an entry with an alpha that is less than 1).

```cpp
HRESULT HasAlpha(
    BOOL *pfHasAlpha // [out]
);
```

### HasAlpha - Parameter

1. *pfHasAlpha* - Pointer that receives **TRUE** if the palette contains a transparent color; otherwise, **FALSE**.

### HasAlpha - Return value

If this method succeeds, it returns **S_OK**. Otherwise, it returns an **HRESULT** error code.

### HasAlpha - Remarks

Various image formats support alpha in different ways.
PNG has full alpha support by supporting partially transparent palette entries.
GIF stores colors as 24bpp, without alpha, but allows one palette entry to be specified as fully transparent.
If a palette has multiple fully transparent entries (0x00RRGGBB), GIF will use the last one as its transparent index.

## InitializeCustom

Initializes a palette to the custom color entries provided.

```cpp
HRESULT InitializeCustom(
    WICColor *pColors, // [in]
    UINT     cCount    // [in]
);
```

### InitializeCustom - Parameter

1. *pColors* - Pointer to the color array.
2. *cCount* - The number of colors in pColors.

### InitializeCustom - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### InitializeCustom - Remarks

If a transparent color is required, provide it as part of the custom entries.
To add a transparent value to the palette, its alpha value must be 0 (0x00RRGGBB).

The entry count is limited to 256.

## InitializeFromBitmap

Initializes a palette using a computed optimized values based on the reference bitmap.

```cpp
HRESULT InitializeFromBitmap(
    IWICBitmapSource *pISurface,          // [in]
    UINT             cCount,              // [in]
    BOOL             fAddTransparentColor // [in]
);
```

### InitializeFromBitmap - Parameter

1. *pISurface* - Pointer to the source bitmap.
2. *cCount* - The number of colors to initialize the palette with.
3. *fAddTransparentColor* - A value to indicate whether to add a transparent color.

### InitializeFromBitmap - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### InitializeFromBitmap - Remarks

The resulting palette contains the specified number of colors which best represent the colors present in the bitmap.
The algorithm operates on the opaque RGB color value of each pixel in the reference bitmap and hence ignores any alpha values.
If a transparent color is required, set the *fAddTransparentColor* parameter to TRUE and one fewer optimized color will be computed, reducing the colorCount, and a fully transparent color entry will be added.

## InitializeFromPalette

Initialize the palette based on a given palette.

```cpp
HRESULT InitializeFromPalette(
    **IWICPalette** *pIPalette // [in]
);
```

### InitializeFromPalette - Parameter

1. *pIPalette* - Pointer to the source palette.

### InitializeFromPalette - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## InitializePredefined

Initializes the palette to one of the pre-defined palettes specified by [WICBitmapPaletteType][wbpc] and optionally adds a transparent color.

```cpp
HRESULT InitializePredefined(
    WICBitmapPaletteType ePaletteType,        // [in]
    BOOL                 fAddTransparentColor // [in]
);
```

### InitializePredefined - Parameter

1. *ePaletteType* - The desired pre-defined palette type.
2. *fAddTransparentColor* - The optional transparent color to add to the palette.
   If no transparent color is needed, use 0.
   When initializing to a grayscale or black and white palette, set this parameter to **FALSE**.

### InitializePredefined - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### InitializePredefined - Remarks

If a transparent color is added to a palette, the palette is no longer predefined and is returned as [WICBitmapPaletteTypeCustom][wbpc].
For palettes with less than 256 entries, the transparent entry is added to the end of the palette (that is, a 16-color palette becomes a 17-color palette).
For palettes with 256 colors, the transparent palette entry will replace the last entry in the pre-defined palette.

## IsBlackWhite

Retrieves a value that describes whether the palette is black and white.

```cpp
HRESULT IsBlackWhite(
    BOOL *pfIsBlackWhite // [out]
);
```

### IsBlackWhite - Parameter

1. *pfIsBlackWhite* - A pointer to a variable that receives a boolean value that indicates whether the palette is black and white. **TRUE** indicates that the palette is black and white; otherwise, **FALSE**.

### IsBlackWhite - Return value

If this method succeeds, it returns **S_OK**. Otherwise, it returns an **HRESULT** error code.

### IsBlackWhite - Remarks

A palette is considered to be black and white only if it contains exactly two entries, one full black (0xFF000000) and one full white (0xFFFFFFF).

## IsGrayscale

Retrieves a value that describes whether a palette is grayscale.

```cpp
HRESULT IsGrayscale(
    BOOL *pfIsGrayscale // [out]
);
```

### IsGrayscale - Parameter

1. *pfIsGrayscale* - A pointer to a variable that receives a boolean value that indicates whether the palette is grayscale.
   **TRUE** indicates that the palette is grayscale; otherwise **FALSE**.

### IsGrayscale - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### IsGrayscale - Remarks

A palette is considered grayscale only if, for every entry, the alpha value is 0xFF and the red, green and blue values match.

## Related

- [IWICImagingFactory::CreatePalette](IWICImagingFactory#createpalette)
