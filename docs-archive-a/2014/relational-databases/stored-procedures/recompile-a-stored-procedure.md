---
title: 重新编译存储过程 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- sp_recompile
- WITH RECOMPILE clause
- recompiling stored procedures
- stored procedures [SQL Server], recompiling
ms.assetid: b90deb27-0099-4fe7-ba60-726af78f7c18
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2a9bc0e1d4baecb7f4c66b83b57081ed3131123d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591855"
---
# <a name="recompile-a-stored-procedure"></a><span data-ttu-id="7c006-102">重新编译存储过程</span><span class="sxs-lookup"><span data-stu-id="7c006-102">Recompile a Stored Procedure</span></span>
  <span data-ttu-id="7c006-103">本主题介绍如何在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中使用 [!INCLUDE[tsql](../../includes/tsql-md.md)]重新编译存储过程。</span><span class="sxs-lookup"><span data-stu-id="7c006-103">This topic describes how to recompile a stored procedure in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="7c006-104">有三种方法可以执行此操作： `WITH RECOMPILE` 过程定义中的选项或过程的调用时间、 `RECOMPILE` 单个语句的查询提示或使用 `sp_recompile` 系统存储过程。</span><span class="sxs-lookup"><span data-stu-id="7c006-104">There are three ways to do this: `WITH RECOMPILE` option in the procedure definition or when the procedure is called, the `RECOMPILE` query hint on individual statements, or by using the `sp_recompile` system stored procedure.</span></span> <span data-ttu-id="7c006-105">本主题介绍在创建过程定义或执行现有过程时使用 WITH RECOMPILE 选项。</span><span class="sxs-lookup"><span data-stu-id="7c006-105">This topic describes using the WITH RECOMPILE option when creating a procedure definition and executing an existing procedure.</span></span> <span data-ttu-id="7c006-106">它还描述如何使用 sp_recompile 系统存储过程重新编译现有过程。</span><span class="sxs-lookup"><span data-stu-id="7c006-106">It also describes using the sp_recompile system stored procedure to recompile an existing procedure.</span></span>  
  
 <span data-ttu-id="7c006-107">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="7c006-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="7c006-108">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="7c006-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="7c006-109">建议</span><span class="sxs-lookup"><span data-stu-id="7c006-109">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="7c006-110">安全性</span><span class="sxs-lookup"><span data-stu-id="7c006-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="7c006-111">**若要重新编译存储过程，请使用：**</span><span class="sxs-lookup"><span data-stu-id="7c006-111">**To recompile a stored procedure, using:**</span></span>  
  
     [<span data-ttu-id="7c006-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="7c006-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="7c006-113">开始之前</span><span class="sxs-lookup"><span data-stu-id="7c006-113">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="7c006-114">建议</span><span class="sxs-lookup"><span data-stu-id="7c006-114">Recommendations</span></span>  
  
-   <span data-ttu-id="7c006-115">在首次编译或重新编译过程时，该过程的查询计划针对该数据库及其对象的当前状态进行优化。</span><span class="sxs-lookup"><span data-stu-id="7c006-115">When a procedure is compiled for the first time or recompiled, the procedure's query plan is optimized for the current state of the database and its objects.</span></span> <span data-ttu-id="7c006-116">如果数据库对其数据或结构进行了重要更改，则重新编译过程会进行更新并针对这些更改优化过程的查询计划。</span><span class="sxs-lookup"><span data-stu-id="7c006-116">If a database undergoes significant changes to its data or structure, recompiling a procedure updates and optimizes the procedure's query plan for those changes.</span></span> <span data-ttu-id="7c006-117">这样可以提高过程的处理性能。</span><span class="sxs-lookup"><span data-stu-id="7c006-117">This can improve the procedure's processing performance.</span></span>  
  
-   <span data-ttu-id="7c006-118">有时必须强制执行过程重新编译，而其他时间将自动执行。</span><span class="sxs-lookup"><span data-stu-id="7c006-118">There are times when procedure recompilation must be forced and other times when it occurs automatically.</span></span> <span data-ttu-id="7c006-119">只要重新启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，就会发生自动重新编译操作。</span><span class="sxs-lookup"><span data-stu-id="7c006-119">Automatic recompiling occurs whenever [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is restarted.</span></span> <span data-ttu-id="7c006-120">当该过程引用的基础表发生物理设计更改时，也会执行此操作。</span><span class="sxs-lookup"><span data-stu-id="7c006-120">It also occurs if an underlying table referenced by the procedure has undergone physical design changes.</span></span>  
  
-   <span data-ttu-id="7c006-121">强制过程重新编译的另一个原因是抵消过程编译的“参数查找”行为。</span><span class="sxs-lookup"><span data-stu-id="7c006-121">Another reason to force a procedure to recompile is to counteract the "parameter sniffing" behavior of procedure compilation.</span></span> <span data-ttu-id="7c006-122">当 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 执行过程时，该过程在编译时使用的任何参数值都作为生成查询计划的一部分包括在内。</span><span class="sxs-lookup"><span data-stu-id="7c006-122">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] executes procedures, any parameter values that are used by the procedure when it compiles are included as part of generating the query plan.</span></span> <span data-ttu-id="7c006-123">如果这些值表示随后调用此过程时使用的典型值，则该过程在每次编译和执行时都会从查询计划中获益。</span><span class="sxs-lookup"><span data-stu-id="7c006-123">If these values represent the typical ones with which the procedure is subsequently called, then the procedure benefits from the query plan every time that it compiles and executes.</span></span> <span data-ttu-id="7c006-124">如果过程的参数值频繁异常，则强制执行过程的重新编译和基于其他参数值的新计划可以改善性能。</span><span class="sxs-lookup"><span data-stu-id="7c006-124">If parameter values on the procedure are frequently atypical, forcing a recompile of the procedure and a new plan based on different parameter values can improve performance.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="7c006-125">具有对过程执行语句级重新编译的特点。</span><span class="sxs-lookup"><span data-stu-id="7c006-125">features statement-level recompilation of procedures.</span></span> <span data-ttu-id="7c006-126">当 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 重新编译存储过程时，只编译导致重新编译的语句，而不编译整个过程。</span><span class="sxs-lookup"><span data-stu-id="7c006-126">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] recompiles stored procedures, only the statement that caused the recompilation is compiled, instead of the complete procedure.</span></span>  
  
