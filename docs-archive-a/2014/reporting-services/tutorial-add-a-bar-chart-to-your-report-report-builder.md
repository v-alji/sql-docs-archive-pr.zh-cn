---
title: 教程：向报表添加条形图（报表生成器）| Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 6956ebd6-0217-4087-a4fa-5cc1c3804691
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 01708ca548c40118daa03fac34d8a323d628b012
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580555"
---
# <a name="tutorial-add-a-bar-chart-to-your-report-report-builder"></a><span data-ttu-id="b7957-102">教程：向报表添加条形图（报表生成器）</span><span class="sxs-lookup"><span data-stu-id="b7957-102">Tutorial: Add a Bar Chart to Your Report (Report Builder)</span></span>
  <span data-ttu-id="b7957-103">条形图以水平方式显示类别数据。</span><span class="sxs-lookup"><span data-stu-id="b7957-103">A bar chart displays category data horizontally.</span></span> <span data-ttu-id="b7957-104">这有助于：</span><span class="sxs-lookup"><span data-stu-id="b7957-104">This can help to:</span></span>  
  
-   <span data-ttu-id="b7957-105">提高长类别名称的可读性。</span><span class="sxs-lookup"><span data-stu-id="b7957-105">Improve readability of long category names.</span></span>  
  
-   <span data-ttu-id="b7957-106">提高绘制为值的时间的可理解性。</span><span class="sxs-lookup"><span data-stu-id="b7957-106">Improve understandability of times plotted as values.</span></span>  
  
-   <span data-ttu-id="b7957-107">比较多个序列的相对值。</span><span class="sxs-lookup"><span data-stu-id="b7957-107">Compare the relative value of multiple series.</span></span>  
  
 <span data-ttu-id="b7957-108">下图显示了您将创建的条形图，条形图中按字母顺序显示了 2008 和 2009 年度前五位销售人员的销售情况。</span><span class="sxs-lookup"><span data-stu-id="b7957-108">The following illustration shows the bar chart that you will create, with sales for 2008 and 2009 for the top five salespeople, in alphabetical order.</span></span>  
  
 <span data-ttu-id="b7957-109">![rs_BarChartTutorial](../../2014/tutorials/media/rs-barcharttutorial.gif "rs_BarChartTutorial")</span><span class="sxs-lookup"><span data-stu-id="b7957-109">![rs_BarChartTutorial](../../2014/tutorials/media/rs-barcharttutorial.gif "rs_BarChartTutorial")</span></span>  
  
##  <a name="what-you-will-learn"></a><a name="BackToTop"></a><span data-ttu-id="b7957-110">你将学习的内容</span><span class="sxs-lookup"><span data-stu-id="b7957-110">What You Will Learn</span></span>  
 <span data-ttu-id="b7957-111">在本教程中，您将学习如何执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="b7957-111">In this tutorial you will learn how to do the following:</span></span>  
  
