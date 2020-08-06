---
title: 从其他应用程序打印报表（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a5560581-fd57-4a45-b7ea-43b21a8a7419
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 58fee2cf31601dc638eebd69a13727a805408ac0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690403"
---
# <a name="print-reports-from-other-applications-report-builder-and-ssrs"></a><span data-ttu-id="058c2-102">从其他应用程序打印报表（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="058c2-102">Print Reports from Other Applications (Report Builder and SSRS)</span></span>
  <span data-ttu-id="058c2-103">通过报表生成器提供的导出选项，可以在其他应用程序中轻松查看报表。</span><span class="sxs-lookup"><span data-stu-id="058c2-103">Report Builder provides an export option that allows you to easily view a report in other applications.</span></span> <span data-ttu-id="058c2-104">`Export` 命令可以在报表工具栏上找到，当您在浏览器或基于 Web 的应用程序中打开报表时，该工具栏将显示在报表的顶部。</span><span class="sxs-lookup"><span data-stu-id="058c2-104">The `Export` command is available on the report toolbar that appears at the top of a report when you open it in a browser or Web-based application.</span></span> <span data-ttu-id="058c2-105">导出报表将会在其他应用程序中显示该报表（例如，将报表导出到 Excel 将会在 [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)]中打开该报表）。</span><span class="sxs-lookup"><span data-stu-id="058c2-105">Exporting a report displays it in a different application (for example, exporting a report to Excel opens the report in [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)]).</span></span> <span data-ttu-id="058c2-106">出于打印目的，建议仅当相关应用程序具有您需要使用的特定打印功能时才导出报表。</span><span class="sxs-lookup"><span data-stu-id="058c2-106">For printing purposes, exporting a report is recommended only if the application has specific printing features that you want to use.</span></span>  
  
 <span data-ttu-id="058c2-107">若要将报表导出到其他应用程序，您必须已安装该应用程序。</span><span class="sxs-lookup"><span data-stu-id="058c2-107">To export a report to another application, you must have that application installed.</span></span> <span data-ttu-id="058c2-108">例如，在可以导出到 Acrobat (PDF) 格式之前，必须先在计算机上安装 Adobe Acrobat Reader。</span><span class="sxs-lookup"><span data-stu-id="058c2-108">For example, you must have Adobe Acrobat Reader installed on your computer before you can export to the Acrobat (PDF) format.</span></span> <span data-ttu-id="058c2-109">如果选择将报表导出为 TIFF 格式，报表服务器将把报表置于与 TIFF 文件类型关联的查看应用程序中。</span><span class="sxs-lookup"><span data-stu-id="058c2-109">If you choose to export a report to TIFF format, the report server places the report in a viewing application that is associated with the TIFF file type.</span></span> <span data-ttu-id="058c2-110">尽管所用的应用程序取决于您使用哪个 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 版本，但通常该工具是 Windows 图片和传真查看器。</span><span class="sxs-lookup"><span data-stu-id="058c2-110">Although the application used depends on which version of [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows you have, typically this tool is Windows Picture and Fax Viewer.</span></span> <span data-ttu-id="058c2-111">默认分辨率对应于屏幕分辨率每英寸 96 点 (DPI)。</span><span class="sxs-lookup"><span data-stu-id="058c2-111">The default resolution corresponds to a screen resolution of 96 dots per inch (DPI).</span></span> <span data-ttu-id="058c2-112">可以在 Windows 图片和传真查看器中将分辨率增加到 300 DPI 或 600 DPI，以匹配打印机的能力。</span><span class="sxs-lookup"><span data-stu-id="058c2-112">You can increase the resolution in Windows Picture and Fax Viewer to 300 DPI or 600 DPI to match the capabilities of your printer.</span></span> <span data-ttu-id="058c2-113">有关调整分辨率的详细信息，请参阅 Windows 产品文档。</span><span class="sxs-lookup"><span data-stu-id="058c2-113">For more information about adjusting the resolution, see the Windows product documentation.</span></span>  
  
 <span data-ttu-id="058c2-114">如果选择导出为 Web 存档（也称为 MHTML）格式，则会将报表导出到您的默认浏览器。</span><span class="sxs-lookup"><span data-stu-id="058c2-114">If you choose Web archive (also known as MHTML), the report is exported to your default browser.</span></span> <span data-ttu-id="058c2-115">通过浏览器进行打印可能会导致在每页的底部添加报表路径信息。</span><span class="sxs-lookup"><span data-stu-id="058c2-115">Printing from the browser may result in report path information being added at the bottom of every page.</span></span> <span data-ttu-id="058c2-116">在大多数情况下，您可以通过设置浏览器选项，以避免在打印的页面上添加路径信息。</span><span class="sxs-lookup"><span data-stu-id="058c2-116">In most cases, you can set browser options to omit path information on a printed page.</span></span> <span data-ttu-id="058c2-117">有关详细信息，请参阅所用浏览器的产品文档。</span><span class="sxs-lookup"><span data-stu-id="058c2-117">For more information, see the product documentation for the browser you are using.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="058c2-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="058c2-118">See Also</span></span>  
 <span data-ttu-id="058c2-119">[&#40;报表生成器和 SSRS 打印报表&#41;](print-a-report-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="058c2-119">[Print a Report &#40;Report Builder and SSRS&#41;](print-a-report-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="058c2-120">[使用打印控件从浏览器打印报表 &#40;报表生成器和 SSRS&#41;](print-reports-from-a-browser-with-the-print-control-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="058c2-120">[Print Reports from a Browser with the Print Control &#40;Report Builder and SSRS&#41;](print-reports-from-a-browser-with-the-print-control-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="058c2-121">[导出报表 &#40;报表生成器和 SSRS&#41;](export-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="058c2-121">[Exporting Reports &#40;Report Builder and SSRS&#41;](export-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="058c2-122">[将报表导出为其他文件类型 &#40;报表生成器和 SSRS&#41;](../export-a-report-as-another-file-type-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="058c2-122">[Export a Report as Another File Type &#40;Report Builder and SSRS&#41;](../export-a-report-as-another-file-type-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="058c2-123">查找、查看和管理报表（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="058c2-123">Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;</span></span>](finding-viewing-and-managing-reports-report-builder-and-ssrs.md)  
  
  
