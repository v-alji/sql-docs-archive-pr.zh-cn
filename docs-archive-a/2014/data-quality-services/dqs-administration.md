---
title: DQS 管理 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
helpviewer_keywords:
- dqs administration
- administration
- dqs,adminstration
ms.assetid: 9940ef5d-f6f6-4dec-9414-1077a4d7f12b
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 1803759f0ada269960c5abf1c3ee9f528fa53b86
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579049"
---
# <a name="dqs-administration"></a><span data-ttu-id="56f67-102">dqs 管理</span><span class="sxs-lookup"><span data-stu-id="56f67-102">DQS Administration</span></span>
  <span data-ttu-id="56f67-103">使用[!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS)，您可以管理在 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]上执行的各种 DQS 活动、配置与 DQS 活动有关的服务器级属性、配置 Reference Data Services 设置以及 DQS 日志设置。</span><span class="sxs-lookup"><span data-stu-id="56f67-103">[!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) allows you to administer and manage various DQS activities performed on [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)], configure server-level properties related to DQS activities, configure the Reference Data Service settings, and configure DQS log settings.</span></span> <span data-ttu-id="56f67-104">通过 **的** 管理 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]功能来执行这些操作。</span><span class="sxs-lookup"><span data-stu-id="56f67-104">These things are done through the **Administration** feature in [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].</span></span> <span data-ttu-id="56f67-105">根据您在 DQS 中的安全访问权限（角色），授权/拒绝您在此区域中执行某些功能。</span><span class="sxs-lookup"><span data-stu-id="56f67-105">Depending upon your security access (role) in DQS, you are granted/denied access to certain functionalities in this area.</span></span>  
  
 <span data-ttu-id="56f67-106">除了这些管理活动之外，本主题还提供有关备份和还原 DQS 数据库（此管理活动不是使用 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]执行的）的信息。</span><span class="sxs-lookup"><span data-stu-id="56f67-106">Apart from these administration activities, this topic also provides information about an administration activity, backing up and restoring DQS databases, which is not performed using [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].</span></span>  
  
 <span data-ttu-id="56f67-107">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 中的管理功能具有以下优点：</span><span class="sxs-lookup"><span data-stu-id="56f67-107">The administration feature in [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] has the following benefits:</span></span>  
  
-   <span data-ttu-id="56f67-108">使数据专员可以从 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 监视 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]上的各种 DQS 活动。</span><span class="sxs-lookup"><span data-stu-id="56f67-108">Enables data stewards to monitor various DQS activities on a [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] from a [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].</span></span>  
  
-   <span data-ttu-id="56f67-109">使 DQS 管理员可以从 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 监视 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]上的各种 DQS 活动、根据需要 *终止* 正在运行的活动或 *停止* 活动中某个正在运行的过程。</span><span class="sxs-lookup"><span data-stu-id="56f67-109">Enables DQS administrators to monitor the DQS activities on a [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] from a [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)], and *terminate* a running activity or *stop* a running process within an activity, if required.</span></span>  
  
-   <span data-ttu-id="56f67-110">配置引用数据服务设置，如设置与 Azure Marketplace 的连接以及管理直接第三方引用数据服务提供程序。</span><span class="sxs-lookup"><span data-stu-id="56f67-110">Configure reference data service settings such as setting up connectivity with Azure Marketplace and managing direct third-party reference data service providers.</span></span>  
  
-   <span data-ttu-id="56f67-111">配置清理和匹配活动的阈值。</span><span class="sxs-lookup"><span data-stu-id="56f67-111">Configure threshold values for the cleansing and matching activities.</span></span>  
  
-   <span data-ttu-id="56f67-112">在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]中启用/禁用通知。</span><span class="sxs-lookup"><span data-stu-id="56f67-112">Enable/disable notifications in [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].</span></span>  
  
-   <span data-ttu-id="56f67-113">基于事件的严重级别配置日志记录。</span><span class="sxs-lookup"><span data-stu-id="56f67-113">Configure logging based on the severity level of the events.</span></span>  
  
