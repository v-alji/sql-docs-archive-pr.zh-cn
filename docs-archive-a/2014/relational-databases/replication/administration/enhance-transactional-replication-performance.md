---
title: 增强事务复制性能 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- publications [SQL Server replication], design and performance
- performance [SQL Server replication], transactional replication
- designing databases [SQL Server], replication performance
- performance [SQL Server replication], snapshot replication
- snapshot replication [SQL Server], performance
- subscriptions [SQL Server replication], performance considerations
- agents [SQL Server replication], performance
- Distribution Agent, performance
- transactional replication, performance
- Log Reader Agent, performance
ms.assetid: 67084a67-43ff-4065-987a-3b16d1841565
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: fe802796b129ff9bdb50e5dea13e1fe98beee269
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693774"
---
# <a name="enhance-transactional-replication-performance"></a><span data-ttu-id="21d97-102">增强事务复制性能</span><span class="sxs-lookup"><span data-stu-id="21d97-102">Enhance Transactional Replication Performance</span></span>
  <span data-ttu-id="21d97-103">在考虑 [增强常规复制性能](enhance-general-replication-performance.md)中介绍的常规性能提示后，还需要考虑特定于事务复制的其他几个方面。</span><span class="sxs-lookup"><span data-stu-id="21d97-103">After considering the general performance tips described in [Enhancing General Replication Performance](enhance-general-replication-performance.md), consider these additional areas specific to transactional replication.</span></span>  
  
## <a name="database-design"></a><span data-ttu-id="21d97-104">数据库设计</span><span class="sxs-lookup"><span data-stu-id="21d97-104">Database Design</span></span>  
  
-   <span data-ttu-id="21d97-105">在应用程序设计中，最大限度地减小事务大小。</span><span class="sxs-lookup"><span data-stu-id="21d97-105">Minimize transaction size in your application design.</span></span>  
  
     <span data-ttu-id="21d97-106">默认情况下，事务复制根据事务边界传播更改。</span><span class="sxs-lookup"><span data-stu-id="21d97-106">By default, transactional replication propagates changes according to transaction boundaries.</span></span> <span data-ttu-id="21d97-107">如果事务越小，则分发代理因网络问题而重新发送事务的可能性就越小。</span><span class="sxs-lookup"><span data-stu-id="21d97-107">If transactions are smaller, it is less likely that the Distribution Agent will have to resend a transaction due to network issues.</span></span> <span data-ttu-id="21d97-108">如果重新发送事务需要代理，则发送的数据量会较小。</span><span class="sxs-lookup"><span data-stu-id="21d97-108">If the agent is required to resend a transaction, the amount of data sent is smaller.</span></span>  
  
## <a name="distributor-configuration"></a><span data-ttu-id="21d97-109">分发服务器配置</span><span class="sxs-lookup"><span data-stu-id="21d97-109">Distributor Configuration</span></span>  
  
-   <span data-ttu-id="21d97-110">在专用服务器上配置分发服务器。</span><span class="sxs-lookup"><span data-stu-id="21d97-110">Configure the Distributor on a dedicated server.</span></span>  
  
     <span data-ttu-id="21d97-111">通过配置远程分发服务器可以减少发布服务器的处理开销。</span><span class="sxs-lookup"><span data-stu-id="21d97-111">You can reduce processing overhead on the Publisher by configuring a remote Distributor.</span></span> <span data-ttu-id="21d97-112">有关详细信息，请参阅 [Configure Distribution](../configure-distribution.md)。</span><span class="sxs-lookup"><span data-stu-id="21d97-112">For more information, see [Configure Distribution](../configure-distribution.md).</span></span>  
  
