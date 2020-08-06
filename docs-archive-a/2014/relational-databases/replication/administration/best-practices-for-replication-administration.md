---
title: 复制管理最佳做法 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- administering replication, best practices
- replication [SQL Server], administering
ms.assetid: 850e8a87-b34c-4934-afb5-a1104f118ba8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 16652561fa873c5d8a33d8826372837744543e70
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691697"
---
# <a name="best-practices-for-replication-administration"></a><span data-ttu-id="596c0-102">复制管理最佳实践</span><span class="sxs-lookup"><span data-stu-id="596c0-102">Best Practices for Replication Administration</span></span>
  <span data-ttu-id="596c0-103">在配置复制后，了解如何管理复制拓扑十分重要。</span><span class="sxs-lookup"><span data-stu-id="596c0-103">After you have configured replication, it is important to understand how to administer a replication topology.</span></span> <span data-ttu-id="596c0-104">本主题介绍了许多方面的基本最佳实践指导原则，还提供了有关每一方面的详细信息的链接。</span><span class="sxs-lookup"><span data-stu-id="596c0-104">This topic provides basic best practice guidance in a number of areas with links to more information for each area.</span></span> <span data-ttu-id="596c0-105">除遵循本主题中介绍的最佳实践指导原则之外，还请仔细阅读常见问题解答主题，以了解常见的问题：[复制管理常见问题解答](frequently-asked-questions-for-replication-administrators.md)。</span><span class="sxs-lookup"><span data-stu-id="596c0-105">In addition to following the best practice guidance presented in this topic, consider reading through the frequently asked questions topic to acquaint yourself with common questions and issues: [Frequently Asked Questions for Replication Administrators](frequently-asked-questions-for-replication-administrators.md).</span></span>  
  
 <span data-ttu-id="596c0-106">将最佳实践指导原则分成两个部分很有用：</span><span class="sxs-lookup"><span data-stu-id="596c0-106">It is useful to divide the best practice guidance into two areas:</span></span>  
  
-   <span data-ttu-id="596c0-107">下列信息介绍应为所有复制拓扑实现的最佳实践：</span><span class="sxs-lookup"><span data-stu-id="596c0-107">The following information covers best practices that should be implemented for all replication topologies:</span></span>  
  
    -   <span data-ttu-id="596c0-108">开发并测试备份和还原策略。</span><span class="sxs-lookup"><span data-stu-id="596c0-108">Develop and test a backup and restore strategy.</span></span>  
  
    -   <span data-ttu-id="596c0-109">编写复制拓扑脚本。</span><span class="sxs-lookup"><span data-stu-id="596c0-109">Script the replication topology.</span></span>  
  
    -   <span data-ttu-id="596c0-110">创建阈值和警报。</span><span class="sxs-lookup"><span data-stu-id="596c0-110">Create thresholds and alerts.</span></span>  
  
    -   <span data-ttu-id="596c0-111">监视复制拓扑。</span><span class="sxs-lookup"><span data-stu-id="596c0-111">Monitor the replication topology.</span></span>  
  
    -   <span data-ttu-id="596c0-112">如果有必要，确定性能基准并优化复制。</span><span class="sxs-lookup"><span data-stu-id="596c0-112">Establish performance baselines and tune replication if necessary.</span></span>  
  
-   <span data-ttu-id="596c0-113">下列信息介绍应该考虑，但可能不是您的拓扑所必需的最佳实践：</span><span class="sxs-lookup"><span data-stu-id="596c0-113">The following information covers best practices that should be considered, but might not be required for your topology:</span></span>  
  
    -   <span data-ttu-id="596c0-114">定期验证数据。</span><span class="sxs-lookup"><span data-stu-id="596c0-114">Validate data periodically.</span></span>  
  
    -   <span data-ttu-id="596c0-115">通过配置文件调整代理参数。</span><span class="sxs-lookup"><span data-stu-id="596c0-115">Adjust agent parameters through profiles.</span></span>  
  
    -   <span data-ttu-id="596c0-116">调整发布和分发保持期。</span><span class="sxs-lookup"><span data-stu-id="596c0-116">Adjust publication and distribution retention periods.</span></span>  
  
    -   <span data-ttu-id="596c0-117">如果应用程序要求发生更改，了解如何更改项目和发布属性。</span><span class="sxs-lookup"><span data-stu-id="596c0-117">Understand how to change article and publication properties if application requirements change.</span></span>  
  
    -   <span data-ttu-id="596c0-118">如果应用程序要求发生更改，了解如何进行架构更改。</span><span class="sxs-lookup"><span data-stu-id="596c0-118">Understand how to make schema changes if application requirements change.</span></span>  
  
