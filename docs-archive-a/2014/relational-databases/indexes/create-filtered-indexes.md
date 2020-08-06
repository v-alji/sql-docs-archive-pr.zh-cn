---
title: 创建筛选索引 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- filtered indexes [SQL Server], about filtered indexes
- designing indexes [SQL Server], filtered
- filtered indexes [SQL Server]
- nonclustered indexes [SQL Server], filtered
- indexes [SQL Server], filtered
ms.assetid: 25e1fcc5-45d7-4c53-8c79-5493dfaa1c74
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 77cf641ca84181496f26a995244029d0525ade63
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693319"
---
# <a name="create-filtered-indexes"></a><span data-ttu-id="0564e-102">创建筛选索引</span><span class="sxs-lookup"><span data-stu-id="0564e-102">Create Filtered Indexes</span></span>
  <span data-ttu-id="0564e-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中创建筛选索引。</span><span class="sxs-lookup"><span data-stu-id="0564e-103">This topic describes how to create a filtered index in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="0564e-104">筛选索引是一种经过优化的非聚集索引，尤其适用于涵盖从定义完善的数据子集中选择数据的查询。</span><span class="sxs-lookup"><span data-stu-id="0564e-104">A filtered index is an optimized nonclustered index especially suited to cover queries that select from a well-defined subset of data.</span></span> <span data-ttu-id="0564e-105">筛选索引使用筛选谓词对表中的部分行进行索引。</span><span class="sxs-lookup"><span data-stu-id="0564e-105">It uses a filter predicate to index a portion of rows in the table.</span></span> <span data-ttu-id="0564e-106">与全表索引相比，设计良好的筛选索引可以提高查询性能、减少索引维护开销并可降低索引存储开销。</span><span class="sxs-lookup"><span data-stu-id="0564e-106">A well-designed filtered index can improve query performance as well as reduce index maintenance and storage costs compared with full-table indexes.</span></span>  
  
 <span data-ttu-id="0564e-107">筛选索引与全表索引相比具有以下优点：</span><span class="sxs-lookup"><span data-stu-id="0564e-107">Filtered indexes can provide the following advantages over full-table indexes:</span></span>  
  
-   <span data-ttu-id="0564e-108">**提高了查询性能和计划质量**</span><span class="sxs-lookup"><span data-stu-id="0564e-108">**Improved query performance and plan quality**</span></span>  
  
     <span data-ttu-id="0564e-109">设计良好的筛选索引可以提高查询性能和执行计划质量，因为它比全表非聚集索引小并且具有经过筛选的统计信息。</span><span class="sxs-lookup"><span data-stu-id="0564e-109">A well-designed filtered index improves query performance and execution plan quality because it is smaller than a full-table nonclustered index and has filtered statistics.</span></span> <span data-ttu-id="0564e-110">与全表统计信息相比，经过筛选的统计信息更加准确，因为它们只涵盖筛选索引中的行。</span><span class="sxs-lookup"><span data-stu-id="0564e-110">The filtered statistics are more accurate than full-table statistics because they cover only the rows in the filtered index.</span></span>  
  
-   <span data-ttu-id="0564e-111">**减少了索引维护开销**</span><span class="sxs-lookup"><span data-stu-id="0564e-111">**Reduced index maintenance costs**</span></span>  
  
     <span data-ttu-id="0564e-112">仅在数据操作语言 (DML) 语句对索引中的数据产生影响时，才对索引进行维护。</span><span class="sxs-lookup"><span data-stu-id="0564e-112">An index is maintained only when data manipulation language (DML) statements affect the data in the index.</span></span> <span data-ttu-id="0564e-113">与全表非聚集索引相比，筛选索引减少了索引维护开销，因为它更小并且仅在索引中的数据更改时才进行维护。</span><span class="sxs-lookup"><span data-stu-id="0564e-113">A filtered index reduces index maintenance costs compared with a full-table nonclustered index because it is smaller and is only maintained when the data in the index is changed.</span></span> <span data-ttu-id="0564e-114">筛选索引的数量可以非常多，特别是在其中包含很少更改的数据时。</span><span class="sxs-lookup"><span data-stu-id="0564e-114">It is possible to have a large number of filtered indexes, especially when they contain data that is changed infrequently.</span></span> <span data-ttu-id="0564e-115">同样，如果筛选索引只包含频繁修改的数据，则索引大小较小时可以减少更新统计信息的开销。</span><span class="sxs-lookup"><span data-stu-id="0564e-115">Similarly, if a filtered index contains only the frequently modified data, the smaller size of the index reduces the cost of updating the statistics.</span></span>  
  
