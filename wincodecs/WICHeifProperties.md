---
layout: interface
category: ENUMERATIONS
title: WICHeifProperties
---

Specifies the properties of a High Efficiency Image Format (**HEIF**) image.

```cpp
typedef enum WICHeifProperties {
  WICHeifOrientation,
  WICHeifProperties_FORCE_DWORD
} ;
```

## WICHeifOrientation

Indicates the orientation of the image.

The value of this property uses the same numbering scheme as the System.Photo.Orientation property.
For example, a value of 1 (**PHOTO_ORIENTATION_NORMAL**) indicates a 0 degree rotation.
