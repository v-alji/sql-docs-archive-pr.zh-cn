---
title: 查看存储过程的依赖关系 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- stored procedures [SQL Server], dependencies
- displaying stored procedure dependencies
- viewing stored procedure dependencies
ms.assetid: 6ae0a369-1bc7-4ae4-be89-2b483697cd1f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 790684035d2db3b697fb8b718c96182eda8f1186
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591847"
---
# <a name="view-the-dependencies-of-a-stored-procedure"></a><span data-ttu-id="ca91e-102">查看存储过程的依赖关系</span><span class="sxs-lookup"><span data-stu-id="ca91e-102">View the Dependencies of a Stored Procedure</span></span>
    
##  <a name="this-topic-describes-how-to-view-stored-procedure-dependencies-in-sscurrent-by-using-ssmanstudiofull-or-tsql"></a><a name="Top"></a><span data-ttu-id="ca91e-103">本主题介绍了如何使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 [!INCLUDE[tsql](../../includes/tsql-md.md)] 在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中查看存储过程依赖关系。</span><span class="sxs-lookup"><span data-stu-id="ca91e-103">This topic describes how to view stored procedure dependencies in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
-   <span data-ttu-id="ca91e-104">**开始之前：** [安全性](#Security)</span><span class="sxs-lookup"><span data-stu-id="ca91e-104">**Before you begin:**  [Security](#Security)</span></span>  
  
-   <span data-ttu-id="ca91e-105">要查看过程的依赖关系，请使用：[SQL Server Management Studio](#SSMSProcedure)、[Transact-SQL](#TsqlProcedure)</span><span class="sxs-lookup"><span data-stu-id="ca91e-105">**To view the dependencies of a procedure, using:**  [SQL Server Management Studio](#SSMSProcedure), [Transact-SQL](#TsqlProcedure)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ca91e-106">开始之前</span><span class="sxs-lookup"><span data-stu-id="ca91e-106">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ca91e-107">Security</span><span class="sxs-lookup"><span data-stu-id="ca91e-107">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ca91e-108">权限</span><span class="sxs-lookup"><span data-stu-id="ca91e-108">Permissions</span></span>  
 <span data-ttu-id="ca91e-109">系统函数：`sys.dm_sql_referencing_entities`</span><span class="sxs-lookup"><span data-stu-id="ca91e-109">System Function: `sys.dm_sql_referencing_entities`</span></span>  
 <span data-ttu-id="ca91e-110">要求对被引用的实体拥有 CONTROL 权限，并且对 sys.dm_sql_referencing_entities 拥有 SELECT 权限。</span><span class="sxs-lookup"><span data-stu-id="ca91e-110">Requires CONTROL permission on the referenced entity and SELECT permission on sys.dm_sql_referencing_entities.</span></span> <span data-ttu-id="ca91e-111">当被引用的实体是分区函数时，要求对数据库拥有 CONTROL 权限。</span><span class="sxs-lookup"><span data-stu-id="ca91e-111">When the referenced entity is a partition function, CONTROL permission on the database is required.</span></span> <span data-ttu-id="ca91e-112">默认情况下，SELECT 权限授予 public。</span><span class="sxs-lookup"><span data-stu-id="ca91e-112">By default, SELECT permission is granted to public.</span></span>  
  
 <span data-ttu-id="ca91e-113">系统函数：`sys.dm_sql_referenced_entities`</span><span class="sxs-lookup"><span data-stu-id="ca91e-113">System Function: `sys.dm_sql_referenced_entities`</span></span>  
 <span data-ttu-id="ca91e-114">要求对 sys.dm_sql_referenced_entities 拥有 SELECT 权限并对引用实体拥有 VIEW DEFINITION 权限。</span><span class="sxs-lookup"><span data-stu-id="ca91e-114">Requires SELECT permission on sys.dm_sql_referenced_entities and VIEW DEFINITION permission on the referencing entity.</span></span> <span data-ttu-id="ca91e-115">默认情况下，SELECT 权限授予 public。</span><span class="sxs-lookup"><span data-stu-id="ca91e-115">By default, SELECT permission is granted to public.</span></span> <span data-ttu-id="ca91e-116">要求对数据库拥有 VIEW DEFINITION 权限或 ALTER DATABASE DDL TRIGGER 权限（当引用实体为数据库级 DDL 触发器时）。</span><span class="sxs-lookup"><span data-stu-id="ca91e-116">Requires VIEW DEFINITION permission on the database or ALTER DATABASE DDL TRIGGER permission on the database when the referencing entity is a database-level DDL trigger.</span></span> <span data-ttu-id="ca91e-117">当引用实体为服务器级 DDL 触发器时，要求对服务器拥有 VIEW ANY DEFINITION 权限。</span><span class="sxs-lookup"><span data-stu-id="ca91e-117">Requires VIEW ANY DEFINITION permission on the server when the referencing entity is a server-level DDL trigger.</span></span>  
  
 <span data-ttu-id="ca91e-118">对象目录视图：`sys.sql_expression_dependencies`</span><span class="sxs-lookup"><span data-stu-id="ca91e-118">Object Catalog View: `sys.sql_expression_dependencies`</span></span>  
 <span data-ttu-id="ca91e-119">要求对数据库具有 VIEW DEFINITION 权限，并对数据库的 sys.sql_expression_dependencies 具有 SELECT 权限。</span><span class="sxs-lookup"><span data-stu-id="ca91e-119">Requires VIEW DEFINITION permission on the database and SELECT permission on sys.sql_expression_dependencies for the database.</span></span> <span data-ttu-id="ca91e-120">默认情况下，SELECT 权限仅授予 db_owner 固定数据库角色的成员。</span><span class="sxs-lookup"><span data-stu-id="ca91e-120">By default, SELECT permission is granted only to members of the db_owner fixed database role.</span></span> <span data-ttu-id="ca91e-121">将 SELECT 和 VIEW DEFINITION 权限授予其他用户时，被授权者可以查看数据库中的所有依赖关系。</span><span class="sxs-lookup"><span data-stu-id="ca91e-121">When SELECT and VIEW DEFINITION permissions are granted to another user, the grantee can view all dependencies in the database.</span></span>  
  
##  <a name="how-to-view-the-dependencies-of-a-stored-procedure"></a><a name="Procedures"></a> <span data-ttu-id="ca91e-122">如何查看存储过程的依赖关系</span><span class="sxs-lookup"><span data-stu-id="ca91e-122">How to View the Dependencies of a Stored Procedure</span></span>  
 <span data-ttu-id="ca91e-123">您可以使用以下项之一：</span><span class="sxs-lookup"><span data-stu-id="ca91e-123">You can use one of the following:</span></span>  
  
-   [<span data-ttu-id="ca91e-124">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ca91e-124">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
-   [<span data-ttu-id="ca91e-125">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ca91e-125">Transact-SQL</span></span>](#TsqlProcedure)  
  
###  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="ca91e-126">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ca91e-126">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="ca91e-127">**在对象资源管理器中查看过程的依赖关系**</span><span class="sxs-lookup"><span data-stu-id="ca91e-127">**To view the dependencies of a procedure in Object Explorer**</span></span>  
  
1.  <span data-ttu-id="ca91e-128">在对象资源管理器中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的实例，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="ca91e-128">In Object Explorer, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="ca91e-129">展开 **“数据库”** 、过程所属的数据库以及 **“可编程性”** 。</span><span class="sxs-lookup"><span data-stu-id="ca91e-129">Expand **Databases**, expand the database in which the procedure belongs, and then expand **Programmability**.</span></span>  
  
3.  <span data-ttu-id="ca91e-130">展开“存储过程”，右键单击此过程，再单击“查看依赖关系”。</span><span class="sxs-lookup"><span data-stu-id="ca91e-130">Expand **Stored Procedures**, right-click the procedure and then click **View Dependencies**.</span></span>  
  
4.  <span data-ttu-id="ca91e-131">查看依赖于过程的对象的列表。</span><span class="sxs-lookup"><span data-stu-id="ca91e-131">View the list of objects that depend on the procedure.</span></span>  
  
5.  <span data-ttu-id="ca91e-132">查看过程所依赖的对象的列表。</span><span class="sxs-lookup"><span data-stu-id="ca91e-132">View the list of objects on which the procedure depends.</span></span>  
  
6.  <span data-ttu-id="ca91e-133">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="ca91e-133">Click **OK**.</span></span>  
  
###  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="ca91e-134">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ca91e-134">Using Transact-SQL</span></span>  
 <span data-ttu-id="ca91e-135">**在查询编辑器中查看过程的依赖关系**</span><span class="sxs-lookup"><span data-stu-id="ca91e-135">**To view the dependencies of a procedure in Query Editor**</span></span>  
  
 <span data-ttu-id="ca91e-136">系统函数：`sys.dm_sql_referencing_entities`</span><span class="sxs-lookup"><span data-stu-id="ca91e-136">System Function: `sys.dm_sql_referencing_entities`</span></span>  
 <span data-ttu-id="ca91e-137">此函数用于显示依赖于过程的对象。</span><span class="sxs-lookup"><span data-stu-id="ca91e-137">This function is used to display the objects that depend on a procedure.</span></span>  
  
1.  <span data-ttu-id="ca91e-138">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的实例，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="ca91e-138">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="ca91e-139">展开 **“数据库”** ，然后展开过程所属的数据库。</span><span class="sxs-lookup"><span data-stu-id="ca91e-139">Expand **Databases**, expand the database in which the procedure belongs.</span></span>  
  
3.  <span data-ttu-id="ca91e-140">在 **“文件”** 菜单下，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="ca91e-140">Click on **New Query** under the **File** menu.</span></span>  
  
4.  <span data-ttu-id="ca91e-141">复制以下示例并将其粘贴到查询编辑器中。</span><span class="sxs-lookup"><span data-stu-id="ca91e-141">Copy and paste the following examples into the query editor.</span></span> <span data-ttu-id="ca91e-142">第一个示例创建 `uspVendorAllInfo` 过程，该过程返回 [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] 数据库中所有供应商的名称、所提供的产品、信用等级以及可用性。</span><span class="sxs-lookup"><span data-stu-id="ca91e-142">The first example creates the `uspVendorAllInfo` procedure, which returns the names of all the vendors in the [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] database, the products they supply, their credit ratings, and their availability.</span></span>  
  
     [!code-sql[ProcedureDDL#CreateProc8](../../snippets/tsql/SQL14/tsql/procedureddl/transact-sql/createproc.sql#createproc8)]  
  
5.  <span data-ttu-id="ca91e-143">创建该过程后，第二个示例使用 sys.dm_sql_referencing_entities 函数来显示依赖于该过程的对象。</span><span class="sxs-lookup"><span data-stu-id="ca91e-143">After the procedure is created, the second example uses the sys.dm_sql_referencing_entities function to display the objects that depend on the procedure.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT referencing_schema_name, referencing_entity_name, referencing_id, referencing_class_desc, is_caller_dependent  
    FROM sys.dm_sql_referencing_entities ('Purchasing.uspVendorAllInfo', 'OBJECT');   
    GO  
  
    ```  
  
 <span data-ttu-id="ca91e-144">系统函数：`sys.dm_sql_referenced_entities`</span><span class="sxs-lookup"><span data-stu-id="ca91e-144">System Function: `sys.dm_sql_referenced_entities`</span></span>  
 <span data-ttu-id="ca91e-145">此函数用于显示过程所依赖的对象。</span><span class="sxs-lookup"><span data-stu-id="ca91e-145">This function is used to display the objects a procedure depends on.</span></span>  
  
1.  <span data-ttu-id="ca91e-146">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的实例，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="ca91e-146">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="ca91e-147">展开 **“数据库”** ，然后展开过程所属的数据库。</span><span class="sxs-lookup"><span data-stu-id="ca91e-147">Expand **Databases**, expand the database in which the procedure belongs.</span></span>  
  
3.  <span data-ttu-id="ca91e-148">在 **“文件”** 菜单下，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="ca91e-148">Click on **New Query** under the **File** menu.</span></span>  
  
4.  <span data-ttu-id="ca91e-149">复制以下示例并将其粘贴到查询编辑器中。</span><span class="sxs-lookup"><span data-stu-id="ca91e-149">Copy and paste the following examples into the query editor.</span></span> <span data-ttu-id="ca91e-150">第一个示例创建 `uspVendorAllInfo` 过程，该过程返回 [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] 数据库中所有供应商的名称、所提供的产品、信用等级以及可用性。</span><span class="sxs-lookup"><span data-stu-id="ca91e-150">The first example creates the `uspVendorAllInfo` procedure, which returns the names of all the vendors in the [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] database, the products they supply, their credit ratings, and their availability.</span></span>  
  
     [!code-sql[ProcedureDDL#CreateProc8](../../snippets/tsql/SQL14/tsql/procedureddl/transact-sql/createproc.sql#createproc8)]  
  
5.  <span data-ttu-id="ca91e-151">创建该过程后，第二个示例使用 sys.dm_sql_referenced_entities 函数来显示该过程依赖的对象。</span><span class="sxs-lookup"><span data-stu-id="ca91e-151">After the procedure is created, the second example uses the sys.dm_sql_referenced_entities function to display the objects that the procedure depends on.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT referenced_schema_name, referenced_entity_name,  
    referenced_minor_name,referenced_minor_id, referenced_class_desc,  
    is_caller_dependent, is_ambiguous  
    FROM sys.dm_sql_referencing_entities ('Purchasing.uspVendorAllInfo', 'OBJECT');  
    GO  
    ```  
  
 <span data-ttu-id="ca91e-152">对象目录视图：`sys.sql_expression_dependencies`</span><span class="sxs-lookup"><span data-stu-id="ca91e-152">Object Catalog View: `sys.sql_expression_dependencies`</span></span>  
 <span data-ttu-id="ca91e-153">此视图可以用于显示过程所依赖的对象或依赖于过程的对象。</span><span class="sxs-lookup"><span data-stu-id="ca91e-153">This view can be used to display objects that a procedure depends on or that depend on a procedure.</span></span>  
  
 <span data-ttu-id="ca91e-154">显示依赖于过程的对象。</span><span class="sxs-lookup"><span data-stu-id="ca91e-154">Displaying the objects that depend on a procedure.</span></span>  
 1.  <span data-ttu-id="ca91e-155">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的实例，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="ca91e-155">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="ca91e-156">展开 **“数据库”** ，然后展开过程所属的数据库。</span><span class="sxs-lookup"><span data-stu-id="ca91e-156">Expand **Databases**, expand the database in which the procedure belongs.</span></span>  
  
3.  <span data-ttu-id="ca91e-157">在 **“文件”** 菜单下，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="ca91e-157">Click on **New Query** under the **File** menu.</span></span>  
  
4.  <span data-ttu-id="ca91e-158">复制以下示例并将其粘贴到查询编辑器中。</span><span class="sxs-lookup"><span data-stu-id="ca91e-158">Copy and paste the following examples into the query editor.</span></span> <span data-ttu-id="ca91e-159">第一个示例创建 `uspVendorAllInfo` 过程，该过程返回 [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] 数据库中所有供应商的名称、所提供的产品、信用等级以及可用性。</span><span class="sxs-lookup"><span data-stu-id="ca91e-159">The first example creates the `uspVendorAllInfo` procedure, which returns the names of all the vendors in the [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] database, the products they supply, their credit ratings, and their availability.</span></span>  
  
     [!code-sql[ProcedureDDL#CreateProc8](../../snippets/tsql/SQL14/tsql/procedureddl/transact-sql/createproc.sql#createproc8)]  
  
5.  <span data-ttu-id="ca91e-160">创建该过程后，第二个示例使用 sys.sql_expression_dependencies 视图来显示依赖于该过程的对象。</span><span class="sxs-lookup"><span data-stu-id="ca91e-160">After the procedure is created, the second example uses the sys.sql_expression_dependencies view to display the objects that depend on the procedure.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT OBJECT_SCHEMA_NAME ( referencing_id ) AS referencing_schema_name,  
        OBJECT_NAME(referencing_id) AS referencing_entity_name,   
        o.type_desc AS referencing_desciption,   
        COALESCE(COL_NAME(referencing_id, referencing_minor_id), '(n/a)') AS referencing_minor_id,   
        referencing_class_desc, referenced_class_desc,  
        referenced_server_name, referenced_database_name, referenced_schema_name,  
        referenced_entity_name,   
        COALESCE(COL_NAME(referenced_id, referenced_minor_id), '(n/a)') AS referenced_column_name,  
        is_caller_dependent, is_ambiguous  
    FROM sys.sql_expression_dependencies AS sed  
    INNER JOIN sys.objects AS o ON sed.referencing_id = o.object_id  
    WHERE referenced_id = OBJECT_ID(N'Purchasing.uspVendorAllInfo')  
    GO  
    ```  
  
 <span data-ttu-id="ca91e-161">显示过程所依赖的对象。</span><span class="sxs-lookup"><span data-stu-id="ca91e-161">Displaying the objects a procedure depends on.</span></span>  
 1.  <span data-ttu-id="ca91e-162">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的实例，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="ca91e-162">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="ca91e-163">展开 **“数据库”** ，然后展开过程所属的数据库。</span><span class="sxs-lookup"><span data-stu-id="ca91e-163">Expand **Databases**, expand the database in which the procedure belongs.</span></span>  
  
3.  <span data-ttu-id="ca91e-164">在 **“文件”** 菜单下，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="ca91e-164">Click on **New Query** under the **File** menu.</span></span>  
  
4.  <span data-ttu-id="ca91e-165">复制以下示例并将其粘贴到查询编辑器中。</span><span class="sxs-lookup"><span data-stu-id="ca91e-165">Copy and paste the following examples into the query editor.</span></span> <span data-ttu-id="ca91e-166">第一个示例创建 `uspVendorAllInfo` 过程，该过程返回 [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] 数据库中所有供应商的名称、所提供的产品、信用等级以及可用性。</span><span class="sxs-lookup"><span data-stu-id="ca91e-166">The first example creates the `uspVendorAllInfo` procedure, which returns the names of all the vendors in the [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] database, the products they supply, their credit ratings, and their availability.</span></span>  
  
     [!code-sql[ProcedureDDL#CreateProc8](../../snippets/tsql/SQL14/tsql/procedureddl/transact-sql/createproc.sql#createproc8)]  
  
5.  <span data-ttu-id="ca91e-167">创建该过程后，第二个示例使用 sys.sql_expression_dependencies 视图来显示该过程依赖的对象。</span><span class="sxs-lookup"><span data-stu-id="ca91e-167">After the procedure is created, the second example uses the sys.sql_expression_dependencies view to display the objects the procedure depends on.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT OBJECT_NAME(referencing_id) AS referencing_entity_name,   
        o.type_desc AS referencing_desciption,   
        COALESCE(COL_NAME(referencing_id, referencing_minor_id), '(n/a)') AS referencing_minor_id,   
        referencing_class_desc, referenced_class_desc,  
        referenced_server_name, referenced_database_name, referenced_schema_name,  
        referenced_entity_name,   
        COALESCE(COL_NAME(referenced_id, referenced_minor_id), '(n/a)') AS referenced_column_name,  
        is_caller_dependent, is_ambiguous  
    FROM sys.sql_expression_dependencies AS sed  
    INNER JOIN sys.objects AS o ON sed.referencing_id = o.object_id  
    WHERE referencing_id = OBJECT_ID(N'Purchasing.uspVendorAllInfo')  
    GO  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="ca91e-168">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ca91e-168">See Also</span></span>  
 <span data-ttu-id="ca91e-169">[重命名存储过程](rename-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="ca91e-169">[Rename a Stored Procedure](rename-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="ca91e-170">[sys.dm_sql_referencing_entities (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ca91e-170">[sys.dm_sql_referencing_entities &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql) </span></span>  
 <span data-ttu-id="ca91e-171">[sys.dm_sql_referenced_entities (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ca91e-171">[sys.dm_sql_referenced_entities &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql) </span></span>  
 [<span data-ttu-id="ca91e-172">sys.sql_expression_dependencies (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="ca91e-172">sys.sql_expression_dependencies &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql)  
  
  