-   <span data-ttu-id="0564e-116">**减少了索引存储开销**</span><span class="sxs-lookup"><span data-stu-id="0564e-116">**Reduced index storage costs**</span></span>  
  
     <span data-ttu-id="0564e-117">在没必要创建全表索引时，创建筛选索引可以减少非聚集索引的磁盘存储开销。</span><span class="sxs-lookup"><span data-stu-id="0564e-117">Creating a filtered index can reduce disk storage for nonclustered indexes when a full-table index is not necessary.</span></span> <span data-ttu-id="0564e-118">可以使用多个筛选索引替换一个全表非聚集索引而不会明显增加存储需求。</span><span class="sxs-lookup"><span data-stu-id="0564e-118">You can replace a full-table nonclustered index with multiple filtered indexes without significantly increasing the storage requirements.</span></span>  
  
 <span data-ttu-id="0564e-119">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="0564e-119">**In This Topic**</span></span>  
  
-   <span data-ttu-id="0564e-120">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="0564e-120">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="0564e-121">设计注意事项</span><span class="sxs-lookup"><span data-stu-id="0564e-121">Design Considerations</span></span>](#Design)  
  
     [<span data-ttu-id="0564e-122">限制和局限</span><span class="sxs-lookup"><span data-stu-id="0564e-122">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="0564e-123">安全性</span><span class="sxs-lookup"><span data-stu-id="0564e-123">Security</span></span>](#Security)  
  
-   <span data-ttu-id="0564e-124">**创建筛选索引，使用：**</span><span class="sxs-lookup"><span data-stu-id="0564e-124">**To create a filtered index, using:**</span></span>  
  
     [<span data-ttu-id="0564e-125">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0564e-125">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="0564e-126">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="0564e-126">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="0564e-127">开始之前</span><span class="sxs-lookup"><span data-stu-id="0564e-127">Before You Begin</span></span>  
  
###  <a name="design-considerations"></a><a name="Design"></a> <span data-ttu-id="0564e-128">设计注意事项</span><span class="sxs-lookup"><span data-stu-id="0564e-128">Design Considerations</span></span>  
  
-   <span data-ttu-id="0564e-129">在列中只有少量相关值需要查询时，可以针对值的子集创建筛选索引。</span><span class="sxs-lookup"><span data-stu-id="0564e-129">When a column only has a small number of relevant values for queries, you can create a filtered index on the subset of values.</span></span> <span data-ttu-id="0564e-130">例如，当列中的值大部分为 NULL 并且查询只从非 NULL 值中进行选择时，可以为非 NULL 数据行创建筛选索引。</span><span class="sxs-lookup"><span data-stu-id="0564e-130">For example, when the values in a column are mostly NULL and the query selects only from the non-NULL values, you can create a filtered index for the non-NULL data rows.</span></span> <span data-ttu-id="0564e-131">由此得到的索引与对相同键列定义的全表非聚集索引相比，前者更小且维护开销更低。</span><span class="sxs-lookup"><span data-stu-id="0564e-131">The resulting index will be smaller and cost less to maintain than a full-table nonclustered index defined on the same key columns.</span></span>  
  
-   <span data-ttu-id="0564e-132">表中含有异类数据行时，可以为一种或多种类别的数据创建筛选索引。</span><span class="sxs-lookup"><span data-stu-id="0564e-132">When a table has heterogeneous data rows, you can create a filtered index for one or more categories of data.</span></span> <span data-ttu-id="0564e-133">通过将查询范围缩小为表的特定区域，这可以提高针对这些数据行的查询性能。</span><span class="sxs-lookup"><span data-stu-id="0564e-133">This can improve the performance of queries on these data rows by narrowing the focus of a query to a specific area of the table.</span></span> <span data-ttu-id="0564e-134">此外，由此得到的索引与全表非聚集索引相比，前者更小且维护开销更低。</span><span class="sxs-lookup"><span data-stu-id="0564e-134">Again, the resulting index will be smaller and cost less to maintain than a full-table nonclustered index.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="0564e-135">限制和局限</span><span class="sxs-lookup"><span data-stu-id="0564e-135">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="0564e-136">不能对视图创建筛选索引。</span><span class="sxs-lookup"><span data-stu-id="0564e-136">You cannot create a filtered index on a view.</span></span> <span data-ttu-id="0564e-137">但是，查询优化器可以从对视图中引用的表定义的筛选索引中获益。</span><span class="sxs-lookup"><span data-stu-id="0564e-137">However, the query optimizer can benefit from a filtered index defined on a table that is referenced in a view.</span></span> <span data-ttu-id="0564e-138">对于从视图中选择数据的查询，如果查询结果正确，查询优化器会考虑对此查询使用筛选索引。</span><span class="sxs-lookup"><span data-stu-id="0564e-138">The query optimizer considers a filtered index for a query that selects from a view if the query results will be correct.</span></span>  
  
-   <span data-ttu-id="0564e-139">筛选索引与索引视图相比，具有以下优点：</span><span class="sxs-lookup"><span data-stu-id="0564e-139">Filtered indexes have the following advantages over indexed views:</span></span>  
  
    -   <span data-ttu-id="0564e-140">减少了索引维护开销。</span><span class="sxs-lookup"><span data-stu-id="0564e-140">Reduced index maintenance costs.</span></span> <span data-ttu-id="0564e-141">例如，相对于索引视图而言，查询处理器使用更少的 CPU 资源便可更新筛选的索引。</span><span class="sxs-lookup"><span data-stu-id="0564e-141">For example, the query processor uses fewer CPU resources to update a filtered index than an indexed view.</span></span>  
  
    -   <span data-ttu-id="0564e-142">改善了计划质量。</span><span class="sxs-lookup"><span data-stu-id="0564e-142">Improved plan quality.</span></span> <span data-ttu-id="0564e-143">例如，在查询编译期间，查询优化器考虑使用筛选的索引的情况要比考虑使用等效的索引视图的情况多。</span><span class="sxs-lookup"><span data-stu-id="0564e-143">For example, during query compilation, the query optimizer considers using a filtered index in more situations than the equivalent indexed view.</span></span>  
  
    -   <span data-ttu-id="0564e-144">联机索引重新生成。</span><span class="sxs-lookup"><span data-stu-id="0564e-144">Online index rebuilds.</span></span> <span data-ttu-id="0564e-145">您可以在筛选的索引可用于查询时重新生成它们。</span><span class="sxs-lookup"><span data-stu-id="0564e-145">You can rebuild filtered indexes while they are available for queries.</span></span> <span data-ttu-id="0564e-146">索引视图不支持联机索引重新生成。</span><span class="sxs-lookup"><span data-stu-id="0564e-146">Online index rebuilds are not supported for indexed views.</span></span> <span data-ttu-id="0564e-147">有关详细信息，请参阅 [ALTER INDEX (Transact-SQL)](/sql/t-sql/statements/alter-index-transact-sql) 的 REBUILD 选项。</span><span class="sxs-lookup"><span data-stu-id="0564e-147">For more information, see the REBUILD option for [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql).</span></span>  
  
    -   <span data-ttu-id="0564e-148">非唯一索引。</span><span class="sxs-lookup"><span data-stu-id="0564e-148">Non-unique indexes.</span></span> <span data-ttu-id="0564e-149">筛选索引可以是非唯一的，而索引视图必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="0564e-149">Filtered indexes can be non-unique, whereas indexed views must be unique.</span></span>  
  
-   <span data-ttu-id="0564e-150">筛选索引是针对一个表定义的，仅支持简单比较运算符。</span><span class="sxs-lookup"><span data-stu-id="0564e-150">Filtered indexes are defined on one table and only support simple comparison operators.</span></span> <span data-ttu-id="0564e-151">如果需要引用多个表或具有复杂逻辑的筛选表达式，则应创建视图。</span><span class="sxs-lookup"><span data-stu-id="0564e-151">If you need a filter expression that references multiple tables or has complex logic, you should create a view.</span></span>  
  
-   <span data-ttu-id="0564e-152">如果筛选索引表达式等效于查询谓词并且查询并未在查询结果中返回筛选索引表达式中的列，则筛选索引表达式中的列不需要作为筛选索引定义中的键或包含列。</span><span class="sxs-lookup"><span data-stu-id="0564e-152">A column in the filtered index expression does not need to be a key or included column in the filtered index definition if the filtered index expression is equivalent to the query predicate and the query does not return the column in the filtered index expression with the query results.</span></span>  
  
-   <span data-ttu-id="0564e-153">如果查询谓词在不与筛选索引表达式等效的比较中使用了筛选索引表达式中的某列，则该列应为筛选索引定义中的键或包含列。</span><span class="sxs-lookup"><span data-stu-id="0564e-153">A column in the filtered index expression should be a key or included column in the filtered index definition if the query predicate uses the column in a comparison that is not equivalent to the filtered index expression.</span></span>  
  
-   <span data-ttu-id="0564e-154">如果筛选索引表达式中的某列在查询结果集中，则该列应为筛选索引定义中的键或包含列。</span><span class="sxs-lookup"><span data-stu-id="0564e-154">A column in the filtered index expression should be a key or included column in the filtered index definition if the column is in the query result set.</span></span>  
  
-   <span data-ttu-id="0564e-155">表的聚集索引键不需要是筛选索引定义中的键或包含列。</span><span class="sxs-lookup"><span data-stu-id="0564e-155">The clustered index key of the table does not need to be a key or included column in the filtered index definition.</span></span> <span data-ttu-id="0564e-156">聚集索引键自动包含在所有非聚集索引（包括筛选索引）中。</span><span class="sxs-lookup"><span data-stu-id="0564e-156">The clustered index key is automatically included in all nonclustered indexes, including filtered indexes.</span></span>  
  
-   <span data-ttu-id="0564e-157">如果筛选索引结果的筛选索引表达式中指定的比较运算符会导致隐式或显式数据转换，则转换发生在比较运算符的左边时，会出现错误。</span><span class="sxs-lookup"><span data-stu-id="0564e-157">If the comparison operator specified in the filtered index expression of the filtered index results in an implicit or explicit data conversion, an error will occur if the conversion occurs on the left side of a comparison operator.</span></span> <span data-ttu-id="0564e-158">解决方法是在比较运算符的右边编写包含数据转换运算符（CAST 或 CONVERT）的筛选索引表达式。</span><span class="sxs-lookup"><span data-stu-id="0564e-158">A solution is to write the filtered index expression with the data conversion operator (CAST or CONVERT) on the right side of the comparison operator.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="0564e-159">Security</span><span class="sxs-lookup"><span data-stu-id="0564e-159">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="0564e-160">权限</span><span class="sxs-lookup"><span data-stu-id="0564e-160">Permissions</span></span>  
 <span data-ttu-id="0564e-161">要求对表或视图具有 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="0564e-161">Requires ALTER permission on the table or view.</span></span> <span data-ttu-id="0564e-162">用户必须是 **sysadmin** 固定服务器角色的成员，或者是 **db_ddladmin** 和 **db_owner** 固定数据库角色的成员。</span><span class="sxs-lookup"><span data-stu-id="0564e-162">User must be a member of the **sysadmin** fixed server role or the **db_ddladmin** and **db_owner** fixed database roles.</span></span> <span data-ttu-id="0564e-163">若要修改筛选索引表达式，请使用 CREATE INDEX WITH DROP_EXISTING。</span><span class="sxs-lookup"><span data-stu-id="0564e-163">To modify the filtered index expression, use CREATE INDEX WITH DROP_EXISTING.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="0564e-164">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0564e-164">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-filtered-index"></a><span data-ttu-id="0564e-165">创建筛选索引</span><span class="sxs-lookup"><span data-stu-id="0564e-165">To create a filtered index</span></span>  
  
1.  <span data-ttu-id="0564e-166">在对象资源管理器中，单击加号以便展开包含您要创建筛选索引的表的数据库。</span><span class="sxs-lookup"><span data-stu-id="0564e-166">In Object Explorer, click the plus sign to expand the database that contains the table on which you want to create a filtered index.</span></span>  
  
2.  <span data-ttu-id="0564e-167">单击加号以便展开 **“表”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="0564e-167">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="0564e-168">单击加号以便展开您要创建筛选索引的表。</span><span class="sxs-lookup"><span data-stu-id="0564e-168">Click the plus sign to expand the table on which you want to create a filtered index.</span></span>  
  
4.  <span data-ttu-id="0564e-169">右键单击“索引”文件夹，指向“新建索引”，然后选择“非群集索引…”  。</span><span class="sxs-lookup"><span data-stu-id="0564e-169">Right-click the **Indexes** folder, point to **New Index**, and select **Non-Clustered Index...**.</span></span>  
  
5.  <span data-ttu-id="0564e-170">在 **“新建索引”** 对话框的 **“常规”** 页中，在 **“索引名称”** 框中输入新索引的名称。</span><span class="sxs-lookup"><span data-stu-id="0564e-170">In the **New Index** dialog box, on the **General** page, enter the name of the new index in the **Index name** box.</span></span>  
  
6.  <span data-ttu-id="0564e-171">在“索引键列”下，单击“添加…” 。</span><span class="sxs-lookup"><span data-stu-id="0564e-171">Under **Index key columns**, click **Add...**.</span></span>  
  
7.  <span data-ttu-id="0564e-172">在 "**从**_Table_name_中选择列" 对话框中，选中要添加到唯一索引的一个或多个表列的复选框。</span><span class="sxs-lookup"><span data-stu-id="0564e-172">In the **Select Columns from**_table_name_ dialog box, select the check box or check boxes of the table column or columns to be added to the unique index.</span></span>  
  
8.  <span data-ttu-id="0564e-173">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="0564e-173">Click **OK**.</span></span>  
  
9. <span data-ttu-id="0564e-174">在“筛选器”页的“筛选表达式”下，输入要用于创建筛选索引的 SQL 表达式 。</span><span class="sxs-lookup"><span data-stu-id="0564e-174">On the **Filter** page, under **Filter Expression**, enter SQL expression that you'll use to create the filtered index.</span></span>  
  
10. <span data-ttu-id="0564e-175">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="0564e-175">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="0564e-176">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="0564e-176">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-filtered-index"></a><span data-ttu-id="0564e-177">创建筛选索引</span><span class="sxs-lookup"><span data-stu-id="0564e-177">To create a filtered index</span></span>  
  
1.  <span data-ttu-id="0564e-178">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="0564e-178">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="0564e-179">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="0564e-179">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="0564e-180">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="0564e-180">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Looks for an existing filtered index named "FIBillOfMaterialsWithEndDate"  
    -- and deletes it from the table Production.BillOfMaterials if found.   
    IF EXISTS (SELECT name FROM sys.indexes  
        WHERE name = N'FIBillOfMaterialsWithEndDate'  
        AND object_id = OBJECT_ID (N'Production.BillOfMaterials'))  
    DROP INDEX FIBillOfMaterialsWithEndDate  
        ON Production.BillOfMaterials  
    GO  
    -- Creates a filtered index "FIBillOfMaterialsWithEndDate"  
    -- on the table Production.BillOfMaterials   
    -- using the columms ComponentID and StartDate.  
  
    CREATE NONCLUSTERED INDEX FIBillOfMaterialsWithEndDate  
        ON Production.BillOfMaterials (ComponentID, StartDate)  
        WHERE EndDate IS NOT NULL ;  
    GO  
    ```  
  
     <span data-ttu-id="0564e-181">以上筛选索引对下面的查询有效。</span><span class="sxs-lookup"><span data-stu-id="0564e-181">The filtered index above is valid for the following query.</span></span> <span data-ttu-id="0564e-182">您可以显示查询执行计划，以确定查询优化器是否使用了该筛选索引。</span><span class="sxs-lookup"><span data-stu-id="0564e-182">You can display the query execution plan to determine if the query optimizer used the filtered index.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT ProductAssemblyID, ComponentID, StartDate   
    FROM Production.BillOfMaterials  
    WHERE EndDate IS NOT NULL   
        AND ComponentID = 5   
        AND StartDate > '01/01/2008' ;  
    GO  
    ```  
  
#### <a name="to-ensure-that-a-filtered-index-is-used-in-a-sql-query"></a><span data-ttu-id="0564e-183">确保在 SQL 查询中使用筛选索引</span><span class="sxs-lookup"><span data-stu-id="0564e-183">To ensure that a filtered index is used in a SQL query</span></span>  
  
1.  <span data-ttu-id="0564e-184">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="0564e-184">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="0564e-185">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="0564e-185">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="0564e-186">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="0564e-186">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT ComponentID, StartDate FROM Production.BillOfMaterials  
        WITH ( INDEX ( FIBillOfMaterialsWithEndDate ) )   
    WHERE EndDate IN ('20000825', '20000908', '20000918');   
    GO  
    ```  
  
 <span data-ttu-id="0564e-187">有关详细信息，请参阅 [CREATE INDEX (Transact-SQL)](/sql/t-sql/statements/create-index-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="0564e-187">For more information, see  [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql).</span></span>  
  
  
