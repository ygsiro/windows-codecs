---
layout: interface
category: ENUMERATIONS
title: WICComponentSigning
---

Specifies the component signing status.

```cpp
typedef enum WICComponentSigning {
  WICComponentSigned,
  WICComponentUnsigned,
  WICComponentSafe,
  WICComponentDisabled,
  WICCOMPONENTSIGNING_FORCE_DWORD
} ;
```

## WICComponentSigned

A signed component.

## WICComponentUnsigned

An unsigned component

## WICComponentSafe

A component is safe.

Components that do not have a binary component to sign, such as a pixel format, should return this value.

## WICComponentDisabled

A component has been disabled.
