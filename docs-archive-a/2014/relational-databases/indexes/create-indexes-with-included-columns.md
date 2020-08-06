---
title: 创建带有包含列的索引 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- index size [SQL Server]
- index keys [SQL Server]
- index columns [SQL Server]
- size [SQL Server], indexes
- key columns [SQL Server]
- included columns
- nonclustered indexes [SQL Server], included columns
- designing indexes [SQL Server], included columns
- nonkey columns
ms.assetid: d198648d-fea5-416d-9f30-f9d4aebbf4ec
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e5a464f9791ea635236069555647229bf1f0d79e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693313"
---
# <a name="create-indexes-with-included-columns"></a><span data-ttu-id="d3dca-102">创建带有包含列的索引</span><span class="sxs-lookup"><span data-stu-id="d3dca-102">Create Indexes with Included Columns</span></span>
  <span data-ttu-id="d3dca-103">本主题说明如何通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，添加包含列（或非键列）以便在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中扩展非聚集索引的功能。</span><span class="sxs-lookup"><span data-stu-id="d3dca-103">This topic describes how to add included (or nonkey) columns to extend the functionality of nonclustered indexes in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="d3dca-104">通过包含非键列，可以创建覆盖更多查询的非聚集索引。</span><span class="sxs-lookup"><span data-stu-id="d3dca-104">By including nonkey columns, you can create nonclustered indexes that cover more queries.</span></span> <span data-ttu-id="d3dca-105">这是因为非键列具有下列优点：</span><span class="sxs-lookup"><span data-stu-id="d3dca-105">This is because the nonkey columns have the following benefits:</span></span>  
  
-   <span data-ttu-id="d3dca-106">它们可以是不允许作为索引键列的数据类型。</span><span class="sxs-lookup"><span data-stu-id="d3dca-106">They can be data types not allowed as index key columns.</span></span>  
  
-   <span data-ttu-id="d3dca-107">在计算索引键列数或索引键大小时， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 不考虑它们。</span><span class="sxs-lookup"><span data-stu-id="d3dca-107">They are not considered by the [!INCLUDE[ssDE](../../includes/ssde-md.md)] when calculating the number of index key columns or index key size.</span></span>  
  
 <span data-ttu-id="d3dca-108">当查询中的所有列都作为键列或非键列包含在索引中时，带有包含性非键列的索引可以显著提高查询性能。</span><span class="sxs-lookup"><span data-stu-id="d3dca-108">An index with nonkey columns can significantly improve query performance when all columns in the query are included in the index either as key or nonkey columns.</span></span> <span data-ttu-id="d3dca-109">这样可以实现性能提升，因为查询优化器可以在索引中找到所有列值；不访问表或聚集索引数据，从而减少磁盘 I/O 操作。</span><span class="sxs-lookup"><span data-stu-id="d3dca-109">Performance gains are achieved because the query optimizer can locate all the column values within the index; table or clustered index data is not accessed resulting in fewer disk I/O operations.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d3dca-110">当索引包含查询引用的所有列时，它通常称为“覆盖查询”。</span><span class="sxs-lookup"><span data-stu-id="d3dca-110">When an index contains all the columns referenced by a query it is typically referred to as *covering the query*.</span></span>  
  
 <span data-ttu-id="d3dca-111">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="d3dca-111">**In This Topic**</span></span>  
  
