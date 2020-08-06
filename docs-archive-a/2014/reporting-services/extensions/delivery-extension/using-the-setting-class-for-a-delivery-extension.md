---
title: 将 Setting 类用于传递扩展插件 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- delivery extensions [Reporting Services], settings
- Setting class
ms.assetid: 50746639-da7c-46a5-ac7b-e87dd6b91880
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 594cf28391ae4523e1a95ad79ee5b1280ff72218
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687528"
---
# <a name="using-the-setting-class-for-a-delivery-extension"></a><span data-ttu-id="1aea8-102">将 Setting 类用于传递扩展插件</span><span class="sxs-lookup"><span data-stu-id="1aea8-102">Using the Setting Class for a Delivery Extension</span></span>
  <span data-ttu-id="1aea8-103"><xref:Microsoft.ReportingServices.Interfaces.Setting> 类位于 <xref:Microsoft.ReportingServices.Interfaces> 命名空间中，表示与传递扩展插件的扩展插件设置有关的信息。</span><span class="sxs-lookup"><span data-stu-id="1aea8-103">The <xref:Microsoft.ReportingServices.Interfaces.Setting> class is located in the <xref:Microsoft.ReportingServices.Interfaces> namespace and represents information about extension settings for a delivery extension.</span></span> <span data-ttu-id="1aea8-104"><xref:Microsoft.ReportingServices.Interfaces.Setting> 类提供了基础结构，用于存储与为使传递扩展插件正常工作所需的设置有关的信息。</span><span class="sxs-lookup"><span data-stu-id="1aea8-104">The <xref:Microsoft.ReportingServices.Interfaces.Setting> class provides infrastructure for storing information about the settings that are required in order for a delivery extension to function properly.</span></span> <span data-ttu-id="1aea8-105">例如，在报表服务器电子邮件传递中，要求某一用户提供特定于电子邮件传递的设置，例如收件人的地址、发件人的地址、电子邮件的标题行等。</span><span class="sxs-lookup"><span data-stu-id="1aea8-105">For example, in Report Server E-Mail delivery, a user is required to supply settings specific to e-mail delivery, such as the recipient's address, the sender's address, the subject line of the e-mail, and more.</span></span> <span data-ttu-id="1aea8-106">毋庸置疑，您的自定义传递提供程序将要求用户提供特定设置，以便传递扩展插件可以提供通知和报表。</span><span class="sxs-lookup"><span data-stu-id="1aea8-106">Undoubtedly, your custom delivery providers will require the user to supply specific settings in order for the delivery extension to deliver notifications and reports.</span></span>  
  
 <span data-ttu-id="1aea8-107">在实现 <xref:Microsoft.ReportingServices.Interfaces.Setting> 接口的 <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ExtensionSettings%2A> 属性时，使用 <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> 类。</span><span class="sxs-lookup"><span data-stu-id="1aea8-107">The <xref:Microsoft.ReportingServices.Interfaces.Setting> class is used when implementing the <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ExtensionSettings%2A> property of the <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> interface.</span></span> <span data-ttu-id="1aea8-108"><xref:Microsoft.ReportingServices.Interfaces.Setting> 类还用于处理用户在创建订阅或通知时提供的扩展插件设置数据。</span><span class="sxs-lookup"><span data-stu-id="1aea8-108">The <xref:Microsoft.ReportingServices.Interfaces.Setting> class is also used for processing the extension setting data that is supplied by a user when a subscription or notification is created.</span></span>  
  
 <span data-ttu-id="1aea8-109">有关如何使用 <xref:Microsoft.ReportingServices.Interfaces.Setting> 类的示例，请参阅 [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889)（SQL Server Reporting Services 产品示例）。</span><span class="sxs-lookup"><span data-stu-id="1aea8-109">For an example of how to use the <xref:Microsoft.ReportingServices.Interfaces.Setting> class, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1aea8-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1aea8-110">See Also</span></span>  
 <span data-ttu-id="1aea8-111">[实现传递扩展插件](implementing-a-delivery-extension.md) </span><span class="sxs-lookup"><span data-stu-id="1aea8-111">[Implementing a Delivery Extension](implementing-a-delivery-extension.md) </span></span>  
 [<span data-ttu-id="1aea8-112">Reporting Services 扩展插件库</span><span class="sxs-lookup"><span data-stu-id="1aea8-112">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
