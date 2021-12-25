---
layout: interface
category: Interface
title: IWICBitmapLock
code:
  - key: WICRect
  - key: IWICBitmapLock
  - key: IWICPalette
TOC:
  - name: Inheritance
  - name: Remarks
  - name: GetDataPointer
  - name: GetPixelFormat
  - name: GetSize
  - name: GetStride
---

Exposes methods that support the Lock method.

## Inheritance

The **IWICBitmapLock** interface inherits from the IUnknown interface.
**IWICBitmapLock** also has these types of members:

- [GetDataPointer](#getdatapointer)
- [GetPixelFormat](#getpixelformat)
- [GetSize](#getsize)
- [GetStride](#getstride)

## Remarks

The bitmap lock is simply an abstraction for a rectangular memory window into the bitmap.
For the simplest case, a system memory bitmap, this is simply a pointer to the top left corner of the rectangle and a stride value.

To release the exclusive lock set by Lock method and the associated **IWICBitmapLock** object, call IUnknown::Release on the **IWICBitmapLock** object.

## GetDataPointer

```cpp
HRESULT GetDataPointer(
  UINT             *pcbBufferSize, // [out]
  WICInProcPointer *ppbData        // [out]
);
```

### GetDataPointer - Parameters

1. _pcbBufferSize_ - A pointer that receives the size of the buffer.
2. _ppbData_ - A pointer that receives a pointer to the top left pixel in the locked rectangle.

### GetDataPointer - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### GetDataPointer - Remarks

The pointer provided by this method should not be used outside of the lifetime of the lock itself.

**GetDataPointer** is not available in multi-threaded apartment applications.

## GetPixelFormat

Gets the pixel format of for the locked area of pixels.
This can be used to compute the number of bytes-per-pixel in the locked area.

```cpp
HRESULT GetPixelFormat(
  WICPixelFormatGUID *pPixelFormat // [out]
);
```

### GetPixelFormat - Parameters

1. _pPixelFormat_ - A pointer that receives the pixel format GUID of the locked area.

### GetPixelFormat - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## GetSize

```cpp
HRESULT GetSize(
  UINT *puiWidth, // [in, out]
  UINT *puiHeight // [in, out]
);
```

### GetSize - Parameters

1. _puiWidth_ - A pointer that receives the width of the locked rectangle.
2. _puiHeight_ - A pointer that receives the height of the locked rectangle.

### GetSize - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## GetStride

```cpp
HRESULT GetStride(
  UINT *pcbStride // [in, out]
);
```

### GetStride - Parameters

1. _pcbStride_ - stride

### GetStride - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### GetStride - Remarks

Note the stride value is specific to the **IWICBitmapLock**, not the bitmap.
For example, two consecutive locks on the same rectangle of a bitmap may return different pointers and stride values, depending on internal implementation.
