---
title: 呈现报表项（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 99ebb4dc-41cc-42ac-82dd-a2b0e31155a0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f4e0b1dabee096cfbaab53227926633f8d7a3697
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586429"
---
# <a name="rendering-report-items-report-builder-and-ssrs"></a><span data-ttu-id="4ecfb-102">呈现报表项（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="4ecfb-102">Rendering Report Items (Report Builder and SSRS)</span></span>
  <span data-ttu-id="4ecfb-103">报表项的数量、大小和位置会影响呈现器对表体的分页方式。</span><span class="sxs-lookup"><span data-stu-id="4ecfb-103">The number, size, and location of report items affect how the renderers paginate the report body.</span></span> <span data-ttu-id="4ecfb-104">下面说明了各种报表项的呈现方式。</span><span class="sxs-lookup"><span data-stu-id="4ecfb-104">Below is a description of how various report items are rendered.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="overlapping-report-items"></a><span data-ttu-id="4ecfb-105">重叠报表项</span><span class="sxs-lookup"><span data-stu-id="4ecfb-105">Overlapping Report Items</span></span>  
 <span data-ttu-id="4ecfb-106">在 HTML、MHTML、Word、Excel、预览模式或报表查看器中不支持重叠报表项。</span><span class="sxs-lookup"><span data-stu-id="4ecfb-106">Overlapping report items are not supported in HTML, MHTML, Word, Excel, in Preview, or the Report Viewer.</span></span> <span data-ttu-id="4ecfb-107">如果存在重叠项，则会移动它们。</span><span class="sxs-lookup"><span data-stu-id="4ecfb-107">If overlapping items exist, they are moved.</span></span> <span data-ttu-id="4ecfb-108">以下规则应用于重叠报表项：</span><span class="sxs-lookup"><span data-stu-id="4ecfb-108">The following rules are applied to overlapping report items:</span></span>  
  
-   <span data-ttu-id="4ecfb-109">如果报表项的垂直重叠较多，则其中一个重叠项将向右移动。</span><span class="sxs-lookup"><span data-stu-id="4ecfb-109">If the vertical overlap of report items is greater, one of the overlapping items is moved to the right.</span></span> <span data-ttu-id="4ecfb-110">最左侧的项保持在原位置。</span><span class="sxs-lookup"><span data-stu-id="4ecfb-110">The left-most item remains where it is positioned.</span></span>  
  
-   <span data-ttu-id="4ecfb-111">如果报表项的水平重叠较多，则其中一个重叠项将向下移动。</span><span class="sxs-lookup"><span data-stu-id="4ecfb-111">If the horizontal overlap of report items is greater, one of the overlapping items is moved down.</span></span> <span data-ttu-id="4ecfb-112">最顶端的项保持在原位置。</span><span class="sxs-lookup"><span data-stu-id="4ecfb-112">The top-most item remains where it is positioned.</span></span>  
  
-   <span data-ttu-id="4ecfb-113">如果垂直重叠和水平重叠相同，则其中一个重叠项将向右移动。</span><span class="sxs-lookup"><span data-stu-id="4ecfb-113">If the vertical and horizontal overlap is equal, one of the overlapping items is moved to the right.</span></span> <span data-ttu-id="4ecfb-114">最左侧的项保持在原位置。</span><span class="sxs-lookup"><span data-stu-id="4ecfb-114">The left-most item remains where it is positioned.</span></span>  
  
-   <span data-ttu-id="4ecfb-115">如果必须将某项移至正确的重叠，则相邻报表项将向下和/或向右移动，以在该项与其上方和/或左侧的报表项之间保持最小间距。</span><span class="sxs-lookup"><span data-stu-id="4ecfb-115">If an item must be moved to correct overlapping, adjacent report items move down and/or to the right to maintain a minimum amount of spacing between the item and the report items that end above it and/or to the left of it.</span></span> <span data-ttu-id="4ecfb-116">例如，假定两个报表项垂直重叠，并且第三个报表项位于这两项右侧 2 英寸处。</span><span class="sxs-lookup"><span data-stu-id="4ecfb-116">For example, suppose two report items overlap vertically and a third report item is 2 inches to the right of them.</span></span> <span data-ttu-id="4ecfb-117">将重叠的报表项向右移动时，第三个报表项也会向右移动，以在其自身与其左侧的报表项之间保持 2 英寸距离。</span><span class="sxs-lookup"><span data-stu-id="4ecfb-117">When the overlapping report item is moved to the right, the third report item moves to the right as well in order to maintain the 2 inches between itself and the report item to its left.</span></span>  
  
 <span data-ttu-id="4ecfb-118">硬分页格式（包括打印）支持重叠报表项。</span><span class="sxs-lookup"><span data-stu-id="4ecfb-118">Overlapping report items are supported in hard page-break formats, including print.</span></span>  
  
