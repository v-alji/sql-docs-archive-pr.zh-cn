---
title: 重播要求 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- event classes [SQL Server], replaying traces
- traces [SQL Server], replaying
- replaying traces
- TSQL_Replay template [SQL Server]
ms.assetid: 0e01dfc7-84b9-47f6-8bf7-b0656df4fa7d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 65546f6820765286b558d2043e0155a79a07eb58
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692025"
---
# <a name="replay-requirements"></a><span data-ttu-id="da7f5-102">Replay Requirements</span><span class="sxs-lookup"><span data-stu-id="da7f5-102">Replay Requirements</span></span>
  <span data-ttu-id="da7f5-103">若要使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 或分布式重播实用工具重播跟踪数据，则必须在跟踪中捕获一组特定的事件类和列。</span><span class="sxs-lookup"><span data-stu-id="da7f5-103">In order to replay trace data with [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] or the Distributed Replay Utility, a specific set of event classes and columns must be captured in the trace.</span></span> <span data-ttu-id="da7f5-104">如果使用 **TSQL_Replay** 跟踪模板配置稍后用于重播的跟踪，则会默认启用这些设置。</span><span class="sxs-lookup"><span data-stu-id="da7f5-104">These settings are enabled by default if the **TSQL_Replay** trace template is used to configure a trace that is later used for replay.</span></span> <span data-ttu-id="da7f5-105">本主题介绍这些设置以及其他重播要求。</span><span class="sxs-lookup"><span data-stu-id="da7f5-105">This topic describes these settings and other replay requirements.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="da7f5-106">建议使用分布式重播实用工具重播密集型 OLTP 应用程序（具有大量活动并发连接或高吞吐量）。</span><span class="sxs-lookup"><span data-stu-id="da7f5-106">We recommend using the Distributed Replay Utility for replaying an intensive OLTP application (with many active concurrent connections or high throughput).</span></span> <span data-ttu-id="da7f5-107">分布式重播实用工具可以从多台计算机重播跟踪数据，并更好地模拟任务关键型工作负荷。</span><span class="sxs-lookup"><span data-stu-id="da7f5-107">The Distributed Replay Utility can replay trace data from multiple computers, better simulating a mission-critical workload.</span></span> <span data-ttu-id="da7f5-108">有关详细信息，请参阅 [SQL Server Distributed Replay](../distributed-replay/sql-server-distributed-replay.md)。</span><span class="sxs-lookup"><span data-stu-id="da7f5-108">For more information, see [SQL Server Distributed Replay](../distributed-replay/sql-server-distributed-replay.md).</span></span>  
  
## <a name="event-classes-required-for-replay"></a><span data-ttu-id="da7f5-109">重播所需的事件类</span><span class="sxs-lookup"><span data-stu-id="da7f5-109">Event Classes Required for Replay</span></span>  
 <span data-ttu-id="da7f5-110">若要通过 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]进行重播，除了要监视的任何其他事件类之外，还必须在跟踪中捕获以下一组事件类：</span><span class="sxs-lookup"><span data-stu-id="da7f5-110">To be replayed by [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], the following set of event classes, in addition to any other event classes you want to monitor, must be captured in the trace:</span></span>  
  
-   <span data-ttu-id="da7f5-111">**CursorClose**（仅在重播服务器端游标时需要）</span><span class="sxs-lookup"><span data-stu-id="da7f5-111">**CursorClose (** only required when replaying server-side cursors)</span></span>  
  
-   <span data-ttu-id="da7f5-112">**CursorExecute** （仅在重播服务器端游标时需要）</span><span class="sxs-lookup"><span data-stu-id="da7f5-112">**CursorExecute** (only required when replaying server-side cursors)</span></span>  
  
-   <span data-ttu-id="da7f5-113">**CursorOpen** （仅在重播服务器端游标时需要）</span><span class="sxs-lookup"><span data-stu-id="da7f5-113">**CursorOpen** (only required when replaying server-side cursors)</span></span>  
  
-   <span data-ttu-id="da7f5-114">**CursorPrepare** （仅在重播服务器端游标时需要）</span><span class="sxs-lookup"><span data-stu-id="da7f5-114">**CursorPrepare** (only required when replaying server-side cursors)</span></span>  
  
