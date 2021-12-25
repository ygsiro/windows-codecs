---
layout: interface
category: ENUMERATIONS
title: WICComponentEnumerateOptions
---

Specifies component enumeration options.

```cpp
typedef enum WICComponentEnumerateOptions {
  WICComponentEnumerateDefault,
  WICComponentEnumerateRefresh,
  WICComponentEnumerateDisabled,
  WICComponentEnumerateUnsigned,
  WICComponentEnumerateBuiltInOnly,
  WICCOMPONENTENUMERATEOPTIONS_FORCE_DWORD
} ;
```

## WICComponentEnumerateDefault

Enumerate any components that are not disabled. Because this value is 0x0, it is always included with the other options.

## WICComponentEnumerateRefresh

Force a read of the registry before enumerating components.

## WICComponentEnumerateDisabled

Include disabled components in the enumeration.
The set of disabled components is disjoint with the set of default enumerated components

## WICComponentEnumerateUnsigned

Include unsigned components in the enumeration.
This option has no effect.

## WICComponentEnumerateBuiltInOnly

At the end of component enumeration, filter out any components that are not Windows provided.
