---
title: 内存优化表查询处理指南 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 065296fe-6711-4837-965e-252ef6c13a0f
author: rothja
ms.author: jroth
ms.openlocfilehash: 93489e5dea295964826005e081bcffe889cb7586
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589573"
---
# <a name="a-guide-to-query-processing-for-memory-optimized-tables"></a><span data-ttu-id="0ad24-102">内存优化表查询处理指南</span><span class="sxs-lookup"><span data-stu-id="0ad24-102">A Guide to Query Processing for Memory-Optimized Tables</span></span>
  <span data-ttu-id="0ad24-103">内存中 OLTP 在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]中引入内存优化的表和本机编译的存储过程。</span><span class="sxs-lookup"><span data-stu-id="0ad24-103">In-Memory OLTP introduces memory-optimized tables and natively compiled stored procedures in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="0ad24-104">本文简单介绍针对内存优化表和本机编译存储过程的查询处理。</span><span class="sxs-lookup"><span data-stu-id="0ad24-104">This article gives an overview of query processing for both memory-optimized tables and natively compiled stored procedures.</span></span>  
  
 <span data-ttu-id="0ad24-105">本文档介绍如何编译和执行对内存优化表的查询，包括：</span><span class="sxs-lookup"><span data-stu-id="0ad24-105">The document explains how queries on memory-optimized tables are compiled and executed, including:</span></span>  
  
-   <span data-ttu-id="0ad24-106">基于磁盘的表的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中的查询处理管道。</span><span class="sxs-lookup"><span data-stu-id="0ad24-106">The query processing pipeline in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] for disk-based tables.</span></span>  
  
-   <span data-ttu-id="0ad24-107">查询优化；内存优化的表统计信息的作用以及有关处理有错的查询计划的准则。</span><span class="sxs-lookup"><span data-stu-id="0ad24-107">Query optimization; the role of statistics on memory-optimized tables as well as guidelines for troubleshooting bad query plans.</span></span>  
  
-   <span data-ttu-id="0ad24-108">使用解释型 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 访问内存优化表。</span><span class="sxs-lookup"><span data-stu-id="0ad24-108">The use of interpreted [!INCLUDE[tsql](../../../includes/tsql-md.md)] to access memory-optimized tables.</span></span>  
  
-   <span data-ttu-id="0ad24-109">有关优化访问内存优化表的查询的注意事项。</span><span class="sxs-lookup"><span data-stu-id="0ad24-109">Considerations about query optimization for memory-optimized table access.</span></span>  
  
-   <span data-ttu-id="0ad24-110">本机编译存储过程编译和处理。</span><span class="sxs-lookup"><span data-stu-id="0ad24-110">Natively compiled stored procedure compilation and processing.</span></span>  
  
-   <span data-ttu-id="0ad24-111">优化器用来估计开销的统计信息。</span><span class="sxs-lookup"><span data-stu-id="0ad24-111">Statistics that are used for cost estimation by the optimizer.</span></span>  
  
-   <span data-ttu-id="0ad24-112">修复问题查询计划的方式。</span><span class="sxs-lookup"><span data-stu-id="0ad24-112">Ways to fix bad query plans.</span></span>  
  
## <a name="example-query"></a><span data-ttu-id="0ad24-113">示例查询</span><span class="sxs-lookup"><span data-stu-id="0ad24-113">Example Query</span></span>  
 <span data-ttu-id="0ad24-114">我们将用下面两个示例说明本文中讨论的查询处理概念。</span><span class="sxs-lookup"><span data-stu-id="0ad24-114">The following example will be used to illustrate the query processing concepts discussed in this article.</span></span>  
  
 <span data-ttu-id="0ad24-115">我们考虑 Customer 和 Order 这两个表。</span><span class="sxs-lookup"><span data-stu-id="0ad24-115">We consider two tables, Customer and Order.</span></span> <span data-ttu-id="0ad24-116">以下 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 脚本按（传统）基于磁盘的形式定义了这两个表和关联的索引：</span><span class="sxs-lookup"><span data-stu-id="0ad24-116">The following [!INCLUDE[tsql](../../../includes/tsql-md.md)] script contains the definitions for these two tables and associated indexes, in their (traditional) disk-based form:</span></span>  
  
```sql  
CREATE TABLE dbo.[Customer] (  
  CustomerID nchar (5) NOT NULL PRIMARY KEY,  
  ContactName nvarchar (30) NOT NULL   
)  
GO  
  
CREATE TABLE dbo.[Order] (  
  OrderID int NOT NULL PRIMARY KEY,  
  CustomerID nchar (5) NOT NULL,  
  OrderDate date NOT NULL  
)  
GO  
CREATE INDEX IX_CustomerID ON dbo.[Order](CustomerID)  
GO  
CREATE INDEX IX_OrderDate ON dbo.[Order](OrderDate)  
GO  
```  
  
 <span data-ttu-id="0ad24-117">为构造本文中所示的查询计划，这两个表是用来自 Northwind 示例数据库的示例数据填充的，你可以从 [SQL Server 2000 的 Northwind 和 pubs 示例数据库](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)下载相关数据库。</span><span class="sxs-lookup"><span data-stu-id="0ad24-117">For constructing the query plans shown in this article, the two tables were populated with sample data from the Northwind sample database, which you can download from [Northwind and pubs Sample Databases for SQL Server 2000](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs).</span></span>  
  
 <span data-ttu-id="0ad24-118">考虑以下查询，这些查询联接 Customer 和 Order 表，并返回订单 ID 和相关客户信息：</span><span class="sxs-lookup"><span data-stu-id="0ad24-118">Consider the following query, which joins the tables Customer and Order and returns the ID of the order and the associated customer information:</span></span>  
  
```sql  
SELECT o.OrderID, c.* FROM dbo.[Customer] c INNER JOIN dbo.[Order] o ON c.CustomerID = o.CustomerID  
```  
  
 <span data-ttu-id="0ad24-119">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 显示的估计的执行计划如下</span><span class="sxs-lookup"><span data-stu-id="0ad24-119">The estimated execution plan as displayed by [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] is as follows</span></span>  
  
 <span data-ttu-id="0ad24-120">![用于联接基于磁盘的表的查询计划。](../../database-engine/media/hekaton-query-plan-1.gif "用于联接基于磁盘的表的查询计划。")</span><span class="sxs-lookup"><span data-stu-id="0ad24-120">![Query plan for join of disk-based tables.](../../database-engine/media/hekaton-query-plan-1.gif "Query plan for join of disk-based tables.")</span></span>  
<span data-ttu-id="0ad24-121">用于联接基于磁盘的表的查询计划。</span><span class="sxs-lookup"><span data-stu-id="0ad24-121">Query plan for join of disk-based tables.</span></span>  
  
 <span data-ttu-id="0ad24-122">关于此查询计划：</span><span class="sxs-lookup"><span data-stu-id="0ad24-122">About this query plan:</span></span>  
  
-   <span data-ttu-id="0ad24-123">来自 Customer 表的行从聚集索引检索，聚集索引是主数据结构并且有完整的表数据。</span><span class="sxs-lookup"><span data-stu-id="0ad24-123">The rows from the Customer table are retrieved from the clustered index, which is the primary data structure and has the full table data.</span></span>  
  