## <a name="develop-and-test-a-backup-and-restore-strategy"></a><span data-ttu-id="596c0-119">开发并测试备份和还原策略</span><span class="sxs-lookup"><span data-stu-id="596c0-119">Develop and test a backup and restore strategy</span></span>  
 <span data-ttu-id="596c0-120">所有数据库都应定期备份，还应对还原这些备份的能力定期进行测试；复制的数据库没有差异。</span><span class="sxs-lookup"><span data-stu-id="596c0-120">All databases should be backed up on a regular basis, and the ability to restore those backups should be tested periodically; replicated databases are no different.</span></span> <span data-ttu-id="596c0-121">下列数据库应定期备份：</span><span class="sxs-lookup"><span data-stu-id="596c0-121">The following databases should be backed up regularly:</span></span>  
  
-   <span data-ttu-id="596c0-122">发布数据库</span><span class="sxs-lookup"><span data-stu-id="596c0-122">Publication database</span></span>  
  
-   <span data-ttu-id="596c0-123">分发数据库</span><span class="sxs-lookup"><span data-stu-id="596c0-123">Distribution database</span></span>  
  
-   <span data-ttu-id="596c0-124">订阅数据库</span><span class="sxs-lookup"><span data-stu-id="596c0-124">Subscription databases</span></span>  
  
