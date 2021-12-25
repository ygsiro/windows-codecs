---
layout: interface
category: ENUMERATIONS
title: WICJpegIndexingOptions
---

Specifies the options for indexing a JPEG image.

```cpp
typedef enum WICJpegIndexingOptions {
  WICJpegIndexingOptionsGenerateOnDemand,
  WICJpegIndexingOptionsGenerateOnLoad,
  WICJpegIndexingOptions_FORCE_DWORD
} ;
```

## WICJpegIndexingOptionsGenerateOnDemand

[wbs]: IWICBitmapSource
[wbs-cp]: IWICBitmapSource#copypixels

Index generation is deferred until [IWICBitmapSource][wbs]::[CopyPixels][wbs-cp] is called on the image.

## WICJpegIndexingOptionsGenerateOnLoad

Index generation is performed when the when the image is initially loaded.
