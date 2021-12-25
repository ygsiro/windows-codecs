---
layout: interface
category: ENUMERATIONS
title: WICColorContextType
---

Specifies the color context types.

```cpp
typedef enum WICColorContextType {
  WICColorContextUninitialized,
  WICColorContextProfile,
  WICColorContextExifColorSpace
} ;
```

## WICColorContextUninitialized

An uninitialized color context.

## WICColorContextProfile

A color context that is a full ICC color profile.

## WICColorContextExifColorSpace

A color context that is one of a number of set color spaces (sRGB, AdobeRGB) that are defined in the EXIF specification.
