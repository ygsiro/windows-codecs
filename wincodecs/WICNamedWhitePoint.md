---
layout: interface
category: ENUMERATIONS
title: WICNamedWhitePoint
---

Specifies named white balances for raw images.

```cpp
typedef enum WICNamedWhitePoint {
  WICWhitePointDefault,
  WICWhitePointDaylight,
  WICWhitePointCloudy,
  WICWhitePointShade,
  WICWhitePointTungsten,
  WICWhitePointFluorescent,
  WICWhitePointFlash,
  WICWhitePointUnderwater,
  WICWhitePointCustom,
  WICWhitePointAutoWhiteBalance,
  WICWhitePointAsShot,
  WICNAMEDWHITEPOINT_FORCE_DWORD
};
```

## WICWhitePointDefault

The default white balance.

## WICWhitePointDaylight

A daylight white balance.

## WICWhitePointCloudy

A daylight white balance.

## WICWhitePointShade

A shade white balance.

## WICWhitePointTungsten

A tungsten white balance.

## WICWhitePointFluorescent

A fluorescent white balance.

## WICWhitePointFlash

Daylight white balance.

## WICWhitePointUnderwater

A flash white balance.

## WICWhitePointCustom

A custom white balance. This is typically used when using a picture (grey-card) as white balance.

## WICWhitePointAutoWhiteBalance

An automatic balance.

## WICWhitePointAsShot

An "as shot" white balance.