-   <span data-ttu-id="0ad24-124">Order 表的数据是使用 CustomerID 列的非聚集索引检索的。</span><span class="sxs-lookup"><span data-stu-id="0ad24-124">Data from the Order table is retrieved using the nonclustered index on the CustomerID column.</span></span> <span data-ttu-id="0ad24-125">此索引包含 CustomerID 列（用于联接）和主键列 OrderID（返回给用户）。</span><span class="sxs-lookup"><span data-stu-id="0ad24-125">This index contains both the CustomerID column, which is used for the join, and the primary key column OrderID, which is returned to the user.</span></span> <span data-ttu-id="0ad24-126">返回 Order 表的其他列需要查找 Order 表的聚集索引。</span><span class="sxs-lookup"><span data-stu-id="0ad24-126">Returning additional columns from the Order table would require lookups in the clustered index for the Order table.</span></span>  
  
-   <span data-ttu-id="0ad24-127">逻辑运算符 `Inner Join` 是通过物理运算符 `Merge Join` 实现的。</span><span class="sxs-lookup"><span data-stu-id="0ad24-127">The logical operator `Inner Join` is implemented by the physical operator `Merge Join`.</span></span> <span data-ttu-id="0ad24-128">其他物理联接类型为 `Nested Loops` 和 `Hash Join`。</span><span class="sxs-lookup"><span data-stu-id="0ad24-128">The other physical join types are `Nested Loops` and `Hash Join`.</span></span> <span data-ttu-id="0ad24-129">`Merge Join` 运算符利用两个索引都按联接列 CustomerID 排序这一事实。</span><span class="sxs-lookup"><span data-stu-id="0ad24-129">The `Merge Join` operator takes advantage of the fact that both indexes are sorted on the join column CustomerID.</span></span>  
  
 <span data-ttu-id="0ad24-130">考虑一个与此查询稍有不同的查询，它返回 Order 表的所有行，而不仅是 OrderID：</span><span class="sxs-lookup"><span data-stu-id="0ad24-130">Consider a slight variation on this query, which returns all rows from the Order table, not only OrderID:</span></span>  
  
```sql  
SELECT o.*, c.* FROM dbo.[Customer] c INNER JOIN dbo.[Order] o ON c.CustomerID = o.CustomerID  
```  
  
 <span data-ttu-id="0ad24-131">此查询的估计的计划为：</span><span class="sxs-lookup"><span data-stu-id="0ad24-131">The estimated plan for this query is:</span></span>  
  
 <span data-ttu-id="0ad24-132">![哈希联接基于磁盘的表的查询计划。](../../database-engine/media/hekaton-query-plan-2.gif "哈希联接基于磁盘的表的查询计划。")</span><span class="sxs-lookup"><span data-stu-id="0ad24-132">![Query plan for a hash join of disk-based tables.](../../database-engine/media/hekaton-query-plan-2.gif "Query plan for a hash join of disk-based tables.")</span></span>  
<span data-ttu-id="0ad24-133">哈希联接基于磁盘的表的查询计划。</span><span class="sxs-lookup"><span data-stu-id="0ad24-133">Query plan for a hash join of disk-based tables.</span></span>  
  
 <span data-ttu-id="0ad24-134">在此查询中，Order 表的行是使用聚集索引检索的。</span><span class="sxs-lookup"><span data-stu-id="0ad24-134">In this query, rows from the Order table are retrieved using the clustered index.</span></span> <span data-ttu-id="0ad24-135">`Hash Match` 物理运算符现在用于 `Inner Join`。</span><span class="sxs-lookup"><span data-stu-id="0ad24-135">The `Hash Match` physical operator is now used for the `Inner Join`.</span></span> <span data-ttu-id="0ad24-136">Order 的聚集索引不是按 CustomerID 排序的，因此 `Merge Join` 需要一个排序运算符，这会影响性能。</span><span class="sxs-lookup"><span data-stu-id="0ad24-136">The clustered index on Order is not sorted on CustomerID, and so a `Merge Join` would require a sort operator, which would affect performance.</span></span> <span data-ttu-id="0ad24-137">请注意 `Hash Match` 运算符的相对开销 (75%) 和上一示例中 `Merge Join` 运算符的开销 (46%)。</span><span class="sxs-lookup"><span data-stu-id="0ad24-137">Note the relative cost of the `Hash Match` operator (75%) compared with the cost of the `Merge Join` operator in the previous example (46%).</span></span> <span data-ttu-id="0ad24-138">优化器在上一示例中也考虑了 `Hash Match` 运算符，但结论是 `Merge Join` 运算符可以提供更好的性能。</span><span class="sxs-lookup"><span data-stu-id="0ad24-138">The optimizer would have considered the `Hash Match` operator also in the previous example, but concluded that the `Merge Join` operator gave better performance.</span></span>  
  
## <a name="ssnoversion-query-processing-for-disk-based-tables"></a>[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="0ad24-139">基于磁盘的表的查询处理</span><span class="sxs-lookup"><span data-stu-id="0ad24-139">Query Processing for Disk-Based Tables</span></span>  
 <span data-ttu-id="0ad24-140">下图显示 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中针对即席查询的查询处理流程：</span><span class="sxs-lookup"><span data-stu-id="0ad24-140">The following diagram outlines the query processing flow in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] for ad hoc queries:</span></span>  
  
 <span data-ttu-id="0ad24-141">![SQL Server 查询处理管道。](../../database-engine/media/hekaton-query-plan-3.gif "SQL Server 查询处理管道。")</span><span class="sxs-lookup"><span data-stu-id="0ad24-141">![SQL Server query processing pipeline.](../../database-engine/media/hekaton-query-plan-3.gif "SQL Server query processing pipeline.")</span></span>  
<span data-ttu-id="0ad24-142">SQL Server 查询处理管道。</span><span class="sxs-lookup"><span data-stu-id="0ad24-142">SQL Server query processing pipeline.</span></span>  
  
 <span data-ttu-id="0ad24-143">在本方案中：</span><span class="sxs-lookup"><span data-stu-id="0ad24-143">In this scenario:</span></span>  
  
1.  <span data-ttu-id="0ad24-144">用户发出查询。</span><span class="sxs-lookup"><span data-stu-id="0ad24-144">The user issues a query.</span></span>  
  
2.  <span data-ttu-id="0ad24-145">分析器和 algebrizer 根据用户提交的 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 文本采用逻辑运算符构造查询树。</span><span class="sxs-lookup"><span data-stu-id="0ad24-145">The parser and algebrizer construct a query tree with logical operators based on the [!INCLUDE[tsql](../../../includes/tsql-md.md)] text submitted by the user.</span></span>  
  
3.  <span data-ttu-id="0ad24-146">优化器创建一个包含物理运算符的查询优化计划（例如，嵌套循环联接）。</span><span class="sxs-lookup"><span data-stu-id="0ad24-146">The optimizer creates an optimized query plan containing physical operators (for example, nested-loops join).</span></span> <span data-ttu-id="0ad24-147">优化后，该计划存储在计划高速缓存中。</span><span class="sxs-lookup"><span data-stu-id="0ad24-147">After optimization, the plan may be stored in the plan cache.</span></span> <span data-ttu-id="0ad24-148">如果计划高速缓存中已经包含针对此查询的计划，则跳过此步骤。</span><span class="sxs-lookup"><span data-stu-id="0ad24-148">This step is bypassed if the plan cache already contains a plan for this query.</span></span>  
  
