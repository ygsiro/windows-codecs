---
layout: interface
category: Interface
title: IWICDdsDecoder
TOC:
  - name: Inheritance
---

Provides information and functionality specific to the DDS image format.

## Inheritance

The IWICDdsDecoder interface inherits from the IUnknown interface. IWICDdsDecoder also has these types of members:

## Remarks

This interface is implemented by the WIC DDS codec. To obtain this interface, create an IWICBitmapDecoder using the DDS codec and QueryInterface for IWICDdsDecoder.

## GetFrame

Retrieves the specified frame of the DDS image.

```cpp
HRESULT GetFrame(
   UINT                  arrayIndex, // [in]
   UINT                  mipLevel, // [in]
   UINT                  sliceIndex, // [in]
   IWICBitmapFrameDecode **ppIBitmapFrame // [out]
);
```

### GetFrame - Parameter

1. *arrayIndex* - The requested index within the texture array.
2. *mipLevel* - The requested mip level.
3. *sliceIndex* - The requested slice within the 3D texture.
4. *ppIBitmapFrame* - A pointer to a IWICBitmapFrameDecode object.

### GetFrame - Return value

If this method succeeds, it returns **S_OK**. Otherwise, it returns an **HRESULT** error code.

### GetFrame - Remarks

A DDS file can contain multiple images that are organized into a three level hierarchy. First, DDS file may contain multiple textures in a texture array. Second, each texture can have multiple mip levels. Finally, the texture may be a 3D (volume) texture and have multiple slices, each of which is a 2D texture. See the DDS documentation for more information.

WIC maps this three level hierarchy into a linear array of IWICBitmapFrameDecode, accessible via IWICBitmapDecoder::GetFrame. However, determining which frame corresponds to a triad of arrayIndex, mipLevel, and sliceIndex value is not trivial because each mip level of a 3D texture has a different depth (number of slices). This method provides additional convenience over IWICBitmapDecoder::GetFrame for DDS images by calculating the correct frame given the three indices.

## GetParameters

Gets DDS-specific data.

```cpp
HRESULT GetParameters(
   WICDdsParameters *pParameters // [out]
);
```

### GetParameters - Parameter

1. *pParameters* - A pointer to the structure where the information is returned.

### GetParameters - Return value

If this method succeeds, it returns **S_OK**. Otherwise, it returns an **HRESULT** error code.
