---
title: AlwaysOn 可用性组 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], about
- secondary replicas, see Availability Groups [SQL Server]
- availability [SQL Server]
- AlwaysOn [SQL Server], see Availability Groups [SQL Server]
- Availability Groups [SQL Server]
ms.assetid: aa427606-8422-4656-b205-c9e665ddc8c1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 169d720868a4c721e5f409e97971047ec7b04483
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585990"
---
# <a name="always-on-availability-groups-sql-server"></a><span data-ttu-id="1d9f7-102">AlwaysOn 可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="1d9f7-102">Always On Availability Groups (SQL Server)</span></span>
  <span data-ttu-id="1d9f7-103">[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 功能是一个提供替代数据库镜像的企业级方案的高可用性和灾难恢复解决方案。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-103">The [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] feature is a high-availability and disaster-recovery solution that provides an enterprise-level alternative to database mirroring.</span></span> <span data-ttu-id="1d9f7-104">[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 中引入了 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]功能，此功能可最大程度地提高一组用户数据库对企业的可用性。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-104">Introduced in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] maximizes the availability of a set of user databases for an enterprise.</span></span> <span data-ttu-id="1d9f7-105">*可用性组*支持故障转移的一组离散的用户数据库（称为*可用性数据库*）的故障转移环境。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-105">An *availability group* supports a failover environment for a discrete set of user databases, known as *availability databases*, that fail over together.</span></span> <span data-ttu-id="1d9f7-106">一个可用性组支持一组读写主数据库以及一至八组对应的辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-106">An availability group supports a set of read-write primary databases and one to eight sets of corresponding secondary databases.</span></span> <span data-ttu-id="1d9f7-107">（可选）可使辅助数据库能进行只读访问和/或某些备份操作。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-107">Optionally, secondary databases can be made available for read-only access and/or some backup operations.</span></span>  
  
 <span data-ttu-id="1d9f7-108">可用性组在可用性副本级别进行故障转移。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-108">An availability group fails over at the level of an availability replica.</span></span> <span data-ttu-id="1d9f7-109">故障转移不是由诸如因数据文件丢失而使数据库成为可疑数据库、删除数据库或事务日志损坏等此类数据库问题导致的。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-109">Failovers are not caused by database issues such as a database becoming suspect due to a loss of a data file, deletion of a database, or corruption of a transaction log.</span></span>  
  
  
##  <a name="benefits"></a><a name="Benefits"></a> <span data-ttu-id="1d9f7-110">优势</span><span class="sxs-lookup"><span data-stu-id="1d9f7-110">Benefits</span></span>  
 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] <span data-ttu-id="1d9f7-111">提供了一组丰富的选项来提高数据库的可用性并改进资源使用情况。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-111">provides a rich set of options that improve database availability and that enable improved resource use.</span></span> <span data-ttu-id="1d9f7-112">主要组件如下：</span><span class="sxs-lookup"><span data-stu-id="1d9f7-112">The key components are as follows:</span></span>  
  
