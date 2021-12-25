---
layout: interface
category: ENUMERATIONS
title: WICDdsDimension
---

Specifies the dimension type of the data contained in DDS image.

```cpp
typedef enum WICDdsDimension {
  WICDdsTexture1D,
  WICDdsTexture2D,
  WICDdsTexture3D,
  WICDdsTextureCube,
  WICDDSTEXTURE_FORCE_DWORD
} ;
```

## WICDdsTexture1D

DDS image contains a 1-dimensional texture.

## WICDdsTexture2D

DDS image contains a 2-dimensional texture.

## WICDdsTexture3D

DDS image contains a 3-dimensional texture.

## WICDdsTextureCube

The DDS image contains a cube texture represented as an array of 6 faces.

## Remarks

Both **WICDdsTexture2d** and **WICDdsTextureCube** correspond to **D3D11_RESOURCE_DIMENSION_TEXTURE2D**.
When using ID3D11Device::CreateTexture2D, they are distinguished by the flag **D3D11_RESOURCE_MISC_TEXTURECUBE** in the structure **D3D11_TEXTURE2D_DESC**.
