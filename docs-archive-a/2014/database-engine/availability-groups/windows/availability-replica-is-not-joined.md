---
title: 可用性副本未联接 | Microsoft Docs
ms.custom: ''
ms.date: 01/09/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.arp4joined.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 9c0d10b1-9e12-430c-83b9-ca2bd0a3afc4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7c4f76e98d373e50124f5ca2b135a9fad8f34226
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690150"
---
# <a name="availability-replica-is-not-joined"></a><span data-ttu-id="8953c-102">可用性副本未联接</span><span class="sxs-lookup"><span data-stu-id="8953c-102">Availability replica is not joined</span></span>
    
## <a name="introduction"></a><span data-ttu-id="8953c-103">简介</span><span class="sxs-lookup"><span data-stu-id="8953c-103">Introduction</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8953c-104">**策略名称**</span><span class="sxs-lookup"><span data-stu-id="8953c-104">**Policy Name**</span></span>|<span data-ttu-id="8953c-105">可用性副本联接状态</span><span class="sxs-lookup"><span data-stu-id="8953c-105">Availability Replica Join State</span></span>|  
|<span data-ttu-id="8953c-106">**问题**</span><span class="sxs-lookup"><span data-stu-id="8953c-106">**Issue**</span></span>|<span data-ttu-id="8953c-107">可用性副本未联接。</span><span class="sxs-lookup"><span data-stu-id="8953c-107">Availability Replica is not joined.</span></span>|  
|<span data-ttu-id="8953c-108">**类别**</span><span class="sxs-lookup"><span data-stu-id="8953c-108">**Category**</span></span>|<span data-ttu-id="8953c-109">**警告**</span><span class="sxs-lookup"><span data-stu-id="8953c-109">**Warning**</span></span>|  
|<span data-ttu-id="8953c-110">**方面**</span><span class="sxs-lookup"><span data-stu-id="8953c-110">**Facet**</span></span>|<span data-ttu-id="8953c-111">可用性副本</span><span class="sxs-lookup"><span data-stu-id="8953c-111">Availability replica</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8953c-112">说明</span><span class="sxs-lookup"><span data-stu-id="8953c-112">Description</span></span>  
 <span data-ttu-id="8953c-113">此策略检查可用性副本的联接状态。</span><span class="sxs-lookup"><span data-stu-id="8953c-113">This policy checks the join state of the availability replica.</span></span> <span data-ttu-id="8953c-114">当可用性副本添加到可用性组但未正确联接时，该策略将处于不正常状态。</span><span class="sxs-lookup"><span data-stu-id="8953c-114">The policy is in an unhealthy state when the availability replica is added to the availability group, but is not joined properly.</span></span> <span data-ttu-id="8953c-115">否则，该策略处于正常状态。</span><span class="sxs-lookup"><span data-stu-id="8953c-115">The policy is otherwise in a healthy state.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8953c-116">对于此版本的 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]，与可能原因和解决方法有关的信息位于 TechNet Wiki 上的 [可用性副本未联接](https://go.microsoft.com/fwlink/p/?LinkId=220859) 中。</span><span class="sxs-lookup"><span data-stu-id="8953c-116">For this release of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], information about possible causes and solutions is located at [Availability replica is not joined](https://go.microsoft.com/fwlink/p/?LinkId=220859) on the TechNet Wiki.</span></span>  
  
## <a name="possible-causes"></a><span data-ttu-id="8953c-117">可能的原因</span><span class="sxs-lookup"><span data-stu-id="8953c-117">Possible Causes</span></span>  
 <span data-ttu-id="8953c-118">辅助副本未联接到可用性组。</span><span class="sxs-lookup"><span data-stu-id="8953c-118">The secondary replica is not joined to the availability group.</span></span> <span data-ttu-id="8953c-119">要将某一可用性副本成功联接到可用性组，联接状态必须为“已联接独立实例”(1) 或“已联接故障转移群集”(2)。</span><span class="sxs-lookup"><span data-stu-id="8953c-119">For an availability replica to be successfully joined to the availability group, the join state must be Joined Standalone Instance (1) or Joined Failover Cluster (2).</span></span>  
  
## <a name="possible-solution"></a><span data-ttu-id="8953c-120">可能的解决方法</span><span class="sxs-lookup"><span data-stu-id="8953c-120">Possible Solution</span></span>  
 <span data-ttu-id="8953c-121">使用 Transact-SQL、PowerShell 或 SQL Server Management Studio 将辅助副本联接到可用性组。</span><span class="sxs-lookup"><span data-stu-id="8953c-121">Use Transact-SQL, PowerShell, or SQL Server Management Studio to join the secondary replica to the availability group.</span></span> <span data-ttu-id="8953c-122">有关将辅助副本联接到可用性组的详细信息，请参阅 [将辅助副本联接到可用性组 (SQL Server)](https://msdn.microsoft.com/library/ff878473\(en-us,SQL.110\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="8953c-122">For more information about joining secondary replicas to availability groups, see [Joining a Secondary Replica to an Availability Group (SQL Server)](https://msdn.microsoft.com/library/ff878473\(en-us,SQL.110\).aspx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8953c-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8953c-123">See Also</span></span>  
 <span data-ttu-id="8953c-124">[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="8953c-124">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="8953c-125">使用 AlwaysOn 面板 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="8953c-125">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
