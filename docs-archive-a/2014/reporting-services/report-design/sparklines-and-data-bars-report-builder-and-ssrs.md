---
title: 迷你图和数据条（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.sparklines.f1
- "10544"
ms.assetid: b287436b-fa48-4970-a1a7-1dbcb86e7411
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: eb6f050b1985cf165533e3677242bffb0d7b680f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578625"
---
# <a name="sparklines-and-data-bars-report-builder-and-ssrs"></a><span data-ttu-id="db64a-102">迷你图和数据条（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="db64a-102">Sparklines and Data Bars (Report Builder and SSRS)</span></span>
  <span data-ttu-id="db64a-103">迷你图和数据条是较小的简单图表，它们可以在很小的空间中传递很多信息，并且常常与文本并排。</span><span class="sxs-lookup"><span data-stu-id="db64a-103">Sparklines and data bars are small, simple charts that convey a lot of information in a little space, often inline with text.</span></span> <span data-ttu-id="db64a-104">迷你图和数据条通常用于表和矩阵中。</span><span class="sxs-lookup"><span data-stu-id="db64a-104">Sparklines and data bars are often used in tables and matrices.</span></span> <span data-ttu-id="db64a-105">其影响来自于将它们一起进行查看并且能够快速对它们进行相互比较，而不是单独查看它们。</span><span class="sxs-lookup"><span data-stu-id="db64a-105">Their impact comes from viewing many of them together and being able to quickly compare them one above the other, rather than viewing them singly.</span></span> <span data-ttu-id="db64a-106">这样可以便于看到离群值，即不像其他项那样执行的行。</span><span class="sxs-lookup"><span data-stu-id="db64a-106">They make it easy to see the outliers, the rows that are not performing like the others.</span></span> <span data-ttu-id="db64a-107">尽管较小，但每个迷你图通常表示一段时间中的多个数据点。</span><span class="sxs-lookup"><span data-stu-id="db64a-107">Although they are small, each sparkline often represents multiple data points, often over time.</span></span> <span data-ttu-id="db64a-108">数据条可表示多个数据点，但通常只说明一个。</span><span class="sxs-lookup"><span data-stu-id="db64a-108">Data bars can represent multiple data points, but typically illustrate only one.</span></span> <span data-ttu-id="db64a-109">每个迷你图通常展示单个序列。</span><span class="sxs-lookup"><span data-stu-id="db64a-109">Each sparkline typically presents a single series.</span></span> <span data-ttu-id="db64a-110">不能将迷你图添加到表的详细信息组中。</span><span class="sxs-lookup"><span data-stu-id="db64a-110">You cannot add a sparkline to a detail group in a table.</span></span> <span data-ttu-id="db64a-111">因为迷你图显示聚合数据，所以它们必须处于与某一组相关联的单元中。</span><span class="sxs-lookup"><span data-stu-id="db64a-111">Because sparklines display aggregated data, they must go in a cell associated with a group.</span></span> <span data-ttu-id="db64a-112">迷你图和数据条具有相同的基本图表元素类别、序列和值，但没有图例、轴线、标签或刻度线。</span><span class="sxs-lookup"><span data-stu-id="db64a-112">Sparklines and data bars have the same basic chart elements of categories, series, and values, but they have no legend, axis lines, labels, or tick marks.</span></span>  
  
 <span data-ttu-id="db64a-113">![rs_SparklineExample](../media/rs-sparklineexample.gif "rs_SparklineExample")</span><span class="sxs-lookup"><span data-stu-id="db64a-113">![rs_SparklineExample](../media/rs-sparklineexample.gif "rs_SparklineExample")</span></span>  
  
 <span data-ttu-id="db64a-114">若要快速开始使用迷你图，请参阅 [教程：向报表添加迷你图（报表生成器）](../tutorial-add-a-sparkline-to-your-report-report-builder.md) 和视频 [如何：在表中创建迷你图](https://go.microsoft.com/fwlink/?LinkId=197092) 以及 [报表生成器中的迷你图、条形图和指示器](https://technet.microsoft.com/bi/video/ff877165) 。</span><span class="sxs-lookup"><span data-stu-id="db64a-114">To quickly get started with sparklines, see [Tutorial: Add a Sparkline to Your Report &#40;Report Builder&#41;](../tutorial-add-a-sparkline-to-your-report-report-builder.md) and the videos [How to: Create a Sparkline in a Table](https://go.microsoft.com/fwlink/?LinkId=197092) and [Sparklines, Bar Charts, and Indicators in Report Builder](https://technet.microsoft.com/bi/video/ff877165) .</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="db64a-115">您可以将迷你图和数据条连同它们的父表、矩阵或列表作为报表部件与报表分开发布。</span><span class="sxs-lookup"><span data-stu-id="db64a-115">You can publish sparklines and data bars with their parent table, matrix, or list, separately from a report as a report part.</span></span> [!INCLUDE[ssRBrptparts](../../includes/ssrbrptparts-md.md)]  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="types-of-sparklines"></a><a name="KindsofSparklines"></a> <span data-ttu-id="db64a-116">迷你图的类型</span><span class="sxs-lookup"><span data-stu-id="db64a-116">Types of Sparklines</span></span>  
 <span data-ttu-id="db64a-117">您几乎可以像常规图表一样创建任意类型的迷你图。</span><span class="sxs-lookup"><span data-stu-id="db64a-117">You can create almost as many types of sparklines as there are regular charts.</span></span> <span data-ttu-id="db64a-118">一般情况下，不能生成三维迷你图。</span><span class="sxs-lookup"><span data-stu-id="db64a-118">In general, you cannot make 3D sparklines.</span></span> <span data-ttu-id="db64a-119">您可以生成以下完整图表的迷你图版本：</span><span class="sxs-lookup"><span data-stu-id="db64a-119">You can make sparkline versions of these full charts:</span></span>  
  
-   <span data-ttu-id="db64a-120">[柱形图（报表生成器和 SSRS）](charts-report-builder-and-ssrs.md)：基本柱形图、堆叠柱形图和百分比堆叠柱形图。</span><span class="sxs-lookup"><span data-stu-id="db64a-120">[Column Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md): The basic, stacked, and 100% stacked column charts.</span></span>  
  
-   <span data-ttu-id="db64a-121">[折线图（报表生成器和 SSRS）](line-charts-report-builder-and-ssrs.md)：除三维折线图之外的所有图。</span><span class="sxs-lookup"><span data-stu-id="db64a-121">[Line Charts &#40;Report Builder and SSRS&#41;](line-charts-report-builder-and-ssrs.md): All except the 3D line chart.</span></span>  
  
-   <span data-ttu-id="db64a-122">[分区图（报表生成器和 SSRS）](area-charts-report-builder-and-ssrs.md)：除三维分区图之外的所有图</span><span class="sxs-lookup"><span data-stu-id="db64a-122">[Area Charts &#40;Report Builder and SSRS&#41;](area-charts-report-builder-and-ssrs.md): All except the 3D area charts</span></span>  
  
-   <span data-ttu-id="db64a-123">[饼图（报表生成器和 SSRS）](pie-charts-report-builder-and-ssrs.md)：圆环图（平面和三维均可），但不包括漏斗图和棱锥图之类的其他形状。</span><span class="sxs-lookup"><span data-stu-id="db64a-123">[Pie Charts &#40;Report Builder and SSRS&#41;](pie-charts-report-builder-and-ssrs.md): And doughnut charts, both flat and 3D, but not the other shapes such as funnel and pyramid charts.</span></span>  
  
-   <span data-ttu-id="db64a-124">[范围图（报表生成器和 SSRS）](range-charts-report-builder-and-ssrs.md)：股价图、K 线图、误差线和盒须图。</span><span class="sxs-lookup"><span data-stu-id="db64a-124">[Range Charts &#40;Report Builder and SSRS&#41;](range-charts-report-builder-and-ssrs.md): The stock, candlestick, error bar, and box plot charts.</span></span>  
  
##  <a name="data-bars"></a><a name="DataBars"></a><span data-ttu-id="db64a-125">数据条</span><span class="sxs-lookup"><span data-stu-id="db64a-125">Data Bars</span></span>  
 <span data-ttu-id="db64a-126">数据条通常表示单个数据点，尽管它们也可以像常规条形图一样表示多个数据点。</span><span class="sxs-lookup"><span data-stu-id="db64a-126">Data bars typically represent a single data point, though they can represent multiple data points, just like regular bar charts.</span></span> <span data-ttu-id="db64a-127">它们通常包含无类别的若干序列，或者具有序列分组。</span><span class="sxs-lookup"><span data-stu-id="db64a-127">They often contain several series with no category, or have series grouping.</span></span>  
  
 <span data-ttu-id="db64a-128">![rs_DataBars](../media/rs-databars.gif "rs_DataBars")</span><span class="sxs-lookup"><span data-stu-id="db64a-128">![rs_DataBars](../media/rs-databars.gif "rs_DataBars")</span></span>  
  
 <span data-ttu-id="db64a-129">在此示例中使用堆积数据条，每个数据条（尽管只有一个）说明多个数据点。</span><span class="sxs-lookup"><span data-stu-id="db64a-129">In this example using stacked data bars, each data bar, although only one bar, illustrates more than one data point.</span></span> <span data-ttu-id="db64a-130">例如，数据条的三种不同颜色可以表示三个优先级的任务，并且数据条的长度表示分配给每个人的任务的总数。</span><span class="sxs-lookup"><span data-stu-id="db64a-130">For example, the three different colors of the bar could represent tasks of three levels of priority with the length of the bar representing the total number of tasks assigned to each person.</span></span> <span data-ttu-id="db64a-131">如果您改为生成这些百分比堆积数据条，则每个条都将填充单元，并且不同颜色将表示对于每个优先级占整体的百分比。</span><span class="sxs-lookup"><span data-stu-id="db64a-131">If you made these 100% stacked data bars instead, each bar would fill the cell, and the different colors would represent the percentage of the whole for each priority level.</span></span>  
  
 <span data-ttu-id="db64a-132">您可以生成以下完整图表的数据条版本：</span><span class="sxs-lookup"><span data-stu-id="db64a-132">You can make data bar versions of these full charts:</span></span>  
  
-   <span data-ttu-id="db64a-133">[条形图（报表生成器和 SSRS）](bar-charts-report-builder-and-ssrs.md)：基本条形图、堆叠条形图和百分比堆叠条形图。</span><span class="sxs-lookup"><span data-stu-id="db64a-133">[Bar Charts &#40;Report Builder and SSRS&#41;](bar-charts-report-builder-and-ssrs.md): Basic, stacked, and 100% stacked bar charts.</span></span>  
  
-   <span data-ttu-id="db64a-134">[柱形图（报表生成器和 SSRS）](charts-report-builder-and-ssrs.md)：基本柱形图、堆叠柱形图和百分比堆叠柱形图。</span><span class="sxs-lookup"><span data-stu-id="db64a-134">[Column Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md): Basic, stacked, and 100% stacked column charts.</span></span> <span data-ttu-id="db64a-135">柱形图可以是迷你图或数据条。</span><span class="sxs-lookup"><span data-stu-id="db64a-135">Column charts can be either sparklines or data bars.</span></span>  

##  <a name="aligning-sparkline-data-in-a-table-or-matrix"></a><a name="AlignDatainTableMatrix"></a> <span data-ttu-id="db64a-136">在表或矩阵中对齐迷你图数据</span><span class="sxs-lookup"><span data-stu-id="db64a-136">Aligning Sparkline Data in a Table or Matrix</span></span>  
 <span data-ttu-id="db64a-137">在您将一个迷你图插入到表或矩阵中时，将每个迷你图中的数据点与该列中其他迷你图的数据点对齐通常十分重要。</span><span class="sxs-lookup"><span data-stu-id="db64a-137">When you insert a sparkline in a table or matrix, it is usually important for the data points in each sparkline to align with the data points of the other sparklines in that column.</span></span> <span data-ttu-id="db64a-138">否则，很难比较不同行中的数据。</span><span class="sxs-lookup"><span data-stu-id="db64a-138">Otherwise it is hard to compare the data in the different rows.</span></span> <span data-ttu-id="db64a-139">例如，为您的公司中的不同销售人员按月比较销售数据时，您需要对齐月份。</span><span class="sxs-lookup"><span data-stu-id="db64a-139">For example, when you compare sales data by month for different salespeople in your company, you would want the months to align.</span></span> <span data-ttu-id="db64a-140">如果某个员工在四月外出，则该员工在该月可能会没有销售数据。</span><span class="sxs-lookup"><span data-stu-id="db64a-140">If an employee was out for the month of April, there would be no data for that employee for that month.</span></span> <span data-ttu-id="db64a-141">您想要看到该月的差距，并且看到后续月份的数据与其他员工的数据对齐。</span><span class="sxs-lookup"><span data-stu-id="db64a-141">You would want to see a gap for that month, and see the data for subsequent months align with the data for the other employees.</span></span> <span data-ttu-id="db64a-142">为此，您可以对齐水平轴。</span><span class="sxs-lookup"><span data-stu-id="db64a-142">You can do this by aligning the horizontal axis.</span></span> <span data-ttu-id="db64a-143">有关详细信息，请参阅[总计、聚合和内置集合的表达式作用域（报表生成器和 SSRS）](expression-scope-for-totals-aggregates-and-built-in-collections.md)中关于迷你图的部分，另请参阅[在表或矩阵中的图表中对齐数据（报表生成器和 SSRS）](align-the-data-in-a-chart-in-a-table-or-matrix-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="db64a-143">For more information, see the section about sparklines in [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md), and see [Align the Data in a Chart in a Table or Matrix &#40;Report Builder and SSRS&#41;](align-the-data-in-a-chart-in-a-table-or-matrix-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="db64a-144">同样，为了可以跨多行进行比较，数据还必须垂直对齐，这意味着一个迷你图或数据条中条和线条的高度必须相对于所有其他迷你图或数据条中条和线条的高度。</span><span class="sxs-lookup"><span data-stu-id="db64a-144">Likewise, to be comparable across rows, data must also align vertically, meaning that the height of the bars or lines in one sparkline or data bar must be relative to the height of the bars and lines in all the other sparklines or data bars.</span></span> <span data-ttu-id="db64a-145">否则，将不能彼此比较这些行。</span><span class="sxs-lookup"><span data-stu-id="db64a-145">Otherwise, you can't compare the rows to each other.</span></span>  
  
 <span data-ttu-id="db64a-146">![rs_SparklineAlignData](../media/rs-sparklinealigndata.gif "rs_SparklineAlignData")</span><span class="sxs-lookup"><span data-stu-id="db64a-146">![rs_SparklineAlignData](../media/rs-sparklinealigndata.gif "rs_SparklineAlignData")</span></span>  
  
 <span data-ttu-id="db64a-147">在此图像中，柱形图显示每个雇员每天的销售额。</span><span class="sxs-lookup"><span data-stu-id="db64a-147">In this image, the column chart shows daily sales for each employee.</span></span> <span data-ttu-id="db64a-148">请注意，对于雇员没有销售额数据的那些天，该图留空并对齐后面的天。</span><span class="sxs-lookup"><span data-stu-id="db64a-148">Note that for days that an employee has no sales, the chart leaves a blank and aligns subsequent days.</span></span> <span data-ttu-id="db64a-149">这是一个水平对齐的示例。</span><span class="sxs-lookup"><span data-stu-id="db64a-149">This is an example of horizontal alignment.</span></span> <span data-ttu-id="db64a-150">还要注意的是，对于某些员工，每个条都比较短，并且没有条达到单元的顶部。</span><span class="sxs-lookup"><span data-stu-id="db64a-150">Also note that for some employees, every bar is short, and no bar reaches the top of the cell.</span></span> <span data-ttu-id="db64a-151">这是一个垂直对齐的示例；如果没有垂直对齐，则在没有较高的条的行中，短条将扩展以便填充单元的高度。</span><span class="sxs-lookup"><span data-stu-id="db64a-151">This is an example of vertical alignment; without it, in the rows with no tall bars, the short bars would expand to fill the height of the cell.</span></span>  

##  <a name="understanding-the-data-supplied-to-a-sparkline-or-data-bar"></a><a name="UnderstandScope"></a> <span data-ttu-id="db64a-152">理解提供给迷你图或数据条的数据</span><span class="sxs-lookup"><span data-stu-id="db64a-152">Understanding the Data Supplied to a Sparkline or Data Bar</span></span>  
 <span data-ttu-id="db64a-153">\*\* 在您向表或矩阵添加迷你图或数据条时，这称作在一个数据区域内“嵌套”另一个数据区域。</span><span class="sxs-lookup"><span data-stu-id="db64a-153">When you add a sparkline or data bar to a table or matrix, this is referred to as *nesting* one data region inside another.</span></span> <span data-ttu-id="db64a-154">嵌套意味着提供给迷你图或数据条的数据由表或矩阵所基于的数据集控制，或者由将其放置于表或矩阵中的位置控制。</span><span class="sxs-lookup"><span data-stu-id="db64a-154">Nesting means that the data supplied to the sparkline or data bar is controlled by the dataset that the table or matrix is based on, and by where you put it in the table or matrix.</span></span> <span data-ttu-id="db64a-155">有关详细信息，请参阅 [嵌套数据区域（报表生成器和 SSRS）](nested-data-regions-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="db64a-155">For more information, see [Nested Data Regions &#40;Report Builder and SSRS&#41;](nested-data-regions-report-builder-and-ssrs.md).</span></span>  
  
##  <a name="converting-a-sparkline-or-data-bar-to-a-full-chart"></a><a name="ConvertSparklinetoChart"></a><span data-ttu-id="db64a-156">将迷你图或数据条转换为完整图表</span><span class="sxs-lookup"><span data-stu-id="db64a-156">Converting a Sparkline or Data Bar to a Full Chart</span></span>  
 <span data-ttu-id="db64a-157">因为迷你图和数据条只是一种图表，所以，在你决定想要具备整个图表功能时，可以通过右键单击图表并单击“转换为整个图表”\*\*\*\*，将迷你图或数据条转换为整个图表。</span><span class="sxs-lookup"><span data-stu-id="db64a-157">Because sparklines and data bars are just a kind of chart, if you decide you would rather have the full chart functionality, you can convert one to a full chart by right-clicking the chart and clicking **Convert to Full Chart**.</span></span> <span data-ttu-id="db64a-158">执行此操作时，将自动添加轴线、标签、刻度线和图例。</span><span class="sxs-lookup"><span data-stu-id="db64a-158">When you do, the axis lines, labels, tick marks, and legend are added automatically.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="db64a-159">通过一次单击不能将整个图表转换为迷你图或数据栏。</span><span class="sxs-lookup"><span data-stu-id="db64a-159">You cannot convert a full chart to a sparkline or data bar with one click.</span></span> <span data-ttu-id="db64a-160">但是，只需通过删除不在迷你图和数据条中的所有图表元素，即可从完整图表生成迷你图或数据条。</span><span class="sxs-lookup"><span data-stu-id="db64a-160">However, you can make a sparkline or data bar from a full chart just by deleting all the chart elements that are not in sparklines and data bars.</span></span>  

##  <a name="how-to-topics"></a><a name="HowTo"></a><span data-ttu-id="db64a-161">操作指南主题</span><span class="sxs-lookup"><span data-stu-id="db64a-161">How-to Topics</span></span>  
 [<span data-ttu-id="db64a-162">添加迷你图和数据条（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="db64a-162">Add Sparklines and Data Bars &#40;Report Builder and SSRS&#41;</span></span>](sparklines-and-data-bars-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="db64a-163">在表或矩阵中的图表中对齐数据（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="db64a-163">Align the Data in a Chart in a Table or Matrix &#40;Report Builder and SSRS&#41;</span></span>](align-the-data-in-a-chart-in-a-table-or-matrix-report-builder-and-ssrs.md)  
  
### <a name="other-how-to-topics-for-charts"></a><span data-ttu-id="db64a-164">针对图表的其他操作指南主题</span><span class="sxs-lookup"><span data-stu-id="db64a-164">Other how-to topics for charts</span></span>  
 <span data-ttu-id="db64a-165">因为迷你图和数据条为图表类型，所以，您可能还会发现以下针对图表的操作指南主题既对您很有帮助，又颇具针对性：</span><span class="sxs-lookup"><span data-stu-id="db64a-165">Because sparklines and data bars are a type of chart, you might also find the following how-to topics for charts helpful and relevant:</span></span>  
  
 [<span data-ttu-id="db64a-166">向报表添加图表（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="db64a-166">Add a Chart to a Report &#40;Report Builder and SSRS&#41;</span></span>](add-a-chart-to-a-report-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="db64a-167">向图表添加空点 &#40;报表生成器和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="db64a-167">Add Empty Points to the Chart &#40;Report Builder and SSRS&#41;</span></span>](add-empty-points-to-a-chart-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="db64a-168">在图表中添加或删除边距（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="db64a-168">Add or Remove Margins from a Chart &#40;Report Builder and SSRS&#41;</span></span>](add-or-remove-margins-from-a-chart-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="db64a-169">更改图表类型（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="db64a-169">Change a Chart Type &#40;Report Builder and SSRS&#41;</span></span>](change-a-chart-type-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="db64a-170">使用调色板 &#40;报表生成器和 SSRS 来定义图表上的颜色&#41;</span><span class="sxs-lookup"><span data-stu-id="db64a-170">Define Colors on a Chart Using a Palette &#40;Report Builder and SSRS&#41;</span></span>](define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="db64a-171">在序列上显示工具提示（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="db64a-171">Show ToolTips on a Series &#40;Report Builder and SSRS&#41;</span></span>](show-tooltips-on-a-series-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="db64a-172">指定对数刻度（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="db64a-172">Specify a Logarithmic Scale &#40;Report Builder and SSRS&#41;</span></span>](specify-a-logarithmic-scale-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="db64a-173">指定轴间隔（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="db64a-173">Specify an Axis Interval &#40;Report Builder and SSRS&#41;</span></span>](specify-an-axis-interval-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="db64a-174">对多个形状图指定一致的颜色（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="db64a-174">Specify Consistent Colors across Multiple Shape Charts &#40;Report Builder and SSRS&#41;</span></span>](shape-charts-report-builder-and-ssrs.md)  
  
## <a name="see-also"></a><span data-ttu-id="db64a-175">另请参阅</span><span class="sxs-lookup"><span data-stu-id="db64a-175">See Also</span></span>  
 <span data-ttu-id="db64a-176">[图表 &#40;报表生成器和 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="db64a-176">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="db64a-177">[教程：向报表添加迷你图 &#40;报表生成器&#41;](../tutorial-add-a-sparkline-to-your-report-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="db64a-177">[Tutorial: Add a Sparkline to Your Report &#40;Report Builder&#41;](../tutorial-add-a-sparkline-to-your-report-report-builder.md) </span></span>  
 <span data-ttu-id="db64a-178">[报表生成器 (视频的迷你图、条形图和指示器) ](https://technet.microsoft.com/bi/video/ff877165) </span><span class="sxs-lookup"><span data-stu-id="db64a-178">[Sparklines, Bar Charts, and Indicators in Report Builder (video)](https://technet.microsoft.com/bi/video/ff877165) </span></span>  
 [<span data-ttu-id="db64a-179">如何：在表中创建迷你图（视频）</span><span class="sxs-lookup"><span data-stu-id="db64a-179">How to: Create a Sparkline in a Table (video)</span></span>](https://go.microsoft.com/fwlink/?LinkId=197092)  
