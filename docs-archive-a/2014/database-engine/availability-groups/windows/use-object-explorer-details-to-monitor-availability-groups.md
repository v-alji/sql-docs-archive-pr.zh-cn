---
title: 使用对象资源管理器详细信息来监视可用性组 (SQL Server Management Studio) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.OEdetails.f1
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- Availability Groups [SQL Server], databases
- Availability Groups [SQL Server]
ms.assetid: 84affc47-40e0-43d9-855e-468967068c35
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 419f1cd22e0a7aa314f6a1036793091bb7b385fc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578436"
---
# <a name="use-the-object-explorer-details-to-monitor-availability-groups-sql-server-management-studio"></a><span data-ttu-id="6bca0-102">使用对象资源管理器详细信息监视可用性组 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="6bca0-102">Use the Object Explorer Details to Monitor Availability Groups (SQL Server Management Studio)</span></span>
  <span data-ttu-id="6bca0-103">本主题说明如何通过使用 **的** “对象资源管理器详细信息” [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 窗格来监视和管理现有的 AlwaysOn 可用性组、可用性副本和可用性数据库。</span><span class="sxs-lookup"><span data-stu-id="6bca0-103">This topic describes how to use the **Object Explorer Details** pane of [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] to monitor and manage existing AlwaysOn availability groups, availability replicas, and availability databases.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6bca0-104">有关使用“对象资源管理器详细信息”窗格的信息，请参阅 [对象资源管理器详细信息窗格](../../../ssms/object/object-explorer-details-pane.md)。</span><span class="sxs-lookup"><span data-stu-id="6bca0-104">For information about using the Object Explorer Details pane, see [Object Explorer Details Pane](../../../ssms/object/object-explorer-details-pane.md).</span></span>  
  
-   <span data-ttu-id="6bca0-105">**准备工作：**  [先决条件](#Prerequisites)</span><span class="sxs-lookup"><span data-stu-id="6bca0-105">**Before you begin:**  [Prerequisites](#Prerequisites)</span></span>  
  
-   <span data-ttu-id="6bca0-106">**若要监视可用性组，请使用：**  [SQL Server Management Studio](#SSMSProcedure)</span><span class="sxs-lookup"><span data-stu-id="6bca0-106">**To Monitor an Availability Group, using:**  [SQL Server Management Studio](#SSMSProcedure)</span></span>  
  
-   <span data-ttu-id="6bca0-107">**对象资源管理器详细信息：**</span><span class="sxs-lookup"><span data-stu-id="6bca0-107">**Object Explorer Details:**</span></span>  
  
     [<span data-ttu-id="6bca0-108">可用性组详细信息</span><span class="sxs-lookup"><span data-stu-id="6bca0-108">Availability Group Details</span></span>](#AvGroupsDetails)  
  
     [<span data-ttu-id="6bca0-109">可用性副本详细信息</span><span class="sxs-lookup"><span data-stu-id="6bca0-109">Availability Replica Details</span></span>](#AvReplicaDetails)  
  
     [<span data-ttu-id="6bca0-110">可用性数据库详细信息</span><span class="sxs-lookup"><span data-stu-id="6bca0-110">Availability Database Details</span></span>](#AvDbDetails)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="6bca0-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="6bca0-111">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="6bca0-112">先决条件</span><span class="sxs-lookup"><span data-stu-id="6bca0-112">Prerequisites</span></span>  
 <span data-ttu-id="6bca0-113">您必须连接到承载主副本或辅助副本的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例（服务器实例）。</span><span class="sxs-lookup"><span data-stu-id="6bca0-113">You must be connected to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (server instance) that hosts either the primary replica or a secondary replica.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="6bca0-114">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="6bca0-114">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="6bca0-115">**监视可用性组、可用性副本和可用性数据库**</span><span class="sxs-lookup"><span data-stu-id="6bca0-115">**To monitor availability groups, availability replicas, and availability databases**</span></span>  
  
1.  <span data-ttu-id="6bca0-116">在“视图”菜单上单击 **“对象资源管理器详细信息”** ，或按 **F7** 键。</span><span class="sxs-lookup"><span data-stu-id="6bca0-116">On the View menu, click **Object Explorer Details**, or press the **F7** key.</span></span>  
  
2.  <span data-ttu-id="6bca0-117">在对象资源管理器中，连接到要在其上监视可用性组的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例，然后单击服务器名称以展开服务器树。</span><span class="sxs-lookup"><span data-stu-id="6bca0-117">In Object Explorer, connect to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on which you want to monitor an availability group, and click the server name to expand the server tree.</span></span>  
  
3.  <span data-ttu-id="6bca0-118">依次展开 **“AlwaysOn 高可用性”** 节点和 **“可用性组”** 节点。</span><span class="sxs-lookup"><span data-stu-id="6bca0-118">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
4.  <span data-ttu-id="6bca0-119">**“对象资源管理器详细信息”** 窗格显示所连接的服务器实例为其承载副本的所有可用性组。</span><span class="sxs-lookup"><span data-stu-id="6bca0-119">The **Object Explorer Details** pane displays every availability group for which the connected server instance hosts a replica.</span></span> <span data-ttu-id="6bca0-120">对于每个可用性组，“服务器实例(主)”列都显示当前承载主要副本的服务器实例的名称。</span><span class="sxs-lookup"><span data-stu-id="6bca0-120">For each availability group, the **Server Instance (Primary)** column displays the name of the server instance that is currently hosting the primary replica.</span></span>  <span data-ttu-id="6bca0-121">若要显示有关给定的可用性组的详细信息，请在对象资源管理器中选择它。</span><span class="sxs-lookup"><span data-stu-id="6bca0-121">To display more information about a given availability group, select it in Object Explorer.</span></span>  
  
5.  <span data-ttu-id="6bca0-122">**“对象资源管理器详细信息”** 窗格随后显示此可用性组的 **“可用性副本”** 和 **“可用性数据库”** 节点：</span><span class="sxs-lookup"><span data-stu-id="6bca0-122">The **Object Explorer Details** pane then displays the **Availability Replicas** and **Availability Databases** nodes for this availability group:</span></span>  
  
    -   <span data-ttu-id="6bca0-123">当您展开对象资源管理器中的 **“可用性组”** 节点并选择 **“可用性副本”** 节点后， **“对象资源管理器详细信息”** 窗格将显示有关该组中每个可用性副本的信息。</span><span class="sxs-lookup"><span data-stu-id="6bca0-123">When you expand the **Availability Group** node in Object Explorer and select the **Availability Replicas** node, the **Object Explorer Details** pane displays information about each of the availability replicas in the group.</span></span> <span data-ttu-id="6bca0-124">有关详细信息，请参阅本主题后面的 [可用性副本详细信息](#AvReplicaDetails)。</span><span class="sxs-lookup"><span data-stu-id="6bca0-124">For more information, see [Availability Replica Details](#AvReplicaDetails), later in this topic.</span></span>  
  
         <span data-ttu-id="6bca0-125">若要对多个可用性副本执行操作，请选择这些副本，然后右键单击它们以打开一个列出可用命令的上下文菜单。</span><span class="sxs-lookup"><span data-stu-id="6bca0-125">To perform operations on multiple availability replicas, select them, and right-click them to open up a context menu that lists the available commands.</span></span>  
  
    -   <span data-ttu-id="6bca0-126">当您展开对象资源管理器中的 **“可用性组”** 节点并选择 **“可用性数据库”** 节点后， **“对象资源管理器详细信息”** 窗格将显示有关该组中每个可用性数据库的信息。</span><span class="sxs-lookup"><span data-stu-id="6bca0-126">When you expand the **Availability Group** node in Object Explorer and select the **Availability Databases** node, the **Object Explorer Details** pane displays information about each of the availability databases in the group.</span></span> <span data-ttu-id="6bca0-127">有关详细信息，请参阅本主题后面的 [可用性数据库详细信息](#AvDbDetails)。</span><span class="sxs-lookup"><span data-stu-id="6bca0-127">For more information, see [Availability Database Details](#AvDbDetails), later in this topic.</span></span>  
  
         <span data-ttu-id="6bca0-128">若要对多个可用性数据库执行操作，请选择这些数据库，然后右键单击它们以打开一个列出可用命令的上下文菜单。</span><span class="sxs-lookup"><span data-stu-id="6bca0-128">To perform operations on multiple availability databases, select them, and right-click them to open up a context menu that lists the available commands.</span></span>  
  
##  <a name="availability-groups-details"></a><a name="AvGroupsDetails"></a> <span data-ttu-id="6bca0-129">可用性组详细信息</span><span class="sxs-lookup"><span data-stu-id="6bca0-129">Availability Groups Details</span></span>  
 <span data-ttu-id="6bca0-130">**“可用性组”** 详细信息屏幕显示以下列：</span><span class="sxs-lookup"><span data-stu-id="6bca0-130">The **Availability Groups** details screen displays the following columns:</span></span>  
  
 <span data-ttu-id="6bca0-131">**名称**</span><span class="sxs-lookup"><span data-stu-id="6bca0-131">**Name**</span></span>  
 <span data-ttu-id="6bca0-132">列出所选可用性组的“可用性副本”、“可用性数据库”和“可用性组”侦听器等文件夹。  </span><span class="sxs-lookup"><span data-stu-id="6bca0-132">Lists the **Availability Replicas**, **Availability Databases**, and **Availability Group** Listeners folders of the selected availability group.</span></span>  
  
##  <a name="availability-replica-details"></a><a name="AvReplicaDetails"></a> <span data-ttu-id="6bca0-133">可用性副本详细信息</span><span class="sxs-lookup"><span data-stu-id="6bca0-133">Availability Replica Details</span></span>  
 <span data-ttu-id="6bca0-134">**“可用性副本”** 详细信息屏幕显示以下列：</span><span class="sxs-lookup"><span data-stu-id="6bca0-134">The **Availability Replica** details screen displays the following columns:</span></span>  
  
 <span data-ttu-id="6bca0-135">**服务器实例**</span><span class="sxs-lookup"><span data-stu-id="6bca0-135">**Server Instance**</span></span>  
 <span data-ttu-id="6bca0-136">显示承载可用性副本的服务器实例的名称，以及指示该服务器实例与本地服务器实例的当前连接状态的图标。</span><span class="sxs-lookup"><span data-stu-id="6bca0-136">Displays the name of the server instance that hosts the availability replica, along with an icon that indicates the current connection state of the server instance to the local server instance.</span></span>  
  
 <span data-ttu-id="6bca0-137">**角色**</span><span class="sxs-lookup"><span data-stu-id="6bca0-137">**Role**</span></span>  
 <span data-ttu-id="6bca0-138">指示可用性副本的当前角色，即“主”或“辅助”。</span><span class="sxs-lookup"><span data-stu-id="6bca0-138">Indicates the current role of the availability replica, either **Primary** or **Secondary**.</span></span> <span data-ttu-id="6bca0-139">有关 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 角色的详细信息，请参阅 [AlwaysOn 可用性组概述 (SQL Server)](overview-of-always-on-availability-groups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="6bca0-139">For information about [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] roles, see [Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md).</span></span>  
  
 <span data-ttu-id="6bca0-140">**辅助角色中的连接模式**</span><span class="sxs-lookup"><span data-stu-id="6bca0-140">**Connection Mode in Secondary Role**</span></span>  
 <span data-ttu-id="6bca0-141">指示给定的可用性副本（正在执行辅助角色，也就是充当辅助副本）的数据库是否可以接受来自客户端的连接。</span><span class="sxs-lookup"><span data-stu-id="6bca0-141">Indicates whether the databases of a given availability replica that is performing the secondary role (that is, is acting as a secondary replica) can accept connections from clients.</span></span>  
  
 <span data-ttu-id="6bca0-142">可能的值如下：</span><span class="sxs-lookup"><span data-stu-id="6bca0-142">The possible values are as follows:</span></span>  
  
|<span data-ttu-id="6bca0-143">值</span><span class="sxs-lookup"><span data-stu-id="6bca0-143">Value</span></span>|<span data-ttu-id="6bca0-144">说明</span><span class="sxs-lookup"><span data-stu-id="6bca0-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6bca0-145">**禁止连接**</span><span class="sxs-lookup"><span data-stu-id="6bca0-145">**Disallow Connections**</span></span>|<span data-ttu-id="6bca0-146">当此可用性副本充当辅助副本时，不允许直接连接到可用性数据库。</span><span class="sxs-lookup"><span data-stu-id="6bca0-146">No direct connections are allowed to the availability databases when this availability replica is acting as a secondary replica.</span></span> <span data-ttu-id="6bca0-147">辅助数据库不可用于读访问。</span><span class="sxs-lookup"><span data-stu-id="6bca0-147">Secondary databases are not available for read access.</span></span>|  
|<span data-ttu-id="6bca0-148">**只允许读意向连接**</span><span class="sxs-lookup"><span data-stu-id="6bca0-148">**Allow Only Read Intent Connections**</span></span>|<span data-ttu-id="6bca0-149">当此副本充当辅助副本时，仅允许直接只读连接。</span><span class="sxs-lookup"><span data-stu-id="6bca0-149">Only direct read-only connections are allowed  when this replica acting as a secondary replica.</span></span> <span data-ttu-id="6bca0-150">副本中的所有数据库都可用于读访问。</span><span class="sxs-lookup"><span data-stu-id="6bca0-150">All database(s) in the replica are available for read access.</span></span>|  
|<span data-ttu-id="6bca0-151">**允许所有连接**</span><span class="sxs-lookup"><span data-stu-id="6bca0-151">**Allow All Connections**</span></span>|<span data-ttu-id="6bca0-152">当此副本充当辅助副本时，允许与这些数据库建立的所有连接进行只读访问。</span><span class="sxs-lookup"><span data-stu-id="6bca0-152">All connections are allowed to these databases for read-only access when this replica acting as a secondary replica.</span></span>|  
  
 <span data-ttu-id="6bca0-153">**连接状态**</span><span class="sxs-lookup"><span data-stu-id="6bca0-153">**Connection State**</span></span>  
 <span data-ttu-id="6bca0-154">指示辅助副本当前是否连接到主副本。</span><span class="sxs-lookup"><span data-stu-id="6bca0-154">Indicates whether a secondary replica is currently connected to the primary replica.</span></span> <span data-ttu-id="6bca0-155">可能的值如下：</span><span class="sxs-lookup"><span data-stu-id="6bca0-155">The possible values are as follows:</span></span>  
  
|<span data-ttu-id="6bca0-156">值</span><span class="sxs-lookup"><span data-stu-id="6bca0-156">Value</span></span>|<span data-ttu-id="6bca0-157">说明</span><span class="sxs-lookup"><span data-stu-id="6bca0-157">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6bca0-158">**已断开连接**</span><span class="sxs-lookup"><span data-stu-id="6bca0-158">**Disconnected**</span></span>|<span data-ttu-id="6bca0-159">对于远程可用性副本，指示它与本地可用性副本已断开连接。</span><span class="sxs-lookup"><span data-stu-id="6bca0-159">For a remote availability replica, indicates that it is disconnected from the local availability replica.</span></span> <span data-ttu-id="6bca0-160">本地副本对于“已断开连接”状态的响应取决于它的角色，如下所示：</span><span class="sxs-lookup"><span data-stu-id="6bca0-160">The response of the local replica to the Disconnected state depends on its role, as follows:</span></span><br /><br /> <span data-ttu-id="6bca0-161">在主副本上，如果辅助副本已断开连接，辅助数据库将在主副本上标记为 **“未同步”** ，主副本等待辅助副本重新连接。</span><span class="sxs-lookup"><span data-stu-id="6bca0-161">On the primary replica, if a secondary replica is disconnected, the secondary databases are marked as **Not Synchronized** on the primary replica, and the primary replica waits for the secondary to reconnect.</span></span><br /><br /> <span data-ttu-id="6bca0-162">在辅助副本上，一旦检测到其未连接，辅助副本会尝试重新连接主副本。</span><span class="sxs-lookup"><span data-stu-id="6bca0-162">On the secondary replica, upon detecting that it is disconnected, the secondary replica attempts to reconnect to the primary replica.</span></span>|  
|<span data-ttu-id="6bca0-163">**已连接**</span><span class="sxs-lookup"><span data-stu-id="6bca0-163">**Connected**</span></span>|<span data-ttu-id="6bca0-164">远程可用性副本当前连接到本地副本。</span><span class="sxs-lookup"><span data-stu-id="6bca0-164">A remote availability replica that is currently connected to the local replica.</span></span>|  
|<span data-ttu-id="6bca0-165">**NULL**</span><span class="sxs-lookup"><span data-stu-id="6bca0-165">**NULL**</span></span>|<span data-ttu-id="6bca0-166">如果本地副本是一个辅助副本，则此值对于其他辅助副本均为 NULL。</span><span class="sxs-lookup"><span data-stu-id="6bca0-166">If the local replica is a secondary replica, this value is NULL for other secondary replicas.</span></span>|  
  
 <span data-ttu-id="6bca0-167">**同步状态**</span><span class="sxs-lookup"><span data-stu-id="6bca0-167">**Synchronization State**</span></span>  
 <span data-ttu-id="6bca0-168">指示辅助副本当前是否与主副本同步。</span><span class="sxs-lookup"><span data-stu-id="6bca0-168">Indicates whether a secondary replica is currently synchronized with primary replica.</span></span> <span data-ttu-id="6bca0-169">可能的值如下：</span><span class="sxs-lookup"><span data-stu-id="6bca0-169">The possible values are as follows:</span></span>  
  
|<span data-ttu-id="6bca0-170">值</span><span class="sxs-lookup"><span data-stu-id="6bca0-170">Value</span></span>|<span data-ttu-id="6bca0-171">说明</span><span class="sxs-lookup"><span data-stu-id="6bca0-171">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6bca0-172">**“未同步”**</span><span class="sxs-lookup"><span data-stu-id="6bca0-172">**Not Synchronized**</span></span>|<span data-ttu-id="6bca0-173">该数据库未同步或尚未联接到可用性组。</span><span class="sxs-lookup"><span data-stu-id="6bca0-173">The database is not synchronized or has not yet been joined to the availability group.</span></span>|  
|<span data-ttu-id="6bca0-174">**已同步**</span><span class="sxs-lookup"><span data-stu-id="6bca0-174">**Synchronized**</span></span>|<span data-ttu-id="6bca0-175">该数据库与当前主副本（如果有）或上一个主副本上的主数据库同步。</span><span class="sxs-lookup"><span data-stu-id="6bca0-175">The database is synchronized with the primary database on the current primary replica, if any, or on the last primary replica.</span></span><br /><br /> <span data-ttu-id="6bca0-176">注意：在性能模式中，数据库从不处于“已同步”状态。</span><span class="sxs-lookup"><span data-stu-id="6bca0-176">Note: In performance mode, the database is never in the Synchronized state.</span></span>|  
|<span data-ttu-id="6bca0-177">**NULL**</span><span class="sxs-lookup"><span data-stu-id="6bca0-177">**NULL**</span></span>|<span data-ttu-id="6bca0-178">未知状态。</span><span class="sxs-lookup"><span data-stu-id="6bca0-178">Unknown state.</span></span> <span data-ttu-id="6bca0-179">当本地服务器实例无法与 WSFC 故障转移群集通信（即本地节点不是 WSFC 仲裁的一部分）时，出现此值。</span><span class="sxs-lookup"><span data-stu-id="6bca0-179">This value occurs when the local server instance cannot communicate with the WSFC failover cluster (that is the local node is not part of WSFC quorum).</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="6bca0-180">有关可用性副本的性能计数器的信息，请参阅 [SQL Server，可用性副本](../../../relational-databases/performance-monitor/sql-server-availability-replica.md)。</span><span class="sxs-lookup"><span data-stu-id="6bca0-180">For information about performance counters for availability replicas, see [SQL Server, Availability Replica](../../../relational-databases/performance-monitor/sql-server-availability-replica.md).</span></span>  
  
##  <a name="availability-database-details"></a><a name="AvDbDetails"></a> <span data-ttu-id="6bca0-181">可用性数据库详细信息</span><span class="sxs-lookup"><span data-stu-id="6bca0-181">Availability Database Details</span></span>  
 <span data-ttu-id="6bca0-182">**“可用性数据库”** 详细信息屏幕显示给定可用性组中的可用性数据库的以下属性：</span><span class="sxs-lookup"><span data-stu-id="6bca0-182">The **Availability Database** details screen displays the following properties of the availability databases in a given availability group:</span></span>  
  
 <span data-ttu-id="6bca0-183">**名称**</span><span class="sxs-lookup"><span data-stu-id="6bca0-183">**Name**</span></span>  
 <span data-ttu-id="6bca0-184">可用性数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="6bca0-184">The name of the availability database.</span></span>  
  
 <span data-ttu-id="6bca0-185">**同步状态**</span><span class="sxs-lookup"><span data-stu-id="6bca0-185">**Synchronization State**</span></span>  
 <span data-ttu-id="6bca0-186">指示可用性数据库当前是否与主副本同步。</span><span class="sxs-lookup"><span data-stu-id="6bca0-186">Indicates whether the availability database is currently synchronized with primary replica.</span></span>  
  
 <span data-ttu-id="6bca0-187">可能的同步状态如下所示：</span><span class="sxs-lookup"><span data-stu-id="6bca0-187">The possible synchronization states are as follows:</span></span>  
  
|<span data-ttu-id="6bca0-188">值</span><span class="sxs-lookup"><span data-stu-id="6bca0-188">Value</span></span>|<span data-ttu-id="6bca0-189">说明</span><span class="sxs-lookup"><span data-stu-id="6bca0-189">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6bca0-190">正在同步</span><span class="sxs-lookup"><span data-stu-id="6bca0-190">Synchronizing</span></span>|<span data-ttu-id="6bca0-191">辅助数据库已收到主数据库尚未写入磁盘（硬编码）的事务日志记录。</span><span class="sxs-lookup"><span data-stu-id="6bca0-191">The secondary database has received the transaction log records for the primary database that are not yet written to disk (hardened).</span></span><br /><br /> <span data-ttu-id="6bca0-192">注意：在异步提交模式中，同步状态始终是“正在同步”。</span><span class="sxs-lookup"><span data-stu-id="6bca0-192">Note: In asynchronous-commit mode, the synchronization state is always **Synchronizing**.</span></span>|  
  
 <span data-ttu-id="6bca0-193">**已挂起**</span><span class="sxs-lookup"><span data-stu-id="6bca0-193">**Suspended**</span></span>  
 <span data-ttu-id="6bca0-194">指示可用性数据库当前是否联机。</span><span class="sxs-lookup"><span data-stu-id="6bca0-194">Indicates whether the availability database is currently online.</span></span> <span data-ttu-id="6bca0-195">可能的值如下：</span><span class="sxs-lookup"><span data-stu-id="6bca0-195">The possible values are as follows:</span></span>  
  
|<span data-ttu-id="6bca0-196">值</span><span class="sxs-lookup"><span data-stu-id="6bca0-196">Value</span></span>|<span data-ttu-id="6bca0-197">说明</span><span class="sxs-lookup"><span data-stu-id="6bca0-197">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6bca0-198">**已挂起**</span><span class="sxs-lookup"><span data-stu-id="6bca0-198">**Suspended**</span></span>|<span data-ttu-id="6bca0-199">此状态指示该数据库在本地挂起，需要手动恢复。</span><span class="sxs-lookup"><span data-stu-id="6bca0-199">This state indicates that the database is suspended locally and needs to be manually resumed.</span></span><br /><br /> <span data-ttu-id="6bca0-200">在主副本上，该值对于辅助数据库是不可靠的。</span><span class="sxs-lookup"><span data-stu-id="6bca0-200">On the primary replica, the value is unreliable for a secondary database.</span></span> <span data-ttu-id="6bca0-201">若要确认辅助数据库是否挂起，请在承载该数据库的辅助副本上进行查询。</span><span class="sxs-lookup"><span data-stu-id="6bca0-201">To reliably determine whether a secondary database is suspended, query it on the secondary replica that hosts the database.</span></span>|  
|<span data-ttu-id="6bca0-202">**未联接**</span><span class="sxs-lookup"><span data-stu-id="6bca0-202">**Not Joined**</span></span>|<span data-ttu-id="6bca0-203">指示辅助数据库要么未联接到可用性组，要么已从该组中删除。</span><span class="sxs-lookup"><span data-stu-id="6bca0-203">Indicates that the secondary database either has not been joined to the availability group or has been removed from the group.</span></span>|  
|<span data-ttu-id="6bca0-204">**联机**</span><span class="sxs-lookup"><span data-stu-id="6bca0-204">**Online**</span></span>|<span data-ttu-id="6bca0-205">指示数据库在本地可用性副本上未挂起，并且该数据库处于连接状态。</span><span class="sxs-lookup"><span data-stu-id="6bca0-205">Indicates that the database is not suspended on the local availability replica and that the database is connected.</span></span>|  
|<span data-ttu-id="6bca0-206">**未连接**</span><span class="sxs-lookup"><span data-stu-id="6bca0-206">**Not Connected**</span></span>|<span data-ttu-id="6bca0-207">指示辅助副本当前未能连接到主副本。</span><span class="sxs-lookup"><span data-stu-id="6bca0-207">Indicates that the secondary replica is currently unable to connect to the primary replica.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="6bca0-208">有关可用性数据库的性能计数器的信息，请参阅 [SQL Server，数据库复制](../../../relational-databases/performance-monitor/sql-server-database-replica.md)。</span><span class="sxs-lookup"><span data-stu-id="6bca0-208">For information about performance counters for availability databases, see [SQL Server, Database Replica](../../../relational-databases/performance-monitor/sql-server-database-replica.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bca0-209">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6bca0-209">See Also</span></span>  
 <span data-ttu-id="6bca0-210">[sys.dm_os_performance_counters (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6bca0-210">[sys.dm_os_performance_counters &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql) </span></span>  
 <span data-ttu-id="6bca0-211">[使用 AlwaysOn 仪表板 &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="6bca0-211">[Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md) </span></span>  
 <span data-ttu-id="6bca0-212">[查看可用性组属性 (SQL Server)](view-availability-group-properties-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6bca0-212">[View Availability Group Properties &#40;SQL Server&#41;](view-availability-group-properties-sql-server.md) </span></span>  
 [<span data-ttu-id="6bca0-213">查看可用性副本属性 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6bca0-213">View Availability Replica Properties &#40;SQL Server&#41;</span></span>](view-availability-replica-properties-sql-server.md)  
  
  
