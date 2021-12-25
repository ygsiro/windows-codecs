---
layout: interface
category: FUNCTIONS
title: WICCreateBitmapFromSectionEx
code:
  - key: WICSectionAccessLevel
  - key: IWICBitmap
---

Returns a IWICBitmapSource that is backed by the pixels of a Windows Graphics Device Interface (**GDI**) section handle.

```cpp
HRESULT WICCreateBitmapFromSectionEx(
  UINT                  width,             // [in]
  UINT                  height,            // [in]
  REFWICPixelFormatGUID pixelFormat,       // [in]
  HANDLE                hSection,          // [in]
  UINT                  stride,            // [in]
  UINT                  offset,            // [in]
  WICSectionAccessLevel desiredAccessLevel,// [in]
  IWICBitmap            **ppIBitmap        // [out]
);
```

## Parameters

1. *width* - The width of the bitmap pixels.
2. *height* - The height of the bitmap pixels.
3. *pixelFormat* - The pixel format of the bitmap.
4. *hSection* - The section handle.
   This is a file mapping object handle returned by the CreateFileMapping function.
5. *stride* - The byte count of each scanline.
6. *offset* - The offset into the section.
7. *desiredAccessLevel* - The desired access level.
8. *ppIBitmap* - A pointer that receives the bitmap.

## Return value

If this function succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.
