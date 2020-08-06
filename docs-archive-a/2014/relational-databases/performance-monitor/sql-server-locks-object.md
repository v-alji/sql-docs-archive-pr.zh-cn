---
title: SQL Server - Locks 对象 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Locks object
- SQLServer:Locks
ms.assetid: ace04f0d-3993-4444-8317-ca39d7087e49
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f13d4ea1172d6b32b90c045a45445c5c87f48a94
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578824"
---
# <a name="sql-server-locks-object"></a><span data-ttu-id="34273-102">SQL Server Locks 对象</span><span class="sxs-lookup"><span data-stu-id="34273-102">SQL Server, Locks Object</span></span>
  <span data-ttu-id="34273-103">Microsoft **中的** SQLServer:Locks [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 对象提供了有关各种资源类型的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 锁的信息。</span><span class="sxs-lookup"><span data-stu-id="34273-103">The **SQLServer:Locks** object in Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] locks on individual resource types.</span></span> <span data-ttu-id="34273-104">锁加在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 资源上（如在一个事务中读取或修改的行），以防止各种事务并发使用资源。</span><span class="sxs-lookup"><span data-stu-id="34273-104">Locks are held on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resources, such as rows read or modified during a transaction, to prevent concurrent use of resources by different transactions.</span></span> <span data-ttu-id="34273-105">例如，如果一个排它 (X) 锁被一个事务加在某一表的某一行上，在这个锁被释放前，其他事务都不可以修改这一行。</span><span class="sxs-lookup"><span data-stu-id="34273-105">For example, if an exclusive (X) lock is held on a row within a table by a transaction, no other transaction can modify that row until the lock is released.</span></span> <span data-ttu-id="34273-106">尽可能少使用锁可提高并发性，从而改善性能。</span><span class="sxs-lookup"><span data-stu-id="34273-106">Minimizing locks increases concurrency, which can improve performance.</span></span> <span data-ttu-id="34273-107">可以同时监视 **Locks** 对象的多个实例，每个实例代表一个资源类型上的一个锁。</span><span class="sxs-lookup"><span data-stu-id="34273-107">Multiple instances of the **Locks** object can be monitored at the same time, with each instance representing a lock on a resource type.</span></span>  
  
 <span data-ttu-id="34273-108">下表介绍了 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Locks 计数器。</span><span class="sxs-lookup"><span data-stu-id="34273-108">This table describes the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Locks** counters.</span></span>  
  
|<span data-ttu-id="34273-109">SQL Server Locks 计数器</span><span class="sxs-lookup"><span data-stu-id="34273-109">SQL Server Locks counters</span></span>|<span data-ttu-id="34273-110">说明</span><span class="sxs-lookup"><span data-stu-id="34273-110">Description</span></span>|  
|-------------------------------|-----------------|  
|<span data-ttu-id="34273-111">**Average Wait Time (ms)**</span><span class="sxs-lookup"><span data-stu-id="34273-111">**Average Wait Time (ms)**</span></span>|<span data-ttu-id="34273-112">每个导致等待的锁请求的平均等待时间（毫秒）。</span><span class="sxs-lookup"><span data-stu-id="34273-112">Average amount of wait time (in milliseconds) for each lock request that resulted in a wait.</span></span>|  
|<span data-ttu-id="34273-113">**Lock Requests/sec**</span><span class="sxs-lookup"><span data-stu-id="34273-113">**Lock Requests/sec**</span></span>|<span data-ttu-id="34273-114">锁管理器每秒请求的新锁和锁转换数。</span><span class="sxs-lookup"><span data-stu-id="34273-114">Number of new locks and lock conversions per second requested from the lock manager.</span></span>|  
|<span data-ttu-id="34273-115">**Lock Timeouts (timeout > 0)/sec**</span><span class="sxs-lookup"><span data-stu-id="34273-115">**Lock Timeouts (timeout > 0)/sec**</span></span>|<span data-ttu-id="34273-116">每秒超时的锁请求数，但不包括对 NOWAIT 锁的请求。</span><span class="sxs-lookup"><span data-stu-id="34273-116">Number of lock requests per second that timed out, but excluding requests for NOWAIT locks.</span></span>|  
|<span data-ttu-id="34273-117">**Lock Timeouts/sec**</span><span class="sxs-lookup"><span data-stu-id="34273-117">**Lock Timeouts/sec**</span></span>|<span data-ttu-id="34273-118">每秒超时的锁请求数，包括对 NOWAIT 锁的请求。</span><span class="sxs-lookup"><span data-stu-id="34273-118">Number of lock requests per second that timed out, including requests for NOWAIT locks.</span></span>|  
|<span data-ttu-id="34273-119">**Lock Wait Time (ms)**</span><span class="sxs-lookup"><span data-stu-id="34273-119">**Lock Wait Time (ms)**</span></span>|<span data-ttu-id="34273-120">锁在最后一秒内的总等待时间（毫秒）。</span><span class="sxs-lookup"><span data-stu-id="34273-120">Total wait time (in milliseconds) for locks in the last second.</span></span>|  
|<span data-ttu-id="34273-121">**Lock Waits/sec**</span><span class="sxs-lookup"><span data-stu-id="34273-121">**Lock Waits/sec**</span></span>|<span data-ttu-id="34273-122">每秒要求调用者等待的锁请求数。</span><span class="sxs-lookup"><span data-stu-id="34273-122">Number of lock requests per second that required the caller to wait.</span></span>|  
|<span data-ttu-id="34273-123">**Number of Deadlocks/sec**</span><span class="sxs-lookup"><span data-stu-id="34273-123">**Number of Deadlocks/sec**</span></span>|<span data-ttu-id="34273-124">每秒导致死锁的锁请求数。</span><span class="sxs-lookup"><span data-stu-id="34273-124">Number of lock requests per second that resulted in a deadlock.</span></span>|  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="34273-125">可以锁定下列这些资源。</span><span class="sxs-lookup"><span data-stu-id="34273-125">can lock these resources.</span></span>  
  
