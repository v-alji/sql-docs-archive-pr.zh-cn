---
title: 管理运行中的进程 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- report processing [Reporting Services], status information
- jobs [Reporting Services]
- viewing jobs
- canceling jobs
- user jobs [Reporting Services]
- system jobs [Reporting Services]
- report processing [Reporting Services], managing running processes
- processes [Reporting Services]
- scanning processes [Reporting Services]
- status information [Reporting Services]
- report processing [Reporting Services]
- canceling subscriptions
- report servers [Reporting Services], jobs
- data-driven subscriptions
- displaying jobs
- subscriptions [Reporting Services], running processes
ms.assetid: 473e574e-f1ff-4ef9-bda6-7028b357ac42
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 002dda5a9708b68c6bbf978fb00e85f27b493da2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590552"
---
# <a name="manage-a-running-process"></a><span data-ttu-id="39d72-102">管理运行中的进程</span><span class="sxs-lookup"><span data-stu-id="39d72-102">Manage a Running Process</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="39d72-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 可监视报表服务器上正在运行的作业的状态。</span><span class="sxs-lookup"><span data-stu-id="39d72-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] monitors the status of jobs that are running on the report server.</span></span> <span data-ttu-id="39d72-104">报表服务器会定期扫描正在进行的作业，并将状态信息写入到报表服务器数据库或针对 SharePoint 模式的服务应用程序数据库中。</span><span class="sxs-lookup"><span data-stu-id="39d72-104">At regular intervals, the report server does a scan of in-progress jobs and writes the status information to the report server database or the service application databases for SharePoint mode.</span></span> <span data-ttu-id="39d72-105">如果正在执行以下任意进程，则表明正在处理作业：对远程或本地数据库服务器的查询执行、报表处理以及报表呈现。</span><span class="sxs-lookup"><span data-stu-id="39d72-105">A job is in progress if any of the following processes are underway: query execution on a remote or local database server, report processing, and report rendering.</span></span>  
  
 <span data-ttu-id="39d72-106">您可以同时管理“用户作业  ”和“系统作业  ”。</span><span class="sxs-lookup"><span data-stu-id="39d72-106">You can manage both *user jobs* and *system jobs*.</span></span>  
  
-   <span data-ttu-id="39d72-107">用户作业是由各个用户或订阅启动的。</span><span class="sxs-lookup"><span data-stu-id="39d72-107">User jobs are initiated by an individual user or subscription.</span></span> <span data-ttu-id="39d72-108">这包括按需运行报表，请求报表历史记录快照，手动创建报表快照，以及处理标准订阅等。</span><span class="sxs-lookup"><span data-stu-id="39d72-108">This includes running a report on demand, requesting a report history snapshot, manually creating a report snapshot, and processing a standard subscription.</span></span>  
  
