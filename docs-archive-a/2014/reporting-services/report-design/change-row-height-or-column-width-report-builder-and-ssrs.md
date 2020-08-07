---
title: 更改行高或列宽（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f061c204-5cd5-4467-9a9c-8a12803d93ba
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b5d75a8101d07d7d6e81c624d08cd951277936eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588913"
---
# <a name="change-row-height-or-column-width-report-builder-and-ssrs"></a><span data-ttu-id="03906-102">更改行高或列宽（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="03906-102">Change Row Height or Column Width (Report Builder and SSRS)</span></span>
  <span data-ttu-id="03906-103">设置行高时，您所指定的是呈现的报表中行的最大高度。</span><span class="sxs-lookup"><span data-stu-id="03906-103">When you set a row height, you are specifying the maximum height for the row in the rendered report.</span></span> <span data-ttu-id="03906-104">但默认情况下，行中的文本框设置为可在运行时沿垂直方向增长，以容纳其中的数据，这会使行超过您指定的高度。</span><span class="sxs-lookup"><span data-stu-id="03906-104">However, by default, text boxes in the row are set to grow vertically to accommodate their data at run-time, and this can cause a row to expand beyond the height that you specify.</span></span> <span data-ttu-id="03906-105">若要设置固定行高，您必须更改文本框的属性，使其不会自动增高。</span><span class="sxs-lookup"><span data-stu-id="03906-105">To set a fixed row height, you must change the text box properties so they do not automatically expand.</span></span>  
  
 <span data-ttu-id="03906-106">设置列宽时，您所指定的是呈现的报表中列的最大宽度。</span><span class="sxs-lookup"><span data-stu-id="03906-106">When you set a column width, you are specifying the maximum width for the column in the rendered report.</span></span> <span data-ttu-id="03906-107">列不会自动进行水平调整来容纳文本。</span><span class="sxs-lookup"><span data-stu-id="03906-107">Columns do not automatically adjust horizontally to accommodate text.</span></span>  
  
 <span data-ttu-id="03906-108">如果行或列中的单元格包含矩形或数据区域，则单元格的最小高度和宽度将由所含项的高度和宽度决定。</span><span class="sxs-lookup"><span data-stu-id="03906-108">If a cell in a row or column contains a rectangle or data region, the minimum height and width of the cell is determined by the height and width of the contained item.</span></span> <span data-ttu-id="03906-109">有关详细信息，请参阅[呈现行为（报表生成器和 SSRS）](rendering-behaviors-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="03906-109">For more information, see [Rendering Behaviors &#40;Report Builder  and SSRS&#41;](rendering-behaviors-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-change-row-height-by-moving-row-handles"></a><span data-ttu-id="03906-110">通过移动行控点来更改行高</span><span class="sxs-lookup"><span data-stu-id="03906-110">To change row height by moving row handles</span></span>  
  
1.  <span data-ttu-id="03906-111">在“设计”视图中，单击 Tablix 数据区域中的任何位置以选中该区域。</span><span class="sxs-lookup"><span data-stu-id="03906-111">In Design view, click anywhere in the tablix data region to select it.</span></span> <span data-ttu-id="03906-112">Tablix 数据区域的外边框上将会出现灰色的行控点。</span><span class="sxs-lookup"><span data-stu-id="03906-112">Gray row handles appear on the outside border of the tablix data region.</span></span>  
  
2.  <span data-ttu-id="03906-113">将鼠标悬停于要拉伸的行控点边缘上。</span><span class="sxs-lookup"><span data-stu-id="03906-113">Hover over the row handle edge that you want to expand.</span></span> <span data-ttu-id="03906-114">此时将会出现一个双向箭头。</span><span class="sxs-lookup"><span data-stu-id="03906-114">A double-headed arrow appears.</span></span>  
  
3.  <span data-ttu-id="03906-115">单击以抓住行边缘，然后向上或向下移动行边缘，从而调整行高。</span><span class="sxs-lookup"><span data-stu-id="03906-115">Click to grab the edge of the row and move it higher or lower to adjust the row height.</span></span>  
  
### <a name="to-change-row-height-by-setting-cell-properties"></a><span data-ttu-id="03906-116">通过设置单元属性来更改行高</span><span class="sxs-lookup"><span data-stu-id="03906-116">To change row height by setting cell properties</span></span>  
  
1.  <span data-ttu-id="03906-117">在设计视图中，单击表行中的单元。</span><span class="sxs-lookup"><span data-stu-id="03906-117">In Design view, click a cell in the table row.</span></span>  
  
     <span data-ttu-id="03906-118">![表中的已选单元](../media/table-selectcell.png "表中的已选单元")</span><span class="sxs-lookup"><span data-stu-id="03906-118">![Selected Cell in a Table](../media/table-selectcell.png "Selected Cell in a Table")</span></span>  
  
2.  <span data-ttu-id="03906-119">在显示的“属性”  窗格中，修改“高度”  属性，然后单击“属性”  窗格外部的任意位置。</span><span class="sxs-lookup"><span data-stu-id="03906-119">In the **Properties** pane that displays, modify the **Height** property, and then click anywhere outside the **Properties** pane.</span></span>  
  
     <span data-ttu-id="03906-120">![所选表单元的“属性”窗格](../media/cell-propertiespane.png "所选表单元的“属性”窗格")</span><span class="sxs-lookup"><span data-stu-id="03906-120">![Properties Pane for selected table cell](../media/cell-propertiespane.png "Properties Pane for selected table cell")</span></span>  
  
### <a name="to-prevent-a-row-from-automatically-expanding-vertically"></a><span data-ttu-id="03906-121">防止行自动垂直增高</span><span class="sxs-lookup"><span data-stu-id="03906-121">To prevent a row from automatically expanding vertically</span></span>  
  
1.  <span data-ttu-id="03906-122">在“设计”视图中，单击 Tablix 数据区域中的任何位置以选中该区域。</span><span class="sxs-lookup"><span data-stu-id="03906-122">In Design view, click anywhere in the tablix data region to select it.</span></span> <span data-ttu-id="03906-123">Tablix 数据区域的外边框上将会出现灰色的行控点。</span><span class="sxs-lookup"><span data-stu-id="03906-123">Gray row handles appear on the outside border of the tablix data region.</span></span>  
  
2.  <span data-ttu-id="03906-124">单击行控点以选中行。</span><span class="sxs-lookup"><span data-stu-id="03906-124">Click the row handle to select the row.</span></span>  
  
3.  <span data-ttu-id="03906-125">在“属性”窗格中，将 CanGrow 设置为 **False**。</span><span class="sxs-lookup"><span data-stu-id="03906-125">In the Properties pane, set CanGrow to **False**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="03906-126">如果没有看到“属性”窗格，请单击“视图”菜单上的“属性”   。</span><span class="sxs-lookup"><span data-stu-id="03906-126">If you cannot see the Properties pane, from the **View** menu, click **Properties**.</span></span>  
  
### <a name="to-change-column-width"></a><span data-ttu-id="03906-127">更改列宽</span><span class="sxs-lookup"><span data-stu-id="03906-127">To change column width</span></span>  
  
1.  <span data-ttu-id="03906-128">在“设计”视图中，单击 Tablix 数据区域中的任何位置以选中该区域。</span><span class="sxs-lookup"><span data-stu-id="03906-128">In Design view, click anywhere in the tablix data region to select it.</span></span> <span data-ttu-id="03906-129">Tablix 数据区域的外边框上将会出现灰色的列控点。</span><span class="sxs-lookup"><span data-stu-id="03906-129">Gray column handles appear on the outside border of the tablix data region.</span></span>  
  
2.  <span data-ttu-id="03906-130">将鼠标悬停于要拉伸的列控点边缘上。</span><span class="sxs-lookup"><span data-stu-id="03906-130">Hover over the column handle edge that you want to expand.</span></span> <span data-ttu-id="03906-131">此时将会出现一个双向箭头。</span><span class="sxs-lookup"><span data-stu-id="03906-131">A double-headed arrow appears.</span></span>  
  
3.  <span data-ttu-id="03906-132">单击以抓住列边缘，然后向左或向右移动列边缘，从而调整列宽。</span><span class="sxs-lookup"><span data-stu-id="03906-132">Click to grab the edge of the column and move it left or right to adjust the column width.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03906-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="03906-133">See Also</span></span>  
 <span data-ttu-id="03906-134">[Tablix 数据区域 &#40;报表生成器和 SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="03906-134">[Tablix Data Region &#40;Report Builder and SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="03906-135">[Tablix 数据区域单元、行和列 &#40;报表生成器&#41; 和 SSRS](tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="03906-135">[Tablix Data Region Cells, Rows, and Columns &#40;Report Builder&#41; and SSRS](tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="03906-136">[表 &#40;报表生成器和 SSRS&#41;](tables-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="03906-136">[Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="03906-137">[矩阵 &#40;报表生成器和 SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="03906-137">[Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="03906-138">[列出 &#40;报表生成器和 SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="03906-138">[Lists &#40;Report Builder and SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="03906-139">表、矩阵和列表（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="03906-139">Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;</span></span>](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
