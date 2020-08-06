---
title: 教程：向报表添加饼图（报表生成器）| Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: eaadf7bf-c312-428a-b214-0a1fbf959c3f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 318370b185dcd75a8c3c54be49c47756bad5f3c9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691549"
---
# <a name="tutorial-add-a-pie-chart-to-your-report-report-builder"></a><span data-ttu-id="f40b7-102">教程：向报表添加饼图（报表生成器）</span><span class="sxs-lookup"><span data-stu-id="f40b7-102">Tutorial: Add a Pie Chart to Your Report (Report Builder)</span></span>
  <span data-ttu-id="f40b7-103">饼图和圆环图将数据显示为整体的一定比例。</span><span class="sxs-lookup"><span data-stu-id="f40b7-103">Pie charts and doughnut charts display data as a proportion of the whole.</span></span> <span data-ttu-id="f40b7-104">饼图常用于在各组之间进行比较。</span><span class="sxs-lookup"><span data-stu-id="f40b7-104">Pie charts are most commonly used to make comparisons between groups.</span></span> <span data-ttu-id="f40b7-105">饼图和圆环图与棱锥图和漏斗图一起构成了一组称为形状图的图表。</span><span class="sxs-lookup"><span data-stu-id="f40b7-105">Pie and doughnut charts, along with pyramid and funnel charts, constitute a group of charts known as shape charts.</span></span> <span data-ttu-id="f40b7-106">形状图没有轴。</span><span class="sxs-lookup"><span data-stu-id="f40b7-106">Shape charts have no axes.</span></span> <span data-ttu-id="f40b7-107">在形状图上放置某数值字段后，该图表将计算每个值相对总计的百分比。</span><span class="sxs-lookup"><span data-stu-id="f40b7-107">When a numeric field is dropped on a shape chart, the chart calculates the percentage of each value to the total.</span></span>  
  
 <span data-ttu-id="f40b7-108">如果饼图上有太多数据点，这些数据点就可能挤在一起，这会降低图表的可读性。</span><span class="sxs-lookup"><span data-stu-id="f40b7-108">If there are too many data points on a pie chart, your data point labels might be too crowded to read.</span></span> <span data-ttu-id="f40b7-109">在此情况下，应考虑使用折线图。</span><span class="sxs-lookup"><span data-stu-id="f40b7-109">In that case, consider using a line chart.</span></span> <span data-ttu-id="f40b7-110">仅在已经将数据聚合到少量数据点之后，才能考虑使用饼图。</span><span class="sxs-lookup"><span data-stu-id="f40b7-110">Consider using pie charts only after you have aggregated your data into a few data points.</span></span>  
  
 <span data-ttu-id="f40b7-111">下图显示了将创建的饼图。</span><span class="sxs-lookup"><span data-stu-id="f40b7-111">The following illustration shows the pie chart you will create.</span></span>  
  
 <span data-ttu-id="f40b7-112">![rs_TutorialPieChartConcave](../../2014/tutorials/media/rs-tutorialpiechartconcave.gif "rs_TutorialPieChartConcave")</span><span class="sxs-lookup"><span data-stu-id="f40b7-112">![rs_TutorialPieChartConcave](../../2014/tutorials/media/rs-tutorialpiechartconcave.gif "rs_TutorialPieChartConcave")</span></span>  
  
##  <a name="what-you-will-learn"></a><a name="BackToTop"></a><span data-ttu-id="f40b7-113">你将学习的内容</span><span class="sxs-lookup"><span data-stu-id="f40b7-113">What You Will Learn</span></span>  
 <span data-ttu-id="f40b7-114">在本教程中，您将学习如何执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="f40b7-114">In this tutorial, you will learn how to:</span></span>  
  
