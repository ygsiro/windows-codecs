---
layout: interface
category: ENUMERATIONS
title: WICBitmapTransformOptions
---

Specifies the flip and rotation transforms.

```cpp
typedef enum WICBitmapTransformOptions {
  WICBitmapTransformRotate0,
  WICBitmapTransformRotate90,
  WICBitmapTransformRotate180,
  WICBitmapTransformRotate270,
  WICBitmapTransformFlipHorizontal,
  WICBitmapTransformFlipVertical,
  WICBITMAPTRANSFORMOPTIONS_FORCE_DWORD
} ;
```

## WICBitmapTransformRotate0

A rotation of 0 degrees.

## WICBitmapTransformRotate90

A rotation of 90 degrees.

## WICBitmapTransformRotate180

A rotation of 180 degrees.

## WICBitmapTransformRotate270

A rotation of 270 degrees.

## WICBitmapTransformFlipHorizontal

A horizontal flip.
Pixels are flipped around the vertical y-axis.

## WICBitmapTransformFlipVertical

A vertical flip.
Pixels are flipped around the vertical x-axis.
