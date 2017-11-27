---
title: KSPROPERTY\_BDA\_CONTROLLING\_PIN\_ID
description: Clients use KSPROPERTY\_BDA\_CONTROLLING\_PIN\_ID to retrieve the controlling pin for a node in the BDA template connection list.
MS-HAID:
- 'bdaref\_7981c343-1782-473d-b568-a619bf2bf2fe.xml'
- 'stream.ksproperty\_bda\_controlling\_pin\_id'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: d40454a3-0938-4efb-8b06-06b599be8b20
keywords: ["KSPROPERTY_BDA_CONTROLLING_PIN_ID Streaming Media Devices"]
topic_type:
- apiref
api_name:
- KSPROPERTY_BDA_CONTROLLING_PIN_ID
api_location:
- Bdamedia.h
api_type:
- HeaderDef
---

# KSPROPERTY\_BDA\_CONTROLLING\_PIN\_ID


Clients use KSPROPERTY\_BDA\_CONTROLLING\_PIN\_ID to retrieve the controlling pin for a node in the BDA template connection list.

## <span id="ddk_ksproperty_bda_controlling_pin_id_ks"></span><span id="DDK_KSPROPERTY_BDA_CONTROLLING_PIN_ID_KS"></span>


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
<th>Property descriptor type</th>
<th>Property value type</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Yes</p></td>
<td><p>No</p></td>
<td><p>Filter</p></td>
<td><p>KSP_BDA_NODE_PIN</p></td>
<td><p>ULONG</p></td>
</tr>
</tbody>
</table>

 

Remarks
-------

The returned value specifies the controlling pin ID.

Nodes are associated with one pin in the filter, either an input pin or an output pin. Nodes can only be accessed through the controlling pin because nodes do not have their own file handle. The network provider can use this property and the KSP\_BDA\_NODE\_PIN structure to query for the controlling pin for each node in the BDA template connection list (KSTOPOLOGY\_CONNECTION or BDA\_TEMPLATE\_CONNECTION array).

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
<td>Bdamedia.h (include Bdamedia.h)</td>
</tr>
</tbody>
</table>

## <span id="see_also"></span>See also


[**BdaPropertyGetControllingPinId**](https://msdn.microsoft.com/library/windows/hardware/ff556480)

[**BDA\_TEMPLATE\_CONNECTION**](https://msdn.microsoft.com/library/windows/hardware/ff556558)

[**KSP\_BDA\_NODE\_PIN**](https://msdn.microsoft.com/library/windows/hardware/ff566716)

[**KSTOPOLOGY\_CONNECTION**](https://msdn.microsoft.com/library/windows/hardware/ff567148)

 

 

[Send comments about this topic to Microsoft](mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bstream\stream%5D:%20KSPROPERTY_BDA_CONTROLLING_PIN_ID%20%20RELEASE:%20%2811/22/2017%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "Send comments about this topic to Microsoft")




