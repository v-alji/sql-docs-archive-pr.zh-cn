---
title: 可用性组未准备好进行自动故障转移 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.agp3autofailover.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 28261014-342c-442a-bd89-6d04b8d4e8b7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2995ddec51cd70d8a3f209229d0ecb9b0132c79e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577867"
---
# <a name="availability-group-is-not-ready-for-automatic-failover"></a><span data-ttu-id="0a32b-102">可用性组未准备好进行自动故障转移</span><span class="sxs-lookup"><span data-stu-id="0a32b-102">Availability group is not ready for automatic failover</span></span>
    
## <a name="introduction"></a><span data-ttu-id="0a32b-103">简介</span><span class="sxs-lookup"><span data-stu-id="0a32b-103">Introduction</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0a32b-104">**策略名称**</span><span class="sxs-lookup"><span data-stu-id="0a32b-104">**Policy Name**</span></span>|<span data-ttu-id="0a32b-105">可用性组自动故障转移就绪</span><span class="sxs-lookup"><span data-stu-id="0a32b-105">Availability Group Automatic Failover Readiness</span></span>|  
|<span data-ttu-id="0a32b-106">**问题**</span><span class="sxs-lookup"><span data-stu-id="0a32b-106">**Issue**</span></span>|<span data-ttu-id="0a32b-107">可用性组未准备好进行自动故障转移。</span><span class="sxs-lookup"><span data-stu-id="0a32b-107">Availability group is not ready for automatic failover.</span></span>|  
|<span data-ttu-id="0a32b-108">**类别**</span><span class="sxs-lookup"><span data-stu-id="0a32b-108">**Category**</span></span>|<span data-ttu-id="0a32b-109">**严重**</span><span class="sxs-lookup"><span data-stu-id="0a32b-109">**Critical**</span></span>|  
|<span data-ttu-id="0a32b-110">**方面**</span><span class="sxs-lookup"><span data-stu-id="0a32b-110">**Facet**</span></span>|<span data-ttu-id="0a32b-111">可用性组 (availability group)</span><span class="sxs-lookup"><span data-stu-id="0a32b-111">Availability group</span></span>|  
  
## <a name="description"></a><span data-ttu-id="0a32b-112">说明</span><span class="sxs-lookup"><span data-stu-id="0a32b-112">Description</span></span>  
 <span data-ttu-id="0a32b-113">此策略检查验证可用性组是否至少具有一个故障转移就绪的辅助副本。</span><span class="sxs-lookup"><span data-stu-id="0a32b-113">This policy checks to verify that the availability group has at least one secondary replica that is failover ready.</span></span> <span data-ttu-id="0a32b-114">当主副本的故障转移模式为自动但是可用性组中没有故障转移就绪的辅助副本时，此策略处于不正常状态并引发警报。</span><span class="sxs-lookup"><span data-stu-id="0a32b-114">The policy is in an unhealthy state and an alert is raised when the failover mode of the primary replica is automatic, however none of the secondary replicas in the availability group are failover ready.</span></span>  
  
 <span data-ttu-id="0a32b-115">当至少一个辅助副本的自动故障转移就绪时，此策略处于正常状态。</span><span class="sxs-lookup"><span data-stu-id="0a32b-115">The policy is in a healthy state when at least one secondary replica is automatic failover ready.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0a32b-116">对于此版本的 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]，与可能原因和解决方法有关的信息位于 TechNet Wiki 上的 [可用性组未准备好进行自动故障转移](https://go.microsoft.com/fwlink/p/?LinkId=220851) 中。</span><span class="sxs-lookup"><span data-stu-id="0a32b-116">For this release of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], information about possible causes and solutions is located at [Availability group is not ready for automatic failover](https://go.microsoft.com/fwlink/p/?LinkId=220851) on the TechNet Wiki.</span></span>  
  
## <a name="possible-causes"></a><span data-ttu-id="0a32b-117">可能的原因</span><span class="sxs-lookup"><span data-stu-id="0a32b-117">Possible Causes</span></span>  
 <span data-ttu-id="0a32b-118">可用性组未准备好进行自动故障转移。</span><span class="sxs-lookup"><span data-stu-id="0a32b-118">The availability group is not ready for automatic failover.</span></span> <span data-ttu-id="0a32b-119">将主副本配置为自动故障转移，但是辅助副本未准备好进行自动故障转移。</span><span class="sxs-lookup"><span data-stu-id="0a32b-119">The primary replica is configured for automatic failover; however, the secondary replica is not ready for automatic failover.</span></span> <span data-ttu-id="0a32b-120">为自动故障转移配置的辅助副本可能不可用或其数据同步状态当前不是 SYNCHRONIZED。</span><span class="sxs-lookup"><span data-stu-id="0a32b-120">The secondary replica that is configured for automatic failover might be unavailable or its data synchronization state is currently not SYNCHRONIZED.</span></span>  
  
## <a name="possible-solutions"></a><span data-ttu-id="0a32b-121">可能的解决方法</span><span class="sxs-lookup"><span data-stu-id="0a32b-121">Possible Solutions</span></span>  
 <span data-ttu-id="0a32b-122">以下是此问题的可能解决方法：</span><span class="sxs-lookup"><span data-stu-id="0a32b-122">Following are possible solutions for this issue:</span></span>  
  
-   <span data-ttu-id="0a32b-123">验证至少将一个辅助副本配置为自动故障转移。</span><span class="sxs-lookup"><span data-stu-id="0a32b-123">Verify that at least one secondary replica is configured as automatic failover.</span></span> <span data-ttu-id="0a32b-124">如果没有一个辅助副本被配置为自动故障转移，请将辅助副本的配置更新为具有异步提交功能的自动故障转移目标。</span><span class="sxs-lookup"><span data-stu-id="0a32b-124">If there is not a secondary replica configured as automatic failover, update the configuration of a secondary replica to be the automatic failover target with synchronous commit.</span></span>  
  
-   <span data-ttu-id="0a32b-125">使用此策略验证数据是否处于同步状态以及自动故障转移目标是否 SYNCHRONIZED，然后解决可用性副本的问题。</span><span class="sxs-lookup"><span data-stu-id="0a32b-125">Use the policy to verify that the data is in a synchronization state and the automatic failover target is SYNCHRONIZED, and then resolve the issue at the availability replica.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a32b-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0a32b-126">See Also</span></span>  
 <span data-ttu-id="0a32b-127">[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="0a32b-127">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="0a32b-128">使用 AlwaysOn 面板 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="0a32b-128">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
