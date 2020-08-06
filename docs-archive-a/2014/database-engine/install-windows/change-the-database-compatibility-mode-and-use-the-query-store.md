---
title: 迁移查询计划 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- query plans [SQL Server], migrating
- upgrading SQL Server, migrating query plans
- plan guides [SQL Server], migrating query plans
ms.assetid: 7e02a137-6867-4f6a-a45a-2b02674f7e65
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: dafd3a5f8a460bb08e63919c2cb853ad74dc2f1f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690790"
---
# <a name="migrate-query-plans"></a><span data-ttu-id="bb054-102">迁移查询计划</span><span class="sxs-lookup"><span data-stu-id="bb054-102">Migrate Query Plans</span></span>
  <span data-ttu-id="bb054-103">大多数情况下，将数据库升级到最新版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 会提高查询性能。</span><span class="sxs-lookup"><span data-stu-id="bb054-103">In most cases, upgrading a database to the most recent version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will result in improved query performance.</span></span> <span data-ttu-id="bb054-104">但是，如果您具有已针对性能进行过认真优化的任务关键查询，在升级前最好为每个查询创建一个计划指南，以保留这些查询的查询计划。</span><span class="sxs-lookup"><span data-stu-id="bb054-104">However, if you have mission-critical queries that have been carefully tuned for performance, you may want to preserve the query plans for these queries before upgrading by creating a plan guide for each query.</span></span> <span data-ttu-id="bb054-105">如果在升级后，查询优化器为一个或多个查询选择了效率较低的计划，则可以启用这些计划指南并强制查询优化器使用升级前的计划。</span><span class="sxs-lookup"><span data-stu-id="bb054-105">If, after upgrading, the query optimizer chooses a less efficient plan for one or more of the queries, you can enable the plan guides and force the query optimizer to use the pre-upgrade plans.</span></span>  
  
 <span data-ttu-id="bb054-106">若要在升级前创建计划指南，请按照以下步骤执行操作：</span><span class="sxs-lookup"><span data-stu-id="bb054-106">To create plan guides before upgrading follow these steps:</span></span>  
  
1.  <span data-ttu-id="bb054-107">使用[sp_create_plan_guide](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)存储过程并在 USE plan 查询提示中指定查询计划，记录每个任务关键查询的当前计划。</span><span class="sxs-lookup"><span data-stu-id="bb054-107">Record the current plan for each mission critical query by using the [sp_create_plan_guide](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) stored procedure and specifying the query plan in the USE PLAN query hint.</span></span>  
  
2.  <span data-ttu-id="bb054-108">验证计划指南是否适用于此查询。</span><span class="sxs-lookup"><span data-stu-id="bb054-108">Verify that the plan guide is applied to the query.</span></span>  
  
3.  <span data-ttu-id="bb054-109">将数据库升级到最新版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="bb054-109">Upgrade the database to the newer version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="bb054-110">计划保留在升级后的数据库中的计划指南中，如果在升级后计划的性能出现退步，则这些计划将用作后备计划。</span><span class="sxs-lookup"><span data-stu-id="bb054-110">The plans are persisted in the upgraded database in the plan guides and serve as a fallback in case of plan regressions after the upgrade.</span></span>  
  
     <span data-ttu-id="bb054-111">建议您在升级后不要启用计划指南，因为由于统计信息进行了更新，您可能会错过新版本中的更好计划或者重新编译所带来的益处。</span><span class="sxs-lookup"><span data-stu-id="bb054-111">We recommend that you not enable the plan guides after the upgrade because you might miss opportunities for better plans in the new release or beneficial recompiles due to updated statistics.</span></span>  
  
4.  <span data-ttu-id="bb054-112">如果在升级后选择了效率较低的计划，可以激活所有计划指南或部分计划指南以取代新计划。</span><span class="sxs-lookup"><span data-stu-id="bb054-112">If less efficient plans are chosen after the upgrade, activate all or a subset of the plan guides to override the new plans.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb054-113">示例</span><span class="sxs-lookup"><span data-stu-id="bb054-113">Example</span></span>  
 <span data-ttu-id="bb054-114">下面的示例显示如何通过创建计划指南来为查询记录升级前的计划。</span><span class="sxs-lookup"><span data-stu-id="bb054-114">The following example shows how to record a pre-upgrade plan for a query by creating a plan guide.</span></span>  
  