## <a name="visibility-and-report-items"></a><span data-ttu-id="4ecfb-119">可见性与报表项</span><span class="sxs-lookup"><span data-stu-id="4ecfb-119">Visibility and Report Items</span></span>  
 <span data-ttu-id="4ecfb-120">默认情况下可以隐藏或显示报表项，也可以使用表达式按条件隐藏或显示报表项。</span><span class="sxs-lookup"><span data-stu-id="4ecfb-120">Report items can be hidden or displayed by default, or hidden or displayed conditionally using expressions.</span></span> <span data-ttu-id="4ecfb-121">或者，可以通过单击其他报表项来切换可见性。</span><span class="sxs-lookup"><span data-stu-id="4ecfb-121">Optionally, the visibility can be switched by clicking another report item.</span></span>  
  
 <span data-ttu-id="4ecfb-122">呈现报表项时应用下列可见性规则：</span><span class="sxs-lookup"><span data-stu-id="4ecfb-122">The following visibility rules apply when rendering report items:</span></span>  
  
-   <span data-ttu-id="4ecfb-123">如果报表项及其内容始终隐藏（不是基于表达式隐藏或不能通过单击其他报表项来切换其可见性），则其右侧或下方的其他报表项不会移动来填充空白区域。</span><span class="sxs-lookup"><span data-stu-id="4ecfb-123">If a report item and its contents are always hidden (it is not hidden based on an expression or its visibility cannot be switched by clicking another report item), then other report items to the right or below it do not move to fill the empty space.</span></span> <span data-ttu-id="4ecfb-124">例如，如果矩形及其内包含的图像隐藏，则始于矩形右侧的报表项不会向左移动来填充空白区域。</span><span class="sxs-lookup"><span data-stu-id="4ecfb-124">For example, if a rectangle and the image contained within it are hidden, the report item that starts to the right of the rectangle does not move to the left to fill what appears to be empty space.</span></span> <span data-ttu-id="4ecfb-125">矩形所占的空间将被保留。</span><span class="sxs-lookup"><span data-stu-id="4ecfb-125">The space occupied by the rectangle is preserved.</span></span>  
  
-   <span data-ttu-id="4ecfb-126">如果报表项及其内容按条件隐藏（基于表达式隐藏或通过单击其他报表项来切换其可见性），则其右侧或下方的报表项将向左移动来填充项隐藏时的空间。</span><span class="sxs-lookup"><span data-stu-id="4ecfb-126">If a report item and its contents are hidden conditionally (it is hidden based on an expression or its visibility is switched by clicking another report item), then report items to the right or below it move to the left to fill in the space when the item is hidden.</span></span>  
  
-   <span data-ttu-id="4ecfb-127">如果可通过单击其他报表项来切换报表项及其内容的可见性，则仅当报表项最初显示时，才会更改分页来容纳该报表项及其内容。</span><span class="sxs-lookup"><span data-stu-id="4ecfb-127">If the visibility of a report item and its contents can be switched by clicking another report item, then pagination changes to accommodate the report item and its contents only when it is initially displayed.</span></span>  
  
