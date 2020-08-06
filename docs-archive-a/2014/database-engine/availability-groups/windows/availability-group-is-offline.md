---
title: 可用性组处于脱机状态 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.agp2online.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 093c5208-bf7a-49f4-a546-72b48197cadf
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b25e5b22a09783c8dfcad862500b5c0dfcb2c319
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577864"
---
# <a name="availability-group-is-offline"></a><span data-ttu-id="b4f2e-102">可用性组处于脱机状态</span><span class="sxs-lookup"><span data-stu-id="b4f2e-102">Availability group is offline</span></span>
    
## <a name="introduction"></a><span data-ttu-id="b4f2e-103">简介</span><span class="sxs-lookup"><span data-stu-id="b4f2e-103">Introduction</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b4f2e-104">**策略名称**</span><span class="sxs-lookup"><span data-stu-id="b4f2e-104">**Policy Name**</span></span>|<span data-ttu-id="b4f2e-105">可用性组联机状态</span><span class="sxs-lookup"><span data-stu-id="b4f2e-105">Availability Group Online State</span></span>|  
|<span data-ttu-id="b4f2e-106">**问题**</span><span class="sxs-lookup"><span data-stu-id="b4f2e-106">**Issue**</span></span>|<span data-ttu-id="b4f2e-107">可用性组处于脱机状态。</span><span class="sxs-lookup"><span data-stu-id="b4f2e-107">Availability group is offline.</span></span>|  
|<span data-ttu-id="b4f2e-108">**类别**</span><span class="sxs-lookup"><span data-stu-id="b4f2e-108">**Category**</span></span>|<span data-ttu-id="b4f2e-109">**严重**</span><span class="sxs-lookup"><span data-stu-id="b4f2e-109">**Critical**</span></span>|  
|<span data-ttu-id="b4f2e-110">**方面**</span><span class="sxs-lookup"><span data-stu-id="b4f2e-110">**Facet**</span></span>|<span data-ttu-id="b4f2e-111">可用性组 (availability group)</span><span class="sxs-lookup"><span data-stu-id="b4f2e-111">Availability group</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b4f2e-112">说明</span><span class="sxs-lookup"><span data-stu-id="b4f2e-112">Description</span></span>  
 <span data-ttu-id="b4f2e-113">此策略检查可用性组的联机或脱机状态。</span><span class="sxs-lookup"><span data-stu-id="b4f2e-113">This policy checks the online or offline state of the availability group.</span></span> <span data-ttu-id="b4f2e-114">当可用性组的群集资源处于脱机状态或可用性组不具有主副本时，此策略处于不正常状态并引发警报。</span><span class="sxs-lookup"><span data-stu-id="b4f2e-114">The policy is in an unhealthy state and an alert is raised when the cluster resource of the availability group is offline or the availability group does not have a primary replica.</span></span>  
  
 <span data-ttu-id="b4f2e-115">当可用性组的群集资源处于联机状态并且可用性组具有主副本时，此策略处于正常状态。</span><span class="sxs-lookup"><span data-stu-id="b4f2e-115">The policy state is healthy when the cluster resource of the availability group is online and the availability group has a primary replica.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b4f2e-116"> 对于此版本的 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]，与可能原因和解决方法有关的信息位于 TechNet Wiki 上的 [可用性组处于脱机状态](https://go.microsoft.com/fwlink/p/?LinkId=220850) 中。</span><span class="sxs-lookup"><span data-stu-id="b4f2e-116">For this release of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], information about possible causes and solutions is located at [Availability group is offline](https://go.microsoft.com/fwlink/p/?LinkId=220850) on the TechNet Wiki.</span></span>  
  
## <a name="possible-causes"></a><span data-ttu-id="b4f2e-117">可能的原因</span><span class="sxs-lookup"><span data-stu-id="b4f2e-117">Possible Causes</span></span>  
 <span data-ttu-id="b4f2e-118">此问题可能由承载主副本的服务器实例中的失败或 Windows Server 故障转移群集 (WSFC) 可用性组资源脱机引起。</span><span class="sxs-lookup"><span data-stu-id="b4f2e-118">This issue can be caused by a failure in the server instance that hosts the primary replica or by the Windows Server Failover Cluster (WSFC) availability group resource going offline.</span></span> <span data-ttu-id="b4f2e-119">可用性组脱机可能有以下原因：</span><span class="sxs-lookup"><span data-stu-id="b4f2e-119">Following are possible causes for the availability group to be offline:</span></span>  
  
-   <span data-ttu-id="b4f2e-120">可用性组未配置为自动故障转移模式。</span><span class="sxs-lookup"><span data-stu-id="b4f2e-120">The availability group is not configured with automatic failover mode.</span></span> <span data-ttu-id="b4f2e-121">主副本变为不可用且可用性组中所有副本的角色变为 RESOLVING。</span><span class="sxs-lookup"><span data-stu-id="b4f2e-121">The primary replica becomes unavailable and the role of all replicas in the availability group become RESOLVING.</span></span>  
  
    -   <span data-ttu-id="b4f2e-122">主副本实例服务已关闭或停止响应。</span><span class="sxs-lookup"><span data-stu-id="b4f2e-122">The primary replica instance service is down or unresponsive.</span></span>  
  
    -   <span data-ttu-id="b4f2e-123">可用性组与群集的连接有问题。</span><span class="sxs-lookup"><span data-stu-id="b4f2e-123">The availability group has a connectivity issue with the cluster.</span></span>  
  
