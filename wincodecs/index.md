---
title: wincodec.h header
category: index
layout: index
---

## Interface

### [IWICBitmap](IWICBitmap)

Defines methods that add the concept of writeability and static in-memory representations of bitmaps to [IWICBitmapSource](#iwicbitmapsource).

### [IWICBitmapClipper](IWICBitmapClipper)

Exposes methods that produce a clipped version of the input bitmap for a specified rectangular region of interest.

### [IWICBitmapCodecInfo](IWICBitmapCodecInfo)

Exposes methods that provide information about a particular codec.

### [IWICBitmapCodecProgressNotification](IWICBitmapCodecProgressNotification)

Exposes methods used for progress notification for encoders and decoders.

### [IWICBitmapDecoder](IWICBitmapDecoder)

Exposes methods that represent a decoder.

### [IWICBitmapDecoderInfo](IWICBitmapDecoderInfo)

Exposes methods that provide information about a decoder.

### [IWICBitmapEncoder](IWICBitmapEncoder)

Defines methods for setting an encoder's properties such as thumbnails, frames, and palettes.

### [IWICBitmapEncoderInfo](IWICBitmapEncoderInfo)

Exposes methods that provide information about an encoder.

### [IWICBitmapFlipRotator](IWICBitmapFlipRotator)

Exposes methods that produce a flipped (horizontal or vertical) and/or rotated (by 90 degree increments) bitmap source.
The flip is done before the rotation.

### [IWICBitmapFrameDecode](IWICBitmapFrameDecode)

Defines methods for decoding individual image frames of an encoded file.

### [IWICBitmapFrameEncode](IWICBitmapFrameEncode)

Represents an encoder's individual image frames.

### [IWICBitmapLock](IWICBitmapLock)

Exposes methods that support the Lock method.

### [IWICBitmapScaler](IWICBitmapScaler)

Represents a resized version of the input bitmap using a resampling or filtering algorithm.

### [IWICBitmapSource](IWICBitmapSource)

Exposes methods that refers to a source from which pixels are retrieved, but cannot be written back to.

### [IWICBitmapSourceTransform](IWICBitmapSourceTransform)

Exposes methods for offloading certain operations to the underlying [IWICBitmapSource](IWICBitmapSource) implementation.

### [IWICColorContext](IWICColorContext)

Exposes methods for color management.

### [IWICColorTransform](IWICColorTransform)

Exposes methods that transforms an [IWICBitmapSource](IWICBitmapSource) from one color context to another.

### [IWICComponentInfo](IWICComponentInfo)

Exposes methods that provide component information.

### [IWICDdsDecoder](IWICDdsDecoder)

Provides information and functionality specific to the DDS image format.

### [IWICDdsEncoder](IWICDdsEncoder)

Enables writing DDS format specific information to an encoder.

### [IWICDdsFrameDecode](IWICDdsFrameDecode)

Provides access to a single frame of DDS image data in its native **DXGI_FORMAT** form, as well as information about the image data.

### [IWICDevelopRaw](IWICDevelopRaw)

Exposes methods that provide access to the capabilities of a raw codec format.

### [IWICDevelopRawNotificationCallback](IWICDevelopRawNotificationCallback)

Exposes a callback method for raw image change nofications.

### [IWICEnumMetadataItem](IWICEnumMetadataItem)

Exposes methods that provide enumeration services for individual metadata items.

### [IWICFastMetadataEncoder](IWICFastMetadataEncoder)

Exposes methods used for in-place metadata editing.
A fast metadata encoder enables you to add and remove metadata to an image without having to fully re-encode the image.

### [IWICFormatConverter](IWICFormatConverter)

Represents an IWICBitmapSource that converts the image data from one pixel format to another, handling dithering and halftoning to indexed formats, palette translation and alpha thresholding.

### [IWICFormatConverterInfo](IWICFormatConverterInfo)

Exposes methods that provide information about a pixel format converter.

### [IWICImageEncoder](IWICImageEncoder)

Encodes ID2D1Image interfaces to an IWICBitmapEncoder.

### [IWICImagingFactory](IWICImagingFactory)

Exposes methods used to create components for the Windows Imaging Component (**WIC**) such as decoders, encoders and pixel format converters.

### [IWICImagingFactory2](IWICImagingFactory2)

An extension of the WIC factory interface that includes the ability to create an [IWICImageEncoder](IWICImageEncoder).

### [IWICJpegFrameDecode](IWICJpegFrameDecode)

Exposes methods for decoding JPEG images.
Provides access to the Start Of Frame (**SOF**) header, Start of Scan (**SOS**) header, the Huffman and Quantization tables, and the compressed JPEG JPEG data.
Also enables indexing for efficient random access.

### [IWICJpegFrameEncode](IWICJpegFrameEncode)

Exposes methods for writing compressed JPEG scan data directly to the WIC encoder's output stream.
Also provides access to the Huffman and quantization tables.

### [IWICMetadataQueryReader](IWICMetadataQueryReader)

Exposes methods for retrieving metadata blocks and items from a decoder or its image frames using a metadata query expression.

### [IWICMetadataQueryWriter](IWICMetadataQueryWriter)

Exposes methods for setting or removing metadata blocks and items to an encoder or its image frames using a metadata query expression.

### [IWICPalette](IWICPalette)

Exposes methods for accessing and building a color table, primarily for indexed pixel formats.

### [IWICPixelFormatInfo](IWICPixelFormatInfo)

Exposes methods that provide information about a pixel format.

### [IWICPixelFormatInfo2](IWICPixelFormatInfo2)

Extends IWICPixelFormatInfo by providing additional information about a pixel format.

### [IWICPlanarBitmapFrameEncode](IWICPlanarBitmapFrameEncode)

Allows planar component image pixels to be written to an encoder.

### [IWICPlanarBitmapSourceTransform](IWICPlanarBitmapSourceTransform)

Provides access to planar Y’CbCr pixel formats where pixel components are stored in separate component planes.

### [IWICPlanarFormatConverter](IWICPlanarFormatConverter)

Allows a format converter to be initialized with a planar source.

### [IWICProgressCallback](IWICProgressCallback)

**IWICProgressCallback** interface is documented only for compliance;
its use is not recommended and may be altered or unavailable in the future.
Instead, and use RegisterProgressNotification.

### [IWICProgressiveLevelControl](IWICProgressiveLevelControl)

Exposes methods for obtaining information about and controlling progressive decoding.

### [IWICStream](IWICStream)

Represents a Windows Imaging Component (**WIC**) stream for referencing imaging and metadata content.

## FUNCTIONS

### [WICConvertBitmapSource](WICConvertBitmapSource)

Obtains a [IWICBitmapSource](IWICBitmapSource) in the desired pixel format from a given [IWICBitmapSource](IWICBitmapSource).

### [WICCreateBitmapFromSection](WICCreateBitmapFromSection)

Returns a [IWICBitmapSource](IWICBitmapSource) that is backed by the pixels of a Windows Graphics Device Interface (**GDI**) section handle.

### [WICCreateBitmapFromSectionEx](WICCreateBitmapFromSectionEx)

Returns a [IWICBitmapSource](IWICBitmapSource) that is backed by the pixels of a Windows Graphics Device Interface (**GDI**) section handle.

### [WICMapGuidToShortName](WICMapGuidToShortName)

Obtains the short name associated with a given GUID.

### [WICMapSchemaToName](WICMapSchemaToName)

Obtains the name associated with a given schema.

### [WICMapShortNameToGuid](WICMapShortNameToGuid)

Obtains the GUID associated with the given short name.

## CALLBACK FUNCTIONS

### [PFNProgressNotification](PFNProgressNotification)

Application defined callback function called when codec component progress is made.

## STRUCTURES

### [WICBitmapPattern](WICBitmapPattern)

Contains members that identify a pattern within an image file which can be used to identify a particular format.

### [WICBitmapPlane](WICBitmapPlane)

Specifies the pixel format, buffer, stride and size of a component plane for a planar pixel format.

### [WICBitmapPlaneDescription](WICBitmapPlaneDescription)

Specifies the pixel format and size of a component plane.

### [WICDdsFormatInfo](WICDdsFormatInfo)

Specifies the **DXGI_FORMAT** and block information of a DDS format.

### [WICDdsParameters](WICDdsParameters)

Specifies the DDS image dimension, **DXGI_FORMAT** and alpha mode of contained data.

### [WICImageParameters](WICImageParameters)

This defines parameters that you can use to override the default parameters normally used when encoding an image.

### [WICJpegFrameHeader](WICJpegFrameHeader)

Represents a JPEG frame header.

### [WICJpegScanHeader](WICJpegScanHeader)

Represents a JPEG frame header.

### [WICRawCapabilitiesInfo](WICRawCapabilitiesInfo)

Defines raw codec capabilities.

### [WICRawToneCurve](WICRawToneCurve)

Represents a raw image tone curve.

### [WICRawToneCurvePoint](WICRawToneCurvePoint)

Represents a raw image tone curve point.

### [WICRect](WICRect)

Represents a rectangle for Windows Imaging Component (**WIC**) API.

## ENUMERATIONS

### [WIC8BIMIptcDigestProperties](WIC8BIMIptcDigestProperties)

Specifies the identifiers of the metadata items in an 8BIM IPTC digest metadata block.

### [WIC8BIMIptcProperties](WIC8BIMIptcProperties)

Specifies the identifiers of the metadata items in an 8BIM IPTC block.

### [WIC8BIMResolutionInfoProperties](WIC8BIMResolutionInfoProperties)

Specifies the identifiers of the metadata items in an 8BIMResolutionInfo block.

### [WICBitmapAlphaChannelOption](WICBitmapAlphaChannelOption)

Specifies the desired alpha channel usage.

### [WICBitmapCreateCacheOption](WICBitmapCreateCacheOption)

Specifies the desired cache usage.

### [WICBitmapDecoderCapabilities](WICBitmapDecoderCapabilities)

Specifies the capabilities of the decoder.

### [WICBitmapDitherType](WICBitmapDitherType)

Specifies the type of dither algorithm to apply when converting between image formats.

### [WICBitmapEncoderCacheOption](WICBitmapEncoderCacheOption)

Specifies the cache options available for an encoder.

### [WICBitmapInterpolationMode](WICBitmapInterpolationMode)

Specifies the sampling or filtering mode to use when scaling an image.

### [WICBitmapLockFlags](WICBitmapLockFlags)

Specifies access to an IWICBitmap.

### [WICBitmapPaletteType](WICBitmapPaletteType)

Specifies the type of palette used for an indexed image format.

### [WICBitmapTransformOptions](WICBitmapTransformOptions)

Specifies the flip and rotation transforms.

### [WICColorContextType](WICColorContextType)

Specifies the color context types.

### [WICComponentEnumerateOptions](WICComponentEnumerateOptions)

Specifies component enumeration options.

### [WICComponentSigning](WICComponentSigning)

Specifies the component signing status.

### [WICComponentType](WICComponentType)

Specifies the type of Windows Imaging Component (**WIC**) component.

### [WICDdsAlphaMode](WICDdsAlphaMode)

Specifies the the meaning of pixel color component values contained in the DDS image.

### [WICDdsDimension](WICDdsDimension)

Specifies the dimension type of the data contained in DDS image.

### [WICDecodeOptions](WICDecodeOptions)

Specifies decode options.

### [WICGifApplicationExtensionProperties](WICGifApplicationExtensionProperties)

Specifies the application extension metadata properties for a Graphics Interchange Format (**GIF**) image.

### [WICGifCommentExtensionProperties](WICGifCommentExtensionProperties)

Specifies the comment extension metadata properties for a Graphics Interchange Format (**GIF**) image.

### [WICGifGraphicControlExtensionProperties](WICGifGraphicControlExtensionProperties)

Specifies the graphic control extension metadata properties that define the transitions between each frame animation for Graphics Interchange Format (**GIF**) images.

### [WICGifImageDescriptorProperties](WICGifImageDescriptorProperties)

Specifies the image descriptor metadata properties for Graphics Interchange Format (**GIF**) frames.

### [WICGifLogicalScreenDescriptorProperties](WICGifLogicalScreenDescriptorProperties)

Specifies the logical screen descriptor properties for Graphics Interchange Format (**GIF**) metadata.

### [WICHeifHdrProperties](WICHeifHdrProperties)

Specifies the HDR properties of a High Efficiency Image Format (**HEIF**) image.

### [WICHeifProperties](WICHeifProperties)

Specifies the properties of a High Efficiency Image Format (**HEIF**) image.

### [WICJpegChrominanceProperties](WICJpegChrominanceProperties)

Specifies the JPEG chrominance table property.

### [WICJpegCommentProperties](WICJpegCommentProperties)

Specifies the JPEG comment properties.

### [WICJpegIndexingOptions](WICJpegIndexingOptions)

Specifies the options for indexing a JPEG image.

### [WICJpegLuminanceProperties](WICJpegLuminanceProperties)

Specifies the JPEG luminance table property.

### [WICJpegScanType](WICJpegScanType)

Specifies the memory layout of pixel data in a JPEG image scan.

### [WICJpegTransferMatrix](WICJpegTransferMatrix)

Specifies conversion matrix from `Y'Cb'Cr'` to `R'G'B'`.

### [WICJpegYCrCbSubsamplingOption](WICJpegYCrCbSubsamplingOption)

Specifies the JPEG `YCrCB` subsampling options.

### [WICNamedWhitePoint](WICNamedWhitePoint)

Specifies named white balances for raw images.

### [WICPixelFormatNumericRepresentation](WICPixelFormatNumericRepresentation)

Defines constants that specify a primitive type for numeric representation of a WIC pixel format.

### [WICPlanarOptions](WICPlanarOptions)

Specifies additional options to an [IWICPlanarBitmapSourceTransform](IWICPlanarBitmapSourceTransform) implementation.

### [WICPngBkgdProperties](WICPngBkgdProperties)

Specifies the Portable Network Graphics (**PNG**) background (**bKGD**) chunk metadata properties.

### [WICPngChrmProperties](WICPngChrmProperties)

Specifies the Portable Network Graphics (**PNG**) cHRM chunk metadata properties for CIE XYZ chromaticity.

### [WICPngFilterOption](WICPngFilterOption)

Specifies the Portable Network Graphics (**PNG**) filters available for compression optimization.

### [WICPngGamaProperties](WICPngGamaProperties)

Specifies the Portable Network Graphics (**PNG**) gAMA chunk metadata properties.

### [WICPngHistProperties](WICPngHistProperties)

Specifies the Portable Network Graphics (**PNG**) hIST chunk metadata properties.

### [WICPngIccpProperties](WICPngIccpProperties)

Specifies the Portable Network Graphics (**PNG**) iCCP chunk metadata properties.

### [WICPngItxtProperties](WICPngItxtProperties)

Specifies the Portable Network Graphics (**PNG**) iTXT chunk metadata properties.

### [WICPngSrgbProperties](WICPngSrgbProperties)

Specifies the Portable Network Graphics (**PNG**) sRGB chunk metadata properties.

### [WICPngTimeProperties](WICPngTimeProperties)

Specifies the Portable Network Graphics (**PNG**) tIME chunk metadata properties.

### [WICProgressNotification](WICProgressNotification)

Specifies when the progress notification callback should be called.

### [WICProgressOperation](WICProgressOperation)

Specifies the progress operations to receive notifications for.

### [WICRawCapabilities](WICRawCapabilities)

Specifies the capability support of a raw image.

### [WICRawParameterSet](WICRawParameterSet)

Specifies the parameter set used by a raw codec.

### [WICRawRenderMode](WICRawRenderMode)

Specifies the render intent of the next CopyPixels call.

### [WICRawRotationCapabilities](WICRawRotationCapabilities)

Specifies the rotation capabilities of the codec.

### [WICSectionAccessLevel](WICSectionAccessLevel)

Specifies the access level of a Windows Graphics Device Interface (**GDI**) section.

### [WICTiffCompressionOption](WICTiffCompressionOption)

Specifies the Tagged Image File Format (**TIFF**) compression options.

### [WICWebpAnimProperties](WICWebpAnimProperties)

Specifies the animation properties of a WebP image.

### [WICWebpAnmfProperties](WICWebpAnmfProperties)

Specifies the animation frame properties of a WebP image.
