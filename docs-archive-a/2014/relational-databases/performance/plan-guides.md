---
title: 计划指南 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- TEMPLATE plan guide
- SQL plan guides
- OPTIMIZE FOR query hint
- RECOMPILE query hint
- OBJECT plan guide
- plan guides [SQL Server], about plan guides
- OPTION clause
- plan guides [SQL Server]
- USE PLAN query hint
ms.assetid: bfc97632-c14c-4768-9dc5-a9c512f6b2bd
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c97682163313a56acb8521174fa8d4012a69b529
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588485"
---
# <a name="plan-guides"></a><span data-ttu-id="b7836-102">计划指南</span><span class="sxs-lookup"><span data-stu-id="b7836-102">Plan Guides</span></span>
  <span data-ttu-id="b7836-103">如果您无法或不希望直接在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中更改实际查询文本，则可以使用计划指南来优化查询性能。</span><span class="sxs-lookup"><span data-stu-id="b7836-103">Plan guides let you optimize the performance of queries when you cannot or do not want to directly change the text of the actual query in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="b7836-104">计划指南通过将查询提示或固定的查询计划附加到查询来影响查询的优化。</span><span class="sxs-lookup"><span data-stu-id="b7836-104">Plan guides influence the optimization of queries by attaching query hints or a fixed query plan to them.</span></span> <span data-ttu-id="b7836-105">当第三方供应商提供的数据库应用程序中的一个小的查询子集没有按预期执行时，计划指南将很有用。</span><span class="sxs-lookup"><span data-stu-id="b7836-105">Plan guides can be useful when a small subset of queries in a database application provided by a third-party vendor are not performing as expected.</span></span> <span data-ttu-id="b7836-106">在计划指南中，您需要指定要优化的 Transact-SQL 语句以及包含要使用的查询提示的 OPTION 子句或要用于优化查询的特定查询计划。</span><span class="sxs-lookup"><span data-stu-id="b7836-106">In the plan guide, you specify the Transact-SQL statement that you want optimized and either an OPTION clause that contains the query hints you want to use or a specific query plan you want to use to optimize the query.</span></span> <span data-ttu-id="b7836-107">当执行查询时， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将 Transact-SQL 语句与计划指南进行匹配，然后在运行时将此 OPTION 子句附加到查询，或使用指定的查询计划。</span><span class="sxs-lookup"><span data-stu-id="b7836-107">When the query executes, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] matches the Transact-SQL statement to the plan guide and attaches the OPTION clause to the query at run time or uses the specified query plan.</span></span>  
  
 <span data-ttu-id="b7836-108">可创建的计划指南总数仅受可用系统资源的限制。</span><span class="sxs-lookup"><span data-stu-id="b7836-108">The total number of plan guides you can create is limited only by available system resources.</span></span> <span data-ttu-id="b7836-109">尽管如此，计划指南还是应当限于针对提高或稳定性能的关键查询。</span><span class="sxs-lookup"><span data-stu-id="b7836-109">Nevertheless, plan guides should be limited to mission-critical queries that are targeted for improved or stabilized performance.</span></span> <span data-ttu-id="b7836-110">计划指南不应用来影响已部署应用程序的大部分查询负荷。</span><span class="sxs-lookup"><span data-stu-id="b7836-110">Plan guides should not be used to influence most of the query load of a deployed application.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b7836-111">计划指南不适用于每个 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b7836-111">Plan guides cannot be used in every edition of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="b7836-112">有关各个版本支持的功能列表 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，请参阅 SQL Server 2014 的各个[版本支持的功能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="b7836-112">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span> <span data-ttu-id="b7836-113">计划指南在任何版本中可见。</span><span class="sxs-lookup"><span data-stu-id="b7836-113">Plan guides are visible in any edition.</span></span> <span data-ttu-id="b7836-114">包含计划指南的数据库可以附加到任何版本。</span><span class="sxs-lookup"><span data-stu-id="b7836-114">You can also attach a database that contains plan guides to any edition.</span></span> <span data-ttu-id="b7836-115">将数据库还原或附加到升级版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]后，计划指南保持不变。</span><span class="sxs-lookup"><span data-stu-id="b7836-115">Plan guides remain intact when you restore or attach a database to an upgraded version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="types-of-plan-guides"></a><span data-ttu-id="b7836-116">计划指南的类型</span><span class="sxs-lookup"><span data-stu-id="b7836-116">Types of Plan Guides</span></span>  
 <span data-ttu-id="b7836-117">可以创建以下类型的计划指南。</span><span class="sxs-lookup"><span data-stu-id="b7836-117">The following types of plan guides can be created.</span></span>  
  
 <span data-ttu-id="b7836-118">OBJECT 计划指南</span><span class="sxs-lookup"><span data-stu-id="b7836-118">OBJECT plan guide</span></span>  
 <span data-ttu-id="b7836-119">OBJECT 计划指南与在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 存储过程、用户定义标量函数、多语句表值用户定义函数和 DML 触发器上下文中执行的查询匹配。</span><span class="sxs-lookup"><span data-stu-id="b7836-119">An OBJECT plan guide matches queries that execute in the context of [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedures, scalar user-defined functions, multi-statement table-valued user-defined functions, and DML triggers.</span></span>  
  
 <span data-ttu-id="b7836-120">假设下面的存储过程采用 `@Country`_`region` 参数，位于对 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 数据库部署的数据库应用程序中：</span><span class="sxs-lookup"><span data-stu-id="b7836-120">Suppose the following stored procedure, which takes the `@Country`_`region` parameter, is in a database application that is deployed against the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database:</span></span>  
  
```  
CREATE PROCEDURE Sales.GetSalesOrderByCountry (@Country_region nvarchar(60))  
AS  
BEGIN  
    SELECT *  
    FROM Sales.SalesOrderHeader AS h, Sales.Customer AS c,   
        Sales.SalesTerritory AS t  
    WHERE h.CustomerID = c.CustomerID  
        AND c.TerritoryID = t.TerritoryID  
        AND CountryRegionCode = @Country_region  
END;  
```  
  
 <span data-ttu-id="b7836-121">假设已为 `@Country`_`region = N'AU'` （澳大利亚）编译并优化了此存储过程。</span><span class="sxs-lookup"><span data-stu-id="b7836-121">Assume that this stored procedure has been compiled and optimized for `@Country`_`region = N'AU'` (Australia).</span></span> <span data-ttu-id="b7836-122">但是，由于来自澳大利亚的销售订单相对较少，当使用具有较多销售订单的国家/地区的参数值执行查询时，性能会降低。</span><span class="sxs-lookup"><span data-stu-id="b7836-122">However, because there are relatively few sales orders that originate from Australia, performance decreases when the query executes using parameter values of countries with more sales orders.</span></span> <span data-ttu-id="b7836-123">因为大多数销售订单来自美国，所以针对 `@Country`\_`region = N'US'` 生成的查询计划的性能对于所有可能的 `@Country`\_`region` 参数值而言都可能会更好一些。</span><span class="sxs-lookup"><span data-stu-id="b7836-123">Because the most sales orders originate in the United States, a query plan that is generated for `@Country`\_`region = N'US'` would likely perform better for all possible values of the `@Country`\_`region` parameter.</span></span>  
  
 <span data-ttu-id="b7836-124">您可以通过修改存储过程以将 `OPTIMIZE FOR` 查询提示添加到查询中来解决这一问题。</span><span class="sxs-lookup"><span data-stu-id="b7836-124">You could address this problem by modifying the stored procedure to add the `OPTIMIZE FOR` query hint to the query.</span></span> <span data-ttu-id="b7836-125">但是，因为存储过程在部署应用程序中，所以您不能直接修改应用程序代码。</span><span class="sxs-lookup"><span data-stu-id="b7836-125">However, because the stored procedure is in a deployed application, you cannot directly modify the application code.</span></span> <span data-ttu-id="b7836-126">不过，您可以在 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 数据库中创建下面的计划指南。</span><span class="sxs-lookup"><span data-stu-id="b7836-126">Instead, you can create the following plan guide in the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span>  
  
```  
sp_create_plan_guide   
@name = N'Guide1',  
@stmt = N'SELECT *FROM Sales.SalesOrderHeader AS h,  
        Sales.Customer AS c,  
        Sales.SalesTerritory AS t  
        WHERE h.CustomerID = c.CustomerID   
            AND c.TerritoryID = t.TerritoryID  
            AND CountryRegionCode = @Country_region',  
@type = N'OBJECT',  
@module_or_batch = N'Sales.GetSalesOrderByCountry',  
@params = NULL,  
@hints = N'OPTION (OPTIMIZE FOR (@Country_region = N''US''))';  
```  
  
 <span data-ttu-id="b7836-127">执行在 `sp_create_plan_guide` 语句中指定的查询时，将在优化之前修改该查询以使其包括 `OPTIMIZE FOR (@Country = N''US'')` 子句。</span><span class="sxs-lookup"><span data-stu-id="b7836-127">When the query specified in the `sp_create_plan_guide` statement executes, the query is modified before optimization to include the `OPTIMIZE FOR (@Country = N''US'')` clause.</span></span>  
  
 <span data-ttu-id="b7836-128">SQL 计划指南</span><span class="sxs-lookup"><span data-stu-id="b7836-128">SQL plan guide</span></span>  
 <span data-ttu-id="b7836-129">SQL 计划指南与在独立 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句和不属于数据库对象的批处理上下文中执行的查询匹配。</span><span class="sxs-lookup"><span data-stu-id="b7836-129">An SQL plan guide matches queries that execute in the context of stand-alone [!INCLUDE[tsql](../../includes/tsql-md.md)] statements and batches that are not part of a database object.</span></span> <span data-ttu-id="b7836-130">基于 SQL 的计划指南还可用于与参数化为指定形式的查询匹配。</span><span class="sxs-lookup"><span data-stu-id="b7836-130">SQL-based plan guides can also be used to match queries that parameterize to a specified form.</span></span> <span data-ttu-id="b7836-131">SQL 计划指南适用于独立 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句和批处理。</span><span class="sxs-lookup"><span data-stu-id="b7836-131">SQL plan guides apply to stand-alone [!INCLUDE[tsql](../../includes/tsql-md.md)] statements and batches.</span></span> <span data-ttu-id="b7836-132">通常，这些语句由应用程序使用 [sp_executesql](/sql/relational-databases/system-stored-procedures/sp-executesql-transact-sql) 系统存储过程来提交。</span><span class="sxs-lookup"><span data-stu-id="b7836-132">Frequently, these statements are submitted by an application by using the [sp_executesql](/sql/relational-databases/system-stored-procedures/sp-executesql-transact-sql) system stored procedure.</span></span> <span data-ttu-id="b7836-133">以下面的独立批处理为例：</span><span class="sxs-lookup"><span data-stu-id="b7836-133">For example, consider the following stand-alone batch:</span></span>  
  
```  
SELECT TOP 1 * FROM Sales.SalesOrderHeader ORDER BY OrderDate DESC;  
```  
  
 <span data-ttu-id="b7836-134">为了防止对该查询生成并行执行计划，请创建以下计划指南并在 `MAXDOP` 参数中将 `1` 查询提示设置为 `@hints` 。</span><span class="sxs-lookup"><span data-stu-id="b7836-134">To prevent a parallel execution plan from being generated on this query, create the following plan guide and set the `MAXDOP` query hint to `1` in the `@hints` parameter.</span></span>  
  
```  
sp_create_plan_guide   
@name = N'Guide2',   
@stmt = N'SELECT TOP 1 * FROM Sales.SalesOrderHeader ORDER BY OrderDate DESC',  
@type = N'SQL',  
@module_or_batch = NULL,   
@params = NULL,   
@hints = N'OPTION (MAXDOP 1)';  
```  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b7836-135">为 `@module_or_batch` 语句的 `@params` 和 `sp_create_plan guide` 参数提供的值必须与在实际查询中提交的相应文本匹配。</span><span class="sxs-lookup"><span data-stu-id="b7836-135">The values that are supplied for the `@module_or_batch` and `@params` arguments of the `sp_create_plan guide` statement must match the corresponding text submitted in the actual query.</span></span> <span data-ttu-id="b7836-136">有关详细信息，请参阅 [sp_create_plan_guide (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) 语句的 [使用 SQL Server Profiler 创建和测试计划指南](plan-guides.md)中更改实际查询文本，则可以使用计划指南来优化查询性能。</span><span class="sxs-lookup"><span data-stu-id="b7836-136">For more information, see [sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) and [Use SQL Server Profiler to Create and Test Plan Guides](plan-guides.md).</span></span>  
  
 <span data-ttu-id="b7836-137">PARAMETERIZATION 数据库选项设置为 FORCED 后，或者创建了指定参数化查询类的 TEMPLATE 计划指南后，还可以对参数化为相同形式的查询创建 SQL 计划指南。</span><span class="sxs-lookup"><span data-stu-id="b7836-137">SQL plan guides can also be created on queries that parameterize to the same form when the PARAMETERIZATION database option is SET to FORCED, or when a TEMPLATE plan guide is created specifying that a parameterized class of queries.</span></span>  
  
 <span data-ttu-id="b7836-138">TEMPLATE 计划指南</span><span class="sxs-lookup"><span data-stu-id="b7836-138">TEMPLATE plan guide</span></span>  
 <span data-ttu-id="b7836-139">TEMPLATE 计划指南与参数化为指定形式的独立查询匹配。</span><span class="sxs-lookup"><span data-stu-id="b7836-139">A TEMPLATE plan guide matches stand-alone queries that parameterize to a specified form.</span></span> <span data-ttu-id="b7836-140">这些计划指南用于覆盖查询类的数据库的当前 PARAMETERIZATION 数据库 SET 选项。</span><span class="sxs-lookup"><span data-stu-id="b7836-140">These plan guides are used to override the current PARAMETERIZATION database SET option of a database for a class of queries.</span></span>  
  
 <span data-ttu-id="b7836-141">您可以在以下任一情况下创建 TEMPLATE 计划指南：</span><span class="sxs-lookup"><span data-stu-id="b7836-141">You can create a TEMPLATE plan guide in either of the following situations:</span></span>  
  
-   <span data-ttu-id="b7836-142">PARAMETERIZATION 数据库选项设置为 FORCED，但是您要按照简单参数化规则编译某些查询。</span><span class="sxs-lookup"><span data-stu-id="b7836-142">The PARAMETERIZATION database option is SET to FORCED, but there are queries you want compiled according to the rules of simple parameterization.</span></span>  
  
-   <span data-ttu-id="b7836-143">PARAMETERIZATION 数据库选项设置为 SIMPLE（默认设置），但是您要尝试对某一类查询执行强制参数化。</span><span class="sxs-lookup"><span data-stu-id="b7836-143">The PARAMETERIZATION database option is SET to SIMPLE (the default setting), but you want forced parameterization to be tried on a class of queries.</span></span>  
  
## <a name="plan-guide-matching-requirements"></a><span data-ttu-id="b7836-144">符合要求的计划指南</span><span class="sxs-lookup"><span data-stu-id="b7836-144">Plan Guide Matching Requirements</span></span>  
 <span data-ttu-id="b7836-145">计划指南的作用域是在其中创建这些计划指南的数据库。</span><span class="sxs-lookup"><span data-stu-id="b7836-145">Plan guides are scoped to the database in which they are created.</span></span> <span data-ttu-id="b7836-146">因此，执行查询时，只有处于当前状态的数据库中的计划指南可以与该查询匹配。</span><span class="sxs-lookup"><span data-stu-id="b7836-146">Therefore, only plan guides that are in the database that is current when a query executes can be matched to the query.</span></span> <span data-ttu-id="b7836-147">例如，如果 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 是当前数据库并执行下面的查询：</span><span class="sxs-lookup"><span data-stu-id="b7836-147">For example, if [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] is the current database and the following query executes:</span></span>  
  
 `SELECT FirstName, LastName FROM Person.Person;`  
  
 <span data-ttu-id="b7836-148">则只有 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 数据库中的计划指南可以与此查询匹配。</span><span class="sxs-lookup"><span data-stu-id="b7836-148">Only plan guides in the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database are eligible to be matched to this query.</span></span> <span data-ttu-id="b7836-149">但是，如果 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 是当前数据库并运行下列语句：</span><span class="sxs-lookup"><span data-stu-id="b7836-149">However, if [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] is the current database and the following statements are run:</span></span>  
  
 `USE DB1;`  
  
 `SELECT FirstName, LastName FROM Person.Person;`  
  
 <span data-ttu-id="b7836-150">则只有 `DB1` 中的计划指南可以与该查询匹配，这是因为该查询是在 `DB1`的上下文中执行的。</span><span class="sxs-lookup"><span data-stu-id="b7836-150">Only plan guides in `DB1` are eligible to be matched to the query because the query is executing in the context of `DB1`.</span></span>  
  
 <span data-ttu-id="b7836-151">对于基于 SQL 或 TEMPLATE 的计划指南， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 通过对 @module_or_batch 参数和 @params 参数的值逐个字符地进行比较来将这两个值与查询匹配。</span><span class="sxs-lookup"><span data-stu-id="b7836-151">For SQL- or TEMPLATE-based plan guides, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] matches the values for the @module_or_batch and @params arguments to a query by comparing the two values character by character.</span></span> <span data-ttu-id="b7836-152">这意味着必须提供与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在实际批处理中接收的文本完全相同的文本。</span><span class="sxs-lookup"><span data-stu-id="b7836-152">This means you must provide the text exactly as [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] receives it in the actual batch.</span></span>  
  
 <span data-ttu-id="b7836-153">当 @type = 'SQL' 且 @module_or_batch 设置为 NULL 时，则将 @module_or_batch 的值设置为 @stmt 的值。这意味着 *statement_text* 值的提供格式必须与其提交到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]时所采用的格式完全相同（字符对字符）。</span><span class="sxs-lookup"><span data-stu-id="b7836-153">When @type = 'SQL' and @module_or_batch is set to NULL, the value of @module_or_batch is set to the value of @stmt. This means that the value for *statement_text* must be provided in the identical format, character-for-character, as it is submitted to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="b7836-154">不会执行内部转换来帮助完成该匹配。</span><span class="sxs-lookup"><span data-stu-id="b7836-154">No internal conversion is performed to facilitate this match.</span></span>  
  
 <span data-ttu-id="b7836-155">当常规（SQL 或 OBJECT）计划指南和 TEMPLATE 计划指南都适用于语句时，将只使用常规计划指南。</span><span class="sxs-lookup"><span data-stu-id="b7836-155">When both a regular (SQL or OBJECT) plan guide and a TEMPLATE plan guide can apply to a statement, only the regular plan guide will be used.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b7836-156">包含要对其创建计划指南的语句的批处理不能包含 USE *database* 语句。</span><span class="sxs-lookup"><span data-stu-id="b7836-156">The batch that contains the statement on which you want to create a plan guide cannot contain a USE *database* statement.</span></span>  
  
