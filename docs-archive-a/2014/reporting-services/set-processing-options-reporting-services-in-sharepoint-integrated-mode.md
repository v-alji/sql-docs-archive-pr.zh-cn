---
title: 在 SharePoint 集成模式下 (Reporting Services 设置处理选项) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- SharePoint integration [Reporting Services], content management
- snapshots [Reporting Services], creating
ms.assetid: 453b19a1-739a-4b67-aeea-2069b52204e1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8c33b205a702d4ab77abf74154232990da9840b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689767"
---
# <a name="set-processing-options-reporting-services-in-sharepoint-integrated-mode"></a><span data-ttu-id="fdedd-102">设置处理选项（SharePoint 集成模式下的 Reporting Services）</span><span class="sxs-lookup"><span data-stu-id="fdedd-102">Set Processing Options (Reporting Services in SharePoint Integrated Mode)</span></span>
  <span data-ttu-id="fdedd-103">可以对 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 报表设置处理选项，以决定何时进行数据处理。</span><span class="sxs-lookup"><span data-stu-id="fdedd-103">You can set processing options on a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] report to determine when data processing occurs.</span></span> <span data-ttu-id="fdedd-104">还可以为报表处理设置超时值和用于决定是否为当前报表启用报表历史记录的选项。</span><span class="sxs-lookup"><span data-stu-id="fdedd-104">You can also set a time-out value for report processing, and options that determine whether report history is enabled for the current report.</span></span>  
  
-   <span data-ttu-id="fdedd-105">您可以按报表快照形式运行报表，以防止报表在任意时间运行（例如，在执行计划备份期间）。</span><span class="sxs-lookup"><span data-stu-id="fdedd-105">You can run a report as a report snapshot to prevent the report from being run at arbitrary times (for example, during a scheduled backup).</span></span> <span data-ttu-id="fdedd-106">报表快照通常按计划创建并在随后进行刷新，因此您可以精确地设定进行报表和数据处理的时间。</span><span class="sxs-lookup"><span data-stu-id="fdedd-106">A report snapshot is usually created and subsequently refreshed on a schedule, allowing you to time exactly when report and data processing will occur.</span></span> <span data-ttu-id="fdedd-107">如果报表所基于的查询需要很长的运行时间，或查询使用的数据来自您需要在特定时间无人访问的数据源，则应以快照形式运行报表。</span><span class="sxs-lookup"><span data-stu-id="fdedd-107">If a report is based on queries that take a long time to run, or on queries that use data from a data source that you prefer no one access during certain hours, you should run the report as a snapshot.</span></span>  
  
-   <span data-ttu-id="fdedd-108">报表服务器可以缓存已处理报表的副本，并在用户打开此报表时返回该副本。</span><span class="sxs-lookup"><span data-stu-id="fdedd-108">A report server can cache a copy of a processed report and return that copy when a user opens the report.</span></span> <span data-ttu-id="fdedd-109">缓存是一种性能增强技术。</span><span class="sxs-lookup"><span data-stu-id="fdedd-109">Caching is a performance-enhancement technique.</span></span> <span data-ttu-id="fdedd-110">在报表很大或需要频繁访问的情况下，缓存报表可以缩短检索该报表所需的时间。</span><span class="sxs-lookup"><span data-stu-id="fdedd-110">Caching can shorten the time required to retrieve a report if the report is large or accessed frequently.</span></span>  
  
