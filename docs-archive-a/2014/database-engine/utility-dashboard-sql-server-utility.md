---
title: SQL Server 实用工具) 的实用工具仪表板 (|Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 999eb741-4a60-43f6-ab37-2df7dce845c1
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 1e6f59eca0aaaee0d0fc79f267a781b650fb3d58
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689566"
---
# <a name="utility-dashboard-sql-server-utility"></a><span data-ttu-id="91762-102">实用工具面板（SQL Server 实用工具）</span><span class="sxs-lookup"><span data-stu-id="91762-102">Utility Dashboard (SQL Server Utility)</span></span>
  <span data-ttu-id="91762-103">若要在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实用工具仪表板中查看数据，请在标有“Utility<UCP_Name>\\(ComputerName\UCP)”的实用工具资源管理器树中选择顶端节点。</span><span class="sxs-lookup"><span data-stu-id="91762-103">To see data in the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Utility dashboard, select the top node in the Utility Explorer tree - labeled "Utility<UCP_Name>\\(ComputerName\UCP)."</span></span> <span data-ttu-id="91762-104">该面板包括来自 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的所有托管实例和 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实用工具中所有数据层应用程序的摘要和详细信息数据。</span><span class="sxs-lookup"><span data-stu-id="91762-104">The dashboard includes summary and detail data from all managed instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] and all data-tier applications in the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Utility.</span></span> <span data-ttu-id="91762-105">若要刷新仪表板中的数据，请在实用工具资源管理器树中右键单击该顶端节点，然后选择“刷新”。</span><span class="sxs-lookup"><span data-stu-id="91762-105">To refresh data in the dashboard, right-click the top node in the Utility Explorer tree, and select **Refresh**.</span></span>  
  
 <span data-ttu-id="91762-106">有关如何创建实用工具控制点的详细信息点，请参阅 [创建 SQL Server 实用工具控制点（SQL Server 实用工具）](../relational-databases/manage/create-a-sql-server-utility-control-point-sql-server-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="91762-106">For more information about how to create a utility control point, see [Create a SQL Server Utility Control Point &#40;SQL Server Utility&#41;](../relational-databases/manage/create-a-sql-server-utility-control-point-sql-server-utility.md).</span></span> <span data-ttu-id="91762-107">有关如何将 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例添加到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实用工具的详细信息，请参阅 [注册 SQL Server 实例（SQL Server 实用工具）](../relational-databases/manage/enroll-an-instance-of-sql-server-sql-server-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="91762-107">For more information about how to add an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Utility, see [Enroll an Instance of SQL Server &#40;SQL Server Utility&#41;](../relational-databases/manage/enroll-an-instance-of-sql-server-sql-server-utility.md).</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="91762-108">UI 元素列表</span><span class="sxs-lookup"><span data-stu-id="91762-108">UI element list</span></span>  
 <span data-ttu-id="91762-109">托管实例运行状况</span><span class="sxs-lookup"><span data-stu-id="91762-109">Managed Instance Health</span></span>  
 <span data-ttu-id="91762-110">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的托管实例的运行状态显示在实用工具资源管理器内容窗格的左侧。</span><span class="sxs-lookup"><span data-stu-id="91762-110">Health status for managed instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] is displayed on the left side of the Utility Explorer content pane.</span></span>  
  
 <span data-ttu-id="91762-111">托管实例的运行状况参数如下所示：</span><span class="sxs-lookup"><span data-stu-id="91762-111">Managed Instance Health parameters are as follows:</span></span>  
  
-   <span data-ttu-id="91762-112">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]实例的 CPU 使用率。</span><span class="sxs-lookup"><span data-stu-id="91762-112">CPU utilization for the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="91762-113">数据库文件使用率。</span><span class="sxs-lookup"><span data-stu-id="91762-113">Database file utilization.</span></span>  
  
-   <span data-ttu-id="91762-114">存储卷空间使用率。</span><span class="sxs-lookup"><span data-stu-id="91762-114">Storage volume space utilization.</span></span>  
  
-   <span data-ttu-id="91762-115">计算机的 CPU 使用率。</span><span class="sxs-lookup"><span data-stu-id="91762-115">CPU utilization for the computer.</span></span>  
  
-   <span data-ttu-id="91762-116">每个参数的状态划分为三个类别：</span><span class="sxs-lookup"><span data-stu-id="91762-116">Status for each parameter is divided into three categories:</span></span>  
  
-   <span data-ttu-id="91762-117">很好地利用 - 没有违反资源使用策略的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 托管实例的数目。</span><span class="sxs-lookup"><span data-stu-id="91762-117">Well-utilized - Number of managed instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] which are not violating resource utilization policies.</span></span>  
  
