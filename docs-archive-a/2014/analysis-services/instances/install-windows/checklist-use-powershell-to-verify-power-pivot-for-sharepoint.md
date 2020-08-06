---
title: 清单：使用 PowerShell 验证 PowerPivot for SharePoint |Microsoft Docs
ms.custom: ''
ms.date: 07/20/2020
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 73a13f05-3450-411f-95f9-4b6167cc7607
author: minewiskan
ms.author: owend
ms.openlocfilehash: 001b3fae82851b9ec08b0383bb3db9e6d011ae32
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688360"
---
# <a name="checklist-use-powershell-to-verify-powerpivot-for-sharepoint"></a><span data-ttu-id="01138-102">清单：使用 PowerShell 验证 PowerPivot for SharePoint</span><span class="sxs-lookup"><span data-stu-id="01138-102">CheckList: Use PowerShell to Verify PowerPivot for SharePoint</span></span>
  <span data-ttu-id="01138-103">若非通过可靠的验证测试确认服务和数据运行正常， [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] 安装或恢复操作就不算完成。</span><span class="sxs-lookup"><span data-stu-id="01138-103">No [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] installation or recovery operation is complete without a solid verification test pass that confirms your services and data are operational.</span></span> <span data-ttu-id="01138-104">在本文中，我们将介绍如何使用 Windows PowerShell 执行这些步骤。</span><span class="sxs-lookup"><span data-stu-id="01138-104">In this article, we show you how to perform these steps using Windows PowerShell.</span></span> <span data-ttu-id="01138-105">我们将每个步骤作为一个章节，方便您跳转到特定的任务。</span><span class="sxs-lookup"><span data-stu-id="01138-105">We put each step into its own section so that you can go straight to specific tasks.</span></span> <span data-ttu-id="01138-106">例如，如果您需要安排服务应用程序和内容数据库的维护或备份操作，则可运行此主题中 [“数据库”](#bkmk_databases) 章节的脚本，以验证服务应用程序和内容数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="01138-106">For example, run the script in the [Databases](#bkmk_databases) section of this topic to verify the name of the service application and content databases if you want to schedule them for maintenance or backup.</span></span>

|||
|-|-|
|<span data-ttu-id="01138-107">![PowerShell 相关内容](../../../reporting-services/media/rs-powershellicon.jpg "PowerShell 相关内容")</span><span class="sxs-lookup"><span data-stu-id="01138-107">![PowerShell related content](../../../reporting-services/media/rs-powershellicon.jpg "PowerShell related content")</span></span>|<span data-ttu-id="01138-108">本主题下方包含了一个完整的 PowerShell 脚本。</span><span class="sxs-lookup"><span data-stu-id="01138-108">A full PowerShell script is included at the bottom of the topic.</span></span> <span data-ttu-id="01138-109">您可以使用此完整脚本作为起点，构建用于审计 [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] 完整部署的自定义脚本。</span><span class="sxs-lookup"><span data-stu-id="01138-109">Use the full script as a starting point to build a custom script for auditing your full [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] deployment.</span></span>|

||
|-|
|<span data-ttu-id="01138-110">**[!INCLUDE[applies](../../../includes/applies-md.md)]** SharePoint 2013 &#124; SharePoint 2010</span><span class="sxs-lookup"><span data-stu-id="01138-110">**[!INCLUDE[applies](../../../includes/applies-md.md)]**  SharePoint 2013 &#124; SharePoint 2010</span></span>|

 <span data-ttu-id="01138-111">**本主题内容**：下面目录中带字母的项目对应于关系图区域。</span><span class="sxs-lookup"><span data-stu-id="01138-111">**In this topic**: The lettered items in the following the TOC correspond to areas of the diagram.</span></span> <span data-ttu-id="01138-112">关系图说明</span><span class="sxs-lookup"><span data-stu-id="01138-112">The diagram illustrates the</span></span>

|||
|-|-|
|[<span data-ttu-id="01138-113">准备 PowerShell 环境</span><span class="sxs-lookup"><span data-stu-id="01138-113">Prepare your PowerShell environment</span></span>](#bkmk_prerequisites)<br /><br /> [<span data-ttu-id="01138-114">症状和建议操作</span><span class="sxs-lookup"><span data-stu-id="01138-114">Symptoms and Recommended Actions</span></span>](#bkmk_symptoms)<br /><br /> <span data-ttu-id="01138-115">**(A)** [Analysis Services Windows 服务](#bkmk_windows_service)</span><span class="sxs-lookup"><span data-stu-id="01138-115">**(A)** [Analysis Services Windows Service](#bkmk_windows_service)</span></span><br /><br /> <span data-ttu-id="01138-116">\*\* (B) \*\* [get-powerpivotsystemservice 和 get-powerpivotengineservice](#bkmk_engine_and_system_service)</span><span class="sxs-lookup"><span data-stu-id="01138-116">**(B)** [PowerPivotSystemService and PowerPivotEngineService](#bkmk_engine_and_system_service)</span></span><br /><br /> <span data-ttu-id="01138-117">**(C)** [PowerPivot 服务应用程序和代理](#bkmk_powerpivot_service_application)</span><span class="sxs-lookup"><span data-stu-id="01138-117">**(C)** [PowerPivot Service Application(s) and proxies](#bkmk_powerpivot_service_application)</span></span><br /><br /> <span data-ttu-id="01138-118">**(D)** [“数据库”](#bkmk_databases)</span><span class="sxs-lookup"><span data-stu-id="01138-118">**(D)** [Databases](#bkmk_databases)</span></span><br /><br /> [<span data-ttu-id="01138-119">SharePoint 功能</span><span class="sxs-lookup"><span data-stu-id="01138-119">SharePoint Features</span></span>](#bkmk_features)<br /><br /> [<span data-ttu-id="01138-120">计时器作业</span><span class="sxs-lookup"><span data-stu-id="01138-120">Timer Jobs</span></span>](#bkmk_timer_jobs)<br /><br /> [<span data-ttu-id="01138-121">运行状况规则</span><span class="sxs-lookup"><span data-stu-id="01138-121">Health Rules</span></span>](#bkmk_health_rules)<br /><br /> <span data-ttu-id="01138-122">**(E)** [Windows 和 ULS 日志](#bkmk_logs)</span><span class="sxs-lookup"><span data-stu-id="01138-122">**(E)** [Windows and ULS Logs](#bkmk_logs)</span></span><br /><br /> [<span data-ttu-id="01138-123">MSOLAP 访问接口</span><span class="sxs-lookup"><span data-stu-id="01138-123">MSOLAP Provider</span></span>](#bkmk_msolap)<br /><br /> [<span data-ttu-id="01138-124">ADOMD.Net 客户端库</span><span class="sxs-lookup"><span data-stu-id="01138-124">ADOMD.Net client Library</span></span>](#bkmk_adomd)<br /><br /> [<span data-ttu-id="01138-125">运行状况数据收集规则</span><span class="sxs-lookup"><span data-stu-id="01138-125">Health Data Collection Rules</span></span>](#bkmk_health_collection)<br /><br /> [<span data-ttu-id="01138-126">解决方案</span><span class="sxs-lookup"><span data-stu-id="01138-126">Solutions</span></span>](#bkmk_solutions)<br /><br /> [<span data-ttu-id="01138-127">手动验证步骤</span><span class="sxs-lookup"><span data-stu-id="01138-127">Manual Verification Steps</span></span>](#bkmk_manual)<br /><br /> [<span data-ttu-id="01138-128">更多资源</span><span class="sxs-lookup"><span data-stu-id="01138-128">More Resources</span></span>](#bkmk_more_resources)<br /><br /> [<span data-ttu-id="01138-129">完整的 PowerShell 脚本</span><span class="sxs-lookup"><span data-stu-id="01138-129">Full PowerShell Script</span></span>](#bkmk_full_script)|<span data-ttu-id="01138-130">![powerpivot 的 powershell 验证](../../../sql-server/install/media/ssas-powershell-component-verification.png "powerpivot 的 powershell 验证")</span><span class="sxs-lookup"><span data-stu-id="01138-130">![powershell verification of powerpivot](../../../sql-server/install/media/ssas-powershell-component-verification.png "powershell verification of powerpivot")</span></span>|

##  <a name="prepare-your-powershell-environment"></a><a name="bkmk_prerequisites"></a><span data-ttu-id="01138-131">准备 PowerShell 环境</span><span class="sxs-lookup"><span data-stu-id="01138-131">Prepare your PowerShell environment</span></span>
 <span data-ttu-id="01138-132">本章节的步骤旨在准备 PowerShell 环境。</span><span class="sxs-lookup"><span data-stu-id="01138-132">The steps in this section prepare your PowerShell environment.</span></span> <span data-ttu-id="01138-133">这些不一定是必需步骤，具体视脚本环境的当前配置方式而定。</span><span class="sxs-lookup"><span data-stu-id="01138-133">The steps may not be required, depending on how your scripting environment is currently configured.</span></span>

 <span data-ttu-id="01138-134">**PowerShell 权限**</span><span class="sxs-lookup"><span data-stu-id="01138-134">**PowerShell Permissions**</span></span>

 <span data-ttu-id="01138-135">以 **管理员权限**打开 Powershell 窗口或 PowerShell ISE（集成脚本环境）。</span><span class="sxs-lookup"><span data-stu-id="01138-135">Open a Powershell window or the PowerShell ISE (Integrated Scripting Environment) with **administrative privileges**.</span></span> <span data-ttu-id="01138-136">如果您不具备管理员权限，则在运行命令时，可能会显示类似以下内容的错误消息：</span><span class="sxs-lookup"><span data-stu-id="01138-136">If you do not have administrative privileges when you run commands, you will see an error message similar to the following:</span></span>

 <span data-ttu-id="01138-137">Get-SPLogEvent：需要拥有计算机的 **管理员权限** 才能运行此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="01138-137">Get-SPLogEvent : You need to have Machine **administrator privileges** to run this cmdlet.</span></span>

 <span data-ttu-id="01138-138">**SharePoint 和 [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)]** 模块</span><span class="sxs-lookup"><span data-stu-id="01138-138">**SharePoint and [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)]** Module</span></span>

 <span data-ttu-id="01138-139">在运行 SharePoint 相关 cmdlet 时，如果显示类似以下内容的错误消息，请运行 Add-PSSnapin 命令：</span><span class="sxs-lookup"><span data-stu-id="01138-139">If you see an error message similar to the following when you run SharePoint related cmdlets, run the Add-PSSnapin command:</span></span>

 <span data-ttu-id="01138-140">无法将“Get-PowerPivotSystemService”项 **识别为 cmdlet**、函数、脚本文件或可运行程序的名称。</span><span class="sxs-lookup"><span data-stu-id="01138-140">The term 'Get-PowerPivotSystemService' **is not recognized as the name of a cmdlet**, function, script file, or operable program.</span></span> <span data-ttu-id="01138-141">请检查名称的拼写，如果包含路径，请验证该路径是否正确，并重试。</span><span class="sxs-lookup"><span data-stu-id="01138-141">Check the spelling of the name, or if a path was included, verify that the path is correct and try again.</span></span>

