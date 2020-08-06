---
title: 未联接辅助数据库 | Microsoft Docs
ms.custom: ''
ms.date: 01/09/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.drp2joined.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 10817e5e-75fa-42dd-baa2-359bea3ad051
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 81275e85fd865924778f6d6f985e170a5bda9f9a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693103"
---
# <a name="secondary-database-is-not-joined"></a><span data-ttu-id="888e0-102">未联接辅助数据库</span><span class="sxs-lookup"><span data-stu-id="888e0-102">Secondary database is not joined</span></span>
    
## <a name="introduction"></a><span data-ttu-id="888e0-103">简介</span><span class="sxs-lookup"><span data-stu-id="888e0-103">Introduction</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="888e0-104">**策略名称**</span><span class="sxs-lookup"><span data-stu-id="888e0-104">**Policy Name**</span></span>|<span data-ttu-id="888e0-105">可用性数据库联接状态</span><span class="sxs-lookup"><span data-stu-id="888e0-105">Availability Database Join State</span></span>|  
|<span data-ttu-id="888e0-106">**问题**</span><span class="sxs-lookup"><span data-stu-id="888e0-106">**Issue**</span></span>|<span data-ttu-id="888e0-107">未联接辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="888e0-107">Secondary database is not joined.</span></span>|  
|<span data-ttu-id="888e0-108">**类别**</span><span class="sxs-lookup"><span data-stu-id="888e0-108">**Category**</span></span>|<span data-ttu-id="888e0-109">**警告**</span><span class="sxs-lookup"><span data-stu-id="888e0-109">**Warning**</span></span>|  
|<span data-ttu-id="888e0-110">**方面**</span><span class="sxs-lookup"><span data-stu-id="888e0-110">**Facet**</span></span>|<span data-ttu-id="888e0-111">可用性数据库</span><span class="sxs-lookup"><span data-stu-id="888e0-111">Availability database</span></span>|  
  
## <a name="description"></a><span data-ttu-id="888e0-112">说明</span><span class="sxs-lookup"><span data-stu-id="888e0-112">Description</span></span>  
 <span data-ttu-id="888e0-113">此策略检查辅助数据库（也称为“辅助数据库副本”）的联接状态。</span><span class="sxs-lookup"><span data-stu-id="888e0-113">This policy checks the join state of the secondary database (also known as a "secondary database replica").</span></span> <span data-ttu-id="888e0-114">数据集副本未联接时，此策略处于不正常状态。</span><span class="sxs-lookup"><span data-stu-id="888e0-114">The policy is in an unhealthy state when the dataset replica is not joined.</span></span> <span data-ttu-id="888e0-115">否则，该策略处于正常状态。</span><span class="sxs-lookup"><span data-stu-id="888e0-115">The policy is otherwise in a healthy state.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="888e0-116">对于此版本的 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]，与可能原因和解决方法有关的信息位于 TechNet Wiki 上的 [未联接辅助数据库](https://go.microsoft.com/fwlink/p/?LinkId=220862) 中。</span><span class="sxs-lookup"><span data-stu-id="888e0-116">For this release of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], information about possible causes and solutions is located at [Secondary database is not joined](https://go.microsoft.com/fwlink/p/?LinkId=220862) on the TechNet Wiki.</span></span>  
  
## <a name="possible-causes"></a><span data-ttu-id="888e0-117">可能的原因</span><span class="sxs-lookup"><span data-stu-id="888e0-117">Possible Causes</span></span>  
 <span data-ttu-id="888e0-118">此辅助数据库未联接到可用性组。</span><span class="sxs-lookup"><span data-stu-id="888e0-118">This secondary database is not joined to the availability group.</span></span> <span data-ttu-id="888e0-119">此辅助数据库的配置不完整。</span><span class="sxs-lookup"><span data-stu-id="888e0-119">The configuration of this secondary database is incomplete.</span></span>  
  
## <a name="possible-solution"></a><span data-ttu-id="888e0-120">可能的解决方法</span><span class="sxs-lookup"><span data-stu-id="888e0-120">Possible Solution</span></span>  
 <span data-ttu-id="888e0-121">使用 Transact-SQL、PowerShell 或 SQL Server Management Studio 将辅助副本联接到可用性组。</span><span class="sxs-lookup"><span data-stu-id="888e0-121">Use Transact-SQL, PowerShell, or SQL Server Management Studio to join the secondary replica to the availability group.</span></span> <span data-ttu-id="888e0-122">有关将辅助副本联接到可用性组的详细信息，请参阅 [将辅助副本联接到可用性组 (SQL Server)](https://msdn.microsoft.com/library/ff878473\(en-us,SQL.110\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="888e0-122">For more information about joining secondary replicas to availability groups, see [Joining a Secondary Replica to an Availability Group (SQL Server)](https://msdn.microsoft.com/library/ff878473\(en-us,SQL.110\).aspx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="888e0-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="888e0-123">See Also</span></span>  
 <span data-ttu-id="888e0-124">[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="888e0-124">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="888e0-125">使用 AlwaysOn 面板 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="888e0-125">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
