---
title: 段落还原 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- partial updates [SQL Server]
- staged restores [SQL Server]
- piecemeal restores [SQL Server]
- restoring [SQL Server], piecemeal restore scenario
ms.assetid: 208f55e0-0762-4cfb-85c4-d36a76ea0f5b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ebc4ea11780908f847946a01338571211b57678a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689449"
---
# <a name="piecemeal-restores-sql-server"></a><span data-ttu-id="55050-102">段落还原 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="55050-102">Piecemeal Restores (SQL Server)</span></span>
  <span data-ttu-id="55050-103">本主题仅与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise Edition 中包含多个文件或文件组的数据库相关；在简单恢复模式下，仅与包含只读文件组的数据库相关。</span><span class="sxs-lookup"><span data-stu-id="55050-103">This topic is relevant only for databases in the Enterprise edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that contain multiple files or filegroups; and, under the simple model, only for read-only filegroups.</span></span>  
  
 <span data-ttu-id="55050-104">有关段落还原和内存优化表的信息，请参阅 [对具有内存优化表的数据库进行段落还原](../in-memory-oltp/memory-optimized-tables.md)。</span><span class="sxs-lookup"><span data-stu-id="55050-104">For information about piecemeal restore and memory-optimized tables, see [Piecemeal Restore of Databases With Memory-Optimized Tables](../in-memory-oltp/memory-optimized-tables.md).</span></span>  
  
 <span data-ttu-id="55050-105"> “段落还原”允许分阶段还原和恢复包含多个文件组的数据库。</span><span class="sxs-lookup"><span data-stu-id="55050-105">*Piecemeal restore* allows databases that contain multiple filegroups to be restored and recovered in stages.</span></span> <span data-ttu-id="55050-106">段落还原包括从主文件组开始（有时也从一个或多个辅助文件组开始）的一系列还原顺序。</span><span class="sxs-lookup"><span data-stu-id="55050-106">Piecemeal restore involves a series of restore sequences, starting with the primary filegroup and, in some cases, one or more secondary filegroups.</span></span> <span data-ttu-id="55050-107">段落还原保持进行检查，以便确保数据库在结束时将是一致的。</span><span class="sxs-lookup"><span data-stu-id="55050-107">Piecemeal restore maintains checks to ensure that the database will be consistent in the end.</span></span> <span data-ttu-id="55050-108">在还原顺序结束后，如果恢复的文件有效并且与数据库一致，则恢复的文件将直接变为联机状态。</span><span class="sxs-lookup"><span data-stu-id="55050-108">After the restore sequence is completed, recovered files, if they are valid and consistent with the database, can be brought online directly.</span></span>  
  
 <span data-ttu-id="55050-109">段落还原适用于所有恢复模式，但在完整恢复模式和大容量日志恢复模式下比在简单恢复模式下更灵活。</span><span class="sxs-lookup"><span data-stu-id="55050-109">Piecemeal restore works with all recovery models, but is more flexible for the full and bulk-logged models than for the simple model.</span></span>  
  
 <span data-ttu-id="55050-110">所有的段落还原都以称为“部分还原顺序”  的初始还原顺序开始。</span><span class="sxs-lookup"><span data-stu-id="55050-110">Every piecemeal restore starts with an initial restore sequence called the *partial-restore sequence*.</span></span> <span data-ttu-id="55050-111">部分还原顺序至少还原和恢复主文件组，在简单恢复模式下还会还原和恢复所有读/写文件组。</span><span class="sxs-lookup"><span data-stu-id="55050-111">Minimally, the partial-restore sequence restores and recovers the primary filegroup and, under the simple recovery model, all read/write filegroups.</span></span> <span data-ttu-id="55050-112">在段落还原顺序中，整个数据库都必须脱机。</span><span class="sxs-lookup"><span data-stu-id="55050-112">During the piecemeal-restore sequence, the whole database must go offline.</span></span> <span data-ttu-id="55050-113">随后，数据库将处于联机状态，并且还原的文件组都处于可用状态。</span><span class="sxs-lookup"><span data-stu-id="55050-113">Thereafter, the database is online and restored filegroups are available.</span></span> <span data-ttu-id="55050-114">但是，所有未还原的文件组都将保持脱机状态，无法访问。</span><span class="sxs-lookup"><span data-stu-id="55050-114">However, any unrestored filegroups remain offline and are not accessible.</span></span> <span data-ttu-id="55050-115">不过，对于任何脱机文件组，都可以在以后通过文件还原进行还原并进入联机状态。</span><span class="sxs-lookup"><span data-stu-id="55050-115">Any offline filegroups, however, can be restored and brought online later by a file restore.</span></span>  
  
 <span data-ttu-id="55050-116">无论数据库采用何种恢复模式，部分还原顺序都从 RESTORE DATABASE 语句开始，该语句将还原完整备份并指定 PARTIAL 选项。</span><span class="sxs-lookup"><span data-stu-id="55050-116">Regardless of the recovery model that is used by the database, the partial-restore sequence starts with a RESTORE DATABASE statement that restores a full backup and specifies the PARTIAL option.</span></span> <span data-ttu-id="55050-117">PARTIAL 选项总是会启动一个新的段落还原；因此，在部分还原顺序的初始语句中，只能指定 PARTIAL 一次。</span><span class="sxs-lookup"><span data-stu-id="55050-117">The PARTIAL option always starts a new piecemeal restore; therefore, you must specify PARTIAL only one time in the initial statement of the partial-restore sequence.</span></span> <span data-ttu-id="55050-118">当部分还原顺序完成并且数据库联机后，由于余下文件的恢复被推迟，这些文件的状态将变为“恢复已挂起”。</span><span class="sxs-lookup"><span data-stu-id="55050-118">When the partial restore sequence finishes and the database is brought online, the state of the remaining files becomes "recovery pending" because their recovery has been postponed.</span></span>  
  
 <span data-ttu-id="55050-119">此后，段落还原通常包括一个或多个还原顺序，这些还原顺序称为“文件组还原顺序”  。</span><span class="sxs-lookup"><span data-stu-id="55050-119">Subsequently, a piecemeal restore typically includes one or more restore sequences, which are called *filegroup-restore sequences*.</span></span> <span data-ttu-id="55050-120">您可以等待执行特定的文件组还原顺序，等待的时间长短由您决定。</span><span class="sxs-lookup"><span data-stu-id="55050-120">You can wait to perform a specific filegroup-restore sequence for as long as you want.</span></span> <span data-ttu-id="55050-121">每个文件组还原顺序将一个或多个脱机文件组还原并恢复到与数据库一致的点。</span><span class="sxs-lookup"><span data-stu-id="55050-121">Each filegroup-restore sequence restores and recovers one or more offline filegroups to a point consistent with the database.</span></span> <span data-ttu-id="55050-122">文件组还原顺序的时间安排和数量取决于您的恢复目标、您想要还原的脱机文件组数量以及每个文件组还原顺序中还原的脱机文件组的数量。</span><span class="sxs-lookup"><span data-stu-id="55050-122">The timing and number of filegroup-restore sequences depends on your recovery goal, the number of offline filegroups you want to restore, and on how many of them you restore per filegroup-restore sequence.</span></span>  
  
 <span data-ttu-id="55050-123">执行段落还原的精确要求取决于数据库的恢复模式。</span><span class="sxs-lookup"><span data-stu-id="55050-123">The exact requirements for performing a piecemeal restore depend on the recovery model of the database.</span></span> <span data-ttu-id="55050-124">有关详细信息，请参阅本主题后面的“简单恢复模式下的段落还原”和“完整恢复模式下的段落还原”。</span><span class="sxs-lookup"><span data-stu-id="55050-124">For more information, see "Piecemeal Restore Under the Simple Recovery Model" and "Piecemeal Restore Under the Full Recovery Model," later in this topic.</span></span>  
  
