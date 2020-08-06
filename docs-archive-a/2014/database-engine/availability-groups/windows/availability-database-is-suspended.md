---
title: 可用性数据库挂起 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.drp1notsuspended.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 6baee70f-848c-4e86-b20d-78875c0f82cb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 07a547f217367f13df739348325461c862d831f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577871"
---
# <a name="availability-database-is-suspended"></a><span data-ttu-id="ce566-102">可用性数据库挂起</span><span class="sxs-lookup"><span data-stu-id="ce566-102">Availability database is suspended</span></span>
    
## <a name="introduction"></a><span data-ttu-id="ce566-103">简介</span><span class="sxs-lookup"><span data-stu-id="ce566-103">Introduction</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ce566-104">**策略名称**</span><span class="sxs-lookup"><span data-stu-id="ce566-104">**Policy Name**</span></span>|<span data-ttu-id="ce566-105">可用性数据库挂起状态</span><span class="sxs-lookup"><span data-stu-id="ce566-105">Availability Database Suspension State</span></span>|  
|<span data-ttu-id="ce566-106">**问题**</span><span class="sxs-lookup"><span data-stu-id="ce566-106">**Issue**</span></span>|<span data-ttu-id="ce566-107">可用性数据库挂起。</span><span class="sxs-lookup"><span data-stu-id="ce566-107">Availability database is suspended.</span></span>|  
|<span data-ttu-id="ce566-108">**类别**</span><span class="sxs-lookup"><span data-stu-id="ce566-108">**Category**</span></span>|<span data-ttu-id="ce566-109">**警告**</span><span class="sxs-lookup"><span data-stu-id="ce566-109">**Warning**</span></span>|  
|<span data-ttu-id="ce566-110">**方面**</span><span class="sxs-lookup"><span data-stu-id="ce566-110">**Facet**</span></span>|<span data-ttu-id="ce566-111">可用性数据库</span><span class="sxs-lookup"><span data-stu-id="ce566-111">Availability database</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ce566-112">说明</span><span class="sxs-lookup"><span data-stu-id="ce566-112">Description</span></span>  
 <span data-ttu-id="ce566-113">此策略检查辅助数据库（也称为“辅助数据库副本”）的数据移动状态。</span><span class="sxs-lookup"><span data-stu-id="ce566-113">This policy checks the state of data movement of the secondary database (also known as a "secondary database replica").</span></span> <span data-ttu-id="ce566-114">数据移动挂起时，此策略处于不正常状态。</span><span class="sxs-lookup"><span data-stu-id="ce566-114">The policy is in an unhealthy state when the data movement is suspended.</span></span> <span data-ttu-id="ce566-115">否则，该策略处于正常状态。</span><span class="sxs-lookup"><span data-stu-id="ce566-115">The policy is otherwise in a healthy state.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ce566-116">对于此版本的 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]，与可能原因和解决方法有关的信息位于 [TechNet Wiki 上的可用性数据库挂起](https://go.microsoft.com/fwlink/p/?LinkId=220860) 中。</span><span class="sxs-lookup"><span data-stu-id="ce566-116">For this release of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], information about possible causes and solutions is located at [Availability database is suspended](https://go.microsoft.com/fwlink/p/?LinkId=220860) on the TechNet Wiki.</span></span>  
  
## <a name="possible-causes"></a><span data-ttu-id="ce566-117">可能的原因</span><span class="sxs-lookup"><span data-stu-id="ce566-117">Possible Causes</span></span>  
 <span data-ttu-id="ce566-118">由于下列原因，此可用性数据库上的数据同步可能已挂起：</span><span class="sxs-lookup"><span data-stu-id="ce566-118">Data synchronization on this availability database might have been suspended because of the following:</span></span>  
  
-   <span data-ttu-id="ce566-119">由于错误，系统可能已挂起数据同步。</span><span class="sxs-lookup"><span data-stu-id="ce566-119">Due to an error, the system might have suspended data synchronization.</span></span>  
  
-   <span data-ttu-id="ce566-120">数据库管理员出于维护目的可能已挂起数据同步。</span><span class="sxs-lookup"><span data-stu-id="ce566-120">The database administrator might have suspended data synchronization for maintenance purposes.</span></span>  
  
## <a name="possible-solution"></a><span data-ttu-id="ce566-121">可能的解决方法</span><span class="sxs-lookup"><span data-stu-id="ce566-121">Possible Solution</span></span>  
 <span data-ttu-id="ce566-122">继续数据同步。</span><span class="sxs-lookup"><span data-stu-id="ce566-122">Resume data synchronization.</span></span> <span data-ttu-id="ce566-123">如果问题仍然存在，请在事件日志中查看该可用性组，然后诊断系统挂起数据移动的原因。</span><span class="sxs-lookup"><span data-stu-id="ce566-123">If the issue persists, check the availability group in the Event log, and then diagnose why the system suspended data movement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce566-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ce566-124">See Also</span></span>  
 <span data-ttu-id="ce566-125">[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ce566-125">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="ce566-126">使用 AlwaysOn 面板 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="ce566-126">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
