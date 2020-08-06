---
title: 可用性副本属性（“常规”页）| Microsoft Docs
ms.custom: ''
ms.date: 10/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilityreplicaproperties.general.f1
ms.assetid: 8318fefb-e045-4fab-8507-e1951fc7cec6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 313314baf009cdfb6109e63e9b65e369ac314f60
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693501"
---
# <a name="availability-replica-properties-general-page"></a><span data-ttu-id="cd6b3-102">可用性副本属性（“常规”页）</span><span class="sxs-lookup"><span data-stu-id="cd6b3-102">Availability Replica Properties (General Page)</span></span>
  <span data-ttu-id="cd6b3-103">使用此对话框可以查看可用性副本的属性。</span><span class="sxs-lookup"><span data-stu-id="cd6b3-103">Use this dialog box to viewthe properties of an availability replica.</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="cd6b3-104">任务列表</span><span class="sxs-lookup"><span data-stu-id="cd6b3-104">Task List</span></span>  
 <span data-ttu-id="cd6b3-105">**查看可用性副本属性**</span><span class="sxs-lookup"><span data-stu-id="cd6b3-105">**To view availability replica properties**</span></span>  
  
-   [<span data-ttu-id="cd6b3-106">查看可用性副本属性 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="cd6b3-106">View Availability Replica Properties &#40;SQL Server&#41;</span></span>](view-availability-replica-properties-sql-server.md)  
  
-   [<span data-ttu-id="cd6b3-107">使用 AlwaysOn 面板 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="cd6b3-107">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
## <a name="ui-element-list"></a><span data-ttu-id="cd6b3-108">UI 元素列表</span><span class="sxs-lookup"><span data-stu-id="cd6b3-108">UI element list</span></span>  
 <span data-ttu-id="cd6b3-109">**可用性组名称**</span><span class="sxs-lookup"><span data-stu-id="cd6b3-109">**Availability group name**</span></span>  
 <span data-ttu-id="cd6b3-110">可用性组的名称。</span><span class="sxs-lookup"><span data-stu-id="cd6b3-110">Name of the availability group.</span></span> <span data-ttu-id="cd6b3-111">这是在 Windows Server 故障转移群集 (WSFC) 内必须唯一的用户指定的名称。</span><span class="sxs-lookup"><span data-stu-id="cd6b3-111">This is a user-specified name that must be unique within the Windows Server Failover Cluster (WSFC).</span></span>  
  
 <span data-ttu-id="cd6b3-112">**服务器实例**</span><span class="sxs-lookup"><span data-stu-id="cd6b3-112">**Server instance**</span></span>  
 <span data-ttu-id="cd6b3-113">承载此副本的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例的服务器名称；对于非默认实例，则为其实例名称。</span><span class="sxs-lookup"><span data-stu-id="cd6b3-113">Server name of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that is hosting this replica and, for a non-default instance, its instance name.</span></span>  
  
 <span data-ttu-id="cd6b3-114">**角色**</span><span class="sxs-lookup"><span data-stu-id="cd6b3-114">**Role**</span></span>  
 <span data-ttu-id="cd6b3-115">**主要节点**</span><span class="sxs-lookup"><span data-stu-id="cd6b3-115">**Primary**</span></span>  
 <span data-ttu-id="cd6b3-116">当前主副本。</span><span class="sxs-lookup"><span data-stu-id="cd6b3-116">Currently the primary replica.</span></span>  
  
 <span data-ttu-id="cd6b3-117">**辅助节点**</span><span class="sxs-lookup"><span data-stu-id="cd6b3-117">**Secondary**</span></span>  
 <span data-ttu-id="cd6b3-118">当前辅助副本。</span><span class="sxs-lookup"><span data-stu-id="cd6b3-118">Currently a secondary replica.</span></span>  
  
 <span data-ttu-id="cd6b3-119">**正在解析**</span><span class="sxs-lookup"><span data-stu-id="cd6b3-119">**Resolving**</span></span>  
 <span data-ttu-id="cd6b3-120">当前该副本角色处于正在解析为主角色或辅助角色的进程中。</span><span class="sxs-lookup"><span data-stu-id="cd6b3-120">Currently the replica role is in the process of being resolved to either the primary or secondary role.</span></span>  
  
 <span data-ttu-id="cd6b3-121">**可用性模式**</span><span class="sxs-lookup"><span data-stu-id="cd6b3-121">**Availability mode**</span></span>  
 <span data-ttu-id="cd6b3-122">副本的可用性模式，可为下列值之一：</span><span class="sxs-lookup"><span data-stu-id="cd6b3-122">The availability mode of the replica, one of:</span></span>  
  
 <span data-ttu-id="cd6b3-123">**异步提交**</span><span class="sxs-lookup"><span data-stu-id="cd6b3-123">**Asynchronous commit**</span></span>  
 <span data-ttu-id="cd6b3-124">主副本可以不必等待辅助副本将日志写入磁盘，即可提交事务。</span><span class="sxs-lookup"><span data-stu-id="cd6b3-124">The primary replica can commit transactions without waiting for the secondary to write the log to disk.</span></span>  
  
 <span data-ttu-id="cd6b3-125">**同步提交**</span><span class="sxs-lookup"><span data-stu-id="cd6b3-125">**Synchronous commit**</span></span>  
 <span data-ttu-id="cd6b3-126">主副本等待提交给定的事务，直到辅助副本将事务写入磁盘。</span><span class="sxs-lookup"><span data-stu-id="cd6b3-126">The primary replica waits to commit a given transaction until the secondary replica has written the transaction to disk.</span></span>  
  
 <span data-ttu-id="cd6b3-127">有关详细信息，请参阅[可用性模式 (AlwaysOn 可用性组) ](availability-modes-always-on-availability-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="cd6b3-127">For more information, see [Availability Modes (AlwaysOn Availability Groups)](availability-modes-always-on-availability-groups.md).</span></span>  
  
 <span data-ttu-id="cd6b3-128">**Failover mode**</span><span class="sxs-lookup"><span data-stu-id="cd6b3-128">**Failover mode**</span></span>  
 <span data-ttu-id="cd6b3-129">副本的故障转移模式，可为下列值之一：</span><span class="sxs-lookup"><span data-stu-id="cd6b3-129">The failover mode of the replica, one of:</span></span>  
  
 <span data-ttu-id="cd6b3-130">**自动**</span><span class="sxs-lookup"><span data-stu-id="cd6b3-130">**Automatic**</span></span>  
 <span data-ttu-id="cd6b3-131">自动故障转移。</span><span class="sxs-lookup"><span data-stu-id="cd6b3-131">Automatic failover.</span></span> <span data-ttu-id="cd6b3-132">副本为自动故障转移的目标。</span><span class="sxs-lookup"><span data-stu-id="cd6b3-132">The replica is a target for automatic failovers.</span></span> <span data-ttu-id="cd6b3-133">仅当可用性模式设置为同步提交时，才选择此选项。</span><span class="sxs-lookup"><span data-stu-id="cd6b3-133">This is supported only if the availability mode is set to synchronous commit.</span></span>  
  
 <span data-ttu-id="cd6b3-134">**手动**</span><span class="sxs-lookup"><span data-stu-id="cd6b3-134">**Manual**</span></span>  
 <span data-ttu-id="cd6b3-135">手动故障转移。</span><span class="sxs-lookup"><span data-stu-id="cd6b3-135">Manual failover.</span></span> <span data-ttu-id="cd6b3-136">副本仅能由数据库管理员手动进行故障转移。</span><span class="sxs-lookup"><span data-stu-id="cd6b3-136">The replica can only be failed over to manually by the database administrator.</span></span>  
  
 <span data-ttu-id="cd6b3-137">**主角色中的连接**</span><span class="sxs-lookup"><span data-stu-id="cd6b3-137">**Connections in primary role**</span></span>  
 <span data-ttu-id="cd6b3-138">当副本拥有主角色时支持的客户端连接类型。</span><span class="sxs-lookup"><span data-stu-id="cd6b3-138">The type of client connections supported when the replica owns the primary role.</span></span>  
  
 <span data-ttu-id="cd6b3-139">**允许所有连接**</span><span class="sxs-lookup"><span data-stu-id="cd6b3-139">**Allow all connections**</span></span>  
 <span data-ttu-id="cd6b3-140">主副本中的数据库允许所有连接。</span><span class="sxs-lookup"><span data-stu-id="cd6b3-140">All connections are allowed to the databases in the primary replica.</span></span> <span data-ttu-id="cd6b3-141">这是默认设置。</span><span class="sxs-lookup"><span data-stu-id="cd6b3-141">This is the default setting.</span></span>  
  
 <span data-ttu-id="cd6b3-142">**允许读/写连接**</span><span class="sxs-lookup"><span data-stu-id="cd6b3-142">**Allow read/write connections**</span></span>  
 <span data-ttu-id="cd6b3-143">不允许 Application Intent 连接属性设置为 **ReadOnly** 的连接。</span><span class="sxs-lookup"><span data-stu-id="cd6b3-143">Connections where the Application Intent connection property is set to **ReadOnly** are disallowed.</span></span> <span data-ttu-id="cd6b3-144">在 Application Intent 属性设置为 **ReadWrite** 或者未设置 Application Intent 连接属性时，将允许连接。</span><span class="sxs-lookup"><span data-stu-id="cd6b3-144">When the Application Intent property is set to **ReadWrite** or the application intent connection property is not set, the connection is allowed.</span></span>  
  
 <span data-ttu-id="cd6b3-145">**可读取辅助角色**</span><span class="sxs-lookup"><span data-stu-id="cd6b3-145">**Readable Secondary**</span></span>  
 <span data-ttu-id="cd6b3-146">正在履行辅助角色的可用性副本（也就是辅助副本）是否可以接受来自客户端的连接，可为下列值之一：</span><span class="sxs-lookup"><span data-stu-id="cd6b3-146">Whether an availability replica that is performing the secondary role (that is, a secondary replica) can accept connections from clients, one of:</span></span>  
  
 <span data-ttu-id="cd6b3-147">**是**</span><span class="sxs-lookup"><span data-stu-id="cd6b3-147">**No**</span></span>  
 <span data-ttu-id="cd6b3-148">不允许与此副本的辅助数据库的直接连接。</span><span class="sxs-lookup"><span data-stu-id="cd6b3-148">No direct connections are allowed to secondary databases of this replica.</span></span> <span data-ttu-id="cd6b3-149">它们不可用于读访问。</span><span class="sxs-lookup"><span data-stu-id="cd6b3-149">They are not available for read access.</span></span> <span data-ttu-id="cd6b3-150">这是默认设置。</span><span class="sxs-lookup"><span data-stu-id="cd6b3-150">This is the default setting.</span></span>  
  
 <span data-ttu-id="cd6b3-151">**仅限读意向**</span><span class="sxs-lookup"><span data-stu-id="cd6b3-151">**Read-intent only**</span></span>  
 <span data-ttu-id="cd6b3-152">仅允许与此副本的辅助数据库的直接只读连接。</span><span class="sxs-lookup"><span data-stu-id="cd6b3-152">Only direct read-only connections are allowed to secondary databases of this replica.</span></span> <span data-ttu-id="cd6b3-153">辅助数据库全都可用于读访问。</span><span class="sxs-lookup"><span data-stu-id="cd6b3-153">The secondary database(s) are all available for read access.</span></span>  
  
 <span data-ttu-id="cd6b3-154">**是**</span><span class="sxs-lookup"><span data-stu-id="cd6b3-154">**Yes**</span></span>  
 <span data-ttu-id="cd6b3-155">允许与此副本的辅助数据库的所有连接，但仅限读访问。</span><span class="sxs-lookup"><span data-stu-id="cd6b3-155">All connections are allowed to secondary databases of this replica, but only for read access.</span></span> <span data-ttu-id="cd6b3-156">辅助数据库全都可用于读访问。</span><span class="sxs-lookup"><span data-stu-id="cd6b3-156">The secondary database(s) are all available for read access.</span></span>  
  
 <span data-ttu-id="cd6b3-157">有关详细信息，请参阅[活动辅助副本：可读辅助副本 (AlwaysOn 可用性组) ](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="cd6b3-157">For more information, see [Active Secondaries: Readable Secondary Replicas (AlwaysOn Availability Groups)](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md).</span></span>  
  
 <span data-ttu-id="cd6b3-158">**会话超时(秒)**</span><span class="sxs-lookup"><span data-stu-id="cd6b3-158">**Session timeout (seconds)**</span></span>  
 <span data-ttu-id="cd6b3-159">超时期限（秒）。</span><span class="sxs-lookup"><span data-stu-id="cd6b3-159">The time-out period, in seconds.</span></span> <span data-ttu-id="cd6b3-160">超时期限是指副本接收来自其他副本的消息而等待的最长时间，超过此时间，将主副本和辅助副本之间的连接视为已失败。</span><span class="sxs-lookup"><span data-stu-id="cd6b3-160">The time-out period is the maximum time that the replica waits to receive a message from another replica before considering connection between the primary and secondary replica have failed.</span></span> <span data-ttu-id="cd6b3-161">会话超时检测辅助副本是否与主副本相连接。</span><span class="sxs-lookup"><span data-stu-id="cd6b3-161">Session timeout detects whether secondaries are connected the primary replica.</span></span> <span data-ttu-id="cd6b3-162">在检测到与辅助副本的连接失败时，主副本将辅助副本视为 NOT_SYNCHRONIZED。</span><span class="sxs-lookup"><span data-stu-id="cd6b3-162">On detecting a failed connection with a secondary replica, the primary replica considers the secondary replica to be NOT_SYNCHRONIZED.</span></span> <span data-ttu-id="cd6b3-163">在检测到与辅助副本的连接失败时，辅助副本只会尝试重新连接。</span><span class="sxs-lookup"><span data-stu-id="cd6b3-163">On detecting a failed connection with the primary replica, a secondary replica simply attempts to reconnect.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cd6b3-164">会话超时不会导致自动故障转移。</span><span class="sxs-lookup"><span data-stu-id="cd6b3-164">Session timeouts do not cause automatic failovers.</span></span>  
  
 <span data-ttu-id="cd6b3-165">**端点 URL**</span><span class="sxs-lookup"><span data-stu-id="cd6b3-165">**Endpoint URL**</span></span>  
 <span data-ttu-id="cd6b3-166">用户指定的数据库镜像端点的字符串表示形式，该数据库镜像端点由用于数据同步的主副本和辅助副本之间的连接使用。</span><span class="sxs-lookup"><span data-stu-id="cd6b3-166">String representation of the user-specified database mirroring endpoint that is used by connections between primary and secondary replicas for data synchronization.</span></span> <span data-ttu-id="cd6b3-167">有关这些端点 URL 语法的信息，请参阅[在添加或修改可用性副本时指定端点 URL (SQL Server)](specify-endpoint-url-adding-or-modifying-availability-replica.md)。</span><span class="sxs-lookup"><span data-stu-id="cd6b3-167">For information about the syntax of endpoint URLs, see [Specify the Endpoint URL When Adding or Modifying an Availability Replica &#40;SQL Server&#41;](specify-endpoint-url-adding-or-modifying-availability-replica.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd6b3-168">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cd6b3-168">See Also</span></span>  
 [<span data-ttu-id="cd6b3-169">AlwaysOn 可用性组 &#40;SQL Server 概述&#41;</span><span class="sxs-lookup"><span data-stu-id="cd6b3-169">Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](overview-of-always-on-availability-groups-sql-server.md)  
  
  
