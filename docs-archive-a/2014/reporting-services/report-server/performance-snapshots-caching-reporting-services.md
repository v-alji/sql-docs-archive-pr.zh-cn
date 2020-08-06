---
title: 性能、快照、缓存 (Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- performance [Reporting Services]
- Reporting Services, performance
ms.assetid: 85afd00f-e8d7-4ef7-9174-2ff84d82f960
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f171586e136b36bd694fa40b15272f62e1cb1378
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689779"
---
# <a name="performance-snapshots-caching-reporting-services"></a><span data-ttu-id="54235-102">性能、快照、缓存 (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="54235-102">Performance, Snapshots, Caching (Reporting Services)</span></span>
  <span data-ttu-id="54235-103">报表服务器性能受各种组合因素的影响，这些因素包括硬件、访问报表的并发用户的数量、报表中的数据量和输出格式。</span><span class="sxs-lookup"><span data-stu-id="54235-103">Report server performance is affected by a combination of factors that include hardware, number of concurrent users accessing reports, the amount of data in a report, and output format.</span></span> <span data-ttu-id="54235-104">若要了解影响您的安装的具体性能因素以及哪个补救办法将生成所需的结果，您将需要获得基准数据并运行测试。</span><span class="sxs-lookup"><span data-stu-id="54235-104">To understand the performance factors that are specific to your installation and which remedies will produce the results you want, you will need to get baseline data and run tests.</span></span> <span data-ttu-id="54235-105">有关工具和指南的详细信息，请参阅 MSDN 上的以下发布内容： [Reporting Services 性能优化](https://blogs.msdn.com/b/sqlcat/archive/2013/10/30/reporting-services-performance-and-optimization.aspx) 和 [使用 Visual Studio 2005 在 SQL Server 2005 Reporting Services 报表服务器上执行负载测试](https://go.microsoft.com/fwlink/?LinkID=77519)。</span><span class="sxs-lookup"><span data-stu-id="54235-105">For more information about tools and guidelines, see the following publications on MSDN: [Reporting Services Performance Optimization](https://blogs.msdn.com/b/sqlcat/archive/2013/10/30/reporting-services-performance-and-optimization.aspx) and [Using Visual Studio 2005 to Perform Load Testing on a SQL Server 2005 Reporting Services Report Server](https://go.microsoft.com/fwlink/?LinkID=77519).</span></span>  
  
 <span data-ttu-id="54235-106">下面是需要考虑的总原则：</span><span class="sxs-lookup"><span data-stu-id="54235-106">General principles to consider include the following:</span></span>  
  
-   <span data-ttu-id="54235-107">报表的处理和呈现操作会占用大量内存。</span><span class="sxs-lookup"><span data-stu-id="54235-107">Report processing and rendering are memory intensive operations.</span></span> <span data-ttu-id="54235-108">如有可能，请选择具有大量内存的计算机。</span><span class="sxs-lookup"><span data-stu-id="54235-108">When possible, choose a computer that has a lot of memory.</span></span>  
  
-   <span data-ttu-id="54235-109">将报表服务器和报表服务器数据库承载到单独的计算机上往往比将二者同时承载到单台高端计算机上能取得更好的性能。</span><span class="sxs-lookup"><span data-stu-id="54235-109">Hosting the report server and the report server database on separate computers tends to provide better performance than hosting both on a single high-end computer.</span></span>  
  
-   <span data-ttu-id="54235-110">如果所有报表的处理速度都慢，请考虑使用一个扩展部署，其中的多个报表服务器实例都支持单个报表服务器数据库。</span><span class="sxs-lookup"><span data-stu-id="54235-110">If all reports are processing slowly, consider a scale-out deployment where multiple report server instances support a single report server database.</span></span> <span data-ttu-id="54235-111">为了获得最佳效果，请使用负载平衡软件来将请求平均分布到部署中。</span><span class="sxs-lookup"><span data-stu-id="54235-111">For best results, use load balancing software to distribute requests evenly across the deployment.</span></span>  
  
-   <span data-ttu-id="54235-112">如果只是单个报表的处理速度慢，而且该报表必须按需运行，请对报表数据集查询进行优化。</span><span class="sxs-lookup"><span data-stu-id="54235-112">If a single report is processing slowly, tune report dataset queries if the report must run on demand.</span></span> <span data-ttu-id="54235-113">您还可以考虑使用可高速缓存的共享数据集、高速缓存报表或将报表作为快照运行。</span><span class="sxs-lookup"><span data-stu-id="54235-113">You might also consider using shared datasets that you can cache, caching the report, or running the report as a snapshot.</span></span>  
  
-   <span data-ttu-id="54235-114">如果所有报表在以特定格式处理（例如，以 PDF 格式呈现）时都慢，请考虑使用文件共享传递、添加更多的内存或者选择其他格式。</span><span class="sxs-lookup"><span data-stu-id="54235-114">If all reports process slowly in a specific format (for example, while rendering to PDF), consider file share delivery, adding more memory, or choosing a different format.</span></span>  
  
-   <span data-ttu-id="54235-115">若要确定处理报表所需的时间以及其他使用情况指标，请检查报表服务器的执行日志。</span><span class="sxs-lookup"><span data-stu-id="54235-115">To find out how long it takes to process a report and other usage metrics, review the report server execution log.</span></span> <span data-ttu-id="54235-116">有关详细信息，请参阅[报表服务器执行日志和 ExecutionLog3 视图](report-server-executionlog-and-the-executionlog3-view.md)。</span><span class="sxs-lookup"><span data-stu-id="54235-116">For more information, see [Report Server Execution Log and the ExecutionLog3 View](report-server-executionlog-and-the-executionlog3-view.md).</span></span>  
  
-   <span data-ttu-id="54235-117">有关如何通过优化内存管理配置设置来缓解性能问题的详细信息，请参阅 [为报表服务器应用程序配置可用内存](../report-server/configure-available-memory-for-report-server-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="54235-117">For more information about how to mitigate performance issues by tuning memory management configuration settings, see [Configure Available Memory for Report Server Applications](../report-server/configure-available-memory-for-report-server-applications.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="54235-118">本节内容</span><span class="sxs-lookup"><span data-stu-id="54235-118">In This Section</span></span>  
 [<span data-ttu-id="54235-119">监视报表服务器性能</span><span class="sxs-lookup"><span data-stu-id="54235-119">Monitoring Report Server Performance</span></span>](monitoring-report-server-performance.md)  
 <span data-ttu-id="54235-120">介绍可用来跟踪服务器上的处理负载的性能对象。</span><span class="sxs-lookup"><span data-stu-id="54235-120">Describes the performance objects you can use to track the processing load on your server.</span></span>  
  
 [<span data-ttu-id="54235-121">设置报表处理属性</span><span class="sxs-lookup"><span data-stu-id="54235-121">Set Report Processing Properties</span></span>](set-report-processing-properties.md)  
 <span data-ttu-id="54235-122">介绍如何将报表配置为按需运行、从高速缓存运行或按计划作为报表快照运行。</span><span class="sxs-lookup"><span data-stu-id="54235-122">Describes ways of configuring a report to run on demand, from cache, or on a schedule as a report snapshot.</span></span>  
  
 [<span data-ttu-id="54235-123">为报表服务器应用程序配置可用内存</span><span class="sxs-lookup"><span data-stu-id="54235-123">Configure Available Memory for Report Server Applications</span></span>](../report-server/configure-available-memory-for-report-server-applications.md)  
 <span data-ttu-id="54235-124">说明如何覆盖默认内存管理行为。</span><span class="sxs-lookup"><span data-stu-id="54235-124">Describes how you can override default memory management behavior.</span></span>  
  
 [<span data-ttu-id="54235-125">缓存报表 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="54235-125">Caching Reports &#40;SSRS&#41;</span></span>](caching-reports-ssrs.md)  
 <span data-ttu-id="54235-126">介绍报表服务器上的报表高速缓存行为。</span><span class="sxs-lookup"><span data-stu-id="54235-126">Describes report caching behavior on a report server.</span></span>  
  
 [<span data-ttu-id="54235-127">缓存共享数据集 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="54235-127">Cache Shared Datasets &#40;SSRS&#41;</span></span>](cache-shared-datasets-ssrs.md)  
 <span data-ttu-id="54235-128">介绍报表服务器上的共享数据集高速缓存行为。</span><span class="sxs-lookup"><span data-stu-id="54235-128">Describes shared dataset caching behavior on a report server.</span></span>  
  
 [<span data-ttu-id="54235-129">处理大型报表</span><span class="sxs-lookup"><span data-stu-id="54235-129">Process Large Reports</span></span>](process-large-reports.md)  
 <span data-ttu-id="54235-130">为如何配置和分发大型报表提供建议。</span><span class="sxs-lookup"><span data-stu-id="54235-130">Provides recommendations on how to configure and distribute a large report.</span></span>  
  
 [<span data-ttu-id="54235-131">为报表和共享数据集处理设置超时值 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="54235-131">Setting Time-out Values for Report and Shared Dataset Processing &#40;SSRS&#41;</span></span>](setting-time-out-values-for-report-and-shared-dataset-processing-ssrs.md)  
 <span data-ttu-id="54235-132">介绍如何针对查询和报表处理设置超时值。</span><span class="sxs-lookup"><span data-stu-id="54235-132">Explains how to set time outs on query and report processing.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54235-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="54235-133">See Also</span></span>  
 <span data-ttu-id="54235-134">[管理运行中的进程](../subscriptions/manage-a-running-process.md) </span><span class="sxs-lookup"><span data-stu-id="54235-134">[Manage a Running Process](../subscriptions/manage-a-running-process.md) </span></span>  
 [<span data-ttu-id="54235-135">验证报表运行情况</span><span class="sxs-lookup"><span data-stu-id="54235-135">Verifying a Report Run</span></span>](verifying-a-report-run.md)  
  
  
