---
layout: interface
category: Interface
title: IWICDevelopRawNotificationCallback
TOC:
  - name: Inheritance
  - name: Notify
---

Exposes a callback method for raw image change nofications.

## Inheritance

The **IWICDevelopRawNotificationCallback** interface inherits from the IUnknown interface.
**IWICDevelopRawNotificationCallback** also has these types of members:

- [Notify](#notify)

## Notify

An application-defined callback method used for raw image parameter change notifications.

```cpp
HRESULT Notify(
   UINT NotificationMask // [in]
);
```

### Notify - Parameter

1. *NotificationMask* - A set of **IWICDevelopRawNotificationCallback** Constants parameter notification flags.

### Notify - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.
