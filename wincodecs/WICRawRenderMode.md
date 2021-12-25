---
layout: interface
category: ENUMERATIONS
title: WICRawRenderMode
---

Specifies the render intent of the next CopyPixels call.

```cpp
typedef enum WICRawRenderMode {
  WICRawRenderModeDraft,
  WICRawRenderModeNormal,
  WICRawRenderModeBestQuality,
  WICRAWRENDERMODE_FORCE_DWORD
};
```

## WICRawRenderModeDraft

Use speed priority mode.

## WICRawRenderModeNormal

Use normal priority mode. Balance of speed and quality.

## WICRawRenderModeBestQuality

Use best quality mode.