4.  <span data-ttu-id="0ad24-149">查询执行引擎处理查询计划的解释。</span><span class="sxs-lookup"><span data-stu-id="0ad24-149">The query execution engine processes an interpretation of the query plan.</span></span>  
  
5.  <span data-ttu-id="0ad24-150">对于每个索引查找、索引扫描和表扫描运算符，执行引擎都会从 Access Methods 请求来自相应索引和表结构的行。</span><span class="sxs-lookup"><span data-stu-id="0ad24-150">For each index seek, index scan, and table scan operator, the execution engine requests rows from the respective index and table structures from Access Methods.</span></span>  
  
6.  <span data-ttu-id="0ad24-151">Access Methods 根据需要从缓冲池中的索引和数据页检索行并将页面从磁盘加载到缓冲池。</span><span class="sxs-lookup"><span data-stu-id="0ad24-151">Access Methods retrieves the rows from the index and data pages in the buffer pool and loads pages from disk into the buffer pool as needed.</span></span>  
  
 <span data-ttu-id="0ad24-152">对于第一个示例查询，执行引擎从 Access Methods 请求 Customer 聚集索引中的行和 Order 非聚集索引中的行。</span><span class="sxs-lookup"><span data-stu-id="0ad24-152">For the first example query, the execution engine requests rows in the clustered index on Customer and the nonclustered index on Order from Access Methods.</span></span> <span data-ttu-id="0ad24-153">Access Methods 遍历 B 树索引结构以检索请求的行。</span><span class="sxs-lookup"><span data-stu-id="0ad24-153">Access Methods traverses the B-tree index structures to retrieve the requested rows.</span></span> <span data-ttu-id="0ad24-154">在本例中检索所有行，因为计划需要全部索引扫描。</span><span class="sxs-lookup"><span data-stu-id="0ad24-154">In this case all rows are retrieved as the plan calls for full index scans.</span></span>  
  
