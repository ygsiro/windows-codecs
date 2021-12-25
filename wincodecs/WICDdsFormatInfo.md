---
layout: interface
category: STRUCTURES
title: WICDdsFormatInfo
---

Specifies the DXGI_FORMAT and block information of a DDS format.

```cpp
typedef struct WICDdsFormatInfo {
  DXGI_FORMAT DxgiFormat;
  UINT        BytesPerBlock;
  UINT        BlockWidth;
  UINT        BlockHeight;
} WICDdsFormatInfo;
```

## Members

### DxgiFormat

DXGI format

### BytesPerBlock

The size of a single block in bytes.
For DXGI_FORMAT values that are not block-based, the value is equal to the size of a single pixel in bytes.

### BlockWidth

The width of a single block in pixels.
For **DXGI_FORMAT** values that are not block-based, the value is 1.

### BlockHeight

The height of a single block in pixels.
For **DXGI_FORMAT** values that are not block-based, the value is 1.
