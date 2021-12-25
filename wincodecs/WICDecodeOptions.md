---
layout: interface
category: ENUMERATIONS
title: WICDecodeOptions
---

Specifies decode options.

```cpp
typedef enum WICDecodeOptions {
  WICDecodeMetadataCacheOnDemand,
  WICDecodeMetadataCacheOnLoad,
  WICMETADATACACHEOPTION_FORCE_DWORD
} ;
```

## WICDecodeMetadataCacheOnDemand

Cache metadata when needed.

## WICDecodeMetadataCacheOnLoad

Cache metadata when decoder is loaded.