## <a name="keeping-report-items-together-on-a-single-page"></a><span data-ttu-id="4ecfb-128">将报表项显示在一页中</span><span class="sxs-lookup"><span data-stu-id="4ecfb-128">Keeping Report Items Together on a Single Page</span></span>  
 <span data-ttu-id="4ecfb-129">通过设置分组显示或显示在一起属性，可以显式或隐式地将报表内的许多报表项显示在一页中。</span><span class="sxs-lookup"><span data-stu-id="4ecfb-129">Many report items within a report can be kept together on a single page implicitly or explicitly by setting the keep with group or keep together properties.</span></span> <span data-ttu-id="4ecfb-130">如果报表项没有任何逻辑分页符并且其大小小于可用页面区域，则报表项始终会呈现在同一页中。</span><span class="sxs-lookup"><span data-stu-id="4ecfb-130">Report items are always rendered on the same page if the report item does not have any logical page breaks and is smaller in size than the usable page area.</span></span> <span data-ttu-id="4ecfb-131">如果报表项不能完全适合以通常方式开始的页面，则会在报表项之前插入硬分页符，强制将其显示在下一页。</span><span class="sxs-lookup"><span data-stu-id="4ecfb-131">If a report item does not fit completely on the page on which it would usually start, a hard page break is inserted before the report item, forcing it to the next page.</span></span> <span data-ttu-id="4ecfb-132">对于软分页符呈现器，页面会增大以容纳该报表项。</span><span class="sxs-lookup"><span data-stu-id="4ecfb-132">For soft page-break renderers, the page grows to accommodate the report item.</span></span>  
  
 <span data-ttu-id="4ecfb-133">当报表项始终隐藏时，将忽略将项显示在一起的规则。</span><span class="sxs-lookup"><span data-stu-id="4ecfb-133">When the report item is always hidden, the rules for keeping items together are ignored.</span></span>  
  
 <span data-ttu-id="4ecfb-134">以下项将始终显示在一起：</span><span class="sxs-lookup"><span data-stu-id="4ecfb-134">The following items are always kept together:</span></span>  
  
-   <span data-ttu-id="4ecfb-135">图像。</span><span class="sxs-lookup"><span data-stu-id="4ecfb-135">Images.</span></span>  
  
-   <span data-ttu-id="4ecfb-136">线条：</span><span class="sxs-lookup"><span data-stu-id="4ecfb-136">Lines.</span></span>  
  
-   <span data-ttu-id="4ecfb-137">图表、仪表和结构图。</span><span class="sxs-lookup"><span data-stu-id="4ecfb-137">Charts, gauges, and maps.</span></span>  
  
-   <span data-ttu-id="4ecfb-138">单独显示在另一页中的数据区域中的一行，选中分组显示选项。</span><span class="sxs-lookup"><span data-stu-id="4ecfb-138">A single row in a data region that appears separately on another page, by selecting the keep with group option.</span></span> <span data-ttu-id="4ecfb-139">这样会隐式将这一行与至少一个组实例显示在一起，以便不会使这一行孤立。</span><span class="sxs-lookup"><span data-stu-id="4ecfb-139">This will implicitly keep together the single row with at least one instance of the group so that the row is not orphaned.</span></span> <span data-ttu-id="4ecfb-140">可以在数据区域或组中设置此选项。</span><span class="sxs-lookup"><span data-stu-id="4ecfb-140">You can set this option on a data region or a group.</span></span>  
  
-   <span data-ttu-id="4ecfb-141">数据区域的标题区域。</span><span class="sxs-lookup"><span data-stu-id="4ecfb-141">Header area of a data region.</span></span>  
  
-   <span data-ttu-id="4ecfb-142">数据区域的标题区域和第一行数据。</span><span class="sxs-lookup"><span data-stu-id="4ecfb-142">Header area of a data region and the first row of data.</span></span>  
  
-   <span data-ttu-id="4ecfb-143">可在 Tablix 数据区域中切换的报表项。</span><span class="sxs-lookup"><span data-stu-id="4ecfb-143">Report items that can be toggled in a tablix data region.</span></span>  
  
### <a name="priority-order"></a><span data-ttu-id="4ecfb-144">优先级顺序</span><span class="sxs-lookup"><span data-stu-id="4ecfb-144">Priority Order</span></span>  
 <span data-ttu-id="4ecfb-145">由于页面大小的限制，在将报表项显示在一起的规则之间可能会发生冲突。</span><span class="sxs-lookup"><span data-stu-id="4ecfb-145">Due to page size limitations, conflicts can arise between the rules for keeping report items together.</span></span> <span data-ttu-id="4ecfb-146">发生冲突时，以下优先级顺序用于在呈现时将项显示在一起：</span><span class="sxs-lookup"><span data-stu-id="4ecfb-146">When conflicts occur, the following priority order is used to keep items together when rendering:</span></span>  
  
