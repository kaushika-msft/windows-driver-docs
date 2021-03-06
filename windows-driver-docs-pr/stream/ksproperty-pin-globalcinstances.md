---
title: KSPROPERTY\_PIN\_GLOBALCINSTANCES
description: The client uses the KSPROPERTY\_PIN\_GLOBALCINSTANCES to determine the current number of pins instantiated by a pin factory, as well as the maximum number of pins this pin factory can instantiate. This property is optional.
ms.assetid: 888b8ddf-aa36-4e2f-a74c-ab4ee693bb36
keywords: ["KSPROPERTY_PIN_GLOBALCINSTANCES Streaming Media Devices"]
topic_type:
- apiref
api_name:
- KSPROPERTY_PIN_GLOBALCINSTANCES
api_location:
- ks.h
api_type:
- HeaderDef
ms.author: windowsdriverdev
ms.date: 11/28/2017
ms.topic: article
ms.prod: windows-hardware
ms.technology: windows-devices
---

# KSPROPERTY\_PIN\_GLOBALCINSTANCES


The client uses the KSPROPERTY\_PIN\_GLOBALCINSTANCES to determine the current number of pins instantiated by a pin factory, as well as the maximum number of pins this pin factory can instantiate. This property is optional.

## <span id="ddk_ksproperty_pin_globalcinstances_ks"></span><span id="DDK_KSPROPERTY_PIN_GLOBALCINSTANCES_KS"></span>


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
<td><p>[<strong>KSP_PIN</strong>](https://msdn.microsoft.com/library/windows/hardware/ff566722)</p></td>
<td><p>KSPIN_CINSTANCES</p></td>
</tr>
</tbody>
</table>

 

Remarks
-------

Specify this property using KSP\_PIN, where the **PinId** member specifies the pin factory.

KSPIN\_CINSTANCES is a data structure of the form:

```
typedef struct {
    ULONG PossibleCount;
    ULONG CurrentCount;
} KSPIN_CINSTANCES;
```

The following is a description of each member of the KSPIN\_CINSTANCES structure.

<span id="PossibleCount"></span><span id="possiblecount"></span><span id="POSSIBLECOUNT"></span>**PossibleCount**  
Specifies the maximum number of pin the pin factory can instantiate on the driver, or KSINTANCE\_INDETERMINATE if there is no maximum.

<span id="CurrentCount"></span><span id="currentcount"></span><span id="CURRENTCOUNT"></span>**CurrentCount**  
Specifies the current number of pins the pin factory has instantiated on the driver.

The class driver does not handle this property; the stream minidriver must provide handling on its own.

KSPROPERTY\_PIN\_GLOBALCINSTANCES specifies the absolute current and maximum number of instances, over all instances of the filter. To determine per-filter values, use [**KSPROPERTY\_PIN\_CINSTANCES**](ksproperty-pin-cinstances.md).

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


[**KSP\_PIN**](https://msdn.microsoft.com/library/windows/hardware/ff566722)

[**KSPROPERTY\_PIN\_CINSTANCES**](ksproperty-pin-cinstances.md)

 

 

[Send comments about this topic to Microsoft](mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bstream\stream%5D:%20KSPROPERTY_PIN_GLOBALCINSTANCES%20%20RELEASE:%20%2811/22/2017%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "Send comments about this topic to Microsoft")





