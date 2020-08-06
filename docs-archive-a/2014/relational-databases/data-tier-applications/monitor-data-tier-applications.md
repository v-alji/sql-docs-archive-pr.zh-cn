---
title: 监视数据层应用程序 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- monitoring [SQL Server], data-tier applications
- monitoring server performance [SQL Server], DACs
- data-tier application [SQL Server], monitor
ms.assetid: d2765828-2385-4019-aef2-1de3ab7d1b26
author: stevestein
ms.author: sstein
ms.openlocfilehash: 100ad85847c131b71ea6eff93346f283f70aaec0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591383"
---
# <a name="monitor-data-tier-applications"></a><span data-ttu-id="70211-102">监视数据层应用程序</span><span class="sxs-lookup"><span data-stu-id="70211-102">Monitor Data-tier Applications</span></span>
  <span data-ttu-id="70211-103">可以从 **(SSMS) 中的** 实用工具资源管理器 **和** 对象资源管理器 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 以及系统视图和表中监视数据层应用程序 (DAC)。</span><span class="sxs-lookup"><span data-stu-id="70211-103">A data-tier application (DAC) can be monitored from the **Utility Explorer** and **Object Explorer** in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] (SSMS), along with system views and tables.</span></span> <span data-ttu-id="70211-104">此外，可以使用标准数据库和 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 监视技术监视 DAC 中包含的数据库中的所有对象。</span><span class="sxs-lookup"><span data-stu-id="70211-104">In addition, all objects in the database contained in the DAC can be monitored using standard database and [!INCLUDE[ssDE](../../includes/ssde-md.md)] monitoring techniques.</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="70211-105">开始之前</span><span class="sxs-lookup"><span data-stu-id="70211-105">Before You Begin</span></span>  
 <span data-ttu-id="70211-106">如果您将 DAC 部署到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的托管实例，在下次将实用工具收集组从该实例发送到实用工具控制点时，与部署的 DAC 有关的信息将合并到 SQL Server 实用工具中。</span><span class="sxs-lookup"><span data-stu-id="70211-106">If you deploy a DAC to a managed instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], information about the deployed DAC is incorporated into the SQL Server Utility the next time the utility collection set is sent from the instance to the utility control point.</span></span> <span data-ttu-id="70211-107">然后，通过使用 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 实用工具资源管理器，可以查看与该 DAC 有关的基本运行状况信息。</span><span class="sxs-lookup"><span data-stu-id="70211-107">You can then view basic health information about the DAC by using the [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] **Utility Explorer**.</span></span>  
  
 <span data-ttu-id="70211-108">SSMS **“对象资源管理器”** 显示与部署到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]实例的每个 DAC 有关的基本配置信息，而与该实例是否在 SQL Server 实用工具中进行管理无关。</span><span class="sxs-lookup"><span data-stu-id="70211-108">The SSMS **Object Explorer** displays basic configuration information about each DAC deployed to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], regardless of whether the instance is managed in the SQL Server Utility.</span></span> <span data-ttu-id="70211-109">此外，可以使用与用于监视任何数据库的相同过程来监视与部署的 DAC 相关联的数据库。</span><span class="sxs-lookup"><span data-stu-id="70211-109">Also, the database associated with a deployed DAC can be monitored using the same procedures for monitoring any database.</span></span>  
  
