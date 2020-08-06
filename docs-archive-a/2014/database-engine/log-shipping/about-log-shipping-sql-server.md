---
title: 关于日志传送 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- secondary servers [SQL Server]
- log shipping [SQL Server], jobs
- copy jobs [SQL Server]
- primary databases [SQL Server]
- log shipping [SQL Server], monitoring
- log shipping [SQL Server], about log shipping
- alert jobs [SQL Server]
- availability [SQL Server]
- jobs [SQL Server], log shipping
- monitor servers [SQL Server]
- restore jobs [SQL Server]
- log shipping [SQL Server]
- backup jobs [SQL Server]
- primary servers [SQL Server]
ms.assetid: 55da6b94-3a4b-4bae-850f-4bf7f6e918ca
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: cbf36e0ddd94ec0ab0a40a448e50602decfc0645
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689009"
---
# <a name="about-log-shipping-sql-server"></a><span data-ttu-id="03c62-102">关于日志传送 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="03c62-102">About Log Shipping (SQL Server)</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="03c62-103">使用日志传送，可以自动将“主服务器”实例上“主数据库”内的事务日志备份发送到单独“辅助服务器”实例上的一个或多个“辅助数据库”。</span><span class="sxs-lookup"><span data-stu-id="03c62-103">Log shipping allows you to automatically send transaction log backups from a *primary database* on a *primary server* instance to one or more *secondary databases* on separate *secondary server* instances.</span></span> <span data-ttu-id="03c62-104">事务日志备份分别应用于每个辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="03c62-104">The transaction log backups are applied to each of the secondary databases individually.</span></span> <span data-ttu-id="03c62-105">可选的第三个服务器实例（称为“监视服务器 ”）记录备份和还原操作的历史记录及状态，还可以在无法按计划执行这些操作时引发警报。</span><span class="sxs-lookup"><span data-stu-id="03c62-105">An optional third server instance, known as the *monitor server*, records the history and status of backup and restore operations and, optionally, raises alerts if these operations fail to occur as scheduled.</span></span>  
  
 <span data-ttu-id="03c62-106">**本主题内容：**</span><span class="sxs-lookup"><span data-stu-id="03c62-106">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="03c62-107">优点</span><span class="sxs-lookup"><span data-stu-id="03c62-107">Benefits</span></span>](#Benefits)  
  
-   [<span data-ttu-id="03c62-108">术语和定义</span><span class="sxs-lookup"><span data-stu-id="03c62-108">Terms and Definitions</span></span>](#TermsAndDefinitions)  
  
-   [<span data-ttu-id="03c62-109">日志传送概述</span><span class="sxs-lookup"><span data-stu-id="03c62-109">Log Shipping Overview</span></span>](#ComponentsAndConcepts)  
  
-   [<span data-ttu-id="03c62-110">互操作性</span><span class="sxs-lookup"><span data-stu-id="03c62-110">Interoperability</span></span>](#Interoperability)  
  
-   [<span data-ttu-id="03c62-111">相关任务</span><span class="sxs-lookup"><span data-stu-id="03c62-111">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="benefits"></a><a name="Benefits"></a> <span data-ttu-id="03c62-112">优势</span><span class="sxs-lookup"><span data-stu-id="03c62-112">Benefits</span></span>  
  
-   <span data-ttu-id="03c62-113">为单个主数据库以及一个或多个辅助数据库（每个数据库都位于单独的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例上）提供灾难恢复解决方案。</span><span class="sxs-lookup"><span data-stu-id="03c62-113">Provides a disaster-recovery solution for a single primary database and one or more secondary databases, each on a separate instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="03c62-114">支持对辅助数据库的受限的只读访问权限（在还原作业之间的间隔期间）。</span><span class="sxs-lookup"><span data-stu-id="03c62-114">Supports limited read-only access to secondary databases (during the interval between restore jobs).</span></span>  
  
-   <span data-ttu-id="03c62-115">允许用户将延迟时间定义为：从主服务器备份主数据库日志到辅助服务器必须还原（应用）日志备份之间的时间。</span><span class="sxs-lookup"><span data-stu-id="03c62-115">Allows a user-specified delay between when the primary server backs up the log of the primary database and when the secondary servers must restore (apply) the log backup.</span></span> <span data-ttu-id="03c62-116">例如，如果主数据库上的数据被意外更改，则较长的延迟会很有用。</span><span class="sxs-lookup"><span data-stu-id="03c62-116">A longer delay can be useful, for example, if data is accidentally changed on the primary database.</span></span> <span data-ttu-id="03c62-117">如果很快发现意外更改，则通过延迟，您可以在辅助数据库反映此更改之前从其中检索仍未更改的数据。</span><span class="sxs-lookup"><span data-stu-id="03c62-117">If the accidental change is noticed quickly, a delay can let you retrieve still unchanged data from a secondary database before the change is reflected there.</span></span>  
  
##  <a name="terms-and-definitions"></a><a name="TermsAndDefinitions"></a> <span data-ttu-id="03c62-118">术语和定义</span><span class="sxs-lookup"><span data-stu-id="03c62-118">Terms and Definitions</span></span>  
 <span data-ttu-id="03c62-119">主服务器 (primary server)</span><span class="sxs-lookup"><span data-stu-id="03c62-119">primary server</span></span>  
 <span data-ttu-id="03c62-120">位于生产服务器上的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="03c62-120">The instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is your production server.</span></span>  
  
 <span data-ttu-id="03c62-121">主数据库 (primary database)</span><span class="sxs-lookup"><span data-stu-id="03c62-121">primary database</span></span>  
 <span data-ttu-id="03c62-122">希望备份到其他服务器的主服务器上的数据库。</span><span class="sxs-lookup"><span data-stu-id="03c62-122">The database on the primary server that you want to back up to another server.</span></span> <span data-ttu-id="03c62-123">通过 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 进行的所有日志传送配置管理都是在主数据库中执行的。</span><span class="sxs-lookup"><span data-stu-id="03c62-123">All administration of the log shipping configuration through [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] is performed from the primary database.</span></span>  
  
 <span data-ttu-id="03c62-124">辅助服务器 (secondary server)</span><span class="sxs-lookup"><span data-stu-id="03c62-124">secondary server</span></span>  
 <span data-ttu-id="03c62-125">想要在其中保留主数据库的热备用副本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="03c62-125">The instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] where you want to keep a warm standby copy of your primary database.</span></span>  
  
 <span data-ttu-id="03c62-126">辅助数据库 (secondary database)</span><span class="sxs-lookup"><span data-stu-id="03c62-126">secondary database</span></span>  
 <span data-ttu-id="03c62-127">主数据库的热备用副本。</span><span class="sxs-lookup"><span data-stu-id="03c62-127">The warm standby copy of the primary database.</span></span> <span data-ttu-id="03c62-128">辅助数据库可以处于 RECOVERING 状态或 STANDBY 状态，这将使数据库可用于受限的只读访问。</span><span class="sxs-lookup"><span data-stu-id="03c62-128">The secondary database may be in either the RECOVERING state or the STANDBY state, which leaves the database available for limited read-only access.</span></span>  
  
 <span data-ttu-id="03c62-129">监视服务器 (monitor server)</span><span class="sxs-lookup"><span data-stu-id="03c62-129">monitor server</span></span>  
 <span data-ttu-id="03c62-130">跟踪日志传送的所有详细信息的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的可选实例，包括：</span><span class="sxs-lookup"><span data-stu-id="03c62-130">An optional instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that tracks all of the details of log shipping, including:</span></span>  
  
-   <span data-ttu-id="03c62-131">主数据库中事务日志最近一次备份的时间。</span><span class="sxs-lookup"><span data-stu-id="03c62-131">When the transaction log on the primary database was last backed up.</span></span>  
  
-   <span data-ttu-id="03c62-132">辅助服务器最近一次复制和还原备份文件的时间。</span><span class="sxs-lookup"><span data-stu-id="03c62-132">When the secondary servers last copied and restored the backup files.</span></span>  
  
-   <span data-ttu-id="03c62-133">有关任何备份失败警报的信息。</span><span class="sxs-lookup"><span data-stu-id="03c62-133">Information about any backup failure alerts.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="03c62-134">配置监视服务器之后，只有先删除日志传送才能对其进行更改。</span><span class="sxs-lookup"><span data-stu-id="03c62-134">Once the monitor server has been configured, it cannot be changed without removing log shipping first.</span></span>  
  
 <span data-ttu-id="03c62-135">备份作业</span><span class="sxs-lookup"><span data-stu-id="03c62-135">backup job</span></span>  
 <span data-ttu-id="03c62-136">一种 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业，它执行备份操作，将历史记录信息记录到本地服务器和监视服务器上，并删除旧的备份文件和历史记录信息。</span><span class="sxs-lookup"><span data-stu-id="03c62-136">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job that  performs the backup operation, logs history to the local server and the monitor server, and deletes old backup files and history information.</span></span> <span data-ttu-id="03c62-137">启用日志传送后，将在主服务器实例上创建作业类别“日志传送备份”。</span><span class="sxs-lookup"><span data-stu-id="03c62-137">When log shipping is enabled, the job category "Log Shipping Backup" is created on the primary server instance.</span></span>  
  
 <span data-ttu-id="03c62-138">复制作业</span><span class="sxs-lookup"><span data-stu-id="03c62-138">copy job</span></span>  
 <span data-ttu-id="03c62-139">一种 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业，它将备份文件从主服务器复制到辅助服务器中的可配置目标，并在辅助服务器和监视服务器中记录历史记录。</span><span class="sxs-lookup"><span data-stu-id="03c62-139">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job that copies the backup files from the primary server to a configurable destination on the secondary server and logs history on the secondary server and the monitor server.</span></span> <span data-ttu-id="03c62-140">在数据库上启用日志传送后，将在日志传送配置中在各辅助服务器上创建作业类别“日志传送复制”。</span><span class="sxs-lookup"><span data-stu-id="03c62-140">When log shipping is enabled on a database, the job category "Log Shipping Copy" is created on each secondary server in a log shipping configuration.</span></span>  
  
 <span data-ttu-id="03c62-141">还原作业</span><span class="sxs-lookup"><span data-stu-id="03c62-141">restore job</span></span>  
 <span data-ttu-id="03c62-142">一种 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业，它将复制的备份文件还原到辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="03c62-142">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job that restores the copied backup files to the secondary databases.</span></span> <span data-ttu-id="03c62-143">它将历史记录信息记录在本地服务器和监视服务器上，并删除旧文件和旧历史记录信息。</span><span class="sxs-lookup"><span data-stu-id="03c62-143">It logs history on the local server and the monitor server, and deletes old files and old history information.</span></span> <span data-ttu-id="03c62-144">在数据库上启用日志传送后，在辅助服务器实例上会创建作业类别“日志传送还原”。</span><span class="sxs-lookup"><span data-stu-id="03c62-144">When log shipping is enabled on a database, the job category "Log Shipping Restore" is created on the secondary server instance.</span></span>  
  
 <span data-ttu-id="03c62-145">警报作业</span><span class="sxs-lookup"><span data-stu-id="03c62-145">alert job</span></span>  
 <span data-ttu-id="03c62-146">一种 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业，它在备份或还原操作在指定阈值内未成功完成时为主数据库和辅助数据库引发警报。</span><span class="sxs-lookup"><span data-stu-id="03c62-146">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job that raises alerts for primary and secondary databases when a backup or restore operation does not complete successfully within a specified threshold.</span></span> <span data-ttu-id="03c62-147">在数据库上启用日志传送后，在监视服务器实例上会创建作业类别“日志传送警报”。</span><span class="sxs-lookup"><span data-stu-id="03c62-147">When log shipping is enabled on a database, job category "Log Shipping Alert" is created on the monitor server instance.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="03c62-148">对于每个警报，您需要指定警报编号。</span><span class="sxs-lookup"><span data-stu-id="03c62-148">For each alert, you need to specify an alert number.</span></span> <span data-ttu-id="03c62-149">此外，请确保配置警报以便在引发警报时通知操作员。</span><span class="sxs-lookup"><span data-stu-id="03c62-149">Also, be sure to configure the alert to notify an operator when an alert is raised.</span></span>  
  
##  <a name="log-shipping-overview"></a><a name="ComponentsAndConcepts"></a> <span data-ttu-id="03c62-150">日志传送概述</span><span class="sxs-lookup"><span data-stu-id="03c62-150">Log Shipping Overview</span></span>  
 <span data-ttu-id="03c62-151">日志传送由三项操作组成：</span><span class="sxs-lookup"><span data-stu-id="03c62-151">Log shipping consists of three operations:</span></span>  
  
1.  <span data-ttu-id="03c62-152">在主服务器实例中备份事务日志。</span><span class="sxs-lookup"><span data-stu-id="03c62-152">Back up the transaction log at the primary server instance.</span></span>  
  
2.  <span data-ttu-id="03c62-153">将事务日志文件复制到辅助服务器实例。</span><span class="sxs-lookup"><span data-stu-id="03c62-153">Copy the transaction log file to the secondary server instance.</span></span>  
  
3.  <span data-ttu-id="03c62-154">在辅助服务器实例中还原日志备份。</span><span class="sxs-lookup"><span data-stu-id="03c62-154">Restore the log backup on the secondary server instance.</span></span>  
  
 <span data-ttu-id="03c62-155">日志可传送到多个辅助服务器实例。</span><span class="sxs-lookup"><span data-stu-id="03c62-155">The log can be shipped to multiple secondary server instances.</span></span> <span data-ttu-id="03c62-156">在这些情况下，将针对每个辅助服务器实例重复执行操作 2 和操作 3。</span><span class="sxs-lookup"><span data-stu-id="03c62-156">In such cases, operations 2 and 3 are duplicated for each secondary server instance.</span></span>  
  
 <span data-ttu-id="03c62-157">日志传送配置不会自动从主服务器故障转移到辅助服务器。</span><span class="sxs-lookup"><span data-stu-id="03c62-157">A log shipping configuration does not automatically fail over from the primary server to the secondary server.</span></span> <span data-ttu-id="03c62-158">如果主数据库变为不可用，可手动使任意辅助数据库联机。</span><span class="sxs-lookup"><span data-stu-id="03c62-158">If the primary database becomes unavailable, any of the secondary databases can be brought online manually.</span></span>  
  
 <span data-ttu-id="03c62-159">您可以为了实现报表目的而使用辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="03c62-159">You can use a secondary database for reporting purposes.</span></span>  
  
 <span data-ttu-id="03c62-160">此外，可以针对日志传送配置来配置警报。</span><span class="sxs-lookup"><span data-stu-id="03c62-160">In addition, you can configure alerts for your log shipping configuration.</span></span>  
  
### <a name="a-typical-log-shipping-configuration"></a><span data-ttu-id="03c62-161">典型日志传送配置</span><span class="sxs-lookup"><span data-stu-id="03c62-161">A Typical Log Shipping Configuration</span></span>  
 <span data-ttu-id="03c62-162">下图显示了具有主服务器实例、三个辅助服务器实例和一个监视服务器实例的日志传送配置。</span><span class="sxs-lookup"><span data-stu-id="03c62-162">The following figure shows a log shipping configuration with the primary server instance, three secondary server instances, and a monitor server instance.</span></span> <span data-ttu-id="03c62-163">此图阐释了备份作业、复制作业以及还原作业所执行步骤，如下所示：</span><span class="sxs-lookup"><span data-stu-id="03c62-163">The figure illustrates the steps performed by backup, copy, and restorejobs, as follows:</span></span>  
  
1.  <span data-ttu-id="03c62-164">主服务器实例执行备份作业以在主数据库上备份事务日志。</span><span class="sxs-lookup"><span data-stu-id="03c62-164">The primary server instance runs the backup job to back up the transaction log on the primary database.</span></span> <span data-ttu-id="03c62-165">然后，该服务器实例将日志备份放入主日志备份文件（此文件将被发送到备份文件夹中）。</span><span class="sxs-lookup"><span data-stu-id="03c62-165">This server instance then places the log backup into a primary log-backup file, which it sends to the backup folder.</span></span>  <span data-ttu-id="03c62-166">在这个图中，备份文件夹位于共享目录“备份共享”中。</span><span class="sxs-lookup"><span data-stu-id="03c62-166">In this figure, the backup folder is on a shared directory-the *backup share*.</span></span>  
  
2.  <span data-ttu-id="03c62-167">全部三个辅助服务器实例都执行其各自的复制作业，以将主日志备份文件复制到它本地的目标文件夹中。</span><span class="sxs-lookup"><span data-stu-id="03c62-167">Each of the three secondary server instances runs its own copy job to copy the primary log-backup file to its own local destination folder.</span></span>  
  
3.  <span data-ttu-id="03c62-168">每个辅助服务器实例都执行其还原作业，以将日志备份从本地目标文件夹还原到本地辅助数据库中。</span><span class="sxs-lookup"><span data-stu-id="03c62-168">Each secondary server instance runs its own restore job to restore the log backup from the local destination folder onto the local secondary database.</span></span>  
  
 <span data-ttu-id="03c62-169">主服务器实例和辅助服务器实例将它们自己的历史记录和状态发送到监视服务器实例。</span><span class="sxs-lookup"><span data-stu-id="03c62-169">The primary and secondary server instances send their own history and status to the monitor server instance.</span></span>  
  
 <span data-ttu-id="03c62-170">![显示备份、复制和还原作业的配置](../media/ls-typical-configuration.gif "显示备份、复制和还原作业的配置")</span><span class="sxs-lookup"><span data-stu-id="03c62-170">![Configuration showing backup, copy, & restore jobs](../media/ls-typical-configuration.gif "Configuration showing backup, copy, & restore jobs")</span></span>  
  
##  <a name="interoperability"></a><a name="Interoperability"></a> <span data-ttu-id="03c62-171">互操作性</span><span class="sxs-lookup"><span data-stu-id="03c62-171">Interoperability</span></span>  
 <span data-ttu-id="03c62-172">日志传送功能可以与下列 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]功能或组件一起使用：</span><span class="sxs-lookup"><span data-stu-id="03c62-172">Log shipping can be used with the following features or components of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   [<span data-ttu-id="03c62-173">从日志传送迁移到 AlwaysOn 可用性组 &#40;SQL Server 的先决条件&#41;</span><span class="sxs-lookup"><span data-stu-id="03c62-173">Prerequisites for Migrating from Log Shipping to AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](../availability-groups/windows/prereqs-migrating-log-shipping-to-always-on-availability-groups.md)  
  
-   [<span data-ttu-id="03c62-174">数据库镜像和日志传送 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="03c62-174">Database Mirroring and Log Shipping &#40;SQL Server&#41;</span></span>](../database-mirroring/database-mirroring-and-log-shipping-sql-server.md)  
  
-   [<span data-ttu-id="03c62-175">日志传送和复制 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="03c62-175">Log Shipping and Replication &#40;SQL Server&#41;</span></span>](log-shipping-and-replication-sql-server.md)  
  
> [!NOTE]  
>  [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] <span data-ttu-id="03c62-176">和数据库镜像是互斥的。</span><span class="sxs-lookup"><span data-stu-id="03c62-176">and database mirroring are mutually exclusive.</span></span> <span data-ttu-id="03c62-177">不能将数据库配置为同时用于这些互斥的功能。</span><span class="sxs-lookup"><span data-stu-id="03c62-177">A database that is configured for one of these features cannot be configured for the other.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="03c62-178">相关任务</span><span class="sxs-lookup"><span data-stu-id="03c62-178">Related Tasks</span></span>  
  
-   [<span data-ttu-id="03c62-179">将日志传送升级到 SQL Server 2014 &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="03c62-179">Upgrade Log Shipping to SQL Server 2014 &#40;Transact-SQL&#41;</span></span>](upgrading-log-shipping-to-sql-server-2016-transact-sql.md)  
  
-   [<span data-ttu-id="03c62-180">配置日志传送 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="03c62-180">Configure Log Shipping &#40;SQL Server&#41;</span></span>](configure-log-shipping-sql-server.md)  
  
-   [<span data-ttu-id="03c62-181">向日志传送配置添加辅助数据库 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="03c62-181">Add a Secondary Database to a Log Shipping Configuration &#40;SQL Server&#41;</span></span>](add-a-secondary-database-to-a-log-shipping-configuration-sql-server.md)  
  
-   [<span data-ttu-id="03c62-182">从日志传送配置中删除辅助数据库 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="03c62-182">Remove a Secondary Database from a Log Shipping Configuration &#40;SQL Server&#41;</span></span>](remove-a-secondary-database-from-a-log-shipping-configuration-sql-server.md)  
  
-   [<span data-ttu-id="03c62-183">删除日志传送 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="03c62-183">Remove Log Shipping &#40;SQL Server&#41;</span></span>](remove-log-shipping-sql-server.md)  
  
-   [<span data-ttu-id="03c62-184">查看日志传送报告 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="03c62-184">View the Log Shipping Report &#40;SQL Server Management Studio&#41;</span></span>](view-the-log-shipping-report-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="03c62-185">监视日志传送 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="03c62-185">Monitor Log Shipping &#40;Transact-SQL&#41;</span></span>](monitor-log-shipping-transact-sql.md)  
  
-   [<span data-ttu-id="03c62-186">故障转移到日志传送辅助服务器 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="03c62-186">Fail Over to a Log Shipping Secondary &#40;SQL Server&#41;</span></span>](fail-over-to-a-log-shipping-secondary-sql-server.md)  
  
-   [<span data-ttu-id="03c62-187">故障转移到日志传送辅助服务器 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="03c62-187">Fail Over to a Log Shipping Secondary &#40;SQL Server&#41;</span></span>](fail-over-to-a-log-shipping-secondary-sql-server.md)  
  
-   [<span data-ttu-id="03c62-188">角色切换后登录名和作业的管理 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="03c62-188">Management of Logins and Jobs After Role Switching &#40;SQL Server&#41;</span></span>](../../sql-server/failover-clusters/management-of-logins-and-jobs-after-role-switching-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="03c62-189">另请参阅</span><span class="sxs-lookup"><span data-stu-id="03c62-189">See Also</span></span>  
 [<span data-ttu-id="03c62-190">AlwaysOn 可用性组 &#40;SQL Server 概述&#41;</span><span class="sxs-lookup"><span data-stu-id="03c62-190">Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](../availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)  
  
  
