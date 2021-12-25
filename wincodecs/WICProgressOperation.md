---
layout: interface
category: ENUMERATIONS
title: WICProgressOperation
---

Specifies the progress operations to receive notifications for.

```cpp
typedef enum WICProgressOperation {
  WICProgressOperationCopyPixels,
  WICProgressOperationWritePixels,
  WICProgressOperationAll,
  WICPROGRESSOPERATION_FORCE_DWORD
} ;
```

## WICProgressOperationCopyPixels

Receive copy pixel operation.

## WICProgressOperationWritePixels

Receive write pixel operation.

## WICProgressOperationAll

Receive all progress operations available.
