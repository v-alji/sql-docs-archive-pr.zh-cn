---
title: 教程：向报表添加柱形图（报表生成器）| Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 63480059-b7b9-44b5-9d7f-91780db708b6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0ef3b3f2872c2f8181296bb05337ca18975ac2f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692233"
---
# <a name="tutorial-add-a-column-chart-to-your-report-report-builder"></a><span data-ttu-id="d0e23-102">教程：向报表添加柱形图（报表生成器）</span><span class="sxs-lookup"><span data-stu-id="d0e23-102">Tutorial: Add a Column Chart to Your Report (Report Builder)</span></span>
  <span data-ttu-id="d0e23-103">柱形图将序列显示为一组按类别分组的垂直图条。</span><span class="sxs-lookup"><span data-stu-id="d0e23-103">A column chart displays a series as a set of vertical bars that are grouped by category.</span></span> <span data-ttu-id="d0e23-104">柱形图可能在以下方面十分有用：</span><span class="sxs-lookup"><span data-stu-id="d0e23-104">A column chart can be useful to:</span></span>  
  
-   <span data-ttu-id="d0e23-105">显示一段时间内数据的更改。</span><span class="sxs-lookup"><span data-stu-id="d0e23-105">Show data changes over a period of time.</span></span>  
  
-   <span data-ttu-id="d0e23-106">比较多个序列的相对值。</span><span class="sxs-lookup"><span data-stu-id="d0e23-106">Compare the relative value of multiple series.</span></span>  
  
-   <span data-ttu-id="d0e23-107">显示移动平均线，以显示趋势。</span><span class="sxs-lookup"><span data-stu-id="d0e23-107">Display a moving average to show trends.</span></span>  
  
 <span data-ttu-id="d0e23-108">下图显示了将创建的带有移动平均线的柱形图。</span><span class="sxs-lookup"><span data-stu-id="d0e23-108">The following illustration shows the column chart you will create, with a moving average.</span></span>  
  
 <span data-ttu-id="d0e23-109">![rs_TutorialColChartFinished](../../2014/tutorials/media/rs-tutorialcolchartfinished.gif "rs_TutorialColChartFinished")</span><span class="sxs-lookup"><span data-stu-id="d0e23-109">![rs_TutorialColChartFinished](../../2014/tutorials/media/rs-tutorialcolchartfinished.gif "rs_TutorialColChartFinished")</span></span>  
  
##  <a name="what-you-will-learn"></a><a name="BackToTop"></a><span data-ttu-id="d0e23-110">你将学习的内容</span><span class="sxs-lookup"><span data-stu-id="d0e23-110">What You Will Learn</span></span>  
 <span data-ttu-id="d0e23-111">在本教程中，您将学习如何执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="d0e23-111">In this tutorial you will learn how to do the following:</span></span>  
  
