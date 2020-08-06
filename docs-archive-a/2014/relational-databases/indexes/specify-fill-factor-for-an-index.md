---
title: 为索引指定填充因子 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- fill factor [SQL Server]
- page splits [SQL Server]
ms.assetid: 237a577e-b42b-4adb-90cf-aa7fb174f3ab
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ac54f2b22de55ed74c4635ec0f86d008c7624a42
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692918"
---
# <a name="specify-fill-factor-for-an-index"></a><span data-ttu-id="1393e-102">为索引指定填充因子</span><span class="sxs-lookup"><span data-stu-id="1393e-102">Specify Fill Factor for an Index</span></span>
  <span data-ttu-id="1393e-103">本主题说明什么是填充因子以及如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中指定索引的填充因子值。</span><span class="sxs-lookup"><span data-stu-id="1393e-103">This topic describes what fill factor is and how to specify a fill factor value on an index in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="1393e-104">提供填充因子选项是为了优化索引数据存储和性能。</span><span class="sxs-lookup"><span data-stu-id="1393e-104">The fill-factor option is provided for fine-tuning index data storage and performance.</span></span> <span data-ttu-id="1393e-105">当创建或重新生成索引时，填充因子的值可确定每个叶级页上要填充数据的空间百分比，以便在每一页上保留一些剩余空间作为以后扩展索引的可用空间。</span><span class="sxs-lookup"><span data-stu-id="1393e-105">When an index is created or rebuilt, the fill-factor value determines the percentage of space on each leaf-level page to be filled with data, reserving the remainder on each page as free space for future growth.</span></span> <span data-ttu-id="1393e-106">例如，指定填充因子的值为 80 表示每个叶级页上将有 20% 的空间保留为空，以便随着向基础表中添加数据而为扩展索引提供空间。</span><span class="sxs-lookup"><span data-stu-id="1393e-106">For example, specifying a fill-factor value of 80 means that 20 percent of each leaf-level page will be left empty, providing space for index expansion as data is added to the underlying table.</span></span> <span data-ttu-id="1393e-107">在索引行之间保留可用空间，而不是在索引的末尾保留。</span><span class="sxs-lookup"><span data-stu-id="1393e-107">The empty space is reserved between the index rows rather than at the end of the index.</span></span>  
  
 <span data-ttu-id="1393e-108">填充因子的值是 1 到 100 之间的百分比，服务器范围的默认值为 0，这表示将完全填充叶级页。</span><span class="sxs-lookup"><span data-stu-id="1393e-108">The fill-factor value is a percentage from 1 to 100, and the server-wide default is 0 which means that the leaf-level pages are filled to capacity.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1393e-109">填充因子的值 0 和 100 在所有方面都是相同的。</span><span class="sxs-lookup"><span data-stu-id="1393e-109">Fill-factor values 0 and 100 are the same in all respects.</span></span>  
  
 <span data-ttu-id="1393e-110">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="1393e-110">**In This Topic**</span></span>  
  
