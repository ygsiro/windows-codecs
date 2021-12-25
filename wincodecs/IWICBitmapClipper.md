---
layout: interface
category: Interface
title: IWICBitmapClipper
code:
  - key: IWICBitmapSource
  - key: WICRect
TOC:
  - name: Inheritance
  - name: Initialize
  - name: Related
---

Exposes methods that produce a clipped version of the input bitmap for a specified rectangular region of interest.

## Inheritance

The **IWICBitmapClipper** interface inherits from [IWICBitmapSource][bs].
**IWICBitmapClipper** also has these types of members:

- [Initialize](#initialize)

## Initialize

Initializes the bitmap clipper with the provided parameters.

```cpp
HRESULT Initialize(
  IWICBitmapSource *pISource, // [in]
  const WICRect    *prc       // [in]
);
```

### Initialize - Parameters

1. _pISource_ - he input bitmap source.
2. _prc_ - The rectangle of the bitmap source to clip.

### Initialize - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

[bs]: IWICBitmapSource

## Related

- [IWICImagingFactory::CreateBitmapClipper](IWICImagingFactory#createbitmapclipper)
