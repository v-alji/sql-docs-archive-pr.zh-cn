---
title: 创建数据库 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- databases [SQL Server], creating
- database creation [SQL Server], SQL Server Management Studio
- creating databases
ms.assetid: 4c4beea2-6cbc-4352-9db6-49ea8130bb64
author: stevestein
ms.author: sstein
ms.openlocfilehash: fe42e394482e3abf4d87c00c6e79ee84db6ba278
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581311"
---
# <a name="create-a-database"></a><span data-ttu-id="41b16-102">创建数据库</span><span class="sxs-lookup"><span data-stu-id="41b16-102">Create a Database</span></span>
  <span data-ttu-id="41b16-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中创建数据库。</span><span class="sxs-lookup"><span data-stu-id="41b16-103">This topic describes how to create a database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="41b16-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="41b16-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="41b16-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="41b16-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="41b16-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="41b16-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="41b16-107">先决条件</span><span class="sxs-lookup"><span data-stu-id="41b16-107">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="41b16-108">建议</span><span class="sxs-lookup"><span data-stu-id="41b16-108">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="41b16-109">安全性</span><span class="sxs-lookup"><span data-stu-id="41b16-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="41b16-110">**创建数据库，使用：**</span><span class="sxs-lookup"><span data-stu-id="41b16-110">**To create a database, using:**</span></span>  
  
     [<span data-ttu-id="41b16-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="41b16-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="41b16-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="41b16-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="41b16-113">开始之前</span><span class="sxs-lookup"><span data-stu-id="41b16-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="41b16-114">限制和局限</span><span class="sxs-lookup"><span data-stu-id="41b16-114">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="41b16-115">在一个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的实例中最多可以指定 32,767 个数据库。</span><span class="sxs-lookup"><span data-stu-id="41b16-115">A maximum of 32,767 databases can be specified on an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="41b16-116">先决条件</span><span class="sxs-lookup"><span data-stu-id="41b16-116">Prerequisites</span></span>  
  
-   <span data-ttu-id="41b16-117">CREATE DATABASE 语句必须以自动提交模式（默认事务管理模式）运行，不允许在显式或隐式事务中使用。</span><span class="sxs-lookup"><span data-stu-id="41b16-117">The CREATE DATABASE statement must run in autocommit mode (the default transaction management mode) and is not allowed in an explicit or implicit transaction.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="41b16-118">建议</span><span class="sxs-lookup"><span data-stu-id="41b16-118">Recommendations</span></span>  
  
-   <span data-ttu-id="41b16-119">创建、修改或删除用户数据库后，应备份 [master](master-database.md) 数据库。</span><span class="sxs-lookup"><span data-stu-id="41b16-119">The [master](master-database.md) database should be backed up whenever a user database is created, modified, or dropped.</span></span>  
  
-   <span data-ttu-id="41b16-120">在创建数据库时，请根据数据库中预期的最大数据量，创建尽可能大的数据文件。</span><span class="sxs-lookup"><span data-stu-id="41b16-120">When you create a database, make the data files as large as possible based on the maximum amount of data you expect in the database.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="41b16-121">Security</span><span class="sxs-lookup"><span data-stu-id="41b16-121">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="41b16-122">权限</span><span class="sxs-lookup"><span data-stu-id="41b16-122">Permissions</span></span>  
 <span data-ttu-id="41b16-123">需要对 master 数据库的 CREATE DATABASE 权限，或需要 CREATE ANY DATABASE/ALTER ANY DATABASE 权限。</span><span class="sxs-lookup"><span data-stu-id="41b16-123">Requires CREATE DATABASE permission in the master database, or requires CREATE ANY DATABASE, or ALTER ANY DATABASE permission.</span></span>  
  
 <span data-ttu-id="41b16-124">为了控制对运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例的计算机上的磁盘使用，通常只有少数登录帐户才有创建数据库的权限。</span><span class="sxs-lookup"><span data-stu-id="41b16-124">To maintain control over disk use on an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], permission to create databases is typically limited to a few login accounts.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="41b16-125">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="41b16-125">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-database"></a><span data-ttu-id="41b16-126">创建数据库</span><span class="sxs-lookup"><span data-stu-id="41b16-126">To create a database</span></span>  
  