-   <span data-ttu-id="39d72-109">系统作业是由报表服务器启动的。</span><span class="sxs-lookup"><span data-stu-id="39d72-109">System jobs are initiated by the report server.</span></span> <span data-ttu-id="39d72-110">系统作业包括计划的报表执行快照、计划的报表历史记录快照以及数据驱动订阅。</span><span class="sxs-lookup"><span data-stu-id="39d72-110">System jobs include scheduled report execution snapshots, scheduled report history snapshots, and data-driven subscriptions.</span></span>  
  
 <span data-ttu-id="39d72-111">根据报表、查询复杂程度、数据量以及为报表指定的呈现格式，报表处理时间和资源使用情况会有很大的差异。</span><span class="sxs-lookup"><span data-stu-id="39d72-111">Report processing time and resource use varies considerably depending on the report, the query complexity, the amount of data, and the rendering format that is specified for the report.</span></span> <span data-ttu-id="39d72-112">具有对本地数据源的简单查询的报表通常会在数毫秒内完成，因此从不需要进行管理或优化。</span><span class="sxs-lookup"><span data-stu-id="39d72-112">Reports that have simple queries against a local data source will often complete in milliseconds and never require management or tuning.</span></span> <span data-ttu-id="39d72-113">相反，以 PDF 或 Excel 格式呈现的大型报表可能需要很长的处理时间，这取决于硬件资源、传递选项以及是否有其他进程正在并发运行。</span><span class="sxs-lookup"><span data-stu-id="39d72-113">In contrast, a large report that is rendered in PDF or Excel might require significant processing time depending on hardware resources, delivery options, and whether other processes are running concurrently.</span></span> <span data-ttu-id="39d72-114">在报表服务器上，大多数长时间运行的进程都是一些报表呈现操作以及等待查询处理结束的进程。</span><span class="sxs-lookup"><span data-stu-id="39d72-114">On a report server, most long-running processes are report rendering operations and processes that are waiting for query processing to conclude.</span></span> <span data-ttu-id="39d72-115">有时，您可能希望将计算机脱机，或停止需很长时间才能完成的运行中作业，在这种情况下，则需要取消报表进程。</span><span class="sxs-lookup"><span data-stu-id="39d72-115">Occasionally, you might need to cancel a report process if you want to take a computer offline, or stop a running job that is taking too long to complete.</span></span>  
  
 <span data-ttu-id="39d72-116">可以取消以下进程：</span><span class="sxs-lookup"><span data-stu-id="39d72-116">The following processes can be cancelled:</span></span>  
  
-   <span data-ttu-id="39d72-117">按需报表处理。</span><span class="sxs-lookup"><span data-stu-id="39d72-117">On-demand report processing.</span></span>  
  
-   <span data-ttu-id="39d72-118">计划报表处理。</span><span class="sxs-lookup"><span data-stu-id="39d72-118">Scheduled report processing.</span></span>  
  
