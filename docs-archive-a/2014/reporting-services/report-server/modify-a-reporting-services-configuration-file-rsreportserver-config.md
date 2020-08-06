---
title: 修改 Reporting Services 配置文件 (RSreportserver.config) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 958ef51f-2699-4cb2-a92e-3b4322e36a30
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 75ff276a0ba43cb89393466bf40a71b7acd21368
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586341"
---
# <a name="modify-a-reporting-services-configuration-file-rsreportserverconfig"></a><span data-ttu-id="26a76-102">修改 Reporting Services 配置文件 (RSreportserver.config)</span><span class="sxs-lookup"><span data-stu-id="26a76-102">Modify a Reporting Services Configuration File (RSreportserver.config)</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="26a76-103">将应用程序设置存储在一组配置文件中。</span><span class="sxs-lookup"><span data-stu-id="26a76-103">stores application settings in a set of configuration files.</span></span> <span data-ttu-id="26a76-104">安装程序会为您安装的每个报表服务器实例创建配置文件。</span><span class="sxs-lookup"><span data-stu-id="26a76-104">Setup creates the configuration files for each report server instance you install.</span></span> <span data-ttu-id="26a76-105">每个文件中的值要么在安装过程中设置，要么在您使用工具和应用程序将服务器配置为执行某个操作时设置。</span><span class="sxs-lookup"><span data-stu-id="26a76-105">Within each file, values are either set during installation or when you use tools and applications to configure a server for operation.</span></span> <span data-ttu-id="26a76-106">在某些情况下，必须直接修改文件来添加或配置高级设置。</span><span class="sxs-lookup"><span data-stu-id="26a76-106">In some cases, you must modify a file directly to add or configure advanced settings.</span></span> <span data-ttu-id="26a76-107">将配置设置指定为 XML 元素或属性。</span><span class="sxs-lookup"><span data-stu-id="26a76-107">Configuration settings are specified as either XML elements or attributes.</span></span> <span data-ttu-id="26a76-108">如果您了解 XML 和配置文件，则可以使用文本编辑器或代码编辑器来修改可以由用户定义的设置。</span><span class="sxs-lookup"><span data-stu-id="26a76-108">If you understand XML and configuration files, you can use a text or code editor to modify user-definable settings.</span></span>  
  
 <span data-ttu-id="26a76-109">某些配置设置只能通过工具来设置。</span><span class="sxs-lookup"><span data-stu-id="26a76-109">Some configuration settings can be set only through a tool.</span></span> <span data-ttu-id="26a76-110">包含加密值的设置必须通过 Reporting Services 配置工具、安装程序或 **rsconfig** 命令行实用工具来修改。</span><span class="sxs-lookup"><span data-stu-id="26a76-110">Settings that contain encrypted values must be modified through the Reporting Services Configuration tool, the Setup program, or the **rsconfig** command line utility.</span></span> <span data-ttu-id="26a76-111">若要运行这些工具，您必须是本地 Administrators 组的成员。</span><span class="sxs-lookup"><span data-stu-id="26a76-111">You must be a member of the local Administrators group to run these tools.'</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="26a76-112">在修改配置文件时一定要格外小心。</span><span class="sxs-lookup"><span data-stu-id="26a76-112">Use caution when modifying configuration files.</span></span> <span data-ttu-id="26a76-113">如果要修改供内部使用而保留的设置，则可能会禁用您的安装。</span><span class="sxs-lookup"><span data-stu-id="26a76-113">If you modify a setting that is reserved for internal use, you may disable your installation.</span></span> <span data-ttu-id="26a76-114">通常，除非试图解决的是特定问题，否则建议您不要修改配置设置。</span><span class="sxs-lookup"><span data-stu-id="26a76-114">Generally, modifying configuration settings is not recommended unless you are trying to solve a specific problem.</span></span> <span data-ttu-id="26a76-115">有关哪些设置可以安全更改的详细信息，请参阅 [RSReportServer Configuration File](rsreportserver-config-configuration-file.md) 或 [RSReportDesigner Configuration File](rsreportdesigner-configuration-file.md)。</span><span class="sxs-lookup"><span data-stu-id="26a76-115">For more information about which settings are safe to change, see [RSReportServer Configuration File](rsreportserver-config-configuration-file.md) or [RSReportDesigner Configuration File](rsreportdesigner-configuration-file.md).</span></span> <span data-ttu-id="26a76-116">有关配置文件的详细信息，请参阅 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 产品文档。</span><span class="sxs-lookup"><span data-stu-id="26a76-116">For more information about configuration files, see the [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] product documentation.</span></span>  
  
 <span data-ttu-id="26a76-117">本主题内容：</span><span class="sxs-lookup"><span data-stu-id="26a76-117">In this topic:</span></span>  
  
