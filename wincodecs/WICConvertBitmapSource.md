---
layout: interface
category: FUNCTIONS
title: WICConvertBitmapSource
code:
  - key: IWICBitmapSource
---

Obtains a IWICBitmapSource in the desired pixel format from a given IWICBitmapSource.

```cpp
HRESULT WICConvertBitmapSource(
  REFWICPixelFormatGUID dstFormat, // [in]
  IWICBitmapSource      *pISrc,    // [in]
  IWICBitmapSource      **ppIDst   // [out]
);
```

## Parameters

1. *dstFormat* - The pixel format to convert to.
2. *pISrc* - The source bitmap.
3. *ppIDst* - A pointer to the null-initialized destination bitmap pointer.

## ReturnValue

If this function succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## Remarks

If the *pISrc* bitmap is already in the desired format, then *pISrc* is copied to the destination bitmap pointer and a reference is added.
If it is not in the desired format however, **WICConvertBitmapSource** will instantiate a *dstFormat* format converter and initialize it with *pISrc*.
