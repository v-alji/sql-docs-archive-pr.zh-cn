---
title: 创建非聚集索引 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- index creation [SQL Server], nonclustered indexes
- nonclustered indexes [SQL Server], creating
- nonclustered indexes [SQL Server], UNIQUE constraint
- indexes [SQL Server], nonclustered
- nonclustered indexes [SQL Server], PRIMARY KEY constraint
ms.assetid: 9402029a-1227-46c4-93aa-c2122eb1b943
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: fae0c06b1f562dc3fc518a319df1787b3384c0cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693306"
---
# <a name="create-nonclustered-indexes"></a><span data-ttu-id="60659-102">创建非聚集索引</span><span class="sxs-lookup"><span data-stu-id="60659-102">Create Nonclustered Indexes</span></span>
  <span data-ttu-id="60659-103">您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中创建非聚集索引。</span><span class="sxs-lookup"><span data-stu-id="60659-103">You can create nonclustered indexes in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="60659-104">非聚集索引是一种与存储在表中的数据相分离的索引结构，可对一个或多个选定列重新排序。</span><span class="sxs-lookup"><span data-stu-id="60659-104">A nonclustered index is an index structure separate from the data stored in a table that reorders one or more selected columns.</span></span> <span data-ttu-id="60659-105">非聚集索引通常可帮助您通过比搜索基础表更快的速度查找数据；有时可以完全由非聚集索引中的数据回答查询，或非聚集索引可将 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 指向基础表中的行。</span><span class="sxs-lookup"><span data-stu-id="60659-105">Nonclustered indexes can often help you find data more quickly than searching the underlying table; queries can sometimes be answered entirely by the data in the nonclustered index, or the nonclustered index can point the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to the rows in the underlying table.</span></span> <span data-ttu-id="60659-106">一般来说，创建非聚集索引是为了提高聚集索引不涵盖的频繁使用的查询的性能，或在没有聚集索引的表（称为堆）中查找行。</span><span class="sxs-lookup"><span data-stu-id="60659-106">Generally, nonclustered indexes are created to improve the performance of frequently used queries not covered by the clustered index or to locate rows in a table without a clustered index (called a heap).</span></span> <span data-ttu-id="60659-107">可以对表或索引视图创建多个非聚集索引。</span><span class="sxs-lookup"><span data-stu-id="60659-107">You can create multiple nonclustered indexes on a table or indexed view.</span></span>  
  
 <span data-ttu-id="60659-108">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="60659-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="60659-109">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="60659-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="60659-110">典型实现</span><span class="sxs-lookup"><span data-stu-id="60659-110">Typical Implementations</span></span>](#Implementations)  
  
     [<span data-ttu-id="60659-111">安全性</span><span class="sxs-lookup"><span data-stu-id="60659-111">Security</span></span>](#Security)  
  
-   <span data-ttu-id="60659-112">**若要创建非聚集索引，请使用：**</span><span class="sxs-lookup"><span data-stu-id="60659-112">**To create a nonclustered index, using:**</span></span>  
  
     [<span data-ttu-id="60659-113">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="60659-113">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="60659-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="60659-114">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="60659-115">开始之前</span><span class="sxs-lookup"><span data-stu-id="60659-115">Before You Begin</span></span>  
  
###  <a name="typical-implementations"></a><a name="Implementations"></a><span data-ttu-id="60659-116">典型实现</span><span class="sxs-lookup"><span data-stu-id="60659-116">Typical Implementations</span></span>  
 <span data-ttu-id="60659-117">可以通过下列方法实现非聚集索引：</span><span class="sxs-lookup"><span data-stu-id="60659-117">Nonclustered indexes are implemented in the following ways:</span></span>  
  
-   <span data-ttu-id="60659-118">**UNIQUE 约束**</span><span class="sxs-lookup"><span data-stu-id="60659-118">**UNIQUE constraints**</span></span>  
  
     <span data-ttu-id="60659-119">在创建 UNIQUE 约束时，默认情况下将创建唯一非聚集索引，以便强制 UNIQUE 约束。</span><span class="sxs-lookup"><span data-stu-id="60659-119">When you create a UNIQUE constraint, a unique nonclustered index is created to enforce a UNIQUE constraint by default.</span></span> <span data-ttu-id="60659-120">如果不存在该表的聚集索引，则可以指定唯一聚集索引。</span><span class="sxs-lookup"><span data-stu-id="60659-120">You can specify a unique clustered index if a clustered index on the table does not already exist.</span></span> <span data-ttu-id="60659-121">有关详细信息，请参阅 [Unique Constraints and Check Constraints](../tables/unique-constraints-and-check-constraints.md)。</span><span class="sxs-lookup"><span data-stu-id="60659-121">For more information, see [Unique Constraints and Check Constraints](../tables/unique-constraints-and-check-constraints.md).</span></span>  
  
-   <span data-ttu-id="60659-122">**独立于约束的索引**</span><span class="sxs-lookup"><span data-stu-id="60659-122">**Index independent of a constraint**</span></span>  
  
     <span data-ttu-id="60659-123">默认情况下，如果未指定聚集，将创建非聚集索引。</span><span class="sxs-lookup"><span data-stu-id="60659-123">By default, a nonclustered index is created if clustered is not specified.</span></span> <span data-ttu-id="60659-124">对于每个表可创建的最大非聚集索引数为 999。</span><span class="sxs-lookup"><span data-stu-id="60659-124">The maximum number of nonclustered indexes that can be created per table is 999.</span></span> <span data-ttu-id="60659-125">这包括使用 PRIMARY KEY 或 UNIQUE 约束创建的任何索引，但不包括 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="60659-125">This includes any indexes created by PRIMARY KEY or UNIQUE constraints, but does not include XML indexes.</span></span>  
  
-   <span data-ttu-id="60659-126">**索引视图的非聚集索引**</span><span class="sxs-lookup"><span data-stu-id="60659-126">**Nonclustered index on an indexed view**</span></span>  
  
     <span data-ttu-id="60659-127">对视图创建唯一的聚集索引后，便可以创建非聚集索引。</span><span class="sxs-lookup"><span data-stu-id="60659-127">After a unique clustered index has been created on a view, nonclustered indexes can be created.</span></span> <span data-ttu-id="60659-128">有关详细信息，请参阅 [创建索引视图](../views/views.md)。</span><span class="sxs-lookup"><span data-stu-id="60659-128">For more information, see [Create Indexed Views](../views/views.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="60659-129">Security</span><span class="sxs-lookup"><span data-stu-id="60659-129">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="60659-130">权限</span><span class="sxs-lookup"><span data-stu-id="60659-130">Permissions</span></span>  
 <span data-ttu-id="60659-131">要求对表或视图具有 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="60659-131">Requires ALTER permission on the table or view.</span></span> <span data-ttu-id="60659-132">用户必须是 **sysadmin** 固定服务器角色的成员，或者是 **db_ddladmin** 和 **db_owner** 固定数据库角色的成员。</span><span class="sxs-lookup"><span data-stu-id="60659-132">User must be a member of the **sysadmin** fixed server role or the **db_ddladmin** and **db_owner** fixed database roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="60659-133">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="60659-133">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-nonclustered-index-by-using-the-table-designer"></a><span data-ttu-id="60659-134">使用表设计器创建非聚集索引</span><span class="sxs-lookup"><span data-stu-id="60659-134">To create a nonclustered index by using the Table Designer</span></span>  
  
1.  <span data-ttu-id="60659-135">在“对象资源管理器”中，展开其中包含您要创建非聚集索引的表的数据库。</span><span class="sxs-lookup"><span data-stu-id="60659-135">In Object Explorer, expand the database that contains the table on which you want to create a nonclustered index.</span></span>  
  
2.  <span data-ttu-id="60659-136">展开 **“表”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="60659-136">Expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="60659-137">右键单击你要创建非聚集索引的表，然后选择“设计”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="60659-137">Right-click the table on which you want to create a nonclustered index and select **Design**.</span></span>  
  
4.  <span data-ttu-id="60659-138">在 "**表设计器**" 菜单上，单击 "**索引/键**"。</span><span class="sxs-lookup"><span data-stu-id="60659-138">On the **Table Designer** menu, click **Indexes/Keys**.</span></span>  
  
5.  <span data-ttu-id="60659-139">在“索引/键”\*\*\*\* 对话框中，单击“添加”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="60659-139">In the **Indexes/Keys** dialog box, click **Add**.</span></span>  
  
6.  <span data-ttu-id="60659-140">从“选定的主/唯一键或索引”\*\*\*\* 文本框中选择新索引。</span><span class="sxs-lookup"><span data-stu-id="60659-140">Select the new index in the **Selected Primary/Unique Key or Index** text box.</span></span>  
  
7.  <span data-ttu-id="60659-141">在网格中，选择“创建为聚集”\*\*\*\*，然后从该属性右侧的下拉列表中选择“否”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="60659-141">In the grid, select **Create as Clustered**, and choose **No** from the drop-down list to the right of the property.</span></span>  
  
8.  <span data-ttu-id="60659-142">单击 **“关闭”** 。</span><span class="sxs-lookup"><span data-stu-id="60659-142">Click **Close**.</span></span>  
  
9. <span data-ttu-id="60659-143">在“文件”\*\*\*\* 菜单上，单击“保存”\*\*\*\* 以保存 _table_name_。</span><span class="sxs-lookup"><span data-stu-id="60659-143">On the **File** menu, click **Save**_table_name_.</span></span>  
  
#### <a name="to-create-a-nonclustered-index-by-using-object-explorer"></a><span data-ttu-id="60659-144">使用对象资源管理器创建非聚集索引</span><span class="sxs-lookup"><span data-stu-id="60659-144">To create a nonclustered index by using Object Explorer</span></span>  
  
1.  <span data-ttu-id="60659-145">在“对象资源管理器”中，展开其中包含您要创建非聚集索引的表的数据库。</span><span class="sxs-lookup"><span data-stu-id="60659-145">In Object Explorer, expand the database that contains the table on which you want to create a nonclustered index.</span></span>  
  
2.  <span data-ttu-id="60659-146">展开 **“表”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="60659-146">Expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="60659-147">展开要为其创建非聚集索引的表。</span><span class="sxs-lookup"><span data-stu-id="60659-147">Expand the table on which you want to create a nonclustered index.</span></span>  
  
4.  <span data-ttu-id="60659-148">右键单击“索引”文件夹，指向“新建索引”，然后选择“非群集索引…”  。</span><span class="sxs-lookup"><span data-stu-id="60659-148">Right-click the **Indexes** folder, point to **New Index**, and select **Non-Clustered Index...**.</span></span>  
  
5.  <span data-ttu-id="60659-149">在 **“新建索引”** 对话框的 **“常规”** 页中，在 **“索引名称”** 框中输入新索引的名称。</span><span class="sxs-lookup"><span data-stu-id="60659-149">In the **New Index** dialog box, on the **General** page, enter the name of the new index in the **Index name** box.</span></span>  
  
6.  <span data-ttu-id="60659-150">在“索引键列”下，单击“添加…” 。</span><span class="sxs-lookup"><span data-stu-id="60659-150">Under **Index key columns**, click **Add...**.</span></span>  
  
7.  <span data-ttu-id="60659-151">在“从 table_name 中选择列”\*\*\*\*__ 对话框中，选中要添加到非聚集索引的一个或多个表列的复选框。</span><span class="sxs-lookup"><span data-stu-id="60659-151">In the **Select Columns from**_table_name_ dialog box, select the check box or check boxes of the table column or columns to be added to the nonclustered index.</span></span>  
  
8.  <span data-ttu-id="60659-152">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="60659-152">Click **OK**.</span></span>  
  
9. <span data-ttu-id="60659-153">在 **“新建索引”** 对话框中，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="60659-153">In the **New Index** dialog box, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="60659-154">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="60659-154">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-nonclustered-index-on-a-table"></a><span data-ttu-id="60659-155">对表创建非聚集索引</span><span class="sxs-lookup"><span data-stu-id="60659-155">To create a nonclustered index on a table</span></span>  
  
1.  <span data-ttu-id="60659-156">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="60659-156">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="60659-157">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="60659-157">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="60659-158">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="60659-158">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Find an existing index named IX_ProductVendor_VendorID and delete it if found.   
    IF EXISTS (SELECT name FROM sys.indexes  
                WHERE name = N'IX_ProductVendor_VendorID')   
        DROP INDEX IX_ProductVendor_VendorID ON Purchasing.ProductVendor;   
    GO  
    -- Create a nonclustered index called IX_ProductVendor_VendorID   
    -- on the Purchasing.ProductVendor table using the BusinessEntityID column.   
    CREATE NONCLUSTERED INDEX IX_ProductVendor_VendorID   
        ON Purchasing.ProductVendor (BusinessEntityID);   
    GO  
    ```  
  
 <span data-ttu-id="60659-159">有关详细信息，请参阅 [CREATE INDEX (Transact-SQL)](/sql/t-sql/statements/create-index-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="60659-159">For more information, see [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql).</span></span>  
  
  