##  <a name="administration-activities-by-using-data-quality-client"></a><a name="AdminUsingClent"></a><span data-ttu-id="56f67-114">使用 Data Quality Client 管理活动</span><span class="sxs-lookup"><span data-stu-id="56f67-114">Administration Activities by Using Data Quality Client</span></span>  
 <span data-ttu-id="56f67-115">使用 **中的** “管理” [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]功能执行这些活动。</span><span class="sxs-lookup"><span data-stu-id="56f67-115">These activities are performed by using the **Administration** feature in [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].</span></span>  
  
### <a name="activity-monitoring"></a><span data-ttu-id="56f67-116">活动监视</span><span class="sxs-lookup"><span data-stu-id="56f67-116">Activity Monitoring</span></span>  
 <span data-ttu-id="56f67-117">**中的** “活动监视” [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 屏幕显示有关在 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]上执行的每个活动的详细信息。</span><span class="sxs-lookup"><span data-stu-id="56f67-117">The **Activity Monitoring** screen in [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] displays detailed information about each activity performed on a [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)].</span></span> <span data-ttu-id="56f67-118">此屏幕将主要供数据专员使用，用于对 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 应用程序所连接的 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 上执行的所有活动执行高级监视。</span><span class="sxs-lookup"><span data-stu-id="56f67-118">This screen will be primarily used by the data steward to perform a high-level monitoring of all the activities performed on the [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] that the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] application is connected to.</span></span> <span data-ttu-id="56f67-119">此屏幕不提供任何系统级别的监视。</span><span class="sxs-lookup"><span data-stu-id="56f67-119">This screen does not provide any system-level monitoring.</span></span> <span data-ttu-id="56f67-120">此外，DQS 管理员还可以使用此屏幕在需要时终止正在运行的活动或停止活动中正在运行的过程，从而控制活动或活动中的过程。</span><span class="sxs-lookup"><span data-stu-id="56f67-120">Additionally, this screen also enables the DQS administrators to control an activity or a process within an activity by terminating a running activity or stopping a running process within an activity, if required.</span></span> <span data-ttu-id="56f67-121">为知识发现、域管理、匹配策略、清理、匹配和基于 SQL Server Integration Services (SSIS) 的清理显示此数据。</span><span class="sxs-lookup"><span data-stu-id="56f67-121">The data is displayed for knowledge discovery, domain management, matching policy, cleansing, matching, and SQL Server Integration Services (SSIS)-based cleansing.</span></span>  
  
### <a name="configuration"></a><span data-ttu-id="56f67-122">配置</span><span class="sxs-lookup"><span data-stu-id="56f67-122">Configuration</span></span>  
 <span data-ttu-id="56f67-123">DQS 管理员使用 **中的** “配置” [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 屏幕执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="56f67-123">The **Configuration** screen in [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] enables the DQS administrator to do the following things:</span></span>  
  
-   <span data-ttu-id="56f67-124">**引用数据**：配置引用数据服务提供程序： Azure Marketplace 或直接引用数据服务提供程序。</span><span class="sxs-lookup"><span data-stu-id="56f67-124">**Reference Data**: Configure reference data service providers: Azure Marketplace or direct reference data service providers.</span></span> <span data-ttu-id="56f67-125">在设置引用数据服务提供程序后，可以在域管理活动期间在知识库中使用引用数据映射域/复合域，然后将同一知识库用于数据质量项目中的清理活动。</span><span class="sxs-lookup"><span data-stu-id="56f67-125">After you set up the reference data service providers, you can map a domain/composite domain with the reference data during domain management activity in a knowledge base, and then use the same knowledge base for the cleansing activity in a data quality project.</span></span> <span data-ttu-id="56f67-126">它还使你能够指定用于连接到 Internet 的代理设置以使用 Azure Marketplace。</span><span class="sxs-lookup"><span data-stu-id="56f67-126">It also enables you to specify the proxy settings for connecting to the Internet to use Azure Marketplace.</span></span>  
  
-   <span data-ttu-id="56f67-127">**常规设置**：指定数据清理和数据匹配的阈值，以及在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]中是否启用事件探查的通知。</span><span class="sxs-lookup"><span data-stu-id="56f67-127">**General Settings**: Specify the threshold values for data cleansing and data matching, and whether to enable notifications for profiling in [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].</span></span> <span data-ttu-id="56f67-128">DQS 在执行数据质量项目中的计算机辅助的清理和匹配活动期间使用这些阈值。</span><span class="sxs-lookup"><span data-stu-id="56f67-128">These threshold values are used by DQS during the computer-assisted cleansing and matching activities in a data quality project.</span></span>  
  
