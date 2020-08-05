---
title: 创建聚集索引 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- index creation [SQL Server], clustered indexes
- clustered indexes, creating
- clustered indexes, PRIMARY KEY constraint
- clustered indexes, UNIQUE constraint
- indexes [SQL Server], clustered
ms.assetid: 47148383-c2c7-4f08-a9e4-7016bf2d1d13
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 567ff9a01bd93323149168b9e3aa0f34d78aee39
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581191"
---
# <a name="create-clustered-indexes"></a><span data-ttu-id="555d2-102">创建聚集索引</span><span class="sxs-lookup"><span data-stu-id="555d2-102">Create Clustered Indexes</span></span>
  <span data-ttu-id="555d2-103">可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中创建表的聚集索引。</span><span class="sxs-lookup"><span data-stu-id="555d2-103">You can create clustered indexes on tables in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="555d2-104">除了个别表之外，每个表都应该有聚集索引。</span><span class="sxs-lookup"><span data-stu-id="555d2-104">With few exceptions, every table should have a clustered index.</span></span> <span data-ttu-id="555d2-105">聚集索引除了可以提高查询性能之外，还可以按需重新生成或重新组织来控制表碎片。</span><span class="sxs-lookup"><span data-stu-id="555d2-105">Besides improving query performance, a clustered index can be rebuilt or reorganized on demand to control table fragmentation.</span></span> <span data-ttu-id="555d2-106">也可以对视图创建聚集索引。</span><span class="sxs-lookup"><span data-stu-id="555d2-106">A clustered index can also be created on a view.</span></span> <span data-ttu-id="555d2-107">（ [描述的聚集索引和非聚集索引](clustered-and-nonclustered-indexes-described.md)主题中定义了聚集索引。）</span><span class="sxs-lookup"><span data-stu-id="555d2-107">(Clustered indexes are defined in the topic [Clustered and Nonclustered Indexes Described](clustered-and-nonclustered-indexes-described.md).)</span></span>  
  
 <span data-ttu-id="555d2-108">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="555d2-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="555d2-109">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="555d2-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="555d2-110">典型实现</span><span class="sxs-lookup"><span data-stu-id="555d2-110">Typical Implementations</span></span>](#Implementations)  
  
     [<span data-ttu-id="555d2-111">限制和局限</span><span class="sxs-lookup"><span data-stu-id="555d2-111">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="555d2-112">安全性</span><span class="sxs-lookup"><span data-stu-id="555d2-112">Security</span></span>](#Security)  
  
-   <span data-ttu-id="555d2-113">**若要创建表的聚集索引，请使用：**</span><span class="sxs-lookup"><span data-stu-id="555d2-113">**To create a clustered index on a table, using:**</span></span>  
  
     [<span data-ttu-id="555d2-114">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="555d2-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="555d2-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="555d2-115">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="555d2-116">开始之前</span><span class="sxs-lookup"><span data-stu-id="555d2-116">Before You Begin</span></span>  
  
###  <a name="typical-implementations"></a><a name="Implementations"></a> <span data-ttu-id="555d2-117">典型实现</span><span class="sxs-lookup"><span data-stu-id="555d2-117">Typical Implementations</span></span>  
 <span data-ttu-id="555d2-118">聚集索引按下列方式实现：</span><span class="sxs-lookup"><span data-stu-id="555d2-118">Clustered indexes are implemented in the following ways:</span></span>  
  
-   <span data-ttu-id="555d2-119">**PRIMARY KEY 和 UNIQUE 约束**</span><span class="sxs-lookup"><span data-stu-id="555d2-119">**PRIMARY KEY and UNIQUE constraints**</span></span>  
  
     <span data-ttu-id="555d2-120">在创建 PRIMARY KEY 约束时，如果不存在该表的聚集索引且未指定唯一非聚集索引，则将自动对一列或多列创建唯一聚集索引。</span><span class="sxs-lookup"><span data-stu-id="555d2-120">When you create a PRIMARY KEY constraint, a unique clustered index on the column or columns is automatically created if a clustered index on the table does not already exist and you do not specify a unique nonclustered index.</span></span> <span data-ttu-id="555d2-121">主键列不允许空值。</span><span class="sxs-lookup"><span data-stu-id="555d2-121">The primary key column cannot allow NULL values.</span></span>  
  
     <span data-ttu-id="555d2-122">在创建 UNIQUE 约束时，默认情况下将创建唯一非聚集索引，以便强制 UNIQUE 约束。</span><span class="sxs-lookup"><span data-stu-id="555d2-122">When you create a UNIQUE constraint, a unique nonclustered index is created to enforce a UNIQUE constraint by default.</span></span> <span data-ttu-id="555d2-123">如果不存在该表的聚集索引，则可以指定唯一聚集索引。</span><span class="sxs-lookup"><span data-stu-id="555d2-123">You can specify a unique clustered index if a clustered index on the table does not already exist.</span></span>  
  
     <span data-ttu-id="555d2-124">将索引创建为约束的一部分后，会自动将索引命名为与约束名称相同的名称。</span><span class="sxs-lookup"><span data-stu-id="555d2-124">An index created as part of the constraint is automatically given the same name as the constraint name.</span></span> <span data-ttu-id="555d2-125">有关详细信息，请参阅 [Primary and Foreign Key Constraints](../tables/primary-and-foreign-key-constraints.md) 和 [Unique Constraints and Check Constraints](../tables/unique-constraints-and-check-constraints.md)。</span><span class="sxs-lookup"><span data-stu-id="555d2-125">For more information, see [Primary and Foreign Key Constraints](../tables/primary-and-foreign-key-constraints.md) and [Unique Constraints and Check Constraints](../tables/unique-constraints-and-check-constraints.md).</span></span>  
  
-   <span data-ttu-id="555d2-126">**独立于约束的索引**</span><span class="sxs-lookup"><span data-stu-id="555d2-126">**Index independent of a constraint**</span></span>  
  
     <span data-ttu-id="555d2-127">指定非聚集主键约束后，您可以对非主键列的列创建聚集索引。</span><span class="sxs-lookup"><span data-stu-id="555d2-127">You can create a clustered index on a column other than primary key column if a nonclustered primary key constraint was specified.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="555d2-128">限制和局限</span><span class="sxs-lookup"><span data-stu-id="555d2-128">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="555d2-129">创建聚集索引结构后，旧（源）结构和新（目标）结构的各自的文件和文件组都需要磁盘空间。</span><span class="sxs-lookup"><span data-stu-id="555d2-129">When a clustered index structure is created, disk space for both the old (source) and new (target) structures is required in their respective files and filegroups.</span></span> <span data-ttu-id="555d2-130">在完成事务提交后，才会释放旧结构。</span><span class="sxs-lookup"><span data-stu-id="555d2-130">The old structure is not deallocated until the complete transaction commits.</span></span> <span data-ttu-id="555d2-131">排序也需要其他临时磁盘空间。</span><span class="sxs-lookup"><span data-stu-id="555d2-131">Additional temporary disk space for sorting may also be required.</span></span> <span data-ttu-id="555d2-132">有关详细信息，请参阅 [Disk Space Requirements for Index DDL Operations](disk-space-requirements-for-index-ddl-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="555d2-132">For more information, see [Disk Space Requirements for Index DDL Operations](disk-space-requirements-for-index-ddl-operations.md).</span></span>  
  
-   <span data-ttu-id="555d2-133">如果对具有多个现有非聚集索引的堆创建聚集索引，则必须重新生成所有非聚集索引，以使它们包含聚集键值而非行标识符 (RID)。</span><span class="sxs-lookup"><span data-stu-id="555d2-133">If a clustered index is created on a heap with several existing nonclustered indexes, all the nonclustered indexes must be rebuilt so that they contain the clustering key value instead of the row identifier (RID).</span></span> <span data-ttu-id="555d2-134">同样，如果删除具有多个非聚集索引的表的聚集索引，在 DROP 操作过程中，将重新生成非聚集索引。</span><span class="sxs-lookup"><span data-stu-id="555d2-134">Similarly, if a clustered index is dropped on a table that has several nonclustered indexes, the nonclustered indexes are all rebuilt as part of the DROP operation.</span></span> <span data-ttu-id="555d2-135">对于大型表，这可能需要很长时间。</span><span class="sxs-lookup"><span data-stu-id="555d2-135">This may take significant time on large tables.</span></span>  
  
     <span data-ttu-id="555d2-136">对大型表创建索引的首选方法是先创建聚集索引，然后创建任何非聚集索引。</span><span class="sxs-lookup"><span data-stu-id="555d2-136">The preferred way to build indexes on large tables is to start with the clustered index and then build any nonclustered indexes.</span></span> <span data-ttu-id="555d2-137">在对现有表创建索引时，请考虑将 ONLINE 选项设置为 ON。</span><span class="sxs-lookup"><span data-stu-id="555d2-137">Consider setting the ONLINE option to ON when you create indexes on existing tables.</span></span> <span data-ttu-id="555d2-138">如果设置为 ON，则不会持有长期表锁。</span><span class="sxs-lookup"><span data-stu-id="555d2-138">When set to ON, long-term table locks are not held.</span></span> <span data-ttu-id="555d2-139">这使对基础表的查询或更新可以继续进行。</span><span class="sxs-lookup"><span data-stu-id="555d2-139">This enables queries or updates to the underlying table to continue.</span></span> <span data-ttu-id="555d2-140">有关详细信息，请参阅 [Perform Index Operations Online](perform-index-operations-online.md)。</span><span class="sxs-lookup"><span data-stu-id="555d2-140">For more information, see [Perform Index Operations Online](perform-index-operations-online.md).</span></span>  
  
-   <span data-ttu-id="555d2-141">聚集索引的索引键不能包含在 ROW_OVERFLOW_DATA 分配单元中具有现有数据的 `varchar` 列。</span><span class="sxs-lookup"><span data-stu-id="555d2-141">The index key of a clustered index cannot contain `varchar` columns that have existing data in the ROW_OVERFLOW_DATA allocation unit.</span></span> <span data-ttu-id="555d2-142">如果对 `varchar` 列创建了聚集索引，并且在 IN_ROW_DATA 分配单元中存在现有数据，则对该列执行的将数据推送到行外的后续插入或更新操作将会失败。</span><span class="sxs-lookup"><span data-stu-id="555d2-142">If a clustered index is created on a `varchar` column and the existing data is in the IN_ROW_DATA allocation unit, subsequent insert or update actions on the column that would push the data off-row will fail.</span></span> <span data-ttu-id="555d2-143">若要获得有关可能包含行溢出数据的表的信息，请使用 [sys.dm_db_index_physical_stats (Transact-SQL) ](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql) 动态管理函数。</span><span class="sxs-lookup"><span data-stu-id="555d2-143">To obtain information about tables that might contain row-overflow data, use the [sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql) dynamic management function.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="555d2-144">Security</span><span class="sxs-lookup"><span data-stu-id="555d2-144">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="555d2-145">权限</span><span class="sxs-lookup"><span data-stu-id="555d2-145">Permissions</span></span>  
 <span data-ttu-id="555d2-146">要求对表或视图具有 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="555d2-146">Requires ALTER permission on the table or view.</span></span> <span data-ttu-id="555d2-147">用户必须是 **sysadmin** 固定服务器角色的成员，或者是 **db_ddladmin** 和 **db_owner** 固定数据库角色的成员。</span><span class="sxs-lookup"><span data-stu-id="555d2-147">User must be a member of the **sysadmin** fixed server role or the **db_ddladmin** and **db_owner** fixed database roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="555d2-148">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="555d2-148">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-clustered-index-by-using-object-explorer"></a><span data-ttu-id="555d2-149">使用对象资源管理器创建聚集索引</span><span class="sxs-lookup"><span data-stu-id="555d2-149">To create a clustered index by using Object Explorer</span></span>  
  
1.  <span data-ttu-id="555d2-150">在“对象资源管理器”中，展开要创建聚集索引的表。</span><span class="sxs-lookup"><span data-stu-id="555d2-150">In Object Explorer, expand the table on which you want to create a clustered index.</span></span>  
  
2.  <span data-ttu-id="555d2-151">右键单击“索引”文件夹，指向“新建索引”，然后选择“聚集索引…”    。</span><span class="sxs-lookup"><span data-stu-id="555d2-151">Right-click the **Indexes** folder, point to **New Index**, and select **Clustered Index...**.</span></span>  
  
3.  <span data-ttu-id="555d2-152">在 **“新建索引”** 对话框的 **“常规”** 页中，在 **“索引名称”** 框中输入新索引的名称。</span><span class="sxs-lookup"><span data-stu-id="555d2-152">In the **New Index** dialog box, on the **General** page, enter the name of the new index in the **Index name** box.</span></span>  
  
4.  <span data-ttu-id="555d2-153">在“索引键列”下，单击“添加…”   。</span><span class="sxs-lookup"><span data-stu-id="555d2-153">Under **Index key columns**, click **Add...**.</span></span>  
  
5.  <span data-ttu-id="555d2-154">在 "**从**_Table_name_中选择列" 对话框中，选中要添加到聚集索引的表列的复选框。</span><span class="sxs-lookup"><span data-stu-id="555d2-154">In the **Select Columns from**_table_name_ dialog box, select the check box of the table column to be added to the clustered index.</span></span>  
  
6.  <span data-ttu-id="555d2-155">单击“确定”。 </span><span class="sxs-lookup"><span data-stu-id="555d2-155">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="555d2-156">在 **“新建索引”** 对话框中，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="555d2-156">In the **New Index** dialog box, click **OK**.</span></span>  
  
#### <a name="to-create-a-clustered-index-by-using-the-table-designer"></a><span data-ttu-id="555d2-157">使用表设计器创建聚集索引</span><span class="sxs-lookup"><span data-stu-id="555d2-157">To create a clustered index by using the Table Designer</span></span>  
  
1.  <span data-ttu-id="555d2-158">在“对象资源管理器”中，展开要使用聚集索引创建表的数据库。</span><span class="sxs-lookup"><span data-stu-id="555d2-158">In Object Explorer, expand the database on which you want to create a table with a clustered index.</span></span>  
  
2.  <span data-ttu-id="555d2-159">右键单击“表”文件夹，然后单击“新建表…”   。</span><span class="sxs-lookup"><span data-stu-id="555d2-159">Right-click the **Tables** folder and click **New Table...**.</span></span>  
  
3.  <span data-ttu-id="555d2-160">按常规方式创建新表。</span><span class="sxs-lookup"><span data-stu-id="555d2-160">Create a new table as you normally would.</span></span> <span data-ttu-id="555d2-161">有关详细信息，请参阅[创建表（数据库引擎）](../tables/create-tables-database-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="555d2-161">For more information, see [Create Tables &#40;Database Engine&#41;](../tables/create-tables-database-engine.md).</span></span>  
  
4.  <span data-ttu-id="555d2-162">右键单击上面创建的新表，然后单击“设计”  。</span><span class="sxs-lookup"><span data-stu-id="555d2-162">Right-click the new table created above and click **Design**.</span></span>  
  
5.  <span data-ttu-id="555d2-163">在“表设计器”  菜单上，单击“索引/键”  。</span><span class="sxs-lookup"><span data-stu-id="555d2-163">On the **Table Designer** menu, click **Indexes/Keys**.</span></span>  
  
6.  <span data-ttu-id="555d2-164">在“索引/键”  对话框中，单击“添加”  。</span><span class="sxs-lookup"><span data-stu-id="555d2-164">In the **Indexes/Keys** dialog box, click **Add**.</span></span>  
  
7.  <span data-ttu-id="555d2-165">从“选定的主/唯一键或索引”  文本框中选择新索引。</span><span class="sxs-lookup"><span data-stu-id="555d2-165">Select the new index in the **Selected Primary/Unique Key or Index** text box.</span></span>  
  
8.  <span data-ttu-id="555d2-166">在网格中，选择“创建为聚集”  ，然后从该属性右侧的下拉列表中选择“是”  。</span><span class="sxs-lookup"><span data-stu-id="555d2-166">In the grid, select **Create as Clustered**, and choose **Yes** from the drop-down list to the right of the property.</span></span>  
  
9. <span data-ttu-id="555d2-167">单击“关闭”  。</span><span class="sxs-lookup"><span data-stu-id="555d2-167">Click **Close**.</span></span>  
  
10. <span data-ttu-id="555d2-168">在“文件”\*\*\*\* 菜单上，单击“保存”\*\*\*\* 以保存 _table_name_。</span><span class="sxs-lookup"><span data-stu-id="555d2-168">On the **File** menu, click **Save**_table_name_.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="555d2-169">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="555d2-169">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-clustered-index"></a><span data-ttu-id="555d2-170">创建聚集索引</span><span class="sxs-lookup"><span data-stu-id="555d2-170">To create a clustered index</span></span>  
  
1.  <span data-ttu-id="555d2-171">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="555d2-171">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="555d2-172">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="555d2-172">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="555d2-173">将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。</span><span class="sxs-lookup"><span data-stu-id="555d2-173">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Create a new table with three columns.  
    CREATE TABLE dbo.TestTable  
        (TestCol1 int NOT NULL,  
         TestCol2 nchar(10) NULL,  
         TestCol3 nvarchar(50) NULL);  
    GO  
    -- Create a clustered index called IX_TestTable_TestCol1  
    -- on the dbo.TestTable table using the TestCol1 column.  
    CREATE CLUSTERED INDEX IX_TestTable_TestCol1   
        ON dbo.TestTable (TestCol1);   
    GO  
    ```  
  
 <span data-ttu-id="555d2-174">有关详细信息，请参阅 [CREATE INDEX (Transact-SQL)](/sql/t-sql/statements/create-index-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="555d2-174">For more information, see [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="555d2-175">另请参阅</span><span class="sxs-lookup"><span data-stu-id="555d2-175">See Also</span></span>  
 <span data-ttu-id="555d2-176">[创建主键](../tables/create-primary-keys.md) </span><span class="sxs-lookup"><span data-stu-id="555d2-176">[Create Primary Keys](../tables/create-primary-keys.md) </span></span>  
 [<span data-ttu-id="555d2-177">创建唯一约束</span><span class="sxs-lookup"><span data-stu-id="555d2-177">Create Unique Constraints</span></span>](../tables/create-unique-constraints.md)  
  
  
