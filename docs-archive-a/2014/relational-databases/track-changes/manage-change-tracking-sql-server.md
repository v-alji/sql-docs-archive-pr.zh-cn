---
title: 管理更改跟踪 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- tracking data changes [SQL Server]
- change tracking [SQL Server], overhead
- change tracking [SQL Server]
- change tracking [SQL Server], managing
ms.assetid: 94a8d361-e897-4d6d-9a8f-1bb652e7a850
author: rothja
ms.author: jroth
ms.openlocfilehash: 36409f2ce256325da1c9849e5bec7e7ce114cf25
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586558"
---
# <a name="manage-change-tracking-sql-server"></a><span data-ttu-id="0cf13-102">管理更改跟踪 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0cf13-102">Manage Change Tracking (SQL Server)</span></span>
  <span data-ttu-id="0cf13-103">本主题说明如何管理更改跟踪。</span><span class="sxs-lookup"><span data-stu-id="0cf13-103">This topic describes how to manage change tracking.</span></span> <span data-ttu-id="0cf13-104">本主题还说明如何配置安全性以及如何确定使用更改跟踪时对存储和性能的影响。</span><span class="sxs-lookup"><span data-stu-id="0cf13-104">It also describes how to configure security and determine the effects on storage and performance when change tracking is used.</span></span>  
  
## <a name="managing-change-tracking"></a><span data-ttu-id="0cf13-105">管理更改跟踪</span><span class="sxs-lookup"><span data-stu-id="0cf13-105">Managing Change Tracking</span></span>  
 <span data-ttu-id="0cf13-106">以下各节列出了与管理更改跟踪相关的目录视图、权限和设置。</span><span class="sxs-lookup"><span data-stu-id="0cf13-106">The following sections list catalog views, permissions, and settings that are relevant for managing change tracking.</span></span>  
  
### <a name="catalog-views"></a><span data-ttu-id="0cf13-107">目录视图</span><span class="sxs-lookup"><span data-stu-id="0cf13-107">Catalog Views</span></span>  
 <span data-ttu-id="0cf13-108">若要确定哪些表和数据库启用了更改跟踪，可以使用以下目录视图：</span><span class="sxs-lookup"><span data-stu-id="0cf13-108">To determine which tables and databases have change tracking enabled, you can use the following catalog views:</span></span>  
  