## <a name="piecemeal-restore-scenarios"></a><span data-ttu-id="55050-125">段落还原方案</span><span class="sxs-lookup"><span data-stu-id="55050-125">Piecemeal Restore Scenarios</span></span>  
 <span data-ttu-id="55050-126">所有版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 都支持脱机段落还原。</span><span class="sxs-lookup"><span data-stu-id="55050-126">All editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] support offline piecemeal restores.</span></span> <span data-ttu-id="55050-127">在 Enterprise Edition 中，段落还原可以联机进行也可以脱机进行。</span><span class="sxs-lookup"><span data-stu-id="55050-127">In the Enterprise edition, a piecemeal restore can be either online or offline.</span></span> <span data-ttu-id="55050-128">脱机和联机段落还原的含义如下：</span><span class="sxs-lookup"><span data-stu-id="55050-128">The implications of offline and online piecemeal restores are as follows:</span></span>  
  
-   <span data-ttu-id="55050-129">脱机段落还原方案</span><span class="sxs-lookup"><span data-stu-id="55050-129">Offline piecemeal restore scenario</span></span>  
  
     <span data-ttu-id="55050-130">在脱机段落还原中，数据库在部分还原顺序之后处于联机状态。</span><span class="sxs-lookup"><span data-stu-id="55050-130">In an offline piecemeal restore, the database is online after the partial-restore sequence.</span></span> <span data-ttu-id="55050-131">尚未还原的文件组保持脱机状态，但是在数据库脱机后，可以根据需要还原这些文件组。</span><span class="sxs-lookup"><span data-stu-id="55050-131">Filegroups that have not yet been restored remain offline, but they can be restored as you need them after taking the database offline.</span></span>  
  
