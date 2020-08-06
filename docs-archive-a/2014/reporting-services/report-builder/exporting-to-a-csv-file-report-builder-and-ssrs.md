---
title: 导出到 CSV 文件（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 68ec746e-8c82-47f5-8c3d-dbe403a441e5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 635d5904acf6e616378f5423bfbaf4cf5390fa9e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577355"
---
# <a name="exporting-to-a-csv-file-report-builder-and-ssrs"></a><span data-ttu-id="dd092-102">导出到 CSV 文件（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="dd092-102">Exporting to a CSV File (Report Builder and SSRS)</span></span>
  <span data-ttu-id="dd092-103">逗号分隔值 (CSV) 呈现扩展插件以平展的表示形式呈现报表中的数据，格式为标准化的纯文本，这种数据表示形式容易读取且可与多个应用程序交换。</span><span class="sxs-lookup"><span data-stu-id="dd092-103">The Comma-Separated Value (CSV) rendering extension renders reports as a flattened representation of data from a report in a standardized, plain-text format that is easily readable and exchangeable with many applications.</span></span>  
  
 <span data-ttu-id="dd092-104">CSV 呈现扩展插件使用字符串分隔符来分隔字段和行，字符串分隔符可以配置为逗号之外的其他字符。</span><span class="sxs-lookup"><span data-stu-id="dd092-104">The CSV rendering extension uses a string character delimiter to separate fields and rows, with the string character delimiter configurable to be a character other than a comma.</span></span> <span data-ttu-id="dd092-105">生成的文件可以用电子表格程序（如 [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] ）打开，也可以用作其他程序的导入格式。</span><span class="sxs-lookup"><span data-stu-id="dd092-105">The resulting file can be opened in a spreadsheet program like [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] or used as an import format for other programs.</span></span> <span data-ttu-id="dd092-106">所导出的报表会变为 .csv 文件，并返回 MIME 类型的 `text/csv`。</span><span class="sxs-lookup"><span data-stu-id="dd092-106">The exported report becomes a .csv file, and returns a MIME type of `text/csv`.</span></span>  
  
 <span data-ttu-id="dd092-107">如果您想要在 [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)]中处理与图表、数据条、迷你图、仪表和指示器相关的数据，请将报表导出为 CSV 文件，然后在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel 中打开该文件。</span><span class="sxs-lookup"><span data-stu-id="dd092-107">If you want to work with data related to charts, data bars, sparklines, gauges, and indicators in [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)], export the report to a CSV file, and then open the file in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="csv-rendering"></a><a name="CSVRendering"></a> <span data-ttu-id="dd092-108">CSV 呈现</span><span class="sxs-lookup"><span data-stu-id="dd092-108">CSV Rendering</span></span>  
 <span data-ttu-id="dd092-109">当使用默认设置进行呈现时，CSV 报表具有以下特征：</span><span class="sxs-lookup"><span data-stu-id="dd092-109">When rendered using the default settings, a CSV report has the following characteristics:</span></span>  
  
