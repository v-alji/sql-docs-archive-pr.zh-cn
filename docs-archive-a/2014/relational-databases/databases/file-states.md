---
title: 文件状态 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- restoring file state [SQL Server]
- verifying file states
- current file states
- verifying filegroup states
- file states [SQL Server]
- online file state
- offline file state [SQL Server]
- viewing filegroup states
- viewing file states
- suspect file state
- recovering file state [SQL Server]
- current filegroup state
- recovery pending file state [SQL Server]
- displaying file states
- states [SQL Server], files
- displaying filegroup states
- defunct file state
ms.assetid: b426474d-8954-4df0-b78b-887becfbe8d6
author: stevestein
ms.author: sstein
ms.openlocfilehash: b7cad94527d9191609a6920b5dfa200a98cd8bbd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589684"
---
# <a name="file-states"></a><span data-ttu-id="d8345-102">文件状态</span><span class="sxs-lookup"><span data-stu-id="d8345-102">File States</span></span>
  <span data-ttu-id="d8345-103">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中，数据库文件的状态独立于数据库的状态。</span><span class="sxs-lookup"><span data-stu-id="d8345-103">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the state of a database file is maintained independently from the state of the database.</span></span> <span data-ttu-id="d8345-104">文件始终处于一个特定状态，例如 ONLINE 或 OFFLINE。</span><span class="sxs-lookup"><span data-stu-id="d8345-104">A file is always in one specific state, such as ONLINE or OFFLINE.</span></span> <span data-ttu-id="d8345-105">若要查看文件的当前状态，请使用 [sys.master_files](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql) 或 [sys.database_files](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql) 目录视图。</span><span class="sxs-lookup"><span data-stu-id="d8345-105">To view the current state of a file, use the [sys.master_files](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql) or [sys.database_files](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql) catalog view.</span></span> <span data-ttu-id="d8345-106">如果数据库处于离线状态，则可以从 [sys.master_files](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql) 目录视图中查看文件的状态。</span><span class="sxs-lookup"><span data-stu-id="d8345-106">If the database is offline, the state of the files can be viewed from the [sys.master_files](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql) catalog view.</span></span>  
  
 <span data-ttu-id="d8345-107">文件组中文件的状态决定整个文件组的可用性。</span><span class="sxs-lookup"><span data-stu-id="d8345-107">The state of the files in a filegroup determines the availability of the whole filegroup.</span></span> <span data-ttu-id="d8345-108">文件组中的所有文件都必须联机，文件组才可用。</span><span class="sxs-lookup"><span data-stu-id="d8345-108">For a filegroup to be available, all files within the filegroup must be online.</span></span> <span data-ttu-id="d8345-109">若要查看文件组的当前状态，请使用 [sys.filegroups](/sql/relational-databases/system-catalog-views/sys-filegroups-transact-sql) 目录视图。</span><span class="sxs-lookup"><span data-stu-id="d8345-109">To view the current state of a filegroup, use the [sys.filegroups](/sql/relational-databases/system-catalog-views/sys-filegroups-transact-sql) catalog view.</span></span> <span data-ttu-id="d8345-110">如果文件组处于离线状态，而您尝试使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句访问该文件组，则操作将失败并显示一条错误。</span><span class="sxs-lookup"><span data-stu-id="d8345-110">If a filegroup is offline and you try to access the filegroup by a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement, it will fail with an error.</span></span> <span data-ttu-id="d8345-111">当查询优化器生成 SELECT 语句的查询计划时，它将避免使用位于离线文件组中的非聚集索引和索引视图，从而使这些语句成功。</span><span class="sxs-lookup"><span data-stu-id="d8345-111">When the query optimizer builds query plans for SELECT statements, it avoids nonclustered indexes and indexed views that reside in offline filegroups, letting these statements to succeed.</span></span> <span data-ttu-id="d8345-112">但是，如果脱机文件组包含目标表的堆或聚集索引，SELECT 语句将失败。</span><span class="sxs-lookup"><span data-stu-id="d8345-112">However, if the offline filegroup contains the heap or clustered index of the target table, the SELECT statements fail.</span></span> <span data-ttu-id="d8345-113">此外，如果 INSERT、UPDATE 或 DELETE 语句修改的表的索引包含在脱机文件组中，这些语句将失败。</span><span class="sxs-lookup"><span data-stu-id="d8345-113">Additionally, any INSERT, UPDATE, or DELETE statement that modifies a table with any index in an offline filegroup will fail.</span></span>  
  
