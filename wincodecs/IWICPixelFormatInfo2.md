---
layout: interface
category: Interface
title: IWICPixelFormatInfo2
TOC:
  - name: Inheritance
---

Extends IWICPixelFormatInfo by providing additional information about a pixel format.

## Inheritance

The IWICPixelFormatInfo2 interface inherits from IWICPixelFormatInfo. IWICPixelFormatInfo2 also has these types of members:

## GetNumericRepresentation

Retrieves the WICPixelFormatNumericRepresentation of the pixel format.

```cpp
HRESULT GetNumericRepresentation(
    WICPixelFormatNumericRepresentation *pNumericRepresentation // [out]
);
```

### GetNumericRepresentation - Parameter

1. *pNumericRepresentation* - The address of a WICPixelFormatNumericRepresentation variable that you've defined. On successful completion, the function sets your variable to the WICPixelFormatNumericRepresentation of the pixel format.

### GetNumericRepresentation - Return value

If this method succeeds, it returns **S_OK**. Otherwise, it returns an **HRESULT** error code.

## SupportsTransparency

Returns whether the format supports transparent pixels.

```cpp
HRESULT SupportsTransparency(
    BOOL *pfSupportsTransparency // [out]
);
```

### SupportsTransparency - Parameter

1. *pfSupportsTransparency* - Returns TRUE if the pixel format supports transparency; otherwise, FALSE.

### SupportsTransparency - Return value

If this method succeeds, it returns **S_OK**. Otherwise, it returns an **HRESULT** error code.

### SupportsTransparency - Remarks

An indexed pixel format will not return TRUE even though it may have some transparency support.
