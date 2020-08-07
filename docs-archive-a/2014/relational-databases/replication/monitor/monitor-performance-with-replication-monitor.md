---
title: 使用复制监视器监视性能 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- monitoring performance [SQL Server replication], Replication Monitor
- Log Reader Agent, monitoring
- Replication Monitor, performance
- Merge Agent, monitoring
- Queue Reader Agent, monitoring
- Snapshot Agent, monitoring
- Distribution Agent, monitoring
- monitoring performance [SQL Server replication]
ms.assetid: f212397d-1bfd-496b-a246-668952891d09
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d02cb17aae5dfe72a9660de62e516e61313ef03c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580130"
---
# <a name="monitor-performance-with-replication-monitor"></a><span data-ttu-id="6ac51-102">用复制监视器监视性能</span><span class="sxs-lookup"><span data-stu-id="6ac51-102">Monitor Performance with Replication Monitor</span></span>
  <span data-ttu-id="6ac51-103">使用 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 复制监视器，可以通过以下列方式监视事务复制和合并复制性能：</span><span class="sxs-lookup"><span data-stu-id="6ac51-103">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Replication Monitor allows you to monitor the performance of transactional replication and merge replication in the following ways:</span></span>  
  
-   <span data-ttu-id="6ac51-104">设置警告和阈值</span><span class="sxs-lookup"><span data-stu-id="6ac51-104">Setting warnings and thresholds</span></span>  
  
-   <span data-ttu-id="6ac51-105">查看性能度量值</span><span class="sxs-lookup"><span data-stu-id="6ac51-105">Viewing performance measurements</span></span>  
  
-   <span data-ttu-id="6ac51-106">使用跟踪令牌确定滞后时间（事务复制）</span><span class="sxs-lookup"><span data-stu-id="6ac51-106">Determining latency with tracer tokens (transactional replication)</span></span>  
  
-   <span data-ttu-id="6ac51-107">查看详细的同步统计信息（合并复制）</span><span class="sxs-lookup"><span data-stu-id="6ac51-107">Viewing detailed synchronization statistics (merge replication)</span></span>  
  
-   <span data-ttu-id="6ac51-108">查看事务和传递时间（事务复制）</span><span class="sxs-lookup"><span data-stu-id="6ac51-108">Viewing transactions and delivery time (transactional replication)</span></span>  
  
## <a name="set-warnings-and-thresholds"></a><span data-ttu-id="6ac51-109">设置警告和阈值</span><span class="sxs-lookup"><span data-stu-id="6ac51-109">Set Warnings and Thresholds</span></span>  
 <span data-ttu-id="6ac51-110">复制监视器允许为大量性能条件启用警告。</span><span class="sxs-lookup"><span data-stu-id="6ac51-110">Replication Monitor allows you to enable warnings for a number of performance conditions.</span></span> <span data-ttu-id="6ac51-111">启用警告时，需要指定阈值。</span><span class="sxs-lookup"><span data-stu-id="6ac51-111">When you enable a warning, you specify a threshold.</span></span> <span data-ttu-id="6ac51-112">达到或超过该阈值时，在与其进行同步的订阅和发布的 **“状态”** 列中将显示警告（除非需要显示更高优先级的问题）。</span><span class="sxs-lookup"><span data-stu-id="6ac51-112">When that threshold is met or exceeded, a warning is displayed in the **Status** column for the subscription and the publication with which it synchronizes (unless an issue with a higher priority needs to be displayed).</span></span> <span data-ttu-id="6ac51-113">除了在复制监视器中显示警告之外，达到阈值也可以触发警报。</span><span class="sxs-lookup"><span data-stu-id="6ac51-113">In addition to displaying a warning in Replication Monitor, reaching a threshold can also trigger an alert.</span></span> <span data-ttu-id="6ac51-114">可以为下列性能条件启用警告：</span><span class="sxs-lookup"><span data-stu-id="6ac51-114">You can enable warnings for the following performance conditions:</span></span>  
  
