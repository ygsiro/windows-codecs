---
layout: interface
category: ENUMERATIONS
title: WIC8BIMIptcProperties
---

Specifies the identifiers of the metadata items in an 8BIM IPTC block.

```cpp
typedef enum WIC8BIMIptcProperties {
  WIC8BIMIptcPString,
  WIC8BIMIptcEmbeddedIPTC,
  WIC8BIMIptcProperties_FORCE_DWORD
} ;
```

## WIC8BIMIptcPString

A name that identifies the 8BIM block.

## WIC8BIMIptcEmbeddedIPTC

The embedded IPTC digest value.
