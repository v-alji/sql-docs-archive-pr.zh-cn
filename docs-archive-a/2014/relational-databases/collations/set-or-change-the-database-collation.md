---
title: 设置或更改数据库排序规则 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- collations [SQL Server], database
- database collations [SQL Server]
ms.assetid: 1379605c-1242-4ac8-ab1b-e2a2b5b1f895
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6d7f7c3e3ddba7ba0ea9701993dbe0fad3a8d975
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591396"
---
# <a name="set-or-change-the-database-collation"></a><span data-ttu-id="12a9e-102">设置或更改数据库排序规则</span><span class="sxs-lookup"><span data-stu-id="12a9e-102">Set or Change the Database Collation</span></span>
  <span data-ttu-id="12a9e-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中设置和更改数据库排序规则。</span><span class="sxs-lookup"><span data-stu-id="12a9e-103">This topic describes how set and change the database collation in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="12a9e-104">如果未指定排序规则，则使用服务器排序规则。</span><span class="sxs-lookup"><span data-stu-id="12a9e-104">If no collation is specified, the server collation is used.</span></span>  
  
 <span data-ttu-id="12a9e-105">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="12a9e-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="12a9e-106">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="12a9e-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="12a9e-107">限制和局限</span><span class="sxs-lookup"><span data-stu-id="12a9e-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="12a9e-108">建议</span><span class="sxs-lookup"><span data-stu-id="12a9e-108">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="12a9e-109">安全性</span><span class="sxs-lookup"><span data-stu-id="12a9e-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="12a9e-110">**若要设置或更改数据库排序规则，请使用：**</span><span class="sxs-lookup"><span data-stu-id="12a9e-110">**To set or change the database collation, using:**</span></span>  
  
     [<span data-ttu-id="12a9e-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="12a9e-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="12a9e-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="12a9e-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="12a9e-113">开始之前</span><span class="sxs-lookup"><span data-stu-id="12a9e-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="12a9e-114">限制和局限</span><span class="sxs-lookup"><span data-stu-id="12a9e-114">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="12a9e-115">仅限 Windows Unicode 的排序规则只能与 COLLATE 子句一起使用，以便将排序规则应用于列级别和表达式级别数据上的 `nchar`、`nvarchar` 和 `ntext` 数据类型。</span><span class="sxs-lookup"><span data-stu-id="12a9e-115">Windows Unicode-only collations can only be used with the COLLATE clause to apply collations to the `nchar`, `nvarchar`, and `ntext` data types on column level and expression-level data.</span></span> <span data-ttu-id="12a9e-116">它们不能与 COLLATE 子句一起使用以更改数据库或服务器实例的排序规则。</span><span class="sxs-lookup"><span data-stu-id="12a9e-116">They cannot be used with the COLLATE clause to change the collation of a database or server instance.</span></span>  
  
-   <span data-ttu-id="12a9e-117">如果指定的排序规则或者被引用的对象所使用的排序规则使用 Windows 不支持的代码页，则 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 将显示错误。</span><span class="sxs-lookup"><span data-stu-id="12a9e-117">If the specified collation or the collation used by the referenced object uses a code page that is not supported by Windows, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] displays an error.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="12a9e-118">建议</span><span class="sxs-lookup"><span data-stu-id="12a9e-118">Recommendations</span></span>  
  