-   <span data-ttu-id="56f67-129">**日志设置**：DQS 中的日志文件记录在 DQS 中执行的活动，在维护和故障排除期间对于跟踪操作问题很有用。</span><span class="sxs-lookup"><span data-stu-id="56f67-129">**Log Settings**: The log files in DQS record the activities performed in DQS, and are useful for tracking operational issues during maintenance and troubleshooting.</span></span> <span data-ttu-id="56f67-130">您可以基于事件的严重级别筛选要为各种 DQS 功能（域管理、知识发现、清理、匹配和 Reference Data Services）记录的消息和 DQS 模块。</span><span class="sxs-lookup"><span data-stu-id="56f67-130">You can filter the messages that you want to be logged for various DQS features (domain management, knowledge discovery, cleansing, matching, and reference data services) and DQS modules based on the severity level of the events.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="56f67-131">**“配置”** 屏幕仅适用于对 DQS_MAIN 数据库具有 dqs_administrator 角色的那些用户。</span><span class="sxs-lookup"><span data-stu-id="56f67-131">The **Configuration** screen is available only for those users who have the dqs_administrator role on the DQS_MAIN database.</span></span>  
  
##  <a name="administration-activities-outside-of-data-quality-client"></a><a name="AdminOutsideClient"></a><span data-ttu-id="56f67-132">Data Quality Client 以外的管理活动</span><span class="sxs-lookup"><span data-stu-id="56f67-132">Administration Activities Outside of Data Quality Client</span></span>  
 <span data-ttu-id="56f67-133">下面这些活动在数据质量客户端的外部执行：</span><span class="sxs-lookup"><span data-stu-id="56f67-133">There activities are performed outside of Data Quality Client:</span></span>  
  
-   <span data-ttu-id="56f67-134">**备份和还原 DQS 数据库**：备份和还原 DQS 数据库与备份和还原任何 SQL Server 数据库一样，但是针对 DQS 有一些注意事项。</span><span class="sxs-lookup"><span data-stu-id="56f67-134">**Backup and Restore DQS Databases**: The backup and restore of DQS databases is same as backing up and restoring any SQL Server database with some considerations that are specific to DQS.</span></span>  
  
