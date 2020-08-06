---
title: 向下钻取操作（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10249"
- "10186"
- sql12.rtp.rptdesigner.calculatedseriesproperties.visibility.f1
- sql12.rtp.rptdesigner.seriesproperties.visibility.f1
- sql12.rtp.rptdesigner.chartareaproperties.visibility.f1
- "10092"
- sql12.rtp.rptdesigner.textboxproperties.visibility.f1
- sql12.rtp.rptdesigner.charttitleproperties.visibility.f1
- "10167"
- sql12.rtp.rptdesigner.rectangleproperties.visibility.f1
- "10174"
- sql12.rtp.rptdesigner.majorgridlineproperties.visibility.f1
- "10155"
- "10123"
- sql12.rtp.rptdesigner.subreportproperties.visibility.f1
- "10425"
- sql12.rtp.rptdesigner.minorgridlineproperties.visibility.f1
- "10217"
- sql12.rtp.rptdesigner.axisproperties.visibility.f1
- sql12.rtp.rptdesigner.serieslabelproperties.visibility.f1
- "10161"
- sql12.rtp.rptdesigner.chartproperties.visibility.f1
- sql12.rtp.rptdesigner.legendproperties.visibility.f1
- sql12.rtp.rptdesigner.pictureproperties.visibility.f1
- "10215"
- "10258"
- "10144"
- "10062"
- "10053"
ms.assetid: 1f8d1ef2-0daf-40c6-9ba7-3b391249bcd4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2fe3d55dc70a606df759c049b7b147820f0e3110
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590055"
---
# <a name="drilldown-action-report-builder-and-ssrs"></a><span data-ttu-id="ff9de-102">深化操作（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="ff9de-102">Drilldown Action (Report Builder and SSRS)</span></span>
  <span data-ttu-id="ff9de-103">B 在文本框上提供了加号和减号图标，使用户能够以交互方式隐藏和显示项。</span><span class="sxs-lookup"><span data-stu-id="ff9de-103">B providing plus and minus icons on a text box, you can enable users to hide and display items interactively.</span></span> <span data-ttu-id="ff9de-104">这称为 *深化* 操作。</span><span class="sxs-lookup"><span data-stu-id="ff9de-104">This is called a *drilldown* action.</span></span> <span data-ttu-id="ff9de-105">对于表或矩阵，可以显示或隐藏静态行和列，或者与组关联的行和列。</span><span class="sxs-lookup"><span data-stu-id="ff9de-105">For a table or matrix, you can show or hide static rows and columns, or rows and columns that are associated with groups.</span></span>  
  
 <span data-ttu-id="ff9de-106">![rs_drilldown](../media/rs-drilldown.gif "rs_drilldown")</span><span class="sxs-lookup"><span data-stu-id="ff9de-106">![rs_drilldown](../media/rs-drilldown.gif "rs_drilldown")</span></span>  
  
 <span data-ttu-id="ff9de-107">在此图中，用户单击报表中的加号 (+) 可显示详细信息数据。</span><span class="sxs-lookup"><span data-stu-id="ff9de-107">In this illustration, the user clicks the plus signs (+) in the report to show detail data.</span></span>  
  
 <span data-ttu-id="ff9de-108">例如，对于包含行组的表，您可以一开始就隐藏除外部组摘要行之外的所有行。</span><span class="sxs-lookup"><span data-stu-id="ff9de-108">For example, you can initially hide all the rows except the outer group summary row for a table with row groups.</span></span> <span data-ttu-id="ff9de-109">对于每个内部组（包括详细信息组），可为包含组的分组单元格添加展开/折叠图标。</span><span class="sxs-lookup"><span data-stu-id="ff9de-109">For each inner group (including the details group), add an expand/collapse icon to the grouping cell of the containing group.</span></span> <span data-ttu-id="ff9de-110">当呈现出报表后，用户就可以单击该文本框来展开或折叠详细信息数据。</span><span class="sxs-lookup"><span data-stu-id="ff9de-110">When the report is rendered, the user can click the text box to expand and collapse the detail data.</span></span> <span data-ttu-id="ff9de-111">有关详细信息，请参阅[表（报表生成器和 SSRS）](tables-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="ff9de-111">For more information, see [Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="ff9de-112">若要让用户能够展开或折叠某个项，请设置该项的可见性属性。</span><span class="sxs-lookup"><span data-stu-id="ff9de-112">To allow users to expand or collapse an item, you set the visibility properties for that item.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ff9de-113">在通过深化操作创建报表时，必须对要隐藏的组、列或行设置可见性信息，而不能仅对行或列中的单个文本框设置可见性信息。</span><span class="sxs-lookup"><span data-stu-id="ff9de-113">When you create a report with a drilldown action, the visibility information must be set on the group, column, or row that you want to hide, not just a single text box in the row or column.</span></span> <span data-ttu-id="ff9de-114">此外，用于切换的文本框必须位于控制要显示或隐藏的项的包含作用域中。</span><span class="sxs-lookup"><span data-stu-id="ff9de-114">In addition, the text box that you use for the toggle must be in a containing scope that controls the item that you want to show or hide.</span></span>  
>   
>  <span data-ttu-id="ff9de-115">例如，若要隐藏与嵌套组关联的行，文本框必须位于在包容层次结构中与父组或更高层次结构关联的行中。</span><span class="sxs-lookup"><span data-stu-id="ff9de-115">For example, to hide a row associated with a nested group, the text box must be in a row associated with the parent group or higher in the containment hierarchy.</span></span>  
>   
>  <span data-ttu-id="ff9de-116">有关在组、列或行上设置可见性信息的内容，请参阅[为项添加展开或折叠操作（报表生成器和 SSRS）](add-an-expand-or-collapse-action-to-an-item-report-builder-and-ssrs.md)</span><span class="sxs-lookup"><span data-stu-id="ff9de-116">For information on setting visibility information on the group, column or row, see [Add an Expand or Collapse Action to an Item &#40;Report Builder and SSRS&#41;](add-an-expand-or-collapse-action-to-an-item-report-builder-and-ssrs.md)</span></span>  
  
 <span data-ttu-id="ff9de-117">有关隐藏报表项的详细信息，请参阅[隐藏项（报表生成器和 SSRS）](../report-builder/hide-an-item-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="ff9de-117">For more information about hiding report items, see [Hide an Item &#40;Report Builder and SSRS&#41;](../report-builder/hide-an-item-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="comparing-drilldown-and-drillthrough-reports"></a><span data-ttu-id="ff9de-118">比较明细报表和钻取报表</span><span class="sxs-lookup"><span data-stu-id="ff9de-118">Comparing Drilldown and Drillthrough Reports</span></span>  
 <span data-ttu-id="ff9de-119">在明细报表中，用户单击加号或减号按钮即可展开或折叠报表的某个部分，以显示详细信息数据。</span><span class="sxs-lookup"><span data-stu-id="ff9de-119">In a drilldown report, a user clicks a plus or minus button to expand or collapse a section of a report to show detail data in place.</span></span> <span data-ttu-id="ff9de-120">在钻取报表中，用户单击摘要值的链接即可打开一个单独的相关报表，来显示详细信息数据。</span><span class="sxs-lookup"><span data-stu-id="ff9de-120">In a drillthrough report, the user clicks a link for a summary value, and this opens a separate, related report to show detail data.</span></span> <span data-ttu-id="ff9de-121">详细信息数据仅在运行详细信息报表时检索。</span><span class="sxs-lookup"><span data-stu-id="ff9de-121">The detail data is only retrieved when the detail report runs.</span></span> <span data-ttu-id="ff9de-122">钻取报表所需的资源通常少于明细报表。</span><span class="sxs-lookup"><span data-stu-id="ff9de-122">Drillthrough reports typically require fewer resources than drilldown reports.</span></span> <span data-ttu-id="ff9de-123">有关详细信息，请参阅 [钻取、深化、子报表和嵌套数据区域（报表生成器和 SSRS）](drillthrough-drilldown-subreports-and-nested-data-regions.md)。</span><span class="sxs-lookup"><span data-stu-id="ff9de-123">For more information, see [Drillthrough, Drilldown, Subreports, and Nested Data Regions &#40;Report Builder and SSRS&#41;](drillthrough-drilldown-subreports-and-nested-data-regions.md).</span></span>  
  
## <a name="rendering-extension-support-for-hidden-report-items"></a><span data-ttu-id="ff9de-124">呈现扩展插件对隐藏报表项的支持</span><span class="sxs-lookup"><span data-stu-id="ff9de-124">Rendering Extension Support for Hidden Report Items</span></span>  
 <span data-ttu-id="ff9de-125">只有支持用户交互功能的呈现扩展插件（如在报表生成器和报表管理器中运行报表时使用的 HTML 呈现扩展插件）才支持报表项在显示状态和隐藏状态之间的切换功能。</span><span class="sxs-lookup"><span data-stu-id="ff9de-125">The show-and-hide toggle on report items is supported only by rendering extensions that support user interactivity, such as the HTML rendering extension that is used when you run a report in Report Builder and in Report Manager, for example.</span></span> <span data-ttu-id="ff9de-126">其他呈现扩展插件会显示隐藏项。</span><span class="sxs-lookup"><span data-stu-id="ff9de-126">Other rendering extensions display hidden items.</span></span> <span data-ttu-id="ff9de-127">下面的列表说明了对具有条件可见性的报表项的支持：</span><span class="sxs-lookup"><span data-stu-id="ff9de-127">The following list describes support for report items with conditional visibility:</span></span>  
  
-   <span data-ttu-id="ff9de-128">在 HTML 中，如果项已隐藏，则在 HTML 源中不可见。</span><span class="sxs-lookup"><span data-stu-id="ff9de-128">In HTML, if items are hidden, they are not visible in the HTML source.</span></span>  
  
-   <span data-ttu-id="ff9de-129">不管报表项是否为隐藏状态，XML 呈现扩展插件都会显示所有的报表项。</span><span class="sxs-lookup"><span data-stu-id="ff9de-129">The XML rendering extension displays all report items, regardless of whether they are hidden.</span></span>  
  
-   <span data-ttu-id="ff9de-130">Excel 呈现扩展插件将显示并扩展表、矩阵或列表的隐藏行和列。</span><span class="sxs-lookup"><span data-stu-id="ff9de-130">The Excel rendering extension displays and expands hidden rows and columns for a table, matrix, or list.</span></span> <span data-ttu-id="ff9de-131">所有行和列都可见。</span><span class="sxs-lookup"><span data-stu-id="ff9de-131">All rows and columns are visible.</span></span>  
  
 <span data-ttu-id="ff9de-132">有关详细信息，请参阅[呈现行为（报表生成器和 SSRS）](rendering-behaviors-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="ff9de-132">For more information, see [Rendering Behaviors &#40;Report Builder  and SSRS&#41;](rendering-behaviors-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff9de-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ff9de-133">See Also</span></span>  
 <span data-ttu-id="ff9de-134">[钻取、深化、子报表和嵌套数据区域（报表生成器和 SSRS）](drillthrough-drilldown-subreports-and-nested-data-regions.md) </span><span class="sxs-lookup"><span data-stu-id="ff9de-134">[Drillthrough, Drilldown, Subreports, and Nested Data Regions &#40;Report Builder and SSRS&#41;](drillthrough-drilldown-subreports-and-nested-data-regions.md) </span></span>  
 <span data-ttu-id="ff9de-135">[交互式排序、文档结构图和链接（报表生成器和 SSRS）](interactive-sort-document-maps-and-links-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ff9de-135">[Interactive Sort, Document Maps, and Links &#40;Report Builder and SSRS&#41;](interactive-sort-document-maps-and-links-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="ff9de-136">表达式示例（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="ff9de-136">Expression Examples &#40;Report Builder and SSRS&#41;</span></span>](expression-examples-report-builder-and-ssrs.md)  
  
  