-   <span data-ttu-id="4ecfb-147">线条、图表和图像。</span><span class="sxs-lookup"><span data-stu-id="4ecfb-147">Lines, charts, and images.</span></span>  
  
-   <span data-ttu-id="4ecfb-148">末行和孤立行控件。</span><span class="sxs-lookup"><span data-stu-id="4ecfb-148">Widow and orphan control.</span></span>  
  
-   <span data-ttu-id="4ecfb-149">重复的列标题和行标题。</span><span class="sxs-lookup"><span data-stu-id="4ecfb-149">Repeated column headers and row headers.</span></span>  
  
     <span data-ttu-id="4ecfb-150">表头优先于表尾。</span><span class="sxs-lookup"><span data-stu-id="4ecfb-150">Headers take precedence over footers.</span></span> <span data-ttu-id="4ecfb-151">内部重复的组优先于外部组。</span><span class="sxs-lookup"><span data-stu-id="4ecfb-151">Inner repeated groups have priority over outer groups.</span></span> <span data-ttu-id="4ecfb-152">如果项设置了 `RepeatWith` 属性且距离目标数据区域较近，则这些项优先于距离数据区域较远的项。</span><span class="sxs-lookup"><span data-stu-id="4ecfb-152">Items where the `RepeatWith` property is set that are closer to the target data region have priority over items that are farther away from the data region.</span></span>  
  
-   <span data-ttu-id="4ecfb-153">小报表项（例如文本框或矩形），其显式保持的属性设置为 `true` 。</span><span class="sxs-lookup"><span data-stu-id="4ecfb-153">Small report items, such as text boxes or rectangles, with an explicit KeepTogether property set to `true`.</span></span>  
  
-   <span data-ttu-id="4ecfb-154">大型报表项（例如子报表或非最内部的 tablix 成员），其显式保持的属性设置为 `true` 。</span><span class="sxs-lookup"><span data-stu-id="4ecfb-154">Large report items, such as subreports or a non-innermost tablix member, with an explicit KeepTogether property set to `true`.</span></span>  
  
-   <span data-ttu-id="4ecfb-155">Tablix 数据区域，其显式保持和属性均设置为 `true` 。</span><span class="sxs-lookup"><span data-stu-id="4ecfb-155">Tablix data regions with an explicit KeepTogether property set to `true`.</span></span>  
  
### <a name="subreports"></a><span data-ttu-id="4ecfb-156">子报表</span><span class="sxs-lookup"><span data-stu-id="4ecfb-156">Subreports</span></span>  
 <span data-ttu-id="4ecfb-157">子报表呈现为一个包含在单独的报表 .rdl 文件中定义的另一报表的矩形。</span><span class="sxs-lookup"><span data-stu-id="4ecfb-157">A subreport renders as a rectangle that contains another report that is defined in a separate report .rdl file.</span></span> <span data-ttu-id="4ecfb-158">子报表文件必须先发布到报表服务器，之后才能由父报表进行访问。</span><span class="sxs-lookup"><span data-stu-id="4ecfb-158">The subreport file must be published to a report server before it can be accessed by the parent report.</span></span>  
  
 <span data-ttu-id="4ecfb-159">呈现子报表时应用以下规则：</span><span class="sxs-lookup"><span data-stu-id="4ecfb-159">The following rules apply when rendering subreports:</span></span>  
  
-   <span data-ttu-id="4ecfb-160">子报表可以增大至在定义子报表的 .rdl 文件中定义的表体大小。</span><span class="sxs-lookup"><span data-stu-id="4ecfb-160">Subreports can grow to the size of the body defined in the .rdl file that defines the subreport.</span></span> <span data-ttu-id="4ecfb-161">例如，如果子报表的 RDL 指明子报表表体的宽度为 5 英寸，则子报表在父报表内的宽度也将为 5 英寸。</span><span class="sxs-lookup"><span data-stu-id="4ecfb-161">For example, if the RDL for the subreport states that the subreport body is 5 inches wide, then the subreport will be 5 inches wide within the parent report.</span></span>  
  
