---
title: "\"站点设置\" 页 (报表管理器) |Microsoft Docs"
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4d67a01c-eae4-49ba-a6e8-8e983c0248f5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 75805a4e30293195b23cd5b75f1de3a01a1e76d6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689271"
---
# <a name="site-settings-page-report-manager"></a><span data-ttu-id="26d3a-102">“站点设置”页（报表管理器）</span><span class="sxs-lookup"><span data-stu-id="26d3a-102">Site Settings Page (Report Manager)</span></span>
  <span data-ttu-id="26d3a-103">使用“站点设置”页可以更改应用程序标题，为报表历史记录限制和报表处理超时值设置服务器范围的默认值，管理系统级角色分配以及管理共享计划。</span><span class="sxs-lookup"><span data-stu-id="26d3a-103">Use the Site Settings page to change the application title, set server-wide defaults for report history limits and report processing timeout values, manage system-level role assignments, and manage shared schedules.</span></span> <span data-ttu-id="26d3a-104">必须拥有“内容管理员”和“系统管理员”权限才能查看此页。</span><span class="sxs-lookup"><span data-stu-id="26d3a-104">You must have Content Manager and System Administrator permissions to view this page.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="26d3a-105">并非在 SQL Server 的每个版本中均提供以下功能：报表历史记录、报表执行和共享计划。</span><span class="sxs-lookup"><span data-stu-id="26d3a-105">The following features are not available in every edition of SQL Server: report history, report execution, and shared schedules.</span></span> <span data-ttu-id="26d3a-106">有关各个版本支持的功能列表 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ，请参阅 SQL Server 2014 的各个[版本支持的功能](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="26d3a-106">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="26d3a-107">导航</span><span class="sxs-lookup"><span data-stu-id="26d3a-107">Navigation</span></span>  
 <span data-ttu-id="26d3a-108">使用以下过程导航到用户界面 (UI) 中的这一位置。</span><span class="sxs-lookup"><span data-stu-id="26d3a-108">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
### <a name="to-open-the-site-settings-page"></a><span data-ttu-id="26d3a-109">打开“站点设置”页</span><span class="sxs-lookup"><span data-stu-id="26d3a-109">To open the Site Settings page</span></span>  
  
1.  <span data-ttu-id="26d3a-110">打开报表管理器。</span><span class="sxs-lookup"><span data-stu-id="26d3a-110">Open Report Manager.</span></span>  
  
2.  <span data-ttu-id="26d3a-111">单击页面顶部的 **“站点设置”**。</span><span class="sxs-lookup"><span data-stu-id="26d3a-111">At the top of the page, click **Site Settings**.</span></span> <span data-ttu-id="26d3a-112">这会打开该站点的“常规属性”页。</span><span class="sxs-lookup"><span data-stu-id="26d3a-112">This opens the General Properties page of the site.</span></span>  
  
     <span data-ttu-id="26d3a-113">**注意：** 如果在菜单中看不到 "**站点设置**" 选项，则没有所需的权限。有关详细信息，请参阅为[本地管理配置本机模式报表服务器 &#40;SSRS&#41;](report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md)中的 "站点设置" 部分。</span><span class="sxs-lookup"><span data-stu-id="26d3a-113">**Note:** If you do not see the **Site Settings** option in the menu, you do not have the required permissions, For more information see the "site settings" section of [Configure a Native Mode Report Server for Local Administration &#40;SSRS&#41;](report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="26d3a-114">选项</span><span class="sxs-lookup"><span data-stu-id="26d3a-114">Options</span></span>  
 <span data-ttu-id="26d3a-115">**名称**</span><span class="sxs-lookup"><span data-stu-id="26d3a-115">**Name**</span></span>  
 <span data-ttu-id="26d3a-116">指定用于此 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 报表管理器实例的标题。</span><span class="sxs-lookup"><span data-stu-id="26d3a-116">Specify the title to use for this instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Report Manager.</span></span> <span data-ttu-id="26d3a-117">默认情况下，标题为 " [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] "。</span><span class="sxs-lookup"><span data-stu-id="26d3a-117">By default, the title is "[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]".</span></span>  
  
 <span data-ttu-id="26d3a-118">**选择报表历史记录的默认设置**</span><span class="sxs-lookup"><span data-stu-id="26d3a-118">**Select the default settings for report history**</span></span>  
 <span data-ttu-id="26d3a-119">为要保留的报表历史副本数选择默认值。</span><span class="sxs-lookup"><span data-stu-id="26d3a-119">Select a default value for the number of copies of report history to retain.</span></span> <span data-ttu-id="26d3a-120">此默认值为报表历史记录的相关限制提供了初始设置。</span><span class="sxs-lookup"><span data-stu-id="26d3a-120">The default value provides an initial setting that establishes report history limits.</span></span> <span data-ttu-id="26d3a-121">您可以在报表级别更改这些设置。</span><span class="sxs-lookup"><span data-stu-id="26d3a-121">You can vary these settings at the report level.</span></span> <span data-ttu-id="26d3a-122">有关详细信息，请参阅[“快照选项”属性页（报表管理器）](../../2014/reporting-services/snapshot-options-properties-page-report-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="26d3a-122">For more information, see [Snapshot Options Properties Page &#40;Report Manager&#41;](../../2014/reporting-services/snapshot-options-properties-page-report-manager.md).</span></span>  
  
 <span data-ttu-id="26d3a-123">如果以后限制报表历史记录，则在现有的报表历史记录超出您指定的限制时，报表服务器将减少现有的报表历史记录以符合新限制。</span><span class="sxs-lookup"><span data-stu-id="26d3a-123">If you limit report history later, when the existing report history exceeds the limit you specify, the report server reduces the existing report history to the new limit.</span></span> <span data-ttu-id="26d3a-124">首先删除最旧的报表快照。</span><span class="sxs-lookup"><span data-stu-id="26d3a-124">The oldest report snapshots are deleted first.</span></span> <span data-ttu-id="26d3a-125">如果报表历史为空或者低于限制，则添加新的报表快照。</span><span class="sxs-lookup"><span data-stu-id="26d3a-125">If report history is empty or below the limit, new report snapshots are added.</span></span> <span data-ttu-id="26d3a-126">到达限制后，将在添加新的报表快照时删除时间最早的快照。</span><span class="sxs-lookup"><span data-stu-id="26d3a-126">When the limit is reached, the oldest snapshot is deleted when a new report snapshot is added.</span></span>  
  
 <span data-ttu-id="26d3a-127">**报表执行超时**</span><span class="sxs-lookup"><span data-stu-id="26d3a-127">**Report Execution Timeout**</span></span>  
 <span data-ttu-id="26d3a-128">指定在给定的秒数之后报表处理是否超时。</span><span class="sxs-lookup"><span data-stu-id="26d3a-128">Specify whether report processing times out after a certain number of seconds.</span></span>  
  
 <span data-ttu-id="26d3a-129">此值应用于报表服务器上的报表处理。</span><span class="sxs-lookup"><span data-stu-id="26d3a-129">This value applies to report processing on a report server.</span></span> <span data-ttu-id="26d3a-130">它不会影响为报表提供数据的数据库服务器上的数据处理。</span><span class="sxs-lookup"><span data-stu-id="26d3a-130">It does not affect data processing on the database server that provides the data for your report.</span></span>  
  
 <span data-ttu-id="26d3a-131">报表处理计时器时钟在您选择报表时开始运行，而在报表打开时结束运行。</span><span class="sxs-lookup"><span data-stu-id="26d3a-131">The report processing timer clock begins when the report is selected and ends when the report opens.</span></span> <span data-ttu-id="26d3a-132">设置该值时，请指定足够的时间以完成数据处理和报表处理。</span><span class="sxs-lookup"><span data-stu-id="26d3a-132">When you set this value, specify enough time to complete both data processing and report processing.</span></span>  
  
 <span data-ttu-id="26d3a-133">**自定义报表生成器启动 URL**</span><span class="sxs-lookup"><span data-stu-id="26d3a-133">**Custom Report Builder launch URL**</span></span>  
 <span data-ttu-id="26d3a-134">当报表服务器不使用默认报表生成器 URL 时，可指定自定义 URL。</span><span class="sxs-lookup"><span data-stu-id="26d3a-134">Specify a custom URL when the report server does not use the default Report Builder URL.</span></span> <span data-ttu-id="26d3a-135">此设置是可选的。</span><span class="sxs-lookup"><span data-stu-id="26d3a-135">This setting is optional.</span></span> <span data-ttu-id="26d3a-136">如果不指定值，将使用默认 URL，此时报表生成器将作为 ClickOnce 应用程序启动。</span><span class="sxs-lookup"><span data-stu-id="26d3a-136">If you do not specify a value, the default URL will be used, which launches Report Builder as a ClickOnce application.</span></span> <span data-ttu-id="26d3a-137">默认 URL 为下列值之一：</span><span class="sxs-lookup"><span data-stu-id="26d3a-137">The default URL is one of the following:</span></span>  
  
 <span data-ttu-id="26d3a-138">**本机模式 Report Server：** 在本机模式安装中，默认 URL 将采用 http://ReportBuilder_3_0_0_0/Reportserver/reportbuilder/的形式 \<*computername*> 。</span><span class="sxs-lookup"><span data-stu-id="26d3a-138">**Native mode report server:** In a native mode installation, the default URL will take the form of http://\<*computername*>/reportserver/ReportBuilder/ReportBuilder_3_0_0_0.application.</span></span>  
  
 <span data-ttu-id="26d3a-139">SharePoint 集成模式：默认 URL 将采用 http:// \<*SharePoint_site*> /_vti_bin ReportBuilder_3_0_0_0/reportbuilder/的形式。</span><span class="sxs-lookup"><span data-stu-id="26d3a-139">SharePoint integrated mode: The default URL will take the form of http://\<*SharePoint_site*>/_vti_bin/ReportBuilder/ReportBuilder_3_0_0_0.application."</span></span>  
  
 <span data-ttu-id="26d3a-140">**应用**</span><span class="sxs-lookup"><span data-stu-id="26d3a-140">**Apply**</span></span>  
 <span data-ttu-id="26d3a-141">单击此选项可保存对报表服务器所做的更改。</span><span class="sxs-lookup"><span data-stu-id="26d3a-141">Click to save your changes to the report server.</span></span>  
  
 <span data-ttu-id="26d3a-142">**安全性**</span><span class="sxs-lookup"><span data-stu-id="26d3a-142">**Security**</span></span>  
 <span data-ttu-id="26d3a-143">单击此链接可打开“系统角色分配”页，在该页可以向预定义的系统角色分配用户和组帐户。</span><span class="sxs-lookup"><span data-stu-id="26d3a-143">Click this link to open the System Role Assignments page, on which you can assign user and group accounts to predefined system roles.</span></span>  
  
 <span data-ttu-id="26d3a-144">**计划**</span><span class="sxs-lookup"><span data-stu-id="26d3a-144">**Schedules**</span></span>  
 <span data-ttu-id="26d3a-145">单击此链接将打开“计划”页，在该页可以预定义供用户选择以用于其报表和订阅的共享计划。</span><span class="sxs-lookup"><span data-stu-id="26d3a-145">Click this link to open the Schedules page, on which you can predefine shared schedules that users can select for their reports and subscriptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26d3a-146">另请参阅</span><span class="sxs-lookup"><span data-stu-id="26d3a-146">See Also</span></span>  
 <span data-ttu-id="26d3a-147">[报表管理器（SSRS 本机模式）](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="26d3a-147">[Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="26d3a-148">[授予对本机模式报表服务器的权限](security/granting-permissions-on-a-native-mode-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="26d3a-148">[Granting Permissions on a Native Mode Report Server](security/granting-permissions-on-a-native-mode-report-server.md) </span></span>  
 <span data-ttu-id="26d3a-149">[预定义角色](security/role-definitions-predefined-roles.md) </span><span class="sxs-lookup"><span data-stu-id="26d3a-149">[Predefined Roles](security/role-definitions-predefined-roles.md) </span></span>  
 [<span data-ttu-id="26d3a-150">报表管理器的 F1 帮助</span><span class="sxs-lookup"><span data-stu-id="26d3a-150">Report Manager F1 Help</span></span>](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
