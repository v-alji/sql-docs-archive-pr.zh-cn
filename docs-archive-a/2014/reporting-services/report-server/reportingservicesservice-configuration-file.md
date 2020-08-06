---
title: ReportingServicesService 配置文件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- traces [Reporting Services]
- Report Server Windows service, ReportingServicesService configuration file
- ReportingServicesService configuration file
ms.assetid: 40f4a401-cb61-4c42-b1ec-01acdacdacd1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5124631db9635211827dd3b1abbff7116101a61d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587186"
---
# <a name="reportingservicesservice-configuration-file"></a><span data-ttu-id="3bbe5-102">ReportingServicesService 配置文件</span><span class="sxs-lookup"><span data-stu-id="3bbe5-102">ReportingServicesService Configuration File</span></span>
  <span data-ttu-id="3bbe5-103">ReportingServicesService.exe.config 文件包含配置跟踪的设置信息。</span><span class="sxs-lookup"><span data-stu-id="3bbe5-103">The ReportingServicesService.exe.config file includes settings that configure tracing.</span></span>  
  
## <a name="file-location"></a><span data-ttu-id="3bbe5-104">文件位置</span><span class="sxs-lookup"><span data-stu-id="3bbe5-104">File Location</span></span>  
 <span data-ttu-id="3bbe5-105">此文件位于 \Reporting Services\Report Server\Bin 文件夹。</span><span class="sxs-lookup"><span data-stu-id="3bbe5-105">This file is located in the \Reporting Services\Report Server\Bin folder.</span></span>  
  
