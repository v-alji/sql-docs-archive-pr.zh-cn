---
title: 监视 CPU 使用率 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- monitoring performance [SQL Server], CPU usage
- tuning databases [SQL Server], CPU usage
- processors [SQL Server], monitoring usage
- database performance [SQL Server], CPU usage
- monitoring CPU usage [SQL Server]
- server performance [SQL Server], CPU usage
- database monitoring [SQL Server], CPU usage
- monitoring [SQL Server], CPU usage
- processors [SQL Server]
- CPU [SQL Server], monitoring
- monitoring server performance [SQL Server], CPU usage
ms.assetid: 2a02a3b6-07b2-4ad0-8a24-670414d19812
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f08d49348fd25593f27a87f2b0123f7ce43e35b5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692862"
---
# <a name="monitor-cpu-usage"></a><span data-ttu-id="a0610-102">监视 CPU 使用率</span><span class="sxs-lookup"><span data-stu-id="a0610-102">Monitor CPU Usage</span></span>
  <span data-ttu-id="a0610-103">定期监视 Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例以确定 CPU 使用率是否在正常范围内。</span><span class="sxs-lookup"><span data-stu-id="a0610-103">Monitor an instance of Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] periodically to determine whether CPU usage rates are within normal ranges.</span></span> <span data-ttu-id="a0610-104">持续的高 CPU 使用率可能表明需要升级 CPU 或需要增加多个处理器。</span><span class="sxs-lookup"><span data-stu-id="a0610-104">A continually high rate of CPU usage may indicate the need to upgrade the CPU or add multiple processors.</span></span> <span data-ttu-id="a0610-105">或者，高 CPU 使用率也可能表明应用程序的调整或设计不良。</span><span class="sxs-lookup"><span data-stu-id="a0610-105">Alternatively, a high CPU usage rate may indicate a poorly tuned or designed application.</span></span> <span data-ttu-id="a0610-106">优化应用程序可以降低 CPU 的使用率。</span><span class="sxs-lookup"><span data-stu-id="a0610-106">Optimizing the application can lower CPU utilization.</span></span>  
  
 <span data-ttu-id="a0610-107">一个确定 CPU 使用率的有效方法是使用系统监视器中的 **Processor:% Processor Time** 计数器。</span><span class="sxs-lookup"><span data-stu-id="a0610-107">An efficient way to determine CPU usage is to use the **Processor:% Processor Time** counter in System Monitor.</span></span> <span data-ttu-id="a0610-108">该计数器监视 CPU 执行非闲置线程所用的时间。</span><span class="sxs-lookup"><span data-stu-id="a0610-108">This counter monitors the amount of time the CPU spends executing a thread that is not idle.</span></span> <span data-ttu-id="a0610-109">持续 80% 到 90% 的状态可能表明需要升级 CPU 或需要增加更多的处理器。</span><span class="sxs-lookup"><span data-stu-id="a0610-109">A consistent state of 80 percent to 90 percent may indicate the need to upgrade your CPU or add more processors.</span></span> <span data-ttu-id="a0610-110">对于多处理器系统，应为每个处理器监视一个该计数器的独立实例。</span><span class="sxs-lookup"><span data-stu-id="a0610-110">For multiprocessor systems, monitor a separate instance of this counter for each processor.</span></span> <span data-ttu-id="a0610-111">这一值代表了在一个特定处理器上的处理器时间之和。</span><span class="sxs-lookup"><span data-stu-id="a0610-111">This value represents the sum of processor time on a specific processor.</span></span> <span data-ttu-id="a0610-112">若要确定所有处理器的平均时间，请改用 **System: %Total Processor Time** 计数器。</span><span class="sxs-lookup"><span data-stu-id="a0610-112">To determine the average for all processors, use the **System: %Total Processor Time** counter instead.</span></span>  
  
 <span data-ttu-id="a0610-113">另外还可以监视下列计数器来监视处理器的使用率：</span><span class="sxs-lookup"><span data-stu-id="a0610-113">Optionally, you can also monitor the following counters to monitor processor usage:</span></span>  
  
