---
layout: interface
category: Interface
title: IWICPlanarBitmapFrameEncode
TOC:
  - name: Inheritance
---

Allows planar component image pixels to be written to an encoder. When supported by the encoder, this allows an application to encode planar component image data without first converting to an interleaved pixel format.

You can use

QueryInterface to obtain this interface from the Windows provided implementation of IWICBitmapFrameEncode for the JPEG encoder.

## Inheritance

The IWICPlanarBitmapFrameEncode interface inherits from the IUnknown interface. IWICPlanarBitmapFrameEncode also has these types of members:

## Remarks

Encoding YCbCr data using IWICPlanarBitmapFrameEncode is similar but not identical to encoding interleaved data using IWICBitmapFrameEncode. The planar interface only exposes the ability to write planar frame image data, and you should continue to use the frame encode interface to set metadata or a thumbnail and to commit at the end of the operation.

## WritePixels

Writes lines from the source planes to the encoded format.

```cpp
HRESULT WritePixels(
    UINT           lineCount, // [in]
    WICBitmapPlane *pPlanes, // [in]
    UINT           cPlanes // [in]
);
```

### WritePixels - Parameter

1. _lineCount_ - The number of lines to encode. See the Remarks section for WIC Jpeg specific line count restrictions.
2. _pPlanes_ - Specifies the source buffers for each component plane encoded.
3. _cPlanes_ - The number of component planes specified by the pPlanes parameter.

### WritePixels - Return value

If the planes and source rectangle do not meet the requirements, this method fails with WINCODEC_ERR_IMAGESIZEOUTOFRANGE.

If the IWICBitmapSource format does not meet the encoder requirements, this method fails with WINCODEC_ERR_UNSUPPORTEDPIXELFORMAT.

### WritePixels - Remarks

Successive WritePixels calls are assumed sequentially add scanlines to the output image. IWICBitmapFrameEncode::Initialize, IWICBitmapFrameEncode::SetSize and IWICBitmapFrameEncode::SetPixelFormat must be called before this method or it will fail.

The interleaved pixel format set via IWICBitmapFrameEncode::SetPixelFormat and the codec specific encode parameters determine the supported planar formats.

WIC JPEG Encoder: QueryInterface can be used to obtain this interface from the WIC JPEG IWICBitmapFrameEncode implementation. When using this method to encode Y’CbCr data with the WIC JPEG encoder, chroma subsampling can be configured with encoder options during frame creation. See the Encoding Overview and IWICBitmapEncoder::CreateNewFrame for more details.

Depending upon the configured chroma subsampling, the lineCount parameter has the following restrictions:

| Chroma Subsampling | Line Count Restriction                                               | Chroma Plane Width                               | Chroma Plane Height                                |
| :----------------- | :------------------------------------------------------------------- | :----------------------------------------------- | :------------------------------------------------- |
| 4:2:0              | Multiple of 2, unless the call covers the last scanline of the image | lumaWidth / 2 Rounded up to the nearest integer. | lumaHeight / 2 Rounded up to the nearest integer.  |
| 4:2:2              | Any                                                                  | lumaWidth / 2 Rounded up to the nearest integer. | Any                                                |
| 4:4:4              | Any                                                                  | Any                                              | Any                                                |
| 4:4:0              | Multiple of 2, unless the call covers the last scanline of the image | Any                                              | llumaHeight / 2 Rounded up to the nearest integer. |

The full scanline width must be encoded, and the width of the bitmap sources must match their planar configuration.

Additionally, if a pixel format is set via IWICBitmapFrameEncode::SetPixelFormat, it must be GUID_WICPixelFormat24bppBGR.

The supported pixel formats of the bitmap sources passed into this method are as follows:

| Plane Count | Plane 1                  | Plane 2                      | Plane 3                   |
| :---------- | :----------------------- | :--------------------------- | :------------------------ |
| 3           | GUID_WICPixelFormat8bppY | GUID_WICPixelFormat8bppCb    | GUID_WICPixelFormat8bppCr |
| 2           | GUID_WICPixelFormat8bppY | GUID_WICPixelFormat16bppCbCr | N/A                       |

## WriteSource

Writes lines from the source planes to the encoded format.

```cpp
HRESULT WriteSource(
    IWICBitmapSource **ppPlanes, // [in]
    UINT             cPlanes, // [in]
    WICRect          *prcSource // [in]
);
```

### WriteSource - Parameter

1. _ppPlanes_ - Specifies an array of IWICBitmapSource that represent image planes.
2. _cPlanes_ - The number of component planes specified by the planes parameter.
3. _prcSource_ - The source rectangle of pixels to encode from the IWICBitmapSource planes. Null indicates the entire source. The source rect width must match the width set through SetSize. Repeated WriteSource calls can be made as long as the total accumulated source rect height is the same as set through SetSize.

### WriteSource - Return value

If the planes and source rectangle do not meet the requirements, this method fails with WINCODEC_ERR_IMAGESIZEOUTOFRANGE.

If the IWICBitmapSource format does not meet the encoder requirements, this method fails with WINCODEC_ERR_UNSUPPORTEDPIXELFORMAT.

### WriteSource - Remarks

Successive WriteSource calls are assumed sequentially add scanlines to the output image. IWICBitmapFrameEncode::Initialize, IWICBitmapFrameEncode::SetSize and IWICBitmapFrameEncode::SetPixelFormat must be called before this method or it will fail.

The interleaved pixel format set via IWICBitmapFrameEncode::SetPixelFormat and the codec specific encode parameters determine the supported planar formats.

WIC JPEG Encoder: QueryInterface can be used to obtain this interface from the WIC JPEG IWICBitmapFrameEncode implementation. When using this method to encode Y’CbCr data with the WIC JPEG encoder, chroma subsampling can be configured with encoder options during frame creation. See the Encoding Overview and IWICBitmapEncoder::CreateNewFrame for more details.

Depending upon the configured chroma subsampling, the lineCount parameter has the following restrictions:

| Chroma Subsampling | X Coordinate  | Y Coordinate  | Chroma Width                                     | Chroma Height                                      |
| :----------------- | :------------ | :------------ | :----------------------------------------------- | -------------------------------------------------- |
| 4:2:0              | Multiple of 2 | Multiple of 2 | lumaWidth / 2 Rounded up to the nearest integer. | lumaHeight / 2 Rounded up to the nearest integer.  |
| 4:2:2              | Multiple of 2 | Any           | lumaWidth / 2 Rounded up to the nearest integer. | Any                                                |
| 4:4:4              | Any           | Any           | Any                                              | Any                                                |
| 4:4:0              | Any           | Multiple of 2 | lumaWidth                                        | llumaHeight / 2 Rounded up to the nearest integer. |

The full scanline width must be encoded, and the width of the bitmap sources must match their planar configuration.

Additionally, if a pixel format is set via IWICBitmapFrameEncode::SetPixelFormat, it must be GUID_WICPixelFormat24bppBGR.

The supported pixel formats of the bitmap sources passed into this method are as follows:

| Plane Count | Plane 1                  | Plane 2                      | Plane 3                   |
| :---------- | :----------------------- | :--------------------------- | :------------------------ |
| 3           | GUID_WICPixelFormat8bppY | GUID_WICPixelFormat8bppCb    | GUID_WICPixelFormat8bppCr |
| 2           | GUID_WICPixelFormat8bppY | GUID_WICPixelFormat16bppCbCr | N/A                       |
