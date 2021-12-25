---
layout: interface
category: ENUMERATIONS
title: WICJpegTransferMatrix
---

Specifies conversion matrix from `Y'Cb'Cr'` to `R'G'B'`.

```cpp
typedef enum WICJpegTransferMatrix {
  WICJpegTransferMatrixIdentity,
  WICJpegTransferMatrixBT601,
  WICJpegTransferMatrix_FORCE_DWORD
} ;
```

## WICJpegTransferMatrixIdentity

Specifies the identity transfer matrix.

## WICJpegTransferMatrixBT601

Specifies the BT601 transfer matrix.
