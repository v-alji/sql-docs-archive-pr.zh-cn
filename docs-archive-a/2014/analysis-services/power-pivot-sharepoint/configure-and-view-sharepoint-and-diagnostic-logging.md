---
title: 配置和查看 SharePoint 日志文件和诊断日志记录 (PowerPivot for SharePoint) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 85f62d29-cdc6-45b3-be1f-ff1182939858
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5c031614b0b55560c5b03b7235a6cc0a73023807
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589913"
---
# <a name="configure-and-view-sharepoint-log-files--and-diagnostic-logging-powerpivot-for-sharepoint"></a><span data-ttu-id="c5b4b-102">配置和查看 SharePoint 日志文件和诊断日志记录 (PowerPivot for SharePoint)</span><span class="sxs-lookup"><span data-stu-id="c5b4b-102">Configure and View SharePoint Log Files  and Diagnostic Logging (PowerPivot for SharePoint)</span></span>
  [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] <span data-ttu-id="c5b4b-103">服务器操作、事件和消息均记录在 SharePoint 日志文件中。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-103">server operations, events, and messages are recorded in SharePoint log files.</span></span> <span data-ttu-id="c5b4b-104">使用此主题中的信息可配置日志记录级别和查看日志文件信息。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-104">Use the information in this topic to configure logging levels and view log file information.</span></span> <span data-ttu-id="c5b4b-105">您可以控制要将哪些 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 服务器事件记录到文件中。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-105">You can control which [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] server events are logged to the file.</span></span> <span data-ttu-id="c5b4b-106">还可以控制所记录的消息的严重性。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-106">You can also control the severity of messages that are logged.</span></span> <span data-ttu-id="c5b4b-107">有关详细信息，请参阅[为 &#40;PowerPivot for SharePoint 配置使用情况数据收集](configure-usage-data-collection-for-power-pivot-for-sharepoint.md)。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-107">For more information, see [Configure Usage Data Collection for &#40;PowerPivot for SharePoint](configure-usage-data-collection-for-power-pivot-for-sharepoint.md).</span></span>  
  
 <span data-ttu-id="c5b4b-108">本主题内容：</span><span class="sxs-lookup"><span data-stu-id="c5b4b-108">In this topic:</span></span>  
  
-   [<span data-ttu-id="c5b4b-109">日志文件位置</span><span class="sxs-lookup"><span data-stu-id="c5b4b-109">Log File Location</span></span>](#bkmk_filelocation)  
  
-   [<span data-ttu-id="c5b4b-110">修改单独事件类别的诊断日志记录级别</span><span class="sxs-lookup"><span data-stu-id="c5b4b-110">Modify diagnostic logging levels for individual event categories</span></span>](#bkmk_modifyloglevels)  
  
-   [<span data-ttu-id="c5b4b-111">如何查看 SharePoint 日志文件</span><span class="sxs-lookup"><span data-stu-id="c5b4b-111">How to View SharePoint Log Files</span></span>](#bkmk_how2viewlogfiles)  
  
##  <a name="log-file-location"></a><a name="bkmk_filelocation"></a><span data-ttu-id="c5b4b-112">日志文件位置</span><span class="sxs-lookup"><span data-stu-id="c5b4b-112">Log File Location</span></span>  
 <span data-ttu-id="c5b4b-113">默认情况下，SharePoint 日志文件保存到以下位置：</span><span class="sxs-lookup"><span data-stu-id="c5b4b-113">By default, SharePoint log files are saved to the following location:</span></span>  
  
 `C:\Program files\Common Files\Microsoft Shared\Web Server Extensions\14\LOGS`  
  
 <span data-ttu-id="c5b4b-114">LOGS 文件夹包含日志文件 (`.log`)、数据文件 (`.txt`) 和使用情况文件 (`.usage`)。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-114">The LOGS folder contains log files (`.log`), data files (`.txt`), and usage files (`.usage`).</span></span> <span data-ttu-id="c5b4b-115">SharePoint 跟踪日志的文件命名约定是服务器名称后跟日期和时间戳。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-115">The file naming convention for a SharePoint trace log is the server name followed by a date and time stamp.</span></span> <span data-ttu-id="c5b4b-116">SharePoint 跟踪日志会定期创建并在每次运行 IISRESET 时创建。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-116">SharePoint trace logs are created at regular intervals and whenever there is an IISRESET.</span></span> <span data-ttu-id="c5b4b-117">24 小时的时段中有多个跟踪日志是常见现象。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-117">It is common to have many trace logs within a 24 hour period.</span></span>  
  
##  <a name="modify-diagnostic-logging-levels-for-individual-event-categories"></a><a name="bkmk_modifyloglevels"></a><span data-ttu-id="c5b4b-118">修改各个事件类别的诊断日志记录级别</span><span class="sxs-lookup"><span data-stu-id="c5b4b-118">Modify diagnostic logging levels for individual event categories</span></span>  
 <span data-ttu-id="c5b4b-119">默认情况下，PowerPivot 事件的 ULS 日志记录设置为“中” \*\*。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-119">By default, ULS logging of PowerPivot events is set at *Medium*.</span></span> <span data-ttu-id="c5b4b-120">此设置是 SQL Server 2012 中新增的设置。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-120">This setting is new for SQL Server 2012.</span></span> <span data-ttu-id="c5b4b-121">如果您是从先前版本升级的服务器，日志记录级别可能仍设置为“详细” \*\*，这是 SQL Server 2008 R2 中的默认级别。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-121">If you upgraded a server from the prior release, the logging level might still be set at *Verbose*, the default level in SQL Server 2008 R2.</span></span> <span data-ttu-id="c5b4b-122">如果您习惯于查看 PowerPivot 服务器使用信息的 ULS 日志，您会发现经过这一修改，PowerPivot 服务器操作的相关信息已经减少。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-122">If you are accustomed to reviewing the ULS logs for PowerPivot server usage information, you will notice that as a result of this change, there is less information about PowerPivot server operations.</span></span>  
  
 <span data-ttu-id="c5b4b-123">除了异常（类型为“高” \*\*），所有 PowerPivot 消息均属于“详细”类别。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-123">Except for exceptions, which are of type *High*, all PowerPivot messages fall into the Verbose category.</span></span> <span data-ttu-id="c5b4b-124">如果要将日常服务器操作（如连接、请求或查询报告）等条目记入日志，则必须将日志记录级别设置为“详细”。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-124">If you want log entries for routine server operations such as connections, requests, or query reporting, you must change the logging level to Verbose.</span></span>  
  
 <span data-ttu-id="c5b4b-125">修改各个事件类别的诊断日志记录级别：</span><span class="sxs-lookup"><span data-stu-id="c5b4b-125">To modify diagnostic logging levels for individual event categories:</span></span>  
  
1.  <span data-ttu-id="c5b4b-126">在 SharePoint 管理中心中，单击 **“监视”**。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-126">In SharePoint Central Administration, click **Monitoring**.</span></span>  
  
2.  <span data-ttu-id="c5b4b-127">单击 **“配置诊断日志记录”**。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-127">Click **Configure diagnostic logging**.</span></span>  
  
3.  <span data-ttu-id="c5b4b-128">滚动到 **“PowerPivot 服务”**。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-128">Scroll to **PowerPivot Service**.</span></span>  
  
4.  <span data-ttu-id="c5b4b-129">展开类别，然后选择单独类别。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-129">Expand the category and select individual categories.</span></span>  
  
     <span data-ttu-id="c5b4b-130">**“应用程序页请求”** 指定在定位 [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] 以便加载 PowerPivot 数据源以及与场中的其他服务器通信时，服务应用程序触发的事件。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-130">**Application Page Request** specifies events triggered by the service application when locating a [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] for loading a PowerPivot data source and communicating with other servers in the farm.</span></span>  
  
     <span data-ttu-id="c5b4b-131">**“请求处理”** 根据场中服务器上加载的 PowerPivot 数据库指定查询请求触发的事件。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-131">**Request Processing** specifies events triggered by query requests against a PowerPivot database that is loaded on a server in the farm.</span></span>  
  
     <span data-ttu-id="c5b4b-132">**“使用情况”** 指定与 PowerPivot 使用情况数据收集相关的事件。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-132">**Usage** specifies an event related to PowerPivot usage data collection.</span></span>  
  
5.  <span data-ttu-id="c5b4b-133">在“要报告给事件日志的严重程度最低的事件”中，选择 **“无”** 将禁用该类别的事件日志记录，选择 **“错误”** 将只记录错误事件。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-133">In Least critical event to report to the event log, select **None** to disable event logging for the category, or **Error** to limit logging for just errors.</span></span>  
  
6.  <span data-ttu-id="c5b4b-134">选择 **“详细”** ，可将所有事件记录到事件日志中。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-134">Select **Verbose** to log all events to the event log.</span></span>  
  
7.  <span data-ttu-id="c5b4b-135">在“要报告给跟踪日志的严重程度最低的事件”中，选择 **“无”** 将禁用该类别的跟踪，选择 **“错误”** 将只跟踪错误。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-135">In Least critical event to report to the trace log, select **None** to disable tracing for the category, or **Error** to limit tracing for just errors.</span></span>  
  
8.  <span data-ttu-id="c5b4b-136">选择 **“详细”** ，可将所有事件记录到跟踪日志中。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-136">Select **Verbose** to log all events to the trace log.</span></span>  
  
9. <span data-ttu-id="c5b4b-137">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-137">Click **OK**.</span></span>  
  
##  <a name="how-to-view-sharepoint-log-files"></a><a name="bkmk_how2viewlogfiles"></a><span data-ttu-id="c5b4b-138">如何查看 SharePoint 日志文件</span><span class="sxs-lookup"><span data-stu-id="c5b4b-138">How to View SharePoint Log Files</span></span>  
 <span data-ttu-id="c5b4b-139">日志文件是文本文件。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-139">Log files are text files.</span></span> <span data-ttu-id="c5b4b-140">可以在任何文本编辑器中打开它们。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-140">You can open them in any text editor.</span></span> <span data-ttu-id="c5b4b-141">还可以使用第三方日志查看器应用程序。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-141">You can also use third-party log viewer applications.</span></span>  
  
#### <a name="use-a-text-editor"></a><span data-ttu-id="c5b4b-142">使用文本编辑器</span><span class="sxs-lookup"><span data-stu-id="c5b4b-142">Use a Text Editor</span></span>  
 <span data-ttu-id="c5b4b-143">如果使用文本编辑器排除 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 服务器错误，下列提示可帮助您在文件中定位相关信息：</span><span class="sxs-lookup"><span data-stu-id="c5b4b-143">If you are using a text editor to troubleshoot a [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] server error, the following tips can help you locate relevant information in the file:</span></span>  
  
-   <span data-ttu-id="c5b4b-144">对于与发布、查看或刷新 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 工作簿相关的错误，在日志文件中搜索工作簿的名称。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-144">For errors related to publishing, viewing, or refreshing a [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] workbook, search the log file for the name of the workbook.</span></span>  
  
-   <span data-ttu-id="c5b4b-145">对于提供了相关 ID 的错误，复制 ID 并将其用作在日志文件中搜索时的搜索项。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-145">For errors that provide a correlation ID, copy the ID and use it as a search term in the log file.</span></span>  
  
-   <span data-ttu-id="c5b4b-146">搜索错误状态“高”或“异常”。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-146">Search for error status "High" or "Exception".</span></span> <span data-ttu-id="c5b4b-147">搜索 "PowerPivot 服务"。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-147">Search for "PowerPivot Service".</span></span>  
  
-   <span data-ttu-id="c5b4b-148">如果知道发生错误的时间，使用日期和时间信息来缩小必须搜索的条目范围。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-148">If you know when the error occurred, use the date and time information to narrow the scope of entries you must scroll through.</span></span>  
  
#### <a name="use-a-log-viewer-application"></a><span data-ttu-id="c5b4b-149">使用日志查看器应用程序</span><span class="sxs-lookup"><span data-stu-id="c5b4b-149">Use a Log Viewer Application</span></span>  
 <span data-ttu-id="c5b4b-150">尽管可以使用文本编辑器来逐个查看跟踪日志，但是允许您将多个日志文件一起查看的日志查看器应用程序会有用得多。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-150">Although you can use a text editor to view the trace logs individually, a log viewer application that enables you to view several log files together can be far more useful.</span></span> <span data-ttu-id="c5b4b-151">幸运的是，Codeplex 网站上有多个第三方日志查看器应用程序可供下载，这些应用程序可帮助您在单个工作区中查看多个跟踪日志。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-151">Fortunately, there are several third-party log viewer applications available for download on the Codeplex site that can help you view multiple trace logs in a single workspace.</span></span>  
  
 <span data-ttu-id="c5b4b-152">下面的说明包含指向您可以从 Codeplex 下载的常用 SharePoint ULS 日志查看器的链接。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-152">The following instructions include links to popular SharePoint ULS Log Viewers that you can download from Codeplex.</span></span>  
  
1.  <span data-ttu-id="c5b4b-153">转到 Codeplex 站点上的 [SharePoint 日志查看器](http://sharepointlogviewer.codeplex.com) 或 [SharePoint ULS 日志查看器](https://go.microsoft.com/fwlink/?LinkId=150052) 。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-153">Go to [SharePoint LogViewer](http://sharepointlogviewer.codeplex.com) or [SharePoint ULS Log Viewer](https://go.microsoft.com/fwlink/?LinkId=150052) on the Codeplex site.</span></span>  
  
2.  <span data-ttu-id="c5b4b-154">单击 **“Downloads”** （下载）选项卡。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-154">Click the **Downloads** tab.</span></span>  
  
3.  <span data-ttu-id="c5b4b-155">单击可执行文件。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-155">Click the executable file.</span></span> <span data-ttu-id="c5b4b-156">该可执行文件是 **SharePointLogViewer.exe** 或 **ULS Viewer 2.0 Binary**。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-156">It will either be **SharePointLogViewer.exe** or **ULS Viewer 2.0 Binary**.</span></span>  
  
4.  <span data-ttu-id="c5b4b-157">阅读并接受许可条款。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-157">Read and accept the licensing terms.</span></span>  
  
5.  <span data-ttu-id="c5b4b-158">单击 **“保存”** 以将该软件保存到您的本地系统上。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-158">Click **Save** to download the software to your local system.</span></span>  
  
     <span data-ttu-id="c5b4b-159">如果您正在下载 SharePoint ULS 日志查看器，则将 ULSViewer.zip 保存到下载文件夹。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-159">If you are downloading SharePoint ULS Log Viewer, save ULSViewer.zip to the Downloads folder.</span></span>  
  
6.  <span data-ttu-id="c5b4b-160">在 Downloads 文件夹中，右键单击 ULSViewer.zip 并选择 **“全部提取”**。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-160">In the Downloads folder, right-click ULSViewer.zip and select **Extract All**.</span></span>  
  
7.  <span data-ttu-id="c5b4b-161">指定目标文件夹，然后单击 **“提取”**。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-161">Specify a destination folder, and then click **Extract**.</span></span>  
  
8.  <span data-ttu-id="c5b4b-162">在包含所提取的程序文件的文件夹中，双击 **ULSViewer** 并运行该应用程序。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-162">In the folder that contains the extracted program files, double-click **ULSViewer** and run the application.</span></span>  
  
9. <span data-ttu-id="c5b4b-163">单击位于应用程序窗口左上角的文件夹图标。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-163">Click the folder icon at the top left corner of the application window.</span></span>  
  
10. <span data-ttu-id="c5b4b-164">浏览到 \Program files\Common Files\Microsoft Shared\Web Server Extensions\14\Logs。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-164">Browse to \Program files\Common Files\Microsoft Shared\Web Server Extensions\14\Logs.</span></span>  
  
11. <span data-ttu-id="c5b4b-165">选择一个或多个跟踪日志。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-165">Select one or more trace logs.</span></span> <span data-ttu-id="c5b4b-166">默认情况下，跟踪日志文件名由计算机名加上日期和时间信息组成。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-166">By default, trace log file names consist of the computer name plus date and time information.</span></span> <span data-ttu-id="c5b4b-167">文件类型为“文本文档”。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-167">The file type is Text Document.</span></span>  
  
12. <span data-ttu-id="c5b4b-168">单击 **“打开”** 并等待文件加载。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-168">Click **Open** and wait for the files to load.</span></span>  
  
13. <span data-ttu-id="c5b4b-169">使用内置筛选器，基于严重性、进程、类别或用户定义的文本文件来选择记录。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-169">Use the built-in filters to select records based on severity, process, category, or a user-defined text file.</span></span> <span data-ttu-id="c5b4b-170">还可以单击列标题更改排序顺序。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-170">You can also click column headings to change the sort order.</span></span>  
  
#### <a name="entries-for-powerpivot-services"></a><span data-ttu-id="c5b4b-171">针对 PowerPivot Services 的条目</span><span class="sxs-lookup"><span data-stu-id="c5b4b-171">Entries for PowerPivot Services</span></span>  
 <span data-ttu-id="c5b4b-172">下表描述了 SharePoint 日志文件中最可能存在的针对 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 服务器操作的条目。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-172">The following table describes entries for [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] server operations most likely to be found in a SharePoint log file.</span></span>  
  
|<span data-ttu-id="c5b4b-173">进程</span><span class="sxs-lookup"><span data-stu-id="c5b4b-173">Process</span></span>|<span data-ttu-id="c5b4b-174">区域</span><span class="sxs-lookup"><span data-stu-id="c5b4b-174">Area</span></span>|<span data-ttu-id="c5b4b-175">类别</span><span class="sxs-lookup"><span data-stu-id="c5b4b-175">Category</span></span>|<span data-ttu-id="c5b4b-176">级别</span><span class="sxs-lookup"><span data-stu-id="c5b4b-176">Level</span></span>|<span data-ttu-id="c5b4b-177">消息</span><span class="sxs-lookup"><span data-stu-id="c5b4b-177">Message</span></span>|<span data-ttu-id="c5b4b-178">详细信息</span><span class="sxs-lookup"><span data-stu-id="c5b4b-178">Details</span></span>|  
|-------------|----------|--------------|-----------|-------------|-------------|  
|<span data-ttu-id="c5b4b-179">w3wp.exe</span><span class="sxs-lookup"><span data-stu-id="c5b4b-179">w3wp.exe</span></span>|<span data-ttu-id="c5b4b-180">“PowerPivot 服务”</span><span class="sxs-lookup"><span data-stu-id="c5b4b-180">PowerPivot Service</span></span>|<span data-ttu-id="c5b4b-181">使用情况</span><span class="sxs-lookup"><span data-stu-id="c5b4b-181">Usage</span></span>|<span data-ttu-id="c5b4b-182">“详细”</span><span class="sxs-lookup"><span data-stu-id="c5b4b-182">Verbose</span></span>|<span data-ttu-id="c5b4b-183">不存在当前请求统计信息，无信息可供记录。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-183">There are no current request statistics, nothing to log.</span></span>|<span data-ttu-id="c5b4b-184">按照预定义的间隔，服务将查询响应统计信息作为使用情况事件向使用情况数据收集系统报告。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-184">At predefined intervals, the service reports query response statistics as a usage event to the usage data collection system.</span></span> <span data-ttu-id="c5b4b-185">此消息指示没有查询统计信息可供报告。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-185">This message indicates there were no query statistics to report.</span></span>|  
|<span data-ttu-id="c5b4b-186">w3wp.exe</span><span class="sxs-lookup"><span data-stu-id="c5b4b-186">w3wp.exe</span></span>|<span data-ttu-id="c5b4b-187">“PowerPivot 服务”</span><span class="sxs-lookup"><span data-stu-id="c5b4b-187">PowerPivot Service</span></span>|<span data-ttu-id="c5b4b-188">Web 前端</span><span class="sxs-lookup"><span data-stu-id="c5b4b-188">Web front end</span></span>|<span data-ttu-id="c5b4b-189">“详细”</span><span class="sxs-lookup"><span data-stu-id="c5b4b-189">Verbose</span></span>|<span data-ttu-id="c5b4b-190">开始查找数据源的应用程序服务器 =\<*path*></span><span class="sxs-lookup"><span data-stu-id="c5b4b-190">Starting to locate an application server for data source=\<*path*></span></span>|<span data-ttu-id="c5b4b-191">收到连接请求时， [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 服务确定可用的 [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] 以处理该请求。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-191">When it receives a connection request, the [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] service identifies an available [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] to handle the request.</span></span> <span data-ttu-id="c5b4b-192">如果场中只有一个服务器，则在所有情况下都是本地服务器接受请求。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-192">If there is only one server in the farm, the local server accepts the request in all cases.</span></span>|  
|<span data-ttu-id="c5b4b-193">w3wp.exe</span><span class="sxs-lookup"><span data-stu-id="c5b4b-193">w3wp.exe</span></span>|<span data-ttu-id="c5b4b-194">“PowerPivot 服务”</span><span class="sxs-lookup"><span data-stu-id="c5b4b-194">PowerPivot Service</span></span>|<span data-ttu-id="c5b4b-195">Web 前端</span><span class="sxs-lookup"><span data-stu-id="c5b4b-195">Web front end</span></span>|<span data-ttu-id="c5b4b-196">“详细”</span><span class="sxs-lookup"><span data-stu-id="c5b4b-196">Verbose</span></span>|<span data-ttu-id="c5b4b-197">定位应用程序服务器成功。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-197">Locating the application server succeeded.</span></span>|<span data-ttu-id="c5b4b-198">请求已分配到 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 服务应用程序。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-198">The request was allocated to a [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] service application.</span></span>|  
|<span data-ttu-id="c5b4b-199">w3wp.exe</span><span class="sxs-lookup"><span data-stu-id="c5b4b-199">w3wp.exe</span></span>|<span data-ttu-id="c5b4b-200">“PowerPivot 服务”</span><span class="sxs-lookup"><span data-stu-id="c5b4b-200">PowerPivot Service</span></span>|<span data-ttu-id="c5b4b-201">Web 前端</span><span class="sxs-lookup"><span data-stu-id="c5b4b-201">Web front end</span></span>|<span data-ttu-id="c5b4b-202">“详细”</span><span class="sxs-lookup"><span data-stu-id="c5b4b-202">Verbose</span></span>|<span data-ttu-id="c5b4b-203">将请求重定向 \<*PowerPivotdata source*> 到 [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-203">Redirecting request for the \<*PowerPivotdata source*> to the [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)].</span></span>|<span data-ttu-id="c5b4b-204">请求已转发给 [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-204">The request was forwarded to the [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)].</span></span>|  
|<span data-ttu-id="c5b4b-205">w3wp.exe</span><span class="sxs-lookup"><span data-stu-id="c5b4b-205">w3wp.exe</span></span>|<span data-ttu-id="c5b4b-206">“PowerPivot 服务”</span><span class="sxs-lookup"><span data-stu-id="c5b4b-206">PowerPivot Service</span></span>|<span data-ttu-id="c5b4b-207">请求处理</span><span class="sxs-lookup"><span data-stu-id="c5b4b-207">Request Processing</span></span>|<span data-ttu-id="c5b4b-208">“详细”</span><span class="sxs-lookup"><span data-stu-id="c5b4b-208">Verbose</span></span>|<span data-ttu-id="c5b4b-209">将用户名请求重定向 \<*SharePoint user*> 到数据库</span><span class="sxs-lookup"><span data-stu-id="c5b4b-209">Redirecting request for UserName\<*SharePoint user*> to the database</span></span>|<span data-ttu-id="c5b4b-210">已代表 SharePoint 用户创建了与 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 数据源的模拟连接。</span><span class="sxs-lookup"><span data-stu-id="c5b4b-210">An impersonated connection to the [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] data source was created on behalf of the SharePoint user.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c5b4b-211">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c5b4b-211">See Also</span></span>  
 <span data-ttu-id="c5b4b-212">[PowerPivot 使用情况数据收集](power-pivot-usage-data-collection.md) </span><span class="sxs-lookup"><span data-stu-id="c5b4b-212">[PowerPivot Usage Data Collection](power-pivot-usage-data-collection.md) </span></span>  
 <span data-ttu-id="c5b4b-213">[查看和读取 SQL Server 安装程序日志文件](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md) </span><span class="sxs-lookup"><span data-stu-id="c5b4b-213">[View and Read SQL Server Setup Log Files](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md) </span></span>  
 [<span data-ttu-id="c5b4b-214">为 &#40;配置使用情况数据收集 PowerPivot for SharePoint</span><span class="sxs-lookup"><span data-stu-id="c5b4b-214">Configure Usage Data Collection for &#40;PowerPivot for SharePoint</span></span>](configure-usage-data-collection-for-power-pivot-for-sharepoint.md)  
  
  
