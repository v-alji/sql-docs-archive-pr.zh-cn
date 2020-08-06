---
title: 添加筛选器（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 10ae54e7-0e8a-4dff-995d-05516c51d076
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 61a5444c437027d92a9f054e74cbcac6af5cc776
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694253"
---
# <a name="add-a-filter-report-builder-and-ssrs"></a><span data-ttu-id="27451-102">添加筛选器（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="27451-102">Add a Filter (Report Builder and SSRS)</span></span>
  <span data-ttu-id="27451-103">如果您希望在计算或显示时包含或排除特定值，可向数据集、数据区域或组添加筛选器。</span><span class="sxs-lookup"><span data-stu-id="27451-103">Add a filter to a dataset, data region, or group when you want to include or exclude specific values for calculations or display.</span></span> <span data-ttu-id="27451-104">在运行时应用筛选器的顺序为：先对数据集，再对数据区域，最后对组，并按照组层次结构自上而下的顺序。</span><span class="sxs-lookup"><span data-stu-id="27451-104">Filters are applied at run time first on the dataset, and then on the data region, and then on the group, in top-down order for group hierarchies.</span></span> <span data-ttu-id="27451-105">在表、矩阵或列表中，对行组、列组和相邻组分别应用各自的筛选器。</span><span class="sxs-lookup"><span data-stu-id="27451-105">In a table, matrix, or list, filters for row groups, column groups, and adjacent groups are applied independently.</span></span> <span data-ttu-id="27451-106">在图表中，对类别组和序列组分别应用各自的筛选器。</span><span class="sxs-lookup"><span data-stu-id="27451-106">In a chart, filters for category groups and series groups are applied independently.</span></span>  
  
 <span data-ttu-id="27451-107">若要添加筛选器，必须指定一个或多个筛选器公式。</span><span class="sxs-lookup"><span data-stu-id="27451-107">To add a filter, you must specify one or more filter equations.</span></span> <span data-ttu-id="27451-108">筛选器公式由标识了要筛选的数据的表达式、运算符和要比较的值组成。</span><span class="sxs-lookup"><span data-stu-id="27451-108">A filter equation consists of an expression that identifies the data that you want to filter, an operator, and the value to compare to.</span></span> <span data-ttu-id="27451-109">所筛选数据的数据类型和值必须匹配。</span><span class="sxs-lookup"><span data-stu-id="27451-109">The data types of the filtered data and the value must match.</span></span> <span data-ttu-id="27451-110">不支持筛选数据集或数据区域的聚合值。</span><span class="sxs-lookup"><span data-stu-id="27451-110">Filtering on aggregate values for a dataset or data region is not supported.</span></span>  
  
 <span data-ttu-id="27451-111">若要筛选图表中的数据点，可以对类别组或序列组设置筛选器。</span><span class="sxs-lookup"><span data-stu-id="27451-111">To filter data points in a chart, you can set a filter on a category group or a series group.</span></span> <span data-ttu-id="27451-112">默认情况下，图表使用内置函数 Sum 将属于同一组的值聚合到序列中的单个数据点中。</span><span class="sxs-lookup"><span data-stu-id="27451-112">By default, the chart uses the built-in function Sum to aggregate values that belong to the same group into an individual data point in the series.</span></span> <span data-ttu-id="27451-113">如果更改序列的聚合函数，则必须更改筛选表达式中的聚合函数。</span><span class="sxs-lookup"><span data-stu-id="27451-113">If you change the aggregate function of a series, you must change the aggregate function in the filter expression.</span></span>  
  
 <span data-ttu-id="27451-114">有关筛选嵌入数据集和共享数据集的详细信息，请参阅[向数据集添加筛选器（报表生成器和 SSRS）](../report-data/add-a-filter-to-a-dataset-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="27451-114">For more information about filtering embedded and shared datasets, see [Add a Filter to a Dataset &#40;Report Builder and SSRS&#41;](../report-data/add-a-filter-to-a-dataset-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-set-a-filter-on-a-data-region"></a><span data-ttu-id="27451-115">对数据区域设置筛选器</span><span class="sxs-lookup"><span data-stu-id="27451-115">To set a filter on a data region</span></span>  
  
1.  <span data-ttu-id="27451-116">在 **“设计”** 视图中打开报表。</span><span class="sxs-lookup"><span data-stu-id="27451-116">Open a report in **Design** view.</span></span>  
  
2.  <span data-ttu-id="27451-117">在设计图面上选择数据区域，然后右键单击 " _\<data region>_ **属性**"。</span><span class="sxs-lookup"><span data-stu-id="27451-117">Select the data region on the design surface, and then right-click _\<data region>_**Properties**.</span></span> <span data-ttu-id="27451-118">对于仪表，选择 **“仪表面板属性”** 。</span><span class="sxs-lookup"><span data-stu-id="27451-118">For a gauge, select **Gauge Panel Properties**.</span></span> <span data-ttu-id="27451-119">此时将打开 " _\<data region>_ **属性**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="27451-119">The _\<data region>_**Properties** dialog box opens.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="27451-120">在 Tablix 数据区域上，右键单击角部单元格或行或列的控点，然后单击“Tablix 属性”  。</span><span class="sxs-lookup"><span data-stu-id="27451-120">On a Tablix data region, right-click the corner cell or a row or column handle, and then click **Tablix Properties**.</span></span>  
  
3.  <span data-ttu-id="27451-121">单击 **“筛选器”** 。</span><span class="sxs-lookup"><span data-stu-id="27451-121">Click **Filters**.</span></span> <span data-ttu-id="27451-122">此时将显示当前筛选器公式的列表。</span><span class="sxs-lookup"><span data-stu-id="27451-122">This displays the current list of filter equations.</span></span> <span data-ttu-id="27451-123">默认情况下，此列表是空的。</span><span class="sxs-lookup"><span data-stu-id="27451-123">By default, the list is empty.</span></span>  
  
4.  <span data-ttu-id="27451-124">单击“添加”  。</span><span class="sxs-lookup"><span data-stu-id="27451-124">Click **Add**.</span></span> <span data-ttu-id="27451-125">此时将显示一个新的空白筛选器公式。</span><span class="sxs-lookup"><span data-stu-id="27451-125">A new blank filter equation appears.</span></span>  
  
5.  <span data-ttu-id="27451-126">在 **“表达式”** 中，键入或选择要筛选的字段的表达式。</span><span class="sxs-lookup"><span data-stu-id="27451-126">In **Expression**, type or select the expression for the field to filter.</span></span> <span data-ttu-id="27451-127">若要编辑该表达式，请单击表达式 (*fx*) 按钮。</span><span class="sxs-lookup"><span data-stu-id="27451-127">To edit the expression, click the expression (*fx*) button.</span></span>  
  
6.  <span data-ttu-id="27451-128">从下拉框中选择与您在步骤 5 中创建的表达式的数据类型相匹配的数据类型。</span><span class="sxs-lookup"><span data-stu-id="27451-128">From the drop-down box, select the data type that matches the type of data in the expression you created in step 5.</span></span>  
  
7.  <span data-ttu-id="27451-129">在 **“运算符”** 框中，选择一个供筛选器使用的运算符，以比较 **“表达式”** 框和 **“值”** 框中的值。</span><span class="sxs-lookup"><span data-stu-id="27451-129">In the **Operator** box, select the operator that you want the filter to use to compare the values in the **Expression** box and the **Value** box.</span></span> <span data-ttu-id="27451-130">您所选择的运算符将决定下一步中使用的值数。</span><span class="sxs-lookup"><span data-stu-id="27451-130">The operator you choose determines the number of values that are used from the next step.</span></span>  
  
8.  <span data-ttu-id="27451-131">在 **“值”** 框中，键入筛选器对 **“表达式”** 中的值进行比较时的目标表达式或值。</span><span class="sxs-lookup"><span data-stu-id="27451-131">In the **Value** box, type the expression or value against which you want the filter to evaluate the value in **Expression**.</span></span>  
  
     <span data-ttu-id="27451-132">有关筛选器公式的示例，请参阅[筛选器公式示例（报表生成器和 SSRS）](filter-equation-examples-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="27451-132">For examples of filter equations, see [Filter Equation Examples &#40;Report Builder and SSRS&#41;](filter-equation-examples-report-builder-and-ssrs.md).</span></span>  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-set-a-filter-on-a-tablix-row-or-column-group"></a><span data-ttu-id="27451-133">对 Tablix 行或列组设置筛选器</span><span class="sxs-lookup"><span data-stu-id="27451-133">To set a filter on a Tablix row or column group</span></span>  
  
1.  <span data-ttu-id="27451-134">在 **“设计”** 视图中打开报表。</span><span class="sxs-lookup"><span data-stu-id="27451-134">Open a report in **Design** view.</span></span>  
  
2.  <span data-ttu-id="27451-135">右键单击设计图面上的表、矩阵或列表数据区域以将其选中。</span><span class="sxs-lookup"><span data-stu-id="27451-135">Right-click the table, matrix, or list data region on the design surface to select it.</span></span> <span data-ttu-id="27451-136">“分组”窗格将显示所选项的组。</span><span class="sxs-lookup"><span data-stu-id="27451-136">The Grouping pane displays the groups for the selected item.</span></span>  
  
3.  <span data-ttu-id="27451-137">在“分组”窗格中，右键单击组，然后单击“编辑组”  。</span><span class="sxs-lookup"><span data-stu-id="27451-137">In the Grouping pane, right-click the group, and then click **Edit Group**.</span></span> <span data-ttu-id="27451-138">此时将打开 **“Tablix 组”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="27451-138">The **Tablix Group** dialog box opens.</span></span>  
  
4.  <span data-ttu-id="27451-139">单击 **“筛选器”** 。</span><span class="sxs-lookup"><span data-stu-id="27451-139">Click **Filters**.</span></span> <span data-ttu-id="27451-140">此时将显示当前筛选器公式的列表。</span><span class="sxs-lookup"><span data-stu-id="27451-140">This displays the current list of filter equations.</span></span> <span data-ttu-id="27451-141">默认情况下，此列表是空的。</span><span class="sxs-lookup"><span data-stu-id="27451-141">By default, the list is empty.</span></span>  
  
5.  <span data-ttu-id="27451-142">单击“添加”  。</span><span class="sxs-lookup"><span data-stu-id="27451-142">Click **Add**.</span></span> <span data-ttu-id="27451-143">此时将显示一个新的空白筛选器公式。</span><span class="sxs-lookup"><span data-stu-id="27451-143">A new blank filter equation appears.</span></span>  
  
6.  <span data-ttu-id="27451-144">在 **“表达式”** 中，键入或选择要筛选的字段的表达式。</span><span class="sxs-lookup"><span data-stu-id="27451-144">In **Expression**, type or select the expression for the field to filter.</span></span> <span data-ttu-id="27451-145">若要编辑该表达式，请单击表达式 (*fx*) 按钮。</span><span class="sxs-lookup"><span data-stu-id="27451-145">To edit the expression, click the expression (*fx*) button.</span></span>  
  
7.  <span data-ttu-id="27451-146">从下拉框中选择与您在步骤 5 中创建的表达式的数据类型相匹配的数据类型。</span><span class="sxs-lookup"><span data-stu-id="27451-146">From the drop-down box, select the data type that matches the type of data in the expression you created in step 5.</span></span>  
  
8.  <span data-ttu-id="27451-147">在 **“运算符”** 框中，选择一个供筛选器使用的运算符，以比较 **“表达式”** 框和 **“值”** 框中的值。</span><span class="sxs-lookup"><span data-stu-id="27451-147">In the **Operator** box, select the operator that you want the filter to use to compare the values in the **Expression** box and the **Value** box.</span></span> <span data-ttu-id="27451-148">您所选择的运算符将决定下一步中使用的值数。</span><span class="sxs-lookup"><span data-stu-id="27451-148">The operator you choose determines the number of values that are used from the next step.</span></span>  
  
9. <span data-ttu-id="27451-149">在 **“值”** 框中，键入筛选器对 **“表达式”** 中的值进行比较时的目标表达式或值。</span><span class="sxs-lookup"><span data-stu-id="27451-149">In the **Value** box, type the expression or value against which you want the filter to evaluate the value in **Expression**.</span></span>  
  
     <span data-ttu-id="27451-150">有关筛选器公式的示例，请参阅[筛选器公式示例（报表生成器和 SSRS）](filter-equation-examples-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="27451-150">For examples of filter equations, see [Filter Equation Examples &#40;Report Builder and SSRS&#41;](filter-equation-examples-report-builder-and-ssrs.md).</span></span>  
  
10. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-set-a-filter-on-a-chart-category-group"></a><span data-ttu-id="27451-151">对图表类别组设置筛选器</span><span class="sxs-lookup"><span data-stu-id="27451-151">To set a filter on a Chart category group</span></span>  
  
1.  <span data-ttu-id="27451-152">在 **“设计”** 视图中打开报表。</span><span class="sxs-lookup"><span data-stu-id="27451-152">Open a report in **Design** view.</span></span>  
  
2.  <span data-ttu-id="27451-153">在设计图面上，单击图表两次以调出数据、序列和类别字段放置区。</span><span class="sxs-lookup"><span data-stu-id="27451-153">On the design surface, click the chart twice to bring up data, series and category field drop zones.</span></span>  
  
3.  <span data-ttu-id="27451-154">右键单击包含在类别字段放置区中的字段，然后选择“类别组属性”  。</span><span class="sxs-lookup"><span data-stu-id="27451-154">Right-click on a field contained in the category field drop zone and select **Category Group Properties**.</span></span>  
  
4.  <span data-ttu-id="27451-155">单击 **“筛选器”** 。</span><span class="sxs-lookup"><span data-stu-id="27451-155">Click **Filters**.</span></span> <span data-ttu-id="27451-156">此时将显示当前筛选器公式的列表。</span><span class="sxs-lookup"><span data-stu-id="27451-156">This displays the current list of filter equations.</span></span> <span data-ttu-id="27451-157">默认情况下，此列表是空的。</span><span class="sxs-lookup"><span data-stu-id="27451-157">By default, the list is empty.</span></span>  
  
5.  <span data-ttu-id="27451-158">单击“添加”  。</span><span class="sxs-lookup"><span data-stu-id="27451-158">Click **Add**.</span></span> <span data-ttu-id="27451-159">此时将显示一个新的空白筛选器公式。</span><span class="sxs-lookup"><span data-stu-id="27451-159">A new blank filter equation appears.</span></span>  
  
6.  <span data-ttu-id="27451-160">在 **“表达式”** 中，键入或选择要筛选的字段的表达式。</span><span class="sxs-lookup"><span data-stu-id="27451-160">In **Expression**, type or select the expression for the field to filter.</span></span> <span data-ttu-id="27451-161">若要编辑该表达式，请单击表达式 (*fx*) 按钮。</span><span class="sxs-lookup"><span data-stu-id="27451-161">To edit the expression, click the expression (*fx*) button.</span></span>  
  
7.  <span data-ttu-id="27451-162">从下拉框中选择与您在步骤 5 中创建的表达式的数据类型相匹配的数据类型。</span><span class="sxs-lookup"><span data-stu-id="27451-162">From the drop-down box, select the data type that matches the type of data in the expression you created in step 5.</span></span>  
  
8.  <span data-ttu-id="27451-163">在 **“运算符”** 框中，选择一个供筛选器使用的运算符，以比较 **“表达式”** 框和 **“值”** 框中的值。</span><span class="sxs-lookup"><span data-stu-id="27451-163">In the **Operator** box, select the operator that you want the filter to use to compare the values in the **Expression** box and the **Value** box.</span></span> <span data-ttu-id="27451-164">您所选择的运算符将决定下一步中使用的值数。</span><span class="sxs-lookup"><span data-stu-id="27451-164">The operator you choose determines the number of values that are used from the next step.</span></span>  
  
9. <span data-ttu-id="27451-165">在 **“值”** 框中，键入筛选器对 **“表达式”** 中的值进行比较时的目标表达式或值。</span><span class="sxs-lookup"><span data-stu-id="27451-165">In the **Value** box, type the expression or value against which you want the filter to evaluate the value in **Expression**.</span></span>  
  
     <span data-ttu-id="27451-166">有关筛选器公式的示例，请参阅[筛选器公式示例（报表生成器和 SSRS）](filter-equation-examples-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="27451-166">For examples of filter equations, see [Filter Equation Examples &#40;Report Builder and SSRS&#41;](filter-equation-examples-report-builder-and-ssrs.md).</span></span>  
  
10. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-set-a-filter-on-a-chart-series-group"></a><span data-ttu-id="27451-167">对图表序列组设置筛选器</span><span class="sxs-lookup"><span data-stu-id="27451-167">To set a filter on a Chart series group</span></span>  
  
1.  <span data-ttu-id="27451-168">在 **“设计”** 视图中打开报表。</span><span class="sxs-lookup"><span data-stu-id="27451-168">Open a report in **Design** view.</span></span>  
  
2.  <span data-ttu-id="27451-169">在设计图面上，单击图表两次以调出数据、序列和类别字段放置区。</span><span class="sxs-lookup"><span data-stu-id="27451-169">On the design surface, click the chart twice to bring up data, series and category field drop zones.</span></span>  
  
3.  <span data-ttu-id="27451-170">右键单击包含在序列字段放置区中的字段，然后选择“序列组属性”  。</span><span class="sxs-lookup"><span data-stu-id="27451-170">Right-click on a field contained in the series field drop zone and select **Series Group Properties**.</span></span>  
  
4.  <span data-ttu-id="27451-171">单击 **“筛选器”** 。</span><span class="sxs-lookup"><span data-stu-id="27451-171">Click **Filters**.</span></span> <span data-ttu-id="27451-172">此时将显示当前筛选器公式的列表。</span><span class="sxs-lookup"><span data-stu-id="27451-172">This displays the current list of filter equations.</span></span> <span data-ttu-id="27451-173">默认情况下，此列表是空的。</span><span class="sxs-lookup"><span data-stu-id="27451-173">By default, the list is empty.</span></span>  
  
5.  <span data-ttu-id="27451-174">单击“添加”  。</span><span class="sxs-lookup"><span data-stu-id="27451-174">Click **Add**.</span></span> <span data-ttu-id="27451-175">此时将显示一个新的空白筛选器公式。</span><span class="sxs-lookup"><span data-stu-id="27451-175">A new blank filter equation appears.</span></span>  
  
6.  <span data-ttu-id="27451-176">在 **“表达式”** 中，键入或选择要筛选的字段的表达式。</span><span class="sxs-lookup"><span data-stu-id="27451-176">In **Expression**, type or select the expression for the field to filter.</span></span> <span data-ttu-id="27451-177">若要编辑该表达式，请单击表达式 (*fx*) 按钮。</span><span class="sxs-lookup"><span data-stu-id="27451-177">To edit the expression, click the expression (*fx*) button.</span></span>  
  
7.  <span data-ttu-id="27451-178">从下拉框中选择与您在步骤 5 中创建的表达式的数据类型相匹配的数据类型。</span><span class="sxs-lookup"><span data-stu-id="27451-178">From the drop-down box, select the data type that matches the type of data in the expression you created in step 5.</span></span>  
  
8.  <span data-ttu-id="27451-179">在 **“运算符”** 框中，选择一个供筛选器使用的运算符，以比较 **“表达式”** 框和 **“值”** 框中的值。</span><span class="sxs-lookup"><span data-stu-id="27451-179">In the **Operator** box, select the operator that you want the filter to use to compare the values in the **Expression** box and the **Value** box.</span></span> <span data-ttu-id="27451-180">您所选择的运算符将决定下一步中使用的值数。</span><span class="sxs-lookup"><span data-stu-id="27451-180">The operator you choose determines the number of values that are used from the next step.</span></span>  
  
9. <span data-ttu-id="27451-181">在 **“值”** 框中，键入筛选器对 **“表达式”** 中的值进行比较时的目标表达式或值。</span><span class="sxs-lookup"><span data-stu-id="27451-181">In the **Value** box, type the expression or value against which you want the filter to evaluate the value in **Expression**.</span></span>  
  
     <span data-ttu-id="27451-182">有关筛选器公式的示例，请参阅[筛选器公式示例（报表生成器和 SSRS）](filter-equation-examples-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="27451-182">For examples of filter equations, see [Filter Equation Examples &#40;Report Builder and SSRS&#41;](filter-equation-examples-report-builder-and-ssrs.md).</span></span>  
  
10. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="27451-183">另请参阅</span><span class="sxs-lookup"><span data-stu-id="27451-183">See Also</span></span>  
 <span data-ttu-id="27451-184">[添加数据集筛选器、数据区域筛选器和组筛选器（报表生成器和 SSRS）](add-dataset-filters-data-region-filters-and-group-filters.md) </span><span class="sxs-lookup"><span data-stu-id="27451-184">[Add Dataset Filters, Data Region Filters, and Group Filters &#40;Report Builder and SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md) </span></span>  
 <span data-ttu-id="27451-185">[表达式示例（报表生成器和 SSRS）](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="27451-185">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="27451-186">[仪表（报表生成器和 SSRS）](gauges-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="27451-186">[Gauges &#40;Report Builder and SSRS&#41;](gauges-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="27451-187">[列出 &#40;报表生成器和 SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="27451-187">[Lists &#40;Report Builder and SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="27451-188">图表&#40;报表生成器和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="27451-188">Charts &#40;Report Builder and SSRS&#41;</span></span>](charts-report-builder-and-ssrs.md)  
  
  
