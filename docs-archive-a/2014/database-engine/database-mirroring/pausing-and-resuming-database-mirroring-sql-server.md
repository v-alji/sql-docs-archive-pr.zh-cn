---
title: 暂停和恢复数据库镜像 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- sessions [SQL Server], database mirroring
- resuming database mirroring
- database mirroring [SQL Server], pausing
- database mirroring [SQL Server], resuming
- pausing database mirroring
ms.assetid: c67802c6-ee8c-4cbd-a6d4-f7b80413a4ab
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8c231876b11303992e0e3300c9cb73c0cf53b3af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690130"
---
# <a name="pausing-and-resuming-database-mirroring-sql-server"></a><span data-ttu-id="c87b2-102">暂停和恢复数据库镜像 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="c87b2-102">Pausing and Resuming Database Mirroring (SQL Server)</span></span>
  <span data-ttu-id="c87b2-103">数据库所有者可以暂停并在以后随时恢复数据库镜像会话。</span><span class="sxs-lookup"><span data-stu-id="c87b2-103">The database owner can pause and later resume a database mirroring session at any time.</span></span> <span data-ttu-id="c87b2-104">执行暂停操作将保留在挂起镜像时的会话状态。</span><span class="sxs-lookup"><span data-stu-id="c87b2-104">Pausing preserves the session state while suspending mirroring.</span></span> <span data-ttu-id="c87b2-105">当出现瓶颈时，暂停可能有利于提高主体服务器的性能。</span><span class="sxs-lookup"><span data-stu-id="c87b2-105">During bottlenecks, pausing might be useful to improve performance on the principal server.</span></span>  
  
 <span data-ttu-id="c87b2-106">会话暂停后，主体数据库仍然可用。</span><span class="sxs-lookup"><span data-stu-id="c87b2-106">When a session is paused, the principal database remains available.</span></span> <span data-ttu-id="c87b2-107">暂停操作将镜像会话的状态设置为 SUSPENDED，并且镜像数据库不再与主体数据库保持一致，从而导致主体数据库公开运行。</span><span class="sxs-lookup"><span data-stu-id="c87b2-107">Pausing sets the state of the mirroring session to SUSPENDED, and the mirror database no longer keeps up with the principal database, causing the principal database to run exposed.</span></span>  
  
 <span data-ttu-id="c87b2-108">由于在数据库镜像会话处于暂停时无法截断事务日志，因此建议您尽快恢复暂停的会话。</span><span class="sxs-lookup"><span data-stu-id="c87b2-108">We recommend that you resume a paused session quickly, because as long as a database mirroring session remains paused, the transaction log cannot be truncated.</span></span> <span data-ttu-id="c87b2-109">因此，如果数据库镜像会话暂停的时间太长，事务日志将填满，导致数据库不可用。</span><span class="sxs-lookup"><span data-stu-id="c87b2-109">Therefore, if a database mirroring session is paused for too long, the transaction log fills up, making the database unavailable.</span></span> <span data-ttu-id="c87b2-110">有关此现象产生原因的解释，请参阅本主题后面的“暂停和恢复如何影响日志截断”。</span><span class="sxs-lookup"><span data-stu-id="c87b2-110">For an explanation of why this happens, see "How Pausing and Resuming Affect Log Truncation," later in this topic.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="c87b2-111">执行强制服务之后，当重新连接原始主体服务器时，镜像便会挂起。</span><span class="sxs-lookup"><span data-stu-id="c87b2-111">Following a forced service, when the original principal server reconnects mirroring is suspended.</span></span> <span data-ttu-id="c87b2-112">在这种情况下，恢复镜像可能会导致原始主体服务器上的数据丢失。</span><span class="sxs-lookup"><span data-stu-id="c87b2-112">Resuming mirroring in this situation could possibly cause data loss on the original principal server.</span></span> <span data-ttu-id="c87b2-113">有关管理潜在的数据丢失的信息，请参阅 [Database Mirroring Operating Modes](database-mirroring-operating-modes.md)。</span><span class="sxs-lookup"><span data-stu-id="c87b2-113">For information about managing the potential data loss, see [Database Mirroring Operating Modes](database-mirroring-operating-modes.md).</span></span>  
  
 <span data-ttu-id="c87b2-114">**本主题内容：**</span><span class="sxs-lookup"><span data-stu-id="c87b2-114">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="c87b2-115">暂停和恢复如何影响日志截断</span><span class="sxs-lookup"><span data-stu-id="c87b2-115">How Pausing and Resuming Affect Log Truncation</span></span>](#EffectOnLogTrunc)  
  
-   [<span data-ttu-id="c87b2-116">避免出现已满事务日志</span><span class="sxs-lookup"><span data-stu-id="c87b2-116">Avoid a Full Transaction Log</span></span>](#AvoidFullLog)  
  
-   [<span data-ttu-id="c87b2-117">相关任务</span><span class="sxs-lookup"><span data-stu-id="c87b2-117">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="how-pausing-and-resuming-affect-log-truncation"></a><a name="EffectOnLogTrunc"></a> <span data-ttu-id="c87b2-118">暂停和恢复如何影响日志截断</span><span class="sxs-lookup"><span data-stu-id="c87b2-118">How Pausing and Resuming Affect Log Truncation</span></span>  
 <span data-ttu-id="c87b2-119">通常，在数据库上执行自动检查点操作时，事务日志将在下一个日志备份后截断到该检查点。</span><span class="sxs-lookup"><span data-stu-id="c87b2-119">Normally, when an automatic checkpoint is performed on a database, its transaction log is truncated to that checkpoint after the next log backup.</span></span> <span data-ttu-id="c87b2-120">当数据库镜像会话处于暂停时，当前所有日志记录都保持为活动状态，因为主体服务器正等待将这些记录发送到镜像服务器。</span><span class="sxs-lookup"><span data-stu-id="c87b2-120">While a database mirroring session remains paused, all of the current log records remain active because the principal server is waiting to send them to the mirror server.</span></span> <span data-ttu-id="c87b2-121">未发送的日志记录将堆积在主体数据库的事务日志中，直到会话恢复并且主体服务器将它们发送到镜像服务器为止。</span><span class="sxs-lookup"><span data-stu-id="c87b2-121">The unsent log records accumulate in the transaction log of the principal database until the session resumes and the principal server has sent the log records to the mirror server.</span></span>  
  
 <span data-ttu-id="c87b2-122">会话恢复时，主体服务器立即开始将堆积的日志记录发送到镜像服务器。</span><span class="sxs-lookup"><span data-stu-id="c87b2-122">When the session is resumed, the principal server immediately begins sending the accumulated log records to the mirror server.</span></span> <span data-ttu-id="c87b2-123">当镜像服务器确认与最早的自动检查点相对应的日志记录已排队后，主体服务器便会将主体数据库的日志截断到该检查点。</span><span class="sxs-lookup"><span data-stu-id="c87b2-123">After the mirror server confirms that it has queued the log record corresponding to the oldest automatic checkpoint, the principal server truncates the log of the principal database to that checkpoint.</span></span> <span data-ttu-id="c87b2-124">镜像服务器会截断同一个日志记录的重做队列。</span><span class="sxs-lookup"><span data-stu-id="c87b2-124">The mirror server truncates the redo queue at the same log record.</span></span> <span data-ttu-id="c87b2-125">随着对每个连续的检查点重复此过程，日志将对检查点逐个分阶段地截断。</span><span class="sxs-lookup"><span data-stu-id="c87b2-125">As this process is repeated for each successive checkpoint, the log is truncated in stages, checkpoint by checkpoint.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c87b2-126">有关检查点和日志截断的详细信息，请参阅[数据库检查点 (SQL Server)](../../relational-databases/logs/database-checkpoints-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="c87b2-126">For more information about the checkpoints and log truncation, see [Database Checkpoints &#40;SQL Server&#41;](../../relational-databases/logs/database-checkpoints-sql-server.md).</span></span>  
  
##  <a name="avoid-a-full-transaction-log"></a><a name="AvoidFullLog"></a> <span data-ttu-id="c87b2-127">避免出现已满事务日志</span><span class="sxs-lookup"><span data-stu-id="c87b2-127">Avoid a Full Transaction Log</span></span>  
 <span data-ttu-id="c87b2-128">如果填满该日志（因为它达到其最大大小或服务器实例耗尽空间），则数据库将无法再执行任何更新。</span><span class="sxs-lookup"><span data-stu-id="c87b2-128">If the log fills up (either because it reaches its maximum size or the server instance runs out of space), the database cannot perform any more updates.</span></span> <span data-ttu-id="c87b2-129">若要避免出现这种问题，有两种选择：</span><span class="sxs-lookup"><span data-stu-id="c87b2-129">To avoid this problem, you have two alternatives:</span></span>  
  
-   <span data-ttu-id="c87b2-130">在该日志填满之前恢复数据库镜像会话，或添加更多的日志空间。</span><span class="sxs-lookup"><span data-stu-id="c87b2-130">Resume the database mirroring session before the log fills up, or add more log space.</span></span> <span data-ttu-id="c87b2-131">恢复数据库镜像会使主体服务器将其累积的活动日志发送到镜像服务器，并将镜像数据库设置为 SYNCHRONIZING 状态。</span><span class="sxs-lookup"><span data-stu-id="c87b2-131">Resuming database mirroring lets the principal server send its accumulated active log to the mirror server and puts the mirror database in the SYNCHRONIZING state.</span></span> <span data-ttu-id="c87b2-132">然后镜像服务器可将日志镜像到磁盘并开始重做。</span><span class="sxs-lookup"><span data-stu-id="c87b2-132">The mirror server can then harden the log to disk and start to redo it.</span></span>  
  
-   <span data-ttu-id="c87b2-133">通过删除镜像来停止数据库镜像会话。</span><span class="sxs-lookup"><span data-stu-id="c87b2-133">Stop the database mirroring session by removing mirroring.</span></span>  
  
     <span data-ttu-id="c87b2-134">和暂停会话不同，删除镜像将删除有关镜像会话的所有信息。</span><span class="sxs-lookup"><span data-stu-id="c87b2-134">Unlike pausing a session, removing mirroring drops all information about the mirroring session.</span></span> <span data-ttu-id="c87b2-135">每个伙伴服务器实例将保留其自己的数据库副本。</span><span class="sxs-lookup"><span data-stu-id="c87b2-135">Each partner server instance retains its own copy of the database.</span></span> <span data-ttu-id="c87b2-136">如果前一个镜像副本已恢复，则它将与前一个主体副本分离，且滞后时间等于此会话暂停的时间。</span><span class="sxs-lookup"><span data-stu-id="c87b2-136">If the former mirror copy is recovered, it will have diverged from the former principal copy and be behind by the amount of time that has elapsed since the session was paused.</span></span> <span data-ttu-id="c87b2-137">有关详细信息，请参阅 [删除数据库镜像 (SQL Server)](database-mirroring-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="c87b2-137">For more information, see [Removing Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="c87b2-138">相关任务</span><span class="sxs-lookup"><span data-stu-id="c87b2-138">Related Tasks</span></span>  
 <span data-ttu-id="c87b2-139">**暂停或恢复数据库镜像**</span><span class="sxs-lookup"><span data-stu-id="c87b2-139">**To pause or resume database mirroring**</span></span>  
  
-   [<span data-ttu-id="c87b2-140">暂停或恢复数据库镜像会话 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="c87b2-140">Pause or Resume a Database Mirroring Session &#40;SQL Server&#41;</span></span>](pause-or-resume-a-database-mirroring-session-sql-server.md)  
  
 <span data-ttu-id="c87b2-141">**停止数据库镜像**</span><span class="sxs-lookup"><span data-stu-id="c87b2-141">**To stop database mirroring**</span></span>  
  
-   [<span data-ttu-id="c87b2-142">删除数据库镜像 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="c87b2-142">Remove Database Mirroring &#40;SQL Server&#41;</span></span>](remove-database-mirroring-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="c87b2-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c87b2-143">See Also</span></span>  
 <span data-ttu-id="c87b2-144">[ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c87b2-144">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="c87b2-145">[数据库镜像 (SQL Server)](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="c87b2-145">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="c87b2-146">删除数据库镜像 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="c87b2-146">Removing Database Mirroring &#40;SQL Server&#41;</span></span>](database-mirroring-sql-server.md)  
  
  
