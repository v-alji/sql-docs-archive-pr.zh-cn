---
title: 交互式排序、文档结构图和链接（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: cc6ef408-4a76-408a-9d3f-033481fe21cf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 35d88e89ed14a205153374d44562e6d3fda92e02
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692711"
---
# <a name="interactive-sort-document-maps-and-links-report-builder-and-ssrs"></a><span data-ttu-id="9f284-102">交互式排序、文档结构图和链接（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="9f284-102">Interactive Sort, Document Maps, and Links (Report Builder and SSRS)</span></span>
  <span data-ttu-id="9f284-103">在基于 Web 的环境中，您可以添加许多让用户与报表进行交互的功能。</span><span class="sxs-lookup"><span data-stu-id="9f284-103">In Web-based environments, you can add a number of features that let your users interact with reports.</span></span> <span data-ttu-id="9f284-104">用户可以更改报表中值的排序顺序，在报表中显示或隐藏某些项，或者单击其中的链接以访问其他报表或网页。</span><span class="sxs-lookup"><span data-stu-id="9f284-104">Your users can change the sort order of values in your report, show or hide items in the report, or click links that go to other reports or Web pages.</span></span> <span data-ttu-id="9f284-105">还可以添加目录或文档结构图。</span><span class="sxs-lookup"><span data-stu-id="9f284-105">You can also add a table of contents or document map.</span></span> <span data-ttu-id="9f284-106">报表用户只需单击目录或文档结构图中的项，即可跳至报表内的相应区域。</span><span class="sxs-lookup"><span data-stu-id="9f284-106">Your report users can click items in the table of contents or document map to jump to areas within a report.</span></span>  
  
 <span data-ttu-id="9f284-107">报表生成器和报表设计器支持三种类型的链接，它们分别执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="9f284-107">Report Builder and Report Designer support three types of links with the following actions:</span></span>  
  
-   <span data-ttu-id="9f284-108">**书签链接** 跳至报表中的其他区域。</span><span class="sxs-lookup"><span data-stu-id="9f284-108">**Bookmark links** Jump to other areas within the report.</span></span>  
  
-   <span data-ttu-id="9f284-109">**超链接** 跳至用于指定网页地址的 URL 或使用 URL 访问跳至报表服务器上的报表。</span><span class="sxs-lookup"><span data-stu-id="9f284-109">**Hyperlinks** Jump to URLs that specify the address of Web pages or reports on a report server by using URL access.</span></span>  
  
-   <span data-ttu-id="9f284-110">**钻取报表链接** 跳至同一报表服务器上的其他报表。</span><span class="sxs-lookup"><span data-stu-id="9f284-110">**Drillthrough report links** Jump to other reports on the same report server.</span></span> <span data-ttu-id="9f284-111">有关详细信息，请参阅[钻取报表（报表生成器和 SSRS）](drillthrough-reports-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="9f284-111">For more information, see [Drillthrough Reports &#40;Report Builder and SSRS&#41;](drillthrough-reports-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9f284-112">绑定到数据集字段的链接容易被篡改。</span><span class="sxs-lookup"><span data-stu-id="9f284-112">Links that are bound to dataset fields can be vulnerable to tampering for malicious purposes.</span></span> <span data-ttu-id="9f284-113">有关详细信息，请参阅 msdn.microsoft.com 上 [联机丛书](../security/secure-reports-and-resources.md) 中的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][保护报表和资源](https://go.microsoft.com/fwlink/?LinkId=154888) 。</span><span class="sxs-lookup"><span data-stu-id="9f284-113">For more information, see [Secure Reports and Resources](../security/secure-reports-and-resources.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][Books Online](https://go.microsoft.com/fwlink/?LinkId=154888) on msdn.microsoft.com.</span></span>  
  
 <span data-ttu-id="9f284-114">您还可以设计包含排序、筛选器和可见性参数引用的表达式，让用户控制报表的显示和内容。</span><span class="sxs-lookup"><span data-stu-id="9f284-114">You can also let your users control report display and content by designing expressions that include parameter references for sort, filter, and visibility.</span></span> <span data-ttu-id="9f284-115">有关详细信息，请参阅[报表参数（报表生成器和报表设计器）](report-parameters-report-builder-and-report-designer.md)、[对数据进行筛选、分组和排序（报表生成器和 SSRS）](filter-group-and-sort-data-report-builder-and-ssrs.md)和[添加数据集筛选器、数据区域筛选器和组筛选器（报表生成器和 SSRS）](add-dataset-filters-data-region-filters-and-group-filters.md)。</span><span class="sxs-lookup"><span data-stu-id="9f284-115">For more information, see [Report Parameters &#40;Report Builder and Report Designer&#41;](report-parameters-report-builder-and-report-designer.md), [Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md), and [Add Dataset Filters, Data Region Filters, and Group Filters &#40;Report Builder and SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="in-this-section"></a><span data-ttu-id="9f284-116">本节内容</span><span class="sxs-lookup"><span data-stu-id="9f284-116">In This Section</span></span>  
 [<span data-ttu-id="9f284-117">交互式排序（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="9f284-117">Interactive Sort &#40;Report Builder and SSRS&#41;</span></span>](interactive-sort-report-builder-and-ssrs.md)  
 <span data-ttu-id="9f284-118">介绍如何将交互排序按钮添加到列标题。</span><span class="sxs-lookup"><span data-stu-id="9f284-118">Explains how to add interactive sort buttons to column headers.</span></span>  
  
 [<span data-ttu-id="9f284-119">创建文档结构图（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="9f284-119">Create a Document Map &#40;Report Builder and SSRS&#41;</span></span>](create-a-document-map-report-builder-and-ssrs.md)  
 <span data-ttu-id="9f284-120">介绍如何添加目录以支持在大型报表中导航。</span><span class="sxs-lookup"><span data-stu-id="9f284-120">Explains how to add a table of contents to support navigation in a large report.</span></span>  
  
 [<span data-ttu-id="9f284-121">向报表添加书签（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="9f284-121">Add a Bookmark to a Report &#40;Report Builder and SSRS&#41;</span></span>](add-a-bookmark-to-a-report-report-builder-and-ssrs.md)  
 <span data-ttu-id="9f284-122">说明如何添加书签以在报表内创建链接。</span><span class="sxs-lookup"><span data-stu-id="9f284-122">Explains how to add bookmarks to create links within a report.</span></span>  
  
 [<span data-ttu-id="9f284-123">向 URL 添加超链接（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="9f284-123">Add a Hyperlink to a URL &#40;Report Builder and SSRS&#41;</span></span>](add-a-hyperlink-to-a-url-report-builder-and-ssrs.md)  
 <span data-ttu-id="9f284-124">说明如何添加从报表指向 URL 的链接。</span><span class="sxs-lookup"><span data-stu-id="9f284-124">Explains how to add a link from your report to a URL</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f284-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9f284-125">See Also</span></span>  
 [<span data-ttu-id="9f284-126">钻取、深化、子报表和嵌套数据区域（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="9f284-126">Drillthrough, Drilldown, Subreports, and Nested Data Regions &#40;Report Builder and SSRS&#41;</span></span>](drillthrough-drilldown-subreports-and-nested-data-regions.md)  
  
  
