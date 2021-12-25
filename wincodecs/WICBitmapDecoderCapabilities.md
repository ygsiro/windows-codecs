---
layout: interface
category: ENUMERATIONS
title: WICBitmapDecoderCapabilities
---

Specifies the capabilities of the decoder.

```cpp
typedef enum WICBitmapDecoderCapabilities {
  WICBitmapDecoderCapabilitySameEncoder,
  WICBitmapDecoderCapabilityCanDecodeAllImages,
  WICBitmapDecoderCapabilityCanDecodeSomeImages,
  WICBitmapDecoderCapabilityCanEnumerateMetadata,
  WICBitmapDecoderCapabilityCanDecodeThumbnail,
  WICBITMAPDECODERCAPABILITIES_FORCE_DWORD
} ;
```

## WICBitmapDecoderCapabilitySameEncoder

Decoder recognizes the image was encoded with an encoder produced by the same vendor.

## WICBitmapDecoderCapabilityCanDecodeAllImages

Decoder can decode all the images within an image container.

## WICBitmapDecoderCapabilityCanDecodeSomeImages

Decoder can decode some of the images within an image container.

## WICBitmapDecoderCapabilityCanEnumerateMetadata

Decoder can enumerate the metadata blocks within a container format.

## WICBitmapDecoderCapabilityCanDecodeThumbnail

Decoder can find and decode a thumbnail.
