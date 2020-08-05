---
title: 在升级服务器实例时最大程度减少镜像数据库的停机时间 |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- upgrading SQL Server, rolling upgrade of mirrored databases
- database mirroring [SQL Server], upgrading system
- rolling upgrades [SQL Server]
ms.assetid: 0e73bd23-497d-42f1-9e81-8d5314bcd597
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0a343e6b9e93aa1910c82f436f3a50daf00d57bc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580880"
---
# <a name="minimize-downtime-for-mirrored-databases-when-upgrading-server-instances"></a><span data-ttu-id="c9c34-102">在升级服务器实例时最大限度地减少镜像数据库的停机时间</span><span class="sxs-lookup"><span data-stu-id="c9c34-102">Minimize Downtime for Mirrored Databases When Upgrading Server Instances</span></span>
  <span data-ttu-id="c9c34-103">将服务器实例升级到时 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ，可以通过执行顺序升级（称为 "*滚动升级*"）将每个镜像数据库的停机时间减少为只进行一次手动故障转移。</span><span class="sxs-lookup"><span data-stu-id="c9c34-103">When upgrading server instances to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], you can reduce downtime for each mirrored database to only a single manual failover by performing a sequential upgrade, known as a *rolling upgrade*.</span></span> <span data-ttu-id="c9c34-104">滚动升级是一个多阶段过程，其最简单的形式如下：升级当前在镜像会话中充当镜像服务器的服务器实例，然后对镜像数据库进行手动故障转移，升级以前的主体服务器，恢复镜像。</span><span class="sxs-lookup"><span data-stu-id="c9c34-104">A rolling upgrade is a multi-stage process that in its simplest form involves upgrading the server instance that is currently acting as the mirror server in a mirroring session, then manually failing over the mirrored database, upgrading the former principal server, and resuming mirroring.</span></span> <span data-ttu-id="c9c34-105">实际上，确切过程将取决于运行模式以及在所升级的服务器实例上运行的镜像会话的编号和布局。</span><span class="sxs-lookup"><span data-stu-id="c9c34-105">In practice, the exact process will depend on the operating mode and the number and layout of mirroring session running on the server instances that you are upgrading.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c9c34-106">有关执行滚动升级以安装 Service Pack 或修补程序的信息，请参阅[在系统上安装 Service pack，并且镜像数据库的停机时间最短](../install-a-service-pack-on-a-system-with-minimal-downtime-for-mirrored-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="c9c34-106">For information about performing a rolling upgrade to install a service pack or hotfix, see [Install a Service Pack on a System with Minimal Downtime for Mirrored Databases](../install-a-service-pack-on-a-system-with-minimal-downtime-for-mirrored-databases.md).</span></span>  
  
 <span data-ttu-id="c9c34-107">**建议的准备工作（最佳实践）**</span><span class="sxs-lookup"><span data-stu-id="c9c34-107">**Recommended Preparation (Best Practices)**</span></span>  
  
 <span data-ttu-id="c9c34-108">在开始滚动升级之前，建议您：</span><span class="sxs-lookup"><span data-stu-id="c9c34-108">Before starting a rolling upgrade, we recommend that you:</span></span>  
  
