---
title: 查看备份集中的数据文件和日志文件 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- database backups [SQL Server], viewing backup sets
- viewing backup set information
- backup sets [SQL Server], viewing files in
- displaying backup set information
- transaction log backups [SQL Server], viewing backup sets
- backing up [SQL Server], viewing backup sets
ms.assetid: abb6420c-f809-426e-aeb4-d0a74989cf39
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7dbcb14a658b49aba6f5f2ebe3425a2ab5759efa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690662"
---
# <a name="view-the-data-and-log-files-in-a-backup-set-sql-server"></a><span data-ttu-id="ab5ec-102">查看备份集中的数据文件和日志文件 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ab5ec-102">View the Data and Log Files in a Backup Set (SQL Server)</span></span>
  <span data-ttu-id="ab5ec-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中查看备份集中的数据文件和日志文件。</span><span class="sxs-lookup"><span data-stu-id="ab5ec-103">This topic describes how to view the data and log files in a backup set in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="ab5ec-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="ab5ec-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="ab5ec-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="ab5ec-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="ab5ec-106">安全性</span><span class="sxs-lookup"><span data-stu-id="ab5ec-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="ab5ec-107">**若要查看备份集中的数据文件和日志文件，可使用：**</span><span class="sxs-lookup"><span data-stu-id="ab5ec-107">**To view the data and log files in a backup set, using:**</span></span>  
  
     [<span data-ttu-id="ab5ec-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ab5ec-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="ab5ec-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ab5ec-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ab5ec-110">开始之前</span><span class="sxs-lookup"><span data-stu-id="ab5ec-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ab5ec-111">Security</span><span class="sxs-lookup"><span data-stu-id="ab5ec-111">Security</span></span>  
 <span data-ttu-id="ab5ec-112">有关安全性的信息，请参阅 [RESTORE FILELISTONLY (Transact SQL)](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="ab5ec-112">For information about security, see [RESTORE FILELISTONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql)</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ab5ec-113">权限</span><span class="sxs-lookup"><span data-stu-id="ab5ec-113">Permissions</span></span>  
 <span data-ttu-id="ab5ec-114">在 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 和更高版本中，获取有关备份集或备份设备的信息要求具有 CREATE DATABASE 权限。</span><span class="sxs-lookup"><span data-stu-id="ab5ec-114">In [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] and later versions, obtaining information about a backup set or backup device requires CREATE DATABASE permission.</span></span> <span data-ttu-id="ab5ec-115">有关详细信息，请参阅 [GRANT 数据库权限 (Transact-SQL)](/sql/t-sql/statements/grant-database-permissions-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="ab5ec-115">For more information, see [GRANT Database Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-database-permissions-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="ab5ec-116">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ab5ec-116">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-the-data-and-log-files-in-a-backup-set"></a><span data-ttu-id="ab5ec-117">查看备份集中的数据文件和日志文件</span><span class="sxs-lookup"><span data-stu-id="ab5ec-117">To view the data and log files in a backup set</span></span>  
  
1.  <span data-ttu-id="ab5ec-118">连接到相应的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 实例之后，在“对象资源管理器”中，单击服务器名称以展开服务器树。</span><span class="sxs-lookup"><span data-stu-id="ab5ec-118">After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="ab5ec-119">展开 **“数据库”** ，然后根据数据库的不同，选择用户数据库，或展开 **“系统数据库”** ，再选择系统数据库。</span><span class="sxs-lookup"><span data-stu-id="ab5ec-119">Expand **Databases**, and, depending on the database, either select a user database or expand **System Databases** and select a system database.</span></span>  
  
3.  <span data-ttu-id="ab5ec-120">右键单击该数据库，再单击“属性”  ，这将打开“数据库属性”  对话框。</span><span class="sxs-lookup"><span data-stu-id="ab5ec-120">Right-click the database, and then click **Properties**, which opens the **Database Properties** dialog box.</span></span>  
  
4.  <span data-ttu-id="ab5ec-121">在 **“选择页”** 窗格中，单击 **“文件”** 。</span><span class="sxs-lookup"><span data-stu-id="ab5ec-121">In the **Select a Page** pane, click **Files**.</span></span>  
  
5.  <span data-ttu-id="ab5ec-122">在 **“数据库文件”** 网格查找数据和日志文件及其属性的列表。</span><span class="sxs-lookup"><span data-stu-id="ab5ec-122">Look in the **Database files** grid for a list of the data and log files and their properties.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="ab5ec-123">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ab5ec-123">Using Transact-SQL</span></span>  
  
#### <a name="to-view-the-data-and-log-files-in-a-backup-set"></a><span data-ttu-id="ab5ec-124">查看备份集中的数据文件和日志文件</span><span class="sxs-lookup"><span data-stu-id="ab5ec-124">To view the data and log files in a backup set</span></span>  
  
1.  <span data-ttu-id="ab5ec-125">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ab5ec-125">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="ab5ec-126">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="ab5ec-126">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="ab5ec-127">使用 [RESTORE FILELISTONLY](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql) 语句。</span><span class="sxs-lookup"><span data-stu-id="ab5ec-127">Use the [RESTORE FILELISTONLY](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql) statement.</span></span> <span data-ttu-id="ab5ec-128">此示例返回有关`FILE=2`备份设备上的第二个备份集 ( `AdventureWorksBackups` ) 的信息。</span><span class="sxs-lookup"><span data-stu-id="ab5ec-128">This example returns information about the second backup set (`FILE=2`) on the `AdventureWorksBackups` backup device.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
RESTORE FILELISTONLY FROM AdventureWorksBackups   
   WITH FILE=2;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="ab5ec-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ab5ec-129">See Also</span></span>  
 <span data-ttu-id="ab5ec-130">[backupfilegroup (Transact-SQL)](/sql/relational-databases/system-tables/backupfilegroup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ab5ec-130">[backupfilegroup &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupfilegroup-transact-sql) </span></span>  
 <span data-ttu-id="ab5ec-131">[backupfile (Transact-SQL)](/sql/relational-databases/system-tables/backupfile-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ab5ec-131">[backupfile &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupfile-transact-sql) </span></span>  
 <span data-ttu-id="ab5ec-132">[backupset (Transact-SQL)](/sql/relational-databases/system-tables/backupset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ab5ec-132">[backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql) </span></span>  
 <span data-ttu-id="ab5ec-133">[backupmediaset (Transact-SQL)](/sql/relational-databases/system-tables/backupmediaset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ab5ec-133">[backupmediaset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupmediaset-transact-sql) </span></span>  
 <span data-ttu-id="ab5ec-134">[backupmediafamily (Transact-SQL)](/sql/relational-databases/system-tables/backupmediafamily-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ab5ec-134">[backupmediafamily &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupmediafamily-transact-sql) </span></span>  
 [<span data-ttu-id="ab5ec-135">备份设备 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ab5ec-135">Backup Devices &#40;SQL Server&#41;</span></span>](backup-devices-sql-server.md)  
  
  
