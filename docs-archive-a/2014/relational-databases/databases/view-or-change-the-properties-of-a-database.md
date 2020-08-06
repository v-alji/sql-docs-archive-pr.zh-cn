---
title: 查看或更改数据库的属性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- displaying databases
- database viewing [SQL Server]
- databases [SQL Server], viewing
- viewing databases
ms.assetid: 9e8ac097-84b7-46c7-85e3-c1e79f94d747
author: stevestein
ms.author: sstein
ms.openlocfilehash: d6aee7503ca02d47575be4e8103641f61d9696d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693369"
---
# <a name="view-or-change-the-properties-of-a-database"></a><span data-ttu-id="5305e-102">查看或更改数据库的属性</span><span class="sxs-lookup"><span data-stu-id="5305e-102">View or Change the Properties of a Database</span></span>
  <span data-ttu-id="5305e-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中查看或更改数据库的属性。</span><span class="sxs-lookup"><span data-stu-id="5305e-103">This topic describes how to view or change the properties of a database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="5305e-104">更改数据库属性后，修改内容将立即生效。</span><span class="sxs-lookup"><span data-stu-id="5305e-104">After you change a database property, the modification takes effect immediately.</span></span>  
  
 <span data-ttu-id="5305e-105">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="5305e-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="5305e-106">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="5305e-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="5305e-107">建议</span><span class="sxs-lookup"><span data-stu-id="5305e-107">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="5305e-108">安全性</span><span class="sxs-lookup"><span data-stu-id="5305e-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="5305e-109">**查看或更改数据库的属性，使用：**</span><span class="sxs-lookup"><span data-stu-id="5305e-109">**To view or change the properties of a database, using:**</span></span>  
  
     [<span data-ttu-id="5305e-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="5305e-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="5305e-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="5305e-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="5305e-112">开始之前</span><span class="sxs-lookup"><span data-stu-id="5305e-112">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="5305e-113">建议</span><span class="sxs-lookup"><span data-stu-id="5305e-113">Recommendations</span></span>  
  
-   <span data-ttu-id="5305e-114">当 AUTO_CLOSE 为 ON 时，由于该数据库不可用于检索数据，因此 [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) 目录视图中的某些列和 DATABASEPROPERTYEX 函数将返回 NULL。</span><span class="sxs-lookup"><span data-stu-id="5305e-114">When AUTO_CLOSE is ON, some columns in the [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) catalog view and DATABASEPROPERTYEX function will return NULL because the database is unavailable to retrieve the data.</span></span> <span data-ttu-id="5305e-115">若要解决此问题，请执行 USE 语句打开数据库。</span><span class="sxs-lookup"><span data-stu-id="5305e-115">To resolve this, execute a USE statement to open the database.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="5305e-116">Security</span><span class="sxs-lookup"><span data-stu-id="5305e-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="5305e-117">权限</span><span class="sxs-lookup"><span data-stu-id="5305e-117">Permissions</span></span>  
 <span data-ttu-id="5305e-118">需要对数据库拥有 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="5305e-118">Requires ALTER permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="5305e-119">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="5305e-119">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-or-change-the-properties-of-a-database"></a><span data-ttu-id="5305e-120">查看或更改数据库的属性</span><span class="sxs-lookup"><span data-stu-id="5305e-120">To view or change the properties of a database</span></span>  
  
1.  <span data-ttu-id="5305e-121">在 **对象资源管理器**中，连接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]的实例，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="5305e-121">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="5305e-122">展开“数据库”，右键单击要查看的数据库，再单击“属性”。</span><span class="sxs-lookup"><span data-stu-id="5305e-122">Expand **Databases**, right-click the database to view, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="5305e-123">在 **“数据库属性”** 对话框中，选择一个页以查看相应的信息。</span><span class="sxs-lookup"><span data-stu-id="5305e-123">In the **Database Properties** dialog box, select a page to view the corresponding information.</span></span> <span data-ttu-id="5305e-124">例如，选择 **“文件”** 页可以查看数据和日志文件信息。</span><span class="sxs-lookup"><span data-stu-id="5305e-124">For example, select the **Files** page to view data and log file information.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="5305e-125">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="5305e-125">Using Transact-SQL</span></span>  
  
#### <a name="to-view-a-property-of-a-database-by-using-databasepropertyex"></a><span data-ttu-id="5305e-126">使用 DATABASEPROPERTYEX 查看数据库的属性</span><span class="sxs-lookup"><span data-stu-id="5305e-126">To view a property of a database by using DATABASEPROPERTYEX</span></span>  
  
1.  <span data-ttu-id="5305e-127">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5305e-127">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="5305e-128">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="5305e-128">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="5305e-129">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="5305e-129">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="5305e-130">此示例使用 [DATABASEPROPERTYEX](/sql/t-sql/functions/databasepropertyex-transact-sql) 系统函数返回 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 数据库中 AUTO_SHRINK 数据库选项的状态。</span><span class="sxs-lookup"><span data-stu-id="5305e-130">This example uses the [DATABASEPROPERTYEX](/sql/t-sql/functions/databasepropertyex-transact-sql) system function to return the status of the AUTO_SHRINK database option in the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="5305e-131">返回值 1 表示将该选项设置为 ON，返回值 0 表示将该选项设置为 OFF。</span><span class="sxs-lookup"><span data-stu-id="5305e-131">A return value of 1 means that the option is set to ON, and a return value of 0 means that the option is set to OFF.</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT DATABASEPROPERTYEX('AdventureWorks2012', 'IsAutoShrink');  
GO  
  
