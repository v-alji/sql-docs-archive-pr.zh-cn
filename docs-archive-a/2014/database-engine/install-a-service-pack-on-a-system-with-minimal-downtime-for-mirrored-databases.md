---
title: 在系统上安装 Service Pack，并且镜像数据库的停机时间最短 |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- hotfixes [SQL Server]
- database mirroring [SQL Server], upgrading system
- rolling upgrades [SQL Server]
- service packs [SQL Server]
- upgrading mirrored database systems
- upgrading SQL Server, mirrored databases
ms.assetid: bdc63142-027d-4ead-9d3e-147331387ef5
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: e878d31ec926f8b2cc460854f422b4d01d32d414
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690793"
---
# <a name="install-a-service-pack-on-a-system-with-minimal-downtime-for-mirrored-databases"></a><span data-ttu-id="1c723-102">在系统上安装 Service Pack 并且尽量缩短镜像数据库停机时间</span><span class="sxs-lookup"><span data-stu-id="1c723-102">Install a Service Pack on a System with Minimal Downtime for Mirrored Databases</span></span>
  <span data-ttu-id="1c723-103">本主题介绍了如何在安装 Service Pack 和修补程序时尽量减少镜像服务器的停机时间。</span><span class="sxs-lookup"><span data-stu-id="1c723-103">This topic describes how to minimize downtime for mirrored databases when you install service packs and hotfixes.</span></span> <span data-ttu-id="1c723-104">此过程包括按顺序升级参与数据库镜像的 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="1c723-104">This process involves sequentially upgrading the instances of [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] that are participating in database mirroring.</span></span> <span data-ttu-id="1c723-105">这种形式的更新称为 "*滚动更新*"，可将停机时间减少为只进行一次故障转移。</span><span class="sxs-lookup"><span data-stu-id="1c723-105">This form of update, which is known as a *rolling update*, reduces downtime to only a single failover.</span></span> <span data-ttu-id="1c723-106">请注意，对于镜像服务器与主体服务器在地理位置上有一定距离的高性能模式会话而言，滚动更新可能不适合。</span><span class="sxs-lookup"><span data-stu-id="1c723-106">Note that for high-performance mode sessions in which the mirror server is geographically distant from the principal server, a rolling update might be inappropriate.</span></span>  
  
 <span data-ttu-id="1c723-107">滚动更新是包含下列阶段的一个多阶段过程：</span><span class="sxs-lookup"><span data-stu-id="1c723-107">A rolling update is a multi-stage process that consists of the following stages:</span></span>  
  
-   <span data-ttu-id="1c723-108">保护数据。</span><span class="sxs-lookup"><span data-stu-id="1c723-108">Protect your data.</span></span>  
  
-   <span data-ttu-id="1c723-109">如果会话包括见证服务器，建议您删除见证服务器。</span><span class="sxs-lookup"><span data-stu-id="1c723-109">If the session includes a witness, we recommend that you remove the witness.</span></span> <span data-ttu-id="1c723-110">否则，在更新镜像服务器实例时，数据库的可用性将取决于仍然连接至主体服务器实例的见证服务器。</span><span class="sxs-lookup"><span data-stu-id="1c723-110">Otherwise, when the mirror server instance is being updated, database availability depends on the witness that remains connected to the principal server instance.</span></span> <span data-ttu-id="1c723-111">删除见证服务器之后，可以在滚动更新过程中随时对其进行更新，而不会有数据库停机的风险。</span><span class="sxs-lookup"><span data-stu-id="1c723-111">After you remove a witness, you can update it at any time during the rolling update process without risking database downtime.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1c723-112">有关详细信息，请参阅[仲裁：见证服务器如何影响数据库可用性（数据库镜像）](database-mirroring/quorum-how-a-witness-affects-database-availability-database-mirroring.md)。</span><span class="sxs-lookup"><span data-stu-id="1c723-112">For more information, see [Quorum: How a Witness Affects Database Availability &#40;Database Mirroring&#41;](database-mirroring/quorum-how-a-witness-affects-database-availability-database-mirroring.md).</span></span>  
  