1.  <span data-ttu-id="41b16-127">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 的实例，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="41b16-127">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="41b16-128">右键单击“数据库”，然后单击“新建数据库”。</span><span class="sxs-lookup"><span data-stu-id="41b16-128">Right-click **Databases**, and then click **New Database**.</span></span>  
  
3.  <span data-ttu-id="41b16-129">在 **“新建数据库”** 中，输入数据库名称。</span><span class="sxs-lookup"><span data-stu-id="41b16-129">In **New Database**, enter a database name.</span></span>  
  
4.  <span data-ttu-id="41b16-130">若要通过接受所有默认值创建数据库，请单击 **“确定”** ；否则，请继续后面的可选步骤。</span><span class="sxs-lookup"><span data-stu-id="41b16-130">To create the database by accepting all default values, click **OK**; otherwise, continue with the following optional steps.</span></span>  
  
5.  <span data-ttu-id="41b16-131">若要更改所有者名称，请单击 (…) 选择其他所有者。</span><span class="sxs-lookup"><span data-stu-id="41b16-131">To change the owner name, click (**...**) to select another owner.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="41b16-132">“使用全文检索”选项始终处于选中和灰显状态，这是因为从 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 开始，所有用户数据库都启用了全文检索。</span><span class="sxs-lookup"><span data-stu-id="41b16-132">The **Use full-text indexing** option is always checked and dimmed because, beginning in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], all user databases are full-text enabled.</span></span>  
  
6.  <span data-ttu-id="41b16-133">若要更改主数据文件和事务日志文件的默认值，请在 **“数据库文件”** 网格中单击相应的单元并输入新值。</span><span class="sxs-lookup"><span data-stu-id="41b16-133">To change the default values of the primary data and transaction log files, in the **Database files** grid, click the appropriate cell and enter the new value.</span></span> <span data-ttu-id="41b16-134">有关详细信息，请参阅 [向数据库中添加数据文件或日志文件](add-data-or-log-files-to-a-database.md)。</span><span class="sxs-lookup"><span data-stu-id="41b16-134">For more information, see [Add Data or Log Files to a Database](add-data-or-log-files-to-a-database.md).</span></span>  
  
7.  <span data-ttu-id="41b16-135">若要更改数据库的排序规则，请选择 **“选项”** 页，然后从列表中选择一个排序规则。</span><span class="sxs-lookup"><span data-stu-id="41b16-135">To change the collation of the database, select the **Options** page, and then select a collation from the list.</span></span>  
  
8.  <span data-ttu-id="41b16-136">若要更改恢复模式，请选择 **“选项”** 页，然后从列表中选择一个恢复模式。</span><span class="sxs-lookup"><span data-stu-id="41b16-136">To change the recovery model, select the **Options** page and select a recovery model from the list.</span></span>  
  
