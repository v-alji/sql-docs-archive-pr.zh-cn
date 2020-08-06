---
title: Tablix 数据区域（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f6c13407-2887-4287-9396-a58dba619d9b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 14d34193ee4fed796637b55bc9f34cf901e7e258
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586365"
---
# <a name="tablix-data-region-areas-report-builder-and-ssrs"></a><span data-ttu-id="85ebc-102">Tablix 数据区域（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="85ebc-102">Tablix Data Region Areas (Report Builder and SSRS)</span></span>
  <span data-ttu-id="85ebc-103">Tablix 数据区域具有四个包含 Tablix 单元的区域：角部区、行组区、列组区和正文区。</span><span class="sxs-lookup"><span data-stu-id="85ebc-103">A tablix data region has four areas that contain tablix cells: the corner, the row group area, the column group area, and the body.</span></span> <span data-ttu-id="85ebc-104">每个区域中的单元都具有不同功能。</span><span class="sxs-lookup"><span data-stu-id="85ebc-104">Cells in each area have a distinct function.</span></span> <span data-ttu-id="85ebc-105">向 Tablix 正文区添加单元可以显示详细信息数据和分组数据。</span><span class="sxs-lookup"><span data-stu-id="85ebc-105">You add cells to the tablix body area to display detail and grouped data.</span></span> <span data-ttu-id="85ebc-106">创建组时，报表生成器和报表设计器向行组区或列组区添加单元，以便显示组实例值。</span><span class="sxs-lookup"><span data-stu-id="85ebc-106">Report Builder and Report Designer add cells to the row group or column group area when you create a group in order to display group instance values.</span></span> <span data-ttu-id="85ebc-107">存在行组和列组时，报表生成器和报表设计器将创建 Tablix 角单元。</span><span class="sxs-lookup"><span data-stu-id="85ebc-107">Report Builder and Report Designer create tablix corner cells when both row groups and column groups exist.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
 <span data-ttu-id="85ebc-108">在设计图面上，用点线表示选定 Tablix 数据区域中的上述四个区域。</span><span class="sxs-lookup"><span data-stu-id="85ebc-108">On the design surface, dotted lines denote the four areas of a selected tablix data region.</span></span> <span data-ttu-id="85ebc-109">下图显示了 Tablix 区域的相应区域，该 Tablix 区域具有基于 Category 和 Subcategory 的嵌套行组、基于 Geography 和 Country/Region 的嵌套列组，以及基于 Year 的相邻列组。</span><span class="sxs-lookup"><span data-stu-id="85ebc-109">The following figure shows the areas for a tablix region with nested row groups based on category and subcategory, nested column groups based on geography and country/region, and an adjacent column group based on year.</span></span>  
  
 <span data-ttu-id="85ebc-110">![Tablix 数据区域](../media/rs-tablixareas.gif "Tablix 数据区域")</span><span class="sxs-lookup"><span data-stu-id="85ebc-110">![Tablix data region areas](../media/rs-tablixareas.gif "Tablix data region areas")</span></span>  
  
 <span data-ttu-id="85ebc-111">下表对各区域进行了说明：</span><span class="sxs-lookup"><span data-stu-id="85ebc-111">The following list describes each area:</span></span>  
  
-   <span data-ttu-id="85ebc-112">**Tablix 角部区**。</span><span class="sxs-lookup"><span data-stu-id="85ebc-112">**Tablix corner area**.</span></span> <span data-ttu-id="85ebc-113">（可选）对于从右到左 (RTL) 的布局，Tablix 角位于左上角或右上角。</span><span class="sxs-lookup"><span data-stu-id="85ebc-113">(Optional) A tablix corner is located in the upper-left corner, or upper-right corner for right-to-left (RTL) layouts.</span></span> <span data-ttu-id="85ebc-114">向 Tablix 数据区域添加行组和列组时，将自动创建该区域。</span><span class="sxs-lookup"><span data-stu-id="85ebc-114">This area is automatically created when you add both row groups and column groups to a tablix data region.</span></span> <span data-ttu-id="85ebc-115">您可以在该区域中合并多个单元，并添加标签或嵌入其他报表项。</span><span class="sxs-lookup"><span data-stu-id="85ebc-115">In this area, you can merge cells and add a label or embed another report item.</span></span> <span data-ttu-id="85ebc-116">在该图中，合并后的角单元根据 Area 和 Year 显示标签 Sales。</span><span class="sxs-lookup"><span data-stu-id="85ebc-116">In the figure, merged cells in the corner display the label Sales by Area and Year.</span></span>  
  
