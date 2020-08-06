---
title: 可用性组和数据库镜像的自动页修复 () |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- automatic page repair
- Availability Groups [SQL Server], automatic page repair
- database mirroring [SQL Server], automatic page repair
- suspect pages [SQL Server]
ms.assetid: cf2e3650-5fac-4f34-b50e-d17765578a8e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 09b5a5069d019dc452a49179e1c83d78a50e0566
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586299"
---
# <a name="automatic-page-repair-for-availability-groups-and-database-mirroring"></a><span data-ttu-id="e8ef2-102">自动页修复 （针对可用性组和数据库镜像）</span><span class="sxs-lookup"><span data-stu-id="e8ef2-102">Automatic Page Repair (For Availability Groups and Database Mirroring)</span></span>
  <span data-ttu-id="e8ef2-103">数据库镜像和 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]支持自动页修复。</span><span class="sxs-lookup"><span data-stu-id="e8ef2-103">Automatic page repair is supported by database mirroring and by [!INCLUDE[ssHADR](../../includes/sshadr-md.md)].</span></span> <span data-ttu-id="e8ef2-104">在某些类型的错误导致页损坏，使其无法读取后，数据库镜像伙伴（主体或镜像）或可用性副本（主副本或辅助副本）将尝试自动修复该页。</span><span class="sxs-lookup"><span data-stu-id="e8ef2-104">After certain types of errors corrupt a page, making it unreadable, a database mirroring partner (principal or mirror) or an availability replica (primary or secondary) attempts to automatically recover the page.</span></span> <span data-ttu-id="e8ef2-105">无法读取该页的伙伴/副本将从其伙伴或从其他副本请求该页的新副本。</span><span class="sxs-lookup"><span data-stu-id="e8ef2-105">The partner/replica that cannot read the page requests a fresh copy of the page from its partner or from another replica.</span></span> <span data-ttu-id="e8ef2-106">如果此请求成功，则将以可读副本替换不可读的页，并且这通常会解决该错误。</span><span class="sxs-lookup"><span data-stu-id="e8ef2-106">If this request succeeds, the unreadable page is replaced by the readable copy, and this usually resolves the error.</span></span>  
  
 <span data-ttu-id="e8ef2-107">一般来说，数据库镜像和 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] 以等效方式处理 I/O 错误。</span><span class="sxs-lookup"><span data-stu-id="e8ef2-107">Generally speaking, database mirroring and [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] handle I/O errors in equivalent ways.</span></span> <span data-ttu-id="e8ef2-108">下面将具体介绍几个差异。</span><span class="sxs-lookup"><span data-stu-id="e8ef2-108">The few differences are explicitly called out here.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e8ef2-109">自动页修复有别于 DBCC 修复。</span><span class="sxs-lookup"><span data-stu-id="e8ef2-109">Automatic page repair differs from DBCC repair.</span></span> <span data-ttu-id="e8ef2-110">自动页修复会保留所有数据。</span><span class="sxs-lookup"><span data-stu-id="e8ef2-110">All of the data is preserved by an automatic page repair.</span></span> <span data-ttu-id="e8ef2-111">相反，使用 DBCC REPAIR_ALLOW_DATA_LOSS 选项更正错误可能需要删除某些页（从而会删除数据）。</span><span class="sxs-lookup"><span data-stu-id="e8ef2-111">In contrast, correcting errors by using the DBCC REPAIR_ALLOW_DATA_LOSS option might require that some pages, and therefore data, be deleted.</span></span>  
  
  
  
##  <a name="error-types-that-cause-an-automatic-page-repair-attempt"></a><a name="ErrorTypes"></a><span data-ttu-id="e8ef2-112">导致自动页修复尝试的错误类型</span><span class="sxs-lookup"><span data-stu-id="e8ef2-112">Error Types That Cause an Automatic Page-Repair Attempt</span></span>  
 <span data-ttu-id="e8ef2-113">数据库镜像自动页修复只尝试修复特定数据文件中的页，此数据文件是指对其执行的操作由于下表中列出的某一错误而失败的数据文件。</span><span class="sxs-lookup"><span data-stu-id="e8ef2-113">Database mirroring automatic page repair tries to repair only pages in a data file on which an operation has failed for one of the errors listed in the following table.</span></span>  
  
