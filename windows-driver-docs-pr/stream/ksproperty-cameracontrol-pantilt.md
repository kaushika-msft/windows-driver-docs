---
title: KSPROPERTY\_CAMERACONTROL\_PANTILT
description: The KSPROPERTY\_CAMERACONTROL\_PANTILT property specifies absolute pan and tilt settings.
MS-HAID:
- 'vidcapprop\_72427924-365f-4eea-85e9-b6428b0dded4.xml'
- 'stream.ksproperty\_cameracontrol\_pantilt'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: d6f151c9-a428-4d76-9854-5064d901643e
keywords: ["KSPROPERTY_CAMERACONTROL_PANTILT Streaming Media Devices"]
topic_type:
- apiref
api_name:
- KSPROPERTY_CAMERACONTROL_PANTILT
api_location:
- Ksmedia.h
api_type:
- HeaderDef
---

# KSPROPERTY\_CAMERACONTROL\_PANTILT


The KSPROPERTY\_CAMERACONTROL\_PANTILT property specifies absolute pan and tilt settings.

## <span id="ddk_ksproperty_cameracontrol_pantilt_ks"></span><span id="DDK_KSPROPERTY_CAMERACONTROL_PANTILT_KS"></span>


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
<td><p>Yes</p></td>
<td><p>Filter or node</p></td>
<td><p>[<strong>KSPROPERTY_CAMERACONTROL_S2</strong>](https://msdn.microsoft.com/library/windows/hardware/ff564451) or [<strong>KSPROPERTY_CAMERACONTROL_NODE_S2</strong>](https://msdn.microsoft.com/library/windows/hardware/ff564421) depending on whether the request is for a filter or a node</p></td>
<td><p>Pair of LONG integers</p></td>
</tr>
</tbody>
</table>

 

The property value (operation data) is a pair of LONG integers that specify a camera's absolute pan and tilt settings. These values are expressed in arc-second units.

One arc second is 1/3600 of a degree. Acceptable values range from −180\*3600 to +180\*3600 arc seconds. If a pan or tilt value is not provided, the default is 0.

When making a pan request, specify a positive value to rotate the camera to the right and specify a negative value to rotate the camera to the left.

When making a tilt request, a positive value tilts the camera up and a negative value tilts the camera down.

Remarks
-------

The **Value1** member of the [**KSPROPERTY\_CAMERACONTROL\_S2**](https://msdn.microsoft.com/library/windows/hardware/ff564451) or [**KSPROPERTY\_CAMERACONTROL\_NODE\_S2**](https://msdn.microsoft.com/library/windows/hardware/ff564421) structures specifies the pan setting. The **Value2** member specifies the tilt setting.

Requirements
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Version</p></td>
<td><p>Available for Windows Vista and later versions of the Windows operating system.</p></td>
</tr>
<tr class="even">
<td><p>Header</p></td>
<td>Ksmedia.h (include Ksmedia.h)</td>
</tr>
</tbody>
</table>

## <span id="see_also"></span>See also


[**KSPROPERTY\_CAMERACONTROL\_S2**](https://msdn.microsoft.com/library/windows/hardware/ff564451)

[**KSPROPERTY\_CAMERACONTROL\_NODE\_S2**](https://msdn.microsoft.com/library/windows/hardware/ff564421)

 

 

[Send comments about this topic to Microsoft](mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bstream\stream%5D:%20KSPROPERTY_CAMERACONTROL_PANTILT%20%20RELEASE:%20%2811/22/2017%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "Send comments about this topic to Microsoft")