1.  <span data-ttu-id="c9c34-109">至少对一个镜像会话执行实际手动故障转移：</span><span class="sxs-lookup"><span data-stu-id="c9c34-109">Perform a practice manual failover on at least one of your mirroring sessions:</span></span>  
  
    -   [<span data-ttu-id="c9c34-110">手动故障转移数据库镜像会话 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="c9c34-110">Manually Fail Over a Database Mirroring Session &#40;SQL Server Management Studio&#41;</span></span>](manually-fail-over-a-database-mirroring-session-sql-server-management-studio.md)  
  
    -   <span data-ttu-id="c9c34-111">[手动故障转移数据库镜像会话 (Transact-SQL)](manually-fail-over-a-database-mirroring-session-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="c9c34-111">[Manually Fail Over a Database Mirroring Session &#40;Transact-SQL&#41;](manually-fail-over-a-database-mirroring-session-transact-sql.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c9c34-112">有关手动故障转移如何实现的详细信息，请参阅[数据库镜像会话期间的角色切换 (SQL Server)](role-switching-during-a-database-mirroring-session-sql-server.md) 。</span><span class="sxs-lookup"><span data-stu-id="c9c34-112">For information about how manual failover works, see [Role Switching During a Database Mirroring Session &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="c9c34-113">保护数据：</span><span class="sxs-lookup"><span data-stu-id="c9c34-113">Protect your data:</span></span>  
  
    1.  <span data-ttu-id="c9c34-114">对每个主体数据库执行完整数据库备份：</span><span class="sxs-lookup"><span data-stu-id="c9c34-114">Perform a full database backup on every principal database:</span></span>  
  
         <span data-ttu-id="c9c34-115">[创建完整数据库备份 (SQL Server)](../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="c9c34-115">[Create a Full Database Backup &#40;SQL Server&#41;](../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md).</span></span>  
  
    2.  <span data-ttu-id="c9c34-116">在每个主体服务器上运行 [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) 命令。</span><span class="sxs-lookup"><span data-stu-id="c9c34-116">Run the [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) command on every principal database.</span></span>  
  
 <span data-ttu-id="c9c34-117">**滚动升级的阶段**</span><span class="sxs-lookup"><span data-stu-id="c9c34-117">**Stages of a Rolling Upgrade**</span></span>  
  
 <span data-ttu-id="c9c34-118">滚动升级的具体步骤取决于镜像配置的运行模式。</span><span class="sxs-lookup"><span data-stu-id="c9c34-118">The specific steps of a rolling upgrade depend on the operating mode of the mirroring configuration.</span></span> <span data-ttu-id="c9c34-119">不过基本阶段是相同的。</span><span class="sxs-lookup"><span data-stu-id="c9c34-119">However, the basic stages are the same.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c9c34-120">有关运行模式的详细信息，请参阅 [数据库镜像运行模式](database-mirroring-operating-modes.md)。</span><span class="sxs-lookup"><span data-stu-id="c9c34-120">For information about the operating modes, see [Database Mirroring Operating Modes](database-mirroring-operating-modes.md).</span></span>  
  
 <span data-ttu-id="c9c34-121">下图是显示各个运行模式的滚动升级基本阶段的流程图。</span><span class="sxs-lookup"><span data-stu-id="c9c34-121">The following illustration is a flowchart that shows the basic stages of a rolling upgrade for each operating mode.</span></span> <span data-ttu-id="c9c34-122">该图后面的内容介绍了对应的步骤。</span><span class="sxs-lookup"><span data-stu-id="c9c34-122">The corresponding procedures are described after the illustration.</span></span>  
  
 <span data-ttu-id="c9c34-123">![显示滚动升级步骤的流程图](../media/dbm-rolling-upgrade.gif "显示滚动升级步骤的流程图")</span><span class="sxs-lookup"><span data-stu-id="c9c34-123">![Flowchart showing steps of a rolling upgrade](../media/dbm-rolling-upgrade.gif "Flowchart showing steps of a rolling upgrade")</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="c9c34-124">在并发镜像会话中，一个服务器实例可能扮演不同的镜像角色（主体服务器、镜像服务器或见证服务器）。</span><span class="sxs-lookup"><span data-stu-id="c9c34-124">A server instance might be performing different mirroring roles (principal server, mirror server, or witness) in concurrent mirroring sessions.</span></span> <span data-ttu-id="c9c34-125">在这种情况下，必须相应地调整基本滚动升级过程。</span><span class="sxs-lookup"><span data-stu-id="c9c34-125">In this case, you will have to adapt the basic rolling upgrade process accordingly.</span></span> <span data-ttu-id="c9c34-126">有关详细信息，请参阅 [数据库镜像会话期间的角色切换 (SQL Server)](role-switching-during-a-database-mirroring-session-sql-server.md)的各版本中均未提供见证服务器实例。</span><span class="sxs-lookup"><span data-stu-id="c9c34-126">For more information, see [Role Switching During a Database Mirroring Session &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md).</span></span>  
  
### <a name="to-change-a-session-from-high-performance-mode-to-high-safety-mode"></a><span data-ttu-id="c9c34-127">将会话从高性能模式更改为高安全模式</span><span class="sxs-lookup"><span data-stu-id="c9c34-127">To change a session from high-performance mode to high-safety mode</span></span>  
  
1.  <span data-ttu-id="c9c34-128">如果镜像会话在高性能模式下运行，则在执行滚动升级之前，将运行模式更改为不带自动故障转移功能的高安全模式。</span><span class="sxs-lookup"><span data-stu-id="c9c34-128">If a mirroring session is running in high-performance mode, before you perform a rolling upgrade, change the operating mode to high safety without automatic failover.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="c9c34-129">如果镜像服务器与主体服务器在地理位置上存有一定距离，则可能不适宜进行滚动升级。</span><span class="sxs-lookup"><span data-stu-id="c9c34-129">If the mirror server is geographically distant from the principal server, a rolling upgrade might be inappropriate.</span></span>  
  
    -   <span data-ttu-id="c9c34-130">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中：使用“数据库属性”对话框中的[镜像页](../../relational-databases/databases/database-properties-mirroring-page.md)将“操作模式”选项更改为“不带自动故障转移功能的高安全(同步)”  。</span><span class="sxs-lookup"><span data-stu-id="c9c34-130">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]: Change the **Operating mode** option to **High safety without automatic failover (synchronous)** by using the [Mirroring Page](../../relational-databases/databases/database-properties-mirroring-page.md) of the **Database Properties** dialog box.</span></span> <span data-ttu-id="c9c34-131">有关如何访问此页的详细信息，请参阅[启动配置数据库镜像安全向导 (SQL Server Management Studio)](start-the-configuring-database-mirroring-security-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="c9c34-131">For information about how to access this page, see [Start the Configuring Database Mirroring Security Wizard &#40;SQL Server Management Studio&#41;](start-the-configuring-database-mirroring-security-wizard.md).</span></span>  
  
    -   <span data-ttu-id="c9c34-132">在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 中：将事务安全设置为 FULL。</span><span class="sxs-lookup"><span data-stu-id="c9c34-132">In [!INCLUDE[tsql](../../includes/tsql-md.md)]: Set transaction safety to FULL.</span></span> <span data-ttu-id="c9c34-133">有关详细信息，请参阅[更改数据库镜像会话中的事务安全 (Transact-SQL)](change-transaction-safety-in-a-database-mirroring-session-transact-sql.md)</span><span class="sxs-lookup"><span data-stu-id="c9c34-133">For more information, see [Change Transaction Safety in a Database Mirroring Session &#40;Transact-SQL&#41;](change-transaction-safety-in-a-database-mirroring-session-transact-sql.md)</span></span>  
  
### <a name="to-remove-a-witness-from-a-session"></a><span data-ttu-id="c9c34-134">从会话中删除见证服务器</span><span class="sxs-lookup"><span data-stu-id="c9c34-134">To remove a witness from a session</span></span>  
  
1.  <span data-ttu-id="c9c34-135">如果镜像会话包括见证服务器，则建议您在执行滚动升级之前删除该见证服务器。</span><span class="sxs-lookup"><span data-stu-id="c9c34-135">If a mirroring session involves a witness, we recommend that you remove the witness before you perform a rolling upgrade.</span></span> <span data-ttu-id="c9c34-136">否则，在升级镜像服务器实例时，数据库的可用性将取决于仍然连接至主体服务器实例的见证服务器。</span><span class="sxs-lookup"><span data-stu-id="c9c34-136">Otherwise, when the mirror server instance is being upgraded, database availability depends on the witness that remains connected to the principal server instance.</span></span> <span data-ttu-id="c9c34-137">删除见证服务器之后，可以在滚动升级过程中随时对其进行升级，而不会有数据库停机的风险。</span><span class="sxs-lookup"><span data-stu-id="c9c34-137">After you remove a witness, you can upgrade it at any time during the rolling upgrade process without risking database downtime.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c9c34-138">有关详细信息，请参阅[仲裁：见证服务器如何影响数据库可用性（数据库镜像）](quorum-how-a-witness-affects-database-availability-database-mirroring.md)。</span><span class="sxs-lookup"><span data-stu-id="c9c34-138">For more information, see [Quorum: How a Witness Affects Database Availability &#40;Database Mirroring&#41;](quorum-how-a-witness-affects-database-availability-database-mirroring.md).</span></span>  
  
    -   [<span data-ttu-id="c9c34-139">从数据库镜像会话删除见证服务器 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="c9c34-139">Remove the Witness from a Database Mirroring Session &#40;SQL Server&#41;</span></span>](remove-the-witness-from-a-database-mirroring-session-sql-server.md)  
  
### <a name="to-perform-the-rolling-upgrade"></a><span data-ttu-id="c9c34-140">执行滚动升级</span><span class="sxs-lookup"><span data-stu-id="c9c34-140">To perform the rolling upgrade</span></span>  
  
1.  <span data-ttu-id="c9c34-141">为了最大限度地减少停机时间，我们建议：通过更新任何当前在其所有镜像会话中均为镜像服务器的镜像伙伴开始滚动升级。</span><span class="sxs-lookup"><span data-stu-id="c9c34-141">To minimize downtime, we recommend the following: Start the rolling upgrade by updating any mirroring partner that is currently the mirror server in all its mirroring sessions.</span></span> <span data-ttu-id="c9c34-142">此时，可能需要更新多个服务器实例。</span><span class="sxs-lookup"><span data-stu-id="c9c34-142">You might have to update multiple server instances at this point.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c9c34-143">在滚动升级过程中可以随时升级见证服务器。</span><span class="sxs-lookup"><span data-stu-id="c9c34-143">A witness can be upgraded at any point in the rolling upgrade process.</span></span> <span data-ttu-id="c9c34-144">例如，如果某个服务器实例在会话 1 中为镜像服务器，在会话 2 中为见证服务器，则可以立即升级此服务器实例。</span><span class="sxs-lookup"><span data-stu-id="c9c34-144">For example, if a server instance is a mirror server in Session 1 and is a witness in Session 2, you can upgrade the server instance now.</span></span>  
  
     <span data-ttu-id="c9c34-145">要首先升级的服务器实例是由镜像会话的当前配置决定的，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c9c34-145">The server instance to upgrade first depends on the current configuration of your mirroring sessions, as follows:</span></span>  
  
    -   <span data-ttu-id="c9c34-146">如果任何服务器实例在其所有镜像会话中均已为镜像服务器，则将此服务器实例升级为新版本。</span><span class="sxs-lookup"><span data-stu-id="c9c34-146">If any server instance is already the mirror server in all its mirroring sessions, upgrade the server instance to the new version.</span></span>  
  
    -   <span data-ttu-id="c9c34-147">如果在任何镜像会话中所有服务器实例当前都是主体服务器，则选择一个要首先升级的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="c9c34-147">If all your server instances are currently the principal server in any mirroring sessions, select one server instance to upgrade first.</span></span> <span data-ttu-id="c9c34-148">然后，对其每个主体数据库进行手动故障转移并升级该服务器实例。</span><span class="sxs-lookup"><span data-stu-id="c9c34-148">Then, manually fail over each of its principal databases and upgrade that server instance.</span></span>  
  
     <span data-ttu-id="c9c34-149">升级完成后，服务器实例将自动重新加入其每个镜像会话。</span><span class="sxs-lookup"><span data-stu-id="c9c34-149">After being upgraded, a server instance automatically rejoins each of its mirroring sessions.</span></span>  
  
2.  <span data-ttu-id="c9c34-150">对于其镜像服务器实例刚完成升级的每个镜像会话，请等待会话进行同步。</span><span class="sxs-lookup"><span data-stu-id="c9c34-150">For each mirroring session whose mirror server instance has just been upgraded, wait for the session to synchronize.</span></span> <span data-ttu-id="c9c34-151">然后，连接到主体服务器实例并对会话进行手动故障转移。</span><span class="sxs-lookup"><span data-stu-id="c9c34-151">Then, connect to the principal server instance, and manually fail over the session.</span></span> <span data-ttu-id="c9c34-152">故障转移后，已升级的服务器实例成为该会话的主体服务器，而以前的主体服务成为镜像服务器。</span><span class="sxs-lookup"><span data-stu-id="c9c34-152">On failover, the upgraded server instance becomes the principal server for that session, and the former principal server becomes the mirror server.</span></span>  
  
     <span data-ttu-id="c9c34-153">此步骤的目的是让其他服务器实例在其作为伙伴的每个镜像会话中成为镜像服务器。</span><span class="sxs-lookup"><span data-stu-id="c9c34-153">The goal of this step is for another server instance to become the mirror server in every mirroring session in which it is a partner.</span></span>  
  
     <span data-ttu-id="c9c34-154">**在出现故障时转移到已升级的服务器实例后的限制。**</span><span class="sxs-lookup"><span data-stu-id="c9c34-154">**Restrictions after you failover to an upgraded server instance.**</span></span>  
  
     <span data-ttu-id="c9c34-155">在从早期服务器实例故障转移到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 服务器实例后，数据库会话将挂起。</span><span class="sxs-lookup"><span data-stu-id="c9c34-155">After failing over from an earlier server instance to a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] server instance, the database session is suspended.</span></span> <span data-ttu-id="c9c34-156">直到升级完其他伙伴后，此会话才能继续。</span><span class="sxs-lookup"><span data-stu-id="c9c34-156">It cannot be resumed until the other partner has been upgraded.</span></span> <span data-ttu-id="c9c34-157">但主体服务器仍然接受连接，并允许对主体数据库进行数据访问和修改。</span><span class="sxs-lookup"><span data-stu-id="c9c34-157">However, the principal server is still accepting connections and allowing data access and modifications on the principal database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c9c34-158">如果建立新镜像会话，则要求所有服务器实例运行相同版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c9c34-158">Establishing a new mirroring session requires that the server instances all be running the same version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
3.  <span data-ttu-id="c9c34-159">故障转移后，我们建议你在 theprincipal 数据库上运行[DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)命令。</span><span class="sxs-lookup"><span data-stu-id="c9c34-159">After you fail over, we recommend that you run the [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) command on theprincipal database.</span></span>  
  
4.  <span data-ttu-id="c9c34-160">升级在其作为伙伴的所有镜像会话中目前为镜像服务器的每个服务器实例。</span><span class="sxs-lookup"><span data-stu-id="c9c34-160">Upgrade each server instance that is now the mirror server in all mirroring sessions in which it is a partner.</span></span> <span data-ttu-id="c9c34-161">此时，可能需要更新多个服务器。</span><span class="sxs-lookup"><span data-stu-id="c9c34-161">You might have to update multiple servers at this point.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="c9c34-162">在复杂的镜像配置中，某个服务器实例在一个或多个镜像会话中可能仍作为原始主体服务器。</span><span class="sxs-lookup"><span data-stu-id="c9c34-162">In a complex mirroring configuration, some server instance might still be the original principal server in one or more mirroring sessions.</span></span> <span data-ttu-id="c9c34-163">对这些服务器实例重复步骤 2-4，直至涉及的所有实例均已升级。</span><span class="sxs-lookup"><span data-stu-id="c9c34-163">Repeat steps 2-4 for those server instances until all instances involved are upgraded.</span></span>  
  
5.  <span data-ttu-id="c9c34-164">继续镜像会话。</span><span class="sxs-lookup"><span data-stu-id="c9c34-164">Resume the mirroring session.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c9c34-165">升级完见证服务器并将其重新添加到镜像会话中之后，自动故障转移功能才会起作用。</span><span class="sxs-lookup"><span data-stu-id="c9c34-165">Automatic failover will not work until the witness has been upgraded and added back into the mirroring session.</span></span>  
  
6.  <span data-ttu-id="c9c34-166">升级在其所有镜像会话中为见证服务器的任何剩余服务器实例。</span><span class="sxs-lookup"><span data-stu-id="c9c34-166">Upgrade any remaining server instance that is the witness in all its mirroring sessions.</span></span> <span data-ttu-id="c9c34-167">在已升级的见证服务器重新加入镜像会话之后，自动故障转移功能将重新变为可用。</span><span class="sxs-lookup"><span data-stu-id="c9c34-167">After an upgraded witness rejoins a mirroring session, automatic failover becomes possible again.</span></span> <span data-ttu-id="c9c34-168">此时，可能需要更新多个服务器。</span><span class="sxs-lookup"><span data-stu-id="c9c34-168">You might have to update multiple servers at this point.</span></span>  
  
### <a name="to-return-a-session-to-high-performance-mode"></a><span data-ttu-id="c9c34-169">将会话恢复为高性能模式</span><span class="sxs-lookup"><span data-stu-id="c9c34-169">To return a session to high-performance mode</span></span>  
  
1.  <span data-ttu-id="c9c34-170">可以选择使用下列方法之一返回高性能模式：</span><span class="sxs-lookup"><span data-stu-id="c9c34-170">Optionally, return to high-performance mode by using one of the following methods:</span></span>  
  
    -   <span data-ttu-id="c9c34-171">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中：使用“数据库属性”对话框中的[镜像页](../../relational-databases/databases/database-properties-mirroring-page.md)将“操作模式”选项更改为“高性能(同步)”  。</span><span class="sxs-lookup"><span data-stu-id="c9c34-171">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]: Change the **Operating mode** option to **High performance (asynchronous)** by using the [Mirroring Page](../../relational-databases/databases/database-properties-mirroring-page.md) of the **Database Properties** dialog box.</span></span>  
  
    -   <span data-ttu-id="c9c34-172">在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 中：使用 [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) 将事务安全设置为 OFF。</span><span class="sxs-lookup"><span data-stu-id="c9c34-172">In [!INCLUDE[tsql](../../includes/tsql-md.md)]: Use [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring)to set transaction safety to OFF.</span></span>  
  
### <a name="to-add-a-witness-back-into-a-mirroring-session"></a><span data-ttu-id="c9c34-173">将见证服务器重新添加到镜像会话中</span><span class="sxs-lookup"><span data-stu-id="c9c34-173">To add a witness back into a mirroring session</span></span>  
  
1.  <span data-ttu-id="c9c34-174">在高安全模式下，可以选择让见证服务器重新回到每个镜像会话中。</span><span class="sxs-lookup"><span data-stu-id="c9c34-174">Optionally, in high-safety mode, reestablish the witness to each mirroring session.</span></span>  
  
     <span data-ttu-id="c9c34-175">**返回见证服务器**</span><span class="sxs-lookup"><span data-stu-id="c9c34-175">**To return a witness**</span></span>  
  
    -   [<span data-ttu-id="c9c34-176">添加或替换数据库镜像见证服务器 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="c9c34-176">Add or Replace a Database Mirroring Witness &#40;SQL Server Management Studio&#41;</span></span>](add-or-replace-a-database-mirroring-witness-sql-server-management-studio.md)  
  
    -   [<span data-ttu-id="c9c34-177">使用 Windows 身份验证添加数据库镜像见证服务器 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="c9c34-177">Add a Database Mirroring Witness Using Windows Authentication &#40;Transact-SQL&#41;</span></span>](add-a-database-mirroring-witness-using-windows-authentication-transact-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="c9c34-178">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c9c34-178">See Also</span></span>  
 <span data-ttu-id="c9c34-179">[ALTER DATABASE 数据库镜像 (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) </span><span class="sxs-lookup"><span data-stu-id="c9c34-179">[ALTER DATABASE Database Mirroring &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) </span></span>  
 <span data-ttu-id="c9c34-180">[BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c9c34-180">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="c9c34-181">[查看镜像数据库的状态 (SQL Server Management Studio)](view-the-state-of-a-mirrored-database-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="c9c34-181">[View the State of a Mirrored Database &#40;SQL Server Management Studio&#41;](view-the-state-of-a-mirrored-database-sql-server-management-studio.md) </span></span>  
 <span data-ttu-id="c9c34-182">[数据库镜像 (SQL Server)](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="c9c34-182">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="c9c34-183">[在系统上安装 Service Pack，并且镜像数据库的停机时间最短](../install-a-service-pack-on-a-system-with-minimal-downtime-for-mirrored-databases.md) </span><span class="sxs-lookup"><span data-stu-id="c9c34-183">[Install a Service Pack on a System with Minimal Downtime for Mirrored Databases](../install-a-service-pack-on-a-system-with-minimal-downtime-for-mirrored-databases.md) </span></span>  
 <span data-ttu-id="c9c34-184">[数据库镜像会话期间的角色切换 (SQL Server)](role-switching-during-a-database-mirroring-session-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="c9c34-184">[Role Switching During a Database Mirroring Session &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md) </span></span>  
 <span data-ttu-id="c9c34-185">[在数据库镜像会话中强制服务 (Transact-SQL)](force-service-in-a-database-mirroring-session-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="c9c34-185">[Force Service in a Database Mirroring Session &#40;Transact-SQL&#41;](force-service-in-a-database-mirroring-session-transact-sql.md) </span></span>  
 <span data-ttu-id="c9c34-186">[启动数据库镜像监视器 (SQL Server Management Studio)](start-database-mirroring-monitor-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="c9c34-186">[Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;](start-database-mirroring-monitor-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="c9c34-187">数据库镜像运行模式</span><span class="sxs-lookup"><span data-stu-id="c9c34-187">Database Mirroring Operating Modes</span></span>](database-mirroring-operating-modes.md)  
  
  
