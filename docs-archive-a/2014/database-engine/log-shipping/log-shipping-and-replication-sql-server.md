---
title: 日志传送和复制 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], log shipping and
- log shipping [SQL Server], replication and
ms.assetid: 132bebfd-0206-4d23-829a-b38e5ed17bc9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e3b1a0e08c5850b9e31202965909dfcfe1273e47
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588030"
---
# <a name="log-shipping-and-replication-sql-server"></a><span data-ttu-id="7c049-102">日志传送和复制 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="7c049-102">Log Shipping and Replication (SQL Server)</span></span>
  <span data-ttu-id="7c049-103">日志传送涉及单个数据库的两个副本，而这两个副本通常驻留在不同的计算机上。</span><span class="sxs-lookup"><span data-stu-id="7c049-103">Log shipping involves two copies of a single database that typically reside on different computers.</span></span> <span data-ttu-id="7c049-104">在任何给定时间都只有一个数据库副本可供客户端使用。</span><span class="sxs-lookup"><span data-stu-id="7c049-104">At any given time, only one copy of the database is currently available to clients.</span></span> <span data-ttu-id="7c049-105">该副本称为主数据库。</span><span class="sxs-lookup"><span data-stu-id="7c049-105">This copy is known as the primary database.</span></span> <span data-ttu-id="7c049-106">通过日志传送将客户端对主数据库所做的更新传播到数据库的另一副本（称为辅助数据库）。</span><span class="sxs-lookup"><span data-stu-id="7c049-106">Updates made by clients to the primary database are propagated by means of log shipping to the other copy of the database, known as the secondary database.</span></span> <span data-ttu-id="7c049-107">日志传送涉及将由主数据库上执行的每个插入、更新或删除所组成的事务日志应用到辅助数据库上。</span><span class="sxs-lookup"><span data-stu-id="7c049-107">Log shipping involves applying the transaction log from every insertion, update, or deletion made on the primary database onto the secondary database.</span></span>  
  
 <span data-ttu-id="7c049-108">日志传送可以与复制一起使用，具有以下行为：</span><span class="sxs-lookup"><span data-stu-id="7c049-108">Log shipping can be used in conjunction with replication, with the following behavior:</span></span>  
  
-   <span data-ttu-id="7c049-109">日志传送故障转移后，复制不继续。</span><span class="sxs-lookup"><span data-stu-id="7c049-109">Replication does not continue after a log shipping failover.</span></span> <span data-ttu-id="7c049-110">如果发生故障转移，复制代理不连接到辅助数据库，因此不将事务复制到订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="7c049-110">If a failover occurs, replication agents do not connect to the secondary, so transactions are not replicated to Subscribers.</span></span> <span data-ttu-id="7c049-111">如果发生到主数据库的故障回复，则复制恢复。</span><span class="sxs-lookup"><span data-stu-id="7c049-111">If a failback to the primary occurs, replication resumes.</span></span> <span data-ttu-id="7c049-112">所有由日志传送从辅助数据库复制回主数据库的事务均被复制到订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="7c049-112">All transactions that log shipping copies from the secondary back to the primary are replicated to Subscribers.</span></span>  
  