### <a name="step-1-collect-the-plan"></a><span data-ttu-id="bb054-115">步骤 1：收集计划</span><span class="sxs-lookup"><span data-stu-id="bb054-115">Step 1: Collect the Plan</span></span>  
 <span data-ttu-id="bb054-116">计划指南中记录的查询计划必须采用 XML 格式。</span><span class="sxs-lookup"><span data-stu-id="bb054-116">The query plan recorded in the plan guide must be in XML format.</span></span> <span data-ttu-id="bb054-117">可通过以下方式生成 XML 格式的查询计划：</span><span class="sxs-lookup"><span data-stu-id="bb054-117">XML-formatted query plans can be produced through the following ways:</span></span>  
  
-   [<span data-ttu-id="bb054-118">SET SHOWPLAN_XML</span><span class="sxs-lookup"><span data-stu-id="bb054-118">SET SHOWPLAN_XML</span></span>](/sql/t-sql/statements/set-showplan-xml-transact-sql)  
  
-   [<span data-ttu-id="bb054-119">SET STATISTICS XML</span><span class="sxs-lookup"><span data-stu-id="bb054-119">SET STATISTICS XML</span></span>](/sql/t-sql/statements/set-statistics-xml-transact-sql)  
  
-   <span data-ttu-id="bb054-120">查询[sys.databases dm_exec_query_plan](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql)动态管理函数的 query_plan 列。</span><span class="sxs-lookup"><span data-stu-id="bb054-120">Querying the query_plan column of the [sys.dm_exec_query_plan](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql) dynamic management function.</span></span>  
  
-   <span data-ttu-id="bb054-121">显示 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] [计划](../../relational-databases/event-classes/showplan-xml-event-class.md)xml、显示[计划 Xml 统计信息](../../relational-databases/event-classes/showplan-xml-statistics-profile-event-class.md)以及[用于查询编译](../../relational-databases/event-classes/showplan-xml-for-query-compile-event-class.md)事件类的显示计划 xml。</span><span class="sxs-lookup"><span data-stu-id="bb054-121">The [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] [Showplan XML](../../relational-databases/event-classes/showplan-xml-event-class.md), [Showplan XML Statistics Profile](../../relational-databases/event-classes/showplan-xml-statistics-profile-event-class.md), and [Showplan XML For Query Compile](../../relational-databases/event-classes/showplan-xml-for-query-compile-event-class.md) event classes.</span></span>  
  
 <span data-ttu-id="bb054-122">下面的示例通过查询动态管理视图收集语句 `SELECT City, StateProvinceID, PostalCode FROM Person.Address ORDER BY PostalCode DESC;` 的查询计划。</span><span class="sxs-lookup"><span data-stu-id="bb054-122">The following example collects the query plan for the statement `SELECT City, StateProvinceID, PostalCode FROM Person.Address ORDER BY PostalCode DESC;` by querying dynamic management views.</span></span>  
  
```  
USE AdventureWorks;  
GO  
SELECT query_plan  
    FROM sys.dm_exec_query_stats AS qs   
    CROSS APPLY sys.dm_exec_sql_text(qs.sql_handle) AS st  
    CROSS APPLY sys.dm_exec_text_query_plan(qs.plan_handle, DEFAULT, DEFAULT) AS qp  
    WHERE st.text LIKE N'SELECT City, StateProvinceID, PostalCode FROM Person.Address ORDER BY PostalCode DESC;%';  
GO  
```  
  
