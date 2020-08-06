---
title: 教程：地图报表（报表生成器）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 8d831356-7efa-40cc-ae95-383b3eecf833
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b737bb3fe74eb3524f2944a7458cb4837b1aeedf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692208"
---
# <a name="tutorial-map-report-report-builder"></a><span data-ttu-id="3c3f6-102">教程：地图报表（报表生成器）</span><span class="sxs-lookup"><span data-stu-id="3c3f6-102">Tutorial: Map Report (Report Builder)</span></span>
  <span data-ttu-id="3c3f6-103">本教程旨在帮助您了解地图功能，您可以使用该功能针对地理背景显示报表数据。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-103">This tutorial is designed to help you learn about the map features you can use to display report data against a geographic background.</span></span>  
  
 <span data-ttu-id="3c3f6-104">地图以空间数据为基础，这些数据通常包含点、线条和多边形。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-104">Maps are based on spatial data that typically consists of points, lines, and polygons.</span></span> <span data-ttu-id="3c3f6-105">例如，多边形可以表示国家/地区轮廓，线条可以表示道路，而点则可以表示市县所在位置。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-105">For example, a polygon can represent the outline of a county, a line can represent a road, and a point can represent the location of a city.</span></span> <span data-ttu-id="3c3f6-106">各种类型的空间数据作为一组地图元素显示在单独的地图层上。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-106">Each type of spatial data is displayed on a separate map layer as a set of map elements.</span></span>  
  
 <span data-ttu-id="3c3f6-107">若要改变地图元素的外观，可以指定一个字段，通过字段值将地图元素与数据集中分析数据相匹配。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-107">To vary the appearance of map elements, you specify a field that has values that match the map elements with analytical data from a dataset.</span></span> <span data-ttu-id="3c3f6-108">还可以定义相关规则，依据数据范围改变颜色、大小、或其他属性。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-108">You can also define rules that vary color, size, or other properties based on ranges of data.</span></span>  
  
 <span data-ttu-id="3c3f6-109">本教程中，将生成一个地图报表，该报表显示了纽约州各县内的商店位置。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-109">In this tutorial, you will build a map report that displays store locations in New York state counties.</span></span>  
  
##  <a name="what-you-will-learn"></a><a name="BackToTop"></a><span data-ttu-id="3c3f6-110">你将学习的内容</span><span class="sxs-lookup"><span data-stu-id="3c3f6-110">What You Will Learn</span></span>  
 <span data-ttu-id="3c3f6-111">在本教程中，您将学习如何执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="3c3f6-111">In this tutorial you will learn how to do the following:</span></span>  
  
