---
title: 禁用索引和约束 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
f1_keywords:
- sql12.swb.disableindexes.f1
helpviewer_keywords:
- disabled indexes [SQL Server], index operations
- nonclustered indexes [SQL Server], disabling
- disabled indexes [SQL Server], guidelines
- clustered indexes, disabling
- constraints [SQL Server], disabling
- disabled indexes [SQL Server], viewing
- FOREIGN KEY constraints, disabling
- statistical information [SQL Server], indexes
- index disabling [SQL Server]
- indexed views [SQL Server], disabled indexes
ms.assetid: 2198f1af-fa44-47e9-92df-f4fde322ba18
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 40f9de4108be4defeb2353a9e7835c289641a819
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693300"
---
# <a name="disable-indexes-and-constraints"></a><span data-ttu-id="cdf3b-102">禁用索引和约束</span><span class="sxs-lookup"><span data-stu-id="cdf3b-102">Disable Indexes and Constraints</span></span>
  <span data-ttu-id="cdf3b-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中禁用索引或约束。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-103">This topic describes how to disable an index or constraints in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="cdf3b-104">禁用索引可以防止用户访问索引，而对于聚集索引，则可以防止用户访问基础表数据。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-104">Disabling an index prevents user access to the index, and for clustered indexes to the underlying table data.</span></span> <span data-ttu-id="cdf3b-105">索引定义保留在元数据中，非聚集索引的索引统计信息仍保留。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-105">The index definition remains in metadata, and index statistics are kept on nonclustered indexes.</span></span> <span data-ttu-id="cdf3b-106">对视图禁用非聚集索引或聚集索引会以物理方式删除索引数据。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-106">Disabling a nonclustered or clustered index on a view physically deletes the index data.</span></span> <span data-ttu-id="cdf3b-107">禁用表的聚集索引可以防止对数据的访问，数据仍保留在表中，但在删除或重新生成索引之前，无法对这些数据执行数据操作语言 (DML) 操作。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-107">Disabling a clustered index on a table prevents access to the data; the data still remains in the table, but is unavailable for data manipulation language (DML) operations until the index is dropped or rebuilt.</span></span>  
  
 <span data-ttu-id="cdf3b-108">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="cdf3b-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="cdf3b-109">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="cdf3b-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="cdf3b-110">限制和局限</span><span class="sxs-lookup"><span data-stu-id="cdf3b-110">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="cdf3b-111">安全性</span><span class="sxs-lookup"><span data-stu-id="cdf3b-111">Security</span></span>](#Security)  
  
-   <span data-ttu-id="cdf3b-112">**禁用索引，使用：**</span><span class="sxs-lookup"><span data-stu-id="cdf3b-112">**To disable an index, using:**</span></span>  
  
     [<span data-ttu-id="cdf3b-113">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="cdf3b-113">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="cdf3b-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="cdf3b-114">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="cdf3b-115">开始之前</span><span class="sxs-lookup"><span data-stu-id="cdf3b-115">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="cdf3b-116">限制和局限</span><span class="sxs-lookup"><span data-stu-id="cdf3b-116">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="cdf3b-117">索引处于禁用状态时，不对其进行维护。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-117">The index is not maintained while it is disabled.</span></span>  
  
-   <span data-ttu-id="cdf3b-118">查询优化器创建查询执行计划时不考虑禁用的索引。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-118">The query optimizer does not consider the disabled index when creating query execution plans.</span></span> <span data-ttu-id="cdf3b-119">另外，引用包含表提示的已禁用索引的查询将失败。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-119">Also, queries that reference the disabled index with a table hint fail.</span></span>  
  
-   <span data-ttu-id="cdf3b-120">无法创建与现有禁用索引同名的索引。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-120">You cannot create an index that uses the same name as an existing disabled index.</span></span>  
  
-   <span data-ttu-id="cdf3b-121">可以删除已禁用索引。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-121">A disabled index can be dropped.</span></span>  
  
-   <span data-ttu-id="cdf3b-122">禁用唯一索引时，还将禁用 PRIMARY KEY 约束或 UNIQUE 约束及引用其他表中的索引列的所有 FOREIGN KEY 约束。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-122">When disabling a unique index, the PRIMARY KEY or UNIQUE constraint and all FOREIGN KEY constraints that reference the indexed columns from other tables are also disabled.</span></span> <span data-ttu-id="cdf3b-123">禁用聚集索引时，还将禁用基础表的所有传入和传出的 FOREIGN KEY 约束。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-123">When disabling a clustered index, all incoming and outgoing FOREIGN KEY constraints on the underlying table are also disabled.</span></span> <span data-ttu-id="cdf3b-124">索引处于禁用状态时，会在警告消息中列出约束名称。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-124">The constraint names are listed in a warning message when the index is disabled.</span></span> <span data-ttu-id="cdf3b-125">重新生成索引后，必须使用 ALTER TABLE CHECK CONSTRAINT 语句手动启用所有约束。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-125">After rebuilding the index, all constraints must be manually enabled by using the ALTER TABLE CHECK CONSTRAINT statement.</span></span>  
  
-   <span data-ttu-id="cdf3b-126">相关联的聚集索引处于禁用状态时，会自动禁用非聚集索引。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-126">Nonclustered indexes are automatically disabled when the associated clustered index is disabled.</span></span> <span data-ttu-id="cdf3b-127">表或视图的聚集索引处于启用状态或删除了表的聚集索引时，才能启用这些非聚集索引。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-127">They cannot be enabled until either the clustered index on the table or view is enabled or the clustered index on the table is dropped.</span></span> <span data-ttu-id="cdf3b-128">除非使用 ALTER INDEX ALL REBUILD 语句启用了聚集索引，否则必须显式启用非聚集索引。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-128">Nonclustered indexes must be explicitly enabled, unless the clustered index was enabled by using the ALTER INDEX ALL REBUILD statement.</span></span>  
  
-   <span data-ttu-id="cdf3b-129">ALTER INDEX ALL REBUILD 语句将重新生成并启用表的所有已禁用索引（视图的已禁用索引除外）。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-129">The ALTER INDEX ALL REBUILD statement rebuilds and enables all disabled indexes on the table, except for disabled indexes on views.</span></span> <span data-ttu-id="cdf3b-130">视图的索引必须另外使用 ALTER INDEX ALL REBUILD 语句来启用。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-130">Indexes on views must be enabled in a separate ALTER INDEX ALL REBUILD statement.</span></span>  
  
-   <span data-ttu-id="cdf3b-131">禁用表的聚集索引时，还将禁用针对引用该表的视图的所有聚集索引和非聚集索引。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-131">Disabling a clustered index on a table also disables all clustered and nonclustered indexes on views that reference that table.</span></span> <span data-ttu-id="cdf3b-132">必须像重新生成被引用表的索引那样重新生成这些索引。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-132">These indexes must be rebuilt just as those on the referenced table.</span></span>  
  
-   <span data-ttu-id="cdf3b-133">不能访问已禁用的聚集索引的数据行，但可以删除或重新生成该聚集索引。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-133">The data rows of the disabled clustered index cannot be accessed except to drop or rebuild the clustered index.</span></span>  
  
-   <span data-ttu-id="cdf3b-134">表中没有已禁用的聚集索引时，可以联机重新生成已禁用的非聚集索引。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-134">You can rebuild a disabled nonclustered index online when the table does not have a disabled clustered index.</span></span> <span data-ttu-id="cdf3b-135">但是，如果使用 ALTER INDEX REBUILD 语句或 CREATE INDEX WITH DROP_EXISTING 语句，则务必脱机重新生成已禁用的聚集索引。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-135">However, you must always rebuild a disabled clustered index offline if you use either the ALTER INDEX REBUILD or CREATE INDEX WITH DROP_EXISTING statement.</span></span> <span data-ttu-id="cdf3b-136">有关联机索引操作的详细信息，请参阅 [联机执行索引操作](perform-index-operations-online.md)。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-136">For more information about online index operations, see [Perform Index Operations Online](perform-index-operations-online.md).</span></span>  
  
-   <span data-ttu-id="cdf3b-137">无法对包含已禁用的聚集索引的表成功执行 CREATE STATISTICS 语句。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-137">The CREATE STATISTICS statement cannot be successfully executed on a table that has a disabled clustered index.</span></span>  
  
-   <span data-ttu-id="cdf3b-138">当索引处于禁用状态且存在以下条件时，AUTO_CREATE_STATISTICS 数据库选项将对列创建新的统计信息：</span><span class="sxs-lookup"><span data-stu-id="cdf3b-138">The AUTO_CREATE_STATISTICS database option creates new statistics on a column when the index is disabled and the following conditions exist:</span></span>  
  
    -   <span data-ttu-id="cdf3b-139">AUTO_CREATE_STATISTICS 设置为 ON</span><span class="sxs-lookup"><span data-stu-id="cdf3b-139">AUTO_CREATE_STATISTICS is set to ON</span></span>  
  
    -   <span data-ttu-id="cdf3b-140">当前还没有列的相关统计信息。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-140">There are no existing statistics for the column.</span></span>  
  
    -   <span data-ttu-id="cdf3b-141">在查询优化过程中需要统计信息。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-141">Statistics are required during query optimization.</span></span>  
  
-   <span data-ttu-id="cdf3b-142">如果聚集索引处于禁用状态， [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) 无法返回有关基础表的信息；该语句将报告聚集索引已禁用。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-142">If a clustered index is disabled, [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) cannot return information about the underlying table; instead, the statement reports that the clustered index is disabled.</span></span> <span data-ttu-id="cdf3b-143">[DBCC INDEXDEFRAG](/sql/t-sql/database-console-commands/dbcc-indexdefrag-transact-sql) 不能用于对已禁用的索引进行碎片整理；该语句将失败并显示错误消息。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-143">[DBCC INDEXDEFRAG](/sql/t-sql/database-console-commands/dbcc-indexdefrag-transact-sql) cannot be used to defragment a disabled index; the statement fails with an error message.</span></span> <span data-ttu-id="cdf3b-144">可以使用 [DBCC DBREINDEX](/sql/t-sql/database-console-commands/dbcc-dbreindex-transact-sql) 重新生成已禁用索引。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-144">You can use [DBCC DBREINDEX](/sql/t-sql/database-console-commands/dbcc-dbreindex-transact-sql) to rebuild a disabled index.</span></span>  
  
-   <span data-ttu-id="cdf3b-145">创建一个新的聚集索引将启用以前禁用的非聚集索引。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-145">Creating a new clustered index enables previously disabled nonclustered indexes.</span></span> <span data-ttu-id="cdf3b-146">有关详细信息，请参阅 [Enable Indexes and Constraints](enable-indexes-and-constraints.md)。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-146">For more information, see [Enable Indexes and Constraints](enable-indexes-and-constraints.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="cdf3b-147">Security</span><span class="sxs-lookup"><span data-stu-id="cdf3b-147">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="cdf3b-148">权限</span><span class="sxs-lookup"><span data-stu-id="cdf3b-148">Permissions</span></span>  
 <span data-ttu-id="cdf3b-149">若要执行 ALTER INDEX，至少需要对表或视图具有 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-149">To execute ALTER INDEX, at a minimum, ALTER permission on the table or view is required.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="cdf3b-150">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="cdf3b-150">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-disable-an-index"></a><span data-ttu-id="cdf3b-151">禁用索引</span><span class="sxs-lookup"><span data-stu-id="cdf3b-151">To disable an index</span></span>  
  
1.  <span data-ttu-id="cdf3b-152">在对象资源管理器中，单击加号以便展开包含您要禁用索引的表的数据库。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-152">In Object Explorer, click the plus sign to expand the database that contains the table on which you want to disable an index.</span></span>  
  
2.  <span data-ttu-id="cdf3b-153">单击加号以便展开 **“表”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-153">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="cdf3b-154">单击加号以便展开您要禁用索引的表。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-154">Click the plus sign to expand the table on which you want to disable an index.</span></span>  
  
4.  <span data-ttu-id="cdf3b-155">单击加号以便展开 **“索引”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-155">Click the plus sign to expand the **Indexes** folder.</span></span>  
  
5.  <span data-ttu-id="cdf3b-156">右键单击要禁用的索引，然后选择  “禁用”。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-156">Right-click the index you want to disable and select **Disable**.</span></span>  
  
6.  <span data-ttu-id="cdf3b-157">在 **“禁用索引”** 对话框中，确认正确的索引位于 **“要禁用的索引”** 网格中，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-157">In the **Disable Indexes** dialog box, verify that the correct index is in the **Indexes to disable** grid and click **OK**.</span></span>  
  
#### <a name="to-disable-all-indexes-on-a-table"></a><span data-ttu-id="cdf3b-158">禁用表的所有索引</span><span class="sxs-lookup"><span data-stu-id="cdf3b-158">To disable all indexes on a table</span></span>  
  
1.  <span data-ttu-id="cdf3b-159">在对象资源管理器中，单击加号以便展开包含您要禁用索引的表的数据库。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-159">In Object Explorer, click the plus sign to expand the database that contains the table on which you want to disable the indexes.</span></span>  
  
2.  <span data-ttu-id="cdf3b-160">单击加号以便展开 **“表”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-160">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="cdf3b-161">单击加号以便展开您要禁用索引的表。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-161">Click the plus sign to expand the table on which you want to disable the indexes.</span></span>  
  
4.  <span data-ttu-id="cdf3b-162">右键单击  “索引”文件夹，然后选择  “全部禁用”。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-162">Right-click the **Indexes** folder and select **Disable All**.</span></span>  
  
5.  <span data-ttu-id="cdf3b-163">在 **“禁用索引”** 对话框中，确认正确的索引位于 **“要禁用的索引”** 网格中，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-163">In the **Disable Indexes** dialog box, verify that the correct indexes are in the **Indexes to disable** grid and click **OK**.</span></span> <span data-ttu-id="cdf3b-164">若要从 **“要禁用的索引”** 网格中删除索引，请选择该索引，再按 Delete 键。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-164">To remove an index from the **Indexes to disable** grid, select the index and then press the Delete key.</span></span>  
  
 <span data-ttu-id="cdf3b-165">在 **“禁用索引”** 对话框中将提供以下信息：</span><span class="sxs-lookup"><span data-stu-id="cdf3b-165">The following information is available in the **Disable Indexes** dialog box:</span></span>  
  
 <span data-ttu-id="cdf3b-166">**Index Name**</span><span class="sxs-lookup"><span data-stu-id="cdf3b-166">**Index Name**</span></span>  
 <span data-ttu-id="cdf3b-167">显示索引的名称。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-167">Displays the name of the index.</span></span> <span data-ttu-id="cdf3b-168">执行期间，此列还会显示表示状态的图标。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-168">During execution, this column also displays an icon representing the status.</span></span>  
  
 <span data-ttu-id="cdf3b-169">**表名**</span><span class="sxs-lookup"><span data-stu-id="cdf3b-169">**Table Name**</span></span>  
 <span data-ttu-id="cdf3b-170">显示创建索引的表或视图的名称。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-170">Displays the name of the table or view that the index was created on.</span></span>  
  
 <span data-ttu-id="cdf3b-171">**索引类型**</span><span class="sxs-lookup"><span data-stu-id="cdf3b-171">**Index Type**</span></span>  
 <span data-ttu-id="cdf3b-172">显示索引的类型：  “聚集”、  “非聚集”、  “空间”或  ”XML”。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-172">Displays the type of the index: **Clustered**, **Nonclustered**, **Spatial**, or **XML**.</span></span>  
  
 <span data-ttu-id="cdf3b-173">**Status**</span><span class="sxs-lookup"><span data-stu-id="cdf3b-173">**Status**</span></span>  
 <span data-ttu-id="cdf3b-174">显示禁用操作的状态。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-174">Displays the status of the disable operation.</span></span> <span data-ttu-id="cdf3b-175">执行之后可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="cdf3b-175">Possible values after execution are:</span></span>  
  
-   <span data-ttu-id="cdf3b-176">空白</span><span class="sxs-lookup"><span data-stu-id="cdf3b-176">Blank</span></span>  
  
     <span data-ttu-id="cdf3b-177">执行之前， **“状态”** 为空白。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-177">Prior to execution **Status** is blank.</span></span>  
  
-   <span data-ttu-id="cdf3b-178">**正在进行**</span><span class="sxs-lookup"><span data-stu-id="cdf3b-178">**In progress**</span></span>  
  
     <span data-ttu-id="cdf3b-179">禁用索引操作已启动，但尚未完成。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-179">Disabling of the indexes has been started but is not complete.</span></span>  
  
-   <span data-ttu-id="cdf3b-180">**Success**</span><span class="sxs-lookup"><span data-stu-id="cdf3b-180">**Success**</span></span>  
  
     <span data-ttu-id="cdf3b-181">禁用操作已成功完成。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-181">The disable operation completed successfully.</span></span>  
  
-   <span data-ttu-id="cdf3b-182">**错误**</span><span class="sxs-lookup"><span data-stu-id="cdf3b-182">**Error**</span></span>  
  
     <span data-ttu-id="cdf3b-183">禁用索引操作过程中遇到错误，操作未成功完成。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-183">An error was encountered during the index disable operation, and the operation did not complete successfully.</span></span>  
  
-   <span data-ttu-id="cdf3b-184">**已停止**</span><span class="sxs-lookup"><span data-stu-id="cdf3b-184">**Stopped**</span></span>  
  
     <span data-ttu-id="cdf3b-185">用户已停止禁用索引操作，该操作未成功完成。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-185">The disable of the index was not completed successfully because the user stopped the operation.</span></span>  
  
 <span data-ttu-id="cdf3b-186">**消息**</span><span class="sxs-lookup"><span data-stu-id="cdf3b-186">**Message**</span></span>  
 <span data-ttu-id="cdf3b-187">禁用操作期间提供错误消息文本。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-187">Provides the text of error messages during the disable operation.</span></span> <span data-ttu-id="cdf3b-188">执行过程中，错误显示为超链接。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-188">During execution, errors appear as hyperlinks.</span></span> <span data-ttu-id="cdf3b-189">超链接的文本描述错误的正文。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-189">The text of the hyperlinks describes the body of the error.</span></span> <span data-ttu-id="cdf3b-190">**“消息”** 列宽度一般不够，无法阅读完整的消息文本。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-190">The **Message** column is rarely wide enough to read the full message text.</span></span> <span data-ttu-id="cdf3b-191">获取完整文本的方法有两种：</span><span class="sxs-lookup"><span data-stu-id="cdf3b-191">There are two ways to get the full text:</span></span>  
  
-   <span data-ttu-id="cdf3b-192">将鼠标指针移到消息单元上以显示包含错误文本的工具提示。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-192">Move the mouse pointer over the message cell to display a ToolTip with the error text.</span></span>  
  
-   <span data-ttu-id="cdf3b-193">单击超链接以显示一个对话框，显示完整的错误。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-193">Click the hyperlink to display a dialog box displaying the full error.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="cdf3b-194">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="cdf3b-194">Using Transact-SQL</span></span>  
  
#### <a name="to-disable-an-index"></a><span data-ttu-id="cdf3b-195">禁用索引</span><span class="sxs-lookup"><span data-stu-id="cdf3b-195">To disable an index</span></span>  
  
1.  <span data-ttu-id="cdf3b-196">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-196">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="cdf3b-197">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-197">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="cdf3b-198">将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-198">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- disables the IX_Employee_OrganizationLevel_OrganizationNode index  
    -- on the HumanResources.Employee table  
    ALTER INDEX IX_Employee_OrganizationLevel_OrganizationNode ON HumanResources.Employee  
    DISABLE;  
    ```  
  
#### <a name="to-disable-all-indexes-on-a-table"></a><span data-ttu-id="cdf3b-199">禁用表的所有索引</span><span class="sxs-lookup"><span data-stu-id="cdf3b-199">To disable all indexes on a table</span></span>  
  
1.  <span data-ttu-id="cdf3b-200">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-200">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="cdf3b-201">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-201">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="cdf3b-202">将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-202">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Disables all indexes on the HumanResources.Employee table.  
    ALTER INDEX ALL ON HumanResources.Employee  
    DISABLE;  
    ```  
  
 <span data-ttu-id="cdf3b-203">有关详细信息，请参阅 [ALTER INDEX (Transact-SQL)](/sql/t-sql/statements/alter-index-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="cdf3b-203">For more information, see [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql).</span></span>  
  
  
