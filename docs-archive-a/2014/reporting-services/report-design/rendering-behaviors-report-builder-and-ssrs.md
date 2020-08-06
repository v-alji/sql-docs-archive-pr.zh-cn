---
title: 呈现行为（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 8f873ef9-27a3-40e5-b58b-6774f8027a58
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1d6a6aa91c547f4739b172f9303ac9e61bde5771
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691610"
---
# <a name="rendering-behaviors-report-builder--and-ssrs"></a><span data-ttu-id="a8e37-102">呈现行为（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="a8e37-102">Rendering Behaviors (Report Builder  and SSRS)</span></span>
  <span data-ttu-id="a8e37-103">根据选择的呈现器，呈现报表时，将针对表体及其内容应用特定的规则。</span><span class="sxs-lookup"><span data-stu-id="a8e37-103">Depending on the renderer you select, certain rules are applied to the report body and its contents when rendering a report.</span></span> <span data-ttu-id="a8e37-104">报表项在页面上的呈现方式由以下因素综合确定：</span><span class="sxs-lookup"><span data-stu-id="a8e37-104">How report items fit together on a page is determined by the combination of these factors:</span></span>  
  
-   <span data-ttu-id="a8e37-105">呈现规则。</span><span class="sxs-lookup"><span data-stu-id="a8e37-105">Rendering rules.</span></span>  
  
-   <span data-ttu-id="a8e37-106">报表项的高度和宽度。</span><span class="sxs-lookup"><span data-stu-id="a8e37-106">The width and height of report items.</span></span>  
  
-   <span data-ttu-id="a8e37-107">表体的大小。</span><span class="sxs-lookup"><span data-stu-id="a8e37-107">The size of the report body.</span></span>  
  
-   <span data-ttu-id="a8e37-108">页面的高度和宽度。</span><span class="sxs-lookup"><span data-stu-id="a8e37-108">The width and height of the page.</span></span>  
  
