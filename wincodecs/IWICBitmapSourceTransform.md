---
layout: interface
category: Interface
title: IWICBitmapSourceTransform
TOC:
  - name: Inheritance
  - name: Remarks
  - name: CopyPixels
  - name: DoesSupportTransform
  - name: GetClosestPixelFormat
  - name: GetClosestSize
code:
  - key: WICPixelFormatGUID
  - key: WICBitmapTransformOptions
---

Exposes methods for offloading certain operations to the underlying [IWICBitmapSource][wbs] implementation.

[wbs]: IWICBitmapSource

## Inheritance

The **IWICBitmapSourceTransform** interface inherits from the IUnknown interface. **IWICBitmapSourceTransform** also has these types of members:

## Remarks

[wfc]: IWICFormatConverter
[wbsc]: IWICBitmapScaler
[wbfr]: IWICBitmapFlipRotator

The **IWICBitmapSourceTransform** interface is implemented by codecs which can natively scale, flip, rotate, or format convert pixels during decoding. As the transformation is combined with the decoding process, native transformation will generally offer performance advantages over non-native transformations.
The inbox [IWICBitmapScaler][wbsc], [IWICBitmapFlipRotator][wbfr], and [IWICFormatConverter][wfc] implementations all make use of the **IWICBitmapSourceTransform** interface when they are placed immediately after a supported [IWICBitmapFrameDecode][wbfd], so in the typical case an application will automatically receive this performance increase and does not need to directly use this interface.
However, when chaining multiple transformations, or when implementing a custom transformation, there may be a performance advantage to using the **IWICBitmapSourceTransform** interface directly.

## CopyPixels

Copies pixel data using the supplied input parameters.

```cpp
HRESULT CopyPixels(
    const WICRect             *prc,            // [in]
    UINT                      uiWidth,         // [in]
    UINT                      uiHeight,        // [in]
    WICPixelFormatGUID        *pguidDstFormat, // [in]
    WICBitmapTransformOptions dstTransform,    // [in]
    UINT                      nStride,         // [in]
    UINT                      cbBufferSize,    // [in]
    BYTE                      *pbBuffer        // [out]
);
```

### CopyPixels - Parameter

[gcs]: #getclosestsize
[gcpf]: #getclosestpixelformat
[dst]: #doessupporttransform

1. _prc_ - The rectangle of pixels to copy.
2. _uiWidth_ - The width to scale the source bitmap.
   This parameter must equal the value obtainable through **IWICBitmapSourceTransform**::[GetClosestSize][gcs].
3. _uiHeight_ - The height to scale the source bitmap.
   This parameter must equal the value obtainable through **IWICBitmapSourceTransform**::[GetClosestSize][gcs].
4. _pguidDstFormat_ - The GUID of desired pixel format in which the pixels should be returned.
   This GUID must be a format obtained through an [GetClosestPixelFormat][gcpf] call.
5. _dstTransform_ - The desired rotation or flip to perform prior to the pixel copy.
   The transform must be an operation supported by an [DoesSupportTransform][dst] call.
   If a dstTransform is specified, nStride is the transformed stride and is based on the pguidDstFormat pixel format, not the original source's pixel format.
6. _nStride_ - The stride of the destination buffer.
7. _cbBufferSize_ - The size of the destination buffer.
8. _pbBuffer_ - The output buffer.

### CopyPixels - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### CopyPixels - Codec Developer Remarks

If NULL is passed in for prc, the entire image is copied.
For codec developer implementation details for this method, see Implementing **IWICBitmapSourceTransform**.

When multiple transform operations are requested, the result is dependent on the order in which the operations are performed.
To ensure predictability and consistency across CODECs, it's important that all CODECs perform these operations in the same order. The recommended order of these operations is:

1. Scale
2. Crop
3. Flip/Rotate

Pixel format conversion can be performed at any time, since it has no effect on the other transforms.

The first parameter, prc is used to specify the region of interest for clipping the image.
By convention, scaling is performed before clipping so, if the image is to be scaled as well as clipped, the region of interest should be determined after the image has been scaled.

If a dstTransform is specified, the stride is the transformed stride, and is based on the pixelFormat specified in the CopyPixels call, not the original frame's pixel format.

## DoesSupportTransform

Determines whether a specific transform option is supported natively by the implementation of the **IWICBitmapSourceTransform** interface.

```cpp
HRESULT DoesSupportTransform(
    WICBitmapTransformOptions dstTransform, // [in]
   BOOL                      *pfIsSupported // [out]
);
```

### DoesSupportTransform - Parameter

[wbtfo]: WICBitmapTransformOptions

1. _dstTransform_ - The [WICBitmapTransformOptions][wbtfo] to check if they are supported.
2. _pfIsSupported_ - A pointer that receives a value specifying whether the transform option is supported.

### DoesSupportTransform - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### DoesSupportTransform - Remarks

The Windows provided codecs provide the following level of support:

- **BMP**, **ICO**, **GIF**, **TIFF**: No implementation of **IWICBitmapSourceTransform**.
- **JPEG**, **PNG**: Trivial support ([WICBitmapTransformRotate0][wbtfo] only).
- **JPEG-XR**: Support for all transformation/rotations.

## GetClosestPixelFormat

Retrieves the closest pixel format to which the implementation of **IWICBitmapSourceTransform** can natively copy pixels, given a desired format.

```cpp
HRESULT GetClosestPixelFormat(
   WICPixelFormatGUID *pguidDstFormat // [in, out]
);
```

### GetClosestPixelFormat - Parameter

1. _pguidDstFormat_ - A pointer that receives the GUID of the pixel format that is the closest supported pixel format of the desired format.

### GetClosestPixelFormat - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### GetClosestPixelFormat - Remarks

The Windows provided codecs provide the following support:

- **BMP**, **ICO**, **GIF**, **TIFF**: No implementation of **IWICBitmapSourceTransform**.
- **JPEG**, **PNG**, **JPEG-XR**: Trivial support (always returns the same value as [IWICBitmapFrameDecode][wbfd]::[GetPixelFormat][wbfd-gpf]).

[wbfd]: IWICBitmapFrameDecode
[wbfd-gpf]: IWICBitmapFrameDecode#getpixelformat

## GetClosestSize

Returns the closest dimensions the implementation can natively scale to given the desired dimensions.

```cpp
HRESULT GetClosestSize(
   UINT *puiWidth, // [in, out]
   UINT *puiHeight // [in, out]
);
```

### GetClosestSize - Parameter

1. _puiWidth_ - The desired width. A pointer that receives the closest supported width.
2. _puiHeight_ - The desired height. A pointer that receives the closest supported height.

### GetClosestSize - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### GetClosestSize - Remarks

The Windows provided codecs provide the following support for native scaling:

- **BMP**, **ICO**, **GIF**, **TIFF**: No implementation of **IWICBitmapSourceTransform**.
- **PNG**: No scaling support.
- **JPEG**: Native down-scaling by a factor of 8, 4, or 2.
- **JPEG-XR**: Native scaling of the original image by powers of 2.