-   <span data-ttu-id="12a9e-119">你可以在 [Windows 排序规则名称 (Transact-SQL)](/sql/t-sql/statements/windows-collation-name-transact-sql) 和 [SQL Server 排序规则名称 (Transact-SQL)](/sql/t-sql/statements/sql-server-collation-name-transact-sql)中找到支持的排序规则名称，或者可以使用 [sys.fn_helpcollations (Transact-SQL)](/sql/relational-databases/system-functions/sys-fn-helpcollations-transact-sql) 系统函数。</span><span class="sxs-lookup"><span data-stu-id="12a9e-119">You can find the supported collation names in [Windows Collation Name &#40;Transact-SQL&#41;](/sql/t-sql/statements/windows-collation-name-transact-sql) and [SQL Server Collation Name &#40;Transact-SQL&#41;](/sql/t-sql/statements/sql-server-collation-name-transact-sql); or you can use the [sys.fn_helpcollations &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-helpcollations-transact-sql) system function.</span></span>  
  
-   <span data-ttu-id="12a9e-120">更改数据库排序规则时，需要更改下列内容：</span><span class="sxs-lookup"><span data-stu-id="12a9e-120">When you change the database collation, you change the following:</span></span>  
  
    -   <span data-ttu-id="12a9e-121">将系统表中的任何 `char`、`varchar`、`text`、`nchar`、`nvarchar` 或 `ntext` 列更改为使用新的排序规则。</span><span class="sxs-lookup"><span data-stu-id="12a9e-121">Any `char`, `varchar`, `text`, `nchar`, `nvarchar`, or `ntext` columns in system tables are changed to the new collation.</span></span>  
  
    -   <span data-ttu-id="12a9e-122">将存储过程和用户定义函数的所有现有 `char`、`varchar`、`text`、`nchar`、`nvarchar` 或 `ntext` 参数和标量返回值更改为使用新的排序规则。</span><span class="sxs-lookup"><span data-stu-id="12a9e-122">All existing `char`, `varchar`, `text`, `nchar`, `nvarchar`, or `ntext` parameters and scalar return values for stored procedures and user-defined functions are changed to the new collation.</span></span>  
  
    -   <span data-ttu-id="12a9e-123">将 `char`、`varchar`、`text`、`nchar`、`nvarchar` 或 `ntext` 系统数据类型和基于这些系统数据类型的所有用户定义的数据类型更改为使用新的默认排序规则。</span><span class="sxs-lookup"><span data-stu-id="12a9e-123">The `char`, `varchar`, `text`, `nchar`, `nvarchar`, or `ntext` system data types, and all user-defined data types based on these system data types, are changed to the new default collation.</span></span>  
  
-   <span data-ttu-id="12a9e-124">可以使用 [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) 语句的 COLLATE 子句来更改在用户数据库中创建的任何新对象的排序规则。</span><span class="sxs-lookup"><span data-stu-id="12a9e-124">You can change the collation of any new objects that are created in a user database by using the COLLATE clause of the [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) statement.</span></span> <span data-ttu-id="12a9e-125">使用此语句不能更改任何现有用户定义的表中列的排序规则。</span><span class="sxs-lookup"><span data-stu-id="12a9e-125">This statement does not change the collation of the columns in any existing user-defined tables.</span></span> <span data-ttu-id="12a9e-126">使用 [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql)的 COLLATE 子句可以更改这些列的排序规则。</span><span class="sxs-lookup"><span data-stu-id="12a9e-126">These can be changed by using the COLLATE clause of [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="12a9e-127">Security</span><span class="sxs-lookup"><span data-stu-id="12a9e-127">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="12a9e-128">权限</span><span class="sxs-lookup"><span data-stu-id="12a9e-128">Permissions</span></span>  
 <span data-ttu-id="12a9e-129">CREATE DATABASE</span><span class="sxs-lookup"><span data-stu-id="12a9e-129">CREATE DATABASE</span></span>  
 <span data-ttu-id="12a9e-130">需要**master**数据库中的 create database 权限，或需要 CREATE any DATABASE 或 ALTER any database 权限。</span><span class="sxs-lookup"><span data-stu-id="12a9e-130">Requires CREATE DATABASE permission in the **master** database, or requires CREATE ANY DATABASE, or ALTER ANY DATABASE permission.</span></span>  
  
 <span data-ttu-id="12a9e-131">ALTER DATABASE</span><span class="sxs-lookup"><span data-stu-id="12a9e-131">ALTER DATABASE</span></span>  
 <span data-ttu-id="12a9e-132">需要对数据库拥有 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="12a9e-132">Requires ALTER permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="12a9e-133">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="12a9e-133">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-set-or-change-the-database-collation"></a><span data-ttu-id="12a9e-134">设置或更改数据库排序规则</span><span class="sxs-lookup"><span data-stu-id="12a9e-134">To set or change the database collation</span></span>  
  
1.  <span data-ttu-id="12a9e-135">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]的实例，再依次展开该实例、 **“数据库”** 。</span><span class="sxs-lookup"><span data-stu-id="12a9e-135">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], expand that instance, and then expand **Databases**.</span></span>  
  
