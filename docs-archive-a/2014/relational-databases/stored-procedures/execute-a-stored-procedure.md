---
title: 执行存储过程 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.executeprocedure.f1
- sql12.swb.executeprocedure.general.f1
helpviewer_keywords:
- stored procedures [SQL Server], parameters
- extended stored procedures [SQL Server], executing
- system stored procedures [SQL Server], executing
- stored procedures [SQL Server], executing
- user-defined stored procedures [SQL Server]
ms.assetid: a0b1337d-2059-4872-8c62-3f967d8b170f
author: stevestein
ms.author: sstein
ms.openlocfilehash: c679ba7af3ac9f60d312b33c0346e50687387476
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590099"
---
# <a name="execute-a-stored-procedure"></a><span data-ttu-id="2a452-102">执行存储过程</span><span class="sxs-lookup"><span data-stu-id="2a452-102">Execute a Stored Procedure</span></span>
  <span data-ttu-id="2a452-103">本主题介绍如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中执行存储过程。</span><span class="sxs-lookup"><span data-stu-id="2a452-103">This topic describes how to execute a stored procedure in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="2a452-104">有两种不同方法执行存储过程。</span><span class="sxs-lookup"><span data-stu-id="2a452-104">There are two different ways to execute a stored procedure.</span></span> <span data-ttu-id="2a452-105">第一种方法和最常见的方法供应用程序或用户调用过程。</span><span class="sxs-lookup"><span data-stu-id="2a452-105">The first and most common approach is for an application or user to call the procedure.</span></span> <span data-ttu-id="2a452-106">第二种方法是将过程设置为在启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例时自动运行。</span><span class="sxs-lookup"><span data-stu-id="2a452-106">The second approach is to set the procedure to run automatically when an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] starts.</span></span> <span data-ttu-id="2a452-107">当应用程序或用户调用过程时，调用中显式声明了 [!INCLUDE[tsql](../../includes/tsql-md.md)] EXECUTE 或 EXEC 关键字。</span><span class="sxs-lookup"><span data-stu-id="2a452-107">When a procedure is called by an application or user, the [!INCLUDE[tsql](../../includes/tsql-md.md)] EXECUTE or EXEC keyword is explicitly stated in the call.</span></span> <span data-ttu-id="2a452-108">或者，如果过程是 [!INCLUDE[tsql](../../includes/tsql-md.md)] 批处理中的第一条语句，那么不使用关键字也可以调用并执行此过程。</span><span class="sxs-lookup"><span data-stu-id="2a452-108">Alternatively, the procedure can be called and executed without the keyword if the procedure is the first statement in the [!INCLUDE[tsql](../../includes/tsql-md.md)] batch.</span></span>  
  
 <span data-ttu-id="2a452-109">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="2a452-109">**In This Topic**</span></span>  
  
