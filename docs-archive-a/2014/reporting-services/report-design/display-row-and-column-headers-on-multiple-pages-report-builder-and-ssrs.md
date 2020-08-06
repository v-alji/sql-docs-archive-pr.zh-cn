---
title: 在多个页中显示行标题和列标题（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 2422b1e2-822f-4379-9d7f-9afebb350e3f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2e3b38aa0faab267a0cd71feafe600829237b55c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691619"
---
# <a name="display-row-and-column-headers-on-multiple-pages-report-builder-and-ssrs"></a><span data-ttu-id="5c0e1-102">在多个页中显示行标题和列标题（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="5c0e1-102">Display Row and Column Headers on Multiple Pages (Report Builder and SSRS)</span></span>
  <span data-ttu-id="5c0e1-103">您可以控制在跨越多个页的 Tablix 数据区域的每个页上是否重复行标题和列标题。</span><span class="sxs-lookup"><span data-stu-id="5c0e1-103">You can control whether to repeat row and column headers on every page for a tablix data region that spans multiple pages.</span></span> <span data-ttu-id="5c0e1-104">Tablix 数据区域可以是一个表、矩阵或列表。</span><span class="sxs-lookup"><span data-stu-id="5c0e1-104">A tablix data region can be a table, matrix, or list.</span></span>  
  
 <span data-ttu-id="5c0e1-105">控制行和列的方式取决于 Tablix 数据区域是否具有组头。</span><span class="sxs-lookup"><span data-stu-id="5c0e1-105">How you control the rows and columns depends on whether the tablix data region has group headers.</span></span> <span data-ttu-id="5c0e1-106">在包含组头的 Tablix 数据区域中单击时，点线将显示 Tablix 区域，如下图所示：</span><span class="sxs-lookup"><span data-stu-id="5c0e1-106">When you click in a tablix data region that has group headers, a dotted line shows the tablix areas, as shown in the following figure:</span></span>  
  
 <span data-ttu-id="5c0e1-107">![Tablix 数据区域](../media/rs-tablixareas.gif "Tablix 数据区域")</span><span class="sxs-lookup"><span data-stu-id="5c0e1-107">![Tablix data region areas](../media/rs-tablixareas.gif "Tablix data region areas")</span></span>  
  
 <span data-ttu-id="5c0e1-108">通过使用新建表或矩阵向导或者新建图表向导，向“分组”窗格添加字段或使用上下文菜单添加组时，将自动创建行组标头和列组标头。</span><span class="sxs-lookup"><span data-stu-id="5c0e1-108">Row and column group headers are created automatically when you add groups by using the New Table or Matrix wizard or the New Chart wizard, by adding fields to the Grouping pane, or by using context menus.</span></span> <span data-ttu-id="5c0e1-109">如果 Tablix 数据区域只包含 Tablix 正文区域，而没有组头，则行和列为 Tablix 成员。</span><span class="sxs-lookup"><span data-stu-id="5c0e1-109">If the tablix data region has only a tablix body area and no group headers, the rows and columns are tablix members.</span></span>  
  
 <span data-ttu-id="5c0e1-110">对于静态成员，您可以在多个页面上显示顶部相邻的行或侧面相邻的列。</span><span class="sxs-lookup"><span data-stu-id="5c0e1-110">For static members, you can display the top adjacent rows or the side adjacent columns on multiple pages.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-display-row-headers-on-multiple-pages"></a><span data-ttu-id="5c0e1-111">在多个页上显示行标题</span><span class="sxs-lookup"><span data-stu-id="5c0e1-111">To display row headers on multiple pages</span></span>  
  
1.  <span data-ttu-id="5c0e1-112">右键单击 Tablix 数据区域的行控点、列控点或角部控点，然后单击 **“Tablix 属性”** 。</span><span class="sxs-lookup"><span data-stu-id="5c0e1-112">Right-click the row, column, or corner handle of a tablix data region, and then click **Tablix Properties**.</span></span>  
  
2.  <span data-ttu-id="5c0e1-113">在 **“行标题”** 中，选择 **“在每一页上重复标题行”** 。</span><span class="sxs-lookup"><span data-stu-id="5c0e1-113">In **Row Headers**, select **Repeat header rows on each page**.</span></span>  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="to-display-column-headers-on-multiple-pages"></a><span data-ttu-id="5c0e1-114">在多个页上显示列标题</span><span class="sxs-lookup"><span data-stu-id="5c0e1-114">To display column headers on multiple pages</span></span>  
  
1.  <span data-ttu-id="5c0e1-115">右键单击 Tablix 数据区域的行控点、列控点或角部控点，然后单击 **“Tablix 属性”** 。</span><span class="sxs-lookup"><span data-stu-id="5c0e1-115">Right-click the row, column, or corner handle of a tablix data region, and then click **Tablix Properties**.</span></span>  
  