-   <span data-ttu-id="b4f2e-124">可用性组配置为自动故障转移模式，但是未成功完成。</span><span class="sxs-lookup"><span data-stu-id="b4f2e-124">The availability group is configured with automatic failover mode and does not complete successfully.</span></span>  
  
    -   <span data-ttu-id="b4f2e-125">在自动故障转移期间，对目标副本的主副本就绪检查失败，并且没有副本可以变为新的主副本。</span><span class="sxs-lookup"><span data-stu-id="b4f2e-125">During the automatic failover, the primary readiness check on the target replica fails, and there is no replica available to become the new primary.</span></span>  
  
-   <span data-ttu-id="b4f2e-126">群集中的可用性组资源变为脱机状态。</span><span class="sxs-lookup"><span data-stu-id="b4f2e-126">The availability group resource in the cluster becomes offline.</span></span>  
  
    -   <span data-ttu-id="b4f2e-127">任何依赖的群集资源遇到严重问题并变为脱机状态。</span><span class="sxs-lookup"><span data-stu-id="b4f2e-127">Any dependent cluster resource encounters a critical issue and becomes offline.</span></span> <span data-ttu-id="b4f2e-128">可用性组资源还处于脱机状态，直到依赖的资源变为联机状态。</span><span class="sxs-lookup"><span data-stu-id="b4f2e-128">The availability group resource is also offline until the dependent resource becomes online.</span></span>  
  
    -   <span data-ttu-id="b4f2e-129">群集中的严重问题导致禁用了可用性组资源。</span><span class="sxs-lookup"><span data-stu-id="b4f2e-129">A critical issue in the cluster turns off the availability group resource.</span></span>  
  
-   <span data-ttu-id="b4f2e-130">对可用性组存在正在进行的自动、手动或强制故障转移。</span><span class="sxs-lookup"><span data-stu-id="b4f2e-130">There is an automatic, manual, or forced failover in progress for the availability group.</span></span>  
  
## <a name="possible-solutions"></a><span data-ttu-id="b4f2e-131">可能的解决方法</span><span class="sxs-lookup"><span data-stu-id="b4f2e-131">Possible Solutions</span></span>  
 <span data-ttu-id="b4f2e-132">以下是此问题的可能解决方法：</span><span class="sxs-lookup"><span data-stu-id="b4f2e-132">Following are possible solutions for this issue:</span></span>  
  
-   <span data-ttu-id="b4f2e-133">如果主副本的 SQL Server 实例关闭，请重新启动服务器，然后验证可用性组恢复到正常状态。</span><span class="sxs-lookup"><span data-stu-id="b4f2e-133">If the SQL Server instance of the primary replica is down, restart the server and then verify that the availability group recovers to a healthy state.</span></span>  
  
-   <span data-ttu-id="b4f2e-134">如果自动故障转移失败，请验证副本上的数据库与以前已知的主副本同步，然后故障转移到主副本。</span><span class="sxs-lookup"><span data-stu-id="b4f2e-134">If the automatic failover appears to have failed, verify that the databases on the replica are synchronized with the previously known primary replica, and then failover to the primary replica.</span></span> <span data-ttu-id="b4f2e-135">如果数据库不同步，请选择数据丢失最少的副本，然后恢复到故障转移模式。</span><span class="sxs-lookup"><span data-stu-id="b4f2e-135">If the databases are not synchronized, select a replica with a minimum loss of data, and then recover to failover mode.</span></span>  
  
-   <span data-ttu-id="b4f2e-136">如果群集中的资源在 SQL Server 实例处于正常状态时脱机，请使用故障转移群集管理器检查群集运行状况或服务器上的其他群集问题。</span><span class="sxs-lookup"><span data-stu-id="b4f2e-136">If the resource in the cluster is offline while the instances of SQL Server appear to be healthy, use Failover Cluster Manager to check the cluster health or other cluster issues on the server.</span></span> <span data-ttu-id="b4f2e-137">您还可以使用故障转移群集管理器尝试将可用性组资源联机。</span><span class="sxs-lookup"><span data-stu-id="b4f2e-137">You can also use the Failover Cluster Manager to attempt to turn the availability group resource online.</span></span>  
  
-   <span data-ttu-id="b4f2e-138">如果正在进行故障转移，请等待故障转移完成。</span><span class="sxs-lookup"><span data-stu-id="b4f2e-138">If there is a failover in progress, wait for the failover to complete.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4f2e-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b4f2e-139">See Also</span></span>  
 <span data-ttu-id="b4f2e-140">[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="b4f2e-140">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="b4f2e-141">使用 AlwaysOn 面板 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="b4f2e-141">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
