---
layout: interface
category: Interface
title: IWICBitmapDecoder
code:
  - key: IWICPalette
  - key: IWICBitmapDecoderInfo
  - key: IWICBitmapFrameDecode
  - key: IWICMetadataQueryReader
  - key: IWICBitmapSource
  - key: WICDecodeOptions
  - key: IWICColorContext
TOC:
  - name: Inheritance
  - name: Remarks
  - name: GetColorContexts
  - name: GetContainerFormat
  - name: GetDecoderInfo
  - name: GetFrame
  - name: GetFrameCount
  - name: GetMetadataQueryReader
  - name: GetPreview
  - name: GetThumbnail
  - name: Initialize
  - name: QueryCapability
---

Exposes methods that represent a decoder.

## Inheritance

The **IWICBitmapDecoder** interface inherits from the IUnknown interface.
**IWICBitmapDecoder** also has these types of members:

- [GetColorContexts](#getcolorcontexts)
- [GetContainerFormat](#getcontainerformat)
- [GetDecoderInfo](#getdecoderinfo)
- [GetFrame](#getframe)
- [GetFrameCount](#getframecount)
- [GetMetadataQueryReader](#getmetadataqueryreader)
- [GetPreview](#getpreview)
- [GetThumbnail](#getthumbnail)
- [Initialize](#initialize)
- [QueryCapability](#querycapability)

## Remarks

There are a number of concrete implementations of this interface representing each of the standard decoders provided by the platform including bitmap (**BMP**), Portable Network Graphics (**PNG**), icon (**ICO**), Joint Photographic Experts Group (**JPEG**), Graphics Interchange Format (**GIF**), Tagged Image File Format (**TIFF**), and Microsoft Windows Digital Photo (**WDP**).
The following table includes the class identifier (**CLSID**) for each native decoder.

| CLSID Name               | CLSID                                                                      |
| :----------------------- | :------------------------------------------------------------------------- |
| **CLSID_WICBmpDecoder**  | 0x6b462062, 0x7cbf, 0x400d, 0x9f, 0xdb, 0x81, 0x3d, 0xd1, 0x0f, 0x27, 0x78 |
| **CLSID_WICGifDecoder**  | 0x381dda3c, 0x9ce9, 0x4834, 0xa2, 0x3e, 0x1f, 0x98, 0xf8, 0xfc, 0x52, 0xbe |
| **CLSID_WICHeifDecoder** | 0xe9a4a80a, 0x44fe, 0x4de4, 0x89, 0x71, 0x71, 0x50, 0xb1, 0x0a, 0x51, 0x99 |
| **CLSID_WICIcoDecoder**  | 0xc61bfcdf, 0x2e0f, 0x4aad, 0xa8, 0xd7, 0xe0, 0x6b, 0xaf, 0xeb, 0xcd, 0xfe |
| **CLSID_WICJpegDecoder** | 0x9456a480, 0xe88b, 0x43ea, 0x9e, 0x73, 0x0b, 0x2d, 0x9b, 0x71, 0xb1, 0xca |
| **CLSID_WICPngDecoder**  | 0x389ea17b, 0x5078, 0x4cde, 0xb6, 0xef, 0x25, 0xc1, 0x51, 0x75, 0xc7, 0x51 |
| **CLSID_WICTiffDecoder** | 0xb54e85d9, 0xfe23, 0x499f, 0x8b, 0x88, 0x6a, 0xce, 0xa7, 0x13, 0x75, 0x2b |
| **CLSID_WICWebpDecoder** | 0x7693e886, 0x51c9, 0x4070, 0x84, 0x19, 0x9f, 0x70, 0X73, 0X8e, 0Xc8, 0Xfa |
| **CLSID_WICWmpDecoder**  | 0xa26cec36, 0x234c, 0x4950, 0xae, 0x16, 0xe3, 0x4a, 0xac, 0xe7, 0x1d, 0x0d |

This interface may be sub-classed to provide support for third party codecs as part of the extensibility model.

<!--See the AITCodec Sample CODEC.-->

Codecs written as **TIFF** container formats that are not register will decode as a **TIFF** image.
Client applications should check for a zero frame count to determine if the codec is valid.

**CLSID_WICHeifDecoder** operates on **HEIF** (High Efficiency Image Format) images.

## CopyPalette

Copies the decoder's [IWICPalette][wp].

```cpp
HRESULT CopyPalette(
  IWICPalette *pIPalette // [in]
);
```

### CopyPalette - Parameters

1. _pIPalette_ - An [IWICPalette][wp] to which the decoder's global palette is to be copied.
   Use CreatePalette to create the destination palette before calling **CopyPalette**.

### CopyPalette - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### CopyPalette - Remarks

**CopyPalette** returns a global palette (a palette that applies to all the frames in the image) if there is one;
otherwise, it returns **WINCODEC_ERR_PALETTEUNAVAILABLE**.
If an image doesn't have a global palette, it may still have a frame-level palette, which can be retrieved using [IWICBitmapFrameDecode][wbfd]::[CopyPalette][wbfd-cp].

## GetColorContexts

Retrieves the [IWICColorContext][wcc] objects of the image.

```cpp
HRESULT GetColorContexts(
  UINT             cCount,             // [in]
  IWICColorContext **ppIColorContexts, // [in, out]
  UINT             *pcActualCount      // [out]
);
```

### GetColorContexts - Parameters

1. _cCount_ - The number of color contexts to retrieve.
   This value must be the size of, or smaller than, the size available to _ppIColorContexts_.
2. _ppIColorContexts_ - A pointer that receives a pointer to the [IWICColorContext][wcc].
3. _pcActualCount_ - A pointer that receives the number of color contexts contained in the image.

### GetColorContexts - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## GetContainerFormat

Retrieves the image's container format.

```cpp
HRESULT GetContainerFormat(
  GUID *pguidContainerFormat // [out]
);
```

### GetContainerFormat - Parameters

1. _pguidContainerFormat_ - A pointer that receives the image's container format GUID.

### GetContainerFormat - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## GetDecoderInfo

Retrieves an [IWICBitmapDecoderInfo][wbdi] for the image.

```cpp
HRESULT GetDecoderInfo(
  IWICBitmapDecoderInfo **ppIDecoderInfo // [out]
);
```

### GetDecoderInfo - Parameters

1. _ppIDecoderInfo_ - A pointer that receives a pointer to an [IWICBitmapDecoderInfo][wbdi].

### GetDecoderInfo - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## GetFrame

Retrieves the specified frame of the image.

```cpp
HRESULT GetFrame(
  UINT                  index,           // [in]
  IWICBitmapFrameDecode **ppIBitmapFrame // [out]
);
```

### GetFrame - Parameters

1. _index_ - The particular frame to retrieve.
2. _ppIBitmapFrame_ - A pointer that receives a pointer to the [IWICBitmapFrameDecode][wbfd].

### GetFrame - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## GetFrameCount

Retrieves the total number of frames in the image.

```cpp
HRESULT GetFrameCount(
  UINT *pCount // [out]
);
```

### GetFrameCount - Parameters

1. _pCount_ - A pointer that receives the total number of frames in the image.

### GetFrameCount - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## GetMetadataQueryReader

Retrieves the metadata query reader from the decoder.

```cpp
HRESULT GetMetadataQueryReader(
  IWICMetadataQueryReader **ppIMetadataQueryReader // [out]
);
```

### GetMetadataQueryReader - Parameters

1. _ppIMetadataQueryReader_ - Receives a pointer to the decoder's [IWICMetadataQueryReader][wmqr].

### GetMetadataQueryReader - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### GetMetadataQueryReader - Remarks

If an image format does not support container-level metadata, this will return **WINCODEC_ERR_UNSUPPORTEDOPERATION**.
The only Windows provided image format that supports container-level metadata is **GIF**.
Instead, use [IWICBitmapFrameDecode][wbfd]::[GetMetadataQueryReader][gmqr].

## GetPreview

Retrieves a preview image, if supported.

```cpp
HRESULT GetPreview(
  IWICBitmapSource **ppIBitmapSource // [out]
);
```

### GetPreview - Parameters

1. _ppIBitmapSource_ - Receives a pointer to the preview bitmap if supported.

### GetPreview - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### GetPreview - Remarks

Not all formats support previews.
Only the native Microsoft Windows Digital Photo (**WDP**) codec support previews.

## GetThumbnail

Retrieves a bitmap thumbnail of the image, if one exists

```cpp
HRESULT GetThumbnail(
  IWICBitmapSource **ppIThumbnail // [out]
);
```

### GetThumbnail - Parameters

1. _ppIThumbnail_ - Receives a pointer to the [IWICBitmapSource][wbs] of the thumbnail.

### GetThumbnail - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### GetThumbnail - Remarks

The returned thumbnail can be of any size, so the caller should scale the thumbnail to the desired size.
The only Windows provided image formats that support thumbnails are **JPEG**, **TIFF**, and **JPEG-XR**.
If the thumbnail is not available, this will return **WINCODEC_ERR_CODECNOTHUMBNAIL**.

## Initialize

Initializes the decoder with the provided stream.

```cpp
HRESULT Initialize(
  IStream          *pIStream,   // [in]
  WICDecodeOptions cacheOptions // [in]
);
```

### Initialize - Parameters

1. _pIStream_ - The stream to use for initialization.
   The stream contains the encoded pixels which are decoded each time the CopyPixels method on the [IWICBitmapFrameDecode][wbfd] interface (see GetFrame) is invoked.
2. _chachOptions_ - The [WICDecodeOptions][wdo] to use for initialization.

### Initialize - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## QueryCapability

Retrieves the capabilities of the decoder based on the specified stream.

```cpp
HRESULT QueryCapability(
  IStream *pIStream,     // [in]
  DWORD   *pdwCapability // [out]
);
```

### QueryCapability - Parameters

1. _pIStream_ - The stream to retrieve the decoder capabilities from.
2. _pdwCapability_ - The [WICBitmapDecoderCapabilities][wbdc] of the decoder.

### QueryCapability - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### QueryCapability - Remarks

Custom decoder implementations should save the current position of the specified **IStream**, read whatever information is necessary in order to determine which capabilities it can provide for the supplied stream, and restore the stream position.

[wp]: IWICPalette
[wcc]: IWICColorContext
[wbdi]: IWICBitmapDecoderInfo
[wbfd]: IWICBitmapFrameDecode
[wbfd-cp]: IWICBitmapSource#copypalette
[wmqr]: IWICMetadataQueryReader
[wbs]: IWICBitmapSource
[wdo]: WICDecodeOptions
[wbdc]: WICBitmapDecoderCapabilities
[gmqr]: IWICBitmapFrameDecode#getmetadataqueryreader