## <a name="using-the-sql-server-utility"></a><span data-ttu-id="70211-110">使用 SQL Server 实用工具</span><span class="sxs-lookup"><span data-stu-id="70211-110">Using the SQL Server Utility</span></span>  
 <span data-ttu-id="70211-111">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] **实用工具资源管理器**中的“已部署的数据层应用程序”\*\*\*\* 详细信息页显示一个面板，该面板报告已部署到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的托管实例的所有 DAC 的资源利用情况。</span><span class="sxs-lookup"><span data-stu-id="70211-111">The **Deployed Data-tier Applications** detail page in the [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] **Utility Explorer** displays a dashboard that reports the resource utilization of all DACs that have been deployed to managed instances of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="70211-112">该详细信息页的顶部窗格列出每个已部署的 DAC，同时还列出直观的指示器，显示 CPU 和文件资源的使用率是否超出为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实用工具定义的策略。</span><span class="sxs-lookup"><span data-stu-id="70211-112">The top pane of the details page lists each deployed DAC with visual indicators showing whether their utilization of CPU and file resources are outside the policies defined for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility.</span></span> <span data-ttu-id="70211-113">如果您在列表视图中选择任何 DAC，则进一步的详细信息将显示在该页面的底部窗格的选项卡中。</span><span class="sxs-lookup"><span data-stu-id="70211-113">If you select any DAC in the list view, further details are displayed in tabs in the bottom pane of the page.</span></span> <span data-ttu-id="70211-114">有关详细信息页上提供的信息的详细信息，请参阅[已部署的数据层应用程序详细信息（SQL Server 实用工具）](../../database-engine/deployed-data-tier-application-details-sql-server-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="70211-114">For more information about the information presented on the details page, see [Deployed Data-tier Application Details &#40;SQL Server Utility&#41;](../../database-engine/deployed-data-tier-application-details-sql-server-utility.md).</span></span>  
  
 <span data-ttu-id="70211-115">在使用“已部署的数据层应用程序”详细信息页迅速确定导致硬件资源利用不足或压力过大的 DAC 后，你可以制订计划以便解决任何问题。</span><span class="sxs-lookup"><span data-stu-id="70211-115">After using the **Deployed Data-tier Applications** detail page to quickly identify any DACs that are either under-utilizing or stressing their hardware resource, you can make plans to address any problems.</span></span> <span data-ttu-id="70211-116">未充分利用其当前硬件资源的多个 DAC 可被合并为单个服务器，从而释放某些服务器以用于其他用途。</span><span class="sxs-lookup"><span data-stu-id="70211-116">Multiple DACs that are not fully utilizing their current hardware resources could be consolidated to a single server, freeing some of the servers for other uses.</span></span> <span data-ttu-id="70211-117">如果某一 DAC 对其当前服务器上的资源压力过大，则可以将该 DAC 移到性能更高的服务器上，或者向当前服务器添加更多的资源。</span><span class="sxs-lookup"><span data-stu-id="70211-117">If a DAC is stressing the resources on its current server, the DAC can be moved to a larger server, or additional resources can be added to the current server.</span></span>  
  
 <span data-ttu-id="70211-118">针对资源利用率的最低和最高限制由在 **“实用工具管理”** 详细信息页中定义的应用程序监视策略定义。</span><span class="sxs-lookup"><span data-stu-id="70211-118">The minimum and maximum limits for resource usage are defined by application monitoring policies defined in the **Utility Administration** details page.</span></span> <span data-ttu-id="70211-119">数据库管理员可以对策略进行定制，以便匹配其组织建立的限制。</span><span class="sxs-lookup"><span data-stu-id="70211-119">Database administrators can tailor the policies to match the limits established by their organizations.</span></span> <span data-ttu-id="70211-120">例如，一个公司可以将 75% 设置为针对某一 DAC 的最高 CPU 利用率，而另一个公司可以将该最高值设置为 80%。</span><span class="sxs-lookup"><span data-stu-id="70211-120">For example, one company might set 75% as the maximum CPU utilization for a DAC, while another company might set the maximum at 80%.</span></span> <span data-ttu-id="70211-121">有关设置应用程序监视策略的详细信息，请参阅[实用工具管理（SQL Server 实用工具）](../../database-engine/utility-administration-sql-server-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="70211-121">For more information about setting application monitoring policies, see [Utility Administration &#40;SQL Server Utility&#41;](../../database-engine/utility-administration-sql-server-utility.md).</span></span>  
  
 <span data-ttu-id="70211-122">查看“已部署的数据层应用程序”详细信息页：</span><span class="sxs-lookup"><span data-stu-id="70211-122">To view the **Deployed Data-tier Applications** detail page:</span></span>  
  
1.  <span data-ttu-id="70211-123">选择“视图/实用工具资源管理器”菜单。</span><span class="sxs-lookup"><span data-stu-id="70211-123">Select the **View/Utility Explorer** menu.</span></span>  
  
2.  <span data-ttu-id="70211-124">将“实用工具资源管理器”连接到实用工具控制点 (UCP)。</span><span class="sxs-lookup"><span data-stu-id="70211-124">Connect the **Utility Explorer** to the utility control point (UCP).</span></span>  
  
3.  <span data-ttu-id="70211-125">选择“视图/实用工具资源管理器详细信息”菜单。</span><span class="sxs-lookup"><span data-stu-id="70211-125">Select the **View/Utility Explorer Details** menu.</span></span>  
  
4.  <span data-ttu-id="70211-126">在“实用工具资源管理器”中选择“已部署的数据层应用程序”节点。</span><span class="sxs-lookup"><span data-stu-id="70211-126">Select the **Deployed Data-tier Applications** node in the **Utility Explorer**.</span></span>  
  
 <span data-ttu-id="70211-127">“已部署的数据层应用程序”详细信息页中的信息来自实用工具管理数据仓库中的数据，实用工具管理数据仓库默认为每 15 分钟收集数据。</span><span class="sxs-lookup"><span data-stu-id="70211-127">The information in the **Deployed Data-tier Applications** detail page comes from the data in the utility management data warehouse, which defaults to collecting the data every 15 minutes.</span></span> <span data-ttu-id="70211-128">还可以使用 **“实用工具管理”** 详细信息页定制该间隔。</span><span class="sxs-lookup"><span data-stu-id="70211-128">The interval can also be tailored using the **Utility Administration** details page.</span></span>  
  
## <a name="using-object-explorer"></a><span data-ttu-id="70211-129">使用对象资源管理器</span><span class="sxs-lookup"><span data-stu-id="70211-129">Using Object Explorer</span></span>  
 <span data-ttu-id="70211-130">SSMS **“对象资源管理器”** 显示与部署到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]实例的每个 DAC 有关的基本配置信息。</span><span class="sxs-lookup"><span data-stu-id="70211-130">The SSMS **Object Explorer** displays basic configuration information about each DAC deployed to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="70211-131">这包括已在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实用工具中注册的托管实例，以及无法在“实用工具资源管理器”\*\*\*\* 中查看的独立实例。</span><span class="sxs-lookup"><span data-stu-id="70211-131">This includes both managed instances that have been enrolled in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility, and stand-alone instances that cannot be viewed in the **Utility Explorer**.</span></span>  
  
 <span data-ttu-id="70211-132">查看与部署到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]实例的 DAC 有关的详细信息：</span><span class="sxs-lookup"><span data-stu-id="70211-132">To view the details of a DAC deployed to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)]:</span></span>  
  
