---
title: 呈现和执行方法 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- rendered reports [Reporting Services]
- reports [Reporting Services], execution options
- methods [Reporting Services], execution options
- methods [Reporting Services], rendering
ms.assetid: 12626aad-f0be-4653-87d0-60eb3a3fff78
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d0bc793e9a18e993989563fd3526ff12272f775c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691587"
---
# <a name="rendering-and-execution-methods"></a><span data-ttu-id="6663d-102">呈现和执行方法</span><span class="sxs-lookup"><span data-stu-id="6663d-102">Rendering and Execution Methods</span></span>
  <span data-ttu-id="6663d-103">可以使用这些方法来管理项执行和缓存以及报表呈现。</span><span class="sxs-lookup"><span data-stu-id="6663d-103">You can use these methods to manage item execution and caching, and report rendering.</span></span>  
  
|<span data-ttu-id="6663d-104">方法</span><span class="sxs-lookup"><span data-stu-id="6663d-104">Method</span></span>|<span data-ttu-id="6663d-105">操作</span><span class="sxs-lookup"><span data-stu-id="6663d-105">Action</span></span>|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.FlushCache%2A>|<span data-ttu-id="6663d-106">使项的缓存无效。</span><span class="sxs-lookup"><span data-stu-id="6663d-106">Invalidates the cache for an item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetCacheOptions%2A>|<span data-ttu-id="6663d-107">返回项的缓存配置以及说明项的缓存副本何时到期的设置。</span><span class="sxs-lookup"><span data-stu-id="6663d-107">Returns the cache configuration for an item and the settings that describe when the cached copy of the item expires.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetExecutionOptions%2A>|<span data-ttu-id="6663d-108">返回单个项的执行选项和相关设置。</span><span class="sxs-lookup"><span data-stu-id="6663d-108">Returns the execution option and associated settings for an individual item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListExecutionSettings%2A>|<span data-ttu-id="6663d-109">返回支持的执行设置的列表。</span><span class="sxs-lookup"><span data-stu-id="6663d-109">Returns a list of supported execution settings.</span></span>|  
|<xref:ReportExecution2005.ReportExecutionService.Render%2A>|<span data-ttu-id="6663d-110">处理指定报表并以指定格式呈现报表。</span><span class="sxs-lookup"><span data-stu-id="6663d-110">Processes the specified report and renders it in a specified format.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetCacheOptions%2A>|<span data-ttu-id="6663d-111">配置要缓存的项并提供指定项的缓存副本何时到期的设置。</span><span class="sxs-lookup"><span data-stu-id="6663d-111">Configures an item to be cached and provides settings that specify when the cached copy of the item expires.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetExecutionOptions%2A>|<span data-ttu-id="6663d-112">为指定的项设置执行选项和相关的执行属性。</span><span class="sxs-lookup"><span data-stu-id="6663d-112">Sets execution options and associated execution properties for a specified item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.UpdateItemExecutionSnapshot%2A>|<span data-ttu-id="6663d-113">生成指定项的项执行快照。</span><span class="sxs-lookup"><span data-stu-id="6663d-113">Generates an item execution snapshot for a specified item.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6663d-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6663d-114">See Also</span></span>  
 <span data-ttu-id="6663d-115">[使用 Web 服务和 .NET Framework 生成应用程序](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="6663d-115">[Building Applications Using the Web Service and the .NET Framework](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 <span data-ttu-id="6663d-116">[报表服务器 Web 服务](../report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="6663d-116">[Report Server Web Service](../report-server-web-service.md) </span></span>  
 <span data-ttu-id="6663d-117">[报表服务器 Web 服务方法](report-server-web-service-methods.md) </span><span class="sxs-lookup"><span data-stu-id="6663d-117">[Report Server Web Service Methods](report-server-web-service-methods.md) </span></span>  
 [<span data-ttu-id="6663d-118">技术参考 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="6663d-118">Technical Reference &#40;SSRS&#41;</span></span>](../../technical-reference-ssrs.md)  
  
  
