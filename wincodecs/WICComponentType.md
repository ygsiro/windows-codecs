---
layout: interface
category: ENUMERATIONS
title: WICComponentType
---

Specifies the type of Windows Imaging Component (**WIC**) component.

```cpp
typedef enum WICComponentType {
  WICDecoder,
  WICEncoder,
  WICPixelFormatConverter,
  WICMetadataReader,
  WICMetadataWriter,
  WICPixelFormat,
  WICAllComponents,
  WICCOMPONENTTYPE_FORCE_DWORD
} ;
```

## WICDecoder

A WIC decoder.

## WICEncoder

A WIC encoder.

## WICPixelFormatConverter

A WIC pixel converter.

## WICMetadataReader

A WIC metadata reader.

## WICMetadataWriter

A WIC metadata writer.

## WICPixelFormat

A WIC pixel format.

## WICAllComponents

All WIC components.
