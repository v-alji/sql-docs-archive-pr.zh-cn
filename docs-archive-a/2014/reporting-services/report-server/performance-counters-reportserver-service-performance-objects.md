---
title: ReportServer： Service 和 ReportServerSharePoint： Service 性能对象的性能计数器 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Report Server service, performance counters
ms.assetid: 2bcacab2-3a4f-4aae-b123-19d756b9b9ed
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8244f22797ac284d7037bad445f12e0f9c117d55
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689778"
---
# <a name="performance-counters-for-the-reportserverservice--and-reportserversharepointservice-performance-objects"></a><span data-ttu-id="13205-102">ReportServer:Service 和 ReportServerSharePoint:Service 性能对象的性能计数器</span><span class="sxs-lookup"><span data-stu-id="13205-102">Performance Counters for the ReportServer:Service  and ReportServerSharePoint:Service Performance Objects</span></span>
  <span data-ttu-id="13205-103">本主题介绍以下 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 性能对象的性能计数器：</span><span class="sxs-lookup"><span data-stu-id="13205-103">This topic describes performance counters for the following [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] performance objects:</span></span>

-   `ReportServer:Service`

-   `ReportServerSharePoint:Service`

> [!NOTE]
>  <span data-ttu-id="13205-104">性能对象用于监视本地报表服务器上的事件。</span><span class="sxs-lookup"><span data-stu-id="13205-104">The performance objects are used to monitor events on the local report server.</span></span> <span data-ttu-id="13205-105">如果是在扩展部署中运行报表服务器，则只对当前服务器（而不是整个扩展部署）进行计数。</span><span class="sxs-lookup"><span data-stu-id="13205-105">If you are running a report server in a scale-out deployment, the counts apply to the current server and not the scale-out deployment as a whole.</span></span>

 <span data-ttu-id="13205-106">Windows 性能监视器 (**Perfmon.exe**) 中提供了性能对象。</span><span class="sxs-lookup"><span data-stu-id="13205-106">The performance objects are available in the Windows Performance Monitor (**Perfmon.exe**).</span></span> <span data-ttu-id="13205-107">有关详细信息，请参阅 Windows 文档。</span><span class="sxs-lookup"><span data-stu-id="13205-107">For more information, see the Windows documentation.</span></span> <span data-ttu-id="13205-108">[运行时分析](https://msdn.microsoft.com/library/w4bz2147.aspx) (https://msdn.microsoft.com/library/w4bz2147.aspx) 。</span><span class="sxs-lookup"><span data-stu-id="13205-108">[Runtime Profiling](https://msdn.microsoft.com/library/w4bz2147.aspx) (https://msdn.microsoft.com/library/w4bz2147.aspx).</span></span>

 <span data-ttu-id="13205-109">本主题内容：</span><span class="sxs-lookup"><span data-stu-id="13205-109">In this topic:</span></span>

-   [<span data-ttu-id="13205-110">ReportServer:Service 性能计数器（本机模式报表服务器）</span><span class="sxs-lookup"><span data-stu-id="13205-110">ReportServer:Service Performance Counters (Native Mode Report Server)</span></span>](#bkmk_ReportServer)

-   [<span data-ttu-id="13205-111">ReportServerSharePoint:Service（SharePoint 模式报表服务器）</span><span class="sxs-lookup"><span data-stu-id="13205-111">ReportServerSharePoint:Service (SharePoint Mode Report Server)</span></span>](#bkmk_ReportServerSharePoint)

-   [<span data-ttu-id="13205-112">使用 PowerShell Cmdlet 返回列表</span><span class="sxs-lookup"><span data-stu-id="13205-112">Use PowerShell Cmdlets to return lists</span></span>](#bkmk_powershell)

 [!INCLUDE[applies](../../includes/applies-md.md)]<span data-ttu-id="13205-113">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]SharePoint 模式 |本机模式。</span><span class="sxs-lookup"><span data-stu-id="13205-113">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] SharePoint mode | Native mode.</span></span>

##  <a name="reportserverservice-performance-counters-native-mode-report-server"></a><a name="bkmk_ReportServer"></a> <span data-ttu-id="13205-114">ReportServer:Service 性能计数器（本机模式报表服务器）</span><span class="sxs-lookup"><span data-stu-id="13205-114">ReportServer:Service Performance Counters (Native Mode Report Server)</span></span>
 <span data-ttu-id="13205-115">`ReportServer:Service` 性能对象包含一个计数器集合，用于跟踪报表服务器实例的与 HTTP 相关的事件以及与内存相关的事件。</span><span class="sxs-lookup"><span data-stu-id="13205-115">The `ReportServer:Service` performance object includes a collection of counters to track HTTP-related events and memory-related events for a report server instance.</span></span> <span data-ttu-id="13205-116">此性能对象对计算机上的每个 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 实例显示一次，可以在每个实例的性能对象中添加或删除计数器。</span><span class="sxs-lookup"><span data-stu-id="13205-116">This performance object appears one time for each [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] instance on the computer, and you can add or remove counters from the performance object for each instance.</span></span> <span data-ttu-id="13205-117">默认实例的计数器以 `ReportServer:Service` 格式显示。</span><span class="sxs-lookup"><span data-stu-id="13205-117">Counters for the default instance appear in the format `ReportServer:Service`.</span></span> <span data-ttu-id="13205-118">命名实例的计数器以 instance_name 格式显示 `ReportServer$<` *instance_name* `>:Service` 。</span><span class="sxs-lookup"><span data-stu-id="13205-118">Counters for named instances appear in the format `ReportServer$<`*instance_name*`>:Service`.</span></span>

 <span data-ttu-id="13205-119">`ReportServer:Service`性能对象是中的新对象 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] ，它提供了 Internet Information Services (IIS) 和以前版本中包含的计数器的子集 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="13205-119">The `ReportServer:Service` performance object was new in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], and it provides a subset of counters that were included with Internet Information Services (IIS) and [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] in previous versions of [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="13205-120">这些新计数器是特定于 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]，用于跟踪报表服务器中与 HTTP 相关的事件，例如请求、连接和登录尝试。</span><span class="sxs-lookup"><span data-stu-id="13205-120">These new counters are specific to [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], and they track HTTP-related events for the report server, such as requests, connections, and logon attempts.</span></span> <span data-ttu-id="13205-121">此外，此性能对象还包括用于跟踪内存管理事件的计数器。</span><span class="sxs-lookup"><span data-stu-id="13205-121">Additionally, this performance object includes counters to track memory management events.</span></span>

 <span data-ttu-id="13205-122">下表列出了 `ReportServer:Service` 性能对象中包含的计数器。</span><span class="sxs-lookup"><span data-stu-id="13205-122">The following table lists the counters that are included in the `ReportServer:Service` performance object.</span></span>

 <span data-ttu-id="13205-123">![与 PowerShell 相关的内容](../media/rs-powershellicon.jpg "PowerShell 相关内容") 下面的 Windows PowerShell 脚本将返回 CounterSetName 的性能计数器列表</span><span class="sxs-lookup"><span data-stu-id="13205-123">![PowerShell related content](../media/rs-powershellicon.jpg "PowerShell related content") The following Windows PowerShell script will return the list of performance counters for the CounterSetName</span></span>