-   <span data-ttu-id="1c723-113">如果会话在高性能模式下运行，则将运行模式更改为高安全模式。</span><span class="sxs-lookup"><span data-stu-id="1c723-113">If a session is running in high-performance mode, change the operating mode to high-safety mode.</span></span>  
  
-   <span data-ttu-id="1c723-114">更新数据库镜像中涉及的每个服务器实例。</span><span class="sxs-lookup"><span data-stu-id="1c723-114">Update each server instance that is involved in database mirroring.</span></span> <span data-ttu-id="1c723-115">滚动更新包括升级当前作为镜像服务器的服务器实例，对其每个镜像数据库进行手动故障转移以及升级最初作为主体服务器（现在作为新镜像服务器）的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="1c723-115">A rolling update involves upgrading the server instance that is currently the mirror server, manually failing over each of its mirrored databases, and upgrading the server instance that was first the principal server (and is now the new mirror server).</span></span> <span data-ttu-id="1c723-116">此时，必须继续镜像。</span><span class="sxs-lookup"><span data-stu-id="1c723-116">At this point, you will have to resume mirroring.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1c723-117">在开始滚动更新之前，建议您至少对一个镜像会话执行实际手动故障转移。</span><span class="sxs-lookup"><span data-stu-id="1c723-117">Before starting a rolling update, we recommend that you perform a practice manual failover on at least one of your mirroring sessions.</span></span>  
  
-   <span data-ttu-id="1c723-118">如有必要，则恢复为高性能模式。</span><span class="sxs-lookup"><span data-stu-id="1c723-118">Revert to high-performance mode, if it is required.</span></span>  
  
-   <span data-ttu-id="1c723-119">如有必要，则将见证服务器返回镜像会话。</span><span class="sxs-lookup"><span data-stu-id="1c723-119">Return the witness to the mirroring session, if it is required.</span></span>  
  
 <span data-ttu-id="1c723-120">下面将介绍各个阶段的过程。</span><span class="sxs-lookup"><span data-stu-id="1c723-120">The procedures for these stages are described here.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="1c723-121">在并发镜像会话中，一个服务器实例可能扮演不同的镜像角色（主体服务器、镜像服务器或见证服务器）。</span><span class="sxs-lookup"><span data-stu-id="1c723-121">A server instance might be performing different mirroring roles (principal server, mirror server, or witness) in concurrent mirroring sessions.</span></span> <span data-ttu-id="1c723-122">在这种情况下，必须相应地调整基本滚动更新过程。</span><span class="sxs-lookup"><span data-stu-id="1c723-122">In this case, you will have to adapt the basic rolling update process accordingly.</span></span>  
  
### <a name="to-protect-your-data-before-an-update-a-best-practice"></a><span data-ttu-id="1c723-123">在更新之前保护数据（最佳做法）</span><span class="sxs-lookup"><span data-stu-id="1c723-123">To protect your data before an update (a best practice)</span></span>  
  
