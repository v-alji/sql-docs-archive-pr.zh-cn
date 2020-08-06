---
title: 服务器属性（“高级”页）- Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 10/18/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.serverproperties.advanced.f1
ms.assetid: 07b78a84-a6aa-4502-861d-349720ef790e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1834b1eb458ec718db23ad229a4ed6e04ae826c1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587714"
---
# <a name="server-properties-advanced-page---reporting-services"></a><span data-ttu-id="3ad89-102">服务器属性（“高级”页）- Reporting Services</span><span class="sxs-lookup"><span data-stu-id="3ad89-102">Server Properties (Advanced Page) - Reporting Services</span></span>
  <span data-ttu-id="3ad89-103">使用此页可以针对报表服务器设置系统属性。</span><span class="sxs-lookup"><span data-stu-id="3ad89-103">Use this page to set system properties on the report server.</span></span> <span data-ttu-id="3ad89-104">可通过多种方法来设置系统属性。</span><span class="sxs-lookup"><span data-stu-id="3ad89-104">There are a number of ways to set system properties.</span></span> <span data-ttu-id="3ad89-105">此工具提供了一个图形用户界面，您不必编写代码即可设置属性。</span><span class="sxs-lookup"><span data-stu-id="3ad89-105">This tool provides a graphical user interface so that you can set properties without having to write code.</span></span>  
  
 <span data-ttu-id="3ad89-106">若要打开此页，请启动 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]，连接到报表服务器实例，右键单击报表服务器名称，然后选择“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3ad89-106">To open this page, start [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to a report server instance, right-click the report server name, and select **Properties**.</span></span> <span data-ttu-id="3ad89-107">单击 **“高级”** 打开此页。</span><span class="sxs-lookup"><span data-stu-id="3ad89-107">Click **Advanced** to open this page.</span></span>  
  
