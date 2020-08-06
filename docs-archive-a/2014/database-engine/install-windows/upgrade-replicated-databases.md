---
title: 升级复制数据库 | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- merge replication database upgrades [SQL Server replication]
- replication [SQL Server], upgrading
- transactional replication, upgrading databases
- snapshot replication [SQL Server], upgrading databases
- upgrading replicated databases
ms.assetid: 9926a4f7-bcd8-4b9b-9dcf-5426a5857116
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 326a94820876b40128428aac58e47c650ce122b8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580339"
---
# <a name="upgrade-replicated-databases"></a><span data-ttu-id="a24c3-102">升级复制数据库</span><span class="sxs-lookup"><span data-stu-id="a24c3-102">Upgrade Replicated Databases</span></span>
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="a24c3-103">支持从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的早期版本升级复制数据库；在升级某一节点时，不需要停止其他节点的活动。</span><span class="sxs-lookup"><span data-stu-id="a24c3-103">supports upgrading replicated databases from previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]; it is not required to stop activity at other nodes while a node is being upgraded.</span></span> <span data-ttu-id="a24c3-104">请务必遵守有关拓扑中支持哪些版本的规则：</span><span class="sxs-lookup"><span data-stu-id="a24c3-104">Ensure that you adhere to the rules regarding which versions are supported in a topology:</span></span>  
  
-   <span data-ttu-id="a24c3-105">分发服务器的版本可以是高于或等于发布服务器版本的任何版本（在许多情况下，分发服务器与发布服务器是同一个实例）。</span><span class="sxs-lookup"><span data-stu-id="a24c3-105">A Distributor can be any version as long as it is greater than or equal to the Publisher version (in many cases the Distributor is the same instance as the Publisher).</span></span>  
  
-   <span data-ttu-id="a24c3-106">发布服务器的版本可以是低于或等于分发服务器版本的任何版本。</span><span class="sxs-lookup"><span data-stu-id="a24c3-106">A Publisher can be any version as long as it less than or equal to the Distributor version.</span></span>  
  