|<span data-ttu-id="34273-126">项</span><span class="sxs-lookup"><span data-stu-id="34273-126">Item</span></span>|<span data-ttu-id="34273-127">说明</span><span class="sxs-lookup"><span data-stu-id="34273-127">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="34273-128">**_Total**</span><span class="sxs-lookup"><span data-stu-id="34273-128">**_Total**</span></span>|<span data-ttu-id="34273-129">所有锁的信息。</span><span class="sxs-lookup"><span data-stu-id="34273-129">Information for all locks.</span></span>|  
|<span data-ttu-id="34273-130">**分配单元**</span><span class="sxs-lookup"><span data-stu-id="34273-130">**AllocUnit**</span></span>|<span data-ttu-id="34273-131">分配单元的锁。</span><span class="sxs-lookup"><span data-stu-id="34273-131">A lock on an allocation unit.</span></span>|  
|<span data-ttu-id="34273-132">**应用程序**</span><span class="sxs-lookup"><span data-stu-id="34273-132">**Application**</span></span>|<span data-ttu-id="34273-133">锁定指定了应用程序的资源。</span><span class="sxs-lookup"><span data-stu-id="34273-133">A lock on an application-specified resource.</span></span>|  
|<span data-ttu-id="34273-134">**Database**</span><span class="sxs-lookup"><span data-stu-id="34273-134">**Database**</span></span>|<span data-ttu-id="34273-135">锁定数据库（包括数据库中的所有对象）。</span><span class="sxs-lookup"><span data-stu-id="34273-135">A lock on a database, including all objects in the database.</span></span>|  
|<span data-ttu-id="34273-136">**扩展盘区**</span><span class="sxs-lookup"><span data-stu-id="34273-136">**Extent**</span></span>|<span data-ttu-id="34273-137">锁定由连续的 8 个页构成的一组。</span><span class="sxs-lookup"><span data-stu-id="34273-137">A lock on a contiguous group of 8 pages.</span></span>|  
|<span data-ttu-id="34273-138">**File**</span><span class="sxs-lookup"><span data-stu-id="34273-138">**File**</span></span>|<span data-ttu-id="34273-139">锁定数据库文件。</span><span class="sxs-lookup"><span data-stu-id="34273-139">A lock on a database file.</span></span>|  
|<span data-ttu-id="34273-140">**堆/B 树**</span><span class="sxs-lookup"><span data-stu-id="34273-140">**Heap/BTree**</span></span>|<span data-ttu-id="34273-141">堆或 B 树 (HOBT)。</span><span class="sxs-lookup"><span data-stu-id="34273-141">Heap or BTree (HOBT).</span></span> <span data-ttu-id="34273-142">锁定数据页堆，或索引的 B 树结构。</span><span class="sxs-lookup"><span data-stu-id="34273-142">A lock on a heap of data pages, or on the BTree structure of an index.</span></span>|  
|<span data-ttu-id="34273-143">**Key**</span><span class="sxs-lookup"><span data-stu-id="34273-143">**Key**</span></span>|<span data-ttu-id="34273-144">锁定索引中的某行。</span><span class="sxs-lookup"><span data-stu-id="34273-144">A lock on a row in an index.</span></span>|  
|<span data-ttu-id="34273-145">**元数据**</span><span class="sxs-lookup"><span data-stu-id="34273-145">**Metadata**</span></span>|<span data-ttu-id="34273-146">锁定一些目录信息（又称为元数据）。</span><span class="sxs-lookup"><span data-stu-id="34273-146">A lock on a piece of catalog information, also called metadata.</span></span>|  
|<span data-ttu-id="34273-147">**Object**</span><span class="sxs-lookup"><span data-stu-id="34273-147">**Object**</span></span>|<span data-ttu-id="34273-148">锁定表、存储过程、视图等（包括所有数据和索引）。</span><span class="sxs-lookup"><span data-stu-id="34273-148">A lock on table, stored procedure, view, etc, including all data and indexes.</span></span> <span data-ttu-id="34273-149">该对象可以是包含 **sys.all_objects**中某项的任何一个对象。</span><span class="sxs-lookup"><span data-stu-id="34273-149">The object can be anything that has an entry in **sys.all_objects**.</span></span>|  
|<span data-ttu-id="34273-150">**第**</span><span class="sxs-lookup"><span data-stu-id="34273-150">**Page**</span></span>|<span data-ttu-id="34273-151">锁定数据库中 8 KB 页。</span><span class="sxs-lookup"><span data-stu-id="34273-151">A lock on an 8-kilobyte (KB) page in a database.</span></span>|  
|<span data-ttu-id="34273-152">**RID**</span><span class="sxs-lookup"><span data-stu-id="34273-152">**RID**</span></span>|<span data-ttu-id="34273-153">行 ID。</span><span class="sxs-lookup"><span data-stu-id="34273-153">Row ID.</span></span> <span data-ttu-id="34273-154">锁定一个堆中的一行。</span><span class="sxs-lookup"><span data-stu-id="34273-154">A lock on a single row in a heap.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="34273-155">另请参阅</span><span class="sxs-lookup"><span data-stu-id="34273-155">See Also</span></span>  
 [<span data-ttu-id="34273-156">监视资源使用情况（系统监视器）</span><span class="sxs-lookup"><span data-stu-id="34273-156">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  
