---
layout: interface
category: STRUCTURES
title: WICRawToneCurve
---

Represents a raw image tone curve.

```cpp
typedef struct WICRawToneCurve {
  UINT                 cPoints;
  WICRawToneCurvePoint aPoints[1];
} WICRawToneCurve;
```

## Members

### cPoints

The number of tone curve points.

### aPoints

The array of tone curve points.
