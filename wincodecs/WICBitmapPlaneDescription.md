---
layout: interface
category: STRUCTURES
title: WICBitmapPlaneDescription
---

Specifies the pixel format and size of a component plane.

```cpp
typedef struct WICBitmapPlaneDescription {
  WICPixelFormatGUID Format;
  UINT               Width;
  UINT               Height;
} WICBitmapPlaneDescription;
```

## Members

### Format

Describes the pixel format of the plane.

### Width

Component width of the plane.

### Height

Component height of the plane.
