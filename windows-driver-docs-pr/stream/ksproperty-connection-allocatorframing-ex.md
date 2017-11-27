---
title: KSPROPERTY\_CONNECTION\_ALLOCATORFRAMING\_EX
description: AVStream clients use the KSPROPERTY\_CONNECTION\_ALLOCATORFRAMING\_EX property to determine framing requirements for a pin.
MS-HAID:
- 'ks-prop\_a81b5574-dcd6-432d-bd0d-f78ab4b1182d.xml'
- 'stream.ksproperty\_connection\_allocatorframing\_ex'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 7ff1462f-959b-413e-a888-bcf7d251edee
keywords: ["KSPROPERTY_CONNECTION_ALLOCATORFRAMING_EX Streaming Media Devices"]
topic_type:
- apiref
api_name:
- KSPROPERTY_CONNECTION_ALLOCATORFRAMING_EX
api_location:
- ks.h
api_type:
- HeaderDef
---

# KSPROPERTY\_CONNECTION\_ALLOCATORFRAMING\_EX


AVStream clients use the KSPROPERTY\_CONNECTION\_ALLOCATORFRAMING\_EX property to determine framing requirements for a pin.

## <span id="ddk_ksproperty_connection_allocatorframing_ex_ks"></span><span id="DDK_KSPROPERTY_CONNECTION_ALLOCATORFRAMING_EX_KS"></span>


### <span id="Usage_Summary_Table"></span><span id="usage_summary_table"></span><span id="USAGE_SUMMARY_TABLE"></span>Usage Summary Table

<table>
<colgroup>
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
</colgroup>
<thead>
<tr class="header">
<th>Get</th>
<th>Set</th>
<th>Target</th>
<th>Property Descriptor Type</th>
<th>Property Value Type</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Yes</p></td>
<td><p>No</p></td>
<td><p>Pin</p></td>
<td><p>[<strong>KSPROPERTY</strong>](https://msdn.microsoft.com/library/windows/hardware/ff564262)</p></td>
<td><p>[<strong>KSALLOCATOR_FRAMING_EX</strong>](https://msdn.microsoft.com/library/windows/hardware/ff560982)</p></td>
</tr>
</tbody>
</table>

 

Remarks
-------

This property returns a [**KSALLOCATOR\_FRAMING\_EX**](https://msdn.microsoft.com/library/windows/hardware/ff560982), which describes the framing requirements for an AVStream pin.

Minidrivers running under stream class should use [**KSPROPERTY\_CONNECTION\_ALLOCATORFRAMING**](ksproperty-connection-allocatorframing.md).

See [KS Allocators](https://msdn.microsoft.com/library/windows/hardware/ff567257). and [AVStream Allocators](https://msdn.microsoft.com/library/windows/hardware/ff554202).

Requirements
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Header</p></td>
<td>Ks.h (include Ks.h)</td>
</tr>
</tbody>
</table>

## <span id="see_also"></span>See also


[**KSALLOCATOR\_FRAMING\_EX**](https://msdn.microsoft.com/library/windows/hardware/ff560982)

 

 

[Send comments about this topic to Microsoft](mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bstream\stream%5D:%20KSPROPERTY_CONNECTION_ALLOCATORFRAMING_EX%20%20RELEASE:%20%2811/22/2017%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "Send comments about this topic to Microsoft")




