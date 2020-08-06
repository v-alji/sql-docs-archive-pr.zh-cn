---
title: 一些同步副本不同步 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.agp5synchronized.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: e58ed56e-4c30-42e6-a9fc-a8c401620e02
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ecef2d16e80e128834a71e1f1f112096f8ccc9cb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586976"
---
# <a name="some-synchronous-replicas-are-not-synchronized"></a><span data-ttu-id="90eb9-102">一些同步副本不同步</span><span class="sxs-lookup"><span data-stu-id="90eb9-102">Some synchronous replicas are not synchronized</span></span>
    
## <a name="introduction"></a><span data-ttu-id="90eb9-103">简介</span><span class="sxs-lookup"><span data-stu-id="90eb9-103">Introduction</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="90eb9-104">**策略名称**</span><span class="sxs-lookup"><span data-stu-id="90eb9-104">**Policy Name**</span></span>|<span data-ttu-id="90eb9-105">同步副本数据同步状态</span><span class="sxs-lookup"><span data-stu-id="90eb9-105">Synchronous Replicas Data Synchronization State</span></span>|  
|<span data-ttu-id="90eb9-106">**问题**</span><span class="sxs-lookup"><span data-stu-id="90eb9-106">**Issue**</span></span>|<span data-ttu-id="90eb9-107">一些同步副本不同步。</span><span class="sxs-lookup"><span data-stu-id="90eb9-107">Some synchronous replicas are not synchronized.</span></span>|  
|<span data-ttu-id="90eb9-108">**类别**</span><span class="sxs-lookup"><span data-stu-id="90eb9-108">**Category**</span></span>|<span data-ttu-id="90eb9-109">**警告**</span><span class="sxs-lookup"><span data-stu-id="90eb9-109">**Warning**</span></span>|  
|<span data-ttu-id="90eb9-110">**方面**</span><span class="sxs-lookup"><span data-stu-id="90eb9-110">**Facet**</span></span>|<span data-ttu-id="90eb9-111">可用性组 (availability group)</span><span class="sxs-lookup"><span data-stu-id="90eb9-111">Availability group</span></span>|  
  
## <a name="description"></a><span data-ttu-id="90eb9-112">说明</span><span class="sxs-lookup"><span data-stu-id="90eb9-112">Description</span></span>  
 <span data-ttu-id="90eb9-113">此策略将汇总所有可用性副本的数据同步状态，并且检查是否存在未处于预期同步状态的任何可用性副本。</span><span class="sxs-lookup"><span data-stu-id="90eb9-113">This policy rolls up the data synchronization state of all availability replicas and checks for any availability replicas that are not in the expected synchronization state.</span></span> <span data-ttu-id="90eb9-114">在任何异步副本未处于 SYNCHRONIZING 状态以及任何同步副本未处于 SYNCHRONIZED 状态时，该策略处于不正常状态。</span><span class="sxs-lookup"><span data-stu-id="90eb9-114">The policy is in an unhealthy state when any asynchronous replica is not in a SYNCHRONIZING state and any synchronous replica is not in a SYNCHRONIZED state.</span></span> <span data-ttu-id="90eb9-115">否则，策略状态为正常。</span><span class="sxs-lookup"><span data-stu-id="90eb9-115">The policy state is otherwise healthy.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="90eb9-116">对于此版本的 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]，与可能原因和解决方法有关的信息位于 TechNet Wiki 上的 [某些同步副本未同步](https://go.microsoft.com/fwlink/p/?LinkId=220853) 中。</span><span class="sxs-lookup"><span data-stu-id="90eb9-116">For this release of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], information about possible causes and solutions is located at [Some synchronous replicas are not synchronized](https://go.microsoft.com/fwlink/p/?LinkId=220853) on the TechNet Wiki.</span></span>  
  
## <a name="possible-causes"></a><span data-ttu-id="90eb9-117">可能的原因</span><span class="sxs-lookup"><span data-stu-id="90eb9-117">Possible Causes</span></span>  
 <span data-ttu-id="90eb9-118">在该可用性组中，至少一个同步副本当前未同步。</span><span class="sxs-lookup"><span data-stu-id="90eb9-118">In this availability group, at least one synchronous replica is not currently synchronized.</span></span> <span data-ttu-id="90eb9-119">副本同步状态可以是 SYNCHONIZING 或 SYNCHRONIZING。</span><span class="sxs-lookup"><span data-stu-id="90eb9-119">The replica synchronization state could be either SYNCHONIZING or NOT SYNCHRONIZING.</span></span>  
  
## <a name="possible-solution"></a><span data-ttu-id="90eb9-120">可能的解决方法</span><span class="sxs-lookup"><span data-stu-id="90eb9-120">Possible Solution</span></span>  
 <span data-ttu-id="90eb9-121">使用可用性副本策略状态可以找到具有错误同步状态的可用性副本，然后解决该可用性副本上的问题。</span><span class="sxs-lookup"><span data-stu-id="90eb9-121">Use the availability replica policy state to find the availability replica with the incorrect synchronization state, and then resolve the issue at the availability replica.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90eb9-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="90eb9-122">See Also</span></span>  
 <span data-ttu-id="90eb9-123">[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="90eb9-123">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="90eb9-124">使用 AlwaysOn 面板 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="90eb9-124">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
