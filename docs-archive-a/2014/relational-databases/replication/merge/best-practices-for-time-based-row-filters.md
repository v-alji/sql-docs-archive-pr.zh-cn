---
title: 基于时间的行筛选器的最佳做法 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- best practices
ms.assetid: 773c5c62-fd44-44ab-9c6b-4257dbf8ffdb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ccaafe71d4137fd4b31eec412c1e35595861bdd0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576696"
---
# <a name="best-practices-for-time-based-row-filters"></a><span data-ttu-id="5c94c-102">基于时间的行筛选器的最佳实践</span><span class="sxs-lookup"><span data-stu-id="5c94c-102">Best Practices for Time-Based Row Filters</span></span>
  <span data-ttu-id="5c94c-103">应用程序用户通常需要某个表的基于时间的数据子集。</span><span class="sxs-lookup"><span data-stu-id="5c94c-103">Users of applications often require a time-based subset of data from a table.</span></span> <span data-ttu-id="5c94c-104">例如，销售人员可能需要上周的订单数据，事件计划人员可能需要下周的事件数据。</span><span class="sxs-lookup"><span data-stu-id="5c94c-104">For instance, a salesperson might require data for orders in the last week, or an event planner might require data for events in the upcoming week.</span></span> <span data-ttu-id="5c94c-105">在许多情况下，应用程序使用包含 `GETDATE()` 函数的查询来实现此功能。</span><span class="sxs-lookup"><span data-stu-id="5c94c-105">In many cases, applications use queries containing the `GETDATE()` function to accomplish this.</span></span> <span data-ttu-id="5c94c-106">请考虑以下行筛选器语句：</span><span class="sxs-lookup"><span data-stu-id="5c94c-106">Consider the following row filter statement:</span></span>  
  
```  
WHERE SalesPersonID = CONVERT(INT,HOST_NAME()) AND OrderDate >= (GETDATE()-6)  
```  
  
 <span data-ttu-id="5c94c-107">使用此类型的筛选器时，通常假定合并代理运行时始终发生两件事情：满足此筛选器的行复制到订阅服务器中；从订阅服务器中清除不再满足此筛选器的行。</span><span class="sxs-lookup"><span data-stu-id="5c94c-107">With a filter of this type, it is usually assumed that two things always occur when the Merge Agent runs: rows that satisfy this filter are replicated to Subscribers; and rows that no longer satisfy this filter are cleaned up at Subscribers.</span></span> <span data-ttu-id="5c94c-108"> (有关使用进行筛选的详细信息 `HOST_NAME()` ，请参阅[参数化行筛选器](parameterized-filters-parameterized-row-filters.md)。 ) 不过，合并复制只复制并清除自上次同步后发生更改的数据，而不管如何为该数据定义行筛选器。</span><span class="sxs-lookup"><span data-stu-id="5c94c-108">(For more information about filtering with `HOST_NAME()`, see [Parameterized Row Filters](parameterized-filters-parameterized-row-filters.md).) However, merge replication only replicates and cleans up data that has changed since the last synchronization, regardless of how you define a row filter for that data.</span></span>  
  
 <span data-ttu-id="5c94c-109">要使合并复制处理某一行，该行中的数据必须满足行筛选器，并且该行自上次同步以来必须已发生更改。</span><span class="sxs-lookup"><span data-stu-id="5c94c-109">For merge replication to process a row, the data in the row must satisfy the row filter, and it must have changed since the last synchronization.</span></span> <span data-ttu-id="5c94c-110">对于 **SalesOrderHeader** 表，插入行时将输入 **OrderDate** 。</span><span class="sxs-lookup"><span data-stu-id="5c94c-110">In the case of the **SalesOrderHeader** table, **OrderDate** is entered when a row is inserted.</span></span> <span data-ttu-id="5c94c-111">由于插入是一种数据更改，因此各行将如预期的那样被复制到订阅服务器中。</span><span class="sxs-lookup"><span data-stu-id="5c94c-111">Rows are replicated to the Subscriber as expected because the insert is a data change.</span></span> <span data-ttu-id="5c94c-112">但是，如果订阅服务器中存在不再满足此筛选器的行（这些行是早于七天前的订单中的行），除非由于某种原因更新这些行，否则不会从订阅服务器中将其删除。</span><span class="sxs-lookup"><span data-stu-id="5c94c-112">However, if there are rows at the Subscriber that no longer satisfy the filter (they are for orders older than seven days), they are not removed from the Subscriber unless they were updated for some other reason.</span></span>  
  
 <span data-ttu-id="5c94c-113">事件计划人员的情况进一步突显了此类型筛选所存在的问题。</span><span class="sxs-lookup"><span data-stu-id="5c94c-113">The case of the event planner further highlights the issue with this type of filtering.</span></span> <span data-ttu-id="5c94c-114">对于 **Events** 表，请考虑以下筛选器：</span><span class="sxs-lookup"><span data-stu-id="5c94c-114">Consider the following filter for an **Events** table:</span></span>  
  
