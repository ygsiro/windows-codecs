---
layout: interface
category: FUNCTIONS
title: WICMapSchemaToName
---

Obtains the name associated with a given schema.

```cpp
HRESULT WICMapSchemaToName(
  REFGUID guidMetadataFormat, // [in]
  LPWSTR  pwzSchema,          // [in]
  UINT    cchName,            // [in]
  WCHAR   *wzName,            // [in, out]
  UINT    *pcchActual,        // [out]
);
```

## Parameters

1. *guidMetadataFormat* - The metadata format GUID.
2. *pwzSchema* - The URI string of the schema for which the name is to be retrieved.
3. *cchName* - The size of the *wzName* buffer.
4. *wzName* - A pointer to a buffer that receives the schema's name.
   To obtain the required buffer size, call **WICMapSchemaToName** with cchName set to 0 and *wzName* set to **NULL**.
5. *pcchActual* - The actual buffer size needed to retrieve the entire schema name.

## Return value

If this function succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## Remarks

You can extend the schema name mapping by adding to the following registry key:

```text
HKEY_CLASSES_ROOT
   CLSID
      {FAE3D380-FEA4-4623-8C75-C6B61110B681}
         Schemas
            BB5ACC38-F216-4CEC-A6C5-5F6E739763A9
               ...
```

For more information, see How to Write a WIC-Enabled Codec.
