---
title: WIA\_IPS\_MAXIMUM\_PATCH\_CODES\_PER\_PAGE
description: The WIA\_IPS\_MAXIMUM\_PATCH\_CODES\_PER\_PAGE property describes the maximum number of patch codes that the device can and should detect on one document page side when patch code detection is enabled.
ms.assetid: 91A0DAC0-D8F3-48BB-9DD4-AF50BD8F09AB
keywords: ["WIA_IPS_MAXIMUM_PATCH_CODES_PER_PAGE Imaging Devices"]
topic_type:
- apiref
api_name:
- WIA_IPS_MAXIMUM_PATCH_CODES_PER_PAGE
api_location:
- Wiadef.h
api_type:
- HeaderDef
ms.author: windowsdriverdev
ms.date: 11/28/2017
ms.topic: article
ms.prod: windows-hardware
ms.technology: windows-devices
---

# WIA\_IPS\_MAXIMUM\_PATCH\_CODES\_PER\_PAGE


The **WIA\_IPS\_MAXIMUM\_PATCH\_CODES\_PER\_PAGE** property describes the maximum number of patch codes that the device can and should detect on one document page side when patch code detection is enabled.

## <span id="ddk_wia_ipa_depth_si"></span><span id="DDK_WIA_IPA_DEPTH_SI"></span>


Property Type: VT\_I4

Valid Values: WIA\_PROP\_RANGE

Access Rights: Read/Write

Remarks
-------

A value of 0 means "no maximum". The application can decrease the current value of this property in order to reduce the time spent on patch code detection and increase the scan speed.

This property is required for all Patch Code Reader items but it can be implemented as a range container containing only the value of 0 (minimum equal with maximum and set to 0, step size of 0).

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
<td>Wiadef.h (include Wiadef.h)</td>
</tr>
</tbody>
</table>

 

 

[Send comments about this topic to Microsoft](mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bimage\image%5D:%20WIA_IPS_MAXIMUM_PATCH_CODES_PER_PAGE%20%20RELEASE:%20%2811/13/2017%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "Send comments about this topic to Microsoft")




