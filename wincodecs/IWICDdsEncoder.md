---
layout: interface
category: Interface
title: IWICDdsEncoder
TOC:
  - name: Inheritance
  - name: Remarks
  - name: CreateNewFrame
  - name: GetParameters
  - name: SetParameters
code:
  - key: IWICBitmapFrameEncode
  - key: WICDdsParameters
---

Enables writing DDS format specific information to an encoder.

## Inheritance

The **IWICDdsEncoder** interface inherits from the IUnknown interface.
**IWICDdsEncoder** also has these types of members:

- [CreateNewFrame](#createnewframe)
- [GetParameters](#getparameters)
- [SetParameters](#setparameters)

## Remarks

This interface is implemented by the WIC DDS codec.
To obtain this interface, create an [IWICBitmapEncoder][wbe] using the DDS codec and QueryInterface for **IWICDdsEncoder**.

## CreateNewFrame

Creates a new frame to encode.

```cpp
HRESULT CreateNewFrame(
   IWICBitmapFrameEncode **ppIFrameEncode, // [out]
   UINT                  *pArrayIndex,     // [out, optional]
   UINT                  *pMipLevel,       // [out, optional]
   UINT                  *pSliceIndex      // [out, optional]
);
```

### CreateNewFrame - Parameter

1. _ppIFrameEncode_ - A pointer to the newly created frame object.
2. _pArrayIndex_ - Points to the location where the array index is returned.
3. _pMipLevel_ - Points to the location where the mip level index is returned.
4. _pSliceIndex_ - Points to the location where the slice index is returned.

### CreateNewFrame - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### CreateNewFrame - Remarks

[wbe]: IWICBitmapEncoder
[wbe-cnf]: IWICBitmapEncoder#createnewframe

This is equivalent to [IWICBitmapEncoder][wbe]::[CreateNewFrame][wbe-cnf], but returns additional information about the array index, mip level and slice of the newly created frame. In contrast to [IWICBitmapEncoder][wbe]::[CreateNewFrame][wbe-cnf], there is no IPropertyBag2\* parameter because individual DDS frames do not have separate properties.

## GetParameters

Gets DDS-specific data.

```cpp
HRESULT GetParameters(
   WICDdsParameters *pParameters // [out]
);
```

### GetParameters - Parameter

1. _pParameters_ - Points to the structure where the information is returned.

### GetParameters - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### GetParameters - Remarks

An application can call **GetParameters** to obtain the default DDS parameters, modify some or all of them, and then call [SetParameters](#setparameters).

## SetParameters

Sets DDS-specific data.

```cpp
HRESULT SetParameters(
   WICDdsParameters *pParameters // [out]
);
```

### SetParameters - Parameter

1. _pParameters_ - Points to the structure where the information is described.

### SetParameters - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### SetParameters - Remarks

You cannot call this method after you have started to write frame data, for example by calling **IWICDdsEncoder**::[CreateNewFrame](#createnewframe).

[wdp]: WICDdsParameters

Setting DDS parameters using this method provides the DDS encoder with information about the expected number of frames and the dimensions and other parameters of each frame.
The DDS encoder will fail if you do not set frame data that matches these expectations.
For example, if you set [WICDdsParameters][wdp]::Width and Height to 32, and MipLevels to 6, the DDS encoder will expect 6 frames with the following dimensions:

- 32x32 pixels.
- 16x16 pixels.
- 8x8 pixels.
- 4x4 pixels.
- 2x2 pixels.
- 1x1 pixels.