1.  [<span data-ttu-id="b7957-112">使用图表向导创建图表</span><span class="sxs-lookup"><span data-stu-id="b7957-112">Create a Chart from the Chart Wizard</span></span>](#Chart)  
  
2.  [<span data-ttu-id="b7957-113">选择图表类型</span><span class="sxs-lookup"><span data-stu-id="b7957-113">Choose the Chart Type</span></span>](#ChartType)  
  
3.  [<span data-ttu-id="b7957-114">在垂直轴上显示所有类别值</span><span class="sxs-lookup"><span data-stu-id="b7957-114">Display all Category Values on the Vertical Axis</span></span>](#AllValues)  
  
4.  [<span data-ttu-id="b7957-115">修改垂直轴上的显示名称</span><span class="sxs-lookup"><span data-stu-id="b7957-115">Modify the Display of Names on the Vertical Axis</span></span>](#Sort)  
  
5.  [<span data-ttu-id="b7957-116">移动图例</span><span class="sxs-lookup"><span data-stu-id="b7957-116">Move the Legend</span></span>](#Legend)  
  
6.  [<span data-ttu-id="b7957-117">移动图表标题</span><span class="sxs-lookup"><span data-stu-id="b7957-117">Move the Chart Title</span></span>](#ChartTitle)  
  
7.  [<span data-ttu-id="b7957-118">设置水平轴的格式和标签</span><span class="sxs-lookup"><span data-stu-id="b7957-118">Format and Label the Horizontal Axis</span></span>](#Horizontal)  
  
8.  [<span data-ttu-id="b7957-119">添加筛选器以显示前五个值</span><span class="sxs-lookup"><span data-stu-id="b7957-119">Add a Filter to Display the Top Five Values</span></span>](#Filter)  
  
9. [<span data-ttu-id="b7957-120">添加报表标题</span><span class="sxs-lookup"><span data-stu-id="b7957-120">Add a Report Title</span></span>](#Title)  
  
10. [<span data-ttu-id="b7957-121">保存报表</span><span class="sxs-lookup"><span data-stu-id="b7957-121">Save the Report</span></span>](#Save)  
  
> [!NOTE]  
>  <span data-ttu-id="b7957-122">在本教程中，将向导的多个步骤合并为一个过程。</span><span class="sxs-lookup"><span data-stu-id="b7957-122">In this tutorial, the steps for the wizard are consolidated into one procedure.</span></span> <span data-ttu-id="b7957-123">有关如何浏览到报表服务器、创建数据集和选择数据源的分步说明，请参阅这一系列教程中的第一个教程：[教程：创建基本表报表（报表生成器）](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="b7957-123">For step-by-step instructions about how to browse to a report server, create a dataset, and choose a data source, see the first tutorial in this series: [Tutorial: Creating a Basic Table Report &#40;Report Builder&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md).</span></span>  
  
 <span data-ttu-id="b7957-124">本教程的预计学时：15 分钟。</span><span class="sxs-lookup"><span data-stu-id="b7957-124">Estimated time to complete this tutorial: 15 minutes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7957-125">要求</span><span class="sxs-lookup"><span data-stu-id="b7957-125">Requirements</span></span>  
 <span data-ttu-id="b7957-126">有关要求的详细信息，请参阅[教程先决条件（报表生成器）](../reporting-services/report-builder-tutorials.md)。</span><span class="sxs-lookup"><span data-stu-id="b7957-126">For more information about requirements, see [Prerequisites for Tutorials &#40;Report Builder&#41;](../reporting-services/report-builder-tutorials.md).</span></span>  
  
##  <a name="1-create-a-chart-report-from-the-chart-wizard"></a><a name="Chart"></a><span data-ttu-id="b7957-127">1. 使用图表向导创建图表报表</span><span class="sxs-lookup"><span data-stu-id="b7957-127">1. Create a Chart Report from the Chart Wizard</span></span>  
 <span data-ttu-id="b7957-128">从 "**入门**" 对话框中，创建嵌入数据集，选择共享数据源，并使用图表向导创建条形图。</span><span class="sxs-lookup"><span data-stu-id="b7957-128">From the **Getting Started** dialog box, create an embedded dataset, choose a shared data source, and create a bar chart by using the Chart Wizard.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b7957-129">在本教程中，由于查询包含了数据值，因此它不需要外部数据源。</span><span class="sxs-lookup"><span data-stu-id="b7957-129">In this tutorial, the query contains the data values so that it does not need an external data source.</span></span> <span data-ttu-id="b7957-130">这样，查询就会非常长。</span><span class="sxs-lookup"><span data-stu-id="b7957-130">This makes the query quite long.</span></span> <span data-ttu-id="b7957-131">在业务环境中，查询不会包含数据。</span><span class="sxs-lookup"><span data-stu-id="b7957-131">In a business environment, a query would not contain the data.</span></span> <span data-ttu-id="b7957-132">本教程中的查询仅供学习使用。</span><span class="sxs-lookup"><span data-stu-id="b7957-132">This is for learning purposes only.</span></span>  
  
#### <a name="to-create-a-new-chart-report"></a><span data-ttu-id="b7957-133">创建新的图表报表</span><span class="sxs-lookup"><span data-stu-id="b7957-133">To create a new chart report</span></span>  
  
1.  <span data-ttu-id="b7957-134">单击 **“开始”**，依次指向 **“程序”**、 **Microsoft SQL Server 2012 Report Builder**，再单击 **“报表生成器”**。</span><span class="sxs-lookup"><span data-stu-id="b7957-134">Click **Start**, point to **Programs**, point to **Microsoft SQL Server 2012 Report Builder**, and then click **Report Builder**.</span></span>  
  
     <span data-ttu-id="b7957-135">此时将显示 "**入门**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="b7957-135">The **Getting Started** dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b7957-136">如果 "**入门**" 对话框未出现，请单击 "报表生成器" 按钮，然后单击 "**新建**"。</span><span class="sxs-lookup"><span data-stu-id="b7957-136">If the **Getting Started** dialog box does not appear, click the Report Builder button, and then click **New**.</span></span>  
  
2.  <span data-ttu-id="b7957-137">在左窗格中，确认已选中 **“新建报表”** 。</span><span class="sxs-lookup"><span data-stu-id="b7957-137">In the left pane, verify that **New Report** is selected.</span></span>  
  
3.  <span data-ttu-id="b7957-138">在右窗格中，单击“图表向导”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b7957-138">In the right pane, click **Chart Wizard**.</span></span>  
  
4.  <span data-ttu-id="b7957-139">在 "**选择数据集**" 页上，单击 "**创建数据集**"，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="b7957-139">On the **Choose a dataset** page, click **Create a dataset**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="b7957-140">在“选择数据源的连接”页中，选择现有数据源或浏览到报表服务器并选择一个数据源，然后单击“下一步”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b7957-140">On the **Choose a connection to a data source** page, select an existing data source or browse to the report server and select a data source, and then click **Next**.</span></span> <span data-ttu-id="b7957-141">您可能需要输入用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="b7957-141">You may need to enter a user name and password.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b7957-142">只要您具有足够的权限，则选择哪一个数据源并不重要。</span><span class="sxs-lookup"><span data-stu-id="b7957-142">The data source you choose is unimportant, as long as you have adequate permissions.</span></span> <span data-ttu-id="b7957-143">您将不会从数据源中获取数据。</span><span class="sxs-lookup"><span data-stu-id="b7957-143">You will not be getting data from the data source.</span></span> <span data-ttu-id="b7957-144">有关详细信息，请参阅[获取数据连接的备选方式（报表生成器）](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="b7957-144">For more information, see [Alternative Ways to Get a Data Connection &#40;Report Builder&#41;](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md).</span></span>  
  
6.  <span data-ttu-id="b7957-145">在“设计查询”页上，单击“编辑为文本”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b7957-145">On the **Design a query** page, click **Edit as Text**.</span></span>  
  
7.  <span data-ttu-id="b7957-146">将以下查询粘贴到查询窗格中：</span><span class="sxs-lookup"><span data-stu-id="b7957-146">Paste the following query into the query pane:</span></span>  
  
    ```  
    SELECT 'Luis' as FirstName, 'Alverca' as LastName, CAST(170000.00 AS money) AS SalesYear2009, CAST(150000. AS money) AS SalesYear2008  
    UNION SELECT 'Jeffrey' as FirstName, 'Zeng' as LastName, CAST(210000. AS money) AS SalesYear2009, CAST(190000. AS money) AS SalesYear2008  
    UNION SELECT 'Houman' as FirstName, 'Pournasseh' as LastName, CAST(150000. AS money) AS SalesYear2009, CAST(180000. AS money) AS SalesYear2008  
    UNION SELECT 'Robin' as FirstName, 'Wood' as LastName, CAST(75000. AS money) AS SalesYear2009, CAST(175000. AS money) AS SalesYear2008  
    UNION SELECT 'Daniela' as FirstName, 'Guaita' as LastName,  CAST(170000. AS money) AS SalesYear2009, CAST(175000. AS money) AS SalesYear2008  
    UNION SELECT 'John' as FirstName, 'Yokim' as LastName, CAST(160000. AS money) AS SalesYear2009, CAST(195000. AS money) AS SalesYear2008  
    UNION SELECT 'Delphine' as FirstName, 'Ribaute' as LastName, CAST(180000. AS money) AS SalesYear2009, CAST(205000. AS money) AS SalesYear2008  
    UNION SELECT 'Robert' as FirstName, 'Hernady' as LastName, CAST(140000. AS money) AS SalesYear2009, CAST(180000. AS money) AS SalesYear2008  
    UNION SELECT 'Tanja' as FirstName, 'Plate' as LastName, CAST(150000. AS money) AS SalesYear2009, CAST(160000. AS money) AS SalesYear2008  
    UNION SELECT 'David' as FirstName, 'Bradley' as LastName, CAST(210000. AS money) AS SalesYear2009, CAST(180000. AS money) AS SalesYear2008  
    UNION SELECT 'Michal' as FirstName, 'Jaworski' as LastName, CAST(175000. AS money) AS SalesYear2009, CAST(220000. AS money) AS SalesYear2008  
    UNION SELECT 'Chris' as FirstName, 'Ashton' as LastName, CAST(195000. AS money) AS SalesYear2009, CAST(205000. AS money) AS SalesYear2008  
    UNION SELECT 'Pongsiri' as FirstName, 'Hirunyanitiwatna' as LastName, CAST(175000. AS money) AS SalesYear2009, CAST(215000. AS money) AS SalesYear2008  
    UNION SELECT 'Brian' as FirstName, 'Burke' as LastName, CAST(187000. AS money) AS SalesYear2009, CAST(207000. AS money) AS SalesYear2008  
    ```  
  
8.  <span data-ttu-id="b7957-147">（可选）单击“运行”按钮 (!)，查看要用于图表的数据\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b7957-147">(Optional) Click the Run button (**!**) to see the data your chart will be based on.</span></span>  
  
9. <span data-ttu-id="b7957-148">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="b7957-148">Click **Next**.</span></span>  
  
##  <a name="2-choose-the-chart-type"></a><a name="ChartType"></a><span data-ttu-id="b7957-149">2. 选择图表类型</span><span class="sxs-lookup"><span data-stu-id="b7957-149">2. Choose the Chart Type</span></span>  
 <span data-ttu-id="b7957-150">可以从各种预定义的图表类型中进行选择。</span><span class="sxs-lookup"><span data-stu-id="b7957-150">You can choose from a variety of predefined chart types.</span></span>  
  
#### <a name="to-add-a-column-chart"></a><span data-ttu-id="b7957-151">添加柱形图</span><span class="sxs-lookup"><span data-stu-id="b7957-151">To add a column chart</span></span>  
  
1.  <span data-ttu-id="b7957-152">在“选择图表类型”页上，柱形图为默认图表类型\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b7957-152">On the **Choose a chart type** page, the column chart is the default chart type.</span></span>  
  
2.  <span data-ttu-id="b7957-153">单击“条形图”，然后单击“下一步”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b7957-153">Click **Bar**, and then click **Next**.</span></span>  
  
     <span data-ttu-id="b7957-154">在 "**排列图表字段**" 页上，"**可用字段**" 窗格中有4个字段： FirstName、LastName、SalesYear2009 和 SalesYear2008。</span><span class="sxs-lookup"><span data-stu-id="b7957-154">On the **Arrange chart fields** page, there are four fields in the **Available fields** pane: FirstName, LastName, SalesYear2009, and SalesYear2008.</span></span>  
  
3.  <span data-ttu-id="b7957-155">将 LastName 拖动到“类别”窗格。</span><span class="sxs-lookup"><span data-stu-id="b7957-155">Drag LastName to the Categories pane.</span></span>  
  
4.  <span data-ttu-id="b7957-156">将 SalesYear2009 拖动到“值”窗格。</span><span class="sxs-lookup"><span data-stu-id="b7957-156">Drag SalesYear2009 to the Values pane.</span></span> <span data-ttu-id="b7957-157">SalesYear2009 表示每个销售人员在 2009 年的销售总额。</span><span class="sxs-lookup"><span data-stu-id="b7957-157">SalesYear2009 represents the sales amount for each salesperson for the year 2009.</span></span> <span data-ttu-id="b7957-158">“值”窗格显示 `[Sum(SalesYear2009)]` ，因为该图表显示的是每个产品的销售总额。</span><span class="sxs-lookup"><span data-stu-id="b7957-158">The Values pane displays `[Sum(SalesYear2009)]` because the chart displays the aggregate for each product.</span></span>  
  
5.  <span data-ttu-id="b7957-159">将 SalesYear2008 拖动到 SalesYear2009 下的“值”窗格。</span><span class="sxs-lookup"><span data-stu-id="b7957-159">Drag SalesYear2008 to the Values pane under SalesYear2009.</span></span> <span data-ttu-id="b7957-160">SalesYear2008 表示每个销售人员在 2008 年的销售总额。</span><span class="sxs-lookup"><span data-stu-id="b7957-160">SalesYear2008 represents the sales amount for each salesperson for the year 2008.</span></span>  
  
6.  <span data-ttu-id="b7957-161">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="b7957-161">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="b7957-162">在 "**选择样式**" 页上的 "样式" 窗格中，选择样式。</span><span class="sxs-lookup"><span data-stu-id="b7957-162">On the **Choose a style** page, in the Styles pane, select a style.</span></span>  
  
     <span data-ttu-id="b7957-163">样式指定字形、颜色集和边框样式。</span><span class="sxs-lookup"><span data-stu-id="b7957-163">A style specifies a font style, a set of colors, and a border style.</span></span> <span data-ttu-id="b7957-164">选择样式时，“预览”窗格将显示具有该样式的图表的示例。</span><span class="sxs-lookup"><span data-stu-id="b7957-164">When you select a style, the Preview pane displays a sample of the chart with that style.</span></span>  
  
8.  <span data-ttu-id="b7957-165">单击“完成”。</span><span class="sxs-lookup"><span data-stu-id="b7957-165">Click **Finish**.</span></span>  
  
     <span data-ttu-id="b7957-166">图表将添加到设计图面中。</span><span class="sxs-lookup"><span data-stu-id="b7957-166">The chart is added to the design surface.</span></span>  
  
9. <span data-ttu-id="b7957-167">单击图表以显示图表控点。</span><span class="sxs-lookup"><span data-stu-id="b7957-167">Click the chart to display the chart handles.</span></span> <span data-ttu-id="b7957-168">拖动该图表的右下角以扩大该图表。</span><span class="sxs-lookup"><span data-stu-id="b7957-168">Drag the bottom-right corner of the chart to increase the size of the chart.</span></span>  
  
10. <span data-ttu-id="b7957-169">单击 **“运行”** 以预览报表。</span><span class="sxs-lookup"><span data-stu-id="b7957-169">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="b7957-170">报表将显示每个销售人员在 2008 和 2009 年度销售情况的条形图。</span><span class="sxs-lookup"><span data-stu-id="b7957-170">The report displays the bar chart for sales for each sales person for the years 2008 and 2009.</span></span> <span data-ttu-id="b7957-171">条形图的长度对应于总销售额。</span><span class="sxs-lookup"><span data-stu-id="b7957-171">The length of the bar corresponds to the sales total.</span></span>  
  
##  <a name="3-modify-the-display-of-names-on-the-vertical-axis"></a><a name="AllValues"></a><span data-ttu-id="b7957-172">3. 修改垂直轴上的显示名称</span><span class="sxs-lookup"><span data-stu-id="b7957-172">3. Modify the Display of Names on the Vertical Axis</span></span>  
 <span data-ttu-id="b7957-173">默认情况下，垂直轴上只显示某些值。</span><span class="sxs-lookup"><span data-stu-id="b7957-173">By default, only some of the values on the vertical axis appear.</span></span> <span data-ttu-id="b7957-174">您可以更改图表以显示所有类别。</span><span class="sxs-lookup"><span data-stu-id="b7957-174">You can change the chart to display all categories.</span></span>  
  
#### <a name="to-display-all-sales-persons-along-the-category-axis-of-a-bar-chart"></a><span data-ttu-id="b7957-175">沿条形图的类别轴显示所有销售人员</span><span class="sxs-lookup"><span data-stu-id="b7957-175">To display all sales persons along the category axis of a bar chart</span></span>  
  
1.  <span data-ttu-id="b7957-176">切换到报表设计视图。</span><span class="sxs-lookup"><span data-stu-id="b7957-176">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="b7957-177">右键单击垂直轴，然后单击 "**垂直轴属性**"。</span><span class="sxs-lookup"><span data-stu-id="b7957-177">Right-click the vertical axis, and then click **Vertical Axis Properties**.</span></span>  
  
3.  <span data-ttu-id="b7957-178">在“轴范围和间隔”下的“间隔”框中，键入 1\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b7957-178">Under **Axis range and interval**, in the **Interval** box, type **1**.</span></span>  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="b7957-179">右键单击垂直**轴标题**，然后取消选中 "**显示轴标题**" 复选框。</span><span class="sxs-lookup"><span data-stu-id="b7957-179">Right-click the vertical **Axis Title** and clear the **Show Axis Title** check box.</span></span>  
  
6.  <span data-ttu-id="b7957-180">单击 **“运行”** 以预览报表。</span><span class="sxs-lookup"><span data-stu-id="b7957-180">Click **Run** to preview the report.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b7957-181">如果无法阅读垂直轴上的销售人员姓名，则可以增加图表的高度，或更改轴标签的格式选项。</span><span class="sxs-lookup"><span data-stu-id="b7957-181">If you cannot read the salesperson names on the vertical axis, you can make your chart taller or change the formatting options for the axis labels.</span></span>  
  
###  <a name="display-last-name-and-first-name-on-vertical-axis"></a><a name="CategoryExpression"></a><span data-ttu-id="b7957-182">在垂直轴上显示姓氏和名字</span><span class="sxs-lookup"><span data-stu-id="b7957-182">Display Last Name and First Name on Vertical Axis</span></span>  
 <span data-ttu-id="b7957-183">可以更改类别表达式以将每个销售人员的姓氏包含在名字之后。</span><span class="sxs-lookup"><span data-stu-id="b7957-183">You can change the category expression to include last name followed by first name of each sales person.</span></span>  
  
##### <a name="to-change-the-category-expression"></a><span data-ttu-id="b7957-184">更改类别表达式</span><span class="sxs-lookup"><span data-stu-id="b7957-184">To change the category expression</span></span>  
  
1.  <span data-ttu-id="b7957-185">切换到报表设计视图。</span><span class="sxs-lookup"><span data-stu-id="b7957-185">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="b7957-186">双击图表以显示“图表数据”窗格\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b7957-186">Double-click the chart to display the **Chart Data** pane.</span></span>  
  
3.  <span data-ttu-id="b7957-187">在“类别组”区域中右键单击 [LastName]，然后单击“类别组属性”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b7957-187">In the **Category Groups** area, right-click [LastName], and then click **Category Group Properties**.</span></span>  
  
4.  <span data-ttu-id="b7957-188">在“标签”中，单击表达式 (Fx) 按钮。</span><span class="sxs-lookup"><span data-stu-id="b7957-188">In Label, click the expression (Fx) button.</span></span>  
  
5.  <span data-ttu-id="b7957-189">键入以下表达式： `=Fields!LastName.Value & ", " & Fields!FirstName.Value`</span><span class="sxs-lookup"><span data-stu-id="b7957-189">Type the following expression: `=Fields!LastName.Value & ", " & Fields!FirstName.Value`</span></span>  
  
     <span data-ttu-id="b7957-190">此表达式将连接姓氏、逗号和名字。</span><span class="sxs-lookup"><span data-stu-id="b7957-190">This expression concatenates the last name, a comma, and the first name.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
8.  <span data-ttu-id="b7957-191">单击 **“运行”** 以预览报表。</span><span class="sxs-lookup"><span data-stu-id="b7957-191">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="b7957-192">如果在运行报表时没有显示名字，则您可以手动刷新数据。</span><span class="sxs-lookup"><span data-stu-id="b7957-192">If the first names do not appear when you run the report, you can refresh the data manually.</span></span> <span data-ttu-id="b7957-193">在仍处于预览模式时，在“导航”组的“运行”选项卡上，单击“刷新”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b7957-193">While still in preview mode, on the **Run** tab in the **Navigation** group, click **Refresh**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b7957-194">如果无法阅读垂直轴上的销售人员姓名，则可以增加图表的高度，或更改轴标签的格式选项。</span><span class="sxs-lookup"><span data-stu-id="b7957-194">If you cannot read the salesperson names on the vertical axis, you can make your chart taller or change the formatting options for the axis labels.</span></span>  
  
##  <a name="4-change-the-sort-order-for-names-on-the-vertical-axis"></a><a name="Sort"></a><span data-ttu-id="b7957-195">4. 更改垂直轴上的名称的排序顺序</span><span class="sxs-lookup"><span data-stu-id="b7957-195">4. Change the Sort Order for Names on the Vertical Axis</span></span>  
 <span data-ttu-id="b7957-196">当您对图表中的数据进行排序时，您是在更改类别轴上的值的顺序。</span><span class="sxs-lookup"><span data-stu-id="b7957-196">When you sort the data on a chart, you are changing the order of values on the category axis.</span></span>  
  
#### <a name="to-sort-the-names-in-alphabetical-order-on-the-bar-chart"></a><span data-ttu-id="b7957-197">按字母顺序对条形图中的姓名进行排序</span><span class="sxs-lookup"><span data-stu-id="b7957-197">To sort the names in alphabetical order on the bar chart</span></span>  
  
1.  <span data-ttu-id="b7957-198">切换到报表设计视图。</span><span class="sxs-lookup"><span data-stu-id="b7957-198">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="b7957-199">双击图表以显示“图表数据”窗格\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b7957-199">Double-click the chart to display the **Chart Data** pane.</span></span>  
  
3.  <span data-ttu-id="b7957-200">在“类别组”区域中右键单击 [LastName]，然后单击“类别组属性”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b7957-200">In the **Category Groups** area, right-click [LastName], and then click **Category Group Properties**.</span></span>  
  
4.  <span data-ttu-id="b7957-201">单击 **“排序”**。</span><span class="sxs-lookup"><span data-stu-id="b7957-201">Click **Sorting**.</span></span> <span data-ttu-id="b7957-202">“更改排序选项”页将显示排序表达式的列表\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b7957-202">The **Change sorting options** page displays a list of sort expressions.</span></span> <span data-ttu-id="b7957-203">默认情况下，此列表具有一个与原始类别组表达式相同的排序表达式。</span><span class="sxs-lookup"><span data-stu-id="b7957-203">By default, this list has one sort expression that is the same as the original category group expression.</span></span>  
  
5.  <span data-ttu-id="b7957-204">在 "排序依据" 中，单击表达式 (**Fx**) "按钮。</span><span class="sxs-lookup"><span data-stu-id="b7957-204">In Sort by, click the expression (**Fx**) button.</span></span>  
  
6.  <span data-ttu-id="b7957-205">键入以下表达式： `=Fields!LastName.Value & ", " & Fields!FirstName.Value`</span><span class="sxs-lookup"><span data-stu-id="b7957-205">Type the following expression: `=Fields!LastName.Value & ", " & Fields!FirstName.Value`</span></span>  
  
7.  <span data-ttu-id="b7957-206">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="b7957-206">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="b7957-207">返回 "**类别组属性**" 页，在 "**顺序**" 下拉列表中，选择 " **Z 到 A**"。这将选择反向字母顺序，以便按从上到下的顺序显示姓名。</span><span class="sxs-lookup"><span data-stu-id="b7957-207">Back on the **Category Group Properties** page, in the **Order** drop-down list, select **Z to A**. This selects reverse alphabetical order so that the names appear in order from top to bottom.</span></span>  
  
9. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
10. <span data-ttu-id="b7957-208">单击 **“运行”** 以预览报表。</span><span class="sxs-lookup"><span data-stu-id="b7957-208">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="b7957-209">水平轴上的名称按逆序排序， **Alerca**位于顶部，而**Zeng**位于底部。</span><span class="sxs-lookup"><span data-stu-id="b7957-209">The names on the horizontal axis are sorted in reverse order, with **Alerca** at the top and **Zeng** at the bottom.</span></span>  
  
##  <a name="5-move-the-legend"></a><a name="Legend"></a><span data-ttu-id="b7957-210">5. 移动图例</span><span class="sxs-lookup"><span data-stu-id="b7957-210">5. Move the Legend</span></span>  
 <span data-ttu-id="b7957-211">为了提高图表值的可读性，可能需要移动图表图例。</span><span class="sxs-lookup"><span data-stu-id="b7957-211">To improve the readability of the chart values, you might want to move the chart legend.</span></span> <span data-ttu-id="b7957-212">例如，在水平显示图条的条形图中，可以更改图例的位置，将其放置在图表区的上方或下方。</span><span class="sxs-lookup"><span data-stu-id="b7957-212">For example, in a bar chart where bars are shown horizontally, you can change the position of the legend so that it is above or below the chart area.</span></span> <span data-ttu-id="b7957-213">这可为图条提供更大的水平空间。</span><span class="sxs-lookup"><span data-stu-id="b7957-213">This gives more horizontal space to the bars.</span></span>  
  
#### <a name="to-display-the-legend-below-the-chart-area-of-a-bar-chart"></a><span data-ttu-id="b7957-214">在条形图的图表区下方显示图例</span><span class="sxs-lookup"><span data-stu-id="b7957-214">To display the legend below the chart area of a bar chart</span></span>  
  
1.  <span data-ttu-id="b7957-215">切换到报表设计视图。</span><span class="sxs-lookup"><span data-stu-id="b7957-215">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="b7957-216">右键单击图表上的图例。</span><span class="sxs-lookup"><span data-stu-id="b7957-216">Right-click the legend on the chart.</span></span>  
  
3.  <span data-ttu-id="b7957-217">选择“图例属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b7957-217">Select **Legend Properties**.</span></span>  
  
4.  <span data-ttu-id="b7957-218">对于“图例位置”，请选择其他位置\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b7957-218">For **Legend position**, select a different position.</span></span> <span data-ttu-id="b7957-219">例如，将图例位置设置为底部中间。</span><span class="sxs-lookup"><span data-stu-id="b7957-219">For example, set the position to the middle bottom option.</span></span>  
  
     <span data-ttu-id="b7957-220">如果将图例置于图表的顶部或底部，则图例的布局将会从垂直改为水平。</span><span class="sxs-lookup"><span data-stu-id="b7957-220">When the legend is placed at the top or bottom of a chart, the layout of the legend changes from vertical to horizontal.</span></span> <span data-ttu-id="b7957-221">可以从“布局”下拉列表中选择不同的布局\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b7957-221">You can select a different layout from the **Layout** drop-down list.</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="b7957-222">单击 **“运行”** 以预览报表。</span><span class="sxs-lookup"><span data-stu-id="b7957-222">Click **Run** to preview the report.</span></span>  
  
##  <a name="6-title-the-chart"></a><a name="ChartTitle"></a><span data-ttu-id="b7957-223">6. 为图表标题</span><span class="sxs-lookup"><span data-stu-id="b7957-223">6. Title the Chart</span></span>  
  
#### <a name="to-change-the-chart-title-above-the-chart-area-of-a-bar-chart"></a><span data-ttu-id="b7957-224">更改条形图的图表区上方的图表标题</span><span class="sxs-lookup"><span data-stu-id="b7957-224">To change the chart title above the chart area of a bar chart</span></span>  
  
1.  <span data-ttu-id="b7957-225">切换到报表设计视图。</span><span class="sxs-lookup"><span data-stu-id="b7957-225">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="b7957-226">选择图表顶部的词语 "**图表标题**"，然后键入以下文本： " **2008" 和 "2009**" 的销售额。</span><span class="sxs-lookup"><span data-stu-id="b7957-226">Select the words **Chart Title** at the top of the chart, and then type the following text: **Sales for 2008 and 2009**.</span></span>  
  
3.  <span data-ttu-id="b7957-227">单击该文本的外部。</span><span class="sxs-lookup"><span data-stu-id="b7957-227">Click anywhere outside the text.</span></span>  
  
4.  <span data-ttu-id="b7957-228">单击 **“运行”** 以预览报表。</span><span class="sxs-lookup"><span data-stu-id="b7957-228">Click **Run** to preview the report.</span></span>  
  
##  <a name="7-format-and-label-the-horizontal-axis"></a><a name="Horizontal"></a><span data-ttu-id="b7957-229">7. 设置水平轴的格式和标签</span><span class="sxs-lookup"><span data-stu-id="b7957-229">7. Format and Label the Horizontal Axis</span></span>  
 <span data-ttu-id="b7957-230">默认情况下，水平轴采用常用格式显示值，将自动调整为适合图表的大小。</span><span class="sxs-lookup"><span data-stu-id="b7957-230">By default, the horizontal axis displays values in a general format that is automatically scaled to fit the size of the chart.</span></span>  
  
#### <a name="to-format-the-numbers-on-the-horizontal-axis"></a><span data-ttu-id="b7957-231">设置水平轴上数字的格式</span><span class="sxs-lookup"><span data-stu-id="b7957-231">To format the numbers on the horizontal axis</span></span>  
  
1.  <span data-ttu-id="b7957-232">切换到报表设计视图。</span><span class="sxs-lookup"><span data-stu-id="b7957-232">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="b7957-233">沿图表底部单击水平轴，以选择它。</span><span class="sxs-lookup"><span data-stu-id="b7957-233">Click the horizontal axis along the bottom of the chart to select it.</span></span>  
  
     <span data-ttu-id="b7957-234">在功能区上，在 "**主页**" 选项卡上的 "**数字**" 组中，单击 "**货币**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="b7957-234">On the ribbon, on the **Home** tab, in the **Number** group, click the **Currency** button.</span></span> <span data-ttu-id="b7957-235">水平轴标签将更改为货币。</span><span class="sxs-lookup"><span data-stu-id="b7957-235">The horizontal axis labels change to currency.</span></span>  
  
3.  <span data-ttu-id="b7957-236">（可选）删除小数位数。</span><span class="sxs-lookup"><span data-stu-id="b7957-236">(Optional) Remove the decimal digits.</span></span> <span data-ttu-id="b7957-237">在“货币”按钮附近，单击两次“减少小数位数”按钮\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b7957-237">Near the **Currency** button, click the **Decrease Decimal** button twice.</span></span>  
  
4.  <span data-ttu-id="b7957-238">右键单击水平轴，然后单击“水平轴属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b7957-238">Right-click the horizontal axis, and click **Horizontal Axis Properties**.</span></span>  
  
5.  <span data-ttu-id="b7957-239">在 "**数字**" 选项卡上，选择 "**以千为单位显示值"。**</span><span class="sxs-lookup"><span data-stu-id="b7957-239">On the **Number** tab, select **Show values in Thousands.**</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  <span data-ttu-id="b7957-240">右键单击 "**轴标题**"，然后单击 "**轴标题属性**"。</span><span class="sxs-lookup"><span data-stu-id="b7957-240">Right-click **Axis Title** and click **Axis Title Properties**.</span></span>  
  
8.  <span data-ttu-id="b7957-241">在 "**标题" 文本框**中，键入**Sales in 上千**，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="b7957-241">In the **Title text** box, type **Sales in thousands** and click **OK**.</span></span>  
  
9. <span data-ttu-id="b7957-242">单击 **“运行”** 以预览报表。</span><span class="sxs-lookup"><span data-stu-id="b7957-242">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="b7957-243">报表将在水平轴上以千为单位将销售额显示为货币，且没有小数位数。</span><span class="sxs-lookup"><span data-stu-id="b7957-243">The report displays the sales amount on the horizontal axis as currency in thousands, and has no decimal digits.</span></span>  
  
##  <a name="8-add-a-filter-to-display-the-top-five-values"></a><a name="Filter"></a><span data-ttu-id="b7957-244">8. 添加筛选器以显示前五个值</span><span class="sxs-lookup"><span data-stu-id="b7957-244">8. Add a Filter to Display the Top Five Values</span></span>  
 <span data-ttu-id="b7957-245">可以向图表添加筛选器，以指定数据集中哪些数据要包含于图表中或排除在图表外。</span><span class="sxs-lookup"><span data-stu-id="b7957-245">You can add a filter to the chart to specify which data from the dataset to include or exclude in the chart.</span></span>  
  
#### <a name="to-add-a-filter-and-display-the-top-five-values"></a><span data-ttu-id="b7957-246">添加筛选器并显示前五个值</span><span class="sxs-lookup"><span data-stu-id="b7957-246">To add a filter and display the top five values</span></span>  
  
1.  <span data-ttu-id="b7957-247">切换到报表设计视图。</span><span class="sxs-lookup"><span data-stu-id="b7957-247">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="b7957-248">双击图表以显示“图表数据”窗格\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b7957-248">Double-click the chart to display the **Chart Data** pane.</span></span>  
  
3.  <span data-ttu-id="b7957-249">在“类别组”区域中，右键单击 [LastName] 字段，然后单击“类别组属性”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b7957-249">In the **Category Groups** area, right-click the [LastName] field, and then click **Category Group Properties**.</span></span>  
  
4.  <span data-ttu-id="b7957-250">单击 **“筛选器”** 。</span><span class="sxs-lookup"><span data-stu-id="b7957-250">Click **Filters**.</span></span> <span data-ttu-id="b7957-251">“更改筛选器”页可以显示筛选器表达式的列表\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b7957-251">The **Change filters** page can display a list of filter expressions.</span></span> <span data-ttu-id="b7957-252">默认情况下，此列表为空。</span><span class="sxs-lookup"><span data-stu-id="b7957-252">By default, this list is empty.</span></span>  
  
5.  <span data-ttu-id="b7957-253">单击“添加”。</span><span class="sxs-lookup"><span data-stu-id="b7957-253">Click **Add**.</span></span> <span data-ttu-id="b7957-254">此时将显示一个新的空白筛选器。</span><span class="sxs-lookup"><span data-stu-id="b7957-254">A new blank filter appears.</span></span>  
  
6.  <span data-ttu-id="b7957-255">在 "**表达式**" 中，键入 **[Sum (SalesYear2009) ]**。</span><span class="sxs-lookup"><span data-stu-id="b7957-255">In **Expression**, type **[Sum(SalesYear2009)]**.</span></span> <span data-ttu-id="b7957-256">此时将创建基础表达式 `=Sum(Fields!SalesYear2009.Value)`，可以查看是否单击了“fx”按钮\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b7957-256">This creates the underlying expression `=Sum(Fields!SalesYear2009.Value)`, which you can see if you click the **fx** button.</span></span>  
  
7.  <span data-ttu-id="b7957-257">验证确保数据类型是“文本”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b7957-257">Verify that the data type is **Text**.</span></span>  
  
8.  <span data-ttu-id="b7957-258">在“运算符”中，从下拉列表中选择“前 N 个”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b7957-258">In **Operator**, select **Top N** from the drop-down list.</span></span>  
  
9. <span data-ttu-id="b7957-259">在“值”中，键入以下表达式：=5\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="b7957-259">In **Value**, type the following expression: **=5**</span></span>  
  
10. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
11. <span data-ttu-id="b7957-260">单击 **“运行”** 以预览报表。</span><span class="sxs-lookup"><span data-stu-id="b7957-260">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="b7957-261">如果在运行报表时没有对结果进行筛选，则可以手动刷新数据。</span><span class="sxs-lookup"><span data-stu-id="b7957-261">If the results are not filtered when you run the report, you can refresh the data manually.</span></span> <span data-ttu-id="b7957-262">在“导航”组的“运行”选项卡上，单击“刷新”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b7957-262">On the **Run** tab in the **Navigation** group, click **Refresh**.</span></span>  
  
 <span data-ttu-id="b7957-263">图表将显示 2009 年销售数据中前五位销售人员的姓名。</span><span class="sxs-lookup"><span data-stu-id="b7957-263">The chart shows the top five salesperson names from the 2009 sales data.</span></span>  
  
##  <a name="9-add-a-report-title"></a><a name="Title"></a><span data-ttu-id="b7957-264">9. 添加报表标题</span><span class="sxs-lookup"><span data-stu-id="b7957-264">9. Add a Report Title</span></span>  
  
#### <a name="to-add-a-report-title"></a><span data-ttu-id="b7957-265">添加报表标题</span><span class="sxs-lookup"><span data-stu-id="b7957-265">To add a report title</span></span>  
  
1.  <span data-ttu-id="b7957-266">在设计图面上，单击“单击以添加标题”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b7957-266">On the design surface, click **Click to add title**.</span></span>  
  
2.  <span data-ttu-id="b7957-267">键入**Sales Bar Chart**，按 enter，然后键入**2009 的前五个卖方**，如下所示：</span><span class="sxs-lookup"><span data-stu-id="b7957-267">Type **Sales Bar Chart**, press ENTER, and then type **Top Five Sellers for 2009**, so it looks like this:</span></span>  
  
     <span data-ttu-id="b7957-268">**Sales Bar Chart**</span><span class="sxs-lookup"><span data-stu-id="b7957-268">**Sales Bar Chart**</span></span>  
  
     <span data-ttu-id="b7957-269">**Top Five Sellers for 2009**</span><span class="sxs-lookup"><span data-stu-id="b7957-269">**Top Five Sellers for 2009**</span></span>  
  
3.  <span data-ttu-id="b7957-270">选择 **Sales Bar Chart**，并单击“加粗”\*\*\*\* 按钮。</span><span class="sxs-lookup"><span data-stu-id="b7957-270">Select **Sales Bar Chart**, and click the **Bold** button.</span></span>  
  
4.  <span data-ttu-id="b7957-271">选择**2009 的前五个卖方**，然后在 "**主页**" 选项卡的 "**字体**" 部分中，将字号设置为**10**。</span><span class="sxs-lookup"><span data-stu-id="b7957-271">Select **Top Five Sellers for 2009**, and in the **Font** section on the **Home** tab, set the font size to **10**.</span></span>  
  
5.  <span data-ttu-id="b7957-272">（可选）您可能需要使“标题”文本框更高一些，以容纳两行文本。</span><span class="sxs-lookup"><span data-stu-id="b7957-272">(Optional) You may need to make the Title text box taller to accommodate the two lines of text.</span></span>  
  
     <span data-ttu-id="b7957-273">此标题将显示在报表的顶部。</span><span class="sxs-lookup"><span data-stu-id="b7957-273">This title will appear at the top of the report.</span></span> <span data-ttu-id="b7957-274">未定义页标头时，报表体顶部的项就等同于报表标头。</span><span class="sxs-lookup"><span data-stu-id="b7957-274">When there is no page header defined, items at the top of the report body are the equivalent of a report header.</span></span>  
  
6.  <span data-ttu-id="b7957-275">单击 **“运行”** 以预览报表。</span><span class="sxs-lookup"><span data-stu-id="b7957-275">Click **Run** to preview the report.</span></span>  
  
##  <a name="10-save-the-report"></a><a name="Save"></a><span data-ttu-id="b7957-276">10. 保存报表</span><span class="sxs-lookup"><span data-stu-id="b7957-276">10. Save the Report</span></span>  
  
#### <a name="to-save-the-report"></a><span data-ttu-id="b7957-277">保存报表</span><span class="sxs-lookup"><span data-stu-id="b7957-277">To save the report</span></span>  
  
1.  <span data-ttu-id="b7957-278">切换到报表设计视图。</span><span class="sxs-lookup"><span data-stu-id="b7957-278">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="b7957-279">从 **“报表生成器”** 按钮，单击 **“另存为”**。</span><span class="sxs-lookup"><span data-stu-id="b7957-279">From the **Report Builder** button, click **Save As**.</span></span>  
  
3.  <span data-ttu-id="b7957-280">在“名称”中，键入 Sales Bar Chart\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b7957-280">In **Name**, type **Sales Bar Chart**.</span></span>  
  
4.  <span data-ttu-id="b7957-281">单击“ **保存**”。</span><span class="sxs-lookup"><span data-stu-id="b7957-281">Click **Save**.</span></span>  
  
 <span data-ttu-id="b7957-282">报表将保存在报表服务器上。</span><span class="sxs-lookup"><span data-stu-id="b7957-282">Your report is saved on the report server.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="b7957-283">后续步骤</span><span class="sxs-lookup"><span data-stu-id="b7957-283">Next Steps</span></span>  
 <span data-ttu-id="b7957-284">您已成功完成“向报表添加条形图”教程的学习。</span><span class="sxs-lookup"><span data-stu-id="b7957-284">You have successfully completed the Adding a Bar Chart to Your Report tutorial.</span></span> <span data-ttu-id="b7957-285">若要了解有关图表的详细信息，请参阅[图表（报表生成器和 SSRS）](report-design/charts-report-builder-and-ssrs.md)和[迷你图和数据条（报表生成器和 SSRS）](report-design/sparklines-and-data-bars-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="b7957-285">To learn more about charts, see [Charts &#40;Report Builder and SSRS&#41;](report-design/charts-report-builder-and-ssrs.md) and [Sparklines and Data Bars &#40;Report Builder and SSRS&#41;](report-design/sparklines-and-data-bars-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7957-286">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b7957-286">See Also</span></span>  
 <span data-ttu-id="b7957-287">[教程 &#40;报表生成器&#41;](report-builder-tutorials.md) </span><span class="sxs-lookup"><span data-stu-id="b7957-287">[Tutorials &#40;Report Builder&#41;](report-builder-tutorials.md) </span></span>  
 [<span data-ttu-id="b7957-288">SQL Server 2014 中的报表生成器</span><span class="sxs-lookup"><span data-stu-id="b7957-288">Report Builder in SQL Server 2014</span></span>](report-builder/report-builder-in-sql-server-2016.md)  
  
  
