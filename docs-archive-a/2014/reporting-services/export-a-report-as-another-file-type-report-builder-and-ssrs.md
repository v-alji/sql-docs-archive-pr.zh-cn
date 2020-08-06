---
title: 将报表导出为其他文件类型 (报表生成器和 SSRS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: b577568b-ecbd-44c3-be88-31dab6fc38a2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 240d3266b7b8c9a445658a9fd21fb9ea18a4c113
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682750"
---
# <a name="export-a-report-as-another-file-type-report-builder-and-ssrs"></a><span data-ttu-id="beb29-102">将报表导出为其他文件类型（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="beb29-102">Export a Report as Another File Type (Report Builder and SSRS)</span></span>
  <span data-ttu-id="beb29-103">在报表生成器或报表设计器中预览报表时，可以将报表呈现为其他文件格式，如 CSV、图像、PDF、 [!INCLUDE[ofprword](../includes/ofprword-md.md)]或 [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)]；也可以在查看报表服务器上的报表时呈现报表。</span><span class="sxs-lookup"><span data-stu-id="beb29-103">You can render a report to another file format, such as CSV, Image, PDF, [!INCLUDE[ofprword](../includes/ofprword-md.md)], or [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)], while previewing your report in Report Builder or Report Designer, or you can render the report while viewing the report on the report server.</span></span> <span data-ttu-id="beb29-104">如果希望立即将报表另存为其他文件类型而不将报表发布到报表服务器，或者希望查看报表设计在以特定格式传递给报表读者时的显示效果，则以特定格式呈现报表将非常有用。</span><span class="sxs-lookup"><span data-stu-id="beb29-104">Rendering the report in a specific format in is helpful when you want to immediately save the report as another file type without publishing the report to the report server or when you want to see how your report design will appear when delivered to your report readers in a specific format.</span></span> <span data-ttu-id="beb29-105">在设置订阅或通过电子邮件传递报表时，或者希望保存报表服务器上可用的报表时，呈现报表服务器上的报表将非常有用。</span><span class="sxs-lookup"><span data-stu-id="beb29-105">Rendering the report on the report server is useful when you set up subscriptions or deliver your reports via e-mail, or if you want to save a report that is available on the report server.</span></span> <span data-ttu-id="beb29-106">有关详细信息，请参阅[订阅和传递 (Reporting Services)](subscriptions/subscriptions-and-delivery-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="beb29-106">For more information, see [Subscriptions and Delivery &#40;Reporting Services&#41;](subscriptions/subscriptions-and-delivery-reporting-services.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../includes/ssrbrddup-md.md)]  
  
### <a name="to-export-a-report-as-another-file-type-in-report-builder"></a><span data-ttu-id="beb29-107">在报表生成器中将报表导出为其他文件类型</span><span class="sxs-lookup"><span data-stu-id="beb29-107">To export a report as another file type in Report Builder</span></span>  
  
1.  <span data-ttu-id="beb29-108">预览报表。</span><span class="sxs-lookup"><span data-stu-id="beb29-108">Preview the report.</span></span>  
  
2.  <span data-ttu-id="beb29-109">在功能区上，单击 **“导出”**。</span><span class="sxs-lookup"><span data-stu-id="beb29-109">On the ribbon, click **Export**.</span></span>  
  
3.  <span data-ttu-id="beb29-110">选择要使用的格式。</span><span class="sxs-lookup"><span data-stu-id="beb29-110">Select the format that you want to use.</span></span>  
  
     <span data-ttu-id="beb29-111">此时会打开“另存为”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="beb29-111">The **Save As** dialog box opens.</span></span> <span data-ttu-id="beb29-112">默认情况下，文件名为所导出报表的名称。</span><span class="sxs-lookup"><span data-stu-id="beb29-112">By default, the file name is that of the report that you exported.</span></span> <span data-ttu-id="beb29-113">也可更改该文件名。</span><span class="sxs-lookup"><span data-stu-id="beb29-113">Optionally, you can change the file name.</span></span>  
  
4.  <span data-ttu-id="beb29-114">导航到保存导出报表的位置并打开此报表。</span><span class="sxs-lookup"><span data-stu-id="beb29-114">Navigate to the location where you saved the exported report and open it.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="beb29-115">如果由于您没有与此文件类型关联的程序而导致程序无法以所选格式打开此报表，系统会提示您保存导出的报表或在线查找可打开此报表的程序。</span><span class="sxs-lookup"><span data-stu-id="beb29-115">If the program cannot open the report in the format that you chose because you do not have a program associated with this file type, you will be prompted to save the exported report or to find a program online to open the report.</span></span>  
  
### <a name="to-export-a-report-as-another-file-type-in-report-manager"></a><span data-ttu-id="beb29-116">在报表管理器中将报表导出为其他文件类型</span><span class="sxs-lookup"><span data-stu-id="beb29-116">To export a report as another file type in Report Manager</span></span>  
  
1.  <span data-ttu-id="beb29-117">从报表管理器的 **“主页”** 导航至要导出的报表。</span><span class="sxs-lookup"><span data-stu-id="beb29-117">From the Report Manager **Home** page, navigate to the report that you want to export.</span></span>  
  
2.  <span data-ttu-id="beb29-118">单击该报表。</span><span class="sxs-lookup"><span data-stu-id="beb29-118">Click the report.</span></span>  
  
     <span data-ttu-id="beb29-119">即会生成该报表。</span><span class="sxs-lookup"><span data-stu-id="beb29-119">The report is generated.</span></span>  
  
3.  <span data-ttu-id="beb29-120">在报表查看器工具栏上，单击 **“选择格式”** 下拉箭头。</span><span class="sxs-lookup"><span data-stu-id="beb29-120">On the Report Viewer toolbar, click the **Select a format** drop-down arrow.</span></span>  
  
4.  <span data-ttu-id="beb29-121">选择要使用的格式。</span><span class="sxs-lookup"><span data-stu-id="beb29-121">Select the format that you want to use.</span></span>  
  
5.  <span data-ttu-id="beb29-122">单击“导出”  。</span><span class="sxs-lookup"><span data-stu-id="beb29-122">Click **Export**.</span></span>  
  
     <span data-ttu-id="beb29-123">将出现一条消息，询问是要打开还是要保存该文件。</span><span class="sxs-lookup"><span data-stu-id="beb29-123">A message appears asking you if you want to open or save the file.</span></span>  
  
6.  <span data-ttu-id="beb29-124">若要以选定的导出格式查看该报表，请单击 **“打开”**。</span><span class="sxs-lookup"><span data-stu-id="beb29-124">To view the report in the selected export format, click **Open**.</span></span>  
  
     <span data-ttu-id="beb29-125">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="beb29-125">\- or -</span></span>  
  
     <span data-ttu-id="beb29-126">若要立即以选定的导出格式保存该报表，请单击 **“保存”**。</span><span class="sxs-lookup"><span data-stu-id="beb29-126">To immediately save the report in the selected export format, click **Save**.</span></span>  
  
     <span data-ttu-id="beb29-127">将使用与所选格式关联的应用程序显示或保存该报表。</span><span class="sxs-lookup"><span data-stu-id="beb29-127">Using the application that is associated with the format that you chose, the report is either displayed or saved.</span></span> <span data-ttu-id="beb29-128">如果单击 **“保存”**，系统将提示您指定保存报表的位置。</span><span class="sxs-lookup"><span data-stu-id="beb29-128">If you click **Save**, you will be prompted for a location where you can save your report.</span></span>  
  
     <span data-ttu-id="beb29-129">**注意** 如果因没有与此文件类型关联的程序而导致程序无法以您所选的格式打开此报表，系统会提示您保存导出的报表或在线查找可打开此报表的程序。</span><span class="sxs-lookup"><span data-stu-id="beb29-129">**Note** If the program cannot open the report in the format that you chose because you do not have a program associated with this file type, you will be prompted to save the exported report or to find a program online to open the report.</span></span>  
  
### <a name="to-export-a-report-as-another-file-type-in-a-sharepoint-library"></a><span data-ttu-id="beb29-130">在 SharePoint 库中将报表导出为其他文件类型</span><span class="sxs-lookup"><span data-stu-id="beb29-130">To export a report as another file type in a SharePoint library</span></span>  
  
1.  <span data-ttu-id="beb29-131">预览报表。</span><span class="sxs-lookup"><span data-stu-id="beb29-131">Preview the report.</span></span>  
  
2.  <span data-ttu-id="beb29-132">在工具栏上，单击 **“操作”**，指向 **“导出”**，然后选择要使用的格式。</span><span class="sxs-lookup"><span data-stu-id="beb29-132">On the toolbar, click **Actions**, point to **Export**, and then select the format that you want to use.</span></span>  
  
     <span data-ttu-id="beb29-133">将打开 **“文件下载”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="beb29-133">The **File Download** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="beb29-134">若要以选定的导出格式查看该报表，请单击 **“打开”**。</span><span class="sxs-lookup"><span data-stu-id="beb29-134">To view the report in the selected export format, click **Open**.</span></span>  
  
     <span data-ttu-id="beb29-135">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="beb29-135">\- or -</span></span>  
  
     <span data-ttu-id="beb29-136">若要立即以选定的导出格式保存该报表，请单击 **“保存”**。</span><span class="sxs-lookup"><span data-stu-id="beb29-136">To immediately save the report in the selected export format, click **Save**.</span></span>  
  
     <span data-ttu-id="beb29-137">将使用与所选格式关联的应用程序显示或保存该报表。</span><span class="sxs-lookup"><span data-stu-id="beb29-137">Using the application that is associated with the format that you chose, the report is either displayed or saved.</span></span> <span data-ttu-id="beb29-138">如果单击 **“保存”**，系统将提示您指定保存报表的位置。</span><span class="sxs-lookup"><span data-stu-id="beb29-138">If you click **Save**, you will be prompted for a location where you can save your report.</span></span>  
  
     <span data-ttu-id="beb29-139">还可以选择更改导出的报表的文件名。</span><span class="sxs-lookup"><span data-stu-id="beb29-139">Optionally, change the file name of the exported report.</span></span>  
  
     <span data-ttu-id="beb29-140">**注意** 如果因没有与此文件类型关联的程序而导致程序无法以您所选的格式打开此报表，系统会提示您保存导出的报表或在线查找可打开此报表的程序。</span><span class="sxs-lookup"><span data-stu-id="beb29-140">**Note** If the program cannot open the report in the format that you chose because you do not have a program associated with this file type, you will be prompted to save the exported report or to find a program online to open the report.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="beb29-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="beb29-141">See Also</span></span>  
 <span data-ttu-id="beb29-142">[导出报表 &#40;报表生成器和 SSRS&#41;](report-builder/export-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="beb29-142">[Exporting Reports &#40;Report Builder and SSRS&#41;](report-builder/export-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="beb29-143">[Reporting Services &#40;报表生成器和 SSRS 中的分页&#41;](report-design/pagination-in-reporting-services-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="beb29-143">[Pagination in Reporting Services &#40;Report Builder  and SSRS&#41;](report-design/pagination-in-reporting-services-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="beb29-144">不同报表呈现扩展插件的交互功能（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="beb29-144">Interactive Functionality for Different Report Rendering Extensions &#40;Report Builder and SSRS&#41;</span></span>](report-builder/interactive-functionality-different-report-rendering-extensions.md)  
  
  
