---
title: 为 SharePoint 跟踪日志 (ULS) 启用 Reporting Services 事件 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 81110ef6-4289-405c-a931-e7e9f49e69ba
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b7d1b0a936c234035baf18ca947661de2663195a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586321"
---
# <a name="turn-on-reporting-services-events-for-the-sharepoint-trace-log-uls"></a><span data-ttu-id="4834a-102">为 SharePoint 跟踪日志 (ULS) 启用 Reporting Services 事件</span><span class="sxs-lookup"><span data-stu-id="4834a-102">Turn on Reporting Services events for the SharePoint trace log (ULS)</span></span>
  <span data-ttu-id="4834a-103">从 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]开始，SharePoint 模式下的 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 服务器可以将 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 事件写入 SharePoint 统一日志记录服务 (ULS) 跟踪日志。</span><span class="sxs-lookup"><span data-stu-id="4834a-103">Starting with [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] servers in SharePoint mode can write [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] events to the SharePoint Unified Logging Service (ULS) trace log.</span></span> [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="4834a-104">的类别在 SharePoint 管理中心的“监视”页上提供。</span><span class="sxs-lookup"><span data-stu-id="4834a-104">specific categories are available on the Monitoring page of SharePoint Central Administration.</span></span>

 <span data-ttu-id="4834a-105">本主题内容：</span><span class="sxs-lookup"><span data-stu-id="4834a-105">In this Topic:</span></span>

-   [<span data-ttu-id="4834a-106">一般 ULS 日志建议</span><span class="sxs-lookup"><span data-stu-id="4834a-106">General ULS Log Recommendations</span></span>](#bkmk_general)

-   [<span data-ttu-id="4834a-107">在 Reporting Services 类别中打开和关闭 Reporting Services 事件</span><span class="sxs-lookup"><span data-stu-id="4834a-107">To turn on and off Reporting Services events in the Reporting Services Category</span></span>](#bkmk_turnon)

-   [<span data-ttu-id="4834a-108">建议配置</span><span class="sxs-lookup"><span data-stu-id="4834a-108">Recommended Configuration</span></span>](#bkmk_recommended)

-   [<span data-ttu-id="4834a-109">读取日志条目</span><span class="sxs-lookup"><span data-stu-id="4834a-109">Reading the logs entries</span></span>](#bkmk_readentries)

-   [<span data-ttu-id="4834a-110">SQL Server Reporting Services 事件列表</span><span class="sxs-lookup"><span data-stu-id="4834a-110">List of SQL Server Reporting Services Events</span></span>](#bkmk_list)

-   [<span data-ttu-id="4834a-111">使用 PowerShell 查看日志文件</span><span class="sxs-lookup"><span data-stu-id="4834a-111">View a Log file with PowerShell</span></span>](#bkmk_powershell)

-   [<span data-ttu-id="4834a-112">跟踪日志位置</span><span class="sxs-lookup"><span data-stu-id="4834a-112">Trace Log Location</span></span>](#bkmk_trace)

##  <a name="general-uls-log-recommendations"></a><a name="bkmk_general"></a> <span data-ttu-id="4834a-113">一般 ULS 日志建议</span><span class="sxs-lookup"><span data-stu-id="4834a-113">General ULS Log Recommendations</span></span>
 <span data-ttu-id="4834a-114">下表列出了监视 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 环境的推荐事件类别和级别。</span><span class="sxs-lookup"><span data-stu-id="4834a-114">The following table lists event categories and levels that are recommended for monitoring a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] environment..</span></span> <span data-ttu-id="4834a-115">记录事件时，每一项都包括记录事件的时间、进程名和线程 ID。</span><span class="sxs-lookup"><span data-stu-id="4834a-115">When an event is logged, each entry includes the time the event was logged, the process name, and the thread ID.</span></span>

|<span data-ttu-id="4834a-116">类别</span><span class="sxs-lookup"><span data-stu-id="4834a-116">Category</span></span>|<span data-ttu-id="4834a-117">级别</span><span class="sxs-lookup"><span data-stu-id="4834a-117">Level</span></span>|<span data-ttu-id="4834a-118">说明</span><span class="sxs-lookup"><span data-stu-id="4834a-118">Description</span></span>|
|--------------|-----------|-----------------|
|<span data-ttu-id="4834a-119">数据库</span><span class="sxs-lookup"><span data-stu-id="4834a-119">Database</span></span>|<span data-ttu-id="4834a-120">“详细”</span><span class="sxs-lookup"><span data-stu-id="4834a-120">Verbose</span></span>|<span data-ttu-id="4834a-121">记录涉及数据库访问的事件。</span><span class="sxs-lookup"><span data-stu-id="4834a-121">Logs events that involve database access.</span></span>|
|<span data-ttu-id="4834a-122">常规</span><span class="sxs-lookup"><span data-stu-id="4834a-122">General</span></span>|<span data-ttu-id="4834a-123">“详细”</span><span class="sxs-lookup"><span data-stu-id="4834a-123">Verbose</span></span>|<span data-ttu-id="4834a-124">记录涉及访问以下各项的事件：</span><span class="sxs-lookup"><span data-stu-id="4834a-124">Logs events that involve access to the following items:</span></span><br /><br /> [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="4834a-125">网页</span><span class="sxs-lookup"><span data-stu-id="4834a-125">Web pages</span></span><br /><br /> <span data-ttu-id="4834a-126">报表查看器 HTTP 处理程序</span><span class="sxs-lookup"><span data-stu-id="4834a-126">Report Viewer HTTP handler</span></span><br /><br /> <span data-ttu-id="4834a-127">报表访问（.rdl 文件）</span><span class="sxs-lookup"><span data-stu-id="4834a-127">Report access (.rdl files)</span></span><br /><br /> <span data-ttu-id="4834a-128">数据源（.rsds 文件）</span><span class="sxs-lookup"><span data-stu-id="4834a-128">Data sources (.rsds files)</span></span><br /><br /> <span data-ttu-id="4834a-129">SharePoint 网站上的 URL（.smdl 文件）</span><span class="sxs-lookup"><span data-stu-id="4834a-129">URLs on the SharePoint site (.smdl files)</span></span>|
|<span data-ttu-id="4834a-130">Office Server 常规</span><span class="sxs-lookup"><span data-stu-id="4834a-130">Office Server General</span></span>|<span data-ttu-id="4834a-131">异常</span><span class="sxs-lookup"><span data-stu-id="4834a-131">Exception</span></span>|<span data-ttu-id="4834a-132">记录登录失败。</span><span class="sxs-lookup"><span data-stu-id="4834a-132">Logs logon failures.</span></span>|
|<span data-ttu-id="4834a-133">拓扑</span><span class="sxs-lookup"><span data-stu-id="4834a-133">Topology</span></span>|<span data-ttu-id="4834a-134">“详细”</span><span class="sxs-lookup"><span data-stu-id="4834a-134">Verbose</span></span>|<span data-ttu-id="4834a-135">记录当前用户信息。</span><span class="sxs-lookup"><span data-stu-id="4834a-135">Logs current user information.</span></span>|
|<span data-ttu-id="4834a-136">Web 部件</span><span class="sxs-lookup"><span data-stu-id="4834a-136">Web Parts</span></span>|<span data-ttu-id="4834a-137">“详细”</span><span class="sxs-lookup"><span data-stu-id="4834a-137">Verbose</span></span>|<span data-ttu-id="4834a-138">记录涉及访问报表查看器 Web 部件的事件。</span><span class="sxs-lookup"><span data-stu-id="4834a-138">Logs events that involve access to the Report Viewer Web Part.</span></span>|

##  <a name="to-turn-on-and-off-reporting-services-events-in-the-reporting-services-category"></a><a name="bkmk_turnon"></a> <span data-ttu-id="4834a-139">在 Reporting Services 类别中打开和关闭 Reporting Services 事件</span><span class="sxs-lookup"><span data-stu-id="4834a-139">To turn on and off Reporting Services events in the Reporting Services Category</span></span>

1.  <span data-ttu-id="4834a-140">从 SharePoint 管理中心</span><span class="sxs-lookup"><span data-stu-id="4834a-140">From SharePoint Central Administration</span></span>

2.  <span data-ttu-id="4834a-141">单击 **“监视”** 。</span><span class="sxs-lookup"><span data-stu-id="4834a-141">Click **Monitoring**.</span></span>

3.  <span data-ttu-id="4834a-142">在 **“报告”** 组中单击 **“配置诊断日志记录”** 。</span><span class="sxs-lookup"><span data-stu-id="4834a-142">Click **Configure Diagnostic Logging** in the **Reporting** group.</span></span>

4.  <span data-ttu-id="4834a-143">在类别列表中找到 **SQL Server Reporting Services** 。</span><span class="sxs-lookup"><span data-stu-id="4834a-143">Find **SQL Server Reporting Services** in the category list.</span></span>

5.  <span data-ttu-id="4834a-144">单击加号 (+) 以展开 **SQL Server Reporting Services**下的子类别。</span><span class="sxs-lookup"><span data-stu-id="4834a-144">Click the plus symbol (+) to expand the sub categories under **SQL Server Reporting Services**.</span></span>

6.  <span data-ttu-id="4834a-145">选择要添加到跟踪日志中的子类别。</span><span class="sxs-lookup"><span data-stu-id="4834a-145">Select the subcategories to be added to the trace log.</span></span>

7.  <span data-ttu-id="4834a-146">在类别列表的底部，为 **“要报告给跟踪日志的严重程度最低的事件”** 选择一个事件级别。</span><span class="sxs-lookup"><span data-stu-id="4834a-146">At the bottom of the categories list, select an event level for the **Least critical event to report to the trace log**.</span></span> <span data-ttu-id="4834a-147">选择 **“无”** 以禁用跟踪。</span><span class="sxs-lookup"><span data-stu-id="4834a-147">Select **None** to disable tracing.</span></span>

> [!NOTE]
>  <span data-ttu-id="4834a-148">**不支持选项** “要报告给事件日志的严重程度最低的事件” [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4834a-148">The option **Least critical event to report to the event log** is not supported by [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="4834a-149">已忽略该选项。</span><span class="sxs-lookup"><span data-stu-id="4834a-149">The option is ignored.</span></span>

##  <a name="recommended-configuration"></a><a name="bkmk_recommended"></a> <span data-ttu-id="4834a-150">建议配置</span><span class="sxs-lookup"><span data-stu-id="4834a-150">Recommended Configuration</span></span>
 <span data-ttu-id="4834a-151">以下日志记录选项建议用作标准配置：</span><span class="sxs-lookup"><span data-stu-id="4834a-151">The following logging options are recommended as a standard configuration:</span></span>

-   <span data-ttu-id="4834a-152">**HTTP 重定向程序**</span><span class="sxs-lookup"><span data-stu-id="4834a-152">**HTTP Redirector**</span></span>

-   <span data-ttu-id="4834a-153">**SOAP 客户端代理**</span><span class="sxs-lookup"><span data-stu-id="4834a-153">**SOAP Client Proxy**</span></span>

-   <span data-ttu-id="4834a-154">如果您遇到配置问题，则添加 **“配置页”** 。</span><span class="sxs-lookup"><span data-stu-id="4834a-154">If you are experiencing issues with configuration, add **Configuration Pages**.</span></span>

 <span data-ttu-id="4834a-155">您可以使用以下 PowerShell cmdlet 检查所有当前的场诊断日志设置：</span><span class="sxs-lookup"><span data-stu-id="4834a-155">You can review all of the current farm diagnostic log settings with the following PowerShell cmdlet:</span></span>

```powershell
Get-SPDiagnosticConfig
```

##  <a name="reading-the-logs-entries"></a><a name="bkmk_readentries"></a> <span data-ttu-id="4834a-156">读取日志条目</span><span class="sxs-lookup"><span data-stu-id="4834a-156">Reading the logs entries</span></span>
 <span data-ttu-id="4834a-157">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 日志中的条目采用以下方式进行格式化。</span><span class="sxs-lookup"><span data-stu-id="4834a-157">The [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] entries in the log are formatted in the following way.</span></span>

1.  <span data-ttu-id="4834a-158">**产品：SQL Server Reporting Services**</span><span class="sxs-lookup"><span data-stu-id="4834a-158">**Product:SQL Server Reporting Services**</span></span>

2.  <span data-ttu-id="4834a-159">**类别：** 与服务器相关的事件将在名称的开头带有字符“Report Server”。</span><span class="sxs-lookup"><span data-stu-id="4834a-159">**Category:** Events related to the server will have the characters "Report Server", at the beginning of the name.</span></span> <span data-ttu-id="4834a-160">例如“Report Server Alerting Runtime”，这些事件还将记录到报表服务器日志文件。</span><span class="sxs-lookup"><span data-stu-id="4834a-160">For example "Report Server Alerting Runtime" These events are also logged to the report server log files.</span></span>

3.  <span data-ttu-id="4834a-161">**类别：** 与 Web 前端组件相关或从中进行通信的事件不包含“Report Server”。</span><span class="sxs-lookup"><span data-stu-id="4834a-161">**Category:** Events related to or communicated from a web front-end component do not contain "Report Server".</span></span> <span data-ttu-id="4834a-162">例如“服务应用程序代理”、“报表服务器警报运行时”。</span><span class="sxs-lookup"><span data-stu-id="4834a-162">For example "Service Application Proxy" Report Server Alerting Runtime".</span></span> <span data-ttu-id="4834a-163">WFE 条目包含 CorrelationID，而服务器条目不包含。</span><span class="sxs-lookup"><span data-stu-id="4834a-163">The WFE entries do contain a CorrelationID but the server entries do not.</span></span>

##  <a name="list-of-sql-server-reporting-services-events"></a><a name="bkmk_list"></a> <span data-ttu-id="4834a-164">SQL Server Reporting Services 事件列表</span><span class="sxs-lookup"><span data-stu-id="4834a-164">List of SQL Server Reporting Services Events</span></span>
 <span data-ttu-id="4834a-165">下表是 SQL Server Reporting Services 类别中事件的列表：</span><span class="sxs-lookup"><span data-stu-id="4834a-165">The following table is a list of the events in the SQL Server Reporting Services Category:</span></span>

|<span data-ttu-id="4834a-166">区域名称</span><span class="sxs-lookup"><span data-stu-id="4834a-166">Area Name</span></span>|<span data-ttu-id="4834a-167">说明或示例条目</span><span class="sxs-lookup"><span data-stu-id="4834a-167">Description or sample entries</span></span>|
|---------------|-----------------------------------|
|<span data-ttu-id="4834a-168">“配置页”</span><span class="sxs-lookup"><span data-stu-id="4834a-168">Configuration Pages</span></span>||
|<span data-ttu-id="4834a-169">HTTP 重定向程序</span><span class="sxs-lookup"><span data-stu-id="4834a-169">HTTP Redirector</span></span>||
|<span data-ttu-id="4834a-170">本地模式处理</span><span class="sxs-lookup"><span data-stu-id="4834a-170">Local Mode Processing</span></span>||
|<span data-ttu-id="4834a-171">本地模式呈现</span><span class="sxs-lookup"><span data-stu-id="4834a-171">Local Mode Rendering</span></span>||
|<span data-ttu-id="4834a-172">SOAP 客户端代理</span><span class="sxs-lookup"><span data-stu-id="4834a-172">SOAP Client Proxy</span></span>||
|<span data-ttu-id="4834a-173">UI 页</span><span class="sxs-lookup"><span data-stu-id="4834a-173">UI Pages</span></span>||
|<span data-ttu-id="4834a-174">Power View</span><span class="sxs-lookup"><span data-stu-id="4834a-174">Power View</span></span>|<span data-ttu-id="4834a-175">写入 **LogClientTraceEvents** API 的日志条目。</span><span class="sxs-lookup"><span data-stu-id="4834a-175">Log entries that were written to the **LogClientTraceEvents** API.</span></span> <span data-ttu-id="4834a-176">这些条目源自客户端应用程序，包括 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] （ [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 用于 Enterprise Edition 的外接程序的一项功能） [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="4834a-176">These entries are sourced from client applications, including [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], a feature of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Add-in for [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[SPS2010](../../includes/sps2010-md.md)] Enterprise Edition.</span></span><br /><br /> <span data-ttu-id="4834a-177">来自 LogClientTraceEvents API 的所有日志条目将记录在“SQL Server Reporting Services”的“类别”和“Power View”的“区域”下   。</span><span class="sxs-lookup"><span data-stu-id="4834a-177">All log entries from the LogClientTraceEvents API will be logged under the **Category** of "SQL Server Reporting Services" and the **Area** of "Power View".</span></span><br /><br /> <span data-ttu-id="4834a-178">使用“Power View”区域记录的条目内容由客户端应用程序决定。</span><span class="sxs-lookup"><span data-stu-id="4834a-178">The content of entries logged with the area of "Power View" is determined by the client application.</span></span>|
|<span data-ttu-id="4834a-179">报表服务器警报运行时</span><span class="sxs-lookup"><span data-stu-id="4834a-179">Report Server Alerting Runtime</span></span>||
|<span data-ttu-id="4834a-180">报表服务器应用程序域管理器</span><span class="sxs-lookup"><span data-stu-id="4834a-180">Report Server App Domain Manager</span></span>||
|<span data-ttu-id="4834a-181">报表服务器缓冲响应</span><span class="sxs-lookup"><span data-stu-id="4834a-181">Report Server Buffered Response</span></span>||
|<span data-ttu-id="4834a-182">报表服务器缓存</span><span class="sxs-lookup"><span data-stu-id="4834a-182">Report Server Cache</span></span>||
|<span data-ttu-id="4834a-183">报表服务器目录</span><span class="sxs-lookup"><span data-stu-id="4834a-183">Report Server Catalog</span></span>||
|<span data-ttu-id="4834a-184">报表服务器块区</span><span class="sxs-lookup"><span data-stu-id="4834a-184">Report Server Chunk</span></span>||
|<span data-ttu-id="4834a-185">报表服务器清除</span><span class="sxs-lookup"><span data-stu-id="4834a-185">Report Server Cleanup</span></span>||
|<span data-ttu-id="4834a-186">报表服务器配置管理器</span><span class="sxs-lookup"><span data-stu-id="4834a-186">Report Server Configuration Manager</span></span>|<span data-ttu-id="4834a-187">示例条目：</span><span class="sxs-lookup"><span data-stu-id="4834a-187">Sample entries:</span></span><br /><br /> <span data-ttu-id="4834a-188">MediumUsing 报表服务器内部 URL http://localhost:80/ReportServer。</span><span class="sxs-lookup"><span data-stu-id="4834a-188">MediumUsing report server internal url http://localhost:80/ReportServer.</span></span><br /><br /> <span data-ttu-id="4834a-189">UnexpectedMissing or Invalid ExtendedProtectionLevel setting</span><span class="sxs-lookup"><span data-stu-id="4834a-189">UnexpectedMissing or Invalid ExtendedProtectionLevel setting</span></span>|
|<span data-ttu-id="4834a-190">报表服务器 Crypto</span><span class="sxs-lookup"><span data-stu-id="4834a-190">Report Server Crypto</span></span>||
|<span data-ttu-id="4834a-191">报表服务器数据扩展插件</span><span class="sxs-lookup"><span data-stu-id="4834a-191">Report Server Data Extension</span></span>||
|<span data-ttu-id="4834a-192">报表服务器数据库轮询</span><span class="sxs-lookup"><span data-stu-id="4834a-192">Report Server DB Polling</span></span>||
|<span data-ttu-id="4834a-193">报表服务器默认值</span><span class="sxs-lookup"><span data-stu-id="4834a-193">Report Server Default</span></span>||
|<span data-ttu-id="4834a-194">报表服务器电子邮件扩展插件</span><span class="sxs-lookup"><span data-stu-id="4834a-194">Report Server Email Extension</span></span>||
|<span data-ttu-id="4834a-195">报表服务器 Excel 呈现器</span><span class="sxs-lookup"><span data-stu-id="4834a-195">Report Server Excel Renderer</span></span>||
|<span data-ttu-id="4834a-196">报表服务器扩展插件工厂</span><span class="sxs-lookup"><span data-stu-id="4834a-196">Report Server Extension Factory</span></span>||
|<span data-ttu-id="4834a-197">报表服务器 HTTP 运行时</span><span class="sxs-lookup"><span data-stu-id="4834a-197">Report Server HTTP Runtime</span></span>||
|<span data-ttu-id="4834a-198">报表服务器图像呈现器</span><span class="sxs-lookup"><span data-stu-id="4834a-198">Report Server Image Renderer</span></span>||
|<span data-ttu-id="4834a-199">报表服务器内存监视</span><span class="sxs-lookup"><span data-stu-id="4834a-199">Report Server Memory Monitoring</span></span>||
|<span data-ttu-id="4834a-200">报表服务器通知</span><span class="sxs-lookup"><span data-stu-id="4834a-200">Report Server Notification</span></span>||
|<span data-ttu-id="4834a-201">报表服务器处理</span><span class="sxs-lookup"><span data-stu-id="4834a-201">Report Server Processing</span></span>||
|<span data-ttu-id="4834a-202">报表服务器提供程序</span><span class="sxs-lookup"><span data-stu-id="4834a-202">Report Server Provider</span></span>||
|<span data-ttu-id="4834a-203">报表服务器呈现</span><span class="sxs-lookup"><span data-stu-id="4834a-203">Report Server Rendering</span></span>||
|<span data-ttu-id="4834a-204">报表服务器报表预览</span><span class="sxs-lookup"><span data-stu-id="4834a-204">Report Server Report Preview</span></span>||
|<span data-ttu-id="4834a-205">报表服务器资源实用工具</span><span class="sxs-lookup"><span data-stu-id="4834a-205">Report Server Resource Utility</span></span>|<span data-ttu-id="4834a-206">示例条目：</span><span class="sxs-lookup"><span data-stu-id="4834a-206">Sample Entries:</span></span><br /><br /> <span data-ttu-id="4834a-207">MediumReporting Services starting SKU: Evaluation</span><span class="sxs-lookup"><span data-stu-id="4834a-207">MediumReporting Services starting SKU: Evaluation</span></span><br /><br /> <span data-ttu-id="4834a-208">MediumEvaluation copy: 180 days left</span><span class="sxs-lookup"><span data-stu-id="4834a-208">MediumEvaluation copy: 180 days left</span></span>|
|<span data-ttu-id="4834a-209">报表服务器运行作业</span><span class="sxs-lookup"><span data-stu-id="4834a-209">Report Server Running Jobs</span></span>||
|<span data-ttu-id="4834a-210">报表服务器运行请求</span><span class="sxs-lookup"><span data-stu-id="4834a-210">Report Server Running Requests</span></span>||
|<span data-ttu-id="4834a-211">报表服务器计划</span><span class="sxs-lookup"><span data-stu-id="4834a-211">Report Server Schedule</span></span>||
|<span data-ttu-id="4834a-212">报表服务器安全性</span><span class="sxs-lookup"><span data-stu-id="4834a-212">Report Server Security</span></span>||
|<span data-ttu-id="4834a-213">报表服务器服务控制器</span><span class="sxs-lookup"><span data-stu-id="4834a-213">Report Server Service Controller</span></span>||
|<span data-ttu-id="4834a-214">报表服务器会话</span><span class="sxs-lookup"><span data-stu-id="4834a-214">Report Server Session</span></span>||
|<span data-ttu-id="4834a-215">报表服务器订阅</span><span class="sxs-lookup"><span data-stu-id="4834a-215">Report Server Subscription</span></span>||
|<span data-ttu-id="4834a-216">报表服务器 WCF 运行时</span><span class="sxs-lookup"><span data-stu-id="4834a-216">Report Server WCF Runtime</span></span>||
|<span data-ttu-id="4834a-217">报表服务器 Web 服务</span><span class="sxs-lookup"><span data-stu-id="4834a-217">Report Server Web Server</span></span>||
|<span data-ttu-id="4834a-218">服务应用程序代理</span><span class="sxs-lookup"><span data-stu-id="4834a-218">Service Application Proxy</span></span>||
|<span data-ttu-id="4834a-219">共享服务</span><span class="sxs-lookup"><span data-stu-id="4834a-219">Shared Service</span></span>|<span data-ttu-id="4834a-220">示例条目：</span><span class="sxs-lookup"><span data-stu-id="4834a-220">Sample entries:</span></span><br /><br /> <span data-ttu-id="4834a-221">MediumUpdating ReportingWebServiceApplication</span><span class="sxs-lookup"><span data-stu-id="4834a-221">MediumUpdating ReportingWebServiceApplication</span></span><br /><br /> <span data-ttu-id="4834a-222">MediumGranting access to content databases.</span><span class="sxs-lookup"><span data-stu-id="4834a-222">MediumGranting access to content databases.</span></span><br /><br /> <span data-ttu-id="4834a-223">MediumProvisioning instances for ReportingWebServiceApplication</span><span class="sxs-lookup"><span data-stu-id="4834a-223">MediumProvisioning instances for ReportingWebServiceApplication</span></span><br /><br /> <span data-ttu-id="4834a-224">MediumProcessing service account change for ReportingWebServiceApplication</span><span class="sxs-lookup"><span data-stu-id="4834a-224">MediumProcessing service account change for ReportingWebServiceApplication</span></span><br /><br /> <span data-ttu-id="4834a-225">MediumSetting database permissions.</span><span class="sxs-lookup"><span data-stu-id="4834a-225">MediumSetting database permissions.</span></span>|

##  <a name="view-a-log-file-with-powershell"></a><a name="bkmk_powershell"></a> <span data-ttu-id="4834a-226">使用 PowerShell 查看日志文件</span><span class="sxs-lookup"><span data-stu-id="4834a-226">View a Log file with PowerShell</span></span>
 <span data-ttu-id="4834a-227">![PowerShell 相关内容](../media/rs-powershellicon.jpg "PowerShell 相关内容")可以使用 PowerShell 从 ULS 日志文件中返回 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 相关事件列表。</span><span class="sxs-lookup"><span data-stu-id="4834a-227">![PowerShell related content](../media/rs-powershellicon.jpg "PowerShell related content")You can use PowerShell to return a list of the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] related events from a ULS Log file.</span></span> <span data-ttu-id="4834a-228">从 SharePoint 2010 Management Shell 运行以下命令以便从该文件（ULS 日志文件 UESQL11SPOINT-20110606-1530.log）中返回包含“sql server reporting services”的行的筛选后列表  ：</span><span class="sxs-lookup"><span data-stu-id="4834a-228">Type the following command from the SharePoint 2010 Management Shell to return a filtered list of rows from the file a ULS log file UESQL11SPOINT-20110606-1530.log, that contain "**sql server reporting services**":</span></span>

```powershell
Get-Content -Path "C:\Program Files\Common Files\Microsoft Shared\Web Server Extensions\14\LOGS\UESQL11SPOINT-20110606-1530.log" | Select-String "sql server reporting services"
```

 <span data-ttu-id="4834a-229">有许多可以下载的工具，通过这些工具可以读取 ULS 日志。</span><span class="sxs-lookup"><span data-stu-id="4834a-229">There are also many tools you can download which will allow you read ULS logs.</span></span> <span data-ttu-id="4834a-230">例如， [SharePoint LogViewer](https://sharepointlogviewer.codeplex.com/) 或 [SharePoint ULS Log Viewer](http://ulsviewer.codeplex.com/workitem/list/basic)。</span><span class="sxs-lookup"><span data-stu-id="4834a-230">For example, the [SharePoint LogViewer](https://sharepointlogviewer.codeplex.com/) or [SharePoint ULS Log Viewer](http://ulsviewer.codeplex.com/workitem/list/basic).</span></span> <span data-ttu-id="4834a-231">两者都在 CodePlex 上提供。</span><span class="sxs-lookup"><span data-stu-id="4834a-231">Both are available on CodePlex.</span></span>

 <span data-ttu-id="4834a-232">有关如何使用 PowerShell 查看日志数据的详细信息，请参阅 [查看诊断日志 (SharePoint Server 2010)](https://technet.microsoft.com/library/ff463595.aspx)</span><span class="sxs-lookup"><span data-stu-id="4834a-232">For more information on how to use PowerShell to view log data, see [View diagnostic logs (SharePoint Server 2010)](https://technet.microsoft.com/library/ff463595.aspx)</span></span>

##  <a name="trace-log-location"></a><a name="bkmk_trace"></a><span data-ttu-id="4834a-233">跟踪日志位置</span><span class="sxs-lookup"><span data-stu-id="4834a-233">Trace Log Location</span></span>
 <span data-ttu-id="4834a-234">跟踪日志文件通常位于文件夹 **c:\Program Files\Common files\Microsoft Shared\Web Server Extensions\14\logs** 中，但您可以从 SharePoint 管理中心的 **“诊断日志记录”** 页中验证或更改此路径。</span><span class="sxs-lookup"><span data-stu-id="4834a-234">The Trace Log files are usually found in the folder **c:\Program Files\Common files\Microsoft Shared\Web Server Extensions\14\logs** but you can verify or change the path from the **Diagnostic Logging** page in SharePoint Central Administration.</span></span>

