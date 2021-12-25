---
layout: interface
category: Interface
title: IWICDdsFrameDecode
TOC:
  - name: Inheritance
---

Provides access to a single frame of DDS image data in its native DXGI_FORMAT form, as well as information about the image data.

## Inheritance

The IWICDdsFrameDecode interface inherits from the IUnknown interface. IWICDdsFrameDecode also has these types of members:

## Remarks

This interface is implemented by the WIC DDS codec. To obtain this interface, create an IWICBitmapFrameDecode using the DDS codec and QueryInterface for IID_IWICDdsFrameDecode.

## CopyBlocks

Requests pixel data as it is natively stored within the DDS file.

```cpp
HRESULT CopyBlocks(
   const WICRect *prcBoundsInBlocks, // [in]
   UINT          cbStride, // [in]
   UINT          cbBufferSize, // [in]
   BYTE          *pbBuffer // [out]
);
```

### CopyBlocks - Parameter

1. *prcBoundsInBlocks* - The rectangle to copy from the source. A NULL value specifies the entire texture.
   If the texture uses a block-compressed DXGI_FORMAT, all values of the rectangle are expressed in number of blocks, not pixels.
2. *cbStride* - The stride, in bytes, of the destination buffer. This represents the number of bytes from the buffer pointer to the next row of data. If the texture uses a block-compressed DXGI_FORMAT, a "row of data" is defined as a row of blocks which contains multiple pixel scanlines.
3. *cbBufferSize* - The size, in bytes, of the destination buffer.
4. *pbBuffer* - A pointer to the destination buffer.

### CopyBlocks - Return value

If this method succeeds, it returns **S_OK**. Otherwise, it returns an **HRESULT** error code.

### CopyBlocks - Remarks

If the texture does not use a block-compressed DXGI_FORMAT, this method behaves similarly to IWICBitmapSource::CopyPixels. However, it does not perform any pixel format conversion, and instead produces the raw data from the DDS file.

If the texture uses a block-compressed DXGI_FORMAT, this method copies the block data directly into the provided buffer. In this case, the prcBoundsInBlocks parameter is defined in blocks, not pixels. To determine if this is the case, call GetFormatInfo and read the DxgiFormat member of the returned WICDdsFormatInfo structure.

## GetFormatInfo

Gets information about the format in which the DDS image is stored.

```cpp
HRESULT GetFormatInfo(
   WICDdsFormatInfo *pFormatInfo // [out]
);
```

### GetFormatInfo - Parameter

1. *pFormatInfo* - Information about the DDS format.

### GetFormatInfo - Return value

If this method succeeds, it returns **S_OK**. Otherwise, it returns an **HRESULT** error code.

## GetSizeInBlocks

Gets the width and height, in blocks, of the DDS image.

```cpp
HRESULT GetSizeInBlocks(
   UINT *pWidthInBlocks, // [out]
   UINT *pHeightInBlocks // [out]
);
```

### GetSizeInBlocks - Parameter

1. *pWidthInBlocks* - The width of the DDS image in blocks.
2. *pHeightInBlocks* - The height of the DDS image in blocks.

### GetSizeInBlocks - Return value

If this method succeeds, it returns **S_OK**. Otherwise, it returns an **HRESULT** error code.

### GetSizeInBlocks - Remarks

For block compressed textures, the returned width and height values do not completely define the texture size because the image is padded to fit the closest whole block size. For example, three BC1 textures with pixel dimensions of 1x1, 2x2 and 4x4 will all report pWidthInBlocks = 1 and pHeightInBlocks = 1.

If the texture does not use a block-compressed DXGI_FORMAT, this method returns the texture size in pixels; for these formats the block size returned by IWICDdsFrameDecoder::GetFormatInfo is 1x1.
