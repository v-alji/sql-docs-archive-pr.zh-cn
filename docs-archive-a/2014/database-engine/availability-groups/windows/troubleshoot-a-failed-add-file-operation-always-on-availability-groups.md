---
title: 排查失败的添加文件操作 (AlwaysOn 可用性组) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- secondary databases [SQL Server], Availability Groups
- Availability Groups [SQL Server], troubleshooting
ms.assetid: 31ceaebf-864b-4dd0-9112-0d047b0316ad
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2551080c214f18473caa71a3e17797c34fcc943a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693473"
---
# <a name="troubleshoot-a-failed-add-file-operation-alwayson-availability-groups"></a><span data-ttu-id="1d7ba-102">解决失败的添加文件操作问题（AlwaysOn 可用性组）</span><span class="sxs-lookup"><span data-stu-id="1d7ba-102">Troubleshoot a Failed Add-File Operation (AlwaysOn Availability Groups)</span></span>
  <span data-ttu-id="1d7ba-103">在某些 AlwaysOn 可用性组部署中，文件路径在承载主副本的系统与承载辅助副本的系统之间存在差异。</span><span class="sxs-lookup"><span data-stu-id="1d7ba-103">In some AlwaysOn availability group deployments, file paths differ between the system that hosts the primary replica and systems that host a secondary replica.</span></span> <span data-ttu-id="1d7ba-104">如果辅助副本上不存在添加文件操作的文件路径，则添加文件操作会在主数据库上取得成功。</span><span class="sxs-lookup"><span data-stu-id="1d7ba-104">If the file path of an add-file operation does not exist on a secondary replica, the add-file operation will succeed on the primary database.</span></span> <span data-ttu-id="1d7ba-105">但添加文件操作将会导致辅助数据库挂起。</span><span class="sxs-lookup"><span data-stu-id="1d7ba-105">But the add-file operation will cause the secondary database to be suspended.</span></span> <span data-ttu-id="1d7ba-106">而这又会导致辅助副本进入“非同步”状态。</span><span class="sxs-lookup"><span data-stu-id="1d7ba-106">This, in turn, causes the secondary replica to enter the NOT SYNCHRONIZING state.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1d7ba-107">我们建议，如有可能，给定辅助数据库的文件路径（包括驱动器号）应该与相应的主数据库的路径相同。</span><span class="sxs-lookup"><span data-stu-id="1d7ba-107">We recommend that, if possible, the file path (including the drive letter) of a given secondary database be identical to the path of the corresponding primary database.</span></span>  
  
## <a name="problem-resolution"></a><span data-ttu-id="1d7ba-108">问题解决方法</span><span class="sxs-lookup"><span data-stu-id="1d7ba-108">Problem Resolution</span></span>  
 <span data-ttu-id="1d7ba-109">若要解决此问题，数据库所有者必须完成以下步骤：</span><span class="sxs-lookup"><span data-stu-id="1d7ba-109">To resolve this problem the database owner must complete the following steps:</span></span>  
  
1.  <span data-ttu-id="1d7ba-110">从可用性组中删除辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="1d7ba-110">Remove the secondary database from the availability group.</span></span> <span data-ttu-id="1d7ba-111">有关详细信息，请参阅[从可用性组中删除辅助数据库 (SQL Server)](remove-a-secondary-database-from-an-availability-group-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="1d7ba-111">For more information, see [Remove a Secondary Database from an Availability Group &#40;SQL Server&#41;](remove-a-secondary-database-from-an-availability-group-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="1d7ba-112">在现有辅助数据库上，使用 WITH NORECOVERY 和 WITH MOVE（指定将承载辅助副本的服务器实例上的文件路径）将包含添加的文件的文件组的完整副本还原到辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="1d7ba-112">On the existing secondary database, restore a full backup of the filegroup that contains the added file to the secondary database, using WITH NORECOVERY and WITH MOVE (specifying the file path on the server instance that hosts the secondary replica).</span></span> <span data-ttu-id="1d7ba-113">有关详细信息，请参阅[将数据库还原到新位置 (SQL Server)](../../../relational-databases/backup-restore/restore-a-database-to-a-new-location-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="1d7ba-113">For more information, see [Restore a Database to a New Location &#40;SQL Server&#41;](../../../relational-databases/backup-restore/restore-a-database-to-a-new-location-sql-server.md).</span></span>  
  
3.  <span data-ttu-id="1d7ba-114">备份包含对主数据库的添加文件操作的事务日志，并且使用 WITH NORECOVERY 和 WITH MOVE 手动还原辅助数据库上的日志备份。</span><span class="sxs-lookup"><span data-stu-id="1d7ba-114">Back up the transaction log that contains the add-file operation on the primary database, and manually restore the log backup on the secondary database using WITH NORECOVERY and WITH MOVE.</span></span>  
  
4.  <span data-ttu-id="1d7ba-115">通过使用 WITH NO RECOVERY 从主数据库还原任何其他待定日志备份，对辅助数据库进行准备以便重新联接到可用性组。</span><span class="sxs-lookup"><span data-stu-id="1d7ba-115">Prepare the secondary database for re-joining the availability group, by restoring, WITH NO RECOVERY, any other outstanding log backups from the primary database.</span></span>  
  
5.  <span data-ttu-id="1d7ba-116">将辅助数据库重新联接到可用性组。</span><span class="sxs-lookup"><span data-stu-id="1d7ba-116">Rejoin the secondary database to the availability group.</span></span> <span data-ttu-id="1d7ba-117">有关详细信息，请参阅 [将辅助数据库联接到可用性组 (SQL Server)](join-a-secondary-database-to-an-availability-group-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="1d7ba-117">For more information, see [Join a Secondary Database to an Availability Group &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d7ba-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1d7ba-118">See Also</span></span>  
 <span data-ttu-id="1d7ba-119">[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1d7ba-119">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="1d7ba-120">[为可用性组手动准备辅助数据库 (SQL Server)](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1d7ba-120">[Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md) </span></span>  
 <span data-ttu-id="1d7ba-121">[孤立用户故障排除 (SQL Server)](../../../sql-server/failover-clusters/troubleshoot-orphaned-users-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1d7ba-121">[Troubleshoot Orphaned Users &#40;SQL Server&#41;](../../../sql-server/failover-clusters/troubleshoot-orphaned-users-sql-server.md) </span></span>  
 [<span data-ttu-id="1d7ba-122">&#41;删除 AlwaysOn 可用性组配置 &#40;SQL Server 的疑难解答</span><span class="sxs-lookup"><span data-stu-id="1d7ba-122">Troubleshoot AlwaysOn Availability Groups Configuration &#40;SQL Server&#41;deleted</span></span>](troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
  
