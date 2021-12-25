---
layout: interface
category: Interface
title: IWICDevelopRaw
TOC:
  - name: Inheritance
  - name: GetContrast
  - name: GetCurrentParameterSet
  - name: GetExposureCompensation
  - name: GetGamma
  - name: GetKelvinRangeInfo
  - name: GetNamedWhitePoint
  - name: GetNoiseReduction
  - name: GetRenderMode
  - name: GetRotation
  - name: GetSaturation
  - name: GetSharpness
  - name: GetTint
  - name: GetToneCurve
  - name: GetWhitePointKelvin
  - name: GetWhitePointRGB
  - name: LoadParameterSet
  - name: QueryRawCapabilitiesInfo
  - name: SetContrast
  - name: SetDestinationColorContext
  - name: SetExposureCompensation
  - name: SetGamma
  - name: SetNamedWhitePoint
  - name: SetNoiseReduction
  - name: SetNotificationCallback
  - name: SetRenderMode
  - name: SetRotation
  - name: SetSaturation
  - name: SetSharpness
  - name: SetToneCurve
  - name: SetWhitePointKelvin
  - name: SetWhitePointRGB
code:
  - key: WICNamedWhitePoint
  - key: WICRawRenderMode
  - key: WICRawToneCurve
  - key: IWICColorContext
  - key: WICRawParameterSet
  - key: WICRawCapabilitiesInfo
  - key: IWICDevelopRawNotificationCallback
---

Exposes methods that provide access to the capabilities of a raw codec format.

## Inheritance

[wbfd]: IWICBitmapFrameDecode

The **IWICDevelopRaw** interface inherits from [IWICBitmapFrameDecode][wbfd].
**IWICDevelopRaw** also has these types of members:

