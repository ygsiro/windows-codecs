---
layout: interface
category: Interface
title: IWICBitmapFrameEncode
TOC:
  - name: Inheritance
  - name: Commit
  - name: GetMetadataQueryWriter
  - name: Initialize
  - name: SetColorContexts
  - name: SetPalette
  - name: SetPixelFormat
  - name: SetResolution
  - name: SetSize
  - name: SetThumbnail
  - name: WritePixels
  - name: WriteSource
  - name: Related
code:
  - key: IWICMetadataQueryWriter
  - key: IWICColorContext
  - key: IWICPalette
  - key: IWICBitmapSource
---

Represents an encoder's individual image frames.

## Inheritance

The **IWICBitmapFrameEncode** interface inherits from the IUnknown interface.
**IWICBitmapFrameEncode** also has these types of members:

- [Commit](#commit)
- [GetMetadataQueryWriter](#getmetadataquerywriter)
- [Initialize](#initialize)
- [SetColorContexts](#setcolorcontexts)
- [SetPalette](#setpalette)
- [SetPixelFormat](#setpixelformat)
- [SetResolution](#setresolution)
- [SetSize](#setsize)
- [SetThumbnail](#setthumbnail)
- [WritePixels](#writepixels)
- [WriteSource](#writesource)

## Commit

Commits the frame to the image.

```cpp
HRESULT Commit();
```

### Commit - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### Commit - Remarks

After the frame Commit has been called, you can't use or reinitialize the **IWICBitmapFrameEncode** object and any objects created from it.

To finalize the image, both the frame Commit and the encoder Commit must be called.
However, only call the encoder Commit method after all frames have been committed.

## GetMetadataQueryWriter

Gets the metadata query writer for the encoder frame.

```cpp
HRESULT GetMetadataQueryWriter(
   IWICMetadataQueryWriter **ppIMetadataQueryWriter // [out]
);
```

### GetMetadataQueryWriter - Parameter

1. _ppIMetadataQueryWriter_ - When this method returns, contains a pointer to metadata query writer for the encoder frame.

### GetMetadataQueryWriter - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### GetMetadataQueryWriter - Remarks

If you are setting metadata on the frame, you must do this before you use **IWICBitmapFrameEncode**::[WritePixels](#writepixels) or **IWICBitmapFrameEncode**::[WriteSource](#writesource) to write any image pixels to the frame

## Initialize

Initializes the frame encoder using the given properties.

```cpp
HRESULT Initialize(
   IPropertyBag2 *pIEncoderOptions // [in]
);
```

### Initialize - Parameter

1. _pIEncoderOptions_ - The set of properties to use for **IWICBitmapFrameEncode** initialization.

### Initialize - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### Initialize - Remarks

If you don't want any encoding options, pass **NULL** for _pIEncoderOptions_.
Otherwise, pass the IPropertyBag2 that was provided by [IWICBitmapEncoder][wbe]::[CreateNewFrame][wbe-cnf] with updated values.

[wbe]: IWICBitmapEncoder
[wbe-cnf]: IWICBitmapEncoder#createnewframe

For a complete list of encoding options supported by the Windows-provided codecs, see Native WIC Codecs.

## SetColorContexts

Sets a given number [IWICColorContext][wcc] profiles to the frame.

[wcc]: IWICColorContext

```cpp
HRESULT SetColorContexts(
   UINT             cCount,           // [in]
   IWICColorContext **ppIColorContext // [in]
);
```

### SetColorContexts - Parameter

1. _cCount_ - The number of [IWICColorContext][wcc] profiles to set.
2. _ppIColorContext_ - A pointer to an [IWICColorContext][wcc] pointer containing the color contexts profiles to set to the frame.

### SetColorContexts - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### SetColorContexts - Remarks

- **BMP** Setting color contexts is unsupported.
  This function will return **WINCODEC_ERR_UNSUPPORTEDOPERATION**.
- **PNG** Setting at most one color context is supported, and additional color contexts will be ignored.
  This context must be a [WICColorContextProfile][wccp], and is used to encode the iCCP, gAMA, and cHRM chunks in the PNG file.
- **JPEG**, **TIFF**, **JPEG-XR** Setting up to one [WICColorContextProfile][wccp] and one [WICColorContextExifColorSpace][wccp] is supported. Users must not provide more than one of each type of color context, as all but the last context of each type will be ignored. In JPEG, the [WICColorContextProfile][wccp] is encoded to **JPEG** APP2 ICC metadata block.

In TIFF and **JPEG-XR**, the [WICColorContextProfile][wccp] is encoded to the IFD ICC profile metadata block (IFD tag 0x8773).
In all three formats, the [WICColorContextExifColorSpace][wccp] is encoded to EXIF colorspace metadata block (EXIF tag 0xA001).

[wccp]: WICColorContextType

## SetPalette

Sets the [IWICPalette][wp] for indexed pixel formats.

[wp]: IWICPalette

```cpp
HRESULT SetPalette(
   IWICPalette *pIPalette // [in]
);
```

### SetPalette - Parameter

1. _pIPalette_ - The [IWICPalette][wp] to use for indexed pixel formats.
   The encoder may change the palette to reflect the pixel formats the encoder supports.

### SetPalette - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### SetPalette - Remarks

This method doesn't fail if called on a frame whose pixel format is set to a non-indexed pixel format.
If the target pixel format is a non-indexed format, the palette will be ignored.

If you already called [IWICBitmapEncoder][wbe]::[SetPalette][wbe-sp] to set a global palette, this method overrides that palette for the current frame.

[wbe-sp]: IWICBitmapEncoder#setpalette

The palette must be specified before your first call to [WritePixels](#writepixels)/[WriteSource](#writesource).
Doing so will cause [WriteSource](#writesource) to use the specified palette when converting the source image to the encoder pixel format. If no palette is specified, a palette will be generated on the first call to [WriteSource](#writesource).

## SetPixelFormat

Requests that the encoder use the specified pixel format.

```cpp
HRESULT SetPixelFormat(
   WICPixelFormatGUID *pPixelFormat // [in, out]
);
```

### SetPixelFormat - Parameter

1. _pPixelFormat_ - On input, the requested pixel format GUID.
   On output, the closest pixel format GUID supported by the encoder;
   this may be different than the requested format.
   For a list of pixel format GUIDs, see Native Pixel Formats.

### SetPixelFormat - Return value

Possible return values include the following.

| Return code                 | Description                                                                     |
| :-------------------------- | :------------------------------------------------------------------------------ |
| **S_OK**                    | Success.                                                                        |
| **WINCODEC_ERR_WRONGSTATE** | The **IWICBitmapFrameEncode**::[Initialize](#initialize) method was not called. |

### SetPixelFormat - Remarks

The encoder might not support the requested pixel format.
If not, **SetPixelFormat** returns the closest match in the memory block that _pPixelFormat_ points to.
If the returned pixel format doesn't match the requested format, you must use an [IWICFormatConverter][wfc] object to convert the pixel data.

[wfc]: IWICFormatConverter

## SetResolution

Sets the physical resolution of the output image.

```cpp
HRESULT SetResolution(
   double dpiX, // [in]
   double dpiY  // [in]
);
```

### SetResolution - Parameter

1. _dpiX_ - The horizontal resolution value.
2. _dpiY_ - The vertical resolution value.

### SetResolution - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### SetResolution - Remarks

Windows Imaging Component (**WIC**) doesn't perform any special processing as a result of DPI resolution values.
For example, data returned from [IWICBitmapSource][wbs]::[CopyPixels][wbs-cp] isn't scaled by the DPI.
The app must handle DPI resolution.

[wbs]: IWICBitmapSource
[wbs]: IWICBitmapSource#copypixels

## SetSize

Sets the output image dimensions for the frame.

```cpp
HRESULT SetSize(
   UINT uiWidth, // [in]
   UINT uiHeight // [in]
);
```

### SetSize - Parameter

1. _uiWidth_ - The width of the output image.
2. _uiHeight_ - The height of the output image.

### SetSize - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## SetThumbnail

Sets the frame thumbnail if supported by the codec.

```cpp
HRESULT SetThumbnail(
   IWICBitmapSource *pIThumbnail // [in]
);
```

### SetThumbnail - Parameter

1. _pIThumbnail_ - The bitmap source to use as the thumbnail.

### SetThumbnail - Return value

Returns **S_OK** if successful, or an error value otherwise.

Returns **WINCODEC_ERR_UNSUPPORTEDOPERATION** if the feature is not supported by the encoder.

### SetThumbnail - Remarks

We recommend that you call **SetThumbnail** before calling [WritePixels](#writepixels) or [WriteSource](#writesource).
The thumbnail won't be added to the encoded file if **SetThumbnail** is called after a call to [WritePixels](#writepixels) or [WriteSource](#writesource).

- **BMP**, **PNG** Setting thumbnails is unsupported.
  This function will return **WINCODEC_ERR_UNSUPPORTEDOPERATION**.
- **JPEG** Setting the thumbnail is supported.
  The source image will be re-encoded as either an 8bpp or 24bpp **JPEG** and will be written to the **JPEG’s** APP1 metadata block.
- **TIFF** Setting the thumbnail is supported.
  The source image will be re-encoded as a **TIFF** and will be written to the frame’s SubIFD block.
- **JPEG-XR** Setting the thumbnail is supported.
  The source image will be re-encoded as an additional 8bpp or 24bpp frame.

## WritePixels

Copies scan-line data from a caller-supplied buffer to the [IWICBitmapFrameEncode][wbfe] object.

[wbfe]: IWICBitmapFrameEncode

```cpp
HRESULT WritePixels(
   UINT lineCount,    // [in]
   UINT cbStride,     // [in]
   UINT cbBufferSize, // [in]
   BYTE *pbPixels     // [in]
);
```

### WritePixels - Parameter

1. _lineCount_ - The number of lines to encode.
2. _cbStride_ - The stride of the image pixels.
3. _cbBufferSize_ - The size of the pixel buffer.
4. _pbPixels_ - A pointer to the pixel buffer.

### WritePixels - Return value

Possible return values include the following.

| Return code                            | Description                                                                    |
| :------------------------------------- | :----------------------------------------------------------------------------- |
| **S_OK**                               | Success.                                                                       |
| **WINCODEC_ERR_CODECTOOMANYSCANLINES** | The value of _lineCount_ is larger than the number of scan lines in the image. |

### WritePixels - Remarks

Successive **WritePixels** calls are assumed to be sequential scan-line access in the output image.

## WriteSource

Encodes a bitmap source.

```cpp
HRESULT WriteSource(
   IWICBitmapSource *pIBitmapSource, // [in]
   WICRect          *prc             // [in]
);
```

### WriteSource - Parameter

1. _pIBitmapSource_ - The bitmap source to encode.
2. _prc_ - The size rectangle of the bitmap source.

### WriteSource - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### WriteSource - Remarks

If SetSize is not called prior to calling **WriteSource**, the size given in prc is used if not NULL.
Otherwise, the size of the [IWICBitmapSource][wbs] given in _pIBitmapSource_ is used.

If SetPixelFormat is not called prior to calling **WriteSource**, the pixel format of the [IWICBitmapSource][wbs] given in _pIBitmapSource_ is used.

If SetResolution is not called prior to calling **WriteSource**, the pixel format of _pIBitmapSource_ is used.

If SetPalette is not called prior to calling **WriteSource**, the target pixel format is indexed, and the pixel format of _pIBitmapSource_ matches the encoder frame's pixel format, then the _pIBitmapSource_ pixel format is used.

When encoding a GIF image, if the global palette is set and the frame level palette is not set directly by the user or by a custom independent software vendor (**ISV**) GIF codec, **WriteSource** will use the global palette to encode the frame even when _pIBitmapSource_ has a frame level palette.

Starting with Windows Vista, repeated WriteSource calls can be made as long as the total accumulated source rect height is the same as set through [SetSize](#setsize).

Starting with Windows 8.1, the source rect must be at least the dimensions set through [SetSize](#setsize).
If the source rect width exceeds the [SetSize](#setsize) width, extra pixels on the right side are ignored. If the source rect height exceeds the remaining unfilled height, extra scan lines on the bottom are ignored.

## Related

- [IWICDdsEncoder::CreateNewFrame](IWICDdsEncoder#createnewframe)