-   <span data-ttu-id="85ebc-117">**Tablix 列组区**。</span><span class="sxs-lookup"><span data-stu-id="85ebc-117">**Tablix column groups area**.</span></span> <span data-ttu-id="85ebc-118">（可选）Tablix 列组位于右上角（对于 RTL 布局，则位于左上角）。</span><span class="sxs-lookup"><span data-stu-id="85ebc-118">(Optional) Tablix column groups are located in the upper-right corner (upper-left corner for RTL layout).</span></span> <span data-ttu-id="85ebc-119">该区域是在添加列组时自动创建的。</span><span class="sxs-lookup"><span data-stu-id="85ebc-119">This area is automatically created when you add a column group.</span></span> <span data-ttu-id="85ebc-120">该区域中的单元表示列组层次结构的成员，并显示列组实例值。</span><span class="sxs-lookup"><span data-stu-id="85ebc-120">Cells in this area represent members of the column groups hierarchy, and display the column group instance values.</span></span> <span data-ttu-id="85ebc-121">在该图中，显示 [Geography] 和 [CountryRegion] 的单元为嵌套列组，显示 [Year] 的单元为相邻列组。</span><span class="sxs-lookup"><span data-stu-id="85ebc-121">In the figure, the cells that display [Geography] and [CountryRegion] are nested column groups, and the cell that displays [Year] is an adjacent column group.</span></span> <span data-ttu-id="85ebc-122">[Total] 列显示跨每个行的聚合总计。</span><span class="sxs-lookup"><span data-stu-id="85ebc-122">The column [Total] displays the aggregated totals across each row.</span></span>  
  
-   <span data-ttu-id="85ebc-123">**Tablix 行组区**。</span><span class="sxs-lookup"><span data-stu-id="85ebc-123">**Tablix row groups area**.</span></span> <span data-ttu-id="85ebc-124">（可选）Tablix 行组位于左下角（对于 RTL 布局，则位于右下角）。</span><span class="sxs-lookup"><span data-stu-id="85ebc-124">(Optional) Tablix row groups are located on the lower-left corner (lower right for RTL layout).</span></span> <span data-ttu-id="85ebc-125">该区域是在添加行组时自动创建的。</span><span class="sxs-lookup"><span data-stu-id="85ebc-125">This area is automatically created when you add a row group.</span></span> <span data-ttu-id="85ebc-126">该区域中的单元表示行组层次结构的成员，并显示行组实例值。</span><span class="sxs-lookup"><span data-stu-id="85ebc-126">Cells in this area represent members of the row groups hierarchy, and display row group instance values.</span></span> <span data-ttu-id="85ebc-127">在该图中，显示 [Category] 和 [Subcat] 的单元为嵌套行组。</span><span class="sxs-lookup"><span data-stu-id="85ebc-127">In the figure, the cells that display [Category] and [Subcat] are nested row groups.</span></span> <span data-ttu-id="85ebc-128">Subcat 下面的 Total 行重复每个类别组，以便显示每个列的聚合小计。</span><span class="sxs-lookup"><span data-stu-id="85ebc-128">The Total row below Subcat repeats with each category group to show the aggregated subtotals for each column.</span></span> <span data-ttu-id="85ebc-129">总计行显示所有类别的总计。</span><span class="sxs-lookup"><span data-stu-id="85ebc-129">The grand total row shows the totals for all categories.</span></span>  
  
