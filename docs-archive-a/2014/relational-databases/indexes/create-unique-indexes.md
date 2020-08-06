---
title: 创建唯一索引 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- unique indexes
- designing indexes [SQL Server], unique
- clustered indexes, unique
- indexes [SQL Server], unique
- nonclustered indexes [SQL Server], unique
- unique indexes, design guidelines
ms.assetid: 56b5982e-cb94-46c0-8fbb-772fc275354a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8c96c4e17a8ce0863452db171302d650f6114919
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693309"
---
# <a name="create-unique-indexes"></a><span data-ttu-id="4813e-102">创建唯一索引</span><span class="sxs-lookup"><span data-stu-id="4813e-102">Create Unique Indexes</span></span>
  <span data-ttu-id="4813e-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中创建表的唯一索引。</span><span class="sxs-lookup"><span data-stu-id="4813e-103">This topic describes how to create a unique index on a table in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="4813e-104">唯一索引能够保证索引键中不包含重复的值，从而使表中的每一行从某种方式上具有唯一性。</span><span class="sxs-lookup"><span data-stu-id="4813e-104">A unique index guarantees that the index key contains no duplicate values and therefore every row in the table is in some way unique.</span></span> <span data-ttu-id="4813e-105">创建 UNIQUE 约束和创建与约束无关的唯一索引并没有明显的区别。</span><span class="sxs-lookup"><span data-stu-id="4813e-105">There are no significant differences between creating a UNIQUE constraint and creating a unique index that is independent of a constraint.</span></span> <span data-ttu-id="4813e-106">进行数据验证的方式相同，而且对于唯一索引是由约束创建的还是手动创建的，查询优化器并不加以区分。</span><span class="sxs-lookup"><span data-stu-id="4813e-106">Data validation occurs in the same manner, and the query optimizer does not differentiate between a unique index created by a constraint or manually created.</span></span> <span data-ttu-id="4813e-107">但是，创建列的 UNIQUE 约束会使索引目标更清晰。</span><span class="sxs-lookup"><span data-stu-id="4813e-107">However, creating a UNIQUE constraint on the column makes the objective of the index clear.</span></span> <span data-ttu-id="4813e-108">有关 UNIQUE 约束的详细信息，请参阅 [Unique Constraints and Check Constraints](../tables/unique-constraints-and-check-constraints.md)。</span><span class="sxs-lookup"><span data-stu-id="4813e-108">For more information on UNIQUE constraints, see [Unique Constraints and Check Constraints](../tables/unique-constraints-and-check-constraints.md).</span></span>  
  
 <span data-ttu-id="4813e-109">在创建唯一索引时，可以设置一个忽略重复键的选项。</span><span class="sxs-lookup"><span data-stu-id="4813e-109">When you create a unique index, you can set an option to ignore duplicate keys.</span></span> <span data-ttu-id="4813e-110">如果此选项已设置为“是”  ，当你试图通过添加影响多行的数据来创建重复键（使用 INSERT 语句）时，则不会添加包含重复项的行。</span><span class="sxs-lookup"><span data-stu-id="4813e-110">If this option is set to **Yes** and you attempt to create duplicate keys by adding data that affects multiple rows (with the INSERT statement), the row containing a duplicate is not added.</span></span> <span data-ttu-id="4813e-111">如果此选项设置为 **“否”** ，则整个插入操作将失败，并且将回滚所有数据。</span><span class="sxs-lookup"><span data-stu-id="4813e-111">If it is set to **No**, the entire insert operation fails and all the data is rolled back.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4813e-112">如果单个列在多行中包含 NULL，则无法对该列创建唯一索引。</span><span class="sxs-lookup"><span data-stu-id="4813e-112">You cannot create a unique index on a single column if that column contains NULL in more than one row.</span></span> <span data-ttu-id="4813e-113">同样，如果列的组合在多行中包含 NULL，则无法对多个列创建唯一索引。</span><span class="sxs-lookup"><span data-stu-id="4813e-113">Similarly, you cannot create a unique index on multiple columns if the combination of columns contains NULL in more than one row.</span></span> <span data-ttu-id="4813e-114">在进行索引时，它们都被视为重复值。</span><span class="sxs-lookup"><span data-stu-id="4813e-114">These are treated as duplicate values for indexing purposes.</span></span>  
  
 <span data-ttu-id="4813e-115">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="4813e-115">**In This Topic**</span></span>  
  
