---
title: 从备份初始化事务订阅 (复制 Transact-sql 编程) |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- manual subscription initialization [SQL Server replication]
- subscriptions [SQL Server replication], initializing
- initializing subscriptions [SQL Server replication], without snapshots
- transactional replication, backup and restore
- backups [SQL Server replication], transactional replication
ms.assetid: d0637fc4-27cc-4046-98ea-dc86b7a3bd75
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1563d58f2d54f77680781e22a162112ade1658e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578072"
---
# <a name="initialize-a-transactional-subscription-from-a-backup-replication-transact-sql-programming"></a><span data-ttu-id="12de5-102">从备份初始化事务订阅（复制 Transact-SQL 编程）</span><span class="sxs-lookup"><span data-stu-id="12de5-102">Initialize a Transactional Subscription from a Backup (Replication Transact-SQL Programming)</span></span>
  <span data-ttu-id="12de5-103">虽然通常使用快照来初始化对事务发布的订阅，但也可以使用复制存储过程通过备份初始化订阅。</span><span class="sxs-lookup"><span data-stu-id="12de5-103">Although a subscription to a transactional publication is typically initialized with a snapshot, a subscription can be initialized from a backup using replication stored procedures.</span></span> <span data-ttu-id="12de5-104">有关详细信息，请参阅 [初始化事务订阅（不使用快照）](initialize-a-transactional-subscription-without-a-snapshot.md)中手动初始化订阅。</span><span class="sxs-lookup"><span data-stu-id="12de5-104">For more information, see [Initialize a Transactional Subscription Without a Snapshot](initialize-a-transactional-subscription-without-a-snapshot.md).</span></span>  
  
### <a name="to-initialize-a-transactional-subscriber-from-a-backup"></a><span data-ttu-id="12de5-105">从备份初始化事务订阅服务器</span><span class="sxs-lookup"><span data-stu-id="12de5-105">To initialize a transactional subscriber from a backup</span></span>  
  
