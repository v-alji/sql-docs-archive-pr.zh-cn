---
title: 查看逻辑备份设备的属性和内容 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- displaying backup content
- viewing backup content
- database backups [SQL Server], viewing content
- backing up databases [SQL Server], viewing content
- backing up databases [SQL Server], properties
- displaying backup properties
- backup devices [SQL Server], viewing information
- viewing backup properties
- database backups [SQL Server], properties
ms.assetid: 3a309074-e816-454d-b6c3-fcfdde0cbf74
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f2bdf41e3dbda079e3627ff7a7c1c3c78103b728
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690656"
---
# <a name="view-the-properties-and-contents-of-a-logical-backup-device-sql-server"></a><span data-ttu-id="251e2-102">查看逻辑备份设备的属性和内容 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="251e2-102">View the Properties and Contents of a Logical Backup Device (SQL Server)</span></span>
  <span data-ttu-id="251e2-103">本主题介绍如何通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 查看 [!INCLUDE[tsql](../../includes/tsql-md.md)]中逻辑备份设备的属性和内容。</span><span class="sxs-lookup"><span data-stu-id="251e2-103">This topic describes how to view the properties and contents of a logical backup device in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="251e2-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="251e2-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="251e2-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="251e2-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="251e2-106">安全性</span><span class="sxs-lookup"><span data-stu-id="251e2-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="251e2-107">**若要查看逻辑备份设备的属性和内容，请使用：**</span><span class="sxs-lookup"><span data-stu-id="251e2-107">**To view the properties and contents of a logical backup device, using:**</span></span>  
  
     [<span data-ttu-id="251e2-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="251e2-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="251e2-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="251e2-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="251e2-110">开始之前</span><span class="sxs-lookup"><span data-stu-id="251e2-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="251e2-111">Security</span><span class="sxs-lookup"><span data-stu-id="251e2-111">Security</span></span>  
 <span data-ttu-id="251e2-112">有关安全性的信息，请参阅 [RESTORE LABELONLY (Transact SQL)](/sql/t-sql/statements/restore-statements-labelonly-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="251e2-112">For information about security, see [RESTORE LABELONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-labelonly-transact-sql).</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="251e2-113">权限</span><span class="sxs-lookup"><span data-stu-id="251e2-113">Permissions</span></span>  
 <span data-ttu-id="251e2-114">在 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 和更高版本中，获取有关备份集或备份设备的信息要求具有 CREATE DATABASE 权限。</span><span class="sxs-lookup"><span data-stu-id="251e2-114">In [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] and later versions, obtaining information about a backup set or backup device requires CREATE DATABASE permission.</span></span> <span data-ttu-id="251e2-115">有关详细信息，请参阅 [GRANT 数据库权限 (Transact-SQL)](/sql/t-sql/statements/grant-database-permissions-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="251e2-115">For more information, see [GRANT Database Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-database-permissions-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="251e2-116">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="251e2-116">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-the-properties-and-contents-of-a-logical-backup-device"></a><span data-ttu-id="251e2-117">查看逻辑备份设备的属性和内容</span><span class="sxs-lookup"><span data-stu-id="251e2-117">To view the properties and contents of a logical backup device</span></span>  
  
1.  <span data-ttu-id="251e2-118">连接到相应的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 实例之后，在“对象资源管理器”中，单击服务器名称以展开服务器树。</span><span class="sxs-lookup"><span data-stu-id="251e2-118">After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="251e2-119">展开 **“服务器对象”** ，然后展开 **“备份设备”** 。</span><span class="sxs-lookup"><span data-stu-id="251e2-119">Expand **Server Objects**, and expand **Backup Devices**.</span></span>  
  
3.  <span data-ttu-id="251e2-120">单击设备并右键单击“属性”  ，将打开“备份设备”  对话框。</span><span class="sxs-lookup"><span data-stu-id="251e2-120">Click the device and right-click **Properties**, which opens the **Backup Device** dialog box.</span></span>  
  
4.  <span data-ttu-id="251e2-121">**“常规”** 页将显示设备名称和目标，目标为磁带设备或者文件路径。</span><span class="sxs-lookup"><span data-stu-id="251e2-121">The **General** page displays the device name and destination, which is either a tape device or file path.</span></span>  
  
5.  <span data-ttu-id="251e2-122">在 **“选择页”** 窗格中，单击 **“介质内容”** 。</span><span class="sxs-lookup"><span data-stu-id="251e2-122">In the **Select a Page** pane, click **Media Contents**.</span></span>  
  
6.  <span data-ttu-id="251e2-123">以下属性面板中将显示右侧窗格：</span><span class="sxs-lookup"><span data-stu-id="251e2-123">The right-hand pane displays in the following properties panels:</span></span>  
  
    -   <span data-ttu-id="251e2-124">**介质**</span><span class="sxs-lookup"><span data-stu-id="251e2-124">**Media**</span></span>  
  
         <span data-ttu-id="251e2-125">介质顺序信息（介质序列号、簇序列号和镜像标识符（如果存在））以及介质的创建日期和时间。</span><span class="sxs-lookup"><span data-stu-id="251e2-125">Media sequence information (the media sequence number, the family sequence number, and the mirror identifier, if any) and the media creation date and time.</span></span>  
  
    -   <span data-ttu-id="251e2-126">**介质集**</span><span class="sxs-lookup"><span data-stu-id="251e2-126">**Media set**</span></span>  
  
         <span data-ttu-id="251e2-127">介质集信息：介质集名称和说明（如果有）以及介质集中的簇数。</span><span class="sxs-lookup"><span data-stu-id="251e2-127">Media set information: the media set name and description, if any, and the number of families in the media set.</span></span>  
  
7.  <span data-ttu-id="251e2-128">**“备份集”** 网格显示了有关介质集内容的信息。</span><span class="sxs-lookup"><span data-stu-id="251e2-128">The **Backup sets** grid displays information about the contents of the media set.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="251e2-129">有关详细信息，请参阅 [媒体内容页](backup-device-media-contents-page.md)。</span><span class="sxs-lookup"><span data-stu-id="251e2-129">For more information, see [Media Contents Page](backup-device-media-contents-page.md).</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="251e2-130">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="251e2-130">Using Transact-SQL</span></span>  
  
#### <a name="to-view-the-properties-and-contents-of-a-logical-backup-device"></a><span data-ttu-id="251e2-131">查看逻辑备份设备的属性和内容</span><span class="sxs-lookup"><span data-stu-id="251e2-131">To view the properties and contents of a logical backup device</span></span>  
  
1.  <span data-ttu-id="251e2-132">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="251e2-132">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="251e2-133">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="251e2-133">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="251e2-134">使用 [RESTORE LABELONLY](/sql/t-sql/statements/restore-statements-labelonly-transact-sql) 语句。</span><span class="sxs-lookup"><span data-stu-id="251e2-134">Use the [RESTORE LABELONLY](/sql/t-sql/statements/restore-statements-labelonly-transact-sql) statement.</span></span> <span data-ttu-id="251e2-135">此示例返回有关 `AdvWrks2008R2Backup` 逻辑备份设备的信息。</span><span class="sxs-lookup"><span data-stu-id="251e2-135">This example returns information about the `AdvWrks2008R2Backup` logical backup device.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
RESTORE LABELONLY  
   FROM AdvWrks2008R2Backup ;  
GO  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="251e2-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="251e2-136">See Also</span></span>  
 <span data-ttu-id="251e2-137">[backupfilegroup (Transact-SQL)](/sql/relational-databases/system-tables/backupfilegroup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="251e2-137">[backupfilegroup &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupfilegroup-transact-sql) </span></span>  
 <span data-ttu-id="251e2-138">[backupfile (Transact-SQL)](/sql/relational-databases/system-tables/backupfile-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="251e2-138">[backupfile &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupfile-transact-sql) </span></span>  
 <span data-ttu-id="251e2-139">[backupset (Transact-SQL)](/sql/relational-databases/system-tables/backupset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="251e2-139">[backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql) </span></span>  
 <span data-ttu-id="251e2-140">[backupmediaset (Transact-SQL)](/sql/relational-databases/system-tables/backupmediaset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="251e2-140">[backupmediaset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupmediaset-transact-sql) </span></span>  
 <span data-ttu-id="251e2-141">[backupmediafamily (Transact-SQL)](/sql/relational-databases/system-tables/backupmediafamily-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="251e2-141">[backupmediafamily &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupmediafamily-transact-sql) </span></span>  
 <span data-ttu-id="251e2-142">[sp_addumpdevice (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="251e2-142">[sp_addumpdevice &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) </span></span>  
 [<span data-ttu-id="251e2-143">备份设备 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="251e2-143">Backup Devices &#40;SQL Server&#41;</span></span>](backup-devices-sql-server.md)  
  
  