1.  [<span data-ttu-id="d0e23-112">使用图表向导创建图表</span><span class="sxs-lookup"><span data-stu-id="d0e23-112">Create a Chart from the Chart Wizard</span></span>](#Chart)  
  
2.  [<span data-ttu-id="d0e23-113">选择图表类型</span><span class="sxs-lookup"><span data-stu-id="d0e23-113">Choose the Chart Type</span></span>](#ChartType)  
  
3.  [<span data-ttu-id="d0e23-114">设置水平轴的格式和标签</span><span class="sxs-lookup"><span data-stu-id="d0e23-114">Format and Label the Horizontal Axis</span></span>](#Horizontal)  
  
4.  [<span data-ttu-id="d0e23-115">移动图例</span><span class="sxs-lookup"><span data-stu-id="d0e23-115">Move the Legend</span></span>](#Legend)  
  
5.  [<span data-ttu-id="d0e23-116">设置图表的标题</span><span class="sxs-lookup"><span data-stu-id="d0e23-116">Title the Chart</span></span>](#ChartTitle)  
  
6.  [<span data-ttu-id="d0e23-117">设置垂直轴的格式和标签</span><span class="sxs-lookup"><span data-stu-id="d0e23-117">Format and Label the Vertical Axis</span></span>](#Vertical)  
  
7.  [<span data-ttu-id="d0e23-118">添加移动平均线</span><span class="sxs-lookup"><span data-stu-id="d0e23-118">Add a Moving Average</span></span>](#Average)  
  
8.  [<span data-ttu-id="d0e23-119">添加报表标题</span><span class="sxs-lookup"><span data-stu-id="d0e23-119">Add a Report Title</span></span>](#Title)  
  
9. [<span data-ttu-id="d0e23-120">保存报表</span><span class="sxs-lookup"><span data-stu-id="d0e23-120">Save the Report</span></span>](#Save)  
  
> [!NOTE]  
>  <span data-ttu-id="d0e23-121">在本教程中，将向导的多个步骤合并为一个过程。</span><span class="sxs-lookup"><span data-stu-id="d0e23-121">In this tutorial, the steps for the wizard are consolidated into one procedure.</span></span> <span data-ttu-id="d0e23-122">有关如何浏览到报表服务器、选择数据源和创建数据集的分步说明，请参阅本系列中的第一个教程：[教程：创建基本表报表（报表生成器）](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="d0e23-122">For step-by-step instructions about how to browse to a report server, choose a data source, and create a dataset, see the first tutorial in this series: [Tutorial: Creating a Basic Table Report &#40;Report Builder&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md).</span></span>  
  
 <span data-ttu-id="d0e23-123">本教程的预计学时：15 分钟。</span><span class="sxs-lookup"><span data-stu-id="d0e23-123">Estimated time to complete this tutorial: 15 minutes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0e23-124">要求</span><span class="sxs-lookup"><span data-stu-id="d0e23-124">Requirements</span></span>  
 <span data-ttu-id="d0e23-125">有关要求的信息，请参阅[教程先决条件（报表生成器）](../reporting-services/report-builder-tutorials.md)。</span><span class="sxs-lookup"><span data-stu-id="d0e23-125">For information about requirements, see [Prerequisites for Tutorials &#40;Report Builder&#41;](../reporting-services/report-builder-tutorials.md).</span></span>  
  
##  <a name="1-create-a-chart-report-from-the-chart-wizard"></a><a name="Chart"></a><span data-ttu-id="d0e23-126">1. 使用图表向导创建图表报表</span><span class="sxs-lookup"><span data-stu-id="d0e23-126">1. Create a Chart Report from the Chart Wizard</span></span>  
 <span data-ttu-id="d0e23-127">从 "**入门**" 对话框中，使用图表向导创建嵌入数据集，选择共享数据源，并创建柱形图。</span><span class="sxs-lookup"><span data-stu-id="d0e23-127">From the **Getting Started** dialog box, use the Chart Wizard to create an embedded dataset, choose a shared data source, and create a column chart.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d0e23-128">在本教程中，由于查询包含了数据值，因此它不需要外部数据源。</span><span class="sxs-lookup"><span data-stu-id="d0e23-128">In this tutorial, the query contains the data values, so that it does not need an external data source.</span></span> <span data-ttu-id="d0e23-129">这样，查询就会非常长。</span><span class="sxs-lookup"><span data-stu-id="d0e23-129">This makes the query quite long.</span></span> <span data-ttu-id="d0e23-130">在业务环境中，查询不会包含数据。</span><span class="sxs-lookup"><span data-stu-id="d0e23-130">In a business environment, a query would not contain the data.</span></span> <span data-ttu-id="d0e23-131">本教程中的查询仅供学习使用。</span><span class="sxs-lookup"><span data-stu-id="d0e23-131">This is for learning purposes only.</span></span>  
  
#### <a name="to-create-a-new-chart-report"></a><span data-ttu-id="d0e23-132">创建新的图表报表</span><span class="sxs-lookup"><span data-stu-id="d0e23-132">To create a new chart report</span></span>  
  
1.  <span data-ttu-id="d0e23-133">单击 **“开始”**，依次指向 **“程序”**、 **Microsoft SQL Server 2012 Report Builder**，再单击 **“报表生成器”**。</span><span class="sxs-lookup"><span data-stu-id="d0e23-133">Click **Start**, point to **Programs**, point to **Microsoft SQL Server 2012 Report Builder**, and then click **Report Builder**.</span></span>  
  
     <span data-ttu-id="d0e23-134">此时将显示 "**入门**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="d0e23-134">The **Getting Started** dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d0e23-135">如果未显示 "**入门**" 对话框，请在 "**报表生成器**" 按钮中单击 "**新建**"。</span><span class="sxs-lookup"><span data-stu-id="d0e23-135">If the **Getting Started** dialog box does not appear, from the **Report Builder** button, click **New**.</span></span>  
  
2.  <span data-ttu-id="d0e23-136">在左窗格中，确认已选中 **“新建报表”** 。</span><span class="sxs-lookup"><span data-stu-id="d0e23-136">In the left pane, verify that **New Report** is selected.</span></span>  
  
3.  <span data-ttu-id="d0e23-137">在右窗格中，单击“图表向导”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d0e23-137">In the right pane, click **Chart Wizard**.</span></span>  
  
4.  <span data-ttu-id="d0e23-138">在“选择数据集”页上，单击“创建数据集”，然后单击“下一步”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d0e23-138">On the **Choose a dataset page**, click **Create a dataset**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="d0e23-139">在“选择数据源的连接”页中，选择现有数据源或浏览到报表服务器并选择一个数据源，然后单击“下一步”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d0e23-139">On the **Choose a connection to a data source** page, select an existing data source or browse to the report server and select a data source, and then click **Next**.</span></span> <span data-ttu-id="d0e23-140">您可能需要输入用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="d0e23-140">You may need to enter a user name and password.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d0e23-141">只要您具有足够的权限，则选择哪一个数据源并不重要。</span><span class="sxs-lookup"><span data-stu-id="d0e23-141">The data source you choose is unimportant, as long as you have adequate permissions.</span></span> <span data-ttu-id="d0e23-142">您将不会从数据源中获取数据。</span><span class="sxs-lookup"><span data-stu-id="d0e23-142">You will not be getting data from the data source.</span></span> <span data-ttu-id="d0e23-143">有关详细信息，请参阅[获取数据连接的备选方式（报表生成器）](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="d0e23-143">For more information, see [Alternative Ways to Get a Data Connection &#40;Report Builder&#41;](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md).</span></span>  
  
6.  <span data-ttu-id="d0e23-144">在“设计查询”页上，单击“编辑为文本”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d0e23-144">On the **Design a query** page, click **Edit as Text**.</span></span>  
  
7.  <span data-ttu-id="d0e23-145">将以下查询粘贴到查询窗格中：</span><span class="sxs-lookup"><span data-stu-id="d0e23-145">Paste the following query into the query pane:</span></span>  
  
    ```  
    SELECT CAST('2009-01-01' AS date) AS SalesDate, CAST(54995.21 AS money) AS Sales  
    UNION SELECT CAST('2009-01-05' AS date) AS SalesDate, CAST(64499.04 AS money) AS Sales  
    UNION SELECT CAST('2009-02-11' AS date) AS SalesDate, CAST(37821.79 AS money) AS Sales  
    UNION SELECT CAST('2009-03-18' AS date) AS SalesDate, CAST(53633.08 AS money) AS Sales  
    UNION SELECT CAST('2009-04-23' AS date) AS SalesDate, CAST(24019.3 AS money) AS Sales  
    UNION SELECT CAST('2009-05-01' AS date) AS SalesDate, CAST(93245.5 AS money) AS Sales  
    UNION SELECT CAST('2009-06-06' AS date) AS SalesDate, CAST(55288.0 AS money) AS Sales  
    UNION SELECT CAST('2009-06-16' AS date) AS SalesDate, CAST(68733.5 AS money) AS Sales  
    UNION SELECT CAST('2009-07-16' AS date) AS SalesDate, CAST(24750.85 AS money) AS Sales  
    UNION SELECT CAST('2009-08-23' AS date) AS SalesDate, CAST(43452.3 AS money) AS Sales  
    UNION SELECT CAST('2009-09-24' AS date) AS SalesDate, CAST(58656. AS money) AS Sales  
    UNION SELECT CAST('2009-10-15' AS date) AS SalesDate, CAST(44583. AS money) AS Sales  
    UNION SELECT CAST('2009-11-21' AS date) AS SalesDate, CAST(81568. AS money) AS Sales  
    UNION SELECT CAST('2009-12-15' AS date) AS SalesDate, CAST(45973. AS money) AS Sales  
    UNION SELECT CAST('2009-12-26' AS date) AS SalesDate, CAST(96357. AS money) AS Sales  
    UNION SELECT CAST('2009-12-31' AS date) AS SalesDate, CAST(81946. AS money) AS Sales  
    ```  
  
8.  <span data-ttu-id="d0e23-146">（可选）单击“运行”按钮 (!)，查看要用于图表的数据\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d0e23-146">(Optional) Click the Run button (**!**) to see the data your chart will be based on.</span></span>  
  
9. <span data-ttu-id="d0e23-147">单击“下一步”。 </span><span class="sxs-lookup"><span data-stu-id="d0e23-147">Click **Next**.</span></span>  
  
##  <a name="2-choose-the-chart-type"></a><a name="ChartType"></a><span data-ttu-id="d0e23-148">2. 选择图表类型</span><span class="sxs-lookup"><span data-stu-id="d0e23-148">2. Choose the Chart Type</span></span>  
 <span data-ttu-id="d0e23-149">可以从各种预定义的图表类型中进行选择。</span><span class="sxs-lookup"><span data-stu-id="d0e23-149">You can choose from a variety of predefined chart types.</span></span>  
  
#### <a name="to-add-a-column-chart"></a><span data-ttu-id="d0e23-150">添加柱形图</span><span class="sxs-lookup"><span data-stu-id="d0e23-150">To add a column chart</span></span>  
  
1.  <span data-ttu-id="d0e23-151">在“选择图表类型”页上，柱形图为默认图表类型\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d0e23-151">On the **Choose a chart type** page, the column chart is the default chart type.</span></span> <span data-ttu-id="d0e23-152">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="d0e23-152">Click **Next**.</span></span>  
  
2.  <span data-ttu-id="d0e23-153">在“排列图表字段”页上，将 SalesDate 字段拖到“类别”中\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d0e23-153">On the **Arrange chart fields** page, drag the SalesDate field to **Categories**.</span></span> <span data-ttu-id="d0e23-154">“类别”显示在水平轴上。</span><span class="sxs-lookup"><span data-stu-id="d0e23-154">Categories display on the horizontal axis.</span></span>  
  
3.  <span data-ttu-id="d0e23-155">将 Sales 字段拖到“值”中\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d0e23-155">Drag the Sales field to **Values**.</span></span> <span data-ttu-id="d0e23-156">“值”框显示 Sum(Sales)，因为销售总计值之和是对每个日期的合计\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d0e23-156">The **Values** box displays Sum(Sales) because the sum of the sales total value is aggregated for each date.</span></span> <span data-ttu-id="d0e23-157">“值”显示在垂直轴上。</span><span class="sxs-lookup"><span data-stu-id="d0e23-157">Values display on the vertical axis.</span></span>  
  
4.  <span data-ttu-id="d0e23-158">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="d0e23-158">Click **Next**.</span></span>  
  
5.  <span data-ttu-id="d0e23-159">在 "**选择样式**" 页上的 "样式" 框中，选择样式。</span><span class="sxs-lookup"><span data-stu-id="d0e23-159">On the **Choose a Style** page, in the Styles box, select a style.</span></span>  
  
     <span data-ttu-id="d0e23-160">样式指定字形、颜色集和边框样式。</span><span class="sxs-lookup"><span data-stu-id="d0e23-160">A style specifies a font style, a set of colors, and a border style.</span></span> <span data-ttu-id="d0e23-161">选择样式时，“预览”窗格将显示具有该样式的图表的示例。</span><span class="sxs-lookup"><span data-stu-id="d0e23-161">When you select a style, the Preview pane displays a sample of the chart with that style.</span></span>  
  
6.  <span data-ttu-id="d0e23-162">单击“完成”。</span><span class="sxs-lookup"><span data-stu-id="d0e23-162">Click **Finish**.</span></span>  
  
     <span data-ttu-id="d0e23-163">图表将添加到设计图面中。</span><span class="sxs-lookup"><span data-stu-id="d0e23-163">The chart is added to the design surface.</span></span>  
  
7.  <span data-ttu-id="d0e23-164">单击图表以显示图表控点。</span><span class="sxs-lookup"><span data-stu-id="d0e23-164">Click the chart to display the chart handles.</span></span> <span data-ttu-id="d0e23-165">拖动该图表的右下角以扩大该图表。</span><span class="sxs-lookup"><span data-stu-id="d0e23-165">Drag the bottom-right corner of the chart to increase the size of the chart.</span></span> <span data-ttu-id="d0e23-166">请注意，报表设计图面的大小将增大以容纳图表。</span><span class="sxs-lookup"><span data-stu-id="d0e23-166">Note that the report design surface increases in size to accommodate the chart size.</span></span>  
  
8.  <span data-ttu-id="d0e23-167">单击 **“运行”** 以预览报表。</span><span class="sxs-lookup"><span data-stu-id="d0e23-167">Click **Run** to preview the report.</span></span>  
  
##  <a name="3-format-and-label-the-horizontal-axis"></a><a name="Horizontal"></a><span data-ttu-id="d0e23-168">3. 设置水平轴的格式和标签</span><span class="sxs-lookup"><span data-stu-id="d0e23-168">3. Format and Label the Horizontal Axis</span></span>  
 <span data-ttu-id="d0e23-169">默认情况下，水平轴采用常用格式显示值，将自动调整为适合图表的大小。</span><span class="sxs-lookup"><span data-stu-id="d0e23-169">By default, the horizontal axis displays values in a general format that is automatically scaled to fit the size of the chart.</span></span>  
  
#### <a name="to-format-a-date-on-the-horizontal-axis"></a><span data-ttu-id="d0e23-170">设置水平轴上的日期格式</span><span class="sxs-lookup"><span data-stu-id="d0e23-170">To format a date on the horizontal axis</span></span>  
  
1.  <span data-ttu-id="d0e23-171">切换到报表设计视图。</span><span class="sxs-lookup"><span data-stu-id="d0e23-171">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="d0e23-172">右键单击水平轴，然后单击 "**水平轴属性**"。</span><span class="sxs-lookup"><span data-stu-id="d0e23-172">Right-click the horizontal axis, and then click **Horizontal Axis Properties**.</span></span>  
  
3.  <span data-ttu-id="d0e23-173">单击 "**数字**"。</span><span class="sxs-lookup"><span data-stu-id="d0e23-173">Click **Number**.</span></span>  
  
4.  <span data-ttu-id="d0e23-174">在 "**类别**" 中，选择 "**日期**"。</span><span class="sxs-lookup"><span data-stu-id="d0e23-174">In **Category**, select **Date**.</span></span>  
  
5.  <span data-ttu-id="d0e23-175">在“类型”框中，选择“2000 年 1 月 31 日”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d0e23-175">In the **Type** box, select **31 Jan 2000**.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  <span data-ttu-id="d0e23-176">在“主文件夹”选项卡上，单击“运行”以预览报表\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d0e23-176">On the Home tab, click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="d0e23-177">日期会以您选择的日期格式显示。</span><span class="sxs-lookup"><span data-stu-id="d0e23-177">The date displays in the date format that you selected.</span></span> <span data-ttu-id="d0e23-178">请注意，图表不会在水平轴上显示每个类别的标签。</span><span class="sxs-lookup"><span data-stu-id="d0e23-178">Notice that the chart does not label every category on the horizontal axis.</span></span> <span data-ttu-id="d0e23-179">默认情况下，仅包括适合放在轴旁边的标签。</span><span class="sxs-lookup"><span data-stu-id="d0e23-179">By default, only labels that fit next to the axis are included.</span></span>  
  
 <span data-ttu-id="d0e23-180">通过旋转标签和指定间隔，可以自定义标签显示方式。</span><span class="sxs-lookup"><span data-stu-id="d0e23-180">You can customize the label display by rotating the labels and specifying the interval.</span></span>  
  
#### <a name="to-rotate-the-axis-labels-and-change-the-display-interval-along-the-horizontal-axis"></a><span data-ttu-id="d0e23-181">沿着水平轴旋转轴标签并更改显示间隔</span><span class="sxs-lookup"><span data-stu-id="d0e23-181">To rotate the axis labels and change the display interval along the horizontal axis</span></span>  
  
1.  <span data-ttu-id="d0e23-182">切换到报表设计视图。</span><span class="sxs-lookup"><span data-stu-id="d0e23-182">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="d0e23-183">右键单击水平轴标题，然后单击 "**显示轴标题**" 以删除标题。</span><span class="sxs-lookup"><span data-stu-id="d0e23-183">Right-click the horizontal axis title, and then click **Show Axis Title** to remove the title.</span></span> <span data-ttu-id="d0e23-184">因为水平轴显示日期，所以不需要标题。</span><span class="sxs-lookup"><span data-stu-id="d0e23-184">Because the horizontal axis displays dates, the title is not needed.</span></span>  
  
3.  <span data-ttu-id="d0e23-185">右键单击水平轴，然后单击 "**水平轴属性**"。</span><span class="sxs-lookup"><span data-stu-id="d0e23-185">Right-click the horizontal axis and then click **Horizontal Axis Properties**.</span></span>  
  
4.  <span data-ttu-id="d0e23-186">在 "轴**选项**" 页中的 "**轴范围和间隔**" 下，键入**3**作为 "**间隔**"。</span><span class="sxs-lookup"><span data-stu-id="d0e23-186">In the **Axis Options** page under **Axis range and interval**, type **3** for **Interval**.</span></span> <span data-ttu-id="d0e23-187">图表将每隔三个日期显示一次标签。</span><span class="sxs-lookup"><span data-stu-id="d0e23-187">The chart will display every third date.</span></span>  
  
5.  <span data-ttu-id="d0e23-188">单击 "**标签**"。</span><span class="sxs-lookup"><span data-stu-id="d0e23-188">Click **Labels**.</span></span>  
  
6.  <span data-ttu-id="d0e23-189">在 "**更改轴标签自动调整" 选项**中，选择 "**禁用自动调整**"。</span><span class="sxs-lookup"><span data-stu-id="d0e23-189">In **Change axis label auto-fit options**, select **Disable auto-fit**.</span></span>  
  
7.  <span data-ttu-id="d0e23-190">在“标签旋转角度”中，选择 -90\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d0e23-190">In **Label rotation angle**, select **-90**.</span></span>  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="d0e23-191">水平轴的示例文本将旋转 90 度。</span><span class="sxs-lookup"><span data-stu-id="d0e23-191">The sample text for the horizontal axis rotates by 90 degrees.</span></span>  
  
9. <span data-ttu-id="d0e23-192">单击 **“运行”** 以预览报表。</span><span class="sxs-lookup"><span data-stu-id="d0e23-192">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="d0e23-193">在图表上，标签将旋转并每隔三个日期显示一次标签。</span><span class="sxs-lookup"><span data-stu-id="d0e23-193">On the chart, the labels are rotated and the label for every third date is shown.</span></span>  
  
##  <a name="4-move-the-legend"></a><a name="Legend"></a><span data-ttu-id="d0e23-194">4. 移动图例</span><span class="sxs-lookup"><span data-stu-id="d0e23-194">4. Move the Legend</span></span>  
 <span data-ttu-id="d0e23-195">系统会根据类别和序列数据自动创建图例。</span><span class="sxs-lookup"><span data-stu-id="d0e23-195">The legend is automatically created from category and series data.</span></span>  
  
#### <a name="to-move-the-legend-below-the-chart-area-of-a-column-chart"></a><span data-ttu-id="d0e23-196">在柱形图的图表区域的下方移动图例</span><span class="sxs-lookup"><span data-stu-id="d0e23-196">To move the legend below the chart area of a column chart</span></span>  
  
1.  <span data-ttu-id="d0e23-197">切换到报表设计视图。</span><span class="sxs-lookup"><span data-stu-id="d0e23-197">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="d0e23-198">右键单击图表上的图例，然后单击 "**图例属性**"。</span><span class="sxs-lookup"><span data-stu-id="d0e23-198">Right-click the legend on the chart, and then click **Legend Properties**.</span></span>  
  
3.  <span data-ttu-id="d0e23-199">对于 "**布局和位置**"，请选择其他位置。</span><span class="sxs-lookup"><span data-stu-id="d0e23-199">For **Layout and Position**, select a different position.</span></span> <span data-ttu-id="d0e23-200">例如，将图例位置设置为底部中间。</span><span class="sxs-lookup"><span data-stu-id="d0e23-200">For example, set the position to the middle bottom option.</span></span>  
  
     <span data-ttu-id="d0e23-201">如果将图例置于图表的顶部或底部，则图例的布局将会从垂直改为水平。</span><span class="sxs-lookup"><span data-stu-id="d0e23-201">When the legend is placed at the top or bottom of a chart, the layout of the legend changes from vertical to horizontal.</span></span> <span data-ttu-id="d0e23-202">可以从“布局”下拉列表中选择不同的布局\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d0e23-202">You can select a different layout from the **Layout** drop-down list.</span></span>  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="d0e23-203">（可选）因为本教程中只有一个类别，所以不需要图例。</span><span class="sxs-lookup"><span data-stu-id="d0e23-203">(Optional) Because there is only one category in this tutorial, the legend is not needed.</span></span> <span data-ttu-id="d0e23-204">若要删除图例，请右键单击图例，然后单击 "**删除图例**"。</span><span class="sxs-lookup"><span data-stu-id="d0e23-204">To remove the legend, right-click the legend and then click **Delete Legend**.</span></span>  
  
6.  <span data-ttu-id="d0e23-205">单击 **“运行”** 以预览报表。</span><span class="sxs-lookup"><span data-stu-id="d0e23-205">Click **Run** to preview the report.</span></span>  
  
##  <a name="5-title-the-chart"></a><a name="ChartTitle"></a><span data-ttu-id="d0e23-206">5. 为图表标题</span><span class="sxs-lookup"><span data-stu-id="d0e23-206">5. Title the Chart</span></span>  
  
#### <a name="to-change-the-chart-title-above-the-chart-area"></a><span data-ttu-id="d0e23-207">更改图表区上方的图表标题</span><span class="sxs-lookup"><span data-stu-id="d0e23-207">To change the chart title above the chart area</span></span>  
  
1.  <span data-ttu-id="d0e23-208">切换到报表设计视图。</span><span class="sxs-lookup"><span data-stu-id="d0e23-208">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="d0e23-209">选择图表顶部的词语 "**图表标题**"，然后键入以下文本：**商店销售订单总计**。</span><span class="sxs-lookup"><span data-stu-id="d0e23-209">Select the words **Chart Title** at the top of the chart, and then type the following text: **Store Sales Order Totals**.</span></span>  
  
3.  <span data-ttu-id="d0e23-210">单击 **“运行”** 以预览报表。</span><span class="sxs-lookup"><span data-stu-id="d0e23-210">Click **Run** to preview the report.</span></span>  
  
##  <a name="6-format-and-label-the-vertical-axis"></a><a name="Vertical"></a><span data-ttu-id="d0e23-211">6. 设置垂直轴的格式和标签</span><span class="sxs-lookup"><span data-stu-id="d0e23-211">6. Format and Label the Vertical Axis</span></span>  
 <span data-ttu-id="d0e23-212">默认情况下，垂直轴采用常用格式显示值，将自动调整为适合图表的大小。</span><span class="sxs-lookup"><span data-stu-id="d0e23-212">By default, the vertical axis displays values in a general format that is automatically scaled to fit the size of the chart.</span></span>  
  
#### <a name="to-format-as-currency-the-numbers-on-the-vertical-axis"></a><span data-ttu-id="d0e23-213">将货币格式设置为垂直轴上的数字</span><span class="sxs-lookup"><span data-stu-id="d0e23-213">To format as currency the numbers on the vertical axis</span></span>  
  
1.  <span data-ttu-id="d0e23-214">切换到报表设计视图。</span><span class="sxs-lookup"><span data-stu-id="d0e23-214">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="d0e23-215">在图表的一侧双击垂直轴上的标签以选择它们。</span><span class="sxs-lookup"><span data-stu-id="d0e23-215">Double-click the labels on the vertical axis along the side of the chart to select them.</span></span>  
  
3.  <span data-ttu-id="d0e23-216">在功能区上，在 "**主页**" 选项卡上的 "**数字**" 组中，单击 "**货币**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="d0e23-216">On the ribbon, on the **Home** tab, in the **Number** group, click the **Currency** button.</span></span> <span data-ttu-id="d0e23-217">轴标签将更改以显示货币格式。</span><span class="sxs-lookup"><span data-stu-id="d0e23-217">The axis labels change to show the currency format.</span></span>  
  
4.  <span data-ttu-id="d0e23-218">在功能区上，在 "**主页**" 选项卡上的 "**数字**" 组中，单击两次 "**减少小数位数**" 按钮，以显示舍入为最接近的数字。</span><span class="sxs-lookup"><span data-stu-id="d0e23-218">On the ribbon, on the **Home** tab, in the **Number** group, click the **Decrease Decimal** button two times, to show the number rounded to the nearest dollar.</span></span>  
  
5.  <span data-ttu-id="d0e23-219">右键单击垂直轴，然后单击 "**垂直轴属性**"。</span><span class="sxs-lookup"><span data-stu-id="d0e23-219">Right-click the vertical axis and click **Vertical Axis Properties**.</span></span>  
  
6.  <span data-ttu-id="d0e23-220">单击 "**数字**"。</span><span class="sxs-lookup"><span data-stu-id="d0e23-220">Click **Number**.</span></span> <span data-ttu-id="d0e23-221">请注意，已在 "**类别**" 框中选择了 "**货币**"，并且 "**小数位数**" 已经为**0** (零) 。</span><span class="sxs-lookup"><span data-stu-id="d0e23-221">Note that **Currency** is already selected in the **Category** box, and **Decimal places** is already **0** (zero).</span></span>  
  
7.  <span data-ttu-id="d0e23-222">在 "**显示值**" 框中，单击 "**千位**"。</span><span class="sxs-lookup"><span data-stu-id="d0e23-222">In the **Show Values in** box, click **Thousands**.</span></span>  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
9. <span data-ttu-id="d0e23-223">右键单击图表一侧的垂直轴标题，然后单击 "**轴标题属性**"。</span><span class="sxs-lookup"><span data-stu-id="d0e23-223">Right-click the vertical axis title along the side of the chart and click **Axis Title Properties**.</span></span>  
  
10. <span data-ttu-id="d0e23-224">将 "**标题文本**" 字段中的文本替换为以下文本： \*\*Sales Total (千) \*\*。</span><span class="sxs-lookup"><span data-stu-id="d0e23-224">Replace the text in the **Title text** field with the following text: **Sales Total (in Thousands)**.</span></span> <span data-ttu-id="d0e23-225">还可以指定与如何设置标题格式相关的多种选项。</span><span class="sxs-lookup"><span data-stu-id="d0e23-225">You can also specify a variety of options related to how the title is formatted.</span></span>  
  
11. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
12. <span data-ttu-id="d0e23-226">单击 **“运行”** 以预览报表。</span><span class="sxs-lookup"><span data-stu-id="d0e23-226">Click **Run** to preview the report.</span></span>  
  
##  <a name="7-add-a-moving-average"></a><a name="Average"></a><span data-ttu-id="d0e23-227">7. 添加移动平均线</span><span class="sxs-lookup"><span data-stu-id="d0e23-227">7. Add a Moving Average</span></span>  
  
#### <a name="to-add-a-moving-average"></a><span data-ttu-id="d0e23-228">添加移动平均线</span><span class="sxs-lookup"><span data-stu-id="d0e23-228">To add a moving average</span></span>  
  
1.  <span data-ttu-id="d0e23-229">切换到报表设计视图。</span><span class="sxs-lookup"><span data-stu-id="d0e23-229">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="d0e23-230">双击图表以显示“图表数据”窗格\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d0e23-230">Double-click the chart to display the **Chart Data** pane.</span></span>  
  
3.  <span data-ttu-id="d0e23-231">右键单击 "**值**" 区域中的 **[Sum (Sales) ]** 字段，然后单击 "**添加计算序列**"。</span><span class="sxs-lookup"><span data-stu-id="d0e23-231">Right-click the **[Sum(Sales)]** field that is in the **Values** area, and then click **Add Calculated Series**.</span></span>  
  
4.  <span data-ttu-id="d0e23-232">在“公式”中，验证是否已选中“移动平均线”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d0e23-232">In **Formula**, verify that **Moving average** is selected.</span></span>  
  
5.  <span data-ttu-id="d0e23-233">在“设置公式参数”中，针对“期间”，选择“4”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d0e23-233">In **Set Formula Parameters**, for **Period**, select **4**.</span></span>  
  
6.  <span data-ttu-id="d0e23-234">单击 "**边框**"。</span><span class="sxs-lookup"><span data-stu-id="d0e23-234">Click **Border**.</span></span>  
  
7.  <span data-ttu-id="d0e23-235">在 "**线条宽度**" 中，选择**3pt**。</span><span class="sxs-lookup"><span data-stu-id="d0e23-235">In **Line width**, select **3pt**.</span></span>  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
9. <span data-ttu-id="d0e23-236">单击 **“运行”** 以预览报表。</span><span class="sxs-lookup"><span data-stu-id="d0e23-236">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="d0e23-237">图表将显示一条线条，它按日期显示销售总计的移动平均线，每隔四天计算一次平均值。</span><span class="sxs-lookup"><span data-stu-id="d0e23-237">The chart displays a line that shows the moving average for total sales by date, averaged over every four dates.</span></span>  
  
##  <a name="8-add-a-report-title"></a><a name="Title"></a><span data-ttu-id="d0e23-238">8. 添加报表标题</span><span class="sxs-lookup"><span data-stu-id="d0e23-238">8. Add a Report Title</span></span>  
  
#### <a name="to-add-a-report-title"></a><span data-ttu-id="d0e23-239">添加报表标题</span><span class="sxs-lookup"><span data-stu-id="d0e23-239">To add a report title</span></span>  
  
1.  <span data-ttu-id="d0e23-240">切换到报表设计视图。</span><span class="sxs-lookup"><span data-stu-id="d0e23-240">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="d0e23-241">在设计图面上，单击“单击以添加标题”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d0e23-241">On the design surface, click **Click to add title**.</span></span>  
  
3.  <span data-ttu-id="d0e23-242">键入**Sales Chart**，按 enter，然后键入**一月到12月 2009**，如下所示：</span><span class="sxs-lookup"><span data-stu-id="d0e23-242">Type **Sales Chart**, press ENTER, and then type **January to December 2009**, so it looks like this:</span></span>  
  
     <span data-ttu-id="d0e23-243">**Sales Chart**</span><span class="sxs-lookup"><span data-stu-id="d0e23-243">**Sales Chart**</span></span>  
  
     <span data-ttu-id="d0e23-244">**2009 年 1 月到 12 月**</span><span class="sxs-lookup"><span data-stu-id="d0e23-244">**January to December 2009**</span></span>  
  
4.  <span data-ttu-id="d0e23-245">选择 "**销售图表**"，然后单击功能区 "**主页**" 选项卡上 "**字体**" 部分中的 "**粗体**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="d0e23-245">Select **Sales Chart**, and click the **Bold** button in the **Font** section on the **Home** tab of the ribbon.</span></span>  
  
5.  <span data-ttu-id="d0e23-246">选择 "**一月到12月 2009**"，然后在 "**主页**" 选项卡的 "**字体**" 部分中，将字号设置为**10**。</span><span class="sxs-lookup"><span data-stu-id="d0e23-246">Select **January to December 2009**, and in the **Font** section on the **Home** tab, set the font size to **10**.</span></span>  
  
6.  <span data-ttu-id="d0e23-247"> (可选) 您可能需要使 "**标题**" 文本框更高一些，以容纳两行文本，方法是在单击下边缘中间的双箭头时下拉。</span><span class="sxs-lookup"><span data-stu-id="d0e23-247">(Optional) You may need to make the **Title** text box taller to accommodate the two lines of text by pulling down on the double-headed arrows when you click in the middle of the bottom edge.</span></span>  
  
     <span data-ttu-id="d0e23-248">此标题将显示在报表的顶部。</span><span class="sxs-lookup"><span data-stu-id="d0e23-248">This title will appear at the top of the report.</span></span> <span data-ttu-id="d0e23-249">未定义页标头时，报表体顶部的项就等同于报表标头。</span><span class="sxs-lookup"><span data-stu-id="d0e23-249">When there is no page header defined, items at the top of the report body are the equivalent of a report header.</span></span>  
  
7.  <span data-ttu-id="d0e23-250">单击 **“运行”** 以预览报表。</span><span class="sxs-lookup"><span data-stu-id="d0e23-250">Click **Run** to preview the report.</span></span>  
  
##  <a name="9-save-the-report"></a><a name="Save"></a><span data-ttu-id="d0e23-251">9. 保存报表</span><span class="sxs-lookup"><span data-stu-id="d0e23-251">9. Save the Report</span></span>  
  
#### <a name="to-save-the-report"></a><span data-ttu-id="d0e23-252">保存报表</span><span class="sxs-lookup"><span data-stu-id="d0e23-252">To save the report</span></span>  
  
1.  <span data-ttu-id="d0e23-253">切换到报表设计视图。</span><span class="sxs-lookup"><span data-stu-id="d0e23-253">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="d0e23-254">从 “报表生成器” 按钮，单击 **“另存为”**。</span><span class="sxs-lookup"><span data-stu-id="d0e23-254">From the Report Builder button, click **Save As**.</span></span>  
  
3.  <span data-ttu-id="d0e23-255">在“名称”中，键入 Sales Order Column Chart\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d0e23-255">In **Name**, type **Sales Order Column Chart**.</span></span>  
  
4.  <span data-ttu-id="d0e23-256">单击“ **保存**”。</span><span class="sxs-lookup"><span data-stu-id="d0e23-256">Click **Save**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="d0e23-257">后续步骤</span><span class="sxs-lookup"><span data-stu-id="d0e23-257">Next Steps</span></span>  
 <span data-ttu-id="d0e23-258">您已成功完成“向报表添加柱形图”教程。</span><span class="sxs-lookup"><span data-stu-id="d0e23-258">You have successfully completed the Adding a Column Chart to Your Report tutorial.</span></span> <span data-ttu-id="d0e23-259">若要了解有关图表的详细信息，请参阅[图表（报表生成器和 SSRS）](report-design/charts-report-builder-and-ssrs.md)和[迷你图和数据条（报表生成器和 SSRS）](report-design/sparklines-and-data-bars-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="d0e23-259">To learn more about charts, see [Charts &#40;Report Builder and SSRS&#41;](report-design/charts-report-builder-and-ssrs.md) and [Sparklines and Data Bars &#40;Report Builder and SSRS&#41;](report-design/sparklines-and-data-bars-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0e23-260">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d0e23-260">See Also</span></span>  
 <span data-ttu-id="d0e23-261">[教程 &#40;报表生成器&#41;](report-builder-tutorials.md) </span><span class="sxs-lookup"><span data-stu-id="d0e23-261">[Tutorials &#40;Report Builder&#41;](report-builder-tutorials.md) </span></span>  
 [<span data-ttu-id="d0e23-262">SQL Server 2014 中的报表生成器</span><span class="sxs-lookup"><span data-stu-id="d0e23-262">Report Builder in SQL Server 2014</span></span>](report-builder/report-builder-in-sql-server-2016.md)  
  
  
