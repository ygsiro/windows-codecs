---
layout: interface
category: CALLBACK FUNCTIONS
title: WICMapShortNameToGuid
---

Obtains the GUID associated with the given short name.

```cpp
HRESULT WICMapShortNameToGuid(
  PCWSTR wzName, // [in]
  GUID   *pguid  // [out]
);
```

## Parameters

1. wzName - A pointer to the short name.
2. pguid - A pointer that receives the GUID associated with the given short name.

## Return value

If this function succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## Remarks

You can extend the short name mapping by adding to the following registry key:

```text
HKEY_CLASSES_ROOT
   CLSID
      {FAE3D380-FEA4-4623-8C75-C6B61110B681}
         Namespace
            ...
```

For more information, see How to Write a WIC-Enabled Codec.
