---
layout: interface
category: STRUCTURES
title: WICBitmapPlane
---

Specifies the pixel format, buffer, stride and size of a component plane for a planar pixel format.

```cpp
typedef struct WICBitmapPlane {
  WICPixelFormatGUID Format;
  BYTE               *pbBuffer;
  UINT               cbStride;
  UINT               cbBufferSize;
} WICBitmapPlane;
```

## Members

### Format

Describes the pixel format of the plane.

### pbBuffer

Pointer to the buffer that holds the plane’s pixel components.

### cbStride

The stride of the buffer pointed to by *pbData*.
Stride indicates the total number of bytes to go from the beginning of one scanline to the beginning of the next scanline.

### cbBufferSize

The total size of the buffer pointed to by *pbBuffer*.
