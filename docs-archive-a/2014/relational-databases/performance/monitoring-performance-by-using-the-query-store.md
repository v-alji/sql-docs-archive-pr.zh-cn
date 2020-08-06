---
title: 使用查询存储监视性能 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: e06344a4-22a5-4c67-b6c6-a7060deb5de6
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e5d74b9c4def9c0314569a8d0bd87939cdcb11b2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590738"
---
# <a name="monitoring-performance-by-using-the-query-store"></a><span data-ttu-id="c6386-102">Monitoring Performance By Using the Query Store</span><span class="sxs-lookup"><span data-stu-id="c6386-102">Monitoring Performance By Using the Query Store</span></span>
  <span data-ttu-id="c6386-103">查询存储功能让 DBA 可以探查查询计划选项和性能。</span><span class="sxs-lookup"><span data-stu-id="c6386-103">The query store feature provides DBAs with insight on query plan choice and performance.</span></span> <span data-ttu-id="c6386-104">它让你可以快速找到查询计划中的更改所造成的性能差异，从而简化了性能疑难解答。</span><span class="sxs-lookup"><span data-stu-id="c6386-104">It simplifies performance troubleshooting by enabling you to quickly find performance differences caused by changes in query plans.</span></span> <span data-ttu-id="c6386-105">这一性能会自动捕获查询、计划和运行时统计信息的历史记录，并将其保留以供你查看。</span><span class="sxs-lookup"><span data-stu-id="c6386-105">The feature automatically captures a history of queries, plans, and runtime statistics, and retains these for your review.</span></span> <span data-ttu-id="c6386-106">它按时间窗口将数据分割开来，使你可以查看数据库使用情况模式并了解服务器上何时发生了查询计划更改。</span><span class="sxs-lookup"><span data-stu-id="c6386-106">It separates data by time windows, allowing you to see database usage patterns and understand when query plan changes happened on the server.</span></span> <span data-ttu-id="c6386-107">可使用 [ALTER DATABASE SET](/sql/t-sql/statements/alter-database-transact-sql-set-options) 选项来配置查询存储。</span><span class="sxs-lookup"><span data-stu-id="c6386-107">The query store can be configured by using the [ALTER DATABASE SET](/sql/t-sql/statements/alter-database-transact-sql-set-options) option.</span></span>

