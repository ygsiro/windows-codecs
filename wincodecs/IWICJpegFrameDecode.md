---
layout: interface
category: Interface
title: IWICJpegFrameDecode
TOC:
  - name: Inheritance
---

Exposes methods for decoding JPEG images.
Provides access to the Start Of Frame (**SOF**) header, Start of Scan (**SOS**) header, the Huffman and Quantization tables, and the compressed JPEG JPEG data. Also enables indexing for efficient random access.

## Inheritance

The IWICJpegFrameDecode interface inherits from the IUnknown interface. IWICJpegFrameDecode also has these types of members:

## ClearIndexing

Removes the indexing from a JPEG that has been indexed using SetIndexing

```cpp
HRESULT ClearIndexing();
```

### ClearIndexing - Return value

Returns S_OK upon successful completion.

## CopyScan

Retrieves a copy of the compressed JPEG scan directly from the WIC decoder frame's output stream.

```cpp
HRESULT CopyScan(
    UINT scanIndex, // [in]
    UINT scanOffset, // [in]
    UINT cbScanData, // [in]
    BYTE *pbScanData, // [out]
    UINT *pcbScanDataActual // [out]
);
```

### CopyScan - Parameter

1. _scanIndex_ - The zero-based index of the scan for which data is retrieved.
2. _scanOffset_ - The byte position in the scan data to begin copying. Use 0 on the first call. If the output buffer size is insufficient to store the entire scan, this offset allows you to resume copying from the end of the previous copy operation.
3. _cbScanData_ - The size, in bytes, of the pbScanData array.
4. _pbScanData_ - A pointer that receives the table data. This parameter must not be NULL.
5. _pcbScanDataActual_ - A pointer that receives the size of the scan data actually copied into pbScanData. The size returned may be smaller that the size of cbScanData. This parameter may be NULL.

### CopyScan - Return value

This method can return one of these values.

| Return value                      | Description                          |
| :-------------------------------- | :----------------------------------- |
| S_OK                              | The operation was successful.        |
| WINCODEC_ERR_INVALIDJPEGSCANINDEX | The specified scan index is invalid. |

## DoesSupportIndexing

Retrieves a value indicating whether this decoder supports indexing for efficient random access.

```cpp
HRESULT DoesSupportIndexing(
  BOOL *pfIndexingSupported
);
```

### DoesSupportIndexing - Parameter

1. _pfIndexingSupported_ - True if indexing is supported; otherwise, false.

### DoesSupportIndexing - Return value

Returns S_OK on successful completion.

### DoesSupportIndexing - Remarks

Indexing is only supported for some JPEG types. Call this method

## GetAcHuffmanTable

Retrieves a copy of the AC Huffman table for the specified scan and table.

```cpp
HRESULT GetAcHuffmanTable(
    UINT                       scanIndex, // [in]
     UINT                       tableIndex, // [in]
    DXGI_JPEG_AC_HUFFMAN_TABLE *pAcHuffmanTable // [out]
);
```

### GetAcHuffmanTable - Parameter

1. _scanIndex_ - The zero-based index of the scan for which data is retrieved.
2. _tableIndex_ - The index of the AC Huffman table to retrieve. Valid indices for a given scan can be determined by retrieving the scan header with IWICJpegFrameDecode::GetScanHeader.
3. _pAcHuffmanTable_ - A pointer that receives the table data. This parameter must not be NULL.

### GetAcHuffmanTable - Return value

| Return value                      | Description                                                                                                                                |
| :-------------------------------- | :----------------------------------------------------------------------------------------------------------------------------------------- |
| S_OK                              | The operation was successful.                                                                                                              |
| WINCODEC_ERR_INVALIDJPEGSCANINDEX | The specified scan index is invalid.                                                                                                       |
| WINCODEC_ERR_INVALIDPARAMETER     | Can occur if pAcHuffmanTable is NULL or if tableIndex does not point to a valid table slot. Check the scan header for valid table indices. |

## GetDcHuffmanTable

Retrieves a copy of the DC Huffman table for the specified scan and table.

```cpp
HRESULT GetDcHuffmanTable(
    UINT                       scanIndex, // [in]
    UINT                       tableIndex, // [in]
    DXGI_JPEG_DC_HUFFMAN_TABLE *pDcHuffmanTable // [out]
);
```

### GetDcHuffmanTable - Parameter

