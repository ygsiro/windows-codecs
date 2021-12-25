---
layout: interface
category: ENUMERATIONS
title: WICBitmapCreateCacheOption
---

Specifies the desired cache usage.

```cpp
typedef enum WICBitmapCreateCacheOption {
  WICBitmapNoCache,
  WICBitmapCacheOnDemand,
  WICBitmapCacheOnLoad,
  WICBITMAPCREATECACHEOPTION_FORCE_DWORD
} ;
```

## WICBitmapNoCache

Do not cache the bitmap.

## WICBitmapCacheOnDemand

Cache the bitmap when needed.

## WICBitmapCacheOnLoad

Cache the bitmap at initialization.

## Remarks

The CreateBitmap of the [IWICImagingFactory][wif] interface does not support [WICBitmapNoCache][wbnc] when the pixelFormat is a native pixel format provided by Windows Imaging Component (**WIC**).

[wif]: IWICImagingFactory
[wbnc]: #wicbitmapnocache
