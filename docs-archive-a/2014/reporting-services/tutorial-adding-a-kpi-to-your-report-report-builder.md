---
title: 教程：向报表添加 KPI（报表生成器）| Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 1bf77859-0b33-4f40-abaf-ebeeb6ebb1f8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 405978721068583597adf5c4257978a222121078
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691542"
---
# <a name="tutorial-adding-a-kpi-to-your-report-report-builder"></a><span data-ttu-id="4b076-102">教程：向报表添加 KPI（报表生成器）</span><span class="sxs-lookup"><span data-stu-id="4b076-102">Tutorial: Adding a KPI to Your Report (Report Builder)</span></span>
  <span data-ttu-id="4b076-103">关键绩效指标 (KPI) 是对业务具有重大意义的可测量值。</span><span class="sxs-lookup"><span data-stu-id="4b076-103">A key performance indicator (KPI) is a measurable value that has business significance.</span></span> <span data-ttu-id="4b076-104">本教程教您如何在报表中包含一个 KPI。</span><span class="sxs-lookup"><span data-stu-id="4b076-104">This tutorial teaches you how to include a (KPI) in a report.</span></span> <span data-ttu-id="4b076-105">在本教程中，按产品子类别进行的销售汇总为 KPI。</span><span class="sxs-lookup"><span data-stu-id="4b076-105">In this scenario, the sales summary by product subcategories is the KPI.</span></span> <span data-ttu-id="4b076-106">可以使用颜色、仪表和指示器来显示 KPI 的当前状态。</span><span class="sxs-lookup"><span data-stu-id="4b076-106">The current state of the KPI is shown by using colors, gauges, and indicators.</span></span>  
  
 <span data-ttu-id="4b076-107">下图显示了将创建的报表。</span><span class="sxs-lookup"><span data-stu-id="4b076-107">The following illustration shows the report that you will create.</span></span>  
  
 <span data-ttu-id="4b076-108">![rs_AddKPITutorial](../../2014/tutorials/media/rs-addkpitutorial.gif "rs_AddKPITutorial")</span><span class="sxs-lookup"><span data-stu-id="4b076-108">![rs_AddKPITutorial](../../2014/tutorials/media/rs-addkpitutorial.gif "rs_AddKPITutorial")</span></span>  
  
##  <a name="what-you-will-learn"></a><a name="BackToTop"></a><span data-ttu-id="4b076-109">你将学习的内容</span><span class="sxs-lookup"><span data-stu-id="4b076-109">What You Will Learn</span></span>  
 <span data-ttu-id="4b076-110">在本教程中，将学习如何通过基于单元值设置表单元的背景色来添加 KPI，以及添加和配置仪表和指示器。</span><span class="sxs-lookup"><span data-stu-id="4b076-110">In this tutorial, you will learn to add a KPI by setting the background color of table cells based on cell value and add and configure a gauge and an indicator.</span></span> <span data-ttu-id="4b076-111">还将学习如何编写设置表单元的背景色的表达式。</span><span class="sxs-lookup"><span data-stu-id="4b076-111">You also learn to write the expression that sets the background color of the table cells.</span></span>  
  
 <span data-ttu-id="4b076-112">本教程包含下列过程：</span><span class="sxs-lookup"><span data-stu-id="4b076-112">This tutorial contains the following procedures:</span></span>  
  
