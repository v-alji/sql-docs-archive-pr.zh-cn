---
title: Reporting Services SharePoint 模式的 PowerShell cmdlet |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 7835bc97-2827-4215-b0dd-52f692ce5e02
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2b20ad870fd8a9cd7f220eebb2b954d7a88a10c3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694286"
---
# <a name="powershell-cmdlets-for-reporting-services-sharepoint-mode"></a><span data-ttu-id="c0ae6-102">用于 Reporting Services SharePoint 模式的 PowerShell cmdlet</span><span class="sxs-lookup"><span data-stu-id="c0ae6-102">PowerShell cmdlets for Reporting Services SharePoint Mode</span></span>
  <span data-ttu-id="c0ae6-103">安装 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] sharepoint 模式时，会安装 PowerShell cmdlet 以支持 SharePoint 模式下的报表服务器。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-103">When you install [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint mode, PowerShell cmdlets are installed to support report Servers in SharePoint mode.</span></span> <span data-ttu-id="c0ae6-104">这些 cmdlet 涵盖三个功能类别。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-104">The cmdlets cover three categories of functionality.</span></span>  
  
-   <span data-ttu-id="c0ae6-105">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint 共享服务和代理的安装。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-105">Installation of the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint shared service and proxy.</span></span>  
  
-   <span data-ttu-id="c0ae6-106">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 服务应用程序和关联代理的设置和管理。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-106">Provisioning and management of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service applications and associated proxies.</span></span>  
  
-   <span data-ttu-id="c0ae6-107">管理 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 功能，例如扩展插件和加密密钥。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-107">Management of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] features, for example extensions and encryption keys.</span></span>  
  
||  
|-|  
|[!INCLUDE[applies](../includes/applies-md.md)]<span data-ttu-id="c0ae6-108">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]SharePoint 模式</span><span class="sxs-lookup"><span data-stu-id="c0ae6-108">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint Mode</span></span>|  
  
 <span data-ttu-id="c0ae6-109">**本主题包含以下内容：**</span><span class="sxs-lookup"><span data-stu-id="c0ae6-109">**This topic contains the following:**</span></span>  
  
