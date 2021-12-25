---
layout: interface
category: ENUMERATIONS
title: WICProgressNotification
---

Specifies when the progress notification callback should be called.

```cpp
typedef enum WICProgressNotification {
  WICProgressNotificationBegin,
  WICProgressNotificationEnd,
  WICProgressNotificationFrequent,
  WICProgressNotificationAll,
  WICPROGRESSNOTIFICATION_FORCE_DWORD
} ;
```

## WICProgressNotificationBegin

The callback should be called when codec operations begin.

## WICProgressNotificationEnd

The callback should be called when codec operations end.

## WICProgressNotificationFrequent

The callback should be called frequently to report status.

## WICProgressNotificationAll

The callback should be called on all available progress notifications.
