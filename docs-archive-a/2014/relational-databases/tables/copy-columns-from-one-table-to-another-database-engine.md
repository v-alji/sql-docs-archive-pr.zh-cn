---
title: 将列从一个表复制到另一个表 (数据库引擎) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- copying columns
- columns [SQL Server], copying
ms.assetid: 5f5e70dc-69f9-44b8-bc48-b5d51ac20d77
author: stevestein
ms.author: sstein
ms.openlocfilehash: 37b98bf0910cbbb4c2a1d7fe01f11d52703ec88c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591844"
---
# <a name="copy-columns-from-one-table-to-another-database-engine"></a><span data-ttu-id="31369-102">将列从一个表复制到另一个表 (数据库引擎)</span><span class="sxs-lookup"><span data-stu-id="31369-102">Copy Columns from One Table to Another (Database Engine)</span></span>
  <span data-ttu-id="31369-103">本主题介绍如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中通过仅复制列定义或者复制定义和数据将列从一个表复制到另一个表。</span><span class="sxs-lookup"><span data-stu-id="31369-103">This topic describes how to copy columns from one table to another, copying either just the column definition, or the definition and data in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="31369-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="31369-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="31369-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="31369-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="31369-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="31369-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="31369-107">安全性</span><span class="sxs-lookup"><span data-stu-id="31369-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="31369-108">**若要复制列，请使用：**</span><span class="sxs-lookup"><span data-stu-id="31369-108">**To coy columns, using:**</span></span>  
  
     [<span data-ttu-id="31369-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="31369-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="31369-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="31369-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="31369-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="31369-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="31369-112">限制和局限</span><span class="sxs-lookup"><span data-stu-id="31369-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="31369-113">当将具有别名数据类型的列从一个数据库复制到另一个数据库时，别名数据类型在目标数据库中可能不可用。</span><span class="sxs-lookup"><span data-stu-id="31369-113">When you copy a column that has an alias data type from one database to another, the alias data type may not be available in the destination database.</span></span> <span data-ttu-id="31369-114">在这种情况下，将为该列分配该数据库中可用的匹配度最高的基数据类型。</span><span class="sxs-lookup"><span data-stu-id="31369-114">In such a case, the column will be assigned the nearest matching base data type available in that database.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="31369-115">Security</span><span class="sxs-lookup"><span data-stu-id="31369-115">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="31369-116">权限</span><span class="sxs-lookup"><span data-stu-id="31369-116">Permissions</span></span>  
 <span data-ttu-id="31369-117">需要对表的 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="31369-117">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="31369-118">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="31369-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-copy-column-definitions-from-one-table-to-another"></a><span data-ttu-id="31369-119">将列定义从一个表复制到另一个表</span><span class="sxs-lookup"><span data-stu-id="31369-119">To copy column definitions from one table to another</span></span>  
  
1.  <span data-ttu-id="31369-120">右键单击相应表，然后单击“设计”  ，打开要复制的列所在的表以及要复制到的表。</span><span class="sxs-lookup"><span data-stu-id="31369-120">Open the table with columns you want to copy and the one you want to copy into by right-clicking the tables, and then clicking **Design**.</span></span>  
  
2.  <span data-ttu-id="31369-121">单击包含要复制的列的表的选项卡，然后选择这些列。</span><span class="sxs-lookup"><span data-stu-id="31369-121">Click the tab for the table with the columns you want to copy and select those columns.</span></span>  
  
3.  <span data-ttu-id="31369-122">在 **“编辑”** 菜单中，单击 **“复制”** 。</span><span class="sxs-lookup"><span data-stu-id="31369-122">From the **Edit** menu, click **Copy**.</span></span>  
  
4.  <span data-ttu-id="31369-123">单击要将列复制到的表的选项卡。</span><span class="sxs-lookup"><span data-stu-id="31369-123">Click the tab for the table into which you want to copy the columns.</span></span>  
  
5.  <span data-ttu-id="31369-124">选择要排在插入列之后的列，然后在 **“编辑”** 菜单中，单击 **“粘贴”** 。</span><span class="sxs-lookup"><span data-stu-id="31369-124">Select the column you want to follow the inserted columns and, from the **Edit** menu, click **Paste**.</span></span>  
  
#### <a name="to-copy-data-from-one-table-to-another"></a><span data-ttu-id="31369-125">将数据从一个表复制到另一个表</span><span class="sxs-lookup"><span data-stu-id="31369-125">To copy data from one table to another</span></span>  
  
1.  <span data-ttu-id="31369-126">按照以上关于复制列定义的说明执行操作。</span><span class="sxs-lookup"><span data-stu-id="31369-126">Follow the directions for copying column definitions above.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="31369-127">在开始将数据从一个表复制到另一个表之前，请确保目标列中的数据类型与源列的数据类型相兼容。</span><span class="sxs-lookup"><span data-stu-id="31369-127">Before you begin to copy data from one table to another, make sure that the data types in the destination columns are compatible with the data types of the source columns</span></span>  
  
2.  <span data-ttu-id="31369-128">在对象资源管理器中，右键单击“视图”\*\*\*\* 节点，然后单击“新建视图”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="31369-128">In Object Explorer, right-click the **Views** node, and then click **New View**.</span></span>  
  
3.  <span data-ttu-id="31369-129">在 **“查询设计器”** 菜单中，指向 **“更改类型”**，再单击 **“插入结果”**。</span><span class="sxs-lookup"><span data-stu-id="31369-129">From the **Query Designer** menu, point to **Change Type**, and then click **Insert Results**.</span></span>  
  
4.  <span data-ttu-id="31369-130">在 **“选择插入结果的目标表”** 对话框中选择要将数据复制到的表，再单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="31369-130">In the **Choose Target Table for Insert Results** dialog box, select the table into which you want to copy the data, and then click **OK**.</span></span>  
  
     <span data-ttu-id="31369-131">若要在同一个表内复制行，则可将源表作为目标表添加。</span><span class="sxs-lookup"><span data-stu-id="31369-131">If you are copying rows within a table, you can add the source table as a destination table.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="31369-132">**查询设计器** 无法事先确定可以更新哪些表和视图。</span><span class="sxs-lookup"><span data-stu-id="31369-132">**Query Designer** cannot determine in advance which tables and views you can update.</span></span> <span data-ttu-id="31369-133">因此， **“选择插入结果的目标表”** 对话框中的表列表将显示正在查询的数据连接中的所有可用表和视图，甚至显示不能将行复制到其中的表和视图。</span><span class="sxs-lookup"><span data-stu-id="31369-133">Therefore, the list of tables in the **Choose Target Table for Insert Results** dialog box shows all available tables and views in the data connection you are querying, even those that you might not be able to copy rows to.</span></span>  
  
5.  <span data-ttu-id="31369-134">右键单击“关系图”窗格的主题，然后在快捷菜单中单击“将表添加到关系图”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="31369-134">Right-click in the body of the diagram pane and, from the shortcut menu, click **Add Table to Diagram**.</span></span>  
  
6.  <span data-ttu-id="31369-135">在 **“添加表”** 对话框中选择要从中复制数据的各个表，单击 **“添加”**，再单击 **“关闭”**。</span><span class="sxs-lookup"><span data-stu-id="31369-135">In the **Add Table** dialog box, select each table from which you want to copy data, click **Add**, and then click **Close**.</span></span>  
  
     <span data-ttu-id="31369-136">这些表将以缩略形式显示在“关系图”窗格中。</span><span class="sxs-lookup"><span data-stu-id="31369-136">The tables, in an abbreviated form, appear in the diagram pane.</span></span>  
  
7.  <span data-ttu-id="31369-137">在缩略表中，选中要从中复制数据的所有列的复选框。</span><span class="sxs-lookup"><span data-stu-id="31369-137">In the abbreviated tables, check the boxes for any columns from which you want to copy data.</span></span>  
  
8.  <span data-ttu-id="31369-138">在“条件”窗格的 **“追加”** 列中，为每个目标列选择要从其中复制数据的列。</span><span class="sxs-lookup"><span data-stu-id="31369-138">In the criteria pane, in the **Append** column, for each target column choose a column from which you want to copy data.</span></span>  
  
9. <span data-ttu-id="31369-139">通过在“条件”窗格中输入搜索条件来指定要复制的行。</span><span class="sxs-lookup"><span data-stu-id="31369-139">Specify the rows to copy by entering search conditions in the criteria pane.</span></span> <span data-ttu-id="31369-140">有关详细信息，请参阅[指定搜索条件 (Visual Database Tools)](../../ssms/visual-db-tools/visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="31369-140">For details, see [Specify Search Conditions &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/visual-database-tools.md).</span></span>  
  
     <span data-ttu-id="31369-141">如果未指定搜索条件，则源表中的所有行都会复制到目标表中。</span><span class="sxs-lookup"><span data-stu-id="31369-141">If you do not specify a search condition, all rows from the source table will be copied to the destination table.</span></span>  
  
10. <span data-ttu-id="31369-142">如果要复制摘要信息，请指定 "**分组依据**" 选项。</span><span class="sxs-lookup"><span data-stu-id="31369-142">If you want to copy summary information, specify **Group By** options.</span></span> <span data-ttu-id="31369-143">有关详细信息，请参阅[汇总或聚合表中所有行的值 (Visual Database Tools)](../../ssms/visual-db-tools/summarize-or-aggregate-values-for-all-rows-in-a-table-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="31369-143">For details, see [Summarize or Aggregate Values for All Rows in a Table &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/summarize-or-aggregate-values-for-all-rows-in-a-table-visual-database-tools.md).</span></span>  
  
11. <span data-ttu-id="31369-144">单击 **“执行 SQL”** 按钮以运行该查询。</span><span class="sxs-lookup"><span data-stu-id="31369-144">Click the **Execute SQL button** to run the query.</span></span>  
  
     <span data-ttu-id="31369-145">执行 "插入结果" 查询时，不会在 "结果"[窗格](../../ssms/visual-db-tools/results-pane-visual-database-tools.md)中报告任何结果。</span><span class="sxs-lookup"><span data-stu-id="31369-145">When you execute an insert results query, no results are reported in the [Results Pane](../../ssms/visual-db-tools/results-pane-visual-database-tools.md).</span></span> <span data-ttu-id="31369-146">但是，会显示一条消息，指出已复制的行数。</span><span class="sxs-lookup"><span data-stu-id="31369-146">Instead, a message appears indicating how many rows were copied.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="31369-147">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="31369-147">Using Transact-SQL</span></span>  
  
#### <a name="to-copy-column-definitions-from-one-table-to-another"></a><span data-ttu-id="31369-148">将列定义从一个表复制到另一个表</span><span class="sxs-lookup"><span data-stu-id="31369-148">To copy column definitions from one table to another</span></span>  
  
1.  <span data-ttu-id="31369-149">不能通过使用 Transact-SQL 语句将单独列从一个表复制到另一个现有表。</span><span class="sxs-lookup"><span data-stu-id="31369-149">You cannot copy individual columns from one table to another existing table by using Transact-SQL statements.</span></span> <span data-ttu-id="31369-150">但是，您可以通过使用 SELECT INTO 在默认文件组中创建一个新表，并将来自查询的结果行插入该表中。</span><span class="sxs-lookup"><span data-stu-id="31369-150">However, you can create a new table in the default filegroup and inserts the resulting rows from the query into it by using SELECT INTO.</span></span> <span data-ttu-id="31369-151">有关详细信息，请参阅 [ INTO 子句 (Transact-SQL)](/sql/t-sql/queries/select-into-clause-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="31369-151">For more information, see [INTO Clause &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-into-clause-transact-sql).</span></span>  
  
#### <a name="to-copy-data-from-one-table-to-another"></a><span data-ttu-id="31369-152">将数据从一个表复制到另一个表</span><span class="sxs-lookup"><span data-stu-id="31369-152">To copy data from one table to another</span></span>  
  
1.  <span data-ttu-id="31369-153">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="31369-153">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="31369-154">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="31369-154">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="31369-155">将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。</span><span class="sxs-lookup"><span data-stu-id="31369-155">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    CREATE TABLE dbo.EmployeeSales  
    ( BusinessEntityID   varchar(11) NOT NULL,  
      SalesYTD money NOT NULL  
    );  
    GO  
    INSERT INTO dbo.EmployeeSales  
        SELECT BusinessEntityID, SalesYTD   
        FROM Sales.SalesPerson;  
    GO  
    ```  
  
  