2.  <span data-ttu-id="12a9e-136">如果您正在创建一个新数据库，则右键单击 **“数据库”** ，然后单击 **“新建数据库”** 。</span><span class="sxs-lookup"><span data-stu-id="12a9e-136">If you are creating a new database, right-click **Databases** and then click **New Database**.</span></span> <span data-ttu-id="12a9e-137">如果您不希望使用默认排序规则，则单击 **“选项”** 页，然后从 **“排序规则”** 下拉列表中选择某一排序规则。</span><span class="sxs-lookup"><span data-stu-id="12a9e-137">If you do not want the default collation, click the **Options** page, and select a collation from the **Collation** drop-down list.</span></span>  
  
     <span data-ttu-id="12a9e-138">或者，如果数据库已经存在，则右键单击所需数据库，然后单击 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="12a9e-138">Alternatively, if the database already exists, right-click the database that you want and click **Properties**.</span></span> <span data-ttu-id="12a9e-139">单击 **“选项”** 页，然后从 **“排序规则”** 下拉列表中选择某一排序规则。</span><span class="sxs-lookup"><span data-stu-id="12a9e-139">Click the **Options** page, and select a collation from the **Collation** drop-down list.</span></span>  
  
3.  <span data-ttu-id="12a9e-140">在完成后，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="12a9e-140">After you are finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="12a9e-141">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="12a9e-141">Using Transact-SQL</span></span>  
  
#### <a name="to-set-the-database-collation"></a><span data-ttu-id="12a9e-142">设置数据库排序规则</span><span class="sxs-lookup"><span data-stu-id="12a9e-142">To set the database collation</span></span>  
  
1.  <span data-ttu-id="12a9e-143">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="12a9e-143">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="12a9e-144">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="12a9e-144">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="12a9e-145">将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。</span><span class="sxs-lookup"><span data-stu-id="12a9e-145">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="12a9e-146">此示例演示如何使用 [COLLATE](/sql/t-sql/statements/collations) 子句来指定排序规则名称。</span><span class="sxs-lookup"><span data-stu-id="12a9e-146">This example shows how to use the [COLLATE](/sql/t-sql/statements/collations) clause to specify a collation name.</span></span> <span data-ttu-id="12a9e-147">此示例创建使用 `MyOptionsTest` 排序规则的数据库 `Latin1_General_100_CS_AS_SC` 。</span><span class="sxs-lookup"><span data-stu-id="12a9e-147">The example creates the database `MyOptionsTest` that uses the `Latin1_General_100_CS_AS_SC` collation.</span></span> <span data-ttu-id="12a9e-148">在创建数据库后，执行 `SELECT` 语句以验证设置。</span><span class="sxs-lookup"><span data-stu-id="12a9e-148">After you create the database, execute the `SELECT` statement to verify the setting.</span></span>  
  
```sql  
USE master;  
GO  
IF DB_ID (N'MyOptionsTest') IS NOT NULL  
DROP DATABASE MyOptionsTest;  
GO  
CREATE DATABASE MyOptionsTest  
COLLATE Latin1_General_100_CS_AS_SC;  
GO  
  
--Verify the collation setting.  
SELECT name, collation_name  
FROM sys.databases  
WHERE name = N'MyOptionsTest';  
GO  
  
```  
  
#### <a name="to-change-the-database-collation"></a><span data-ttu-id="12a9e-149">更改数据库排序规则</span><span class="sxs-lookup"><span data-stu-id="12a9e-149">To change the database collation</span></span>  
  
