---
title: SQL Server 2014 报表生成器的新增功能&#39;Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 8223c19b-4b0d-4b1d-a042-9a726c18e708
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0ce72af225130bc3f081a53008a303c5213db636
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587707"
---
# <a name="what39s-new-in-report-builder-for-sql-server-2014"></a><span data-ttu-id="60027-102">SQL Server 2014 报表生成器的新增功能&#39;</span><span class="sxs-lookup"><span data-stu-id="60027-102">What&#39;s New in Report Builder for SQL Server 2014</span></span>
  <span data-ttu-id="60027-103">[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 引入了许多 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 功能。</span><span class="sxs-lookup"><span data-stu-id="60027-103">The [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] introduces a number of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] features.</span></span>  
  
 <span data-ttu-id="60027-104">有关此版本中有关其他产品和技术的功能的信息 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] ，请参阅[SQL Server 2014 中的新增](../sql-server/what-s-new-in-sql-server-2016.md)功能。</span><span class="sxs-lookup"><span data-stu-id="60027-104">For information about features in this release for other [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] products and technologies, see [What's New in SQL Server 2014](../sql-server/what-s-new-in-sql-server-2016.md).</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="60027-105">有关此版本中的新增功能的最新信息和资源，请参阅有关[SQL Server Reporting Services 中的新增功能 (SSRS) 的详细信息](https://go.microsoft.com/fwlink/?LinkId=207147)。</span><span class="sxs-lookup"><span data-stu-id="60027-105">For the most recent information and resources regarding new features in this release, see [Additional information on what is new in SQL Server Reporting Services (SSRS)](https://go.microsoft.com/fwlink/?LinkId=207147).</span></span>  
  
##  <a name="excel-renderer-for-microsoft-excel-2007-2010-and-microsoft-excel-2003"></a><a name="ExcelRenderer"></a><span data-ttu-id="60027-106">用于 Microsoft Excel 2007-2010 和 Microsoft Excel 2003 的 Excel 呈现器</span><span class="sxs-lookup"><span data-stu-id="60027-106">Excel Renderer for Microsoft Excel 2007-2010 and Microsoft Excel 2003</span></span>  
 <span data-ttu-id="60027-107">如果安装了针对 Word、Excel 和 PowerPoint 的 Microsoft Office 兼容包，[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 中新增的 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Excel 呈现扩展插件可将报表呈现为能够兼容 [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] 2007-2010 及 [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] 2003 的 Excel 文档。</span><span class="sxs-lookup"><span data-stu-id="60027-107">The [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Excel rendering extension, new in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], renders a report as an Excel document that is compatible with [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] 2007-2010 as well as [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] 2003 with the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint installed.</span></span> <span data-ttu-id="60027-108">该格式为 Office Open XML，文件扩展名为 .xlsx。</span><span class="sxs-lookup"><span data-stu-id="60027-108">The format is Office Open XML and the file extension of files is .xlsx.</span></span>  
  
 <span data-ttu-id="60027-109">此 Excel 呈现扩展插件消除了与 Excel 2003 兼容的早期版本的限制。</span><span class="sxs-lookup"><span data-stu-id="60027-109">This Excel-rendering extension removes limitations of the earlier version, compatible with Excel 2003.</span></span> <span data-ttu-id="60027-110">下面列出了呈现扩展插件中的改进：</span><span class="sxs-lookup"><span data-stu-id="60027-110">The following lists the improvement in the rendering extension:</span></span>  
  
-   <span data-ttu-id="60027-111">每个工作表的最大行数是 1,048,576。</span><span class="sxs-lookup"><span data-stu-id="60027-111">Maximum rows per worksheet is 1,048,576.</span></span>  
  
-   <span data-ttu-id="60027-112">每个工作表的最大列数是 16,384。</span><span class="sxs-lookup"><span data-stu-id="60027-112">Maximum columns per worksheet is 16,384.</span></span>  
  
-   <span data-ttu-id="60027-113">工作表中允许的颜色数目大约是 1600 万（24 位颜色）。</span><span class="sxs-lookup"><span data-stu-id="60027-113">Number of colors allowed in a worksheet is approximately 16 million (24-bit color).</span></span>  
  
-   <span data-ttu-id="60027-114">ZIP 压缩提供较小的文件大小。</span><span class="sxs-lookup"><span data-stu-id="60027-114">ZIP compression provides smaller files sizes.</span></span>  
  
 <span data-ttu-id="60027-115">有关详细信息，请参阅 [导出到 Microsoft Excel（报表生成器和 SSRS）](report-builder/exporting-to-microsoft-excel-report-builder-and-ssrs.md)中处理数据。</span><span class="sxs-lookup"><span data-stu-id="60027-115">For more information, see [Exporting to Microsoft Excel &#40;Report Builder and SSRS&#41;](report-builder/exporting-to-microsoft-excel-report-builder-and-ssrs.md).</span></span>  
  
##  <a name="word-renderer-for-microsoft-word-2007-2010-and-microsoft-word-2003"></a><a name="WordRenderer"></a><span data-ttu-id="60027-116">Microsoft Word 2007-2010 和 Microsoft Word 2003 的 word 呈现器</span><span class="sxs-lookup"><span data-stu-id="60027-116">Word Renderer for Microsoft Word 2007-2010 and Microsoft Word 2003</span></span>  
 <span data-ttu-id="60027-117">如果安装了针对 Word、Excel 和 PowerPoint 的 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Office 兼容包，[!INCLUDE[ssSQL11](../includes/sssql11-md.md)] 中新增的 [!INCLUDE[ofprword](../includes/ofprword-md.md)] Word 呈现扩展插件可将报表呈现为能够兼容 [!INCLUDE[ofprword](../includes/ofprword-md.md)] 2007-2010 及 [!INCLUDE[msCoName](../includes/msconame-md.md)] 2003 的 Word 文档。</span><span class="sxs-lookup"><span data-stu-id="60027-117">The [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Word rendering extension, new in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], renders a report as a Word document that is compatible with [!INCLUDE[ofprword](../includes/ofprword-md.md)] 2007-2010 as well as [!INCLUDE[ofprword](../includes/ofprword-md.md)] 2003 with the [!INCLUDE[msCoName](../includes/msconame-md.md)] Office Compatibility Pack for Word, Excel, and PowerPoint installed.</span></span> <span data-ttu-id="60027-118">该格式为 Office Open XML，文件扩展名为 docx。</span><span class="sxs-lookup"><span data-stu-id="60027-118">The format is Office Open XML and the file extension of files is docx.</span></span>  
  
 <span data-ttu-id="60027-119">除了使 Word 2007-2010 中的新增功能可用于导出的报表之外，导出的报表的 \*.docx 文件往往更小。</span><span class="sxs-lookup"><span data-stu-id="60027-119">In addition to making the features that are new in Word 2007-2010 available to exported reports, \*.docx files of exported reports tend to be smaller.</span></span> <span data-ttu-id="60027-120">通过使用 Word 呈现器导出的报表通常显著小于通过使用 Word 2003 呈现器导出的相同报表。</span><span class="sxs-lookup"><span data-stu-id="60027-120">Reports exported by using the Word renderer are typically significantly smaller than the same reports exported by using the Word 2003 renderer.</span></span>  
  
 <span data-ttu-id="60027-121">有关详细信息，请参阅 [导出到 Microsoft Word（报表生成器和 SSRS）](report-builder/exporting-to-microsoft-word-report-builder-and-ssrs.md)中处理数据。</span><span class="sxs-lookup"><span data-stu-id="60027-121">For more information, see [Exporting to Microsoft Word &#40;Report Builder and SSRS&#41;](report-builder/exporting-to-microsoft-word-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60027-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="60027-122">See Also</span></span>  
 [<span data-ttu-id="60027-123">SQL Server 2014 中的报表生成器</span><span class="sxs-lookup"><span data-stu-id="60027-123">Report Builder in SQL Server 2014</span></span>](report-builder/report-builder-in-sql-server-2016.md)  
  
  
