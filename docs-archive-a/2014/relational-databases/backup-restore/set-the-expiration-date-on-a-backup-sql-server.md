---
title: 设置备份的到期日期 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backing up databases [SQL Server], expiration dates
- expiration [SQL Server]
- database backups [SQL Server], expiration dates
ms.assetid: 76e814df-6487-4893-9f09-7759f1863a5c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 9185222df93e0a1150256535526ba910c593cf6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580303"
---
# <a name="set-the-expiration-date-on-a-backup-sql-server"></a><span data-ttu-id="7df9a-102">设置备份的过期日期 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="7df9a-102">Set the Expiration Date on a Backup (SQL Server)</span></span>
  <span data-ttu-id="7df9a-103">本主题介绍如何通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中设置备份的过期日期。</span><span class="sxs-lookup"><span data-stu-id="7df9a-103">This topic describes how to set the expiration date on a backup in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="7df9a-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="7df9a-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="7df9a-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="7df9a-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="7df9a-106">安全性</span><span class="sxs-lookup"><span data-stu-id="7df9a-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="7df9a-107">**若要设置备份的过期日期，请使用**</span><span class="sxs-lookup"><span data-stu-id="7df9a-107">**To set the expiration date on a backup, using:**</span></span>  
  
     [<span data-ttu-id="7df9a-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="7df9a-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="7df9a-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="7df9a-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="7df9a-110">开始之前</span><span class="sxs-lookup"><span data-stu-id="7df9a-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="7df9a-111">Security</span><span class="sxs-lookup"><span data-stu-id="7df9a-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="7df9a-112">权限</span><span class="sxs-lookup"><span data-stu-id="7df9a-112">Permissions</span></span>  
 <span data-ttu-id="7df9a-113">默认情况下，为 **sysadmin** 固定服务器角色以及 **db_owner** 和 **db_backupoperator** 固定数据库角色的成员授予 BACKUP DATABASE 和 BACKUP LOG 权限。</span><span class="sxs-lookup"><span data-stu-id="7df9a-113">BACKUP DATABASE and BACKUP LOG permissions default to members of the **sysadmin** fixed server role and the **db_owner** and **db_backupoperator** fixed database roles.</span></span>  
  
 <span data-ttu-id="7df9a-114">备份设备的物理文件的所有权和权限问题可能会妨碍备份操作。</span><span class="sxs-lookup"><span data-stu-id="7df9a-114">Ownership and permission problems on the backup device's physical file can interfere with a backup operation.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="7df9a-115">必须能够读取和写入设备；运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务的帐户必须具有写入权限。</span><span class="sxs-lookup"><span data-stu-id="7df9a-115">must be able to read and write to the device; the account under which the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service runs must have write permissions.</span></span> <span data-ttu-id="7df9a-116">但是，用于在系统表中为备份设备添加项目的 [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql)不检查文件访问权限。</span><span class="sxs-lookup"><span data-stu-id="7df9a-116">However, [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql), which adds an entry for a backup device in the system tables, does not check file access permissions.</span></span> <span data-ttu-id="7df9a-117">备份设备物理文件的这些问题可能直到为备份或还原而访问物理资源时才会出现。</span><span class="sxs-lookup"><span data-stu-id="7df9a-117">Such problems on the backup device's physical file may not appear until the physical resource is accessed when the backup or restore is attempted.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="7df9a-118">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="7df9a-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-set-the-expiration-date-on-a-backup"></a><span data-ttu-id="7df9a-119">设置备份的过期日期</span><span class="sxs-lookup"><span data-stu-id="7df9a-119">To set the expiration date on a backup</span></span>  
  
1.  <span data-ttu-id="7df9a-120">连接到相应的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)] 实例之后，在“对象资源管理器”中，单击服务器名称以展开服务器树。</span><span class="sxs-lookup"><span data-stu-id="7df9a-120">After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="7df9a-121">展开 **“数据库”** ，然后根据数据库的不同，选择用户数据库，或展开 **“系统数据库”** ，再选择系统数据库。</span><span class="sxs-lookup"><span data-stu-id="7df9a-121">Expand **Databases**, and, depending on the database, either select a user database or expand **System Databases** and select a system database.</span></span>  
  