```
Add-PSSnapin Microsoft.Sharepoint.Powershell -EA 0
```

 <span data-ttu-id="01138-142">**Windows PowerShell**</span><span class="sxs-lookup"><span data-stu-id="01138-142">**Windows PowerShell**</span></span>

 <span data-ttu-id="01138-143">有关 PowerShell ISE 的详细信息，请参阅 [Windows PowerShell ISE 简介](https://technet.microsoft.com/library/dd315244.aspx) 和 [使用 Windows PowerShell 管理 SharePoint 2013](https://technet.microsoft.com/library/ee806878\(v=office.15\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="01138-143">For more information on the PowerShell ISE, see [Introducing the Windows PowerShell ISE](https://technet.microsoft.com/library/dd315244.aspx) and [Use Windows PowerShell to administer SharePoint 2013](https://technet.microsoft.com/library/ee806878\(v=office.15\).aspx).</span></span>

|||
|-|-|
|<span data-ttu-id="01138-144">![sharepoint 常规应用程序设置中的 powerpivot](../../../sql-server/install/media/ssas-powerpivot-logo.png "sharepoint 常规应用程序设置中的 powerpivot")</span><span class="sxs-lookup"><span data-stu-id="01138-144">![powerpivot in sharepoint general application set](../../../sql-server/install/media/ssas-powerpivot-logo.png "powerpivot in sharepoint general application set")</span></span>|<span data-ttu-id="01138-145">借助 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 管理面板，您可以在管理中心有选择地验证大多数组件。</span><span class="sxs-lookup"><span data-stu-id="01138-145">You can optionally verify a majority of the components in Central Administration, using the [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] management dashboard.</span></span> <span data-ttu-id="01138-146">要在“管理中心”打开该面板，请单击 **“常规应用程序设置”**，然后单击 **“PowerPivot”** 中的 **“管理面板”**。</span><span class="sxs-lookup"><span data-stu-id="01138-146">To open the dashboard in Central Administration, click **General Application Settings**, and then click **Management Dashboard** in the **PowerPivot**.</span></span> <span data-ttu-id="01138-147">有关该面板的详细信息，请参阅 [PowerPivot Management Dashboard and Usage Data](../../power-pivot-sharepoint/power-pivot-management-dashboard-and-usage-data.md)。</span><span class="sxs-lookup"><span data-stu-id="01138-147">For more information on the dashboard, see [PowerPivot Management Dashboard and Usage Data](../../power-pivot-sharepoint/power-pivot-management-dashboard-and-usage-data.md).</span></span>|

##  <a name="symptoms-and-recommended-actions"></a><a name="bkmk_symptoms"></a><span data-ttu-id="01138-148">症状和建议操作</span><span class="sxs-lookup"><span data-stu-id="01138-148">Symptoms and Recommended Actions</span></span>
 <span data-ttu-id="01138-149">下表列出了症状或问题，以及本主题的建议章节（旨在帮助您解决问题）。</span><span class="sxs-lookup"><span data-stu-id="01138-149">The following table is a list of symptoms or issues and the suggested section of this topic to consult to help you resolve the issue.</span></span>

|<span data-ttu-id="01138-150">症状</span><span class="sxs-lookup"><span data-stu-id="01138-150">Symptom</span></span>|<span data-ttu-id="01138-151">参阅章节</span><span class="sxs-lookup"><span data-stu-id="01138-151">See section</span></span>|
|-------------|-----------------|
|<span data-ttu-id="01138-152">未运行数据刷新</span><span class="sxs-lookup"><span data-stu-id="01138-152">Data refresh is not running</span></span>|<span data-ttu-id="01138-153">请参阅 [Timer Jobs](#bkmk_timer_jobs) 章节，并验证 **“联机 PowerPivot 数据刷新计时器作业”** 是否处于联机状态。</span><span class="sxs-lookup"><span data-stu-id="01138-153">See the section [Timer Jobs](#bkmk_timer_jobs) and verify the **Online PowerPivot Data Refresh Timer Job** is online.</span></span>|
|<span data-ttu-id="01138-154">管理面板数据陈旧</span><span class="sxs-lookup"><span data-stu-id="01138-154">Management dashboard data is old</span></span>|<span data-ttu-id="01138-155">请参阅 [计时器作业](#bkmk_timer_jobs) 章节，并验证 **“管理面板处理计时器作业”** 是否处于联机状态。</span><span class="sxs-lookup"><span data-stu-id="01138-155">See the section [Timer Jobs](#bkmk_timer_jobs) and verify the **Management Dashboard Processing Timer Job** is online.</span></span>|
|<span data-ttu-id="01138-156">管理面板的某些部分</span><span class="sxs-lookup"><span data-stu-id="01138-156">Some portions of the Management Dashboard</span></span>|<span data-ttu-id="01138-157">如果您将 PowerPivot for SharePoint 安装到具有管理中心拓扑但没有 Excel Services 或 PowerPivot for SharePoint 的场中，并且希望对 PowerPivot 管理面板中的内置报表具有完全访问权限，则必须下载和安装 Microsoft ADOMD.NET 客户端库。</span><span class="sxs-lookup"><span data-stu-id="01138-157">If you install PowerPivot for SharePoint into a farm that has the topology of Central Administration, without Excel Services or PowerPivot for SharePoint, you must download and install the Microsoft ADOMD.NET client library if you want full access to the built-in reports in the PowerPivot management dashboard.</span></span> <span data-ttu-id="01138-158">该面板中的某些报表将使用 ADOMD.NET 来访问内部数据，内部数据可提供有关 PowerPivot 查询处理和场中服务器运行状况的报告数据。</span><span class="sxs-lookup"><span data-stu-id="01138-158">Some reports in the dashboard use ADOMD.NET to access internal data that provides reporting data on PowerPivot query processing and server health in the farm.</span></span> <span data-ttu-id="01138-159">请参阅 [ADOMD.Net 客户端库](#bkmk_adomd) 章节和 [在运行管理中心的 Web 前端服务器上安装 ADOMD.NET](../../../sql-server/install/install-adomd-net-on-web-front-end-servers-running-central-administration.md)主题。</span><span class="sxs-lookup"><span data-stu-id="01138-159">See the section [ADOMD.Net client Library](#bkmk_adomd) and the topic [Install ADOMD.NET on Web Front-End Servers Running Central Administration](../../../sql-server/install/install-adomd-net-on-web-front-end-servers-running-central-administration.md).</span></span>|
|\<future content>||

##  <a name="analysis-services-windows-service"></a><a name="bkmk_windows_service"></a><span data-ttu-id="01138-160">Analysis Services Windows 服务</span><span class="sxs-lookup"><span data-stu-id="01138-160">Analysis Services Windows Service</span></span>
 <span data-ttu-id="01138-161">本章节中的脚本用于验证 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] SharePoint 模式下的实例。</span><span class="sxs-lookup"><span data-stu-id="01138-161">The script in this section verifies the instance of [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] in SharePoint mode.</span></span> <span data-ttu-id="01138-162">验证服务是否**正在运行**。</span><span class="sxs-lookup"><span data-stu-id="01138-162">Verify the service is **running**.</span></span>

```powershell
Get-Service | Select name, displayname, status | Where {$_.Name -eq "msolap`$powerpivot"} | Format-Table -Property * -AutoSize | Out-Default
```

```Output
Name              DisplayName                                Status
----              -----------                                ------
MSOLAP$POWERPIVOT SQL Server Analysis Services (POWERPIVOT) Running
```

##  <a name="powerpivotsystemservice-and-powerpivotengineservice"></a><a name="bkmk_engine_and_system_service"></a><span data-ttu-id="01138-163">Get-powerpivotsystemservice 和 Get-powerpivotengineservice</span><span class="sxs-lookup"><span data-stu-id="01138-163">PowerPivotSystemService and PowerPivotEngineService</span></span>
 <span data-ttu-id="01138-164">本章节中的脚本用于验证 [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] 系统服务。</span><span class="sxs-lookup"><span data-stu-id="01138-164">The scripts in this section verify the [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] system services.</span></span> <span data-ttu-id="01138-165">用于 SharePoint 2013 部署的系统服务有一个，用于 SharePoint 2010 部署的服务有两个。</span><span class="sxs-lookup"><span data-stu-id="01138-165">There is one system service for a SharePoint 2013 deployment and two services for a SharePoint 2010 deployment.</span></span>

 <span data-ttu-id="01138-166">**PowerPivotSystemService**</span><span class="sxs-lookup"><span data-stu-id="01138-166">**PowerPivotSystemService**</span></span>

 <span data-ttu-id="01138-167">验证状态是否为 "**联机**"。</span><span class="sxs-lookup"><span data-stu-id="01138-167">Verify the Status is **Online**.</span></span>

```powershell
Get-PowerPivotSystemService | Select typename, status, applications, farm | Format-Table -Property * -AutoSize | Out-Default
```

```Output
TypeName                                  Status Applications                             Farm
--------                                  ------ ------------                             ----
SQL Server PowerPivot Service Application Online {Default PowerPivot Service Application} SPFarm Name=SharePoint_Config_77d8ab0744a34e8aa27c806a2b8c760c
```

 <span data-ttu-id="01138-168">**Get-powerpivotengineservice**</span><span class="sxs-lookup"><span data-stu-id="01138-168">**PowerPivotEngineService**</span></span>

> [!NOTE]
>  <span data-ttu-id="01138-169">如果您使用的是 SharePoint 2013，请**跳过该脚本** 。</span><span class="sxs-lookup"><span data-stu-id="01138-169">**Skip this script if** you are using SharePoint 2013.</span></span> <span data-ttu-id="01138-170">PowerPivotEngineService 不是 SharePoint 2013 部署的一部分。</span><span class="sxs-lookup"><span data-stu-id="01138-170">The PowerPivotEngineService is not part of a SharePoint 2013 deployment.</span></span> <span data-ttu-id="01138-171">如果您在 SharePoint 2013 上运行 Get-PowerPivot**引擎**服务 cmdlet，则系统会显示类似以下内容的错误消息。</span><span class="sxs-lookup"><span data-stu-id="01138-171">If you run the Get-PowerPivot**Engine**Service cmdlet on SharePoint 2013, you will see an error message similar to the following.</span></span> <span data-ttu-id="01138-172">即使您已运行了本主题先决条件中说明的 Add-PSSnapin 命令，仍会返回该错误消息。</span><span class="sxs-lookup"><span data-stu-id="01138-172">This error message is returned even if you have run the Add-PSSnapin command described in the prerequisites section of this topic.</span></span>
> 
>  <span data-ttu-id="01138-173">无法将“Get-PowerPivotEngineService”项识别为 cmdlet 的名称</span><span class="sxs-lookup"><span data-stu-id="01138-173">The term 'Get-PowerPivotEngineService' is not recognized as the name of a cmdlet</span></span>

 <span data-ttu-id="01138-174">在 SharePoint 2010 部署中，请验证状态是否为 **联机**。</span><span class="sxs-lookup"><span data-stu-id="01138-174">In a SharePoint 2010 deployment, verify the status is **Online**.</span></span>

```powershell
Get-PowerPivotEngineService | Select typename, status, name, instances, farm | Format-Table -Property * -AutoSize | Out-Default
```

```Output
TypeName  : SQL Server Analysis Services
Status    : Online
Name      : MSOLAP$POWERPIVOT
Instances : {POWERPIVOT}
Farm      : SPFarm Name=SharePoint_Config
```

##  <a name="powerpivot-service-applications-and-proxies"></a><a name="bkmk_powerpivot_service_application"></a><span data-ttu-id="01138-175">PowerPivot 服务应用程序 (s) 和代理</span><span class="sxs-lookup"><span data-stu-id="01138-175">PowerPivot Service Application(s) and proxies</span></span>
 <span data-ttu-id="01138-176">验证状态是否为 **联机**。</span><span class="sxs-lookup"><span data-stu-id="01138-176">Verify the status is **Online**.</span></span> <span data-ttu-id="01138-177">Excel Services 应用程序不使用服务应用程序数据库，因此，cmdlet 不返回数据库名称。</span><span class="sxs-lookup"><span data-stu-id="01138-177">The Excel Services Application does not use a service application database and therefore the cmdlet does not return a database name.</span></span> <span data-ttu-id="01138-178">记下 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 服务应用程序使用的数据库，以便在本主题后面的数据库章节中验证此数据库是否联机。</span><span class="sxs-lookup"><span data-stu-id="01138-178">Note the database used by the [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] service application so you can verify the database is online in the database section later in this topic.</span></span>

 <span data-ttu-id="01138-179">**PowerPivot 和 Excel Service 应用程序**</span><span class="sxs-lookup"><span data-stu-id="01138-179">**PowerPivot and Excel Service Application(s)**</span></span>

 <span data-ttu-id="01138-180">对于 SharePoint 2010 部署，验证状态是否为 **联机**。</span><span class="sxs-lookup"><span data-stu-id="01138-180">For a SharePoint 2010 deployment, verify the status is **Online**.</span></span>

```powershell
Get-PowerPivotServiceApplication | Select typename,name, status, unattendedaccount, applicationpool, farm, database
Get-SPExcelServiceApplication | Select typename, DisplayName, status
```

```Output
TypeName          : PowerPivot Service Application
Name              : PowerPivotServiceApplication1
Status            : Online
UnattendedAccount : PowerPivotUnattendedAccount
ApplicationPool   : SPIisWebServiceApplicationPool Name=sqlbi_serviceapp
Farm              : SPFarm Name=SharePoint_Config
Database          : GeminiServiceDatabase Name=PowerPivotServiceApplication1_19648f3f2c944e27acdc6c20aab8487a

TypeName    : Excel Services Application Web Service Application
DisplayName : Excel Services Application
Status      : Online
```

 <span data-ttu-id="01138-181">**服务应用程序池**</span><span class="sxs-lookup"><span data-stu-id="01138-181">**Service Application Pool**</span></span>

> [!NOTE]
>  <span data-ttu-id="01138-182">下面的代码示例首先返回默认 [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] 服务应用程序的 applicationpool 属性。</span><span class="sxs-lookup"><span data-stu-id="01138-182">The following code sample first returns the applicationpool property of the default [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] service application.</span></span> <span data-ttu-id="01138-183">系统从此字符串解析出名称，并用其获取应用程序池对象的状态。</span><span class="sxs-lookup"><span data-stu-id="01138-183">The name is parsed from the string and used to get the status of the application pool object.</span></span>
> 
>  <span data-ttu-id="01138-184">验证状态是否为 "**联机**"。</span><span class="sxs-lookup"><span data-stu-id="01138-184">Verify the Status is **Online**.</span></span> <span data-ttu-id="01138-185">如果状态为 "未联机"，或在浏览站点时出现 "http 错误" [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] ，请验证 IIS 应用程序池中的标识凭据是否仍正确。</span><span class="sxs-lookup"><span data-stu-id="01138-185">If the status is not Online or you see "http error" when you browse the [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] site, verify the identity credentials in the IIS application pools are still correct.</span></span> <span data-ttu-id="01138-186">IIS 池名称将为 Get-SPServiceApplicationPool 命令返回的 ID 属性的值。</span><span class="sxs-lookup"><span data-stu-id="01138-186">The IIS pool name will is the value of the ID property returned by the Get-SPServiceApplicationPool command.</span></span>

```powershell
$poolname = [string](Get-PowerPivotServiceApplication | Select -Property applicationpool)
$position = $poolname.lastindexof("=")
$poolname = $poolname.substring($position+1)
$poolname = $poolname.substring(0,$poolname.length-1)

Get-SPServiceApplicationPool | Select name, status, processaccountname, id | Where {$_.Name -eq $poolname} | Format-Table -Property * -AutoSize | Out-Default
```

```Output
Name                           Status ProcessAccountName Id
----                           ------ ------------------ ------- 
SharePoint Web Services System Online DOMAIN\account     89b50ec3-49e3-4de7-881a-2cec4b8b73ea
```

 ![注意](../../../reporting-services/media/rs-fyinote.png "注意")还可以在管理中心页面 "**管理服务应用程序**" 上验证应用程序池。 <span data-ttu-id="01138-188">单击服务应用程序的名称，然后单击功能区中的 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="01138-188">Click the name of the service application and then click **properties** in the ribbon.</span></span>

 <span data-ttu-id="01138-189">**PowerPivot 和 Excel Service 应用程序代理**</span><span class="sxs-lookup"><span data-stu-id="01138-189">**PowerPivot and Excel Service Application proxies**</span></span>

 <span data-ttu-id="01138-190">验证状态是否为 "**联机**"。</span><span class="sxs-lookup"><span data-stu-id="01138-190">Verify the Status is **Online**.</span></span>

```powershell
Get-SPServiceApplicationProxy | Select typename, status, unattendedaccount, displayname | Where {$_.TypeName -Like "*powerpivot*" -Or $_.TypeName -Like "*excel services*"} | Format-Table -Property * -AutoSize | Out-Default
```

```Output
TypeName                                                 Status UnattendedAccount           DisplayName
--------                                                 ------ -----------------           -----------
PowerPivot Service Application Proxy                     Online PowerPivotUnattendedAccount PowerPivotServiceApplication1
Excel Services Application Web Service Application Proxy Online                             Excel Services Application
```

##  <a name="databases"></a><a name="bkmk_databases"></a><span data-ttu-id="01138-191">数据库</span><span class="sxs-lookup"><span data-stu-id="01138-191">Databases</span></span>
 <span data-ttu-id="01138-192">下面的脚本返回服务应用程序数据库和所有内容数据库的状态。</span><span class="sxs-lookup"><span data-stu-id="01138-192">The following script returns the status of the service application databases and all content databases.</span></span> <span data-ttu-id="01138-193">验证状态是否为 **联机**。</span><span class="sxs-lookup"><span data-stu-id="01138-193">Verify the status is **Online**.</span></span>

```powershell
Get-SPDatabase | Select name, status, server, typename | Where {$_.TypeName -eq "content database" -Or $_.TypeName -Like "*Gemini*"} | Format-Table -Property * -AutoSize | Out-Default
```

```Output
Name                                                                       Status Server                  TypeName 
----                                                                       ------ ------                  -------- 
DefaultPowerPivotServiceApplicationDB-38422181-2b68-4ab2-b2bb-9c00c39e5a5e Online SPServer Name=TESTSERVER Microsoft.AnalysisServices.SPAddin.GeminiServiceDatabase
DefaultWebApplicationDB-f0db1a8e-4c22-408c-b9b9-153bd74b0312               Online TESTSERVER\POWERPIVOT    Content Database 
SharePoint_Admin_3cadf0b098bf49e0bb15abd487f5c684                          Online TESTSERVER\POWERPIVOT    Content Database
```

##  <a name="sharepoint-features"></a><a name="bkmk_features"></a><span data-ttu-id="01138-194">SharePoint 功能</span><span class="sxs-lookup"><span data-stu-id="01138-194">SharePoint Features</span></span>
 <span data-ttu-id="01138-195">验证站点、Web 和场功能是否联机。</span><span class="sxs-lookup"><span data-stu-id="01138-195">Verify the site, web, and farm features are online.</span></span>

```powershell
Get-SPFeature | Select displayname, status, scope, farm | Where {$_.displayName -Like "*powerpivot*"} | Format-Table -Property * -AutoSize | Out-Default
```

```Output
DisplayName     Status Scope Farm                         
-----------     ------ ----- ----                         
PowerPivotSite  Online  Site SPFarm Name=SharePoint_Config
PowerPivotAdmin Online   Web SPFarm Name=SharePoint_Config
PowerPivot      Online  Farm SPFarm Name=SharePoint_Config
```

##  <a name="timer-jobs"></a><a name="bkmk_timer_jobs"></a><span data-ttu-id="01138-196">计时器作业</span><span class="sxs-lookup"><span data-stu-id="01138-196">Timer Jobs</span></span>
 <span data-ttu-id="01138-197">验证计时器作业是否 **“联机”**。</span><span class="sxs-lookup"><span data-stu-id="01138-197">Verify the Time Jobs are **Online**.</span></span> <span data-ttu-id="01138-198">[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] EngineService 未安装在 SharePoint 2013 上，因此，此脚本不会列出 SharePoint 2013 部署中的 EngineService 计时器作业。</span><span class="sxs-lookup"><span data-stu-id="01138-198">The [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] EngineService is not installed on SharePoint 2013, therefore the script will not list EngineService timer jobs in a SharePoint 2013 deployment.</span></span>

```powershell
Get-SPTimerJob | Where {$_.service -Like "*power*" -Or $_.service -Like "*mid*"} | Select status, displayname, LastRunTime, service | Format-Table -Property * -AutoSize | Out-Default
```

```Output
      Status DisplayName                                                                          LastRunTime          Service                             
------ -----------                                                                          -----------          -------                             
Online Health Analysis Job (Daily, SQL Server Analysis Services, All Servers)               4/9/2014 12:00:01 AM EngineService Name=MSOLAP$POWERPIVOT
Online Health Analysis Job (Hourly, SQL Server Analysis Services, All Servers)              4/9/2014 1:00:01 PM  EngineService Name=MSOLAP$POWERPIVOT
Online Health Analysis Job (Weekly, SQL Server Analysis Services, All Servers)              4/6/2014 12:00:10 AM EngineService Name=MSOLAP$POWERPIVOT
Online PowerPivot Management Dashboard Processing Timer Job                                 4/8/2014 3:45:38 AM  MidTierService
Online PowerPivot Health Statistics Collector Timer Job                                     4/9/2014 1:00:12 PM  MidTierService
Online PowerPivot Data Refresh Timer Job                                                    4/9/2014 1:09:36 PM  MidTierService
Online Health Analysis Job (Daily, SQL Server PowerPivot Service Application, All Servers)  4/9/2014 12:00:00 AM MidTierService
Online Health Analysis Job (Daily, SQL Server PowerPivot Service Application, Any Server)   4/9/2014 12:00:00 AM MidTierService
Online Health Analysis Job (Weekly, SQL Server PowerPivot Service Application, All Servers) 4/6/2014 12:00:03 AM MidTierService
Online Health Analysis Job (Weekly, SQL Server PowerPivot Service Application, Any Server)  4/6/2014 12:00:03 AM MidTierService
Online PowerPivot Setup Extension Timer Job                                                 4/1/2014 1:40:31 AM  MidTierService
```

##  <a name="health-rules"></a><a name="bkmk_health_rules"></a><span data-ttu-id="01138-199">运行状况规则</span><span class="sxs-lookup"><span data-stu-id="01138-199">Health Rules</span></span>
 <span data-ttu-id="01138-200">SharePoint 2013 部署中包含少量规则。</span><span class="sxs-lookup"><span data-stu-id="01138-200">There are fewer rules in a SharePoint 2013 deployment.</span></span> <span data-ttu-id="01138-201">有关每个 SharePoint 环境规则的完整列表以及如何使用这些规则的说明，请参阅[PowerPivot 运行状况规则-配置](../../power-pivot-sharepoint/configure-power-pivot-health-rules.md)。</span><span class="sxs-lookup"><span data-stu-id="01138-201">For a full list of rules for each SharePoint environment and an explanation of how to use the rules, see [PowerPivot Health Rules - Configure](../../power-pivot-sharepoint/configure-power-pivot-health-rules.md).</span></span>

```powershell
Get-SPHealthAnalysisRule | Select name, enabled, summary | Where {$_.summary -Like "*power*"}  | Format-Table -Property * -AutoSize | Out-Default
```

```Output
Name                          Enabled Summary
----                          ------- -------         
SecondaryLogonHealthRule         True PowerPivot:  Secondary Logon service (seclogon) is disabled
DataRefreshTimerJobHealthRule    True PowerPivot: The PowerPivot Data Refresh timer job is disabled.
ASUsageLoadHealthRule            True PowerPivot: The ratio of load events to connections is too high.
ASMiniDumpHealthRule             True PowerPivot: One or more minidump files were found in the Logs directory, indicating a program crash
ASUsageCubeRule                  True PowerPivot: Usage data is not getting updated at the expected frequency.
ASADOMDNETHealthRule             True PowerPivot: ADOMD.NET is not installed on a standalone WFE that is configured for central admin
MidTierAcctReadPermissionRule    True PowerPivot: MidTier process account should have 'Full Read' permission on all associated SPWebApplications.
```

##  <a name="windows-and-uls-logs"></a><a name="bkmk_logs"></a><span data-ttu-id="01138-202">Windows 和 ULS 日志</span><span class="sxs-lookup"><span data-stu-id="01138-202">Windows and ULS Logs</span></span>
 <span data-ttu-id="01138-203">**Windows 事件日志**</span><span class="sxs-lookup"><span data-stu-id="01138-203">**Windows event log**</span></span>

 <span data-ttu-id="01138-204">下面的命令将在 Windows 事件日志中搜索与 SharePoint 模式下的 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 实例相关的事件。</span><span class="sxs-lookup"><span data-stu-id="01138-204">The following command will search the windows event log for events related to the instance of [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] in SharePoint mode.</span></span> <span data-ttu-id="01138-205">有关禁用事件或更改事件级别的信息，请参阅[配置和查看 SharePoint 日志文件和诊断日志记录 &#40;PowerPivot for SharePoint&#41;](../../power-pivot-sharepoint/configure-and-view-sharepoint-and-diagnostic-logging.md)。</span><span class="sxs-lookup"><span data-stu-id="01138-205">For information on disabling events or changing the event level, see [Configure and View SharePoint Log Files  and Diagnostic Logging &#40;PowerPivot for SharePoint&#41;](../../power-pivot-sharepoint/configure-and-view-sharepoint-and-diagnostic-logging.md).</span></span>

 <span data-ttu-id="01138-206">**服务名称：** MSOLAP$POWERPIVOT</span><span class="sxs-lookup"><span data-stu-id="01138-206">**Service Name:** MSOLAP$POWERPIVOT</span></span>

 <span data-ttu-id="01138-207">**Windows 服务中的显示名称：** SQL Server Analysis Services (POWERPIVOT)</span><span class="sxs-lookup"><span data-stu-id="01138-207">**Display name in Windows Services:** SQL Server Analysis Services (POWERPIVOT)</span></span>

```powershell
Get-EventLog "application" | Where-Object {$_.source -Like "msolap`$powerpivot*"}  | Select timegenerated, entrytype , source, message | Format-Table -property * -AutoSize | Out-Default
```

```Output
TimeGenerated           EntryType Source            Message
-------------           --------- ------            -------
4/16/2014 1:45:19 PM  Information MSOLAP$POWERPIVOT Software usage metrics are disabled.
4/16/2014 1:45:19 PM  Information MSOLAP$POWERPIVOT Service started. Microsoft SQL Server Analysis Services 64 Bit Evaluation (x64) RTM 12.0.1997.5.
4/16/2014 1:45:18 PM  Information MSOLAP$POWERPIVOT The flight recorder was started.
4/14/2014 6:45:37 PM  Information MSOLAP$POWERPIVOT Software usage metrics are disabled.
```

 <span data-ttu-id="01138-208">**SharePoint ULS 日志，最近 48 小时**</span><span class="sxs-lookup"><span data-stu-id="01138-208">**SharePoint ULS Log, last 48 hours**</span></span>

 <span data-ttu-id="01138-209">下面的命令将从 ULS 日志返回最近 48 小时内创建的 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 消息。</span><span class="sxs-lookup"><span data-stu-id="01138-209">The following command will return [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] messages from the ULS log that were created in the last 48 hours.</span></span> <span data-ttu-id="01138-210">根据需要调整 addhours 参数。</span><span class="sxs-lookup"><span data-stu-id="01138-210">Adjust the addhours parameter for your need.</span></span>

```powershell
Get-SPLogEvent -StartTime(Get-Date).AddHours(-48) | Where-Object {$_.Area -eq "powerpivot service" -and $_.level -eq "high"} | Select timestamp, area, category, eventid,level, message | Format-Table -Property * -AutoSize | Out-Default
```

 <span data-ttu-id="01138-211">下面的命令变体只返回 **数据刷新** 类别的日志事件。</span><span class="sxs-lookup"><span data-stu-id="01138-211">The following variation of the command only returns log events for the **data refresh** category.</span></span>

```powershell
Get-SPLogEvent -starttime(Get-Date).addhours(-48) | Where-Object {$_.category -eq "data refresh" -and $_.level -eq "high"} | Select timestamp, area, category, eventid, level, correlation, message
```

```Output
Timestamp   : 4/14/2014 7:15:01 PM
Area        : PowerPivot Service
Category    : Data Refresh
EventID     : 43
Level       : High
Correlation : 5755879c-7cab-e097-8f80-f27895d44a77
Message     : The following error occurred when working with the service application, Default PowerPivot Service Application. Skipping the service application..

Timestamp   : 4/14/2014 7:15:02 PM
Area        : PowerPivot Service
Category    : Data Refresh
EventID     : 99
Level       : High
Correlation : 5755879c-7cab-e097-8f80-f27895d44a77
Message     : EXCEPTION: System.TimeoutException: The request channel timed out while waiting for a reply after 00:00:47.0625313. Increase the timeout value passed to 
              the call to Request or increase the SendTimeout value on the Binding. The time allotted to this operation may have been a portion of a longer timeout. 
              ---> System.TimeoutException: The HTTP request to 'http://localhost:32843/SecurityTokenServiceApplication/securitytoken.svc/actas' has exceeded the 
              allotted timeout of 00:00:54.5930000. The time allotted to this operation may have been a portion of a longer timeout. ---> System.Net.WebException: The 
              operation has timed out     at System.Net.HttpWebRequest.GetResponse()     at 
              System.ServiceModel.Channels.HttpChannelFactory`1.HttpRequestChannel.HttpChannelRequest.WaitForReply(TimeSpan timeout...
```

##  <a name="msolap-provider"></a><a name="bkmk_msolap"></a><span data-ttu-id="01138-212">MSOLAP 提供程序</span><span class="sxs-lookup"><span data-stu-id="01138-212">MSOLAP Provider</span></span>
 <span data-ttu-id="01138-213">验证 MSOLAP 访问接口。</span><span class="sxs-lookup"><span data-stu-id="01138-213">Verify the provider MSOLAP provider.</span></span> [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]<span data-ttu-id="01138-214">和 [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 需要 MSOLAP. 5。</span><span class="sxs-lookup"><span data-stu-id="01138-214">and [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] require MSOLAP.5.</span></span>

```powershell
$excelApp = Get-SPExcelServiceApplication
Get-SPExcelDataProvider -ExcelServiceApplication $excelApp | Select providerid, providertype, description | Where {$_.providerid -like "msolap*" } | Format-Table -Property * -AutoSize | Out-Default
```

```Output
ProviderId ProviderType Description
---------- ------------ -----------
MSOLAP     Oledb        Microsoft OLE DB Provider for OLAP Services     
MSOLAP.3   Oledb        Microsoft OLE DB Provider for OLAP Services 9.0 
MSOLAP.4   Oledb        Microsoft OLE DB Provider for OLAP Services 10.0
MSOLAP.5   Oledb        Microsoft OLE DB Provider for OLAP Services 11.0
```

 <span data-ttu-id="01138-215">有关详细信息，请参阅 [在 SharePoint 服务器上安装 Analysis Services OLE DB 提供程序](../../../sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md) 和 [将 MSOLAP.5 添加为 Excel Services 中的受信任数据提供程序](https://technet.microsoft.com/library/hh758436.aspx)。</span><span class="sxs-lookup"><span data-stu-id="01138-215">For more information, see [Install the Analysis Services OLE DB Provider on SharePoint Servers](../../../sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md) and [Add MSOLAP.5 as a Trusted Data Provider in Excel Services](https://technet.microsoft.com/library/hh758436.aspx).</span></span>

##  <a name="adomdnet-client-library"></a><a name="bkmk_adomd"></a><span data-ttu-id="01138-216">ADOMD.Net 客户端库</span><span class="sxs-lookup"><span data-stu-id="01138-216">ADOMD.Net client Library</span></span>

```powershell
Get-WMIObject -Class win32_product | Where-Object {$_.name -Like "*ado*"} | Select name, version, vendor | Format-Table -Property * -AutoSize | out-default
```

```Output
name                                                  version      vendor
----                                                  -------      ------
Microsoft SQL Server 2008 Analysis Services ADOMD.NET 10.1.2531.0  Microsoft Corporation
Microsoft SQL Server 2005 Analysis Services ADOMD.NET 9.00.1399.06 Microsoft Corporation
```

 <span data-ttu-id="01138-217">有关详细信息，请参阅 [在运行管理中心的 Web 前端服务器上安装 ADOMD.NET](../../../sql-server/install/install-adomd-net-on-web-front-end-servers-running-central-administration.md)。</span><span class="sxs-lookup"><span data-stu-id="01138-217">For more information, see [Install ADOMD.NET on Web Front-End Servers Running Central Administration](../../../sql-server/install/install-adomd-net-on-web-front-end-servers-running-central-administration.md).</span></span>

##  <a name="health-data-collection-rules"></a><a name="bkmk_health_collection"></a><span data-ttu-id="01138-218">运行状况数据收集规则</span><span class="sxs-lookup"><span data-stu-id="01138-218">Health Data Collection Rules</span></span>
 <span data-ttu-id="01138-219">验证 **“状态”** 是否联机，以及 **“已启用”** 是否为 True。</span><span class="sxs-lookup"><span data-stu-id="01138-219">Verify the **Status** is Online and **Enabled** is True.</span></span>

```powershell
Get-SPUsageDefinition | Select name, status, enabled, tablename, DaysToKeepDetailedData | Where {$_.name -Like "powerpivot*"} | Format-Table -Property * -AutoSize | Out-Default
```

```Output
Name                         Status Enabled TableName                   DaysToKeepDetailedData
----                         ------ ------- ---------                   ----------------------
PowerPivot Connections       OnlineTrue AnalysisServicesConnections  14
PowerPivot Load Data Usage   Online    True AnalysisServicesLoads                           14
PowerPivot Query Usage       Online    True AnalysisServicesRequests                        14
PowerPivot Unload Data Usage Online    True AnalysisServicesUnloads                         14
```

 <span data-ttu-id="01138-220">有关详细信息，请参阅 [PowerPivot Usage Data Collection](../../power-pivot-sharepoint/power-pivot-usage-data-collection.md)。</span><span class="sxs-lookup"><span data-stu-id="01138-220">For more information, see [PowerPivot Usage Data Collection](../../power-pivot-sharepoint/power-pivot-usage-data-collection.md).</span></span>

##  <a name="solutions"></a><a name="bkmk_solutions"></a><span data-ttu-id="01138-221">解决方案</span><span class="sxs-lookup"><span data-stu-id="01138-221">Solutions</span></span>
 <span data-ttu-id="01138-222">如果其他组件联机，则可跳过方案验证的验证。</span><span class="sxs-lookup"><span data-stu-id="01138-222">If the other components are online then you can skip verifying the solutions.</span></span> <span data-ttu-id="01138-223">但是，如果缺少运行状况规则，则需验证这两个解决方案是否存在，并验证两个 PowerPivot 解决方案是否为 **“联机”** 且 **“已部署”**。</span><span class="sxs-lookup"><span data-stu-id="01138-223">If however the Health rules are missing, verify the two solutions exist and showed Verify the two PowerPivot solutions are **Online** and **Deployed**.</span></span>

```powershell
Get-SPSolution | Select name, status, deployed, DeploymentState, DeployedServers | Where {$_.Name -Like "*powerpivot*"} | Format-Table -Property * -AutoSize | Out-Default
```

<span data-ttu-id="01138-224">SharePoint 2013：</span><span class="sxs-lookup"><span data-stu-id="01138-224">SharePoint 2013:</span></span>

```Output
Name                                 Status Deployed        DeploymentState DeployedServers
----                                 ------ --------        --------------- ---------------
powerpivotfarm14solution.wsp         Online     True         GlobalDeployed {UETESTA00}
powerpivotfarmsolution.wsp           Online     True         GlobalDeployed {UETESTA00}
powerpivotwebapplicationsolution.wsp Online     True WebApplicationDeployed {UETESTA00}
```

<span data-ttu-id="01138-225">SharePoint 2010：</span><span class="sxs-lookup"><span data-stu-id="01138-225">SharePoint 2010:</span></span>

```Output
Name                 Status Deployed        DeploymentState DeployedServers 
----                 ------ --------        --------------- --------------- 
powerpivotfarm.wsp   Online     True         GlobalDeployed {uesql11spoint2}
powerpivotwebapp.wsp Online     True WebApplicationDeployed {uesql11spoint2}
```

 <span data-ttu-id="01138-226">有关如何部署 SharePoint 解决方案的详细信息，请参阅 [部署解决方案包 (SharePoint Server 2010)](https://technet.microsoft.com/library/cc262995\(v=office.14\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="01138-226">For more information on how to deploy SharePoint solutions, see [Deploy solution packages (SharePoint Server 2010)](https://technet.microsoft.com/library/cc262995\(v=office.14\).aspx).</span></span>

##  <a name="manual-verification-steps"></a><a name="bkmk_manual"></a><span data-ttu-id="01138-227">手动验证步骤</span><span class="sxs-lookup"><span data-stu-id="01138-227">Manual Verification Steps</span></span>
 <span data-ttu-id="01138-228">本章节介绍无法借由 PowerShell cmdlet 完成的验证步骤。</span><span class="sxs-lookup"><span data-stu-id="01138-228">This section describes verification steps that cannot be completed with PowerShell cmdlets.</span></span>

 <span data-ttu-id="01138-229">**计划的数据刷新：** 将工作簿的刷新计划配置为 **“也尽快刷新”**。</span><span class="sxs-lookup"><span data-stu-id="01138-229">**Scheduled Data Refresh:** Configure the refresh schedule a workbook to **Also refresh as soon as possible**.</span></span>  <span data-ttu-id="01138-230">有关详细信息，请参阅[计划数据刷新和不支持 Windows 身份验证的数据源 &#40;PowerPivot for SharePoint&#41;](../../power-pivot-sharepoint/schedule-data-refresh-and-data-sources-no-windows-authentication.md)的 "验证数据刷新" 一节。</span><span class="sxs-lookup"><span data-stu-id="01138-230">For more information, see the "Verify Data Refresh" section of [Schedule Data Refresh and Data Sources That Do Not Support Windows Authentication &#40;PowerPivot for SharePoint&#41;](../../power-pivot-sharepoint/schedule-data-refresh-and-data-sources-no-windows-authentication.md).</span></span>

##  <a name="more-resources"></a><a name="bkmk_more_resources"></a><span data-ttu-id="01138-231">更多资源</span><span class="sxs-lookup"><span data-stu-id="01138-231">More Resources</span></span>
 <span data-ttu-id="01138-232">[Windows PowerShell 中的 Web 服务器 (IIS) 管理 Cmdlet](https://technet.microsoft.com/library/ee790599.aspx)。</span><span class="sxs-lookup"><span data-stu-id="01138-232">[Web Server (IIS) Administration Cmdlets in Windows PowerShell](https://technet.microsoft.com/library/ee790599.aspx).</span></span>

 <span data-ttu-id="01138-233">[用于检查 SharePoint 中服务、IIS 站点和应用程序池状态的 PowerShell](https://gallery.technet.microsoft.com/office/PowerShell-to-check-a6ed72a0)。</span><span class="sxs-lookup"><span data-stu-id="01138-233">[PowerShell to check services, IIS sites and Application Pool status in SharePoint](https://gallery.technet.microsoft.com/office/PowerShell-to-check-a6ed72a0).</span></span>

 <span data-ttu-id="01138-234">[Windows PowerShell for SharePoint 2013 参考](https://technet.microsoft.com/library/ee890108\(v=office.15\).aspx)</span><span class="sxs-lookup"><span data-stu-id="01138-234">[Windows PowerShell for SharePoint 2013 reference](https://technet.microsoft.com/library/ee890108\(v=office.15\).aspx)</span></span>

 <span data-ttu-id="01138-235">[Windows PowerShell for SharePoint Foundation 2010 参考](https://technet.microsoft.com/library/ee890105\(v=office.14\).aspx)</span><span class="sxs-lookup"><span data-stu-id="01138-235">[Windows PowerShell for SharePoint Foundation 2010 reference](https://technet.microsoft.com/library/ee890105\(v=office.14\).aspx)</span></span>

 <span data-ttu-id="01138-236">[使用 Windows PowerShell 管理 Excel Services (SharePoint Server 2010)](https://technet.microsoft.com/library/ff191201\(v=office.14\).aspx)</span><span class="sxs-lookup"><span data-stu-id="01138-236">[Manage Excel Services with Windows PowerShell (SharePoint Server 2010)](https://technet.microsoft.com/library/ff191201\(v=office.14\).aspx)</span></span>

 [<span data-ttu-id="01138-237">查看和读取 SQL Server 安装程序日志文件</span><span class="sxs-lookup"><span data-stu-id="01138-237">View and Read SQL Server Setup Log Files</span></span>](../../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)

 [<span data-ttu-id="01138-238">使用 Get-EvenLog cmdlet</span><span class="sxs-lookup"><span data-stu-id="01138-238">Use the Get-EvenLog cmdlet</span></span>](https://technet.microsoft.com/library/ee176846.aspx)

##  <a name="full-powershell-script"></a><a name="bkmk_full_script"></a><span data-ttu-id="01138-239">完整的 PowerShell 脚本</span><span class="sxs-lookup"><span data-stu-id="01138-239">Full PowerShell Script</span></span>
 <span data-ttu-id="01138-240">下面的脚本包含上述章节的所有命令。</span><span class="sxs-lookup"><span data-stu-id="01138-240">The Following script contains all of the commands from the previous sections.</span></span> <span data-ttu-id="01138-241">此脚本以本主题中显示的顺序运行命令。</span><span class="sxs-lookup"><span data-stu-id="01138-241">The script runs the commands in the same order as they are presented in this topic.</span></span> <span data-ttu-id="01138-242">此脚本包含本主题中提到的某些可选命令变体，方便您在需要其他筛选条件时使用。</span><span class="sxs-lookup"><span data-stu-id="01138-242">The script contains some optional variations of the commands noted in this topic in case you need additional filtering.</span></span> <span data-ttu-id="01138-243">变体已用注释字符 (#) 禁用。</span><span class="sxs-lookup"><span data-stu-id="01138-243">The variations are disabled with a comment character (#).</span></span> <span data-ttu-id="01138-244">此脚本还包含某些验证 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] SharePoint 模式的语句。</span><span class="sxs-lookup"><span data-stu-id="01138-244">The script also includes some statements for verifying [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] SharePoint mode.</span></span> <span data-ttu-id="01138-245">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 语句已用注释字符 (#) 禁用。</span><span class="sxs-lookup"><span data-stu-id="01138-245">The [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] statements are disabled with a comment character (#).</span></span>

```powershell
# This script audits services related to PowerPivot for SharePoint
$starttime = Get-Date
write-host -foregroundcolor DarkGray StartTime $starttime

Write-Host  "Import the SharePoint PowerShell snappin"
Add-PSSnapin Microsoft.Sharepoint.Powershell -EA 0

Write-Host -ForegroundColor Green "Analysis Services Windows Service"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-Service | Select name, displayname, status | Where {$_.Name -eq "msolap`$powerpivot"} | Format-Table -Property * -AutoSize | Out-Default

Write-Host -ForegroundColor Green "PowerPivotEngineService and PowerPivotSystemService"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"

Get-PowerPivotSystemService | Select typename, status, applications, farm | Format-Table -property * -AutoSize | Out-Default
# If needed, you can run the following to compare job definitions specific to the service against the results of the timer job definition section
#Get-PowerPivotSystemService | select -ExpandProperty jobdefinitions | select displayname, schedule, service | format-table -property * -autosize | out-default

Get-PowerPivotEngineService | Select typename, status, name, instances, farm | Format-Table -property * -AutoSize | Out-Default
# If needed, you can run the following to compare job definitions specific to the service against the results of the timer job definition section
#Get-PowerPivotEngineService | select -ExpandProperty jobdefinitions | select displayname, schedule, service | format-table -property * -autosize | out-default

#Write-Host -ForegroundColor Green "Service Instances - optional if you want to associate services with the server"
#Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
#Get-SPServiceInstance | select typename, status, server, service, instance | where {$_.TypeName -like "*powerpivot*" -or $_.TypeName -like "*excel*" -or $_.TypeName -like "*Analysis Services*"} | format-table -property * -autosize | out-default
#Get-PowerPivotEngineServiceInstance  | select typename, ASServername, status, server, service, instance
#Get-PowerPivotSystemServiceInstance  | select typename, ASSServerName, status, server, service, instance

Write-Host -ForegroundColor Green "PowerPivot And Excel Service Applications"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-PowerPivotServiceApplication | Select typename,name, status, unattendedaccount, applicationpool, farm, database
Get-SPExcelServiceApplication | Select typename,  DisplayName, status

#Write-Host ""
Write-Host -ForegroundColor Green "PowerPivot Service Application pool"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
# the following assumes there is only 1 PowerPivot Service Application, and returns that application's pool name.  if you have more than one, use the 2nd version
$poolname = [string](Get-PowerPivotServiceApplication | Select -Property applicationpool)
$position = $poolname.lastindexof("=")
$poolname = $poolname.substring($position+1)
$poolname = $poolname.substring(0,$poolname.length-1)
Get-SPServiceApplicationPool | Select name, status, processaccountname, id | Where {$_.Name -eq $poolname} | Format-Table -Property * -AutoSize | Out-Default

#Write-Host ""
Write-Host -ForegroundColor Green "PowerPivot and Excel Service Application Proxy"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-SPServiceApplicationProxy |  Select typename, status, unattendedaccount, displayname | Where {$_.TypeName -like "*powerpivot*" -or $_.TypeName -like "*excel services*"} | Format-Table -Property * -AutoSize | Out-Default
#Get-SPServiceApplicationProxy |  select typename, status, unattendedaccount, displayname | where {$_.TypeName -like "*powerpivot*" -or $_.TypeName -like "*Reporting Services*" -or $_.TypeName -like "*excel services*"} | format-table -property * -autosize | out-default

Write-Host -ForegroundColor Green "DATABASES"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-SPDatabase | Select name, status, server, typename | Where {$_.TypeName -eq "content database" -or $_.TypeName -like "*Gemini*"} | Format-Table -Property * -AutoSize | Out-Default
#Get-SPDatabase | select name, status, server, typename | where {$_.TypeName -eq "content database" -or $_.TypeName -like "*Gemini*" -or $_.TypeName -like "*ReportingServices*"}

Write-Host -ForegroundColor Green "features"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-SPFeature | Select displayname, status, scope, farm | Where {$_.displayName -like "*powerpivot*"} | Format-Table -Property * -AutoSize | Out-Default
#Get-SPFeature | select displayname, status, scope, farm | where {$_.displayName -like "*powerpivot*" -or $_.displayName -like "*ReportServer*"}  | format-table -property * -autosize | out-default

Write-Host -ForegroundColor Green "Timer Jobs (Job Definitions) -- list is the same as seen in the 'Review timer job definitions' section of the management dashboard"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-SPTimerJob | Where {$_.service -like "*power*" -or $_.service -like "*mid*"} | Select status, displayname, LastRunTime, service | Format-Table -Property * -AutoSize | Out-Default

Write-Host -ForegroundColor Green "health rules"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-SPHealthAnalysisRule | Select name, enabled, summary | Where {$_.summary -Like "*power*"}  | Format-Table -Property * -AutoSize | Out-Default

$time = Get-Date
Write-Host -ForegroundColor DarkGray StartTime $starttime
Write-Host -ForegroundColor DarkGray EndTime $time

Write-Host -ForegroundColor Green "Windows Event Log data MSSQL$POWERPIVOT and "
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-EventLog "application" | Where-Object {$_.source -like "msolap`$powerpivot*"}  | Select timegenerated, entrytype , source, message | Format-Table -Property * -autosize | Out-Default
#The following is the same command but with the Inforamtion events filtered out.
#Get-EventLog "application" | Where-Object {$_.source -like "msolap`$powerpivot*" -and ($_.entrytype -match "error" -or $_.entrytype -match "critical" -or $_.entrytype -match "warning")}  |select timegenerated, entrytype , source, message | format-table -property * -autosize | out-default

#Write-Host ""
Write-Host -ForegroundColor Green "ULS Log data"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-SPLogEvent -StartTime(Get-Date).AddHours(-48) | Where-Object {$_.Area -eq "powerpivot service" -and $_.level -eq "high"} | Select timestamp, area, category, eventid, level, correlation, message | Format-Table -Property * -AutoSize | Out-Default
#the following example filters for the category 'data refresh'
#Get-SPLogEvent -starttime(get-date).addhours(-48) | Where-Object {$_.category -eq "data refresh" -and $_.level -eq "high"} | select timestamp, area, category, eventid, level, correlation, message

$time = Get-Date
Write-Host -ForegroundColor DarkGray StartTime $starttime
Write-Host -ForegroundColor DarkGray EndTime $time

Write-Host -ForegroundColor Green "MSOLAP data provider for Excel Servivces, service application"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
$excelApp = Get-SPExcelServiceApplication
Get-SPExcelDataProvider -ExcelServiceApplication $excelApp | Select providerid, providertype, description | Where {$_.providerid -like "msolap*" } | Format-Table -Property * -AutoSize | Out-Default

Write-Host -ForegroundColor Green "ADOMD.net client library"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-WMIObject -Class win32_product | Where-Object {$_.name -like "*ado*"} | Select name, version, vendor | Format-Table -Property * -AutoSize | Out-Default

Write-Host -ForegroundColor Green "Usage Data Rules"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-SPUsageDefinition | Select name, status, enabled, tablename, DaysToKeepDetailedData | Where {$_.name -like "powerpivot*"} | Format-Table -Property * -AutoSize | Out-Default

Write-Host -ForegroundColor Green "Solutions"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-SPSolution | Select name, status, deployed, DeploymentState, DeployedServers | Where {$_.Name -like "*powerpivot*"} | Format-Table -Property * -AutoSize | Out-Default

$time = Get-Date
Write-Host -ForegroundColor DarkGray StartTime $starttime
Write-Host -ForegroundColor DarkGray EndTime $time
```