-   <span data-ttu-id="da7f5-115">**CursorUnprepare** （仅在重播服务器端游标时需要）</span><span class="sxs-lookup"><span data-stu-id="da7f5-115">**CursorUnprepare** (only required when replaying server-side cursors)</span></span>  
  
-   <span data-ttu-id="da7f5-116">**审核登录**</span><span class="sxs-lookup"><span data-stu-id="da7f5-116">**Audit Login**</span></span>  
  
-   <span data-ttu-id="da7f5-117">**审核注销**</span><span class="sxs-lookup"><span data-stu-id="da7f5-117">**Audit Logout**</span></span>  
  
-   <span data-ttu-id="da7f5-118">**ExistingConnection**</span><span class="sxs-lookup"><span data-stu-id="da7f5-118">**ExistingConnection**</span></span>  
  
-   <span data-ttu-id="da7f5-119">**RPC Output Parameter**</span><span class="sxs-lookup"><span data-stu-id="da7f5-119">**RPC Output Parameter**</span></span>  
  
-   <span data-ttu-id="da7f5-120">**RPC:Completed**</span><span class="sxs-lookup"><span data-stu-id="da7f5-120">**RPC:Completed**</span></span>  
  
-   <span data-ttu-id="da7f5-121">**RPC:Starting**</span><span class="sxs-lookup"><span data-stu-id="da7f5-121">**RPC:Starting**</span></span>  
  
-   <span data-ttu-id="da7f5-122">**Exec Prepared SQL** （仅在重播服务器端准备的 SQL 语句时需要）</span><span class="sxs-lookup"><span data-stu-id="da7f5-122">**Exec Prepared SQL** (only required when replaying server-side prepared SQL statements)</span></span>  
  
-   <span data-ttu-id="da7f5-123">**Prepare SQL** （仅在重播服务器端准备的 SQL 语句时需要）</span><span class="sxs-lookup"><span data-stu-id="da7f5-123">**Prepare SQL** (only required when replaying server-side prepared SQL statements)</span></span>  
  
-   <span data-ttu-id="da7f5-124">**SQL:BatchCompleted**</span><span class="sxs-lookup"><span data-stu-id="da7f5-124">**SQL:BatchCompleted**</span></span>  
  
-   <span data-ttu-id="da7f5-125">**SQL:BatchStarting**</span><span class="sxs-lookup"><span data-stu-id="da7f5-125">**SQL:BatchStarting**</span></span>  
  
## <a name="data-columns-required-for-replay"></a><span data-ttu-id="da7f5-126">重播所需的数据列</span><span class="sxs-lookup"><span data-stu-id="da7f5-126">Data Columns Required for Replay</span></span>  
 <span data-ttu-id="da7f5-127">除任何其他要捕获的数据列外，还必须在跟踪内捕获下列数据列才能重播跟踪：</span><span class="sxs-lookup"><span data-stu-id="da7f5-127">In addition to any other data columns you want to capture, the following data columns must be captured in a trace to allow the trace to be replayed:</span></span>  
  
-   <span data-ttu-id="da7f5-128">**Event Class**</span><span class="sxs-lookup"><span data-stu-id="da7f5-128">**Event Class**</span></span>  
  
-   <span data-ttu-id="da7f5-129">**EventSequence**</span><span class="sxs-lookup"><span data-stu-id="da7f5-129">**EventSequence**</span></span>  
  
-   <span data-ttu-id="da7f5-130">**TextData**</span><span class="sxs-lookup"><span data-stu-id="da7f5-130">**TextData**</span></span>  
  
-   <span data-ttu-id="da7f5-131">**应用程序名称**</span><span class="sxs-lookup"><span data-stu-id="da7f5-131">**Application Name**</span></span>  
  
-   <span data-ttu-id="da7f5-132">**LoginName**</span><span class="sxs-lookup"><span data-stu-id="da7f5-132">**LoginName**</span></span>  
  
-   <span data-ttu-id="da7f5-133">**DatabaseName**</span><span class="sxs-lookup"><span data-stu-id="da7f5-133">**DatabaseName**</span></span>  
  
-   <span data-ttu-id="da7f5-134">**数据库 ID**</span><span class="sxs-lookup"><span data-stu-id="da7f5-134">**Database ID**</span></span>  
  
