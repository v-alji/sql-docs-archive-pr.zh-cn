---
title: 更改可用性组脱机
description: 脱机设置 Always On 可用性组的步骤
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], take offline
ms.assetid: 50f5aad8-0dff-45ef-8350-f9596d3db898
author: rothja
ms.author: jroth
ms.openlocfilehash: db2f56befe6905b9c3de6bd1ab6a2e5a4a00b1b3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587576"
---
# <a name="take-an-availability-group-offline-sql-server"></a><span data-ttu-id="a79e8-103">使可用性组脱机 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="a79e8-103">Take an Availability Group Offline (SQL Server)</span></span>
  <span data-ttu-id="a79e8-104">本主题介绍如何在 [!INCLUDE[tsql](../includes/tsql-md.md)] 和更高版本中通过使用 [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)] ，将某一 AlwaysOn 可用性组从 ONLINE 状态转换为 OFFLINE 状态。</span><span class="sxs-lookup"><span data-stu-id="a79e8-104">This topic describes how to take an AlwaysOn availability group from the ONLINE state to the OFFLINE state by using [!INCLUDE[tsql](../includes/tsql-md.md)] in [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)] and later versions.</span></span> <span data-ttu-id="a79e8-105">对于同步提交数据库没有数据丢失，因为如果任何同步提交副本未同步，OFFLINE 操作将引发错误并且保持可用性组处于 ONLINE 状态。</span><span class="sxs-lookup"><span data-stu-id="a79e8-105">There is no data loss for synchronous-commit databases because if any synchronous-commit replica is not synchronized, the OFFLINE operation raises an error and leaves the availability group ONLINE.</span></span> <span data-ttu-id="a79e8-106">保持可用性组处于联机状态将保护未同步的同步提交数据库，以防可能的数据丢失。</span><span class="sxs-lookup"><span data-stu-id="a79e8-106">Keeping the availability group online protects unsynchronized synchronous-commit databases from possible data loss.</span></span> <span data-ttu-id="a79e8-107">可用性组脱机后，其数据库将不可用于客户端，并且您无法使可用性组重新联机。</span><span class="sxs-lookup"><span data-stu-id="a79e8-107">After an availability group goes offline, its databases become unavailable to clients and you cannot bring the availability group back online.</span></span> <span data-ttu-id="a79e8-108">因此，使某一可用性组处于脱机状态只会将该可用性组的资源从一个 WSFC 群集迁移到另一个 WSFC 群集。</span><span class="sxs-lookup"><span data-stu-id="a79e8-108">Therefore, take an availability group offline only to migrate the availability group resources from one WSFC cluster to another.</span></span>  
  
 <span data-ttu-id="a79e8-109">在 [!INCLUDE[ssHADR](../includes/sshadr-md.md)]的跨群集迁移过程中，如果任何应用程序直接连接到某一可用性组的主副本，则该可用性组必须置于脱机状态。</span><span class="sxs-lookup"><span data-stu-id="a79e8-109">During a cross-cluster migration of [!INCLUDE[ssHADR](../includes/sshadr-md.md)], if any applications connect directly to the primary replica of an availability group, the availability group must be taken offline.</span></span> <span data-ttu-id="a79e8-110">[!INCLUDE[ssHADR](../includes/sshadr-md.md)] 的跨群集迁移支持用最短的可用性组停机时间进行操作系统升级。</span><span class="sxs-lookup"><span data-stu-id="a79e8-110">Cross-cluster migration of [!INCLUDE[ssHADR](../includes/sshadr-md.md)] supports OS upgrade with minimal downtime of availability groups.</span></span> <span data-ttu-id="a79e8-111">典型的情形是将 [!INCLUDE[ssHADR](../includes/sshadr-md.md)] 的跨群集迁移用于升级到 [!INCLUDE[win8](../includes/win8-md.md)] 或 [!INCLUDE[win8srv](../includes/win8srv-md.md)]的操作系统升级。</span><span class="sxs-lookup"><span data-stu-id="a79e8-111">The typical scenario is to use cross-cluster migration of [!INCLUDE[ssHADR](../includes/sshadr-md.md)] for OS upgrade to [!INCLUDE[win8](../includes/win8-md.md)] or [!INCLUDE[win8srv](../includes/win8srv-md.md)].</span></span> <span data-ttu-id="a79e8-112">有关详细信息，请参阅[针对操作系统升级的 AlwaysOn 可用性组的跨群集迁移](https://msdn.microsoft.com/library/jj873730.aspx)。</span><span class="sxs-lookup"><span data-stu-id="a79e8-112">For more information, see [Cross-Cluster Migration of AlwaysOn Availability Groups for OS Upgrade](https://msdn.microsoft.com/library/jj873730.aspx).</span></span>  
  

  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a79e8-113">开始之前</span><span class="sxs-lookup"><span data-stu-id="a79e8-113">Before You Begin</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="a79e8-114">仅将 OFFLINE 选项用于可用性组资源的跨群集迁移。</span><span class="sxs-lookup"><span data-stu-id="a79e8-114">Use the OFFLINE option only for a cross-cluster migration of availability group resources.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="a79e8-115">先决条件</span><span class="sxs-lookup"><span data-stu-id="a79e8-115">Prerequisites</span></span>  
  
-   <span data-ttu-id="a79e8-116">您对其输入 OFFLINE 命令的服务器实例必须正在运行 [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)] 或更高版本（Enterprise Edition 或更高）。</span><span class="sxs-lookup"><span data-stu-id="a79e8-116">The server instance on which you enter the OFFLINE command must be running [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)] or above (Enterprise edition or above).</span></span>  
  