```  
WHERE EventCoordID = CONVERT(INT,HOST_NAME()) AND EventDate <= (GETDATE()+6)  
```  
  
 <span data-ttu-id="5c94c-115">对于包含事件的表，可能在事件日期之前进行插入。</span><span class="sxs-lookup"><span data-stu-id="5c94c-115">For a table that contains events, inserts might be made well ahead of the event date.</span></span> <span data-ttu-id="5c94c-116">如果在一个月之前插入了要在下周发生的事件，并且由于某种原因未更新行，那么即使该行满足行筛选器，也不会将该行复制到订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="5c94c-116">If the insert for an event in the coming week was made a month ago and the row was not updated for another reason, the row is not replicated to the Subscriber even if it satisfies the row filter.</span></span>  
  
 <span data-ttu-id="5c94c-117">此外，根据发布的配置方式，合并复制可能会在不同时间对筛选器求值：</span><span class="sxs-lookup"><span data-stu-id="5c94c-117">In addition, depending on how the publication is configured, merge replication evaluates filters at different times:</span></span>  
  
-   <span data-ttu-id="5c94c-118">如果发布使用预计算分区（默认设置），将在插入或更新行时对筛选器求值。</span><span class="sxs-lookup"><span data-stu-id="5c94c-118">If a publication uses precomputed partitions (the default), filters are evaluated when a row is inserted or updated.</span></span>  
  
-   <span data-ttu-id="5c94c-119">如果发布不使用预计算分区，则在合并代理运行时对筛选器求值。</span><span class="sxs-lookup"><span data-stu-id="5c94c-119">If the publication does not use precomputed partitions, filters are evaluated when the Merge Agent runs.</span></span>  
  
 <span data-ttu-id="5c94c-120">有关预计算分区的详细信息，请参阅[使用预计算分区优化参数化筛选器性能](parameterized-filters-optimize-for-precomputed-partitions.md)。</span><span class="sxs-lookup"><span data-stu-id="5c94c-120">For more information about precomputed partitions, see [Optimize Parameterized Filter Performance with Precomputed Partitions](parameterized-filters-optimize-for-precomputed-partitions.md).</span></span> <span data-ttu-id="5c94c-121">对筛选器求值的时间会影响什么数据满足筛选器。</span><span class="sxs-lookup"><span data-stu-id="5c94c-121">The time at which the filter is evaluated affects what data satisfies the filter.</span></span> <span data-ttu-id="5c94c-122">例如，如果发布使用预计算分区，并且每两天同步一次数据，则销售人员的数据子集可能包括比预期时间早两天的行。</span><span class="sxs-lookup"><span data-stu-id="5c94c-122">For example, if a publication uses precomputed partitions, and you synchronize data every two days, the subset of data for the salesperson could include rows up to two days older than expected.</span></span>  
  
## <a name="recommendations-for-using-time-based-row-filters"></a><span data-ttu-id="5c94c-123">使用基于时间的行筛选器时的建议</span><span class="sxs-lookup"><span data-stu-id="5c94c-123">Recommendations for Using Time-Based Row Filters</span></span>  
 <span data-ttu-id="5c94c-124">下面的方法提供了基于时间进行筛选的强大而直接的途径：</span><span class="sxs-lookup"><span data-stu-id="5c94c-124">The following method provides a robust and straightforward approach to filtering based on time:</span></span>  
  
