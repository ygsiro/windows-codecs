---
layout: interface
category: Interface
title: IWICEnumMetadataItem
TOC:
  - name: Inheritance
  - name: Clone
  - name: Next
  - name: Reset
  - name: Skip
---

Exposes methods that provide enumeration services for individual metadata items.

## Inheritance

The **IWICEnumMetadataItem** interface inherits from the IUnknown interface.
**IWICEnumMetadataItem** also has these types of members:

- [Clone](#clone)
- [Next](#next)
- [Reset](#reset)
- [Skip](#skip)

## Clone

Creates a copy of the current **IWICEnumMetadataItem**.

```cpp
HRESULT Clone(
   IWICEnumMetadataItem **ppIEnumMetadataItem // [out]
);
```

### Clone - Parameter

1. *ppIEnumMetadataItem* - A pointer that receives a pointer to the **IWICEnumMetadataItem** copy.

### Clone - Return value

If this method succeeds, it returns **S_OK**. Otherwise, it returns an **HRESULT** error code.

## Next

Advanced the current position in the enumeration.

```cpp
HRESULT Next(
   ULONG       celt,         // [in]
   PROPVARIANT *rgeltSchema, // [in, out]
   PROPVARIANT *rgeltId,     // [in, out]
   PROPVARIANT *rgeltValue,  // [in, out, optional]
   ULONG       *pceltFetched // [out, optional]
);
```

### Next - Parameter

1. *celt* - The number of items to be retrieved.
2. *rgeltSchema* - An array of enumerated items.
   This parameter is optional.
3. *rgeltId* - An array of enumerated items.
4. *rgeltValue* - An array of enumerated items.
   This parameter is optional.
5. *pceltFetched* - The number of items that were retrieved.
   This value is always less than or equal to the number of items requested.

### Next - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## Reset

Resets the current position to the beginning of the enumeration.

```cpp
HRESULT Reset();
```

### Reset - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## Skip

Skips to given number of objects.

```cpp
HRESULT Skip(
    ULONG celt // [in]
);
```

### Skip - Parameter

1. *celt* - The number of objects to skip.

### Skip - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.
