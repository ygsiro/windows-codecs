---
layout: interface
category: STRUCTURES
title: WICBitmapPattern
---

Contains members that identify a pattern within an image file which can be used to identify a particular format.

```cpp
typedef struct WICBitmapPattern {
  ULARGE_INTEGER Position;
  ULONG          Length;
  BYTE           *Pattern;
  BYTE           *Mask;
  BOOL           EndOfStream;
} WICBitmapPattern;
```

## Members

### Position

The offset the pattern is located in the file.

### Length

The pattern length.

### Pattern

The actual pattern.

### Mask

The pattern mask.

### EndOfStream

The end of the stream.