1.  <span data-ttu-id="12de5-106">对于现有的发布，请通过在发布服务器上对发布数据库执行 [sp_helppublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql) 来确保该发布支持从备份进行初始化操作。</span><span class="sxs-lookup"><span data-stu-id="12de5-106">For an existing publication, ensure that the publication supports the ability to initialize from backup by executing [sp_helppublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql) at the Publisher on the publication database.</span></span> <span data-ttu-id="12de5-107">请注意结果集中 **allow_initialize_from_backup** 的值。</span><span class="sxs-lookup"><span data-stu-id="12de5-107">Note the value of **allow_initialize_from_backup** in the result set.</span></span>  
  
    -   <span data-ttu-id="12de5-108">如果值为 **1**，则该发布支持此功能。</span><span class="sxs-lookup"><span data-stu-id="12de5-108">If the value is **1**, the publication supports this functionality.</span></span>  
  
    -   <span data-ttu-id="12de5-109">如果值为 **0**，则在发布服务器上对发布数据库执行 [sp_changepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="12de5-109">If the value is **0**, execute [sp_changepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql) at the Publisher on the publication database.</span></span> <span data-ttu-id="12de5-110">为\*\* \@ 属性**指定**allow_initialize_from_backup**的值，并将值指定 `true` 为** \@ \*\*。</span><span class="sxs-lookup"><span data-stu-id="12de5-110">Specify a value of **allow_initialize_from_backup** for **\@property** and a value of `true` for **\@value**.</span></span>  
  
2.  <span data-ttu-id="12de5-111">对于新发布，在发布服务器上对发布数据库执行 [sp_addpublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="12de5-111">For a new publication, execute [sp_addpublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql) at the Publisher on the publication database.</span></span> <span data-ttu-id="12de5-112">将的值指定 `true` 为**allow_initialize_from_backup**。</span><span class="sxs-lookup"><span data-stu-id="12de5-112">Specify a value of `true` for **allow_initialize_from_backup**.</span></span> <span data-ttu-id="12de5-113">有关详细信息，请参阅 [Create a Publication](publish/create-a-publication.md)。</span><span class="sxs-lookup"><span data-stu-id="12de5-113">For more information, see [Create a Publication](publish/create-a-publication.md).</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="12de5-114">为了避免丢失订阅服务器数据，在将 **sp_addpublication** 与 `@allow_initialize_from_backup = N'true'`一起使用时，始终使用 `@immediate_sync = N'true'`。</span><span class="sxs-lookup"><span data-stu-id="12de5-114">To avoid missing subscriber data, when using **sp_addpublication** with `@allow_initialize_from_backup = N'true'`, always use `@immediate_sync = N'true'`.</span></span>  
  
3.  <span data-ttu-id="12de5-115">使用 [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) 语句创建发布数据库的备份。</span><span class="sxs-lookup"><span data-stu-id="12de5-115">Create a backup of the publication database using the [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) statement.</span></span>  
  
4.  <span data-ttu-id="12de5-116">使用 [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) 语句在订阅服务器上还原备份。</span><span class="sxs-lookup"><span data-stu-id="12de5-116">Restore the backup on the Subscriber using the [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) statement.</span></span>  
  
5.  <span data-ttu-id="12de5-117">在发布服务器上对发布数据库执行存储过程 [sp_addsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="12de5-117">At the Publisher on the publication database, execute the stored procedure [sp_addsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql).</span></span> <span data-ttu-id="12de5-118">指定下列参数：</span><span class="sxs-lookup"><span data-stu-id="12de5-118">Specify the following parameters:</span></span>  
  
    -   <span data-ttu-id="12de5-119">\*\* \@ sync_type\*\* -值为**initialize with backup**。</span><span class="sxs-lookup"><span data-stu-id="12de5-119">**\@sync_type** - a value of **initialize with backup**.</span></span>  
  
    -   <span data-ttu-id="12de5-120">\*\* \@ backupdevicetype\*\* -备份设备的类型： **logical** (默认) 、**磁盘**或**磁带**。</span><span class="sxs-lookup"><span data-stu-id="12de5-120">**\@backupdevicetype** - the type of backup device: **logical** (default), **disk**, or **tape**.</span></span>  
  
    -   <span data-ttu-id="12de5-121">\*\* \@ backupdevicename\*\* -用于还原的逻辑或物理备份设备。</span><span class="sxs-lookup"><span data-stu-id="12de5-121">**\@backupdevicename** - the logical or physical backup device to use for the restore.</span></span>  
  
         <span data-ttu-id="12de5-122">对于逻辑设备，指定使用 **sp_addumpdevice** 创建该设备时指定的备份设备的名称。</span><span class="sxs-lookup"><span data-stu-id="12de5-122">For a logical device, specify the name of the backup device specified when **sp_addumpdevice** was used to create the device.</span></span>  
  
         <span data-ttu-id="12de5-123">对于物理设备，指定完整的路径和文件名，比如 `DISK = 'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\BACKUP\Mybackup.dat'` 或 `TAPE = '\\.\TAPE0'`。</span><span class="sxs-lookup"><span data-stu-id="12de5-123">For a physical device, specify a complete path and file name, such as `DISK = 'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\BACKUP\Mybackup.dat'` or `TAPE = '\\.\TAPE0'`.</span></span>  
  
    -   <span data-ttu-id="12de5-124"> (可选)\ \** \@ 密\码\**-创建备份集时提供的密码。</span><span class="sxs-lookup"><span data-stu-id="12de5-124">(Optional) **\@password** - a password that was provided when the backup set was created.</span></span>  
  
    -   <span data-ttu-id="12de5-125"> (可选)\ \** \@ mediapasswor\d\** -在对介质集设置格式时提供的密码。</span><span class="sxs-lookup"><span data-stu-id="12de5-125">(Optional) **\@mediapassword** - a password that was provided when the media set was formatted.</span></span>  
  
    -   <span data-ttu-id="12de5-126"> (可选)\ \** \@ fileidhin\t\** -要还原的备份集的标识符。</span><span class="sxs-lookup"><span data-stu-id="12de5-126">(Optional) **\@fileidhint** - identifier for the backup set to be restored.</span></span> <span data-ttu-id="12de5-127">例如，指定为 **1** 表示备份介质中的第一个备份集，而指定为 **2** 则表示第二个备份集。</span><span class="sxs-lookup"><span data-stu-id="12de5-127">For example, specifying **1** indicates the first backup set on the backup medium and **2** indicates the second backup set.</span></span>  
  
    -   <span data-ttu-id="12de5-128"> (可选的：)\ \** \@ 卸载**磁带设备，如果在完成还原后应从驱动器卸载磁带，则将值指定为**\1\** (默认) ; 如果不应卸载磁带，则指定为**0** 。</span><span class="sxs-lookup"><span data-stu-id="12de5-128">(Optional for tape devices) **\@unload** - specify a value of **1** (default) if the tape should be unloaded from the drive after the restore is complete and **0** if it should not be unloaded.</span></span>  
  
6.  <span data-ttu-id="12de5-129">（可选）对于请求订阅，在订阅服务器上对订阅数据库执行 [sp_addpullsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql) 和 [sp_addpullsubscription_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="12de5-129">(Optional) For a pull subscription, execute [sp_addpullsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql) and [sp_addpullsubscription_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql) at the Subscriber on the subscription database.</span></span> <span data-ttu-id="12de5-130">有关详细信息，请参阅 [创建请求订阅](create-a-pull-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="12de5-130">For more information, see [Create a Pull Subscription](create-a-pull-subscription.md).</span></span>  
  
7.  <span data-ttu-id="12de5-131">（可选）启动分发代理。</span><span class="sxs-lookup"><span data-stu-id="12de5-131">(Optional) Start the Distribution Agent.</span></span> <span data-ttu-id="12de5-132">有关详细信息，请参阅 [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md) 或 [Synchronize a Push Subscription](synchronize-a-push-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="12de5-132">For more information, see [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md) or [Synchronize a Push Subscription](synchronize-a-push-subscription.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12de5-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="12de5-133">See Also</span></span>  
 <span data-ttu-id="12de5-134">[通过备份和还原来复制数据库](../databases/copy-databases-with-backup-and-restore.md) </span><span class="sxs-lookup"><span data-stu-id="12de5-134">[Copy Databases with Backup and Restore](../databases/copy-databases-with-backup-and-restore.md) </span></span>  
 [<span data-ttu-id="12de5-135">SQL Server 数据库的备份和还原</span><span class="sxs-lookup"><span data-stu-id="12de5-135">Back Up and Restore of SQL Server Databases</span></span>](../backup-restore/back-up-and-restore-of-sql-server-databases.md)  
  
  