1.  <span data-ttu-id="12a9e-150">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="12a9e-150">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="12a9e-151">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="12a9e-151">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="12a9e-152">将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。</span><span class="sxs-lookup"><span data-stu-id="12a9e-152">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="12a9e-153">此示例说明如何在 [ALTER DATABASE](/sql/t-sql/statements/collations) 语句中使用 [COLLATE](/sql/t-sql/statements/alter-database-transact-sql) 子句来更改排序规则名称。</span><span class="sxs-lookup"><span data-stu-id="12a9e-153">This example shows how to use the [COLLATE](/sql/t-sql/statements/collations) clause in an [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) statement to change the collation name.</span></span> <span data-ttu-id="12a9e-154">执行 `SELECT` 语句以验证更改。</span><span class="sxs-lookup"><span data-stu-id="12a9e-154">Execute the `SELECT` statement to verify the change.</span></span>  
  
```sql  
USE master;  
GO  
ALTER DATABASE MyOptionsTest  
COLLATE French_CI_AS ;  
GO  
  
--Verify the collation setting.  
SELECT name, collation_name  
FROM sys.databases  
WHERE name = N'MyOptionsTest';  
GO  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="12a9e-155">另请参阅</span><span class="sxs-lookup"><span data-stu-id="12a9e-155">See Also</span></span>  
 <span data-ttu-id="12a9e-156">[排序规则和 Unicode 支持](collation-and-unicode-support.md) </span><span class="sxs-lookup"><span data-stu-id="12a9e-156">[Collation and Unicode Support](collation-and-unicode-support.md) </span></span>  
 <span data-ttu-id="12a9e-157">[sys.fn_helpcollations (Transact-SQL)](/sql/relational-databases/system-functions/sys-fn-helpcollations-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="12a9e-157">[sys.fn_helpcollations &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-helpcollations-transact-sql) </span></span>  
 <span data-ttu-id="12a9e-158">[sys.databases (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="12a9e-158">[sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) </span></span>  
 <span data-ttu-id="12a9e-159">[SQL Server 排序规则名称 (Transact-SQL)](/sql/t-sql/statements/sql-server-collation-name-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="12a9e-159">[SQL Server Collation Name &#40;Transact-SQL&#41;](/sql/t-sql/statements/sql-server-collation-name-transact-sql) </span></span>  
 <span data-ttu-id="12a9e-160">[Windows 排序规则名称 (Transact-SQL)](/sql/t-sql/statements/windows-collation-name-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="12a9e-160">[Windows Collation Name &#40;Transact-SQL&#41;](/sql/t-sql/statements/windows-collation-name-transact-sql) </span></span>  
 <span data-ttu-id="12a9e-161">[COLLATE (Transact-SQL)](/sql/t-sql/statements/collations) </span><span class="sxs-lookup"><span data-stu-id="12a9e-161">[COLLATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/collations) </span></span>  
 <span data-ttu-id="12a9e-162">[排序规则优先级 (Transact-SQL)](/sql/t-sql/statements/collation-precedence-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="12a9e-162">[Collation Precedence &#40;Transact-SQL&#41;](/sql/t-sql/statements/collation-precedence-transact-sql) </span></span>  
 <span data-ttu-id="12a9e-163">[CREATE TABLE (Transact-SQL)](/sql/t-sql/statements/create-table-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="12a9e-163">[CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) </span></span>  
 <span data-ttu-id="12a9e-164">[CREATE DATABASE (SQL Server Transact-SQL)](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="12a9e-164">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span></span>  
 <span data-ttu-id="12a9e-165">[ALTER TABLE (Transact-SQL)](/sql/t-sql/statements/alter-table-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="12a9e-165">[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) </span></span>  
 [<span data-ttu-id="12a9e-166">ALTER DATABASE (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="12a9e-166">ALTER DATABASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql)  
  
  