1. *scanIndex* - The zero-based index of the scan for which data is retrieved.
2. *tableIndex* - The index of the DC Huffman table to retrieve. Valid indices for a given scan can be determined by retrieving the scan header with IWICJpegFrameDecode::GetScanHeader.
3. *pDcHuffmanTable* - A pointer that receives the table data. This parameter must not be NULL.

### GetDcHuffmanTable - Return value

| Return value                      | Description                                                                                                                                |
| :-------------------------------- | :----------------------------------------------------------------------------------------------------------------------------------------- |
| S_OK                              | The operation was successful.                                                                                                              |
| WINCODEC_ERR_INVALIDJPEGSCANINDEX | The specified scan index is invalid.                                                                                                       |
| WINCODEC_ERR_INVALIDPARAMETER     | Can occur if pTable is NULL or if tableIndex does not point to a valid table slot. Check the scan header for valid table indices. |

## GetFrameHeader

Retrieves header data from the entire frame. The result includes parameters from the Start Of Frame (SOF) marker for the scan as well as parameters derived from other metadata such as the color model of the compressed data.

```cpp
HRESULT GetFrameHeader(
    WICJpegFrameHeader *pFrameHeader // [out]
);
```

### GetFrameHeader - Parameter

1. *pFrameHeader* - A pointer that receives the frame header data.

### GetFrameHeader - Return value

Returns S_OK on successful completion.

## GetQuantizationTable

Retrieves a copy of the quantization table.

```cpp
HRESULT GetQuantizationTable(
    UINT                         scanIndex, // [in]
     UINT                         tableIndex, // [in]
    DXGI_JPEG_QUANTIZATION_TABLE *pQuantizationTable // [out]
);
```

### GetQuantizationTable - Parameter

1. *scanIndex* - The zero-based index of the scan for which data is retrieved.
2. *tableIndex* - The index of the quantization table to retrieve. Valid indices for a given scan can be determined by retrieving the scan header with IWICJpegFrameDecode::GetScanHeader.
3. *pQuantizationTable* - A pointer that receives the table data. This parameter must not be NULL.

### GetQuantizationTable - Return value

This method can return one of these values.

|Return value|Description|
|:--|:--|
|S_OK|The operation was successful.|
|WINCODEC_ERR_INVALIDJPEGSCANINDEX|The specified scan index is invalid.|
|WINCODEC_ERR_INVALIDPARAMETER|Can occur if pTable is NULL or if tableIndex does not point to a valid table slot. Check the scan header for valid table indices.|

## GetScanHeader

Retrieves parameters from the Start Of Scan (SOS) marker for the scan with the specified index.

```cpp
HRESULT GetScanHeader(
    UINT              scanIndex, // [in]
    WICJpegScanHeader *pScanHeader // [out]
);
```

### GetScanHeader - Parameter

1. *scanIndex* - The index of the scan for which header data is retrieved.
2. *pScanHeader* - A pointer that receives the frame header data.

### GetScanHeader - Return value

Returns S_OK on successful completion.

## SetIndexing

Enables indexing of the JPEG for efficient random access.

```cpp
HRESULT SetIndexing(
  WICJpegIndexingOptions options, // [in]
  UINT                   horizontalIntervalSize // [in]
);
```

### SetIndexing - Parameter

1. *options* - A value specifying whether indexes should be generated immediately or deferred until a future call to IWICBitmapSource::CopyPixels.
2. *horizontalIntervalSize* - The granularity of the indexing, in pixels.

### SetIndexing - Return value

Returns S_OK upon successful completion.

### SetIndexing - Remarks

This method enables efficient random-access to the image pixels at the expense of memory usage. The amount of memory required for indexing depends on the requested index granularity. Unless SetIndexing is called, it is much more efficient to access a JPEG by progressing through its pixels top-down during calls to IWICBitmapSource::CopyPixels.

This method will fail if indexing is unsupported on the file. IWICJpegFrameDecode::DoesSupportIndexing should be called to first determine whether indexing is supported. If this method is called multiple times, the final call changes the index granularity to the requested size.

The provided interval size controls horizontal spacing of index entries. This value is internally rounded up according to the JPEG’s MCU (minimum coded unit) size, which is typically either 8 or 16 unscaled pixels. The vertical size of the index interval is always equal to one MCU size.

Indexes can be generated immediately, or during future calls to IWICBitmapSource::CopyPixels to reduce redundant decompression work.
