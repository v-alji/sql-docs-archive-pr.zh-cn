---
title: 在数据区域中添加或删除组（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4de53c3c-c6fc-49ce-b692-3609fc0b3ec5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c355ca87db578d47181935e1ca6bc48e75bf8b8d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691097"
---
# <a name="add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs"></a><span data-ttu-id="c2d12-102">在数据区域中添加或删除组（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="c2d12-102">Add or Delete a Group in a Data Region (Report Builder and SSRS)</span></span>
  <span data-ttu-id="c2d12-103">如果您希望在显示或计算时根据特定值或表达式集来组织数据，可向数据区域添加组。</span><span class="sxs-lookup"><span data-stu-id="c2d12-103">Add a group to a data region when you want to organize data by a specific value or set of expressions, for display and calculations.</span></span> <span data-ttu-id="c2d12-104">组具有标识该组所包含的数据集数据的名称和表达式。</span><span class="sxs-lookup"><span data-stu-id="c2d12-104">A group has a name and an expression that identifies which data from a dataset belongs to the group.</span></span> <span data-ttu-id="c2d12-105">有关组的详细信息，请参阅 [了解组（报表生成器和 SSRS）](understanding-groups-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="c2d12-105">For more information about groups, see [Understanding Groups &#40;Report Builder and SSRS&#41;](understanding-groups-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="c2d12-106">在 Tablix 数据区域中，单击表、矩阵或列表可以显示“分组”窗格。</span><span class="sxs-lookup"><span data-stu-id="c2d12-106">In a tablix data region, click in the table, matrix, or list to display the Grouping pane.</span></span> <span data-ttu-id="c2d12-107">将数据集字段拖到“行组”和“列组”窗格可以创建父组或子组。</span><span class="sxs-lookup"><span data-stu-id="c2d12-107">Drag dataset fields to the Row Group and Column Group pane to create parent or child groups.</span></span> <span data-ttu-id="c2d12-108">右键单击现有组可以添加相邻组。</span><span class="sxs-lookup"><span data-stu-id="c2d12-108">Right-click an existing group to add an adjacent group.</span></span> <span data-ttu-id="c2d12-109">根据定义，详细信息组是最内部的组，并且只能作为子组添加。</span><span class="sxs-lookup"><span data-stu-id="c2d12-109">By definition, the details group is the innermost group and can only be added as a child group.</span></span> <span data-ttu-id="c2d12-110">右键单击现有组可以删除它。</span><span class="sxs-lookup"><span data-stu-id="c2d12-110">Right-click an existing group to delete it.</span></span> <span data-ttu-id="c2d12-111">显示组值的行和列是自动添加的。</span><span class="sxs-lookup"><span data-stu-id="c2d12-111">Rows and columns on which to display group values are automatically added for you.</span></span> <span data-ttu-id="c2d12-112">有关详细信息，请参阅 [表、矩阵和列表（报表生成器和 SSRS）](tables-matrices-and-lists-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="c2d12-112">For more information, see [Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="c2d12-113">在图表数据区域中，单击图表以显示放置区。</span><span class="sxs-lookup"><span data-stu-id="c2d12-113">In a Chart data region, click in the chart to display the drop-zones.</span></span> <span data-ttu-id="c2d12-114">通过将数据集字段拖到类别和序列放置区来创建组。</span><span class="sxs-lookup"><span data-stu-id="c2d12-114">Create groups by dragging dataset fields to the category and series drop zones.</span></span> <span data-ttu-id="c2d12-115">若要添加嵌套组，请向放置区添加多个字段。</span><span class="sxs-lookup"><span data-stu-id="c2d12-115">To add nested groups, add multiple fields to the drop-zone.</span></span>  
  
 <span data-ttu-id="c2d12-116">默认情况下，组不在仪表中定义。</span><span class="sxs-lookup"><span data-stu-id="c2d12-116">Groups are not defined in a gauge by default.</span></span> <span data-ttu-id="c2d12-117">仪表的默认行为是将指定字段中的所有值聚合为在仪表中显示的一个值。</span><span class="sxs-lookup"><span data-stu-id="c2d12-117">The default behavior for the gauge is to aggregate all values in the specified field into one value that is displayed on the gauge.</span></span> <span data-ttu-id="c2d12-118">有关详细信息，请参阅 [仪表（报表生成器和 SSRS）](gauges-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="c2d12-118">For more information, see [Gauges &#40;Report Builder and SSRS&#41;](gauges-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-parent-or-child-row-or-column-group-to-a-tablix-data-region"></a><span data-ttu-id="c2d12-119">向 Tablix 数据区域添加父/子行组或父/子列组</span><span class="sxs-lookup"><span data-stu-id="c2d12-119">To add a parent or child row or column group to a tablix data region</span></span>  
  
1.  <span data-ttu-id="c2d12-120">将字段从 **“报表数据”** 窗格拖到 **“行组”** 窗格或 **“列组”** 窗格。</span><span class="sxs-lookup"><span data-stu-id="c2d12-120">Drag a field from the **Report Data** pane to the **Row Groups** pane or the **Column Groups** pane.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c2d12-121">如果未显示“分组”窗格，请在“视图”选项卡上，单击“分组”  。</span><span class="sxs-lookup"><span data-stu-id="c2d12-121">If you do not see the Grouping pane, on the View tab, click **Grouping**.</span></span>  
  
2.  <span data-ttu-id="c2d12-122">使用向导栏将该字段拖到组层次结构之上或之下，将其放置到相应位置作为现有组的父组或子组。</span><span class="sxs-lookup"><span data-stu-id="c2d12-122">Drop the field above or below the group hierarchy using the guide bar to place the group as a parent group or a child group to an existing group.</span></span>  
  
     <span data-ttu-id="c2d12-123">添加的组具有默认名称、组表达式和基于字段名称的排序表达式。</span><span class="sxs-lookup"><span data-stu-id="c2d12-123">The group is added with a default name, group expression, and sort expression that is based on the field name.</span></span>  
  
### <a name="to-add-an-adjacent-row-or-column-group-to-a-tablix-data-region"></a><span data-ttu-id="c2d12-124">向 Tablix 数据区域添加相邻的行组或列组</span><span class="sxs-lookup"><span data-stu-id="c2d12-124">To add an adjacent row or column group to a tablix data region</span></span>  
  
1.  <span data-ttu-id="c2d12-125">在“分组”窗格中，右键单击要添加的组的对等组。</span><span class="sxs-lookup"><span data-stu-id="c2d12-125">In the Grouping pane, right-click a group that is a peer to the group that you want to add.</span></span> <span data-ttu-id="c2d12-126">单击 **“添加组”** ，然后单击 **“前面相邻”** 或 **“后面相邻”** 以指定组的添加位置。</span><span class="sxs-lookup"><span data-stu-id="c2d12-126">Click **Add Group**, and then click **Adjacent Before** or **Adjacent After** to specify where to add the group.</span></span> <span data-ttu-id="c2d12-127">此时将打开 **“Tablix 组”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="c2d12-127">The **Tablix Group** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="c2d12-128">在 **“名称”** 中，键入组的名称。</span><span class="sxs-lookup"><span data-stu-id="c2d12-128">In **Name**, type a name for the group.</span></span>  
  
3.  <span data-ttu-id="c2d12-129">在“组表达式”中，键入表达式，或者单击表达式按钮 (fx)，创建表达式   。</span><span class="sxs-lookup"><span data-stu-id="c2d12-129">In **Group expression**, type an expression or click the expression button (**fx**) to create an expression.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="c2d12-130">新组即被添加到“分组”窗格，显示组值的行或列则被添加到设计图面上的 Tablix 数据区域中。</span><span class="sxs-lookup"><span data-stu-id="c2d12-130">A new group is added to the Grouping pane and a row or column on which to display group values is added to the tablix data region on the design surface.</span></span>  
  
### <a name="to-add-a-details-group-to-a-tablix-data-region"></a><span data-ttu-id="c2d12-131">向 tablix 数据区域添加详细信息组</span><span class="sxs-lookup"><span data-stu-id="c2d12-131">To add a details group to a tablix data region</span></span>  
  
1.  <span data-ttu-id="c2d12-132">在“分组”窗格中，右键单击作为最内部的子组的组，而非“详细信息”组  。</span><span class="sxs-lookup"><span data-stu-id="c2d12-132">In the Grouping pane, right-click a group that is the innermost child group, but not the **Details** group.</span></span> <span data-ttu-id="c2d12-133">单击 **“添加组”** ，然后单击 **“子组”** 。</span><span class="sxs-lookup"><span data-stu-id="c2d12-133">Click **Add Group**, and then click **Child Group**.</span></span> <span data-ttu-id="c2d12-134">此时将打开 **“Tablix 组”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="c2d12-134">The **Tablix Group** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="c2d12-135">在 **“组表达式”** 中，使表达式保留为空白。</span><span class="sxs-lookup"><span data-stu-id="c2d12-135">In **Group expression**, leave the expression blank.</span></span> <span data-ttu-id="c2d12-136">详细信息组没有任何表达式。</span><span class="sxs-lookup"><span data-stu-id="c2d12-136">A details group has no expression.</span></span>  
  
3.  <span data-ttu-id="c2d12-137">选择 **“显示详细信息数据”** 。</span><span class="sxs-lookup"><span data-stu-id="c2d12-137">Select **Show detail data**.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="c2d12-138">新的详细信息组作为子组添加到“分组”窗格，在步骤 1 中选择的组的行控点显示详细信息组图标。</span><span class="sxs-lookup"><span data-stu-id="c2d12-138">A new details group is added as a child group in the Grouping pane, and the row handle for the group you selected in step 1 displays the details group icon.</span></span> <span data-ttu-id="c2d12-139">有关控点的详细信息，请参阅 [Tablix 数据区域单元、行和列（报表生成器和 SSRS）](tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="c2d12-139">For more information about handles, see [Tablix Data Region Cells, Rows, and Columns &#40;Report Builder&#41; and SSRS](tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md).</span></span>  
  
### <a name="to-edit-a-row-or-column-group-in-a-tablix-data-region"></a><span data-ttu-id="c2d12-140">在 Tablix 数据区域中编辑行组或列组</span><span class="sxs-lookup"><span data-stu-id="c2d12-140">To edit a row or column group in a tablix data region</span></span>  
  
1.  <span data-ttu-id="c2d12-141">在报表设计图面上，单击 Tablix 数据区域中的任意位置以将其选中。</span><span class="sxs-lookup"><span data-stu-id="c2d12-141">On the report design surface, click anywhere in the tablix data region to select it.</span></span> <span data-ttu-id="c2d12-142">“分组”窗格随即显示行组和列组。</span><span class="sxs-lookup"><span data-stu-id="c2d12-142">The Grouping pane displays the row and column groups.</span></span>  
  
2.  <span data-ttu-id="c2d12-143">右键单击该组，然后单击“组属性”  。</span><span class="sxs-lookup"><span data-stu-id="c2d12-143">Right-click the group, and then click **Group Properties**.</span></span>  
  
3.  <span data-ttu-id="c2d12-144">在 **“名称”** 中，键入组的名称。</span><span class="sxs-lookup"><span data-stu-id="c2d12-144">In **Name**, type the name of the group.</span></span>  
  
4.  <span data-ttu-id="c2d12-145">在“组表达式”中，键入或选择简单表达式，或者单击表达式 (fx) 按钮，创建组表达式   。</span><span class="sxs-lookup"><span data-stu-id="c2d12-145">In **Group expressions**, type or select a simple expression, or click the Expression (**fx**) button to create a group expression.</span></span>  
  
5.  <span data-ttu-id="c2d12-146">单击 **“添加”** 以创建其他表达式。</span><span class="sxs-lookup"><span data-stu-id="c2d12-146">Click **Add** to create additional expressions.</span></span> <span data-ttu-id="c2d12-147">使用逻辑与组合指定的所有表达式，以便指定该组的数据。</span><span class="sxs-lookup"><span data-stu-id="c2d12-147">All expressions you specify are combined using a logical AND to specify data for this group.</span></span>  
  
6.  <span data-ttu-id="c2d12-148">（可选）单击“分页符”设置分页符选项  。</span><span class="sxs-lookup"><span data-stu-id="c2d12-148">(Optional) Click **Page Breaks** to set page break options.</span></span>  
  
7.  <span data-ttu-id="c2d12-149">（可选）单击“排序”，选择或键入指定组中的值的排序顺序的表达式  。</span><span class="sxs-lookup"><span data-stu-id="c2d12-149">(Optional) Click **Sorting** to select or type expressions that specify the sort order for values in the group.</span></span>  
  
8.  <span data-ttu-id="c2d12-150">（可选）单击“可见性”，选择该项的可见性选项  。</span><span class="sxs-lookup"><span data-stu-id="c2d12-150">(Optional) Click **Visibility** to select the visibility options for the item.</span></span>  
  
9. <span data-ttu-id="c2d12-151">（可选）单击“筛选器”，设置该组的筛选器  。</span><span class="sxs-lookup"><span data-stu-id="c2d12-151">(Optional) Click **Filters** to set filters for this group.</span></span>  
  
10. <span data-ttu-id="c2d12-152">（可选）单击“变量”，定义以该组作为作用域、并且可以从任何子组访问的变量  。</span><span class="sxs-lookup"><span data-stu-id="c2d12-152">(Optional) Click **Variables** to define variables scoped to this group and accessible from any child groups.</span></span>  
  
11. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-delete-a-group-from-a-tablix-data-region"></a><span data-ttu-id="c2d12-153">删除 Tablix 数据区域中的组</span><span class="sxs-lookup"><span data-stu-id="c2d12-153">To delete a group from a tablix data region</span></span>  
  
1.  <span data-ttu-id="c2d12-154">在“分组”窗格中，右键单击组，然后单击“删除组”  。</span><span class="sxs-lookup"><span data-stu-id="c2d12-154">In the Grouping pane, right-click the group, and then click **Delete Group**.</span></span>  
  
2.  <span data-ttu-id="c2d12-155">在 **“删除组”** 对话框中，请选择下列选项之一：</span><span class="sxs-lookup"><span data-stu-id="c2d12-155">In the **Delete Group** dialog box, select one of the following options:</span></span>  
  
    -   <span data-ttu-id="c2d12-156">**删除组以及相关行和列** ：选择该选项可以删除组定义和显示组数据的所有相关行。</span><span class="sxs-lookup"><span data-stu-id="c2d12-156">**Delete group and related rows and columns** Choose this option to delete the group definition and all related rows that display group data.</span></span> <span data-ttu-id="c2d12-157">对于详细信息组，如果同一行同时作为详细信息和组数据，则仅删除详细信息数据行。</span><span class="sxs-lookup"><span data-stu-id="c2d12-157">For the details group, if the same row belongs to both detail and group data, only the detail data rows are deleted.</span></span>  
  
    -   <span data-ttu-id="c2d12-158">**仅删除组** 选择该选项可以使 Tablix 数据区域的结构保持不变，并且仅删除组定义。</span><span class="sxs-lookup"><span data-stu-id="c2d12-158">**Delete group only** Choose this option to keep the structure of the tablix data region the same and delete only the group definition.</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-delete-a-details-group-from-a-tablix-data-region"></a><span data-ttu-id="c2d12-159">删除 Tablix 数据区域中的详细信息组</span><span class="sxs-lookup"><span data-stu-id="c2d12-159">To delete a details group from a tablix data region</span></span>  
  
1.  <span data-ttu-id="c2d12-160">在“分组”窗格中，右键单击详细信息组，然后单击“删除组”  。</span><span class="sxs-lookup"><span data-stu-id="c2d12-160">In the Grouping pane, right-click the details group, and then click **Delete Group**.</span></span>  
  
2.  <span data-ttu-id="c2d12-161">在 **“删除组”** 对话框中，请选择下列选项之一：</span><span class="sxs-lookup"><span data-stu-id="c2d12-161">In the **Delete Group** dialog box, select one of the following options:</span></span>  
  
    -   <span data-ttu-id="c2d12-162">**删除组以及相关行和列** ：选择该选项可以删除组定义和显示组数据的所有相关行。</span><span class="sxs-lookup"><span data-stu-id="c2d12-162">**Delete group and related rows and columns** Choose this option to delete the group definition and all related rows that display group data.</span></span> <span data-ttu-id="c2d12-163">对于详细信息组，如果同一行同时作为详细信息和组数据，则仅删除详细信息数据行。</span><span class="sxs-lookup"><span data-stu-id="c2d12-163">For the details group, if the same row belongs to both detail and group data, only the detail data rows are deleted.</span></span>  
  
    -   <span data-ttu-id="c2d12-164">**仅删除组** 选择该选项可以使 Tablix 数据区域的结构保持不变，并且仅删除组定义。</span><span class="sxs-lookup"><span data-stu-id="c2d12-164">**Delete group only** Choose this option to keep the structure of the tablix data region the same and delete only the group definition.</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="c2d12-165">详细信息组即被删除。</span><span class="sxs-lookup"><span data-stu-id="c2d12-165">The details group is deleted.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c2d12-166">验证在删除详细信息行之后，每个单元中的表达式视具体情况指定聚合表达式。</span><span class="sxs-lookup"><span data-stu-id="c2d12-166">Verify that after you remove a details row, the expression in each cell specifies an aggregate expression where appropriate.</span></span> <span data-ttu-id="c2d12-167">如有必要，请编辑表达式以便根据需要指定聚合函数。</span><span class="sxs-lookup"><span data-stu-id="c2d12-167">If necessary, edit the expression to specify aggregate functions as needed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2d12-168">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c2d12-168">See Also</span></span>  
 <span data-ttu-id="c2d12-169">[报表和组变量集合引用（报表生成器和 SSRS）](built-in-collections-report-and-group-variables-references-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="c2d12-169">[Report and Group Variables Collections References &#40;Report Builder and SSRS&#41;](built-in-collections-report-and-group-variables-references-report-builder.md) </span></span>  
 <span data-ttu-id="c2d12-170">[组表达式示例（报表生成器和 SSRS）](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c2d12-170">[Group Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="c2d12-171">[对数据进行筛选、分组和排序（报表生成器和 SSRS）](filter-group-and-sort-data-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c2d12-171">[Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="c2d12-172">[Tablix 数据区域（报表生成器和 SSRS）](../tablix-data-region-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c2d12-172">[Tablix Data Region &#40;Report Builder and SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="c2d12-173">[表（报表生成器和 SSRS）](tables-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c2d12-173">[Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="c2d12-174">[矩阵（报表生成器和 SSRS）](create-a-matrix-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c2d12-174">[Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="c2d12-175">[列表（报表生成器和 SSRS）](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c2d12-175">[Lists &#40;Report Builder and SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="c2d12-176">表、矩阵和列表（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="c2d12-176">Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;</span></span>](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
