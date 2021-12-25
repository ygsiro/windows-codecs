---
layout: interface
category: STRUCTURES
title: WICDdsParameters
code:
  - key: WICDdsDimension
  - key: WICDdsAlphaMode
---

Specifies the DDS image dimension, **DXGI_FORMAT** and alpha mode of contained data.

```cpp
typedef struct WICDdsParameters {
  UINT            Width;
  UINT            Height;
  UINT            Depth;
  UINT            MipLevels;
  UINT            ArraySize;
  DXGI_FORMAT     DxgiFormat;
  WICDdsDimension Dimension;
  WICDdsAlphaMode AlphaMode;
} WICDdsParameters;
```

## Members

### Width

The width, in pixels, of the texture at the largest mip size (mip level 0).

### Height

The height, in pixels, of the texture at the largest mip size (mip level 0).
When the DDS image contains a 1-dimensional texture, this value is equal to 1.

### Depth

The number of slices in the 3D texture.
This is equivalent to the depth, in pixels, of the 3D texture at the largest mip size (mip level 0).
When the DDS image contains a 1- or 2-dimensional texture, this value is equal to 1.

### MipLevels

The number of mip levels contained in the DDS image.

### ArraySize

The number of textures in the array in the DDS image.

### DxgiFormat

The **DXGI_FORMAT** of the DDS pixel data.

### Dimension

Specifies the dimension type of the data contained in DDS image (1D, 2D, 3D or cube texture).

### AlphaMode

Specifies the alpha behavior of the DDS image.
