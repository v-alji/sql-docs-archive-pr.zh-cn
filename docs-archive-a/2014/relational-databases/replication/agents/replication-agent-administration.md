---
title: 复制代理管理 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Snapshot Agent, administering
- Log Reader Agent, administering
- Queue Reader Agent, administering
- shared agents [SQL Server replication]
- Merge Agent, administering
- Distribution Agent, administering
- agents [SQL Server replication], administering
- replication cleanup jobs [SQL Server]
- administering replication, agents
- replication [SQL Server], administering
- independent agents [SQL Server replication]
ms.assetid: f27186b8-b1b2-4da0-8b2b-91f632c2ab7e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 99cf9be6b31310e5ae0ebac3c096851ac4f63452
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580153"
---
# <a name="replication-agent-administration"></a><span data-ttu-id="89f3b-102">复制代理管理</span><span class="sxs-lookup"><span data-stu-id="89f3b-102">Replication Agent Administration</span></span>
  <span data-ttu-id="89f3b-103">复制代理执行许多与复制有关的任务，其中包括创建架构和数据副本、检测发布服务器或订阅服务器上的更新以及在服务器之间传播更改。</span><span class="sxs-lookup"><span data-stu-id="89f3b-103">Replication agents carry out many of the tasks associated with replication, including creating copies of schema and data, detecting updates at the Publisher or Subscriber, and propagating changes between servers.</span></span> <span data-ttu-id="89f3b-104">默认情况下，复制代理在 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 代理作业步骤下运行。</span><span class="sxs-lookup"><span data-stu-id="89f3b-104">By default, replication agents run under [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent job steps.</span></span> <span data-ttu-id="89f3b-105">由于这些代理完全是可执行文件，因此可以从命令行和批处理脚本直接调用它们。</span><span class="sxs-lookup"><span data-stu-id="89f3b-105">The agents are simply executables, so they can also be called directly from the command line and from batch scripts.</span></span> <span data-ttu-id="89f3b-106">每个复制代理支持一组运行时参数，用于控制代理的运行方式；这些参数在代理配置文件或命令行中指定。</span><span class="sxs-lookup"><span data-stu-id="89f3b-106">Each replication agent supports a set of run-time parameters used to control how it runs; these parameters are specified in an agent profile or on the command line.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="89f3b-107">默认情况下，安装完 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 之后， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 代理服务处于禁用状态，除非在安装过程中明确选择自动启动该服务。</span><span class="sxs-lookup"><span data-stu-id="89f3b-107">By default, the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent service is disabled when [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is installed unless you explicitly choose to autostart the service during installation.</span></span>  
  
 <span data-ttu-id="89f3b-108">复制代理文件位于 [!INCLUDE[ssInstallPathVar](../../../includes/ssinstallpathvar-md.md)]\COM 目录下。</span><span class="sxs-lookup"><span data-stu-id="89f3b-108">Replication agent files are located under [!INCLUDE[ssInstallPathVar](../../../includes/ssinstallpathvar-md.md)]\COM.</span></span> <span data-ttu-id="89f3b-109">下表列出了可执行复制的名称和文件名。</span><span class="sxs-lookup"><span data-stu-id="89f3b-109">The following table lists the replication executable names and file names.</span></span> <span data-ttu-id="89f3b-110">单击代理链接可查看其参数引用。</span><span class="sxs-lookup"><span data-stu-id="89f3b-110">Click the link for an agent to view its parameter reference.</span></span>  
  
|<span data-ttu-id="89f3b-111">可执行代理</span><span class="sxs-lookup"><span data-stu-id="89f3b-111">Agent Executable</span></span>|<span data-ttu-id="89f3b-112">文件名</span><span class="sxs-lookup"><span data-stu-id="89f3b-112">File Name</span></span>|  
|----------------------|---------------|  
|[<span data-ttu-id="89f3b-113">Replication Snapshot Agent</span><span class="sxs-lookup"><span data-stu-id="89f3b-113">Replication Snapshot Agent</span></span>](replication-snapshot-agent.md)|<span data-ttu-id="89f3b-114">snapshot.exe</span><span class="sxs-lookup"><span data-stu-id="89f3b-114">snapshot.exe</span></span>|  
|[<span data-ttu-id="89f3b-115">Replication Distribution Agent</span><span class="sxs-lookup"><span data-stu-id="89f3b-115">Replication Distribution Agent</span></span>](replication-distribution-agent.md)|<span data-ttu-id="89f3b-116">distrib.exe</span><span class="sxs-lookup"><span data-stu-id="89f3b-116">distrib.exe</span></span>|  
|[<span data-ttu-id="89f3b-117">复制日志读取器代理</span><span class="sxs-lookup"><span data-stu-id="89f3b-117">Replication Log Reader Agent</span></span>](replication-log-reader-agent.md)|<span data-ttu-id="89f3b-118">logread.exe</span><span class="sxs-lookup"><span data-stu-id="89f3b-118">logread.exe</span></span>|  
|[<span data-ttu-id="89f3b-119">复制队列读取器代理</span><span class="sxs-lookup"><span data-stu-id="89f3b-119">Replication Queue Reader Agent</span></span>](replication-queue-reader-agent.md)|<span data-ttu-id="89f3b-120">qrdrsvc.exe</span><span class="sxs-lookup"><span data-stu-id="89f3b-120">qrdrsvc.exe</span></span>|  
|[<span data-ttu-id="89f3b-121">Replication Merge Agent</span><span class="sxs-lookup"><span data-stu-id="89f3b-121">Replication Merge Agent</span></span>](replication-merge-agent.md)|<span data-ttu-id="89f3b-122">replmerg.exe</span><span class="sxs-lookup"><span data-stu-id="89f3b-122">replmerg.exe</span></span>|  
  
 <span data-ttu-id="89f3b-123">除了复制代理之外，复制还有大量执行计划维护和按需维护的作业。</span><span class="sxs-lookup"><span data-stu-id="89f3b-123">In addition to replication agents, replication has a number of jobs that perform scheduled and on-demand maintenance.</span></span>  
  
 <span data-ttu-id="89f3b-124">**运行代理和运行维护作业**</span><span class="sxs-lookup"><span data-stu-id="89f3b-124">**To run agents and maintenance jobs**</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]<span data-ttu-id="89f3b-125">复制监视器：[启动和停止复制代理 &#40;SQL Server Management Studio&#41;](start-and-stop-a-replication-agent-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="89f3b-125">and Replication Monitor: [Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](start-and-stop-a-replication-agent-sql-server-management-studio.md).</span></span>  
  
-   <span data-ttu-id="89f3b-126">复制编程：[Replication Agent Executables Concepts](../concepts/replication-agent-executables-concepts.md)</span><span class="sxs-lookup"><span data-stu-id="89f3b-126">Replication programming: [Replication Agent Executables Concepts](../concepts/replication-agent-executables-concepts.md)</span></span>  
  
## <a name="agent-profiles"></a><span data-ttu-id="89f3b-127">代理配置文件</span><span class="sxs-lookup"><span data-stu-id="89f3b-127">Agent Profiles</span></span>  
 <span data-ttu-id="89f3b-128">在配置复制时，将在分发服务器上安装一组代理配置文件。</span><span class="sxs-lookup"><span data-stu-id="89f3b-128">When replication is configured, a set of agent profiles is installed on the Distributor.</span></span> <span data-ttu-id="89f3b-129">代理配置文件包含一组在代理每次运行时都要使用的参数：在代理启动过程中，每个代理都会登录到分发服务器，并查询其配置文件中的参数。</span><span class="sxs-lookup"><span data-stu-id="89f3b-129">An agent profile contains a set of parameters that are used each time an agent runs: each agent logs in to the Distributor during its startup process and queries for the parameters in its profile.</span></span> <span data-ttu-id="89f3b-130">复制为每个代理提供一个默认的配置文件，同时还为日志读取器代理、分发代理和合并代理提供附加的预定义配置文件。</span><span class="sxs-lookup"><span data-stu-id="89f3b-130">Replication provides a default profile for each agent and additional predefined profiles for the Log Reader Agent, Distribution Agent, and Merge Agent.</span></span> <span data-ttu-id="89f3b-131">除了所提供的配置文件之外，您还可以创建符合自己应用程序要求的配置文件。</span><span class="sxs-lookup"><span data-stu-id="89f3b-131">In addition to the profiles provided, you can create profiles suited to your application requirements.</span></span> <span data-ttu-id="89f3b-132">有关详细信息，请参阅 [Replication Agent Profiles](replication-agent-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="89f3b-132">For more information, see [Replication Agent Profiles](replication-agent-profiles.md).</span></span>  
  
 <span data-ttu-id="89f3b-133">有关如何直接指定命令行参数的信息，请参阅[复制代理可执行文件概念](../concepts/replication-agent-executables-concepts.md)。</span><span class="sxs-lookup"><span data-stu-id="89f3b-133">For information about specifying command line parameters directly, see [Replication Agent Executables Concepts](../concepts/replication-agent-executables-concepts.md).</span></span>  
  
## <a name="monitoring-replication-agents"></a><span data-ttu-id="89f3b-134">监视复制代理</span><span class="sxs-lookup"><span data-stu-id="89f3b-134">Monitoring Replication Agents</span></span>  
 <span data-ttu-id="89f3b-135">复制监视器使您可以查看信息和执行与每个复制代理关联的任务。</span><span class="sxs-lookup"><span data-stu-id="89f3b-135">Replication Monitor allows you to view information and perform tasks associated with each replication agent.</span></span> <span data-ttu-id="89f3b-136">以下列表列出了每个代理、可以在其中找到代理的选项卡（位于复制监视器中）以及指向说明如何访问这些选项卡的主题的链接：</span><span class="sxs-lookup"><span data-stu-id="89f3b-136">The following list includes each agent, the tabs in the Replication Monitor on which it can be found, and a link to a topic that explains how to access these tabs:</span></span>  
  
-   <span data-ttu-id="89f3b-137">以下代理与复制监视器中的发布相关联：</span><span class="sxs-lookup"><span data-stu-id="89f3b-137">The following agents are associated with publications in Replication Monitor:</span></span>  
  
    -   <span data-ttu-id="89f3b-138">快照代理</span><span class="sxs-lookup"><span data-stu-id="89f3b-138">Snapshot Agent</span></span>  
  
    -   <span data-ttu-id="89f3b-139">日志读取器代理</span><span class="sxs-lookup"><span data-stu-id="89f3b-139">Log Reader Agent</span></span>  
  
    -   <span data-ttu-id="89f3b-140">队列读取器代理</span><span class="sxs-lookup"><span data-stu-id="89f3b-140">Queue Reader Agent</span></span>  
  
     <span data-ttu-id="89f3b-141">通过 "**代理**" 选项卡访问与这些代理关联的信息和任务。有关详细信息，请参阅[使用复制监视器查看信息和执行任务](../monitor/view-information-and-perform-tasks-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="89f3b-141">Access information and tasks associated with these agents through the **Agents** tab. For more information, see [View Information and Perform Tasks using Replication Monitor](../monitor/view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
-   <span data-ttu-id="89f3b-142">以下代理与复制监视器中的订阅相关联：</span><span class="sxs-lookup"><span data-stu-id="89f3b-142">The following agents are associated with subscriptions in Replication Monitor:</span></span>  
  
    -   <span data-ttu-id="89f3b-143">分发代理</span><span class="sxs-lookup"><span data-stu-id="89f3b-143">Distribution Agent</span></span>  
  
    -   <span data-ttu-id="89f3b-144">合并代理</span><span class="sxs-lookup"><span data-stu-id="89f3b-144">Merge Agent</span></span>  
  
     <span data-ttu-id="89f3b-145">通过以下选项卡访问与这些代理相关联的信息和任务：“订阅监视列表”（所有发布服务器都提供）或“所有订阅”选项卡（所有发布都提供） 。</span><span class="sxs-lookup"><span data-stu-id="89f3b-145">Access information and tasks associated with these agents through the following tabs: **Subscription Watch List** (available for each Publisher) or the **All Subscriptions** tab (available for each publication).</span></span> <span data-ttu-id="89f3b-146">有关详细信息，请参阅[使用复制监视器查看信息和执行任务](../monitor/view-information-and-perform-tasks-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="89f3b-146">For more information, see [View Information and Perform Tasks using Replication Monitor](../monitor/view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
## <a name="independent-and-shared-agents"></a><span data-ttu-id="89f3b-147">独立代理和共享代理</span><span class="sxs-lookup"><span data-stu-id="89f3b-147">Independent and Shared Agents</span></span>  
 <span data-ttu-id="89f3b-148">独立代理是为一个订阅提供服务的代理。</span><span class="sxs-lookup"><span data-stu-id="89f3b-148">An independent agent is an agent that services one subscription.</span></span> <span data-ttu-id="89f3b-149">共享代理为多个订阅提供服务；如果使用同一共享代理的多个订阅需要同步，则在默认情况下，它们会排队等候，共享代理一次为一个订阅提供服务。</span><span class="sxs-lookup"><span data-stu-id="89f3b-149">A shared agent services multiple subscriptions; if multiple subscriptions using the same shared agent need to synchronize, by default they wait in a queue, and the shared agent services them one at a time.</span></span> <span data-ttu-id="89f3b-150">使用独立代理会减少滞后时间，因为只要订阅需要同步，独立代理就可以为其提供服务。</span><span class="sxs-lookup"><span data-stu-id="89f3b-150">Latency is reduced when using independent agents because the agent is ready whenever the subscription needs to be synchronized.</span></span> <span data-ttu-id="89f3b-151">合并复制始终使用独立代理，而事务复制在默认情况下为在新建发布向导中创建的发布使用独立代理（在早期的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]版本中，事务复制在默认情况下使用共享代理）。</span><span class="sxs-lookup"><span data-stu-id="89f3b-151">Merge replication always uses independent agents, and transactional replication uses independent agents by default for publications created in the New Publication Wizard (in previous versions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], transactional replication used shared agents by default).</span></span>  
  
## <a name="replication-maintenance-jobs"></a><span data-ttu-id="89f3b-152">复制维护作业</span><span class="sxs-lookup"><span data-stu-id="89f3b-152">Replication Maintenance Jobs</span></span>  
 <span data-ttu-id="89f3b-153">复制使用下列作业来执行计划维护和按需维护。</span><span class="sxs-lookup"><span data-stu-id="89f3b-153">Replication uses the following jobs to perform scheduled and on-demand maintenance.</span></span>  
  
|<span data-ttu-id="89f3b-154">清除作业</span><span class="sxs-lookup"><span data-stu-id="89f3b-154">Clean up job</span></span>|<span data-ttu-id="89f3b-155">说明</span><span class="sxs-lookup"><span data-stu-id="89f3b-155">Description</span></span>|<span data-ttu-id="89f3b-156">默认计划</span><span class="sxs-lookup"><span data-stu-id="89f3b-156">Default schedule</span></span>|  
|------------------|-----------------|----------------------|  
|<span data-ttu-id="89f3b-157">清除代理历史记录：分发</span><span class="sxs-lookup"><span data-stu-id="89f3b-157">Agent History Clean Up: Distribution</span></span>|<span data-ttu-id="89f3b-158">从分发数据库中删除复制代理历史记录。</span><span class="sxs-lookup"><span data-stu-id="89f3b-158">Removes replication agent history from the distribution database.</span></span>|<span data-ttu-id="89f3b-159">每十分钟运行一次</span><span class="sxs-lookup"><span data-stu-id="89f3b-159">Runs every ten minutes</span></span>|  
|<span data-ttu-id="89f3b-160">清除分发：分发</span><span class="sxs-lookup"><span data-stu-id="89f3b-160">Distribution Clean Up: Distribution</span></span>|<span data-ttu-id="89f3b-161">从分发数据库中删除复制的事务。</span><span class="sxs-lookup"><span data-stu-id="89f3b-161">Removes replicated transactions from the distribution database.</span></span> <span data-ttu-id="89f3b-162">停用在最大分发保持期内尚未同步的订阅。</span><span class="sxs-lookup"><span data-stu-id="89f3b-162">Deactivates subscriptions that have not been synchronized within the maximum distribution retention period.</span></span>|<span data-ttu-id="89f3b-163">每十分钟运行一次</span><span class="sxs-lookup"><span data-stu-id="89f3b-163">Runs every ten minutes</span></span>|  
|<span data-ttu-id="89f3b-164">过期订阅清除</span><span class="sxs-lookup"><span data-stu-id="89f3b-164">Expired Subscription Clean Up</span></span>|<span data-ttu-id="89f3b-165">从发布数据库检测和删除过期的订阅。</span><span class="sxs-lookup"><span data-stu-id="89f3b-165">Detects and removes expired subscriptions from publication databases.</span></span>|<span data-ttu-id="89f3b-166">每天凌晨 1:00 运行</span><span class="sxs-lookup"><span data-stu-id="89f3b-166">Runs every day at 1:00 A.M.</span></span>|  
|<span data-ttu-id="89f3b-167">重新初始化数据验证失败的订阅</span><span class="sxs-lookup"><span data-stu-id="89f3b-167">Reinitialize Subscriptions Having Data Validation Failures</span></span>|<span data-ttu-id="89f3b-168">检测所有未通过数据验证的订阅并标记它们以进行重新初始化。</span><span class="sxs-lookup"><span data-stu-id="89f3b-168">Detects all subscriptions that have data validation failures and marks them for reinitialization.</span></span> <span data-ttu-id="89f3b-169">下次合并代理或分发代理运行时，订阅服务器上将应用新快照。</span><span class="sxs-lookup"><span data-stu-id="89f3b-169">The next time the Merge Agent or Distribution Agent runs, a new snapshot will be applied at the Subscribers.</span></span>|<span data-ttu-id="89f3b-170">无默认调度（默认情况下未启用）。</span><span class="sxs-lookup"><span data-stu-id="89f3b-170">No default schedule (not enabled by default).</span></span>|  
|<span data-ttu-id="89f3b-171">复制代理检查</span><span class="sxs-lookup"><span data-stu-id="89f3b-171">Replication Agents Checkup</span></span>|<span data-ttu-id="89f3b-172">检测未积极记录历史信息的复制代理。</span><span class="sxs-lookup"><span data-stu-id="89f3b-172">Detects replication agents that are not actively logging history.</span></span> <span data-ttu-id="89f3b-173">如果作业步骤失败，它将写入 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows 事件日志。</span><span class="sxs-lookup"><span data-stu-id="89f3b-173">It writes to the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows event log if a job step fails.</span></span>|<span data-ttu-id="89f3b-174">每十分钟运行一次。</span><span class="sxs-lookup"><span data-stu-id="89f3b-174">Runs every ten minutes.</span></span>|  
|<span data-ttu-id="89f3b-175">分发的复制监视刷新器</span><span class="sxs-lookup"><span data-stu-id="89f3b-175">Replication monitoring refresher for distribution</span></span>|<span data-ttu-id="89f3b-176">刷新复制监视器所使用的缓存的查询。</span><span class="sxs-lookup"><span data-stu-id="89f3b-176">Refreshes cached queries used by Replication Monitor..</span></span>|<span data-ttu-id="89f3b-177">连续运行。</span><span class="sxs-lookup"><span data-stu-id="89f3b-177">Runs continuously.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="89f3b-178">另请参阅</span><span class="sxs-lookup"><span data-stu-id="89f3b-178">See Also</span></span>  
 [<span data-ttu-id="89f3b-179">监视复制</span><span class="sxs-lookup"><span data-stu-id="89f3b-179">Monitoring Replication</span></span>](../monitoring-replication.md)  
  
  
