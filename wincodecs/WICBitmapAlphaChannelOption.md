---
layout: interface
category: ENUMERATIONS
title: WICBitmapAlphaChannelOption
---

Specifies the desired alpha channel usage.

```cpp
typedef enum WICBitmapAlphaChannelOption {
  WICBitmapUseAlpha,
  WICBitmapUsePremultipliedAlpha,
  WICBitmapIgnoreAlpha,
  WICBITMAPALPHACHANNELOPTIONS_FORCE_DWORD
} ;
```

## WICBitmapUseAlpha

Use alpha channel.

## WICBitmapUsePremultipliedAlpha

Use a pre-multiplied alpha channel.

## WICBitmapIgnoreAlpha

Sentinel value.