-   <span data-ttu-id="a24c3-107">订阅服务器版本取决于发布的类型：</span><span class="sxs-lookup"><span data-stu-id="a24c3-107">Subscriber version depends on the type of publication:</span></span>  
  
    -   <span data-ttu-id="a24c3-108">用于事务发布的订阅服务器版本可以是两个发布服务器版本中的任何一个版本。</span><span class="sxs-lookup"><span data-stu-id="a24c3-108">A Subscriber to a transactional publication can be any version within two versions of the Publisher version.</span></span> <span data-ttu-id="a24c3-109">例如，[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 发布服务器可以对应 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 订阅服务器，而 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 发布服务器可以对应 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="a24c3-109">For example: a [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Publisher running can have [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Subscribers; and a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Publisher can have [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Subscribers.</span></span>  
  
    -   <span data-ttu-id="a24c3-110">合并发布的订阅服务器版本可以是低于或等于发布服务器版本的任何版本。</span><span class="sxs-lookup"><span data-stu-id="a24c3-110">A Subscriber to a merge publication can be any version less than or equal to the Publisher version.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a24c3-111">在“安装帮助”文档和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机丛书中可以查看此主题。</span><span class="sxs-lookup"><span data-stu-id="a24c3-111">This topic is available in the Setup Help documentation and in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span> <span data-ttu-id="a24c3-112">对于“安装帮助”文档中显示为粗体文本的主题链接来说，所指向的主题仅在联机丛书中提供。</span><span class="sxs-lookup"><span data-stu-id="a24c3-112">Topic links that appear as bold text in the Setup Help documentation refer to topics that are only available in Books Online.</span></span>  
  
## <a name="run-the-log-reader-agent-for-transactional-replication-before-upgrade"></a><span data-ttu-id="a24c3-113">在升级前先运行用于事务复制的日志读取器代理</span><span class="sxs-lookup"><span data-stu-id="a24c3-113">Run the Log Reader Agent for Transactional Replication Before Upgrade</span></span>  
 <span data-ttu-id="a24c3-114">升级到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]之前，必须确保已发布表的所有已提交事务已由日志读取器代理进行了处理。</span><span class="sxs-lookup"><span data-stu-id="a24c3-114">Before you upgrade to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], you must make sure that all committed transactions from published tables have been processed by the Log Reader Agent.</span></span> <span data-ttu-id="a24c3-115">若要确保所有事务均得到处理，请针对包含事务发布的每个数据库执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="a24c3-115">To make sure that all transactions have been processed, perform the following steps for each database that contains transactional publications:</span></span>  
  
1.  <span data-ttu-id="a24c3-116">确保针对数据库运行了日志读取器代理。</span><span class="sxs-lookup"><span data-stu-id="a24c3-116">Make sure that the Log Reader Agent is running for the database.</span></span> <span data-ttu-id="a24c3-117">默认情况下，该代理会连续运行。</span><span class="sxs-lookup"><span data-stu-id="a24c3-117">By default, the agent runs continuously.</span></span>  
  
2.  <span data-ttu-id="a24c3-118">停止已发布表上的用户活动。</span><span class="sxs-lookup"><span data-stu-id="a24c3-118">Stop user activity on published tables.</span></span>  
  
3.  <span data-ttu-id="a24c3-119">日志读取器代理和分发代理支持事务读取和提交操作的批大小。</span><span class="sxs-lookup"><span data-stu-id="a24c3-119">Allow time for the Log Reader Agent to copy transactions to the distribution database, and then stop the agent.</span></span>  
  
4.  <span data-ttu-id="a24c3-120">执行 [sp_replcmds](/sql/relational-databases/system-stored-procedures/sp-replcmds-transact-sql) 以验证所有事务是否得到了处理。</span><span class="sxs-lookup"><span data-stu-id="a24c3-120">Execute [sp_replcmds](/sql/relational-databases/system-stored-procedures/sp-replcmds-transact-sql) to verify that all transactions have been processed.</span></span> <span data-ttu-id="a24c3-121">此过程的结果集应为空。</span><span class="sxs-lookup"><span data-stu-id="a24c3-121">The result set from this procedure should be empty.</span></span>  
  
5.  <span data-ttu-id="a24c3-122">执行 [sp_replflush](/sql/relational-databases/system-stored-procedures/sp-replflush-transact-sql) 以关闭与 sp_replcmds 的连接。</span><span class="sxs-lookup"><span data-stu-id="a24c3-122">Execute [sp_replflush](/sql/relational-databases/system-stored-procedures/sp-replflush-transact-sql) to close the connection from sp_replcmds.</span></span>  
  
6.  <span data-ttu-id="a24c3-123">将服务器升级到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a24c3-123">Perform the server upgrade to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
7.  <span data-ttu-id="a24c3-124">如果在升级后 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理和日志读取器代理没有自动启动，请重新启动它们。</span><span class="sxs-lookup"><span data-stu-id="a24c3-124">Restart [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent and the Log Reader Agent if they do not start automatically after the upgrade.</span></span>  
  
## <a name="run-agents-for-merge-replication-after-upgrade"></a><span data-ttu-id="a24c3-125">升级后运行用于合并复制的代理</span><span class="sxs-lookup"><span data-stu-id="a24c3-125">Run Agents for Merge Replication After Upgrade</span></span>  
 <span data-ttu-id="a24c3-126">升级后，请为每一个合并发布运行快照代理，并为每一个订阅运行合并代理，以更新复制元数据。</span><span class="sxs-lookup"><span data-stu-id="a24c3-126">After upgrade, run the Snapshot Agent for each merge publication and the Merge Agent for each subscription to update replication metadata.</span></span> <span data-ttu-id="a24c3-127">因为不必重新初始化订阅，所以不需要应用新快照。</span><span class="sxs-lookup"><span data-stu-id="a24c3-127">You do not have to apply the new snapshot, because it is not necessary to reinitialize subscriptions.</span></span> <span data-ttu-id="a24c3-128">升级后首次运行合并代理时，将更新订阅元数据。</span><span class="sxs-lookup"><span data-stu-id="a24c3-128">Subscription metadata is updated the first time the Merge Agent is run after upgrade.</span></span> <span data-ttu-id="a24c3-129">这表明发布服务器升级时订阅数据库可以保持在线状态和活动状态。</span><span class="sxs-lookup"><span data-stu-id="a24c3-129">This means that the subscription database can remain online and active during the Publisher upgrade.</span></span>  
  
 <span data-ttu-id="a24c3-130">合并复制将发布和订阅元数据存储在发布和订阅数据库中的若干系统表中。</span><span class="sxs-lookup"><span data-stu-id="a24c3-130">Merge replication stores publication and subscription metadata in a number of system tables in the publication and subscription databases.</span></span> <span data-ttu-id="a24c3-131">运行快照代理将更新发布元数据，而运行合并代理将更新订阅元数据。</span><span class="sxs-lookup"><span data-stu-id="a24c3-131">Running the Snapshot Agent updates publication metadata and running the Merge Agent updates subscription metadata.</span></span> <span data-ttu-id="a24c3-132">只需生成发布快照。</span><span class="sxs-lookup"><span data-stu-id="a24c3-132">It is only required to generate a publication snapshot.</span></span> <span data-ttu-id="a24c3-133">如果合并发布使用参数化筛选器，则每一个分区也都有快照。</span><span class="sxs-lookup"><span data-stu-id="a24c3-133">If a merge publication uses parameterized filters, each partition also has a snapshot.</span></span> <span data-ttu-id="a24c3-134">不必更新这些分区快照。</span><span class="sxs-lookup"><span data-stu-id="a24c3-134">It is not necessary to update these partitioned snapshots.</span></span>  
  
 <span data-ttu-id="a24c3-135">从 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、复制监视器或命令行运行代理。</span><span class="sxs-lookup"><span data-stu-id="a24c3-135">Run the agents from [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], Replication Monitor, or from the command line.</span></span> <span data-ttu-id="a24c3-136">有关运行快照代理的详细信息，请参阅下列主题：</span><span class="sxs-lookup"><span data-stu-id="a24c3-136">For more information about running the Snapshot Agent, see the following topics:</span></span>  
  
-   [<span data-ttu-id="a24c3-137">创建并应用初始快照</span><span class="sxs-lookup"><span data-stu-id="a24c3-137">Create and Apply the Initial Snapshot</span></span>](../../../2014/relational-databases/replication/create-and-apply-the-initial-snapshot.md)  
  
-   [<span data-ttu-id="a24c3-138">启动和停止复制代理 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="a24c3-138">Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;</span></span>](../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="a24c3-139">创建并应用初始快照</span><span class="sxs-lookup"><span data-stu-id="a24c3-139">Create and Apply the Initial Snapshot</span></span>](../../../2014/relational-databases/replication/create-and-apply-the-initial-snapshot.md)  
  
-   [<span data-ttu-id="a24c3-140">Replication Agent Executables Concepts</span><span class="sxs-lookup"><span data-stu-id="a24c3-140">Replication Agent Executables Concepts</span></span>](../../../2014/relational-databases/replication/concepts/replication-agent-executables-concepts.md)  
  
 <span data-ttu-id="a24c3-141">有关运行合并代理的详细信息，请参阅下列主题：</span><span class="sxs-lookup"><span data-stu-id="a24c3-141">For more information about running the Merge Agent, see the following topics:</span></span>  
  
-   [<span data-ttu-id="a24c3-142">同步请求订阅</span><span class="sxs-lookup"><span data-stu-id="a24c3-142">Synchronize a Pull Subscription</span></span>](../../../2014/relational-databases/replication/synchronize-a-pull-subscription.md)  
  
-   [<span data-ttu-id="a24c3-143">同步推送订阅</span><span class="sxs-lookup"><span data-stu-id="a24c3-143">Synchronize a Push Subscription</span></span>](../../../2014/relational-databases/replication/synchronize-a-push-subscription.md)  
  
 <span data-ttu-id="a24c3-144">在使用合并复制的拓扑中升级 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之后，如果要使用新功能，请更改所有发布的发布兼容级别。</span><span class="sxs-lookup"><span data-stu-id="a24c3-144">After upgrading [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in a topology that uses merge replication, change the publication compatibility level of any publications if you want to use new features.</span></span>  
  
## <a name="upgrading-to-standard-workgroup-or-express-editions"></a><span data-ttu-id="a24c3-145">升级至 Standard Edition、Workgroup Edition 或 Express Edition</span><span class="sxs-lookup"><span data-stu-id="a24c3-145">Upgrading to Standard, Workgroup, or Express Editions</span></span>  
 <span data-ttu-id="a24c3-146">在从 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 的某一版本升级到另一版本之前，请验证要升级到的版本是否支持当前使用的功能。</span><span class="sxs-lookup"><span data-stu-id="a24c3-146">Before upgrading from one edition of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] to another, verify that the functionality you are currently using is supported in the edition to which you are upgrading.</span></span> <span data-ttu-id="a24c3-147">有关详细信息，请参阅 SQL Server 2014 的各个[版本支持的功能](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)中有关复制的部分。</span><span class="sxs-lookup"><span data-stu-id="a24c3-147">For more information, see the section on Replication in [Features Supported by the Editions of SQL Server 2014](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
## <a name="web-synchronization-for-merge-replication"></a><span data-ttu-id="a24c3-148">合并复制的 Web 同步</span><span class="sxs-lookup"><span data-stu-id="a24c3-148">Web Synchronization for Merge Replication</span></span>  
 <span data-ttu-id="a24c3-149">合并复制的 Web 同步选项要求将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 复制侦听器 (replisapi.dll) 复制到用于同步的 Internet Information Services (IIS) 服务器上的虚拟目录中。</span><span class="sxs-lookup"><span data-stu-id="a24c3-149">The Web synchronization option for merge replication requires that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Replication Listener (replisapi.dll) be copied to the virtual directory on the Internet Information Services (IIS) server used for synchronization.</span></span> <span data-ttu-id="a24c3-150">配置 Web 同步时，该文件被配置 Web 同步向导复制到虚拟目录中。</span><span class="sxs-lookup"><span data-stu-id="a24c3-150">When you configure Web synchronization, the file is copied to the virtual directory by the Configure Web Synchronization Wizard.</span></span> <span data-ttu-id="a24c3-151">若要升级安装在 IIS 服务器上的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 组件，必须将 replisapi.dll 从 COM 目录手动复制到 IIS 服务器上的虚拟目录。</span><span class="sxs-lookup"><span data-stu-id="a24c3-151">If you upgrade the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components installed on the IIS server, you must manually copy replisapi.dll from the COM directory to the virtual directory on the IIS server.</span></span> <span data-ttu-id="a24c3-152">有关配置 Web 同步的详细信息，请参阅 [配置 Web 同步](../../../2014/relational-databases/replication/configure-web-synchronization.md)。</span><span class="sxs-lookup"><span data-stu-id="a24c3-152">For more information about configuring Web synchronization, see [Configure Web Synchronization](../../../2014/relational-databases/replication/configure-web-synchronization.md).</span></span>  
  
## <a name="restoring-a-replicated-database-from-an-earlier-version"></a><span data-ttu-id="a24c3-153">从早期版本还原复制的数据库</span><span class="sxs-lookup"><span data-stu-id="a24c3-153">Restoring a Replicated Database from an Earlier Version</span></span>  
 <span data-ttu-id="a24c3-154">在从早期版本还原复制数据库的备份时，若要确保保留复制设置：请还原到与创建备份的服务器和数据库同名的服务器和数据库。</span><span class="sxs-lookup"><span data-stu-id="a24c3-154">To ensure replication settings are retained when restoring a backup of a replicated database from a previous version: restore to a server and database with the same names as the server and database at which the backup was taken.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a24c3-155">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a24c3-155">See Also</span></span>  
 <span data-ttu-id="a24c3-156">[复制管理常见问题解答](../../relational-databases/replication/administration/frequently-asked-questions-for-replication-administrators.md) </span><span class="sxs-lookup"><span data-stu-id="a24c3-156">[Replication Administration FAQ](../../relational-databases/replication/administration/frequently-asked-questions-for-replication-administrators.md) </span></span>  
 <span data-ttu-id="a24c3-157">[副本后向兼容性](../../../2014/relational-databases/replication/replication-backward-compatibility.md) </span><span class="sxs-lookup"><span data-stu-id="a24c3-157">[Replication Backward Compatibility](../../../2014/relational-databases/replication/replication-backward-compatibility.md) </span></span>  
 <span data-ttu-id="a24c3-158">[支持的版本升级](../../database-engine/install-windows/supported-version-and-edition-upgrades.md) </span><span class="sxs-lookup"><span data-stu-id="a24c3-158">[Supported Version and Edition Upgrades](../../database-engine/install-windows/supported-version-and-edition-upgrades.md) </span></span>  
 [<span data-ttu-id="a24c3-159">升级到 SQL Server 2014</span><span class="sxs-lookup"><span data-stu-id="a24c3-159">Upgrade to SQL Server 2014</span></span>](upgrade-sql-server.md)  
  
  