-   <span data-ttu-id="5c94c-125">向表中添加数据类型为 `bit` 的一列。</span><span class="sxs-lookup"><span data-stu-id="5c94c-125">Add a column to the table of data type `bit`.</span></span> <span data-ttu-id="5c94c-126">此列用来指示是否应复制行。</span><span class="sxs-lookup"><span data-stu-id="5c94c-126">This column is used to indicate whether a row should be replicated.</span></span>  
  
-   <span data-ttu-id="5c94c-127">使用引用新列而非基于时间的列的行筛选器。</span><span class="sxs-lookup"><span data-stu-id="5c94c-127">Use a row filter that references the new column rather than a time-based column.</span></span>  
  
-   <span data-ttu-id="5c94c-128">创建一个 SQL Server 代理作业（通过另一种机制计划的作业），该作业在合并代理计划运行之前更新列。</span><span class="sxs-lookup"><span data-stu-id="5c94c-128">Create a SQL Server Agent job (or a job scheduled through another mechanism) that updates the column before the Merge Agent is scheduled to run.</span></span>  
  
 <span data-ttu-id="5c94c-129">此方法解决了使用 `GETDATE()` 或其他基于时间的方法时的缺点，并避免了必须确定何时为分区对筛选器求值的问题。</span><span class="sxs-lookup"><span data-stu-id="5c94c-129">This approach addresses the shortcomings of using `GETDATE()` or another time-based method and avoids the problem of having to determine when filters are evaluated for partitions.</span></span> <span data-ttu-id="5c94c-130">考虑 **Events** 表的以下示例：</span><span class="sxs-lookup"><span data-stu-id="5c94c-130">Consider the following example of an **Events** table:</span></span>  
  
|<span data-ttu-id="5c94c-131">**EventID**</span><span class="sxs-lookup"><span data-stu-id="5c94c-131">**EventID**</span></span>|<span data-ttu-id="5c94c-132">**EventName**</span><span class="sxs-lookup"><span data-stu-id="5c94c-132">**EventName**</span></span>|<span data-ttu-id="5c94c-133">**EventCoordID**</span><span class="sxs-lookup"><span data-stu-id="5c94c-133">**EventCoordID**</span></span>|<span data-ttu-id="5c94c-134">**EventDate**</span><span class="sxs-lookup"><span data-stu-id="5c94c-134">**EventDate**</span></span>|<span data-ttu-id="5c94c-135">**复制**</span><span class="sxs-lookup"><span data-stu-id="5c94c-135">**Replicate**</span></span>|  
|-----------------|-------------------|----------------------|-------------------|-------------------|  
|<span data-ttu-id="5c94c-136">1</span><span class="sxs-lookup"><span data-stu-id="5c94c-136">1</span></span>|<span data-ttu-id="5c94c-137">招待会</span><span class="sxs-lookup"><span data-stu-id="5c94c-137">Reception</span></span>|<span data-ttu-id="5c94c-138">112</span><span class="sxs-lookup"><span data-stu-id="5c94c-138">112</span></span>|<span data-ttu-id="5c94c-139">2006-10-04</span><span class="sxs-lookup"><span data-stu-id="5c94c-139">2006-10-04</span></span>|<span data-ttu-id="5c94c-140">1</span><span class="sxs-lookup"><span data-stu-id="5c94c-140">1</span></span>|  
|<span data-ttu-id="5c94c-141">2</span><span class="sxs-lookup"><span data-stu-id="5c94c-141">2</span></span>|<span data-ttu-id="5c94c-142">晚餐</span><span class="sxs-lookup"><span data-stu-id="5c94c-142">Dinner</span></span>|<span data-ttu-id="5c94c-143">112</span><span class="sxs-lookup"><span data-stu-id="5c94c-143">112</span></span>|<span data-ttu-id="5c94c-144">2006-10-10</span><span class="sxs-lookup"><span data-stu-id="5c94c-144">2006-10-10</span></span>|<span data-ttu-id="5c94c-145">0</span><span class="sxs-lookup"><span data-stu-id="5c94c-145">0</span></span>|  
|<span data-ttu-id="5c94c-146">3</span><span class="sxs-lookup"><span data-stu-id="5c94c-146">3</span></span>|<span data-ttu-id="5c94c-147">聚会</span><span class="sxs-lookup"><span data-stu-id="5c94c-147">Party</span></span>|<span data-ttu-id="5c94c-148">112</span><span class="sxs-lookup"><span data-stu-id="5c94c-148">112</span></span>|<span data-ttu-id="5c94c-149">2006-10-11</span><span class="sxs-lookup"><span data-stu-id="5c94c-149">2006-10-11</span></span>|<span data-ttu-id="5c94c-150">0</span><span class="sxs-lookup"><span data-stu-id="5c94c-150">0</span></span>|  
|<span data-ttu-id="5c94c-151">4</span><span class="sxs-lookup"><span data-stu-id="5c94c-151">4</span></span>|<span data-ttu-id="5c94c-152">婚礼</span><span class="sxs-lookup"><span data-stu-id="5c94c-152">Wedding</span></span>|<span data-ttu-id="5c94c-153">112</span><span class="sxs-lookup"><span data-stu-id="5c94c-153">112</span></span>|<span data-ttu-id="5c94c-154">2006-10-12</span><span class="sxs-lookup"><span data-stu-id="5c94c-154">2006-10-12</span></span>|<span data-ttu-id="5c94c-155">0</span><span class="sxs-lookup"><span data-stu-id="5c94c-155">0</span></span>|  
  
 <span data-ttu-id="5c94c-156">此表的行筛选器将如下所示：</span><span class="sxs-lookup"><span data-stu-id="5c94c-156">The row filter for this table would then look like this:</span></span>  
  
