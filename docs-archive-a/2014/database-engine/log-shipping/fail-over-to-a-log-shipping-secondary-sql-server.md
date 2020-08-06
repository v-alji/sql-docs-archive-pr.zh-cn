---
title: 故障转移到日志传送辅助服务器 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- primary databases [SQL Server]
- secondary data files [SQL Server], manual fail over
- log shipping [SQL Server], failover
- failover [SQL Server], log shipping
ms.assetid: edfe5d59-4287-49c1-96c9-dd56212027bc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 164e2809e4eff5a14ef54124df7c7ca9077793ba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690783"
---
# <a name="fail-over-to-a-log-shipping-secondary-sql-server"></a><span data-ttu-id="ffb2c-102">故障转移到日志传送辅助服务器 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ffb2c-102">Fail Over to a Log Shipping Secondary (SQL Server)</span></span>
  <span data-ttu-id="ffb2c-103">如果主服务器实例失败或需要维护，则在出现故障时转移到日志传送辅助服务器将十分有用。</span><span class="sxs-lookup"><span data-stu-id="ffb2c-103">Failing over to a log shipping secondary is useful if the primary server instance fails or requires maintenance.</span></span>  
  
## <a name="preparing-for-a-controlled-failover"></a><span data-ttu-id="ffb2c-104">为受控故障转移做准备</span><span class="sxs-lookup"><span data-stu-id="ffb2c-104">Preparing for a Controlled Failover</span></span>  
 <span data-ttu-id="ffb2c-105">通常，主数据库与辅助数据库不同步，因为主数据库在其最新的备份作业后会继续更新。</span><span class="sxs-lookup"><span data-stu-id="ffb2c-105">Typically, the primary and secondary databases are unsynchronized, because the primary database continues to be updated after its latest backup job.</span></span> <span data-ttu-id="ffb2c-106">此外，在某些情况下，最新的事务日志备份尚未复制到辅助服务器实例中，或者某些已复制的日志备份可能尚未应用到辅助数据库中。</span><span class="sxs-lookup"><span data-stu-id="ffb2c-106">Also, in some cases, recent transaction log backups have not been copied to the secondary server instances, or some copied log backups might still not have been applied to the secondary database.</span></span> <span data-ttu-id="ffb2c-107">建议如有可能，首先将所有辅助数据库与主数据库同步。</span><span class="sxs-lookup"><span data-stu-id="ffb2c-107">We recommend that you begin by synchronizing all of the secondary databases with the primary database, if possible.</span></span>  
  
 <span data-ttu-id="ffb2c-108">有关日志传送作业的信息，请参阅 [关于日志传送 (SQL Server)](about-log-shipping-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ffb2c-108">For information about log shipping jobs, see [About Log Shipping &#40;SQL Server&#41;](about-log-shipping-sql-server.md).</span></span>  
  
## <a name="failing-over"></a><span data-ttu-id="ffb2c-109">故障转移</span><span class="sxs-lookup"><span data-stu-id="ffb2c-109">Failing Over</span></span>  
 <span data-ttu-id="ffb2c-110">在出现故障时转移到辅助数据库：</span><span class="sxs-lookup"><span data-stu-id="ffb2c-110">To fail over to a secondary database:</span></span>  
  
1.  <span data-ttu-id="ffb2c-111">将所有未复制的备份文件从备份共享复制到每台辅助服务器的复制目标文件夹中。</span><span class="sxs-lookup"><span data-stu-id="ffb2c-111">Copy any uncopied backup files from the backup share to the copy destination folder of each secondary server.</span></span>  
  
2.  <span data-ttu-id="ffb2c-112">将所有未应用的事务日志备份按顺序应用到每个辅助数据库中。</span><span class="sxs-lookup"><span data-stu-id="ffb2c-112">Apply any unapplied transaction log backups in sequence to each secondary database.</span></span> <span data-ttu-id="ffb2c-113">有关详细信息，请参阅[应用事务日志备份 (SQL Server)](../../relational-databases/backup-restore/apply-transaction-log-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ffb2c-113">For more information, see [Apply Transaction Log Backups &#40;SQL Server&#41;](../../relational-databases/backup-restore/apply-transaction-log-backups-sql-server.md).</span></span>  
  
3.  <span data-ttu-id="ffb2c-114">如果可以访问主数据库，则请备份活动的事务日志，并将日志备份应用到辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="ffb2c-114">If the primary database is accessible, back up the active transaction log and apply the log backup to the secondary databases.</span></span>  
  
     <span data-ttu-id="ffb2c-115">如果原始主服务器实例没有损坏，则请使用 WITH NORECOVERY 备份主数据库的事务日志尾部。</span><span class="sxs-lookup"><span data-stu-id="ffb2c-115">If the original primary server instance is not damaged, back up the tail of the transaction log of the primary database using WITH NORECOVERY.</span></span> <span data-ttu-id="ffb2c-116">这将使数据库处于还原状态，因此用户无法使用。</span><span class="sxs-lookup"><span data-stu-id="ffb2c-116">This leaves the database in the restoring state and therefore unavailable to users.</span></span> <span data-ttu-id="ffb2c-117">最终，您将能够通过应用替换主数据库中的事务日志备份前滚此数据库。</span><span class="sxs-lookup"><span data-stu-id="ffb2c-117">Eventually you will be able to roll this database forward by applying transaction log backups from the replacement primary database.</span></span>  
  
     <span data-ttu-id="ffb2c-118">有关详细信息，请参阅[事务日志备份 (SQL Server)](../../relational-databases/backup-restore/transaction-log-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ffb2c-118">For more information, see [Transaction Log Backups &#40;SQL Server&#41;](../../relational-databases/backup-restore/transaction-log-backups-sql-server.md).</span></span>  
  
4.  <span data-ttu-id="ffb2c-119">同步辅助服务器之后，可以根据您的首选，通过恢复任一辅助数据库并将客户端重定向到该服务器实例来故障转移该辅助服务器。</span><span class="sxs-lookup"><span data-stu-id="ffb2c-119">After the secondary servers are synchronized, you can fail over to whichever one you prefer by recovering its secondary database and redirecting clients to that server instance.</span></span> <span data-ttu-id="ffb2c-120">恢复操作将使数据库处于一致的状态并使其联机。</span><span class="sxs-lookup"><span data-stu-id="ffb2c-120">Recovering puts the database into a consistent state and brings it online.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ffb2c-121">辅助数据库可用时，应确保其元数据与原始主数据库的元数据一致。</span><span class="sxs-lookup"><span data-stu-id="ffb2c-121">When you make a secondary database available, you should ensure that its metadata is consistent with the metadata of the original primary database.</span></span> <span data-ttu-id="ffb2c-122">有关详细信息，请参阅 [当数据库在其他服务器实例上可用时管理元数据 (SQL Server)](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ffb2c-122">For more information, see [Manage Metadata When Making a Database Available on Another Server Instance &#40;SQL Server&#41;](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md).</span></span>  
  
5.  <span data-ttu-id="ffb2c-123">恢复辅助数据库之后，可以将其重新配置为其他辅助数据库的主数据库。</span><span class="sxs-lookup"><span data-stu-id="ffb2c-123">After you have recovered a secondary database, you can reconfigure it to act as a primary database for other secondary databases.</span></span>  
  
     <span data-ttu-id="ffb2c-124">如果其他辅助数据库不可用，请参阅[配置日志传送 (SQL Server)](configure-log-shipping-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ffb2c-124">If no other secondary database is available, see [Configure Log Shipping &#40;SQL Server&#41;](configure-log-shipping-sql-server.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="ffb2c-125">相关任务</span><span class="sxs-lookup"><span data-stu-id="ffb2c-125">Related Tasks</span></span>  
  
-   [<span data-ttu-id="ffb2c-126">交换主日志传送服务器和辅助日志传送服务器的角色 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ffb2c-126">Change Roles Between Primary and Secondary Log Shipping Servers &#40;SQL Server&#41;</span></span>](change-roles-between-primary-and-secondary-log-shipping-servers-sql-server.md)  
  
-   [<span data-ttu-id="ffb2c-127">角色切换后登录名和作业的管理 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ffb2c-127">Management of Logins and Jobs After Role Switching &#40;SQL Server&#41;</span></span>](../../sql-server/failover-clusters/management-of-logins-and-jobs-after-role-switching-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="ffb2c-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ffb2c-128">See Also</span></span>  
 <span data-ttu-id="ffb2c-129">[日志传送表和存储过程](log-shipping-tables-and-stored-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="ffb2c-129">[Log Shipping Tables and Stored Procedures](log-shipping-tables-and-stored-procedures.md) </span></span>  
 <span data-ttu-id="ffb2c-130">[关于日志传送 (SQL Server)](about-log-shipping-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ffb2c-130">[About Log Shipping &#40;SQL Server&#41;](about-log-shipping-sql-server.md) </span></span>  
 [<span data-ttu-id="ffb2c-131">结尾日志备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ffb2c-131">Tail-Log Backups &#40;SQL Server&#41;</span></span>](../../relational-databases/backup-restore/tail-log-backups-sql-server.md)  
  
  
