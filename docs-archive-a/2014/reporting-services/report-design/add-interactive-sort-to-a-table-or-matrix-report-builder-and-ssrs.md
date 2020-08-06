---
title: 向表或矩阵添加交互式排序（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10121"
- sql12.rtp.rptdesigner.textboxproperties.intrctvsort.f1
ms.assetid: 05819637-729b-4cf6-82de-91a99f184ec6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c0c453a8ea338ab9a09d7552c064f2eb85add985
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692731"
---
# <a name="add-interactive-sort-to-a-table-or-matrix-report-builder-and-ssrs"></a><span data-ttu-id="e06ee-102">向表或矩阵添加交互式排序（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="e06ee-102">Add Interactive Sort to a Table or Matrix (Report Builder and SSRS)</span></span>
  <span data-ttu-id="e06ee-103">添加交互式排序按钮可以让用户能够更改表和矩阵中行和列的排序顺序。</span><span class="sxs-lookup"><span data-stu-id="e06ee-103">Add interactive sort buttons to enable users to change the sort order of rows and columns in tables and matrices.</span></span> <span data-ttu-id="e06ee-104">只有支持用户交互的呈现格式（例如 HTML）才支持此功能。</span><span class="sxs-lookup"><span data-stu-id="e06ee-104">This feature is supported only in rendering formats that support user interaction, such as HTML.</span></span>  
  
 <span data-ttu-id="e06ee-105">创建交互式排序按钮时，必须指定要排序的对象、排序依据以及要应用排序的作用域。</span><span class="sxs-lookup"><span data-stu-id="e06ee-105">When you create an interactive sort button, you must specify what to sort, what to sort by, and the scope to which to apply the sort.</span></span> <span data-ttu-id="e06ee-106">例如，可以按客户姓氏对详细信息行进行排序，按销售额对类别组中的子类别组值进行排序，或者按总计对类别和子类别组值的组合进行排序。</span><span class="sxs-lookup"><span data-stu-id="e06ee-106">For example, you can sort detail rows by customer last name, subcategory group values within a category group by sales, or category and subcategory group values combined by totals.</span></span>  
  
 <span data-ttu-id="e06ee-107">查看报表时，支持交互式排序的列带有箭头图标，图标可以更改来指示排序顺序。</span><span class="sxs-lookup"><span data-stu-id="e06ee-107">When you view the report, columns that support interactive sorting have arrow icons that change to indicate the sort order.</span></span> <span data-ttu-id="e06ee-108">第一次单击交互式排序按钮时，将按升序对项进行排序。</span><span class="sxs-lookup"><span data-stu-id="e06ee-108">The first time you click an interactive sort button, items are sorted in ascending order.</span></span> <span data-ttu-id="e06ee-109">随后单击则会在升序和降序之间切换排序顺序。</span><span class="sxs-lookup"><span data-stu-id="e06ee-109">Subsequent clicks toggle the sort order between ascending and descending order.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="in-this-article"></a><a name="BackToTop"></a> <span data-ttu-id="e06ee-110">本文内容</span><span class="sxs-lookup"><span data-stu-id="e06ee-110">In this Article</span></span>  
 [<span data-ttu-id="e06ee-111">对不具有组的表的详细信息行进行排序</span><span class="sxs-lookup"><span data-stu-id="e06ee-111">Sorting Detail Rows for a Table with No Groups</span></span>](#SortingDetailRows)  
  
 [<span data-ttu-id="e06ee-112">对表或矩阵的顶级父行组进行排序</span><span class="sxs-lookup"><span data-stu-id="e06ee-112">Sorting a Top Level Parent Row Group for a Table or Matrix</span></span>](#SortingTopLevelParent)  
  
 [<span data-ttu-id="e06ee-113">对组的子组或详细信息行进行排序</span><span class="sxs-lookup"><span data-stu-id="e06ee-113">Sorting Child Groups or Detail Rows for a Group</span></span>](#SortingChildGroups)  
  
 [<span data-ttu-id="e06ee-114">基于复杂组表达式对行进行排序</span><span class="sxs-lookup"><span data-stu-id="e06ee-114">Sorting Rows Based on a Complex Group Expression</span></span>](#SortingMultipleRowGroups)  
  
 [<span data-ttu-id="e06ee-115">同步多个数据区域的排序顺序</span><span class="sxs-lookup"><span data-stu-id="e06ee-115">Synchronizing Sort Order for Multiple Data Regions</span></span>](#SynchronizingSortOrder)  
  
##  <a name="sorting-detail-rows-for-a-table-with-no-groups"></a><a name="SortingDetailRows"></a> <span data-ttu-id="e06ee-116">对不具有组的表的详细信息行进行排序</span><span class="sxs-lookup"><span data-stu-id="e06ee-116">Sorting Detail Rows for a Table with No Groups</span></span>  
 <span data-ttu-id="e06ee-117">将交互式排序按钮添加到列标题，可使用户能够单击列标题并按该列中显示的值对表中的详细信息行进行排序。</span><span class="sxs-lookup"><span data-stu-id="e06ee-117">Add an interactive sort button to a column header to enable a user to click the column header and sort the details rows in a table by the value displayed in that column.</span></span>  
  
#### <a name="to-add-an-interactive-sort-button-to-a-column-header-to-sort-the-table-by-value"></a><span data-ttu-id="e06ee-118">将交互式排序按钮添加到列标题以按值对表进行排序</span><span class="sxs-lookup"><span data-stu-id="e06ee-118">To add an interactive sort button to a column header to sort the table by value</span></span>  
  
1.  <span data-ttu-id="e06ee-119">在报表设计视图内不具有组的表中，右键单击要向其添加交互式排序按钮的列标题中的文本框，再单击“文本框属性”  。</span><span class="sxs-lookup"><span data-stu-id="e06ee-119">In report design view, in a table with no groups, right-click the text box in the column header to which you want to add an interactive sort button, and then click **Text Box Properties**.</span></span>  
  
2.  <span data-ttu-id="e06ee-120">单击 **“交互式排序”** 。</span><span class="sxs-lookup"><span data-stu-id="e06ee-120">Click **Interactive Sorting**.</span></span>  
  
3.  <span data-ttu-id="e06ee-121">选择 **“对此文本框启用交互式排序”** 。</span><span class="sxs-lookup"><span data-stu-id="e06ee-121">Select **Enable interactive sorting on this text box**.</span></span>  
  
4.  <span data-ttu-id="e06ee-122">在 **“选择排序对象”** 中，单击 **“详细信息行”** 。</span><span class="sxs-lookup"><span data-stu-id="e06ee-122">In **Choose what to sort**, click **Detail rows**.</span></span>  
  
5.  <span data-ttu-id="e06ee-123">在 **“排序依据”** 中，指定排序表达式。</span><span class="sxs-lookup"><span data-stu-id="e06ee-123">In **Sort by**, specify a sort expression.</span></span> <span data-ttu-id="e06ee-124">从下拉列表中，选择与要为其定义排序操作的列对应的字段（例如，对名为“Title”的列标题，选择 `[Title]`）。</span><span class="sxs-lookup"><span data-stu-id="e06ee-124">From the drop-down list, select the field that corresponds to the column for which you are defining a sort action (for example, for a column heading named "Title", choose `[Title]`).</span></span> <span data-ttu-id="e06ee-125">需要指定排序表达式。</span><span class="sxs-lookup"><span data-stu-id="e06ee-125">Specifying a sort expression is required.</span></span>  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
7.  <span data-ttu-id="e06ee-126">对要向其添加交互式排序按钮的每一列重复步骤 1-6。</span><span class="sxs-lookup"><span data-stu-id="e06ee-126">Repeat steps 1-6 for every column to which you want to add an interactive sort button.</span></span>  
  
 <span data-ttu-id="e06ee-127">若要验证排序操作，请单击 **“运行”** 以预览报表，然后单击交互式排序按钮。</span><span class="sxs-lookup"><span data-stu-id="e06ee-127">To verify the sort action, click **Run** to preview the report, and then click the interactive sort buttons.</span></span>  
  
 <span data-ttu-id="e06ee-128">![用于“返回页首”链接的箭头图标](../../2014-toc/media/uparrow16x16.gif "用于返回页首链接的箭头图标") [返回页首](#BackToTop)</span><span class="sxs-lookup"><span data-stu-id="e06ee-128">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [Back to Top](#BackToTop)</span></span>  
  
##  <a name="sorting-a-top-level-parent-row-group-for-a-table-or-matrix"></a><a name="SortingTopLevelParent"></a> <span data-ttu-id="e06ee-129">对表或矩阵的顶级父行组进行排序</span><span class="sxs-lookup"><span data-stu-id="e06ee-129">Sorting a Top-Level Parent Row Group for a Table or Matrix</span></span>  
 <span data-ttu-id="e06ee-130">将交互式排序按钮添加到列标题，可使用户能够单击列标题并按该列中显示的值对表或矩阵中的父组行进行排序。</span><span class="sxs-lookup"><span data-stu-id="e06ee-130">Add an interactive sort button to a column header to enable a user to click the column header and sort the parent group rows in a table or matrix by the value displayed in that column.</span></span> <span data-ttu-id="e06ee-131">子组的顺序保持不变。</span><span class="sxs-lookup"><span data-stu-id="e06ee-131">The order of child groups remains unchanged.</span></span>  
  
#### <a name="to-add-an-interactive-sort-button-to-a-column-header-to-sort-groups"></a><span data-ttu-id="e06ee-132">将交互式排序按钮添加到列标题以对组进行排序</span><span class="sxs-lookup"><span data-stu-id="e06ee-132">To add an interactive sort button to a column header to sort groups</span></span>  
  
1.  <span data-ttu-id="e06ee-133">在报表设计视图内的表或矩阵中，右键单击要向其添加交互式排序按钮的组的列标题中的文本框，再单击“文本框属性”  。</span><span class="sxs-lookup"><span data-stu-id="e06ee-133">In a table or matrix in report design view, right-click the text box in the column header for the group to which you want to add an interactive sort button, and then click **Text Box Properties**.</span></span>  
  
2.  <span data-ttu-id="e06ee-134">单击 **“交互式排序”** 。</span><span class="sxs-lookup"><span data-stu-id="e06ee-134">Click **Interactive Sorting**.</span></span>  
  
3.  <span data-ttu-id="e06ee-135">选择 **“对此文本框启用交互式排序”** 。</span><span class="sxs-lookup"><span data-stu-id="e06ee-135">Select **Enable interactive sorting on this text box**.</span></span>  
  
4.  <span data-ttu-id="e06ee-136">在 **“选择排序对象”** 中，单击 **“组”** 。</span><span class="sxs-lookup"><span data-stu-id="e06ee-136">In **Choose what to sort**, click **Groups**.</span></span>  
  
5.  <span data-ttu-id="e06ee-137">从下拉列表中，选择要排序的组的名称。</span><span class="sxs-lookup"><span data-stu-id="e06ee-137">From the drop-down list, select the name of the group that you are sorting.</span></span> <span data-ttu-id="e06ee-138">对于基于简单组表达式的组，将用组表达式填充 **“排序依据”** 值。</span><span class="sxs-lookup"><span data-stu-id="e06ee-138">For groups based on simple group expressions, the **Sort by** value is populated with group expression.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e06ee-139">对于复杂组表达式，请将“排序依据”表达式手动设置为与组表达式相同的值  。</span><span class="sxs-lookup"><span data-stu-id="e06ee-139">For complex group expressions, manually set the **Sort by** expression to the same value as the group expression.</span></span>  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
 <span data-ttu-id="e06ee-140">若要验证排序操作，请单击 **“运行”** 以预览报表，然后单击交互式排序按钮。</span><span class="sxs-lookup"><span data-stu-id="e06ee-140">To verify the sort action, click **Run** to preview the report, and then click the interactive sort buttons.</span></span>  
  
 <span data-ttu-id="e06ee-141">![用于“返回页首”链接的箭头图标](../../2014-toc/media/uparrow16x16.gif "用于返回页首链接的箭头图标") [返回页首](#BackToTop)</span><span class="sxs-lookup"><span data-stu-id="e06ee-141">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [Back to Top](#BackToTop)</span></span>  
  
##  <a name="sorting-child-groups-or-detail-rows-for-a-group"></a><a name="SortingChildGroups"></a> <span data-ttu-id="e06ee-142">对组的子组或详细信息行进行排序</span><span class="sxs-lookup"><span data-stu-id="e06ee-142">Sorting Child Groups or Detail Rows for a Group</span></span>  
 <span data-ttu-id="e06ee-143">将交互式排序按钮添加到组头行，可使用户能够对父组中的子组的值进行排序，或者对最内部的子组的详细信息行进行排序。</span><span class="sxs-lookup"><span data-stu-id="e06ee-143">Add an interactive sort button to a group header row to enable the user to sort the values of a child group from a parent group or to sort the detail rows for the innermost child group.</span></span>  
  
#### <a name="to-add-an-interactive-sort-button-to-a-text-box-in-a-group-row-header-to-sort-child-groups-or-detail-rows"></a><span data-ttu-id="e06ee-144">将交互式排序按钮添加到组行标题中的文本框以对子组或详细信息行进行排序</span><span class="sxs-lookup"><span data-stu-id="e06ee-144">To add an interactive sort button to a text box in a group row header to sort child groups or detail rows</span></span>  
  
1.  <span data-ttu-id="e06ee-145">在报表设计视图中，右键单击要向其添加交互式排序按钮的组头行中的文本框，然后单击“文本框属性”  。</span><span class="sxs-lookup"><span data-stu-id="e06ee-145">In report design view, right-click the text box in the group header row to which you want to add an interactive sort button, and then click **Text Box Properties**.</span></span>  
  
2.  <span data-ttu-id="e06ee-146">单击 **“交互式排序”** 。</span><span class="sxs-lookup"><span data-stu-id="e06ee-146">Click **Interactive Sorting**.</span></span>  
  
3.  <span data-ttu-id="e06ee-147">选择 **“对此文本框启用交互式排序”** 。</span><span class="sxs-lookup"><span data-stu-id="e06ee-147">Select **Enable interactive sorting on this text box**.</span></span>  
  
4.  <span data-ttu-id="e06ee-148">在 **“选择排序对象”** 中，单击下列某个选项：</span><span class="sxs-lookup"><span data-stu-id="e06ee-148">In **Choose what to sort**, click one of the following options:</span></span>  
  
    -   <span data-ttu-id="e06ee-149">**详细信息** ：单击 **“详细信息”** 以对详细信息行进行排序。</span><span class="sxs-lookup"><span data-stu-id="e06ee-149">**Details** Click **Details** to sort the detail rows.</span></span> <span data-ttu-id="e06ee-150">从下拉列表中，选择要按其排序的字段。</span><span class="sxs-lookup"><span data-stu-id="e06ee-150">From the drop-down list, select the field to sort by.</span></span> <span data-ttu-id="e06ee-151">对于此选项，必须指定要按其排序的值。</span><span class="sxs-lookup"><span data-stu-id="e06ee-151">For this option, you must specify the value to sort by.</span></span>  
  
    -   <span data-ttu-id="e06ee-152">**组** ：单击 **“组”** 以对子组值进行排序。</span><span class="sxs-lookup"><span data-stu-id="e06ee-152">**Groups** Click **Groups** to sort the child group values.</span></span> <span data-ttu-id="e06ee-153">对于此选项，将从组表达式自动填充 **“排序依据”** 表达式。</span><span class="sxs-lookup"><span data-stu-id="e06ee-153">For this option, the **Sort by** expression is automatically filled in from the group expression.</span></span>  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
 <span data-ttu-id="e06ee-154">若要验证排序操作，请单击 **“运行”** 以预览报表，然后单击交互式排序按钮。</span><span class="sxs-lookup"><span data-stu-id="e06ee-154">To verify the sort action, click **Run** to preview the report, and then click the interactive sort buttons.</span></span>  
  
 <span data-ttu-id="e06ee-155">![用于“返回页首”链接的箭头图标](../../2014-toc/media/uparrow16x16.gif "用于返回页首链接的箭头图标") [返回页首](#BackToTop)</span><span class="sxs-lookup"><span data-stu-id="e06ee-155">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [Back to Top](#BackToTop)</span></span>  
  
##  <a name="sorting-rows-based-on-a-complex-group-expression"></a><a name="SortingMultipleRowGroups"></a> <span data-ttu-id="e06ee-156">基于复杂组表达式对行进行排序</span><span class="sxs-lookup"><span data-stu-id="e06ee-156">Sorting Rows Based on a Complex Group Expression</span></span>  
 <span data-ttu-id="e06ee-157">将交互式排序按钮添加到列标题，可使用户能够单击列标题并对组合的父组和子组进行排序。</span><span class="sxs-lookup"><span data-stu-id="e06ee-157">Add an interactive sort button to a column header to enable a user to click the column header and sort the combined parent and child groups.</span></span> <span data-ttu-id="e06ee-158">若要获得此效果，必须将组表达式更改为两个组的组合。</span><span class="sxs-lookup"><span data-stu-id="e06ee-158">To achieve this affect, you must change the group expression to be a composite of both groups.</span></span> <span data-ttu-id="e06ee-159">例如，假定用一个矩阵显示某个商店中按颜色和大小分组的商品的库存总计。</span><span class="sxs-lookup"><span data-stu-id="e06ee-159">For example, suppose a matrix displays inventory totals for a store for items grouped by both color and size.</span></span> <span data-ttu-id="e06ee-160">若要基于颜色和大小的组合对行进行排序，而不是让颜色和大小各有单独的组，则可以基于颜色和大小的组合来定义组。</span><span class="sxs-lookup"><span data-stu-id="e06ee-160">To sort the rows based on the combination of color and size, instead of having a separate group for color and a separate group for size, you can define a group based on the combination of color and size.</span></span> <span data-ttu-id="e06ee-161">有关定义组表达式的详细信息，请参阅[组表达式示例（报表生成器和 SSRS）](expression-examples-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="e06ee-161">For more information about defining group expressions, see [Group Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="e06ee-162">在下面的过程中，术语指定 Tablix 数据区域。</span><span class="sxs-lookup"><span data-stu-id="e06ee-162">In the following procedure, terms specify tablix data region areas.</span></span> <span data-ttu-id="e06ee-163">有关详细信息，请参阅 [Tablix 数据区域（报表生成器和 SSRS）](tablix-data-region-areas-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="e06ee-163">For more information, see [Tablix Data Region Areas &#40;Report Builder and SSRS&#41;](tablix-data-region-areas-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="e06ee-164">通常，基于多个组对行进行排序时，希望看到排序行的总计，而不考虑列组。</span><span class="sxs-lookup"><span data-stu-id="e06ee-164">Typically, when you sort rows based on multiple groups, you want to see totals for the sorted rows, regardless of column groups.</span></span> <span data-ttu-id="e06ee-165">在此过程中，不使用任何列组。</span><span class="sxs-lookup"><span data-stu-id="e06ee-165">In this procedure, no column groups are used.</span></span> <span data-ttu-id="e06ee-166">开始将添加矩阵并删除默认列组。</span><span class="sxs-lookup"><span data-stu-id="e06ee-166">You start by adding a matrix and removing the default column group.</span></span> <span data-ttu-id="e06ee-167">另外，开始也可以添加表并删除详细信息组。</span><span class="sxs-lookup"><span data-stu-id="e06ee-167">Alternatively, you could start by adding a table and removing the details group.</span></span>  
  
#### <a name="to-add-an-interactive-sort-button-to-a-column-header-to-sort-multiple-groups"></a><span data-ttu-id="e06ee-168">将交互式排序按钮添加到列标题以对多个组进行排序</span><span class="sxs-lookup"><span data-stu-id="e06ee-168">To add an interactive sort button to a column header to sort multiple groups</span></span>  
  
1.  <span data-ttu-id="e06ee-169">在报表设计视图中，添加一个矩阵。</span><span class="sxs-lookup"><span data-stu-id="e06ee-169">In report design view, add a matrix.</span></span>  
  
2.  <span data-ttu-id="e06ee-170">将数值字段拖到数据单元，以将数据集链接到该矩阵。</span><span class="sxs-lookup"><span data-stu-id="e06ee-170">Drag a numeric field to the data cell to link the dataset to the matrix.</span></span>  
  
     <span data-ttu-id="e06ee-171">接下来，您将需要用指定多个字段的组表达式创建组，并创建一个组头以用来显示组值。</span><span class="sxs-lookup"><span data-stu-id="e06ee-171">Next, you will create a group with a group expression that specifies multiple fields, and a group header to use to display the group values.</span></span>  
  
3.  <span data-ttu-id="e06ee-172">确认在设计图面上已选择该矩阵。</span><span class="sxs-lookup"><span data-stu-id="e06ee-172">Verify that the matrix is selected on the design surface.</span></span> <span data-ttu-id="e06ee-173">“分组”窗格将显示默认的行和列组。</span><span class="sxs-lookup"><span data-stu-id="e06ee-173">The Grouping pane displays a default row and column group.</span></span>  
  
4.  <span data-ttu-id="e06ee-174">在“行组”窗格中，右键单击默认行组，再单击“编辑组”  。</span><span class="sxs-lookup"><span data-stu-id="e06ee-174">In the Row Groups pane, right-click the default row group, and then click **Edit Group**.</span></span> <span data-ttu-id="e06ee-175">此时将打开 **“组属性”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="e06ee-175">The **Group Properties** dialog box opens.</span></span>  
  
5.  <span data-ttu-id="e06ee-176">在 **“名称”** 中，用一个名称替换默认名称，该名称应指定要按其分组的多个组。</span><span class="sxs-lookup"><span data-stu-id="e06ee-176">In **Name**, replace the default name with a name that specifies the multiple groups that you want to group by.</span></span>  
  
6.  <span data-ttu-id="e06ee-177">在“组表达式”的“分组方式”中，单击表达式 (fx) 按钮，打开“表达式”对话框     。</span><span class="sxs-lookup"><span data-stu-id="e06ee-177">In **Group expressions**, in **Group on**, click the Expression (**fx**) button to open the **Expression** dialog box.</span></span>  
  
7.  <span data-ttu-id="e06ee-178">键入用于指定要按其分组的所有字段的表达式。</span><span class="sxs-lookup"><span data-stu-id="e06ee-178">Type the expression that specifies all fields that you want to group by.</span></span> <span data-ttu-id="e06ee-179">例如，以下组表达式将名为 Color 和 Size 的字段组合在一起： `=Fields!Color.Value & Fields!Size.Value`。</span><span class="sxs-lookup"><span data-stu-id="e06ee-179">For example, the following group expression combines a field named Color and a field named Size: `=Fields!Color.Value & Fields!Size.Value`.</span></span>  
  
8.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
     <span data-ttu-id="e06ee-180">此时已定义组。</span><span class="sxs-lookup"><span data-stu-id="e06ee-180">You have now defined the group.</span></span> <span data-ttu-id="e06ee-181">接下来，将要显示的字段拖到矩阵的 Tablix 正文区。</span><span class="sxs-lookup"><span data-stu-id="e06ee-181">Next, drag the fields to display to the tablix body area of the matrix.</span></span> <span data-ttu-id="e06ee-182">将第 7 步中选择的按其分组的字段添加到 Tablix 正文区，每个字段位于其各自的列中。</span><span class="sxs-lookup"><span data-stu-id="e06ee-182">Add the fields that you chose to group by in step 7 to the tablix body area, each in its own column.</span></span>  
  
     <span data-ttu-id="e06ee-183">此情况下，不需要 Tablix 行组区域中的第一个列。</span><span class="sxs-lookup"><span data-stu-id="e06ee-183">For this scenario, the first column in the tablix row groups area is not needed.</span></span> <span data-ttu-id="e06ee-184">若要删除此列，请右键单击列标题，再单击“删除列”  。</span><span class="sxs-lookup"><span data-stu-id="e06ee-184">To delete the column, right-click the column header, and then click **Delete Columns**.</span></span> <span data-ttu-id="e06ee-185">所显示的对话框将询问是否删除关联的组。</span><span class="sxs-lookup"><span data-stu-id="e06ee-185">A dialog box asks whether to delete the associated groups.</span></span> <span data-ttu-id="e06ee-186">单击 **“否”** 。</span><span class="sxs-lookup"><span data-stu-id="e06ee-186">Click **No**.</span></span> <span data-ttu-id="e06ee-187">将删除行组区域，而只保留 Tablix 正文区。</span><span class="sxs-lookup"><span data-stu-id="e06ee-187">The row group area is deleted and only the tablix body area remains.</span></span>  
  
     <span data-ttu-id="e06ee-188">接下来，将删除默认列组。</span><span class="sxs-lookup"><span data-stu-id="e06ee-188">Next, you will remove the default column group.</span></span>  
  
9. <span data-ttu-id="e06ee-189">在“列组”窗格中，右键单击默认列组，再单击“删除组”  。</span><span class="sxs-lookup"><span data-stu-id="e06ee-189">In the Column Groups pane, right-click the default column group, and then click **Delete Group**.</span></span> <span data-ttu-id="e06ee-190">将出现一个对话框，询问是要删除组以及相关的行和列，还是仅删除组。</span><span class="sxs-lookup"><span data-stu-id="e06ee-190">A dialog box asks whether to delete the group and related rows and columns or the group only.</span></span> <span data-ttu-id="e06ee-191">单击 **“仅删除组”** 。</span><span class="sxs-lookup"><span data-stu-id="e06ee-191">Click **Delete group only**.</span></span> <span data-ttu-id="e06ee-192">将删除列组，并删除列组区域。</span><span class="sxs-lookup"><span data-stu-id="e06ee-192">The column group is deleted, and the column group area is deleted.</span></span> <span data-ttu-id="e06ee-193">只保留 Tablix 正文区。</span><span class="sxs-lookup"><span data-stu-id="e06ee-193">Only the tablix body area remains.</span></span>  
  
     <span data-ttu-id="e06ee-194">接下来，需将交互式排序按钮添加到跨越矩阵的文本框。</span><span class="sxs-lookup"><span data-stu-id="e06ee-194">Next, you will add an interactive sort button to the text box that spans the matrix.</span></span>  
  
10. <span data-ttu-id="e06ee-195">单击第一行中的文本框，再单击 **“文本框属性”** 。</span><span class="sxs-lookup"><span data-stu-id="e06ee-195">Click in the text box in the first row and then click **Text Box Properties**.</span></span>  
  
11. <span data-ttu-id="e06ee-196">单击 **“交互式排序”** 。</span><span class="sxs-lookup"><span data-stu-id="e06ee-196">Click **Interactive Sorting**.</span></span>  
  
12. <span data-ttu-id="e06ee-197">选择 **“对此文本框启用交互式排序”** 。</span><span class="sxs-lookup"><span data-stu-id="e06ee-197">Select **Enable interactive sorting on this text box**.</span></span>  
  
13. <span data-ttu-id="e06ee-198">在 **“选择排序对象”** 中，单击 **“组”** 。</span><span class="sxs-lookup"><span data-stu-id="e06ee-198">In **Choose what to sort**, click **Groups**.</span></span>  
  
14. <span data-ttu-id="e06ee-199">从下拉列表中，选择在步骤 5 中创建的组的名称。</span><span class="sxs-lookup"><span data-stu-id="e06ee-199">From the drop-down list, select the name of the group you created in step 5.</span></span> <span data-ttu-id="e06ee-200">组表达式将自动复制到 **“排序依据”** 文本框。</span><span class="sxs-lookup"><span data-stu-id="e06ee-200">The group expression is automatically copied to the **Sort by** text box.</span></span>  
  
15. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
     <span data-ttu-id="e06ee-201">您已将排序按钮添加到文本框。</span><span class="sxs-lookup"><span data-stu-id="e06ee-201">You have added the sort button to the text box.</span></span>  
  
16. <span data-ttu-id="e06ee-202">（可选）还可以在显示组值的列中取消重复值。</span><span class="sxs-lookup"><span data-stu-id="e06ee-202">(Optional) You can suppress duplicate values in the columns that display group values.</span></span> <span data-ttu-id="e06ee-203">在报表设计图面上，单击用于显示要隐藏其重复值的值的文本框。</span><span class="sxs-lookup"><span data-stu-id="e06ee-203">On the report design surface, click the text box that displays the value for which you want to hide repeating values.</span></span> <span data-ttu-id="e06ee-204">在“属性”窗格中，滚动到 **HideDuplicates**，并从下拉列表中，选择链接到此矩阵的数据集的名称。</span><span class="sxs-lookup"><span data-stu-id="e06ee-204">In the Properties pane, scroll to **HideDuplicates**, and from the drop-down list, select the name of the dataset that is linked to this matrix.</span></span>  
  
 <span data-ttu-id="e06ee-205">若要验证排序操作，请单击 **“运行”** 以预览报表，然后单击交互式排序按钮。</span><span class="sxs-lookup"><span data-stu-id="e06ee-205">To verify the sort action, click **Run** to preview the report, and then click the interactive sort button.</span></span> <span data-ttu-id="e06ee-206">矩阵将按组表达式的组合值进行排序，但每个值分别显示在其各自的列中。</span><span class="sxs-lookup"><span data-stu-id="e06ee-206">The matrix sorts by the combined values of the group expression, although each individual value displays in its own column.</span></span>  
  
 <span data-ttu-id="e06ee-207">![用于“返回页首”链接的箭头图标](../../2014-toc/media/uparrow16x16.gif "用于返回页首链接的箭头图标") [返回页首](#BackToTop)</span><span class="sxs-lookup"><span data-stu-id="e06ee-207">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [Back to Top](#BackToTop)</span></span>  
  
##  <a name="synchronizing-sort-order-for-multiple-data-regions"></a><a name="SynchronizingSortOrder"></a> <span data-ttu-id="e06ee-208">同步多个数据区域的排序顺序</span><span class="sxs-lookup"><span data-stu-id="e06ee-208">Synchronizing Sort Order for Multiple Data Regions</span></span>  
 <span data-ttu-id="e06ee-209">添加交互式排序按钮，可使用户能够单击一个排序按钮并对多个数据区域进行排序。</span><span class="sxs-lookup"><span data-stu-id="e06ee-209">Add an interactive sort button that enables a user to click one sort button and sort multiple data regions.</span></span> <span data-ttu-id="e06ee-210">创建交互式排序按钮时，可以指定是否基于相同报表数据集同步多个数据区域的排序。</span><span class="sxs-lookup"><span data-stu-id="e06ee-210">When you create an interactive sort button, you can specify whether to synchronize the sort for multiple data regions based on the same report dataset.</span></span> <span data-ttu-id="e06ee-211">例如，报表可能包括以图形方式显示数据的矩阵和图表。</span><span class="sxs-lookup"><span data-stu-id="e06ee-211">For example, a report might include a matrix and a chart that graphically displays the data.</span></span> <span data-ttu-id="e06ee-212">用户更改矩阵中行的排序顺序时，图表将自动显示相同的排序顺序。</span><span class="sxs-lookup"><span data-stu-id="e06ee-212">When a user changes the sort order of the rows in the matrix, the chart automatically displays the same sort order.</span></span>  
  
 <span data-ttu-id="e06ee-213">若要同步排序顺序，必须为要排序的数据区域或组使用相同的排序表达式，并将排序的作用预定义为两个数据区域的共同祖先。</span><span class="sxs-lookup"><span data-stu-id="e06ee-213">To synchronize the sort order, you must use identical sort expressions for the data regions or groups to sort, and define the scope for the sort to be a mutual ancestor of both data regions.</span></span> <span data-ttu-id="e06ee-214">共同祖先可以是两个数据区域都链接到的数据集，也可以是两个数据区域都显示在其中的包含数据区域。</span><span class="sxs-lookup"><span data-stu-id="e06ee-214">The mutual ancestor can be either the dataset to which both data regions are linked or a containing data region within which both data regions appear.</span></span> <span data-ttu-id="e06ee-215">例如，假定一个报表同时具有显示相同数据集的数据和包含在列表中的矩阵和图表。</span><span class="sxs-lookup"><span data-stu-id="e06ee-215">For example, assume a report has both a matrix and a chart that display data from the same dataset and that are contained in a list.</span></span> <span data-ttu-id="e06ee-216">若要同步排序操作，必须对该矩阵的列指定交互式排序，并将作用域设置为该列表。</span><span class="sxs-lookup"><span data-stu-id="e06ee-216">To synchronize the sort action, you must specify the interactive sort on a column in the matrix and set the scope to the list.</span></span> <span data-ttu-id="e06ee-217">用户对矩阵进行排序时，也将对图表进行排序。</span><span class="sxs-lookup"><span data-stu-id="e06ee-217">When the user sorts the matrix, the chart is also sorted.</span></span>  
  
#### <a name="to-synchronize-sort-order-with-a-chart-for-an-interactive-sort-button-on-a-matrix-data-region"></a><span data-ttu-id="e06ee-218">将矩阵数据区域上交互式排序按钮的排序顺序与图表同步</span><span class="sxs-lookup"><span data-stu-id="e06ee-218">To synchronize sort order with a chart for an interactive sort button on a matrix data region</span></span>  
  
1.  <span data-ttu-id="e06ee-219">在报表设计视图中，向报表中添加一个矩阵。</span><span class="sxs-lookup"><span data-stu-id="e06ee-219">In report design view, add a matrix to the report.</span></span>  
  
2.  <span data-ttu-id="e06ee-220">将数值数据集字段添加到矩阵数据单元，例如，表示数量或销售额的字段。</span><span class="sxs-lookup"><span data-stu-id="e06ee-220">Add a numeric dataset field to the matrix data cell, for example, a field representing quantity or sales.</span></span>  
  
3.  <span data-ttu-id="e06ee-221">定义行组。</span><span class="sxs-lookup"><span data-stu-id="e06ee-221">Define a row group.</span></span> <span data-ttu-id="e06ee-222">默认情况下，组的排序顺序设置为与组表达式相同的表达式。</span><span class="sxs-lookup"><span data-stu-id="e06ee-222">By default, the sort order for the group is set to the same expression as the group expression.</span></span>  
  
4.  <span data-ttu-id="e06ee-223">将图表（例如饼图）添加到报表。</span><span class="sxs-lookup"><span data-stu-id="e06ee-223">Add a chart to the report, for example, a pie chart.</span></span>  
  
5.  <span data-ttu-id="e06ee-224">将步骤 2 中选择的字段拖到 **“图表数据”** 窗格的 **“值”** 区域中。</span><span class="sxs-lookup"><span data-stu-id="e06ee-224">Drag the field you chose in step 2 to the **Value** area of the **Chart Data** pane.</span></span>  
  
6.  <span data-ttu-id="e06ee-225">将选择的要按其分组的字段拖到 **“类别组”** 区域中。</span><span class="sxs-lookup"><span data-stu-id="e06ee-225">Drag the field you chose to group by to the **Category Groups** area.</span></span>  
  
     <span data-ttu-id="e06ee-226">矩阵行组和图表类别组的组表达式必须相同。</span><span class="sxs-lookup"><span data-stu-id="e06ee-226">The group expression for the matrix row group and the chart category group must be identical.</span></span>  
  
7.  <span data-ttu-id="e06ee-227">右键单击类别组，再单击“类别组属性”  。</span><span class="sxs-lookup"><span data-stu-id="e06ee-227">Right-click the category group, and then click **Category Group Properties**.</span></span>  
  
8.  <span data-ttu-id="e06ee-228">单击 **“排序”** 。</span><span class="sxs-lookup"><span data-stu-id="e06ee-228">Click **Sorting**.</span></span>  
  
9. <span data-ttu-id="e06ee-229">单击“添加”  。</span><span class="sxs-lookup"><span data-stu-id="e06ee-229">Click **Add**.</span></span> <span data-ttu-id="e06ee-230">将向排序选项网格添加一个新的排序行。</span><span class="sxs-lookup"><span data-stu-id="e06ee-230">A new sort row is added to the sorting options grid.</span></span>  
  
10. <span data-ttu-id="e06ee-231">在“排序依据”中，从下拉列表选择在步骤 6 中选择的要按其分组的相同字段。</span><span class="sxs-lookup"><span data-stu-id="e06ee-231">In Sort by, from the drop-down list, choose the same field that you chose in step 6 to group by.</span></span>  
  
11. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
12. <span data-ttu-id="e06ee-232">在矩阵中，右键单击要向其添加交互式排序按钮的列标题中的文本框，再单击“文本框属性”  。</span><span class="sxs-lookup"><span data-stu-id="e06ee-232">In the matrix, right-click the text box in the column header to which you want to add an interactive sort button, and then click **Text Box Properties**.</span></span>  
  
13. <span data-ttu-id="e06ee-233">单击 **“交互式排序”** 。</span><span class="sxs-lookup"><span data-stu-id="e06ee-233">Click **Interactive Sorting**.</span></span>  
  
14. <span data-ttu-id="e06ee-234">选择 **“对此文本框启用交互式排序”** 。</span><span class="sxs-lookup"><span data-stu-id="e06ee-234">Select **Enable interactive sorting on this text box**.</span></span>  
  
15. <span data-ttu-id="e06ee-235">在 **“选择排序对象”** 中，单击 **“组”** 。</span><span class="sxs-lookup"><span data-stu-id="e06ee-235">In **Choose what to sort**, click **Groups**.</span></span>  
  
16. <span data-ttu-id="e06ee-236">从“组”下的下拉列表中，选择要排序的组的名称  。</span><span class="sxs-lookup"><span data-stu-id="e06ee-236">From the drop-down list under **Groups**, select the name of the group that you are sorting.</span></span> <span data-ttu-id="e06ee-237">将会自动为 **“排序依据”** 值设置此组的组表达式。</span><span class="sxs-lookup"><span data-stu-id="e06ee-237">The group expression for this group is automatically set for the **Sort by** value.</span></span>  
  
17. <span data-ttu-id="e06ee-238">选择 **“同样将此排序应用于以下位置中的其他组和数据区域”** 。</span><span class="sxs-lookup"><span data-stu-id="e06ee-238">Select **Also apply this sort to other groups and data regions within**.</span></span> <span data-ttu-id="e06ee-239">在文本框中，键入数据集的名称，例如 "SalesData"。</span><span class="sxs-lookup"><span data-stu-id="e06ee-239">In the text box, type the name of the dataset, for example, "SalesData".</span></span>  
  
18. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
 <span data-ttu-id="e06ee-240">若要验证排序操作，请单击 **“运行”** 以预览报表，然后单击交互式排序按钮。</span><span class="sxs-lookup"><span data-stu-id="e06ee-240">To verify the sort action, click **Run** to preview the report, and then click the interactive sort button.</span></span> <span data-ttu-id="e06ee-241">矩阵将按组表达式的组合值进行排序，但每个值分别显示在其各自的列中。</span><span class="sxs-lookup"><span data-stu-id="e06ee-241">The matrix sorts by the combined values of the group expression, although each individual value displays in its own column.</span></span>  
  
 <span data-ttu-id="e06ee-242">![用于“返回页首”链接的箭头图标](../../2014-toc/media/uparrow16x16.gif "用于返回页首链接的箭头图标") [返回页首](#BackToTop)</span><span class="sxs-lookup"><span data-stu-id="e06ee-242">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [Back to Top](#BackToTop)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e06ee-243">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e06ee-243">See Also</span></span>  
 <span data-ttu-id="e06ee-244">[对数据进行筛选、分组和排序（报表生成器和 SSRS）](filter-group-and-sort-data-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e06ee-244">[Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="e06ee-245">[交互式排序（报表生成器和 SSRS）](interactive-sort-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e06ee-245">[Interactive Sort &#40;Report Builder and SSRS&#41;](interactive-sort-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="e06ee-246">[对数据区域中的数据进行排序（报表生成器和 SSRS）](sort-data-in-a-data-region-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e06ee-246">[Sort Data in a Data Region &#40;Report Builder and SSRS&#41;](sort-data-in-a-data-region-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="e06ee-247">利用 Tablix 数据区域的灵活性（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="e06ee-247">Exploring the Flexibility of a Tablix Data Region &#40;Report Builder and SSRS&#41;</span></span>](exploring-the-flexibility-of-a-tablix-data-region-report-builder-and-ssrs.md)  
  
  