-   <span data-ttu-id="dd092-110">默认字段分隔符字符串是逗号 (,)。</span><span class="sxs-lookup"><span data-stu-id="dd092-110">The default field delimiter string is a comma (,).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="dd092-111">可通过更改设备信息设置将字段分隔符更改为任何所需的字符，包括 TAB。</span><span class="sxs-lookup"><span data-stu-id="dd092-111">You can change the field delimiter to any character that you want, including TAB, by changing the device information settings.</span></span> <span data-ttu-id="dd092-112">有关详细信息，请参阅 [CSV Device Information Settings](../csv-device-information-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="dd092-112">For more information, see [CSV Device Information Settings](../csv-device-information-settings.md).</span></span>  
  
-   <span data-ttu-id="dd092-113">记录分隔符字符串是回车符和换行 (\<cr> \<lf>) 。</span><span class="sxs-lookup"><span data-stu-id="dd092-113">The record delimiter string is the carriage return and line feed (\<cr>\<lf>).</span></span>  
  
-   <span data-ttu-id="dd092-114">文本限定符字符串是引号 (")。</span><span class="sxs-lookup"><span data-stu-id="dd092-114">The text qualifier string is a quotation mark (").</span></span>  
  
     <span data-ttu-id="dd092-115">CSV 呈现器不在所有文本字符串周围添加限定符。</span><span class="sxs-lookup"><span data-stu-id="dd092-115">The CSV renderer does not add qualifiers around all text strings.</span></span> <span data-ttu-id="dd092-116">只有在值包含分隔符或值具有换行符时才会添加文本限定符。</span><span class="sxs-lookup"><span data-stu-id="dd092-116">Text qualifiers are added only when the value contains the delimiter character or when the value has a line break.</span></span>  
  
-   <span data-ttu-id="dd092-117">如果文本包含嵌入的分隔符字符串或限定符字符串，则会用文本限定符（引号）将该文本括起来，还将嵌入的限定符字符串（引号）用引号引起来。</span><span class="sxs-lookup"><span data-stu-id="dd092-117">If the text contains an embedded delimiter string or qualifier string, the text qualifier is placed around the text, and the embedded qualifier strings are doubled.</span></span>  
  
-   <span data-ttu-id="dd092-118">忽略格式设置和布局。</span><span class="sxs-lookup"><span data-stu-id="dd092-118">Formatting and layout are ignored.</span></span>  
  
 <span data-ttu-id="dd092-119">在呈现期间会忽略以下项：</span><span class="sxs-lookup"><span data-stu-id="dd092-119">The following items are ignored during rendering:</span></span>  
  
-   <span data-ttu-id="dd092-120">页眉</span><span class="sxs-lookup"><span data-stu-id="dd092-120">Page header</span></span>  
  
-   <span data-ttu-id="dd092-121">页脚</span><span class="sxs-lookup"><span data-stu-id="dd092-121">Page footer</span></span>  
  
-   <span data-ttu-id="dd092-122">自定义报表项</span><span class="sxs-lookup"><span data-stu-id="dd092-122">Custom report items</span></span>  
  
-   <span data-ttu-id="dd092-123">线</span><span class="sxs-lookup"><span data-stu-id="dd092-123">Line</span></span>  
  
-   <span data-ttu-id="dd092-124">映像</span><span class="sxs-lookup"><span data-stu-id="dd092-124">Image</span></span>  
  
-   <span data-ttu-id="dd092-125">矩形</span><span class="sxs-lookup"><span data-stu-id="dd092-125">Rectangle</span></span>  
  
-   <span data-ttu-id="dd092-126">自动小计</span><span class="sxs-lookup"><span data-stu-id="dd092-126">Automatic subtotals</span></span>  
  
 <span data-ttu-id="dd092-127">对其余的报表项进行排序，先从上到下排，再从左到右排。</span><span class="sxs-lookup"><span data-stu-id="dd092-127">The remaining report items are sorted, from top to bottom, then left to right.</span></span> <span data-ttu-id="dd092-128">之后，每一项将呈现到一列中。</span><span class="sxs-lookup"><span data-stu-id="dd092-128">Each item is then rendered to a column.</span></span> <span data-ttu-id="dd092-129">如果报表有嵌套数据项（如列表或表），则会在每条记录中重复它的父项。</span><span class="sxs-lookup"><span data-stu-id="dd092-129">If the report has nested data items like lists or tables, the parent items are repeated in each record.</span></span>  
  
 <span data-ttu-id="dd092-130">下表说明了呈现报表项时这些报表项的外观：</span><span class="sxs-lookup"><span data-stu-id="dd092-130">The following table indicates the appearance of report items when rendered:</span></span>  
  
|<span data-ttu-id="dd092-131">项</span><span class="sxs-lookup"><span data-stu-id="dd092-131">Item</span></span>|<span data-ttu-id="dd092-132">呈现行为</span><span class="sxs-lookup"><span data-stu-id="dd092-132">Rendering behavior</span></span>|  
|----------|------------------------|  
|<span data-ttu-id="dd092-133">文本框</span><span class="sxs-lookup"><span data-stu-id="dd092-133">Text box</span></span>|<span data-ttu-id="dd092-134">呈现文本框的内容。</span><span class="sxs-lookup"><span data-stu-id="dd092-134">Renders the contents of the text box.</span></span> <span data-ttu-id="dd092-135">在默认模式下，会根据项的格式设置属性对其进行格式化。</span><span class="sxs-lookup"><span data-stu-id="dd092-135">In default mode, items are formatted based on the item's formatting properties.</span></span> <span data-ttu-id="dd092-136">在兼容模式下，可以根据设备信息设置对格式进行更改。</span><span class="sxs-lookup"><span data-stu-id="dd092-136">In compliant mode, formatting can be changed by device information settings.</span></span> <span data-ttu-id="dd092-137">有关 CSV 呈现模式的详细信息，请参阅下文。</span><span class="sxs-lookup"><span data-stu-id="dd092-137">For more information about CSV rendering modes, see below.</span></span>|  
|<span data-ttu-id="dd092-138">表</span><span class="sxs-lookup"><span data-stu-id="dd092-138">Table</span></span>|<span data-ttu-id="dd092-139">呈现方式为扩展该表，在只保留最起码的格式的情况下为每一行和每一列都分别创建行和列。</span><span class="sxs-lookup"><span data-stu-id="dd092-139">Renders by expanding the table and creating a row and column for each row and column at the lowest level of detail.</span></span> <span data-ttu-id="dd092-140">小计行和小计列没有列标题或行标题。</span><span class="sxs-lookup"><span data-stu-id="dd092-140">Subtotal rows and columns do not have column or row headings.</span></span> <span data-ttu-id="dd092-141">不支持钻取报表。</span><span class="sxs-lookup"><span data-stu-id="dd092-141">Drillthrough reports are not supported.</span></span>|  
|<span data-ttu-id="dd092-142">Matrix</span><span class="sxs-lookup"><span data-stu-id="dd092-142">Matrix</span></span>|<span data-ttu-id="dd092-143">呈现方式为扩展该矩阵，在只保留最起码的格式的情况下为每一行和每一列都分别创建行和列。</span><span class="sxs-lookup"><span data-stu-id="dd092-143">Renders by expanding the matrix and creating a row and column for each row and column at the lowest level of detail.</span></span> <span data-ttu-id="dd092-144">小计行和小计列没有列标题或行标题。</span><span class="sxs-lookup"><span data-stu-id="dd092-144">Subtotal rows and columns do not have column or row headings.</span></span>|  
|<span data-ttu-id="dd092-145">列出</span><span class="sxs-lookup"><span data-stu-id="dd092-145">List</span></span>|<span data-ttu-id="dd092-146">为列表中每一明细行或实例呈现一个记录。</span><span class="sxs-lookup"><span data-stu-id="dd092-146">Renders a record for each detail row or instance in the list.</span></span>|  
|<span data-ttu-id="dd092-147">子报表</span><span class="sxs-lookup"><span data-stu-id="dd092-147">Subreport</span></span>|<span data-ttu-id="dd092-148">对于内容的每个实例，都会重复它的父项。</span><span class="sxs-lookup"><span data-stu-id="dd092-148">The parent item is repeated for each instance of the contents.</span></span>|  
|<span data-ttu-id="dd092-149">图表</span><span class="sxs-lookup"><span data-stu-id="dd092-149">Chart</span></span>|<span data-ttu-id="dd092-150">通过创建每个图表值的行和成员标签来呈现。</span><span class="sxs-lookup"><span data-stu-id="dd092-150">Renders by creating a row for each chart value and member labels.</span></span> <span data-ttu-id="dd092-151">来自系列和类别的标签采用平展的层次结构，并包含在图表值的行中。</span><span class="sxs-lookup"><span data-stu-id="dd092-151">Labels from series and categories in hierarchies are flattened and included in the row for a chart value.</span></span>|  
|<span data-ttu-id="dd092-152">数据条</span><span class="sxs-lookup"><span data-stu-id="dd092-152">Data bar</span></span>|<span data-ttu-id="dd092-153">像图表一样呈现。</span><span class="sxs-lookup"><span data-stu-id="dd092-153">Renders like a chart.</span></span> <span data-ttu-id="dd092-154">通常，数据条并不包括层次结构或标签。</span><span class="sxs-lookup"><span data-stu-id="dd092-154">Typically, a data bar does not include hierarchies or labels.</span></span>|  
|<span data-ttu-id="dd092-155">迷你图</span><span class="sxs-lookup"><span data-stu-id="dd092-155">Sparkline</span></span>|<span data-ttu-id="dd092-156">像图表一样呈现。</span><span class="sxs-lookup"><span data-stu-id="dd092-156">Renders like a chart.</span></span> <span data-ttu-id="dd092-157">通常，迷你图并不包括层次结构或标签。</span><span class="sxs-lookup"><span data-stu-id="dd092-157">Typically, a sparkline does not  do not include hierarchies or labels.</span></span>|  
|<span data-ttu-id="dd092-158">仪表</span><span class="sxs-lookup"><span data-stu-id="dd092-158">Gauge</span></span>|<span data-ttu-id="dd092-159">作为单个记录呈现，具有线性刻度的最小值和最大值、范围的起始和终止值，以及指针的值。</span><span class="sxs-lookup"><span data-stu-id="dd092-159">Renders as a single record with the minimum and maximum values of the linear scale, start and end values of the range, and the value of the pointer.</span></span>|  
|<span data-ttu-id="dd092-160">指示器</span><span class="sxs-lookup"><span data-stu-id="dd092-160">Indicator</span></span>|<span data-ttu-id="dd092-161">作为单个记录呈现，具有活动状态名称、可用状态以及数据值。</span><span class="sxs-lookup"><span data-stu-id="dd092-161">Renders as a single record with the active state name, available states, and the data value.</span></span>|  
|<span data-ttu-id="dd092-162">映射</span><span class="sxs-lookup"><span data-stu-id="dd092-162">Map</span></span>|<span data-ttu-id="dd092-163">对于地图层的每个地图成员，呈现包含标签和值的行。</span><span class="sxs-lookup"><span data-stu-id="dd092-163">Renders a row with the labels and values for each map member of a map layer.</span></span><br /><br /> <span data-ttu-id="dd092-164">如果地图具有多个层，则行中的值将会变化，具体取决于地图层是使用相同还是不同的地图数据区域。</span><span class="sxs-lookup"><span data-stu-id="dd092-164">If the map has multiple layers the values in the rows varies depending on whether the map layers use the same or different map data regions.</span></span> <span data-ttu-id="dd092-165">如果多个地图层使用相同数据区域，该行将包含所有层的数据。</span><span class="sxs-lookup"><span data-stu-id="dd092-165">If multiple map layers use the same data region, the rows contain data from all layers.</span></span>|  
  
### <a name="hierarchical-and-grouped-data"></a><span data-ttu-id="dd092-166">分层数据和分组数据</span><span class="sxs-lookup"><span data-stu-id="dd092-166">Hierarchical and Grouped Data</span></span>  
 <span data-ttu-id="dd092-167">分层数据和分组数据必须进行平展才能以 CSV 格式表示。</span><span class="sxs-lookup"><span data-stu-id="dd092-167">Hierarchical and grouped data must be flattened in order to be represented in the CSV format.</span></span>  
  
 <span data-ttu-id="dd092-168">呈现扩展插件可将报表平展为用于表示数据区域中嵌套组的树结构。</span><span class="sxs-lookup"><span data-stu-id="dd092-168">The rendering extension flattens the report into a tree structure that represents the nested groups within the data region.</span></span> <span data-ttu-id="dd092-169">要平展报表：</span><span class="sxs-lookup"><span data-stu-id="dd092-169">To flatten the report:</span></span>  
  
-   <span data-ttu-id="dd092-170">行层次结构在列层次结构之前进行平展。</span><span class="sxs-lookup"><span data-stu-id="dd092-170">A row hierarchy is flattened before a column hierarchy.</span></span>  
  
-   <span data-ttu-id="dd092-171">列按照以下顺序排序：表体中的文本框的顺序为从左到右，从上到下，后面紧跟数据区域，后者顺序为从左到右，从上到下。</span><span class="sxs-lookup"><span data-stu-id="dd092-171">Columns are ordered as follows: text boxes in body order left-to-right, top-to-bottom followed by data regions ordered left-to-right, top-to-bottom.</span></span>  
  
-   <span data-ttu-id="dd092-172">在数据区域中，列按照以下顺序排序：角成员、行层次结构成员、列层次结构成员，然后是单元。</span><span class="sxs-lookup"><span data-stu-id="dd092-172">Within a data region, the columns are ordered as follows: corner members, row hierarchy members, column hierarchy members, and then cells.</span></span>  
  
-   <span data-ttu-id="dd092-173">对等数据区域是一些共享一个公共数据区域或动态祖先的数据区域或动态组。</span><span class="sxs-lookup"><span data-stu-id="dd092-173">Peer data regions are data regions or dynamic groups that share a common data region or dynamic ancestor.</span></span> <span data-ttu-id="dd092-174">对等数据通过平展后的树的分支进行标识。</span><span class="sxs-lookup"><span data-stu-id="dd092-174">Peer data is identified by branching of the flattened tree.</span></span>  
  
 <span data-ttu-id="dd092-175">有关详细信息，请参阅 [表、矩阵和列表（报表生成器和 SSRS）](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="dd092-175">For more information, see [Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md).</span></span>  
  
 
  
##  <a name="renderer-modes"></a><a name="RenderingModes"></a> <span data-ttu-id="dd092-176">呈现器模式</span><span class="sxs-lookup"><span data-stu-id="dd092-176">Renderer Modes</span></span>  
 <span data-ttu-id="dd092-177">CSV 呈现扩展插件可在两种模式下运行：一种模式针对 Excel 进行了优化，另一种模式针对要求严格遵守 RFC 4180 中的 CSV 规范的第三方应用程序进行了优化。</span><span class="sxs-lookup"><span data-stu-id="dd092-177">The CSV rendering extension can operate in two modes: one is optimized for Excel and the other is optimized for third-party applications that require strict CSV compliance to the CSV specification in RFC 4180.</span></span> <span data-ttu-id="dd092-178">根据所用模式的不同，对等数据区域的处理方式也有所不同。</span><span class="sxs-lookup"><span data-stu-id="dd092-178">Depending on which mode you use, peer data regions are handled differently.</span></span>  
  
### <a name="default-mode"></a><span data-ttu-id="dd092-179">默认模式</span><span class="sxs-lookup"><span data-stu-id="dd092-179">Default Mode</span></span>  
 <span data-ttu-id="dd092-180">默认模式针对 Excel 进行了优化。</span><span class="sxs-lookup"><span data-stu-id="dd092-180">The default mode is optimized for Excel.</span></span> <span data-ttu-id="dd092-181">使用默认模式呈现时，报表将呈现为带多个以 CSV 格式呈现的数据部分的 CSV 文件。</span><span class="sxs-lookup"><span data-stu-id="dd092-181">When rendered in default mode, the report is rendered as a CSV file with multiple sections of CSV-rendered data.</span></span> <span data-ttu-id="dd092-182">每个对等数据区域均由一个空行分隔。</span><span class="sxs-lookup"><span data-stu-id="dd092-182">Each peer data region is delimited by an empty line.</span></span> <span data-ttu-id="dd092-183">表体中的各对等数据区域呈现为 CSV 文件中的独立数据块。</span><span class="sxs-lookup"><span data-stu-id="dd092-183">Peer data regions within the report body are rendered as separate blocks of data within the CSV file.</span></span> <span data-ttu-id="dd092-184">呈现结果为 CSV 文件，在该 CSV 文件中：</span><span class="sxs-lookup"><span data-stu-id="dd092-184">The result is a CSV file in which:</span></span>  
  
-   <span data-ttu-id="dd092-185">表体中的各个文本框均作为 CSV 文件中的第一个数据块呈现，只呈现一次。</span><span class="sxs-lookup"><span data-stu-id="dd092-185">Individual text boxes within the report body are rendered once as the first block of data within the CSV file.</span></span>  
  
-   <span data-ttu-id="dd092-186">表体中的每个顶级对等数据区域在其各自的数据块中呈现。</span><span class="sxs-lookup"><span data-stu-id="dd092-186">Each top-level peer data region in the report body is rendered in its own data block.</span></span>  
  
-   <span data-ttu-id="dd092-187">嵌套数据区域会沿对角线呈现到同一数据块中。</span><span class="sxs-lookup"><span data-stu-id="dd092-187">Nested data regions are rendered diagonally into the same data block.</span></span>  
  
#### <a name="formatting"></a><span data-ttu-id="dd092-188">格式化</span><span class="sxs-lookup"><span data-stu-id="dd092-188">Formatting</span></span>  
 <span data-ttu-id="dd092-189">数值按照其格式化后的状态呈现。</span><span class="sxs-lookup"><span data-stu-id="dd092-189">Numeric values are rendered in their formatted state.</span></span> <span data-ttu-id="dd092-190">Excel 可识别经过格式化的数值（例如货币、百分比和日期），并可在导入 CSV 文件时对单元进行合适的格式化。</span><span class="sxs-lookup"><span data-stu-id="dd092-190">Excel can recognize formatted numeric values, such as currency, percentage and date, and format the cells appropriately when importing the CSV file.</span></span>  
  
### <a name="compliant-mode"></a><span data-ttu-id="dd092-191">兼容模式</span><span class="sxs-lookup"><span data-stu-id="dd092-191">Compliant Mode</span></span>  
 <span data-ttu-id="dd092-192">兼容模式针对第三方应用程序进行了优化。</span><span class="sxs-lookup"><span data-stu-id="dd092-192">Compliant mode is optimized for third-party applications.</span></span>  
  
#### <a name="data-regions"></a><span data-ttu-id="dd092-193">数据区域</span><span class="sxs-lookup"><span data-stu-id="dd092-193">Data Regions</span></span>  
 <span data-ttu-id="dd092-194">只有文件的第一行包含列标题，并且每一行均具有数目相同的列。</span><span class="sxs-lookup"><span data-stu-id="dd092-194">Only the first row of the file contains the column headers and each row has the same number of columns.</span></span>  
  
#### <a name="formatting"></a><span data-ttu-id="dd092-195">格式化</span><span class="sxs-lookup"><span data-stu-id="dd092-195">Formatting</span></span>  
 <span data-ttu-id="dd092-196">值未经过格式化。</span><span class="sxs-lookup"><span data-stu-id="dd092-196">Values are unformatted.</span></span>  
  
##  <a name="interactivity"></a><a name="Interactivity"></a><span data-ttu-id="dd092-197">互动</span><span class="sxs-lookup"><span data-stu-id="dd092-197">Interactivity</span></span>  
 <span data-ttu-id="dd092-198">此呈现器生成的两种 CSV 格式都不支持交互。</span><span class="sxs-lookup"><span data-stu-id="dd092-198">Interactivity is not supported by either CSV formats generated by this renderer.</span></span> <span data-ttu-id="dd092-199">不会呈现以下交互元素：</span><span class="sxs-lookup"><span data-stu-id="dd092-199">The following interactive elements are not rendered:</span></span>  
  
-   <span data-ttu-id="dd092-200">超链接</span><span class="sxs-lookup"><span data-stu-id="dd092-200">Hyperlinks</span></span>  
  
-   <span data-ttu-id="dd092-201">显示或隐藏</span><span class="sxs-lookup"><span data-stu-id="dd092-201">Show or Hide</span></span>  
  
-   <span data-ttu-id="dd092-202">文档结构图</span><span class="sxs-lookup"><span data-stu-id="dd092-202">Document Map</span></span>  
  
-   <span data-ttu-id="dd092-203">钻取链接或点击链接</span><span class="sxs-lookup"><span data-stu-id="dd092-203">Drillthrough or clickthrough links</span></span>  
  
-   <span data-ttu-id="dd092-204">最终用户排序</span><span class="sxs-lookup"><span data-stu-id="dd092-204">End user sort</span></span>  
  
-   <span data-ttu-id="dd092-205">修复标题</span><span class="sxs-lookup"><span data-stu-id="dd092-205">Fixes headers</span></span>  
  
-   <span data-ttu-id="dd092-206">书签</span><span class="sxs-lookup"><span data-stu-id="dd092-206">Bookmarks</span></span>  
  

  
##  <a name="device-information-settings"></a><a name="DeviceInfo"></a><span data-ttu-id="dd092-207">设备信息设置</span><span class="sxs-lookup"><span data-stu-id="dd092-207">Device Information Settings</span></span>  
 <span data-ttu-id="dd092-208">您可以通过更改设备信息设置来更改相应呈现器的某些默认设置，包括呈现使用的模式、用作分隔符的字符以及用作文本限定符默认字符串的字符。</span><span class="sxs-lookup"><span data-stu-id="dd092-208">You can change some default settings for this renderer, including which mode to render in, which characters to use as delimiters and which characters to use as the text qualifier default string, by changing the device information settings.</span></span> <span data-ttu-id="dd092-209">有关详细信息，请参阅 [CSV Device Information Settings](../csv-device-information-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="dd092-209">For more information, see [CSV Device Information Settings](../csv-device-information-settings.md).</span></span>  
  
  
  
## <a name="see-also"></a><span data-ttu-id="dd092-210">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dd092-210">See Also</span></span>  
 <span data-ttu-id="dd092-211">[Reporting Services &#40;报表生成器和 SSRS 中的分页&#41;](../report-design/pagination-in-reporting-services-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="dd092-211">[Pagination in Reporting Services &#40;Report Builder  and SSRS&#41;](../report-design/pagination-in-reporting-services-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="dd092-212">[呈现行为 &#40;报表生成器和 SSRS&#41;](../report-design/rendering-behaviors-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="dd092-212">[Rendering Behaviors &#40;Report Builder  and SSRS&#41;](../report-design/rendering-behaviors-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="dd092-213">[不同报表呈现扩展插件的交互功能 &#40;报表生成器和 SSRS&#41;](interactive-functionality-different-report-rendering-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="dd092-213">[Interactive Functionality for Different Report Rendering Extensions &#40;Report Builder and SSRS&#41;](interactive-functionality-different-report-rendering-extensions.md) </span></span>  
 <span data-ttu-id="dd092-214">[&#40;报表生成器和 SSRS 呈现报表项&#41;](../report-design/rendering-report-items-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="dd092-214">[Rendering Report Items &#40;Report Builder and SSRS&#41;](../report-design/rendering-report-items-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="dd092-215">表、矩阵和列表（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="dd092-215">Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;</span></span>](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)  
  
  
