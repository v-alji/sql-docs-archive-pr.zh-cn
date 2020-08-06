---
title: 在 AlwaysOn 辅助数据库上启动数据移动 (SQL Server) |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], databases
ms.assetid: 498eb3fb-6a43-434d-ad95-68a754232c45
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3ce4f80b456244cd6e024377383abe75e002057a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693483"
---
# <a name="start-data-movement-on-an-alwayson-secondary-database-sql-server"></a><span data-ttu-id="cd3fa-102">启动 AlwaysOn 辅助数据库的数据移动 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="cd3fa-102">Start Data Movement on an AlwaysOn Secondary Database (SQL Server)</span></span>
  <span data-ttu-id="cd3fa-103">本主题包含有关如何在将数据库添加到 AlwaysOn 可用性组后启动数据同步的信息。</span><span class="sxs-lookup"><span data-stu-id="cd3fa-103">This topic contains information about how to start data synchronization after you add a database to an AlwaysOn availability group.</span></span> <span data-ttu-id="cd3fa-104">对于每个新的主副本，必须在承载辅助副本的服务器实例上准备辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="cd3fa-104">For each new primary replica, secondary databases must be prepared on the server instances that host the secondary replicas.</span></span> <span data-ttu-id="cd3fa-105">然后，必须将这些辅助数据库手动添加到可用性组。</span><span class="sxs-lookup"><span data-stu-id="cd3fa-105">Then each of these secondary databases must be manually joined to the availability group.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cd3fa-106">如果文件路径在每个承载可用性组的可用性副本的服务器实例上完全相同，则 [新建可用性组向导](use-the-availability-group-wizard-sql-server-management-studio.md)、 [将副本添加到可用性组向导](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)或 [将数据库添加到可用性组向导](availability-group-add-database-to-group-wizard.md) 可为你自动启动数据同步。</span><span class="sxs-lookup"><span data-stu-id="cd3fa-106">If the file paths are identical on every server instance that hosts an availability replica for an availability group, the [New Availability Group Wizard](use-the-availability-group-wizard-sql-server-management-studio.md), [Add Replica to Availability Group Wizard](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md), or [Add Database to Availability Group Wizard](availability-group-add-database-to-group-wizard.md) might be able to automatically start data synchronization for you.</span></span>  
  
 <span data-ttu-id="cd3fa-107">若要手动启动数据同步，需要依次连接到每个承载可用性组的辅助副本的服务器实例并完成以下步骤：</span><span class="sxs-lookup"><span data-stu-id="cd3fa-107">To start data synchronization manually, you need to connect, in turn, to each server instance that is hosting a secondary replica for the availability group and complete the following steps:</span></span>  
  
