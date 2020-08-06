---
title: 保存报表（报表生成器）| Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 59ddc4b8-9517-4d3f-9c88-a07e9907cecb
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9210eafb65ee7adced8d0cd821d88b5f0cbcb9c5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577351"
---
# <a name="saving-reports-report-builder"></a><span data-ttu-id="83306-102">保存报表（报表生成器）</span><span class="sxs-lookup"><span data-stu-id="83306-102">Saving Reports (Report Builder)</span></span>
  <span data-ttu-id="83306-103">在报表生成器中，可以将报表保存到您有写入权限的报表服务器、SharePoint 库和文件共享区，也可以将其保存到您的计算机。</span><span class="sxs-lookup"><span data-stu-id="83306-103">In Report Builder you can save a report to a report server, SharePoint library, file share on which you have write permission, or your computer.</span></span> <span data-ttu-id="83306-104">可以将报表保存到打开报表时的相同位置或将其保存到其他位置，也可以使用新名称将报表保存到相同或不同位置。</span><span class="sxs-lookup"><span data-stu-id="83306-104">You can save a report to the same location from which you opened it, save it to a different location, or save it with a new name to the same or different location.</span></span> <span data-ttu-id="83306-105">默认情况下，将报表重新保存到与其打开位置相同的位置。</span><span class="sxs-lookup"><span data-stu-id="83306-105">By default, a report is resaved to the location from which you opened it.</span></span> <span data-ttu-id="83306-106">保存报表时，真正保存的内容是报表定义，该定义描述了报表布局。</span><span class="sxs-lookup"><span data-stu-id="83306-106">When you save the report, what you are really saving is the report definition, which describes the report layout.</span></span> <span data-ttu-id="83306-107">您不是在保存数据。</span><span class="sxs-lookup"><span data-stu-id="83306-107">You are not saving the data.</span></span> <span data-ttu-id="83306-108">每次运行报表时，报表数据将刷新，它可能不同于您上次运行报表时的数据。</span><span class="sxs-lookup"><span data-stu-id="83306-108">Every time you run the report, the report data is refreshed and is likely to be different than the previous time you ran the report.</span></span>  
  
 <span data-ttu-id="83306-109">如果要将报表保存为另一格式或同时保存报表定义和数据，请使用以下 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 功能之一：</span><span class="sxs-lookup"><span data-stu-id="83306-109">If you want to save the report to a different format or save the report definition with the data, use one of the following [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] features:</span></span>  
  
-   <span data-ttu-id="83306-110">将呈现的报表导出为另一文件格式，如逗号分隔文件 (CSV) 或 Excel 工作簿，然后以该格式保存报表。</span><span class="sxs-lookup"><span data-stu-id="83306-110">Export a rendered report to a different file format such as comma separated files (CSV) or Excel workbooks and save the report in that format.</span></span> <span data-ttu-id="83306-111">还可以从报表生成数据馈送并保存报表数据。</span><span class="sxs-lookup"><span data-stu-id="83306-111">You can also generate data feeds from reports and save the report data.</span></span>  
  
-   <span data-ttu-id="83306-112">创建报表订阅以便传递和将报表保存到文件共享区。</span><span class="sxs-lookup"><span data-stu-id="83306-112">Create report subscriptions to deliver and save reports to a file share.</span></span>  
  
