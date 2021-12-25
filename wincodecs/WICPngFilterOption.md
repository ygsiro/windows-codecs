---
layout: interface
category: ENUMERATIONS
title: WICPngFilterOption
---

Specifies the Portable Network Graphics (**PNG**) filters available for compression optimization.

```cpp
typedef enum WICPngFilterOption {
  WICPngFilterUnspecified,
  WICPngFilterNone,
  WICPngFilterSub,
  WICPngFilterUp,
  WICPngFilterAverage,
  WICPngFilterPaeth,
  WICPngFilterAdaptive,
  WICPNGFILTEROPTION_FORCE_DWORD
} ;
```

## WICPngFilterUnspecified

Indicates an unspecified PNG filter.
This enables WIC to algorithmically choose the best filtering option for the image.

## WICPngFilterNone

Indicates no PNG filter.

## WICPngFilterSub

Indicates a PNG sub filter.

## WICPngFilterUp

Indicates a PNG up filter.

## WICPngFilterAverage

Indicates a PNG average filter.

## WICPngFilterPaeth

Indicates a PNG paeth filter.

## WICPngFilterAdaptive

Indicates a PNG adaptive filter.
This enables WIC to choose the best filtering mode on a per-scanline basis.
