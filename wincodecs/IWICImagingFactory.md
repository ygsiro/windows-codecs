---
layout: interface
category: Interface
title: IWICImagingFactory
TOC:
  - name: Inheritance
  - name: CreateBitmap
  - name: CreateBitmapClipper
  - name: CreateBitmapFlipRotator
  - name: CreateBitmapFromHBITMAP
  - name: CreateBitmapFromHICON
  - name: CreateBitmapFromMemory
  - name: CreateBitmapFromSource
  - name: CreateBitmapFromSourceRect
  - name: CreateBitmapScaler
  - name: CreateColorContext
  - name: CreateColorTransformer
  - name: CreateComponentEnumerator
  - name: CreateComponentInfo
  - name: CreateDecoder
  - name: CreateDecoderFromFileHandle
  - name: CreateDecoderFromFilename
  - name: CreateDecoderFromStream
  - name: CreateEncoder
  - name: CreateFastMetadataEncoderFromDecoder
  - name: CreateFastMetadataEncoderFromFrameDecode
  - name: CreateFormatConverter
  - name: CreatePalette
  - name: CreateQueryWriter
  - name: CreateQueryWriterFromReader
  - name: CreateStream
code:
  - key: IWICBitmap
  - key: IWICBitmapClipper
  - key: IWICBitmapDecoder
  - key: IWICBitmapFlipRotator
  - key: IWICBitmapFrameDecode
  - key: IWICBitmapScaler
  - key: IWICBitmapSource
  - key: IWICColorContext
  - key: IWICColorTransform
  - key: IWICComponentInfo
  - key: IWICFastMetadataEncoder
  - key: IWICFastMetadataEncoder
  - key: IWICFormatConverter
  - key: IWICMetadataQueryReader
  - key: IWICMetadataQueryWriter
  - key: IWICStream
  - key: WICBitmapAlphaChannelOption
  - key: WICBitmapCreateCacheOption
  - key: WICDecodeOptions
---

Exposes methods used to create components for the Windows Imaging Component (**WIC**) such as decoders, encoders and pixel format converters.

## Inheritance

The **IWICImagingFactory** interface inherits from the IUnknown interface.
**IWICImagingFactory** also has these types of members:

