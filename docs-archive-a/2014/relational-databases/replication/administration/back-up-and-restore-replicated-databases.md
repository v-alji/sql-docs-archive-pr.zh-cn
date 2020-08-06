---
title: 备份和还原复制的数据库 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- backups [SQL Server replication]
- administering replication, restoring
- backing up replicated databases
- backups [SQL Server replication], about backups
- restoring replicated databases [SQL Server replication]
- recovery [SQL Server replication], about recovery
- restoring databases [SQL Server], replicated databases
- backing up databases [SQL Server], replicated databases
- restoring [SQL Server replication], about restoring
- recovery [SQL Server replication]
- replication [SQL Server], administering
- distribution databases [SQL Server replication], backing up
- restoring [SQL Server replication]
- administering replication, backing up
ms.assetid: 04588807-21e7-4bbe-9727-b72f692cffa7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e91505bacf67f7f4628bd1b3f6b2cc78a6bc4c3a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587359"
---
# <a name="back-up-and-restore-replicated-databases"></a><span data-ttu-id="ecba2-102">备份和还原复制的数据库</span><span class="sxs-lookup"><span data-stu-id="ecba2-102">Back Up and Restore Replicated Databases</span></span>
  <span data-ttu-id="ecba2-103">对于复制的数据库，需要特别注意与备份和还原数据有关的信息。</span><span class="sxs-lookup"><span data-stu-id="ecba2-103">Replicated databases require special attention with regards to backing up and restoring data.</span></span> <span data-ttu-id="ecba2-104">本主题介绍了适用于各种复制类型的备份和还原策略，并提供了其详细信息的链接。</span><span class="sxs-lookup"><span data-stu-id="ecba2-104">This topic provides introductory information and links to further information on backup and restore strategies for each type of replication.</span></span>  
  
 <span data-ttu-id="ecba2-105">复制支持将复制的数据库还原到从中创建备份的同一服务器和数据库。</span><span class="sxs-lookup"><span data-stu-id="ecba2-105">Replication supports restoring replicated databases to the same server and database from which the backup was created.</span></span> <span data-ttu-id="ecba2-106">如果将复制数据库的备份还原到其他服务器或数据库，则无法保留复制设置。</span><span class="sxs-lookup"><span data-stu-id="ecba2-106">If you restore a backup of a replicated database to another server or database, replication settings cannot be preserved.</span></span> <span data-ttu-id="ecba2-107">在这种情况下，您必须在还原备份后重新创建所有发布和订阅。</span><span class="sxs-lookup"><span data-stu-id="ecba2-107">In this case, you must recreate all publications and subscriptions after backups are restored.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ecba2-108">如果正在使用日志传送，则可以将复制数据库还原到备用服务器。</span><span class="sxs-lookup"><span data-stu-id="ecba2-108">It is possible to restore a replicated database to a standby server if log shipping is being used.</span></span> <span data-ttu-id="ecba2-109">有关详细信息，请参阅[日志传送和复制 (SQL Server)](../../../database-engine/log-shipping/log-shipping-and-replication-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ecba2-109">For more information, see [Log Shipping and Replication &#40;SQL Server&#41;](../../../database-engine/log-shipping/log-shipping-and-replication-sql-server.md).</span></span>  
  
 <span data-ttu-id="ecba2-110">应定期备份复制数据库及其关联系统数据库。</span><span class="sxs-lookup"><span data-stu-id="ecba2-110">Replicated databases and their associated system databases should be backed up regularly.</span></span> <span data-ttu-id="ecba2-111">备份下列数据库：</span><span class="sxs-lookup"><span data-stu-id="ecba2-111">Back up the following databases:</span></span>  
  
-   <span data-ttu-id="ecba2-112">发布服务器上的发布数据库</span><span class="sxs-lookup"><span data-stu-id="ecba2-112">The publication database at the Publisher</span></span>  
  
-   <span data-ttu-id="ecba2-113">分发服务器上的分发数据库</span><span class="sxs-lookup"><span data-stu-id="ecba2-113">The distribution database at the Distributor</span></span>  
  
-   <span data-ttu-id="ecba2-114">各个订阅服务器上的订阅数据库</span><span class="sxs-lookup"><span data-stu-id="ecba2-114">The subscription database at each Subscriber</span></span>  
  
-   <span data-ttu-id="ecba2-115">发布服务器、分发服务器和所有订阅服务器上的 **master** 和 **msdb** 系统数据库。</span><span class="sxs-lookup"><span data-stu-id="ecba2-115">The **master** and **msdb** system databases at the Publisher, Distributor and all Subscribers.</span></span> <span data-ttu-id="ecba2-116">当备份这些数据库中的一个数据库或相关的复制数据库时，应同时备份这些数据库。</span><span class="sxs-lookup"><span data-stu-id="ecba2-116">These databases should be backed up at the same time as each other and the relevant replication database.</span></span> <span data-ttu-id="ecba2-117">例如，应在备份发布数据库的同时备份发布服务器上的 **master** 和 **msdb** 数据库。</span><span class="sxs-lookup"><span data-stu-id="ecba2-117">For example, back up the **master** and **msdb** databases at the Publisher at the same time you back up the publication database.</span></span> <span data-ttu-id="ecba2-118">如果还原发布数据库，请确保 **master** 和 **msdb** 数据库在复制配置和设置方面与发布数据库保持一致。</span><span class="sxs-lookup"><span data-stu-id="ecba2-118">If the publication database is restored, ensure that the **master** and **msdb** database are consistent with the publication database in terms of replication configuration and settings.</span></span>  
  
 <span data-ttu-id="ecba2-119">如果执行定期日志备份，则在日志备份中应捕获所有与复制相关的更改。</span><span class="sxs-lookup"><span data-stu-id="ecba2-119">If you perform regular log backups, any replication-related changes should be captured in the log backups.</span></span> <span data-ttu-id="ecba2-120">如果不执行日志备份，则当与复制相关的设置发生更改时，应执行备份。</span><span class="sxs-lookup"><span data-stu-id="ecba2-120">If you do not perform log backups, a backup should be performed whenever a setting relevant to replication is changed.</span></span> <span data-ttu-id="ecba2-121">有关详细信息，请参阅 [Common Actions Requiring an Updated Backup](common-actions-requiring-an-updated-backup.md)。</span><span class="sxs-lookup"><span data-stu-id="ecba2-121">For more information, see [Common Actions Requiring an Updated Backup](common-actions-requiring-an-updated-backup.md).</span></span>  
  
## <a name="backup-and-restore-strategies"></a><span data-ttu-id="ecba2-122">备份和还原策略</span><span class="sxs-lookup"><span data-stu-id="ecba2-122">Backup and Restore Strategies</span></span>  
 <span data-ttu-id="ecba2-123">复制拓扑中每个节点的备份和还原策略都因所用复制类型的不同而有所差异。</span><span class="sxs-lookup"><span data-stu-id="ecba2-123">The strategies for backing up and restoring each node in a replication topology differ according to the type of replication used.</span></span> <span data-ttu-id="ecba2-124">有关每种复制的备份和还原策略的信息，请参阅下列主题：</span><span class="sxs-lookup"><span data-stu-id="ecba2-124">For information on backup and restore strategies for each type of replication, see the following topics:</span></span>  
  
-   [<span data-ttu-id="ecba2-125">快照复制和事务复制的备份和还原策略</span><span class="sxs-lookup"><span data-stu-id="ecba2-125">Strategies for Backing Up and Restoring Snapshot and Transactional Replication</span></span>](strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md)  
  
-   [<span data-ttu-id="ecba2-126">合并复制的备份和还原策略</span><span class="sxs-lookup"><span data-stu-id="ecba2-126">Strategies for Backing Up and Restoring Merge Replication</span></span>](strategies-for-backing-up-and-restoring-merge-replication.md)  
  
 <span data-ttu-id="ecba2-127">作为任何恢复策略的一部分，请始终将当前复制设置的脚本保存在安全的位置。</span><span class="sxs-lookup"><span data-stu-id="ecba2-127">As part of any recovery strategy, always keep a current script of your replication settings in a safe location.</span></span> <span data-ttu-id="ecba2-128">在服务器出现故障或需要设置测试环境时，可以通过更改服务器名称引用来修改脚本，并用该脚本帮助重新创建复制设置。</span><span class="sxs-lookup"><span data-stu-id="ecba2-128">In the event of server failure or the need to set up a test environment, you can modify the script by changing server name references, and it can be used to help recreate your replication settings.</span></span> <span data-ttu-id="ecba2-129">除了编写当前复制设置的脚本之外，还应编写启用和禁用复制的脚本。</span><span class="sxs-lookup"><span data-stu-id="ecba2-129">In addition to scripting your current replication settings, you should script the enabling and disabling of replication.</span></span> <span data-ttu-id="ecba2-130">有关编写复制对象脚本的信息，请参阅 [Scripting Replication](../scripting-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="ecba2-130">For information about scripting replication objects, see [Scripting Replication](../scripting-replication.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecba2-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ecba2-131">See Also</span></span>  
 <span data-ttu-id="ecba2-132">[SQL Server 数据库的备份和还原](../../backup-restore/back-up-and-restore-of-sql-server-databases.md) </span><span class="sxs-lookup"><span data-stu-id="ecba2-132">[Back Up and Restore of SQL Server Databases](../../backup-restore/back-up-and-restore-of-sql-server-databases.md) </span></span>  
 [<span data-ttu-id="ecba2-133">Best Practices for Replication Administration</span><span class="sxs-lookup"><span data-stu-id="ecba2-133">Best Practices for Replication Administration</span></span>](best-practices-for-replication-administration.md)  
  
  
