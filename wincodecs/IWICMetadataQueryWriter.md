---
layout: interface
category: Interface
title: IWICMetadataQueryWriter
TOC:
  - name: Inheritance
  - name: Remarks
  - name: RemoveMetadataByName
  - name: SetMetadataByName
---

Exposes methods for setting or removing metadata blocks and items to an encoder or its image frames using a metadata query expression.

## Inheritance

[wmqr]: IWICMetadataQueryReader

The **IWICMetadataQueryWriter** interface inherits from [IWICMetadataQueryReader][wmqr].
**IWICMetadataQueryWriter** also has these types of members:

- [Remarks](#remarks)
- [RemoveMetadataByName](#removemetadatabyname)
- [SetMetadataByName](#setmetadatabyname)

## Remarks

A metadata query writer uses metadata query expressions to set or remove metadata. For more information on the metadata query language, see the Metadata Query Language Overview.

## RemoveMetadataByName

Removes a metadata item from a specific location using a metadata query expression.

```cpp
HRESULT RemoveMetadataByName(
    LPCWSTR wzName // [in]
);
```

### RemoveMetadataByName - Parameter

1. *wzName* - The name of the metadata item to remove.

### RemoveMetadataByName - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### RemoveMetadataByName - Remarks

**RemoveMetadataByName** uses metadata query expressions to remove metadata.
For more information on the metadata query language, see the Metadata Query Language Overview.

If the metadata item is a metadata block, it is removed from the metadata hierarchy.

## SetMetadataByName

Sets a metadata item to a specific location.

```cpp
HRESULT SetMetadataByName(
    LPCWSTR           wzName,    // [in]
    const PROPVARIANT *pvarValue // [in]
);
```

### SetMetadataByName - Parameter

1. *wzName* - The name of the metadata item.
2. *pvarValue* - The metadata to set.

### SetMetadataByName - Return value

If this method succeeds, it returns **S_OK**.
 Otherwise, it returns an **HRESULT** error code.

### SetMetadataByName - Remarks

**SetMetadataByName** uses metadata query expressions to remove metadata.
For more information on the metadata query language, see the Metadata Query Language Overview.

If the value set is a nested metadata block then use variant type **VT_UNKNOWN** and *pvarValue* pointing to the **IWICMetadataQueryWriter** of the new metadata block.
The ordering of metadata items is at the discretion of the query writer since relative locations are not specified.
