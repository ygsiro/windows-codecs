---
layout: interface
category: Interface
title: IWICBitmapDecoderInfo
code:
  - key: IWICBitmapDecoder
TOC:
  - name: CreateInstance
  - name: GetPatterns
  - name: MatchesPattern
---

Exposes methods that provide information about a decoder.

## Inheritance

The **IWICBitmapDecoderInfo** interface inherits from [IWICBitmapCodecInfo][wbci].
**IWICBitmapDecoderInfo** also has these types of members:

- [CreateInstance](#createinstance)
- [GetPatterns](#getpatterns)
- [MatchesPattern](#matchespattern)

## CreateInstance

Creates a new [IWICBitmapDecoder][wbd] instance.

```cpp
HRESULT CreateInstance(
  IWICBitmapDecoder **ppIBitmapDecoder // [out]
);
```

### CreateInstance - Parameters

1. _ppIBitmapDecoder_ - A pointer that receives a pointer to a new instance of the [IWICBitmapDecoder][wbd].

### CreateInstance - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## GetPatterns

Retrieves the file pattern signatures supported by the decoder.

```cpp
HRESULT GetPatterns(
  UINT             cbSizePatterns,    // [in]
  WICBitmapPattern *pPatterns,        // [out]
  UINT             *pcPatterns,       // [out]
  UINT             *pcbPatternsActual // [out]
);
```

### GetPatterns - Parameters

1. _cbSizePatterns_ - The array size of the pPatterns array.
2. _pPatterns_ - Receives a list of [WICBitmapPattern][wbp] objects supported by the decoder.
3. _pcPatterns_ - Receives the number of patterns the decoder supports.
4. _pcbPatternsActual_ - Receives the actual buffer size needed to retrieve all pattern signatures supported by the decoder.

### GetPatterns - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### GetPatterns - Remarks

To retrieve all pattern signatures, this method should first be called with _pPatterns_ set to **NULL** to retrieve the actual buffer size needed through _pcbPatternsActual_.
Once the needed buffer size is known, allocate a buffer of the needed size and call **GetPatterns** again with the allocated buffer.

## MatchesPattern

Retrieves a value that indicates whether the codec recognizes the pattern within a specified stream.

```cpp
HRESULT MatchesPattern(
  IStream *pIStream, // [in]
  BOOL    *pfMatches // [out]
);
```

### MatchesPattern - Parameters

1. _pIStream_ - The stream to pattern match within.
2. _pfMatches_ - A pointer that receives **TRUE** if the patterns match;
   otherwise, **FALSE**.

### MatchesPattern - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

[wbd]: IWICBitmapDecoder
[wbp]: WICBitmapPattern
[wbci]: IWICBitmapCodecInfo
