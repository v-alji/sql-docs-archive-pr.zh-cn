---
title: 一些可用性数据库的数据同步状态不正常 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.drp3datasynchealthy.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 89f95d15-33c6-4768-bccd-9dbf8c4f49a9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 221f25a1ee7e4a8719acc133372c742ca4a79303
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694556"
---
# <a name="data-synchronization-state-of-some-availability-database-is-not-healthy"></a><span data-ttu-id="de4fa-102">一些可用性数据库的数据同步状态不正常</span><span class="sxs-lookup"><span data-stu-id="de4fa-102">Data synchronization state of some availability database is not healthy</span></span>
    
## <a name="introduction"></a><span data-ttu-id="de4fa-103">简介</span><span class="sxs-lookup"><span data-stu-id="de4fa-103">Introduction</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="de4fa-104">**策略名称**</span><span class="sxs-lookup"><span data-stu-id="de4fa-104">**Policy Name**</span></span>|<span data-ttu-id="de4fa-105">可用性副本数据同步状态</span><span class="sxs-lookup"><span data-stu-id="de4fa-105">Availability Replica Data Synchronization State</span></span>|  
|<span data-ttu-id="de4fa-106">**问题**</span><span class="sxs-lookup"><span data-stu-id="de4fa-106">**Issue**</span></span>|<span data-ttu-id="de4fa-107">一些可用性数据库的数据同步状态不正常。</span><span class="sxs-lookup"><span data-stu-id="de4fa-107">Data synchronization state of some availability database is not healthy.</span></span>|  
|<span data-ttu-id="de4fa-108">**类别**</span><span class="sxs-lookup"><span data-stu-id="de4fa-108">**Category**</span></span>|<span data-ttu-id="de4fa-109">**警告**</span><span class="sxs-lookup"><span data-stu-id="de4fa-109">**Warning**</span></span>|  
|<span data-ttu-id="de4fa-110">**方面**</span><span class="sxs-lookup"><span data-stu-id="de4fa-110">**Facet**</span></span>|<span data-ttu-id="de4fa-111">可用性副本</span><span class="sxs-lookup"><span data-stu-id="de4fa-111">Availability replica</span></span>|  
  
## <a name="description"></a><span data-ttu-id="de4fa-112">说明</span><span class="sxs-lookup"><span data-stu-id="de4fa-112">Description</span></span>  
 <span data-ttu-id="de4fa-113">此策略检查可用性数据库（也称为“数据库副本”）的数据同步状态。</span><span class="sxs-lookup"><span data-stu-id="de4fa-113">This policy checks the data synchronization state of the availability database (also known as a "database replica").</span></span> <span data-ttu-id="de4fa-114">当数据同步状态为 NOT SYNCHRONIZING 或同步提交数据库副本的状态不为 SYNCHRONIZED 时，此策略处于不正常状态。</span><span class="sxs-lookup"><span data-stu-id="de4fa-114">The policy is in an unhealthy state when the data synchronization state is NOT SYNCHRONIZING or the state is not SYNCHRONIZED for the synchronous-commit database replica.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="de4fa-115">对于此版本的 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]，与可能原因和解决方法有关的信息位于 TechNet Wiki 上的 [可用性数据库的数据同步状态不正常](https://go.microsoft.com/fwlink/p/?LinkId=220863) 中。</span><span class="sxs-lookup"><span data-stu-id="de4fa-115">For this release of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], information about possible causes and solutions is located at [Data synchronization state of availability database is not healthy](https://go.microsoft.com/fwlink/p/?LinkId=220863) on the TechNet Wiki.</span></span>  
  
## <a name="possible-causes"></a><span data-ttu-id="de4fa-116">可能的原因</span><span class="sxs-lookup"><span data-stu-id="de4fa-116">Possible Causes</span></span>  
 <span data-ttu-id="de4fa-117">副本上至少一个可用性数据库处于不正常数据同步状态。</span><span class="sxs-lookup"><span data-stu-id="de4fa-117">At least one availability database on the replica has an unhealthy data synchronization state.</span></span> <span data-ttu-id="de4fa-118">如果该副本是异步-提交可用性副本，则所有可用性数据库都应该处于“正在同步”状态。</span><span class="sxs-lookup"><span data-stu-id="de4fa-118">If this is an asynchronous-commit availability replica, all availability databases should be in the SYNCHRONIZING state.</span></span> <span data-ttu-id="de4fa-119">如果这是同步提交可用性副本，所有可用性数据库应处于 SYNCHRONIZED 状态。</span><span class="sxs-lookup"><span data-stu-id="de4fa-119">If this is a synchronous-commit availability replica, all availability databases should be in the SYNCHRONIZED state.</span></span> <span data-ttu-id="de4fa-120">此问题可能由以下原因导致：</span><span class="sxs-lookup"><span data-stu-id="de4fa-120">This issue can be caused by the following:</span></span>  
  
-   <span data-ttu-id="de4fa-121">可用性副本可能已断开连接。</span><span class="sxs-lookup"><span data-stu-id="de4fa-121">The availability replica might be disconnected.</span></span>  
  
-   <span data-ttu-id="de4fa-122">数据移动可能已挂起。</span><span class="sxs-lookup"><span data-stu-id="de4fa-122">The data movement might be suspended.</span></span>  
  
-   <span data-ttu-id="de4fa-123">数据库可能无法访问。</span><span class="sxs-lookup"><span data-stu-id="de4fa-123">The database might not be accessible.</span></span>  
  
-   <span data-ttu-id="de4fa-124">可能存在由于网络滞后或主副本/辅助副本上的负载导致的临时延迟问题。</span><span class="sxs-lookup"><span data-stu-id="de4fa-124">There might be a temporary delay issue due to network latency or the load on the primary or secondary replica.</span></span>  
  
## <a name="possible-solution"></a><span data-ttu-id="de4fa-125">可能的解决方法</span><span class="sxs-lookup"><span data-stu-id="de4fa-125">Possible Solution</span></span>  
 <span data-ttu-id="de4fa-126">解决所有连接或数据移动挂起问题。</span><span class="sxs-lookup"><span data-stu-id="de4fa-126">Resolve any connection or data movement suspend issues.</span></span> <span data-ttu-id="de4fa-127">使用 SQL Server Management Studio 查看此问题的事件，查找数据库错误。</span><span class="sxs-lookup"><span data-stu-id="de4fa-127">Check the events for this issue using SQL Server Management Studio, and find the database error.</span></span> <span data-ttu-id="de4fa-128">按照特定错误的故障排除步骤操作。</span><span class="sxs-lookup"><span data-stu-id="de4fa-128">Follow the troubleshooting steps for the specific error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de4fa-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="de4fa-129">See Also</span></span>  
 <span data-ttu-id="de4fa-130">[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="de4fa-130">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="de4fa-131">使用 AlwaysOn 面板 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="de4fa-131">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
