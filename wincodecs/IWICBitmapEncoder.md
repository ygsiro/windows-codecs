---
layout: interface
category: Interface
title: IWICBitmapEncoder
code:
  - key: IWICBitmapEncoderInfo
  - key: IWICBitmapFrameEncode
  - key: IWICBitmapSource
  - key: IWICColorContext
  - key: IWICMetadataQueryWriter
  - key: IWICPalette
  - key: WICBitmapEncoderCacheOption
TOC:
  - name: Inheritance
  - name: Remarks
  - name: Commit
  - name: CreateNewFrame
  - name: GetContainerFormat
  - name: GetEncoderInfo
  - name: GetMetadataQueryWriter
  - name: Initialize
  - name: SetColorContexts
  - name: SetPalette
  - name: SetPreview
  - name: SetThumbnail
---

Defines methods for setting an encoder's properties such as thumbnails, frames, and palettes.

## Inheritance

The **IWICBitmapEncoder** interface inherits from the IUnknown interface.
**IWICBitmapEncoder** also has these types of members:

- [Commit](#commit)
- [CreateNewFrame](#createnewframe)
- [GetContainerFormat](#getcontainerformat)
- [GetEncoderInfo](#getencoderinfo)
- [GetMetadataQueryWriter](#getmetadataquerywriter)
- [Initialize](#initialize)
- [SetColorContexts](#setcolorcontexts)
- [SetPalette](#setpalette)
- [SetPreview](#setpreview)
- [SetThumbnail](#setthumbnail)

## Remarks

There are a number of concrete implementations of this interface representing each of the standard encoders provided by the platform including bitmap (**BMP**), Portable Network Graphics (**PNG**), Joint Photographic Experts Group (**JPEG**), Graphics Interchange Format (**GIF**), Tagged Image File Format (**TIFF**), and Microsoft Windows Digital Photo (**WDP**).
The following table includes the class identifier (**CLSID**) for each native encoder.

| CLSID Name               | CLSID                                                                      |
| :----------------------- | :------------------------------------------------------------------------- |
| **CLSID_WICBmpEncoder**  | 0x69be8bb4, 0xd66d, 0x47c8, 0x86, 0x5a, 0xed, 0x15, 0x89, 0x43, 0x37, 0x82 |
| **CLSID_WICGifEncoder**  | 0x114f5598, 0xb22, 0x40a0, 0x86, 0xa1, 0xc8, 0x3e, 0xa4, 0x95, 0xad, 0xbd  |
| **CLSID_WICHeifEncoder** | 0x0dbecec1, 0x9eb3, 0x4860, 0x9c, 0x6f, 0xdd, 0xbe, 0x86, 0x63, 0x45, 0x75 |
| **CLSID_WICJpegEncoder** | 0x1a34f5c1, 0x4a5a, 0x46dc, 0xb6, 0x44, 0x1f, 0x45, 0x67, 0xe7, 0xa6, 0x76 |
| **CLSID_WICPngEncoder**  | 0x27949969, 0x876a, 0x41d7, 0x94, 0x47, 0x56, 0x8f, 0x6a, 0x35, 0xa4, 0xdc |
| **CLSID_WICTiffEncoder** | 0x0131be10, 0x2001, 0x4c5f, 0xa9, 0xb0, 0xcc, 0x88, 0xfa, 0xb6, 0x4c, 0xe8 |
| **CLSID_WICWmpEncoder**  | 0xac4ce3cb, 0xe1c1, 0x44cd, 0x82, 0x15, 0x5a, 0x16, 0x65, 0x50, 0x9e, 0xc2 |

Additionally this interface may be sub-classed to provide support for third party codecs as part of the extensibility model.

<!-- See the AITCodec Sample CODEC. -->

**CLSID_WICHeifDecoder** operates on **HEIF** (High Efficiency Image Format) images.

## Commit

Commits all changes for the image and closes the stream.

```cpp
HRESULT Commit();
```

### Commit - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### Commit - Remarks

To finalize an image, both the frame Commit and the encoder Commit must be called.
However, only call the encoder Commit method after all frames have been committed.

After the encoder has been committed, it can't be re-initialized or reused with another stream.
A new encoder interface must be created, for example, with [IWICImagingFactory][wif]::[CreateEncoder][wif-c].

For the encoder Commit to succeed, you must at a minimum call **IWICBitmapEncoder**::[Initialize](#initialize) and either [IWICBitmapFrameEncode][wbfe]::[WriteSource][wbfe-ws] or [IWICBitmapFrameEncode][wbfe]::[WritePixels][wbfe-wp].

[IWICBitmapFrameEncode][wbfe]::[WriteSource][wbfe-ws] specifies all parameters needed to encode the image data.
[IWICBitmapFrameEncode][wbfe]::[WritePixels][wbfe-wp] requires that you also call [IWICBitmapFrameEncode][wbfe]::[SetSize][wbfe-ss], [IWICBitmapFrameEncode][wbfe]::[SetPixelFormat][wbfe-spf], and [IWICBitmapFrameEncode][wbfe]::[SetPalette][wbfe-sp] (if the pixel format is indexed).

## CreateNewFrame

Creates a new [IWICBitmapFrameEncode][wbfe] instance.

```cpp
HRESULT CreateNewFrame(
  IWICBitmapFrameEncode **ppIFrameEncode,   // [out]
  IPropertyBag2         **ppIEncoderOptions // [in, out]
);
```

### CreateNewFrame - Parameters

1. _ppIFrameEncode_ - A pointer that receives a pointer to the new instance of an [IWICBitmapFrameEncode][wbfe].
2. _ppIEncoderOptions_ - Optional. Receives the named properties to use for subsequent frame initialization. See Remarks.

### CreateNewFrame - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### CreateNewFrame - Remarks

The parameter _ppIEncoderOptions_ can be used to receive an IPropertyBag2 that can then be used to specify encoder options.
This is done by passing a pointer to a **NULL** IPropertyBag2 pointer in _ppIEncoderOptions_.
The returned IPropertyBag2 is initialized with all encoder options that are available for the given format, at their default values.
To specify non-default encoding behavior, set the needed encoder options on the IPropertyBag2 and pass it to [IWICBitmapFrameEncode][wbfe]::[Initialize][wbfe-i].

**Note:** Do not pass in a pointer to an initialized IPropertyBag2.
The pointer will be overwritten, and the original IPropertyBag2 will not be freed.

Otherwise, you can pass **NULL** in _ppIEncoderOptions_ if you do not intend to specify encoder options.
See Encoding Overview for an example of how to set encoder options.

For formats that support encoding multiple frames (for example, **TIFF**, **JPEG-XR**), you can work on only one frame at a time.
This means that you must call [IWICBitmapFrameEncode][wbfe]::[Commit][wbfe-c] before you call **CreateNewFrame** again.

## GetContainerFormat

Retrieves the encoder's container format.

```cpp
HRESULT GetContainerFormat(
  GUID *pguidContainerFormat // [out]
);
```

### GetContainerFormat - Parameters

1. _pguidContainerFormat_ - A pointer that receives the encoder's container format GUID.

### GetContainerFormat - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## GetEncoderInfo

Retrieves an [IWICBitmapEncoderInfo](wbei) for the encoder.

```cpp
HRESULT GetEncoderInfo(
  IWICBitmapEncoderInfo **ppIEncoderInfo // [out]
);
```

### GetEncoderInfo - Parameters

1. _ppIEncoderInfo_ - A pointer that receives a pointer to an [IWICBitmapEncoderInfo][wbei].

### GetEncoderInfo - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## GetMetadataQueryWriter

Retrieves a metadata query writer for the encoder.

```cpp
HRESULT GetMetadataQueryWriter(
  IWICMetadataQueryWriter **ppIMetadataQueryWriter // [out]
);
```

### GetMetadataQueryWriter - Parameters

1. _ppIMetadataQueryWriter_ - When this method returns, contains a pointer to the encoder's metadata query writer.

### GetMetadataQueryWriter - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## Initialize

Initializes the encoder with an IStream which tells the encoder where to encode the bits.

```cpp
HRESULT Initialize(
  IStream                     *pIStream,  // [in]
  WICBitmapEncoderCacheOption cacheOption // [in]
);
```

### Initialize - Parameters

1. _pIStream_ - The output stream.
2. _cacheOption_ - The [WICBitmapEncoderCacheOption][wbeco] used on initialization.

### Initialize - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## SetColorContexts

Sets the [IWICColorContext][wcc] objects for the encoder.

```cpp
HRESULT SetColorContexts(
  UINT             cCount,           // [in]
  IWICColorContext **ppIColorContext // [in]
);
```

### SetColorContexts - Parameters

1. _cCount_ - The number of [IWICColorContext][wcc] to set.
2. _ppIColorContext_ - A pointer an [IWICColorContext][wcc] pointer containing the color contexts to set for the encoder.

### SetColorContexts - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### SetColorContexts - Remarks

## SetPalette

Sets the global palette for the image.

```cpp
HRESULT SetPalette(
  IWICPalette *pIPalette // [in]
);
```

### SetPalette - Parameters

1. _pIPalette_ - The [IWICPalette][wp] to use as the global palette.

### SetPalette - Return value

Returns **S_OK** if successful, or an error value otherwise.

Returns **WINCODEC_ERR_UNSUPPORTEDOPERATION** if the feature is not supported by the encoder.

### SetPalette - Remarks

Only **GIF** images support an optional global palette, and you must set the global palette before adding any frames to the image.
You only need to set the palette for indexed pixel formats.

## SetPreview

Sets the global preview for the image.

```cpp
HRESULT SetPreview(
  IWICBitmapSource *pIPreview // [in]
);
```

### SetPreview - Parameters

1. _pIPreview_ - The [IWICBitmapSource][wbs] to use as the global preview.

### SetPreview - Return value

Returns **S_OK** if successful, or an error value otherwise.

Returns **WINCODEC_ERR_UNSUPPORTEDOPERATION** if the feature is not supported by the encoder.

## SetThumbnail

Sets the global thumbnail for the image.

```cpp
HRESULT SetThumbnail(
  IWICBitmapSource *pIThumbnail // [in]
);
```

### SetThumbnail - Parameters

1. _pIThumbnail_ - The [IWICBitmapSource][wbs] to set as the global thumbnail.

### SetThumbnail - Return value

Returns **S_OK** if successful, or an error value otherwise.

Returns **WINCODEC_ERR_UNSUPPORTEDOPERATION** if the feature is not supported by the encoder.

[wbeco]: WICBitmapEncoderCacheOption
[wbei]: IWICBitmapEncoderInfo
[wbfe-c]: IWICBitmapFrameEncode#commit
[wbfe-i]: IWICBitmapFrameEncode#initialize
[wbfe-sp]: IWICBitmapFrameEncode#setpalette
[wbfe-spf]: IWICBitmapFrameEncode#setpixelformat
[wbfe-ss]: IWICBitmapFrameEncode#setsize
[wbfe-ss]: IWICBitmapFrameEncode#setsize
[wbfe-wp]: IWICBitmapFrameEncode#writepixels
[wbfe-ws]: IWICBitmapFrameEncode#writesource
[wbfe]: IWICBitmapFrameEncode
[wbs]: IWICBitmapSource
[wcc]: IWICColorContext
[wif-c]: IWICImagingFactory#createencoder
[wif]: IWICImagingFactory
[wp]: IWICPalette
