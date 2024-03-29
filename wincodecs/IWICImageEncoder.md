---
layout: interface
category: Interface
title: IWICImageEncoder
TOC:
  - name: Inheritance
  - name: WriteFrame
  - name: WriteFrameThumbnail
  - name: WriteThumbnail
  - name: Related
code:
  - key: IWICBitmapFrameEncode
  - key: WICImageParameters
---

[wbe]: IWICBitmapEncoder

Encodes ID2D1Image interfaces to an [IWICBitmapEncoder][wbe].

## Inheritance

The **IWICImageEncoder** interface inherits from the IUnknown interface.
**IWICImageEncoder** also has these types of members:

- [WriteFrame](#writeframe)
- [WriteFrameThumbnail](#writeframethumbnail)
- [WriteThumbnail](#writethumbnail)

## WriteFrame

[wbfe]: IWICBitmapFrameEncode

Encodes the image to the frame given by the [IWICBitmapFrameEncode][wbfe].

```cpp
HRESULT WriteFrame(
    ID2D1Image               *pImage,          // [in]
    IWICBitmapFrameEncode    *pFrameEncode,    // [in]
    const WICImageParameters *pImageParameters // [in]
);
```

### WriteFrame - Parameter

1. *pImage* - The Direct2D image that will be encoded.
2. *pFrameEncode* - The frame encoder to which the image is written.
3. *pImageParameters* - Additional parameters to control encoding.

### WriteFrame - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### WriteFrame - Remarks

[wif2]: IWICImagingFactory2
[wif2-cie]: IWICImagingFactory2#createimageencoder
[wip]: WICImageParameters

The image passed in must be created on the same device as in [IWICImagingFactory2][wif2]::[CreateImageEncoder][wif2-cie]. If the pImageParameters are not specified, a set of useful defaults will be assumed, see [WICImageParameters][wip] for more info.

You must correctly and independently have set up the [IWICBitmapFrameEncode][wbfe] before calling this API.

## WriteFrameThumbnail

Encodes the image as a thumbnail to the frame given by the [IWICBitmapFrameEncode][wbfe].

```cpp
HRESULT WriteFrameThumbnail(
    ID2D1Image               *pImage,          // [in]
    IWICBitmapFrameEncode    *pFrameEncode,    // [in]
    const WICImageParameters *pImageParameters // [in]
);
```

### WriteFrameThumbnail - Parameter

1. *pImage* - The Direct2D image that will be encoded.
2. *pFrameEncode* - The frame encoder on which the thumbnail is set.
3. *pImageParameters* - Additional parameters to control encoding.

### WriteFrameThumbnail - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### WriteFrameThumbnail - Remarks

The image passed in must be created on the same device as in [IWICImagingFactory2][wif2]::[CreateImageEncoder][wif2-cie].
If the *pImageParameters* are not specified, a set of useful defaults will be assumed, see [WICImageParameters][wip] for more info.

You must correctly and independently have set up the [IWICBitmapFrameEncode][wbfe] before calling this API.

## WriteThumbnail

Encodes the given image as the thumbnail to the given WIC bitmap encoder.

```cpp
HRESULT WriteThumbnail(
    ID2D1Image               *pImage,          // [in]
    IWICBitmapEncoder        *pEncoder,        // [in]
    const WICImageParameters *pImageParameters // [in]
);
```

### WriteThumbnail - Parameter

1. *pImage* - The Direct2D image that will be encoded.
2. *pEncoder* - The encoder on which the thumbnail is set.
3. *pImageParameters* - Additional parameters to control encoding.

### WriteThumbnail - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### WriteThumbnail - Remarks

You must create the image that you pass in on the same device as in [IWICImagingFactory2][wif2]::[CreateImageEncoder][wif2-cie].
If you don't specify additional parameters in the variable that *pImageParameters* points to, the encoder uses a set of useful defaults.
For info about these defaults, see [WICImageParameters][wip].

Before you call **WriteThumbnail**, you must set up the [IWICBitmapEncoder][wbe] interface for the encoder on which you want to set the thumbnail.

If **WriteThumbnail** fails, it might return **E_OUTOFMEMORY**, **D2DERR_WRONG_RESOURCE_DOMAIN**, or other error codes from the encoder.

## Related

- [IWICImagingFactory2::CreateImageEncoder](IWICImagingFactory2#createimageencoder)