2.  <span data-ttu-id="5c0e1-116">在 **“列标题”** 中，选择 **“在每一页上重复标题列”** 。</span><span class="sxs-lookup"><span data-stu-id="5c0e1-116">In **Column Headers**, select **Repeat header columns on each page**.</span></span>  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="to-display-a-static-tablix-member-row-or-column-on-multiple-pages"></a><span data-ttu-id="5c0e1-117">在多个页面上显示静态 Tablix 成员（行或列）</span><span class="sxs-lookup"><span data-stu-id="5c0e1-117">To display a static tablix member (row or column) on multiple pages</span></span>  
  
1.  <span data-ttu-id="5c0e1-118">在设计图面上，单击 Tablix 数据区域中的行控点或列控点以将其选定。</span><span class="sxs-lookup"><span data-stu-id="5c0e1-118">On the design surface, click the row or column handle of the tablix data region to select it.</span></span> <span data-ttu-id="5c0e1-119">“分组”窗格随即显示行组和列组。</span><span class="sxs-lookup"><span data-stu-id="5c0e1-119">The Grouping pane displays the row and column groups.</span></span>  
  
2.  <span data-ttu-id="5c0e1-120">在“分组”窗格的右侧，单击下箭头，然后单击 **“高级模式”** 。</span><span class="sxs-lookup"><span data-stu-id="5c0e1-120">On the right side of the Grouping pane, click the down arrow, and then click **Advanced Mode**.</span></span> <span data-ttu-id="5c0e1-121">“行组”窗格显示行组层次结构的层次结构静态和动态成员，而“列组”窗格显示列组层次结构的相同内容。</span><span class="sxs-lookup"><span data-stu-id="5c0e1-121">The Row Groups pane displays the hierarchical static and dynamic members for the row groups hierarchy and the Column groups pane shows a similar display for the column groups hierarchy.</span></span>  
  
3.  <span data-ttu-id="5c0e1-122">单击与在滚动时要使其保持可见的静态成员（行或列）相对应的静态成员。</span><span class="sxs-lookup"><span data-stu-id="5c0e1-122">Click the static member that corresponds to the static member (row or column) that you want to remain visible while scrolling.</span></span> <span data-ttu-id="5c0e1-123">“属性”窗格显示 **“Tablix 成员”** 属性。</span><span class="sxs-lookup"><span data-stu-id="5c0e1-123">The Properties pane displays the **Tablix Member** properties.</span></span>  
  
     <span data-ttu-id="5c0e1-124">如果未显示“属性”窗格，请单击报表生成器窗口顶部的“视图”选项卡，然后单击“属性”   。</span><span class="sxs-lookup"><span data-stu-id="5c0e1-124">If you don't see the Properties pane, click the **View** tab at the top of the Report Builder window and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="5c0e1-125">在“属性”窗格中，将 **RepeatOnNewPage** 设置为 True。</span><span class="sxs-lookup"><span data-stu-id="5c0e1-125">In the Properties pane, set **RepeatOnNewPage** to True.</span></span>  
  
5.  <span data-ttu-id="5c0e1-126">将 **“KeepWithGroup”** 设为 After。</span><span class="sxs-lookup"><span data-stu-id="5c0e1-126">Set **KeepWithGroup** to After.</span></span>  
  
6.  <span data-ttu-id="5c0e1-127">为要重复此出现的任意多个相邻成员重复此步骤。</span><span class="sxs-lookup"><span data-stu-id="5c0e1-127">Repeat this for as many adjacent members as you want to repeat.</span></span>  
  
7.  <span data-ttu-id="5c0e1-128">预览报表。</span><span class="sxs-lookup"><span data-stu-id="5c0e1-128">Preview the report.</span></span>  
  
 <span data-ttu-id="5c0e1-129">当您查看 Tablix 数据区域分布的报表的每一页时，静态 Tablix 成员将在每页中重复出现。</span><span class="sxs-lookup"><span data-stu-id="5c0e1-129">As you view each page of the report that the tablix data region spans, the static tablix members repeat on each page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c0e1-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5c0e1-130">See Also</span></span>  
 <span data-ttu-id="5c0e1-131">[查找、查看和管理报表（报表生成器和 SSRS）](../report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="5c0e1-131">[Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;](../report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="5c0e1-132">[导出报表 &#40;报表生成器和 SSRS&#41;](../report-builder/export-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="5c0e1-132">[Exporting Reports &#40;Report Builder and SSRS&#41;](../report-builder/export-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="5c0e1-133">[控制分页符、标题、列和行（报表生成器和 SSRS）](controlling-page-breaks-headings-columns-and-rows-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="5c0e1-133">[Controlling Page Breaks, Headings, Columns, and Rows &#40;Report Builder and SSRS&#41;](controlling-page-breaks-headings-columns-and-rows-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="5c0e1-134">[与组一起显示组头和组尾（报表生成器和 SSRS）](display-headers-and-footers-with-a-group-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="5c0e1-134">[Display Headers and Footers with a Group &#40;Report Builder and SSRS&#41;](display-headers-and-footers-with-a-group-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="5c0e1-135">在滚动报表时保持标题可见（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="5c0e1-135">Keep Headers Visible When Scrolling Through a Report &#40;Report Builder and SSRS&#41;</span></span>](keep-headers-visible-when-scrolling-through-a-report-report-builder-and-ssrs.md)  
  
  
