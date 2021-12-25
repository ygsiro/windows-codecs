---
layout: interface
category: Interface
title: IWICPlanarBitmapSourceTransform
TOC:
  - name: Inheritance
---

Provides access to planar Y’CbCr pixel formats where pixel components are stored in separate component planes. This interface also allows access to other codec optimizations for flip/rotate, scale, and format conversion to other Y’CbCr planar formats; this is similar to the pre-existing IWICBitmapSourceTransform interface.

QueryInterface can be used to obtain this interface from the Windows provided implementations of IWICBitmapFrameDecode for the JPEG decoder, IWICBitmapScaler, IWICBitmapFlipRotator, and IWICColorTransform.

## Inheritance

The IWICPlanarBitmapSourceTransform interface inherits from the IUnknown interface. IWICPlanarBitmapSourceTransform also has these types of members:

## CopyPixels

Copies pixels into the destination planes. Configured by the supplied input parameters.

If a dstTransform, scale, or format conversion is specified, cbStride is the transformed stride and is based on the destination pixel format of the pDstPlanes parameter, not the original source's pixel format.

```cpp
HRESULT CopyPixels(
    const WICRect             *prcSource, // [in]
    UINT                      uiWidth, // [in]
    UINT                      uiHeight, // [in]
    WICBitmapTransformOptions dstTransform, // [in]
    WICPlanarOptions          dstPlanarOptions, // [in]
    const WICBitmapPlane      *pDstPlanes, // [in]
    UINT                      cPlanes // [in]
);
```

### CopyPixels - Parameter

1. _prcSource_ - The source rectangle of pixels to copy.
2. _uiWidth_ - The width to scale the source bitmap. This parameter must be equal to a value obtainable through IWICPlanarBitmapSourceTransform:: DoesSupportTransform.
3. _uiHeight_ - The height to scale the source bitmap. This parameter must be equal to a value obtainable through IWICPlanarBitmapSourceTransform:: DoesSupportTransform.
4. _dstTransform_ - The desired rotation or flip to perform prior to the pixel copy. A rotate can be combined with a flip horizontal or a flip vertical, see WICBitmapTransformOptions.
5. _dstPlanarOptions_ - Used to specify additional configuration options for the transform. See WICPlanarOptions for more detail.
   WIC JPEG Decoder: WICPlanarOptionsPreserveSubsampling can be specified to retain the subsampling ratios when downscaling. By default, the JPEG decoder attempts to preserve quality by downscaling only the Y plane in some cases, changing the image to 4:4:4 chroma subsampling.
6. _pDstPlanes_ - Specifies the pixel format and output buffer for each component plane. The number of planes and pixel format of each plane must match values obtainable through IWICPlanarBitmapSourceTransform::DoesSupportTransform.
7. _cPlanes_ - The number of component planes specified by the pDstPlanes parameter.

### CopyPixels - Return value

If the specified scale, flip/rotate, and planar format configuration is not supported this method fails with WINCODEC_ERR_INVALIDPARAMETER. You can check if a transform is supported by calling IWICPlanarBitmapSourceTransform::DoesSupportTransform.

### CopyPixels - Remarks

WIC JPEG Decoder: Depending on the configured chroma subsampling of the image, the source rectangle has the following restrictions:

| Chroma Subsampling | X Coordinate  | Y Coordinate  | Chroma Width                                     | Chroma Height                                      |
| :----------------- | :------------ | :------------ | :----------------------------------------------- | -------------------------------------------------- |
| 4:2:0              | Multiple of 2 | Multiple of 2 | lumaWidth / 2 Rounded up to the nearest integer. | lumaHeight / 2 Rounded up to the nearest integer.  |
| 4:2:2              | Multiple of 2 | Any           | lumaWidth / 2 Rounded up to the nearest integer. | lumaHeight                                         |
| 4:4:4              | Any           | Any           | llumaWidth                                       | llumaHeight                                        |
| 4:4:0              | Any           | Multiple of 2 | lumaWidth                                        | llumaHeight / 2 Rounded up to the nearest integer. |

The pDstPlanes parameter supports the following pixel formats.

| Plane Count | Plane 1                  | Plane 2                      | Plane 3                   |
| :---------- | :----------------------- | :--------------------------- | :------------------------ |
| 3           | GUID_WICPixelFormat8bppY | GUID_WICPixelFormat8bppCb    | GUID_WICPixelFormat8bppCr |
| 2           | GUID_WICPixelFormat8bppY | GUID_WICPixelFormat16bppCbCr | N/A                       |

## DoesSupportTransform

Use this method to determine if a desired planar output is supported and allow the caller to choose an optimized code path if it is. Otherwise, callers should fall back to IWICBitmapSourceTransform or IWICBitmapSource and retrieve interleaved pixels.

The following transforms can be checked:

+ Determine if the flip/rotate option specified via WICBitmapTransformOptions is supported.
+ Determine if the requested planar pixel format configuration is supported.
+ Determine the closest dimensions the implementation can natively scale to given the desired dimensions.

When a transform is supported, this method returns the description of the resulting planes in the pPlaneDescriptions parameter.

```cpp
HRESULT DoesSupportTransform(
    UINT                      *puiWidth, // [in, out]
    UINT                      *puiHeight, // [in, out]
    WICBitmapTransformOptions dstTransform, // [in]
    WICPlanarOptions          dstPlanarOptions, // [in]
    const WICPixelFormatGUID  *pguidDstFormats, // [in]
    WICBitmapPlaneDescription *pPlaneDescriptions, // [out]
    UINT                      cPlanes, // [in]
    BOOL                      *pfIsSupported // [out]
);
```

### DoesSupportTransform - Parameter

1. *puiWidth* - On input, the desired width. On output, the closest supported width to the desired width; this is the same size or larger than the desired width.
2. *puiHeight* - On input, the desired height. On output, the closest supported height to the desired height; this is the same size or larger than the desired width.
3. *dstTransform* - The desired rotation or flip operation. Multiple WICBitmapTransformOptions can be combined in this flag parameter, see WICBitmapTransformOptions.
4. *dstPlanarOptions* - Used to specify additional configuration options for the transform. See WICPlanarOptions for more detail.

   WIC JPEG Decoder:

   WICPlanarOptionsPreserveSubsampling can be specified to retain the subsampling ratios when downscaling. By default, the JPEG decoder attempts to preserve quality by downscaling only the Y plane in some cases, changing the image to 4:4:4 chroma subsampling.
5. *pguidDstFormats* - The requested pixel formats of the respective planes.
6. *pPlaneDescriptions* - When *pfIsSupported == TRUE, the array of plane descriptions contains the size and format of each of the planes.

   WIC JPEG Decoder: The Cb and Cr planes can be a different size from the values returned by puiWidth and puiHeight due to chroma subsampling.
7. *cPlanes* - The number of component planes requested.
8. *pfIsSupported* - Set to TRUE if the requested transforms are natively supported.

### DoesSupportTransform - Return value

Check the value of pfIsSupported to determine if the transform is supported via IWICPlanarBitmapSourceTransform::CopyPixels. If this method fails, the output parameters for width, height, and plane descriptions are zero initialized. Other return values indicate failure.
