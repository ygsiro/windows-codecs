---
layout: interface
category: Interface
title: IWICFastMetadataEncoder
TOC:
  - name: Inheritance
---

Exposes methods used for in-place metadata editing.
A fast metadata encoder enables you to add and remove metadata to an image without having to fully re-encode the image.

## Inheritance

The IWICFastMetadataEncoder interface inherits from the IUnknown interface. IWICFastMetadataEncoder also has these types of members:

## Remarks

A decoder must be created using the WICDecodeOptions value WICDecodeMetadataCacheOnDemand to perform in-place metadata updates. Using the WICDecodeMetadataCacheOnLoad option causes the decoder to release the file stream necessary to perform the metadata updates.

Not all metadata formats support fast metadata encoding. The native metadata handlers that support metadata are IFD, Exif, XMP, and GPS.

If a fast metadata encoder fails, the image will need to be fully re-encoded to add the metadata.

## Commit

Finalizes metadata changes to the image stream.

```cpp
HRESULT Commit();
```

### Commit - Return value

If this method succeeds, it returns **S_OK**. Otherwise, it returns an **HRESULT** error code.

### Commit - Remarks

If the commit fails and returns WINCODEC_ERR_STREAMNOTAVAILABLE, ensure that the image decoder was loaded using the WICDecodeMetadataCacheOnDemand option. A fast metadata encoder is not supported when the decoder is created using the WICDecodeMetadataCacheOnLoad option.

If the commit fails for any reason, you will need to re-encode the image to ensure the new metadata is added to the image.

## GetMetadataQueryWriter

Retrieves a metadata query writer for fast metadata encoding.

```cpp
HRESULT GetMetadataQueryWriter(
    IWICMetadataQueryWriter **ppIMetadataQueryWriter // [out]
);
```

### GetMetadataQueryWriter - Parameter

1. *ppIMetadataQueryWriter* - When this method returns, contains a pointer to the fast metadata encoder's metadata query writer.

### GetMetadataQueryWriter - Return value

If this method succeeds, it returns **S_OK**. Otherwise, it returns an **HRESULT** error code.
