---
title: 使用 AlwaysOn 策略查看可用性组的运行状况 (SQL Server) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 6f1bcbc3-1220-4071-8e53-4b957f5d3089
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5c4444afc2348b2407dc19c1c12761ef0251631e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693469"
---
# <a name="use-alwayson-policies-to-view-the-health-of-an-availability-group-sql-server"></a><span data-ttu-id="72af8-102">使用 AlwaysOn 策略查看可用性组的运行状况 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="72af8-102">Use AlwaysOn Policies to View the Health of an Availability Group (SQL Server)</span></span>
  <span data-ttu-id="72af8-103">本主题说明在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 中如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]或 PowerShell 通过 AlwaysOn 策略确定 AlwaysOn 可用性组的运行状况。</span><span class="sxs-lookup"><span data-stu-id="72af8-103">This topic describes how to determine the operational health of an AlwaysOn availability group by using an AlwaysOn policy in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="72af8-104">有关 AlwaysOn 基于策略的管理的信息，请参阅[AlwaysOn 可用性组 (SQL Server) 的操作问题的 AlwaysOn 策略](always-on-policies-for-operational-issues-always-on-availability.md)。</span><span class="sxs-lookup"><span data-stu-id="72af8-104">For information about AlwaysOn Policy Based Management, see [AlwaysOn Policies for Operational Issues with AlwaysOn Availability Groups (SQL Server)](always-on-policies-for-operational-issues-always-on-availability.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="72af8-105">对于 AlwaysOn 策略，类别名称用作 ID。</span><span class="sxs-lookup"><span data-stu-id="72af8-105">For AlwaysOn policies, the category names are used as IDs.</span></span> <span data-ttu-id="72af8-106">更改 AlwaysOn 类别的名称将会破坏其运行状况评价功能。</span><span class="sxs-lookup"><span data-stu-id="72af8-106">Changing the name of an AlwaysOn category would break its health-evaluation functionality.</span></span> <span data-ttu-id="72af8-107">因此，任何时候都不应修改 AlwaysOn 类别的名称。</span><span class="sxs-lookup"><span data-stu-id="72af8-107">Therefore, the names of AlwaysOn category should never be modified.</span></span>  
  

  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="72af8-108">开始之前</span><span class="sxs-lookup"><span data-stu-id="72af8-108">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="72af8-109">Security</span><span class="sxs-lookup"><span data-stu-id="72af8-109">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="72af8-110">权限</span><span class="sxs-lookup"><span data-stu-id="72af8-110">Permissions</span></span>  
 <span data-ttu-id="72af8-111">需要 CONNECT、VIEW SERVER STATE 和 VIEW ANY DEFINITION 权限。</span><span class="sxs-lookup"><span data-stu-id="72af8-111">Requires CONNECT, VIEW SERVER STATE, and VIEW ANY DEFINITION permissions.</span></span>  
  
##  <a name="using-the-alwayson-dashboard"></a><a name="SSMSProcedure"></a><span data-ttu-id="72af8-112">使用 AlwaysOn 仪表板</span><span class="sxs-lookup"><span data-stu-id="72af8-112">Using the AlwaysOn Dashboard</span></span>  
 <span data-ttu-id="72af8-113">**打开 AlwaysOn 仪表板**</span><span class="sxs-lookup"><span data-stu-id="72af8-113">**To open the AlwaysOn Dashboard**</span></span>  
  
1.  <span data-ttu-id="72af8-114">在对象资源管理器中，连接到承载可用性副本之一的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="72af8-114">In Object Explorer, connect to the server instance that hosts one of the availability replicas.</span></span> <span data-ttu-id="72af8-115">若要查看有关可用性组中所有可用性副本的信息，请使用承载主副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="72af8-115">To view information about all of the availability replicas in an availability group, use to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="72af8-116">单击服务器名称以展开服务器树。</span><span class="sxs-lookup"><span data-stu-id="72af8-116">Click the server name to expand the server tree.</span></span>  
  
3.  <span data-ttu-id="72af8-117">展开 **“AlwaysOn 高可用性”** 节点。</span><span class="sxs-lookup"><span data-stu-id="72af8-117">Expand the **AlwaysOn High Availability** node.</span></span>  
  
     <span data-ttu-id="72af8-118">右键单击“可用性组”\*\*\*\* 节点或展开此节点，然后右键单击特定的可用性组。</span><span class="sxs-lookup"><span data-stu-id="72af8-118">Either right-click the **Availability Groups** node or expand this node and right-click a specific availability group.</span></span>  
  
4.  <span data-ttu-id="72af8-119">选择 **“显示面板”** 命令。</span><span class="sxs-lookup"><span data-stu-id="72af8-119">Select the **Show Dashboard** command.</span></span>  
  
 <span data-ttu-id="72af8-120">有关如何使用 AlwaysOn 面板的信息，请参阅[使用 AlwaysOn 面板 (SQL Server Management Studio)](use-the-always-on-dashboard-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="72af8-120">For information about how to use the AlwaysOn Dashboard, see [Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md).</span></span>  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="72af8-121">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="72af8-121">Using PowerShell</span></span>  
 <span data-ttu-id="72af8-122">**使用 AlwaysOn 策略查看可用性组的运行状况**</span><span class="sxs-lookup"><span data-stu-id="72af8-122">**Use AlwaysOn policies to view the health of an availability group**</span></span>  
  
1.  <span data-ttu-id="72af8-123">将默认值 (`cd`) 设置为承载其中一个可用性副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="72af8-123">Set default (`cd`) to a server instance that hosts one of the availability replicas.</span></span> <span data-ttu-id="72af8-124">若要查看有关可用性组中所有可用性副本的信息，请使用承载主副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="72af8-124">To view information about all of the availability replicas in an availability group, use to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="72af8-125">使用以下 cmdlet：</span><span class="sxs-lookup"><span data-stu-id="72af8-125">Use the following cmdlets:</span></span>  
  
     `Test-SqlAvailabilityGroup`  
     <span data-ttu-id="72af8-126">通过评估 SQL Server 基于策略的管理 (PBM) 策略来评估可用性组的运行状况。</span><span class="sxs-lookup"><span data-stu-id="72af8-126">Assesses the health of an availability group by evaluating SQL Server policy based management (PBM) policies.</span></span> <span data-ttu-id="72af8-127">您必须具有 CONNECT、VIEW SERVER STATE 和 VIEW ANY DEFINITION 权限才能执行此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="72af8-127">You must have CONNECT, VIEW SERVER STATE, and VIEW ANY DEFINITION permissions to execute this cmdlet.</span></span>  
  
     <span data-ttu-id="72af8-128">例如，以下命令显示服务器实例 `Computer\Instance`上运行状况状态为“Error”的所有可用性组。</span><span class="sxs-lookup"><span data-stu-id="72af8-128">For example, the following command shows all availability groups with a health state of "Error" on the server instance `Computer\Instance`.</span></span>  
  
    ```powershell
    Get-ChildItem SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups |
        Test-SqlAvailabilityGroup |
        Where-Object { $_.HealthState -eq "Error" }  
    ```  
  
     `Test-SqlAvailabilityReplica`  
     <span data-ttu-id="72af8-129">通过评估 SQL Server 基于策略的管理 (PBM) 策略来评估可用性副本的运行状况。</span><span class="sxs-lookup"><span data-stu-id="72af8-129">Assesses the health of availability replicas by evaluating SQL Server policy based management (PBM) policies.</span></span> <span data-ttu-id="72af8-130">您必须具有 CONNECT、VIEW SERVER STATE 和 VIEW ANY DEFINITION 权限才能执行此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="72af8-130">You must have CONNECT, VIEW SERVER STATE, and VIEW ANY DEFINITION permissions to execute this cmdlet.</span></span>  
  
     <span data-ttu-id="72af8-131">例如，以下命令评估可用性组 `MyReplica` 中名为 `MyAg` 的可用性副本的运行状况并输出简短摘要。</span><span class="sxs-lookup"><span data-stu-id="72af8-131">For example, the following command evaluates the health of the availability replica named `MyReplica` in the availability group `MyAg` and outputs a brief summary.</span></span>  
  
    ```powershell
    Test-SqlAvailabilityReplica -Path SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\MyAg\AvailabilityReplicas\MyReplica  
    ```  
  
     `Test-SqlDatabaseReplicaState`  
     <span data-ttu-id="72af8-132">通过评估 SQL Server 基于策略的管理 (PBM) 策略来评估所有联接的可用性副本的可用性数据库的运行状况。</span><span class="sxs-lookup"><span data-stu-id="72af8-132">Assesses the health of an availability database on all joined availability replicas by evaluating SQL Server policy based management (PBM) policies.</span></span>  
  
     <span data-ttu-id="72af8-133">例如，以下命令评估可用性组 `MyAg` 中所有可用性数据库的运行状况并输出各数据库的简短摘要。</span><span class="sxs-lookup"><span data-stu-id="72af8-133">For example, the following command evaluates the health of all availability databases in the availability group `MyAg` and outputs a brief summary for each database.</span></span>  
  
    ```powershell
    Get-ChildItem SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\MyAg\DatabaseReplicaStates |
        Test-SqlDatabaseReplicaState  
    ```  
  
     <span data-ttu-id="72af8-134">这些 cmdlet 接受以下选项：</span><span class="sxs-lookup"><span data-stu-id="72af8-134">These cmdlets accept the following options:</span></span>  
  
    |<span data-ttu-id="72af8-135">选项</span><span class="sxs-lookup"><span data-stu-id="72af8-135">Option</span></span>|<span data-ttu-id="72af8-136">说明</span><span class="sxs-lookup"><span data-stu-id="72af8-136">Description</span></span>|  
    |------------|-----------------|  
    |`AllowUserPolicies`|<span data-ttu-id="72af8-137">运行在 AlwaysOn 策略类别中找到的用户策略。</span><span class="sxs-lookup"><span data-stu-id="72af8-137">Runs user policies found in the AlwaysOn policy categories.</span></span>|  
    |`InputObject`|<span data-ttu-id="72af8-138">对象的集合，表示可用性组、可用性副本或可用性数据库状态（取决于正在使用的 cmdlet）。</span><span class="sxs-lookup"><span data-stu-id="72af8-138">A collection of objects that, represent availability groups, availability replicas, or availability database states (depending on which cmdlet you are using).</span></span> <span data-ttu-id="72af8-139">此 cmdlet 将计算指定对象的运行状况。</span><span class="sxs-lookup"><span data-stu-id="72af8-139">The cmdlet will compute the health of the specified objects.</span></span>|  
    |`NoRefresh`|<span data-ttu-id="72af8-140">如果设置了此参数，cmdlet 将不会手动刷新由 `-Path` 或 `-InputObject` 参数指定的对象。</span><span class="sxs-lookup"><span data-stu-id="72af8-140">When this parameter is set, the cmdlet will not manually refresh the objects specified by the `-Path` or `-InputObject` parameter.</span></span>|  
    |`Path`|<span data-ttu-id="72af8-141">指向可用性组、一个或多个可用性副本或可用性数据库的数据库副本群集状态的路径（具体取决于正在使用的 cmdlet）。</span><span class="sxs-lookup"><span data-stu-id="72af8-141">The path to the availability group, one or more availability replicas, or database replica cluster state of the availability database (depending on which cmdlet you are using).</span></span> <span data-ttu-id="72af8-142">这是一个可选参数。</span><span class="sxs-lookup"><span data-stu-id="72af8-142">This is an optional parameter.</span></span> <span data-ttu-id="72af8-143">如果未指定，此参数的值默认为当前的工作位置。</span><span class="sxs-lookup"><span data-stu-id="72af8-143">If not specified, the value of this parameter defaults to the current working location.</span></span>|  
    |`ShowPolicyDetails`|<span data-ttu-id="72af8-144">显示由 cmdlet 执行的每个策略评估的结果。</span><span class="sxs-lookup"><span data-stu-id="72af8-144">Shows the result of each policy evaluation performed by this cmdlet.</span></span> <span data-ttu-id="72af8-145">对于每个策略评估，cmdlet 都输出一个对象，该对象具有用于描述评估结果的字段（是否传递了策略、策略名称和类别等等）。</span><span class="sxs-lookup"><span data-stu-id="72af8-145">The cmdlet outputs one object per policy evaluation, and this object has fields describing the results of evaluation (whether the policy passed or not, the policy name and category, and so forth).</span></span>|  
  
     <span data-ttu-id="72af8-146">例如，以下 `Test-SqlAvailabilityGroup` 命令指定 `-ShowPolicyDetails` 参数，以为在名为 `MyAg` 的可用性组上执行的每个基于策略的管理 (PBM) 策略显示此 cmdlet 执行的每个策略评估结果。</span><span class="sxs-lookup"><span data-stu-id="72af8-146">For example, the following `Test-SqlAvailabilityGroup` command specifies the `-ShowPolicyDetails` parameter to show the result of each policy evaluation performed by this cmdlet for each policy-based management (PBM) policy that was executed on the availability group named `MyAg`.</span></span>  
  
    ```powershell
    Test-SqlAvailabilityGroup -Path SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\AgName -ShowPolicyDetails  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="72af8-147">若要查看 cmdlet 的语法，请在 `Get-Help` PowerShell 环境中使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cmdlet。</span><span class="sxs-lookup"><span data-stu-id="72af8-147">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="72af8-148">有关详细信息，请参阅 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="72af8-148">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
 <span data-ttu-id="72af8-149">**设置和使用 SQL Server PowerShell 提供程序**</span><span class="sxs-lookup"><span data-stu-id="72af8-149">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="72af8-150">SQL Server PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="72af8-150">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
-   [<span data-ttu-id="72af8-151">Get Help SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="72af8-151">Get Help SQL Server PowerShell</span></span>](../../../powershell/sql-server-powershell.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="72af8-152">相关内容</span><span class="sxs-lookup"><span data-stu-id="72af8-152">Related Content</span></span>  
 <span data-ttu-id="72af8-153">**SQL Server AlwaysOn 团队博客-通过 PowerShell 监视 AlwaysOn 运行状况：**</span><span class="sxs-lookup"><span data-stu-id="72af8-153">**SQL Server AlwaysOn Team Blogs-Monitoring AlwaysOn Health with PowerShell:**</span></span>  
  
-   [<span data-ttu-id="72af8-154">第一部分：基本 Cmdlet 概述</span><span class="sxs-lookup"><span data-stu-id="72af8-154">Part 1: Basic Cmdlet Overview</span></span>](https://docs.microsoft.com/archive/blogs/sqlalwayson/monitoring-alwayson-health-with-powershell-part-1-basic-cmdlet-overview)  
  
-   [<span data-ttu-id="72af8-155">第二部分：高级 Cmdlet 用法</span><span class="sxs-lookup"><span data-stu-id="72af8-155">Part 2: Advanced Cmdlet Usage</span></span>](https://docs.microsoft.com/archive/blogs/sqlalwayson/the-alwayson-health-model-part-2-extending-the-health-model)  
  
-   [<span data-ttu-id="72af8-156">第三部分：简单的监视应用程序</span><span class="sxs-lookup"><span data-stu-id="72af8-156">Part 3: A Simple Monitoring Application</span></span>](https://docs.microsoft.com/archive/blogs/sqlalwayson/monitoring-alwayson-health-with-powershell-part-3-a-simple-monitoring-application)  
  
-   [<span data-ttu-id="72af8-157">第四部分：与 SQL Server 代理集成</span><span class="sxs-lookup"><span data-stu-id="72af8-157">Part 4: Integration with SQL Server Agent</span></span>](https://docs.microsoft.com/archive/blogs/sqlalwayson/monitoring-alwayson-health-with-powershell-part-4-integration-with-sql-server-agent)  
  
## <a name="see-also"></a><span data-ttu-id="72af8-158">另请参阅</span><span class="sxs-lookup"><span data-stu-id="72af8-158">See Also</span></span>  
 <span data-ttu-id="72af8-159">[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="72af8-159">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="72af8-160">[管理可用性组 &#40;SQL Server&#41;](administration-of-an-availability-group-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="72af8-160">[Administration of an Availability Group &#40;SQL Server&#41;](administration-of-an-availability-group-sql-server.md) </span></span>  
 <span data-ttu-id="72af8-161">[监视可用性组 (SQL Server)](monitoring-of-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="72af8-161">[Monitoring of Availability Groups &#40;SQL Server&#41;](monitoring-of-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="72af8-162">针对 AlwaysOn 可用性组运行问题的 AlwaysOn 策略 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="72af8-162">AlwaysOn Policies for Operational Issues with AlwaysOn Availability Groups (SQL Server)</span></span>](always-on-policies-for-operational-issues-always-on-availability.md) 
