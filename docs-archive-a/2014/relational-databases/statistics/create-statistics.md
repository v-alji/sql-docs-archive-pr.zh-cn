---
title: 创建统计信息 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
f1_keywords:
- sql12.swb.statistics.propertis.f1
- sql12.swb.statistics.filter.f1
- sql12.swb.stat.properties.f1
- sql12.swb.stat.columns.f1
helpviewer_keywords:
- creating statistics
- statistics [SQL Server], creating
ms.assetid: 95a455fb-664d-4c95-851e-c6b62d7ebe04
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 230bd4d840c3d59dc1267dd6801754b68386cb32
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590117"
---
# <a name="create-statistics"></a><span data-ttu-id="01986-102">创建统计信息</span><span class="sxs-lookup"><span data-stu-id="01986-102">Create Statistics</span></span>
  <span data-ttu-id="01986-103">您可以通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中为表或索引视图的一个或多个列创建查询优化统计信息。</span><span class="sxs-lookup"><span data-stu-id="01986-103">You can create query optimization statistics on one or more columns of a table or indexed view in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="01986-104">对于大多数查询，查询优化器已为高质量查询计划生成必要的统计信息；但在少数一些情况下，您需要创建附加的统计信息。</span><span class="sxs-lookup"><span data-stu-id="01986-104">For most queries, the query optimizer already generates the necessary statistics for a high-quality query plan; in a few cases, you need to create additional statistics.</span></span>  
  
 <span data-ttu-id="01986-105">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="01986-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="01986-106">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="01986-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="01986-107">限制和局限</span><span class="sxs-lookup"><span data-stu-id="01986-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="01986-108">安全性</span><span class="sxs-lookup"><span data-stu-id="01986-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="01986-109">**若要创建统计信息，请使用：**</span><span class="sxs-lookup"><span data-stu-id="01986-109">**To create statistics, using:**</span></span>  
  
     [<span data-ttu-id="01986-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="01986-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="01986-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="01986-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="01986-112">开始之前</span><span class="sxs-lookup"><span data-stu-id="01986-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="01986-113">限制和局限</span><span class="sxs-lookup"><span data-stu-id="01986-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="01986-114">在使用 CREATE STATISTICS 语句创建统计信息前，请确认在数据库级别设置了 AUTO_CREATE_STATISTICS 选项。</span><span class="sxs-lookup"><span data-stu-id="01986-114">Before creating statistics with the CREATE STATISTICS statement, verify that the AUTO_CREATE_STATISTICS option is set at the database level.</span></span> <span data-ttu-id="01986-115">这将确保查询优化器继续定期为查询谓词列创建单列统计信息。</span><span class="sxs-lookup"><span data-stu-id="01986-115">This will ensure that the query optimizer continues to routinely create single-column statistics for query predicate columns.</span></span>  
  
-   <span data-ttu-id="01986-116">每个统计信息对象至多可列出 32 列。</span><span class="sxs-lookup"><span data-stu-id="01986-116">You can list up to 32 columns per statistics object.</span></span>  
  
-   <span data-ttu-id="01986-117">不能删除、重命名或更改在筛选的统计信息谓词中定义的表列的定义。</span><span class="sxs-lookup"><span data-stu-id="01986-117">You cannot drop, rename, or alter the definition of a table column that is defined in a filtered statistics predicate.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="01986-118">Security</span><span class="sxs-lookup"><span data-stu-id="01986-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="01986-119">权限</span><span class="sxs-lookup"><span data-stu-id="01986-119">Permissions</span></span>  
 <span data-ttu-id="01986-120">要求用户是表或索引视图所有者，或者是以下角色之一的成员： **sysadmin** 固定服务器角色、 **db_owner** 固定数据库角色或 **db_ddladmin** 固定数据库角色。</span><span class="sxs-lookup"><span data-stu-id="01986-120">Requires that the user be the table or indexed view owner, or a member of one of the following roles: **sysadmin** fixed server role, **db_owner** fixed database role, or the **db_ddladmin** fixed database role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="01986-121">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="01986-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-statistics"></a><span data-ttu-id="01986-122">创建统计信息</span><span class="sxs-lookup"><span data-stu-id="01986-122">To create statistics</span></span>  
  
1.  <span data-ttu-id="01986-123">在 **“对象资源管理器”** 中，单击加号以便展开要创建新的统计信息的数据库。</span><span class="sxs-lookup"><span data-stu-id="01986-123">In **Object Explorer**, click the plus sign to expand the database in which you want to create a new statistic.</span></span>  
  
2.  <span data-ttu-id="01986-124">单击加号以便展开 **“表”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="01986-124">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="01986-125">单击加号以便展开您要创建新统计信息的表。</span><span class="sxs-lookup"><span data-stu-id="01986-125">Click the plus sign to expand the table in which you want to create a new statistic.</span></span>  
  
4.  <span data-ttu-id="01986-126">右键单击“统计信息”文件夹，然后选择“新建统计信息…” 。</span><span class="sxs-lookup"><span data-stu-id="01986-126">Right-click the **Statistics** folder and select **New Statistics...**.</span></span>  
  
     <span data-ttu-id="01986-127">以下属性将显示在 "**新建表的统计信息**_table_name_ " 对话框的 "**常规**" 页上。</span><span class="sxs-lookup"><span data-stu-id="01986-127">The following properties show on the **General** page in the **New Statistics on Table**_table_name_ dialog box.</span></span>  
  
     <span data-ttu-id="01986-128">**表名**</span><span class="sxs-lookup"><span data-stu-id="01986-128">**Table Name**</span></span>  
     <span data-ttu-id="01986-129">显示统计信息中所涉及表的名称。</span><span class="sxs-lookup"><span data-stu-id="01986-129">Displays the name of the table described by the statistics.</span></span>  
  
     <span data-ttu-id="01986-130">**统计信息名称**</span><span class="sxs-lookup"><span data-stu-id="01986-130">**Statistics Name**</span></span>  
     <span data-ttu-id="01986-131">显示存储统计信息的数据库对象的名称。</span><span class="sxs-lookup"><span data-stu-id="01986-131">Displays the name of the database object where the statistics are stored.</span></span>  
  
     <span data-ttu-id="01986-132">**统计信息列**</span><span class="sxs-lookup"><span data-stu-id="01986-132">**Statistics Columns**</span></span>  
     <span data-ttu-id="01986-133">此网格显示该组统计信息中所涉及的列。</span><span class="sxs-lookup"><span data-stu-id="01986-133">This grid shows the columns described by this set of statistics.</span></span> <span data-ttu-id="01986-134">网格中的所有值都是只读的。</span><span class="sxs-lookup"><span data-stu-id="01986-134">All values in the grid are read-only.</span></span>  
  
     <span data-ttu-id="01986-135">**名称**</span><span class="sxs-lookup"><span data-stu-id="01986-135">**Name**</span></span>  
     <span data-ttu-id="01986-136">显示统计信息中所涉及列的名称。</span><span class="sxs-lookup"><span data-stu-id="01986-136">Displays the name of the column described by the statistics.</span></span> <span data-ttu-id="01986-137">它可以是单个的列或单个表中的列组合。</span><span class="sxs-lookup"><span data-stu-id="01986-137">This can be a single column or a combination of columns in a single table.</span></span>  
  
     <span data-ttu-id="01986-138">**数据类型**</span><span class="sxs-lookup"><span data-stu-id="01986-138">**Data Type**</span></span>  
     <span data-ttu-id="01986-139">指示统计信息中所涉及列的数据类型。</span><span class="sxs-lookup"><span data-stu-id="01986-139">Indicates the data type of the columns described by the statistics.</span></span>  
  
     <span data-ttu-id="01986-140">**大小**</span><span class="sxs-lookup"><span data-stu-id="01986-140">**Size**</span></span>  
     <span data-ttu-id="01986-141">显示每列的数据类型大小。</span><span class="sxs-lookup"><span data-stu-id="01986-141">Displays the size of the data type for each column.</span></span>  
  
     <span data-ttu-id="01986-142">**标识**</span><span class="sxs-lookup"><span data-stu-id="01986-142">**Identity**</span></span>  
     <span data-ttu-id="01986-143">如果选中此项，则指示标识列。</span><span class="sxs-lookup"><span data-stu-id="01986-143">Indicates an identity column when it is checked.</span></span>  
  
     <span data-ttu-id="01986-144">**允许 Null 值**</span><span class="sxs-lookup"><span data-stu-id="01986-144">**Allow Nulls**</span></span>  
     <span data-ttu-id="01986-145">指示列是否接受空值。</span><span class="sxs-lookup"><span data-stu-id="01986-145">Indicates whether the column accepts NULL values.</span></span>  
  
     <span data-ttu-id="01986-146">**添加**</span><span class="sxs-lookup"><span data-stu-id="01986-146">**Add**</span></span>  
     <span data-ttu-id="01986-147">将表中的其他列添加到统计信息网格。</span><span class="sxs-lookup"><span data-stu-id="01986-147">Add additional columns from the table to the statistics grid.</span></span>  
  
     <span data-ttu-id="01986-148">**删除**</span><span class="sxs-lookup"><span data-stu-id="01986-148">**Remove**</span></span>  
     <span data-ttu-id="01986-149">从统计信息网格中删除所选列。</span><span class="sxs-lookup"><span data-stu-id="01986-149">Remove the selected column from the statistics grid.</span></span>  
  
     <span data-ttu-id="01986-150">**上移**</span><span class="sxs-lookup"><span data-stu-id="01986-150">**Move Up**</span></span>  
     <span data-ttu-id="01986-151">将所选列移动到统计信息网格中更靠前的位置。</span><span class="sxs-lookup"><span data-stu-id="01986-151">Move the selected column to an earlier location in the statistics grid.</span></span> <span data-ttu-id="01986-152">网格中的位置会显著地影响统计信息的有效性。</span><span class="sxs-lookup"><span data-stu-id="01986-152">The location in the grid can substantially impact the usefulness of the statistics.</span></span>  
  
     <span data-ttu-id="01986-153">**“下移”**</span><span class="sxs-lookup"><span data-stu-id="01986-153">**Move Down**</span></span>  
     <span data-ttu-id="01986-154">将所选列移到统计信息网格中更后面的位置。</span><span class="sxs-lookup"><span data-stu-id="01986-154">Move the selected column to a later location in the statistics grid.</span></span>  
  
     <span data-ttu-id="01986-155">**上次更新了这些列的统计信息:**</span><span class="sxs-lookup"><span data-stu-id="01986-155">**Statistics for these columns were last updated:**</span></span>  
     <span data-ttu-id="01986-156">指示统计信息的存在时间。</span><span class="sxs-lookup"><span data-stu-id="01986-156">Indicates how old the statistics are.</span></span> <span data-ttu-id="01986-157">如果统计信息是最新的，则会更有价值。</span><span class="sxs-lookup"><span data-stu-id="01986-157">Statistics are more valuable when they are current.</span></span> <span data-ttu-id="01986-158">在对数据进行较大的更改或者添加异常数据之后，请更新统计信息。</span><span class="sxs-lookup"><span data-stu-id="01986-158">Update statistics after large changes to the data or after adding atypical data.</span></span> <span data-ttu-id="01986-159">对于数据分布一致的表，其统计信息更新频率应较低。</span><span class="sxs-lookup"><span data-stu-id="01986-159">Statistics for tables that have a consistent distribution of data need to be updated less frequently.</span></span>  
  
     <span data-ttu-id="01986-160">**更新这些列的统计信息**</span><span class="sxs-lookup"><span data-stu-id="01986-160">**Update statistics for these columns**</span></span>  
     <span data-ttu-id="01986-161">选中此项后将在对话框关闭时更新统计信息。</span><span class="sxs-lookup"><span data-stu-id="01986-161">Check to update the statistics when the dialog box is closed.</span></span>  
  
     <span data-ttu-id="01986-162">以下属性将显示在 "表_table_name_的**新统计信息**" 对话框中的 "**筛选器**" 页上。</span><span class="sxs-lookup"><span data-stu-id="01986-162">The following property shows on the **Filter** page in the **New Statistics on Table**_table_name_ dialog box.</span></span>  
  
     <span data-ttu-id="01986-163">**筛选表达式**</span><span class="sxs-lookup"><span data-stu-id="01986-163">**Filter Expression**</span></span>  
     <span data-ttu-id="01986-164">定义要将哪些数据行包含在筛选的统计信息中。</span><span class="sxs-lookup"><span data-stu-id="01986-164">Defines which data rows to include in the filtered statistics.</span></span> <span data-ttu-id="01986-165">例如： `Production.ProductSubcategoryID IN ( 1,2,3 )`</span><span class="sxs-lookup"><span data-stu-id="01986-165">For example, `Production.ProductSubcategoryID IN ( 1,2,3 )`</span></span>  
  
5.  <span data-ttu-id="01986-166">在 "**新建表的统计信息**_table_name_ " 对话框的 "**常规**" 页上，单击 "**添加**"。</span><span class="sxs-lookup"><span data-stu-id="01986-166">In the **New Statistics on Table**_table_name_ dialog box, on the **General** page, click **Add**.</span></span>  
  
     <span data-ttu-id="01986-167">**“选择列”** 对话框中显示以下属性：</span><span class="sxs-lookup"><span data-stu-id="01986-167">The following properties show in the **Select Columns** dialog box.</span></span> <span data-ttu-id="01986-168">此信息为只读信息。</span><span class="sxs-lookup"><span data-stu-id="01986-168">This information is read-only.</span></span>  
  
     <span data-ttu-id="01986-169">**名称**</span><span class="sxs-lookup"><span data-stu-id="01986-169">**Name**</span></span>  
     <span data-ttu-id="01986-170">显示统计信息中所涉及列的名称。</span><span class="sxs-lookup"><span data-stu-id="01986-170">Displays the name of the column described by the statistics.</span></span> <span data-ttu-id="01986-171">它可以是单个的列或单个表中的列组合。</span><span class="sxs-lookup"><span data-stu-id="01986-171">This can be a single column or a combination of columns in a single table.</span></span>  
  
     <span data-ttu-id="01986-172">**数据类型**</span><span class="sxs-lookup"><span data-stu-id="01986-172">**Data Type**</span></span>  
     <span data-ttu-id="01986-173">指示统计信息中所涉及列的数据类型。</span><span class="sxs-lookup"><span data-stu-id="01986-173">Indicates the data type of the columns described by the statistics.</span></span>  
  
     <span data-ttu-id="01986-174">**大小**</span><span class="sxs-lookup"><span data-stu-id="01986-174">**Size**</span></span>  
     <span data-ttu-id="01986-175">显示每列的数据类型大小。</span><span class="sxs-lookup"><span data-stu-id="01986-175">Displays the size of the data type for each column.</span></span>  
  
     <span data-ttu-id="01986-176">**标识**</span><span class="sxs-lookup"><span data-stu-id="01986-176">**Identity**</span></span>  
     <span data-ttu-id="01986-177">如果选中，则指示标识列。</span><span class="sxs-lookup"><span data-stu-id="01986-177">Indicates an identity column when checked.</span></span>  
  
     <span data-ttu-id="01986-178">**允许 Null**</span><span class="sxs-lookup"><span data-stu-id="01986-178">**Allow NULLs**</span></span>  
     <span data-ttu-id="01986-179">指示列是否接受空值。</span><span class="sxs-lookup"><span data-stu-id="01986-179">Indicates whether the column accepts NULL values.</span></span>  
  
6.  <span data-ttu-id="01986-180">在 **“选择列”** 对话框中，选中要为其创建统计信息的每个列旁边的复选框，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="01986-180">In the **Select Columns** dialog box, select the check box or check boxes of each column for which you want to create a statistic and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="01986-181">在 "**新建表的统计信息**_table_name_ " 对话框中，单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="01986-181">In the **New Statistics on Table**_table_name_ dialog box, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="01986-182">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="01986-182">Using Transact-SQL</span></span>  
  
#### <a name="to-create-statistics"></a><span data-ttu-id="01986-183">创建统计信息</span><span class="sxs-lookup"><span data-stu-id="01986-183">To create statistics</span></span>  
  
1.  <span data-ttu-id="01986-184">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="01986-184">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="01986-185">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="01986-185">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="01986-186">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="01986-186">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    -- Create new statistic object called ContactMail1  
    -- on the BusinessEntityID and EmailPromotion columns in the Person.Person table.   
  
    CREATE STATISTICS ContactMail1  
        ON Person.Person (BusinessEntityID, EmailPromotion);   
    GO  
    ```  
  
4.  <span data-ttu-id="01986-187">上面创建的统计信息可能会改进以下查询的结果。</span><span class="sxs-lookup"><span data-stu-id="01986-187">The statistic created above potentially improves the results for the following query.</span></span>  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    SELECT LastName, FirstName  
    FROM Person.Person  
    WHERE EmailPromotion = 2  
    ORDER BY LastName, FirstName;   
    GO  
    ```  
  
 <span data-ttu-id="01986-188">有关详细信息，请参阅 [CREATE STATISTICS (Transact-SQL)](/sql/t-sql/statements/create-statistics-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="01986-188">For more information, see [CREATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-statistics-transact-sql).</span></span>  
  
  