1.  <span data-ttu-id="70211-133">选择“视图/对象资源管理器”菜单。</span><span class="sxs-lookup"><span data-stu-id="70211-133">Select the **View/Object Explorer** menu.</span></span>  
  
2.  <span data-ttu-id="70211-134">从对象资源管理器窗格连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]实例。</span><span class="sxs-lookup"><span data-stu-id="70211-134">Connect to the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)]from the Object Explorer pane.</span></span>  
  
3.  <span data-ttu-id="70211-135">选择“视图/对象资源管理器详细信息”菜单。</span><span class="sxs-lookup"><span data-stu-id="70211-135">Select the **View/Object Explorer Details** menu.</span></span>  
  
4.  <span data-ttu-id="70211-136">在“对象资源管理器”中选择映射到该实例的服务器节点，然后导航到“管理\数据层应用程序”节点。</span><span class="sxs-lookup"><span data-stu-id="70211-136">Select the server node in **Object Explorer** that maps to the instance, and then navigate to the **Management\Data-tier Applications** node.</span></span>  
  
5.  <span data-ttu-id="70211-137">详细信息页的顶部窗格中的列表视图列出部署到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]实例的每个 DAC。</span><span class="sxs-lookup"><span data-stu-id="70211-137">The list view in the top pane of the details page lists each DAC deployed to the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="70211-138">在页面的底部选择要在详细信息窗格中显示信息的 DAC。</span><span class="sxs-lookup"><span data-stu-id="70211-138">Select a DAC to display the information in the detail pane at the bottom of the page.</span></span>  
  
 <span data-ttu-id="70211-139">“数据层应用程序”节点的右键单击菜单还用于部署新的 DAC 或者删除现有 DAC。</span><span class="sxs-lookup"><span data-stu-id="70211-139">The right-click menu of the **Data-tier Applications** node is also used to deploy a new DAC or delete an existing DAC.</span></span>  
  
