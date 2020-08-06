---
title: 索引属性 F1 帮助 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
f1_keywords:
- sql12.swb.indexproperties.storage.f1
- sql12.swb.indexproperties.columns.f1
- sql12.swb.indexproperties.partitions.f1
- sql12.swb.indexproperties.general.f1
- sql12.swb.indexproperties.filter.f1
- sql12.swb.indexproperties.options.f1
- sql12.swb.indexproperties.spatial.f1
ms.assetid: 45efd81a-3796-4b04-b0cc-f3deec94c733
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 390a63d21dc72e052017f2d30b061d71de863bc1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693859"
---
# <a name="index-properties-f1-help"></a><span data-ttu-id="06f59-102">“索引属性”对话框的 F1 帮助</span><span class="sxs-lookup"><span data-stu-id="06f59-102">Index Properties F1 Help</span></span>
  <span data-ttu-id="06f59-103">本主题中的这部分引用了使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 对话框提供的各种索引属性。</span><span class="sxs-lookup"><span data-stu-id="06f59-103">The sections in this topic refer to various index properties that are available by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] dialogs.</span></span>  
  
 <span data-ttu-id="06f59-104">**本主题内容：**</span><span class="sxs-lookup"><span data-stu-id="06f59-104">**In This Topic:**</span></span>  
  
 [<span data-ttu-id="06f59-105">索引属性常规页</span><span class="sxs-lookup"><span data-stu-id="06f59-105">Index Properties General Page</span></span>](#General)  
  
 [<span data-ttu-id="06f59-106">用于为索引选择列的对话框</span><span class="sxs-lookup"><span data-stu-id="06f59-106">Select (Index) Columns Dialog Box</span></span>](#Columns)  
  
 [<span data-ttu-id="06f59-107">索引属性存储页</span><span class="sxs-lookup"><span data-stu-id="06f59-107">Index Properties Storage Page</span></span>](#Storage)  
  
 [<span data-ttu-id="06f59-108">索引属性空间页</span><span class="sxs-lookup"><span data-stu-id="06f59-108">Index Properties Spatial Page</span></span>](#Spatial)  
  
 [<span data-ttu-id="06f59-109">索引属性筛选器页</span><span class="sxs-lookup"><span data-stu-id="06f59-109">Index Properties Filter Page</span></span>](#Filter)  
  
##  <a name="index-properties-general-page"></a><a name="General"></a> <span data-ttu-id="06f59-110">索引属性常规页</span><span class="sxs-lookup"><span data-stu-id="06f59-110">Index Properties General Page</span></span>  
 <span data-ttu-id="06f59-111">使用“常规”页可以查看或修改所选表或视图的索引属性。</span><span class="sxs-lookup"><span data-stu-id="06f59-111">Use the General page to view or modify index properties for the selected table or view.</span></span> <span data-ttu-id="06f59-112">每一页上的选项可基于所选索引的类型更改。</span><span class="sxs-lookup"><span data-stu-id="06f59-112">The options for each page may change based on the type of index selected.</span></span>  
  
 <span data-ttu-id="06f59-113">**表名称**</span><span class="sxs-lookup"><span data-stu-id="06f59-113">**Table name**</span></span>  
 <span data-ttu-id="06f59-114">显示创建索引的表或视图的名称。</span><span class="sxs-lookup"><span data-stu-id="06f59-114">Displays the name of the table or view that the index was created on.</span></span> <span data-ttu-id="06f59-115">此字段为只读。</span><span class="sxs-lookup"><span data-stu-id="06f59-115">This field is read-only.</span></span> <span data-ttu-id="06f59-116">若要选择不同的表，请关闭“索引属性”页，选择适当的表，然后再次打开“索引属性”页。</span><span class="sxs-lookup"><span data-stu-id="06f59-116">To select a different table, close the Index Properties page, select the correct table, and then open the Index Properties page again.</span></span>  
  
 <span data-ttu-id="06f59-117">不能对索引视图指定空间索引。</span><span class="sxs-lookup"><span data-stu-id="06f59-117">Spatial indexes cannot be specified on indexed views.</span></span> <span data-ttu-id="06f59-118">仅可为具有主键的表定义空间索引。</span><span class="sxs-lookup"><span data-stu-id="06f59-118">Spatial indexes can be defined only for a table that has a primary key.</span></span> <span data-ttu-id="06f59-119">表中主键列的最大数目为 15。</span><span class="sxs-lookup"><span data-stu-id="06f59-119">The maximum number of primary key columns on the table is 15.</span></span> <span data-ttu-id="06f59-120">复合主键列的每行大小限制在最多 895 个字节。</span><span class="sxs-lookup"><span data-stu-id="06f59-120">The combined per-row size of the primary-key columns is limited to a maximum of 895 bytes.</span></span>  
  
 <span data-ttu-id="06f59-121">**索引名称**</span><span class="sxs-lookup"><span data-stu-id="06f59-121">**Index name**</span></span>  
 <span data-ttu-id="06f59-122">显示索引的名称。</span><span class="sxs-lookup"><span data-stu-id="06f59-122">Displays the name of the index.</span></span> <span data-ttu-id="06f59-123">对于现有索引，此字段是只读的。</span><span class="sxs-lookup"><span data-stu-id="06f59-123">This field is read-only for an existing index.</span></span> <span data-ttu-id="06f59-124">在创建新的索引时，请键入索引的名称。</span><span class="sxs-lookup"><span data-stu-id="06f59-124">When creating a new index, type the name of the index.</span></span>  
  
 <span data-ttu-id="06f59-125">**索引类型**</span><span class="sxs-lookup"><span data-stu-id="06f59-125">**Index type**</span></span>  
 <span data-ttu-id="06f59-126">指示索引的类型。</span><span class="sxs-lookup"><span data-stu-id="06f59-126">Indicates the type of index.</span></span> <span data-ttu-id="06f59-127">对于新索引，指示在打开该对话框时所选索引的类型。</span><span class="sxs-lookup"><span data-stu-id="06f59-127">For new indexes, indicates the type of index selected when opening the dialog box.</span></span> <span data-ttu-id="06f59-128">索引可以是：“聚集”、“非聚集”、“主 XML”、“辅助 XML”、“空间”、“聚集列存储”或“非聚集列存储”      。</span><span class="sxs-lookup"><span data-stu-id="06f59-128">Indexes can be: **Clustered**, **Nonclustered**, **Primary XML**, **Secondary XML**, **Spatial**, **Clustered columnstore**, or **Nonclustered Columnstore**.</span></span>  
  
 <span data-ttu-id="06f59-129">**注意** 每个表只允许创建一个聚集索引。</span><span class="sxs-lookup"><span data-stu-id="06f59-129">**Note** Only one clustered index is allowed for each table.</span></span> <span data-ttu-id="06f59-130">每个表只允许创建一个 xVelocity 内存优化的列存储索引。</span><span class="sxs-lookup"><span data-stu-id="06f59-130">Only one xVelocity memory optimized columnstore index is allowed for each table.</span></span>  
  
 <span data-ttu-id="06f59-131">**唯一**</span><span class="sxs-lookup"><span data-stu-id="06f59-131">**Unique**</span></span>  
 <span data-ttu-id="06f59-132">选中此复选框可使该索引成为唯一索引。</span><span class="sxs-lookup"><span data-stu-id="06f59-132">Selecting this check box makes the index unique.</span></span> <span data-ttu-id="06f59-133">不允许两行具有相同的索引值。</span><span class="sxs-lookup"><span data-stu-id="06f59-133">No two rows are permitted to have the same index value.</span></span> <span data-ttu-id="06f59-134">默认情况下，此复选框处于未选中状态。</span><span class="sxs-lookup"><span data-stu-id="06f59-134">By default, this check box is cleared.</span></span> <span data-ttu-id="06f59-135">如果两行具有相同的值，在修改现有索引时，索引创建将会失败。</span><span class="sxs-lookup"><span data-stu-id="06f59-135">When modifying an existing index, index creation will fail if two rows have the same value.</span></span> <span data-ttu-id="06f59-136">对于允许 NULL 的列，唯一索引允许为 NULL 值。</span><span class="sxs-lookup"><span data-stu-id="06f59-136">For columns where NULL is permitted, a unique index permits one NULL value.</span></span>  
  
 <span data-ttu-id="06f59-137">如果在 **“索引类型”** 字段中选择 **“空间”** ，则 **“唯一”** 复选框呈灰色。</span><span class="sxs-lookup"><span data-stu-id="06f59-137">If you select **Spatial** in the **Index type** field, the **Unique** check box is dimmed.</span></span>  
  
 <span data-ttu-id="06f59-138">**索引键列**</span><span class="sxs-lookup"><span data-stu-id="06f59-138">**Index key columns**</span></span>  
 <span data-ttu-id="06f59-139">向 **“索引键列”** 网格中添加所需的列。</span><span class="sxs-lookup"><span data-stu-id="06f59-139">Add the desired columns to the **Index key columns** grid.</span></span> <span data-ttu-id="06f59-140">如果添加多列，则必须以所需的顺序列出这些列。</span><span class="sxs-lookup"><span data-stu-id="06f59-140">When more than one column is added, the columns must be listed in the order desired.</span></span> <span data-ttu-id="06f59-141">索引中的列顺序对索引的性能具有很大影响。</span><span class="sxs-lookup"><span data-stu-id="06f59-141">The column order in an index can have a great impact on the index performance.</span></span>  
  
 <span data-ttu-id="06f59-142">单个组合索引不能超过 16 列。</span><span class="sxs-lookup"><span data-stu-id="06f59-142">No more than 16 columns can participate in a single composite index.</span></span> <span data-ttu-id="06f59-143">如果超过 16 列，请参阅本文末尾的“包含列”。</span><span class="sxs-lookup"><span data-stu-id="06f59-143">For greater than 16 columns, see included columns at the end of this topic.</span></span>  
  
 <span data-ttu-id="06f59-144">只能对包含空间数据类型（ *空间列*）的单个列定义空间索引。</span><span class="sxs-lookup"><span data-stu-id="06f59-144">A spatial index can be defined only on a single column that contains a spatial data type (a *spatial column*).</span></span>  
  
 <span data-ttu-id="06f59-145">**名称**</span><span class="sxs-lookup"><span data-stu-id="06f59-145">**Name**</span></span>  
 <span data-ttu-id="06f59-146">显示组成索引键的列的名称。</span><span class="sxs-lookup"><span data-stu-id="06f59-146">Displays the name of the column that participates in the index key.</span></span>  
  
 <span data-ttu-id="06f59-147">**排序顺序**</span><span class="sxs-lookup"><span data-stu-id="06f59-147">**Sort Order**</span></span>  
 <span data-ttu-id="06f59-148">指定所选索引列的排序方向， **“升序”** 或 **“降序”** 。</span><span class="sxs-lookup"><span data-stu-id="06f59-148">Specifies the sort direction of the selected index column, either **Ascending** or **Descending**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="06f59-149">如果索引类型为 **“主 XML”** 或 **“空间”** ，则表中将不显示此列。</span><span class="sxs-lookup"><span data-stu-id="06f59-149">If the index type is **Primary XML** or **Spatial**, this column does not appear in the table.</span></span>  
  
 <span data-ttu-id="06f59-150">**数据类型**</span><span class="sxs-lookup"><span data-stu-id="06f59-150">**Data Type**</span></span>  
 <span data-ttu-id="06f59-151">显示数据类型信息。</span><span class="sxs-lookup"><span data-stu-id="06f59-151">Displays the data type information.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="06f59-152">如果表列为计算列，则 **“数据类型”** 显示“计算列”。</span><span class="sxs-lookup"><span data-stu-id="06f59-152">If the table column is a computed column, **Data type** displays "computed column."</span></span>  
  
 <span data-ttu-id="06f59-153">**大小**</span><span class="sxs-lookup"><span data-stu-id="06f59-153">**Size**</span></span>  
 <span data-ttu-id="06f59-154">显示存储列数据类型所需的最大字节数。</span><span class="sxs-lookup"><span data-stu-id="06f59-154">Displays the maximum number of bytes required to store the column data type.</span></span> <span data-ttu-id="06f59-155">对于空间列或 XML 列，显示零 (0)。</span><span class="sxs-lookup"><span data-stu-id="06f59-155">Displays zero (0) for a spatial or XML column.</span></span>  
  
 <span data-ttu-id="06f59-156">**标识**</span><span class="sxs-lookup"><span data-stu-id="06f59-156">**Identity**</span></span>  
 <span data-ttu-id="06f59-157">显示组成索引键的列是否为标识列。</span><span class="sxs-lookup"><span data-stu-id="06f59-157">Displays whether the column participating in the index key is an identity column.</span></span>  
  
 <span data-ttu-id="06f59-158">**允许 Null**</span><span class="sxs-lookup"><span data-stu-id="06f59-158">**Allow NULLs**</span></span>  
 <span data-ttu-id="06f59-159">显示组成索引键的列是否允许在表或视图列中存储 Null 值。</span><span class="sxs-lookup"><span data-stu-id="06f59-159">Displays whether the column participating in the index key allows NULL values to be stored in the table or view column.</span></span>  
  
 <span data-ttu-id="06f59-160">**添加**</span><span class="sxs-lookup"><span data-stu-id="06f59-160">**Add**</span></span>  
 <span data-ttu-id="06f59-161">向索引键添加列。</span><span class="sxs-lookup"><span data-stu-id="06f59-161">Adds a column to the index key.</span></span> <span data-ttu-id="06f59-162">从单击“添加”时显示的“从 \<table name> 中选择列”对话框中选择表列。</span><span class="sxs-lookup"><span data-stu-id="06f59-162">Select table columns from the **Select Columns from** *\<table name>* dialog box that appears when you click **Add**.</span></span> <span data-ttu-id="06f59-163">对于空间索引，在选择一列后，该按钮将呈灰色。</span><span class="sxs-lookup"><span data-stu-id="06f59-163">For a spatial index, after you select one column, this button is dimmed.</span></span>  
  
 <span data-ttu-id="06f59-164">**删除**</span><span class="sxs-lookup"><span data-stu-id="06f59-164">**Remove**</span></span>  
 <span data-ttu-id="06f59-165">从组成索引键的列中删除所选列。</span><span class="sxs-lookup"><span data-stu-id="06f59-165">Removes the selected column from participation in the index key.</span></span>  
  
 <span data-ttu-id="06f59-166">**上移**</span><span class="sxs-lookup"><span data-stu-id="06f59-166">**Move Up**</span></span>  
 <span data-ttu-id="06f59-167">在索引键网格中向上移动所选列。</span><span class="sxs-lookup"><span data-stu-id="06f59-167">Moves the selected column up in the index key grid.</span></span>  
  
 <span data-ttu-id="06f59-168">**“下移”**</span><span class="sxs-lookup"><span data-stu-id="06f59-168">**Move Down**</span></span>  
 <span data-ttu-id="06f59-169">在索引键网格中向下移动所选列。</span><span class="sxs-lookup"><span data-stu-id="06f59-169">Moves the selected column down in the index key grid.</span></span>  
  
 <span data-ttu-id="06f59-170">**列存储列**</span><span class="sxs-lookup"><span data-stu-id="06f59-170">**Columnstore columns**</span></span>  
 <span data-ttu-id="06f59-171">单击“添加”可为列存储索引选择列。</span><span class="sxs-lookup"><span data-stu-id="06f59-171">Click **Add** to select columns for the columnstore index.</span></span> <span data-ttu-id="06f59-172">有关列存储索引的限制，请参阅 [CREATE COLUMNSTORE INDEX (Transact-SQL)](/sql/t-sql/statements/create-columnstore-index-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="06f59-172">For limitations on a columnstore index, see [CREATE COLUMNSTORE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-columnstore-index-transact-sql).</span></span>  
  
 <span data-ttu-id="06f59-173">**包含列**</span><span class="sxs-lookup"><span data-stu-id="06f59-173">**Included columns**</span></span>  
 <span data-ttu-id="06f59-174">在非聚集索引中包含非键列。</span><span class="sxs-lookup"><span data-stu-id="06f59-174">Include nonkey columns in the nonclustered index.</span></span> <span data-ttu-id="06f59-175">使用此选项，您可以将列作为非键列添加到非聚集索引的叶级别中，从而跳过当前对索引键总大小的索引限制以及对构成索引键的最大列数的索引限制。</span><span class="sxs-lookup"><span data-stu-id="06f59-175">This option allows you to bypass the current index limits on the total size of an index key and the maximum number of columns participating in an index key by adding columns as nonkey columns in the leaf level of the nonclustered index.</span></span> <span data-ttu-id="06f59-176">有关详细信息，请参阅 [创建带有包含列的索引](create-indexes-with-included-columns.md)。</span><span class="sxs-lookup"><span data-stu-id="06f59-176">For more information, see [Create Indexes with Included Columns](create-indexes-with-included-columns.md)</span></span>  
  
##  <a name="select-index-columns-dialog-box"></a><a name="Columns"></a> <span data-ttu-id="06f59-177">用于为索引选择列的对话框</span><span class="sxs-lookup"><span data-stu-id="06f59-177">Select (Index) Columns Dialog Box</span></span>  
 <span data-ttu-id="06f59-178">在创建或修改索引时，使用此页可以向 **“索引属性常规”** 页中添加列。</span><span class="sxs-lookup"><span data-stu-id="06f59-178">Use this page to add columns to the **Index Properties General** page when creating or modifying an index.</span></span>  
  
 <span data-ttu-id="06f59-179">**复选框**</span><span class="sxs-lookup"><span data-stu-id="06f59-179">**Check box**</span></span>  
 <span data-ttu-id="06f59-180">选中复选框可添加列。</span><span class="sxs-lookup"><span data-stu-id="06f59-180">Select to add columns.</span></span>  
  
 <span data-ttu-id="06f59-181">**名称**</span><span class="sxs-lookup"><span data-stu-id="06f59-181">**Name**</span></span>  
 <span data-ttu-id="06f59-182">列的名称。</span><span class="sxs-lookup"><span data-stu-id="06f59-182">Name of the column.</span></span>  
  
 <span data-ttu-id="06f59-183">**数据类型**</span><span class="sxs-lookup"><span data-stu-id="06f59-183">**Data Type**</span></span>  
 <span data-ttu-id="06f59-184">列的数据类型。</span><span class="sxs-lookup"><span data-stu-id="06f59-184">The data type of the column.</span></span>  
  
 <span data-ttu-id="06f59-185">**字节**</span><span class="sxs-lookup"><span data-stu-id="06f59-185">**Bytes**</span></span>  
 <span data-ttu-id="06f59-186">列的大小（字节）。</span><span class="sxs-lookup"><span data-stu-id="06f59-186">The size of the column in bytes.</span></span>  
  
 <span data-ttu-id="06f59-187">**标识**</span><span class="sxs-lookup"><span data-stu-id="06f59-187">**Identity**</span></span>  
 <span data-ttu-id="06f59-188">对于标识列显示 **“是”** ；如果该列不是标识列，则显示 **“否”** 。</span><span class="sxs-lookup"><span data-stu-id="06f59-188">Displays **Yes** for identity columns, and **No** when the column is not an identity column.</span></span>  
  
 <span data-ttu-id="06f59-189">**允许 Null 值**</span><span class="sxs-lookup"><span data-stu-id="06f59-189">**Allow Nulls**</span></span>  
 <span data-ttu-id="06f59-190">如果表定义允许该列包含空值，则显示 **“是”** 。</span><span class="sxs-lookup"><span data-stu-id="06f59-190">Displays **Yes** when the table definition allows null values for the column.</span></span> <span data-ttu-id="06f59-191">如果表定义不允许该列包含 Null 值，则显示 **“否”** 。</span><span class="sxs-lookup"><span data-stu-id="06f59-191">Displays **No** when the table definition does not allow nulls for the column.</span></span>  
  
##  <a name="storage-page-options"></a><a name="Storage"></a> <span data-ttu-id="06f59-192">存储页选项</span><span class="sxs-lookup"><span data-stu-id="06f59-192">Storage Page Options</span></span>  
 <span data-ttu-id="06f59-193">使用此页可查看或修改所选索引的文件组或分区方案属性。</span><span class="sxs-lookup"><span data-stu-id="06f59-193">Use this page to view or modify filegroup or partition scheme properties for the selected index.</span></span> <span data-ttu-id="06f59-194">仅显示与索引类型相关的选项。</span><span class="sxs-lookup"><span data-stu-id="06f59-194">Only shows options related to the type of index.</span></span>  
  
 <span data-ttu-id="06f59-195">**文件组**</span><span class="sxs-lookup"><span data-stu-id="06f59-195">**Filegroup**</span></span>  
 <span data-ttu-id="06f59-196">在指定的文件组中存储索引。</span><span class="sxs-lookup"><span data-stu-id="06f59-196">Stores the index in the specified filegroup.</span></span> <span data-ttu-id="06f59-197">该列表仅显示标准 (row) 文件组。</span><span class="sxs-lookup"><span data-stu-id="06f59-197">The list only displays standard (row) filegroups.</span></span> <span data-ttu-id="06f59-198">默认情况下，将在该列表中选择相应数据库的 PRIMARY 文件组。</span><span class="sxs-lookup"><span data-stu-id="06f59-198">The default list selection is the PRIMARY filegroup of the database.</span></span> <span data-ttu-id="06f59-199">有关详细信息，请参阅 [数据库文件和文件组](../databases/database-files-and-filegroups.md)。</span><span class="sxs-lookup"><span data-stu-id="06f59-199">For more information, see [Database Files and Filegroups](../databases/database-files-and-filegroups.md).</span></span>  
  
 <span data-ttu-id="06f59-200">**Filestream 文件组**</span><span class="sxs-lookup"><span data-stu-id="06f59-200">**Filestream filegroup**</span></span>  
 <span data-ttu-id="06f59-201">指定 FILESTREAM 数据的文件组。</span><span class="sxs-lookup"><span data-stu-id="06f59-201">Specifies the filegroup for FILESTREAM data.</span></span> <span data-ttu-id="06f59-202">该列表仅显示 FILESTREAM 文件组。</span><span class="sxs-lookup"><span data-stu-id="06f59-202">This list displays only FILESTREAM filegroups.</span></span> <span data-ttu-id="06f59-203">默认情况下，将在该列表中选择 PRIMARY FILESTREAM 文件组。</span><span class="sxs-lookup"><span data-stu-id="06f59-203">The default list selection is the PRIMARY FILESTREAM filegroup.</span></span> <span data-ttu-id="06f59-204">有关详细信息，请参阅 [FILESTREAM (SQL Server)](../blob/filestream-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="06f59-204">For more information, see [FILESTREAM &#40;SQL Server&#41;](../blob/filestream-sql-server.md).</span></span>  
  
 <span data-ttu-id="06f59-205">**分区方案**</span><span class="sxs-lookup"><span data-stu-id="06f59-205">**Partition scheme**</span></span>  
 <span data-ttu-id="06f59-206">在分区方案中存储索引。</span><span class="sxs-lookup"><span data-stu-id="06f59-206">Stores the index in a partition scheme.</span></span> <span data-ttu-id="06f59-207">单击 **“分区方案”** 可启用下面的网格。</span><span class="sxs-lookup"><span data-stu-id="06f59-207">Clicking **Partition Scheme** enables the grid below.</span></span> <span data-ttu-id="06f59-208">默认情况下，将在该列表中选择用于存储表数据的分区方案。</span><span class="sxs-lookup"><span data-stu-id="06f59-208">The default list selection is the partition scheme that is used for storing the table data.</span></span> <span data-ttu-id="06f59-209">在列表中选择其他分区方案将更新该网格中的信息。</span><span class="sxs-lookup"><span data-stu-id="06f59-209">When you select a different partition scheme in the list, the information in the grid is updated.</span></span> <span data-ttu-id="06f59-210">有关详细信息，请参阅 [Partitioned Tables and Indexes](../partitions/partitioned-tables-and-indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="06f59-210">For more information, see [Partitioned Tables and Indexes](../partitions/partitioned-tables-and-indexes.md).</span></span>  
  
 <span data-ttu-id="06f59-211">如果数据库中没有分区方案，则分区方案选项不可用。</span><span class="sxs-lookup"><span data-stu-id="06f59-211">The partition scheme option is unavailable if there are no partition schemes in the database.</span></span>  
  
 <span data-ttu-id="06f59-212">**Filestream 分区方案**</span><span class="sxs-lookup"><span data-stu-id="06f59-212">**Filestream partition scheme**</span></span>  
 <span data-ttu-id="06f59-213">指定 FILESTREAM 数据的分区方案。</span><span class="sxs-lookup"><span data-stu-id="06f59-213">Specifies the partition scheme for FILESTREAM data.</span></span> <span data-ttu-id="06f59-214">分区方案必须与 **“分区方案”** 选项中指定的方案对称。</span><span class="sxs-lookup"><span data-stu-id="06f59-214">The partition scheme must be symmetric with the scheme that is specified in the **Partition scheme** option.</span></span>  
  
 <span data-ttu-id="06f59-215">如果表未分区，则该字段为空白。</span><span class="sxs-lookup"><span data-stu-id="06f59-215">If the table is not partitioned, the field is blank.</span></span>  
  
 <span data-ttu-id="06f59-216">**分区方案参数**</span><span class="sxs-lookup"><span data-stu-id="06f59-216">**Partition Scheme Parameter**</span></span>  
 <span data-ttu-id="06f59-217">显示构成分区方案的列的名称。</span><span class="sxs-lookup"><span data-stu-id="06f59-217">Displays the name of the column that participates in the partition scheme.</span></span>  
  
 <span data-ttu-id="06f59-218">**表列**</span><span class="sxs-lookup"><span data-stu-id="06f59-218">**Table Column**</span></span>  
 <span data-ttu-id="06f59-219">选择要映射到分区方案的表或视图。</span><span class="sxs-lookup"><span data-stu-id="06f59-219">Select the table or view to map to the partition scheme.</span></span>  
  
 <span data-ttu-id="06f59-220">**列数据类型**</span><span class="sxs-lookup"><span data-stu-id="06f59-220">**Column Data Type**</span></span>  
 <span data-ttu-id="06f59-221">显示有关列的数据类型信息。</span><span class="sxs-lookup"><span data-stu-id="06f59-221">Displays data type information about the column.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="06f59-222">如果表列是计算列，则 **“列数据类型”** 显示为“计算列”。</span><span class="sxs-lookup"><span data-stu-id="06f59-222">If the table column is a computed column, **Column Data Type** displays "computed column."</span></span>  
  
 <span data-ttu-id="06f59-223">**允许在移动索引时在线处理 DML 语句**</span><span class="sxs-lookup"><span data-stu-id="06f59-223">**Allow online processing of DML statements while moving the index**</span></span>  
 <span data-ttu-id="06f59-224">在索引操作过程中，允许用户访问基础表或聚集索引数据以及任何相关联的非聚集索引。</span><span class="sxs-lookup"><span data-stu-id="06f59-224">Allows users to access the underlying table or clustered index data and any associated nonclustered indexes during the index operation.</span></span> <span data-ttu-id="06f59-225">有关详细信息，请参阅 [Perform Index Operations Online](perform-index-operations-online.md)。</span><span class="sxs-lookup"><span data-stu-id="06f59-225">For more information, see [Perform Index Operations Online](perform-index-operations-online.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="06f59-226">此选项对 XML 索引不可用，或者如果索引为禁用的聚集索引，此选项也不可用。</span><span class="sxs-lookup"><span data-stu-id="06f59-226">This option is not available for XML indexes, or if the index is a disabled clustered index.</span></span>  
  
 <span data-ttu-id="06f59-227">**设置最大并行度**</span><span class="sxs-lookup"><span data-stu-id="06f59-227">**Set maximum degree of parallelism**</span></span>  
 <span data-ttu-id="06f59-228">限制执行并行计划时所使用的处理器数。</span><span class="sxs-lookup"><span data-stu-id="06f59-228">Limits the number of processors to use during parallel plan execution.</span></span> <span data-ttu-id="06f59-229">默认值为 0，表示使用实际可用的 CPU 数。</span><span class="sxs-lookup"><span data-stu-id="06f59-229">The default value, 0, uses the actual number of available CPUs.</span></span> <span data-ttu-id="06f59-230">若将此值设置为 1，则取消生成并行计划；若将此值设置为大于 1 的数，则会限制单个查询执行使用的最多处理器数。</span><span class="sxs-lookup"><span data-stu-id="06f59-230">Setting the value to 1 suppresses parallel plan generation; setting the value to a number greater than 1 restricts the maximum number of processors used by a single query execution.</span></span> <span data-ttu-id="06f59-231">该选项仅在此对话框处于 **“重新生成”** 或 **“重新创建”** 状态时才可用。</span><span class="sxs-lookup"><span data-stu-id="06f59-231">This option only becomes available if the dialog box is in the **Rebuild** or **Recreate** state.</span></span> <span data-ttu-id="06f59-232">有关详细信息，请参阅 [设置最大并行度选项以获取最佳性能](../policy-based-management/set-the-max-degree-of-parallelism-option-for-optimal-performance.md)。</span><span class="sxs-lookup"><span data-stu-id="06f59-232">For more information, see [Set the Max Degree of Parallelism Option for Optimal Performance](../policy-based-management/set-the-max-degree-of-parallelism-option-for-optimal-performance.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="06f59-233">如果指定的值比可用 CPU 数大，则将使用实际的可用 CPU 数。</span><span class="sxs-lookup"><span data-stu-id="06f59-233">If a value greater than the number of available CPUs is specified, the actual number of available CPUs is used.</span></span>  
  
##  <a name="spatial-page-index-options"></a><a name="Spatial"></a> <span data-ttu-id="06f59-234">空间页索引选项</span><span class="sxs-lookup"><span data-stu-id="06f59-234">Spatial Page Index Options</span></span>  
 <span data-ttu-id="06f59-235">使用 **“空间”** 页，可以查看或指定空间属性的值。</span><span class="sxs-lookup"><span data-stu-id="06f59-235">Use the **Spatial** page to view or specify the values of the spatial properties.</span></span> <span data-ttu-id="06f59-236">有关详细信息，请参阅[空间数据 (SQL Server)](../spatial/spatial-data-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="06f59-236">For more information, see [Spatial Data &#40;SQL Server&#41;](../spatial/spatial-data-sql-server.md).</span></span>  
  
### <a name="bounding-box"></a><span data-ttu-id="06f59-237">边界框</span><span class="sxs-lookup"><span data-stu-id="06f59-237">Bounding Box</span></span>  
 <span data-ttu-id="06f59-238">“边界框”  为几何平面的顶级网格的周界。</span><span class="sxs-lookup"><span data-stu-id="06f59-238">The *bounding box* is the perimeter of the top-level grid of a geometric plane.</span></span> <span data-ttu-id="06f59-239">边界框参数仅存在于几何图形网格分割中。</span><span class="sxs-lookup"><span data-stu-id="06f59-239">The bounding-box parameters exist only in the geometry grid tessellation.</span></span> <span data-ttu-id="06f59-240">如果 **“分割方案”** 为 **“地理网格”** ，这些参数将不可用。</span><span class="sxs-lookup"><span data-stu-id="06f59-240">These parameters are unavailable if the **Tessellation Scheme** is **Geography grid**.</span></span>  
  
 <span data-ttu-id="06f59-241">面板将显示\*\* (*`X-min`* 、 *`Y-min`*) **和** (*`X-max`* *`Y-max`*) \*\*边界框的坐标。</span><span class="sxs-lookup"><span data-stu-id="06f59-241">The panel displays the **(*`X-min`*,*`Y-min`*)** and **(*`X-max`*,*`Y-max`*)** coordinates of the bounding box.</span></span> <span data-ttu-id="06f59-242">没有任何默认坐标值。</span><span class="sxs-lookup"><span data-stu-id="06f59-242">There are no default coordinate values.</span></span> <span data-ttu-id="06f59-243">因此，在对 `geometry` 类型列创建新的空间索引时，必须指定坐标值。</span><span class="sxs-lookup"><span data-stu-id="06f59-243">Therefore, when you are creating a new spatial index on a `geometry` type column, you must specify the coordinate values.</span></span>  
  
 `X-min`  
 <span data-ttu-id="06f59-244">边界框左下角的 X 坐标。</span><span class="sxs-lookup"><span data-stu-id="06f59-244">The X-coordinate of the lower-left corner of the bounding box.</span></span>  
  
 `Y-min`  
 <span data-ttu-id="06f59-245">边界框左下角的 Y 坐标。</span><span class="sxs-lookup"><span data-stu-id="06f59-245">The Y-coordinate of the lower-left corner of the bounding box.</span></span>  
  
 `X-max`  
 <span data-ttu-id="06f59-246">边界框右上角的 X 坐标。</span><span class="sxs-lookup"><span data-stu-id="06f59-246">The X-coordinate of the upper-right corner of the bounding box.</span></span>  
  
 `Y-max`  
 <span data-ttu-id="06f59-247">边界框右上角的 Y 坐标。</span><span class="sxs-lookup"><span data-stu-id="06f59-247">The Y-coordinate of upper-right corner of the bounding box.</span></span>  
  
### <a name="general"></a><span data-ttu-id="06f59-248">常规</span><span class="sxs-lookup"><span data-stu-id="06f59-248">General</span></span>  
 <span data-ttu-id="06f59-249">**分割方案**</span><span class="sxs-lookup"><span data-stu-id="06f59-249">**Tessellation Scheme**</span></span>  
 <span data-ttu-id="06f59-250">指示索引的分割方案。</span><span class="sxs-lookup"><span data-stu-id="06f59-250">Indicates the tessellation scheme of the index.</span></span> <span data-ttu-id="06f59-251">支持的分割方案如下所示。</span><span class="sxs-lookup"><span data-stu-id="06f59-251">The supported tessellation schemes are as follows.</span></span>  
  
 <span data-ttu-id="06f59-252">**几何图形网格**</span><span class="sxs-lookup"><span data-stu-id="06f59-252">**Geometry grid**</span></span>  
 <span data-ttu-id="06f59-253">指定“几何图形网格”分割方案，它适用于 `geometry` 数据类型的列。</span><span class="sxs-lookup"><span data-stu-id="06f59-253">Specifies the geometry grid tessellation scheme, which applies to a column of the `geometry` data type.</span></span>  
  
 <span data-ttu-id="06f59-254">**几何自动网格**</span><span class="sxs-lookup"><span data-stu-id="06f59-254">**Geometry Auto grid**</span></span>  
 <span data-ttu-id="06f59-255">在数据库兼容级别设置为 110 或更高时，将为 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 启用此选项。</span><span class="sxs-lookup"><span data-stu-id="06f59-255">This option is enabled for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] when database compatibility level is set to 110 or higher.</span></span>  
  
 <span data-ttu-id="06f59-256">**“地理网格”**</span><span class="sxs-lookup"><span data-stu-id="06f59-256">**Geography grid**</span></span>  
 <span data-ttu-id="06f59-257">指定“地理网格”分割方案，它适用于 **geography** 数据类型的列。</span><span class="sxs-lookup"><span data-stu-id="06f59-257">Specifies the geography grid tessellation scheme, which applies to a column of the **geography** data type.</span></span>  
  
 <span data-ttu-id="06f59-258">**地理自动网格**</span><span class="sxs-lookup"><span data-stu-id="06f59-258">**Geography Auto grid**</span></span>  
 <span data-ttu-id="06f59-259">在数据库兼容级别设置为 110 或更高时，将为 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 启用此选项。</span><span class="sxs-lookup"><span data-stu-id="06f59-259">This option is enabled for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] when database compatibility level is set to 110 or higher.</span></span>  
  
 <span data-ttu-id="06f59-260">有关 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 如何实现分割的信息，请参阅[空间数据 (SQL Server)](../spatial/spatial-data-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="06f59-260">For information about how [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] implements tessellation, see [Spatial Data &#40;SQL Server&#41;](../spatial/spatial-data-sql-server.md).</span></span>  
  
 <span data-ttu-id="06f59-261">**每个对象的单元格数**</span><span class="sxs-lookup"><span data-stu-id="06f59-261">**Cells Per Object**</span></span>  
 <span data-ttu-id="06f59-262">指示可用于索引中单个空间对象的每个对象的分割单元格数。</span><span class="sxs-lookup"><span data-stu-id="06f59-262">Indicates the number of tessellation cells-per-object that can be used for a single spatial object in the index.</span></span> <span data-ttu-id="06f59-263">该数字可以是 1 和 8192 之间（含 1 和 8192）的任何整数。</span><span class="sxs-lookup"><span data-stu-id="06f59-263">This number can be any integer between 1 and 8192, inclusive.</span></span> <span data-ttu-id="06f59-264">当数据库兼容级别设置为 110 或更高时，默认值为 16，并且对于 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的早期版本为 8。</span><span class="sxs-lookup"><span data-stu-id="06f59-264">The default is 16, and 8 for earlier versions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] when database compatibility level is set to 110 or higher.</span></span>  
  
 <span data-ttu-id="06f59-265">在顶级，如果对象包含的单元格多于 *n*指定的单元格，则索引操作将根据需要使用尽可能多的单元格来提供完整的顶级分割。</span><span class="sxs-lookup"><span data-stu-id="06f59-265">At the top level, if an object covers more cells than specified by *n*, the indexing uses as many cells as necessary to provide a complete top-level tessellation.</span></span> <span data-ttu-id="06f59-266">在这种情况下，对象收到的单元格数可能会大于指定的单元格数。</span><span class="sxs-lookup"><span data-stu-id="06f59-266">In such cases, an object might receive more than the specified number of cells.</span></span> <span data-ttu-id="06f59-267">这种情况下，最大数量即为顶级网格创建的单元格数，这取决于 **“级别 1”** 的密度。</span><span class="sxs-lookup"><span data-stu-id="06f59-267">In this case, the maximum number is the number of cells generated by the top-level grid, which depends on the **Level 1** density.</span></span>  
  
### <a name="grids"></a><span data-ttu-id="06f59-268">网格</span><span class="sxs-lookup"><span data-stu-id="06f59-268">Grids</span></span>  
 <span data-ttu-id="06f59-269">此面板显示分割方案的每个级别上网格的密度。</span><span class="sxs-lookup"><span data-stu-id="06f59-269">This panel shows the density of the grid at each level of the tessellation scheme.</span></span> <span data-ttu-id="06f59-270">密度可指定为 **“低”** 、 **“中”** 或 **“高”** 三个级别。</span><span class="sxs-lookup"><span data-stu-id="06f59-270">Density is specified as **Low**, **Medium**, or **High**.</span></span> <span data-ttu-id="06f59-271">默认值为 **“中”** 。</span><span class="sxs-lookup"><span data-stu-id="06f59-271">The default is **Medium**.</span></span> <span data-ttu-id="06f59-272">**“低”** 表示 4x4 网格（16 个单元格）、 **“中”** 表示 8x8 网格（64 个单元格）而 **“高”** 表示 16x16 网格（256 个单元格）。</span><span class="sxs-lookup"><span data-stu-id="06f59-272">**Low** represents a 4x4 grid (16 cells), **Medium** represents an 8x8 grid (64 cells), and **High** represents a 16x16 grid (256 cells).</span></span> <span data-ttu-id="06f59-273">在选择 **“几何自动网格”** 或 **“地理自动网格”** 分割选项时，这些选项将不可用。</span><span class="sxs-lookup"><span data-stu-id="06f59-273">These options are not available when the **Geometry Auto grid** or **Geography Auto grid** tessellation options are chosen.</span></span>  
  
 <span data-ttu-id="06f59-274">**级别 1**</span><span class="sxs-lookup"><span data-stu-id="06f59-274">**Level 1**</span></span>  
 <span data-ttu-id="06f59-275">第一级（顶级）网格的密度。</span><span class="sxs-lookup"><span data-stu-id="06f59-275">The density of the first-level (top) grid.</span></span>  
  
 <span data-ttu-id="06f59-276">**级别 2**</span><span class="sxs-lookup"><span data-stu-id="06f59-276">**Level 2**</span></span>  
 <span data-ttu-id="06f59-277">第二级网格的密度。</span><span class="sxs-lookup"><span data-stu-id="06f59-277">The density of the second-level grid.</span></span>  
  
 <span data-ttu-id="06f59-278">**级别 3**</span><span class="sxs-lookup"><span data-stu-id="06f59-278">**Level 3**</span></span>  
 <span data-ttu-id="06f59-279">第三级网格的密度。</span><span class="sxs-lookup"><span data-stu-id="06f59-279">The density of the third-level grid.</span></span>  
  
 <span data-ttu-id="06f59-280">**级别 4**</span><span class="sxs-lookup"><span data-stu-id="06f59-280">**Level 4**</span></span>  
 <span data-ttu-id="06f59-281">第四级网格的密度。</span><span class="sxs-lookup"><span data-stu-id="06f59-281">The density of the fourth-level grid.</span></span>  
  
##  <a name="filter-page"></a><a name="Filter"></a> <span data-ttu-id="06f59-282">筛选器页</span><span class="sxs-lookup"><span data-stu-id="06f59-282">Filter Page</span></span>  
 <span data-ttu-id="06f59-283">使用此页可以输入用于筛选索引的筛选器谓词。</span><span class="sxs-lookup"><span data-stu-id="06f59-283">Use this page to enter the filter predicate for a filtered index.</span></span> <span data-ttu-id="06f59-284">有关详细信息，请参阅 [Create Filtered Indexes](create-filtered-indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="06f59-284">For more information, see [Create Filtered Indexes](create-filtered-indexes.md).</span></span>  
  
 <span data-ttu-id="06f59-285">**筛选表达式**</span><span class="sxs-lookup"><span data-stu-id="06f59-285">**Filter Expression**</span></span>  
 <span data-ttu-id="06f59-286">定义要将哪些数据行包含在筛选索引中。</span><span class="sxs-lookup"><span data-stu-id="06f59-286">Defines which data rows to include in the filtered index.</span></span> <span data-ttu-id="06f59-287">例如： `StartDate > '20000101' AND EndDate IS NOT NULL'.`</span><span class="sxs-lookup"><span data-stu-id="06f59-287">For example, `StartDate > '20000101' AND EndDate IS NOT NULL'.`</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06f59-288">另请参阅</span><span class="sxs-lookup"><span data-stu-id="06f59-288">See Also</span></span>  
 <span data-ttu-id="06f59-289">[设置索引选项](set-index-options.md) </span><span class="sxs-lookup"><span data-stu-id="06f59-289">[Set Index Options](set-index-options.md) </span></span>  
 <span data-ttu-id="06f59-290">[INDEXPROPERTY (Transact-SQL)](/sql/t-sql/functions/indexproperty-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="06f59-290">[INDEXPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/indexproperty-transact-sql) </span></span>  
 [<span data-ttu-id="06f59-291">sys.indexes (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="06f59-291">sys.indexes &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-indexes-transact-sql)  
  
  
