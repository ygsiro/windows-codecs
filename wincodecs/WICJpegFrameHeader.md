---
layout: interface
category: STRUCTURES
title: WICJpegFrameHeader
---

Represents a JPEG frame header.

```cpp
typedef struct WICJpegFrameHeader {
  UINT                  Width;
  UINT                  Height;
  WICJpegTransferMatrix TransferMatrix;
  WICJpegScanType       ScanType;
  UINT                  cComponents;
  DWORD                 ComponentIdentifiers;
  DWORD                 SampleFactors;
  DWORD                 QuantizationTableIndices;
} WICJpegFrameHeader;
```

## Members

### Width

The width of the JPEG frame.

### Height

The height of the JPEG frame.

### TransferMatrix

The transfer matrix of the JPEG frame.

### ScanType

The scan type of the JPEG frame.

### cComponents

The number of components in the frame.

### ComponentIdentifiers

The component identifiers.

### SampleFactors

[wjfd]: IWICJpegFrameDecode

The sample factors. Use one of the following constants, described in [IWICJpegFrameDecode][wjfd] Constants.

- **WIC_JPEG_SAMPLE_FACTORS_ONE**
- **WIC_JPEG_SAMPLE_FACTORS_THREE_420**
- **WIC_JPEG_SAMPLE_FACTORS_THREE_422**
- **WIC_JPEG_SAMPLE_FACTORS_THREE_440**
- **WIC_JPEG_SAMPLE_FACTORS_THREE_444**

### QuantizationTableIndices

The format of the quantization table indices. Use one of the following constants, described in [IWICJpegFrameDecode][wjfd] Constants.

- **WIC_JPEG_QUANTIZATION_BASELINE_ONE**
- **WIC_JPEG_QUANTIZATION_BASELINE_THREE**

## Remarks

[wjfd-gf]: IWICJpegFrameDecode#getframeheader

Get the frame header for an image by calling [IWICJpegFrameDecode][wjfd]::[GetFrameHeader][wjfd-gf].

## Related

- [IWICJpegFrameDecode::GetFrameHeader](IWICJpegFrameDecode#getframeheader)