```
(get-counter -listset "ReportServer:Service").paths
```

|<span data-ttu-id="13205-124">计数器</span><span class="sxs-lookup"><span data-stu-id="13205-124">Counter</span></span>|<span data-ttu-id="13205-125">说明</span><span class="sxs-lookup"><span data-stu-id="13205-125">Description</span></span>|
|-------------|-----------------|
|`Active connections`|<span data-ttu-id="13205-126">在服务器上当前活动的连接数。</span><span class="sxs-lookup"><span data-stu-id="13205-126">The number of connections currently active on the server.</span></span>|
|`Bytes Received Total`|<span data-ttu-id="13205-127">服务器接收的字节数。</span><span class="sxs-lookup"><span data-stu-id="13205-127">The number of bytes received by the server.</span></span> <span data-ttu-id="13205-128">该计数器计数报表管理器和报表服务器接收的原始字节总数。</span><span class="sxs-lookup"><span data-stu-id="13205-128">This counter counts the raw bytes received in total by both Report Manager and the report server.</span></span>|
|`Bytes Received/sec`|<span data-ttu-id="13205-129">服务器每秒接收的字节数。</span><span class="sxs-lookup"><span data-stu-id="13205-129">The number of bytes received per second by the server.</span></span> <span data-ttu-id="13205-130">该计数器只在传输完成时更新。</span><span class="sxs-lookup"><span data-stu-id="13205-130">This counter is updated only when a transfer is completed.</span></span> <span data-ttu-id="13205-131">这意味着此计数器开始保持为 0，传输完成后值会增加。</span><span class="sxs-lookup"><span data-stu-id="13205-131">This means that the counter remains at 0 and then the value increases after a transfer is complete.</span></span>|
|`Bytes Sent Total`|<span data-ttu-id="13205-132">从服务器发送的字节数。</span><span class="sxs-lookup"><span data-stu-id="13205-132">The number of bytes sent from the server.</span></span> <span data-ttu-id="13205-133">该计数器计数报表管理器和报表服务器发送的原始字节总数。</span><span class="sxs-lookup"><span data-stu-id="13205-133">This counter counts the raw bytes sent in total by both Report Manager and the report server.</span></span>|
|`Bytes Sent/sec`|<span data-ttu-id="13205-134">从服务器每秒发送的字节数。</span><span class="sxs-lookup"><span data-stu-id="13205-134">The number of bytes sent per second from the server.</span></span> <span data-ttu-id="13205-135">该计数器只在传输完成时更新。</span><span class="sxs-lookup"><span data-stu-id="13205-135">This counter is updated only when a transfer is completed.</span></span> <span data-ttu-id="13205-136">这意味着此计数器开始保持为 0，传输完成后值会增加。</span><span class="sxs-lookup"><span data-stu-id="13205-136">This means that the counter remains at 0 and then the value increases after a transfer is complete.</span></span>|
|`Errors Total`|<span data-ttu-id="13205-137">处理 HTTP 请求过程中发生的错误总数。</span><span class="sxs-lookup"><span data-stu-id="13205-137">The total number of errors that occur during the processing of HTTP requests.</span></span> <span data-ttu-id="13205-138">这些错误包括 400s 和 500s 形式的 HTTP 状态代码。</span><span class="sxs-lookup"><span data-stu-id="13205-138">These errors include HTTP status codes in the 400s and 500s.</span></span>|
|`Errors/sec`|<span data-ttu-id="13205-139">处理 HTTP 请求过程中每秒发生的错误总数。</span><span class="sxs-lookup"><span data-stu-id="13205-139">The total number of errors that occur per second during the processing of HTTP requests.</span></span> <span data-ttu-id="13205-140">这些错误包括 400s 和 500s 形式的 HTTP 状态代码。</span><span class="sxs-lookup"><span data-stu-id="13205-140">These errors include HTTP status codes in the 400s and 500s.</span></span>|
|`Logon Attempts Total`|<span data-ttu-id="13205-141">从 RSWindows 身份验证类型进行的登录尝试次数。</span><span class="sxs-lookup"><span data-stu-id="13205-141">The number of logon attempts made from RSWindows authentication types.</span></span> <span data-ttu-id="13205-142">RSWindows 身份验证类型包括 RSWindowsNegotiate、RSWindowsNTLM、RSWindowsKerberos 和 RSWindowsB asic。</span><span class="sxs-lookup"><span data-stu-id="13205-142">RSWindows authentication types include RSWindowsNegotiate, RSWindowsNTLM, RSWindowsKerberos, and RSWindowsB asic.</span></span> <span data-ttu-id="13205-143">值为零 (0) 表示自定义身份验证。</span><span class="sxs-lookup"><span data-stu-id="13205-143">The value zero (0) represents Custom authentication.</span></span>|
|`Logon Attempts/sec`|<span data-ttu-id="13205-144">登录尝试的频率。</span><span class="sxs-lookup"><span data-stu-id="13205-144">The rate of logon attempts.</span></span>|
|`Logon Successes Total`|<span data-ttu-id="13205-145">RSWindows 身份验证类型的成功登录次数。</span><span class="sxs-lookup"><span data-stu-id="13205-145">The number of successful logons for RSWindows authentication types.</span></span> <span data-ttu-id="13205-146">RSWindows 身份验证类型包括 RSWindowsNegotiate、RSWindowsNTLM、RSWindowsKerberos 和 RSWindowsB asic。</span><span class="sxs-lookup"><span data-stu-id="13205-146">RSWindows authentication types include RSWindowsNegotiate, RSWindowsNTLM, RSWindowsKerberos, and RSWindowsB asic.</span></span> <span data-ttu-id="13205-147">值为零 (0) 表示自定义身份验证。</span><span class="sxs-lookup"><span data-stu-id="13205-147">The value zero (0) represents Custom authentication.</span></span>|
|`Logon Successes/sec`|<span data-ttu-id="13205-148">登录成功率。</span><span class="sxs-lookup"><span data-stu-id="13205-148">The rate of successful logons.</span></span>|
|`Memory Pressure State`|<span data-ttu-id="13205-149">以下从 1-5 的数字，指示服务器的当前内存状态：</span><span class="sxs-lookup"><span data-stu-id="13205-149">One of the following numbers, from 1-5, which indicates the current memory state of the server:</span></span><br /><br /> <span data-ttu-id="13205-150">1：没有压力</span><span class="sxs-lookup"><span data-stu-id="13205-150">1: No pressure</span></span><br /><br /> <span data-ttu-id="13205-151">2：低压力</span><span class="sxs-lookup"><span data-stu-id="13205-151">2: Low pressure</span></span><br /><br /> <span data-ttu-id="13205-152">3：中等压力</span><span class="sxs-lookup"><span data-stu-id="13205-152">3: Medium pressure</span></span><br /><br /> <span data-ttu-id="13205-153">4：高压力</span><span class="sxs-lookup"><span data-stu-id="13205-153">4: High pressure</span></span><br /><br /> <span data-ttu-id="13205-154">5：过度压力</span><span class="sxs-lookup"><span data-stu-id="13205-154">5: Exceeded pressure</span></span>|
|`Memory Shrink Amount`|<span data-ttu-id="13205-155">服务器请求缩小使用中内存的字节数。</span><span class="sxs-lookup"><span data-stu-id="13205-155">The number of bytes that the server requested to shrink the memory in use.</span></span>|
|`Memory Shrink Notifications/sec`|<span data-ttu-id="13205-156">服务器上一秒内发出的缩小使用中内存的通知数。</span><span class="sxs-lookup"><span data-stu-id="13205-156">The number of notifications that the server issued in the last second to shrink the memory in use.</span></span> <span data-ttu-id="13205-157">该值表示服务器经历内存压力的频率。</span><span class="sxs-lookup"><span data-stu-id="13205-157">This value indicates how often the server experiences memory pressure.</span></span>|
|`Requests Disconnected`|<span data-ttu-id="13205-158">由于通信故障而断开连接的请求数。</span><span class="sxs-lookup"><span data-stu-id="13205-158">The number of requests that are disconnected because of a communication failure.</span></span>|
|`Requests Executing`|<span data-ttu-id="13205-159">当前正在处理的请求数。</span><span class="sxs-lookup"><span data-stu-id="13205-159">The number of requests that are currently processing.</span></span>|
|`Requests Not Authorized`|<span data-ttu-id="13205-160">失败并返回 HTTP 401 状态代码的请求数。</span><span class="sxs-lookup"><span data-stu-id="13205-160">The number of requests that fail with an HTTP 401 status code.</span></span>|
|`Requests Rejected`|<span data-ttu-id="13205-161">由于服务器资源不足而未处理的请求总数。</span><span class="sxs-lookup"><span data-stu-id="13205-161">The total number of requests that were not processed because of insufficient server resources.</span></span> <span data-ttu-id="13205-162">该计数器表示返回 HTTP 503 状态代码（指示服务器太忙）的请求数。</span><span class="sxs-lookup"><span data-stu-id="13205-162">This counter represents the number of requests that return a HTTP 503 status code, which indicates that the server is too busy.</span></span>|
|`Requests Total`|<span data-ttu-id="13205-163">报表服务器服务启动后接收到的请求总数。</span><span class="sxs-lookup"><span data-stu-id="13205-163">The total number of requests that are received by the report server service since startup.</span></span> <span data-ttu-id="13205-164">此计数器计数发送给报表管理器的请求数以及从报表管理器发送给报表服务器的请求数。</span><span class="sxs-lookup"><span data-stu-id="13205-164">This counter counts requests that are sent to Report Manager and requests that are sent from Report Manager to the report server.</span></span>|
|`Requests/sec`|<span data-ttu-id="13205-165">每秒处理的请求数。</span><span class="sxs-lookup"><span data-stu-id="13205-165">The number of requests that are processed per second.</span></span> <span data-ttu-id="13205-166">该值表示应用程序的当前吞吐量。</span><span class="sxs-lookup"><span data-stu-id="13205-166">This value represents the current throughput of the application.</span></span>|
|`Tasks Queued`|<span data-ttu-id="13205-167">等待线程变为可供处理的任务数。</span><span class="sxs-lookup"><span data-stu-id="13205-167">The number of tasks that are waiting for a thread to become available for processing.</span></span> <span data-ttu-id="13205-168">向报表服务器发出的每个请求都与一个或多个任务对应。</span><span class="sxs-lookup"><span data-stu-id="13205-168">Each request made to the report server corresponds to one or more tasks.</span></span> <span data-ttu-id="13205-169">此计数器只表示可以处理的任务数量，不包括当前正在运行的任务数量。</span><span class="sxs-lookup"><span data-stu-id="13205-169">This counter represents only the number of tasks that are ready for processing; it does not include the number of tasks that are currently running.</span></span>|

