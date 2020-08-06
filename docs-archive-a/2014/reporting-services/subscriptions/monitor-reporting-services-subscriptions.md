---
title: 监视 Reporting Services 订阅 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [Reporting Services], inactive
- subscriptions [Reporting Services], status
- monitoring [Reporting Services], subscriptions
- status information [Reporting Services]
- inactive subscriptions [Reporting Services]
ms.assetid: 054c4a87-60bf-4556-9a8c-8b2d77a534e6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7c94cd093fb4a5a095e270ae3cb0eb29d795347e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587163"
---
# <a name="monitor-reporting-services-subscriptions"></a><span data-ttu-id="e0657-102">监视 Reporting Services 订阅</span><span class="sxs-lookup"><span data-stu-id="e0657-102">Monitor Reporting Services Subscriptions</span></span>
  <span data-ttu-id="e0657-103">你可以从用户界面、Windows PowerShell 或日志文件监视 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 订阅。</span><span class="sxs-lookup"><span data-stu-id="e0657-103">You can monitor [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] subscriptions from the user interface, Windows PowerShell, or log files.</span></span> <span data-ttu-id="e0657-104">可用于监视的选项取决于你正在运行的报表服务器的模式。</span><span class="sxs-lookup"><span data-stu-id="e0657-104">The options available to you for monitoring depend on what mode of report server you are running.</span></span>  
  
