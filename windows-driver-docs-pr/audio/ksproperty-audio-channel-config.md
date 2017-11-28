---
title: KSPROPERTY\_AUDIO\_CHANNEL\_CONFIG
description: The KSPROPERTY\_AUDIO\_CHANNEL\_CONFIG property specifies the actual spatial placement of channels in the audio stream that a node outputs.
ms.assetid: 5ce9bf4a-c84e-4d7e-8e75-896c88ec1a72
keywords: ["KSPROPERTY_AUDIO_CHANNEL_CONFIG Audio Devices"]
topic_type:
- apiref
api_name:
- KSPROPERTY_AUDIO_CHANNEL_CONFIG
api_location:
- Ksmedia.h
api_type:
- HeaderDef
---

# KSPROPERTY\_AUDIO\_CHANNEL\_CONFIG


The KSPROPERTY\_AUDIO\_CHANNEL\_CONFIG property specifies the actual spatial placement of channels in the audio stream that a node outputs.

## <span id="ddk_ksproperty_audio_channel_config_ks"></span><span id="DDK_KSPROPERTY_AUDIO_CHANNEL_CONFIG_KS"></span>


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
<th align="left">Get</th>
<th align="left">Set</th>
<th align="left">Target</th>
<th align="left">Property descriptor type</th>
<th align="left">Property value type</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Yes</p></td>
<td align="left"><p>Yes</p></td>
<td align="left"><p>Filter/Pin</p></td>
<td align="left">[<strong>KSNODEPROPERTY</strong>](https://msdn.microsoft.com/library/windows/hardware/ff537143)</td>
<td align="left"><p>[<strong>KSAUDIO_CHANNEL_CONFIG</strong>](https://msdn.microsoft.com/library/windows/hardware/ff537083)</p></td>
</tr>
</tbody>
</table>

 

The property value (operation data) is a structure of type KSAUDIO\_CHANNEL\_CONFIG. This structure specifies the channels that are contained in the output stream and the assignment of those channels to speakers.

### <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value

A KSPROPERTY\_AUDIO\_CHANNEL\_CONFIG property request returns STATUS\_SUCCESS to indicate that it has completed successfully. Otherwise, the request returns an appropriate error status code.

Remarks
-------

When used as a property of a DAC node ([**KSNODETYPE\_DAC**](ksnodetype-dac.md)) or 3D node ([**KSNODETYPE\_3D\_EFFECTS**](ksnodetype-3d-effects.md)), the KSPROPERTY\_AUDIO\_CHANNEL\_CONFIG property specifies the DirectSound speaker configuration. For stereo speaker configurations, this property is used in conjunction with the [**KSPROPERTY\_AUDIO\_STEREO\_SPEAKER\_GEOMETRY**](ksproperty-audio-stereo-speaker-geometry.md) property, which distinguishes between headphones and several stereo speaker configurations. For more information about speaker configurations, see [DirectSound Speaker-Configuration Settings](https://msdn.microsoft.com/library/windows/hardware/ff536332).

DirectSound also uses the KSPROPERTY\_AUDIO\_CHANNEL\_CONFIG property to query a "pan" node for its channel configuration. A pan node is the second volume node ([**KSNODETYPE\_VOLUME**](ksnodetype-volume.md)) on a mixer pin that meets the [DirectSound node-ordering requirements](https://msdn.microsoft.com/library/windows/hardware/ff536331). DirectSound implementation of the **IDirectSoundBuffer::SetPan** method (described in the Microsoft Windows SDK documentation) uses the pan node's [**KSPROPERTY\_AUDIO\_VOLUMELEVEL**](ksproperty-audio-volumelevel.md) property to control panning.

DirectSound treats KSPROPERTY\_AUDIO\_CHANNEL\_CONFIG as a filter property on a DAC node, and as a pin property on volume and 3D nodes.

Clients also use this property to select the format of the stream that a [**KSNODETYPE\_PROLOGIC\_DECODER**](ksnodetype-prologic-decoder.md) node outputs.

Requirements
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p>Header</p></td>
<td align="left">Ksmedia.h (include Ksmedia.h)</td>
</tr>
</tbody>
</table>

## <span id="see_also"></span>See also


[**KSNODEPROPERTY**](https://msdn.microsoft.com/library/windows/hardware/ff537143)

[**KSAUDIO\_CHANNEL\_CONFIG**](https://msdn.microsoft.com/library/windows/hardware/ff537083)

[**KSNODETYPE\_DAC**](ksnodetype-dac.md)

[**KSNODETYPE\_3D\_EFFECTS**](ksnodetype-3d-effects.md)

[**KSNODETYPE\_VOLUME**](ksnodetype-volume.md)

[**KSNODETYPE\_PROLOGIC\_DECODER**](ksnodetype-prologic-decoder.md)

[**KSPROPERTY\_AUDIO\_STEREO\_SPEAKER\_GEOMETRY**](ksproperty-audio-stereo-speaker-geometry.md)

[**KSPROPERTY\_AUDIO\_VOLUMELEVEL**](ksproperty-audio-volumelevel.md)

 

 

[Send comments about this topic to Microsoft](mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20[audio\audio]:%20KSPROPERTY_AUDIO_CHANNEL_CONFIG%20%20RELEASE:%20%2811/22/2017%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "Send comments about this topic to Microsoft")




