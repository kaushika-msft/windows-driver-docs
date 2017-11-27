---
title: KSPROPERTY\_CAMERACONTROL\_EXTENDED\_FLASHMODE
description: The flash property control sets flash mode operation for both normal and sequence photo mode of the camera.
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: A190CB91-0AC4-4ECC-8C55-F0C48CF7B190
keywords: ["KSPROPERTY_CAMERACONTROL_EXTENDED_FLASHMODE Streaming Media Devices"]
topic_type:
- apiref
api_name:
- KSPROPERTY_CAMERACONTROL_EXTENDED_FLASHMODE
api_location:
- Ksmedia.h
api_type:
- HeaderDef
---

# KSPROPERTY\_CAMERACONTROL\_EXTENDED\_FLASHMODE


The flash property control sets flash mode operation for both normal and sequence photo mode of the camera.

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
<td><p>Filter</p></td>
<td><p>[<strong>KSPROPERTY</strong>](https://msdn.microsoft.com/library/windows/hardware/ff564262)</p></td>
<td><p>[<strong>KSCAMERA_EXTENDEDPROP_HEADER</strong>](https://msdn.microsoft.com/library/windows/hardware/dn567563)</p></td>
</tr>
</tbody>
</table>

 

The property value (operation data) contains a [**KSCAMERA\_EXTENDEDPROP\_HEADER**](https://msdn.microsoft.com/library/windows/hardware/dn567563) structure and a [**KSCAMERA\_EXTENDEDPROP\_VALUE**](https://msdn.microsoft.com/library/windows/hardware/dn567564) structure.

The total property data size is **sizeof**(KSCAMERA\_EXTENDEDPROP\_HEADER) + **sizeof**(KSCAMERA\_EXTENDEDPROP\_VALUE). The **Size** member of [**KSCAMERA\_EXTENDEDPROP\_HEADER**](https://msdn.microsoft.com/library/windows/hardware/dn567563) is set to this total property data size.

The **Capability** member of [**KSCAMERA\_EXTENDEDPROP\_HEADER**](https://msdn.microsoft.com/library/windows/hardware/dn567563) contains a bitwise OR combination of one or more of the following flash modes that are supported by the driver.

| Flash mode                                           | Description                                                                |
|------------------------------------------------------|----------------------------------------------------------------------------|
| KSCAMERA\_EXTENDEDPROP\_FLASH\_OFF                   | Flash is off.                                                              |
| KSCAMERA\_EXTENDEDPROP\_FLASH\_ON                    | Flash is on at the default intensity level.                                |
| KSCAMERA\_EXTENDEDPROP\_FLASH\_ON\_ADJUSTABLEPOWER   | Flash is on at a specific power level.                                     |
| KSCAMERA\_EXTENDEDPROP\_FLASH\_AUTO                  | Flash is automatic based on lighting conditions.                           |
| KSCAMERA\_EXTENDEDPROP\_FLASH\_AUTO\_ADJUSTABLEPOWER | Flash is automatic based on lighting conditions at a specific power level. |

 

The following feature flags can be combined with the previous flash settings except for KSCAMERA\_EXTENDEDPROP\_FLASH\_OFF.

| Flash feature                                      | Description                                                                                                          |
|----------------------------------------------------|----------------------------------------------------------------------------------------------------------------------|
| KSCAMERA\_EXTENDEDPROP\_FLASH\_REDEYEREDUCTION     | Enable redeye reduction feature. This flag can be combined with any other setting.                                   |
| KSCAMERA\_EXTENDEDPROP\_FLASH\_SINGLEFLASH         | Set flash for only one trigger. This feature is ignored when the camera is not in photo sequence mode.               |
| KSCAMERA\_EXTENDEDPROP\_FLASH\_MULTIFLASHSUPPORTED | Set flash to trigger on every sequence frame. This feature is ignored when the camera is not in photo sequence mode. |

 

The **Flags** member of [**KSCAMERA\_EXTENDEDPROP\_HEADER**](https://msdn.microsoft.com/library/windows/hardware/dn567563) contains the flash mode currently set for the camera.

The default flash mode for a camera is KSCAMERA\_EXTENDEDPROP\_FLASH\_OFF. If the camera supports flash, KSCAMERA\_EXTENDEDPROP\_FLASH\_OFF, KSCAMERA\_EXTENDEDPROP\_FLASH\_ON, and KSCAMERA\_EXTENDEDPROP\_FLASH\_AUTO are required modes. The KSCAMERA\_EXTENDEDPROP\_FLASH\_AUTO\_ADJUSTABLEPOWER and KSCAMERA\_EXTENDEDPROP\_FLASH\_AUTO\_ADJUSTABLEPOWER modes are optional.

If photo sequence mode is supported by the camera, the flash control property is required with support for KSCAMERA\_EXTENDEDPROP\_FLASH\_SINGLEFLASH.

This property control is synchronous.

Remarks
-------

### <span id="Getting_the_property"></span><span id="getting_the_property"></span><span id="GETTING_THE_PROPERTY"></span>Getting the property

When responding to a KSPROPERTY\_TYPE\_GET request, the driver sets the members of the [**KSCAMERA\_EXTENDEDPROP\_HEADER**](https://msdn.microsoft.com/library/windows/hardware/dn567563) to the following.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Member</th>
<th>Value</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Version</td>
<td>1</td>
</tr>
<tr class="even">
<td>PinId</td>
<td>KSCAMERA_EXTENDEDPROP_FILTERSCOPE (0xFFFFFFFF).</td>
</tr>
<tr class="odd">
<td>Size</td>
<td><p>sizeof(KSCAMERA_EXTENDEDPROP_HEADER) + sizeof(KSCAMERA_EXTENDEDPROP_VALUE)</p></td>
</tr>
<tr class="even">
<td>Result</td>
<td>0</td>
</tr>
<tr class="odd">
<td>Capability</td>
<td>Flash mode values supported.</td>
</tr>
<tr class="even">
<td>Flags</td>
<td>(The current flash mode value setting) | (flash feature flags)</td>
</tr>
</tbody>
</table>

 

When the torch mode is KSCAMERA\_EXTENDEDPROP\_FLASH\_ON\_ADJUSTABLEPOWER or KSCAMERA\_EXTENDEDPROP\_FLASH\_ON\_ADJUSTABLEPOWER, the **Value.ull** member of [**KSCAMERA\_EXTENDEDPROP\_VALUE**](https://msdn.microsoft.com/library/windows/hardware/dn567564) contains an intensity level value between 0 - 100. An intensity of 0 indicates a minimum level and an intensity of 100 indicates a maximum intensity level. When the adjustable power flags are not set, the value for the normalized intensity setting is returned in **Value.ull**.

If no flash mode was previously set, then **Flags** is set to KSCAMERA\_EXTENDEDPROP\_FLASH\_OFF (default).

### <span id="Setting_the_property"></span><span id="setting_the_property"></span><span id="SETTING_THE_PROPERTY"></span>Setting the property

When the property is set, a KSPROPERTY\_TYPE\_SET request, the **Flags** member of [**KSCAMERA\_EXTENDEDPROP\_HEADER**](https://msdn.microsoft.com/library/windows/hardware/dn567563) will contain the torch mode to set. The **Value.ull** member of [**KSCAMERA\_EXTENDEDPROP\_VALUE**](https://msdn.microsoft.com/library/windows/hardware/dn567564) will contain the intensity level to set if **Flags** is KSCAMERA\_EXTENDEDPROP\_FLASH\_ON\_ADJUSTABLEPOWER or KSCAMERA\_EXTENDEDPROP\_FLASH\_AUTO\_ADJUSTABLEPOWER.

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
<td><p>Available starting with Windows 8.1.</p></td>
</tr>
<tr class="even">
<td><p>Header</p></td>
<td>Ksmedia.h (include Ksmedia.h)</td>
</tr>
</tbody>
</table>

## <span id="see_also"></span>See also


[**KSCAMERA\_EXTENDEDPROP\_HEADER**](https://msdn.microsoft.com/library/windows/hardware/dn567563)

[**KSCAMERA\_EXTENDEDPROP\_VALUE**](https://msdn.microsoft.com/library/windows/hardware/dn567564)

 

 

[Send comments about this topic to Microsoft](mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bstream\stream%5D:%20KSPROPERTY_CAMERACONTROL_EXTENDED_FLASHMODE%20%20RELEASE:%20%2811/22/2017%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "Send comments about this topic to Microsoft")




