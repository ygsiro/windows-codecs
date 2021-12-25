---
layout: interface
category: Interface
title: IWICBitmapCodecProgressNotification
code:
  - key: PFNProgressNotification
TOC:
  - name: Inheritance
  - name: RegisterProgressNotification
---

Exposes methods used for progress notification for encoders and decoders.

## Inheritance

The **IWICBitmapCodecProgressNotification** interface inherits from the IUnknown interface.
**IWICBitmapCodecProgressNotification** also has these types of members:

## RegisterProgressNotification

Registers a progress notification callback function.

```cpp
HRESULT RegisterProgressNotification(
  PFNProgressNotification pfnProgressNotification, // [in]
  LPVOID                  pvData,                  // [in]
  DWORD                   dwProgressFlags          // [in]
);
```

## RegisterProgressNotification - Parameters

1. _pfnProgressNotification_ - A function pointer to the application defined progress notification callback function.
   See [ProgressNotificationCallback][pnc] for the callback signature.
2. _pvData_ - A pointer to component data for the callback method.
3. _dwProgressFlags_ - The [WICProgressOperation][po] and [WICProgressNotification][pn] flags to use for progress notification.

## RegisterProgressNotification - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## RegisterProgressNotification - Remarks

Applications can only register a single callback.
Subsequent registration calls will replace the previously registered callback.
To unregister a callback, pass in **NULL** or register a new callback function.

Progress is reported in an increasing order between 0.0 and 1.0.
If _dwProgressFlags_ includes **WICProgressNotificationBegin**, the callback is guaranteed to be called with progress 0.0.
If _dwProgressFlags_ includes **WICProgressNotificationEnd**, the callback is guaranteed to be called with progress 1.0.

**WICProgressNotificationFrequent** increases the frequency in which the callback is called.
If an operation is expected to take more than 30 seconds, **WICProgressNotificationFrequent** should be added to _dwProgressFlags_.

[pnc]: PFNProgressNotification
[po]: WICProgressOperation
[pn]: WICProgressNotification