-   <span data-ttu-id="7c049-113">如果主数据库永久丢失，则可以重命名辅助数据库，以使复制可以继续。</span><span class="sxs-lookup"><span data-stu-id="7c049-113">If the primary is permanently lost, the secondary can be renamed so that replication can continue.</span></span> <span data-ttu-id="7c049-114">本主题的其余部分说明处理此情况的要求和过程。</span><span class="sxs-lookup"><span data-stu-id="7c049-114">The remainder of this topic describes the requirements and procedures for handling this case.</span></span> <span data-ttu-id="7c049-115">给出的示例是发布数据库（对日志传送最常见的数据库），但也可以对订阅数据库和分发数据库应用类似的过程。</span><span class="sxs-lookup"><span data-stu-id="7c049-115">The example given is the publication database, which is the most common database to log ship, but a similar process can also be applied to subscription and distribution databases.</span></span>  
  
 <span data-ttu-id="7c049-116">有关无需重新配置复制即可恢复复制中所涉及数据库的信息，请参阅 [备份和还原复制的数据库](../../relational-databases/replication/administration/back-up-and-restore-replicated-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="7c049-116">For information about recovering databases involved in replication without any need to reconfigure replication, see [Back Up and Restore Replicated Databases](../../relational-databases/replication/administration/back-up-and-restore-replicated-databases.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7c049-117">建议使用数据库镜像而不使用日志传送，以便提供发布数据库的可用性。</span><span class="sxs-lookup"><span data-stu-id="7c049-117">We recommend using database mirroring, rather than log shipping, to provide availability for the publication database.</span></span> <span data-ttu-id="7c049-118">有关详细信息，请参阅 [数据库镜像和复制 (SQL Server)](../database-mirroring/database-mirroring-and-replication-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="7c049-118">For more information, see [Database Mirroring and Replication &#40;SQL Server&#41;](../database-mirroring/database-mirroring-and-replication-sql-server.md).</span></span>  
  
## <a name="requirements-and-procedures-for-replicating-from-the-secondary-if-the-primary-is-lost"></a><span data-ttu-id="7c049-119">主数据库丢失时从辅助数据库复制的要求和过程</span><span class="sxs-lookup"><span data-stu-id="7c049-119">Requirements and Procedures for Replicating from the Secondary If the Primary Is Lost</span></span>  
 <span data-ttu-id="7c049-120">注意以下要求和注意事项：</span><span class="sxs-lookup"><span data-stu-id="7c049-120">Be aware of the following requirements and considerations:</span></span>  
  
-   <span data-ttu-id="7c049-121">如果主数据库包含多个发布数据库，则将所有发布数据库日志传送到同一个辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="7c049-121">If a primary contains more than one publication database, log ship all of the publication databases to the same secondary.</span></span>  
  
-   <span data-ttu-id="7c049-122">辅助服务器实例的安装路径必须与主服务器实例的路径相同。</span><span class="sxs-lookup"><span data-stu-id="7c049-122">The installation path for the secondary server instance must be the same as the primary.</span></span> <span data-ttu-id="7c049-123">辅助服务器中的用户数据库位置必须与主服务器中的位置相同。</span><span class="sxs-lookup"><span data-stu-id="7c049-123">User database locations on the secondary server must be the same as on the primary.</span></span>  
  
-   <span data-ttu-id="7c049-124">在主服务器中备份服务主键。</span><span class="sxs-lookup"><span data-stu-id="7c049-124">Back up the service master key at the primary.</span></span> <span data-ttu-id="7c049-125">该键将在辅助服务器中还原。</span><span class="sxs-lookup"><span data-stu-id="7c049-125">This key will be restored at the secondary.</span></span> <span data-ttu-id="7c049-126">有关详细信息，请参阅 [BACKUP SERVICE MASTER KEY (Transact-SQL)](/sql/t-sql/statements/backup-service-master-key-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="7c049-126">For more information, see [BACKUP SERVICE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-service-master-key-transact-sql).</span></span>  
  
-   <span data-ttu-id="7c049-127">日志传送不保证不丢失数据。</span><span class="sxs-lookup"><span data-stu-id="7c049-127">Log shipping does not guarantee against data loss.</span></span> <span data-ttu-id="7c049-128">主数据库上的失败可能导致丢失尚未备份的数据或失败期间所丢失备份的数据。</span><span class="sxs-lookup"><span data-stu-id="7c049-128">A failure on the primary database can result in the loss of data that has not yet been backed up or for backups that are lost during the failure.</span></span>  
  
### <a name="log-shipping-with-transactional-replication"></a><span data-ttu-id="7c049-129">事务复制的日志传送</span><span class="sxs-lookup"><span data-stu-id="7c049-129">Log Shipping with Transactional Replication</span></span>  
 <span data-ttu-id="7c049-130">对于事务复制，日志传送的行为取决于 **sync with backup** 选项。</span><span class="sxs-lookup"><span data-stu-id="7c049-130">For transactional replication, the behavior of log shipping depends on the **sync with backup** option.</span></span> <span data-ttu-id="7c049-131">可以对发布数据库和分发数据库设置此选项；发布服务器的日志传送仅与对发布数据库的设置有关。</span><span class="sxs-lookup"><span data-stu-id="7c049-131">This option can be set on the publication database and distribution database; in log shipping for the Publisher, only the setting on the publication database is relevant.</span></span>  
  
 <span data-ttu-id="7c049-132">对发布数据库设置此选项可以确保事务在发布数据库上备份之前不会传递到分发数据库。</span><span class="sxs-lookup"><span data-stu-id="7c049-132">Setting this option on the publication database ensures that transactions are not delivered to the distribution database until they are backed up at the publication database.</span></span> <span data-ttu-id="7c049-133">这样，便可以在辅助服务器中还原上次的发布数据库备份，而分发数据库不可能具有已还原发布数据库中没有的事务。</span><span class="sxs-lookup"><span data-stu-id="7c049-133">The last publication database backup can then be restored at the secondary server without any possibility of the distribution database having transactions that the restored publication database does not have.</span></span> <span data-ttu-id="7c049-134">此选项可保证在发布服务器故障转移到辅助服务器时，发布服务器、分发服务器和订阅服务器之间保持一致性。</span><span class="sxs-lookup"><span data-stu-id="7c049-134">This option guarantees that if the Publisher fails over to a secondary server, consistency is maintained between the Publisher, Distributor, and Subscribers.</span></span> <span data-ttu-id="7c049-135">由于直到将事务在发布服务器中备份之后才能将其传递到分发数据库，因此滞后时间和吞吐量会受到影响；如果应用程序允许此滞后时间，则建议对发布数据库设置此选项。</span><span class="sxs-lookup"><span data-stu-id="7c049-135">Latency and throughput are affected because transactions cannot be delivered to the distribution database until they have been backed up at the Publisher; if your application can tolerate this latency, we recommend that you set this option on the publication database.</span></span> <span data-ttu-id="7c049-136">如果未设置 **sync with backup** 选项，订阅服务器可能会收到辅助服务器中已恢复数据库中不再包含的更改。</span><span class="sxs-lookup"><span data-stu-id="7c049-136">If the **sync with backup** option is not set, Subscribers might receive changes that are no longer included in the recovered database at the secondary server.</span></span> <span data-ttu-id="7c049-137">有关详细信息，请参阅 [快照复制和事务复制的备份和还原策略](../../relational-databases/replication/transactional/transactional-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="7c049-137">For more information, see [Strategies for Backing Up and Restoring Snapshot and Transactional Replication](../../relational-databases/replication/transactional/transactional-replication.md).</span></span>  
  
 <span data-ttu-id="7c049-138">**使用 sync with backup 选项配置事务复制和日志传送**</span><span class="sxs-lookup"><span data-stu-id="7c049-138">**To configure transactional replication and log shipping with the sync with backup option**</span></span>  
  
1.  <span data-ttu-id="7c049-139">如果未对发布数据库设置 sync with backup 选项，请执行 `sp_replicationdboption '<publicationdatabasename>', 'sync with backup', 'true'`。</span><span class="sxs-lookup"><span data-stu-id="7c049-139">If the sync with backup option is not set on the publication database, execute `sp_replicationdboption '<publicationdatabasename>', 'sync with backup', 'true'`.</span></span> <span data-ttu-id="7c049-140">有关详细信息，请参阅 [sp_replicationdboption (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="7c049-140">For more information, see [sp_replicationdboption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql).</span></span>  
  
2.  <span data-ttu-id="7c049-141">为发布数据库配置日志传送。</span><span class="sxs-lookup"><span data-stu-id="7c049-141">Configure log shipping for the publication database.</span></span> <span data-ttu-id="7c049-142">有关详细信息，请参阅[配置日志传送 (SQL Server)](configure-log-shipping-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="7c049-142">For more information, see [Configure Log Shipping &#40;SQL Server&#41;](configure-log-shipping-sql-server.md).</span></span>  
  
3.  <span data-ttu-id="7c049-143">如果发布服务器出现故障，则使用 RESTORE LOG 的 KEEP_REPLICATION 选项，将上次的数据库日志还原到辅助服务器。</span><span class="sxs-lookup"><span data-stu-id="7c049-143">If the Publisher fails, restore the last log of the database to the secondary server, using the KEEP_REPLICATION option of RESTORE LOG.</span></span> <span data-ttu-id="7c049-144">这将保留数据库的所有复制设置。</span><span class="sxs-lookup"><span data-stu-id="7c049-144">This retains all replication settings for the database.</span></span> <span data-ttu-id="7c049-145">有关详细信息，请参阅[故障转移到日志传送辅助服务器 (SQL Server)](fail-over-to-a-log-shipping-secondary-sql-server.md) 和 [RESTORE (Transact-SQL)](/sql/t-sql/statements/restore-statements-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="7c049-145">For more information, see [Fail Over to a Log Shipping Secondary &#40;SQL Server&#41;](fail-over-to-a-log-shipping-secondary-sql-server.md) and [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql).</span></span>  
  
4.  <span data-ttu-id="7c049-146">将 **msdb** 数据库和 **master** 数据库从主服务器还原到辅助服务器。</span><span class="sxs-lookup"><span data-stu-id="7c049-146">Restore the **msdb** database and **master** databases from the primary to the secondary.</span></span> <span data-ttu-id="7c049-147">有关详细信息，请参阅[备份和还原系统数据库 (SQL Server)](../../relational-databases/backup-restore/back-up-and-restore-of-system-databases-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="7c049-147">For more information, see [Back Up and Restore of System Databases &#40;SQL Server&#41;](../../relational-databases/backup-restore/back-up-and-restore-of-system-databases-sql-server.md).</span></span> <span data-ttu-id="7c049-148">如果主服务器同时也是分发服务器，则将分发数据库从主服务器还原到辅助服务器。</span><span class="sxs-lookup"><span data-stu-id="7c049-148">If the primary was also a Distributor, restore the distribution database from the primary to the secondary.</span></span>  
  
     <span data-ttu-id="7c049-149">这些数据库在复制配置和设置方面必须与主服务器中的发布数据库一致。</span><span class="sxs-lookup"><span data-stu-id="7c049-149">These databases must be consistent with the publication database at the primary in terms of replication configuration and settings.</span></span>  
  
5.  <span data-ttu-id="7c049-150">在辅助服务器中，重命名计算机，再重命名 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例，以便与主服务器名称匹配。</span><span class="sxs-lookup"><span data-stu-id="7c049-150">At the secondary server, rename the computer and then rename the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance to match the primary server name.</span></span> <span data-ttu-id="7c049-151">有关重命名计算机的信息，请参阅 Windows 文档。</span><span class="sxs-lookup"><span data-stu-id="7c049-151">For information about renaming the computer, see the Windows documentation.</span></span> <span data-ttu-id="7c049-152">有关重命名服务器的详细信息，请参阅 [重命名托管 SQL Server 的独立实例的计算机](../install-windows/rename-a-computer-that-hosts-a-stand-alone-instance-of-sql-server.md) 和 [重命名 SQL Server 故障转移群集实例](../../sql-server/failover-clusters/install/rename-a-sql-server-failover-cluster-instance.md)。</span><span class="sxs-lookup"><span data-stu-id="7c049-152">For information about renaming the server, see [Rename a Computer that Hosts a Stand-Alone Instance of SQL Server](../install-windows/rename-a-computer-that-hosts-a-stand-alone-instance-of-sql-server.md) and [Rename a SQL Server Failover Cluster Instance](../../sql-server/failover-clusters/install/rename-a-sql-server-failover-cluster-instance.md).</span></span>  
  
6.  <span data-ttu-id="7c049-153">在辅助服务器中，还原以前从主服务器备份的服务主键。</span><span class="sxs-lookup"><span data-stu-id="7c049-153">At the secondary server, restore the service master key that was backed up from the primary.</span></span> <span data-ttu-id="7c049-154">有关详细信息，请参阅 [RESTORE SERVICE MASTER KEY (Transact-SQL)](/sql/t-sql/statements/restore-service-master-key-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="7c049-154">For more information, see [RESTORE SERVICE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-service-master-key-transact-sql).</span></span>  
  
 <span data-ttu-id="7c049-155">**不设置 sync with backup 选项的情况下配置事务复制和日志传送**</span><span class="sxs-lookup"><span data-stu-id="7c049-155">**To configure transactional replication and log shipping without the sync with backup option**</span></span>  
  
1.  <span data-ttu-id="7c049-156">为发布数据库配置日志传送。</span><span class="sxs-lookup"><span data-stu-id="7c049-156">Configure log shipping for the publication database.</span></span> <span data-ttu-id="7c049-157">有关详细信息，请参阅[配置日志传送 (SQL Server)](configure-log-shipping-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="7c049-157">For more information, see [Configure Log Shipping &#40;SQL Server&#41;](configure-log-shipping-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="7c049-158">如果发布服务器出现故障，则使用 RESTORE LOG 的 KEEP_REPLICATION 选项，将上次的数据库日志还原到辅助服务器。</span><span class="sxs-lookup"><span data-stu-id="7c049-158">If the Publisher fails, restore the last log of the database to the secondary server, using the KEEP_REPLICATION option of RESTORE LOG.</span></span> <span data-ttu-id="7c049-159">这将保留数据库的所有复制设置。</span><span class="sxs-lookup"><span data-stu-id="7c049-159">This retains all replication settings for the database.</span></span> <span data-ttu-id="7c049-160">有关详细信息，请参阅[故障转移到日志传送辅助服务器 (SQL Server)](fail-over-to-a-log-shipping-secondary-sql-server.md) 和 [RESTORE (Transact-SQL)](/sql/t-sql/statements/restore-statements-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="7c049-160">For more information, see [Fail Over to a Log Shipping Secondary &#40;SQL Server&#41;](fail-over-to-a-log-shipping-secondary-sql-server.md) and [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql).</span></span>  
  
3.  <span data-ttu-id="7c049-161">将 **msdb** 数据库和 **master** 数据库从主服务器还原到辅助服务器。</span><span class="sxs-lookup"><span data-stu-id="7c049-161">Restore the **msdb** database and **master** databases from the primary to the secondary.</span></span> <span data-ttu-id="7c049-162">有关详细信息，请参阅[备份和还原系统数据库 (SQL Server)](../../relational-databases/backup-restore/back-up-and-restore-of-system-databases-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="7c049-162">For more information, see [Back Up and Restore of System Databases &#40;SQL Server&#41;](../../relational-databases/backup-restore/back-up-and-restore-of-system-databases-sql-server.md).</span></span> <span data-ttu-id="7c049-163">如果主服务器同时也是分发服务器，则将分发数据库从主服务器还原到辅助服务器。</span><span class="sxs-lookup"><span data-stu-id="7c049-163">If the primary was also a Distributor, restore the distribution database from the primary to the secondary.</span></span>  
  
     <span data-ttu-id="7c049-164">这些数据库在复制配置和设置方面必须与主服务器中的发布数据库一致。</span><span class="sxs-lookup"><span data-stu-id="7c049-164">These databases must be consistent with the publication database at the primary in terms of replication configuration and settings.</span></span>  
  
4.  <span data-ttu-id="7c049-165">在辅助服务器中，重命名计算机，再重命名 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例，以便与主服务器名称匹配。</span><span class="sxs-lookup"><span data-stu-id="7c049-165">At the secondary server, rename the computer and then rename the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance to match the primary server name.</span></span> <span data-ttu-id="7c049-166">有关重命名计算机的信息，请参阅 Windows 文档。</span><span class="sxs-lookup"><span data-stu-id="7c049-166">For information about renaming the computer, see the Windows documentation.</span></span> <span data-ttu-id="7c049-167">有关重命名服务器的详细信息，请参阅 [重命名托管 SQL Server 的独立实例的计算机](../install-windows/rename-a-computer-that-hosts-a-stand-alone-instance-of-sql-server.md) 和 [重命名 SQL Server 故障转移群集实例](../../sql-server/failover-clusters/install/rename-a-sql-server-failover-cluster-instance.md)。</span><span class="sxs-lookup"><span data-stu-id="7c049-167">For information about renaming the server, see [Rename a Computer that Hosts a Stand-Alone Instance of SQL Server](../install-windows/rename-a-computer-that-hosts-a-stand-alone-instance-of-sql-server.md) and [Rename a SQL Server Failover Cluster Instance](../../sql-server/failover-clusters/install/rename-a-sql-server-failover-cluster-instance.md).</span></span>  
  
     <span data-ttu-id="7c049-168">可能从日志读取器代理会收到错误消息，指出发布数据库与分发数据库不同步。</span><span class="sxs-lookup"><span data-stu-id="7c049-168">You might receive an error message from the Log Reader Agent that the publication database and the distribution database are not synchronized.</span></span>  
  
5.  <span data-ttu-id="7c049-169">在辅助服务器中，还原以前从主服务器备份的服务主键。</span><span class="sxs-lookup"><span data-stu-id="7c049-169">At the secondary server, restore the service master key that was backed up from the primary.</span></span> <span data-ttu-id="7c049-170">有关详细信息，请参阅 [RESTORE SERVICE MASTER KEY (Transact-SQL)](/sql/t-sql/statements/restore-service-master-key-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="7c049-170">For more information, see [RESTORE SERVICE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-service-master-key-transact-sql).</span></span>  
  
6.  <span data-ttu-id="7c049-171">执行 **sp_replrestart**。</span><span class="sxs-lookup"><span data-stu-id="7c049-171">Execute **sp_replrestart**.</span></span> <span data-ttu-id="7c049-172">该存储过程可用于强制日志读取器代理忽略发布数据库日志中所有以前复制的事务。</span><span class="sxs-lookup"><span data-stu-id="7c049-172">This stored procedure can be used to force the Log Reader Agent to ignore all the previous replicated transactions in the publication database log.</span></span> <span data-ttu-id="7c049-173">存储过程完成后应用的事务由日志读取器代理处理。</span><span class="sxs-lookup"><span data-stu-id="7c049-173">Transactions applied after the completion of the stored procedure are processed by the Log Reader Agent.</span></span> <span data-ttu-id="7c049-174">有关详细信息，请参阅 [sp_replrestart (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-replrestart-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="7c049-174">For more information, see [sp_replrestart &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replrestart-transact-sql).</span></span>  
  
7.  <span data-ttu-id="7c049-175">存储过程成功执行后，请重新启动日志读取器代理。</span><span class="sxs-lookup"><span data-stu-id="7c049-175">Restart the Log Reader Agent after the stored procedure executes successfully.</span></span> <span data-ttu-id="7c049-176">有关详细信息，请参阅[启动和停止复制代理 (SQL Server Management Studio)](../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).</span><span class="sxs-lookup"><span data-stu-id="7c049-176">For more information, see [Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).</span></span>  
  
8.  <span data-ttu-id="7c049-177">可以在发布服务器中应用已经分发到订阅服务器的事务。</span><span class="sxs-lookup"><span data-stu-id="7c049-177">Transactions that have already been distributed to Subscriber might be applied at the Publisher.</span></span> <span data-ttu-id="7c049-178">为确保分发代理尝试在订阅服务器中重新应用这些事务时不会因错误而失败，请指定标题为“遇到数据一致性错误时继续” 的代理配置文件。</span><span class="sxs-lookup"><span data-stu-id="7c049-178">To ensure that the Distribution Agent does not fail with an error when attempting to reapply these transactions at a Subscriber, specify the agent profile titled **Continue On Data Consistency Errors**.</span></span>  
  
### <a name="log-shipping-with-merge-replication"></a><span data-ttu-id="7c049-179">合并复制的日志传送</span><span class="sxs-lookup"><span data-stu-id="7c049-179">Log Shipping with Merge Replication</span></span>  
 <span data-ttu-id="7c049-180">请按照下面过程中的步骤配置合并复制和日志传送。</span><span class="sxs-lookup"><span data-stu-id="7c049-180">Follow the steps in the procedure below to configure merge replication and log shipping.</span></span>  
  
 <span data-ttu-id="7c049-181">**配置合并复制和日志传送**</span><span class="sxs-lookup"><span data-stu-id="7c049-181">**To configure merge replication and log shipping**</span></span>  
  
1.  <span data-ttu-id="7c049-182">为发布数据库配置日志传送。</span><span class="sxs-lookup"><span data-stu-id="7c049-182">Configure log shipping for the publication database.</span></span> <span data-ttu-id="7c049-183">有关详细信息，请参阅[配置日志传送 (SQL Server)](configure-log-shipping-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="7c049-183">For more information, see [Configure Log Shipping &#40;SQL Server&#41;](configure-log-shipping-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="7c049-184">如果发布服务器出现故障，则在辅助服务器中重命名计算机，然后重命名 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例，以便与主服务器名称匹配。</span><span class="sxs-lookup"><span data-stu-id="7c049-184">If the Publisher fails, at the secondary server, rename the computer and then rename the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance to match the primary server name.</span></span> <span data-ttu-id="7c049-185">有关重命名计算机的信息，请参阅 Windows 文档。</span><span class="sxs-lookup"><span data-stu-id="7c049-185">For information about renaming the computer, see the Windows documentation.</span></span> <span data-ttu-id="7c049-186">有关重命名服务器的详细信息，请参阅 [重命名托管 SQL Server 的独立实例的计算机](../install-windows/rename-a-computer-that-hosts-a-stand-alone-instance-of-sql-server.md) 和 [重命名 SQL Server 故障转移群集实例](../../sql-server/failover-clusters/install/rename-a-sql-server-failover-cluster-instance.md)。</span><span class="sxs-lookup"><span data-stu-id="7c049-186">For information about renaming the server, see [Rename a Computer that Hosts a Stand-Alone Instance of SQL Server](../install-windows/rename-a-computer-that-hosts-a-stand-alone-instance-of-sql-server.md) and [Rename a SQL Server Failover Cluster Instance](../../sql-server/failover-clusters/install/rename-a-sql-server-failover-cluster-instance.md).</span></span>  
  
3.  <span data-ttu-id="7c049-187">使用 RESTORE LOG 的 KEEP_REPLICATION 选项，将上次的数据库日志还原到辅助服务器。</span><span class="sxs-lookup"><span data-stu-id="7c049-187">Restore the last log of the database to the secondary server, using the KEEP_REPLICATION option of RESTORE LOG.</span></span> <span data-ttu-id="7c049-188">这将保留数据库的所有复制设置。</span><span class="sxs-lookup"><span data-stu-id="7c049-188">This retains all replication settings for the database.</span></span> <span data-ttu-id="7c049-189">有关详细信息，请参阅[故障转移到日志传送辅助服务器 (SQL Server)](fail-over-to-a-log-shipping-secondary-sql-server.md) 和 [RESTORE (Transact-SQL)](/sql/t-sql/statements/restore-statements-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="7c049-189">For more information, see [Fail Over to a Log Shipping Secondary &#40;SQL Server&#41;](fail-over-to-a-log-shipping-secondary-sql-server.md) and [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql).</span></span>  
  
4.  <span data-ttu-id="7c049-190">将 **msdb** 数据库和 **master** 数据库从主服务器还原到辅助服务器。</span><span class="sxs-lookup"><span data-stu-id="7c049-190">Restore the **msdb** database and **master** databases from the primary to the secondary.</span></span> <span data-ttu-id="7c049-191">有关详细信息，请参阅[备份和还原系统数据库 (SQL Server)](../../relational-databases/backup-restore/back-up-and-restore-of-system-databases-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="7c049-191">For more information, see [Back Up and Restore of System Databases &#40;SQL Server&#41;](../../relational-databases/backup-restore/back-up-and-restore-of-system-databases-sql-server.md).</span></span> <span data-ttu-id="7c049-192">如果主服务器同时也是分发服务器，则将分发数据库从主服务器还原到辅助服务器。</span><span class="sxs-lookup"><span data-stu-id="7c049-192">If the primary was also a Distributor, restore the distribution database from the primary to the secondary.</span></span>  
  
     <span data-ttu-id="7c049-193">这些数据库在复制配置和设置方面必须与主服务器中的发布数据库一致。</span><span class="sxs-lookup"><span data-stu-id="7c049-193">These databases must be consistent with the publication database at the primary in terms of replication configuration and settings.</span></span>  
  
5.  <span data-ttu-id="7c049-194">在辅助服务器中，还原以前从主服务器备份的服务主键。</span><span class="sxs-lookup"><span data-stu-id="7c049-194">At the secondary server, restore the service master key that was backed up from the primary.</span></span> <span data-ttu-id="7c049-195">有关详细信息，请参阅 [RESTORE SERVICE MASTER KEY (Transact-SQL)](/sql/t-sql/statements/restore-service-master-key-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="7c049-195">For more information, see [RESTORE SERVICE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-service-master-key-transact-sql).</span></span>  
  
6.  <span data-ttu-id="7c049-196">将发布数据库与一个或多个订阅数据库同步。</span><span class="sxs-lookup"><span data-stu-id="7c049-196">Synchronize the publication database with one or more subscription databases.</span></span> <span data-ttu-id="7c049-197">通过此操作可以上载那些以前在发布数据库中做出的但未在已还原备份中显示的更改。</span><span class="sxs-lookup"><span data-stu-id="7c049-197">This allows you to upload those changes made previously in the publication database, but not represented in the restored backup.</span></span> <span data-ttu-id="7c049-198">可以上载的数据取决于筛选发布的方法：</span><span class="sxs-lookup"><span data-stu-id="7c049-198">The data that can be uploaded depends on the way in which a publication is filtered:</span></span>  
  
    -   <span data-ttu-id="7c049-199">如果发布未经筛选，则应能通过与最新订阅服务器同步来更新发布数据库。</span><span class="sxs-lookup"><span data-stu-id="7c049-199">If the publication is not filtered, you should be able to bring the publication database up-to-date by synchronizing with the most up-to-date Subscriber.</span></span>  
  
    -   <span data-ttu-id="7c049-200">如果发布经过筛选，则可能无法更新发布数据库。</span><span class="sxs-lookup"><span data-stu-id="7c049-200">If the publication is filtered, you might not be able to bring the publication database up-to-date.</span></span> <span data-ttu-id="7c049-201">假设有一个按如下方式分区的表：每个订阅仅收到一个区域（北部、东部、南部和西部）的客户数据。</span><span class="sxs-lookup"><span data-stu-id="7c049-201">Consider a table that is partitioned such that each subscription receives customer data only for a single region: North, East, South, and West.</span></span> <span data-ttu-id="7c049-202">如果每个数据分区至少有一个订阅服务器，那么使每个分区与订阅服务器同步会更新发布数据库。</span><span class="sxs-lookup"><span data-stu-id="7c049-202">If there is at least one Subscriber for each partition of data, synchronizing with a Subscriber for each partition should bring the publication database up-to-date.</span></span> <span data-ttu-id="7c049-203">但是，以西分区为例，如果其中的数据未复制到任何订阅服务器，那么发布服务器上的此数据就无法更新。</span><span class="sxs-lookup"><span data-stu-id="7c049-203">However, if data in the West partition, for example, was not replicated to any Subscribers, this data at the Publisher cannot be brought up-to-date.</span></span> <span data-ttu-id="7c049-204">在这种情况下，建议重新初始化所有订阅，以使发布服务器和订阅服务器中的数据收敛。</span><span class="sxs-lookup"><span data-stu-id="7c049-204">In this case, we recommend reinitializing all subscriptions so that the data at the Publisher and Subscribers converges.</span></span> <span data-ttu-id="7c049-205">有关详细信息，请参阅 [重新初始化订阅](../../relational-databases/replication/reinitialize-subscriptions.md)。</span><span class="sxs-lookup"><span data-stu-id="7c049-205">For more information, see [Reinitialize Subscriptions](../../relational-databases/replication/reinitialize-subscriptions.md).</span></span>  
  
     <span data-ttu-id="7c049-206">如果与运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之前的 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]版本的订阅服务器同步，则订阅无法匿名；它必须是客户端订阅或服务器订阅（在早期版本中称为本地订阅和全局订阅）。</span><span class="sxs-lookup"><span data-stu-id="7c049-206">If you synchronize with a Subscriber that is running a version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prior to [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], the subscription cannot be anonymous; it must be a client subscription or server subscription (referred to as local subscriptions and global subscriptions in previous releases).</span></span> <span data-ttu-id="7c049-207">有关详细信息，请参阅 [同步数据](../../relational-databases/replication/synchronize-data.md)。</span><span class="sxs-lookup"><span data-stu-id="7c049-207">For more information, see [Synchronize Data](../../relational-databases/replication/synchronize-data.md).</span></span>   
  
## <a name="see-also"></a><span data-ttu-id="7c049-208">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7c049-208">See Also</span></span>  
 <span data-ttu-id="7c049-209">[SQL Server 复制](../../relational-databases/replication/sql-server-replication.md) </span><span class="sxs-lookup"><span data-stu-id="7c049-209">[SQL Server Replication](../../relational-databases/replication/sql-server-replication.md) </span></span>  
 <span data-ttu-id="7c049-210">[关于日志传送 (SQL Server)](about-log-shipping-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="7c049-210">[About Log Shipping &#40;SQL Server&#41;](about-log-shipping-sql-server.md) </span></span>  
 [<span data-ttu-id="7c049-211">数据库镜像和复制 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="7c049-211">Database Mirroring and Replication &#40;SQL Server&#41;</span></span>](../database-mirroring/database-mirroring-and-replication-sql-server.md)  
  
  