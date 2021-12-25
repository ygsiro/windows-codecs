---
layout: interface
category: Interface
title: IWICJpegFrameEncode
TOC:
  - name: Inheritance
  - name: Remarks
  - name: GetAcHuffmanTable
  - name: GetDcHuffmanTable
  - name: GetQuantizationTable
  - name: WriteScan
---

Exposes methods for writing compressed JPEG scan data directly to the WIC encoder's output stream.
Also provides access to the Huffman and quantization tables.

## Inheritance

The **IWICJpegFrameEncode** interface inherits from the IUnknown interface.
**IWICJpegFrameEncode** also has these types of members:

- [GetAcHuffmanTable](#getachuffmantable)
- [GetDcHuffmanTable](#getdchuffmantable)
- [GetQuantizationTable](#getquantizationtable)
- [WriteScan](#writescan)

## Remarks

[wbfe]: IWICBitmapFrameEncoder

Obtain this interface by calling IUnknown::QueryInterface on the Windows-provided [IWICBitmapFrameEncoder][wbfe] interface for the JPEG encoder.

The WIC JPEG encoder supports a smaller subset of JPEG features than the decoder does.

- The encoder is limited to a single scan.
  It does not support encoding images that are multi-scan, either for progressive encoding or planar component data.
- The encoder supports two quantization tables, two AC Huffman tables, and two DC Huffman tables.
  The luma tables are used for the Y channel and, in the case of YCCK, the black channel.
  The chroma tables are used for the CbCr channels.
- The encoder supports encoding gray, YCbCr (**RGB**), and YCCK (**CMYK**).
- The encoder supports 4 fixed component subsampling, 4:2:0, 4:2:2, 4:4:0, and 4:4:4.
  This subsamples chroma only.
- The encoder does not support restart markers.

## GetAcHuffmanTable

Retrieves a copy of the AC Huffman table for the specified scan and table.

```cpp
HRESULT GetAcHuffmanTable(
    UINT                       scanIndex,       // [in]
    UINT                       tableIndex,      // [in]
    DXGI_JPEG_AC_HUFFMAN_TABLE *pAcHuffmanTable // [out]
);
```

### GetAcHuffmanTable - Parameter

1. _scanIndex_ - The zero-based index of the scan for which data is retrieved.
2. _tableIndex_ - The index of the AC Huffman table to retrieve.
3. _pAcHuffmanTable_ - A pointer that receives the table data. This parameter must not be NULL.

### GetAcHuffmanTable - Return value

This method can return one of these values.

| Return value  | Description                  |
| :------------ | :-------------------------------------- |
| S_OK          | The operation was successful.          |
| **WINCODEC_ERR_INVALIDJPEGSCANINDEX** | The specified scan index is invalid.                       |
| **WINCODEC_ERR_INVALIDPARAMETER**     | Can occur if *pAcHuffmanTable* is **NULL** or if *tableIndex* does not point to a valid table slot. Check the scan header for valid table indices. |

## GetDcHuffmanTable

Retrieves a copy of the DC Huffman table for the specified scan and table.

```cpp
HRESULT GetDcHuffmanTable(
    UINT                       scanIndex,       // [in]
    UINT                       tableIndex,      // [in]
    DXGI_JPEG_DC_HUFFMAN_TABLE *pDcHuffmanTable // [out]
);
```

### GetDcHuffmanTable - Parameter

1. _scanIndex_ - The zero-based index of the scan for which data is retrieved.
2. _tableIndex_ - The index of the DC Huffman table to retrieve.
3. _pDcHuffmanTable_ - A pointer that receives the table data. This parameter must not be NULL.

### GetDcHuffmanTable - Return value

| Return value      | Description                   |
| :---------------- | :---------------------------- |
| **S_OK**          | The operation was successful. |
| **WINCODEC_ERR_INVALIDJPEGSCANINDEX** | The specified scan index is invalid.              |
| **WINCODEC_ERR_INVALIDPARAMETER**     | Can occur if *pTable* is **NULL** or if *tableIndex* does not point to a valid table slot. Check the scan header for valid table indices. |

## GetQuantizationTable

Retrieves a copy of the quantization table.

```cpp
HRESULT GetQuantizationTable(
    UINT                         scanIndex,          // [in]
    UINT                         tableIndex,         // [in]
    DXGI_JPEG_QUANTIZATION_TABLE *pQuantizationTable // [out]
);
```

### GetQuantizationTable - Parameter

1. _scanIndex_ - The zero-based index of the scan for which data is retrieved.
2. _tableIndex_ - The index of the quantization table to retrieve.
3. _pQuantizationTable_ - A pointer that receives the table data. This parameter must not be NULL.

### GetQuantizationTable - Return value

| Return value     | Description                   |
| :--------------- | :---------------------------- |
| **S_OK**         | The operation was successful. |
| **WINCODEC_ERR_INVALIDJPEGSCANINDEX** | The specified scan index is invalid.          |
| **WINCODEC_ERR_INVALIDPARAMETER**     | Can occur if *pTable* is **NULL** or if *tableIndex* does not point to a valid table slot. Check the scan header for valid table indices. |

## WriteScan

Writes scan data to a JPEG frame.

```cpp
HRESULT WriteScan(
  UINT       cbScanData, // [in]
  const BYTE *pbScanData // [in]
);
```

### WriteScan - Parameter

1. _cbScanData_ - The size of the data in the pbScanData parameter.
2. _pbScanData_ - The scan data to write.

### WriteScan - Return value

Returns **S_OK** on successful completion.

### WriteScan - Remarks

[wbfe-c]: IWICBitmapFrameEncode#commit
[wbfe-scc]: IWICBitmapFrameEncode#setcolorcontexts
[wbfe-sp]: IWICBitmapFrameEncode#setpalette
[wbfe-spf]: IWICBitmapFrameEncode#setpixelformat
[wbfe-sr]: IWICBitmapFrameEncode#setresolution
[wbfe-st]: IWICBitmapFrameEncode#setthumbnail
[wbfe-ss]: IWICBitmapFrameEncode#setsize

WriteScan may be called multiple times.
Each call appends the scan data specified to any previous scan data.
Complete the scan by calling [IWICBitmapFrameEncode][wbfe]::[Commit][wbfe-c].

Any calls to set encoder parameters or image metadata that will appear before the scan data in the resulting JPEG file must be completed before the first call to this method.
This includes calls to [IWICBitmapFrameEncode][wbfe]::[SetColorContexts][wbfe-scc] , [IWICBitmapFrameEncode][wbfe]::[SetPalette][wbfe-sp], [IWICBitmapFrameEncode][wbfe]::[SetPixelFormat][wbfe-spf], [IWICBitmapFrameEncode][wbfe]::[SetResolution][wbfe-sr], and [IWICBitmapFrameEncode][wbfe]::[SetThumbnail][wbfe-st].
[IWICBitmapFrameEncode][wbfe]::[SetSize][wbfe-ss] is required as it has no default value for encoded image size.
