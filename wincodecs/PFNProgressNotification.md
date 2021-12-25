---
layout: interface
category: Callbackfunctions
title: PFNProgressNotification
code:
  - key: WICProgressOperation
---

Application defined callback function called when codec component progress is made.

```cpp
PFNProgressNotification Pfnprogressnotification;

HRESULT Pfnprogressnotification(
  LPVOID pvData,
  ULONG uFrameNum,
  WICProgressOperation operation,
  double dblProgress
)
{...}
```

## Parameters

1. *pvData* - Component data passed to the callback function.
2. *uFrameNum* - The current frame number.
3. *operation* - The current operation the component is in.
4. *dblProgress* - The progress value.
   The range is 0.0 to 1.0.

## Return value

If this callback function succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## Remarks

An operation can be canceled by returning **WINCODEC_ERR_ABORTED**.

To register your callback function, query the encoder or decoder for the [IWICBitmapCodecProgressNotification][wbcpn] interface and call [RegisterProgressNotification][wbcpn-rpn].

[wbcpn]: IWICBitmapCodecProgressNotification
[wbcpn-rpn]: IWICBitmapCodecProgressNotification#registerprogressnotification
