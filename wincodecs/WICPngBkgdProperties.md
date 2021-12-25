---
layout: interface
category: ENUMERATIONS
title: WICPngBkgdProperties
---

Specifies the Portable Network Graphics (**PNG**) background (**bKGD**) chunk metadata properties.

```cpp
typedef enum WICPngBkgdProperties {
  WICPngBkgdBackgroundColor,
  WICPngBkgdProperties_FORCE_DWORD
} ;
```

## WICPngBkgdBackgroundColor

Indicates the background color.
There are three possible types, depending on the image's pixel format.

Specifies the background color in an RGB image as three USHORT values: {0xRRRR, 0xGGGG, 0xBBBB}.

Specifies the index of the background color in an image with an indexed pixel format.

Specifies the background color in a grayscale image.
