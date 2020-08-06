---
title: 可用性组属性：新建可用性组 (备份首选项页面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroupproperties.backuppreferences.f1
helpviewer_keywords:
- read-only routing
ms.assetid: 65fff22d-5963-4a8c-8b31-fe9ab247a03e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7914d4b1d7af06bcaf4f3fd05a260138e3edf5fc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577858"
---
# <a name="availability-group-properties-new-availability-group-backup-preferences-page"></a><span data-ttu-id="23ed1-102">可用性组属性：新建可用性组（“备份首选项”页）</span><span class="sxs-lookup"><span data-stu-id="23ed1-102">Availability Group Properties: New Availability Group (Backup Preferences Page)</span></span>
  <span data-ttu-id="23ed1-103">使用此对话框可以查看和更改所选可用性组的备份首选项。</span><span class="sxs-lookup"><span data-stu-id="23ed1-103">Use this dialog box to view and change the backup preferences of the selected availability group.</span></span>  
  
 <span data-ttu-id="23ed1-104">**查看可用性组属性**</span><span class="sxs-lookup"><span data-stu-id="23ed1-104">**To view availability group properties**</span></span>  
  
-   [<span data-ttu-id="23ed1-105">查看可用性组属性 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="23ed1-105">View Availability Group Properties &#40;SQL Server&#41;</span></span>](view-availability-group-properties-sql-server.md)  
  
-   [<span data-ttu-id="23ed1-106">使用 AlwaysOn 面板 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="23ed1-106">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
## <a name="where-should-backups-occur"></a><span data-ttu-id="23ed1-107">应在何处进行备份？</span><span class="sxs-lookup"><span data-stu-id="23ed1-107">Where should backups occur?</span></span>  
 <span data-ttu-id="23ed1-108">**优先辅助**</span><span class="sxs-lookup"><span data-stu-id="23ed1-108">**Prefer Secondary**</span></span>  
 <span data-ttu-id="23ed1-109">指定备份应在辅助副本上发生，但在主副本是唯一联机的副本时除外。</span><span class="sxs-lookup"><span data-stu-id="23ed1-109">Specifies that backups should occur on a secondary replica except when the primary replica is the only replica online.</span></span> <span data-ttu-id="23ed1-110">在该情况下，备份应在主副本上发生。</span><span class="sxs-lookup"><span data-stu-id="23ed1-110">In that case, the backup should occur on the primary replica.</span></span> <span data-ttu-id="23ed1-111">这是默认选项。</span><span class="sxs-lookup"><span data-stu-id="23ed1-111">This is the default option.</span></span>  
  
 <span data-ttu-id="23ed1-112">**仅辅助**</span><span class="sxs-lookup"><span data-stu-id="23ed1-112">**Secondary only**</span></span>  
 <span data-ttu-id="23ed1-113">指定备份应该永远不会在主副本上执行。</span><span class="sxs-lookup"><span data-stu-id="23ed1-113">Specifies that backups should never be performed on the primary replica.</span></span> <span data-ttu-id="23ed1-114">如果主副本是唯一的联机副本，则备份应不会发生。</span><span class="sxs-lookup"><span data-stu-id="23ed1-114">If the primary replica is the only replica online, the backup should not occur.</span></span>  
  
 <span data-ttu-id="23ed1-115">**主要节点**</span><span class="sxs-lookup"><span data-stu-id="23ed1-115">**Primary**</span></span>  
 <span data-ttu-id="23ed1-116">指定备份应该始终在主副本上发生。</span><span class="sxs-lookup"><span data-stu-id="23ed1-116">Specifies that the backups should always occur on the primary replica.</span></span> <span data-ttu-id="23ed1-117">如果您需要在对辅助副本运行备份时不支持的备份功能，例如创建差异备份，此选项将很有用。</span><span class="sxs-lookup"><span data-stu-id="23ed1-117">This option is useful if you need backup features, such as creating differential backups, that are not supported when backup is run on a secondary replica.</span></span>  
  
 <span data-ttu-id="23ed1-118">**任何副本**</span><span class="sxs-lookup"><span data-stu-id="23ed1-118">**Any Replica**</span></span>  
 <span data-ttu-id="23ed1-119">指定您希望在选择要执行备份的副本时备份作业将忽略可用性副本的角色。</span><span class="sxs-lookup"><span data-stu-id="23ed1-119">Specifies that you prefer that backup jobs ignore the role of the availability replicas when choosing the replica to perform backups.</span></span> <span data-ttu-id="23ed1-120">请注意，备份作业可能评估其他因素，例如每个可用性副本的备份优先级及其操作状态和已连接状态。</span><span class="sxs-lookup"><span data-stu-id="23ed1-120">Note backup jobs might evaluate other factors such as backup priority of each availability replica in combination with its operational state and connected state.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="23ed1-121">没有实施备份首选项设置。</span><span class="sxs-lookup"><span data-stu-id="23ed1-121">There is no enforcement of the backup-preference setting.</span></span> <span data-ttu-id="23ed1-122">对此首选项的解释依赖于您为给定可用性组中的数据库撰写作业脚本的逻辑（如果有）。</span><span class="sxs-lookup"><span data-stu-id="23ed1-122">The interpretation of this preference depends on the logic, if any, that you script into back jobs for the databases in a given availability group.</span></span> <span data-ttu-id="23ed1-123">有关详细信息，请参阅[活动辅助副本：辅助副本上的备份 (AlwaysOn 可用性组) ](active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="23ed1-123">For more information, see [Active Secondaries: Backup on Secondary Replicas (AlwaysOn Availability Groups)](active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md).</span></span>  
  
## <a name="replica-backup-priorities"></a><span data-ttu-id="23ed1-124">副本备份优先级</span><span class="sxs-lookup"><span data-stu-id="23ed1-124">Replica backup priorities</span></span>  
 <span data-ttu-id="23ed1-125">此网格将显示每个承载可用性组的副本的服务器实例的当前备份优先级。</span><span class="sxs-lookup"><span data-stu-id="23ed1-125">This grid displays the current backup priority of each server instance that hosts a replica for the availability group.</span></span> <span data-ttu-id="23ed1-126">使用此网格可以更改一个或多个可用性副本的备份优先级。</span><span class="sxs-lookup"><span data-stu-id="23ed1-126">Use this grid to change the backup priority of one or more availability replicas.</span></span>  
  
 <span data-ttu-id="23ed1-127">**服务器实例**</span><span class="sxs-lookup"><span data-stu-id="23ed1-127">**Server Instance**</span></span>  
 <span data-ttu-id="23ed1-128">承载可用性副本的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例的名称。</span><span class="sxs-lookup"><span data-stu-id="23ed1-128">The name of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that hosts the availability replica.</span></span>  
  
 <span data-ttu-id="23ed1-129">**备份优先级(最低 = 1，最高 = 100)**</span><span class="sxs-lookup"><span data-stu-id="23ed1-129">**Backup Priority (Lowest=1, Highest=100)**</span></span>  
 <span data-ttu-id="23ed1-130">指定相对于同一可用性组中的其他副本，在此副本上执行备份的优先级。</span><span class="sxs-lookup"><span data-stu-id="23ed1-130">Specifies your priority for performing backups on this replica relative to the other replicas in the same availability group.</span></span> <span data-ttu-id="23ed1-131">该值是范围 0..100 中的整数。</span><span class="sxs-lookup"><span data-stu-id="23ed1-131">The value is an integer in the range of 0..100.</span></span> <span data-ttu-id="23ed1-132">1 表示最低优先级，100 表示最高优先级。</span><span class="sxs-lookup"><span data-stu-id="23ed1-132">1 indicates the lowest priority, and 100 indicates the highest priority.</span></span> <span data-ttu-id="23ed1-133">如果“备份优先级”\*\*\*\*= 1，则仅在当前没有更高优先级的可用性副本可用时，才选择此可用性副本来执行备份。</span><span class="sxs-lookup"><span data-stu-id="23ed1-133">If **Backup Priority** = 1, the availability replica would be chosen for performing backups only if no higher priority availability replicas are currently available.</span></span>  
  
 <span data-ttu-id="23ed1-134">**排除副本**</span><span class="sxs-lookup"><span data-stu-id="23ed1-134">**Exclude Replica**</span></span>  
 <span data-ttu-id="23ed1-135">如果从不希望选择此可用性副本来执行备份，请选择此选项。</span><span class="sxs-lookup"><span data-stu-id="23ed1-135">Select if you never want this availability replica to be chosen for performing backups.</span></span> <span data-ttu-id="23ed1-136">例如，这对于您永远不希望备份故障转移到的远程可用性副本十分有用。</span><span class="sxs-lookup"><span data-stu-id="23ed1-136">This is useful, for example, for a remote availability replica to which you never want backups to fail over.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23ed1-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="23ed1-137">See Also</span></span>  
 <span data-ttu-id="23ed1-138">[活动辅助副本：辅助副本上的备份 (AlwaysOn 可用性组) ](active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md) </span><span class="sxs-lookup"><span data-stu-id="23ed1-138">[Active Secondaries: Backup on Secondary Replicas (AlwaysOn Availability Groups)](active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md) </span></span>  
 [<span data-ttu-id="23ed1-139">ALTER AVAILABILITY GROUP (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="23ed1-139">ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-availability-group-transact-sql)  
  
  