-   [<span data-ttu-id="c0ae6-110">Cmdlet 摘要</span><span class="sxs-lookup"><span data-stu-id="c0ae6-110">Cmdlet Summary</span></span>](#bkmk_cmdlet_sum)  
  
-   [<span data-ttu-id="c0ae6-111">共享服务和代理 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c0ae6-111">Shared Service and Proxy Cmdlets</span></span>](#bkmk_sharedservice_cmdlets)  
  
-   [<span data-ttu-id="c0ae6-112">服务应用程序和代理 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c0ae6-112">Service Application and Proxy Cmdlets</span></span>](#bkmk_serviceapp_cmdlets)  
  
-   [<span data-ttu-id="c0ae6-113">Reporting Services 自定义功能 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c0ae6-113">Reporting Services Custom Functionality Cmdlets</span></span>](#bkmk_ssrsfeatures_cmdlets)  
  
-   [<span data-ttu-id="c0ae6-114">基本示例</span><span class="sxs-lookup"><span data-stu-id="c0ae6-114">Basic Samples</span></span>](#bkmk_basic_samples)  
  
-   [<span data-ttu-id="c0ae6-115">详细示例</span><span class="sxs-lookup"><span data-stu-id="c0ae6-115">Detailed Samples</span></span>](#bkmk_detailedsamples)  
  
    -   [<span data-ttu-id="c0ae6-116">创建 Reporting Services 服务应用程序和代理</span><span class="sxs-lookup"><span data-stu-id="c0ae6-116">Create a Reporting Services service application and proxy</span></span>](#bkmk_example_create_service_application)  
  
    -   [<span data-ttu-id="c0ae6-117">查看和更新 Reporting Services 传递扩展插件</span><span class="sxs-lookup"><span data-stu-id="c0ae6-117">Review and update a Reporting Services delivery extension</span></span>](#bkmk_example_delivery_extension)  
  
    -   [<span data-ttu-id="c0ae6-118">获取和设置 Reporting Service 应用程序数据库的属性，例如，数据库超时值</span><span class="sxs-lookup"><span data-stu-id="c0ae6-118">Get and set properties of the Reporting Servicea application database, for example database timeout</span></span>](#bkmk_example_db_properties)  
  
    -   [<span data-ttu-id="c0ae6-119">列出 reporting services 数据扩展插件-SharePoint 模式</span><span class="sxs-lookup"><span data-stu-id="c0ae6-119">List reporting services data extensions - SharePoint mode</span></span>](#bkmk_example_list_data_extensions)  
  
    -   [<span data-ttu-id="c0ae6-120">更改并列出订阅所有者</span><span class="sxs-lookup"><span data-stu-id="c0ae6-120">Change and list subscription owners</span></span>](#bkmk_change_subscription_owner)  
  
##  <a name="cmdlet-summary"></a><a name="bkmk_cmdlet_sum"></a><span data-ttu-id="c0ae6-121">Cmdlet 摘要</span><span class="sxs-lookup"><span data-stu-id="c0ae6-121">Cmdlet Summary</span></span>  

 <span data-ttu-id="c0ae6-122">若要运行 cmdlet，您需要打开 SharePoint Management Shell。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-122">To run the cmdlets you need to open the SharePoint Management Shell.</span></span> <span data-ttu-id="c0ae6-123">还可以使用 Microsoft Windows 附带的图形用户界面编辑器 **Windows PowerShell 集成脚本环境 (ISE)**。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-123">You can also use the graphical user interface editor that is included with Microsoft Windows, **Windows PowerShell Integrated Scripting Environment (ISE)**.</span></span> <span data-ttu-id="c0ae6-124">有关详细信息，请参阅 [在 Windows Server 上启动 Windows PowerShell](https://docs.microsoft.com/powershell/scripting/getting-started/starting-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-124">For more information, see [Starting Windows PowerShell on Windows Server](https://docs.microsoft.com/powershell/scripting/getting-started/starting-windows-powershell).</span></span> <span data-ttu-id="c0ae6-125">在以下 cmdlet 摘要中，对服务应用程序 "数据库" 的引用是指由服务应用程序创建并使用的所有数据库 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-125">In the following cmdlet summaries, the references to service application 'databases', refer to all of the databases created and used by a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service application.</span></span> <span data-ttu-id="c0ae6-126">这包括配置、警报和 temp 数据库。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-126">This includes the configuration, alerting, and temp databases.</span></span>  

  
 <span data-ttu-id="c0ae6-127">如果您在键入 PowerShell 示例时看到类似以下内容的错误消息：</span><span class="sxs-lookup"><span data-stu-id="c0ae6-127">If you see an error message similar to the following when you type the PowerShell examples:</span></span>  
  
-   <span data-ttu-id="c0ae6-128">Install-SPRSService：无法将项“Install-SPRSService”识别为</span><span class="sxs-lookup"><span data-stu-id="c0ae6-128">Install-SPRSService : The term 'Install-SPRSService' is not recognized as the</span></span>  
    <span data-ttu-id="c0ae6-129">cmdlet、函数、脚本文件或可运行程序的名称。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-129">name of a cmdlet, function, script file, or operable program.</span></span> <span data-ttu-id="c0ae6-130">请检查名称的拼写，如果包含路径，请验证该路径是否正确，并重试。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-130">Check the spelling of the name, or if a path was included, verify that the path is correct and try again.</span></span>  
  
 <span data-ttu-id="c0ae6-131">出现以下问题之一：</span><span class="sxs-lookup"><span data-stu-id="c0ae6-131">One of the following issues is occurring:</span></span>  
  
-   [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="c0ae6-132">SharePoint 模式，因此未安装 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-132">SharePoint mode is not installed and therefore the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] cmdlets are not installed.</span></span>  
  
-   <span data-ttu-id="c0ae6-133">您在 Windows PowerShell 或 Windows PowerShell ISE 而非 SharePoint Management Shell 中运行了 PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-133">You ran the PowerShell command in Windows PowerShell or Windows PowerShell ISE instead of the SharePoint Management Shell.</span></span> <span data-ttu-id="c0ae6-134">使用 SharePoint Management shell 或使用以下命令将 SharePoint 管理单元添加到 Windows PowerShell 窗口：</span><span class="sxs-lookup"><span data-stu-id="c0ae6-134">Use the SharePoint Management shell or add the SharePoint Snap-in to the Windows PowerShell window with the following command:</span></span>  
  
    ```powershell
    Add-PSSnapin Microsoft.SharePoint.PowerShell  
    ```  
  
 <span data-ttu-id="c0ae6-135">有关详细信息，请参阅[使用 Windows PowerShell 管理 SharePoint 2013](https://technet.microsoft.com/library/ee806878.aspx) (https://technet.microsoft.com/library/ee806878.aspx) 。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-135">For more information see [Use Windows PowerShell to administer SharePoint 2013](https://technet.microsoft.com/library/ee806878.aspx) (https://technet.microsoft.com/library/ee806878.aspx).</span></span>  
  
#### <a name="to-open-the-sharepoint-management-shell-and-run-cmdlets"></a><span data-ttu-id="c0ae6-136">打开 SharePoint Management Shell 并运行 cmdlet</span><span class="sxs-lookup"><span data-stu-id="c0ae6-136">To Open the SharePoint Management Shell and run cmdlets</span></span>  
  
1.  <span data-ttu-id="c0ae6-137">单击 **“开始”** 按钮</span><span class="sxs-lookup"><span data-stu-id="c0ae6-137">Click the **Start** button</span></span>  
  
2.  <span data-ttu-id="c0ae6-138">单击 **“Microsoft SharePoint 产品”** 组。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-138">Click the **Microsoft SharePoint Products** group.</span></span>  
  
3.  <span data-ttu-id="c0ae6-139">单击 **“SharePoint Management Shell”**。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-139">Click the **SharePoint Management Shell**.</span></span>  
  
 <span data-ttu-id="c0ae6-140">若要查看针对 cmdlet 的命令行帮助，请在 PowerShell 命令提示符处使用 PowerShell“Get-Help”命令。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-140">To view command line help for a cmdlet use the PowerShell 'Get-Help' command at the PowerShell command prompt.</span></span> <span data-ttu-id="c0ae6-141">例如：</span><span class="sxs-lookup"><span data-stu-id="c0ae6-141">For example:</span></span>  
  
 `Get-Help Get-SPRSServiceApplicationServers`  
  
###  <a name="shared-service-and-proxy-cmdlets"></a><a name="bkmk_sharedservice_cmdlets"></a> <span data-ttu-id="c0ae6-142">共享服务和代理 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c0ae6-142">Shared Service and Proxy Cmdlets</span></span>  
 <span data-ttu-id="c0ae6-143">下表包含用于 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint 共享服务的 PowerShell cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-143">The following table contains the PowerShell cmdlets for the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint shared service.</span></span>  
  
|<span data-ttu-id="c0ae6-144">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c0ae6-144">Cmdlet</span></span>|<span data-ttu-id="c0ae6-145">说明</span><span class="sxs-lookup"><span data-stu-id="c0ae6-145">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="c0ae6-146">Install-SPRSService</span><span class="sxs-lookup"><span data-stu-id="c0ae6-146">Install-SPRSService</span></span>|<span data-ttu-id="c0ae6-147">安装并注册或卸载 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 共享服务。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-147">Installs and registers, or uninstalls, the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] shared service.</span></span> <span data-ttu-id="c0ae6-148">这只能在 SharePoint 模式下具有 SQL Server [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 安装的计算机上进行。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-148">This can be done only on the machine that has an installation of SQL Server [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] in SharePoint mode.</span></span> <span data-ttu-id="c0ae6-149">对于安装，将发生两个操作：</span><span class="sxs-lookup"><span data-stu-id="c0ae6-149">For installation, two operations occur:</span></span><br /><br /> <span data-ttu-id="c0ae6-150">1) [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 服务器场中安装了该服务。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-150">1) The [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service is installed in the farm.</span></span><br /><br /> <span data-ttu-id="c0ae6-151">2) 将 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 服务实例安装到当前计算机上。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-151">2) The [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service instance is installed to the current machine.</span></span><br /><br /> <span data-ttu-id="c0ae6-152">对于卸载，将发生两个操作：</span><span class="sxs-lookup"><span data-stu-id="c0ae6-152">For Uninstallation, two operations occur:</span></span><br /><span data-ttu-id="c0ae6-153">1) [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 从当前计算机上卸载服务。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-153">1) The [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service is uninstalled from the current machine.</span></span><br /><span data-ttu-id="c0ae6-154">2) [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 从场中卸载服务。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-154">2) The [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service is uninstalled from the farm.</span></span><br /><br /> <br /><br /> <span data-ttu-id="c0ae6-155">注意：如果在场中存在安装了 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 服务的任何其他计算机，或者场中仍有 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 服务应用程序在运行，将显示一条警告消息。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-155">NOTE: If there are any other machines in the farm that have the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service installed, or if there are still [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service applications running in the farm, a warning message is displayed.</span></span>|  
|<span data-ttu-id="c0ae6-156">Install-SPRSServiceProxy</span><span class="sxs-lookup"><span data-stu-id="c0ae6-156">Install-SPRSServiceProxy</span></span>|<span data-ttu-id="c0ae6-157">安装并注册（或卸载）SharePoint 场中的 Reporting Services 服务代理。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-157">Installs and registers, or uninstalls, the Reporting Services service proxy in the SharePoint farm.</span></span>|  
|<span data-ttu-id="c0ae6-158">Get-SPRSProxyUrl</span><span class="sxs-lookup"><span data-stu-id="c0ae6-158">Get-SPRSProxyUrl</span></span>|<span data-ttu-id="c0ae6-159">获取用于访问 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 服务的 URL。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-159">Gets the URL(s) for accessing the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service.</span></span>|  
|<span data-ttu-id="c0ae6-160">Get-SPRSServiceApplicationServers</span><span class="sxs-lookup"><span data-stu-id="c0ae6-160">Get-SPRSServiceApplicationServers</span></span>|<span data-ttu-id="c0ae6-161">获取本地 SharePoint 场中包含 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 共享服务安装的所有服务器。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-161">Gets all servers in the local SharePoint farm that contain an installation of the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] shared service.</span></span> <span data-ttu-id="c0ae6-162">此 cmdlet 可用于 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 升级，以确定运行共享服务并因此需要升级的服务器。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-162">This cmdlet is useful for [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] upgrades, to determine which servers run the shared service and therefore need to be upgraded.</span></span>|  
  
###  <a name="service-application-and-proxy-cmdlets"></a><a name="bkmk_serviceapp_cmdlets"></a> <span data-ttu-id="c0ae6-163">服务应用程序和代理 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c0ae6-163">Service Application and Proxy Cmdlets</span></span>  
 <span data-ttu-id="c0ae6-164">下表包含用于 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 服务应用程序及其关联代理的 PowerShell cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-164">The following table contains the PowerShell cmdlets for [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service applications and their associated proxies.</span></span>  
  
|<span data-ttu-id="c0ae6-165">cmdlet</span><span class="sxs-lookup"><span data-stu-id="c0ae6-165">cmdlet</span></span>|<span data-ttu-id="c0ae6-166">说明</span><span class="sxs-lookup"><span data-stu-id="c0ae6-166">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="c0ae6-167">Get-SPRSServiceApplication</span><span class="sxs-lookup"><span data-stu-id="c0ae6-167">Get-SPRSServiceApplication</span></span>|<span data-ttu-id="c0ae6-168">获取一个或多个 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 服务应用程序对象。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-168">Gets one or more [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service application objects.</span></span>|  
|<span data-ttu-id="c0ae6-169">New-SPRSServiceApplication</span><span class="sxs-lookup"><span data-stu-id="c0ae6-169">New-SPRSServiceApplication</span></span>|<span data-ttu-id="c0ae6-170">创建一个新的 Reporting Services 服务应用程序及关联的数据库。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-170">Create a new Reporting Services service application and associated databases.</span></span><br /><br /> <span data-ttu-id="c0ae6-171">LogonType 参数：指定报表服务器是否使用 SSRS 应用程序池帐户或 SQL Server 登录名来访问报表服务器数据库。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-171">LogonType Parameter: Specifies if the report server uses the SSRS Application Pool account or a SQL Server login to access the report server database.</span></span> <span data-ttu-id="c0ae6-172">该参数可以是下列值之一：</span><span class="sxs-lookup"><span data-stu-id="c0ae6-172">It can be one of the following:</span></span><br /><br /> <span data-ttu-id="c0ae6-173">0 Windows 身份验证</span><span class="sxs-lookup"><span data-stu-id="c0ae6-173">0 Windows Authentication</span></span><br /><br /> <span data-ttu-id="c0ae6-174">1 SQL Server</span><span class="sxs-lookup"><span data-stu-id="c0ae6-174">1 SQL Server</span></span><br /><br /> <span data-ttu-id="c0ae6-175">2 应用程序池帐户（默认值）</span><span class="sxs-lookup"><span data-stu-id="c0ae6-175">2 Application Pool Account (default)</span></span>|  
|<span data-ttu-id="c0ae6-176">Remove-SPRSServiceApplication</span><span class="sxs-lookup"><span data-stu-id="c0ae6-176">Remove-SPRSServiceApplication</span></span>|<span data-ttu-id="c0ae6-177">删除指定的 Reporting Services 服务应用程序。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-177">Removes the specified Reporting Services service application.</span></span> <span data-ttu-id="c0ae6-178">此操作也将删除关联的数据库。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-178">This will also remove the associated databases.</span></span>|  
|<span data-ttu-id="c0ae6-179">Set-SPRSServiceApplication</span><span class="sxs-lookup"><span data-stu-id="c0ae6-179">Set-SPRSServiceApplication</span></span>|<span data-ttu-id="c0ae6-180">编辑现有 Reporting Services 服务应用程序的属性。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-180">Edits the properties of an existing Reporting Services service application.</span></span>|  
|<span data-ttu-id="c0ae6-181">New-SPRSServiceApplicationProxy</span><span class="sxs-lookup"><span data-stu-id="c0ae6-181">New-SPRSServiceApplicationProxy</span></span>|<span data-ttu-id="c0ae6-182">创建新的 Reporting Services 服务应用程序代理。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-182">Creates a new Reporting Services service application proxy.</span></span>|  
|<span data-ttu-id="c0ae6-183">Get-SPRSServiceApplicationProxy</span><span class="sxs-lookup"><span data-stu-id="c0ae6-183">Get-SPRSServiceApplicationProxy</span></span>|<span data-ttu-id="c0ae6-184">获取一个或多个 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 服务应用程序代理。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-184">Gets one or more [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service application proxies.</span></span>|  
|<span data-ttu-id="c0ae6-185">Dismount-SPRSDatabase</span><span class="sxs-lookup"><span data-stu-id="c0ae6-185">Dismount-SPRSDatabase</span></span>|<span data-ttu-id="c0ae6-186">为 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 服务应用程序卸除服务应用程序数据库。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-186">Dismounts the service application databases for a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service application.</span></span>|  
|<span data-ttu-id="c0ae6-187">Remove-SPRSDatabase</span><span class="sxs-lookup"><span data-stu-id="c0ae6-187">Remove-SPRSDatabase</span></span>|<span data-ttu-id="c0ae6-188">为 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 服务应用程序移除服务应用程序数据库。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-188">Remove the service application databases for a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service application.</span></span>|  
|<span data-ttu-id="c0ae6-189">Set-SPRSDatabase</span><span class="sxs-lookup"><span data-stu-id="c0ae6-189">Set-SPRSDatabase</span></span>|<span data-ttu-id="c0ae6-190">设置与 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 服务应用程序关联的数据库的属性。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-190">Sets the properties of the databases associated to a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service application.</span></span>|  
|<span data-ttu-id="c0ae6-191">Mount-SPRSDatabase</span><span class="sxs-lookup"><span data-stu-id="c0ae6-191">Mount-SPRSDatabase</span></span>|<span data-ttu-id="c0ae6-192">装入 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 服务应用程序的数据库。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-192">Mounts databases for a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service application.</span></span>|  
|<span data-ttu-id="c0ae6-193">New-SPRSDatabase</span><span class="sxs-lookup"><span data-stu-id="c0ae6-193">New-SPRSDatabase</span></span>|<span data-ttu-id="c0ae6-194">为指定的 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 服务应用程序创建新的服务应用程序数据库。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-194">Create new service application databases for the specified [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service application.</span></span>|  
|<span data-ttu-id="c0ae6-195">Get-SPRSDatabaseCreationScript</span><span class="sxs-lookup"><span data-stu-id="c0ae6-195">Get-SPRSDatabaseCreationScript</span></span>|<span data-ttu-id="c0ae6-196">将数据库创建脚本输出到 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 服务应用程序的屏幕。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-196">Outputs the database creation script to the screen for a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service application.</span></span> <span data-ttu-id="c0ae6-197">然后，您可以在 SQL Server Management Studio 中运行此脚本。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-197">You can then run the script in SQL Server Management Studio.</span></span>|  
|<span data-ttu-id="c0ae6-198">Get-SPRSDatabase</span><span class="sxs-lookup"><span data-stu-id="c0ae6-198">Get-SPRSDatabase</span></span>|<span data-ttu-id="c0ae6-199">获取一个或多个 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 服务应用程序数据库。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-199">Gets one or more [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service application databases.</span></span> <span data-ttu-id="c0ae6-200">使用命令来获取服务应用程序数据库的 ID，以便使用 Set-SPRSDatabase cmdlet 来修改属性，例如 `querytimeout`。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-200">Use the command to get the ID of service application database so you can use the Set-SPRSDatabase comdlet to modify properties, for example the `querytimeout`.</span></span> <span data-ttu-id="c0ae6-201">请参阅本主题中的示例，[获取和设置 Reporting Servicea 应用程序数据库的属性，例如数据库超时](#bkmk_example_db_properties)。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-201">See the example in this topic, [Get and set properties of the Reporting Servicea application database, for example database timeout](#bkmk_example_db_properties).</span></span>|  
|<span data-ttu-id="c0ae6-202">Get-SPRSDatabaseRightsScript</span><span class="sxs-lookup"><span data-stu-id="c0ae6-202">Get-SPRSDatabaseRightsScript</span></span>|<span data-ttu-id="c0ae6-203">将数据库权限脚本输出到 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 服务应用程序的屏幕。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-203">Outputs the database rights script to the screen for a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service application.</span></span> <span data-ttu-id="c0ae6-204">系统会提示所需的用户和数据库，然后返回您可以运行以修改权限的 Transact SQL。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-204">It will prompt for desired user and database then returns transact SQL you can run to modify permissions.</span></span> <span data-ttu-id="c0ae6-205">然后，您可以在 SQL Server Management Studio 中运行此脚本。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-205">You can then run this script in SQL Server Management Studio.</span></span>|  
|<span data-ttu-id="c0ae6-206">Get-SPRSDatabaseUpgradeScript</span><span class="sxs-lookup"><span data-stu-id="c0ae6-206">Get-SPRSDatabaseUpgradeScript</span></span>|<span data-ttu-id="c0ae6-207">将数据库升级脚本输出到此屏幕。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-207">Outputs a database upgrade script to the screen.</span></span> <span data-ttu-id="c0ae6-208">该脚本将 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 服务应用程序数据库升级到当前 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 安装的数据库版本。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-208">The script will upgrade [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service application databases to the database version of the current [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] installation.</span></span>|  
  
###  <a name="reporting-services-custom-functionality-cmdlets"></a><a name="bkmk_ssrsfeatures_cmdlets"></a><span data-ttu-id="c0ae6-209">Reporting Services 自定义功能 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c0ae6-209">Reporting Services Custom Functionality Cmdlets</span></span>  
  
|<span data-ttu-id="c0ae6-210">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c0ae6-210">Cmdlet</span></span>|<span data-ttu-id="c0ae6-211">说明</span><span class="sxs-lookup"><span data-stu-id="c0ae6-211">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="c0ae6-212">Update-SPRSEncryptionKey</span><span class="sxs-lookup"><span data-stu-id="c0ae6-212">Update-SPRSEncryptionKey</span></span>|<span data-ttu-id="c0ae6-213">为指定的 Reporting Services 服务应用程序更新加密密钥并且重新加密其数据。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-213">Updates the encryption key for the specified Reporting Services service application and re-encrypts its data.</span></span>|  
|<span data-ttu-id="c0ae6-214">Restore-SPRSEncryptionKey</span><span class="sxs-lookup"><span data-stu-id="c0ae6-214">Restore-SPRSEncryptionKey</span></span>|<span data-ttu-id="c0ae6-215">还原以前为 Reporting Services 服务应用程序备份的加密密钥。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-215">Restores a previously backed up encryption key for a Reporting Services service application.</span></span>|  
|<span data-ttu-id="c0ae6-216">Remove-SPRSEncryptedData</span><span class="sxs-lookup"><span data-stu-id="c0ae6-216">Remove-SPRSEncryptedData</span></span>|<span data-ttu-id="c0ae6-217">为指定的 Reporting Services 服务应用程序删除加密数据。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-217">Delete the encrypted data for the specified Reporting Services service application.</span></span>|  
|<span data-ttu-id="c0ae6-218">Backup-SPRSEncryptionKey</span><span class="sxs-lookup"><span data-stu-id="c0ae6-218">Backup-SPRSEncryptionKey</span></span>|<span data-ttu-id="c0ae6-219">为指定的 Reporting Services 服务应用程序备份加密密钥。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-219">Backs up the encryption key for the specified Reporting Services service application.</span></span>|  
|<span data-ttu-id="c0ae6-220">New-SPRSExtension</span><span class="sxs-lookup"><span data-stu-id="c0ae6-220">New-SPRSExtension</span></span>|<span data-ttu-id="c0ae6-221">向 Reporting Services 服务应用程序注册新的扩展插件。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-221">Registers a new extension with a Reporting Services service application.</span></span>|  
|<span data-ttu-id="c0ae6-222">Set-SPRSExtension</span><span class="sxs-lookup"><span data-stu-id="c0ae6-222">Set-SPRSExtension</span></span>|<span data-ttu-id="c0ae6-223">设置现有 Reporting Services 扩展插件的属性。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-223">Sets the properties of an existing Reporting Services extension.</span></span>|  
|<span data-ttu-id="c0ae6-224">Remove-SPRSExtension</span><span class="sxs-lookup"><span data-stu-id="c0ae6-224">Remove-SPRSExtension</span></span>|<span data-ttu-id="c0ae6-225">从 Reporting Services 服务应用程序删除扩展插件。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-225">Removes an extension from a Reporting Services service application.</span></span>|  
|<span data-ttu-id="c0ae6-226">Get-SPRSExtension</span><span class="sxs-lookup"><span data-stu-id="c0ae6-226">Get-SPRSExtension</span></span>|<span data-ttu-id="c0ae6-227">获取一个或多个用于 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 服务应用程序的 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 扩展插件。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-227">Gets one or more [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] extensions for a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service application.</span></span><br /><br /> <span data-ttu-id="c0ae6-228">有效值是：</span><span class="sxs-lookup"><span data-stu-id="c0ae6-228">Valid values are:</span></span><br /><br /> <span data-ttu-id="c0ae6-229">**交付**</span><span class="sxs-lookup"><span data-stu-id="c0ae6-229">**Delivery**</span></span><br /><br /> <span data-ttu-id="c0ae6-230">**DeliveryUI**</span><span class="sxs-lookup"><span data-stu-id="c0ae6-230">**DeliveryUI**</span></span><br /><br /> <span data-ttu-id="c0ae6-231">**呈现**</span><span class="sxs-lookup"><span data-stu-id="c0ae6-231">**Render**</span></span><br /><br /> <span data-ttu-id="c0ae6-232">**Data**</span><span class="sxs-lookup"><span data-stu-id="c0ae6-232">**Data**</span></span><br /><br /> <span data-ttu-id="c0ae6-233">**安全性**</span><span class="sxs-lookup"><span data-stu-id="c0ae6-233">**Security**</span></span><br /><br /> <span data-ttu-id="c0ae6-234">**身份验证**</span><span class="sxs-lookup"><span data-stu-id="c0ae6-234">**Authentication**</span></span><br /><br /> <span data-ttu-id="c0ae6-235">**EventProcessing**</span><span class="sxs-lookup"><span data-stu-id="c0ae6-235">**EventProcessing**</span></span><br /><br /> <span data-ttu-id="c0ae6-236">**ReportItems**</span><span class="sxs-lookup"><span data-stu-id="c0ae6-236">**ReportItems**</span></span><br /><br /> <span data-ttu-id="c0ae6-237">**Designer**</span><span class="sxs-lookup"><span data-stu-id="c0ae6-237">**Designer**</span></span><br /><br /> <span data-ttu-id="c0ae6-238">**ReportItemDesigner**</span><span class="sxs-lookup"><span data-stu-id="c0ae6-238">**ReportItemDesigner**</span></span><br /><br /> <span data-ttu-id="c0ae6-239">**ReportItemConverter**</span><span class="sxs-lookup"><span data-stu-id="c0ae6-239">**ReportItemConverter**</span></span><br /><br /> <span data-ttu-id="c0ae6-240">**ReportDefinitionCustomization**</span><span class="sxs-lookup"><span data-stu-id="c0ae6-240">**ReportDefinitionCustomization**</span></span>|  
|<span data-ttu-id="c0ae6-241">Get-SPRSSite</span><span class="sxs-lookup"><span data-stu-id="c0ae6-241">Get-SPRSSite</span></span>|<span data-ttu-id="c0ae6-242">基于是否启用了“ReportingService”功能来获取 SharePoint 站点。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-242">Gets the SharePoint sites based on whether the "ReportingService" feature is enabled.</span></span> <span data-ttu-id="c0ae6-243">默认情况下，将返回启用“ReportingService”功能的站点。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-243">By default, sites that enable the "ReportingService" feature are returned.</span></span>|  
  
##  <a name="basic-samples"></a><a name="bkmk_basic_samples"></a><span data-ttu-id="c0ae6-244">基本示例</span><span class="sxs-lookup"><span data-stu-id="c0ae6-244">Basic Samples</span></span>  
 <span data-ttu-id="c0ae6-245">返回在名称中包含“SPRS”的 cmdlet 的列表。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-245">Return a list of cmdlets that contain 'SPRS' in the name.</span></span> <span data-ttu-id="c0ae6-246">这将是 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] cmdlet 的完整列表。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-246">This will be the full list of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] cmdlets.</span></span>  
  
```powershell
Get-command -noun *SPRS*  
```  
  
 <span data-ttu-id="c0ae6-247">或者借助更详细的信息，传送到名为 commandlist.txt 的文本文件</span><span class="sxs-lookup"><span data-stu-id="c0ae6-247">Or with a little more detail, piped to a text file named commandlist.txt</span></span>  
  
```powershell
Get-Command -Noun *SPRS* | Select name, definition | Format-List | Out-File c:\commandlist.txt  
```  
  
 <span data-ttu-id="c0ae6-248">安装 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint 服务和服务代理。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-248">Install the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint service and service proxy.</span></span>  
  
```powershell
Install-SPRSService  
```  
  
```powershell
Install-SPRSServiceProxy  
```  
  
 <span data-ttu-id="c0ae6-249">启动 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 服务</span><span class="sxs-lookup"><span data-stu-id="c0ae6-249">Start the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service</span></span>  
  
```powershell
Get-SPServiceInstance -all | where {$_.TypeName -like "SQL Server Reporting*"} | Start-SPServiceInstance  
```  
  
 <span data-ttu-id="c0ae6-250">从 SharePoint Management Shell 键入以下命令，以便从日志文件中返回行的筛选后列表。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-250">Type the following command from the SharePoint Management Shell to return a filtered list of rows from the a log file.</span></span> <span data-ttu-id="c0ae6-251">该命令将筛选包含“ssrscustomactionerror”的行。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-251">The command will filter for lines that contain "ssrscustomactionerror".</span></span> <span data-ttu-id="c0ae6-252">此示例用于在安装 rssharepoint.msi 时查找创建的日志文件。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-252">This example is looking at the log file created when the rssharepoint.msi was installed.</span></span>  
  
```powershell
Get-Content -Path C:\Users\testuser\AppData\Local\Temp\rs_sp_0.log | Select-String "ssrscustomactionerror"  
```  
  
##  <a name="detailed-samples"></a><a name="bkmk_detailedsamples"></a><span data-ttu-id="c0ae6-253">详细示例</span><span class="sxs-lookup"><span data-stu-id="c0ae6-253">Detailed Samples</span></span>  
 <span data-ttu-id="c0ae6-254">除了下面的示例外，请参阅 Windows PowerShell 脚本主题中的 "Windows PowerShell 脚本" 部分，[了解步骤 1-4](../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md#bkmk_full_script)。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-254">In addition to the following samples, see the section "Windows PowerShell Script" in the topic [Windows PowerShell script for Steps 1-4](../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md#bkmk_full_script).</span></span>  
  
###  <a name="create-a-reporting-services-service-application-and-proxy"></a><a name="bkmk_example_create_service_application"></a><span data-ttu-id="c0ae6-255">创建 Reporting Services 服务应用程序和代理</span><span class="sxs-lookup"><span data-stu-id="c0ae6-255">Create a Reporting Services service application and proxy</span></span>  
 <span data-ttu-id="c0ae6-256">此示例脚本完成以下任务：</span><span class="sxs-lookup"><span data-stu-id="c0ae6-256">This sample script completes the following tasks:</span></span>  
  
1.  <span data-ttu-id="c0ae6-257">创建 Reporting Services 服务应用程序和代理。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-257">Create a Reporting Services service application and proxy.</span></span> <span data-ttu-id="c0ae6-258">该脚本假设应用程序池“My App Pool”已存在。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-258">The script assumes the application pool "My App Pool" already exists.</span></span>  
  
2.  <span data-ttu-id="c0ae6-259">向默认代理组添加代理</span><span class="sxs-lookup"><span data-stu-id="c0ae6-259">Add the proxy to the default proxy group</span></span>  
  
3.  <span data-ttu-id="c0ae6-260">授予服务应用对端口 80 Web 应用的内容数据库的访问权限。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-260">Grant the service app access to the port 80 web app's content database.</span></span> <span data-ttu-id="c0ae6-261">脚本假定网站 " http://sitename " 已存在。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-261">The script assumes site "http://sitename" already exists.</span></span>  
  
```powershell
# Create service application and service application proxy  
$appPool = Get-SPServiceApplicationPool "My App Pool"  
$serviceApp = New-SPRSServiceApplication "My RS Service App" -ApplicationPool $appPool  
$serviceAppProxy = New-SPRSServiceApplicationProxy -Name "My RS Service App Proxy" -ServiceApplication $serviceApp  
  
# Add service application proxy to default proxy group.  Any web application that uses the default proxy group will now be able to use this service application.  
Get-SPServiceApplicationProxyGroup -default | Add-SPServiceApplicationProxyGroupMember -Member $serviceAppProxy  
  
# Grant application pool account access to the port 80 web application's content database.  
$webApp = Get-SPWebApplication "http://sitename"  
$appPoolAccountName = $appPool.ProcessAccount.LookupName()  
$webApp.GrantAccessToProcessIdentity($appPoolAccountName)
```  
  
###  <a name="review-and-update-a-reporting-services-delivery-extension"></a><a name="bkmk_example_delivery_extension"></a><span data-ttu-id="c0ae6-262">查看并更新 Reporting Services 传递扩展插件</span><span class="sxs-lookup"><span data-stu-id="c0ae6-262">Review and update a Reporting Services delivery extension</span></span>  
 <span data-ttu-id="c0ae6-263">以下 PowerShell 脚本示例更新了名为 `My RS Service App`的服务应用程序的报表服务器电子邮件传递扩展插件的配置。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-263">The following PowerShell script example, updates the configuration for the report server e-mail delivery extension for the service application named `My RS Service App`.</span></span> <span data-ttu-id="c0ae6-264">更新 SMTP 服务器 (`<email server name>`) 的值和 FROM 电子邮件别名 (`<your FROM email address>`)。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-264">Update the values for the SMTP server (`<email server name>`) and the FROM email alias (`<your FROM email address>`).</span></span>  
  
```powershell
$app = Get-SPRSServiceApplication -Name "My RS Service App"  
$emailCfg = Get-SPRSExtension -Identity $app -ExtensionType "Delivery" -Name "Report Server Email" | Select -ExpandProperty ConfigurationXml
$emailXml = [xml]$emailCfg
$emailXml.SelectSingleNode("//SMTPServer").InnerText = "<email server name>"  
$emailXml.SelectSingleNode("//SendUsing").InnerText = "2"  
$emailXml.SelectSingleNode("//SMTPAuthenticate").InnerText = "2"  
$emailXml.SelectSingleNode("//From").InnerText = '<your FROM email address>'  
Set-SPRSExtension -Identity $app -ExtensionType "Delivery" -Name "Report Server Email" -ExtensionConfiguration $emailXml.OuterXml  
```  
  
 <span data-ttu-id="c0ae6-265">在上述示例中，如果您不知道服务应用程序的确切名称，则可重写第一个语句，以基于对部分名称的搜索获取服务应用程序。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-265">In the above example if you did not know the exact name of the service application, you could rewrite the first statement to get the service application based on a search of the partial name.</span></span> <span data-ttu-id="c0ae6-266">例如：</span><span class="sxs-lookup"><span data-stu-id="c0ae6-266">For example:</span></span>  
  
```powershell
$app = Get-SPRSServiceApplication | Where {$_.name -like " ssrs_testapp *"}  
```  
  
 <span data-ttu-id="c0ae6-267">下列脚本将返回名为“Reporting Services Application”的服务应用程序的报表服务器电子邮件传递扩展插件的当前配置值。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-267">The following script will return the current configuration values for the report server e-mail delivery extension for the service application named "Reporting Services Application".</span></span> <span data-ttu-id="c0ae6-268">第一步将变量 $app 的值设置为具有“My RS Service App”名称的服务应用程序的对象。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-268">The first step sets the value of the variable $app to the object of the service application that has a name of " My RS Service App "</span></span>  
  
 <span data-ttu-id="c0ae6-269">第二个语句将获取变量 $app 中的服务应用程序对象的“报表服务器电子邮件”传递扩展插件，并选择配置 XML</span><span class="sxs-lookup"><span data-stu-id="c0ae6-269">The second statement will Get the 'Report Server Email' delivery extension for the service application object in variable $app, and select the configurationXML</span></span>  
  
```powershell
$app = Get-SPRSServiceapplication -Name "Reporting Services Application"  
Get-SPRSExtension -Identity $app -ExtensionType "Delivery" -Name "Report Server Email" | Select -ExpandProperty ConfigurationXml  
```  
  
 <span data-ttu-id="c0ae6-270">你还可以将以上两个语句重写为一个：</span><span class="sxs-lookup"><span data-stu-id="c0ae6-270">You can also rewrite the above two statements as one:</span></span>  
  
```powershell
Get-SPRSServiceApplication -Name "Reporting Services Application" | Get-SPRSExtension -ExtensionType "Delivery" -Name "Report Server Email" | Select -ExpandProperty ConfigurationXml  
```  
  
###  <a name="get-and-set-properties-of-the-reporting-servicea-application-database-for-example-database-timeout"></a><a name="bkmk_example_db_properties"></a><span data-ttu-id="c0ae6-271">获取和设置 Reporting Servicea 应用程序数据库的属性，例如数据库超时</span><span class="sxs-lookup"><span data-stu-id="c0ae6-271">Get and set properties of the Reporting Servicea application database, for example database timeout</span></span>  
 <span data-ttu-id="c0ae6-272">下面的示例首先返回数据库和属性列表，这样你可以确定你接下来为设置命令提供的数据库 GUID (ID)。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-272">The following example first returns a list of the databases and properties so you can determine the database guid (ID) that you then supply to the set command.</span></span> <span data-ttu-id="c0ae6-273">使用 `Get-SPRSDatabase | format-list`来获取完整的属性列表。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-273">For a full list of the properties, use `Get-SPRSDatabase | format-list`.</span></span>  
  
```powershell
Get-SPRSDatabase | Select id, querytimeout,connectiontimeout, status, server, ServiceInstance
```  
  
 <span data-ttu-id="c0ae6-274">以下是输出的一个示例。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-274">The following is an example of the output.</span></span> <span data-ttu-id="c0ae6-275">确定你想要修改的数据库的 ID，并在 SET cmdlet 中使用该ID。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-275">Determine the ID for the database you want to modify and use the ID in the SET cmdlet.</span></span>  
  
-   `Id                : 56f8d1bc-cb04-44cf-bd41-a873643c5a14`  
  
     `QueryTimeout      : 120`  
  
     `ConnectionTimeout : 15`  
  
     `Status            : Online`  
  
     `Server            : SPServer Name=uetestb01`  
  
     `ServiceInstance   : SPDatabaseServiceInstance`  
  
```powershell
Set-SPRSDatabase -Identity 56f8d1bc-cb04-44cf-bd41-a873643c5a14 -QueryTimeout 300  
```  
  
 <span data-ttu-id="c0ae6-276">若要验证是否已设置该值，请再次运行 GET cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-276">To verify the value is set, run the GET cmdlet again.</span></span>  
  
```powershell
Get-SPRSDatabase -Identity 56f8d1bc-cb04-44cf-bd41-a873643c5a14 | Select id, querytimeout,connectiontimeout, status, server, ServiceInstance  
```  
  
###  <a name="list-reporting-services-data-extensions---sharepoint-mode"></a><a name="bkmk_example_list_data_extensions"></a><span data-ttu-id="c0ae6-277">列出 reporting services 数据扩展插件-SharePoint 模式</span><span class="sxs-lookup"><span data-stu-id="c0ae6-277">List reporting services data extensions - SharePoint mode</span></span>  
 <span data-ttu-id="c0ae6-278">以下示例遍历每个 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 服务应用程序并列出它们每个的当前数据扩展插件。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-278">The following example loops through each [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service application and lists the current data extensions for each.</span></span>  
  
```powershell
$apps = Get-SPRSServiceApplication  
foreach ($app in $apps)
{  
Write-host -ForegroundColor "yellow" Service App Name $app.Name  
Get-SPRSExtension -identity $app -ExtensionType "Data" | select name, extensiontype | Format-Table -AutoSize  
}  
```  
  
 <span data-ttu-id="c0ae6-279">**示例输出：**</span><span class="sxs-lookup"><span data-stu-id="c0ae6-279">**Example output:**</span></span>  
  
-   `Name           ExtensionType`  
  
     `----           -------------`  
  
     `SQL                     Data`  
  
     `SQLAZURE                Data`  
  
     `SQLPDW                  Data`  
  
     `OLEDB                   Data`  
  
     `OLEDB-MD                Data`  
  
     `ORACLE                  Data`  
  
     `ODBC                    Data`  
  
     `XML                     Data`  
  
     `SHAREPOINTLIST          Data`  
  
###  <a name="change-and-list-subscription-owners"></a><a name="bkmk_change_subscription_owner"></a><span data-ttu-id="c0ae6-280">更改并列出订阅所有者</span><span class="sxs-lookup"><span data-stu-id="c0ae6-280">Change and list subscription owners</span></span>  
 <span data-ttu-id="c0ae6-281">请参阅 [Use PowerShell to Change and List Reporting Services Subscription Owners and Run a Subscription](subscriptions/manage-subscription-owners-and-run-subscription-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="c0ae6-281">See [Use PowerShell to Change and List Reporting Services Subscription Owners and Run a Subscription](subscriptions/manage-subscription-owners-and-run-subscription-powershell.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0ae6-282">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c0ae6-282">See Also</span></span>  
 <span data-ttu-id="c0ae6-283">[使用 PowerShell 更改和列出 Reporting Services 订阅所有者并运行订阅](subscriptions/manage-subscription-owners-and-run-subscription-powershell.md) </span><span class="sxs-lookup"><span data-stu-id="c0ae6-283">[Use PowerShell to Change and List Reporting Services Subscription Owners and Run a Subscription](subscriptions/manage-subscription-owners-and-run-subscription-powershell.md) </span></span>  
 <span data-ttu-id="c0ae6-284">[清单：使用 PowerShell 验证 PowerPivot for SharePoint](https://docs.microsoft.com/analysis-services/instances/install-windows/checklist-use-powershell-to-verify-power-pivot-for-sharepoint) </span><span class="sxs-lookup"><span data-stu-id="c0ae6-284">[CheckList: Use PowerShell to Verify PowerPivot for SharePoint](https://docs.microsoft.com/analysis-services/instances/install-windows/checklist-use-powershell-to-verify-power-pivot-for-sharepoint) </span></span>  
 [<span data-ttu-id="c0ae6-285">CodePlex SharePoint Management PowerShell 脚本</span><span class="sxs-lookup"><span data-stu-id="c0ae6-285">CodePlex SharePoint Management PowerShell scripts</span></span>](https://sharepointpsscripts.codeplex.com/)   
