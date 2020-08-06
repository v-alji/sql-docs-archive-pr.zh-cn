---
title: 监视 Analysis Services 实例 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- monitoring [Analysis Services - multidimensional data]
- multidimensional data [Analysis Services], monitoring
- monitoring performance [SQL Server], SQL Server Profiler
- performance [SQL Server], monitoring tools
ms.assetid: 2f0ab717-05f3-427e-b8cd-a8bdca374add
author: minewiskan
ms.author: owend
ms.openlocfilehash: b98037ea9f26c339cdf7aba22c37e2cfb3dfbb97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588737"
---
# <a name="monitor-an-analysis-services-instance"></a><span data-ttu-id="fb9fe-102">监视 Analysis Services 实例</span><span class="sxs-lookup"><span data-stu-id="fb9fe-102">Monitor an Analysis Services Instance</span></span>
  <span data-ttu-id="fb9fe-103">可以使用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 或性能监视器（此应用程序有时称为 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] PerfMon **）监视**的性能。</span><span class="sxs-lookup"><span data-stu-id="fb9fe-103">You can monitor the performance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] or Performance Monitor, an application sometimes referred to as **PerfMon**.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="fb9fe-104">用于创建和管理跟踪并分析和重播跟踪结果。</span><span class="sxs-lookup"><span data-stu-id="fb9fe-104">lets you create and manage traces and analyze and replay trace results.</span></span> <span data-ttu-id="fb9fe-105">性能监视器报告服务器状态（通过某些计数器进行索引），下一节中将对此进行讨论。</span><span class="sxs-lookup"><span data-stu-id="fb9fe-105">Performance Monitor reports on server status, as indexed through certain counters, which are discussed in the next section.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fb9fe-106">有关监视的详细信息，请参阅 [SQL Server 2008 R2 Operations Guide](https://go.microsoft.com/fwlink/?LinkID=225539)（SQL Server 2008 R2 操作指南）。</span><span class="sxs-lookup"><span data-stu-id="fb9fe-106">For more information about monitoring, see the [SQL Server 2008 R2 Operations Guide](https://go.microsoft.com/fwlink/?LinkID=225539).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fb9fe-107">本节内容</span><span class="sxs-lookup"><span data-stu-id="fb9fe-107">In This Section</span></span>  
 <span data-ttu-id="fb9fe-108">单击这些链接以了解有关监视的更多信息。</span><span class="sxs-lookup"><span data-stu-id="fb9fe-108">Follow these links to learn more about monitoring.</span></span>  
  
 [<span data-ttu-id="fb9fe-109">Analysis Services 跟踪事件</span><span class="sxs-lookup"><span data-stu-id="fb9fe-109">Analysis Services Trace Events</span></span>](https://docs.microsoft.com/bi-reference/trace-events/analysis-services-trace-events)  
  
 [<span data-ttu-id="fb9fe-110">Use SQL Server Profiler to Monitor Analysis Services</span><span class="sxs-lookup"><span data-stu-id="fb9fe-110">Use SQL Server Profiler to Monitor Analysis Services</span></span>](use-sql-server-profiler-to-monitor-analysis-services.md)  
  
 [<span data-ttu-id="fb9fe-111">使用 &#40;XEvents&#41; SQL Server 扩展事件监视 Analysis Services</span><span class="sxs-lookup"><span data-stu-id="fb9fe-111">Use SQL Server Extended Events &#40;XEvents&#41; to Monitor Analysis Services</span></span>](../instances/monitor-analysis-services-with-sql-server-extended-events.md)  
  
 [<span data-ttu-id="fb9fe-112">使用动态管理视图 (DMV) 监视 Analysis Services</span><span class="sxs-lookup"><span data-stu-id="fb9fe-112">Use Dynamic Management Views &#40;DMVs&#41; to Monitor Analysis Services</span></span>](use-dynamic-management-views-dmvs-to-monitor-analysis-services.md)  
  
 [<span data-ttu-id="fb9fe-113">性能计数器 (SSAS)</span><span class="sxs-lookup"><span data-stu-id="fb9fe-113">Performance Counters &#40;SSAS&#41;</span></span>](performance-counters-ssas.md)  
  
  
