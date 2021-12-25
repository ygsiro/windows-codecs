---
layout: interface
category: FUNCTIONS
title: WICMapGuidToShortName
---

Obtains the short name associated with a given GUID.

```cpp
HRESULT WICMapGuidToShortName(
  REFGUID guid,       // [in]
  UINT    cchName,    // [in]
  WCHAR   *wzName,    // [in, out]
  UINT    *pcchActual // [out]
);
```

## Parameters

1. *guid* - The GUID to retrieve the short name for.
2. *cchName* - The size of the *wzName* buffer.
3. *wzName* - A pointer that receives the short name associated with the GUID.
4. *pcchActual* - The actual size needed to retrieve the entire short name associated with the GUID.

## Return value

If this function succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## Remarks

Windows Imaging Component (**WIC**) short name mappings can be found within the following registry key:

```text
HKEY_CLASSES_ROOT
   CLSID
      {FAE3D380-FEA4-4623-8C75-C6B61110B681}
         Namespace
            ...
```