## <a name="interpreted-tsql-access-to-memory-optimized-tables"></a><span data-ttu-id="0ad24-155">使用解释型 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 访问内存优化表</span><span class="sxs-lookup"><span data-stu-id="0ad24-155">Interpreted [!INCLUDE[tsql](../../../includes/tsql-md.md)] Access to Memory-Optimized Tables</span></span>  
 [!INCLUDE[tsql](../../../includes/tsql-md.md)] <span data-ttu-id="0ad24-156">即席批处理和存储过程也称为解释型 [!INCLUDE[tsql](../../../includes/tsql-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0ad24-156">ad hoc batches and stored procedures are also referred to as interpreted [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="0ad24-157">解释型是指这样一个事实，即对于查询计划中的每个运算符，查询计划都由查询执行引擎进行解释。</span><span class="sxs-lookup"><span data-stu-id="0ad24-157">Interpreted refers to the fact that the query plan is interpreted by the query execution engine for each operator in the query plan.</span></span> <span data-ttu-id="0ad24-158">执行引擎读取运算符及其参数并执行运算。</span><span class="sxs-lookup"><span data-stu-id="0ad24-158">The execution engine reads the operator and its parameters and performs the operation.</span></span>  
  
 <span data-ttu-id="0ad24-159">解释型 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 可用于访问内存优化表和基于磁盘的表。</span><span class="sxs-lookup"><span data-stu-id="0ad24-159">Interpreted [!INCLUDE[tsql](../../../includes/tsql-md.md)] can be used to access both memory-optimized and disk-based tables.</span></span> <span data-ttu-id="0ad24-160">下图举例说明对解释型 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 访问内存优化表的查询处理：</span><span class="sxs-lookup"><span data-stu-id="0ad24-160">The following figure illustrates query processing for interpreted [!INCLUDE[tsql](../../../includes/tsql-md.md)] access to memory-optimized tables:</span></span>  
  
 <span data-ttu-id="0ad24-161">![用于解释型 tsql 的查询处理管道。](../../database-engine/media/hekaton-query-plan-4.gif "用于解释型 tsql 的查询处理管道。")</span><span class="sxs-lookup"><span data-stu-id="0ad24-161">![Query processing pipeline for interpreted tsql.](../../database-engine/media/hekaton-query-plan-4.gif "Query processing pipeline for interpreted tsql.")</span></span>  
<span data-ttu-id="0ad24-162">有关解释型 Transact-SQL 访问内存优化表的查询处理管道。</span><span class="sxs-lookup"><span data-stu-id="0ad24-162">Query processing pipeline for interpreted Transact-SQL access to memory-optimized tables.</span></span>  
  
 <span data-ttu-id="0ad24-163">如图所示，查询处理管道基本保持不变：</span><span class="sxs-lookup"><span data-stu-id="0ad24-163">As illustrated by the figure, the query processing pipeline remains mostly unchanged:</span></span>  
  
-   <span data-ttu-id="0ad24-164">分析器和 algebrizer 构造查询树。</span><span class="sxs-lookup"><span data-stu-id="0ad24-164">The parser and algebrizer construct the query tree.</span></span>  
  
-   <span data-ttu-id="0ad24-165">优化器创建执行计划。</span><span class="sxs-lookup"><span data-stu-id="0ad24-165">The optimizer creates the execution plan.</span></span>  
  
-   <span data-ttu-id="0ad24-166">查询执行引擎解释执行计划。</span><span class="sxs-lookup"><span data-stu-id="0ad24-166">The query execution engine interprets the execution plan.</span></span>  
  
 <span data-ttu-id="0ad24-167">与传统查询处理管道（图 2）的主要不同之处在于并非使用访问方法从缓冲池检索内存优化表的行。</span><span class="sxs-lookup"><span data-stu-id="0ad24-167">The main difference with the traditional query processing pipeline (figure 2) is that rows for memory-optimized tables are not retrieved from the buffer pool using Access Methods.</span></span> <span data-ttu-id="0ad24-168">而是通过内存中 OLTP 引擎从内存中数据结构检索行。</span><span class="sxs-lookup"><span data-stu-id="0ad24-168">Instead, rows are retrieved from the in-memory data structures through the In-Memory OLTP engine.</span></span> <span data-ttu-id="0ad24-169">数据结构上的差异导致优化器在某些情况下选取不同的计划，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="0ad24-169">Differences in data structures cause the optimizer to pick different plans in some cases, as illustrated by the following example.</span></span>  
  
 <span data-ttu-id="0ad24-170">下面的 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 脚本包含 Order 和 Customer 表的内存优化版本，其中使用哈希索引：</span><span class="sxs-lookup"><span data-stu-id="0ad24-170">The following [!INCLUDE[tsql](../../../includes/tsql-md.md)] script contains memory-optimized versions of the Order and Customer tables, using hash indexes:</span></span>  
  
```sql  
CREATE TABLE dbo.[Customer] (  
  CustomerID nchar (5) NOT NULL PRIMARY KEY NONCLUSTERED,  
  ContactName nvarchar (30) NOT NULL   
) WITH (MEMORY_OPTIMIZED=ON)  
GO  
  
CREATE TABLE dbo.[Order] (  
  OrderID int NOT NULL PRIMARY KEY NONCLUSTERED,  
  CustomerID nchar (5) NOT NULL INDEX IX_CustomerID HASH(CustomerID) WITH (BUCKET_COUNT=100000),  
  OrderDate date NOT NULL INDEX IX_OrderDate HASH(OrderDate) WITH (BUCKET_COUNT=100000)  
) WITH (MEMORY_OPTIMIZED=ON)  
GO  
```  
  
 <span data-ttu-id="0ad24-171">考虑对内存优化表执行相同的查询：</span><span class="sxs-lookup"><span data-stu-id="0ad24-171">Consider the same query executed on memory-optimized tables:</span></span>  
  
```sql  
SELECT o.OrderID, c.* FROM dbo.[Customer] c INNER JOIN dbo.[Order] o ON c.CustomerID = o.CustomerID  
```  
  
 <span data-ttu-id="0ad24-172">估计的计划如下：</span><span class="sxs-lookup"><span data-stu-id="0ad24-172">The estimated plan is as follows:</span></span>  
  
 <span data-ttu-id="0ad24-173">![用于联接内存优化表的查询计划。](../../database-engine/media/hekaton-query-plan-5.gif "用于联接内存优化表的查询计划。")</span><span class="sxs-lookup"><span data-stu-id="0ad24-173">![Query plan for join of memory optimized tables.](../../database-engine/media/hekaton-query-plan-5.gif "Query plan for join of memory optimized tables.")</span></span>  
<span data-ttu-id="0ad24-174">用于联接内存优化表的查询计划。</span><span class="sxs-lookup"><span data-stu-id="0ad24-174">Query plan for join of memory-optimized tables.</span></span>  
  
 <span data-ttu-id="0ad24-175">观察该计划与基于磁盘的表的相同查询计划（图 1）的以下不同：</span><span class="sxs-lookup"><span data-stu-id="0ad24-175">Observe the following differences with the plan for the same query on disk-based tables (figure 1):</span></span>  
  
-   <span data-ttu-id="0ad24-176">此计划包含针对 Customer 表的表扫描，而不是聚集索引扫描：</span><span class="sxs-lookup"><span data-stu-id="0ad24-176">This plan contains a table scan rather than a clustered index scan for the table Customer:</span></span>  
  
    -   <span data-ttu-id="0ad24-177">表定义不包含聚集索引。</span><span class="sxs-lookup"><span data-stu-id="0ad24-177">The definition of the table does not contain a clustered index.</span></span>  
  
    -   <span data-ttu-id="0ad24-178">内存优化表不支持聚集索引。</span><span class="sxs-lookup"><span data-stu-id="0ad24-178">Clustered indexes are not supported with memory-optimized tables.</span></span> <span data-ttu-id="0ad24-179">相反，每个内存优化表必须至少有一个非聚集索引，因此内存优化表上的所有索引可高效访问表中的所有列，而不必将其存储在索引中或引用聚集索引。</span><span class="sxs-lookup"><span data-stu-id="0ad24-179">Instead, every memory-optimized table must have at least one nonclustered index and all indexes on memory-optimized tables can efficiently access all columns in the table without having to store them in the index or refer to a clustered index.</span></span>  
  
-   <span data-ttu-id="0ad24-180">此计划包含 `Hash Match` 而不是 `Merge Join`。</span><span class="sxs-lookup"><span data-stu-id="0ad24-180">This plan contains a `Hash Match` rather than a `Merge Join`.</span></span> <span data-ttu-id="0ad24-181">Order 和 Customer 表的索引均为哈希索引，因此没有顺序。</span><span class="sxs-lookup"><span data-stu-id="0ad24-181">The indexes on both the Order and the Customer table are hash indexes, and are thus not ordered.</span></span> <span data-ttu-id="0ad24-182">`Merge Join` 会要求排序运算符，这会降低性能。</span><span class="sxs-lookup"><span data-stu-id="0ad24-182">A `Merge Join` would require sort operators that would decrease performance.</span></span>  
  
## <a name="natively-compiled-stored-procedures"></a><span data-ttu-id="0ad24-183">本机编译的存储过程</span><span class="sxs-lookup"><span data-stu-id="0ad24-183">Natively Compiled Stored Procedures</span></span>  
 <span data-ttu-id="0ad24-184">本机编译存储过程是编译为机器代码的 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 存储过程，而不是由查询执行引擎解释。</span><span class="sxs-lookup"><span data-stu-id="0ad24-184">Natively compiled stored procedures are [!INCLUDE[tsql](../../../includes/tsql-md.md)] stored procedures compiled to machine code, rather than interpreted by the query execution engine.</span></span> <span data-ttu-id="0ad24-185">以下脚本创建一个本机编译存储过程来运行示例查询（来自“示例查询”部分）。</span><span class="sxs-lookup"><span data-stu-id="0ad24-185">The following script creates a natively compiled stored procedure that runs the example query (from the Example Query section).</span></span>  
  
```sql  
CREATE PROCEDURE usp_SampleJoin  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH   
(  TRANSACTION ISOLATION LEVEL = SNAPSHOT,  
  LANGUAGE = 'english')  
  
  SELECT o.OrderID, c.CustomerID, c.ContactName   
FROM dbo.[Order] o INNER JOIN dbo.[Customer] c   
  ON c.CustomerID = o.CustomerID  
  
END  
```  
  
 <span data-ttu-id="0ad24-186">本机编译存储过程在创建时编译，而解释型存储过程在首次执行时编译。</span><span class="sxs-lookup"><span data-stu-id="0ad24-186">Natively compiled stored procedures are compiled at create time, whereas interpreted stored procedures are compiled at first execution time.</span></span> <span data-ttu-id="0ad24-187">（部分编译（特别是分析和 algebrization）发生在创建时。</span><span class="sxs-lookup"><span data-stu-id="0ad24-187">(A portion of the compilation, particularly parsing and algebrization, take place at create.</span></span> <span data-ttu-id="0ad24-188">但是，对于解释型存储过程，将在首次执行时优化查询计划。）重新编译逻辑相似。</span><span class="sxs-lookup"><span data-stu-id="0ad24-188">However, for interpreted stored procedures, optimization of the query plans takes place at first execution.) The recompilation logic is similar.</span></span> <span data-ttu-id="0ad24-189">如果服务器已重新启动，本机编译的存储过程将在该过程首次执行时重新编译。</span><span class="sxs-lookup"><span data-stu-id="0ad24-189">Natively compiled stored procedures are recompiled on first execution of the procedure if the server is restarted.</span></span> <span data-ttu-id="0ad24-190">解释型存储过程在计划不再存在于计划高速缓存中时重新编译。</span><span class="sxs-lookup"><span data-stu-id="0ad24-190">Interpreted stored procedures are recompiled if the plan is no longer in the plan cache.</span></span> <span data-ttu-id="0ad24-191">下表对本机编译存储过程和解释型存储过程的编译和重新编译进行了总结：</span><span class="sxs-lookup"><span data-stu-id="0ad24-191">The following table summarizes compilation and recompilation cases for both natively compiled and interpreted stored procedures:</span></span>  
  
||<span data-ttu-id="0ad24-192">本机编译</span><span class="sxs-lookup"><span data-stu-id="0ad24-192">Natively compiled</span></span>|<span data-ttu-id="0ad24-193">使用解释型</span><span class="sxs-lookup"><span data-stu-id="0ad24-193">Interpreted</span></span>|  
|-|-----------------------|-----------------|  
|<span data-ttu-id="0ad24-194">初始编译</span><span class="sxs-lookup"><span data-stu-id="0ad24-194">Initial compilation</span></span>|<span data-ttu-id="0ad24-195">创建时。</span><span class="sxs-lookup"><span data-stu-id="0ad24-195">At create time.</span></span>|<span data-ttu-id="0ad24-196">首次执行时。</span><span class="sxs-lookup"><span data-stu-id="0ad24-196">At first execution.</span></span>|  
|<span data-ttu-id="0ad24-197">自动重新编译</span><span class="sxs-lookup"><span data-stu-id="0ad24-197">Automatic recompilation</span></span>|<span data-ttu-id="0ad24-198">在数据库或服务器重新启动后首次执行该过程时。</span><span class="sxs-lookup"><span data-stu-id="0ad24-198">Upon first execution of the procedure after a database or server restart.</span></span>|<span data-ttu-id="0ad24-199">服务器重新启动时。</span><span class="sxs-lookup"><span data-stu-id="0ad24-199">On server restart.</span></span> <span data-ttu-id="0ad24-200">或者从计划高速缓存中逐出时（通常是由于架构或状态更改，或者内存压力）。</span><span class="sxs-lookup"><span data-stu-id="0ad24-200">Or, eviction from the plan cache, usually based on schema or stats changes, or memory pressure.</span></span>|  
|<span data-ttu-id="0ad24-201">手动重新编译</span><span class="sxs-lookup"><span data-stu-id="0ad24-201">Manual recompilation</span></span>|<span data-ttu-id="0ad24-202">不支持。</span><span class="sxs-lookup"><span data-stu-id="0ad24-202">Not supported.</span></span> <span data-ttu-id="0ad24-203">解决方法是删除并重新创建存储过程。</span><span class="sxs-lookup"><span data-stu-id="0ad24-203">The workaround is to drop and recreate the stored procedure.</span></span>|<span data-ttu-id="0ad24-204">请使用 `sp_recompile`。</span><span class="sxs-lookup"><span data-stu-id="0ad24-204">Use `sp_recompile`.</span></span> <span data-ttu-id="0ad24-205">您可以手动将计划逐出高速缓存，例如通过 DBCC FREEPROCCACHE。</span><span class="sxs-lookup"><span data-stu-id="0ad24-205">You can manually evict the plan from the cache, for example through DBCC FREEPROCCACHE.</span></span> <span data-ttu-id="0ad24-206">也可以创建存储过程 WITH RECOMPILE，存储过程将在每次执行时重新编译。</span><span class="sxs-lookup"><span data-stu-id="0ad24-206">You can also create the stored procedure WITH RECOMPILE and the stored procedure will be recompiled at every execution.</span></span>|  
  
### <a name="compilation-and-query-processing"></a><span data-ttu-id="0ad24-207">编译和查询处理</span><span class="sxs-lookup"><span data-stu-id="0ad24-207">Compilation and Query Processing</span></span>  
 <span data-ttu-id="0ad24-208">下图说明本机编译存储过程的编译流程：</span><span class="sxs-lookup"><span data-stu-id="0ad24-208">The following diagram illustrates the compilation process for natively compiled stored procedures:</span></span>  
  
 <span data-ttu-id="0ad24-209">![存储过程的本机编译。](../../database-engine/media/hekaton-query-plan-6.gif "存储过程的本机编译。")</span><span class="sxs-lookup"><span data-stu-id="0ad24-209">![Native compilation of stored procedures.](../../database-engine/media/hekaton-query-plan-6.gif "Native compilation of stored procedures.")</span></span>  
<span data-ttu-id="0ad24-210">存储过程的本机编译。</span><span class="sxs-lookup"><span data-stu-id="0ad24-210">Native compilation of stored procedures.</span></span>  
  
 <span data-ttu-id="0ad24-211">该过程如下，</span><span class="sxs-lookup"><span data-stu-id="0ad24-211">The process is described as,</span></span>  
  
1.  <span data-ttu-id="0ad24-212">用户向 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 发出一条 `CREATE PROCEDURE` 语句。</span><span class="sxs-lookup"><span data-stu-id="0ad24-212">The user issues a `CREATE PROCEDURE` statement to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="0ad24-213">分析器和 algebrizer 为该过程创建处理流程，并为存储过程中的 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 查询创建查询树。</span><span class="sxs-lookup"><span data-stu-id="0ad24-213">The parser and algebrizer create the processing flow for the procedure, as well as query trees for the [!INCLUDE[tsql](../../../includes/tsql-md.md)] queries in the stored procedure.</span></span>  
  
3.  <span data-ttu-id="0ad24-214">优化器为存储过程中的所有查询创建优化的查询执行计划。</span><span class="sxs-lookup"><span data-stu-id="0ad24-214">The optimizer creates optimized query execution plans for all the queries in the stored procedure.</span></span>  
  
4.  <span data-ttu-id="0ad24-215">内存中 OLTP 编译器通过嵌入的优化查询计划接管处理流程，并生成一个 DLL，其中包含执行存储过程的机器代码。</span><span class="sxs-lookup"><span data-stu-id="0ad24-215">The In-Memory OLTP compiler takes the processing flow with the embedded optimized query plans and generates a DLL that contains the machine code for executing the stored procedure.</span></span>  
  
5.  <span data-ttu-id="0ad24-216">生成的 DLL 加载到内存中。</span><span class="sxs-lookup"><span data-stu-id="0ad24-216">The generated DLL is loaded into memory.</span></span>  
  
 <span data-ttu-id="0ad24-217">本机编译存储过程的调用转换为对 DLL 中函数的调用。</span><span class="sxs-lookup"><span data-stu-id="0ad24-217">Invocation of a natively compiled stored procedure translates to calling a function in the DLL.</span></span>  
  
 <span data-ttu-id="0ad24-218">![本机编译存储过程的执行。](../../database-engine/media/hekaton-query-plan-7.gif "本机编译存储过程的执行。")</span><span class="sxs-lookup"><span data-stu-id="0ad24-218">![Execution of natively compiled stored procedures.](../../database-engine/media/hekaton-query-plan-7.gif "Execution of natively compiled stored procedures.")</span></span>  
<span data-ttu-id="0ad24-219">本机编译存储过程的执行。</span><span class="sxs-lookup"><span data-stu-id="0ad24-219">Execution of natively compiled stored procedures.</span></span>  
  
 <span data-ttu-id="0ad24-220">本机编译存储过程的调用如下所述：</span><span class="sxs-lookup"><span data-stu-id="0ad24-220">Invocation of a natively compiled stored procedure is described as follows:</span></span>  
  
1.  <span data-ttu-id="0ad24-221">用户发出 `EXEC` *usp_myproc*语句。</span><span class="sxs-lookup"><span data-stu-id="0ad24-221">The user issues an `EXEC`*usp_myproc* statement.</span></span>  
  
2.  <span data-ttu-id="0ad24-222">分析器提取名称和存储过程参数。</span><span class="sxs-lookup"><span data-stu-id="0ad24-222">The parser extracts the name and stored procedure parameters.</span></span>  
  
     <span data-ttu-id="0ad24-223">如果语句已准备就绪（例如使用 `sp_prep_exec`），则分析器执行时不需要提取过程名称和参数。</span><span class="sxs-lookup"><span data-stu-id="0ad24-223">If the statement was prepared, for example using `sp_prep_exec`, the parser does not need to extract the procedure name and parameters at execution time.</span></span>  
  
3.  <span data-ttu-id="0ad24-224">内存中 OLTP 运行时查找存储过程的 DLL 入口点。</span><span class="sxs-lookup"><span data-stu-id="0ad24-224">The In-Memory OLTP runtime locates the DLL entry point for the stored procedure.</span></span>  
  
4.  <span data-ttu-id="0ad24-225">DLL 中的机器代码将执行，结果会返回到客户端。</span><span class="sxs-lookup"><span data-stu-id="0ad24-225">The machine code in the DLL is executed and the results of are returned to the client.</span></span>  
  
 <span data-ttu-id="0ad24-226">**参数截取**</span><span class="sxs-lookup"><span data-stu-id="0ad24-226">**Parameter sniffing**</span></span>  
  
 <span data-ttu-id="0ad24-227">解释型 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 存储过程在首次执行时编译，而本机编译存储过程在创建时编译。</span><span class="sxs-lookup"><span data-stu-id="0ad24-227">Interpreted [!INCLUDE[tsql](../../../includes/tsql-md.md)] stored procedures are compiled at first execution, in contrast to natively compiled stored procedures, which are compiled at create time.</span></span> <span data-ttu-id="0ad24-228">由于调用编译解释型存储过程时，优化器使用为此调用提供的参数值生成执行计划。</span><span class="sxs-lookup"><span data-stu-id="0ad24-228">When interpreted stored procedures are compiled at invocation, the values of the parameters supplied for this invocation are used by the optimizer when generating the execution plan.</span></span> <span data-ttu-id="0ad24-229">这种编译期间的参数用法称为参数截取。</span><span class="sxs-lookup"><span data-stu-id="0ad24-229">This use of parameters during compilation is called parameter sniffing.</span></span>  
  
 <span data-ttu-id="0ad24-230">参数截取不适用于编译本机编译存储过程。</span><span class="sxs-lookup"><span data-stu-id="0ad24-230">Parameter sniffing is not used for compiling natively compiled stored procedures.</span></span> <span data-ttu-id="0ad24-231">此类存储过程的所有参数都视为具有 UNKNOWN 值。</span><span class="sxs-lookup"><span data-stu-id="0ad24-231">All parameters to the stored procedure are considered to have UNKNOWN values.</span></span> <span data-ttu-id="0ad24-232">与解释型存储过程不同，本机编译存储过程还支持 `OPTIMIZE FOR` 提示。</span><span class="sxs-lookup"><span data-stu-id="0ad24-232">Like interpreted stored procedures, natively compiled stored procedures also support the `OPTIMIZE FOR` hint.</span></span> <span data-ttu-id="0ad24-233">有关详细信息，请参阅[查询提示 (Transact-SQL)](/sql/t-sql/queries/hints-transact-sql-query)。</span><span class="sxs-lookup"><span data-stu-id="0ad24-233">For more information, see [Query Hints &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-query).</span></span>  
  
### <a name="retrieving-a-query-execution-plan-for-natively-compiled-stored-procedures"></a><span data-ttu-id="0ad24-234">为本机编译存储过程检索查询执行计划</span><span class="sxs-lookup"><span data-stu-id="0ad24-234">Retrieving a Query Execution Plan for Natively Compiled Stored Procedures</span></span>  
 <span data-ttu-id="0ad24-235">可使用 **中的** 估计的执行计划 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]，或使用 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中的 SHOWPLAN_XML 选项，检索本机编译的存储过程的查询执行计划。</span><span class="sxs-lookup"><span data-stu-id="0ad24-235">The query execution plan for a natively compiled stored procedure can be retrieved using **Estimated Execution Plan** in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], or using the SHOWPLAN_XML option in [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="0ad24-236">例如：</span><span class="sxs-lookup"><span data-stu-id="0ad24-236">For example:</span></span>  
  
```sql  
SET SHOWPLAN_XML ON  
GO  
EXEC dbo.usp_myproc  
GO  
SET SHOWPLAN_XML OFF  
GO  
```  
  
 <span data-ttu-id="0ad24-237">查询优化器生成的执行计划由树组成，树的节点和叶是查询运算符。</span><span class="sxs-lookup"><span data-stu-id="0ad24-237">The execution plan generated by the query optimizer consists of a tree with query operators on the nodes and leaves of the tree.</span></span> <span data-ttu-id="0ad24-238">树的结构确定运算符之间的交互（行从一个运算符到另一个运算符的流动）。</span><span class="sxs-lookup"><span data-stu-id="0ad24-238">The structure of the tree determines the interaction (the flow of rows from one operator to another) between the operators.</span></span> <span data-ttu-id="0ad24-239">在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]图形视图中，是从右向左流动的。</span><span class="sxs-lookup"><span data-stu-id="0ad24-239">In the graphical view of [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], the flow is from right to left.</span></span> <span data-ttu-id="0ad24-240">例如，图 1 中的查询计划包含两个索引扫描运算符，它们向合并联接运算符提供行。</span><span class="sxs-lookup"><span data-stu-id="0ad24-240">For example, the query plan in figure 1 contains two index scan operators, which supplies rows to a merge join operator.</span></span> <span data-ttu-id="0ad24-241">合并联接运算符向选择运算符提供行。</span><span class="sxs-lookup"><span data-stu-id="0ad24-241">The merge join operator supplies rows to a select operator.</span></span> <span data-ttu-id="0ad24-242">最后，选择运算符将行返回客户端。</span><span class="sxs-lookup"><span data-stu-id="0ad24-242">The select operator, finally, returns the rows to the client.</span></span>  
  
