---
title: 创建、修改和删除空间索引 | Microsoft Docs
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- indexes [SQL Server], creating
- spatial indexes [SQL Server], dropping
- spatial indexes [SQL Server], creating
- indexes [SQL Server], dropping
- indexes [SQL Server], modifying
- spatial indexes [SQL Server], modifying
ms.assetid: 00c1b927-8ec5-44cf-87c2-c8de59745735
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 88de17e8c487d9a965f2e236edac064dc2fe4c7c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578052"
---
# <a name="create-modify-and-drop-spatial-indexes"></a><span data-ttu-id="718cc-102">创建、修改和删除空间索引</span><span class="sxs-lookup"><span data-stu-id="718cc-102">Create, Modify, and Drop Spatial Indexes</span></span>
  <span data-ttu-id="718cc-103">空间索引可以更高效地对或数据类型的列执行某些操作， `geometry` `geography` () *空间列*。</span><span class="sxs-lookup"><span data-stu-id="718cc-103">A spatial index can more efficiently perform certain operations on a column of the `geometry` or `geography` data type (a *spatial column*).</span></span> <span data-ttu-id="718cc-104">可对空间数据列指定多个空间索引。</span><span class="sxs-lookup"><span data-stu-id="718cc-104">More than one spatial index can be specified on a spatial column.</span></span> <span data-ttu-id="718cc-105">这非常有用，例如，对单一列中的不同分割参数建立索引时，就是如此。</span><span class="sxs-lookup"><span data-stu-id="718cc-105">This is useful, for example, for indexing different tessellation parameters in a single column.</span></span>  
  
 <span data-ttu-id="718cc-106">创建空间索引时有许多限制。</span><span class="sxs-lookup"><span data-stu-id="718cc-106">There are a number of restrictions on creating spatial indexes.</span></span> <span data-ttu-id="718cc-107">有关详细信息，请参阅本主题中的 [对空间索引的限制](#restrictions) 。</span><span class="sxs-lookup"><span data-stu-id="718cc-107">For more information, see [Restrictions on Spatial Indexes](#restrictions) in this topic.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="718cc-108">有关空间索引与分区和文件组的关系的信息，请参阅 [CREATE SPATIAL INDEX (Transact-SQL)](/sql/t-sql/statements/create-spatial-index-transact-sql)中的“备注”部分。</span><span class="sxs-lookup"><span data-stu-id="718cc-108">For information about the relationship of spatial indexes to partition and to filegroups, see the "Remarks" section in [CREATE SPATIAL INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-spatial-index-transact-sql).</span></span>  
  
##  <a name="creating-modifying-and-dropping-spatial-indexes"></a><a name="creating"></a> <span data-ttu-id="718cc-109">创建、修改和删除空间索引</span><span class="sxs-lookup"><span data-stu-id="718cc-109">Creating, Modifying, and Dropping Spatial Indexes</span></span>  
  
###  <a name="to-create-a-spatial-index"></a><a name="create"></a> <span data-ttu-id="718cc-110">创建空间索引</span><span class="sxs-lookup"><span data-stu-id="718cc-110">To create a spatial index</span></span>  
 <span data-ttu-id="718cc-111">**使用 Transact-SQL 创建空间索引**</span><span class="sxs-lookup"><span data-stu-id="718cc-111">**To create a spatial index by using Transact-SQL**</span></span>  
 [<span data-ttu-id="718cc-112">CREATE SPATIAL INDEX (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="718cc-112">CREATE SPATIAL INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-spatial-index-transact-sql)  
  
 <span data-ttu-id="718cc-113">**在 Management Studio 中使用“新建索引”对话框创建空间索引**</span><span class="sxs-lookup"><span data-stu-id="718cc-113">**To create a spatial index by using the New Index dialog box in Management Studio**</span></span>  
 ##### <a name="to-create-a-spatial-index-in-management-studio"></a><span data-ttu-id="718cc-114">在 Management Studio 中创建空间索引</span><span class="sxs-lookup"><span data-stu-id="718cc-114">To create a spatial index in Management Studio</span></span>  
  
1.  <span data-ttu-id="718cc-115">在对象资源管理器中，连接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 的实例，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="718cc-115">In Object Explorer, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="718cc-116">展开 **“数据库”** ，展开包含具有指定索引的表的数据库，再展开 **“表”** 。</span><span class="sxs-lookup"><span data-stu-id="718cc-116">Expand **Databases**, expand the database that contains the table with the specified index, and then expand **Tables**.</span></span>  
  
3.  <span data-ttu-id="718cc-117">展开要为其创建索引的表。</span><span class="sxs-lookup"><span data-stu-id="718cc-117">Expand the table for which you want to create the index.</span></span>  
  
4.  <span data-ttu-id="718cc-118">右键单击“索引”，再选择“新建索引”。</span><span class="sxs-lookup"><span data-stu-id="718cc-118">Right-click **Indexes** and select **New Index**.</span></span>  
  
5.  <span data-ttu-id="718cc-119">在 **“索引名称”** 字段中，输入索引的名称。</span><span class="sxs-lookup"><span data-stu-id="718cc-119">In the **Index name** field, enter a name for the index.</span></span>  
  
6.  <span data-ttu-id="718cc-120">在“索引类型”下拉列表中，选择“空间”。</span><span class="sxs-lookup"><span data-stu-id="718cc-120">In the **Index type** drop-down list, select **Spatial**.</span></span>  
  
7.  <span data-ttu-id="718cc-121">若要指定想为其创建索引的空间数据列，请单击 **“添加”** 。</span><span class="sxs-lookup"><span data-stu-id="718cc-121">To specify the spatial column that you want to index, click **Add**.</span></span>  
  
8.  <span data-ttu-id="718cc-122">在 "**从中选择列**" 对话框中 *\<table name>* ， `geometry` 通过选中相应的 `geography` 复选框来选择类型为或的列。</span><span class="sxs-lookup"><span data-stu-id="718cc-122">In the **Select Columns from** *\<table name>* dialog box, select a column of type `geometry` or `geography` by selecting the corresponding check box.</span></span> <span data-ttu-id="718cc-123">然后，任何其他空间数据列将变为不可编辑状态。</span><span class="sxs-lookup"><span data-stu-id="718cc-123">Any other spatial columns then become uneditable.</span></span> <span data-ttu-id="718cc-124">如果要选择其他空间数据列，必须首先清除当前选定的列。</span><span class="sxs-lookup"><span data-stu-id="718cc-124">If you want to select a different spatial column, you must first clear the currently selected column.</span></span> <span data-ttu-id="718cc-125">完成后，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="718cc-125">When finished, click **OK**.</span></span>  
  
9. <span data-ttu-id="718cc-126">请在 **“索引键列”** 网格中验证您的列选择。</span><span class="sxs-lookup"><span data-stu-id="718cc-126">Verify your column selection in the **Index key columns** grid.</span></span>  
  
10. <span data-ttu-id="718cc-127">在 **“索引属性”** 对话框的 **“选择页”** 窗格中，单击 **“空间”** 。</span><span class="sxs-lookup"><span data-stu-id="718cc-127">In the **Select a page** pane of the **Index Properties** dialog box, click **Spatial**.</span></span>  
  
11. <span data-ttu-id="718cc-128">在 **“空间”** 页上，指定要用于索引的空间属性的值。</span><span class="sxs-lookup"><span data-stu-id="718cc-128">On the **Spatial** page, specify the values that you want to use for the spatial properties of the index.</span></span>  
  
     <span data-ttu-id="718cc-129">对类型列创建索引时 `geometry` ，必须指定\*\* (*`X-min`* 、 *`Y-min`*) **和** (*`X-max`* ， *`Y-max`*) \*\*边界框的坐标。</span><span class="sxs-lookup"><span data-stu-id="718cc-129">When creating an index on a `geometry` type column, you must specify the **(*`X-min`*,*`Y-min`*)** and **(*`X-max`*,*`Y-max`*)** coordinates of the bounding box.</span></span> <span data-ttu-id="718cc-130">对于类型列上的索引 `geography` ，指定 "**地理网格**" 分割方案后，边界框字段变为只读，因为地理网格分割不使用边界框。</span><span class="sxs-lookup"><span data-stu-id="718cc-130">For an index on a `geography` type column, the bounding-box fields become read-only after you specify the **Geography grid** tessellation scheme, because geography grid tessellation does not use a bounding box.</span></span>  
  
     <span data-ttu-id="718cc-131">您还可以指定任意级别的分割方案的 **“每个对象的单元数”** 字段和网格密度的非默认值。</span><span class="sxs-lookup"><span data-stu-id="718cc-131">Optionally, you can specify nondefault values for the **Cells Per Object** field and for the grid density at any level of the tessellation scheme.</span></span> <span data-ttu-id="718cc-132">对于 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] ，每个对象的默认单元数为 16；对于 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 或更高版本，则为 8。对于 **，默认网格密度为** “中” [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="718cc-132">The default number of cells per object is 16 for [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] or 8 for [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] or higher, and the default grid density is **Medium** for [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)].</span></span>  
  
     <span data-ttu-id="718cc-133">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中，可以为分割方案选择 GEOMETRY_AUTO_GRID 或 GEOGRAPHY_AUTO_GRID。</span><span class="sxs-lookup"><span data-stu-id="718cc-133">You can select GEOMETRY_AUTO_GRID or GEOGRAPHY_AUTO_GRID for tessellation scheme in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="718cc-134">选择 GEOMETRY_AUTO_GRID 或 GEOGRAPHY_AUTO_GRID 时，禁用级别 1、级别 2、级别 3 和级别 4 网格密度选项。</span><span class="sxs-lookup"><span data-stu-id="718cc-134">When GEOMETRY_AUTO_GRID or GEOGRAPHY_AUTO_GRID is selected, then Level 1, Level 2, Level 3, and Level 4 grid density options are disabled.</span></span>  
  
     <span data-ttu-id="718cc-135">有关这些属性的详细信息，请参阅 [Index Properties F1 Help](../indexes/index-properties-f1-help.md)。</span><span class="sxs-lookup"><span data-stu-id="718cc-135">For more information about these properties, see [Index Properties F1 Help](../indexes/index-properties-f1-help.md).</span></span>  
  
12. <span data-ttu-id="718cc-136">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="718cc-136">Click **OK**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="718cc-137">若要对同一空间数据列或另一个空间数据列再创建一个空间索引，请重复上述步骤。</span><span class="sxs-lookup"><span data-stu-id="718cc-137">To create another spatial index on the same or a different spatial column, repeat the preceding steps.</span></span>  
  
  
 <span data-ttu-id="718cc-138">**在 Management Studio 中使用表设计器创建空间索引**</span><span class="sxs-lookup"><span data-stu-id="718cc-138">**To create a spatial index by using Table Designer in Management Studio**</span></span>  
 ##### <a name="to-create-a-spatial-index-in-table-designer"></a><span data-ttu-id="718cc-139">在表设计器中创建空间索引</span><span class="sxs-lookup"><span data-stu-id="718cc-139">To create a spatial index in Table Designer</span></span>  
  
1.  <span data-ttu-id="718cc-140">在对象资源管理器中，右键单击要为其创建空间索引的表，然后单击“设计”。</span><span class="sxs-lookup"><span data-stu-id="718cc-140">In Object Explorer, right-click the table for which you want to create a spatial index, and then click **Design**.</span></span>  
  
     <span data-ttu-id="718cc-141">此时，将在表设计器中打开该表。</span><span class="sxs-lookup"><span data-stu-id="718cc-141">The table opens in Table Designer.</span></span>  
  
2.  <span data-ttu-id="718cc-142">为索引选择 `geometry` 列或 `geography` 列。</span><span class="sxs-lookup"><span data-stu-id="718cc-142">Select a `geometry` or `geography` column for the index.</span></span>  
  
3.  <span data-ttu-id="718cc-143">在 **表设计器** 菜单上，单击 **“空间索引”** 。</span><span class="sxs-lookup"><span data-stu-id="718cc-143">On the **Table Designer** menu, click **Spatial Index**.</span></span>  
  
4.  <span data-ttu-id="718cc-144">在 **“空间索引”** 对话框中，单击 **“添加”** 。</span><span class="sxs-lookup"><span data-stu-id="718cc-144">In the **Spatial Indexes** dialog box, click **Add**.</span></span>  
  
5.  <span data-ttu-id="718cc-145">在 **“所选空间索引”** 列表中选择新的索引，然后在右侧的网格中设置空间索引的属性。</span><span class="sxs-lookup"><span data-stu-id="718cc-145">Select the new index in the **Selected Spatial Index** list, and in the grid to the right, set the properties for the spatial index.</span></span> <span data-ttu-id="718cc-146">有关属性的信息，请参阅[空间索引对话框 (Visual Database Tools)](../../ssms/visual-db-tools/visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="718cc-146">For information about the properties, see [Spatial Indexes Dialog Box &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/visual-database-tools.md).</span></span>  
  
  
###  <a name="to-alter-a-spatial-index"></a><a name="alter"></a> <span data-ttu-id="718cc-147">更改空间索引</span><span class="sxs-lookup"><span data-stu-id="718cc-147">To alter a spatial index</span></span>  
  
-   [<span data-ttu-id="718cc-148">ALTER INDEX (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="718cc-148">ALTER INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-index-transact-sql)  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="718cc-149">若要更改特定于某个空间索引的选项（例如 BOUNDING_BOX 或 GRID），您可以使用 CREATE SPATIAL INDEX 语句指定 DROP_EXISTING = ON，或删除该空间索引并创建一个新的空间索引。</span><span class="sxs-lookup"><span data-stu-id="718cc-149">To change options that are specific to a spatial index, such as BOUNDING_BOX or GRID, you can either use a CREATE SPATIAL INDEX statement that specifies DROP_EXISTING = ON, or drop the spatial index and create a new one.</span></span> <span data-ttu-id="718cc-150">有关示例，请参阅 [CREATE SPATIAL INDEX (Transact-SQL)](/sql/t-sql/statements/create-spatial-index-transact-sql)中的“备注”部分。</span><span class="sxs-lookup"><span data-stu-id="718cc-150">For an example, see [CREATE SPATIAL INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-spatial-index-transact-sql).</span></span>  
  
-   [<span data-ttu-id="718cc-151">修改索引</span><span class="sxs-lookup"><span data-stu-id="718cc-151">Modify an Index</span></span>](../indexes/modify-an-index.md)  
  
-   [<span data-ttu-id="718cc-152">将现有索引移动到其他文件组中</span><span class="sxs-lookup"><span data-stu-id="718cc-152">Move an Existing Index to a Different Filegroup</span></span>](../indexes/move-an-existing-index-to-a-different-filegroup.md)  
  
  
###  <a name="to-drop-a-spatial-index"></a><a name="drop"></a> <span data-ttu-id="718cc-153">删除空间索引</span><span class="sxs-lookup"><span data-stu-id="718cc-153">To drop a spatial index</span></span>  
 <span data-ttu-id="718cc-154">**使用 Transact-SQL 删除空间索引**</span><span class="sxs-lookup"><span data-stu-id="718cc-154">**To drop a spatial index by using Transact-SQL**</span></span>  
 [<span data-ttu-id="718cc-155">DROP INDEX (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="718cc-155">DROP INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-index-transact-sql)  
  
 <span data-ttu-id="718cc-156">**使用 Management Studio 删除索引**</span><span class="sxs-lookup"><span data-stu-id="718cc-156">**To drop an index by using Management Studio**</span></span>  
 [<span data-ttu-id="718cc-157">删除索引</span><span class="sxs-lookup"><span data-stu-id="718cc-157">Delete an Index</span></span>](../indexes/delete-an-index.md)  
  
 <span data-ttu-id="718cc-158">**在 Management Studio 中使用表设计器删除空间索引**</span><span class="sxs-lookup"><span data-stu-id="718cc-158">**To drop a spatial index by using Table Designer in Management Studio**</span></span>  
 ##### <a name="to-drop-a-spatial-index-in-table-designer"></a><span data-ttu-id="718cc-159">在表设计器中删除空间索引</span><span class="sxs-lookup"><span data-stu-id="718cc-159">To drop a spatial index in Table Designer</span></span>  
  
1.  <span data-ttu-id="718cc-160">在对象资源管理器中，右键单击具有要删除的空间索引的表，再单击“设计”。</span><span class="sxs-lookup"><span data-stu-id="718cc-160">In Object Explorer, right-click the table with the spatial index you want to delete and click **Design**.</span></span>  
  
     <span data-ttu-id="718cc-161">此时，将在表设计器中打开该表。</span><span class="sxs-lookup"><span data-stu-id="718cc-161">The table opens in Table Designer.</span></span>  
  
2.  <span data-ttu-id="718cc-162">在 **表设计器** 菜单上，单击 **“空间索引”** 。</span><span class="sxs-lookup"><span data-stu-id="718cc-162">On the **Table Designer** menu, click **Spatial Index**.</span></span>  
  
     <span data-ttu-id="718cc-163">**“空间索引”** 对话框随即打开。</span><span class="sxs-lookup"><span data-stu-id="718cc-163">The **Spatial Index** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="718cc-164">在 **“所选空间索引”** 列中单击要删除的索引。</span><span class="sxs-lookup"><span data-stu-id="718cc-164">Click the index you want to delete in the **Selected Spatial Index** column.</span></span>  
  
4.  <span data-ttu-id="718cc-165">单击 **“删除”** 。</span><span class="sxs-lookup"><span data-stu-id="718cc-165">Click **Delete**.</span></span>  
  
  
##  <a name="restrictions-on-spatial-indexes"></a><a name="restrictions"></a> <span data-ttu-id="718cc-166">对空间索引的限制</span><span class="sxs-lookup"><span data-stu-id="718cc-166">Restrictions on Spatial Indexes</span></span>  
 <span data-ttu-id="718cc-167">只能对类型为 `geometry` 或 `geography` 的列创建空间索引。</span><span class="sxs-lookup"><span data-stu-id="718cc-167">A spatial index can be created only on a column of type `geometry` or `geography`.</span></span>  
  
### <a name="table-and-view-restrictions"></a><span data-ttu-id="718cc-168">针对表和视图的限制</span><span class="sxs-lookup"><span data-stu-id="718cc-168">Table and View Restrictions</span></span>  
 <span data-ttu-id="718cc-169">只能对具有主键的表定义空间索引。</span><span class="sxs-lookup"><span data-stu-id="718cc-169">Spatial indexes can be defined only on a table that has a primary key.</span></span> <span data-ttu-id="718cc-170">表中主键列的最大数目为 15。</span><span class="sxs-lookup"><span data-stu-id="718cc-170">The maximum number of primary key columns on the table is 15.</span></span>  
  
 <span data-ttu-id="718cc-171">索引键记录的最大大小为 895 字节。</span><span class="sxs-lookup"><span data-stu-id="718cc-171">The maximum size of index key records is 895 bytes.</span></span> <span data-ttu-id="718cc-172">超过此大小会引发错误。</span><span class="sxs-lookup"><span data-stu-id="718cc-172">Larger sizes raise an error.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="718cc-173">对表定义空间索引时，不能更改主键元数据。</span><span class="sxs-lookup"><span data-stu-id="718cc-173">Primary key metadata cannot be changed while a spatial index is defined on a table.</span></span>  
  
 <span data-ttu-id="718cc-174">不能对索引视图指定空间索引。</span><span class="sxs-lookup"><span data-stu-id="718cc-174">Spatial indexes cannot be specified on indexed views.</span></span>  
  
### <a name="multiple-spatial-index-restrictions"></a><span data-ttu-id="718cc-175">多空间索引限制</span><span class="sxs-lookup"><span data-stu-id="718cc-175">Multiple Spatial Index Restrictions</span></span>  
 <span data-ttu-id="718cc-176">最多可对支持的表中的任何空间数据列创建 249 个空间索引。</span><span class="sxs-lookup"><span data-stu-id="718cc-176">You can create up to 249 spatial indexes on any of the spatial columns in a supported table.</span></span> <span data-ttu-id="718cc-177">对同一空间数据列创建多个空间索引可能很有用，例如，在要对单个列中的不同分割参数建立索引时。</span><span class="sxs-lookup"><span data-stu-id="718cc-177">Creating more than one spatial index on the same spatial column can be useful, for example, to index different tessellation parameters in a single column.</span></span>  
  
 <span data-ttu-id="718cc-178">一次只能创建一个空间索引。</span><span class="sxs-lookup"><span data-stu-id="718cc-178">You can create only one spatial index at a time.</span></span>  
  
### <a name="spatial-indexes-and-process-parallelism"></a><span data-ttu-id="718cc-179">空间索引和处理并行度</span><span class="sxs-lookup"><span data-stu-id="718cc-179">Spatial Indexes and Process Parallelism</span></span>  
 <span data-ttu-id="718cc-180">索引的生成过程可以利用可用的处理并行度。</span><span class="sxs-lookup"><span data-stu-id="718cc-180">An index build can use available process parallelism.</span></span>  
  
### <a name="version-restrictions"></a><span data-ttu-id="718cc-181">版本限制</span><span class="sxs-lookup"><span data-stu-id="718cc-181">Version Restrictions</span></span>  
 <span data-ttu-id="718cc-182">[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 中引入的空间分割方案不能复制到 [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] 或 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]中。</span><span class="sxs-lookup"><span data-stu-id="718cc-182">Spatial tessellations introduced in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] cannot be replicated to [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] or [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)].</span></span> <span data-ttu-id="718cc-183">当要求向后与 [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] 或 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] 数据库兼容时，您必须将 [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] 或 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] 空间分割方案用于空间索引。</span><span class="sxs-lookup"><span data-stu-id="718cc-183">You must use [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] or [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] spatial tessellations for spatial indexes when backward compatibility with [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] or [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] databases is a requirement.</span></span>  
  
  
## <a name="see-also"></a><span data-ttu-id="718cc-184">另请参阅</span><span class="sxs-lookup"><span data-stu-id="718cc-184">See Also</span></span>  
 [<span data-ttu-id="718cc-185">空间索引概述</span><span class="sxs-lookup"><span data-stu-id="718cc-185">Spatial Indexes Overview</span></span>](spatial-indexes-overview.md)  
  
  