|<span data-ttu-id="e8ef2-114">错误号</span><span class="sxs-lookup"><span data-stu-id="e8ef2-114">Error number</span></span>|<span data-ttu-id="e8ef2-115">说明</span><span class="sxs-lookup"><span data-stu-id="e8ef2-115">Description</span></span>|<span data-ttu-id="e8ef2-116">导致自动页修复尝试的实例</span><span class="sxs-lookup"><span data-stu-id="e8ef2-116">Instances that cause automatic page-repair attempt</span></span>|  
|------------------|-----------------|---------------------------------------------------------|  
|[<span data-ttu-id="e8ef2-117">823</span><span class="sxs-lookup"><span data-stu-id="e8ef2-117">823</span></span>](../../relational-databases/errors-events/mssqlserver-823-database-engine-error.md)|<span data-ttu-id="e8ef2-118">仅当操作系统对数据执行循环冗余检查 (CRC) 失败时才执行此操作。</span><span class="sxs-lookup"><span data-stu-id="e8ef2-118">Action is taken only if the operating system performed a cyclic redundancy check (CRC) that failed on the data.</span></span>|<span data-ttu-id="e8ef2-119">ERROR_CRC。</span><span class="sxs-lookup"><span data-stu-id="e8ef2-119">ERROR_CRC.</span></span> <span data-ttu-id="e8ef2-120">此错误的操作系统值为 23。</span><span class="sxs-lookup"><span data-stu-id="e8ef2-120">The operating-system value for this error is 23.</span></span>|  
|[<span data-ttu-id="e8ef2-121">824</span><span class="sxs-lookup"><span data-stu-id="e8ef2-121">824</span></span>](../../relational-databases/errors-events/mssqlserver-824-database-engine-error.md)|<span data-ttu-id="e8ef2-122">逻辑错误。</span><span class="sxs-lookup"><span data-stu-id="e8ef2-122">Logical errors.</span></span>|<span data-ttu-id="e8ef2-123">逻辑数据错误，例如残缺写或错误的页校验和。</span><span class="sxs-lookup"><span data-stu-id="e8ef2-123">Logical data errors, such as torn write or bad page checksum.</span></span>|  
|<span data-ttu-id="e8ef2-124">829</span><span class="sxs-lookup"><span data-stu-id="e8ef2-124">829</span></span>|<span data-ttu-id="e8ef2-125">页已标记为还原已挂起。</span><span class="sxs-lookup"><span data-stu-id="e8ef2-125">A page has been marked as restore pending.</span></span>|<span data-ttu-id="e8ef2-126">全部。</span><span class="sxs-lookup"><span data-stu-id="e8ef2-126">All.</span></span>|  
  
 <span data-ttu-id="e8ef2-127">若要查看最近的 823 CRC 错误和 824 错误，请参阅 [msdb](/sql/relational-databases/system-tables/suspect-pages-transact-sql) 数据库中的 [suspect_pages](../../relational-databases/databases/msdb-database.md) 表。</span><span class="sxs-lookup"><span data-stu-id="e8ef2-127">To view recent 823 CRC errors and 824 errors, see the [suspect_pages](/sql/relational-databases/system-tables/suspect-pages-transact-sql) table in the [msdb](../../relational-databases/databases/msdb-database.md) database.</span></span>  
  
  
  
##  <a name="page-types-that-cannot-be-automatically-repaired"></a><a name="UnrepairablePageTypes"></a><span data-ttu-id="e8ef2-128">无法自动修复的页类型</span><span class="sxs-lookup"><span data-stu-id="e8ef2-128">Page Types That Cannot Be Automatically Repaired</span></span>  
 <span data-ttu-id="e8ef2-129">页自动修复不能修复以下控制页类型：</span><span class="sxs-lookup"><span data-stu-id="e8ef2-129">Automatic page repair cannot repair the following control page types:</span></span>  
  
