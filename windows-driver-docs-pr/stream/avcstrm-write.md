---
title: AVCSTRM\_WRITE
description: AVCSTRM\_WRITE
MS-HAID:
- 'avcsref\_f0d56c9c-2188-4c75-bae8-1a5ec6ebfbe0.xml'
- 'stream.avcstrm\_write'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: de11778d-21ab-40ae-8e7f-5229acfeea42
keywords: ["AVCSTRM_WRITE Streaming Media Devices"]
topic_type:
- apiref
api_name:
- AVCSTRM_WRITE
api_type:
- NA
---

# AVCSTRM\_WRITE


## <span id="ddk_avcstrm_write_ks"></span><span id="DDK_AVCSTRM_WRITE_KS"></span>


The **AVCSTRM\_WRITE** function code is used to submit a data buffer to be transmitted to the specified stream.

### <span id="i_o_status_block"></span><span id="I_O_STATUS_BLOCK"></span>I/O Status Block

If successful, *avcstrm.sys* sets **Irp-&gt;IoStatus.Status** to STATUS\_SUCCESS.

Possible error return values include:

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Error Status</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>STATUS_DEVICE_REMOVED</p></td>
<td><p>The device corresponding to the <strong>AVCSTRM_READ</strong> operation no longer exists.</p></td>
</tr>
<tr class="even">
<td><p>STATUS_CANCELLED</p></td>
<td><p>The request was unable to be completed.</p></td>
</tr>
<tr class="odd">
<td><p>STATUS_INVALID_PARAMETER</p></td>
<td><p>A parameter specified in the IRP is incorrect,</p></td>
</tr>
<tr class="even">
<td><p>STATUS_INSUFFICIENT_RESOURCES</p></td>
<td><p>There were not sufficient system resources to complete the request.</p></td>
</tr>
<tr class="odd">
<td><p>STATUS_PENDING</p></td>
<td><p>The request has been received but requires further processing. The I/O completion routine will handle the final response.</p></td>
</tr>
</tbody>
</table>

 

### <span id="comments"></span><span id="COMMENTS"></span>Comments

This function uses the **BufferStruct** member of the **CommandData** union in the AVC\_STREAM\_REQUEST\_BLOCK structure as shown below.

```
typedef struct _AVC_STREAM_REQUEST_BLOCK {
  ULONG  SizeOfThisBlock;
  ULONG  Version;
  AVCSTRM_FUNCTION  Function;
  .
  .
  PVOID AVCStreamContext;
  .
  .
  union _tagCommandData {
    .
    .
    AVCSTRM_BUFFER_STRUCT  BufferStruct;
    .
    .
  } CommandData;
} AVC_STREAM_REQUEST_BLOCK, *PAVC_STREAM_REQUEST_BLOCK;
```

### <span id="requirements"></span><span id="REQUIREMENTS"></span>Requirements

**Headers:** Declared in *avcstrm.h*. Include *avcstrm.h*.

### <span id="avc_stream_request_block_input"></span><span id="AVC_STREAM_REQUEST_BLOCK_INPUT"></span>AVC\_STREAM\_REQUEST\_BLOCK Input

<span id="SizeOfThisBlock__Version_and_Function"></span><span id="sizeofthisblock__version_and_function"></span><span id="SIZEOFTHISBLOCK__VERSION_AND_FUNCTION"></span>**SizeOfThisBlock, Version and Function**  
Use the [**INIT\_AVCSTRM\_HEADER**](https://msdn.microsoft.com/library/windows/hardware/ff560750) macro to initialize these members. Pass **AVCSTRM\_WRITE** in the Request argument of the macro.

<span id="AVCStreamContext"></span><span id="avcstreamcontext"></span><span id="AVCSTREAMCONTEXT"></span>**AVCStreamContext**  
Specifies the stream context (handle) returned by an earlier **AVCSTRM\_OPEN** call that is the target for the data write operation.

<span id="BufferStruct"></span><span id="bufferstruct"></span><span id="BUFFERSTRUCT"></span>**BufferStruct**  
Specifies the buffer the write operation should obtain data from.

A subunit driver must first allocate an IRP and an [**AVC\_STREAM\_REQUEST\_BLOCK**](https://msdn.microsoft.com/library/windows/hardware/ff554194) structure. Next, it should use the [**INIT\_AVCSTRM\_HEADER**](https://msdn.microsoft.com/library/windows/hardware/ff560750) macro to initialize the AVC\_STREAM\_REQUEST\_BLOCK structure, passing **AVCSTRM\_READ** as the Request argument to the macro. Next, the subunit driver sets the **AVCStreamContext** member to the stream context (handle) of the stream that is the target of the write data operation. Finally, the subunit driver sets the **BufferStruct** member of the **CommandData** union that describes the buffer the write operation obtains data from.

To send this request, a subunit submits an [**IRP\_MJ\_INTERNAL\_DEVICE\_CONTROL**](https://msdn.microsoft.com/library/windows/hardware/ff550766) IRP with the **IoControlCode** member of the IRP set to [**IOCTL\_AVCSTRM\_CLASS**](https://msdn.microsoft.com/library/windows/hardware/ff560778) and the **Argument1** member of the IRP set to the AVC\_STREAM\_REQUEST\_BLOCK structure that describes the write operation to take place.

This command completes asynchronously. When it is completed, the I/O completion routine set in the IRP is be called.

This function code must be called at IRQL = PASSIVE\_LEVEL.

### <span id="see_also"></span><span id="SEE_ALSO"></span>See Also

[**AVC\_STREAM\_REQUEST\_BLOCK**](https://msdn.microsoft.com/library/windows/hardware/ff554194), [**INIT\_AVCSTRM\_HEADER**](https://msdn.microsoft.com/library/windows/hardware/ff560750), [**IRP\_MJ\_INTERNAL\_DEVICE\_CONTROL**](https://msdn.microsoft.com/library/windows/hardware/ff550766), [**IOCTL\_AVCSTRM\_CLASS**](https://msdn.microsoft.com/library/windows/hardware/ff560778), [**AVCSTRM\_BUFFER\_STRUCT**](https://msdn.microsoft.com/library/windows/hardware/ff554108), [**AVCSTRM\_FUNCTION**](https://msdn.microsoft.com/library/windows/hardware/ff554120)

 

 

[Send comments about this topic to Microsoft](mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bstream\stream%5D:%20AVCSTRM_WRITE%20%20RELEASE:%20%2811/22/2017%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "Send comments about this topic to Microsoft")



