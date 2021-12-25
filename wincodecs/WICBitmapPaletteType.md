---
layout: interface
category: ENUMERATIONS
title: WICBitmapPaletteType
---

Specifies the type of palette used for an indexed image format.

```cpp
typedef enum WICBitmapPaletteType {
  WICBitmapPaletteTypeCustom,
  WICBitmapPaletteTypeMedianCut,
  WICBitmapPaletteTypeFixedBW,
  WICBitmapPaletteTypeFixedHalftone8,
  WICBitmapPaletteTypeFixedHalftone27,
  WICBitmapPaletteTypeFixedHalftone64,
  WICBitmapPaletteTypeFixedHalftone125,
  WICBitmapPaletteTypeFixedHalftone216,
  WICBitmapPaletteTypeFixedWebPalette,
  WICBitmapPaletteTypeFixedHalftone252,
  WICBitmapPaletteTypeFixedHalftone256,
  WICBitmapPaletteTypeFixedGray4,
  WICBitmapPaletteTypeFixedGray16,
  WICBitmapPaletteTypeFixedGray256,
  WICBITMAPPALETTETYPE_FORCE_DWORD
} ;
```

## WICBitmapPaletteTypeCustom

An arbitrary custom palette provided by caller.

## WICBitmapPaletteTypeMedianCut

An optimal palette generated using a median-cut algorithm. Derived from the colors in an image.

## WICBitmapPaletteTypeFixedBW

A black and white palette.

## WICBitmapPaletteTypeFixedHalftone8

A palette that has its 8-color on-off primaries and the 16 system colors added. With duplicates removed, 16 colors are available.

## WICBitmapPaletteTypeFixedHalftone27

A palette that has 3 intensity levels of each primary: 27-color on-off primaries and the 16 system colors added. With duplicates removed, 35 colors are available.

## WICBitmapPaletteTypeFixedHalftone64

A palette that has 4 intensity levels of each primary: 64-color on-off primaries and the 16 system colors added. With duplicates removed, 72 colors are available.

## WICBitmapPaletteTypeFixedHalftone125

A palette that has 5 intensity levels of each primary: 125-color on-off primaries and the 16 system colors added. With duplicates removed, 133 colors are available.

## WICBitmapPaletteTypeFixedHalftone216

A palette that has 6 intensity levels of each primary: 216-color on-off primaries and the 16 system colors added. With duplicates removed, 224 colors are available. This is the same as **WICBitmapPaletteFixedHalftoneWeb**.

## WICBitmapPaletteTypeFixedWebPalette

A palette that has 6 intensity levels of each primary: 216-color on-off primaries and the 16 system colors added. With duplicates removed, 224 colors are available. This is the same as **WICBitmapPaletteTypeFixedHalftone216**.

## WICBitmapPaletteTypeFixedHalftone252

A palette that has its 252-color on-off primaries and the 16 system colors added. With duplicates removed, 256 colors are available.

## WICBitmapPaletteTypeFixedHalftone256

A palette that has its 256-color on-off primaries and the 16 system colors added. With duplicates removed, 256 colors are available.

## WICBitmapPaletteTypeFixedGray4

A palette that has 4 shades of gray.

## WICBitmapPaletteTypeFixedGray16

A palette that has 16 shades of gray.

## WICBitmapPaletteTypeFixedGray256

A palette that has 256 shades of gray.
