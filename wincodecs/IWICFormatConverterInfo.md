---
layout: interface
category: Interface
title: IWICFormatConverterInfo
TOC:
  - name: Inheritance
---

Exposes methods that provide information about a pixel format converter.

## Inheritance

The IWICFormatConverterInfo interface inherits from IWICComponentInfo. IWICFormatConverterInfo also has these types of members:

## CreateInstance

Creates a new IWICFormatConverter instance.

```cpp
HRESULT CreateInstance(
    IWICFormatConverter **ppIConverter // [out]
);
```

### CreateInstance - Parameter

1. *ppIConverter* - A pointer that receives a new IWICFormatConverter instance.

### CreateInstance - Return value

If this method succeeds, it returns **S_OK**. Otherwise, it returns an **HRESULT** error code.

## GetPixelFormats

Retrieves a list of GUIDs that signify which pixel formats the converter supports.

```cpp
HRESULT GetPixelFormats(
    UINT               cFormats, // [in]
    WICPixelFormatGUID *pPixelFormatGUIDs, // [in, out]
    UINT               *pcActual // [out]
);
```

### GetPixelFormats - Parameter

1. *cFormats* - The size of the pPixelFormatGUIDs array.
2. *pPixelFormatGUIDs* - Pointer to a GUID array that receives the pixel formats the converter supports.
3. *pcActual* - The actual array size needed to retrieve all pixel formats supported by the converter.

### GetPixelFormats - Return value

If this method succeeds, it returns **S_OK**. Otherwise, it returns an **HRESULT** error code.

### GetPixelFormats - Remarks

The format converter does not necessarily guarantee symmetricality with respect to conversion; that is, a converter may be able to convert FROM a particular format without actually being able to convert TO a particular format. In order to test symmetricality, use CanConvert.

To determine the number of pixel formats a converter can handle, set cFormats to 0 and pPixelFormatGUIDs to NULL. The converter will fill pcActual with the number of formats supported by that converter.
