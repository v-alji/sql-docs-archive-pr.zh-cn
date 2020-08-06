---
title: 为磁带机定义逻辑备份设备 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backup devices [SQL Server], defining
- backup devices [SQL Server], tapes
- backing up databases [SQL Server], tapes
- database backups [SQL Server], tapes
- tape backup devices, creating
ms.assetid: 66f36e1d-0287-4fac-8a51-71f9f0d7ad5b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8728df2cc0b5907e51da84ed9e77d897a1718d36
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694005"
---
# <a name="define-a-logical-backup-device-for-a-tape-drive-sql-server"></a><span data-ttu-id="ba824-102">为磁带机定义逻辑备份设备 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ba824-102">Define a Logical Backup Device for a Tape Drive (SQL Server)</span></span>
  <span data-ttu-id="ba824-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中为磁带机定义逻辑备份设备。</span><span class="sxs-lookup"><span data-stu-id="ba824-103">This topic describes how to define a logical backup device for a tape drive in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="ba824-104">逻辑设备是指向特定物理备份设备（磁盘文件或磁带机）的用户定义名称。</span><span class="sxs-lookup"><span data-stu-id="ba824-104">A logical device is a user-defined name that points to a specific physical backup device (a disk file or tape drive).</span></span>  <span data-ttu-id="ba824-105">将备份写入备份设备后，便会初始化物理设备。</span><span class="sxs-lookup"><span data-stu-id="ba824-105">The initialization of the physical device occurs later, when a backup is written to the backup device.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ba824-106">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的未来版本中将不再支持磁带备份设备。</span><span class="sxs-lookup"><span data-stu-id="ba824-106">Support for tape backup devices will be removed in a future version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="ba824-107">请避免在新的开发工作中使用该功能，并着手修改当前还在使用该功能的应用程序。</span><span class="sxs-lookup"><span data-stu-id="ba824-107">Avoid using this feature in new development work, and plan to modify applications that currently use this feature.</span></span>  
  
 <span data-ttu-id="ba824-108">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="ba824-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="ba824-109">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="ba824-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="ba824-110">限制和局限</span><span class="sxs-lookup"><span data-stu-id="ba824-110">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="ba824-111">安全性</span><span class="sxs-lookup"><span data-stu-id="ba824-111">Security</span></span>](#Security)  
  
-   <span data-ttu-id="ba824-112">**若要为磁带机定义逻辑备份设备，请使用：**</span><span class="sxs-lookup"><span data-stu-id="ba824-112">**To define a logical backup device for a tape drive, using:**</span></span>  
  
     [<span data-ttu-id="ba824-113">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ba824-113">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="ba824-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ba824-114">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ba824-115">开始之前</span><span class="sxs-lookup"><span data-stu-id="ba824-115">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="ba824-116">限制和局限</span><span class="sxs-lookup"><span data-stu-id="ba824-116">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="ba824-117">Microsoft Windows 操作系统必须支持磁带机。</span><span class="sxs-lookup"><span data-stu-id="ba824-117">The tape drive or drives must be supported by the Microsoft Windows operating system.</span></span>  
  
-   <span data-ttu-id="ba824-118">磁带设备必须物理连接到运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例的计算机上。</span><span class="sxs-lookup"><span data-stu-id="ba824-118">The tape device must be connected physically to the computer that is running an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="ba824-119">不支持备份到远程磁带设备上。</span><span class="sxs-lookup"><span data-stu-id="ba824-119">Backing up to remote tape devices is not supported.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ba824-120">Security</span><span class="sxs-lookup"><span data-stu-id="ba824-120">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ba824-121">权限</span><span class="sxs-lookup"><span data-stu-id="ba824-121">Permissions</span></span>  
 <span data-ttu-id="ba824-122">要求具有 **diskadmin** 固定服务器角色中的成员身份。</span><span class="sxs-lookup"><span data-stu-id="ba824-122">Requires membership in the **diskadmin** fixed server role.</span></span>  
  
 <span data-ttu-id="ba824-123">要求拥有写入磁盘的权限。</span><span class="sxs-lookup"><span data-stu-id="ba824-123">Requires permission to write to the disk.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="ba824-124">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ba824-124">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-define-a-logical-backup-device-for-a-tape-drive"></a><span data-ttu-id="ba824-125">为磁带机定义逻辑备份设备</span><span class="sxs-lookup"><span data-stu-id="ba824-125">To define a logical backup device for a tape drive</span></span>  
  
1.  <span data-ttu-id="ba824-126">连接到相应的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 实例之后，在“对象资源管理器”中，单击服务器名称以展开服务器树。</span><span class="sxs-lookup"><span data-stu-id="ba824-126">After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="ba824-127">展开“服务器对象”  ，然后右键单击“备份设备”  。</span><span class="sxs-lookup"><span data-stu-id="ba824-127">Expand **Server Objects**, and then right-click **Backup Devices**.</span></span>  
  
3.  <span data-ttu-id="ba824-128">单击 **“新建备份设备”** 打开 **“备份设备”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="ba824-128">Click **New Backup Device**, which opens the **Backup Device** dialog box.</span></span>  
  
4.  <span data-ttu-id="ba824-129">输入设备名称。</span><span class="sxs-lookup"><span data-stu-id="ba824-129">Enter a device name.</span></span>  
  
5.  <span data-ttu-id="ba824-130">为了确定要使用的备份设备，请单击 **“磁带”** ，然后选择一个未与其他备份设备相关联的磁带设备。</span><span class="sxs-lookup"><span data-stu-id="ba824-130">For the destination, click **Tape** and select a tape drive that is not already associated with another backup device.</span></span> <span data-ttu-id="ba824-131">如果没有这种磁带机，则 **“磁带”** 选项处于非活动状态。</span><span class="sxs-lookup"><span data-stu-id="ba824-131">If no such tape drives are available, the **Tape** option is inactive.</span></span>  
  
6.  <span data-ttu-id="ba824-132">若要定义新设备，请单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="ba824-132">To define the new device, click **OK**.</span></span>  
  
 <span data-ttu-id="ba824-133">若要备份至此新设备，请将该设备添加到“备份数据库”  （“常规”  ）对话框中的“备份到：”  字段。</span><span class="sxs-lookup"><span data-stu-id="ba824-133">To back up to this new device, add it to the **Back up to:** field in the **Back up Database** (**General**) dialog box.</span></span> <span data-ttu-id="ba824-134">有关详细信息，请参阅 [创建完整数据库备份 (SQL Server)](create-a-full-database-backup-sql-server.md)中创建差异数据库备份。</span><span class="sxs-lookup"><span data-stu-id="ba824-134">For more information, see [Create a Full Database Backup &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md).</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="ba824-135">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ba824-135">Using Transact-SQL</span></span>  
  
#### <a name="to-define-a-logical-backup-device-for-a-tape-drive"></a><span data-ttu-id="ba824-136">为磁带机定义逻辑备份设备</span><span class="sxs-lookup"><span data-stu-id="ba824-136">To define a logical backup device for a tape drive</span></span>  
  
1.  <span data-ttu-id="ba824-137">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ba824-137">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="ba824-138">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="ba824-138">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="ba824-139">将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。</span><span class="sxs-lookup"><span data-stu-id="ba824-139">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="ba824-140">此示例说明如何使用 [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) 为磁带定义逻辑备份设备。</span><span class="sxs-lookup"><span data-stu-id="ba824-140">This example shows how to use [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) to define a logical backup device for a tape.</span></span> <span data-ttu-id="ba824-141">下面的示例以物理名称 `tapedump1`添加名为 `\\.\tape0`的磁带备份设备。</span><span class="sxs-lookup"><span data-stu-id="ba824-141">The example adds the tape backup device named `tapedump1`, with the physical name `\\.\tape0`.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_addumpdevice 'tape', 'tapedump1', '\\.\tape0' ;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="ba824-142">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ba824-142">See Also</span></span>  
 <span data-ttu-id="ba824-143">[BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ba824-143">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="ba824-144">[sys.backup_devices (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-backup-devices-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ba824-144">[sys.backup_devices &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-backup-devices-transact-sql) </span></span>  
 <span data-ttu-id="ba824-145">[sp_addumpdevice (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ba824-145">[sp_addumpdevice &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) </span></span>  
 <span data-ttu-id="ba824-146">[sp_dropdevice (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-dropdevice-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ba824-146">[sp_dropdevice &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropdevice-transact-sql) </span></span>  
 <span data-ttu-id="ba824-147">[备份设备 (SQL Server)](backup-devices-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ba824-147">[Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md) </span></span>  
 <span data-ttu-id="ba824-148">[为磁盘文件定义逻辑备份设备 (SQL Server)](define-a-logical-backup-device-for-a-disk-file-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ba824-148">[Define a Logical Backup Device for a Disk File &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-disk-file-sql-server.md) </span></span>  
 [<span data-ttu-id="ba824-149">查看逻辑备份设备的属性和内容 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ba824-149">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
  
