---
title: 打印报表（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4bad1b6e-7d94-4b17-9502-ccd3dce0fdd9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3004734226e67ec435e90a4e62895c94173b23d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579520"
---
# <a name="print-reports-report-builder-and-ssrs"></a><span data-ttu-id="36a0b-102">打印报表（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="36a0b-102">Print Reports (Report Builder and SSRS)</span></span>
  <span data-ttu-id="36a0b-103">在将报表保存到报表服务器之后，可以通过浏览器、报表管理器或用于查看导出报表的任意应用程序查看和打印报表。</span><span class="sxs-lookup"><span data-stu-id="36a0b-103">After you save a report to a report server, you can view and print the report from a browser, Report Manager, or any application that you use to view an exported report.</span></span> <span data-ttu-id="36a0b-104">在保存报表之前，可以在预览报表时打印它。</span><span class="sxs-lookup"><span data-stu-id="36a0b-104">Before saving a report, you can print it when you preview it.</span></span>  
  
 <span data-ttu-id="36a0b-105">所有打印处理都是在客户端计算机上按需执行的。</span><span class="sxs-lookup"><span data-stu-id="36a0b-105">All print processing is performed on demand and on the client computer.</span></span> <span data-ttu-id="36a0b-106">现在还没有任何服务器端打印功能可以实现以下操作：即将打印作业从报表服务器直接传送到与 Web 服务器连接的打印机。</span><span class="sxs-lookup"><span data-stu-id="36a0b-106">There is no server-side print functionality that enables you to route a print job directly from a report server to a printer that is attached to the Web server.</span></span> <span data-ttu-id="36a0b-107">打印机和打印选项由每个报表用户使用标准的 **“打印”** 对话框自行选择。</span><span class="sxs-lookup"><span data-stu-id="36a0b-107">Printers and print options are selected by individual report users by using a standard **Print** dialog box.</span></span>  
  
 <span data-ttu-id="36a0b-108">对于所设计报表专用于打印输出的报表作者来说，可以使用分页符、页眉和页脚、表达式和背景图像，来创建符合打印目的的设计方案。</span><span class="sxs-lookup"><span data-stu-id="36a0b-108">Report authors who design reports specifically for print output can use page breaks, page headers and footers, expressions, and background images to create a print-based design.</span></span> <span data-ttu-id="36a0b-109">专用于打印输出的报表设计元素示例包括在每个报表背面打印的条款和条件，或类似信头的图形和文本元素等等。</span><span class="sxs-lookup"><span data-stu-id="36a0b-109">Examples of report design elements intended for print output might include terms and conditions that you print on the back of every report, or graphic and text elements that mimic letterhead.</span></span>  
  
 <span data-ttu-id="36a0b-110">由于不同呈现格式的分页方式不同，因此对于所有报表的每种呈现格式，您可能无法都获得最佳的打印输出效果。</span><span class="sxs-lookup"><span data-stu-id="36a0b-110">Due to the way pagination is implemented for different rendering formats, you might not be able to achieve optimum print output results for every report in every rendering format.</span></span> <span data-ttu-id="36a0b-111">下面的列表提供示例：</span><span class="sxs-lookup"><span data-stu-id="36a0b-111">The following list provides examples:</span></span>  
  
1.  <span data-ttu-id="36a0b-112">报表页设计为可以容纳可变的数据量。</span><span class="sxs-lookup"><span data-stu-id="36a0b-112">Report pages are designed to accommodate variable amounts of data.</span></span> <span data-ttu-id="36a0b-113">例如，对于包括矩阵的报表，根据用户是否以交互方式切换行和列，报表页可能会在水平方向和垂直方向同时扩展。</span><span class="sxs-lookup"><span data-stu-id="36a0b-113">Reports that include a matrix, for example, can cause a page to grow both horizontally and vertically depending on whether a user interactively toggles rows and columns.</span></span> <span data-ttu-id="36a0b-114">不扩展矩阵的用户将获得与扩展矩阵的用户不同的打印效果。</span><span class="sxs-lookup"><span data-stu-id="36a0b-114">A user who does not expand a matrix will get different print results than a user who does.</span></span>  
  
2.  <span data-ttu-id="36a0b-115">您无法将横向模式页面和纵向模式页面组合在同一报表中，也无法创建能够替换报表布局或与之并存的满足打印要求的布局（如在浏览器或其他应用程序中所呈现的布局）。</span><span class="sxs-lookup"><span data-stu-id="36a0b-115">You cannot combine landscape and portrait mode pages in the same report, nor is there a way to create a print-based layout that replaces or exists alongside the layout of a report as rendered in a browser or other application.</span></span>  
  