1.  [<span data-ttu-id="3c3f6-112">通过地图向导使用多边形层创建地图</span><span class="sxs-lookup"><span data-stu-id="3c3f6-112">Create a Map with a Polygon Layer from the Map Wizard</span></span>](#Map)  
  
2.  [<span data-ttu-id="3c3f6-113">添加地图点层以显示商店位置</span><span class="sxs-lookup"><span data-stu-id="3c3f6-113">Add a Map Point Layer to Display Store Locations</span></span>](#PointLayer)  
  
3.  [<span data-ttu-id="3c3f6-114">添加地图线条层以显示路线</span><span class="sxs-lookup"><span data-stu-id="3c3f6-114">Add a Map Line Layer to Display a Route</span></span>](#LineLayer)  
  
4.  [<span data-ttu-id="3c3f6-115">添加 Bing 地图图块背景</span><span class="sxs-lookup"><span data-stu-id="3c3f6-115">Add a Bing Maps Tile Background</span></span>](#TileLayer)  
  
5.  [<span data-ttu-id="3c3f6-116">将层设置为透明</span><span class="sxs-lookup"><span data-stu-id="3c3f6-116">Make a Layer Transparent</span></span>](#Transparent)  
  
6.  [<span data-ttu-id="3c3f6-117">根据销售改变县颜色</span><span class="sxs-lookup"><span data-stu-id="3c3f6-117">Vary County Color Based on Sales</span></span>](#Vary)  
  
    1.  [<span data-ttu-id="3c3f6-118">在空间数据与分析数据之间建立关系</span><span class="sxs-lookup"><span data-stu-id="3c3f6-118">Build a Relationship between Spatial and Analytical Data</span></span>](#Relationship)  
  
    2.  [<span data-ttu-id="3c3f6-119">为多边形指定颜色规则</span><span class="sxs-lookup"><span data-stu-id="3c3f6-119">Specify Color Rules for Polygons</span></span>](#ColorRules)  
  
    3.  [<span data-ttu-id="3c3f6-120">将色阶中的数据的格式设置为“货币”</span><span class="sxs-lookup"><span data-stu-id="3c3f6-120">Format the Data in the Color Scale as Currency</span></span>](#ColorScale)  
  
    4.  [<span data-ttu-id="3c3f6-121">创建新图例</span><span class="sxs-lookup"><span data-stu-id="3c3f6-121">Create a New Legend</span></span>](#NewLegend)  
  
    5.  [<span data-ttu-id="3c3f6-122">将图例与颜色规则关联</span><span class="sxs-lookup"><span data-stu-id="3c3f6-122">Associate Legend and Color Rules</span></span>](#Associate)  
  
    6.  [<span data-ttu-id="3c3f6-123">清除没有数据的县的颜色</span><span class="sxs-lookup"><span data-stu-id="3c3f6-123">Clear Color from Counties with No Data</span></span>](#NoData)  
  
7.  [<span data-ttu-id="3c3f6-124">添加自定义点</span><span class="sxs-lookup"><span data-stu-id="3c3f6-124">Add a Custom Point</span></span>](#CustomPoint)  
  
8.  [<span data-ttu-id="3c3f6-125">将地图视图居中</span><span class="sxs-lookup"><span data-stu-id="3c3f6-125">Center the Map View</span></span>](#CenterView)  
  
9. [<span data-ttu-id="3c3f6-126">添加报表标题</span><span class="sxs-lookup"><span data-stu-id="3c3f6-126">Add a Report Title</span></span>](#Title)  
  
10. [<span data-ttu-id="3c3f6-127">保存报表</span><span class="sxs-lookup"><span data-stu-id="3c3f6-127">Save the Report</span></span>](#Save)  
  
> [!NOTE]  
>  <span data-ttu-id="3c3f6-128">在本教程中，将向导的多个步骤合并为两个过程：一个用于创建数据集，一个用于创建表。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-128">In this tutorial, the steps for the wizard are consolidated into two procedures: one to create the dataset and one to create a table.</span></span> <span data-ttu-id="3c3f6-129">有关如何浏览到报表服务器、选择数据源、创建数据集和运行向导的分步说明，请参阅本系列的第一个教程：[教程：创建基本表报表（报表生成器）](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-129">For step-by-step instructions about how to browse to a report server, choose a data source, create a dataset, and run the wizard, see the first tutorial in this series: [Tutorial: Creating a Basic Table Report &#40;Report Builder&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md).</span></span>  
  
 <span data-ttu-id="3c3f6-130">本教程的预计学时：30 分钟。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-130">Estimated time to complete this tutorial: 30 minutes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c3f6-131">要求</span><span class="sxs-lookup"><span data-stu-id="3c3f6-131">Requirements</span></span>  
 <span data-ttu-id="3c3f6-132">有关要求的信息，请参阅[教程先决条件（报表生成器）](../reporting-services/report-builder-tutorials.md)。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-132">For information about requirements, see [Prerequisites for Tutorials &#40;Report Builder&#41;](../reporting-services/report-builder-tutorials.md).</span></span>  
  
##  <a name="1-create-a-map-with-a-polygon-layer-from-the-map-wizard"></a><a name="Map"></a><span data-ttu-id="3c3f6-133">1. 使用地图向导创建具有多边形层的地图</span><span class="sxs-lookup"><span data-stu-id="3c3f6-133">1. Create a Map with a Polygon Layer from the Map Wizard</span></span>  
 <span data-ttu-id="3c3f6-134">从地图库向报表中添加地图。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-134">Add a map to your report from the map gallery.</span></span> <span data-ttu-id="3c3f6-135">该地图具有一个层，此层显示了纽约州中的各个县。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-135">The map has one layer that displays the counties in New York state.</span></span> <span data-ttu-id="3c3f6-136">各县的形状为根据地图库中的地图内嵌入的空间数据得出的多边形。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-136">The shape of each county is a polygon based on spatial data that is embedded in the map from the map gallery.</span></span>  
  
#### <a name="to-add-a-map-with-the-map-wizard-in-a-new-report"></a><span data-ttu-id="3c3f6-137">使用地图向导在新报表中添加地图</span><span class="sxs-lookup"><span data-stu-id="3c3f6-137">To add a map with the map wizard in a new report</span></span>  
  
1.  <span data-ttu-id="3c3f6-138">单击 "**开始**"，指向 "**程序**"，指向 [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)] "**报表生成器**"，然后单击 "**报表生成器**"。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-138">Click **Start**, point to **Programs**, point to [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)]**Report Builder**, and then click **Report Builder**.</span></span>  
  
     <span data-ttu-id="3c3f6-139">此时将显示“入门”对话框。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-139">The Getting Started dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3c3f6-140">如果未显示 "入门" 对话框，请在 "报表生成器" 按钮中单击 "**新建**"。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-140">If the Getting Started dialog box does not appear, from the Report Builder button, click **New**.</span></span>  
  
2.  <span data-ttu-id="3c3f6-141">在左窗格中，验证是否选择了 "**报表**"。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-141">In the left pane, verify that **Report** is selected.</span></span>  
  
3.  <span data-ttu-id="3c3f6-142">在右窗格中，单击“地图向导”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-142">In the right pane, click **Map Wizard**.</span></span>  
  
4.  <span data-ttu-id="3c3f6-143">单击“创建”。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-143">Click **Create**.</span></span>  
  
5.  <span data-ttu-id="3c3f6-144">**选择 "空间数据源**" 页上，验证是否选择了 "**地图库**"。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-144">**Choose a source of spatial data** page, verify that **Map gallery** is selected.</span></span>  
  
6.  <span data-ttu-id="3c3f6-145">在 "地图库" 窗格中，展开 "**美国国内\*\*\*\*的国家/地区**"，然后单击 "**纽约**"。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-145">In the Map Gallery pane, expand **States by County** under **USA**, and click **New York**.</span></span>  
  
     <span data-ttu-id="3c3f6-146">此时，“地图预览”窗格将显示纽约的县地图。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-146">The Map Preview pane displays the New York county map.</span></span>  
  
7.  <span data-ttu-id="3c3f6-147">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-147">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="3c3f6-148">在 "**选择空间数据和地图视图选项**" 页上，接受默认值。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-148">On the **Choose spatial data and map view options** page, accept the defaults.</span></span> <span data-ttu-id="3c3f6-149">默认情况下，来自地图库的地图元素将自动嵌入到报表定义中。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-149">By default, map elements from a map gallery will automatically be embedded in the report definition.</span></span>  
  
9. <span data-ttu-id="3c3f6-150">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-150">Click **Next**.</span></span>  
  
10. <span data-ttu-id="3c3f6-151">在“选择地图可视化”页上，确认已选中“基本地图”，然后单击“下一步”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-151">On the **Choose map visualization** page, verify **Basic Map** is selected, and click **Next**.</span></span>  
  
11. <span data-ttu-id="3c3f6-152">在“选择颜色主题和数据可视化”页上，选择“显示标签”选项\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-152">On the **Choose color theme and data visualization** page, select the **Display labels** option.</span></span>  
  
12. <span data-ttu-id="3c3f6-153">如果已选择，则清除“单色图”选项\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-153">If it is selected, clear the **Single color map** option.</span></span>  
  
13. <span data-ttu-id="3c3f6-154">从 "**数据字段**" 下拉列表中，单击 "#COUNTYNAME"。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-154">From the **Data field** drop-down list, click #COUNTYNAME.</span></span> <span data-ttu-id="3c3f6-155">向导中的“地图预览”窗格显示以下各项：</span><span class="sxs-lookup"><span data-stu-id="3c3f6-155">The Map Preview pane in the wizard displays the following items:</span></span>  
  
    -   <span data-ttu-id="3c3f6-156">一个标题，其文本为“地图标题”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-156">A title with the text **Map Title**.</span></span>  
  
    -   <span data-ttu-id="3c3f6-157">一个地图，显示纽约的各个县，其中每个县都用一种不同的颜色表示，且县名称出现在县区域上方适合的位置。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-157">A map that displays counties in New York where each county is a different color and the county name appears wherever it fits over the county area.</span></span>  
  
    -   <span data-ttu-id="3c3f6-158">一个图例，包含标题和项 1 至 5 的列表。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-158">A legend that contains a title and a list of items 1 through 5.</span></span>  
  
    -   <span data-ttu-id="3c3f6-159">一个色阶，包含值 0 到 160 但没有颜色。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-159">A color scale that contains values 0 to 160 and no color.</span></span>  
  
    -   <span data-ttu-id="3c3f6-160">一个距离宽度，显示公里数 (km) 和英里数 (mi)。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-160">A distance scale that displays kilometers (km) and miles (mi).</span></span>  
  
14. <span data-ttu-id="3c3f6-161">单击“完成”。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-161">Click **Finish**.</span></span>  
  
     <span data-ttu-id="3c3f6-162">此时，将向设计图面添加一个地图。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-162">The map is added to the design surface.</span></span>  
  
15. <span data-ttu-id="3c3f6-163">单击地图以选择它并显示 "**地图层" 窗格**。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-163">Click the map to select it and display the **Map Layers Pane**.</span></span> <span data-ttu-id="3c3f6-164">"**地图层" 窗格**显示第一个层类型为 "**嵌入**" 的多边形层。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-164">The **Map Layers Pane** shows one polygon layer of layer type **Embedded**.</span></span> <span data-ttu-id="3c3f6-165">每个县都是该层上的一个嵌入地图元素。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-165">Each county is an embedded map element on this layer.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3c3f6-166">如果看不到 "**地图层**" 窗格，则它可能显示在当前视图之外。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-166">If you do not see the **Map Layers** pane, it might be displayed outside your current view.</span></span> <span data-ttu-id="3c3f6-167">请使用位于“设计”视图窗口底部的滚动条来更改视图。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-167">Use the scroll bar at the bottom of the Design view window to change your view.</span></span> <span data-ttu-id="3c3f6-168">或者，在 "**视图**" 选项卡中，清除 "**属性**" 或 "**报表数据**" 选项以提供更多的设计图面区域。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-168">Alternatively, in the **View** tab, clear the **Properties** or the **Report Data** option to provide more design surface area.</span></span>  
  
16. <span data-ttu-id="3c3f6-169">右键单击地图标题，然后单击 "**标题属性**"。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-169">Right-click the map title, and then click **Title Properties**.</span></span>  
  
17. <span data-ttu-id="3c3f6-170">将标题文本替换为**Sales By Store**。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-170">Replace the title text with **Sales by Store**.</span></span>  
  
18. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
19. <span data-ttu-id="3c3f6-171">预览报表。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-171">Preview the report.</span></span>  
  
 <span data-ttu-id="3c3f6-172">呈现的报表显示地图标题、地图以及距离刻度。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-172">The rendered report displays the map title, the map, and the distance scale.</span></span> <span data-ttu-id="3c3f6-173">各县位于地图多边形层上。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-173">The counties are on a map polygon layer.</span></span> <span data-ttu-id="3c3f6-174">各个县均为多边形，以调色板中的颜色区分，但颜色并不与任何数据关联。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-174">Each county is a polygon that varies by color from a color palette, but the colors are not associated with any data.</span></span> <span data-ttu-id="3c3f6-175">距离刻度同时用公里和英里显示距离。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-175">The distance scale displays distances in both kilometers and miles.</span></span>  
  
 <span data-ttu-id="3c3f6-176">并不显示地图图例和色阶，因为没有任何与各县关联的分析数据。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-176">The map legend and color scale do not yet appear because there is no analytical data associated with each county.</span></span> <span data-ttu-id="3c3f6-177">稍后，您将在本教程中添加分析数据。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-177">You will add analytical data later in this tutorial.</span></span>  
  
##  <a name="2-add-a-map-point-layer-to-display-store-locations"></a><a name="PointLayer"></a><span data-ttu-id="3c3f6-178">2. 添加地图点层以显示商店位置</span><span class="sxs-lookup"><span data-stu-id="3c3f6-178">2. Add a Map Point Layer to Display Store Locations</span></span>  
 <span data-ttu-id="3c3f6-179">使用地图层向导添加一个点层，用于显示商店的位置。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-179">Use the map layer wizard to add a point layer that displays the locations of stores.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3c3f6-180">在本教程中，由于查询包含了数据值，因此它不需要外部数据源。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-180">In this tutorial, the query contains the data values, so that it does not need an external data source.</span></span> <span data-ttu-id="3c3f6-181">这样，查询就会非常长。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-181">This makes the query quite long.</span></span> <span data-ttu-id="3c3f6-182">在业务环境中，查询不会包含数据。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-182">In a business environment, a query would not contain the data.</span></span> <span data-ttu-id="3c3f6-183">本教程中的查询仅供学习使用。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-183">This is for learning purposes only.</span></span>  
  
#### <a name="to-add-a-point-layer-based-on-a-sql-server-spatial-query"></a><span data-ttu-id="3c3f6-184">基于 SQL Server 空间查询添加点层</span><span class="sxs-lookup"><span data-stu-id="3c3f6-184">To add a point layer based on a SQL Server spatial query</span></span>  
  
1.  <span data-ttu-id="3c3f6-185">切换到“设计”视图。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-185">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="3c3f6-186">双击地图以显示“地图层”\*\*\*\* 窗格。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-186">Double-click the map to display the **Map Layer** pane.</span></span> <span data-ttu-id="3c3f6-187">在工具栏上，单击“新建层向导”\*\*\*\* 按钮 ![rs_IconMapLayerWizard](../../2014/tutorials/media/rs-iconmaplayerwizard.gif "rs_IconMapLayerWizard")。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-187">On the toolbar, click the **New layer wizard** button ![rs_IconMapLayerWizard](../../2014/tutorials/media/rs-iconmaplayerwizard.gif "rs_IconMapLayerWizard").</span></span>  
  
3.  <span data-ttu-id="3c3f6-188">在 "**选择空间数据的源**" 页上，选择 " **SQL Server 空间查询**"，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-188">On the **Choose a source of spatial data** page, select **SQL Server spatial query**, and click **Next**.</span></span>  
  
4.  <span data-ttu-id="3c3f6-189">在 "**选择具有 SQL Server 空间数据**的数据集" 页上，单击 "**添加具有 SQL Server 空间数据的新数据集**"，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-189">On the **Choose a dataset with SQL Server spatial data** page, click **Add a new dataset with SQL Server spatial data**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="3c3f6-190">在“选择与 SQL Server 空间数据源的连接”页上，选择现有数据源，或浏览到报表服务器并选择数据源\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-190">On the **Choose a connection to a SQL Server spatial data source** page, select an existing data source or browse to the report server and select a data source.</span></span>  
  
6.  <span data-ttu-id="3c3f6-191">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-191">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="3c3f6-192">在 "设计查询" 页上，单击 "**编辑为文本**"。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-192">On the Design a Query page, click **Edit as Text**.</span></span>  
  
8.  <span data-ttu-id="3c3f6-193">将以下文本粘贴到查询窗格中：</span><span class="sxs-lookup"><span data-stu-id="3c3f6-193">Paste the following text in the query pane:</span></span>  
  
    ```  
    Select 114 as StoreKey, 'Contoso Albany Store' as StoreName, 1125 as SellingArea, 'Albany' as City, 'Albany' as County,   
     CAST(1000000 as money) as Sales, CAST('POINT(-73.7472924218681 42.6564617079878)' as geography) AS SpatialLocation  
    UNION ALL SELECT 115 AS StoreKey, 'Contoso New York No.1 Store' AS  StoreName, 500 as SellingArea, 'New York' AS City, 'New York City' as County,  
     CAST('2000000' as money) as Sales, CAST('POINT(-73.9922069374483 40.7549638237402)' as geography) AS SpatialLocation  
    UNION ALL Select 116 as StoreKey, 'Contoso Rochester No.1 Store' as StoreName, 462 as SellingArea, 'Rochester' as City,  'Monroe' as County,    
     CAST(3000000 as money) as Sales, CAST('POINT(-77.624041566786 43.1547066024338)' as geography)  AS SpatialLocation  
    UNION ALL Select 117 as StoreKey, 'Contoso New York No.2 Store' as StoreName, 700 as SellingArea, 'New York' as City,'New York City' as County,    
      CAST(4000000 as money) as Sales, CAST('POINT(-73.9712488 40.7830603)' as geography) AS SpatialLocation  
    UNION ALL Select 118 as StoreKey, 'Contoso Syracuse Store' as StoreName, 680 as SellingArea, 'Syracuse' as City, 'Onondaga' as County,  
     CAST(5000000 as money) as Sales, CAST('POINT(-76.1349120532546 43.0610223535974)' as geography) AS SpatialLocation  
    UNION ALL Select 120 as StoreKey, 'Contoso Plattsburgh Store' as StoreName, 560 as SellingArea, 'Plattsburgh' as City,  'Clinton' as County,  
     CAST(6000000 as money) as Sales, CAST('POINT(-73.4728622833178 44.7028831413324)' as geography) AS SpatialLocation  
    UNION ALL Select 121 as StoreKey, 'Contoso Brooklyn Store' as StoreName, 1125 as SellingArea, 'Brooklyn' as City, 'New York City' as County,  
     CAST(7000000 as money) as Sales, CAST('POINT (-73.9638533447143 40.6785123489351)' as geography) AS SpatialLocation  
    UNION ALL Select 122 as StoreKey, 'Contoso Oswego Store' as StoreName, 500 as SellingArea, 'Oswego' as City, 'Oswego' as County,    
     CAST(8000000 as money) as Sales, CAST('POINT(-76.4602850815536 43.4353224527794)' as geography) AS SpatialLocation  
    UNION ALL Select 123 as StoreKey, 'Contoso Ithaca Store' as StoreName, 460 as SellingArea, 'Ithaca' as City, 'Tompkins' as County,  
     CAST(9000000 as money) as Sales, CAST('POINT(-76.5001866085881 42.4310489934743)' as geography) AS SpatialLocation  
    UNION ALL Select 124 as StoreKey, 'Contoso Rochester No.2 Store' as StoreName, 700 as SellingArea, 'Rochester' as City, 'Monroe' as County,    
     CAST(100000 as money) as Sales, CAST('POINT(-77.6240415667866 43.1547066024338)' as geography) AS SpatialLocation  
    UNION ALL Select 125 as StoreKey, 'Contoso Queens Store' as StoreName, 700 as SellingArea,'Queens' as City, 'New York City' as County,  
     CAST(500000 as money) as Sales, CAST('POINT(-73.7930979029883 40.7152781765927)' as geography) AS SpatialLocation  
    UNION ALL Select 126 as StoreKey, 'Contoso Elmira Store' as StoreName, 680 as SellingArea, 'Elmira' as City, 'Chemung' as County,  
     CAST(800000 as money) as Sales, CAST('POINT(-76.7397414783301 42.0736492742663)' as geography) AS SpatialLocation  
    UNION ALL Select 127 as StoreKey, 'Contoso Poestenkill Store' as StoreName, 455 as SellingArea, 'Poestenkill' as City, 'Rensselaer' as County,    
    CAST(1500000 as money) as Sales, CAST('POINT(-73.5626737425063 42.6940551238618)' as geography) AS SpatialLocation  
    ```  
  
9. <span data-ttu-id="3c3f6-194">在查询设计器工具栏上，单击 "**运行** (**！**) "。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-194">On the query designer toolbar, click **Run** (**!**).</span></span>  
  
     <span data-ttu-id="3c3f6-195">结果集将显示七列：StoreKey、StoreName、SellingArea、City、County、Sales 和 SpatialLocation。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-195">The result set displays seven columns: StoreKey, StoreName, SellingArea, City, County, Sales, and SpatialLocation.</span></span> <span data-ttu-id="3c3f6-196">此数据表示纽约州销售生活消费品的一组商店。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-196">This data represents a set of stores in New York State that sell consumer goods.</span></span> <span data-ttu-id="3c3f6-197">结果集中的每行都包含一个商店标识符、商店名称、用于产品显示的区域、商店所在的市和县、总销售额以及用经度和纬度表示的空间位置。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-197">Each row in the result set contains a store identifier, store name, the area available for product display, the city and county where the store is located, the sales total, and the spatial location in longitude and latitude.</span></span> <span data-ttu-id="3c3f6-198">显示区域范围从 455 平方英尺到 1125 平方英尺。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-198">The display area ranges from 455 square feet to 1125 square feet.</span></span>  
  
10. <span data-ttu-id="3c3f6-199">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-199">Click **Next**.</span></span>  
  
     <span data-ttu-id="3c3f6-200">此时，将会为您创建一个名为 DataSet1 的报表数据集。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-200">The report dataset named DataSet1 is created for you.</span></span> <span data-ttu-id="3c3f6-201">在完成向导后，可以将“报表数据”用于其字段集合。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-201">After you complete the wizard, you can use the Report Data to its field collection.</span></span>  
  
11. <span data-ttu-id="3c3f6-202">在 "**选择空间数据和地图视图选项**" 页上，确认 "**空间" 字段**为 `SpatialLocation` ，"**层类型**" 为 "**点**"。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-202">On the **Choose a spatial data and map view options** page, verify that the **Spatial field** is `SpatialLocation` and that the **Layer type** is **Point**.</span></span> <span data-ttu-id="3c3f6-203">接受本页上的其他默认值。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-203">Accept the other defaults on this page.</span></span>  
  
     <span data-ttu-id="3c3f6-204">地图视图显示圆圈，这些圆圈标记了每个商店的位置。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-204">The map view displays circles that mark the location of each store.</span></span>  
  
12. <span data-ttu-id="3c3f6-205">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-205">Click **Next**.</span></span>  
  
13. <span data-ttu-id="3c3f6-206">指定一个地图类型，它显示随分析数据而改变的标记。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-206">Specify a map type that displays markers that vary by analytic data.</span></span> <span data-ttu-id="3c3f6-207">在 "选择地图可视化" 页上，单击 "**分析标记映射**"，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-207">On the Choose map visualization page, click **Analytical Marker Map**, and then click **Next**.</span></span>  
  
14. <span data-ttu-id="3c3f6-208">在 "**选择分析数据集**" 页上，单击 "DataSet1"。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-208">On the **Choose the analytical dataset** page, click DataSet1.</span></span> <span data-ttu-id="3c3f6-209">此数据集同时包含分析数据和空间数据，它将显示在新的点层上。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-209">This dataset contains both analytical data and spatial data that will be displayed on the new point layer.</span></span>  
  
15. <span data-ttu-id="3c3f6-210">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-210">Click **Next**.</span></span>  
  
16. <span data-ttu-id="3c3f6-211">在 "**选择颜色主题和数据可视化**" 页上，清除 "**使用标记颜色实现数据可视化**" 选项，然后选择选项 "**使用标记类型实现数据的可视化效果**"。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-211">On the **Choose color theme and data visualization** page, clear the **Use marker colors to visualize data** option, and then select the option **Use marker types to visualize data**.</span></span>  
  
17. <span data-ttu-id="3c3f6-212">在 "**数据" 字段**中，选择此项可根据 `[Sum(SellingArea)]` 商店设置的区域的大小改变标记类型以显示产品。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-212">In **Data field**, select `[Sum(SellingArea)]` to vary marker types by the size of the area a store sets aside to display the products.</span></span>  
  
18. <span data-ttu-id="3c3f6-213">单击“完成”。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-213">Click **Finish**.</span></span>  
  
     <span data-ttu-id="3c3f6-214">将向报表添加该地图层。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-214">The map layer is added to the report.</span></span> <span data-ttu-id="3c3f6-215">图例根据 SellingArea 值显示标记类型。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-215">The legend displays marker types based on SellingArea values.</span></span>  
  
     <span data-ttu-id="3c3f6-216">双击地图以显示“地图层”\*\*\*\* 窗格。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-216">Double-click the map to display the **Map Layer** pane.</span></span> <span data-ttu-id="3c3f6-217">“地图层”窗格显示新层“PointLayer1”，以及空间数据源类型“DataRegion”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-217">The **Map Layer** pane displays a new layer, PointLayer1, with spatial data source type **DataRegion**.</span></span>  
  
19. <span data-ttu-id="3c3f6-218">添加图例标题。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-218">Add a legend title.</span></span> <span data-ttu-id="3c3f6-219">右键单击图例标题，然后单击 "**图例标题属性**"。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-219">Right-click the legend title, and then click **Legend Title Properties**.</span></span>  
  
20. <span data-ttu-id="3c3f6-220">删除标题，然后键入\*\*显示区域 (平方英尺) \*\*。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-220">Delete the title, and type **Display Area (Square Feet)**.</span></span>  
  
21. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
22. <span data-ttu-id="3c3f6-221">查看向导设置的默认值。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-221">View the default values that were set by the wizard.</span></span> <span data-ttu-id="3c3f6-222">在 "**地图层" 窗格**中，右键单击点层，然后单击 "**标记类型规则**"。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-222">In the **Map Layers Pane**, right-click the point layer, and then click **Marker Type Rule**.</span></span>  
  
     <span data-ttu-id="3c3f6-223">在 "**常规**" 选项卡上，标记按它们在图例中的显示顺序列出。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-223">On the **General** tab, the markers are listed in the order in which they appear in the legend.</span></span> <span data-ttu-id="3c3f6-224">在 "**分发**" 选项卡上，子范围数为5。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-224">On the **Distribution** tab, the number of subranges is 5.</span></span> <span data-ttu-id="3c3f6-225">在 "**图例**" 选项卡上，图例文本设置为显示每个范围中的起始值和结束值。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-225">On the **Legend** tab, the legend text is set to display the start and end value in each range.</span></span>  
  
23. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
24. <span data-ttu-id="3c3f6-226">预览报表。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-226">Preview the report.</span></span>  
  
 <span data-ttu-id="3c3f6-227">该地图显示纽约州的商店的位置。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-227">The map displays the locations of stores in New York state.</span></span> <span data-ttu-id="3c3f6-228">每个商店的标记类型基于显示区域。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-228">The marker type for each store is based on the display area.</span></span> <span data-ttu-id="3c3f6-229">系统会自动为您计算五个范围的显示区域。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-229">Five ranges of display area were automatically calculated for you.</span></span>  
  
##  <a name="3-add-a-map-line-layer-to-display-a-route"></a><a name="LineLayer"></a><span data-ttu-id="3c3f6-230">3. 添加地图线条层以显示路线</span><span class="sxs-lookup"><span data-stu-id="3c3f6-230">3. Add a Map Line Layer to Display a Route</span></span>  
 <span data-ttu-id="3c3f6-231">使用地图层向导添加一个显示两个商店间路线的地图层。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-231">Use the map layer wizard to add a map layer that displays a route between two stores.</span></span> <span data-ttu-id="3c3f6-232">本教程中，通过三个商店位置创建路径。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-232">In this tutorial, the path is created from three store locations.</span></span> <span data-ttu-id="3c3f6-233">在业务应用程序中，路径可能是两个商店间的最佳路线。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-233">In a business application, the path might be the best route between stores.</span></span>  
  
#### <a name="to-add-a-line-layer-to-map"></a><span data-ttu-id="3c3f6-234">向地图添加线条层</span><span class="sxs-lookup"><span data-stu-id="3c3f6-234">To add a line layer to map</span></span>  
  
1.  <span data-ttu-id="3c3f6-235">切换到“设计”视图。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-235">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="3c3f6-236">双击地图以显示“地图层”\*\*\*\* 窗格。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-236">Double-click the map to display the **Map Layer** pane.</span></span> <span data-ttu-id="3c3f6-237">在工具栏上，单击 "**新建层向导**"。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-237">On the toolbar, click **New layer wizard**.</span></span>  
  
3.  <span data-ttu-id="3c3f6-238">在“选择空间数据的来源”\*\*\*\* 页上，选择“SQL Server 空间查询”\*\*\*\*，然后单击“下一步”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-238">On the **Choose a source of spatial data** page, select **SQL Server spatial query** and click **Next**.</span></span>  
  
4.  <span data-ttu-id="3c3f6-239">在“选择具有 SQL Server 空间数据的数据集”页上，单击“添加具有 SQL Server 空间数据的新数据集”，然后单击“下一步”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-239">On the **Choose a dataset with SQL Server spatial data** page, click **Add a new dataset with SQL Server spatial data** and click **Next**.</span></span>  
  
5.  <span data-ttu-id="3c3f6-240">在 "**选择与 SQL Server 空间数据源的连接**" 中，选择 "DataSource1"，即在第一个过程中创建的数据源。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-240">On the **Choose a connection to a SQL Server spatial data source**, select DataSource1, the data source that you created in the first procedure.</span></span>  
  
6.  <span data-ttu-id="3c3f6-241">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-241">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="3c3f6-242">在 "**设计查询**" 页上，单击 "**编辑为文本**"。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-242">On the **Design a Query** page, click **Edit as Text**.</span></span> <span data-ttu-id="3c3f6-243">查询设计器切换到基于文本的模式。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-243">The query designer switches to text-based mode.</span></span>  
  
8.  <span data-ttu-id="3c3f6-244">将以下文本粘贴到查询窗格中：</span><span class="sxs-lookup"><span data-stu-id="3c3f6-244">Paste the following text in the query pane:</span></span>  
  
    ```  
    SELECT N'Path' AS Name, CAST('LINESTRING(  
       -76.5001866085881 42.4310489934743,  
       -76.4602850815536 43.4353224527794,  
       -73.4728622833178 44.7028831413324)' AS geography) as Route  
    ```  
  
9. <span data-ttu-id="3c3f6-245">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-245">Click **Next**.</span></span>  
  
     <span data-ttu-id="3c3f6-246">此时，地图上将显示一条连接三个商店的路径。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-246">A path appears on the map that connects three stores.</span></span>  
  
10. <span data-ttu-id="3c3f6-247">在“选择空间数据和地图视图选项”页上，确认“空间字段”为“路线”，且“层类型”为“线条”\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-247">On the **Choose spatial data and map view options** page, verify that the **Spatial field** is **Route** and that the **Layer type** is **Line**.</span></span> <span data-ttu-id="3c3f6-248">接受其他默认值。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-248">Accept the other defaults.</span></span>  
  
     <span data-ttu-id="3c3f6-249">地图视图显示一条从位于纽约州北部的商店到位于纽约州南部商店的路径。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-249">The map view displays a path from a store in the northern part of New York state to a store in the southern part of New York state.</span></span>  
  
11. <span data-ttu-id="3c3f6-250">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-250">Click **Next**.</span></span>  
  
12. <span data-ttu-id="3c3f6-251">在“选择地图可视化”页上，单击“基本线条图”，然后单击“下一步”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-251">On the **Choose map visualization** page, click **Basic Line Map**, and then click **Next**.</span></span>  
  
13. <span data-ttu-id="3c3f6-252">在“选择颜色主题和数据可视化”上，选择“单色图”选项\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-252">On the **Choose color theme and data visualization**, select the option **Single color map**.</span></span> <span data-ttu-id="3c3f6-253">该路径基于所选主题显示为某种颜色。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-253">The path appears as a single color based on the selected theme.</span></span>  
  
14. <span data-ttu-id="3c3f6-254">单击“完成”。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-254">Click **Finish**.</span></span>  
  
 <span data-ttu-id="3c3f6-255">该地图显示了一个具有空间数据源类型**数据集**的新线条层。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-255">The map displays a new line layer with spatial data source type **DataSet**.</span></span> <span data-ttu-id="3c3f6-256">在本例中，空间数据来自数据源，但没有分析数据与此线条关联。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-256">In this example, the spatial data comes from a dataset but no analytical data is associated with the line.</span></span>  
  
##  <a name="4-add-a-bing-maps-tile-background"></a><a name="TileLayer"></a><span data-ttu-id="3c3f6-257">4. 添加 Bing 地图图块背景</span><span class="sxs-lookup"><span data-stu-id="3c3f6-257">4. Add a Bing Maps Tile Background</span></span>  
 <span data-ttu-id="3c3f6-258">添加一个地图层，用于显示 Bing 地图图块背景。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-258">Add a map layer that displays a Bing Maps tile background.</span></span>  
  
#### <a name="to-add-a-virtual-earth-tile-background"></a><span data-ttu-id="3c3f6-259">添加 Virtual Earth 图块背景</span><span class="sxs-lookup"><span data-stu-id="3c3f6-259">To add a Virtual Earth tile background</span></span>  
  
1.  <span data-ttu-id="3c3f6-260">切换到“设计”视图。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-260">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="3c3f6-261">双击地图以显示“地图层”\*\*\*\* 窗格。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-261">Double-click the map to display the **Map Layer** pane.</span></span> <span data-ttu-id="3c3f6-262">在工具栏上，单击“添加层”\*\*\*\*![rs_IconMapAddLayer](../../2014/tutorials/media/rs-iconmapaddlayer.gif "rs_IconMapAddLayer")。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-262">On the toolbar, click **Add Layer**![rs_IconMapAddLayer](../../2014/tutorials/media/rs-iconmapaddlayer.gif "rs_IconMapAddLayer").</span></span>  
  
3.  <span data-ttu-id="3c3f6-263">从下拉列表中，单击“图块层”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-263">From the drop-down list, click **Tile Layer**.</span></span>  
  
     <span data-ttu-id="3c3f6-264">“地图层”窗格中的最后一层为“TileLayer1”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-264">The last layer in the **Map Layer** pane is TileLayer1.</span></span> <span data-ttu-id="3c3f6-265">默认情况下，图块层显示道路图样式。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-265">By default, the tile layer displays the road map style.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3c3f6-266">在本向导中，还可以在“选择空间数据和地图视图选项”页上添加图块层\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-266">In the wizard, you can also add a tile layer on the **Choose spatial data and map view options** page.</span></span> <span data-ttu-id="3c3f6-267">若要执行此操作，请选择“为该地图视图添加必应地图背景”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-267">To do this, select **Add a Bing Maps background for this map view**.</span></span> <span data-ttu-id="3c3f6-268">在呈现的报表中，图块背景为当前地图视区中心和缩放级别显示 Bing 地图图块。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-268">In a rendered report, the tile background displays Bing Maps tiles for the current map viewport center and zoom level.</span></span>  
  
4.  <span data-ttu-id="3c3f6-269">单击 "TileLayer1" 上的向下箭头，然后单击 "**图块属性**"。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-269">Click the down arrow on TileLayer1, and then click **Tile Properties**.</span></span>  
  
5.  <span data-ttu-id="3c3f6-270">在 "**类型**" 中，选择 "**高空**"。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-270">In **Type**, select **Aerial**.</span></span> <span data-ttu-id="3c3f6-271">空中视图不包含文本。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-271">The aerial view does not contain text.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="5-make-a-layer-transparent"></a><a name="Transparent"></a><span data-ttu-id="3c3f6-272">5. 将层设置为透明</span><span class="sxs-lookup"><span data-stu-id="3c3f6-272">5. Make a Layer Transparent</span></span>  
 <span data-ttu-id="3c3f6-273">若希望某一层上的项透过另一层显示出来，则可以调整层的顺序以及每层的透明度以获得您想要的效果。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-273">To let the items on one layer show through another layer, you can adjust the order of layers and the transparency of each layer to get the effect that you want.</span></span>  
  
#### <a name="to-set-the-transparency-of-a-layer"></a><span data-ttu-id="3c3f6-274">设置层的透明度</span><span class="sxs-lookup"><span data-stu-id="3c3f6-274">To set the transparency of a layer</span></span>  
  
1.  <span data-ttu-id="3c3f6-275">切换到“设计”视图。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-275">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="3c3f6-276">双击地图以显示“地图层”\*\*\*\* 窗格。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-276">Double-click the map to display the **Map Layer** pane.</span></span>  
  
3.  <span data-ttu-id="3c3f6-277">单击 "PolygonLayer1" 上的向下箭头，然后单击 "**层数据**"。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-277">Click the down arrow on PolygonLayer1, and then click **Layer Data**.</span></span> <span data-ttu-id="3c3f6-278">将打开“地图多边形层属性”对话框\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-278">The **Map Polygon Layer Properties** dialog box opens.</span></span>  
  
4.  <span data-ttu-id="3c3f6-279">单击 **“可见性”** 。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-279">Click **Visibility**.</span></span>  
  
5.  <span data-ttu-id="3c3f6-280">在**透明度 (% ) **中，键入**30**。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-280">In **Transparency (%)**, type **30**.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
 <span data-ttu-id="3c3f6-281">设计图面将县显示为半透明。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-281">The design surface displays the counties as semi-transparent.</span></span>  
  
##  <a name="6-vary-county-color-based-on-sales"></a><a name="Vary"></a><span data-ttu-id="3c3f6-282">6. 根据销售改变县颜色</span><span class="sxs-lookup"><span data-stu-id="3c3f6-282">6. Vary County Color Based on Sales</span></span>  
 <span data-ttu-id="3c3f6-283">多边形层上的每个县都有一种不同的颜色，因为报表处理器会根据您在地图向导的最后一页选择的主题，自动从调色板中分配一个颜色值。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-283">Each county on the polygon layer has a different color because the report processor automatically assigns a color value from the color palette based on the theme that you chose on the last page of the map wizard.</span></span>  
  
 <span data-ttu-id="3c3f6-284">在下面的步骤中，指定颜色规则，以便将特定的颜色与每个县的商店销售额范围关联起来。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-284">In the following steps, specify a color rule to associate specific colors with a range of store sales for each county.</span></span> <span data-ttu-id="3c3f6-285">颜色红-黄-绿指示相应的高-中-低销售额。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-285">The colors red-yellow-green indicate relative high-middle-low sales.</span></span> <span data-ttu-id="3c3f6-286">设置色阶的格式以显示货币。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-286">Format the color scale to show currency.</span></span> <span data-ttu-id="3c3f6-287">在新的图例中显示年销售额范围。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-287">Display the annual sales ranges in a new legend.</span></span> <span data-ttu-id="3c3f6-288">对于不包含商店的县，不使用任何颜色，以指明没有关联的数据。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-288">For counties that do not contain stores, use no color to show that there is no associated data.</span></span>  
  
###  <a name="6a-build-a-relationship-between-spatial-and-analytical-data"></a><a name="Relationship"></a><span data-ttu-id="3c3f6-289">6a.</span><span class="sxs-lookup"><span data-stu-id="3c3f6-289">6a.</span></span> <span data-ttu-id="3c3f6-290">在空间数据与分析数据之间建立关系</span><span class="sxs-lookup"><span data-stu-id="3c3f6-290">Build a Relationship between Spatial and Analytical Data</span></span>  
 <span data-ttu-id="3c3f6-291">若要基于分析数据改变县形状中的颜色，首先必须将分析数据与空间数据关联起来。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-291">To vary the county shapes by color based on analytical data, you first must associate the analytical data with the spatial data.</span></span> <span data-ttu-id="3c3f6-292">在本教程中，您将使用要匹配的县名称。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-292">In this tutorial, you will use the county name to match on.</span></span>  
  
##### <a name="to-build-a-relationship-between-spatial-data-and-analytical-data"></a><span data-ttu-id="3c3f6-293">在空间数据与分析数据之间建立关系</span><span class="sxs-lookup"><span data-stu-id="3c3f6-293">To build a relationship between spatial data and analytical data</span></span>  
  
1.  <span data-ttu-id="3c3f6-294">切换到“设计”视图。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-294">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="3c3f6-295">双击地图以显示“地图层”\*\*\*\* 窗格。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-295">Double-click the map to display the **Map Layer** pane.</span></span>  
  
3.  <span data-ttu-id="3c3f6-296">单击 "PolygonLayer1" 上的向下箭头，然后单击 "**层数据**"。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-296">Click the down arrow on PolygonLayer1, and then click **Layer Data**.</span></span> <span data-ttu-id="3c3f6-297">将打开“地图多边形层属性”对话框\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-297">The **Map Polygon Layer Properties** dialog box opens.</span></span>  
  
4.  <span data-ttu-id="3c3f6-298">单击 **“分析数据”** 。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-298">Click **Analytical data**.</span></span>  
  
5.  <span data-ttu-id="3c3f6-299">从下拉列表中选择 DataSet1。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-299">From the drop-down list, select DataSet1.</span></span> <span data-ttu-id="3c3f6-300">此数据集是您为县指定空间数据查询时由向导创建的。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-300">This dataset was created by the wizard when you specified the spatial data query for the counties.</span></span>  
  
6.  <span data-ttu-id="3c3f6-301">在 "**要匹配的字段**" 中，单击 "**添加**"。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-301">In **Fields to match on**, click **Add**.</span></span> <span data-ttu-id="3c3f6-302">将添加一个新行。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-302">A new row is added.</span></span>  
  
7.  <span data-ttu-id="3c3f6-303">在 "**来自空间数据集**" 的下拉列表中，单击 "COUNTYNAME"。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-303">In **From spatial dataset**, from the drop-down list, click COUNTYNAME.</span></span>  
  
8.  <span data-ttu-id="3c3f6-304">在 "**来自分析数据集**" 的下拉列表中，单击 "[县]"。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-304">In **From analytical dataset**, from the drop-down list, click [County].</span></span>  
  
9. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
10. <span data-ttu-id="3c3f6-305">预览报表。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-305">Preview the report.</span></span>  
  
 <span data-ttu-id="3c3f6-306">通过从空间数据源和分析数据集中指定一个匹配字段，报表处理器可以基于地图元素对分析数据进行分组。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-306">By specifying a match field from the spatial data source and from the analytical dataset, you enable the report processor to group analytical data based on the map elements.</span></span> <span data-ttu-id="3c3f6-307">针对您指定的值，数据绑定的地图元素具有成功的匹配项。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-307">A data-bound map element has a successful match for the values that you specified.</span></span>  
  
 <span data-ttu-id="3c3f6-308">对于包含商店的每个县，其颜色取决于您在向导中选择的样式的调色板。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-308">Each county that contains a store has a color that is based on the color palette for the style that you chose in the wizard.</span></span>  
  
###  <a name="6b-specify-color-rules-for-polygons"></a><a name="ColorRules"></a><span data-ttu-id="3c3f6-309">60.</span><span class="sxs-lookup"><span data-stu-id="3c3f6-309">6b.</span></span> <span data-ttu-id="3c3f6-310">为多边形指定颜色规则</span><span class="sxs-lookup"><span data-stu-id="3c3f6-310">Specify Color Rules for Polygons</span></span>  
 <span data-ttu-id="3c3f6-311">若要创建根据商店销售额改变每个县颜色的规则，必须指定范围值、要显示的范围的划分数以及要使用的颜色。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-311">To create a rule that varies the color of each county based store sales, you must specify the range values, the number of divisions within that range that you want to display, and the colors to use.</span></span>  
  
##### <a name="to-specify-color-rules-for-all-polygons-that-have-associated-data"></a><span data-ttu-id="3c3f6-312">为具有关联数据的所有多边形指定颜色规则</span><span class="sxs-lookup"><span data-stu-id="3c3f6-312">To specify color rules for all polygons that have associated data</span></span>  
  
1.  <span data-ttu-id="3c3f6-313">切换到“设计”视图。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-313">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="3c3f6-314">单击 "PolygonLayer1" 上的向下箭头，然后单击 "**多边形颜色规则**"。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-314">Click the down arrow on PolygonLayer1, and then click **Polygon Color Rule**.</span></span> <span data-ttu-id="3c3f6-315">将打开“地图颜色规则属性”对话框\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-315">The **Map Color Rules Properties** dialog box opens.</span></span> <span data-ttu-id="3c3f6-316">请注意，已选择“使用调色板实现数据的可视化效果”颜色规则选项\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-316">Notice that the color rule option **Visualize data by using color palette** is selected.</span></span> <span data-ttu-id="3c3f6-317">此选项已由向导进行设置。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-317">This option was set by the wizard.</span></span>  
  
3.  <span data-ttu-id="3c3f6-318">选择“使用颜色范围实现数据的可视化效果”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-318">Select **Visualize data by using color ranges**.</span></span> <span data-ttu-id="3c3f6-319">调色板选项被开始颜色、中间颜色和结束颜色选项取代。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-319">The palette option is replaced by start color, middle color, and end color options.</span></span>  
  
4.  <span data-ttu-id="3c3f6-320">为每个县的销售额定义范围值。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-320">Define range values for sales per county.</span></span> <span data-ttu-id="3c3f6-321">在“数据字段”\*\*\*\* 中，从下拉列表中选择“`[Sum(Sales)]`”。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-321">In **Data field**, from the drop-down list, select `[Sum(Sales)]`.</span></span>  
  
5.  <span data-ttu-id="3c3f6-322">若要更改格式以便以千为单位显示货币，请将表达式更改为以下形式： `=Sum(Fields!Sales.Value)/1000`</span><span class="sxs-lookup"><span data-stu-id="3c3f6-322">To change the format to display currency in thousands, change the expression to the following: `=Sum(Fields!Sales.Value)/1000`</span></span>  
  
6.  <span data-ttu-id="3c3f6-323">将“开始颜色”\*\*\*\* 更改为“红色”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-323">Change **Start color** to **Red**.</span></span>  
  
7.  <span data-ttu-id="3c3f6-324">将“结束颜色”更改为“绿色”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-324">Change **End color** to **Green**.</span></span>  
  
     <span data-ttu-id="3c3f6-325">“红色”表示低销售值，“黄色”表示中等销售值，而“绿色”表示高销售值\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-325">**Red** represents low sales values, **Yellow** represents middle sales values, and **Green** represents high sales values.</span></span> <span data-ttu-id="3c3f6-326">报表处理器将基于这些值以及在“分布”页上选择的选项来计算颜色范围\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-326">The report processor calculates a range of colors based on these values and the options that you choose on the **Distribution** page.</span></span>  
  
8.  <span data-ttu-id="3c3f6-327">单击 **“分布”**。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-327">Click **Distribution**.</span></span>  
  
9. <span data-ttu-id="3c3f6-328">确认分布类型为“最佳”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-328">Verify that the distribution type is **Optimal**.</span></span> <span data-ttu-id="3c3f6-329">对于步骤 5 中的表达式，最佳分布将值划分到各个子范围，这些子范围在每个范围中的项数与每个范围的跨度之间实现平衡。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-329">For the expression from step 5, optimal distribution divides the values into subranges that balance the number of items in each range and the span for each range.</span></span>  
  
10. <span data-ttu-id="3c3f6-330">对于本页上的其他选项接受默认值。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-330">Accept the default values for other options on this page.</span></span> <span data-ttu-id="3c3f6-331">如果您选择最佳分布类型，则在运行报表时将计算子范围数。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-331">When you select the optimal distribution type, the number of subranges are calculated when the report runs.</span></span>  
  
11. <span data-ttu-id="3c3f6-332">单击 **“图例”**。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-332">Click **Legend**.</span></span>  
  
12. <span data-ttu-id="3c3f6-333">在“色阶选项”中，确认已选中“在色阶中显示”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-333">In **Color scale options**, verify that **Show in color scale** is selected.</span></span>  
  
13. <span data-ttu-id="3c3f6-334">在“在此图例中显示”中，从下拉列表中选择空行\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-334">In **Show in this legend**, from the drop-down list, select the blank line.</span></span> <span data-ttu-id="3c3f6-335">现在，您只将颜色范围显示在色阶中。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-335">For now, you will show the color ranges only in the color scale.</span></span>  
  
14. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
 <span data-ttu-id="3c3f6-336">色阶显示五种颜色：红色、橙色、黄色、黄绿色和绿色。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-336">The color scale displays five colors: red, orange, yellow, yellow green, and green.</span></span> <span data-ttu-id="3c3f6-337">每个颜色表示一个销售额范围，此范围是以县为单位根据销售额自动计算得出的。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-337">Each color represents a sales range that is automatically calculated based on the sales by county.</span></span>  
  
###  <a name="6c-format-the-data-in-the-color-scale-as-currency"></a><a name="ColorScale"></a><span data-ttu-id="3c3f6-338">6c.</span><span class="sxs-lookup"><span data-stu-id="3c3f6-338">6c.</span></span> <span data-ttu-id="3c3f6-339">将色阶中的数据的格式设置为“货币”</span><span class="sxs-lookup"><span data-stu-id="3c3f6-339">Format the Data in the Color Scale as Currency</span></span>  
 <span data-ttu-id="3c3f6-340">默认情况下，数据具有常规格式。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-340">By default, data has a general format.</span></span> <span data-ttu-id="3c3f6-341">您可以应用自定义格式。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-341">You can apply custom formats.</span></span>  
  
##### <a name="to-set-the-format-for-the-color-scale"></a><span data-ttu-id="3c3f6-342">设置色阶的格式</span><span class="sxs-lookup"><span data-stu-id="3c3f6-342">To set the format for the color scale</span></span>  
  
1.  <span data-ttu-id="3c3f6-343">右键单击色阶，然后单击 "色阶**属性**"。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-343">Right-click the color scale, and then click **Color Scale Properties**.</span></span>  
  
2.  <span data-ttu-id="3c3f6-344">单击 "**数字**"。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-344">Click **Number**.</span></span>  
  
3.  <span data-ttu-id="3c3f6-345">在 "**类别**" 中，单击 "**货币**"。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-345">In **Category**, click **Currency**.</span></span>  
  
4.  <span data-ttu-id="3c3f6-346">在 "**小数位数**" 中，键入**0**。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-346">In **Decimal places**, type **0**.</span></span> <span data-ttu-id="3c3f6-347">此格式指定货币没有小数位。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-347">This format specifies no decimal places for currency.</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="3c3f6-348">预览报表。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-348">Preview the report.</span></span>  
  
 <span data-ttu-id="3c3f6-349">色阶对于每个范围用货币格式显示年销售额。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-349">The color scale displays annual sales in currency format for each range.</span></span>  
  
###  <a name="6d-create-a-new-legend"></a><a name="NewLegend"></a><span data-ttu-id="3c3f6-350">6d.</span><span class="sxs-lookup"><span data-stu-id="3c3f6-350">6d.</span></span> <span data-ttu-id="3c3f6-351">创建新图例</span><span class="sxs-lookup"><span data-stu-id="3c3f6-351">Create a New Legend</span></span>  
 <span data-ttu-id="3c3f6-352">默认情况下，所有规则显示在第一个图例中。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-352">By default, all rules display in the first legend.</span></span> <span data-ttu-id="3c3f6-353">若要改进地图的显示效果，可以添加图例。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-353">To improve the display for a map, you can add legends.</span></span>  
  
 <span data-ttu-id="3c3f6-354">若要更改默认显示，有两个步骤：创建新的图例，然后将地图层的规则结果与新的图例相关联。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-354">To change the default display, there are two steps: create a new legend and then associate the rule results for a map layer with the new legend.</span></span>  
  
##### <a name="to-create-a-new-legend"></a><span data-ttu-id="3c3f6-355">创建新图例</span><span class="sxs-lookup"><span data-stu-id="3c3f6-355">To create a new legend</span></span>  
  
1.  <span data-ttu-id="3c3f6-356">切换到“设计”视图。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-356">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="3c3f6-357">右键单击视区外的地图，然后单击 "**添加图例**"。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-357">Right-click the map outside the viewport, and then click **Add Legend**.</span></span> <span data-ttu-id="3c3f6-358">将在默认位置向地图添加新图例。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-358">A new legend is added to the map at a default location.</span></span>  
  
3.  <span data-ttu-id="3c3f6-359">右键单击图例，然后单击 "**图例属性**"。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-359">Right-click the legend, and then click **Legend Properties**.</span></span>  
  
4.  <span data-ttu-id="3c3f6-360">在 "**位置选项**" 中，单击指定图例相对于视区的显示位置的位置。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-360">In **Position options**, click the location that specifies where you want the legend to appear relative to the viewport.</span></span> <span data-ttu-id="3c3f6-361">设计图面上的地图将更改以显示您的选择效果。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-361">The map on the design surface changes to show the effect of your selections.</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="3c3f6-362">单击图例上的**标题**以选择图例标题。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-362">Click **Title** on the legend to select the legend title.</span></span>  
  
7.  <span data-ttu-id="3c3f6-363">再次单击 "**标题**" 以进入文本插入模式。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-363">Click **Title** again to enter insert mode for the text.</span></span> <span data-ttu-id="3c3f6-364">按销售额将**标题**替换\*\* (千) \*\*，然后在文本外部单击。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-364">Replace **Title** by **Sales (Thousands)**, and then click outside the text.</span></span>  
  
 <span data-ttu-id="3c3f6-365">图例将展开以显示标题。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-365">The legend expands to display the title.</span></span>  
  
###  <a name="6e-associate-legend-and-color-rules"></a><a name="Associate"></a><span data-ttu-id="3c3f6-366">6e.</span><span class="sxs-lookup"><span data-stu-id="3c3f6-366">6e.</span></span> <span data-ttu-id="3c3f6-367">将图例与颜色规则关联</span><span class="sxs-lookup"><span data-stu-id="3c3f6-367">Associate Legend and Color Rules</span></span>  
 <span data-ttu-id="3c3f6-368">每个图例可以显示一组或多组规则结果。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-368">Each legend can display one or more sets of rule results.</span></span>  
  
##### <a name="to-associate-a-legend-with-color-rules"></a><span data-ttu-id="3c3f6-369">将图例与颜色规则关联</span><span class="sxs-lookup"><span data-stu-id="3c3f6-369">To associate a legend with color rules</span></span>  
  
1.  <span data-ttu-id="3c3f6-370">双击地图以显示“地图层”\*\*\*\* 窗格。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-370">Double-click the map to display the **Map Layer** pane.</span></span>  
  
2.  <span data-ttu-id="3c3f6-371">单击 "PolygonLayer1" 上的向下箭头，然后单击 "**多边形颜色规则**"。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-371">Click the down arrow on PolygonLayer1, and then click **Polygon Color Rule**.</span></span> <span data-ttu-id="3c3f6-372">将打开“地图颜色规则属性”对话框\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-372">The **Map Color Rules Properties** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="3c3f6-373">单击 **“图例”**。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-373">Click **Legend**.</span></span>  
  
4.  <span data-ttu-id="3c3f6-374">在 "色阶**选项**" 中，清除 "**在色阶中显示**"。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-374">In **Color scale options**, clear **Show in color scale**.</span></span>  
  
5.  <span data-ttu-id="3c3f6-375">在 "**图例选项**" 的下拉列表中，选择 "Legend2"。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-375">In **Legend options**, from the drop-down list, select Legend2.</span></span> <span data-ttu-id="3c3f6-376">将显示图例文本选项。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-376">The legend text option appears.</span></span> <span data-ttu-id="3c3f6-377">默认情况下使用常规 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 格式字符串设置图例文本的格式。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-377">By default, legend text is formatted with a general [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] format string.</span></span> <span data-ttu-id="3c3f6-378">N0 中的 0 指定没有小数位数。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-378">The 0 in N0 specifies no decimal digits.</span></span>  
  
6.  <span data-ttu-id="3c3f6-379">在 "**图例文本**" 中，使用以下格式指定没有小数位数的货币：`#FROMVALUE {C0} - #TOVALUE {C0}`</span><span class="sxs-lookup"><span data-stu-id="3c3f6-379">In **Legend text**, use the following format to specify currency with no decimal digits: `#FROMVALUE {C0} - #TOVALUE {C0}`</span></span>  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="3c3f6-380">在设计图面上，图例显示颜色范围，且示例数据的格式设置为货币。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-380">On the design surface, the legend displays the color ranges with sample data formatted as currency.</span></span>  
  
8.  <span data-ttu-id="3c3f6-381">预览报表。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-381">Preview the report.</span></span>  
  
 <span data-ttu-id="3c3f6-382">具有关联的商店和销售额的县根据颜色规则进行显示。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-382">The counties that have associated stores and sales display according to the color rules.</span></span> <span data-ttu-id="3c3f6-383">没有销售额的县没有颜色。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-383">Counties that have no sales have no color.</span></span>  
  
###  <a name="6f-change-color-for-counties-with-no-data"></a><a name="NoData"></a><span data-ttu-id="3c3f6-384">6f.</span><span class="sxs-lookup"><span data-stu-id="3c3f6-384">6f.</span></span> <span data-ttu-id="3c3f6-385">更改没有数据的县的颜色</span><span class="sxs-lookup"><span data-stu-id="3c3f6-385">Change Color for Counties with No Data</span></span>  
 <span data-ttu-id="3c3f6-386">可以为层上所有地图元素设置默认显示选项。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-386">You can set the default display options for all map elements on a layer.</span></span> <span data-ttu-id="3c3f6-387">颜色规则优先于这些显示选项。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-387">Color rules take precedence over these display options.</span></span>  
  
##### <a name="to-set-the-display-properties-for-all-elements-on-a-layer"></a><span data-ttu-id="3c3f6-388">为层上的所有元素设置显示属性</span><span class="sxs-lookup"><span data-stu-id="3c3f6-388">To set the display properties for all elements on a layer</span></span>  
  
1.  <span data-ttu-id="3c3f6-389">切换到“设计”视图。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-389">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="3c3f6-390">双击地图以显示“地图层”\*\*\*\* 窗格。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-390">Double-click the map to display the **Map Layer** pane.</span></span>  
  
3.  <span data-ttu-id="3c3f6-391">单击“PolygonLayer1”上的向下箭头，然后单击“多边形属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-391">Click the down arrow on PolygonLayer1, and then click **Polygon Properties**.</span></span> <span data-ttu-id="3c3f6-392">将打开“地图多边形属性”对话框\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-392">The **Map Polygon Properties** dialog box opens.</span></span> <span data-ttu-id="3c3f6-393">在应用基于规则的显示选项之前，此对话框中设置的显示选项将应用于层上的所有多边形。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-393">Display options set in this dialog box apply to all polygons on the layer before rule-based display options are applied.</span></span>  
  
4.  <span data-ttu-id="3c3f6-394">单击 "**填充**"。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-394">Click **Fill**.</span></span>  
  
5.  <span data-ttu-id="3c3f6-395">验证填充样式是否为**纯色。**</span><span class="sxs-lookup"><span data-stu-id="3c3f6-395">Verify that the fill style is **Solid.**</span></span> <span data-ttu-id="3c3f6-396">。渐变样式和图案样式应用于所有颜色。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-396">Gradients and patterns apply to all colors.</span></span>  
  
6.  <span data-ttu-id="3c3f6-397">在 "**颜色**" 中，单击向下箭头，然后单击 "**浅钢蓝色**"。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-397">In **Color**, click the down arrow, and then click **Light Steel Blue**.</span></span>  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
8.  <span data-ttu-id="3c3f6-398">预览报表。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-398">Preview the report.</span></span>  
  
 <span data-ttu-id="3c3f6-399">不具有关联数据的县显示为蓝色。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-399">Counties that have no associated data display as blue.</span></span> <span data-ttu-id="3c3f6-400">只有具有关联分析数据的县才会根据指定的颜色规则显示为**红色**到**绿色**颜色。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-400">Only counties that have associated analytical data appear in the **Red** through **Green** colors from the color rules that you specified.</span></span>  
  
##  <a name="7-add-a-custom-point"></a><a name="CustomPoint"></a><span data-ttu-id="3c3f6-401">7. 添加自定义点</span><span class="sxs-lookup"><span data-stu-id="3c3f6-401">7. Add a Custom Point</span></span>  
 <span data-ttu-id="3c3f6-402">若要表示尚未生成的新存储，请指定一个点并使用**图钉**标记类型。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-402">To represent a new store that has not yet been built, specify a point and use the **PushPin** marker type.</span></span>  
  
#### <a name="to-add-a-custom-point"></a><span data-ttu-id="3c3f6-403">添加自定义点</span><span class="sxs-lookup"><span data-stu-id="3c3f6-403">To add a custom point</span></span>  
  
1.  <span data-ttu-id="3c3f6-404">切换到“设计”视图。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-404">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="3c3f6-405">双击地图以显示“地图层”\*\*\*\* 窗格。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-405">Double-click the map to display the **Map Layer** pane.</span></span> <span data-ttu-id="3c3f6-406">在工具栏上，单击 "**添加层**"，然后单击 "**点层**"。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-406">On the toolbar, click **Add Layer**, and then click **Point Layer**.</span></span>  
  
     <span data-ttu-id="3c3f6-407">将向地图添加一个新点层。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-407">A new point layer is added to the map.</span></span> <span data-ttu-id="3c3f6-408">默认情况下，该点层的空间数据类型为“嵌入”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-408">By default, the point layer has spatial data type **Embedded**.</span></span>  
  
3.  <span data-ttu-id="3c3f6-409">单击 "PointLayer2" 上的向下箭头，然后单击 "**添加点**"。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-409">Click the down arrow on PointLayer2, and then click **Add Point**.</span></span>  
  
4.  <span data-ttu-id="3c3f6-410">将指针移到地图视区上方。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-410">Move the pointer over the map viewport.</span></span> <span data-ttu-id="3c3f6-411">光标将变为十字准线。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-411">The cursor changes to crosshairs.</span></span>  
  
5.  <span data-ttu-id="3c3f6-412">单击地图上您要添加点的位置。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-412">Click the location on the map where you want to add a point.</span></span> <span data-ttu-id="3c3f6-413">在本教程中，单击县中路线起点旁边的位置。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-413">In this tutorial, click a location in a county next to the start of the route.</span></span> <span data-ttu-id="3c3f6-414">用圆圈标记的点将添加到层中您单击的位置。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-414">A point marked by a circle is added to the layer at the location where you clicked.</span></span> <span data-ttu-id="3c3f6-415">默认情况下，该点处于选中状态。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-415">By default, the point is selected.</span></span>  
  
6.  <span data-ttu-id="3c3f6-416">右键单击添加的点，然后单击“嵌入的点属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-416">Right-click the point you added, and then click **Embedded Point Properties**.</span></span>  
  
7.  <span data-ttu-id="3c3f6-417">选择 "**覆盖此层的点选项**" 选项。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-417">Select the option **Override point options for this layer**.</span></span> <span data-ttu-id="3c3f6-418">其他页将显示在对话框中。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-418">Additional pages appear in the dialog box.</span></span> <span data-ttu-id="3c3f6-419">您在此处设置的值优先于层或颜色规则的显示选项。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-419">Values that you set here take precedence over display options for the layer or for color rules.</span></span>  
  
8.  <span data-ttu-id="3c3f6-420">单击 "**标记**"。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-420">Click **Marker**.</span></span>  
  
9. <span data-ttu-id="3c3f6-421">对于 "**标记类型**"，请选择**星号**。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-421">For **Marker type**, select **Star**.</span></span>  
  
10. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
11. <span data-ttu-id="3c3f6-422">预览报表。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-422">Preview the report.</span></span>  
  
 <span data-ttu-id="3c3f6-423">您添加的新点将显示为**星号**。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-423">The new point you added appears as a **Star**.</span></span>  
  
#### <a name="to-add-a-label-for-the-custom-point"></a><span data-ttu-id="3c3f6-424">为自定义点添加标签</span><span class="sxs-lookup"><span data-stu-id="3c3f6-424">To add a label for the custom point</span></span>  
  
1.  <span data-ttu-id="3c3f6-425">切换到“设计”视图。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-425">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="3c3f6-426">右键单击刚添加的点，然后单击 "嵌入的**点属性**"。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-426">Right-click the point you just added, and then click **Embedded Point Properties**.</span></span>  
  
3.  <span data-ttu-id="3c3f6-427">单击 "**标签**"。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-427">Click **Labels**.</span></span>  
  
4.  <span data-ttu-id="3c3f6-428">在 "**标签文本**" 中，键入**New Store**。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-428">In **Label text**, type **New Store**.</span></span>  
  
5.  <span data-ttu-id="3c3f6-429">在“位置”中，单击“顶部”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-429">In **Placement**, click **Top**.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  <span data-ttu-id="3c3f6-430">预览报表。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-430">Preview the report.</span></span>  
  
 <span data-ttu-id="3c3f6-431">标签显示在商店位置上方。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-431">The label appears above the store location.</span></span>  
  
##  <a name="center-the-map-view"></a><a name="CenterView"></a><span data-ttu-id="3c3f6-432">居中对齐地图视图</span><span class="sxs-lookup"><span data-stu-id="3c3f6-432">Center the Map View</span></span>  
 <span data-ttu-id="3c3f6-433">更改地图视区中心和缩放级别。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-433">Change the map viewport center and zoom level.</span></span>  
  
#### <a name="to-change-the-viewport"></a><span data-ttu-id="3c3f6-434">更改视区</span><span class="sxs-lookup"><span data-stu-id="3c3f6-434">To change the viewport</span></span>  
  
1.  <span data-ttu-id="3c3f6-435">右键单击地图视区，然后单击 "**视区属性**"。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-435">Right-click the map viewport, and then click **Viewport Properties**.</span></span>  
  
2.  <span data-ttu-id="3c3f6-436">单击 "**中心和缩放**"。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-436">Click **Center and Zoom**.</span></span>  
  
3.  <span data-ttu-id="3c3f6-437">验证是否已选择 "**设置视图中心和缩放级别**" 选项。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-437">Verify that the option **Set a view center and zoom level** is selected.</span></span>  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="3c3f6-438">左键单击地图视区，并将视区中心拖到您希望的位置。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-438">Left-click the map viewport, and drag the center of the viewport to the location that you want.</span></span>  
  
6.  <span data-ttu-id="3c3f6-439">使用鼠标滚轮更改视区的缩放级别。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-439">Use the mouse wheel to change the zoom level of the viewport.</span></span>  
  
7.  <span data-ttu-id="3c3f6-440">预览报表。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-440">Preview the report.</span></span>  
  
 <span data-ttu-id="3c3f6-441">在“设计”视图中，显示图面上的地图以及视图基于示例数据。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-441">In Design view, the map on the display surface and the view is based on sample data.</span></span> <span data-ttu-id="3c3f6-442">在呈现的报表中，地图视图位于您指定的视图的中心。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-442">In the rendered report, the map view is centered on the view that you specified.</span></span>  
  
##  <a name="add-a-report-title"></a><a name="Title"></a><span data-ttu-id="3c3f6-443">添加报表标题</span><span class="sxs-lookup"><span data-stu-id="3c3f6-443">Add a Report Title</span></span>  
  
#### <a name="to-add-a-report-title"></a><span data-ttu-id="3c3f6-444">添加报表标题</span><span class="sxs-lookup"><span data-stu-id="3c3f6-444">To add a report title</span></span>  
  
1.  <span data-ttu-id="3c3f6-445">在设计图面上，单击“单击以添加标题”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-445">On the design surface, click **Click to add title**.</span></span>  
  
2.  <span data-ttu-id="3c3f6-446">键入 **Sales in New York Stores** ，然后在文本框外部单击。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-446">Type **Sales in New York Stores** and then click outside the text box.</span></span>  
  
 <span data-ttu-id="3c3f6-447">此标题将显示在报表的顶部。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-447">This title will appear at the top of the report.</span></span> <span data-ttu-id="3c3f6-448">当未定义页眉时，表体顶部的项等同于报表表头。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-448">Items at the top of the report body when there is no page header defined are the equivalent of a report header.</span></span>  
  
##  <a name="save-the-report"></a><a name="Save"></a><span data-ttu-id="3c3f6-449">保存报表</span><span class="sxs-lookup"><span data-stu-id="3c3f6-449">Save the Report</span></span>  
  
#### <a name="to-save-the-report"></a><span data-ttu-id="3c3f6-450">保存报表</span><span class="sxs-lookup"><span data-stu-id="3c3f6-450">To save the report</span></span>  
  
1.  <span data-ttu-id="3c3f6-451">切换到“设计”视图。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-451">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="3c3f6-452">从 “报表生成器” 按钮，单击 **“另存为”**。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-452">From the Report Builder button, click **Save As**.</span></span>  
  
3.  <span data-ttu-id="3c3f6-453">在“名称”中，键入“纽约的商店销售额”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-453">In **Name**, type **Store Sales in New York**.</span></span>  
  
 <span data-ttu-id="3c3f6-454">单击“ **保存**”。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-454">Click **Save**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="3c3f6-455">后续步骤</span><span class="sxs-lookup"><span data-stu-id="3c3f6-455">Next Steps</span></span>  
 <span data-ttu-id="3c3f6-456">到此为止，我们结束了有关如何向报表添加地图的演练。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-456">This concludes the walkthrough for how to add a map to your report.</span></span>  
  
 <span data-ttu-id="3c3f6-457">有关详细信息，请参阅[Maps &#40;报表生成器和 SSRS&#41;](report-design/maps-report-builder-and-ssrs.md)和博客条目为 blogs.msdn.com 上的[SQL Server Reporting Services 调整空间数据的 cartographic adjustment of](https://go.microsoft.com/fwlink/?LinkId=152771) 。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-457">For more information, see [Maps &#40;Report Builder and SSRS&#41;](report-design/maps-report-builder-and-ssrs.md) and the blog entry [Cartographic Adjustment of Spatial Data for SQL Server Reporting Services](https://go.microsoft.com/fwlink/?LinkId=152771) on blogs.msdn.com.</span></span>  
  
 <span data-ttu-id="3c3f6-458">有关更多教程，请参阅[教程 &#40;报表生成器&#41;](report-builder-tutorials.md)。</span><span class="sxs-lookup"><span data-stu-id="3c3f6-458">For more tutorials, see [Tutorials &#40;Report Builder&#41;](report-builder-tutorials.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c3f6-459">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3c3f6-459">See Also</span></span>  
 <span data-ttu-id="3c3f6-460">[教程 &#40;报表生成器&#41;](report-builder-tutorials.md) </span><span class="sxs-lookup"><span data-stu-id="3c3f6-460">[Tutorials &#40;Report Builder&#41;](report-builder-tutorials.md) </span></span>  
 <span data-ttu-id="3c3f6-461">[SQL Server 2014 中的报表生成器](report-builder/report-builder-in-sql-server-2016.md) </span><span class="sxs-lookup"><span data-stu-id="3c3f6-461">[Report Builder in SQL Server 2014](report-builder/report-builder-in-sql-server-2016.md) </span></span>  
 <span data-ttu-id="3c3f6-462">[地图向导和地图层向导 &#40;报表生成器和 SSRS&#41;](report-design/map-wizard-and-map-layer-wizard-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="3c3f6-462">[Map Wizard and Map Layer Wizard &#40;Report Builder and SSRS&#41;](report-design/map-wizard-and-map-layer-wizard-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="3c3f6-463">按规则和分析数据更改多边形、线条和点的显示方式（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="3c3f6-463">Vary Polygon, Line, and Point Display by Rules and Analytical Data &#40;Report Builder and SSRS&#41;</span></span>](report-design/vary-polygon-line-and-point-display-by-rules-and-analytical-data.md)  
  
  
