---
title: 管理 DQS 数据库 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 655a67aa-d662-42f2-b982-c6217125ada8
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 7228021dd3fe0af61312eeb891081cc24e1aa95d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590386"
---
# <a name="manage-dqs-databases"></a><span data-ttu-id="0fbbd-102">管理 DQS 数据库</span><span class="sxs-lookup"><span data-stu-id="0fbbd-102">Manage DQS Databases</span></span>
  <span data-ttu-id="0fbbd-103">本节提供了有关可在 DQS 数据库上执行的数据库管理活动（例如备份/还原或分离/附加）的信息。</span><span class="sxs-lookup"><span data-stu-id="0fbbd-103">This section provides information about database management activities that can be performed on the DQS databases such as backup/restore or detach/attach.</span></span>  
  
##  <a name="backup-and-restore-the-dqs-databases"></a><a name="BackupRestore"></a> <span data-ttu-id="0fbbd-104">备份和还原 DQS 数据库</span><span class="sxs-lookup"><span data-stu-id="0fbbd-104">Backup and Restore the DQS Databases</span></span>  
 <span data-ttu-id="0fbbd-105">SQL Server 数据库的备份和还原是数据库管理员经常要执行的操作，以便通过从备份数据库恢复数据在出现灾难时避免数据丢失。</span><span class="sxs-lookup"><span data-stu-id="0fbbd-105">Backup and restore of SQL Server databases are common operations that database administrators perform for preventing loss of data in a case of disaster by recovering data from the backup databases.</span></span> [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] <span data-ttu-id="0fbbd-106">主要由两个 SQL Server 数据库实现：DQS_MAIN 和 DQS_PROJECTS。</span><span class="sxs-lookup"><span data-stu-id="0fbbd-106">is primarily implemented by two SQL Server databases: DQS_MAIN and DQS_PROJECTS.</span></span> <span data-ttu-id="0fbbd-107">[!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 数据库的备份和还原过程与其他 SQL Server 数据库相似。有三个与 DQS 数据库的备份和还原相关联的挑战：</span><span class="sxs-lookup"><span data-stu-id="0fbbd-107">The backup and restore procedures of the [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) databases are similar to any other SQL Server databases.There are three challenges that are associated with backup and restore of the DQS databases:</span></span>  
  
-   <span data-ttu-id="0fbbd-108">DQS 数据库的备份和还原操作必须同步。</span><span class="sxs-lookup"><span data-stu-id="0fbbd-108">The backup and restore operations of the DQS databases must be synchronized.</span></span> <span data-ttu-id="0fbbd-109">否则，还原的 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 将不会正常工作。</span><span class="sxs-lookup"><span data-stu-id="0fbbd-109">Otherwise the restored [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] will not be functional.</span></span>  
  
-   <span data-ttu-id="0fbbd-110">这两个 DQS 数据库（DQS_MAIN 和 DQS_PROJECTS）包含程序集和其他复杂对象，而非只是简单数据库对象（例如表和存储过程）。</span><span class="sxs-lookup"><span data-stu-id="0fbbd-110">The two DQS databases, DQS_MAIN and DQS_PROJECTS, contain assemblies and other complex objects, apart from just simple database objects (such as tables and stored procedures).</span></span>  
  
-   <span data-ttu-id="0fbbd-111">在 DQS 数据库之外有一些实体，这些实体必须存在 DQS 数据库才能像 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]一样正常工作，尤其是两个 SQL Server 登录名（##MS_dqs_db_owner_login## 和 ##MS_dqs_service_login##）以及 master 数据库中的一个初始化存储过程 (DQInitDQS_MAIN)。</span><span class="sxs-lookup"><span data-stu-id="0fbbd-111">There are some entities outside of the DQS databases that must exist for the DQS databases to be functional as [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)], specifically the two SQL Server logins (##MS_dqs_db_owner_login## and ##MS_dqs_service_login##), and an initialization stored procedure (DQInitDQS_MAIN) in the master database.</span></span>  
  
 <span data-ttu-id="0fbbd-112">有关 SQL Server 中备份和还原的详细信息，请参阅 [SQL Server 数据库的备份和还原](../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="0fbbd-112">For detailed information about backup and restore in SQL Server, see [Back Up and Restore of SQL Server Databases](../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md).</span></span>  
  
### <a name="default-autogrowth-size-and-recovery-model-for-the-dqs-databases"></a><span data-ttu-id="0fbbd-113">DQS 数据库的默认自动增长大小和恢复模式</span><span class="sxs-lookup"><span data-stu-id="0fbbd-113">Default Autogrowth Size and Recovery Model for the DQS Databases</span></span>  
 <span data-ttu-id="0fbbd-114">防止 DQS 数据库和事务日志无限增长以致有可能填满硬盘：</span><span class="sxs-lookup"><span data-stu-id="0fbbd-114">To prevent DQS databases and transaction logs to grow infinitely and potentially fill the hard disk:</span></span>  
  
-   <span data-ttu-id="0fbbd-115">DQS 数据库的默认 **“自动增长”** 大小设置为 10%。</span><span class="sxs-lookup"><span data-stu-id="0fbbd-115">The default **Autogrowth** size of the DQS databases is set to 10%.</span></span>  
  
-   <span data-ttu-id="0fbbd-116">DQS 数据库的默认恢复模式设置为“简单” \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0fbbd-116">The default recovery model of the DQS databases is set to **Simple**.</span></span> <span data-ttu-id="0fbbd-117">在“简单”恢复模式下，会尽量少地记录事务日志，而且在完成事务后会自动截断日志以释放事务日志（.ldf 文件）中的空间。</span><span class="sxs-lookup"><span data-stu-id="0fbbd-117">In the Simple recovery model, transactions are minimally logged, and the log truncation happens automatically after the transaction is complete to free up space in the transaction log (.ldf file).</span></span> <span data-ttu-id="0fbbd-118">有关简单恢复模式的详细信息，请参阅[完整数据库备份 (SQL Server)](../relational-databases/backup-restore/full-database-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="0fbbd-118">For detailed information about the simple recovery model, see [Full Database Backups &#40;SQL Server&#41;](../relational-databases/backup-restore/full-database-backups-sql-server.md).</span></span>  
  
> [!IMPORTANT]
>  -   <span data-ttu-id="0fbbd-119">在“简单”恢复模式中，日志记录长时间处于活动状态时（例如，占用时间很长的事务），日志截断可能被延迟，因此可能填满事务日志。</span><span class="sxs-lookup"><span data-stu-id="0fbbd-119">In the Simple recovery model, when log records remain active for a long time (for example, a long and time-consuming transaction), log truncation can be delayed, and therefore can result in the filling up of transaction log.</span></span> <span data-ttu-id="0fbbd-120">此外，日志截断并不减小物理日志文件（.ldf 文件）的大小。</span><span class="sxs-lookup"><span data-stu-id="0fbbd-120">Also, log truncation does not reduce the size of the physical log file (.ldf file).</span></span> <span data-ttu-id="0fbbd-121">若要减少物理日志文件的大小，需要收缩日志文件。</span><span class="sxs-lookup"><span data-stu-id="0fbbd-121">To reduce the size of a physical log file, you need to shrink the log file.</span></span> <span data-ttu-id="0fbbd-122">有关如何解决涉及事务日志的问题的信息，请参阅[事务日志 &#40;SQL Server&#41;](../relational-databases/logs/the-transaction-log-sql-server.md) 或 [https://go.microsoft.com/fwlink/?LinkId=237446](https://go.microsoft.com/fwlink/?LinkId=237446) 上的 Microsoft 技术支持文章。</span><span class="sxs-lookup"><span data-stu-id="0fbbd-122">For information about troubleshooting issues around transaction log, see [The Transaction Log &#40;SQL Server&#41;](../relational-databases/logs/the-transaction-log-sql-server.md) or the Microsoft Support article at [https://go.microsoft.com/fwlink/?LinkId=237446](https://go.microsoft.com/fwlink/?LinkId=237446).</span></span>  
> -   <span data-ttu-id="0fbbd-123">必须定期执行 DQS 数据库的完整或差异备份，同时备份事务日志以执行时间点数据恢复。</span><span class="sxs-lookup"><span data-stu-id="0fbbd-123">You must regularly perform a Full or Differential backup of the DQS databases and back up the transaction log as well to perform point-in-time recovery of data.</span></span> <span data-ttu-id="0fbbd-124">有关详细信息，请参阅[完整数据库备份 (SQL Server)](../relational-databases/backup-restore/full-database-backups-sql-server.md) 和 [备份事务日志 (SQL Server)](../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="0fbbd-124">For more information, see [Full Database Backups &#40;SQL Server&#41;](../relational-databases/backup-restore/full-database-backups-sql-server.md) and [Back Up a Transaction Log &#40;SQL Server&#41;](../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md).</span></span>  
  
##  <a name="detachattach-the-dqs-databases"></a><a name="DetachAttach"></a> <span data-ttu-id="0fbbd-125">分离/附加 DQS 数据库</span><span class="sxs-lookup"><span data-stu-id="0fbbd-125">Detach/Attach the DQS Databases</span></span>  
 <span data-ttu-id="0fbbd-126">如果您想要将 DQS 数据库更改到同一台计算机上的其他 SQL Server 实例或移动数据库，则可以分离 DQS 数据库的数据和事务日志文件，然后将这些数据库重新附加到 SQL Server 的同一个实例或其他实例。</span><span class="sxs-lookup"><span data-stu-id="0fbbd-126">You can detach the data and transaction log files of the DQS databases, and then reattach the databases to the same or another instance of SQL Server if you want to change the DQS databases to a different instance of SQL Server on the same computer or to move the database.</span></span>  
  
 <span data-ttu-id="0fbbd-127">有关在 SQL Server 中分离和附加数据库之前或在此过程中要考虑的事项的详细信息，请参阅[数据库分离和附加 (SQL Server)](../relational-databases/databases/database-detach-and-attach-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="0fbbd-127">For detailed information about things to consider before and during detaching and attaching databases in SQL Server, see [Database Detach and Attach &#40;SQL Server&#41;](../relational-databases/databases/database-detach-and-attach-sql-server.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="0fbbd-128">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="0fbbd-128">Related Tasks</span></span>  
  
|<span data-ttu-id="0fbbd-129">任务说明</span><span class="sxs-lookup"><span data-stu-id="0fbbd-129">Task Description</span></span>|<span data-ttu-id="0fbbd-130">主题</span><span class="sxs-lookup"><span data-stu-id="0fbbd-130">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="0fbbd-131">说明如何备份和还原 DQS 数据库。</span><span class="sxs-lookup"><span data-stu-id="0fbbd-131">Describes how to back up and restore the DQS databases.</span></span>|[<span data-ttu-id="0fbbd-132">备份和还原 DQS 数据库</span><span class="sxs-lookup"><span data-stu-id="0fbbd-132">Backing Up and Restoring DQS Databases</span></span>](../../2014/data-quality-services/backing-up-and-restoring-dqs-databases.md)|  
|<span data-ttu-id="0fbbd-133">介绍如何分离和附加 DQS 数据库。</span><span class="sxs-lookup"><span data-stu-id="0fbbd-133">Describes how to detach and attach the DQS databases.</span></span>|[<span data-ttu-id="0fbbd-134">分离数据库和附加 DQS 数据库</span><span class="sxs-lookup"><span data-stu-id="0fbbd-134">Detaching and Attaching DQS Databases</span></span>](../../2014/data-quality-services/detaching-and-attaching-dqs-databases.md)|  
  
## <a name="see-also"></a><span data-ttu-id="0fbbd-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0fbbd-135">See Also</span></span>  
 [<span data-ttu-id="0fbbd-136">dqs 管理</span><span class="sxs-lookup"><span data-stu-id="0fbbd-136">DQS Administration</span></span>](../../2014/data-quality-services/dqs-administration.md)  
  
  