3.  <span data-ttu-id="7df9a-122">右键单击数据库，指向 **“任务”** ，再单击 **“备份”** 。</span><span class="sxs-lookup"><span data-stu-id="7df9a-122">Right-click the database, point to **Tasks**, and then click **Back Up**.</span></span> <span data-ttu-id="7df9a-123">将出现 **“备份数据库”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="7df9a-123">The **Back Up Database** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="7df9a-124">在 **“常规”** 页上，为 **“备份集过期时间”** 指定一个过期日期以指明其他备份可以覆盖该备份集的时间：</span><span class="sxs-lookup"><span data-stu-id="7df9a-124">On the **General** page, for **Backup set will expire**, specify an expiration date to indicate when the backup set can be overwritten by another backup:</span></span>  
  
    -   <span data-ttu-id="7df9a-125">若要使备份集在特定天数后过期，请单击 **“之后”** （默认选项），并输入备份集从创建到过期所需的天数。</span><span class="sxs-lookup"><span data-stu-id="7df9a-125">To have the backup set expire after a specific number of days, click **After** (the default option), and enter the number of days after set creation that the set will expire.</span></span> <span data-ttu-id="7df9a-126">此值范围为 0 到 99999 天；0 天表示备份集将永不过期。</span><span class="sxs-lookup"><span data-stu-id="7df9a-126">This value can be from 0 to 99999 days; a value of 0 days means that the backup set will never expire.</span></span>  
  
         <span data-ttu-id="7df9a-127">默认值在 **“服务器属性”** 对话框（位于 **“数据库设置”** 页上）的 **“默认备份媒体保持期(天)”** 选项中设置。</span><span class="sxs-lookup"><span data-stu-id="7df9a-127">The default value is set in the **Default backup media retention (in days)** option of the **Server Properties** dialog box (**Database Settings** page).</span></span> <span data-ttu-id="7df9a-128">若要访问它，请在对象资源管理器中右键单击服务器名称，选择属性，再选择“数据库设置”  页。</span><span class="sxs-lookup"><span data-stu-id="7df9a-128">To access this, right-click the server name in Object Explorer and select properties; then select the **Database Settings** page.</span></span>  
  
    -   <span data-ttu-id="7df9a-129">若要使备份集在特定日期过期，请单击 **“在”** ，并输入备份集的过期日期。</span><span class="sxs-lookup"><span data-stu-id="7df9a-129">To have the backup set expire on a specific date, click **On**, and enter the date on which the set will expire.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="7df9a-130">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="7df9a-130">Using Transact-SQL</span></span>  
  
#### <a name="to-set-the-expiration-date-on-a-backup"></a><span data-ttu-id="7df9a-131">设置备份的过期日期</span><span class="sxs-lookup"><span data-stu-id="7df9a-131">To set the expiration date on a backup</span></span>  
  
1.  <span data-ttu-id="7df9a-132">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="7df9a-132">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="7df9a-133">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="7df9a-133">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="7df9a-134">在 [BACKUP](/sql/t-sql/statements/backup-transact-sql) 语句中，指定 EXPIREDATE 或 RETAINDAYS 选项以便确定 [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)] 何时可以覆盖备份。</span><span class="sxs-lookup"><span data-stu-id="7df9a-134">In the [BACKUP](/sql/t-sql/statements/backup-transact-sql) statement, specify either the EXPIREDATE or RETAINDAYS option to determine when the [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)] can overwrite the backup.</span></span> <span data-ttu-id="7df9a-135">如果这两个选项均未指定，则过期日期由 [介质保持期](../../database-engine/configure-windows/configure-the-media-retention-server-configuration-option.md) 服务器配置设置确定。</span><span class="sxs-lookup"><span data-stu-id="7df9a-135">If neither option is specified, the expiration date is determined by the [media retention](../../database-engine/configure-windows/configure-the-media-retention-server-configuration-option.md) server configuration setting.</span></span> <span data-ttu-id="7df9a-136">下面的示例使用 `EXPIREDATE` 选项指定过期日期为 2015 年 6 月 30 日 (`6/30/2015`)。</span><span class="sxs-lookup"><span data-stu-id="7df9a-136">This example uses the `EXPIREDATE` option to specify an expiration date of June 30, 2015 (`6/30/2015`).</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
BACKUP DATABASE AdventureWorks2012  
 TO DISK = 'Z:\SQLServerBackups\AdventureWorks2012.Bak'  
   WITH EXPIREDATE = '6/30/2015' ;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="7df9a-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7df9a-137">See Also</span></span>  
 <span data-ttu-id="7df9a-138">[创建完整数据库备份 (SQL Server)](create-a-full-database-backup-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="7df9a-138">[Create a Full Database Backup &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md) </span></span>  
 <span data-ttu-id="7df9a-139">[备份文件和文件组 (SQL Server)](back-up-files-and-filegroups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="7df9a-139">[Back Up Files and Filegroups &#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md) </span></span>  
 <span data-ttu-id="7df9a-140">[备份事务日志 (SQL Server)](back-up-a-transaction-log-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="7df9a-140">[Back Up a Transaction Log &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md) </span></span>  
 [<span data-ttu-id="7df9a-141">创建差异数据库备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="7df9a-141">Create a Differential Database Backup &#40;SQL Server&#41;</span></span>](create-a-differential-database-backup-sql-server.md)  
  
  
