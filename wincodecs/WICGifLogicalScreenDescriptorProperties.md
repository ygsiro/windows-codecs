---
layout: interface
category: ENUMERATIONS
title: WICGifLogicalScreenDescriptorProperties
---

Specifies the logical screen descriptor properties for Graphics Interchange Format (**GIF**) metadata.

```cpp
typedef enum WICGifLogicalScreenDescriptorProperties {
  WICGifLogicalScreenSignature,
  WICGifLogicalScreenDescriptorWidth,
  WICGifLogicalScreenDescriptorHeight,
  WICGifLogicalScreenDescriptorGlobalColorTableFlag,
  WICGifLogicalScreenDescriptorColorResolution,
  WICGifLogicalScreenDescriptorSortFlag,
  WICGifLogicalScreenDescriptorGlobalColorTableSize,
  WICGifLogicalScreenDescriptorBackgroundColorIndex,
  WICGifLogicalScreenDescriptorPixelAspectRatio,
  WICGifLogicalScreenDescriptorProperties_FORCE_DWORD
} ;
```

## WICGifLogicalScreenSignature

Indicates the signature property.

## WICGifLogicalScreenDescriptorWidth

Indicates the width in pixels.

## WICGifLogicalScreenDescriptorHeight

Indicates the height in pixels.

## WICGifLogicalScreenDescriptorGlobalColorTableFlag

Indicates the global color table flag.
**TRUE** if a global color table is present; otherwise, **FALSE**.

## WICGifLogicalScreenDescriptorColorResolution

Indicates the color resolution in bits per pixel.

## WICGifLogicalScreenDescriptorSortFlag

Indicates the sorted color table flag.
**TRUE** if the table is sorted; otherwise, **FALSE**.

## WICGifLogicalScreenDescriptorGlobalColorTableSize

Indicates the value used to calculate the number of bytes contained in the global color table.

To calculate the actual size of the color table, raise 2 to the value of the field + 1.

## WICGifLogicalScreenDescriptorBackgroundColorIndex

Indicates the index within the color table to use for the background (pixels not defined in the image).

## WICGifLogicalScreenDescriptorPixelAspectRatio

Indicates the factor used to compute an approximation of the aspect ratio.
