---
title: 删除备份设备 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- database backups [SQL Server], deleting devices
- backup devices [SQL Server], deleting
- deleting backup devices
- removing backup devices
- backing up databases [SQL Server], backup devices
ms.assetid: 7be62480-ed6a-4262-a071-1feba73b1c02
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e8734e587a8ecde315fb17120511455a59e38901
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581331"
---
# <a name="delete-a-backup-device-sql-server"></a><span data-ttu-id="88f15-102">删除备份设备 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="88f15-102">Delete a Backup Device (SQL Server)</span></span>
  <span data-ttu-id="88f15-103">本主题介绍了如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中删除备份设备。</span><span class="sxs-lookup"><span data-stu-id="88f15-103">This topic describes how to delete a backup device in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="88f15-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="88f15-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="88f15-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="88f15-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="88f15-106">安全性</span><span class="sxs-lookup"><span data-stu-id="88f15-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="88f15-107">**若要删除备份设备，请使用：**</span><span class="sxs-lookup"><span data-stu-id="88f15-107">**To delete a backup device, using:**</span></span>  
  
     [<span data-ttu-id="88f15-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="88f15-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="88f15-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="88f15-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="88f15-110">开始之前</span><span class="sxs-lookup"><span data-stu-id="88f15-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="88f15-111">Security</span><span class="sxs-lookup"><span data-stu-id="88f15-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="88f15-112">权限</span><span class="sxs-lookup"><span data-stu-id="88f15-112">Permissions</span></span>  
 <span data-ttu-id="88f15-113">要求具有 **diskadmin** 固定服务器角色中的成员身份。</span><span class="sxs-lookup"><span data-stu-id="88f15-113">Requires membership in the **diskadmin** fixed server role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="88f15-114">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="88f15-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-a-backup-device"></a><span data-ttu-id="88f15-115">删除备份设备</span><span class="sxs-lookup"><span data-stu-id="88f15-115">To delete a backup device</span></span>  
  
1.  <span data-ttu-id="88f15-116">连接到相应的 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]实例之后，在对象资源管理器中，单击服务器名称以展开服务器树。</span><span class="sxs-lookup"><span data-stu-id="88f15-116">After connecting to the appropriate instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="88f15-117">展开 **“服务器对象”** ，然后展开 **“备份设备”** 。</span><span class="sxs-lookup"><span data-stu-id="88f15-117">Expand **Server Objects**, and then expand **Backup Devices**.</span></span>  
  
3.  <span data-ttu-id="88f15-118">右键单击要删除的设备，然后单击“删除”  。</span><span class="sxs-lookup"><span data-stu-id="88f15-118">Right-click the device you want, and then click **Delete**.</span></span>  
  
4.  <span data-ttu-id="88f15-119">在 **“删除对象”** 对话框中，请验证 **“对象名称”** 列中显示正确的设备名称。</span><span class="sxs-lookup"><span data-stu-id="88f15-119">In the **Delete Object** dialog box, verify that the correct device name appears in the **Object Name** column.</span></span>  
  
5.  <span data-ttu-id="88f15-120">单击“确定”。 </span><span class="sxs-lookup"><span data-stu-id="88f15-120">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="88f15-121">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="88f15-121">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-a-backup-device"></a><span data-ttu-id="88f15-122">删除备份设备</span><span class="sxs-lookup"><span data-stu-id="88f15-122">To delete a backup device</span></span>  
  
1.  <span data-ttu-id="88f15-123">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="88f15-123">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="88f15-124">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="88f15-124">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="88f15-125">复制并将以下示例粘贴到查询中。</span><span class="sxs-lookup"><span data-stu-id="88f15-125">Copy and paste the following example into the query.</span></span> <span data-ttu-id="88f15-126">此示例演示如何使用 [sp_dropdevice](/sql/relational-databases/system-stored-procedures/sp-dropdevice-transact-sql) 删除备份设备。</span><span class="sxs-lookup"><span data-stu-id="88f15-126">This example shows how to use [sp_dropdevice](/sql/relational-databases/system-stored-procedures/sp-dropdevice-transact-sql) to delete a backup device.</span></span> <span data-ttu-id="88f15-127">执行第一个示例以创建 `mybackupdisk` 备份设备和物理名称 `c:\backup\backup1.bak`。</span><span class="sxs-lookup"><span data-stu-id="88f15-127">Execute the first example to create the `mybackupdisk` backup device and the physical name `c:\backup\backup1.bak`.</span></span> <span data-ttu-id="88f15-128">执行 `sp_dropdevice` 以便删除 `mybackupdisk` 备份设备。</span><span class="sxs-lookup"><span data-stu-id="88f15-128">Execute `sp_dropdevice` to delete the `mybackupdisk` backup device.</span></span> <span data-ttu-id="88f15-129">`delfile` 参数将删除物理名称。</span><span class="sxs-lookup"><span data-stu-id="88f15-129">The `delfile` parameter deletes the physical name.</span></span>  
  
```sql  
--Define a backup device and physical name.   
USE AdventureWorks2012 ;  
GO  
EXEC sp_addumpdevice 'disk', 'mybackupdisk', 'c:\backup\backup1.bak' ;  
GO  
--Delete the backup device and the physical name.  
USE AdventureWorks2012 ;  
GO  
EXEC sp_dropdevice ' mybackupdisk ', 'delfile' ;  
GO  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="88f15-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="88f15-130">See Also</span></span>  
 <span data-ttu-id="88f15-131">[查看逻辑备份设备的属性和内容 (SQL Server)](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="88f15-131">[View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md) </span></span>  
 <span data-ttu-id="88f15-132">[sys.backup_devices (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-backup-devices-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="88f15-132">[sys.backup_devices &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-backup-devices-transact-sql) </span></span>  
 <span data-ttu-id="88f15-133">[BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="88f15-133">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="88f15-134">[备份设备 (SQL Server)](backup-devices-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="88f15-134">[Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md) </span></span>  
 [<span data-ttu-id="88f15-135">sp_addumpdevice (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="88f15-135">sp_addumpdevice &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql)  
  
  
