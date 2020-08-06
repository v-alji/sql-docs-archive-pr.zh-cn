---
title: 可用性副本不具有运行状况良好的角色 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.arp1rolehealthy.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: ebb2c9f4-2097-4688-b4fb-8f0571047317
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f7be26945903a5e3b602ef4a99c269de6a58b04a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690154"
---
# <a name="availability-replica-does-not-have-a-healthy-role"></a><span data-ttu-id="a10a6-102">可用性副本不具有运行状况良好的角色</span><span class="sxs-lookup"><span data-stu-id="a10a6-102">Availability replica does not have a healthy role</span></span>
    
## <a name="introduction"></a><span data-ttu-id="a10a6-103">简介</span><span class="sxs-lookup"><span data-stu-id="a10a6-103">Introduction</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a10a6-104">**策略名称**</span><span class="sxs-lookup"><span data-stu-id="a10a6-104">**Policy Name**</span></span>|<span data-ttu-id="a10a6-105">可用性副本角色状态</span><span class="sxs-lookup"><span data-stu-id="a10a6-105">Availability Replica Role State</span></span>|  
|<span data-ttu-id="a10a6-106">**问题**</span><span class="sxs-lookup"><span data-stu-id="a10a6-106">**Issue**</span></span>|<span data-ttu-id="a10a6-107">可用性副本不具有运行状况良好的角色。</span><span class="sxs-lookup"><span data-stu-id="a10a6-107">Availability replica does not have a healthy role.</span></span>|  
|<span data-ttu-id="a10a6-108">**类别**</span><span class="sxs-lookup"><span data-stu-id="a10a6-108">**Category**</span></span>|<span data-ttu-id="a10a6-109">**严重**</span><span class="sxs-lookup"><span data-stu-id="a10a6-109">**Critical**</span></span>|  
|<span data-ttu-id="a10a6-110">**方面**</span><span class="sxs-lookup"><span data-stu-id="a10a6-110">**Facet**</span></span>|<span data-ttu-id="a10a6-111">可用性副本</span><span class="sxs-lookup"><span data-stu-id="a10a6-111">Availability replica</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a10a6-112">说明</span><span class="sxs-lookup"><span data-stu-id="a10a6-112">Description</span></span>  
 <span data-ttu-id="a10a6-113">此策略检查可用性副本的角色的状态。</span><span class="sxs-lookup"><span data-stu-id="a10a6-113">This policy checks the state of the role of the availability replica.</span></span> <span data-ttu-id="a10a6-114">在可用性副本的角色既不是主副本也不是辅助副本时，该策略将处于不正常状态。</span><span class="sxs-lookup"><span data-stu-id="a10a6-114">The policy is in an unhealthy state when the role of the availability replica is neither primary nor secondary.</span></span> <span data-ttu-id="a10a6-115">否则，该策略处于正常状态。</span><span class="sxs-lookup"><span data-stu-id="a10a6-115">The policy is otherwise in a healthy state.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a10a6-116">对于此版本的 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]，与可能原因和解决方法有关的信息位于 TechNet Wiki 上的 [可用性副本不具有正常角色](https://go.microsoft.com/fwlink/p/?LinkId=220856) 中。</span><span class="sxs-lookup"><span data-stu-id="a10a6-116">For this release of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], information about possible causes and solutions is located at [Availability replica does not have a healthy role](https://go.microsoft.com/fwlink/p/?LinkId=220856) on the TechNet Wiki.</span></span>  
  
## <a name="possible-causes"></a><span data-ttu-id="a10a6-117">可能的原因</span><span class="sxs-lookup"><span data-stu-id="a10a6-117">Possible Causes</span></span>  
 <span data-ttu-id="a10a6-118">此可用性副本的角色是不正常。</span><span class="sxs-lookup"><span data-stu-id="a10a6-118">The role of this availability replica is unhealthy.</span></span> <span data-ttu-id="a10a6-119">副本既没有主副本角色，也没有辅助副本角色。</span><span class="sxs-lookup"><span data-stu-id="a10a6-119">The replica does not have either the primary or secondary role.</span></span>  
  
## <a name="possible-solution-information_still_to_come"></a><span data-ttu-id="a10a6-120">可能的解决方法：Information_still_to_come</span><span class="sxs-lookup"><span data-stu-id="a10a6-120">Possible Solution: Information_still_to_come</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a10a6-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a10a6-121">See Also</span></span>  
 <span data-ttu-id="a10a6-122">[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a10a6-122">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="a10a6-123">使用 AlwaysOn 面板 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="a10a6-123">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
