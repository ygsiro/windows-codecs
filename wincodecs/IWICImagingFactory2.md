---
layout: interface
category: Interface
title: IWICImagingFactory2
TOC:
  - name: Inheritance
---

An extension of the WIC factory interface that includes the ability to create an IWICImageEncoder.

## Inheritance

The IWICImagingFactory2 interface inherits from IWICImagingFactory. IWICImagingFactory2 also has these types of members:

## CreateImageEncoder

```cpp
HRESULT CreateImageEncoder(
     ID2D1Device      *pD2DDevice, // [in]
    IWICImageEncoder **ppWICImageEncoder // [out]
);
```

### CreateImageEncoder - Parameter

1. *pD2DDevice* - The ID2D1Device object on which the corresponding image encoder is created.
2. *ppWICImageEncoder* - A pointer to a variable that receives a pointer to the IWICImageEncoder interface for the encoder object that you can use to encode Direct2D images.

### CreateImageEncoder - Return value

If this method succeeds, it returns **S_OK**. Otherwise, it returns an **HRESULT** error code.

### CreateImageEncoder - Remarks

You must create images to pass to the image encoder on the same Direct2D device that you pass to this method.

You are responsible for setting up the bitmap encoder itself through the existing IWICBitmapEncoder APIs. The IWICBitmapEncoder or the IWICBitmapFrameEncode object is passed to each of the IWICImageEncoder methods: WriteThumbnail, WriteFrame, and WriteFrameThumbnail.