||  
|-|  
|<span data-ttu-id="e0657-105">**[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 本机模式 | [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 模式</span><span class="sxs-lookup"><span data-stu-id="e0657-105">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode &#124; [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode</span></span>|  
  
 <span data-ttu-id="e0657-106">**本主题内容：**</span><span class="sxs-lookup"><span data-stu-id="e0657-106">**In this topic:**</span></span>  
  
-   [<span data-ttu-id="e0657-107">本机模式用户界面</span><span class="sxs-lookup"><span data-stu-id="e0657-107">Native mode user interface</span></span>](#bkmk_native_mode)  
  
-   [<span data-ttu-id="e0657-108">SharePoint 模式</span><span class="sxs-lookup"><span data-stu-id="e0657-108">SharePoint Mode</span></span>](#bkmk_sharepoint_mode)  
  
-   [<span data-ttu-id="e0657-109">使用 PowerShell 监视订阅</span><span class="sxs-lookup"><span data-stu-id="e0657-109">Use PowerShell to monitor subscriptions</span></span>](#bkmk_use_powershell)  
  
-   [<span data-ttu-id="e0657-110">管理非活动订阅</span><span class="sxs-lookup"><span data-stu-id="e0657-110">Managing Inactive Subscriptions</span></span>](#bkmk_manage_inactive)  
  
##  <a name="native-mode-user-interface"></a><a name="bkmk_native_mode"></a> <span data-ttu-id="e0657-111">本机模式用户界面</span><span class="sxs-lookup"><span data-stu-id="e0657-111">Native mode user interface</span></span>  
 <span data-ttu-id="e0657-112">单个 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 用户可以使用 \*\*\*\* “我的订阅”页面或报表管理器中的 \*\*\*\* “订阅”选项卡来监视订阅状态。</span><span class="sxs-lookup"><span data-stu-id="e0657-112">Individual [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] users can monitor the status of a subscription using the **My Subscriptions** page or the **Subscriptions** tab in Report Manager.</span></span> <span data-ttu-id="e0657-113">“订阅”页中包括指示订阅最后运行的时间和订阅状态的列。</span><span class="sxs-lookup"><span data-stu-id="e0657-113">Subscription pages include columns that indicate when the subscription was last run and the status of the subscription.</span></span> <span data-ttu-id="e0657-114">如果已安排订阅处理计划，则将会更新状态消息。</span><span class="sxs-lookup"><span data-stu-id="e0657-114">Status messages are updated when the subscription is scheduled to process.</span></span> <span data-ttu-id="e0657-115">如果从未引发触发器（例如，从未刷新报表执行快照或计划从未运行），则不会更新状态消息。</span><span class="sxs-lookup"><span data-stu-id="e0657-115">If the trigger never occurs (for example, a report execution snapshot is never refreshed or a schedule never runs), the status message will not be updated.</span></span>  
  
 <span data-ttu-id="e0657-116">下表描述了  “状态”列的可能的值。</span><span class="sxs-lookup"><span data-stu-id="e0657-116">The following table describes the possible values for the **Status** column.</span></span>  
  
|<span data-ttu-id="e0657-117">状态</span><span class="sxs-lookup"><span data-stu-id="e0657-117">Status</span></span>|<span data-ttu-id="e0657-118">说明</span><span class="sxs-lookup"><span data-stu-id="e0657-118">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="e0657-119">新订阅</span><span class="sxs-lookup"><span data-stu-id="e0657-119">New subscription</span></span>|<span data-ttu-id="e0657-120">在您首次创建订阅时显示。</span><span class="sxs-lookup"><span data-stu-id="e0657-120">Appears when you first create the subscription.</span></span>|  
|<span data-ttu-id="e0657-121">非活动</span><span class="sxs-lookup"><span data-stu-id="e0657-121">Inactive</span></span>|<span data-ttu-id="e0657-122">无法处理订阅时显示。</span><span class="sxs-lookup"><span data-stu-id="e0657-122">Appears when a subscription is cannot be processed.</span></span> <span data-ttu-id="e0657-123">有关详细信息，请参阅本主题后面的“管理不活动订阅”部分。</span><span class="sxs-lookup"><span data-stu-id="e0657-123">For more information, see "Managing Inactive Subscriptions" later in this topic.</span></span>|  
|<span data-ttu-id="e0657-124">已完成：已 \<*number*> 处理 \<*number*> total; 个 \<*number*> 错误。</span><span class="sxs-lookup"><span data-stu-id="e0657-124">Done: \<*number*> processed of \<*number*> total; \<*number*> errors.</span></span>|<span data-ttu-id="e0657-125">显示数据驱动订阅执行的状态；此消息来自计划和传递处理器。</span><span class="sxs-lookup"><span data-stu-id="e0657-125">Shows the status of a data-driven subscription execution; this message is from the Scheduling and Delivery Processor.</span></span>|  
|<span data-ttu-id="e0657-126">\<*number*>#a1</span><span class="sxs-lookup"><span data-stu-id="e0657-126">\<*number*> processed</span></span>|<span data-ttu-id="e0657-127">计划和传递处理器成功传递或不再试图传递的通知数。</span><span class="sxs-lookup"><span data-stu-id="e0657-127">The number of notifications that the Scheduling and Delivery Processor successfully delivered or is no longer attempting to deliver.</span></span> <span data-ttu-id="e0657-128">当数据驱动传递完成后，已处理通知数应等于已生成通知的总数。</span><span class="sxs-lookup"><span data-stu-id="e0657-128">When a data-driven delivery completes, the number of processed notifications should equal the total number of generated notifications.</span></span>|  
|<span data-ttu-id="e0657-129">\<*number*>总</span><span class="sxs-lookup"><span data-stu-id="e0657-129">\<*number*> total</span></span>|<span data-ttu-id="e0657-130">最后一次传递订阅生成的通知总数。</span><span class="sxs-lookup"><span data-stu-id="e0657-130">The total number of notifications generated for the last delivery for the subscription.</span></span>|  
|<span data-ttu-id="e0657-131">\<*number*>条</span><span class="sxs-lookup"><span data-stu-id="e0657-131">\<*number*> error</span></span>|<span data-ttu-id="e0657-132">计划和传递处理器无法传递或不再试图传递的通知数。</span><span class="sxs-lookup"><span data-stu-id="e0657-132">The number of notifications that the Scheduling and Delivery Processor could not deliver or is no longer attempting to deliver.</span></span>|  
|<span data-ttu-id="e0657-133">无法发送邮件：传输无法连接到服务器。</span><span class="sxs-lookup"><span data-stu-id="e0657-133">Failure sending mail: the transport failed to connect to the server.</span></span>|<span data-ttu-id="e0657-134">表示报表服务器未连接到邮件服务器；此消息来自电子邮件传递扩展插件。</span><span class="sxs-lookup"><span data-stu-id="e0657-134">Indicates that the report server did not connect to the mail server; this message is from the e-mail delivery extension.</span></span>|  
|<span data-ttu-id="e0657-135">文件 \<*filename*> 已写入 \<path> 。</span><span class="sxs-lookup"><span data-stu-id="e0657-135">File \<*filename*> was written to \<path>.</span></span>|<span data-ttu-id="e0657-136">表示已成功传递到文件共享位置；此消息来自文件共享传递扩展插件。</span><span class="sxs-lookup"><span data-stu-id="e0657-136">Indicates that the delivery to the file share location was successful; this message is from the file share delivery extension.</span></span>|  
|<span data-ttu-id="e0657-137">写入文件时出现未知错误。</span><span class="sxs-lookup"><span data-stu-id="e0657-137">An unknown error occurred when writing file.</span></span>|<span data-ttu-id="e0657-138">表示未能成功传递到文件共享位置；此消息来自文件共享传递扩展插件。</span><span class="sxs-lookup"><span data-stu-id="e0657-138">Indicates that the delivery to the file share location did not succeed; this message is from the file share delivery extension.</span></span>|  
|<span data-ttu-id="e0657-139">未能连接到目标文件夹 \<path> 。</span><span class="sxs-lookup"><span data-stu-id="e0657-139">Failure connecting to the destination folder, \<path>.</span></span> <span data-ttu-id="e0657-140">请验证目标文件夹或文件共享是否存在。</span><span class="sxs-lookup"><span data-stu-id="e0657-140">Verify the destination folder or file share exists.</span></span>|<span data-ttu-id="e0657-141">表示无法找到指定的文件夹；此消息来自文件共享传递扩展插件。</span><span class="sxs-lookup"><span data-stu-id="e0657-141">Indicates that the folder you specified could not be found; this message is from the file share delivery extension.</span></span>|  
|<span data-ttu-id="e0657-142">\<filename>未能写入文件 \<path> 。</span><span class="sxs-lookup"><span data-stu-id="e0657-142">The file \<filename> could not be written to \<path>.</span></span> <span data-ttu-id="e0657-143">请重试。</span><span class="sxs-lookup"><span data-stu-id="e0657-143">Attempting to retry.</span></span>|<span data-ttu-id="e0657-144">表示无法用新版本更新文件；此消息来自文件共享传递扩展插件。</span><span class="sxs-lookup"><span data-stu-id="e0657-144">Indicates that the file could not be updated with a newer version; this message is from the file share delivery extension.</span></span>|  
|<span data-ttu-id="e0657-145">写入文件时出错 \<filename> ：\<message></span><span class="sxs-lookup"><span data-stu-id="e0657-145">Failure writing file \<filename>: \<message></span></span>|<span data-ttu-id="e0657-146">表示未能成功传递到文件共享位置；此消息来自文件共享传递扩展插件。</span><span class="sxs-lookup"><span data-stu-id="e0657-146">Indicates that the delivery to the file share location did not succeed; this message is from the file share delivery extension.</span></span>|  
|\<custom status messages>|<span data-ttu-id="e0657-147">与传递成功和失败有关的状态消息，由传递扩展插件提供。</span><span class="sxs-lookup"><span data-stu-id="e0657-147">Status messages about delivery success and failure, provided by delivery extensions.</span></span> <span data-ttu-id="e0657-148">如果使用的是第三方传递扩展插件或自定义传递扩展插件，可能出现其他状态消息。</span><span class="sxs-lookup"><span data-stu-id="e0657-148">If you are using a third-party or custom delivery extension, additional status messages may be provided.</span></span>|  
  
 <span data-ttu-id="e0657-149">报表服务器管理员还可以监视当前处理的标准订阅。</span><span class="sxs-lookup"><span data-stu-id="e0657-149">Report server administrators can also monitor standard subscriptions that are currently processing.</span></span> <span data-ttu-id="e0657-150">但不能监视数据驱动订阅。</span><span class="sxs-lookup"><span data-stu-id="e0657-150">Data-driven subscriptions cannot be monitored.</span></span> <span data-ttu-id="e0657-151">有关详细信息，请参阅 [管理运行中的进程](manage-a-running-process.md)。</span><span class="sxs-lookup"><span data-stu-id="e0657-151">For more information, see [Manage a Running Process](manage-a-running-process.md).</span></span>  
  
 <span data-ttu-id="e0657-152">如果无法传递订阅（例如，如果邮件服务器不可用），传递扩展插件将重试传递。</span><span class="sxs-lookup"><span data-stu-id="e0657-152">If a subscription cannot be delivered (for example, if the mail server is unavailable), the delivery extension retries the delivery.</span></span> <span data-ttu-id="e0657-153">可以通过配置设置指定重试的次数。</span><span class="sxs-lookup"><span data-stu-id="e0657-153">A configuration setting specifies the number of attempts to make.</span></span> <span data-ttu-id="e0657-154">默认值为不重试。</span><span class="sxs-lookup"><span data-stu-id="e0657-154">The default value is no retries.</span></span> <span data-ttu-id="e0657-155">在某些情况下，处理的报表中可能未包含数据（例如，如果数据源处于脱机状态），这时消息正文中会有相关的内容说明这种情况。</span><span class="sxs-lookup"><span data-stu-id="e0657-155">In some cases, the report might have been processed without data (for example, if the data source is offline), in which case text to that effect is provided in the body of the message.</span></span>  
  
### <a name="native-mode-log-files"></a><span data-ttu-id="e0657-156">本机模式日志文件</span><span class="sxs-lookup"><span data-stu-id="e0657-156">Native Mode Log Files</span></span>  
 <span data-ttu-id="e0657-157">如果在传递过程中出现错误，将在报表服务器跟踪日志中记录一个条目。</span><span class="sxs-lookup"><span data-stu-id="e0657-157">If an error occurs during delivery, an entry is made in the report server trace log.</span></span>  
  
 <span data-ttu-id="e0657-158">报表服务器管理员可以查看**reportserverservice_ \* 日志**文件来确定订阅传递状态。</span><span class="sxs-lookup"><span data-stu-id="e0657-158">Report server administrators can review the **reportserverservice_\*.log** files to determine subscription delivery status.</span></span> <span data-ttu-id="e0657-159">对于电子邮件传递，报表服务器日志文件包括针对特定电子邮件帐户的处理和传递记录。</span><span class="sxs-lookup"><span data-stu-id="e0657-159">For e-mail delivery, report server log files include a record of processing and deliveries to specific e-mail accounts.</span></span> <span data-ttu-id="e0657-160">以下是日志文件的默认位置：</span><span class="sxs-lookup"><span data-stu-id="e0657-160">The following is the default location of the log files:</span></span>  
  
 `C:\Program Files\Microsoft SQL Server\MSRS11.MSSQLSERVER\Reporting Services\LogFiles`  
  
 <span data-ttu-id="e0657-161">以下是一个示例日志文件名：</span><span class="sxs-lookup"><span data-stu-id="e0657-161">The following is an example log filename:</span></span>  
  
 `ReportServerService__05_21_2014_00_05_07.log`  
  
 <span data-ttu-id="e0657-162">以下是与订阅相关的跟踪日志文件错误消息示例：</span><span class="sxs-lookup"><span data-stu-id="e0657-162">The following is a trace log file example error message related to subscriptions:</span></span>  
  
-   <span data-ttu-id="e0657-163">library!WindowsService_7!b60!05/20/2014-22:34:36:: i INFO: Initializing EnableExecutionLogging to 'True'  as specified in Server system properties.emailextension!WindowsService_7!b60!05/20/2014-22:34:41:: e ERROR: **Error sending email**.</span><span class="sxs-lookup"><span data-stu-id="e0657-163">library!WindowsService_7!b60!05/20/2014-22:34:36:: i INFO: Initializing EnableExecutionLogging to 'True'  as specified in Server system properties.emailextension!WindowsService_7!b60!05/20/2014-22:34:41:: e ERROR: **Error sending email**.</span></span> <span data-ttu-id="e0657-164">异常：System.Net.Mail.SmtpException:SMTP 服务器需要一个安全连接或客户端未经过身份验证。</span><span class="sxs-lookup"><span data-stu-id="e0657-164">Exception: System.Net.Mail.SmtpException: The SMTP server requires a secure connection or the client was not authenticated.</span></span> <span data-ttu-id="e0657-165">服务器响应为：5.7.1 Client was not authenticated   at System.Net.Mail.MailCommand.CheckResponse(SmtpStatusCode statusCode, String response)</span><span class="sxs-lookup"><span data-stu-id="e0657-165">The server response was: 5.7.1 Client was not authenticated   at System.Net.Mail.MailCommand.CheckResponse(SmtpStatusCode statusCode, String response)</span></span>  
  
 <span data-ttu-id="e0657-166">日志文件不包括有关是否打开报表或传递是否真正成功的信息。</span><span class="sxs-lookup"><span data-stu-id="e0657-166">The log file does not include information about whether the report was opened, or whether the delivery actually succeeded.</span></span> <span data-ttu-id="e0657-167">成功传递意味着计划和传递处理器未生成任何错误，并且报表服务器已连接到邮件服务器。</span><span class="sxs-lookup"><span data-stu-id="e0657-167">Successful delivery means that there were no errors generated by the Scheduling and Delivery Processor, and that the report server connected to the mail server.</span></span> <span data-ttu-id="e0657-168">如果电子邮件在用户邮箱中产生无法传递的消息错误，该信息不会包括在日志文件中。</span><span class="sxs-lookup"><span data-stu-id="e0657-168">If the e-mail resulted in an undeliverable message error in the user mailbox, that information will not be included in the log file.</span></span> <span data-ttu-id="e0657-169">有关日志文件的详细信息，请参阅 [Reporting Services 日志文件和源](../report-server/reporting-services-log-files-and-sources.md)。</span><span class="sxs-lookup"><span data-stu-id="e0657-169">For more information about log files, see [Reporting Services Log Files and Sources](../report-server/reporting-services-log-files-and-sources.md).</span></span>  
  
##  <a name="sharepoint-mode"></a><a name="bkmk_sharepoint_mode"></a><span data-ttu-id="e0657-170">SharePoint 模式</span><span class="sxs-lookup"><span data-stu-id="e0657-170">SharePoint Mode</span></span>  
 <span data-ttu-id="e0657-171">若要在 SharePoint 模式下监视订阅：可以从“管理订阅”  页面监视订阅状态。</span><span class="sxs-lookup"><span data-stu-id="e0657-171">To monitor a subscription in SharePoint mode: the subscription status can be monitored from the **Manage Subscriptions** page.</span></span>  
  
1.  <span data-ttu-id="e0657-172">浏览到包含该报表的文档库</span><span class="sxs-lookup"><span data-stu-id="e0657-172">browse to the document library that contains the report</span></span>  
  
2.  <span data-ttu-id="e0657-173">打开报表的上下文菜单 (…)  。</span><span class="sxs-lookup"><span data-stu-id="e0657-173">Open the context menu of the report (**...**).</span></span>  
  
3.  <span data-ttu-id="e0657-174">选择展开的菜单选项 (…)  。</span><span class="sxs-lookup"><span data-stu-id="e0657-174">Select the expanded menu option (**...**).</span></span>  
  
4.  <span data-ttu-id="e0657-175">选择 </span><span class="sxs-lookup"><span data-stu-id="e0657-175">Select **Manage Subscriptions**</span></span>  
  
### <a name="sharepoint-uls-log-files"></a><span data-ttu-id="e0657-176">SharePoint ULS 日志文件</span><span class="sxs-lookup"><span data-stu-id="e0657-176">SharePoint ULS Log files</span></span>  
 <span data-ttu-id="e0657-177">订阅相关信息被写入 SharePoint ULS 日志。</span><span class="sxs-lookup"><span data-stu-id="e0657-177">Subscription related information is written to the SharePoint ULS log.</span></span> <span data-ttu-id="e0657-178">有关为 ULS 日志配置 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 事件的详细信息，请参阅[为 SharePoint 跟踪日志 (ULS) 开启 Reporting Services 事件](../report-server/turn-on-reporting-services-events-for-the-sharepoint-trace-log-uls.md)。</span><span class="sxs-lookup"><span data-stu-id="e0657-178">For more information on configuring [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] events for the ULS log, see [Turn on Reporting Services events for the SharePoint trace log &#40;ULS&#41;](../report-server/turn-on-reporting-services-events-for-the-sharepoint-trace-log-uls.md).</span></span>  <span data-ttu-id="e0657-179">以下是一个与 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 订阅相关的 ULS 日志条目的示例。</span><span class="sxs-lookup"><span data-stu-id="e0657-179">The following is an example ULS log entry related to [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] subscriptions.</span></span>  
  
||||||||  
|-|-|-|-|-|-|-|  
|<span data-ttu-id="e0657-180">Date</span><span class="sxs-lookup"><span data-stu-id="e0657-180">Date</span></span>|<span data-ttu-id="e0657-181">进程</span><span class="sxs-lookup"><span data-stu-id="e0657-181">Process</span></span>|<span data-ttu-id="e0657-182">区域</span><span class="sxs-lookup"><span data-stu-id="e0657-182">Area</span></span>|<span data-ttu-id="e0657-183">类别</span><span class="sxs-lookup"><span data-stu-id="e0657-183">Category</span></span>|<span data-ttu-id="e0657-184">级别</span><span class="sxs-lookup"><span data-stu-id="e0657-184">Level</span></span>|<span data-ttu-id="e0657-185">Correlation</span><span class="sxs-lookup"><span data-stu-id="e0657-185">Correlation</span></span>|<span data-ttu-id="e0657-186">消息</span><span class="sxs-lookup"><span data-stu-id="e0657-186">Message</span></span>|  
|<span data-ttu-id="e0657-187">5/21/2014 14:34:06:15</span><span class="sxs-lookup"><span data-stu-id="e0657-187">5/21/2014 14:34:06:15</span></span>|<span data-ttu-id="e0657-188">应用池：a0ba039332294f40bc4a81544afde01d</span><span class="sxs-lookup"><span data-stu-id="e0657-188">App Pool: a0ba039332294f40bc4a81544afde01d</span></span>|<span data-ttu-id="e0657-189">SQL Server Reporting Services</span><span class="sxs-lookup"><span data-stu-id="e0657-189">SQL Server Reporting Services</span></span>|<span data-ttu-id="e0657-190">报表服务器电子邮件扩展插件</span><span class="sxs-lookup"><span data-stu-id="e0657-190">Report Server Email Extension</span></span>|<span data-ttu-id="e0657-191">意外</span><span class="sxs-lookup"><span data-stu-id="e0657-191">Unexpected</span></span>|<span data-ttu-id="e0657-192">(empty)</span><span class="sxs-lookup"><span data-stu-id="e0657-192">(empty)</span></span>|<span data-ttu-id="e0657-193">**发送邮件时出错。**</span><span class="sxs-lookup"><span data-stu-id="e0657-193">**Error sending email.**</span></span> <span data-ttu-id="e0657-194">异常：System.Net.Mail.SmtpException:邮箱不可用。</span><span class="sxs-lookup"><span data-stu-id="e0657-194">Exception: System.Net.Mail.SmtpException: Mailbox unavailable.</span></span> <span data-ttu-id="e0657-195">服务器响应为：5.7.1 Client does not have permissions to send as this sender  at System.Net.Mail.DataStopCommand.CheckResponse(SmtpStatusCode statusCode, String serverResponse)  at System.Net.Mail.DataStopCommand.Send(SmtpConnection conn)  at System.Net.Mail.SmtpClient.Send(MailMessage message)  at Microsoft.ReportingServices.EmailDeliveryProvider.EmailProvider.Deliver(Notification notification)</span><span class="sxs-lookup"><span data-stu-id="e0657-195">The server response was: 5.7.1 Client does not have permissions to send as this sender  at System.Net.Mail.DataStopCommand.CheckResponse(SmtpStatusCode statusCode, String serverResponse)  at System.Net.Mail.DataStopCommand.Send(SmtpConnection conn)  at System.Net.Mail.SmtpClient.Send(MailMessage message)  at Microsoft.ReportingServices.EmailDeliveryProvider.EmailProvider.Deliver(Notification notification)</span></span>|  
  
##  <a name="use-powershell-to-monitor-subscriptions"></a><a name="bkmk_use_powershell"></a> <span data-ttu-id="e0657-196">使用 PowerShell 监视订阅</span><span class="sxs-lookup"><span data-stu-id="e0657-196">Use PowerShell to monitor subscriptions</span></span>  
 <span data-ttu-id="e0657-197">如需查看可用于检查本机模式或 SharePoint 模式订阅的状态的 PowerShell 脚本的示例，请参见 [Use PowerShell to Change and List Reporting Services Subscription Owners and Run a Subscription](manage-subscription-owners-and-run-subscription-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="e0657-197">For example PowerShell scripts you can use to check the status of Native mode or SharePoint mode subscriptions, see [Use PowerShell to Change and List Reporting Services Subscription Owners and Run a Subscription](manage-subscription-owners-and-run-subscription-powershell.md).</span></span>  
  
##  <a name="managing-inactive-subscriptions"></a><a name="bkmk_manage_inactive"></a><span data-ttu-id="e0657-198">管理非活动订阅</span><span class="sxs-lookup"><span data-stu-id="e0657-198">Managing Inactive Subscriptions</span></span>  
 <span data-ttu-id="e0657-199">如果订阅处于不活动状态，则应将其删除，或者通过消除阻止对其进行处理的基本条件将其重新激活。</span><span class="sxs-lookup"><span data-stu-id="e0657-199">If a subscription becomes inactive, you should either delete it or reactivate it by resolving the underlying conditions that prevent it from being processed.</span></span> <span data-ttu-id="e0657-200">如果发生阻止处理订阅的条件，订阅会变为不活动状态。</span><span class="sxs-lookup"><span data-stu-id="e0657-200">Subscriptions can become inactive if conditions occur that prevent processing.</span></span> <span data-ttu-id="e0657-201">这些条件包括：</span><span class="sxs-lookup"><span data-stu-id="e0657-201">These conditions include:</span></span>  
  
-   <span data-ttu-id="e0657-202">删除或卸载订阅中指定的传递扩展插件。</span><span class="sxs-lookup"><span data-stu-id="e0657-202">Removing or uninstalling the delivery extension specified in the subscription.</span></span>  
  
-   <span data-ttu-id="e0657-203">将凭据设置从存储值更改为集成值或提示值。</span><span class="sxs-lookup"><span data-stu-id="e0657-203">Changing credential settings from stored to integrated or prompted values.</span></span>  
  
-   <span data-ttu-id="e0657-204">在报表定义中更改参数名称或数据类型，然后重新发布报表。</span><span class="sxs-lookup"><span data-stu-id="e0657-204">Changing a parameter name or data type in the report definition and then republishing a report.</span></span> <span data-ttu-id="e0657-205">如果订阅包括不再有效的参数，则订阅将变为不活动状态。</span><span class="sxs-lookup"><span data-stu-id="e0657-205">If a subscription includes a parameter that is no longer valid, the subscription becomes inactive.</span></span>  
  
-   <span data-ttu-id="e0657-206">更改报表的执行模式（例如，修改按需运行报表，使其作为报表执行快照运行）。</span><span class="sxs-lookup"><span data-stu-id="e0657-206">Changing the execution mode of a report (for example, modifying an on-demand report so that it runs as a report execution snapshot).</span></span> <span data-ttu-id="e0657-207">有关详细信息，请参阅 [设置报表处理属性](../report-server/set-report-processing-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="e0657-207">For more information, see [Set Report Processing Properties](../report-server/set-report-processing-properties.md).</span></span>  
  
 <span data-ttu-id="e0657-208">不活动的订阅由订阅本身所包含的消息来表示。</span><span class="sxs-lookup"><span data-stu-id="e0657-208">An inactive subscription is indicated by a message in the subscription itself.</span></span> <span data-ttu-id="e0657-209">该消息包括有关原因以及重新激活订阅所应采取的步骤的信息。</span><span class="sxs-lookup"><span data-stu-id="e0657-209">The message includes information about the cause and what steps you should take to reactivate the subscription.</span></span>  
  
 <span data-ttu-id="e0657-210">如果存在导致订阅变为不活动的条件，当报表服务器运行订阅时，订阅会反映此情况。</span><span class="sxs-lookup"><span data-stu-id="e0657-210">When conditions cause the subscription to become inactive, the subscription reflects this fact when the report server runs the subscription.</span></span> <span data-ttu-id="e0657-211">如果安排订阅在每周五早上 2:00 传递报表，而订阅使用的传递扩展插件在周一上午 9:00 被卸载，则订阅直到周五早上 2:00 才会反映其不活动状态。</span><span class="sxs-lookup"><span data-stu-id="e0657-211">If a subscription is scheduled to deliver a report every Friday at 2:00 A.M., and the delivery extension it uses was uninstalled on Monday at 9:00 A.M., the subscription will not reflect its inactive state until Friday at 2:00 A.M.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0657-212">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e0657-212">See Also</span></span>  
 <span data-ttu-id="e0657-213">[创建和管理本机模式报表服务器的订阅](../create-manage-subscriptions-native-mode-report-servers.md) </span><span class="sxs-lookup"><span data-stu-id="e0657-213">[Create and Manage Subscriptions for Native Mode Report Servers](../create-manage-subscriptions-native-mode-report-servers.md) </span></span>  
 [<span data-ttu-id="e0657-214">订阅和传递 (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="e0657-214">Subscriptions and Delivery &#40;Reporting Services&#41;</span></span>](subscriptions-and-delivery-reporting-services.md)  
  
  