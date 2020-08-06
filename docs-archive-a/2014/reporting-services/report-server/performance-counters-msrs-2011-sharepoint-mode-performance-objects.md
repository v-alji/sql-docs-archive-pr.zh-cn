---
title: " (SharePoint 模式) 的 MSRS 2014 Web Service SharePoint Mode 和 MSRS 2014 Windows Service SharePoint Mode 性能对象的性能计数器 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- performance counters [Reporting Services]
- counters [Reporting Services]
- Report Server Windows service, performance counters
- RS Windows Service performance object
- Scheduling and Delivery Processor performance object [Reporting Services]
- performance [Reporting Services]
ms.assetid: 70bf6980-7845-4ab5-8b2a-ebf526d811a6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 91b77a62ea9d81af836e062cfafe9b700c47109e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689783"
---
# <a name="performance-counters-for-the-msrs-2014-web-service-sharepoint-mode-and-msrs-2014-windows-service-sharepoint-mode-performance-objects-sharepoint-mode"></a><span data-ttu-id="4baab-102">MSRS 2014 Web Service SharePoint Mode 性能对象和 MSRS 2014 Windows Service SharePoint Mode 性能对象的性能计数器（SharePoint 模式）</span><span class="sxs-lookup"><span data-stu-id="4baab-102">Performance Counters for the MSRS 2014 Web Service SharePoint Mode and MSRS 2014 Windows Service SharePoint Mode Performance Objects (SharePoint Mode)</span></span>
  <span data-ttu-id="4baab-103">本主题介绍作为 `MSRS 2014 Web Service SharePoint Mode` SharePoint 模式部署一部分的 `MSRS 2014 Windows Service SharePoint Mode` 性能对象和 [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] 性能对象的性能计数器。</span><span class="sxs-lookup"><span data-stu-id="4baab-103">This topic describes performance counters for the `MSRS 2014 Web Service SharePoint Mode` and `MSRS 2014 Windows Service SharePoint Mode` performance objects that are part of a [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] SharePoint mode deployment.</span></span>

