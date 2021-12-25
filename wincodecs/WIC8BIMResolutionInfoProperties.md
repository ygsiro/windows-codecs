---
layout: interface
category: ENUMERATIONS
title: WIC8BIMResolutionInfoProperties
---

Specifies the identifiers of the metadata items in an 8BIMResolutionInfo block.

```cpp
typedef enum WIC8BIMResolutionInfoProperties {
  WIC8BIMResolutionInfoPString,
  WIC8BIMResolutionInfoHResolution,
  WIC8BIMResolutionInfoHResolutionUnit,
  WIC8BIMResolutionInfoWidthUnit,
  WIC8BIMResolutionInfoVResolution,
  WIC8BIMResolutionInfoVResolutionUnit,
  WIC8BIMResolutionInfoHeightUnit,
  WIC8BIMResolutionInfoProperties_FORCE_DWORD
} ;
```

## WIC8BIMResolutionInfoPString

 A name that identifies the 8BIM block.

## WIC8BIMResolutionInfoHResolution

The horizontal resolution of the image.

## WIC8BIMResolutionInfoHResolutionUnit

The units that the horizontal resolution is specified in; a 1 indicates pixels per inch and a 2 indicates pixels per centimeter.

## WIC8BIMResolutionInfoWidthUnit

The units that the image width is specified in; a 1 indicates inches, a 2 indicates centimeters, a 3 indicates points, a 4 specifies picas, and a 5 specifies columns.

## WIC8BIMResolutionInfoVResolution

The vertical resolution of the image.

## WIC8BIMResolutionInfoVResolutionUnit

The units that the vertical resolution is specified in; a 1 indicates pixels per inch and a 2 indicates pixels per centimeter.

## WIC8BIMResolutionInfoHeightUnit

The units that the image height is specified in; a 1 indicates inches, a 2 indicates centimeters, a 3 indicates points, a 4 specifies picas, and a 5 specifies columns.