##  <a name="reportserversharepointservice-sharepoint-mode-report-server"></a><a name="bkmk_ReportServerSharePoint"></a><span data-ttu-id="13205-170">ReportServerSharePoint： Service (SharePoint 模式报表服务器) </span><span class="sxs-lookup"><span data-stu-id="13205-170">ReportServerSharePoint:Service (SharePoint Mode Report Server)</span></span>
 <span data-ttu-id="13205-171">`ReportServerSharePoint:Service`已在中添加了性能对象 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="13205-171">The `ReportServerSharePoint:Service` performance object was added in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>

 <span data-ttu-id="13205-172">![与 PowerShell 相关的内容](../media/rs-powershellicon.jpg "PowerShell 相关内容") 下面的 Windows PowerShell 脚本将返回 CounterSetName 的性能计数器列表</span><span class="sxs-lookup"><span data-stu-id="13205-172">![PowerShell related content](../media/rs-powershellicon.jpg "PowerShell related content") The following Windows PowerShell script will return the list of performance counters for the CounterSetName</span></span>

```
(get-counter -listset "ReportServerSharePoint:Service").paths
```

|<span data-ttu-id="13205-173">计数器</span><span class="sxs-lookup"><span data-stu-id="13205-173">Counter</span></span>|
|-------------|
|`Memory Pressure State`|
|`Memory Shrink Amount`|
|`Memory Shrink Notifications/Sec`|

