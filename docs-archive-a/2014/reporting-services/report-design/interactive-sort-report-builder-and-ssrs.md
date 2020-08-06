---
title: 交互式排序（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 00cafed5-1a3c-4ce0-a1fb-ff1e2613f495
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 92f8a63ebd3d16c84dc12bb4a08549efa91e949a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692709"
---
# <a name="interactive-sort-report-builder-and-ssrs"></a><span data-ttu-id="ea0f4-102">交互式排序（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="ea0f4-102">Interactive Sort (Report Builder and SSRS)</span></span>
  <span data-ttu-id="ea0f4-103">对于表中的行或矩阵中的行和列，可以添加交互式排序按钮，以便用户能够在升序和降序顺序之间切换。</span><span class="sxs-lookup"><span data-stu-id="ea0f4-103">You can add interactive sort buttons to enable a user to toggle between ascending and descending order for rows in a table or for rows and columns in a matrix.</span></span> <span data-ttu-id="ea0f4-104">交互式排序最常见的用途是向每一个列标题添加一个排序按钮。</span><span class="sxs-lookup"><span data-stu-id="ea0f4-104">The most common use of interactive sort is to add a sort button to every column header.</span></span> <span data-ttu-id="ea0f4-105">这样，用户就可以选择要按哪个列排序。</span><span class="sxs-lookup"><span data-stu-id="ea0f4-105">The user can then choose which column to sort by.</span></span>  
  
 <span data-ttu-id="ea0f4-106">但是，您不仅可以向列标题添加交互式排序按钮，还可以向任何文本框添加这种按钮。</span><span class="sxs-lookup"><span data-stu-id="ea0f4-106">However, you can add an interactive sort button to any text box, not just column headers.</span></span> <span data-ttu-id="ea0f4-107">例如，对于行组外部的行中的文本框，可以为父组行或列、为子组行或列或者为详细信息行或列指定排序。</span><span class="sxs-lookup"><span data-stu-id="ea0f4-107">For example, for a text box in a row outside a row group, you can specify a sort for the parent group rows or columns, for child group rows or columns, or for the detail rows or columns.</span></span> <span data-ttu-id="ea0f4-108">还可以将多个字段组合成单个组表达式，然后按多个字段排序。</span><span class="sxs-lookup"><span data-stu-id="ea0f4-108">You can also combine fields into a single group expression, and then sort by multiple fields.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
 <span data-ttu-id="ea0f4-109">添加交互式排序时，必须指定以下项：</span><span class="sxs-lookup"><span data-stu-id="ea0f4-109">When you add an interactive sort, you must specify the following items:</span></span>  
  
-   <span data-ttu-id="ea0f4-110">**排序对象：** 是对行还是对列进行排序？</span><span class="sxs-lookup"><span data-stu-id="ea0f4-110">**What to sort:** Rows or columns?</span></span>  
  
-   <span data-ttu-id="ea0f4-111">**排序依据：** 是依据表列中显示的某一字段？</span><span class="sxs-lookup"><span data-stu-id="ea0f4-111">**What to sort by:** A field that is displayed in a table column?</span></span> <span data-ttu-id="ea0f4-112">还是依据未显示的某一字段？</span><span class="sxs-lookup"><span data-stu-id="ea0f4-112">A field that is not displayed?</span></span>  
  
-   <span data-ttu-id="ea0f4-113">**排序上下文：** 例如，可以在与行组关联的行、与列组关联的列、详细信息行、父组内的子组中进行排序，或者同时在父组和子组中进行排序。</span><span class="sxs-lookup"><span data-stu-id="ea0f4-113">**What context to sort in:** For example, you can sort on rows associated with row groups; columns associated with column groups; detail rows; child groups within a parent group; or parent and child group together.</span></span>  
  
-   <span data-ttu-id="ea0f4-114">**要将排序按钮添加到的文本框：** 是添加到列标题中还是添加到组行标题中？</span><span class="sxs-lookup"><span data-stu-id="ea0f4-114">**Which text box to add the sort button to:** In the column header or in the group row header?</span></span>  
  