-   <span data-ttu-id="a79e8-117">可用性组当前必须处于联机状态。</span><span class="sxs-lookup"><span data-stu-id="a79e8-117">The availability group must currently be online.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="a79e8-118">建议</span><span class="sxs-lookup"><span data-stu-id="a79e8-118">Recommendations</span></span>  
 <span data-ttu-id="a79e8-119">在您使可用性组脱机之前，删除可用性组侦听器。</span><span class="sxs-lookup"><span data-stu-id="a79e8-119">Before you take the availability group offline, delete the availability group listener or listeners.</span></span> <span data-ttu-id="a79e8-120">有关详细信息，请参阅 [删除可用性组侦听程序 (SQL Server)](availability-groups/windows/remove-an-availability-group-listener-sql-server.md)的操作系统升级。</span><span class="sxs-lookup"><span data-stu-id="a79e8-120">For more information, see [Remove an Availability Group Listener &#40;SQL Server&#41;](availability-groups/windows/remove-an-availability-group-listener-sql-server.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="a79e8-121">Security</span><span class="sxs-lookup"><span data-stu-id="a79e8-121">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="a79e8-122">权限</span><span class="sxs-lookup"><span data-stu-id="a79e8-122">Permissions</span></span>  
 <span data-ttu-id="a79e8-123">对可用性组要求 ALTER AVAILABILITY GROUP 权限、CONTROL AVAILABILITY GROUP 权限、ALTER ANY AVAILABILITY GROUP 权限或 CONTROL SERVER 权限。</span><span class="sxs-lookup"><span data-stu-id="a79e8-123">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="a79e8-124">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a79e8-124">Using Transact-SQL</span></span>  
 <span data-ttu-id="a79e8-125">**使可用性组脱机**</span><span class="sxs-lookup"><span data-stu-id="a79e8-125">**To take an availability group offline**</span></span>  
  
1.  <span data-ttu-id="a79e8-126">连接到为可用性组承载可用性副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="a79e8-126">Connect to a server instance that hosts an availability replica for the availability group.</span></span> <span data-ttu-id="a79e8-127">此副本可以是主副本或辅助副本。</span><span class="sxs-lookup"><span data-stu-id="a79e8-127">This replica can be the primary replica or a secondary replica.</span></span>  
  
2.  <span data-ttu-id="a79e8-128">按如下所示使用 [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) 语句：</span><span class="sxs-lookup"><span data-stu-id="a79e8-128">Use the [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) statement, as follows:</span></span>  
  
     <span data-ttu-id="a79e8-129">ALTER AVAILABILITY GROUP *group_name* OFFLINE</span><span class="sxs-lookup"><span data-stu-id="a79e8-129">ALTER AVAILABILITY GROUP *group_name* OFFLINE</span></span>  
  
     <span data-ttu-id="a79e8-130">其中， *group_name* 是可用性组的名称。</span><span class="sxs-lookup"><span data-stu-id="a79e8-130">where *group_name* is the name of the availability group.</span></span>  
  
### <a name="example"></a><span data-ttu-id="a79e8-131">示例</span><span class="sxs-lookup"><span data-stu-id="a79e8-131">Example</span></span>  
 <span data-ttu-id="a79e8-132">下面的示例将 `AccountsAG` 可用性组脱机。</span><span class="sxs-lookup"><span data-stu-id="a79e8-132">The following example takes the `AccountsAG` availability group offline.</span></span>  
  
```sql
ALTER AVAILABILITY GROUP AccountsAG OFFLINE;  
```  
  
##  <a name="follow-up-after-the-availability-group-goes-offline"></a><a name="FollowUp"></a> <span data-ttu-id="a79e8-133">跟进：在可用性组处于脱机状态后</span><span class="sxs-lookup"><span data-stu-id="a79e8-133">Follow Up: After the Availability Group Goes Offline</span></span>  
  
-   <span data-ttu-id="a79e8-134">**OFFLINE 操作的日志记录：** 启动了 OFFLINE 操作的 WSFC 节点的标识存储于 WSFC 群集日志和 SQL ERRORLOG 中。</span><span class="sxs-lookup"><span data-stu-id="a79e8-134">**Logging of OFFLINE operation:**  The identity of the WSFC node where the OFFLINE operation was initiated is stored in both the WSFC cluster log and the SQL ERRORLOG.</span></span>  
  
-   <span data-ttu-id="a79e8-135">**如果在使组脱机之前未删除可用性组侦听程序：** 如果要将可用性组迁移到其他 WSFC 群集，请删除其侦听器的 VNN 和 VIP。</span><span class="sxs-lookup"><span data-stu-id="a79e8-135">**If you did not delete the availability group listener before taking the group offline:**  If you are migrating the availability group to another WSFC cluster, delete the VNN and VIP of the listener.</span></span> <span data-ttu-id="a79e8-136">你可以通过使用故障转移群集管理控制台、 [Remove-ClusterResource](https://technet.microsoft.com/library/ee461015\(WS.10\).aspx) PowerShell cmdlet 或 [cluster.exe](https://technet.microsoft.com/library/ee461015\(WS.10\).aspx)删除侦听程序的 VNN 和 VIP。</span><span class="sxs-lookup"><span data-stu-id="a79e8-136">You can delete them by using either the Failover Cluster Management console, the [Remove-ClusterResource](https://technet.microsoft.com/library/ee461015\(WS.10\).aspx) PowerShell cmdlet, or [cluster.exe](https://technet.microsoft.com/library/ee461015\(WS.10\).aspx).</span></span> <span data-ttu-id="a79e8-137">请注意，在 Windows 8 上不推荐使用 cluster.exe。</span><span class="sxs-lookup"><span data-stu-id="a79e8-137">Note that cluster.exe is deprecated on Windows 8.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="a79e8-138">相关任务</span><span class="sxs-lookup"><span data-stu-id="a79e8-138">Related Tasks</span></span>  
  
-   [<span data-ttu-id="a79e8-139">删除可用性组侦听程序 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="a79e8-139">Remove an Availability Group Listener &#40;SQL Server&#41;</span></span>](availability-groups/windows/remove-an-availability-group-listener-sql-server.md)  
  
-   [<span data-ttu-id="a79e8-140">更改服务器实例的 HADR 群集上下文 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="a79e8-140">Change the HADR Cluster Context of Server Instance &#40;SQL Server&#41;</span></span>](availability-groups/windows/change-the-hadr-cluster-context-of-server-instance-sql-server.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="a79e8-141">相关内容</span><span class="sxs-lookup"><span data-stu-id="a79e8-141">Related Content</span></span>  
  
-   <span data-ttu-id="a79e8-142">[SQL Server 2012 技术文章](https://msdn.microsoft.com/library/bb418445\(SQL.10\).aspx)</span><span class="sxs-lookup"><span data-stu-id="a79e8-142">[SQL Server 2012 Technical Articles](https://msdn.microsoft.com/library/bb418445\(SQL.10\).aspx)</span></span>  
  
-   [<span data-ttu-id="a79e8-143">SQL Server AlwaysOn 团队博客：SQL Server AlwaysOn 官方团队博客</span><span class="sxs-lookup"><span data-stu-id="a79e8-143">SQL Server AlwaysOn Team Blog: The official SQL Server AlwaysOn Team Blog</span></span>](https://blogs.msdn.com/b/sqlalwayson/)  
  
## <a name="see-also"></a><span data-ttu-id="a79e8-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a79e8-144">See Also</span></span>  
 [<span data-ttu-id="a79e8-145">AlwaysOn 可用性组 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a79e8-145">AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](availability-groups/windows/always-on-availability-groups-sql-server.md)  
