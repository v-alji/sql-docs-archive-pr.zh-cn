---
title: Reporting Services 属性 | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- report servers [Reporting Services], properties
- properties [Reporting Services], about properties
- reports [Reporting Services], properties
- Report Server Web service, properties
- report properties [Reporting Services]
- XML Web service [Reporting Services], properties
- Web service [Reporting Services], properties
- properties [Reporting Services]
ms.assetid: 8c855194-4c20-4ecc-a328-5137d54b560c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 61f1f50ea7a49acc616a36a4eaf1d3d5fcdf269a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688507"
---
# <a name="reporting-services-properties"></a><span data-ttu-id="71014-102">Reporting Services 属性</span><span class="sxs-lookup"><span data-stu-id="71014-102">Reporting Services Properties</span></span>
  <span data-ttu-id="71014-103">报表服务器定义对于报表服务器而言为全局的一组系统属性，并定义与报表服务器数据库中存储的单独项关联的一组项属性。</span><span class="sxs-lookup"><span data-stu-id="71014-103">The report server defines a set of system properties that are global to the report server and a set of item properties that are associated with an individual item stored in the report server database.</span></span> <span data-ttu-id="71014-104">不能删除由报表服务器定义的属性，在某些情况下，它们是只读的。</span><span class="sxs-lookup"><span data-stu-id="71014-104">Properties defined by the report server cannot be deleted, and in some cases they are read-only.</span></span> <span data-ttu-id="71014-105">应用程序可以通过将其他用户定义属性添加到系统以及添加项属性来扩展系统属性和项属性。</span><span class="sxs-lookup"><span data-stu-id="71014-105">An application can extend system properties and item properties by adding additional user-defined properties to the system and item properties.</span></span>  
  
 <span data-ttu-id="71014-106">以下 Web 服务方法检索并设置 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 属性。</span><span class="sxs-lookup"><span data-stu-id="71014-106">The following Web service methods retrieve and set [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] properties.</span></span>  
  
|<span data-ttu-id="71014-107">方法</span><span class="sxs-lookup"><span data-stu-id="71014-107">Method</span></span>|<span data-ttu-id="71014-108">操作</span><span class="sxs-lookup"><span data-stu-id="71014-108">Action</span></span>|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.GetProperties%2A>|<span data-ttu-id="71014-109">对于报表服务器数据库中的项返回一个或多个属性的值。</span><span class="sxs-lookup"><span data-stu-id="71014-109">Returns the values of one or more properties on an item in the report server database.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetSystemProperties%2A>|<span data-ttu-id="71014-110">返回一个或多个系统属性。</span><span class="sxs-lookup"><span data-stu-id="71014-110">Returns one or more system properties.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetProperties%2A>|<span data-ttu-id="71014-111">为报表服务器数据库中的项设置一个或多个属性。</span><span class="sxs-lookup"><span data-stu-id="71014-111">Sets one or more properties of an item in the report server database.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetSystemProperties%2A>|<span data-ttu-id="71014-112">设置一个或多个系统属性。</span><span class="sxs-lookup"><span data-stu-id="71014-112">Sets one or more system properties.</span></span>|  
  
## <a name="in-this-section"></a><span data-ttu-id="71014-113">本节内容</span><span class="sxs-lookup"><span data-stu-id="71014-113">In This Section</span></span>  
  
|<span data-ttu-id="71014-114">主题</span><span class="sxs-lookup"><span data-stu-id="71014-114">Topic</span></span>|<span data-ttu-id="71014-115">说明</span><span class="sxs-lookup"><span data-stu-id="71014-115">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="71014-116">报表服务器项属性</span><span class="sxs-lookup"><span data-stu-id="71014-116">Report Server Item Properties</span></span>](reporting-services-properties-report-server-item-properties.md)|<span data-ttu-id="71014-117">介绍 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中特定于项的属性。</span><span class="sxs-lookup"><span data-stu-id="71014-117">Describes the item-specific properties in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="71014-118">报表服务器系统属性</span><span class="sxs-lookup"><span data-stu-id="71014-118">Report Server System Properties</span></span>](reporting-services-properties-report-server-system-properties.md)|<span data-ttu-id="71014-119">介绍 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中特定于系统的属性。</span><span class="sxs-lookup"><span data-stu-id="71014-119">Describes the system-specific properties in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="71014-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="71014-120">See Also</span></span>  
 <span data-ttu-id="71014-121">[使用 Web 服务和 .NET Framework 生成应用程序](building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="71014-121">[Building Applications Using the Web Service and the .NET Framework](building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 <span data-ttu-id="71014-122">[报表服务器 Web 服务](../report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="71014-122">[Report Server Web Service](../report-server-web-service.md) </span></span>  
 [<span data-ttu-id="71014-123">技术参考 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="71014-123">Technical Reference &#40;SSRS&#41;</span></span>](../../technical-reference-ssrs.md)  
  
  
