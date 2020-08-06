---
title: 更改服务器实例的 HADR 群集上下文 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], WSFC clusters
- Availability replicas [SQL Server], change WSFC cluster context
ms.assetid: ecd99f91-b9a2-4737-994e-507065a12f80
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: cbc29fa2ebaaf2bbc9e577b5bd303e8a0dd0ec4c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693496"
---
# <a name="change-the-hadr-cluster-context-of-server-instance-sql-server"></a><span data-ttu-id="67998-102">更改服务器实例的 HADR 群集上下文 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="67998-102">Change the HADR Cluster Context of Server Instance (SQL Server)</span></span>
  <span data-ttu-id="67998-103">本主题介绍如何通过在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 和更高版本中使用 [!INCLUDE[tsql](../../../includes/tsql-md.md)] ，切换 [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] 实例的 HADR 群集上下文。</span><span class="sxs-lookup"><span data-stu-id="67998-103">This topic describes how to switch the HADR cluster context of an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by using [!INCLUDE[tsql](../../../includes/tsql-md.md)] in [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] and later versions.</span></span> <span data-ttu-id="67998-104">*HADR 群集上下文* 用于确定哪一 Windows Server 故障转移群集 (WSFC) 群集管理服务器实例所承载的可用性副本的元数据。</span><span class="sxs-lookup"><span data-stu-id="67998-104">The *HADR cluster context* determines which Windows Server Failover Clustering (WSFC) cluster manages the metadata for availability replicas hosted by the server instance.</span></span>  
  
 <span data-ttu-id="67998-105">仅在 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 跨群集迁移到新 WSFC 群集上的 [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] 实例的过程中切换 HADR 群集上下文。</span><span class="sxs-lookup"><span data-stu-id="67998-105">Switch the HADR cluster context only during a cross-cluster migration of [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] to an instance of [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] on a new WSFC cluster.</span></span> <span data-ttu-id="67998-106">[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 的跨群集迁移支持用最短的可用性组停机时间将操作系统升级到 [!INCLUDE[win8](../../../includes/win8-md.md)] 或 [!INCLUDE[win8srv](../../../includes/win8srv-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="67998-106">Cross-cluster migration of [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] supports OS upgrade to [!INCLUDE[win8](../../../includes/win8-md.md)] or [!INCLUDE[win8srv](../../../includes/win8srv-md.md)] with minimal downtime of availability groups.</span></span> <span data-ttu-id="67998-107">有关详细信息，请参阅[针对操作系统升级的 AlwaysOn 可用性组的跨群集迁移](https://msdn.microsoft.com/library/jj873730.aspx)。</span><span class="sxs-lookup"><span data-stu-id="67998-107">For more information, see [Cross-Cluster Migration of AlwaysOn Availability Groups for OS Upgrade](https://msdn.microsoft.com/library/jj873730.aspx).</span></span>  
  

  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="67998-108">开始之前</span><span class="sxs-lookup"><span data-stu-id="67998-108">Before You Begin</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="67998-109">仅在跨群集迁移 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 部署的过程中切换 HADR 群集上下文。</span><span class="sxs-lookup"><span data-stu-id="67998-109">Switch the HADR cluster context only during cross-cluster migration of [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] deployments.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="67998-110">限制和局限</span><span class="sxs-lookup"><span data-stu-id="67998-110">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="67998-111">您只能将 HADR 群集上下文从本地 WSFC 群集切换到远程群集，然后再从远程群集切换回本地群集。</span><span class="sxs-lookup"><span data-stu-id="67998-111">You can switch the HADR cluster context only from the local WSFC cluster to a remote cluster and then back from the remote cluster to the local cluster.</span></span> <span data-ttu-id="67998-112">不能将 HADR 群集上下文从一个远程群集切换到另一个远程群集。</span><span class="sxs-lookup"><span data-stu-id="67998-112">You cannot switch the HADR cluster context from one remote cluster to another remote cluster.</span></span>  
  
-   <span data-ttu-id="67998-113">只有在 SQL Server 实例不承载任何可用性副本时，才能将 HADR 群集上下文切换到远程群集。</span><span class="sxs-lookup"><span data-stu-id="67998-113">The HADR cluster context can be switched to a remote cluster only when the instance of SQL Server is not hosting any availability replicas.</span></span>  
  
-   <span data-ttu-id="67998-114">远程 HADR 群集上下文随时可以切换回本地群集。</span><span class="sxs-lookup"><span data-stu-id="67998-114">A remote HADR cluster context can be switched back to the local cluster at any time.</span></span> <span data-ttu-id="67998-115">但是，只要服务器实例承载任何可用性副本，该上下文将无法再进行切换。</span><span class="sxs-lookup"><span data-stu-id="67998-115">However, the context cannot be switched again as long as the server instance is hosting any availability replicas.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="67998-116">先决条件</span><span class="sxs-lookup"><span data-stu-id="67998-116">Prerequisites</span></span>  
  
-   <span data-ttu-id="67998-117">您对其更改 HADR 群集上下文的服务器实例必须正在运行 [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] 或更高版本（Enterprise Edition 或更高）。</span><span class="sxs-lookup"><span data-stu-id="67998-117">The server instance on which you change the HADR cluster context must be running [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] or above (Enterprise edition or above).</span></span>  
  
-   <span data-ttu-id="67998-118">必须为 AlwaysOn 启用该服务器实例。</span><span class="sxs-lookup"><span data-stu-id="67998-118">The server instance must be enabled for AlwaysOn.</span></span> <span data-ttu-id="67998-119">有关详细信息，请参阅[启用和禁用 AlwaysOn 可用性组 (SQL Server)](enable-and-disable-always-on-availability-groups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="67998-119">For more information, see [Enable and Disable AlwaysOn Availability Groups &#40;SQL Server&#41;](enable-and-disable-always-on-availability-groups-sql-server.md).</span></span>  
  
-   <span data-ttu-id="67998-120">为了符合从本地群集上下文切换到远程群集上下文的条件，服务器实例不能承载任何可用性副本。</span><span class="sxs-lookup"><span data-stu-id="67998-120">To be eligible to be switched from the local cluster context to a remote cluster cluster, a server instance cannot be hosting any availability replicas.</span></span> <span data-ttu-id="67998-121">[sys.availability_replicas](/sql/relational-databases/system-catalog-views/sys-availability-replicas-transact-sql) 目录视图不应返回任何行。</span><span class="sxs-lookup"><span data-stu-id="67998-121">The [sys.availability_replicas](/sql/relational-databases/system-catalog-views/sys-availability-replicas-transact-sql) catalog view should not return any rows.</span></span>  
  
     <span data-ttu-id="67998-122">如果在服务器实例上存在任何可用性副本，则您必须首先执行以下操作之一，然后才能更改 HADR 群集上下文：</span><span class="sxs-lookup"><span data-stu-id="67998-122">If any availability replicas exist on the server instance, before you can change the HADR cluster context, you must do one of the following:</span></span>  
  
    |<span data-ttu-id="67998-123">副本角色</span><span class="sxs-lookup"><span data-stu-id="67998-123">Replica Role</span></span>|<span data-ttu-id="67998-124">操作</span><span class="sxs-lookup"><span data-stu-id="67998-124">Action</span></span>|<span data-ttu-id="67998-125">链接</span><span class="sxs-lookup"><span data-stu-id="67998-125">Link</span></span>|  
    |------------------|------------|----------|  
    |<span data-ttu-id="67998-126">主</span><span class="sxs-lookup"><span data-stu-id="67998-126">Primary</span></span>|<span data-ttu-id="67998-127">使可用性组脱机。</span><span class="sxs-lookup"><span data-stu-id="67998-127">Take the availability group offline.</span></span>|[<span data-ttu-id="67998-128">使可用性组脱机 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="67998-128">Take an Availability Group Offline &#40;SQL Server&#41;</span></span>](../../take-an-availability-group-offline-sql-server.md)|  
    |<span data-ttu-id="67998-129">辅助副本</span><span class="sxs-lookup"><span data-stu-id="67998-129">Secondary</span></span>|<span data-ttu-id="67998-130">从其可用性组中删除副本</span><span class="sxs-lookup"><span data-stu-id="67998-130">Remove the replica from its availability group</span></span>|[<span data-ttu-id="67998-131">将次要副本从可用性组删除 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="67998-131">Remove a Secondary Replica from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-secondary-replica-from-an-availability-group-sql-server.md)|  
  
-   <span data-ttu-id="67998-132">在您可以从远程群集切换到本地群集之前，所有同步提交副本必须都处于 SYNCHRONIZED 状态。</span><span class="sxs-lookup"><span data-stu-id="67998-132">Before you can switch from a remote cluster to the local cluster, all synchronous-commit replicas must be SYNCHRONIZED.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="67998-133">建议</span><span class="sxs-lookup"><span data-stu-id="67998-133">Recommendations</span></span>  
  
-   <span data-ttu-id="67998-134">我们建议您指定完整的域名。</span><span class="sxs-lookup"><span data-stu-id="67998-134">We recommend that you specify the full domain name.</span></span> <span data-ttu-id="67998-135">这是因为为了找到短名称的目标 IP 地址，ALTER SERVER CONFIGURATION 使用 DNS 名称解析。</span><span class="sxs-lookup"><span data-stu-id="67998-135">This is because to find the target IP address of a short name, ALTER SERVER CONFIGURATION uses DNS resolution.</span></span> <span data-ttu-id="67998-136">在某些情况下，根据 DNS 搜索顺序，使用短名称可能会导致混淆。</span><span class="sxs-lookup"><span data-stu-id="67998-136">Under some situations, depending on the DNS searching order, using a short name could cause confusion.</span></span> <span data-ttu-id="67998-137">例如，考虑以下命令，该命令在 `abc` 域 (`node1.abc.com`) 中的节点上执行。</span><span class="sxs-lookup"><span data-stu-id="67998-137">For example, consider the following command, which is executed on a node in the `abc` domain, (`node1.abc.com`).</span></span> <span data-ttu-id="67998-138">意向的目标群集是 `CLUS01` 域 ( `xyz` ) 中的`clus01.xyz.com`群集。</span><span class="sxs-lookup"><span data-stu-id="67998-138">The intended destination cluster is the `CLUS01` cluster in the `xyz` domain (`clus01.xyz.com`).</span></span> <span data-ttu-id="67998-139">但是，本地域主机还承载名为 `CLUS01` (`clus01.abc.com`) 的一个群集。</span><span class="sxs-lookup"><span data-stu-id="67998-139">However, the local  domain hosts also hosts a cluster named `CLUS01` (`clus01.abc.com`).</span></span>  
  
     <span data-ttu-id="67998-140">如果已指定目标群集 `CLUS01`的短名称，则 DNS 名称解析可能会返回错误群集 `clus01.abc.com`的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="67998-140">If the short name of the target cluster, `CLUS01`, were specified, DNS name resolution could return the IP address of the wrong cluster, `clus01.abc.com`.</span></span> <span data-ttu-id="67998-141">为了避免此类混淆，请指定目标群集的完整名称，如下例中所示：</span><span class="sxs-lookup"><span data-stu-id="67998-141">To avoid such confusion, specify the full name of the target cluster, as in the following example:</span></span>  
  
    ```  
    ALTER SERVER CONFIGURATION SET HADR CLUSTER CONTEXT = 'clus01.xyz.com'  
    ```  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="67998-142">Security</span><span class="sxs-lookup"><span data-stu-id="67998-142">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="67998-143">权限</span><span class="sxs-lookup"><span data-stu-id="67998-143">Permissions</span></span>  
  
-   <span data-ttu-id="67998-144">**SQL Server 登录**</span><span class="sxs-lookup"><span data-stu-id="67998-144">**SQL Server login**</span></span>  
  
     <span data-ttu-id="67998-145">需要 CONTROL SERVER 权限。</span><span class="sxs-lookup"><span data-stu-id="67998-145">Requires CONTROL SERVER permission.</span></span>  
  
-   <span data-ttu-id="67998-146">**SQL Server 服务帐户**</span><span class="sxs-lookup"><span data-stu-id="67998-146">**SQL Server service account**</span></span>  
  
     <span data-ttu-id="67998-147">服务器实例的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服务帐户必须具有：</span><span class="sxs-lookup"><span data-stu-id="67998-147">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service account of the server instance must have:</span></span>  
  
    -   <span data-ttu-id="67998-148">打开目标 WSFC 群集的权限。</span><span class="sxs-lookup"><span data-stu-id="67998-148">Permission to open the destination WSFC cluster.</span></span>  
  
    -   <span data-ttu-id="67998-149">远程 WSFC 读写访问权限。</span><span class="sxs-lookup"><span data-stu-id="67998-149">Remote WSFC read-write access.</span></span>  
  
 
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="67998-150">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="67998-150">Using Transact-SQL</span></span>  
 <span data-ttu-id="67998-151">**更改可用性副本的 WSFC 群集上下文**</span><span class="sxs-lookup"><span data-stu-id="67998-151">**To change the WSFC cluster context of an availability replica**</span></span>  
  
1.  <span data-ttu-id="67998-152">连接到承载可用性组的主副本或辅助副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="67998-152">Connect to the server instance that hosts either the primary replica or a secondary replica of the availability group.</span></span>  
  
2.  <span data-ttu-id="67998-153">使用 [ALTER SERVER CONFIGURATION](/sql/t-sql/statements/alter-server-configuration-transact-sql) 语句的 SET HADR CLUSTER CONTEXT 子句，如下所示：</span><span class="sxs-lookup"><span data-stu-id="67998-153">Use the SET HADR CLUSTER CONTEXT clause of the [ALTER SERVER CONFIGURATION](/sql/t-sql/statements/alter-server-configuration-transact-sql) statement, as follows:</span></span>  
  
     <span data-ttu-id="67998-154">更改服务器配置集 HADR 群集上下文 **=** { **" *`windows_cluster`* "** |地方</span><span class="sxs-lookup"><span data-stu-id="67998-154">ALTER SERVER CONFIGURATION SET HADR CLUSTER CONTEXT **=** { **'*`windows_cluster`*'** | LOCAL }</span></span>  
  
     <span data-ttu-id="67998-155">其中：</span><span class="sxs-lookup"><span data-stu-id="67998-155">where,</span></span>  
  
     <span data-ttu-id="67998-156">*windows_cluster*</span><span class="sxs-lookup"><span data-stu-id="67998-156">*windows_cluster*</span></span>  
     <span data-ttu-id="67998-157">WSFC 群集的群集对象名称 (CON)。</span><span class="sxs-lookup"><span data-stu-id="67998-157">The cluster object name (CON) of a WSFC cluster.</span></span> <span data-ttu-id="67998-158">您可以指定短名称或者完整的域名称。</span><span class="sxs-lookup"><span data-stu-id="67998-158">You can specify either the short name or the full domain name.</span></span> <span data-ttu-id="67998-159">我们建议您指定完整的域名。</span><span class="sxs-lookup"><span data-stu-id="67998-159">We recommend that you specify the full domain name.</span></span> <span data-ttu-id="67998-160">有关详细信息，请参阅本主题前面的[建议](#Recommendations)。</span><span class="sxs-lookup"><span data-stu-id="67998-160">For more information, see [Recommendations](#Recommendations), earlier in this topic.</span></span>  
  
     <span data-ttu-id="67998-161">LOCAL</span><span class="sxs-lookup"><span data-stu-id="67998-161">LOCAL</span></span>  
     <span data-ttu-id="67998-162">本地 WSFC 群集。</span><span class="sxs-lookup"><span data-stu-id="67998-162">The local WSFC cluster.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="67998-163">示例</span><span class="sxs-lookup"><span data-stu-id="67998-163">Examples</span></span>  
 <span data-ttu-id="67998-164">下面的示例将 HADR 群集上下文更改为其他群集。</span><span class="sxs-lookup"><span data-stu-id="67998-164">The following example changes the HADR cluster context to a different cluster.</span></span> <span data-ttu-id="67998-165">若要标识目标 WSFC 群集 ( `clus01`)，本示例指定完整的群集对象名称 ( `clus01.xyz.com`)。</span><span class="sxs-lookup"><span data-stu-id="67998-165">To identify the destination WSFC cluster, `clus01`, the example specifies the full cluster object name, `clus01.xyz.com`.</span></span>  
  
```  
ALTER SERVER CONFIGURATION SET HADR CLUSTER CONTEXT = 'clus01.xyz.com';  
```  
  
 <span data-ttu-id="67998-166">下面的示例将 HADR 群集上下文更改为本地 WSFC 群集。</span><span class="sxs-lookup"><span data-stu-id="67998-166">The following example changes the HADR cluster context to the local WSFC cluster.</span></span>  
  
```  
ALTER SERVER CONFIGURATION SET HADR CLUSTER CONTEXT = LOCAL;  
```  
  

  
##  <a name="follow-up-after-switching-the-cluster-context-of-an-availability-replica"></a><a name="FollowUp"></a><span data-ttu-id="67998-167">跟进：在切换可用性副本的群集上下文后</span><span class="sxs-lookup"><span data-stu-id="67998-167">Follow Up: After Switching the Cluster Context of an Availability Replica</span></span>  
 <span data-ttu-id="67998-168">新的 HADR 群集上下文将立即生效，而不重新启动服务器实例。</span><span class="sxs-lookup"><span data-stu-id="67998-168">The new HADR cluster context takes effect immediately, without restarting the server instance.</span></span> <span data-ttu-id="67998-169">HADR 群集上下文设置是持久的实例级别设置，在服务器实例重新启动时也保持不变。</span><span class="sxs-lookup"><span data-stu-id="67998-169">The HADR cluster context setting is a persistent instance-level setting that remains unchanged if the server instance restarts.</span></span>  
  
 <span data-ttu-id="67998-170">通过查询 [sys.dm_hadr_cluster](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-transact-sql) 动态管理视图确认新的 HADR 群集上下文，如下所示：</span><span class="sxs-lookup"><span data-stu-id="67998-170">Confirm the new HADR cluster context by querying the [sys.dm_hadr_cluster](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-transact-sql) dynamic management view, as follows:</span></span>  
  
```  
SELECT cluster_name FROM sys.dm_hadr_cluster  
```  
  
 <span data-ttu-id="67998-171">此查询应返回为其设置 HADR 群集上下文的群集的名称。</span><span class="sxs-lookup"><span data-stu-id="67998-171">This query should return the name of the cluster to which you set the HADR cluster context.</span></span>  
  
 <span data-ttu-id="67998-172">在 HADR 群集上下文切换为新的群集时：</span><span class="sxs-lookup"><span data-stu-id="67998-172">When the HADR cluster context is switched to a new cluster:</span></span>  
  
-   <span data-ttu-id="67998-173">对于 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]的实例当前承载的任何可用性副本，将清除元数据。</span><span class="sxs-lookup"><span data-stu-id="67998-173">The metadata is cleaned up for any availability replicas that are currently hosted by the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="67998-174">以前属于可用性副本的所有数据库现在都处于 RESTORING 状态。</span><span class="sxs-lookup"><span data-stu-id="67998-174">All the databases that previously belonged to an availability replica are now in the RESTORING state.</span></span>  
  
 
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="67998-175">相关任务</span><span class="sxs-lookup"><span data-stu-id="67998-175">Related Tasks</span></span>  
  
-   [<span data-ttu-id="67998-176">删除可用性组侦听程序 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="67998-176">Remove an Availability Group Listener &#40;SQL Server&#41;</span></span>](remove-an-availability-group-listener-sql-server.md)  
  
-   [<span data-ttu-id="67998-177">使可用性组脱机 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="67998-177">Take an Availability Group Offline &#40;SQL Server&#41;</span></span>](../../take-an-availability-group-offline-sql-server.md)  
  
-   [<span data-ttu-id="67998-178">将辅助副本添加到可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="67998-178">Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="67998-179">将次要副本从可用性组删除 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="67998-179">Remove a Secondary Replica from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-secondary-replica-from-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="67998-180">创建或配置可用性组侦听程序 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="67998-180">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [<span data-ttu-id="67998-181">将辅助数据库联接到可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="67998-181">Join a Secondary Database to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
 
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="67998-182">相关内容</span><span class="sxs-lookup"><span data-stu-id="67998-182">Related Content</span></span>  
  
-   <span data-ttu-id="67998-183">[SQL Server 2012 技术文章](https://msdn.microsoft.com/library/bb418445\(SQL.10\).aspx)</span><span class="sxs-lookup"><span data-stu-id="67998-183">[SQL Server 2012 Technical Articles](https://msdn.microsoft.com/library/bb418445\(SQL.10\).aspx)</span></span>  
  
-   [<span data-ttu-id="67998-184">SQL Server AlwaysOn 团队博客：SQL Server AlwaysOn 官方团队博客</span><span class="sxs-lookup"><span data-stu-id="67998-184">SQL Server AlwaysOn Team Blog: The official SQL Server AlwaysOn Team Blog</span></span>](https://blogs.msdn.com/b/sqlalwayson/)  
  
  
  
## <a name="see-also"></a><span data-ttu-id="67998-185">另请参阅</span><span class="sxs-lookup"><span data-stu-id="67998-185">See Also</span></span>  
 <span data-ttu-id="67998-186">[AlwaysOn 可用性组 (SQL Server) ](always-on-availability-groups-sql-server.md) [Windows Server 故障转移群集 &#40;WSFC&#41; 与 SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="67998-186">[AlwaysOn Availability Groups (SQL Server)](always-on-availability-groups-sql-server.md) [Windows Server Failover Clustering &#40;WSFC&#41; with SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md) </span></span>  
 [<span data-ttu-id="67998-187">ALTER SERVER CONFIGURATION (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="67998-187">ALTER SERVER CONFIGURATION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-server-configuration-transact-sql)  
  
  
