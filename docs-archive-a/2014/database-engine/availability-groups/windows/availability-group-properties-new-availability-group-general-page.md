---
title: 可用性组属性和新的可用性组 (常规页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroupproperties.general.f1
ms.assetid: 9af5379f-91b8-4729-9f75-4a80242a30e9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 876b9d0948b7cd0d01c21b0ec1d64c51a55fa157
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577853"
---
# <a name="availability-group-properties-and-new-availability-group-general-page"></a><span data-ttu-id="7660e-102">可用性组属性和新建可用性组（“常规”页）</span><span class="sxs-lookup"><span data-stu-id="7660e-102">Availability Group Properties and New Availability Group (General Page)</span></span>
  <span data-ttu-id="7660e-103">本主题同时适用于 **“新建可用性组”** 对话框和 **“可用性组属性”** 对话框的 **“常规”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="7660e-103">This topic applies to the **General** tab of both the **New Availability Group** dialog box and the **Availability Group Properties** dialog box.</span></span>  <span data-ttu-id="7660e-104">**“新建可用性组”** 对话框支持您无需使用 [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)]即创建新的可用性组。</span><span class="sxs-lookup"><span data-stu-id="7660e-104">The **New Availability Group** dialog box enables you to create a new availability group without using the [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)].</span></span> <span data-ttu-id="7660e-105">**“可用性组属性”** 对话框支持您查看和修改现有的可用性组的配置。</span><span class="sxs-lookup"><span data-stu-id="7660e-105">The **Availability Group Properties** dialog box enables you to view and alter the configuration of an existing availability group.</span></span>  
  
 <span data-ttu-id="7660e-106">**查看可用性组属性**</span><span class="sxs-lookup"><span data-stu-id="7660e-106">**To view availability group properties**</span></span>  
  