-   <span data-ttu-id="56f67-135">**分离和附加 DQS 数据库**：分离和附加 DQS 数据库与分离和附加任何 SQL Server 数据库一样，但是针对 DQS 有一些注意事项。</span><span class="sxs-lookup"><span data-stu-id="56f67-135">**Detach and Attach DQS Databases**: The steps to detach and attach DQS databases is same as detaching and attaching any SQL Server database with some considerations that are specific to DQS.</span></span>  
  
 <span data-ttu-id="56f67-136">有关详细信息，请参阅 [Manage DQS Databases](../../2014/data-quality-services/manage-dqs-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="56f67-136">For more information, see [Manage DQS Databases](../../2014/data-quality-services/manage-dqs-databases.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="56f67-137">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="56f67-137">Related Tasks</span></span>  
  
|<span data-ttu-id="56f67-138">任务说明</span><span class="sxs-lookup"><span data-stu-id="56f67-138">Task Description</span></span>|<span data-ttu-id="56f67-139">主题</span><span class="sxs-lookup"><span data-stu-id="56f67-139">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="56f67-140">说明如何在 DQS 中监视活动。</span><span class="sxs-lookup"><span data-stu-id="56f67-140">Describes how to monitor activities in DQS.</span></span>|[<span data-ttu-id="56f67-141">监视 DQS 活动</span><span class="sxs-lookup"><span data-stu-id="56f67-141">Monitor DQS Activities</span></span>](../../2014/data-quality-services/monitor-dqs-activities.md)|  
|<span data-ttu-id="56f67-142">说明如何在 DQS 中配置引用数据设置。</span><span class="sxs-lookup"><span data-stu-id="56f67-142">Describes how to configure reference data settings in DQS.</span></span>|[<span data-ttu-id="56f67-143">将 DQS 配置为使用引用数据</span><span class="sxs-lookup"><span data-stu-id="56f67-143">Configure DQS to Use Reference Data</span></span>](../../2014/data-quality-services/configure-dqs-to-use-reference-data.md)|  
|<span data-ttu-id="56f67-144">说明如何配置清理和匹配活动的阈值。</span><span class="sxs-lookup"><span data-stu-id="56f67-144">Describes how to configure threshold values for the cleansing and matching activities.</span></span>|[<span data-ttu-id="56f67-145">配置清理和匹配活动的阈值</span><span class="sxs-lookup"><span data-stu-id="56f67-145">Configure Threshold Values for Cleansing and Matching</span></span>](../../2014/data-quality-services/configure-threshold-values-for-cleansing-and-matching.md)|  
|<span data-ttu-id="56f67-146">说明如何在 DQS 中启用或禁用通知。</span><span class="sxs-lookup"><span data-stu-id="56f67-146">Describes how to enable or disable notifications in DQS.</span></span>|[<span data-ttu-id="56f67-147">在 DQS 中启用或禁用事件探查通知</span><span class="sxs-lookup"><span data-stu-id="56f67-147">Enable or Disable Profiling Notifications in DQS</span></span>](../../2014/data-quality-services/enable-or-disable-profiling-notifications-in-dqs.md)|  
|<span data-ttu-id="56f67-148">说明如何基于事件的严重级别配置 DQS 日志记录。</span><span class="sxs-lookup"><span data-stu-id="56f67-148">Describes how to configure DQS logging based on the severity level of the events.</span></span>|[<span data-ttu-id="56f67-149">为 DQS 日志文件配置严重级别</span><span class="sxs-lookup"><span data-stu-id="56f67-149">Configure Severity Levels for DQS Log Files</span></span>](../../2014/data-quality-services/configure-severity-levels-for-dqs-log-files.md)|  
|<span data-ttu-id="56f67-150">说明如何配置 DQS 日志记录的高级设置。</span><span class="sxs-lookup"><span data-stu-id="56f67-150">Describes how to configure advanced settings for DQS logging.</span></span>|[<span data-ttu-id="56f67-151">为 DQS 日志文件配置高级设置</span><span class="sxs-lookup"><span data-stu-id="56f67-151">Configure Advanced Settings for DQS Log Files</span></span>](../../2014/data-quality-services/configure-advanced-settings-for-dqs-log-files.md)|  
|<span data-ttu-id="56f67-152">说明如何备份和还原 DQS 数据库。</span><span class="sxs-lookup"><span data-stu-id="56f67-152">Describes how to back up and restore DQS databases.</span></span>|[<span data-ttu-id="56f67-153">备份和还原 DQS 数据库</span><span class="sxs-lookup"><span data-stu-id="56f67-153">Backing Up and Restoring DQS Databases</span></span>](../../2014/data-quality-services/backing-up-and-restoring-dqs-databases.md)|  
|<span data-ttu-id="56f67-154">介绍如何分离和附加 DQS 数据库。</span><span class="sxs-lookup"><span data-stu-id="56f67-154">Describes how to detach and attach DQS databases.</span></span>|[<span data-ttu-id="56f67-155">分离数据库和附加 DQS 数据库</span><span class="sxs-lookup"><span data-stu-id="56f67-155">Detaching and Attaching DQS Databases</span></span>](../../2014/data-quality-services/detaching-and-attaching-dqs-databases.md)|  
  
## <a name="see-also"></a><span data-ttu-id="56f67-156">另请参阅</span><span class="sxs-lookup"><span data-stu-id="56f67-156">See Also</span></span>  
 <span data-ttu-id="56f67-157">[DQS 中的引用数据服务](../../2014/data-quality-services/reference-data-services-in-dqs.md) </span><span class="sxs-lookup"><span data-stu-id="56f67-157">[Reference Data Services in DQS](../../2014/data-quality-services/reference-data-services-in-dqs.md) </span></span>  
 <span data-ttu-id="56f67-158">[管理 DQS 日志文件](../../2014/data-quality-services/manage-dqs-log-files.md) </span><span class="sxs-lookup"><span data-stu-id="56f67-158">[Manage DQS Log Files](../../2014/data-quality-services/manage-dqs-log-files.md) </span></span>  
 [<span data-ttu-id="56f67-159">管理 DQS 数据库</span><span class="sxs-lookup"><span data-stu-id="56f67-159">Manage DQS Databases</span></span>](../../2014/data-quality-services/manage-dqs-databases.md)  
  
  