-   <span data-ttu-id="d3dca-112">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="d3dca-112">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="d3dca-113">设计建议</span><span class="sxs-lookup"><span data-stu-id="d3dca-113">Design Recommendations</span></span>](#DesignRecs)  
  
     [<span data-ttu-id="d3dca-114">限制和局限</span><span class="sxs-lookup"><span data-stu-id="d3dca-114">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="d3dca-115">安全性</span><span class="sxs-lookup"><span data-stu-id="d3dca-115">Security</span></span>](#Security)  
  
-   <span data-ttu-id="d3dca-116">**若要创建带有非键列的索引，请使用：**</span><span class="sxs-lookup"><span data-stu-id="d3dca-116">**To create an index with nonkey columns, using:**</span></span>  
  
     [<span data-ttu-id="d3dca-117">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="d3dca-117">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="d3dca-118">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="d3dca-118">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="d3dca-119">开始之前</span><span class="sxs-lookup"><span data-stu-id="d3dca-119">Before You Begin</span></span>  
  
###  <a name="design-recommendations"></a><a name="DesignRecs"></a> <span data-ttu-id="d3dca-120">设计建议</span><span class="sxs-lookup"><span data-stu-id="d3dca-120">Design Recommendations</span></span>  
  
-   <span data-ttu-id="d3dca-121">重新设计索引键大小较大的非聚集索引，以便只有用于搜索和查找的列为键列。</span><span class="sxs-lookup"><span data-stu-id="d3dca-121">Redesign nonclustered indexes with a large index key size so that only columns used for searching and lookups are key columns.</span></span> <span data-ttu-id="d3dca-122">使覆盖查询的所有其他列成为非键列。</span><span class="sxs-lookup"><span data-stu-id="d3dca-122">Make all other columns that cover the query into nonkey columns.</span></span> <span data-ttu-id="d3dca-123">这样，将具有覆盖查询所需的所有列，但索引键本身较小，而且效率高。</span><span class="sxs-lookup"><span data-stu-id="d3dca-123">In this way, you will have all columns needed to cover the query, but the index key itself is small and efficient.</span></span>  
  
-   <span data-ttu-id="d3dca-124">将非键列包含在非聚集索引中，以避免超过当前索引大小的限制（最大键列数为 16，最大索引键大小为 900 字节）。</span><span class="sxs-lookup"><span data-stu-id="d3dca-124">Include nonkey columns in a nonclustered index to avoid exceeding the current index size limitations of a maximum of 16 key columns and a maximum index key size of 900 bytes.</span></span> <span data-ttu-id="d3dca-125">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 计算索引键列数或索引键大小时，不考虑非键列。</span><span class="sxs-lookup"><span data-stu-id="d3dca-125">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] does not consider nonkey columns when calculating the number of index key columns or index key size.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="d3dca-126">限制和局限</span><span class="sxs-lookup"><span data-stu-id="d3dca-126">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="d3dca-127">只能对非聚集索引定义非键列。</span><span class="sxs-lookup"><span data-stu-id="d3dca-127">Nonkey columns can only be defined on nonclustered indexes.</span></span>  
  
-   <span data-ttu-id="d3dca-128">除了 `text`、`ntext` 和 `image` 之外的所有数据类型都可以用作非键列。</span><span class="sxs-lookup"><span data-stu-id="d3dca-128">All data types except `text`, `ntext`, and `image` can be used as nonkey columns.</span></span>  
  
-   <span data-ttu-id="d3dca-129">精确或不精确的确定性计算列都可以是非键列。</span><span class="sxs-lookup"><span data-stu-id="d3dca-129">Computed columns that are deterministic and either precise or imprecise can be nonkey columns.</span></span> <span data-ttu-id="d3dca-130">有关详细信息，请参阅 [计算列上的索引](indexes-on-computed-columns.md)。</span><span class="sxs-lookup"><span data-stu-id="d3dca-130">For more information, see [Indexes on Computed Columns](indexes-on-computed-columns.md).</span></span>  
  
-   <span data-ttu-id="d3dca-131">只要允许将计算列数据类型作为非键索引列，从 `image`、`ntext` 和 `text` 数据类型派生的计算列就可以作为非键索引列。</span><span class="sxs-lookup"><span data-stu-id="d3dca-131">Computed columns derived from `image`, `ntext`, and `text` data types can be nonkey columns as long as the computed column data type is allowed as a nonkey index column.</span></span>  
  
-   <span data-ttu-id="d3dca-132">除非先删除某一表的索引，否则无法从该表中删除非键列。</span><span class="sxs-lookup"><span data-stu-id="d3dca-132">Nonkey columns cannot be dropped from a table unless that table's index is dropped first.</span></span>  
  
-   <span data-ttu-id="d3dca-133">除进行下列更改外，不能对非键列进行其他更改：</span><span class="sxs-lookup"><span data-stu-id="d3dca-133">Nonkey columns cannot be changed, except to do the following:</span></span>  
  
    -   <span data-ttu-id="d3dca-134">将列的为空性从 NOT NULL 改为 NULL。</span><span class="sxs-lookup"><span data-stu-id="d3dca-134">Change the nullability of the column from NOT NULL to NULL.</span></span>  
  
    -   <span data-ttu-id="d3dca-135">增加 `varchar`、`nvarchar` 或 `varbinary` 列的长度。</span><span class="sxs-lookup"><span data-stu-id="d3dca-135">Increase the length of `varchar`, `nvarchar`, or `varbinary` columns.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="d3dca-136">Security</span><span class="sxs-lookup"><span data-stu-id="d3dca-136">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="d3dca-137">权限</span><span class="sxs-lookup"><span data-stu-id="d3dca-137">Permissions</span></span>  
 <span data-ttu-id="d3dca-138">要求对表或视图具有 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="d3dca-138">Requires ALTER permission on the table or view.</span></span> <span data-ttu-id="d3dca-139">用户必须是 **sysadmin** 固定服务器角色的成员，或者是 **db_ddladmin** 和 **db_owner** 固定数据库角色的成员。</span><span class="sxs-lookup"><span data-stu-id="d3dca-139">User must be a member of the **sysadmin** fixed server role or the **db_ddladmin** and **db_owner** fixed database roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="d3dca-140">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="d3dca-140">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-an-index-with-nonkey-columns"></a><span data-ttu-id="d3dca-141">创建带有非键列的索引</span><span class="sxs-lookup"><span data-stu-id="d3dca-141">To create an index with nonkey columns</span></span>  
  
1.  <span data-ttu-id="d3dca-142">在对象资源管理器中，单击加号以便展开包含您要创建带有非键列的索引的表的数据库。</span><span class="sxs-lookup"><span data-stu-id="d3dca-142">In Object Explorer, click the plus sign to expand the database that contains the table on which you want to create an index with nonkey columns.</span></span>  
  
2.  <span data-ttu-id="d3dca-143">单击加号以便展开 **“表”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="d3dca-143">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="d3dca-144">单击加号以便展开您要创建带有非键列的索引的表。</span><span class="sxs-lookup"><span data-stu-id="d3dca-144">Click the plus sign to expand the table on which you want to create an index with nonkey columns.</span></span>  
  
4.  <span data-ttu-id="d3dca-145">右键单击“索引”文件夹，指向“新建索引”，然后选择“非群集索引…”  。</span><span class="sxs-lookup"><span data-stu-id="d3dca-145">Right-click the **Indexes** folder, point to **New Index**, and select **Non-Clustered Index...**.</span></span>  
  
5.  <span data-ttu-id="d3dca-146">在 **“新建索引”** 对话框的 **“常规”** 页中，在 **“索引名称”** 框中输入新索引的名称。</span><span class="sxs-lookup"><span data-stu-id="d3dca-146">In the **New Index** dialog box, on the **General** page, enter the name of the new index in the **Index name** box.</span></span>  
  
6.  <span data-ttu-id="d3dca-147">在“索引键列”选项卡下，单击“添加…” 。</span><span class="sxs-lookup"><span data-stu-id="d3dca-147">Under the **Index key columns** tab, click **Add...**.</span></span>  
  
7.  <span data-ttu-id="d3dca-148">在 "**从**_Table_name_中选择列" 对话框中，选中要添加到索引的一个或多个表列的复选框。</span><span class="sxs-lookup"><span data-stu-id="d3dca-148">In the **Select Columns from**_table_name_ dialog box, select the check box or check boxes of the table column or columns to be added to the index.</span></span>  
  
8.  <span data-ttu-id="d3dca-149">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="d3dca-149">Click **OK**.</span></span>  
  
9. <span data-ttu-id="d3dca-150">在“包含性列”选项卡下，单击“添加…” 。</span><span class="sxs-lookup"><span data-stu-id="d3dca-150">Under the **Included columns** tab, click **Add...**.</span></span>  
  
10. <span data-ttu-id="d3dca-151">在 "**从**_Table_name_中选择列" 对话框中，选中要作为非键列添加到索引的一个或多个表列的复选框。</span><span class="sxs-lookup"><span data-stu-id="d3dca-151">In the **Select Columns from**_table_name_ dialog box, select the check box or check boxes of the table column or columns to be added to the index as nonkey columns.</span></span>  
  
11. <span data-ttu-id="d3dca-152">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="d3dca-152">Click **OK**.</span></span>  
  
12. <span data-ttu-id="d3dca-153">在 **“新建索引”** 对话框中，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="d3dca-153">In the **New Index** dialog box, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="d3dca-154">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="d3dca-154">Using Transact-SQL</span></span>  
  
#### <a name="to-create-an-index-with-nonkey-columns"></a><span data-ttu-id="d3dca-155">创建带有非键列的索引</span><span class="sxs-lookup"><span data-stu-id="d3dca-155">To create an index with nonkey columns</span></span>  
  
1.  <span data-ttu-id="d3dca-156">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="d3dca-156">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="d3dca-157">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="d3dca-157">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="d3dca-158">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="d3dca-158">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Creates a nonclustered index on the Person.Address table with four included (nonkey) columns.   
    -- index key column is PostalCode and the nonkey columns are  
    -- AddressLine1, AddressLine2, City, and StateProvinceID.  
    CREATE NONCLUSTERED INDEX IX_Address_PostalCode  
    ON Person.Address (PostalCode)  
    INCLUDE (AddressLine1, AddressLine2, City, StateProvinceID);  
    GO  
    ```  
  
 <span data-ttu-id="d3dca-159">有关详细信息，请参阅 [CREATE INDEX (Transact-SQL)](/sql/t-sql/statements/create-index-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="d3dca-159">For more information, see [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql).</span></span>  
  
  
