---
layout: interface
category: ENUMERATIONS
title: WICBitmapInterpolationMode
---

Specifies the sampling or filtering mode to use when scaling an image.

```cpp
typedef enum WICBitmapInterpolationMode {
  WICBitmapInterpolationModeNearestNeighbor,
  WICBitmapInterpolationModeLinear,
  WICBitmapInterpolationModeCubic,
  WICBitmapInterpolationModeFant,
  WICBitmapInterpolationModeHighQualityCubic,
  WICBITMAPINTERPOLATIONMODE_FORCE_DWORD
};
```

## WICBitmapInterpolationModeNearestNeighbor

A nearest neighbor interpolation algorithm.
Also known as nearest pixel or point interpolation.

The output pixel is assigned the value of the pixel that the point falls within.
No other pixels are considered.

## WICBitmapInterpolationModeLinear

A bilinear interpolation algorithm.

The output pixel values are computed as a weighted average of the nearest four pixels in a 2x2 grid.

## WICBitmapInterpolationModeCubic

A bicubic interpolation algorithm.

Destination pixel values are computed as a weighted average of the nearest sixteen pixels in a 4x4 grid.

## WICBitmapInterpolationModeFant

A Fant resampling algorithm.

Destination pixel values are computed as a weighted average of the all the pixels that map to the new pixel.

## WICBitmapInterpolationModeHighQualityCubic

A high quality bicubic interpolation algorithm. Destination pixel values are computed using a much denser sampling
kernel than regular cubic.
The kernel is resized in response to the scale factor, making it suitable for downscaling by factors greater than 2.

> **Note** This value is supported beginning with Windows 10.