## <a name="plan-guide-effect-on-the-plan-cache"></a><span data-ttu-id="b7836-157">计划指南对计划缓存的影响</span><span class="sxs-lookup"><span data-stu-id="b7836-157">Plan Guide Effect on the Plan Cache</span></span>  
 <span data-ttu-id="b7836-158">对模块创建计划指南将会从计划缓存中删除该模块的查询计划。</span><span class="sxs-lookup"><span data-stu-id="b7836-158">Creating a plan guide on a module removes the query plan for that module from the plan cache.</span></span> <span data-ttu-id="b7836-159">对批处理创建类型为 OBJECT 或 SQL 的计划指南会删除具有相同哈希值的批处理的查询计划。</span><span class="sxs-lookup"><span data-stu-id="b7836-159">Creating a plan guide of type OBJECT or SQL on a batch removes the query plan for a batch that has the same hash value.</span></span> <span data-ttu-id="b7836-160">创建类型为 TEMPLATE 的计划指南会从该数据库中的计划缓存中删除所有单语句批处理。</span><span class="sxs-lookup"><span data-stu-id="b7836-160">Creating a plan guide of type TEMPLATE removes all single-statement batches from the plan cache within that database.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="b7836-161">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="b7836-161">Related Tasks</span></span>  
  
|<span data-ttu-id="b7836-162">任务</span><span class="sxs-lookup"><span data-stu-id="b7836-162">Task</span></span>|<span data-ttu-id="b7836-163">主题</span><span class="sxs-lookup"><span data-stu-id="b7836-163">Topic</span></span>|  
|----------|-----------|  
|<span data-ttu-id="b7836-164">说明如何创建计划指南。</span><span class="sxs-lookup"><span data-stu-id="b7836-164">Describes how to create a plan guide.</span></span>|[<span data-ttu-id="b7836-165">创建新的计划指南</span><span class="sxs-lookup"><span data-stu-id="b7836-165">Create a New Plan Guide</span></span>](create-a-new-plan-guide.md)|  
|<span data-ttu-id="b7836-166">说明如何为参数化查询创建计划指南。</span><span class="sxs-lookup"><span data-stu-id="b7836-166">Describes how to create a plan guide for parameterized queries.</span></span>|[<span data-ttu-id="b7836-167">为参数化查询创建计划指南</span><span class="sxs-lookup"><span data-stu-id="b7836-167">Create a Plan Guide for Parameterized Queries</span></span>](create-a-plan-guide-for-parameterized-queries.md)|  
|<span data-ttu-id="b7836-168">说明如何通过使用计划指南控制查询参数化行为。</span><span class="sxs-lookup"><span data-stu-id="b7836-168">Describes how to control query parameterization behavior by using plan guides.</span></span>|[<span data-ttu-id="b7836-169">使用计划指南指定查询参数化行为</span><span class="sxs-lookup"><span data-stu-id="b7836-169">Specify Query Parameterization Behavior by Using Plan Guides</span></span>](specify-query-parameterization-behavior-by-using-plan-guides.md)|  
|<span data-ttu-id="b7836-170">说明如何在计划指南中包括固定查询计划。</span><span class="sxs-lookup"><span data-stu-id="b7836-170">Describes how to include a fixed query plan in a plan guide.</span></span>|[<span data-ttu-id="b7836-171">将现有查询计划应用到计划指南</span><span class="sxs-lookup"><span data-stu-id="b7836-171">Apply a Fixed Query Plan to a Plan Guide</span></span>](apply-a-fixed-query-plan-to-a-plan-guide.md)|  
|<span data-ttu-id="b7836-172">说明如何在计划指南中指定查询提示。</span><span class="sxs-lookup"><span data-stu-id="b7836-172">Describes how to specify query hints in a plan guide.</span></span>|[<span data-ttu-id="b7836-173">将查询提示附加到计划指南</span><span class="sxs-lookup"><span data-stu-id="b7836-173">Attach Query Hints to a Plan Guide</span></span>](attach-query-hints-to-a-plan-guide.md)|  
|<span data-ttu-id="b7836-174">说明如何查看计划指南属性。</span><span class="sxs-lookup"><span data-stu-id="b7836-174">Describes how to view plan guide properties.</span></span>|[<span data-ttu-id="b7836-175">查看计划指南属性</span><span class="sxs-lookup"><span data-stu-id="b7836-175">View Plan Guide Properties</span></span>](view-plan-guide-properties.md)|  
|<span data-ttu-id="b7836-176">说明如何使用 SQL Server 事件探查器创建和测试计划指南。</span><span class="sxs-lookup"><span data-stu-id="b7836-176">Describes how to use SQL Server Profiler to create and test plan guides.</span></span>|[<span data-ttu-id="b7836-177">使用 SQL Server Profiler 创建和测试计划指南</span><span class="sxs-lookup"><span data-stu-id="b7836-177">Use SQL Server Profiler to Create and Test Plan Guides</span></span>](plan-guides.md)|  
|<span data-ttu-id="b7836-178">说明如何验证计划指南。</span><span class="sxs-lookup"><span data-stu-id="b7836-178">Describes how to validate plan guides.</span></span>|[<span data-ttu-id="b7836-179">升级后验证计划指南</span><span class="sxs-lookup"><span data-stu-id="b7836-179">Validate Plan Guides After Upgrade</span></span>](validate-plan-guides-after-upgrade.md)|  
  
## <a name="see-also"></a><span data-ttu-id="b7836-180">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b7836-180">See Also</span></span>  
 <span data-ttu-id="b7836-181">[sp_create_plan_guide (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b7836-181">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span></span>  
 <span data-ttu-id="b7836-182">[sp_create_plan_guide_from_handle (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b7836-182">[sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql) </span></span>  
 <span data-ttu-id="b7836-183">[sp_control_plan_guide (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-control-plan-guide-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b7836-183">[sp_control_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-control-plan-guide-transact-sql) </span></span>  
 <span data-ttu-id="b7836-184">[sys.plan_guides (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-plan-guides-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b7836-184">[sys.plan_guides &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-plan-guides-transact-sql) </span></span>  
 [<span data-ttu-id="b7836-185">sys.fn_validate_plan_guide (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b7836-185">sys.fn_validate_plan_guide &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-functions/sys-fn-validate-plan-guide-transact-sql)  
  
  
