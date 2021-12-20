---
layout: interface
category: Interface
title: IWICBitmapSource
code:
  - key: IWICPalette
  - key: WICPixelFormatGUID
  - key: WICRect
TOC:
  - name: Inheritance
  - name: Remarks
  - name: CopyPalette
  - name: CopyPixels
  - name: GetPixelFormat
  - name: GetResolution
  - name: GetSize
---

Exposes methods that refers to a source from which pixels are retrieved, but cannot be written back to.

## Inheritance

The **IWICBitmapSource** interface inherits from the IUnknown interface.
**IWICBitmapSource** also has these types of members:

- [CopyPalette](#copypalette)
- [CopyPixels](#copypixels)
- [GetPixelFormat](#getpixelformat)
- [GetResolution](#getresolution)
- [GetSize](#getsize)

## Remarks

This interface provides a common way of accessing and linking together bitmaps, decoders, format converters, and scalers.
Components that implement this interface can be connected together in a graph to pull imaging data through.

This interface defines only the notion of readability or being able to produce pixels.
Modifying or writing to a bitmap is considered to be a specialization specific to bitmaps which have storage and is defined in the descendant interface [IWICBitmap][b].

## CopyPalette

Retrieves the color table for indexed pixel formats.

```cpp
HRESULT CopyPalette(
  IWICPalette *pIPalette // [in]
);
```

### CopyPalette - Parameters

1. _pIPalette_ - An [IWICPalette][wp]. A palette can be created using the **CreatePalette** method.

### CopyPalette - Return value

Returns one of the following values.

| Return code                         | Description                          |
| :---------------------------------- | :----------------------------------- |
| **WINCODEC_ERR_PALETTEUNAVAILABLE** | The palette was unavailable.         |
| **S_OK**                            | The palette was successfully copied. |

### CopyPalette - Remarks

If the **IWICBitmapSource** is an [IWICBitmapFrameDecode][wbfd], the function may return the image's global palette if a frame-level palette is not available.
The global palette may also be retrieved using the **CopyPalette** method.

## CopyPixels

Instructs the object to produce pixels.

```cpp
HRESULT CopyPixels(
  const WICRect *prc,         // [in]
  UINT          cbStride,     // [in]
  UINT          cbBufferSize, // [in]
  BYTE          *pbBuffer     // [out]
);
```

### CopyPixels - Parameters

1. _prc_ - The rectangle to copy. A **NULL** value specifies the entire bitmap.
2. _cbStride_ - The stride of the bitmap
3. _cbBufferSize_ - The size of the buffer.
4. _pbBuffer_ - A pointer to the buffer.

### CopyPixels - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### CopyPixels - Remarks

**CopyPixels** is one of the two main image processing routines (the other being Lock) triggering the actual processing.
It instructs the object to produce pixels according to its algorithm - this may involve decoding a portion of a **JPEG** stored on disk, copying a block of memory, or even analytically computing a complex gradient.
The algorithm is completely dependent on the object implementing the interface.

The caller can restrict the operation to a rectangle of interest (**ROI**) using the _prc_ parameter.
The **ROI** sub-rectangle must be fully contained in the bounds of the bitmap.
Specifying a **NULL** **ROI** implies that the whole bitmap should be returned.

The caller controls the memory management and must provide an output buffer (_pbBuffer_) for the results of the copy along with the buffer's bounds (_cbBufferSize_). The _cbStride_ parameter defines the count of bytes between two vertically adjacent pixels in the output buffer.
The caller must ensure that there is sufficient buffer to complete the call based on the width, height and pixel format of the bitmap and the sub-rectangle provided to the copy method.

If the caller needs to perform numerous copies of an expensive **IWICBitmapSource** such as a JPEG, it is recommended to create an in-memory [IWICBitmap][b] first.

### CopyPixels - Codec Developer Remarks

The callee must only write to the first `(prc->Width*bitsperpixel+7)/8` bytes of each line of the output buffer (in this case, a line is a consecutive string of _cbStride_ bytes).

## GetPixelFormat

Retrieves the pixel format of the bitmap source.

```cpp
HRESULT GetPixelFormat(
  WICPixelFormatGUID *pPixelFormat // [out]
);
```

### GetPixelFormat - Parameters

1. *pPixelFormat* - Receives the pixel format **GUID** the bitmap is stored in.
   For a list of available pixel formats, see the Native Pixel Formats topic.

### GetPixelFormat - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### GetPixelFormat - Remarks

The pixel format returned by this method is not necessarily the pixel format the image is stored as.
The codec may perform a format conversion from the storage pixel format to an output pixel format.

## GetResolution

Retrieves the sampling rate between pixels and physical world measurements.

```cpp
HRESULT GetResolution(
  double *pDpiX, // [out]
  double *pDpiY  // [out]
);
```

### GetResolution - Parameters

1. *pDpiX* - A pointer that receives the x-axis dpi resolution.
2. *pDpiY* - A pointer that receives the y-axis dpi resolution.

### GetResolution - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### GetResolution - Remarks

Some formats, such as **GIF** and **ICO**, do not have full DPI support.
For **GIF**, this method calculates the DPI values from the aspect ratio, using a base DPI of (96.0, 96.0).
The **ICO** format does not support DPI at all, and the method always returns (96.0,96.0) for **ICO** images.

Additionally, WIC itself does not transform images based on the DPI values in an image.
It is up to the caller to transform an image based on the resolution returned.

## GetSize

Retrieves the pixel width and height of the bitmap.

```cpp
HRESULT GetSize(
  UINT *puiWidth, // [out]
  UINT *puiHeight // [out]
);
```

### GetSize - Parameters

1. *puiWidth* - A pointer that receives the pixel width of the bitmap.
2. *puiHeight* - A pointer that receives the pixel height of the bitmap

### GetSize - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

[b]: IWICBitmap
[wp]: IWICPalette
[wbfd]: IWICBitmapFrameDecode