1.  <span data-ttu-id="1c723-124">对每个主体数据库执行完整数据库备份。</span><span class="sxs-lookup"><span data-stu-id="1c723-124">Perform a full database backup on every principal database.</span></span>  
  
     <span data-ttu-id="1c723-125">**备份数据库**</span><span class="sxs-lookup"><span data-stu-id="1c723-125">**To back up a database**</span></span>  
  
    -   <span data-ttu-id="1c723-126">[创建完整数据库备份 (SQL Server)](../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="1c723-126">[Create a Full Database Backup &#40;SQL Server&#41;](../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="1c723-127">在每个主体服务器上运行 [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) 命令。</span><span class="sxs-lookup"><span data-stu-id="1c723-127">Run the [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) command on every principal database.</span></span>  
  
### <a name="to-remove-a-witness-from-a-session"></a><span data-ttu-id="1c723-128">从会话中删除见证服务器</span><span class="sxs-lookup"><span data-stu-id="1c723-128">To remove a witness from a session</span></span>  
  
1.  <span data-ttu-id="1c723-129">如果镜像会话包括见证服务器，则建议您在执行滚动更新之前删除该见证服务器。</span><span class="sxs-lookup"><span data-stu-id="1c723-129">If a mirroring session involves a witness, we recommend that you remove the witness before you perform a rolling update.</span></span>  
  
     <span data-ttu-id="1c723-130">**删除见证服务器**</span><span class="sxs-lookup"><span data-stu-id="1c723-130">**To remove the witness**</span></span>  
  
    -   [<span data-ttu-id="1c723-131">从数据库镜像会话删除见证服务器 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="1c723-131">Remove the Witness from a Database Mirroring Session &#40;SQL Server&#41;</span></span>](database-mirroring/remove-the-witness-from-a-database-mirroring-session-sql-server.md)  
  
### <a name="to-change-a-session-from-high-performance-mode-to-high-safety-mode"></a><span data-ttu-id="1c723-132">将会话从高性能模式更改为高安全模式</span><span class="sxs-lookup"><span data-stu-id="1c723-132">To change a session from high-performance mode to high-safety mode</span></span>  
  
1.  <span data-ttu-id="1c723-133">如果镜像会话在高性能模式下运行，则在执行滚动更新之前，将运行模式更改为不带自动故障转移功能的高安全模式。</span><span class="sxs-lookup"><span data-stu-id="1c723-133">If a mirroring session is running in high-performance mode, before you perform a rolling update, change the operating mode to high safety without automatic failover.</span></span> <span data-ttu-id="1c723-134">使用以下方法之一：</span><span class="sxs-lookup"><span data-stu-id="1c723-134">Use one of the following methods:</span></span>  
  
    -   <span data-ttu-id="1c723-135">在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中：使用“数据库属性”对话框中的[镜像页](../relational-databases/databases/database-properties-mirroring-page.md)将“操作模式”选项更改为“不带自动故障转移功能的高安全(同步)”  。</span><span class="sxs-lookup"><span data-stu-id="1c723-135">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]: Change the **Operating mode** option to **High safety without automatic failover (synchronous)** by using the [Mirroring Page](../relational-databases/databases/database-properties-mirroring-page.md) of the **Database Properties** dialog box.</span></span> <span data-ttu-id="1c723-136">有关如何访问此页的详细信息，请参阅[启动配置数据库镜像安全向导 (SQL Server Management Studio)](database-mirroring/start-the-configuring-database-mirroring-security-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="1c723-136">For information about how to access this page, see [Start the Configuring Database Mirroring Security Wizard &#40;SQL Server Management Studio&#41;](database-mirroring/start-the-configuring-database-mirroring-security-wizard.md).</span></span>  
  
    -   <span data-ttu-id="1c723-137">在 [!INCLUDE[tsql](../includes/tsql-md.md)] 中：将事务安全设置为 FULL。</span><span class="sxs-lookup"><span data-stu-id="1c723-137">In [!INCLUDE[tsql](../includes/tsql-md.md)]: Set transaction safety to FULL.</span></span> <span data-ttu-id="1c723-138">有关详细信息，请参阅[更改数据库镜像会话中的事务安全 (Transact-SQL)](database-mirroring/change-transaction-safety-in-a-database-mirroring-session-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="1c723-138">For more information, see [Change Transaction Safety in a Database Mirroring Session &#40;Transact-SQL&#41;](database-mirroring/change-transaction-safety-in-a-database-mirroring-session-transact-sql.md).</span></span>  
  
### <a name="to-perform-the-rolling-update"></a><span data-ttu-id="1c723-139">执行滚动更新</span><span class="sxs-lookup"><span data-stu-id="1c723-139">To perform the rolling update</span></span>  
  
1.  <span data-ttu-id="1c723-140">为了最大限度地减少停机时间，我们建议：通过更新任何当前在其所有镜像会话中均为镜像服务器的镜像伙伴开始滚动更新。</span><span class="sxs-lookup"><span data-stu-id="1c723-140">To minimize downtime, we recommend the following: Start the rolling update by updating any mirroring partner that is currently the mirror server in all its mirroring sessions.</span></span> <span data-ttu-id="1c723-141">此时，可能需要更新多个服务器实例。</span><span class="sxs-lookup"><span data-stu-id="1c723-141">You might have to update multiple server instances at this point.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1c723-142">在滚动更新过程中可以随时更新见证服务器。</span><span class="sxs-lookup"><span data-stu-id="1c723-142">A witness can be updated at any point in the rolling update process.</span></span> <span data-ttu-id="1c723-143">例如，如果某个服务器实例在会话 1 中为镜像服务器，在会话 2 中为见证服务器，则可以立即更新此服务器实例。</span><span class="sxs-lookup"><span data-stu-id="1c723-143">For example, if a server instance is a mirror server in Session 1 and is a witness in Session 2, you can update the server instance now.</span></span>  
  
     <span data-ttu-id="1c723-144">要首先更新的服务器实例是由镜像会话的当前配置决定的，如下所示：</span><span class="sxs-lookup"><span data-stu-id="1c723-144">The server instance to update first depends on the current configuration of your mirroring sessions, as follows:</span></span>  
  
    -   <span data-ttu-id="1c723-145">如果有任何服务器实例已经是其所有镜像会话中的镜像服务器，则在该服务器实例上安装 Service Pack 或修补程序。</span><span class="sxs-lookup"><span data-stu-id="1c723-145">If any server instance is already the mirror server in all of its mirroring sessions, install the service pack or the hotfix on that server instance.</span></span>  
  
    -   <span data-ttu-id="1c723-146">如果在任何镜像会话中所有服务器实例当前都是主体服务器，则选择一个服务器实例首先更新。</span><span class="sxs-lookup"><span data-stu-id="1c723-146">If all of your server instances are currently the principal server in any mirroring sessions, select one server instance to update first.</span></span> <span data-ttu-id="1c723-147">然后，对其每个主体数据库进行手动故障转移，并通过安装 Service Pack 或修补程序来更新该数据库实例。</span><span class="sxs-lookup"><span data-stu-id="1c723-147">Then, manually fail over each of its principal databases and update that server instance by installing the service pack or the hotfix.</span></span>  
  
     <span data-ttu-id="1c723-148">更新完成后，服务器实例将自动重新加入其每个镜像会话。</span><span class="sxs-lookup"><span data-stu-id="1c723-148">After being updated, a server instance automatically rejoins each of its mirroring sessions.</span></span>  
  
     <span data-ttu-id="1c723-149">**执行手动故障转移**</span><span class="sxs-lookup"><span data-stu-id="1c723-149">**To perform a manual failover**</span></span>  
  
    -   [<span data-ttu-id="1c723-150">手动故障转移数据库镜像会话 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="1c723-150">Manually Fail Over a Database Mirroring Session &#40;SQL Server Management Studio&#41;</span></span>](database-mirroring/manually-fail-over-a-database-mirroring-session-sql-server-management-studio.md)  
  
    -   <span data-ttu-id="1c723-151">[手动故障转移数据库镜像会话 (Transact-SQL)](database-mirroring/manually-fail-over-a-database-mirroring-session-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="1c723-151">[Manually Fail Over a Database Mirroring Session &#40;Transact-SQL&#41;](database-mirroring/manually-fail-over-a-database-mirroring-session-transact-sql.md).</span></span>  
  
     <span data-ttu-id="1c723-152">有关手动故障转移如何实现的详细信息，请参阅[数据库镜像会话期间的角色切换 (SQL Server)](database-mirroring/role-switching-during-a-database-mirroring-session-sql-server.md) 。</span><span class="sxs-lookup"><span data-stu-id="1c723-152">For information about how manual failover works, see [Role Switching During a Database Mirroring Session &#40;SQL Server&#41;](database-mirroring/role-switching-during-a-database-mirroring-session-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="1c723-153">对于其镜像服务器实例刚完成更新的每个镜像会话，请等待会话进行同步。</span><span class="sxs-lookup"><span data-stu-id="1c723-153">For each mirroring session whose mirror server instance has just been updated, wait for the session to synchronize.</span></span> <span data-ttu-id="1c723-154">然后，连接到主体服务器实例并对会话进行手动故障转移。</span><span class="sxs-lookup"><span data-stu-id="1c723-154">Then, connect to the principal server instance, and manually fail over the session.</span></span> <span data-ttu-id="1c723-155">故障转移后，已更新的服务器实例成为该会话的主体服务器，而以前的主体服务成为镜像服务器。</span><span class="sxs-lookup"><span data-stu-id="1c723-155">On failover, the updated server instance becomes the principal server for that session, and the former principal server becomes the mirror server.</span></span>  
  
     <span data-ttu-id="1c723-156">此步骤的目的是让其他服务器实例在其作为伙伴的每个镜像会话中成为镜像服务器。</span><span class="sxs-lookup"><span data-stu-id="1c723-156">The goal of this step is for another server instance to become the mirror server in every mirroring session in which it is a partner.</span></span>  
  
3.  <span data-ttu-id="1c723-157">完成故障转移后，我们建议您在主体数据库上运行 [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) 命令。</span><span class="sxs-lookup"><span data-stu-id="1c723-157">After you fail over, we recommend that you run the [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) command on the principal database.</span></span>  
  
4.  <span data-ttu-id="1c723-158">对于在其作为伙伴的所有镜像会话中目前为镜像服务器的每个服务器实例，在该服务器实例上安装 Service Pack 或修补程序。</span><span class="sxs-lookup"><span data-stu-id="1c723-158">Install the service pack or the hotfix on each server instance that is now the mirror server in all mirroring sessions in which it is a partner.</span></span> <span data-ttu-id="1c723-159">此时，可能需要更新多个服务器。</span><span class="sxs-lookup"><span data-stu-id="1c723-159">You might have to update multiple servers at this point.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="1c723-160">在复杂的镜像配置中，某个服务器实例在一个或多个镜像会话中可能仍作为原始主体服务器。</span><span class="sxs-lookup"><span data-stu-id="1c723-160">In a complex mirroring configuration, some server instance might still be the original principal server in one or more mirroring sessions.</span></span> <span data-ttu-id="1c723-161">对这些服务器实例重复步骤2-4，直到所有涉及的实例都更新。</span><span class="sxs-lookup"><span data-stu-id="1c723-161">Repeat steps 2-4 for those server instances until all instances involved are updated.</span></span>  
  
5.  <span data-ttu-id="1c723-162">继续镜像会话。</span><span class="sxs-lookup"><span data-stu-id="1c723-162">Resume the mirroring session.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1c723-163">更新完见证服务器后，自动故障转移功能才会起作用。</span><span class="sxs-lookup"><span data-stu-id="1c723-163">Automatic failover will not work until the witness has been updated.</span></span>  
  
6.  <span data-ttu-id="1c723-164">对于在其所有镜像会话中为见证服务器的任何剩余服务器实例，在该服务器实例上安装 Service Pack 或修补程序。</span><span class="sxs-lookup"><span data-stu-id="1c723-164">Install the service packs or hotfixes on any remaining server instance that is the witness in all its mirroring sessions.</span></span> <span data-ttu-id="1c723-165">在已更新的见证服务器重新加入镜像会话之后，自动故障转移功能将重新变为可用。</span><span class="sxs-lookup"><span data-stu-id="1c723-165">After an updated witness rejoins a mirroring session, automatic failover becomes possible again.</span></span> <span data-ttu-id="1c723-166">此时，可能需要更新多个服务器。</span><span class="sxs-lookup"><span data-stu-id="1c723-166">You might have to update multiple servers at this point.</span></span>  
  
### <a name="to-return-a-session-to-high-performance-mode"></a><span data-ttu-id="1c723-167">将会话恢复为高性能模式</span><span class="sxs-lookup"><span data-stu-id="1c723-167">To return a session to high-performance mode</span></span>  
  
1.  <span data-ttu-id="1c723-168">可以选择使用下列方法之一返回高性能模式：</span><span class="sxs-lookup"><span data-stu-id="1c723-168">Optionally, return to high-performance mode by using one of the following methods:</span></span>  
  
    -   <span data-ttu-id="1c723-169">在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中：使用“数据库属性”对话框中的[镜像页](../relational-databases/databases/database-properties-mirroring-page.md)将“操作模式”选项更改为“高性能(同步)”  。</span><span class="sxs-lookup"><span data-stu-id="1c723-169">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]: Change the **Operating mode** option to **High performance (asynchronous)** by using the [Mirroring Page](../relational-databases/databases/database-properties-mirroring-page.md) of the **Database Properties** dialog box.</span></span>  
  
    -   <span data-ttu-id="1c723-170">在中 [!INCLUDE[tsql](../includes/tsql-md.md)] ：使用[ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring)将事务安全设置为 OFF。</span><span class="sxs-lookup"><span data-stu-id="1c723-170">In [!INCLUDE[tsql](../includes/tsql-md.md)]: Use [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) to set transaction safety to OFF.</span></span>  
  
### <a name="to-return-a-witness-to-a-mirroring-session"></a><span data-ttu-id="1c723-171">将见证服务器返回镜像会话</span><span class="sxs-lookup"><span data-stu-id="1c723-171">To return a witness to a mirroring session</span></span>  
  
1.  <span data-ttu-id="1c723-172">在高安全模式下，可以选择让见证服务器重新回到每个镜像会话中。</span><span class="sxs-lookup"><span data-stu-id="1c723-172">Optionally, in high-safety mode, reestablish the witness to each mirroring session.</span></span>  
  
     <span data-ttu-id="1c723-173">**重新设置见证服务器**</span><span class="sxs-lookup"><span data-stu-id="1c723-173">**To reestablish the witness**</span></span>  
  
    -   [<span data-ttu-id="1c723-174">添加或替换数据库镜像见证服务器 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="1c723-174">Add or Replace a Database Mirroring Witness &#40;SQL Server Management Studio&#41;</span></span>](database-mirroring/add-or-replace-a-database-mirroring-witness-sql-server-management-studio.md)  
  
    -   [<span data-ttu-id="1c723-175">使用 Windows 身份验证添加数据库镜像见证服务器 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="1c723-175">Add a Database Mirroring Witness Using Windows Authentication &#40;Transact-SQL&#41;</span></span>](database-mirroring/add-a-database-mirroring-witness-using-windows-authentication-transact-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="1c723-176">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1c723-176">See Also</span></span>  
 <span data-ttu-id="1c723-177">[ALTER DATABASE 数据库镜像 (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) </span><span class="sxs-lookup"><span data-stu-id="1c723-177">[ALTER DATABASE Database Mirroring &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) </span></span>  
 <span data-ttu-id="1c723-178">[BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="1c723-178">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="1c723-179">[数据库镜像 (SQL Server)](database-mirroring/database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1c723-179">[Database Mirroring &#40;SQL Server&#41;](database-mirroring/database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="1c723-180">[数据库镜像运行模式](database-mirroring/database-mirroring-operating-modes.md) </span><span class="sxs-lookup"><span data-stu-id="1c723-180">[Database Mirroring Operating Modes](database-mirroring/database-mirroring-operating-modes.md) </span></span>  
 <span data-ttu-id="1c723-181">[数据库镜像会话期间的角色切换 (SQL Server)](database-mirroring/role-switching-during-a-database-mirroring-session-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1c723-181">[Role Switching During a Database Mirroring Session &#40;SQL Server&#41;](database-mirroring/role-switching-during-a-database-mirroring-session-sql-server.md) </span></span>  
 <span data-ttu-id="1c723-182">[启动数据库镜像监视器 (SQL Server Management Studio)](database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="1c723-182">[Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;](database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="1c723-183">查看镜像数据库的状态 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="1c723-183">View the State of a Mirrored Database &#40;SQL Server Management Studio&#41;</span></span>](database-mirroring/view-the-state-of-a-mirrored-database-sql-server-management-studio.md)  
  
  