-   <span data-ttu-id="e8ef2-130">文件头页（页 ID 0）。</span><span class="sxs-lookup"><span data-stu-id="e8ef2-130">File header page (page ID 0).</span></span>  
  
-   <span data-ttu-id="e8ef2-131">页 9（数据库引导页）。</span><span class="sxs-lookup"><span data-stu-id="e8ef2-131">Page 9 (the database boot page).</span></span>  
  
-   <span data-ttu-id="e8ef2-132">分配页：全局分配映射 (GAM) 页、共享全局分配映射 (SGAM) 页和页可用空间 (PFS) 页。</span><span class="sxs-lookup"><span data-stu-id="e8ef2-132">Allocation pages: Global Allocation Map (GAM) pages, Shared Global Allocation Map (SGAM) pages, and Page Free Space (PFS) pages.</span></span>  
  

  
##  <a name="handling-io-errors-on-the-principalprimary-database"></a><a name="PrimaryIOErrors"></a><span data-ttu-id="e8ef2-133">处理主体/主数据库上的 i/o 错误</span><span class="sxs-lookup"><span data-stu-id="e8ef2-133">Handling I/O Errors on the Principal/Primary Database</span></span>  
 <span data-ttu-id="e8ef2-134">在主体/主数据库中，仅当数据库处于 SYNCHRONIZED 状态且主体/主数据库仍向镜像/辅助数据库发送数据库日志记录时，才会尝试自动页修复。</span><span class="sxs-lookup"><span data-stu-id="e8ef2-134">On the principal/primary database, automatic page repair is tried only when the database is in the SYNCHRONIZED state and the principal/primary is still sending log records for the database to the mirror/secondary.</span></span> <span data-ttu-id="e8ef2-135">自动页修复尝试中操作的基本顺序如下：</span><span class="sxs-lookup"><span data-stu-id="e8ef2-135">The basic sequence of actions in an automatic page-repair attempt are as follows:</span></span>  
  
1.  <span data-ttu-id="e8ef2-136">当主体/主数据库中的数据页上发生读取错误时，主体/主数据库将使用相应的错误状态在 [suspect_pages](/sql/relational-databases/system-tables/suspect-pages-transact-sql) 表中插入一行。</span><span class="sxs-lookup"><span data-stu-id="e8ef2-136">When a read error occurs on a data page in the principal/primary database, the principal/primary inserts a row in the [suspect_pages](/sql/relational-databases/system-tables/suspect-pages-transact-sql) table with the appropriate error status.</span></span> <span data-ttu-id="e8ef2-137">对于数据库镜像，主体服务器将从镜像服务器请求该页的副本。</span><span class="sxs-lookup"><span data-stu-id="e8ef2-137">For database mirroring, the principal then requests a copy of the page from the mirror.</span></span> <span data-ttu-id="e8ef2-138">对于 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]，主体数据库将向所有辅助数据库广播请求，并且从第一个响应中获取该页。</span><span class="sxs-lookup"><span data-stu-id="e8ef2-138">For [!INCLUDE[ssHADR](../../includes/sshadr-md.md)], the primary broadcasts the request to all the secondaries and gets the page from the first to respond.</span></span> <span data-ttu-id="e8ef2-139">此请求指定当前在刷新日志末尾的页 ID 和 LSN。</span><span class="sxs-lookup"><span data-stu-id="e8ef2-139">The request specifies the page ID and the LSN that is currently at the end of the flushed log.</span></span> <span data-ttu-id="e8ef2-140">此页将标记为“还原已挂起” \*\*。</span><span class="sxs-lookup"><span data-stu-id="e8ef2-140">The page is marked as *restore pending*.</span></span> <span data-ttu-id="e8ef2-141">这将使它在自动页修复尝试期间不可访问。</span><span class="sxs-lookup"><span data-stu-id="e8ef2-141">This makes it inaccessible during the automatic page-repair attempt.</span></span> <span data-ttu-id="e8ef2-142">修复尝试期间对此页的访问尝试将失败，并显示错误 829（还原已挂起）。</span><span class="sxs-lookup"><span data-stu-id="e8ef2-142">Attempts to access this page during the repair attempt will fail with error 829 (restore pending).</span></span>  
  
