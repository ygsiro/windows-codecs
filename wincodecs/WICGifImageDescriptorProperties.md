---
layout: interface
category: ENUMERATIONS
title: WICGifImageDescriptorProperties
---

Specifies the image descriptor metadata properties for Graphics Interchange Format (**GIF**) frames.

```cpp
typedef enum WICGifImageDescriptorProperties {
  WICGifImageDescriptorLeft,
  WICGifImageDescriptorTop,
  WICGifImageDescriptorWidth,
  WICGifImageDescriptorHeight,
  WICGifImageDescriptorLocalColorTableFlag,
  WICGifImageDescriptorInterlaceFlag,
  WICGifImageDescriptorSortFlag,
  WICGifImageDescriptorLocalColorTableSize,
  WICGifImageDescriptorProperties_FORCE_DWORD
};
```

## WICGifImageDescriptorLeft

Indicates the X offset at which to locate this frame within the logical screen.

## WICGifImageDescriptorTop

Indicates the Y offset at which to locate this frame within the logical screen.

## WICGifImageDescriptorWidth

Indicates width of this frame, in pixels.

## WICGifImageDescriptorHeight

Indicates height of this frame, in pixels.

## WICGifImageDescriptorLocalColorTableFlag

Indicates the local color table flag.
**TRUE** if global color table is present; otherwise, **FALSE**.

## WICGifImageDescriptorInterlaceFlag

Indicates the interlace flag.
**TRUE** if image is interlaced; otherwise, **FALSE**.

## WICGifImageDescriptorSortFlag

Indicates the sorted color table flag.
**TRUE** if the color table is sorted from most frequently to least frequently used color; otherwise, **FALSE**.

## WICGifImageDescriptorLocalColorTableSize

Indicates the value used to calculate the number of bytes contained in the global color table.

To calculate the actual size of the color table, raise 2 to the value of the field + 1.
