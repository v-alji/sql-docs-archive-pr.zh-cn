---
title: 断开可用性副本的连接 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.arp2connected.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 1a2162d3-54fb-4356-b349-effbdc15a5a4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1db92b8e73b6daaee7edf5042b1d73cfeb471d1d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690151"
---
# <a name="availability-replica-is-disconnected"></a><span data-ttu-id="6683a-102">断开可用性副本的连接</span><span class="sxs-lookup"><span data-stu-id="6683a-102">Availability replica is disconnected</span></span>
    
## <a name="introduction"></a><span data-ttu-id="6683a-103">简介</span><span class="sxs-lookup"><span data-stu-id="6683a-103">Introduction</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6683a-104">**策略名称**</span><span class="sxs-lookup"><span data-stu-id="6683a-104">**Policy Name**</span></span>|<span data-ttu-id="6683a-105">可用性副本连接状态</span><span class="sxs-lookup"><span data-stu-id="6683a-105">Availability Replica Connection State</span></span>|  
|<span data-ttu-id="6683a-106">**问题**</span><span class="sxs-lookup"><span data-stu-id="6683a-106">**Issue**</span></span>|<span data-ttu-id="6683a-107">断开可用性副本的连接。</span><span class="sxs-lookup"><span data-stu-id="6683a-107">Availability replica is disconnected.</span></span>|  
|<span data-ttu-id="6683a-108">**类别**</span><span class="sxs-lookup"><span data-stu-id="6683a-108">**Category**</span></span>|<span data-ttu-id="6683a-109">**严重**</span><span class="sxs-lookup"><span data-stu-id="6683a-109">**Critical**</span></span>|  
|<span data-ttu-id="6683a-110">**方面**</span><span class="sxs-lookup"><span data-stu-id="6683a-110">**Facet**</span></span>|<span data-ttu-id="6683a-111">可用性副本</span><span class="sxs-lookup"><span data-stu-id="6683a-111">Availability replica</span></span>|  
  
## <a name="description"></a><span data-ttu-id="6683a-112">说明</span><span class="sxs-lookup"><span data-stu-id="6683a-112">Description</span></span>  
 <span data-ttu-id="6683a-113">此策略检查可用性副本之间的连接状态。</span><span class="sxs-lookup"><span data-stu-id="6683a-113">This policy checks the connection state between availability replicas.</span></span> <span data-ttu-id="6683a-114">当可用性副本的连接状态为 DISCONNECTED 时，此策略处于不正常状态。</span><span class="sxs-lookup"><span data-stu-id="6683a-114">The policy is in an unhealthy state when the connection state of the availability replica is DISCONNECTED.</span></span> <span data-ttu-id="6683a-115">否则，该策略处于正常状态。</span><span class="sxs-lookup"><span data-stu-id="6683a-115">The policy is otherwise in a healthy state.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6683a-116"> 对于此版本的 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]，与可能原因和解决方法有关的信息位于 TechNet Wiki 上的 [断开可用性副本的连接](https://go.microsoft.com/fwlink/p/?LinkId=220857) 中。</span><span class="sxs-lookup"><span data-stu-id="6683a-116">For this release of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], information about possible causes and solutions is located at [Availability replica is disconnected](https://go.microsoft.com/fwlink/p/?LinkId=220857) on the TechNet Wiki.</span></span>  
  
## <a name="possible-causes"></a><span data-ttu-id="6683a-117">可能的原因</span><span class="sxs-lookup"><span data-stu-id="6683a-117">Possible Causes</span></span>  
 <span data-ttu-id="6683a-118">辅助副本未连接到主副本。</span><span class="sxs-lookup"><span data-stu-id="6683a-118">The secondary replica is not connected to the primary replica.</span></span> <span data-ttu-id="6683a-119">连接状态为 DISCONNECTED。</span><span class="sxs-lookup"><span data-stu-id="6683a-119">The connected state is DISCONNECTED.</span></span> <span data-ttu-id="6683a-120">此问题可能由以下原因导致：</span><span class="sxs-lookup"><span data-stu-id="6683a-120">This issue can be caused by the following:</span></span>  
  
-   <span data-ttu-id="6683a-121">连接端口可能与另一个应用程序冲突。</span><span class="sxs-lookup"><span data-stu-id="6683a-121">The connection port might be in conflict with another application.</span></span>  
  
-   <span data-ttu-id="6683a-122">加密类型或算法不匹配。</span><span class="sxs-lookup"><span data-stu-id="6683a-122">The encryption type or algorithm is mismatched.</span></span>  
  
-   <span data-ttu-id="6683a-123">连接端点已被删除或尚未启动。</span><span class="sxs-lookup"><span data-stu-id="6683a-123">The connection endpoint has been deleted or has not been started.</span></span>  
  
-   <span data-ttu-id="6683a-124">传输已断开连接。</span><span class="sxs-lookup"><span data-stu-id="6683a-124">The transport is disconnected.</span></span>  
  
## <a name="possible-solutions"></a><span data-ttu-id="6683a-125">可能的解决方法</span><span class="sxs-lookup"><span data-stu-id="6683a-125">Possible Solutions</span></span>  
 <span data-ttu-id="6683a-126">以下是此问题的可能解决方法：</span><span class="sxs-lookup"><span data-stu-id="6683a-126">Following are possible solutions for this issue:</span></span>  
  
-   <span data-ttu-id="6683a-127">检查主副本和辅助副本实例的数据库镜像端点配置，并更新不匹配的配置。</span><span class="sxs-lookup"><span data-stu-id="6683a-127">Check the database mirroring endpoint configuration for the instances of the primary and secondary replica and update the mismatched configuration.</span></span>  
  
-   <span data-ttu-id="6683a-128">检查端口是否冲突，如果冲突，请更改端口号。</span><span class="sxs-lookup"><span data-stu-id="6683a-128">Check if the port is conflicting, and if so, change the port number.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6683a-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6683a-129">See Also</span></span>  
 <span data-ttu-id="6683a-130">[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6683a-130">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="6683a-131">使用 AlwaysOn 面板 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="6683a-131">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
