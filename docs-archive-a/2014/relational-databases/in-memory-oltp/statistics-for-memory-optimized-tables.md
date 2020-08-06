---
title: 内存优化表的统计信息 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: e644766d-1d1c-43d7-83ff-8ccfe4f3af9f
author: rothja
ms.author: jroth
ms.openlocfilehash: 0ae09d76c2642e23c56afcdd5ae4e1e468ef5883
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693335"
---
# <a name="statistics-for-memory-optimized-tables"></a><span data-ttu-id="134c6-102">内存优化表的统计信息</span><span class="sxs-lookup"><span data-stu-id="134c6-102">Statistics for Memory-Optimized Tables</span></span>
  <span data-ttu-id="134c6-103">查询优化器使用有关列的统计信息来创建可提高查询性能的查询计划。</span><span class="sxs-lookup"><span data-stu-id="134c6-103">The query optimizer uses statistics about columns to create query plans that improve query performance.</span></span> <span data-ttu-id="134c6-104">从数据库中的表收集统计信息并将它保存在数据库元数据中。</span><span class="sxs-lookup"><span data-stu-id="134c6-104">Statistics are collected from the tables in the database and stored in the database metadata.</span></span>  
  
 <span data-ttu-id="134c6-105">统计信息自动创建，但也可以手动创建。</span><span class="sxs-lookup"><span data-stu-id="134c6-105">Statistics are created automatically, but can also be created manually.</span></span> <span data-ttu-id="134c6-106">例如，在创建索引时自动对索引键列创建统计信息。</span><span class="sxs-lookup"><span data-stu-id="134c6-106">For example, statistics are created automatically for index key columns when the index is created.</span></span> <span data-ttu-id="134c6-107">有关创建统计信息的详细信息，请参阅 [Statistics](../statistics/statistics.md)。</span><span class="sxs-lookup"><span data-stu-id="134c6-107">For more information about creating statistics see [Statistics](../statistics/statistics.md).</span></span>  
  
 <span data-ttu-id="134c6-108">随着行的插入、更新和删除，表数据通常在一段时间后发生变化。</span><span class="sxs-lookup"><span data-stu-id="134c6-108">Table data typically changes over time as rows are inserted, updated, and deleted.</span></span> <span data-ttu-id="134c6-109">这意味着需要定期更新统计信息。</span><span class="sxs-lookup"><span data-stu-id="134c6-109">This means statistics need to be updated periodically.</span></span> <span data-ttu-id="134c6-110">默认情况下，在优化器确定基于磁盘的表的统计信息可能过期时，自动更新它们。</span><span class="sxs-lookup"><span data-stu-id="134c6-110">By default, statistics on disk-based tables are updated automatically when the optimizer determines they might be out of date.</span></span>  
  
 <span data-ttu-id="134c6-111">默认情况下，不更新针对内存优化表的统计信息。</span><span class="sxs-lookup"><span data-stu-id="134c6-111">Statistics on memory-optimized tables are not updated by default.</span></span> <span data-ttu-id="134c6-112">您需要手动更新它们。</span><span class="sxs-lookup"><span data-stu-id="134c6-112">Instead, you need to update them manually.</span></span> <span data-ttu-id="134c6-113">对单个列、索引或表使用[UPDATE STATISTICS &#40;transact-sql&#41;](/sql/t-sql/statements/update-statistics-transact-sql) 。</span><span class="sxs-lookup"><span data-stu-id="134c6-113">Use [UPDATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/update-statistics-transact-sql) for individual columns, indexes, or tables.</span></span> <span data-ttu-id="134c6-114">使用[sp_updatestats &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql)为数据库中的所有用户和内部表更新统计信息。</span><span class="sxs-lookup"><span data-stu-id="134c6-114">Use [sp_updatestats &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql) to update statistics for all user and internal tables in the database.</span></span>  
  
 <span data-ttu-id="134c6-115">当使用[CREATE STATISTICS &#40;transact-sql&#41;](/sql/t-sql/statements/create-statistics-transact-sql)或[&#40;TRANSACT-SQL&#41;更新统计信息](/sql/t-sql/statements/update-statistics-transact-sql)时，必须指定 `NORECOMPUTE` 禁用内存优化表的自动统计信息更新。</span><span class="sxs-lookup"><span data-stu-id="134c6-115">When using [CREATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-statistics-transact-sql) or [UPDATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/update-statistics-transact-sql), you must specify `NORECOMPUTE` to disable automatic statistics update for memory-optimized tables.</span></span> <span data-ttu-id="134c6-116">对于基于磁盘的表， [sp_updatestats &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql)仅在自上次[sp_updatestats &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql)后修改了统计信息时才更新统计信息。</span><span class="sxs-lookup"><span data-stu-id="134c6-116">For disk based tables, [sp_updatestats &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql) only updates statistics if the table has been modified since the last [sp_updatestats &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql).</span></span> <span data-ttu-id="134c6-117">对于内存优化表， [sp_updatestats &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql)始终会生成更新的统计信息。</span><span class="sxs-lookup"><span data-stu-id="134c6-117">For memory-optimized tables, [sp_updatestats &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql) always generates updated statistics.</span></span> <span data-ttu-id="134c6-118">对于内存优化的表， [sp_updatestats &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql)是一个不错的选择;否则，您需要了解哪些表有重大更改，以便您可以单独更新统计信息。</span><span class="sxs-lookup"><span data-stu-id="134c6-118">[sp_updatestats &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql) is a good option for memory-optimized tables; otherwise you need to know which tables have significant changes so you can update statistics individually.</span></span>  
  
 <span data-ttu-id="134c6-119">可以通过对数据进行采样或执行完全扫描来生成统计信息。</span><span class="sxs-lookup"><span data-stu-id="134c6-119">Statistics can either be generated by either sampling the data or performing a full scan.</span></span> <span data-ttu-id="134c6-120">抽样的统计信息只使用表数据的样本来估计数据分布情况。</span><span class="sxs-lookup"><span data-stu-id="134c6-120">Sampled statistics only use a sample of the table data to estimate the data distribution.</span></span> <span data-ttu-id="134c6-121">完全扫描统计信息扫描整个表以确定数据分布情况。</span><span class="sxs-lookup"><span data-stu-id="134c6-121">Fullscan statistics scan the entire table to determine the data distribution.</span></span> <span data-ttu-id="134c6-122">完全扫描统计信息通常更为准确，但计算时间较长。</span><span class="sxs-lookup"><span data-stu-id="134c6-122">Fullscan statistics are usually more accurate but take longer to compute.</span></span> <span data-ttu-id="134c6-123">抽样的统计信息收集得更快。</span><span class="sxs-lookup"><span data-stu-id="134c6-123">Sampled statistics can be collected faster.</span></span>  
  
 <span data-ttu-id="134c6-124">默认情况下，基于磁盘的表使用抽样的统计信息。</span><span class="sxs-lookup"><span data-stu-id="134c6-124">Disk-based tables use sampled statistics by default.</span></span> <span data-ttu-id="134c6-125">内存优化的表仅支持完全扫描统计信息。</span><span class="sxs-lookup"><span data-stu-id="134c6-125">Memory-optimized tables only support fullscan statistics.</span></span> <span data-ttu-id="134c6-126">当使用[CREATE STATISTICS &#40;transact-sql&#41;](/sql/t-sql/statements/create-statistics-transact-sql)或[&#40;TRANSACT-SQL&#41;更新统计信息](/sql/t-sql/statements/update-statistics-transact-sql)时，必须 `FULLSCAN` 为内存优化表指定选项。</span><span class="sxs-lookup"><span data-stu-id="134c6-126">When using [CREATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-statistics-transact-sql) or [UPDATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/update-statistics-transact-sql), you must specify the `FULLSCAN` option for memory-optimized tables.</span></span>  
  
 <span data-ttu-id="134c6-127">对于内存优化表的统计信息还有其他注意事项：</span><span class="sxs-lookup"><span data-stu-id="134c6-127">Additional considerations for statistics on memory-optimized tables:</span></span>  
  
-   <span data-ttu-id="134c6-128">使用该表创建内存优化的表的索引。</span><span class="sxs-lookup"><span data-stu-id="134c6-128">Indexes on memory-optimized tables are created with the table.</span></span> <span data-ttu-id="134c6-129">该表为空时，创建索引键列的统计信息。</span><span class="sxs-lookup"><span data-stu-id="134c6-129">The statistics on the index key columns are created when the table is empty.</span></span> <span data-ttu-id="134c6-130">因此，在将数据加载到表后，需要更新这些统计信息。</span><span class="sxs-lookup"><span data-stu-id="134c6-130">Therefore, these statistics need to be updated after data is loaded into the table.</span></span>  
  
-   <span data-ttu-id="134c6-131">对于本机编译的存储过程，在编译该过程时对过程中的查询的执行计划进行优化。</span><span class="sxs-lookup"><span data-stu-id="134c6-131">For natively compiled stored procedures, execution plans for queries in the procedure are optimized when the procedure is compiled.</span></span> <span data-ttu-id="134c6-132">仅当创建该过程和服务器重新启动时才进行这样的优化，在更新统计信息时不进行优化。</span><span class="sxs-lookup"><span data-stu-id="134c6-132">This happens only when the procedure is created and when the server restarts, not when statistics are updated.</span></span> <span data-ttu-id="134c6-133">因此，这些表需要包含数据的有代表性集且在创建过程前统计信息需要是最新的。</span><span class="sxs-lookup"><span data-stu-id="134c6-133">Therefore, the tables need to contain a representative set of data and statistics need to be up-to-date before the procedures are created.</span></span> <span data-ttu-id="134c6-134">（如果数据库脱机并重新联机，或者如果发生服务器重新启动，将重新编译本机编译的存储过程。）</span><span class="sxs-lookup"><span data-stu-id="134c6-134">(Natively compiled stored procedures are recompiled if the database is taken offline and brought back online, or if there is a server restart.)</span></span>  
  
## <a name="guidelines-for-statistics-when-deploying-memory-optimized-tables"></a><span data-ttu-id="134c6-135">部署内存优化的表时统计信息的指南</span><span class="sxs-lookup"><span data-stu-id="134c6-135">Guidelines for Statistics When Deploying Memory-Optimized Tables</span></span>  
 <span data-ttu-id="134c6-136">要确保查询优化器在创建查询计划时具有最新统计信息，请执行以下五个步骤部署内存优化表：</span><span class="sxs-lookup"><span data-stu-id="134c6-136">To ensure that the query optimizer has up-to-date statistics when creating query plans, deploy memory-optimized tables using these five steps:</span></span>  
  
1.  <span data-ttu-id="134c6-137">创建表和索引。</span><span class="sxs-lookup"><span data-stu-id="134c6-137">Create tables and indexes.</span></span> <span data-ttu-id="134c6-138">在 `CREATE TABLE` 语句中内联指定索引。</span><span class="sxs-lookup"><span data-stu-id="134c6-138">Indexes are specified inline in the `CREATE TABLE` statements.</span></span>  
  
2.  <span data-ttu-id="134c6-139">将数据加载到表。</span><span class="sxs-lookup"><span data-stu-id="134c6-139">Load data into the tables.</span></span>  
  
3.  <span data-ttu-id="134c6-140">更新表的统计信息。</span><span class="sxs-lookup"><span data-stu-id="134c6-140">Update statistics on the tables.</span></span>  
  
4.  <span data-ttu-id="134c6-141">创建访问表的存储过程。</span><span class="sxs-lookup"><span data-stu-id="134c6-141">Create stored procedures that access the tables.</span></span>  
  
5.  <span data-ttu-id="134c6-142">运行该工作负荷（它可以包含本机编译的和解释的 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 存储过程）以及即席批处理。</span><span class="sxs-lookup"><span data-stu-id="134c6-142">Run the workload, which can contain a mix of natively compiled and interpreted [!INCLUDE[tsql](../../../includes/tsql-md.md)] stored procedures, as well as ad hoc batches.</span></span>  
  
 <span data-ttu-id="134c6-143">在加载数据并更新统计信息后创建本机编译的存储过程可确保优化器为内存优化的表提供统计信息。</span><span class="sxs-lookup"><span data-stu-id="134c6-143">Creating natively compiled stored procedures after you load the data and update the statistics ensures that the optimizer has statistics available for the memory-optimized tables.</span></span> <span data-ttu-id="134c6-144">这将确保在编译过程时生成高效的查询计划。</span><span class="sxs-lookup"><span data-stu-id="134c6-144">This will ensure efficient query plans when the procedure is compiled.</span></span>  
  
## <a name="guidelines-for-maintaining-statistics-on-memory-optimized-tables"></a><span data-ttu-id="134c6-145">维护内存优化表的统计信息的指南</span><span class="sxs-lookup"><span data-stu-id="134c6-145">Guidelines for Maintaining Statistics on Memory-Optimized Tables</span></span>  
 <span data-ttu-id="134c6-146">要保持统计信息最新，请定期更新内存优化表的统计信息。</span><span class="sxs-lookup"><span data-stu-id="134c6-146">To keep statistics up-to-date, regularly update the statistics on memory-optimized tables.</span></span>  
  
 <span data-ttu-id="134c6-147">如果数据频繁更改，应频繁更新统计信息。</span><span class="sxs-lookup"><span data-stu-id="134c6-147">If data changes frequently, you should update statistics frequently.</span></span> <span data-ttu-id="134c6-148">例如，在批处理更新后更新表统计信息。</span><span class="sxs-lookup"><span data-stu-id="134c6-148">For example, update table statistics after a batch update.</span></span> <span data-ttu-id="134c6-149">更新统计信息后，请删除并重新创建本机编译的存储过程，以便它们可以从更新的统计信息中受益。</span><span class="sxs-lookup"><span data-stu-id="134c6-149">After you update statistics, drop and recreate natively compiled stored procedures so they can benefit from the updated statistics.</span></span>  
  
 <span data-ttu-id="134c6-150">.</span><span class="sxs-lookup"><span data-stu-id="134c6-150">.</span></span>  
  
 <span data-ttu-id="134c6-151">不要在峰值工作负荷期间更新统计信息。</span><span class="sxs-lookup"><span data-stu-id="134c6-151">Do not update statistics during peak workload.</span></span>  
  
 <span data-ttu-id="134c6-152">要更新统计信息：</span><span class="sxs-lookup"><span data-stu-id="134c6-152">To update statistics:</span></span>  
  
-   <span data-ttu-id="134c6-153">用于 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 创建具有[更新统计信息任务](../maintenance-plans/update-statistics-task-maintenance-plan.md)的[维护计划](../maintenance-plans/create-a-maintenance-plan.md)</span><span class="sxs-lookup"><span data-stu-id="134c6-153">Use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to [Create a Maintenance Plan](../maintenance-plans/create-a-maintenance-plan.md) with an [Update Statistic Task](../maintenance-plans/update-statistics-task-maintenance-plan.md)</span></span>  
  
-   <span data-ttu-id="134c6-154">或如下所述通过 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 脚本更新统计信息。</span><span class="sxs-lookup"><span data-stu-id="134c6-154">Or, update statistics through a [!INCLUDE[tsql](../../../includes/tsql-md.md)] script, as discussed below.</span></span>  
  
 <span data-ttu-id="134c6-155"> (*myschema.xml*更新单个内存优化表的统计信息。</span><span class="sxs-lookup"><span data-stu-id="134c6-155">To update the statistics for a single memory-optimized table (*myschema*.</span></span> <span data-ttu-id="134c6-156">*Mytable*) ，请运行以下脚本：</span><span class="sxs-lookup"><span data-stu-id="134c6-156">*Mytable*), run the following script:</span></span>  
  
```  
UPDATE STATISTICS myschema.Mytable WITH FULLSCAN, NORECOMPUTE  
```  
  
 <span data-ttu-id="134c6-157">要更新当前数据库中所有内存优化表的统计信息，请运行以下脚本：</span><span class="sxs-lookup"><span data-stu-id="134c6-157">To update statistics for all memory-optimized tables in the current database, run the following script:</span></span>  
  
```sql  
DECLARE @sql NVARCHAR(MAX) = N''  
  
SELECT @sql += N'  
   UPDATE STATISTICS ' + quotename(schema_name(schema_id)) + N'.' + quotename(name) + N' WITH FULLSCAN, NORECOMPUTE'  
FROM sys.tables WHERE is_memory_optimized=1  
  
EXEC sp_executesql @sql  
```  
  
 <span data-ttu-id="134c6-158">若要更新数据库中所有表的统计信息，请运行[&#40;transact-sql&#41;sp_updatestats ](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="134c6-158">To update statistics for all tables in the database, run [sp_updatestats &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql).</span></span>  
  
 <span data-ttu-id="134c6-159">下面的示例报告有关内存优化表的统计信息上次是在何时更新的。</span><span class="sxs-lookup"><span data-stu-id="134c6-159">The following sample reports when the statistics on memory-optimized tables were last updated.</span></span> <span data-ttu-id="134c6-160">此信息可帮助您决定是否需要更新统计信息。</span><span class="sxs-lookup"><span data-stu-id="134c6-160">This information can help you decide if you need to update the statistics.</span></span>  
  
```sql  
select t.object_id, t.name, sp.last_updated as 'stats_last_updated'  
from sys.tables t join sys.stats s on t.object_id=s.object_id cross apply sys.dm_db_stats_properties(t.object_id, s.stats_id) sp  
where t.is_memory_optimized=1  
```  
  
## <a name="see-also"></a><span data-ttu-id="134c6-161">另请参阅</span><span class="sxs-lookup"><span data-stu-id="134c6-161">See Also</span></span>  
 [<span data-ttu-id="134c6-162">Memory-Optimized Tables</span><span class="sxs-lookup"><span data-stu-id="134c6-162">Memory-Optimized Tables</span></span>](memory-optimized-tables.md)  
  
  
