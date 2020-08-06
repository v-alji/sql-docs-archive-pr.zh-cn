---
title: 在矩阵和图表上显示相同数据（报表生成器）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 1262f283-9fc2-4bc1-9c79-457f7642abc7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7746ce1f06d4dcc67c51ddc40714f19a3ff83d51
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691616"
---
# <a name="display-the-same-data-on-a-matrix-and-a-chart-report-builder"></a><span data-ttu-id="5b65b-102">在矩阵和图表上显示相同数据（报表生成器）</span><span class="sxs-lookup"><span data-stu-id="5b65b-102">Display the Same Data on a Matrix and a Chart (Report Builder)</span></span>
  <span data-ttu-id="5b65b-103">如果希望在矩阵和图表中显示相同数据，则必须将两个数据区域的属性都设置为指定相同数据集，而且还要为筛选器、组、排序和数据指定相同表达式。</span><span class="sxs-lookup"><span data-stu-id="5b65b-103">When you want to show the same data in a matrix and a chart, you must set properties on both data regions to specify the same dataset, and also the same expressions for filters, groups, sorts, and data.</span></span>  
  
 <span data-ttu-id="5b65b-104">由于两个数据区域的数据将有相同的祖先（报表数据集），因此在向矩阵添加交互式排序按钮之后，当用户单击该按钮时它会同时更改矩阵和图表的排序顺序。</span><span class="sxs-lookup"><span data-stu-id="5b65b-104">Because both data regions will have the same ancestor for data (the report dataset), you can add an interactive sort button to the matrix that, when the user clicks it, changes the sort order for both the matrix and the chart.</span></span> <span data-ttu-id="5b65b-105">有关详细信息，请参阅 [将交互式排序添加到表或矩阵（报表生成器和 SSRS）](add-interactive-sort-to-a-table-or-matrix-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="5b65b-105">For more information, see [Add Interactive Sort to a Table or Matrix &#40;Report Builder and SSRS&#41;](add-interactive-sort-to-a-table-or-matrix-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="5b65b-106">若要使用矩阵列组值作为图表的图例，必须指定图表上序列数据的颜色，然后使用与填充颜色相同的颜色作为用于显示组值的矩阵单元中文本框的背景色。</span><span class="sxs-lookup"><span data-stu-id="5b65b-106">To use the matrix column group values as a legend for the chart, you must specify the colors for the series data on the chart, and then use the same colors as the fill colors for the background of the text boxes in the matrix cell that displays the group values.</span></span> <span data-ttu-id="5b65b-107">有关详细信息，请参阅[对多个形状图指定一致的颜色（报表生成器和 SSRS）](charts-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="5b65b-107">For more information, see [Specify Consistent Colors across Multiple Shape Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="5b65b-108">在运行时，如果组定义中有太多组值，则报表可能显得很混乱。</span><span class="sxs-lookup"><span data-stu-id="5b65b-108">At run-time, your report may appear cluttered if there are too many group values for your group definitions.</span></span> <span data-ttu-id="5b65b-109">您可能需要筛选值、组合组或调整阈值，以便图表为您组合组。</span><span class="sxs-lookup"><span data-stu-id="5b65b-109">You might need to filter values, combine groups, or adjust the threshold for the chart to combine groups for you.</span></span> <span data-ttu-id="5b65b-110">有关详细信息，请参阅 [将多个数据区域链接到同一数据集（报表生成器和 SSRS）](linking-multiple-data-regions-to-the-same-dataset-report-builder-and-ssrs.md)</span><span class="sxs-lookup"><span data-stu-id="5b65b-110">For more information, see [Linking Multiple Data Regions to the Same Dataset &#40;Report Builder and SSRS&#41;](linking-multiple-data-regions-to-the-same-dataset-report-builder-and-ssrs.md)</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-matrix-and-chart-to-display-the-same-data"></a><span data-ttu-id="5b65b-111">添加矩阵和图表以显示相同数据</span><span class="sxs-lookup"><span data-stu-id="5b65b-111">To add a matrix and chart to display the same data</span></span>  
  
1.  <span data-ttu-id="5b65b-112">在设计视图中打开报表。</span><span class="sxs-lookup"><span data-stu-id="5b65b-112">Open a report in design view.</span></span>  
  
2.  <span data-ttu-id="5b65b-113">在 **“插入”** 选项卡的 **“数据区域”** 组中，单击 **“矩阵”** ，然后单击报表正文或报表正文中的矩形。</span><span class="sxs-lookup"><span data-stu-id="5b65b-113">From the **Insert** tab, in the **Data Regions** group, click **Matrix**, and then click the report body or in a rectangle in the report body.</span></span> <span data-ttu-id="5b65b-114">将在报表中添加一个矩阵。</span><span class="sxs-lookup"><span data-stu-id="5b65b-114">A matrix is added to the report.</span></span>  
  
3.  <span data-ttu-id="5b65b-115">在 **“插入”** 选项卡的 **“数据区域”** 组中，单击 **“图”** ，然后选择图表类型。</span><span class="sxs-lookup"><span data-stu-id="5b65b-115">From the **Insert** tab, in the **Data Regions** group, click **Chart**, and then select the chart type.</span></span> <span data-ttu-id="5b65b-116">将在报表中添加一个图表。</span><span class="sxs-lookup"><span data-stu-id="5b65b-116">A chart is added to the report.</span></span>  
  
4.  <span data-ttu-id="5b65b-117">（可选）在“插入”  选项卡的“报表项”  组中，单击“矩形”  ，然后单击报表。</span><span class="sxs-lookup"><span data-stu-id="5b65b-117">(Optional) From the **Insert** tab, in the **Report Items** group, click **Rectangle**, and then click the report.</span></span> <span data-ttu-id="5b65b-118">将在报表中添加一个矩形。</span><span class="sxs-lookup"><span data-stu-id="5b65b-118">A rectangle is added to the report.</span></span> <span data-ttu-id="5b65b-119">将步骤 2 和 3 中的矩阵和图表拖到该矩形中。</span><span class="sxs-lookup"><span data-stu-id="5b65b-119">Drag the matrix and chart from steps 2 and 3 into the rectangle.</span></span>  
  
     <span data-ttu-id="5b65b-120">通过在矩形容器中放入多个数据区域，可以帮助控制当您查看报表时如何呈现矩阵和图表。</span><span class="sxs-lookup"><span data-stu-id="5b65b-120">By placing multiple data regions in the rectangle container, you help control how the matrix and chart render when you view the report.</span></span>  
  
     <span data-ttu-id="5b65b-121">在后面几个步骤中，将选择要在矩阵中显示和在图表中显示的相同数据集字段。</span><span class="sxs-lookup"><span data-stu-id="5b65b-121">In the next few steps, you will choose the same dataset field to display in the matrix and to display in the chart.</span></span>  
  
5.  <span data-ttu-id="5b65b-122">从“报表数据”窗格中，将数值数据集字段拖到矩阵中的数据单元。</span><span class="sxs-lookup"><span data-stu-id="5b65b-122">From the Report Data pane, drag a numeric dataset field to the Data cell in the matrix.</span></span>  
  
     <span data-ttu-id="5b65b-123">默认情况下，将使用聚合函数 Sum 计算组值。</span><span class="sxs-lookup"><span data-stu-id="5b65b-123">By default, the aggregate function Sum is used for calculating the group value.</span></span> <span data-ttu-id="5b65b-124">如果更改矩阵中的聚合函数，还必须在图表中进行更改。</span><span class="sxs-lookup"><span data-stu-id="5b65b-124">If you change the aggregate function in the matrix, you must change in the chart also.</span></span>  
  
6.  <span data-ttu-id="5b65b-125">在矩阵中，右键单击包含数据的单元，单击“文本框属性”  ，再单击“数字”  。</span><span class="sxs-lookup"><span data-stu-id="5b65b-125">In the matrix, right-click the cell with data, click **Text Box Properties**, and then click **Number**.</span></span> <span data-ttu-id="5b65b-126">为数据集字段值选择适当的格式。</span><span class="sxs-lookup"><span data-stu-id="5b65b-126">Choose an appropriate format for the dataset field value.</span></span>  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
8.  <span data-ttu-id="5b65b-127">将在步骤 3 中选择的相同数据集字段拖到图表上的 **“值”** 区域中。</span><span class="sxs-lookup"><span data-stu-id="5b65b-127">Drag the same dataset field you chose in step 3 to the **Values** area on the chart.</span></span>  
  
9. <span data-ttu-id="5b65b-128">在图表中，右键单击 Y 轴，单击“轴属性”  ，再单击“数字”  。</span><span class="sxs-lookup"><span data-stu-id="5b65b-128">In the chart, right-click the Y axis, click **Axis Properties**, and then click **Number**.</span></span> <span data-ttu-id="5b65b-129">为在步骤 4 中选择的数据选择相同格式。</span><span class="sxs-lookup"><span data-stu-id="5b65b-129">Choose the same format for the data that you chose in step 4.</span></span>  
  
10. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="5b65b-130">在后面几个步骤中，需要将矩阵行组和图表序列组设置为相同表达式，而且还要设置图表序列组的排序顺序。</span><span class="sxs-lookup"><span data-stu-id="5b65b-130">In the next few steps, you will set the matrix row group and the chart series group to the same expression, and also set the sort order for the chart series group.</span></span>  
  
11. <span data-ttu-id="5b65b-131">从“报表数据”窗格中，将要按其为矩阵行分组的数据集字段拖到“行组”窗格。</span><span class="sxs-lookup"><span data-stu-id="5b65b-131">From the Report Data pane, drag the dataset field that you want to group by for matrix rows to the Row Groups pane.</span></span>  
  
     <span data-ttu-id="5b65b-132">默认情况下，矩阵行组会添加与组表达式相同的排序表达式。</span><span class="sxs-lookup"><span data-stu-id="5b65b-132">By default, the matrix row group adds a sort expression that is the same as the group expression.</span></span>  
  
12. <span data-ttu-id="5b65b-133">将在步骤 9 中使用的相同数据集字段拖到图表的 **“序列组”** 区域。</span><span class="sxs-lookup"><span data-stu-id="5b65b-133">Drag the same dataset field that you used in step 9 to the **Series Groups** area for the chart.</span></span>  
  
13. <span data-ttu-id="5b65b-134">在“序列组”  区域中右键单击该组，然后单击“序列组属性”  。</span><span class="sxs-lookup"><span data-stu-id="5b65b-134">Right-click the group in the **Series Groups** area, and then click **Series Group Properties**.</span></span>  
  
14. <span data-ttu-id="5b65b-135">单击 **“排序”** 。</span><span class="sxs-lookup"><span data-stu-id="5b65b-135">Click **Sorting**.</span></span>  
  
15. <span data-ttu-id="5b65b-136">单击“添加”  。</span><span class="sxs-lookup"><span data-stu-id="5b65b-136">Click **Add**.</span></span> <span data-ttu-id="5b65b-137">将在排序表达式网格中出现一个新行。</span><span class="sxs-lookup"><span data-stu-id="5b65b-137">A new row appears in the sort expressions grid.</span></span>  
  
16. <span data-ttu-id="5b65b-138">在“排序依据”  中，从下拉列表选择在步骤 9 中选择要按其分组的数据集字段。</span><span class="sxs-lookup"><span data-stu-id="5b65b-138">In **Sort by**, from the drop-down list, choose the dataset field that you chose to group by in step 9.</span></span>  
  
17. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="5b65b-139">在后面几个步骤中，需要将矩阵列组和图表类别组设置为相同表达式，而且还要设置图表类别组的排序顺序。</span><span class="sxs-lookup"><span data-stu-id="5b65b-139">In the next few steps, you will set the matrix column group and the chart category group to the same expression, and also set the sort order for the chart category group.</span></span>  
  
18. <span data-ttu-id="5b65b-140">从“报表数据”窗格中，将要按其为矩阵列分组的数据集字段拖到“列组”窗格。</span><span class="sxs-lookup"><span data-stu-id="5b65b-140">From the Report Data pane, drag the dataset field that you want to group by for matrix columns to the Column Groups pane.</span></span>  
  
     <span data-ttu-id="5b65b-141">默认情况下，矩阵列组会添加与组表达式相同的排序表达式。</span><span class="sxs-lookup"><span data-stu-id="5b65b-141">By default, the matrix column group adds a sort expression that is the same as the group expression.</span></span>  
  
19. <span data-ttu-id="5b65b-142">将在步骤 16 中使用的相同数据集字段拖到图表的 **“类别组”** 区域。</span><span class="sxs-lookup"><span data-stu-id="5b65b-142">Drag the same dataset field that you used in step 16 to the **Category Groups** area for the chart.</span></span>  
  
20. <span data-ttu-id="5b65b-143">在“类别组”  区域中右键单击该组，然后单击“类别组属性”  。</span><span class="sxs-lookup"><span data-stu-id="5b65b-143">Right-click the group in the **CategoryGroups** area, and then click **Category Group Properties**.</span></span>  
  
21. <span data-ttu-id="5b65b-144">单击 **“排序”** 。</span><span class="sxs-lookup"><span data-stu-id="5b65b-144">Click **Sorting**.</span></span>  
  
22. <span data-ttu-id="5b65b-145">单击“添加”  。</span><span class="sxs-lookup"><span data-stu-id="5b65b-145">Click **Add**.</span></span> <span data-ttu-id="5b65b-146">将在排序表达式网格中出现一个新行。</span><span class="sxs-lookup"><span data-stu-id="5b65b-146">A new row appears in the sort expressions grid.</span></span>  
  
23. <span data-ttu-id="5b65b-147">在“排序依据”  中，从下拉列表选择在步骤 16 中选择要按其分组的数据集字段。</span><span class="sxs-lookup"><span data-stu-id="5b65b-147">In **Sort by**, from the drop-down list, choose the dataset field that you chose to group by in step 16.</span></span>  
  
24. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
25. <span data-ttu-id="5b65b-148">预览结果。</span><span class="sxs-lookup"><span data-stu-id="5b65b-148">Preview the result.</span></span> <span data-ttu-id="5b65b-149">矩阵行组和列组将显示与图表序列组和类别组相同的数据。</span><span class="sxs-lookup"><span data-stu-id="5b65b-149">The matrix row and column groups display the same data as the chart series and category groups.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b65b-150">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5b65b-150">See Also</span></span>  
 <span data-ttu-id="5b65b-151">[将多个数据区域链接到同一数据集（报表生成器和 SSRS）](linking-multiple-data-regions-to-the-same-dataset-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="5b65b-151">[Linking Multiple Data Regions to the Same Dataset &#40;Report Builder and SSRS&#41;](linking-multiple-data-regions-to-the-same-dataset-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="5b65b-152">[添加数据集筛选器、数据区域筛选器和组筛选器（报表生成器和 SSRS）](add-dataset-filters-data-region-filters-and-group-filters.md) </span><span class="sxs-lookup"><span data-stu-id="5b65b-152">[Add Dataset Filters, Data Region Filters, and Group Filters &#40;Report Builder and SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md) </span></span>  
 <span data-ttu-id="5b65b-153">[列出 &#40;报表生成器和 SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="5b65b-153">[Lists &#40;Report Builder and SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="5b65b-154">图表&#40;报表生成器和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="5b65b-154">Charts &#40;Report Builder and SSRS&#41;</span></span>](charts-report-builder-and-ssrs.md)  
  
  