##  <a name="use-powershell-cmdlets-to-return-lists"></a><a name="bkmk_powershell"></a><span data-ttu-id="13205-174">使用 PowerShell Cmdlet 返回列表</span><span class="sxs-lookup"><span data-stu-id="13205-174">Use PowerShell Cmdlets to return lists</span></span>
 <span data-ttu-id="13205-175">![与 PowerShell 相关的内容](../media/rs-powershellicon.jpg "PowerShell 相关内容") 下面的 Windows PowerShell 脚本将返回 CounterSetName“ReportServerSharePoint:Service”的性能计数器列表：</span><span class="sxs-lookup"><span data-stu-id="13205-175">![PowerShell related content](../media/rs-powershellicon.jpg "PowerShell related content") The following Windows PowerShell script will return the list of performance counters for the CounterSetName "ReportServerSharePoint:Service":</span></span>

```
(get-counter -listset "ReportServerSharePoint:Service").paths
```

## <a name="see-also"></a><span data-ttu-id="13205-176">另请参阅</span><span class="sxs-lookup"><span data-stu-id="13205-176">See Also</span></span>
 <span data-ttu-id="13205-177">[Monitoring Report Server Performance](monitoring-report-server-performance.md) [为 MSRS 2014 WEB 服务和 MSRS 2014 Windows Service 性能对象监视报表服务器性能性能计数器 &#40;纯模式&#41;](../report-server/performance-counters-msrs-2011-web-service-performance-objects.md) [MSRS 2014 Web SERVICE sharepoint 模式和 MSRS 2014 Windows service Sharepoint mode 性能 &#40;对象的性能计数器&#41;] .。。/performance-counters-msrs-2011-sharepoint-mode-performance-objects.md) </span><span class="sxs-lookup"><span data-stu-id="13205-177">[Monitoring Report Server Performance](monitoring-report-server-performance.md) [Performance Counters for the MSRS 2014 Web Service and MSRS 2014 Windows Service Performance Objects &#40;Native Mode&#41;](../report-server/performance-counters-msrs-2011-web-service-performance-objects.md) [Performance Counters for the MSRS 2014 Web Service SharePoint Mode and MSRS 2014 Windows Service SharePoint Mode Performance Objects &#40;SharePoint Mode&#41;]../performance-counters-msrs-2011-sharepoint-mode-performance-objects.md)</span></span>


