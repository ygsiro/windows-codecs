---
layout: interface
category: Interface
title: IWICProgressiveLevelControl
TOC:
  - name: Inheritance
  - name: Remarks
  - name: GetCurrentLevel
  - name: GetLevelCount
  - name: SetCurrentLevel
---

Exposes methods for obtaining information about and controlling progressive decoding.

## Inheritance

The **IWICProgressiveLevelControl** interface inherits from the IUnknown interface.
**IWICProgressiveLevelControl** also has these types of members:

- [GetCurrentLevel](#getcurrentlevel)
- [GetLevelCount](#getlevelcount)
- [SetCurrentLevel](#setcurrentlevel)

## Remarks

Images can only be progressively decoded if they were progressively encoded.
Progressive images automatically start at the highest (best quality) progressive level.
The caller must manually set the decoder to a lower progressive level.

**E_NOTIMPL** is returned if the codec does not support progressive level decoding.

## GetCurrentLevel

Gets the decoder's current progressive level.

```cpp
HRESULT GetCurrentLevel(
    UINT *pnLevel // [out, retval]
);
```

### GetCurrentLevel - Parameter

1. *pnLevel* - Indicates the current level specified.

### GetCurrentLevel - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### GetCurrentLevel - Remarks

The level always defaults to the highest progressive level.
In order to decode a lower progressive level, [SetCurrentLevel](#setcurrentlevel) must first be called.

## GetLevelCount

Gets the number of levels of progressive decoding supported by the CODEC.

```cpp
HRESULT GetLevelCount(
    UINT *pcLevels // [out, retval]
);
```

### GetLevelCount - Parameter

1. *pcLevels* - Indicates the number of levels supported by the CODEC.

### GetLevelCount - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### GetLevelCount - Remarks

Users should not use this function to iterate through the progressive levels of a progressive **JPEG** image.
**JPEG** progressive levels are determined by the image and do not have a fixed level count.
Using this method will force the application to wait for all progressive levels to be downloaded before it can return.
Instead, applications should use the following code to iterate through the progressive levels of a progressive **JPEG** image.

## SetCurrentLevel

Specifies the level to retrieve on the next call to CopyPixels.

```cpp
HRESULT SetCurrentLevel(
    UINT nLevel // [in]
);
```

### SetCurrentLevel - Parameter

1. *nLevel* - Specifies which level to return next.
   If greater than the total number of levels supported, an error will be returned.

### SetCurrentLevel - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### SetCurrentLevel - Remarks

A call does not have to request every level supported.
If a caller requests level 1, without having previously requested level 0, the bits returned by the next call to CopyPixels will include both levels.

If the requested level is invalid, the error returned is **WINCODEC_ERR_INVALIDPROGRESSIVELEVEL**.