-   <span data-ttu-id="2a452-110">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="2a452-110">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="2a452-111">限制和局限</span><span class="sxs-lookup"><span data-stu-id="2a452-111">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="2a452-112">建议</span><span class="sxs-lookup"><span data-stu-id="2a452-112">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="2a452-113">安全性</span><span class="sxs-lookup"><span data-stu-id="2a452-113">Security</span></span>](#Security)  
  
-   <span data-ttu-id="2a452-114">**若要执行存储过程，请使用：**</span><span class="sxs-lookup"><span data-stu-id="2a452-114">**To execute a stored procedure, using:**</span></span>  
  
     [<span data-ttu-id="2a452-115">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2a452-115">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="2a452-116">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2a452-116">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="2a452-117">开始之前</span><span class="sxs-lookup"><span data-stu-id="2a452-117">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="2a452-118">限制和局限</span><span class="sxs-lookup"><span data-stu-id="2a452-118">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="2a452-119">与系统过程名称匹配时使用调用数据库排序规则。</span><span class="sxs-lookup"><span data-stu-id="2a452-119">The calling database collation is used when matching system procedure names.</span></span> <span data-ttu-id="2a452-120">因此，在过程调用中始终使用系统过程名称的正确大小写形式。</span><span class="sxs-lookup"><span data-stu-id="2a452-120">Therefore, always use the exact case of system procedure names in procedure calls.</span></span> <span data-ttu-id="2a452-121">例如，如果在具有区分大小写的排序规则的数据库上下文中执行，以下代码将失败：</span><span class="sxs-lookup"><span data-stu-id="2a452-121">For example, this code will fail if it is executed in the context of a database that has a case-sensitive collation:</span></span>  
  
    ```sql  
    EXEC SP_heLP; -- Will fail to resolve because SP_heLP does not equal sp_help  
    ```  
  
     <span data-ttu-id="2a452-122">若要显示确切的系统过程名称，请查询 [sys.system_objects](/sql/relational-databases/system-catalog-views/sys-system-objects-transact-sql) 和 [sys.system_parameters](/sql/relational-databases/system-catalog-views/sys-system-parameters-transact-sql) 目录视图。</span><span class="sxs-lookup"><span data-stu-id="2a452-122">To display the exact system procedure names, query the [sys.system_objects](/sql/relational-databases/system-catalog-views/sys-system-objects-transact-sql) and [sys.system_parameters](/sql/relational-databases/system-catalog-views/sys-system-parameters-transact-sql) catalog views.</span></span>  
  
-   <span data-ttu-id="2a452-123">如果用户定义的过程与系统过程同名，则可能不会执行用户定义的过程。</span><span class="sxs-lookup"><span data-stu-id="2a452-123">If a user-defined procedure has the same name as a system procedure, the user-defined procedure might not ever execute.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="2a452-124">建议</span><span class="sxs-lookup"><span data-stu-id="2a452-124">Recommendations</span></span>  
  
-   <span data-ttu-id="2a452-125">执行系统存储过程</span><span class="sxs-lookup"><span data-stu-id="2a452-125">Executing System Stored Procedures</span></span>  
  
     <span data-ttu-id="2a452-126">系统过程以前缀 **sp_** 开头。</span><span class="sxs-lookup"><span data-stu-id="2a452-126">System procedures begin with the prefix **sp_**.</span></span> <span data-ttu-id="2a452-127">因为从逻辑意义上讲，这些过程出现在所有用户定义的数据库和系统定义的数据库中，所以可以从任何数据库执行这些过程，而不必完全限定过程名称。</span><span class="sxs-lookup"><span data-stu-id="2a452-127">Because they logically appear in all user- and system- defined databases, they can be executed from any database without having to fully quality the procedure name.</span></span> <span data-ttu-id="2a452-128">但是，建议使用 **sys** 架构名称对所有系统过程名称进行架构限定，以防止名称冲突。</span><span class="sxs-lookup"><span data-stu-id="2a452-128">However, we recommend schema-qualifying all system procedure names with the **sys** schema name to prevent name conflicts.</span></span> <span data-ttu-id="2a452-129">以下示例说明调用系统过程的推荐方法。</span><span class="sxs-lookup"><span data-stu-id="2a452-129">The following example demonstrates the recommended method of calling a system procedure.</span></span>  
  
    ```sql  
    EXEC sys.sp_who;  
    ```  
  
-   <span data-ttu-id="2a452-130">执行用户定义存储过程</span><span class="sxs-lookup"><span data-stu-id="2a452-130">Executing User-defined Stored Procedures</span></span>  
  
     <span data-ttu-id="2a452-131">当执行用户定义的过程时，我们建议使用架构名称限定过程名称。</span><span class="sxs-lookup"><span data-stu-id="2a452-131">When executing a user-defined procedure, we recommend qualifying the procedure name with the schema name.</span></span> <span data-ttu-id="2a452-132">这种做法使性能得到小幅提升，因为 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 不必搜索多个架构。</span><span class="sxs-lookup"><span data-stu-id="2a452-132">This practice gives a small performance boost because the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] does not have to search multiple schemas.</span></span> <span data-ttu-id="2a452-133">如果某个数据库在多个架构中具有同名过程，则这还可以防止执行错误的过程。</span><span class="sxs-lookup"><span data-stu-id="2a452-133">It also prevents executing the wrong procedure if a database has procedures with the same name in multiple schemas.</span></span>  
  
     <span data-ttu-id="2a452-134">以下示例说明执行用户定义过程的推荐方法。</span><span class="sxs-lookup"><span data-stu-id="2a452-134">The following example demonstrates the recommended method to execute a user-defined procedure.</span></span> <span data-ttu-id="2a452-135">请注意，此过程接受一个输入参数。</span><span class="sxs-lookup"><span data-stu-id="2a452-135">Notice that the procedure accepts one input parameter.</span></span> <span data-ttu-id="2a452-136">有关指定输入参数和输出参数的信息，请参阅 [指定参数](specify-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="2a452-136">For information about specifying input and output parameters, see [Specify Parameters](specify-parameters.md).</span></span>  
  
    ```sql  
    USE AdventureWorks2012;  
    GO  
    EXEC dbo.uspGetEmployeeManagers @BusinessEntityID = 50;  
    ```  
  
     <span data-ttu-id="2a452-137">-或-</span><span class="sxs-lookup"><span data-stu-id="2a452-137">-Or-</span></span>  
  
    ```sql  
    EXEC AdventureWorks2012.dbo.uspGetEmployeeManagers 50;  
    GO  
    ```  
  
     <span data-ttu-id="2a452-138">如果指定了非限定的用户定义过程，则 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 按以下顺序搜索此过程：</span><span class="sxs-lookup"><span data-stu-id="2a452-138">If a nonqualified user-defined procedure is specified, the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] searches for the procedure in the following order:</span></span>  
  
    1.  <span data-ttu-id="2a452-139">当前数据库的 **sys** 架构。</span><span class="sxs-lookup"><span data-stu-id="2a452-139">The **sys** schema of the current database.</span></span>  
  
    2.  <span data-ttu-id="2a452-140">调用方的默认架构（如果它在批处理或动态 SQL 中执行）。</span><span class="sxs-lookup"><span data-stu-id="2a452-140">The caller's default schema if it is executed in a batch or in dynamic SQL.</span></span> <span data-ttu-id="2a452-141">或者，如果非限定的过程名称出现在另一个过程定义的主体中，则接着搜索包含后一过程的架构。</span><span class="sxs-lookup"><span data-stu-id="2a452-141">Or, if the nonqualified procedure name appears inside the body of another procedure definition, the schema that contains this other procedure is searched next.</span></span>  
  
    3.  <span data-ttu-id="2a452-142">当前数据库中的 **dbo** 架构。</span><span class="sxs-lookup"><span data-stu-id="2a452-142">The **dbo** schema in the current database.</span></span>  
  
-   <span data-ttu-id="2a452-143">自动执行存储过程</span><span class="sxs-lookup"><span data-stu-id="2a452-143">Executing Stored Procedures Automatically</span></span>  
  
     <span data-ttu-id="2a452-144">在每次启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 时将执行标记为自动执行的过程，并在启动过程期间中恢复 **master** 数据库。</span><span class="sxs-lookup"><span data-stu-id="2a452-144">Procedures marked for automatic execution are executed every time [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] starts and the **master** database is recovered during that startup process.</span></span> <span data-ttu-id="2a452-145">将这些过程设置为自动执行对执行数据库维护操作或使这些过程作为后台进程连续运行很有用。</span><span class="sxs-lookup"><span data-stu-id="2a452-145">Setting up procedures to execute automatically can be useful for performing database maintenance operations or for having procedures run continuously as background processes.</span></span> <span data-ttu-id="2a452-146">自动执行的另一个用途是使该过程执行 **tempdb**中的系统或维护任务，如创建一个全局临时表。</span><span class="sxs-lookup"><span data-stu-id="2a452-146">Another use for automatic execution is to have the procedure perform system or maintenance tasks in **tempdb**, such as creating a global temporary table.</span></span> <span data-ttu-id="2a452-147">这将确保在 **启动过程中重新创建** tempdb [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 时，始终存在这样一个临时表。</span><span class="sxs-lookup"><span data-stu-id="2a452-147">This makes sure that such a temporary table will always exist when **tempdb** is re-created during [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] startup.</span></span>  
  
     <span data-ttu-id="2a452-148">自动执行的过程使用与固定服务器角色 **sysadmin** 的成员相同的权限进行操作。</span><span class="sxs-lookup"><span data-stu-id="2a452-148">A procedure that is automatically executed operates with the same permissions as members of the **sysadmin** fixed server role.</span></span> <span data-ttu-id="2a452-149">该过程生成的所有错误消息都将写入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志。</span><span class="sxs-lookup"><span data-stu-id="2a452-149">Any error messages generated by the procedure are written to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log.</span></span>  
  
     <span data-ttu-id="2a452-150">虽然对启动过程的数目没有限制，但是请注意，在执行时每个启动过程将占用一个工作线程。</span><span class="sxs-lookup"><span data-stu-id="2a452-150">There is no limit to the number of startup procedures you can have, but be aware that each consumes one worker thread while executing.</span></span> <span data-ttu-id="2a452-151">如果必须在启动时执行多个过程，但不需要并行执行，则可以指定一个过程作为启动过程，让该过程调用其他过程。</span><span class="sxs-lookup"><span data-stu-id="2a452-151">If you must execute multiple procedures at startup but do not need to execute them in parallel, make one procedure the startup procedure and have that procedure call the other procedures.</span></span> <span data-ttu-id="2a452-152">这样就只占用一个工作线程。</span><span class="sxs-lookup"><span data-stu-id="2a452-152">This uses only one worker thread.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="2a452-153">请勿从自动执行的过程中返回任何结果集。</span><span class="sxs-lookup"><span data-stu-id="2a452-153">Do not return any result sets from a procedure that is executed automatically.</span></span> <span data-ttu-id="2a452-154">因为该过程是由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 而不是由应用程序或用户执行的，所以结果集将无处可去。</span><span class="sxs-lookup"><span data-stu-id="2a452-154">Because the procedure is being executed by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instead of an application or user, there is nowhere for the result sets to go.</span></span>  
  
-   <span data-ttu-id="2a452-155">设置、清除和控制自动执行</span><span class="sxs-lookup"><span data-stu-id="2a452-155">Setting, Clearing, and Controlling Automatic Execution</span></span>  
  
     <span data-ttu-id="2a452-156">只有系统管理员 (**sa**) 可以将过程标记为自动执行。</span><span class="sxs-lookup"><span data-stu-id="2a452-156">Only the system administrator (**sa**) can mark a procedure to execute automatically.</span></span> <span data-ttu-id="2a452-157">另外，该过程必须在 **master** 数据库中，由 **sa**所有，而且不能有输入或输出参数。</span><span class="sxs-lookup"><span data-stu-id="2a452-157">In addition, the procedure must be in the **master** database, owned by **sa**, and cannot have input or output parameters.</span></span>  
  
     <span data-ttu-id="2a452-158">使用 [sp_procoption](/sql/relational-databases/system-stored-procedures/sp-procoption-transact-sql) 可以：</span><span class="sxs-lookup"><span data-stu-id="2a452-158">Use [sp_procoption](/sql/relational-databases/system-stored-procedures/sp-procoption-transact-sql) to:</span></span>  
  
    1.  <span data-ttu-id="2a452-159">将现有过程指定为启动过程。</span><span class="sxs-lookup"><span data-stu-id="2a452-159">Designate an existing procedure as a startup procedure.</span></span>  
  
    2.  <span data-ttu-id="2a452-160">阻止过程在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 启动时执行。</span><span class="sxs-lookup"><span data-stu-id="2a452-160">Stop a procedure from executing at [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] startup.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="2a452-161">Security</span><span class="sxs-lookup"><span data-stu-id="2a452-161">Security</span></span>  
 <span data-ttu-id="2a452-162">有关详细信息，请参阅 [EXECUTE AS (Transact-SQL)](/sql/t-sql/statements/execute-as-transact-sql) 和 [EXECUTE AS 子句 (Transact-SQL)](/sql/t-sql/statements/execute-as-clause-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2a452-162">For more information, see [EXECUTE AS &#40;Transact-SQL&#41;](/sql/t-sql/statements/execute-as-transact-sql) and [EXECUTE AS Clause &#40;Transact-SQL&#41;](/sql/t-sql/statements/execute-as-clause-transact-sql).</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="2a452-163">权限</span><span class="sxs-lookup"><span data-stu-id="2a452-163">Permissions</span></span>  
 <span data-ttu-id="2a452-164">有关详细信息，请参阅 [EXECUTE (Transact-SQL)](/sql/t-sql/language-elements/execute-transact-sql)中执行存储过程。</span><span class="sxs-lookup"><span data-stu-id="2a452-164">For more information, see the "Permissions" section in [EXECUTE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/execute-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="2a452-165">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2a452-165">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-execute-a-stored-procedure"></a><span data-ttu-id="2a452-166">执行存储过程</span><span class="sxs-lookup"><span data-stu-id="2a452-166">To execute a stored procedure</span></span>  
  
1.  <span data-ttu-id="2a452-167">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]的实例，再依次展开该实例、 **“数据库”** 。</span><span class="sxs-lookup"><span data-stu-id="2a452-167">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], expand that instance, and then expand **Databases**.</span></span>  
  
2.  <span data-ttu-id="2a452-168">展开所需的数据库，然后依次展开 **“可编程性”** 和 **“存储过程”** 。</span><span class="sxs-lookup"><span data-stu-id="2a452-168">Expand the database that you want, expand **Programmability**, and then expand **Stored Procedures**.</span></span>  
  
3.  <span data-ttu-id="2a452-169">右键单击所需的用户定义存储过程，然后单击“执行存储过程”。</span><span class="sxs-lookup"><span data-stu-id="2a452-169">Right-click the user-defined stored procedure that you want and click **Execute Stored Procedure**.</span></span>  
  
4.  <span data-ttu-id="2a452-170">在 **“执行过程”** 对话框中，为每个参数指定一个值以及它是否应传递 Null 值。</span><span class="sxs-lookup"><span data-stu-id="2a452-170">In the **Execute Procedure** dialog box, specify a value for each parameter and whether it should pass a null value.</span></span>  
  
     <span data-ttu-id="2a452-171">**Parameter**</span><span class="sxs-lookup"><span data-stu-id="2a452-171">**Parameter**</span></span>  
     <span data-ttu-id="2a452-172">指示参数的名称。</span><span class="sxs-lookup"><span data-stu-id="2a452-172">Indicates the name of the parameter.</span></span>  
  
     <span data-ttu-id="2a452-173">**数据类型**</span><span class="sxs-lookup"><span data-stu-id="2a452-173">**Data Type**</span></span>  
     <span data-ttu-id="2a452-174">指示参数的数据类型。</span><span class="sxs-lookup"><span data-stu-id="2a452-174">Indicates the data type of the parameter.</span></span>  
  
     <span data-ttu-id="2a452-175">**输出参数**</span><span class="sxs-lookup"><span data-stu-id="2a452-175">**Output Parameter**</span></span>  
     <span data-ttu-id="2a452-176">指示是否为输出参数。</span><span class="sxs-lookup"><span data-stu-id="2a452-176">Indicates if this is an output parameter.</span></span>  
  
     <span data-ttu-id="2a452-177">**传递空值**</span><span class="sxs-lookup"><span data-stu-id="2a452-177">**Pass Null Value**</span></span>  
     <span data-ttu-id="2a452-178">将 NULL 作为参数值传递。</span><span class="sxs-lookup"><span data-stu-id="2a452-178">Pass a NULL as the value of the parameter.</span></span>  
  
     <span data-ttu-id="2a452-179">**值**</span><span class="sxs-lookup"><span data-stu-id="2a452-179">**Value**</span></span>  
     <span data-ttu-id="2a452-180">在调用过程时键入参数的值。</span><span class="sxs-lookup"><span data-stu-id="2a452-180">Type the value for the parameter when calling the procedure.</span></span>  
  
5.  <span data-ttu-id="2a452-181">若要执行存储过程，请单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="2a452-181">To execute the stored procedure, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="2a452-182">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2a452-182">Using Transact-SQL</span></span>  
  
#### <a name="to-execute-a-stored-procedure"></a><span data-ttu-id="2a452-183">执行存储过程</span><span class="sxs-lookup"><span data-stu-id="2a452-183">To execute a stored procedure</span></span>  
  
1.  <span data-ttu-id="2a452-184">连接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2a452-184">Connect to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="2a452-185">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="2a452-185">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="2a452-186">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="2a452-186">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="2a452-187">此示例演示如何执行应有一个参数的存储过程。</span><span class="sxs-lookup"><span data-stu-id="2a452-187">This example shows how to execute a stored procedure that expects one parameter.</span></span> <span data-ttu-id="2a452-188">该示例执行 `uspGetEmployeeManagers` 存储过程，并将值  `6` 指定为 `@EmployeeID` 参数。</span><span class="sxs-lookup"><span data-stu-id="2a452-188">The example executes the `uspGetEmployeeManagers` stored procedure with the value  `6` specified as the `@EmployeeID` parameter.</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC dbo.uspGetEmployeeManagers 6;  
GO  
```  
  
#### <a name="to-set-or-clear-a-procedure-for-executing-automatically"></a><span data-ttu-id="2a452-189">设置或清除过程自动执行</span><span class="sxs-lookup"><span data-stu-id="2a452-189">To set or clear a procedure for executing automatically</span></span>  
  
1.  <span data-ttu-id="2a452-190">连接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2a452-190">Connect to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="2a452-191">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="2a452-191">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="2a452-192">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="2a452-192">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="2a452-193">此示例演示如何使用 [sp_procoption](/sql/relational-databases/system-stored-procedures/sp-procoption-transact-sql) 设置过程自动执行。</span><span class="sxs-lookup"><span data-stu-id="2a452-193">This example shows how to use [sp_procoption](/sql/relational-databases/system-stored-procedures/sp-procoption-transact-sql) to set a procedure for automatic execution.</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_procoption @ProcName = '<procedure name>'   
    , @OptionName = ] 'startup'   
    , @OptionValue = 'on';  
```  
  
#### <a name="to-stop-a-procedure-from-executing-automatically"></a><span data-ttu-id="2a452-194">阻止过程自动执行</span><span class="sxs-lookup"><span data-stu-id="2a452-194">To stop a procedure from executing automatically</span></span>  
  
1.  <span data-ttu-id="2a452-195">连接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2a452-195">Connect to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="2a452-196">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="2a452-196">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="2a452-197">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="2a452-197">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="2a452-198">此示例说明如何使用 [sp_procoption](/sql/relational-databases/system-stored-procedures/sp-procoption-transact-sql) 阻止过程自动执行。</span><span class="sxs-lookup"><span data-stu-id="2a452-198">This example shows how to use [sp_procoption](/sql/relational-databases/system-stored-procedures/sp-procoption-transact-sql) to stop a procedure from executing automatically.</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_procoption @ProcName = '<procedure name>'   
    , @OptionValue = 'off';  
```  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="2a452-199">示例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="2a452-199">Example (Transact-SQL)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a452-200">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2a452-200">See Also</span></span>  
 <span data-ttu-id="2a452-201">[指定参数](specify-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="2a452-201">[Specify Parameters](specify-parameters.md) </span></span>  
 <span data-ttu-id="2a452-202">[配置 scan for startup procs 服务器配置选项](../../database-engine/configure-windows/configure-the-scan-for-startup-procs-server-configuration-option.md) </span><span class="sxs-lookup"><span data-stu-id="2a452-202">[Configure the scan for startup procs Server Configuration Option](../../database-engine/configure-windows/configure-the-scan-for-startup-procs-server-configuration-option.md) </span></span>  
 <span data-ttu-id="2a452-203">[EXECUTE (Transact-SQL)](/sql/t-sql/language-elements/execute-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2a452-203">[EXECUTE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/execute-transact-sql) </span></span>  
 <span data-ttu-id="2a452-204">[CREATE PROCEDURE (Transact-SQL)](/sql/t-sql/statements/create-procedure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2a452-204">[CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql) </span></span>  
 [<span data-ttu-id="2a452-205">存储过程（数据库引擎）</span><span class="sxs-lookup"><span data-stu-id="2a452-205">Stored Procedures &#40;Database Engine&#41;</span></span>](stored-procedures-database-engine.md)  
  
  
