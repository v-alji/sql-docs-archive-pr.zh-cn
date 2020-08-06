---
title: 基数估计 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 11/24/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- cardinality estimator
- CE (cardinality estimator)
- estimating cardinality
ms.assetid: baa8a304-5713-4cfe-a699-345e819ce6df
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: aa56127f649d71bfcc8825322f8bf729175d41df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591316"
---
# <a name="cardinality-estimation-sql-server"></a><span data-ttu-id="ba6c5-102">基数估计 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ba6c5-102">Cardinality Estimation (SQL Server)</span></span>
  <span data-ttu-id="ba6c5-103">称作基数估计器的基数估计逻辑已在 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 中重新设计，以便改进查询计划的质量，并因此改进查询性能。</span><span class="sxs-lookup"><span data-stu-id="ba6c5-103">The cardinality estimation logic, called the cardinality estimator, is re-designed in [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] to improve the quality of query plans, and therefore to improve query performance.</span></span> <span data-ttu-id="ba6c5-104">新的基数估计器纳入在新型 OLTP 和数据仓库工作负荷中表现优异的假设和算法。</span><span class="sxs-lookup"><span data-stu-id="ba6c5-104">The new cardinality estimator incorporates assumptions and algorithms that work well on modern OLTP and data warehousing workloads.</span></span> <span data-ttu-id="ba6c5-105">它基于针对新型工作负荷的深入基数估计研究，以及我们在过去 15 年在改进 SQL Server 基数估计器方面的学习。</span><span class="sxs-lookup"><span data-stu-id="ba6c5-105">It is based on in-depth cardinality estimation research on modern workloads, and our learnings over the past 15 years of improving the SQL Server cardinality estimator.</span></span> <span data-ttu-id="ba6c5-106">客户反馈表明，尽管大多数查询将会从更改或保持不更改中受益，但与以前的基数估计器相比，少数查询可能会显得退步。</span><span class="sxs-lookup"><span data-stu-id="ba6c5-106">Feedback from customers shows that while most queries will benefit from the change or remain unchanged, a small number might show regressions compared to the previous cardinality estimator.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ba6c5-107">基数估计是对查询结果中行数的预测。</span><span class="sxs-lookup"><span data-stu-id="ba6c5-107">Cardinality estimates are a prediction of the number of rows in the query result.</span></span> <span data-ttu-id="ba6c5-108">查询优化器使用这些估计选择查询执行计划。</span><span class="sxs-lookup"><span data-stu-id="ba6c5-108">The query optimizer uses these estimates to choose a plan for executing the query.</span></span> <span data-ttu-id="ba6c5-109">查询计划的质量对于改进查询性能有着直接影响。</span><span class="sxs-lookup"><span data-stu-id="ba6c5-109">The quality of the query plan has a direct impact on improving query performance.</span></span>  
  
## <a name="performance-testing-and-tuning-recommendations"></a><span data-ttu-id="ba6c5-110">性能测试和优化建议</span><span class="sxs-lookup"><span data-stu-id="ba6c5-110">Performance Testing and Tuning Recommendations</span></span>  
 <span data-ttu-id="ba6c5-111">对于在 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]中创建的所有新数据库，将启用新基数估计器。</span><span class="sxs-lookup"><span data-stu-id="ba6c5-111">The new cardinality estimator is enabled for all new databases created in [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)].</span></span> <span data-ttu-id="ba6c5-112">但是，升级到 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 并不会对现有数据库启用新基数估计器。</span><span class="sxs-lookup"><span data-stu-id="ba6c5-112">However, upgrading to [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] does not enable the new cardinality estimator on existing databases.</span></span>  
  
 <span data-ttu-id="ba6c5-113">若要确保最佳查询性能，请使用以下建议用新的基数估计器测试您的工作负荷，然后在您的生产系统中启用它。</span><span class="sxs-lookup"><span data-stu-id="ba6c5-113">To ensure the best query performance, use these recommendations to test your workload with the new cardinality estimator before enabling it on your production system.</span></span>  
  
