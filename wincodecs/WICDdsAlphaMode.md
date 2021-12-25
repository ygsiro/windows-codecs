---
layout: interface
category: ENUMERATIONS
title: WICDdsAlphaMode
---

Specifies the the meaning of pixel color component values contained in the DDS image.

```cpp
typedef enum WICDdsAlphaMode {
  WICDdsAlphaModeUnknown,
  WICDdsAlphaModeStraight,
  WICDdsAlphaModePremultiplied,
  WICDdsAlphaModeOpaque,
  WICDdsAlphaModeCustom,
  WICDDSALPHAMODE_FORCE_DWORD
};
```

## WICDdsAlphaModeUnknown

Alpha behavior is unspecified and must be determined by the reader.

## WICDdsAlphaModeStraight

The alpha data is straight.

## WICDdsAlphaModePremultiplied

The alpha data is premultiplied.

## WICDdsAlphaModeOpaque

The alpha data is opaque (UNORM value of 1).
This can be used by a compliant reader as a performance optimization.
For example, blending operations can be converted to copies.

## WICDdsAlphaModeCustom

The alpha channel contains custom data that is not alpha.