-   <span data-ttu-id="6ac51-115">超过指定的滞后时间（从事务在发布服务器上提交到相应的事务在订阅服务器上提交之间间隔的时间）。</span><span class="sxs-lookup"><span data-stu-id="6ac51-115">Exceeding the specified latency (the amount of time that elapses between a transaction being committed at the Publisher and the corresponding transaction being committed at the Subscriber).</span></span>  
  
     <span data-ttu-id="6ac51-116">这适用于事务复制。</span><span class="sxs-lookup"><span data-stu-id="6ac51-116">This applies to transactional replication.</span></span> <span data-ttu-id="6ac51-117">如果达到或超过指定的阈值，状态将显示为 **“‘严重’状态下的性能”** 。</span><span class="sxs-lookup"><span data-stu-id="6ac51-117">If the specified threshold is met or exceeded, the status is displayed as **Performance critical**.</span></span>  
  
-   <span data-ttu-id="6ac51-118">超出了指定的同步时间。</span><span class="sxs-lookup"><span data-stu-id="6ac51-118">Exceeding the specified synchronization time.</span></span>  
  
     <span data-ttu-id="6ac51-119">这适用于合并复制。</span><span class="sxs-lookup"><span data-stu-id="6ac51-119">This applies to merge replication.</span></span> <span data-ttu-id="6ac51-120">如果达到或超过指定的阈值，状态将显示为 **“长时间运行的合并”** 。</span><span class="sxs-lookup"><span data-stu-id="6ac51-120">If the specified threshold is met or exceeded, the status is displayed as **Long-running merge**.</span></span> <span data-ttu-id="6ac51-121">您可以为拨号连接和局域网 (LAN) 连接指定不同的阈值。</span><span class="sxs-lookup"><span data-stu-id="6ac51-121">You can specify different thresholds for dial-up and Local Area Network (LAN) connections.</span></span>  
  
