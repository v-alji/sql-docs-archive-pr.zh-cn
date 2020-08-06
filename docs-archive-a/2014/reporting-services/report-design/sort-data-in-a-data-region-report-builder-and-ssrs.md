---
title: 对数据区域中的数据排序（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 2fcb9be2-1daa-4c92-ad00-5f63cdf39f70
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bc1fb458066bb942a490b08c0faad876dd3d5438
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692687"
---
# <a name="sort-data-in-a-data-region-report-builder-and-ssrs"></a><span data-ttu-id="e59d8-102">对数据区域中的数据排序（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="e59d8-102">Sort Data in a Data Region (Report Builder and SSRS)</span></span>
  <span data-ttu-id="e59d8-103">若要更改报表首次运行时数据区域中数据的排序顺序，必须为数据区域或组设置排序表达式。</span><span class="sxs-lookup"><span data-stu-id="e59d8-103">To change the sort order of data in a data region when a report first runs, you must set the sort expression on the data region or group.</span></span> <span data-ttu-id="e59d8-104">默认情况下，组的排序表达式自动设置为与组表达式相同的值。</span><span class="sxs-lookup"><span data-stu-id="e59d8-104">By default, the sort expression for a group is automatically set to the same value as the group expression.</span></span>  
  
-   <span data-ttu-id="e59d8-105">在 Tablix 数据区域中，可以为数据区域或为每个组（包括详细信息组）设置排序表达式。</span><span class="sxs-lookup"><span data-stu-id="e59d8-105">In a tablix data region, set the sort expression for the data region or for each group, including the details group.</span></span> <span data-ttu-id="e59d8-106">如果在 Tablix 数据区域中只有一个详细信息组，则可以在查询中、在数据区域上或在详细信息组上定义排序表达式，它们全都有相同的效果。</span><span class="sxs-lookup"><span data-stu-id="e59d8-106">If you have only one details group in a tablix data region, you can define a sort expression in the query, on the data region, or on the details group and they all have the same effect.</span></span>  
  
-   <span data-ttu-id="e59d8-107">在图表数据区域中，可以为类别组和序列组设置排序表达式，以控制每个组的排序顺序。</span><span class="sxs-lookup"><span data-stu-id="e59d8-107">In a chart data region, set the sort expression for the Category and Series groups to control the sort order for each group.</span></span> <span data-ttu-id="e59d8-108">图表图例中的颜色顺序由类别组中数据点的排序表达式确定。</span><span class="sxs-lookup"><span data-stu-id="e59d8-108">The order for colors in a chart legend is determined by the sort expression for the data points in the Category group.</span></span>  
  
