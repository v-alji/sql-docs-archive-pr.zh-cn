---
title: SQL Server 监视器概述 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.sqlservermonitor.main.f1
helpviewer_keywords:
- SQL Server Monitor [SQL Server]
ms.assetid: 048ae16d-31c3-489a-9f1e-1400a3bacd39
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ab90186ed493e616e672cfacf881fd61be166f88
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577827"
---
# <a name="sql-server-monitor-overview"></a><span data-ttu-id="96de2-102">SQL Server 监视器概述</span><span class="sxs-lookup"><span data-stu-id="96de2-102">SQL Server Monitor Overview</span></span>
  <span data-ttu-id="96de2-103">SQL Server 监视器不执行监视功能，但它可以承载执行此功能的模块。</span><span class="sxs-lookup"><span data-stu-id="96de2-103">SQL Server Monitor does not perform monitoring functions, but it hosts modules that do.</span></span> <span data-ttu-id="96de2-104">SQL Server 监视器模块包括复制监视器和数据库镜像监视器。</span><span class="sxs-lookup"><span data-stu-id="96de2-104">The SQL Server Monitor modules include Replication Monitor and Database Mirroring Monitor.</span></span>  
  
 <span data-ttu-id="96de2-105">若要使用其中的一个模块，请在 **“转到”** 菜单上选择该模块。</span><span class="sxs-lookup"><span data-stu-id="96de2-105">To use one of these modules, select that module on the **Go** menu.</span></span> <span data-ttu-id="96de2-106">当前选择的模块拥有导航窗格和详细信息窗格的内容、详细信息窗格中的用户交互以及对内容和状态的查询。</span><span class="sxs-lookup"><span data-stu-id="96de2-106">The currently selected module owns the content of the navigation and detail panes, user interaction in the detail panes, and the queries for content and status.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="96de2-107">有关这些监视器的详细信息，请参阅 [监视复制](../../relational-databases/replication/monitoring-replication.md) 和 [监视数据库镜像 (SQL Server)](../database-mirroring/database-mirroring-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="96de2-107">For more information about these monitors, see [Monitoring Replication](../../relational-databases/replication/monitoring-replication.md) and [Monitoring Database Mirroring &#40;SQL Server&#41;](../database-mirroring/database-mirroring-sql-server.md).</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="96de2-108">权限</span><span class="sxs-lookup"><span data-stu-id="96de2-108">Permissions</span></span>  
  
-   <span data-ttu-id="96de2-109">复制监视器</span><span class="sxs-lookup"><span data-stu-id="96de2-109">Replication Monitor</span></span>  
  
     <span data-ttu-id="96de2-110">若要监视复制，您必须是分发服务器上 **sysadmin** 固定服务器角色的成员，或者是分发数据库中 **replmonitor** 固定数据库角色的成员。</span><span class="sxs-lookup"><span data-stu-id="96de2-110">To monitor replication, you must be a member of the **sysadmin** fixed server role at the Distributor or a member of the **replmonitor** fixed database role in the distribution database.</span></span> <span data-ttu-id="96de2-111">系统管理员可以将任何用户添加到 **replmonitor** 角色中，这样该用户就可以在复制监视器中查看复制活动，但不能管理复制。</span><span class="sxs-lookup"><span data-stu-id="96de2-111">A system administrator can add any user to the **replmonitor** role, which allows that user to view replication activity in Replication Monitor; however, the user cannot administer replication.</span></span>  
  
-   <span data-ttu-id="96de2-112">数据库镜像监视器</span><span class="sxs-lookup"><span data-stu-id="96de2-112">Database Mirroring Monitor</span></span>  
  
     <span data-ttu-id="96de2-113">若要监视数据库镜像，必须是服务器实例中 **sysadmin** 固定服务器角色的成员或 **dbm_monitor** 固定数据库角色的成员。</span><span class="sxs-lookup"><span data-stu-id="96de2-113">To monitor database mirroring, you must be a member of either the **sysadmin** fixed server role or the **dbm_monitor** fixed database role on the server instance.</span></span> <span data-ttu-id="96de2-114">如果你只是某一个伙伴服务器实例中的 **sysadmin** 或 **dbm_monitor** 的成员，则监视器只能连接到该伙伴；监视器不能从其他伙伴中检索信息。</span><span class="sxs-lookup"><span data-stu-id="96de2-114">If you are a member of **sysadmin** or **dbm_monitor** on only one of the partner server instances, the monitor can connect only to that partner; the monitor cannot retrieve information from the other partner.</span></span> <span data-ttu-id="96de2-115">有关详细信息，请参阅 [Database Mirroring Monitor Overview](../database-mirroring/database-mirroring-monitor-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="96de2-115">For more information, see [Database Mirroring Monitor Overview](../database-mirroring/database-mirroring-monitor-overview.md).</span></span>  
  
## <a name="menu-options"></a><span data-ttu-id="96de2-116">菜单选项</span><span class="sxs-lookup"><span data-stu-id="96de2-116">Menu Options</span></span>  
 <span data-ttu-id="96de2-117">SQL Server 监视器有一个菜单，其中包括用于 SQL Server 监视器的命令。</span><span class="sxs-lookup"><span data-stu-id="96de2-117">SQL Server Monitor has a menu that contains commands that pertain to SQL Server Monitor.</span></span> <span data-ttu-id="96de2-118">该菜单中还包括来自选定模块的命令。</span><span class="sxs-lookup"><span data-stu-id="96de2-118">This menu may also contain commands from the selected module.</span></span>  
  
 <span data-ttu-id="96de2-119">以下菜单选项适用于 SQL Server 监视器。</span><span class="sxs-lookup"><span data-stu-id="96de2-119">The following menu options pertain to SQL Server Monitor.</span></span>  
  
 <span data-ttu-id="96de2-120">**File**</span><span class="sxs-lookup"><span data-stu-id="96de2-120">**File**</span></span>  
 <span data-ttu-id="96de2-121">此菜单包含“退出”命令。</span><span class="sxs-lookup"><span data-stu-id="96de2-121">This menu contains the **Exit** command.</span></span>  
  
 <span data-ttu-id="96de2-122">**Action**</span><span class="sxs-lookup"><span data-stu-id="96de2-122">**Action**</span></span>  
 <span data-ttu-id="96de2-123">包含在导航树中所选节点的上下文菜单。</span><span class="sxs-lookup"><span data-stu-id="96de2-123">Contains the context menu of the node selected in the navigation tree.</span></span>  
  
 <span data-ttu-id="96de2-124">**Go**</span><span class="sxs-lookup"><span data-stu-id="96de2-124">**Go**</span></span>  
 <span data-ttu-id="96de2-125">包含监视组件的列表：</span><span class="sxs-lookup"><span data-stu-id="96de2-125">Contains a list of monitoring components:</span></span>  
  
-   <span data-ttu-id="96de2-126">数据库镜像</span><span class="sxs-lookup"><span data-stu-id="96de2-126">Database Mirroring</span></span>  
  
-   <span data-ttu-id="96de2-127">复制</span><span class="sxs-lookup"><span data-stu-id="96de2-127">Replication</span></span>  
  
 <span data-ttu-id="96de2-128">**使用 SQL Server Management Studio 监视数据库镜像**</span><span class="sxs-lookup"><span data-stu-id="96de2-128">**To use SQL Server Management Studio to monitor database mirroring**</span></span>  
  
-   [<span data-ttu-id="96de2-129">启动数据库镜像监视器 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="96de2-129">Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;</span></span>](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)  
  
## <a name="see-also"></a><span data-ttu-id="96de2-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="96de2-130">See Also</span></span>  
 [<span data-ttu-id="96de2-131">监视数据库镜像 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="96de2-131">Monitoring Database Mirroring &#40;SQL Server&#41;</span></span>](../database-mirroring/database-mirroring-sql-server.md)  
  
  
