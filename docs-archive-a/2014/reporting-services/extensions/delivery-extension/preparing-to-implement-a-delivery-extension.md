---
title: 准备实现传递扩展插件 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- interfaces [Reporting Services]
- delivery extensions [Reporting Services], implementing
ms.assetid: aee1608d-374f-4ad3-bc23-fe07fdaa52b7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bbf98286e6ed35542d8117b4b87b5ff3425def69
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591782"
---
# <a name="preparing-to-implement-a-delivery-extension"></a><span data-ttu-id="66f8b-102">准备实现传递扩展插件</span><span class="sxs-lookup"><span data-stu-id="66f8b-102">Preparing to Implement a Delivery Extension</span></span>
  <span data-ttu-id="66f8b-103">在实现 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 传递扩展插件之前，应定义要实现的接口。</span><span class="sxs-lookup"><span data-stu-id="66f8b-103">Before you implement your [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] delivery extension, you should define the interfaces to implement.</span></span> <span data-ttu-id="66f8b-104">首先需要确定使用传递扩展插件的方式、传递扩展插件需要哪些设置以及为传递报表通知而需要实现的特定功能。</span><span class="sxs-lookup"><span data-stu-id="66f8b-104">You first need to decide how your delivery extension will be used, what settings your delivery extension will require, and the specific functionality you will need to implement in order to deliver report notifications.</span></span>  
  
 <span data-ttu-id="66f8b-105">每个 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 传递扩展插件都必须提供以下功能：</span><span class="sxs-lookup"><span data-stu-id="66f8b-105">Each [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] delivery extension must provide the following functionality:</span></span>  
  
-   <span data-ttu-id="66f8b-106"><xref:Microsoft.ReportingServices.Interfaces.IExtension> 接口实现，它表示此扩展插件和本地化的扩展插件名称。</span><span class="sxs-lookup"><span data-stu-id="66f8b-106">An <xref:Microsoft.ReportingServices.Interfaces.IExtension> interface implementation that represents the extension and a localized extension name.</span></span>  
  
-   <span data-ttu-id="66f8b-107"><xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> 实现，它创建可用来向最终用户传递报表通知的传递扩展插件。</span><span class="sxs-lookup"><span data-stu-id="66f8b-107">An <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> implementation that creates a delivery extension that can be used to deliver report notifications to end users.</span></span>  
  
-   <span data-ttu-id="66f8b-108">为订阅处理特定用户数据的功能。</span><span class="sxs-lookup"><span data-stu-id="66f8b-108">The ability to process specific user data for a subscription.</span></span>  
  
 <span data-ttu-id="66f8b-109">可以增强每个传递扩展插件以包含以下功能：</span><span class="sxs-lookup"><span data-stu-id="66f8b-109">Each delivery extension can be enhanced to include the following functionality:</span></span>  
  