### <a name="query-operators-in-natively-compiled-stored-procedures"></a><span data-ttu-id="0ad24-243">本机编译存储过程中的查询运算符</span><span class="sxs-lookup"><span data-stu-id="0ad24-243">Query Operators in Natively Compiled Stored Procedures</span></span>  
 <span data-ttu-id="0ad24-244">下表对本机编译存储过程中支持的查询运算符进行了总结：</span><span class="sxs-lookup"><span data-stu-id="0ad24-244">The following table summarizes the query operators supported inside natively compiled stored procedures:</span></span>  
  
|<span data-ttu-id="0ad24-245">操作员</span><span class="sxs-lookup"><span data-stu-id="0ad24-245">Operator</span></span>|<span data-ttu-id="0ad24-246">示例查询</span><span class="sxs-lookup"><span data-stu-id="0ad24-246">Sample query</span></span>|  
|--------------|------------------|  
|<span data-ttu-id="0ad24-247">SELECT</span><span class="sxs-lookup"><span data-stu-id="0ad24-247">SELECT</span></span>|`SELECT OrderID FROM dbo.[Order]`|  
|<span data-ttu-id="0ad24-248">INSERT</span><span class="sxs-lookup"><span data-stu-id="0ad24-248">INSERT</span></span>|`INSERT dbo.Customer VALUES ('abc', 'def')`|  
|<span data-ttu-id="0ad24-249">UPDATE</span><span class="sxs-lookup"><span data-stu-id="0ad24-249">UPDATE</span></span>|`UPDATE dbo.Customer SET ContactName='ghi' WHERE CustomerID='abc'`|  
|<span data-ttu-id="0ad24-250">DELETE</span><span class="sxs-lookup"><span data-stu-id="0ad24-250">DELETE</span></span>|`DELETE dbo.Customer WHERE CustomerID='abc'`|  
|<span data-ttu-id="0ad24-251">Compute Scalar</span><span class="sxs-lookup"><span data-stu-id="0ad24-251">Compute Scalar</span></span>|<span data-ttu-id="0ad24-252">此运算符用于内部函数和类型转换。</span><span class="sxs-lookup"><span data-stu-id="0ad24-252">This operator is used both for intrinsic functions and type conversions.</span></span> <span data-ttu-id="0ad24-253">不是所有函数和类型转换在本机编译存储过程中都受支持。</span><span class="sxs-lookup"><span data-stu-id="0ad24-253">Not all functions and type conversions are supported inside natively compiled stored procedures.</span></span><br /><br /> `SELECT OrderID+1 FROM dbo.[Order]`|  
|<span data-ttu-id="0ad24-254">Nested Loops Join</span><span class="sxs-lookup"><span data-stu-id="0ad24-254">Nested Loops Join</span></span>|<span data-ttu-id="0ad24-255">Nested Loops 是本机编译存储过程内唯一支持的联接运算符。</span><span class="sxs-lookup"><span data-stu-id="0ad24-255">Nested Loops is the only join operator supported in natively compiled stored procedures.</span></span> <span data-ttu-id="0ad24-256">所有包含联接的计划都将使用 Nested Loops 运算符，即使以解释型 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 执行的同一查询计划包含哈希或合并联接也是如此。</span><span class="sxs-lookup"><span data-stu-id="0ad24-256">All plans that contain joins will use the Nested Loops operator, even if the plan for same query executed as interpreted [!INCLUDE[tsql](../../../includes/tsql-md.md)] contains a hash or merge join.</span></span><br /><br /> `SELECT o.OrderID, c.CustomerID`  <br /> `FROM dbo.[Order] o INNER JOIN dbo.[Customer] c`|  
|<span data-ttu-id="0ad24-257">排序</span><span class="sxs-lookup"><span data-stu-id="0ad24-257">Sort</span></span>|`SELECT ContactName FROM dbo.Customer`  <br /> `ORDER BY ContactName`|  
|<span data-ttu-id="0ad24-258">TOP</span><span class="sxs-lookup"><span data-stu-id="0ad24-258">Top</span></span>|`SELECT TOP 10 ContactName FROM dbo.Customer`|  
|<span data-ttu-id="0ad24-259">Top-sort</span><span class="sxs-lookup"><span data-stu-id="0ad24-259">Top-sort</span></span>|<span data-ttu-id="0ad24-260">`TOP` 表达式（要返回的行的数量）不能超过 8,000 行。</span><span class="sxs-lookup"><span data-stu-id="0ad24-260">The `TOP` expression (the number of rows to be returned) cannot exceed 8,000 rows.</span></span> <span data-ttu-id="0ad24-261">如果查询中还有联接和聚合运算符，数量会更少。</span><span class="sxs-lookup"><span data-stu-id="0ad24-261">Fewer if there are also join and aggregation operators in the query.</span></span> <span data-ttu-id="0ad24-262">与基表的行数相比，联接和聚合通常可减少要排序的行数。</span><span class="sxs-lookup"><span data-stu-id="0ad24-262">Joins and aggregation do typically reduce the number of rows to be sorted, compared with the row count of the base tables.</span></span><br /><br /> `SELECT TOP 10 ContactName FROM dbo.Customer`  <br /> `ORDER BY ContactName`|  
|<span data-ttu-id="0ad24-263">Stream Aggregate</span><span class="sxs-lookup"><span data-stu-id="0ad24-263">Stream Aggregate</span></span>|<span data-ttu-id="0ad24-264">请注意，聚合不支持 Hash Match 运算符。</span><span class="sxs-lookup"><span data-stu-id="0ad24-264">Note that the Hash Match operator is not supported for aggregation.</span></span> <span data-ttu-id="0ad24-265">因此，本机编译存储过程中的所有聚合都使用 Stream Aggregate 运算符，即使解释型 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 中针对同一查询计划使用 Hash Match 运算符也是如此。</span><span class="sxs-lookup"><span data-stu-id="0ad24-265">Therefore, all aggregation in natively compiled stored procedures uses the Stream Aggregate operator, even if the plan for the same query in interpreted [!INCLUDE[tsql](../../../includes/tsql-md.md)] uses the Hash Match operator.</span></span><br /><br /> `SELECT count(CustomerID) FROM dbo.Customer`|  
  
