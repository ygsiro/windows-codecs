---
layout: interface
category: ENUMERATIONS
title: WICRawRotationCapabilities
---

Specifies the rotation capabilities of the codec.

```cpp
typedef enum WICRawRotationCapabilities {
  WICRawRotationCapabilityNotSupported,
  WICRawRotationCapabilityGetSupported,
  WICRawRotationCapabilityNinetyDegreesSupported,
  WICRawRotationCapabilityFullySupported,
  WICRAWROTATIONCAPABILITIES_FORCE_DWORD
} ;
```

## WICRawRotationCapabilityNotSupported

Rotation is not supported.

## WICRawRotationCapabilityGetSupported

Set operations for rotation is not supported.

## WICRawRotationCapabilityNinetyDegreesSupported

90 degree rotations are supported.

## WICRawRotationCapabilityFullySupported

All rotation angles are supported.
