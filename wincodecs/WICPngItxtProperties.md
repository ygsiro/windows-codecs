---
layout: interface
category: ENUMERATIONS
title: WICPngItxtProperties
---

Specifies the Portable Network Graphics (**PNG**) iTXT chunk metadata properties.

```cpp
typedef enum WICPngItxtProperties {
  WICPngItxtKeyword,
  WICPngItxtCompressionFlag,
  WICPngItxtLanguageTag,
  WICPngItxtTranslatedKeyword,
  WICPngItxtText,
  WICPngItxtProperties_FORCE_DWORD
} ;
```

## WICPngItxtKeyword

Indicates the keywords in the iTXT metadata chunk.

## WICPngItxtCompressionFlag

Indicates whether the text in the iTXT chunk is compressed.
1 if the text is compressed; otherwise, 0.

## WICPngItxtLanguageTag

Indicates the human language used by the translated keyword and the text.

## WICPngItxtTranslatedKeyword

Indicates a translation of the keyword into the language indicated by the language tag.

## WICPngItxtText

Indicates additional text in the iTXT metadata chunk.
