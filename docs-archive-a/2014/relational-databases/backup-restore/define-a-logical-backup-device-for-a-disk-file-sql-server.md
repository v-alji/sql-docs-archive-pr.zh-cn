---
title: 为磁盘文件定义逻辑备份设备 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backup devices [SQL Server], defining
- backup devices [SQL Server], disks
- disk backup devices [SQL Server]
- database backups [SQL Server], disks
- backing up databases [SQL Server], disks
ms.assetid: 86331d43-c738-4523-ae3d-7d6700348ed1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8aa92296da81f984f260deace887c15f13443b95
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694008"
---
# <a name="define-a-logical-backup-device-for-a-disk-file-sql-server"></a><span data-ttu-id="0e695-102">为磁盘文件定义逻辑备份设备 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0e695-102">Define a Logical Backup Device for a Disk File (SQL Server)</span></span>
  <span data-ttu-id="0e695-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中为磁盘文件定义逻辑备份设备。</span><span class="sxs-lookup"><span data-stu-id="0e695-103">This topic describes how to define a logical backup device for a disk file in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="0e695-104">逻辑设备是指向特定物理备份设备（磁盘文件或磁带机）的用户定义名称。</span><span class="sxs-lookup"><span data-stu-id="0e695-104">A logical device is a user-defined name that points to a specific physical backup device (a disk file or tape drive).</span></span>  <span data-ttu-id="0e695-105">将备份写入备份设备后，便会初始化物理设备。</span><span class="sxs-lookup"><span data-stu-id="0e695-105">The initialization of the physical device occurs later, when a backup is written to the backup device.</span></span>  
  
 <span data-ttu-id="0e695-106">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="0e695-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="0e695-107">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="0e695-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="0e695-108">限制和局限</span><span class="sxs-lookup"><span data-stu-id="0e695-108">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="0e695-109">建议</span><span class="sxs-lookup"><span data-stu-id="0e695-109">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="0e695-110">安全性</span><span class="sxs-lookup"><span data-stu-id="0e695-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="0e695-111">**若要为磁盘文件定义逻辑备份设备，请使用：**</span><span class="sxs-lookup"><span data-stu-id="0e695-111">**To define a logical backup device for a disk file, using:**</span></span>  
  
     [<span data-ttu-id="0e695-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0e695-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="0e695-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="0e695-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="0e695-114">开始之前</span><span class="sxs-lookup"><span data-stu-id="0e695-114">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="0e695-115">限制和局限</span><span class="sxs-lookup"><span data-stu-id="0e695-115">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="0e695-116">逻辑设备名称在服务器实例上的所有逻辑备份设备中必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="0e695-116">The logical device name must be unique among all the logical backup devices on the server instance.</span></span> <span data-ttu-id="0e695-117">若要查看现有逻辑设备名称，请查询 [sys.backup_devices](/sql/relational-databases/system-catalog-views/sys-backup-devices-transact-sql) 目录视图。</span><span class="sxs-lookup"><span data-stu-id="0e695-117">To view the existing logical device names, query the [sys.backup_devices](/sql/relational-databases/system-catalog-views/sys-backup-devices-transact-sql) catalog view.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="0e695-118">建议</span><span class="sxs-lookup"><span data-stu-id="0e695-118">Recommendations</span></span>  
  
-   <span data-ttu-id="0e695-119">我们建议备份磁盘应不同于数据库数据和日志的磁盘。</span><span class="sxs-lookup"><span data-stu-id="0e695-119">We recommend that a backup disk be a different disk than the database data and log disks.</span></span> <span data-ttu-id="0e695-120">这是数据或日志磁盘出现故障时访问备份数据必不可少的。</span><span class="sxs-lookup"><span data-stu-id="0e695-120">This is necessary to make sure that you can access the backups if the data or log disk fails.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="0e695-121">Security</span><span class="sxs-lookup"><span data-stu-id="0e695-121">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="0e695-122">权限</span><span class="sxs-lookup"><span data-stu-id="0e695-122">Permissions</span></span>  
 <span data-ttu-id="0e695-123">要求具有 **diskadmin** 固定服务器角色中的成员身份。</span><span class="sxs-lookup"><span data-stu-id="0e695-123">Requires membership in the **diskadmin** fixed server role.</span></span>  
  
 <span data-ttu-id="0e695-124">要求拥有写入磁盘的权限。</span><span class="sxs-lookup"><span data-stu-id="0e695-124">Requires permission to write to the disk.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="0e695-125">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0e695-125">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-define-a-logical-backup-device-for-a-disk-file"></a><span data-ttu-id="0e695-126">为磁盘文件定义逻辑备份设备</span><span class="sxs-lookup"><span data-stu-id="0e695-126">To define a logical backup device for a disk file</span></span>  
  
1.  <span data-ttu-id="0e695-127">连接到相应的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 实例之后，在“对象资源管理器”中，单击服务器名称以展开服务器树。</span><span class="sxs-lookup"><span data-stu-id="0e695-127">After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="0e695-128">展开“服务器对象”  ，然后右键单击“备份设备”  。</span><span class="sxs-lookup"><span data-stu-id="0e695-128">Expand **Server Objects**, and right-click **Backup Devices**.</span></span>  
  
3.  <span data-ttu-id="0e695-129">单击 **“新建备份设备”** 。</span><span class="sxs-lookup"><span data-stu-id="0e695-129">Click **New Backup Device**.</span></span> <span data-ttu-id="0e695-130">将打开 **“备份设备”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="0e695-130">The **Backup Device** dialog box opens.</span></span>  
  
4.  <span data-ttu-id="0e695-131">输入设备名称。</span><span class="sxs-lookup"><span data-stu-id="0e695-131">Enter a device name.</span></span>  
  
5.  <span data-ttu-id="0e695-132">若要确定目标位置，请单击 **“文件”** 并指定该文件的完整路径。</span><span class="sxs-lookup"><span data-stu-id="0e695-132">For the destination, click **File** and specify the full path of the file.</span></span>  
  
6.  <span data-ttu-id="0e695-133">若要定义新设备，请单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="0e695-133">To define the new device, click **OK**.</span></span>  
  
 <span data-ttu-id="0e695-134">若要备份至此新设备，请将该设备添加到“备份数据库”  （“常规”  ）对话框中的“备份到：”  字段。</span><span class="sxs-lookup"><span data-stu-id="0e695-134">To back up to this new device, add it to the **Back up to:** field in the **Back up Database** (**General**) dialog box.</span></span> <span data-ttu-id="0e695-135">有关详细信息，请参阅 [创建完整数据库备份 (SQL Server)](create-a-full-database-backup-sql-server.md)中创建差异数据库备份。</span><span class="sxs-lookup"><span data-stu-id="0e695-135">For more information, see [Create a Full Database Backup &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md).</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="0e695-136">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="0e695-136">Using Transact-SQL</span></span>  
  
#### <a name="to-define-a-logical-backup-for-a-disk-file"></a><span data-ttu-id="0e695-137">为磁盘文件定义逻辑备份</span><span class="sxs-lookup"><span data-stu-id="0e695-137">To define a logical backup for a disk file</span></span>  
  
1.  <span data-ttu-id="0e695-138">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0e695-138">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="0e695-139">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="0e695-139">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="0e695-140">将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。</span><span class="sxs-lookup"><span data-stu-id="0e695-140">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="0e695-141">此示例说明如何使用 [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) 为磁盘文件定义逻辑备份设备。</span><span class="sxs-lookup"><span data-stu-id="0e695-141">This example shows how to use [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) to define a logical backup device for a disk file.</span></span> <span data-ttu-id="0e695-142">下面的示例以物理名称 `mydiskdump`添加名为 `c:\dump\dump1.bak`的磁盘备份设备。</span><span class="sxs-lookup"><span data-stu-id="0e695-142">The example adds the disk backup device named `mydiskdump`, with the physical name `c:\dump\dump1.bak`.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_addumpdevice 'disk', 'mydiskdump', 'c:\dump\dump1.bak' ;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="0e695-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0e695-143">See Also</span></span>  
 <span data-ttu-id="0e695-144">[BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0e695-144">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="0e695-145">[备份设备 (SQL Server)](backup-devices-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="0e695-145">[Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md) </span></span>  
 <span data-ttu-id="0e695-146">[sys.backup_devices (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-backup-devices-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0e695-146">[sys.backup_devices &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-backup-devices-transact-sql) </span></span>  
 <span data-ttu-id="0e695-147">[sp_addumpdevice (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0e695-147">[sp_addumpdevice &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) </span></span>  
 <span data-ttu-id="0e695-148">[sp_dropdevice (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-dropdevice-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0e695-148">[sp_dropdevice &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropdevice-transact-sql) </span></span>  
 <span data-ttu-id="0e695-149">[为磁带驱动器定义逻辑备份设备 (SQL Server)](define-a-logical-backup-device-for-a-tape-drive-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="0e695-149">[Define a Logical Backup Device for a Tape Drive &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-tape-drive-sql-server.md) </span></span>  
 [<span data-ttu-id="0e695-150">查看逻辑备份设备的属性和内容 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0e695-150">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
  
