---
title: 可用性数据库的数据同步状态不正常 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.arp3datasynchealthy.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 4fd003e7-808e-4b0e-b28a-47d9f2616f06
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a179008c20b108a2f6aaefd5dd80b22708e94a8b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694561"
---
# <a name="data-synchronization-state-of-availability-database-is-not-healthy"></a><span data-ttu-id="a8c73-102">可用性数据库的数据同步状态不正常</span><span class="sxs-lookup"><span data-stu-id="a8c73-102">Data synchronization state of availability database is not healthy</span></span>
    
## <a name="introduction"></a><span data-ttu-id="a8c73-103">简介</span><span class="sxs-lookup"><span data-stu-id="a8c73-103">Introduction</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a8c73-104">**策略名称**</span><span class="sxs-lookup"><span data-stu-id="a8c73-104">**Policy Name**</span></span>|<span data-ttu-id="a8c73-105">可用性数据库数据同步状态</span><span class="sxs-lookup"><span data-stu-id="a8c73-105">Availability Database Data Synchronization State</span></span>|  
|<span data-ttu-id="a8c73-106">**问题**</span><span class="sxs-lookup"><span data-stu-id="a8c73-106">**Issue**</span></span>|<span data-ttu-id="a8c73-107">可用性数据库的数据同步状态不正常。</span><span class="sxs-lookup"><span data-stu-id="a8c73-107">Data synchronization state of availability database is not healthy.</span></span>|  
|<span data-ttu-id="a8c73-108">**类别**</span><span class="sxs-lookup"><span data-stu-id="a8c73-108">**Category**</span></span>|<span data-ttu-id="a8c73-109">**警告**</span><span class="sxs-lookup"><span data-stu-id="a8c73-109">**Warning**</span></span>|  
|<span data-ttu-id="a8c73-110">**方面**</span><span class="sxs-lookup"><span data-stu-id="a8c73-110">**Facet**</span></span>|<span data-ttu-id="a8c73-111">可用性数据库</span><span class="sxs-lookup"><span data-stu-id="a8c73-111">Availability database</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a8c73-112">说明</span><span class="sxs-lookup"><span data-stu-id="a8c73-112">Description</span></span>  
 <span data-ttu-id="a8c73-113">此策略汇总可用性副本中所有可用性数据库（也称为“数据库副本”）的数据同步状态。</span><span class="sxs-lookup"><span data-stu-id="a8c73-113">This policy rolls up the data synchronization state of all availability databases (also known as "database replicas") in the availability replica.</span></span> <span data-ttu-id="a8c73-114">当有数据库副本不处于要求的数据同步状态时，此策略处于不正常状态。</span><span class="sxs-lookup"><span data-stu-id="a8c73-114">The policy is in an unhealthy sate when any database replica is not in the expected data synchronization state.</span></span> <span data-ttu-id="a8c73-115">否则，该策略处于正常状态。</span><span class="sxs-lookup"><span data-stu-id="a8c73-115">The policy is otherwise in a healthy state.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a8c73-116">对于此版本的 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]，与可能原因和解决方法有关的信息位于 TechNet Wiki 上的 [一些可用性数据库的数据同步状态不正常](https://go.microsoft.com/fwlink/p/?LinkId=220858) 中。</span><span class="sxs-lookup"><span data-stu-id="a8c73-116">For this release of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], information about possible causes and solutions is located at [Data synchronization state of some availability database is not healthy](https://go.microsoft.com/fwlink/p/?LinkId=220858) on the TechNet Wiki.</span></span>  
  
## <a name="possible-causes"></a><span data-ttu-id="a8c73-117">可能的原因</span><span class="sxs-lookup"><span data-stu-id="a8c73-117">Possible Causes</span></span>  
 <span data-ttu-id="a8c73-118">此可用性数据库的数据同步状态不正常。</span><span class="sxs-lookup"><span data-stu-id="a8c73-118">The data synchronization state of this availability database is unhealthy.</span></span> <span data-ttu-id="a8c73-119">在异步-提交可用性副本上，每个可用性数据库都应该处于“正在同步”状态。</span><span class="sxs-lookup"><span data-stu-id="a8c73-119">On an asynchronous-commit availability replica, every availability database should be in the SYNCHRONIZING state.</span></span> <span data-ttu-id="a8c73-120">在同步提交副本上，每个可用性数据库必须处于 SYNCHRONIZED 状态。</span><span class="sxs-lookup"><span data-stu-id="a8c73-120">On a synchronous-commit replica, every availability database must be in the SYNCHRONIZED state.</span></span>  
  
## <a name="possible-solution"></a><span data-ttu-id="a8c73-121">可能的解决方法</span><span class="sxs-lookup"><span data-stu-id="a8c73-121">Possible Solution</span></span>  
 <span data-ttu-id="a8c73-122">使用数据库副本策略查找具有不正常数据同步状态的数据库副本，然后解决该数据库副本上的问题。</span><span class="sxs-lookup"><span data-stu-id="a8c73-122">Use the database replica policy to find the database replica with an unhealthy data synchronization state, and then resolve the issue at the database replica.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8c73-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a8c73-123">See Also</span></span>  
 <span data-ttu-id="a8c73-124">[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a8c73-124">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="a8c73-125">使用 AlwaysOn 面板 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="a8c73-125">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
