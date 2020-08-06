---
title: 实现传递扩展插件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- delivery [Reporting Services]
- custom delivery extensions [Reporting Services]
- extensions [Reporting Services], delivery
- delivery extensions [Reporting Services]
ms.assetid: 600cd229-efcd-480e-8c95-3c3c39ff4e7a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: af1e804e029dae77fb7836577aa8d4a45ad20109
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591788"
---
# <a name="implementing-a-delivery-extension"></a><span data-ttu-id="38cb8-102">实现传递扩展插件</span><span class="sxs-lookup"><span data-stu-id="38cb8-102">Implementing a Delivery Extension</span></span>
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="38cb8-103">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 使得用户能够创建和发布报表，一旦创建和发布，就可以将报表传递到不同位置。</span><span class="sxs-lookup"><span data-stu-id="38cb8-103">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] enables users to create and publish reports that, once created and published, can be delivered to various locations.</span></span> <span data-ttu-id="38cb8-104">此外，[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 包括多个传递扩展插件和一个传递 API，它们使得开发人员能够创建其他传递扩展插件，以便在 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中进一步扩展传递的功能。</span><span class="sxs-lookup"><span data-stu-id="38cb8-104">In addition, [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] includes several delivery extensions and a delivery API that enable developers to create additional delivery extensions to further extend the functionality of delivery in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="38cb8-105">有关传递扩展插件的示例实现，请参阅 [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889)（SQL Server Reporting Services 产品示例）。</span><span class="sxs-lookup"><span data-stu-id="38cb8-105">For a sample implementation of a delivery extension, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="38cb8-106">本节内容</span><span class="sxs-lookup"><span data-stu-id="38cb8-106">In This Section</span></span>  
 <span data-ttu-id="38cb8-107">[传递扩展插件概述] 传递扩展-overview.md) </span><span class="sxs-lookup"><span data-stu-id="38cb8-107">[Delivery Extensions Overview]delivery-extensions-overview.md)</span></span>  
 <span data-ttu-id="38cb8-108">介绍如何为 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 编写自定义传递扩展插件。</span><span class="sxs-lookup"><span data-stu-id="38cb8-108">Introduces how to write a custom delivery extension for [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="38cb8-109">准备实现传递扩展插件</span><span class="sxs-lookup"><span data-stu-id="38cb8-109">Preparing to Implement a Delivery Extension</span></span>](preparing-to-implement-a-delivery-extension.md)  
 <span data-ttu-id="38cb8-110">介绍在实现 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 传递扩展插件时可用的接口和类，以及在实现前要考虑的问题。</span><span class="sxs-lookup"><span data-stu-id="38cb8-110">Describes the interfaces and classes available when implementing an [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] delivery extension, as well as issues to consider before implementation.</span></span>  
  
 [<span data-ttu-id="38cb8-111">创建传递扩展插件库</span><span class="sxs-lookup"><span data-stu-id="38cb8-111">Creating a Delivery Extension Library</span></span>](creating-a-delivery-extension-library.md)  
 <span data-ttu-id="38cb8-112">介绍如何为 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 传递扩展插件分配命名空间以及如何将传递扩展插件编译成库 DLL。</span><span class="sxs-lookup"><span data-stu-id="38cb8-112">Describes assigning a namespace for your [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] delivery extension and compiling your delivery extension into a library DLL.</span></span>  
  
 [<span data-ttu-id="38cb8-113">为传递扩展插件实现 IDeliveryExtension 接口</span><span class="sxs-lookup"><span data-stu-id="38cb8-113">Implementing the IDeliveryExtension Interface for a Delivery Extension</span></span>](implementing-the-ideliveryextension-interface-for-a-delivery-extension.md)  
 <span data-ttu-id="38cb8-114">介绍传递扩展插件的属性以及如何实现您自己的传递扩展插件类。</span><span class="sxs-lookup"><span data-stu-id="38cb8-114">Describes the attributes of a delivery extension, and how to implement your own delivery extension class.</span></span>  
  
 [<span data-ttu-id="38cb8-115">将通知类用于传递扩展插件</span><span class="sxs-lookup"><span data-stu-id="38cb8-115">Using a Notification Class for a Delivery Extension</span></span>](using-a-notification-class-for-a-delivery-extension.md)  
 <span data-ttu-id="38cb8-116">介绍 Notification 类的属性以及如何在传递扩展插件实现中使用该类  。</span><span class="sxs-lookup"><span data-stu-id="38cb8-116">Describes the attributes of a **Notification** class and how to use it in your delivery extension implementation.</span></span>  
  
 [<span data-ttu-id="38cb8-117">将 Setting 类用于传递扩展插件</span><span class="sxs-lookup"><span data-stu-id="38cb8-117">Using the Setting Class for a Delivery Extension</span></span>](using-the-setting-class-for-a-delivery-extension.md)  
 <span data-ttu-id="38cb8-118">介绍 Setting 类的属性以及如何在传递扩展插件实现中使用该类  。</span><span class="sxs-lookup"><span data-stu-id="38cb8-118">Describes the attributes of a **Setting** class and how to use it in your delivery extension implementation.</span></span>  
  
 [<span data-ttu-id="38cb8-119">将 IDeliveryReportServerInformation 接口用于传递扩展插件</span><span class="sxs-lookup"><span data-stu-id="38cb8-119">Using the IDeliveryReportServerInformation Interface for a Delivery Extension</span></span>](using-the-ideliveryreportserverinformation-interface-for-a-delivery-extension.md)  
 <span data-ttu-id="38cb8-120">介绍 IDeliveryReportServerInformation 接口的属性以及如何在传递扩展插件实现中使用该接口\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="38cb8-120">Describes the attributes of a **IDeliveryReportServerInformation** interface and how to use it in your delivery extension implementation.</span></span>  
  
 [<span data-ttu-id="38cb8-121">将 Report 类用于传递扩展插件</span><span class="sxs-lookup"><span data-stu-id="38cb8-121">Using the Report Class for a Delivery Extension</span></span>](using-the-report-class-for-a-delivery-extension.md)  
 <span data-ttu-id="38cb8-122">介绍 Report 类的属性以及如何在传递扩展插件实现中使用该类\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="38cb8-122">Describes the attributes of a **Report** class and how to use it in your delivery extension implementation.</span></span>  
  
 [<span data-ttu-id="38cb8-123">将 RenderedOutputFile 类用于传递扩展插件</span><span class="sxs-lookup"><span data-stu-id="38cb8-123">Using the RenderedOutputFile Class for a Delivery Extension</span></span>](using-the-renderedoutputfile-class-for-a-delivery-extension.md)  
 <span data-ttu-id="38cb8-124">介绍 RenderedOutputFile 类的属性以及如何在传递扩展插件实现中使用该类\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="38cb8-124">Describes the attributes of a **RenderedOutputFile** class and how to use it in your delivery extension implementation.</span></span>  
  
 [<span data-ttu-id="38cb8-125">为传递扩展插件实现 ISubscriptionBaseUIUserControl 接口</span><span class="sxs-lookup"><span data-stu-id="38cb8-125">Implementing the ISubscriptionBaseUIUserControl Interface for a Delivery Extension</span></span>](implementing-the-isubscriptionbaseuiusercontrol-interface.md)  
 <span data-ttu-id="38cb8-126">介绍传递扩展插件用户控件的属性以及如何实现您自己的用于订阅的用户界面。</span><span class="sxs-lookup"><span data-stu-id="38cb8-126">Describes the attributes of a delivery extension user control and how to implement your own user interface for a subscription.</span></span>  
  
 [<span data-ttu-id="38cb8-127">部署传递扩展插件</span><span class="sxs-lookup"><span data-stu-id="38cb8-127">Deploying a Delivery Extension</span></span>](deploying-a-delivery-extension.md)  
 <span data-ttu-id="38cb8-128">介绍如何部署传递扩展插件。</span><span class="sxs-lookup"><span data-stu-id="38cb8-128">Describes how to deploy your delivery extension.</span></span>  
  
 [<span data-ttu-id="38cb8-129">调试传递扩展插件代码</span><span class="sxs-lookup"><span data-stu-id="38cb8-129">Debugging Delivery Extension Code</span></span>](debugging-delivery-extension-code.md)  
 <span data-ttu-id="38cb8-130">介绍如何调试传递扩展插件中的代码。</span><span class="sxs-lookup"><span data-stu-id="38cb8-130">Describes how to debug code in your delivery extension.</span></span>  
  
 [<span data-ttu-id="38cb8-131">删除传递扩展插件</span><span class="sxs-lookup"><span data-stu-id="38cb8-131">Removing a Delivery Extension</span></span>](removing-a-delivery-extension.md)  
 <span data-ttu-id="38cb8-132">说明如何从报表服务器上删除传递扩展插件。</span><span class="sxs-lookup"><span data-stu-id="38cb8-132">Describes how to remove a delivery extension from a report server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38cb8-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="38cb8-133">See Also</span></span>  
 <span data-ttu-id="38cb8-134">[Reporting Services 扩展](../reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="38cb8-134">[Reporting Services Extensions](../reporting-services-extensions.md) </span></span>  
 [<span data-ttu-id="38cb8-135">Reporting Services 扩展插件库</span><span class="sxs-lookup"><span data-stu-id="38cb8-135">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