-   <span data-ttu-id="83306-113">使用报表历史记录功能将所呈现报表的各个版本作为历史记录副本保存。</span><span class="sxs-lookup"><span data-stu-id="83306-113">Use report history to save versions of rendered reports as historical copies.</span></span>  
  
 <span data-ttu-id="83306-114">若要了解有关直接在报表服务器上查看和管理报表的详细信息，请参阅 msdn.microsoft.com 上[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [联机丛书](https://go.microsoft.com/fwlink/?LinkId=154888)中的[查找、查看和管理报表（报表生成器和 SSRS）](finding-viewing-and-managing-reports-report-builder-and-ssrs.md)和 [Reporting Services 报表服务器（本机模式）](../report-server/reporting-services-report-server-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="83306-114">To learn more about viewing and managing reports directly on the report server, see [Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;](finding-viewing-and-managing-reports-report-builder-and-ssrs.md) and [Reporting Services Report Server &#40;Native Mode&#41;](../report-server/reporting-services-report-server-native-mode.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?LinkId=154888) on msdn.microsoft.com.</span></span>  
  
##  <a name="saving-report-definitions"></a><a name="SavingReportDefinitions"></a><span data-ttu-id="83306-115">保存报表定义</span><span class="sxs-lookup"><span data-stu-id="83306-115">Saving Report Definitions</span></span>  
 <span data-ttu-id="83306-116">尽管可以将报表保存到您的计算机，但是将报表保存到报表服务器更有利。</span><span class="sxs-lookup"><span data-stu-id="83306-116">Although you can save reports to your computer, saving reports to a report server offers many advantages.</span></span>  
  
 <span data-ttu-id="83306-117">将报表保存到报表服务器具有以下优势：</span><span class="sxs-lookup"><span data-stu-id="83306-117">Saving a report to a report server offers the following advantages:</span></span>  
  
-   <span data-ttu-id="83306-118">报表可供其他有权访问您保存报表的文件夹的用户使用。</span><span class="sxs-lookup"><span data-stu-id="83306-118">Reports become available to others who have permission to access the folder in which you saved the report.</span></span>  
  
-   <span data-ttu-id="83306-119">可以使用报表管理器来管理和查看报表。</span><span class="sxs-lookup"><span data-stu-id="83306-119">Reports can be managed and viewed from Report Manager.</span></span>  
  
-   <span data-ttu-id="83306-120">将报表资源（如数据源、图像和子报表）存储在一个位置以便于访问。</span><span class="sxs-lookup"><span data-stu-id="83306-120">Report resources such as data sources, images, and subreports are stored in one place for easier access.</span></span>  
  
-   <span data-ttu-id="83306-121">可以通过订阅将报表传递给其他用户。</span><span class="sxs-lookup"><span data-stu-id="83306-121">Reports can be delivered to others by subscriptions.</span></span>  
  
-   <span data-ttu-id="83306-122">报表安全存储在报表服务器数据库中。</span><span class="sxs-lookup"><span data-stu-id="83306-122">Reports are securely stored in the report server database.</span></span>  
  
-   <span data-ttu-id="83306-123">可以记录报表运行情况，提供性能和审核信息。</span><span class="sxs-lookup"><span data-stu-id="83306-123">Report runs can be logged and provide performance and auditing information.</span></span>  
  
 <span data-ttu-id="83306-124">将报表保存到报表服务器也称为发布报表。</span><span class="sxs-lookup"><span data-stu-id="83306-124">Saving a report to a report server is also known as publishing a report.</span></span> <span data-ttu-id="83306-125">保存报表时，只是保存报表定义。</span><span class="sxs-lookup"><span data-stu-id="83306-125">When you save the report you save the report definition only.</span></span> <span data-ttu-id="83306-126">每次运行报表时，报表数据将刷新，它可能不同于您上次运行报表时的数据。</span><span class="sxs-lookup"><span data-stu-id="83306-126">Every time you run the report, the report data is refreshed and likely different that the previous time you ran the report.</span></span> <span data-ttu-id="83306-127">如果要同时保存报表定义和数据，应使用报表历史记录功能。</span><span class="sxs-lookup"><span data-stu-id="83306-127">If you want to save the report definition with the data you should use the report history feature.</span></span> <span data-ttu-id="83306-128">使用此功能，您可以保存包含报表数据的报表副本。</span><span class="sxs-lookup"><span data-stu-id="83306-128">Using this feature, you save a copy of the report with its data.</span></span>  
  

  
##  <a name="exporting-and-saving-reports"></a><a name="ExportingAndSavingReports"></a> <span data-ttu-id="83306-129">导出和保存报表</span><span class="sxs-lookup"><span data-stu-id="83306-129">Exporting and Saving Reports</span></span>  
 <span data-ttu-id="83306-130">如果只有少量要存档的报表，可以考虑导出报表并将其另存为文件。</span><span class="sxs-lookup"><span data-stu-id="83306-130">If you have a small number of reports to archive, consider exporting a report and saving it as a file.</span></span> <span data-ttu-id="83306-131">在将报表导出到其他应用程序（如 PDF 或 Excel）后，您可以将其另存为文件，并放在网络上受保护的共享目录中。</span><span class="sxs-lookup"><span data-stu-id="83306-131">After you export a report to an application (such as PDF or Excel), you can save it as a file and place it in a protected shared directory on the network.</span></span> <span data-ttu-id="83306-132">或者，如果希望在报表服务器数据库中保留报表的所有副本（不论何种格式），则可以将已保存的 PDF 或 Excel 文件作为资源项上载。</span><span class="sxs-lookup"><span data-stu-id="83306-132">Alternatively, you can upload a saved PDF or Excel file as a resource item if you want to keep all copies of a report, regardless of the format, in the report server database.</span></span> <span data-ttu-id="83306-133">有关导出报表的详细信息，请参阅将[报表导出 &#40;报表生成器和 SSRS&#41;](export-reports-report-builder-and-ssrs.md)并[将文件或报表 &#40;报表管理器&#41;上传](../reports/upload-a-file-or-report-report-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="83306-133">For more information about exporting a report, see [Exporting Reports &#40;Report Builder and SSRS&#41;](export-reports-report-builder-and-ssrs.md) and [Upload a File or Report &#40;Report Manager&#41;](../reports/upload-a-file-or-report-report-manager.md).</span></span>  
  

  
##  <a name="using-file-share-delivery"></a><a name="UsingFileShareDelivery"></a> <span data-ttu-id="83306-134">使用文件共享传递</span><span class="sxs-lookup"><span data-stu-id="83306-134">Using File-Share Delivery</span></span>  
 <span data-ttu-id="83306-135">如果有大量要存档的报表，则可以创建订阅，将报表直接传递到文件系统。</span><span class="sxs-lookup"><span data-stu-id="83306-135">If you have a large number of reports to archive, create a subscription that delivers the report directly to the file system.</span></span> <span data-ttu-id="83306-136">对于这种方法，您必须为每个报表创建订阅，选择存储这些报表的共享文件夹，并制订用于指定文件创建时间的计划。</span><span class="sxs-lookup"><span data-stu-id="83306-136">For this approach, you must create a subscription for each report, choose a shared folder to store the reports, and define a schedule that determines when the file is created.</span></span> <span data-ttu-id="83306-137">一旦定义订阅，报表服务器即可在无人参与的情况下运行报表，并且使用提供的计划存档报表文件。</span><span class="sxs-lookup"><span data-stu-id="83306-137">Once you define a subscription, the report server can run the report unattended and add report files to the archive using the schedule that you provide.</span></span> <span data-ttu-id="83306-138">如果只是偶尔存档报表，您也可以创建一次性的计划。</span><span class="sxs-lookup"><span data-stu-id="83306-138">You can also create single-use schedules if you want to archive reports on an occasional basis.</span></span> <span data-ttu-id="83306-139">有关订阅和文件共享传递的详细信息，请参阅 SQL Server 联机丛书中 [Reporting Services 文档](https://go.microsoft.com/fwlink/?linkid=121312) 中的“Reporting Services 中的文件传递”。</span><span class="sxs-lookup"><span data-stu-id="83306-139">For more information about subscriptions and file share delivery, see "File Delivery in Reporting Services" in the [Reporting Services documentation](https://go.microsoft.com/fwlink/?linkid=121312) in SQL Server Books Online.</span></span>  
  

  
##  <a name="using-report-history"></a><a name="UsingReportHistory"></a> <span data-ttu-id="83306-140">使用报表历史记录</span><span class="sxs-lookup"><span data-stu-id="83306-140">Using Report History</span></span>  
 <span data-ttu-id="83306-141">您还可以使用报表历史记录功能创建历史记录副本。</span><span class="sxs-lookup"><span data-stu-id="83306-141">You can also use the report history feature to create historical copies.</span></span> <span data-ttu-id="83306-142">随后，您可以备份报表服务器数据库，将备份内容存储在安全的位置，以备将来使用。</span><span class="sxs-lookup"><span data-stu-id="83306-142">You can then back up the report server database and store the backup in a safe location for future use.</span></span> <span data-ttu-id="83306-143">所有报表历史记录（连同报表、共享数据源项、文件夹、订阅和共享计划）都存储在报表服务器数据库中。</span><span class="sxs-lookup"><span data-stu-id="83306-143">All report history (along with reports, shared data source items, folders, subscriptions, and shared schedules) is stored in the report server database.</span></span> <span data-ttu-id="83306-144">您可以通过创建备份来维护报表历史记录和元数据（如指定报表接收人的订阅信息）的永久副本。</span><span class="sxs-lookup"><span data-stu-id="83306-144">You can create a backup to maintain a permanent copy of report history and metadata such as subscription information that indicates the recipients of a report.</span></span> <span data-ttu-id="83306-145">有关详细信息，请参阅 SQL Server 联机丛书中 [Reporting Services 文档](https://go.microsoft.com/fwlink/?linkid=121312) 中的“管理报表历史记录”。</span><span class="sxs-lookup"><span data-stu-id="83306-145">For more information, see "Managing Report History" in the [Reporting Services documentation](https://go.microsoft.com/fwlink/?linkid=121312) in SQL Server Books Online.</span></span>  
  

  
##  <a name="how-to-topics"></a><a name="HowTo"></a><span data-ttu-id="83306-146">操作指南主题</span><span class="sxs-lookup"><span data-stu-id="83306-146">How-To Topics</span></span>  
  
-   [<span data-ttu-id="83306-147">将报表保存到报表服务器（报表生成器）</span><span class="sxs-lookup"><span data-stu-id="83306-147">Save Reports to a Report Server &#40;Report Builder&#41;</span></span>](save-reports-to-a-report-server-report-builder.md)  
  
-   [<span data-ttu-id="83306-148">将报表保存到 SharePoint 库（报表生成器）</span><span class="sxs-lookup"><span data-stu-id="83306-148">Save a Report to a SharePoint Library &#40;Report Builder&#41;</span></span>](save-a-report-to-a-sharepoint-library-report-builder.md)  
  
-   [<span data-ttu-id="83306-149">将报表保存到计算机 &#40;报表生成器&#41;</span><span class="sxs-lookup"><span data-stu-id="83306-149">Save Reports to Your Computer &#40;Report Builder&#41;</span></span>](../save-reports-to-your-computer-report-builder.md)  
  

  
## <a name="see-also"></a><span data-ttu-id="83306-150">另请参阅</span><span class="sxs-lookup"><span data-stu-id="83306-150">See Also</span></span>  
 <span data-ttu-id="83306-151">[报表、报表部件和报表定义 &#40;报表生成器和 SSRS&#41;](../report-design/reports-report-parts-and-report-definitions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="83306-151">[Reports, Report Parts, and Report Definitions &#40;Report Builder and SSRS&#41;](../report-design/reports-report-parts-and-report-definitions-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="83306-152">[安装、卸载和报表生成器支持](../install-uninstall-and-report-builder-support.md) </span><span class="sxs-lookup"><span data-stu-id="83306-152">[Install, Uninstall, and Report Builder Support](../install-uninstall-and-report-builder-support.md) </span></span>  
 <span data-ttu-id="83306-153">[查找、查看和管理 &#40;报表生成器和 SSRS 的报表 &#41;](finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="83306-153">[Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;](finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="83306-154">[导出报表 &#40;报表生成器和 SSRS&#41;](export-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="83306-154">[Exporting Reports &#40;Report Builder and SSRS&#41;](export-reports-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="83306-155">打印报表（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="83306-155">Print Reports &#40;Report Builder and SSRS&#41;</span></span>](print-reports-report-builder-and-ssrs.md)  
  
  