-   <span data-ttu-id="da7f5-135">**ClientProcessID**</span><span class="sxs-lookup"><span data-stu-id="da7f5-135">**ClientProcessID**</span></span>  
  
-   <span data-ttu-id="da7f5-136">**HostName**</span><span class="sxs-lookup"><span data-stu-id="da7f5-136">**HostName**</span></span>  
  
-   <span data-ttu-id="da7f5-137">**ServerName**</span><span class="sxs-lookup"><span data-stu-id="da7f5-137">**ServerName**</span></span>  
  
-   <span data-ttu-id="da7f5-138">**Binary Data**</span><span class="sxs-lookup"><span data-stu-id="da7f5-138">**Binary Data**</span></span>  
  
-   <span data-ttu-id="da7f5-139">**SPID**</span><span class="sxs-lookup"><span data-stu-id="da7f5-139">**SPID**</span></span>  
  
-   <span data-ttu-id="da7f5-140">**Start Time**</span><span class="sxs-lookup"><span data-stu-id="da7f5-140">**Start Time**</span></span>  
  
-   <span data-ttu-id="da7f5-141">**EndTime**</span><span class="sxs-lookup"><span data-stu-id="da7f5-141">**EndTime**</span></span>  
  
-   <span data-ttu-id="da7f5-142">**IsSystem**</span><span class="sxs-lookup"><span data-stu-id="da7f5-142">**IsSystem**</span></span>  
  
-   <span data-ttu-id="da7f5-143">**NTDomainName**</span><span class="sxs-lookup"><span data-stu-id="da7f5-143">**NTDomainName**</span></span>  
  
-   <span data-ttu-id="da7f5-144">**NTUserName**</span><span class="sxs-lookup"><span data-stu-id="da7f5-144">**NTUserName**</span></span>  
  
-   <span data-ttu-id="da7f5-145">**错误**</span><span class="sxs-lookup"><span data-stu-id="da7f5-145">**Error**</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="da7f5-146">将跟踪模板 **TSQL_Replay** 用于捕获重播数据的跟踪。</span><span class="sxs-lookup"><span data-stu-id="da7f5-146">Use the trace template **TSQL_Replay** for traces that capture data for replay.</span></span>  
  
## <a name="other-replay-requirements"></a><span data-ttu-id="da7f5-147">其他重播要求</span><span class="sxs-lookup"><span data-stu-id="da7f5-147">Other Replay Requirements</span></span>  
 <span data-ttu-id="da7f5-148">在 Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中，重播将检查是否存在所需的事件和列。</span><span class="sxs-lookup"><span data-stu-id="da7f5-148">In Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], replay checks for the presence of required events and columns.</span></span> <span data-ttu-id="da7f5-149">此更改有助于改进重播的准确性，从而在缺少所需数据的情况下对重播进行故障排除时无需进行任何猜测。</span><span class="sxs-lookup"><span data-stu-id="da7f5-149">This change helps improve the accuracy of replay and takes the guesswork out of troubleshooting replay when required data is missing.</span></span> <span data-ttu-id="da7f5-150">当跟踪中缺少所需的数据时，重播将会返回一个错误，并停止重播文件。</span><span class="sxs-lookup"><span data-stu-id="da7f5-150">Replay returns an error and stops replaying a file when required data is missing from a trace.</span></span>  
  
 <span data-ttu-id="da7f5-151">若要重播对运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的服务器（目标）而非最初跟踪的服务器（源）的跟踪，请确保已执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="da7f5-151">To replay a trace against a server (the target) on which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running other than the server originally traced (the source), make sure the following has been done:</span></span>  
  
-   <span data-ttu-id="da7f5-152">必须在目标上而且是在与源相同的数据库中创建跟踪包含的所有登录名和用户。</span><span class="sxs-lookup"><span data-stu-id="da7f5-152">All logins and users contained in the trace must be created already on the target and in the same database as the source.</span></span>  
  
-   <span data-ttu-id="da7f5-153">目标中的所有登录名和用户具有的权限必须与源中的相同。</span><span class="sxs-lookup"><span data-stu-id="da7f5-153">All logins and users in the target must have the same permissions they had in the source.</span></span>  
  
