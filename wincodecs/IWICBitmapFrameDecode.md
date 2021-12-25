---
layout: interface
category: Interface
title: IWICBitmapFrameDecode
TOC:
  - name: Inheritance
  - name: GetColorContexts
  - name: GetMetadataQueryReader
  - name: GetThumbnail
  - name: Related
code:
  - key: IWICBitmapSource
  - key: IWICColorContext
  - key: IWICMetadataQueryReader
---

Defines methods for decoding individual image frames of an encoded file.

## Inheritance

The **IWICBitmapFrameDecode** interface inherits from [IWICBitmapSource][wbs].
**IWICBitmapFrameDecode** also has these types of members:

- [GetColorContexts](#getcolorcontexts)
- [GetMetadataQueryReader](#getmetadataqueryreader)
- [GetThumbnail](#getthumbnail)

[wbs]: IWICBitmapSource

## GetColorContexts

Retrieves the [IWICColorContext][wcc] associated with the image frame.

[wcc]: IWICColorContext

```c++
HRESULT GetColorContexts(
  UINT             cCount,             // [in]
  IWICColorContext **ppIColorContexts, // [in, out]
  UINT             *pcActualCount      // [out]
);
```

### GetColorContexts - Parameter

1. _cCount_ - The number of color contexts to retrieve.
   This value must be the size of, or smaller than, the size available to _ppIColorContexts_.
2. _ppIColorContexts_ - A pointer that receives a pointer to the [IWICColorContext][wcc] objects.
3. _pcActualCount_ - A pointer that receives the number of color contexts contained in the image frame.

### GetColorContexts - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### GetColorContexts - Remarks

If **NULL** is passed for _ppIColorContexts_, and 0 is passed for cCount, this method will return the total number of color contexts in the image in _pcActualCount_.

The _ppIColorContexts_ array must be filled with valid data: each [IWICColorContext][wcc]\* in the array must have been created using [IWICImagingFactory][wif]::[CreateColorContext][wif-ccc].

[wif]: IWICImagingFactory
[wif-ccc]: IWICImagingFactory#createcolorcontext

## GetMetadataQueryReader

Retrieves a metadata query reader for the frame.

```cpp
HRESULT GetMetadataQueryReader(
  IWICMetadataQueryReader **ppIMetadataQueryReader // [out]
);
```

### GetMetadataQueryReader - Parameter

1. _ppIMetadataQueryReader_ - When this method returns, contains a pointer to the frame's metadata query reader.

### GetMetadataQueryReader - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### GetMetadataQueryReader - Remarks

For image formats with one frame (**JPG**, **PNG**, **JPEG-XR**), the frame-level query reader of the first frame is used to access all image metadata, and the decoder-level query reader isn’t used.
For formats with more than one frame (**GIF**, **TIFF**), the frame-level query reader for a given frame is used to access metadata specific to that frame, and in the case of **GIF** a decoder-level metadata reader will be present.
If the decoder doesn’t support metadata (**BMP**, **ICO**), this will return **WINCODEC_ERR_UNSUPPORTEDOPERATION**.

## GetThumbnail

Retrieves a small preview of the frame, if supported by the codec.

```cpp
HRESULT GetThumbnail(
  IWICBitmapSource **ppIThumbnail // [out]
);
```

### GetThumbnail - Parameter

1. _ppIThumbnail_ - A pointer that receives a pointer to the [IWICBitmapSource][wbs] of the thumbnail.

### GetThumbnail - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### GetThumbnail - Remarks

Not all formats support thumbnails.
Joint Photographic Experts Group (**JPEG**), Tagged Image File Format (**TIFF**), and Microsoft Windows Digital Photo (**WDP**) support thumbnails.

### GetThumbnail - Note to Implementers

If the codec does not support thumbnails, return **WINCODEC_ERROR_CODECNOTHUMBNAIL** rather than **E_NOTIMPL**.

## Related

- [IWICDdsDecoder::GetFrame](IWICDdsDecoder#getframe)