2.  <span data-ttu-id="e8ef2-143">收到页请求后，镜像/辅助数据库将等待，直到将日志重做到请求中指定的 LSN 处。</span><span class="sxs-lookup"><span data-stu-id="e8ef2-143">After receiving the page request, the mirror/secondary waits until it has redone the log up to the LSN specified in the request.</span></span> <span data-ttu-id="e8ef2-144">然后，镜像/辅助数据库将在其数据库副本中尝试访问此页。</span><span class="sxs-lookup"><span data-stu-id="e8ef2-144">Then, the mirror/secondary tries to access the page in its copy of the database.</span></span> <span data-ttu-id="e8ef2-145">如果可以访问此页，则镜像/辅助数据库将此页的副本发送到主体/主数据库。</span><span class="sxs-lookup"><span data-stu-id="e8ef2-145">If the page can be accessed, the mirror/secondary sends the copy of the page to the principal/primary.</span></span> <span data-ttu-id="e8ef2-146">否则，镜像/辅助数据库将向主体/主数据库返回错误，并且自动页修复失败。</span><span class="sxs-lookup"><span data-stu-id="e8ef2-146">Otherwise, the mirror/secondary returns an error to the principal/primary, and the automatic page-repair attempt fails.</span></span>  
  
3.  <span data-ttu-id="e8ef2-147">主体/主数据库处理包含此页新副本的响应。</span><span class="sxs-lookup"><span data-stu-id="e8ef2-147">The principal/primary processes the response that contains the fresh copy of the page.</span></span>  
  
4.  <span data-ttu-id="e8ef2-148">自动页修复尝试修复可疑页后，此页将在 **suspect_pages** 表中标记为已还原 (**event_type** = 5)。</span><span class="sxs-lookup"><span data-stu-id="e8ef2-148">After the automatic page-repair attempt fixes a suspect page, the page is marked in the **suspect_pages** table as restored (**event_type** = 5).</span></span>  
  
5.  <span data-ttu-id="e8ef2-149">如果此页 I/O 错误导致出现任何 [延迟的事务](../../relational-databases/backup-restore/deferred-transactions-sql-server.md)，则修复此页后，主体/主数据库将尝试解决这些事务。</span><span class="sxs-lookup"><span data-stu-id="e8ef2-149">If the page I/O error caused any [deferred transactions](../../relational-databases/backup-restore/deferred-transactions-sql-server.md), after you repair the page, the principal/primary tries to resolve those transactions.</span></span>  
  

  
##  <a name="handling-io-errors-on-the-mirrorsecondary-database"></a><a name="SecondaryIOErrors"></a><span data-ttu-id="e8ef2-150">处理镜像/辅助数据库上的 i/o 错误</span><span class="sxs-lookup"><span data-stu-id="e8ef2-150">Handling I/O Errors on the Mirror/Secondary Database</span></span>  
 <span data-ttu-id="e8ef2-151">处理在镜像/辅助数据库中发生的数据页 I/O 错误通常采用与数据库镜像和 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]相同的方式。</span><span class="sxs-lookup"><span data-stu-id="e8ef2-151">I/O errors on data pages that occur on the mirror/secondary database are handled in generally the same way by database mirroring and by [!INCLUDE[ssHADR](../../includes/sshadr-md.md)].</span></span>  
  
