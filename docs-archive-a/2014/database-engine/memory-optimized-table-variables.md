---
title: 内存优化表变量 |Microsoft Docs
ms.custom: ''
ms.date: 07/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: bd102e95-53e2-4da6-9b8b-0e4f02d286d3
author: stevestein
ms.author: sstein
ms.openlocfilehash: bec720c53c257240ee92274a6391ebc3f17faa25
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587578"
---
# <a name="memory-optimized-table-variables"></a><span data-ttu-id="36b74-102">内存优化表变量</span><span class="sxs-lookup"><span data-stu-id="36b74-102">Memory-Optimized Table Variables</span></span>
  <span data-ttu-id="36b74-103">除了内存优化表（用于高效的数据访问）和本机编译的存储过程（用于高效的查询处理和业务逻辑执行）之外，[!INCLUDE[hek_2](../includes/hek-2-md.md)] 还引入了第三种对象：内存优化表类型。</span><span class="sxs-lookup"><span data-stu-id="36b74-103">In addition to memory-optimized tables (for efficient data access) and natively compiled stored procedures (for efficient query processing and business logic execution) [!INCLUDE[hek_2](../includes/hek-2-md.md)] introduces a third kind of object: the memory-optimized table type.</span></span> <span data-ttu-id="36b74-104">使用内存优化表类型创建的表变量是内存优化表变量。</span><span class="sxs-lookup"><span data-stu-id="36b74-104">A table variable created using a memory-optimized table type is a memory-optimized table variable.</span></span>  
  
 <span data-ttu-id="36b74-105">与基于磁盘的表变量相比，内存优化表变量提供以下好处：</span><span class="sxs-lookup"><span data-stu-id="36b74-105">Memory-optimized table variables offer the following advantages when compared to disk-based table variables:</span></span>  
  
-   <span data-ttu-id="36b74-106">变量仅存储于内存中。</span><span class="sxs-lookup"><span data-stu-id="36b74-106">The variables are only stored in memory.</span></span> <span data-ttu-id="36b74-107">数据访问更高效，因为内存优化表类型将相同的内存优化算法和数据结构用于内存优化表，特别是在本机编译的存储过程中使用变量时。</span><span class="sxs-lookup"><span data-stu-id="36b74-107">Data access is more efficient because memory-optimized table type use the same memory-optimized algorithm and data structures used for memory-optimized tables, especially when the variables are used in natively compiled stored procedures.</span></span>  
  
-   <span data-ttu-id="36b74-108">对于内存优化表变量，不会占用 tempdb。</span><span class="sxs-lookup"><span data-stu-id="36b74-108">With memory-optimized table variables, there is no tempdb utilization.</span></span> <span data-ttu-id="36b74-109">表变量存储于 tempdb 中，并且不会使用 tempdb 中的任何资源。</span><span class="sxs-lookup"><span data-stu-id="36b74-109">Table variables are not stored in tempdb and do not use any resources in tempdb.</span></span>  
  
 <span data-ttu-id="36b74-110">下面是内存优化表变量的典型使用方案：</span><span class="sxs-lookup"><span data-stu-id="36b74-110">The typical usage scenarios for memory-optimized table variables are:</span></span>  
  
-   <span data-ttu-id="36b74-111">基于本机编译的存储过程中的多个查询，存储临时结果和创建单个结果集。</span><span class="sxs-lookup"><span data-stu-id="36b74-111">Storing intermediate results and creating single result sets based on multiple queries in natively compiled stored procedures.</span></span>  
  
-   <span data-ttu-id="36b74-112">将表值参数传递到本机编译的存储过程和解释型存储过程中。</span><span class="sxs-lookup"><span data-stu-id="36b74-112">Passing table-valued parameters into natively compiled stored procedures and interpreted stored procedures.</span></span>  
  
-   <span data-ttu-id="36b74-113">代替基于磁盘的表变量，并且在某些情况下代替对于存储过程而言是本地的 #temp 表。</span><span class="sxs-lookup"><span data-stu-id="36b74-113">Replacing disk-based table variables, and in some cases #temp tables that are local to a stored procedure.</span></span> <span data-ttu-id="36b74-114">这在系统中有许多 tempdb 争用的情况下特别有用。</span><span class="sxs-lookup"><span data-stu-id="36b74-114">This is particularly useful if there is a lot of tempdb contention in the system.</span></span>  
  