1.  [<span data-ttu-id="4b076-113">使用表向导或矩阵向导创建表报表和数据集</span><span class="sxs-lookup"><span data-stu-id="4b076-113">Create a Table Report and Dataset from the Table or Matrix Wizard</span></span>](#Table)  
  
2.  [<span data-ttu-id="4b076-114">使用表或矩阵向导组织数据并选择布局和样式</span><span class="sxs-lookup"><span data-stu-id="4b076-114">Organize Data, Choose Layout, and Style from the Table or Matrix Wizard</span></span>](#CompleteWizard)  
  
3.  [<span data-ttu-id="4b076-115">使用背景色显示 KPI</span><span class="sxs-lookup"><span data-stu-id="4b076-115">Use Background Colors to Display a KPI</span></span>](#BackgroundColors)  
  
4.  [<span data-ttu-id="4b076-116">使用仪表显示 KPI</span><span class="sxs-lookup"><span data-stu-id="4b076-116">Display a KPI by Using a Gauge</span></span>](#Gauge)  
  
5.  [<span data-ttu-id="4b076-117">使用指示器显示 KPI</span><span class="sxs-lookup"><span data-stu-id="4b076-117">Display a KPI by Using an Indicator</span></span>](#Indicator)  
  
6.  [<span data-ttu-id="4b076-118">添加报表标题</span><span class="sxs-lookup"><span data-stu-id="4b076-118">Add a Report Title</span></span>](#Title)  
  
7.  [<span data-ttu-id="4b076-119">保存报表</span><span class="sxs-lookup"><span data-stu-id="4b076-119">Save the Report</span></span>](#Save)  
  
> [!NOTE]  
>  <span data-ttu-id="4b076-120">在本教程中，将向导的多个步骤合并为两个过程：一个用于创建数据集，一个用于创建表。</span><span class="sxs-lookup"><span data-stu-id="4b076-120">In this tutorial, the steps for the wizard are consolidated into two procedures: one to create the dataset and one to create a table.</span></span> <span data-ttu-id="4b076-121">有关如何浏览到报表服务器、选择数据源、创建数据集和运行向导的分步说明，请参阅本系列的第一个教程：[教程：创建基本表报表（报表生成器）](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="4b076-121">For step-by-step instructions about how to browse to a report server, choose a data source, create a dataset, and run the wizard, see the first tutorial in this series: [Tutorial: Creating a Basic Table Report &#40;Report Builder&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md).</span></span>  
  
 <span data-ttu-id="4b076-122">本教程的预计学时：15 分钟。</span><span class="sxs-lookup"><span data-stu-id="4b076-122">Estimated time to complete this tutorial: 15 minutes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b076-123">要求</span><span class="sxs-lookup"><span data-stu-id="4b076-123">Requirements</span></span>  
 <span data-ttu-id="4b076-124">有关要求的详细信息，请参阅[教程先决条件（报表生成器）](../reporting-services/report-builder-tutorials.md)。</span><span class="sxs-lookup"><span data-stu-id="4b076-124">For more information about requirements, see [Prerequisites for Tutorials &#40;Report Builder&#41;](../reporting-services/report-builder-tutorials.md).</span></span>  
  
##  <a name="1-create-a-table-report-and-dataset-from-the-table-or-matrix-wizard"></a><a name="Table"></a><span data-ttu-id="4b076-125">1. 使用表或矩阵向导创建表报表和数据集</span><span class="sxs-lookup"><span data-stu-id="4b076-125">1. Create a Table Report and Dataset from the Table or Matrix Wizard</span></span>  
 <span data-ttu-id="4b076-126">从 "**入门**" 对话框中，选择共享数据源，创建嵌入数据集，并在表中显示数据。</span><span class="sxs-lookup"><span data-stu-id="4b076-126">From the **Getting Started** dialog box, choose a shared data source, create an embedded dataset, and display the data in a table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4b076-127">在本教程中，由于查询包含了数据值，因此它不需要外部数据源。</span><span class="sxs-lookup"><span data-stu-id="4b076-127">In this tutorial, the query contains the data values, so that it does not need an external data source.</span></span> <span data-ttu-id="4b076-128">这样，查询就会非常长。</span><span class="sxs-lookup"><span data-stu-id="4b076-128">This makes the query quite long.</span></span> <span data-ttu-id="4b076-129">在业务环境中，查询不会包含数据。</span><span class="sxs-lookup"><span data-stu-id="4b076-129">In a business environment, a query would not contain the data.</span></span> <span data-ttu-id="4b076-130">本教程中的查询仅供学习使用。</span><span class="sxs-lookup"><span data-stu-id="4b076-130">This is for learning purposes only.</span></span>  
  
#### <a name="to-create-a-new-table"></a><span data-ttu-id="4b076-131">创建新表</span><span class="sxs-lookup"><span data-stu-id="4b076-131">To create a new table</span></span>  
  
1.  <span data-ttu-id="4b076-132">单击 **“开始”**，依次指向 **“程序”**、 **Microsoft SQL Server 2012 Report Builder**，再单击 **“报表生成器”**。</span><span class="sxs-lookup"><span data-stu-id="4b076-132">Click **Start**, point to **Programs**, point to **Microsoft SQL Server 2012 Report Builder**, and then click **Report Builder**.</span></span>  
  
     <span data-ttu-id="4b076-133">此时将显示 "**入门**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="4b076-133">The **Getting Started** dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4b076-134">如果未显示 "**入门**" 对话框，请在 "报表生成器" 按钮中单击 "**新建**"。</span><span class="sxs-lookup"><span data-stu-id="4b076-134">If the **Getting Started** dialog box does not appear, from the Report Builder button, click **New**.</span></span>  
  
2.  <span data-ttu-id="4b076-135">在左窗格中，确认已选中 **“新建报表”** 。</span><span class="sxs-lookup"><span data-stu-id="4b076-135">In the left pane, verify that **New Report** is selected.</span></span>  
  
3.  <span data-ttu-id="4b076-136">在右窗格中，单击“表或矩阵向导”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4b076-136">In the right pane, click **Table or Matrix Wizard**.</span></span>  
  
4.  <span data-ttu-id="4b076-137">在“选择数据集”页上，单击“创建数据集”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4b076-137">On the Choose a dataset page, click **Create a dataset**.</span></span>  
  
5.  <span data-ttu-id="4b076-138">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="4b076-138">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="4b076-139">在 "**选择数据源的连接**" 页上，选择现有数据源或浏览到 Report Server 并选择一个数据源。</span><span class="sxs-lookup"><span data-stu-id="4b076-139">On the **Choose a connection to a data source** page, select an existing data source or browse to the report server and select a data source.</span></span> <span data-ttu-id="4b076-140">如果没有可用数据源，或无权访问报表服务器，可以改用嵌入数据源。</span><span class="sxs-lookup"><span data-stu-id="4b076-140">If there no data source is available or you do not have access to a report server, you can use an embedded data source instead.</span></span> <span data-ttu-id="4b076-141">有关详细信息，请参阅[教程：创建基本表报表（报表生成器）](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="4b076-141">For more information, see [Tutorial: Creating a Basic Table Report &#40;Report Builder&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md).</span></span>  
  
7.  <span data-ttu-id="4b076-142">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="4b076-142">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="4b076-143">在“设计查询”页上，单击“编辑为文本”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4b076-143">On the **Design a query** page, click **Edit as Text**.</span></span>  
  
9. <span data-ttu-id="4b076-144">复制并将以下查询粘贴到查询窗格中：</span><span class="sxs-lookup"><span data-stu-id="4b076-144">Copy and paste the following query into the query pane:</span></span>  
  
    ```  
    SELECT CAST('2009-01-05' AS date) as SalesDate, 'Accessories' as Subcategory,   
       'Carrying Case' as Product, CAST(16996.60 AS money) AS Sales, 68 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Accessories' as Subcategory,  
       'Tripod' as Product, CAST(1350.00 AS money) AS Sales, 18 as Quantity  
    UNION SELECT CAST('2009-01-11' AS date) as SalesDate, 'Accessories' as Subcategory,  
       'Lens Adapter' as Product, CAST(1147.50 AS money) AS Sales, 17 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Accessories' as Subcategory,  
       'Mini Battery Charger' as Product, CAST(1056.00 AS money) AS Sales, 44 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'Accessories' as Subcategory,  
       'Telephoto Conversion Lens' as Product, CAST(1380.00 AS money) AS Sales, 18 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,'Accessories' as Subcategory,    
       'USB Cable' as Product, CAST(780.00 AS money) AS Sales, 26 as Quantity  
    UNION SELECT CAST('2009-01-08' AS date) as SalesDate, 'Accessories' as Subcategory,   
       'Budget Movie-Maker' as Product, CAST(3798.00 AS money) AS Sales, 9 as Quantity  
    UNION SELECT CAST('2009-01-09' AS date) as SalesDate, 'Camcorders' as Subcategory,   
       'Business Videographer' as Product, CAST(10400.00 AS money) AS Sales, 13 as Quantity  
    UNION SELECT CAST('2009-01-10' AS date) as SalesDate, 'Camcorders' as Subcategory,   
       'Social Videographer' as Product, CAST(3000.00 AS money) AS Sales, 60 as Quantity  
    UNION SELECT CAST('2009-01-11' AS date) as SalesDate,  'Digital' as Subcategory,   
       'Advanced Digital' as Product, CAST(7234.50 AS money) AS Sales, 39 as Quantity  
    UNION SELECT CAST('2009-01-07' AS date) as SalesDate,  'Digital' as Subcategory,   
       'Compact Digital' as Product, CAST(10836.00 AS money) AS Sales, 84 as Quantity  
    UNION SELECT CAST('2009-01-08' AS date) as SalesDate,  'Digital' as Subcategory,   
       'Consumer Digital' as Product, CAST(2550.00 AS money) AS Sales, 17 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Digital' as Subcategory,   
       'Slim Digital' as Product, CAST(8357.80 AS money) AS Sales, 44 as Quantity  
    UNION SELECT CAST('2009-01-09' AS date) as SalesDate, 'Digital SLR' as Subcategory,   
       'SLR Camera 35mm' as Product, CAST(18530.00 AS money) AS Sales, 34 as Quantity  
    UNION SELECT CAST('2009-01-07' AS date) as SalesDate, 'Digital SLR' as Subcategory,   
       'SLR Camera' as Product, CAST(26576.00 AS money) AS Sales, 88 as Quantity  
    ```  
  
10. <span data-ttu-id="4b076-145">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="4b076-145">Click **Next**.</span></span>  
  
##  <a name="2-organize-data-choose-layout-and-style-from-the-table-or-matrix-wizard"></a><a name="CompleteWizard"></a><span data-ttu-id="4b076-146">2. 在表或矩阵向导中组织数据、选择布局和样式</span><span class="sxs-lookup"><span data-stu-id="4b076-146">2. Organize Data, Choose Layout, and Style from the Table or Matrix Wizard</span></span>  
 <span data-ttu-id="4b076-147">使用此向导可提供用于显示数据的起始设计。</span><span class="sxs-lookup"><span data-stu-id="4b076-147">Use the wizard to provide a starting design on which to display data.</span></span> <span data-ttu-id="4b076-148">此向导中的预览窗格可帮助您在完成表或矩阵设计之前将对数据进行分组的结果可视化。</span><span class="sxs-lookup"><span data-stu-id="4b076-148">The preview pane in the wizard helps you to visualize the result of grouping data before you complete the table or matrix design.</span></span>  
  
#### <a name="to-organize-data-into-groups-choose-a-layout-and-a-style"></a><span data-ttu-id="4b076-149">若要将数据组织到组中，请选择布局和样式</span><span class="sxs-lookup"><span data-stu-id="4b076-149">To organize data into groups, choose a layout and a style</span></span>  
  
1.  <span data-ttu-id="4b076-150">在“排列字段”页上，将 Product 拖到“值”中\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4b076-150">On the Arrange fields page, drag Product to **Values**.</span></span>  
  
2.  <span data-ttu-id="4b076-151">将 Quantity 拖到“值”中并将其置于 Product 下方\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4b076-151">Drag Quantity to **Values** and place below Product.</span></span>  
  
     <span data-ttu-id="4b076-152">将使用汇总数值字段的默认函数 Sum 函数对 Quantity 进行汇总。</span><span class="sxs-lookup"><span data-stu-id="4b076-152">Quantity is summarized with the Sum function, the default function to summarize numeric fields.</span></span>  
  
3.  <span data-ttu-id="4b076-153">将 Sales 拖到“值”中并将其放在 Quantity 下面\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4b076-153">Drag Sales to **Values** and place below Quantity.</span></span>  
  
     <span data-ttu-id="4b076-154">步骤 1、2 和 3 指定要在表中显示的数据。</span><span class="sxs-lookup"><span data-stu-id="4b076-154">Steps 1, 2, and 3 specify the data to display in the table.</span></span>  
  
4.  <span data-ttu-id="4b076-155">将 SalesDate 拖到“行组”\*\*\*\* 中。</span><span class="sxs-lookup"><span data-stu-id="4b076-155">Drag SalesDate to **Row groups**.</span></span>  
  
5.  <span data-ttu-id="4b076-156">将 Subcategory 拖到“行组”中并将其置于 SalesDate 下方\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4b076-156">Drag Subcategory to **Row groups** and place below SalesDate.</span></span>  
  
     <span data-ttu-id="4b076-157">步骤 4 和 5 首先按日期组织字段的值，然后按照该日期的所有销售组织字段的值。</span><span class="sxs-lookup"><span data-stu-id="4b076-157">Steps 4 and 5 organize the values for the fields first by date, and then by all sales for that date.</span></span>  
  
6.  <span data-ttu-id="4b076-158">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="4b076-158">Click **Next**.</span></span>  
  
     <span data-ttu-id="4b076-159">当您运行报表时，表将显示每个日期、每个日期的所有订单以及每个订单的所有产品、数量和销售额总计。</span><span class="sxs-lookup"><span data-stu-id="4b076-159">When you run the report, the table displays each date, all orders for each date, and all products, quantities, and sales totals for each order.</span></span>  
  
7.  <span data-ttu-id="4b076-160">在 "选择布局" 页的 "**选项**" 下，验证是否选择了 "**显示小计和总计**"。</span><span class="sxs-lookup"><span data-stu-id="4b076-160">On the Choose the Layout page, under **Options**, verify that **Show subtotals and grand totals** is selected.</span></span>  
  
8.  <span data-ttu-id="4b076-161">验证是否选择了“分块式，小计下方显示”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4b076-161">Verify that **Blocked, subtotal below** is selected.</span></span>  
  
9. <span data-ttu-id="4b076-162">清除“展开/折叠组”选项\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4b076-162">Clear the option **Expand/collapse groups**.</span></span>  
  
     <span data-ttu-id="4b076-163">在本教程中，创建的报表不会使用明细功能（用户可通过此功能来展开父组层次结构）来显示子组行和详细信息行。</span><span class="sxs-lookup"><span data-stu-id="4b076-163">In this tutorial, the report you create does not use the drilldown feature that lets a user expand a parent group hierarchy to display child group rows and detail rows.</span></span>  
  
10. <span data-ttu-id="4b076-164">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="4b076-164">Click **Next**.</span></span>  
  
11. <span data-ttu-id="4b076-165">在“选择样式”页的“样式”窗格中，选择样式。</span><span class="sxs-lookup"><span data-stu-id="4b076-165">On the Choose a Style page, in the Styles pane, select a style.</span></span>  
  
     <span data-ttu-id="4b076-166">已完成报表的图采用“海洋”样式显示报表。</span><span class="sxs-lookup"><span data-stu-id="4b076-166">The illustration of the completed report shows the report using the Ocean style.</span></span>  
  
12. <span data-ttu-id="4b076-167">单击“完成”。</span><span class="sxs-lookup"><span data-stu-id="4b076-167">Click **Finish**.</span></span>  
  
     <span data-ttu-id="4b076-168">表将添加到设计图面中。</span><span class="sxs-lookup"><span data-stu-id="4b076-168">The table is added to the design surface.</span></span> <span data-ttu-id="4b076-169">此表有五个列和五个行。</span><span class="sxs-lookup"><span data-stu-id="4b076-169">The table has five columns and five rows.</span></span> <span data-ttu-id="4b076-170">“行组”窗格显示三个行组：SalesDate、Subcategory 和 Details。</span><span class="sxs-lookup"><span data-stu-id="4b076-170">The Row Groups pane shows three row groups: SalesDate, Subcategory, and Details.</span></span> <span data-ttu-id="4b076-171">详细信息数据是由数据集查询检索的所有数据。</span><span class="sxs-lookup"><span data-stu-id="4b076-171">Detail data is all the data that is retrieved by the dataset query.</span></span>  
  
13. <span data-ttu-id="4b076-172">单击 **“运行”** 以预览报表。</span><span class="sxs-lookup"><span data-stu-id="4b076-172">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="4b076-173">对于在特定日期销售的每个产品，表显示产品名称、销售数量及销售额总计。</span><span class="sxs-lookup"><span data-stu-id="4b076-173">For each product that is sold on a specific date, the table displays the product name, the quantity sold, and the sales total.</span></span> <span data-ttu-id="4b076-174">此数据首先按销售日期组织，然后按子类别组织。</span><span class="sxs-lookup"><span data-stu-id="4b076-174">The data is organized first by sales date and then by subcategory.</span></span>  
  
##  <a name="3-use-background-colors-to-display-a-kpi"></a><a name="BackgroundColors"></a><span data-ttu-id="4b076-175">3. 使用背景色显示 KPI</span><span class="sxs-lookup"><span data-stu-id="4b076-175">3. Use Background Colors to Display a KPI</span></span>  
 <span data-ttu-id="4b076-176">可将背景色设置为运行报表时计算的表达式。</span><span class="sxs-lookup"><span data-stu-id="4b076-176">Background colors can be set to an expression that is evaluated when you run the report.</span></span>  
  
#### <a name="to-display-the-present-state-of-a-kpi-by-using-background-colors"></a><span data-ttu-id="4b076-177">使用背景色显示 KPI 的当前状态</span><span class="sxs-lookup"><span data-stu-id="4b076-177">To display the present state of a KPI by using background colors</span></span>  
  
1.  <span data-ttu-id="4b076-178">在表中，右键单击 " `[Sum(Sales)]` 小计" 行 (显示子类别销售额) 的单元格，然后单击 "**文本框属性**"。</span><span class="sxs-lookup"><span data-stu-id="4b076-178">In the table, right-click two cells down from the `[Sum(Sales)]` cell (the subtotal row that displays the sales for a subcategory), and then click **Text Box Properties**.</span></span>  
  
2.  <span data-ttu-id="4b076-179">在 "**填充**" 中，单击 "**填充颜色**" 选项旁边的**fx**按钮，然后在 "为以下项**设置表达式： BackgroundColor** " 字段中输入以下表达式：</span><span class="sxs-lookup"><span data-stu-id="4b076-179">In **Fill**, click the **fx** button next to the **Fill color** option and enter the following expression in the **Set expression for: BackgroundColor** field:</span></span>  
  
 `=IIF(Sum(Fields!Sales.Value) >= 5000 ,"Lime", IIF(Sum(Fields!Sales.Value) < 2500, "Red","Yellow"))`  
  
 <span data-ttu-id="4b076-180">对于包含大于或等于 5000 的 `[Sum(Sales)]` 聚合汇总的每个单元，该表达式会使用名为“Lime”的绿色阴影，将背景色会更改为绿色。</span><span class="sxs-lookup"><span data-stu-id="4b076-180">This changes the background color to green, using the shade of green named "Lime", for each cell that contains an aggregated sum for `[Sum(Sales)]` that is greater than or equal to 5000.</span></span> <span data-ttu-id="4b076-181">2500 和 5000 之间的 `[Sum(Sales)]` 值会变为黄色。</span><span class="sxs-lookup"><span data-stu-id="4b076-181">Values of `[Sum(Sales)]` between 2500 and 5000 are colored yellow.</span></span> <span data-ttu-id="4b076-182">小于 2500 的值会变为红色。</span><span class="sxs-lookup"><span data-stu-id="4b076-182">Values less than 2500 are colored red.</span></span>  
  
1.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
2.  <span data-ttu-id="4b076-183">单击 **“运行”** 以预览报表。</span><span class="sxs-lookup"><span data-stu-id="4b076-183">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="4b076-184">在显示子类别销售额的小计行中，根据销售额总计的值，单元的背景色为红色、黄色或绿色。</span><span class="sxs-lookup"><span data-stu-id="4b076-184">In the subtotal row that displays the sales for a subcategory, the background color of the cell is red, yellow, or green depending on value of the sales sum.</span></span>  
  
##  <a name="4-display-a-kpi-by-using-a-gauge"></a><a name="Gauge"></a><span data-ttu-id="4b076-185">4. 使用仪表显示 KPI</span><span class="sxs-lookup"><span data-stu-id="4b076-185">4. Display a KPI by Using a Gauge</span></span>  
 <span data-ttu-id="4b076-186">仪表显示数据集中的单个值。</span><span class="sxs-lookup"><span data-stu-id="4b076-186">A gauge depicts a single value in a dataset.</span></span> <span data-ttu-id="4b076-187">本教程使用水平线性仪表，因为即使是在该仪表较小或在表单元内使用的情况下，其形状和简便性也使其易于读取。</span><span class="sxs-lookup"><span data-stu-id="4b076-187">This tutorial uses a horizontal linear gauge because its shape and simplicity makes it easy to read, even in when it is a small size and used within a table cell.</span></span> <span data-ttu-id="4b076-188">有关详细信息，请参阅 [仪表（报表生成器和 SSRS）](report-design/gauges-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="4b076-188">For more information, see [Gauges &#40;Report Builder and SSRS&#41;](report-design/gauges-report-builder-and-ssrs.md).</span></span>  
  
#### <a name="to-display-the-present-state-of-a-kpi-using-a-gauge"></a><span data-ttu-id="4b076-189">使用仪表显示 KPI 的当前状态</span><span class="sxs-lookup"><span data-stu-id="4b076-189">To display the present state of a KPI using a gauge</span></span>  
  
1.  <span data-ttu-id="4b076-190">切换到“设计”视图。</span><span class="sxs-lookup"><span data-stu-id="4b076-190">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="4b076-191">在表中，右键单击在上一过程中更改的单元的列处理程序，指向 "**插入列**"，然后单击 "**右**"。</span><span class="sxs-lookup"><span data-stu-id="4b076-191">In the table, right-click the column handler for the cell that you changed in the previous procedure, point to **Insert Column**, and then click **Right**.</span></span> <span data-ttu-id="4b076-192">此时将向表添加一个新列。</span><span class="sxs-lookup"><span data-stu-id="4b076-192">A new column is added to the table.</span></span>  
  
3.  <span data-ttu-id="4b076-193">在列标题中键入**KPI** 。</span><span class="sxs-lookup"><span data-stu-id="4b076-193">Type **KPI** in the column heading.</span></span>  
  
4.  <span data-ttu-id="4b076-194">在 "**插入**" 选项卡上的 "**数据区域**" 组中，单击 "**仪表**"，然后单击表外的设计图面。</span><span class="sxs-lookup"><span data-stu-id="4b076-194">On the **Insert** tab, in the **Data Regions** group, click **Gauge**, and then click the design surface outside the table.</span></span> <span data-ttu-id="4b076-195">此时将显示 **“选择仪表类型”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="4b076-195">The **Select Gauge Type** dialog box appears.</span></span>  
  
5.  <span data-ttu-id="4b076-196">单击 "**线性**"。</span><span class="sxs-lookup"><span data-stu-id="4b076-196">Click **Linear**.</span></span> <span data-ttu-id="4b076-197">选择第一个线性仪表类型 "**水平**"。</span><span class="sxs-lookup"><span data-stu-id="4b076-197">The first linear gauge type, **Horizontal**, is selected.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="4b076-198">此时将向设计图面添加一个仪表。</span><span class="sxs-lookup"><span data-stu-id="4b076-198">A gauge is added to the design surface.</span></span>  
  
7.  <span data-ttu-id="4b076-199">从“报表数据”窗格，将 Sales 拖至该仪表。</span><span class="sxs-lookup"><span data-stu-id="4b076-199">From the Report Data pane, drag Sales to the gauge.</span></span> <span data-ttu-id="4b076-200">当您在仪表中拖动 Sales 时，将打开“仪表数据”窗格。</span><span class="sxs-lookup"><span data-stu-id="4b076-200">When you drag Sales across the gauge, the Gauge Data pane opens.</span></span>  
  
8.  <span data-ttu-id="4b076-201">在 "**值**" 列表中删除 Sales。</span><span class="sxs-lookup"><span data-stu-id="4b076-201">Drop Sales in the **Values** list.</span></span>  
  
     <span data-ttu-id="4b076-202">将该字段拖到仪表中时，将使用内置 Sum 函数聚合该字段。</span><span class="sxs-lookup"><span data-stu-id="4b076-202">When you drop the field onto the gauge, the field is aggregated by using the built-in Sum function.</span></span>  
  
9. <span data-ttu-id="4b076-203">右键单击仪表中的指针，然后单击 "**指针属性**"。</span><span class="sxs-lookup"><span data-stu-id="4b076-203">Right-click the pointer in the gauge and click **Pointer Properties**.</span></span>  
  
10. <span data-ttu-id="4b076-204">在 "**指针类型**" 中选择 "**条形图**"。</span><span class="sxs-lookup"><span data-stu-id="4b076-204">In **Pointer Type**, select **Bar**.</span></span> <span data-ttu-id="4b076-205">这会将指针从标记改为条形，从而在将仪表添加到表中时更加清晰可见。</span><span class="sxs-lookup"><span data-stu-id="4b076-205">This changes the pointer from a marker to a bar that will be more visible when the gauge is added to the table.</span></span>  
  
11. <span data-ttu-id="4b076-206">单击 "**指针填充**"。</span><span class="sxs-lookup"><span data-stu-id="4b076-206">Click **Pointer Fill**.</span></span> <span data-ttu-id="4b076-207">在**辅助颜色中，** 选取**黄色**。</span><span class="sxs-lookup"><span data-stu-id="4b076-207">In **Secondary Color,** pick **Yellow**.</span></span> <span data-ttu-id="4b076-208">渐变填充模式将从白色改为黄色。</span><span class="sxs-lookup"><span data-stu-id="4b076-208">The gradient fill pattern will change from white to yellow.</span></span>  
  
12. <span data-ttu-id="4b076-209">右键单击仪表中的刻度，然后单击“刻度属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4b076-209">Right-click the scale in the gauge and click **Scale Properties**.</span></span>  
  
13. <span data-ttu-id="4b076-210">将 "**最大值**" 选项设置为25000。</span><span class="sxs-lookup"><span data-stu-id="4b076-210">Set the **Maximum** option to 25000.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4b076-211">可以使用一个表达式动态计算“最大值”选项的值来代替常数（如 25000）\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4b076-211">Instead of a constant such as 25000, you can use an expression to dynamically calculate the value of the **Maximum** option.</span></span> <span data-ttu-id="4b076-212">该表达式将使用聚合功能的聚合，类似于表达式 `=Max(Sum(Fields!Sales.value), "Tablix1")`。</span><span class="sxs-lookup"><span data-stu-id="4b076-212">The expression would use the aggregate of aggregate feature and look similar to the expression `=Max(Sum(Fields!Sales.value), "Tablix1")`.</span></span>  
  
14. <span data-ttu-id="4b076-213">将表内的仪表拖到所插入列的小计行（此行显示子类别的销售额）的第三个单元中。</span><span class="sxs-lookup"><span data-stu-id="4b076-213">Drag the gauge inside the table into the third cell in the subtotal row that displays the sales for a subcategory of the column that you inserted.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4b076-214">可能需要调整列大小，以使单元能够容纳水平线性仪表。</span><span class="sxs-lookup"><span data-stu-id="4b076-214">You might have to resize the column so that the horizontal linear gauge fits into the cell.</span></span> <span data-ttu-id="4b076-215">若要调整列大小，请单击列标题，并使用控点水平和垂直调整单元大小。</span><span class="sxs-lookup"><span data-stu-id="4b076-215">To resize the column, click a column header and use the handles to resize the cells horizontally and vertically.</span></span>  
  
15. <span data-ttu-id="4b076-216">单击 **“运行”** 以预览报表。</span><span class="sxs-lookup"><span data-stu-id="4b076-216">Click **Run** to preview the report.</span></span>  
  
     <span data-ttu-id="4b076-217">仪表中条形的水平长度将根据 KPI 的值变化。</span><span class="sxs-lookup"><span data-stu-id="4b076-217">The horizontal length of the bar in the gauge changes depending on the value of the KPI.</span></span>  
  
16. <span data-ttu-id="4b076-218">（可选）添加处理溢出的最大刻度格，以使超出最大刻度的任何值始终指向最大刻度格：</span><span class="sxs-lookup"><span data-stu-id="4b076-218">(Optional) Add a maximum pin to handle overflow so that any value over the scale maximum always points to the maximum pin:</span></span>  
  
    1.  <span data-ttu-id="4b076-219">打开“属性”窗格。</span><span class="sxs-lookup"><span data-stu-id="4b076-219">Open the Properties pane.</span></span>  
  
    2.  <span data-ttu-id="4b076-220">单击 "缩放"。</span><span class="sxs-lookup"><span data-stu-id="4b076-220">Click the scale.</span></span> <span data-ttu-id="4b076-221">该线性刻度的属性将显示在“属性”窗格中。</span><span class="sxs-lookup"><span data-stu-id="4b076-221">The properties for the linear scale are displayed in the Properties pane.</span></span>  
  
    3.  <span data-ttu-id="4b076-222">在 "**缩放 pin** " 类别中，展开 " **MaximumPin** " 节点。</span><span class="sxs-lookup"><span data-stu-id="4b076-222">In the **Scale Pins** category, expand the **MaximumPin** node.</span></span>  
  
    4.  <span data-ttu-id="4b076-223">将**Enable**属性设置为 `True` 。</span><span class="sxs-lookup"><span data-stu-id="4b076-223">Set the **Enable** property to `True`.</span></span> <span data-ttu-id="4b076-224">随即将在刻度的最大值之后显示一个刻度格。</span><span class="sxs-lookup"><span data-stu-id="4b076-224">A pin appears after the maximum value on the scale.</span></span>  
  
    5.  <span data-ttu-id="4b076-225">将 "**边框**" 设置为 `Lime` 。</span><span class="sxs-lookup"><span data-stu-id="4b076-225">Set **BorderColor** to `Lime`.</span></span>  
  
17. <span data-ttu-id="4b076-226">单击 **“运行”** 以预览报表。</span><span class="sxs-lookup"><span data-stu-id="4b076-226">Click **Run** to preview the report.</span></span>  
  
##  <a name="5-display-a-kpi-by-using-an-indicator"></a><a name="Indicator"></a><span data-ttu-id="4b076-227">5. 使用指示器显示 KPI</span><span class="sxs-lookup"><span data-stu-id="4b076-227">5. Display a KPI by Using an Indicator</span></span>  
 <span data-ttu-id="4b076-228">指示器是以直观的形式传递数据值的小巧而简单的仪表。</span><span class="sxs-lookup"><span data-stu-id="4b076-228">Indicators are small simple gauges that communicate data values at a glance.</span></span> <span data-ttu-id="4b076-229">由于指示器尺寸较小且具有简便性，其经常被用于表和矩阵中。</span><span class="sxs-lookup"><span data-stu-id="4b076-229">Because of their size and simplicity, indicators are often used in tables and matrices.</span></span> <span data-ttu-id="4b076-230">有关详细信息，请参阅[指示器（报表生成器和 SSRS）](report-design/indicators-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="4b076-230">For more information, see [Indicators &#40;Report Builder and SSRS&#41;](report-design/indicators-report-builder-and-ssrs.md).</span></span>  
  
#### <a name="to-display-the-present-state-of-a-kpi-using-an-indicator"></a><span data-ttu-id="4b076-231">使用指示器显示 KPI 的当前状态</span><span class="sxs-lookup"><span data-stu-id="4b076-231">To display the present state of a KPI using an indicator</span></span>  
  
1.  <span data-ttu-id="4b076-232">切换到“设计”视图。</span><span class="sxs-lookup"><span data-stu-id="4b076-232">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="4b076-233">在表中，右键单击在上一过程中更改的单元的列处理程序，指向 "**插入列**"，然后单击 "**右**"。</span><span class="sxs-lookup"><span data-stu-id="4b076-233">In the table, right-click the column handler for the cell that you changed in the previous procedure, point to **Insert Column**, and then click **Right**.</span></span> <span data-ttu-id="4b076-234">此时将向表添加一个新列。</span><span class="sxs-lookup"><span data-stu-id="4b076-234">A new column is added to the table.</span></span>  
  
3.  <span data-ttu-id="4b076-235">在列标题中键入**KPI** 。</span><span class="sxs-lookup"><span data-stu-id="4b076-235">Type **KPI** in the column heading.</span></span>  
  
4.  <span data-ttu-id="4b076-236">单击子类别小计的单元。</span><span class="sxs-lookup"><span data-stu-id="4b076-236">Click the cell for the subcategory subtotal.</span></span>  
  
5.  <span data-ttu-id="4b076-237">在 "**插入**" 选项卡上的 "**数据区域**" 组中，双击 "**指示器"。**</span><span class="sxs-lookup"><span data-stu-id="4b076-237">On the **Insert** tab, in the **Data Regions** group, double-click **Indicator.**</span></span>  
  
     <span data-ttu-id="4b076-238">“选择指示器类型”\*\*\*\* 对话框即会打开。</span><span class="sxs-lookup"><span data-stu-id="4b076-238">The **Select Indicator Type** dialog box opens.</span></span>  
  
6.  <span data-ttu-id="4b076-239">单击 "**形状**"。</span><span class="sxs-lookup"><span data-stu-id="4b076-239">Click **Shapes**.</span></span> <span data-ttu-id="4b076-240">选择第一个形状类型， **3 个交通灯 (个交通) "** 。</span><span class="sxs-lookup"><span data-stu-id="4b076-240">The first shape type, **3 Traffic Lights (Unrimmed),** is selected.</span></span>  
  
     <span data-ttu-id="4b076-241">在本教程中，您将使用该指示器。</span><span class="sxs-lookup"><span data-stu-id="4b076-241">You will use this indicator in the tutorial.</span></span>  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="4b076-242">该指示器将添加到设计图面中。</span><span class="sxs-lookup"><span data-stu-id="4b076-242">The indicator is added to the design surface.</span></span>  
  
8.  <span data-ttu-id="4b076-243">右键单击指示器，然后单击“指示器属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4b076-243">Right-click the indicator and click **Indicator Properties**.</span></span>  
  
9. <span data-ttu-id="4b076-244">单击 "**值和状态**"。</span><span class="sxs-lookup"><span data-stu-id="4b076-244">Click **Values and States**.</span></span>  
  
10. <span data-ttu-id="4b076-245">在 "值" 下拉列表中，选择 **[Sum (Sales) ]**，但不要更改任何其他选项。</span><span class="sxs-lookup"><span data-stu-id="4b076-245">In the Value drop-down list, select **[Sum(Sales)]**, but do not change any other options.</span></span>  
  
     <span data-ttu-id="4b076-246">默认情况下，数据区域会发生数据同步，且将在“同步作用域”框中看到“Tablix1”值（报表中表数据区域的名称）\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4b076-246">By default, data synchronization occurs across the data region and you see the value **Tablix1**, the name of the table data region in the report, in the **Synchronization scope** box.</span></span>  
  
     <span data-ttu-id="4b076-247">在该报表中，还可以更改放在子类别小计单元中的指示器的作用域，以在 SalesDate 字段内同步。</span><span class="sxs-lookup"><span data-stu-id="4b076-247">In this report, you can also change the scope of an indicator placed in the cell of the subcategory subtotal to synchronize across the SalesDate field.</span></span>  
  
11. <span data-ttu-id="4b076-248">单击 **“运行”** 以预览报表。</span><span class="sxs-lookup"><span data-stu-id="4b076-248">Click **Run** to preview the report.</span></span>  
  
##  <a name="6-add-a-report-title"></a><a name="Title"></a><span data-ttu-id="4b076-249">6. 添加报表标题</span><span class="sxs-lookup"><span data-stu-id="4b076-249">6. Add a Report Title</span></span>  
 <span data-ttu-id="4b076-250">报表标题将出现在报表的顶部。</span><span class="sxs-lookup"><span data-stu-id="4b076-250">A report title appears at the top of the report.</span></span> <span data-ttu-id="4b076-251">可以将报表标题置于报表表头中或置于表体顶部的文本框中（如果报表未使用表头）。</span><span class="sxs-lookup"><span data-stu-id="4b076-251">You can place the report title in a report header or if the report does not use one, in a text box at the top of the report body.</span></span> <span data-ttu-id="4b076-252">您将使用自动放在表体顶部的文本框。</span><span class="sxs-lookup"><span data-stu-id="4b076-252">You will use the text box that is automatically placed at the top of the report body.</span></span>  
  
 <span data-ttu-id="4b076-253">通过将不同的字体样式、大小和颜色应用于文本的短语和单个字符，可以进一步增强文本。</span><span class="sxs-lookup"><span data-stu-id="4b076-253">The text can be further enhanced by applying different font styles, sizes, and colors to phrases and individual characters of the text.</span></span> <span data-ttu-id="4b076-254">有关详细信息，请参阅[设置文本框中文本的格式（报表生成器和 SSRS）](report-design/format-text-in-a-text-box-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="4b076-254">For more information, see [Format Text in a Text Box &#40;Report Builder and SSRS&#41;](report-design/format-text-in-a-text-box-report-builder-and-ssrs.md).</span></span>  
  
#### <a name="to-add-a-report-title"></a><span data-ttu-id="4b076-255">添加报表标题</span><span class="sxs-lookup"><span data-stu-id="4b076-255">To add a report title</span></span>  
  
1.  <span data-ttu-id="4b076-256">在设计图面上，单击“单击以添加标题”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4b076-256">On the design surface, click **Click to add title**.</span></span>  
  
2.  <span data-ttu-id="4b076-257">键入**Product SALES KPI**，然后在文本框外部单击。</span><span class="sxs-lookup"><span data-stu-id="4b076-257">Type **Product Sales KPI**, and then click outside the text box.</span></span>  
  
3.  <span data-ttu-id="4b076-258">也可以右键单击包含**Product SALES KPI**的文本框，单击 "**文本框属性**"，然后在 "字体" 选项卡上选择不同的字体样式、大小和颜色。</span><span class="sxs-lookup"><span data-stu-id="4b076-258">Optionally, right-click the text box that contains **Product Sales KPI**, click **Text Box Properties**, and then on the Font tab select the different font styles, sizes and colors.</span></span>  
  
4.  <span data-ttu-id="4b076-259">单击 **“运行”** 以预览报表。</span><span class="sxs-lookup"><span data-stu-id="4b076-259">Click **Run** to preview the report.</span></span>  
  
##  <a name="7-save-the-report"></a><a name="Save"></a><span data-ttu-id="4b076-260">7. 保存报表</span><span class="sxs-lookup"><span data-stu-id="4b076-260">7. Save the Report</span></span>  
 <span data-ttu-id="4b076-261">将报表保存到报表服务器或计算机上。</span><span class="sxs-lookup"><span data-stu-id="4b076-261">Save the report to a report server or your computer.</span></span> <span data-ttu-id="4b076-262">如果不将报表保存到报表服务器上，则许多 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 功能（如报表部件和子报表）将不可用。</span><span class="sxs-lookup"><span data-stu-id="4b076-262">If you do not save the report to the report server, a number of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] features such as report parts and subreports are not available.</span></span>  
  
#### <a name="to-save-the-report-on-a-report-server"></a><span data-ttu-id="4b076-263">将报表保存到报表服务器</span><span class="sxs-lookup"><span data-stu-id="4b076-263">To save the report on a report server</span></span>  
  
1.  <span data-ttu-id="4b076-264">从 **“报表生成器”** 按钮，单击 **“另存为”**。</span><span class="sxs-lookup"><span data-stu-id="4b076-264">From the **Report Builder** button, click **Save As**.</span></span>  
  
2.  <span data-ttu-id="4b076-265">单击 **“最近使用的站点和服务器”**。</span><span class="sxs-lookup"><span data-stu-id="4b076-265">Click **Recent Sites and Servers**.</span></span>  
  
3.  <span data-ttu-id="4b076-266">选择或键入您拥有保存报表权限的报表服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="4b076-266">Select or type the name of the report server where you have permission to save reports.</span></span>  
  
     <span data-ttu-id="4b076-267">此时将显示“正在连接到报表服务器”消息。</span><span class="sxs-lookup"><span data-stu-id="4b076-267">The message "Connecting to report server" appears.</span></span> <span data-ttu-id="4b076-268">当连接完成时，您将看到报表服务器管理员指定为报表默认位置的报表文件夹的内容。</span><span class="sxs-lookup"><span data-stu-id="4b076-268">When the connection is complete, you see the contents of the report folder that the report server administrator specified as the default location for reports.</span></span>  
  
4.  <span data-ttu-id="4b076-269">在“名称”中，用 Product Sales KPI 替换默认名称\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4b076-269">In **Name**, replace the default name with **Product Sales KPI**.</span></span>  
  
5.  <span data-ttu-id="4b076-270">单击“ **保存**”。</span><span class="sxs-lookup"><span data-stu-id="4b076-270">Click **Save**.</span></span>  
  
 <span data-ttu-id="4b076-271">报表即已保存至报表服务器。</span><span class="sxs-lookup"><span data-stu-id="4b076-271">The report is saved to the report server.</span></span> <span data-ttu-id="4b076-272">您连接的报表服务器的名称将显示在窗口底部的状态栏中。</span><span class="sxs-lookup"><span data-stu-id="4b076-272">The name of report server that you are connected to appears in the status bar at the bottom of the window.</span></span>  
  
#### <a name="to-save-the-report-on-your-computer"></a><span data-ttu-id="4b076-273">将报表保存到计算机上</span><span class="sxs-lookup"><span data-stu-id="4b076-273">To save the report on your computer</span></span>  
  
1.  <span data-ttu-id="4b076-274">从 **“报表生成器”** 按钮，单击 **“另存为”**。</span><span class="sxs-lookup"><span data-stu-id="4b076-274">From the **Report Builder** button, click **Save As**.</span></span>  
  
2.  <span data-ttu-id="4b076-275">依次单击“桌面”、“我的文档”或“我的电脑”，并浏览到要保存该报表的文件夹\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4b076-275">Click **Desktop**, **My Documents**, or **My computer**, and browse to the folder where you want to save the report.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4b076-276">如果无权访问报表服务器，请单击“桌面”、“我的文档”或“我的电脑”，将报表保存到计算机上\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4b076-276">If you do not have access to a report server, click **Desktop**, **My Documents**, or **My computer** and save the report to your computer.</span></span>  
  
1.  <span data-ttu-id="4b076-277">在“名称”中，用 Product Sales KPI 替换默认名称\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4b076-277">In **Name**, replace the default name with **Product Sales KPI**.</span></span>  
  
2.  <span data-ttu-id="4b076-278">单击“ **保存**”。</span><span class="sxs-lookup"><span data-stu-id="4b076-278">Click **Save**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="4b076-279">后续步骤</span><span class="sxs-lookup"><span data-stu-id="4b076-279">Next Steps</span></span>  
 <span data-ttu-id="4b076-280">您已成功完成“向报表添加 KPI”教程的学习。</span><span class="sxs-lookup"><span data-stu-id="4b076-280">You have successfully completed the Adding a KPI to Your Report tutorial.</span></span> <span data-ttu-id="4b076-281">有关详细信息，请参阅仪表 (报表生成器) [指标 &#40;报表生成器和 SSRS&#41;](report-design/indicators-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="4b076-281">For more information, see Gauges (Report Builder) [Indicators &#40;Report Builder and SSRS&#41;](report-design/indicators-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b076-282">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4b076-282">See Also</span></span>  
 <span data-ttu-id="4b076-283">[教程 &#40;报表生成器&#41;](report-builder-tutorials.md) </span><span class="sxs-lookup"><span data-stu-id="4b076-283">[Tutorials &#40;Report Builder&#41;](report-builder-tutorials.md) </span></span>  
 [<span data-ttu-id="4b076-284">SQL Server 2014 中的报表生成器</span><span class="sxs-lookup"><span data-stu-id="4b076-284">Report Builder in SQL Server 2014</span></span>](report-builder/report-builder-in-sql-server-2016.md)  
  
  