-   <span data-ttu-id="4ecfb-162">子报表将继承父报表的列设置。</span><span class="sxs-lookup"><span data-stu-id="4ecfb-162">Subreports inherit column settings from the parent report.</span></span> <span data-ttu-id="4ecfb-163">会始终忽略原始 RDL 中定义的列设置。</span><span class="sxs-lookup"><span data-stu-id="4ecfb-163">Column settings that are defined in the original RDL are always ignored.</span></span>  
  
-   <span data-ttu-id="4ecfb-164">将只呈现子报表的表体。</span><span class="sxs-lookup"><span data-stu-id="4ecfb-164">Only the body of the subreport is rendered.</span></span> <span data-ttu-id="4ecfb-165">当子报表呈现在父报表中时，将不呈现子报表的 .rdl 文件中定义的表头和表尾部分。</span><span class="sxs-lookup"><span data-stu-id="4ecfb-165">Header and footer sections that are defined in the subreport's .rdl file are not rendered when the subreport is rendered in the parent report.</span></span>  
  
-   <span data-ttu-id="4ecfb-166">子报表具有显式 KeepTogether 属性。</span><span class="sxs-lookup"><span data-stu-id="4ecfb-166">Subreports have an explicit KeepTogether property.</span></span> <span data-ttu-id="4ecfb-167">当该属性设置为 `true` 时，如有可能，子报表中的所有项都将显示在一页中。</span><span class="sxs-lookup"><span data-stu-id="4ecfb-167">When it is set to `true`, all the items in the subreport are kept together on one page when possible.</span></span>  
  
-   <span data-ttu-id="4ecfb-168">如果子报表无法运行，则会在报表中显示为一个带有错误消息的文本框。</span><span class="sxs-lookup"><span data-stu-id="4ecfb-168">If a subreport cannot run, it is displayed in the report as a text box with an error message.</span></span> <span data-ttu-id="4ecfb-169">应用于子报表的样式属性将改为应用于该文本框。</span><span class="sxs-lookup"><span data-stu-id="4ecfb-169">The style properties applied to the subreport are applied to the text box instead.</span></span>  
  
-   <span data-ttu-id="4ecfb-170">如果子报表由分页符拆分开，则 **“去掉分页符上的边框”** 设置将控制子报表的边框是关闭还是打开。</span><span class="sxs-lookup"><span data-stu-id="4ecfb-170">If the subreport is split by a page break, the **Omit border on page break** setting controls whether or not the borders on the subreport are closed or open.</span></span>  
  
 <span data-ttu-id="4ecfb-171">有关子报表的详细信息，请参阅[子报表（报表生成器和 SSRS）](subreports-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="4ecfb-171">For more information about subreports, see [Subreports &#40;Report Builder and SSRS&#41;](subreports-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ecfb-172">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4ecfb-172">See Also</span></span>  
 <span data-ttu-id="4ecfb-173">[Reporting Services 中的分页（报表生成器和 SSRS）](pagination-in-reporting-services-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4ecfb-173">[Pagination in Reporting Services &#40;Report Builder  and SSRS&#41;](pagination-in-reporting-services-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="4ecfb-174">[呈现行为（报表生成器和 SSRS）](rendering-behaviors-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4ecfb-174">[Rendering Behaviors &#40;Report Builder  and SSRS&#41;](rendering-behaviors-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="4ecfb-175">[不同报表呈现扩展插件的交互功能（报表生成器和 SSRS）](../report-builder/interactive-functionality-different-report-rendering-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="4ecfb-175">[Interactive Functionality for Different Report Rendering Extensions &#40;Report Builder and SSRS&#41;](../report-builder/interactive-functionality-different-report-rendering-extensions.md) </span></span>  
 [<span data-ttu-id="4ecfb-176">列表（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="4ecfb-176">Lists &#40;Report Builder and SSRS&#41;</span></span>](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