-   <span data-ttu-id="21d97-113">适当调整分发数据库的大小。</span><span class="sxs-lookup"><span data-stu-id="21d97-113">Size the distribution database appropriately.</span></span>  
  
     <span data-ttu-id="21d97-114">在系统承受典型负载的情况下对复制进行测试，以确定存储命令需要多少空间。</span><span class="sxs-lookup"><span data-stu-id="21d97-114">Test replication with a typical load for your system to determine how much space is required to store commands.</span></span> <span data-ttu-id="21d97-115">确保数据库足以存储命令，而无需频繁地自动增大。</span><span class="sxs-lookup"><span data-stu-id="21d97-115">Ensure the database is large enough to store commands without having to auto-grow frequently.</span></span> <span data-ttu-id="21d97-116">有关更改数据库大小的详细信息，请参阅 [ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="21d97-116">For more information about changing the size of a database, see [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
## <a name="publication-design"></a><span data-ttu-id="21d97-117">发布设计</span><span class="sxs-lookup"><span data-stu-id="21d97-117">Publication Design</span></span>  
  
-   <span data-ttu-id="21d97-118">在对已发布的表进行批更新时，复制存储过程执行。</span><span class="sxs-lookup"><span data-stu-id="21d97-118">Replicate stored procedure execution when making batch updates to published tables.</span></span>  
  
     <span data-ttu-id="21d97-119">如果所做的批处理更新有时会影响订阅服务器上的大量行，则应考虑使用存储过程更新已发布的表，并发布存储过程的执行。</span><span class="sxs-lookup"><span data-stu-id="21d97-119">If you have batch updates that occasionally affect a large number of rows at the Subscriber, you should consider updating the published table using a stored procedure and publish the execution of the stored procedure.</span></span> <span data-ttu-id="21d97-120">分发代理不是为每个受影响的行都发送一个更新或删除，而是在订阅服务器上用相同的参数值执行相同的过程。</span><span class="sxs-lookup"><span data-stu-id="21d97-120">Instead of sending an update or delete for every row affected, the Distribution Agent executes the same procedure at the Subscriber with the same parameter values.</span></span> <span data-ttu-id="21d97-121">有关详细信息，请参阅 [Publishing Stored Procedure Execution in Transactional Replication](../transactional/publishing-stored-procedure-execution-in-transactional-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="21d97-121">For more information, see [Publishing Stored Procedure Execution in Transactional Replication](../transactional/publishing-stored-procedure-execution-in-transactional-replication.md).</span></span>  
  
-   <span data-ttu-id="21d97-122">将项目分布在多个发布上。</span><span class="sxs-lookup"><span data-stu-id="21d97-122">Spread articles across multiple publications.</span></span>  
  
     <span data-ttu-id="21d97-123">如果不能使用 **-SubscriptionStreams** 参数（将在本主题的后面部分进行介绍），请考虑创建多个发布。</span><span class="sxs-lookup"><span data-stu-id="21d97-123">If you cannot use the **-SubscriptionStreams** parameter (described later in this topic), consider creating multiple publications.</span></span> <span data-ttu-id="21d97-124">将项目分布在这些发布上使复制可以并行地将更改应用到订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="21d97-124">Spreading articles across these publications allows replication to apply changes in parallel to Subscribers.</span></span>  
  
## <a name="subscription-considerations"></a><span data-ttu-id="21d97-125">订阅注意事项</span><span class="sxs-lookup"><span data-stu-id="21d97-125">Subscription Considerations</span></span>  
  
-   <span data-ttu-id="21d97-126">如果在相同的发布服务器中拥有多个发布（这是新建发布向导中的默认情况），则使用独立代理而非共享代理。</span><span class="sxs-lookup"><span data-stu-id="21d97-126">Use independent agents rather than shared agents if you have multiple publications on the same Publisher (this is the default for the New Publication Wizard).</span></span>  
  
-   <span data-ttu-id="21d97-127">连续运行而不是按非常频繁的计划运行代理。</span><span class="sxs-lookup"><span data-stu-id="21d97-127">Run agents continuously instead of on very frequent schedules.</span></span>  
  
     <span data-ttu-id="21d97-128">将代理设置为连续运行而不是创建频繁的计划（如每分钟）会提高复制性能，因为代理不必启动和停止。</span><span class="sxs-lookup"><span data-stu-id="21d97-128">Setting the agents to run continuously rather than creating frequent schedules (such as every minute) improves replication performance, because the agent does not have to start and stop.</span></span> <span data-ttu-id="21d97-129">将分发代理设置为连续运行后，以低滞后时间将更改传播到拓扑中连接的其他服务器。</span><span class="sxs-lookup"><span data-stu-id="21d97-129">When you set the Distribution Agent to run continuously, changes are propagated with low latency to the other servers that are connected in the topology.</span></span> <span data-ttu-id="21d97-130">有关详细信息，请参阅：</span><span class="sxs-lookup"><span data-stu-id="21d97-130">For more information, see:</span></span>  
  
    -   [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]<span data-ttu-id="21d97-131">：[指定同步计划](../specify-synchronization-schedules.md)</span><span class="sxs-lookup"><span data-stu-id="21d97-131">: [Specify Synchronization Schedules](../specify-synchronization-schedules.md)</span></span>  
  
## <a name="distribution-agent-and-log-reader-agent-parameters"></a><span data-ttu-id="21d97-132">分发代理和日志读取器代理参数</span><span class="sxs-lookup"><span data-stu-id="21d97-132">Distribution Agent and Log Reader Agent Parameters</span></span>  
  
-   <span data-ttu-id="21d97-133">若要解决意外、一次性瓶颈，请使用 **-MaxCmdsInTran**参数进行日志读取器代理。</span><span class="sxs-lookup"><span data-stu-id="21d97-133">To resolve accidental, one-time bottlenecks use the **-MaxCmdsInTran** parameter for the Log Reader Agent.</span></span>  
  
     <span data-ttu-id="21d97-134">**-MaxCmdsInTran**参数指定日志读取器向分发数据库写入命令时分组到事务中的语句的最大数目。</span><span class="sxs-lookup"><span data-stu-id="21d97-134">The **-MaxCmdsInTran** parameter specifies the maximum number of statements grouped into a transaction as the Log Reader writes commands to the distribution database.</span></span> <span data-ttu-id="21d97-135">使用此参数能够使日志读取器代理和分发代理在订阅服务器上应用命令时将发布服务器上的大事务（由许多命令组成）分成若干个较小的事务。</span><span class="sxs-lookup"><span data-stu-id="21d97-135">Using this parameter allows the Log Reader Agent and Distribution Agent to divide large transactions (consisting of many commands) at the Publisher into several smaller transactions when applying commands at the Subscriber.</span></span> <span data-ttu-id="21d97-136">指定此参数可以减少分发服务器的争用问题并缩短发布服务器与订阅服务器之间的滞后时间。</span><span class="sxs-lookup"><span data-stu-id="21d97-136">Specifying this parameter can reduce contention at the Distributor and reduce latency between the Publisher and Subscriber.</span></span> <span data-ttu-id="21d97-137">由于初始事务是以较小的单元应用的，订阅服务器可以在初始事务结束之前访问一个较大的逻辑发布服务器事务的行，因而会破坏事务的原子性。</span><span class="sxs-lookup"><span data-stu-id="21d97-137">Because the original transaction is applied in smaller units, the Subscriber can access rows of a large logical Publisher transaction prior to the end of the original transaction, breaking strict transactional atomicity.</span></span> <span data-ttu-id="21d97-138">默认值为 0 ，这将保持发布服务器的事务边界。</span><span class="sxs-lookup"><span data-stu-id="21d97-138">The default is **0**, which preserves the transaction boundaries of the Publisher.</span></span> <span data-ttu-id="21d97-139">此参数不适用于 Oracle 发布服务器。</span><span class="sxs-lookup"><span data-stu-id="21d97-139">This parameter does not apply to Oracle Publishers.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="21d97-140">`MaxCmdsInTran` 并非始终开启。</span><span class="sxs-lookup"><span data-stu-id="21d97-140">`MaxCmdsInTran` was not designed to be always turned on.</span></span> <span data-ttu-id="21d97-141">其之所以存在，是为了解决某人在单个事务中意外执行了大量 DML 操作（在整个事务进入分发数据库并持有锁之前，导致命令分发延迟等）的问题。</span><span class="sxs-lookup"><span data-stu-id="21d97-141">It exists to work around cases where someone accidentally performed a large number of DML operations in a single transaction (causing delay in distribution of commands until the entire transaction is in distribution database, locks being held, etc.).</span></span> <span data-ttu-id="21d97-142">如果您经常遇到这种情况，则应审查应用程序并找到减少事务大小的方法。</span><span class="sxs-lookup"><span data-stu-id="21d97-142">If you routinely fall into this situation, you should review your applications and find ways to reduce the transaction size.</span></span>  
  
-   <span data-ttu-id="21d97-143">对分发代理使用 **-SubscriptionStreams**参数。</span><span class="sxs-lookup"><span data-stu-id="21d97-143">Use the **-SubscriptionStreams** parameter for the Distribution Agent.</span></span>  
  
     <span data-ttu-id="21d97-144">**-SubscriptionStreams**参数可以显著提高聚合复制吞吐量。</span><span class="sxs-lookup"><span data-stu-id="21d97-144">The **-SubscriptionStreams** parameter can greatly improve aggregate replication throughput.</span></span> <span data-ttu-id="21d97-145">它使到一台订阅服务器的多个连接可以并行应用批量更改，同时在使用单线程时保持多个事务特征的存在。</span><span class="sxs-lookup"><span data-stu-id="21d97-145">It allows multiple connections to a Subscriber to apply batches of changes in parallel, while maintaining many of the transactional characteristics present when using a single thread.</span></span> <span data-ttu-id="21d97-146">如果有一个连接无法执行或提交，则所有连接将中止当前批处理，而且代理将用单独的流重试失败的批处理。</span><span class="sxs-lookup"><span data-stu-id="21d97-146">If one of the connections fails to execute or commit, all connections will abort the current batch, and the agent will use a single stream to retry the failed batches.</span></span> <span data-ttu-id="21d97-147">在重试阶段完成之前，订阅服务器上会存在临时事务不一致。</span><span class="sxs-lookup"><span data-stu-id="21d97-147">Before this retry phase completes, there can be temporary transactional inconsistencies at the Subscriber.</span></span> <span data-ttu-id="21d97-148">失败的批处理成功提交后，订阅服务器将恢复到事务一致状态。</span><span class="sxs-lookup"><span data-stu-id="21d97-148">After the failed batches are successfully committed, the Subscriber is brought back to a state of transactional consistency.</span></span>  
  
     <span data-ttu-id="21d97-149">可以使用[sp_addsubscription &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql)的\*\* \@ subscriptionstreams\*\*指定此代理参数的值。</span><span class="sxs-lookup"><span data-stu-id="21d97-149">A value for this agent parameter can be specified using the **\@subscriptionstreams** of [sp_addsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql).</span></span>  
  
-   <span data-ttu-id="21d97-150">增大日志读取器代理的 **-ReadBatchSize** 参数的值。</span><span class="sxs-lookup"><span data-stu-id="21d97-150">Increase the value of the **-ReadBatchSize** parameter for the Log Reader Agent.</span></span>  
  
     <span data-ttu-id="21d97-151">日志读取器代理和分发代理支持事务读取和提交操作的批大小。</span><span class="sxs-lookup"><span data-stu-id="21d97-151">The Log Reader Agent and Distribution Agent support batch sizes for transaction read and commit operations.</span></span> <span data-ttu-id="21d97-152">批大小的默认值为 500 个事务。</span><span class="sxs-lookup"><span data-stu-id="21d97-152">Batch sizes default to 500 transactions.</span></span> <span data-ttu-id="21d97-153">日志读取器代理从日志中读取特定数量的事务，而不管这些事务是否标记为复制。</span><span class="sxs-lookup"><span data-stu-id="21d97-153">The Log Reader Agent reads the specific number of transactions from the log, whether or not they are marked for replication.</span></span> <span data-ttu-id="21d97-154">将大量事务写入发布数据库，而其中只有一小部分标记为复制时，则应使用 **-ReadBatchSize** 参数增加日志读取器代理的读取批大小。</span><span class="sxs-lookup"><span data-stu-id="21d97-154">When a large number of transactions is written to a publication database, but only a small subset of those are marked for replication, you should use the **-ReadBatchSize** parameter to increase the read batch size of the Log Reader Agent.</span></span> <span data-ttu-id="21d97-155">此参数不适用于 Oracle 发布服务器。</span><span class="sxs-lookup"><span data-stu-id="21d97-155">This parameter does not apply to Oracle Publishers.</span></span>  
  
-   <span data-ttu-id="21d97-156">增大分发代理的 **-CommitBatchSize** 参数的值。</span><span class="sxs-lookup"><span data-stu-id="21d97-156">Increase the value of the **-CommitBatchSize** parameter for the Distribution Agent.</span></span>  
  
     <span data-ttu-id="21d97-157">提交一组事务的开销是固定的；通过不经常提交大量事务，就可以将开销分散在大量数据上。</span><span class="sxs-lookup"><span data-stu-id="21d97-157">Committing a set of transactions has a fixed overhead; by committing a larger number of transactions less frequently, the overhead is spread across a larger volume of data.</span></span> <span data-ttu-id="21d97-158">但是，增大此参数的优势因应用更改的开销由其他因素（例如包含日志的最大磁盘 I/O）限制而降低。</span><span class="sxs-lookup"><span data-stu-id="21d97-158">However, the benefit of increasing this parameter drops off as the cost of applying changes is gated by other factors, such as the maximum I/O of the disk that contains the log.</span></span> <span data-ttu-id="21d97-159">另外，需要考虑以下权衡问题：必须回滚任何导致分发代理重新开始的失败并重新应用大量事务。</span><span class="sxs-lookup"><span data-stu-id="21d97-159">Additionally, there is a trade off to be considered: any failure that causes the Distribution Agent to start over must rollback and reapply a larger number of transactions.</span></span> <span data-ttu-id="21d97-160">对于不可靠的网络，越小的值导致失败的几率越小，如果导致失败，将回滚并重新应用较少量事务。</span><span class="sxs-lookup"><span data-stu-id="21d97-160">For unreliable networks, a lower value can result in less failures and a smaller number of transactions to rollback and reapply if a failure occurs.</span></span>  
  
-   <span data-ttu-id="21d97-161">减小日志读取器代理的 **-PollingInterval** 参数的值。</span><span class="sxs-lookup"><span data-stu-id="21d97-161">Decrease the value of the **-PollingInterval** parameter for the Log Reader Agent.</span></span>  
  
     <span data-ttu-id="21d97-162">**-PollingInterval** 参数指定为要复制的事务查询已发布数据库的事务日志的频率。</span><span class="sxs-lookup"><span data-stu-id="21d97-162">The **-PollingInterval** parameter specifies how often the transaction log of a published database is queried for transactions to replicate.</span></span> <span data-ttu-id="21d97-163">默认值为 5 秒。</span><span class="sxs-lookup"><span data-stu-id="21d97-163">The default is 5 seconds.</span></span> <span data-ttu-id="21d97-164">如果减小此值，日志的轮询将更加频繁，这会使事务从发布数据库传递到分发数据库的滞后时间较低。</span><span class="sxs-lookup"><span data-stu-id="21d97-164">If you decrease this value, the log is polled more frequently, which can result in lower latency for the delivery of transactions from the publication database to the distribution database.</span></span> <span data-ttu-id="21d97-165">但是，应该对较低滞后时间的需要和因频繁轮询导致的服务器上增加的负荷之间进行平衡。</span><span class="sxs-lookup"><span data-stu-id="21d97-165">However, you should balance the need for lower latency against the increased load on the server from polling more frequently.</span></span>  
  
 <span data-ttu-id="21d97-166">代理参数可以在代理配置文件和命令行中指定。</span><span class="sxs-lookup"><span data-stu-id="21d97-166">Agent parameters can be specified in agent profiles and on the command line.</span></span> <span data-ttu-id="21d97-167">有关详细信息，请参阅：</span><span class="sxs-lookup"><span data-stu-id="21d97-167">For more information, see:</span></span>  
  
-   [<span data-ttu-id="21d97-168">处理复制代理配置文件</span><span class="sxs-lookup"><span data-stu-id="21d97-168">Work with Replication Agent Profiles</span></span>](../agents/replication-agent-profiles.md)  
  
-   [<span data-ttu-id="21d97-169">查看和修改复制代理命令提示符参数 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="21d97-169">View and Modify Replication Agent Command Prompt Parameters &#40;SQL Server Management Studio&#41;</span></span>](../agents/view-and-modify-replication-agent-command-prompt-parameters.md)  
  
-   [<span data-ttu-id="21d97-170">Replication Agent Executables Concepts</span><span class="sxs-lookup"><span data-stu-id="21d97-170">Replication Agent Executables Concepts</span></span>](../concepts/replication-agent-executables-concepts.md)  
  
  
