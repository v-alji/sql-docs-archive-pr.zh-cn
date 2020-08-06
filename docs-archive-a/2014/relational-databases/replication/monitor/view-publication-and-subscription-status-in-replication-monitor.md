---
title: 在复制监视器中查看发布和订阅状态 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Log Reader Agent, monitoring
- Merge Agent, monitoring
- Queue Reader Agent, monitoring
- publications [SQL Server replication], viewing information
- Snapshot Agent, monitoring
- Distribution Agent, monitoring
- monitoring performance [SQL Server replication], publication status
- monitoring performance [SQL Server replication], subscription status
- subscriptions [SQL Server replication], viewing status
- Replication Monitor, publication and subscription status
ms.assetid: 16590771-9867-463e-a973-36a5c145ac16
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4f1f714e18a961546a4e5a7f6709beca8d525800
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693744"
---
# <a name="view-publication-and-subscription-status-in-replication-monitor"></a><span data-ttu-id="058de-102">在复制监视器中查看发布和订阅状态</span><span class="sxs-lookup"><span data-stu-id="058de-102">View Publication and Subscription Status in Replication Monitor</span></span>
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)]<span data-ttu-id="058de-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]复制监视器显示发布和订阅的状态信息：</span><span class="sxs-lookup"><span data-stu-id="058de-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Replication Monitor displays status information for publications and subscriptions:</span></span>  
  
-   <span data-ttu-id="058de-104">发布的状态由其订阅的最高优先级状态决定。</span><span class="sxs-lookup"><span data-stu-id="058de-104">The status of a publication is determined by the highest priority status of its subscriptions.</span></span> <span data-ttu-id="058de-105">例如，如果对发布的一个订阅有错误，另一个订阅有性能问题，则显示发布的错误状态。</span><span class="sxs-lookup"><span data-stu-id="058de-105">For example, if one subscription to a publication has an error and another has a performance issue, a status of error is displayed for the publication.</span></span>  
  
-   <span data-ttu-id="058de-106">订阅的状态由处理该订阅的代理的状态决定。</span><span class="sxs-lookup"><span data-stu-id="058de-106">The status of a subscription is determined by the status of the agents that service the subscription.</span></span> <span data-ttu-id="058de-107">对于合并复制，由合并代理的状态决定。</span><span class="sxs-lookup"><span data-stu-id="058de-107">For merge replication, this is the Merge Agent.</span></span> <span data-ttu-id="058de-108">对于事务复制，由日志读取器代理或分发代理（显示较高优先级状态；如果使用的是排队更新订阅，则状态还可以由队列读取器代理的状态决定）的状态决定。</span><span class="sxs-lookup"><span data-stu-id="058de-108">For transactional replication, this is either the Log Reader Agent or the Distribution Agent (the higher priority status is displayed; the status can also be determined by the Queue Reader Agent if queued updating subscriptions are used).</span></span> <span data-ttu-id="058de-109">对于快照复制，由快照代理或分发代理（显示较高优先级状态）的状态决定。</span><span class="sxs-lookup"><span data-stu-id="058de-109">For snapshot replication, this is the Snapshot Agent or the Distribution Agent (the higher priority status is displayed).</span></span>  
  
 <span data-ttu-id="058de-110">下列表列出了发布和订阅的可能状态值。</span><span class="sxs-lookup"><span data-stu-id="058de-110">Tables in the following sections list the possible status values for publications and subscriptions.</span></span> <span data-ttu-id="058de-111">只有在达到或超过阈值时，才显示三个状态值。</span><span class="sxs-lookup"><span data-stu-id="058de-111">Three of the status values are displayed only if a threshold is met or exceeded:</span></span>  
  
