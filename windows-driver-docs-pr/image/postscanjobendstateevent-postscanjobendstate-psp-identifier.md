---
title: PostScanJobEndStateEvent.PostScanJobEndState.PSP\_Identifier
description: PostScanJobEndStateEvent.PostScanJobEndState.PSP\_Identifier
ms.assetid: 57b7f75a-b2ef-4d8a-a620-82348b6d28e5
keywords: ["PostScanJobEndStateEvent.PostScanJobEndState.PSP_Identifier"]
ms.author: windowsdriverdev
ms.date: 11/28/2017
ms.topic: article
ms.prod: windows-hardware
ms.technology: windows-devices
---

# PostScanJobEndStateEvent.PostScanJobEndState.PSP\_Identifier


The **PSP\_Identifier** element contains an identifier for a scan process.

To create a post-scan job, a DSM device sends a **CreatePostScanJobRequest** message to a DSM scan server. This message contains a **PSP\_Identifier** element to identify the scan process for the scan server to use to create the post-scan job. The scan process specifies how the job is to process the image data that it receives from the device.

When an IT administrator creates a scan process, the scan-management console (SMC) generates a GUID value to uniquely identify the scan process. A **PSP\_Identifier** element contains this GUID value.

In contrast to a **PSP\_Identifier** element, which identifies a scan process, a **JobToken** element identifies a post-scan job. A post-scan job is an instance of a scan process.

This element has no sub-elements.

 

 

[Send comments about this topic to Microsoft](mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bimage\image%5D:%20PostScanJobEndStateEvent.PostScanJobEndState.PSP_Identifier%20%20RELEASE:%20%2811/8/2017%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "Send comments about this topic to Microsoft")