1.  <span data-ttu-id="cd3fa-108">还原每个主数据库及其事务日志的当前副本（使用 RESTORE WITH NORECOVERY）。</span><span class="sxs-lookup"><span data-stu-id="cd3fa-108">Restore current backups of each primary database and its transaction log (using RESTORE WITH NORECOVERY).</span></span> <span data-ttu-id="cd3fa-109">您可以使用以下两种可选方法中的一种：</span><span class="sxs-lookup"><span data-stu-id="cd3fa-109">You can use either of the following alternative approaches:</span></span>  
  
    -   <span data-ttu-id="cd3fa-110">使用 RESTORE WITH NORECOVERY 手动还原主数据库的最新数据库备份，然后使用 RESTORE WITH NORECOVERY 还原各个后续日志备份。</span><span class="sxs-lookup"><span data-stu-id="cd3fa-110">Manually restore a recent database backup of the primary database using RESTORE WITH NORECOVERY, and then restore each subsequent log backup using RESTORE WITH NORECOVERY.</span></span> <span data-ttu-id="cd3fa-111">在每个承载可用性组的辅助副本的服务器实例上执行此还原序列。</span><span class="sxs-lookup"><span data-stu-id="cd3fa-111">Perform this restore sequence on every server instance that hosts a secondary replica for the availability group.</span></span>  
  
         <span data-ttu-id="cd3fa-112">**有关详细信息：**</span><span class="sxs-lookup"><span data-stu-id="cd3fa-112">**For more information:**</span></span>  
  
         [<span data-ttu-id="cd3fa-113">为可用性组手动准备辅助数据库 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="cd3fa-113">Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;</span></span>](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
    -   <span data-ttu-id="cd3fa-114">如果您在将一个或多个日志传送主数据库添加到可用性组，则可能能够将一个或多个相应的辅助数据库从日志传送迁移到 AlwaysOn 可用性组。</span><span class="sxs-lookup"><span data-stu-id="cd3fa-114">If you are adding one or more log shipping primary databases to an availability group, you might be able to migrate one or more of the corresponding secondary databases from log shipping to AlwaysOn Availability Groups.</span></span> <span data-ttu-id="cd3fa-115">迁移日志传送辅助数据库要求它使用与主数据库相同的数据库名称以及驻留在承载可用性组的辅助副本的服务器实例上。</span><span class="sxs-lookup"><span data-stu-id="cd3fa-115">Migrating a log shipping secondary database requires that it use the same database name as the primary database and that it reside on a server instance that is hosting a secondary replica for the availability group.</span></span> <span data-ttu-id="cd3fa-116">此外，必须配置可用性组以便主副本成为备份的首选并且是执行备份的候选（即，具有 >0 的备份优先级）。</span><span class="sxs-lookup"><span data-stu-id="cd3fa-116">Furthermore, the availability group must be configured so that the primary replica is preferred for backups and is a candidate for performing backups (that is, that has a backup priority that is >0).</span></span> <span data-ttu-id="cd3fa-117">在备份作业已在主数据库上运行后，您将需要禁用该备份作业；并且在还原作业已在给定辅助数据库上运行后，将需要禁用还原作业。</span><span class="sxs-lookup"><span data-stu-id="cd3fa-117">Once the backup job has run on the primary database, you will need to disable the backup job, and once the restore job has run on a given secondary database, you will need to disable the restore job.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="cd3fa-118">在您为可用性组创建了所有辅助数据库后，如果您想要在辅助副本上执行备份，将需要重新配置该可用性组的自动备份首选项。</span><span class="sxs-lookup"><span data-stu-id="cd3fa-118">After you have created all the secondary databases for the availability group, if you want to perform backups on secondary replicas, you will need to re-configure the automated backup preference of the availability group.</span></span>  
  
         <span data-ttu-id="cd3fa-119">**有关详细信息：**</span><span class="sxs-lookup"><span data-stu-id="cd3fa-119">**For more information:**</span></span>  
  
         [<span data-ttu-id="cd3fa-120">从日志传送迁移到 AlwaysOn 可用性组 &#40;SQL Server 的先决条件&#41;</span><span class="sxs-lookup"><span data-stu-id="cd3fa-120">Prerequisites for Migrating from Log Shipping to AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](prereqs-migrating-log-shipping-to-always-on-availability-groups.md)  
  
         [<span data-ttu-id="cd3fa-121">配置可用性副本备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="cd3fa-121">Configure Backup on Availability Replicas &#40;SQL Server&#41;</span></span>](configure-backup-on-availability-replicas-sql-server.md)  
  
2.  <span data-ttu-id="cd3fa-122">尽快将每个新准备的辅助数据库加入可用性组。</span><span class="sxs-lookup"><span data-stu-id="cd3fa-122">As soon as possible, join each newly prepared secondary database to the availability group.</span></span>  
  
     <span data-ttu-id="cd3fa-123">**有关详细信息：**</span><span class="sxs-lookup"><span data-stu-id="cd3fa-123">**For more information:**</span></span>  
  
     [<span data-ttu-id="cd3fa-124">将辅助数据库联接到可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="cd3fa-124">Join a Secondary Database to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
##  <a name="related-tasks"></a><a name="LaunchWiz"></a> <span data-ttu-id="cd3fa-125">相关任务</span><span class="sxs-lookup"><span data-stu-id="cd3fa-125">Related Tasks</span></span>  
  
-   [<span data-ttu-id="cd3fa-126">使用“新建可用性组”对话框 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="cd3fa-126">Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;</span></span>](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="cd3fa-127">使用“将副本添加到可用性组向导”(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="cd3fa-127">Use the Add Replica to Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="cd3fa-128">使用“将数据库添加到可用性组向导”(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="cd3fa-128">Use the Add Database to Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](availability-group-add-database-to-group-wizard.md)  
  
## <a name="see-also"></a><span data-ttu-id="cd3fa-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cd3fa-129">See Also</span></span>  
 [<span data-ttu-id="cd3fa-130">AlwaysOn 可用性组 &#40;SQL Server 概述&#41;</span><span class="sxs-lookup"><span data-stu-id="cd3fa-130">Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](overview-of-always-on-availability-groups-sql-server.md)  
  
  
