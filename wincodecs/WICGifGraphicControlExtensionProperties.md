---
layout: interface
category: ENUMERATIONS
title: WICGifGraphicControlExtensionProperties
---

Specifies the graphic control extension metadata properties that define the transitions between each frame animation for Graphics Interchange Format (**GIF**) images.

```cpp
typedef enum WICGifGraphicControlExtensionProperties {
  WICGifGraphicControlExtensionDisposal,
  WICGifGraphicControlExtensionUserInputFlag,
  WICGifGraphicControlExtensionTransparencyFlag,
  WICGifGraphicControlExtensionDelay,
  WICGifGraphicControlExtensionTransparentColorIndex,
  WICGifGraphicControlExtensionProperties_FORCE_DWORD
} ;
```

## WICGifGraphicControlExtensionDisposal

Indicates the disposal requirements.
0 - no disposal, 1 - do not dispose, 2 - restore to background color, 3 - restore to previous.

## WICGifGraphicControlExtensionUserInputFlag

Indicates the user input flag.
**TRUE** if user input should advance to the next frame; otherwise, **FALSE**.

## WICGifGraphicControlExtensionTransparencyFlag

Indicates the transparency flag.
**TRUE** if a transparent color in is in the color table for this frame; otherwise, **FALSE**.

## WICGifGraphicControlExtensionDelay

Indicates how long to display the next frame before advancing to the next frame, in units of 1/100th of a second.

## WICGifGraphicControlExtensionTransparentColorIndex

Indicates which color in the palette should be treated as transparent.