-   <span data-ttu-id="4813e-116">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="4813e-116">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="4813e-117">唯一索引的优点</span><span class="sxs-lookup"><span data-stu-id="4813e-117">Benefits of a Unique Index</span></span>](#Benefits)  
  
     [<span data-ttu-id="4813e-118">典型实现</span><span class="sxs-lookup"><span data-stu-id="4813e-118">Typical Implementations</span></span>](#Implementations)  
  
     [<span data-ttu-id="4813e-119">限制和局限</span><span class="sxs-lookup"><span data-stu-id="4813e-119">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="4813e-120">安全性</span><span class="sxs-lookup"><span data-stu-id="4813e-120">Security</span></span>](#Security)  
  
-   <span data-ttu-id="4813e-121">**创建表的唯一索引，使用：**</span><span class="sxs-lookup"><span data-stu-id="4813e-121">**To create a unique index on a table, using:**</span></span>  
  
     [<span data-ttu-id="4813e-122">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4813e-122">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="4813e-123">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4813e-123">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="4813e-124">开始之前</span><span class="sxs-lookup"><span data-stu-id="4813e-124">Before You Begin</span></span>  
  
###  <a name="benefits-of-a-unique-index"></a><a name="Benefits"></a> <span data-ttu-id="4813e-125">唯一索引的优点</span><span class="sxs-lookup"><span data-stu-id="4813e-125">Benefits of a Unique Index</span></span>  
  
-   <span data-ttu-id="4813e-126">多列唯一索引能够保证索引键中值的每个组合都是唯一的。</span><span class="sxs-lookup"><span data-stu-id="4813e-126">Multicolumn unique indexes guarantee that each combination of values in the index key is unique.</span></span> <span data-ttu-id="4813e-127">例如，如果为 **LastName**、 **FirstName**和 **MiddleName** 列的组合创建了唯一索引，则表中的任意两行都不会有这些列值的相同组合。</span><span class="sxs-lookup"><span data-stu-id="4813e-127">For example, if a unique index is created on a combination of **LastName**, **FirstName**, and **MiddleName** columns, no two rows in the table could have the same combination of values for these columns.</span></span>  
  
-   <span data-ttu-id="4813e-128">只要每个列中的数据是唯一的，就可以为同一个表创建一个唯一聚集索引和多个唯一非聚集索引。</span><span class="sxs-lookup"><span data-stu-id="4813e-128">Provided that the data in each column is unique, you can create both a unique clustered index and multiple unique nonclustered indexes on the same table.</span></span>  
  
-   <span data-ttu-id="4813e-129">唯一索引能够确保定义的列的数据完整性。</span><span class="sxs-lookup"><span data-stu-id="4813e-129">Unique indexes ensure the data integrity of the defined columns.</span></span>  
  
-   <span data-ttu-id="4813e-130">唯一索引提供帮助查询优化器生成更高效的执行计划的其他信息。</span><span class="sxs-lookup"><span data-stu-id="4813e-130">Unique indexes provide additional information helpful to the query optimizer that can produce more efficient execution plans.</span></span>  
  
###  <a name="typical-implementations"></a><a name="Implementations"></a> <span data-ttu-id="4813e-131">典型实现</span><span class="sxs-lookup"><span data-stu-id="4813e-131">Typical Implementations</span></span>  
 <span data-ttu-id="4813e-132">唯一索引可通过以下方式实现：</span><span class="sxs-lookup"><span data-stu-id="4813e-132">Unique indexes are implemented in the following ways:</span></span>  
  
-   <span data-ttu-id="4813e-133">**PRIMARY KEY 或 UNIQUE 约束**</span><span class="sxs-lookup"><span data-stu-id="4813e-133">**PRIMARY KEY or UNIQUE constraint**</span></span>  
  
     <span data-ttu-id="4813e-134">在创建 PRIMARY KEY 约束时，如果不存在该表的聚集索引且未指定唯一非聚集索引，则将自动对一列或多列创建唯一聚集索引。</span><span class="sxs-lookup"><span data-stu-id="4813e-134">When you create a PRIMARY KEY constraint, a unique clustered index on the column or columns is automatically created if a clustered index on the table does not already exist and you do not specify a unique nonclustered index.</span></span> <span data-ttu-id="4813e-135">主键列不允许空值。</span><span class="sxs-lookup"><span data-stu-id="4813e-135">The primary key column cannot allow NULL values.</span></span>  
  
     <span data-ttu-id="4813e-136">在创建 UNIQUE 约束时，默认情况下将创建唯一非聚集索引，以便强制 UNIQUE 约束。</span><span class="sxs-lookup"><span data-stu-id="4813e-136">When you create a UNIQUE constraint, a unique nonclustered index is created to enforce a UNIQUE constraint by default.</span></span> <span data-ttu-id="4813e-137">如果不存在该表的聚集索引，则可以指定唯一聚集索引。</span><span class="sxs-lookup"><span data-stu-id="4813e-137">You can specify a unique clustered index if a clustered index on the table does not already exist.</span></span>  
  
     <span data-ttu-id="4813e-138">有关详细信息，请参阅 [Unique Constraints and Check Constraints](../tables/unique-constraints-and-check-constraints.md) 和 [Primary and Foreign Key Constraints](../tables/primary-and-foreign-key-constraints.md)。</span><span class="sxs-lookup"><span data-stu-id="4813e-138">For more information, see [Unique Constraints and Check Constraints](../tables/unique-constraints-and-check-constraints.md) and [Primary and Foreign Key Constraints](../tables/primary-and-foreign-key-constraints.md).</span></span>  
  
-   <span data-ttu-id="4813e-139">**独立于约束的索引**</span><span class="sxs-lookup"><span data-stu-id="4813e-139">**Index independent of a constraint**</span></span>  
  
     <span data-ttu-id="4813e-140">可以为一个表定义多个唯一非聚集索引。</span><span class="sxs-lookup"><span data-stu-id="4813e-140">Multiple unique nonclustered indexes can be defined on a table.</span></span>  
  
     <span data-ttu-id="4813e-141">有关详细信息，请参阅 [CREATE INDEX (Transact-SQL)](/sql/t-sql/statements/create-index-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="4813e-141">For more information, see [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql).</span></span>  
  
-   <span data-ttu-id="4813e-142">**索引视图**</span><span class="sxs-lookup"><span data-stu-id="4813e-142">**Indexed view**</span></span>  
  
     <span data-ttu-id="4813e-143">若要创建索引视图，请对一个或多个视图列定义唯一聚集索引。</span><span class="sxs-lookup"><span data-stu-id="4813e-143">To create an indexed view, a unique clustered index is defined on one or more view columns.</span></span> <span data-ttu-id="4813e-144">视图将执行，并且结果集存储在该索引的页级别中，其存储方式与表数据存储在聚集索引中的方式相同。</span><span class="sxs-lookup"><span data-stu-id="4813e-144">The view is executed and the result set is stored in the leaf level of the index in the same way table data is stored in a clustered index.</span></span> <span data-ttu-id="4813e-145">有关详细信息，请参阅 [创建索引视图](../views/views.md)。</span><span class="sxs-lookup"><span data-stu-id="4813e-145">For more information, see [Create Indexed Views](../views/views.md).</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="4813e-146">限制和局限</span><span class="sxs-lookup"><span data-stu-id="4813e-146">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="4813e-147">如果数据中存在重复的键值，则不能创建唯一索引、UNIQUE 约束或 PRIMARY KEY 约束。</span><span class="sxs-lookup"><span data-stu-id="4813e-147">A unique index, UNIQUE constraint, or PRIMARY KEY constraint cannot be created if duplicate key values exist in the data.</span></span>  
  
-   <span data-ttu-id="4813e-148">唯一非聚集索引可以包括包含性非键列。</span><span class="sxs-lookup"><span data-stu-id="4813e-148">A unique nonclustered index can contain included nonkey columns.</span></span> <span data-ttu-id="4813e-149">有关详细信息，请参阅 [Create Indexes with Included Columns](create-indexes-with-included-columns.md)。</span><span class="sxs-lookup"><span data-stu-id="4813e-149">For more information, see [Create Indexes with Included Columns](create-indexes-with-included-columns.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="4813e-150">Security</span><span class="sxs-lookup"><span data-stu-id="4813e-150">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="4813e-151">权限</span><span class="sxs-lookup"><span data-stu-id="4813e-151">Permissions</span></span>  
 <span data-ttu-id="4813e-152">要求对表或视图具有 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="4813e-152">Requires ALTER permission on the table or view.</span></span> <span data-ttu-id="4813e-153">用户必须是 **sysadmin** 固定服务器角色的成员，或者是 **db_ddladmin** 和 **db_owner** 固定数据库角色的成员。</span><span class="sxs-lookup"><span data-stu-id="4813e-153">User must be a member of the **sysadmin** fixed server role or the **db_ddladmin** and **db_owner** fixed database roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="4813e-154">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4813e-154">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-unique-index-by-using-the-table-designer"></a><span data-ttu-id="4813e-155">使用表设计器创建唯一索引</span><span class="sxs-lookup"><span data-stu-id="4813e-155">To create a unique index by using the Table Designer</span></span>  
  
1.  <span data-ttu-id="4813e-156">在“对象资源管理器”中，展开包含您要创建唯一索引的表的数据库。</span><span class="sxs-lookup"><span data-stu-id="4813e-156">In Object Explorer, expand the database that contains the table on which you want to create a unique index.</span></span>  
  
2.  <span data-ttu-id="4813e-157">展开 **“表”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="4813e-157">Expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="4813e-158">右键单击你要创建唯一索引的表，然后选择“设计”  。</span><span class="sxs-lookup"><span data-stu-id="4813e-158">Right-click the table on which you want to create a unique index and select **Design**.</span></span>  
  
4.  <span data-ttu-id="4813e-159">在“表设计器”  菜单上，选择“索引/键”  。</span><span class="sxs-lookup"><span data-stu-id="4813e-159">On the **Table Designer** menu, select **Indexes/Keys**.</span></span>  
  
5.  <span data-ttu-id="4813e-160">在“索引/键”  对话框中，单击“添加”  。</span><span class="sxs-lookup"><span data-stu-id="4813e-160">In the **Indexes/Keys** dialog box, click **Add**.</span></span>  
  
6.  <span data-ttu-id="4813e-161">从“选定的主/唯一键或索引”  文本框中选择新索引。</span><span class="sxs-lookup"><span data-stu-id="4813e-161">Select the new index in the **Selected Primary/Unique Key or Index** text box.</span></span>  
  
7.  <span data-ttu-id="4813e-162">在主网格中，在“(常规)”  下，选择“类型”  ，然后从列表中选择“索引”  。</span><span class="sxs-lookup"><span data-stu-id="4813e-162">In the main grid, under **(General)**, select **Type** and then choose **Index** from the list.</span></span>  
  
8.  <span data-ttu-id="4813e-163">选择“列”，然后单击省略号 (…)   。</span><span class="sxs-lookup"><span data-stu-id="4813e-163">Select **Columns**, and then click the ellipsis **(...)**.</span></span>  
  
9. <span data-ttu-id="4813e-164">在 **“索引列”** 对话框中的 **“列名”** 下，选择要编制索引的列。</span><span class="sxs-lookup"><span data-stu-id="4813e-164">In the **Index Columns** dialog box, under **Column Name**, select the columns you want to index.</span></span> <span data-ttu-id="4813e-165">最多可选择 16 列。</span><span class="sxs-lookup"><span data-stu-id="4813e-165">You can select up to 16 columns.</span></span> <span data-ttu-id="4813e-166">为获得最佳的性能，请只为每个索引选择一列或两列。</span><span class="sxs-lookup"><span data-stu-id="4813e-166">For optimal performance, select only one or two columns per index.</span></span> <span data-ttu-id="4813e-167">对于所选的每一列，指定索引是以升序还是以降序来排列此列的值。</span><span class="sxs-lookup"><span data-stu-id="4813e-167">For each column you select, indicate whether the index arranges values of this column in ascending or descending order.</span></span>  
  
10. <span data-ttu-id="4813e-168">选择索引的所有列后，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="4813e-168">When all columns for the index are selected, click **OK**.</span></span>  
  
11. <span data-ttu-id="4813e-169">在主网格中，在“(常规)”  下，选择“是唯一的”  ，然后从列表中选择“是”  。</span><span class="sxs-lookup"><span data-stu-id="4813e-169">In the grid, under **(General)**, select **Is Unique** and then choose **Yes** from the list.</span></span>  
  
12. <span data-ttu-id="4813e-170">可选：在主网格中，在 **“表设计器”** 下，选择 **“忽略重复键”** ，然后从列表中选择 **“是”** 。</span><span class="sxs-lookup"><span data-stu-id="4813e-170">Optional: In the main grid, under **Table Designer**, select **Ignore Duplicate Keys** and then choose **Yes** from the list.</span></span> <span data-ttu-id="4813e-171">如果要忽略尝试添加导致唯一索引中有重复键的数据，请这样做。</span><span class="sxs-lookup"><span data-stu-id="4813e-171">Do this if you want to ignore attempts to add data that would create a duplicate key in the unique index.</span></span>  
  
13. <span data-ttu-id="4813e-172">单击“关闭”  。</span><span class="sxs-lookup"><span data-stu-id="4813e-172">Click **Close**.</span></span>  
  
14. <span data-ttu-id="4813e-173">在“文件”\*\*\*\* 菜单上，单击“保存”\*\*\*\* 以保存 _table_name_。</span><span class="sxs-lookup"><span data-stu-id="4813e-173">On the **File** menu, click **Save**_table_name_.</span></span>  
  
#### <a name="create-a-unique-index-by-using-object-explorer"></a><span data-ttu-id="4813e-174">使用对象资源管理器创建唯一索引</span><span class="sxs-lookup"><span data-stu-id="4813e-174">Create a unique index by using Object Explorer</span></span>  
  
1.  <span data-ttu-id="4813e-175">在“对象资源管理器”中，展开包含您要创建唯一索引的表的数据库。</span><span class="sxs-lookup"><span data-stu-id="4813e-175">In Object Explorer, expand the database that contains the table on which you want to create a unique index.</span></span>  
  
2.  <span data-ttu-id="4813e-176">展开 **“表”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="4813e-176">Expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="4813e-177">展开要为其创建唯一索引的表。</span><span class="sxs-lookup"><span data-stu-id="4813e-177">Expand the table on which you want to create a unique index.</span></span>  
  
4.  <span data-ttu-id="4813e-178">右键单击“索引”文件夹，指向“新建索引”，然后选择“非群集索引…”    。</span><span class="sxs-lookup"><span data-stu-id="4813e-178">Right-click the **Indexes** folder, point to **New Index**, and select **Non-Clustered Index...**.</span></span>  
  
5.  <span data-ttu-id="4813e-179">在 **“新建索引”** 对话框的 **“常规”** 页中，在 **“索引名称”** 框中输入新索引的名称。</span><span class="sxs-lookup"><span data-stu-id="4813e-179">In the **New Index** dialog box, on the **General** page, enter the name of the new index in the **Index name** box.</span></span>  
  
6.  <span data-ttu-id="4813e-180">选中 **“唯一”** 复选框。</span><span class="sxs-lookup"><span data-stu-id="4813e-180">Select the **Unique** check box.</span></span>  
  
7.  <span data-ttu-id="4813e-181">在“索引键列”下，单击“添加…”   。</span><span class="sxs-lookup"><span data-stu-id="4813e-181">Under **Index key columns**, click **Add...**.</span></span>  
  
8.  <span data-ttu-id="4813e-182">在 "**从**_Table_name_中选择列" 对话框中，选中要添加到唯一索引的一个或多个表列的复选框。</span><span class="sxs-lookup"><span data-stu-id="4813e-182">In the **Select Columns from**_table_name_ dialog box, select the check box or check boxes of the table column or columns to be added to the unique index.</span></span>  
  
9. <span data-ttu-id="4813e-183">单击“确定”。 </span><span class="sxs-lookup"><span data-stu-id="4813e-183">Click **OK**.</span></span>  
  
10. <span data-ttu-id="4813e-184">在 **“新建索引”** 对话框中，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="4813e-184">In the **New Index** dialog box, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="4813e-185">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4813e-185">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-unique-index-on-a-table"></a><span data-ttu-id="4813e-186">创建表的唯一索引</span><span class="sxs-lookup"><span data-stu-id="4813e-186">To create a unique index on a table</span></span>  
  
1.  <span data-ttu-id="4813e-187">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="4813e-187">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="4813e-188">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="4813e-188">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="4813e-189">将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。</span><span class="sxs-lookup"><span data-stu-id="4813e-189">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Find an existing index named AK_UnitMeasure_Name and delete it if found  
    IF EXISTS (SELECT name from sys.indexes  
               WHERE name = N'AK_UnitMeasure_Name')   
       DROP INDEX AK_UnitMeasure_Name ON Production.UnitMeasure;   
    GO  
    -- Create a unique index called AK_UnitMeasure_Name  
    -- on the Production.UnitMeasure table using the Name column.  
    CREATE UNIQUE INDEX AK_UnitMeasure_Name   
       ON Production.UnitMeasure (Name);   
    GO  
    ```  
  
 <span data-ttu-id="4813e-190">有关详细信息，请参阅 [CREATE INDEX (Transact-SQL)](/sql/t-sql/statements/create-index-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="4813e-190">For more information, see [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql).</span></span>  
  
  
