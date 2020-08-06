---
title: 查看排序规则信息 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- collations [SQL Server], view
ms.assetid: 1338b4ea-7142-44bc-a3b9-44e54431405f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 995e559cfd7ca871f5abd90751f2f79167bdf76f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591388"
---
# <a name="view-collation-information"></a><span data-ttu-id="9433c-102">查看排序规则信息</span><span class="sxs-lookup"><span data-stu-id="9433c-102">View Collation Information</span></span>
    
##  <a name="you-can-view-the-collation-of-a-server-database-or-column-in-ssmanstudiofull-using-object-explorer-menu-options-or-by-using-tsql"></a><a name="Top"></a> <span data-ttu-id="9433c-103">您可以通过使用“对象资源管理器”菜单选项或使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 查看 [!INCLUDE[tsql](../../includes/tsql-md.md)]中的服务器、数据库或列的排序规则。</span><span class="sxs-lookup"><span data-stu-id="9433c-103">You can view the collation of a server, database, or column in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] using Object Explorer menu options or by using [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
##  <a name="how-to-view-a-collation-setting"></a><a name="Procedures"></a> <span data-ttu-id="9433c-104">如何查看排序规则设置</span><span class="sxs-lookup"><span data-stu-id="9433c-104">How to View a Collation Setting</span></span>  
 <span data-ttu-id="9433c-105">您可以使用以下项之一：</span><span class="sxs-lookup"><span data-stu-id="9433c-105">You can use one of the following:</span></span>  
  