-   <span data-ttu-id="91762-118">使用不足 - 违反资源使用不足策略的托管资源的数目。</span><span class="sxs-lookup"><span data-stu-id="91762-118">Underutilized - Number of managed resources which are violating resource underutilization policies.</span></span>  
  
-   <span data-ttu-id="91762-119">使用过度 - 违反资源使用过度策略的托管资源的数目。</span><span class="sxs-lookup"><span data-stu-id="91762-119">Overutilized - Number of managed resources which are violating resource overutilization policies.</span></span>  
  
-   <span data-ttu-id="91762-120">没有可用数据 - 数据不可用于 SQL Server 的托管实例，这或者是因为 SQL Server 刚注册并且第一个数据收集操作尚未完成，或者是因为存在与收集数据并将数据上载到 UCP 的 SQL Server 托管实例有关的问题。</span><span class="sxs-lookup"><span data-stu-id="91762-120">No Data Available - Data is not available for managed instances of SQL Server either because the instance of SQL Server has just been enrolled and the first data collection operation has not completed, or because there is a problem with the managed instance of SQL Server collecting and uploading data to the UCP.</span></span>  
  
 <span data-ttu-id="91762-121">每个运行状况参数的详细状态在滑动指示器中列出。</span><span class="sxs-lookup"><span data-stu-id="91762-121">Detailed status for each health parameter is listed in sliding indicators.</span></span> <span data-ttu-id="91762-122">滑动指示器右侧的部分显示有多少个托管实例处于各状态类别中。</span><span class="sxs-lookup"><span data-stu-id="91762-122">The fraction to the right of the sliding indicators shows how many managed instances are in each status category.</span></span>  
  
 <span data-ttu-id="91762-123">若要创建 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的托管实例或数据层应用程序的筛选视图，请在实用工具面板中单击其滑动指示器旁的使用率类别链接。</span><span class="sxs-lookup"><span data-stu-id="91762-123">To create a filtered view of a managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] or a data-tier application, click on the link for a utilization category next to its sliding indicator in the Utility dashboard.</span></span> <span data-ttu-id="91762-124">例如，如果您在 **“实用工具资源管理器内容”** 窗格中单击 **“使用过度的实例 CPU”** ，则 SSMS 将基于当前策略设置创建具有使用过度的 CPU 的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 托管实例的筛选后列表视图。</span><span class="sxs-lookup"><span data-stu-id="91762-124">For example, if you click on **Overutilized Instance CPU** in the **Utility Explorer Content** pane, SSMS creates a filtered list view of managed instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that have overutilized CPU based on current policy settings.</span></span>  
  
 <span data-ttu-id="91762-125">请注意，在你单击某一使用率类别链接时，实用工具资源管理器导航窗格中的相应节点将追加“(已筛选)”- 也就是说，“托管实例”将标记为“托管实例(已筛选)”。</span><span class="sxs-lookup"><span data-stu-id="91762-125">Notice that when you click on a link for a utilization category, the corresponding node in the Utility Explorer navigation pane is appended with **(filtered)** - that is, **Managed Instances** is labeled **Managed Instances (filtered)**.</span></span> <span data-ttu-id="91762-126">若要查看筛选设置，请在导航窗格中右键单击该节点，选择“筛选器”，然后单击“筛选设置”。</span><span class="sxs-lookup"><span data-stu-id="91762-126">To view filter settings, right-click on the node in the navigation pane and select **Filter**, then click on **Filter Settings**.</span></span> <span data-ttu-id="91762-127">若要清除筛选设置，请在导航窗格中右键单击该节点，选择“筛选器”，然后单击“删除筛选器”。</span><span class="sxs-lookup"><span data-stu-id="91762-127">To clear filter settings, right-click on the node in the navigation pane and select **Filter**, then click on **Remove Filter**.</span></span>  
  
 <span data-ttu-id="91762-128">有关查看 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的单独实例的运行状况的详细信息，或者有关查看或更改策略配置设置的详细信息，请参阅[托管实例详细信息（SQL Server 实用工具）](../../2014/database-engine/managed-instance-details-sql-server-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="91762-128">For more information about viewing health status for individual instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], or to view or change policy configuration settings, see [Managed Instance Details &#40;SQL Server Utility&#41;](../../2014/database-engine/managed-instance-details-sql-server-utility.md).</span></span>  
  
 <span data-ttu-id="91762-129">实用工具摘要</span><span class="sxs-lookup"><span data-stu-id="91762-129">Utility Summary</span></span>  
 <span data-ttu-id="91762-130">显示 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的托管实例的数目以及 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实用工具管理的数据层应用程序的数目。</span><span class="sxs-lookup"><span data-stu-id="91762-130">Displays the number of managed instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] and the number of data-tier applications managed by the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Utility.</span></span>  
  
 <span data-ttu-id="91762-131">数据层应用程序运行状况</span><span class="sxs-lookup"><span data-stu-id="91762-131">Data-tier Application Health</span></span>  
 <span data-ttu-id="91762-132">数据层应用程序的运行状态显示在实用工具资源管理器内容窗格的右侧。</span><span class="sxs-lookup"><span data-stu-id="91762-132">Health status for data-tier applications is displayed on the right side of the Utility Explorer content pane.</span></span>  
  
 <span data-ttu-id="91762-133">数据层应用程序运行状况参数如下所示：</span><span class="sxs-lookup"><span data-stu-id="91762-133">Data-tier Application Health parameters are as follows:</span></span>  
  
