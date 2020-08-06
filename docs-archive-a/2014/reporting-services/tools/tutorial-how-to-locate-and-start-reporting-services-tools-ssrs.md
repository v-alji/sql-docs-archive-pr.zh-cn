---
title: 教程：如何查找并启动 Reporting Services 工具 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Report Builder 1.0, locating and starting tool
- Reporting Services, tutorials
- Reporting Services, tools
- Reporting Services Configuration tool
- Business Intelligence Development Studio, locating and starting tool
- Model Designer [Reporting Services], locating and starting tool
- Report Designer [Reporting Services], tutorials
- tools [Reporting Services]
- tutorials [Reporting Services]
- Report Manager [Reporting Services]
ms.assetid: 51ad69d8-fe92-4662-a7cd-d235692f0c03
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2b7a981a53378ea6b37959e891cac8bd891c2578
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691563"
---
# <a name="tutorial-how-to-locate-and-start-reporting-services-tools-ssrs"></a><span data-ttu-id="e3538-102">教程：如何查找并启动 Reporting Services 工具 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="e3538-102">Tutorial: How to Locate and Start Reporting Services Tools (SSRS)</span></span>
  <span data-ttu-id="e3538-103">该教程介绍了用于配置报表服务器、管理报表服务器内容和操作以及创建与发布报表的工具。</span><span class="sxs-lookup"><span data-stu-id="e3538-103">This tutorial introduces the tools used to configure a report server, manage report server content and operations, and create and publish reports.</span></span> <span data-ttu-id="e3538-104">本教程旨在于帮助新用户了解如何查找和打开各个工具。</span><span class="sxs-lookup"><span data-stu-id="e3538-104">The purpose of this tutorial is to help new users understand how to find and open each tool.</span></span> <span data-ttu-id="e3538-105">如果您已经熟悉了这些工具，您可以转到其他教程学习有关使用 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]的重要技能。</span><span class="sxs-lookup"><span data-stu-id="e3538-105">If you are already familiar with the tools, you can move on to other tutorials that can help you learn important skills for using [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="e3538-106">有关其他教程的详细信息，请参阅[&#40;SSRS&#41;Reporting Services 教程](../reporting-services-tutorials-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="e3538-106">For more information about other tutorials, see [Reporting Services Tutorials &#40;SSRS&#41;](../reporting-services-tutorials-ssrs.md).</span></span>  
  
 <span data-ttu-id="e3538-107">本主题内容：</span><span class="sxs-lookup"><span data-stu-id="e3538-107">In this topic:</span></span>  
  
-   [<span data-ttu-id="e3538-108">Reporting Services 配置管理器（本机节点）</span><span class="sxs-lookup"><span data-stu-id="e3538-108">Reporting Services Configuration Manager (Native Mode)</span></span>](#bkmk_configuration_manager)  
  
-   [<span data-ttu-id="e3538-109">报表管理器（本机模式）</span><span class="sxs-lookup"><span data-stu-id="e3538-109">Report Manager (Native Mode)</span></span>](#bkmk_report_manager)  
  
-   [<span data-ttu-id="e3538-110">Management Studio</span><span class="sxs-lookup"><span data-stu-id="e3538-110">Management Studio</span></span>](#bkmk_managements_studio)  
  
-   [<span data-ttu-id="e3538-111">具有报表设计器和报表向导的 SQL Server Data Tools</span><span class="sxs-lookup"><span data-stu-id="e3538-111">SQL Server Data Tools with Report Designer and Report Wizard</span></span>](#bkmk_ssdt)  
  
-   [<span data-ttu-id="e3538-112">报表生成器</span><span class="sxs-lookup"><span data-stu-id="e3538-112">Report Builder</span></span>](#bkmk_report_builder)  
  
##  <a name="reporting-services-configuration-manager-native-mode"></a><a name="bkmk_configuration_manager"></a> <span data-ttu-id="e3538-113">(本机模式下 Reporting Services 配置管理器) </span><span class="sxs-lookup"><span data-stu-id="e3538-113">Reporting Services Configuration Manager (Native Mode)</span></span>  
 <span data-ttu-id="e3538-114">使用本机模式配置管理器完成以下任务： 、 、 、 、 和 。</span><span class="sxs-lookup"><span data-stu-id="e3538-114">Use the Native mode configuration manager to complete the following:, , , , , and.</span></span>  
  
-   <span data-ttu-id="e3538-115">指定服务帐户。</span><span class="sxs-lookup"><span data-stu-id="e3538-115">Specify the service account.</span></span>  
  
-   <span data-ttu-id="e3538-116">创建或升级报表服务器数据库。</span><span class="sxs-lookup"><span data-stu-id="e3538-116">Create or upgrade the report server database.</span></span>  
  
-   <span data-ttu-id="e3538-117">修改连接属性。</span><span class="sxs-lookup"><span data-stu-id="e3538-117">Modify the connection properties.</span></span>  
  
-   <span data-ttu-id="e3538-118">指定 URL。</span><span class="sxs-lookup"><span data-stu-id="e3538-118">Specify URLs.</span></span>  
  
-   <span data-ttu-id="e3538-119">管理加密密钥。</span><span class="sxs-lookup"><span data-stu-id="e3538-119">Manage encryption keys.</span></span>  
  
-   <span data-ttu-id="e3538-120">配置无人参与的报表处理和电子邮件报表传递。</span><span class="sxs-lookup"><span data-stu-id="e3538-120">Configure unattended report processing and e-mail report delivery.</span></span>  
  
 <span data-ttu-id="e3538-121">**安装：** [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 本机模式时会安装 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 配置管理器。</span><span class="sxs-lookup"><span data-stu-id="e3538-121">**Installation:** [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Configuration Manager is installed when you install [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Native mode.</span></span> <span data-ttu-id="e3538-122">有关详细信息，请参阅 [安装 Reporting Services 本机模式报表服务器](../install-windows/install-reporting-services-native-mode-report-server.md)</span><span class="sxs-lookup"><span data-stu-id="e3538-122">For more information, see [Install Reporting Services Native Mode Report Server](../install-windows/install-reporting-services-native-mode-report-server.md)</span></span>  
  
#### <a name="to-start-the-reporting-services-configuration-manager"></a><span data-ttu-id="e3538-123">启动 Reporting Services 配置管理器</span><span class="sxs-lookup"><span data-stu-id="e3538-123">To start the Reporting Services Configuration Manager</span></span>  
  
1.  <span data-ttu-id="e3538-124">在 Windows 的 "开始" 屏幕上，键入， `reporting` 然后在 "**应用**" 搜索结果中，单击 " **Reporting Services 配置管理器**"。</span><span class="sxs-lookup"><span data-stu-id="e3538-124">On the Windows start screen, type `reporting` and in the **Apps** search results, click **Reporting Services Configuration Manager**.</span></span>  
  
     <span data-ttu-id="e3538-125">![“开始”屏幕中的 Reporting Services 配置管理器](../media/bi-ssrs-configmanager-win8-startscreen.gif "“开始”屏幕中的 Reporting Services 配置管理器")</span><span class="sxs-lookup"><span data-stu-id="e3538-125">![reporting services configuration manager on start](../media/bi-ssrs-configmanager-win8-startscreen.gif "reporting services configuration manager on start")</span></span>  
  
     <span data-ttu-id="e3538-126">**Or**</span><span class="sxs-lookup"><span data-stu-id="e3538-126">**Or**</span></span>  
  
     <span data-ttu-id="e3538-127">单击 **“开始”**，然后依次单击 **“程序”**、“ [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)]”、 **“配置工具”**、 **“Reporting Services 配置管理器”**。</span><span class="sxs-lookup"><span data-stu-id="e3538-127">Click **Start**, then click **Programs**, then click [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)], then click **Configuration Tools**, and then click **Reporting Services Configuration Manager**.</span></span>  
  
     <span data-ttu-id="e3538-128">此时将出现 **“选择报表服务器安装实例”** 对话框，可以选择要配置的报表服务器实例。</span><span class="sxs-lookup"><span data-stu-id="e3538-128">The **Report Server Installation Instance Selection** dialog box appears so that you can select the report server instance you want to configure.</span></span>  
  
2.  <span data-ttu-id="e3538-129">在 **“服务器名称”** 中，指定安装报表服务器实例的计算机的名称。</span><span class="sxs-lookup"><span data-stu-id="e3538-129">In **Server Name**, specify the name of the computer on which the report server instance is installed.</span></span> <span data-ttu-id="e3538-130">指定的默认值是本地计算机名称，但也可以键入远程 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例的名称。</span><span class="sxs-lookup"><span data-stu-id="e3538-130">The name of the local computer is specified by default, but you can also type the name of a remote [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance.</span></span>  
  
     <span data-ttu-id="e3538-131">如果指定远程计算机，请单击 **“查找”** 以建立一个连接。</span><span class="sxs-lookup"><span data-stu-id="e3538-131">If you specify a remote computer, click **Find** to establish a connection.</span></span> <span data-ttu-id="e3538-132">必须事先配置报表服务器，以便进行远程管理。</span><span class="sxs-lookup"><span data-stu-id="e3538-132">The report server must be configured for remote administration in advance.</span></span> <span data-ttu-id="e3538-133">有关详细信息，请参阅 [配置报表服务器以进行远程管理](../report-server/configure-a-report-server-for-remote-administration.md)。</span><span class="sxs-lookup"><span data-stu-id="e3538-133">For more information, see [Configure a Report Server for Remote Administration](../report-server/configure-a-report-server-for-remote-administration.md).</span></span>  
  
3.  <span data-ttu-id="e3538-134">在“实例名称”\*\*\*\* 中，选择要配置的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="e3538-134">In **Instance Name**, choose the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] instance that you want to configure.</span></span> <span data-ttu-id="e3538-135">列表中只显示 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]和 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 报表服务器实例。</span><span class="sxs-lookup"><span data-stu-id="e3538-135">Only [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], and [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] report server instances appear in the list.</span></span> <span data-ttu-id="e3538-136">不能配置较早版本的 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e3538-136">You cannot configure earlier versions of [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>  
  
4.  <span data-ttu-id="e3538-137">单击“连接” 。</span><span class="sxs-lookup"><span data-stu-id="e3538-137">Click **Connect**.</span></span>  
  
5.  <span data-ttu-id="e3538-138">若要验证是否已启动工具，请将您的结果与下图进行比较：</span><span class="sxs-lookup"><span data-stu-id="e3538-138">To verify that you launched the tool, compare your results to the following image:</span></span>  
  
     <span data-ttu-id="e3538-139">![Reporting Services 配置工具](../media/rs-ui-reportserverconfigkatmai.gif "Reporting Services 配置工具")</span><span class="sxs-lookup"><span data-stu-id="e3538-139">![Reporting Services Configuration tool](../media/rs-ui-reportserverconfigkatmai.gif "Reporting Services Configuration tool")</span></span>  
  
 <span data-ttu-id="e3538-140">**后续步骤：** [配置和管理报表服务器（SSRS 本机模式）](../report-server/configure-and-administer-a-report-server-ssrs-native-mode.md)和 [Reporting Services Configuration Manager（本机模式）](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="e3538-140">**Next Steps:** [Configure and Administer a Report Server &#40;SSRS Native Mode&#41;](../report-server/configure-and-administer-a-report-server-ssrs-native-mode.md) and [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
##  <a name="report-manager-native-mode"></a><a name="bkmk_report_manager"></a> <span data-ttu-id="e3538-141">(本机模式下报表管理器) </span><span class="sxs-lookup"><span data-stu-id="e3538-141">Report Manager (Native Mode)</span></span>  
 <span data-ttu-id="e3538-142">使用[报表管理器 &#40;SSRS 本机模式&#41;](../report-manager-ssrs-native-mode.md)设置权限、管理订阅和计划以及处理报表。</span><span class="sxs-lookup"><span data-stu-id="e3538-142">Use [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md) to set permissions, manage subscriptions and schedules, and work with reports.</span></span> <span data-ttu-id="e3538-143">也可以使用报表管理器来查看报表。</span><span class="sxs-lookup"><span data-stu-id="e3538-143">You can also use Report Manager to view reports.</span></span>  
  
 <span data-ttu-id="e3538-144">**安装：** 安装本机模式时安装报表管理器 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] ：[安装 Reporting Services 本机模式报表服务器](../install-windows/install-reporting-services-native-mode-report-server.md)</span><span class="sxs-lookup"><span data-stu-id="e3538-144">**Installation:** Report Manager Is installed when you install [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Native mode: [Install Reporting Services Native Mode Report Server](../install-windows/install-reporting-services-native-mode-report-server.md)</span></span>  
  
 <span data-ttu-id="e3538-145">必须拥有足够的权限才能打开报表管理器（最初，只有本地 Administrators 组的成员拥有访问报表管理器功能的权限）。</span><span class="sxs-lookup"><span data-stu-id="e3538-145">Before you can open Report Manager, you must have sufficient permissions (initially, only members of the local Administrators group have permissions that provide access to Report Manager features).</span></span> <span data-ttu-id="e3538-146">报表管理器根据当前用户的角色分配提供不同的页和选项。</span><span class="sxs-lookup"><span data-stu-id="e3538-146">Report Manager provides different pages and options depending on the role assignments of the current user.</span></span> <span data-ttu-id="e3538-147">没有权限的用户将得到一个空页。</span><span class="sxs-lookup"><span data-stu-id="e3538-147">Users who have no permissions will get an empty page.</span></span> <span data-ttu-id="e3538-148">拥有查看报表权限的用户将获得链接，用户点击这些链接可以打开报表。</span><span class="sxs-lookup"><span data-stu-id="e3538-148">Users with permissions to view reports will get links that they can click to open the reports.</span></span> <span data-ttu-id="e3538-149">若要了解有关权限的详细信息，请参阅[角色和权限 (Reporting Services)](../security/roles-and-permissions-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="e3538-149">To learn more about permissions, see [Roles and Permissions &#40;Reporting Services&#41;](../security/roles-and-permissions-reporting-services.md).</span></span>  
  
#### <a name="to-start-report-manager"></a><span data-ttu-id="e3538-150">启动报表管理器</span><span class="sxs-lookup"><span data-stu-id="e3538-150">To start Report Manager</span></span>  
  
1.  <span data-ttu-id="e3538-151">打开浏览器。</span><span class="sxs-lookup"><span data-stu-id="e3538-151">Open your browser.</span></span> <span data-ttu-id="e3538-152">有关支持的浏览器和浏览器版本的信息，请参阅[规划 Reporting Services 和 Power View 浏览器支持 &#40;Reporting Services 2014&#41;](../browser-support-for-reporting-services-and-power-view.md)。</span><span class="sxs-lookup"><span data-stu-id="e3538-152">For information on supported browsers and browser versions, see [Planning for Reporting Services and Power View Browser Support &#40;Reporting Services 2014&#41;](../browser-support-for-reporting-services-and-power-view.md).</span></span>  
  
2.  <span data-ttu-id="e3538-153">在 Web 浏览器的地址栏中，键入报表管理器 URL。</span><span class="sxs-lookup"><span data-stu-id="e3538-153">In the address bar of the Web browser, type the Report Manager URL.</span></span> <span data-ttu-id="e3538-154">默认情况下，URL 是**http:// \<serverName> /reports**。</span><span class="sxs-lookup"><span data-stu-id="e3538-154">By default, the URL is **http://\<serverName>/reports**.</span></span> <span data-ttu-id="e3538-155">可以使用 Reporting Services 配置工具确认服务器名称和 URL。</span><span class="sxs-lookup"><span data-stu-id="e3538-155">You can use the Reporting Services Configuration tool to confirm the server name and URL.</span></span> <span data-ttu-id="e3538-156">有关 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中使用的 URL 的详细信息，请参阅[配置报表服务器 URL（SSRS 配置管理器）](../install-windows/configure-report-server-urls-ssrs-configuration-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="e3538-156">For more information about URLs used in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], see [Configure Report Server URLs  &#40;SSRS Configuration Manager&#41;](../install-windows/configure-report-server-urls-ssrs-configuration-manager.md).</span></span>  
  
3.  <span data-ttu-id="e3538-157">报表管理器将在浏览器窗口中打开。</span><span class="sxs-lookup"><span data-stu-id="e3538-157">Report Manager opens in the browser window.</span></span> <span data-ttu-id="e3538-158">引导页为主文件夹。</span><span class="sxs-lookup"><span data-stu-id="e3538-158">The startup page is the Home folder.</span></span> <span data-ttu-id="e3538-159">根据权限，您可能看到引导页中的其他文件夹、指向报表的超链接和资源文件。</span><span class="sxs-lookup"><span data-stu-id="e3538-159">Depending on permissions, you might see additional folders, hyperlinks to reports, and resource files within the startup page.</span></span> <span data-ttu-id="e3538-160">也可能在工具栏上看到其他按钮和命令。</span><span class="sxs-lookup"><span data-stu-id="e3538-160">You might also see additional buttons and commands on the toolbar.</span></span>  
  
4.  <span data-ttu-id="e3538-161">如果在本地 Report Server 上运行报表管理器，请参阅[为本地管理配置本机模式报表服务器 &#40;SSRS&#41;](../report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="e3538-161">If you run Report Manager on the local report server, see [Configure a Native Mode Report Server for Local Administration &#40;SSRS&#41;](../report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).</span></span>  
  
 <span data-ttu-id="e3538-162">**后续步骤：** [&#40;本机模式下配置报表管理器&#41;](../report-server/configure-web-portal.md)。</span><span class="sxs-lookup"><span data-stu-id="e3538-162">**Next Steps:** [Configure Report Manager &#40;Native Mode&#41;](../report-server/configure-web-portal.md).</span></span>  
  
##  <a name="management-studio"></a><a name="bkmk_managements_studio"></a> <span data-ttu-id="e3538-163">Management Studio</span><span class="sxs-lookup"><span data-stu-id="e3538-163">Management Studio</span></span>  
 <span data-ttu-id="e3538-164">报表服务器管理员可以使用 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 来管理报表服务器及其他 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 组件服务器。</span><span class="sxs-lookup"><span data-stu-id="e3538-164">Report server administrators can use [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] to manage a report server alongside other [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] component servers.</span></span> <span data-ttu-id="e3538-165">有关详细信息，请参阅 [Use SQL Server Management Studio](../../database-engine/use-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="e3538-165">For more information, see [Use SQL Server Management Studio](../../database-engine/use-sql-server-management-studio.md).</span></span>  
  
#### <a name="to-start-sql-server-management-studio"></a><span data-ttu-id="e3538-166">启动 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e3538-166">To Start SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="e3538-167">在 Windows 的 "开始" 屏幕中键入， `sql server` 然后在 "**应用**" 搜索结果中，单击 " **SQL Server Management Studio**"。</span><span class="sxs-lookup"><span data-stu-id="e3538-167">From the Windows Start Screen type `sql server` and in the **Apps** search results, click **SQL Server Management Studio**.</span></span>  
  
     <span data-ttu-id="e3538-168">![Windows“开始”屏幕中的 Managment Studio](../media/bi-ssms-win8-startscreen.gif "Windows“开始”屏幕中的 Managment Studio")</span><span class="sxs-lookup"><span data-stu-id="e3538-168">![managment studio from windows start screen](../media/bi-ssms-win8-startscreen.gif "managment studio from windows start screen")</span></span>  
  
     <span data-ttu-id="e3538-169">**Or**</span><span class="sxs-lookup"><span data-stu-id="e3538-169">**Or**</span></span>  
  
     <span data-ttu-id="e3538-170">依次单击“开始” \*\*\*\*、“所有程序” \*\*\*\*、“ [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)]”和“SQL Server Management Studio” \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e3538-170">Click **Start**, then click **All Programs**, then click [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)], and then click **SQL Server Management Studio**.</span></span> <span data-ttu-id="e3538-171">此时会显示“连接到服务器”对话框。</span><span class="sxs-lookup"><span data-stu-id="e3538-171">The **Connect to Server** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="e3538-172">如果没有出现 **“连接到服务器”** 对话框，请在 **“对象资源管理器”** 中单击 **“连接”** ，然后选择 **Reporting Services**。</span><span class="sxs-lookup"><span data-stu-id="e3538-172">If the **Connect to Server** dialog box does not appear, in **Object Explorer**, click **Connect** and then select **Reporting Services**.</span></span>  
  
3.  <span data-ttu-id="e3538-173">在 **“服务器类型”** 列表中，选择 **Reporting Services**。</span><span class="sxs-lookup"><span data-stu-id="e3538-173">In the **Server type** list, select **Reporting Services**.</span></span> <span data-ttu-id="e3538-174">如果 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 不在列表中，则说明没有安装它。</span><span class="sxs-lookup"><span data-stu-id="e3538-174">If [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] is not on the list, it is not installed.</span></span>  
  
4.  <span data-ttu-id="e3538-175">在 **“服务器名称”** 列表中，选择一个报表服务器实例。</span><span class="sxs-lookup"><span data-stu-id="e3538-175">In the **Server name** list, select a report server instance.</span></span> <span data-ttu-id="e3538-176">本地实例将显示在列表中。</span><span class="sxs-lookup"><span data-stu-id="e3538-176">Local instances appear in the list.</span></span> <span data-ttu-id="e3538-177">您还可以键入远程 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例的名称。</span><span class="sxs-lookup"><span data-stu-id="e3538-177">You can also type the name of a remote [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance.</span></span>  
  
5.  <span data-ttu-id="e3538-178">单击“连接” 。</span><span class="sxs-lookup"><span data-stu-id="e3538-178">Click **Connect**.</span></span> <span data-ttu-id="e3538-179">可以扩展根节点以设置服务器属性，修改角色定义或关闭报表服务器功能。</span><span class="sxs-lookup"><span data-stu-id="e3538-179">You can expand the root node to set server properties, modify role definitions, or turn off report server features.</span></span>  
  
##  <a name="sql-server-data-tools-with-report-designer-and-report-wizard"></a><a name="bkmk_ssdt"></a><span data-ttu-id="e3538-180">与报表设计器和报表向导 SQL Server Data Tools</span><span class="sxs-lookup"><span data-stu-id="e3538-180">SQL Server Data Tools with Report Designer and Report Wizard</span></span>  
 <span data-ttu-id="e3538-181">[!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] 提供了报表设计器 - Business Intelligence for Visual Studio 2012。</span><span class="sxs-lookup"><span data-stu-id="e3538-181">Report Designer is available within [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] - Business Intelligence for Visual Studio 2012.</span></span> <span data-ttu-id="e3538-182">该工具中的设计图面包括用于访问报表创作功能的选项卡式窗口、向导和菜单。</span><span class="sxs-lookup"><span data-stu-id="e3538-182">The design surface in the tool includes tabbed windows, wizards, and menus used to access report authoring features.</span></span> <span data-ttu-id="e3538-183">选择报表服务器项目或者报表服务器向导模板后，该报表设计器工具即可用。</span><span class="sxs-lookup"><span data-stu-id="e3538-183">The report designer tool becomes available when you choose a Report Server Project or a Report Server Wizard template.</span></span> <span data-ttu-id="e3538-184">若要了解详细信息，请参阅 [SQL Server Data Tools 中的 Reporting Services (SSDT)](reporting-services-in-sql-server-data-tools-ssdt.md)。</span><span class="sxs-lookup"><span data-stu-id="e3538-184">To learn more, see [Reporting Services in SQL Server Data Tools &#40;SSDT&#41;](reporting-services-in-sql-server-data-tools-ssdt.md).</span></span>  
  
#### <a name="to-start-report-designer"></a><span data-ttu-id="e3538-185">启动报表设计器</span><span class="sxs-lookup"><span data-stu-id="e3538-185">To start Report Designer</span></span>  
  
1.  <span data-ttu-id="e3538-186">从 Windows“开始”屏幕，键入 **“data”** ，然后在 **“应用程序”** 搜索结果中，单击 **“SQL Server Data Tools for Visual Studio 2012”**。</span><span class="sxs-lookup"><span data-stu-id="e3538-186">From the Windows start screen, type **data** and in the **Apps** search results, click **SQL Server Data Tools for Visual Studio 2012**.</span></span>  
  
     <span data-ttu-id="e3538-187">**Or**</span><span class="sxs-lookup"><span data-stu-id="e3538-187">**Or**</span></span>  
  
     <span data-ttu-id="e3538-188">单击 "**开始**"，指向 "**所有程序**"，指向 [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)] ，然后单击 " \*\*SQL Server Data Tools (SSDT) \*\*"。</span><span class="sxs-lookup"><span data-stu-id="e3538-188">Click **Start**, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)], and then click **SQL Server Data Tools (SSDT)**.</span></span>  
  
2.  <span data-ttu-id="e3538-189">在 **“文件”** 菜单上，指向 **“新建”** ，然后单击 **“项目”** 。</span><span class="sxs-lookup"><span data-stu-id="e3538-189">On the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="e3538-190">在 **“项目类型”** 列表中，单击 **“商业智能项目”**。</span><span class="sxs-lookup"><span data-stu-id="e3538-190">In the **Project Types** list, click **Business Intelligence Projects**.</span></span>  
  
4.  <span data-ttu-id="e3538-191">在 **“模板”** 列表中，单击 **“报表服务器项目”**。</span><span class="sxs-lookup"><span data-stu-id="e3538-191">In the **Templates** list, click **Report Server Project**.</span></span> <span data-ttu-id="e3538-192">下图显示了对话框中显示的项目模板的外观：</span><span class="sxs-lookup"><span data-stu-id="e3538-192">The following diagram shows how the project templates appear in the dialog box:</span></span>  
  
     <span data-ttu-id="e3538-193">![“新建项目模板”对话框](../media/rs-ui-newrsproject.gif "“新建项目模板”对话框")</span><span class="sxs-lookup"><span data-stu-id="e3538-193">![New Project template dialog box](../media/rs-ui-newrsproject.gif "New Project template dialog box")</span></span>  
  
5.  <span data-ttu-id="e3538-194">为项目键入名称和位置，或单击 **“浏览”** 并选择位置。</span><span class="sxs-lookup"><span data-stu-id="e3538-194">Type a name and location for the project, or click **Browse** and select a location.</span></span>  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]<span data-ttu-id="e3538-195">[!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]打开并出现 " [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 起始页"。</span><span class="sxs-lookup"><span data-stu-id="e3538-195">[!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] opens with the [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] start page.</span></span> <span data-ttu-id="e3538-196">解决方案资源管理器提供用来创建报表和数据源的类别。</span><span class="sxs-lookup"><span data-stu-id="e3538-196">Solution Explorer provides categories for creating reports and data sources.</span></span> <span data-ttu-id="e3538-197">可以使用这些类别来创建新的报表和数据源。</span><span class="sxs-lookup"><span data-stu-id="e3538-197">You can use these categories to create new reports and data sources.</span></span> <span data-ttu-id="e3538-198">创建报表定义时将显示选项卡式窗口。</span><span class="sxs-lookup"><span data-stu-id="e3538-198">Tabbed windows appear when you create a report definition.</span></span> <span data-ttu-id="e3538-199">选项卡式窗口包括“数据”、“布局”和“预览”。</span><span class="sxs-lookup"><span data-stu-id="e3538-199">The tabbed windows are Data, Layout, and Preview..</span></span>  
  
 <span data-ttu-id="e3538-200">若要掌握有关创建报表的入门知识，请参阅[创建基本表报表（SSRS 教程）](../create-a-basic-table-report-ssrs-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="e3538-200">To get started on your first report, see [Create a Basic Table Report &#40;SSRS Tutorial&#41;](../create-a-basic-table-report-ssrs-tutorial.md).</span></span> <span data-ttu-id="e3538-201">若要了解有关可在报表设计器中使用的查询设计器的详细信息，请参阅[报表设计器 SQL Server Data Tools &#40;SSRS&#41;中的查询设计工具](../report-data/query-design-tools-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="e3538-201">To learn more about query designers you can use within Report Designer, see [Query Design Tools in Report Designer SQL Server Data Tools &#40;SSRS&#41;](../report-data/query-design-tools-ssrs.md).</span></span>  
  
##  <a name="report-builder"></a><a name="bkmk_report_builder"></a> <span data-ttu-id="e3538-202">报表生成器</span><span class="sxs-lookup"><span data-stu-id="e3538-202">Report Builder</span></span>  
 <span data-ttu-id="e3538-203">使用[&#40;SSRS&#41;报表生成器](report-builder-authoring-environment-ssrs.md)在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 类似 Office 的创作环境中创建报表。</span><span class="sxs-lookup"><span data-stu-id="e3538-203">Use [Report Builder &#40;SSRS&#41;](report-builder-authoring-environment-ssrs.md) to create reports in a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office-like authoring environment.</span></span> <span data-ttu-id="e3538-204">您可以自定义和更新所有的现有报表，无论这些报表是在报表设计器中还是在早期版本的报表生成器中创建的。</span><span class="sxs-lookup"><span data-stu-id="e3538-204">You can customize and update all existing reports, regardless of whether they were created in Report Designer or in the previous versions of Report Builder.</span></span> <span data-ttu-id="e3538-205">请与管理员联系，以获得在本地计算机上安装报表生成器所要运行的 ReportBuilder3.msi 文件的位置。</span><span class="sxs-lookup"><span data-stu-id="e3538-205">Contact your administrator for the location of the ReportBuilder3.msi file that you run to install Report Builder on your local computer.</span></span>  
  
 <span data-ttu-id="e3538-206">**安装：** 报表生成器的单击一次版本通过 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 本机模式或 SharePoint 模式安装。</span><span class="sxs-lookup"><span data-stu-id="e3538-206">**Installation:** The click-once version of report builder is installed by either [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Native mode or SharePoint mode.</span></span> <span data-ttu-id="e3538-207">报表生成器的独立版是一个单独的下载包。</span><span class="sxs-lookup"><span data-stu-id="e3538-207">The Stand-alone version of Report Builder is a separate download.</span></span>  <span data-ttu-id="e3538-208">请参阅[安装报表生成器的独立版本 &#40;报表生成器&#41;](../install-windows/install-report-builder.md)</span><span class="sxs-lookup"><span data-stu-id="e3538-208">See [Install the Stand-Alone Version of Report Builder &#40;Report Builder&#41;](../install-windows/install-report-builder.md)</span></span>  
  
#### <a name="to-start-report-builder-clickonce-from-report-manager-native-mode"></a><span data-ttu-id="e3538-209">从报表管理器启动 ClickOnce 版报表生成器（本机模式）</span><span class="sxs-lookup"><span data-stu-id="e3538-209">To start Report Builder ClickOnce from Report Manager (Native Mode)</span></span>  
  
1.  <span data-ttu-id="e3538-210">在 Web 浏览器中，键入报表服务器的报表管理器 URL。</span><span class="sxs-lookup"><span data-stu-id="e3538-210">In your Web browser, type the Report Manager URL for your report server.</span></span> <span data-ttu-id="e3538-211">默认情况下，URL 是 http:// \<*servername*> /reports。</span><span class="sxs-lookup"><span data-stu-id="e3538-211">By default, the URL is http://\<*servername*>/reports.</span></span> <span data-ttu-id="e3538-212">报表管理器随之打开。</span><span class="sxs-lookup"><span data-stu-id="e3538-212">Report Manager opens.</span></span>  
  
2.  <span data-ttu-id="e3538-213">单击 **“报表生成器”**。</span><span class="sxs-lookup"><span data-stu-id="e3538-213">Click **Report Builder**.</span></span>  
  
     <span data-ttu-id="e3538-214">报表生成器将打开，您随后可以在报表服务器上创建报表或打开报表。</span><span class="sxs-lookup"><span data-stu-id="e3538-214">Report Builder opens and you can create a report or open a report on the report server.</span></span>  
  
#### <a name="to-start-report-builder-clickonce-using-a-url"></a><span data-ttu-id="e3538-215">使用 URL 启动报表生成器 ClickOnce</span><span class="sxs-lookup"><span data-stu-id="e3538-215">To start Report Builder ClickOnce using a URL</span></span>  
  
1.  <span data-ttu-id="e3538-216">在 Web 浏览器的地址栏中，键入以下 URL：</span><span class="sxs-lookup"><span data-stu-id="e3538-216">In your Web browser, type the following URL in the address bar:</span></span>  
  
     <span data-ttu-id="e3538-217">**http:// \<servername> /reportserver/reportbuilder/ReportBuilder_3_0_0_0**</span><span class="sxs-lookup"><span data-stu-id="e3538-217">**http://\<servername>/reportserver/reportbuilder/ReportBuilder_3_0_0_0.application**</span></span>  
  
2.  <span data-ttu-id="e3538-218">按 Enter。</span><span class="sxs-lookup"><span data-stu-id="e3538-218">Press ENTER.</span></span>  
  
     <span data-ttu-id="e3538-219">报表生成器将打开，您随后可以在报表服务器上创建报表或打开报表。</span><span class="sxs-lookup"><span data-stu-id="e3538-219">Report Builder opens and you can create a report or open a report on the report server.</span></span>  
  
#### <a name="to-start-report-builder-clickonce-in-reporting-services-sharepoint-mode"></a><span data-ttu-id="e3538-220">在 Reporting Services SharePoint 模式下启动 ClickOnce 版报表生成器</span><span class="sxs-lookup"><span data-stu-id="e3538-220">To start Report Builder ClickOnce in Reporting Services SharePoint mode</span></span>  
  
1.  <span data-ttu-id="e3538-221">导航到包含要创建新报表的库的站点。</span><span class="sxs-lookup"><span data-stu-id="e3538-221">Navigate to the site that contains the library where you want to create a new report.</span></span>  
  
2.  <span data-ttu-id="e3538-222">打开库。</span><span class="sxs-lookup"><span data-stu-id="e3538-222">Open the library.</span></span>  
  
3.  <span data-ttu-id="e3538-223">在 **“新建”** 菜单中单击 **“报表生成器报表”**。</span><span class="sxs-lookup"><span data-stu-id="e3538-223">On the **New** menu, click **Report Builder Report**.</span></span>  
  
     <span data-ttu-id="e3538-224">报表生成器将打开，您随后可以在报表服务器上创建报表或打开报表。</span><span class="sxs-lookup"><span data-stu-id="e3538-224">Report Builder opens and you can create a report or open a report on the report server.</span></span>  
  
#### <a name="to-start-report-builder-stand-alone"></a><span data-ttu-id="e3538-225">启动独立版报表生成器</span><span class="sxs-lookup"><span data-stu-id="e3538-225">To start Report Builder Stand-alone</span></span>  
  
1.  <span data-ttu-id="e3538-226">在 Windows“开始”屏幕上，键入 **“report builder”** ，然后单击 **“Report Builder 3.0”**。</span><span class="sxs-lookup"><span data-stu-id="e3538-226">From the Windows start screen, type **report builder** and then click **Report Builder 3.0**.</span></span>  
  
     <span data-ttu-id="e3538-227">**Or**</span><span class="sxs-lookup"><span data-stu-id="e3538-227">**Or**</span></span>  
  
     <span data-ttu-id="e3538-228">在“开始”菜单上，依次单击 **“所有程序”** 和 **“Microsoft SQL Server 2014 报表生成器”**。</span><span class="sxs-lookup"><span data-stu-id="e3538-228">On the Start menu, click **All Programs**, and then click **Microsoft SQL Server 2014 Report Builder**.</span></span>  
  
2.  <span data-ttu-id="e3538-229">单击 **“报表生成器”**。</span><span class="sxs-lookup"><span data-stu-id="e3538-229">Click **Report Builder**.</span></span>  
  
     <span data-ttu-id="e3538-230">报表生成器将打开，您可以创建或打开报表了。</span><span class="sxs-lookup"><span data-stu-id="e3538-230">Report Builder opens and you can create or open a report.</span></span>  
  
3.  <span data-ttu-id="e3538-231">单击 **“报表生成器帮助”** 可打开报表生成器的文档。</span><span class="sxs-lookup"><span data-stu-id="e3538-231">Click **Report Builder Help** to open the documentation for Report Builder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3538-232">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e3538-232">See Also</span></span>  
 <span data-ttu-id="e3538-233">[安装、卸载和报表生成器支持](../install-uninstall-and-report-builder-support.md) </span><span class="sxs-lookup"><span data-stu-id="e3538-233">[Install, Uninstall, and Report Builder Support](../install-uninstall-and-report-builder-support.md) </span></span>  
 <span data-ttu-id="e3538-234">[Reporting Services sharepoint 模式安装 &#40;SharePoint 2010 和 SharePoint 2013&#41;](../install-windows/install-reporting-services-sharepoint-mode.md) </span><span class="sxs-lookup"><span data-stu-id="e3538-234">[Reporting Services SharePoint Mode Installation &#40;SharePoint 2010 and SharePoint 2013&#41;](../install-windows/install-reporting-services-sharepoint-mode.md) </span></span>  
 <span data-ttu-id="e3538-235">[Reporting Services 报表服务器](../reporting-services-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="e3538-235">[Reporting Services Report Server](../reporting-services-report-server.md) </span></span>  
 <span data-ttu-id="e3538-236">[查询设计工具报表设计器 SQL Server Data Tools &#40;SSRS&#41;](../report-data/query-design-tools-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e3538-236">[Query Design Tools in Report Designer SQL Server Data Tools &#40;SSRS&#41;](../report-data/query-design-tools-ssrs.md) </span></span>  
 [<span data-ttu-id="e3538-237">Reporting Services 教程 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="e3538-237">Reporting Services Tutorials &#40;SSRS&#41;</span></span>](../reporting-services-tutorials-ssrs.md)  
  
  
