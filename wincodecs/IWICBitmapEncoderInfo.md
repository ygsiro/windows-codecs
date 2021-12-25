---
layout: interface
category: Interface
title: IWICBitmapEncoderInfo
code:
  - key: IWICBitmapEncoder
TOC:
  - name: Inheritance
  - name: CreateInstance
---

Exposes methods that provide information about an encoder.

## Inheritance

The **IWICBitmapEncoderInfo** interface inherits from [IWICBitmapCodecInfo][wbci].
**IWICBitmapEncoderInfo** also has these types of members:

- [CreateInstance](#createinstance)

## CreateInstance

Creates a new [IWICBitmapEncoder][wbe] instance.

```cpp
HRESULT CreateInstance(
  IWICBitmapEncoder **ppIBitmapEncoder // [out]
);
```

### CreateInstance - Parameters

1. _ppIBitmapEncoder_ - A pointer that receives a pointer to a new [IWICBitmapEncoder][wbe] instance.

### CreateInstance - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

[wbe]: IWICBitmapEncoder
[wbci]: IWICBitmapCodecInfo