1.  [<span data-ttu-id="f40b7-115">使用图表向导创建饼图</span><span class="sxs-lookup"><span data-stu-id="f40b7-115">Create a Pie Chart from the Chart Wizard</span></span>](#Chart)  
  
2.  [<span data-ttu-id="f40b7-116">选择图表类型</span><span class="sxs-lookup"><span data-stu-id="f40b7-116">Choose the Chart Type</span></span>](#ChartType)  
  
3.  [<span data-ttu-id="f40b7-117">在每个切片中显示百分比</span><span class="sxs-lookup"><span data-stu-id="f40b7-117">Display Percentages in Each Slice</span></span>](#Percentages)  
  
4.  [<span data-ttu-id="f40b7-118">将多个小型切片合并为一个切片</span><span class="sxs-lookup"><span data-stu-id="f40b7-118">Combine Small Slices into One Slice</span></span>](#CombineSlices)  
  
5.  [<span data-ttu-id="f40b7-119">自定义绘图效果</span><span class="sxs-lookup"><span data-stu-id="f40b7-119">Customize the Drawing Effect</span></span>](#DrawingEffect)  
  
6.  [<span data-ttu-id="f40b7-120">添加报表标题</span><span class="sxs-lookup"><span data-stu-id="f40b7-120">Add a Report Title</span></span>](#Title)  
  
7.  [<span data-ttu-id="f40b7-121">保存报表</span><span class="sxs-lookup"><span data-stu-id="f40b7-121">Save the Report</span></span>](#Save)  
  
> [!NOTE]  
>  <span data-ttu-id="f40b7-122">在本教程中，将向导的多个步骤合并为两个过程。</span><span class="sxs-lookup"><span data-stu-id="f40b7-122">In this tutorial, the steps for the wizard are consolidated into two procedures.</span></span> <span data-ttu-id="f40b7-123">有关如何浏览到报表服务器、添加数据源和添加数据集的分步说明，请参阅这一系列教程中的第一个教程：[教程：创建基本表报表（报表生成器）](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="f40b7-123">For step-by-step instructions about how to browse to a report server, add a data source, and add a dataset, see the first tutorial in this series: [Tutorial: Creating a Basic Table Report &#40;Report Builder&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md).</span></span>  
  
 <span data-ttu-id="f40b7-124">本教程的预计学时：10 分钟</span><span class="sxs-lookup"><span data-stu-id="f40b7-124">Estimated time to complete this tutorial: 10 minutes</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f40b7-125">要求</span><span class="sxs-lookup"><span data-stu-id="f40b7-125">Requirements</span></span>  
 <span data-ttu-id="f40b7-126">有关要求的详细信息，请参阅[教程先决条件（报表生成器）](../reporting-services/report-builder-tutorials.md)。</span><span class="sxs-lookup"><span data-stu-id="f40b7-126">For more information about requirements, see [Prerequisites for Tutorials &#40;Report Builder&#41;](../reporting-services/report-builder-tutorials.md).</span></span>  
  
##  <a name="1-create-a-pie-chart-from-the-chart-wizard"></a><a name="Chart"></a><span data-ttu-id="f40b7-127">1. 使用图表向导创建饼图</span><span class="sxs-lookup"><span data-stu-id="f40b7-127">1. Create a Pie Chart from the Chart Wizard</span></span>  
 <span data-ttu-id="f40b7-128">从“入门”对话框中使用图表向导创建嵌入数据集，选择共享数据源，并创建饼图。</span><span class="sxs-lookup"><span data-stu-id="f40b7-128">From the Getting Started dialog box, use the Chart Wizard to create an embedded dataset, choose a shared data source, and create a pie chart.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f40b7-129">在本教程中，由于查询包含了数据值，因此它不需要外部数据源。</span><span class="sxs-lookup"><span data-stu-id="f40b7-129">In this tutorial, the query contains the data values, so that it does not need an external data source.</span></span> <span data-ttu-id="f40b7-130">这样，查询就会非常长。</span><span class="sxs-lookup"><span data-stu-id="f40b7-130">This makes the query quite long.</span></span> <span data-ttu-id="f40b7-131">在业务环境中，查询不会包含数据。</span><span class="sxs-lookup"><span data-stu-id="f40b7-131">In a business environment, a query would not contain the data.</span></span> <span data-ttu-id="f40b7-132">本教程中的查询仅供学习使用。</span><span class="sxs-lookup"><span data-stu-id="f40b7-132">This is for learning purposes only.</span></span>  
  
#### <a name="to-create-a-new-chart-report"></a><span data-ttu-id="f40b7-133">创建新的图表报表</span><span class="sxs-lookup"><span data-stu-id="f40b7-133">To create a new chart report</span></span>  
  
1.  <span data-ttu-id="f40b7-134">单击 **“开始”**，依次指向 **“程序”**、 **Microsoft SQL Server 2012 Report Builder**，再单击 **“报表生成器”**。</span><span class="sxs-lookup"><span data-stu-id="f40b7-134">Click **Start**, point to **Programs**, point to **Microsoft SQL Server 2012 Report Builder**, and then click **Report Builder**.</span></span>  
  
     <span data-ttu-id="f40b7-135">此时将显示“入门”对话框。</span><span class="sxs-lookup"><span data-stu-id="f40b7-135">The Getting Started dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f40b7-136">如果未显示 "入门" 对话框，请在 "报表生成器" 按钮中单击 "**新建**"。</span><span class="sxs-lookup"><span data-stu-id="f40b7-136">If the Getting Started dialog box does not appear, from the Report Builder button, click **New**.</span></span>  
  
2.  <span data-ttu-id="f40b7-137">在左窗格中，确认已选中 **“新建报表”** 。</span><span class="sxs-lookup"><span data-stu-id="f40b7-137">In the left pane, verify that **New Report** is selected.</span></span>  
  
3.  <span data-ttu-id="f40b7-138">在右窗格中，单击“图表向导”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f40b7-138">In the right pane, click **Chart Wizard**.</span></span>  
  
4.  <span data-ttu-id="f40b7-139">在 "**选择数据集**" 页上，单击 "**创建数据集**"，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="f40b7-139">On the **Choose a dataset** page, click **Create a dataset**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="f40b7-140">在“选择数据源的连接”页中，选择现有数据源或浏览到报表服务器并选择一个数据源，然后单击“下一步”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f40b7-140">On the **Choose a connection to a data source** page, select an existing data source or browse to the report server and select a data source, and then click **Next**.</span></span> <span data-ttu-id="f40b7-141">您可能需要输入用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="f40b7-141">You may need to enter a user name and password.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f40b7-142">只要您具有足够的权限，则选择哪一个数据源并不重要。</span><span class="sxs-lookup"><span data-stu-id="f40b7-142">The data source you choose is unimportant, as long as you have adequate permissions.</span></span> <span data-ttu-id="f40b7-143">您将不会从数据源中获取数据。</span><span class="sxs-lookup"><span data-stu-id="f40b7-143">You will not be getting data from the data source.</span></span> <span data-ttu-id="f40b7-144">有关详细信息，请参阅[获取数据连接的备选方式（报表生成器）](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="f40b7-144">For more information, see [Alternative Ways to Get a Data Connection &#40;Report Builder&#41;](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md).</span></span>  
  
6.  <span data-ttu-id="f40b7-145">在 "**设计查询**" 页上，单击 "**编辑为文本**"。</span><span class="sxs-lookup"><span data-stu-id="f40b7-145">On the **Design a Query** page, click **Edit as Text**.</span></span>  
  
7.  <span data-ttu-id="f40b7-146">将以下查询粘贴到查询窗格中：</span><span class="sxs-lookup"><span data-stu-id="f40b7-146">Paste the following query into the query pane:</span></span>  
  
    ```  
    SELECT 'Advanced Digital Camera' AS Product, CAST(254995.21 AS money) AS Sales  
    UNION SELECT 'Slim Digital Camera' AS Product, CAST(164499.04 AS money) AS Sales  
    UNION SELECT 'SLR Digital Camera' AS Product, CAST(782176.79 AS money) AS Sales  
    UNION SELECT 'Lens Adapter' AS Product, CAST(36333.08 AS money) AS Sales  
    UNION SELECT 'Macro Zoom Lens' AS Product, CAST(40199.3 AS money) AS Sales  
    UNION SELECT 'USB Cable' AS Product, CAST(53245.5 AS money) AS Sales  
    UNION SELECT 'Independent Filmmaker Camcorder' AS Product, CAST(452288.0 AS money) AS Sales  
    UNION SELECT 'Full Frame Digital Camera' AS Product, CAST(247250.85 AS money) AS Sales  
    ```  
  
8.  <span data-ttu-id="f40b7-147">（可选）单击“运行”按钮 (!)，查看要用于图表的数据\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f40b7-147">(Optional) Click the Run button (**!**) to see the data your chart will be based on.</span></span>  
  
9. <span data-ttu-id="f40b7-148">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="f40b7-148">Click **Next**.</span></span>  
  
##  <a name="2-choose-the-chart-type"></a><a name="ChartType"></a><span data-ttu-id="f40b7-149">2. 选择图表类型</span><span class="sxs-lookup"><span data-stu-id="f40b7-149">2. Choose the Chart Type</span></span>  
 <span data-ttu-id="f40b7-150">可以从各种预定义的图表类型中进行选择。</span><span class="sxs-lookup"><span data-stu-id="f40b7-150">You can choose from a variety of predefined chart types.</span></span>  
  
#### <a name="to-add-a-pie-chart"></a><span data-ttu-id="f40b7-151">添加饼图</span><span class="sxs-lookup"><span data-stu-id="f40b7-151">To add a pie chart</span></span>  
  
1.  <span data-ttu-id="f40b7-152">在 "**选择图表类型**" 页上，单击 "**饼图**"，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="f40b7-152">On the **Choose a chart type** page, click **Pie**, and then click **Next**.</span></span> <span data-ttu-id="f40b7-153">将打开“排列图表字段”\*\*\*\* 页。</span><span class="sxs-lookup"><span data-stu-id="f40b7-153">The **Arrange chart fields** page opens.</span></span>  
  
     <span data-ttu-id="f40b7-154">在“排列图表字段”\*\*\*\* 页上，将“Product”字段拖到“类别”\*\*\*\* 窗格中。</span><span class="sxs-lookup"><span data-stu-id="f40b7-154">On the **Arrange chart fields** page, drag the Product field to the **Categories** pane.</span></span> <span data-ttu-id="f40b7-155">类别定义了饼图上的切片数。</span><span class="sxs-lookup"><span data-stu-id="f40b7-155">Categories define the number of slices in the pie chart.</span></span> <span data-ttu-id="f40b7-156">在本示例中，将有 8 个切片，每个产品对应一个切片。</span><span class="sxs-lookup"><span data-stu-id="f40b7-156">In this example, there will be eight slices, one for each product.</span></span>  
  
2.  <span data-ttu-id="f40b7-157">将“Sales”字段拖到“值”\*\*\*\* 窗格中。</span><span class="sxs-lookup"><span data-stu-id="f40b7-157">Drag the Sales field to the **Values** pane.</span></span> <span data-ttu-id="f40b7-158">Sales 表示子类别的销售量。</span><span class="sxs-lookup"><span data-stu-id="f40b7-158">Sales represents the sales amount for the subcategory.</span></span> <span data-ttu-id="f40b7-159">“值”\*\*\*\* 窗格显示 `[Sum(Sales)]`，因为该图表显示的是每个产品的销售总额。</span><span class="sxs-lookup"><span data-stu-id="f40b7-159">The **Values** pane displays `[Sum(Sales)]` because the chart displays the aggregate for each product.</span></span>  
  
3.  <span data-ttu-id="f40b7-160">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="f40b7-160">Click **Next**.</span></span>  
  
4.  <span data-ttu-id="f40b7-161">在 "**选择样式**" 页上的 "样式" 窗格中，选择样式。</span><span class="sxs-lookup"><span data-stu-id="f40b7-161">On the **Choose a style** page, in the Styles pane, select a style.</span></span>  
  
     <span data-ttu-id="f40b7-162">样式指定字形、颜色集和边框样式。</span><span class="sxs-lookup"><span data-stu-id="f40b7-162">A style specifies a font style, a set of colors, and a border style.</span></span> <span data-ttu-id="f40b7-163">选择样式时，“预览”窗格将显示具有该样式的图表的示例。</span><span class="sxs-lookup"><span data-stu-id="f40b7-163">When you select a style, the Preview pane displays a sample of the chart with that style.</span></span>  
  
5.  <span data-ttu-id="f40b7-164">单击“完成”。</span><span class="sxs-lookup"><span data-stu-id="f40b7-164">Click **Finish**.</span></span>  
  
     <span data-ttu-id="f40b7-165">图表将添加到设计图面中。</span><span class="sxs-lookup"><span data-stu-id="f40b7-165">The chart is added to the design surface.</span></span>  
  
6.  <span data-ttu-id="f40b7-166">单击图表以显示图表控点。</span><span class="sxs-lookup"><span data-stu-id="f40b7-166">Click the chart to display the chart handles.</span></span> <span data-ttu-id="f40b7-167">拖动该图表的右下角以扩大该图表。</span><span class="sxs-lookup"><span data-stu-id="f40b7-167">Drag the bottom-right corner of the chart to increase the size of the chart.</span></span> <span data-ttu-id="f40b7-168">请注意，报表设计图面的大小将增大以容纳图表。</span><span class="sxs-lookup"><span data-stu-id="f40b7-168">Note that the report design surface increases in size to accommodate the chart size.</span></span>  
  
7.  <span data-ttu-id="f40b7-169">单击 **“运行”** 以预览报表。</span><span class="sxs-lookup"><span data-stu-id="f40b7-169">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="f40b7-170">报表会显示具有 8 个切片的饼图，每个产品对应一个切片。</span><span class="sxs-lookup"><span data-stu-id="f40b7-170">The report displays the pie chart with eight slices, one for each product.</span></span> <span data-ttu-id="f40b7-171">每个切片的大小表示该产品在 2004 年的销售额。</span><span class="sxs-lookup"><span data-stu-id="f40b7-171">The size of each slice represents the sales for that product.</span></span> <span data-ttu-id="f40b7-172">其中有三个切片非常薄。</span><span class="sxs-lookup"><span data-stu-id="f40b7-172">Three of the slices are quite thin.</span></span>  
  
##  <a name="3-display-percentages-in-each-slice"></a><a name="Percentages"></a><span data-ttu-id="f40b7-173">3. 在每个切片中显示百分比</span><span class="sxs-lookup"><span data-stu-id="f40b7-173">3. Display Percentages in Each Slice</span></span>  
 <span data-ttu-id="f40b7-174">在饼图的每个切片上，可以显示此切片占整个饼图的百分比。</span><span class="sxs-lookup"><span data-stu-id="f40b7-174">On each slice of the pie, you can display a percentage for this slice compared to the whole pie.</span></span>  
  
#### <a name="to-display-percentages-in-each-slice-of-the-pie-chart"></a><span data-ttu-id="f40b7-175">在饼图的每个切片中显示百分比</span><span class="sxs-lookup"><span data-stu-id="f40b7-175">To display percentages in each slice of the pie chart</span></span>  
  
1.  <span data-ttu-id="f40b7-176">切换到报表设计视图。</span><span class="sxs-lookup"><span data-stu-id="f40b7-176">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="f40b7-177">右键单击饼图，然后单击“显示数据标签”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f40b7-177">Right-click the pie chart and click **Show Data Labels**.</span></span> <span data-ttu-id="f40b7-178">数据标签会显示在图表上。</span><span class="sxs-lookup"><span data-stu-id="f40b7-178">The data labels appear on the chart.</span></span>  
  
3.  <span data-ttu-id="f40b7-179">右键单击标签，然后单击 "**序列标签属性**"。</span><span class="sxs-lookup"><span data-stu-id="f40b7-179">Right-click a label, and then click **Series Label Properties**.</span></span>  
  
4.  <span data-ttu-id="f40b7-180">在 "标签数据" 的下拉框中，选择 " **#PERCENT**"。</span><span class="sxs-lookup"><span data-stu-id="f40b7-180">In Label data, from the drop-down box, select **#PERCENT**.</span></span>  
  
     <span data-ttu-id="f40b7-181">若要将值显示为百分比，则 UseValueAsLabel 属性必须为 false。</span><span class="sxs-lookup"><span data-stu-id="f40b7-181">To display values as percentages, the UseValueAsLabel property must be false.</span></span> <span data-ttu-id="f40b7-182">如果系统提示设置此值，请在“确认操作”\*\*\*\* 对话框中单击“是”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f40b7-182">If you are prompted to set this value in the **Confirm Action** dialog, click **Yes**.</span></span>  
  
5.  <span data-ttu-id="f40b7-183"> (可选) 若要指定标签显示的小数位数，请键入， `#PERCENT{Pn}` 其中*n*是要显示的小数位数。</span><span class="sxs-lookup"><span data-stu-id="f40b7-183">(Optional) To specify how many decimal places the label shows, type `#PERCENT{Pn}` where *n* is the number of decimal places to display.</span></span> <span data-ttu-id="f40b7-184">例如，若要不显示小数位数，请键入 `#PERCENT{P0}` 。</span><span class="sxs-lookup"><span data-stu-id="f40b7-184">For example, to display no decimal places, type `#PERCENT{P0}`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f40b7-185">设置百分比格式时，“序列标签属性”\*\*\*\* 对话框中的“数字格式”\*\*\*\* 不起作用。</span><span class="sxs-lookup"><span data-stu-id="f40b7-185">**Number Format** in the **Series Label Properties** dialog box has no effect when you format percentages.</span></span> <span data-ttu-id="f40b7-186">它将标签的格式设置为百分比，但不会计算每一切片占饼图的百分比。</span><span class="sxs-lookup"><span data-stu-id="f40b7-186">This formats the labels as percentages, but does not calculate the percentage of the pie that each slice represents.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  <span data-ttu-id="f40b7-187">单击 **“运行”** 以预览报表。</span><span class="sxs-lookup"><span data-stu-id="f40b7-187">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="f40b7-188">报表会显示每个饼图切片占总体的百分比。</span><span class="sxs-lookup"><span data-stu-id="f40b7-188">The report displays the percentage of the whole for each pie slice.</span></span>  
  
##  <a name="4-combine-small-slices-into-one-slice"></a><a name="CombineSlices"></a><span data-ttu-id="f40b7-189">4. 将小型切片合并为一个切片</span><span class="sxs-lookup"><span data-stu-id="f40b7-189">4. Combine Small Slices into One Slice</span></span>  
 <span data-ttu-id="f40b7-190">在饼图所包含的切片中，有三个切片非常小。</span><span class="sxs-lookup"><span data-stu-id="f40b7-190">Three of the slices in the pie are quite small.</span></span> <span data-ttu-id="f40b7-191">可以将多个小型切片合并为一个表示所有这些小型切片的大型切片。</span><span class="sxs-lookup"><span data-stu-id="f40b7-191">You can combine multiple small slices into one larger slice that represents all of them.</span></span>  
  
#### <a name="to-combine-any-slices-on-the-pie-chart-smaller-than-5-percent-into-one-slice"></a><span data-ttu-id="f40b7-192">将饼图上所有小于 5% 的切片组合为一个切片</span><span class="sxs-lookup"><span data-stu-id="f40b7-192">To combine any slices on the pie chart smaller than 5 percent into one slice</span></span>  
  
1.  <span data-ttu-id="f40b7-193">切换到报表设计视图。</span><span class="sxs-lookup"><span data-stu-id="f40b7-193">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="f40b7-194">在 "**视图**" 选项卡上的 "**显示/隐藏**" 组中，选择 "**属性**"。</span><span class="sxs-lookup"><span data-stu-id="f40b7-194">On the **View** tab, in the **Show/Hide** group, select **Properties**.</span></span>  
  
3.  <span data-ttu-id="f40b7-195">在设计图面上，单击饼图的任一切片。</span><span class="sxs-lookup"><span data-stu-id="f40b7-195">On the design surface, click on any slice of the pie chart.</span></span> <span data-ttu-id="f40b7-196">序列的属性将显示在“属性”窗格中。</span><span class="sxs-lookup"><span data-stu-id="f40b7-196">The properties for the series are displayed in the Properties pane.</span></span>  
  
4.  <span data-ttu-id="f40b7-197">在 **“常规”** 部分，展开 **CustomAttributes** 节点。</span><span class="sxs-lookup"><span data-stu-id="f40b7-197">In the **General** section, expand the **CustomAttributes** node.</span></span>  
  
5.  <span data-ttu-id="f40b7-198">将“CollectedStyle”\*\*\*\* 属性设置为“SingleSlice”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f40b7-198">Set the **CollectedStyle** property to **SingleSlice**.</span></span>  
  
6.  <span data-ttu-id="f40b7-199">确保将“CollectedThreshold”\*\*\*\* 属性设置为“5”。</span><span class="sxs-lookup"><span data-stu-id="f40b7-199">Verify that the **CollectedThreshold** property is set to 5.</span></span>  
  
7.  <span data-ttu-id="f40b7-200">确保将“CollectedThresholdUsePercent”\*\*\*\* 属性设置为“True”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f40b7-200">Verify that the **CollectedThresholdUsePercent** property is set to **True**.</span></span>  
  
8.  <span data-ttu-id="f40b7-201">在功能区上的 "**主页**" 选项卡上，单击 "**运行**" 以预览报表。</span><span class="sxs-lookup"><span data-stu-id="f40b7-201">On the Ribbon, on the **Home** tab, click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="f40b7-202">现在，在图例中已存在类别“其他”。</span><span class="sxs-lookup"><span data-stu-id="f40b7-202">In the legend, the category "Other" now exists.</span></span> <span data-ttu-id="f40b7-203">新饼图切片将所有小于 5% 的切片组合成一个占整个饼图 6% 的切片。</span><span class="sxs-lookup"><span data-stu-id="f40b7-203">The new pie slice combines all the slices that were under 5% into one slice that is 6% of the whole pie.</span></span>  
  
##  <a name="5-customize-the-drawing-effect"></a><a name="DrawingEffect"></a><span data-ttu-id="f40b7-204">5. 自定义绘图效果</span><span class="sxs-lookup"><span data-stu-id="f40b7-204">5. Customize the Drawing Effect</span></span>  
 <span data-ttu-id="f40b7-205">在图表向导中，饼图的默认样式为“海蓝色”，这将呈现凹陷绘图效果。</span><span class="sxs-lookup"><span data-stu-id="f40b7-205">In the Chart Wizard, the default style for a pie chart is Ocean, which features a Concave drawing effect.</span></span> <span data-ttu-id="f40b7-206">可以在运行改向导后更改此样式。</span><span class="sxs-lookup"><span data-stu-id="f40b7-206">You can change that after you run the wizard.</span></span>  
  
#### <a name="to-add-a-drawing-effect-to-the-pie-chart"></a><span data-ttu-id="f40b7-207">向饼图添加绘制效果</span><span class="sxs-lookup"><span data-stu-id="f40b7-207">To add a drawing effect to the pie chart</span></span>  
  
1.  <span data-ttu-id="f40b7-208">切换到报表设计视图。</span><span class="sxs-lookup"><span data-stu-id="f40b7-208">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="f40b7-209">如果尚未打开 "属性" 窗格，请在 "**视图**" 选项卡上选择 "**属性**"。</span><span class="sxs-lookup"><span data-stu-id="f40b7-209">If the Properties pane is not already opened, on the **View** tab, select **Properties**.</span></span>  
  
3.  <span data-ttu-id="f40b7-210">双击饼图本身。</span><span class="sxs-lookup"><span data-stu-id="f40b7-210">Double-click the pie chart itself.</span></span> <span data-ttu-id="f40b7-211">饼图的序列属性将会显示在“属性”窗格中。</span><span class="sxs-lookup"><span data-stu-id="f40b7-211">The series properties for the pie chart are shown in the Properties pane.</span></span>  
  
4.  <span data-ttu-id="f40b7-212">在“属性”窗格中，展开 **CustomAttributes** 节点。</span><span class="sxs-lookup"><span data-stu-id="f40b7-212">In the Properties pane, expand the **CustomAttributes** node.</span></span>  
  
5.  <span data-ttu-id="f40b7-213">将**PieDrawingStyle**设置为**SoftEdge**。</span><span class="sxs-lookup"><span data-stu-id="f40b7-213">Set the **PieDrawingStyle** to **SoftEdge**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f40b7-214">绘图效果和三维效果是相互排斥的选项。</span><span class="sxs-lookup"><span data-stu-id="f40b7-214">Drawing effects and three-dimensional effects are exclusive options.</span></span> <span data-ttu-id="f40b7-215">如果图表应用了三维效果，则 "属性" 窗格上的 " **PieDrawingStyle** " 不可用。</span><span class="sxs-lookup"><span data-stu-id="f40b7-215">If a chart has three-dimensional effects applied, **PieDrawingStyle** is not available on the Properties pane.</span></span>  
  
6.  <span data-ttu-id="f40b7-216">单击 **“运行”** 以预览报表。</span><span class="sxs-lookup"><span data-stu-id="f40b7-216">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="f40b7-217">下图显示了具有软边效果的饼图。</span><span class="sxs-lookup"><span data-stu-id="f40b7-217">The following illustration shows the pie chart with the soft edge effect.</span></span>  
  
 <span data-ttu-id="f40b7-218">![rs_TutorialPieChartSoftEdge](../../2014/tutorials/media/rs-tutorialpiechartsoftedge.gif "rs_TutorialPieChartSoftEdge")</span><span class="sxs-lookup"><span data-stu-id="f40b7-218">![rs_TutorialPieChartSoftEdge](../../2014/tutorials/media/rs-tutorialpiechartsoftedge.gif "rs_TutorialPieChartSoftEdge")</span></span>  
  
##  <a name="6-add-a-report-title"></a><a name="Title"></a><span data-ttu-id="f40b7-219">6. 添加报表标题</span><span class="sxs-lookup"><span data-stu-id="f40b7-219">6. Add a Report Title</span></span>  
  
#### <a name="to-add-a-report-title"></a><span data-ttu-id="f40b7-220">添加报表标题</span><span class="sxs-lookup"><span data-stu-id="f40b7-220">To add a report title</span></span>  
  
1.  <span data-ttu-id="f40b7-221">在设计图面上，单击“单击以添加标题”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f40b7-221">On the design surface, click **Click to add title**.</span></span>  
  
2.  <span data-ttu-id="f40b7-222">键入 **Camera and Camcorder Sales**，按 Enter，然后键入 **As a Percentage of Total Sales**，如下所示：</span><span class="sxs-lookup"><span data-stu-id="f40b7-222">Type **Camera and Camcorder Sales**, press ENTER, and then type **As a Percentage of Total Sales**, so it looks like this:</span></span>  
  
     <span data-ttu-id="f40b7-223">**Camera and Camcorder Sales**</span><span class="sxs-lookup"><span data-stu-id="f40b7-223">**Camera and Camcorder Sales**</span></span>  
  
     <span data-ttu-id="f40b7-224">**As a Percentage of Total Sales**</span><span class="sxs-lookup"><span data-stu-id="f40b7-224">**As a Percentage of Total Sales**</span></span>  
  
3.  <span data-ttu-id="f40b7-225">选择 **"摄像机和摄像机销售**"，然后在功能区的 "**主页**" 选项卡的 "**字体**" 部分中单击 "**粗体**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="f40b7-225">Select **Camera and Camcorder Sales**, and click the **Bold** button from the **Font** section of the **Home** tab of the ribbon.</span></span>  
  
4.  <span data-ttu-id="f40b7-226">选择 "**按总销售额的百分比**"，然后在 "**主页**" 选项卡的 "**字体**" 部分中，将字号设置为**10**。</span><span class="sxs-lookup"><span data-stu-id="f40b7-226">Select **As a Percentage of Total Sales**, and in the **Font** section on the **Home** tab, set the font size to **10**.</span></span>  
  
5.  <span data-ttu-id="f40b7-227">（可选）您可能需要使“标题”文本框更高一些，以容纳两行文本。</span><span class="sxs-lookup"><span data-stu-id="f40b7-227">(Optional) You may need to make the Title text box taller to accommodate the two lines of text.</span></span>  
  
     <span data-ttu-id="f40b7-228">此标题将显示在报表的顶部。</span><span class="sxs-lookup"><span data-stu-id="f40b7-228">This title will appear at the top of the report.</span></span> <span data-ttu-id="f40b7-229">未定义页标头时，报表体顶部的项就等同于报表标头。</span><span class="sxs-lookup"><span data-stu-id="f40b7-229">When there is no page header defined, items at the top of the report body are the equivalent of a report header.</span></span>  
  
6.  <span data-ttu-id="f40b7-230">单击 **“运行”** 以预览报表。</span><span class="sxs-lookup"><span data-stu-id="f40b7-230">Click **Run** to preview the report.</span></span>  
  
##  <a name="7-save-the-report"></a><a name="Save"></a><span data-ttu-id="f40b7-231">7. 保存报表</span><span class="sxs-lookup"><span data-stu-id="f40b7-231">7. Save the Report</span></span>  
  
#### <a name="to-save-the-report"></a><span data-ttu-id="f40b7-232">保存报表</span><span class="sxs-lookup"><span data-stu-id="f40b7-232">To save the report</span></span>  
  
1.  <span data-ttu-id="f40b7-233">切换到报表设计视图。</span><span class="sxs-lookup"><span data-stu-id="f40b7-233">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="f40b7-234">从 “报表生成器” 按钮，单击 **“另存为”**。</span><span class="sxs-lookup"><span data-stu-id="f40b7-234">From the Report Builder button, click **Save As**.</span></span>  
  
3.  <span data-ttu-id="f40b7-235">在“名称”\*\*\*\* 中，键入“Sales Pie Chart”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f40b7-235">In **Name**, type **Sales Pie Chart**.</span></span>  
  
4.  <span data-ttu-id="f40b7-236">单击“ **保存**”。</span><span class="sxs-lookup"><span data-stu-id="f40b7-236">Click **Save**.</span></span>  
  
 <span data-ttu-id="f40b7-237">报表将保存在报表服务器上。</span><span class="sxs-lookup"><span data-stu-id="f40b7-237">Your report is saved on the report server.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="f40b7-238">后续步骤</span><span class="sxs-lookup"><span data-stu-id="f40b7-238">Next Steps</span></span>  
 <span data-ttu-id="f40b7-239">这样，您就成功完成了“向报表添加饼图”教程的学习。</span><span class="sxs-lookup"><span data-stu-id="f40b7-239">You have successfully completed the Adding a Pie Chart to Your Report tutorial.</span></span> <span data-ttu-id="f40b7-240">若要了解有关图表的详细信息，请参阅[图表（报表生成器和 SSRS）](report-design/charts-report-builder-and-ssrs.md)和[迷你图和数据条（报表生成器和 SSRS）](report-design/sparklines-and-data-bars-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="f40b7-240">To learn more about charts, see [Charts &#40;Report Builder and SSRS&#41;](report-design/charts-report-builder-and-ssrs.md) and [Sparklines and Data Bars &#40;Report Builder and SSRS&#41;](report-design/sparklines-and-data-bars-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f40b7-241">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f40b7-241">See Also</span></span>  
 <span data-ttu-id="f40b7-242">[教程 &#40;报表生成器&#41;](report-builder-tutorials.md) </span><span class="sxs-lookup"><span data-stu-id="f40b7-242">[Tutorials &#40;Report Builder&#41;](report-builder-tutorials.md) </span></span>  
 [<span data-ttu-id="f40b7-243">SQL Server 2014 中的报表生成器</span><span class="sxs-lookup"><span data-stu-id="f40b7-243">Report Builder in SQL Server 2014</span></span>](report-builder/report-builder-in-sql-server-2016.md)  
  
  