1.  <span data-ttu-id="e8ef2-152">对于数据库镜像，如果镜像服务器在其重做日志记录时遇到一个或多个页 I/O 错误，则镜像会话将进入 SUSPENDED 状态。</span><span class="sxs-lookup"><span data-stu-id="e8ef2-152">With database mirroring, if the mirror encounters one or more page I/O errors when it redoes a log record, the mirroring session enters the SUSPENDED state.</span></span> <span data-ttu-id="e8ef2-153">对于 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]，如果辅助副本在其重做日志记录时遇到一个或多个页 I/O 错误，则辅助数据库将进入 SUSPENDED 状态。</span><span class="sxs-lookup"><span data-stu-id="e8ef2-153">With [!INCLUDE[ssHADR](../../includes/sshadr-md.md)], if a secondary replica encounters one or more page I/O errors when it redoes a log record, the secondary database enters the SUSPENDED state.</span></span> <span data-ttu-id="e8ef2-154">此时，镜像/辅助数据库使用相应的错误状态在 **suspect_pages** 表中插入一行。</span><span class="sxs-lookup"><span data-stu-id="e8ef2-154">At that point, the mirror/secondary inserts a row in the **suspect_pages** table with the appropriate error status.</span></span> <span data-ttu-id="e8ef2-155">然后，镜像/辅助数据库从主体/主数据库请求此页的副本。</span><span class="sxs-lookup"><span data-stu-id="e8ef2-155">The mirror/secondary then requests a copy of the page from the principal/primary.</span></span>  
  
2.  <span data-ttu-id="e8ef2-156">主体/主数据库服务器尝试在其数据库副本中访问此页。</span><span class="sxs-lookup"><span data-stu-id="e8ef2-156">The principal/primary tries to access the page in its copy of the database.</span></span> <span data-ttu-id="e8ef2-157">如果可以访问此页，则主体/主数据库将此页的副本发送到镜像/辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="e8ef2-157">If the page can be accessed, the principal/primary sends the copy of page to the mirror/secondary.</span></span>  
  
3.  <span data-ttu-id="e8ef2-158">如果镜像/辅助数据库收到它请求的每一页的副本，则镜像/辅助数据库将尝试恢复镜像会话。</span><span class="sxs-lookup"><span data-stu-id="e8ef2-158">If the mirror/secondary receives copies of every page it has requested, the mirror/secondary tries to resume the mirroring session.</span></span> <span data-ttu-id="e8ef2-159">如果自动页修复尝试修复了可疑页，此页将在 **suspect_pages** 表中标记为已还原 (**event_type** = 4)。</span><span class="sxs-lookup"><span data-stu-id="e8ef2-159">If an automatic page-repair attempt fixes a suspect page, the page is marked in the **suspect_pages** table as restored (**event_type** = 4).</span></span>  
  
     <span data-ttu-id="e8ef2-160">如果镜像/辅助数据库未从主体/主数据库收到它请求的页，则自动页修复尝试将失败。</span><span class="sxs-lookup"><span data-stu-id="e8ef2-160">If a mirror/secondary does not receive a page that it requested from the principal/primary, the automatic page-repair attempt fails.</span></span> <span data-ttu-id="e8ef2-161">对于数据库镜像，镜像会话将保持挂起。</span><span class="sxs-lookup"><span data-stu-id="e8ef2-161">With database mirroring, the mirroring session remains suspended.</span></span> <span data-ttu-id="e8ef2-162">对于 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]，辅助数据库将保持挂起。</span><span class="sxs-lookup"><span data-stu-id="e8ef2-162">With [!INCLUDE[ssHADR](../../includes/sshadr-md.md)], the secondary database remains suspended.</span></span> <span data-ttu-id="e8ef2-163">如果手动恢复镜像会话或辅助数据库，则损坏的页将在同步阶段再次导致错误。</span><span class="sxs-lookup"><span data-stu-id="e8ef2-163">If the mirroring session or secondary database is resumed manually, the corrupted pages will be hit again during the synchronization phase.</span></span>  

  
