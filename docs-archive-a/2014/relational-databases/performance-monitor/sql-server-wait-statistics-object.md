---
title: SQL Server - Wait Statistics 对象 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Wait Statistics object
- SQLServer:Wait Statistics
ms.assetid: cb7f917d-4291-4115-9b78-ee7692ebbb2d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5cfd2f1309cb118896ff7951b7f82feb38de60e7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687791"
---
# <a name="sql-server-wait-statistics-object"></a><span data-ttu-id="0d360-102">SQL Server Wait Statistics 对象</span><span class="sxs-lookup"><span data-stu-id="0d360-102">SQL Server, Wait Statistics Object</span></span>
  <span data-ttu-id="0d360-103">**SQLServer:Wait Statistics** 性能对象包含报告有关等待状态的性能计数器。</span><span class="sxs-lookup"><span data-stu-id="0d360-103">The **SQLServer:Wait Statistics** performance object contains performance counters that report information about wait status.</span></span>  
  
 <span data-ttu-id="0d360-104">下表列出了 Wait Statistics 对象包含的计数器。</span><span class="sxs-lookup"><span data-stu-id="0d360-104">The table below lists the counters that the Wait Statistics object contains.</span></span>  
  
|<span data-ttu-id="0d360-105">SQL Server Wait Statistics 计数器</span><span class="sxs-lookup"><span data-stu-id="0d360-105">SQL Server Wait Statistics counters</span></span>|<span data-ttu-id="0d360-106">说明</span><span class="sxs-lookup"><span data-stu-id="0d360-106">Description</span></span>|  
|-----------------------------------------|-----------------|  
|<span data-ttu-id="0d360-107">**Lock waits**</span><span class="sxs-lookup"><span data-stu-id="0d360-107">**Lock waits**</span></span>|<span data-ttu-id="0d360-108">等待锁的进程的统计信息。</span><span class="sxs-lookup"><span data-stu-id="0d360-108">Statistics for processes waiting on a lock.</span></span>|  
|<span data-ttu-id="0d360-109">**Log buffer waits**</span><span class="sxs-lookup"><span data-stu-id="0d360-109">**Log buffer waits**</span></span>|<span data-ttu-id="0d360-110">等待日志缓冲区可用的进程的统计信息。</span><span class="sxs-lookup"><span data-stu-id="0d360-110">Statistics for processes waiting for log buffer to be available.</span></span>|  
|<span data-ttu-id="0d360-111">**Log write waits**</span><span class="sxs-lookup"><span data-stu-id="0d360-111">**Log write waits**</span></span>|<span data-ttu-id="0d360-112">等待写入日志缓冲区的进程的统计信息。</span><span class="sxs-lookup"><span data-stu-id="0d360-112">Statistics for processes waiting for log buffer to be written.</span></span>|  
|<span data-ttu-id="0d360-113">**Memory grant queue waits**</span><span class="sxs-lookup"><span data-stu-id="0d360-113">**Memory grant queue waits**</span></span>|<span data-ttu-id="0d360-114">等待内存授予的进程的统计信息。</span><span class="sxs-lookup"><span data-stu-id="0d360-114">Statistics for processes waiting for memory grant to become available.</span></span>|  
|<span data-ttu-id="0d360-115">**Network IO waits**</span><span class="sxs-lookup"><span data-stu-id="0d360-115">**Network IO waits**</span></span>|<span data-ttu-id="0d360-116">与等待网络 I/O 相关的统计信息。</span><span class="sxs-lookup"><span data-stu-id="0d360-116">Statistics relevant to wait on network I/O.</span></span>|  
|<span data-ttu-id="0d360-117">**Non-Page latch waits**</span><span class="sxs-lookup"><span data-stu-id="0d360-117">**Non-Page latch waits**</span></span>|<span data-ttu-id="0d360-118">与非页闩锁相关的统计信息。</span><span class="sxs-lookup"><span data-stu-id="0d360-118">Statistics relevant to non-page latches.</span></span>|  
|<span data-ttu-id="0d360-119">**Page IO latch waits**</span><span class="sxs-lookup"><span data-stu-id="0d360-119">**Page IO latch waits**</span></span>|<span data-ttu-id="0d360-120">与页 I/O 闩锁相关的统计信息。</span><span class="sxs-lookup"><span data-stu-id="0d360-120">Statistics relevant to page I/O latches.</span></span>|  
|<span data-ttu-id="0d360-121">**Page latch waits**</span><span class="sxs-lookup"><span data-stu-id="0d360-121">**Page latch waits**</span></span>|<span data-ttu-id="0d360-122">与页闩锁（不包括 I/O 闩锁）相关的统计信息。</span><span class="sxs-lookup"><span data-stu-id="0d360-122">Statistics relevant to page latches, not including I/O latches.</span></span>|  
|<span data-ttu-id="0d360-123">**Thread-safe memory objects waits**</span><span class="sxs-lookup"><span data-stu-id="0d360-123">**Thread-safe memory objects waits**</span></span>|<span data-ttu-id="0d360-124">等待线程安全内存分配器的进程的统计信息。</span><span class="sxs-lookup"><span data-stu-id="0d360-124">Statistics for processes waiting on thread-safe memory allocators.</span></span>|  
|<span data-ttu-id="0d360-125">**Transaction ownership waits**</span><span class="sxs-lookup"><span data-stu-id="0d360-125">**Transaction ownership waits**</span></span>|<span data-ttu-id="0d360-126">与同步访问事务的进程相关的统计信息。</span><span class="sxs-lookup"><span data-stu-id="0d360-126">Statistics relevant to processes synchronizing access to transaction.</span></span>|  
|<span data-ttu-id="0d360-127">**Wait for the worker**</span><span class="sxs-lookup"><span data-stu-id="0d360-127">**Wait for the worker**</span></span>|<span data-ttu-id="0d360-128">与等待工作线程变得可用的进程相关的统计信息。</span><span class="sxs-lookup"><span data-stu-id="0d360-128">Statistics relevant to processes waiting for worker to become available.</span></span>|  
|<span data-ttu-id="0d360-129">**Workspace synchronization waits**</span><span class="sxs-lookup"><span data-stu-id="0d360-129">**Workspace synchronization waits**</span></span>|<span data-ttu-id="0d360-130">与同步访问工作空间的进程相关的统计信息。</span><span class="sxs-lookup"><span data-stu-id="0d360-130">Statistics relevant to processes synchronizing access to workspace.</span></span>|  
  
 <span data-ttu-id="0d360-131">对象中的每个计数器均包含以下实例：</span><span class="sxs-lookup"><span data-stu-id="0d360-131">Each counter in the object contains the following instances:</span></span>  
  
