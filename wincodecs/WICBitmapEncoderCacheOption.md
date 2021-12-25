---
layout: interface
category: ENUMERATIONS
title: WICBitmapEncoderCacheOption
---

Specifies the cache options available for an encoder.

```cpp
typedef enum WICBitmapEncoderCacheOption {
  WICBitmapEncoderCacheInMemory,
  WICBitmapEncoderCacheTempFile,
  WICBitmapEncoderNoCache,
  WICBITMAPENCODERCACHEOPTION_FORCE_DWORD
} ;
```

## WICBitmapEncoderCacheInMemory

The encoder is cached in memory.
This option is not supported.

## WICBitmapEncoderCacheTempFile

The encoder is cached to a temporary file.
This option is not supported.

## WICBitmapEncoderNoCache

The encoder is not cached.