## <a name="file-state-definitions"></a><span data-ttu-id="d8345-114">文件状态定义</span><span class="sxs-lookup"><span data-stu-id="d8345-114">File State Definitions</span></span>  
 <span data-ttu-id="d8345-115">下表定义了文件状态。</span><span class="sxs-lookup"><span data-stu-id="d8345-115">The following table defines the file states.</span></span>  
  
|<span data-ttu-id="d8345-116">状态</span><span class="sxs-lookup"><span data-stu-id="d8345-116">State</span></span>|<span data-ttu-id="d8345-117">定义</span><span class="sxs-lookup"><span data-stu-id="d8345-117">Definition</span></span>|  
|-----------|----------------|  
|<span data-ttu-id="d8345-118">ONLINE</span><span class="sxs-lookup"><span data-stu-id="d8345-118">ONLINE</span></span>|<span data-ttu-id="d8345-119">文件可用于所有操作。</span><span class="sxs-lookup"><span data-stu-id="d8345-119">The file is available for all operations.</span></span> <span data-ttu-id="d8345-120">如果数据库本身处于在线状态，则主文件组中的文件始终处于在线状态。</span><span class="sxs-lookup"><span data-stu-id="d8345-120">Files in the primary filegroup are always online if the database itself is online.</span></span> <span data-ttu-id="d8345-121">如果主文件组中的文件处于离线状态，则数据库将处于离线状态，并且辅助文件的状态未定义。</span><span class="sxs-lookup"><span data-stu-id="d8345-121">If a file in the primary filegroup is not online, the database is not online and the states of the secondary files are undefined.</span></span>|  
|<span data-ttu-id="d8345-122">OFFLINE</span><span class="sxs-lookup"><span data-stu-id="d8345-122">OFFLINE</span></span>|<span data-ttu-id="d8345-123">文件不可访问，并且可能不显示在磁盘中。</span><span class="sxs-lookup"><span data-stu-id="d8345-123">The file is not available for access and may not be present on the disk.</span></span> <span data-ttu-id="d8345-124">文件通过显式用户操作变为离线，并在执行其他用户操作之前保持离线状态。</span><span class="sxs-lookup"><span data-stu-id="d8345-124">Files become offline by explicit user action and remain offline until additional user action is taken.</span></span><br /><br /> <span data-ttu-id="d8345-125">\*\* \* \* 警告 \* ： \* \*\*仅当文件已损坏时才应脱机设置文件，但可以还原文件。</span><span class="sxs-lookup"><span data-stu-id="d8345-125">**\*\* Caution \*\*** A file should only be set offline when the file is corrupted, but it can be restored.</span></span> <span data-ttu-id="d8345-126">设置为离线的文件只能通过从备份还原才能设置为在线。</span><span class="sxs-lookup"><span data-stu-id="d8345-126">A file set to offline can only be set online by restoring the file from backup.</span></span> <span data-ttu-id="d8345-127">有关还原单个文件的详细信息，请参阅 [RESTORE (Transact-SQL)](/sql/t-sql/statements/restore-statements-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="d8345-127">For more information about restoring a single file, see [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql).</span></span>|  
|<span data-ttu-id="d8345-128">RESTORING</span><span class="sxs-lookup"><span data-stu-id="d8345-128">RESTORING</span></span>|<span data-ttu-id="d8345-129">正在还原文件。</span><span class="sxs-lookup"><span data-stu-id="d8345-129">The file is being restored.</span></span> <span data-ttu-id="d8345-130">文件处于还原状态（因为还原命令会影响整个文件，而不仅是页还原），并且在还原完成及文件恢复之前，一直保持此状态。</span><span class="sxs-lookup"><span data-stu-id="d8345-130">Files enter the restoring state because of a restore command affecting the whole file, not just a page restore, and remain in this state until the restore is completed and the file is recovered.</span></span>|  
|<span data-ttu-id="d8345-131">RECOVERY PENDING</span><span class="sxs-lookup"><span data-stu-id="d8345-131">RECOVERY PENDING</span></span>|<span data-ttu-id="d8345-132">文件恢复被推迟。</span><span class="sxs-lookup"><span data-stu-id="d8345-132">The recovery of the file has been postponed.</span></span> <span data-ttu-id="d8345-133">由于在段落还原过程中未还原和恢复文件，因此文件将自动进入此状态。</span><span class="sxs-lookup"><span data-stu-id="d8345-133">A file enters this state automatically because of a piecemeal restore process in which the file is not restored and recovered.</span></span> <span data-ttu-id="d8345-134">需要用户执行其他操作来解决该错误，并允许完成恢复过程。</span><span class="sxs-lookup"><span data-stu-id="d8345-134">Additional action by the user is required to resolve the error and allow for the recovery process to be completed.</span></span> <span data-ttu-id="d8345-135">有关详细信息，请参阅[段落还原 (SQL Server)](../backup-restore/piecemeal-restores-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="d8345-135">For more information, see [Piecemeal Restores &#40;SQL Server&#41;](../backup-restore/piecemeal-restores-sql-server.md).</span></span>|  
|<span data-ttu-id="d8345-136">SUSPECT</span><span class="sxs-lookup"><span data-stu-id="d8345-136">SUSPECT</span></span>|<span data-ttu-id="d8345-137">联机还原过程中，恢复文件失败。</span><span class="sxs-lookup"><span data-stu-id="d8345-137">Recovery of the file failed during an online restore process.</span></span> <span data-ttu-id="d8345-138">如果文件位于主文件组，则数据库还将标记为可疑。</span><span class="sxs-lookup"><span data-stu-id="d8345-138">If the file is in the primary filegroup, the database is also marked as suspect.</span></span> <span data-ttu-id="d8345-139">否则，仅文件处于可疑状态，而数据库仍处于在线状态。</span><span class="sxs-lookup"><span data-stu-id="d8345-139">Otherwise, only the file is suspect and the database is still online.</span></span><br /><br /> <span data-ttu-id="d8345-140">在通过以下方法之一将文件变为可用之前，该文件将保持可疑状态：</span><span class="sxs-lookup"><span data-stu-id="d8345-140">The file will remain in the suspect state until it is made available by one of the following methods:</span></span><br /><br /> <span data-ttu-id="d8345-141">还原和恢复</span><span class="sxs-lookup"><span data-stu-id="d8345-141">Restore and recovery</span></span><br /><br /> <span data-ttu-id="d8345-142">包含 REPAIR_ALLOW_DATA_LOSS 的 BCC CHECKDB</span><span class="sxs-lookup"><span data-stu-id="d8345-142">DBCC CHECKDB with REPAIR_ALLOW_DATA_LOSS</span></span>|  
|<span data-ttu-id="d8345-143">DEFUNCT</span><span class="sxs-lookup"><span data-stu-id="d8345-143">DEFUNCT</span></span>|<span data-ttu-id="d8345-144">当文件不处于在线状态时被删除。</span><span class="sxs-lookup"><span data-stu-id="d8345-144">The file was dropped when it was not online.</span></span> <span data-ttu-id="d8345-145">删除离线文件组后，文件组中的所有文件都将失效。</span><span class="sxs-lookup"><span data-stu-id="d8345-145">All files in a filegroup become defunct when an offline filegroup is removed.</span></span>|  
  
## <a name="related-content"></a><span data-ttu-id="d8345-146">相关内容</span><span class="sxs-lookup"><span data-stu-id="d8345-146">Related Content</span></span>  
 [<span data-ttu-id="d8345-147">ALTER DATABASE (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="d8345-147">ALTER DATABASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql)  
  
 [<span data-ttu-id="d8345-148">数据库状态</span><span class="sxs-lookup"><span data-stu-id="d8345-148">Database States</span></span>](database-states.md)  
  
 [<span data-ttu-id="d8345-149">镜像状态 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="d8345-149">Mirroring States &#40;SQL Server&#41;</span></span>](../../database-engine/database-mirroring/mirroring-states-sql-server.md)  
  
 [<span data-ttu-id="d8345-150">DBCC CHECKDB (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="d8345-150">DBCC CHECKDB &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)  
  
 [<span data-ttu-id="d8345-151">数据库文件和文件组</span><span class="sxs-lookup"><span data-stu-id="d8345-151">Database Files and Filegroups</span></span>](database-files-and-filegroups.md)  
  
  