|<span data-ttu-id="0d360-132">项</span><span class="sxs-lookup"><span data-stu-id="0d360-132">Item</span></span>|<span data-ttu-id="0d360-133">说明</span><span class="sxs-lookup"><span data-stu-id="0d360-133">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="0d360-134">**平均等待时间(ms)**</span><span class="sxs-lookup"><span data-stu-id="0d360-134">**Average wait time (ms)**</span></span>|<span data-ttu-id="0d360-135">所选类型等待的平均等待时间。</span><span class="sxs-lookup"><span data-stu-id="0d360-135">Average time for the selected type of wait.</span></span>|  
|<span data-ttu-id="0d360-136">**每秒的累积等待时间(ms)**</span><span class="sxs-lookup"><span data-stu-id="0d360-136">**Cumulative wait time (ms) per second**</span></span>|<span data-ttu-id="0d360-137">所选类型等待的每秒累积等待时间。</span><span class="sxs-lookup"><span data-stu-id="0d360-137">Aggregated wait time per second, for the selected type of wait.</span></span>|  
|<span data-ttu-id="0d360-138">**正在进行的等待数**</span><span class="sxs-lookup"><span data-stu-id="0d360-138">**Waits in progress**</span></span>|<span data-ttu-id="0d360-139">当前正在等待的以下类型的进程数。</span><span class="sxs-lookup"><span data-stu-id="0d360-139">Number of processes currently waiting on the following type.</span></span>|  
|<span data-ttu-id="0d360-140">**每秒启动的等待数**</span><span class="sxs-lookup"><span data-stu-id="0d360-140">**Waits started per second**</span></span>|<span data-ttu-id="0d360-141">每秒启动的所选类型等待的等待数。</span><span class="sxs-lookup"><span data-stu-id="0d360-141">Number of waits started per second of the selected type of wait.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0d360-142">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0d360-142">See Also</span></span>  
 [<span data-ttu-id="0d360-143">监视资源使用情况（系统监视器）</span><span class="sxs-lookup"><span data-stu-id="0d360-143">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  