-   <span data-ttu-id="91762-134">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]实例的 CPU 使用率。</span><span class="sxs-lookup"><span data-stu-id="91762-134">CPU utilization for the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="91762-135">数据库文件使用率。</span><span class="sxs-lookup"><span data-stu-id="91762-135">Database file utilization.</span></span>  
  
-   <span data-ttu-id="91762-136">存储卷空间使用率。</span><span class="sxs-lookup"><span data-stu-id="91762-136">Storage volume space utilization.</span></span>  
  
-   <span data-ttu-id="91762-137">计算机的 CPU 使用率。</span><span class="sxs-lookup"><span data-stu-id="91762-137">CPU utilization for the computer.</span></span>  
  
 <span data-ttu-id="91762-138">每个参数的状态划分为三个类别：</span><span class="sxs-lookup"><span data-stu-id="91762-138">Status for each parameter is divided into three categories:</span></span>  
  
-   <span data-ttu-id="91762-139">很好地利用 - 没有违反资源使用策略的数据层应用程序的数目。</span><span class="sxs-lookup"><span data-stu-id="91762-139">Well-utilized - Number of data-tier applications which are not violating resource utilization policies.</span></span>  
  
-   <span data-ttu-id="91762-140">使用过度 - 违反资源使用过度策略的数据层应用程序的数目。</span><span class="sxs-lookup"><span data-stu-id="91762-140">Overutilized - Number of data-tier applications which are violating resource overutilization policies.</span></span>  
  
-   <span data-ttu-id="91762-141">使用过度 - 违反资源使用过度策略的数据层应用程序的数目。</span><span class="sxs-lookup"><span data-stu-id="91762-141">Underutilized - Number of data-tier applications which are violating resource underutilization policies.</span></span>  
  