## <a name="using-the-dac-system-views-and-tables"></a><span data-ttu-id="70211-140">使用 DAC 系统视图和表</span><span class="sxs-lookup"><span data-stu-id="70211-140">Using the DAC System Views and Tables</span></span>  
 <span data-ttu-id="70211-141">msdb.dbo.sysdac_history_internal 系统表记录对 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例执行的所有 DAC 管理操作是成功还是失败。</span><span class="sxs-lookup"><span data-stu-id="70211-141">The msdb.dbo.sysdac_history_internal system table records the success or failure of all DAC management actions performed on an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="70211-142">该表记录发生每个操作的时间，以及执行了操作的登录名。</span><span class="sxs-lookup"><span data-stu-id="70211-142">The table records the time each action occurred, and which login initiated the action.</span></span> <span data-ttu-id="70211-143">有关详细信息，请参阅 [sysdac_history_internal (Transact-SQL)](/sql/relational-databases/system-tables/data-tier-application-tables-sysdac-history-internal)。</span><span class="sxs-lookup"><span data-stu-id="70211-143">For more information, see [sysdac_history_internal &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/data-tier-application-tables-sysdac-history-internal).</span></span>  
  
 <span data-ttu-id="70211-144">DAC 系统视图报告基本的目录信息。</span><span class="sxs-lookup"><span data-stu-id="70211-144">The DAC system views report basic catalog information.</span></span> <span data-ttu-id="70211-145">有关详细信息，请参阅[数据层应用程序视图 (Transact-SQL)](/sql/relational-databases/system-catalog-views/data-tier-application-views-dbo-sysdac-instances)。</span><span class="sxs-lookup"><span data-stu-id="70211-145">For more information, see [Data-tier Application Views &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/data-tier-application-views-dbo-sysdac-instances).</span></span>  
  
## <a name="monitoring-dac-databases"></a><span data-ttu-id="70211-146">监视 DAC 数据库</span><span class="sxs-lookup"><span data-stu-id="70211-146">Monitoring DAC Databases</span></span>  
 <span data-ttu-id="70211-147">在已成功部署某一 DAC 后，在该 DAC 中包含的数据库将像任何其他数据库一样操作。</span><span class="sxs-lookup"><span data-stu-id="70211-147">After a DAC has been successfully deployed, the database contained in the DAC operates the same as any other database.</span></span> <span data-ttu-id="70211-148">使用标准 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 技术和工具来监视数据库的性能、日志、事件和资源利用率。</span><span class="sxs-lookup"><span data-stu-id="70211-148">Use standard [!INCLUDE[ssDE](../../includes/ssde-md.md)] techniques and tools for monitoring the performance, log, events, and resource utilization of the database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70211-149">另请参阅</span><span class="sxs-lookup"><span data-stu-id="70211-149">See Also</span></span>  
 <span data-ttu-id="70211-150">[数据层应用程序](data-tier-applications.md) </span><span class="sxs-lookup"><span data-stu-id="70211-150">[Data-tier Applications](data-tier-applications.md) </span></span>  
 [<span data-ttu-id="70211-151">部署数据层应用程序</span><span class="sxs-lookup"><span data-stu-id="70211-151">Deploy a Data-tier Application</span></span>](deploy-a-data-tier-application.md)  
  
  
