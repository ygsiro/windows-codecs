---
layout: interface
category: Interface
title: IWICProgressCallback
TOC:
  - name: Inheritance
  - name: Notify
code:
  - key: WICProgressOperation
---

**IWICProgressCallback** interface is documented only for compliance;
its use is not recommended and may be altered or unavailable in the future.
Instead, and use RegisterProgressNotification.

## Inheritance

The **IWICProgressCallback** interface inherits from the IUnknown interface.
**IWICProgressCallback** also has these types of members:

- [Notify](#notify)

## Notify

Notify method is documented only for compliance;
its use is not recommended and may be altered or unavailable in the future.
Instead, and use RegisterProgressNotification.

```cpp
HRESULT Notify(
    ULONG                uFrameNum,  // [in]
    WICProgressOperation operation,  // [in]
    double               dblProgress // [in]
);
```

### Notify - Parameter

1. *uFrameNum* - The current frame number.
2. *operation* - The operation on which progress is being reported.
3. *dblProgress* - The progress value ranging from is 0.0 to 1.0. 0.0 indicates the beginning of the operation.
   1.0 indicates the end of the operation.

### Notify - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.
