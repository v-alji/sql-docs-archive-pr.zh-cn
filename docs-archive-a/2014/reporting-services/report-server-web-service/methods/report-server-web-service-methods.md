---
title: 报表服务器 Web 服务方法 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Report Server Web service, methods
- Web service [Reporting Services], methods
- XML Web service [Reporting Services], features
- Web service [Reporting Services], features
- Report Server Web service, features
- XML Web service [Reporting Services], methods
ms.assetid: ce5afa27-e90c-44a7-b204-098a065b3665
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 37d0031ebfb4ec6d31da6aad9a8842c0623cb75b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578623"
---
# <a name="report-server-web-service-methods"></a><span data-ttu-id="a20b8-102">报表服务器 Web 服务方法</span><span class="sxs-lookup"><span data-stu-id="a20b8-102">Report Server Web Service Methods</span></span>
  <span data-ttu-id="a20b8-103">根据不同的组件功能，报表服务器 Web 服务方法包含不同的类别。</span><span class="sxs-lookup"><span data-stu-id="a20b8-103">The Report Server Web services include several categories of methods that are based on component features.</span></span> <span data-ttu-id="a20b8-104">这些方法通过作为 <xref:ReportService2010.ReportingService2010> 和 <xref:ReportExecution2005.ReportExecutionService> 类的成员公开的若干 Web 服务端点（三个用于报表管理，一个用于报表执行）提供。</span><span class="sxs-lookup"><span data-stu-id="a20b8-104">These methods are provided through several Web service endpoints (three for report management and one for report execution) which are exposed as members of the <xref:ReportService2010.ReportingService2010> and <xref:ReportExecution2005.ReportExecutionService> classes.</span></span> <span data-ttu-id="a20b8-105">这些类可通过代理类工具（如 wsdl.exe）生成，该工具随 SDK 一起提供 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="a20b8-105">These classes can be generated through a proxy class tool such as wsdl.exe, which is included with the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK.</span></span> <span data-ttu-id="a20b8-106">有关使用报表服务器 Web 服务和 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 的详细信息，请参阅[使用 Web 服务和 .NET Framework 生成应用程序](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md)。</span><span class="sxs-lookup"><span data-stu-id="a20b8-106">For more information about the Report Server Web services and the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], see [Building Applications Using the Web Service and the .NET Framework](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md).</span></span>  
  