-   [<span data-ttu-id="7660e-107">查看可用性组属性 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="7660e-107">View Availability Group Properties &#40;SQL Server&#41;</span></span>](view-availability-group-properties-sql-server.md)  
  
-   [<span data-ttu-id="7660e-108">使用 AlwaysOn 面板 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="7660e-108">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
## <a name="ui-element-list"></a><span data-ttu-id="7660e-109">UI 元素列表</span><span class="sxs-lookup"><span data-stu-id="7660e-109">UI element list</span></span>  
 <span data-ttu-id="7660e-110">**可用性组名称**</span><span class="sxs-lookup"><span data-stu-id="7660e-110">**Availability group name**</span></span>  
 <span data-ttu-id="7660e-111">可用性组的名称。</span><span class="sxs-lookup"><span data-stu-id="7660e-111">Name of the availability group.</span></span> <span data-ttu-id="7660e-112">这是在 Windows Server 故障转移群集 (WSFC) 内必须唯一的用户指定的名称。</span><span class="sxs-lookup"><span data-stu-id="7660e-112">This is a user-specified name that must be unique within the Windows Server Failover Cluster (WSFC).</span></span>  
  
## <a name="availability-databases"></a><span data-ttu-id="7660e-113">可用性数据库</span><span class="sxs-lookup"><span data-stu-id="7660e-113">Availability Databases</span></span>  
 <span data-ttu-id="7660e-114">**Database Name**</span><span class="sxs-lookup"><span data-stu-id="7660e-114">**Database Name**</span></span>  
 <span data-ttu-id="7660e-115">已添加到可用性组中的数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="7660e-115">Name of a database that has been added to the availability group.</span></span>  
  
 <span data-ttu-id="7660e-116">**添加**</span><span class="sxs-lookup"><span data-stu-id="7660e-116">**Add**</span></span>  
 <span data-ttu-id="7660e-117">单击此选项可将数据库添加到可用性组。</span><span class="sxs-lookup"><span data-stu-id="7660e-117">Click to add a database to the availability group.</span></span>  
  
 <span data-ttu-id="7660e-118">**删除**</span><span class="sxs-lookup"><span data-stu-id="7660e-118">**Remove**</span></span>  
 <span data-ttu-id="7660e-119">单击此选项可从可用性组中删除所选数据库。</span><span class="sxs-lookup"><span data-stu-id="7660e-119">Click to remove a selected database from the availability group.</span></span>  
  
## <a name="availability-replicas"></a><span data-ttu-id="7660e-120">可用性副本</span><span class="sxs-lookup"><span data-stu-id="7660e-120">Availability Replicas</span></span>  
 <span data-ttu-id="7660e-121">**服务器实例**</span><span class="sxs-lookup"><span data-stu-id="7660e-121">**Server instance**</span></span>  
 <span data-ttu-id="7660e-122">承载此副本的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例的服务器名称；对于非默认实例，则为其实例名称。</span><span class="sxs-lookup"><span data-stu-id="7660e-122">Server name of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that is hosting this replica and, for a non-default instance, its instance name.</span></span>  
  
 <span data-ttu-id="7660e-123">**角色**</span><span class="sxs-lookup"><span data-stu-id="7660e-123">**Role**</span></span>  
 <span data-ttu-id="7660e-124">**主要节点**</span><span class="sxs-lookup"><span data-stu-id="7660e-124">**Primary**</span></span>  
 <span data-ttu-id="7660e-125">当前主副本。</span><span class="sxs-lookup"><span data-stu-id="7660e-125">Currently the primary replica.</span></span>  
  
 <span data-ttu-id="7660e-126">**辅助节点**</span><span class="sxs-lookup"><span data-stu-id="7660e-126">**Secondary**</span></span>  
 <span data-ttu-id="7660e-127">当前辅助副本。</span><span class="sxs-lookup"><span data-stu-id="7660e-127">Currently a secondary replica.</span></span>  
  
 <span data-ttu-id="7660e-128">**正在解析**</span><span class="sxs-lookup"><span data-stu-id="7660e-128">**Resolving**</span></span>  
 <span data-ttu-id="7660e-129">当前该副本角色处于正在解析为主角色或辅助角色的进程中。</span><span class="sxs-lookup"><span data-stu-id="7660e-129">Currently the replica role is in the process of being resolved to either the primary or secondary role.</span></span>  
  
 <span data-ttu-id="7660e-130">**可用性模式**</span><span class="sxs-lookup"><span data-stu-id="7660e-130">**Availability Mode**</span></span>  
 <span data-ttu-id="7660e-131">副本的可用性模式，可为下列值之一：</span><span class="sxs-lookup"><span data-stu-id="7660e-131">The availability mode of the replica, one of:</span></span>  
  
 <span data-ttu-id="7660e-132">**异步提交**</span><span class="sxs-lookup"><span data-stu-id="7660e-132">**Asynchronous commit**</span></span>  
 <span data-ttu-id="7660e-133">主副本可以不必等待辅助副本将日志写入磁盘，即可提交事务。</span><span class="sxs-lookup"><span data-stu-id="7660e-133">The primary replica can commit transactions without waiting for the secondary to write the log to disk.</span></span>  
  
 <span data-ttu-id="7660e-134">**同步提交**</span><span class="sxs-lookup"><span data-stu-id="7660e-134">**Synchronous commit**</span></span>  
 <span data-ttu-id="7660e-135">主副本等待提交给定的事务，直到辅助副本将事务写入磁盘。</span><span class="sxs-lookup"><span data-stu-id="7660e-135">The primary replica waits to commit a given transaction until the secondary replica has written the transaction to disk.</span></span>  
  
 <span data-ttu-id="7660e-136">有关详细信息，请参阅[可用性模式 (AlwaysOn 可用性组) ](availability-modes-always-on-availability-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="7660e-136">For more information, see [Availability Modes (AlwaysOn Availability Groups)](availability-modes-always-on-availability-groups.md).</span></span>  
  
 <span data-ttu-id="7660e-137">**故障转移模式**</span><span class="sxs-lookup"><span data-stu-id="7660e-137">**Failover Mode**</span></span>  
 <span data-ttu-id="7660e-138">副本的故障转移模式，可为下列值之一：</span><span class="sxs-lookup"><span data-stu-id="7660e-138">The failover mode of the replica, one of:</span></span>  
  
 <span data-ttu-id="7660e-139">**自动**</span><span class="sxs-lookup"><span data-stu-id="7660e-139">**Automatic**</span></span>  
 <span data-ttu-id="7660e-140">自动故障转移。</span><span class="sxs-lookup"><span data-stu-id="7660e-140">Automatic failover.</span></span> <span data-ttu-id="7660e-141">副本为自动故障转移的目标。</span><span class="sxs-lookup"><span data-stu-id="7660e-141">The replica is a target for automatic failovers.</span></span> <span data-ttu-id="7660e-142">仅当可用性模式设置为同步提交时，才选择此选项。</span><span class="sxs-lookup"><span data-stu-id="7660e-142">This is supported only if the availability mode is set to synchronous commit.</span></span>  
  
 <span data-ttu-id="7660e-143">**手动**</span><span class="sxs-lookup"><span data-stu-id="7660e-143">**Manual**</span></span>  
 <span data-ttu-id="7660e-144">手动故障转移。</span><span class="sxs-lookup"><span data-stu-id="7660e-144">Manual failover.</span></span> <span data-ttu-id="7660e-145">副本仅能由数据库管理员手动进行故障转移。</span><span class="sxs-lookup"><span data-stu-id="7660e-145">The replica can only be failed over to manually by the database administrator.</span></span>  
  
 <span data-ttu-id="7660e-146">**主角色中的连接**</span><span class="sxs-lookup"><span data-stu-id="7660e-146">**Connections in Primary Role**</span></span>  
 <span data-ttu-id="7660e-147">当副本拥有主角色时支持的客户端连接类型。</span><span class="sxs-lookup"><span data-stu-id="7660e-147">The type of client connections supported when the replica owns the primary role.</span></span>  
  
 <span data-ttu-id="7660e-148">**允许所有连接**</span><span class="sxs-lookup"><span data-stu-id="7660e-148">**Allow all connections**</span></span>  
 <span data-ttu-id="7660e-149">主副本中的数据库允许所有连接。</span><span class="sxs-lookup"><span data-stu-id="7660e-149">All connections are allowed to the databases in the primary replica.</span></span> <span data-ttu-id="7660e-150">这是默认设置。</span><span class="sxs-lookup"><span data-stu-id="7660e-150">This is the default setting.</span></span>  
  
 <span data-ttu-id="7660e-151">**允许读/写连接**</span><span class="sxs-lookup"><span data-stu-id="7660e-151">**Allow read/write connections**</span></span>  
 <span data-ttu-id="7660e-152">不允许 Application Intent 连接属性设置为 **ReadOnly** 的连接。</span><span class="sxs-lookup"><span data-stu-id="7660e-152">Connections where the Application Intent connection property is set to **ReadOnly** are disallowed.</span></span> <span data-ttu-id="7660e-153">在 Application Intent 属性设置为 **ReadWrite** 或者未设置 Application Intent 连接属性时，将允许连接。</span><span class="sxs-lookup"><span data-stu-id="7660e-153">When the Application Intent property is set to **ReadWrite** or the Application Intent connection property is not set, the connection is allowed.</span></span> <span data-ttu-id="7660e-154">有关 Application Intent 连接属性的详细信息，请参阅 [Using Connection String Keywords with SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)。</span><span class="sxs-lookup"><span data-stu-id="7660e-154">For more information about Application Intent connection property, see [Using Connection String Keywords with SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).</span></span>  
  
 <span data-ttu-id="7660e-155">**可读取辅助角色**</span><span class="sxs-lookup"><span data-stu-id="7660e-155">**Readable Secondary**</span></span>  
 <span data-ttu-id="7660e-156">正在履行辅助角色的可用性副本（也就是辅助副本）是否可以接受来自客户端的连接，可为下列值之一：</span><span class="sxs-lookup"><span data-stu-id="7660e-156">Whether an availability replica that is performing the secondary role (that is, a secondary replica) can accept connections from clients, one of:</span></span>  
  
 <span data-ttu-id="7660e-157">**是**</span><span class="sxs-lookup"><span data-stu-id="7660e-157">**No**</span></span>  
 <span data-ttu-id="7660e-158">不允许与此副本的辅助数据库的直接连接。</span><span class="sxs-lookup"><span data-stu-id="7660e-158">No direct connections are allowed to secondary databases of this replica.</span></span> <span data-ttu-id="7660e-159">它们不可用于读访问。</span><span class="sxs-lookup"><span data-stu-id="7660e-159">They are not available for read access.</span></span> <span data-ttu-id="7660e-160">这是默认设置。</span><span class="sxs-lookup"><span data-stu-id="7660e-160">This is the default setting.</span></span>  
  
 <span data-ttu-id="7660e-161">**仅限读意向**</span><span class="sxs-lookup"><span data-stu-id="7660e-161">**Read-intent only**</span></span>  
 <span data-ttu-id="7660e-162">仅允许与此副本的辅助数据库的直接只读连接。</span><span class="sxs-lookup"><span data-stu-id="7660e-162">Only direct read-only connections are allowed to secondary databases of this replica.</span></span> <span data-ttu-id="7660e-163">辅助数据库全都可用于读访问。</span><span class="sxs-lookup"><span data-stu-id="7660e-163">The secondary database(s) are all available for read access.</span></span>  
  
 <span data-ttu-id="7660e-164">**是**</span><span class="sxs-lookup"><span data-stu-id="7660e-164">**Yes**</span></span>  
 <span data-ttu-id="7660e-165">允许与此副本的辅助数据库的所有连接，但仅限读访问。</span><span class="sxs-lookup"><span data-stu-id="7660e-165">All connections are allowed to secondary databases of this replica, but only for read access.</span></span> <span data-ttu-id="7660e-166">辅助数据库全都可用于读访问。</span><span class="sxs-lookup"><span data-stu-id="7660e-166">The secondary database(s) are all available for read access.</span></span>  
  
 <span data-ttu-id="7660e-167">**会话超时（秒）**</span><span class="sxs-lookup"><span data-stu-id="7660e-167">**Session Timeout (seconds)**</span></span>  
 <span data-ttu-id="7660e-168">此副本上会话超时期限的秒数。</span><span class="sxs-lookup"><span data-stu-id="7660e-168">The number of seconds for the session-timeout period on this replica.</span></span>  
  
 <span data-ttu-id="7660e-169">**端点 URL**</span><span class="sxs-lookup"><span data-stu-id="7660e-169">**Endpoint URL**</span></span>  
 <span data-ttu-id="7660e-170">端点的 URL。</span><span class="sxs-lookup"><span data-stu-id="7660e-170">The URL of the endpoint.</span></span> <span data-ttu-id="7660e-171">有关这些 URL 格式的信息，请参阅[在添加或修改可用性副本时指定终结点 URL (SQL Server)](specify-endpoint-url-adding-or-modifying-availability-replica.md)。</span><span class="sxs-lookup"><span data-stu-id="7660e-171">For information the format of these URLs, see [Specify the Endpoint URL When Adding or Modifying an Availability Replica &#40;SQL Server&#41;](specify-endpoint-url-adding-or-modifying-availability-replica.md).</span></span>  
  
 <span data-ttu-id="7660e-172">**添加**</span><span class="sxs-lookup"><span data-stu-id="7660e-172">**Add**</span></span>  
 <span data-ttu-id="7660e-173">单击此选项可将辅助副本添加到可用性组。</span><span class="sxs-lookup"><span data-stu-id="7660e-173">Click to add a secondary replica to the availability group.</span></span>  
  
 <span data-ttu-id="7660e-174">**删除**</span><span class="sxs-lookup"><span data-stu-id="7660e-174">**Remove**</span></span>  
 <span data-ttu-id="7660e-175">单击此选项可从可用性组中删除辅助副本。</span><span class="sxs-lookup"><span data-stu-id="7660e-175">Click to remove a secondary replica from the availability group.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7660e-176">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7660e-176">See Also</span></span>  
 [<span data-ttu-id="7660e-177">AlwaysOn 可用性组 &#40;SQL Server 概述&#41;</span><span class="sxs-lookup"><span data-stu-id="7660e-177">Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](overview-of-always-on-availability-groups-sql-server.md)  
  
  
