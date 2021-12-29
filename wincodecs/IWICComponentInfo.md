---
layout: interface
category: Interface
title: IWICComponentInfo
TOC:
  - name: Inheritance
  - name: GetAuthor
  - name: GetCLSID
  - name: GetComponentType
  - name: GetFriendlyName
  - name: GetSigningStatus
  - name: GetSpecVersion
  - name: GetVendorGUID
  - name: GetVersion
  - name: Related
code:
  - key: WICComponentType
---

Exposes methods that provide component information.

## Inheritance

The **IWICComponentInfo** interface inherits from the IUnknown interface.
**IWICComponentInfo** also has these types of members:

- [GetAuthor](#getauthor)
- [GetCLSID](#getclsid)
- [GetComponentType](#getcomponenttype)
- [GetFriendlyName](#getfriendlyname)
- [GetSigningStatus](#getsigningstatus)
- [GetSpecVersion](#getspecversion)
- [GetVendorGUID](#getvendorguid)
- [GetVersion](#getversion)

## GetAuthor

Retrieves the name of component's author.

```cpp
HRESULT GetAuthor(
   UINT  cchAuthor,  // [in]
   WCHAR *wzAuthor,  // [in, out]
   UINT  *pcchActual // [out]
);
```

### GetAuthor - Parameter

1. *cchAuthor* - The size of the wzAuthor buffer.
2. *wzAuthor* - A pointer that receives the name of the component's author.
   The locale of the string depends on the value that the codec wrote to the registry at install time.
   For built-in components, these strings are always in English.
3. *pcchActual* - A pointer that receives the actual length of the component's authors name.
   The author name is optional; if an author name is not specified by the component, the length returned is 0.

### GetAuthor - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### GetAuthor - Remarks

If *cchAuthor* is 0 and wzAuthor is **NULL**, the required buffer size is returned in pccchActual.

## GetCLSID

Retrieves the component's class identifier (**CLSID**)

```cpp
HRESULT GetCLSID(
   CLSID *pclsid // [out]
);
```

### GetCLSID - Parameter

1. *pclsid* - A pointer that receives the component's CLSID.

### GetCLSID - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### GetCLSID - Remarks

## GetComponentType

[wct]: WICComponentType

Retrieves the component's [WICComponentType][wct].

```cpp
HRESULT GetComponentType(
   WICComponentType *pType // [out]
);
```

### GetComponentType - Parameter

A pointer that receives the [WICComponentType][wct].

### GetComponentType - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## GetFriendlyName

Retrieves the component's friendly name, which is a human-readable display name for the component.

```cpp
HRESULT GetFriendlyName(
   UINT  cchFriendlyName, // [in]
   WCHAR *wzFriendlyName, // [in, out]
   UINT  *pcchActual      // [out]
);
```

### GetFriendlyName - Parameter

1. *cchFriendlyName* - The size of the *wzFriendlyName* buffer.
2. *wzFriendlyName* - A pointer that receives the friendly name of the componen
   The locale of the string depends on the value that the codec wrote to the registry at install time.
   For built-in components, these strings are always in English.
3. *pcchActual* - A pointer that receives the actual length of the component's friendly name.

### GetFriendlyName - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### GetFriendlyName - Remarks

If *cchFriendlyName* is 0 and *wzFriendlyName* is **NULL**, the required buffer size is returned in *pccchActual*.

## GetSigningStatus

Retrieves the signing status of the component.

```cpp
HRESULT GetSigningStatus(
   DWORD *pStatus // [out]
);
```

### GetSigningStatus - Parameter

[wcs]: WICComponentSigning

1. *pStatus* - A pointer that receives the [WICComponentSigning][wcs] status of the component.

### GetSigningStatus - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### GetSigningStatus - Remarks

Signing is unused by WIC. Therefore, all components [WICComponentSigned][wcs].

This function can be used to determine whether a component has no binary component or has been added to the disabled components list in the registry.

## GetSpecVersion

Retrieves the component's specification version.

```cpp
HRESULT GetSpecVersion(
   UINT  cchSpecVersion, // [in]
   WCHAR *wzSpecVersion, // [in, out]
   UINT  *pcchActual     // [out]
);
```

### GetSpecVersion - Parameter

1. *cchSpecVersion* - The size of the *wzSpecVersion* buffer.
2. *wzSpecVersion* - When this method returns, contain a culture invariant string of the component's specification version. The version form is NN.NN.NN.NN.
3. *pcchActual* - A pointer that receives the actual length of the component's specification version.
   The specification version is optional; if a value is not specified by the component, the length returned is 0.

### GetSpecVersion - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### GetSpecVersion - Remarks

All built-in components return "1.0.0.0", except for pixel formats, which do not have a spec version.

If *cchAuthor* is 0 and *wzAuthor* is NULL, the required buffer size is returned in *pccchActual*.

## GetVendorGUID

Retrieves the vendor GUID.

```cpp
HRESULT GetVendorGUID(
   GUID *pguidVendor // [out]
);
```

### GetVendorGUID - Parameter

1. *pguidVendor* - A pointer that receives the component's vendor GUID.

### GetVendorGUID - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## GetVersion

Retrieves the component's version.

```cpp
HRESULT GetVersion(
   UINT  cchVersion, // [in]
   WCHAR *wzVersion, // [in, out]
   UINT  *pcchActual // [out]
);
```

### GetVersion - Parameter

1. *cchVersion* - The size of the *wzVersion* buffer.
2. *wzVersion* - A pointer that receives a culture invariant string of the component's version.
3. *pcchActual* - A pointer that receives the actual length of the component's version.
   The version is optional; if a value is not specified by the component, the length returned is 0.

### GetVersion - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### GetVersion - Remarks

All built-in components return "1.0.0.0", except for pixel formats, which do not have a version.

If *cchAuthor* is 0 and *wzAuthor* is NULL, the required buffer size is returned in *pccchActual*.

## Related

- [IWICImagingFactory::CreateComponentInfo](IWICImagingFactory#createcomponentinfo)
