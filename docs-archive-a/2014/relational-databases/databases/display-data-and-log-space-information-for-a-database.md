---
title: 显示数据库的数据和日志空间信息 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- logs [SQL Server], space
- status information [SQL Server], space
- displaying space information
- disk space [SQL Server], displaying
- databases [SQL Server], space used
- viewing space information
- space allocation [SQL Server], displaying
- data space [SQL Server]
ms.assetid: c7b99463-4bab-4e9b-9217-fcb0898dc757
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1beb8cdedbc2b72eadeeb350ee1c3b6d16218205
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693935"
---
# <a name="display-data-and-log-space-information-for-a-database"></a><span data-ttu-id="b5207-102">显示数据库的数据和日志空间信息</span><span class="sxs-lookup"><span data-stu-id="b5207-102">Display Data and Log Space Information for a Database</span></span>
  <span data-ttu-id="b5207-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中显示数据库的数据和日志空间信息。</span><span class="sxs-lookup"><span data-stu-id="b5207-103">This topic describes how to display the data and log space information for a database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="b5207-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="b5207-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="b5207-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="b5207-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="b5207-106">安全性</span><span class="sxs-lookup"><span data-stu-id="b5207-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="b5207-107">**若要显示数据库的数据和日志空间信息，请使用：**</span><span class="sxs-lookup"><span data-stu-id="b5207-107">**To display data and log space information for a database, using:**</span></span>  
  
     [<span data-ttu-id="b5207-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b5207-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="b5207-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b5207-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="b5207-110">开始之前</span><span class="sxs-lookup"><span data-stu-id="b5207-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="b5207-111">Security</span><span class="sxs-lookup"><span data-stu-id="b5207-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="b5207-112">权限</span><span class="sxs-lookup"><span data-stu-id="b5207-112">Permissions</span></span>  
 <span data-ttu-id="b5207-113">执行 **sp_spaceused** 的权限授予 **public** 角色。</span><span class="sxs-lookup"><span data-stu-id="b5207-113">Permission to execute **sp_spaceused** is granted to the **public** role.</span></span> <span data-ttu-id="b5207-114">只有 **db_owner** 固定数据库角色的成员可以指定 **@updateusage** 参数。</span><span class="sxs-lookup"><span data-stu-id="b5207-114">Only members of the **db_owner** fixed database role can specify the **@updateusage** parameter.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="b5207-115">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b5207-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-display-data-and-log-space-information-for-a-database"></a><span data-ttu-id="b5207-116">若要显示数据库的数据和日志空间信息</span><span class="sxs-lookup"><span data-stu-id="b5207-116">To display data and log space information for a database</span></span>  
  
1.  <span data-ttu-id="b5207-117">在对象资源管理器中，连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的实例，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="b5207-117">In Object Explorer, connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="b5207-118">展开 **“数据库”** 。</span><span class="sxs-lookup"><span data-stu-id="b5207-118">Expand **Databases**.</span></span>  
  
3.  <span data-ttu-id="b5207-119">右键单击某数据库，依次指向“报表”和“标准报表”，然后单击“磁盘使用情况”。</span><span class="sxs-lookup"><span data-stu-id="b5207-119">Right-click a database, point to **Reports**, point to **Standard Reports,**, and then click **Disk Usage**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="b5207-120">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b5207-120">Using Transact-SQL</span></span>  
  
#### <a name="to-display-data-and-log-space-information-for-a-database-by-using-sp_spaceused"></a><span data-ttu-id="b5207-121">使用 sp_spaceused 显示数据库的数据和日志空间信息</span><span class="sxs-lookup"><span data-stu-id="b5207-121">To display data and log space information for a database by using sp_spaceused</span></span>  
  
1.  <span data-ttu-id="b5207-122">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b5207-122">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="b5207-123">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="b5207-123">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="b5207-124">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="b5207-124">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="b5207-125">该示例使用 [sp_spaceused](/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql) 系统存储过程报告 `Vendor` 表及其索引的磁盘空间信息。</span><span class="sxs-lookup"><span data-stu-id="b5207-125">This example uses the [sp_spaceused](/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql) system stored procedure to report disk space information for the `Vendor` table and its indexes.</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_spaceused N'Purchasing.Vendor';  
GO  
```  
  
#### <a name="to-display-data-and-log-space-information-for-a-database-by-querying-sysdatabase_files"></a><span data-ttu-id="b5207-126">通过查询 sys.database_files 显示数据库的数据和日志空间信息</span><span class="sxs-lookup"><span data-stu-id="b5207-126">To display data and log space information for a database by querying sys.database_files</span></span>  
  
1.  <span data-ttu-id="b5207-127">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b5207-127">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="b5207-128">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="b5207-128">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="b5207-129">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="b5207-129">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="b5207-130">此示例查询 [sys.database_files](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql) 目录视图以便返回与 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 数据库中的数据和日志文件有关的特定信息。</span><span class="sxs-lookup"><span data-stu-id="b5207-130">This example queries the [sys.database_files](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql) catalog view to return specific information about the data and log files in the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT file_id, name, type_desc, physical_name, size, max_size  
FROM sys.database_files ;  
GO  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="b5207-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b5207-131">See Also</span></span>  
 <span data-ttu-id="b5207-132">[SELECT (Transact-SQL)](/sql/t-sql/queries/select-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b5207-132">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span></span>  
 <span data-ttu-id="b5207-133">[sys.database_files (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b5207-133">[sys.database_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql) </span></span>  
 <span data-ttu-id="b5207-134">[sp_spaceused (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b5207-134">[sp_spaceused &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql) </span></span>  
 <span data-ttu-id="b5207-135">[向数据库中添加数据文件或日志文件](add-data-or-log-files-to-a-database.md) </span><span class="sxs-lookup"><span data-stu-id="b5207-135">[Add Data or Log Files to a Database](add-data-or-log-files-to-a-database.md) </span></span>  
 [<span data-ttu-id="b5207-136">删除数据库中的数据文件或日志文件</span><span class="sxs-lookup"><span data-stu-id="b5207-136">Delete Data or Log Files from a Database</span></span>](delete-data-or-log-files-from-a-database.md)  
  
  
