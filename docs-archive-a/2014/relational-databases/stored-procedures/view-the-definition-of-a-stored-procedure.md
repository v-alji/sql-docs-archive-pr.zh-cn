---
title: 查看存储过程的定义 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- stored procedures [SQL Server], viewing
- definition of stored procedure
- viewing stored procedures
- displaying stored procedures
ms.assetid: 93318587-a0c5-4788-946f-3b5dc8372ea9
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4da455d38f984b08ee1f396f26cd4cc85411be92
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586577"
---
# <a name="view-the-definition-of-a-stored-procedure"></a><span data-ttu-id="982f8-102">查看存储过程的定义</span><span class="sxs-lookup"><span data-stu-id="982f8-102">View the Definition of a Stored Procedure</span></span>
    
##  <a name="you-can-view-the-definition-of-a-stored-procedure-in-ssmanstudiofull-using-object-explorer-menu-options-or-in-the-query-editor-using-tsql-this-topic-describes-how-to-view-the-definition-of-procedure-in-object-explorer-and-by-using-a-system-stored-procedure-system-function-and-object-catalog-view-in-the-query-editor"></a><a name="Top"></a><span data-ttu-id="982f8-103">您可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 对象资源管理器菜单选项或在查询编辑器中使用来查看存储过程的定义 [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="982f8-103">You can view the definition of a stored procedure in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] using Object Explorer menu options or in the Query Editor using [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="982f8-104">本主题介绍如何在对象资源管理器中查看过程的定义，以及如何在查询编辑器中使用系统存储过程、系统函数和对象目录视图来查看过程的定义。</span><span class="sxs-lookup"><span data-stu-id="982f8-104">This topic describes how to view the definition of procedure in Object Explorer and by using a system stored procedure, system function, and object catalog view in the Query Editor.</span></span>  
  
