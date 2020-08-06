---
title: 第11课：创建分区 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 92eb21a8-5fc4-4999-ad37-1332ce26431d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4db5edd5d47fe424ef6e6ad2a822106110209059
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577042"
---
# <a name="lesson-11-create-partitions"></a><span data-ttu-id="87d3f-102">第 11 课：创建分区</span><span class="sxs-lookup"><span data-stu-id="87d3f-102">Lesson 11: Create Partitions</span></span>
  <span data-ttu-id="87d3f-103">在本课中，您将创建分区，以便将 Internet Sales 表划分为可独立于其他分区进行处理（刷新）的更小逻辑部分。</span><span class="sxs-lookup"><span data-stu-id="87d3f-103">In this lesson, you will create partitions to divide the Internet Sales table into smaller logical parts that can be processed (Refreshed) independent of other partitions.</span></span> <span data-ttu-id="87d3f-104">默认情况下，模型中包含的每个表都有一个分区，其中包含表的所有列和行。</span><span class="sxs-lookup"><span data-stu-id="87d3f-104">By default, every table you include in your model has one partition which includes all of the table's columns and rows.</span></span> <span data-ttu-id="87d3f-105">对于 Internet Sales 表，我们希望按年份划分数据;每个表的5年的一个分区。</span><span class="sxs-lookup"><span data-stu-id="87d3f-105">For the Internet Sales table, we want to divide the data by year; one partition for each of the table's five years.</span></span>  <span data-ttu-id="87d3f-106">然后，每个分区可独立进行处理。</span><span class="sxs-lookup"><span data-stu-id="87d3f-106">Each partition can then be processed independently.</span></span> <span data-ttu-id="87d3f-107">若要了解详细信息，请参阅[分区（SSAS 表格）](tabular-models/partitions-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="87d3f-107">To learn more, see [Partitions &#40;SSAS Tabular&#41;](tabular-models/partitions-ssas-tabular.md).</span></span>  
  
 <span data-ttu-id="87d3f-108">学完本课的估计时间： **15 分钟**</span><span class="sxs-lookup"><span data-stu-id="87d3f-108">Estimated time to complete this lesson: **15 minutes**</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="87d3f-109">先决条件</span><span class="sxs-lookup"><span data-stu-id="87d3f-109">Prerequisites</span></span>  
 <span data-ttu-id="87d3f-110">本主题是表格建模教程的一部分，应当按顺序完成。</span><span class="sxs-lookup"><span data-stu-id="87d3f-110">This topic is part of a tabular modeling tutorial, which should be completed in order.</span></span> <span data-ttu-id="87d3f-111">在执行本课程中的任务之前，应该已完成上一课： [第 10 课：创建层次结构](lesson-9-create-hierarchies.md)。</span><span class="sxs-lookup"><span data-stu-id="87d3f-111">Before performing the tasks in this lesson, you should have completed the previous lesson: [Lesson 10: Create Hierarchies](lesson-9-create-hierarchies.md).</span></span>  
  
## <a name="create-partitions"></a><span data-ttu-id="87d3f-112">创建分区</span><span class="sxs-lookup"><span data-stu-id="87d3f-112">Create Partitions</span></span>  
  
#### <a name="to-create-partitions-in-the-internet-sales-table"></a><span data-ttu-id="87d3f-113">在 Internet Sales 表中创建分区</span><span class="sxs-lookup"><span data-stu-id="87d3f-113">To create partitions in the Internet Sales table</span></span>  
  
1.  <span data-ttu-id="87d3f-114">在模型设计器中，依次单击“Internet Sales”\*\*\*\* 表、“表”\*\*\*\* 菜单和“分区”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="87d3f-114">In the model designer, click on the **Internet Sales** table, then click on the **Table** menu, and then click **Partitions**.</span></span>  
  
     <span data-ttu-id="87d3f-115">“分区管理器”\*\*\*\* 对话框将打开。</span><span class="sxs-lookup"><span data-stu-id="87d3f-115">The **Partition Manager** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="87d3f-116">在 "**分区管理器**" 对话框的 "**分区**" 中，单击 " **Internet 销售**" 分区。</span><span class="sxs-lookup"><span data-stu-id="87d3f-116">In the **Partition Manager** dialog box, in **Partitions**, click the **Internet Sales** partition.</span></span>  
  
3.  <span data-ttu-id="87d3f-117">在 "**分区名称**" 中，将名称更改为 `Internet Sales 2005` 。</span><span class="sxs-lookup"><span data-stu-id="87d3f-117">In **Partition Name**, change the name to `Internet Sales 2005`.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="87d3f-118">在继续执行下一步之前，您将注意到“表预览”窗口中的列名显示模型表中包含的、但其列名来自源中的这些列（已勾选）。</span><span class="sxs-lookup"><span data-stu-id="87d3f-118">Before continuing to the next step, notice the column names in the Table Preview window display those columns included in the model table (checked) with the column names from the source.</span></span> <span data-ttu-id="87d3f-119">这是因为“表预览”窗口显示源表（而非模型表）中的列。</span><span class="sxs-lookup"><span data-stu-id="87d3f-119">This is because the Table Preview window displays columns from the source table, not from the model table.</span></span>  
  
4.  <span data-ttu-id="87d3f-120">选择位于预览窗口右侧上方的“查询编辑器”\*\*\*\* 按钮。</span><span class="sxs-lookup"><span data-stu-id="87d3f-120">Select the **Query Editor** button just above the right side of the preview window.</span></span>  
  
     <span data-ttu-id="87d3f-121">因为您希望分区只包含特定期间内的那些行，所以您必须包含 WHERE 子句。</span><span class="sxs-lookup"><span data-stu-id="87d3f-121">Because you want the partition to include only those rows within a certain period, you must include a WHERE clause.</span></span> <span data-ttu-id="87d3f-122">您只能通过使用 SQL 语句创建 WHERE 子句。</span><span class="sxs-lookup"><span data-stu-id="87d3f-122">You can only create a WHERE clause by using a SQL Statement.</span></span>  
  
5.  <span data-ttu-id="87d3f-123">在“SQL 语句”\*\*\*\* 字段中，通过粘贴以下语句替换现有语句：</span><span class="sxs-lookup"><span data-stu-id="87d3f-123">In the **SQL Statement** field, replace the existing statement by pasting in the following statement:</span></span>  
  
    ```  
    SELECT   
    [dbo].[FactInternetSales].[ProductKey],  
    [dbo].[FactInternetSales].[CustomerKey],  
    [dbo].[FactInternetSales].[PromotionKey],  
    [dbo].[FactInternetSales].[CurrencyKey],  
    [dbo].[FactInternetSales].[SalesTerritoryKey],  
    [dbo].[FactInternetSales].[SalesOrderNumber],  
    [dbo].[FactInternetSales].[SalesOrderLineNumber],  
    [dbo].[FactInternetSales].[RevisionNumber],  
    [dbo].[FactInternetSales].[OrderQuantity],  
    [dbo].[FactInternetSales].[UnitPrice],  
    [dbo].[FactInternetSales].[ExtendedAmount],  
    [dbo].[FactInternetSales].[UnitPriceDiscountPct],  
    [dbo].[FactInternetSales].[DiscountAmount],  
    [dbo].[FactInternetSales].[ProductStandardCost],  
    [dbo].[FactInternetSales].[TotalProductCost],  
    [dbo].[FactInternetSales].[SalesAmount],  
    [dbo].[FactInternetSales].[TaxAmt],  
    [dbo].[FactInternetSales].[Freight],  
    [dbo].[FactInternetSales].[CarrierTrackingNumber],  
    [dbo].[FactInternetSales].[CustomerPONumber],  
    [dbo].[FactInternetSales].[OrderDate],  
    [dbo].[FactInternetSales].[DueDate],  
    [dbo].[FactInternetSales].[ShipDate]   
    FROM [dbo].[FactInternetSales]  
    WHERE (([OrderDate] >= N'2005-01-01 00:00:00') AND ([OrderDate] < N'2006-01-01 00:00:00'))  
    ```  
  
     <span data-ttu-id="87d3f-124">本语句指定分区应包含以下行中的所有数据：对于这些行，OrderDate 对应于在 WHERE 子句中指定的 2005 日历年。</span><span class="sxs-lookup"><span data-stu-id="87d3f-124">This statement specifies the partition should include all of the data in those rows where the OrderDate is for the 2005 calendar year as specified in the WHERE clause.</span></span>  
  
6.  <span data-ttu-id="87d3f-125">单击 **“验证”** 。</span><span class="sxs-lookup"><span data-stu-id="87d3f-125">Click **Validate**.</span></span>  
  
     <span data-ttu-id="87d3f-126">请注意，此时将显示一条警告，指出某些列在源中不存在。</span><span class="sxs-lookup"><span data-stu-id="87d3f-126">Notice a warning is displayed stating that certain columns are not present in source.</span></span> <span data-ttu-id="87d3f-127">这是因为在[第3课：重命名列](rename-columns.md)时，在模型中将 Internet Sales 表中的这些列重命名为不同于源中相同列。</span><span class="sxs-lookup"><span data-stu-id="87d3f-127">This is because in [Lesson 3: Rename Columns](rename-columns.md), you renamed those columns in the Internet Sales table in the model to be different from those same columns at the source.</span></span>  
  
#### <a name="to-create-a-partition-for-the-2006-year-in-the-internet-sales-table"></a><span data-ttu-id="87d3f-128">在 Internet Sales 表中创建2006年的分区</span><span class="sxs-lookup"><span data-stu-id="87d3f-128">To create a partition for the 2006 year in the Internet Sales table</span></span>  
  
1.  <span data-ttu-id="87d3f-129">在 "**分区管理器**" 对话框的 "**分区**" 中，单击 `Internet Sales 2005` 刚创建的分区，然后**复制**。</span><span class="sxs-lookup"><span data-stu-id="87d3f-129">In the **Partition Manager** dialog box, in **Partitions**, click the `Internet Sales 2005` partition you just created, and then **Copy**.</span></span>  
  
2.  <span data-ttu-id="87d3f-130">在 "**分区名称**" 中，键入 `Internet Sales 2006` 。</span><span class="sxs-lookup"><span data-stu-id="87d3f-130">In **Partition Name**, type `Internet Sales 2006`.</span></span>  
  
3.  <span data-ttu-id="87d3f-131">在 SQL 语句中，要使分区只包含2006年的那些行，请将 WHERE 子句替换为以下内容：</span><span class="sxs-lookup"><span data-stu-id="87d3f-131">In the SQL Statement, in-order for the partition to include only those rows for the 2006 year, replace the WHERE clause with the following:</span></span>  
  
    ```  
    WHERE (([OrderDate] >= N'2006-01-01 00:00:00') AND ([OrderDate] < N'2007-01-01 00:00:00'))  
    ```  
  
#### <a name="to-create-a-partition-for-the-2007-year-in-the-internet-sales-table"></a><span data-ttu-id="87d3f-132">在 Internet Sales 表中创建2007年的分区</span><span class="sxs-lookup"><span data-stu-id="87d3f-132">To create a partition for the 2007 year in the Internet Sales table</span></span>  
  
1.  <span data-ttu-id="87d3f-133">在“分区管理器”\*\*\*\* 对话框中，单击“复制”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="87d3f-133">In the **Partition Manager** dialog box, click **Copy**.</span></span>  
  
2.  <span data-ttu-id="87d3f-134">在 "**分区名称**" 中，键入 `Internet Sales 2007` 。</span><span class="sxs-lookup"><span data-stu-id="87d3f-134">In **Partition Name**, type `Internet Sales 2007`.</span></span>  
  
3.  <span data-ttu-id="87d3f-135">在 "**切换到**" 中，选择 "**查询编辑器**"。</span><span class="sxs-lookup"><span data-stu-id="87d3f-135">In **Switch To**, select **Query Editor**.</span></span>  
  
4.  <span data-ttu-id="87d3f-136">在 SQL 语句中，要使分区只包含2007年的那些行，请将 WHERE 子句替换为以下内容：</span><span class="sxs-lookup"><span data-stu-id="87d3f-136">In the SQL Statement, in-order for the partition to include only those rows for the 2007 year, replace the WHERE clause with the following:</span></span>  
  
    ```  
    WHERE (([OrderDate] >= N'2007-01-01 00:00:00') AND ([OrderDate] < N'2008-01-01 00:00:00'))  
    ```  
  
#### <a name="to-create-a-partition-for-the-2008-year-in-the-internet-sales-table"></a><span data-ttu-id="87d3f-137">在 Internet Sales 表中创建2008年的分区</span><span class="sxs-lookup"><span data-stu-id="87d3f-137">To create a partition for the 2008 year in the Internet Sales table</span></span>  
  
1.  <span data-ttu-id="87d3f-138">在“分区管理器”\*\*\*\* 对话框中，单击“新建”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="87d3f-138">In the **Partition Manager** dialog box, click **New**.</span></span>  
  
2.  <span data-ttu-id="87d3f-139">在 "**分区名称**" 中，键入 `Internet Sales 2008` 。</span><span class="sxs-lookup"><span data-stu-id="87d3f-139">In **Partition Name**, type `Internet Sales 2008`.</span></span>  
  
3.  <span data-ttu-id="87d3f-140">在 "**切换到**" 中，选择 "**查询编辑器**"。</span><span class="sxs-lookup"><span data-stu-id="87d3f-140">In **Switch To**, select **Query Editor**.</span></span>  
  
4.  <span data-ttu-id="87d3f-141">在 SQL 语句中，要使分区只包含2008年的那些行，请将 WHERE 子句替换为以下内容：</span><span class="sxs-lookup"><span data-stu-id="87d3f-141">In the SQL Statement, in-order for the partition to include only those rows for the 2008 year, replace the WHERE clause with the following:</span></span>  
  
    ```  
    WHERE (([OrderDate] >= N'2008-01-01 00:00:00') AND ([OrderDate] < N'2009-01-01 00:00:00'))  
    ```  
  
#### <a name="to-create-a-partition-for-the-2009-year-in-the-internet-sales-table"></a><span data-ttu-id="87d3f-142">在 Internet Sales 表中为 2009 年份创建分区</span><span class="sxs-lookup"><span data-stu-id="87d3f-142">To create a partition for the 2009 year in the Internet Sales table</span></span>  
  
1.  <span data-ttu-id="87d3f-143">在“分区管理器”\*\*\*\* 对话框中，单击“新建”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="87d3f-143">In the **Partition Manager** dialog box, click **New**.</span></span>  
  
2.  <span data-ttu-id="87d3f-144">在 "**分区名称**" 中，键入 `Internet Sales 2009` 。</span><span class="sxs-lookup"><span data-stu-id="87d3f-144">In **Partition Name**, type `Internet Sales 2009`.</span></span>  
  
3.  <span data-ttu-id="87d3f-145">在 "**切换到**" 中，选择 "**查询编辑器**"。</span><span class="sxs-lookup"><span data-stu-id="87d3f-145">In **Switch To**, select **Query Editor**.</span></span>  
  
4.  <span data-ttu-id="87d3f-146">在 SQL 语句中，要使分区只包含 2009 年份的这些行，请将 WHERE 子句替换为：</span><span class="sxs-lookup"><span data-stu-id="87d3f-146">In the SQL Statement, in-order for the partition to include only those rows for the 2009 year, replace the WHERE clause with the following:</span></span>  
  
    ```  
    WHERE (([OrderDate] >= N'2009-01-01 00:00:00') AND ([OrderDate] < N'2010-01-01 00:00:00'))  
    ```  
  
## <a name="process-partitions"></a><span data-ttu-id="87d3f-147">处理分区</span><span class="sxs-lookup"><span data-stu-id="87d3f-147">Process Partitions</span></span>  
 <span data-ttu-id="87d3f-148">在“分区管理器”\*\*\*\* 对话框中，请注意，对于刚才创建的每个新分区，分区名称旁边会有一个星号 (**\***)。</span><span class="sxs-lookup"><span data-stu-id="87d3f-148">In the **Partition Manager** dialog box, notice the asterisk (**\***) next to the partition names for each of the new partitions you just created.</span></span> <span data-ttu-id="87d3f-149">这指示尚未处理（刷新）分区。</span><span class="sxs-lookup"><span data-stu-id="87d3f-149">This indicates that the partition has not been processed (refreshed).</span></span> <span data-ttu-id="87d3f-150">当您创建新分区时，您应运行“处理分区”或“处理表”操作以刷新这些分区中的数据。</span><span class="sxs-lookup"><span data-stu-id="87d3f-150">When you create new partitions, you should run a Process Partitions or Process Table operation to refresh the data in those partitions.</span></span>  
  
#### <a name="to-process-internet-sales-partitions"></a><span data-ttu-id="87d3f-151">处理 Internet Sales 分区</span><span class="sxs-lookup"><span data-stu-id="87d3f-151">To process Internet Sales partitions</span></span>  
  
1.  <span data-ttu-id="87d3f-152">单击“确定”\*\*\*\* 关闭“分区管理器”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="87d3f-152">Click **OK** to close the **Partition Manager** dialog box.</span></span>  
  
2.  <span data-ttu-id="87d3f-153">在模型设计器中，单击“Internet Sales”\*\*\*\* 表，然后单击“模型”\*\*\*\* 菜单，指向“处理”\*\*\*\*（刷新），然后单击“处理分区”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="87d3f-153">In the model designer, click the **Internet Sales** table, then click the **Model** menu, then point to **Process** (Refresh), and then click **Process Partitions**.</span></span>  
  
3.  <span data-ttu-id="87d3f-154">在“处理分区”\*\*\*\* 对话框中，确认“模式”\*\*\*\* 已设置为“处理默认值”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="87d3f-154">In the **Process Partitions** dialog box, verify the **Mode** is set to **Process Default**.</span></span>  
  
4.  <span data-ttu-id="87d3f-155">选中创建的五个分区中每个分区的“处理”列中的复选框，并单击“确定”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="87d3f-155">Select the checkbox in the **Process** column for each of the five partitions you created, and then click **OK**.</span></span>  
  
     <span data-ttu-id="87d3f-156">如果系统提示您输入模拟凭据，则输入您在第 2 课的第 6 步中指定的 Windows 用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="87d3f-156">If you are prompted for Impersonation credentials, enter the Windows user name and password you specified in Lesson 2, step 6.</span></span>  
  
     <span data-ttu-id="87d3f-157">然后，将出现 "**数据处理**" 对话框，并显示每个分区的进程详细信息。</span><span class="sxs-lookup"><span data-stu-id="87d3f-157">The **Data Process** dialog box then appears and displays process details for each partition.</span></span> <span data-ttu-id="87d3f-158">请注意，为每个分区传输的行数不同。</span><span class="sxs-lookup"><span data-stu-id="87d3f-158">Notice that a different number of rows for each partition are transferred.</span></span> <span data-ttu-id="87d3f-159">这是因为，每个分区值包含您在 SQL 语句的 WHERE 子句中指定的年份的那些行。</span><span class="sxs-lookup"><span data-stu-id="87d3f-159">This is because each partition includes only those rows for the year specified in the WHERE clause in the SQL Statement.</span></span> <span data-ttu-id="87d3f-160">对于 2010 年份没有数据。</span><span class="sxs-lookup"><span data-stu-id="87d3f-160">There is no data for the 2010 year.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="87d3f-161">后续步骤</span><span class="sxs-lookup"><span data-stu-id="87d3f-161">Next Steps</span></span>  
 <span data-ttu-id="87d3f-162">若要继续学习本教程，请转到下一课： [第 12 课：创建角色](lesson-11-create-roles.md)。</span><span class="sxs-lookup"><span data-stu-id="87d3f-162">To continue this tutorial, go to the next lesson: Lesson: [Lesson 12: Create Roles](lesson-11-create-roles.md).</span></span>  
  
  
