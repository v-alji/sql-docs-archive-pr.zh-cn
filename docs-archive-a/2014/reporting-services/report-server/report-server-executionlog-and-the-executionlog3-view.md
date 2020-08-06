---
title: 报表服务器执行日志和 ExecutionLog3 视图 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- logs [Reporting Services], execution
- execution logs [Reporting Services]
ms.assetid: a7ead67d-1404-4e67-97e7-4c7b0d942070
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 868f8497e61c17662cb621850cdb8aee74c82706
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579496"
---
# <a name="report-server-execution-log-and-the-executionlog3-view"></a><span data-ttu-id="65a70-102">报告服务器执行日志和 ExecutionLog3 视图</span><span class="sxs-lookup"><span data-stu-id="65a70-102">Report Server Execution Log and the ExecutionLog3 View</span></span>
  <span data-ttu-id="65a70-103">报表服务器执行日志包含有关在一个或多个服务器上在本机模式扩展部署或 SharePoint 场中执行的报表的信息。</span><span class="sxs-lookup"><span data-stu-id="65a70-103">The report server execution log contains information about the reports that execute on the server or on multiple servers in a native mode scale-out deployment or a SharePoint farm.</span></span> <span data-ttu-id="65a70-104">您可以使用报表执行日志来查明报表的请求频率、最常用的输出格式以及每个处理阶段所用的处理时间（毫秒）。</span><span class="sxs-lookup"><span data-stu-id="65a70-104">You can use the report execution log to find out how often a report is requested, what output formats are used the most, and how many milliseconds of processing time is spent on each processing phase.</span></span> <span data-ttu-id="65a70-105">该日志包含与执行报表的数据集查询所用的时间长度和处理数据所用的时间长度有关的信息。</span><span class="sxs-lookup"><span data-stu-id="65a70-105">The log contains information on the length of time spent executing a report's dataset query and the time spent processing the data.</span></span> <span data-ttu-id="65a70-106">如果您是报表服务器管理员，则可以查看日志信息并标识长时间运行的任务，并且向报表作者就其可以改进的报表方面（数据集或处理）提出建议。</span><span class="sxs-lookup"><span data-stu-id="65a70-106">If you are a report server administrator, you can review the log information and identify long running tasks and make suggestions to the report authors on the areas of the report (dataset or processing) they may be able to improve.</span></span>  
  
 <span data-ttu-id="65a70-107">配置为 SharePoint 模式的报表服务器也可以利用 SharePoint ULS 日志。</span><span class="sxs-lookup"><span data-stu-id="65a70-107">Report servers configured for SharePoint mode, can also utilize the SharePoint ULS logs.</span></span> <span data-ttu-id="65a70-108">有关详细信息，请参阅 [为 SharePoint 跟踪日志 (ULS) 启用 Reporting Services 事件](turn-on-reporting-services-events-for-the-sharepoint-trace-log-uls.md)</span><span class="sxs-lookup"><span data-stu-id="65a70-108">For more information, see [Turn on Reporting Services events for the SharePoint trace log &#40;ULS&#41;](turn-on-reporting-services-events-for-the-sharepoint-trace-log-uls.md)</span></span>  
  
##  <a name="viewing-log-information"></a><a name="bkmk_top"></a> <span data-ttu-id="65a70-109">查看日志信息</span><span class="sxs-lookup"><span data-stu-id="65a70-109">Viewing Log Information</span></span>  
 <span data-ttu-id="65a70-110">报表服务器执行日志将报表执行情况的有关数据记录在内部数据库表中。</span><span class="sxs-lookup"><span data-stu-id="65a70-110">The report server execution logs data about report execution into an internal database table.</span></span> <span data-ttu-id="65a70-111">表中的信息可从 SQL Server 视图获得。</span><span class="sxs-lookup"><span data-stu-id="65a70-111">The information from the table is available from SQL Server views.</span></span>  
  
 <span data-ttu-id="65a70-112">报表执行日志存储于默认名为 **ReportServer**的报表服务器数据库中。</span><span class="sxs-lookup"><span data-stu-id="65a70-112">The report execution log is stored in the report server database that by default is named **ReportServer**.</span></span> <span data-ttu-id="65a70-113">SQL 视图提供执行日志信息。</span><span class="sxs-lookup"><span data-stu-id="65a70-113">The SQL views provide the execution log information.</span></span> <span data-ttu-id="65a70-114">“2”和“3”视图已在最近的版本中添加，并且包含新字段或者所包含字段的名称比以前版本更友好。</span><span class="sxs-lookup"><span data-stu-id="65a70-114">The "2" and "3" views were added in more recent releases and contain new fields or they contain fields with friendlier names than the previous releases.</span></span> <span data-ttu-id="65a70-115">较旧的视图仍保留在产品中，这样，依赖于它们的自定义应用程序将不会受到影响。</span><span class="sxs-lookup"><span data-stu-id="65a70-115">The older views remain in the product so custom applications that depend on them are not impacted.</span></span> <span data-ttu-id="65a70-116">如果您不依赖于较旧的视图，例如 ExecutionLog，则建议您使用最新视图 ExecutionLog**3**。</span><span class="sxs-lookup"><span data-stu-id="65a70-116">If you do not have a dependence on an older view, for example ExecutionLog, it is recommended you use the most recent view, ExecutionLog**3**.</span></span>  
  
 <span data-ttu-id="65a70-117">本主题内容：</span><span class="sxs-lookup"><span data-stu-id="65a70-117">In this topic:</span></span>  
  
-   [<span data-ttu-id="65a70-118">针对 SharePoint 模式报表服务器的配置设置</span><span class="sxs-lookup"><span data-stu-id="65a70-118">Configuration Settings for a SharePoint mode Report Server</span></span>](#bkmk_sharepoint)  
  
-   [<span data-ttu-id="65a70-119">针对本机模式报表服务器的配置设置</span><span class="sxs-lookup"><span data-stu-id="65a70-119">Configuration Settings for a Native Mode Report Server</span></span>](#bkmk_native)  
  
-   [<span data-ttu-id="65a70-120">日志字段 (ExecutionLog3)</span><span class="sxs-lookup"><span data-stu-id="65a70-120">Log Fields (ExecutionLog3)</span></span>](#bkmk_executionlog3)  
  
-   [<span data-ttu-id="65a70-121">AdditionalInfo 字段</span><span class="sxs-lookup"><span data-stu-id="65a70-121">The AdditionalInfo Field</span></span>](#bkmk_additionalinfo)  
  
-   [<span data-ttu-id="65a70-122">日志字段 (ExecutionLog2)</span><span class="sxs-lookup"><span data-stu-id="65a70-122">Log Fields (ExecutionLog2)</span></span>](#bkmk_executionlog2)  
  
-   [<span data-ttu-id="65a70-123">日志字段 (ExecutionLog)</span><span class="sxs-lookup"><span data-stu-id="65a70-123">Log Fields (ExecutionLog)</span></span>](#bkmk_executionlog)  
  
##  <a name="configuration-settings-for-a-sharepoint-mode-report-server"></a><a name="bkmk_sharepoint"></a> <span data-ttu-id="65a70-124">针对 SharePoint 模式报表服务器的配置设置</span><span class="sxs-lookup"><span data-stu-id="65a70-124">Configuration Settings for a SharePoint mode Report Server</span></span>  
 <span data-ttu-id="65a70-125">您可以从 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服务应用程序的系统设置启用或禁用报表执行日志记录。</span><span class="sxs-lookup"><span data-stu-id="65a70-125">You can turn report execution logging on or off from the system settings of a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application.</span></span>  
  
 <span data-ttu-id="65a70-126">默认情况下，日志条目保留 60 天。</span><span class="sxs-lookup"><span data-stu-id="65a70-126">By default, log entries are kept 60 days.</span></span> <span data-ttu-id="65a70-127">超过此日期的条目将于每日凌晨 2:00 删</span><span class="sxs-lookup"><span data-stu-id="65a70-127">Entries that exceed this date are removed at 2:00 A.M.</span></span> <span data-ttu-id="65a70-128">除。</span><span class="sxs-lookup"><span data-stu-id="65a70-128">every day.</span></span> <span data-ttu-id="65a70-129">对于成熟的安装，在任何给定时间都只保留 60 天的信息。</span><span class="sxs-lookup"><span data-stu-id="65a70-129">On a mature installation, only 60 days of information will be available at any given time.</span></span>  
  
 <span data-ttu-id="65a70-130">不能针对行数或所记录的条目类型设置限制。</span><span class="sxs-lookup"><span data-stu-id="65a70-130">You cannot set limits on the number of rows or on the type of entries that are logged.</span></span>  
  
 <span data-ttu-id="65a70-131">**启用执行日志记录：**</span><span class="sxs-lookup"><span data-stu-id="65a70-131">**To enable execution logging:**</span></span>  
  
1.  <span data-ttu-id="65a70-132">在 SharePoint 管理中心内，在 **“应用程序管理”** 组中单击 **“管理服务应用程序”** 。</span><span class="sxs-lookup"><span data-stu-id="65a70-132">From SharePoint Central Administration, click **Manage service applications** in the **Application Management** group.</span></span>  
  
2.  <span data-ttu-id="65a70-133">单击要配置的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服务应用程序的名称。</span><span class="sxs-lookup"><span data-stu-id="65a70-133">Click the name of the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application you want to configure.</span></span>  
  
3.  <span data-ttu-id="65a70-134">单击 **“系统设置”** 。</span><span class="sxs-lookup"><span data-stu-id="65a70-134">Click **System Settings**.</span></span>  
  
4.  <span data-ttu-id="65a70-135">在 **“日志记录”** 部分中选择 **“启用执行日志记录”** 。</span><span class="sxs-lookup"><span data-stu-id="65a70-135">Select **Enable Execution Logging** in the **Logging** section.</span></span>  
  
5.  <span data-ttu-id="65a70-136">单击“确定”。 </span><span class="sxs-lookup"><span data-stu-id="65a70-136">Click **OK**.</span></span>  
  
 <span data-ttu-id="65a70-137">**启用详细日志记录：**</span><span class="sxs-lookup"><span data-stu-id="65a70-137">**To enable verbose logging:**</span></span>  
  
 <span data-ttu-id="65a70-138">您需要如前面的步骤中所述启用日志记录，然后完成以下内容：</span><span class="sxs-lookup"><span data-stu-id="65a70-138">You need to enable logging as described in the previous steps and then complete the following:</span></span>  
  
1.  <span data-ttu-id="65a70-139">从 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服务应用程序的“系统设置”页，找到“用户定义”部分。</span><span class="sxs-lookup"><span data-stu-id="65a70-139">From the **System Settings** page of your [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] services application, find the **User-defined** section.</span></span>  
  
2.  <span data-ttu-id="65a70-140">将 **ExecutionLogLevel** 更改为 **verbose**。</span><span class="sxs-lookup"><span data-stu-id="65a70-140">Change the **ExecutionLogLevel** to **verbose**.</span></span> <span data-ttu-id="65a70-141">该字段是文本输入字段，其两个可能的值是 **verbose** 和 **normal**。</span><span class="sxs-lookup"><span data-stu-id="65a70-141">This field is a text entry field and the two possible values are **verbose** and **normal**.</span></span>  
  
##  <a name="configuration-settings-for-a-native-mode-report-server"></a><a name="bkmk_native"></a> <span data-ttu-id="65a70-142">针对本机模式报表服务器的配置设置</span><span class="sxs-lookup"><span data-stu-id="65a70-142">Configuration Settings for a Native Mode Report Server</span></span>  
 <span data-ttu-id="65a70-143">从 SQL Server Management Studio 的“服务器属性”页，您可以启用或禁用报表执行日志记录。</span><span class="sxs-lookup"><span data-stu-id="65a70-143">You can turn report execution logging on or off from the Server Properties page in SQL Server Management Studio.</span></span> <span data-ttu-id="65a70-144">**EnableExecutionLogging** 是高级属性。</span><span class="sxs-lookup"><span data-stu-id="65a70-144">The **EnableExecutionLogging** is and Advanced property.</span></span>  
  
 <span data-ttu-id="65a70-145">默认情况下，日志条目保留 60 天。</span><span class="sxs-lookup"><span data-stu-id="65a70-145">By default, log entries are kept 60 days.</span></span> <span data-ttu-id="65a70-146">超过此日期的条目将于每日凌晨 2:00 删</span><span class="sxs-lookup"><span data-stu-id="65a70-146">Entries that exceed this date are removed at 2:00 A.M.</span></span> <span data-ttu-id="65a70-147">除。</span><span class="sxs-lookup"><span data-stu-id="65a70-147">every day.</span></span> <span data-ttu-id="65a70-148">对于成熟的安装，在任何给定时间都只保留 60 天的信息。</span><span class="sxs-lookup"><span data-stu-id="65a70-148">On a mature installation, only 60 days of information will be available at any given time.</span></span>  
  
 <span data-ttu-id="65a70-149">不能针对行数或所记录的条目类型设置限制。</span><span class="sxs-lookup"><span data-stu-id="65a70-149">You cannot set limits on the number of rows or on the type of entries that are logged.</span></span>  
  
 <span data-ttu-id="65a70-150">**启用执行日志记录：**</span><span class="sxs-lookup"><span data-stu-id="65a70-150">**To enable execution logging:**</span></span>  
  
1.  <span data-ttu-id="65a70-151">使用管理权限启动 SQL Server Management Studio。</span><span class="sxs-lookup"><span data-stu-id="65a70-151">Start SQL Server Management Studio with administrative privileges.</span></span> <span data-ttu-id="65a70-152">例如，用鼠标右键单击 Management Studio 图标，然后单击“以管理员身份运行”。</span><span class="sxs-lookup"><span data-stu-id="65a70-152">For example right-click the Management Studio icon and click 'Run as administrator'.</span></span>  
  
2.  <span data-ttu-id="65a70-153">连接到所需报表服务器。</span><span class="sxs-lookup"><span data-stu-id="65a70-153">Connect to the desired report server.</span></span>  
  
3.  <span data-ttu-id="65a70-154">右键单击服务器名称并单击“属性”  。</span><span class="sxs-lookup"><span data-stu-id="65a70-154">Right-click the server name and click **Properties**.</span></span> <span data-ttu-id="65a70-155">如果“属性”选项被禁用，请确认您是在使用管理权限运行 SQL Server Management Studio。</span><span class="sxs-lookup"><span data-stu-id="65a70-155">If the Properties option is disabled, verify you ran SQL Server Management Studio with administrative privileges.</span></span>  
  
4.  <span data-ttu-id="65a70-156">单击 **“日志记录”** 页。</span><span class="sxs-lookup"><span data-stu-id="65a70-156">Click the **Logging** page.</span></span>  
  
5.  <span data-ttu-id="65a70-157">选择“启用报表执行日志记录”  。</span><span class="sxs-lookup"><span data-stu-id="65a70-157">Select **Enable report execution Logging**.</span></span>  
  
 <span data-ttu-id="65a70-158">**启用详细日志记录：**</span><span class="sxs-lookup"><span data-stu-id="65a70-158">**To enable verbose logging:**</span></span>  
  
 <span data-ttu-id="65a70-159">您需要如前面的步骤中所述启用日志记录，然后完成以下内容：</span><span class="sxs-lookup"><span data-stu-id="65a70-159">You need to enable logging as described in the previous steps and then complete the following:</span></span>  
  
1.  <span data-ttu-id="65a70-160">在 **“服务器属性”** 对话框中，单击 **“高级”** 页。</span><span class="sxs-lookup"><span data-stu-id="65a70-160">From the **Server Properties** dialog, click the **Advanced** page.</span></span>  
  
2.  <span data-ttu-id="65a70-161">在“用户定义”部分中，将 ExecutionLogLevel 更改为 verbose    。</span><span class="sxs-lookup"><span data-stu-id="65a70-161">In the **User-defined** section, change the **ExecutionLogLevel** to **verbose**.</span></span> <span data-ttu-id="65a70-162">该字段是文本输入字段，其两个可能的值是 **verbose** 和 **normal**。</span><span class="sxs-lookup"><span data-stu-id="65a70-162">This field is a text entry field and the two possible values are **verbose** and **normal**.</span></span>  
  
##  <a name="log-fields-executionlog3"></a><a name="bkmk_executionlog3"></a> <span data-ttu-id="65a70-163">日志字段 (ExecutionLog3)</span><span class="sxs-lookup"><span data-stu-id="65a70-163">Log Fields (ExecutionLog3)</span></span>  
 <span data-ttu-id="65a70-164">此视图在基于 XML 的 **AdditionalInfo** 列中添加了其他性能诊断节点。</span><span class="sxs-lookup"><span data-stu-id="65a70-164">This view added additional performance diagnostics node inside the XML based **AdditionalInfo** column.</span></span> <span data-ttu-id="65a70-165">AdditionalInfo 列包含 1 对多的其他字段的 XML 结构信息。</span><span class="sxs-lookup"><span data-stu-id="65a70-165">The AdditionalInfo column contains an XML structure of 1 to many additional fields of information.</span></span> <span data-ttu-id="65a70-166">下面是一个示例 Transact SQL 语句，从视图 ExecutionLog3 检索行。</span><span class="sxs-lookup"><span data-stu-id="65a70-166">The following is a sample Transact SQL statement to retrieve rows from the view ExecutionLog3.</span></span> <span data-ttu-id="65a70-167">该示例假定报表服务器数据库名为 **ReportServer**：</span><span class="sxs-lookup"><span data-stu-id="65a70-167">The sample assumes the report server database is named **ReportServer**:</span></span>  
  
```  
Use ReportServer  
select * from ExecutionLog3 order by TimeStart DESC  
```  
  
 <span data-ttu-id="65a70-168">下表描述在报表执行日志中捕获的数据</span><span class="sxs-lookup"><span data-stu-id="65a70-168">The following table describes the data that is captured in the report execution log</span></span>  
  
|<span data-ttu-id="65a70-169">列</span><span class="sxs-lookup"><span data-stu-id="65a70-169">Column</span></span>|<span data-ttu-id="65a70-170">说明</span><span class="sxs-lookup"><span data-stu-id="65a70-170">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="65a70-171">InstanceName</span><span class="sxs-lookup"><span data-stu-id="65a70-171">InstanceName</span></span>|<span data-ttu-id="65a70-172">处理请求的报表服务器实例的名称。</span><span class="sxs-lookup"><span data-stu-id="65a70-172">Name of the report server instance that handled the request.</span></span> <span data-ttu-id="65a70-173">如果您的环境具有多个报表服务器，则可以对 InstanceName 分布进行分析，以便监视并确定您的网络负载平衡器是否按预期跨多个报表服务器分布请求。</span><span class="sxs-lookup"><span data-stu-id="65a70-173">If your environment has more than one report server, you can analyze the InstanceName distribution to monitor and determine if your network-load balancer distributes requests across report servers as expected.</span></span>|  
|<span data-ttu-id="65a70-174">ItemPath</span><span class="sxs-lookup"><span data-stu-id="65a70-174">ItemPath</span></span>|<span data-ttu-id="65a70-175">存储报表或报表项的位置的路径。</span><span class="sxs-lookup"><span data-stu-id="65a70-175">Path of where a report or report item is stored.</span></span>|  
|<span data-ttu-id="65a70-176">UserName</span><span class="sxs-lookup"><span data-stu-id="65a70-176">UserName</span></span>|<span data-ttu-id="65a70-177">用户标识符。</span><span class="sxs-lookup"><span data-stu-id="65a70-177">User identifier.</span></span>|  
|<span data-ttu-id="65a70-178">ExecutionID</span><span class="sxs-lookup"><span data-stu-id="65a70-178">ExecutionID</span></span>|<span data-ttu-id="65a70-179">与请求关联的内部标识符。</span><span class="sxs-lookup"><span data-stu-id="65a70-179">The internal identifier associated with a request.</span></span> <span data-ttu-id="65a70-180">同一用户会话的请求共享相同的执行 ID。</span><span class="sxs-lookup"><span data-stu-id="65a70-180">Requests on the same user sessions share the same execution id.</span></span>|  
|<span data-ttu-id="65a70-181">RequestType</span><span class="sxs-lookup"><span data-stu-id="65a70-181">RequestType</span></span>|<span data-ttu-id="65a70-182">可能的值：</span><span class="sxs-lookup"><span data-stu-id="65a70-182">Possible Values:</span></span><br /><span data-ttu-id="65a70-183">**交互式**</span><span class="sxs-lookup"><span data-stu-id="65a70-183">**Interactive**</span></span><br /><span data-ttu-id="65a70-184">**订阅**</span><span class="sxs-lookup"><span data-stu-id="65a70-184">**Subscription**</span></span><br /><br /> <br /><br /> <span data-ttu-id="65a70-185">分析按 RequestType=Subscription 筛选的日志数据和按 TimeStart 排序的数据可揭示大量使用订阅的时间段，这样您可能要将某些报表订阅修改为其他时间。</span><span class="sxs-lookup"><span data-stu-id="65a70-185">Analyzing log data filtered by RequestType=Subscription and sorted by TimeStart may reveal periods of heavy subscription usage and you may want to modify some of the report subscriptions to a different time.</span></span>|  
|<span data-ttu-id="65a70-186">格式</span><span class="sxs-lookup"><span data-stu-id="65a70-186">Format</span></span>|<span data-ttu-id="65a70-187">呈现格式。</span><span class="sxs-lookup"><span data-stu-id="65a70-187">Rendering format.</span></span>|  
|<span data-ttu-id="65a70-188">parameters</span><span class="sxs-lookup"><span data-stu-id="65a70-188">Parameters</span></span>|<span data-ttu-id="65a70-189">用于执行报表的参数值。</span><span class="sxs-lookup"><span data-stu-id="65a70-189">Parameter values used for a report execution.</span></span>|  
|<span data-ttu-id="65a70-190">ItemAction</span><span class="sxs-lookup"><span data-stu-id="65a70-190">ItemAction</span></span>|<span data-ttu-id="65a70-191">可能的值：</span><span class="sxs-lookup"><span data-stu-id="65a70-191">Possible values:</span></span><br /><br /> <span data-ttu-id="65a70-192">**呈现**</span><span class="sxs-lookup"><span data-stu-id="65a70-192">**Render**</span></span><br /><br /> <span data-ttu-id="65a70-193">**Sort**</span><span class="sxs-lookup"><span data-stu-id="65a70-193">**Sort**</span></span><br /><br /> <span data-ttu-id="65a70-194">**BookMarkNavigation**</span><span class="sxs-lookup"><span data-stu-id="65a70-194">**BookMarkNavigation**</span></span><br /><br /> <span data-ttu-id="65a70-195">**DocumentNavigation**</span><span class="sxs-lookup"><span data-stu-id="65a70-195">**DocumentNavigation**</span></span><br /><br /> <span data-ttu-id="65a70-196">**GetDocumentMap**</span><span class="sxs-lookup"><span data-stu-id="65a70-196">**GetDocumentMap**</span></span><br /><br /> <span data-ttu-id="65a70-197">**Findstring**</span><span class="sxs-lookup"><span data-stu-id="65a70-197">**Findstring**</span></span><br /><br /> <span data-ttu-id="65a70-198">**执行**</span><span class="sxs-lookup"><span data-stu-id="65a70-198">**Execute**</span></span><br /><br /> <span data-ttu-id="65a70-199">**RenderEdit**</span><span class="sxs-lookup"><span data-stu-id="65a70-199">**RenderEdit**</span></span>|  
|<span data-ttu-id="65a70-200">TimeStart</span><span class="sxs-lookup"><span data-stu-id="65a70-200">TimeStart</span></span>|<span data-ttu-id="65a70-201">指示报表进程的持续时段的开始时间和结束时间。</span><span class="sxs-lookup"><span data-stu-id="65a70-201">Start and stop times that indicate the duration of a report process.</span></span>|  
|<span data-ttu-id="65a70-202">TimeEnd</span><span class="sxs-lookup"><span data-stu-id="65a70-202">TimeEnd</span></span>||  
|<span data-ttu-id="65a70-203">TimeDataRetrieval</span><span class="sxs-lookup"><span data-stu-id="65a70-203">TimeDataRetrieval</span></span>|<span data-ttu-id="65a70-204">用于检索数据的毫秒数。</span><span class="sxs-lookup"><span data-stu-id="65a70-204">Number of milliseconds spent retrieving the data.</span></span>|  
|<span data-ttu-id="65a70-205">TimeProcessing</span><span class="sxs-lookup"><span data-stu-id="65a70-205">TimeProcessing</span></span>|<span data-ttu-id="65a70-206">用于处理报表的毫秒数。</span><span class="sxs-lookup"><span data-stu-id="65a70-206">Number of milliseconds spent processing the report.</span></span>|  
|<span data-ttu-id="65a70-207">TimeRendering</span><span class="sxs-lookup"><span data-stu-id="65a70-207">TimeRendering</span></span>|<span data-ttu-id="65a70-208">用于呈现报表的毫秒数。</span><span class="sxs-lookup"><span data-stu-id="65a70-208">Number of milliseconds spent rendering the report.</span></span>|  
|<span data-ttu-id="65a70-209">源</span><span class="sxs-lookup"><span data-stu-id="65a70-209">Source</span></span>|<span data-ttu-id="65a70-210">报表执行的源。</span><span class="sxs-lookup"><span data-stu-id="65a70-210">Source of the report execution.</span></span> <span data-ttu-id="65a70-211">可能的值：</span><span class="sxs-lookup"><span data-stu-id="65a70-211">Possible values:</span></span><br /><br /> <span data-ttu-id="65a70-212">**直播**</span><span class="sxs-lookup"><span data-stu-id="65a70-212">**Live**</span></span><br /><br /> <span data-ttu-id="65a70-213">**Cache**：指示缓存的执行，例如，数据集查询不实时执行。</span><span class="sxs-lookup"><span data-stu-id="65a70-213">**Cache**: Indicates a cached execution, for example, dataset queries are not executed live.</span></span><br /><br /> <span data-ttu-id="65a70-214">**快照**</span><span class="sxs-lookup"><span data-stu-id="65a70-214">**Snapshot**</span></span><br /><br /> <span data-ttu-id="65a70-215">**History**</span><span class="sxs-lookup"><span data-stu-id="65a70-215">**History**</span></span><br /><br /> <span data-ttu-id="65a70-216">**即席**：指示基于动态生成的报表模型的钻取报表，或使用 Report Server 进行处理和呈现的客户端上预览的报表生成器报表。</span><span class="sxs-lookup"><span data-stu-id="65a70-216">**AdHoc** : Indicates either a dynamically generated report model based drill through report, or a Report Builder report that is previewed on a client utilizing the report server for processing and rendering.</span></span><br /><br /> <span data-ttu-id="65a70-217">**Session**：指示已建立的会话内的跟进请求。</span><span class="sxs-lookup"><span data-stu-id="65a70-217">**Session**: Indicates a follow up request within an already established session.</span></span>  <span data-ttu-id="65a70-218">例如，初始请求为查看第一页，跟进请求为使用当前会话状态导出到 Excel。</span><span class="sxs-lookup"><span data-stu-id="65a70-218">For example the initial request is to view page 1, and the follow up request is to export to Excel with the current session state.</span></span><br /><br /> <span data-ttu-id="65a70-219">**Rdce**：指示报表定义自定义扩展插件。</span><span class="sxs-lookup"><span data-stu-id="65a70-219">**Rdce**:  Indicates a Report Definition Customization Extension.</span></span> <span data-ttu-id="65a70-220">在执行报表时，RDCE 自定义扩展插件可以在将某一报表定义传递到处理引擎前动态自定义该报表定义。</span><span class="sxs-lookup"><span data-stu-id="65a70-220">An RDCE custom extension can dynamically customize a report definition before it is passed to the processing engine upon report execution.</span></span>|  
|<span data-ttu-id="65a70-221">状态</span><span class="sxs-lookup"><span data-stu-id="65a70-221">Status</span></span>|<span data-ttu-id="65a70-222">状态（rsSuccess 或错误代码；如果发生多个错误，则只记录第一个）。</span><span class="sxs-lookup"><span data-stu-id="65a70-222">Status (either rsSuccess or an error code; if multiple errors occur, only the first error is recorded).</span></span>|  
|<span data-ttu-id="65a70-223">ByteCount</span><span class="sxs-lookup"><span data-stu-id="65a70-223">ByteCount</span></span>|<span data-ttu-id="65a70-224">所呈现的报表的大小（字节）。</span><span class="sxs-lookup"><span data-stu-id="65a70-224">Size of rendered reports in bytes.</span></span>|  
|<span data-ttu-id="65a70-225">RowCount</span><span class="sxs-lookup"><span data-stu-id="65a70-225">RowCount</span></span>|<span data-ttu-id="65a70-226">查询返回的结果行数。</span><span class="sxs-lookup"><span data-stu-id="65a70-226">Number of rows returned from queries.</span></span>|  
|<span data-ttu-id="65a70-227">AdditionalInfo</span><span class="sxs-lookup"><span data-stu-id="65a70-227">AdditionalInfo</span></span>|<span data-ttu-id="65a70-228">包含与执行有关的附加信息的 XML 属性包。</span><span class="sxs-lookup"><span data-stu-id="65a70-228">An XML property bag containing additional information about the execution.</span></span> <span data-ttu-id="65a70-229">对于每一行，内容可以不同。</span><span class="sxs-lookup"><span data-stu-id="65a70-229">The contents can be different for each row.</span></span>|  
  
##  <a name="the-additionalinfo-field"></a><a name="bkmk_additionalinfo"></a> <span data-ttu-id="65a70-230">AdditionalInfo 字段</span><span class="sxs-lookup"><span data-stu-id="65a70-230">The AdditionalInfo Field</span></span>  
 <span data-ttu-id="65a70-231">AdditionalInfo 字段是包含与执行有关的其他信息的 XML 属性包或结构。</span><span class="sxs-lookup"><span data-stu-id="65a70-231">The AdditionalInfo field is an XML property bag or structure containing additional information about the execution.</span></span> <span data-ttu-id="65a70-232">对于日志中的每一行，内容可以不同。</span><span class="sxs-lookup"><span data-stu-id="65a70-232">The contents can be different for each row in the log.</span></span>  
  
 <span data-ttu-id="65a70-233">下表显示标准日志记录和详细日志记录模式下 AddtionalInfo 字段的内容示例：</span><span class="sxs-lookup"><span data-stu-id="65a70-233">The following tables are examples  of the contents of the AddtionalInfo field for both standard and verbose logging:</span></span>  
  
 <span data-ttu-id="65a70-234">**AddtionalInfo 的标准日志记录示例**</span><span class="sxs-lookup"><span data-stu-id="65a70-234">**Standard logging example of AddtionalInfo**</span></span>  
  
```  
<AdditionalInfo>  
  <ProcessingEngine>2</ProcessingEngine>  
  <ScalabilityTime>  
    <Pagination>0</Pagination>  
    <Processing>0</Processing>  
  </ScalabilityTime>  
  <EstimatedMemoryUsageKB>  
    <Pagination>0</Pagination>  
    <Processing>6</Processing>  
  </EstimatedMemoryUsageKB>  
  <DataExtension>  
    <SQL>1</SQL>  
  </DataExtension>  
  <Connections>  
    <Connection>  
      <ConnectionOpenTime>147</ConnectionOpenTime>  
      <DataSets>  
        <DataSet>  
          <Name>DataSet1</Name>  
          <RowsRead>16</RowsRead>  
          <TotalTimeDataRetrieval>642</TotalTimeDataRetrieval>  
          <ExecuteReaderTime>63</ExecuteReaderTime>  
        </DataSet>  
        <DataSet>  
          <Name>DataSet2</Name>  
          <RowsRead>3</RowsRead>  
          <TotalTimeDataRetrieval>157</TotalTimeDataRetrieval>  
          <ExecuteReaderTime>60</ExecuteReaderTime>  
        </DataSet>  
      </DataSets>  
    </Connection>  
  </Connections>  
</AdditionalInfo>  
  
```  
  
 <span data-ttu-id="65a70-235">**AdditionalInfo 的详细日志记录示例**</span><span class="sxs-lookup"><span data-stu-id="65a70-235">**Verbose logging example of AdditionalInfo**</span></span>  
  
```  
<AdditionalInfo>  
  <ProcessingEngine>2</ProcessingEngine>  
  <ScalabilityTime>  
    <Pagination>0</Pagination>  
    <Processing>0</Processing>  
  </ScalabilityTime>  
  <EstimatedMemoryUsageKB>  
    <Pagination>0</Pagination>  
    <Processing>6</Processing>  
  </EstimatedMemoryUsageKB>  
  <DataExtension>  
    <SQL>1</SQL>  
  </DataExtension>  
  <Connections>  
    <Connection>  
      <ConnectionOpenTime>127</ConnectionOpenTime>  
      <DataSource>  
        <Name>DataSource1</Name>  
        <DataExtension>SQL</DataExtension>  
      </DataSource>  
      <DataSets>  
        <DataSet>  
          <Name>DataSet1</Name>  
          <RowsRead>16</RowsRead>  
          <TotalTimeDataRetrieval>655</TotalTimeDataRetrieval>  
          <QueryPrepareAndExecutionTime>94</QueryPrepareAndExecutionTime>  
          <ExecuteReaderTime>33</ExecuteReaderTime>  
          <DataReaderMappingTime>30</DataReaderMappingTime>  
          <DisposeDataReaderTime>1</DisposeDataReaderTime>  
        </DataSet>  
        <DataSet>  
          <Name>DataSet2</Name>  
          <RowsRead>3</RowsRead>  
          <TotalTimeDataRetrieval>16</TotalTimeDataRetrieval>  
          <QueryPrepareAndExecutionTime>2</QueryPrepareAndExecutionTime>  
          <ExecuteReaderTime>1</ExecuteReaderTime>  
          <DataReaderMappingTime>0</DataReaderMappingTime>  
          <DisposeDataReaderTime>0</DisposeDataReaderTime>  
        </DataSet>  
      </DataSets>  
    </Connection>  
  </Connections>  
</AdditionalInfo>  
  
```  
  
 <span data-ttu-id="65a70-236">下面介绍你将在 AdditionalInfo 字段中看到的一些属性：</span><span class="sxs-lookup"><span data-stu-id="65a70-236">The following describes some of the properties you will see in the AdditionalInfo field:</span></span>  
  
-   <span data-ttu-id="65a70-237">**ProcessingEngine**： 1 = SQL Server 2005，2 = 新的按需处理引擎。</span><span class="sxs-lookup"><span data-stu-id="65a70-237">**ProcessingEngine**: 1=SQL Server 2005, 2=The new On-demand Processing Engine.</span></span> <span data-ttu-id="65a70-238">如果您的大多数报表仍在显示值 1，则可以研究如何对它们进行重新设计，以便利用更新且效率更高的按需处理引擎。</span><span class="sxs-lookup"><span data-stu-id="65a70-238">If a majority of your reports are still showing the value of 1, you may investigate how to redesign them so they utilize the newer and more efficient on-demand processing engine.</span></span>  
  
     `<ProcessingEngine>2</ProcessingEngine>`  
  
-   <span data-ttu-id="65a70-239">**ScalabilityTime**：在处理引擎中执行与缩放相关的操作所用的毫秒数。</span><span class="sxs-lookup"><span data-stu-id="65a70-239">**ScalabilityTime**: The number of milliseconds spent performing scale related operations in the processing engine.</span></span> <span data-ttu-id="65a70-240">值为 0 指示没有额外的时间用于进制运算，值为 0 还指示请求没有处于内存不足的状态。</span><span class="sxs-lookup"><span data-stu-id="65a70-240">A value of 0 indicates that no additional time was spent on scale operations and a 0 also indicates the request was not under memory pressure.</span></span>  
  
    ```  
    <ScalabilityTime>  
        <Processing>0</Processing>  
    </ScalabilityTime>  
    ```  
  
-   <span data-ttu-id="65a70-241">**EstimatedMemoryUsageKB**：特定请求期间每个组件使用的最大内存量（以 kb 为单位）。</span><span class="sxs-lookup"><span data-stu-id="65a70-241">**EstimatedMemoryUsageKB**: An estimate of the peak amount of memory, in kilobytes, consumed by each component during a particular request.</span></span>  
  
    ```  
    <EstimatedMemoryUsageKB>  
        <Processing>38</Processing>  
    </EstimatedMemoryUsageKB>  
    ```  
  
-   <span data-ttu-id="65a70-242">**DataExtension**：报表中使用的数据扩展插件或数据源的类型。</span><span class="sxs-lookup"><span data-stu-id="65a70-242">**DataExtension**: The types of data extensions or data sources used in the report.</span></span> <span data-ttu-id="65a70-243">该数目是特定数据源出现的次数。</span><span class="sxs-lookup"><span data-stu-id="65a70-243">The number is a count of the number of occurrences of the particular data source.</span></span>  
  
    ```  
    <DataExtension>  
       <DAX>2</DAX>  
    </DataExtension>  
    ```  
  
-   <span data-ttu-id="65a70-244">**ExternalImages**值为 (毫秒) 。</span><span class="sxs-lookup"><span data-stu-id="65a70-244">**ExternalImages**The value is in miliseconds.</span></span> <span data-ttu-id="65a70-245">此数据可用于诊断性能问题。</span><span class="sxs-lookup"><span data-stu-id="65a70-245">This data can be used to diagnose performance issues.</span></span> <span data-ttu-id="65a70-246">从外部 Web 服务器检索图像所需的时间可能使总体报表执行速度变慢。</span><span class="sxs-lookup"><span data-stu-id="65a70-246">The time needed to retrieve images from an external webserver may slow the overall report execution.</span></span> <span data-ttu-id="65a70-247">已在中添加 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="65a70-247">Added in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].</span></span>  
  
    ```  
    <ExternalImages>  
        <Count>3</Count>  
        <ByteCount>9268</ByteCount>  
        <ResourceFetchTime>9</ResourceFetchTime>  
    </ExternalImages>  
    ```  
  
-   <span data-ttu-id="65a70-248">**连接**：多个调配的结构。</span><span class="sxs-lookup"><span data-stu-id="65a70-248">**Connections**: A multi-leveled structure.</span></span> <span data-ttu-id="65a70-249">已在中添加 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="65a70-249">Added in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].</span></span>  
  
    ```  
    <Connections>  
        <Connection>  
          <ConnectionOpenTime>127</ConnectionOpenTime>  
          <DataSource>  
            <Name>DataSource1</Name>  
            <DataExtension>SQL</DataExtension>  
          </DataSource>  
          <DataSets>  
            <DataSet>  
              <Name>DataSet1</Name>  
              <RowsRead>16</RowsRead>  
              <TotalTimeDataRetrieval>655</TotalTimeDataRetrieval>  
              <QueryPrepareAndExecutionTime>94</QueryPrepareAndExecutionTime>  
              <ExecuteReaderTime>33</ExecuteReaderTime>  
              <DataReaderMappingTime>30</DataReaderMappingTime>  
              <DisposeDataReaderTime>1</DisposeDataReaderTime>  
            </DataSet>  
            <DataSet>  
              <Name>DataSet2</Name>  
              <RowsRead>3</RowsRead>  
              <TotalTimeDataRetrieval>16</TotalTimeDataRetrieval>  
              <QueryPrepareAndExecutionTime>2</QueryPrepareAndExecutionTime>  
              <ExecuteReaderTime>1</ExecuteReaderTime>  
              <DataReaderMappingTime>0</DataReaderMappingTime>  
              <DisposeDataReaderTime>0</DisposeDataReaderTime>  
            </DataSet>  
          </DataSets>  
        </Connection>  
    </Connections>  
  
    ```  
  
##  <a name="log-fields-executionlog2"></a><a name="bkmk_executionlog2"></a><span data-ttu-id="65a70-250">日志字段 (ExecutionLog2) </span><span class="sxs-lookup"><span data-stu-id="65a70-250">Log Fields (ExecutionLog2)</span></span>  
 <span data-ttu-id="65a70-251">此视图添加了几个新字段并且重命名了其他几个字段。</span><span class="sxs-lookup"><span data-stu-id="65a70-251">This view added a few new fields and renamed a few others.</span></span> <span data-ttu-id="65a70-252">下面是一个示例 Transact SQL 语句，从视图 ExecutionLog2 检索行。</span><span class="sxs-lookup"><span data-stu-id="65a70-252">The following is a sample Transact SQL statement to retrieve rows from the view ExecutionLog2.</span></span> <span data-ttu-id="65a70-253">该示例假定报表服务器数据库名为 **ReportServer**：</span><span class="sxs-lookup"><span data-stu-id="65a70-253">The sample assumes the report server database is named **ReportServer**:</span></span>  
  
```  
Use ReportServer  
select * from ExecutionLog2 order by TimeStart DESC  
```  
  
 <span data-ttu-id="65a70-254">下表描述在报表执行日志中捕获的数据</span><span class="sxs-lookup"><span data-stu-id="65a70-254">The following table describes the data that is captured in the report execution log</span></span>  
  
|<span data-ttu-id="65a70-255">列</span><span class="sxs-lookup"><span data-stu-id="65a70-255">Column</span></span>|<span data-ttu-id="65a70-256">说明</span><span class="sxs-lookup"><span data-stu-id="65a70-256">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="65a70-257">InstanceName</span><span class="sxs-lookup"><span data-stu-id="65a70-257">InstanceName</span></span>|<span data-ttu-id="65a70-258">处理请求的报表服务器实例的名称。</span><span class="sxs-lookup"><span data-stu-id="65a70-258">Name of the report server instance that handled the request.</span></span>|  
|<span data-ttu-id="65a70-259">ReportPath</span><span class="sxs-lookup"><span data-stu-id="65a70-259">ReportPath</span></span>|<span data-ttu-id="65a70-260">报表的路径结构。</span><span class="sxs-lookup"><span data-stu-id="65a70-260">The path structure to the report.</span></span>  <span data-ttu-id="65a70-261">例如，在报表管理器的根文件夹中名为“test”的报表将具有“/test”的 ReportPath。</span><span class="sxs-lookup"><span data-stu-id="65a70-261">For example a report named "test" which is the in root folder in Report Manager, would have a ReportPath of "/test".</span></span><br /><br /> <span data-ttu-id="65a70-262">保存在报表管理器上文件夹“samples”中的名为“test”的报表将具有“/Samples/test/”的 ReportPath</span><span class="sxs-lookup"><span data-stu-id="65a70-262">A report named "test" that is saved in the folder "samples" on Report Manager , will have a ReportPath of "/Samples/test/"</span></span>|  
|<span data-ttu-id="65a70-263">UserName</span><span class="sxs-lookup"><span data-stu-id="65a70-263">UserName</span></span>|<span data-ttu-id="65a70-264">用户标识符。</span><span class="sxs-lookup"><span data-stu-id="65a70-264">User identifier.</span></span>|  
|<span data-ttu-id="65a70-265">ExecutionID</span><span class="sxs-lookup"><span data-stu-id="65a70-265">ExecutionID</span></span>||  
|<span data-ttu-id="65a70-266">RequestType</span><span class="sxs-lookup"><span data-stu-id="65a70-266">RequestType</span></span>|<span data-ttu-id="65a70-267">请求类型（用户或系统）。</span><span class="sxs-lookup"><span data-stu-id="65a70-267">Request type (either user or system).</span></span>|  
|<span data-ttu-id="65a70-268">格式</span><span class="sxs-lookup"><span data-stu-id="65a70-268">Format</span></span>|<span data-ttu-id="65a70-269">呈现格式。</span><span class="sxs-lookup"><span data-stu-id="65a70-269">Rendering format.</span></span>|  
|<span data-ttu-id="65a70-270">参数</span><span class="sxs-lookup"><span data-stu-id="65a70-270">Parameters</span></span>|<span data-ttu-id="65a70-271">用于执行报表的参数值。</span><span class="sxs-lookup"><span data-stu-id="65a70-271">Parameter values used for a report execution.</span></span>|  
|<span data-ttu-id="65a70-272">ReportAction</span><span class="sxs-lookup"><span data-stu-id="65a70-272">ReportAction</span></span>|<span data-ttu-id="65a70-273">可能的值：Render、Sort、BookMarkNavigation、DocumentNavigation、GetDocumentMap、Findstring</span><span class="sxs-lookup"><span data-stu-id="65a70-273">Possible values: Render, Sort, BookMarkNavigation, DocumentNavigation, GetDocumentMap, Findstring</span></span>|  
|<span data-ttu-id="65a70-274">TimeStart</span><span class="sxs-lookup"><span data-stu-id="65a70-274">TimeStart</span></span>|<span data-ttu-id="65a70-275">指示报表进程的持续时段的开始时间和结束时间。</span><span class="sxs-lookup"><span data-stu-id="65a70-275">Start and stop times that indicate the duration of a report process.</span></span>|  
|<span data-ttu-id="65a70-276">TimeEnd</span><span class="sxs-lookup"><span data-stu-id="65a70-276">TimeEnd</span></span>||  
|<span data-ttu-id="65a70-277">TimeDataRetrieval</span><span class="sxs-lookup"><span data-stu-id="65a70-277">TimeDataRetrieval</span></span>|<span data-ttu-id="65a70-278">检索数据、处理报表以及呈现报表所用的毫秒数。</span><span class="sxs-lookup"><span data-stu-id="65a70-278">Number of milliseconds spent retrieving the data, processing the report, and rendering the report.</span></span>|  
|<span data-ttu-id="65a70-279">TimeProcessing</span><span class="sxs-lookup"><span data-stu-id="65a70-279">TimeProcessing</span></span>||  
|<span data-ttu-id="65a70-280">TimeRendering</span><span class="sxs-lookup"><span data-stu-id="65a70-280">TimeRendering</span></span>||  
|<span data-ttu-id="65a70-281">源</span><span class="sxs-lookup"><span data-stu-id="65a70-281">Source</span></span>|<span data-ttu-id="65a70-282">报表执行源（1 = 实时，2 = 缓存，3 = 快照，4 = 历史记录）。</span><span class="sxs-lookup"><span data-stu-id="65a70-282">Source of the report execution (1=Live, 2=Cache, 3=Snapshot, 4=History).</span></span>|  
|<span data-ttu-id="65a70-283">状态</span><span class="sxs-lookup"><span data-stu-id="65a70-283">Status</span></span>|<span data-ttu-id="65a70-284">状态（rsSuccess 或错误代码；如果发生多个错误，则只记录第一个）。</span><span class="sxs-lookup"><span data-stu-id="65a70-284">Status (either rsSuccess or an error code; if multiple errors occur, only the first error is recorded).</span></span>|  
|<span data-ttu-id="65a70-285">ByteCount</span><span class="sxs-lookup"><span data-stu-id="65a70-285">ByteCount</span></span>|<span data-ttu-id="65a70-286">所呈现的报表的大小（字节）。</span><span class="sxs-lookup"><span data-stu-id="65a70-286">Size of rendered reports in bytes.</span></span>|  
|<span data-ttu-id="65a70-287">RowCount</span><span class="sxs-lookup"><span data-stu-id="65a70-287">RowCount</span></span>|<span data-ttu-id="65a70-288">查询返回的结果行数。</span><span class="sxs-lookup"><span data-stu-id="65a70-288">Number of rows returned from queries.</span></span>|  
|<span data-ttu-id="65a70-289">AdditionalInfo</span><span class="sxs-lookup"><span data-stu-id="65a70-289">AdditionalInfo</span></span>|<span data-ttu-id="65a70-290">包含与执行有关的附加信息的 XML 属性包。</span><span class="sxs-lookup"><span data-stu-id="65a70-290">An XML property bag containing additional information about the execution.</span></span>|  
  
##  <a name="log-fields-executionlog"></a><a name="bkmk_executionlog"></a><span data-ttu-id="65a70-291">日志字段 (ExecutionLog) </span><span class="sxs-lookup"><span data-stu-id="65a70-291">Log Fields (ExecutionLog)</span></span>  
 <span data-ttu-id="65a70-292">下面是一个示例 Transact SQL 语句，从视图 ExecutionLog 检索行。</span><span class="sxs-lookup"><span data-stu-id="65a70-292">The following is a sample Transact SQL statement to retrieve rows from the view ExecutionLog.</span></span> <span data-ttu-id="65a70-293">该示例假定报表服务器数据库名为 **ReportServer**：</span><span class="sxs-lookup"><span data-stu-id="65a70-293">The sample assumes the report server database is named **ReportServer**:</span></span>  
  
```  
Use ReportServer  
select * from ExecutionLog order by TimeStart DESC  
  
```  
  
 <span data-ttu-id="65a70-294">下表描述在报表执行日志中捕获的数据</span><span class="sxs-lookup"><span data-stu-id="65a70-294">The following table describes the data that is captured in the report execution log</span></span>  
  
|<span data-ttu-id="65a70-295">列</span><span class="sxs-lookup"><span data-stu-id="65a70-295">Column</span></span>|<span data-ttu-id="65a70-296">说明</span><span class="sxs-lookup"><span data-stu-id="65a70-296">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="65a70-297">InstanceName</span><span class="sxs-lookup"><span data-stu-id="65a70-297">InstanceName</span></span>|<span data-ttu-id="65a70-298">处理请求的报表服务器实例的名称。</span><span class="sxs-lookup"><span data-stu-id="65a70-298">Name of the report server instance that handled the request.</span></span>|  
|<span data-ttu-id="65a70-299">ReportID</span><span class="sxs-lookup"><span data-stu-id="65a70-299">ReportID</span></span>|<span data-ttu-id="65a70-300">报表标识符。</span><span class="sxs-lookup"><span data-stu-id="65a70-300">Report identifier.</span></span>|  
|<span data-ttu-id="65a70-301">UserName</span><span class="sxs-lookup"><span data-stu-id="65a70-301">UserName</span></span>|<span data-ttu-id="65a70-302">用户标识符。</span><span class="sxs-lookup"><span data-stu-id="65a70-302">User identifier.</span></span>|  
|<span data-ttu-id="65a70-303">RequestType</span><span class="sxs-lookup"><span data-stu-id="65a70-303">RequestType</span></span>|<span data-ttu-id="65a70-304">可能的值：</span><span class="sxs-lookup"><span data-stu-id="65a70-304">Possible values:</span></span><br /><br /> <span data-ttu-id="65a70-305">True = 订阅请求</span><span class="sxs-lookup"><span data-stu-id="65a70-305">True = A Subscription request</span></span><br /><br /> <span data-ttu-id="65a70-306">False = 交互请求</span><span class="sxs-lookup"><span data-stu-id="65a70-306">False= An Interactive request</span></span>|  
|<span data-ttu-id="65a70-307">格式</span><span class="sxs-lookup"><span data-stu-id="65a70-307">Format</span></span>|<span data-ttu-id="65a70-308">呈现格式。</span><span class="sxs-lookup"><span data-stu-id="65a70-308">Rendering format.</span></span>|  
|<span data-ttu-id="65a70-309">参数</span><span class="sxs-lookup"><span data-stu-id="65a70-309">Parameters</span></span>|<span data-ttu-id="65a70-310">用于执行报表的参数值。</span><span class="sxs-lookup"><span data-stu-id="65a70-310">Parameter values used for a report execution.</span></span>|  
|<span data-ttu-id="65a70-311">TimeStart</span><span class="sxs-lookup"><span data-stu-id="65a70-311">TimeStart</span></span>|<span data-ttu-id="65a70-312">指示报表进程的持续时段的开始时间和结束时间。</span><span class="sxs-lookup"><span data-stu-id="65a70-312">Start and stop times that indicate the duration of a report process.</span></span>|  
|<span data-ttu-id="65a70-313">TimeEnd</span><span class="sxs-lookup"><span data-stu-id="65a70-313">TimeEnd</span></span>||  
|<span data-ttu-id="65a70-314">TimeDataRetrieval</span><span class="sxs-lookup"><span data-stu-id="65a70-314">TimeDataRetrieval</span></span>|<span data-ttu-id="65a70-315">检索数据、处理报表以及呈现报表所用的毫秒数。</span><span class="sxs-lookup"><span data-stu-id="65a70-315">Number of milliseconds spent retrieving the data, processing the report, and rendering the report.</span></span>|  
|<span data-ttu-id="65a70-316">TimeProcessing</span><span class="sxs-lookup"><span data-stu-id="65a70-316">TimeProcessing</span></span>||  
|<span data-ttu-id="65a70-317">TimeRendering</span><span class="sxs-lookup"><span data-stu-id="65a70-317">TimeRendering</span></span>||  
|<span data-ttu-id="65a70-318">源</span><span class="sxs-lookup"><span data-stu-id="65a70-318">Source</span></span>|<span data-ttu-id="65a70-319">报表执行的源。</span><span class="sxs-lookup"><span data-stu-id="65a70-319">Source of the report execution.</span></span> <span data-ttu-id="65a70-320">可能的值：（1 = 实时，2 = 缓存，3 = 快照，4 = 历史记录，5 = 特别，6 = 会话，7 = RDCE）。</span><span class="sxs-lookup"><span data-stu-id="65a70-320">Possible values: (1=Live, 2=Cache, 3=Snapshot, 4=History, 5=Adhoc, 6=Session, 7=RDCE).</span></span>|  
|<span data-ttu-id="65a70-321">状态</span><span class="sxs-lookup"><span data-stu-id="65a70-321">Status</span></span>|<span data-ttu-id="65a70-322">可能的值：rsSuccess、rsProcessingAborted 或错误代码。</span><span class="sxs-lookup"><span data-stu-id="65a70-322">Possible values: rsSuccess, rsProcessingAborted, or an error code.</span></span> <span data-ttu-id="65a70-323">如果出现多个错误，则只记录第一个错误。</span><span class="sxs-lookup"><span data-stu-id="65a70-323">If multiple errors occur, only the first error is recorded.</span></span>|  
|<span data-ttu-id="65a70-324">ByteCount</span><span class="sxs-lookup"><span data-stu-id="65a70-324">ByteCount</span></span>|<span data-ttu-id="65a70-325">所呈现的报表的大小（字节）。</span><span class="sxs-lookup"><span data-stu-id="65a70-325">Size of rendered reports in bytes.</span></span>|  
|<span data-ttu-id="65a70-326">RowCount</span><span class="sxs-lookup"><span data-stu-id="65a70-326">RowCount</span></span>|<span data-ttu-id="65a70-327">查询返回的结果行数。</span><span class="sxs-lookup"><span data-stu-id="65a70-327">Number of rows returned from queries.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="65a70-328">另请参阅</span><span class="sxs-lookup"><span data-stu-id="65a70-328">See Also</span></span>  
 <span data-ttu-id="65a70-329">[打开 SharePoint 跟踪日志 &#40;ULS Reporting Services 事件&#41;](turn-on-reporting-services-events-for-the-sharepoint-trace-log-uls.md) </span><span class="sxs-lookup"><span data-stu-id="65a70-329">[Turn on Reporting Services events for the SharePoint trace log &#40;ULS&#41;](turn-on-reporting-services-events-for-the-sharepoint-trace-log-uls.md) </span></span>  
 <span data-ttu-id="65a70-330">[Reporting Services 日志文件和来源](../report-server/reporting-services-log-files-and-sources.md) </span><span class="sxs-lookup"><span data-stu-id="65a70-330">[Reporting Services Log Files and Sources](../report-server/reporting-services-log-files-and-sources.md) </span></span>  
 [<span data-ttu-id="65a70-331">错误和事件参考 (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="65a70-331">Errors and Events Reference &#40;Reporting Services&#41;</span></span>](../troubleshooting/errors-and-events-reference-reporting-services.md)  
  
  