-   <span data-ttu-id="1393e-111">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="1393e-111">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="1393e-112">性能注意事项</span><span class="sxs-lookup"><span data-stu-id="1393e-112">Performance Considerations</span></span>](#Performance)  
  
     [<span data-ttu-id="1393e-113">安全性</span><span class="sxs-lookup"><span data-stu-id="1393e-113">Security</span></span>](#Security)  
  
-   <span data-ttu-id="1393e-114">**为索引指定填充因子，使用：**</span><span class="sxs-lookup"><span data-stu-id="1393e-114">**To specify a fill factor in an index, using:**</span></span>  
  
     [<span data-ttu-id="1393e-115">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1393e-115">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="1393e-116">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1393e-116">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="1393e-117">开始之前</span><span class="sxs-lookup"><span data-stu-id="1393e-117">Before You Begin</span></span>  
  
###  <a name="performance-considerations"></a><a name="Performance"></a> <span data-ttu-id="1393e-118">性能注意事项</span><span class="sxs-lookup"><span data-stu-id="1393e-118">Performance Considerations</span></span>  
  
#### <a name="page-splits"></a><span data-ttu-id="1393e-119">页拆分</span><span class="sxs-lookup"><span data-stu-id="1393e-119">Page Splits</span></span>  
 <span data-ttu-id="1393e-120">正确选择填充因子值可提供足够的空间，以便随着向基础表中添加数据而扩展索引，从而降低页拆分的可能性。如果向已满的索引页添加新行， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 将把大约一半的行移到新页中，以便为该新行腾出空间。</span><span class="sxs-lookup"><span data-stu-id="1393e-120">A correctly chosen fill-factor value can reduce potential page splits by providing enough space for index expansion as data is added to the underlying table.When a new row is added to a full index page, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] moves approximately half the rows to a new page to make room for the new row.</span></span> <span data-ttu-id="1393e-121">这种重组称为页拆分。</span><span class="sxs-lookup"><span data-stu-id="1393e-121">This reorganization is known as a page split.</span></span> <span data-ttu-id="1393e-122">页拆分可为新记录腾出空间，但是执行页拆分可能需要花费一定的时间，此操作会消耗大量资源。</span><span class="sxs-lookup"><span data-stu-id="1393e-122">A page split makes room for new records, but can take time to perform and is a resource intensive operation.</span></span> <span data-ttu-id="1393e-123">此外，它还可能造成碎片，从而导致 I/O 操作增加。</span><span class="sxs-lookup"><span data-stu-id="1393e-123">Also, it can cause fragmentation that causes increased I/O operations.</span></span> <span data-ttu-id="1393e-124">如果经常发生页拆分，可通过使用新的或现有的填充因子值来重新生成索引，从而重新分发数据。</span><span class="sxs-lookup"><span data-stu-id="1393e-124">When frequent page splits occur, the index can be rebuilt by using a new or existing fill-factor value to redistribute the data.</span></span> <span data-ttu-id="1393e-125">有关详细信息，请参阅 [重新组织和重新生成索引](reorganize-and-rebuild-indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="1393e-125">For more information, see [Reorganize and Rebuild Indexes](reorganize-and-rebuild-indexes.md).</span></span>  
  
 <span data-ttu-id="1393e-126">虽然采用较小的非零填充因子值可减少随着索引的增长而拆分页的需求，但是索引将需要更多的存储空间，并且会降低读取性能。</span><span class="sxs-lookup"><span data-stu-id="1393e-126">Although a low, nonzero fill-factor value may reduce the requirement to split pages as the index grows, the index will require more storage space and can decrease read performance.</span></span> <span data-ttu-id="1393e-127">即使对于面向许多插入和更新操作的应用程序，数据库的读取次数一般也会超过数据库写入次数的 5 到 10 倍。</span><span class="sxs-lookup"><span data-stu-id="1393e-127">Even for an application oriented for many insert and update operations, the number of database reads typically outnumber database writes by a factor of 5 to 10.</span></span> <span data-ttu-id="1393e-128">因此，指定一个不同于默认值的填充因子会降低数据库的读取性能，而降低量与填充因子设置的值成反比。</span><span class="sxs-lookup"><span data-stu-id="1393e-128">Therefore, specifying a fill factor other than the default can decrease database read performance by an amount inversely proportional to the fill-factor setting.</span></span> <span data-ttu-id="1393e-129">例如，当填充因子的值为 50 时，数据库的读取性能会降低两倍。</span><span class="sxs-lookup"><span data-stu-id="1393e-129">For example, a fill-factor value of 50 can cause database read performance to decrease by two times.</span></span> <span data-ttu-id="1393e-130">读取性能降低是因为索引包含较多的页，因此增加了检索数据所需的磁盘 I/O 操作。</span><span class="sxs-lookup"><span data-stu-id="1393e-130">Read performance is decreased because the index contains more pages, therefore increasing the disk IO operations required to retrieve the data.</span></span>  
  
#### <a name="adding-data-to-the-end-of-the-table"></a><span data-ttu-id="1393e-131">将数据添加到表的末尾</span><span class="sxs-lookup"><span data-stu-id="1393e-131">Adding Data to the End of the Table</span></span>  
 <span data-ttu-id="1393e-132">如果新数据在表中均匀分布，则不是 0 或 100 的非零填充因子对性能有利。</span><span class="sxs-lookup"><span data-stu-id="1393e-132">A nonzero fill factor other than 0 or 100 can be good for performance if the new data is evenly distributed throughout the table.</span></span> <span data-ttu-id="1393e-133">但是，如果所有数据都添加到表的末尾，则不会填充索引页中的可用空间。</span><span class="sxs-lookup"><span data-stu-id="1393e-133">However, if all the data is added to the end of the table, the empty space in the index pages will not be filled.</span></span> <span data-ttu-id="1393e-134">例如，如果索引键列是 IDENTITY 列，则新行的键将总是增加，并且索引行在逻辑意义上将添加到索引的末尾。</span><span class="sxs-lookup"><span data-stu-id="1393e-134">For example, if the index key column is an IDENTITY column, the key for new rows is always increasing and the index rows are logically added to the end of the index.</span></span> <span data-ttu-id="1393e-135">如果将用加长行的大小的数据来更新现有行，则请使用小于 100 的填充因子。</span><span class="sxs-lookup"><span data-stu-id="1393e-135">If existing rows will be updated with data that lengthens the size of the rows, use a fill factor of less than 100.</span></span> <span data-ttu-id="1393e-136">每页上的额外字节将有助于把行中的额外长度造成的页拆分降低到最小限度。</span><span class="sxs-lookup"><span data-stu-id="1393e-136">The extra bytes on each page will help to minimize page splits caused by extra length in the rows.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="1393e-137">Security</span><span class="sxs-lookup"><span data-stu-id="1393e-137">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="1393e-138">权限</span><span class="sxs-lookup"><span data-stu-id="1393e-138">Permissions</span></span>  
 <span data-ttu-id="1393e-139">要求对表或视图具有 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="1393e-139">Requires ALTER permission on the table or view.</span></span> <span data-ttu-id="1393e-140">用户必须是 **sysadmin** 固定服务器角色的成员，或者是 **db_ddladmin** 和 **db_owner** 固定数据库角色的成员。</span><span class="sxs-lookup"><span data-stu-id="1393e-140">User must be a member of the **sysadmin** fixed server role or the **db_ddladmin** and **db_owner** fixed database roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="1393e-141">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1393e-141">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-specify-a-fill-factor-by-using-table-designer"></a><span data-ttu-id="1393e-142">使用表设计器指定填充因子</span><span class="sxs-lookup"><span data-stu-id="1393e-142">To specify a fill factor by using Table Designer</span></span>  
  
1.  <span data-ttu-id="1393e-143">在对象资源管理器中，单击加号以便展开包含你要指定索引填充因子的表的数据库。</span><span class="sxs-lookup"><span data-stu-id="1393e-143">In Object Explorer, click the plus sign to expand the database that contains the table on which you want to specify an index's fill factor.</span></span>  
  
2.  <span data-ttu-id="1393e-144">单击加号以便展开 **“表”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="1393e-144">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="1393e-145">右键单击你要指定索引的填充因子的表，然后选择“设计”  。</span><span class="sxs-lookup"><span data-stu-id="1393e-145">Right-click the table on which you want to specify an index's fill factor and select **Design**.</span></span>  
  
4.  <span data-ttu-id="1393e-146">在“表设计器”  菜单上，单击“索引/键”  。</span><span class="sxs-lookup"><span data-stu-id="1393e-146">On the **Table Designer** menu, click **Indexes/Keys**.</span></span>  
  
5.  <span data-ttu-id="1393e-147">选择您要指定填充因子的索引。</span><span class="sxs-lookup"><span data-stu-id="1393e-147">Select the index with the fill factor that you want to specify.</span></span>  
  
6.  <span data-ttu-id="1393e-148">展开 **“填充规范”** ，选择 **“填充因子”** 行并在行中输入所需的填充因子。</span><span class="sxs-lookup"><span data-stu-id="1393e-148">Expand **Fill Specification**, select the **Fill Factor** row and enter the fill factor you want in the row.</span></span>  
  
7.  <span data-ttu-id="1393e-149">单击“关闭”  。</span><span class="sxs-lookup"><span data-stu-id="1393e-149">Click **Close**.</span></span>  
  
8.  <span data-ttu-id="1393e-150">在“文件”  菜单上，选择“保存”  以保存 _table_name_。</span><span class="sxs-lookup"><span data-stu-id="1393e-150">On the **File** menu, select **Save**_table_name_.</span></span>  
  
#### <a name="to-specify-a-fill-factor-in-an-index-by-using-object-explorer"></a><span data-ttu-id="1393e-151">使用对象资源管理器为索引指定填充因子</span><span class="sxs-lookup"><span data-stu-id="1393e-151">To specify a fill factor in an index by using Object Explorer</span></span>  
  
1.  <span data-ttu-id="1393e-152">在对象资源管理器中，单击加号以便展开包含你要指定索引填充因子的表的数据库。</span><span class="sxs-lookup"><span data-stu-id="1393e-152">In Object Explorer, click the plus sign to expand the database that contains the table on which you want to specify an index's fill factor.</span></span>  
  
2.  <span data-ttu-id="1393e-153">单击加号以便展开 **“表”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="1393e-153">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="1393e-154">单击加号以展开要指定索引的填充因子的表。</span><span class="sxs-lookup"><span data-stu-id="1393e-154">Click the plus sign to expand the table on which you want to specify an index's fill factor.</span></span>  
  
4.  <span data-ttu-id="1393e-155">单击加号以便展开 **“索引”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="1393e-155">Click the plus sign to expand the **Indexes** folder.</span></span>  
  
5.  <span data-ttu-id="1393e-156">右键单击要指定填充因子的索引，然后选择“属性”  。</span><span class="sxs-lookup"><span data-stu-id="1393e-156">Right-click the index with the fill factor that you want to specify and select **Properties**.</span></span>  
  
6.  <span data-ttu-id="1393e-157">在 **“选择页”** 下，选择 **“选项”** 。</span><span class="sxs-lookup"><span data-stu-id="1393e-157">Under **Select a page**, select **Options**.</span></span>  
  
7.  <span data-ttu-id="1393e-158">在 **“填充因子”** 行中，输入所需的填充因子。</span><span class="sxs-lookup"><span data-stu-id="1393e-158">In the **Fill factor** row, enter the fill factor that you want.</span></span>  
  
8.  <span data-ttu-id="1393e-159">单击“确定”。 </span><span class="sxs-lookup"><span data-stu-id="1393e-159">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="1393e-160">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1393e-160">Using Transact-SQL</span></span>  
  
#### <a name="to-specify-a-fill-factor-in-an-existing-index"></a><span data-ttu-id="1393e-161">在现有索引中指定填充因子</span><span class="sxs-lookup"><span data-stu-id="1393e-161">To specify a fill factor in an existing index</span></span>  
  
1.  <span data-ttu-id="1393e-162">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="1393e-162">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="1393e-163">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="1393e-163">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="1393e-164">将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。</span><span class="sxs-lookup"><span data-stu-id="1393e-164">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="1393e-165">该示例重新生成现有索引，并在重新生成操作过程中应用指定的填充因子。</span><span class="sxs-lookup"><span data-stu-id="1393e-165">The example rebuilds an existing index and applies the specified fill factor during the rebuild operation.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Rebuilds the IX_Employee_OrganizationLevel_OrganizationNode index   
    -- with a fill factor of 80 on the HumanResources.Employee table.  
  
    ALTER INDEX IX_Employee_OrganizationLevel_OrganizationNode ON HumanResources.Employee  
    REBUILD WITH (FILLFACTOR = 80);   
    GO  
    ```  
  
#### <a name="another-way-to-specify-a-fill-factor-in-an-index"></a><span data-ttu-id="1393e-166">为索引指定填充因子的其他方法</span><span class="sxs-lookup"><span data-stu-id="1393e-166">Another way to specify a fill factor in an index</span></span>  
  
1.  <span data-ttu-id="1393e-167">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="1393e-167">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="1393e-168">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="1393e-168">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="1393e-169">将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。</span><span class="sxs-lookup"><span data-stu-id="1393e-169">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    /* Drops and re-creates the IX_Employee_OrganizationLevel_OrganizationNode index on the HumanResources.Employee table with a fill factor of 80.  
    */  
  
    CREATE INDEX IX_Employee_OrganizationLevel_OrganizationNode ON HumanResources.Employee  
       (OrganizationLevel, OrganizationNode)   
    WITH (DROP_EXISTING = ON, FILLFACTOR = 80);   
    GO  
    ```  
  
 <span data-ttu-id="1393e-170">有关详细信息，请参阅 [ALTER INDEX (Transact-SQL)](/sql/t-sql/statements/alter-index-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="1393e-170">For more information, see [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql).</span></span>  
  
  
