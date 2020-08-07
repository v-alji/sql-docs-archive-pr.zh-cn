---
title: SQL Server，数据库副本 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- SQLServer:Database Replica
- performance counters [SQL Server], AlwaysOn Availability Groups
- Availability Groups [SQL Server], performance counters
ms.assetid: a5f6bdce-2b13-4924-aaeb-b50b57d624d8
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c8830ae30ad3514e107b718f9a02fef873e20295
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588992"
---
# <a name="sql-server-database-replica"></a><span data-ttu-id="2aea4-102">SQL Server，数据库副本</span><span class="sxs-lookup"><span data-stu-id="2aea4-102">SQL Server, Database Replica</span></span>
  <span data-ttu-id="2aea4-103">**SQLServer:Database Replica** 性能对象包含的性能计数器报告有关 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中 AlwaysOn 可用性组的辅助数据库的信息。</span><span class="sxs-lookup"><span data-stu-id="2aea4-103">The **SQLServer:Database Replica** performance object contains performance counters that report information about the secondary databases of an AlwaysOn availability group in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="2aea4-104">此对象仅在承载辅助副本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例上有效。</span><span class="sxs-lookup"><span data-stu-id="2aea4-104">This object is valid only on an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that hosts a secondary replica.</span></span>  
  
|<span data-ttu-id="2aea4-105">计数器名称</span><span class="sxs-lookup"><span data-stu-id="2aea4-105">Counter Name</span></span>|<span data-ttu-id="2aea4-106">说明</span><span class="sxs-lookup"><span data-stu-id="2aea4-106">Description</span></span>|<span data-ttu-id="2aea4-107">有关视图…</span><span class="sxs-lookup"><span data-stu-id="2aea4-107">View on...</span></span>|  
|------------------|-----------------|--------------|  
|<span data-ttu-id="2aea4-108">**File Bytes Received/sec**</span><span class="sxs-lookup"><span data-stu-id="2aea4-108">**File Bytes Received/sec**</span></span>|<span data-ttu-id="2aea4-109">辅助副本在最后一秒为辅助数据库接收的 FILESTREAM 数据量。</span><span class="sxs-lookup"><span data-stu-id="2aea4-109">Amount of FILESTREAM data received by the secondary replica for the secondary database in the last second.</span></span>|<span data-ttu-id="2aea4-110">辅助副本</span><span class="sxs-lookup"><span data-stu-id="2aea4-110">Secondary replica</span></span>|  
|<span data-ttu-id="2aea4-111">**Log Bytes Received/sec**</span><span class="sxs-lookup"><span data-stu-id="2aea4-111">**Log Bytes Received/sec**</span></span>|<span data-ttu-id="2aea4-112">辅助副本在最后一秒为数据库接收的日志记录量。</span><span class="sxs-lookup"><span data-stu-id="2aea4-112">Amount of log records received by the secondary replica for the database in the last second.</span></span>|<span data-ttu-id="2aea4-113">辅助副本</span><span class="sxs-lookup"><span data-stu-id="2aea4-113">Secondary replica</span></span>|  
|<span data-ttu-id="2aea4-114">**Log remaining for undo**</span><span class="sxs-lookup"><span data-stu-id="2aea4-114">**Log remaining for undo**</span></span>|<span data-ttu-id="2aea4-115">为完成撤消阶段尚剩余的日志量 (KB)。</span><span class="sxs-lookup"><span data-stu-id="2aea4-115">The amount of log in kilobytes remaining to complete the undo phase.</span></span>|<span data-ttu-id="2aea4-116">辅助副本</span><span class="sxs-lookup"><span data-stu-id="2aea4-116">Secondary replica</span></span>|  
|<span data-ttu-id="2aea4-117">**Log Send Queue**</span><span class="sxs-lookup"><span data-stu-id="2aea4-117">**Log Send Queue**</span></span>|<span data-ttu-id="2aea4-118">主数据库的日志文件中尚未发送到辅助副本的日志记录量 (KB)。</span><span class="sxs-lookup"><span data-stu-id="2aea4-118">Amount of log records in the log files of the primary database, in kilobytes, that has not yet been sent to the secondary replica.</span></span> <span data-ttu-id="2aea4-119">此值从主副本发送到辅助副本。</span><span class="sxs-lookup"><span data-stu-id="2aea4-119">This value is sent to the secondary replica from the primary replica.</span></span> <span data-ttu-id="2aea4-120">队列大小不包括发送到辅助副本的 FILESTREAM 文件。</span><span class="sxs-lookup"><span data-stu-id="2aea4-120">Queue size does not include FILESTREAM files that are sent to a secondary.</span></span>|<span data-ttu-id="2aea4-121">辅助副本</span><span class="sxs-lookup"><span data-stu-id="2aea4-121">Secondary replica</span></span>|  
|<span data-ttu-id="2aea4-122">**Mirrored Write Transaction/sec**</span><span class="sxs-lookup"><span data-stu-id="2aea4-122">**Mirrored Write Transaction/sec**</span></span>|<span data-ttu-id="2aea4-123">在最后一秒钟内写入主数据库，然后等待提交直到将日志发送到辅助数据库的事务数。</span><span class="sxs-lookup"><span data-stu-id="2aea4-123">Number of transactions that were written to the primary database and then waited to commit until the log was sent to the secondary database, in the last second.</span></span>|<span data-ttu-id="2aea4-124">主副本</span><span class="sxs-lookup"><span data-stu-id="2aea4-124">Primary replica</span></span>|  
|<span data-ttu-id="2aea4-125">**恢复队列**</span><span class="sxs-lookup"><span data-stu-id="2aea4-125">**Recovery Queue**</span></span>|<span data-ttu-id="2aea4-126">辅助副本的日志文件中尚未重做的日志记录量。</span><span class="sxs-lookup"><span data-stu-id="2aea4-126">Amount of log records in the log files of the secondary replica that has not yet been redone.</span></span>|<span data-ttu-id="2aea4-127">辅助副本</span><span class="sxs-lookup"><span data-stu-id="2aea4-127">Secondary replica</span></span>|  
|<span data-ttu-id="2aea4-128">**Redo blocked/sec**</span><span class="sxs-lookup"><span data-stu-id="2aea4-128">**Redo blocked/sec**</span></span>|<span data-ttu-id="2aea4-129">被数据库读取器持有的锁阻塞的重做线程数。</span><span class="sxs-lookup"><span data-stu-id="2aea4-129">Number of times the redo thread is blocked on locks held by readers of the database.</span></span>|<span data-ttu-id="2aea4-130">辅助副本</span><span class="sxs-lookup"><span data-stu-id="2aea4-130">Secondary replica</span></span>|  
|<span data-ttu-id="2aea4-131">**Redo Bytes Remaining**</span><span class="sxs-lookup"><span data-stu-id="2aea4-131">**Redo Bytes Remaining**</span></span>|<span data-ttu-id="2aea4-132">为完成恢复阶段而要重做的剩余的日志量 (KB)。</span><span class="sxs-lookup"><span data-stu-id="2aea4-132">The amount of log in kilobytes remaining to be redone to finish the reverting phase.</span></span>|<span data-ttu-id="2aea4-133">辅助副本</span><span class="sxs-lookup"><span data-stu-id="2aea4-133">Secondary replica</span></span>|  
|<span data-ttu-id="2aea4-134">**Redone Bytes/sec**</span><span class="sxs-lookup"><span data-stu-id="2aea4-134">**Redone Bytes/sec**</span></span>|<span data-ttu-id="2aea4-135">在最后一秒在辅助数据库上重做的日志记录量。</span><span class="sxs-lookup"><span data-stu-id="2aea4-135">Amount of log records redone on the secondary database in the last second.</span></span>|<span data-ttu-id="2aea4-136">辅助副本</span><span class="sxs-lookup"><span data-stu-id="2aea4-136">Secondary replica</span></span>|  
|<span data-ttu-id="2aea4-137">**Total Log requiring undo**</span><span class="sxs-lookup"><span data-stu-id="2aea4-137">**Total Log requiring undo**</span></span>|<span data-ttu-id="2aea4-138">必须撤消的日志总字节数 (KB)。</span><span class="sxs-lookup"><span data-stu-id="2aea4-138">Total kilobytes of log that must be undone.</span></span>|<span data-ttu-id="2aea4-139">辅助副本</span><span class="sxs-lookup"><span data-stu-id="2aea4-139">Secondary replica</span></span>|  
|<span data-ttu-id="2aea4-140">**Transaction Delay**</span><span class="sxs-lookup"><span data-stu-id="2aea4-140">**Transaction Delay**</span></span>|<span data-ttu-id="2aea4-141">等待未终止的提交确认的延迟时间（毫秒）。</span><span class="sxs-lookup"><span data-stu-id="2aea4-141">Delay in waiting for unterminated commit acknowledgement, in milliseconds.</span></span>|<span data-ttu-id="2aea4-142">主副本</span><span class="sxs-lookup"><span data-stu-id="2aea4-142">Primary replica</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2aea4-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2aea4-143">See Also</span></span>  
 <span data-ttu-id="2aea4-144">[监视资源使用情况（系统监视器）](monitor-resource-usage-system-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="2aea4-144">[Monitor Resource Usage &#40;System Monitor&#41;](monitor-resource-usage-system-monitor.md) </span></span>  
 <span data-ttu-id="2aea4-145">[SQL Server，可用性副本](sql-server-availability-replica.md) </span><span class="sxs-lookup"><span data-stu-id="2aea4-145">[SQL Server, Availability Replica](sql-server-availability-replica.md) </span></span>  
 <span data-ttu-id="2aea4-146">[SQL Server，Databases 对象](sql-server-databases-object.md) </span><span class="sxs-lookup"><span data-stu-id="2aea4-146">[SQL Server, Databases Object](sql-server-databases-object.md) </span></span>  
 [<span data-ttu-id="2aea4-147">AlwaysOn 可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="2aea4-147">AlwaysOn Availability Groups (SQL Server)</span></span>](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)  
  
  
