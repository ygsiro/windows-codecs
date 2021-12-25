---
layout: interface
category: ENUMERATIONS
title: WICSectionAccessLevel
---

Specifies the access level of a Windows Graphics Device Interface (**GDI**) section.

```cpp
typedef enum WICSectionAccessLevel {
  WICSectionAccessLevelRead,
  WICSectionAccessLevelReadWrite,
  WICSectionAccessLevel_FORCE_DWORD
} ;
```

## WICSectionAccessLevelRead

Indicates a read only access level.

## WICSectionAccessLevelReadWrite

Indicates a read/write access level.