-   [<span data-ttu-id="26a76-118">读取和使用配置值</span><span class="sxs-lookup"><span data-stu-id="26a76-118">Reading and Using Configuration Values</span></span>](#bkmk_read_values)  
  
-   [<span data-ttu-id="26a76-119">关于默认值</span><span class="sxs-lookup"><span data-stu-id="26a76-119">About Default Values</span></span>](#bkmk_default_values)  
  
-   [<span data-ttu-id="26a76-120">删除配置设置</span><span class="sxs-lookup"><span data-stu-id="26a76-120">Deleting Configuration Settings</span></span>](#bkmk_delete_config_settings)  
  
-   [<span data-ttu-id="26a76-121">编辑 Reporting Services 配置文件</span><span class="sxs-lookup"><span data-stu-id="26a76-121">To Edit a Reporting Services Configuration File</span></span>](#bkmk_edit_configuation_file)  
  
##  <a name="reading-and-using-configuration-values"></a><a name="bkmk_read_values"></a> <span data-ttu-id="26a76-122">读取和使用配置值</span><span class="sxs-lookup"><span data-stu-id="26a76-122">Reading and Using Configuration Values</span></span>  
 <span data-ttu-id="26a76-123">当启动服务时或保存配置文件时，报表服务器会读取配置文件。</span><span class="sxs-lookup"><span data-stu-id="26a76-123">A report server reads the configuration files when the service starts and whenever the configuration file is saved.</span></span> <span data-ttu-id="26a76-124">在当前的应用程序域过期之后，新值和修订后的值会在新应用程序域中生效。</span><span class="sxs-lookup"><span data-stu-id="26a76-124">New and revised values take effect in a new application domain after the current application domain expires.</span></span> <span data-ttu-id="26a76-125">如有可能，仍在当前应用程序域中处理的请求将能够完成。</span><span class="sxs-lookup"><span data-stu-id="26a76-125">Whenever possible, requests that are still processing in the current application domain are allowed to complete.</span></span> <span data-ttu-id="26a76-126">但是，有几个设置要求立即执行应用程序域回收操作。</span><span class="sxs-lookup"><span data-stu-id="26a76-126">However, a few settings require an immediate application domain recycle operation.</span></span> <span data-ttu-id="26a76-127">在这种情况下，所有正在进行的请求都将在新的应用程序域中重新启动。</span><span class="sxs-lookup"><span data-stu-id="26a76-127">In this case, all requests that are in process are restarted in a new application domain.</span></span>  
  
 <span data-ttu-id="26a76-128">如果报表服务器检测到无效值，则报表服务器会在 Windows 应用程序日志中记录一个错误，报表服务器将无法启动或者将使用默认值，具体取决于错误的类型：</span><span class="sxs-lookup"><span data-stu-id="26a76-128">If the report server detects an invalid value, the report server logs an error to the Windows application log and either fails to start or uses a default value, depending on the error:</span></span>  
  
-   <span data-ttu-id="26a76-129">如果错误类型为 XML 格式不正确，则报表服务器将不启动。</span><span class="sxs-lookup"><span data-stu-id="26a76-129">If the error is malformed XML, the report server will not start.</span></span> <span data-ttu-id="26a76-130">如果当引入错误时报表服务器正在运行，则报表服务器将忽略无效的配置文件，直到报表服务器重新启动或回收了应用程序域为止。</span><span class="sxs-lookup"><span data-stu-id="26a76-130">If the report server is running when you introduce the error, the report server ignores the invalid configuration file until the report server restarts or the application domain is recycled.</span></span> <span data-ttu-id="26a76-131">一旦检测到错误，报表服务器将不再启动。</span><span class="sxs-lookup"><span data-stu-id="26a76-131">Once the error is detected, the report server will no longer start.</span></span>  
  
-   <span data-ttu-id="26a76-132">如果该错误是无效的配置值，则服务器将使用内部默认值并在跟踪日志文件中记录一个错误。</span><span class="sxs-lookup"><span data-stu-id="26a76-132">If the error is an invalid configuration value, the server will use internal default values and log an error to the trace log files.</span></span> <span data-ttu-id="26a76-133">在少数情况下，内部默认值不可用，如果无效的配置设置对于服务器操作至关重要，则服务器将返回 rsServerConfigurationError 错误。</span><span class="sxs-lookup"><span data-stu-id="26a76-133">In the few cases where internal default values are not available, the server will return the rsServerConfigurationError error if the invalid configuration setting is critical to server operations.</span></span> <span data-ttu-id="26a76-134">有关缺少或无效的关键设置的错误将以 HTML 错误页的形式返回到客户端应用程序，并且将记录到事件日志中。</span><span class="sxs-lookup"><span data-stu-id="26a76-134">Errors about missing or invalid critical settings are returned to the client application in an HTML error page and logged to the event log.</span></span>  
  
 <span data-ttu-id="26a76-135">所有的配置文件更改（包括成功的更改）都将记录在报表服务器的跟踪日志文件中。</span><span class="sxs-lookup"><span data-stu-id="26a76-135">All configuration file changes, including successful changes, are recorded in the report server trace log file.</span></span> <span data-ttu-id="26a76-136">仅将错误记录到应用程序事件日志中。</span><span class="sxs-lookup"><span data-stu-id="26a76-136">Only errors are logged to the application event log.</span></span>  
  
##  <a name="about-default-values"></a><a name="bkmk_default_values"></a> <span data-ttu-id="26a76-137">关于默认值</span><span class="sxs-lookup"><span data-stu-id="26a76-137">About Default Values</span></span>  
 <span data-ttu-id="26a76-138">大多数配置设置都具有在报表服务器内部指定的默认值。</span><span class="sxs-lookup"><span data-stu-id="26a76-138">Most configuration settings have default values that are specified internally in the report server.</span></span> <span data-ttu-id="26a76-139">如果用户定义的值无效或者未指定，报表服务器将使用这些默认值。</span><span class="sxs-lookup"><span data-stu-id="26a76-139">The report server will use these values if a user-defined value is invalid or not specified.</span></span> <span data-ttu-id="26a76-140">如果由于配置设置无效而必须使用默认值，则错误将写入跟踪日志文件中。</span><span class="sxs-lookup"><span data-stu-id="26a76-140">If a default value must be used due to an invalid configuration setting, an error is written to the trace log file.</span></span>  
  
##  <a name="deleting-configuration-settings"></a><a name="bkmk_delete_config_settings"></a> <span data-ttu-id="26a76-141">删除配置设置</span><span class="sxs-lookup"><span data-stu-id="26a76-141">Deleting Configuration Settings</span></span>  
 <span data-ttu-id="26a76-142">对于具有默认值的配置设置，从配置文件中删除该设置将没有任何效果。</span><span class="sxs-lookup"><span data-stu-id="26a76-142">For configuration settings that have default values, removing the setting from the configuration file has no effect.</span></span> <span data-ttu-id="26a76-143">大多数配置设置实际上都是在内部定义和配置的。</span><span class="sxs-lookup"><span data-stu-id="26a76-143">Most configuration settings are actually defined and configured internally.</span></span> <span data-ttu-id="26a76-144">如果从配置文件中删除项目，则内部副本仍将可用并使用为其定义的默认值。</span><span class="sxs-lookup"><span data-stu-id="26a76-144">If you delete an item from the configuration file, the internal copy is still available and uses the default value that is defined for it.</span></span>  
  
##  <a name="to-edit-a-reporting-services-configuration-file"></a><a name="bkmk_edit_configuation_file"></a> <span data-ttu-id="26a76-145">编辑 Reporting Services 配置文件</span><span class="sxs-lookup"><span data-stu-id="26a76-145">To Edit a Reporting Services Configuration File</span></span>  
  
1.  <span data-ttu-id="26a76-146">查找要编辑的配置文件：</span><span class="sxs-lookup"><span data-stu-id="26a76-146">Find the configuration file you want to edit:</span></span>  
  
    -   <span data-ttu-id="26a76-147">**RSReportServer.config** 位于以下文件夹中：</span><span class="sxs-lookup"><span data-stu-id="26a76-147">**RSReportServer.config** is located in the following folder:</span></span>  
  
        ```  
        C:\Program Files\Microsoft SQL Server\MSRS11.MSSQLSERVER\Reporting Services\ReportServer  
        ```  
  
    -   <span data-ttu-id="26a76-148">**RSReportServerServices.exe.config** 位于以下文件夹中：</span><span class="sxs-lookup"><span data-stu-id="26a76-148">**RSReportServerServices.exe.config** is located in the following folder:</span></span>  
  
        ```  
        C:\Program Files\Microsoft SQL Server\MSRS11.MSSQLSERVER\Reporting Services\ReportServer\bin  
        ```  
  
    -   <span data-ttu-id="26a76-149">**RSReportDesigner.config** 位于以下文件夹中：</span><span class="sxs-lookup"><span data-stu-id="26a76-149">**RSReportDesigner.config** is located in the following folder:</span></span>  
  
        ```  
        C:\Program Files\Microsoft Visual Studio 10.0\Common7\IDE\PrivateAssemblies  
        ```  
  
2.  <span data-ttu-id="26a76-150">如果需要回滚所做的更改，请保存该文件的副本。</span><span class="sxs-lookup"><span data-stu-id="26a76-150">Save a copy of the file in case you need to roll back your changes.</span></span>  
  
3.  <span data-ttu-id="26a76-151">在“记事本”或代码编辑器中打开原始文件。</span><span class="sxs-lookup"><span data-stu-id="26a76-151">Open the original file in Notepad or a code editor.</span></span> <span data-ttu-id="26a76-152">请不要使用 Textpad，因为它会在保存文件之前设置文件长度，从而导致向跟踪日志文件中写入无效字符的错误。</span><span class="sxs-lookup"><span data-stu-id="26a76-152">Do not use Textpad; it sets the file length before the file is saved, causing an invalid character error to be written to the trace log file.</span></span>  
  
4.  <span data-ttu-id="26a76-153">键入要添加或使用的元素或值。</span><span class="sxs-lookup"><span data-stu-id="26a76-153">Type the element or value that you want to add or use.</span></span> <span data-ttu-id="26a76-154">元素是区分大小写的。</span><span class="sxs-lookup"><span data-stu-id="26a76-154">Elements are case-sensitive.</span></span> <span data-ttu-id="26a76-155">如果要添加元素，请确保使用大小写正确的字母。</span><span class="sxs-lookup"><span data-stu-id="26a76-155">If you are adding an element, be sure to use the correct upper and lower case letters.</span></span> <span data-ttu-id="26a76-156">如果要自定义呈现扩展插件、身份验证扩展插件或数据处理扩展插件，则可以使用配置文件的具体编辑说明：</span><span class="sxs-lookup"><span data-stu-id="26a76-156">Specific instructions for editing configuration files are available if you are customizing rendering extension, authentication extensions, or data processing extensions:</span></span>  
  
    -   [<span data-ttu-id="26a76-157">针对报表服务器的身份验证</span><span class="sxs-lookup"><span data-stu-id="26a76-157">Authentication with the Report Server</span></span>](../security/authentication-with-the-report-server.md)  
  
    -   [<span data-ttu-id="26a76-158">配置报表管理器以便传递自定义身份验证 Cookie</span><span class="sxs-lookup"><span data-stu-id="26a76-158">Configure Report Manager to Pass Custom Authentication Cookies</span></span>](../security/configure-the-web-portal-to-pass-custom-authentication-cookies.md)  
  
    -   [<span data-ttu-id="26a76-159">在 RSReportServer.Config 中自定义呈现扩展插件参数</span><span class="sxs-lookup"><span data-stu-id="26a76-159">Customize Rendering Extension Parameters in RSReportServer.Config</span></span>](../customize-rendering-extension-parameters-in-rsreportserver-config.md)  
  
5.  <span data-ttu-id="26a76-160">保存文件。</span><span class="sxs-lookup"><span data-stu-id="26a76-160">Save the file.</span></span>  
  
6.  <span data-ttu-id="26a76-161">检查跟踪日志文件，确认没有错误发生。</span><span class="sxs-lookup"><span data-stu-id="26a76-161">Check the trace log files to verify that errors did not occur.</span></span> <span data-ttu-id="26a76-162">如果看到错误情况，则说明错误地指定了某个设置或它的值。</span><span class="sxs-lookup"><span data-stu-id="26a76-162">If you see error conditions, a setting or its value is specified incorrectly.</span></span> <span data-ttu-id="26a76-163">请检查 [RSReportServer Configuration File](rsreportserver-config-configuration-file.md) ，了解引起错误的任何设置的有效值。</span><span class="sxs-lookup"><span data-stu-id="26a76-163">Review the [RSReportServer Configuration File](rsreportserver-config-configuration-file.md) for valid values for any setting that is causing an error.</span></span> <span data-ttu-id="26a76-164">有关查看跟踪日志的详细信息，请参阅 [报表服务器服务跟踪日志](report-server-service-trace-log.md)。</span><span class="sxs-lookup"><span data-stu-id="26a76-164">For more information about how to view the trace log, see [Report Server Service Trace Log](report-server-service-trace-log.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26a76-165">另请参阅</span><span class="sxs-lookup"><span data-stu-id="26a76-165">See Also</span></span>  
 <span data-ttu-id="26a76-166">[Rsreportserver.config 配置文件](rsreportserver-config-configuration-file.md) </span><span class="sxs-lookup"><span data-stu-id="26a76-166">[RSReportServer Configuration File](rsreportserver-config-configuration-file.md) </span></span>  
 <span data-ttu-id="26a76-167">[Reportingservicesservice.exe.config 配置文件](reportingservicesservice-configuration-file.md) </span><span class="sxs-lookup"><span data-stu-id="26a76-167">[ReportingServicesService Configuration File](reportingservicesservice-configuration-file.md) </span></span>  
 <span data-ttu-id="26a76-168">[Rsreportdesigner.config 配置文件](rsreportdesigner-configuration-file.md) </span><span class="sxs-lookup"><span data-stu-id="26a76-168">[RSReportDesigner Configuration File](rsreportdesigner-configuration-file.md) </span></span>  
 <span data-ttu-id="26a76-169">[部署数据处理扩展插件](../extensions/data-processing/deploying-a-data-processing-extension.md) </span><span class="sxs-lookup"><span data-stu-id="26a76-169">[Deploying a Data Processing Extension](../extensions/data-processing/deploying-a-data-processing-extension.md) </span></span>  
 <span data-ttu-id="26a76-170">[部署传递扩展插件](../extensions/delivery-extension/deploying-a-delivery-extension.md) </span><span class="sxs-lookup"><span data-stu-id="26a76-170">[Deploying a Delivery Extension](../extensions/delivery-extension/deploying-a-delivery-extension.md) </span></span>  
 <span data-ttu-id="26a76-171">[部署呈现扩展插件](../extensions/rendering-extension/deploying-a-rendering-extension.md) </span><span class="sxs-lookup"><span data-stu-id="26a76-171">[Deploying a Rendering Extension](../extensions/rendering-extension/deploying-a-rendering-extension.md) </span></span>  
 <span data-ttu-id="26a76-172">[如何：部署自定义报表项](../custom-report-items/how-to-deploy-a-custom-report-item.md) </span><span class="sxs-lookup"><span data-stu-id="26a76-172">[How to: Deploy a Custom Report Item](../custom-report-items/how-to-deploy-a-custom-report-item.md) </span></span>  
 [<span data-ttu-id="26a76-173">Reporting Services 配置文件</span><span class="sxs-lookup"><span data-stu-id="26a76-173">Reporting Services Configuration Files</span></span>](reporting-services-configuration-files.md)  
  
  
