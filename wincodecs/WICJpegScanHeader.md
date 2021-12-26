---
layout: interface
category: STRUCTURES
title: WICJpegScanHeader
---

Represents a JPEG frame header.

```cpp
typedef struct WICJpegScanHeader {
  UINT  cComponents;
  UINT  RestartInterval;
  DWORD ComponentSelectors;
  DWORD HuffmanTableIndices;
  BYTE  StartSpectralSelection;
  BYTE  EndSpectralSelection;
  BYTE  SuccessiveApproximationHigh;
  BYTE  SuccessiveApproximationLow;
} WICJpegScanHeader;
```

## Members

### cComponents

The number of components in the scan.

### RestartInterval

The interval of reset markers within the scan.

### ComponentSelectors

The component identifiers.

### HuffmanTableIndices

[wjfd]: IWICJpegFrameDecode

The format of the quantization table indices.
Use one of the following constants, described in [IWICJpegFrameDecode][wjfd] Constants.

- **WIC_JPEG_HUFFMAN_BASELINE_ONE**
- **WIC_JPEG_HUFFMAN_BASELINE_THREE**

### StartSpectralSelection

The start of the spectral selection.

### EndSpectralSelection

The end of the spectral selection.

### SuccessiveApproximationHigh

The successive approximation high.

### SuccessiveApproximationLow

The successive approximation low.

## Remarks

[wjfd-gsh]: IWICJpegFrameDecode#getscanheader

Get the scan header for an image by calling [IWICJpegFrameDecode][wjfd]::[GetScanHeader][wjfd].

## Related

- [IWICJpegFrameDecode::GetScanHeader](IWICJpegFrameDecode#getscanheader)