### <a name="step-2-create-the-plan-guide-to-force-the-plan"></a><span data-ttu-id="bb054-123">步骤 2：创建计划指南以强制实施计划</span><span class="sxs-lookup"><span data-stu-id="bb054-123">Step 2: Create the Plan Guide to Force the Plan</span></span>  
 <span data-ttu-id="bb054-124">在计划指南中使用 XML 格式的查询计划（通过上述任一方法获取），将该查询计划作为字符串文字复制并粘贴在 sp_create_plan_guide 的 OPTION 子句中指定的 USE PLAN 查询提示中。</span><span class="sxs-lookup"><span data-stu-id="bb054-124">Using the XML-formatted query plan (obtained by any of the methods previously described) in the plan guide, copy and paste the query plan as a string literal inside the USE PLAN query hint specified in the OPTION clause of sp_create_plan_guide.</span></span>  
  
 <span data-ttu-id="bb054-125">在 XML 计划本身中，先将计划中出现的引号 (') 通过第二个引号进行转义，然后再创建计划指南。</span><span class="sxs-lookup"><span data-stu-id="bb054-125">Within the XML plan itself, escape quotation marks (') that appear in the plan with a second quotation mark before creating the plan guide.</span></span> <span data-ttu-id="bb054-126">例如，对于包含 `WHERE A.varchar = 'This is a string'` 的计划，必须通过将该代码修改为 `WHERE A.varchar = ''This is a string''` 来进行转义。</span><span class="sxs-lookup"><span data-stu-id="bb054-126">For example, a plan that contains `WHERE A.varchar = 'This is a string'` must be escaped by modifying the code to `WHERE A.varchar = ''This is a string''`.</span></span>  
  
 <span data-ttu-id="bb054-127">下面的示例为步骤 1 中收集的查询计划创建计划指南，并在 `@hints` 参数中插入此查询的 XML 显示计划。</span><span class="sxs-lookup"><span data-stu-id="bb054-127">The following example creates a plan guide for the query plan collected in step 1 and inserts the XML Showplan for the query in the `@hints` parameter.</span></span> <span data-ttu-id="bb054-128">为简洁起见，此示例中仅包括部分显示计划输出。</span><span class="sxs-lookup"><span data-stu-id="bb054-128">For brevity, only partial Showplan output is included in the example.</span></span>  
  
```  
EXECUTE sp_create_plan_guide   
@name = N'Guide1',  
@stmt = N'SELECT City, StateProvinceID, PostalCode FROM Person.Address ORDER BY PostalCode DESC;',  
@type = N'SQL',  
@module_or_batch = NULL,  
@params = NULL,  
@hints = N'OPTION(USE PLAN N''<ShowPlanXML xmlns=''''https://schemas.microsoft.com/sqlserver/2004/07/showplan''''   
    Version=''''0.5'''' Build=''''9.00.1116''''>  
    <BatchSequence><Batch><Statements><StmtSimple>  
    ...  
    </StmtSimple></Statements></Batch>  
    </BatchSequence></ShowPlanXML>'')';  
GO  
```  
  
### <a name="step-3-verify-that-the-plan-guide-is-applied-to-the-query"></a><span data-ttu-id="bb054-129">步骤 3：验证计划指南是否适用于查询</span><span class="sxs-lookup"><span data-stu-id="bb054-129">Step 3: Verify That the Plan Guide Is Applied to the Query</span></span>  
 <span data-ttu-id="bb054-130">再次运行查询，并检查生成的查询计划。</span><span class="sxs-lookup"><span data-stu-id="bb054-130">Run the query again and examine the query plan that is produced.</span></span> <span data-ttu-id="bb054-131">您应看到该计划与您在计划指南中指定的计划相符。</span><span class="sxs-lookup"><span data-stu-id="bb054-131">You should see that the plan matches the one that you specified in the plan guide.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb054-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bb054-132">See Also</span></span>  
 <span data-ttu-id="bb054-133">[sp_create_plan_guide (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="bb054-133">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span></span>  
 <span data-ttu-id="bb054-134">[查询提示 (Transact-SQL)](/sql/t-sql/queries/hints-transact-sql-query) </span><span class="sxs-lookup"><span data-stu-id="bb054-134">[Query Hints &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-query) </span></span>  
 [<span data-ttu-id="bb054-135">计划指南</span><span class="sxs-lookup"><span data-stu-id="bb054-135">Plan Guides</span></span>](../../relational-databases/performance/plan-guides.md)  
  
  
