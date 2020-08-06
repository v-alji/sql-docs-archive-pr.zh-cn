---
title: " (SharePoint 2013) 配置 PowerPivot 和部署解决方案 |Microsoft Docs"
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 6401fd92-f43b-450e-8298-12db644c25bc
author: minewiskan
ms.author: owend
ms.openlocfilehash: a7eaea7f9c490fd320d6dbd0777519eeca218b79
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688363"
---
# <a name="configure-powerpivot-and-deploy-solutions-sharepoint-2013"></a><span data-ttu-id="b41a8-102">配置 PowerPivot 和部署解决方案 (SharePoint 2013)</span><span class="sxs-lookup"><span data-stu-id="b41a8-102">Configure PowerPivot and Deploy Solutions (SharePoint 2013)</span></span>
  <span data-ttu-id="b41a8-103">本主题介绍如何部署和配置 [!INCLUDE[SPS2013](../../../includes/sps2013-md.md)] 中 PowerPivot 功能的中间层增强功能，包括 PowerPivot 库、计划数据刷新、管理面板和数据提供程序。</span><span class="sxs-lookup"><span data-stu-id="b41a8-103">This topics describes the deployment and configuration of middle-tier enhancements to the PowerPivot features in [!INCLUDE[SPS2013](../../../includes/sps2013-md.md)] including PowerPivot Gallery, Schedule data refresh, Management Dashboard, and data providers.</span></span> <span data-ttu-id="b41a8-104">运行 **PowerPivot for SharePoint 2013 配置** 工具以便完成以下任务：</span><span class="sxs-lookup"><span data-stu-id="b41a8-104">Run **PowerPivot for SharePoint 2013 Configuration** tool to complete the following:</span></span>  
  
-   <span data-ttu-id="b41a8-105">部署 SharePoint 解决方案文件。</span><span class="sxs-lookup"><span data-stu-id="b41a8-105">Deploy SharePoint solution files.</span></span>  
  
-   <span data-ttu-id="b41a8-106">创建 PowerPivot 服务应用程序。</span><span class="sxs-lookup"><span data-stu-id="b41a8-106">Create a PowerPivot service application.</span></span>  
  