-   <span data-ttu-id="e59d8-109">在仪表数据区域中，您通常不需要对数据进行排序，因为仪表将显示相对于范围的单个值。</span><span class="sxs-lookup"><span data-stu-id="e59d8-109">In a gauge data region, you do not typically need to sort data because the gauge displays a single value relative to a range.</span></span> <span data-ttu-id="e59d8-110">如果确实需要对仪表中的数据进行排序，则必须首先定义组，然后设置组的排序表达式。</span><span class="sxs-lookup"><span data-stu-id="e59d8-110">If you do need sort data in a gauge, you must first define a group, and then set the sort expression for the group.</span></span>  
  
 <span data-ttu-id="e59d8-111">有关详细信息，请参阅 [对数据进行筛选、分组和排序（报表生成器和 SSRS）](filter-group-and-sort-data-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="e59d8-111">For more information, see [Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="e59d8-112">对于 Tablix 数据区域，还可以将交互式排序按钮添加到列标题的顶部，以便让用户能够更改组或详细信息行的排序顺序。</span><span class="sxs-lookup"><span data-stu-id="e59d8-112">For a tablix data region, you can also add an interactive sort button to the top of a column header to provide the user with the ability to change the sort order of groups or detail rows.</span></span> <span data-ttu-id="e59d8-113">有关详细信息，请参阅[交互式排序（报表生成器和 SSRS）](interactive-sort-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="e59d8-113">For more information, see [Interactive Sort &#40;Report Builder and SSRS&#41;](interactive-sort-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-sort-data-in-a-tablix-data-region"></a><span data-ttu-id="e59d8-114">对 Tablix 数据区域中的数据进行排序</span><span class="sxs-lookup"><span data-stu-id="e59d8-114">To sort data in a Tablix data region</span></span>  
  
1.  <span data-ttu-id="e59d8-115">在设计图面上，右键单击行控点，然后单击“Tablix 属性”  。</span><span class="sxs-lookup"><span data-stu-id="e59d8-115">On the design surface, right-click a row handle, and then click **Tablix Properties**.</span></span>  
  
2.  <span data-ttu-id="e59d8-116">单击 **“排序”** 。</span><span class="sxs-lookup"><span data-stu-id="e59d8-116">Click **Sorting**.</span></span>  
  
3.  <span data-ttu-id="e59d8-117">对于每个排序表达式，请按照下列步骤进行操作：</span><span class="sxs-lookup"><span data-stu-id="e59d8-117">For each sort expression, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="e59d8-118">单击“添加”  。</span><span class="sxs-lookup"><span data-stu-id="e59d8-118">Click **Add**.</span></span>  
  
    2.  <span data-ttu-id="e59d8-119">键入或选择按其对数据进行排序的表达式。</span><span class="sxs-lookup"><span data-stu-id="e59d8-119">Type or select an expression by which to sort the data.</span></span>  
  
    3.  <span data-ttu-id="e59d8-120">从“顺序”  列下拉列表中，选择每个表达式的排序方向。</span><span class="sxs-lookup"><span data-stu-id="e59d8-120">From the **Order** column drop-down list, choose the sort direction for each expression.</span></span> <span data-ttu-id="e59d8-121">**A-Z** 按升序对表达式进行排序。</span><span class="sxs-lookup"><span data-stu-id="e59d8-121">**A-Z** sorts the expression in ascending order.</span></span> <span data-ttu-id="e59d8-122">**Z-A** 按降序对表达式进行排序。</span><span class="sxs-lookup"><span data-stu-id="e59d8-122">**Z-A** sorts the expression in descending order.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-sort-values-in-a-group-including-the-details-group-for-a-tablix"></a><span data-ttu-id="e59d8-123">对 Tablix 的组（包括详细信息组）中的值进行排序</span><span class="sxs-lookup"><span data-stu-id="e59d8-123">To sort values in a group, including the details group, for a Tablix</span></span>  
  
1.  <span data-ttu-id="e59d8-124">在设计图面上，单击 Tablix 数据区域以将其选中。</span><span class="sxs-lookup"><span data-stu-id="e59d8-124">On the design surface, click in the tablix data region to select it.</span></span> <span data-ttu-id="e59d8-125">“分组”窗格将显示 Tablix 数据区域的行组和列组。</span><span class="sxs-lookup"><span data-stu-id="e59d8-125">The Grouping pane displays the row groups and column groups for the Tablix data region.</span></span>  
  
2.  <span data-ttu-id="e59d8-126">在“行组”窗格中，右键单击组名称，再单击“编辑组”  。</span><span class="sxs-lookup"><span data-stu-id="e59d8-126">In the Row Groups pane, right-click the group name, and then click **Edit Group**.</span></span>  
  
3.  <span data-ttu-id="e59d8-127">在 **“Tablix 组”** 对话框中，单击 **“排序”** 。</span><span class="sxs-lookup"><span data-stu-id="e59d8-127">In the **Tablix Group** dialog box, click **Sort**.</span></span>  
  
4.  <span data-ttu-id="e59d8-128">对于每个排序表达式，请按照下列步骤进行操作：</span><span class="sxs-lookup"><span data-stu-id="e59d8-128">For each sort expression, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="e59d8-129">单击“添加”  。</span><span class="sxs-lookup"><span data-stu-id="e59d8-129">Click **Add**.</span></span>  
  
    2.  <span data-ttu-id="e59d8-130">键入或选择按其对数据进行排序的表达式。</span><span class="sxs-lookup"><span data-stu-id="e59d8-130">Type or select an expression by which to sort the data.</span></span>  
  
    3.  <span data-ttu-id="e59d8-131">从“顺序”  列下拉列表中，选择每个表达式的排序方向。</span><span class="sxs-lookup"><span data-stu-id="e59d8-131">From the **Order** column drop-down list, choose the sort direction for each expression.</span></span> <span data-ttu-id="e59d8-132">**A-Z** 按升序对表达式进行排序。</span><span class="sxs-lookup"><span data-stu-id="e59d8-132">**A-Z** sorts the expression in ascending order.</span></span> <span data-ttu-id="e59d8-133">**Z-A** 按降序对表达式进行排序。</span><span class="sxs-lookup"><span data-stu-id="e59d8-133">**Z-A** sorts the expression in descending order.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-sort-x-axis-labels-in-alphabetical-order-on-a-chart"></a><span data-ttu-id="e59d8-134">在图表上按字母顺序对 x 轴标签进行排序</span><span class="sxs-lookup"><span data-stu-id="e59d8-134">To sort x-axis labels in alphabetical order on a chart</span></span>  
  
1.  <span data-ttu-id="e59d8-135">右键单击类别字段拖放区域中的某个字段，再单击“类别组属性”  。</span><span class="sxs-lookup"><span data-stu-id="e59d8-135">Right-click a field in the Category Field drop-zone and click **Category GroupProperties**.</span></span>  
  
2.  <span data-ttu-id="e59d8-136">在 **“类别组属性”** 对话框中，单击 **“排序”** 。</span><span class="sxs-lookup"><span data-stu-id="e59d8-136">In the **Category Group Properties** dialog box, click **Sorting**.</span></span>  
  
3.  <span data-ttu-id="e59d8-137">对于每个排序表达式，请按照下列步骤进行操作：</span><span class="sxs-lookup"><span data-stu-id="e59d8-137">For each sort expression, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="e59d8-138">单击“添加”  。</span><span class="sxs-lookup"><span data-stu-id="e59d8-138">Click **Add**.</span></span>  
  
    2.  <span data-ttu-id="e59d8-139">选择与分组字段匹配的表达式。</span><span class="sxs-lookup"><span data-stu-id="e59d8-139">Select the expression that matches your grouping field.</span></span> <span data-ttu-id="e59d8-140">通过单击 **“分组”** ，可以验证分组字段的表达式。</span><span class="sxs-lookup"><span data-stu-id="e59d8-140">You can verify the expression for the grouping field by clicking **Grouping**.</span></span>  
  
    3.  <span data-ttu-id="e59d8-141">从“顺序”  列下拉列表中，选择每个表达式的排序方向。</span><span class="sxs-lookup"><span data-stu-id="e59d8-141">From the **Order** column drop-down list, choose the sort direction for each expression.</span></span> <span data-ttu-id="e59d8-142">**A-Z** 按升序字母顺序对表达式进行排序。</span><span class="sxs-lookup"><span data-stu-id="e59d8-142">**A-Z** sorts the expression in ascending alphabetical order.</span></span> <span data-ttu-id="e59d8-143">**Z-A** 按降序字母顺序对表达式进行排序。</span><span class="sxs-lookup"><span data-stu-id="e59d8-143">**Z-A** sorts the expression in descending alphabetical order.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-sort-the-data-points-in-ascending-or-descending-order-on-a-chart"></a><span data-ttu-id="e59d8-144">按升序或降序对图表上的数据点进行排序</span><span class="sxs-lookup"><span data-stu-id="e59d8-144">To sort the data points in ascending or descending order on a chart</span></span>  
  
1.  <span data-ttu-id="e59d8-145">右键单击类别字段拖放区域中的某个字段，再单击“类别组属性”  。</span><span class="sxs-lookup"><span data-stu-id="e59d8-145">Right-click a field in the Category Field drop zone and click **Category GroupProperties**.</span></span>  
  
2.  <span data-ttu-id="e59d8-146">在 **“类别组属性”** 对话框中，单击 **“排序”** 。</span><span class="sxs-lookup"><span data-stu-id="e59d8-146">In the **Category Group Properties** dialog box, click **Sorting**.</span></span>  
  
3.  <span data-ttu-id="e59d8-147">对于每个排序表达式，请按照下列步骤进行操作：</span><span class="sxs-lookup"><span data-stu-id="e59d8-147">For each sort expression, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="e59d8-148">单击“添加”  。</span><span class="sxs-lookup"><span data-stu-id="e59d8-148">Click **Add**.</span></span>  
  
    2.  <span data-ttu-id="e59d8-149">选择与数据字段匹配的表达式。</span><span class="sxs-lookup"><span data-stu-id="e59d8-149">Select the expression that matches your data field.</span></span> <span data-ttu-id="e59d8-150">在大多数情况下，此为聚合值，例如 `=Sum(Fields!Quantity.Value)`。</span><span class="sxs-lookup"><span data-stu-id="e59d8-150">In most cases, this is an aggregated value, such as `=Sum(Fields!Quantity.Value)`.</span></span>  
  
    3.  <span data-ttu-id="e59d8-151">从“顺序”  列下拉列表中，选择每个表达式的排序方向。</span><span class="sxs-lookup"><span data-stu-id="e59d8-151">From the **Order** column drop-down list, choose the sort direction for each expression.</span></span> <span data-ttu-id="e59d8-152">**A-Z** 按升序对表达式进行排序。</span><span class="sxs-lookup"><span data-stu-id="e59d8-152">**A-Z** sorts the expression in ascending order.</span></span> <span data-ttu-id="e59d8-153">**Z-A** 按降序对表达式进行排序。</span><span class="sxs-lookup"><span data-stu-id="e59d8-153">**Z-A** sorts the expression in descending order.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-sort-data-in-ascending-or-descending-order-for-display-on-a-gauge"></a><span data-ttu-id="e59d8-154">按升序或降序对数据进行排序以便显示在仪表上</span><span class="sxs-lookup"><span data-stu-id="e59d8-154">To sort data in ascending or descending order for display on a gauge</span></span>  
  
1.  <span data-ttu-id="e59d8-155">右键单击仪表，再单击“添加数据组”  。</span><span class="sxs-lookup"><span data-stu-id="e59d8-155">Right-click the gauge and click **Add Data Group**.</span></span>  
  
2.  <span data-ttu-id="e59d8-156">如有必要，在“仪表面板组属性”  对话框中，单击“常规”  。</span><span class="sxs-lookup"><span data-stu-id="e59d8-156">In the **Gauge Panel GroupProperties** dialog box, click **General** if necessary.</span></span>  
  
3.  <span data-ttu-id="e59d8-157">在 **“组表达式”** 中，单击 **“添加”** 。</span><span class="sxs-lookup"><span data-stu-id="e59d8-157">In **Group expressions**, click **Add**.</span></span>  
  
4.  <span data-ttu-id="e59d8-158">在 **“分组方式”** 中，键入或选择要按其对数据进行分组的表达式。</span><span class="sxs-lookup"><span data-stu-id="e59d8-158">In **Group on**, type or select an expression by which to group the data.</span></span>  
  
5.  <span data-ttu-id="e59d8-159">重复步骤 3 和 4，直到已添加要使用的所有组表达式。</span><span class="sxs-lookup"><span data-stu-id="e59d8-159">Repeat steps 3 and 4 until you have added all the group expressions you want to use.</span></span>  
  
6.  <span data-ttu-id="e59d8-160">单击 **“排序”** 。</span><span class="sxs-lookup"><span data-stu-id="e59d8-160">Click **Sorting**.</span></span>  
  
7.  <span data-ttu-id="e59d8-161">对于每个排序表达式，请按照下列步骤进行操作：</span><span class="sxs-lookup"><span data-stu-id="e59d8-161">For each sort expression, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="e59d8-162">单击“添加”  。</span><span class="sxs-lookup"><span data-stu-id="e59d8-162">Click **Add**.</span></span>  
  
    2.  <span data-ttu-id="e59d8-163">选择与分组字段匹配的表达式。</span><span class="sxs-lookup"><span data-stu-id="e59d8-163">Select the expression that matches your grouping field.</span></span> <span data-ttu-id="e59d8-164">通过单击 **“分组”** ，可以验证分组字段的表达式。</span><span class="sxs-lookup"><span data-stu-id="e59d8-164">You can verify the expression for the grouping field by clicking **Grouping**.</span></span>  
  
    3.  <span data-ttu-id="e59d8-165">从“顺序”  列下拉列表中，选择每个表达式的排序方向。</span><span class="sxs-lookup"><span data-stu-id="e59d8-165">From the **Order** column drop-down list, choose the sort direction for each expression.</span></span> <span data-ttu-id="e59d8-166">**A-Z** 按升序对表达式进行排序。</span><span class="sxs-lookup"><span data-stu-id="e59d8-166">**A-Z** sorts the expression in ascending order.</span></span> <span data-ttu-id="e59d8-167">**Z-A** 按降序对表达式进行排序。</span><span class="sxs-lookup"><span data-stu-id="e59d8-167">**Z-A** sorts the expression in descending order.</span></span>  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
 <span data-ttu-id="e59d8-168">有关如何在仪表中对数据进行分组的详细信息，请参阅[仪表（报表生成器和 SSRS）](gauges-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="e59d8-168">For more information about how data is grouped in a gauge, see [Gauges &#40;Report Builder and SSRS&#41;](gauges-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e59d8-169">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e59d8-169">See Also</span></span>  
 <span data-ttu-id="e59d8-170">[报表生成器对话框、窗格和向导的帮助](../report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span><span class="sxs-lookup"><span data-stu-id="e59d8-170">[Report Builder Help for Dialog Boxes, Panes, and Wizards](../report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span></span>  
 <span data-ttu-id="e59d8-171">[图表 &#40;报表生成器和 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e59d8-171">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="e59d8-172">[设置图表上轴标签的格式 &#40;报表生成器和 SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e59d8-172">[Formatting Axis Labels on a Chart &#40;Report Builder and SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="e59d8-173">对多个形状图指定一致的颜色（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="e59d8-173">Specify Consistent Colors across Multiple Shape Charts &#40;Report Builder and SSRS&#41;</span></span>](shape-charts-report-builder-and-ssrs.md)  
  
  