##  <a name="developer-best-practice"></a><a name="DevBP"></a><span data-ttu-id="e8ef2-164">开发人员最佳做法</span><span class="sxs-lookup"><span data-stu-id="e8ef2-164">Developer Best Practice</span></span>  
 <span data-ttu-id="e8ef2-165">自动页修复是一个运行在后台的异步进程。</span><span class="sxs-lookup"><span data-stu-id="e8ef2-165">An automatic page repair is an asynchronous process that runs in the background.</span></span> <span data-ttu-id="e8ef2-166">因此，请求不可读的页的数据库操作将失败，并且不管导致失败的条件是什么均返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="e8ef2-166">Therefore, a database operation that requests an unreadable page fails and returns the error code for whatever condition caused the failure.</span></span> <span data-ttu-id="e8ef2-167">当开发用于镜像数据库或可用性数据库的应用程序时，应截获失败操作的异常。</span><span class="sxs-lookup"><span data-stu-id="e8ef2-167">When developing an application for a mirrored database or an availability database, you should intercept exceptions for failed operations.</span></span> <span data-ttu-id="e8ef2-168">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误代码为 823、824 或 829，则应稍后重试操作。</span><span class="sxs-lookup"><span data-stu-id="e8ef2-168">If the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error code is 823, 824, or 829, you should retry the operation later.</span></span>  
  

  
##  <a name="how-to-view-automatic-page-repair-attempts"></a><a name="ViewAPRattempts"></a><span data-ttu-id="e8ef2-169">如何查看自动页修复尝试</span><span class="sxs-lookup"><span data-stu-id="e8ef2-169">How To: View Automatic Page-Repair Attempts</span></span>  
 <span data-ttu-id="e8ef2-170">下面的动态管理视图返回对应于给定可用性数据库或镜像数据库上最新自动页修复尝试的行，每个数据库最多可对应 100 行。</span><span class="sxs-lookup"><span data-stu-id="e8ef2-170">The following dynamic management views return rows for the latest automatic page-repair attempts on a given availability database or mirrored database, with a maximum of 100 rows per database.</span></span>  
  
-   <span data-ttu-id="e8ef2-171">**AlwaysOn 可用性组：**</span><span class="sxs-lookup"><span data-stu-id="e8ef2-171">**AlwaysOn Availability Groups:**</span></span>  
  
     [<span data-ttu-id="e8ef2-172">sys.dm_hadr_auto_page_repair (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="e8ef2-172">sys.dm_hadr_auto_page_repair &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-auto-page-repair-transact-sql)  
  
     <span data-ttu-id="e8ef2-173">为针对任何可用性数据库（位于服务器实例为任何可用性组承载的可用性副本上）的每一个自动页修复尝试都返回一行。</span><span class="sxs-lookup"><span data-stu-id="e8ef2-173">Returns a row for every automatic page-repair attempt on any availability database on an availability replica that is hosted for any availability group by the server instance.</span></span>  
  
-   <span data-ttu-id="e8ef2-174">**数据库镜像：**</span><span class="sxs-lookup"><span data-stu-id="e8ef2-174">**Database mirroring:**</span></span>  
  
     [<span data-ttu-id="e8ef2-175">sys.dm_db_mirroring_auto_page_repair (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="e8ef2-175">sys.dm_db_mirroring_auto_page_repair &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/database-mirroring-sys-dm-db-mirroring-auto-page-repair)  
  
     <span data-ttu-id="e8ef2-176">对服务器实例上所有镜像数据库的每个自动页修复尝试返回一行。</span><span class="sxs-lookup"><span data-stu-id="e8ef2-176">Returns a row for every automatic page-repair attempt on any mirrored database on the server instance.</span></span>  
  
 
  
## <a name="see-also"></a><span data-ttu-id="e8ef2-177">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e8ef2-177">See Also</span></span>  
 <span data-ttu-id="e8ef2-178">[管理 suspect_pages 表 (SQL Server)](../../relational-databases/backup-restore/manage-the-suspect-pages-table-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e8ef2-178">[Manage the suspect_pages Table &#40;SQL Server&#41;](../../relational-databases/backup-restore/manage-the-suspect-pages-table-sql-server.md) </span></span>  
 <span data-ttu-id="e8ef2-179">[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e8ef2-179">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="e8ef2-180">数据库镜像 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="e8ef2-180">Database Mirroring &#40;SQL Server&#41;</span></span>](../../database-engine/database-mirroring/database-mirroring-sql-server.md)  
  
  
