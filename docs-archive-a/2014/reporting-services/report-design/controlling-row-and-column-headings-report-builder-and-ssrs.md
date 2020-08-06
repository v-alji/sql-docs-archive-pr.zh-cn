---
title: 控制行标题和列标题（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4be6e836-158e-4bc9-8870-7f394d7c7e11
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 19d0deb86bfeea70c92ffb17ec79966788102748
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586464"
---
# <a name="controlling-row-and-column-headings-report-builder-and-ssrs"></a><span data-ttu-id="ef3b3-102">控制行标题和列标题（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="ef3b3-102">Controlling Row and Column Headings (Report Builder and SSRS)</span></span>
  <span data-ttu-id="ef3b3-103">表、矩阵或列表数据区域可以水平或垂直跨多页。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-103">A table, matrix, or list data region can span multiple pages horizontally or vertically.</span></span> <span data-ttu-id="ef3b3-104">您可以指定是否在每页上重复显示行标题或列标题。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-104">You can specify whether to repeat row or column headings on each page.</span></span> <span data-ttu-id="ef3b3-105">在交互式呈现器（如报表管理器）或报表预览中，还可以指定是否冻结行标题或列标题，以便在滚动报表时始终显示标题。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-105">In an interactive renderer such as Report Manager or report preview, you can also specify whether to freeze row or column headings to keep them in view when you scroll across or down a report.</span></span> <span data-ttu-id="ef3b3-106">在表或矩阵中，第一行通常包含列标题，用来为每列中的数据加上标签；第一列通常包含行标题，用来为每行中的数据加上标签。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-106">In a table or matrix, the first row usually contains column headings that label data in each column; the first column usually contains row headings that label the data in each row.</span></span> <span data-ttu-id="ef3b3-107">对于嵌套组，您可能需要重复显示包含组标签的初始行标题集和列标题集。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-107">For nested groups, you might want to repeat the initial set of row and column headings that contain group labels.</span></span> <span data-ttu-id="ef3b3-108">默认情况下，列表数据区域不包含标题。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-108">By default, a list data region does not include headings.</span></span>

 <span data-ttu-id="ef3b3-109">控制是否重复或冻结标题的方式取决于以下因素：</span><span class="sxs-lookup"><span data-stu-id="ef3b3-109">How you control whether headings repeat or freeze depends on the following:</span></span>

-   <span data-ttu-id="ef3b3-110">对于在每页顶部重复的列标题：</span><span class="sxs-lookup"><span data-stu-id="ef3b3-110">For column headings that repeat at the top of each page:</span></span>

    -   <span data-ttu-id="ef3b3-111">表或矩阵是否具有水平扩展的列组区域。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-111">Whether the table or matrix has a column group area that expands horizontally.</span></span>

    -   <span data-ttu-id="ef3b3-112">您是否要将与列组关联的所有行作为一个单元进行控制。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-112">Whether you want to control all rows that are associated with column groups as a unit.</span></span>

-   <span data-ttu-id="ef3b3-113">对于沿每页的边线重复的行标题：</span><span class="sxs-lookup"><span data-stu-id="ef3b3-113">For row headings that repeat along the side of each page:</span></span>

    -   <span data-ttu-id="ef3b3-114">表或矩阵是否具有垂直扩展的行组区域。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-114">Whether the table or matrix has a row group area that expands vertically.</span></span> <span data-ttu-id="ef3b3-115">仅支持具有行组头的行组的行标题。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-115">Row headings are supported only for row groups with a row group header.</span></span>

> [!NOTE]
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]

## <a name="understanding-rows-and-columns-in-a-tablix-data-region"></a><span data-ttu-id="ef3b3-116">了解 Tablix 数据区域中的行和列</span><span class="sxs-lookup"><span data-stu-id="ef3b3-116">Understanding Rows and Columns in a Tablix Data Region</span></span>
 <span data-ttu-id="ef3b3-117">表或矩阵是基础 tablix 数据区域的模板。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-117">A table or matrix is a template for the underlying tablix data region.</span></span> <span data-ttu-id="ef3b3-118">Tablix 数据区域可能具有四个区域：行组区（控制报表中向下扩展的行）、列组区（控制报表中横向扩展的列）、正文区（显示数据）和角区。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-118">A tablix data region has four possible areas: the row group area that controls rows that expand down a report, the column group area that controls columns that expand across a report, the body that displays data, and the corner.</span></span> <span data-ttu-id="ef3b3-119">若要了解在何处设置属性来控制重复或冻结标题，首先应了解 tablix 数据区域有两种表示形式：</span><span class="sxs-lookup"><span data-stu-id="ef3b3-119">To understand where to set properties to control repeating or freezing headers, it helps to understand that there are two representations for a tablix data region:</span></span>

