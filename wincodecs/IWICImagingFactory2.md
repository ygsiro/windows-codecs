---
layout: interface
category: Interface
title: IWICImagingFactory2
TOC:
  - name: Inheritance
  - name: CreateImageEncoder
code:
  - key: IWICImageEncoder
---

[wie]: IWICImageEncoder

An extension of the WIC factory interface that includes the ability to create an [IWICImageEncoder][wie].

## Inheritance

[wif]: IWICImagingFactory

The **IWICImagingFactory2** interface inherits from [IWICImagingFactory][wif].
**IWICImagingFactory2** also has these types of members:

- [CreateImageEncoder](#createimageencoder)

## CreateImageEncoder

```cpp
HRESULT CreateImageEncoder(
    ID2D1Device      *pD2DDevice,        // [in]
    IWICImageEncoder **ppWICImageEncoder // [out]
);
```

### CreateImageEncoder - Parameter

1. *pD2DDevice* - The ID2D1Device object on which the corresponding image encoder is created.
2. *ppWICImageEncoder* - A pointer to a variable that receives a pointer to the [IWICImageEncoder][wie] interface for the encoder object that you can use to encode Direct2D images.

### CreateImageEncoder - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### CreateImageEncoder - Remarks

You must create images to pass to the image encoder on the same Direct2D device that you pass to this method.

[wbe]: IWICBitmapEncoder
[wbfe]: IWICBitmapFrameEncode
[wt]: IWICImageEncoder#writethumbnail
[wft]: IWICImageEncoder#writeframethumbnail

You are responsible for setting up the bitmap encoder itself through the existing [IWICBitmapEncoder][wbe] APIs.
The [IWICBitmapEncoder][wbe] or the [IWICBitmapFrameEncode][wbfe] object is passed to each of the [IWICImageEncoder][wie] methods: [WriteThumbnail][wt], WriteFrame, and [WriteFrameThumbnail][wft].
