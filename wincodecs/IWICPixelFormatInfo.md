---
layout: interface
category: Interface
title: IWICPixelFormatInfo
TOC:
  - name: Inheritance
  - name: GetBitsPerPixel
  - name: GetChannelCount
  - name: GetChannelMask
  - name: GetColorContext
  - name: GetFormatGUID
code:
  - key: IWICColorContext
---

Exposes methods that provide information about a pixel format.

## Inheritance

[wci]: IWICComponentInfo

The **IWICPixelFormatInfo** interface inherits from [IWICComponentInfo][wci].
**IWICPixelFormatInfo** also has these types of members:

- [GetBitsPerPixel](#getbitsperpixel)
- [GetChannelCount](#getchannelcount)
- [GetChannelMask](#getchannelmask)
- [GetColorContext](#getcolorcontext)
- [GetFormatGUID](#getformatguid)

## GetBitsPerPixel

Gets the bits per pixel (**BPP**) of the pixel format.

```cpp
HRESULT GetBitsPerPixel(
    UINT *puiBitsPerPixel // [out]
);
```

### GetBitsPerPixel - Parameter

1. *puiBitsPerPixel* - Pointer that receives the BPP of the pixel format.

### GetBitsPerPixel - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## GetChannelCount

Gets the number of channels the pixel format contains.

```cpp
HRESULT GetChannelCount(
    UINT *puiChannelCount // [out]
);
```

### GetChannelCount - Parameter

1. *puiChannelCount* - Pointer that receives the channel count.

### GetChannelCount - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## GetChannelMask

Gets the pixel format's channel mask.

```cpp
HRESULT GetChannelMask(
    UINT uiChannelIndex, // [in]
    UINT cbMaskBuffer,   // [in]
    BYTE *pbMaskBuffer,  // [in, out]
    UINT *pcbActual      // [out]
);
```

### GetChannelMask - Parameter

1. *uiChannelIndex* - The index to the channel mask to retrieve.
2. *cbMaskBuffer* - The size of the pbMaskBuffer buffer.
3. *pbMaskBuffer* - Pointer to the mask buffer.
4. *pcbActual* - The actual buffer size needed to obtain the channel mask.

### GetChannelMask - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### GetChannelMask - Remarks

If 0 and **NULL** are passed in for *cbMaskBuffer* and *pbMaskBuffer*, respectively, the required buffer size will be returned through *pcbActual*.

## GetColorContext

Gets the pixel format's [IWICColorContext][wcc].

[wcc]: IWICColorContext

```cpp
HRESULT GetColorContext(
    IWICColorContext **ppIColorContext // [out]
);
```

### GetColorContext - Parameter

1. *ppIColorContext* - Pointer that receives the pixel format's color context.

### GetColorContext - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### GetColorContext - Remarks

[wbs]: IWICBitmapSource

The returned color context is the default color space for the pixel format.
However, if an [IWICBitmapSource][wbs] specifies its own color context, the source's context should be preferred over the pixel format's default.

## GetFormatGUID

Gets the pixel format GUID.

```cpp
HRESULT GetFormatGUID(
    GUID *pFormat // [out]
);
```

### GetFormatGUID - Parameter

1. *pFormat* - Pointer that receives the pixel format GUID.

### GetFormatGUID - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.
