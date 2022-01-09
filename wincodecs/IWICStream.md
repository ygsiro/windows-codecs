---
layout: interface
category: Interface
title: IWICStream
TOC:
  - name: Inheritance
  - name: Remarks
  - name: InitializeFromFilename
  - name: InitializeFromIStream
  - name: InitializeFromIStreamRegion
  - name: InitializeFromMemory
  - name: Related
code:
  - key: WICInProcPointer
---

Represents a Windows Imaging Component (**WIC**) stream for referencing imaging and metadata content.

## Inheritance

The **IWICStream** interface inherits from IStream.
**IWICStream** also has these types of members:

- [InitializeFromFilename](#initializefromfilename)
- [InitializeFromIStream](#initializefromistream)
- [InitializeFromIStreamRegion](#initializefromistreamregion)
- [InitializeFromMemory](#initializefrommemory)

## Remarks

Decoders and metadata handlers are expected to create sub streams of whatever stream they hold when handing off control for embedded metadata to another metadata handler.
If the stream is not restricted then use **MAXLONGLONG** as the max size and offset 0.

The **IWICStream** interface methods do not enable you to provide a file sharing option.
To create a file stream for an image, use the SHCreateStreamOnFileEx function.
This stream can then be used to create an [IWICBitmapDecoder][wbd] using the CreateDecoderFromStream method.

## InitializeFromFilename

Initializes a stream from a particular file.

```cpp
HRESULT InitializeFromFilename(
    LPCWSTR wzFileName,     // [in]
    DWORD   dwDesiredAccess // [in]
);
```

### InitializeFromFilename - Parameter

1. _wzFileName_ - The file used to initialize the stream.
2. _dwDesiredAccess_ - The desired file access mode.

   | Value         | Meaning       |
   | :------------ | :------------ |
   | GENERIC_READ  | Read access.  |
   | GENERIC_WRITE | Write access. |

### InitializeFromFilename - Return value

If this method succeeds, it returns **S_OK**. Otherwise, it returns an **HRESULT** error code.

### InitializeFromFilename - Remarks

The **IWICStream** interface methods do not enable you to provide a file sharing option.
To create a shared file stream for an image, use the SHCreateStreamOnFileEx function.
This stream can then be used to create an [IWICBitmapDecoder][wbd] using the CreateDecoderFromStream method.

[wbd]: IWICBitmapDecoder

## InitializeFromIStream

Initializes a stream from another stream. Access rights are inherited from the underlying stream.

```cpp
HRESULT InitializeFromIStream(
    IStream *pIStream // [in]
);
```

### InitializeFromIStream - Parameter

1. _pIStream_ - The initialize stream.

### InitializeFromIStream - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

## InitializeFromIStreamRegion

Initializes the stream as a substream of another stream.

```cpp
HRESULT InitializeFromIStreamRegion(
    IStream        *pIStream, // [in]
    ULARGE_INTEGER ulOffset,  // [in]
    ULARGE_INTEGER ulMaxSize  // [in]
);
```

### InitializeFromIStreamRegion - Parameter

1. _pIStream_ - Pointer to the input stream.
2. _ulOffset_ - The stream offset used to create the new stream.
3. _ulMaxSize_ - The maximum size of the stream.

### InitializeFromIStreamRegion - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### InitializeFromIStreamRegion - Remarks

The stream functions with its own stream position, independent of the underlying stream but restricted to a region.
All seek positions are relative to the sub region.
It is allowed, though not recommended, to have multiple writable sub streams overlapping the same range.

## InitializeFromMemory

Initializes a stream to treat a block of memory as a stream.
The stream cannot grow beyond the buffer size.

```cpp
HRESULT InitializeFromMemory(
    WICInProcPointer pbBuffer,    // [in]
    DWORD            cbBufferSize // [in]
);
```

### InitializeFromMemory - Parameter

1. _pbBuffer_ - Pointer to the buffer used to initialize the stream.
2. _cbBufferSize_ - The size of buffer.

### InitializeFromMemory - Return value

If this method succeeds, it returns **S_OK**.
Otherwise, it returns an **HRESULT** error code.

### InitializeFromMemory - Remarks

This method should be avoided whenever possible.
The caller is responsible for ensuring the memory block is valid for the lifetime of the stream when using **InitializeFromMemory**.
A workaround for this behavior is to create an IStream and use [InitializeFromIStream][ifis] to create the **IWICStream**.

[ifis]: #initializefromistream

If you require a growable memory stream, use CreateStreamOnHGlobal.

## Related

- [IWICImagingFactory::CreateStream](IWICImagingFactory#createstream)
