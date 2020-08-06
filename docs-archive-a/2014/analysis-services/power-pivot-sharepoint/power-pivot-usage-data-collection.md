---
title: PowerPivot 使用情况数据收集 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 9057cb89-fb17-466e-a1ce-192c8ca20692
author: minewiskan
ms.author: owend
ms.openlocfilehash: b04ec76284208d6d0d721208987f50223c1418f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587015"
---
# <a name="powerpivot-usage-data-collection"></a><span data-ttu-id="382c3-102">PowerPivot 使用情况数据收集</span><span class="sxs-lookup"><span data-stu-id="382c3-102">PowerPivot Usage Data Collection</span></span>
  <span data-ttu-id="382c3-103">使用情况数据收集是场级 SharePoint 功能。</span><span class="sxs-lookup"><span data-stu-id="382c3-103">Usage data collection is a farm-level SharePoint feature.</span></span> <span data-ttu-id="382c3-104">PowerPivot for SharePoint 使用并扩展此系统以便在 PowerPivot 管理面板中提供显示 PowerPivot 数据和服务的使用情况的报告。</span><span class="sxs-lookup"><span data-stu-id="382c3-104">PowerPivot for SharePoint uses and extends this system to provide reports in the PowerPivot Management Dashboard that show how PowerPivot data and services are used.</span></span> <span data-ttu-id="382c3-105">根据您安装 SharePoint 的方式，可能会为场禁用使用情况数据收集。</span><span class="sxs-lookup"><span data-stu-id="382c3-105">Depending on how you install SharePoint, usage data collection might be turned off for the farm.</span></span> <span data-ttu-id="382c3-106">场管理员必须启用使用情况日志记录，才能创建显示在 PowerPivot 管理面板中的使用情况数据。</span><span class="sxs-lookup"><span data-stu-id="382c3-106">A farm administrator must enable usage logging to create the usage data that appears in the PowerPivot Management Dashboard.</span></span> <span data-ttu-id="382c3-107">有关如何为 PowerPivot 事件启用和配置使用情况数据收集的详细信息，请参阅[为 &#40;PowerPivot for SharePoint 配置使用情况数据收集](configure-usage-data-collection-for-power-pivot-for-sharepoint.md)。</span><span class="sxs-lookup"><span data-stu-id="382c3-107">For more information on how to enable and configure usage data collection for PowerPivot events see [Configure Usage Data Collection for &#40;PowerPivot for SharePoint](configure-usage-data-collection-for-power-pivot-for-sharepoint.md).</span></span>  
  
 <span data-ttu-id="382c3-108">有关 PowerPivot 管理面板中使用情况数据的信息，请参阅 [PowerPivot Management Dashboard and Usage Data](power-pivot-management-dashboard-and-usage-data.md)。</span><span class="sxs-lookup"><span data-stu-id="382c3-108">For information on usage data in the PowerPivot Management Dashboard, see [PowerPivot Management Dashboard and Usage Data](power-pivot-management-dashboard-and-usage-data.md).</span></span>  
  
 <span data-ttu-id="382c3-109">**本主题内容：**</span><span class="sxs-lookup"><span data-stu-id="382c3-109">**In this topic:**</span></span>  
  
 [<span data-ttu-id="382c3-110">使用情况数据收集和报告体系结构</span><span class="sxs-lookup"><span data-stu-id="382c3-110">Usage Data Collection and Reporting Architecture</span></span>](#usagearch)  
  
 [<span data-ttu-id="382c3-111">使用情况数据的来源</span><span class="sxs-lookup"><span data-stu-id="382c3-111">Sources of Usage Data</span></span>](#sources)  
  
 [<span data-ttu-id="382c3-112">服务和计时器作业</span><span class="sxs-lookup"><span data-stu-id="382c3-112">Services and Timer Jobs</span></span>](#servicesjobs)  
  
 [<span data-ttu-id="382c3-113">报告使用情况数据</span><span class="sxs-lookup"><span data-stu-id="382c3-113">Reporting on Usage Data</span></span>](#reporting)  
  
##  <a name="usage-data-collection-and-reporting-architecture"></a><a name="usagearch"></a> <span data-ttu-id="382c3-114">使用情况数据收集和报告体系结构</span><span class="sxs-lookup"><span data-stu-id="382c3-114">Usage Data Collection and Reporting Architecture</span></span>  
 <span data-ttu-id="382c3-115">使用 SharePoint 基础结构和 PowerPivot 服务器组件中功能的组合收集、存储和管理 PowerPivot 使用情况数据。</span><span class="sxs-lookup"><span data-stu-id="382c3-115">PowerPivot usage data is collected, stored, and managed using a combination of features from the SharePoint infrastructure and PowerPivot server components.</span></span> <span data-ttu-id="382c3-116">SharePoint 基础结构提供了集中的使用情况服务和内置的计时器作业。</span><span class="sxs-lookup"><span data-stu-id="382c3-116">SharePoint infrastructure provides a centralized usage service and built-in timer jobs.</span></span> <span data-ttu-id="382c3-117">PowerPivot for SharePoint 为您在 SharePoint 管理中心中查看的 PowerPivot 使用情况数据和报告添加了更长期的存储。</span><span class="sxs-lookup"><span data-stu-id="382c3-117">PowerPivot for SharePoint adds longer term storage for PowerPivot usage data and reports that you view in SharePoint Central Administration.</span></span>  
  
 <span data-ttu-id="382c3-118">在使用情况数据收集系统中，事件信息进入应用程序服务器或 Web 前端上的使用情况收集系统。</span><span class="sxs-lookup"><span data-stu-id="382c3-118">In the usage data collection system, event information enters the usage collection system on the application server or Web front end.</span></span> <span data-ttu-id="382c3-119">使用情况数据在系统中移动以便响应计时器作业，这些计时器作业导致数据从物理服务器上的临时数据文件移到数据库服务器上的永久存储区中。</span><span class="sxs-lookup"><span data-stu-id="382c3-119">Usage data moves through the system in response to timer jobs that cause data to move from temporary data files on the physical server to persistent storage on a database server.</span></span> <span data-ttu-id="382c3-120">下图说明了通过数据收集和报告系统移动使用情况数据的组件和过程。</span><span class="sxs-lookup"><span data-stu-id="382c3-120">The following diagram illustrates the components and processes that move usage data through the data collection and reporting system.</span></span>  
  
 <span data-ttu-id="382c3-121">**注意：** 请验证启用了使用情况数据收集。</span><span class="sxs-lookup"><span data-stu-id="382c3-121">**Note:** Verify usage data collection is enabled.</span></span> <span data-ttu-id="382c3-122">要进行验证，请在 SharePoint 管理中心中转到 **“监视”** 。</span><span class="sxs-lookup"><span data-stu-id="382c3-122">To verify, go to **Monitoring** in SharePoint Central Administration.</span></span> <span data-ttu-id="382c3-123">有关详细信息，请参阅[为 &#40;PowerPivot for SharePoint 配置使用情况数据收集](configure-usage-data-collection-for-power-pivot-for-sharepoint.md)。</span><span class="sxs-lookup"><span data-stu-id="382c3-123">For more information, see [Configure Usage Data Collection for &#40;PowerPivot for SharePoint](configure-usage-data-collection-for-power-pivot-for-sharepoint.md).</span></span>  
  
 <span data-ttu-id="382c3-124">![使用情况数据收集的组件和过程。](../media/gmni-usagedata.gif "使用情况数据收集的组件和过程。")</span><span class="sxs-lookup"><span data-stu-id="382c3-124">![Components and processes of usage data collection.](../media/gmni-usagedata.gif "Components and processes of usage data collection.")</span></span>  
  
|<span data-ttu-id="382c3-125">阶段</span><span class="sxs-lookup"><span data-stu-id="382c3-125">Phase</span></span>|<span data-ttu-id="382c3-126">说明</span><span class="sxs-lookup"><span data-stu-id="382c3-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="382c3-127">1</span><span class="sxs-lookup"><span data-stu-id="382c3-127">1</span></span>|<span data-ttu-id="382c3-128">使用情况数据收集由 SharePoint 部署中的 PowerPivot 组件和 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据访问接口所生成的事件触发。</span><span class="sxs-lookup"><span data-stu-id="382c3-128">Usage data collection is triggered by events that are generated by PowerPivot components and [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] data providers in SharePoint deployments.</span></span> <span data-ttu-id="382c3-129">可启用或禁用的可配置事件包括连接请求、加载和卸载请求以及应用程序服务器上 PowerPivot 服务监视的查询响应计时事件。</span><span class="sxs-lookup"><span data-stu-id="382c3-129">Configurable events that can be turned on or off include connection requests, load and unload requests, and query response timing events that are monitored by the PowerPivot service on the application server.</span></span> <span data-ttu-id="382c3-130">由服务器管理单独并且不能禁用的其他事件。</span><span class="sxs-lookup"><span data-stu-id="382c3-130">Other events that are managed solely by the server and cannot be turned off.</span></span> <span data-ttu-id="382c3-131">这些事件包括数据刷新事件和服务器运行状况事件。</span><span class="sxs-lookup"><span data-stu-id="382c3-131">These include data refresh and server health events.</span></span><br /><br /> <span data-ttu-id="382c3-132">最初，使用 SharePoint 系统的数据收集功能在本地日志文件中收集和存储使用情况数据。</span><span class="sxs-lookup"><span data-stu-id="382c3-132">Initially, usage data is collected and stored in local log files using the data collection features of the SharePoint system.</span></span> <span data-ttu-id="382c3-133">这些文件和它们的位置是 SharePoint 中标准使用情况数据收集系统的一部分。</span><span class="sxs-lookup"><span data-stu-id="382c3-133">The files and their location are part of the standard usage data collection system in SharePoint.</span></span> <span data-ttu-id="382c3-134">文件的位置在场中的每个服务器上均相同。</span><span class="sxs-lookup"><span data-stu-id="382c3-134">The location of the files is the same on every server in the farm.</span></span> <span data-ttu-id="382c3-135">要查看或更改日志记录目录的位置，请在 SharePoint 管理中心中转到 **“监视”** ，然后单击 **“配置 Usage and Health Data Collection”**。</span><span class="sxs-lookup"><span data-stu-id="382c3-135">To view or change the location of the logging directory, go to **Monitoring** in SharePoint Central Administration, and then click **Configure usage and health data collection**.</span></span>|  
|<span data-ttu-id="382c3-136">2</span><span class="sxs-lookup"><span data-stu-id="382c3-136">2</span></span>|<span data-ttu-id="382c3-137">“Microsoft SharePoint Foundation 使用情况数据导入”计时器作业按照计划的间隔（默认为每小时）将使用情况数据从本地文件移到 PowerPivot 服务应用程序数据库。</span><span class="sxs-lookup"><span data-stu-id="382c3-137">At scheduled intervals (every hour by default) the Microsoft SharePoint Foundation Usage Data Import timer job moves usage data from the local files to the PowerPivot service application database.</span></span> <span data-ttu-id="382c3-138">如果您在场中具有多个 PowerPivot 服务应用程序，则每个应用程序都将具有自己的数据库。</span><span class="sxs-lookup"><span data-stu-id="382c3-138">If you have multiple PowerPivot service applications in a farm, each one will have its own database.</span></span> <span data-ttu-id="382c3-139">事件包含标识哪个 PowerPivot 服务应用程序生成此事件的内部信息。</span><span class="sxs-lookup"><span data-stu-id="382c3-139">Events include internal information that identifies which PowerPivot service application produced the event.</span></span> <span data-ttu-id="382c3-140">应用程序标识符确保使用情况数据绑定到创建它的应用程序。</span><span class="sxs-lookup"><span data-stu-id="382c3-140">The application identifiers ensure that usage data is bound to the application that created it.</span></span>|  
|<span data-ttu-id="382c3-141">3</span><span class="sxs-lookup"><span data-stu-id="382c3-141">3</span></span>|<span data-ttu-id="382c3-142">数据复制到可用于管理中心中的 PowerPivot 管理面板的内部报告数据库。</span><span class="sxs-lookup"><span data-stu-id="382c3-142">Data is copied to an internal reporting database that is available to the PowerPivot Management Dashboard in Central Administration.</span></span>|  
|<span data-ttu-id="382c3-143">4</span><span class="sxs-lookup"><span data-stu-id="382c3-143">4</span></span>|<span data-ttu-id="382c3-144">该数据源是您可以访问以便在 Excel 中创建自定义报告的 PowerPivot 工作簿。</span><span class="sxs-lookup"><span data-stu-id="382c3-144">The data source is a PowerPivot workbook that you can access to create custom reports in Excel.</span></span> <span data-ttu-id="382c3-145">只有源工作簿的一个实例。</span><span class="sxs-lookup"><span data-stu-id="382c3-145">There is only one instance of the source workbook.</span></span> <span data-ttu-id="382c3-146">本地化的报告都基于相同的源工作簿。</span><span class="sxs-lookup"><span data-stu-id="382c3-146">The localized reports are all based on the same source workbook.</span></span>|  
|<span data-ttu-id="382c3-147">5</span><span class="sxs-lookup"><span data-stu-id="382c3-147">5</span></span>|<span data-ttu-id="382c3-148">使用情况数据展示在报告中，供管理服务器性能和可用性的 PowerPivot 服务应用程序管理员查看。</span><span class="sxs-lookup"><span data-stu-id="382c3-148">Usage data is presented in reports for PowerPivot service applications for administrators who manage server performance and availability.</span></span> <span data-ttu-id="382c3-149">为支持的 SharePoint 语言创建工作簿的本地化实例。</span><span class="sxs-lookup"><span data-stu-id="382c3-149">Localized instances of the workbooks are created for the supported SharePoint languages.</span></span><br /><br /> <span data-ttu-id="382c3-150">有关详细信息，请参阅本主题中的 [使用情况数据报告](#reporting) 。</span><span class="sxs-lookup"><span data-stu-id="382c3-150">For more information, see [Reporting on Usage Data](#reporting) in this topic.</span></span>|  
  
##  <a name="sources-of-usage-data"></a><a name="sources"></a> <span data-ttu-id="382c3-151">使用情况数据的来源</span><span class="sxs-lookup"><span data-stu-id="382c3-151">Sources of Usage Data</span></span>  
 <span data-ttu-id="382c3-152">在启用使用情况数据收集后，将为以下服务器事件生成数据。</span><span class="sxs-lookup"><span data-stu-id="382c3-152">When usage data collection is enabled, data is generated for the following server events.</span></span>  
  
|<span data-ttu-id="382c3-153">事件</span><span class="sxs-lookup"><span data-stu-id="382c3-153">Event</span></span>|<span data-ttu-id="382c3-154">说明</span><span class="sxs-lookup"><span data-stu-id="382c3-154">Description</span></span>|<span data-ttu-id="382c3-155">可配置</span><span class="sxs-lookup"><span data-stu-id="382c3-155">Configurable</span></span>|  
|-----------|-----------------|------------------|  
|<span data-ttu-id="382c3-156">连接</span><span class="sxs-lookup"><span data-stu-id="382c3-156">Connections</span></span>|<span data-ttu-id="382c3-157">代表在 Excel 工作簿中查询 PowerPivot 数据的用户进行的服务器连接。</span><span class="sxs-lookup"><span data-stu-id="382c3-157">Server connections made on behalf of a user who is querying PowerPivot data in an Excel workbook.</span></span> <span data-ttu-id="382c3-158">连接事件标识打开了与 PowerPivot 工作簿的连接的用户。</span><span class="sxs-lookup"><span data-stu-id="382c3-158">Connection events identify who opened a connection to a PowerPivot workbook.</span></span> <span data-ttu-id="382c3-159">在报告中，该信息用于标识最连接频繁的用户、相同用户访问的 PowerPivot 数据源以及连接随时间变化的趋势。</span><span class="sxs-lookup"><span data-stu-id="382c3-159">In reports, this information is used to identify the most frequent users, the PowerPivot data sources that are accessed by the same users, and trends in connections over time.</span></span>|<span data-ttu-id="382c3-160">可以[为 &#40;PowerPivot for SharePoint 启用和禁用配置使用情况数据收集](configure-usage-data-collection-for-power-pivot-for-sharepoint.md)。</span><span class="sxs-lookup"><span data-stu-id="382c3-160">You can enable and disable [Configure Usage Data Collection for &#40;PowerPivot for SharePoint](configure-usage-data-collection-for-power-pivot-for-sharepoint.md).</span></span>|  
|<span data-ttu-id="382c3-161">查询响应时间</span><span class="sxs-lookup"><span data-stu-id="382c3-161">Query response times</span></span>|<span data-ttu-id="382c3-162">基于完成时间的长短对查询进行分类的查询响应统计信息。</span><span class="sxs-lookup"><span data-stu-id="382c3-162">Query response statistics that categorize queries based on how long they take to complete.</span></span> <span data-ttu-id="382c3-163">查询响应统计信息显示服务器响应查询请求的时间长度中的模式。</span><span class="sxs-lookup"><span data-stu-id="382c3-163">Query response statistics show patterns in how long it takes the server to respond to query requests.</span></span>|<span data-ttu-id="382c3-164">可以[为 &#40;PowerPivot for SharePoint 启用和禁用配置使用情况数据收集](configure-usage-data-collection-for-power-pivot-for-sharepoint.md)。</span><span class="sxs-lookup"><span data-stu-id="382c3-164">You can enable and disable [Configure Usage Data Collection for &#40;PowerPivot for SharePoint](configure-usage-data-collection-for-power-pivot-for-sharepoint.md).</span></span>|  
|<span data-ttu-id="382c3-165">数据加载</span><span class="sxs-lookup"><span data-stu-id="382c3-165">Data load</span></span>|<span data-ttu-id="382c3-166">[!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)]执行的数据加载操作。</span><span class="sxs-lookup"><span data-stu-id="382c3-166">Data load operations by the [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)].</span></span> <span data-ttu-id="382c3-167">数据加载事件标识最常用的数据源。</span><span class="sxs-lookup"><span data-stu-id="382c3-167">Data load events identify which data sources are used most often.</span></span>|<span data-ttu-id="382c3-168">可以[为 &#40;PowerPivot for SharePoint 启用和禁用配置使用情况数据收集](configure-usage-data-collection-for-power-pivot-for-sharepoint.md)。</span><span class="sxs-lookup"><span data-stu-id="382c3-168">You can enable and disable [Configure Usage Data Collection for &#40;PowerPivot for SharePoint](configure-usage-data-collection-for-power-pivot-for-sharepoint.md).</span></span>|  
|<span data-ttu-id="382c3-169">数据卸载</span><span class="sxs-lookup"><span data-stu-id="382c3-169">Data unload</span></span>|<span data-ttu-id="382c3-170">由 PowerPivot 服务应用程序执行的数据卸载操作。</span><span class="sxs-lookup"><span data-stu-id="382c3-170">Data unload operations by PowerPivot service applications.</span></span> <span data-ttu-id="382c3-171">如果 PowerPivot 数据源未在使用，或者在服务器处于内存压力下或需要额外的内存来运行数据刷新作业时，则 [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)]将卸载非活动状态的 PowerPivot 数据源。</span><span class="sxs-lookup"><span data-stu-id="382c3-171">An [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] unloads inactive PowerPivot data sources if it is not being used, or when the server is under memory pressure or needs additional memory to run data refresh jobs.</span></span>|<span data-ttu-id="382c3-172">可以[为 &#40;PowerPivot for SharePoint 启用和禁用配置使用情况数据收集](configure-usage-data-collection-for-power-pivot-for-sharepoint.md)。</span><span class="sxs-lookup"><span data-stu-id="382c3-172">You can enable and disable [Configure Usage Data Collection for &#40;PowerPivot for SharePoint](configure-usage-data-collection-for-power-pivot-for-sharepoint.md).</span></span>|  
|<span data-ttu-id="382c3-173">服务器运行状况</span><span class="sxs-lookup"><span data-stu-id="382c3-173">Server health</span></span>|<span data-ttu-id="382c3-174">指示服务器运行状况的服务器操作，以 CPU 和内存使用率度量。</span><span class="sxs-lookup"><span data-stu-id="382c3-174">Server operations that indicate server health, measured in CPU and memory utilization.</span></span> <span data-ttu-id="382c3-175">此数据是历史数据。</span><span class="sxs-lookup"><span data-stu-id="382c3-175">This data is historical.</span></span> <span data-ttu-id="382c3-176">它不提供与服务器上的当前处理负载有关的实时信息。</span><span class="sxs-lookup"><span data-stu-id="382c3-176">It does not provide real time information about the current processing load on the server.</span></span>|<span data-ttu-id="382c3-177">否。</span><span class="sxs-lookup"><span data-stu-id="382c3-177">No.</span></span> <span data-ttu-id="382c3-178">始终为此事件收集使用情况数据。</span><span class="sxs-lookup"><span data-stu-id="382c3-178">Usage data is always collected for this event.</span></span>|  
|<span data-ttu-id="382c3-179">数据刷新</span><span class="sxs-lookup"><span data-stu-id="382c3-179">Data refresh</span></span>|<span data-ttu-id="382c3-180">由 PowerPivot 服务为计划的数据更新启动的数据刷新操作。</span><span class="sxs-lookup"><span data-stu-id="382c3-180">Data refresh operations initiated by the PowerPivot service for scheduled data updates.</span></span> <span data-ttu-id="382c3-181">在应用程序级别收集有关数据刷新的使用情况历史记录以便生成操作报告，并且此历史记录反映在各个工作簿的“管理数据刷新”页中。</span><span class="sxs-lookup"><span data-stu-id="382c3-181">Usage history for data refresh is collected at the application level for operational reports, and is reflected in the Manage Data Refresh pages for individual workbooks.</span></span><br /><br /> <span data-ttu-id="382c3-182">**注意：** 对于 [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] 和 SharePoint 2013 部署，数据刷新由 Excel Services 而不是 Analysis Services 服务器管理。</span><span class="sxs-lookup"><span data-stu-id="382c3-182">**Note:** For [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] and SharePoint 2013 deployments, data refresh is managed by Excel Services and not the Analysis Services Server.</span></span>|<span data-ttu-id="382c3-183">否。</span><span class="sxs-lookup"><span data-stu-id="382c3-183">No.</span></span> <span data-ttu-id="382c3-184">如果您为 PowerPivot 服务应用程序启用数据刷新，则始终收集数据刷新使用情况数据。</span><span class="sxs-lookup"><span data-stu-id="382c3-184">Data refresh usage data is always collected if you enable data refresh for the PowerPivot service application.</span></span>|  
  
##  <a name="services-and-timer-jobs"></a><a name="servicesjobs"></a> <span data-ttu-id="382c3-185">服务和计时器作业</span><span class="sxs-lookup"><span data-stu-id="382c3-185">Services and Timer Jobs</span></span>  
 <span data-ttu-id="382c3-186">下表描述使用情况数据收集系统中的服务和数据集存储区。</span><span class="sxs-lookup"><span data-stu-id="382c3-186">The following table describes the services and data collection stores in the usage data collection system.</span></span> <span data-ttu-id="382c3-187">有关如何覆盖计时器作业计划以强制对 PowerPivot 管理面板报表中的服务器运行状况和使用情况数据进行数据刷新的说明，请参阅[使用 SharePoint 2010 进行 Powerpivot 数据刷新](../powerpivot-data-refresh-with-sharepoint-2010.md)。</span><span class="sxs-lookup"><span data-stu-id="382c3-187">For instructions on how to override the timer job schedules to force a data refresh of server health and usage data in PowerPivot Management Dashboard reports, see [PowerPivot Data Refresh with SharePoint 2010](../powerpivot-data-refresh-with-sharepoint-2010.md).</span></span> <span data-ttu-id="382c3-188">您可以查看 SharePoint 管理中心中的计时器作业。</span><span class="sxs-lookup"><span data-stu-id="382c3-188">You can see the timer jobs in SharePoint central Administration.</span></span> <span data-ttu-id="382c3-189">转到 **“监视”**，然后单击 **“检查作业状态”**。</span><span class="sxs-lookup"><span data-stu-id="382c3-189">Go to **Monitoring**, then click **Check Job Status**.</span></span> <span data-ttu-id="382c3-190">单击 **“检查作业定义”**。</span><span class="sxs-lookup"><span data-stu-id="382c3-190">Click **Review Job Definitions**.</span></span>  
  
|<span data-ttu-id="382c3-191">组件</span><span class="sxs-lookup"><span data-stu-id="382c3-191">Component</span></span>|<span data-ttu-id="382c3-192">默认计划</span><span class="sxs-lookup"><span data-stu-id="382c3-192">Default schedule</span></span>|<span data-ttu-id="382c3-193">说明</span><span class="sxs-lookup"><span data-stu-id="382c3-193">Description</span></span>|  
|---------------|----------------------|-----------------|  
|<span data-ttu-id="382c3-194">SharePoint 计时器服务 (SPTimerV4)</span><span class="sxs-lookup"><span data-stu-id="382c3-194">SharePoint Timer Service (SPTimerV4)</span></span>||<span data-ttu-id="382c3-195">该 Windows 服务在场中的每个成员计算机上的本地运行，并且处理在场级别定义的所有计时器作业。</span><span class="sxs-lookup"><span data-stu-id="382c3-195">This Windows service runs locally on every member computer in the farm and processes all timer jobs that are defined at the farm level.</span></span>|  
|<span data-ttu-id="382c3-196">Microsoft SharePoint Foundation 使用情况数据导入</span><span class="sxs-lookup"><span data-stu-id="382c3-196">Microsoft SharePoint Foundation Usage Data Import</span></span>|<span data-ttu-id="382c3-197">在 SharePoint 2010 中每隔 30 分钟。</span><span class="sxs-lookup"><span data-stu-id="382c3-197">Every 30 minutes in SharePoint 2010.</span></span> <span data-ttu-id="382c3-198">在 SharePoint 2013 中每隔 5 分钟。</span><span class="sxs-lookup"><span data-stu-id="382c3-198">Every 5 minutes in SharePoint 2013.</span></span>|<span data-ttu-id="382c3-199">此计时器作业在场级别全局配置。</span><span class="sxs-lookup"><span data-stu-id="382c3-199">This timer job is configured globally at the farm level.</span></span> <span data-ttu-id="382c3-200">它将使用情况数据从本地使用情况日志文件移到中心使用情况数据收集数据库。</span><span class="sxs-lookup"><span data-stu-id="382c3-200">It moves usage data from local usage log files to the central usage data collection database.</span></span> <span data-ttu-id="382c3-201">您可以手动运行此计时器作业以便强制数据导入操作。</span><span class="sxs-lookup"><span data-stu-id="382c3-201">You can run this timer job manually to force a data import operation.</span></span>|  
|<span data-ttu-id="382c3-202">Microsoft SharePoint Foundation 使用情况数据处理计时器作业</span><span class="sxs-lookup"><span data-stu-id="382c3-202">Microsoft SharePoint Foundation Usage Data Processing timer job</span></span>|<span data-ttu-id="382c3-203">每天凌晨 3:00。</span><span class="sxs-lookup"><span data-stu-id="382c3-203">Daily at 3:00 A.M.</span></span>|<span data-ttu-id="382c3-204">从 SQL Server 2012 PowerPivot for SharePoint 开始\*\* \*)  (\*\* ，此时间作业支持升级或迁移方案，在这些方案中，你可能仍在 SharePoint 使用情况数据库中具有较旧的使用情况数据。</span><span class="sxs-lookup"><span data-stu-id="382c3-204">**(\*)** Starting with SQL Server 2012 PowerPivot for SharePoint, this Time job is supported for upgrade or migration scenarios where you may have older usage data still in the SharePoint usage databases.</span></span> <span data-ttu-id="382c3-205">从 SQL Server 2012 PowerPivot for SharePoint 开始，SharePoint 使用情况数据库不用于 PowerPivot 使用情况收集和管理面板工作流。</span><span class="sxs-lookup"><span data-stu-id="382c3-205">Starting with SQL Server 2012 PowerPivot for SharePoint, the SharePoint usage database is not used for PowerPivot usage collection and Management dashboard workflow.</span></span> <span data-ttu-id="382c3-206">可以手动运行此计时器作业，以将 SharePoint 使用情况数据库中的其余 PowerPivot 相关数据移到 PowerPivot 服务应用程序数据库。</span><span class="sxs-lookup"><span data-stu-id="382c3-206">The time job can be manually run to move any remaining PowerPivot related data in the SharePoint usage database to the PowerPivot service application databases.</span></span><br /><br /> <span data-ttu-id="382c3-207">此计时器作业在场级别全局配置。</span><span class="sxs-lookup"><span data-stu-id="382c3-207">This timer job is configured globally at the farm level.</span></span> <span data-ttu-id="382c3-208">它在中心使用情况数据收集数据库中检查到期的使用情况数据（即早于 30 天的任何记录）。</span><span class="sxs-lookup"><span data-stu-id="382c3-208">It checks for expired usage data in the central usage data collection database (that is, any records that are older than 30 days).</span></span> <span data-ttu-id="382c3-209">对于场中的 PowerPivot 服务器，此计时器作业为 PowerPivot 使用情况数据执行其他检查。</span><span class="sxs-lookup"><span data-stu-id="382c3-209">For PowerPivot servers in the farm, this timer job performs an additional check for PowerPivot usage data.</span></span> <span data-ttu-id="382c3-210">当检测到 PowerPivot 使用情况数据时，此计时器作业通过使用应用程序标识符找到正确的数据库，将数据移到服务应用程序数据库。</span><span class="sxs-lookup"><span data-stu-id="382c3-210">When PowerPivot usage data is detected, the timer job moves the data to a service application database using an application identifier to find the correct database.</span></span><br /><br /> <span data-ttu-id="382c3-211">您可以手动运行此计时器作业，以便强制对到期的数据执行检查，或者强制将 PowerPivot 使用情况数据导入到 PowerPivot 服务应用程序数据库中。</span><span class="sxs-lookup"><span data-stu-id="382c3-211">You can run this timer job manually to force a check on expired data, or to force a data import of PowerPivot usage data to a PowerPivot service application database.</span></span>|  
|<span data-ttu-id="382c3-212">PowerPivot 管理面板处理计时器作业</span><span class="sxs-lookup"><span data-stu-id="382c3-212">PowerPivot Management Dashboard Processing timer job</span></span>|<span data-ttu-id="382c3-213">每天凌晨 3:00。</span><span class="sxs-lookup"><span data-stu-id="382c3-213">Daily at 3:00 A.M.</span></span>|<span data-ttu-id="382c3-214">此计时器作业更新向 PowerPivot 管理面板提供管理数据的内部 PowerPivot 工作簿。</span><span class="sxs-lookup"><span data-stu-id="382c3-214">This timer job updates the internal PowerPivot workbook that provides administrative data to the PowerPivot Management Dashboard.</span></span> <span data-ttu-id="382c3-215">它获取由 SharePoint 管理的更新信息，包括显示在面板报表或 Web 部件中的服务器名称、用户名、应用程序名称和文件名。</span><span class="sxs-lookup"><span data-stu-id="382c3-215">It gets updated information that is managed by SharePoint, including server names, user names, application names, and file names that appear in dashboard reports or web parts.</span></span>|  
  
##  <a name="reporting-on-usage-data"></a><a name="reporting"></a> <span data-ttu-id="382c3-216">使用情况数据报告</span><span class="sxs-lookup"><span data-stu-id="382c3-216">Reporting on Usage Data</span></span>  
 <span data-ttu-id="382c3-217">若要查看针对 PowerPivot 数据的使用情况数据，您可以在 PowerPivot 管理面板上查看内置的报表。</span><span class="sxs-lookup"><span data-stu-id="382c3-217">To view usage data on PowerPivot data, you can view built-in reports in the PowerPivot Management Dashboard.</span></span> <span data-ttu-id="382c3-218">这些内置报告合并从服务应用程序数据库的报告数据结构中检索的使用情况数据。</span><span class="sxs-lookup"><span data-stu-id="382c3-218">The built-in reports consolidate usage data that is retrieved from reporting data structures in the service application database.</span></span> <span data-ttu-id="382c3-219">因为基础报告数据会每天更新，所以，仅在 Microsoft SharePoint Foundation 使用情况数据处理计时器作业将数据复制到 PowerPivot 服务器应用程序数据库后，内置使用情况报告才显示更新的信息。</span><span class="sxs-lookup"><span data-stu-id="382c3-219">Because the underlying report data is updated on a daily basis, the built-in usage reports will show updated information only after the Microsoft SharePoint Foundation Usage Data Processing timer job copies data to a PowerPivot service application database.</span></span> <span data-ttu-id="382c3-220">默认情况下，此操作一天执行一次。</span><span class="sxs-lookup"><span data-stu-id="382c3-220">By default, this occurs once a day.</span></span>  
  
 <span data-ttu-id="382c3-221">有关如何查看报表的详细信息，请参阅[PowerPivot 管理面板和使用情况数据](power-pivot-management-dashboard-and-usage-data.md)。</span><span class="sxs-lookup"><span data-stu-id="382c3-221">For more information about how to view reports, see [PowerPivot Management Dashboard and Usage Data](power-pivot-management-dashboard-and-usage-data.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="382c3-222">另请参阅</span><span class="sxs-lookup"><span data-stu-id="382c3-222">See Also</span></span>  
 <span data-ttu-id="382c3-223">[PowerPivot 管理面板和使用情况数据](power-pivot-management-dashboard-and-usage-data.md) </span><span class="sxs-lookup"><span data-stu-id="382c3-223">[PowerPivot Management Dashboard and Usage Data](power-pivot-management-dashboard-and-usage-data.md) </span></span>  
 <span data-ttu-id="382c3-224">[配置设置引用 &#40;PowerPivot for SharePoint&#41;](configuration-setting-reference-power-pivot-for-sharepoint.md) </span><span class="sxs-lookup"><span data-stu-id="382c3-224">[Configuration Setting Reference &#40;PowerPivot for SharePoint&#41;](configuration-setting-reference-power-pivot-for-sharepoint.md) </span></span>  
 [<span data-ttu-id="382c3-225">为 &#40;配置使用情况数据收集 PowerPivot for SharePoint</span><span class="sxs-lookup"><span data-stu-id="382c3-225">Configure Usage Data Collection for &#40;PowerPivot for SharePoint</span></span>](configure-usage-data-collection-for-power-pivot-for-sharepoint.md)  
  
  