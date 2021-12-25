---
layout: interface
category: ENUMERATIONS
title: WIC8BIMIptcDigestProperties
---

Specifies the identifiers of the metadata items in an 8BIM IPTC digest metadata block.

```cpp
typedef enum WIC8BIMIptcDigestProperties {
  WIC8BIMIptcDigestPString,
  WIC8BIMIptcDigestIptcDigest,
  WIC8BIMIptcDigestProperties_FORCE_DWORD
};
```

## Constants

### WIC8BIMIptcDigestPString

A name that identifies the 8BIM block.

### WIC8BIMIptcDigestIptcDigest

The embedded IPTC digest value.