-   <span data-ttu-id="66f8b-110">[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 用户控件实现，它使最终用户能够使用报表管理器创建使用传递扩展插件的报表订阅。</span><span class="sxs-lookup"><span data-stu-id="66f8b-110">An [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] user control implementation that enables end users to use Report Manager to create report subscriptions that use the delivery extension.</span></span>  
  
 <span data-ttu-id="66f8b-111">下表介绍传递扩展插件的可用接口和类。</span><span class="sxs-lookup"><span data-stu-id="66f8b-111">The following table describes the available interfaces and classes for delivery extensions.</span></span>  
  
|<span data-ttu-id="66f8b-112">接口或类</span><span class="sxs-lookup"><span data-stu-id="66f8b-112">Interface or class</span></span>|<span data-ttu-id="66f8b-113">说明</span><span class="sxs-lookup"><span data-stu-id="66f8b-113">Description</span></span>|  
|------------------------|-----------------|  
|<span data-ttu-id="66f8b-114"><xref:Microsoft.ReportingServices.Interfaces.IExtension> 接口</span><span class="sxs-lookup"><span data-stu-id="66f8b-114"><xref:Microsoft.ReportingServices.Interfaces.IExtension> Interface</span></span>|<span data-ttu-id="66f8b-115">表示 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中的一个扩展插件。</span><span class="sxs-lookup"><span data-stu-id="66f8b-115">Represents an extension in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>|  
|<span data-ttu-id="66f8b-116"><xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> 接口</span><span class="sxs-lookup"><span data-stu-id="66f8b-116"><xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> Interface</span></span>|<span data-ttu-id="66f8b-117">表示 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中的一个传递扩展插件。</span><span class="sxs-lookup"><span data-stu-id="66f8b-117">Represents a delivery extension in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>|  
|<span data-ttu-id="66f8b-118"><xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation> 接口</span><span class="sxs-lookup"><span data-stu-id="66f8b-118"><xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation> Interface</span></span>|<span data-ttu-id="66f8b-119">包含传递扩展插件所需的有关报表服务器的信息（例如，可用呈现扩展插件的列表）。</span><span class="sxs-lookup"><span data-stu-id="66f8b-119">Contains information about the report server that is required by delivery extensions (for example, a list of the available rendering extensions).</span></span>|  
|<span data-ttu-id="66f8b-120"><xref:Microsoft.ReportingServices.Interfaces.Setting> 类</span><span class="sxs-lookup"><span data-stu-id="66f8b-120"><xref:Microsoft.ReportingServices.Interfaces.Setting> Class</span></span>|<span data-ttu-id="66f8b-121">表示扩展插件的设置。</span><span class="sxs-lookup"><span data-stu-id="66f8b-121">Represents a setting for an extension.</span></span>|  
|<span data-ttu-id="66f8b-122"><xref:Microsoft.ReportingServices.Interfaces.Notification> 类</span><span class="sxs-lookup"><span data-stu-id="66f8b-122"><xref:Microsoft.ReportingServices.Interfaces.Notification> Class</span></span>|<span data-ttu-id="66f8b-123">包含传递扩展插件用于传递报表的订阅信息。</span><span class="sxs-lookup"><span data-stu-id="66f8b-123">Contains subscription information that delivery extensions use to deliver reports.</span></span>|  
|<span data-ttu-id="66f8b-124"><xref:Microsoft.ReportingServices.Interfaces.Report> 类</span><span class="sxs-lookup"><span data-stu-id="66f8b-124"><xref:Microsoft.ReportingServices.Interfaces.Report> Class</span></span>|<span data-ttu-id="66f8b-125">表示报表特定的信息以及使传递扩展插件能够向用户传递报表的方法。</span><span class="sxs-lookup"><span data-stu-id="66f8b-125">Represents report-specific information and methods that enable delivery extensions to deliver reports to users.</span></span>|  
|<span data-ttu-id="66f8b-126"><xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> 类</span><span class="sxs-lookup"><span data-stu-id="66f8b-126"><xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> Class</span></span>|<span data-ttu-id="66f8b-127">表示来自呈现扩展插件的输出。</span><span class="sxs-lookup"><span data-stu-id="66f8b-127">Represents the output from a rendering extension.</span></span> <span data-ttu-id="66f8b-128"><xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> 对象包含关联的文件名和类型信息，传递扩展插件需要这些信息以处理由呈现扩展插件返回的流。</span><span class="sxs-lookup"><span data-stu-id="66f8b-128">A <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> object contains the associated file name and type information that is required by the delivery extension in order to process the stream returned by the rendering extension.</span></span>|  
|<span data-ttu-id="66f8b-129"><xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> 接口</span><span class="sxs-lookup"><span data-stu-id="66f8b-129"><xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> Interface</span></span>|<span data-ttu-id="66f8b-130">一个用户控件，表示在报表管理器中从用户检索传递扩展插件特定的订阅信息的方法（例如，电子邮件地址或指向文件共享的路径）。</span><span class="sxs-lookup"><span data-stu-id="66f8b-130">A user control that represents the means to retrieve delivery extension-specific subscription information from the user in Report Manager (for example, an e-mail address or the path to a file share).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="66f8b-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="66f8b-131">See Also</span></span>  
 <span data-ttu-id="66f8b-132">[Reporting Services 扩展插件](../reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="66f8b-132">[Reporting Services Extensions](../reporting-services-extensions.md) </span></span>  
 <span data-ttu-id="66f8b-133">[实现传递扩展插件](implementing-a-delivery-extension.md) </span><span class="sxs-lookup"><span data-stu-id="66f8b-133">[Implementing a Delivery Extension](implementing-a-delivery-extension.md) </span></span>  
 [<span data-ttu-id="66f8b-134">Reporting Services 扩展插件库</span><span class="sxs-lookup"><span data-stu-id="66f8b-134">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