-   <span data-ttu-id="b41a8-107">将 Excel Services 应用程序配置为在 SharePoint 模式下使用 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 服务器。</span><span class="sxs-lookup"><span data-stu-id="b41a8-107">Configure an Excel Services Application to use an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] server in SharePoint mode.</span></span> <span data-ttu-id="b41a8-108">有关后端服务和 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 在 SharePoint 模式下安装服务器的信息，请参阅[PowerPivot for SharePoint 2013 安装](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode)。</span><span class="sxs-lookup"><span data-stu-id="b41a8-108">For information on backend services and installing a [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] server in SharePoint mode, see [PowerPivot for SharePoint 2013 Installation](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode).</span></span>  
  
 <span data-ttu-id="b41a8-109">有关安装 PowerPivot for SharePoint 2013 配置工具的信息，请参阅[&#40;SharePoint 2013 安装或卸载 PowerPivot for SharePoint 外接程序&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013)</span><span class="sxs-lookup"><span data-stu-id="b41a8-109">For information on installing the PowerPivot for SharePoint 2013 Configuration tool, see [Install or Uninstall the PowerPivot for SharePoint Add-in &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013)</span></span>  
  
 <span data-ttu-id="b41a8-110">本主题包含以下各节：</span><span class="sxs-lookup"><span data-stu-id="b41a8-110">This topic contains the following sections:</span></span>  
  
 [<span data-ttu-id="b41a8-111">运行 PowerPivot for SharePoint 2013 配置</span><span class="sxs-lookup"><span data-stu-id="b41a8-111">Run PowerPivot for SharePoint 2013 configuration</span></span>](#bkmk_run_configuration_tool)  
  
 [<span data-ttu-id="b41a8-112">验证 PowerPivot 配置</span><span class="sxs-lookup"><span data-stu-id="b41a8-112">Verify PowerPivot Configuration</span></span>](#bkmk_verify_powerpivot)  
  
 [<span data-ttu-id="b41a8-113">解决问题</span><span class="sxs-lookup"><span data-stu-id="b41a8-113">Troubleshoot Issues</span></span>](#bkmk_troubleshoot_issues)  
  
##  <a name="run-powerpivot-for-sharepoint-2013-configuration"></a><a name="bkmk_run_configuration_tool"></a><span data-ttu-id="b41a8-114">运行 PowerPivot for SharePoint 2013 配置</span><span class="sxs-lookup"><span data-stu-id="b41a8-114">Run PowerPivot for SharePoint 2013 configuration</span></span>  
 <span data-ttu-id="b41a8-115">**注意：**[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 安装向导将为 [!INCLUDE[ssGeminiLong](../../../includes/ssgeminilong-md.md)] 安装两个不同的配置工具。</span><span class="sxs-lookup"><span data-stu-id="b41a8-115">**Note:** The [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] setup wizard installs two different configuration tools for [!INCLUDE[ssGeminiLong](../../../includes/ssgeminilong-md.md)].</span></span> <span data-ttu-id="b41a8-116">这两个工具均支持不同版本的 SharePoint。</span><span class="sxs-lookup"><span data-stu-id="b41a8-116">They each support a different version of SharePoint.</span></span>  
  
|<span data-ttu-id="b41a8-117">名称</span><span class="sxs-lookup"><span data-stu-id="b41a8-117">Name</span></span>|<span data-ttu-id="b41a8-118">说明</span><span class="sxs-lookup"><span data-stu-id="b41a8-118">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="b41a8-119">PowerPivot for SharePoint 2013 配置</span><span class="sxs-lookup"><span data-stu-id="b41a8-119">PowerPivot for SharePoint 2013 Configuration</span></span>|<span data-ttu-id="b41a8-120">SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="b41a8-120">SharePoint 2013</span></span>|  
|<span data-ttu-id="b41a8-121">PowerPivot 配置工具</span><span class="sxs-lookup"><span data-stu-id="b41a8-121">PowerPivot Configuration Tool</span></span>|<span data-ttu-id="b41a8-122">具有 SharePoint 2010 Service Pack 1 (SP1) 的 SharePoint 2010</span><span class="sxs-lookup"><span data-stu-id="b41a8-122">SharePoint 2010 with SharePoint 2010 Service Pack 1 (SP1)</span></span>|  
  
 <span data-ttu-id="b41a8-123">**注意：** 若要完成下列步骤，您必须是场管理员。</span><span class="sxs-lookup"><span data-stu-id="b41a8-123">**Note:** To complete the following steps, you must be a farm administrator.</span></span> <span data-ttu-id="b41a8-124">如果您看到与以下内容类似的错误消息：</span><span class="sxs-lookup"><span data-stu-id="b41a8-124">If you see an error message similar to the following:</span></span>  
  
-   <span data-ttu-id="b41a8-125">"该用户不是场管理员。</span><span class="sxs-lookup"><span data-stu-id="b41a8-125">"The user is not a farm administrator.</span></span> <span data-ttu-id="b41a8-126">请解决验证问题并重试。”</span><span class="sxs-lookup"><span data-stu-id="b41a8-126">Please address the validation failures and try again."</span></span>  
  
 <span data-ttu-id="b41a8-127">以安装了 SharePoint 的帐户登录或将安装帐户配置为 SharePoint 管理中心网站的主管理员。</span><span class="sxs-lookup"><span data-stu-id="b41a8-127">Either login as the account that installed SharePoint or configure the setup account as the primary administrator of the SharePoint Central Administration Site.</span></span>  
  
1.  <span data-ttu-id="b41a8-128">在 **“开始”** 菜单中，单击 **“所有程序”**，然后依次单击 [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)]、 **“配置工具”** 和 **“PowerPivot For SharePoint 2013 配置”**。</span><span class="sxs-lookup"><span data-stu-id="b41a8-128">On the **Start** menu, click **All Programs**, and then click [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)], click **Configuration Tools**, and then click **PowerPivot For SharePoint 2013 Configuration**.</span></span> <span data-ttu-id="b41a8-129">只有在本地服务器上安装了 PowerPivot for SharePoint 后，才会列出工具。</span><span class="sxs-lookup"><span data-stu-id="b41a8-129">Toold is listed only when PowerPivot for SharePoint is installed on the local server.</span></span>  
  
2.  <span data-ttu-id="b41a8-130">单击 **“配置或修复 PowerPivot for SharePoint”** ，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="b41a8-130">Click **Configure or Repair PowerPivot for SharePoint** and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="b41a8-131">该工具将运行验证以验证 PowerPivot 的当前状态和完成配置所需的步骤。</span><span class="sxs-lookup"><span data-stu-id="b41a8-131">The tool runs validation to verify the current state of PowerPivot and what steps are required to complete configuration.</span></span> <span data-ttu-id="b41a8-132">将窗口放大为实际大小。</span><span class="sxs-lookup"><span data-stu-id="b41a8-132">Expand the window to full size.</span></span> <span data-ttu-id="b41a8-133">您应该在该窗口的底部看到一个菜单栏，其中包含 **“验证”**、 **“运行”** 和 **“退出”** 命令。</span><span class="sxs-lookup"><span data-stu-id="b41a8-133">You should see a button bar at the bottom of the window that includes **Validate**, **Run**, and **Exit** commands.</span></span>  
  
4.  <span data-ttu-id="b41a8-134">在 **“参数”** 选项卡上：</span><span class="sxs-lookup"><span data-stu-id="b41a8-134">On the **Parameters** tab:</span></span>  
  
    1.  <span data-ttu-id="b41a8-135">**默认帐户用户名**：输入默认帐户的域用户帐户。</span><span class="sxs-lookup"><span data-stu-id="b41a8-135">**Default Account UserName**: Enter a domain user account for the default account.</span></span> <span data-ttu-id="b41a8-136">此帐户将用于设置服务，包括 PowerPivot 服务应用程序池。</span><span class="sxs-lookup"><span data-stu-id="b41a8-136">This account will be used to provision services, including the PowerPivot service application pool.</span></span> <span data-ttu-id="b41a8-137">不要指定 Network Service 或 Local System 之类的内置帐户。</span><span class="sxs-lookup"><span data-stu-id="b41a8-137">Do not specify a built-in account such as Network Service or Local System.</span></span> <span data-ttu-id="b41a8-138">该工具将阻止指定内置帐户的配置。</span><span class="sxs-lookup"><span data-stu-id="b41a8-138">The tool blocks configurations that specify built-in accounts.</span></span>  
  
    2.  <span data-ttu-id="b41a8-139">**数据库服务器**：您可以使用 SharePoint 场支持的 SQL Server 数据库引擎。</span><span class="sxs-lookup"><span data-stu-id="b41a8-139">**Database Server**: You can use SQL Server Database engine that is supported for the SharePoint farm.</span></span>  
  
    3.  <span data-ttu-id="b41a8-140">**通行短语**：输入密码。</span><span class="sxs-lookup"><span data-stu-id="b41a8-140">**Passphrase**: Enter a passphrase.</span></span> <span data-ttu-id="b41a8-141">如果您在创建新的 SharePoint 场，则在您向该 SharePoint 场中添加新的服务器或应用程序时，将使用该通行短语。</span><span class="sxs-lookup"><span data-stu-id="b41a8-141">If you are creating a new SharePoint farm, the passphrase is used whenever you add a server or application to the SharePoint farm.</span></span> <span data-ttu-id="b41a8-142">如果该场已存在，则输入允许您向该场添加服务器应用程序的通行短语。</span><span class="sxs-lookup"><span data-stu-id="b41a8-142">If the farm already exists, enter the passphrase that allows you to add a server application to the farm.</span></span>  
  
    4.  <span data-ttu-id="b41a8-143">**PowerPivot Server for Excel Services**：键入 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] SharePoint 模式服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="b41a8-143">**PowerPivot Server for Excel Services**: Type the name of an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] SharePoint mode server.</span></span> <span data-ttu-id="b41a8-144">在单服务器部署中，它与数据库服务器相同。</span><span class="sxs-lookup"><span data-stu-id="b41a8-144">In a single-server deployment, it is the same as the database server.</span></span> `[ServerName]\powerpivot`  
  
    5.  <span data-ttu-id="b41a8-145">在左窗口中单击 **“创建网站集”** 。</span><span class="sxs-lookup"><span data-stu-id="b41a8-145">Click **Create Site Collection** in the left window.</span></span> <span data-ttu-id="b41a8-146">请注意 **“网址 URL”** ，以便您可以在后面的步骤中引用它。</span><span class="sxs-lookup"><span data-stu-id="b41a8-146">Note **Site URL** so you can reference it in later steps.</span></span> <span data-ttu-id="b41a8-147">如果 SharePoint 服务器尚未配置，则配置向导默认使用 Web 应用程序，并且将网站集 URL 默认为 `http://[ServerName]`的根。</span><span class="sxs-lookup"><span data-stu-id="b41a8-147">If the SharePoint server is not already configured, then the configuration wizard defaults the web application, and site collection URLs to the root of `http://[ServerName]`.</span></span> <span data-ttu-id="b41a8-148">若要修改这些默认设置，请在左窗口中查看以下页： **“创建默认的 Web 应用程序”** 和 **“部署 Web 应用程序解决方案”**。</span><span class="sxs-lookup"><span data-stu-id="b41a8-148">To modify the defaults review the following pages in the left window: **Create Default Web application** and **Deploy Web Application Solution**</span></span>  
  
5.  <span data-ttu-id="b41a8-149">或者，查看用于完成各操作的剩余输入值。</span><span class="sxs-lookup"><span data-stu-id="b41a8-149">Optionally, review the remaining input values used to complete each action.</span></span> <span data-ttu-id="b41a8-150">单击左窗口中的每个操作以查看操作的详细信息。</span><span class="sxs-lookup"><span data-stu-id="b41a8-150">Click each action in the left window to see and review the details of the action.</span></span> <span data-ttu-id="b41a8-151">有关每个帐户的详细信息，请参阅本主题中的 "[配置或修复 PowerPivot for SharePoint 2010 &#40;PowerPivot 配置工具&#41;](../../configure-repair-powerpivot-sharepoint-2010.md)中的" 用于配置服务器的输入值 "部分。</span><span class="sxs-lookup"><span data-stu-id="b41a8-151">For more information about each one, see the section "Input values used to configure the server in [Configure or Repair PowerPivot for SharePoint 2010 &#40;PowerPivot Configuration Tool&#41;](../../configure-repair-powerpivot-sharepoint-2010.md) in this topic.</span></span>  
  
6.  <span data-ttu-id="b41a8-152">您还可以删除不想在此时处理的任何操作。</span><span class="sxs-lookup"><span data-stu-id="b41a8-152">Optionally, remove any actions that you do not want to process at this time.</span></span> <span data-ttu-id="b41a8-153">例如，如果您想要在以后配置 Secure Store Service，则单击 **“配置 Secure Store Service”**，然后清除 **“在任务列表中包括此操作”** 复选框。</span><span class="sxs-lookup"><span data-stu-id="b41a8-153">For example, if you want to configure Secure Store Service later, click **Configure Secure Store Service**, and then clear the checkbox **Include this action in the task list**.</span></span>  
  
7.  <span data-ttu-id="b41a8-154">单击 **“验证”** 以便检查该工具是否有足够的信息来处理列表中的操作。</span><span class="sxs-lookup"><span data-stu-id="b41a8-154">Click **Validate** to check whether the tool has sufficient information to process the actions in the list.</span></span> <span data-ttu-id="b41a8-155">如果看到验证错误，请单击左窗格中的警告查看验证错误的详细信息。</span><span class="sxs-lookup"><span data-stu-id="b41a8-155">If you see validation errors, click the warnings in the left pane to see details of the validation error.</span></span> <span data-ttu-id="b41a8-156">更正任何验证错误，然后再次单击 **“验证”** 。</span><span class="sxs-lookup"><span data-stu-id="b41a8-156">Correct any validation errors and then click **Validate** again.</span></span>  
  
8.  <span data-ttu-id="b41a8-157">单击 **“运行”** 来处理该任务列表中的所有操作。</span><span class="sxs-lookup"><span data-stu-id="b41a8-157">Click **Run** to process all of the actions in the task list.</span></span> <span data-ttu-id="b41a8-158">请注意， **“运行”** 将在您验证操作之后才可用。</span><span class="sxs-lookup"><span data-stu-id="b41a8-158">Note that **Run** becomes available after you validate the actions.</span></span> <span data-ttu-id="b41a8-159">如果 **“运行”** 未启用，请首先单击 **“验证”** 。</span><span class="sxs-lookup"><span data-stu-id="b41a8-159">If **Run** is not enabled, click **Validate** first.</span></span>  
  
 <span data-ttu-id="b41a8-160">有关详细信息，请参阅[配置或修复 PowerPivot for SharePoint 2010 &#40;PowerPivot 配置工具&#41;](../../configure-repair-powerpivot-sharepoint-2010.md)</span><span class="sxs-lookup"><span data-stu-id="b41a8-160">For more information, see [Configure or Repair PowerPivot for SharePoint 2010 &#40;PowerPivot Configuration Tool&#41;](../../configure-repair-powerpivot-sharepoint-2010.md)</span></span>  
  
##  <a name="verify-powerpivot-configuration"></a><a name="bkmk_verify_powerpivot"></a><span data-ttu-id="b41a8-161">验证 PowerPivot 配置</span><span class="sxs-lookup"><span data-stu-id="b41a8-161">Verify PowerPivot Configuration</span></span>  
 <span data-ttu-id="b41a8-162">**服务：**</span><span class="sxs-lookup"><span data-stu-id="b41a8-162">**Services:**</span></span>  
  
1.  <span data-ttu-id="b41a8-163">在管理中心的 "系统设置" 中，单击 "**管理服务器上的服务**"。</span><span class="sxs-lookup"><span data-stu-id="b41a8-163">In Central Administration, in System Settings, click **Manage services on server**.</span></span>  
  
2.  <span data-ttu-id="b41a8-164">验证 **SQL Server Analysis Services** 和 **SQL Server PowerPivot 系统服务** 是否已启动。</span><span class="sxs-lookup"><span data-stu-id="b41a8-164">Verify that **SQL Server Analysis Services** and **SQL Server PowerPivot System Service** are started.</span></span>  
  
 <span data-ttu-id="b41a8-165">**场功能：**</span><span class="sxs-lookup"><span data-stu-id="b41a8-165">**Farm Feature:**</span></span>  
  
1.  <span data-ttu-id="b41a8-166">在管理中心的“系统设置”中，单击 **“管理场功能”**。</span><span class="sxs-lookup"><span data-stu-id="b41a8-166">In Central Administration, in System Settings, click **Manage farm features**.</span></span>  
  
2.  <span data-ttu-id="b41a8-167">确认 **“PowerPivot 集成功能”** 为 **“活动”**。</span><span class="sxs-lookup"><span data-stu-id="b41a8-167">Verify that **PowerPivot Integration Feature** is **Active**.</span></span>  
  
 <span data-ttu-id="b41a8-168">**网站集功能：**</span><span class="sxs-lookup"><span data-stu-id="b41a8-168">**Site Collection Feature:**</span></span>  
  
1.  <span data-ttu-id="b41a8-169">浏览到您通过使用配置工具创建的网站 URL。</span><span class="sxs-lookup"><span data-stu-id="b41a8-169">Browse to your site URL that was created by the Configuration tool.</span></span>  
  
     <span data-ttu-id="b41a8-170">单击 "**设置**" "![SharePoint 设置](https://docs.microsoft.com/analysis-services/analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint 设置")"，然后单击 "**站点设置**"。</span><span class="sxs-lookup"><span data-stu-id="b41a8-170">Click **Settings**![SharePoint Settings](https://docs.microsoft.com/analysis-services/analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint Settings"), and then click **Site Settings**.</span></span>  
  
     <span data-ttu-id="b41a8-171">单击 **“网站集功能”**。</span><span class="sxs-lookup"><span data-stu-id="b41a8-171">Click **Site Collection Features**.</span></span>  
  
2.  <span data-ttu-id="b41a8-172">确认 **“针对网站集的 PowerPivot 功能集成”** 为 **“活动”**。</span><span class="sxs-lookup"><span data-stu-id="b41a8-172">Verify that **PowerPivot Feature Integration for Site Collections** is **Active**.</span></span>  
  
 <span data-ttu-id="b41a8-173">**PowerPivot 服务应用程序：**</span><span class="sxs-lookup"><span data-stu-id="b41a8-173">**PowerPivot Service Application:**</span></span>  
  
1.  <span data-ttu-id="b41a8-174">在“管理中心”的 **“应用程序管理”** 中，单击 **“管理服务应用程序”**。</span><span class="sxs-lookup"><span data-stu-id="b41a8-174">In Central Administration, in the **Application Management**, click **Manage service applications**.</span></span>  
  
2.  <span data-ttu-id="b41a8-175">确认服务应用程序状态为 **“已启动”**。</span><span class="sxs-lookup"><span data-stu-id="b41a8-175">Verify the service application status is **started**.</span></span> <span data-ttu-id="b41a8-176">默认名称为**默认的 PowerPivot 服务应用程序**。</span><span class="sxs-lookup"><span data-stu-id="b41a8-176">The default name is **Default PowerPivot Service Application**.</span></span>  
  
     <span data-ttu-id="b41a8-177">单击服务应用程序的名称，以便打开 PowerPivot 管理面板以使服务应用程序打开。</span><span class="sxs-lookup"><span data-stu-id="b41a8-177">Click the name of the services application to open the PowerPivot Management Dashboard for the service application opens.</span></span> <span data-ttu-id="b41a8-178">第一次使用时，面板要花几分钟的加载时间。</span><span class="sxs-lookup"><span data-stu-id="b41a8-178">On first use, the dashboard takes several minutes to load.</span></span>  
  
 <span data-ttu-id="b41a8-179">有关详细信息，请参阅 [Verify a PowerPivot for SharePoint Installation](https://docs.microsoft.com/analysis-services/instances/install-windows/verify-a-power-pivot-for-sharepoint-installation)。</span><span class="sxs-lookup"><span data-stu-id="b41a8-179">For more information, see [Verify a PowerPivot for SharePoint Installation](https://docs.microsoft.com/analysis-services/instances/install-windows/verify-a-power-pivot-for-sharepoint-installation).</span></span>  
  
##  <a name="troubleshoot-issues"></a><a name="bkmk_troubleshoot_issues"></a><span data-ttu-id="b41a8-180">解决问题</span><span class="sxs-lookup"><span data-stu-id="b41a8-180">Troubleshoot Issues</span></span>  
 <span data-ttu-id="b41a8-181">为了协助解决问题，最好验证诊断日志记录已启用。</span><span class="sxs-lookup"><span data-stu-id="b41a8-181">To assist in troubleshooting issues, it is a good idea to verify the diagnostic logging is enabled.</span></span>  
  
1.  <span data-ttu-id="b41a8-182">在 SharePoint 管理中心中，单击 **“监视”** ，然后单击 **“配置使用情况和运行状况数据收集”**。</span><span class="sxs-lookup"><span data-stu-id="b41a8-182">In SharePoint Central Administration, click **Monitoring** and then click **Configure usage and health data collection**.</span></span>  
  
2.  <span data-ttu-id="b41a8-183">确认选择了 **“启用使用情况数据收集”** 。</span><span class="sxs-lookup"><span data-stu-id="b41a8-183">Verify **Enable usage data collection** is selected.</span></span>  
  
3.  <span data-ttu-id="b41a8-184">验证是否选择了以下事件：</span><span class="sxs-lookup"><span data-stu-id="b41a8-184">Verify the following events are selected:</span></span>  
  
    -   <span data-ttu-id="b41a8-185">针对教育遥测的使用情况字段的定义</span><span class="sxs-lookup"><span data-stu-id="b41a8-185">Definition of usage fields for Education telemetry</span></span>  
  
    -   <span data-ttu-id="b41a8-186">PowerPivot 连接</span><span class="sxs-lookup"><span data-stu-id="b41a8-186">PowerPivot Connects</span></span>  
  
    -   <span data-ttu-id="b41a8-187">PowerPivot 加载数据使用情况</span><span class="sxs-lookup"><span data-stu-id="b41a8-187">PowerPivot Load Data Usage</span></span>  
  
    -   <span data-ttu-id="b41a8-188">PowerPivot 查询使用情况</span><span class="sxs-lookup"><span data-stu-id="b41a8-188">PowerPivot Query Usage</span></span>  
  
    -   <span data-ttu-id="b41a8-189">PowerPivot 卸载数据使用情况</span><span class="sxs-lookup"><span data-stu-id="b41a8-189">PowerPivot Unload Data Usage</span></span>  
  
4.  <span data-ttu-id="b41a8-190">确认选择了 **“启用运行状况数据收集”** 。</span><span class="sxs-lookup"><span data-stu-id="b41a8-190">Verify **Enable health data collection** is selected.</span></span>  
  
5.  <span data-ttu-id="b41a8-191">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="b41a8-191">Click **OK**.</span></span>  
  
 <span data-ttu-id="b41a8-192">有关排除数据刷新问题的详细信息，请参阅[PowerPivot 数据刷新故障排除](https://social.technet.microsoft.com/wiki/contents/articles/3870.troubleshooting-powerpivot-data-refresh.aspx) (https://social.technet.microsoft.com/wiki/contents/articles/3870.troubleshooting-powerpivot-data-refresh.aspx) 。</span><span class="sxs-lookup"><span data-stu-id="b41a8-192">For more information on trouble shooting data refresh, see [Troubleshooting PowerPivot Data Refresh](https://social.technet.microsoft.com/wiki/contents/articles/3870.troubleshooting-powerpivot-data-refresh.aspx) (https://social.technet.microsoft.com/wiki/contents/articles/3870.troubleshooting-powerpivot-data-refresh.aspx).</span></span>  
  
 <span data-ttu-id="b41a8-193">有关配置工具的详细信息，请参阅 [PowerPivot Configuration Tools](../../power-pivot-sharepoint/power-pivot-configuration-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="b41a8-193">For more information on the configuration tool, see [PowerPivot Configuration Tools](../../power-pivot-sharepoint/power-pivot-configuration-tools.md).</span></span>  
  
  
