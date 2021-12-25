---
layout: interface
category: ENUMERATIONS
title: WICRawCapabilities
---

Specifies the capability support of a raw image.

```cpp
typedef enum WICRawCapabilities {
  WICRawCapabilityNotSupported,
  WICRawCapabilityGetSupported,
  WICRawCapabilityFullySupported,
  WICRAWCAPABILITIES_FORCE_DWORD
} ;
```

## WICRawCapabilityNotSupported

The capability is not supported.

## WICRawCapabilityGetSupported

The capability supports only get operations.

## WICRawCapabilityFullySupported

The capability supports get and set operations.