- [CreateBitmap](#createbitmap)
- [CreateBitmapClipper](#createbitmapclipper)
- [CreateBitmapFlipRotator](#createbitmapfliprotator)
- [CreateBitmapFromHBITMAP](#createbitmapfromhbitmap)
- [CreateBitmapFromHICON](#createbitmapfromhicon)
- [CreateBitmapFromMemory](#createbitmapfrommemory)
- [CreateBitmapFromSource](#createbitmapfromsource)
- [CreateBitmapFromSourceRect](#createbitmapfromsourcerect)
- [CreateBitmapScaler](#createbitmapscaler)
- [CreateColorContext](#createcolorcontext)
- [CreateColorTransformer](#createcolortransformer)
- [CreateComponentEnumerator](#createcomponentenumerator)
- [CreateComponentInfo](#createcomponentinfo)
- [CreateDecoder](#createdecoder)
- [CreateDecoderFromFileHandle](#createdecoderfromfilehandle)
- [CreateDecoderFromFilename](#createdecoderfromfilename)
- [CreateDecoderFromStream](#createdecoderfromstream)
- [CreateEncoder](#createencoder)
- [CreateFastMetadataEncoderFromDecoder](#createfastmetadataencoderfromdecoder)
- [CreateFastMetadataEncoderFromFrameDecode](#createfastmetadataencoderfromframedecode)
- [CreateFormatConverter](#createformatconverter)
- [CreatePalette](#createpalette)
- [CreateQueryWriter](#createquerywriter)
- [CreateQueryWriterFromReader](#createquerywriterfromreader)
- [CreateStream](#createstream)

## CreateBitmap

Creates an [IWICBitmap][wb] object.

```cpp
HRESULT CreateBitmap(
    UINT                       uiWidth, // [in]
    UINT                       uiHeight, // [in]
    REFWICPixelFormatGUID      pixelFormat, // [in]
    WICBitmapCreateCacheOption option, // [in]
    IWICBitmap                 **ppIBitmap // [out]
);
```

### CreateBitmap - Parameter

[wbcco]: WICBitmapCreateCacheOption

1. _uiWidth_ - The width of the new bitmap .
2. _uiHeight_ - The height of the new bitmap.
3. _pixelFormat_ - The pixel format of the new bitmap.
4. _option_ - The cache creation options of the new bitmap. This can be one of the values in the [WICBitmapCreateCacheOption][wbcco] enumeration.

   | Value                  | Meaning                                                               |
   | :--------------------- | :-------------------------------------------------------------------- |
   | **WICBitmapCacheOnDemand** | Allocates system memory for the bitmap at initialization.             |
   | **WICBitmapCacheOnLoad**   | Allocates system memory for the bitmap when the bitmap is first used. |
   | **WICBitmapNoCache**       | This option is not valid for this method and should not be used.      |

5. _ppIBitmap_ - A pointer that receives a pointer to the new bitmap.

### CreateBitmap - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## CreateBitmapClipper

[wbc]: IWICBitmapClipper

Creates a new instance of an [IWICBitmapClipper][wbc] object.

```cpp
HRESULT CreateBitmapClipper(
    IWICBitmapClipper **ppIBitmapClipper // [out]
);
```

### CreateBitmapClipper - Parameter

1. _ppIBitmapClipper_ - A pointer that receives a pointer to a new [IWICBitmapClipper][wbc].

### CreateBitmapClipper - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## CreateBitmapFlipRotator

Creates a new instance of an [IWICBitmapFlipRotator][wbfr] object.

```cpp
HRESULT CreateBitmapFlipRotator(
    IWICBitmapFlipRotator **ppIBitmapFlipRotator // [out]
);
```

### CreateBitmapFlipRotator - Parameter

[wbfr]: IWICBitmapFlipRotator

1. _ppIBitmapFlipRotator_ - A pointer that receives a pointer to a new [IWICBitmapFlipRotator][wbfr].

### CreateBitmapFlipRotator - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## CreateBitmapFromHBITMAP

Creates an [IWICBitmap][wb] from a bitmap handle.

```cpp
HRESULT CreateBitmapFromHBITMAP(
    HBITMAP                     hBitmap, // [in]
    HPALETTE                    hPalette, // [in]
    WICBitmapAlphaChannelOption options, // [in]
    IWICBitmap                  **ppIBitmap // [out]
);
```

### CreateBitmapFromHBITMAP - Parameter

1. _hBitmap_ - A bitmap handle to create the bitmap from.
2. _hPalette_ - A palette handle used to create the bitmap.
3. _options_ - The alpha channel options to create the bitmap.
4. _ppIBitmap_ - A pointer that receives a pointer to the new bitmap.

### CreateBitmapFromHBITMAP - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### CreateBitmapFromHBITMAP - Remarks

For a non-palletized bitmap, set **NULL** for the hPalette parameter.

## CreateBitmapFromHICON

Creates an [IWICBitmap][wb] from an icon handle.

```cpp
HRESULT CreateBitmapFromHICON(
    HICON      hIcon, // [in]
    IWICBitmap **ppIBitmap // [out]
);
```

### CreateBitmapFromHICON - Parameter

1. _hIcon_ - The icon handle to create the new bitmap from.
2. _ppIBitmap_ - A pointer that receives a pointer to the new bitmap.

### CreateBitmapFromHICON - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## CreateBitmapFromMemory

Creates an [IWICBitmap][wb] from a memory block.

```cpp
HRESULT CreateBitmapFromMemory(
    UINT                  uiWidth, // [in]
    UINT                  uiHeight, // [in]
    REFWICPixelFormatGUID pixelFormat, // [in]
    UINT                  cbStride, // [in]
    UINT                  cbBufferSize, // [in]
    BYTE                  *pbBuffer, // [in]
    IWICBitmap            **ppIBitmap // [out]
);
```

### CreateBitmapFromMemory - Parameter

1. _uiWidth_ - The width of the new bitmap.
2. _uiHeight_ - The height of the new bitmap.
3. _pixelFormat_ - The pixel format of the new bitmap. For valid pixel formats, see Native Pixel Formats.
4. _cbStride_ - The number of bytes between successive scanlines in pbBuffer.
5. _cbBufferSize_ - The size of pbBuffer.
6. _pbBuffer_ - The buffer used to create the bitmap.
7. _ppIBitmap_ - A pointer that receives a pointer to the new bitmap.

### CreateBitmapFromMemory - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### CreateBitmapFromMemory - Remarks

The size of the [IWICBitmap][wb] to be created must be smaller than or equal to the size of the image in *pbBuffer*.

The stride of the destination bitmap will equal the stride of the source data, regardless of the width and height specified.

The *pixelFormat* parameter defines the pixel format for both the input data and the output bitmap.

## CreateBitmapFromSource

Creates a [IWICBitmap][wb] from a [IWICBitmapSource][wbso].

```cpp
HRESULT CreateBitmapFromSource(
    IWICBitmapSource           *pIBitmapSource, // [in]
    WICBitmapCreateCacheOption option, // [in]
    IWICBitmap                 **ppIBitmap // [out]
);
```

### CreateBitmapFromSource - Parameter

1. _pIBitmapSource_ - The [IWICBitmapSource][wbso] to create the bitmap from.
2. _option_ - The cache options of the new bitmap. This can be one of the values in the **WICBitmapCreateCacheOption** enumeration.

   | Value                  | Meaning                                                               |
   | :--------------------- | :-------------------------------------------------------------------- |
   | **WICBitmapNoCache**       | Do not create a system memory copy. Share the bitmap with the source. |
   | **WICBitmapCacheOnDemand** | Create a system memory copy when the bitmap is first used.            |
   | **WICBitmapCacheOnLoad**   | Create a system memory copy when this method is called.               |

3. _ppIBitmap_ - A pointer that receives a pointer to the new bitmap.

### CreateBitmapFromSource - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## CreateBitmapFromSourceRect

[wb]: IWICBitmap

Creates an [IWICBitmap][wb] from a specified rectangle of an [IWICBitmapSource][wbso].

```cpp
HRESULT CreateBitmapFromSourceRect(
    IWICBitmapSource *pIBitmapSource, // [in]
    UINT             x, // [in]
    UINT             y, // [in]
    UINT             width, // [in]
    UINT             height, // [in]
    IWICBitmap       **ppIBitmap // [out]
);
```

### CreateBitmapFromSourceRect - Parameter

[wbso]: IWICBitmapSource

1. _pIBitmapSource_ - The [IWICBitmapSource][wbso] to create the bitmap from.
2. _x_ - The horizontal coordinate of the upper-left corner of the rectangle.
3. _y_ - The vertical coordinate of the upper-left corner of the rectangle.
4. _width_ - The width of the rectangle and the new bitmap.
5. _height_ - The height of the rectangle and the new bitmap.
6. _ppIBitmap_ - A pointer that receives a pointer to the new bitmap.

### CreateBitmapFromSourceRect - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### CreateBitmapFromSourceRect - Remarks

Providing a rectangle that is larger than the source will produce undefined results.

This method always creates a separate copy of the source image, similar to the cache option **WICBitmapCacheOnLoad**.

## CreateBitmapScaler

Creates a new instance of an [IWICBitmapScaler][wbs].

```cpp
HRESULT CreateBitmapScaler(
    IWICBitmapScaler **ppIBitmapScaler // [out]
);
```

### CreateBitmapScaler - Parameter

[wbs]: IWICBitmapScaler

1. _ppIBitmapScaler_ - A pointer that receives a pointer to a new [IWICBitmapScaler][wbs].

### CreateBitmapScaler - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## CreateColorContext

[wcc]: IWICColorContext

Creates a new instance of the [IWICColorContext][wcc] class.

```cpp
HRESULT CreateColorContext(
    IWICColorContext **ppIWICColorContext // [out]
);
```

### CreateColorContext - Parameter

1. _ppIWICColorContext_ - A pointer that receives a pointer to a new IWICColorContext.

### CreateColorContext - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## CreateColorTransformer

Creates a new instance of the [IWICColorTransform][wct] class.

```cpp
HRESULT CreateColorTransformer(
    IWICColorTransform **ppIWICColorTransform // [out]
);
```

### CreateColorTransformer - Parameter

[wct]: IWICColorTransform

1. _ppIWICColorTransform_ - A pointer that receives a pointer to a new [IWICColorTransform][wct].

### CreateColorTransformer - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## CreateComponentEnumerator

Creates an IEnumUnknown object of the specified component types.

```cpp
HRESULT CreateComponentEnumerator(
    DWORD        componentTypes,  // [in]
    DWORD        options,         // [in]
    IEnumUnknown **ppIEnumUnknown // [out]
);
```

### CreateComponentEnumerator - Parameter

1. _componentTypes_ - The types of WICComponentType to enumerate.
2. _options_ - The WICComponentEnumerateOptions used to enumerate the given component types.
3. _ppIEnumUnknown_ - A pointer that receives a pointer to a new component enumerator.

### CreateComponentEnumerator - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### CreateComponentEnumerator - Remarks

Component types must be enumerated separately. Combinations of component types and WICAllComponents are unsupported.

## CreateComponentInfo

Creates a new instance of the IWICComponentInfo class for the given component class identifier (CLSID).

```cpp
HRESULT CreateComponentInfo(
    REFCLSID          clsidComponent, // [in]
    IWICComponentInfo **ppIInfo       // [out]
);
```

### CreateComponentInfo - Parameter

[wci]: IWICComponentInfo

1. _clsidComponent_ - The CLSID for the desired component.
2. _ppIInfo_ - A pointer that receives a pointer to a new [IWICComponentInfo][wci].

### CreateComponentInfo - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## CreateDecoder

Creates a new instance of [IWICBitmapDecoder][wbd].

```cpp
HRESULT CreateDecoder(
    REFGUID           guidContainerFormat, // [in]
    const GUID        *pguidVendor, // [in]
    IWICBitmapDecoder **ppIDecoder // [out, retval]
);
```

### CreateDecoder - Parameter

1. _guidContainerFormat_ - The GUID for the desired container format.

   | Value                    | Meaning                             |
   | :----------------------- | :---------------------------------- |
   | **GUID_ContainerFormatBmp**  | The BMP container format GUID.      |
   | **GUID_ContainerFormatPng**  | The PNG container format GUID.      |
   | **GUID_ContainerFormatIco**  | The ICO container format GUID.      |
   | **GUID_ContainerFormatJpeg** | The JPEG container format GUID.     |
   | **GUID_ContainerFormatTiff** | The TIFF container format GUID.     |
   | **GUID_ContainerFormatGif**  | The GIF container format GUID.      |
   | **GUID_ContainerFormatWmp**  | The HD Photo container format GUID. |

2. _pguidVendor_ - The GUID for the preferred encoder vendor.

   | Value                       | Meaning                                     |
   | :-------------------------- | :------------------------------------------ |
   | **NULL**                        | No preferred codec vendor.                  |
   | **GUID_VendorMicrosoft**        | Prefer to use Microsoft encoder.            |
   | **GUID_VendorMicrosoftBuiltIn** | Prefer to use the native Microsoft encoder. |

3. _ppIDecoder_ - A pointer that receives a pointer to a new [IWICBitmapDecoder][wbd].
   You must initialize this [IWICBitmapDecoder][wbd] on a stream using the Initialize method later.

### CreateDecoder - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### CreateDecoder - Remarks

Other values may be available for both guidContainerFormat and pguidVendor depending on the installed WIC-enabled encoders.
The values listed are those that are natively supported by the operating system.

## CreateDecoderFromFileHandle

Creates a new instance of the [IWICBitmapDecoder][wbd] based on the given file handle.

```cpp
HRESULT CreateDecoderFromFileHandle(
    ULONG_PTR         hFile, // [in]
    const GUID        *pguidVendor, // [in]
    WICDecodeOptions  metadataOptions, // [in]
    IWICBitmapDecoder **ppIDecoder // [out, retval]
);
```

### CreateDecoderFromFileHandle - Parameter

[wbd]: IWICBitmapDecoder

1. _hFile_ - The file handle to create the decoder from.
2. _pguidVendor_ - The GUID for the preferred decoder vendor. Use NULL if no preferred vendor.
3. _metadataOptions_ - The [WICDecodeOptions][wdo] to use when creating the decoder.
4. _ppIDecoder_ - A pointer that receives a pointer to a new [IWICBitmapDecoder][wbd].

### CreateDecoderFromFileHandle - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### CreateDecoderFromFileHandle - Remarks

When a decoder is created using this method, the file handle must remain alive during the lifetime of the decoder.

## CreateDecoderFromFilename

Creates a new instance of the [IWICBitmapDecoder][wbd] class based on the given file.

```cpp
HRESULT CreateDecoderFromFilename(
    LPCWSTR           wzFilename, // [in]
    const GUID        *pguidVendor, // [in]
    DWORD             dwDesiredAccess, // [in]
    WICDecodeOptions  metadataOptions, // [in]
    IWICBitmapDecoder **ppIDecoder // [out, retval]
);
```

### CreateDecoderFromFilename - Parameter

1. _wzFilename_ - A pointer to a null-terminated string that specifies the name of an object to create or open.
2. _pguidVendor_ - The GUID for the preferred decoder vendor. Use NULL if no preferred vendor.
3. _dwDesiredAccess_ - The access to the object, which can be read, write, or both.

   | Value         | Meaning       |
   | :------------ | :------------ |
   | GENERIC_READ  | Read access.  |
   | GENERIC_WRITE | Write access. |

   For more information, see Generic Access Rights.

4. _metadataOptions_ - The WICDecodeOptions to use when creating the decoder.
5. _ppIDecoder_ - A pointer that receives a pointer to the new IWICBitmapDecoder.

### CreateDecoderFromFilename - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## CreateDecoderFromStream

Creates a new instance of the IWICBitmapDecoder class based on the given IStream.

```cpp
HRESULT CreateDecoderFromStream(
    IStream           *pIStream, // [in]
    const GUID        *pguidVendor, // [in]
    WICDecodeOptions  metadataOptions, // [in]
    IWICBitmapDecoder **ppIDecoder // [out, retval]
);
```

### CreateDecoderFromStream - Parameter

[wdo]: WICDecodeOptions

1. _pIStream_ - The stream to create the decoder from.
2. _pguidVendor_ - The GUID for the preferred decoder vendor. Use NULL if no preferred vendor.
3. _metadataOptions_ - The [WICDecodeOptions][wdo] to use when creating the decoder.
4. _ppIDecoder_ - A pointer that receives a pointer to a new IWICBitmapDecoder.

### CreateDecoderFromStream - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## CreateEncoder

Creates a new instance of the IWICBitmapEncoder class.

```cpp
HRESULT CreateEncoder(
    REFGUID           guidContainerFormat, // [in]
    const GUID        *pguidVendor, // [in, optional]
    IWICBitmapEncoder **ppIEncoder // [out, retval]
);
```

### CreateEncoder - Parameter

1. _guidContainerFormat_ - The GUID for the desired container format.

   | Value                    | Meaning                             |
   | :----------------------- | :---------------------------------- |
   | **GUID_ContainerFormatBmp**  | The BMP container format GUID.      |
   | **GUID_ContainerFormatPng**  | The PNG container format GUID.      |
   | **GUID_ContainerFormatIco**  | The ICO container format GUID.      |
   | **GUID_ContainerFormatJpeg** | The JPEG container format GUID.     |
   | **GUID_ContainerFormatTiff** | The TIFF container format GUID.     |
   | **GUID_ContainerFormatGif**  | The GIF container format GUID.      |
   | **GUID_ContainerFormatWmp**  | The HD Photo container format GUID. |

2. _pguidVendor_ - The GUID for the preferred encoder vendor.

   | Value                       | Meaning                                     |
   | :-------------------------- | :------------------------------------------ |
   | **NULL**                        | No preferred codec vendor.                  |
   | **GUID_VendorMicrosoft**        | Prefer to use Microsoft encoder.            |
   | **GUID_VendorMicrosoftBuiltIn** | Prefer to use the native Microsoft encoder. |

3. _ppIEncoder_ - A pointer that receives a pointer to a new IWICBitmapEncoder.

### CreateEncoder - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### CreateEncoder - Remarks

Other values may be available for both guidContainerFormat and pguidVendor depending on the installed WIC-enabled encoders. The values listed are those that are natively supported by the operating system.

## CreateFastMetadataEncoderFromDecoder

Creates a new instance of the fast metadata encoder based on the given IWICBitmapDecoder.

```cpp
HRESULT CreateFastMetadataEncoderFromDecoder(
    IWICBitmapDecoder       *pIDecoder, // [in]
    IWICFastMetadataEncoder **ppIFastEncoder // [out]
);
```

### CreateFastMetadataEncoderFromDecoder - Parameter

1. *pIDecoder* - The decoder to create the fast metadata encoder from.
2. *ppIFastEncoder* - When this method returns, contains a pointer to the new IWICFastMetadataEncoder.

### CreateFastMetadataEncoderFromDecoder - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### CreateFastMetadataEncoderFromDecoder - Remarks

The Windows provided codecs do not support fast metadata encoding at the decoder level, and only support fast metadata encoding at the frame level. To create a fast metadata encoder from a frame, see CreateFastMetadataEncoderFromFrameDecode.

## CreateFastMetadataEncoderFromFrameDecode

Creates a new instance of the fast metadata encoder based on the given image frame.

```cpp
HRESULT CreateFastMetadataEncoderFromFrameDecode(
    IWICBitmapFrameDecode   *pIFrameDecoder, // [in]
    IWICFastMetadataEncoder **ppIFastEncoder // [out]
);
```

### CreateFastMetadataEncoderFromFrameDecode - Parameter

1. *pIFrameDecoder* - The IWICBitmapFrameDecode to create the IWICFastMetadataEncoder from.
2. *ppIFastEncoder* - When this method returns, contains a pointer to a new fast metadata encoder.

### CreateFastMetadataEncoderFromFrameDecode - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### CreateFastMetadataEncoderFromFrameDecode - Remarks

For a list of support metadata formats for fast metadata encoding, see WIC Metadata Overview.

## CreateFormatConverter

Creates a new instance of the IWICFormatConverter class.

```cpp
HRESULT CreateFormatConverter(
    IWICFormatConverter **ppIFormatConverter // [out]
);
```

### CreateFormatConverter - Parameter

1. *ppIFormatConverter* - A pointer that receives a pointer to a new IWICFormatConverter.

### CreateFormatConverter - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## CreatePalette

Creates a new instance of the IWICPalette class.

```cpp
HRESULT CreatePalette(
    IWICPalette **ppIPalette // [out]
);
```

### CreatePalette - Parameter

1. *ppIPalette* - A pointer that receives a pointer to a new IWICPalette.

### CreatePalette - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## CreateQueryWriter

Creates a new instance of a query writer.

```cpp
HRESULT CreateQueryWriter(
     REFGUID                 guidMetadataFormat, // [in]
     const GUID              *pguidVendor, // [in]
    IWICMetadataQueryWriter **ppIQueryWriter // [out]
);
```

### CreateQueryWriter - Parameter

1. *guidMetadataFormat* - The GUID for the desired metadata format.
2. *pguidVendor* - The GUID for the preferred metadata writer vendor. Use NULL if no preferred vendor.
3. *ppIQueryWriter* - When this method returns, contains a pointer to a new IWICMetadataQueryWriter.

### CreateQueryWriter - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## CreateQueryWriterFromReader

Creates a new instance of a query writer based on the given query reader. The query writer will be pre-populated with metadata from the query reader.

```cpp
HRESULT CreateQueryWriterFromReader(
    IWICMetadataQueryReader *pIQueryReader, // [in]
    const GUID              *pguidVendor, // [in]
    IWICMetadataQueryWriter **ppIQueryWriter // [out]
);
```

### CreateQueryWriterFromReader - Parameter

1. *pIQueryReader* - The IWICMetadataQueryReader to create the IWICMetadataQueryWriter from.
2. *pguidVendor* - The GUID for the preferred metadata writer vendor. Use NULL if no preferred vendor.
3. *ppIQueryWriter* - When this method returns, contains a pointer to a new metadata writer.

### CreateQueryWriterFromReader - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## CreateStream

Creates a new instance of the IWICStream class.

```cpp
HRESULT CreateStream(
    IWICStream **ppIWICStream // [out]
);
```

### CreateStream - Parameter

1. *ppIWICStream* - A pointer that receives a pointer to a new IWICStream.

### CreateStream - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.