-   <span data-ttu-id="1d9f7-113">支持最多九个可用性副本。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-113">Supports up to nine availability replicas.</span></span> <span data-ttu-id="1d9f7-114">“可用性副本” \*\* 是可用性组的实例化，此可用性组由特定的 SQL Server 实例承载，该实例维护属于此可用性组的每个可用性数据库的本地副本。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-114">An *availability replica* is an instantiation of an availability group that is hosted by a specific instance of SQL Server and maintains a local copy of each availability database that belongs to the availability group.</span></span> <span data-ttu-id="1d9f7-115">每个可用性组都支持一个主副本和最多八个辅助副本。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-115">Each availability group supports one primary replica and up to eight secondary replicas.</span></span> <span data-ttu-id="1d9f7-116">有关详细信息，请参阅： [AlwaysOn 可用性组概述 (SQL Server)](overview-of-always-on-availability-groups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-116">For more information, see [Overview of Always On Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md).</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="1d9f7-117">每个可用性副本都必须驻留在单个 Windows Server 故障转移群集 (WSFC) 群集的不同节点中。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-117">Each availability replica must reside on a different node of a single Windows Server Failover Clustering (WSFC) cluster.</span></span> <span data-ttu-id="1d9f7-118">有关可用性组的先决条件、限制和建议的详细信息，请参阅[Always On 可用性组的先决条件、限制和建议;SQL Server;](prereqs-restrictions-recommendations-always-on-availability.md)。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-118">For more information about prerequisites, restrictions, and recommendations for availability groups, see [Prerequisites, Restrictions, and Recommendations for Always On Availability Groups;SQL Server;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span>  
  
-   <span data-ttu-id="1d9f7-119">支持替代可用性模式，如下所示：</span><span class="sxs-lookup"><span data-stu-id="1d9f7-119">Supports alternative availability modes, as follows:</span></span>  
  
    -   <span data-ttu-id="1d9f7-120">*异步提交模式*。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-120">*Asynchronous-commit mode*.</span></span> <span data-ttu-id="1d9f7-121">此可用性模式是一种灾难恢复解决方案，适合于可用性副本的分布距离较远的情况。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-121">This availability mode is a disaster-recovery solution that works well when the availability replicas are distributed over considerable distances.</span></span>  
  
    -   <span data-ttu-id="1d9f7-122">*同步提交模式*。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-122">*Synchronous-commit mode*.</span></span> <span data-ttu-id="1d9f7-123">此可用性模式相对于性能而言更强调高可用性和数据保护，为此付出的代价是事务延迟时间增加。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-123">This availability mode emphasizes high availability and data protection over performance, at the cost of increased transaction latency.</span></span> <span data-ttu-id="1d9f7-124">一个给定的可用性组可支持最多三个同步提交可用性副本（包括当前主副本）。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-124">A given availability group can support up to three synchronous-commit availability replicas, including the current primary replica.</span></span>  
  
     <span data-ttu-id="1d9f7-125">有关详细信息，请参阅[可用性模式;Always On 可用性组;](availability-modes-always-on-availability-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-125">For more information, see [Availability Modes;Always On Availability Groups;](availability-modes-always-on-availability-groups.md).</span></span>  
  
-   <span data-ttu-id="1d9f7-126">支持几种形式的可用性组故障转移：自动故障转移、计划的手动故障转移（通常简称为“手动故障转移”）和强制的手动故障转移（通常简称为“强制故障转移”）。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-126">Supports several forms of availability-group failover:  automatic failover, planned manual failover (generally referred as simply "manual failover"), and forced manual failover (generally referred as simply "forced failover").</span></span> <span data-ttu-id="1d9f7-127">有关详细信息，请参阅[故障转移和故障转移模式;Always On 可用性组;](failover-and-failover-modes-always-on-availability-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-127">For more information, see [Failover and Failover Modes;Always On Availability Groups;](failover-and-failover-modes-always-on-availability-groups.md).</span></span>  
  
-   <span data-ttu-id="1d9f7-128">使您能够将给定的可用性副本配置为支持以下一种或两种活动辅助功能：</span><span class="sxs-lookup"><span data-stu-id="1d9f7-128">Enables you to configure a given availability replica to support either or both of the following active-secondary capabilities:</span></span>  
  
    -   <span data-ttu-id="1d9f7-129">利用只读连接访问，与副本的只读连接可以在此副本作为辅助副本运行时访问和读取其数据库。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-129">Read-only connection access which enables read-only connections to the replica to access and read its databases when it is running as a secondary replica.</span></span> <span data-ttu-id="1d9f7-130">有关详细信息，请参阅[活动辅助副本：可读辅助副本;Always On 可用性组](https://msdn.microsoft.com/library/ff878253.aspx)) 。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-130">For more information, see [Active Secondaries: Readable Secondary Replicas;Always On Availability Groups](https://msdn.microsoft.com/library/ff878253.aspx)).</span></span>  
  
    -   <span data-ttu-id="1d9f7-131">当副本作为辅助副本运行时，对副本的数据库执行备份操作。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-131">Performing backup operations on its databases when it is running as a secondary replica.</span></span> <span data-ttu-id="1d9f7-132">有关详细信息，请参阅[活动辅助副本：辅助副本上的备份](https://msdn.microsoft.com/library/ff878253.aspx)) 。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-132">For more information, see [Active Secondaries: Backup on Secondary Replicas](https://msdn.microsoft.com/library/ff878253.aspx)).</span></span>  
  
     <span data-ttu-id="1d9f7-133">通过使用活动辅助功能，可更好地利用辅助硬件资源，从而提高 IT 效率并降低成本。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-133">Using active secondary capabilities improves your IT efficiency and reduce cost through better resource utilization of secondary hardware.</span></span> <span data-ttu-id="1d9f7-134">此外，通过将读意向应用程序和备份作业转移到辅助副本，有助于提高针对主副本的性能。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-134">In addition, offloading read-intent applications and backup jobs to secondary replicas helps to improve performance on the primary replica.</span></span>  
  
-   <span data-ttu-id="1d9f7-135">支持每个可用性组的可用性组侦听器。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-135">Supports an availability group listener for each availability group.</span></span> <span data-ttu-id="1d9f7-136">“可用性组侦听器” \*\* 是一个服务器名称，客户端可连接到此服务器以访问 AlwaysOn 可用性组的主副本或辅助副本中的数据库。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-136">An *availability group listener* is a server name to which clients can connect in order to access a database in a primary or secondary replica of an AlwaysOn availability group.</span></span> <span data-ttu-id="1d9f7-137">可用性组侦听器将传入连接定向到主副本或只读辅助副本。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-137">Availability group listeners direct incoming connections to the primary replica or to a read-only secondary replica.</span></span> <span data-ttu-id="1d9f7-138">侦听器在可用性组故障转移后提供快速应用程序故障转移。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-138">The listener provides fast application failover after an availability group fails over.</span></span> <span data-ttu-id="1d9f7-139">有关详细信息，请参阅[可用性组侦听器、客户端连接和应用程序故障转移;SQL Server;](../../listeners-client-connectivity-application-failover.md)。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-139">For more information, see [Availability Group Listeners, Client Connectivity, and Application Failover;SQL Server;](../../listeners-client-connectivity-application-failover.md).</span></span>  
  
-   <span data-ttu-id="1d9f7-140">支持灵活的故障转移策略以便更好地控制可用性组故障转移。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-140">Supports a flexible failover policy for greater control over availability-group failover.</span></span> <span data-ttu-id="1d9f7-141">有关详细信息，请参阅[故障转移和故障转移模式;Always On 可用性组;](failover-and-failover-modes-always-on-availability-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-141">For more information, see [Failover and Failover Modes; Always On Availability Groups;](failover-and-failover-modes-always-on-availability-groups.md).</span></span>  
  
-   <span data-ttu-id="1d9f7-142">支持用于避免页损坏的自动页修复。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-142">Supports automatic page repair for protection against page corruption.</span></span> <span data-ttu-id="1d9f7-143">有关详细信息，请参阅[可用性组和数据库镜像的自动页修复 &#40;;](../../../sql-server/failover-clusters/automatic-page-repair-availability-groups-database-mirroring.md)。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-143">For more information, see [Automatic Page Repair &#40;For Availability Groups and Database Mirroring;](../../../sql-server/failover-clusters/automatic-page-repair-availability-groups-database-mirroring.md).</span></span>  
  
-   <span data-ttu-id="1d9f7-144">支持加密和压缩，这提供了安全且高性能的传输方式。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-144">Supports encryption and compression, which provide a secure, high performing transport.</span></span>  
  
-   <span data-ttu-id="1d9f7-145">提供了一组集成的工具来简化部署和管理可用性组，这些工具包括：</span><span class="sxs-lookup"><span data-stu-id="1d9f7-145">Provides an integrated set of tools to simplify deployment and management of availability groups, including:</span></span>  
  
    -   [!INCLUDE[tsql](../../../includes/tsql-md.md)] <span data-ttu-id="1d9f7-146">DDL 语句。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-146">DDL statements for creating and managing availability groups.</span></span> <span data-ttu-id="1d9f7-147">有关详细信息，请参阅[Always On 可用性组的 Transact-sql 语句概述;SQL Server;](transact-sql-statements-for-always-on-availability-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-147">For more information, see [Overview of Transact-SQL Statements for Always On Availability Group;SQL Server;](transact-sql-statements-for-always-on-availability-groups.md).</span></span>  
  
    -   [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="1d9f7-148">工具，如下所示：</span><span class="sxs-lookup"><span data-stu-id="1d9f7-148">tools, as follows:</span></span>  
  
        -   <span data-ttu-id="1d9f7-149">[!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] 创建和配置可用性组。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-149">The [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] creates and configures an availability group.</span></span> <span data-ttu-id="1d9f7-150">在某些环境中，此向导还可以自动准备辅助数据库并且为每个数据库启动数据同步。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-150">In some environments, this wizard can also automatically prepare the secondary databases and start data synchronization for each of them.</span></span> <span data-ttu-id="1d9f7-151">有关详细信息，请参阅[使用 "新建可用性组" 对话框。SQL Server Management Studio;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-151">For more information, see [Use the New Availability Group Dialog Box;SQL Server Management Studio;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md).</span></span>  
  
        -   <span data-ttu-id="1d9f7-152">[!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] 向现有可用性组添加一个或多个主数据库。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-152">The [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] adds one or more primary databases to an existing availability group.</span></span> <span data-ttu-id="1d9f7-153">在某些环境中，此向导还可以自动准备辅助数据库并且为每个数据库启动数据同步。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-153">In some environments, this wizard can also automatically prepare the secondary databases and start data synchronization for each of them.</span></span> <span data-ttu-id="1d9f7-154">有关详细信息，请参阅 [使用“将数据库添加到可用性组向导”(SQL Server)](availability-group-add-database-to-group-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-154">For more information, see [Use the Add Database to Availability Group Wizard (SQL Server)](availability-group-add-database-to-group-wizard.md).</span></span>  
  
        -   <span data-ttu-id="1d9f7-155">[!INCLUDE[ssAoAddRepWiz](../../../includes/ssaoaddrepwiz-md.md)] 向现有可用性组添加一个或多个辅助副本。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-155">The [!INCLUDE[ssAoAddRepWiz](../../../includes/ssaoaddrepwiz-md.md)] adds one or more secondary replicas to an existing availability group.</span></span> <span data-ttu-id="1d9f7-156">在某些环境中，此向导还可以自动准备辅助数据库并且为每个数据库启动数据同步。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-156">In some environments, this wizard can also automatically prepare the secondary databases and start data synchronization for each of them.</span></span> <span data-ttu-id="1d9f7-157">有关详细信息，请参阅[使用 "将副本添加到可用性组向导";SQL Server Management Studio;](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-157">For more information, see [Use the Add Replica to Availability Group Wizard;SQL Server Management Studio;](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md).</span></span>  
  
        -   <span data-ttu-id="1d9f7-158">[!INCLUDE[ssAoFoAgWiz](../../../includes/ssaofoagwiz-md.md)] 启动对可用性组的手动故障转移。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-158">The [!INCLUDE[ssAoFoAgWiz](../../../includes/ssaofoagwiz-md.md)] initiates a manual failover on an availability group.</span></span> <span data-ttu-id="1d9f7-159">根据您指定为故障转移目标的辅助副本的配置和状态，该向导可以指定计划的手动故障转移或强制手动故障转移。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-159">Depending on the configuration and state of the secondary replica that you specify as the failover target, the wizard can perform either a planned or forced manual failover.</span></span> <span data-ttu-id="1d9f7-160">有关详细信息，请参阅[使用故障转移可用性组向导;SQL Server Management Studio;](use-the-fail-over-availability-group-wizard-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-160">For more information, see [Use the Fail Over Availability Group Wizard;SQL Server Management Studio;](use-the-fail-over-availability-group-wizard-sql-server-management-studio.md).</span></span>  
  
    -   <span data-ttu-id="1d9f7-161">[!INCLUDE[ssAoDash](../../../includes/ssaodash-md.md)] 监视 AlwaysOn 可用性组、可用性副本和可用性数据库，并且评估 AlwaysOn 策略的结果。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-161">The [!INCLUDE[ssAoDash](../../../includes/ssaodash-md.md)] monitors AlwaysOn availability groups, availability replicas, and availability databases and evaluates results for AlwaysOn policies.</span></span> <span data-ttu-id="1d9f7-162">有关详细信息，请参阅[使用 AlwaysOn 仪表板;SQL Server Management Studio;](use-the-always-on-dashboard-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-162">For more information, see [Use the AlwaysOn Dashboard;SQL Server Management Studio;](use-the-always-on-dashboard-sql-server-management-studio.md).</span></span>  
  
    -   <span data-ttu-id="1d9f7-163">“对象资源管理器详细信息”窗格显示有关现有可用性组的基本信息。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-163">The Object Explorer Details pane displays basic information about existing availability groups.</span></span> <span data-ttu-id="1d9f7-164">有关详细信息，请参阅[使用对象资源管理器详细信息监视可用性组;SQL Server Management Studio;](use-object-explorer-details-to-monitor-availability-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-164">For more information, see [Use the Object Explorer Details to Monitor Availability Group;SQL Server Management Studio;](use-object-explorer-details-to-monitor-availability-groups.md).</span></span>  
  
    -   <span data-ttu-id="1d9f7-165">PowerShell cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-165">PowerShell cmdlets.</span></span> <span data-ttu-id="1d9f7-166">有关详细信息，请参阅[Always On 可用性组的 PowerShell Cmdlet 概述;SQL 服务](overview-of-powershell-cmdlets-for-always-on-availability-groups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-166">For more information, see [Overview of PowerShell Cmdlets for Always On Availability Groups;SQL Serve;](overview-of-powershell-cmdlets-for-always-on-availability-groups-sql-server.md).</span></span>  
  
##  <a name="terms-and-definitions"></a><a name="TermsAndDefinitions"></a> <span data-ttu-id="1d9f7-167">术语和定义</span><span class="sxs-lookup"><span data-stu-id="1d9f7-167">Terms and Definitions</span></span>  
 <span data-ttu-id="1d9f7-168">可用性组 (availability group)</span><span class="sxs-lookup"><span data-stu-id="1d9f7-168">availability group</span></span>  
 <span data-ttu-id="1d9f7-169">一个容器，用于一组共同实现故障转移的数据库（“可用性数据库”\*\*）。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-169">A container for a set of databases, *availability databases*, that fail over together.</span></span>  
  
 <span data-ttu-id="1d9f7-170">可用性数据库 (availability database)</span><span class="sxs-lookup"><span data-stu-id="1d9f7-170">availability database</span></span>  
 <span data-ttu-id="1d9f7-171">属于可用性组的数据库。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-171">A database that belongs to an availability group.</span></span> <span data-ttu-id="1d9f7-172">对于每个可用性数据库，可用性组将保留一个读写副本（“主数据库”**）和一个到八个只读副本（“辅助数据库”**）。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-172">For each availability database, the availability group maintains a single read-write copy (the *primary database*) and one to eight read-only copies (*secondary databases*).</span></span>  
  
 <span data-ttu-id="1d9f7-173">主数据库 (primary database)</span><span class="sxs-lookup"><span data-stu-id="1d9f7-173">primary database</span></span>  
 <span data-ttu-id="1d9f7-174">可用性数据库的读写副本。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-174">The read-write copy of an availability database.</span></span>  
  
 <span data-ttu-id="1d9f7-175">辅助数据库 (secondary database)</span><span class="sxs-lookup"><span data-stu-id="1d9f7-175">secondary database</span></span>  
 <span data-ttu-id="1d9f7-176">可用性数据库的只读副本。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-176">A read-only copy of an availability database.</span></span>  
  
 <span data-ttu-id="1d9f7-177">可用性副本</span><span class="sxs-lookup"><span data-stu-id="1d9f7-177">availability replica</span></span>  
 <span data-ttu-id="1d9f7-178">可用性组的实例化，该可用性组由特定的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例承载，并维护属于该可用性组的每个可用性数据库的本地副本。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-178">An instantiation of an availability group that is hosted by a specific instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] and maintains a local copy of each availability database that belongs to the availability group.</span></span> <span data-ttu-id="1d9f7-179">存在两种类型的可用性副本：一个 *主副本* 和一至八个 *辅助副本*。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-179">Two types of availability replicas exist: a single *primary replica* and one to eight *secondary replicas*.</span></span>  
  
 <span data-ttu-id="1d9f7-180">主副本</span><span class="sxs-lookup"><span data-stu-id="1d9f7-180">primary replica</span></span>  
 <span data-ttu-id="1d9f7-181">使主数据库可用于来自客户端的读写连接并用于将每个主数据库的事务日志记录发送到每个辅助副本的可用性副本。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-181">The availability replica that makes the primary databases available for read-write connections from clients and, also, sends transaction log records for each primary database to every secondary replica.</span></span>  
  
 <span data-ttu-id="1d9f7-182">辅助副本 (secondary replica)</span><span class="sxs-lookup"><span data-stu-id="1d9f7-182">secondary replica</span></span>  
 <span data-ttu-id="1d9f7-183">维护各可用性数据库的辅助副本的可用性副本，充当可用性组的潜在故障转移目标。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-183">An availability replica that maintains a secondary copy of each availability database, and serves as a potential failover targets for the availability group.</span></span> <span data-ttu-id="1d9f7-184">或者，辅助副本可以支持对辅助数据库进行只读访问，并支持对辅助数据库创建备份。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-184">Optionally, a secondary replica can support read-only access to secondary databases can support creating backups on secondary databases.</span></span>  
  
 <span data-ttu-id="1d9f7-185">可用性组侦听器</span><span class="sxs-lookup"><span data-stu-id="1d9f7-185">availability group listener</span></span>  
 <span data-ttu-id="1d9f7-186">一个服务器名称，客户端可连接到此服务器以访问 AlwaysOn 可用性组的主要副本或次要副本中的数据库。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-186">A server name to which clients can connect in order to access a database in a primary or secondary replica of an Always On availability group.</span></span> <span data-ttu-id="1d9f7-187">可用性组侦听器将传入连接定向到主副本或只读辅助副本。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-187">Availability group listeners direct incoming connections to the primary replica or to a read-only secondary replica.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1d9f7-188">有关详细信息，请参阅[AlwaysOn 可用性组概述;SQL 服务](overview-of-always-on-availability-groups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-188">For more information, see [Overview of AlwaysOn Availability Groups;SQL Serve;](overview-of-always-on-availability-groups-sql-server.md).</span></span>  
  
##  <a name="interoperability-and-coexistence-with-other-database-engine-features"></a><a name="Interoperability"></a> <span data-ttu-id="1d9f7-189">与其他数据库引擎功能的互操作性和共存</span><span class="sxs-lookup"><span data-stu-id="1d9f7-189">Interoperability and Coexistence with Other Database Engine Features</span></span>  
 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] <span data-ttu-id="1d9f7-190">可与以下 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]功能和组件一起使用：</span><span class="sxs-lookup"><span data-stu-id="1d9f7-190">can be used with the following features or components of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]:</span></span>  
  
-   [<span data-ttu-id="1d9f7-191">关于变更数据捕获;SQL Server;</span><span class="sxs-lookup"><span data-stu-id="1d9f7-191">About Change Data Capture;SQL Server;</span></span>](../../../relational-databases/track-changes/about-change-data-capture-sql-server.md)  
  
-   [<span data-ttu-id="1d9f7-192">关于更改跟踪;SQL 服务;</span><span class="sxs-lookup"><span data-stu-id="1d9f7-192">About Change Tracking;SQL Serve;</span></span>](../../../relational-databases/track-changes/about-change-tracking-sql-server.md)  
  
-   [<span data-ttu-id="1d9f7-193">包含的数据库</span><span class="sxs-lookup"><span data-stu-id="1d9f7-193">Contained databases</span></span>](../../../relational-databases/databases/contained-databases.md)  
  
-   [<span data-ttu-id="1d9f7-194">数据库加密</span><span class="sxs-lookup"><span data-stu-id="1d9f7-194">Database encryption</span></span>](../../../relational-databases/security/encryption/transparent-data-encryption.md)  
  
-   [<span data-ttu-id="1d9f7-195">数据库快照</span><span class="sxs-lookup"><span data-stu-id="1d9f7-195">Database snapshots</span></span>](database-snapshots-with-always-on-availability-groups-sql-server.md)  
  
-   [<span data-ttu-id="1d9f7-196">FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="1d9f7-196">FILESTREAM</span></span>](../../../relational-databases/blob/filestream-sql-server.md)  
  
-   [<span data-ttu-id="1d9f7-197">FileTable</span><span class="sxs-lookup"><span data-stu-id="1d9f7-197">FileTable</span></span>](../../../relational-databases/blob/filetables-sql-server.md)  
  
-   [<span data-ttu-id="1d9f7-198">日志传送</span><span class="sxs-lookup"><span data-stu-id="1d9f7-198">Log shipping</span></span>](../../log-shipping/about-log-shipping-sql-server.md)  
  
-   [<span data-ttu-id="1d9f7-199">远程 Blob 存储区 (RBS)</span><span class="sxs-lookup"><span data-stu-id="1d9f7-199">Remote Blob Store (RBS)</span></span>](../../../relational-databases/blob/remote-blob-store-rbs-sql-server.md)  
  
-   [<span data-ttu-id="1d9f7-200">复制</span><span class="sxs-lookup"><span data-stu-id="1d9f7-200">Replication</span></span>](../../install-windows/install-sql-server-replication.md)  
  
-   [<span data-ttu-id="1d9f7-201">Service Broker</span><span class="sxs-lookup"><span data-stu-id="1d9f7-201">Service Broker</span></span>](../../configure-windows/sql-server-service-broker.md)  
  
-   [<span data-ttu-id="1d9f7-202">SQL Server 代理</span><span class="sxs-lookup"><span data-stu-id="1d9f7-202">SQL Server Agent</span></span>](../../../ssms/agent/sql-server-agent.md)  
  
-   [<span data-ttu-id="1d9f7-203">Reporting Services</span><span class="sxs-lookup"><span data-stu-id="1d9f7-203">Reporting Services</span></span>](reporting-services-with-always-on-availability-groups-sql-server.md)  
  
> [!WARNING]  
>  <span data-ttu-id="1d9f7-204">有关使用的其他功能的限制和限制的信息 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] ，请参阅[Always On 可用性组：互操作性;SQL Server;](always-on-availability-groups-interoperability-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="1d9f7-204">For information about restrictions and limitations for using other features with [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], see [Always On Availability Groups: Interoperability;SQL Server;](always-on-availability-groups-interoperability-sql-server.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="1d9f7-205">相关任务</span><span class="sxs-lookup"><span data-stu-id="1d9f7-205">Related Tasks</span></span>  
  
-   [<span data-ttu-id="1d9f7-206">Always On 可用性组的入门;SQL Server;</span><span class="sxs-lookup"><span data-stu-id="1d9f7-206">Getting Started with Always On Availability Groups;SQL Server;</span></span>](getting-started-with-always-on-availability-groups-sql-server.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="1d9f7-207">相关内容</span><span class="sxs-lookup"><span data-stu-id="1d9f7-207">Related Content</span></span>  
  
-   <span data-ttu-id="1d9f7-208">**博客：**</span><span class="sxs-lookup"><span data-stu-id="1d9f7-208">**Blogs:**</span></span>  
  
     [<span data-ttu-id="1d9f7-209">SQL Server Always On 团队博客：官方 SQL Server AlwaysOn 团队博客</span><span class="sxs-lookup"><span data-stu-id="1d9f7-209">SQL Server Always On Team Blogs: The official SQL Server AlwaysOn Team Blog</span></span>](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [<span data-ttu-id="1d9f7-210">CSS SQL Server 工程师博客</span><span class="sxs-lookup"><span data-stu-id="1d9f7-210">CSS SQL Server Engineers Blogs</span></span>](https://blogs.msdn.com/b/psssql/)  
  
-   <span data-ttu-id="1d9f7-211">**视频：**</span><span class="sxs-lookup"><span data-stu-id="1d9f7-211">**Videos:**</span></span>  
  
     <span data-ttu-id="1d9f7-212">[Microsoft SQL Server Code-Named "Denali" Always On Series,Part 1:Introducing the Next Generation High Availability Solution](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI302)（Microsoft SQL Server Code-Named "Denali" Always On 系列，第 1 部分：介绍下一代高可用性解决方案）</span><span class="sxs-lookup"><span data-stu-id="1d9f7-212">[Microsoft SQL Server Code-Named "Denali" Always On Series,Part 1: Introducing the Next Generation High Availability Solution](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI302)</span></span>  
  
     [<span data-ttu-id="1d9f7-213">Microsoft SQL Server 名为 "Denali" Always On 系列，第2部分：使用 AlwaysOn 生成关键任务高可用性解决方案</span><span class="sxs-lookup"><span data-stu-id="1d9f7-213">Microsoft SQL Server Code-Named "Denali" Always On Series,Part 2: Building a Mission-Critical High Availability Solution Using AlwaysOn</span></span>](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI404)  
  
-   <span data-ttu-id="1d9f7-214">**白皮书：**</span><span class="sxs-lookup"><span data-stu-id="1d9f7-214">**Whitepapers:**</span></span>  
  
     [<span data-ttu-id="1d9f7-215">用于高可用性和灾难恢复的 Microsoft SQL Server AlwaysOn 解决方案指南</span><span class="sxs-lookup"><span data-stu-id="1d9f7-215">Microsoft SQL Server Always On Solutions Guide for High Availability and Disaster Recovery</span></span>](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
  
  
## <a name="see-also"></a><span data-ttu-id="1d9f7-216">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1d9f7-216">See Also</span></span>  
 <span data-ttu-id="1d9f7-217">[Always On 可用性组概述;SQL Server;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1d9f7-217">[Overview of Always On Availability Groups;SQL Server;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="1d9f7-218">[AlwaysOn 可用性组 &#40;SQL Server 的先决条件、限制和建议&#41;](prereqs-restrictions-recommendations-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="1d9f7-218">[Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md) </span></span>  
 <span data-ttu-id="1d9f7-219">[为 Always On 可用性组配置服务器实例;SQL Server;](always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1d9f7-219">[Configuration of a Server Instance for Always On Availability Groups;SQL Server;](always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="1d9f7-220">[创建和配置可用性组;SQL Server;](creation-and-configuration-of-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1d9f7-220">[Creation and Configuration of Availability Groups;SQL Server;](creation-and-configuration-of-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="1d9f7-221">[管理可用性组;SQL Server;](administration-of-an-availability-group-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1d9f7-221">[Administration of an Availability Group;SQL Server;](administration-of-an-availability-group-sql-server.md) </span></span>  
 <span data-ttu-id="1d9f7-222">[监视可用性组 (SQL Server)](monitoring-of-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1d9f7-222">[Monitoring of Availability Groups &#40;SQL Server&#41;](monitoring-of-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="1d9f7-223">[Always On 可用性组的 Transact-sql 语句概述;SQL Server;](transact-sql-statements-for-always-on-availability-groups.md) </span><span class="sxs-lookup"><span data-stu-id="1d9f7-223">[Overview of Transact-SQL Statements for Always On Availability Groups;SQL Server;](transact-sql-statements-for-always-on-availability-groups.md) </span></span>  
 [<span data-ttu-id="1d9f7-224">AlwaysOn 可用性组的 PowerShell Cmdlet 概述;SQL Server;</span><span class="sxs-lookup"><span data-stu-id="1d9f7-224">Overview of PowerShell Cmdlets for AlwaysOn Availability Groups;SQL Server;</span></span>](overview-of-powershell-cmdlets-for-always-on-availability-groups-sql-server.md)  
  