```  
WHERE EventCoordID = CONVERT(INT,HOST_NAME()) AND Replicate = 1  
```  
  
 <span data-ttu-id="5c94c-157">SQL Server 代理作业可在每个合并代理运行之前执行类似如下的 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句：</span><span class="sxs-lookup"><span data-stu-id="5c94c-157">The SQL Server Agent job could execute [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements similar to the following before each Merge Agent run:</span></span>  
  
```  
UPDATE Events SET Replicate = 0 WHERE Replicate = 1  
GO  
UPDATE Events SET Replicate = 1 WHERE EventDate <= GETDATE()+6  
GO  
```  
  
 <span data-ttu-id="5c94c-158">第一行将 **Replicate** 列重置为 **0**，第二行对未来七天内发生的事件将该列设置为 **1** 。</span><span class="sxs-lookup"><span data-stu-id="5c94c-158">The first line resets the **Replicate** column to **0**, and the second line sets the column to **1** for events that occur in the next seven days.</span></span> <span data-ttu-id="5c94c-159">如果此 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句在 2006 年 10 月 7 日运行，则该表将更新为：</span><span class="sxs-lookup"><span data-stu-id="5c94c-159">If this [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement runs on 10/07/2006, the table is updated to:</span></span>  
  
|<span data-ttu-id="5c94c-160">**EventID**</span><span class="sxs-lookup"><span data-stu-id="5c94c-160">**EventID**</span></span>|<span data-ttu-id="5c94c-161">**EventName**</span><span class="sxs-lookup"><span data-stu-id="5c94c-161">**EventName**</span></span>|<span data-ttu-id="5c94c-162">**EventCoordID**</span><span class="sxs-lookup"><span data-stu-id="5c94c-162">**EventCoordID**</span></span>|<span data-ttu-id="5c94c-163">**EventDate**</span><span class="sxs-lookup"><span data-stu-id="5c94c-163">**EventDate**</span></span>|<span data-ttu-id="5c94c-164">**复制**</span><span class="sxs-lookup"><span data-stu-id="5c94c-164">**Replicate**</span></span>|  
|-----------------|-------------------|----------------------|-------------------|-------------------|  
|<span data-ttu-id="5c94c-165">1</span><span class="sxs-lookup"><span data-stu-id="5c94c-165">1</span></span>|<span data-ttu-id="5c94c-166">招待会</span><span class="sxs-lookup"><span data-stu-id="5c94c-166">Reception</span></span>|<span data-ttu-id="5c94c-167">112</span><span class="sxs-lookup"><span data-stu-id="5c94c-167">112</span></span>|<span data-ttu-id="5c94c-168">2006-10-04</span><span class="sxs-lookup"><span data-stu-id="5c94c-168">2006-10-04</span></span>|<span data-ttu-id="5c94c-169">0</span><span class="sxs-lookup"><span data-stu-id="5c94c-169">0</span></span>|  
|<span data-ttu-id="5c94c-170">2</span><span class="sxs-lookup"><span data-stu-id="5c94c-170">2</span></span>|<span data-ttu-id="5c94c-171">晚餐</span><span class="sxs-lookup"><span data-stu-id="5c94c-171">Dinner</span></span>|<span data-ttu-id="5c94c-172">112</span><span class="sxs-lookup"><span data-stu-id="5c94c-172">112</span></span>|<span data-ttu-id="5c94c-173">2006-10-10</span><span class="sxs-lookup"><span data-stu-id="5c94c-173">2006-10-10</span></span>|<span data-ttu-id="5c94c-174">1</span><span class="sxs-lookup"><span data-stu-id="5c94c-174">1</span></span>|  
|<span data-ttu-id="5c94c-175">3</span><span class="sxs-lookup"><span data-stu-id="5c94c-175">3</span></span>|<span data-ttu-id="5c94c-176">聚会</span><span class="sxs-lookup"><span data-stu-id="5c94c-176">Party</span></span>|<span data-ttu-id="5c94c-177">112</span><span class="sxs-lookup"><span data-stu-id="5c94c-177">112</span></span>|<span data-ttu-id="5c94c-178">2006-10-11</span><span class="sxs-lookup"><span data-stu-id="5c94c-178">2006-10-11</span></span>|<span data-ttu-id="5c94c-179">1</span><span class="sxs-lookup"><span data-stu-id="5c94c-179">1</span></span>|  
|<span data-ttu-id="5c94c-180">4</span><span class="sxs-lookup"><span data-stu-id="5c94c-180">4</span></span>|<span data-ttu-id="5c94c-181">婚礼</span><span class="sxs-lookup"><span data-stu-id="5c94c-181">Wedding</span></span>|<span data-ttu-id="5c94c-182">112</span><span class="sxs-lookup"><span data-stu-id="5c94c-182">112</span></span>|<span data-ttu-id="5c94c-183">2006-10-12</span><span class="sxs-lookup"><span data-stu-id="5c94c-183">2006-10-12</span></span>|<span data-ttu-id="5c94c-184">1</span><span class="sxs-lookup"><span data-stu-id="5c94c-184">1</span></span>|  
  
 <span data-ttu-id="5c94c-185">现在，下周的事件被标记为正准备进行复制。</span><span class="sxs-lookup"><span data-stu-id="5c94c-185">The events for the next week are now flagged as being ready to replicate.</span></span> <span data-ttu-id="5c94c-186">当下次为事件协调器 112 使用的订阅运行合并代理时，将把第 2、3 和 4 行下载到订阅服务器中，并从订阅服务器中删除第 1 行。</span><span class="sxs-lookup"><span data-stu-id="5c94c-186">The next time the Merge Agent runs for the subscription that event coordinator 112 uses, rows 2, 3, and 4 will be downloaded to the Subscriber and row 1 will be removed from the Subscriber.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c94c-187">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5c94c-187">See Also</span></span>  
 <span data-ttu-id="5c94c-188">[GETDATE (Transact-SQL)](/sql/t-sql/functions/getdate-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5c94c-188">[GETDATE &#40;Transact-SQL&#41;](/sql/t-sql/functions/getdate-transact-sql) </span></span>  
 <span data-ttu-id="5c94c-189">[执行作业](../../../ssms/agent/implement-jobs.md) </span><span class="sxs-lookup"><span data-stu-id="5c94c-189">[Implement Jobs](../../../ssms/agent/implement-jobs.md) </span></span>  
 [<span data-ttu-id="5c94c-190">参数化行筛选器</span><span class="sxs-lookup"><span data-stu-id="5c94c-190">Parameterized Row Filters</span></span>](parameterized-filters-parameterized-row-filters.md)  
  
  