## <a name="options"></a><span data-ttu-id="3ad89-108">选项</span><span class="sxs-lookup"><span data-stu-id="3ad89-108">Options</span></span>  
 <span data-ttu-id="3ad89-109">**EnableMyReports**</span><span class="sxs-lookup"><span data-stu-id="3ad89-109">**EnableMyReports**</span></span>  
 <span data-ttu-id="3ad89-110">指示是否启用“我的报表”功能。</span><span class="sxs-lookup"><span data-stu-id="3ad89-110">Indicates whether the My Reports feature is enabled.</span></span> <span data-ttu-id="3ad89-111">值为 `true` 表示已启用该功能。</span><span class="sxs-lookup"><span data-stu-id="3ad89-111">A value of `true` indicates that the feature is enabled.</span></span>  
  
 <span data-ttu-id="3ad89-112">**MyReportsRole**</span><span class="sxs-lookup"><span data-stu-id="3ad89-112">**MyReportsRole**</span></span>  
 <span data-ttu-id="3ad89-113">对用户的“我的报表”文件夹创建安全策略时所用角色的名称。</span><span class="sxs-lookup"><span data-stu-id="3ad89-113">The name of the role used when creating security policies on user's My Reports folders.</span></span> <span data-ttu-id="3ad89-114">默认值为 `My Reports Role`。</span><span class="sxs-lookup"><span data-stu-id="3ad89-114">The default value is `My Reports Role`.</span></span>  
  
 <span data-ttu-id="3ad89-115">**EnableClientPrinting**</span><span class="sxs-lookup"><span data-stu-id="3ad89-115">**EnableClientPrinting**</span></span>  
 <span data-ttu-id="3ad89-116">确定是否可从报表服务器下载 RSClientPrint ActiveX 控件。</span><span class="sxs-lookup"><span data-stu-id="3ad89-116">Determines whether the RSClientPrint ActiveX control is available for download from the report server.</span></span> <span data-ttu-id="3ad89-117">有效值为 `true` 和 `false` 。</span><span class="sxs-lookup"><span data-stu-id="3ad89-117">The valid values are `true` and `false`.</span></span> <span data-ttu-id="3ad89-118">默认值为 `true`。</span><span class="sxs-lookup"><span data-stu-id="3ad89-118">The default value is `true`.</span></span> <span data-ttu-id="3ad89-119">有关此控件所需的其他设置的详细信息，请参阅 [启用和禁用 Reporting Services 的客户端打印](../report-server/enable-and-disable-client-side-printing-for-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="3ad89-119">For more information about additional settings that are required for this control, see [Enable and Disable Client-Side Printing for Reporting Services](../report-server/enable-and-disable-client-side-printing-for-reporting-services.md).</span></span>  
  
 <span data-ttu-id="3ad89-120">**EnableExecutionLogging**</span><span class="sxs-lookup"><span data-stu-id="3ad89-120">**EnableExecutionLogging**</span></span>  
 <span data-ttu-id="3ad89-121">指示报表执行日志记录是否处于启用状态。</span><span class="sxs-lookup"><span data-stu-id="3ad89-121">Indicates whether report execution logging is enabled.</span></span> <span data-ttu-id="3ad89-122">默认值为 `true`。</span><span class="sxs-lookup"><span data-stu-id="3ad89-122">The default value is `true`.</span></span> <span data-ttu-id="3ad89-123">有关 Report Server 执行日志的详细信息，请参阅[报表服务器执行日志和 ExecutionLog3 视图](../report-server/report-server-executionlog-and-the-executionlog3-view.md)。</span><span class="sxs-lookup"><span data-stu-id="3ad89-123">For more information about the report server execution log, see [Report Server Execution Log and the ExecutionLog3 View](../report-server/report-server-executionlog-and-the-executionlog3-view.md).</span></span>  
  
 <span data-ttu-id="3ad89-124">**ExecutionLogDaysKept**</span><span class="sxs-lookup"><span data-stu-id="3ad89-124">**ExecutionLogDaysKept**</span></span>  
 <span data-ttu-id="3ad89-125">在执行日志中保留报表执行信息的天数。</span><span class="sxs-lookup"><span data-stu-id="3ad89-125">The number of days to keep report execution information in the execution log.</span></span> <span data-ttu-id="3ad89-126">此属性的有效值包括 `-1` 到 `2`、`147`、`483` 和 `647`。</span><span class="sxs-lookup"><span data-stu-id="3ad89-126">Valid values for this property include `-1` through `2`,`147`,`483`,`647`.</span></span> <span data-ttu-id="3ad89-127">如果值为 `-1`，则不从执行日志表中删除项。</span><span class="sxs-lookup"><span data-stu-id="3ad89-127">If the value is `-1` entries are not deleted from the Execution Log table.</span></span> <span data-ttu-id="3ad89-128">默认值为 `60`。</span><span class="sxs-lookup"><span data-stu-id="3ad89-128">The default value is `60`.</span></span>  
  
 <span data-ttu-id="3ad89-129">**SessionTimeout**</span><span class="sxs-lookup"><span data-stu-id="3ad89-129">**SessionTimeout**</span></span>  
 <span data-ttu-id="3ad89-130">会话保持活动状态的时间长度（以秒为单位）。</span><span class="sxs-lookup"><span data-stu-id="3ad89-130">The length of time, in seconds, that a session remains active.</span></span> <span data-ttu-id="3ad89-131">默认值为 `600`。</span><span class="sxs-lookup"><span data-stu-id="3ad89-131">The default value is `600`.</span></span>  
  
 <span data-ttu-id="3ad89-132">**SharePointIntegratedMode**</span><span class="sxs-lookup"><span data-stu-id="3ad89-132">**SharePointIntegratedMode**</span></span>  
 <span data-ttu-id="3ad89-133">这是一个指示服务器模式的只读属性。</span><span class="sxs-lookup"><span data-stu-id="3ad89-133">This is a read-only property that indicates the server mode.</span></span> <span data-ttu-id="3ad89-134">如果此值为 False，则报表服务器在本机模式下运行。</span><span class="sxs-lookup"><span data-stu-id="3ad89-134">If this value is False, the report server runs in native mode.</span></span>  
  
 <span data-ttu-id="3ad89-135">**SiteName**</span><span class="sxs-lookup"><span data-stu-id="3ad89-135">**SiteName**</span></span>  
 <span data-ttu-id="3ad89-136">在报表管理器的页面标题上显示的报表服务器站点的名称。</span><span class="sxs-lookup"><span data-stu-id="3ad89-136">The name of the report server site displayed in the page title of Report Manager.</span></span> <span data-ttu-id="3ad89-137">默认值为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3ad89-137">The default value is [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="3ad89-138">此属性可以是空字符串。</span><span class="sxs-lookup"><span data-stu-id="3ad89-138">This property can be an empty string.</span></span> <span data-ttu-id="3ad89-139">最大长度为 8,000 个字符。</span><span class="sxs-lookup"><span data-stu-id="3ad89-139">The maximum length is 8,000 characters.</span></span>  
  
 <span data-ttu-id="3ad89-140">**StoredParametersLifetime**</span><span class="sxs-lookup"><span data-stu-id="3ad89-140">**StoredParametersLifetime**</span></span>  
 <span data-ttu-id="3ad89-141">指定所存储的参数能够保存的最大天数。</span><span class="sxs-lookup"><span data-stu-id="3ad89-141">Specifies the maximum number of days that a stored parameter can be stored.</span></span> <span data-ttu-id="3ad89-142">有效值为 `-1` 以及 `+1` 到 `2,147,483,647`。</span><span class="sxs-lookup"><span data-stu-id="3ad89-142">Valid values are `-1`, `+1` through `2,147,483,647`.</span></span> <span data-ttu-id="3ad89-143">默认值为 `180` 天。</span><span class="sxs-lookup"><span data-stu-id="3ad89-143">The default value is `180` days.</span></span>  
  
 <span data-ttu-id="3ad89-144">**StoredParametersThreshold**</span><span class="sxs-lookup"><span data-stu-id="3ad89-144">**StoredParametersThreshold**</span></span>  
 <span data-ttu-id="3ad89-145">指定报表服务器可以存储的参数值的最大数目。</span><span class="sxs-lookup"><span data-stu-id="3ad89-145">Specifies the maximum number of parameter values that can be stored by the report server.</span></span> <span data-ttu-id="3ad89-146">有效值为 `-1` 以及 `+1` 到 `2,147,483,647`。</span><span class="sxs-lookup"><span data-stu-id="3ad89-146">Valid values are `-1`, `+1` through `2,147,483,647`.</span></span> <span data-ttu-id="3ad89-147">默认值为 `1500`。</span><span class="sxs-lookup"><span data-stu-id="3ad89-147">The default value is `1500`.</span></span>  
  
 <span data-ttu-id="3ad89-148">**UseSessionCookies**</span><span class="sxs-lookup"><span data-stu-id="3ad89-148">**UseSessionCookies**</span></span>  
 <span data-ttu-id="3ad89-149">指示报表服务器与客户端浏览器通信时是否应使用会话 cookie。</span><span class="sxs-lookup"><span data-stu-id="3ad89-149">Indicates whether the report server should use session cookies when communicating with client browsers.</span></span> <span data-ttu-id="3ad89-150">默认值为 `true`。</span><span class="sxs-lookup"><span data-stu-id="3ad89-150">The default value is `true`.</span></span>  
  
 <span data-ttu-id="3ad89-151">**ExternalImagesTimeout**</span><span class="sxs-lookup"><span data-stu-id="3ad89-151">**ExternalImagesTimeout**</span></span>  
 <span data-ttu-id="3ad89-152">确定在连接超时之前，必须检索外部图像文件的时间长度。默认值为 `600` 秒。</span><span class="sxs-lookup"><span data-stu-id="3ad89-152">Determines the length of time within which an external image file must be retrieved before the connection is timed out. The default is `600` seconds.</span></span>  
  
 <span data-ttu-id="3ad89-153">**SnapshotCompression**</span><span class="sxs-lookup"><span data-stu-id="3ad89-153">**SnapshotCompression**</span></span>  
 <span data-ttu-id="3ad89-154">定义如何压缩快照。</span><span class="sxs-lookup"><span data-stu-id="3ad89-154">Defines how snapshots are compressed.</span></span> <span data-ttu-id="3ad89-155">默认值为 `SQL`。</span><span class="sxs-lookup"><span data-stu-id="3ad89-155">The default value is `SQL`.</span></span> <span data-ttu-id="3ad89-156">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="3ad89-156">The valid values are as follows:</span></span>  
  
 <span data-ttu-id="3ad89-157">**SQL =** 在存储到报表服务器数据库中时压缩快照。</span><span class="sxs-lookup"><span data-stu-id="3ad89-157">**SQL =** Snapshots are compressed when stored in the report server database.</span></span> <span data-ttu-id="3ad89-158">这是当前的行为。</span><span class="sxs-lookup"><span data-stu-id="3ad89-158">This is the current behavior.</span></span>  
  
 <span data-ttu-id="3ad89-159">**None** = 不压缩快照。</span><span class="sxs-lookup"><span data-stu-id="3ad89-159">**None** = Snapshots are not compressed.</span></span>  
  
 <span data-ttu-id="3ad89-160">**All =** 针对所有的存储选项（包括报表服务器数据库或文件系统）压缩快照。</span><span class="sxs-lookup"><span data-stu-id="3ad89-160">**All =** Snapshots are compressed for all storage options, which include the report server database or the file system.</span></span>  
  
 <span data-ttu-id="3ad89-161">**SystemReportTimeout**</span><span class="sxs-lookup"><span data-stu-id="3ad89-161">**SystemReportTimeout**</span></span>  
 <span data-ttu-id="3ad89-162">在报表服务器命名空间中托管的所有报表的默认报表处理超时值（以秒为单位）。</span><span class="sxs-lookup"><span data-stu-id="3ad89-162">The default report processing timeout value, in seconds, for all reports managed in the report server namespace.</span></span> <span data-ttu-id="3ad89-163">该值可在报表级别进行重写。</span><span class="sxs-lookup"><span data-stu-id="3ad89-163">This value can be overridden at the report level.</span></span> <span data-ttu-id="3ad89-164">如果设置了此属性，则超过指定时间后报表服务器会尝试停止处理报表。</span><span class="sxs-lookup"><span data-stu-id="3ad89-164">If this property is set, the report server attempts to stop the processing of a report when the specified time has expired.</span></span> <span data-ttu-id="3ad89-165">有效值为 `-1` 到 `2`、`147`、`483`、`647`。</span><span class="sxs-lookup"><span data-stu-id="3ad89-165">Valid values are `-1` through `2`,`147`,`483`,`647`.</span></span> <span data-ttu-id="3ad89-166">如果值为 `-1`，则处理期间命名空间中的报表不会超时。</span><span class="sxs-lookup"><span data-stu-id="3ad89-166">If the value is `-1`, reports in the namespace do not time out during processing.</span></span> <span data-ttu-id="3ad89-167">默认值为 `1800`。</span><span class="sxs-lookup"><span data-stu-id="3ad89-167">The default value is `1800`.</span></span>  
  
 <span data-ttu-id="3ad89-168">**SystemSnapshotLimit**</span><span class="sxs-lookup"><span data-stu-id="3ad89-168">**SystemSnapshotLimit**</span></span>  
 <span data-ttu-id="3ad89-169">为报表存储的快照的最大数目。</span><span class="sxs-lookup"><span data-stu-id="3ad89-169">The maximum number of snapshots that are stored for a report.</span></span> <span data-ttu-id="3ad89-170">有效值为 `-1` 到 `2`、`147`、`483`、`647`。</span><span class="sxs-lookup"><span data-stu-id="3ad89-170">Valid values are `-1` through `2`,`147`,`483`,`647`.</span></span> <span data-ttu-id="3ad89-171">如果值为 `-1`，则无快照限制。</span><span class="sxs-lookup"><span data-stu-id="3ad89-171">If the value is `-1`, there is no snapshot limit.</span></span>  
  
 <span data-ttu-id="3ad89-172">**EnableIntegratedSecurity**</span><span class="sxs-lookup"><span data-stu-id="3ad89-172">**EnableIntegratedSecurity**</span></span>  
 <span data-ttu-id="3ad89-173">确定报表数据源连接是否支持 Windows 集成安全性。</span><span class="sxs-lookup"><span data-stu-id="3ad89-173">Determines whether Windows integrated security is supported for report data source connections.</span></span> <span data-ttu-id="3ad89-174">默认值为 `True`。</span><span class="sxs-lookup"><span data-stu-id="3ad89-174">The default is `True`.</span></span> <span data-ttu-id="3ad89-175">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="3ad89-175">The valid values are as follows:</span></span>  
  
 <span data-ttu-id="3ad89-176">`True` = 启用 Windows 集成安全性。</span><span class="sxs-lookup"><span data-stu-id="3ad89-176">`True` = Windows integrated security is enabled.</span></span>  
  
 <span data-ttu-id="3ad89-177">`False` = 未启用 Windows 集成安全性。</span><span class="sxs-lookup"><span data-stu-id="3ad89-177">`False` = Windows integrated security is not enabled.</span></span> <span data-ttu-id="3ad89-178">将不运行配置为使用 Windows 集成安全性的报表数据源。</span><span class="sxs-lookup"><span data-stu-id="3ad89-178">Report data sources that are configured to use Windows integrated security will not run.</span></span>  
  
 `EnableLoadReportDefinition`  
 <span data-ttu-id="3ad89-179">选中此选项可以指定用户是否可以从报表生成器报表中执行特别报告执行。</span><span class="sxs-lookup"><span data-stu-id="3ad89-179">Select this option to specify whether users can perform ad hoc report execution from a Report Builder report.</span></span> <span data-ttu-id="3ad89-180">设置此选项即可确定报表服务器的 `EnableLoadReportDefinition` 属性值。</span><span class="sxs-lookup"><span data-stu-id="3ad89-180">Setting this option determines the value of the `EnableLoadReportDefinition` property on the report server.</span></span>  
  
 <span data-ttu-id="3ad89-181">如果清除此选项，则属性将设置为 False，报表服务器将不会为使用报表模型作为数据源的报表生成点击链接型报表。</span><span class="sxs-lookup"><span data-stu-id="3ad89-181">If you clear this option, the property will be set to False and report server will not generate clickthrough reports for reports that use a report model as a data source.</span></span> <span data-ttu-id="3ad89-182">将阻止对 LoadReportDefinition 方法的任何调用。</span><span class="sxs-lookup"><span data-stu-id="3ad89-182">Any calls to the LoadReportDefinition method will be blocked.</span></span>  
  
 <span data-ttu-id="3ad89-183">如果关闭此选项，则会缓解恶意用户通过用 LoadReportDefinition 请求使报表服务器重载来启动拒绝服务攻击的威胁。</span><span class="sxs-lookup"><span data-stu-id="3ad89-183">Turning off this option mitigates a threat whereby a malicious user launches a denial of service attack by overloading the report server with LoadReportDefinition requests.</span></span>  
  
 <span data-ttu-id="3ad89-184">**EnableRemoteErrors**</span><span class="sxs-lookup"><span data-stu-id="3ad89-184">**EnableRemoteErrors**</span></span>  
 <span data-ttu-id="3ad89-185">包括外部错误信息（例如，有关报表数据源的错误信息），其中包含针对从远程计算机请求报表的用户返回的错误消息。</span><span class="sxs-lookup"><span data-stu-id="3ad89-185">Includes external error information (for example, error information about report data sources) with the error messages that are returned for users who request reports from remote computers.</span></span> <span data-ttu-id="3ad89-186">有效值为 `true` 和 `false`。</span><span class="sxs-lookup"><span data-stu-id="3ad89-186">Valid values are `true` and `false`.</span></span> <span data-ttu-id="3ad89-187">默认值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="3ad89-187">The default value is `false`.</span></span> <span data-ttu-id="3ad89-188">有关详细信息，请参阅[启用远程错误 (Reporting Services)](../report-server/enable-remote-errors-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="3ad89-188">For more information, see [Enable Remote Errors &#40;Reporting Services&#41;](../report-server/enable-remote-errors-reporting-services.md).</span></span>  
  
 <span data-ttu-id="3ad89-189">**EnableReportDesignClientDownload**</span><span class="sxs-lookup"><span data-stu-id="3ad89-189">**EnableReportDesignClientDownload**</span></span>  
 <span data-ttu-id="3ad89-190">指定是否可以从报表服务器下载报表生成器安装包。</span><span class="sxs-lookup"><span data-stu-id="3ad89-190">Specifies whether Report Builder installation package can be downloaded from the report server.</span></span> <span data-ttu-id="3ad89-191">如果清除此设置，则指向报表生成器的 URL 将不起作用。</span><span class="sxs-lookup"><span data-stu-id="3ad89-191">If you clear this setting, the URL to Report Builder will not work.</span></span> <span data-ttu-id="3ad89-192">有关详细信息，请参阅 [配置报表生成器访问权限](../report-server/configure-report-builder-access.md)。</span><span class="sxs-lookup"><span data-stu-id="3ad89-192">For more information, see [Configure Report Builder Access](../report-server/configure-report-builder-access.md).</span></span>  
  
 <span data-ttu-id="3ad89-193">**EditSessionCacheLimit**</span><span class="sxs-lookup"><span data-stu-id="3ad89-193">**EditSessionCacheLimit**</span></span>  
 <span data-ttu-id="3ad89-194">指定可在一个报表编辑会话中处于活动状态的数据缓存条目数。</span><span class="sxs-lookup"><span data-stu-id="3ad89-194">Specifies the number of data cache entries that can be active in a report edit session.</span></span> <span data-ttu-id="3ad89-195">默认数量为 5。</span><span class="sxs-lookup"><span data-stu-id="3ad89-195">The default number is 5.</span></span>  
  
 <span data-ttu-id="3ad89-196">**EditSessionTimeout**</span><span class="sxs-lookup"><span data-stu-id="3ad89-196">**EditSessionTimeout**</span></span>  
 <span data-ttu-id="3ad89-197">指定报表编辑会话超时之前的秒数。默认值为7200秒 (2 小时) 。</span><span class="sxs-lookup"><span data-stu-id="3ad89-197">Specifies the number of seconds until a report edit session times out. The default value is 7200 seconds (2 hours).</span></span>  
  
 <span data-ttu-id="3ad89-198">**EnableTestConnectionDetailedErrors**</span><span class="sxs-lookup"><span data-stu-id="3ad89-198">**EnableTestConnectionDetailedErrors**</span></span>  
 <span data-ttu-id="3ad89-199">指示当用户使用报表服务器测试数据源连接时，是否向客户端计算机发送详细的错误消息。</span><span class="sxs-lookup"><span data-stu-id="3ad89-199">Indicates whether detailed error messages are sent to the client computer when users test data source connections using the report server.</span></span> <span data-ttu-id="3ad89-200">默认值为 `true`。</span><span class="sxs-lookup"><span data-stu-id="3ad89-200">The default value is `true`.</span></span> <span data-ttu-id="3ad89-201">如果此选项设置为 `false`，则只发送一般错误消息。</span><span class="sxs-lookup"><span data-stu-id="3ad89-201">If the option is set to `false`, only generic error messages are sent.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ad89-202">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3ad89-202">See Also</span></span>  
 <span data-ttu-id="3ad89-203">[设置报表服务器属性 &#40;Management Studio&#41;](set-report-server-properties-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="3ad89-203">[Set Report Server Properties &#40;Management Studio&#41;](set-report-server-properties-management-studio.md) </span></span>  
 <span data-ttu-id="3ad89-204">[在 Management Studio 中连接到报表服务器](connect-to-a-report-server-in-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="3ad89-204">[Connect to a Report Server in Management Studio](connect-to-a-report-server-in-management-studio.md) </span></span>  
 <span data-ttu-id="3ad89-205">[Reporting Services 属性](../report-server-web-service/net-framework/reporting-services-properties.md) </span><span class="sxs-lookup"><span data-stu-id="3ad89-205">[Reporting Services Properties](../report-server-web-service/net-framework/reporting-services-properties.md) </span></span>  
 <span data-ttu-id="3ad89-206">[Management Studio F1 帮助中的报表服务器](report-server-in-management-studio-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="3ad89-206">[Report Server in Management Studio F1 Help](report-server-in-management-studio-f1-help.md) </span></span>  
 <span data-ttu-id="3ad89-207">[报表服务器系统属性](../report-server-web-service/net-framework/reporting-services-properties-report-server-system-properties.md) </span><span class="sxs-lookup"><span data-stu-id="3ad89-207">[Report Server System Properties](../report-server-web-service/net-framework/reporting-services-properties-report-server-system-properties.md) </span></span>  
 <span data-ttu-id="3ad89-208">[为部署和管理任务编写脚本](script-deployment-and-administrative-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="3ad89-208">[Script Deployment and Administrative Tasks](script-deployment-and-administrative-tasks.md) </span></span>  
 [<span data-ttu-id="3ad89-209">启用和禁用“我的报表”</span><span class="sxs-lookup"><span data-stu-id="3ad89-209">Enable and Disable My Reports</span></span>](../report-server/enable-and-disable-my-reports.md)  
  
  