-   <span data-ttu-id="982f8-105">**开始之前：** [安全性](#Security)</span><span class="sxs-lookup"><span data-stu-id="982f8-105">**Before you begin:**  [Security](#Security)</span></span>  
  
-   <span data-ttu-id="982f8-106">要查看过程的定义，请使用：[SQL Server Management Studio](#SSMSProcedure)、[Transact-SQL](#TsqlProcedure)</span><span class="sxs-lookup"><span data-stu-id="982f8-106">**To view the definition of a procedure, using:**  [SQL Server Management Studio](#SSMSProcedure), [Transact-SQL](#TsqlProcedure)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="982f8-107">开始之前</span><span class="sxs-lookup"><span data-stu-id="982f8-107">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="982f8-108">Security</span><span class="sxs-lookup"><span data-stu-id="982f8-108">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="982f8-109">权限</span><span class="sxs-lookup"><span data-stu-id="982f8-109">Permissions</span></span>  
 <span data-ttu-id="982f8-110">系统存储过程：`sp_helptext`</span><span class="sxs-lookup"><span data-stu-id="982f8-110">System Stored Procedure: `sp_helptext`</span></span>  
 <span data-ttu-id="982f8-111">要求 **公共** 角色具有成员身份。</span><span class="sxs-lookup"><span data-stu-id="982f8-111">Requires membership in the **public** role.</span></span> <span data-ttu-id="982f8-112">系统对象定义对所有用户可见。</span><span class="sxs-lookup"><span data-stu-id="982f8-112">System object definitions are publicly visible.</span></span> <span data-ttu-id="982f8-113">用户对象的定义对于对象所有者或具有下列任一权限的被授权者可见：ALTER、CONTROL、TAKE OWNERSHIP 或 VIEW DEFINITION。</span><span class="sxs-lookup"><span data-stu-id="982f8-113">The definition of user objects is visible to the object owner or grantees that have any one of the following permissions: ALTER, CONTROL, TAKE OWNERSHIP, or VIEW DEFINITION.</span></span>  
  
 <span data-ttu-id="982f8-114">系统函数：`OBJECT_DEFINITION`</span><span class="sxs-lookup"><span data-stu-id="982f8-114">System Function: `OBJECT_DEFINITION`</span></span>  
 <span data-ttu-id="982f8-115">系统对象定义对所有用户可见。</span><span class="sxs-lookup"><span data-stu-id="982f8-115">System object definitions are publicly visible.</span></span> <span data-ttu-id="982f8-116">用户对象的定义对于对象所有者或具有下列任一权限的被授权者可见：ALTER、CONTROL、TAKE OWNERSHIP 或 VIEW DEFINITION。</span><span class="sxs-lookup"><span data-stu-id="982f8-116">The definition of user objects is visible to the object owner or grantees that have any one of the following permissions: ALTER, CONTROL, TAKE OWNERSHIP, or VIEW DEFINITION.</span></span> <span data-ttu-id="982f8-117">**db_owner**、 **db_ddladmin**和 **db_securityadmin** 固定数据库角色的成员隐式具有这些权限。</span><span class="sxs-lookup"><span data-stu-id="982f8-117">These permissions are implicitly held by members of the **db_owner**, **db_ddladmin**, and **db_securityadmin** fixed database roles.</span></span>  
  
 <span data-ttu-id="982f8-118">对象目录视图：`sys.sql_modules`</span><span class="sxs-lookup"><span data-stu-id="982f8-118">Object Catalog View: `sys.sql_modules`</span></span>  
 <span data-ttu-id="982f8-119">目录视图中仅显示用户拥有的安全对象的元数据，或用户对其拥有某些权限的安全对象的元数据。</span><span class="sxs-lookup"><span data-stu-id="982f8-119">The visibility of the metadata in catalog views is limited to securables that a user either owns or on which the user has been granted some permission.</span></span> <span data-ttu-id="982f8-120">有关详细信息，请参阅 [Metadata Visibility Configuration](../security/metadata-visibility-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="982f8-120">For more information, see [Metadata Visibility Configuration](../security/metadata-visibility-configuration.md).</span></span>  
  
##  <a name="how-to-view-the-definition-of-a-stored-procedure"></a><a name="Procedures"></a> <span data-ttu-id="982f8-121">如何查看存储过程的定义</span><span class="sxs-lookup"><span data-stu-id="982f8-121">How to View the Definition of a Stored Procedure</span></span>  
 <span data-ttu-id="982f8-122">您可以使用以下项之一：</span><span class="sxs-lookup"><span data-stu-id="982f8-122">You can use one of the following:</span></span>  
  
-   [<span data-ttu-id="982f8-123">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="982f8-123">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
-   [<span data-ttu-id="982f8-124">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="982f8-124">Transact-SQL</span></span>](#TsqlProcedure)  
  
###  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="982f8-125">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="982f8-125">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="982f8-126">**在对象资源管理器中查看过程的定义**</span><span class="sxs-lookup"><span data-stu-id="982f8-126">**To view the definition a procedure in Object Explorer**</span></span>  
  
1.  <span data-ttu-id="982f8-127">在对象资源管理器中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的实例，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="982f8-127">In Object Explorer, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="982f8-128">展开 **“数据库”** 、过程所属的数据库以及 **“可编程性”** 。</span><span class="sxs-lookup"><span data-stu-id="982f8-128">Expand **Databases**, expand the database in which the procedure belongs, and then expand **Programmability**.</span></span>  
  
3.  <span data-ttu-id="982f8-129">展开“存储过程”，右键单击该过程，再单击“编写存储过程脚本为”，然后单击下列选项之一： “CREATE 到”、“ALTER 到”或“DROP 和 CREATE 到”。</span><span class="sxs-lookup"><span data-stu-id="982f8-129">Expand **Stored Procedures**, right-click the procedure and then click **Script Stored Procedure as**, and then click one of the following: **Create To**, **Alter To**, or **Drop and Create To**.</span></span>  
  
4.  <span data-ttu-id="982f8-130">选择“新建查询编辑器窗口”。</span><span class="sxs-lookup"><span data-stu-id="982f8-130">Select **New Query Editor Window**.</span></span> <span data-ttu-id="982f8-131">这将显示过程定义。</span><span class="sxs-lookup"><span data-stu-id="982f8-131">This will display the procedure definition.</span></span>  
  
###  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="982f8-132">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="982f8-132">Using Transact-SQL</span></span>  
 <span data-ttu-id="982f8-133">**在查询编辑器中查看过程的定义**</span><span class="sxs-lookup"><span data-stu-id="982f8-133">**To view the definition of a procedure in Query Editor**</span></span>  
  
 <span data-ttu-id="982f8-134">系统存储过程：`sp_helptext`</span><span class="sxs-lookup"><span data-stu-id="982f8-134">System Stored Procedure: `sp_helptext`</span></span>  
 1.  <span data-ttu-id="982f8-135">在对象资源管理器中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="982f8-135">In Object Explorer, connect to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="982f8-136">在工具栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="982f8-136">On the toolbar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="982f8-137">在查询窗口中，输入以下使用 `sp_helptext` 系统存储过程的语句。</span><span class="sxs-lookup"><span data-stu-id="982f8-137">In the query window, enter the following statement that uses the `sp_helptext` system stored procedure.</span></span> <span data-ttu-id="982f8-138">更改数据库名称和存储过程名称以引用所需的数据库和存储过程。</span><span class="sxs-lookup"><span data-stu-id="982f8-138">Change the database name and stored procedure name to reference the database and stored procedure that you want.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    EXEC sp_helptext N'AdventureWorks2012.dbo.uspLogError';  
    ```  
  
 <span data-ttu-id="982f8-139">系统函数：`OBJECT_DEFINITION`</span><span class="sxs-lookup"><span data-stu-id="982f8-139">System Function: `OBJECT_DEFINITION`</span></span>  
 1.  <span data-ttu-id="982f8-140">在对象资源管理器中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="982f8-140">In Object Explorer, connect to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="982f8-141">在工具栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="982f8-141">On the toolbar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="982f8-142">在查询窗口中，输入以下使用 `OBJECT_DEFINITION` 系统函数的语句。</span><span class="sxs-lookup"><span data-stu-id="982f8-142">In the query window, enter the following statements that use the `OBJECT_DEFINITION` system function.</span></span> <span data-ttu-id="982f8-143">更改数据库名称和存储过程名称以引用所需的数据库和存储过程。</span><span class="sxs-lookup"><span data-stu-id="982f8-143">Change the database name and stored procedure name to reference the database and stored procedure that you want.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT OBJECT_DEFINITION (OBJECT_ID(N'AdventureWorks2012.dbo.uspLogError'));  
    ```  
  
 <span data-ttu-id="982f8-144">对象目录视图：`sys.sql_modules`</span><span class="sxs-lookup"><span data-stu-id="982f8-144">Object Catalog View: `sys.sql_modules`</span></span>  
 1.  <span data-ttu-id="982f8-145">在对象资源管理器中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="982f8-145">In Object Explorer, connect to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="982f8-146">在工具栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="982f8-146">On the toolbar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="982f8-147">在查询窗口中，输入以下使用 `sys.sql_modules` 目录视图的语句。</span><span class="sxs-lookup"><span data-stu-id="982f8-147">In the query window, enter the following statements that use the `sys.sql_modules` catalog view.</span></span> <span data-ttu-id="982f8-148">更改数据库名称和存储过程名称以引用所需的数据库和存储过程。</span><span class="sxs-lookup"><span data-stu-id="982f8-148">Change the database name and stored procedure name to reference the database and stored procedure that you want.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT definition  
    FROM sys.sql_modules  
    WHERE object_id = (OBJECT_ID(N'AdventureWorks2012.dbo.uspLogError'));  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="982f8-149">另请参阅</span><span class="sxs-lookup"><span data-stu-id="982f8-149">See Also</span></span>  
 <span data-ttu-id="982f8-150">[创建存储过程](create-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="982f8-150">[Create a Stored Procedure](create-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="982f8-151">[修改存储过程](modify-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="982f8-151">[Modify a Stored Procedure](modify-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="982f8-152">[删除存储过程](delete-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="982f8-152">[Delete a Stored Procedure](delete-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="982f8-153">[重命名存储过程](rename-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="982f8-153">[Rename a Stored Procedure](rename-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="982f8-154">[OBJECT_DEFINITION (Transact-SQL)](/sql/t-sql/functions/object-definition-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="982f8-154">[OBJECT_DEFINITION &#40;Transact-SQL&#41;](/sql/t-sql/functions/object-definition-transact-sql) </span></span>  
 <span data-ttu-id="982f8-155">[sys.sql_modules (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="982f8-155">[sys.sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql) </span></span>  
 <span data-ttu-id="982f8-156">[sp_helptext (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-helptext-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="982f8-156">[sp_helptext &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptext-transact-sql) </span></span>  
 [<span data-ttu-id="982f8-157">OBJECT_ID (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="982f8-157">OBJECT_ID &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/object-id-transact-sql)  
  
  