## <a name="editing-guidelines"></a><span data-ttu-id="3bbe5-106">编辑指南</span><span class="sxs-lookup"><span data-stu-id="3bbe5-106">Editing Guidelines</span></span>  
 <span data-ttu-id="3bbe5-107">您可以对此文件进行修改，重命名日志文件或提高/降低跟踪级别。</span><span class="sxs-lookup"><span data-stu-id="3bbe5-107">You can modify this file to rename the log file or to increase or decrease trace levels.</span></span> <span data-ttu-id="3bbe5-108">请不要修改任何其他设置。</span><span class="sxs-lookup"><span data-stu-id="3bbe5-108">Do not modify any of the other settings.</span></span> <span data-ttu-id="3bbe5-109">有关说明，请参阅[修改 Reporting Services 配置文件 (RSreportserver.config)](modify-a-reporting-services-configuration-file-rsreportserver-config.md)。</span><span class="sxs-lookup"><span data-stu-id="3bbe5-109">For instructions, see [Modify a Reporting Services Configuration File &#40;RSreportserver.config&#41;](modify-a-reporting-services-configuration-file-rsreportserver-config.md).</span></span> <span data-ttu-id="3bbe5-110">有关跟踪日志的详细信息，请参阅 [报表服务器服务跟踪日志](report-server-service-trace-log.md)。</span><span class="sxs-lookup"><span data-stu-id="3bbe5-110">For more information about trace logs, see [Report Server Service Trace Log](report-server-service-trace-log.md).</span></span>  
  
## <a name="example-configuration"></a><span data-ttu-id="3bbe5-111">示例配置</span><span class="sxs-lookup"><span data-stu-id="3bbe5-111">Example Configuration</span></span>  
 <span data-ttu-id="3bbe5-112">下面的示例显示了 ReportingServicesService.exe.config 文件中的设置和默认值。</span><span class="sxs-lookup"><span data-stu-id="3bbe5-112">The following example shows the settings and default values found in the ReportingServicesService.exe.config file.</span></span>  
  
```  
<configSections>  
      <section name="RStrace" type="Microsoft.ReportingServices.Diagnostics.RSTraceSectionHandler,Microsoft.ReportingServices.Diagnostics" />  
</configSections>  
<system.diagnostics>  
      <switches>  
          <add name="DefaultTraceSwitch" value="3" />  
      </switches>  
</system.diagnostics>  
<RStrace>  
      <add name="FileName" value="ReportServerService_" />  
      <add name="FileSizeLimitMb" value="32" />  
      <add name="KeepFilesForDays" value="14" />  
      <add name="Prefix" value="tid, time" />  
      <add name="TraceListeners" value="debugwindow, file" />  
      <add name="TraceFileMode" value="unique" />  
      <add name="Components" value="all" />  
</RStrace>  
<runtime>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
             <dependentAssembly>  
                    <assemblyIdentity name="Microsoft.ReportingServices.Interfaces"  
                        publicKeyToken="89845dcd8080cc91"  
                        culture="neutral" />  
                    <bindingRedirect oldVersion="8.0.242.0"  
                                     newVersion="10.0.0.0"/>  
                    <bindingRedirect oldVersion="9.0.242.0"  
                                     newVersion="10.0.0.0"/>  
             </dependentAssembly>  
      </assemblyBinding>  
      <gcServer enabled="true" />  
</runtime>  
```  
  
## <a name="configuration-settings"></a><span data-ttu-id="3bbe5-113">配置设置</span><span class="sxs-lookup"><span data-stu-id="3bbe5-113">Configuration Settings</span></span>  
 <span data-ttu-id="3bbe5-114">下表提供了有关具体设置的信息，</span><span class="sxs-lookup"><span data-stu-id="3bbe5-114">The following table provides information about specific settings.</span></span> <span data-ttu-id="3bbe5-115">将按设置在配置文件中的显示顺序依次列出：</span><span class="sxs-lookup"><span data-stu-id="3bbe5-115">Settings are presented in the order in which they appear in the configuration file.</span></span>  
  
|<span data-ttu-id="3bbe5-116">设置</span><span class="sxs-lookup"><span data-stu-id="3bbe5-116">Setting</span></span>|<span data-ttu-id="3bbe5-117">说明</span><span class="sxs-lookup"><span data-stu-id="3bbe5-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3bbe5-118">**RStrace**</span><span class="sxs-lookup"><span data-stu-id="3bbe5-118">**RStrace**</span></span>|<span data-ttu-id="3bbe5-119">指定用于错误和跟踪的命名空间。</span><span class="sxs-lookup"><span data-stu-id="3bbe5-119">Specifies namespaces used for errors and tracing.</span></span>|  
|<span data-ttu-id="3bbe5-120">**DefaultTraceSwitch**</span><span class="sxs-lookup"><span data-stu-id="3bbe5-120">**DefaultTraceSwitch**</span></span>|<span data-ttu-id="3bbe5-121">指定向 ReportServerService 跟踪日志报告的信息的级别。</span><span class="sxs-lookup"><span data-stu-id="3bbe5-121">Specifies the level of information that is reported to the ReportServerService trace log.</span></span> <span data-ttu-id="3bbe5-122">每个级别都包含所有更低级别（用更小的数字表示）报告的信息。</span><span class="sxs-lookup"><span data-stu-id="3bbe5-122">Each level includes the information reported by all lower-numbered levels.</span></span> <span data-ttu-id="3bbe5-123">建议您不要禁用跟踪。</span><span class="sxs-lookup"><span data-stu-id="3bbe5-123">Disabling tracing is not recommended.</span></span> <span data-ttu-id="3bbe5-124">有效值包括：</span><span class="sxs-lookup"><span data-stu-id="3bbe5-124">Valid values include:</span></span><br /><br /> <span data-ttu-id="3bbe5-125">0= 禁用跟踪</span><span class="sxs-lookup"><span data-stu-id="3bbe5-125">0= Disables tracing</span></span><br /><br /> <span data-ttu-id="3bbe5-126">1= 异常和重新启动</span><span class="sxs-lookup"><span data-stu-id="3bbe5-126">1= Exceptions and restarts</span></span><br /><br /> <span data-ttu-id="3bbe5-127">2= 异常、重新启动、警告</span><span class="sxs-lookup"><span data-stu-id="3bbe5-127">2= Exceptions, restarts, warnings</span></span><br /><br /> <span data-ttu-id="3bbe5-128">3= 异常、重新启动、警告、状态消息（默认值）</span><span class="sxs-lookup"><span data-stu-id="3bbe5-128">3= Exceptions, restarts, warnings, status messages (default)</span></span><br /><br /> <span data-ttu-id="3bbe5-129">4= 详细模式</span><span class="sxs-lookup"><span data-stu-id="3bbe5-129">4= Verbose mode</span></span>|  
|<span data-ttu-id="3bbe5-130">**FileName**</span><span class="sxs-lookup"><span data-stu-id="3bbe5-130">**FileName**</span></span>|<span data-ttu-id="3bbe5-131">指定日志文件名的第一部分。</span><span class="sxs-lookup"><span data-stu-id="3bbe5-131">Specifies the first portion of the log file name.</span></span> <span data-ttu-id="3bbe5-132">日志文件名的其余部分由 `Prefix` 指定的值完成。</span><span class="sxs-lookup"><span data-stu-id="3bbe5-132">The value specified by `Prefix` completes the rest of the name.</span></span> <span data-ttu-id="3bbe5-133">默认情况下，名称为 ReportServerService_。</span><span class="sxs-lookup"><span data-stu-id="3bbe5-133">By default, the name is ReportServerService_.</span></span>|  
|<span data-ttu-id="3bbe5-134">**FileSizeLimitMb**</span><span class="sxs-lookup"><span data-stu-id="3bbe5-134">**FileSizeLimitMb**</span></span>|<span data-ttu-id="3bbe5-135">指定跟踪日志大小的上限。</span><span class="sxs-lookup"><span data-stu-id="3bbe5-135">Specifies an upper limit on trace log size.</span></span> <span data-ttu-id="3bbe5-136">文件大小的单位为 MB。</span><span class="sxs-lookup"><span data-stu-id="3bbe5-136">The file is measured in megabytes.</span></span> <span data-ttu-id="3bbe5-137">有效值介于 0 到最大整数之间。</span><span class="sxs-lookup"><span data-stu-id="3bbe5-137">Valid values are 0 to a maximum integer.</span></span> <span data-ttu-id="3bbe5-138">默认值为 32。</span><span class="sxs-lookup"><span data-stu-id="3bbe5-138">The default value is 32.</span></span>|  
|<span data-ttu-id="3bbe5-139">**KeepFilesForDays**</span><span class="sxs-lookup"><span data-stu-id="3bbe5-139">**KeepFilesForDays**</span></span>|<span data-ttu-id="3bbe5-140">指定多少天后删除跟踪日志文件。</span><span class="sxs-lookup"><span data-stu-id="3bbe5-140">Specifies the number of days after which a trace log file will be deleted.</span></span> <span data-ttu-id="3bbe5-141">有效值介于 0 到最大整数之间。</span><span class="sxs-lookup"><span data-stu-id="3bbe5-141">Valid values are 0 to a maximum integer.</span></span> <span data-ttu-id="3bbe5-142">默认值为 14。</span><span class="sxs-lookup"><span data-stu-id="3bbe5-142">The default value is 14.</span></span>|  
|`Prefix`|<span data-ttu-id="3bbe5-143">指定一个生成的值，该值可将日志实例彼此区分开。</span><span class="sxs-lookup"><span data-stu-id="3bbe5-143">Specifies a generated value that distinguishes one log instance from another.</span></span> <span data-ttu-id="3bbe5-144">默认情况下，跟踪日志文件名后面将附加时间戳值。</span><span class="sxs-lookup"><span data-stu-id="3bbe5-144">By default, timestamp values are appended to trace log file names.</span></span> <span data-ttu-id="3bbe5-145">此值设置为“ tid, time ”。</span><span class="sxs-lookup"><span data-stu-id="3bbe5-145">This value is set to " tid, time ".</span></span> <span data-ttu-id="3bbe5-146">请不要修改此设置。</span><span class="sxs-lookup"><span data-stu-id="3bbe5-146">Do not modify this setting.</span></span>|  
|<span data-ttu-id="3bbe5-147">**TraceListeners**</span><span class="sxs-lookup"><span data-stu-id="3bbe5-147">**TraceListeners**</span></span>|<span data-ttu-id="3bbe5-148">指定输出跟踪日志内容的目标。</span><span class="sxs-lookup"><span data-stu-id="3bbe5-148">Specifies a target for outputting trace log content.</span></span> <span data-ttu-id="3bbe5-149">您可以通过使用逗号进行分隔来指定多个目标。</span><span class="sxs-lookup"><span data-stu-id="3bbe5-149">You can specify multiple targets using a comma to separate each one.</span></span> <span data-ttu-id="3bbe5-150">有效值包括：</span><span class="sxs-lookup"><span data-stu-id="3bbe5-150">Valid values include:</span></span><br /><br /> <span data-ttu-id="3bbe5-151">DebugWindow（默认值）</span><span class="sxs-lookup"><span data-stu-id="3bbe5-151">DebugWindow (default)</span></span><br /><br /> <span data-ttu-id="3bbe5-152">File（默认值）</span><span class="sxs-lookup"><span data-stu-id="3bbe5-152">File (default)</span></span><br /><br /> <span data-ttu-id="3bbe5-153">StdOut</span><span class="sxs-lookup"><span data-stu-id="3bbe5-153">StdOut</span></span>|  
|<span data-ttu-id="3bbe5-154">**TraceFileMode**</span><span class="sxs-lookup"><span data-stu-id="3bbe5-154">**TraceFileMode**</span></span>|<span data-ttu-id="3bbe5-155">指定跟踪日志是否包含 24 小时时段内的数据。</span><span class="sxs-lookup"><span data-stu-id="3bbe5-155">Specifies whether trace logs contain data for a 24-hour period.</span></span> <span data-ttu-id="3bbe5-156">每天应当为每个组件设置唯一的跟踪日志。</span><span class="sxs-lookup"><span data-stu-id="3bbe5-156">You should have one unique trace log for each component on each day.</span></span> <span data-ttu-id="3bbe5-157">此值设置为“Unique”（默认值）。</span><span class="sxs-lookup"><span data-stu-id="3bbe5-157">This value is set to "Unique (default)".</span></span> <span data-ttu-id="3bbe5-158">不要修改此值。</span><span class="sxs-lookup"><span data-stu-id="3bbe5-158">Do not modify this value.</span></span>|  
|<span data-ttu-id="3bbe5-159">**组件**</span><span class="sxs-lookup"><span data-stu-id="3bbe5-159">**Components**</span></span>|<span data-ttu-id="3bbe5-160">指定为其创建跟踪日志的组件。</span><span class="sxs-lookup"><span data-stu-id="3bbe5-160">Specifies the components for which trace logs are created.</span></span> <span data-ttu-id="3bbe5-161">默认值为 `all`。</span><span class="sxs-lookup"><span data-stu-id="3bbe5-161">The default value is `all`.</span></span> <span data-ttu-id="3bbe5-162">此设置的其他有效值包括内部组件名。</span><span class="sxs-lookup"><span data-stu-id="3bbe5-162">Other valid values for this setting include the names of internal components.</span></span> <span data-ttu-id="3bbe5-163">不要修改此值。</span><span class="sxs-lookup"><span data-stu-id="3bbe5-163">Do not modify this value.</span></span>|  
|<span data-ttu-id="3bbe5-164">**时会**</span><span class="sxs-lookup"><span data-stu-id="3bbe5-164">**Runtime**</span></span>|<span data-ttu-id="3bbe5-165">指定支持与早期版本的向后兼容性的配置设置。</span><span class="sxs-lookup"><span data-stu-id="3bbe5-165">Specifies configuration settings that support backward compatibility with the previous version.</span></span> <span data-ttu-id="3bbe5-166">运行时设置用于将指向早期版本的 Microsoft.ReportingServices.Interfaces 的请求重定向到新版本。</span><span class="sxs-lookup"><span data-stu-id="3bbe5-166">Runtime settings are used to redirect requests that target the previous version of Microsoft.ReportingServices.Interfaces to the new version.</span></span><br /><br /> <span data-ttu-id="3bbe5-167">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 产品文档对本节中的所有配置设置都进行了说明。</span><span class="sxs-lookup"><span data-stu-id="3bbe5-167">All of the configuration settings in this section are described in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] product documentation.</span></span> <span data-ttu-id="3bbe5-168">有关详细信息，请在 MSDN 网站上或在 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 文档中搜索“运行时架构设置”。</span><span class="sxs-lookup"><span data-stu-id="3bbe5-168">For more information, search for "Runtime Schema Settings" on the MSDN Web site or in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] documentation.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3bbe5-169">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3bbe5-169">See Also</span></span>  
 <span data-ttu-id="3bbe5-170">[Reporting Services 配置文件](reporting-services-configuration-files.md) </span><span class="sxs-lookup"><span data-stu-id="3bbe5-170">[Reporting Services Configuration Files](reporting-services-configuration-files.md) </span></span>  
 [<span data-ttu-id="3bbe5-171">报表服务器服务跟踪日志</span><span class="sxs-lookup"><span data-stu-id="3bbe5-171">Report Server Service Trace Log</span></span>](report-server-service-trace-log.md)  
  
  