-   <span data-ttu-id="a0610-114">**Processor: % Privileged Time**</span><span class="sxs-lookup"><span data-stu-id="a0610-114">**Processor: % Privileged Time**</span></span>  
  
     <span data-ttu-id="a0610-115">对应于处理器执行 Microsoft Windows 内核命令（例如处理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] I/O 请求）所用时间的百分比。</span><span class="sxs-lookup"><span data-stu-id="a0610-115">Corresponds to the percentage of time the processor spends on execution of Microsoft Windows kernel commands, such as processing of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] I/O requests.</span></span> <span data-ttu-id="a0610-116">如果 **Physical Disk** 计数器的值很高时该计数器的值也一直很高，则考虑安装速度更快或效率更高的磁盘子系统。</span><span class="sxs-lookup"><span data-stu-id="a0610-116">If this counter is consistently high when the **Physical Disk** counters are high, consider installing a faster or more efficient disk subsystem.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a0610-117">不同的磁盘控制器和驱动程序所用的内核处理时间不同。</span><span class="sxs-lookup"><span data-stu-id="a0610-117">Different disk controllers and drivers use different amounts of kernel processing time.</span></span> <span data-ttu-id="a0610-118">高效的控制器和驱动程序所用的特权时间较少，可留出更多的处理器时间给用户应用程序，从而提高总体的吞吐量。</span><span class="sxs-lookup"><span data-stu-id="a0610-118">Efficient controllers and drivers use less privileged time, leaving more processing time available for user applications, increasing overall throughput.</span></span>  
  
-   <span data-ttu-id="a0610-119">**Processor: %User Time**</span><span class="sxs-lookup"><span data-stu-id="a0610-119">**Processor: %User Time**</span></span>  
  
     <span data-ttu-id="a0610-120">对应于处理器执行用户进程（例如 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]）所用时间的百分比。</span><span class="sxs-lookup"><span data-stu-id="a0610-120">Corresponds to the percentage of time that the processor spends on executing user processes such as [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="a0610-121">**系统：Processor Queue Length**</span><span class="sxs-lookup"><span data-stu-id="a0610-121">**System: Processor Queue Length**</span></span>  
  
     <span data-ttu-id="a0610-122">对应于等待处理器时间的线程数。</span><span class="sxs-lookup"><span data-stu-id="a0610-122">Corresponds to the number of threads waiting for processor time.</span></span> <span data-ttu-id="a0610-123">当一个进程的线程需要的处理器循环数超过可获得的循环数时，就产生了处理器瓶颈。</span><span class="sxs-lookup"><span data-stu-id="a0610-123">A processor bottleneck develops when threads of a process require more processor cycles than are available.</span></span> <span data-ttu-id="a0610-124">如果有很多进程在争用处理器时间，可能需要安装一个速度更快的处理器。</span><span class="sxs-lookup"><span data-stu-id="a0610-124">If more than a few processes attempt to utilize the processor's time, you might need to install a faster processor.</span></span> <span data-ttu-id="a0610-125">如果使用的是多处理器系统，则可以增加一个处理器。</span><span class="sxs-lookup"><span data-stu-id="a0610-125">Or, if you have a multiprocessor system, you could add a processor.</span></span>  
  
 <span data-ttu-id="a0610-126">检查处理器使用率时，需考虑 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例执行的工作类型。</span><span class="sxs-lookup"><span data-stu-id="a0610-126">When you examine processor usage, consider the type of work that the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] performs.</span></span> <span data-ttu-id="a0610-127">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 正在做大量的运算，例如包含聚合的查询，或受内存限制但不需要磁盘 I/O 的查询，此时所用的处理器时间可能是 100%。</span><span class="sxs-lookup"><span data-stu-id="a0610-127">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] performs many calculations, such as queries involving aggregates or memory-bound queries that require no disk I/O, 100 percent of the processor's time can be used.</span></span> <span data-ttu-id="a0610-128">如果这导致其他应用程序的性能降低，应尝试改变工作负荷。</span><span class="sxs-lookup"><span data-stu-id="a0610-128">If this causes the performance of other applications to suffer, try changing the workload.</span></span> <span data-ttu-id="a0610-129">例如，让计算机只运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例。</span><span class="sxs-lookup"><span data-stu-id="a0610-129">For example, dedicate the computer to running the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="a0610-130">若使用率为 100% 左右（表示在处理大量的客户端请求），可能表示进程正在排队，等待处理器时间，并因而导致出现瓶颈。</span><span class="sxs-lookup"><span data-stu-id="a0610-130">Usage rates around 100 percent, where many client requests are being processed, may indicate that processes are queuing up, waiting for processor time, and causing a bottleneck.</span></span> <span data-ttu-id="a0610-131">可以通过增加速度更快的处理器来解决这一问题。</span><span class="sxs-lookup"><span data-stu-id="a0610-131">Resolve the problem by adding faster processors.</span></span>  
  
  