-   <span data-ttu-id="da7f5-154">所有登录密码必须是执行重播的用户的密码。</span><span class="sxs-lookup"><span data-stu-id="da7f5-154">All login passwords must be the same as those of the user that executes the replay.</span></span>  
  
-   <span data-ttu-id="da7f5-155">目标上的数据库 ID 最好与源上的数据库 ID 相同。</span><span class="sxs-lookup"><span data-stu-id="da7f5-155">The database IDs on the target ideally should be the same as those on the source.</span></span> <span data-ttu-id="da7f5-156">但是，如果它们不相同，当跟踪中出现 **DatabaseName** 时，将根据它进行匹配。</span><span class="sxs-lookup"><span data-stu-id="da7f5-156">However, if they are not the same, matching can be performed based on **DatabaseName** if it is present in the trace.</span></span>  
  
-   <span data-ttu-id="da7f5-157">必须将跟踪内包含的每个登录名的默认数据库在目标上设置成登录名各自的目标数据库。</span><span class="sxs-lookup"><span data-stu-id="da7f5-157">The default database for each login contained in the trace must be set (on the target) to the respective target database of the login.</span></span> <span data-ttu-id="da7f5-158">例如，在源上，要重播的跟踪包含数据库 **Fred_Db**内登录名 **Fred** 的活动。</span><span class="sxs-lookup"><span data-stu-id="da7f5-158">For example, the trace to be replayed contains activity for the login, **Fred**, in the database **Fred_Db** on the source.</span></span> <span data-ttu-id="da7f5-159">因此在目标上，必须将登录名 **Fred**的默认数据库设置成与 **Fred_Db** 相匹配的数据库（即使数据库名称不同）。</span><span class="sxs-lookup"><span data-stu-id="da7f5-159">Therefore, on the target, the default database for the login, **Fred**, must be set to the database that matches **Fred_Db** (even if the database name is different).</span></span> <span data-ttu-id="da7f5-160">若要设置登录名的默认数据库，请使用 **sp_defaultdb** 系统存储过程。</span><span class="sxs-lookup"><span data-stu-id="da7f5-160">To set the default database of the login, use the **sp_defaultdb** system stored procedure.</span></span>  
  
 <span data-ttu-id="da7f5-161">重播与不存在的或不正确的登录名相关的事件会导致重播错误，但重播操作会继续。</span><span class="sxs-lookup"><span data-stu-id="da7f5-161">Replaying events associated with missing or incorrect logins results in replay errors, but the replay operation continues.</span></span>  
  
 <span data-ttu-id="da7f5-162">有关重播跟踪需要哪些权限的信息，请参阅 [Permissions Required to Run SQL Server Profiler](sql-server-profiler.md)。</span><span class="sxs-lookup"><span data-stu-id="da7f5-162">For information about what permissions are required to replay a trace, see [Permissions Required to Run SQL Server Profiler](sql-server-profiler.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da7f5-163">另请参阅</span><span class="sxs-lookup"><span data-stu-id="da7f5-163">See Also</span></span>  
 <span data-ttu-id="da7f5-164">[重播跟踪表 (SQL Server Profiler)](replay-a-trace-table-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="da7f5-164">[Replay a Trace Table &#40;SQL Server Profiler&#41;](replay-a-trace-table-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="da7f5-165">[重播跟踪文件 (SQL Server Profiler)](replay-a-trace-file-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="da7f5-165">[Replay a Trace File &#40;SQL Server Profiler&#41;](replay-a-trace-file-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="da7f5-166">[SQL Server 事件类参考](../../relational-databases/event-classes/sql-server-event-class-reference.md) </span><span class="sxs-lookup"><span data-stu-id="da7f5-166">[SQL Server Event Class Reference](../../relational-databases/event-classes/sql-server-event-class-reference.md) </span></span>  
 <span data-ttu-id="da7f5-167">[sp_defaultdb (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-defaultdb-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="da7f5-167">[sp_defaultdb &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-defaultdb-transact-sql) </span></span>  
 [<span data-ttu-id="da7f5-168">SQL Server 分布式重播</span><span class="sxs-lookup"><span data-stu-id="da7f5-168">SQL Server Distributed Replay</span></span>](../distributed-replay/sql-server-distributed-replay.md)  
  
  
