---
title: “预览”视图 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.previewview.f1
helpviewer_keywords:
- Preview view [Reporting Services]
ms.assetid: 108255d1-5be8-47c1-80f3-1f2a055e4d02
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1ff7c59c3ac5143d4f4103edea1a5ee309046547
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689744"
---
# <a name="preview-view"></a><span data-ttu-id="782b5-102">“预览”视图</span><span class="sxs-lookup"><span data-stu-id="782b5-102">Preview View</span></span>
  <span data-ttu-id="782b5-103">使用 **“预览”** 视图可以显示呈现的报表。</span><span class="sxs-lookup"><span data-stu-id="782b5-103">Use **Preview** view to display the rendered report.</span></span> <span data-ttu-id="782b5-104">在预览报表时，报表设计器将在本地运行该报表，并在“预览”视图中显示该报表。</span><span class="sxs-lookup"><span data-stu-id="782b5-104">When a report is previewed, Report Designer runs the report locally and displays it in the Preview view.</span></span> <span data-ttu-id="782b5-105">在预览模式下会对报表进行完全处理。</span><span class="sxs-lookup"><span data-stu-id="782b5-105">In preview mode, the report is processed in full.</span></span> <span data-ttu-id="782b5-106">如果报表具有复杂的查询或具有大量数据，则首次查看时，预览可能需要花费几分钟的时间才能完成。</span><span class="sxs-lookup"><span data-stu-id="782b5-106">If the report has a complex query or has a large amount of data, preview might take several minutes to complete the first time you view it.</span></span> <span data-ttu-id="782b5-107">对于只影响报表格式的后续更改，预览使用缓存数据。</span><span class="sxs-lookup"><span data-stu-id="782b5-107">For subsequent changes that affect only the format of the report, preview uses cached data.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="782b5-108">当 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 作为 RemoteApp 运行时，无法在 \*\*\*\* 的“预览” [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]视图中显示报表。</span><span class="sxs-lookup"><span data-stu-id="782b5-108">When [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] is run as a RemoteApp, reports cannot be displayed in **Preview** view in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="782b5-109">RemoteApp 程序是通过远程桌面服务进行远程访问的程序。</span><span class="sxs-lookup"><span data-stu-id="782b5-109">RemoteApp programs are programs that are accessed remotely through Remote Desktop Services.</span></span> <span data-ttu-id="782b5-110">有关详细信息，请参阅[TS RemoteApp 循序渐进指南](https://technet.microsoft.com/library/cc730673\(WS.10\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="782b5-110">For more information, see [TS RemoteApp Step-by-Step Guide](https://technet.microsoft.com/library/cc730673\(WS.10\).aspx).</span></span>  
  
## <a name="options"></a><span data-ttu-id="782b5-111">选项</span><span class="sxs-lookup"><span data-stu-id="782b5-111">Options</span></span>  
 <span data-ttu-id="782b5-112">使用工具栏可以管理预览功能。</span><span class="sxs-lookup"><span data-stu-id="782b5-112">Use the toolbar to manage preview functions.</span></span>  
  
 <span data-ttu-id="782b5-113">**显示或隐藏文档结构图**</span><span class="sxs-lookup"><span data-stu-id="782b5-113">**Show or Hide Document Map**</span></span>  
 <span data-ttu-id="782b5-114">选择此选项可以显示或隐藏文档结构图（如果存在）。</span><span class="sxs-lookup"><span data-stu-id="782b5-114">Choose this option to show or hide the document map if one exists.</span></span>  
  
 <span data-ttu-id="782b5-115">**显示或隐藏参数区域**</span><span class="sxs-lookup"><span data-stu-id="782b5-115">**Show or Hide Parameter Area**</span></span>  
 <span data-ttu-id="782b5-116">选择此选项可以为带有参数的报表显示或隐藏参数框。</span><span class="sxs-lookup"><span data-stu-id="782b5-116">Choose this option to show or hide the parameters boxes for reports with parameters.</span></span>  
  
 <span data-ttu-id="782b5-117">**第一页**</span><span class="sxs-lookup"><span data-stu-id="782b5-117">**First Page**</span></span>  
 <span data-ttu-id="782b5-118">选择此选项可以转到报表的第一页。</span><span class="sxs-lookup"><span data-stu-id="782b5-118">Choose this option to go to the first page of the report.</span></span>  
  
 <span data-ttu-id="782b5-119">**上一页**</span><span class="sxs-lookup"><span data-stu-id="782b5-119">**Previous Page**</span></span>  
 <span data-ttu-id="782b5-120">选择此选项可以转到报表的上一页。</span><span class="sxs-lookup"><span data-stu-id="782b5-120">Choose this option to go to the previous page of the report.</span></span>  
  
 <span data-ttu-id="782b5-121">**当前页面**</span><span class="sxs-lookup"><span data-stu-id="782b5-121">**Current Page**</span></span>  
 <span data-ttu-id="782b5-122">显示报表的当前页。</span><span class="sxs-lookup"><span data-stu-id="782b5-122">Displays the current page of the report.</span></span>  
  
 <span data-ttu-id="782b5-123">**总页数**</span><span class="sxs-lookup"><span data-stu-id="782b5-123">**Total Pages**</span></span>  
 <span data-ttu-id="782b5-124">显示报表中的总页数。</span><span class="sxs-lookup"><span data-stu-id="782b5-124">Displays the total number of pages in the report.</span></span>  
  
 <span data-ttu-id="782b5-125">**下一页**</span><span class="sxs-lookup"><span data-stu-id="782b5-125">**Next Page**</span></span>  
 <span data-ttu-id="782b5-126">选择此选项可以转到报表的下一页。</span><span class="sxs-lookup"><span data-stu-id="782b5-126">Choose this option to go to the next page of the report.</span></span>  
  
 <span data-ttu-id="782b5-127">**最后一页**</span><span class="sxs-lookup"><span data-stu-id="782b5-127">**Last Page**</span></span>  
 <span data-ttu-id="782b5-128">选择此选项可以转到报表的最后一页。</span><span class="sxs-lookup"><span data-stu-id="782b5-128">Choose this option to go to the last page of the report.</span></span>  
  
 <span data-ttu-id="782b5-129">**返回父报表**</span><span class="sxs-lookup"><span data-stu-id="782b5-129">**Back to Parent Report**</span></span>  
 <span data-ttu-id="782b5-130">选择此选项可以转到父报表。</span><span class="sxs-lookup"><span data-stu-id="782b5-130">Choose this option to go to the parent report.</span></span> <span data-ttu-id="782b5-131">此选项用来导航钻取报表。</span><span class="sxs-lookup"><span data-stu-id="782b5-131">This option is used to navigate drillthrough reports.</span></span>  
  
 <span data-ttu-id="782b5-132">**停止呈现**</span><span class="sxs-lookup"><span data-stu-id="782b5-132">**Stop Rendering**</span></span>  
 <span data-ttu-id="782b5-133">选择此选项可以停止呈现进程。</span><span class="sxs-lookup"><span data-stu-id="782b5-133">Choose this option to stop the rendering process.</span></span>  
  
 <span data-ttu-id="782b5-134">**“刷新”**</span><span class="sxs-lookup"><span data-stu-id="782b5-134">**Refresh**</span></span>  
 <span data-ttu-id="782b5-135">选择此选项可以刷新数据缓存并再次运行报表。</span><span class="sxs-lookup"><span data-stu-id="782b5-135">Choose this option to refresh the data cache and run the report again.</span></span>  
  
 <span data-ttu-id="782b5-136">**打印**</span><span class="sxs-lookup"><span data-stu-id="782b5-136">**Print**</span></span>  
 <span data-ttu-id="782b5-137">选择此选项可以打印报表。</span><span class="sxs-lookup"><span data-stu-id="782b5-137">Choose this option to print the report.</span></span>  
  
 <span data-ttu-id="782b5-138">**打印布局**</span><span class="sxs-lookup"><span data-stu-id="782b5-138">**Print Layout**</span></span>  
 <span data-ttu-id="782b5-139">选择此选项可以在预览报表和报表打印视图之间进行切换。</span><span class="sxs-lookup"><span data-stu-id="782b5-139">Choose this option to toggle between the preview report and the view of the report as it will appear on the printed page.</span></span>  
  
 <span data-ttu-id="782b5-140">**页面设置**</span><span class="sxs-lookup"><span data-stu-id="782b5-140">**Page Setup**</span></span>  
 <span data-ttu-id="782b5-141">选择此选项可以方便地更改页属性和打印属性。</span><span class="sxs-lookup"><span data-stu-id="782b5-141">Choose this option to conveniently change page and print properties.</span></span> <span data-ttu-id="782b5-142">使用“打印布局”可以在打印之前查看更改。</span><span class="sxs-lookup"><span data-stu-id="782b5-142">Use Print Layout to view changes before printing.</span></span>  
  
 <span data-ttu-id="782b5-143">**导出**</span><span class="sxs-lookup"><span data-stu-id="782b5-143">**Export**</span></span>  
 <span data-ttu-id="782b5-144">选择此选项可以采用特定格式导出呈现的报表。</span><span class="sxs-lookup"><span data-stu-id="782b5-144">Choose this option to export the rendered report in a specific format.</span></span>  
  
 <span data-ttu-id="782b5-145">**缩放**</span><span class="sxs-lookup"><span data-stu-id="782b5-145">**Zoom**</span></span>  
 <span data-ttu-id="782b5-146">选择缩放系数可以放大或缩小报表。</span><span class="sxs-lookup"><span data-stu-id="782b5-146">Select a zoom factor to zoom in or out on the report.</span></span>  
  
 <span data-ttu-id="782b5-147">**搜索文本**</span><span class="sxs-lookup"><span data-stu-id="782b5-147">**Search Text**</span></span>  
 <span data-ttu-id="782b5-148">输入文本，以在报表中搜索其匹配项。</span><span class="sxs-lookup"><span data-stu-id="782b5-148">Type text to search for a match within the report.</span></span> <span data-ttu-id="782b5-149">不能使用搜索运算符。</span><span class="sxs-lookup"><span data-stu-id="782b5-149">You cannot use search operators.</span></span> <span data-ttu-id="782b5-150">单击 **“查找”** 可以搜索第一个实例。</span><span class="sxs-lookup"><span data-stu-id="782b5-150">Click **Find** to search for the first instance.</span></span>  
  
 <span data-ttu-id="782b5-151">**查找**</span><span class="sxs-lookup"><span data-stu-id="782b5-151">**Find**</span></span>  
 <span data-ttu-id="782b5-152">选择此选项可以在报表中对搜索文本开始搜索。</span><span class="sxs-lookup"><span data-stu-id="782b5-152">Choose this option to begin searching the report for the search text.</span></span>  
  
 <span data-ttu-id="782b5-153">**查找下一个**</span><span class="sxs-lookup"><span data-stu-id="782b5-153">**Find Next**</span></span>  
 <span data-ttu-id="782b5-154">选择此选项可以对搜索文本的下一个实例进行搜索。</span><span class="sxs-lookup"><span data-stu-id="782b5-154">Choose this option to search for the next instance of the search text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="782b5-155">另请参阅</span><span class="sxs-lookup"><span data-stu-id="782b5-155">See Also</span></span>  
 <span data-ttu-id="782b5-156">[预览报表](../reports/previewing-reports.md) </span><span class="sxs-lookup"><span data-stu-id="782b5-156">[Previewing Reports](../reports/previewing-reports.md) </span></span>  
 [<span data-ttu-id="782b5-157">报表设计器的 F1 帮助</span><span class="sxs-lookup"><span data-stu-id="782b5-157">Report Designer F1 Help</span></span>](report-designer-f1-help.md)  
  
  
