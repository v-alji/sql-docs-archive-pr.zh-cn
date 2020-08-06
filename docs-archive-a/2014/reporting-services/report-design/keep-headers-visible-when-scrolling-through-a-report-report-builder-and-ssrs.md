---
title: 在滚动报表时保持标题可见（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 6d9192a4-fd5c-41ad-b9ef-f88f9496afed
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d37fcd38a402dc0f88ac002c679c1046d5b0b583
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692706"
---
# <a name="keep-headers-visible-when-scrolling-through-a-report-report-builder-and-ssrs"></a><span data-ttu-id="aca8d-102">在滚动报表时保持标题可见（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="aca8d-102">Keep Headers Visible When Scrolling Through a Report (Report Builder and SSRS)</span></span>
  <span data-ttu-id="aca8d-103">呈现报表之后，为防止行和列标签滚动出视野之外，可以冻结行或列标题。</span><span class="sxs-lookup"><span data-stu-id="aca8d-103">To prevent row and column labels from scrolling out of view after rendering a report, you can freeze the row or column headings.</span></span>  
  
 <span data-ttu-id="aca8d-104">控制行和列的方式取决于您是拥有表还是矩阵。</span><span class="sxs-lookup"><span data-stu-id="aca8d-104">How you control the rows and columns depends on whether you have a table or a matrix.</span></span> <span data-ttu-id="aca8d-105">如果您拥有表，则将静态成员（行标题和列标题）配置为保持可见。</span><span class="sxs-lookup"><span data-stu-id="aca8d-105">If you have a table, you configure static members (row and column headings) to remain visible.</span></span> <span data-ttu-id="aca8d-106">如果您拥有矩阵，则将行组头和列组头配置为保持可见。</span><span class="sxs-lookup"><span data-stu-id="aca8d-106">If you have a matrix, you configure row and column group headers to remain visible.</span></span>  
  
 <span data-ttu-id="aca8d-107">如果将报表导出到 Excel，则不会自动冻结标头。</span><span class="sxs-lookup"><span data-stu-id="aca8d-107">If you export the report to Excel, the header will not be frozen automatically.</span></span> <span data-ttu-id="aca8d-108">可以冻结 Excel 中的窗格。</span><span class="sxs-lookup"><span data-stu-id="aca8d-108">You can freeze the pane in Excel.</span></span> <span data-ttu-id="aca8d-109">有关详细信息，请参阅[导出到 Microsoft Excel（报表生成器和 SSRS）](../report-builder/exporting-to-microsoft-excel-report-builder-and-ssrs.md)的“页眉和页脚”节。</span><span class="sxs-lookup"><span data-stu-id="aca8d-109">For more information see the **Page Headers and Footers** section of [Exporting to Microsoft Excel &#40;Report Builder and SSRS&#41;](../report-builder/exporting-to-microsoft-excel-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="aca8d-110">即使表拥有行组和列组，也不能使这些组头在滚动时保持可见</span><span class="sxs-lookup"><span data-stu-id="aca8d-110">Even if a table has row and column groups, you cannot keep those group headers visible while scrolling</span></span>  
  
 <span data-ttu-id="aca8d-111">下图显示了一个表。</span><span class="sxs-lookup"><span data-stu-id="aca8d-111">The following image shows a table.</span></span>  
  
 <span data-ttu-id="aca8d-112">![表](../media/table.png "表")</span><span class="sxs-lookup"><span data-stu-id="aca8d-112">![Table](../media/table.png "Table")</span></span>  
  
 <span data-ttu-id="aca8d-113">下图显示了一个矩阵。</span><span class="sxs-lookup"><span data-stu-id="aca8d-113">The following image shows a matrix.</span></span>  
  
 <span data-ttu-id="aca8d-114">![矩阵](../media/matrix.png "矩阵")</span><span class="sxs-lookup"><span data-stu-id="aca8d-114">![Matrix](../media/matrix.png "Matrix")</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-keep-matrix-group-headers-visible-while-scrolling"></a><span data-ttu-id="aca8d-115">使矩阵组头在滚动时保持可见</span><span class="sxs-lookup"><span data-stu-id="aca8d-115">To keep matrix group headers visible while scrolling</span></span>  
  
1.  <span data-ttu-id="aca8d-116">右键单击 Tablix 数据区域的行控点、列控点或角部控点，然后单击 **“Tablix 属性”** 。</span><span class="sxs-lookup"><span data-stu-id="aca8d-116">Right-click the row, column, or corner handle of a tablix data region, and then click **Tablix Properties**.</span></span>  
  
2.  <span data-ttu-id="aca8d-117">在 **“常规”** 选项卡上的 **“行标题”** 或 **“列标题”** 下选择 **“滚动时标题应保持可见”** 。</span><span class="sxs-lookup"><span data-stu-id="aca8d-117">On the **General** tab, under **Row Headers** or **Column Headers**, select **Header should remain visible while scrolling**.</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-keep-a-static-tablix-member-row-or-column-visible-while-scrolling"></a><span data-ttu-id="aca8d-118">滚动时保持静态 Tablix 成员（行或列）可见</span><span class="sxs-lookup"><span data-stu-id="aca8d-118">To keep a static tablix member (row or column) visible while scrolling</span></span>  
  
1.  <span data-ttu-id="aca8d-119">在设计图面上，单击表中任意位置，可在分组窗格中显示静态成员及组。</span><span class="sxs-lookup"><span data-stu-id="aca8d-119">On the design surface, click anywhere in the table to display static members, as well as groups, in the grouping pane.</span></span>  
  
     <span data-ttu-id="aca8d-120">![分组窗格](../media/grouppane-updated.png "分组窗格")</span><span class="sxs-lookup"><span data-stu-id="aca8d-120">![Grouping pane](../media/grouppane-updated.png "Grouping pane")</span></span>  
  
     <span data-ttu-id="aca8d-121">“行组”窗格显示行组层次结构的层次结构静态和动态成员，而“列组”窗格显示列组层次结构的相同内容。</span><span class="sxs-lookup"><span data-stu-id="aca8d-121">The Row Groups pane displays the hierarchical static and dynamic members for the row groups hierarchy, and the Column groups pane shows a similar display for the column groups hierarchy.</span></span>  
  
2.  <span data-ttu-id="aca8d-122">在“分组”窗格的右侧，单击下箭头，然后单击 **“高级模式”** 。</span><span class="sxs-lookup"><span data-stu-id="aca8d-122">On the right side of the grouping pane, click the down arrow, and then click **Advanced Mode**.</span></span>  
  
3.  <span data-ttu-id="aca8d-123">单击要在滚动时保持可见的静态成员（行或列）。</span><span class="sxs-lookup"><span data-stu-id="aca8d-123">Click the static member (row or column) that you want to remain visible while scrolling.</span></span> <span data-ttu-id="aca8d-124">“属性”窗格显示 **“Tablix 成员”** 属性。</span><span class="sxs-lookup"><span data-stu-id="aca8d-124">The Properties pane displays the **Tablix Member** properties.</span></span>  
  
     <span data-ttu-id="aca8d-125">![Tablix 成员属性](../media/grouppane-tablixmember-updated.png "Tablix 成员属性")</span><span class="sxs-lookup"><span data-stu-id="aca8d-125">![Tablix Member properties](../media/grouppane-tablixmember-updated.png "Tablix Member properties")</span></span>  
  
4.  <span data-ttu-id="aca8d-126">在 "属性" 窗格中，将**FixedData**设置为 `True` 。</span><span class="sxs-lookup"><span data-stu-id="aca8d-126">In the Properties pane, set **FixedData** to `True`.</span></span>  
  
5.  <span data-ttu-id="aca8d-127">对所有要在滚动时保持可见的相邻成员重复此过程。</span><span class="sxs-lookup"><span data-stu-id="aca8d-127">Repeat this for as many adjacent members as you want to keep visible while scrolling.</span></span>  
  
6.  <span data-ttu-id="aca8d-128">预览报表。</span><span class="sxs-lookup"><span data-stu-id="aca8d-128">Preview the report.</span></span>  
  
 <span data-ttu-id="aca8d-129">对报表翻页或横向移动时，静态 Tablix 成员仍将可见。</span><span class="sxs-lookup"><span data-stu-id="aca8d-129">As you page down or across the report, the static tablix members remain in view.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aca8d-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="aca8d-130">See Also</span></span>  
 <span data-ttu-id="aca8d-131">[Tablix 数据区域（报表生成器和 SSRS）](../tablix-data-region-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="aca8d-131">[Tablix Data Region &#40;Report Builder and SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="aca8d-132">[查找、查看和管理报表（报表生成器和 SSRS）](../report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="aca8d-132">[Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;](../report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="aca8d-133">[导出报表 &#40;报表生成器和 SSRS&#41;](../report-builder/export-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="aca8d-133">[Exporting Reports &#40;Report Builder and SSRS&#41;](../report-builder/export-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="aca8d-134">[与组一起显示组头和组尾（报表生成器和 SSRS）](display-headers-and-footers-with-a-group-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="aca8d-134">[Display Headers and Footers with a Group &#40;Report Builder and SSRS&#41;](display-headers-and-footers-with-a-group-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="aca8d-135">[在多个页中显示行标题和列标题（报表生成器和 SSRS）](display-row-and-column-headers-on-multiple-pages-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="aca8d-135">[Display Row and Column Headers on Multiple Pages &#40;Report Builder and SSRS&#41;](display-row-and-column-headers-on-multiple-pages-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="aca8d-136">“分组”窗格（报表生成器）</span><span class="sxs-lookup"><span data-stu-id="aca8d-136">Grouping Pane &#40;Report Builder&#41;</span></span>](grouping-pane-report-builder.md)  
  
  