## <a name="column-statistics-and-joins"></a><span data-ttu-id="0ad24-266">列统计信息和联接</span><span class="sxs-lookup"><span data-stu-id="0ad24-266">Column Statistics and Joins</span></span>  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="0ad24-267">在索引键列值中维护统计信息，以帮助估计特定操作的开销，如索引扫描和索引查找。</span><span class="sxs-lookup"><span data-stu-id="0ad24-267">maintains statistics on values in index key columns to help estimate the cost of certain operations, such as index scan and index seeks.</span></span> <span data-ttu-id="0ad24-268">（如果显式创建非索引键列，或者查询优化器在对于带谓词的查询提供的响应中创建非索引键列，则 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 也会对这些列创建统计信息。）开销估计的主要度量是一个运算符处理的行数。</span><span class="sxs-lookup"><span data-stu-id="0ad24-268">( [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] also creates statistics on non-index key columns if you explicitly create them or if the query optimizer creates them in response to a query with a predicate.) The main metric in cost estimation is the number of rows processed by a single operator.</span></span> <span data-ttu-id="0ad24-269">请注意，对于基于磁盘的表，某一特定运算符处理的页数对于开销估计非常重要。</span><span class="sxs-lookup"><span data-stu-id="0ad24-269">Note that for disk-based tables, the number of pages accessed by a particular operator is significant in cost estimation.</span></span> <span data-ttu-id="0ad24-270">但是，由于页数对于内存优化表并不重要（始终为零），因此本次讨论重点在于行数。</span><span class="sxs-lookup"><span data-stu-id="0ad24-270">However, as page count is not important for memory-optimized tables (it is always zero), this discussion focuses on row count.</span></span> <span data-ttu-id="0ad24-271">从计划中的索引查找和扫描运算符开始估计，然后扩展到包含其他运算符，如联接运算符。</span><span class="sxs-lookup"><span data-stu-id="0ad24-271">The estimation starts with the index seek and scan operators in the plan, and is then extended to include the other operators, like the join operator.</span></span> <span data-ttu-id="0ad24-272">对联接运算符要处理的行数的估计基于对基础索引、搜索和扫描运算符的估计。</span><span class="sxs-lookup"><span data-stu-id="0ad24-272">The estimated number of rows to be processed by a join operator is based on the estimation for the underlying index, seek, and scan operators.</span></span> <span data-ttu-id="0ad24-273">对于内存优化表的解释型 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 访问，您可以通过实际执行计划查看计划中运算符的估计行数和实际行计数之差。</span><span class="sxs-lookup"><span data-stu-id="0ad24-273">For interpreted [!INCLUDE[tsql](../../../includes/tsql-md.md)] access to memory-optimized tables, you can observe the actual execution plan to see the difference between the estimated and actual row counts for the operators in the plan.</span></span>  
  
 <span data-ttu-id="0ad24-274">对于图 1 中的示例，</span><span class="sxs-lookup"><span data-stu-id="0ad24-274">For the example in figure 1,</span></span>  
  
