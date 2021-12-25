---
layout: interface
category: Interface
title: IWICBitmapCodecInfo
TOC:
  - name: Inheritance
  - name: DoesSupportAnimation
  - name: DoesSupportChromakey
  - name: DoesSupportLossless
  - name: DoesSupportMultiframe
  - name: GetColorManagementVersion
  - name: GetContainerFormat
  - name: GetDeviceManufacturer
  - name: GetDeviceModels
  - name: GetFileExtensions
  - name: GetMimeTypes
  - name: GetPixelFormats
  - name: MatchesMimeType
---

Exposes methods that provide information about a particular codec.

## Inheritance

The **IWICBitmapCodecInfo** interface inherits from [IWICComponentInfo][wci]. **IWICBitmapCodecInfo** also has these types of members:

- [DoesSupportAnimation](#doessupportanimation)
- [DoesSupportChromakey](#doessupportchromakey)
- [DoesSupportLossless](#doessupportlossless)
- [DoesSupportMultiframe](#doessupportmultiframe)
- [GetColorManagementVersion](#getcolormanagementversion)
- [GetContainerFormat](#getcontainerformat)
- [GetDeviceManufacturer](#getdevicemanufacturer)
- [GetDeviceModels](#getdevicemodels)
- [GetFileExtensions](#getfileextensions)
- [GetMimeTypes](#getmimetypes)
- [GetPixelFormats](#getpixelformats)
- [MatchesMimeType](#matchesmimetype)

## DoesSupportAnimation

Retrieves a value indicating whether the codec supports animation.

```cpp
HRESULT DoesSupportAnimation(
  BOOL *pfSupportAnimation // [out]
);
```

### DoesSupportAnimation - Parameters

1. _pfSupportAnimation_ - Receives **TRUE** if the codec supports images with timing information; otherwise, **FALSE**.

### DoesSupportAnimation - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## DoesSupportChromakey

Retrieves a value indicating whether the codec supports chromakeys.

```cpp
HRESULT DoesSupportChromakey(
  BOOL *pfSupportChromakey // [out]
);
```

### DoesSupportChromakey - Parameters

1. _pfSupportChromakey_ - Receives **TRUE** if the codec supports chromakeys; otherwise, **FALSE**.

### DoesSupportChromakey - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## DoesSupportLossless

Retrieves a value indicating whether the codec supports lossless formats.

```cpp
HRESULT DoesSupportLossless(
  BOOL *pfSupportLossless // [out]
);
```

### DoesSupportLossless - Parameters

1. _pfSupportLossless_ - Receives **TRUE** if the codec supports lossless formats; otherwise, **FALSE**.

### DoesSupportLossless - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## DoesSupportMultiframe

Retrieves a value indicating whether the codec supports multi frame images.

```cpp
HRESULT DoesSupportMultiframe(
  BOOL *pfSupportMultiframe // [out]
);
```

### DoesSupportMultiframe - Parameters

1. _pfSupportMultiframe_ - Receives **TRUE** if the codec supports multi frame images; otherwise, **FALSE**.

### DoesSupportMultiframe - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## GetColorManagementVersion

Retrieves the color management version number the codec supports.

```cpp
HRESULT GetColorManagementVersion(
  UINT  cchColorManagementVersion, // [in]
  WCHAR *wzColorManagementVersion, // [in, out]
  UINT  *pcchActual                // [in, out]
);
```

### GetColorManagementVersion - Parameters

1. _cchColorManagementVersion_ - The size of the version buffer.
   Use 0 on first call to determine needed buffer size.
2. _wzColorManagementVersion_ - Receives the color management version number.
   Use **NULL** on first call to determine needed buffer size.
3. _pcchActual_ - The actual buffer size needed to retrieve the full color management version number.

### GetColorManagementVersion - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### GetColorManagementVersion - Remarks

The usage pattern for this method is a two call process.
The first call retrieves the buffer size needed to retrieve the full color management version number by calling it with _cchColorManagementVersion_ set to 0 and _wzColorManagementVersion_ set to **NULL**.
This call sets _pcchActual_ to the buffer size needed.
Once the needed buffer size is determined, a second **GetColorManagementVersion** call with _cchColorManagementVersion_ set to the buffer size and _wzColorManagementVersion_ set to a buffer of the appropriate size will retrieve the pixel formats.

## GetContainerFormat

Retrieves the container GUID associated with the codec.

```cpp
HRESULT GetContainerFormat(
  GUID *pguidContainerFormat // [out]
);
```

### GetContainerFormat - Parameters

1. _pguidContainerFormat_ - Receives the container GUID.

### GetContainerFormat - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## GetDeviceManufacturer

Retrieves the name of the device manufacture associated with the codec.

```cpp
HRESULT GetDeviceManufacturer(
  UINT  cchDeviceManufacturer, // [in]
  WCHAR *wzDeviceManufacturer, // [in, out]
  UINT  *pcchActual            // [out]
);
```

### GetDeviceManufacturer - Parameters

1. _cchDeviceManufacturer_ - The size of the device manufacture's name.
   Use 0 on first call to determine needed buffer size.
2. _wzDeviceManufacturer_ - Receives the device manufacture's name.
   Use **NULL** on first call to determine needed buffer size.
3. _pcchActual_ - The actual buffer size needed to retrieve the device manufacture's name.

### GetDeviceManufacturer - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### GetDeviceManufacturer - Remarks

The usage pattern for this method is a two call process.
The first call retrieves the buffer size needed to retrieve the full color management version number by calling it with _cchDeviceManufacturer_ set to 0 and _wzDeviceManufacturer_ set to **NULL**.
This call sets _pcchActual_ to the buffer size needed.
Once the needed buffer size is determined, a second **GetDeviceManufacturer** call with _cchDeviceManufacturer_ set to the buffer size and _wzDeviceManufacturer_ set to a buffer of the appropriate size will retrieve the pixel formats.

## GetDeviceModels

Retrieves a comma delimited list of device models associated with the codec.

```cpp
HRESULT GetDeviceModels(
  UINT  cchDeviceModels, // [in]
  WCHAR *wzDeviceModels, // [in, out]
  UINT  *pcchActual      // [in, out]
);
```

### GetDeviceModels - Parameters

1. _cchDeviceModels_ - The size of the device models buffer.
   Use 0 on first call to determine needed buffer size.
2. _wzDeviceModels_ - Receives a comma delimited list of device model names associated with the codec.
   Use **NULL** on first call to determine needed buffer size.
3. _pcchActual_ - The actual buffer size needed to retrieve all of the device model names.

### GetDeviceModels - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### GetDeviceModels - Remarks

The usage pattern for this method is a two call process. The first call retrieves the buffer size needed to retrieve the full color management version number by calling it with _cchDeviceModels_ set to 0 and _wzDeviceModels_ set to **NULL**.
This call sets _pcchActual_ to the buffer size needed.
Once the needed buffer size is determined, a second GetDeviceModels call with _cchDeviceModels_ set to the buffer size and _wzDeviceModels_ set to a buffer of the appropriate size will retrieve the pixel formats.

## GetFileExtensions

Retrieves a comma delimited list of the file name extensions associated with the codec.

```cpp
HRESULT GetFileExtensions(
  UINT  cchFileExtensions, // [in]
  WCHAR *wzFileExtensions, // [in, out]
  UINT  *pcchActual        // [in, out]
);
```

### GetFileExtensions - Parameters

1. _cchFileExtensions_ - The size of the file name extension buffer.
   Use 0 on first call to determine needed buffer size.
2. _wzFileExtensions_ - Receives a comma delimited list of file name extensions associated with the codec.
   Use **NULL** on first call to determine needed buffer size.
3. _pcchActual_ - The actual buffer size needed to retrieve all file name extensions associated with the codec.

### GetFileExtensions - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### GetFileExtensions - Remarks

The default extension for an image encoder is the first item in the list of returned extensions.

The usage pattern for this method is a two call process.
The first call retrieves the buffer size needed to retrieve the full color management version number by calling it with _cchFileExtensions_ set to 0 and _wzFileExtensions_ set to **NULL**.
This call sets _pcchActual_ to the buffer size needed.
Once the needed buffer size is determined, a second **GetFileExtensions** call with _cchFileExtensions_ set to the buffer size and _wzFileExtensions_ set to a buffer of the appropriate size will retrieve the pixel formats.

## GetMimeTypes

Retrieves a comma delimited sequence of mime types associated with the codec.

```cpp
HRESULT GetMimeTypes(
  UINT  cchMimeTypes, // [in]
  WCHAR *wzMimeTypes, // [out]
  UINT  *pcchActual   // [out]
);
```

### GetMimeTypes - Parameters

1. _cchMimeTypes_ - The size of the mime types buffer.
   Use 0 on first call to determine needed buffer size.
2. _wzMimeTypes_ - Receives the mime types associated with the codec.
   Use **NULL** on first call to determine needed buffer size.
3. _pcchActual_ - The actual buffer size needed to retrieve all mime types associated with the codec.

### GetMimeTypes - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### GetMimeTypes - Remarks

The usage pattern for this method is a two call process.
The first call retrieves the buffer size needed to retrieve the full color management version number by calling it with _cchMimeTypes_ set to 0 and _wzMimeTypes_ set to NULL.
This call sets _pcchActual_ to the buffer size needed.
Once the needed buffer size is determined, a second **GetMimeTypes** call with _cchMimeTypes_ set to the buffer size and _wzMimeTypes_ set to a buffer of the appropriate size will retrieve the pixel formats.

## GetPixelFormats

Retrieves the pixel formats the codec supports.

```cpp
HRESULT GetPixelFormats(
  UINT cFormats,           // [in]
  GUID *pguidPixelFormats, // [in, out]
  UINT *pcActual           // [out]
);
```

### GetPixelFormats - Parameters

1. _cFormats_ - The size of the pguidPixelFormats array.
   Use 0 on first call to determine the needed array size.
2. _pguidPixelFormats_ - Receives the supported pixel formats.
   Use NULL on first call to determine needed array size.
3. _pcActual_ - The array size needed to retrieve all supported pixel formats.

### GetPixelFormats - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### GetPixelFormats - Remarks

The usage pattern for this method is a two call process.
The first call retrieves the array size needed to retrieve all the supported pixel formats by calling it with cFormats set to 0 and _pguidPixelFormats_ set to **NULL**.
This call sets _pcActual_ to the array size needed.
Once the needed array size is determined, a second **GetPixelFormats** call with _pguidPixelFormats_ set to an array of the appropriate size will retrieve the pixel formats.

## MatchesMimeType

Retrieves a value indicating whether the given mime type matches the mime type of the codec.

```cpp
HRESULT MatchesMimeType(
  LPCWSTR wzMimeType, // [in]
  BOOL    *pfMatches  // [out]
);
```

### MatchesMimeType - Parameters

1. _wzMimeType_ - The mime type to compare.
2. _pfMatches_ - Receives **TRUE** if the mime types match; otherwise, **FALSE**.

### MatchesMimeType - Return value

This method can return one of these values.

| Return code   | Description                               |
| :------------ | :---------------------------------------- |
| **S_OK**      | The operation was successful.             |
| **E_NOTIMPL** | The codec does not implement this method. |

### MatchesMimeType - Remarks

**Note:** The Windows provided codecs do not implement this method and return **E_NOTIMPL**.

[wci]: IWICComponentInfo