9. <span data-ttu-id="41b16-137">若要更改数据库选项，请选择 **“选项”** 页，然后修改数据库选项。</span><span class="sxs-lookup"><span data-stu-id="41b16-137">To change database options, select the **Options** page, and then modify the database options.</span></span> <span data-ttu-id="41b16-138">有关各选项的详细说明，请参阅 [ALTER DATABASE SET 选项 (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql-set-options)。</span><span class="sxs-lookup"><span data-stu-id="41b16-138">For a description of each option, see [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options).</span></span>  
  
10. <span data-ttu-id="41b16-139">若要添加新文件组，请单击 **“文件组”** 页。</span><span class="sxs-lookup"><span data-stu-id="41b16-139">To add a new filegroup, click the **Filegroups** page.</span></span> <span data-ttu-id="41b16-140">单击 **“添加”** ，然后输入文件组的值。</span><span class="sxs-lookup"><span data-stu-id="41b16-140">Click **Add** and then enter the values for the filegroup.</span></span>  
  
11. <span data-ttu-id="41b16-141">若要将扩展属性添加到数据库中，请选择 **“扩展属性”** 页。</span><span class="sxs-lookup"><span data-stu-id="41b16-141">To add an extended property to the database, select the **Extended Properties** page.</span></span>  
  
    1.  <span data-ttu-id="41b16-142">在 **“名称”** 列中，输入扩展属性的名称。</span><span class="sxs-lookup"><span data-stu-id="41b16-142">In the **Name** column, enter a name for the extended property.</span></span>  
  
    2.  <span data-ttu-id="41b16-143">在 **“值”** 列中，输入扩展属性文本。</span><span class="sxs-lookup"><span data-stu-id="41b16-143">In the **Value** column, enter the extended property text.</span></span> <span data-ttu-id="41b16-144">例如，输入描述数据库的一个或多个语句。</span><span class="sxs-lookup"><span data-stu-id="41b16-144">For example, enter one or more statements that describe the database.</span></span>  
  
12. <span data-ttu-id="41b16-145">若要创建数据库，请单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="41b16-145">To create the database, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="41b16-146">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="41b16-146">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-database"></a><span data-ttu-id="41b16-147">创建数据库</span><span class="sxs-lookup"><span data-stu-id="41b16-147">To create a database</span></span>  
  
1.  <span data-ttu-id="41b16-148">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="41b16-148">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="41b16-149">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="41b16-149">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="41b16-150">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="41b16-150">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="41b16-151">此示例将创建数据库 `Sales`。</span><span class="sxs-lookup"><span data-stu-id="41b16-151">This example creates the database `Sales`.</span></span> <span data-ttu-id="41b16-152">因为没有使用关键字 PRIMARY，第一个文件 (`Sales`_`dat`) 将成为主文件。</span><span class="sxs-lookup"><span data-stu-id="41b16-152">Because the keyword PRIMARY is not used, the first file (`Sales`_`dat`) becomes the primary file.</span></span> <span data-ttu-id="41b16-153">因为在 `Sales`\_`dat` 文件的 SIZE 参数中没有指定 MB 或 KB，将使用 MB 并按 MB 分配。</span><span class="sxs-lookup"><span data-stu-id="41b16-153">Because neither MB nor KB is specified in the SIZE parameter for the `Sales`\_`dat` file, it uses MB and is allocated in megabytes.</span></span> <span data-ttu-id="41b16-154">创建、修改或删除用户数据库后，应备份 `Sales`\_`log` 文件以 MB 为单位进行分配，因为 `MB` 参数中显式声明了 `SIZE` 后缀。</span><span class="sxs-lookup"><span data-stu-id="41b16-154">The `Sales`\_`log` file is allocated in megabytes because the `MB` suffix is explicitly stated in the `SIZE` parameter.</span></span>  
  
```sql  
USE master ;  
GO  
CREATE DATABASE Sales  
ON   
( NAME = Sales_dat,  
    FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\saledat.mdf',  
    SIZE = 10,  
    MAXSIZE = 50,  
    FILEGROWTH = 5 )  
LOG ON  
( NAME = Sales_log,  
    FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\salelog.ldf',  
    SIZE = 5MB,  
    MAXSIZE = 25MB,  
    FILEGROWTH = 5MB ) ;  
GO  
```  
  
 <span data-ttu-id="41b16-155">有关更多示例，请参阅 [CREATE DATABASE (SQL Server Transact-SQL)](/sql/t-sql/statements/create-database-sql-server-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="41b16-155">For more examples, see [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41b16-156">另请参阅</span><span class="sxs-lookup"><span data-stu-id="41b16-156">See Also</span></span>  
 <span data-ttu-id="41b16-157">[Database Files and Filegroups](database-files-and-filegroups.md) </span><span class="sxs-lookup"><span data-stu-id="41b16-157">[Database Files and Filegroups](database-files-and-filegroups.md) </span></span>  
 <span data-ttu-id="41b16-158">[数据库分离和附加 (SQL Server)](database-detach-and-attach-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="41b16-158">[Database Detach and Attach &#40;SQL Server&#41;](database-detach-and-attach-sql-server.md) </span></span>  
 <span data-ttu-id="41b16-159">[ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="41b16-159">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 [<span data-ttu-id="41b16-160">向数据库中添加数据文件或日志文件</span><span class="sxs-lookup"><span data-stu-id="41b16-160">Add Data or Log Files to a Database</span></span>](add-data-or-log-files-to-a-database.md)  
  
  