> [!NOTE]
>  <span data-ttu-id="4baab-104">这些性能对象监视本地报表服务器上的事件。</span><span class="sxs-lookup"><span data-stu-id="4baab-104">This performance objects monitor events on the local report server.</span></span> <span data-ttu-id="4baab-105">如果是在扩展部署中运行报表服务器，则只对当前服务器（而不是整个扩展部署）进行计数。</span><span class="sxs-lookup"><span data-stu-id="4baab-105">If you are running a report server in a scale-out deployment, the counts apply to the current server and not the scale-out deployment as a whole.</span></span>

 <span data-ttu-id="4baab-106">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]SharePoint 模式</span><span class="sxs-lookup"><span data-stu-id="4baab-106">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] SharePoint mode</span></span>

 <span data-ttu-id="4baab-107">Windows 性能监视器 (**Perfmon.exe**) 中提供了性能对象。</span><span class="sxs-lookup"><span data-stu-id="4baab-107">The performance objects are available in the Windows Performance Monitor (**Perfmon.exe**).</span></span> <span data-ttu-id="4baab-108">有关详细信息，请参阅 Windows 文档。</span><span class="sxs-lookup"><span data-stu-id="4baab-108">For more information, see the Windows documentation.</span></span> <span data-ttu-id="4baab-109">[运行时分析](https://msdn.microsoft.com/library/w4bz2147.aspx)。</span><span class="sxs-lookup"><span data-stu-id="4baab-109">[Runtime Profiling](https://msdn.microsoft.com/library/w4bz2147.aspx).</span></span>

 <span data-ttu-id="4baab-110">**本主题内容：**</span><span class="sxs-lookup"><span data-stu-id="4baab-110">**In this topic:**</span></span>

-   [<span data-ttu-id="4baab-111">MSRS 2014 Web Service SharePoint Mode 性能计数器</span><span class="sxs-lookup"><span data-stu-id="4baab-111">MSRS 2014 Web Service SharePoint Mode Performance Counters</span></span>](#bkmk_webservice)

-   [<span data-ttu-id="4baab-112">MSRS 2014 Windows Service SharePoint Mode 性能计数器</span><span class="sxs-lookup"><span data-stu-id="4baab-112">MSRS 2014 Windows Service SharePoint Mode Performance Counters</span></span>](#bkmk_windowsservice)

-   [<span data-ttu-id="4baab-113">使用 PowerShell Cmdlet 返回列表</span><span class="sxs-lookup"><span data-stu-id="4baab-113">Use PowerShell Cmdlets to return lists</span></span>](#bkmk_powershell)

##  <a name="msrs-2014-web-service-sharepoint-mode-performance-counters"></a><a name="bkmk_webservice"></a><span data-ttu-id="4baab-114">MSRS 2014 Web Service SharePoint 模式性能计数器</span><span class="sxs-lookup"><span data-stu-id="4baab-114">MSRS 2014 Web Service SharePoint Mode Performance Counters</span></span>
 <span data-ttu-id="4baab-115">`MSRS 2014 Web Service SharePoint Mode` 性能对象监视报表服务器性能。</span><span class="sxs-lookup"><span data-stu-id="4baab-115">The `MSRS 2014 Web Service SharePoint Mode` performance object monitors report server performance.</span></span> <span data-ttu-id="4baab-116">此性能对象包括一系列用于跟踪报表服务器处理的计数器，这些处理通常通过交互式报表查看操作启动。</span><span class="sxs-lookup"><span data-stu-id="4baab-116">This performance object includes a collection of counters used to track report server processing typically initiated through interactive report viewing operations.</span></span> <span data-ttu-id="4baab-117">在设置计数器时，可将此计数器应用于 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 的全部实例，也可以选择特定实例。</span><span class="sxs-lookup"><span data-stu-id="4baab-117">When you set up this counter, you can apply the counter to all instances of [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] or you can select specific instances.</span></span> <span data-ttu-id="4baab-118">只要 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 停止报表服务器 Web 服务，这些计数器就会重置。</span><span class="sxs-lookup"><span data-stu-id="4baab-118">These counters are reset whenever [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] stops the Report Server Web service.</span></span>

 <span data-ttu-id="4baab-119">下表列出了 `MSRS 2014 Web Service SharePoint Mode` 性能对象中包含的计数器。</span><span class="sxs-lookup"><span data-stu-id="4baab-119">The following table lists the counters that are included with the `MSRS 2014 Web Service SharePoint Mode` performance object.</span></span>

|<span data-ttu-id="4baab-120">计数器</span><span class="sxs-lookup"><span data-stu-id="4baab-120">Counter</span></span>|<span data-ttu-id="4baab-121">说明</span><span class="sxs-lookup"><span data-stu-id="4baab-121">Description</span></span>|
|-------------|-----------------|
|`Active Sessions`|<span data-ttu-id="4baab-122">活动会话的数目。</span><span class="sxs-lookup"><span data-stu-id="4baab-122">Number of active sessions.</span></span> <span data-ttu-id="4baab-123">此计数器提供报表执行生成的所有浏览器会话的累积数，而不管这些会话是否仍处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="4baab-123">This counter provides a cumulative count of all browser sessions generated from report executions, whether they are still active or not.</span></span><br /><br /> <span data-ttu-id="4baab-124">删除会话记录后，此计数器的计数即会相应减少。</span><span class="sxs-lookup"><span data-stu-id="4baab-124">The counter is decremented as session records are removed.</span></span> <span data-ttu-id="4baab-125">默认情况下，如果会话在 10 分钟之内无任何活动，就会被删除。</span><span class="sxs-lookup"><span data-stu-id="4baab-125">By default, sessions are removed after ten minutes of no activity.</span></span>|
|`Cache Hits/Sec`|<span data-ttu-id="4baab-126">每秒请求缓存报表的次数。</span><span class="sxs-lookup"><span data-stu-id="4baab-126">Number of requests per second for cached reports.</span></span> <span data-ttu-id="4baab-127">这些请求是对重新呈现的报表的请求，而不是对直接从缓存处理的报表的请求。</span><span class="sxs-lookup"><span data-stu-id="4baab-127">These are requests for re-rendered reports, not requests for reports processed directly from the cache.</span></span> <span data-ttu-id="4baab-128">（请参阅本主题稍后部分中的 `Total Cache Hits`。）</span><span class="sxs-lookup"><span data-stu-id="4baab-128">(See `Total Cache Hits` later in this topic.)</span></span>|
|`Cache Hits/Sec (Semantic Models)`|<span data-ttu-id="4baab-129">每秒请求缓存模型的次数。</span><span class="sxs-lookup"><span data-stu-id="4baab-129">Number of requests per second for cached model.</span></span> <span data-ttu-id="4baab-130">这些请求是对重新呈现的报表的请求，而不是对直接从缓存处理的报表的请求。</span><span class="sxs-lookup"><span data-stu-id="4baab-130">These are requests for re-rendered reports, not requests for reports processed directly from the cache.</span></span>|
|`Cache Misses/Sec`|<span data-ttu-id="4baab-131">每秒未能从缓存返回报表的请求次数。</span><span class="sxs-lookup"><span data-stu-id="4baab-131">Number of requests per second that failed to return a report from cache.</span></span> <span data-ttu-id="4baab-132">使用此计数器可以查明是否有足够的资源（磁盘或内存）用于缓存。</span><span class="sxs-lookup"><span data-stu-id="4baab-132">Use this counter to find out whether the resources used for caching (disk or memory) are sufficient.</span></span>|
|`Cache Misses/Sec (Semantic Models)`|<span data-ttu-id="4baab-133">每秒未能从缓存返回模型的请求次数。</span><span class="sxs-lookup"><span data-stu-id="4baab-133">Number of requests per second that failed to return a model from cache.</span></span> <span data-ttu-id="4baab-134">使用此计数器可以查明是否有足够的资源（磁盘或内存）用于缓存。</span><span class="sxs-lookup"><span data-stu-id="4baab-134">Use this counter to find out whether the resources used for caching (disk or memory) are sufficient.</span></span>|
|`First Session Requests/Sec`|<span data-ttu-id="4baab-135">每秒从报表服务器缓存启动的新用户会话的数目。</span><span class="sxs-lookup"><span data-stu-id="4baab-135">Number of new user sessions that are started from the report server cache each second.</span></span>|
|`Memory Cache Hits/Sec`|<span data-ttu-id="4baab-136">每秒从内存中缓存检索到报表的次数。</span><span class="sxs-lookup"><span data-stu-id="4baab-136">Number of times per second that reports are retrieved from the in-memory cache.</span></span> <span data-ttu-id="4baab-137">*内存中缓存* 是缓存的一部分，可将报表存储在 CPU 内存中。</span><span class="sxs-lookup"><span data-stu-id="4baab-137">*In-memory cache* is a part of the cache that stores reports in CPU memory.</span></span> <span data-ttu-id="4baab-138">使用内存中缓存时，报表服务器不会在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中查询缓存的内容。</span><span class="sxs-lookup"><span data-stu-id="4baab-138">When in-memory cache is used, the report server does not query [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] for cached content.</span></span>|
|`Memory Cache Misses/Sec`|<span data-ttu-id="4baab-139">每秒从内存中缓存未检索到报表的次数。</span><span class="sxs-lookup"><span data-stu-id="4baab-139">Number of times per second that reports could not be retrieved from the in-memory cache.</span></span>|
|`Next Session Requests/Sec`|<span data-ttu-id="4baab-140">对当前会话中打开的报表（例如通过会话快照呈现的报表）的每秒请求数。</span><span class="sxs-lookup"><span data-stu-id="4baab-140">Number of requests per second for reports that are open in an existing session (such as reports that are rendered from a session snapshot).</span></span>|
|`Report Requests`|<span data-ttu-id="4baab-141">当前处于活动状态正由报表服务器进行处理的报表的数目。</span><span class="sxs-lookup"><span data-stu-id="4baab-141">Number of reports that are currently active and being handled by the report server.</span></span>|
|`Reports Executed/Sec`|<span data-ttu-id="4baab-142">每秒成功执行报表的次数。</span><span class="sxs-lookup"><span data-stu-id="4baab-142">Number of successful report executions per second.</span></span> <span data-ttu-id="4baab-143">此计数器提供有关报表量的统计信息。</span><span class="sxs-lookup"><span data-stu-id="4baab-143">This counter provides statistics about report volume.</span></span> <span data-ttu-id="4baab-144">将此计数器与 `Request/Sec` 一起使用，可以对报表执行与可以从缓存返回的报表请求进行比较。</span><span class="sxs-lookup"><span data-stu-id="4baab-144">Use this counter with `Request/Sec` to compare report execution to report requests that can be returned from cache.</span></span>|
|`Requests/Sec`|<span data-ttu-id="4baab-145">每秒向报表服务器发出的请求的次数。</span><span class="sxs-lookup"><span data-stu-id="4baab-145">Number of requests per second made to the report server.</span></span> <span data-ttu-id="4baab-146">此计数器可跟踪报表服务器处理的所有类型请求。</span><span class="sxs-lookup"><span data-stu-id="4baab-146">This counter tracks all types of requests that are handled by the report server.</span></span>|
|`Total Cache Hits`|<span data-ttu-id="4baab-147">服务启动后请求缓存报表的总次数。</span><span class="sxs-lookup"><span data-stu-id="4baab-147">Total number of requests for reports from the cache after the service started.</span></span> <span data-ttu-id="4baab-148">只要 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 停止报表服务器 Web 服务，此计数器就会重置。</span><span class="sxs-lookup"><span data-stu-id="4baab-148">This counter is reset whenever [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] stops the Report Server Web service.</span></span>|
|`Total Cache Hits (Semantic Models)`|<span data-ttu-id="4baab-149">服务启动后请求缓存中的模型的总次数。</span><span class="sxs-lookup"><span data-stu-id="4baab-149">Total number of requests for model from the cache after the service started.</span></span> <span data-ttu-id="4baab-150">只要 ASP.NET 停止报表服务器 Web 服务，此计数器就会重置。</span><span class="sxs-lookup"><span data-stu-id="4baab-150">This counter is reset whenever ASP.NET stops the Report Server Web service.</span></span>|
|`Total Cache Misses`|<span data-ttu-id="4baab-151">服务启动后未能从缓存返回报表的总次数。</span><span class="sxs-lookup"><span data-stu-id="4baab-151">Total number of times that a report could not be returned from the cache after the service started.</span></span> <span data-ttu-id="4baab-152">只要 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 停止报表服务器 Web 服务，此计数器就会重置。</span><span class="sxs-lookup"><span data-stu-id="4baab-152">This counter is reset whenever [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] stops the Report Server Web service.</span></span> <span data-ttu-id="4baab-153">使用此计数器可确定是否有足够的磁盘空间和内存。</span><span class="sxs-lookup"><span data-stu-id="4baab-153">Use this counter to determine whether disk space and memory are sufficient.</span></span>|
|`Total Cache Misses (Semantic Models)`|<span data-ttu-id="4baab-154">服务启动后未能从缓存返回模型的总次数。</span><span class="sxs-lookup"><span data-stu-id="4baab-154">Total number of times that a model could not be returned from the cache after the service started.</span></span> <span data-ttu-id="4baab-155">只要 ASP.NET 停止报表服务器 Web 服务，此计数器就会重置。</span><span class="sxs-lookup"><span data-stu-id="4baab-155">This counter is reset whenever ASP.NET stops the Report Server Web service.</span></span> <span data-ttu-id="4baab-156">使用此计数器可确定是否有足够的磁盘空间和内存。</span><span class="sxs-lookup"><span data-stu-id="4baab-156">Use this counter to determine whether disk space and memory are sufficient.</span></span>|
|`Total Memory Cache Hits`|<span data-ttu-id="4baab-157">服务启动后从内存中缓存返回的缓存报表的总数。</span><span class="sxs-lookup"><span data-stu-id="4baab-157">Total number of cached reports returned from the in-memory cache after the service started.</span></span> <span data-ttu-id="4baab-158">只要 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 停止报表服务器 Web 服务，此计数器就会重置。</span><span class="sxs-lookup"><span data-stu-id="4baab-158">This counter is reset whenever [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] stops the Report Server Web service.</span></span> <span data-ttu-id="4baab-159">*内存中缓存* 是缓存的一部分，可将报表存储在 CPU 内存中。</span><span class="sxs-lookup"><span data-stu-id="4baab-159">*In-memory cache* is a part of the cache that stores reports in CPU memory.</span></span> <span data-ttu-id="4baab-160">使用内存中缓存时，报表服务器不会在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中查询缓存的内容。</span><span class="sxs-lookup"><span data-stu-id="4baab-160">When in-memory cache is used, the report server does not query [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] for cached content.</span></span>|
|`Total Memory Cache Misses`|<span data-ttu-id="4baab-161">服务启动后在内存中缓存的缓存失误总数。</span><span class="sxs-lookup"><span data-stu-id="4baab-161">Total number of cache misses against the in-memory cache after the service started.</span></span> <span data-ttu-id="4baab-162">只要 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 停止报表服务器 Web 服务，此计数器就会重置。</span><span class="sxs-lookup"><span data-stu-id="4baab-162">This counter is reset whenever [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] stops the Report Server Web service.</span></span>|
|`Total Processing Failures`|<span data-ttu-id="4baab-163">报表服务器 Web 服务请求处理的错误数。</span><span class="sxs-lookup"><span data-stu-id="4baab-163">Number of errors in report server web service request processing.</span></span>|
|`Total Rejected Threads`|<span data-ttu-id="4baab-164">系统拒绝异步处理的总线程数，这些线程随后将以同一线程中同步进程的形式处理。</span><span class="sxs-lookup"><span data-stu-id="4baab-164">Total number of threads rejected for asynchronous processing, and subsequently handled as synchronous processes in the same thread.</span></span> <span data-ttu-id="4baab-165">每个数据源在一个线程中进行处理。</span><span class="sxs-lookup"><span data-stu-id="4baab-165">Each data source is processed on one thread.</span></span> <span data-ttu-id="4baab-166">如果线程量超出了系统容量，系统将拒绝对线程进行异步处理，随后会按串行方式处理。</span><span class="sxs-lookup"><span data-stu-id="4baab-166">If the volume of threads exceeds capacity, threads are rejected for asynchronous processing, and are then processed in a serial manner.</span></span>|
|`Total Reports Executed`|<span data-ttu-id="4baab-167">服务启动后成功运行的报表的总数。</span><span class="sxs-lookup"><span data-stu-id="4baab-167">Total number of reports that ran successfully after the service started.</span></span> <span data-ttu-id="4baab-168">只要 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 停止报表服务器 Web 服务，此计数器就会重置。</span><span class="sxs-lookup"><span data-stu-id="4baab-168">This counter is reset whenever [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] stops the Report Server Web service.</span></span>|
|`Total Requests`|<span data-ttu-id="4baab-169">服务启动后对报表服务器发出的全部请求的总数。</span><span class="sxs-lookup"><span data-stu-id="4baab-169">Total number of all requests made to the report server after the service started.</span></span> <span data-ttu-id="4baab-170">只要 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 停止报表服务器 Web 服务，此计数器就会重置。</span><span class="sxs-lookup"><span data-stu-id="4baab-170">This counter is reset whenever [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] stops the Report Server Web service.</span></span>|

##  <a name="msrs-2014-windows-service-sharepoint-mode-performance-counters"></a><a name="bkmk_windowsservice"></a><span data-ttu-id="4baab-171">MSRS 2014 Windows Service SharePoint Mode 性能计数器</span><span class="sxs-lookup"><span data-stu-id="4baab-171">MSRS 2014 Windows Service SharePoint Mode Performance Counters</span></span>
 <span data-ttu-id="4baab-172">`MSRS 2014 Windows Service SharePoint Mode` 性能对象用于监视报表服务器 Windows 服务。</span><span class="sxs-lookup"><span data-stu-id="4baab-172">The `MSRS 2014 Windows Service SharePoint Mode` performance object is used to monitor the Report Server Windows service.</span></span> <span data-ttu-id="4baab-173">此性能对象包括一系列用于跟踪报表处理的计数器，这些处理通过计划操作启动。</span><span class="sxs-lookup"><span data-stu-id="4baab-173">This performance object includes a collection of counters used to track report processing that is initiated through scheduled operations.</span></span> <span data-ttu-id="4baab-174">计划操作可以包括订阅和传递、报表执行快照和报表历史记录。</span><span class="sxs-lookup"><span data-stu-id="4baab-174">Scheduled operations can include subscription and delivery, report execution snapshots, and report history.</span></span> <span data-ttu-id="4baab-175">在设置计数器时，可将此计数器应用于 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 的全部实例，也可以选择特定实例。</span><span class="sxs-lookup"><span data-stu-id="4baab-175">When you set up this counter, you can apply the counter to all instances of [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] or you can select specific instances.</span></span>

 <span data-ttu-id="4baab-176">下表列出了 `MSRS 2014 Windows Service SharePoint mode` 性能对象中包含的计数器。</span><span class="sxs-lookup"><span data-stu-id="4baab-176">The following table lists the counters that are included in the `MSRS 2014 Windows Service SharePoint mode` performance object.</span></span>

|<span data-ttu-id="4baab-177">计数器</span><span class="sxs-lookup"><span data-stu-id="4baab-177">Counter</span></span>|<span data-ttu-id="4baab-178">说明</span><span class="sxs-lookup"><span data-stu-id="4baab-178">Description</span></span>|
|-------------|-----------------|
|`Active Sessions`|<span data-ttu-id="4baab-179">存储在报表服务器数据库中的活动会话数。</span><span class="sxs-lookup"><span data-stu-id="4baab-179">Number of active sessions stored in the report server database.</span></span> <span data-ttu-id="4baab-180">此计数器提供报表订阅生成的所有可用浏览器会话的累积数，而不管这些会话是否仍处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="4baab-180">This counter provides a cumulative count of all usable browser sessions generated from report subscriptions, whether they are still active or not.</span></span>|
|`Alerting: event queue length`||
|`Alerting: events processed - CreateSchedule`||
|`Alerting: events processed - Delete schedule`||
|`Alerting: events processed - DeliverAlert`||
|`Alerting: events processed - FireAlert`||
|`Alerting: events processed - FireSchedule`||
|`Alerting: events processed - GenerateAlert`||
|`Alerting: events processed - UpdateSchedule`||
|`Cache Flushes/Sec`|<span data-ttu-id="4baab-181">每秒刷新的缓存数。</span><span class="sxs-lookup"><span data-stu-id="4baab-181">Number of cache flushes per second.</span></span>|
|`Cache Hits/Sec`|<span data-ttu-id="4baab-182">每秒请求缓存报表的次数。</span><span class="sxs-lookup"><span data-stu-id="4baab-182">Number of requests per second for cached reports.</span></span> <span data-ttu-id="4baab-183">这些请求是对重新呈现的报表的请求，而不是对直接从缓存处理的报表的请求。</span><span class="sxs-lookup"><span data-stu-id="4baab-183">These are requests for re-rendered reports, not requests for reports processed directly from the cache.</span></span> <span data-ttu-id="4baab-184">（请参阅本主题稍后部分中的 `Total Cache Hits`。）</span><span class="sxs-lookup"><span data-stu-id="4baab-184">(See `Total Cache Hits` later in this topic.)</span></span>|
|`Cache Hits/Sec (Semantic Models)`|<span data-ttu-id="4baab-185">每秒请求缓存模型的次数。</span><span class="sxs-lookup"><span data-stu-id="4baab-185">Number of requests per second for cached models.</span></span>|
|`Cache Misses/Sec`|<span data-ttu-id="4baab-186">每秒未能从缓存返回报表的请求次数。</span><span class="sxs-lookup"><span data-stu-id="4baab-186">Number of requests per second that failed to return a report from cache.</span></span> <span data-ttu-id="4baab-187">使用此计数器可以查明是否有足够的资源（磁盘或内存）用于缓存。</span><span class="sxs-lookup"><span data-stu-id="4baab-187">Use this counter to find out whether the resources used for caching (disk or memory) are sufficient.</span></span>|
|`Cache Misses/Sec (Semantic Models)`|<span data-ttu-id="4baab-188">每秒未能从缓存返回模型的请求次数。</span><span class="sxs-lookup"><span data-stu-id="4baab-188">Number of requests per second that failed to return a model from cache.</span></span> <span data-ttu-id="4baab-189">使用此计数器可以查明是否有足够的资源（磁盘或内存）用于缓存。</span><span class="sxs-lookup"><span data-stu-id="4baab-189">Use this counter to find out whether the resources used for caching (disk or memory) are sufficient.</span></span>|
|`Delivers/Sec`|<span data-ttu-id="4baab-190">所有传递扩展插件每秒进行报表传递的次数。</span><span class="sxs-lookup"><span data-stu-id="4baab-190">Number of report deliveries per second, from any delivery extension.</span></span>|
|`Events/Sec`|<span data-ttu-id="4baab-191">每秒处理的事件数。</span><span class="sxs-lookup"><span data-stu-id="4baab-191">Number of events processed per second.</span></span> <span data-ttu-id="4baab-192">监视的事件包括 `SnapshotUpdated` 和 `TimedSubscription`。</span><span class="sxs-lookup"><span data-stu-id="4baab-192">Events that are monitored include `SnapshotUpdated` and `TimedSubscription`.</span></span>|
|`First Session Requests/Sec`|<span data-ttu-id="4baab-193">每秒创建的新报表执行会话的数目。</span><span class="sxs-lookup"><span data-stu-id="4baab-193">Number of new report execution sessions created per second.</span></span>|
|`Memory Cache Hits/Sec`|<span data-ttu-id="4baab-194">每秒从内存中缓存检索到报表的次数。</span><span class="sxs-lookup"><span data-stu-id="4baab-194">Number of times per second that reports are retrieved from the in-memory cache.</span></span> <span data-ttu-id="4baab-195">*内存中缓存* 是缓存的一部分，可将报表存储在 CPU 内存中。</span><span class="sxs-lookup"><span data-stu-id="4baab-195">*In-memory cache* is a part of the cache that stores reports in CPU memory.</span></span> <span data-ttu-id="4baab-196">使用内存中缓存时，报表服务器不会在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中查询缓存的内容。</span><span class="sxs-lookup"><span data-stu-id="4baab-196">When in-memory cache is used, the report server does not query [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] for cached content.</span></span>|
|`Memory Cache Misses/Sec`|<span data-ttu-id="4baab-197">每秒从内存中缓存未检索到报表的次数。</span><span class="sxs-lookup"><span data-stu-id="4baab-197">Number of times per second that reports cannot be retrieved from the in-memory cache.</span></span>|
|`Next Session Requests/Sec`|<span data-ttu-id="4baab-198">对当前会话中打开的报表（例如通过会话快照呈现的报表）的每秒请求数。</span><span class="sxs-lookup"><span data-stu-id="4baab-198">Number of requests per second for reports that are open in an existing session (such as reports that are rendered from a session snapshot).</span></span>|
|`Report Requests`|<span data-ttu-id="4baab-199">当前处于活动状态正由报表服务器进行处理的报表的数目。</span><span class="sxs-lookup"><span data-stu-id="4baab-199">Number of reports that are currently active and being handled by the report server.</span></span> <span data-ttu-id="4baab-200">使用此计数器可以评估缓存策略。</span><span class="sxs-lookup"><span data-stu-id="4baab-200">Use this counter to evaluate caching strategy.</span></span> <span data-ttu-id="4baab-201">请求数可能会比报表生成的请求数多很多。</span><span class="sxs-lookup"><span data-stu-id="4baab-201">There might be significantly more requests than reports generated.</span></span>|
|`Reports Executed/Sec`|<span data-ttu-id="4baab-202">每秒成功生成的报表数。</span><span class="sxs-lookup"><span data-stu-id="4baab-202">Number of reports successfully generated per second.</span></span>|
|`Requests/Sec`|<span data-ttu-id="4baab-203">报表服务器服务每秒处理的成功请求的总数。</span><span class="sxs-lookup"><span data-stu-id="4baab-203">Total number of successful requests the report server service processed per second.</span></span>|
|`Snapshot Updates/Sec`|<span data-ttu-id="4baab-204">每秒报表执行快照更新的总数。</span><span class="sxs-lookup"><span data-stu-id="4baab-204">Total number of report execution snapshot updates per second.</span></span>|
|`Total App Domain Recycles`|<span data-ttu-id="4baab-205">报表服务器 Windows 服务启动后应用程序域循环的总次数。</span><span class="sxs-lookup"><span data-stu-id="4baab-205">Total number of application domain cycles after the Report Server Windows service started.</span></span>|
|<span data-ttu-id="4baab-206">**总缓存刷新数**</span><span class="sxs-lookup"><span data-stu-id="4baab-206">**Total Cache Flushes**</span></span>|<span data-ttu-id="4baab-207">服务启动后报表服务器缓存更新的总次数。</span><span class="sxs-lookup"><span data-stu-id="4baab-207">Total number of report server cache updates after the service started.</span></span> <span data-ttu-id="4baab-208">当应用程序域回收时，将重置此计数器。</span><span class="sxs-lookup"><span data-stu-id="4baab-208">This counter resets when the application domain recycles.</span></span> <span data-ttu-id="4baab-209">请参阅 `Cache Flushes/Sec`。</span><span class="sxs-lookup"><span data-stu-id="4baab-209">See `Cache Flushes/Sec`.</span></span>|
|`Total Cache Hits`|<span data-ttu-id="4baab-210">报表服务器 Windows 服务启动后请求直接从缓存处理的报表的总次数。</span><span class="sxs-lookup"><span data-stu-id="4baab-210">Total number of requests for reports processed directly from the cache after the Report Server Windows service started.</span></span> <span data-ttu-id="4baab-211">当应用程序域回收时，将重置此计数器。</span><span class="sxs-lookup"><span data-stu-id="4baab-211">This counter resets when the application domain recycles.</span></span> <span data-ttu-id="4baab-212">请参阅 `Cache Hits/Sec`。</span><span class="sxs-lookup"><span data-stu-id="4baab-212">See `Cache Hits/Sec`.</span></span>|
|`Total Cache Hits (Semantic Models)`|<span data-ttu-id="4baab-213">报表服务器 Windows 服务启动后请求直接从缓存处理的模型请求总数。</span><span class="sxs-lookup"><span data-stu-id="4baab-213">Total number of model requests processed directly from the cache after the report server Windows service started.</span></span> <span data-ttu-id="4baab-214">当应用程序域回收时，将重置此计数器。</span><span class="sxs-lookup"><span data-stu-id="4baab-214">This counter resets when the application domain recycles.</span></span>|
|`Total Cache Misses`|<span data-ttu-id="4baab-215">报表服务器 Windows 服务启动后报表未能从缓存返回的总次数。</span><span class="sxs-lookup"><span data-stu-id="4baab-215">Total number of times that a report could not be returned from cache after the Report Server Windows service started.</span></span> <span data-ttu-id="4baab-216">当应用程序域回收时，将重置此计数器。</span><span class="sxs-lookup"><span data-stu-id="4baab-216">This counter resets when the application domain recycles.</span></span> <span data-ttu-id="4baab-217">请参阅 `Cache Misses/Sec`。</span><span class="sxs-lookup"><span data-stu-id="4baab-217">See `Cache Misses/Sec`.</span></span>|
|`Total Cache Misses (Semantic Models)`|<span data-ttu-id="4baab-218">报表服务器 Windows 服务启动后模型未能从缓存返回的总次数。</span><span class="sxs-lookup"><span data-stu-id="4baab-218">Total number of times that a model could not be returned from cache after the Report Server Windows service started.</span></span> <span data-ttu-id="4baab-219">当应用程序域回收时，将重置此计数器。</span><span class="sxs-lookup"><span data-stu-id="4baab-219">This counter resets when the application domain recycles.</span></span>|
|`Total Deliveries`|<span data-ttu-id="4baab-220">对于所有传递扩展插件，计划和传递处理器传递的报表总数。</span><span class="sxs-lookup"><span data-stu-id="4baab-220">Total number of reports delivered by the Scheduling and Delivery Processor, for all delivery extensions.</span></span> <span data-ttu-id="4baab-221">当应用程序域回收时，将重置此计数器。</span><span class="sxs-lookup"><span data-stu-id="4baab-221">This counter resets when the application domain recycles.</span></span>|
|`Total Events`|<span data-ttu-id="4baab-222">报表服务器 Windows 服务启动后发生的事件总数。</span><span class="sxs-lookup"><span data-stu-id="4baab-222">Total number of events after the Report Server Windows service started.</span></span> <span data-ttu-id="4baab-223">当应用程序域回收时，将重置此计数器。</span><span class="sxs-lookup"><span data-stu-id="4baab-223">This counter resets when the application domain recycles.</span></span>|
|`Total Memory Cache Hits`|<span data-ttu-id="4baab-224">报表服务器 Windows 服务启动后从内存中缓存返回的缓存报表总数。</span><span class="sxs-lookup"><span data-stu-id="4baab-224">Total number of cached reports returned from the in-memory cache after the Report Server Windows service started.</span></span> <span data-ttu-id="4baab-225">当应用程序域回收时，将重置此计数器。</span><span class="sxs-lookup"><span data-stu-id="4baab-225">This counter resets when the application domain recycles.</span></span>|
|`Total Memory Cache Misses`|<span data-ttu-id="4baab-226">服务启动后在内存中缓存的缓存失误总数。</span><span class="sxs-lookup"><span data-stu-id="4baab-226">Total number of cache misses against the in-memory cache after the service started.</span></span> <span data-ttu-id="4baab-227">当应用程序域回收时，将重置此计数器。</span><span class="sxs-lookup"><span data-stu-id="4baab-227">This counter resets when the application domain recycles.</span></span>|
|`Total Processing Failures`|<span data-ttu-id="4baab-228">针对报表服务器 Windows 服务的请求处理错误数。</span><span class="sxs-lookup"><span data-stu-id="4baab-228">Number of request processing errors for the report server Windows service.</span></span>|
|`Total Rejected Threads`|<span data-ttu-id="4baab-229">系统拒绝异步处理的总线程数，这些线程随后将以同一线程中同步进程的形式处理。</span><span class="sxs-lookup"><span data-stu-id="4baab-229">Total number of threads rejected for asynchronous processing, and subsequently handled as a synchronous process in the same thread.</span></span> <span data-ttu-id="4baab-230">在中等或高负载下，该计数器将稳定增长。</span><span class="sxs-lookup"><span data-stu-id="4baab-230">Under moderate or heavy load, this counter steadily increases.</span></span>|
|`Total Reports Executed`|<span data-ttu-id="4baab-231">运行报表的总数。</span><span class="sxs-lookup"><span data-stu-id="4baab-231">Total number of reports run.</span></span>|
|`Total Requests`|<span data-ttu-id="4baab-232">服务启动后成功运行的报表的总数。</span><span class="sxs-lookup"><span data-stu-id="4baab-232">Total number of reports that ran successfully after the service started.</span></span> <span data-ttu-id="4baab-233">当应用程序域回收时，将重置此计数器。</span><span class="sxs-lookup"><span data-stu-id="4baab-233">This counter resets when the application domain recycles.</span></span>|
|`Total Snapshot Updates`|<span data-ttu-id="4baab-234">报表执行快照更新的总数。</span><span class="sxs-lookup"><span data-stu-id="4baab-234">Total number of report execution snapshot updates.</span></span>|

##  <a name="use-powershell-cmdlets-to-return-lists"></a><a name="bkmk_powershell"></a><span data-ttu-id="4baab-235">使用 PowerShell Cmdlet 返回列表</span><span class="sxs-lookup"><span data-stu-id="4baab-235">Use PowerShell Cmdlets to return lists</span></span>
 <span data-ttu-id="4baab-236">![PowerShell 相关内容](../media/rs-powershellicon.jpg "PowerShell 相关内容")下面的 Windows PowerShell 脚本返回 CounterSetName 以“msr”开头的计数器集</span><span class="sxs-lookup"><span data-stu-id="4baab-236">![PowerShell related content](../media/rs-powershellicon.jpg "PowerShell related content")The following Windows PowerShell script will return the counter sets where the CounterSetName starts with "msr"</span></span>

```powershell
Get-Counter -ListSet msr*
```

<span data-ttu-id="4baab-237">返回一个列表，其中包含以下信息：</span><span class="sxs-lookup"><span data-stu-id="4baab-237">Returns a list with the following information:</span></span>

```
CounterSetName     : MSRS 2014 Windows Service SharePoint Mode
CounterSetName     : MSRS 2014 Web Service SharePoint Mode
```

 <span data-ttu-id="4baab-238">下面的 Windows PowerShell 脚本将返回 CounterSetName "MSRS 2014 Windows Service SharePoint Mode" 的性能计数器列表。</span><span class="sxs-lookup"><span data-stu-id="4baab-238">The following Windows PowerShell script will return the list of performance counters for the CounterSetName "MSRS 2014 Windows Service SharePoint Mode".</span></span>

```powershell
(Get-Counter -ListSet "MSRS 2014 Windows Service SharePoint Mode").Paths
```

## <a name="see-also"></a><span data-ttu-id="4baab-239">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4baab-239">See Also</span></span>
 <span data-ttu-id="4baab-240">监视[MSRS 2014 Web 服务和 MSRS 2014 Windows Service 性能对象 &#40;本机模式](../report-server/performance-counters-msrs-2011-web-service-performance-objects.md)的[报表服务器性能](monitoring-report-server-performance.md)性能计数器&#41;</span><span class="sxs-lookup"><span data-stu-id="4baab-240">[Monitoring Report Server Performance](monitoring-report-server-performance.md) [Performance Counters for the MSRS 2014 Web Service and MSRS 2014 Windows Service Performance Objects &#40;Native Mode&#41;](../report-server/performance-counters-msrs-2011-web-service-performance-objects.md)</span></span>