```  
  
#### <a name="to-view-the-properties-of-a-database-by-querying-sysdatabases"></a><span data-ttu-id="5305e-132">通过查询 sys.databases 查看数据库的属性</span><span class="sxs-lookup"><span data-stu-id="5305e-132">To view the properties of a database by querying sys.databases</span></span>  
  
1.  <span data-ttu-id="5305e-133">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5305e-133">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="5305e-134">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="5305e-134">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="5305e-135">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="5305e-135">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="5305e-136">此示例查询 [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) 目录视图来查看 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 数据库的几个属性。</span><span class="sxs-lookup"><span data-stu-id="5305e-136">This example queries the [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) catalog view to view several properties of the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="5305e-137">此实例返回数据库 ID 号 (`database_id`)、数据库是只读还是读写的 (`is_read_only`)、数据库的排序规则 (`collation_name`) 和数据库兼容级别 (`compatibility_level`)。</span><span class="sxs-lookup"><span data-stu-id="5305e-137">This example returns the database ID number (`database_id`), whether the database is read-only or read-write (`is_read_only`), the collation for the database (`collation_name`), and the database compatibility level (`compatibility_level`).</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT database_id, is_read_only, collation_name, compatibility_level  
FROM sys.databases WHERE name = 'AdventureWorks2012';  
GO  
  
```  
  
#### <a name="to-change-the-properties-of-a-database"></a><span data-ttu-id="5305e-138">更改数据库的属性</span><span class="sxs-lookup"><span data-stu-id="5305e-138">To change the properties of a database</span></span>  
  
1.  <span data-ttu-id="5305e-139">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5305e-139">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="5305e-140">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="5305e-140">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="5305e-141">复制以下示例并将其粘贴到查询窗口中。</span><span class="sxs-lookup"><span data-stu-id="5305e-141">Copy and paste the following example into the query window.</span></span> <span data-ttu-id="5305e-142">此示例确定 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 数据库上的快照隔离状态，更改属性的状态，然后验证更改。</span><span class="sxs-lookup"><span data-stu-id="5305e-142">The example determines the state of snapshot isolation on the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database, changes the state of the property, and then verifies the change.</span></span>  
  
     <span data-ttu-id="5305e-143">若要确定快照隔离的状态，请选择第一个 `SELECT` 语句，然后单击 **“执行”** 。</span><span class="sxs-lookup"><span data-stu-id="5305e-143">To determine the state of snapshot isolation, select the first `SELECT` statement and click **Execute**.</span></span>  
  
     <span data-ttu-id="5305e-144">若要更改快照隔离的状态，请选择 `ALTER DATABASE` 语句，然后单击 **“执行”** 。</span><span class="sxs-lookup"><span data-stu-id="5305e-144">To change the state of snapshot isolation, select the `ALTER DATABASE` statement and click **Execute**.</span></span>  
  
     <span data-ttu-id="5305e-145">若要验证更改，请选择第二个 `SELECT` 语句，然后单击 **“执行”** 。</span><span class="sxs-lookup"><span data-stu-id="5305e-145">To verify the change, select the second `SELECT` statement, and click **Execute**.</span></span>  
  
 [!code-sql[DatabaseDDL#AlterDatabase9](../../snippets/tsql/SQL14/tsql/databaseddl/transact-sql/alterdatabase.sql#alterdatabase9)]  
  
## <a name="see-also"></a><span data-ttu-id="5305e-146">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5305e-146">See Also</span></span>  
 <span data-ttu-id="5305e-147">[sys.databases (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5305e-147">[sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) </span></span>  
 <span data-ttu-id="5305e-148">[ALTER DATABASE SET HADR (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql-set-hadr) </span><span class="sxs-lookup"><span data-stu-id="5305e-148">[ALTER DATABASE SET HADR &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-hadr) </span></span>  
 <span data-ttu-id="5305e-149">[ALTER DATABASE SET 选项 (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql-set-options) </span><span class="sxs-lookup"><span data-stu-id="5305e-149">[ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options) </span></span>  
 <span data-ttu-id="5305e-150">[ALTER DATABASE 数据库镜像 (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) </span><span class="sxs-lookup"><span data-stu-id="5305e-150">[ALTER DATABASE Database Mirroring &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) </span></span>  
 <span data-ttu-id="5305e-151">[ALTER DATABASE 兼容级别 (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level) </span><span class="sxs-lookup"><span data-stu-id="5305e-151">[ALTER DATABASE Compatibility Level &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level) </span></span>  
 [<span data-ttu-id="5305e-152">ALTER DATABASE 文件和文件组选项 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="5305e-152">ALTER DATABASE File and Filegroup Options &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options)  
  
  