-   <span data-ttu-id="39d72-119">各用户拥有的标准订阅。</span><span class="sxs-lookup"><span data-stu-id="39d72-119">Standard subscriptions owned by individual users.</span></span>  
  
 <span data-ttu-id="39d72-120">取消作业时，取消的仅仅是运行在报表服务器上的进程。</span><span class="sxs-lookup"><span data-stu-id="39d72-120">Canceling a job only cancels the processes that are running on the report server.</span></span> <span data-ttu-id="39d72-121">由于报表服务器不管理其他计算机上发生的数据处理，因此必须手动取消其他系统上后来孤立的查询进程。</span><span class="sxs-lookup"><span data-stu-id="39d72-121">Because the report server does not manage data processing that occurs on other computers, you must manually cancel query processes that are subsequently orphaned on other systems.</span></span> <span data-ttu-id="39d72-122">可以考虑指定查询超时值以自动关闭执行时间过长的查询。</span><span class="sxs-lookup"><span data-stu-id="39d72-122">Consider specifying query time-out values to automatically shut down queries that are taking too long to execute.</span></span> <span data-ttu-id="39d72-123">有关详细信息，请参阅[为报表和共享数据集处理设置超时值 (SSRS)](../report-server/setting-time-out-values-for-report-and-shared-dataset-processing-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="39d72-123">For more information, see [Setting Time-out Values for Report and Shared Dataset Processing &#40;SSRS&#41;](../report-server/setting-time-out-values-for-report-and-shared-dataset-processing-ssrs.md).</span></span> <span data-ttu-id="39d72-124">有关临时暂停报表的详细信息，请参阅[暂停报表和订阅处理](disable-or-pause-report-and-subscription-processing.md)。</span><span class="sxs-lookup"><span data-stu-id="39d72-124">For more information about temporarily pausing a report, see [Pause Report and Subscription Processing](disable-or-pause-report-and-subscription-processing.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="39d72-125">在极少数情况下，可能需要重新启动服务器才能取消进程。</span><span class="sxs-lookup"><span data-stu-id="39d72-125">In rare circumstances, you may need to restart the server to cancel a process.</span></span> <span data-ttu-id="39d72-126">对于 SharePoint 模式，您可能需要重新启动承载 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服务应用程序的应用程序池。</span><span class="sxs-lookup"><span data-stu-id="39d72-126">For SharePoint mode, you may need to restart the application pool hosting the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application.</span></span> <span data-ttu-id="39d72-127">有关详细信息，请参阅 [启动和停止报表服务器服务](../report-server/start-and-stop-the-report-server-service.md)。</span><span class="sxs-lookup"><span data-stu-id="39d72-127">For more information, see [Start and Stop the Report Server Service](../report-server/start-and-stop-the-report-server-service.md).</span></span>  
  
 <span data-ttu-id="39d72-128">本主题内容：</span><span class="sxs-lookup"><span data-stu-id="39d72-128">In this Topic:</span></span>  
  
-   [<span data-ttu-id="39d72-129">查看和取消作业（本机模式）</span><span class="sxs-lookup"><span data-stu-id="39d72-129">View and Cancel Jobs (Native Mode)</span></span>](#bkmk_native)  
  
-   [<span data-ttu-id="39d72-130">查看和取消作业（SharePoint 模式）</span><span class="sxs-lookup"><span data-stu-id="39d72-130">View and Cancel Jobs (SharePoint Mode)</span></span>](#bkmk_sharepoint)  
  
-   [<span data-ttu-id="39d72-131">以编程方式管理作业</span><span class="sxs-lookup"><span data-stu-id="39d72-131">Managing Jobs Programmatically</span></span>](#bkmk_programmatically)  
  
##  <a name="view-and-cancel-jobs-native-mode"></a><a name="bkmk_native"></a> <span data-ttu-id="39d72-132">查看和取消作业（本机模式）</span><span class="sxs-lookup"><span data-stu-id="39d72-132">View and Cancel Jobs (Native Mode)</span></span>  
 <span data-ttu-id="39d72-133">可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 查看或取消报表服务器上正在运行的作业。</span><span class="sxs-lookup"><span data-stu-id="39d72-133">You can use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] to view or cancel a job that is running on the report server.</span></span> <span data-ttu-id="39d72-134">您必须刷新页面，才能检索当前正在运行的作业的列表或从报表服务器数据库中获取最新的作业状态信息。</span><span class="sxs-lookup"><span data-stu-id="39d72-134">You must refresh the page to retrieve a list of jobs that are currently running or to get up-to-date job status from the report server database.</span></span> <span data-ttu-id="39d72-135">在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中连接到报表服务器之后，您可以打开作业文件夹以查看该报表服务器计算机上当前正在处理的报表的列表。</span><span class="sxs-lookup"><span data-stu-id="39d72-135">When you connect to a report server in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], you can open a Jobs folder to view a list of reports that are currently processing on the report server computer.</span></span> <span data-ttu-id="39d72-136">在“作业属性”页上显示了每个作业的状态信息。</span><span class="sxs-lookup"><span data-stu-id="39d72-136">Status information for each job is displayed in the Job Properties page.</span></span> <span data-ttu-id="39d72-137">打开“取消报表服务器作业”对话框可以查看所有作业的状态信息。</span><span class="sxs-lookup"><span data-stu-id="39d72-137">You can view status information for all jobs by opening the Cancel Report Server Jobs dialog box.</span></span>  
  
 <span data-ttu-id="39d72-138">可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 查看或取消报表服务器上正在运行的作业。</span><span class="sxs-lookup"><span data-stu-id="39d72-138">You can use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] to view or cancel a job that is running on the report server.</span></span> <span data-ttu-id="39d72-139">您必须刷新页面，才能检索当前正在运行的作业的列表或从报表服务器数据库中获取最新的作业状态信息。</span><span class="sxs-lookup"><span data-stu-id="39d72-139">You must refresh the page to retrieve a list of jobs that are currently running or to get up-to-date job status from the report server database.</span></span> <span data-ttu-id="39d72-140">在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中连接到报表服务器之后，您可以打开作业文件夹以查看该报表服务器计算机上当前正在处理的报表的列表。</span><span class="sxs-lookup"><span data-stu-id="39d72-140">When you connect to a report server in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], you can open a Jobs folder to view a list of reports that are currently processing on the report server computer.</span></span> <span data-ttu-id="39d72-141">在“作业属性”页上显示了每个作业的状态信息。</span><span class="sxs-lookup"><span data-stu-id="39d72-141">Status information for each job is displayed in the Job Properties page.</span></span> <span data-ttu-id="39d72-142">打开“取消报表服务器作业”对话框可以查看所有作业的状态信息。</span><span class="sxs-lookup"><span data-stu-id="39d72-142">You can view status information for all jobs by opening the Cancel Report Server Jobs dialog box.</span></span>  
  
 <span data-ttu-id="39d72-143">无法使用 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 列出或取消模型生成、模型处理或数据驱动订阅。</span><span class="sxs-lookup"><span data-stu-id="39d72-143">You cannot use [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] to list or cancel model generation, model processing, or data-driven subscriptions.</span></span> <span data-ttu-id="39d72-144">Reporting Services 没有提供取消模型生成或处理的方法。</span><span class="sxs-lookup"><span data-stu-id="39d72-144">Reporting a Services does not provide a way to cancel model generation or processing.</span></span> <span data-ttu-id="39d72-145">但是，您可以按照本主题中的说明取消数据驱动订阅。</span><span class="sxs-lookup"><span data-stu-id="39d72-145">However, you can cancel data-driven subscriptions using the instructions provided in this topic.</span></span>  
  
### <a name="how-to-cancel-report-processing-or-subscription"></a><span data-ttu-id="39d72-146">如何取消报表处理或订阅</span><span class="sxs-lookup"><span data-stu-id="39d72-146">How to Cancel Report Processing or Subscription</span></span>  
  
1.  <span data-ttu-id="39d72-147">在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中，连接到报表服务器。</span><span class="sxs-lookup"><span data-stu-id="39d72-147">In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], connect to the report server.</span></span> <span data-ttu-id="39d72-148">有关说明，请参阅 [在 Management Studio 中连接到报表服务器](../tools/connect-to-a-report-server-in-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="39d72-148">For instructions, see [Connect to a Report Server in Management Studio](../tools/connect-to-a-report-server-in-management-studio.md).</span></span>  
  
2.  <span data-ttu-id="39d72-149">打开 **“作业”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="39d72-149">Open the **Jobs** folder.</span></span>  
  
3.  <span data-ttu-id="39d72-150">右键单击报表，再单击“取消作业”  。</span><span class="sxs-lookup"><span data-stu-id="39d72-150">Right-click the report and then click **Cancel Jobs**.</span></span>  
  
### <a name="how-to-cancel-a-data-driven-subscription"></a><span data-ttu-id="39d72-151">如何取消数据驱动订阅</span><span class="sxs-lookup"><span data-stu-id="39d72-151">How to Cancel a Data-driven Subscription</span></span>  
  
1.  <span data-ttu-id="39d72-152">在文本编辑器中打开 RSReportServer.config 文件。</span><span class="sxs-lookup"><span data-stu-id="39d72-152">Open the RSReportServer.config file in a text editor.</span></span>  
  
2.  <span data-ttu-id="39d72-153">查找 `IsNotificationService`。</span><span class="sxs-lookup"><span data-stu-id="39d72-153">Find `IsNotificationService`.</span></span>  
  
3.  <span data-ttu-id="39d72-154">将其设置为 `False`。</span><span class="sxs-lookup"><span data-stu-id="39d72-154">Set it to `False`.</span></span>  
  
4.  <span data-ttu-id="39d72-155">保存文件。</span><span class="sxs-lookup"><span data-stu-id="39d72-155">Save the file.</span></span>  
  
5.  <span data-ttu-id="39d72-156">在报表管理器中，从报表的“订阅”选项卡或从“我的订阅”中删除数据驱动订阅  。</span><span class="sxs-lookup"><span data-stu-id="39d72-156">In Report Manager, delete the data-driven subscription from the Subscriptions tab of the report or from **My Subscriptions**.</span></span>  
  
6.  <span data-ttu-id="39d72-157">删除订阅之后，在 RSReportServer.config 文件中查找 `IsNotificationService`，并将其设置为 `True`。</span><span class="sxs-lookup"><span data-stu-id="39d72-157">After you delete the subscription, in the RSReportServer.config file, find `IsNotificationService` and set it to `True`.</span></span>  
  
7.  <span data-ttu-id="39d72-158">保存文件。</span><span class="sxs-lookup"><span data-stu-id="39d72-158">Save the file.</span></span>  
  
### <a name="configuring-frequency-settings-for-retrieving-job-status"></a><span data-ttu-id="39d72-159">配置检索作业状态的频率设置</span><span class="sxs-lookup"><span data-stu-id="39d72-159">Configuring Frequency Settings for Retrieving Job Status</span></span>  
 <span data-ttu-id="39d72-160">正在运行的作业存储在报表服务器的临时数据库中。</span><span class="sxs-lookup"><span data-stu-id="39d72-160">A running job is stored in the report server temporary database.</span></span> <span data-ttu-id="39d72-161">您可以修改 RSReportServer.config 文件中的配置设置，以控制报表服务器扫描正在进行的作业的频率，以及正在运行的作业的状态在多长时间间隔后从“新”更改为“正在运行”。</span><span class="sxs-lookup"><span data-stu-id="39d72-161">You can modify configuration settings in the RSReportServer.config file to control how often the report server scans for in-progress jobs and the interval after which the status of a running job changes from new to running.</span></span> <span data-ttu-id="39d72-162">`RunningRequestsDbCycle` 设置指定报表服务器扫描正在运行的进程的频率。</span><span class="sxs-lookup"><span data-stu-id="39d72-162">The `RunningRequestsDbCycle` setting specifies how often the report server scans for running processes.</span></span> <span data-ttu-id="39d72-163">默认情况下，每隔 60 秒记录一次状态信息。</span><span class="sxs-lookup"><span data-stu-id="39d72-163">By default, status information is recorded every 60 seconds.</span></span> <span data-ttu-id="39d72-164">`RunningRequestsAge` 设置指定作业的状态从“新”更改为“正在运行”的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="39d72-164">The `RunningRequestsAge` setting specifies the interval at which a job is transitioned from new to running.</span></span>  
  
##  <a name="view-and-cancel-jobs-sharepoint-mode"></a><a name="bkmk_sharepoint"></a> <span data-ttu-id="39d72-165">查看和取消作业（SharePoint 模式）</span><span class="sxs-lookup"><span data-stu-id="39d72-165">View and Cancel Jobs (SharePoint Mode)</span></span>  
 <span data-ttu-id="39d72-166">使用 SharePoint 管理中心为每个 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服务应用程序完成 SharePoint 模式部署中作业的管理。</span><span class="sxs-lookup"><span data-stu-id="39d72-166">Management of jobs in a SharePoint mode deployment is completed using SharePoint Central Administration, for each [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application.</span></span>  
  
#### <a name="to-manage-jobs-in-sharepoint-mode"></a><span data-ttu-id="39d72-167">在 SharePoint 模式下管理作业</span><span class="sxs-lookup"><span data-stu-id="39d72-167">To manage jobs in SharePoint mode</span></span>  
  
1.  <span data-ttu-id="39d72-168">在 SharePoint 管理中心中，单击 **“管理服务应用程序”** 。</span><span class="sxs-lookup"><span data-stu-id="39d72-168">In SharePoint Central Administration, click **Manage service applications**.</span></span>  
  
2.  <span data-ttu-id="39d72-169">查找并单击您的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服务应用程序的名称，以打开“管理应用程序”页。</span><span class="sxs-lookup"><span data-stu-id="39d72-169">Find and click the name of your [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application to open the manage application page.</span></span>  
  
3.  <span data-ttu-id="39d72-170">单击 **“管理作业”** 。</span><span class="sxs-lookup"><span data-stu-id="39d72-170">Click **Manage Jobs**</span></span>  
  
4.  <span data-ttu-id="39d72-171">单击 **“作业 ID”** 查看作业的详细信息。</span><span class="sxs-lookup"><span data-stu-id="39d72-171">Click the **Job Id** to see the details of the job.</span></span>  
  
5.  <span data-ttu-id="39d72-172">或单击您的作业的框，然后单击 **“删除”** 以取消作业。</span><span class="sxs-lookup"><span data-stu-id="39d72-172">Or click the box for your job and click **Delete** to cancel the job.</span></span> <span data-ttu-id="39d72-173">删除作业并不会删除订阅。</span><span class="sxs-lookup"><span data-stu-id="39d72-173">Deleting the job does not delete the subscription.</span></span>  
  
##  <a name="managing-jobs-programmatically"></a><a name="bkmk_programmatically"></a> <span data-ttu-id="39d72-174">以编程方式管理作业</span><span class="sxs-lookup"><span data-stu-id="39d72-174">Managing Jobs Programmatically</span></span>  
 <span data-ttu-id="39d72-175">您可以通过编程方式或使用脚本来管理作业。</span><span class="sxs-lookup"><span data-stu-id="39d72-175">You can manage jobs programmatically or by using a script.</span></span> <span data-ttu-id="39d72-176">有关详细信息，请参阅 <xref:ReportService2010.ReportingService2010.ListJobs%2A>、 <xref:ReportService2010.ReportingService2010.CancelJob%2A>。</span><span class="sxs-lookup"><span data-stu-id="39d72-176">For more information, see <xref:ReportService2010.ReportingService2010.ListJobs%2A>, <xref:ReportService2010.ReportingService2010.CancelJob%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39d72-177">另请参阅</span><span class="sxs-lookup"><span data-stu-id="39d72-177">See Also</span></span>  
 <span data-ttu-id="39d72-178">[取消报表服务器作业 (Management Studio)](../tools/cancel-report-server-jobs-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="39d72-178">[Cancel Report Server Jobs &#40;Management Studio&#41;](../tools/cancel-report-server-jobs-management-studio.md) </span></span>  
 <span data-ttu-id="39d72-179">[作业属性 (Management Studio)](../tools/job-properties-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="39d72-179">[Job Properties &#40;Management Studio&#41;](../tools/job-properties-management-studio.md) </span></span>  
 <span data-ttu-id="39d72-180">[修改 Reporting Services 配置文件 (RSreportserver.config)](../report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md) </span><span class="sxs-lookup"><span data-stu-id="39d72-180">[Modify a Reporting Services Configuration File &#40;RSreportserver.config&#41;](../report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md) </span></span>  
 <span data-ttu-id="39d72-181">[Rsreportserver.config 配置文件](../report-server/rsreportserver-config-configuration-file.md) </span><span class="sxs-lookup"><span data-stu-id="39d72-181">[RSReportServer Configuration File](../report-server/rsreportserver-config-configuration-file.md) </span></span>  
 <span data-ttu-id="39d72-182">[报表管理器（SSRS 本机模式）](../report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="39d72-182">[Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md) </span></span>  
 [<span data-ttu-id="39d72-183">监视报表服务器性能</span><span class="sxs-lookup"><span data-stu-id="39d72-183">Monitoring Report Server Performance</span></span>](../report-server/monitoring-report-server-performance.md)  
  
  
