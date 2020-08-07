---
title: 控制分页符、标题、列和行（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4b8fa41f-a727-4f23-8efb-fd9bb0d4cd1d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7dae06129ee5dc9962538e8d025dca9966325f5d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588908"
---
# <a name="controlling-page-breaks-headings-columns-and-rows-report-builder-and-ssrs"></a><span data-ttu-id="ecc91-102">控制分页符、标题、列和行（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="ecc91-102">Controlling Page Breaks, Headings, Columns, and Rows (Report Builder and SSRS)</span></span>
  <span data-ttu-id="ecc91-103">分页符可将报表划分为单独的页，以便于查看和打印。</span><span class="sxs-lookup"><span data-stu-id="ecc91-103">A page break divides a report into separate pages for viewing and printing.</span></span> <span data-ttu-id="ecc91-104">预览报表或将其导出为其他文件格式时，分页符可确定报表内容适合报表页的方式，以获得最佳查看效果。</span><span class="sxs-lookup"><span data-stu-id="ecc91-104">Page breaks determine how the content is fitted to a report page for optimal viewing when you preview a report or export it to a different file format.</span></span>  
  
 <span data-ttu-id="ecc91-105">添加分页符还会改进处理大型报表时的性能。</span><span class="sxs-lookup"><span data-stu-id="ecc91-105">Adding page breaks also improves the performance of large reports when the are processed.</span></span> <span data-ttu-id="ecc91-106">将显示呈现的页，同时在后台中呈现其余页。</span><span class="sxs-lookup"><span data-stu-id="ecc91-106">A rendered page is displayed while the rest of the pages are rendered in the background.</span></span> <span data-ttu-id="ecc91-107">这样，您就可以在等待查看报表的其他页面的同时，开始查看初始页。</span><span class="sxs-lookup"><span data-stu-id="ecc91-107">This allows you to begin viewing the initial pages of the report while waiting for additional pages to become available.</span></span>  
  
 <span data-ttu-id="ecc91-108">分页符可以添加到表、矩阵、列表、图表、仪表或图像等报表项中。</span><span class="sxs-lookup"><span data-stu-id="ecc91-108">Page breaks can be added to report items such as a table, matrix, list, chart, gauge, or image.</span></span> <span data-ttu-id="ecc91-109">还可以将分页符添加到表、矩阵或列表内的组中。</span><span class="sxs-lookup"><span data-stu-id="ecc91-109">You can also add page breaks to groups in a table, matrix, or list.</span></span> <span data-ttu-id="ecc91-110">可以在组之前、组之后和组之间添加分页符。</span><span class="sxs-lookup"><span data-stu-id="ecc91-110">Page breaks can be added before, after, and between groups.</span></span> <span data-ttu-id="ecc91-111">默认情况下，不会向报表添加组与组之间的分页符。</span><span class="sxs-lookup"><span data-stu-id="ecc91-111">Page breaks between groups are not added to the report by default.</span></span>  
  
 <span data-ttu-id="ecc91-112">有关详细信息，请参阅[在多个页中显示行标题和列标题（报表生成器和 SSRS）](display-row-and-column-headers-on-multiple-pages-report-builder-and-ssrs.md)和[在滚动报表时保持标题可见（报表生成器和 SSRS）](keep-headers-visible-when-scrolling-through-a-report-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="ecc91-112">For more information, see [Display Row and Column Headers on Multiple Pages &#40;Report Builder and SSRS&#41;](display-row-and-column-headers-on-multiple-pages-report-builder-and-ssrs.md) and [Keep Headers Visible When Scrolling Through a Report &#40;Report Builder and SSRS&#41;](keep-headers-visible-when-scrolling-through-a-report-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ecc91-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ecc91-113">See Also</span></span>  
 <span data-ttu-id="ecc91-114">[列出 &#40;报表生成器和 SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ecc91-114">[Lists &#40;Report Builder and SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="ecc91-115">[控制 Tablix 数据区域在报表页上的显示（报表生成器和 SSRS）](controlling-the-tablix-data-region-display-on-a-report-page.md) </span><span class="sxs-lookup"><span data-stu-id="ecc91-115">[Controlling the Tablix Data Region Display on a Report Page &#40;Report Builder and SSRS&#41;](controlling-the-tablix-data-region-display-on-a-report-page.md) </span></span>  
 <span data-ttu-id="ecc91-116">[“分组”窗格（报表生成器）](grouping-pane-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="ecc91-116">[Grouping Pane &#40;Report Builder&#41;](grouping-pane-report-builder.md) </span></span>  
 [<span data-ttu-id="ecc91-117">与组一起显示组头和组尾（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="ecc91-117">Display Headers and Footers with a Group &#40;Report Builder and SSRS&#41;</span></span>](display-headers-and-footers-with-a-group-report-builder-and-ssrs.md)  
  
  