-   <span data-ttu-id="fdedd-111">报表历史记录是以前运行的报表副本的集合。</span><span class="sxs-lookup"><span data-stu-id="fdedd-111">Report history is a collection of previously run copies of a report.</span></span> <span data-ttu-id="fdedd-112">您可以使用报表历史记录来维护一段时间以来的报表记录。</span><span class="sxs-lookup"><span data-stu-id="fdedd-112">You can use report history to maintain a record of a report over time.</span></span> <span data-ttu-id="fdedd-113">报表历史记录不适用于包含机密数据或个人数据的报表。</span><span class="sxs-lookup"><span data-stu-id="fdedd-113">Report history is not intended for reports that contain confidential or personal data.</span></span> <span data-ttu-id="fdedd-114">因此，报表历史记录只能包含使用单组特定凭据查询数据源的报表。此类凭据可以是已存储的凭据，也可以是在无人参与的情况下执行报表所用的凭据，并且对运行报表的所有用户都可用。</span><span class="sxs-lookup"><span data-stu-id="fdedd-114">For this reason, report history can include only those reports that query a data source using a single set of credentials (either stored credentials or credentials used for unattended report execution) that are available to all users who run a report.</span></span>  
  
    > [!NOTE]  
    >  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="fdedd-115">与 SharePoint 的集成使用 SharePoint 的签出和签入内容管理功能将更新保存到 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 内容类型。</span><span class="sxs-lookup"><span data-stu-id="fdedd-115">integration with SharePoint uses the check out and check in content management features of SharePoint to save updates to [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] content types.</span></span> <span data-ttu-id="fdedd-116">这包括创建报表快照。</span><span class="sxs-lookup"><span data-stu-id="fdedd-116">This includes the creation of report snapshots.</span></span> <span data-ttu-id="fdedd-117">因此，如果您在文档库上启用了版本控制，则当创建新的报表历史记录快照时，您将看到更新后的报表版本。</span><span class="sxs-lookup"><span data-stu-id="fdedd-117">Therefore if you have enabled versioning on a document library, you will see the report version updated when a new report history snapshot is created.</span></span> <span data-ttu-id="fdedd-118">这是更新快照的副作用。</span><span class="sxs-lookup"><span data-stu-id="fdedd-118">This is a side-effect of updating snapshots.</span></span> <span data-ttu-id="fdedd-119">当更新快照时，它导致报表的 LastExecution 属性发生变化，而这会导致报表的版本发生变化。</span><span class="sxs-lookup"><span data-stu-id="fdedd-119">When a snapshot is updated it causes the LastExecution property of the report to change and that will cause a change in the version of the report.</span></span>  
  
-   <span data-ttu-id="fdedd-120">可以通过指定超时值来限制使用系统资源的方式。</span><span class="sxs-lookup"><span data-stu-id="fdedd-120">You can specify time-out values to set limits on how system resources are used.</span></span>  
  