-   <span data-ttu-id="058de-112">过期订阅</span><span class="sxs-lookup"><span data-stu-id="058de-112">Expiring subscription</span></span>  
  
     <span data-ttu-id="058de-113">本状态值适用于所有类型的复制。</span><span class="sxs-lookup"><span data-stu-id="058de-113">This status value applies to all types of replication.</span></span> <span data-ttu-id="058de-114">有关详细信息，请参阅 [Set Thresholds and Warnings in Replication Monitor](set-thresholds-and-warnings-in-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="058de-114">For more information, see [Set Thresholds and Warnings in Replication Monitor](set-thresholds-and-warnings-in-replication-monitor.md).</span></span>  
  
-   <span data-ttu-id="058de-115">“严重”状态下的性能</span><span class="sxs-lookup"><span data-stu-id="058de-115">Performance critical</span></span>  
  
     <span data-ttu-id="058de-116">此状态值适用于事务复制和合并复制。</span><span class="sxs-lookup"><span data-stu-id="058de-116">This status value applies to transactional replication and merge replication.</span></span> <span data-ttu-id="058de-117">有关详细信息，请参阅[使用复制监视器监视性能](monitor-performance-with-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="058de-117">For more information, see [Monitor Performance with Replication Monitor](monitor-performance-with-replication-monitor.md).</span></span>  
  
-   <span data-ttu-id="058de-118">长时间运行的合并</span><span class="sxs-lookup"><span data-stu-id="058de-118">Long-running merge</span></span>  
  
     <span data-ttu-id="058de-119">此状态值适用于合并复制。</span><span class="sxs-lookup"><span data-stu-id="058de-119">This status value applies to merge replication.</span></span> <span data-ttu-id="058de-120">有关详细信息，请参阅[使用复制监视器监视性能](monitor-performance-with-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="058de-120">For more information, see [Monitor Performance with Replication Monitor](monitor-performance-with-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="058de-121">除提供发布和订阅状态外，合并复制还提供项目级统计信息，其中包括关于以下内容的详细信息：完成某个合并阶段还需要多长时间；处理某个给定项目花费的时间；订阅服务器正在使用的连接类型以及其他重要信息。</span><span class="sxs-lookup"><span data-stu-id="058de-121">In addition to publication and subscription status, merge replication provides article-level statistics, which give detailed information about: how much longer a merge phase will take to complete; how much time was spent processing a given article; the type of connection a Subscriber is using; and other important information.</span></span> <span data-ttu-id="058de-122">统计信息显示在复制监视器的合并代理窗口中。</span><span class="sxs-lookup"><span data-stu-id="058de-122">The statistics are displayed in the Merge Agent window in Replication Monitor.</span></span> <span data-ttu-id="058de-123">快照复制和事务复制提供有关分发代理处理的详细信息。</span><span class="sxs-lookup"><span data-stu-id="058de-123">Snapshot and transactional replication provide detailed information on Distribution Agent processing.</span></span>  
  
 <span data-ttu-id="058de-124">**查看发布和订阅状态**</span><span class="sxs-lookup"><span data-stu-id="058de-124">**To view publication and subscription status**</span></span>  
  
-   <span data-ttu-id="058de-125">复制监视器：[使用复制监视器查看信息和执行任务](view-information-and-perform-tasks-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="058de-125">Replication Monitor: [View Information and Perform Tasks using Replication Monitor](view-information-and-perform-tasks-replication-monitor.md).</span></span>
  
  
## <a name="publication-status-values"></a><span data-ttu-id="058de-126">发布状态值</span><span class="sxs-lookup"><span data-stu-id="058de-126">Publication Status Values</span></span>  
 <span data-ttu-id="058de-127">下表按优先级顺序显示了发布状态值及其对应的图标。</span><span class="sxs-lookup"><span data-stu-id="058de-127">The following table shows publication status values and their corresponding icons in priority order.</span></span>  
  
|<span data-ttu-id="058de-128">状态</span><span class="sxs-lookup"><span data-stu-id="058de-128">Status</span></span>|<span data-ttu-id="058de-129">图标</span><span class="sxs-lookup"><span data-stu-id="058de-129">Icon</span></span>|  
|------------|----------|  
|<span data-ttu-id="058de-130">错误</span><span class="sxs-lookup"><span data-stu-id="058de-130">Error</span></span>|<span data-ttu-id="058de-131">![UI 图标：错误](../media/repl-icon-error.gif "UI 图标：错误")</span><span class="sxs-lookup"><span data-stu-id="058de-131">![UI icon: error](../media/repl-icon-error.gif "UI icon: error")</span></span>|  
|<span data-ttu-id="058de-132">“严重”状态下的性能</span><span class="sxs-lookup"><span data-stu-id="058de-132">Performance critical</span></span>|<span data-ttu-id="058de-133">![UI 图标：警告](../media/repl-icon-warn.gif "UI 图标：警告")</span><span class="sxs-lookup"><span data-stu-id="058de-133">![UI icon: warning](../media/repl-icon-warn.gif "UI icon: warning")</span></span>|  
|<span data-ttu-id="058de-134">正在重试失败的命令</span><span class="sxs-lookup"><span data-stu-id="058de-134">Retrying failed command</span></span>|<span data-ttu-id="058de-135">![UI 图标：复制代理重试](../media/repl-icon-retry.gif "UI 图标：复制代理重试")</span><span class="sxs-lookup"><span data-stu-id="058de-135">![UI icon: replication agent retry](../media/repl-icon-retry.gif "UI icon: replication agent retry")</span></span>|  
|<span data-ttu-id="058de-136">确定</span><span class="sxs-lookup"><span data-stu-id="058de-136">OK</span></span>|<span data-ttu-id="058de-137">无</span><span class="sxs-lookup"><span data-stu-id="058de-137">none</span></span>|  
  
## <a name="subscription-status-values"></a><span data-ttu-id="058de-138">订阅状态值</span><span class="sxs-lookup"><span data-stu-id="058de-138">Subscription Status Values</span></span>  
 <span data-ttu-id="058de-139">下列表按优先级顺序显示了订阅状态值及其对应的图标。</span><span class="sxs-lookup"><span data-stu-id="058de-139">The following tables show subscription status values and their corresponding icons in priority order.</span></span> <span data-ttu-id="058de-140">一个订阅可以同时处于两种状态，如“即将过期/已过期” \*\*\*\* 和“正在重试失败的命令” \*\*\*\*；将显示最高优先级状态。</span><span class="sxs-lookup"><span data-stu-id="058de-140">It is possible for a subscription to be in two states at the same time, such as **Expiring soon/Expired** and **Retrying failed command**; the highest priority status is displayed.</span></span>  
  
 <span data-ttu-id="058de-141">状态值“‘严重’状态下的性能” \*\*\*\*、“即将过期/已过期” \*\*\*\* 和“未初始化” \*\*\*\* 都是警告。</span><span class="sxs-lookup"><span data-stu-id="058de-141">The status values **Performance critical**, **Expiring soon/Expired**, and **Uninitialized** are warnings.</span></span> <span data-ttu-id="058de-142">显示警告时，复制监视器还显示是否有代理在运行。</span><span class="sxs-lookup"><span data-stu-id="058de-142">When a warning is displayed, Replication Monitor also displays whether an agent is running.</span></span> <span data-ttu-id="058de-143">例如，状态可能为 **“正在运行，‘严重’状态下的性能”**。</span><span class="sxs-lookup"><span data-stu-id="058de-143">For example, the status could be **Running, Performance critical**.</span></span>  
  
### <a name="transactional-subscriptions"></a><span data-ttu-id="058de-144">事务订阅</span><span class="sxs-lookup"><span data-stu-id="058de-144">Transactional subscriptions</span></span>  
  
|<span data-ttu-id="058de-145">状态</span><span class="sxs-lookup"><span data-stu-id="058de-145">Status</span></span>|<span data-ttu-id="058de-146">图标</span><span class="sxs-lookup"><span data-stu-id="058de-146">Icon</span></span>|  
|------------|----------|  
|<span data-ttu-id="058de-147">错误</span><span class="sxs-lookup"><span data-stu-id="058de-147">Error</span></span>|<span data-ttu-id="058de-148">![UI 图标：错误](../media/repl-icon-error.gif "UI 图标：错误")</span><span class="sxs-lookup"><span data-stu-id="058de-148">![UI icon: error](../media/repl-icon-error.gif "UI icon: error")</span></span>|  
|<span data-ttu-id="058de-149">“严重”状态下的性能</span><span class="sxs-lookup"><span data-stu-id="058de-149">Performance critical</span></span>|<span data-ttu-id="058de-150">![UI 图标：警告](../media/repl-icon-warn.gif "UI 图标：警告")</span><span class="sxs-lookup"><span data-stu-id="058de-150">![UI icon: warning](../media/repl-icon-warn.gif "UI icon: warning")</span></span>|  
|<span data-ttu-id="058de-151">即将过期/已过期</span><span class="sxs-lookup"><span data-stu-id="058de-151">Expiring soon/Expired</span></span>|<span data-ttu-id="058de-152">![UI 图标：警告](../media/repl-icon-warn.gif "UI 图标：警告")</span><span class="sxs-lookup"><span data-stu-id="058de-152">![UI icon: warning](../media/repl-icon-warn.gif "UI icon: warning")</span></span>|  
|<span data-ttu-id="058de-153">未初始化的订阅</span><span class="sxs-lookup"><span data-stu-id="058de-153">Uninitialized subscription</span></span>|<span data-ttu-id="058de-154">![UI 图标：警告](../media/repl-icon-warn.gif "UI 图标：警告")</span><span class="sxs-lookup"><span data-stu-id="058de-154">![UI icon: warning](../media/repl-icon-warn.gif "UI icon: warning")</span></span>|  
|<span data-ttu-id="058de-155">正在重试失败的命令</span><span class="sxs-lookup"><span data-stu-id="058de-155">Retrying failed command</span></span>|<span data-ttu-id="058de-156">![UI 图标：复制代理重试](../media/repl-icon-retry.gif "UI 图标：复制代理重试")</span><span class="sxs-lookup"><span data-stu-id="058de-156">![UI icon: replication agent retry](../media/repl-icon-retry.gif "UI icon: replication agent retry")</span></span>|  
|<span data-ttu-id="058de-157">未运行</span><span class="sxs-lookup"><span data-stu-id="058de-157">Not running</span></span>|<span data-ttu-id="058de-158">![UI 图标：复制代理已停止](../media/repl-icon-stopped.gif "UI 图标：复制代理已停止")</span><span class="sxs-lookup"><span data-stu-id="058de-158">![UI icon: replication agent stopped](../media/repl-icon-stopped.gif "UI icon: replication agent stopped")</span></span>|  
|<span data-ttu-id="058de-159">正在运行</span><span class="sxs-lookup"><span data-stu-id="058de-159">Running</span></span>|<span data-ttu-id="058de-160">![UI 图标：复制代理正在运行](../media/repl-icon-running.gif "UI 图标：复制代理正在运行")</span><span class="sxs-lookup"><span data-stu-id="058de-160">![UI icon: replication agent running](../media/repl-icon-running.gif "UI icon: replication agent running")</span></span>|  
  
### <a name="merge-subscriptions"></a><span data-ttu-id="058de-161">合并订阅</span><span class="sxs-lookup"><span data-stu-id="058de-161">Merge subscriptions</span></span>  
  
|<span data-ttu-id="058de-162">状态</span><span class="sxs-lookup"><span data-stu-id="058de-162">Status</span></span>|<span data-ttu-id="058de-163">图标</span><span class="sxs-lookup"><span data-stu-id="058de-163">Icon</span></span>|  
|------------|----------|  
|<span data-ttu-id="058de-164">错误</span><span class="sxs-lookup"><span data-stu-id="058de-164">Error</span></span>|<span data-ttu-id="058de-165">![UI 图标：错误](../media/repl-icon-error.gif "UI 图标：错误")</span><span class="sxs-lookup"><span data-stu-id="058de-165">![UI icon: error](../media/repl-icon-error.gif "UI icon: error")</span></span>|  
|<span data-ttu-id="058de-166">“严重”状态下的性能</span><span class="sxs-lookup"><span data-stu-id="058de-166">Performance critical</span></span>|<span data-ttu-id="058de-167">![UI 图标：警告](../media/repl-icon-warn.gif "UI 图标：警告")</span><span class="sxs-lookup"><span data-stu-id="058de-167">![UI icon: warning](../media/repl-icon-warn.gif "UI icon: warning")</span></span>|  
|<span data-ttu-id="058de-168">长时间运行的合并</span><span class="sxs-lookup"><span data-stu-id="058de-168">Long-running merge</span></span>|<span data-ttu-id="058de-169">![UI 图标：警告](../media/repl-icon-warn.gif "UI 图标：警告")</span><span class="sxs-lookup"><span data-stu-id="058de-169">![UI icon: warning](../media/repl-icon-warn.gif "UI icon: warning")</span></span>|  
|<span data-ttu-id="058de-170">即将过期/已过期</span><span class="sxs-lookup"><span data-stu-id="058de-170">Expiring soon/Expired</span></span>|<span data-ttu-id="058de-171">![UI 图标：警告](../media/repl-icon-warn.gif "UI 图标：警告")</span><span class="sxs-lookup"><span data-stu-id="058de-171">![UI icon: warning](../media/repl-icon-warn.gif "UI icon: warning")</span></span>|  
|<span data-ttu-id="058de-172">未初始化的订阅</span><span class="sxs-lookup"><span data-stu-id="058de-172">Uninitialized subscription</span></span>|<span data-ttu-id="058de-173">![UI 图标：警告](../media/repl-icon-warn.gif "UI 图标：警告")</span><span class="sxs-lookup"><span data-stu-id="058de-173">![UI icon: warning](../media/repl-icon-warn.gif "UI icon: warning")</span></span>|  
|<span data-ttu-id="058de-174">正在重试失败的命令</span><span class="sxs-lookup"><span data-stu-id="058de-174">Retrying failed command</span></span>|<span data-ttu-id="058de-175">![UI 图标：复制代理重试](../media/repl-icon-retry.gif "UI 图标：复制代理重试")</span><span class="sxs-lookup"><span data-stu-id="058de-175">![UI icon: replication agent retry](../media/repl-icon-retry.gif "UI icon: replication agent retry")</span></span>|  
|<span data-ttu-id="058de-176">正在同步</span><span class="sxs-lookup"><span data-stu-id="058de-176">Synchronizing</span></span>|<span data-ttu-id="058de-177">![UI 图标：复制代理正在运行](../media/repl-icon-running.gif "UI 图标：复制代理正在运行")</span><span class="sxs-lookup"><span data-stu-id="058de-177">![UI icon: replication agent running](../media/repl-icon-running.gif "UI icon: replication agent running")</span></span>|  
|<span data-ttu-id="058de-178">未同步</span><span class="sxs-lookup"><span data-stu-id="058de-178">Not Synchronizing</span></span>|<span data-ttu-id="058de-179">![UI 图标：复制代理已停止](../media/repl-icon-stopped.gif "UI 图标：复制代理已停止")</span><span class="sxs-lookup"><span data-stu-id="058de-179">![UI icon: replication agent stopped](../media/repl-icon-stopped.gif "UI icon: replication agent stopped")</span></span>|  
  
### <a name="snapshot-subscriptions"></a><span data-ttu-id="058de-180">快照订阅</span><span class="sxs-lookup"><span data-stu-id="058de-180">Snapshot subscriptions</span></span>  
  
|<span data-ttu-id="058de-181">状态</span><span class="sxs-lookup"><span data-stu-id="058de-181">Status</span></span>|<span data-ttu-id="058de-182">图标</span><span class="sxs-lookup"><span data-stu-id="058de-182">Icon</span></span>|  
|------------|----------|  
|<span data-ttu-id="058de-183">错误</span><span class="sxs-lookup"><span data-stu-id="058de-183">Error</span></span>|<span data-ttu-id="058de-184">![UI 图标：错误](../media/repl-icon-error.gif "UI 图标：错误")</span><span class="sxs-lookup"><span data-stu-id="058de-184">![UI icon: error](../media/repl-icon-error.gif "UI icon: error")</span></span>|  
|<span data-ttu-id="058de-185">即将过期/已过期</span><span class="sxs-lookup"><span data-stu-id="058de-185">Expiring soon/Expired</span></span>|<span data-ttu-id="058de-186">![UI 图标：警告](../media/repl-icon-warn.gif "UI 图标：警告")</span><span class="sxs-lookup"><span data-stu-id="058de-186">![UI icon: warning](../media/repl-icon-warn.gif "UI icon: warning")</span></span>|  
|<span data-ttu-id="058de-187">未初始化的订阅</span><span class="sxs-lookup"><span data-stu-id="058de-187">Uninitialized subscription</span></span>|<span data-ttu-id="058de-188">![UI 图标：警告](../media/repl-icon-warn.gif "UI 图标：警告")</span><span class="sxs-lookup"><span data-stu-id="058de-188">![UI icon: warning](../media/repl-icon-warn.gif "UI icon: warning")</span></span>|  
|<span data-ttu-id="058de-189">正在重试失败的命令</span><span class="sxs-lookup"><span data-stu-id="058de-189">Retrying failed command</span></span>|<span data-ttu-id="058de-190">![UI 图标：复制代理重试](../media/repl-icon-retry.gif "UI 图标：复制代理重试")</span><span class="sxs-lookup"><span data-stu-id="058de-190">![UI icon: replication agent retry](../media/repl-icon-retry.gif "UI icon: replication agent retry")</span></span>|  
|<span data-ttu-id="058de-191">正在同步</span><span class="sxs-lookup"><span data-stu-id="058de-191">Synchronizing</span></span>|<span data-ttu-id="058de-192">![UI 图标：复制代理正在运行](../media/repl-icon-running.gif "UI 图标：复制代理正在运行")</span><span class="sxs-lookup"><span data-stu-id="058de-192">![UI icon: replication agent running](../media/repl-icon-running.gif "UI icon: replication agent running")</span></span>|  
|<span data-ttu-id="058de-193">未同步</span><span class="sxs-lookup"><span data-stu-id="058de-193">Not Synchronizing</span></span>|<span data-ttu-id="058de-194">![UI 图标：复制代理已停止](../media/repl-icon-stopped.gif "UI 图标：复制代理已停止")</span><span class="sxs-lookup"><span data-stu-id="058de-194">![UI icon: replication agent stopped](../media/repl-icon-stopped.gif "UI icon: replication agent stopped")</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="058de-195">另请参阅</span><span class="sxs-lookup"><span data-stu-id="058de-195">See Also</span></span>  
 [<span data-ttu-id="058de-196">监视复制</span><span class="sxs-lookup"><span data-stu-id="058de-196">Monitoring Replication</span></span>](../monitoring-replication.md)  
  
  
