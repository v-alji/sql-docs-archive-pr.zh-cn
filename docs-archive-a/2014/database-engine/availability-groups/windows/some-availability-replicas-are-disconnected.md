---
title: 断开一些可用性副本的连接 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.agp7allconnected.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: aea808be-6f0f-40c2-9aa2-a2a435ec6443
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1bb6535b513770b9b4718a0e8372c0a5bc3cba84
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586985"
---
# <a name="some-availability-replicas-are-disconnected"></a><span data-ttu-id="866f1-102">断开一些可用性副本的连接</span><span class="sxs-lookup"><span data-stu-id="866f1-102">Some availability replicas are disconnected</span></span>
    
## <a name="introduction"></a><span data-ttu-id="866f1-103">简介</span><span class="sxs-lookup"><span data-stu-id="866f1-103">Introduction</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="866f1-104">**策略名称**</span><span class="sxs-lookup"><span data-stu-id="866f1-104">**Policy Name**</span></span>|<span data-ttu-id="866f1-105">可用性副本连接状态</span><span class="sxs-lookup"><span data-stu-id="866f1-105">Availability Replicas Connection State</span></span>|  
|<span data-ttu-id="866f1-106">**问题**</span><span class="sxs-lookup"><span data-stu-id="866f1-106">**Issue**</span></span>|<span data-ttu-id="866f1-107">断开一些可用性副本的连接。</span><span class="sxs-lookup"><span data-stu-id="866f1-107">Some availability replicas are disconnected.</span></span>|  
|<span data-ttu-id="866f1-108">**类别**</span><span class="sxs-lookup"><span data-stu-id="866f1-108">**Category**</span></span>|<span data-ttu-id="866f1-109">**警告**</span><span class="sxs-lookup"><span data-stu-id="866f1-109">**Warning**</span></span>|  
|<span data-ttu-id="866f1-110">**方面**</span><span class="sxs-lookup"><span data-stu-id="866f1-110">**Facet**</span></span>|<span data-ttu-id="866f1-111">可用性组 (availability group)</span><span class="sxs-lookup"><span data-stu-id="866f1-111">Availability group</span></span>|  
  
## <a name="description"></a><span data-ttu-id="866f1-112">说明</span><span class="sxs-lookup"><span data-stu-id="866f1-112">Description</span></span>  
 <span data-ttu-id="866f1-113">此策略将汇总所有可用性副本的连接状态，并且检查是否存在处于 DISCONENCTED 状态的任何可用性副本。</span><span class="sxs-lookup"><span data-stu-id="866f1-113">This policy rolls up the connection state of all availability replicas and checks for any availability replicas that are DISCONENCTED.</span></span> <span data-ttu-id="866f1-114">当任何可用性副本处于 DISCONNECTED 状态时，此策略处于不正常状态。</span><span class="sxs-lookup"><span data-stu-id="866f1-114">The policy is in an unhealthy state when any availability replica is DISCONNECTED.</span></span> <span data-ttu-id="866f1-115">否则，该策略处于正常状态。</span><span class="sxs-lookup"><span data-stu-id="866f1-115">The policy is otherwise in a healthy state.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="866f1-116"> 对于此版本的 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]，与可能原因和解决方法有关的信息位于 TechNet Wiki 上的 [断开一些可用性副本的连接](https://go.microsoft.com/fwlink/p/?LinkId=220855) 中。</span><span class="sxs-lookup"><span data-stu-id="866f1-116">For this release of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], information about possible causes and solutions is located at [Some availability replicas are disconnected](https://go.microsoft.com/fwlink/p/?LinkId=220855) on the TechNet Wiki.</span></span>  
  
## <a name="possible-causes"></a><span data-ttu-id="866f1-117">可能的原因</span><span class="sxs-lookup"><span data-stu-id="866f1-117">Possible Causes</span></span>  
 <span data-ttu-id="866f1-118">在此可用性组中，至少一个辅助副本未连接到主副本。</span><span class="sxs-lookup"><span data-stu-id="866f1-118">In this availability group, at least one secondary replica is not connected to the primary replica.</span></span> <span data-ttu-id="866f1-119">连接状态为 DISCONNECTED。</span><span class="sxs-lookup"><span data-stu-id="866f1-119">The connected state is DISCONNECTED.</span></span>  
  
## <a name="possible-solution"></a><span data-ttu-id="866f1-120">可能的解决方法</span><span class="sxs-lookup"><span data-stu-id="866f1-120">Possible Solution</span></span>  
 <span data-ttu-id="866f1-121">使用可用性副本策略状态查找处于 DISCONNECTED 状态的可用性副本，然后解决该可用性副本上的问题。</span><span class="sxs-lookup"><span data-stu-id="866f1-121">Use the availability replica policy state to find the availability replica that is DISCONNECTED, and then resolve the issue at the availability replica.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="866f1-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="866f1-122">See Also</span></span>  
 <span data-ttu-id="866f1-123">[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="866f1-123">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="866f1-124">使用 AlwaysOn 面板 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="866f1-124">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