||
|-|
|<span data-ttu-id="c6386-108">**适用**于： [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] ([获取](http://azure.micosoft.com/documentation/articles/sql-database-preview-whats-new/?WT.mc_id=TSQL_GetItTag)) 。</span><span class="sxs-lookup"><span data-stu-id="c6386-108">**Applies to**: [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] ([Get it](http://azure.micosoft.com/documentation/articles/sql-database-preview-whats-new/?WT.mc_id=TSQL_GetItTag)).</span></span>|

> [!IMPORTANT]
>  <span data-ttu-id="c6386-109">目前这是预览功能。</span><span class="sxs-lookup"><span data-stu-id="c6386-109">This is currently a preview feature.</span></span> <span data-ttu-id="c6386-110">为了使用查询存储，你必须承认并同意查询存储的实现遵从你的许可协议的预览条款（如企业协议、Microsoft Azure 协议或 Microsoft 在线订阅协议），以及任何适用于 [Microsoft Azure 预览版的补充使用条款](https://azure.microsoft.com/support/legal/preview-supplemental-terms/)。</span><span class="sxs-lookup"><span data-stu-id="c6386-110">To use the Query Store you must acknowledge and agree that implementation of Query Store is subject to the preview terms in your license agreement (e.g. the Enterprise Agreement, Microsoft Azure Agreement, or Microsoft Online Subscription Agreement), as well as any applicable [Supplemental Terms of Use for Microsoft Azure Preview](https://azure.microsoft.com/support/legal/preview-supplemental-terms/).</span></span>

##  <a name="enabling-the-query-store"></a><a name="Enabling"></a> <span data-ttu-id="c6386-111">启用查询存储</span><span class="sxs-lookup"><span data-stu-id="c6386-111">Enabling the Query Store</span></span>
 <span data-ttu-id="c6386-112">默认情况下，新数据库的查询存储处于非活动状态。</span><span class="sxs-lookup"><span data-stu-id="c6386-112">Query Store is not active for new databases by default.</span></span>

#### <a name="by-using-the-query-store-page-in-management-studio"></a><span data-ttu-id="c6386-113">通过使用 Management Studio 中的查询存储页</span><span class="sxs-lookup"><span data-stu-id="c6386-113">By Using the Query Store Page in Management Studio</span></span>

1.  <span data-ttu-id="c6386-114">在对象资源管理器中，右键单击数据库，然后单击“属性” 。</span><span class="sxs-lookup"><span data-stu-id="c6386-114">In Object Explorer, right-click a database, and then click **Properties**.</span></span> <span data-ttu-id="c6386-115">（要求 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]2016 版。）</span><span class="sxs-lookup"><span data-stu-id="c6386-115">(Requires [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 2016 version of [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)].)</span></span>

2.  <span data-ttu-id="c6386-116">在“数据库属性”  对话框中，选择“查询存储”  页。</span><span class="sxs-lookup"><span data-stu-id="c6386-116">In the **Database Properties** dialog box, select the **Query Store** page.</span></span>

3.  <span data-ttu-id="c6386-117">在“启用” \*\*\*\* 框中，选择“True” \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c6386-117">In the **Enable** box, select **True**.</span></span>

#### <a name="by-using-transact-sql-statements"></a><span data-ttu-id="c6386-118">通过使用 Transact-SQL 语句</span><span class="sxs-lookup"><span data-stu-id="c6386-118">By Using Transact-SQL Statements</span></span>

1.  <span data-ttu-id="c6386-119">使用 `ALTER DATABASE` 语句来启用查询存储。</span><span class="sxs-lookup"><span data-stu-id="c6386-119">Use the `ALTER DATABASE` statement to enable the query store.</span></span> <span data-ttu-id="c6386-120">例如：</span><span class="sxs-lookup"><span data-stu-id="c6386-120">For example:</span></span>

    ```
    ALTER DATABASE AdventureWorks2012 SET QUERY_STORE = ON;
    ```

     <span data-ttu-id="c6386-121">有关与 query store 相关的更多语法选项，请参阅[ALTER DATABASE SET options &#40;transact-sql&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)。</span><span class="sxs-lookup"><span data-stu-id="c6386-121">For more syntax options related to the query store, see [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options).</span></span>

> [!NOTE]
>  <span data-ttu-id="c6386-122">无法启用 master 数据库的查询存储。</span><span class="sxs-lookup"><span data-stu-id="c6386-122">You cannot enable the query store for the master database.</span></span>



##  <a name="information-in-the-query-store"></a><a name="About"></a><span data-ttu-id="c6386-123">查询存储中的信息</span><span class="sxs-lookup"><span data-stu-id="c6386-123">Information in the Query Store</span></span>
 <span data-ttu-id="c6386-124">由于统计信息更改、架构更改、索引的创建/删除等多种不同原因，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中任何特定查询的执行计划通常会随着时间而改进。过程缓存（其中存储了缓存的查询计划）仅存储最近的执行计划。</span><span class="sxs-lookup"><span data-stu-id="c6386-124">Execution plans for any specific query in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] typically evolve over time due to a number of different reasons such as statistics changes, schema changes, creation/deletion of indexes, etc. The procedure cache (where cached query plans are stored) only stores the latest execution plan.</span></span> <span data-ttu-id="c6386-125">还会由于内存压力从计划缓存中逐出计划。</span><span class="sxs-lookup"><span data-stu-id="c6386-125">Plans also get evicted from the plan cache due to memory pressure.</span></span> <span data-ttu-id="c6386-126">因此，执行计划更改造成的查询性能回归可能非常重大，且长时间才能解决。</span><span class="sxs-lookup"><span data-stu-id="c6386-126">As a result, query performance regressions caused by execution plan changes can be non-trivial and time consuming to resolve.</span></span>

 <span data-ttu-id="c6386-127">由于查询存储会保留每个查询的多个执行计划，因此它可以强制执行策略，以引导查询处理器对某个查询使用特定执行计划。</span><span class="sxs-lookup"><span data-stu-id="c6386-127">Since the query store retains multiple execution plans per query, it can enforce policies to direct the query processor to use a specific execution plan for a query.</span></span> <span data-ttu-id="c6386-128">这称为“计划强制”。</span><span class="sxs-lookup"><span data-stu-id="c6386-128">This is referred to as plan forcing.</span></span> <span data-ttu-id="c6386-129">查询存储中的计划强制是通过使用类似于 [USE PLAN](/sql/t-sql/queries/hints-transact-sql-query) 查询提示的机制来提供的，但它不需要在用户应用程序中进行任何更改。</span><span class="sxs-lookup"><span data-stu-id="c6386-129">Plan forcing in Query Store is provided by using a mechanism similar to the [USE PLAN](/sql/t-sql/queries/hints-transact-sql-query) query hint, but it does not require any change in user applications.</span></span> <span data-ttu-id="c6386-130">计划强制可在非常短的时间内解决由计划更改造成的查询性能回归。</span><span class="sxs-lookup"><span data-stu-id="c6386-130">Plan forcing can resolve a query performance regression caused by a plan change in a very short period of time.</span></span>

 <span data-ttu-id="c6386-131">使用查询存储功能的常见方案为：</span><span class="sxs-lookup"><span data-stu-id="c6386-131">Common scenarios for using the Query Store feature are:</span></span>

-   <span data-ttu-id="c6386-132">快速查找并修复通过强制使用先前查询计划而造成的计划性能回归。</span><span class="sxs-lookup"><span data-stu-id="c6386-132">Quickly find and fix a plan performance regression by forcing the previous query plan.</span></span> <span data-ttu-id="c6386-133">修复近期由于执行计划更改而出现性能回归的查询。</span><span class="sxs-lookup"><span data-stu-id="c6386-133">Fix queries that have recently regressed in performance due to execution plan changes.</span></span>

-   <span data-ttu-id="c6386-134">确定在给定时间窗口中查询执行的次数，从而帮助 DBA 对性能资源问题进行故障排除。</span><span class="sxs-lookup"><span data-stu-id="c6386-134">Determine the number of times a query was executed in a given time window, assisting a DBA in troubleshooting performance resource problems.</span></span>

-   <span data-ttu-id="c6386-135">标识过去 *x* 小时内的前 *n* 个查询（按执行时间、内存占用等）。</span><span class="sxs-lookup"><span data-stu-id="c6386-135">Identify top *n* queries (by execution time, memory consumption, etc.) in the past *x* hours.</span></span>

-   <span data-ttu-id="c6386-136">审核给定查询的查询计划历史记录。</span><span class="sxs-lookup"><span data-stu-id="c6386-136">Audit the history of query plans for a given query.</span></span>

-   <span data-ttu-id="c6386-137">分析特定数据库的资源（CPU、I/O 和内存）使用模式。</span><span class="sxs-lookup"><span data-stu-id="c6386-137">Analyze the resource (CPU, I/O, and Memory) usage patterns for a particular database.</span></span>

 <span data-ttu-id="c6386-138">查询存储包含两个存储；用于永久保存执行计划信息的 **计划存储** ，以及用于永久保存执行统计信息的 **运行时统计信息存储** 。</span><span class="sxs-lookup"><span data-stu-id="c6386-138">The query store contains two stores; a **plan store** for persisting the execution plan information, and a **runtime stats store** for persisting the execution statistics information.</span></span> <span data-ttu-id="c6386-139">`max_plans_per_query` 配置选项限制了计划存储中查询可存储的唯一计划数。</span><span class="sxs-lookup"><span data-stu-id="c6386-139">The number of unique plans that can be stored for a query in the plan store is limited by the `max_plans_per_query` configuration option.</span></span> <span data-ttu-id="c6386-140">为增强性能，通过异步方式向这两个存储写入信息。</span><span class="sxs-lookup"><span data-stu-id="c6386-140">To enhance performance, the information is written to the two stores asynchronously.</span></span> <span data-ttu-id="c6386-141">为尽量减少空间使用量，将在按固定时间窗口上聚合运行时统计信息存储中的运行时执行统计信息。</span><span class="sxs-lookup"><span data-stu-id="c6386-141">To minimize space usage, the runtime execution statistics in the runtime stats store are aggregated over a fixed time window.</span></span> <span data-ttu-id="c6386-142">可通过查询查询存储目录视图来查看这些存储中的信息。</span><span class="sxs-lookup"><span data-stu-id="c6386-142">The information in these stores is visible by querying the query store catalog views.</span></span>

 <span data-ttu-id="c6386-143">以下查询返回查询存储中查询和计划的相关信息。</span><span class="sxs-lookup"><span data-stu-id="c6386-143">The following query returns information about queries and plans in the query store.</span></span>

```
SELECT Txt.query_text_id, Txt.query_sql_text, Pl.plan_id, Qry.*
FROM sys.query_store_plan AS Pl
JOIN sys.query_store_query AS Qry
    ON Pl.query_id = Qry.query_id
JOIN sys.query_store_query_text AS Txt
    ON Qry.query_text_id = Txt.query_text_id ;
```



## <a name="using-the-regressed-queries-feature"></a><span data-ttu-id="c6386-144">使用回归查询功能</span><span class="sxs-lookup"><span data-stu-id="c6386-144">Using the Regressed Queries Feature</span></span>
 <span data-ttu-id="c6386-145">启用查询存储后，刷新 "对象资源管理器" 窗格的数据库部分，以添加**查询存储**部分。</span><span class="sxs-lookup"><span data-stu-id="c6386-145">After enabling the query store, refresh the database portion of the Object Explorer pane to add the **Query Store** section.</span></span>

 <span data-ttu-id="c6386-146">![QueryStore](../../database-engine/media/querystore.PNG "QueryStore")</span><span class="sxs-lookup"><span data-stu-id="c6386-146">![QueryStore](../../database-engine/media/querystore.PNG "QueryStore")</span></span>

 <span data-ttu-id="c6386-147">在选择“回归查询” \*\*\*\* 后，打开 **中的“回归查询”**[!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]窗格。</span><span class="sxs-lookup"><span data-stu-id="c6386-147">Selecting **Regressed Queries**, opens the **Regressed Queries** pane in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="c6386-148">“回归查询”窗格将显示查询存储中的查询和计划。</span><span class="sxs-lookup"><span data-stu-id="c6386-148">The Regressed Queries pane shows you the queries, and plans in the query store.</span></span> <span data-ttu-id="c6386-149">借助顶部的下拉列表框，可基于各种条件选择查询。</span><span class="sxs-lookup"><span data-stu-id="c6386-149">Drop down boxes at the top allow you to select queries based on various criteria.</span></span> <span data-ttu-id="c6386-150">选择某个计划以查看图形查询计划。</span><span class="sxs-lookup"><span data-stu-id="c6386-150">Select a plan to see the graphical query plan.</span></span> <span data-ttu-id="c6386-151">可使用按钮来查看源查询，强制执行和取消强制执行某一查询计划，以及刷新显示内容。</span><span class="sxs-lookup"><span data-stu-id="c6386-151">Buttons are available to view the source query, force, and unforce a query plan, and refresh the display.</span></span>

 <span data-ttu-id="c6386-152">![RegressedQueries](../../database-engine/media/regressedqueries.PNG "RegressedQueries")</span><span class="sxs-lookup"><span data-stu-id="c6386-152">![RegressedQueries](../../database-engine/media/regressedqueries.PNG "RegressedQueries")</span></span>

 <span data-ttu-id="c6386-153">若要强制执行某一计划，请选择查询和计划，然后单击 "**强制计划"。**</span><span class="sxs-lookup"><span data-stu-id="c6386-153">To force a plan, select a query and plan, and then click **Force Plan.**</span></span> <span data-ttu-id="c6386-154">你只可以强制执行由查询计划功能保存且仍保留在查询计划缓存中的计划。</span><span class="sxs-lookup"><span data-stu-id="c6386-154">You can only force plans that were saved by the query plan feature and are still retained in the query plan cache.</span></span>



##  <a name="configuration-options"></a><a name="Options"></a> <span data-ttu-id="c6386-155">配置选项</span><span class="sxs-lookup"><span data-stu-id="c6386-155">Configuration Options</span></span>
 <span data-ttu-id="c6386-156">OPERATION_MODE 可以 READ_WRITE 或 READ_ONLY。</span><span class="sxs-lookup"><span data-stu-id="c6386-156">OPERATION_MODE Can be READ_WRITE or READ_ONLY.</span></span>

 <span data-ttu-id="c6386-157">CLEANUP_POLICY 配置 STALE_QUERY_THRESHOLD_DAYS 参数，以指定在查询存储中保留数据的天数。</span><span class="sxs-lookup"><span data-stu-id="c6386-157">CLEANUP_POLICY Configure the STALE_QUERY_THRESHOLD_DAYS argument to specify the number of days to retain data in the query store.</span></span>

 <span data-ttu-id="c6386-158">DATA_FLUSH_INTERVAL_SECONDS 确定写入到查询存储的数据保留到磁盘的频率。</span><span class="sxs-lookup"><span data-stu-id="c6386-158">DATA_FLUSH_INTERVAL_SECONDS Determines the frequency at which data written to the query store is persisted to disk.</span></span> <span data-ttu-id="c6386-159">为了优化性能，由查询存储收集的数据应以异步方式写入到磁盘。</span><span class="sxs-lookup"><span data-stu-id="c6386-159">To optimize for performance, data collected by the query store is asynchronously written to the disk.</span></span> <span data-ttu-id="c6386-160">通过 DATA_FLUSH_INTERVAL_SECONDS 配置此异步传输发生的频率。</span><span class="sxs-lookup"><span data-stu-id="c6386-160">The frequency at which this asynchronous transfer occurs is configured via DATA_FLUSH_INTERVAL_SECONDS.</span></span>

 <span data-ttu-id="c6386-161">MAX_SIZE_MB 配置查询存储的最大大小。</span><span class="sxs-lookup"><span data-stu-id="c6386-161">MAX_SIZE_MB Configures the maximum size of the query store.</span></span> <span data-ttu-id="c6386-162">如果查询存储中的数据命中 MAX_SIZE_MB 限制，则查询存储会自动从读写状态更改为只读状态，并停止收集新数据。</span><span class="sxs-lookup"><span data-stu-id="c6386-162">If the data in the query store hits the MAX_SIZE_MB limit, the query store automatically changes the state from read-write to read-only and stops collecting new data.</span></span>

 <span data-ttu-id="c6386-163">INTERVAL_LENGTH_MINUTES 确定运行时执行统计数据聚合到查询存储中的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="c6386-163">INTERVAL_LENGTH_MINUTES Determines the time interval at which runtime execution statistics data is aggregated into the query store.</span></span> <span data-ttu-id="c6386-164">为了优化空间使用情况，将在固定时间窗口上聚合运行时统计信息存储中的运行时执行统计信息。</span><span class="sxs-lookup"><span data-stu-id="c6386-164">To optimize for space usage, the runtime execution statistics in the Runtime Stats Store are aggregated over a fixed time window.</span></span> <span data-ttu-id="c6386-165">此固定时间窗口通过 INTERVAL_LENGTH_MINUTES 进行配置。</span><span class="sxs-lookup"><span data-stu-id="c6386-165">This fixed time window is configured via INTERVAL_LENGTH_MINUTES.</span></span>

 <span data-ttu-id="c6386-166">查询 `sys.database_query_store_options` 视图以确定查询存储的当前选项。</span><span class="sxs-lookup"><span data-stu-id="c6386-166">Query the `sys.database_query_store_options` view to determine the current options of the query store.</span></span>

 <span data-ttu-id="c6386-167">若要深入了解如何使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句来设置选项，请参阅 [选项管理](#OptionMgmt)。</span><span class="sxs-lookup"><span data-stu-id="c6386-167">For more information about setting options by using [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, see [Option Management](#OptionMgmt).</span></span>

 

##  <a name="related-views-functions-and-procedures"></a><a name="Related"></a> <span data-ttu-id="c6386-168">相关视图、功能和过程</span><span class="sxs-lookup"><span data-stu-id="c6386-168">Related Views, Functions, and Procedures</span></span>
 <span data-ttu-id="c6386-169">可通过 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] 或使用以下视图和过程来查看和管理查询存储。</span><span class="sxs-lookup"><span data-stu-id="c6386-169">The Query Store can be viewed and managed through [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] or by using the following views and procedures.</span></span>

-   [<span data-ttu-id="c6386-170">sys.fn_stmt_sql_handle_from_sql_stmt (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="c6386-170">sys.fn_stmt_sql_handle_from_sql_stmt &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-functions/sys-fn-stmt-sql-handle-from-sql-stmt-transact-sql)

### <a name="query-store-catalog-views"></a><span data-ttu-id="c6386-171">查询存储目录视图</span><span class="sxs-lookup"><span data-stu-id="c6386-171">Query Store Catalog Views</span></span>
 <span data-ttu-id="c6386-172">7 个查询视图提供了查询存储的相关信息。</span><span class="sxs-lookup"><span data-stu-id="c6386-172">Seven catalog views present information about the Query Store.</span></span>

-   [<span data-ttu-id="c6386-173">sys.database_query_store_options (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="c6386-173">sys.database_query_store_options &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql)

-   [<span data-ttu-id="c6386-174">sys.query_context_settings (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="c6386-174">sys.query_context_settings &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-query-context-settings-transact-sql)

-   [<span data-ttu-id="c6386-175">sys.query_store_plan (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="c6386-175">sys.query_store_plan &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-query-store-plan-transact-sql)

-   [<span data-ttu-id="c6386-176">sys.query_store_query (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="c6386-176">sys.query_store_query &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-query-store-query-transact-sql)

-   [<span data-ttu-id="c6386-177">sys.query_store_query_text (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="c6386-177">sys.query_store_query_text &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-query-store-query-text-transact-sql)

-   [<span data-ttu-id="c6386-178">sys.query_store_runtime_stats (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="c6386-178">sys.query_store_runtime_stats &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-query-store-runtime-stats-transact-sql)

-   [<span data-ttu-id="c6386-179">sys.query_store_runtime_stats_interval (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="c6386-179">sys.query_store_runtime_stats_interval &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-query-store-runtime-stats-interval-transact-sql)

### <a name="query-store-stored-procedures"></a><span data-ttu-id="c6386-180">查询存储存储过程</span><span class="sxs-lookup"><span data-stu-id="c6386-180">Query Store Stored Procedures</span></span>
 <span data-ttu-id="c6386-181">6 个存储过程配置了查询存储。</span><span class="sxs-lookup"><span data-stu-id="c6386-181">Six stored procedures configure the Query Store.</span></span>

-   [<span data-ttu-id="c6386-182">sp_query_store_flush_db (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="c6386-182">sp_query_store_flush_db &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-query-store-flush-db-transact-sql)

-   [<span data-ttu-id="c6386-183">sp_query_store_reset_exec_stats (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="c6386-183">sp_query_store_reset_exec_stats &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-query-store-reset-exec-stats-transact-sql)

-   [<span data-ttu-id="c6386-184">sp_query_store_force_plan (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="c6386-184">sp_query_store_force_plan &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-query-store-force-plan-transact-sql)

-   [<span data-ttu-id="c6386-185">sp_query_store_unforce_plan (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="c6386-185">sp_query_store_unforce_plan &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-query-store-unforce-plan-transact-sql)

-   [<span data-ttu-id="c6386-186">sp_query_store_remove_plan (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="c6386-186">sp_query_store_remove_plan &#40;Transct-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-query-store-remove-plan-transct-sql)

-   [<span data-ttu-id="c6386-187">sp_query_store_remove_query (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="c6386-187">sp_query_store_remove_query &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-query-store-remove-query-transact-sql)



##  <a name="key-usage-scenarios"></a><a name="Scenarios"></a><span data-ttu-id="c6386-188">键使用方案</span><span class="sxs-lookup"><span data-stu-id="c6386-188">Key Usage Scenarios</span></span>

###  <a name="option-management"></a><a name="OptionMgmt"></a> <span data-ttu-id="c6386-189">选项管理</span><span class="sxs-lookup"><span data-stu-id="c6386-189">Option Management</span></span>
 <span data-ttu-id="c6386-190">本部分提供一些有关如何管理查询存储功能本身的准则。</span><span class="sxs-lookup"><span data-stu-id="c6386-190">This section provides some guidelines on managing Query Store feature itself.</span></span>

 <span data-ttu-id="c6386-191">**查询存储当前是否处于活动状态？**</span><span class="sxs-lookup"><span data-stu-id="c6386-191">**Is Query Store currently active?**</span></span>

 <span data-ttu-id="c6386-192">查询存储将其数据存储在用户数据库内，正因为此，它具有大小限制（使用 `MAX_STORAGE_SIZE_MB` 进行配置）。</span><span class="sxs-lookup"><span data-stu-id="c6386-192">Query Store stores its data inside the user database and that is why it has size limit (configured  with `MAX_STORAGE_SIZE_MB`).</span></span> <span data-ttu-id="c6386-193">如果查询存储中的数据命中该限制，则查询存储将自动从读写状态更改为只读状态，并停止收集新数据。</span><span class="sxs-lookup"><span data-stu-id="c6386-193">If data in Query Store hits that limit Query Store will automatically change state from read-write to read-only and stop collecting new data.</span></span>

 <span data-ttu-id="c6386-194">执行以下脚本以确定查询存储当前是否处于活动状态，以及它目前是否在收集运行时统计信息。</span><span class="sxs-lookup"><span data-stu-id="c6386-194">Execute the following script to determine if Query Store is currently active, and whether it is currently collects runtime stats or not.</span></span>

```
DECLARE @x nvarchar(100) = CAST(newid() AS nvarchar(100));
DECLARE @query nvarchar(max) = 
N'IF EXISTS
(
    SELECT * 
    FROM sys.query_store_query_text 
    WHERE query_sql_text LIKE ''%' + @x + N'%''
)
SELECT ''Query Store is active'' ;
ELSE SELECT ''Query Store is NOT active''' ;
EXEC sp_executesql @query;
```

 <span data-ttu-id="c6386-195">**获取查询存储选项**</span><span class="sxs-lookup"><span data-stu-id="c6386-195">**Get Query Store options**</span></span>

 <span data-ttu-id="c6386-196">若要了解查询存储状态的相关详细信息，请在用户数据库中执行以下操作。</span><span class="sxs-lookup"><span data-stu-id="c6386-196">To find out detailed information about Query Store status, execute following in a user database.</span></span>

```
SELECT * FROM sys.database_query_store_options;
```

 <span data-ttu-id="c6386-197">**设置查询存储间隔**</span><span class="sxs-lookup"><span data-stu-id="c6386-197">**Setting Query Store interval**</span></span>

 <span data-ttu-id="c6386-198">你可以覆盖用于聚合查询运行时统计信息的时间间隔（默认值为 60 分钟）。</span><span class="sxs-lookup"><span data-stu-id="c6386-198">You can override interval for aggregating query runtime statistics (default is 60 minutes).</span></span>

```

      USE master;
GO

ALTER DATABASE <database_name> 
SET QUERY_STORE (INTERVAL_LENGTH_MINUTES = 15);
```

 <span data-ttu-id="c6386-199">请注意不允许任意值 - 应使用以下值之一：1、5、10、15、30 和 60。</span><span class="sxs-lookup"><span data-stu-id="c6386-199">Note that arbitrary values are not allowed - you should use one of the following: 1, 5, 10, 15, 30 and 60.</span></span>

 <span data-ttu-id="c6386-200">通过 `sys.database_query_store_options` 视图公开时间间隔的新值。</span><span class="sxs-lookup"><span data-stu-id="c6386-200">New value for interval is exposed through `sys.database_query_store_options` view.</span></span>

 <span data-ttu-id="c6386-201">如果查询存储已满，请使用以下语句来扩展存储。</span><span class="sxs-lookup"><span data-stu-id="c6386-201">If the Query Store storage is full use the following statement to extend the storage.</span></span>

```
ALTER DATABASE <database_name> 
SET QUERY_STORE (MAX_STORAGE_SIZE_MB = <new_size>);
```

 <span data-ttu-id="c6386-202">**设置所有查询存储选项**</span><span class="sxs-lookup"><span data-stu-id="c6386-202">**Set all Query Store options**</span></span>

 <span data-ttu-id="c6386-203">你可以使用单个 ALTER DATABASE 语句同时设置多个查询存储选项。</span><span class="sxs-lookup"><span data-stu-id="c6386-203">You can set multiple Query Store options at once with a single ALTER DATABASE statement.</span></span>

```
ALTER DATABASE <database name> 
SET QUERY_STORE (
    OPERATION_MODE = READ_WRITE,
    CLEANUP_POLICY = 
    (STALE_QUERY_THRESHOLD_DAYS = 30),
    DATA_FLUSH_INTERVAL_SECONDS = 3000,
    MAX_STORAGE_SIZE_MB = 500,
    INTERVAL_LENGTH_MINUTES = 15
);
```

 <span data-ttu-id="c6386-204">**清理空间**</span><span class="sxs-lookup"><span data-stu-id="c6386-204">**Cleaning up the space**</span></span>

 <span data-ttu-id="c6386-205">查询存储时间间隔表是在数据库创建期间在 PRIMARY 文件组中创建的，且之后不可更改此配置。</span><span class="sxs-lookup"><span data-stu-id="c6386-205">Query Store internal tables are created in the PRIMARY filegroup during database creation and that configuration cannot be changed later.</span></span> <span data-ttu-id="c6386-206">如果空间不足，你可以要使用以下语句来清理旧的查询存储数据。</span><span class="sxs-lookup"><span data-stu-id="c6386-206">If you are running out of space you might want to clear older Query Store data by using the following statement.</span></span>

```
ALTER DATABASE <db_name> SET QUERY_STORE CLEAR;
```

 <span data-ttu-id="c6386-207">或者，你可以只清理临时查询数据，因为此数据与查询优化和计划分析的相关性更低，但却占用了大量空间。</span><span class="sxs-lookup"><span data-stu-id="c6386-207">Alternatively, you might want to clear up only ad-hoc query data, since it is less relevant for query optimizations and plan analysis but takes up just as much space.</span></span>

 <span data-ttu-id="c6386-208">\*\*\*\* “删除临时查询”会删除只执行了一次且已超过 24 小时的查询。</span><span class="sxs-lookup"><span data-stu-id="c6386-208">**Delete ad-hoc queries** This deletes the queries that were only executed only once and that are more than 24 hours old.</span></span>

```
DECLARE @id int
DECLARE adhoc_queries_cursor CURSOR 
FOR 
SELECT q.query_id
FROM sys.query_store_query_text AS qt
JOIN sys.query_store_query AS q 
    ON q.query_text_id = qt.query_text_id
JOIN sys.query_store_plan AS p 
    ON p.query_id = q.query_id
JOIN sys.query_store_runtime_stats AS rs 
    ON rs.plan_id = p.plan_id
GROUP BY q.query_id
HAVING SUM(rs.count_executions) < 2 
AND MAX(rs.last_execution_time) < DATEADD (hour, -24, GETUTCDATE())
ORDER BY q.query_id ;

OPEN adhoc_queries_cursor ;
FETCH NEXT FROM adhoc_queries_cursor INTO @id;
WHILE @@fetch_status = 0
    BEGIN 
        PRINT @id
        EXEC sp_query_store_remove_query @id
        FETCH NEXT FROM adhoc_queries_cursor INTO @id
    END 
CLOSE adhoc_queries_cursor ;
DEALLOCATE adhoc_queries_cursor;
```

 <span data-ttu-id="c6386-209">你可以使用其他逻辑来定义自己的过程，以清理对你而言不再重要的数据。</span><span class="sxs-lookup"><span data-stu-id="c6386-209">You can define your own procedure with different logic for clearing up the data that is no longer important for you.</span></span>

 <span data-ttu-id="c6386-210">以上示例使用 `sp_query_store_remove_query` 扩展存储过程来删除不必要的数据。</span><span class="sxs-lookup"><span data-stu-id="c6386-210">The example above uses the `sp_query_store_remove_query` extended stored procedure for removing unnecessary data.</span></span> <span data-ttu-id="c6386-211">你还可以使用其他两个过程。</span><span class="sxs-lookup"><span data-stu-id="c6386-211">You can also use two other procedures.</span></span>

-   <span data-ttu-id="c6386-212">`sp_query_store_reset_exec_stats`-清除给定计划的运行时统计信息。</span><span class="sxs-lookup"><span data-stu-id="c6386-212">`sp_query_store_reset_exec_stats` - clear runtime statistics for a given plan.</span></span>

-   <span data-ttu-id="c6386-213">`sp_query_store_remove_plan`-删除单个计划。</span><span class="sxs-lookup"><span data-stu-id="c6386-213">`sp_query_store_remove_plan` - removes a single plan.</span></span>



###  <a name="performance-auditing-and-troubleshooting"></a><a name="Peformance"></a> <span data-ttu-id="c6386-214">性能审核和疑难解答</span><span class="sxs-lookup"><span data-stu-id="c6386-214">Performance Auditing and Troubleshooting</span></span>
 <span data-ttu-id="c6386-215">因为查询存储保存了整个查询执行过程中的编译历史记录和运行时度量，因此你可以轻松回答很多与你的工作负荷相关的不同问题。</span><span class="sxs-lookup"><span data-stu-id="c6386-215">Because Query Store keeps history of compilation and runtime metrics throughout query executions there are many different questions you can easily answer with regards to your workload.</span></span>

 <span data-ttu-id="c6386-216">**在数据库上执行的最后*n*个查询。**</span><span class="sxs-lookup"><span data-stu-id="c6386-216">**Last *n* queries executed on the database.**</span></span>

```
SELECT TOP 10 qt.query_sql_text, q.query_id, 
    qt.query_text_id, p.plan_id, rs.last_execution_time
FROM sys.query_store_query_text AS qt 
JOIN sys.query_store_query AS q 
    ON qt.query_text_id = q.query_text_id 
JOIN sys.query_store_plan AS p 
    ON q.query_id = p.query_id 
JOIN sys.query_store_runtime_stats AS rs 
    ON p.plan_id = rs.plan_id
ORDER BY rs.last_execution_time DESC;
```

 <span data-ttu-id="c6386-217">**每个查询的执行数。**</span><span class="sxs-lookup"><span data-stu-id="c6386-217">**Number of executions for each query.**</span></span>

```
SELECT q.query_id, qt.query_text_id, qt.query_sql_text, 
    SUM(rs.count_executions) AS total_execution_count
FROM sys.query_store_query_text AS qt 
JOIN sys.query_store_query AS q 
    ON qt.query_text_id = q.query_text_id 
JOIN sys.query_store_plan AS p 
    ON q.query_id = p.query_id 
JOIN sys.query_store_runtime_stats AS rs 
    ON p.plan_id = rs.plan_id
GROUP BY q.query_id, qt.query_text_id, qt.query_sql_text
ORDER BY total_execution_count DESC;
```

 <span data-ttu-id="c6386-218">**过去一小时内具有最长平均执行时间的查询数。**</span><span class="sxs-lookup"><span data-stu-id="c6386-218">**The number of queries with the longest average execution time within last hour.**</span></span>

```
SELECT TOP 10 rs.avg_duration, qt.query_sql_text, q.query_id,
    qt.query_text_id, p.plan_id, GETUTCDATE() AS CurrentUTCTime, 
    rs.last_execution_time 
FROM sys.query_store_query_text AS qt 
JOIN sys.query_store_query AS q 
    ON qt.query_text_id = q.query_text_id 
JOIN sys.query_store_plan AS p 
    ON q.query_id = p.query_id 
JOIN sys.query_store_runtime_stats AS rs 
    ON p.plan_id = rs.plan_id
WHERE rs.last_execution_time > DATEADD(hour, -1, GETUTCDATE())
ORDER BY rs.avg_duration DESC;
```

 <span data-ttu-id="c6386-219">**在过去24小时内具有最大平均物理 IO 读取数的查询的数量，其中包含相应的平均行计数和执行计数。**</span><span class="sxs-lookup"><span data-stu-id="c6386-219">**The number of queries that had the biggest average physical IO reads in last 24 hours, with corresponding average row count and execution count.**</span></span>

```
SELECT TOP 10 rs.avg_physical_io_reads, qt.query_sql_text, 
    q.query_id, qt.query_text_id, p.plan_id, rs.runtime_stats_id, 
    rsi.start_time, rsi.end_time, rs.avg_rowcount, rs.count_executions
FROM sys.query_store_query_text AS qt 
JOIN sys.query_store_query AS q 
    ON qt.query_text_id = q.query_text_id 
JOIN sys.query_store_plan AS p 
    ON q.query_id = p.query_id 
JOIN sys.query_store_runtime_stats AS rs 
    ON p.plan_id = rs.plan_id 
JOIN sys.query_store_runtime_stats_interval AS rsi 
    ON rsi.runtime_stats_interval_id = rs.runtime_stats_interval_id
WHERE rsi.start_time >= DATEADD(hour, -24, GETUTCDATE()) 
ORDER BY rs.avg_physical_io_reads DESC;
```

 <span data-ttu-id="c6386-220">**具有多个计划的查询。**</span><span class="sxs-lookup"><span data-stu-id="c6386-220">**Queries with multiple plans.**</span></span> <span data-ttu-id="c6386-221">这些查询特别有趣，因为计划选择更改可能造成它们的性能回归。</span><span class="sxs-lookup"><span data-stu-id="c6386-221">These queries are especially interesting because they are candidates for regressions due to plan choice change.</span></span> <span data-ttu-id="c6386-222">以下查询将这些查询和所有计划一同进行了标识：</span><span class="sxs-lookup"><span data-stu-id="c6386-222">The following query identifies these queries along with all plans:</span></span>

```
WITH Query_MultPlans
AS
(
    SELECT COUNT(*) AS cnt, q.query_id 
    FROM sys.query_store_query_text AS qt
    JOIN sys.query_store_query AS q
        ON qt.query_text_id = q.query_text_id
    JOIN sys.query_store_plan AS p
        ON p.query_id = q.query_id
    GROUP BY q.query_id
    HAVING COUNT(distinct plan_id) > 1
)

SELECT q.query_id, object_name(object_id) AS ContainingObject, query_sql_text,
plan_id, p.query_plan AS plan_xml,
p.last_compile_start_time, p.last_execution_time
FROM Query_MultPlans AS qm
JOIN sys.query_store_query AS q
    ON qm.query_id = q.query_id
JOIN sys.query_store_plan AS p
    ON q.query_id = p.query_id
JOIN sys.query_store_query_text qt 
    ON qt.query_text_id = q.query_text_id
ORDER BY query_id, plan_id;
```

 <span data-ttu-id="c6386-223">**最近回归性能 (比较不同时间点) 的查询。**</span><span class="sxs-lookup"><span data-stu-id="c6386-223">**Queries that recently regressed in performance (comparing different point in time).**</span></span> <span data-ttu-id="c6386-224">以下查询示例返回了其执行时间因计划选择更改而在过去 48 小时内翻倍的所有查询。</span><span class="sxs-lookup"><span data-stu-id="c6386-224">The following query example returns all queries for which execution time doubled in last 48 hours due to a plan choice change.</span></span> <span data-ttu-id="c6386-225">并排查询所有的运行时统计信息时间间隔。</span><span class="sxs-lookup"><span data-stu-id="c6386-225">Query compares all runtime stat intervals side by side.</span></span>

```
SELECT 
    qt.query_sql_text, 
    q.query_id, 
    qt.query_text_id, 
    rs1.runtime_stats_id AS runtime_stats_id_1,
    rsi1.start_time AS interval_1, 
    p1.plan_id AS plan_1, 
    rs1.avg_duration AS avg_duration_1, 
    rs2.avg_duration AS avg_duration_2,
    p2.plan_id AS plan_2, 
    rsi2.start_time AS interval_2, 
    rs2.runtime_stats_id AS runtime_stats_id_2
FROM sys.query_store_query_text AS qt 
JOIN sys.query_store_query AS q 
    ON qt.query_text_id = q.query_text_id 
JOIN sys.query_store_plan AS p1 
    ON q.query_id = p1.query_id 
JOIN sys.query_store_runtime_stats AS rs1 
    ON p1.plan_id = rs1.plan_id 
JOIN sys.query_store_runtime_stats_interval AS rsi1 
    ON rsi1.runtime_stats_interval_id = rs1.runtime_stats_interval_id 
JOIN sys.query_store_plan AS p2 
    ON q.query_id = p2.query_id 
JOIN sys.query_store_runtime_stats AS rs2 
    ON p2.plan_id = rs2.plan_id 
JOIN sys.query_store_runtime_stats_interval AS rsi2 
    ON rsi2.runtime_stats_interval_id = rs2.runtime_stats_interval_id
WHERE rsi1.start_time > DATEADD(hour, -48, GETUTCDATE()) 
    AND rsi2.start_time > rsi1.start_time 
    AND p1.plan_id <> p2.plan_id
    AND rs2.avg_duration > 2*rs1.avg_duration
ORDER BY q.query_id, rsi1.start_time, rsi2.start_time;
```

 <span data-ttu-id="c6386-226">如果你向查看所有性能回归（而不仅是计划选择更改造成的回归），只需从先前查询中删除条件 `AND p1.plan_id <> p2.plan_id` 。</span><span class="sxs-lookup"><span data-stu-id="c6386-226">If you want to see performance all regressions (not only those related to plan choice change) than just remove condition `AND p1.plan_id <> p2.plan_id` from the previous query.</span></span>

 <span data-ttu-id="c6386-227">**最近回归性能 (比较最近的与历史执行的查询) 。**</span><span class="sxs-lookup"><span data-stu-id="c6386-227">**Queries that recently regressed in performance (comparing recent vs. history execution).**</span></span> <span data-ttu-id="c6386-228">下一查询会根据执行时间段来比较查询执行。</span><span class="sxs-lookup"><span data-stu-id="c6386-228">The next query compares query execution based periods of execution.</span></span> <span data-ttu-id="c6386-229">在此特定示例中，查询对比了最近时期（1 小时）和历史时期（过去一天）中的执行，并标识了那些引入 additional_duration_workload 的查询。</span><span class="sxs-lookup"><span data-stu-id="c6386-229">In this particular example the query compares execution in recent period (1 hour) vs. history period (last day) and identifies those that introduced additional_duration_workload.</span></span> <span data-ttu-id="c6386-230">此度量的计算方式是最近平均执行和历史平均执行之差，再乘以最近执行数量。</span><span class="sxs-lookup"><span data-stu-id="c6386-230">This metrics is calculated as a difference between recent average execution and history average execution multiplied by the number of recent executions.</span></span> <span data-ttu-id="c6386-231">它实际上表示相对于历史记录，引入了多少额外的持续时间最近执行：</span><span class="sxs-lookup"><span data-stu-id="c6386-231">It actually represents how much of additional duration recent executions introduced compared to history:</span></span>

```
--- "Recent" workload - last 1 hour
DECLARE @recent_start_time datetimeoffset;
DECLARE @recent_end_time datetimeoffset;
SET @recent_start_time = DATEADD(hour, -1, SYSUTCDATETIME());
SET @recent_end_time = SYSUTCDATETIME();

--- "History" workload
DECLARE @history_start_time datetimeoffset;
DECLARE @history_end_time datetimeoffset;
SET @history_start_time = DATEADD(hour, -24, SYSUTCDATETIME());
SET @history_end_time = SYSUTCDATETIME();

WITH
hist AS
(
    SELECT 
        p.query_id query_id, 
        CONVERT(float, SUM(rs.avg_duration*rs.count_executions)) total_duration, 
        SUM(rs.count_executions) count_executions,
        COUNT(distinct p.plan_id) num_plans 
     FROM sys.query_store_runtime_stats AS rs
        JOIN sys.query_store_plan p ON p.plan_id = rs.plan_id
    WHERE  (rs.first_execution_time >= @history_start_time AND rs.last_execution_time < @history_end_time)
        OR (rs.first_execution_time <= @history_start_time AND rs.last_execution_time > @history_start_time)
        OR (rs.first_execution_time <= @history_end_time AND rs.last_execution_time > @history_end_time)
    GROUP BY p.query_id
),
recent AS
(
    SELECT 
        p.query_id query_id, 
        CONVERT(float, SUM(rs.avg_duration*rs.count_executions)) total_duration, 
        SUM(rs.count_executions) count_executions,
        COUNT(distinct p.plan_id) num_plans 
    FROM sys.query_store_runtime_stats AS rs
        JOIN sys.query_store_plan p ON p.plan_id = rs.plan_id
    WHERE  (rs.first_execution_time >= @recent_start_time AND rs.last_execution_time < @recent_end_time)
        OR (rs.first_execution_time <= @recent_start_time AND rs.last_execution_time > @recent_start_time)
        OR (rs.first_execution_time <= @recent_end_time AND rs.last_execution_time > @recent_end_time)
    GROUP BY p.query_id
)
SELECT 
    results.query_id query_id,
    results.query_text query_text,
    results.additional_duration_workload additional_duration_workload,
    results.total_duration_recent total_duration_recent,
    results.total_duration_hist total_duration_hist,
    ISNULL(results.count_executions_recent, 0) count_executions_recent,
    ISNULL(results.count_executions_hist, 0) count_executions_hist 
FROM
(
    SELECT
        hist.query_id query_id,
        qt.query_sql_text query_text,
        ROUND(CONVERT(float, recent.total_duration/recent.count_executions-hist.total_duration/hist.count_executions)*(recent.count_executions), 2) AS additional_duration_workload,
        ROUND(recent.total_duration, 2) total_duration_recent, 
        ROUND(hist.total_duration, 2) total_duration_hist,
        recent.count_executions count_executions_recent,
        hist.count_executions count_executions_hist   
    FROM hist 
        JOIN recent 
            ON hist.query_id = recent.query_id 
        JOIN sys.query_store_query AS q 
            ON q.query_id = hist.query_id
        JOIN sys.query_store_query_text AS qt 
            ON q.query_text_id = qt.query_text_id    
) AS results
WHERE additional_duration_workload > 0
ORDER BY additional_duration_workload DESC
OPTION (MERGE JOIN);
```



###  <a name="maintaining-query-performance-stability"></a><a name="Stability"></a><span data-ttu-id="c6386-232">维护查询性能稳定性</span><span class="sxs-lookup"><span data-stu-id="c6386-232">Maintaining Query Performance Stability</span></span>
 <span data-ttu-id="c6386-233">对于执行多次的查询，你可能注意到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 使用了会导致不同资源利用率和持续时间的不同计划。</span><span class="sxs-lookup"><span data-stu-id="c6386-233">For queries that are executed multiple times you may notice that [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] used different plans which resulted in different resource utilization and duration.</span></span> <span data-ttu-id="c6386-234">借助查询存储，你可以轻松检测到查询性能何时回归，并确定在感兴趣的时间段内的最优计划。</span><span class="sxs-lookup"><span data-stu-id="c6386-234">With Query Store you can easily detect when the query performance regressed and determine the optimal plan within a period of interest.</span></span> <span data-ttu-id="c6386-235">然后你可以对未来查询执行强制执行此最优计划。</span><span class="sxs-lookup"><span data-stu-id="c6386-235">Then you can force that optimal plan for future query execution.</span></span>

 <span data-ttu-id="c6386-236">你还可以使用参数（自动参数化或手动参数化）来标识某一查询内不一致的查询性能。</span><span class="sxs-lookup"><span data-stu-id="c6386-236">You can also identify inconsistent query performance for a query with parameters (either auto- parameterized or manually parameterized).</span></span> <span data-ttu-id="c6386-237">你可以在不同计划中标识出对所有或大多数参数值而言足够快和最佳的计划，并强制执行此计划；为更大范围的用户方案保留可预测的性能。</span><span class="sxs-lookup"><span data-stu-id="c6386-237">Among different plans you can identify plan which is fast and optimal enough for all or most of the parameter values and force that plan; keeping predictable performance for the wider set of user scenarios.</span></span>

 <span data-ttu-id="c6386-238">**强制执行或计划查询（应用强制策略）。**</span><span class="sxs-lookup"><span data-stu-id="c6386-238">**Force or a plan for a query (apply forcing policy).**</span></span> <span data-ttu-id="c6386-239">当向某一查询强制执行某个计划时，每次查询开始执行时其强制执行的计划都会随同一起执行。</span><span class="sxs-lookup"><span data-stu-id="c6386-239">When a plan is forced for a certain query, every time a query comes to execution it will be executed with the plan that is forced.</span></span>

```
EXEC sp_query_store_force_plan @query_id = 48, @plan_id = 49;
```

 <span data-ttu-id="c6386-240">在使用 `sp_query_store_force_plan` 时，你只可以强制执行查询存储记录为该查询计划的那些计划。</span><span class="sxs-lookup"><span data-stu-id="c6386-240">When using `sp_query_store_force_plan` you can only force plans that were recorded by Query Store as a plan for that query.</span></span> <span data-ttu-id="c6386-241">换句话说，可用于查询的计划只有那些在查询存储处于活动状态时已使用执行 Q1 的哪些计划。</span><span class="sxs-lookup"><span data-stu-id="c6386-241">In other words, the only plans available for a query are those that were already used to execute Q1 while Query Store was active.</span></span>

 <span data-ttu-id="c6386-242">**删除强制执行查询的计划。**</span><span class="sxs-lookup"><span data-stu-id="c6386-242">**Remove plan forcing for a query.**</span></span> <span data-ttu-id="c6386-243">若要再次依赖于 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 查询优化器来计算最佳查询计划，请使用 `sp_query_store_unforce_plan` 取消强制执行为查询选择的计划。</span><span class="sxs-lookup"><span data-stu-id="c6386-243">To rely again on the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] query optimizer to calculate the optimal query plan, use `sp_query_store_unforce_plan` to unforce the plan that was selected for the query.</span></span>

```
EXEC sp_query_store_unforce_plan @query_id = 48, @plan_id = 49;
```



## <a name="see-also"></a><span data-ttu-id="c6386-244">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c6386-244">See Also</span></span>
 <span data-ttu-id="c6386-245">[监视和优化性能](../performance/monitor-and-tune-for-performance.md)[性能监视和优化工具](../performance/performance-monitoring-and-tuning-tools.md)[打开活动监视器 &#40;SQL Server Management Studio&#41;](../performance-monitor/open-activity-monitor-sql-server-management-studio.md) [活动监视器](../performance-monitor/activity-monitor.md)</span><span class="sxs-lookup"><span data-stu-id="c6386-245">[Monitor and Tune for Performance](../performance/monitor-and-tune-for-performance.md) [Performance Monitoring and Tuning Tools](../performance/performance-monitoring-and-tuning-tools.md) [Open Activity Monitor &#40;SQL Server Management Studio&#41;](../performance-monitor/open-activity-monitor-sql-server-management-studio.md) [Activity Monitor](../performance-monitor/activity-monitor.md)</span></span>