-   <span data-ttu-id="7c006-127">如果过程的中某些查询定期使用非典型值或临时值，则可通过使用这些查询中的 RECOMPILE 查询提示来改善过程性能。</span><span class="sxs-lookup"><span data-stu-id="7c006-127">If certain queries in a procedure regularly use atypical or temporary values, procedure performance can be improved by using the RECOMPILE query hint inside those queries.</span></span> <span data-ttu-id="7c006-128">由于仅使用此查询提示的查询将进行重新编译，而不是整个过程进行重新编译，因此将模仿 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]语句级重新编译行为。</span><span class="sxs-lookup"><span data-stu-id="7c006-128">Since only the queries using the query hint will be recompiled instead of the complete procedure, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]'s statement-level recompilation behavior is mimicked.</span></span> <span data-ttu-id="7c006-129">但除了使用过程的当前参数值外，RECOMPILE 查询提示还在编译该语句时使用存储过程中本地变量的值。</span><span class="sxs-lookup"><span data-stu-id="7c006-129">But in addition to using the procedure's current parameter values, the RECOMPILE query hint also uses the values of any local variables inside the stored procedure when you compile the statement.</span></span> <span data-ttu-id="7c006-130">有关详细信息，请参阅 [查询提示 (Transact-SQL)](/sql/t-sql/queries/hints-transact-sql-query)。</span><span class="sxs-lookup"><span data-stu-id="7c006-130">For more information, see [Query Hint (Transact-SQL)](/sql/t-sql/queries/hints-transact-sql-query).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="7c006-131">Security</span><span class="sxs-lookup"><span data-stu-id="7c006-131">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="7c006-132">权限</span><span class="sxs-lookup"><span data-stu-id="7c006-132">Permissions</span></span>  
 <span data-ttu-id="7c006-133">`WITH RECOMPILE`选</span><span class="sxs-lookup"><span data-stu-id="7c006-133">`WITH RECOMPILE` Option</span></span>  
 <span data-ttu-id="7c006-134">如果在创建过程定义时使用此选项，则要求数据库中的 CREATE PROCEDURE 权限，还必须具有对架构（在其下创建过程）的 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="7c006-134">If this option is used when the procedure definition is created, it requires CREATE PROCEDURE permission in the database and ALTER permission on the schema in which the procedure is being created.</span></span>  
  
 <span data-ttu-id="7c006-135">如果在 EXECUTE 语句中使用此选项，则需要对该过程的 EXECUTE 权限。</span><span class="sxs-lookup"><span data-stu-id="7c006-135">If this option is used in an EXECUTE statement, it requires EXECUTE permissions on the procedure.</span></span> <span data-ttu-id="7c006-136">需要对 EXECUTE 语句本身的权限，而无需对 EXECUTE 语句中引用的过程的执行权限。</span><span class="sxs-lookup"><span data-stu-id="7c006-136">Permissions are not required on the EXECUTE statement itself but execute permissions are required on the procedure referenced in the EXECUTE statement.</span></span> <span data-ttu-id="7c006-137">有关详细信息，请参阅 [EXECUTE (Transact-SQL)](/sql/t-sql/language-elements/execute-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="7c006-137">For more information, see [EXECUTE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/execute-transact-sql).</span></span>  
  
 <span data-ttu-id="7c006-138">`RECOMPILE`查询提示</span><span class="sxs-lookup"><span data-stu-id="7c006-138">`RECOMPILE` Query Hint</span></span>  
 <span data-ttu-id="7c006-139">创建过程时使用该功能，并且此提示包含在该过程中的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句中。</span><span class="sxs-lookup"><span data-stu-id="7c006-139">This feature is used when the procedure is created and the hint is included in [!INCLUDE[tsql](../../includes/tsql-md.md)] statements in the procedure.</span></span> <span data-ttu-id="7c006-140">因此，它需要在数据库中有 CREATE PROCEDURE 权限，对在其中创建过程的架构有 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="7c006-140">Therefore, it requires CREATE PROCEDURE permission in the database and ALTER permission on the schema in which the procedure is being created.</span></span>  
  
 <span data-ttu-id="7c006-141">`sp_recompile`系统存储过程</span><span class="sxs-lookup"><span data-stu-id="7c006-141">`sp_recompile` System Stored Procedure</span></span>  
 <span data-ttu-id="7c006-142">需要具有对指定过程的 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="7c006-142">Requires ALTER permission on the specified procedure.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="7c006-143">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="7c006-143">Using Transact-SQL</span></span>  
  
#### <a name="to-recompile-a-stored-procedure-by-using-the-with-recompile-option"></a><span data-ttu-id="7c006-144">使用 WITH RECOMPILE 选项重新编译存储过程</span><span class="sxs-lookup"><span data-stu-id="7c006-144">To recompile a stored procedure by using the WITH RECOMPILE option</span></span>  
  
1.  <span data-ttu-id="7c006-145">连接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="7c006-145">Connect to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="7c006-146">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="7c006-146">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="7c006-147">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="7c006-147">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="7c006-148">该示例将创建过程定义。</span><span class="sxs-lookup"><span data-stu-id="7c006-148">This example creates the procedure definition.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID ( 'dbo.uspProductByVendor', 'P' ) IS NOT NULL   
    DROP PROCEDURE dbo.uspProductByVendor;  
GO  
CREATE PROCEDURE dbo.uspProductByVendor @Name varchar(30) = '%'  
WITH RECOMPILE  
AS  
    SET NOCOUNT ON;  
    SELECT v.Name AS 'Vendor name', p.Name AS 'Product name'  
    FROM Purchasing.Vendor AS v   
    JOIN Purchasing.ProductVendor AS pv   
      ON v.BusinessEntityID = pv.BusinessEntityID   
    JOIN Production.Product AS p   
      ON pv.ProductID = p.ProductID  
    WHERE v.Name LIKE @Name;  
  
```  
  
#### <a name="to-recompile-a-stored-procedure-by-using-the-with-recompile-option"></a><span data-ttu-id="7c006-149">使用 WITH RECOMPILE 选项重新编译存储过程</span><span class="sxs-lookup"><span data-stu-id="7c006-149">To recompile a stored procedure by using the WITH RECOMPILE option</span></span>  
  
1.  <span data-ttu-id="7c006-150">连接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="7c006-150">Connect to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="7c006-151">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="7c006-151">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="7c006-152">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="7c006-152">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="7c006-153">该示例将创建一个简单过程，该过程将从视图中返回所有雇员（提供姓和名）、职务以及部门名称。</span><span class="sxs-lookup"><span data-stu-id="7c006-153">This example creates a simple procedure that returns all employees (first and last names supplied), their job titles, and their department names from a view.</span></span>  
  
     <span data-ttu-id="7c006-154">然后，将第二个代码示例复制并粘贴到查询窗口中，然后单击 **“执行”**。</span><span class="sxs-lookup"><span data-stu-id="7c006-154">And then copy and paste the second code example into the query window and click **Execute**.</span></span> <span data-ttu-id="7c006-155">此操作将执行该过程，并重新编译过程的查询计划。</span><span class="sxs-lookup"><span data-stu-id="7c006-155">This executes the procedure and recompiles the procedure's query plan.</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
EXECUTE HumanResources.uspGetAllEmployees WITH RECOMPILE;  
GO  
  
```  
  
#### <a name="to-recompile-a-stored-procedure-by-using-sp_recompile"></a><span data-ttu-id="7c006-156">使用 sp_recompile 重新编译存储过程</span><span class="sxs-lookup"><span data-stu-id="7c006-156">To recompile a stored procedure by using sp_recompile</span></span>  
  
1.  <span data-ttu-id="7c006-157">连接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="7c006-157">Connect to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="7c006-158">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="7c006-158">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="7c006-159">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="7c006-159">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="7c006-160">该示例将创建一个简单过程，该过程将从视图中返回所有雇员（提供姓和名）、职务以及部门名称。</span><span class="sxs-lookup"><span data-stu-id="7c006-160">This example creates a simple procedure that returns all employees (first and last names supplied), their job titles, and their department names from a view.</span></span>  
  
     <span data-ttu-id="7c006-161">然后，将以下示例复制并粘贴到查询窗口中，然后单击 **“执行”**。</span><span class="sxs-lookup"><span data-stu-id="7c006-161">Then, copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="7c006-162">这将不执行过程，但将该过程标记为重新编译，以便在下次执行该过程时更新其查询计划。</span><span class="sxs-lookup"><span data-stu-id="7c006-162">This does not execute the procedure but it does mark the procedure to be recompiled so that its query plan is updated the next time that the procedure is executed.</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_recompile N'HumanResources.uspGetAllEmployees';  
GO  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="7c006-163">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7c006-163">See Also</span></span>  
 <span data-ttu-id="7c006-164">[创建存储过程](../stored-procedures/create-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="7c006-164">[Create a Stored Procedure](../stored-procedures/create-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="7c006-165">[修改存储过程](../stored-procedures/modify-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="7c006-165">[Modify a Stored Procedure](../stored-procedures/modify-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="7c006-166">[重命名存储过程](rename-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="7c006-166">[Rename a Stored Procedure](rename-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="7c006-167">[查看存储过程的定义](view-the-definition-of-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="7c006-167">[View the Definition of a Stored Procedure](view-the-definition-of-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="7c006-168">[查看存储过程的依赖关系](view-the-dependencies-of-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="7c006-168">[View the Dependencies of a Stored Procedure](view-the-dependencies-of-a-stored-procedure.md) </span></span>  
 [<span data-ttu-id="7c006-169">DROP PROCEDURE (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="7c006-169">DROP PROCEDURE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-procedure-transact-sql)  
  
  
