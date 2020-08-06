---
title: 重命名存储过程 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- stored procedures [SQL Server], renaming
- renaming stored procedures
ms.assetid: 5d2e4c68-7e0b-4405-8919-f5b203e46770
author: stevestein
ms.author: sstein
ms.openlocfilehash: 02e1acb528a32ef242e160e0ce5dd0267237c876
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591852"
---
# <a name="rename-a-stored-procedure"></a><span data-ttu-id="41c02-102">重命名存储过程</span><span class="sxs-lookup"><span data-stu-id="41c02-102">Rename a Stored Procedure</span></span>
  <span data-ttu-id="41c02-103">本主题介绍如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中重命名存储过程。</span><span class="sxs-lookup"><span data-stu-id="41c02-103">This topic describes how to rename a stored procedure in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="41c02-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="41c02-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="41c02-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="41c02-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="41c02-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="41c02-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="41c02-107">安全性</span><span class="sxs-lookup"><span data-stu-id="41c02-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="41c02-108">**若要重命名存储过程，请使用：**</span><span class="sxs-lookup"><span data-stu-id="41c02-108">**To rename a stored procedure, using:**</span></span>  
  
     [<span data-ttu-id="41c02-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="41c02-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="41c02-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="41c02-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="41c02-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="41c02-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="41c02-112">限制和局限</span><span class="sxs-lookup"><span data-stu-id="41c02-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="41c02-113">过程名称必须符合 [标识符](../databases/database-identifiers.md)规则。</span><span class="sxs-lookup"><span data-stu-id="41c02-113">Procedure names must comply with the rules for [identifiers](../databases/database-identifiers.md).</span></span>  
  
-   <span data-ttu-id="41c02-114">重命名存储过程将不会更改 **sys.sql_modules** 目录视图的定义列中相应对象名的名称。</span><span class="sxs-lookup"><span data-stu-id="41c02-114">Renaming a stored procedure will not change the name of the corresponding object name in the definition column of the **sys.sql_modules** catalog view.</span></span> <span data-ttu-id="41c02-115">因此，我们建议不要重命名此对象类型。</span><span class="sxs-lookup"><span data-stu-id="41c02-115">Therefore, we recommend that you do not rename this object type.</span></span> <span data-ttu-id="41c02-116">而是删除存储过程，然后使用新名称重新创建该存储过程。</span><span class="sxs-lookup"><span data-stu-id="41c02-116">Instead, drop and re-create the stored procedure with its new name.</span></span>  
  
-   <span data-ttu-id="41c02-117">在未将对象更新为反映已对过程所做的更改时，更改过程的名称或定义可能导致依赖对象失败。</span><span class="sxs-lookup"><span data-stu-id="41c02-117">Changing the name or definition of a procedure can cause dependent objects to fail when the objects are not updated to reflect the changes that have been made to the procedure.</span></span> <span data-ttu-id="41c02-118">有关详细信息，请参阅 [查看存储过程的依赖关系](view-the-dependencies-of-a-stored-procedure.md)。</span><span class="sxs-lookup"><span data-stu-id="41c02-118">For more information, see [View the Dependencies of a Stored Procedure](view-the-dependencies-of-a-stored-procedure.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="41c02-119">Security</span><span class="sxs-lookup"><span data-stu-id="41c02-119">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="41c02-120">权限</span><span class="sxs-lookup"><span data-stu-id="41c02-120">Permissions</span></span>  
 <span data-ttu-id="41c02-121">CREATE PROCEDURE</span><span class="sxs-lookup"><span data-stu-id="41c02-121">CREATE PROCEDURE</span></span>  
 <span data-ttu-id="41c02-122">要求数据库中的 CREATE PROCEDURE 权限以及对要在其中创建过程的架构的 ALTER 权限，或者要求 **db_ddladmin** 固定数据库角色中的成员身份。</span><span class="sxs-lookup"><span data-stu-id="41c02-122">Requires CREATE PROCEDURE permission in the database and ALTER permission on the schema in which the procedure is being created, or requires membership in the **db_ddladmin** fixed database role.</span></span>  
  
 <span data-ttu-id="41c02-123">ALTER PROCEDURE</span><span class="sxs-lookup"><span data-stu-id="41c02-123">ALTER PROCEDURE</span></span>  
 <span data-ttu-id="41c02-124">要求对过程具有 ALTER 权限，或者要求 **db_ddladmin** 固定数据库角色中的成员身份。</span><span class="sxs-lookup"><span data-stu-id="41c02-124">Requires ALTER permission on the procedure or requires membership in the **db_ddladmin** fixed database role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="41c02-125">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="41c02-125">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-rename-a-stored-procedure"></a><span data-ttu-id="41c02-126">重命名存储过程</span><span class="sxs-lookup"><span data-stu-id="41c02-126">To rename a stored procedure</span></span>  
  
1.  <span data-ttu-id="41c02-127">在对象资源管理器中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的实例，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="41c02-127">In Object Explorer, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="41c02-128">展开 **“数据库”** 、过程所属的数据库以及 **“可编程性”** 。</span><span class="sxs-lookup"><span data-stu-id="41c02-128">Expand **Databases**, expand the database in which the procedure belongs, and then expand **Programmability**.</span></span>  
  
3.  <span data-ttu-id="41c02-129">[确定存储过程的依赖关系](view-the-dependencies-of-a-stored-procedure.md)。</span><span class="sxs-lookup"><span data-stu-id="41c02-129">[Determine the dependencies of the stored procedure](view-the-dependencies-of-a-stored-procedure.md).</span></span>  
  
4.  <span data-ttu-id="41c02-130">展开“存储过程”，右键单击要重命名的过程，再单击“重命名”。</span><span class="sxs-lookup"><span data-stu-id="41c02-130">Expand **Stored Procedures**, right-click the procedure to rename, and then click **Rename**.</span></span>  
  
5.  <span data-ttu-id="41c02-131">修改过程名称。</span><span class="sxs-lookup"><span data-stu-id="41c02-131">Modify the procedure name.</span></span>  
  
6.  <span data-ttu-id="41c02-132">修改在任何相关对象或脚本中引用的过程名称。</span><span class="sxs-lookup"><span data-stu-id="41c02-132">Modify the procedure name referenced in any dependent objects or scripts.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="41c02-133">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="41c02-133">Using Transact-SQL</span></span>  
  
#### <a name="to-rename-a-stored-procedure"></a><span data-ttu-id="41c02-134">重命名存储过程</span><span class="sxs-lookup"><span data-stu-id="41c02-134">To rename a stored procedure</span></span>  
  
1.  <span data-ttu-id="41c02-135">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="41c02-135">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="41c02-136">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="41c02-136">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="41c02-137">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="41c02-137">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="41c02-138">此示例说明如何通过删除过程并使用新名称重新创建该过程来重命名过程。</span><span class="sxs-lookup"><span data-stu-id="41c02-138">This example shows how to rename a procedure by dropping the procedure and re-creating the procedure with a new name.</span></span> <span data-ttu-id="41c02-139">第一个示例将创建 `'HumanResources.uspGetAllEmployeesTest`存储过程。</span><span class="sxs-lookup"><span data-stu-id="41c02-139">The first example creates the stored procedure `'HumanResources.uspGetAllEmployeesTest`.</span></span> <span data-ttu-id="41c02-140">第二个示例将存储过程重命名为 `HumanResources.uspEveryEmployeeTest`。</span><span class="sxs-lookup"><span data-stu-id="41c02-140">The second example renames the stored procedure to `HumanResources.uspEveryEmployeeTest`.</span></span>  
  
```sql  
--Create the stored procedure.  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID ( 'HumanResources.uspGetAllEmployeesTest', 'P' ) IS NOT NULL   
    DROP PROCEDURE HumanResources.uspGetAllEmployeesTest;  
GO  
CREATE PROCEDURE HumanResources.uspGetAllEmployeesTest  
AS  
    SET NOCOUNT ON;  
    SELECT LastName, FirstName, Department  
    FROM HumanResources.vEmployeeDepartmentHistory;  
GO  
  
--Rename the stored procedure.  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID ( 'HumanResources.uspGetAllEmployeesTest', 'P' ) IS NOT NULL   
    DROP PROCEDURE HumanResources.uspGetAllEmployeesTest;  
GO  
CREATE PROCEDURE HumanResources.uspEveryEmployeeTest  
AS  
    SET NOCOUNT ON;  
    SELECT LastName, FirstName, Department  
    FROM HumanResources.vEmployeeDepartmentHistory;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="41c02-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="41c02-141">See Also</span></span>  
 <span data-ttu-id="41c02-142">[ALTER PROCEDURE (Transact-SQL)](/sql/t-sql/statements/alter-procedure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="41c02-142">[ALTER PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-procedure-transact-sql) </span></span>  
 <span data-ttu-id="41c02-143">[CREATE PROCEDURE (Transact-SQL)](/sql/t-sql/statements/create-procedure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="41c02-143">[CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql) </span></span>  
 <span data-ttu-id="41c02-144">[创建存储过程](../stored-procedures/create-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="41c02-144">[Create a Stored Procedure](../stored-procedures/create-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="41c02-145">[修改存储过程](../stored-procedures/modify-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="41c02-145">[Modify a Stored Procedure](../stored-procedures/modify-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="41c02-146">[删除存储过程](../stored-procedures/delete-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="41c02-146">[Delete a Stored Procedure](../stored-procedures/delete-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="41c02-147">[查看存储过程的定义](view-the-definition-of-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="41c02-147">[View the Definition of a Stored Procedure](view-the-definition-of-a-stored-procedure.md) </span></span>  
 [<span data-ttu-id="41c02-148">查看存储过程的依赖关系</span><span class="sxs-lookup"><span data-stu-id="41c02-148">View the Dependencies of a Stored Procedure</span></span>](view-the-dependencies-of-a-stored-procedure.md)  
  
  
