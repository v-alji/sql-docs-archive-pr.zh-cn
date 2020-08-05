---
title: 使用 AlwaysOn 仪表板 (SQL Server Management Studio) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
- Availability Groups [SQL Server], dashboard
ms.assetid: c9ba2589-139e-42bc-99e1-94546717c64d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c4ce0072bcd6642dcb4f3ac63e04c98786bd550e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579787"
---
# <a name="use-the-alwayson-dashboard-sql-server-management-studio"></a><span data-ttu-id="30ffc-102">使用 AlwaysOn 面板 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="30ffc-102">Use the AlwaysOn Dashboard (SQL Server Management Studio)</span></span>
  <span data-ttu-id="30ffc-103">数据库管理员使用 AlwaysOn 面板大致了解 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]中的 AlwaysOn 可用性组及其可用性副本和数据库的运行状况。</span><span class="sxs-lookup"><span data-stu-id="30ffc-103">Database administrators use the AlwaysOn Dashboard to obtains an at-a-glance view the health of an AlwaysOn availability group and its availability replicas and databases in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="30ffc-104">AlwaysOn 面板的一些典型用法如下：</span><span class="sxs-lookup"><span data-stu-id="30ffc-104">Some of the typical uses for the AlwaysOn Dashboard are:</span></span>  
  
-   <span data-ttu-id="30ffc-105">选择要手动故障转移的副本。</span><span class="sxs-lookup"><span data-stu-id="30ffc-105">Choosing a replica for a manual failover.</span></span>  
  
-   <span data-ttu-id="30ffc-106">如果强制故障转移，则估计数据丢失。</span><span class="sxs-lookup"><span data-stu-id="30ffc-106">Estimating data loss if you force failover.</span></span>  
  
-   <span data-ttu-id="30ffc-107">评估数据同步性能。</span><span class="sxs-lookup"><span data-stu-id="30ffc-107">Evaluating data-synchronization performance.</span></span>  
  
-   <span data-ttu-id="30ffc-108">评估同步提交辅助副本对性能的影响</span><span class="sxs-lookup"><span data-stu-id="30ffc-108">Evaluating the performance impact of a synchronous-commit secondary replica</span></span>  
  
 <span data-ttu-id="30ffc-109">AlwaysOn 面板提供关键的可用性组状态和性能指示器，支持您使用以下几类信息轻松做出关于高可用性的可行性决策。</span><span class="sxs-lookup"><span data-stu-id="30ffc-109">The AlwaysOn Dashboard provides key availability group states and performance indicators allowing you to easily make high availability operational decisions using the following types of information.</span></span>  
  
-   <span data-ttu-id="30ffc-110">副本汇总状态</span><span class="sxs-lookup"><span data-stu-id="30ffc-110">Replica roll-up state</span></span>  
  
-   <span data-ttu-id="30ffc-111">同步模式和状态</span><span class="sxs-lookup"><span data-stu-id="30ffc-111">Synchronization mode and state</span></span>  
  
-   <span data-ttu-id="30ffc-112">估计数据丢失</span><span class="sxs-lookup"><span data-stu-id="30ffc-112">Estimate Data Loss</span></span>  
  
-   <span data-ttu-id="30ffc-113">估计的恢复时间（重做追赶时间）</span><span class="sxs-lookup"><span data-stu-id="30ffc-113">Estimated Recovery Time (redo catch up)</span></span>  
  
-   <span data-ttu-id="30ffc-114">数据库副本详细信息</span><span class="sxs-lookup"><span data-stu-id="30ffc-114">Database Replica details</span></span>  
  
-   <span data-ttu-id="30ffc-115">同步模式和状态</span><span class="sxs-lookup"><span data-stu-id="30ffc-115">Synchronization mode and state</span></span>  
  
-   <span data-ttu-id="30ffc-116">还原日志所需的时间</span><span class="sxs-lookup"><span data-stu-id="30ffc-116">Time to restore log</span></span>  
  
 
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="30ffc-117">开始之前</span><span class="sxs-lookup"><span data-stu-id="30ffc-117">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="30ffc-118">先决条件</span><span class="sxs-lookup"><span data-stu-id="30ffc-118">Prerequisites</span></span>  
 <span data-ttu-id="30ffc-119">您必须连接到承载可用性组的主副本或辅助副本的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例（服务器实例）。</span><span class="sxs-lookup"><span data-stu-id="30ffc-119">You must be connected to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (server instance) that hosts either the primary replica or a secondary replica of an availability group.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="30ffc-120">Security</span><span class="sxs-lookup"><span data-stu-id="30ffc-120">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="30ffc-121">权限</span><span class="sxs-lookup"><span data-stu-id="30ffc-121">Permissions</span></span>  
 <span data-ttu-id="30ffc-122">需要 CONNECT、VIEW SERVER STATE 和 VIEW ANY DEFINITION 权限。</span><span class="sxs-lookup"><span data-stu-id="30ffc-122">Requires CONNECT, VIEW SERVER STATE, and VIEW ANY DEFINITION permissions.</span></span>  
  
##  <a name="to-start-the-alwayson-dashboard"></a><a name="SSMSProcedure"></a><span data-ttu-id="30ffc-123">启动 AlwaysOn 面板</span><span class="sxs-lookup"><span data-stu-id="30ffc-123">To start the AlwaysOn Dashboard</span></span>  
  
1.  <span data-ttu-id="30ffc-124">在对象资源管理器中，连接到要运行 AlwaysOn 面板的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="30ffc-124">In Object Explorer, connect to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on which you want to run the AlwaysOn Dashboard.</span></span>  
  
2.  <span data-ttu-id="30ffc-125">展开“AlwaysOn 高可用性”\*\*\*\* 节点，右键单击“可用性组”\*\*\*\* 节点，然后单击“显示面板”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="30ffc-125">Expand the **AlwaysOn High Availability** node, right-click the **Availability Groups** node, and then click **Show Dashboard**.</span></span>  
  
###  <a name="to-change-alwayson-dashboard-options"></a><a name="DashboardOptions"></a><span data-ttu-id="30ffc-126">更改 AlwaysOn 面板选项</span><span class="sxs-lookup"><span data-stu-id="30ffc-126">To Change AlwaysOn Dashboard Options</span></span>  
 <span data-ttu-id="30ffc-127">可以使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 的“选项”\*\*\*\* 对话框配置 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] AlwaysOn 面板行为，使其自动刷新和启用自动定义的 AlwaysOn 策略。</span><span class="sxs-lookup"><span data-stu-id="30ffc-127">You can use the [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]**Options** dialog box to configure the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] AlwaysOn Dashboard behavior for automatic refreshing and enabling an auto-defined AlwaysOn policy.</span></span>  
  
1.  <span data-ttu-id="30ffc-128">从 **“工具”** 菜单中，单击 **“选项”** 。</span><span class="sxs-lookup"><span data-stu-id="30ffc-128">From the **Tools** menu, click **Options**.</span></span>  
  
2.  <span data-ttu-id="30ffc-129">若要自动刷新面板，在 **“选项”** 对话框中，选择 **“启用自动刷新”**，输入以秒计的刷新间隔，然后输入要重试连接的次数。</span><span class="sxs-lookup"><span data-stu-id="30ffc-129">To automatically refresh the dashboard, in the **Options** dialog box, select **Turn on automatic refresh**, enter the refresh interval in seconds, and then enter the number of times you want to retry the connection.</span></span>  
  
