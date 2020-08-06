---
title: 一些可用性副本未同步数据 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.agp4synchronizing.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 3db6a569-e942-4321-a0dd-c4ab002087c8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 762b7da1f7b8a07257c2a900307eb1bb10408653
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586982"
---
# <a name="some-availability-replicas-are-not-synchronizing-data"></a><span data-ttu-id="691ec-102">一些可用性副本未同步数据</span><span class="sxs-lookup"><span data-stu-id="691ec-102">Some availability replicas are not synchronizing data</span></span>
    
## <a name="introduction"></a><span data-ttu-id="691ec-103">简介</span><span class="sxs-lookup"><span data-stu-id="691ec-103">Introduction</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="691ec-104">**策略名称**</span><span class="sxs-lookup"><span data-stu-id="691ec-104">**Policy Name**</span></span>|<span data-ttu-id="691ec-105">可用性副本数据同步状态</span><span class="sxs-lookup"><span data-stu-id="691ec-105">Availability Replicas Data Synchronization State</span></span>|  
|<span data-ttu-id="691ec-106">**问题**</span><span class="sxs-lookup"><span data-stu-id="691ec-106">**Issue**</span></span>|<span data-ttu-id="691ec-107">一些可用性副本未同步数据。</span><span class="sxs-lookup"><span data-stu-id="691ec-107">Some availability replicas are not synchronizing data.</span></span>|  
|<span data-ttu-id="691ec-108">**类别**</span><span class="sxs-lookup"><span data-stu-id="691ec-108">**Category**</span></span>|<span data-ttu-id="691ec-109">**警告**</span><span class="sxs-lookup"><span data-stu-id="691ec-109">**Warning**</span></span>|  
|<span data-ttu-id="691ec-110">**方面**</span><span class="sxs-lookup"><span data-stu-id="691ec-110">**Facet**</span></span>|<span data-ttu-id="691ec-111">可用性组 (availability group)</span><span class="sxs-lookup"><span data-stu-id="691ec-111">Availability group</span></span>|  
  
## <a name="description"></a><span data-ttu-id="691ec-112">说明</span><span class="sxs-lookup"><span data-stu-id="691ec-112">Description</span></span>  
 <span data-ttu-id="691ec-113">此策略将汇总可用性组中所有可用性副本的数据同步状态，并且检查是否有可用性副本的同步未执行。</span><span class="sxs-lookup"><span data-stu-id="691ec-113">This policy rolls up the data synchronization state of all availability replicas in the availability group and checks if the synchronization of any availability replica is not operational.</span></span> <span data-ttu-id="691ec-114">如果可用性副本的任意数据同步状态为 NOT SYNCRONIZING，此策略处于不正常状态。</span><span class="sxs-lookup"><span data-stu-id="691ec-114">The policy is in an unhealthy state if any of the data synchronization states of the availability replica is NOT SYNCRONIZING.</span></span>  
  
 <span data-ttu-id="691ec-115">如果可用性副本的数据同步状态均不为 NOT SYNCRONIZING，则此策略处于正常状态。</span><span class="sxs-lookup"><span data-stu-id="691ec-115">This policy is in a healthy state if none of the data synchronization states of the availability replica is NOT SYNCHRONIZING.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="691ec-116">对于此版本的 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]，与可能原因和解决方法有关的信息位于 TechNet Wiki 上的 [一些可用性副本未同步数据](https://go.microsoft.com/fwlink/p/?LinkId=220852) 中。</span><span class="sxs-lookup"><span data-stu-id="691ec-116">For this release of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], information about possible causes and solutions is located at [Some availability replicas are not synchronizing data](https://go.microsoft.com/fwlink/p/?LinkId=220852) on the TechNet Wiki.</span></span>  
  
## <a name="possible-causes"></a><span data-ttu-id="691ec-117">可能的原因</span><span class="sxs-lookup"><span data-stu-id="691ec-117">Possible Causes</span></span>  
 <span data-ttu-id="691ec-118">在此可用性组中，至少一个辅助副本具有 NOT SYNCHRONIZING 同步状态，未从主副本接收数据。</span><span class="sxs-lookup"><span data-stu-id="691ec-118">In this availability group, at least one secondary replica has a NOT SYNCHRONIZING synchronization state and is not receiving data from the primary replica.</span></span>  
  
## <a name="possible-solution"></a><span data-ttu-id="691ec-119">可能的解决方法</span><span class="sxs-lookup"><span data-stu-id="691ec-119">Possible Solution</span></span>  
 <span data-ttu-id="691ec-120">使用可用性副本策略状态查找具有 NOT SYNCHROINIZING 状态的可用性副本，然后解决该可用性副本上的问题。</span><span class="sxs-lookup"><span data-stu-id="691ec-120">Use the availability replica policy state to find the availability replica with a NOT SYNCHROINIZING state, and then resolve the issue at the availability replica.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="691ec-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="691ec-121">See Also</span></span>  
 <span data-ttu-id="691ec-122">[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="691ec-122">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="691ec-123">使用 AlwaysOn 面板 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="691ec-123">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
