---
layout: interface
category: Interface
title: IWICColorContext
TOC:
  - name: Inheritance
  - name: Remarks
  - name: GetExifColorSpace
  - name: GetProfileBytes
  - name: GetType
  - name: InitializeFromExifColorSpace
  - name: InitializeFromFilename
  - name: InitializeFromMemory
  - name: Related
code:
  - key: WICColorContextType
---

Exposes methods for color management.

## Inheritance

The **IWICColorContext** interface inherits from the IUnknown interface.
**IWICColorContext** also has these types of members:

- [GetExifColorSpace](#getexifcolorspace)
- [GetProfileBytes](#getprofilebytes)
- [GetType](#gettype)
- [InitializeFromExifColorSpace](#initializefromexifcolorspace)
- [InitializeFromFilename](#initializefromfilename)
- [InitializeFromMemory](#initializefrommemory)

## Remarks

A Color Context is an abstraction for a color profile. The profile can either be loaded from a file (like "sRGB Color Space Profile.icm"), read from a memory buffer, or can be defined by an EXIF color space. The system color profile directory can be obtained by calling GetColorDirectoryW.

Once a color context has been initialized, it cannot be re-initialized.

## GetExifColorSpace

Retrieves the Exchangeable Image File (**EXIF**) color space color context.

```cpp
HRESULT GetExifColorSpace(
   UINT *pValue // [out]
);
```

### GetExifColorSpace - Parameter

1. _pValue_ - A pointer that receives the EXIF color space color context.

   | Value           | Meaning                   |
   | :-------------- | :------------------------ |
   | 1               | A sRGB color space.       |
   | 2               | An Adobe RGB color space. |
   | 3 through 65534 | Unused.                   |

### GetExifColorSpace - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### GetExifColorSpace - Remarks

This method should only be used when **IWICColorContext**::[GetType](#gettype) indicates [WICColorContextExifColorSpace][wccecs].

[wccecs]: WICColorContextType

## GetProfileBytes

Retrieves the color context profile.

```cpp
HRESULT GetProfileBytes(
   UINT cbBuffer,  // [in]
   BYTE *pbBuffer, // [in, out]
   UINT *pcbActual // [out]
);
```

### GetProfileBytes - Parameter

1. _cbBuffer_ - The size of the pbBuffer buffer.
2. _pbBuffer_ - A pointer that receives the color context profile.
3. _pcbActual_ - A pointer that receives the actual buffer size needed to retrieve the entire color context profile.

### GetProfileBytes - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### GetProfileBytes - Remarks

Only use this method if the context type is [WICColorContextProfile][wccecs].

Calling this method with pbBuffer set to **NULL** will cause it to return the required buffer size in *pcbActual*.

## GetType

Retrieves the color context type.

```cpp
HRESULT GetType(
   WICColorContextType *pType // [out]
);
```

### GetType - Parameter

1. _pType_ - A pointer that receives the [WICColorContextType][wccecs] of the color context.

### GetType - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## InitializeFromExifColorSpace

Initializes the color context using an Exchangeable Image File (**EXIF**) color space.

```cpp
HRESULT InitializeFromExifColorSpace(
   UINT value // [in]
);
```

### InitializeFromExifColorSpace - Parameter

1. _value_ - The value of the EXIF color space.

   | Value | Meaning                   |
   | :---- | :------------------------ |
   | 1     | A sRGB color space.       |
   | 2     | An Adobe RGB color space. |

### InitializeFromExifColorSpace - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### InitializeFromExifColorSpace - Remarks

Once a color context has been initialized, it can't be re-initialized.

## InitializeFromFilename

Initializes the color context from the given file.

```cpp
HRESULT InitializeFromFilename(
   LPCWSTR wzFilename // [in]
);
```

### InitializeFromFilename - Parameter

1. *wzFilename* - The name of the file.

### InitializeFromFilename - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### InitializeFromFilename - Remarks

Once a color context has been initialized, it can't be re-initialized.

## InitializeFromMemory

Initializes the color context from a memory block.

```cpp
HRESULT InitializeFromMemory(
   const BYTE *pbBuffer,   // [in]
   UINT       cbBufferSize // [in]
);
```

### InitializeFromMemory - Parameter

1. *pbBuffer* - The buffer used to initialize the **IWICColorContext**.
2. *cbBufferSize* - The size of the *pbBuffer* buffer.

### InitializeFromMemory - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### InitializeFromMemory - Remarks

Once a color context has been initialized, it can't be re-initialized.

## Related

- [IWICImagingFactory::CreateColorContext](IWICImagingFactory#createcolorcontext)