3.  <span data-ttu-id="30ffc-130">若要启用用户定义的策略，请选择“启用用户定义的 AlwaysOn 策略”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="30ffc-130">To enable a user-defined policy, select **Enable user-defined AlwaysOn policy**.</span></span>  
  
##  <a name="availability-group-summary"></a><a name="AvGroupsView"></a><span data-ttu-id="30ffc-131">可用性组摘要</span><span class="sxs-lookup"><span data-stu-id="30ffc-131">Availability Group Summary</span></span>  
 <span data-ttu-id="30ffc-132">可用性组屏幕为所连接服务器实例承载其副本的每个可用性组都显示一行摘要。</span><span class="sxs-lookup"><span data-stu-id="30ffc-132">The availability group screen displays a summary line for each availability group for which the connected server instance hosts a replica.</span></span> <span data-ttu-id="30ffc-133">此窗格显示以下列。</span><span class="sxs-lookup"><span data-stu-id="30ffc-133">This pane displays the following columns.</span></span>  
  
 <span data-ttu-id="30ffc-134">**可用性组名称**</span><span class="sxs-lookup"><span data-stu-id="30ffc-134">**Availability Group Name**</span></span>  
 <span data-ttu-id="30ffc-135">所连接服务器实例承载其副本的可用性组的名称。</span><span class="sxs-lookup"><span data-stu-id="30ffc-135">The name of an availability group for which the connected server instance hosts a replica.</span></span>  
  
 <span data-ttu-id="30ffc-136">**主实例**</span><span class="sxs-lookup"><span data-stu-id="30ffc-136">**Primary Instance**</span></span>  
 <span data-ttu-id="30ffc-137">正在承载可用性组的主副本的服务器实例的名称。</span><span class="sxs-lookup"><span data-stu-id="30ffc-137">Name of the server instance that is hosting the primary replica of the availability group.</span></span>  
  
 <span data-ttu-id="30ffc-138">**故障转移模式**</span><span class="sxs-lookup"><span data-stu-id="30ffc-138">**Failover Mode**</span></span>  
 <span data-ttu-id="30ffc-139">显示为副本配置的故障转移模式。</span><span class="sxs-lookup"><span data-stu-id="30ffc-139">Displays the failover mode for which the replica is configured.</span></span> <span data-ttu-id="30ffc-140">可能的故障转移模式值包括：</span><span class="sxs-lookup"><span data-stu-id="30ffc-140">The possible failover mode values are:</span></span>  
  
-   <span data-ttu-id="30ffc-141">**自动**。</span><span class="sxs-lookup"><span data-stu-id="30ffc-141">**Automatic**.</span></span> <span data-ttu-id="30ffc-142">指示一个或多个副本处于自动故障转移模式。</span><span class="sxs-lookup"><span data-stu-id="30ffc-142">Indicates that one or more replicas is in automatic-failover mode.</span></span>  
  
-   <span data-ttu-id="30ffc-143">**手动**。</span><span class="sxs-lookup"><span data-stu-id="30ffc-143">**Manual**.</span></span> <span data-ttu-id="30ffc-144">指示没有副本处于自动故障转移模式。</span><span class="sxs-lookup"><span data-stu-id="30ffc-144">Indicates that no replica is automatic-failover mode.</span></span>  
  
 <span data-ttu-id="30ffc-145">**问题**</span><span class="sxs-lookup"><span data-stu-id="30ffc-145">**Issues**</span></span>  
 <span data-ttu-id="30ffc-146">单击“问题”\*\*\*\* 链接可打开针对某一问题的故障排除文档。</span><span class="sxs-lookup"><span data-stu-id="30ffc-146">Click the **Issues** link to open troubleshooting documentation for a given issue.</span></span> <span data-ttu-id="30ffc-147">有关所有 AlwaysOn 策略问题的列表，请参阅[AlwaysOn 可用性组 (SQL Server) 的操作问题的 AlwaysOn 策略](always-on-policies-for-operational-issues-always-on-availability.md)。</span><span class="sxs-lookup"><span data-stu-id="30ffc-147">For a list of all the AlwaysOn policy issues, see [AlwaysOn Policies for Operational Issues with AlwaysOn Availability Groups (SQL Server)](always-on-policies-for-operational-issues-always-on-availability.md).</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="30ffc-148">单击列标题可按可用性组的名称、主实例、故障转移模式或问题对可用性组信息进行排序。</span><span class="sxs-lookup"><span data-stu-id="30ffc-148">Click the column headings to sort the availability group information by the name of the availability group, primary instance, failover mode, or Issue.</span></span>  
  
##  <a name="availability-group-details"></a><a name="AvGroupDetails"></a><span data-ttu-id="30ffc-149">可用性组详细信息</span><span class="sxs-lookup"><span data-stu-id="30ffc-149">Availability Group Details</span></span>  
 <span data-ttu-id="30ffc-150">将为您可以从摘要屏幕中选择的可用性组显示以下详细信息：</span><span class="sxs-lookup"><span data-stu-id="30ffc-150">The following detail information is displayed for the availability group that you select from the summary screen:</span></span>  
  
 <span data-ttu-id="30ffc-151">**可用性组状态**</span><span class="sxs-lookup"><span data-stu-id="30ffc-151">**Availability group state**</span></span>  
 <span data-ttu-id="30ffc-152">显示可用性组的运行状况。</span><span class="sxs-lookup"><span data-stu-id="30ffc-152">Displays the state of health for the availability group.</span></span>  
  
 <span data-ttu-id="30ffc-153">**Primary instance**</span><span class="sxs-lookup"><span data-stu-id="30ffc-153">**Primary instance**</span></span>  
 <span data-ttu-id="30ffc-154">正在承载可用性组的主副本的服务器实例的名称。</span><span class="sxs-lookup"><span data-stu-id="30ffc-154">Name of the server instance that is hosting the primary replica of the availability group.</span></span>  
  
 <span data-ttu-id="30ffc-155">**Failover mode**</span><span class="sxs-lookup"><span data-stu-id="30ffc-155">**Failover mode**</span></span>  
 <span data-ttu-id="30ffc-156">显示为副本配置的故障转移模式。</span><span class="sxs-lookup"><span data-stu-id="30ffc-156">Displays the failover mode for which the replica is configured.</span></span> <span data-ttu-id="30ffc-157">可能的故障转移模式值包括：</span><span class="sxs-lookup"><span data-stu-id="30ffc-157">The possible failover mode values are:</span></span>  
  
-   <span data-ttu-id="30ffc-158">**自动**。</span><span class="sxs-lookup"><span data-stu-id="30ffc-158">**Automatic**.</span></span> <span data-ttu-id="30ffc-159">指示一个或多个副本处于自动故障转移模式。</span><span class="sxs-lookup"><span data-stu-id="30ffc-159">Indicates that one or more replicas is in automatic-failover mode.</span></span>  
  
