---
title: 使用 SQL Server Profiler 监视 Analysis Services |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Profiler, Analysis Services
- monitoring Analysis Services [SQL Server]
- performance [Analysis Services], SQL Server Profiler
- Profiler [SQL Server Profiler], Analysis Services
ms.assetid: 8b77dafc-4584-4e93-8ad7-299304391bfd
author: minewiskan
ms.author: owend
ms.openlocfilehash: e144c1d858670f8a46b164ffc9885e6e082c4b0a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579155"
---
# <a name="use-sql-server-profiler-to-monitor-analysis-services"></a><span data-ttu-id="1908f-102">Use SQL Server Profiler to Monitor Analysis Services</span><span class="sxs-lookup"><span data-stu-id="1908f-102">Use SQL Server Profiler to Monitor Analysis Services</span></span>
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="1908f-103">跟踪引擎进程事件（例如批处理或事务的启动），并捕获有关这些事件的数据，从而使你可以监视服务器和数据库活动（例如，用户查询或登录活动）。</span><span class="sxs-lookup"><span data-stu-id="1908f-103">tracks engine process events, such as the start of a batch or a transaction, and it captures data about those events, thus enabling you to monitor server and database activity (for example, user queries or login activity).</span></span> <span data-ttu-id="1908f-104">可以将 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 数据捕获到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表或文件中，供后续分析使用，还可以重播在相同或其他 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例中捕获的事件，以确切了解所发生的情况。</span><span class="sxs-lookup"><span data-stu-id="1908f-104">You can capture [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] data to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table or a file for later analysis, and you can also replay the events captured on the same or another [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance to see exactly what happened.</span></span> <span data-ttu-id="1908f-105">可以实时或分步重播事件。</span><span class="sxs-lookup"><span data-stu-id="1908f-105">You can replay events in real time or on a step-by-step basis.</span></span> <span data-ttu-id="1908f-106">在同一计算机中运行跟踪事件和性能计数器是非常有用的。</span><span class="sxs-lookup"><span data-stu-id="1908f-106">It is also very useful to run the trace events along with the Performance counters on the same machine.</span></span> <span data-ttu-id="1908f-107">事件探查器可基于时间将跟踪事件与性能计数器相关联，并在一条时间线上同时显示这两者。</span><span class="sxs-lookup"><span data-stu-id="1908f-107">The profiler can correlate these two based on time and display them together along a single timeline.</span></span> <span data-ttu-id="1908f-108">跟踪事件提供详细信息，而性能计数器提供聚合视图。</span><span class="sxs-lookup"><span data-stu-id="1908f-108">Trace events will give you more details while Performance counters give you an aggregate view.</span></span> <span data-ttu-id="1908f-109">有关如何创建和运行跟踪的信息，请参阅 [为重播创建事件探查器跟踪 (Analysis Services)](create-profiler-traces-for-replay-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="1908f-109">For information about how to create and run traces, see [Create Profiler Traces for Replay &#40;Analysis Services&#41;](create-profiler-traces-for-replay-analysis-services.md).</span></span>  
  
 <span data-ttu-id="1908f-110">下表对本部分的主题进行了说明：</span><span class="sxs-lookup"><span data-stu-id="1908f-110">The following table describes the topics in this section.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1908f-111">本节内容</span><span class="sxs-lookup"><span data-stu-id="1908f-111">In This Section</span></span>  
  
|<span data-ttu-id="1908f-112">主题</span><span class="sxs-lookup"><span data-stu-id="1908f-112">Topic</span></span>|<span data-ttu-id="1908f-113">说明</span><span class="sxs-lookup"><span data-stu-id="1908f-113">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="1908f-114">通过 SQL Server Profiler 监视 Analysis Services 简介</span><span class="sxs-lookup"><span data-stu-id="1908f-114">Introduction to Monitoring Analysis Services with SQL Server Profiler</span></span>](introduction-to-monitoring-analysis-services-with-sql-server-profiler.md)|<span data-ttu-id="1908f-115">说明如何使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 监视 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="1908f-115">Describes how to use [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to monitor an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance.</span></span>|  
|[<span data-ttu-id="1908f-116">为重播创建事件探查器跟踪 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="1908f-116">Create Profiler Traces for Replay &#40;Analysis Services&#41;</span></span>](create-profiler-traces-for-replay-analysis-services.md)|<span data-ttu-id="1908f-117">说明使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]创建用于重播的跟踪的要求。</span><span class="sxs-lookup"><span data-stu-id="1908f-117">Describes the requirements for creating a trace for replay by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>|  
|[<span data-ttu-id="1908f-118">Analysis Services 跟踪事件</span><span class="sxs-lookup"><span data-stu-id="1908f-118">Analysis Services Trace Events</span></span>](https://docs.microsoft.com/bi-reference/trace-events/analysis-services-trace-events)|<span data-ttu-id="1908f-119">说明 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 事件类。</span><span class="sxs-lookup"><span data-stu-id="1908f-119">Describes [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] event classes.</span></span> <span data-ttu-id="1908f-120">这些事件类映射到 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 所生成的操作并用于跟踪重播。</span><span class="sxs-lookup"><span data-stu-id="1908f-120">These event classes map to actions generated by [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] and are used for trace replays.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1908f-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1908f-121">See Also</span></span>  
 [<span data-ttu-id="1908f-122">监视 Analysis Services 实例</span><span class="sxs-lookup"><span data-stu-id="1908f-122">Monitor an Analysis Services Instance</span></span>](monitor-an-analysis-services-instance.md)  
  
  
