---
title: 数据库镜像的先决条件、限制和建议 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], deployment
- partners [SQL Server]
- database mirroring [SQL Server], prerequisites
- database mirroring [SQL Server], recommendations
- database mirroring [SQL Server], restrictions
- database mirroring [SQL Server], planning
- database mirroring [SQL Server], about database mirroring
ms.assetid: fdcf2251-9895-44c6-b81e-768fef32e732
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0dc29dbdc8432a4abd197a2a1a3f15b6ff5f6d52
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690123"
---
# <a name="prerequisites-restrictions-and-recommendations-for-database-mirroring"></a><span data-ttu-id="9de3a-102">数据库镜像的前提条件、限制和建议</span><span class="sxs-lookup"><span data-stu-id="9de3a-102">Prerequisites, Restrictions, and Recommendations for Database Mirroring</span></span>
    
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] <span data-ttu-id="9de3a-103">改为使用 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="9de3a-103">Use [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] instead.</span></span>  
  
 <span data-ttu-id="9de3a-104">本主题说明了设置数据库镜像的前提条件和建议。</span><span class="sxs-lookup"><span data-stu-id="9de3a-104">This topic describes the prerequisites and recommendations for setting up database mirroring.</span></span> <span data-ttu-id="9de3a-105">有关数据库镜像的介绍，请参阅 [数据库镜像 (SQL Server)](database-mirroring-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="9de3a-105">For an introduction to database mirroring, see [Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9de3a-106">在 64 位和 32 位环境中，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 磁盘存储格式均相同。</span><span class="sxs-lookup"><span data-stu-id="9de3a-106">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on-disk storage format is the same in the 64-bit and 32-bit environments.</span></span> <span data-ttu-id="9de3a-107">因此，数据库镜像会话可以将在 32 位环境中运行的服务器实例和在 64 位环境中运行的服务器实例组合在一起。</span><span class="sxs-lookup"><span data-stu-id="9de3a-107">Therefore, a database mirroring session can combine server instances that run in a 32-bit environment and server instances that run in a 64-bit environment.</span></span>  
  

  
##  <a name="support-for-database-mirroring"></a><a name="DbmSupport"></a><span data-ttu-id="9de3a-108">支持数据库镜像</span><span class="sxs-lookup"><span data-stu-id="9de3a-108">Support For Database Mirroring</span></span>  
 <span data-ttu-id="9de3a-109">有关 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中数据库镜像支持的详细信息，请参阅 [SQL Server 2014 各个版本支持的功能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="9de3a-109">For information about support for database mirroring in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
 <span data-ttu-id="9de3a-110">请注意，数据库镜像可使用任意支持的数据库兼容级别。</span><span class="sxs-lookup"><span data-stu-id="9de3a-110">Note that database mirroring works with any supported database compatibility level.</span></span> <span data-ttu-id="9de3a-111">有关支持的兼容级别的信息，请参阅 [ALTER DATABASE 兼容级别 (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level)。</span><span class="sxs-lookup"><span data-stu-id="9de3a-111">For information about the supported compatibility levels, see [ALTER DATABASE Compatibility Level &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level).</span></span>  
  

  
##  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="9de3a-112">先决条件</span><span class="sxs-lookup"><span data-stu-id="9de3a-112">Prerequisites</span></span>  
  
-   <span data-ttu-id="9de3a-113">若要建立镜像会话，伙伴双方和见证服务器（如果有）必须在相同版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]上运行。</span><span class="sxs-lookup"><span data-stu-id="9de3a-113">For a mirroring session to be established, the partners and the witness, if any, must be running on the same version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="9de3a-114">确保两个伙伴（即主体服务器和镜像服务器）必须运行相同版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="9de3a-114">The two partners, that is the principal server and mirror server, must be running the same edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9de3a-115">见证服务器（如果有）在任意支持数据库镜像的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本上运行。</span><span class="sxs-lookup"><span data-stu-id="9de3a-115">The witness, if any, can run on any edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that supports database mirroring.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9de3a-116">您可以将作为镜像会话中的伙伴的服务器实例升级到较新版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="9de3a-116">You can upgrade server instances that are partners in a mirroring session to a more recent version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9de3a-117">有关详细信息，请参阅 [Minimize Downtime for Mirrored Databases When Upgrading Server Instances](upgrading-mirrored-instances.md)。</span><span class="sxs-lookup"><span data-stu-id="9de3a-117">For more information, see [Minimize Downtime for Mirrored Databases When Upgrading Server Instances](upgrading-mirrored-instances.md).</span></span>  
  
-   <span data-ttu-id="9de3a-118">数据库必须使用完整恢复模式。</span><span class="sxs-lookup"><span data-stu-id="9de3a-118">The database must use the full recovery model.</span></span> <span data-ttu-id="9de3a-119">简单恢复模式和大容量日志恢复模式不支持数据库镜像。</span><span class="sxs-lookup"><span data-stu-id="9de3a-119">The simple and bulk-logged recovery models do not support database mirroring.</span></span> <span data-ttu-id="9de3a-120">因此，镜像数据库的大容量操作始终被完整地记入日志。</span><span class="sxs-lookup"><span data-stu-id="9de3a-120">Therefore, bulk operations are always fully logged for a mirrored database.</span></span> <span data-ttu-id="9de3a-121">有关恢复模式的信息，请参阅[恢复模式 (SQL Server)](../../relational-databases/backup-restore/recovery-models-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="9de3a-121">For information about recovery models, see [Recovery Models &#40;SQL Server&#41;](../../relational-databases/backup-restore/recovery-models-sql-server.md).</span></span>  
  
-   <span data-ttu-id="9de3a-122">验证镜像服务器是否能为镜像数据库提供足够的磁盘空间。</span><span class="sxs-lookup"><span data-stu-id="9de3a-122">Verify that the mirror server has sufficient disk space for the mirror database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9de3a-123">有关如何对复制数据库使用数据库镜像的信息，请参阅[数据库镜像和复制 (SQL Server)](database-mirroring-and-replication-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="9de3a-123">For information about how to use database mirroring on a replicated database, see [Database Mirroring and Replication &#40;SQL Server&#41;](database-mirroring-and-replication-sql-server.md).</span></span>  
  
-   <span data-ttu-id="9de3a-124">在镜像服务器上创建镜像数据库时，请确保指定相同数据库名称 WITH NORECOVERY 来还原主体数据库备份。</span><span class="sxs-lookup"><span data-stu-id="9de3a-124">When you are creating the mirror database on the mirror server, make sure that you restore the backup of the principal database specifying the same database name WITH NORECOVERY.</span></span> <span data-ttu-id="9de3a-125">另外，还必须通过 WITH NORECOVERY 应用在该备份执行后创建的所有日志备份。</span><span class="sxs-lookup"><span data-stu-id="9de3a-125">Also, all log backups that were created after that backup was taken must also be applied, again WITH NORECOVERY.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="9de3a-126">如果数据库镜像已经停止，则必须将对主体数据库执行的所有后续日志备份应用到镜像数据库中，然后才可以重新启动镜像。</span><span class="sxs-lookup"><span data-stu-id="9de3a-126">If database mirroring has been stopped, before you can restart it, any subsequent log backups taken on the principal database must be applied to the mirror database.</span></span>  
  

  
##  <a name="restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="9de3a-127">限制</span><span class="sxs-lookup"><span data-stu-id="9de3a-127">Restrictions</span></span>  
  
-   <span data-ttu-id="9de3a-128">只能镜像用户数据库。</span><span class="sxs-lookup"><span data-stu-id="9de3a-128">Only user databases can be mirrored.</span></span> <span data-ttu-id="9de3a-129">不能镜像 **master**、 **msdb**、 **tempdb**或 **model** 数据库。</span><span class="sxs-lookup"><span data-stu-id="9de3a-129">You cannot mirror the **master**, **msdb**, **tempdb**, or **model** databases.</span></span>  
  
-   <span data-ttu-id="9de3a-130">镜像的数据库在数据库镜像会话过程中不能重命名。</span><span class="sxs-lookup"><span data-stu-id="9de3a-130">A mirrored database cannot be renamed during a database mirroring session.</span></span>  
  
-   <span data-ttu-id="9de3a-131">数据库镜像不支持 FILESTREAM。</span><span class="sxs-lookup"><span data-stu-id="9de3a-131">Database mirroring does not support FILESTREAM.</span></span> <span data-ttu-id="9de3a-132">不能在主体服务器上创建 FILESTREAM 文件组。</span><span class="sxs-lookup"><span data-stu-id="9de3a-132">A FILESTREAM filegroup cannot be created on the principal server.</span></span> <span data-ttu-id="9de3a-133">不能为包含 FILESTREAM 文件组的数据库配置数据库镜像。</span><span class="sxs-lookup"><span data-stu-id="9de3a-133">Database mirroring cannot be configured for a database that contains FILESTREAM filegroups.</span></span>  
  
-   <span data-ttu-id="9de3a-134">在 32 位系统上，由于受每个数据库镜像会话所占用的工作线程数限制，对于每个服务器实例，数据库镜像最多支持 10 个数据库。</span><span class="sxs-lookup"><span data-stu-id="9de3a-134">On a 32-bit system, database mirroring can support a maximum of about 10 databases per server instance because of the numbers of worker threads that are consumed by each database mirroring session.</span></span>  
  
-   <span data-ttu-id="9de3a-135">跨数据库事务和分布式事务均不支持数据库镜像。</span><span class="sxs-lookup"><span data-stu-id="9de3a-135">Database mirroring is not supported with either cross-database transactions or distributed transactions.</span></span> <span data-ttu-id="9de3a-136">有关详细信息，请参阅[数据库镜像或 AlwaysOn 可用性组不支持跨数据库事务 (SQL Server)](../availability-groups/windows/transactions-always-on-availability-and-database-mirroring.md)。</span><span class="sxs-lookup"><span data-stu-id="9de3a-136">For more information, see [Cross-Database Transactions Not Supported For Database Mirroring or AlwaysOn Availability Groups &#40;SQL Server&#41;](../availability-groups/windows/transactions-always-on-availability-and-database-mirroring.md).</span></span>  
  

  
##  <a name="recommendations-for-configuring-partner-servers"></a><a name="RecommendationsForPartners"></a><span data-ttu-id="9de3a-137">配置伙伴服务器的建议</span><span class="sxs-lookup"><span data-stu-id="9de3a-137">Recommendations for Configuring Partner Servers</span></span>  
  
-   <span data-ttu-id="9de3a-138">应该在可以处理相同工作负荷的类似系统上运行伙伴。</span><span class="sxs-lookup"><span data-stu-id="9de3a-138">The partners should run on comparable systems that can handle identical workloads.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9de3a-139">如果计划使用具有自动故障转移功能的高安全性模式，则每个故障转移伙伴上的正常负载应小于 50％ 的 CPU。</span><span class="sxs-lookup"><span data-stu-id="9de3a-139">If you plan to use high-safety mode with automatic failover, the normal load on each failover partner should be less than 50 percent of the CPU.</span></span> <span data-ttu-id="9de3a-140">如果工作负荷超过 CPU 负荷，则故障转移伙伴可能无法对镜像会话中的其他服务器实例使用 ping 命令。</span><span class="sxs-lookup"><span data-stu-id="9de3a-140">If your work load overloads the CPU, a failover partner might be unable to ping the other server instances in the mirroring session.</span></span> <span data-ttu-id="9de3a-141">这将导致不必要的故障转移。</span><span class="sxs-lookup"><span data-stu-id="9de3a-141">This causes a unnecessary failover.</span></span> <span data-ttu-id="9de3a-142">如果无法保持 CPU 使用率始终在 50％ 以下，则建议使用不带自动故障转移功能的高安全性模式或使用高性能模式。</span><span class="sxs-lookup"><span data-stu-id="9de3a-142">If you cannot keep the CPU usage under 50 percent, we recommend that you use either high-safety mode without automatic failover or high-performance mode.</span></span>  
  
-   <span data-ttu-id="9de3a-143">如有可能，镜像数据库的路径（包括驱动器号）应该与主体数据库的路径相同。</span><span class="sxs-lookup"><span data-stu-id="9de3a-143">If possible, the path (including the drive letter) of the mirror database should be identical to the path of the principal database.</span></span> <span data-ttu-id="9de3a-144">如果文件布局必须有所不同，则必须在 RESTORE 语句中包括 MOVE 选项。</span><span class="sxs-lookup"><span data-stu-id="9de3a-144">You must include the MOVE option in the RESTORE statement if the file layouts must differ.</span></span> <span data-ttu-id="9de3a-145">例如，如果主体数据库位于“F:”驱动器上，但镜像系统没有“F:”驱动器。</span><span class="sxs-lookup"><span data-stu-id="9de3a-145">For example, if the principal database is on drive 'F:' but the mirror system lacks an F: drive.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="9de3a-146">如果在创建镜像数据库时移动了数据库文件，则可能导致以后不挂起镜像就无法向数据库添加文件。</span><span class="sxs-lookup"><span data-stu-id="9de3a-146">If you move the database files when you create the mirror database, you might be unable to add files to the database later without mirroring being suspended.</span></span>  
  
-   <span data-ttu-id="9de3a-147">镜像会话中的所有服务器实例都应该使用相同的主代码页和排序规则。</span><span class="sxs-lookup"><span data-stu-id="9de3a-147">All of the server instances in a mirroring session should use the same master code page and collation.</span></span> <span data-ttu-id="9de3a-148">如果使用不同的主代码页和排序规则，则在镜像设置期间可能会出现问题。</span><span class="sxs-lookup"><span data-stu-id="9de3a-148">Differences can cause a problem during mirroring setup.</span></span>  
  
-   <span data-ttu-id="9de3a-149">（可选）估计故障转移数据库的时间，以确保系统配置能提供所需性能。</span><span class="sxs-lookup"><span data-stu-id="9de3a-149">Optionally, estimate the time to fail over a database, to make sure that the system configuration will provide the performance you require.</span></span> <span data-ttu-id="9de3a-150">有关详细信息，请参阅 [估计在角色切换期间服务的中断（数据库镜像）](estimate-the-interruption-of-service-during-role-switching-database-mirroring.md)。</span><span class="sxs-lookup"><span data-stu-id="9de3a-150">For more information, see [Estimate the Interruption of Service During Role Switching &#40;Database Mirroring&#41;](estimate-the-interruption-of-service-during-role-switching-database-mirroring.md).</span></span>  
  
-   <span data-ttu-id="9de3a-151">为获得最佳性能，请为镜像使用专用网络适配器（网络接口卡）。</span><span class="sxs-lookup"><span data-stu-id="9de3a-151">For best performance, use a dedicated network adapter (network interface card) for mirroring.</span></span>  
  
-   <span data-ttu-id="9de3a-152">关于广域网 (WAN) 对高安全性模式下的数据库镜像是否足够可靠，我们没有任何建议。</span><span class="sxs-lookup"><span data-stu-id="9de3a-152">We make no recommendations about whether a wide-area network (WAN) is reliable enough for database mirroring in high-safety mode.</span></span> <span data-ttu-id="9de3a-153">如果您决定在 WAN 上使用高安全性模式，则应注意将见证服务器添加至会话的方式，因为可能会发生意外的自动故障转移。</span><span class="sxs-lookup"><span data-stu-id="9de3a-153">If you decide to use high-safety mode over a WAN, be cautious about how you add a witness to the session, because unwanted automatic failovers can occur.</span></span> <span data-ttu-id="9de3a-154">有关详细信息，请参阅本主题稍后部分中的 [部署数据库镜像的建议](#RecommendationsForDeploying)。</span><span class="sxs-lookup"><span data-stu-id="9de3a-154">For more information, see [Recommendations for Deploying Database Mirroring](#RecommendationsForDeploying), later in this topic.</span></span>  
  

  
##  <a name="recommendations-for-deploying-database-mirroring"></a><a name="RecommendationsForDeploying"></a><span data-ttu-id="9de3a-155">部署数据库镜像的建议</span><span class="sxs-lookup"><span data-stu-id="9de3a-155">Recommendations for Deploying Database Mirroring</span></span>  
 <span data-ttu-id="9de3a-156">使用异步操作可获得最佳的数据库镜像性能。</span><span class="sxs-lookup"><span data-stu-id="9de3a-156">Optimal database mirroring performance is obtained by using asynchronous operation.</span></span> <span data-ttu-id="9de3a-157">如果镜像会话使用同步操作，则当该会话的工作负荷生成大量事务日志数据时，可能会降低性能。</span><span class="sxs-lookup"><span data-stu-id="9de3a-157">A mirroring session that uses synchronous operation might experience slowed performance when its workload generates large amounts of transaction log data.</span></span>  
  
 <span data-ttu-id="9de3a-158">在测试环境中，应当研究所有运行模式以评估数据库镜像的执行效率。</span><span class="sxs-lookup"><span data-stu-id="9de3a-158">In test environments, it is appropriate to explore all the operating modes to evaluate how database mirroring performs.</span></span> <span data-ttu-id="9de3a-159">但是，在生产环境中部署镜像之前，务必要了解网络在实际环境中的运行方式。</span><span class="sxs-lookup"><span data-stu-id="9de3a-159">However, before you deploy mirroring into a production environment, make sure that you understand how the network functions in the real world.</span></span>  
  
 <span data-ttu-id="9de3a-160">具有自动故障转移功能的高安全性模式专用于具有专用连接或非常简单的网络配置的高级服务网络，它可最大程度地减少可能的网络故障源。</span><span class="sxs-lookup"><span data-stu-id="9de3a-160">High-safety mode with automatic failover is designed for a high-service network that has either a dedicated connection or a fairly simple network configuration that minimizes the sources of possible network failures.</span></span> <span data-ttu-id="9de3a-161">这种高质量的网络环境对于具有自动故障转移功能的高安全性模式而言是必需的，同时也建议将其用于所有数据库镜像会话。</span><span class="sxs-lookup"><span data-stu-id="9de3a-161">Such a high-quality network environment is necessary for high-safety mode with automatic failover and is recommended for all database mirroring sessions.</span></span> <span data-ttu-id="9de3a-162">但是，网络可靠性对高性能模式和不带自动故障转移功能的高安全性模式具有较小的影响。</span><span class="sxs-lookup"><span data-stu-id="9de3a-162">However, high-performance mode and high-safety mode without automatic failover are much less affected by network reliability.</span></span>  
  
 <span data-ttu-id="9de3a-163">因此，对于生产环境，建议遵守下列部署指南：</span><span class="sxs-lookup"><span data-stu-id="9de3a-163">Therefore, for production environments we recommend that you adhere to the following deployment guidelines:</span></span>  
  
1.  <span data-ttu-id="9de3a-164">在异步、高性能模式下启动运行。</span><span class="sxs-lookup"><span data-stu-id="9de3a-164">Start running in asynchronous, high-performance mode.</span></span> <span data-ttu-id="9de3a-165">此模式受网络环境的影响最小，并为研究镜像的工作方式提供了最佳配置。</span><span class="sxs-lookup"><span data-stu-id="9de3a-165">This mode is the least sensitive to the network environment and provides the best configuration for exploring how mirroring works.</span></span> <span data-ttu-id="9de3a-166">除非您确信自己的带宽支持镜像，并且熟知镜像设置以及异步模式在您环境中的性能，否则，建议异步运行系统。</span><span class="sxs-lookup"><span data-stu-id="9de3a-166">We recommend that you run your system asynchronously until you are confident that your bandwidth supports mirroring and you have developed an understanding of mirroring setup and of the performance of asynchronous mode in your environment.</span></span> <span data-ttu-id="9de3a-167">有关详细信息，请参阅 [Database Mirroring Operating Modes](database-mirroring-operating-modes.md)。</span><span class="sxs-lookup"><span data-stu-id="9de3a-167">For more information, see [Database Mirroring Operating Modes](database-mirroring-operating-modes.md).</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="9de3a-168">建议您在测试过程中监视会话，以便发现导致数据库镜像失败的网络错误。</span><span class="sxs-lookup"><span data-stu-id="9de3a-168">Throughout testing, we recommend that you monitor your sessions for network errors that cause database mirroring to fail.</span></span> <span data-ttu-id="9de3a-169">有关潜在的故障源的详细信息，请参阅 [Possible Failures During Database Mirroring](possible-failures-during-database-mirroring.md)。</span><span class="sxs-lookup"><span data-stu-id="9de3a-169">For more information about potential sources of failure, see [Possible Failures During Database Mirroring](possible-failures-during-database-mirroring.md).</span></span> <span data-ttu-id="9de3a-170">有关如何监视数据库镜像的信息，请参阅[监视数据库镜像 (SQL Server)](monitoring-database-mirroring-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="9de3a-170">For information about how to monitor database mirroring, see [Monitoring Database Mirroring &#40;SQL Server&#41;](monitoring-database-mirroring-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="9de3a-171">在确信异步操作符合您的业务需要之后，您可能希望尝试同步操作来提高数据保护能力。</span><span class="sxs-lookup"><span data-stu-id="9de3a-171">When you are confident that asynchronous operation is meeting the business needs, you might want to try synchronous operation to improve your data protection.</span></span> <span data-ttu-id="9de3a-172">当测试同步镜像在您环境中的工作方式时，建议首先测试不带自动故障转移功能的高安全性模式。</span><span class="sxs-lookup"><span data-stu-id="9de3a-172">When you test how synchronous mirroring works in your environment, we recommend that first you test high-safety mode without automatic failover.</span></span> <span data-ttu-id="9de3a-173">此测试的主要目的是了解同步操作如何影响数据库的性能。</span><span class="sxs-lookup"><span data-stu-id="9de3a-173">The primary purpose of this testing is to see how synchronous operation affects the database performance.</span></span> <span data-ttu-id="9de3a-174">有关详细信息，请参阅 [Database Mirroring Operating Modes](database-mirroring-operating-modes.md)。</span><span class="sxs-lookup"><span data-stu-id="9de3a-174">For more information, see [Database Mirroring Operating Modes](database-mirroring-operating-modes.md).</span></span>  
  
3.  <span data-ttu-id="9de3a-175">等到确信不带自动故障转移功能的高安全性模式满足您的业务需要并且网络错误不会导致故障时再启用自动故障转移。</span><span class="sxs-lookup"><span data-stu-id="9de3a-175">Wait to enable automatic failover until you are confident that high-safety mode without automatic failover is meeting the business needs and that network errors are not causing failures.</span></span> <span data-ttu-id="9de3a-176">有关详细信息，请参阅 [数据库镜像会话期间的角色切换 (SQL Server)](role-switching-during-a-database-mirroring-session-sql-server.md)的各版本中均未提供见证服务器实例。</span><span class="sxs-lookup"><span data-stu-id="9de3a-176">For more information, see [Role Switching During a Database Mirroring Session &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md).</span></span>  
  

  
## <a name="see-also"></a><span data-ttu-id="9de3a-177">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9de3a-177">See Also</span></span>  
 <span data-ttu-id="9de3a-178">[设置数据库镜像 (SQL Server)](setting-up-database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="9de3a-178">[Setting Up Database Mirroring &#40;SQL Server&#41;](setting-up-database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="9de3a-179">[用于数据库镜像和 AlwaysOn 可用性组 &#40;SQL Server 的传输安全&#41;](transport-security-database-mirroring-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="9de3a-179">[Transport Security for Database Mirroring and AlwaysOn Availability Groups &#40;SQL Server&#41;](transport-security-database-mirroring-always-on-availability.md) </span></span>  
 <span data-ttu-id="9de3a-180">[数据库镜像 (SQL Server)](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="9de3a-180">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="9de3a-181">数据库镜像配置故障排除 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="9de3a-181">Troubleshoot Database Mirroring Configuration &#40;SQL Server&#41;</span></span>](troubleshoot-database-mirroring-configuration-sql-server.md)  
  
  
