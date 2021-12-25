---
layout: interface
category: ENUMERATIONS
title: WICBitmapDitherType
---

Specifies the type of dither algorithm to apply when converting between image formats.

```cpp
typedef enum WICBitmapDitherType {
  WICBitmapDitherTypeNone,
  WICBitmapDitherTypeSolid,
  WICBitmapDitherTypeOrdered4x4,
  WICBitmapDitherTypeOrdered8x8,
  WICBitmapDitherTypeOrdered16x16,
  WICBitmapDitherTypeSpiral4x4,
  WICBitmapDitherTypeSpiral8x8,
  WICBitmapDitherTypeDualSpiral4x4,
  WICBitmapDitherTypeDualSpiral8x8,
  WICBitmapDitherTypeErrorDiffusion,
  WICBITMAPDITHERTYPE_FORCE_DWORD
} ;
```

## WICBitmapDitherTypeNone

A solid color algorithm without dither.

## WICBitmapDitherTypeSolid

A solid color algorithm without dither.

## WICBitmapDitherTypeOrdered4x4

A 4x4 ordered dither algorithm.

## WICBitmapDitherTypeOrdered8x8

An 8x8 ordered dither algorithm.

## WICBitmapDitherTypeOrdered16x16

A 16x16 ordered dither algorithm.

## WICBitmapDitherTypeSpiral4x4

A 4x4 spiral dither algorithm.

## WICBitmapDitherTypeSpiral8x8

An 8x8 spiral dither algorithm.

## WICBitmapDitherTypeDualSpiral4x4

A 4x4 dual spiral dither algorithm.

## WICBitmapDitherTypeDualSpiral8x8

An 8x8 dual spiral dither algorithm.

## WICBitmapDitherTypeErrorDiffusion

An error diffusion algorithm.