||  
|-|  
|<span data-ttu-id="fdedd-121">**[!INCLUDE[applies](../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]SharePoint 模式</span><span class="sxs-lookup"><span data-stu-id="fdedd-121">**[!INCLUDE[applies](../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint mode</span></span>|  
  
 <span data-ttu-id="fdedd-122">**本主题内容：**</span><span class="sxs-lookup"><span data-stu-id="fdedd-122">**In this topic:**</span></span>  
  
-   [<span data-ttu-id="fdedd-123">设置数据刷新选项</span><span class="sxs-lookup"><span data-stu-id="fdedd-123">To set data refresh options</span></span>](#bkmk_set_data_refresh)  
  
-   [<span data-ttu-id="fdedd-124">设置报表缓存选项</span><span class="sxs-lookup"><span data-stu-id="fdedd-124">To set report caching options</span></span>](#bkmk_set_report_caching)  
  
-   [<span data-ttu-id="fdedd-125">设置处理超时值</span><span class="sxs-lookup"><span data-stu-id="fdedd-125">To set processing time-out values</span></span>](#bkmk_set_processing)  
  
-   [<span data-ttu-id="fdedd-126">设置报表历史记录选项和限制值</span><span class="sxs-lookup"><span data-stu-id="fdedd-126">To set report history options and limits</span></span>](#bkmk_set_report_history)  
  
-   [<span data-ttu-id="fdedd-127">设置数据库超时</span><span class="sxs-lookup"><span data-stu-id="fdedd-127">Set database timeout</span></span>](#bkmk_set_database_timeout)  
  
##  <a name="to-set-data-refresh-options"></a><a name="bkmk_set_data_refresh"></a><span data-ttu-id="fdedd-128">设置数据刷新选项</span><span class="sxs-lookup"><span data-stu-id="fdedd-128">To set data refresh options</span></span>  
  
1.  <span data-ttu-id="fdedd-129">指向库中的报表。</span><span class="sxs-lookup"><span data-stu-id="fdedd-129">Point to a report in the library.</span></span>  
  
2.  <span data-ttu-id="fdedd-130">单击向下箭头，然后选择 **“管理处理选项”**。</span><span class="sxs-lookup"><span data-stu-id="fdedd-130">Click the down arrow, and select **Manage processing options**.</span></span>  
  
3.  <span data-ttu-id="fdedd-131">在 **“数据刷新选项”** 中，单击 **“使用快照数据”**。</span><span class="sxs-lookup"><span data-stu-id="fdedd-131">In **Data Refresh Options**, click **Use snapshot data**.</span></span> <span data-ttu-id="fdedd-132">如果看到“此报表无法通过快照运行，因为一个或多个数据源凭据未存储”这一信息，则表明报表未配置为以无人参与的方式运行，在设置此选项之前，必须将数据源修改为使用已存储凭据。</span><span class="sxs-lookup"><span data-stu-id="fdedd-132">If you see "This report can not run from a snapshot because one or more of the data sources credentials are not stored", the report is not configured to run unattended and you must modify the data sources to use stored credentials before setting this option.</span></span>  
  
4.  <span data-ttu-id="fdedd-133">在 **“数据快照选项”** 中，选择 **“计划数据处理”**。</span><span class="sxs-lookup"><span data-stu-id="fdedd-133">In **Data Snapshot Options**, select **Schedule data processing**.</span></span>  
  
5.  <span data-ttu-id="fdedd-134">如果有要使用的现有共享计划，请选择 **“根据共享计划”** ，否则请单击 **“根据自定义计划”**，然后单击 **“配置”**。</span><span class="sxs-lookup"><span data-stu-id="fdedd-134">Select **On a shared schedule** if you have an existing shared schedule that you want to use, otherwise click **On a custom schedule**, and then click **Configure**.</span></span>  
  
6.  <span data-ttu-id="fdedd-135">选择频率、计划以及开始和结束日期，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="fdedd-135">Select frequency, schedule, and start and end dates, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="fdedd-136">如果想要立刻创建用于报表的快照数据而不等待预定的数据处理开始执行，则应在 **“数据快照选项”** 中选择 **“保存此页时创建或更新快照”** 。</span><span class="sxs-lookup"><span data-stu-id="fdedd-136">In **Data Snapshot Options**, select **Create or update the snapshot when this page is saved** if you want to immediately create snapshot data to use with the report, without waiting for the scheduled data processing to occur.</span></span>  
  
##  <a name="to-set-report-caching-options"></a><a name="bkmk_set_report_caching"></a><span data-ttu-id="fdedd-137">设置报表缓存选项</span><span class="sxs-lookup"><span data-stu-id="fdedd-137">To set report caching options</span></span>  
  
1.  <span data-ttu-id="fdedd-138">指向库中的报表。</span><span class="sxs-lookup"><span data-stu-id="fdedd-138">Point to a report in the library.</span></span>  
  
2.  <span data-ttu-id="fdedd-139">单击向下箭头，然后选择 **“管理处理选项”**。</span><span class="sxs-lookup"><span data-stu-id="fdedd-139">Click the down arrow, and select **Manage processing options**.</span></span>  
  
3.  <span data-ttu-id="fdedd-140">在 **“数据刷新选项”** 中，单击 **“使用缓存数据”**。</span><span class="sxs-lookup"><span data-stu-id="fdedd-140">In **Data Refresh Options**, click **Use cached data**.</span></span> <span data-ttu-id="fdedd-141">如果看到“此报表无法缓存，因为未存储一个或多个数据源凭据”这一信息，则表明报表未配置为以无人参与的方式运行，在设置此选项之前，必须将数据源修改为使用已存储凭据。</span><span class="sxs-lookup"><span data-stu-id="fdedd-141">If you see "This report can not be cached because one or more of the data sources credentials are not stored", the report is not configured to run unattended and you must modify the data sources to use stored credentials before setting this option.</span></span>  
  
4.  <span data-ttu-id="fdedd-142">在 **“缓存选项”** 中，指定缓存的过期方式：</span><span class="sxs-lookup"><span data-stu-id="fdedd-142">In **Cache Options**, specify how the cache will expire:</span></span>  
  
    -   <span data-ttu-id="fdedd-143">输入缓存将在其后过期的分钟数。</span><span class="sxs-lookup"><span data-stu-id="fdedd-143">Enter a number of minutes after which the cache will expire.</span></span>  
  
    -   <span data-ttu-id="fdedd-144">使用共享计划，在计划中指定的时间清除缓存。</span><span class="sxs-lookup"><span data-stu-id="fdedd-144">Use a shared schedule to clear the cache at times specified in the schedule.</span></span>  
  
    -   <span data-ttu-id="fdedd-145">创建自定义计划，在指定的时间清除缓存。</span><span class="sxs-lookup"><span data-stu-id="fdedd-145">Create a custom schedule to clear the cache at a time that you specify.</span></span>  
  
##  <a name="to-set-processing-time-out-values"></a><a name="bkmk_set_processing"></a><span data-ttu-id="fdedd-146">设置处理超时值</span><span class="sxs-lookup"><span data-stu-id="fdedd-146">To set processing time-out values</span></span>  
  
1.  <span data-ttu-id="fdedd-147">指向库中的报表。</span><span class="sxs-lookup"><span data-stu-id="fdedd-147">Point to a report in the library.</span></span>  
  
2.  <span data-ttu-id="fdedd-148">单击向下箭头，然后选择 **“管理处理选项”** 。</span><span class="sxs-lookup"><span data-stu-id="fdedd-148">Click the down arrow, and select **Manage processing options**.</span></span>  
  
3.  <span data-ttu-id="fdedd-149">如果要使用在报表服务器级指定的值，请在“处理超时”中选择“使用站点默认设置”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fdedd-149">In **Processing Time-out**, select **Use site default setting** if you want to use the value specified at the report server level.</span></span> <span data-ttu-id="fdedd-150">如果要用无超时或不同的超时值来替代该值，请选择“不对报表处理时间设置超时”或“限制报表处理时间(秒)”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fdedd-150">Otherwise, select **Do not time out report processing** or **Limit report processing in seconds** if you want to override that value with no time-out or different time-out values.</span></span>  
  
##  <a name="to-set-report-history-options-and-limits"></a><a name="bkmk_set_report_history"></a><span data-ttu-id="fdedd-151">设置报表历史记录选项和限制</span><span class="sxs-lookup"><span data-stu-id="fdedd-151">To set report history options and limits</span></span>  
  
1.  <span data-ttu-id="fdedd-152">指向库中的报表。</span><span class="sxs-lookup"><span data-stu-id="fdedd-152">Point to a report in the library.</span></span>  
  
2.  <span data-ttu-id="fdedd-153">单击向下箭头，然后选择 **“管理处理选项”**。</span><span class="sxs-lookup"><span data-stu-id="fdedd-153">Click the down arrow, and select **Manage processing options**.</span></span>  
  
3.  <span data-ttu-id="fdedd-154">在 **“历史记录快照选项”** 中，指定数据处理的方式和时间，以及对数据处理进行保存的方式和时间。</span><span class="sxs-lookup"><span data-stu-id="fdedd-154">In **History Snapshot Options**, specify how and when data processing occurs and is saved.</span></span>  
  
4.  <span data-ttu-id="fdedd-155">在 **“历史记录快照限制”** 中，如果要使用在报表服务器级指定的值，请选择 **“使用站点默认设置”** 。</span><span class="sxs-lookup"><span data-stu-id="fdedd-155">In **History Snapshot Limits**, select **Use site default setting** if you want to use the value specified at the report server level.</span></span> <span data-ttu-id="fdedd-156">否则，请选择 **“不限制快照数”** 或 **“将快照数限制在”** 以指定自定义值。</span><span class="sxs-lookup"><span data-stu-id="fdedd-156">Otherwise, select **Do not limit the number of snapshots** or **Limit number of snapshots** to specify a custom value.</span></span>  
  
##  <a name="set-database-timeout"></a><a name="bkmk_set_database_timeout"></a><span data-ttu-id="fdedd-157">设置数据库超时</span><span class="sxs-lookup"><span data-stu-id="fdedd-157">Set database timeout</span></span>  
  
1.  <span data-ttu-id="fdedd-158">使用 Windows PowerShell 设置 SharePoint 报表服务器的数据库超时。</span><span class="sxs-lookup"><span data-stu-id="fdedd-158">Use Windows PowerShell to set the database timeout of a SharePoint report server.</span></span> <span data-ttu-id="fdedd-159">有关详细信息，请参阅[Reporting Services SharePoint 模式的 PowerShell cmdlet](../../2014/reporting-services/powershell-cmdlets-for-reporting-services-sharepoint-mode.md)的 "获取并设置报表服务应用程序数据库的属性" 部分。</span><span class="sxs-lookup"><span data-stu-id="fdedd-159">For more information, see the "Get and set Properties of the Reporting Service Application Database" section of [PowerShell cmdlets for Reporting Services SharePoint Mode](../../2014/reporting-services/powershell-cmdlets-for-reporting-services-sharepoint-mode.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdedd-160">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fdedd-160">See Also</span></span>  
 <span data-ttu-id="fdedd-161">[设置报表处理属性](report-server/set-report-processing-properties.md) </span><span class="sxs-lookup"><span data-stu-id="fdedd-161">[Set Report Processing Properties](report-server/set-report-processing-properties.md) </span></span>  
 <span data-ttu-id="fdedd-162">[缓存报表 (SSRS)](report-server/caching-reports-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="fdedd-162">[Caching Reports &#40;SSRS&#41;](report-server/caching-reports-ssrs.md) </span></span>  
 [<span data-ttu-id="fdedd-163">为报表和共享数据集处理设置超时值 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="fdedd-163">Setting Time-out Values for Report and Shared Dataset Processing &#40;SSRS&#41;</span></span>](report-server/setting-time-out-values-for-report-and-shared-dataset-processing-ssrs.md)  
  
  
