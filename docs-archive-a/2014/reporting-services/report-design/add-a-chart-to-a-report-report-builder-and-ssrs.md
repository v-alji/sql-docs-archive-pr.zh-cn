---
title: 向报表添加图表（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a6b595dc-f775-4a53-8554-74a0bf9335ec
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 789dd6cce10b0425833ea63f2f7941ea75970a25
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577298"
---
# <a name="add-a-chart-to-a-report-report-builder-and-ssrs"></a><span data-ttu-id="4b465-102">向报表添加图表（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="4b465-102">Add a Chart to a Report (Report Builder and SSRS)</span></span>
  <span data-ttu-id="4b465-103">如果要以可视化格式汇总数据，请使用图表数据区域。</span><span class="sxs-lookup"><span data-stu-id="4b465-103">When you want to summarize data in a visual format, use a Chart data region.</span></span> <span data-ttu-id="4b465-104">为您要呈现的数据类型选择一种适当的图表类型非常重要。</span><span class="sxs-lookup"><span data-stu-id="4b465-104">It is important to choose an appropriate chart type for the type of data that you are presenting.</span></span> <span data-ttu-id="4b465-105">这将影响数据以图表形式呈现时对数据进行解释的好坏程度。</span><span class="sxs-lookup"><span data-stu-id="4b465-105">This affects how well the data can be interpreted when put in chart form.</span></span> <span data-ttu-id="4b465-106">有关详细信息，请参阅 [图表（报表生成器和 SSRS）](charts-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="4b465-106">For more information, see [Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="4b465-107">将图表数据区域添加到报表中的最简单方式是运行新建图表向导。</span><span class="sxs-lookup"><span data-stu-id="4b465-107">The simplest way to add a Chart data region to your report is to run the New Chart Wizard.</span></span> <span data-ttu-id="4b465-108">该向导提供柱形图、折线图、饼图、条形图和面积图。</span><span class="sxs-lookup"><span data-stu-id="4b465-108">The wizard offers column, line, pie, bar, and area charts.</span></span> <span data-ttu-id="4b465-109">对于这些图表类型和其他图表类型，还可以手动添加图表。</span><span class="sxs-lookup"><span data-stu-id="4b465-109">For these and other chart types, you can also add a chart manually.</span></span>  
  
 <span data-ttu-id="4b465-110">将图表数据区域添加到设计图面后，可以将数值数据和非数值数据的报表数据集字段拖到图表的“图表数据”窗格中。</span><span class="sxs-lookup"><span data-stu-id="4b465-110">After you add a Chart data region to the design surface, you can drag report dataset fields for numeric and non-numeric data to the Chart Data pane of the chart.</span></span> <span data-ttu-id="4b465-111">单击图表可以显示“图表数据”窗格，并且它具有三个区域（类别组、序列组和值）。</span><span class="sxs-lookup"><span data-stu-id="4b465-111">Click the chart to display the Chart Data pane with its three areas: Series Groups, Category Groups, and Values.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-chart-to-a-report-by-using-the-chart-wizard"></a><span data-ttu-id="4b465-112">通过使用图表向导将图表添加到报表</span><span class="sxs-lookup"><span data-stu-id="4b465-112">To add a chart to a report by using the Chart Wizard</span></span>  
  
1.  > [!NOTE]  
    >  <span data-ttu-id="4b465-113">该图表向导仅在报表生成器中提供。</span><span class="sxs-lookup"><span data-stu-id="4b465-113">The Chart Wizard is only available in Report Builder.</span></span>  
  
     <span data-ttu-id="4b465-114">在 **“插入”** 选项卡上，单击 **“图表”** ，然后单击 **“图表向导”** 。</span><span class="sxs-lookup"><span data-stu-id="4b465-114">On the **Insert** tab, click **Chart**, and then click **Chart Wizard**.</span></span>  
  
2.  <span data-ttu-id="4b465-115">执行 **“新建图表”** 向导中的步骤。</span><span class="sxs-lookup"><span data-stu-id="4b465-115">Follow the steps in the **New** Chart wizard.</span></span>  
  
3.  <span data-ttu-id="4b465-116">在 **“主文件夹”** 选项卡上，单击 **“运行”** ，以查看所呈现的报表。</span><span class="sxs-lookup"><span data-stu-id="4b465-116">On the **Home** tab, click **Run** to see the rendered report.</span></span>  
  
4.  <span data-ttu-id="4b465-117">在 **“运行”** 选项卡上，单击 **“设计”** 以继续处理报表。</span><span class="sxs-lookup"><span data-stu-id="4b465-117">On the **Run** tab, click **Design** to continue working on the report.</span></span>  
  
### <a name="to-add-a-chart-to-a-report"></a><span data-ttu-id="4b465-118">向报表添加图表</span><span class="sxs-lookup"><span data-stu-id="4b465-118">To add a chart to a report</span></span>  
  
1.  <span data-ttu-id="4b465-119">创建一个报表，并定义一个数据集。</span><span class="sxs-lookup"><span data-stu-id="4b465-119">Create a report and define a dataset.</span></span> <span data-ttu-id="4b465-120">有关详细信息，请参阅[将数据添加到报表 &#40;报表生成器和 SSRS&#41;](../report-data/report-datasets-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="4b465-120">For more information, see [Add Data to a Report &#40;Report Builder and SSRS&#41;](../report-data/report-datasets-ssrs.md).</span></span>  
  
2.  <span data-ttu-id="4b465-121">在 **“插入”** 选项卡上，单击 **“图表”** ，然后单击 **“插入图表”** 。</span><span class="sxs-lookup"><span data-stu-id="4b465-121">On the **Insert** tab, click **Chart**, and then click **Insert Chart**.</span></span>  
  
3.  <span data-ttu-id="4b465-122">在设计图面上，单击希望图表左上角所处的位置，并拖动至希望图表右下角所处的位置。</span><span class="sxs-lookup"><span data-stu-id="4b465-122">Click on the design surface where you want the upper-left corner of the chart, and then drag to where you want the lower-right corner of the chart.</span></span>  
  
     <span data-ttu-id="4b465-123">将出现 **“选择图表类型”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="4b465-123">The **Select Chart Type** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="4b465-124">选择要添加的图表类型。</span><span class="sxs-lookup"><span data-stu-id="4b465-124">Select the type of chart you want to add.</span></span> [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="4b465-125">单击图表以显示 **“图表数据”** 窗格。</span><span class="sxs-lookup"><span data-stu-id="4b465-125">Click the chart to display the **Chart Data** pane.</span></span>  
  
6.  <span data-ttu-id="4b465-126">将一个或多个字段添加到 **“值”** 区域。</span><span class="sxs-lookup"><span data-stu-id="4b465-126">Add one or more fields to the **Values** area.</span></span> <span data-ttu-id="4b465-127">此信息将绘制在值轴上。</span><span class="sxs-lookup"><span data-stu-id="4b465-127">This information will be plotted on the value axis.</span></span>  
  
7.  <span data-ttu-id="4b465-128">向 **“类别组”** 区域添加分组字段。</span><span class="sxs-lookup"><span data-stu-id="4b465-128">Add a grouping field to the **Category Groups** area.</span></span> <span data-ttu-id="4b465-129">将此字段添加到 **“类别组”** 区域时，将自动创建一个分组字段。</span><span class="sxs-lookup"><span data-stu-id="4b465-129">When you add this field to the **Category Groups** area, a grouping field is automatically created for you.</span></span> <span data-ttu-id="4b465-130">每个组都表示序列中的一个数据点。</span><span class="sxs-lookup"><span data-stu-id="4b465-130">Each group represents a data point in your series.</span></span>  
  
8.  <span data-ttu-id="4b465-131">若要按类别汇总数据，请右键单击数据字段，然后单击“序列属性”  。</span><span class="sxs-lookup"><span data-stu-id="4b465-131">To summarize the data by category, right-click the data field and click **Series Properties**.</span></span> <span data-ttu-id="4b465-132">在“类别”框中，从下拉列表中选择类别字段  。</span><span class="sxs-lookup"><span data-stu-id="4b465-132">In the **Category** box, select the category field from the drop-down list.</span></span> [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
9. <span data-ttu-id="4b465-133">在 **“主文件夹”** 选项卡上，单击 **“运行”** ，以查看所呈现的报表。</span><span class="sxs-lookup"><span data-stu-id="4b465-133">On the **Home** tab, click **Run** to see the rendered report.</span></span>  
  
10. <span data-ttu-id="4b465-134">在 **“运行”** 选项卡上，单击 **“设计”** 以继续处理报表。</span><span class="sxs-lookup"><span data-stu-id="4b465-134">On the **Run** tab, click **Design** to continue working on the report.</span></span>  
  
 <span data-ttu-id="4b465-135">在具有轴的图表（如条形图和柱形图）中，类别轴可能不会显示所有的类别标签。</span><span class="sxs-lookup"><span data-stu-id="4b465-135">On charts with axes, such as bar and column charts, the category axis may not display all the category labels.</span></span> <span data-ttu-id="4b465-136">有关如何更改轴标签的详细信息，请参阅[指定轴间隔（报表生成器和 SSRS）](specify-an-axis-interval-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="4b465-136">For more information about how to change the axis labels, see [Specify an Axis Interval &#40;Report Builder and SSRS&#41;](specify-an-axis-interval-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b465-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4b465-137">See Also</span></span>  
 <span data-ttu-id="4b465-138">[图表（报表生成器和 SSRS）](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4b465-138">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="4b465-139">[图表类型（报表生成器和 SSRS）](chart-types-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4b465-139">[Chart Types &#40;Report Builder and SSRS&#41;](chart-types-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="4b465-140">[图表中的空点和 Null 数据点（报表生成器和 SSRS）](empty-and-null-data-points-in-charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4b465-140">[Empty and Null Data Points in Charts &#40;Report Builder and SSRS&#41;](empty-and-null-data-points-in-charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="4b465-141">[教程：向报表添加条形图（报表生成器）](https://go.microsoft.com/fwlink/?LinkId=198052) </span><span class="sxs-lookup"><span data-stu-id="4b465-141">[Tutorial: Adding a Bar Chart to Your Report (Report Builder)](https://go.microsoft.com/fwlink/?LinkId=198052) </span></span>  
 <span data-ttu-id="4b465-142">[教程：向报表添加条形图（报表设计器）](https://go.microsoft.com/fwlink/?LinkId=198042) </span><span class="sxs-lookup"><span data-stu-id="4b465-142">[Tutorial: Adding a Bar Chart to a Report (Report Designer)](https://go.microsoft.com/fwlink/?LinkId=198042) </span></span>  
 <span data-ttu-id="4b465-143">[教程：向报表添加饼图（报表生成器）](https://go.microsoft.com/fwlink/?LinkId=198051) </span><span class="sxs-lookup"><span data-stu-id="4b465-143">[Tutorial: Adding a Pie Chart to Your Report (Report Builder)](https://go.microsoft.com/fwlink/?LinkId=198051) </span></span>  
 [<span data-ttu-id="4b465-144">教程：向报表添加饼图（报表设计器）</span><span class="sxs-lookup"><span data-stu-id="4b465-144">Tutorial: Adding a Pie Chart to a Report (Report Designer)</span></span>](https://go.microsoft.com/fwlink/?LinkId=198041)  
  
  
