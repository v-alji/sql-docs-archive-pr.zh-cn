---
title: 查看备份磁带或文件的内容 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backup devices [SQL Server], tapes
- displaying backup content
- viewing backup content
- tape backup devices, viewing contents
- database backups [SQL Server], viewing content
- backing up databases [SQL Server], viewing content
ms.assetid: cd6674a2-ca55-4b5a-a971-878ba001821e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 044519b64d41fbbdfc9302ce24369ab282727f67
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690663"
---
# <a name="view-the-contents-of-a-backup-tape-or-file-sql-server"></a><span data-ttu-id="20d7c-102">查看备份磁带或文件的内容 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="20d7c-102">View the Contents of a Backup Tape or File (SQL Server)</span></span>
  <span data-ttu-id="20d7c-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中查看备份磁带或文件的内容。</span><span class="sxs-lookup"><span data-stu-id="20d7c-103">This topic describes how to view the content of a backup tape or file in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="20d7c-104">在 SQL Server 的未来版本中将不再支持磁带备份设备。</span><span class="sxs-lookup"><span data-stu-id="20d7c-104">Support for tape backup devices will be removed in a future version of SQL Server.</span></span> <span data-ttu-id="20d7c-105">请避免在新的开发工作中使用该功能，并着手修改当前还在使用该功能的应用程序。</span><span class="sxs-lookup"><span data-stu-id="20d7c-105">Avoid using this feature in new development work, and plan to modify applications that currently use this feature.</span></span>  
  
 <span data-ttu-id="20d7c-106">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="20d7c-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="20d7c-107">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="20d7c-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="20d7c-108">安全性</span><span class="sxs-lookup"><span data-stu-id="20d7c-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="20d7c-109">**若要查看备份磁带或文件的内容，可使用：**</span><span class="sxs-lookup"><span data-stu-id="20d7c-109">**To view the content of a backup tape or file, using:**</span></span>  
  
     [<span data-ttu-id="20d7c-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="20d7c-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="20d7c-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="20d7c-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="20d7c-112">开始之前</span><span class="sxs-lookup"><span data-stu-id="20d7c-112">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="20d7c-113">Security</span><span class="sxs-lookup"><span data-stu-id="20d7c-113">Security</span></span>  
 <span data-ttu-id="20d7c-114">有关安全性的信息，请参阅 [RESTORE HEADERONLY (Transact SQL)](/sql/t-sql/statements/restore-statements-headeronly-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="20d7c-114">For information about security, see [RESTORE HEADERONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-headeronly-transact-sql).</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="20d7c-115">权限</span><span class="sxs-lookup"><span data-stu-id="20d7c-115">Permissions</span></span>  
 <span data-ttu-id="20d7c-116">在 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 和更高版本中，获取有关备份集或备份设备的信息要求具有 CREATE DATABASE 权限。</span><span class="sxs-lookup"><span data-stu-id="20d7c-116">In [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] and later versions, obtaining information about a backup set or backup device requires CREATE DATABASE permission.</span></span> <span data-ttu-id="20d7c-117">有关详细信息，请参阅 [GRANT 数据库权限 (Transact-SQL)](/sql/t-sql/statements/grant-database-permissions-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="20d7c-117">For more information, see [GRANT Database Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-database-permissions-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="20d7c-118">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="20d7c-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-the-content-of-a-backup-tape-or-file"></a><span data-ttu-id="20d7c-119">查看备份磁带或文件的内容</span><span class="sxs-lookup"><span data-stu-id="20d7c-119">To view the content of a backup tape or file</span></span>  
  
1.  <span data-ttu-id="20d7c-120">连接到相应的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 实例之后，在“对象资源管理器”中，单击服务器名称以展开服务器树。</span><span class="sxs-lookup"><span data-stu-id="20d7c-120">After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="20d7c-121">展开 **“数据库”** ，然后根据数据库的不同，选择用户数据库，或展开 **“系统数据库”** ，再选择系统数据库。</span><span class="sxs-lookup"><span data-stu-id="20d7c-121">Expand **Databases**, and, depending on the database, either select a user database or expand **System Databases** and select a system database.</span></span>  
  
3.  <span data-ttu-id="20d7c-122">右键单击要备的数据库，指向  “任务”，再单击  “备份”。</span><span class="sxs-lookup"><span data-stu-id="20d7c-122">Right-click the database you want to backup, point to **Tasks**, and then click **Back Up**.</span></span> <span data-ttu-id="20d7c-123">将出现 **“备份数据库”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="20d7c-123">The **Back Up Database** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="20d7c-124">在 **“常规”** 页的 **“目标”** 部分中，单击 **“磁盘”** 或 **“磁带”** 。</span><span class="sxs-lookup"><span data-stu-id="20d7c-124">In the **Destination** section of the **General** page, click either **Disk** or **Tape**.</span></span> <span data-ttu-id="20d7c-125">在 **“备份到”** 列表框中，查找所需的磁盘文件或磁带。</span><span class="sxs-lookup"><span data-stu-id="20d7c-125">In the **Back up to** list box, look for the disk file or tape you want.</span></span>  
  
     <span data-ttu-id="20d7c-126">如果磁盘文件或磁带未显示在列表框中，请单击  “添加”。</span><span class="sxs-lookup"><span data-stu-id="20d7c-126">If the disk file or tape is not displayed in the list-box, click **Add**.</span></span> <span data-ttu-id="20d7c-127">选择一个文件名或磁带机。</span><span class="sxs-lookup"><span data-stu-id="20d7c-127">Select a file name or tape drive.</span></span> <span data-ttu-id="20d7c-128">若要将其添加到  “备份到”列表框，请单击  “确定”。</span><span class="sxs-lookup"><span data-stu-id="20d7c-128">To add it to the **Back up to** list-box, click **OK**.</span></span>  
  
5.  <span data-ttu-id="20d7c-129">在  “备份到”列表框中，选择要查看的磁盘或磁带机的路径，再单击  “内容”。</span><span class="sxs-lookup"><span data-stu-id="20d7c-129">In the **Back up to** list-box, select the path of the disk or tape drive you want to view, and click **Contents**.</span></span> <span data-ttu-id="20d7c-130">将打开 **“设备内容”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="20d7c-130">This opens the **Device Contents** dialog box.</span></span>  
  
6.  <span data-ttu-id="20d7c-131">右侧窗格显示有关所选磁带或文件上的介质集和备份集的信息。</span><span class="sxs-lookup"><span data-stu-id="20d7c-131">The right-hand pane displays information about the media set and backup sets on the selected tape or file.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="20d7c-132">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="20d7c-132">Using Transact-SQL</span></span>  
  
#### <a name="to-view-the-content-of-a-backup-tape-or-file"></a><span data-ttu-id="20d7c-133">查看备份磁带或文件的内容</span><span class="sxs-lookup"><span data-stu-id="20d7c-133">To view the content of a backup tape or file</span></span>  
  
1.  <span data-ttu-id="20d7c-134">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="20d7c-134">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="20d7c-135">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="20d7c-135">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="20d7c-136">使用 [RESTORE HEADERONLY](/sql/t-sql/statements/restore-statements-headeronly-transact-sql) 语句。</span><span class="sxs-lookup"><span data-stu-id="20d7c-136">Use the [RESTORE HEADERONLY](/sql/t-sql/statements/restore-statements-headeronly-transact-sql) statement.</span></span> <span data-ttu-id="20d7c-137">此示例将返回有关名为 `AdventureWorks2012-FullBackup.bak`的文件的信息。</span><span class="sxs-lookup"><span data-stu-id="20d7c-137">This example returns information about the file named `AdventureWorks2012-FullBackup.bak`.</span></span>  
  
```sql  
USE AdventureWorks2012;  
RESTORE HEADERONLY   
FROM DISK = N'C:\AdventureWorks2012-FullBackup.bak' ;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="20d7c-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="20d7c-138">See Also</span></span>  
 <span data-ttu-id="20d7c-139">[backupfilegroup (Transact-SQL)](/sql/relational-databases/system-tables/backupfilegroup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="20d7c-139">[backupfilegroup &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupfilegroup-transact-sql) </span></span>  
 <span data-ttu-id="20d7c-140">[backupfile (Transact-SQL)](/sql/relational-databases/system-tables/backupfile-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="20d7c-140">[backupfile &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupfile-transact-sql) </span></span>  
 <span data-ttu-id="20d7c-141">[backupset (Transact-SQL)](/sql/relational-databases/system-tables/backupset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="20d7c-141">[backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql) </span></span>  
 <span data-ttu-id="20d7c-142">[backupmediaset (Transact-SQL)](/sql/relational-databases/system-tables/backupmediaset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="20d7c-142">[backupmediaset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupmediaset-transact-sql) </span></span>  
 <span data-ttu-id="20d7c-143">[backupmediafamily (Transact-SQL)](/sql/relational-databases/system-tables/backupmediafamily-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="20d7c-143">[backupmediafamily &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupmediafamily-transact-sql) </span></span>  
 <span data-ttu-id="20d7c-144">[备份设备 (SQL Server)](backup-devices-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="20d7c-144">[Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md) </span></span>  
 <span data-ttu-id="20d7c-145">[为磁盘文件定义逻辑备份设备 (SQL Server)](define-a-logical-backup-device-for-a-disk-file-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="20d7c-145">[Define a Logical Backup Device for a Disk File &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-disk-file-sql-server.md) </span></span>  
 [<span data-ttu-id="20d7c-146">为磁带驱动器定义逻辑备份设备 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="20d7c-146">Define a Logical Backup Device for a Tape Drive &#40;SQL Server&#41;</span></span>](define-a-logical-backup-device-for-a-tape-drive-sql-server.md)  
  
  