-   [<span data-ttu-id="9433c-106">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="9433c-106">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
-   [<span data-ttu-id="9433c-107">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="9433c-107">Transact-SQL</span></span>](#TsqlProcedure)  
  
###  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="9433c-108">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="9433c-108">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="9433c-109">**使用对象资源管理器查看服务器（SQL Server 实例）的排序规则设置**</span><span class="sxs-lookup"><span data-stu-id="9433c-109">**To view a collation setting for a server (instance of SQL Server) in Object Explorer**</span></span>  
  
1.  <span data-ttu-id="9433c-110">在“对象资源管理器”中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="9433c-110">In Object Explorer, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="9433c-111">右键单击该实例，然后选择“属性”  。</span><span class="sxs-lookup"><span data-stu-id="9433c-111">Right-click the instance and select **Properties**.</span></span>  
  
 <span data-ttu-id="9433c-112">**使用对象资源管理器查看数据库的排序规则设置**</span><span class="sxs-lookup"><span data-stu-id="9433c-112">**To view a collation setting for a database in Object Explorer**</span></span>  
  
1.  <span data-ttu-id="9433c-113">在对象资源管理器中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的实例，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="9433c-113">In Object Explorer, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="9433c-114">展开“数据库”  ，右键单击数据库，然后选择“属性”  。</span><span class="sxs-lookup"><span data-stu-id="9433c-114">Expand **Databases**, right-click the database and select **Properties**.</span></span>  
  
 <span data-ttu-id="9433c-115">**使用对象资源管理器查看列的排序规则设置**</span><span class="sxs-lookup"><span data-stu-id="9433c-115">**To view a collation setting for a column in Object Explorer**</span></span>  
  
1.  <span data-ttu-id="9433c-116">在对象资源管理器中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的实例，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="9433c-116">In Object Explorer, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="9433c-117">依次展开 **“数据库”** 、数据库和 **“表”** 。</span><span class="sxs-lookup"><span data-stu-id="9433c-117">Expand **Databases**, expand the database and then expand **Tables**.</span></span>  
  
3.  <span data-ttu-id="9433c-118">展开包含该列的表，然后展开 **“列”** 。</span><span class="sxs-lookup"><span data-stu-id="9433c-118">Expand the table that contains the column and then expand **Columns**.</span></span>  
  
4.  <span data-ttu-id="9433c-119">右键单击该列并选择“属性”  。</span><span class="sxs-lookup"><span data-stu-id="9433c-119">Right-click the column and select **Properties**.</span></span> <span data-ttu-id="9433c-120">如果排序规则属性为空，则该列不是字符数据类型。</span><span class="sxs-lookup"><span data-stu-id="9433c-120">If the collation property is empty, the column is not a character data type.</span></span>  
  
###  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="9433c-121">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="9433c-121">Using Transact-SQL</span></span>  
 <span data-ttu-id="9433c-122">**查看服务器的排序规则设置**</span><span class="sxs-lookup"><span data-stu-id="9433c-122">**To view the collation setting of a server**</span></span>  
  
1.  <span data-ttu-id="9433c-123">在对象资源管理器中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 实例，并在工具栏中单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="9433c-123">In Object Explorer, connect to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and on the toolbar, click **New Query**.</span></span>  
  
2.  <span data-ttu-id="9433c-124">在查询窗口中，输入以下使用 SERVERPROPERTY 系统函数的语句。</span><span class="sxs-lookup"><span data-stu-id="9433c-124">In the query window, enter the following statement that uses the SERVERPROPERTY system function.</span></span>  
  
    ```  
    SELECT CONVERT (varchar, SERVERPROPERTY('collation'));  
    ```  
  
3.  <span data-ttu-id="9433c-125">或者，您可以使用 sp_helpsort 系统存储过程。</span><span class="sxs-lookup"><span data-stu-id="9433c-125">Alternatively, you can use the sp_helpsort system stored procedure.</span></span>  
  
    ```  
    EXECUTE sp_helpsort;  
    ```  
  
 <span data-ttu-id="9433c-126">**查看 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="9433c-126">**To view all collations supported by [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]**</span></span>  
  
1.  <span data-ttu-id="9433c-127">在对象资源管理器中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 实例，并在工具栏中单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="9433c-127">In Object Explorer, connect to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and on the toolbar, click **New Query**.</span></span>  
  
2.  <span data-ttu-id="9433c-128">在查询窗口中，输入以下使用 SERVERPROPERTY 系统函数的语句。</span><span class="sxs-lookup"><span data-stu-id="9433c-128">In the query window, enter the following statement that uses the SERVERPROPERTY system function.</span></span>  
  
    ```  
    SELECT name, description FROM sys.fn_helpcollations();  
    ```  
  
 <span data-ttu-id="9433c-129">**查看数据库的排序规则设置**</span><span class="sxs-lookup"><span data-stu-id="9433c-129">**To view the collation setting of a database**</span></span>  
  
1.  <span data-ttu-id="9433c-130">在对象资源管理器中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 实例，并在工具栏中单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="9433c-130">In Object Explorer, connect to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and on the toolbar, click **New Query**.</span></span>  
  
2.  <span data-ttu-id="9433c-131">在查询窗口中，输入以下使用 sys.databases 系统目录视图的语句。</span><span class="sxs-lookup"><span data-stu-id="9433c-131">In the query window, enter the following statement that uses the sys.databases system catalog view.</span></span>  
  
    ```  
    SELECT name, collation_name FROM sys.databases;  
    ```  
  
3.  <span data-ttu-id="9433c-132">或者，您可以使用 DATABASEPROPERTYEX 的系统函数。</span><span class="sxs-lookup"><span data-stu-id="9433c-132">Alternatively, you can use the DATABASEPROPERTYEX system function.</span></span>  
  
    ```  
    SELECT CONVERT (varchar, DATABASEPROPERTYEX('database_name','collation'));  
    ```  
  
 <span data-ttu-id="9433c-133">**查看列的排序规则设置**</span><span class="sxs-lookup"><span data-stu-id="9433c-133">**To view the collation setting of a column**</span></span>  
  
1.  <span data-ttu-id="9433c-134">在对象资源管理器中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 实例，并在工具栏中单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="9433c-134">In Object Explorer, connect to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and on the toolbar, click **New Query**.</span></span>  
  
2.  <span data-ttu-id="9433c-135">在查询窗口中，输入以下使用 sys.columns 系统目录视图的语句。</span><span class="sxs-lookup"><span data-stu-id="9433c-135">In the query window, enter the following statement that uses the sys.columns system catalog view.</span></span>  
  
    ```  
    SELECT name, collation_name FROM sys.columns WHERE name = N'<insert character data type column name>';  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="9433c-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9433c-136">See Also</span></span>  
 <span data-ttu-id="9433c-137">[SERVERPROPERTY (Transact-SQL)](/sql/t-sql/functions/serverproperty-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9433c-137">[SERVERPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/serverproperty-transact-sql) </span></span>  
 <span data-ttu-id="9433c-138">[sys.fn_helpcollations (Transact-SQL)](/sql/relational-databases/system-functions/sys-fn-helpcollations-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9433c-138">[sys.fn_helpcollations &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-helpcollations-transact-sql) </span></span>  
 <span data-ttu-id="9433c-139">[sys.databases (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9433c-139">[sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) </span></span>  
 <span data-ttu-id="9433c-140">[sys.columns (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-columns-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9433c-140">[sys.columns &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-columns-transact-sql) </span></span>  
 <span data-ttu-id="9433c-141">[排序规则优先级 (Transact-SQL)](/sql/t-sql/statements/collation-precedence-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9433c-141">[Collation Precedence &#40;Transact-SQL&#41;](/sql/t-sql/statements/collation-precedence-transact-sql) </span></span>  
 [<span data-ttu-id="9433c-142">sp_helpsort (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="9433c-142">sp_helpsort &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-helpsort-transact-sql)  
  
  