-   <span data-ttu-id="a8e37-109">特定于呈现器的分页支持。</span><span class="sxs-lookup"><span data-stu-id="a8e37-109">Renderer-specific support for paging.</span></span>  
  
 <span data-ttu-id="a8e37-110">本主题讨论 Reporting Services 所应用的一般规则。</span><span class="sxs-lookup"><span data-stu-id="a8e37-110">This topic discusses the general rules that are applied by Reporting Services.</span></span> <span data-ttu-id="a8e37-111">有关详细信息，请参阅[呈现报表项（报表生成器和 SSRS）](rendering-report-items-report-builder-and-ssrs.md)、[呈现数据区域（报表生成器和 SSRS）](rendering-data-regions-report-builder-and-ssrs.md)和[呈现数据（报表生成器和 SSRS）](rendering-data-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="a8e37-111">For more information, see [Rendering Report Items &#40;Report Builder and SSRS&#41;](rendering-report-items-report-builder-and-ssrs.md), [Rendering Data Regions &#40;Report Builder and SSRS&#41;](rendering-data-regions-report-builder-and-ssrs.md), and [Rendering Data &#40;Report Builder and SSRS&#41;](rendering-data-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="general-behaviors-for-html-mhtml-word-and-excel-soft-page-break-renderers"></a><span data-ttu-id="a8e37-112">HTML、MHTML、Word 和 Excel（软分页呈现器）的一般行为</span><span class="sxs-lookup"><span data-stu-id="a8e37-112">General Behaviors for HTML, MHTML, Word, and Excel (Soft Page-Break Renderers)</span></span>  
 <span data-ttu-id="a8e37-113">使用 HTML 和 MHTML 格式导出的报表针对基于计算机屏幕的体验进行了优化，其中的页面可以是各种长度。</span><span class="sxs-lookup"><span data-stu-id="a8e37-113">Reports exported using HTML and MHTML formats are optimized for a computer screen-based experience where pages can be various lengths.</span></span> <span data-ttu-id="a8e37-114">仅在表体内的近似位置垂直插入分页符。</span><span class="sxs-lookup"><span data-stu-id="a8e37-114">Page breaks are inserted vertically only at approximate locations within the report body.</span></span> <span data-ttu-id="a8e37-115">这些近似位置由“属性”窗格中的交互高度设置来确定。</span><span class="sxs-lookup"><span data-stu-id="a8e37-115">These approximate locations are determined by the interactive height setting in the Properties pane.</span></span> <span data-ttu-id="a8e37-116">例如，假定交互高度设置为 5 英寸。</span><span class="sxs-lookup"><span data-stu-id="a8e37-116">For example, suppose the interactive height is set to 5 inches.</span></span> <span data-ttu-id="a8e37-117">呈现报表时，页面高度大约为 5 英寸长。</span><span class="sxs-lookup"><span data-stu-id="a8e37-117">When the report is rendered, the page height is approximately 5 inches in length.</span></span> <span data-ttu-id="a8e37-118">Word 和 Excel 基于逻辑分页符进行分页，并且忽略交互高度设置。</span><span class="sxs-lookup"><span data-stu-id="a8e37-118">Word and Excel paginate based on logical page breaks and ignore the interactive height setting.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a8e37-119">若要确定报表如何在软分页呈现器中显示，请使用报表预览。</span><span class="sxs-lookup"><span data-stu-id="a8e37-119">To determine how a report will appear in a soft page-break renderer, use Report Preview.</span></span> <span data-ttu-id="a8e37-120">报表的显示方式与在 HTML、MHTML、Word 或 Excel 格式中的显示方式相同。</span><span class="sxs-lookup"><span data-stu-id="a8e37-120">The report appears as it would in a HTML, MHTML, Word, or Excel format.</span></span>  
  
 <span data-ttu-id="a8e37-121">将报表导出到 HTML、MHTML、Word 或 Excel 时，应遵循下述一般规则：</span><span class="sxs-lookup"><span data-stu-id="a8e37-121">When exporting a report to HTML, MHTML, Word, or Excel, the following general rules are followed:</span></span>  
  
-   <span data-ttu-id="a8e37-122">逻辑分页符（显式插入的分页符）应用于报表项。</span><span class="sxs-lookup"><span data-stu-id="a8e37-122">Logical page breaks, the page breaks that you explicitly insert, are applied to report items.</span></span> <span data-ttu-id="a8e37-123">例如，如果在每个组之间插入一个分页符，则在呈现报表时将应用这些分页符。</span><span class="sxs-lookup"><span data-stu-id="a8e37-123">For example, if you insert a page break between each group, they are applied when the report is rendered.</span></span>  
  
-   <span data-ttu-id="a8e37-124">通过使用页面高度和报表项显示的次数，可创建一个近似布局。</span><span class="sxs-lookup"><span data-stu-id="a8e37-124">An approximate layout is created using the page height and the number of times that the report item appears.</span></span> <span data-ttu-id="a8e37-125">例如，如果文本框的高度为 0.5 英寸并在报表中重复 5 次，则会保留 2.5 英寸。</span><span class="sxs-lookup"><span data-stu-id="a8e37-125">For example, if a text box is .5 inches in height and repeats five times in the report, 2.5 inches are reserved.</span></span>  
  
-   <span data-ttu-id="a8e37-126">根据交互高度的设置，可以插入多个软分页符。</span><span class="sxs-lookup"><span data-stu-id="a8e37-126">Multiple soft page breaks are inserted based on the interactive height setting.</span></span> <span data-ttu-id="a8e37-127">若要在 HTML 和 ReportViewer 控件中取消软分页符，并仅使用显式分页符控制分页，请将 **interactive height** 值设置为 0 或一个极大的数。</span><span class="sxs-lookup"><span data-stu-id="a8e37-127">To suppress in HTML and the ReportViewer controls, and control pagination only with explicit page breaks, set the **interactive height** value to 0 or an extremely large number.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a8e37-128">交互宽度设置不用于软分页呈现器。</span><span class="sxs-lookup"><span data-stu-id="a8e37-128">The interactive width setting is not used in the soft page break renderers.</span></span>  
  
-   <span data-ttu-id="a8e37-129">报表页可以增大以容纳需要显示在一起的末行、孤立行和报表项。</span><span class="sxs-lookup"><span data-stu-id="a8e37-129">Report pages can grow to accommodate widows, orphans and report items that need to be kept together.</span></span> <span data-ttu-id="a8e37-130">也就是说，报表可以扩展到屏幕宽度之外，并可使用滑动条来查看。</span><span class="sxs-lookup"><span data-stu-id="a8e37-130">This means that the report can extend beyond the screen width and can be viewed by using slider bars.</span></span>  
  
-   <span data-ttu-id="a8e37-131">分页仅垂直应用于报表。</span><span class="sxs-lookup"><span data-stu-id="a8e37-131">Pagination is applied to reports vertically only.</span></span>  
  
-   <span data-ttu-id="a8e37-132">不应用页边距。</span><span class="sxs-lookup"><span data-stu-id="a8e37-132">Page margins are not applied.</span></span>  
  
## <a name="general-behaviors-for-pdf-image-and-print-hard-page-break-renderers"></a><span data-ttu-id="a8e37-133">PDF、图像和打印（硬分页呈现器）的一般行为</span><span class="sxs-lookup"><span data-stu-id="a8e37-133">General Behaviors for PDF, Image, and Print (Hard Page-Break Renderers)</span></span>  
 <span data-ttu-id="a8e37-134">使用 PDF 和图像导出的报表针对书状或打印体验进行了优化，其中的页面大小保持一致。</span><span class="sxs-lookup"><span data-stu-id="a8e37-134">Reports exported using PDF and Image are optimized for a book-like or printed experience where pages are a consistent size.</span></span> <span data-ttu-id="a8e37-135">在表体内的特定位置垂直和水平插入分页符。</span><span class="sxs-lookup"><span data-stu-id="a8e37-135">Page breaks are inserted vertically and horizontally at specific locations within the report body.</span></span> <span data-ttu-id="a8e37-136">这些特定位置由页面宽度和页面高度设置来确定。</span><span class="sxs-lookup"><span data-stu-id="a8e37-136">These specific locations are determined by the page width and page height settings.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a8e37-137">若要确定报表如何在硬分页呈现器中显示，请使用打印预览。</span><span class="sxs-lookup"><span data-stu-id="a8e37-137">To determine how a report will appear in a hard page-break renderer, use Print Preview.</span></span> <span data-ttu-id="a8e37-138">报表的显示方式与在 PDF 或图像格式中的显示方式相同。</span><span class="sxs-lookup"><span data-stu-id="a8e37-138">The report appears as it would in a PDF or Image format.</span></span>  
  
-   <span data-ttu-id="a8e37-139">页的编号顺序是从左到右，然后再从上到下。</span><span class="sxs-lookup"><span data-stu-id="a8e37-139">Pages are numbered sequentially from left to right, then top to bottom.</span></span>  
  
-   <span data-ttu-id="a8e37-140">逻辑分页符（显式插入的分页符）应用于报表项。</span><span class="sxs-lookup"><span data-stu-id="a8e37-140">Logical page breaks, the page breaks that you explicitly insert, are applied to report items.</span></span> <span data-ttu-id="a8e37-141">这些分页符会导致报表项将其他项推到下一页。</span><span class="sxs-lookup"><span data-stu-id="a8e37-141">These page breaks can cause report items to push other items to the next page.</span></span>  
  
-   <span data-ttu-id="a8e37-142">如果物理分页符出现在必须显示在一起的报表项中，则必须显示在一起的项将移至下一页。</span><span class="sxs-lookup"><span data-stu-id="a8e37-142">If a physical page break occurs through report items that must be kept together, the items that must be kept together are moved to the next page.</span></span>  
  
-   <span data-ttu-id="a8e37-143">由于页面大小的约束，可能无法将所有项显示在一起或重复项。</span><span class="sxs-lookup"><span data-stu-id="a8e37-143">Because of page size constraints, it may not be possible to keep all the items together or to repeat items.</span></span> <span data-ttu-id="a8e37-144">如果发生这种情况，呈现器可能忽略重复另一项的某些规则，以便允许报表项适合页面。</span><span class="sxs-lookup"><span data-stu-id="a8e37-144">If that occurs, the renderer might ignore certain rules for repeating with another item in order to allow the report item to fit on the page.</span></span>  
  
-   <span data-ttu-id="a8e37-145">如果项无法显示在一起（例如文本框太大无法适合垂直的可用页面区域），则该项将在物理页边界处剪掉并继续显示在下一页中。</span><span class="sxs-lookup"><span data-stu-id="a8e37-145">If an item cannot be kept together, for example a text box that grows too large to fit within the vertical usable page area, then the item will be clipped at the physical page boundary and will continue on the next page.</span></span>  
  
-   <span data-ttu-id="a8e37-146">分页可垂直和水平应用于报表。</span><span class="sxs-lookup"><span data-stu-id="a8e37-146">Pagination is applied to reports vertically and horizontally.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a8e37-147">交互宽度设置不用于硬分页呈现器。</span><span class="sxs-lookup"><span data-stu-id="a8e37-147">The interactive width setting is not used in the hard page break renderers.</span></span>  
  
## <a name="minimum-spacing-between-report-items"></a><span data-ttu-id="a8e37-148">报表项间的最小间距</span><span class="sxs-lookup"><span data-stu-id="a8e37-148">Minimum Spacing Between Report Items</span></span>  
 <span data-ttu-id="a8e37-149">报表项可以在表体内增大以容纳其内容。</span><span class="sxs-lookup"><span data-stu-id="a8e37-149">Report items grow within the report body to accommodate their contents.</span></span> <span data-ttu-id="a8e37-150">例如，呈现报表时，矩阵数据区域通常在页面内向下扩展，并且文本框的高度可随表达式返回的数据进行调整。</span><span class="sxs-lookup"><span data-stu-id="a8e37-150">For example, a matrix data region typically expands across and down the page when the report is rendered, and the height of a text box adjusts depending on the data returned from an expression.</span></span>  
  
 <span data-ttu-id="a8e37-151">呈现器会在报表项间保留一个最小的间距，该间距在报表布局中定义。</span><span class="sxs-lookup"><span data-stu-id="a8e37-151">Renderers maintain the minimum space between report items that you define in the report layout.</span></span> <span data-ttu-id="a8e37-152">在报表布局上将报表项相邻放置时，报表项间的距离在报表水平或垂直增长时将变成必须保持的最小距离。</span><span class="sxs-lookup"><span data-stu-id="a8e37-152">When you place a report item adjacent to another on the report layout, the distance between the report items becomes the minimum distance that must be maintained as the report grows horizontally or vertically.</span></span> <span data-ttu-id="a8e37-153">例如，如果您向报表添加一个矩阵数据区域，然后在矩阵的右侧 0.25 英寸处添加一个矩形，则在矩阵增长时将保持最小间距。</span><span class="sxs-lookup"><span data-stu-id="a8e37-153">For example, if you add a matrix data region to a report and then add a rectangle .25 inches to the right of the matrix, that space is maintained as the matrix grows.</span></span> <span data-ttu-id="a8e37-154">每个项向右移动以便与其左侧的项之间保持最小距离。</span><span class="sxs-lookup"><span data-stu-id="a8e37-154">Each item moves to the right to maintain the minimum distance from items that end to the left of it.</span></span>  
  
## <a name="page-headers-and-footers"></a><span data-ttu-id="a8e37-155">页眉和页脚</span><span class="sxs-lookup"><span data-stu-id="a8e37-155">Page Headers and Footers</span></span>  
 <span data-ttu-id="a8e37-156">页眉和页脚显示在每个呈现的页面的顶部和底部。</span><span class="sxs-lookup"><span data-stu-id="a8e37-156">Page headers and footers appear at the top and bottom of each rendered page.</span></span> <span data-ttu-id="a8e37-157">您可以设置页眉和页脚的格式，使其具有边框颜色、边框样式和边框宽度。</span><span class="sxs-lookup"><span data-stu-id="a8e37-157">You can format the page header and footer so that there is a border color, border style, and border width.</span></span> <span data-ttu-id="a8e37-158">此外，还可以添加背景色或背景图像。</span><span class="sxs-lookup"><span data-stu-id="a8e37-158">You can also add a background color or background image.</span></span> <span data-ttu-id="a8e37-159">根据所选格式，这些格式选项都会呈现出来。</span><span class="sxs-lookup"><span data-stu-id="a8e37-159">These formatting options are all rendered, depending on the format that you choose.</span></span>  
  
 <span data-ttu-id="a8e37-160">以 HTML 或 MHTML 呈现格式呈现时，以下规则适用于页眉和页脚：</span><span class="sxs-lookup"><span data-stu-id="a8e37-160">The following rules apply to page headers and footers when rendered in the HTML or MHTML rendering format:</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a8e37-161">有关 Excel 如何呈现页眉和页脚的信息，请参阅[导出到 Microsoft Excel（报表生成器和 SSRS）](../report-builder/exporting-to-microsoft-excel-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="a8e37-161">For information about how Excel renders headers and footers, see [Exporting to Microsoft Excel &#40;Report Builder and SSRS&#41;](../report-builder/exporting-to-microsoft-excel-report-builder-and-ssrs.md).</span></span> <span data-ttu-id="a8e37-162">有关 Word 如何呈现页眉和页脚的信息，请参阅[导出到 Microsoft Word（报表生成器和 SSRS）](../report-builder/exporting-to-microsoft-word-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="a8e37-162">For information about how Word renders headers and footers, see [Exporting to Microsoft Word &#40;Report Builder and SSRS&#41;](../report-builder/exporting-to-microsoft-word-report-builder-and-ssrs.md).</span></span>  
  
-   <span data-ttu-id="a8e37-163">显示时，页眉和页脚分别呈现在可用页面区域内每一页的顶部和底部。</span><span class="sxs-lookup"><span data-stu-id="a8e37-163">When present, the header and footer is rendered at the top and bottom of every page within the usable page area.</span></span>  
  
-   <span data-ttu-id="a8e37-164">在页眉或页脚隐藏的页面上，即使不呈现页眉或页脚，可用页面区域内仍然保留页眉或页脚的高度。</span><span class="sxs-lookup"><span data-stu-id="a8e37-164">On pages where the header or footer is hidden, the height of the header or footer is still reserved within the usable page area, even though the header or footer is not rendered.</span></span>  
  
-   <span data-ttu-id="a8e37-165">如果页眉或页脚的内容增长到页眉或页脚的边界之外，则页眉或页脚的大小会增大以容纳这些内容。</span><span class="sxs-lookup"><span data-stu-id="a8e37-165">If the contents of the header or footer grows beyond the boundaries of the header or footer, the header or footer increases in size to accommodate the contents.</span></span>  
  
 <span data-ttu-id="a8e37-166">以 PDF 或图像呈现格式呈现时，以下规则适用于页眉和页脚：</span><span class="sxs-lookup"><span data-stu-id="a8e37-166">The following rules apply to page headers and footers when rendered in the PDF or Image rendering format:</span></span>  
  
-   <span data-ttu-id="a8e37-167">页眉或页脚分别呈现在可用页面区域内每一页的顶部和底部。</span><span class="sxs-lookup"><span data-stu-id="a8e37-167">The header or footer is rendered at the top and bottom of every page within the usable page area.</span></span>  
  
-   <span data-ttu-id="a8e37-168">在页眉或页脚隐藏的页面上，即使不呈现页眉或页脚，可用页面区域内仍然保留页眉或页脚的高度。</span><span class="sxs-lookup"><span data-stu-id="a8e37-168">On pages where the header or footer is hidden, the height of the header or footer is still reserved within the usable page area, even though the header or footer is not rendered.</span></span>  
  
-   <span data-ttu-id="a8e37-169">页眉和页脚不会增长，也不会缩减。</span><span class="sxs-lookup"><span data-stu-id="a8e37-169">The header and footer do not grow or shrink.</span></span> <span data-ttu-id="a8e37-170">它们呈现在每一页上创建页眉或页脚时指定的高度处。</span><span class="sxs-lookup"><span data-stu-id="a8e37-170">They are rendered on every page at the height specified when you created the header or footer.</span></span>  
  
-   <span data-ttu-id="a8e37-171">不论报表内的列数如何，每一页只有一个页眉和页脚。</span><span class="sxs-lookup"><span data-stu-id="a8e37-171">Regardless of the number of columns within the report, there is only one header and footer per page.</span></span>  
  
-   <span data-ttu-id="a8e37-172">如果页眉或页脚的内容增长到页眉或页脚的边界之外，将截断其内容。</span><span class="sxs-lookup"><span data-stu-id="a8e37-172">If the contents of the header or footer grow beyond the boundaries of the header or footer, the contents are clipped.</span></span>  
  
-   <span data-ttu-id="a8e37-173">当报表呈现为子报表时，在原始 RDL 文件中定义的表头和表尾不会呈现出来。</span><span class="sxs-lookup"><span data-stu-id="a8e37-173">Headers and footers that are defined in the original RDL file are not rendered when the report is rendered as a subreport.</span></span>  
  
## <a name="logical-page-breaks"></a><span data-ttu-id="a8e37-174">逻辑分页符</span><span class="sxs-lookup"><span data-stu-id="a8e37-174">Logical Page Breaks</span></span>  
 <span data-ttu-id="a8e37-175">逻辑分页符是在报表项或组之前或之后插入的分页符。</span><span class="sxs-lookup"><span data-stu-id="a8e37-175">Logical page breaks are page breaks that you insert before or after report items or groups.</span></span> <span data-ttu-id="a8e37-176">分页符有助于确定报表内容适合报表页的方式，以便在呈现或导出报表时获得最佳查看效果。</span><span class="sxs-lookup"><span data-stu-id="a8e37-176">Page breaks help to determine how the content is fitted to a report page for optimal viewing when rendering or exporting the report.</span></span>  
  
 <span data-ttu-id="a8e37-177">呈现逻辑分页符时应用以下规则：</span><span class="sxs-lookup"><span data-stu-id="a8e37-177">The following rules apply when rendering logical page breaks:</span></span>  
  
-   <span data-ttu-id="a8e37-178">对于持续隐藏的报表项以及通过单击其他报表项来控制可见性的报表项，将忽略逻辑分页符。</span><span class="sxs-lookup"><span data-stu-id="a8e37-178">Logical page breaks are ignored for report items that are constantly hidden and for report items where the visibility is controlled by clicking another report item.</span></span>  
  
-   <span data-ttu-id="a8e37-179">如果按条件可见的项在报表呈现时可见，则逻辑分页符应用于这些项。</span><span class="sxs-lookup"><span data-stu-id="a8e37-179">Logical page breaks are applied on conditionally visible items if they are currently visible at the time the report is rendered.</span></span>  
  
-   <span data-ttu-id="a8e37-180">在具有逻辑分页符的报表项与对等报表项之间保留有间距。</span><span class="sxs-lookup"><span data-stu-id="a8e37-180">Space is preserved between the report item with the logical page break and its peer report items.</span></span>  
  
-   <span data-ttu-id="a8e37-181">在报表项之前插入的逻辑分页符将报表项向下推至下一页。</span><span class="sxs-lookup"><span data-stu-id="a8e37-181">Logical page breaks that are inserted before a report item push the report item down to the next page.</span></span> <span data-ttu-id="a8e37-182">该报表项将呈现在下一页的顶部。</span><span class="sxs-lookup"><span data-stu-id="a8e37-182">The report item is rendered at the top of the next page.</span></span>  
  
-   <span data-ttu-id="a8e37-183">对表或矩阵单元中的项定义的逻辑分页符将不保留。</span><span class="sxs-lookup"><span data-stu-id="a8e37-183">Logical page breaks defined on items in table or matrix cells are not kept.</span></span> <span data-ttu-id="a8e37-184">此逻辑分页符将不应用于列表中的项。</span><span class="sxs-lookup"><span data-stu-id="a8e37-184">This does not apply to items in lists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8e37-185">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a8e37-185">See Also</span></span>  
 <span data-ttu-id="a8e37-186">[不同报表呈现扩展插件的交互功能（报表生成器和 SSRS）](../report-builder/interactive-functionality-different-report-rendering-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="a8e37-186">[Interactive Functionality for Different Report Rendering Extensions &#40;Report Builder and SSRS&#41;](../report-builder/interactive-functionality-different-report-rendering-extensions.md) </span></span>  
 <span data-ttu-id="a8e37-187">[以 HTML 格式呈现（报表生成器和 SSRS）](../report-builder/rendering-to-html-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a8e37-187">[Rendering to HTML &#40;Report Builder and SSRS&#41;](../report-builder/rendering-to-html-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="a8e37-188">页面布局和呈现方式（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="a8e37-188">Page Layout and Rendering &#40;Report Builder and SSRS&#41;</span></span>](page-layout-and-rendering-report-builder-and-ssrs.md)  
  
  
