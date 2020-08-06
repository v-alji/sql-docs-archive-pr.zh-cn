---
title: 一些可用性副本不具有正常运行的角色 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.agp6allroleshealthy.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 7ec5b337-7201-4a66-a541-7560f8b18784
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 801fe20edf6f2dbe09bc800722cf4210988ebc69
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586981"
---
# <a name="some-availability-replicas-do-not-have-a-healthy-role"></a><span data-ttu-id="0023f-102">一些可用性副本不具有正常运行的角色</span><span class="sxs-lookup"><span data-stu-id="0023f-102">Some availability replicas do not have a healthy role</span></span>
    
## <a name="introduction"></a><span data-ttu-id="0023f-103">简介</span><span class="sxs-lookup"><span data-stu-id="0023f-103">Introduction</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0023f-104">**策略名称**</span><span class="sxs-lookup"><span data-stu-id="0023f-104">**Policy Name**</span></span>|<span data-ttu-id="0023f-105">可用性副本角色状态</span><span class="sxs-lookup"><span data-stu-id="0023f-105">Availability Replicas Role State</span></span>|  
|<span data-ttu-id="0023f-106">**问题**</span><span class="sxs-lookup"><span data-stu-id="0023f-106">**Issue**</span></span>|<span data-ttu-id="0023f-107">一些可用性副本不具有正常运行的角色。</span><span class="sxs-lookup"><span data-stu-id="0023f-107">Some availability replicas do not have a healthy role.</span></span>|  
|<span data-ttu-id="0023f-108">**类别**</span><span class="sxs-lookup"><span data-stu-id="0023f-108">**Category**</span></span>|<span data-ttu-id="0023f-109">**警告**</span><span class="sxs-lookup"><span data-stu-id="0023f-109">**Warning**</span></span>|  
|<span data-ttu-id="0023f-110">**方面**</span><span class="sxs-lookup"><span data-stu-id="0023f-110">**Facet**</span></span>|<span data-ttu-id="0023f-111">可用性组 (availability group)</span><span class="sxs-lookup"><span data-stu-id="0023f-111">Availability group</span></span>|  
  
## <a name="description"></a><span data-ttu-id="0023f-112">说明</span><span class="sxs-lookup"><span data-stu-id="0023f-112">Description</span></span>  
 <span data-ttu-id="0023f-113">此策略将汇总所有可用性副本的连接状态，并且检查是否存在未处于正常运行角色的任何可用性副本。</span><span class="sxs-lookup"><span data-stu-id="0023f-113">This policy rolls up the connection state of all availability replicas and checks if there are any availability replicas that are not in a healthy role.</span></span> <span data-ttu-id="0023f-114">在有可用性副本既不是主副本也不是辅助副本时，此策略处于不正常状态。</span><span class="sxs-lookup"><span data-stu-id="0023f-114">The policy is in an unhealthy state when any availability replica is neither primary nor secondary.</span></span> <span data-ttu-id="0023f-115">否则，该策略处于正常状态。</span><span class="sxs-lookup"><span data-stu-id="0023f-115">The policy is otherwise in a healthy state.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0023f-116">对于此版本的 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]，与可能原因和解决方法有关的信息位于 TechNet Wiki 上的 [一些可用性副本不具有正常运行的角色](https://go.microsoft.com/fwlink/p/?LinkId=220854) 中。</span><span class="sxs-lookup"><span data-stu-id="0023f-116">For this release of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], information about possible causes and solutions is located at [Some availability replicas do not have a healthy role](https://go.microsoft.com/fwlink/p/?LinkId=220854) on the TechNet Wiki.</span></span>  
  
## <a name="possible-causes"></a><span data-ttu-id="0023f-117">可能的原因</span><span class="sxs-lookup"><span data-stu-id="0023f-117">Possible Causes</span></span>  
 <span data-ttu-id="0023f-118">在此可用性组中，至少一个可用性副本当前不具有主角色或辅助角色。</span><span class="sxs-lookup"><span data-stu-id="0023f-118">In this availability group, at least one availability replica does not currently have the primary or secondary role.</span></span>  
  
## <a name="possible-solution"></a><span data-ttu-id="0023f-119">可能的解决方法</span><span class="sxs-lookup"><span data-stu-id="0023f-119">Possible Solution</span></span>  
 <span data-ttu-id="0023f-120">使用可用性副本策略状态查找角色不是主副本或辅助副本的可用性副本，然后解决该可用性副本上的问题。</span><span class="sxs-lookup"><span data-stu-id="0023f-120">Use the availability replica policy state to find the availability replica whose role is not primary or secondary, and then resolve the issue at the availability replica.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0023f-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0023f-121">See Also</span></span>  
 <span data-ttu-id="0023f-122">[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="0023f-122">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="0023f-123">使用 AlwaysOn 面板 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="0023f-123">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
