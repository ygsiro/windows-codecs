---
layout: interface
category: Interface
title: IWICPixelFormatInfo2
TOC:
  - name: Inheritance
  - name: GetNumericRepresentation
  - name: SupportsTransparency
code:
  - key: WICPixelFormatNumericRepresentation
---

Extends [IWICPixelFormatInfo][wpfi] by providing additional information about a pixel format.

[wpfi]: IWICPixelFormatInfo

## Inheritance

The **IWICPixelFormatInfo2** interface inherits from [IWICPixelFormatInfo][wpfi].
**IWICPixelFormatInfo2** also has these types of members:

- [getnumericrepresentation](#getnumericRepresentation)
- [SupportsTransparency](#supportstransparency)

## GetNumericRepresentation

Retrieves the [WICPixelFormatNumericRepresentation][wpfnr] of the pixel format.

[wpfnr]: WICPixelFormatNumericRepresentation

```cpp
HRESULT GetNumericRepresentation(
    WICPixelFormatNumericRepresentation *pNumericRepresentation // [out]
);
```

### GetNumericRepresentation - Parameter

1. *pNumericRepresentation* - The address of a [WICPixelFormatNumericRepresentation][wpfnr] variable that you've defined.
   On successful completion, the function sets your variable to the [WICPixelFormatNumericRepresentation][wpfnr] of the pixel format.

### GetNumericRepresentation - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## SupportsTransparency

Returns whether the format supports transparent pixels.

```cpp
HRESULT SupportsTransparency(
    BOOL *pfSupportsTransparency // [out]
);
```

### SupportsTransparency - Parameter

1. *pfSupportsTransparency* - Returns **TRUE** if the pixel format supports transparency; otherwise, **FALSE**.

### SupportsTransparency - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### SupportsTransparency - Remarks

An indexed pixel format will not return TRUE even though it may have some transparency support.