-   <span data-ttu-id="6ac51-122">在给定时间内未处理完指定的行数。</span><span class="sxs-lookup"><span data-stu-id="6ac51-122">Falling short of processing the specified number of rows in a given amount of time.</span></span>  
  
     <span data-ttu-id="6ac51-123">这适用于合并复制。</span><span class="sxs-lookup"><span data-stu-id="6ac51-123">This applies to merge replication.</span></span> <span data-ttu-id="6ac51-124">如果达到或超过指定的阈值，状态将显示为 **“‘严重’状态下的性能”** 。</span><span class="sxs-lookup"><span data-stu-id="6ac51-124">If the specified threshold is met or exceeded, the status is displayed as **Performance critical**.</span></span> <span data-ttu-id="6ac51-125">您可以为拨号连接和 LAN 连接指定不同的阈值。</span><span class="sxs-lookup"><span data-stu-id="6ac51-125">You can specify different thresholds for dial-up and LAN connections.</span></span>  
  
 <span data-ttu-id="6ac51-126">有关详细信息，请参阅 [Set Thresholds and Warnings in Replication Monitor](set-thresholds-and-warnings-in-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="6ac51-126">For more information, see [Set Thresholds and Warnings in Replication Monitor](set-thresholds-and-warnings-in-replication-monitor.md).</span></span>  
  
## <a name="view-performance-measurements"></a><span data-ttu-id="6ac51-127">查看性能度量值</span><span class="sxs-lookup"><span data-stu-id="6ac51-127">View Performance Measurements</span></span>  
 <span data-ttu-id="6ac51-128">对于发布，复制监视器在 **“当前平均性能”** 和 **“当前最差的性能”** 列中显示事务复制和合并复制的性能质量值；对于订阅，复制监视器在 **“性能”** 列中显示这些值。</span><span class="sxs-lookup"><span data-stu-id="6ac51-128">Replication Monitor displays performance quality values for transactional replication and merge replication in the **Current Average Performance** and **Current Worst Performance** columns for publications and the **Performance** column for subscriptions.</span></span> <span data-ttu-id="6ac51-129">有效值为：</span><span class="sxs-lookup"><span data-stu-id="6ac51-129">The values are:</span></span>  
  
-   <span data-ttu-id="6ac51-130">很好</span><span class="sxs-lookup"><span data-stu-id="6ac51-130">Excellent</span></span>  
  
-   <span data-ttu-id="6ac51-131">好</span><span class="sxs-lookup"><span data-stu-id="6ac51-131">Good</span></span>  
  
-   <span data-ttu-id="6ac51-132">一般</span><span class="sxs-lookup"><span data-stu-id="6ac51-132">Fair</span></span>  
  
-   <span data-ttu-id="6ac51-133">较差</span><span class="sxs-lookup"><span data-stu-id="6ac51-133">Poor</span></span>  
  
-   <span data-ttu-id="6ac51-134">严重（仅适用于事务复制）</span><span class="sxs-lookup"><span data-stu-id="6ac51-134">Critical (transactional replication only)</span></span>  
  
 <span data-ttu-id="6ac51-135">这些值以下列方式确定：</span><span class="sxs-lookup"><span data-stu-id="6ac51-135">The values are determined in the following ways:</span></span>  
  
-   <span data-ttu-id="6ac51-136">对于事务复制，性能质量由滞后时间阈值确定。</span><span class="sxs-lookup"><span data-stu-id="6ac51-136">For transactional replication, performance quality is determined by the latency threshold.</span></span> <span data-ttu-id="6ac51-137">如果不设置阈值，则不显示任何值。</span><span class="sxs-lookup"><span data-stu-id="6ac51-137">If the threshold is not set, a value is not displayed.</span></span> <span data-ttu-id="6ac51-138">下表显示了阈值与性能质量值之间的相关性。</span><span class="sxs-lookup"><span data-stu-id="6ac51-138">The following table shows the correlation between the threshold and the performance quality value.</span></span> <span data-ttu-id="6ac51-139">例如，如果将阈值设置为 60 秒而实际滞后时间为 30 秒（即滞后时间为阈值的 50%），则性能质量值为“好”。</span><span class="sxs-lookup"><span data-stu-id="6ac51-139">For example, if the threshold is set to 60 seconds and the actual latency is 30 seconds, latency is 50% of the threshold, resulting in a value of Good.</span></span>  
  
    |<span data-ttu-id="6ac51-140">很好</span><span class="sxs-lookup"><span data-stu-id="6ac51-140">Excellent</span></span>|<span data-ttu-id="6ac51-141">好</span><span class="sxs-lookup"><span data-stu-id="6ac51-141">Good</span></span>|<span data-ttu-id="6ac51-142">一般</span><span class="sxs-lookup"><span data-stu-id="6ac51-142">Fair</span></span>|<span data-ttu-id="6ac51-143">较差</span><span class="sxs-lookup"><span data-stu-id="6ac51-143">Poor</span></span>|<span data-ttu-id="6ac51-144">严重</span><span class="sxs-lookup"><span data-stu-id="6ac51-144">Critical</span></span>|  
    |---------------|----------|----------|----------|--------------|  
    |<span data-ttu-id="6ac51-145">0 - 34%</span><span class="sxs-lookup"><span data-stu-id="6ac51-145">0 - 34%</span></span>|<span data-ttu-id="6ac51-146">35 - 59%</span><span class="sxs-lookup"><span data-stu-id="6ac51-146">35 - 59%</span></span>|<span data-ttu-id="6ac51-147">60 - 84%</span><span class="sxs-lookup"><span data-stu-id="6ac51-147">60 - 84%</span></span>|<span data-ttu-id="6ac51-148">85 - 99%</span><span class="sxs-lookup"><span data-stu-id="6ac51-148">85 - 99%</span></span>|<span data-ttu-id="6ac51-149">100% +</span><span class="sxs-lookup"><span data-stu-id="6ac51-149">100% +</span></span>|  
  
-   <span data-ttu-id="6ac51-150">对于合并复制，性能质量独立于任意一个阈值（行处理阈值确定是否在 **“状态”** 列中显示 **“‘严重’状态下的性能”** 值）。</span><span class="sxs-lookup"><span data-stu-id="6ac51-150">For merge replication, performance quality is independent of either threshold (the row processing threshold does determine if a value of **Performance critical** is displayed in the **Status** column).</span></span> <span data-ttu-id="6ac51-151">性能质量通过将具有相同连接类型（拨号或 LAN）的发布的单个订阅性能与订阅的平均历史性能进行比较来确定。</span><span class="sxs-lookup"><span data-stu-id="6ac51-151">Performance quality is determined by comparing individual subscription performance to the average historical performance of subscriptions to the publication that have the same connection type (dial-up or LAN).</span></span> <span data-ttu-id="6ac51-152">如果通过同一类型的连接进行了五次同步，且每次同步都进行了 50 处或更多的更改，则复制监视器将在此列中显示一个值。</span><span class="sxs-lookup"><span data-stu-id="6ac51-152">Replication Monitor displays a value after five synchronizations have occurred with 50 or more changes each over the same type of connection.</span></span> <span data-ttu-id="6ac51-153">如果包含 50 或 50 多次更改的同步不到五次，或最新同步中的更改少于 50 次，复制监视器将不显示值。</span><span class="sxs-lookup"><span data-stu-id="6ac51-153">If there have been less than five synchronizations with 50 or more changes or the most recent synchronization has less than 50 changes, Replication Monitor does not display a value.</span></span>  
  
     <span data-ttu-id="6ac51-154">下表显示了平均性能与性能质量值之间的相关性。</span><span class="sxs-lookup"><span data-stu-id="6ac51-154">The following table shows the correlation between the average performance and the performance quality value.</span></span> <span data-ttu-id="6ac51-155">例如，如果在 LAN 连接上有 10 个订阅服务器以每秒 100 行的平均速率进行同步，而其中一个订阅以每秒 125 行的速率进行同步（即该订阅服务器的同步性能的平均值为 125%），则性能质量值为“好”。</span><span class="sxs-lookup"><span data-stu-id="6ac51-155">For example, if ten Subscribers have synchronized over a LAN connection with an average rate of 100 rows per second, and one of the subscriptions then synchronizes at a rate of 125 rows per second, the performance for that Subscriber's synchronization is 125% of the average, resulting in a value of Good.</span></span>  
  
    |<span data-ttu-id="6ac51-156">很好</span><span class="sxs-lookup"><span data-stu-id="6ac51-156">Excellent</span></span>|<span data-ttu-id="6ac51-157">好</span><span class="sxs-lookup"><span data-stu-id="6ac51-157">Good</span></span>|<span data-ttu-id="6ac51-158">一般</span><span class="sxs-lookup"><span data-stu-id="6ac51-158">Fair</span></span>|<span data-ttu-id="6ac51-159">较差</span><span class="sxs-lookup"><span data-stu-id="6ac51-159">Poor</span></span>|  
    |---------------|----------|----------|----------|  
    |<span data-ttu-id="6ac51-160">151+%</span><span class="sxs-lookup"><span data-stu-id="6ac51-160">151+%</span></span>|<span data-ttu-id="6ac51-161">76 - 150%</span><span class="sxs-lookup"><span data-stu-id="6ac51-161">76 - 150%</span></span>|<span data-ttu-id="6ac51-162">26 - 75%</span><span class="sxs-lookup"><span data-stu-id="6ac51-162">26 - 75%</span></span>|<span data-ttu-id="6ac51-163">0 - 25%</span><span class="sxs-lookup"><span data-stu-id="6ac51-163">0 - 25%</span></span>|  
  
 <span data-ttu-id="6ac51-164">有关查看订阅信息的详细信息，请参阅[使用复制监视器查看信息和执行任务](view-information-and-perform-tasks-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="6ac51-164">For more information about viewing subscription information, see [View Information and Perform Tasks using Replication Monitor](view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
## <a name="determine-latency-with-tracer-tokens"></a><span data-ttu-id="6ac51-165">使用跟踪令牌确定滞后时间</span><span class="sxs-lookup"><span data-stu-id="6ac51-165">Determine Latency with Tracer Tokens</span></span>  
 <span data-ttu-id="6ac51-166">事务复制使您可以通过在发布数据库的事务日志中插入一个令牌（少量数据）并记录到达分发服务器和订阅服务器所用的时间，来测量系统的滞后时间。</span><span class="sxs-lookup"><span data-stu-id="6ac51-166">Transactional replication allows you to measure the latency in a system by inserting a token (a small amount of data) in the transaction log of the publication database and recording how long it takes to arrive at the Distributor and Subscribers.</span></span> <span data-ttu-id="6ac51-167">使用令牌还可以识别数据是否未到达分发服务器或订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="6ac51-167">The token also allows you to identify if data is not reaching the Distributor or Subscriber.</span></span> <span data-ttu-id="6ac51-168">有关详细信息，请参阅 [为事务复制测量滞后时间和验证连接](measure-latency-and-validate-connections-for-transactional-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="6ac51-168">For more information, see [Measure Latency and Validate Connections for Transactional Replication](measure-latency-and-validate-connections-for-transactional-replication.md).</span></span>  
  
## <a name="view-detailed-synchronization-performance-for-merge-replication"></a><span data-ttu-id="6ac51-169">查看合并复制的详细同步性能</span><span class="sxs-lookup"><span data-stu-id="6ac51-169">View Detailed Synchronization Performance for Merge Replication</span></span>  
 <span data-ttu-id="6ac51-170">对于合并复制，复制监视器会显示同步过程中所处理的每个项目的详细统计信息，其中包括每个处理阶段（如上载更改、下载更改等等）所用的时间。</span><span class="sxs-lookup"><span data-stu-id="6ac51-170">For merge replication, Replication Monitor displays detailed statistics for each article processed during synchronization, including the amount of time spent in each processing phase (uploading changes, downloading changes, and so on).</span></span> <span data-ttu-id="6ac51-171">它可帮助查明导致速度降低的特定表，是用来解决合并订阅性能问题的最佳途径。</span><span class="sxs-lookup"><span data-stu-id="6ac51-171">It can help pinpoint specific tables that are causing slow downs and is the best place to troubleshoot performance issues with merge subscriptions.</span></span> <span data-ttu-id="6ac51-172">有关查看详细统计信息详细信息，请参阅[使用复制监视器查看信息和执行任务](view-information-and-perform-tasks-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="6ac51-172">For more information on viewing detailed statistics, see [View Information and Perform Tasks using Replication Monitor](view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
## <a name="view-transactions-and-delivery-time-for-transactional-replication"></a><span data-ttu-id="6ac51-173">查看事务及事务复制的传递时间</span><span class="sxs-lookup"><span data-stu-id="6ac51-173">View Transactions and Delivery Time for Transactional Replication</span></span>  
 <span data-ttu-id="6ac51-174">对于事务复制，复制监视器显示分发数据库中尚未分发到订阅服务器的事务数以及分发这些事务的估计时间的信息。</span><span class="sxs-lookup"><span data-stu-id="6ac51-174">For transactional replication, Replication Monitor displays information about the number of transactions in the distribution database that have not yet been distributed to a Subscriber and the estimated time for distributing these transactions.</span></span> <span data-ttu-id="6ac51-175">有关详细信息，请参阅[使用复制监视器查看信息和执行任务](view-information-and-perform-tasks-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="6ac51-175">For more information, see [View Information and Perform Tasks using Replication Monitor](view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ac51-176">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6ac51-176">See Also</span></span>  
 <span data-ttu-id="6ac51-177">[监视复制](../monitoring-replication.md) </span><span class="sxs-lookup"><span data-stu-id="6ac51-177">[Monitoring Replication](../monitoring-replication.md) </span></span>  
 [<span data-ttu-id="6ac51-178">Set Thresholds and Warnings in Replication Monitor</span><span class="sxs-lookup"><span data-stu-id="6ac51-178">Set Thresholds and Warnings in Replication Monitor</span></span>](set-thresholds-and-warnings-in-replication-monitor.md)  
  
  
