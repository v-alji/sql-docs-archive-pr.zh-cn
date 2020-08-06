---
title: 用户定义函数 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- user-defined functions [SQL Server], components
- user-defined functions [SQL Server], about user-defined functions
ms.assetid: d7ddafab-f5a6-44b0-81d5-ba96425aada4
author: rothja
ms.author: jroth
ms.openlocfilehash: c7e4b1a77f2fe5a13e21d8b3fe59e37931669b30
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576584"
---
# <a name="user-defined-functions"></a><span data-ttu-id="f4d61-102">用户定义函数</span><span class="sxs-lookup"><span data-stu-id="f4d61-102">User-Defined Functions</span></span>
  <span data-ttu-id="f4d61-103">与编程语言中的函数类似，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用户定义函数是接受参数、执行操作（例如复杂计算）并将操作结果以值的形式返回的例程。</span><span class="sxs-lookup"><span data-stu-id="f4d61-103">Like functions in programming languages, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user-defined functions are routines that accept parameters, perform an action, such as a complex calculation, and return the result of that action as a value.</span></span> <span data-ttu-id="f4d61-104">返回值可以是单个标量值或结果集。</span><span class="sxs-lookup"><span data-stu-id="f4d61-104">The return value can either be a single scalar value or a result set.</span></span>  
  
 <span data-ttu-id="f4d61-105">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="f4d61-105">**In This Topic**</span></span>  
  
 [<span data-ttu-id="f4d61-106">用户定义函数的优点</span><span class="sxs-lookup"><span data-stu-id="f4d61-106">User-defined Function Benefits</span></span>](#Benefits)  
  
 [<span data-ttu-id="f4d61-107">函数的类型</span><span class="sxs-lookup"><span data-stu-id="f4d61-107">Types of Functions</span></span>](#FunctionTypes)  
  
 [<span data-ttu-id="f4d61-108">指导</span><span class="sxs-lookup"><span data-stu-id="f4d61-108">Guidelines</span></span>](#Guidelines)  
  
 [<span data-ttu-id="f4d61-109">函数中的有效语句</span><span class="sxs-lookup"><span data-stu-id="f4d61-109">Valid Statements in a Function</span></span>](#ValidStatements)  
  
 [<span data-ttu-id="f4d61-110">绑定到架构的函数</span><span class="sxs-lookup"><span data-stu-id="f4d61-110">Schema Bound Functions</span></span>](#SchemaBound)  
  
 [<span data-ttu-id="f4d61-111">指定参数</span><span class="sxs-lookup"><span data-stu-id="f4d61-111">Specifying Parameters</span></span>](#Parameters)  
  
 [<span data-ttu-id="f4d61-112">相关任务</span><span class="sxs-lookup"><span data-stu-id="f4d61-112">Related Tasks</span></span>](#Tasks)  
  
##  <a name="user-defined-function-benefits"></a><a name="Benefits"></a><span data-ttu-id="f4d61-113">用户定义函数的优点</span><span class="sxs-lookup"><span data-stu-id="f4d61-113">User-defined Function Benefits</span></span>  
 <span data-ttu-id="f4d61-114">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中使用用户定义函数有以下优点：</span><span class="sxs-lookup"><span data-stu-id="f4d61-114">The benefits of using user-defined functions in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are:</span></span>  
  
-   <span data-ttu-id="f4d61-115">允许模块化程序设计。</span><span class="sxs-lookup"><span data-stu-id="f4d61-115">They allow modular programming.</span></span>  
  
     <span data-ttu-id="f4d61-116">只需创建一次函数并将其存储在数据库中，以后便可以在程序中调用任意次。</span><span class="sxs-lookup"><span data-stu-id="f4d61-116">You can create the function once, store it in the database, and call it any number of times in your program.</span></span> <span data-ttu-id="f4d61-117">用户定义函数可以独立于程序源代码进行修改。</span><span class="sxs-lookup"><span data-stu-id="f4d61-117">User-defined functions can be modified independently of the program source code.</span></span>  
  
-   <span data-ttu-id="f4d61-118">执行速度更快。</span><span class="sxs-lookup"><span data-stu-id="f4d61-118">They allow faster execution.</span></span>  
  
     <span data-ttu-id="f4d61-119">与存储过程相似，[!INCLUDE[tsql](../../includes/tsql-md.md)] 用户定义函数通过缓存计划并在重复执行时重用它来降低 [!INCLUDE[tsql](../../includes/tsql-md.md)] 代码的编译开销。</span><span class="sxs-lookup"><span data-stu-id="f4d61-119">Similar to stored procedures, [!INCLUDE[tsql](../../includes/tsql-md.md)] user-defined functions reduce the compilation cost of [!INCLUDE[tsql](../../includes/tsql-md.md)] code by caching the plans and reusing them for repeated executions.</span></span> <span data-ttu-id="f4d61-120">这意味着每次使用用户定义函数时均无需重新解析和重新优化，从而缩短了执行时间。</span><span class="sxs-lookup"><span data-stu-id="f4d61-120">This means the user-defined function does not need to be reparsed and reoptimized with each use resulting in much faster execution times.</span></span>  
  
     <span data-ttu-id="f4d61-121">和用于计算任务、字符串操作和业务逻辑的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 函数相比，CLR 函数具有显著的性能优势。</span><span class="sxs-lookup"><span data-stu-id="f4d61-121">CLR functions offer significant performance advantage over [!INCLUDE[tsql](../../includes/tsql-md.md)] functions for computational tasks, string manipulation, and business logic.</span></span> [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="f4d61-122">函数更适用于数据访问密集型逻辑。</span><span class="sxs-lookup"><span data-stu-id="f4d61-122">functions are better suited for data-access intensive logic.</span></span>  
  
-   <span data-ttu-id="f4d61-123">减少网络流量。</span><span class="sxs-lookup"><span data-stu-id="f4d61-123">They can reduce network traffic.</span></span>  
  
     <span data-ttu-id="f4d61-124">基于某种无法用单一标量的表达式表示的复杂约束来过滤数据的操作，可以表示为函数。</span><span class="sxs-lookup"><span data-stu-id="f4d61-124">An operation that filters data based on some complex constraint that cannot be expressed in a single scalar expression can be expressed as a function.</span></span> <span data-ttu-id="f4d61-125">然后，此函数便可以在 WHERE 子句中调用，以减少发送至客户端的数字或行数。</span><span class="sxs-lookup"><span data-stu-id="f4d61-125">The function can then invoked in the WHERE clause to reduce the number or rows sent to the client.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f4d61-126">查询中的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 用户定义函数只能针对单个线程执行（串行执行计划）。</span><span class="sxs-lookup"><span data-stu-id="f4d61-126">[!INCLUDE[tsql](../../includes/tsql-md.md)] user-defined functions in queries can only be executed on a single thread (serial execution plan).</span></span>  
  
##  <a name="types-of-functions"></a><a name="FunctionTypes"></a><span data-ttu-id="f4d61-127">函数的类型</span><span class="sxs-lookup"><span data-stu-id="f4d61-127">Types of Functions</span></span>  
 <span data-ttu-id="f4d61-128">标量函数</span><span class="sxs-lookup"><span data-stu-id="f4d61-128">Scalar Function</span></span>  
 <span data-ttu-id="f4d61-129">用户定义标量函数返回在 RETURNS 子句中定义的类型的单个数据值。</span><span class="sxs-lookup"><span data-stu-id="f4d61-129">User-defined scalar functions return a single data value of the type defined in the RETURNS clause.</span></span> <span data-ttu-id="f4d61-130">对于内联标量函数，没有函数体；标量值是单个语句的结果。</span><span class="sxs-lookup"><span data-stu-id="f4d61-130">For an inline scalar function, there is no function body; the scalar value is the result of a single statement.</span></span> <span data-ttu-id="f4d61-131">对于多语句标量函数，定义在 BEGIN...END 块中的函数体包含一系列返回单个值的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="f4d61-131">For a multistatement scalar function, the function body, defined in a BEGIN...END block, contains a series of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that return the single value.</span></span> <span data-ttu-id="f4d61-132">返回类型可以是除 `text`、`ntext`、`image`、`cursor` 和 `timestamp` 外的任何数据类型。</span><span class="sxs-lookup"><span data-stu-id="f4d61-132">The return type can be any data type except `text`, `ntext`, `image`, `cursor`, and `timestamp`.</span></span>  
  
 <span data-ttu-id="f4d61-133">表值函数</span><span class="sxs-lookup"><span data-stu-id="f4d61-133">Table-Valued Functions</span></span>  
 <span data-ttu-id="f4d61-134">用户定义表值函数返回 `table` 数据类型。</span><span class="sxs-lookup"><span data-stu-id="f4d61-134">User-defined table-valued functions return a `table` data type.</span></span> <span data-ttu-id="f4d61-135">对于内联表值函数，没有函数主体；表是单个 SELECT 语句的结果集。</span><span class="sxs-lookup"><span data-stu-id="f4d61-135">For an inline table-valued function, there is no function body; the table is the result set of a single SELECT statement.</span></span>  
  
 <span data-ttu-id="f4d61-136">系统函数</span><span class="sxs-lookup"><span data-stu-id="f4d61-136">System Functions</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="f4d61-137">提供了许多系统函数，可用于执行各种操作。</span><span class="sxs-lookup"><span data-stu-id="f4d61-137">provides many system functions that you can use to perform a variety of operations.</span></span> <span data-ttu-id="f4d61-138">这些函数不能修改。</span><span class="sxs-lookup"><span data-stu-id="f4d61-138">They cannot be modified.</span></span> <span data-ttu-id="f4d61-139">有关详细信息，请参阅[内置函数 (Transact-SQL)](/sql/t-sql/functions/functions)、[系统存储函数 (Transact-SQL)](/sql/relational-databases/system-functions/system-functions-for-transact-sql) 和[动态管理视图和函数 (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/system-dynamic-management-views)。</span><span class="sxs-lookup"><span data-stu-id="f4d61-139">For more information, see [Built-in Functions &#40;Transact-SQL&#41;](/sql/t-sql/functions/functions), [System Stored Functions &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/system-functions-for-transact-sql), and [Dynamic Management Views and Functions &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/system-dynamic-management-views).</span></span>  
  
##  <a name="guidelines"></a><a name="Guidelines"></a> <span data-ttu-id="f4d61-140">准则</span><span class="sxs-lookup"><span data-stu-id="f4d61-140">Guidelines</span></span>  
 <span data-ttu-id="f4d61-141">在函数中，将会区别处理导致语句被取消并继续执行模块（如触发器或存储过程）中的下一个语句的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 错误。</span><span class="sxs-lookup"><span data-stu-id="f4d61-141">[!INCLUDE[tsql](../../includes/tsql-md.md)] errors that cause a statement to be canceled and continue with the next statement in the module (such as triggers or stored procedures) are treated differently inside a function.</span></span> <span data-ttu-id="f4d61-142">在函数中，上述错误会导致停止执行函数。</span><span class="sxs-lookup"><span data-stu-id="f4d61-142">In functions, such errors cause the execution of the function to stop.</span></span> <span data-ttu-id="f4d61-143">接下来该操作导致取消调用该函数的语句。</span><span class="sxs-lookup"><span data-stu-id="f4d61-143">This in turn causes the statement that invoked the function to be canceled.</span></span>  
  
 <span data-ttu-id="f4d61-144">BEGIN...END 块中的语句不能有任何副作用。</span><span class="sxs-lookup"><span data-stu-id="f4d61-144">The statements in a BEGIN...END block cannot have any side effects.</span></span> <span data-ttu-id="f4d61-145">函数副作用是指对具有函数外作用域（例如数据库表的修改）的资源状态的任何永久性更改。</span><span class="sxs-lookup"><span data-stu-id="f4d61-145">Function side effects are any permanent changes to the state of a resource that has a scope outside the function such as a modification to a database table.</span></span> <span data-ttu-id="f4d61-146">函数中的语句唯一能做的更改是对函数上的局部对象（如局部游标或局部变量）的更改。</span><span class="sxs-lookup"><span data-stu-id="f4d61-146">The only changes that can be made by the statements in the function are changes to objects local to the function, such as local cursors or variables.</span></span> <span data-ttu-id="f4d61-147">不能在函数中执行的操作包括：对数据库表的修改，对不在函数上的局部游标进行操作，发送电子邮件，尝试修改目录，以及生成返回至用户的结果集。</span><span class="sxs-lookup"><span data-stu-id="f4d61-147">Modifications to database tables, operations on cursors that are not local to the function, sending e-mail, attempting a catalog modification, and generating a result set that is returned to the user are examples of actions that cannot be performed in a function.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f4d61-148">如果 CREATE FUNCTION 语句对在发出 CREATE FUNCTION 语句时不存在的资源产生副作用，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将执行该语句。</span><span class="sxs-lookup"><span data-stu-id="f4d61-148">If a CREATE FUNCTION statement produces side effects against resources that do not exist when the CREATE FUNCTION statement is issued, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] executes the statement.</span></span> <span data-ttu-id="f4d61-149">但在调用函数时， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 不执行此函数。</span><span class="sxs-lookup"><span data-stu-id="f4d61-149">However, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not execute the function when it is invoked.</span></span>  
  
 <span data-ttu-id="f4d61-150">在查询中指定的函数的实际执行次数在优化器生成的执行计划间可能不同。</span><span class="sxs-lookup"><span data-stu-id="f4d61-150">The number of times that a function specified in a query is actually executed can vary between execution plans built by the optimizer.</span></span> <span data-ttu-id="f4d61-151">示例为 WHERE 子句中的子查询调用的函数。</span><span class="sxs-lookup"><span data-stu-id="f4d61-151">An example is a function invoked by a subquery in a WHERE clause.</span></span> <span data-ttu-id="f4d61-152">子查询及其函数执行的次数会因优化器选择的访问路径的不同而异。</span><span class="sxs-lookup"><span data-stu-id="f4d61-152">The number of times the subquery and its function is executed can vary with different access paths chosen by the optimizer.</span></span>  
  
##  <a name="valid-statements-in-a-function"></a><a name="ValidStatements"></a><span data-ttu-id="f4d61-153">函数中的有效语句</span><span class="sxs-lookup"><span data-stu-id="f4d61-153">Valid Statements in a Function</span></span>  
 <span data-ttu-id="f4d61-154">函数中的有效语句的类型包括：</span><span class="sxs-lookup"><span data-stu-id="f4d61-154">The types of statements that are valid in a function include:</span></span>  
  
-   <span data-ttu-id="f4d61-155">DECLARE 语句，该语句可用于定义函数局部的数据变量和游标。</span><span class="sxs-lookup"><span data-stu-id="f4d61-155">DECLARE statements can be used to define data variables and cursors that are local to the function.</span></span>  
  
-   <span data-ttu-id="f4d61-156">为函数局部对象的赋值，如使用 SET 为标量和表局部变量赋值。</span><span class="sxs-lookup"><span data-stu-id="f4d61-156">Assignments of values to objects local to the function, such as using SET to assign values to scalar and table local variables.</span></span>  
  
-   <span data-ttu-id="f4d61-157">游标操作，该操作引用在函数中声明、打开、关闭和释放的局部游标。</span><span class="sxs-lookup"><span data-stu-id="f4d61-157">Cursor operations that reference local cursors that are declared, opened, closed, and deallocated in the function.</span></span> <span data-ttu-id="f4d61-158">不允许使用 FETCH 语句将数据返回到客户端。</span><span class="sxs-lookup"><span data-stu-id="f4d61-158">FETCH statements that return data to the client are not allowed.</span></span> <span data-ttu-id="f4d61-159">仅允许使用 FETCH 语句通过 INTO 子句给局部变量赋值。</span><span class="sxs-lookup"><span data-stu-id="f4d61-159">Only FETCH statements that assign values to local variables using the INTO clause are allowed.</span></span>  
  
-   <span data-ttu-id="f4d61-160">TRY...CATCH 语句以外的流控制语句。</span><span class="sxs-lookup"><span data-stu-id="f4d61-160">Control-of-flow statements except TRY...CATCH statements.</span></span>  
  
-   <span data-ttu-id="f4d61-161">SELECT 语句，该语句包含具有为函数的局部变量赋值的表达式的选择列表。</span><span class="sxs-lookup"><span data-stu-id="f4d61-161">SELECT statements containing select lists with expressions that assign values to variables that are local to the function.</span></span>  
  
-   <span data-ttu-id="f4d61-162">INSERT、UPDATE 和 DELETE 语句，这些语句修改函数的局部表变量。</span><span class="sxs-lookup"><span data-stu-id="f4d61-162">UPDATE, INSERT, and DELETE statements modifying table variables that are local to the function.</span></span>  
  
-   <span data-ttu-id="f4d61-163">EXECUTE 语句，该语句调用扩展存储过程。</span><span class="sxs-lookup"><span data-stu-id="f4d61-163">EXECUTE statements calling an extended stored procedure.</span></span>  
  
### <a name="built-in-system-functions"></a><span data-ttu-id="f4d61-164">内置系统函数</span><span class="sxs-lookup"><span data-stu-id="f4d61-164">Built-in System Functions</span></span>  
 <span data-ttu-id="f4d61-165">下列具有不确定性的内置函数可以在 Transact-SQL 用户定义函数中使用。</span><span class="sxs-lookup"><span data-stu-id="f4d61-165">The following nondeterministic built-in functions can be used in Transact-SQL user-defined functions.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f4d61-166">CURRENT_TIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="f4d61-166">CURRENT_TIMESTAMP</span></span>|<span data-ttu-id="f4d61-167">@@MAX_CONNECTIONS</span><span class="sxs-lookup"><span data-stu-id="f4d61-167">@@MAX_CONNECTIONS</span></span>|  
|<span data-ttu-id="f4d61-168">GET_TRANSMISSION_STATUS</span><span class="sxs-lookup"><span data-stu-id="f4d61-168">GET_TRANSMISSION_STATUS</span></span>|<span data-ttu-id="f4d61-169">@@PACK_RECEIVED</span><span class="sxs-lookup"><span data-stu-id="f4d61-169">@@PACK_RECEIVED</span></span>|  
|<span data-ttu-id="f4d61-170">GETDATE</span><span class="sxs-lookup"><span data-stu-id="f4d61-170">GETDATE</span></span>|<span data-ttu-id="f4d61-171">@@PACK_SENT</span><span class="sxs-lookup"><span data-stu-id="f4d61-171">@@PACK_SENT</span></span>|  
|<span data-ttu-id="f4d61-172">GETUTCDATE</span><span class="sxs-lookup"><span data-stu-id="f4d61-172">GETUTCDATE</span></span>|<span data-ttu-id="f4d61-173">@@PACKET_ERRORS</span><span class="sxs-lookup"><span data-stu-id="f4d61-173">@@PACKET_ERRORS</span></span>|  
|<span data-ttu-id="f4d61-174">@@CONNECTIONS</span><span class="sxs-lookup"><span data-stu-id="f4d61-174">@@CONNECTIONS</span></span>|<span data-ttu-id="f4d61-175">@@TIMETICKS</span><span class="sxs-lookup"><span data-stu-id="f4d61-175">@@TIMETICKS</span></span>|  
|<span data-ttu-id="f4d61-176">@@CPU_BUSY</span><span class="sxs-lookup"><span data-stu-id="f4d61-176">@@CPU_BUSY</span></span>|<span data-ttu-id="f4d61-177">@@TOTAL_ERRORS</span><span class="sxs-lookup"><span data-stu-id="f4d61-177">@@TOTAL_ERRORS</span></span>|  
|<span data-ttu-id="f4d61-178">@@DBTS</span><span class="sxs-lookup"><span data-stu-id="f4d61-178">@@DBTS</span></span>|<span data-ttu-id="f4d61-179">@@TOTAL_READ</span><span class="sxs-lookup"><span data-stu-id="f4d61-179">@@TOTAL_READ</span></span>|  
|<span data-ttu-id="f4d61-180">@@IDLE</span><span class="sxs-lookup"><span data-stu-id="f4d61-180">@@IDLE</span></span>|<span data-ttu-id="f4d61-181">@@TOTAL_WRITE</span><span class="sxs-lookup"><span data-stu-id="f4d61-181">@@TOTAL_WRITE</span></span>|  
|<span data-ttu-id="f4d61-182">@@IO_BUSY</span><span class="sxs-lookup"><span data-stu-id="f4d61-182">@@IO_BUSY</span></span>||  
  
 <span data-ttu-id="f4d61-183">下列不确定性内置函数不能在 Transact-SQL 用户定义函数中使用。</span><span class="sxs-lookup"><span data-stu-id="f4d61-183">The following nondeterministic built-in functions cannot be used in Transact-SQL user-defined functions.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f4d61-184">NEWID</span><span class="sxs-lookup"><span data-stu-id="f4d61-184">NEWID</span></span>|<span data-ttu-id="f4d61-185">RAND</span><span class="sxs-lookup"><span data-stu-id="f4d61-185">RAND</span></span>|  
|<span data-ttu-id="f4d61-186">NEWSEQUENTIALID</span><span class="sxs-lookup"><span data-stu-id="f4d61-186">NEWSEQUENTIALID</span></span>|<span data-ttu-id="f4d61-187">TEXTPTR</span><span class="sxs-lookup"><span data-stu-id="f4d61-187">TEXTPTR</span></span>|  
  
 <span data-ttu-id="f4d61-188">有关确定性和不确定性的内置系统函数的列表，请参阅[确定性和不确定性的函数](../user-defined-functions/deterministic-and-nondeterministic-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="f4d61-188">For a list of deterministic and nondeterministic built-in system functions, see [Deterministic and Nondeterministic Functions](../user-defined-functions/deterministic-and-nondeterministic-functions.md).</span></span>  
  
##  <a name="schema-bound-functions"></a><a name="SchemaBound"></a><span data-ttu-id="f4d61-189">绑定到架构的函数</span><span class="sxs-lookup"><span data-stu-id="f4d61-189">Schema-Bound Functions</span></span>  
 <span data-ttu-id="f4d61-190">CREATE FUNCTION 支持 SCHEMABINDING 子句，后者可将函数绑定到它引用的任何对象（如表、视图和其他用户定义函数）的架构。</span><span class="sxs-lookup"><span data-stu-id="f4d61-190">CREATE FUNCTION supports a SCHEMABINDING clause that binds the function to the schema of any objects it references, such as tables, views, and other user-defined functions.</span></span> <span data-ttu-id="f4d61-191">尝试更改或删除绑定到架构的函数所引用的任何对象失败。</span><span class="sxs-lookup"><span data-stu-id="f4d61-191">An attempt to alter or drop any object referenced by a schema-bound function fails.</span></span>  
  
 <span data-ttu-id="f4d61-192">必须满足以下条件才能在 CREATE FUNCTION 中指定 SCHEMABINDING：</span><span class="sxs-lookup"><span data-stu-id="f4d61-192">These conditions must be met before you can specify SCHEMABINDING in CREATE FUNCTION:</span></span>  
  
-   <span data-ttu-id="f4d61-193">该函数引用的所有视图和用户定义函数必须是绑定到架构的视图和函数。</span><span class="sxs-lookup"><span data-stu-id="f4d61-193">All views and user-defined functions referenced by the function must be schema-bound.</span></span>  
  
-   <span data-ttu-id="f4d61-194">该函数引用的所有对象必须与该函数位于同一数据库中。</span><span class="sxs-lookup"><span data-stu-id="f4d61-194">All objects referenced by the function must be in the same database as the function.</span></span> <span data-ttu-id="f4d61-195">必须使用由一部分或两部分构成的名称来引用对象。</span><span class="sxs-lookup"><span data-stu-id="f4d61-195">The objects must be referenced using either one-part or two-part names.</span></span>  
  
-   <span data-ttu-id="f4d61-196">必须具有该函数中引用的所有对象（表、视图和用户定义函数）的 REFERENCES 权限。</span><span class="sxs-lookup"><span data-stu-id="f4d61-196">You must have REFERENCES permission on all objects (tables, views, and user-defined functions) referenced in the function.</span></span>  
  
 <span data-ttu-id="f4d61-197">可使用 ALTER FUNCTION 删除架构绑定。</span><span class="sxs-lookup"><span data-stu-id="f4d61-197">You can use ALTER FUNCTION to remove the schema binding.</span></span> <span data-ttu-id="f4d61-198">ALTER FUNCTION 语句会在不指定 WITH SCHEMABINDING 的情况下重新定义函数。</span><span class="sxs-lookup"><span data-stu-id="f4d61-198">The ALTER FUNCTION statement should redefine the function without specifying WITH SCHEMABINDING.</span></span>  
  
##  <a name="specifying-parameters"></a><a name="Parameters"></a><span data-ttu-id="f4d61-199">指定参数</span><span class="sxs-lookup"><span data-stu-id="f4d61-199">Specifying Parameters</span></span>  
 <span data-ttu-id="f4d61-200">用户定义函数采用零个或多个输入参数并返回标量值或表。</span><span class="sxs-lookup"><span data-stu-id="f4d61-200">A user-defined function takes zero or more input parameters and returns either a scalar value or a table.</span></span> <span data-ttu-id="f4d61-201">一个函数最多可以有 1024 个输入参数。</span><span class="sxs-lookup"><span data-stu-id="f4d61-201">A function can have a maximum of 1024 input parameters.</span></span> <span data-ttu-id="f4d61-202">如果函数的参数有默认值，则调用该函数时必须指定 DEFAULT 关键字，才能获取默认值。</span><span class="sxs-lookup"><span data-stu-id="f4d61-202">When a parameter of the function has a default value, the keyword DEFAULT must be specified when calling the function to get the default value.</span></span> <span data-ttu-id="f4d61-203">此行为与在用户定义存储过程中具有默认值的参数不同，在后一种情况下，忽略参数同样意味着使用默认值。</span><span class="sxs-lookup"><span data-stu-id="f4d61-203">This behavior is different from parameters with default values in user-defined stored procedures in which omitting the parameter also implies the default value.</span></span> <span data-ttu-id="f4d61-204">用户定义函数不支持输出参数。</span><span class="sxs-lookup"><span data-stu-id="f4d61-204">User-defined functions do not support output parameters.</span></span>  
  
##  <a name="related-tasks"></a><a name="Tasks"></a> <span data-ttu-id="f4d61-205">相关任务</span><span class="sxs-lookup"><span data-stu-id="f4d61-205">Related Tasks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f4d61-206">**任务说明**</span><span class="sxs-lookup"><span data-stu-id="f4d61-206">**Task Description**</span></span>|<span data-ttu-id="f4d61-207">**主题**</span><span class="sxs-lookup"><span data-stu-id="f4d61-207">**Topic**</span></span>|  
|<span data-ttu-id="f4d61-208">介绍如何创建 Transact-SQL 用户定义函数。</span><span class="sxs-lookup"><span data-stu-id="f4d61-208">Describes how to create a Transact-SQL user-defined function.</span></span>|[<span data-ttu-id="f4d61-209">创建用户定义函数（数据库引擎）</span><span class="sxs-lookup"><span data-stu-id="f4d61-209">Create User-defined Functions &#40;Database Engine&#41;</span></span>](../user-defined-functions/create-user-defined-functions-database-engine.md)|  
|<span data-ttu-id="f4d61-210">介绍如何创建 CLR 函数。</span><span class="sxs-lookup"><span data-stu-id="f4d61-210">Describes how create a CLR function.</span></span>|[<span data-ttu-id="f4d61-211">创建 CLR 函数</span><span class="sxs-lookup"><span data-stu-id="f4d61-211">Create CLR Functions</span></span>](../user-defined-functions/create-clr-functions.md)|  
|<span data-ttu-id="f4d61-212">介绍如何创建用户定义聚合函数。</span><span class="sxs-lookup"><span data-stu-id="f4d61-212">Describes how to create a user-defined aggregate function</span></span>|[<span data-ttu-id="f4d61-213">创建用户定义聚合</span><span class="sxs-lookup"><span data-stu-id="f4d61-213">Create User-defined Aggregates</span></span>](../user-defined-functions/create-user-defined-aggregates.md)|  
|<span data-ttu-id="f4d61-214">介绍如何修改 Transact-SQL 用户定义函数。</span><span class="sxs-lookup"><span data-stu-id="f4d61-214">Describes how to modify a Transact-SQL user-defined function.</span></span>|[<span data-ttu-id="f4d61-215">修改用户定义的函数</span><span class="sxs-lookup"><span data-stu-id="f4d61-215">Modify User-defined Functions</span></span>](../user-defined-functions/user-defined-functions.md)|  
|<span data-ttu-id="f4d61-216">介绍如何删除用户定义函数。</span><span class="sxs-lookup"><span data-stu-id="f4d61-216">Describes how to delete a user-defined function.</span></span>|[<span data-ttu-id="f4d61-217">删除用户定义的函数</span><span class="sxs-lookup"><span data-stu-id="f4d61-217">Delete User-defined Functions</span></span>](../user-defined-functions/delete-user-defined-functions.md)|  
|<span data-ttu-id="f4d61-218">介绍如何执行用户定义函数。</span><span class="sxs-lookup"><span data-stu-id="f4d61-218">Describes how to execute a user-defined function.</span></span>|[<span data-ttu-id="f4d61-219">执行用户定义的函数</span><span class="sxs-lookup"><span data-stu-id="f4d61-219">Execute User-defined Functions</span></span>](../user-defined-functions/execute-user-defined-functions.md)|  
|<span data-ttu-id="f4d61-220">介绍如何重命名用户定义函数。</span><span class="sxs-lookup"><span data-stu-id="f4d61-220">Describes how to rename a user-defined function</span></span>|[<span data-ttu-id="f4d61-221">重命名用户定义函数</span><span class="sxs-lookup"><span data-stu-id="f4d61-221">Rename User-defined Functions</span></span>](../user-defined-functions/rename-user-defined-functions.md)|  
|<span data-ttu-id="f4d61-222">介绍如何查看用户定义函数的定义。</span><span class="sxs-lookup"><span data-stu-id="f4d61-222">Describes how to view the definition of a user-defined function.</span></span>|[<span data-ttu-id="f4d61-223">查看用户定义的函数</span><span class="sxs-lookup"><span data-stu-id="f4d61-223">View User-defined Functions</span></span>](view-user-defined-functions.md)|  
  
  
