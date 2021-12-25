---
layout: interface
category: Interface
title: IWICMetadataQueryReader
TOC:
  - name: Inheritance
  - name: Remarks
  - name: GetContainerFormat
  - name: GetEnumerator
  - name: GetLocation
  - name: GetMetadataByName
---

Exposes methods for retrieving metadata blocks and items from a decoder or its image frames using a metadata query expression.

## Inheritance

The **IWICMetadataQueryReader** interface inherits from the IUnknown interface.
**IWICMetadataQueryReader** also has these types of members:

- [GetContainerFormat](#getcontainerformat)
- [GetEnumerator](#getenumerator)
- [GetLocation](#getlocation)
- [GetMetadataByName](#getmetadatabyname)

## Remarks

A metadata query reader uses metadata query expressions to access embedded metadata.
For more information on the metadata query language, see the Metadata Query Language Overview.

The benefit of the query reader is the ability to access a metadata item in a single step.

[wmbr]: IWICMetadataBlockReader
[wmr]: IWICMetadataReader

The query reader also provides the way to traverse the whole set of metadata hierarchy with the help of the GetEnumerator method.
However, it is not recommended to use this method since [IWICMetadataBlockReader][wmbr] and [IWICMetadataReader][wmr] provide a more convenient and cheaper way.

## GetContainerFormat

Gets the metadata query readers container format.

```cpp
HRESULT GetContainerFormat(
    GUID *pguidContainerFormat // [out]
);
```

### GetContainerFormat - Parameter

1. *pguidContainerFormat* - Pointer that receives the cointainer format GUID.

### GetContainerFormat - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## GetEnumerator

Gets an enumerator of all metadata items at the current relative location within the metadata hierarchy.

```cpp
HRESULT GetEnumerator(
    IEnumString **ppIEnumString // [out]
);
```

### GetEnumerator - Parameter

1. *ppIEnumString* - A pointer to a variable that receives a pointer to the IEnumString interface for the enumerator that contains query strings that can be used in the current **IWICMetadataQueryReader**.

### GetEnumerator - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### GetEnumerator - Remarks

The retrieved enumerator only contains query strings for the metadata blocks and items in the current level of the hierarchy.

## GetLocation

Retrieves the current path relative to the root metadata block.

```cpp
HRESULT GetLocation(
    UINT  cchMaxLength,     // [in]
    WCHAR *wzNamespace,     // [in, out]
    UINT  *pcchActualLength // [out]
);
```

### GetLocation - Parameter

1. *cchMaxLength* - The length of the *wzNamespace* buffer.
2. *wzNamespace* - Pointer that receives the current namespace location.
3. *pcchActualLength* - The actual buffer length that was needed to retrieve the current namespace location.

### GetLocation - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### GetLocation - Remarks

If you pass **NULL** to *wzNamespace*, GetLocation ignores *cchMaxLength* and returns the required buffer length to store the path in the variable that *pcchActualLength* points to.

If the query reader is relative to the top of the metadata hierarchy, it will return a single-char string.

If the query reader is relative to a nested metadata block, this method will return the path to the current query reader.

## GetMetadataByName

Retrieves the metadata block or item identified by a metadata query expression.

```cpp
HRESULT GetMetadataByName(
    LPCWSTR     wzName,    // [in]
    PROPVARIANT *pvarValue // [in, out]
);
```

### GetMetadataByName - Parameter

1. *wzName* - The query expression to the requested metadata block or item.
2. *pvarValue* - When this method returns, contains the metadata block or item requested.

### GetMetadataByName - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### GetMetadataByName - Remarks

**GetMetadataByName** uses metadata query expressions to access embedded metadata.
For more information on the metadata query language, see the Metadata Query Language Overview.

If multiple blocks or items exist that are expressed by the same query expression, the first metadata block or item found will be returned.
