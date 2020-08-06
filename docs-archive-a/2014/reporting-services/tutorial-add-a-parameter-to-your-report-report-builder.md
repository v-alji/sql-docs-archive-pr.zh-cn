---
title: 教程：向报表添加参数（报表生成器）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: eab34ec4-b3ad-4a76-95cc-07b2f75ee6d7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: dff41066a2d505ab53b17a10fb3da9b6cb17130f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691550"
---
# <a name="tutorial-add-a-parameter-to-your-report-report-builder"></a><span data-ttu-id="1bc5a-102">教程：向报表添加参数（报表生成器）</span><span class="sxs-lookup"><span data-stu-id="1bc5a-102">Tutorial: Add a Parameter to Your Report (Report Builder)</span></span>
  <span data-ttu-id="1bc5a-103">通过向报表添加参数，用户可以筛选来自数据源的报表数据或报表中的报表数据。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-103">Add a parameter to your report to let users filter report data from the data source or in the report.</span></span> <span data-ttu-id="1bc5a-104">报表参数是针对您在数据集查询中包含的每个查询参数自动创建的。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-104">Report parameters are created automatically for each query parameter that you include in a dataset query.</span></span> <span data-ttu-id="1bc5a-105">参数的数据类型确定了参数在报表视图工具栏上显示的方式。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-105">The parameter data type determines how it appears on the report view toolbar.</span></span>  
  
 <span data-ttu-id="1bc5a-106">![rs_tut_Parameter](../../2014/tutorials/media/rs-tut-parameter.gif "rs_tut_Parameter")</span><span class="sxs-lookup"><span data-stu-id="1bc5a-106">![rs_tut_Parameter](../../2014/tutorials/media/rs-tut-parameter.gif "rs_tut_Parameter")</span></span>  
  
##  <a name="what-you-will-learn"></a><a name="BackToTop"></a><span data-ttu-id="1bc5a-107">你将学习的内容</span><span class="sxs-lookup"><span data-stu-id="1bc5a-107">What You Will Learn</span></span>  
 <span data-ttu-id="1bc5a-108">在本教程中，您将学习如何执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="1bc5a-108">In this tutorial you will learn how to do the following:</span></span>  
  
