---
layout: interface
category: Interface
title: IWICBitmap
code:
  - key: WICRect
  - key: IWICBitmapLock
  - key: IWICPalette
TOC:
  - name: Inheritance
  - name: Remarks
  - name: Lock
  - name: SetPalette
  - name: SetResolution
---

Defines methods that add the concept of writeability and static in-memory representations of bitmaps to [IWICBitmapSource][bs].

## Inheritance

The **IWICBitmap** interface inherits from [IWICBitmapSource][bs].
**IWICBitmap** also has these types of members:

- [Lock](#lock)
- [SetPalette](#setpalette)
- [SetResolution](#setresolution)

## Remarks

**IWICBitmap** inherits from [IWICBitmapSource][bs] and therefore also inherits the [CopyPixels][cp] method.
When pixels need to be moved to a new memory location, [CopyPixels][cp] is often the most efficient.

Because of the internal memory representation implied by the **IWICBitmap**, in-place modification and processing using the Lock is more efficient than [CopyPixels][cp], usually reducing to a simple pointer access directly into the memory owned by the bitmap rather than a copy. This is contrasted to procedural bitmaps which implement only [CopyPixels][cp] because there is no internal memory representation and one would need to be created on demand to satisfy a call to [Lock](#lock).

## Lock

Provides access to a rectangular area of the bitmap.

```cpp
HRESULT Lock(
  const WICRect  *prcLock, // [in]
  DWORD  flags,            // [in]
  IWICBitmapLock **ppILock // [out]
);
```

### Lock - Parameters

1. _prcLock_ - The rectangle to be accessed.
2. _flag_ - The access mode you wish to obtain for the lock.  
   This is a bitwise combination of [WICBitmapLockFlags][blf] for read, write, or read and write access.

   | Value                  | Meaning               |
   | :--------------------- | :-------------------- |
   | **WICBitmapLockRead**  | The read access lock  |
   | **WICBitmapLockWrite** | The write access lock |

3. _ppILock_ - A pointer that receives the locked memory location.

### Lock - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### Lock - Remarks

Locks are exclusive for writing but can be shared for reading.
You cannot call [CopyPixels][cp] while the **IWICBitmap** is locked for writing.
Doing so will return an error, since locks are exclusive.

## SetPalette

Provides access for palette modifications.

```cpp
HRESULT SetPalette(
  IWICPalette *pIPalette // [in]
);
```

### SetPalette - Parameters

1. _pIPalette_ - The palette to use for conversion.

### SetPalette - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## SetResolution

Changes the physical resolution of the image.

```cpp
HRESULT SetResolution(
  double dpiX, // [in]
  double dpiY  // [in]
);
```

### SetResolution - Parameters

1. _dpiX_ - The horizontal resolution.
2. _dpiY_ - The vertical resolution.

### SetResolution - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### SetResolution - Remarks

This method has no effect on the actual pixels or samples stored in the bitmap.
Instead the interpretation of the sampling rate is modified.
This means that a 96 DPI image which is 96 pixels wide is one inch.
If the physical resolution is modified to 48 DPI, then the bitmap is considered to be 2 inches wide but has the same number of pixels.
If the resolution is less than **REAL_EPSILON** (1.192092896e-07F) the error code **WINCODEC_ERR_INVALIDPARAMETER** is returned.

[blf]: WICBitmapLockFlags
[bs]: IWICBitmapSource
[bl]: IWICBitmapLock
[cp]: IWICBitmapSource#copypixels