-   <span data-ttu-id="55050-132">联机段落还原方案</span><span class="sxs-lookup"><span data-stu-id="55050-132">Online piecemeal restore scenario</span></span>  
  
     <span data-ttu-id="55050-133">在进行联机段落还原时，数据库在部分还原顺序后处于联机状态，并且主文件组和所有已恢复的辅助文件组都处于可用状态。</span><span class="sxs-lookup"><span data-stu-id="55050-133">In an online piecemeal restore, after the partial-restore sequence, the database is online, and the primary filegroup and any recovered secondary filegroups are available.</span></span> <span data-ttu-id="55050-134">尚未还原的文件组保持脱机状态，但是在数据库保持联机状态时，可以根据需要还原这些文件组。</span><span class="sxs-lookup"><span data-stu-id="55050-134">Filegroups that have not yet been restored remain offline, but they can be restored as needed while the database remains online.</span></span>  
  
     <span data-ttu-id="55050-135">联机段落还原可能引起事务延迟。</span><span class="sxs-lookup"><span data-stu-id="55050-135">Online piecemeal restores can involve deferred transactions.</span></span> <span data-ttu-id="55050-136">如果仅还原了一部分文件组，则数据库中依赖联机文件组的事务可能会延迟。</span><span class="sxs-lookup"><span data-stu-id="55050-136">When only a subset of filegroups has been restored, transactions in the database that depend on online filegroups might become deferred.</span></span> <span data-ttu-id="55050-137">这是正常现象，因为整个数据库必须一致。</span><span class="sxs-lookup"><span data-stu-id="55050-137">This is typical, because the whole database must be consistent.</span></span> <span data-ttu-id="55050-138">有关详细信息，请参阅 [延迟的事务 (SQL Server)](deferred-transactions-sql-server.md)中删除失效的文件组。</span><span class="sxs-lookup"><span data-stu-id="55050-138">For more information, see [Deferred Transactions &#40;SQL Server&#41;](deferred-transactions-sql-server.md).</span></span>  
  
-   [!INCLUDE[hek_1](../../includes/hek-1-md.md)] <span data-ttu-id="55050-139">段落还原方案</span><span class="sxs-lookup"><span data-stu-id="55050-139">piecemeal restore scenario</span></span>  
  
     <span data-ttu-id="55050-140">有关内存中 OLTP 数据库的段落还原信息，请参阅 [对具有内存优化表的数据库进行段落备份和还原](../in-memory-oltp/memory-optimized-tables.md)。</span><span class="sxs-lookup"><span data-stu-id="55050-140">For information on Piecemeal Restores of In-Memory OLTP databases see [Piecemeal Backup and Restore of Databases With Memory-Optimized Tables](../in-memory-oltp/memory-optimized-tables.md).</span></span>  
  
## <a name="restrictions"></a><span data-ttu-id="55050-141">限制</span><span class="sxs-lookup"><span data-stu-id="55050-141">Restrictions</span></span>  
 <span data-ttu-id="55050-142">如果部分还原顺序不包括任何 [FILESTREAM](../blob/filestream-sql-server.md) 文件组，则不支持时间点还原。</span><span class="sxs-lookup"><span data-stu-id="55050-142">If a partial restore sequence excludes any [FILESTREAM](../blob/filestream-sql-server.md) filegroup, point-in-time restore is not supported.</span></span> <span data-ttu-id="55050-143">可以强制该还原顺序以继续执行操作。</span><span class="sxs-lookup"><span data-stu-id="55050-143">You can force the restore sequence to continue.</span></span> <span data-ttu-id="55050-144">但在 RESTORE 语句中省略的 FILESTREAM 文件组将永远无法还原。</span><span class="sxs-lookup"><span data-stu-id="55050-144">However the FILESTREAM filegroups that are omitted from your RESTORE statement can never be restored.</span></span> <span data-ttu-id="55050-145">若要强制执行时点还原，请指定 CONTINUE_AFTER_ERROR 选项以及 STOPAT、STOPATMARK 或 STOPBEFOREMARK 选项，还必须在随后的 RESTORE LOG 语句中指定后面的三个选项。</span><span class="sxs-lookup"><span data-stu-id="55050-145">To force a point-in-time restore, specify the CONTINUE_AFTER_ERROR option together with the STOPAT, STOPATMARK, or STOPBEFOREMARK option, which you must also specify in your subsequent RESTORE LOG statements.</span></span> <span data-ttu-id="55050-146">如果指定 CONTINUE_AFTER_ERROR，则部分还原顺序将成功，但 FILESTREAM 文件组将不可恢复。</span><span class="sxs-lookup"><span data-stu-id="55050-146">If you specify CONTINUE_AFTER_ERROR, the partial restore sequence succeeds and the FILESTREAM filegroup becomes unrecoverable.</span></span>  
  
## <a name="piecemeal-restore-under-the-simple-recovery-model"></a><span data-ttu-id="55050-147">简单恢复模式下的段落还原</span><span class="sxs-lookup"><span data-stu-id="55050-147">Piecemeal Restore Under the Simple Recovery Model</span></span>  
 <span data-ttu-id="55050-148">在简单恢复模式下，段落还原顺序必须从完整数据库备份或部分备份开始。</span><span class="sxs-lookup"><span data-stu-id="55050-148">Under the simple recovery model, the piecemeal restore sequence must start with a full database or partial backup.</span></span> <span data-ttu-id="55050-149">随后，如果还原的备份为差异基准，则接着还原最新差异备份。</span><span class="sxs-lookup"><span data-stu-id="55050-149">Then, if the restored backup is a differential base, restore the latest differential backup next.</span></span>  
  
 <span data-ttu-id="55050-150">在第一个部分还原顺序期间，如果您仅还原读/写文件组的一个子集，当您恢复部分还原的数据库时，未还原的文件组会失效。</span><span class="sxs-lookup"><span data-stu-id="55050-150">During the first partial restore sequence, if you restore only a subset of read/write filegroups, any unrestored filegroups become defunct when you recover the partially restored database.</span></span> <span data-ttu-id="55050-151">从部分还原顺序中省略一个读/写文件组仅适用于下列情况：</span><span class="sxs-lookup"><span data-stu-id="55050-151">Omitting a read/write filegroup from the partial-restore sequence is appropriate only in the following cases:</span></span>  
  
-   <span data-ttu-id="55050-152">需要使未还原的文件组失效。</span><span class="sxs-lookup"><span data-stu-id="55050-152">You intend for the unrestored filegroups to become defunct.</span></span>  
  
-   <span data-ttu-id="55050-153">还原顺序将到达某个恢复点，在此点处的每个未还原文件组（在部分还原顺序中的前一个还原过程中）已变成只读、已删除或失效。</span><span class="sxs-lookup"><span data-stu-id="55050-153">The restore sequence will arrive at a recovery point at which each unrestored filegroup has become read-only, dropped, or defunct (during a previous restore in the partial-restore sequence).</span></span>  
  
-   <span data-ttu-id="55050-154">完整备份是在数据库使用简单恢复模式时进行的，但恢复点却位于数据库使用完整恢复模式的某个时刻。</span><span class="sxs-lookup"><span data-stu-id="55050-154">The full backup was taken while the database was using the simple recovery model, but the recovery point is at a time when the database is using the full recovery model.</span></span> <span data-ttu-id="55050-155">有关详细信息，请参阅本主题后面的“执行已从简单恢复模式切换到完整恢复模式的数据库段落还原”。</span><span class="sxs-lookup"><span data-stu-id="55050-155">For more information, see "Performing a Piecemeal Restore of a Database Whose Recovery Model Has Been Switched from Simple to Full," later in this topic.</span></span>  
  
### <a name="requirements-for-piecemeal-restore-under-the-simple-recovery-model"></a><span data-ttu-id="55050-156">简单恢复模式下的段落还原要求</span><span class="sxs-lookup"><span data-stu-id="55050-156">Requirements for Piecemeal Restore Under the Simple Recovery Model</span></span>  
 <span data-ttu-id="55050-157">在简单恢复模式下，初始阶段还原并恢复主文件组和所有读/写辅助文件组。</span><span class="sxs-lookup"><span data-stu-id="55050-157">Under the simple recovery model, the initial stage restores and recovers the primary filegroup and all read/write secondary filegroups.</span></span> <span data-ttu-id="55050-158">在初始阶段结束后，如果恢复的文件有效并且与数据库一致，则恢复的文件将直接变为联机状态。</span><span class="sxs-lookup"><span data-stu-id="55050-158">After the initial stage is completed, recovered files, if they are valid and consistent with the database, can be brought online directly.</span></span>  
  
 <span data-ttu-id="55050-159">随后，可以在一个或多个其他阶段中还原只读文件组。</span><span class="sxs-lookup"><span data-stu-id="55050-159">Thereafter, read-only filegroups can be restored in one or more additional stages.</span></span>  
  
 <span data-ttu-id="55050-160">只有满足以下条件时，段落还原才适用于只读辅助文件组：</span><span class="sxs-lookup"><span data-stu-id="55050-160">Piecemeal restore is available for a read-only secondary filegroup only if the following are true:</span></span>  
  
-   <span data-ttu-id="55050-161">在备份时处于只读状态。</span><span class="sxs-lookup"><span data-stu-id="55050-161">Was read-only when backed up.</span></span>  
  
-   <span data-ttu-id="55050-162">保持只读状态（逻辑上与主文件组保持一致）。</span><span class="sxs-lookup"><span data-stu-id="55050-162">Has remained read-only (keeping it logically consistent with the primary filegroup).</span></span>  
  
 <span data-ttu-id="55050-163">若要执行段落还原，必须遵照以下原则：</span><span class="sxs-lookup"><span data-stu-id="55050-163">To perform a piecemeal restore, the following guidelines must be followed:</span></span>  
  
-   <span data-ttu-id="55050-164">简单恢复模式数据库的段落还原的完整备份集必须包含：</span><span class="sxs-lookup"><span data-stu-id="55050-164">A complete set of backups for the piecemeal restore of a simple recovery model database must contain the following:</span></span>  
  
    -   <span data-ttu-id="55050-165">部分数据库备份或完整数据库备份，其中包含在备份时处于读/写状态的主文件组和所有文件组。</span><span class="sxs-lookup"><span data-stu-id="55050-165">A partial or full database backup that contains the primary filegroup and all filegroups that were read/write at the time of the backup.</span></span>  
  
    -   <span data-ttu-id="55050-166">每个只读文件的备份。</span><span class="sxs-lookup"><span data-stu-id="55050-166">A backup of each read-only file.</span></span>  
  
-   <span data-ttu-id="55050-167">从备份开始直到包含主文件组的备份完成为止，辅助文件组必须始终为只读，才能使只读文件的备份与主文件组保持一致。</span><span class="sxs-lookup"><span data-stu-id="55050-167">For the backup of a read-only file to be consistent with the primary filegroup, the secondary filegroup must have been read-only from when it was backed up until the backup that contains the primary filegroup was completed.</span></span> <span data-ttu-id="55050-168">如果差异文件备份是在文件组变为只读状态之后进行的，则可以使用差异文件备份。</span><span class="sxs-lookup"><span data-stu-id="55050-168">You can use differential file backups, if they were taken after the filegroup became read-only.</span></span>  
  
### <a name="piecemeal-restore-stages-simple-recovery-model"></a><span data-ttu-id="55050-169">段落还原阶段（简单恢复模式）</span><span class="sxs-lookup"><span data-stu-id="55050-169">Piecemeal Restore Stages (Simple Recovery Model)</span></span>  
 <span data-ttu-id="55050-170">段落还原方案包括下列阶段：</span><span class="sxs-lookup"><span data-stu-id="55050-170">The piecemeal restore scenario involves the following stages:</span></span>  
  
-   <span data-ttu-id="55050-171">初始阶段（还原并恢复主文件组和所有读/写文件组）</span><span class="sxs-lookup"><span data-stu-id="55050-171">Initial stage (restore and recover the primary filegroup and all read/write filegroups)</span></span>  
  
     <span data-ttu-id="55050-172">初始阶段执行部分还原。</span><span class="sxs-lookup"><span data-stu-id="55050-172">The initial stage performs a partial restore.</span></span> <span data-ttu-id="55050-173">部分还原顺序将还原主文件组、所有读/写辅助文件组和（可选的）部分只读文件组。</span><span class="sxs-lookup"><span data-stu-id="55050-173">The partial restore sequence restores the primary filegroup, all read/write secondary filegroups, and (optionally) some of the read-only filegroups.</span></span> <span data-ttu-id="55050-174">在初始阶段中，整个数据库都必须脱机。</span><span class="sxs-lookup"><span data-stu-id="55050-174">During the initial stage, the whole database must go offline.</span></span> <span data-ttu-id="55050-175">初始阶段后，数据库将处于联机状态，并且已还原的文件组都处于可用状态。</span><span class="sxs-lookup"><span data-stu-id="55050-175">After the initial stage, the database is online, and restored filegroups are available.</span></span> <span data-ttu-id="55050-176">但是，尚未还原的任何只读文件组将保持脱机状态。</span><span class="sxs-lookup"><span data-stu-id="55050-176">However, any read-only filegroups that have not yet been restored, remain offline.</span></span>  
  
     <span data-ttu-id="55050-177">初始阶段中的第一条 RESTORE 语句必须执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="55050-177">The first RESTORE statement in the initial stage must do the following:</span></span>  
  
    -   <span data-ttu-id="55050-178">使用包含了在备份时处于读/写状态的主文件组和所有文件组的部分数据库备份或完整数据库备份。</span><span class="sxs-lookup"><span data-stu-id="55050-178">Use a partial or full database backup that contains the primary filegroup and all filegroups that were read/write at the time of the backup.</span></span> <span data-ttu-id="55050-179">常见的是通过还原部分备份来启动部分还原顺序。</span><span class="sxs-lookup"><span data-stu-id="55050-179">It is common to start a partial restore sequence by restoring a partial backup.</span></span>  
  
    -   <span data-ttu-id="55050-180">指定 PARTIAL 选项，该选项指示段落还原的开头。</span><span class="sxs-lookup"><span data-stu-id="55050-180">Specify the PARTIAL option, which indicates the start of a piecemeal restore.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="55050-181">PARTIAL 选项会执行安全检查，确保生成的数据库适合用作生产数据库。</span><span class="sxs-lookup"><span data-stu-id="55050-181">The PARTIAL option performs safety checks that ensure that the resulting database is suited for use as a production database.</span></span>  
  
    -   <span data-ttu-id="55050-182">如果备份是完整数据库备份，则指定 READ_WRITE_FILEGROUPS 选项。</span><span class="sxs-lookup"><span data-stu-id="55050-182">Specify the READ_WRITE_FILEGROUPS option if the backup is a full database backup.</span></span>  
  
-   <span data-ttu-id="55050-183">数据库处于联机状态时，可以使用一个或多个联机文件还原来还原并恢复在备份时处于只读状态的脱机只读文件。</span><span class="sxs-lookup"><span data-stu-id="55050-183">While the database is online, you can use one or more online file restores to restore and recover offline read-only files that were read-only at the time of backup.</span></span> <span data-ttu-id="55050-184">联机文件还原的时间安排取决于您希望数据联机的时间。</span><span class="sxs-lookup"><span data-stu-id="55050-184">The timing of the online file restores depends on when you want to have the data online.</span></span>  
  
     <span data-ttu-id="55050-185">您是否必须将数据还原到文件取决于：</span><span class="sxs-lookup"><span data-stu-id="55050-185">Whether you must restore data to a file depends on the following:</span></span>  
  
    -   <span data-ttu-id="55050-186">通过恢复文件而不还原任何数据，可以直接使与数据库一致的有效只读文件联机。</span><span class="sxs-lookup"><span data-stu-id="55050-186">Valid read-only files that are consistent with the database can be brought online directly by recovering them without restoring any data.</span></span>  
  
    -   <span data-ttu-id="55050-187">恢复文件之前，必须先还原已损坏的或与数据库不一致的文件。</span><span class="sxs-lookup"><span data-stu-id="55050-187">Files that are damaged or inconsistent with the database must be restored before they are recovered.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="55050-188">示例</span><span class="sxs-lookup"><span data-stu-id="55050-188">Examples</span></span>  
  
-   [<span data-ttu-id="55050-189">示例：数据库的段落还原（简单恢复模式）</span><span class="sxs-lookup"><span data-stu-id="55050-189">Example: Piecemeal Restore of Database &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [<span data-ttu-id="55050-190">示例：仅对某些文件组进行段落还原（简单恢复模式）</span><span class="sxs-lookup"><span data-stu-id="55050-190">Example: Piecemeal Restore of Only Some Filegroups &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
## <a name="piecemeal-restore-under-the-full-recovery-model"></a><span data-ttu-id="55050-191">完整恢复模式下的段落还原</span><span class="sxs-lookup"><span data-stu-id="55050-191">Piecemeal Restore Under the Full Recovery Model</span></span>  
 <span data-ttu-id="55050-192">在完整恢复模式或大容量日志恢复模式下，任何包含多个文件组的数据库都可以使用段落还原，并且可以将数据库还原到任何时间点。</span><span class="sxs-lookup"><span data-stu-id="55050-192">Under the full recovery model or bulk-logged recovery model, piecemeal restore is available for any database that contains multiple filegroups and you can restore a database to any point in time.</span></span> <span data-ttu-id="55050-193">段落还原的还原顺序如下：</span><span class="sxs-lookup"><span data-stu-id="55050-193">The restore sequences of a piecemeal restore behave as follows:</span></span>  
  
-   <span data-ttu-id="55050-194">部分还原顺序</span><span class="sxs-lookup"><span data-stu-id="55050-194">Partial-restore sequence</span></span>  
  
     <span data-ttu-id="55050-195">部分还原顺序会还原主文件组和（可选的）部分辅助文件组。</span><span class="sxs-lookup"><span data-stu-id="55050-195">The partial restore sequence restores the primary filegroup and, optionally, some of the secondary filegroups.</span></span>  
  
     <span data-ttu-id="55050-196">第一个 RESTORE DATABASE 语句必须执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="55050-196">The first RESTORE DATABASE statement must do the following:</span></span>  
  
    -   <span data-ttu-id="55050-197">指定 PARTIAL 选项。</span><span class="sxs-lookup"><span data-stu-id="55050-197">Specify the PARTIAL option.</span></span> <span data-ttu-id="55050-198">它表示段落还原的开始。</span><span class="sxs-lookup"><span data-stu-id="55050-198">This indicates the start of a piecemeal restore.</span></span>  
  
    -   <span data-ttu-id="55050-199">使用包含主文件组的任何完整数据库备份。</span><span class="sxs-lookup"><span data-stu-id="55050-199">Use any full database backup that contains the primary filegroup.</span></span> <span data-ttu-id="55050-200">常见的做法是通过还原部分备份来启动部分还原顺序。</span><span class="sxs-lookup"><span data-stu-id="55050-200">The common practice is to start a partial restore sequence by restoring a partial backup.</span></span>  
  
    -   <span data-ttu-id="55050-201">若要还原到特定的时间点，必须在部分还原顺序中指定该时间。</span><span class="sxs-lookup"><span data-stu-id="55050-201">To restore to a specific point in time, you must specify the time in the partial restore sequence.</span></span> <span data-ttu-id="55050-202">还原顺序的每个后续步骤都必须指定相同的时间点。</span><span class="sxs-lookup"><span data-stu-id="55050-202">Every successive step of the restore sequence must specify the same point in time.</span></span>  
  
-   <span data-ttu-id="55050-203">文件组还原顺序会使其他文件组联机并处于与数据库一致的某个点。</span><span class="sxs-lookup"><span data-stu-id="55050-203">Filegroup-restore sequences bring additional filegroups online to a point consistent with the database.</span></span>  
  
     <span data-ttu-id="55050-204">在 Enterprise Edition 中，当数据库保持联机状态时，可还原和恢复任何脱机辅助文件组。</span><span class="sxs-lookup"><span data-stu-id="55050-204">In the Enterprise edition, any offline secondary filegroup can be restored and recovered while the database remains online.</span></span> <span data-ttu-id="55050-205">如果特定只读文件未损坏且与数据库一致，则该文件无需还原。</span><span class="sxs-lookup"><span data-stu-id="55050-205">If a specific read-only file is undamaged and consistent with the database, the file does not have to be restored.</span></span> <span data-ttu-id="55050-206">有关详细信息，请参阅[恢复数据库而不还原数据 (Transact-SQL)](recover-a-database-without-restoring-data-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="55050-206">For more information, see [Recover a Database Without Restoring Data &#40;Transact-SQL&#41;](recover-a-database-without-restoring-data-transact-sql.md).</span></span>  
  
### <a name="applying-log-backups"></a><span data-ttu-id="55050-207">应用日志备份</span><span class="sxs-lookup"><span data-stu-id="55050-207">Applying Log Backups</span></span>  
 <span data-ttu-id="55050-208">如果在文件备份创建之前，只读文件组就已处于只读状态，则该文件组无需应用日志备份，并且文件还原会跳过日志备份的应用过程。</span><span class="sxs-lookup"><span data-stu-id="55050-208">If a read-only filegroup has been read-only since before the file backup was created, applying log backups to the filegroup is unnecessary and is skipped by file restore.</span></span> <span data-ttu-id="55050-209">如果文件组是读/写文件组，则必须将未中断的日志备份链应用于上一次完整还原或差异还原，文件组才能前进到当前的日志文件。</span><span class="sxs-lookup"><span data-stu-id="55050-209">If the filegroup is read/write, an unbroken chain of log backups must be applied to the last full or differential restore to bring the filegroup forward to the current log file.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="55050-210">示例</span><span class="sxs-lookup"><span data-stu-id="55050-210">Examples</span></span>  
  
-   [<span data-ttu-id="55050-211">示例：数据库的段落还原（完整恢复模式）</span><span class="sxs-lookup"><span data-stu-id="55050-211">Example: Piecemeal Restore of Database &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-full-recovery-model.md)  
  
-   [<span data-ttu-id="55050-212">示例：仅对某些文件组进行段落还原（完整恢复模式）</span><span class="sxs-lookup"><span data-stu-id="55050-212">Example: Piecemeal Restore of Only Some Filegroups &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-full-recovery-model.md)  
  
## <a name="performing-a-piecemeal-restore-of-a-database-whose-recovery-model-has-been-switched-from-simple-to-full"></a><span data-ttu-id="55050-213">执行已从简单恢复模式切换到完整恢复模式的数据库段落还原</span><span class="sxs-lookup"><span data-stu-id="55050-213">Performing a Piecemeal Restore of a Database Whose Recovery Model Has Been Switched from Simple to Full</span></span>  
 <span data-ttu-id="55050-214">可以对自完整或部分数据库备份后已从简单恢复模式切换到完整恢复模式的数据库执行段落还原。</span><span class="sxs-lookup"><span data-stu-id="55050-214">You can perform a piecemeal restore of a database that has been switched from the simple recovery model to the full recovery model since the full partial or database backup.</span></span> <span data-ttu-id="55050-215">例如，假设要对某个数据库执行下列步骤：</span><span class="sxs-lookup"><span data-stu-id="55050-215">For example, consider a database for which you take the following steps:</span></span>  
  
1.  <span data-ttu-id="55050-216">创建简单模式数据库的一个部分备份 (backup_1)。</span><span class="sxs-lookup"><span data-stu-id="55050-216">Create a partial backup (backup_1) of a simple-model database.</span></span>  
  
2.  <span data-ttu-id="55050-217">一段时间后，将恢复模式更改为完整恢复模式。</span><span class="sxs-lookup"><span data-stu-id="55050-217">After some time, change the recovery model to full.</span></span>  
  
3.  <span data-ttu-id="55050-218">创建一个差异备份。</span><span class="sxs-lookup"><span data-stu-id="55050-218">Create a differential backup.</span></span>  
  
4.  <span data-ttu-id="55050-219">开始进行日志备份。</span><span class="sxs-lookup"><span data-stu-id="55050-219">Start taking log backups.</span></span>  
  
 <span data-ttu-id="55050-220">此后，下列顺序是有效的：</span><span class="sxs-lookup"><span data-stu-id="55050-220">Thereafter, the following sequence is valid:</span></span>  
  
1.  <span data-ttu-id="55050-221">省略一些辅助文件组的部分还原。</span><span class="sxs-lookup"><span data-stu-id="55050-221">A partial restore that omits some secondary filegroups.</span></span>  
  
2.  <span data-ttu-id="55050-222">后面跟有其他所需还原的差异还原。</span><span class="sxs-lookup"><span data-stu-id="55050-222">A differential restore followed by any other needed restores.</span></span>  
  
3.  <span data-ttu-id="55050-223">随后为 backup_1 部分备份中读/写辅助文件组 (WITH NORECOVERY) 的文件还原</span><span class="sxs-lookup"><span data-stu-id="55050-223">Later, a file restore of a read/write secondary filegroup WITH NORECOVERY from the backup_1 partial backup</span></span>  
  
4.  <span data-ttu-id="55050-224">后面跟有在原始段落还原顺序中还原的用于将数据还原到原始恢复点的任何其他备份的差异备份。</span><span class="sxs-lookup"><span data-stu-id="55050-224">The differential backup followed by any other backups that were restored in the original piecemeal restore sequence to restore the data up to the original recovery point.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55050-225">另请参阅</span><span class="sxs-lookup"><span data-stu-id="55050-225">See Also</span></span>  
 <span data-ttu-id="55050-226">[应用事务日志备份 (SQL Server)](transaction-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="55050-226">[Apply Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span></span>  
 <span data-ttu-id="55050-227">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="55050-227">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="55050-228">[将 SQL Server 数据库还原到某个时间点（完整恢复模式）](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="55050-228">[Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md) </span></span>  
 <span data-ttu-id="55050-229">[还原和恢复概述 (SQL Server)](restore-and-recovery-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="55050-229">[Restore and Recovery Overview &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span></span>  
 [<span data-ttu-id="55050-230">计划和执行还原顺序（完整恢复模式）</span><span class="sxs-lookup"><span data-stu-id="55050-230">Plan and Perform Restore Sequences &#40;Full Recovery Model&#41;</span></span>](plan-and-perform-restore-sequences-full-recovery-model.md)  
  
  
