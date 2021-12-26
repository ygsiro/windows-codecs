---
layout: interface
category: ENUMERATIONS
title: WICPixelFormatNumericRepresentation
---

Defines constants that specify a primitive type for numeric representation of a WIC pixel format.

```cpp
typedef enum WICPixelFormatNumericRepresentation {
  WICPixelFormatNumericRepresentationUnspecified,
  WICPixelFormatNumericRepresentationIndexed,
  WICPixelFormatNumericRepresentationUnsignedInteger,
  WICPixelFormatNumericRepresentationSignedInteger,
  WICPixelFormatNumericRepresentationFixed,
  WICPixelFormatNumericRepresentationFloat,
  WICPixelFormatNumericRepresentation_FORCE_DWORD
} ;
```

## WICPixelFormatNumericRepresentationUnspecified

The format is not specified.

## WICPixelFormatNumericRepresentationIndexed

Specifies that the format is indexed.

## WICPixelFormatNumericRepresentationUnsignedInteger

Specifies that the format is represented as an unsigned integer.

## WICPixelFormatNumericRepresentationSignedInteger

Specifies that the format is represented as a signed integer.

## WICPixelFormatNumericRepresentationFixed

Specifies that the format is represented as a fixed-point number.

## WICPixelFormatNumericRepresentationFloat

Specifies that the format is represented as a floating-point number.

## Related

- [IWICPixelFormatInfo2::GetNumericRepresentation](IWICPixelFormatInfo2#getnumericrepresentation)