-   <span data-ttu-id="91762-142">没有可用数据 - 数据不可用于数据层应用程序，因为包含数据层应用程序的 SQL Server 托管实例未报告数据。</span><span class="sxs-lookup"><span data-stu-id="91762-142">No Data Available - Data is not available for data-tier applications because the managed instance of SQL Server that contains the data-tier application is not reporting data.</span></span>  
  
 <span data-ttu-id="91762-143">每个运行状况参数的详细状态在滑动指示器中列出。</span><span class="sxs-lookup"><span data-stu-id="91762-143">Detailed status for each health parameter is listed in sliding indicators.</span></span> <span data-ttu-id="91762-144">滑动指示器右侧的部分显示有多少个数据层应用程序处于各状态类别中。</span><span class="sxs-lookup"><span data-stu-id="91762-144">The fraction to the right of the sliding indicators shows how many data-tier applications are in each status category.</span></span> <span data-ttu-id="91762-145">有关查看单独数据层应用程序运行状况的详细信息，或者有关查看或更改策略配置设置的详细信息，请参阅[已部署的数据层应用程序详细信息（SQL Server 实用工具）](../../2014/database-engine/deployed-data-tier-application-details-sql-server-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="91762-145">For more information about viewing health status for individual data-tier applications, or to view or change policy configuration settings, see [Deployed Data-tier Application Details &#40;SQL Server Utility&#41;](../../2014/database-engine/deployed-data-tier-application-details-sql-server-utility.md).</span></span>  
  
 <span data-ttu-id="91762-146">实用工具存储使用率历史记录</span><span class="sxs-lookup"><span data-stu-id="91762-146">Utility Storage Utilization History</span></span>  
 <span data-ttu-id="91762-147">实用工具历史记录显示在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实用工具面板底部的时间图中。</span><span class="sxs-lookup"><span data-stu-id="91762-147">Utilization history is shown in a time graph at the bottom of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Utility dashboard.</span></span> <span data-ttu-id="91762-148">请注意，时间数据使用 datetime 数据类型显示 UCP 本地日期和时间。</span><span class="sxs-lookup"><span data-stu-id="91762-148">Note that time data show the UCP local date and time using the datetime data type.</span></span> <span data-ttu-id="91762-149">有关详细信息，请参阅 SQL Server 联机丛书中的 [datetime (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=164071) 主题。</span><span class="sxs-lookup"><span data-stu-id="91762-149">For more information, see the [datetime (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=164071) topic in SQL Server Books Online.</span></span> <span data-ttu-id="91762-150">在使用实用工具对象模型时，请注意 SSMS 使用 datetimeoffset 数据类型。</span><span class="sxs-lookup"><span data-stu-id="91762-150">When using the Utility object model, note that SSMS uses the datetimeoffset data type.</span></span> <span data-ttu-id="91762-151">有关详细信息，请参阅 SQL Server 联机丛书中的 [datetimeoffset (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=141713) 主题。</span><span class="sxs-lookup"><span data-stu-id="91762-151">For more information, see the [datetimeoffset (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=141713) topic in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="91762-152">使用显示区域左侧的单选按钮可以更改图形的报告期间。</span><span class="sxs-lookup"><span data-stu-id="91762-152">Use the radio buttons to the left of the display area to change the reporting period for the graph.</span></span>  
  
 <span data-ttu-id="91762-153">报告间隔选项包括：</span><span class="sxs-lookup"><span data-stu-id="91762-153">Options for the reporting interval are:</span></span>  
  
-   <span data-ttu-id="91762-154">1 天，以 15 分钟间隔显示。</span><span class="sxs-lookup"><span data-stu-id="91762-154">1 Day, displayed in 15-minute intervals.</span></span>  
  
-   <span data-ttu-id="91762-155">1 周，以 1 天间隔显示。</span><span class="sxs-lookup"><span data-stu-id="91762-155">1 Week, displayed in 1-day intervals.</span></span>  
  
-   <span data-ttu-id="91762-156">1 个月，以 1 周间隔显示。</span><span class="sxs-lookup"><span data-stu-id="91762-156">1 Month, displayed in 1-week intervals.</span></span>  
  
-   <span data-ttu-id="91762-157">1 年，以 1 个月间隔显示。</span><span class="sxs-lookup"><span data-stu-id="91762-157">1 Year, displayed in 1-month intervals.</span></span>  
  
 <span data-ttu-id="91762-158">在对报告间隔进行更改后，数据将自动刷新。</span><span class="sxs-lookup"><span data-stu-id="91762-158">After you make a change to the reporting interval, the data refreshes automatically.</span></span>  
  
 <span data-ttu-id="91762-159">实用工具存储使用率</span><span class="sxs-lookup"><span data-stu-id="91762-159">Utility Storage Utilization</span></span>  
 <span data-ttu-id="91762-160">在面板的右下角中，存储使用率饼图显示在包含 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的托管实例的计算机上驻留的卷中已用空间与可用空间的比率。</span><span class="sxs-lookup"><span data-stu-id="91762-160">In the bottom right of the dashboard, the storage utilization pie chart displays the ratio of used space to free space on volumes residing on computers that contain managed instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="91762-161">此显示数据每隔 15 分钟刷新一次。</span><span class="sxs-lookup"><span data-stu-id="91762-161">Data for this display are refreshed every 15 minutes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91762-162">另请参阅</span><span class="sxs-lookup"><span data-stu-id="91762-162">See Also</span></span>  
 <span data-ttu-id="91762-163">[使用实用工具资源管理器管理 SQL Server 实用工具](../relational-databases/manage/use-utility-explorer-to-manage-the-sql-server-utility.md) </span><span class="sxs-lookup"><span data-stu-id="91762-163">[Use Utility Explorer to Manage the SQL Server Utility](../relational-databases/manage/use-utility-explorer-to-manage-the-sql-server-utility.md) </span></span>  
 <span data-ttu-id="91762-164">[SQL Server &#40;SQL Server 实用工具注册实例&#41;](../relational-databases/manage/enroll-an-instance-of-sql-server-sql-server-utility.md) </span><span class="sxs-lookup"><span data-stu-id="91762-164">[Enroll an Instance of SQL Server &#40;SQL Server Utility&#41;](../relational-databases/manage/enroll-an-instance-of-sql-server-sql-server-utility.md) </span></span>  
 [<span data-ttu-id="91762-165">修改资源运行状况策略定义（SQL Server 实用工具）</span><span class="sxs-lookup"><span data-stu-id="91762-165">Modify a Resource Health Policy Definition &#40;SQL Server Utility&#41;</span></span>](../relational-databases/manage/modify-a-resource-health-policy-definition-sql-server-utility.md)  
  
  
