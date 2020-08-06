---
title: Visual Database Tools)  ("索引和键" 对话框 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:65539
- vdt.ppg.indexeskeys
ms.assetid: 9e4060ba-80c3-468f-bccb-e12e99f672c2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 68c9022f3ea7803f372e7c349e0dc75b1fc56adc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576473"
---
# <a name="indexes-and-keys-dialog-box-visual-database-tools"></a><span data-ttu-id="1f120-102">“索引和键”对话框 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="1f120-102">Indexes and Keys Dialog Box (Visual Database Tools)</span></span>
  <span data-ttu-id="1f120-103">使用此对话框可以创建或修改索引、主键和唯一键。</span><span class="sxs-lookup"><span data-stu-id="1f120-103">Use this dialog box to create or modify indexes, primary keys, and unique keys.</span></span> <span data-ttu-id="1f120-104">若要访问此对话框，请打开具有索引或键的表定义，右键单击表定义网格，再单击“索引/键”  。</span><span class="sxs-lookup"><span data-stu-id="1f120-104">To access this dialog box, open the table definition for the table with the index or key, right-click the table definition grid, and then click **Indexes/Keys**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1f120-105">如果表是为复制发布的，则必须使用 Transact-SQL 语句 [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) 或 SQL Server 管理对象 (SMO) 对架构进行更改。</span><span class="sxs-lookup"><span data-stu-id="1f120-105">If the table is published for replication, you must make schema changes using the Transact-SQL statement [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) or SQL Server Management Objects (SMO).</span></span> <span data-ttu-id="1f120-106">使用表设计器或数据库关系图设计器更改架构后，会尝试删除并重新创建表。</span><span class="sxs-lookup"><span data-stu-id="1f120-106">When schema changes are made using the Table Designer or the Database Diagram Designer, it attempts to drop and recreate the table.</span></span> <span data-ttu-id="1f120-107">由于您不能删除已发布的对象，因此架构更改将失败。</span><span class="sxs-lookup"><span data-stu-id="1f120-107">You cannot drop published objects, therefore the schema change will fail.</span></span>  
  
## <a name="options"></a><span data-ttu-id="1f120-108">选项</span><span class="sxs-lookup"><span data-stu-id="1f120-108">Options</span></span>  
 <span data-ttu-id="1f120-109">**选定的主/唯一键或索引**</span><span class="sxs-lookup"><span data-stu-id="1f120-109">**Selected Primary/Unique Key or Index**</span></span>  
 <span data-ttu-id="1f120-110">列出现有的主键/唯一键和索引。</span><span class="sxs-lookup"><span data-stu-id="1f120-110">Lists existing primary or unique keys and indexes.</span></span> <span data-ttu-id="1f120-111">选择其中任意一项可在右侧网格中显示其属性。</span><span class="sxs-lookup"><span data-stu-id="1f120-111">Select one to show its properties in the grid to the right.</span></span> <span data-ttu-id="1f120-112">如果该列表为空，则表示尚未为该表定义任何 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="1f120-112">If the list is empty, none have been defined for the table.</span></span>  
  
 <span data-ttu-id="1f120-113">**添加**</span><span class="sxs-lookup"><span data-stu-id="1f120-113">**Add**</span></span>  
 <span data-ttu-id="1f120-114">创建新的主键/唯一键或索引。</span><span class="sxs-lookup"><span data-stu-id="1f120-114">Create a new primary or unique key or index.</span></span>  
  
 <span data-ttu-id="1f120-115">**删除**</span><span class="sxs-lookup"><span data-stu-id="1f120-115">**Delete**</span></span>  
 <span data-ttu-id="1f120-116">删除在“选定的主/唯一键或索引”  列表中所选的键或索引。</span><span class="sxs-lookup"><span data-stu-id="1f120-116">Delete the key or index selected in the **Selected Primary/Unique Key or Index** list.</span></span>  
  
 <span data-ttu-id="1f120-117">**常规类别**</span><span class="sxs-lookup"><span data-stu-id="1f120-117">**General Category**</span></span>  
 <span data-ttu-id="1f120-118">展开此项可显示属性“列”  、“是唯一的”  和“类型”  。</span><span class="sxs-lookup"><span data-stu-id="1f120-118">When expanded, shows the properties **Columns**, **Is Unique**, and **Type**.</span></span>  
  
 <span data-ttu-id="1f120-119">**“列”**</span><span class="sxs-lookup"><span data-stu-id="1f120-119">**Columns**</span></span>  
 <span data-ttu-id="1f120-120">列出键或索引中的列的所选排序顺序，并且通过此项可访问可在其中定义排序顺序的对话框。</span><span class="sxs-lookup"><span data-stu-id="1f120-120">Lists chosen sort orders for the columns in the key or index, and provides access to a dialog box where the sort orders can be defined.</span></span> <span data-ttu-id="1f120-121">若要显示该对话框，请单击“列”，再单击属性字段右侧显示的省略号 (…)  。</span><span class="sxs-lookup"><span data-stu-id="1f120-121">To display the dialog box, click **Columns** and then click the ellipsis button (...) that appears to the right of the property field.</span></span>  
  
 <span data-ttu-id="1f120-122">**是唯一的**</span><span class="sxs-lookup"><span data-stu-id="1f120-122">**Is Unique**</span></span>  
 <span data-ttu-id="1f120-123">指示输入到此索引或键中的数据是否必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="1f120-123">Indicates whether data entered into this index or key must be unique.</span></span> <span data-ttu-id="1f120-124">这不适用于 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="1f120-124">This is unavailable for XML Indexes.</span></span>  
  
 <span data-ttu-id="1f120-125">类型 </span><span class="sxs-lookup"><span data-stu-id="1f120-125">**Type**</span></span>  
 <span data-ttu-id="1f120-126">指定在“选定的主/唯一键或索引”  列表中所选的项是否为唯一键、主键或索引。</span><span class="sxs-lookup"><span data-stu-id="1f120-126">Specify whether the item selected in the **Selected Primary/Unique Key or Index** list is a unique key, a primary key, or an index.</span></span> <span data-ttu-id="1f120-127">此字段对于主键是只读的。</span><span class="sxs-lookup"><span data-stu-id="1f120-127">For primary keys this field is read-only.</span></span>  
  
 <span data-ttu-id="1f120-128">**标识类别**</span><span class="sxs-lookup"><span data-stu-id="1f120-128">**Identity Category**</span></span>  
 <span data-ttu-id="1f120-129">展开此项可显示“名称”  和“说明”  属性字段。</span><span class="sxs-lookup"><span data-stu-id="1f120-129">When expanded, it shows the property fields for **Name** and **Description**.</span></span>  
  
 <span data-ttu-id="1f120-130">**名称**</span><span class="sxs-lookup"><span data-stu-id="1f120-130">**Name**</span></span>  
 <span data-ttu-id="1f120-131">显示键或索引的名称。</span><span class="sxs-lookup"><span data-stu-id="1f120-131">Shows the name of the key or index.</span></span> <span data-ttu-id="1f120-132">在创建一个新索引时，将基于表设计器的活动窗口中的表为其指定默认名称。</span><span class="sxs-lookup"><span data-stu-id="1f120-132">When a new one is created, it is given a default name based on the table in the active window in Table Designer.</span></span> <span data-ttu-id="1f120-133">可随时更改名称。</span><span class="sxs-lookup"><span data-stu-id="1f120-133">You can change the name at any time.</span></span>  
  
 <span data-ttu-id="1f120-134">**说明**</span><span class="sxs-lookup"><span data-stu-id="1f120-134">**Description**</span></span>  
 <span data-ttu-id="1f120-135">提供一个描述键或索引的位置。</span><span class="sxs-lookup"><span data-stu-id="1f120-135">Provides a place to describe the key or index.</span></span> <span data-ttu-id="1f120-136">若要编写更详细的说明，请单击“说明”，再单击属性字段右侧显示的省略号按钮 (…)   。</span><span class="sxs-lookup"><span data-stu-id="1f120-136">To write a more detailed description, click **Description** and then click the ellipsis button (**...**) that appears to the right of the property field.</span></span> <span data-ttu-id="1f120-137">这可以提供一个更大的文本编写区域。</span><span class="sxs-lookup"><span data-stu-id="1f120-137">This provides a larger area in which to write text.</span></span>  
  
 <span data-ttu-id="1f120-138">**表设计器类别**</span><span class="sxs-lookup"><span data-stu-id="1f120-138">**Table Designer Category**</span></span>  
 <span data-ttu-id="1f120-139">展开此项可显示有关“创建为聚集的”  的信息。</span><span class="sxs-lookup"><span data-stu-id="1f120-139">When expanded, shows information for **Create as Clustered**.</span></span>  
  
 <span data-ttu-id="1f120-140">**创建为聚集的**</span><span class="sxs-lookup"><span data-stu-id="1f120-140">**Create as Clustered**</span></span>  
 <span data-ttu-id="1f120-141">指定创建聚集键或聚集索引。</span><span class="sxs-lookup"><span data-stu-id="1f120-141">Make the key or index clustered.</span></span> <span data-ttu-id="1f120-142">对于每个表只能创建一个聚集索引。</span><span class="sxs-lookup"><span data-stu-id="1f120-142">Only one clustered index is allowed on a table.</span></span> <span data-ttu-id="1f120-143">表中数据按聚集索引的顺序进行存储。</span><span class="sxs-lookup"><span data-stu-id="1f120-143">Data in the table is stored in the order of the clustered index.</span></span> <span data-ttu-id="1f120-144">有关详细信息，请参阅 [创建聚集索引](../../relational-databases/indexes/indexes.md) 和 [创建非聚集索引](../../relational-databases/indexes/create-nonclustered-indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="1f120-144">For more information, see [Create Clustered Indexes](../../relational-databases/indexes/indexes.md) and [Create Nonclustered Indexes](../../relational-databases/indexes/create-nonclustered-indexes.md).</span></span>  
  
 <span data-ttu-id="1f120-145">**数据空间规范**</span><span class="sxs-lookup"><span data-stu-id="1f120-145">**Data Space Specification**</span></span>  
 <span data-ttu-id="1f120-146">展开此项可显示有关“(数据空间类型)”  、“文件组或分区方案名称”  和“分区列列表”  的信息。</span><span class="sxs-lookup"><span data-stu-id="1f120-146">When expanded, shows information for **(Data Space Type)**, **Filegroup or Partition Scheme Name**, and **Partition Column List**.</span></span>  
  
 <span data-ttu-id="1f120-147">**(数据空间类型)**</span><span class="sxs-lookup"><span data-stu-id="1f120-147">**(Data Space Type)**</span></span>  
 <span data-ttu-id="1f120-148">指示此索引或键是属于文件组还是分区方案。</span><span class="sxs-lookup"><span data-stu-id="1f120-148">Indicates whether this index or key belongs to a file group or partition scheme.</span></span>  
  
 <span data-ttu-id="1f120-149">**文件组或分区方案名称**</span><span class="sxs-lookup"><span data-stu-id="1f120-149">**Filegroup or Partition Scheme Name**</span></span>  
 <span data-ttu-id="1f120-150">显示用于存储索引或键的文件组或分区方案的名称。</span><span class="sxs-lookup"><span data-stu-id="1f120-150">Shows the name of the file group or partition scheme on which it is stored.</span></span>  
  
 <span data-ttu-id="1f120-151">**分区列列表**</span><span class="sxs-lookup"><span data-stu-id="1f120-151">**Partition Column List**</span></span>  
 <span data-ttu-id="1f120-152">显示一个逗号分隔的列表，其中列出了参与分区列功能的各个列。</span><span class="sxs-lookup"><span data-stu-id="1f120-152">Displays a comma-separated list of columns that participate in the partition column function.</span></span> <span data-ttu-id="1f120-153">如果在“(数据空间类型)”  字段中选择了“文件组”，则此项不可用。</span><span class="sxs-lookup"><span data-stu-id="1f120-153">Unavailable if Filegroup is selected in the **(Data Space Type)** field.</span></span>  
  
 <span data-ttu-id="1f120-154">**填充规范**</span><span class="sxs-lookup"><span data-stu-id="1f120-154">**Fill Specification**</span></span>  
 <span data-ttu-id="1f120-155">展开此项可显示有关“填充因子”  和“填充索引”  的信息。</span><span class="sxs-lookup"><span data-stu-id="1f120-155">When expanded, shows information for **Fill Factor** and **Pad Index**.</span></span>  
  
 <span data-ttu-id="1f120-156">**填充因子**</span><span class="sxs-lookup"><span data-stu-id="1f120-156">**Fill Factor**</span></span>  
 <span data-ttu-id="1f120-157">指定系统在索引叶级页中能够填充的空间百分比。</span><span class="sxs-lookup"><span data-stu-id="1f120-157">Specifies what percentage of the index's leaf-level pages the system can fill.</span></span> <span data-ttu-id="1f120-158">一旦页面已满，系统就必须拆分页面以添加新数据，因而会影响性能。</span><span class="sxs-lookup"><span data-stu-id="1f120-158">Once a page is full, the system must split the pages to add new data, impairing performance.</span></span>  
  
-   <span data-ttu-id="1f120-159">值为 100 表示页面将填满。</span><span class="sxs-lookup"><span data-stu-id="1f120-159">A value of 100 means the pages will be full.</span></span> <span data-ttu-id="1f120-160">此时需要的存储空间量最小。</span><span class="sxs-lookup"><span data-stu-id="1f120-160">This will require the least amount of storage space.</span></span> <span data-ttu-id="1f120-161">只有在不会对数据进行更改时（例如，对于只读表），才可以使用此设置。</span><span class="sxs-lookup"><span data-stu-id="1f120-161">This setting should be used only when there will be no changes to the data, for example, on a read-only table.</span></span>  
  
-   <span data-ttu-id="1f120-162">值越小，数据页上的可用空间就越大。</span><span class="sxs-lookup"><span data-stu-id="1f120-162">A lower value leaves more empty space on the data pages.</span></span> <span data-ttu-id="1f120-163">这样可以减少在索引增长过程中对数据页进行拆分的需要，但需要更大的存储空间。</span><span class="sxs-lookup"><span data-stu-id="1f120-163">This reduces the need to split data pages as indexes grow but requires more storage space.</span></span>  
  
 <span data-ttu-id="1f120-164">**填充索引**</span><span class="sxs-lookup"><span data-stu-id="1f120-164">**Pad Index**</span></span>  
 <span data-ttu-id="1f120-165">指示此索引中的中间页在增长过程中是否使用与在“填充因子”  中指定的百分比相同的可用空间（填充）百分比设置。</span><span class="sxs-lookup"><span data-stu-id="1f120-165">Indicate whether intermediate pages in this index are provided the same percentage of empty space (padding) specified in **Fill Factor** when they grow.</span></span>  
  
 <span data-ttu-id="1f120-166">**忽略重复的键**</span><span class="sxs-lookup"><span data-stu-id="1f120-166">**Ignore Duplicate Keys**</span></span>  
 <span data-ttu-id="1f120-167">指定在大容量插入操作过程中插入具有与现有键值相同的键值的行时的行为。</span><span class="sxs-lookup"><span data-stu-id="1f120-167">Specify what happens when a row is inserted during a bulk insert operation whose key value equals an existing key value.</span></span> <span data-ttu-id="1f120-168">如果选择：</span><span class="sxs-lookup"><span data-stu-id="1f120-168">If you choose:</span></span>  
  
-   <span data-ttu-id="1f120-169">**是**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 将发出警告，忽略有问题的传入行，并尝试插入剩余行。</span><span class="sxs-lookup"><span data-stu-id="1f120-169">**Yes** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] issues a warning, ignores the offending incoming row, and tries to insert the remaining rows.</span></span>  
  
-   <span data-ttu-id="1f120-170">**否**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 将发出错误信息并回滚整个大容量插入操作。</span><span class="sxs-lookup"><span data-stu-id="1f120-170">**No** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] issues an error message and rolls back the entire bulk insert operation.</span></span>  
  
 <span data-ttu-id="1f120-171">**包含列**</span><span class="sxs-lookup"><span data-stu-id="1f120-171">**Included Columns**</span></span>  
 <span data-ttu-id="1f120-172">显示一个用逗号分隔的列表，其中列出用于组成索引键的所有列的名称。</span><span class="sxs-lookup"><span data-stu-id="1f120-172">Displays a comma-separated list of the names of all the columns that constitute the index key.</span></span> <span data-ttu-id="1f120-173">只能为非聚集索引指定子键列。</span><span class="sxs-lookup"><span data-stu-id="1f120-173">Subkey columns can only be specified for nonclustered indexes.</span></span> <span data-ttu-id="1f120-174">此属性对 XML 索引是隐藏的。</span><span class="sxs-lookup"><span data-stu-id="1f120-174">This property is hidden for XML indexes.</span></span>  
  
 <span data-ttu-id="1f120-175">**已禁用**</span><span class="sxs-lookup"><span data-stu-id="1f120-175">**Is Disabled**</span></span>  
 <span data-ttu-id="1f120-176">指示是否禁用此索引。</span><span class="sxs-lookup"><span data-stu-id="1f120-176">Indicates whether this index is disabled.</span></span> <span data-ttu-id="1f120-177">这是只读属性。</span><span class="sxs-lookup"><span data-stu-id="1f120-177">This is a read-only property.</span></span> <span data-ttu-id="1f120-178">只有在 Visual Database tools 之外禁用了索引，此属性才可设置为“是”  。</span><span class="sxs-lookup"><span data-stu-id="1f120-178">This property is only set to **Yes** if the index has been disabled outside of the Visual Database tools.</span></span>  
  
 <span data-ttu-id="1f120-179">**为全文本键**</span><span class="sxs-lookup"><span data-stu-id="1f120-179">**Is Full-Text Key**</span></span>  
 <span data-ttu-id="1f120-180">指定此索引是否为全文本键。</span><span class="sxs-lookup"><span data-stu-id="1f120-180">Specify whether this index is a full-text key.</span></span> <span data-ttu-id="1f120-181">有关全文本键的详细信息，请参阅 SQL Server 联机丛书。</span><span class="sxs-lookup"><span data-stu-id="1f120-181">For more information on full-text keys, see SQL Server Books Online.</span></span> <span data-ttu-id="1f120-182">此属性对 XML 索引是隐藏的。</span><span class="sxs-lookup"><span data-stu-id="1f120-182">This property is hidden for XML indexes.</span></span>  
  
 <span data-ttu-id="1f120-183">**允许页锁定**</span><span class="sxs-lookup"><span data-stu-id="1f120-183">**Page Locks Allowed**</span></span>  
 <span data-ttu-id="1f120-184">指定对此索引是否允许页级锁定。</span><span class="sxs-lookup"><span data-stu-id="1f120-184">Specify whether page-level locking is allowed on this index.</span></span> <span data-ttu-id="1f120-185">允许或禁用页级锁定会影响数据库性能。</span><span class="sxs-lookup"><span data-stu-id="1f120-185">Allowing or disallowing page-level locking affects database performance.</span></span> <span data-ttu-id="1f120-186">建议设置为“是”  。</span><span class="sxs-lookup"><span data-stu-id="1f120-186">The recommended setting is **Yes**.</span></span>  
  
 <span data-ttu-id="1f120-187">**重新计算统计数据**</span><span class="sxs-lookup"><span data-stu-id="1f120-187">**Re-compute Statistics**</span></span>  
 <span data-ttu-id="1f120-188">指定在创建索引后，基础 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 是否计算新的统计数据。</span><span class="sxs-lookup"><span data-stu-id="1f120-188">Specify whether the underlying [!INCLUDE[ssDE](../../includes/ssde-md.md)] computes new statistics when the index is created.</span></span> <span data-ttu-id="1f120-189">重新计算统计数据会降低索引的生成速度，但很有可能提高查询性能。</span><span class="sxs-lookup"><span data-stu-id="1f120-189">Re-computing statistics slows the building of indexes but will very likely improve query performance.</span></span>  
  
 <span data-ttu-id="1f120-190">**允许行锁定**</span><span class="sxs-lookup"><span data-stu-id="1f120-190">**Row Locks Allowed**</span></span>  
 <span data-ttu-id="1f120-191">指定对此索引是否允许行级锁定。</span><span class="sxs-lookup"><span data-stu-id="1f120-191">Specify whether row-level locking is allowed on this index.</span></span> <span data-ttu-id="1f120-192">允许或禁用行级锁定会影响数据库性能。</span><span class="sxs-lookup"><span data-stu-id="1f120-192">Allowing or disallowing row-level locking affects database performance.</span></span> <span data-ttu-id="1f120-193">建议设置为“是”  。</span><span class="sxs-lookup"><span data-stu-id="1f120-193">The recommended setting is **Yes**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f120-194">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1f120-194">See Also</span></span>  
 <span data-ttu-id="1f120-195">[Unique 约束和 Check 约束](../../relational-databases/tables/unique-constraints-and-check-constraints.md) </span><span class="sxs-lookup"><span data-stu-id="1f120-195">[Unique Constraints and Check Constraints](../../relational-databases/tables/unique-constraints-and-check-constraints.md) </span></span>  
 [<span data-ttu-id="1f120-196">主键和外键约束</span><span class="sxs-lookup"><span data-stu-id="1f120-196">Primary and Foreign Key Constraints</span></span>](../../relational-databases/tables/primary-and-foreign-key-constraints.md)  
  
  