-   <span data-ttu-id="ea0f4-115">**是否对多个数据区域同步排序：** 可以设计一个报表，使得在用户切换排序顺序时具有同一祖先的其他数据区域也进行排序。</span><span class="sxs-lookup"><span data-stu-id="ea0f4-115">**Whether to synchronize the sort for multiple data regions:** You can design a report so that when the user toggles the sort order, other data regions with the same ancestor also sort.</span></span>  
  
 <span data-ttu-id="ea0f4-116">有关分步说明，请参阅 [将交互式排序添加到表或矩阵（报表生成器和 SSRS）](add-interactive-sort-to-a-table-or-matrix-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="ea0f4-116">For step-by-step instructions, see [Add Interactive Sort to a Table or Matrix &#40;Report Builder and SSRS&#41;](add-interactive-sort-to-a-table-or-matrix-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="ea0f4-117">下表总结了通过使用交互式排序按钮可以取得的效果。</span><span class="sxs-lookup"><span data-stu-id="ea0f4-117">The following table summarizes the effects you can achieve by using interactive sort buttons.</span></span>  
  
|<span data-ttu-id="ea0f4-118">操作</span><span class="sxs-lookup"><span data-stu-id="ea0f4-118">Action</span></span>|<span data-ttu-id="ea0f4-119">排序对象</span><span class="sxs-lookup"><span data-stu-id="ea0f4-119">What to sort</span></span>|<span data-ttu-id="ea0f4-120">要将排序按钮添加到的位置</span><span class="sxs-lookup"><span data-stu-id="ea0f4-120">Where to add the sort button</span></span>|<span data-ttu-id="ea0f4-121">排序依据</span><span class="sxs-lookup"><span data-stu-id="ea0f4-121">What to sort on</span></span>|<span data-ttu-id="ea0f4-122">排序范围</span><span class="sxs-lookup"><span data-stu-id="ea0f4-122">Sort scope</span></span>|  
|------------|------------------|----------------------------------|---------------------|----------------|  
|<span data-ttu-id="ea0f4-123">对没有组的表的详细信息行进行排序</span><span class="sxs-lookup"><span data-stu-id="ea0f4-123">Sort detail rows for a table with no groups</span></span>|<span data-ttu-id="ea0f4-124">详细信息</span><span class="sxs-lookup"><span data-stu-id="ea0f4-124">Details</span></span>|<span data-ttu-id="ea0f4-125">列标题</span><span class="sxs-lookup"><span data-stu-id="ea0f4-125">Column header</span></span>|<span data-ttu-id="ea0f4-126">绑定到此列的数据集字段</span><span class="sxs-lookup"><span data-stu-id="ea0f4-126">Dataset field bound to this column</span></span>|<span data-ttu-id="ea0f4-127">数据区域</span><span class="sxs-lookup"><span data-stu-id="ea0f4-127">Data region</span></span>|  
|<span data-ttu-id="ea0f4-128">对矩阵的顶级组实例进行排序</span><span class="sxs-lookup"><span data-stu-id="ea0f4-128">Sort top-level group instances for a matrix</span></span>|<span data-ttu-id="ea0f4-129">组</span><span class="sxs-lookup"><span data-stu-id="ea0f4-129">Groups</span></span>|<span data-ttu-id="ea0f4-130">列标题</span><span class="sxs-lookup"><span data-stu-id="ea0f4-130">Column header</span></span>|<span data-ttu-id="ea0f4-131">父组的组表达式</span><span class="sxs-lookup"><span data-stu-id="ea0f4-131">Group expression for parent group</span></span>|<span data-ttu-id="ea0f4-132">数据区域</span><span class="sxs-lookup"><span data-stu-id="ea0f4-132">Data region</span></span>|  
|<span data-ttu-id="ea0f4-133">对表中子组的详细信息行进行排序</span><span class="sxs-lookup"><span data-stu-id="ea0f4-133">Sort detail rows for a child group in a table</span></span>|<span data-ttu-id="ea0f4-134">详细信息</span><span class="sxs-lookup"><span data-stu-id="ea0f4-134">Details</span></span>|<span data-ttu-id="ea0f4-135">子组的标题行</span><span class="sxs-lookup"><span data-stu-id="ea0f4-135">Child group header row</span></span>|<span data-ttu-id="ea0f4-136">要作为排序依据的数据集字段</span><span class="sxs-lookup"><span data-stu-id="ea0f4-136">Dataset field to sort by</span></span>|<span data-ttu-id="ea0f4-137">子组</span><span class="sxs-lookup"><span data-stu-id="ea0f4-137">Child group</span></span>|  
|<span data-ttu-id="ea0f4-138">对表中的多个行组的行以及详细信息行进行排序</span><span class="sxs-lookup"><span data-stu-id="ea0f4-138">Sort rows for multiple row groups and detail rows in a table</span></span>|<span data-ttu-id="ea0f4-139">组，但您必须重新定义组表达式</span><span class="sxs-lookup"><span data-stu-id="ea0f4-139">Groups, but you must redefine the group expression</span></span>|<span data-ttu-id="ea0f4-140">列标题</span><span class="sxs-lookup"><span data-stu-id="ea0f4-140">Column header</span></span>|<span data-ttu-id="ea0f4-141">要作为排序依据的数据集字段的聚合</span><span class="sxs-lookup"><span data-stu-id="ea0f4-141">Aggregate of dataset field to sort by</span></span>|<span data-ttu-id="ea0f4-142">数据区域</span><span class="sxs-lookup"><span data-stu-id="ea0f4-142">Data region</span></span>|  
|<span data-ttu-id="ea0f4-143">对多个数据区域同步排序顺序</span><span class="sxs-lookup"><span data-stu-id="ea0f4-143">Synchronize the sort order for multiple data regions</span></span>|<span data-ttu-id="ea0f4-144">组</span><span class="sxs-lookup"><span data-stu-id="ea0f4-144">Groups</span></span>|<span data-ttu-id="ea0f4-145">通常是列标题</span><span class="sxs-lookup"><span data-stu-id="ea0f4-145">Typically, column header</span></span>|<span data-ttu-id="ea0f4-146">组表达式</span><span class="sxs-lookup"><span data-stu-id="ea0f4-146">Group expression</span></span>|<span data-ttu-id="ea0f4-147">数据集</span><span class="sxs-lookup"><span data-stu-id="ea0f4-147">Dataset</span></span>|  
  
 <span data-ttu-id="ea0f4-148">在应用所有数据区域和组排序表达式后，报表处理器会应用交互式排序。</span><span class="sxs-lookup"><span data-stu-id="ea0f4-148">The report processor applies interactive sort after all data region and group sort expressions are applied.</span></span> <span data-ttu-id="ea0f4-149">有关详细信息，请参阅 [对数据进行筛选、分组和排序（报表生成器和 SSRS）](filter-group-and-sort-data-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="ea0f4-149">For more information, see [Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md).</span></span>  
  
## <a name="adding-interactive-sort-for-multiple-groups"></a><span data-ttu-id="ea0f4-150">为多个组添加交互式排序</span><span class="sxs-lookup"><span data-stu-id="ea0f4-150">Adding Interactive Sort for Multiple Groups</span></span>  
 <span data-ttu-id="ea0f4-151">如果一个表具有嵌套的行组，且每个行组都基于单个数据集字段，则可以在该表中添加对父组值、子组值或详细信息行进行排序的交互式排序按钮。</span><span class="sxs-lookup"><span data-stu-id="ea0f4-151">In a table with nested row groups each based on a single dataset field, you can add an interactive sort button that sorts parent group values, child group values, or detail rows.</span></span> <span data-ttu-id="ea0f4-152">但是，您可能需要向用户提供这样的功能：无需多次单击，即可同时按父组值和子组值对表进行排序。</span><span class="sxs-lookup"><span data-stu-id="ea0f4-152">However, you might want to provide the user with the ability to sort the table by both the parent and child group values without having to click multiple times.</span></span>  
  
 <span data-ttu-id="ea0f4-153">为此，您必须重新设计该表，以按组合了多个字段的表达式进行分组。</span><span class="sxs-lookup"><span data-stu-id="ea0f4-153">To do this, you must redesign the table to group on an expression that combines multiple fields.</span></span> <span data-ttu-id="ea0f4-154">例如，对于包含库存计数的数据集，如果原始表先按大小、再按颜色进行分组，则您可以使用由大小和颜色组合而成的组表达式指定单个组。</span><span class="sxs-lookup"><span data-stu-id="ea0f4-154">For example, for a dataset with inventory counts, if the original table grouped by size and then by color, you can specify a single group with a group expression that is a combination of size and color.</span></span> <span data-ttu-id="ea0f4-155">有关详细信息，请参阅 [将交互式排序添加到表或矩阵（报表生成器和 SSRS）](add-interactive-sort-to-a-table-or-matrix-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="ea0f4-155">For more information, see [Add Interactive Sort to a Table or Matrix &#40;Report Builder and SSRS&#41;](add-interactive-sort-to-a-table-or-matrix-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea0f4-156">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ea0f4-156">See Also</span></span>  
 <span data-ttu-id="ea0f4-157">[对数据区域中的数据进行排序（报表生成器和 SSRS）](sort-data-in-a-data-region-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ea0f4-157">[Sort Data in a Data Region &#40;Report Builder and SSRS&#41;](sort-data-in-a-data-region-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="ea0f4-158">[对数据进行筛选、分组和排序（报表生成器和 SSRS）](filter-group-and-sort-data-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ea0f4-158">[Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="ea0f4-159">将交互式排序添加到表或矩阵（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="ea0f4-159">Add Interactive Sort to a Table or Matrix &#40;Report Builder and SSRS&#41;</span></span>](add-interactive-sort-to-a-table-or-matrix-report-builder-and-ssrs.md)  
  
  