1.  <span data-ttu-id="ba6c5-114">升级所有现有数据库以便使用新的基数估计器。</span><span class="sxs-lookup"><span data-stu-id="ba6c5-114">Upgrade all existing databases to use the new cardinality estimator.</span></span> <span data-ttu-id="ba6c5-115">为此，请使用[ALTER Database 兼容级别 &#40;transact-sql&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level)将数据库兼容级别设置为120。</span><span class="sxs-lookup"><span data-stu-id="ba6c5-115">To do this, use [ALTER DATABASE Compatibility Level &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level) to set the database compatibility level to 120.</span></span>  
  
2.  <span data-ttu-id="ba6c5-116">使用新基数估计器运行测试工作负荷，然后通过当前用来解决性能问题的相同方式解决任何新性能问题。</span><span class="sxs-lookup"><span data-stu-id="ba6c5-116">Run your test workload with the new cardinality estimator, and then troubleshoot any new performance issues in the same manner you currently troubleshoot performance issues.</span></span>  
  
3.  <span data-ttu-id="ba6c5-117">在用新的基数估计器（数据库兼容级别 120 (SQL Server 2014)）运行工作负荷并且特定查询已回归后，你可以运行具有跟踪标志 9481 的查询，以便使用在 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 及更早版本中使用的基数估计器版本。</span><span class="sxs-lookup"><span data-stu-id="ba6c5-117">Once your workload is running with the new cardinality estimator (database compatibility level 120 (SQL Server 2014)), and a specific query has regressed, you can run the query with trace flag 9481 to use the version of the cardinality estimator used in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] and earlier.</span></span> <span data-ttu-id="ba6c5-118">若要运行具有跟踪标志的查询，请参阅知识库文章 [启用可通过特定查询级别上的不同跟踪标志控制的影响计划的 SQL Server 查询优化器行为](https://support.microsoft.com/kb/2801413)。</span><span class="sxs-lookup"><span data-stu-id="ba6c5-118">To run a query with a trace flag, see the KB article [Enable plan-affecting SQL Server query optimizer behavior that can be controlled by different trace flags on a specific-query level](https://support.microsoft.com/kb/2801413).</span></span>  
  
4.  <span data-ttu-id="ba6c5-119">如果一次无法更改所有数据库以使用新的基数估计器，则可以通过使用[ALTER Database 兼容级别 &#40;transact-sql&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level)将数据库兼容级别设置为110，对所有数据库使用以前的基数估计器。</span><span class="sxs-lookup"><span data-stu-id="ba6c5-119">If you cannot change all of the databases at once to use the new cardinality estimator, you can use the former cardinality estimator for all databases by using [ALTER DATABASE Compatibility Level &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level) to set the database compatibility level to 110.</span></span>  
  
5.  <span data-ttu-id="ba6c5-120">如果使用数据库兼容级别 110 运行您的工作负荷并且您想要使用新的基数估计器测试或运行特定查询，则可以运行具有跟踪标志 2312 的查询，以便使用 SQL Server 2014 版基数估计器。</span><span class="sxs-lookup"><span data-stu-id="ba6c5-120">If your workload is running with database compatibility level 110 and you want to test or run a specific query with the new cardinality estimator, you can run the query with trace flag 2312 to use the SQL Server 2014 version of the cardinality estimator.</span></span>  <span data-ttu-id="ba6c5-121">若要运行具有跟踪标志的查询，请参阅知识库文章 [启用可通过特定查询级别上的不同跟踪标志控制的影响计划的 SQL Server 查询优化器行为](https://support.microsoft.com/kb/2801413)。</span><span class="sxs-lookup"><span data-stu-id="ba6c5-121">To run a query with a trace flag, see the KB article [Enable plan-affecting SQL Server query optimizer behavior that can be controlled by different trace flags on a specific-query level](https://support.microsoft.com/kb/2801413).</span></span>  
  
## <a name="new-xevents"></a><span data-ttu-id="ba6c5-122">新 XEvents</span><span class="sxs-lookup"><span data-stu-id="ba6c5-122">New XEvents</span></span>  
 <span data-ttu-id="ba6c5-123">有两个新的 query_optimizer_estimate_cardinality XEvents 以便支持新查询计划。</span><span class="sxs-lookup"><span data-stu-id="ba6c5-123">There are two new query_optimizer_estimate_cardinality XEvents to support the new query plans.</span></span>  
  
-   <span data-ttu-id="ba6c5-124">*query_optimizer_estimate_cardinality* 在查询优化器对关系表达式上的基数进行评估时发生。</span><span class="sxs-lookup"><span data-stu-id="ba6c5-124">*query_optimizer_estimate_cardinality* occurs when the query optimizer estimates the cardinality on a relational expression.</span></span>  
  
-   <span data-ttu-id="ba6c5-125">*query_optimizer_force_both_cardinality_estimation*_behaviors 在启用跟踪标志 2312 以及 9481 时发生，并且尝试同时强制旧的和新的基数估计行为。</span><span class="sxs-lookup"><span data-stu-id="ba6c5-125">*query_optimizer_force_both_cardinality_estimation*_behaviors occurs when both traceflags 2312 and 9481 are enabled, attempting to force both old and new cardinality estimation behavior at the same time.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="ba6c5-126">示例</span><span class="sxs-lookup"><span data-stu-id="ba6c5-126">Examples</span></span>  
 <span data-ttu-id="ba6c5-127">下面的示例显示新基数估计中的一些更改。</span><span class="sxs-lookup"><span data-stu-id="ba6c5-127">The following examples show some of the changes in the new cardinality estimates.</span></span> <span data-ttu-id="ba6c5-128">用于估计基数的代码已重新编写。</span><span class="sxs-lookup"><span data-stu-id="ba6c5-128">The code for estimating cardinality has been rewritten.</span></span> <span data-ttu-id="ba6c5-129">相关逻辑十分复杂，并且无法提供所有更改的详尽列表。</span><span class="sxs-lookup"><span data-stu-id="ba6c5-129">The logic is complex and it is not possible to provide an exhaustive list of all changes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ba6c5-130">这些示例作为概念信息提供。</span><span class="sxs-lookup"><span data-stu-id="ba6c5-130">These examples are provided as conceptual information.</span></span> <span data-ttu-id="ba6c5-131">您无需执行操作以便改变您设计数据库和查询的方式。</span><span class="sxs-lookup"><span data-stu-id="ba6c5-131">No action is required on your part to change the way you design databases and queries.</span></span>  
  
### <a name="example-a-new-cardinality-estimates-use-an-average-cardinality-for-recently-added-ascending-data"></a><span data-ttu-id="ba6c5-132">示例 A. 新基数估计使用平均基数用于新添加的升序数据</span><span class="sxs-lookup"><span data-stu-id="ba6c5-132">Example A. New cardinality estimates use an average cardinality for recently added ascending data</span></span>  
 <span data-ttu-id="ba6c5-133">该示例演示对于在最近统计信息更新期间超出表中最大值的升序数据，新的基数估计器是如何改进基数估计的。</span><span class="sxs-lookup"><span data-stu-id="ba6c5-133">This example demonstrates how the new cardinality estimator can improve cardinality estimates for ascending data that exceeds the maximum value in the table during the most recent statistics update.</span></span>  
  
```  
SELECT item, category, amount FROM dbo.Sales AS s WHERE Date = '2013-12-19';  
```  
  
 <span data-ttu-id="ba6c5-134">在该示例中，每天都有新行添加到 Sales 表，查询请求在 12/19/2013 发生的销售，并且统计信息上次更新时间是 12/18/2013。</span><span class="sxs-lookup"><span data-stu-id="ba6c5-134">In this example, new rows are added to the Sales table each day, the query asks for sales that occurred on 12/19/2013, and statistics were last updated on 12/18/2013.</span></span> <span data-ttu-id="ba6c5-135">之前的基数估计器假定 12/19/2013 值不存在，因为该日期超出了最大日期并且统计信息没有更新以便包括 12/19/2013 值。</span><span class="sxs-lookup"><span data-stu-id="ba6c5-135">The previous cardinality estimator assumes the 12/19/2013 values do not exist since the date exceeds the maximum date and statistics have not been updated to include the 12/19/2013 values.</span></span> <span data-ttu-id="ba6c5-136">这种情形称作升序键问题，如果在该天您加载数据，然后在更新统计信息前就对数据运行查询，则会发生此问题。</span><span class="sxs-lookup"><span data-stu-id="ba6c5-136">This situation, known as the ascending key problem, will occur if you load data during the day, and then run queries against the data before statistics are updated.</span></span>  
  
 <span data-ttu-id="ba6c5-137">此行为已更改。</span><span class="sxs-lookup"><span data-stu-id="ba6c5-137">This behavior has changed.</span></span> <span data-ttu-id="ba6c5-138">现在，即使对于自上次统计信息更新后添加的最近的升序数据未进行更新，新的基数估计器也假定这些值存在并且对于列中的每个值将平均基数用作基数估计。</span><span class="sxs-lookup"><span data-stu-id="ba6c5-138">Now, even if statistics have not been updated for the most recent ascending data that is added since the last statistics update, the new cardinality estimator assumes the values exist and uses the average cardinality for each value in the column as the cardinality estimate.</span></span>  
  
### <a name="example-b-new-cardinality-estimates-assume-filtered-predicates-on-the-same-table-have-some-correlation"></a><span data-ttu-id="ba6c5-139">示例 B. 新的基数估计假定对同一个表的筛选的谓词具有某种关联</span><span class="sxs-lookup"><span data-stu-id="ba6c5-139">Example B. New cardinality estimates assume filtered predicates on the same table have some correlation</span></span>  
 <span data-ttu-id="ba6c5-140">对于该示例，我们假定表 Cars 是 1000 行，Make 对于“Honda”具有 200 个匹配项，Model 对于“Civic”具有 50 个匹配项，并且所有 Civics 均为 Hondas。</span><span class="sxs-lookup"><span data-stu-id="ba6c5-140">For this example, assume the table Cars as 1000 rows, Make has 200 matches for 'Honda', Model has 50 matches for 'Civic', and that all of the Civics are Hondas.</span></span> <span data-ttu-id="ba6c5-141">因此，Make 列中 20% 的值是“Honda”，Model 列中 5% 的值是“Civic”，并且 Honda Civics 的实际数目为 50。</span><span class="sxs-lookup"><span data-stu-id="ba6c5-141">Therefore, 20% of the values in the Make column are 'Honda', 5% of the values in the Model column are 'Civic', and the actual number of Honda Civics is 50.</span></span> <span data-ttu-id="ba6c5-142">以前的基数估计假定 Make 和 Model 列中的值是彼此独立的。</span><span class="sxs-lookup"><span data-stu-id="ba6c5-142">The previous cardinality estimates assume the values in the Make and the Model columns are independent of each other.</span></span> <span data-ttu-id="ba6c5-143">之前的查询优化器估计有10个 Honda Civics ( .05 \* .20 \* 1000 行 = 10 行) 。</span><span class="sxs-lookup"><span data-stu-id="ba6c5-143">The previous query optimizer estimates there are 10 Honda Civics (.05 \* .20 \* 1000 rows = 10 rows).</span></span>  
  
```  
SELECT year, purchase_price FROM dbo.Cars WHERE Make = 'Honda' AND Model = 'Civic';  
```  
  
 <span data-ttu-id="ba6c5-144">此行为已更改。</span><span class="sxs-lookup"><span data-stu-id="ba6c5-144">This behavior has changed.</span></span> <span data-ttu-id="ba6c5-145">现在，新基数估计假定 Make 和 Model 列具有“某种” \*\* 关联。</span><span class="sxs-lookup"><span data-stu-id="ba6c5-145">Now, the new cardinality estimates assume the Make and Model columns have *some* correlation.</span></span> <span data-ttu-id="ba6c5-146">查询优化器通过向估计公式添加指数成分，估计更高的基数。</span><span class="sxs-lookup"><span data-stu-id="ba6c5-146">The query optimizer estimates a higher cardinality by adding an exponential component to the estimation equation.</span></span> <span data-ttu-id="ba6c5-147">查询优化器现在估计22.36 行 ( .05 \* SQRT ( .20) \* 1000 rows = 22.36 行 ) 与该谓词相匹配。</span><span class="sxs-lookup"><span data-stu-id="ba6c5-147">The query optimizer now estimates that 22.36 rows ( .05 \* SQRT(.20) \* 1000 rows = 22.36 rows ) match the predicate.</span></span> <span data-ttu-id="ba6c5-148">对于此方案以及特定的数据分布，22.36 行更接近于该查询将返回的实际 50 行。</span><span class="sxs-lookup"><span data-stu-id="ba6c5-148">For this scenario and specific data distribution, 22.36 rows is closer to the actual 50 rows that the query will return.</span></span>  
  
 <span data-ttu-id="ba6c5-149">请注意，新的基数估计器逻辑将对谓词选择性进行排序并且增加该指数。</span><span class="sxs-lookup"><span data-stu-id="ba6c5-149">Note, the new cardinality estimator logic sorts the predicate selectivities and increases the exponent.</span></span> <span data-ttu-id="ba6c5-150">例如，如果谓语选择性为 .05、.20 和 .25，则基数估计将是 ( .05 \* SQRT ( .20) \* sqrt (sqrt ( .25) # A6 ) 。</span><span class="sxs-lookup"><span data-stu-id="ba6c5-150">For example, if the predicate selectivities were .05, .20, and .25, the cardinality estimate would be (.05 \* SQRT(.20) \* SQRT(SQRT(.25)) ).</span></span>  
  
### <a name="example-c-new-cardinality-estimates-assume-filtered-predicates-on-different-tables-are-independent"></a><span data-ttu-id="ba6c5-151">示例 C. 新的基数估计假定对不同表的筛选的谓词是独立的</span><span class="sxs-lookup"><span data-stu-id="ba6c5-151">Example C. New cardinality estimates assume filtered predicates on different tables are independent</span></span>  
 <span data-ttu-id="ba6c5-152">对于此示例，以前的基数估计器谓词筛选器 filters s.type 和 r.date 是关联的。</span><span class="sxs-lookup"><span data-stu-id="ba6c5-152">For this example, the previous cardinality estimator assumes that the predicate filters s.type and r.date are correlated.</span></span> <span data-ttu-id="ba6c5-153">但是，针对新型工作负荷的测试结果表明，针对不同表中列上的谓词筛选器通常是彼此不相关的。</span><span class="sxs-lookup"><span data-stu-id="ba6c5-153">However, test results on modern workloads showed that predicate filters on columns in different tables are usually not correlated with each other.</span></span>  
  
```  
SELECT s.ticket, s.customer, r.store FROM dbo.Sales AS s CROSS JOIN dbo.Returns AS r  
WHERE s.ticket = r.ticket AND s.type = 'toy' AND r.date = '2013-12-19';  
```  
  
 <span data-ttu-id="ba6c5-154">此行为已更改。</span><span class="sxs-lookup"><span data-stu-id="ba6c5-154">This behavior has changed.</span></span> <span data-ttu-id="ba6c5-155">现在，新的基数估计器逻辑假定 s.type 与 r.date 不相关。</span><span class="sxs-lookup"><span data-stu-id="ba6c5-155">Now, the new cardinality estimator logic assumes that s.type is not correlated with r.date.</span></span> <span data-ttu-id="ba6c5-156">实际上，假定是每天都会退回玩具，而不是在具体某一天退回。</span><span class="sxs-lookup"><span data-stu-id="ba6c5-156">In practical terms, the assumption is that toys are returned every day and not only on a specific day.</span></span> <span data-ttu-id="ba6c5-157">在此类情形下，与以前的基数估计相比，新的基数估计将是更小的数值。</span><span class="sxs-lookup"><span data-stu-id="ba6c5-157">In this case, the new cardinality estimates will be a smaller number than the previous cardinality estimates.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba6c5-158">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ba6c5-158">See Also</span></span>  
 [<span data-ttu-id="ba6c5-159">监视和优化性能</span><span class="sxs-lookup"><span data-stu-id="ba6c5-159">Monitor and Tune for Performance</span></span>](monitor-and-tune-for-performance.md)  
  
  