-   <span data-ttu-id="ef3b3-120">**在报表定义中** Tablix 数据区域定义中的每行或每列都是特定行组或列组的 tablix 成员。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-120">**In the report definition** Each row or column in a tablix data region definition is a tablix member of a specific row or column group.</span></span> <span data-ttu-id="ef3b3-121">Tablix 成员是静态成员或动态成员。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-121">A tablix member is static or dynamic.</span></span> <span data-ttu-id="ef3b3-122">静态 tablix 成员包含标签或小计，每组重复一次。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-122">A static tablix member contains labels or subtotals and repeats once per group.</span></span> <span data-ttu-id="ef3b3-123">动态 tablix 成员包含组值，每个唯一组值（也称为组实例）重复一次。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-123">A dynamic tablix member contains group values and repeats once per unique value of a group, also known as a group instance.</span></span>

-   <span data-ttu-id="ef3b3-124">**在设计图面上** 在设计图面上，虚线将 tablix 数据区域分为四个区域。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-124">**On the design surface** On the design surface, dotted lines divide a tablix data region into the four areas.</span></span> <span data-ttu-id="ef3b3-125">Tablix 数据区域中的每个单元被组织为行和列。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-125">Each cell in a tablix data region area is organized into rows and columns.</span></span> <span data-ttu-id="ef3b3-126">行和列与组（包括详细信息组）关联。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-126">Rows and columns are associated with groups, including the details group.</span></span> <span data-ttu-id="ef3b3-127">对于选定的 tablix 数据区域，行控点和列控点以及突出显示栏指示组成员身份。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-127">For a selected tablix data region, row and column handles and highlight bars indicate group membership.</span></span> <span data-ttu-id="ef3b3-128">行组或列组区域中的单元表示 tablix 成员的组头。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-128">Cells in the row group or column group area represent group headers for tablix members.</span></span> <span data-ttu-id="ef3b3-129">一行或一列可以与多个组关联。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-129">A single row or column can be associated with multiple groups.</span></span>

     <span data-ttu-id="ef3b3-130">有关详细信息，请参阅 [Tablix 数据区域（报表生成器和 SSRS）](../tablix-data-region-report-builder-and-ssrs.md)和 [Tablix 数据区域单元格、行和列（报表生成器和 SSRS）](tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-130">For more information, see [Tablix Data Region &#40;Report Builder and SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) and [Tablix Data Region Cells, Rows, and Columns &#40;Report Builder&#41; and SSRS](tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md).</span></span>

 <span data-ttu-id="ef3b3-131">对于具有行组或列组区域的 tablix 数据区域，设置 tablix 数据区域的属性即可控制关联的行和列。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-131">For tablix data regions with row group or column group areas, control the associated rows and columns by setting properties on tablix data region.</span></span> <span data-ttu-id="ef3b3-132">对于所有其他情况，则可通过在“属性”窗格中设置选定 tablix 成员的属性来控制行和列。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-132">For all other cases, control the rows and columns by setting properties in the Properties pane for the selected tablix member.</span></span> <span data-ttu-id="ef3b3-133">有关分步说明，请参阅[在多个页中显示行标题和列标题（报表生成器和 SSRS）](display-row-and-column-headers-on-multiple-pages-report-builder-and-ssrs.md)和[在滚动报表时保持标题可见（报表生成器和 SSRS）](keep-headers-visible-when-scrolling-through-a-report-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-133">For step-by-step instructions, see [Display Row and Column Headers on Multiple Pages &#40;Report Builder and SSRS&#41;](display-row-and-column-headers-on-multiple-pages-report-builder-and-ssrs.md) and [Keep Headers Visible When Scrolling Through a Report &#40;Report Builder and SSRS&#41;](keep-headers-visible-when-scrolling-through-a-report-report-builder-and-ssrs.md).</span></span>

##  <a name="examples"></a><a name="Top"></a> <span data-ttu-id="ef3b3-134">示例</span><span class="sxs-lookup"><span data-stu-id="ef3b3-134">Examples</span></span>
 <span data-ttu-id="ef3b3-135">Tablix 数据区域最常见的示例包括：矩阵、没有组的表、具有行组和行组头的表以及具有行组但没有行组头的表。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-135">The most common examples of tablix data regions are for a matrix, a table with no groups, and a table with a row group and a row group header, and a table with a row group but no row group header.</span></span> <span data-ttu-id="ef3b3-136">若要控制如何重复或冻结表头，必须确定要控制的行或列是与行组区域中的组头关联，还是与列组区域中的组头关联。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-136">To control how to repeat or freeze headers, you must determine if the rows or columns that you want to control are associated with a group header in the row groups or column groups area.</span></span>

 <span data-ttu-id="ef3b3-137">以下部分提供有关 tablix 数据区域通用布局的示例：</span><span class="sxs-lookup"><span data-stu-id="ef3b3-137">The following sections provide examples for common layouts for a tablix data region:</span></span>

-   [<span data-ttu-id="ef3b3-138">Matrix</span><span class="sxs-lookup"><span data-stu-id="ef3b3-138">Matrix</span></span>](#Matrix)

-   [<span data-ttu-id="ef3b3-139">没有组的表</span><span class="sxs-lookup"><span data-stu-id="ef3b3-139">Table with no groups</span></span>](#TableNoGroups)

-   [<span data-ttu-id="ef3b3-140">具有行组和行组区域的表</span><span class="sxs-lookup"><span data-stu-id="ef3b3-140">Table with row groups and row group area</span></span>](#TableRowGroupsGroupHeader)

-   [<span data-ttu-id="ef3b3-141">具有行组但没有行组区域的表</span><span class="sxs-lookup"><span data-stu-id="ef3b3-141">Table with row groups but no row group area</span></span>](#TableRowGroupsNoGroupHeader)

###  <a name="matrix"></a><a name="Matrix"></a><span data-ttu-id="ef3b3-142">矩阵</span><span class="sxs-lookup"><span data-stu-id="ef3b3-142">Matrix</span></span>
 <span data-ttu-id="ef3b3-143">默认情况下，简单矩阵具有一个行组和一个列组。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-143">By default, a simple matrix has one row group and one column group.</span></span> <span data-ttu-id="ef3b3-144">下图显示的矩阵具有一个基于 Category 的行组和一个基于 Geography 的列组：</span><span class="sxs-lookup"><span data-stu-id="ef3b3-144">The following figure shows a matrix with a row group that is based on Category and a column group that is based on Geography:</span></span>

 <span data-ttu-id="ef3b3-145">![矩阵、Category 行和 Geography 列组](../media/rs-basicmatrixdesign.gif "矩阵、Category 行和 Geography 列组")</span><span class="sxs-lookup"><span data-stu-id="ef3b3-145">![Matrix, Category row and Geography column group](../media/rs-basicmatrixdesign.gif "Matrix, Category row and Geography column group")</span></span>

 <span data-ttu-id="ef3b3-146">虚线显示四个 tablix 区域。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-146">The dotted lines show the four tablix areas.</span></span> <span data-ttu-id="ef3b3-147">行组区域具有一个控制第一列中类别标签的行组头。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-147">The row group area has a row group header that controls the category labels in the first column.</span></span> <span data-ttu-id="ef3b3-148">同样，列组区域具有一个控制第一行中地理标签的列组头。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-148">Similarly, the column group area has a column group header that controls the geography labels in the first row.</span></span> <span data-ttu-id="ef3b3-149">在预览中，当矩阵跨页展开时，第一行会显示列标题，如下图所示：</span><span class="sxs-lookup"><span data-stu-id="ef3b3-149">In preview, as the matrix expands across the page, the first row displays the column headings, as shown in the following figure:</span></span>

 <span data-ttu-id="ef3b3-150">![呈现的矩阵（包含扩展组）预览](../media/rs-basicmatrixpreview.gif "呈现的矩阵（包含扩展组）预览")</span><span class="sxs-lookup"><span data-stu-id="ef3b3-150">![Preview for rendered matrix with expanded groups](../media/rs-basicmatrixpreview.gif "Preview for rendered matrix with expanded groups")</span></span>

 <span data-ttu-id="ef3b3-151">若要重复或冻结第一行中的列标题，请设置 tablix 数据区域中列标题的属性。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-151">To repeat or freeze column headings in the first row, set properties for column headers on the tablix data region.</span></span> <span data-ttu-id="ef3b3-152">将自动包含嵌套列组的列标题。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-152">Column headers for nested column groups are automatically included.</span></span>

 <span data-ttu-id="ef3b3-153">若要重复或冻结第一列中的行标题，请设置 tablix 数据区域中行标题的属性。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-153">To repeat or freeze row headings in the first column, set properties for row headers on the tablix data region.</span></span> <span data-ttu-id="ef3b3-154">将自动包含嵌套行组的行标题。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-154">Row headers for nested row groups are automatically included.</span></span>

 [<span data-ttu-id="ef3b3-155">返回页首</span><span class="sxs-lookup"><span data-stu-id="ef3b3-155">Return to top</span></span>](#Top)

###  <a name="table-with-no-row-groups"></a><a name="TableNoGroups"></a><span data-ttu-id="ef3b3-156">没有行组的表</span><span class="sxs-lookup"><span data-stu-id="ef3b3-156">Table with no row groups</span></span>
 <span data-ttu-id="ef3b3-157">默认情况下，没有组的简单表包含详细信息组。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-157">By default, a simple table with no groups does include the details group.</span></span> <span data-ttu-id="ef3b3-158">下图所示的表显示了类别、订单号和销售数据：</span><span class="sxs-lookup"><span data-stu-id="ef3b3-158">The following figure shows a table that displays category, order number, and sales data:</span></span>

 <span data-ttu-id="ef3b3-159">![“设计”窗格：包含一个静态行和一个动态行的表](../media/rs-tableheaderstaticdesign.gif "“设计”窗格：包含一个静态行和一个动态行的表")</span><span class="sxs-lookup"><span data-stu-id="ef3b3-159">![Design, table with one static, one dynamic row](../media/rs-tableheaderstaticdesign.gif "Design, table with one static, one dynamic row")</span></span>

 <span data-ttu-id="ef3b3-160">因为该表只有 tablix 正文区，所以没有虚线。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-160">There are no dotted lines because the table consists only of the tablix body area.</span></span> <span data-ttu-id="ef3b3-161">第一行显示列标题，表示一个未与组关联的静态 tablix 成员。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-161">The first row displays column headers, and represents a static tablix member that is not associated with a group.</span></span> <span data-ttu-id="ef3b3-162">第二行显示详细信息数据，表示一个与详细信息组关联的动态 tablix 成员。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-162">The second row displays detail data, and represents a dynamic tablix member that is associated with the details group.</span></span> <span data-ttu-id="ef3b3-163">下图在预览中显示此表：</span><span class="sxs-lookup"><span data-stu-id="ef3b3-163">The following figure shows the table in preview:</span></span>

 <span data-ttu-id="ef3b3-164">![“预览”窗格：包含一个静态行和一个动态行的表](../media/rs-tableheaderstaticpreview.gif "“预览”窗格：包含一个静态行和一个动态行的表")</span><span class="sxs-lookup"><span data-stu-id="ef3b3-164">![Preview, table with one static, one dynamic row](../media/rs-tableheaderstaticpreview.gif "Preview, table with one static, one dynamic row")</span></span>

 <span data-ttu-id="ef3b3-165">若要重复或冻结列标题，请设置某一静态行（该静态行是 tablix 数据区域定义一部分）的 tablix 成员的属性。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-165">To repeat or freeze column headings, set properties on the tablix member for static row that is part of the tablix data region definition.</span></span> <span data-ttu-id="ef3b3-166">若要选择静态行，必须使用“分组”窗格的高级模式。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-166">To select the static row, you must use the Advanced mode of the Grouping pane.</span></span> <span data-ttu-id="ef3b3-167">下图显示的是“行组”窗格：</span><span class="sxs-lookup"><span data-stu-id="ef3b3-167">The following figure shows the Row Groups pane:</span></span>

 <span data-ttu-id="ef3b3-168">![“行组”窗格：包含一个静态行和一个动态行的表](../media/rs-tableheaderstaticgroupingpanedefault.gif "“行组”窗格：包含一个静态行和一个动态行的表")</span><span class="sxs-lookup"><span data-stu-id="ef3b3-168">![Row Groups, table with 1 static, 1 dynamic row](../media/rs-tableheaderstaticgroupingpanedefault.gif "Row Groups, table with 1 static, 1 dynamic row")</span></span>

 <span data-ttu-id="ef3b3-169">在高级模式中，下图显示了表中行组的静态 tablix 成员和动态 tablix 成员：</span><span class="sxs-lookup"><span data-stu-id="ef3b3-169">In Advanced mode, the following figure shows the static and dynamic tablix members for the row groups in the table:</span></span>

 <span data-ttu-id="ef3b3-170">![“行组”窗格：默认表的高级模式](../media/rs-tableheaderstaticgroupingpaneadvanced.gif "“行组”窗格：默认表的高级模式")</span><span class="sxs-lookup"><span data-stu-id="ef3b3-170">![Row Groups, Advanced for default table](../media/rs-tableheaderstaticgroupingpaneadvanced.gif "Row Groups, Advanced for default table")</span></span>

 <span data-ttu-id="ef3b3-171">若要重复或冻结 tablix 成员的列标题，请选择已标记 (**Static**) 的静态行。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-171">To repeat or freeze column headings for the tablix member, select the static row that is labeled (**Static**).</span></span> <span data-ttu-id="ef3b3-172">“属性”窗格将显示所选 tablix 成员的属性。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-172">The properties pane displays the properties for the selected tablix member.</span></span> <span data-ttu-id="ef3b3-173">通过设置此 tablix 成员的属性，您可以控制如何重复或始终显示第一行。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-173">By setting properties for this tablix member, you can control how the first row repeats or stays in view.</span></span>

 [<span data-ttu-id="ef3b3-174">返回页首</span><span class="sxs-lookup"><span data-stu-id="ef3b3-174">Return to top</span></span>](#Top)

###  <a name="table-with-row-groups-and-a-row-group-area"></a><a name="TableRowGroupsGroupHeader"></a><span data-ttu-id="ef3b3-175">具有行组和行组区域的表</span><span class="sxs-lookup"><span data-stu-id="ef3b3-175">Table with row groups and a row group area</span></span>
 <span data-ttu-id="ef3b3-176">如果向简单表中添加行组，将向设计图面上的表添加一个行组区域。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-176">If you add a row group to a simple table, a row group area is added to the table on the design surface.</span></span> <span data-ttu-id="ef3b3-177">下图显示的表具有一个基于 Category 的行组：</span><span class="sxs-lookup"><span data-stu-id="ef3b3-177">The following figure shows a table with a row group that is based on Category:</span></span>

 <span data-ttu-id="ef3b3-178">![“设计”窗格：包含一个行组和详细信息的表](../media/rs-tableheaderdynamicwithgroupheadercelldesign.gif "“设计”窗格：包含一个行组和详细信息的表")</span><span class="sxs-lookup"><span data-stu-id="ef3b3-178">![Design, table with one row group and details](../media/rs-tableheaderdynamicwithgroupheadercelldesign.gif "Design, table with one row group and details")</span></span>

 <span data-ttu-id="ef3b3-179">虚线显示 tablix 行组区和 tablix 正文区。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-179">The dotted lines show the tablix row groups area and the tablix body area.</span></span> <span data-ttu-id="ef3b3-180">行组区有行组头，但没有列组头。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-180">The row group area has a row group header but no column group header.</span></span> <span data-ttu-id="ef3b3-181">下图在预览中显示此表：</span><span class="sxs-lookup"><span data-stu-id="ef3b3-181">The following figure shows this table in preview:</span></span>

 <span data-ttu-id="ef3b3-182">![“预览”窗格：包含一个行组和详细信息的表](../media/rs-tableheaderdynamicwithgroupheadercellpreview.gif "“预览”窗格：包含一个行组和详细信息的表")</span><span class="sxs-lookup"><span data-stu-id="ef3b3-182">![Preview, table with one row group and details](../media/rs-tableheaderdynamicwithgroupheadercellpreview.gif "Preview, table with one row group and details")</span></span>

 <span data-ttu-id="ef3b3-183">若要重复或冻结列标题，请使用前面示例中的相同方法。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-183">To repeat or freeze column headings, use the same approach as the previous example.</span></span> <span data-ttu-id="ef3b3-184">下图显示“行组”窗格的默认视图：</span><span class="sxs-lookup"><span data-stu-id="ef3b3-184">The following figure shows the default view of the Row Groups pane:</span></span>

 <span data-ttu-id="ef3b3-185">![“行组”窗格：包含动态成员的默认视图](../media/rs-tableheaderdynamicgroupingpanedefault.gif "“行组”窗格：包含动态成员的默认视图")</span><span class="sxs-lookup"><span data-stu-id="ef3b3-185">![Row Groups, Default with dynamic members](../media/rs-tableheaderdynamicgroupingpanedefault.gif "Row Groups, Default with dynamic members")</span></span>

 <span data-ttu-id="ef3b3-186">使用“行组”窗格的 **“高级”** 模式显示 tablix 成员，如下图所示：</span><span class="sxs-lookup"><span data-stu-id="ef3b3-186">Use the **Advanced** mode of the Row Groups pane to display the tablix members, as shown in the following figure:</span></span>

 <span data-ttu-id="ef3b3-187">![“行组”窗格：包含静态成员的高级模式](../media/rs-tableheaderdynamicwithgroupheadercelladvanced.gif "“行组”窗格：包含静态成员的高级模式")</span><span class="sxs-lookup"><span data-stu-id="ef3b3-187">![Row Groups, Advanced mode with static members](../media/rs-tableheaderdynamicwithgroupheadercelladvanced.gif "Row Groups, Advanced mode with static members")</span></span>

 <span data-ttu-id="ef3b3-188">列出的 tablix 成员包括： **Static**、(**Static**)、Category 和 (**Details**)。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-188">For tablix members are listed: **Static**, (**Static**), Category, and (**Details**).</span></span> <span data-ttu-id="ef3b3-189">带有括号 () 的 tablix 成员指示没有相应的组头。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-189">A tablix member that includes parentheses () indicates that there is no corresponding group header.</span></span> <span data-ttu-id="ef3b3-190">若要重复或冻结列标题，请选择上面的 Static tablix 成员，然后在“属性”窗格中设置属性。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-190">To repeat or freeze column headings, select the top Static tablix member, and set properties in the Properties pane.</span></span>

 [<span data-ttu-id="ef3b3-191">返回页首</span><span class="sxs-lookup"><span data-stu-id="ef3b3-191">Return to top</span></span>](#Top)

###  <a name="table-with-row-groups-and-no-row-group-area"></a><a name="TableRowGroupsNoGroupHeader"></a><span data-ttu-id="ef3b3-192">具有行组但没有行组区域的表</span><span class="sxs-lookup"><span data-stu-id="ef3b3-192">Table with row groups and no row group area</span></span>
 <span data-ttu-id="ef3b3-193">在很多情况下，表可能具有行组但没有行组区域。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-193">A table can have row groups but no row groups area in several ways.</span></span> <span data-ttu-id="ef3b3-194">其中的两种情况为：</span><span class="sxs-lookup"><span data-stu-id="ef3b3-194">Two possible ways for this to happen include:</span></span>

-   <span data-ttu-id="ef3b3-195">开始时表具有行组和行组区域，后来删除了行组区域的列。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-195">Start with a table with row groups and a row group area and delete the columns for the row group area.</span></span> <span data-ttu-id="ef3b3-196">仅删除列而不是组。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-196">Delete the columns only and not the groups.</span></span> <span data-ttu-id="ef3b3-197">例如，您可能想将表格式控制为简单网格。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-197">For example, you might want to control the table format to be a simple grid.</span></span>

-   <span data-ttu-id="ef3b3-198">升级为早期 RDL 版本（引入 tablix 数据区域之前）创建的报表。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-198">Upgrade a report that was created for a previous RDL version, before tablix data regions were introduced.</span></span>

 <span data-ttu-id="ef3b3-199">下图所示的表在设计图面上具有行组但没有行组区域：</span><span class="sxs-lookup"><span data-stu-id="ef3b3-199">The following figure shows a table with a row group but no row group area on the design surface:</span></span>

 <span data-ttu-id="ef3b3-200">![“设计”窗格：包含行组但无组标头的表](../media/rs-tableheaderdynamicwithnogroupheadercelldesign.gif "“设计”窗格：包含行组但无组标头的表")</span><span class="sxs-lookup"><span data-stu-id="ef3b3-200">![Design, table has row group but no group header](../media/rs-tableheaderdynamicwithnogroupheadercelldesign.gif "Design, table has row group but no group header")</span></span>

 <span data-ttu-id="ef3b3-201">该表有三行。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-201">The table has three rows.</span></span> <span data-ttu-id="ef3b3-202">第一行包含列标题。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-202">The first row contains column headers.</span></span> <span data-ttu-id="ef3b3-203">第二行包含组值和小计。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-203">The second row contains the group value and subtotals.</span></span> <span data-ttu-id="ef3b3-204">第三行包含详细信息数据。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-204">The third row contains the detail data.</span></span> <span data-ttu-id="ef3b3-205">因为只有 tablix 正文区，所以没有虚线。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-205">There are no dotted lines because there is only a tablix body area.</span></span> <span data-ttu-id="ef3b3-206">下图在预览中显示此表：</span><span class="sxs-lookup"><span data-stu-id="ef3b3-206">The following figure shows this table in preview:</span></span>

 <span data-ttu-id="ef3b3-207">![“预览”窗格：包含行组但无组标头的表](../media/rs-tableheaderdynamicwithnogroupheadercellpreview.gif "“预览”窗格：包含行组但无组标头的表")</span><span class="sxs-lookup"><span data-stu-id="ef3b3-207">![Preview, table has row group but no group header](../media/rs-tableheaderdynamicwithnogroupheadercellpreview.gif "Preview, table has row group but no group header")</span></span>

 <span data-ttu-id="ef3b3-208">若要控制如何重复或始终显示行，必须设置每一行 tablix 成员的属性。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-208">To control how the rows repeat or stay in view, you must set properties on the tablix member for each row.</span></span> <span data-ttu-id="ef3b3-209">在默认模式下，此示例与具有行组和组头的表的上一示例没有差别。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-209">In default mode, there is no difference between this example and the previous example for a table with a row group and a group header.</span></span> <span data-ttu-id="ef3b3-210">下图显示的是默认模式下此表的“分组”窗格：</span><span class="sxs-lookup"><span data-stu-id="ef3b3-210">The following figure shows the Grouping pane in default mode for this table:</span></span>

 <span data-ttu-id="ef3b3-211">![“行组”窗格：包含动态成员的默认视图](../media/rs-tableheaderdynamicgroupingpanedefault.gif "“行组”窗格：包含动态成员的默认视图")</span><span class="sxs-lookup"><span data-stu-id="ef3b3-211">![Row Groups, Default with dynamic members](../media/rs-tableheaderdynamicgroupingpanedefault.gif "Row Groups, Default with dynamic members")</span></span>

 <span data-ttu-id="ef3b3-212">但是，在高级模式中，此布局结构显示一组不同的 tablix 成员。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-212">However, in advanced mode, this layout structure shows a different set of tablix members.</span></span> <span data-ttu-id="ef3b3-213">下图显示的是高级模式中此表的“分组”窗格：</span><span class="sxs-lookup"><span data-stu-id="ef3b3-213">The following figure shows the Grouping pane in advanced mode for this table:</span></span>

 <span data-ttu-id="ef3b3-214">![“行组”窗格：不含组标头的高级模式。](../media/rs-tableheaderdynamicwithnogroupheadercelladvanced.gif "“行组”窗格：不含组标头的高级模式。")</span><span class="sxs-lookup"><span data-stu-id="ef3b3-214">![Row Groups, Advanced, no group header.](../media/rs-tableheaderdynamicwithnogroupheadercelladvanced.gif "Row Groups, Advanced, no group header.")</span></span>

 <span data-ttu-id="ef3b3-215">在“行组”窗格中列出了以下 tablix 成员：(**Static**)、(Category)、(**Static**) 和 (**Details**)。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-215">In the Row Groups pane, the following tablix members are listed: (**Static**), (Category), (**Static**), and (**Details**).</span></span> <span data-ttu-id="ef3b3-216">若要重复或冻结列标题，请选择上面的 (**Static**) tablix 成员，然后在“属性”窗格中设置属性。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-216">To repeat or freeze column headings, select the top (**Static**) tablix member, and set properties in the Properties pane.</span></span>

 [<span data-ttu-id="ef3b3-217">返回页首</span><span class="sxs-lookup"><span data-stu-id="ef3b3-217">Return to top</span></span>](#Top)

## <a name="renderer-support-for-repeating-or-freezing-headers"></a><span data-ttu-id="ef3b3-218">呈现器对重复或冻结标题的支持</span><span class="sxs-lookup"><span data-stu-id="ef3b3-218">Renderer Support for Repeating or Freezing Headers</span></span>
 <span data-ttu-id="ef3b3-219">不同呈现器对重复或冻结标题的支持有所不同。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-219">Renderers vary in support for repeating or freezing headers.</span></span>

 <span data-ttu-id="ef3b3-220">使用物理页（PDF、图像和打印稿）的呈现器支持以下功能：</span><span class="sxs-lookup"><span data-stu-id="ef3b3-220">Renderers that use physical pages (PDF, Image, Print) support the following features:</span></span>

-   <span data-ttu-id="ef3b3-221">当 tablix 数据区域跨多页水平扩展时，重复行标题。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-221">Repeat row headers when a tablix data region expands horizontally across multiple pages.</span></span>

-   <span data-ttu-id="ef3b3-222">当 tablix 数据区域跨多页垂直扩展时，重复列标题。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-222">Repeat column headers when a tablix data region expands vertically down multiple pages.</span></span>

 <span data-ttu-id="ef3b3-223">此外，使用软分页符（报表管理器、报表预览或报表查看器控件）的呈现器支持以下功能：</span><span class="sxs-lookup"><span data-stu-id="ef3b3-223">In addition, renderers that use soft page breaks (Report Manager, report preview, or the report viewer control) support the following features:</span></span>

-   <span data-ttu-id="ef3b3-224">当您水平滚动报表时，始终显示行标题。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-224">Keep row headers in view when you scroll horizontally across a report.</span></span>

-   <span data-ttu-id="ef3b3-225">当您向下滚动报表时，始终显示列标题。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-225">Keep column headers in view when you scroll vertically down a report.</span></span>

 <span data-ttu-id="ef3b3-226">有关详细信息，请参阅[呈现行为（报表生成器和 SSRS）](rendering-behaviors-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="ef3b3-226">For more information, see [Rendering Behaviors &#40;Report Builder  and SSRS&#41;](rendering-behaviors-report-builder-and-ssrs.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ef3b3-227">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ef3b3-227">See Also</span></span>
 <span data-ttu-id="ef3b3-228">[对数据进行筛选、分组和排序 &#40;报表生成器和 ssrs&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md) [列表 &#40;报表生成器](tables-matrices-and-lists-report-builder-and-ssrs.md)和 ssrs&#41;Reporting Services &#40;[和 ssrs 报表生成器](pagination-in-reporting-services-report-builder-and-ssrs.md)[导出报表&#41;&#40;和 ssrs](../report-builder/export-reports-report-builder-and-ssrs.md)报表生成器</span><span class="sxs-lookup"><span data-stu-id="ef3b3-228">[Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md) [Lists &#40;Report Builder and SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md) [Pagination in Reporting Services &#40;Report Builder  and SSRS&#41;](pagination-in-reporting-services-report-builder-and-ssrs.md) [Exporting Reports &#40;Report Builder and SSRS&#41;](../report-builder/export-reports-report-builder-and-ssrs.md)</span></span>


