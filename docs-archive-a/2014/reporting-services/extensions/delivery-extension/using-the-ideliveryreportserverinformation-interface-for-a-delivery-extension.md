---
title: 将 IDeliveryReportServerInformation 接口用于传递扩展插件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- IDeliveryReportServerInformation interface
- delivery extensions [Reporting Services], retrieving report server information
ms.assetid: adbce647-18f3-470c-8114-42f8bcc95dc2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 52e137d1a866305ec6435a4940fe98448bce5778
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591774"
---
# <a name="using-the-ideliveryreportserverinformation-interface-for-a-delivery-extension"></a><span data-ttu-id="29215-102">将 IDeliveryReportServerInformation 接口用于传递扩展插件</span><span class="sxs-lookup"><span data-stu-id="29215-102">Using the IDeliveryReportServerInformation Interface for a Delivery Extension</span></span>
  <span data-ttu-id="29215-103"><xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation> 接口公开多个属性，您可以使用这些属性来检索有关报表服务器的信息。</span><span class="sxs-lookup"><span data-stu-id="29215-103">The <xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation> interface exposes several properties that you can use to retrieve information about a report server.</span></span> <span data-ttu-id="29215-104">您可以使用此信息来传递通知和报表。</span><span class="sxs-lookup"><span data-stu-id="29215-104">You can use this information to deliver notifications and reports.</span></span> <span data-ttu-id="29215-105">当实现传递扩展插件类时，您按照 <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ReportServerInformation%2A> 接口的要求实现 <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> 属性。</span><span class="sxs-lookup"><span data-stu-id="29215-105">When implementing your delivery extension class, you implement the <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ReportServerInformation%2A> property as required by the <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> interface.</span></span> <span data-ttu-id="29215-106"><xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ReportServerInformation%2A> 属性返回一个实现 <xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation> 接口的对象。</span><span class="sxs-lookup"><span data-stu-id="29215-106">The <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ReportServerInformation%2A> property returns an object that implements the <xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation> interface.</span></span> <span data-ttu-id="29215-107">从该对象，您可以获得报表服务器当前支持的呈现扩展插件的列表。</span><span class="sxs-lookup"><span data-stu-id="29215-107">From this object you can get a list of rendering extensions currently supported by the report server.</span></span>  
  
 <span data-ttu-id="29215-108">下面的 `for` 循环可用于存储**ArrayList**对象中 Report Server 当前可用的呈现扩展插件的列表。</span><span class="sxs-lookup"><span data-stu-id="29215-108">The following `for` loop could be used to store a list of rendering extensions currently available on the report server in an **ArrayList** object.</span></span>  
  
```vb  
Dim renderFormats As New ArrayList()  
Dim e As Microsoft.ReportingServices.Interfaces.Extension  
For Each e In  ReportServerInformation.RenderingExtension  
   If e.Visible Then  
      renderFormats.Add(e.Name)  
   End If  
Next e  
```  
  
```csharp  
ArrayList renderFormats = new ArrayList();  
foreach (Microsoft.ReportingServices.Interfaces.Extension e in ReportServerInformation.RenderingExtension)  
{   
   if (e.Visible)  
   {  
      renderFormats.Add(e.Name);  
   }  
}  
```  
  
 <span data-ttu-id="29215-109">有关 <xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation> 接口的详细信息，请参阅[将 IDeliveryReportServerInformation 接口用于传递扩展插件](using-the-ideliveryreportserverinformation-interface-for-a-delivery-extension.md)。</span><span class="sxs-lookup"><span data-stu-id="29215-109">For more information about the <xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation> interface, see [Using the IDeliveryReportServerInformation Interface for a Delivery Extension](using-the-ideliveryreportserverinformation-interface-for-a-delivery-extension.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29215-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="29215-110">See Also</span></span>  
 <xref:Microsoft.ReportingServices.Interfaces>   
 <span data-ttu-id="29215-111">[实现传递扩展插件](implementing-a-delivery-extension.md) </span><span class="sxs-lookup"><span data-stu-id="29215-111">[Implementing a Delivery Extension](implementing-a-delivery-extension.md) </span></span>  
 [<span data-ttu-id="29215-112">Reporting Services 扩展插件库</span><span class="sxs-lookup"><span data-stu-id="29215-112">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
