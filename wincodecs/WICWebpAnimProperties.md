---
layout: interface
category: ENUMERATIONS
title: WICWebpAnimProperties
---

Specifies the animation properties of a WebP image.

```cpp
typedef enum WICWebpAnimProperties {
  WICWebpAnimLoopCount,
  WICWebpAnimProperties_FORCE_DWORD
} ;
```

## WICWebpAnimLoopCount

The number of times the animation loops.
A value of 0 indicates that the animation will loop infinitely.
