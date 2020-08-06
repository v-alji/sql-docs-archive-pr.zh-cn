---
title: PowerPivot 管理面板和使用情况数据 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 541c8b1f-c6c2-423d-a97d-65c379967e0c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 581ed571661d54b1cfe9a63224b05f4f8b0267e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587023"
---
# <a name="powerpivot-management-dashboard-and-usage-data"></a><span data-ttu-id="2f670-102">PowerPivot 管理面板和使用情况数据</span><span class="sxs-lookup"><span data-stu-id="2f670-102">PowerPivot Management Dashboard and Usage Data</span></span>
  <span data-ttu-id="2f670-103">PowerPivot 管理面板是 SharePoint 管理中心中预定义报表和 Web 部件的集合，可以帮助您管理 SQL Server PowerPivot for SharePoint 部署。</span><span class="sxs-lookup"><span data-stu-id="2f670-103">PowerPivot Management Dashboard is a collection of predefined reports and web parts in SharePoint Central Administration that help you administer a SQL Server PowerPivot for SharePoint deployment.</span></span> <span data-ttu-id="2f670-104">管理面板提供了与服务器运行状况、工作簿活动以及数据刷新相关的信息。</span><span class="sxs-lookup"><span data-stu-id="2f670-104">The Management Dashboard provides information related to server health, workbook activity, and data refresh.</span></span> <span data-ttu-id="2f670-105">该面板使用的数据来自于 SharePoint 使用情况数据集合。</span><span class="sxs-lookup"><span data-stu-id="2f670-105">The dashboard uses data from the SharePoint usage data collection.</span></span>  
  
 [<span data-ttu-id="2f670-106">先决条件</span><span class="sxs-lookup"><span data-stu-id="2f670-106">Prerequisites</span></span>](#prereq)  
  
 [<span data-ttu-id="2f670-107">仪表板各部分的概述</span><span class="sxs-lookup"><span data-stu-id="2f670-107">Overview of the sections of the Dashboard</span></span>](#items)  
  
 [<span data-ttu-id="2f670-108">打开 PowerPivot 管理面板</span><span class="sxs-lookup"><span data-stu-id="2f670-108">Open PowerPivot Management Dashboard</span></span>](#open)  
  
 [<span data-ttu-id="2f670-109">面板中的源数据</span><span class="sxs-lookup"><span data-stu-id="2f670-109">Source Data in Dashboards</span></span>](#sourcedata)  
  
 [<span data-ttu-id="2f670-110">编辑 PowerPivot 面板</span><span class="sxs-lookup"><span data-stu-id="2f670-110">Edit PowerPivot Dashboard</span></span>](#edit)  
  
 [<span data-ttu-id="2f670-111">为 PowerPivot 管理面板创建自定义报表</span><span class="sxs-lookup"><span data-stu-id="2f670-111">Create Custom Reports for PowerPivot Management Dashboard</span></span>](#reports)  
  
##  <a name="prerequisites"></a><a name="prereq"></a><span data-ttu-id="2f670-112">先决条件</span><span class="sxs-lookup"><span data-stu-id="2f670-112">Prerequisites</span></span>  
 <span data-ttu-id="2f670-113">您必须是服务管理员才能为您管理的 PowerPivot 服务应用程序打开 PowerPivot 管理面板。</span><span class="sxs-lookup"><span data-stu-id="2f670-113">You must be a service administrator to open PowerPivot Management Dashboard for a PowerPivot service application that you manage.</span></span>  
  
##  <a name="overview-of-the-sections-of-the-dashboard"></a><a name="items"></a> <span data-ttu-id="2f670-114">“面板”各个部分的概述</span><span class="sxs-lookup"><span data-stu-id="2f670-114">Overview of the sections of the Dashboard</span></span>  
 <span data-ttu-id="2f670-115">PowerPivot 管理面板包含用于深化到特定信息类别的 Web 部件和嵌入式报表。</span><span class="sxs-lookup"><span data-stu-id="2f670-115">PowerPivot Management Dashboard contains Web Parts and embedded reports that drill down into specific information categories.</span></span> <span data-ttu-id="2f670-116">下面的列表介绍面板的每个部分：</span><span class="sxs-lookup"><span data-stu-id="2f670-116">The following list describes each part of the dashboard:</span></span>  
  
|<span data-ttu-id="2f670-117">仪表板</span><span class="sxs-lookup"><span data-stu-id="2f670-117">Dashboard</span></span>|<span data-ttu-id="2f670-118">说明</span><span class="sxs-lookup"><span data-stu-id="2f670-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2f670-119">基础结构 - 服务器运行状况</span><span class="sxs-lookup"><span data-stu-id="2f670-119">Infrastructure - Server Health</span></span>|<span data-ttu-id="2f670-120">显示 CPU 使用情况、内存消耗量和查询响应时间随时间推移而变化的趋势，以便您可以评估系统资源是接近最大容量还是未充分利用。</span><span class="sxs-lookup"><span data-stu-id="2f670-120">Shows trends in CPU usage, memory consumption, and query response times over time so that you can assess whether system resources are nearing maximum capacity or are under utilized.</span></span>|  
|<span data-ttu-id="2f670-121">操作</span><span class="sxs-lookup"><span data-stu-id="2f670-121">Actions</span></span>|<span data-ttu-id="2f670-122">包含指向管理中心中其他页的链接，包括当前服务应用程序、服务应用程序的列表和使用情况日志记录。</span><span class="sxs-lookup"><span data-stu-id="2f670-122">Contains links to other pages in Central Administration including the current service application, a list of service applications, and usage logging.</span></span>|  
|<span data-ttu-id="2f670-123">工作簿活动 - 图表</span><span class="sxs-lookup"><span data-stu-id="2f670-123">Workbook Activity - Chart</span></span>|<span data-ttu-id="2f670-124">有关数据访问频率的报表。</span><span class="sxs-lookup"><span data-stu-id="2f670-124">Reports on frequency of data access.</span></span> <span data-ttu-id="2f670-125">您可以了解每天或每周与 PowerPivot 数据源建立连接的频率。</span><span class="sxs-lookup"><span data-stu-id="2f670-125">You can learn how often connections to PowerPivot data sources occur on a daily or weekly basis.</span></span>|  
|<span data-ttu-id="2f670-126">工作簿活动 - 列表</span><span class="sxs-lookup"><span data-stu-id="2f670-126">Workbook Activity - Lists</span></span>|<span data-ttu-id="2f670-127">有关数据访问频率的报表。</span><span class="sxs-lookup"><span data-stu-id="2f670-127">Reports on frequency of data access.</span></span> <span data-ttu-id="2f670-128">您可以了解每天或每周与 PowerPivot 数据源建立连接的频率。</span><span class="sxs-lookup"><span data-stu-id="2f670-128">You can learn how often connections to PowerPivot data sources occur on a daily or weekly basis.</span></span>|  
|<span data-ttu-id="2f670-129">数据刷新 - 最近的活动</span><span class="sxs-lookup"><span data-stu-id="2f670-129">Data Refresh - Recent Activity</span></span>|<span data-ttu-id="2f670-130">有关数据刷新作业（包括运行失败的作业）的状态的报表。</span><span class="sxs-lookup"><span data-stu-id="2f670-130">Reports on the status of data refresh jobs, including jobs that failed to run.</span></span> <span data-ttu-id="2f670-131">此报表针对在应用程序级别执行的数据刷新操作提供了一个组合视图。</span><span class="sxs-lookup"><span data-stu-id="2f670-131">This report provides a composite view into data refresh operations at the application level.</span></span> <span data-ttu-id="2f670-132">管理员可以快速查看为整个 PowerPivot 服务应用程序定义的数据刷新作业的数目。</span><span class="sxs-lookup"><span data-stu-id="2f670-132">Administrators can see at a glance the number of data refresh jobs that are defined for the entire PowerPivot service application.</span></span>|  
|<span data-ttu-id="2f670-133">数据刷新 - 最近的失败</span><span class="sxs-lookup"><span data-stu-id="2f670-133">Data Refresh - Recent Failures</span></span>|<span data-ttu-id="2f670-134">列出未成功完成数据刷新的 PowerPivot 工作簿。</span><span class="sxs-lookup"><span data-stu-id="2f670-134">Lists the PowerPivot workbooks that did not complete data refresh successfully.</span></span>|  
|<span data-ttu-id="2f670-135">报表</span><span class="sxs-lookup"><span data-stu-id="2f670-135">Reports</span></span>|<span data-ttu-id="2f670-136">包含指向可以在 Excel 中打开的报表的链接。</span><span class="sxs-lookup"><span data-stu-id="2f670-136">Contains links to reports that you can open in Excel.</span></span>|  
  
##  <a name="open-powerpivot-management-dashboard"></a><a name="open"></a><span data-ttu-id="2f670-137">打开 PowerPivot 管理面板</span><span class="sxs-lookup"><span data-stu-id="2f670-137">Open PowerPivot Management Dashboard</span></span>  
 <span data-ttu-id="2f670-138">面板中一次显示一个 PowerPivot 服务应用程序的信息。</span><span class="sxs-lookup"><span data-stu-id="2f670-138">The dashboard shows information for one PowerPivot service application at a time.</span></span> <span data-ttu-id="2f670-139">您可以从两个不同的位置打开管理面板。</span><span class="sxs-lookup"><span data-stu-id="2f670-139">You can open the management dashboard from two different locations.</span></span>  
  
### <a name="open-the-dashboard-from-general-application-settings"></a><span data-ttu-id="2f670-140">从“常规应用程序设置”打开面板</span><span class="sxs-lookup"><span data-stu-id="2f670-140">Open the dashboard from General Application Settings</span></span>  
  
1.  <span data-ttu-id="2f670-141">在管理中心的 **“常规应用程序设置”** 组中，单击 **“PowerPivot 管理面板”**。</span><span class="sxs-lookup"><span data-stu-id="2f670-141">In Central Administration, in the **General Application Settings** group, click **PowerPivot Management Dashboard**.</span></span>  
  
2.  <span data-ttu-id="2f670-142">在主页上，选择您要查看其操作数据的 PowerPivot 服务应用程序。</span><span class="sxs-lookup"><span data-stu-id="2f670-142">On the main page, select the PowerPivot service application for which you want to view operations data.</span></span>  
  
### <a name="open-the-dashboard-from-a-powerpivot-service-application"></a><span data-ttu-id="2f670-143">从 PowerPivot 服务应用程序中打开该面板</span><span class="sxs-lookup"><span data-stu-id="2f670-143">Open the dashboard from a PowerPivot service application</span></span>  
  
1.  <span data-ttu-id="2f670-144">在管理中心的 "**应用程序管理**" 中，单击 "**管理服务应用程序**"。</span><span class="sxs-lookup"><span data-stu-id="2f670-144">In Central Administration, in **Application Management**, click **Manage service applications**.</span></span>  
  
2.  <span data-ttu-id="2f670-145">单击 PowerPivot 服务应用程序的名称。</span><span class="sxs-lookup"><span data-stu-id="2f670-145">Click the name of the PowerPivot service application.</span></span> <span data-ttu-id="2f670-146">PowerPivot 管理面板显示当前服务应用程序的操作数据。</span><span class="sxs-lookup"><span data-stu-id="2f670-146">The PowerPivot Management Dashboard displays operational data for the current service application.</span></span>  
  
### <a name="change-the-current-service-application"></a><span data-ttu-id="2f670-147">更改当前服务应用程序。</span><span class="sxs-lookup"><span data-stu-id="2f670-147">Change the current service application.</span></span>  
 <span data-ttu-id="2f670-148">在管理面板中更改当前 PowerPivot 服务应用程序：</span><span class="sxs-lookup"><span data-stu-id="2f670-148">To change current PowerPivot service application in the management dashboard:</span></span>  
  
1.  <span data-ttu-id="2f670-149">在 PowerPivot 管理面板顶部，记下当前服务应用程序的名称，例如**默认的 PowerPivot 服务应用**程序。</span><span class="sxs-lookup"><span data-stu-id="2f670-149">At the top of the PowerPivot management dashboard, note the name of the current service application, for example **Default PowerPivot Service Application**.</span></span>  
  
2.  <span data-ttu-id="2f670-150">在 **“操作”** 面板中单击 **“列出服务应用程序”**。</span><span class="sxs-lookup"><span data-stu-id="2f670-150">In the **Actions** dashboard, click **List Service Applications**.</span></span>  
  
3.  <span data-ttu-id="2f670-151">单击要查看管理面板报表的 PowerPivot 服务应用程序的名称。</span><span class="sxs-lookup"><span data-stu-id="2f670-151">Click the name of the PowerPivot Service application for which you want to see management dashboard reports.</span></span>  
  
##  <a name="source-data-in-dashboards"></a><a name="sourcedata"></a> <span data-ttu-id="2f670-152">面板中的源数据</span><span class="sxs-lookup"><span data-stu-id="2f670-152">Source Data in Dashboards</span></span>  
 <span data-ttu-id="2f670-153">面板、报表和 Web 部件显示的数据来自于一个内部数据模型，而该数据模型则从系统和 PowerPivot 应用程序数据库请求这些数据。</span><span class="sxs-lookup"><span data-stu-id="2f670-153">Dashboards, reports and web parts show data from an internal data model that pulls data from the system and PowerPivot application databases.</span></span> <span data-ttu-id="2f670-154">这个内部数据模型嵌入在一个承载于管理中心站点的 PowerPivot 工作簿中。</span><span class="sxs-lookup"><span data-stu-id="2f670-154">The internal data model is embedded in a PowerPivot workbook hosted in the Central Administration site.</span></span> <span data-ttu-id="2f670-155">该数据模型的结构是固定的。</span><span class="sxs-lookup"><span data-stu-id="2f670-155">The structure of the data model is fixed.</span></span> <span data-ttu-id="2f670-156">虽然可以使用 PowertPivot 工作簿作为数据源来创建新报表，但您不得以破坏使用该数据源的预定义报表的方式修改结构。</span><span class="sxs-lookup"><span data-stu-id="2f670-156">Although you can use the PowertPivot workbook as a data source to create new reports, you must not modify the structure in a way that breaks the predefined reports that use it.</span></span>  
  
 <span data-ttu-id="2f670-157">有关如何收集数据的详细信息，请参阅以下主题：</span><span class="sxs-lookup"><span data-stu-id="2f670-157">For more information about how data is collected, see the following:</span></span>  
  
-   [<span data-ttu-id="2f670-158">PowerPivot 使用情况数据收集</span><span class="sxs-lookup"><span data-stu-id="2f670-158">PowerPivot Usage Data Collection</span></span>](power-pivot-usage-data-collection.md)  
  
-   [<span data-ttu-id="2f670-159">为 &#40;配置使用情况数据收集 PowerPivot for SharePoint</span><span class="sxs-lookup"><span data-stu-id="2f670-159">Configure Usage Data Collection for &#40;PowerPivot for SharePoint</span></span>](configure-usage-data-collection-for-power-pivot-for-sharepoint.md)  
  
 <span data-ttu-id="2f670-160">为了捕获有关 PowerPivot 服务器系统的数据，请验证为每个 PowerPivot 服务应用程序启用了事件消息传递、数据刷新历史记录和其他使用情况历史记录。</span><span class="sxs-lookup"><span data-stu-id="2f670-160">To capture data about the PowerPivot server system, verify event messaging, data refresh history, and other usage history is enabled for each PowerPivot service application.</span></span> <span data-ttu-id="2f670-161">在服务器正常操作过程中收集的服务器和使用情况数据是最终完成此内部数据模型的源数据。</span><span class="sxs-lookup"><span data-stu-id="2f670-161">The server and usage data gathered during normal server operations is the source data that ends up in the internal data model.</span></span> <span data-ttu-id="2f670-162">**注意：** 如果您关闭事件或使用情况历史记录，则组合报表将会不完整或出错。</span><span class="sxs-lookup"><span data-stu-id="2f670-162">**Note:** If you turn off events or usage history, the composite reports will be incomplete or erroneous.</span></span>  
  
##  <a name="edit-powerpivot-dashboard"></a><a name="edit"></a><span data-ttu-id="2f670-163">编辑 PowerPivot 面板</span><span class="sxs-lookup"><span data-stu-id="2f670-163">Edit PowerPivot Dashboard</span></span>  
 <span data-ttu-id="2f670-164">如果您具有面板开发或自定义方面的专业知识，则可以编辑此面板以加入新的 Web 部件。</span><span class="sxs-lookup"><span data-stu-id="2f670-164">If you have expertise in dashboard development or customization, you can edit the dashboard to include new web parts.</span></span> <span data-ttu-id="2f670-165">还可以编辑包含在面板中的 Web 部件属性。</span><span class="sxs-lookup"><span data-stu-id="2f670-165">You can also edit the web part properties that are included in the dashboard.</span></span>  
  
##  <a name="create-custom-reports-for-powerpivot-management-dashboard"></a><a name="reports"></a><span data-ttu-id="2f670-166">为 PowerPivot 管理面板创建自定义报表</span><span class="sxs-lookup"><span data-stu-id="2f670-166">Create Custom Reports for PowerPivot Management Dashboard</span></span>  
 <span data-ttu-id="2f670-167">出于报告目的，PowerPivot 使用情况数据和历史记录保留在一个与面板一起创建和配置的内部 PowerPivot 工作簿中。</span><span class="sxs-lookup"><span data-stu-id="2f670-167">For reporting purposes, PowerPivot usage data and history is kept in an internal PowerPivot workbook that is created and configured along with the dashboard.</span></span> <span data-ttu-id="2f670-168">如果默认报表未提供所需信息，您可以在 Excel 中基于该工作簿创建自定义报表。</span><span class="sxs-lookup"><span data-stu-id="2f670-168">If the default reports do not provide the information you require, you can create custom reports in Excel based on the workbook.</span></span> <span data-ttu-id="2f670-169">如果您以后升级或卸载 PowerPivot 解决方案文件，该工作簿和您创建的任何自定义报表都会保留。</span><span class="sxs-lookup"><span data-stu-id="2f670-169">Both the workbook and any custom reports that you create will be preserved if you upgrade or uninstall the PowerPivot solution files later.</span></span> <span data-ttu-id="2f670-170">工作簿和报表存储在管理中心站点的 PowerPivot 管理库中。</span><span class="sxs-lookup"><span data-stu-id="2f670-170">The workbook and reports are stored in the PowerPivot Management library within the Central Administration site.</span></span> <span data-ttu-id="2f670-171">默认情况下此库不可见，但您可以使用“网站操作”下的“查看所有网站内容”操作来查看此库。</span><span class="sxs-lookup"><span data-stu-id="2f670-171">This library is not visible by default, but you can view the library using the View All Site Content action under Site Actions.</span></span>  
  
 <span data-ttu-id="2f670-172">为帮助开始进行自定义报表制作，PowerPivot 管理面板提供了一个 Office 数据连接 (.odc) 文件连接到源工作簿。</span><span class="sxs-lookup"><span data-stu-id="2f670-172">To help you get started with custom reporting, PowerPivot Management Dashboard provides an Office Data Connection (.odc) file to connect to the source workbook.</span></span> <span data-ttu-id="2f670-173">例如，您可以在 Excel 中使用 .odc 文件来创建其他报表。</span><span class="sxs-lookup"><span data-stu-id="2f670-173">Dor example, you can use the .odc file in Excel to create additional reports.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2f670-174">编辑此文件以避免当尝试在 Excel 中使用 .odc 文件时出现以下错误：“数据源初始化失败”。</span><span class="sxs-lookup"><span data-stu-id="2f670-174">Edit the file to avoid the following error when attempting to use the .odc file in Excel: "Initialization of the data source failed".</span></span> <span data-ttu-id="2f670-175">自动生成的 .odc 文件包含 MSOLAP OLE DB 访问接口不支持的一个参数。</span><span class="sxs-lookup"><span data-stu-id="2f670-175">The auto-generated .odc file includes a parameter that are not supported by the MSOLAP OLE DB provider.</span></span> <span data-ttu-id="2f670-176">以下说明介绍了用于删除这些参数的办法。</span><span class="sxs-lookup"><span data-stu-id="2f670-176">The following instructions provide the workaround for removing the parameters.</span></span>  
  
 <span data-ttu-id="2f670-177">您必须是场或服务管理员，才能生成基于管理中心内的 PowerPivot 工作簿的报表。</span><span class="sxs-lookup"><span data-stu-id="2f670-177">You must be a farm or service administrator to build reports that are based on the PowerPivot workbook in Central Administration.</span></span>  
  
1.  <span data-ttu-id="2f670-178">打开 PowerPivot 管理面板。</span><span class="sxs-lookup"><span data-stu-id="2f670-178">Open the PowerPivot Management Dashboard.</span></span>  
  
2.  <span data-ttu-id="2f670-179">滚动到页底部的 **“报表”** 部分。</span><span class="sxs-lookup"><span data-stu-id="2f670-179">Scroll to the **Reports** section at the bottom of the page.</span></span>  
  
3.  <span data-ttu-id="2f670-180">单击 **“PowerPivot 管理数据”**。</span><span class="sxs-lookup"><span data-stu-id="2f670-180">Click **PowerPivot Management Data**.</span></span>  
  
4.  <span data-ttu-id="2f670-181">将 .odc 文件保存到本地文件夹。</span><span class="sxs-lookup"><span data-stu-id="2f670-181">Save the .odc file to a local folder.</span></span>  
  
5.  <span data-ttu-id="2f670-182">在文本编辑器中打开 .odc 文件。</span><span class="sxs-lookup"><span data-stu-id="2f670-182">Open the .odc file in a text editor.</span></span>  
  
6.  <span data-ttu-id="2f670-183">在 `<odc:ConnectionString>` 元素中，滚动至行尾并删除 `Embedded Data=False`，然后删除 `Edit Mode=0`。</span><span class="sxs-lookup"><span data-stu-id="2f670-183">In the `<odc:ConnectionString>` element, scroll to the end of the line and remove `Embedded Data=False`, and then remove `Edit Mode=0`.</span></span> <span data-ttu-id="2f670-184">如果字符串中的最后一个字符为分号，则立即删除它。</span><span class="sxs-lookup"><span data-stu-id="2f670-184">If the last character in the string is a semicolon, remove it now.</span></span>  
  
7.  <span data-ttu-id="2f670-185">保存文件。</span><span class="sxs-lookup"><span data-stu-id="2f670-185">Save the File.</span></span> <span data-ttu-id="2f670-186">其余步骤取决于您使用的 PowerPivot 和 Excel 的版本。</span><span class="sxs-lookup"><span data-stu-id="2f670-186">The remaining steps depend on which version of PowerPivot and Excel you are using.</span></span>  
  
8.  1.  <span data-ttu-id="2f670-187">启动 Excel 2013</span><span class="sxs-lookup"><span data-stu-id="2f670-187">Start Excel 2013</span></span>  
  
    2.  <span data-ttu-id="2f670-188">在 **PowerPivot** 功能区中，单击 **“管理”**。</span><span class="sxs-lookup"><span data-stu-id="2f670-188">In the **PowerPivot** ribbon, click **Manage**.</span></span>  
  
    3.  <span data-ttu-id="2f670-189">单击 **“获取外部数据”** ，然后单击 **“现有连接”**。</span><span class="sxs-lookup"><span data-stu-id="2f670-189">Click **Get External Data** and then click **Existing connections**.</span></span>  
  
    4.  <span data-ttu-id="2f670-190">如果看到 .ODC 文件，请单击它。</span><span class="sxs-lookup"><span data-stu-id="2f670-190">Click the .ODC file if you see it.</span></span> <span data-ttu-id="2f670-191">如果看不到 .ODC 文件，请单击 **“浏览更多”** ，然后在文件路径中指定 .odc 文件。</span><span class="sxs-lookup"><span data-stu-id="2f670-191">If you do not see the .ODC file, click **Browse for More** and then in the file path, specify the .odc file.</span></span>  
  
    5.  <span data-ttu-id="2f670-192">单击**打开**</span><span class="sxs-lookup"><span data-stu-id="2f670-192">Click **Open**</span></span>  
  
    6.  <span data-ttu-id="2f670-193">单击 **“测试连接”** 以验证连接成功。</span><span class="sxs-lookup"><span data-stu-id="2f670-193">Click **Test Connection** to verify the connection succeeds.</span></span>  
  
    7.  <span data-ttu-id="2f670-194">单击键入连接的名称，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="2f670-194">Click type a name for the connection and then click **Next**.</span></span>  
  
    8.  <span data-ttu-id="2f670-195">在 "指定 MDX 查询" 中，单击 "**设计**" 打开 MDX 查询设计器以组合您要使用的数据。**如果您看到错误消息**"编辑模式属性名称格式不正确"，请验证编辑。.ODC 文件。</span><span class="sxs-lookup"><span data-stu-id="2f670-195">In Specify MDX Query, click **Design** to open the MDX query designer to assemble the data you want to work with **If you see the error message** "The Edit Mode property name is not formatted correctly.", verify you edits the .ODC file.</span></span>  
  
    9. <span data-ttu-id="2f670-196">单击 **"确定"** ，然后单击 "**完成**"。</span><span class="sxs-lookup"><span data-stu-id="2f670-196">Click **OK** and then click **Finish**.</span></span>  
  
    10. <span data-ttu-id="2f670-197">创建数据透视表或数据透视图报表以便在 Excel 中直观显示数据。</span><span class="sxs-lookup"><span data-stu-id="2f670-197">Create PivotTable or PivotChart reports to visualize the data in Excel.</span></span>  
  
9. 1.  <span data-ttu-id="2f670-198">启动 Excel 2010。</span><span class="sxs-lookup"><span data-stu-id="2f670-198">Start Excel 2010.</span></span>  
  
    2.  <span data-ttu-id="2f670-199">在 PowerPivot 功能区中，单击 **“启动 PowerPivot 窗口”**。</span><span class="sxs-lookup"><span data-stu-id="2f670-199">On the PowerPivot ribbon, click **Launch PowerPivot Window**.</span></span>  
  
    3.  <span data-ttu-id="2f670-200">在 PowerPivot 窗口的“设计”功能区中，单击 **“现有连接”**。</span><span class="sxs-lookup"><span data-stu-id="2f670-200">On the Design ribbon in the PowerPivot window, click **Existing Connections**.</span></span>  
  
    4.  <span data-ttu-id="2f670-201">单击 **“浏览更多”**。</span><span class="sxs-lookup"><span data-stu-id="2f670-201">Click **Browse for More**.</span></span>  
  
    5.  <span data-ttu-id="2f670-202">在文件路径中，指定 .odc 文件。</span><span class="sxs-lookup"><span data-stu-id="2f670-202">In the file path, specify the .odc file.</span></span>  
  
    6.  <span data-ttu-id="2f670-203">单击 **“打开”** 。</span><span class="sxs-lookup"><span data-stu-id="2f670-203">Click **Open**.</span></span> <span data-ttu-id="2f670-204">此时，将使用指向包含使用情况数据的 PowerPivot 工作簿的连接字符串启动“表导入向导”。</span><span class="sxs-lookup"><span data-stu-id="2f670-204">The Table Import Wizard starts, using the connection string to the PowerPivot workbook that contains usage data.</span></span>  
  
    7.  <span data-ttu-id="2f670-205">单击 **“测试连接”** 以确认您具有访问权限。</span><span class="sxs-lookup"><span data-stu-id="2f670-205">Click **Test Connection** to verify that you have access.</span></span>  
  
    8.  <span data-ttu-id="2f670-206">输入连接的友好名称，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="2f670-206">Enter a friendly name for the connection, and then click **Next**.</span></span>  
  
    9. <span data-ttu-id="2f670-207">在“指定 MDX 查询”中，单击 **“设计”** 打开 MDX 查询设计器以组合您要使用的数据，然后创建数据透视表或数据透视图报表以便在 Excel 中直观显示数据。</span><span class="sxs-lookup"><span data-stu-id="2f670-207">In Specify MDX Query, click **Design** to open the MDX query designer to assemble the data you want to work with, and then create PivotTable or PivotChart reports to visualize the data in Excel.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f670-208">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2f670-208">See Also</span></span>  
 <span data-ttu-id="2f670-209">[通过 SharePoint 2010 进行 PowerPivot 数据刷新](../powerpivot-data-refresh-with-sharepoint-2010.md) </span><span class="sxs-lookup"><span data-stu-id="2f670-209">[PowerPivot Data Refresh with SharePoint 2010](../powerpivot-data-refresh-with-sharepoint-2010.md) </span></span>  
 [<span data-ttu-id="2f670-210">为 &#40;配置使用情况数据收集 PowerPivot for SharePoint</span><span class="sxs-lookup"><span data-stu-id="2f670-210">Configure Usage Data Collection for &#40;PowerPivot for SharePoint</span></span>](configure-usage-data-collection-for-power-pivot-for-sharepoint.md)  
  
  