- [getcontrast](#getcontrast)
- [GetCurrentParameterSet](#getcurrentparameterset)
- [GetExposureCompensation](#GetExposureCompensation)
- [GetGamma](#getgamma)
- [GetKelvinRangeInfo](#getkelvinrangeinfo)
- [GetNamedWhitePoint](#getnamedwhitepoint)
- [GetNoiseReduction](#getnoisereduction)
- [GetRenderMode](#getrendermode)
- [GetRotation](#getrotation)
- [GetSaturation](#getsaturation)
- [GetSharpness](#getsharpness)
- [GetTint](#gettint)
- [GetToneCurve](#gettonecurve)
- [GetWhitePointKelvin](#getwhitepointkelvin)
- [GetWhitePointRGB](#getwhitepointrgb)
- [LoadParameterSet](#loadparameterset)
- [QueryRawCapabilitiesInfo](#queryrawcapabilitiesinfo)
- [SetContrast](#setcontrast)
- [SetDestinationColorContext](#setdestinationcolorcontext)
- [SetExposureCompensation](#setexposurecompensation)
- [SetGamma](#setgamma)
- [SetNamedWhitePoint](#setnamedwhitepoint)
- [SetNoiseReduction](#setnoisereduction)
- [SetNotificationCallback](#setnotificationcallback)
- [SetRenderMode](#setrendermode)
- [SetRotation](#setrotation)
- [SetSaturation](#setsaturation)
- [SetSharpness](#setsharpness)
- [SetToneCurve](#settonecurve)
- [SetWhitePointKelvin](#setwhitepointkelvin)
- [SetWhitePointRGB](#setwhitepointrgb)

## GetContrast

Gets the contrast value of the raw image.

```cpp
HRESULT GetContrast(
   double *pContrast // [out]
);
```

### GetContrast - Parameter

1. *pContrast* - A pointer that receives the contrast value of the raw image.
   The default value is the "as-shot" setting.
   The value range for contrast is 0.0 through 1.0.
   The 0.0 lower limit represents no contrast applied to the image, while the 1.0 upper limit represents the highest amount of contrast that can be applied.

### GetContrast - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## GetCurrentParameterSet

Gets the current set of parameters.

```cpp
HRESULT GetCurrentParameterSet(
   IPropertyBag2 **ppCurrentParameterSet // [out]
);
```

### GetCurrentParameterSet - Parameter

1. *ppCurrentParameterSet* - A pointer that receives a pointer to the current set of parameters.

### GetCurrentParameterSet - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## GetExposureCompensation

Gets the exposure compensation stop value of the raw image.

```cpp
HRESULT GetExposureCompensation(
   double *pEV // [out]
);
```

### GetExposureCompensation - Parameter

1. *pEV* - A pointer that receives the exposure compensation stop value.
   The default is the "as-shot" setting.

### GetExposureCompensation - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## GetGamma

Gets the current gamma setting of the raw image.

```cpp
HRESULT GetGamma(
   double *pGamma // [out]
);
```

### GetGamma - Parameter

1. *pGamma* - A pointer that receives the current gamma setting.

### GetGamma - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## GetKelvinRangeInfo

Gets the information about the current Kelvin range of the raw image.

```cpp
HRESULT GetKelvinRangeInfo(
   UINT *pMinKelvinTemp, // [out]
   UINT *pMaxKelvinTemp, // [out]
   UINT *pKelvinTempStepValue // [out]
);
```

### GetKelvinRangeInfo - Parameter

1. *pMinKelvinTemp* - A pointer that receives the minimum Kelvin temperature.
2. *pMaxKelvinTemp* - A pointer that receives the maximum Kelvin temperature.
3. *pKelvinTempStepValue* - A pointer that receives the Kelvin step value.

### GetKelvinRangeInfo - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## GetNamedWhitePoint

Gets the named white point of the raw image.

```cpp
HRESULT GetNamedWhitePoint(
   WICNamedWhitePoint *pWhitePoint // [out]
);
```

### GetNamedWhitePoint - Parameter

1. *pWhitePoint* - A pointer that receives the bitwise combination of the enumeration values.

### GetNamedWhitePoint - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### GetNamedWhitePoint - Remarks

If the named white points are not supported by the raw image or the raw file contains named white points that are not supported by this API, the codec implementer should still mark this capability as supported.

If the named white points are not supported by the raw image, a best effort should be made to adjust the image to the named white point even when it isn't a pre-defined white point of the raw file.

[wnwp]: WICNamedWhitePoint

If the raw file contains named white points not supported by this API, the codec implementer should support the named white points in [WICNamedWhitePoint][wnwp].

## GetNoiseReduction

Gets the noise reduction value of the raw image.

```cpp
HRESULT GetNoiseReduction(
   double *pNoiseReduction // [out]
);
```

### GetNoiseReduction - Parameter

1. *pNoiseReduction* - A pointer that receives the noise reduction value of the raw image.
   The default value is the "as-shot" setting if it exists or 0.0.
   The value range for noise reduction is 0.0 through 1.0.
   The 0.0 lower limit represents no noise reduction applied to the image, while the 1.0 upper limit represents full highest noise reduction amount that can be applied.

### GetNoiseReduction - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## GetRenderMode

[wrrm]: WICRawRenderMode

Gets the current [WICRawRenderMode][wrrm].

```cpp
HRESULT GetRenderMode(
   WICRawRenderMode *pRenderMode // [out]
);
```

### GetRenderMode - Parameter

1. *pRenderMode* - A pointer that receives the current [WICRawRenderMode][wrrm].

### GetRenderMode - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## GetRotation

Gets the current rotation angle.

```cpp
HRESULT GetRotation(
   double *pRotation // [out]
);
```

### GetRotation - Parameter

1. *pRotation* - A pointer that receives the current rotation angle.

### GetRotation - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## GetSaturation

Gets the saturation value of the raw image.

```cpp
HRESULT GetSaturation(
   double *pSaturation // [out]
);
```

### GetSaturation - Parameter

1. *pSaturation* - A pointer that receives the saturation value of the raw image.
   The default value is the "as-shot" setting.
   The value range for saturation is 0.0 through 1.0.
   A value of 0.0 represents an image with a fully de-saturated image, while a value of 1.0 represents the highest amount of saturation that can be applied.

### GetSaturation - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## GetSharpness

Gets the sharpness value of the raw image.

```cpp
HRESULT GetSharpness(
   double *pSharpness // [out]
);
```

### GetSharpness - Parameter

1. A pointer that receives the sharpness value of the raw image.
   The default value is the "as-shot" setting. The value range for sharpness is 0.0 through 1.0.
   The 0.0 lower limit represents no sharpening applied to the image, while the 1.0 upper limit represents the highest amount of sharpness that can be applied.

### GetSharpness - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## GetTint

Gets the tint value of the raw image.

```cpp
HRESULT GetTint(
   double *pTint // [out]
);
```

### GetTint - Parameter

1. *pTint* - A pointer that receives the tint value of the raw image.
   The default value is the "as-shot" setting if it exists or 0.0.
   The value range for sharpness is -1.0 through +1.0.
   The -1.0 lower limit represents a full green bias to the image, while the 1.0 upper limit represents a full magenta bias.

### GetTint - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## GetToneCurve

Gets the tone curve of the raw image.

```cpp
HRESULT GetToneCurve(
   UINT            cbToneCurveBufferSize, // [in]
   WICRawToneCurve *pToneCurve, // [out]
   UINT            *pcbActualToneCurveBufferSize // [out]
);
```

### GetToneCurve - Parameter

1. *cbToneCurveBufferSize* - The size of the pToneCurve buffer.
2. *pToneCurve* - A pointer that receives the WICRawToneCurve of the raw image.
3. *pcbActualToneCurveBufferSize* - A pointer that receives the size needed to obtain the tone curve structure.

### GetToneCurve - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## GetWhitePointKelvin

Gets the white point Kelvin temperature of the raw image.

```cpp
HRESULT GetWhitePointKelvin(
   UINT *pWhitePointKelvin // [out]
);
```

### GetWhitePointKelvin - Parameter

1. *pWhitePointKelvin* - A pointer that receives the white point Kelvin temperature of the raw image.
   The default is the "as-shot" setting value.

### GetWhitePointKelvin - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## GetWhitePointRGB

Gets the white point RGB values.

```cpp
HRESULT GetWhitePointRGB(
   UINT *pRed, // [out]
   UINT *pGreen, // [out]
   UINT *pBlue // [out]
);
```

### GetWhitePointRGB - Parameter

1. *pRed* - A pointer that receives the red white point value.
2. *pGreen* - A pointer that receives the green white point value.
3. *pBlue* - A pointer that receives the blue white point value.

### GetWhitePointRGB - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## LoadParameterSet

[wrps]: WICRawParameterSet

Sets the desired [WICRawParameterSet][wrps] option.

```cpp
HRESULT LoadParameterSet(
   WICRawParameterSet ParameterSet // [in]
);
```

### LoadParameterSet - Parameter

1. *ParameterSet* - The desired [WICRawParameterSet][wrps] option.

### LoadParameterSet - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## QueryRawCapabilitiesInfo

Retrieves information about which capabilities are supported for a raw image.

```cpp
HRESULT QueryRawCapabilitiesInfo(
   WICRawCapabilitiesInfo *pInfo // [out]
);
```

### QueryRawCapabilitiesInfo - Parameter

[wrci]: WICRawCapabilitiesInfo

1. *pInfo* - A pointer that receives [WICRawCapabilitiesInfo][wrci] that provides the capabilities supported by the raw image.

### QueryRawCapabilitiesInfo - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### QueryRawCapabilitiesInfo - Remarks

It is recommended that a codec report that a capability is supported even if the results at the outer range limits are not of perfect quality.

## SetContrast

Sets the contrast value of the raw image.

```cpp
HRESULT SetContrast(
   double Contrast // [in]
);
```

### SetContrast - Parameter

1. *Contrast* - The contrast value of the raw image.
   The default value is the "as-shot" setting.
   The value range for contrast is 0.0 through 1.0.
   The 0.0 lower limit represents no contrast applied to the image, while the 1.0 upper limit represents the highest amount of contrast that can be applied.

### SetContrast - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### SetContrast - Remarks

The codec implementer must determine what the upper range value represents and must determine how to map the value to their image processing routines.

## SetDestinationColorContext

Sets the destination color context.

```cpp
HRESULT SetDestinationColorContext(
   IWICColorContext *pColorContext // [in]
);
```

### SetDestinationColorContext - Parameter

1. *pColorContext* - The destination color context.

### SetDestinationColorContext - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## SetExposureCompensation

Sets the exposure compensation stop value.

```cpp
HRESULT SetExposureCompensation(
   double ev // [in]
);
```

### SetExposureCompensation - Parameter

1. *ev* - The exposure compensation value. The value range for exposure compensation is -5.0 through +5.0, which equates to 10 full stops.

### SetExposureCompensation - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### SetExposureCompensation - Remarks

It is recommended that a codec report that this method is supported even if the results at the outer range limits are not of perfect quality.

## SetGamma

Sets the desired gamma value.

```cpp
HRESULT SetGamma(
   double Gamma // [in]
);
```

### SetGamma - Parameter

1. *Gamma* - The desired gamma value.

### SetGamma - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## SetNamedWhitePoint

Sets the named white point of the raw file.

```cpp
HRESULT SetNamedWhitePoint(
   WICNamedWhitePoint WhitePoint // [in]
);
```

### SetNamedWhitePoint - Parameter

1. *WhitePoint* - A bitwise combination of the enumeration values.

### SetNamedWhitePoint - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### SetNamedWhitePoint - Remarks

If the named white points are not supported by the raw image or the raw file contains named white points that are not supported by this API, the codec implementer should still mark this capability as supported.

If the named white points are not supported by the raw image, a best effort should be made to adjust the image to the named white point even when it isn't a pre-defined white point of the raw file.

If the raw file contains named white points not supported by this API, the codec implementer should support the named white points in the API.

Due to other white point setting methods (e.g. [SetWhitePointKelvin](#setwhitepointkelvin)), care must be taken by codec implementers to ensure proper interoperability.
For instance, if the caller sets via a named white point then the codec implementer may wish to disable reading back the corresponding Kelvin temperature.
In specific cases where the codec implementer wishes to deny a given action because of previous calls, **WINCODEC_ERR_WRONGSTATE** should be returned.

## SetNoiseReduction

Sets the noise reduction value of the raw image.

```cpp
HRESULT SetNoiseReduction(
   double NoiseReduction // [in]
);
```

### SetNoiseReduction - Parameter

1. *NoiseReduction* - The noise reduction value of the raw image.
   The default value is the "as-shot" setting if it exists or 0.0.
   The value range for noise reduction is 0.0 through 1.0.
   The 0.0 lower limit represents no noise reduction applied to the image, while the 1.0 upper limit represents highest noise reduction amount that can be applied.

### SetNoiseReduction - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### SetNoiseReduction - Remarks

The codec implementer must determine what the upper range value represents and must determine how to map the value to their image processing routines.

## SetNotificationCallback

Sets the notification callback method.

```cpp
HRESULT SetNotificationCallback(
   IWICDevelopRawNotificationCallback *pCallback // [in]
);
```

### SetNotificationCallback - Parameter

1. *pCallback* - Pointer to the notification callback method.

### SetNotificationCallback - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## SetRenderMode

Sets the current [WICRawRenderMode][wrrm].

```cpp
HRESULT SetRenderMode(
   WICRawRenderMode RenderMode // [in]
);
```

### SetRenderMode - Parameter

1. *RenderMode* - The render mode to use.

### SetRenderMode - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## SetRotation

Sets the desired rotation angle.

```cpp
HRESULT SetRotation(
   double Rotation // [in]
);
```

### SetRotation - Parameter

1. *Rotation* - The desired rotation angle.

### SetRotation - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## SetSaturation

Sets the saturation value of the raw image.

```cpp
HRESULT SetSaturation(
   double Saturation // [in]
);
```

### SetSaturation - Parameter

1. *Saturation* - The saturation value of the raw image.
   The value range for saturation is 0.0 through 1.0.
   A value of 0.0 represents an image with a fully de-saturated image, while a value of 1.0 represents the highest amount of saturation that can be applied.

### SetSaturation - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### SetSaturation - Remarks

The codec implementer must determine what the upper range value represents and must determine how to map the value to their image processing routines.

## SetSharpness

Sets the sharpness value of the raw image.

```cpp
HRESULT SetSharpness(
   double Sharpness // [in]
);
```

### SetSharpness - Parameter

1. *Sharpness* - The sharpness value of the raw image. The default value is the "as-shot" setting.
   The value range for sharpness is 0.0 through 1.0.
   The 0.0 lower limit represents no sharpening applied to the image, while the 1.0 upper limit represents the highest amount of sharpness that can be applied.

### SetSharpness - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### SetSharpness - Remarks

The codec implementer must determine what the upper range value represents and must determine how to map the value to their image processing routines.

## SetTint

Sets the tint value of the raw image.

```cpp
HRESULT SetTint(
   double Tint // [in]
);
```

### SetTint - Parameter

1. *Tint* - The tint value of the raw image.
   The default value is the "as-shot" setting if it exists or 0.0.
   The value range for sharpness is -1.0 through +1.0. The -1.0 lower limit represents a full green bias to the image, while the 1.0 upper limit represents a full magenta bias.

### SetTint - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### SetTint - Remarks

The codec implementer must determine what the outer range values represent and must determine how to map the values to their image processing routines.

## SetToneCurve

Sets the tone curve for the raw image.

```cpp
HRESULT SetToneCurve(
   UINT                  cbToneCurveSize, // [in]
   const WICRawToneCurve *pToneCurve // [in]
);
```

### SetToneCurve - Parameter

1. *cbToneCurveSize* - The size of the *pToneCurve* structure.
2. *pToneCurve* - The desired tone curve.

### SetToneCurve - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## SetWhitePointKelvin

Sets the white point Kelvin value.

```cpp
HRESULT SetWhitePointKelvin(
   UINT WhitePointKelvin // [in]
);
```

### SetWhitePointKelvin - Parameter

1. *WhitePointKelvin* - The white point Kelvin value. Acceptable Kelvin values are 1,500 through 30,000.

### SetWhitePointKelvin - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### SetWhitePointKelvin - Remarks

Codec implementers should faithfully adjust the color temperature within the range supported natively by the raw image.
For values outside the native support range, the codec implementer should provide a best effort representation of the image at that color temperature.

Codec implementers should return **WINCODEC_ERR_VALUEOUTOFRANGE** if the value is out of defined acceptable range.

Codec implementers must ensure proper interoperability with other white point setting methods such as [SetWhitePointRGB](#setwhitepointrgb).
For example, if the caller sets the white point via [SetNamedWhitePoint](#setnamedwhitepoint) then the codec implementer may want to disable reading back the corresponding Kelvin temperature.
In specific cases where the codec implementer wants to deny a given action because of previous calls, **WINCODEC_ERR_WRONGSTATE** should be returned.

## SetWhitePointRGB

Sets the white point RGB values.

```cpp
HRESULT SetWhitePointRGB(
   UINT Red, // [in]
   UINT Green, // [in]
   UINT Blue // [in]
);
```

### SetWhitePointRGB - Parameter

1. *Red* - The red white point value.
2. *Green* - The green white point value.
3. *Blue* - The blue white point value.

### SetWhitePointRGB - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### SetWhitePointRGB - Remarks

Due to other white point setting methods (e.g. [SetWhitePointKelvin](#setwhitepointkelvin)), care must be taken by codec implementers to ensure proper interoperability.
For instance, if the caller sets via a named white point then the codec implementer may wish to disable reading back the corresponding Kelvin temperature.
In specific cases where the codec implementer wishes to deny a given action because of previous calls, **WINCODEC_ERR_WRONGSTATE** should be returned.
