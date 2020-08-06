---
title: 与组一起显示组头和组尾（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 8eb7d648-4df2-491a-96cb-99e55629d617
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: adbb3674a16fc77d04ac3ac490a284894588c657
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586436"
---
# <a name="display-headers-and-footers-with-a-group-report-builder-and-ssrs"></a><span data-ttu-id="5225a-102">与组一起显示组头和组尾（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="5225a-102">Display Headers and Footers with a Group (Report Builder and SSRS)</span></span>
  <span data-ttu-id="5225a-103">您可以帮助控制是否在显示与 Tablix 数据区域中某个组相关联的动态行的同时显示静态行，如组头或组尾。</span><span class="sxs-lookup"><span data-stu-id="5225a-103">You can help control whether a static row, such as a group header or footer, renders with dynamic rows that are associated with a group in a tablix data region.</span></span>  
  
 <span data-ttu-id="5225a-104">若要在多个页上重复所有列标题或行标题，可以设置 Tablix 数据区域的属性。</span><span class="sxs-lookup"><span data-stu-id="5225a-104">To repeat all the column headings or row headings on multiple pages, you can set properties for the tablix data region.</span></span> <span data-ttu-id="5225a-105">有关详细信息，请参阅[在多个页中显示行标题和列标题（报表生成器和 SSRS）](display-row-and-column-headers-on-multiple-pages-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="5225a-105">For more information, see [Display Row and Column Headers on Multiple Pages &#40;Report Builder and SSRS&#41;](display-row-and-column-headers-on-multiple-pages-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="5225a-106">若要控制与嵌套组相关联的动态行和列的呈现行为，或者与标签或小计相关联的静态行和列的呈现行为，必须设置 Tablix 成员的属性。</span><span class="sxs-lookup"><span data-stu-id="5225a-106">To control the rendering behavior for dynamic rows and columns that are associated with nested groups, or for static rows and columns that are associated with labels or subtotals, you must set properties for the tablix member.</span></span> <span data-ttu-id="5225a-107">一个 Tablix 成员表示一个静态或动态的行或列。</span><span class="sxs-lookup"><span data-stu-id="5225a-107">A tablix member represents a static or dynamic row or column.</span></span> <span data-ttu-id="5225a-108">每个静态成员重复一次。</span><span class="sxs-lookup"><span data-stu-id="5225a-108">A static member repeats once.</span></span> <span data-ttu-id="5225a-109">例如，总计行就是一个静态行。</span><span class="sxs-lookup"><span data-stu-id="5225a-109">For example, a grand total row is a static row.</span></span> <span data-ttu-id="5225a-110">一个动态成员针对每个组实例重复一次。</span><span class="sxs-lookup"><span data-stu-id="5225a-110">A dynamic member repeats once for each group instance.</span></span> <span data-ttu-id="5225a-111">例如，一个与具有组表达式 [Territory] 的组相关联的行针对每个唯一地区值重复一次。</span><span class="sxs-lookup"><span data-stu-id="5225a-111">For example, a row that is associated with a group that has the group expression [Territory] repeats once for each unique value for territory.</span></span> <span data-ttu-id="5225a-112">有关 Tablix 成员的详细信息，请参阅 [Tablix 数据区域单元、行和列（报表生成器和 SSRS）](tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="5225a-112">For more information about tablix members, see [Tablix Data Region Cells, Rows, and Columns &#40;Report Builder&#41; and SSRS](tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="5225a-113">可以在“分组”窗格中选择 Tablix 成员，并在“属性”窗格中设置 **KeepWithGroup**、 **KeepTogether**和 **RepeatOnNewPage** 属性。</span><span class="sxs-lookup"><span data-stu-id="5225a-113">You can select a tablix member in the Grouping pane and set the properties **KeepWithGroup**, **KeepTogether**, and **RepeatOnNewPage** in the Properties pane.</span></span> <span data-ttu-id="5225a-114">使用 **KeepWithGroup** 可帮助将组头和组尾与组显示在相同页上。</span><span class="sxs-lookup"><span data-stu-id="5225a-114">Use **KeepWithGroup** to help display group headers and footers on the same page as the group.</span></span> <span data-ttu-id="5225a-115">使用 **KeepTogether** 可帮助将静态成员与组的行或列显示在一起。</span><span class="sxs-lookup"><span data-stu-id="5225a-115">Use **KeepTogether** to help display static members with the rows or columns of a group.</span></span> <span data-ttu-id="5225a-116">使用 **RepeatOnNewPage** 可在以下页上重复显示组头和组尾：其中的每一页至少显示 **KeepWithGroup** 值所指定的行组成员的一个完整实例。</span><span class="sxs-lookup"><span data-stu-id="5225a-116">Use **RepeatOnNewPage** to repeat the group header or footer on every page that displays at least one complete instance of the row group member designated by the **KeepWithGroup** value.</span></span> <span data-ttu-id="5225a-117">列组成员不支持**RepeatOnNewPage** 。</span><span class="sxs-lookup"><span data-stu-id="5225a-117">**RepeatOnNewPage** is not supported for column group members.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5225a-118">KeepWithGroup、KeepTogether和 RepeatOnNewPage 是可通过使用“分组”窗格的“高级模式”设置的组成员属性     。</span><span class="sxs-lookup"><span data-stu-id="5225a-118">**KeepWithGroup**, **KeepTogether**, and **RepeatOnNewPage** are group member properties that you can set by using the **Advanced Mode** of the Grouping pane.</span></span> <span data-ttu-id="5225a-119">有关详细信息，请参阅[“分组”窗格（报表生成器）](grouping-pane-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="5225a-119">For more information, see [Grouping Pane &#40;Report Builder&#41;](grouping-pane-report-builder.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-keep-a-static-row-with-a-set-of-dynamic-rows-associated-with-a-row-group"></a><span data-ttu-id="5225a-120">使静态行和一组与行组关联的动态行一起显示</span><span class="sxs-lookup"><span data-stu-id="5225a-120">To keep a static row with a set of dynamic rows associated with a row group</span></span>  
  
1.  <span data-ttu-id="5225a-121">在设计图面上，单击 Tablix 数据区域中的任意位置以将其选定。</span><span class="sxs-lookup"><span data-stu-id="5225a-121">On the design surface, click anywhere in the tablix data region to select it.</span></span> <span data-ttu-id="5225a-122">“分组”窗格将显示数据区域的行组和列组。</span><span class="sxs-lookup"><span data-stu-id="5225a-122">The Grouping pane displays the row and column groups for the data region.</span></span>  
  
2.  <span data-ttu-id="5225a-123">在“分组”窗格的右侧，单击下箭头，然后单击 **“高级模式”** 。</span><span class="sxs-lookup"><span data-stu-id="5225a-123">On the right side of the Grouping pane, click the down arrow, and then click **Advanced Mode**.</span></span> <span data-ttu-id="5225a-124">“行组”窗格显示行组层次结构的分层静态和动态成员。</span><span class="sxs-lookup"><span data-stu-id="5225a-124">The Row Groups pane displays the hierarchical static and dynamic members for the row groups hierarchy.</span></span>  
  
3.  <span data-ttu-id="5225a-125">单击要与组行一起显示的组头或组尾行所对应的静态成员。</span><span class="sxs-lookup"><span data-stu-id="5225a-125">Click the static member that corresponds to the row header or footer that you want to keep with the group rows.</span></span> <span data-ttu-id="5225a-126">“属性”窗格显示 **“Tablix 成员”** 属性。</span><span class="sxs-lookup"><span data-stu-id="5225a-126">The Properties pane displays the **Tablix Member** properties.</span></span>  
  
4.  <span data-ttu-id="5225a-127">在“属性”窗格中，单击 **KeepWithGroup**，然后从下拉列表选择以下值之一：</span><span class="sxs-lookup"><span data-stu-id="5225a-127">In the Properties pane, click **KeepWithGroup**, and then choose one of the following values from the drop-down list:</span></span>  
  
    -   <span data-ttu-id="5225a-128">**无** 选择该选项表示没有指定使该成员与所选行组成员一起显示的首选项。</span><span class="sxs-lookup"><span data-stu-id="5225a-128">**None** Select this option to indicate no preference for keeping this member with the members of the selected row group.</span></span>  
  
    -   <span data-ttu-id="5225a-129">**前面** 选择该选项可以使该成员与上一组的成员一起显示。</span><span class="sxs-lookup"><span data-stu-id="5225a-129">**Before** Select this option to keep this member with the members of the previous group.</span></span> <span data-ttu-id="5225a-130">您可能会对组尾行使用此值。</span><span class="sxs-lookup"><span data-stu-id="5225a-130">You might use this for group footer rows.</span></span>  
  
    -   <span data-ttu-id="5225a-131">**后面** 选择该选项可以使该成员与下一组的成员一起显示。</span><span class="sxs-lookup"><span data-stu-id="5225a-131">**After** Select this option to keep this member with the members of the following group.</span></span> <span data-ttu-id="5225a-132">您可能会对组头行使用此值。</span><span class="sxs-lookup"><span data-stu-id="5225a-132">You might use this for group header rows.</span></span>  
  
5.  <span data-ttu-id="5225a-133">（可选）预览报表。</span><span class="sxs-lookup"><span data-stu-id="5225a-133">(Optional) Preview the report.</span></span> <span data-ttu-id="5225a-134">如果可能，报表呈现器使该成员与指定行组成员一起显示。</span><span class="sxs-lookup"><span data-stu-id="5225a-134">Where possible, the report renderer keeps this member with the specified row group members.</span></span>  
  
### <a name="to-keep-a-static-column-with-a-set-of-dynamic-columns-associated-with-a-column-group"></a><span data-ttu-id="5225a-135">使静态列和一组与列组关联的动态列一起显示</span><span class="sxs-lookup"><span data-stu-id="5225a-135">To keep a static column with a set of dynamic columns associated with a column group</span></span>  
  
1.  <span data-ttu-id="5225a-136">在设计图面上，单击 Tablix 数据区域中的任意位置以将其选定。</span><span class="sxs-lookup"><span data-stu-id="5225a-136">On the design surface, click anywhere in the tablix data region to select it.</span></span> <span data-ttu-id="5225a-137">“分组”窗格将显示数据区域的行组和列组。</span><span class="sxs-lookup"><span data-stu-id="5225a-137">The Grouping pane displays the row and column groups for the data region.</span></span>  
  
2.  <span data-ttu-id="5225a-138">在“分组”窗格的右侧，单击下箭头，然后单击 **“高级模式”** 。</span><span class="sxs-lookup"><span data-stu-id="5225a-138">On the right side of the Grouping pane, click the down arrow, and then click **Advanced Mode**.</span></span> <span data-ttu-id="5225a-139">“列组”窗格显示列组层次结构的分层静态和动态成员。</span><span class="sxs-lookup"><span data-stu-id="5225a-139">The Column Groups pane displays the hierarchical static and dynamic members for the column group hierarchy.</span></span>  
  
3.  <span data-ttu-id="5225a-140">单击要与组列一起显示的静态列所对应的静态成员。</span><span class="sxs-lookup"><span data-stu-id="5225a-140">Click the static member that corresponds to the static column that you want to keep with the group columns.</span></span> <span data-ttu-id="5225a-141">“属性”窗格显示 **“Tablix 成员”** 属性。</span><span class="sxs-lookup"><span data-stu-id="5225a-141">The Properties pane displays the **Tablix Member** properties.</span></span>  
  
4.  <span data-ttu-id="5225a-142">在“属性”窗格中，单击 **KeepWithGroup**，然后从下拉列表选择以下值之一：</span><span class="sxs-lookup"><span data-stu-id="5225a-142">In the Properties pane, click **KeepWithGroup**, and then choose one of the following values from the drop-down list:</span></span>  
  
    -   <span data-ttu-id="5225a-143">**无** 选择该选项表示没有指定使该成员与所选列组成员一起显示的首选项。</span><span class="sxs-lookup"><span data-stu-id="5225a-143">**None** Select this option to indicate no preference for keeping this member with the members of the selected column group.</span></span>  
  
    -   <span data-ttu-id="5225a-144">**前面** 选择该选项可以使该成员与上一组的成员一起显示。</span><span class="sxs-lookup"><span data-stu-id="5225a-144">**Before** Select this option to keep this member with the members of the previous group.</span></span> <span data-ttu-id="5225a-145">您可能会对在指定列组成员之前显示的列标签使用此值。</span><span class="sxs-lookup"><span data-stu-id="5225a-145">You might use this for column labels that display before the specified column group members.</span></span>  
  
    -   <span data-ttu-id="5225a-146">**后面** 选择该选项可以使该成员与下一组的成员一起显示。</span><span class="sxs-lookup"><span data-stu-id="5225a-146">**After** Select this option to keep this member with the members of the following group.</span></span> <span data-ttu-id="5225a-147">您可能会对在指定列组成员之后显示的列总计使用此值。</span><span class="sxs-lookup"><span data-stu-id="5225a-147">You might use this for column totals that display after the specified column group members.</span></span>  
  
5.  <span data-ttu-id="5225a-148">（可选）预览报表。</span><span class="sxs-lookup"><span data-stu-id="5225a-148">(Optional) Preview the report.</span></span> <span data-ttu-id="5225a-149">如果可能，报表呈现器使该成员与指定列组成员一起显示。</span><span class="sxs-lookup"><span data-stu-id="5225a-149">Where possible, the report renderer keeps this member with the specified column group members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5225a-150">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5225a-150">See Also</span></span>  
 <span data-ttu-id="5225a-151">[Tablix 数据区域单元、行和列 &#40;报表生成器&#41; 和 SSRS](tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="5225a-151">[Tablix Data Region Cells, Rows, and Columns &#40;Report Builder&#41; and SSRS](tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="5225a-152">[Tablix 数据区域区 &#40;报表生成器和 SSRS&#41;](tablix-data-region-areas-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="5225a-152">[Tablix Data Region Areas &#40;Report Builder and SSRS&#41;](tablix-data-region-areas-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="5225a-153">[Tablix 数据区域 &#40;报表生成器和 SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="5225a-153">[Tablix Data Region &#40;Report Builder and SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="5225a-154">[表 &#40;报表生成器和 SSRS&#41;](tables-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="5225a-154">[Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="5225a-155">[矩阵 &#40;报表生成器和 SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="5225a-155">[Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="5225a-156">[列出 &#40;报表生成器和 SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="5225a-156">[Lists &#40;Report Builder and SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="5225a-157">表、矩阵和列表（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="5225a-157">Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;</span></span>](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