-   <span data-ttu-id="596c0-125">发布服务器、分发服务器和所有订阅服务器上的**msdb** 数据库和 **master** 数据库</span><span class="sxs-lookup"><span data-stu-id="596c0-125">**msdb** database and **master** database at the Publisher, Distributor, and all Subscribers</span></span>  
  
 <span data-ttu-id="596c0-126">对于复制的数据库，需要特别注意与备份和还原数据有关的信息。</span><span class="sxs-lookup"><span data-stu-id="596c0-126">Replicated databases require special attention with regards to backing up and restoring data.</span></span> <span data-ttu-id="596c0-127">有关详细信息，请参阅 [备份和还原复制的数据库](back-up-and-restore-replicated-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="596c0-127">For more information, see [Back Up and Restore Replicated Databases](back-up-and-restore-replicated-databases.md).</span></span>  
  
## <a name="script-the-replication-topology"></a><span data-ttu-id="596c0-128">编写复制拓扑脚本</span><span class="sxs-lookup"><span data-stu-id="596c0-128">Script the replication topology</span></span>  
 <span data-ttu-id="596c0-129">制订灾难恢复计划时，应要求对拓扑中的所有复制组件编写脚本，另外，脚本还可以用来自动处理重复性的任务。</span><span class="sxs-lookup"><span data-stu-id="596c0-129">All replication components in a topology should be scripted as part of a disaster recovery plan, and scripts can also be used to automate repetitive tasks.</span></span> <span data-ttu-id="596c0-130">脚本包含实现脚本化复制组件（如发布或订阅）所需的 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 系统存储过程。</span><span class="sxs-lookup"><span data-stu-id="596c0-130">A script contains the [!INCLUDE[tsql](../../../includes/tsql-md.md)] system stored procedures necessary to implement the replication component(s) scripted, such as a publication or subscription.</span></span> <span data-ttu-id="596c0-131">创建完组件后，可以在向导（如新建发布向导）或 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 中创建脚本。</span><span class="sxs-lookup"><span data-stu-id="596c0-131">Scripts can be created in a wizard (such as the New Publication Wizard) or in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] after you create a component.</span></span> <span data-ttu-id="596c0-132">您可以使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 或 **sqlcmd**查看、修改和运行脚本。</span><span class="sxs-lookup"><span data-stu-id="596c0-132">You can view, modify, and run the script using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or **sqlcmd**.</span></span> <span data-ttu-id="596c0-133">脚本可以与备份文件存储在一起，以便在必须重新配置复制拓扑时使用。</span><span class="sxs-lookup"><span data-stu-id="596c0-133">Scripts can be stored with backup files to be used in case a replication topology must be reconfigured.</span></span> <span data-ttu-id="596c0-134">有关详细信息，请参阅 [Scripting Replication](../scripting-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="596c0-134">For more information, see [Scripting Replication](../scripting-replication.md).</span></span>  
  
 <span data-ttu-id="596c0-135">如果进行了任何属性更改，则应重新编写组件脚本。</span><span class="sxs-lookup"><span data-stu-id="596c0-135">A component should be rescripted if any property changes are made.</span></span> <span data-ttu-id="596c0-136">如果对事务复制使用自定义存储过程，则应与脚本一起存储每个过程的副本。如果过程发生更改，应更新相应的副本（通常会由于架构更改或应用程序要求的更改而更新过程）。</span><span class="sxs-lookup"><span data-stu-id="596c0-136">If you use custom stored procedures with transactional replication, a copy of each procedure should be stored with the scripts; the copy should be updated if the procedure changes (procedures are typically updated due to schema changes or changing application requirements).</span></span> <span data-ttu-id="596c0-137">有关自定义过程的详细信息，请参阅[指定如何传播事务项目的更改](../transactional/transactional-articles-specify-how-changes-are-propagated.md)。</span><span class="sxs-lookup"><span data-stu-id="596c0-137">For more information about custom procedures, see [Specify How Changes Are Propagated for Transactional Articles](../transactional/transactional-articles-specify-how-changes-are-propagated.md).</span></span>  
  
## <a name="establish-performance-baselines-and-tune-replication-if-necessary"></a><span data-ttu-id="596c0-138">如果有必要，确定性能基准并优化复制</span><span class="sxs-lookup"><span data-stu-id="596c0-138">Establish performance baselines and tune replication if necessary</span></span>  
 <span data-ttu-id="596c0-139">配置复制前，建议先熟悉一下影响复制性能的因素：</span><span class="sxs-lookup"><span data-stu-id="596c0-139">Before replication is configured, it is recommended to familiarize yourself with the factors that affect replication performance:</span></span>  
  
-   <span data-ttu-id="596c0-140">服务器和网络硬件</span><span class="sxs-lookup"><span data-stu-id="596c0-140">Server and network hardware</span></span>  
  
-   <span data-ttu-id="596c0-141">数据库设计</span><span class="sxs-lookup"><span data-stu-id="596c0-141">Database design</span></span>  
  
-   <span data-ttu-id="596c0-142">分发服务器配置</span><span class="sxs-lookup"><span data-stu-id="596c0-142">Distributor configuration</span></span>  
  
-   <span data-ttu-id="596c0-143">发布设计和选项</span><span class="sxs-lookup"><span data-stu-id="596c0-143">Publication design and options</span></span>  
  
-   <span data-ttu-id="596c0-144">筛选器设计和用法</span><span class="sxs-lookup"><span data-stu-id="596c0-144">Filter design and use</span></span>  
  
-   <span data-ttu-id="596c0-145">订阅选项</span><span class="sxs-lookup"><span data-stu-id="596c0-145">Subscription options</span></span>  
  
-   <span data-ttu-id="596c0-146">快照选项</span><span class="sxs-lookup"><span data-stu-id="596c0-146">Snapshot options</span></span>  
  
-   <span data-ttu-id="596c0-147">代理参数</span><span class="sxs-lookup"><span data-stu-id="596c0-147">Agent parameters</span></span>  
  
-   <span data-ttu-id="596c0-148">维护</span><span class="sxs-lookup"><span data-stu-id="596c0-148">Maintenance</span></span>  
  
 <span data-ttu-id="596c0-149">配置复制后，建议制定一个性能基准，这使您可以确定复制在应用程序和拓扑的典型工作量下的行为。</span><span class="sxs-lookup"><span data-stu-id="596c0-149">After replication is configured, it is recommended to develop a performance baseline, which will allow you to determine how replication behaves with a workload that is typical for your applications and topology.</span></span> <span data-ttu-id="596c0-150">使用复制监视器和系统监视器确定复制性能的以下五个维度的典型数目：</span><span class="sxs-lookup"><span data-stu-id="596c0-150">Use Replication Monitor and System Monitor to determine typical numbers for the following five dimensions of replication performance:</span></span>  
  
-   <span data-ttu-id="596c0-151">滞后时间：在复制拓扑中的节点之间传播数据更改所用的时间。</span><span class="sxs-lookup"><span data-stu-id="596c0-151">Latency: the amount of time it takes for a data change to be propagated between nodes in a replication topology.</span></span>  
  
-   <span data-ttu-id="596c0-152">吞吐量：一段时间内系统可以持续的复制活动量（以一段时间内传递的命令来度量）。</span><span class="sxs-lookup"><span data-stu-id="596c0-152">Throughput: the amount of replication activity (measured in commands delivered over a period of time) a system can sustain over time.</span></span>  
  
-   <span data-ttu-id="596c0-153">并发：可以在系统上同时运行的复制进程数。</span><span class="sxs-lookup"><span data-stu-id="596c0-153">Concurrency: the number of replication processes that can operate on a system simultaneously.</span></span>  
  
-   <span data-ttu-id="596c0-154">同步持续时间：完成给定同步所用的时间。</span><span class="sxs-lookup"><span data-stu-id="596c0-154">Duration of synchronization: how long it takes a given synchronization to complete.</span></span>  
  
-   <span data-ttu-id="596c0-155">资源占用：复制处理结束时所用的硬件和网络资源。</span><span class="sxs-lookup"><span data-stu-id="596c0-155">Resource consumption: hardware and network resources used as a result of replication processing.</span></span>  
  
 <span data-ttu-id="596c0-156">滞后时间和吞吐量与事务复制关系最密切，因为建立在事务复制基础上的系统通常需要低滞后时间和大吞吐量。</span><span class="sxs-lookup"><span data-stu-id="596c0-156">Latency and throughput are most relevant to transactional replication, because systems built on transactional replication generally require low latency and high throughput.</span></span> <span data-ttu-id="596c0-157">并发和同步持续时间与合并复制关系最密切，因为建立在合并复制基础上的系统通常具有大量的订阅服务器，并且发布服务器可能具有大量与这些订阅服务器的并发同步。</span><span class="sxs-lookup"><span data-stu-id="596c0-157">Concurrency and duration of synchronization are most relevant to merge replication, because systems built on merge replication often have a large number of Subscribers, and a Publisher can have a significant number of concurrent synchronizations with these Subscribers.</span></span>  
  
 <span data-ttu-id="596c0-158">确定基准数目后，请在复制监视器中设置阈值。</span><span class="sxs-lookup"><span data-stu-id="596c0-158">After you have established baseline numbers, set thresholds in Replication Monitor.</span></span> <span data-ttu-id="596c0-159">有关详细信息，请参阅[在复制监视器中设置阈值和警告](../monitor/set-thresholds-and-warnings-in-replication-monitor.md)和[对复制代理事件使用警报](../agents/use-alerts-for-replication-agent-events.md)。</span><span class="sxs-lookup"><span data-stu-id="596c0-159">For more information, see [Set Thresholds and Warnings in Replication Monitor](../monitor/set-thresholds-and-warnings-in-replication-monitor.md) and [Use Alerts for Replication Agent Events](../agents/use-alerts-for-replication-agent-events.md).</span></span> <span data-ttu-id="596c0-160">如果您遇到性能问题，建议您通读上面列出的增强性能主题中的建议，并在影响所遇到问题的区域中应用更改。</span><span class="sxs-lookup"><span data-stu-id="596c0-160">If you encounter a performance problem, it is recommended to read through the suggestions in the enhancing performance topics listed above and to apply changes in areas that affect the issues you are encountering.</span></span>  
  
## <a name="create-thresholds-and-alerts"></a><span data-ttu-id="596c0-161">创建阈值和警报</span><span class="sxs-lookup"><span data-stu-id="596c0-161">Create thresholds and alerts</span></span>  
 <span data-ttu-id="596c0-162">复制监视器允许您设置大量与状态和性能相关的阈值。</span><span class="sxs-lookup"><span data-stu-id="596c0-162">Replication Monitor allows you to set a number of thresholds related to status and performance.</span></span> <span data-ttu-id="596c0-163">建议为拓扑设置相应的阈值；如果达到阈值，将显示警告，而且（可选）可以向电子邮件帐户、寻呼机或其他设备发送警报。</span><span class="sxs-lookup"><span data-stu-id="596c0-163">It is recommended to set the appropriate thresholds for your topology; if a threshold is reached, a warning is displayed, and, optionally, an alert can be sent to an e-mail account, a pager, or other device.</span></span> <span data-ttu-id="596c0-164">有关详细信息，请参阅 [Set Thresholds and Warnings in Replication Monitor](../monitor/set-thresholds-and-warnings-in-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="596c0-164">For more information, see [Set Thresholds and Warnings in Replication Monitor](../monitor/set-thresholds-and-warnings-in-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="596c0-165">除了可与监视阈值关联的警报外，复制还提供大量响应复制代理操作的预定义警报。</span><span class="sxs-lookup"><span data-stu-id="596c0-165">In addition to the alerts that can be associated with monitoring thresholds, replication provides a number of predefined alerts that respond to replication agent actions.</span></span> <span data-ttu-id="596c0-166">管理员可以使用这些警报随时了解复制拓扑的状态。</span><span class="sxs-lookup"><span data-stu-id="596c0-166">These alerts can be used by an administrator to stay informed about the state of the replication topology.</span></span> <span data-ttu-id="596c0-167">建议通读描述警报的主题，并使用适合您的管理需要的警报（必要时还可以创建其他警报）。</span><span class="sxs-lookup"><span data-stu-id="596c0-167">It is recommended to read through the topic describing the alerts and to use any that fit your administration needs (it is also possible to create additional alerts if necessary).</span></span> <span data-ttu-id="596c0-168">有关详细信息，请参阅[对复制代理事件使用警报](../agents/use-alerts-for-replication-agent-events.md)。</span><span class="sxs-lookup"><span data-stu-id="596c0-168">For more information, see [Use Alerts for Replication Agent Events](../agents/use-alerts-for-replication-agent-events.md).</span></span>  
  
## <a name="monitor-the-replication-topology"></a><span data-ttu-id="596c0-169">监视复制拓扑</span><span class="sxs-lookup"><span data-stu-id="596c0-169">Monitor the replication topology</span></span>  
 <span data-ttu-id="596c0-170">建立复制拓扑并配置阈值和警报后，建议定期监视复制。</span><span class="sxs-lookup"><span data-stu-id="596c0-170">After the replication topology is in place and thresholds and alerts have been configured, it is recommended to regularly monitor replication.</span></span> <span data-ttu-id="596c0-171">监视复制拓扑是部署复制的一个重要方面。</span><span class="sxs-lookup"><span data-stu-id="596c0-171">Monitoring a replication topology is an important aspect of deploying replication.</span></span> <span data-ttu-id="596c0-172">因为复制活动是分布式的，所以跟踪复制过程中涉及的所有计算机的活动和状态非常有必要。</span><span class="sxs-lookup"><span data-stu-id="596c0-172">Because replication activity is distributed, it is essential to track activity and status across all computers involved in replication.</span></span> <span data-ttu-id="596c0-173">以下工具可用于监视复制：</span><span class="sxs-lookup"><span data-stu-id="596c0-173">The following tools can be used to monitor replication:</span></span>  
  
-   <span data-ttu-id="596c0-174">复制监视器是监视复制的最重要的工具，它允许您监视复制拓扑的总体运行状况。</span><span class="sxs-lookup"><span data-stu-id="596c0-174">Replication Monitor is the most important tool for monitoring replication, allowing you to monitor the overall health of a replication topology.</span></span> <span data-ttu-id="596c0-175">有关详细信息，请参阅 [Monitoring Replication](../monitoring-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="596c0-175">For more information, see [Monitoring Replication](../monitoring-replication.md).</span></span>  
  
-   [!INCLUDE[tsql](../../../includes/tsql-md.md)] <span data-ttu-id="596c0-176">和复制管理对象 (RMO) 提供了监视复制的接口。</span><span class="sxs-lookup"><span data-stu-id="596c0-176">and Replication Management Objects (RMO) provide interfaces for monitoring replication.</span></span> <span data-ttu-id="596c0-177">有关详细信息，请参阅 [Monitoring Replication](../monitoring-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="596c0-177">For more information, see [Monitoring Replication](../monitoring-replication.md).</span></span>  
  
-   <span data-ttu-id="596c0-178">系统监视器也可用于监视复制性能。</span><span class="sxs-lookup"><span data-stu-id="596c0-178">System Monitor can also be useful for monitoring replication performance.</span></span> <span data-ttu-id="596c0-179">有关详细信息，请参阅 [Monitoring Replication with System Monitor](../monitor/monitoring-replication-with-system-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="596c0-179">For more information, see [Monitoring Replication with System Monitor](../monitor/monitoring-replication-with-system-monitor.md).</span></span>  
  
## <a name="validate-data-periodically"></a><span data-ttu-id="596c0-180">定期验证数据</span><span class="sxs-lookup"><span data-stu-id="596c0-180">Validate data periodically</span></span>  
 <span data-ttu-id="596c0-181">复制不要求验证，但建议对事务复制和合并复制定期运行验证。</span><span class="sxs-lookup"><span data-stu-id="596c0-181">Validation is not required by replication, but it is recommended to run validation periodically for transactional replication and merge replication.</span></span> <span data-ttu-id="596c0-182">验证允许您验证订阅服务器上的数据与发布服务器上的数据是否匹配。</span><span class="sxs-lookup"><span data-stu-id="596c0-182">Validation allows you to verify that data at the Subscriber matches data at the Publisher.</span></span> <span data-ttu-id="596c0-183">验证成功表示当时发布服务器上的所有更改已复制到订阅服务器上（如果订阅服务器支持更新，则订阅服务器上的所有更改也复制到发布服务器上）并且两个数据库是同步的。</span><span class="sxs-lookup"><span data-stu-id="596c0-183">Successful validation indicates that at that point in time all changes from the Publisher have been replicated to the Subscriber (and from the Subscriber to the Publisher if updates are supported at the Subscriber) and that the two databases are in sync.</span></span>  
  
 <span data-ttu-id="596c0-184">建议根据发布数据库的备份计划执行验证。</span><span class="sxs-lookup"><span data-stu-id="596c0-184">It is recommended that validation be performed according to the backup schedule of the publication database.</span></span> <span data-ttu-id="596c0-185">例如，如果发布数据库有一个每周执行一次的完整备份，则可以在每周完成备份后运行一次验证。</span><span class="sxs-lookup"><span data-stu-id="596c0-185">For example, if the publication database has a full backup once per week, validation could be run once per week after the backup completes.</span></span> <span data-ttu-id="596c0-186">有关详细信息，请参阅[验证已复制的数据](../validate-data-at-the-subscriber.md)。</span><span class="sxs-lookup"><span data-stu-id="596c0-186">For more information, see [Validate Replicated Data](../validate-data-at-the-subscriber.md).</span></span>  
  
## <a name="use-agent-profiles-to-change-agent-parameters-if-necessary"></a><span data-ttu-id="596c0-187">如果有必要，使用代理配置文件更改代理参数</span><span class="sxs-lookup"><span data-stu-id="596c0-187">Use agent profiles to change agent parameters if necessary</span></span>  
 <span data-ttu-id="596c0-188">代理配置文件为设置复制代理参数提供了一个便利的方法。</span><span class="sxs-lookup"><span data-stu-id="596c0-188">Agent profiles provide a convenient method of setting replication agent parameters.</span></span> <span data-ttu-id="596c0-189">也可以在代理命令行上指定参数，但通常更适合使用预定义的代理配置文件或创建新的配置文件（如果需要更改参数值）。</span><span class="sxs-lookup"><span data-stu-id="596c0-189">Parameters can also be specified on the agent command line, but it is typically more appropriate to use a predefined agent profile or to create a new profile if you need to change the value of a parameter.</span></span> <span data-ttu-id="596c0-190">例如，如果使用合并复制并且订阅服务器从宽带连接转为拨号连接，这时可考虑使用合并代理的“慢速链接”  配置文件，此配置文件使用一组更适合慢速通信链接的参数。</span><span class="sxs-lookup"><span data-stu-id="596c0-190">For example, if you are using merge replication and a Subscriber moves from a broadband connection to a dialup connection, consider using the **slow link** profile for the Merge Agent; this profile uses a set of parameters that are better suited to the slower communications link.</span></span> <span data-ttu-id="596c0-191">有关详细信息，请参阅 [Replication Agent Profiles](../agents/replication-agent-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="596c0-191">For more information, see [Replication Agent Profiles](../agents/replication-agent-profiles.md).</span></span>  
  
## <a name="adjust-publication-and-distribution-retention-periods-if-necessary"></a><span data-ttu-id="596c0-192">如果有必要，调整发布和分发保持期</span><span class="sxs-lookup"><span data-stu-id="596c0-192">Adjust publication and distribution retention periods if necessary</span></span>  
 <span data-ttu-id="596c0-193">事务复制和合并复制分别使用保持期确定事务在分发数据库中的存储时间以及订阅必须同步的频率。</span><span class="sxs-lookup"><span data-stu-id="596c0-193">Transactional replication and merge replication use retention periods to determine, respectively, how long transactions are stored in the distribution database, and how frequently a subscription must synchronize.</span></span> <span data-ttu-id="596c0-194">建议开始时使用默认设置，但要监视拓扑以确定是否需要调整默认设置。</span><span class="sxs-lookup"><span data-stu-id="596c0-194">It is recommended to use the default settings initially, but to monitor your topology to determine if the settings require adjustment.</span></span> <span data-ttu-id="596c0-195">例如，在合并复制中，发布保持期（默认为 14 天）决定元数据在系统表中的存储时间。</span><span class="sxs-lookup"><span data-stu-id="596c0-195">For example, in the case of merge replication, the publication retention period (which defaults to 14 days) determines how long metadata is stored in system tables.</span></span> <span data-ttu-id="596c0-196">如果订阅总是在五天内同步，请考虑将该设置调整为较小的数字，这样可以减少元数据，还可能提供更好的性能。</span><span class="sxs-lookup"><span data-stu-id="596c0-196">If subscriptions always synchronize within five days, consider adjusting the setting to a lower number, which will reduce metadata and possibly provide better performance.</span></span> <span data-ttu-id="596c0-197">有关详细信息，请参阅 [Subscription Expiration and Deactivation](../subscription-expiration-and-deactivation.md)。</span><span class="sxs-lookup"><span data-stu-id="596c0-197">For more information, see [Subscription Expiration and Deactivation](../subscription-expiration-and-deactivation.md).</span></span>  
  
## <a name="understand-how-to-modify-publications-if-application-requirements-change"></a><span data-ttu-id="596c0-198">如果应用程序的要求发生更改，了解如何修改发布</span><span class="sxs-lookup"><span data-stu-id="596c0-198">Understand how to modify publications if application requirements change</span></span>  
 <span data-ttu-id="596c0-199">在创建发布后，可能需要添加或删除项目或者更改发布和项目属性。</span><span class="sxs-lookup"><span data-stu-id="596c0-199">After you have created a publication, it might be necessary to add or drop articles, or change publication and article properties.</span></span> <span data-ttu-id="596c0-200">创建发布后，多数更改是允许的，但在某些情况下还需要生成发布的新快照，并且/或者重新初始化对发布的订阅。</span><span class="sxs-lookup"><span data-stu-id="596c0-200">Most changes are allowed after a publication is created, but in some cases, it is necessary to generate a new snapshot for a publication and/or reinitialize subscriptions to the publication.</span></span> <span data-ttu-id="596c0-201">有关详细信息，请参阅[更改发布和项目属性](../publish/change-publication-and-article-properties.md)和[向现有发布添加项目和从中删除项目](../publish/add-articles-to-and-drop-articles-from-existing-publications.md)。</span><span class="sxs-lookup"><span data-stu-id="596c0-201">For more information, see [Change Publication and Article Properties](../publish/change-publication-and-article-properties.md) and [Add Articles to and Drop Articles from Existing Publications](../publish/add-articles-to-and-drop-articles-from-existing-publications.md).</span></span>  
  
## <a name="understand-how-to-make-schema-changes-if-application-requirements-change"></a><span data-ttu-id="596c0-202">如果应用程序的要求发生更改，了解如何进行架构更改</span><span class="sxs-lookup"><span data-stu-id="596c0-202">Understand how to make schema changes if application requirements change</span></span>  
 <span data-ttu-id="596c0-203">在很多情况下，将应用程序投入生产后都需要进行架构更改。</span><span class="sxs-lookup"><span data-stu-id="596c0-203">In many cases, schema changes are required after an application is in production.</span></span> <span data-ttu-id="596c0-204">在复制拓扑中，这些更改通常必须传播到所有的订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="596c0-204">In a replication topology, these changes must often be propagated to all Subscribers.</span></span> <span data-ttu-id="596c0-205">复制支持对已发布对象进行多种架构更改。</span><span class="sxs-lookup"><span data-stu-id="596c0-205">Replication supports a wide range of schema changes to published objects.</span></span> <span data-ttu-id="596c0-206">对 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 发布服务器中相应的发布对象进行下列任何一种架构更改时，默认会将该更改传播到所有 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 订阅服务器：</span><span class="sxs-lookup"><span data-stu-id="596c0-206">When you make any of the following schema changes on the appropriate published object at a [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Publisher, that change is propagated by default to all [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers:</span></span>  
  
-   <span data-ttu-id="596c0-207">ALTER TABLE</span><span class="sxs-lookup"><span data-stu-id="596c0-207">ALTER TABLE</span></span>  
  
-   <span data-ttu-id="596c0-208">ALTER VIEW</span><span class="sxs-lookup"><span data-stu-id="596c0-208">ALTER VIEW</span></span>  
  
-   <span data-ttu-id="596c0-209">ALTER PROCEDURE</span><span class="sxs-lookup"><span data-stu-id="596c0-209">ALTER PROCEDURE</span></span>  
  
-   <span data-ttu-id="596c0-210">ALTER FUNCTION</span><span class="sxs-lookup"><span data-stu-id="596c0-210">ALTER FUNCTION</span></span>  
  
-   <span data-ttu-id="596c0-211">ALTER TRIGGER</span><span class="sxs-lookup"><span data-stu-id="596c0-211">ALTER TRIGGER</span></span>  
  
 <span data-ttu-id="596c0-212">有关详细信息，请参阅[对发布数据库进行架构更改](../publish/make-schema-changes-on-publication-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="596c0-212">For more information, see [Make Schema Changes on Publication Databases](../publish/make-schema-changes-on-publication-databases.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="596c0-213">另请参阅</span><span class="sxs-lookup"><span data-stu-id="596c0-213">See Also</span></span>  
 [<span data-ttu-id="596c0-214">复制管理常见问题解答</span><span class="sxs-lookup"><span data-stu-id="596c0-214">Replication Administration FAQ</span></span>](frequently-asked-questions-for-replication-administrators.md)  
  
  