1.  [<span data-ttu-id="1bc5a-109">使用表或矩阵向导创建矩阵报表和数据集</span><span class="sxs-lookup"><span data-stu-id="1bc5a-109">Create a Matrix Report and Dataset from the Table or Matrix Wizard</span></span>](#Setup)  
  
2.  [<span data-ttu-id="1bc5a-110">使用表或矩阵向导组织数据并选择布局和样式</span><span class="sxs-lookup"><span data-stu-id="1bc5a-110">Organize Data, Choose Layout, and Style from the Table or Matrix Wizard</span></span>](#CompleteWizard)  
  
3.  [<span data-ttu-id="1bc5a-111">添加查询参数以创建报表参数</span><span class="sxs-lookup"><span data-stu-id="1bc5a-111">Add a Query Parameter to Create a Report Parameter</span></span>](#Query)  
  
4.  [<span data-ttu-id="1bc5a-112">更改报表参数的默认数据类型和其他属性</span><span class="sxs-lookup"><span data-stu-id="1bc5a-112">Change Default Data Type and Other Properties for a Report Parameter</span></span>](#ChangeDefaultProperties)  
  
    1.  [<span data-ttu-id="1bc5a-113">添加数据集以提供可用值和显示名称</span><span class="sxs-lookup"><span data-stu-id="1bc5a-113">Add a Dataset to Provide Available Values and Display Names</span></span>](#AddDataset)  
  
    2.  [<span data-ttu-id="1bc5a-114">指定可用值以创建值的下拉列表</span><span class="sxs-lookup"><span data-stu-id="1bc5a-114">Specify Available Values to Create a Drop-List of Values</span></span>](#AvailableValues)  
  
    3.  [<span data-ttu-id="1bc5a-115">指定默认值，以便自动运行报表</span><span class="sxs-lookup"><span data-stu-id="1bc5a-115">Specify Default Values so the Report Runs Automatically</span></span>](#DefaultValues)  
  
    4.  [<span data-ttu-id="1bc5a-116">从具有名称/值对的数据集查找值</span><span class="sxs-lookup"><span data-stu-id="1bc5a-116">Look up a Value from a Dataset that has Name/Value Pairs</span></span>](#NameValue)  
  
5.  [<span data-ttu-id="1bc5a-117">在报表中显示所选参数值</span><span class="sxs-lookup"><span data-stu-id="1bc5a-117">Display the Selected Parameter Value in the Report</span></span>](#Expression)  
  
6.  [<span data-ttu-id="1bc5a-118">在筛选器中使用报表参数</span><span class="sxs-lookup"><span data-stu-id="1bc5a-118">Use the Report Parameter in a Filter</span></span>](#Filter)  
  
7.  [<span data-ttu-id="1bc5a-119">更改报表参数以接受多个值</span><span class="sxs-lookup"><span data-stu-id="1bc5a-119">Change the Report Parameter to Accept Multiple Values</span></span>](#Multivalued)  
  
8.  [<span data-ttu-id="1bc5a-120">为条件可见性添加布尔参数</span><span class="sxs-lookup"><span data-stu-id="1bc5a-120">Add a Boolean Parameter for Conditional Visibility</span></span>](#Boolean)  
  
9. [<span data-ttu-id="1bc5a-121">添加报表标题</span><span class="sxs-lookup"><span data-stu-id="1bc5a-121">Add a Report Title</span></span>](#Title)  
  
10. [<span data-ttu-id="1bc5a-122">保存报表</span><span class="sxs-lookup"><span data-stu-id="1bc5a-122">Save the Report</span></span>](#Save)  
  
> [!NOTE]  
>  <span data-ttu-id="1bc5a-123">在本教程中，将向导的多个步骤合并为一个过程。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-123">In this tutorial, the steps for the wizard are consolidated into one procedure.</span></span> <span data-ttu-id="1bc5a-124">有关如何浏览到报表服务器、选择数据源和创建数据集的分步说明，请参阅本系列中的第一个教程：[教程：创建基本表报表（报表生成器）](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-124">For step-by-step instructions about how to browse to a report server, choose a data source, and create a dataset, see the first tutorial in this series: [Tutorial: Creating a Basic Table Report &#40;Report Builder&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md).</span></span>  
  
 <span data-ttu-id="1bc5a-125">本教程的预计学时：25 分钟。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-125">Estimated time to complete this tutorial: 25 minutes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1bc5a-126">要求</span><span class="sxs-lookup"><span data-stu-id="1bc5a-126">Requirements</span></span>  
 <span data-ttu-id="1bc5a-127">有关要求的信息，请参阅[教程先决条件（报表生成器）](../reporting-services/report-builder-tutorials.md)。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-127">For information about requirements, see [Prerequisites for Tutorials &#40;Report Builder&#41;](../reporting-services/report-builder-tutorials.md).</span></span>  
  
##  <a name="1-create-a-matrix-report-and-dataset-from-the-table-or-matrix-wizard"></a><a name="Setup"></a><span data-ttu-id="1bc5a-128">1. 使用表或矩阵向导创建矩阵报表和数据集</span><span class="sxs-lookup"><span data-stu-id="1bc5a-128">1. Create a Matrix Report and Dataset from the Table or Matrix Wizard</span></span>  
 <span data-ttu-id="1bc5a-129">创建矩阵报表、数据源和数据集。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-129">Create a matrix report, a data source, and a dataset.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1bc5a-130">在本教程中，由于查询包含了数据值，因此它不需要外部数据源。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-130">In this tutorial, the query contains the data values, so that it does not need an external data source.</span></span> <span data-ttu-id="1bc5a-131">这样，查询就会非常长。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-131">This makes the query quite long.</span></span> <span data-ttu-id="1bc5a-132">在业务环境中，查询不会包含数据。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-132">In a business environment, a query would not contain the data.</span></span> <span data-ttu-id="1bc5a-133">本教程中的查询仅供学习使用。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-133">This is for learning purposes only.</span></span>  
  
#### <a name="to-create-a-new-matrix-report"></a><span data-ttu-id="1bc5a-134">创建新的矩阵报表</span><span class="sxs-lookup"><span data-stu-id="1bc5a-134">To create a new matrix report</span></span>  
  
1.  <span data-ttu-id="1bc5a-135">单击 "**开始**"，指向 "**程序**"，指向 [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)] "**报表生成器**"，然后单击 "**报表生成器**"。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-135">Click **Start**, point to **Programs**, point to [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)]**Report Builder**, and then click **Report Builder**.</span></span>  
  
     <span data-ttu-id="1bc5a-136">此时将显示 "**入门**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-136">The **Getting Started** dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1bc5a-137">如果未显示 "**入门**" 对话框，请在 "**报表生成器**" 按钮中单击 "**新建**"。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-137">If the **Getting Started** dialog box does not appear, from the **Report Builder** button, click **New**.</span></span>  
  
2.  <span data-ttu-id="1bc5a-138">在左窗格中，验证是否选择了 "**报表**"。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-138">In the left pane, verify that **Report** is selected.</span></span>  
  
3.  <span data-ttu-id="1bc5a-139">在右窗格中，单击“表或矩阵向导”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-139">In the right pane, click **Table or Matrix Wizard**.</span></span>  
  
4.  <span data-ttu-id="1bc5a-140">单击“创建”。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-140">Click **Create**.</span></span>  
  
5.  <span data-ttu-id="1bc5a-141">在“选择数据集”页上，单击“创建数据集”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-141">On the **Choose a dataset** page, click **Create a dataset**.</span></span>  
  
6.  <span data-ttu-id="1bc5a-142">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-142">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="1bc5a-143">在“选择数据源的连接”\*\*\*\* 页上，选择类型为“SQL Server”\*\*\*\* 的数据源。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-143">On the **Choose a connection to a data source** page, select a data source that is type **SQL Server**.</span></span> <span data-ttu-id="1bc5a-144">从列表中选择一个数据源或浏览到报表服务器以选择一个数据源。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-144">Select a data source from the list or browse to the report server to select one.</span></span>  
  
8.  <span data-ttu-id="1bc5a-145">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-145">Click **Next**.</span></span>  
  
9. <span data-ttu-id="1bc5a-146">在“设计查询”页上，单击“编辑为文本”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-146">On the **Design a query** page, click **Edit as Text**.</span></span>  
  
10. <span data-ttu-id="1bc5a-147">将以下查询粘贴到查询窗格中：</span><span class="sxs-lookup"><span data-stu-id="1bc5a-147">Paste the following query into the query pane:</span></span>  
  
    ```  
    ;WITH CTE (StoreID, Subcategory, Quantity)   
    AS (  
    SELECT 200 AS StoreID, 'Digital SLR Cameras' AS Subcategory, 2002 AS Quantity  
    UNION SELECT  200 AS StoreID, 'Camcorders' AS Subcategory, 1954 AS Quantity  
    UNION SELECT  200 AS StoreID, 'Accessories' AS Subcategory, 1895 AS Quantity  
    UNION SELECT  199 AS StoreID, 'Digital Cameras' AS Subcategory, 1849 AS Quantity  
    UNION SELECT  306 AS StoreID, 'Digital SLR Cameras' AS Subcategory, 1579 AS Quantity  
    UNION SELECT  306 AS StoreID, 'Camcorders' AS Subcategory, 1561 AS Quantity  
    UNION SELECT  306 AS StoreID, 'Digital Cameras' AS Subcategory, 1553 AS Quantity  
    UNION SELECT  306 AS StoreID, 'Accessories' AS Subcategory, 1534 AS Quantity  
    UNION SELECT 307 AS StoreID, 'Accessories' AS Subcategory, 1755 AS Quantity  
    UNION SELECT 307 AS StoreID, 'Camcorders' AS Subcategory, 1631 AS Quantity  
    UNION SELECT 307 AS StoreID, 'Digital SLR Cameras' AS Subcategory, 1772 AS Quantity)  
    SELECT StoreID, Subcategory, Quantity  
    FROM CTE  
    ```  
  
     <span data-ttu-id="1bc5a-148">此查询在一个公用表表达式中组合了若干 [!INCLUDE[tsql](../includes/tsql-md.md)] SELECT 语句的结果，以指定基于来自 Contoso 示例数据库的简化数据的值。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-148">This query combines the results of several [!INCLUDE[tsql](../includes/tsql-md.md)] SELECT statements inside a common table expression to specify values that are based on simplified data from the Contoso sample database.</span></span> <span data-ttu-id="1bc5a-149">Contoso 销售数据表示消费品的国际销售数据。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-149">The Contoso sales data represents international sales data for consumer goods.</span></span> <span data-ttu-id="1bc5a-150">本教程使用相机的销售数据。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-150">This tutorial uses sales data for cameras.</span></span> <span data-ttu-id="1bc5a-151">子类别表示数码相机、数码单反 (SLR) 相机、摄像机和附件。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-151">The subcategories represent digital cameras, digital single lens reflex (SLR) cameras, camcorders, and accessories.</span></span>  
  
     <span data-ttu-id="1bc5a-152">此查询指定了列名称，包括一个商店标识符、一个销售物品子类别以及三个商店的销售订单的订购数量。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-152">The query specifies column names that include a store identifier, a sales item subcategory, and the quantity ordered for sales orders from three stores.</span></span> <span data-ttu-id="1bc5a-153">在此查询中，商店名称不是结果集的一部分。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-153">In this query, the store name is not part of the result set.</span></span> <span data-ttu-id="1bc5a-154">接下来，您将在本教程中从单独的数据集查找与商店标识符对应的商店名称。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-154">Later in this tutorial, you will look up the name of the store that corresponds to the store identifier from a separate dataset.</span></span>  
  
     <span data-ttu-id="1bc5a-155">此查询不包含查询参数。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-155">This query does not contain query parameters.</span></span> <span data-ttu-id="1bc5a-156">稍后，您将在本教程中添加查询参数。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-156">You will add query parameters later in this tutorial.</span></span>  
  
11. <span data-ttu-id="1bc5a-157">在查询设计器工具栏上，单击 "**运行** (**！**) "。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-157">On the query designer toolbar, click **Run** (**!**).</span></span> <span data-ttu-id="1bc5a-158">结果集显示 11 行数据，这些数据显示针对四个商店的每个子类别销售的物品数量，并且结果集包含以下列：StoreID、Subcategory、Quantity。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-158">The result set displays 11 rows of data that show the quantity of items sold for each subcategory for four stores, and includes the following columns: StoreID, Subcategory, Quantity.</span></span>  
  
12. <span data-ttu-id="1bc5a-159">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-159">Click **Next**.</span></span>  
  
##  <a name="2-organize-data-choose-layout-and-style-from-the-table-or-matrix-wizard"></a><a name="CompleteWizard"></a><span data-ttu-id="1bc5a-160">2. 在表或矩阵向导中组织数据、选择布局和样式</span><span class="sxs-lookup"><span data-stu-id="1bc5a-160">2. Organize Data, Choose Layout, and Style from the Table or Matrix Wizard</span></span>  
 <span data-ttu-id="1bc5a-161">使用此向导可提供用于显示数据的起始设计。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-161">Use the wizard to provide a starting design on which to display data.</span></span> <span data-ttu-id="1bc5a-162">此向导中的预览窗格可帮助您在完成表或矩阵设计之前将对数据进行分组的结果可视化。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-162">The preview pane in the wizard helps you to visualize the result of grouping data before you complete the table or matrix design.</span></span>  
  
#### <a name="to-organize-data-into-groups"></a><span data-ttu-id="1bc5a-163">将数据组织到组中</span><span class="sxs-lookup"><span data-stu-id="1bc5a-163">To organize data into groups</span></span>  
  
1.  <span data-ttu-id="1bc5a-164">在“排列字段”页上，将 Subcategory 拖到“行组”中\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-164">On the **Arrange fields** page, drag Subcategory to **Row groups**.</span></span>  
  
2.  <span data-ttu-id="1bc5a-165">将 StoreID 拖到“列组”中\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-165">Drag StoreID to **Column groups**.</span></span>  
  
3.  <span data-ttu-id="1bc5a-166">将 Quantity 拖到“值”中\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-166">Drag Quantity to **Values**.</span></span>  
  
     <span data-ttu-id="1bc5a-167">已将销售量的值组织到按子类别分组的行中。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-167">You have organized the quantity sold values in rows grouped by subcategory.</span></span> <span data-ttu-id="1bc5a-168">每个商店将对应一个列。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-168">There will be one column for each store.</span></span>  
  
4.  <span data-ttu-id="1bc5a-169">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-169">Click **Next**.</span></span>  
  
5.  <span data-ttu-id="1bc5a-170">在 "**选择布局**" 页的 "**选项**" 下，验证是否选择了 "**显示小计和总计**"。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-170">On the **Choose a Layout** page, under **Options**, verify that **Show subtotals and grand totals** is selected.</span></span>  
  
     <span data-ttu-id="1bc5a-171">当您运行报表时，最后一列将显示所有商店的每个子类别的总数量，而最后一行将显示每个商店的所有子类别的总数量。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-171">When you run the report, the last column will show the total quantity of each subcategory for all stores, and the last row will show the total quantity for all subcategories for each store.</span></span>  
  
6.  <span data-ttu-id="1bc5a-172">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-172">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="1bc5a-173">在 "**选择样式**" 页上的 "样式" 窗格中，选择样式。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-173">On the **Choose a Style** page, in the Styles pane, select a style.</span></span>  
  
8.  <span data-ttu-id="1bc5a-174">单击“完成”。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-174">Click **Finish**.</span></span>  
  
     <span data-ttu-id="1bc5a-175">矩阵将添加到设计图面中。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-175">The matrix is added to the design surface.</span></span> <span data-ttu-id="1bc5a-176">矩阵将显示 3 列和 3 行。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-176">The matrix displays three columns and three rows.</span></span> <span data-ttu-id="1bc5a-177">第一行中的单元格内容是 Subcategory、[StoreID] 和“总计”。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-177">The contents of the cells in the first row are Subcategory, [StoreID], and Total.</span></span> <span data-ttu-id="1bc5a-178">第二行中的单元格内容包含的表达式表示子类别、每个商店销售的物品数量以及所有商店每个子类别的总数量。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-178">The contents of the cells in the second row contain expressions that represent the subcategory, the quantity of items sold for each store, and the total quantity for each subcategory for all stores.</span></span> <span data-ttu-id="1bc5a-179">最后一行中的单元格显示每个商店的总计。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-179">The cells in the final row display the grand total for each store.</span></span>  
  
9. <span data-ttu-id="1bc5a-180">在矩阵中单击，将光标悬停在第一个列的边缘并抓住句柄，然后扩展列宽。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-180">Click in the matrix, hover over the edge of the first column, grab the handle, and expand the column width.</span></span>  
  
10. <span data-ttu-id="1bc5a-181">单击 **“运行”** 以预览报表。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-181">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="1bc5a-182">报表将在报表服务器上运行并显示标题以及进行报表处理的时间。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-182">The report runs on the report server and displays the title and the time the report processing occurred.</span></span>  
  
 <span data-ttu-id="1bc5a-183">在此方案中，列标题显示的是商店标识符而不是商店名称。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-183">In this scenario, the column headings display the store identifier but not the store name.</span></span> <span data-ttu-id="1bc5a-184">接下来，您将添加表达式以便在包含商店标识符/商店名称对的数据集中查找商店名称。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-184">Later, you will add an expression to look up the store name in a dataset that contains store identifier/store name pairs.</span></span>  
  
##  <a name="3-add-a-query-parameter-to-create-a-report-parameter"></a><a name="Query"></a><span data-ttu-id="1bc5a-185">3. 添加查询参数以创建报表参数</span><span class="sxs-lookup"><span data-stu-id="1bc5a-185">3. Add a Query Parameter to Create a Report Parameter</span></span>  
 <span data-ttu-id="1bc5a-186">当向查询添加查询参数时，报表生成器将自动创建单值报表参数，其中名称、提示符和数据类型使用默认属性。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-186">When you add a query parameter to a query, Report Builder automatically creates a single-valued report parameter with default properties for name, prompt, and data type.</span></span>  
  
#### <a name="to-add-a-query-parameter"></a><span data-ttu-id="1bc5a-187">添加查询参数</span><span class="sxs-lookup"><span data-stu-id="1bc5a-187">To add a query parameter</span></span>  
  
1.  <span data-ttu-id="1bc5a-188">切换到“设计”视图。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-188">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="1bc5a-189">在“报表数据”窗格中，展开“数据集”文件夹，右键单击“DataSet1”，然后单击“查询”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-189">In the Report Data pane, expand the **Datasets** folder, right-click **DataSet1**, and then click **Query**.</span></span>  
  
3.  <span data-ttu-id="1bc5a-190">将以下子句添加到 [!INCLUDE[tsql](../includes/tsql-md.md)] `WHERE` 查询中的最后一行：</span><span class="sxs-lookup"><span data-stu-id="1bc5a-190">Add the following [!INCLUDE[tsql](../includes/tsql-md.md)] `WHERE` clause as the last line in the query:</span></span>  
  
    ```  
    WHERE StoreID = (@StoreID)  
    ```  
  
     <span data-ttu-id="1bc5a-191">子句将检索到的 `WHERE` 数据限制为查询参数指定的存储区标识符 *@StoreID* 。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-191">The `WHERE` clause limits the retrieved data to the store identifier that is specified by the query parameter *@StoreID*.</span></span>  
  
4.  <span data-ttu-id="1bc5a-192">在查询设计器工具栏上，单击 "**运行** (**！**) "。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-192">On the query designer toolbar, click **Run** (**!**).</span></span> <span data-ttu-id="1bc5a-193">此时将打开“定义查询参数”对话框，提示用户为查询参数 @StoreID 输入值\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-193">The **Define Query Parameters** dialog box opens and prompts for a value for the query parameter *@StoreID*.</span></span>  
  
5.  <span data-ttu-id="1bc5a-194">在“参数值”\*\*\*\* 中，键入 **200**。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-194">In **Parameter Value**, type **200**.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="1bc5a-195">结果集显示了标识符为 **200**的商店销售的附件、摄像机和数码 SLR 相机数量。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-195">The result set displays the quantities sold for Accessories, Camcorders, and Digital SLR Cameras for the store identifier **200**.</span></span>  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
8.  <span data-ttu-id="1bc5a-196">在“报表数据”窗格中，展开“参数”\*\*\*\* 文件夹。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-196">In the Report Data pane, expand the **Parameters** folder.</span></span>  
  
 <span data-ttu-id="1bc5a-197">请注意，现在有一个名为的报表参数 *@StoreID* 。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-197">Notice that there is now a report parameter named *@StoreID*.</span></span> <span data-ttu-id="1bc5a-198">默认情况下，参数的数据类型为**Text**。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-198">By default, the parameter has data type **Text**.</span></span> <span data-ttu-id="1bc5a-199">由于商店标识符是一个整数，因此在下一个过程中将数据类型更改为 Integer。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-199">Because the store identifier is an integer, you will change the data type to Integer in the next procedure.</span></span>  
  
##  <a name="4-change-default-data-type-and-other-properties-for-a-report-parameter"></a><a name="ChangeDefaultProperties"></a><span data-ttu-id="1bc5a-200">4. 更改报表参数的默认数据类型和其他属性</span><span class="sxs-lookup"><span data-stu-id="1bc5a-200">4. Change Default Data Type and Other Properties for a Report Parameter</span></span>  
 <span data-ttu-id="1bc5a-201">创建报表参数之后，可以调整属性的默认值。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-201">After a report parameter is created, you can adjust the default values for properties.</span></span>  
  
#### <a name="to-change-the-default-data-type-for-a-report-parameter"></a><span data-ttu-id="1bc5a-202">更改报表参数的默认数据类型</span><span class="sxs-lookup"><span data-stu-id="1bc5a-202">To change the default data type for a report parameter</span></span>  
  
1.  <span data-ttu-id="1bc5a-203">在 "报表数据" 窗格的 "**参数**" 节点下，右键单击 *@StoreID* ，然后单击 "**参数属性**"。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-203">In the Report Data pane under the **Parameters** node, right-click *@StoreID*, and then click **Parameter Properties**.</span></span>  
  
2.  <span data-ttu-id="1bc5a-204">在提示符下，键入**Store identifier？**</span><span class="sxs-lookup"><span data-stu-id="1bc5a-204">In Prompt, type **Store identifier?**</span></span> <span data-ttu-id="1bc5a-205">当您运行报表时，此文本出现在报表查看器工具栏上。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-205">This text appears on the report viewer toolbar when you run the report.</span></span>  
  
3.  <span data-ttu-id="1bc5a-206">在“数据类型”的下拉列表中，选择“整数”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-206">In **Data type**, from the drop-down list, select **Integer**.</span></span>  
  
4.  <span data-ttu-id="1bc5a-207">接受对话框中的其他默认值。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-207">Accept the remaining default values in the dialog box.</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="1bc5a-208">预览报表。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-208">Preview the report.</span></span> <span data-ttu-id="1bc5a-209">报表查看器将显示的提示 *@StoreID* 。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-209">The report viewer displays the prompt for *@StoreID*.</span></span>  
  
7.  <span data-ttu-id="1bc5a-210">在报表查看器工具栏上，在 Store ID 的旁边键入 **200**，然后单击“查看报表”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-210">On the report viewer toolbar, next to Store ID, type **200**, and then click **View Report**.</span></span>  
  
##  <a name="4a-add-a-dataset-to-provide-available-values-and-display-names"></a><a name="AddDataset"></a><span data-ttu-id="1bc5a-211">4a.</span><span class="sxs-lookup"><span data-stu-id="1bc5a-211">4a.</span></span> <span data-ttu-id="1bc5a-212">添加数据集以提供可用值和显示名称</span><span class="sxs-lookup"><span data-stu-id="1bc5a-212">Add a Dataset to Provide Available Values and Display Names</span></span>  
 <span data-ttu-id="1bc5a-213">若要确保用户只能为参数键入有效值，可以创建一个从中选择值的值下拉列表。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-213">To ensure a user can type only valid values for a parameter, you can create a drop-down list of values to choose from.</span></span> <span data-ttu-id="1bc5a-214">值可以来自于您指定的数据集或列表。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-214">The values can come from a dataset or from a list that you specify.</span></span> <span data-ttu-id="1bc5a-215">可用值必须由具有不包含对参数的引用的查询的数据集提供。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-215">Available values must be supplied from a dataset that has a query that does not contain a reference to the parameter.</span></span>  
  
#### <a name="to-create-a-dataset-for-valid-values-for-a-parameter"></a><span data-ttu-id="1bc5a-216">为参数创建有效值数据集</span><span class="sxs-lookup"><span data-stu-id="1bc5a-216">To create a dataset for valid values for a parameter</span></span>  
  
1.  <span data-ttu-id="1bc5a-217">切换到“设计”视图。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-217">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="1bc5a-218">在“报表数据”窗格中，右键单击“数据集”文件夹，然后单击“添加数据集”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-218">In the Report Data pane, right-click the **Datasets** folder, and then click **Add Dataset**.</span></span>  
  
3.  <span data-ttu-id="1bc5a-219">在“名称”中，键入“Stores”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-219">In **Name**, type **Stores**.</span></span>  
  
4.  <span data-ttu-id="1bc5a-220">选择 "**使用在我的报表中嵌入的数据集**" 选项。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-220">Select the **Use a dataset embedded in my report** option.</span></span>  
  
5.  <span data-ttu-id="1bc5a-221">在 "**数据源**" 的下拉列表中，选择在第一个过程中创建的数据源。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-221">In **Data source**, from the drop-down list, choose the data source you created in the first procedure.</span></span>  
  
6.  <span data-ttu-id="1bc5a-222">在“查询类型”中，确保已选中“文本”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-222">In **Query type**, verify that **Text** is selected.</span></span>  
  
7.  <span data-ttu-id="1bc5a-223">在“查询”中，粘贴以下文本\*\*\*\*：</span><span class="sxs-lookup"><span data-stu-id="1bc5a-223">In **Query**, paste the following text:</span></span>  
  
    ```  
    SELECT 200 AS StoreID, 'Contoso Catalog Store' as StoreName  
    UNION SELECT 199 AS StoreID, 'Contoso North America Online Store' as StoreName  
    UNION SELECT 307 AS StoreID, 'Contoso Asia Online Store' as StoreName  
    UNION SELECT 306 AS StoreID, 'Contoso Europe Online Store' as StoreName  
    ```  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="1bc5a-224">“报表数据”窗格在 **Stores** 数据集节点下显示字段 StoreID 和 StoreName。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-224">The Report Data pane displays the fields StoreID and StoreName under the **Stores** dataset node.</span></span>  
  
##  <a name="4b-specify-available-values-to-create-a-drop-down-list-of-values"></a><a name="AvailableValues"></a><span data-ttu-id="1bc5a-225">4b.</span><span class="sxs-lookup"><span data-stu-id="1bc5a-225">4b.</span></span> <span data-ttu-id="1bc5a-226">指定可用值以创建值的下拉列表</span><span class="sxs-lookup"><span data-stu-id="1bc5a-226">Specify Available Values to Create a Drop-down List of Values</span></span>  
 <span data-ttu-id="1bc5a-227">在创建数据集以提供可用值之后，必须更改报表属性，以指定将哪个数据集和哪个字段用于填充报表查看器工具栏上的有效值下拉列表。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-227">After you create a dataset to provide available values, you must change the report properties to specify which dataset and which field to use to populate the drop-down list of valid values on the reportviewer toolbar.</span></span>  
  
#### <a name="to-provide-available-values-for-a-parameter-from-a-dataset"></a><span data-ttu-id="1bc5a-228">为参数提供数据集中的可用值</span><span class="sxs-lookup"><span data-stu-id="1bc5a-228">To provide available values for a parameter from a dataset</span></span>  
  
1.  <span data-ttu-id="1bc5a-229">在 "报表数据" 窗格中，右键单击参数 *@StoreID* ，然后单击 "**参数属性**"。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-229">In the Report Data pane, right-click the parameter *@StoreID*, and then click **Parameter Properties**.</span></span>  
  
2.  <span data-ttu-id="1bc5a-230">单击“可用值”\*\*\*\*，然后单击“从查询中获取值”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-230">Click **Available Values**, and then click **Get values from a query**.</span></span>  
  
3.  <span data-ttu-id="1bc5a-231">在“数据集”的下拉列表中，单击“Stores”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-231">In **Dataset**, from the drop-down list, click **Stores**.</span></span>  
  
4.  <span data-ttu-id="1bc5a-232">在“值字段”的下拉列表中，单击“StoreID”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-232">In **Value field**, from the drop-down list, click StoreID.</span></span>  
  
5.  <span data-ttu-id="1bc5a-233">在“标签字段”的下拉列表中，单击“StoreName”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-233">In **Label field**, from the drop-down list, click StoreName.</span></span> <span data-ttu-id="1bc5a-234">标签字段指定值的显示名称。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-234">The label field specifies the display name for the value.</span></span>  
  
6.  <span data-ttu-id="1bc5a-235">单击“常规”。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-235">Click **General**.</span></span>  
  
7.  <span data-ttu-id="1bc5a-236">在提示符下，键入**Store name？**</span><span class="sxs-lookup"><span data-stu-id="1bc5a-236">In Prompt, type **Store name?**</span></span>  
  
     <span data-ttu-id="1bc5a-237">用户现在将从商店名称列表而非商店标识符列表中进行选择。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-237">The user will now select from a list of store names instead of store identifiers.</span></span> <span data-ttu-id="1bc5a-238">请注意，参数数据类型保持为 **Integer** ，因为参数是基于商店标识符而不是商店名称。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-238">Note that the parameter data type remains **Integer** because the parameter is based on the store identifier, not the store name.</span></span>  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
9. <span data-ttu-id="1bc5a-239">预览报表。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-239">Preview the report.</span></span>  
  
     <span data-ttu-id="1bc5a-240">在报表查看器工具栏中，参数文本框现在为显示的下拉列表 **\<Select a Value>** 。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-240">In the report viewer toolbar, the parameter text box is now a drop-down list that displays **\<Select a Value>**.</span></span>  
  
10. <span data-ttu-id="1bc5a-241">从下拉列表中，选择 "Contoso Catalog Store"，然后单击 "**查看报告**"。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-241">From the drop-down list, select Contoso Catalog Store, and then click **View Report**.</span></span>  
  
 <span data-ttu-id="1bc5a-242">报表显示了标识符为 **200**的商店销售的附件、摄像机和数码 SLR 相机数量。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-242">The report displays the quantity sold for Accessories, Camcorders, and Digital SLR Cameras for the store identifier **200**.</span></span>  
  
##  <a name="4c-specify-default-values-so-the-report-runs-automatically"></a><a name="DefaultValues"></a><span data-ttu-id="1bc5a-243">4c.</span><span class="sxs-lookup"><span data-stu-id="1bc5a-243">4c.</span></span> <span data-ttu-id="1bc5a-244">指定默认值，以便自动运行报表</span><span class="sxs-lookup"><span data-stu-id="1bc5a-244">Specify Default Values so the Report Runs Automatically</span></span>  
 <span data-ttu-id="1bc5a-245">可以为每个参数指定默认值，以便自动运行报表。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-245">You can specify a default value for each parameter so the report runs automatically.</span></span>  
  
#### <a name="to-specify-a-default-value-from-a-dataset"></a><span data-ttu-id="1bc5a-246">从数据集中指定默认值</span><span class="sxs-lookup"><span data-stu-id="1bc5a-246">To specify a default value from a dataset</span></span>  
  
1.  <span data-ttu-id="1bc5a-247">切换到“设计”视图。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-247">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="1bc5a-248">在 "报表数据" 窗格中，右键单击 *@StoreID* ，然后单击 "**参数属性**"。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-248">In the Report Data pane, right-click *@StoreID*, and then click **Parameter Properties**.</span></span>  
  
3.  <span data-ttu-id="1bc5a-249">单击 "**默认值**"，然后单击 "**从查询中获取值**"。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-249">Click **Default Values**, and then click **Get values from a query**.</span></span>  
  
4.  <span data-ttu-id="1bc5a-250">在“数据集”的下拉列表中，单击“Stores”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-250">In **Dataset**, from the drop-down list, click **Stores**.</span></span>  
  
5.  <span data-ttu-id="1bc5a-251">在“值字段”的下拉列表中，单击“StoreID”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-251">In **Value field**, from the drop-down list, click StoreID.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  <span data-ttu-id="1bc5a-252">预览报表。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-252">Preview the report.</span></span>  
  
 <span data-ttu-id="1bc5a-253">对于 *@StoreID* ，报表查看器显示值 "Contoso 北美 Online Store"。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-253">For *@StoreID*, the report viewer displays the value "Contoso North America Online Store".</span></span> <span data-ttu-id="1bc5a-254">这是数据集**存储**的结果集中的第一个值。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-254">This is the first value from the result set for the dataset **Stores**.</span></span> <span data-ttu-id="1bc5a-255">报表显示了标识符为 **199**的商店销售的数码相机数量。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-255">The report displays the quantity sold for Digital Cameras for store identifier **199**.</span></span>  
  
#### <a name="to-specify-a-custom-default-value"></a><span data-ttu-id="1bc5a-256">指定自定义默认值</span><span class="sxs-lookup"><span data-stu-id="1bc5a-256">To specify a custom default value</span></span>  
  
1.  <span data-ttu-id="1bc5a-257">切换到“设计”视图。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-257">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="1bc5a-258">在 "报表数据" 窗格中，右键单击 *@StoreID* ，然后单击 "**参数属性**"。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-258">In the Report Data pane, right-click *@StoreID*, and then click **Parameter Properties**.</span></span>  
  
3.  <span data-ttu-id="1bc5a-259">单击 "**默认值**"，然后单击 "**指定值**"，然后单击 "**添加**"。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-259">Click **Default Values**, and click **Specify values**, and then click **Add**.</span></span> <span data-ttu-id="1bc5a-260">此时将添加一个新的值行。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-260">A new value row is added.</span></span>  
  
4.  <span data-ttu-id="1bc5a-261">在“值”中，键入“200”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-261">In **Value**, type **200**.</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="1bc5a-262">预览报表。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-262">Preview the report.</span></span>  
  
 <span data-ttu-id="1bc5a-263">对于 *@StoreID* ，报表查看器显示值 "Contoso Catalog Store"。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-263">For *@StoreID*, the report viewer displays the value "Contoso Catalog Store".</span></span> <span data-ttu-id="1bc5a-264">这是商店标识符**200**的显示名称。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-264">This is the display name for store identifier **200**.</span></span> <span data-ttu-id="1bc5a-265">报表显示了标识符为 **200**的商店销售的附件、摄像机和数码 SLR 相机数量。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-265">The report displays the quantity sold for Accessories, Camcorders, and Digital SLR Cameras for the store identifier **200**.</span></span>  
  
##  <a name="4d-look-up-a-value-from-a-dataset-that-has-namevalue-pairs"></a><a name="NameValue"></a><span data-ttu-id="1bc5a-266">4d.</span><span class="sxs-lookup"><span data-stu-id="1bc5a-266">4d.</span></span> <span data-ttu-id="1bc5a-267">从具有名称/值对的数据集查找值</span><span class="sxs-lookup"><span data-stu-id="1bc5a-267">Look up a Value from a Dataset that has Name/Value Pairs</span></span>  
 <span data-ttu-id="1bc5a-268">数据集可以同时包含标识符和对应的名称字段。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-268">A dataset might contain both the identifier and the corresponding name field.</span></span> <span data-ttu-id="1bc5a-269">若只有一个标识符，则可以在创建的包含名称/值对的数据集中查找对应的名称。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-269">When you only have an identifier, you can look up the corresponding name in a dataset that you created that includes name/value pairs.</span></span>  
  
#### <a name="to-look-up-a-value-from-a-dataset"></a><span data-ttu-id="1bc5a-270">从数据集查找值</span><span class="sxs-lookup"><span data-stu-id="1bc5a-270">To look up a value from a dataset</span></span>  
  
1.  <span data-ttu-id="1bc5a-271">切换到“设计”视图。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-271">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="1bc5a-272">在设计图面上，在矩阵的第一行的列标题中，右键单击 `[StoreID]`，然后单击“表达式”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-272">On the design surface, in the matrix, in the first row column header, right-click `[StoreID]` and then click **Expression**.</span></span>  
  
3.  <span data-ttu-id="1bc5a-273">在表达式窗格中，删除除开头的 `equals` (=) 之外的所有文本。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-273">In the expression pane, delete all text except the beginning `equals` (=).</span></span>  
  
4.  <span data-ttu-id="1bc5a-274">在“类别”中，展开“常见函数”，然后单击“杂项”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-274">In **Category**, expand **Common Functions**, and click **Miscellaneous**.</span></span> <span data-ttu-id="1bc5a-275">“项”窗格将显示一组函数。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-275">The Item pane displays a set of functions.</span></span>  
  
5.  <span data-ttu-id="1bc5a-276">在“项”中，双击“查找”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-276">In Item, double-click **Lookup**.</span></span> <span data-ttu-id="1bc5a-277">表达式窗格将显示 `=Lookup(`。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-277">The expression pane displays `=Lookup(`.</span></span> <span data-ttu-id="1bc5a-278">“示例”窗格将显示一个 Lookup 语法示例。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-278">The Example pane displays an example of Lookup syntax.</span></span>  
  
6.  <span data-ttu-id="1bc5a-279">键入以下表达式： `=Lookup(Fields!StoreID.Value,Fields!StoreID.Value,Fields!StoreName.Value,"Stores")`</span><span class="sxs-lookup"><span data-stu-id="1bc5a-279">Type the following expression: `=Lookup(Fields!StoreID.Value,Fields!StoreID.Value,Fields!StoreName.Value,"Stores")`</span></span>  
  
     <span data-ttu-id="1bc5a-280">Lookup 函数将采用 StoreID 的值，在“Stores”数据集中查找该值，并返回 StoreName 值。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-280">The Lookup function takes the value for StoreID, looks it up in the "Stores" dataset, and returns the StoreName value.</span></span>  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="1bc5a-281">Store 列标题包含复杂表达式的显示文本： **<\<Expr>>** 。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-281">The store column header contains the display text for a complex expression: **<\<Expr>>**.</span></span>  
  
8.  <span data-ttu-id="1bc5a-282">预览报表。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-282">Preview the report.</span></span>  
  
 <span data-ttu-id="1bc5a-283">每个页顶部的文本框显示商店名称而不是商店标识符。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-283">The text box at the top of each page displays the store name instead of the store identifier.</span></span>  
  
##  <a name="5-display-the-selected-parameter-value-in-the-report"></a><a name="Expression"></a><span data-ttu-id="1bc5a-284">5. 在报表中显示所选参数值</span><span class="sxs-lookup"><span data-stu-id="1bc5a-284">5. Display the Selected Parameter Value in the Report</span></span>  
 <span data-ttu-id="1bc5a-285">当用户对报表有疑问时，此操作可帮助用户获知他们选择的参数值。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-285">When a user has questions about a report, it helps to know which parameter values they chose.</span></span> <span data-ttu-id="1bc5a-286">可以在报表中保留用户为每个参数的选定的值。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-286">You can preserve user-selected values for each parameter in the report.</span></span> <span data-ttu-id="1bc5a-287">实现这一点的一种方式是在页脚的文本框中显示参数。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-287">One way is to display the parameters in a text box in the page footer.</span></span>  
  
#### <a name="to-display-the-selected-parameter-value-and-label-on-a-page-footer"></a><span data-ttu-id="1bc5a-288">在页脚中显示所选参数值和标签</span><span class="sxs-lookup"><span data-stu-id="1bc5a-288">To display the selected parameter value and label on a page footer</span></span>  
  
1.  <span data-ttu-id="1bc5a-289">切换到“设计”视图。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-289">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="1bc5a-290">右键单击页脚，指向 "**插入**"，然后单击 "**文本框**"。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-290">Right-click the page footer, point to **Insert**, and then click **Text Box**.</span></span> <span data-ttu-id="1bc5a-291">拖动带时间戳的文本框旁边的文本框。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-291">Drag the text box next to the text box with the time stamp.</span></span> <span data-ttu-id="1bc5a-292">抓住该文本框的侧手柄并扩展宽度。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-292">Grab the side handle of the text box and expand the width.</span></span>  
  
3.  <span data-ttu-id="1bc5a-293">从 "报表数据" 窗格中，将参数拖 *@StoreID* 到文本框中。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-293">From the Report Data pane, drag the parameter *@StoreID* to the text box.</span></span> <span data-ttu-id="1bc5a-294">文本框显示 `[@StoreID]`。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-294">The text box displays `[@StoreID]`.</span></span>  
  
4.  <span data-ttu-id="1bc5a-295">若要显示参数标签，请在文本框中单击，直到插入游标出现在现有表达式之后，键入一个空格，然后从“报表数据”窗格将参数的另一个副本拖到文本框。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-295">To display the parameter label, click in the text box until the insert cursor appears after the existing expression, type a space, and then drag another copy of the parameter from the Report Data pane to the text box.</span></span> <span data-ttu-id="1bc5a-296">文本框显示 `[@StoreID] [@StoreID]`。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-296">The text box displays `[@StoreID] [@StoreID]`.</span></span>  
  
5.  <span data-ttu-id="1bc5a-297">右键单击第一个表达式，然后单击 "**表达式**"。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-297">Right-click the first expression and click **Expression**.</span></span> <span data-ttu-id="1bc5a-298">此时将打开 **“表达式”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-298">The **Expression** dialog box opens.</span></span> <span data-ttu-id="1bc5a-299">文本 `Value` 已由 `Label` 代替。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-299">Replace the text `Value` by `Label`.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="1bc5a-300">文本显示： `[@StoreID.Label] [@StoreID]`。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-300">The text displays: `[@StoreID.Label] [@StoreID]`.</span></span>  
  
7.  <span data-ttu-id="1bc5a-301">预览报表。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-301">Preview the report.</span></span>  
  
##  <a name="6-use-the-report-parameter-in-a-filter"></a><a name="Filter"></a><span data-ttu-id="1bc5a-302">6. 在筛选器中使用报表参数</span><span class="sxs-lookup"><span data-stu-id="1bc5a-302">6. Use the Report Parameter in a Filter</span></span>  
 <span data-ttu-id="1bc5a-303">筛选器可帮助控制在从外部数据源检索到数据后在报表中使用哪些数据。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-303">Filters help control which data to use in a report after it is retrieved from an external data source.</span></span> <span data-ttu-id="1bc5a-304">为了让用户能够帮助控制他们要看到的数据，可以在矩阵的筛选器中包含报表参数。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-304">To let a user help control the data they want to see, you can include the report parameter in a filter for the matrix.</span></span>  
  
#### <a name="to-specify-a-parameter-in-a-matrix-filter"></a><span data-ttu-id="1bc5a-305">在矩阵筛选器中指定参数</span><span class="sxs-lookup"><span data-stu-id="1bc5a-305">To specify a parameter in a matrix filter</span></span>  
  
1.  <span data-ttu-id="1bc5a-306">切换到“设计”视图。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-306">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="1bc5a-307">右键单击矩阵中的某个行或列标题句柄，然后单击“Tablix 属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-307">Right-click a row or column header handle on the matrix, and then click **Tablix Properties**.</span></span>  
  
3.  <span data-ttu-id="1bc5a-308">单击“筛选器”，然后单击“添加”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-308">Click **Filters**, and then click **Add**.</span></span> <span data-ttu-id="1bc5a-309">此时将显示一个新的筛选器行。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-309">A new filter row appears.</span></span>  
  
4.  <span data-ttu-id="1bc5a-310">在“表达式”的下拉列表中，选择数据集字段 StoreID\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-310">In **Expression**, from the drop-down list, select the dataset field StoreID.</span></span> <span data-ttu-id="1bc5a-311">数据类型显示 **Integer**。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-311">The data type displays **Integer**.</span></span> <span data-ttu-id="1bc5a-312">当表达式值为数据集字段时，将自动设置数据类型。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-312">When the expression value is a dataset field, the data type is set automatically.</span></span>  
  
5.  <span data-ttu-id="1bc5a-313">在 "**运算符**" 中，验证是否选择了 " `equals` (=) "。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-313">In **Operator**, verify that `equals` (=) is selected.</span></span>  
  
6.  <span data-ttu-id="1bc5a-314">在“值”中键入 `[@StoreID]`。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="1bc5a-314">In **Value**, type `[@StoreID]`.</span></span> <span data-ttu-id="1bc5a-315">`[@StoreID]` 是一个简单表达式语法，它表示 `=Parameters!StoreID.Value`。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-315">`[@StoreID]` is the simple expression syntax that represents `=Parameters!StoreID.Value`.</span></span>  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
8.  <span data-ttu-id="1bc5a-316">预览报表。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-316">Preview the report.</span></span>  
  
     <span data-ttu-id="1bc5a-317">矩阵仅显示“Contoso Catalog Store”的数据。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-317">The matrix displays data only for "Contoso Catalog Store".</span></span>  
  
9. <span data-ttu-id="1bc5a-318">在报表查看器工具栏上，对于“Store name?”，选择“Contoso Asia Online Store”，然后单击“查看报表”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-318">On the report viewer toolbar, for **Store name?**, select **Contoso Asia Online Store**, and then click **View Report**.</span></span>  
  
 <span data-ttu-id="1bc5a-319">矩阵将显示与所选商店对应的数据。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-319">The matrix displays data that corresponds to the store that you selected.</span></span>  
  
##  <a name="7-change-the-report-parameter-to-accept-multiple-values"></a><a name="Multivalued"></a><span data-ttu-id="1bc5a-320">7. 更改报表参数以接受多个值</span><span class="sxs-lookup"><span data-stu-id="1bc5a-320">7. Change the Report Parameter to Accept Multiple Values</span></span>  
 <span data-ttu-id="1bc5a-321">若要将一个参数从单值参数更改为多值参数，则必须更改查询和包含对该参数的引用的所有表达式（包括筛选器）。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-321">To change a parameter from single to multivalued, you must change the query, and all expressions that contain a reference to the parameter, including filters.</span></span> <span data-ttu-id="1bc5a-322">多值参数是一个值数组。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-322">A multivalued parameter is an array of values.</span></span> <span data-ttu-id="1bc5a-323">在数据集查询中，查询语法必须一个值是否包含在一组值中。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-323">In a dataset query, query syntax must test for inclusion of one value in a set of values.</span></span> <span data-ttu-id="1bc5a-324">在报表表达式中，表达式语法必须访问一个值数组而不是单个值。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-324">In a report expression, expression syntax must access an array of values instead of an individual value.</span></span>  
  
#### <a name="to-change-a-parameter-from-single-to-multivalued"></a><span data-ttu-id="1bc5a-325">将一个参数从单值参数更改为多值参数</span><span class="sxs-lookup"><span data-stu-id="1bc5a-325">To change a parameter from single to multivalued</span></span>  
  
1.  <span data-ttu-id="1bc5a-326">切换到“设计”视图。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-326">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="1bc5a-327">在 "报表数据" 窗格中，右键单击 *@StoreID* ，然后单击 "**参数属性**"。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-327">In the Report Data pane, right-click *@StoreID*, and then click **Parameter Properties**.</span></span>  
  
3.  <span data-ttu-id="1bc5a-328">选择“允许多个值”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-328">Select **Allow multiple values**.</span></span>  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="1bc5a-329">在“报表数据”窗格中，展开“数据集”文件夹，右键单击“DataSet1”，然后单击“查询”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-329">In the Report Data pane, expand the **Datasets** folder, right-click **DataSet1**, and then click **Query**.</span></span>  
  
6.  <span data-ttu-id="1bc5a-330">在 `equals` `IN` 查询的最后一行中的 [!INCLUDE[tsql](../includes/tsql-md.md)] 子句中，更改 (=) `WHERE` ：</span><span class="sxs-lookup"><span data-stu-id="1bc5a-330">Change `equals` (=) to `IN` in the [!INCLUDE[tsql](../includes/tsql-md.md)] `WHERE` clause in the last line in the query:</span></span>  
  
    ```  
    WHERE StoreID IN (@StoreID)  
    ```  
  
     <span data-ttu-id="1bc5a-331">`IN` 运算符测试一个值是否包含在一组值中。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-331">The `IN` operator tests a value for inclusion in a set of values.</span></span>  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
8.  <span data-ttu-id="1bc5a-332">右键单击矩阵中的某个行或列标题句柄，然后单击“Tablix 属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-332">Right-click a row or column header handle on the matrix, and then click **Tablix Properties**.</span></span>  
  
9. <span data-ttu-id="1bc5a-333">单击 **“筛选器”** 。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-333">Click **Filters**.</span></span>  
  
10. <span data-ttu-id="1bc5a-334">在“运算符”中，选择“In”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-334">In **Operator**, select **In**.</span></span>  
  
11. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
12. <span data-ttu-id="1bc5a-335">从页脚中用于显示参数的文本框中删除所有文本。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-335">In the text box that displays the parameter in the page footer, delete all text.</span></span>  
  
13. <span data-ttu-id="1bc5a-336">右键单击该文本框，然后单击“表达式”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-336">Right-click the text box, and then click **Expression**.</span></span> <span data-ttu-id="1bc5a-337">键入以下表达式： `=Join(Parameters!StoreID.Label, ", ")`</span><span class="sxs-lookup"><span data-stu-id="1bc5a-337">Type the following expression: `=Join(Parameters!StoreID.Label, ", ")`</span></span>  
  
     <span data-ttu-id="1bc5a-338">此表达式将连接用户所选的所有商店名称。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-338">This expression concatenates all store names that the user selected.</span></span>  
  
14. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
15. <span data-ttu-id="1bc5a-339">在刚创建的表达式的前面的文本框中单击，然后键入以下内容：Parameter Values Selected:。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-339">Click in the text box in front of the expression that you just created, and then type the following: Parameter Values Selected:.</span></span>  
  
16. <span data-ttu-id="1bc5a-340">预览报表。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-340">Preview the report.</span></span>  
  
17. <span data-ttu-id="1bc5a-341">单击 Store Name? 旁边的下拉列表</span><span class="sxs-lookup"><span data-stu-id="1bc5a-341">Click the drop-down list next to Store Name?</span></span>  
  
     <span data-ttu-id="1bc5a-342">每个复选框旁边都会显示一个有效值。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-342">Each valid value appears next to a check box.</span></span>  
  
18. <span data-ttu-id="1bc5a-343">单击“全选”，再单击“查看报表”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-343">Click **Select All**, and then click **View Report**.</span></span>  
  
     <span data-ttu-id="1bc5a-344">报表将显示所有商店销售的所有子类别的数量。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-344">The report displays the quantity sold for all subcategories for all stores.</span></span>  
  
19. <span data-ttu-id="1bc5a-345">从下拉列表中，单击“全选”清除列表，再单击“Contoso Catalog Store”和“Contoso Asia Online Store”，然后单击“查看报表”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-345">From the drop-down list, click **Select All** to clear the list, click "Contoso Catalog Store" and "Contoso Asia Online Store", and then click **View Report**.</span></span>  
  
##  <a name="8-add-a-boolean-parameter-for-conditional-visibility"></a><a name="Boolean"></a><span data-ttu-id="1bc5a-346">8. 为条件可见性添加布尔参数</span><span class="sxs-lookup"><span data-stu-id="1bc5a-346">8. Add a Boolean Parameter for Conditional Visibility</span></span>  
  
#### <a name="to-add-a-boolean-parameter"></a><span data-ttu-id="1bc5a-347">添加布尔参数</span><span class="sxs-lookup"><span data-stu-id="1bc5a-347">To add a boolean parameter</span></span>  
  
1.  <span data-ttu-id="1bc5a-348">在设计图面上的“报表数据”窗格中，右键单击“参数”，再单击“添加参数”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-348">On the design surface, in the Report Data pane, right-click **Parameters**, and click **Add Parameter**.</span></span>  
  
2.  <span data-ttu-id="1bc5a-349">在“名称”中，键入“ShowSelections”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-349">In **Name**, type ShowSelections.</span></span>  
  
3.  <span data-ttu-id="1bc5a-350">在“提示符”，键入“Show selections?”\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="1bc5a-350">In **Prompt**, type Show selections?</span></span>  
  
4.  <span data-ttu-id="1bc5a-351">在 "**数据类型**" 的下拉列表中，单击 "**布尔值**"。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-351">In **Data type**, from the drop-down list, click **Boolean**.</span></span>  
  
5.  <span data-ttu-id="1bc5a-352">单击 **“默认值”**。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-352">Click **Default Values**.</span></span>  
  
6.  <span data-ttu-id="1bc5a-353">单击“指定值”，然后单击“添加”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-353">Click **Specify value**, and then click **Add**.</span></span>  
  
7.  <span data-ttu-id="1bc5a-354">在“值”中，键入“False”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-354">In **Value**, type **False**.</span></span>  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="to-set-visibility-based-on-a-boolean-parameter"></a><span data-ttu-id="1bc5a-355">基于布尔参数设置可见性</span><span class="sxs-lookup"><span data-stu-id="1bc5a-355">To set visibility based on a boolean parameter</span></span>  
  
1.  <span data-ttu-id="1bc5a-356">在设计图面上，右键单击页脚中用于显示参数值的文本框，然后单击“文本框属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-356">On the design surface, right-click the text box in the page footer that displays the parameter values, and then click **Text Box Properties**.</span></span>  
  
2.  <span data-ttu-id="1bc5a-357">单击 **“可见性”** 。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-357">Click **Visibility**.</span></span>  
  
3.  <span data-ttu-id="1bc5a-358">选择选项“基于表达式显示或隐藏”\*\*\*\*，然后单击表达式按钮“Fx”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-358">Select the option **Show or hide based on an expression**, and then click the expression button **Fx**.</span></span>  
  
4.  <span data-ttu-id="1bc5a-359">键入以下表达式： `=Not Parameters!ShowSelections.Value`</span><span class="sxs-lookup"><span data-stu-id="1bc5a-359">Type the following expression: `=Not Parameters!ShowSelections.Value`</span></span>  
  
     <span data-ttu-id="1bc5a-360">文本框的“可见性”选项由属性 Hidden 控制。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-360">The text box Visibility option is controlled by the property Hidden.</span></span> <span data-ttu-id="1bc5a-361">应用 `Not` 运算符，以便在选择参数时，Hidden 属性为 false 并显示文本框。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-361">Apply the `Not` operator so that when the parameter is selected, the Hidden property is false, and the text box will be displayed.</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  <span data-ttu-id="1bc5a-362">预览报表。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-362">Preview the report.</span></span>  
  
     <span data-ttu-id="1bc5a-363">显示参数选项的文本框未出现。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-363">The text box that displays the parameter choices does not appear.</span></span>  
  
8.  <span data-ttu-id="1bc5a-364">在报表查看器工具栏中的 "**显示选定**项" 旁边，单击 `True` 。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-364">In the report viewer toolbar, next to **Show selections**, click `True`.</span></span>  
  
9. <span data-ttu-id="1bc5a-365">预览报表。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-365">Preview the report.</span></span>  
  
 <span data-ttu-id="1bc5a-366">页脚中的文本框将显示所选的所有商店名称。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-366">The text box in the page footer displays all the store names that you selected.</span></span>  
  
##  <a name="9-add-a-report-title"></a><a name="Title"></a><span data-ttu-id="1bc5a-367">9. 添加报表标题</span><span class="sxs-lookup"><span data-stu-id="1bc5a-367">9. Add a Report Title</span></span>  
  
#### <a name="to-add-a-report-title"></a><span data-ttu-id="1bc5a-368">添加报表标题</span><span class="sxs-lookup"><span data-stu-id="1bc5a-368">To add a report title</span></span>  
  
1.  <span data-ttu-id="1bc5a-369">在设计图面上，单击“单击以添加标题”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-369">On the design surface, click **Click to add title**.</span></span>  
  
2.  <span data-ttu-id="1bc5a-370">键入 Parameterized Product Sales，然后在文本框外部单击。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-370">Type Parameterized Product Sales, and then click outside the text box.</span></span>  
  
##  <a name="10-save-the-report"></a><a name="Save"></a><span data-ttu-id="1bc5a-371">10. 保存报表</span><span class="sxs-lookup"><span data-stu-id="1bc5a-371">10. Save the Report</span></span>  
  
#### <a name="to-save-the-report-on-a-report-server"></a><span data-ttu-id="1bc5a-372">将报表保存到报表服务器</span><span class="sxs-lookup"><span data-stu-id="1bc5a-372">To save the report on a report server</span></span>  
  
1.  <span data-ttu-id="1bc5a-373">从 **“报表生成器”** 按钮，单击 **“另存为”**。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-373">From the **Report Builder** button, click **Save As**.</span></span>  
  
2.  <span data-ttu-id="1bc5a-374">单击 **“最近使用的站点和服务器”**。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-374">Click **Recent Sites and Servers**.</span></span>  
  
3.  <span data-ttu-id="1bc5a-375">选择或键入您拥有保存报表权限的报表服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-375">Select or type the name of the report server where you have permission to save reports.</span></span>  
  
     <span data-ttu-id="1bc5a-376">此时将显示“正在连接到报表服务器”消息\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-376">The message **Connecting to report server appears**.</span></span> <span data-ttu-id="1bc5a-377">当连接完成时，您将看到报表服务器管理员指定为报表默认位置的报表文件夹的内容。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-377">When the connection is complete, you see the contents of the report folder that the report server administrator specified as the default location for reports.</span></span>  
  
4.  <span data-ttu-id="1bc5a-378">在“名称”中，用 Parameterized Sales Report 替换默认名称\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-378">In **Name**, replace the default name with Parameterized Sales Report.</span></span>  
  
5.  <span data-ttu-id="1bc5a-379">单击“ **保存**”。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-379">Click **Save**.</span></span>  
  
 <span data-ttu-id="1bc5a-380">报表即已保存至报表服务器。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-380">The report is saved to the report server.</span></span> <span data-ttu-id="1bc5a-381">您连接的报表服务器将显示在窗口底部的状态栏中。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-381">The report server that you are connected to appears in the status bar at the bottom of the window.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="1bc5a-382">后续步骤</span><span class="sxs-lookup"><span data-stu-id="1bc5a-382">Next Steps</span></span>  
 <span data-ttu-id="1bc5a-383">到此为止，我们结束了有关如何向报表添加参数的演练。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-383">This concludes the walkthrough for how to add a parameter to your report.</span></span> <span data-ttu-id="1bc5a-384">要了解有关参数的详细信息，请参阅[报表参数（报表生成器和报表设计器）](report-design/report-parameters-report-builder-and-report-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="1bc5a-384">To learn more about parameters, see [Report Parameters &#40;Report Builder and Report Designer&#41;](report-design/report-parameters-report-builder-and-report-designer.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bc5a-385">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1bc5a-385">See Also</span></span>  
 <span data-ttu-id="1bc5a-386">[教程 &#40;报表生成器&#41;](report-builder-tutorials.md) </span><span class="sxs-lookup"><span data-stu-id="1bc5a-386">[Tutorials &#40;Report Builder&#41;](report-builder-tutorials.md) </span></span>  
 [<span data-ttu-id="1bc5a-387">SQL Server 2014 中的报表生成器</span><span class="sxs-lookup"><span data-stu-id="1bc5a-387">Report Builder in SQL Server 2014</span></span>](report-builder/report-builder-in-sql-server-2016.md)  
  
  