-   <span data-ttu-id="85ebc-130">**Tablix 正文区**。</span><span class="sxs-lookup"><span data-stu-id="85ebc-130">**Tablix body area**.</span></span> <span data-ttu-id="85ebc-131">Tablix 正文位于右下角（对于 RTL 布局，则位于左下角）。</span><span class="sxs-lookup"><span data-stu-id="85ebc-131">The tablix body is located in the lower right corner (lower left for RTL layout).</span></span> <span data-ttu-id="85ebc-132">Tablix 正文显示详细信息数据和分组数据。</span><span class="sxs-lookup"><span data-stu-id="85ebc-132">The tablix body displays detail and grouped data.</span></span> <span data-ttu-id="85ebc-133">在本示例中，只使用了聚合数据。</span><span class="sxs-lookup"><span data-stu-id="85ebc-133">In this example, only aggregated data is used.</span></span> <span data-ttu-id="85ebc-134">表达式的作用域是通过文本框所属的最内部组确定的。</span><span class="sxs-lookup"><span data-stu-id="85ebc-134">The scope for the expression is determined by the innermost groups to which the text box belongs.</span></span> <span data-ttu-id="85ebc-135">当 Tablix 正文中的单元是详细信息行成员时，该单元显示详细信息数据；当该单元是与组关联的行或组的成员时，则表示聚合数据。</span><span class="sxs-lookup"><span data-stu-id="85ebc-135">Cells in the tablix body display detail data when they are members of a detail row and they represent aggregate data when they are members of a row or column associated with a group.</span></span> <span data-ttu-id="85ebc-136">默认情况下，对于组行或组列中包含不含有聚合函数的简单表达式的单元，其计算结果为组中的第一个值。</span><span class="sxs-lookup"><span data-stu-id="85ebc-136">By default, cells in a group row or column that contain simple expressions that do not include an aggregate function, evaluate to the first value in the group.</span></span> <span data-ttu-id="85ebc-137">在该图中，这些单元显示所有销售订单的行总计的聚合总计。</span><span class="sxs-lookup"><span data-stu-id="85ebc-137">In the figure, the cells display the aggregate totals for line totals for all sales order.</span></span>  
  
 <span data-ttu-id="85ebc-138">当报表运行时，列组向右扩展（如果将 Tablix 数据区域的 Direction 属性设置为 RTL，则向左扩展），组表达式有多少唯一值就扩展多少列。</span><span class="sxs-lookup"><span data-stu-id="85ebc-138">When the report runs, column groups expand right (or left, if the Direction property of the tablix data region is set to RTL) for as many columns as there are unique values for a group expression.</span></span> <span data-ttu-id="85ebc-139">行组沿页面向下扩展。</span><span class="sxs-lookup"><span data-stu-id="85ebc-139">Row groups expand down the page.</span></span> <span data-ttu-id="85ebc-140">有关详细信息，请参阅 [Tablix 数据区域单元、行和列（报表生成器和 SSRS）](tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="85ebc-140">For more information, see [Tablix Data Region Cells, Rows, and Columns &#40;Report Builder&#41; and SSRS](tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="85ebc-141">下图在预览中显示 Tablix 数据区域。</span><span class="sxs-lookup"><span data-stu-id="85ebc-141">The following figure shows the tablix data region in Preview.</span></span>  
  
 <span data-ttu-id="85ebc-142">![Tablix 角、行组和列组、正文的预览](../media/rs-tablixareaspreview.gif "Tablix 角、行组和列组、正文的预览")</span><span class="sxs-lookup"><span data-stu-id="85ebc-142">![Preview, Tablix corner, row & column groups, body](../media/rs-tablixareaspreview.gif "Preview, Tablix corner, row & column groups, body")</span></span>  
  
 <span data-ttu-id="85ebc-143">行组区显示 Clothing 和 Components 的两个类别组实例。</span><span class="sxs-lookup"><span data-stu-id="85ebc-143">The row group area displays two category group instances for Clothing and Components.</span></span> <span data-ttu-id="85ebc-144">列组显示 North America 的地理组实例，其中包括 Canada (CA) 和 United States (US) 两个嵌套国家/地区组实例。</span><span class="sxs-lookup"><span data-stu-id="85ebc-144">The column group are displays a geography group instance for North America, with two nested country/region group instances for Canada (CA) and the United States (US).</span></span> <span data-ttu-id="85ebc-145">此外，相邻列显示 2003 和 2004 的两个年份组实例。</span><span class="sxs-lookup"><span data-stu-id="85ebc-145">In addition, the adjacent column displays two year group instances for 2003 and 2004.</span></span> <span data-ttu-id="85ebc-146">Total 列显示行总计；总计 (totals) 行重复用于显示子类别总计的类别组，而总计 (grand total) 行对数据区域显示一次类别总计。</span><span class="sxs-lookup"><span data-stu-id="85ebc-146">The Total column row displays the row totals; the totals row that repeats with the category group shows subcategory totals, and the grand total row displays the category totals once for the data region.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85ebc-147">另请参阅</span><span class="sxs-lookup"><span data-stu-id="85ebc-147">See Also</span></span>  
 <span data-ttu-id="85ebc-148">[列出 &#40;报表生成器和 SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="85ebc-148">[Lists &#40;Report Builder and SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="85ebc-149">[教程 &#40;报表生成器&#41;](../report-builder-tutorials.md) </span><span class="sxs-lookup"><span data-stu-id="85ebc-149">[Tutorials &#40;Report Builder&#41;](../report-builder-tutorials.md) </span></span>  
 <span data-ttu-id="85ebc-150">[表 &#40;报表生成器和 SSRS&#41;](tables-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="85ebc-150">[Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="85ebc-151">[矩阵 &#40;报表生成器和 SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="85ebc-151">[Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="85ebc-152">[列出 &#40;报表生成器和 SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="85ebc-152">[Lists &#40;Report Builder and SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="85ebc-153">Tablix 数据区域（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="85ebc-153">Tablix Data Region &#40;Report Builder and SSRS&#41;</span></span>](../tablix-data-region-report-builder-and-ssrs.md)  
  
  