-   <span data-ttu-id="30ffc-160">**手动**。</span><span class="sxs-lookup"><span data-stu-id="30ffc-160">**Manual**.</span></span> <span data-ttu-id="30ffc-161">指示没有副本处于自动故障转移模式。</span><span class="sxs-lookup"><span data-stu-id="30ffc-161">Indicates that no replica is automatic-failover mode.</span></span>  
  
 <span data-ttu-id="30ffc-162">**群集状态**</span><span class="sxs-lookup"><span data-stu-id="30ffc-162">**Cluster state**</span></span>  
 <span data-ttu-id="30ffc-163">群集的名称和状态，所连接的服务器实例和可用性组都是该群集的成员节点。</span><span class="sxs-lookup"><span data-stu-id="30ffc-163">Name and state of the cluster where the instance of the connected server and the availability group is a member node.</span></span>  
  
##  <a name="availability-replica-details"></a><a name="AvReplicaDetails"></a> <span data-ttu-id="30ffc-164">可用性副本详细信息</span><span class="sxs-lookup"><span data-stu-id="30ffc-164">Availability Replica Details</span></span>  
 <span data-ttu-id="30ffc-165">**“可用性副本”** 窗格显示以下列：</span><span class="sxs-lookup"><span data-stu-id="30ffc-165">The **Availability replica** pane displays the following columns:</span></span>  
  
 <span data-ttu-id="30ffc-166">**名称**</span><span class="sxs-lookup"><span data-stu-id="30ffc-166">**Name**</span></span>  
 <span data-ttu-id="30ffc-167">承载可用性副本的服务器实例的名称。</span><span class="sxs-lookup"><span data-stu-id="30ffc-167">The name of the server instance that hosts the availability replica.</span></span> <span data-ttu-id="30ffc-168">默认情况下显示此列。</span><span class="sxs-lookup"><span data-stu-id="30ffc-168">This column is shown by default.</span></span>  
  
 <span data-ttu-id="30ffc-169">**角色**</span><span class="sxs-lookup"><span data-stu-id="30ffc-169">**Role**</span></span>  
 <span data-ttu-id="30ffc-170">指示可用性副本的当前角色，即“主”或“辅助”。</span><span class="sxs-lookup"><span data-stu-id="30ffc-170">Indicates the current role of the availability replica, either **Primary** or **Secondary**.</span></span> <span data-ttu-id="30ffc-171">有关 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 角色的详细信息，请参阅 [AlwaysOn 可用性组概述 (SQL Server)](overview-of-always-on-availability-groups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="30ffc-171">For information about [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] roles, see [Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md).</span></span> <span data-ttu-id="30ffc-172">默认情况下显示此列。</span><span class="sxs-lookup"><span data-stu-id="30ffc-172">This column is shown by default.</span></span>  
  
 <span data-ttu-id="30ffc-173">**故障转移模式**</span><span class="sxs-lookup"><span data-stu-id="30ffc-173">**Failover Mode**</span></span>  
 <span data-ttu-id="30ffc-174">显示为副本配置的故障转移模式。</span><span class="sxs-lookup"><span data-stu-id="30ffc-174">Displays the failover mode for which the replica is configured.</span></span> <span data-ttu-id="30ffc-175">可能的故障转移模式值包括：</span><span class="sxs-lookup"><span data-stu-id="30ffc-175">The possible failover mode values are:</span></span>  
  
-   <span data-ttu-id="30ffc-176">**自动**。</span><span class="sxs-lookup"><span data-stu-id="30ffc-176">**Automatic**.</span></span> <span data-ttu-id="30ffc-177">指示一个或多个副本处于自动故障转移模式。</span><span class="sxs-lookup"><span data-stu-id="30ffc-177">Indicates that one or more replicas is in automatic-failover mode.</span></span>  
  
-   <span data-ttu-id="30ffc-178">**手动**。</span><span class="sxs-lookup"><span data-stu-id="30ffc-178">**Manual**.</span></span> <span data-ttu-id="30ffc-179">指示没有副本处于自动故障转移模式。</span><span class="sxs-lookup"><span data-stu-id="30ffc-179">Indicates that no replica is automatic-failover mode.</span></span>  
  
 <span data-ttu-id="30ffc-180">**同步状态**</span><span class="sxs-lookup"><span data-stu-id="30ffc-180">**Synchronization State**</span></span>  
 <span data-ttu-id="30ffc-181">指示辅助副本当前是否与主副本同步。</span><span class="sxs-lookup"><span data-stu-id="30ffc-181">Indicates whether a secondary replica is currently synchronized with primary replica.</span></span> <span data-ttu-id="30ffc-182">默认情况下显示此列。</span><span class="sxs-lookup"><span data-stu-id="30ffc-182">This column is shown by default.</span></span> <span data-ttu-id="30ffc-183">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="30ffc-183">The possible values are:</span></span>  
  
-   <span data-ttu-id="30ffc-184">**未同步**。</span><span class="sxs-lookup"><span data-stu-id="30ffc-184">**Not Synchronized**.</span></span> <span data-ttu-id="30ffc-185">副本中的一个或多个数据库未同步或尚未联接到可用性组。</span><span class="sxs-lookup"><span data-stu-id="30ffc-185">One or more databases in the replica are not synchronized or have not yet been joined to the availability group.</span></span>  
  
-   <span data-ttu-id="30ffc-186">**正在同步**。</span><span class="sxs-lookup"><span data-stu-id="30ffc-186">**Synchronizing**.</span></span> <span data-ttu-id="30ffc-187">正在同步副本中的一个或多个数据库。</span><span class="sxs-lookup"><span data-stu-id="30ffc-187">One or more databases in the replica are being synchronized.</span></span>  
  
-   <span data-ttu-id="30ffc-188">已**同步**。</span><span class="sxs-lookup"><span data-stu-id="30ffc-188">**Synchronized**.</span></span> <span data-ttu-id="30ffc-189">辅助副本中的所有数据库均与当前主副本（如果有）或上一个主副本上的相应主数据库同步。</span><span class="sxs-lookup"><span data-stu-id="30ffc-189">All databases in the secondary replica are synchronized with the corresponding primary databases on the current primary replica, if any, or on the last primary replica.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="30ffc-190">在性能模式中，数据库从不处于“已同步”状态。</span><span class="sxs-lookup"><span data-stu-id="30ffc-190">In performance mode, the database is never in the synchronized state.</span></span>  
  
-   <span data-ttu-id="30ffc-191">**NULL**。</span><span class="sxs-lookup"><span data-stu-id="30ffc-191">**NULL**.</span></span> <span data-ttu-id="30ffc-192">未知状态。</span><span class="sxs-lookup"><span data-stu-id="30ffc-192">Unknown state.</span></span> <span data-ttu-id="30ffc-193">当本地服务器实例无法与 WSFC 故障转移群集通信（即本地节点不是 WSFC 仲裁的一部分）时，出现此值。</span><span class="sxs-lookup"><span data-stu-id="30ffc-193">This value occurs when the local server instance cannot communicate with the WSFC failover cluster (that is the local node is not part of WSFC quorum).</span></span>  
  
 <span data-ttu-id="30ffc-194">**问题**</span><span class="sxs-lookup"><span data-stu-id="30ffc-194">**Issues**</span></span>  
 <span data-ttu-id="30ffc-195">列出问题名称。</span><span class="sxs-lookup"><span data-stu-id="30ffc-195">Lists the issue name.</span></span> <span data-ttu-id="30ffc-196">默认情况下显示此值。</span><span class="sxs-lookup"><span data-stu-id="30ffc-196">This value is shown by default.</span></span> <span data-ttu-id="30ffc-197">有关所有 AlwaysOn 策略问题的列表，请参阅[AlwaysOn 可用性组 (SQL Server) 的操作问题的 AlwaysOn 策略](always-on-policies-for-operational-issues-always-on-availability.md)。</span><span class="sxs-lookup"><span data-stu-id="30ffc-197">For a list of all the AlwaysOn policy issues, see [AlwaysOn Policies for Operational Issues with AlwaysOn Availability Groups (SQL Server)](always-on-policies-for-operational-issues-always-on-availability.md).</span></span>  
  
 <span data-ttu-id="30ffc-198">**可用性模式**</span><span class="sxs-lookup"><span data-stu-id="30ffc-198">**Availability Mode**</span></span>  
 <span data-ttu-id="30ffc-199">指示用户为每个可用性副本分别设置的副本属性。</span><span class="sxs-lookup"><span data-stu-id="30ffc-199">Indicates the replica property that you set separately for each availability replica.</span></span> <span data-ttu-id="30ffc-200">默认情况下隐藏此值。</span><span class="sxs-lookup"><span data-stu-id="30ffc-200">This value is hidden by default.</span></span> <span data-ttu-id="30ffc-201">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="30ffc-201">The possible values are:</span></span>  
  
-   <span data-ttu-id="30ffc-202">**异步**。</span><span class="sxs-lookup"><span data-stu-id="30ffc-202">**Asynchronous**.</span></span> <span data-ttu-id="30ffc-203">辅助副本从不与主副本同步。</span><span class="sxs-lookup"><span data-stu-id="30ffc-203">The secondary replica never becomes synchronized with the primary replica.</span></span>  
  
-   <span data-ttu-id="30ffc-204">**同步**。</span><span class="sxs-lookup"><span data-stu-id="30ffc-204">**Synchronous**.</span></span> <span data-ttu-id="30ffc-205">在追赶主数据库以保持与其同步时，辅助数据库将进入此状态，而且只要该数据库一直在同步数据，就会保持追赶状态。</span><span class="sxs-lookup"><span data-stu-id="30ffc-205">When catching up to the primary database, a secondary database enters this state, and it remains caught up as long as data synchronization continues for the database.</span></span>  
  
 <span data-ttu-id="30ffc-206">**主连接模式**</span><span class="sxs-lookup"><span data-stu-id="30ffc-206">**Primary Connection Mode**</span></span>  
 <span data-ttu-id="30ffc-207">指示用于连接主副本的模式。</span><span class="sxs-lookup"><span data-stu-id="30ffc-207">Indicates the mode that is used to connect to the primary replica.</span></span>  <span data-ttu-id="30ffc-208">默认情况下隐藏此值。</span><span class="sxs-lookup"><span data-stu-id="30ffc-208">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="30ffc-209">**辅助连接模式**</span><span class="sxs-lookup"><span data-stu-id="30ffc-209">**Secondary Connection Mode**</span></span>  
 <span data-ttu-id="30ffc-210">指示用于连接辅助副本的模式。</span><span class="sxs-lookup"><span data-stu-id="30ffc-210">Indicates the mode that is used to connect to the secondary replica.</span></span>  <span data-ttu-id="30ffc-211">默认情况下隐藏此值。</span><span class="sxs-lookup"><span data-stu-id="30ffc-211">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="30ffc-212">**连接状态**</span><span class="sxs-lookup"><span data-stu-id="30ffc-212">**Connection State**</span></span>  
 <span data-ttu-id="30ffc-213">指示辅助副本当前是否连接到主副本。</span><span class="sxs-lookup"><span data-stu-id="30ffc-213">Indicates whether a secondary replica is currently connected to the primary replica.</span></span> <span data-ttu-id="30ffc-214">默认情况下隐藏此列。</span><span class="sxs-lookup"><span data-stu-id="30ffc-214">This column is hidden by default.</span></span> <span data-ttu-id="30ffc-215">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="30ffc-215">The possible values are:</span></span>  
  
-   <span data-ttu-id="30ffc-216">**断开连接**。</span><span class="sxs-lookup"><span data-stu-id="30ffc-216">**Disconnected**.</span></span> <span data-ttu-id="30ffc-217">对于远程可用性副本，指示它与本地可用性副本已断开连接。</span><span class="sxs-lookup"><span data-stu-id="30ffc-217">For a remote availability replica, indicates that it is disconnected from the local availability replica.</span></span> <span data-ttu-id="30ffc-218">本地副本对于“已断开连接”状态的响应取决于它的角色，如下所示：</span><span class="sxs-lookup"><span data-stu-id="30ffc-218">The response of the local replica to the Disconnected state depends on its role, as follows:</span></span>  
  
    -   <span data-ttu-id="30ffc-219">在主副本上，如果辅助副本已断开连接，辅助数据库将在主副本上标记为 **“未同步”** ，主副本等待辅助副本重新连接。</span><span class="sxs-lookup"><span data-stu-id="30ffc-219">On the primary replica, if a secondary replica is disconnected, the secondary databases are marked as **Not Synchronized** on the primary replica, and the primary replica waits for the secondary to reconnect.</span></span>  
  
    -   <span data-ttu-id="30ffc-220">在辅助副本上，一旦检测到其未连接，辅助副本会尝试重新连接主副本。</span><span class="sxs-lookup"><span data-stu-id="30ffc-220">On the secondary replica, upon detecting that it is disconnected, the secondary replica attempts to reconnect to the primary replica.</span></span>  
  
-   <span data-ttu-id="30ffc-221">**已连接**。</span><span class="sxs-lookup"><span data-stu-id="30ffc-221">**Connected**.</span></span> <span data-ttu-id="30ffc-222">远程可用性副本当前连接到本地副本。</span><span class="sxs-lookup"><span data-stu-id="30ffc-222">A remote availability replica that is currently connected to the local replica.</span></span>  
  
 <span data-ttu-id="30ffc-223">**操作状态**</span><span class="sxs-lookup"><span data-stu-id="30ffc-223">**Operational State**</span></span>  
 <span data-ttu-id="30ffc-224">指示辅助副本的当前操作状态。</span><span class="sxs-lookup"><span data-stu-id="30ffc-224">Indicates the current operational state of the secondary replica.</span></span> <span data-ttu-id="30ffc-225">默认情况下隐藏此值。</span><span class="sxs-lookup"><span data-stu-id="30ffc-225">This value is hidden by default.</span></span> <span data-ttu-id="30ffc-226">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="30ffc-226">The possible values are:</span></span>  
  
 <span data-ttu-id="30ffc-227">**0**。挂起故障转移</span><span class="sxs-lookup"><span data-stu-id="30ffc-227">**0**. Pending failover</span></span>  
  
 <span data-ttu-id="30ffc-228">**1**。挂起</span><span class="sxs-lookup"><span data-stu-id="30ffc-228">**1**. Pending</span></span>  
  
 <span data-ttu-id="30ffc-229">**2**。联机</span><span class="sxs-lookup"><span data-stu-id="30ffc-229">**2**. Online</span></span>  
  
 <span data-ttu-id="30ffc-230">**3**。Offline</span><span class="sxs-lookup"><span data-stu-id="30ffc-230">**3**. Offline</span></span>  
  
 <span data-ttu-id="30ffc-231">**4**。失败</span><span class="sxs-lookup"><span data-stu-id="30ffc-231">**4**. Failed</span></span>  
  
 <span data-ttu-id="30ffc-232">**5**。失败，无仲裁</span><span class="sxs-lookup"><span data-stu-id="30ffc-232">**5**. Failed, no quorum</span></span>  
  
 <span data-ttu-id="30ffc-233">**NULL**。</span><span class="sxs-lookup"><span data-stu-id="30ffc-233">**NULL**.</span></span> <span data-ttu-id="30ffc-234">副本不在本地</span><span class="sxs-lookup"><span data-stu-id="30ffc-234">Replica is not local</span></span>  
  
 <span data-ttu-id="30ffc-235">**上一个连接错误编号**</span><span class="sxs-lookup"><span data-stu-id="30ffc-235">**Last Connection Error No.**</span></span>  
 <span data-ttu-id="30ffc-236">上一个连接错误的编号。</span><span class="sxs-lookup"><span data-stu-id="30ffc-236">Number of the last connection error.</span></span>  <span data-ttu-id="30ffc-237">默认情况下隐藏此值。</span><span class="sxs-lookup"><span data-stu-id="30ffc-237">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="30ffc-238">**上一个连接错误说明**</span><span class="sxs-lookup"><span data-stu-id="30ffc-238">**Last Connection Error Description**</span></span>  
 <span data-ttu-id="30ffc-239">上一个连接错误的说明。</span><span class="sxs-lookup"><span data-stu-id="30ffc-239">Description of the last connection error.</span></span>  <span data-ttu-id="30ffc-240">默认情况下隐藏此值。</span><span class="sxs-lookup"><span data-stu-id="30ffc-240">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="30ffc-241">**上一个连接错误时间戳**</span><span class="sxs-lookup"><span data-stu-id="30ffc-241">**Last Connection Error Timestamp**</span></span>  
 <span data-ttu-id="30ffc-242">上一个连接错误的时间戳。</span><span class="sxs-lookup"><span data-stu-id="30ffc-242">Timestamp of the last connection error.</span></span> <span data-ttu-id="30ffc-243">默认情况下隐藏此值。</span><span class="sxs-lookup"><span data-stu-id="30ffc-243">This value is hidden by default.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="30ffc-244">有关可用性副本的性能计数器的信息，请参阅 [SQL Server，可用性副本](../../../relational-databases/performance-monitor/sql-server-availability-replica.md)。</span><span class="sxs-lookup"><span data-stu-id="30ffc-244">For information about performance counters for availability replicas, see [SQL Server, Availability Replica](../../../relational-databases/performance-monitor/sql-server-availability-replica.md).</span></span>  
  
##  <a name="to-group-availability-group-information"></a><a name="AvDbDetails"></a><span data-ttu-id="30ffc-245">对可用性组信息分组</span><span class="sxs-lookup"><span data-stu-id="30ffc-245">To Group Availability Group Information</span></span>  
 <span data-ttu-id="30ffc-246">若要对信息进行分组，请单击 **“分组依据”**，并选择下列选项之一：</span><span class="sxs-lookup"><span data-stu-id="30ffc-246">To group the information, click **Group by**, and select one of the following:</span></span>  
  
-   <span data-ttu-id="30ffc-247">**可用性副本**</span><span class="sxs-lookup"><span data-stu-id="30ffc-247">**Availability replicas**</span></span>  
  
-   <span data-ttu-id="30ffc-248">**可用性数据库**</span><span class="sxs-lookup"><span data-stu-id="30ffc-248">**Availability databases**</span></span>  
  
-   <span data-ttu-id="30ffc-249">**同步状态**</span><span class="sxs-lookup"><span data-stu-id="30ffc-249">**Synchronization state**</span></span>  
  
-   <span data-ttu-id="30ffc-250">**故障转移就绪**</span><span class="sxs-lookup"><span data-stu-id="30ffc-250">**Failover readiness**</span></span>  
  
-   <span data-ttu-id="30ffc-251">**问题**</span><span class="sxs-lookup"><span data-stu-id="30ffc-251">**Issues**</span></span>  
  
 <span data-ttu-id="30ffc-252">显示分组依据信息的窗格显示以下列：</span><span class="sxs-lookup"><span data-stu-id="30ffc-252">The pane that displays the grouped information displays the following columns:</span></span>  
  
 <span data-ttu-id="30ffc-253">**名称**</span><span class="sxs-lookup"><span data-stu-id="30ffc-253">**Name**</span></span>  
 <span data-ttu-id="30ffc-254">可用性数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="30ffc-254">The name of the availability database.</span></span> <span data-ttu-id="30ffc-255">默认情况下显示此值。</span><span class="sxs-lookup"><span data-stu-id="30ffc-255">This value is shown by default.</span></span>  
  
 <span data-ttu-id="30ffc-256">**副本**</span><span class="sxs-lookup"><span data-stu-id="30ffc-256">**Replica**</span></span>  
 <span data-ttu-id="30ffc-257">承载可用性副本的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例的名称。</span><span class="sxs-lookup"><span data-stu-id="30ffc-257">The name of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that hosts the availability replica.</span></span> <span data-ttu-id="30ffc-258">默认情况下显示此值。</span><span class="sxs-lookup"><span data-stu-id="30ffc-258">This value is shown by default.</span></span>  
  
 <span data-ttu-id="30ffc-259">**同步状态**</span><span class="sxs-lookup"><span data-stu-id="30ffc-259">**Synchronization State**</span></span>  
 <span data-ttu-id="30ffc-260">指示可用性数据库当前是否与主副本同步。</span><span class="sxs-lookup"><span data-stu-id="30ffc-260">Indicates whether the availability database is currently synchronized with primary replica.</span></span> <span data-ttu-id="30ffc-261">默认情况下显示此值。</span><span class="sxs-lookup"><span data-stu-id="30ffc-261">This value is shown by default.</span></span> <span data-ttu-id="30ffc-262">可能的同步状态如下：</span><span class="sxs-lookup"><span data-stu-id="30ffc-262">The possible synchronization states are:</span></span>  
  
-   <span data-ttu-id="30ffc-263">**未同步**。</span><span class="sxs-lookup"><span data-stu-id="30ffc-263">**Not synchronizing**.</span></span>  
  
    -   <span data-ttu-id="30ffc-264">对于主角色，指示该数据库未做好将其事务日志与相应的辅助数据库同步的准备。</span><span class="sxs-lookup"><span data-stu-id="30ffc-264">For the primary role, indicates that the database is not ready to synchronize its transaction log with the corresponding secondary databases.</span></span>  
  
    -   <span data-ttu-id="30ffc-265">对于辅助数据库，指示数据库由于连接问题而未开始日志同步，正被挂起，或者在启动或角色切换过程中正在转换状态。</span><span class="sxs-lookup"><span data-stu-id="30ffc-265">For a secondary database, indicates that the database has not started log synchronization because of a connection issue, is being suspended, or is going through transition states during startup or a role switch.</span></span>  
  
-   <span data-ttu-id="30ffc-266">**正在同步**。</span><span class="sxs-lookup"><span data-stu-id="30ffc-266">**Synchronizing**.</span></span>  
  
     <span data-ttu-id="30ffc-267">在主副本上：</span><span class="sxs-lookup"><span data-stu-id="30ffc-267">On a primary replica:</span></span>  
  
    -   <span data-ttu-id="30ffc-268">对于主数据库，指示此数据库已做好接受来自辅助数据库的扫描请求的准备。</span><span class="sxs-lookup"><span data-stu-id="30ffc-268">For a primary database, indicates that this database is ready to accept a scan request from a secondary database.</span></span>  
  
    -   <span data-ttu-id="30ffc-269">在辅助副本上，指示存在为该辅助数据库进行的处于活动状态的数据移动。</span><span class="sxs-lookup"><span data-stu-id="30ffc-269">On a secondary replica, indicates that there is active data movement going on for that secondary database.</span></span>  
  
     <span data-ttu-id="30ffc-270">在辅助副本上，指示存在为该副本进行的处于活动状态的数据移动。</span><span class="sxs-lookup"><span data-stu-id="30ffc-270">On a secondary replica, indicates that there is active data movement going on for that replica.</span></span>  
  
-   <span data-ttu-id="30ffc-271">已**同步**。</span><span class="sxs-lookup"><span data-stu-id="30ffc-271">**Synchronized**.</span></span>  
  
     <span data-ttu-id="30ffc-272">对于主数据库，指示至少同步了一个辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="30ffc-272">For a primary database, indicates that at least one secondary database is synchronized.</span></span>  
  
     <span data-ttu-id="30ffc-273">对于辅助数据库，指示该数据库与相应的主数据库保持同步。</span><span class="sxs-lookup"><span data-stu-id="30ffc-273">For a secondary database, indicates that the database is synchronized with the corresponding primary database.</span></span>  
  
-   <span data-ttu-id="30ffc-274">**正在恢复**。</span><span class="sxs-lookup"><span data-stu-id="30ffc-274">**Reverting**.</span></span>  
  
     <span data-ttu-id="30ffc-275">指示撤消进程中辅助数据库主动从主数据库获取页时的阶段。</span><span class="sxs-lookup"><span data-stu-id="30ffc-275">Indicates the phase in the undo process when a secondary database is actively getting pages from the primary database.</span></span>  
  
    > [!CAUTION]  
    >  <span data-ttu-id="30ffc-276">当数据库处于 REVERTING 状态时，强制故障转移到辅助副本可能将使数据库处于不能启动的状态。</span><span class="sxs-lookup"><span data-stu-id="30ffc-276">When a database is in the REVERTING state, forcing failover to the secondary replica can leave that database in a state in which it cannot be started.</span></span>  
  
-   <span data-ttu-id="30ffc-277">**正在初始化**。</span><span class="sxs-lookup"><span data-stu-id="30ffc-277">**Initializing**.</span></span>  
  
     <span data-ttu-id="30ffc-278">指示在正在辅助副本上传送和强制写入辅助数据库跟上撤消 LSN 所需的事务日志时的撤消阶段。</span><span class="sxs-lookup"><span data-stu-id="30ffc-278">Indicates the phase of undo when the transaction log required for a secondary database to catch up to the undo LSN is being shipped and hardened on a secondary replica.</span></span>  
  
    > [!CAUTION]  
    >  <span data-ttu-id="30ffc-279">当数据库处于 INITIALIZING 状态时，强制故障转移到辅助副本将使数据库始终处于不能启动的状态。</span><span class="sxs-lookup"><span data-stu-id="30ffc-279">When a database is in the INITIALIZING state, forcing failover to the secondary replica will always leave that database in a state in which it cannot be started.</span></span>  
  
 <span data-ttu-id="30ffc-280">**“故障转移就绪”**</span><span class="sxs-lookup"><span data-stu-id="30ffc-280">**Failover Readiness**</span></span>  
 <span data-ttu-id="30ffc-281">指示哪些可用性副本可以进行故障转移（有/无数据丢失）。</span><span class="sxs-lookup"><span data-stu-id="30ffc-281">Indicates which availability replica can be failed over with or without potential data loss.</span></span> <span data-ttu-id="30ffc-282">默认情况下显示此列。</span><span class="sxs-lookup"><span data-stu-id="30ffc-282">This column is shown by default.</span></span> <span data-ttu-id="30ffc-283">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="30ffc-283">The possible values are:</span></span>  
  
-   <span data-ttu-id="30ffc-284">**数据丢失**</span><span class="sxs-lookup"><span data-stu-id="30ffc-284">**Data Loss**</span></span>  
  
-   <span data-ttu-id="30ffc-285">**无数据丢失**</span><span class="sxs-lookup"><span data-stu-id="30ffc-285">**No Data Loss**</span></span>  
  
 <span data-ttu-id="30ffc-286">**问题**</span><span class="sxs-lookup"><span data-stu-id="30ffc-286">**Issues**</span></span>  
 <span data-ttu-id="30ffc-287">列出问题名称。</span><span class="sxs-lookup"><span data-stu-id="30ffc-287">Lists the issue name.</span></span> <span data-ttu-id="30ffc-288">默认情况下显示此列。</span><span class="sxs-lookup"><span data-stu-id="30ffc-288">This column is shown by default.</span></span> <span data-ttu-id="30ffc-289">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="30ffc-289">The possible values are:</span></span>  
  
-   <span data-ttu-id="30ffc-290">**警告**。</span><span class="sxs-lookup"><span data-stu-id="30ffc-290">**Warnings**.</span></span> <span data-ttu-id="30ffc-291">单击此选项可显示阈值和警告问题。</span><span class="sxs-lookup"><span data-stu-id="30ffc-291">Click to display the thresholds and warnings issues.</span></span>  
  
-   <span data-ttu-id="30ffc-292">**严重**。</span><span class="sxs-lookup"><span data-stu-id="30ffc-292">**Critical**.</span></span> <span data-ttu-id="30ffc-293">单击此选项可显示严重问题。</span><span class="sxs-lookup"><span data-stu-id="30ffc-293">Click to display the critical issues.</span></span>  
  
 <span data-ttu-id="30ffc-294">有关所有 AlwaysOn 策略问题的列表，请参阅[AlwaysOn 可用性组 (SQL Server) 的操作问题的 AlwaysOn 策略](always-on-policies-for-operational-issues-always-on-availability.md)。</span><span class="sxs-lookup"><span data-stu-id="30ffc-294">For a list of all the AlwaysOn policy issues, see [AlwaysOn Policies for Operational Issues with AlwaysOn Availability Groups (SQL Server)](always-on-policies-for-operational-issues-always-on-availability.md).</span></span>  
  
 <span data-ttu-id="30ffc-295">**已挂起**</span><span class="sxs-lookup"><span data-stu-id="30ffc-295">**Suspended**</span></span>  
 <span data-ttu-id="30ffc-296">指示数据库“已挂起”  还是“已恢复”  。</span><span class="sxs-lookup"><span data-stu-id="30ffc-296">Indicates whether the database is **Suspended** or has been **Resumed**.</span></span> <span data-ttu-id="30ffc-297">默认情况下隐藏此值。</span><span class="sxs-lookup"><span data-stu-id="30ffc-297">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="30ffc-298">**挂起原因**</span><span class="sxs-lookup"><span data-stu-id="30ffc-298">**Suspend Reason**</span></span>  
 <span data-ttu-id="30ffc-299">指示已挂起状态的原因。</span><span class="sxs-lookup"><span data-stu-id="30ffc-299">Indicates the reason for the suspended state.</span></span> <span data-ttu-id="30ffc-300">默认情况下隐藏此值。</span><span class="sxs-lookup"><span data-stu-id="30ffc-300">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="30ffc-301">**估计数据丢失（秒）**</span><span class="sxs-lookup"><span data-stu-id="30ffc-301">**Estimate Data Loss (seconds)**</span></span>  
 <span data-ttu-id="30ffc-302">指示主副本和辅助副本中最后一个事务日志记录的时间差异。</span><span class="sxs-lookup"><span data-stu-id="30ffc-302">Indicates the time difference of the last transaction log record in the primary replica and secondary replica.</span></span> <span data-ttu-id="30ffc-303">如果主副本失败，则丢失该时间窗口内的所有事务日志记录。</span><span class="sxs-lookup"><span data-stu-id="30ffc-303">If the primary replica fails, all transaction log records within the time window will be lost.</span></span> <span data-ttu-id="30ffc-304">默认情况下隐藏此值。</span><span class="sxs-lookup"><span data-stu-id="30ffc-304">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="30ffc-305">**估计的恢复时间（秒）**</span><span class="sxs-lookup"><span data-stu-id="30ffc-305">**Estimated Recovery Time (seconds)**</span></span>  
 <span data-ttu-id="30ffc-306">指示重做追赶时间所需的时间（秒）。</span><span class="sxs-lookup"><span data-stu-id="30ffc-306">Indicates the time in seconds it takes to redo the catch-up time.</span></span> <span data-ttu-id="30ffc-307">追赶时间  是次要副本要与主要副本保持同步所需的时间。</span><span class="sxs-lookup"><span data-stu-id="30ffc-307">The *catch-up time* is the time it will take for the secondary replica to catch up with the primary replica.</span></span> <span data-ttu-id="30ffc-308">默认情况下隐藏此值。</span><span class="sxs-lookup"><span data-stu-id="30ffc-308">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="30ffc-309">**同步性能（秒）**</span><span class="sxs-lookup"><span data-stu-id="30ffc-309">**Synchronization Performance (seconds)**</span></span>  
 <span data-ttu-id="30ffc-310">指示主副本与辅助副本之间的同步所需的时间（秒）。</span><span class="sxs-lookup"><span data-stu-id="30ffc-310">Indicates the time in seconds it takes to synchronize between the primary and secondary replicas.</span></span> <span data-ttu-id="30ffc-311">默认情况下隐藏此值。</span><span class="sxs-lookup"><span data-stu-id="30ffc-311">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="30ffc-312">**日志发送队列大小 (KB)**</span><span class="sxs-lookup"><span data-stu-id="30ffc-312">**Log Send Queue Size (KB)**</span></span>  
 <span data-ttu-id="30ffc-313">指示主数据库的日志文件中尚未发送到辅助副本的日志记录量。</span><span class="sxs-lookup"><span data-stu-id="30ffc-313">Indicates the amount of log records in the log files of the primary database that have not been sent to the secondary replica.</span></span> <span data-ttu-id="30ffc-314">默认情况下隐藏此值。</span><span class="sxs-lookup"><span data-stu-id="30ffc-314">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="30ffc-315">**日志发送速率（KB/秒）**</span><span class="sxs-lookup"><span data-stu-id="30ffc-315">**Log Send Rate (KB/sec)**</span></span>  
 <span data-ttu-id="30ffc-316">指示日志记录发送到辅助副本的速率（KB/秒）。默认情况下隐藏此值。</span><span class="sxs-lookup"><span data-stu-id="30ffc-316">Indicates the rate in KB per second at which log records are being sent to the secondary replica This value is hidden by default.</span></span>  
  
 <span data-ttu-id="30ffc-317">**重做队列大小 (KB)**</span><span class="sxs-lookup"><span data-stu-id="30ffc-317">**Redo Queue Size (KB)**</span></span>  
 <span data-ttu-id="30ffc-318">指示辅助副本的日志文件中尚未重做的日志记录量。</span><span class="sxs-lookup"><span data-stu-id="30ffc-318">Indicates the amount of log records in the log files of the secondary replica that have not yet been redone.</span></span> <span data-ttu-id="30ffc-319">默认情况下隐藏此值。</span><span class="sxs-lookup"><span data-stu-id="30ffc-319">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="30ffc-320">**重做速率（KB/秒）**</span><span class="sxs-lookup"><span data-stu-id="30ffc-320">**Redo Rate (KB/sec)**</span></span>  
 <span data-ttu-id="30ffc-321">指示日志记录重做的速率（KB/秒）。</span><span class="sxs-lookup"><span data-stu-id="30ffc-321">Indicates the rate in KB per second at which the log records are being redone.</span></span> <span data-ttu-id="30ffc-322">默认情况下隐藏此值。</span><span class="sxs-lookup"><span data-stu-id="30ffc-322">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="30ffc-323">**FileStream 发送速率（KB/秒）**</span><span class="sxs-lookup"><span data-stu-id="30ffc-323">**FileStream Send Rate (KB/sec)**</span></span>  
 <span data-ttu-id="30ffc-324">指示将事务发送到副本的 FileStream 速率（KB/秒）。</span><span class="sxs-lookup"><span data-stu-id="30ffc-324">Indicates the rate of the FileStream in KB per second at which transactions are being sent to the replica.</span></span> <span data-ttu-id="30ffc-325">默认情况下隐藏此值。</span><span class="sxs-lookup"><span data-stu-id="30ffc-325">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="30ffc-326">**日志 LSN 的结尾**</span><span class="sxs-lookup"><span data-stu-id="30ffc-326">**End of Log LSN**</span></span>  
 <span data-ttu-id="30ffc-327">指示与主副本和辅助副本上日志缓存中的最后一个日志记录相对应的实际日志序列号 (LSN)。</span><span class="sxs-lookup"><span data-stu-id="30ffc-327">Indicates the actual log sequence number (LSN) that corresponds to the last log record in the log cache on the primary and secondary replicas.</span></span> <span data-ttu-id="30ffc-328">默认情况下隐藏此值。</span><span class="sxs-lookup"><span data-stu-id="30ffc-328">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="30ffc-329">**恢复 LSN**</span><span class="sxs-lookup"><span data-stu-id="30ffc-329">**Recovery LSN**</span></span>  
 <span data-ttu-id="30ffc-330">指示在主副本上，在主副本上恢复或故障转移之后、在副本写入任何新日志记录之前事务日志的结尾。</span><span class="sxs-lookup"><span data-stu-id="30ffc-330">Indicates the end of the transaction log before the replica writes any new log records after recovery or failover on the primary replica.</span></span> <span data-ttu-id="30ffc-331">默认情况下隐藏此值。</span><span class="sxs-lookup"><span data-stu-id="30ffc-331">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="30ffc-332">**截断 LSN**</span><span class="sxs-lookup"><span data-stu-id="30ffc-332">**Truncation LSN**</span></span>  
 <span data-ttu-id="30ffc-333">指示主副本的最小日志截断值。</span><span class="sxs-lookup"><span data-stu-id="30ffc-333">Indicates the minimum log truncation value for the primary replica.</span></span> <span data-ttu-id="30ffc-334">默认情况下隐藏此值。</span><span class="sxs-lookup"><span data-stu-id="30ffc-334">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="30ffc-335">**上次提交 LSN**</span><span class="sxs-lookup"><span data-stu-id="30ffc-335">**Last Commit LSN**</span></span>  
 <span data-ttu-id="30ffc-336">指示与事务日志中的最后提交的记录相对应的实际 LSN。</span><span class="sxs-lookup"><span data-stu-id="30ffc-336">Indicates the actual LSN corresponding to the last commit record in the transaction log.</span></span> <span data-ttu-id="30ffc-337">默认情况下隐藏此值。</span><span class="sxs-lookup"><span data-stu-id="30ffc-337">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="30ffc-338">**上次提交时间**</span><span class="sxs-lookup"><span data-stu-id="30ffc-338">**Last Commit Time**</span></span>  
 <span data-ttu-id="30ffc-339">指示与最后一个提交记录对应的时间。</span><span class="sxs-lookup"><span data-stu-id="30ffc-339">Indicates the time corresponding to the last commit record.</span></span> <span data-ttu-id="30ffc-340">默认情况下隐藏此值。</span><span class="sxs-lookup"><span data-stu-id="30ffc-340">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="30ffc-341">**上次发送的 LSN**</span><span class="sxs-lookup"><span data-stu-id="30ffc-341">**Last Sent LSN**</span></span>  
 <span data-ttu-id="30ffc-342">指示一个点，在该点之前，所有日志块都已由主副本发送。</span><span class="sxs-lookup"><span data-stu-id="30ffc-342">Indicates the point up to which all log blocks have been sent by the primary replica.</span></span> <span data-ttu-id="30ffc-343">默认情况下隐藏此值。</span><span class="sxs-lookup"><span data-stu-id="30ffc-343">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="30ffc-344">**上次发送时间**</span><span class="sxs-lookup"><span data-stu-id="30ffc-344">**Last Sent Time**</span></span>  
 <span data-ttu-id="30ffc-345">指示发送最后一个日志块的时间。</span><span class="sxs-lookup"><span data-stu-id="30ffc-345">Indicates the time when the last log block was sent.</span></span> <span data-ttu-id="30ffc-346">默认情况下隐藏此值。</span><span class="sxs-lookup"><span data-stu-id="30ffc-346">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="30ffc-347">**上次接收的 LSN**</span><span class="sxs-lookup"><span data-stu-id="30ffc-347">**Last Received LSN**</span></span>  
 <span data-ttu-id="30ffc-348">指示一个点，在该点之前，所有日志块都已由承载此辅助数据库的辅助副本接收。</span><span class="sxs-lookup"><span data-stu-id="30ffc-348">Indicates the point up to which all log blocks have been received by the secondary replica that hosts the secondary database.</span></span> <span data-ttu-id="30ffc-349">默认情况下隐藏此值。</span><span class="sxs-lookup"><span data-stu-id="30ffc-349">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="30ffc-350">**上次接收时间**</span><span class="sxs-lookup"><span data-stu-id="30ffc-350">**Last Received Time**</span></span>  
 <span data-ttu-id="30ffc-351">指示在辅助副本上，最后收到的消息中日志块标识符的读取时间。</span><span class="sxs-lookup"><span data-stu-id="30ffc-351">Indicates the time when the log block identifier in last message received was read on the secondary replica.</span></span> <span data-ttu-id="30ffc-352">默认情况下隐藏此值。</span><span class="sxs-lookup"><span data-stu-id="30ffc-352">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="30ffc-353">**上次强化的 LSN**</span><span class="sxs-lookup"><span data-stu-id="30ffc-353">**Last Hardened LSN**</span></span>  
 <span data-ttu-id="30ffc-354">指示一个点，在该点之前，所有日志记录都已刷新到辅助副本上的磁盘。</span><span class="sxs-lookup"><span data-stu-id="30ffc-354">Indicates the point up to which all log records have been flushed to disk on the secondary replica.</span></span> <span data-ttu-id="30ffc-355">默认情况下隐藏此值。</span><span class="sxs-lookup"><span data-stu-id="30ffc-355">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="30ffc-356">**上次强化时间**</span><span class="sxs-lookup"><span data-stu-id="30ffc-356">**Last Hardened Time**</span></span>  
 <span data-ttu-id="30ffc-357">指示在辅助副本上，上次强制写入的 LSN 的日志块标识符的接收时间。</span><span class="sxs-lookup"><span data-stu-id="30ffc-357">Indicates the time when the log-block identifier was received for the last hardened LSN on the secondary replica.</span></span> <span data-ttu-id="30ffc-358">默认情况下隐藏此值。</span><span class="sxs-lookup"><span data-stu-id="30ffc-358">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="30ffc-359">**上次重做的 LSN**</span><span class="sxs-lookup"><span data-stu-id="30ffc-359">**Last Redone LSN**</span></span>  
 <span data-ttu-id="30ffc-360">指示在辅助数据库上上次重做的日志记录的实际 LSN。</span><span class="sxs-lookup"><span data-stu-id="30ffc-360">Indicates the actual LSN of the log record that was redone last on the secondary replica.</span></span> <span data-ttu-id="30ffc-361">默认情况下隐藏此值。</span><span class="sxs-lookup"><span data-stu-id="30ffc-361">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="30ffc-362">**上次重做时间**</span><span class="sxs-lookup"><span data-stu-id="30ffc-362">**Last Redone Time**</span></span>  
 <span data-ttu-id="30ffc-363">指示在辅助数据库上重做最后一个日志记录的时间。</span><span class="sxs-lookup"><span data-stu-id="30ffc-363">Indicates the time when the last log record was redone on the secondary database.</span></span> <span data-ttu-id="30ffc-364">默认情况下隐藏此值。</span><span class="sxs-lookup"><span data-stu-id="30ffc-364">This value is hidden by default.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="30ffc-365">相关任务</span><span class="sxs-lookup"><span data-stu-id="30ffc-365">Related Tasks</span></span>  
  
-   [<span data-ttu-id="30ffc-366">使用 AlwaysOn 策略查看可用性组的运行状况 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="30ffc-366">Use AlwaysOn Policies to View the Health of an Availability Group &#40;SQL Server&#41;</span></span>](use-always-on-policies-to-view-the-health-of-an-availability-group-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="30ffc-367">另请参阅</span><span class="sxs-lookup"><span data-stu-id="30ffc-367">See Also</span></span>  
 <span data-ttu-id="30ffc-368">[sys.dm_os_performance_counters (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="30ffc-368">[sys.dm_os_performance_counters &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql) </span></span>  
 [<span data-ttu-id="30ffc-369">监视可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="30ffc-369">Monitoring of Availability Groups &#40;SQL Server&#41;</span></span>](monitoring-of-availability-groups-sql-server.md)  
  
  