3.  <span data-ttu-id="36a0b-116">对于大多数的导出报表，报表打印输出包括报表上的所有可见内容，与用户在计算机监视器上看到的内容没有分别。</span><span class="sxs-lookup"><span data-stu-id="36a0b-116">For most exported reports, report printouts include everything that is visible on the report, as viewed by the user on a computer monitor.</span></span> <span data-ttu-id="36a0b-117">而报表设计图面中的空白区域将会保留。</span><span class="sxs-lookup"><span data-stu-id="36a0b-117">White space from the report design surface is preserved.</span></span> <span data-ttu-id="36a0b-118">若要以水平方式添加或删除额外的空白页，请更改报表页面宽度。</span><span class="sxs-lookup"><span data-stu-id="36a0b-118">To add or remove extra blank pages horizontally, change the report page width.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="36a0b-119">如果使用浏览器的“打印”命令，则 HTML 报表打印输出可能仅包含第一页中的内容。</span><span class="sxs-lookup"><span data-stu-id="36a0b-119">HTML report printouts may contain only the content on the first page if you are using the browser's Print command.</span></span> <span data-ttu-id="36a0b-120">如果使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 客户端打印功能打印 HTML 报表，效果将更加出色。</span><span class="sxs-lookup"><span data-stu-id="36a0b-120">You can achieve better results if you print HTML reports using the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] client printing functionality.</span></span> <span data-ttu-id="36a0b-121">有关详细信息，请参阅 [使用打印控件从浏览器中打印报表（报表生成器和 SSRS）](print-reports-from-a-browser-with-the-print-control-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="36a0b-121">For more information, see [Print Reports from a Browser with the Print Control &#40;Report Builder and SSRS&#41;](print-reports-from-a-browser-with-the-print-control-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="in-this-section"></a><span data-ttu-id="36a0b-122">本节内容</span><span class="sxs-lookup"><span data-stu-id="36a0b-122">In This Section</span></span>  
 [<span data-ttu-id="36a0b-123">使用打印控件从浏览器中打印报表（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="36a0b-123">Print Reports from a Browser with the Print Control &#40;Report Builder and SSRS&#41;</span></span>](print-reports-from-a-browser-with-the-print-control-report-builder-and-ssrs.md)  
 <span data-ttu-id="36a0b-124">介绍如何使用客户端打印功能通过 Web 浏览器或报表管理器打印报表。</span><span class="sxs-lookup"><span data-stu-id="36a0b-124">Describes how to use client-side printing to print reports from your Web browser or Report Manager.</span></span>  
  
 [<span data-ttu-id="36a0b-125">从其他应用程序打印报表（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="36a0b-125">Print Reports from Other Applications &#40;Report Builder and SSRS&#41;</span></span>](print-reports-from-other-applications-report-builder-and-ssrs.md)  
 <span data-ttu-id="36a0b-126">介绍如何打印已导出到其他应用程序的报表。</span><span class="sxs-lookup"><span data-stu-id="36a0b-126">Describes how to print reports exported to another application.</span></span>  
  
 [<span data-ttu-id="36a0b-127">打印报表（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="36a0b-127">Print a Report &#40;Report Builder and SSRS&#41;</span></span>](print-a-report-report-builder-and-ssrs.md)  
 <span data-ttu-id="36a0b-128">提供有关如何打印报表、如何控制页边距以及如何为硬分页呈现器（PDF、图像或打印）将呈现的报表指定纸张大小的分步说明。</span><span class="sxs-lookup"><span data-stu-id="36a0b-128">Provides step-by-step instructions on how to print a report, how to control the margins on a page, and on how to specify the paper size for reports that will be rendered by hard-page break renderers: PDF, Image, or Print.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36a0b-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="36a0b-129">See Also</span></span>  
 <span data-ttu-id="36a0b-130">[导出报表 &#40;报表生成器和 SSRS&#41;](export-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="36a0b-130">[Exporting Reports &#40;Report Builder and SSRS&#41;](export-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="36a0b-131">[页眉和页脚 &#40;报表生成器和 SSRS&#41;](../report-design/page-headers-and-footers-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="36a0b-131">[Page Headers and Footers &#40;Report Builder and SSRS&#41;](../report-design/page-headers-and-footers-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="36a0b-132">[映像 &#40;报表生成器和 SSRS&#41;](../report-design/images-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="36a0b-132">[Images &#40;Report Builder and SSRS&#41;](../report-design/images-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="36a0b-133">Reporting Services 中的分页（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="36a0b-133">Pagination in Reporting Services &#40;Report Builder  and SSRS&#41;</span></span>](../report-design/pagination-in-reporting-services-report-builder-and-ssrs.md)  
  
  
