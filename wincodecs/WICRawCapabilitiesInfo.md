---
layout: interface
category: STRUCTURES
title: WICRawCapabilitiesInfo
---

Defines raw codec capabilities.

```cpp
typedef struct WICRawCapabilitiesInfo {
  UINT                       cbSize;
  UINT                       CodecMajorVersion;
  UINT                       CodecMinorVersion;
  WICRawCapabilities         ExposureCompensationSupport;
  WICRawCapabilities         ContrastSupport;
  WICRawCapabilities         RGBWhitePointSupport;
  WICRawCapabilities         NamedWhitePointSupport;
  UINT                       NamedWhitePointSupportMask;
  WICRawCapabilities         KelvinWhitePointSupport;
  WICRawCapabilities         GammaSupport;
  WICRawCapabilities         TintSupport;
  WICRawCapabilities         SaturationSupport;
  WICRawCapabilities         SharpnessSupport;
  WICRawCapabilities         NoiseReductionSupport;
  WICRawCapabilities         DestinationColorProfileSupport;
  WICRawCapabilities         ToneCurveSupport;
  WICRawRotationCapabilities RotationSupport;
  WICRawCapabilities         RenderModeSupport;
} WICRawCapabilitiesInfo;
```

## Members

### cbSize

Size of the **WICRawCapabilitiesInfo** structure.

### CodecMajorVersion

The codec's major version.

### CodecMinorVersion

The codec's minor version.

### ExposureCompensationSupport

[wrc]: WICRawCapabilities

The [WICRawCapabilities][wrc] of exposure compensation support.

### ContrastSupport

The [WICRawCapabilities][wrc] of contrast support.

### RGBWhitePointSupport

The [WICRawCapabilities][wrc] of RGB white point support.

### NamedWhitePointSupport

[wnwp]: WICNamedWhitePoint

The [WICRawCapabilities][wrc] of [WICNamedWhitePoint][wnwp] support.

### NamedWhitePointSupportMask

The [WICNamedWhitePoint][wnwp] mask.

### KelvinWhitePointSupport

The [WICRawCapabilities][wrc] of kelvin white point support.

### GammaSupport

The [WICRawCapabilities][wrc] of gamma support.

### TintSupport

The [WICRawCapabilities][wrc] of tint support.

### SaturationSupport

The [WICRawCapabilities][wrc] of saturation support.

### SharpnessSupport

The [WICRawCapabilities][wrc] of sharpness support.

### NoiseReductionSupport

The [WICRawCapabilities][wrc] of noise reduction support.

### DestinationColorProfileSupport

The [WICRawCapabilities][wrc] of destination color profile support.

### ToneCurveSupport

The [WICRawCapabilities][wrc] of tone curve support.

### RotationSupport

[wrrc]: WICRawRotationCapabilities

The [WICRawRotationCapabilities][wrrc] of rotation support.

### RenderModeSupport

[wrrm]: WICRawRenderMode

The [WICRawCapabilities][wrc] of [WICRawRenderMode][wrrm] support.