-   <span data-ttu-id="36b74-115">表变量可以用于模拟本机编译的存储过程中的游标，从而可帮助您解决本机编译的存储过程中的外围应用限制。</span><span class="sxs-lookup"><span data-stu-id="36b74-115">Table variables can be used to simulate cursors in natively compiled stored procedures, which can help you work around surface area limitations in natively compiled stored procedures.</span></span>  
  
 <span data-ttu-id="36b74-116">与内存优化表相似， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 为每个内存优化表类型都生成一个 DLL。</span><span class="sxs-lookup"><span data-stu-id="36b74-116">Like memory-optimized tables, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] generates a DLL for each memory-optimized table type.</span></span> <span data-ttu-id="36b74-117"> (编译在创建内存优化表类型时调用，而不是在用于创建内存优化表变量时调用。 ) 此 DLL 包括用于访问索引和从表变量检索数据的函数。</span><span class="sxs-lookup"><span data-stu-id="36b74-117">(Compilation is invoked when the memory-optimized table type is created and not when used to create memory-optimized table variables.) This DLL includes the functions for accessing indexes and retrieving data from the table variables.</span></span> <span data-ttu-id="36b74-118">当基于表类型声明一个内存优化表变量时，将在用户会话中创建与该表类型相对应的表和索引结构的实例。</span><span class="sxs-lookup"><span data-stu-id="36b74-118">When a memory-optimized table variable is declared based on the table type, an instance of the table and index structures corresponding to the table type is created in the user session.</span></span> <span data-ttu-id="36b74-119">然后，可采用与使用基于磁盘的表变量相同的方式使用该表变量。</span><span class="sxs-lookup"><span data-stu-id="36b74-119">The table variable can then be used in the same way as disk-based table variables.</span></span> <span data-ttu-id="36b74-120">您可以在表变量中插入、更新和删除行，并且可以在 [!INCLUDE[tsql](../includes/tsql-md.md)] 查询中使用变量。</span><span class="sxs-lookup"><span data-stu-id="36b74-120">You can insert, update, and delete rows in the table variable, and you can use the variables in [!INCLUDE[tsql](../includes/tsql-md.md)] queries.</span></span> <span data-ttu-id="36b74-121">还可以像表值参数 (TVP) 一样，将变量传递到本机编译的存储过程和解释型存储过程中。</span><span class="sxs-lookup"><span data-stu-id="36b74-121">You can also pass the variables into natively compiled and interpreted stored procedures, as table-valued parameters (TVP).</span></span>  
  
 <span data-ttu-id="36b74-122">以下示例显示了基于 AdventureWorks 的内存中 OLTP 示例 ([SQL Server 2014 内存中 Oltp 示例](https://msftdbprodsamples.codeplex.com/releases/view/114491)) 的内存优化表类型。</span><span class="sxs-lookup"><span data-stu-id="36b74-122">The following sample shows a memory-optimized table type from the AdventureWorks-based In-Memory OLTP sample ([SQL Server 2014 In-Memory OLTP Sample](https://msftdbprodsamples.codeplex.com/releases/view/114491)).</span></span>  
  
```sql
CREATE TYPE Sales.SalesOrderDetailType_inmem
   AS TABLE
(
   OrderQty         smallint   NOT NULL,
   ProductID        int        NOT NULL,

   SpecialOfferID   int        NOT NULL
      INDEX  IX_SpecialOfferID  NONCLUSTERED,

   LocalID          int        NOT NULL,

   INDEX IX_ProductID HASH (ProductID)
      WITH ( BUCKET_COUNT = 8 )
)
WITH ( MEMORY_OPTIMIZED = ON );
```  
  
 <span data-ttu-id="36b74-123">该示例表明，内存优化的表类型的语法与基于磁盘的表类型相似，但具有以下不同：</span><span class="sxs-lookup"><span data-stu-id="36b74-123">The sample shows that the syntax of memory-optimized table types is similar to disk-based table types, with the following exceptions:</span></span>  
  
-   <span data-ttu-id="36b74-124">`MEMORY_OPTIMIZED=ON` 指示表类型是内存优化表。</span><span class="sxs-lookup"><span data-stu-id="36b74-124">`MEMORY_OPTIMIZED=ON` indicates that the table type is memory-optimized.</span></span>  
  
-   <span data-ttu-id="36b74-125">该类型必须有至少一个索引。</span><span class="sxs-lookup"><span data-stu-id="36b74-125">The type must have at least one index.</span></span> <span data-ttu-id="36b74-126">与内存优化表一样，可以使用哈希索引和非聚集索引。</span><span class="sxs-lookup"><span data-stu-id="36b74-126">As with memory-optimized tables, you can use hash and nonclustered indexes.</span></span>  
  
     <span data-ttu-id="36b74-127">对于哈希索引，Bucket 计数应该是预期唯一索引键数目的一倍到两倍。</span><span class="sxs-lookup"><span data-stu-id="36b74-127">For a hash index, the bucket count should be about one to two times the number of expected unique index keys.</span></span> <span data-ttu-id="36b74-128">有关详细信息，请参阅 [Determining the Correct Bucket Count for Hash Indexes](../relational-databases/indexes/indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="36b74-128">For more information, see [Determining the Correct Bucket Count for Hash Indexes](../relational-databases/indexes/indexes.md).</span></span>  
  
-   <span data-ttu-id="36b74-129">针对内存优化表的数据类型和约束限制也适用于内存优化表类型。</span><span class="sxs-lookup"><span data-stu-id="36b74-129">The data type and constraint restrictions on memory-optimized tables also apply to memory-optimized table types.</span></span> <span data-ttu-id="36b74-130">例如，在 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] 中支持默认约束，但不支持 CHECK 约束。</span><span class="sxs-lookup"><span data-stu-id="36b74-130">For example, in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] default constraints are supported, but check constraints are not.</span></span>  
  
 <span data-ttu-id="36b74-131">与内存优化表相似，内存优化表变量</span><span class="sxs-lookup"><span data-stu-id="36b74-131">Like memory-optimized tables, memory-optimized table variables,</span></span>  
  
-   <span data-ttu-id="36b74-132">不支持并行计划。</span><span class="sxs-lookup"><span data-stu-id="36b74-132">Do not support parallel plans.</span></span>  
  
-   <span data-ttu-id="36b74-133">必须可容纳于内存中，并且不使用磁盘资源。</span><span class="sxs-lookup"><span data-stu-id="36b74-133">Must fit in memory and do not use disk resources.</span></span>  
  
 <span data-ttu-id="36b74-134">基于磁盘的表变量存在于 tempdb 中。</span><span class="sxs-lookup"><span data-stu-id="36b74-134">Disk-based table variables exist in tempdb.</span></span> <span data-ttu-id="36b74-135">内存优化表变量存在于用户数据库中（但它们不占用存储空间并且不恢复）。</span><span class="sxs-lookup"><span data-stu-id="36b74-135">Memory-optimized table variables exist in the user database (but they do not consume storage and are not recovered).</span></span>  
  
 <span data-ttu-id="36b74-136">无法使用内联语法创建内存优化表。</span><span class="sxs-lookup"><span data-stu-id="36b74-136">You cannot create a memory-optimized table variable using in-line syntax.</span></span> <span data-ttu-id="36b74-137">与基于磁盘的表变量不同，您必须首先创建一个类型。</span><span class="sxs-lookup"><span data-stu-id="36b74-137">Unlike disk-based table variables, you must create a type first.</span></span>  
  
## <a name="table-valued-parameters"></a><span data-ttu-id="36b74-138">表值参数</span><span class="sxs-lookup"><span data-stu-id="36b74-138">Table-Valued Parameters</span></span>  
 <span data-ttu-id="36b74-139">下面的示例脚本显示如何将表变量声明为内存优化表类型 `Sales.SalesOrderDetailType_inmem`、将三行插入到该变量中以及将变量以 TVP 的形式传递到 `Sales.usp_InsertSalesOrder_inmem` 中。</span><span class="sxs-lookup"><span data-stu-id="36b74-139">The following sample script shows the declaration of a table variable as the memory-optimized table type `Sales.SalesOrderDetailType_inmem`, the insert of three rows into the variable, and passing the variable as a TVP into `Sales.usp_InsertSalesOrder_inmem`.</span></span>  
  
```sql  
DECLARE @od Sales.SalesOrderDetailType_inmem,  
  @SalesOrderID uniqueidentifier,  
  @DueDate datetime2 = SYSDATETIME()  
  
INSERT @od (LocalID, ProductID, OrderQty, SpecialOfferID) VALUES  
  (1, 888, 2, 1),  
  (2, 450, 13, 1),  
  (3, 841, 1, 1)  
  
EXEC Sales.usp_InsertSalesOrder_inmem  
  @SalesOrderID = @SalesOrderID,  
  @DueDate = @DueDate,  
 @OnlineOrderFlag = 1,  
  @SalesOrderDetails = @od  
```  
  
 <span data-ttu-id="36b74-140">内存优化表类型可用作针对存储过程表值参数 (TVP) 的类型，并且可与基于磁盘的表类型和 TVP 完全相同地由客户端引用。</span><span class="sxs-lookup"><span data-stu-id="36b74-140">Memory-optimized table types can be used as the type for stored procedure table-valued parameters (TVPs) and can be referenced by clients exactly the same as disk-based table types and TVPs.</span></span> <span data-ttu-id="36b74-141">因此，使用内存优化的 TVP 调用存储过程以及本机编译的存储过程在工作方式上与使用基于磁盘 TVP 调用解释型存储过程完全相同。</span><span class="sxs-lookup"><span data-stu-id="36b74-141">Therefore, the invocation of stored procedures with memory-optimized TVPs, and natively compiled stored procedures works exactly the same as the invocation of interpreted stored procedures with disk-based TVPs.</span></span>  
  
## <a name="temp-table-replacement"></a><span data-ttu-id="36b74-142">#temp 表替换</span><span class="sxs-lookup"><span data-stu-id="36b74-142">#temp Table Replacement</span></span>  
 <span data-ttu-id="36b74-143">下面的示例显示内存优化表类型和表变量，用来代替对于存储过程而言处于本地的 #temp 表。</span><span class="sxs-lookup"><span data-stu-id="36b74-143">The following sample shows memory-optimized table types and table variables as a replacement for #temp tables that are local to a stored procedure.</span></span>  
  
```sql  
-- Using SQL procedure and temp table  
CREATE TABLE #tempTable (c INT NOT NULL PRIMARY KEY NONCLUSTERED)  
  
CREATE PROCEDURE sqlProc  
AS  
BEGIN  
  TRUNCATE TABLE #tempTable  
  
  INSERT #tempTable VALUES (1)  
  INSERT #tempTable VALUES (2)  
  INSERT #tempTable VALUES (3)  
  SELECT * FROM #tempTable  
END  
GO  
  
-- Using natively compiled stored procedure and table variable  
CREATE TYPE TT AS TABLE (c INT NOT NULL PRIMARY KEY NONCLUSTERED)  
GO  
  
CREATE PROCEDURE NCSPProc  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS  
BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
  DECLARE @tableVariable TT  
  INSERT @tableVariable VALUES (1)  
  INSERT @tableVariable VALUES (2)  
  INSERT @tableVariable VALUES (3)  
  SELECT c FROM @tableVariable  
END  
GO  
```  
  
## <a name="creating-a-single-result-set"></a><span data-ttu-id="36b74-144">创建单个结果集</span><span class="sxs-lookup"><span data-stu-id="36b74-144">Creating a Single Result Set</span></span>  
 <span data-ttu-id="36b74-145">下面的示例显示如何基于本机编译的存储过程中的多个查询，存储临时结果和创建单个结果集。</span><span class="sxs-lookup"><span data-stu-id="36b74-145">The following sample shows how to store intermediate results and create single result sets based on multiple queries in natively compiled stored procedures.</span></span> <span data-ttu-id="36b74-146">该示例计算并集 `SELECT c1 FROM dbo.t1 UNION SELECT c1 FROM dbo.t2`。</span><span class="sxs-lookup"><span data-stu-id="36b74-146">The sample is computing the union `SELECT c1 FROM dbo.t1 UNION SELECT c1 FROM dbo.t2`.</span></span>  
  
```sql  
CREATE DATABASE hk  
GO  
ALTER DATABASE hk ADD FILEGROUP hk_mod CONTAINS MEMORY_OPTIMIZED_DATA  
ALTER DATABASE hk ADD FILE( NAME = 'hk_mod' , FILENAME = 'c:\data\hk_mod') TO FILEGROUP hk_mod;  
  
USE hk  
GO  
  
CREATE TYPE tab1 AS TABLE (c1 INT NOT NULL, INDEX idx NONCLUSTERED(c1)) WITH (MEMORY_OPTIMIZED = ON)  
  
CREATE TABLE dbo.t1 (c1 INT NOT NULL, INDEX idx NONCLUSTERED(c1)) WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_ONLY)  
CREATE TABLE dbo.t2 (c1 INT NOT NULL, INDEX idx NONCLUSTERED(c1)) WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_ONLY)  
  
INSERT INTO dbo.t1 VALUES (1), (2)  
INSERT INTO dbo.t2 VALUES (3), (4)  
GO  
  
CREATE PROCEDURE dbo.p1  
  WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
  AS  
  BEGIN ATOMIC WITH ( TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english' )  
  
    DECLARE @t dbo.tab1  
    INSERT @t (c1)  
    SELECT c1 FROM dbo.t1;  
  
    INSERT @t (c1)  
    SELECT c1 FROM dbo.t2;  
  
    SELECT c1 FROM @t;  
  END  
GO  
  
EXEC dbo.p1  
GO  
```  
  
## <a name="memory-consumption-for-table-variables"></a><span data-ttu-id="36b74-147">表变量的内存使用情况</span><span class="sxs-lookup"><span data-stu-id="36b74-147">Memory Consumption for Table Variables</span></span>  
 <span data-ttu-id="36b74-148">表变量的内存使用情况类似于内存优化表，只是在非聚集索引上有所不同。</span><span class="sxs-lookup"><span data-stu-id="36b74-148">Memory consumption for table variables is similar to memory-optimized tables, with the exception of nonclustered indexes.</span></span> <span data-ttu-id="36b74-149">如果将多个行插入带有非聚集索引的内存优化表变量，并且索引键很大，则这些表变量将使用不成比例的内存量。</span><span class="sxs-lookup"><span data-stu-id="36b74-149">If you insert a lot of rows into memory-optimized table variables with nonclustered indexes and if the index keys are large, these table variables will use a disproportionate amount of memory.</span></span> <span data-ttu-id="36b74-150">大型表变量上的非聚集索引需要的内存按比例高于插入表中的相同数量行的非聚集索引所需要的内存（索引页面中内存更多）。</span><span class="sxs-lookup"><span data-stu-id="36b74-150">Nonclustered indexes on large table variables require proportionately more memory than a nonclustered index would require for the same number of rows inserted into a table (more memory in the index pages).</span></span>  
  
 <span data-ttu-id="36b74-151">表变量使用的内存来自数据库的资源调控器资源池。</span><span class="sxs-lookup"><span data-stu-id="36b74-151">Memory for table variables comes from the database's Resource Governor resource pool.</span></span>  
  
 <span data-ttu-id="36b74-152">与内存优化表不同，表变量使用的内存（包括删除的行）在表变量超出作用域时将被释放。</span><span class="sxs-lookup"><span data-stu-id="36b74-152">Unlike memory-optimized tables, the memory consumed (including deleted rows) by table variables is freed when the table variable goes out of scope.</span></span>  
  
 <span data-ttu-id="36b74-153">内存将作为数据库的单一 PGPOOL 内存消耗者的一部分加以考虑。</span><span class="sxs-lookup"><span data-stu-id="36b74-153">Memory is accounted for as part of the single PGPOOL memory consumer of the database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36b74-154">另请参阅</span><span class="sxs-lookup"><span data-stu-id="36b74-154">See Also</span></span>  
 [<span data-ttu-id="36b74-155">对内存中 OLTP 的 Transact-SQL 支持</span><span class="sxs-lookup"><span data-stu-id="36b74-155">Transact-SQL Support for In-Memory OLTP</span></span>](../relational-databases/in-memory-oltp/transact-sql-support-for-in-memory-oltp.md)  
  
  