-   <span data-ttu-id="0ad24-275">对 Customer 的聚集索引扫描的估计行数为 91，实际为 91。</span><span class="sxs-lookup"><span data-stu-id="0ad24-275">The clustered index scan on Customer has estimated 91; actual 91.</span></span>  
  
-   <span data-ttu-id="0ad24-276">对 CustomerID 的非聚集索引扫描的估计行数为 830，实际为 830。</span><span class="sxs-lookup"><span data-stu-id="0ad24-276">The nonclustered index scan on CustomerID has estimated 830; actual 830.</span></span>  
  
-   <span data-ttu-id="0ad24-277">Merge Join 运算符的估计值为 815，实际为 830。</span><span class="sxs-lookup"><span data-stu-id="0ad24-277">The Merge Join operator has estimated 815; actual 830.</span></span>  
  
 <span data-ttu-id="0ad24-278">索引扫描的估计值非常准确。</span><span class="sxs-lookup"><span data-stu-id="0ad24-278">The estimates for the index scans are accurate.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="0ad24-279">维护基于磁盘的表的行计数。</span><span class="sxs-lookup"><span data-stu-id="0ad24-279">maintains the row count for disk-based tables.</span></span> <span data-ttu-id="0ad24-280">整个表和索引扫描的估计值始终很准确。</span><span class="sxs-lookup"><span data-stu-id="0ad24-280">Estimates for full table and index scans are always accurate.</span></span> <span data-ttu-id="0ad24-281">联接的估计值也相当准确。</span><span class="sxs-lookup"><span data-stu-id="0ad24-281">The estimate for the join is fairly accurate, too.</span></span>  
  
 <span data-ttu-id="0ad24-282">如果这些估计值更改，不同备选计划的开销考虑也会发生更改。</span><span class="sxs-lookup"><span data-stu-id="0ad24-282">If these estimates change, the cost considerations for different plan alternatives change as well.</span></span> <span data-ttu-id="0ad24-283">例如，如果联接的一端的估计行计数为 1 或几行，则使用嵌套循环联接开销较小。</span><span class="sxs-lookup"><span data-stu-id="0ad24-283">For example, if one of the sides of the join has an estimated row count of 1 or just a few rows, using a nested loops joins is less expensive.</span></span>  
  
 <span data-ttu-id="0ad24-284">下面是查询计划：</span><span class="sxs-lookup"><span data-stu-id="0ad24-284">The following is the plan for the query:</span></span>  
  