## <a name="endpoints-and-methods"></a><span data-ttu-id="a20b8-107">端点和方法</span><span class="sxs-lookup"><span data-stu-id="a20b8-107">Endpoints and Methods</span></span>  
 <span data-ttu-id="a20b8-108">下表列出了报表服务器 Web 服务的端点以及 <xref:ReportService2010.ReportingService2010> 端点提供的方法的类别。</span><span class="sxs-lookup"><span data-stu-id="a20b8-108">The following table lists the endpoints of the Report Server Web service, and the categories of methods provided by the <xref:ReportService2010.ReportingService2010> endpoint.</span></span> <span data-ttu-id="a20b8-109">有关其他终结点中可用方法的信息，请参阅[技术参考 (SSRS)](../../technical-reference-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="a20b8-109">For information on the methods available in the other endpoints, see [Technical Reference &#40;SSRS&#41;](../../technical-reference-ssrs.md).</span></span>  
  
|<span data-ttu-id="a20b8-110">主题</span><span class="sxs-lookup"><span data-stu-id="a20b8-110">Topic</span></span>|<span data-ttu-id="a20b8-111">说明</span><span class="sxs-lookup"><span data-stu-id="a20b8-111">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="a20b8-112">报表服务器 Web 服务端点</span><span class="sxs-lookup"><span data-stu-id="a20b8-112">Report Server Web Service Endpoints</span></span>](report-server-web-service-endpoints.md)|<span data-ttu-id="a20b8-113">介绍如何管理和执行报表服务器 Web 服务的端点。</span><span class="sxs-lookup"><span data-stu-id="a20b8-113">Describes the management and execution endpoints of the Report Server Web service.</span></span>|  
|[<span data-ttu-id="a20b8-114">报表服务器命名空间管理方法</span><span class="sxs-lookup"><span data-stu-id="a20b8-114">Report Server Namespace Management Methods</span></span>](report-server-namespace-management-methods.md)|<span data-ttu-id="a20b8-115">介绍可用来管理报表服务器数据库的方法。</span><span class="sxs-lookup"><span data-stu-id="a20b8-115">Describes methods that you can use to manage the report server database.</span></span> <span data-ttu-id="a20b8-116">特别值得一提的是，您可以管理文件夹和资源，并设置项属性。</span><span class="sxs-lookup"><span data-stu-id="a20b8-116">Specifically you can manage folders and resources and set item properties.</span></span>|  
|[<span data-ttu-id="a20b8-117">授权方法</span><span class="sxs-lookup"><span data-stu-id="a20b8-117">Authorization Methods</span></span>](authorization-methods.md)|<span data-ttu-id="a20b8-118">介绍可用来管理任务、角色和策略的方法。</span><span class="sxs-lookup"><span data-stu-id="a20b8-118">Describes methods that you can use to manage tasks, roles, and policies.</span></span>|  
|[<span data-ttu-id="a20b8-119">数据源和连接方法</span><span class="sxs-lookup"><span data-stu-id="a20b8-119">Data Sources and Connection Methods</span></span>](data-sources-and-connection-methods.md)|<span data-ttu-id="a20b8-120">介绍可用来设置和管理报表的数据源连接和凭据信息的方法。</span><span class="sxs-lookup"><span data-stu-id="a20b8-120">Describes methods that you can use to set and manage data source connection and credential information for reports.</span></span>|  
|[<span data-ttu-id="a20b8-121">报表参数方法</span><span class="sxs-lookup"><span data-stu-id="a20b8-121">Report Parameters Methods</span></span>](report-parameters-methods.md)|<span data-ttu-id="a20b8-122">介绍可用来设置和检索报表的参数的方法。</span><span class="sxs-lookup"><span data-stu-id="a20b8-122">Describes methods that you can use to set and retrieve parameters for reports.</span></span>|  
|[<span data-ttu-id="a20b8-123">模型方法</span><span class="sxs-lookup"><span data-stu-id="a20b8-123">Model Methods</span></span>](../report-server-web-service.md)|<span data-ttu-id="a20b8-124">介绍可用来管理模型的方法。</span><span class="sxs-lookup"><span data-stu-id="a20b8-124">Describes methods that you can use to manage models.</span></span>|  
|[<span data-ttu-id="a20b8-125">呈现和执行方法</span><span class="sxs-lookup"><span data-stu-id="a20b8-125">Rendering and Execution Methods</span></span>](rendering-and-execution-methods.md)|<span data-ttu-id="a20b8-126">介绍可用来管理报表执行、呈现和缓存的方法。</span><span class="sxs-lookup"><span data-stu-id="a20b8-126">Describes methods that you can use to manage report execution, rendering, and caching.</span></span>|  
|[<span data-ttu-id="a20b8-127">报表历史记录方法</span><span class="sxs-lookup"><span data-stu-id="a20b8-127">Report History Methods</span></span>](report-history-methods.md)|<span data-ttu-id="a20b8-128">介绍可用来创建和管理报表历史记录快照的方法。</span><span class="sxs-lookup"><span data-stu-id="a20b8-128">Describes methods that you can use to create and manage report history snapshots.</span></span>|  
|[<span data-ttu-id="a20b8-129">计划方法</span><span class="sxs-lookup"><span data-stu-id="a20b8-129">Scheduling Methods</span></span>](scheduling-methods.md)|<span data-ttu-id="a20b8-130">介绍可用来创建和管理报表服务器采用的共享计划和缓存刷新计划的方法。</span><span class="sxs-lookup"><span data-stu-id="a20b8-130">Describes methods that you can use to create and manage shared schedules and cache refresh plans that are used by the report server.</span></span>|  
|[<span data-ttu-id="a20b8-131">订阅和传递方法</span><span class="sxs-lookup"><span data-stu-id="a20b8-131">Subscription and Delivery Methods</span></span>](subscription-and-delivery-methods.md)|<span data-ttu-id="a20b8-132">介绍可用来创建和管理订阅和报表传递的方法。</span><span class="sxs-lookup"><span data-stu-id="a20b8-132">Describes methods that you can use to create and manage subscriptions and report delivery.</span></span>|  
|[<span data-ttu-id="a20b8-133">链接报表方法</span><span class="sxs-lookup"><span data-stu-id="a20b8-133">Linked Reports Methods</span></span>](linked-reports-methods.md)|<span data-ttu-id="a20b8-134">介绍可用来创建和管理链接报表的方法。</span><span class="sxs-lookup"><span data-stu-id="a20b8-134">Describes methods that you can use to create and manage linked reports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a20b8-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a20b8-135">See Also</span></span>  
 <span data-ttu-id="a20b8-136">[访问 SOAP API](../accessing-the-soap-api.md) </span><span class="sxs-lookup"><span data-stu-id="a20b8-136">[Accessing the SOAP API](../accessing-the-soap-api.md) </span></span>  
 <span data-ttu-id="a20b8-137">[使用 Web 服务和 .NET Framework 生成应用程序](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="a20b8-137">[Building Applications Using the Web Service and the .NET Framework](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 <span data-ttu-id="a20b8-138">[报表服务器 Web 服务](../report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="a20b8-138">[Report Server Web Service](../report-server-web-service.md) </span></span>  
 [<span data-ttu-id="a20b8-139">技术参考 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="a20b8-139">Technical Reference &#40;SSRS&#41;</span></span>](../../technical-reference-ssrs.md)  
  
  