-   [<span data-ttu-id="0cf13-109">sys.change_tracking_databases (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="0cf13-109">sys.change_tracking_databases &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/change-tracking-catalog-views-sys-change-tracking-databases)  
  
-   [<span data-ttu-id="0cf13-110">sys.change_tracking_tables (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="0cf13-110">sys.change_tracking_tables &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/change-tracking-catalog-views-sys-change-tracking-tables)  
  
 <span data-ttu-id="0cf13-111">此外， [sys.internal_tables](/sql/relational-databases/system-catalog-views/sys-internal-tables-transact-sql) 目录视图还列出了对用户表启用更改跟踪时所创建的内部表。</span><span class="sxs-lookup"><span data-stu-id="0cf13-111">Also, the [sys.internal_tables](/sql/relational-databases/system-catalog-views/sys-internal-tables-transact-sql) catalog view lists the internal tables that are created when change tracking is enabled for a user table.</span></span>  
  
### <a name="security"></a><span data-ttu-id="0cf13-112">安全性</span><span class="sxs-lookup"><span data-stu-id="0cf13-112">Security</span></span>  
 <span data-ttu-id="0cf13-113">若要使用 [更改跟踪函数](/sql/relational-databases/system-functions/change-tracking-functions-transact-sql)访问更改跟踪信息，主体必须拥有以下权限：</span><span class="sxs-lookup"><span data-stu-id="0cf13-113">To access change tracking information by using the [change tracking functions](/sql/relational-databases/system-functions/change-tracking-functions-transact-sql), the principal must have the following permissions:</span></span>  
  
-   <span data-ttu-id="0cf13-114">至少针对主键列（已启用更改跟踪的表针对被查询表的主键列）拥有 SELECT 权限。</span><span class="sxs-lookup"><span data-stu-id="0cf13-114">SELECT permission on at least the primary key columns on the change-tracked table to the table that is being queried.</span></span>  
  
-   <span data-ttu-id="0cf13-115">对于要获取其更改的表拥有 VIEW CHANGE TRACKING 权限。</span><span class="sxs-lookup"><span data-stu-id="0cf13-115">VIEW CHANGE TRACKING permission on the table for which changes are being obtained.</span></span> <span data-ttu-id="0cf13-116">要求拥有 VIEW CHANGE TRACKING 权限的原因如下：</span><span class="sxs-lookup"><span data-stu-id="0cf13-116">The VIEW CHANGE TRACKING permission is required for the following reasons:</span></span>  
  
    -   <span data-ttu-id="0cf13-117">更改跟踪记录包含有关已删除行的信息，具体而言，就是已删除行的主键值。</span><span class="sxs-lookup"><span data-stu-id="0cf13-117">Change tracking records include information about rows that have been deleted, specifically the primary key values of the rows that have been deleted.</span></span> <span data-ttu-id="0cf13-118">在删除了某些敏感数据之后，某个主体可能已被授予针对启用了更改跟踪的表的 SELECT 权限。</span><span class="sxs-lookup"><span data-stu-id="0cf13-118">A principal could have been granted SELECT permission for a change tracked table after some sensitive data had been deleted.</span></span> <span data-ttu-id="0cf13-119">在这种情况下，您不会希望该主体能够使用更改跟踪来访问那些已删除的信息。</span><span class="sxs-lookup"><span data-stu-id="0cf13-119">In this case, you would not want that principal to be able to access that deleted information by using change tracking.</span></span>  
  
    -   <span data-ttu-id="0cf13-120">更改跟踪信息可以存储有关更新操作所更改的列的信息。</span><span class="sxs-lookup"><span data-stu-id="0cf13-120">Change tracking information can store information about which columns have been changed by update operations.</span></span> <span data-ttu-id="0cf13-121">某个主体可能无权访问包含敏感信息的列。</span><span class="sxs-lookup"><span data-stu-id="0cf13-121">A principal could be denied permission to a column that contains sensitive information.</span></span> <span data-ttu-id="0cf13-122">但是，由于有更改跟踪信息，因此主体可以确定某列的值是否已更新，但是该主体无法确定该列的值。</span><span class="sxs-lookup"><span data-stu-id="0cf13-122">However, because change tracking information is available, a principal can determine that a column value has been updated, but the principal cannot determine the value of the column.</span></span>  
  
## <a name="understanding-change-tracking-overhead"></a><span data-ttu-id="0cf13-123">了解更改跟踪开销</span><span class="sxs-lookup"><span data-stu-id="0cf13-123">Understanding Change Tracking Overhead</span></span>  
 <span data-ttu-id="0cf13-124">启用表的更改跟踪后，会影响某些管理操作。</span><span class="sxs-lookup"><span data-stu-id="0cf13-124">When change tracking is enabled for a table, some administration operations are affected.</span></span> <span data-ttu-id="0cf13-125">下表列出了应当注意的操作和影响。</span><span class="sxs-lookup"><span data-stu-id="0cf13-125">The following table lists the operations and the effects you should consider.</span></span>  
  
|<span data-ttu-id="0cf13-126">Operation</span><span class="sxs-lookup"><span data-stu-id="0cf13-126">Operation</span></span>|<span data-ttu-id="0cf13-127">启用更改跟踪后</span><span class="sxs-lookup"><span data-stu-id="0cf13-127">When change tracking is enabled</span></span>|  
|---------------|-------------------------------------|  
|<span data-ttu-id="0cf13-128">DROP TABLE</span><span class="sxs-lookup"><span data-stu-id="0cf13-128">DROP TABLE</span></span>|<span data-ttu-id="0cf13-129">会删除已删除表的所有更改跟踪信息。</span><span class="sxs-lookup"><span data-stu-id="0cf13-129">All change tracking information for the dropped table is removed.</span></span>|  
|<span data-ttu-id="0cf13-130">ALTER TABLE DROP CONSTRAINT</span><span class="sxs-lookup"><span data-stu-id="0cf13-130">ALTER TABLE DROP CONSTRAINT</span></span>|<span data-ttu-id="0cf13-131">删除 PRIMARY KEY 约束的尝试将失败。</span><span class="sxs-lookup"><span data-stu-id="0cf13-131">An attempt to drop the PRIMARY KEY constraint will fail.</span></span> <span data-ttu-id="0cf13-132">必须先禁用更改跟踪，然后才能删除 PRIMARY KEY 约束。</span><span class="sxs-lookup"><span data-stu-id="0cf13-132">Change tracking must be disabled before a PRIMARY KEY constraint can be dropped.</span></span>|  
|<span data-ttu-id="0cf13-133">ALTER TABLE DROP COLUMN</span><span class="sxs-lookup"><span data-stu-id="0cf13-133">ALTER TABLE DROP COLUMN</span></span>|<span data-ttu-id="0cf13-134">如果要删除的列是主键的一部分，则不允许删除该列，而不管是否启用了更改跟踪。</span><span class="sxs-lookup"><span data-stu-id="0cf13-134">If a column that is being dropped is part of the primary key, dropping the column is not allowed, regardless of change tracking.</span></span><br /><br /> <span data-ttu-id="0cf13-135">如果要删除的列不是主键的一部分，则可以成功删除该列。</span><span class="sxs-lookup"><span data-stu-id="0cf13-135">If the column that is being dropped is not part of the primary key, dropping the column succeeds.</span></span> <span data-ttu-id="0cf13-136">但是，首先应了解此操作对同步此数据的任何应用程序的影响。</span><span class="sxs-lookup"><span data-stu-id="0cf13-136">However, the effect on any application that is synchronizing this data should be understood first.</span></span> <span data-ttu-id="0cf13-137">如果为该表启用了列更改跟踪，则可能仍会将已删除的列作为更改跟踪信息的一部分返回。</span><span class="sxs-lookup"><span data-stu-id="0cf13-137">If column change tracking is enabled for the table, the dropped column might still be returned as part of the change tracking information.</span></span> <span data-ttu-id="0cf13-138">已删除列的处理由应用程序负责。</span><span class="sxs-lookup"><span data-stu-id="0cf13-138">It is the responsibility of the application to handle the dropped column.</span></span>|  
|<span data-ttu-id="0cf13-139">ALTER TABLE ADD COLUMN</span><span class="sxs-lookup"><span data-stu-id="0cf13-139">ALTER TABLE ADD COLUMN</span></span>|<span data-ttu-id="0cf13-140">如果将新列添加到启用了更改跟踪的表中，则不会跟踪该列的添加。</span><span class="sxs-lookup"><span data-stu-id="0cf13-140">If a new column is added to the change tracked table, the addition of the column is not tracked.</span></span> <span data-ttu-id="0cf13-141">只会跟踪对新列所做的更新和更改。</span><span class="sxs-lookup"><span data-stu-id="0cf13-141">Only the updates and changes that are made to the new column are tracked.</span></span>|  
|<span data-ttu-id="0cf13-142">ALTER TABLE ALTER COLUMN</span><span class="sxs-lookup"><span data-stu-id="0cf13-142">ALTER TABLE ALTER COLUMN</span></span>|<span data-ttu-id="0cf13-143">不会跟踪非主键列的数据类型更改。</span><span class="sxs-lookup"><span data-stu-id="0cf13-143">Data type changes of a non-primary key columns are not tracked.</span></span>|  
|<span data-ttu-id="0cf13-144">ALTER TABLE SWITCH</span><span class="sxs-lookup"><span data-stu-id="0cf13-144">ALTER TABLE SWITCH</span></span>|<span data-ttu-id="0cf13-145">如果其中一个表或两个表都启用了更改跟踪，则切换分区将失败。</span><span class="sxs-lookup"><span data-stu-id="0cf13-145">Switching a partition fails if one or both of the tables has change tracking enabled.</span></span>|  
|<span data-ttu-id="0cf13-146">DROP INDEX 或 ALTER INDEX DISABLE</span><span class="sxs-lookup"><span data-stu-id="0cf13-146">DROP INDEX, or ALTER INDEX DISABLE</span></span>|<span data-ttu-id="0cf13-147">不能删除或禁用强制使用主键的索引。</span><span class="sxs-lookup"><span data-stu-id="0cf13-147">The index that enforces the primary key cannot be dropped or disabled.</span></span>|  
|<span data-ttu-id="0cf13-148">TRUNCATE TABLE</span><span class="sxs-lookup"><span data-stu-id="0cf13-148">TRUNCATE TABLE</span></span>|<span data-ttu-id="0cf13-149">可以对启用了更改跟踪的表执行截断表操作。</span><span class="sxs-lookup"><span data-stu-id="0cf13-149">Truncating a table can be performed on a table that has change tracking enabled.</span></span> <span data-ttu-id="0cf13-150">但是，不会跟踪由该操作删除的行，并且会更新最低有效版本。</span><span class="sxs-lookup"><span data-stu-id="0cf13-150">However, the rows that are deleted by the operation are not tracked, and the minimum valid version is updated.</span></span> <span data-ttu-id="0cf13-151">当应用程序检查其版本时，检查结果会表明该版本太陈旧，需要进行重新初始化。</span><span class="sxs-lookup"><span data-stu-id="0cf13-151">When an application checks its version, the check indicates that the version is too old and a reinitialization is required.</span></span> <span data-ttu-id="0cf13-152">这与禁用后又重新启用表的更改跟踪的效果相同。</span><span class="sxs-lookup"><span data-stu-id="0cf13-152">This is the same as change tracking being disabled, and then reenabled for the table.</span></span>|  
  
 <span data-ttu-id="0cf13-153">由于在操作过程中会存储更改跟踪信息，因此使用更改跟踪会增加 DML 操作的一些开销。</span><span class="sxs-lookup"><span data-stu-id="0cf13-153">Using change tracking does add some overhead to DML operations because of the change tracking information that is being stored as part of the operation.</span></span>  
  
### <a name="effects-on-dml"></a><span data-ttu-id="0cf13-154">对 DML 的影响</span><span class="sxs-lookup"><span data-stu-id="0cf13-154">Effects on DML</span></span>  
 <span data-ttu-id="0cf13-155">更改跟踪已经过优化，以尽可能减小对 DML 操作的性能影响。</span><span class="sxs-lookup"><span data-stu-id="0cf13-155">Change tracking has been optimized to minimize the performance overhead on DML operations.</span></span> <span data-ttu-id="0cf13-156">对表使用更改跟踪所导致的性能开销增加类似于为表创建了一个索引并需要维护该索引时而导致的开销。</span><span class="sxs-lookup"><span data-stu-id="0cf13-156">The incremental performance overhead that is associated with using change tracking on a table is similar to the overhead incurred when an index is created for a table and needs to be maintained.</span></span>  
  
 <span data-ttu-id="0cf13-157">对于由 DML 操作更改的每一行，都会向内部更改跟踪表中添加一行。</span><span class="sxs-lookup"><span data-stu-id="0cf13-157">For each row that is changed by a DML operation, a row is added to the internal change tracking table.</span></span> <span data-ttu-id="0cf13-158">这种与 DML 操作相关的影响取决于各种因素，例如：</span><span class="sxs-lookup"><span data-stu-id="0cf13-158">The effect of this relative to the DML operation depends on various factors, such as the following:</span></span>  
  
-   <span data-ttu-id="0cf13-159">主键列数</span><span class="sxs-lookup"><span data-stu-id="0cf13-159">The number of primary key columns</span></span>  
  
-   <span data-ttu-id="0cf13-160">用户表行中所更改的数据量</span><span class="sxs-lookup"><span data-stu-id="0cf13-160">The amount of data that is being changed in the user table row</span></span>  
  
-   <span data-ttu-id="0cf13-161">事务中所执行的操作数</span><span class="sxs-lookup"><span data-stu-id="0cf13-161">The number of operations that are being performed in a transaction</span></span>  
  
 <span data-ttu-id="0cf13-162">如果使用了快照隔离，则它也会影响所有 DML 操作的性能，而不管是否启用了更改跟踪。</span><span class="sxs-lookup"><span data-stu-id="0cf13-162">Snapshot isolation, if used, also has an effect on performance for all DML operations, whether change tracking is enabled or not.</span></span>  
  
### <a name="effects-on-storage"></a><span data-ttu-id="0cf13-163">对存储的影响</span><span class="sxs-lookup"><span data-stu-id="0cf13-163">Effects on Storage</span></span>  
 <span data-ttu-id="0cf13-164">更改跟踪数据存储在以下类型的内部表中：</span><span class="sxs-lookup"><span data-stu-id="0cf13-164">Change tracking data is stored in the following types of internal tables:</span></span>  
  
-   <span data-ttu-id="0cf13-165">内部更改表</span><span class="sxs-lookup"><span data-stu-id="0cf13-165">Internal change table</span></span>  
  
     <span data-ttu-id="0cf13-166">启用了更改跟踪的每个用户表都有一个内部更改表。</span><span class="sxs-lookup"><span data-stu-id="0cf13-166">There is one internal change table for each user table that has change tracking enabled.</span></span>  
  
-   <span data-ttu-id="0cf13-167">内部事务表</span><span class="sxs-lookup"><span data-stu-id="0cf13-167">Internal transaction table</span></span>  
  
     <span data-ttu-id="0cf13-168">数据库有一个内部事务表。</span><span class="sxs-lookup"><span data-stu-id="0cf13-168">There is one internal transaction table for the database.</span></span>  
  
 <span data-ttu-id="0cf13-169">这些内部表对存储要求有下列影响：</span><span class="sxs-lookup"><span data-stu-id="0cf13-169">These internal tables affect storage requirements in the following ways:</span></span>  
  
-   <span data-ttu-id="0cf13-170">对于用户表中每行的每个更改，都会向内部更改表中添加一行。</span><span class="sxs-lookup"><span data-stu-id="0cf13-170">For each change to each row in the user table, a row is added to the internal change table.</span></span> <span data-ttu-id="0cf13-171">该行有一个较小的固定开销，外加一个大小等于主键列大小的可变开销。</span><span class="sxs-lookup"><span data-stu-id="0cf13-171">This row has a small fixed overhead plus a variable overhead equal to the size of the primary key columns.</span></span> <span data-ttu-id="0cf13-172">该行可以包含由应用程序设置的可选上下文信息。</span><span class="sxs-lookup"><span data-stu-id="0cf13-172">The row can contain optional context information set by an application.</span></span> <span data-ttu-id="0cf13-173">此外，如果启用了列跟踪，则每个发生更改的列还需要在跟踪表中占用 4 字节。</span><span class="sxs-lookup"><span data-stu-id="0cf13-173">And, if column tracking is enabled, each changed column requires 4 bytes in the tracking table.</span></span>  
  
-   <span data-ttu-id="0cf13-174">对于每个已提交的事务，都会向内部事务表中添加一行。</span><span class="sxs-lookup"><span data-stu-id="0cf13-174">For each committed transaction, a row is added to an internal transaction table.</span></span>  
  
 <span data-ttu-id="0cf13-175">对于其他内部表，可以使用 [sp_spaceused](/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql) 存储过程来确定用于更改跟踪表的空间。</span><span class="sxs-lookup"><span data-stu-id="0cf13-175">As with other internal tables, you can determine the space used for the change tracking tables by using the [sp_spaceused](/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql) stored procedure.</span></span> <span data-ttu-id="0cf13-176">可以使用 [sys.internal_tables](/sql/relational-databases/system-catalog-views/sys-internal-tables-transact-sql) 目录视图来获取这些内部表的名称，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="0cf13-176">The names of the internal tables can be obtained by using the [sys.internal_tables](/sql/relational-databases/system-catalog-views/sys-internal-tables-transact-sql) catalog view, as shown in the following example.</span></span>  
  
```sql  
sp_spaceused 'sys.change_tracking_309576141'  
sp_spaceused 'sys.syscommittab'  
```  
  
## <a name="see-also"></a><span data-ttu-id="0cf13-177">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0cf13-177">See Also</span></span>  
 <span data-ttu-id="0cf13-178">[跟踪数据更改 (SQL Server)](track-data-changes-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="0cf13-178">[Track Data Changes &#40;SQL Server&#41;](track-data-changes-sql-server.md) </span></span>  
 <span data-ttu-id="0cf13-179">[ALTER TABLE (Transact-SQL)](/sql/t-sql/statements/alter-table-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0cf13-179">[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) </span></span>  
 <span data-ttu-id="0cf13-180">[数据库属性（“ChangeTracking”页）](../databases/database-properties-changetracking-page.md) </span><span class="sxs-lookup"><span data-stu-id="0cf13-180">[Database Properties &#40;ChangeTracking Page&#41;](../databases/database-properties-changetracking-page.md) </span></span>  
 <span data-ttu-id="0cf13-181">[ALTER DATABASE SET 选项 (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql-set-options) </span><span class="sxs-lookup"><span data-stu-id="0cf13-181">[ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options) </span></span>  
 <span data-ttu-id="0cf13-182">[sys.change_tracking_databases (Transact-SQL)](/sql/relational-databases/system-catalog-views/change-tracking-catalog-views-sys-change-tracking-databases) </span><span class="sxs-lookup"><span data-stu-id="0cf13-182">[sys.change_tracking_databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/change-tracking-catalog-views-sys-change-tracking-databases) </span></span>  
 <span data-ttu-id="0cf13-183">[sys.change_tracking_tables (Transact-SQL)](/sql/relational-databases/system-catalog-views/change-tracking-catalog-views-sys-change-tracking-tables) </span><span class="sxs-lookup"><span data-stu-id="0cf13-183">[sys.change_tracking_tables &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/change-tracking-catalog-views-sys-change-tracking-tables) </span></span>  
 <span data-ttu-id="0cf13-184">[跟踪数据更改 (SQL Server)](track-data-changes-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="0cf13-184">[Track Data Changes &#40;SQL Server&#41;](track-data-changes-sql-server.md) </span></span>  
 <span data-ttu-id="0cf13-185">[关于更改跟踪 (SQL Server)](../track-changes/about-change-tracking-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="0cf13-185">[About Change Tracking &#40;SQL Server&#41;](../track-changes/about-change-tracking-sql-server.md) </span></span>  
 [<span data-ttu-id="0cf13-186">处理变更数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0cf13-186">Work with Change Data &#40;SQL Server&#41;</span></span>](work-with-change-data-sql-server.md)  
  
  