```  
SELECT o.OrderID, c.* FROM dbo.[Customer] c INNER JOIN dbo.[Order] o ON c.CustomerID = o.CustomerID  
```  
  
 <span data-ttu-id="0ad24-285">删除 Customer 表中一行外的所有行后：</span><span class="sxs-lookup"><span data-stu-id="0ad24-285">After deleting all rows but one in the table Customer:</span></span>  
  
 <span data-ttu-id="0ad24-286">![列统计信息和联接。](../../database-engine/media/hekaton-query-plan-9.gif "列统计信息和联接。")</span><span class="sxs-lookup"><span data-stu-id="0ad24-286">![Column statistics and joins.](../../database-engine/media/hekaton-query-plan-9.gif "Column statistics and joins.")</span></span>  
  
 <span data-ttu-id="0ad24-287">关于此查询计划：</span><span class="sxs-lookup"><span data-stu-id="0ad24-287">Regarding this query plan:</span></span>  
  
-   <span data-ttu-id="0ad24-288">用 Nested Loops 物理联接运算符替换了 Hash Match。</span><span class="sxs-lookup"><span data-stu-id="0ad24-288">The Hash Match has been replaced with a Nested Loops physical join operator.</span></span>  
  
-   <span data-ttu-id="0ad24-289">用索引查找替换了对 IX_CustomerID 的全文检索扫描。</span><span class="sxs-lookup"><span data-stu-id="0ad24-289">The full index scan on IX_CustomerID has been replaced with an index seek.</span></span> <span data-ttu-id="0ad24-290">这样只需扫描 5 行，而全文检索扫描需要扫描 830 行。</span><span class="sxs-lookup"><span data-stu-id="0ad24-290">This resulted in scanning 5 rows, instead of the 830 rows required for the full index scan.</span></span>  
  
### <a name="statistics-and-cardinality-for-memory-optimized-tables"></a><span data-ttu-id="0ad24-291">内存优化表的统计信息和基数</span><span class="sxs-lookup"><span data-stu-id="0ad24-291">Statistics and Cardinality for Memory-Optimized Tables</span></span>  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="0ad24-292">保留内存优化表的列级统计信息。</span><span class="sxs-lookup"><span data-stu-id="0ad24-292">maintains column-level statistics for memory-optimized tables.</span></span> <span data-ttu-id="0ad24-293">此外，它还保留表的实际行数。</span><span class="sxs-lookup"><span data-stu-id="0ad24-293">In addition, it maintains the actual row count of the table.</span></span> <span data-ttu-id="0ad24-294">但是，与基于磁盘的表相比，它并不自动更新内存优化表的统计信息。</span><span class="sxs-lookup"><span data-stu-id="0ad24-294">However, in contrast to disk-based tables, the statistics for memory-optimized tables are not automatically updated.</span></span> <span data-ttu-id="0ad24-295">因此，在表中进行重大更改之后需要手动更新统计信息。</span><span class="sxs-lookup"><span data-stu-id="0ad24-295">Therefore, statistics need to be manually updated after significant changes in the tables.</span></span> <span data-ttu-id="0ad24-296">有关详细信息，请参阅 [内存优化表的统计信息](memory-optimized-tables.md)。</span><span class="sxs-lookup"><span data-stu-id="0ad24-296">For more information, see [Statistics for Memory-Optimized Tables](memory-optimized-tables.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ad24-297">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0ad24-297">See Also</span></span>  
 [<span data-ttu-id="0ad24-298">Memory-Optimized Tables</span><span class="sxs-lookup"><span data-stu-id="0ad24-298">Memory-Optimized Tables</span></span>](memory-optimized-tables.md)  
  
  
