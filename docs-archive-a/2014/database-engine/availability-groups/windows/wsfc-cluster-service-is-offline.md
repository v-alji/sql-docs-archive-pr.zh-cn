---
title: WSFC 群集服务处于脱机状态 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.agp1WSFCquorum.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: d502548d-ece6-4a42-9ded-2157d33e3d21
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e6e7b48f96eb09638291b1d0655d385d606b1666
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690146"
---
# <a name="wsfc-cluster-service-is-offline"></a><span data-ttu-id="fa677-102">WSFC 群集服务处于脱机状态</span><span class="sxs-lookup"><span data-stu-id="fa677-102">WSFC cluster service is offline</span></span>
    
## <a name="introduction"></a><span data-ttu-id="fa677-103">简介</span><span class="sxs-lookup"><span data-stu-id="fa677-103">Introduction</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fa677-104">**策略名称**</span><span class="sxs-lookup"><span data-stu-id="fa677-104">**Policy Name**</span></span>|<span data-ttu-id="fa677-105">WSFC 群集状态</span><span class="sxs-lookup"><span data-stu-id="fa677-105">WSFC Cluster State</span></span>|  
|<span data-ttu-id="fa677-106">**问题**</span><span class="sxs-lookup"><span data-stu-id="fa677-106">**Issue**</span></span>|<span data-ttu-id="fa677-107">WSFC 群集服务处于脱机状态。</span><span class="sxs-lookup"><span data-stu-id="fa677-107">WSFC cluster service is offline.</span></span>|  
|<span data-ttu-id="fa677-108">**类别**</span><span class="sxs-lookup"><span data-stu-id="fa677-108">**Category**</span></span>|<span data-ttu-id="fa677-109">**严重**</span><span class="sxs-lookup"><span data-stu-id="fa677-109">**Critical**</span></span>|  
|<span data-ttu-id="fa677-110">**方面**</span><span class="sxs-lookup"><span data-stu-id="fa677-110">**Facet**</span></span>|<span data-ttu-id="fa677-111">SQL Server 实例</span><span class="sxs-lookup"><span data-stu-id="fa677-111">Instance of SQL Server</span></span>|  
  
## <a name="description"></a><span data-ttu-id="fa677-112">说明</span><span class="sxs-lookup"><span data-stu-id="fa677-112">Description</span></span>  
 <span data-ttu-id="fa677-113">此策略检查 Windows Server 故障转移群集 (WSFC) 的状态。</span><span class="sxs-lookup"><span data-stu-id="fa677-113">This policy checks the state of the Windows Server Failover Cluster (WSFC).</span></span> <span data-ttu-id="fa677-114">此策略处于不正常状态，在 WSFC 群集处于脱机状态或者处于强制仲裁状态时将引发警报。</span><span class="sxs-lookup"><span data-stu-id="fa677-114">The policy is in an unhealthy state and an alert is raised when the WSFC cluster is offline or in the forced quorum state.</span></span> <span data-ttu-id="fa677-115">此群集中承载的所有可用性组处于脱机状态或者需要灾难恢复操作。</span><span class="sxs-lookup"><span data-stu-id="fa677-115">All availability groups hosted within this cluster are offline or a disaster recovery action is required.</span></span>  
  
 <span data-ttu-id="fa677-116">在群集状态为正常仲裁时，此群集状态是正常的。</span><span class="sxs-lookup"><span data-stu-id="fa677-116">The policy state is healthy when the cluster state is in the normal quorum.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fa677-117">对于此版本的 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]，与可能原因和解决方法有关的信息位于 TechNet Wiki 上的 [WSFC 群集服务处于脱机状态](https://go.microsoft.com/fwlink/p/?LinkId=220849) 中。</span><span class="sxs-lookup"><span data-stu-id="fa677-117">For this release of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], information about possible causes and solutions is located at [WSFC cluster service is offline](https://go.microsoft.com/fwlink/p/?LinkId=220849) on the TechNet Wiki.</span></span>  
  
## <a name="possible-causes"></a><span data-ttu-id="fa677-118">可能的原因</span><span class="sxs-lookup"><span data-stu-id="fa677-118">Possible Causes</span></span>  
 <span data-ttu-id="fa677-119">此问题可能是由于群集服务问题或在群集中缺少仲裁导致的。</span><span class="sxs-lookup"><span data-stu-id="fa677-119">This issue can be caused by a cluster service issue or by the loss of the quorum in the cluster.</span></span>  
  
## <a name="possible-solution"></a><span data-ttu-id="fa677-120">可能的解决方法</span><span class="sxs-lookup"><span data-stu-id="fa677-120">Possible Solution</span></span>  
 <span data-ttu-id="fa677-121">使用群集管理器工具可执行强制仲裁或灾难恢复工作流。</span><span class="sxs-lookup"><span data-stu-id="fa677-121">Use the Cluster Administrator tool to perform the forced quorum or disaster recovery workflow.</span></span> <span data-ttu-id="fa677-122">如果您通过执行强制仲裁或灾难恢复无法解决该问题，请与您的群集管理员联系以便帮助解决此问题。</span><span class="sxs-lookup"><span data-stu-id="fa677-122">If you cannot resolve the issue by performing the forced quorum or disaster recovery, contact your cluster administrator to help resolve this issue.</span></span> <span data-ttu-id="fa677-123">有关详细信息，请参阅 [联机丛书中的](../../../sql-server/failover-clusters/windows/force-a-wsfc-cluster-to-start-without-a-quorum.md) 在无仲裁情况下强制启动 WSFC 群集 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="fa677-123">For more information, see [Force a WSFC Cluster to Start Without a Quorum](../../../sql-server/failover-clusters/windows/force-a-wsfc-cluster-to-start-without-a-quorum.md) in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa677-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fa677-124">See Also</span></span>  
 <span data-ttu-id="fa677-125">[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="fa677-125">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="fa677-126">使用 AlwaysOn 面板 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="fa677-126">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
