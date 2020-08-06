---
title: 增强常规复制性能 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- publications [SQL Server replication], design and performance
- designing databases [SQL Server], replication performance
- Snapshot Agent, performance
- snapshots [SQL Server replication], performance considerations
- merge replication performance [SQL Server replication]
- snapshot replication [SQL Server], performance
- subscriptions [SQL Server replication], performance considerations
- agents [SQL Server replication], performance
- performance [SQL Server replication], general considerations
- transactional replication, performance
ms.assetid: 895b1ad7-ffb9-4a5c-bda6-e1dfbd56d9bf
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0a85519a947e7d5d03f324b71984d2ffb40bcefe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693777"
---
# <a name="enhance-general-replication-performance"></a><span data-ttu-id="4473b-102">增强常规复制性能</span><span class="sxs-lookup"><span data-stu-id="4473b-102">Enhance General Replication Performance</span></span>
  <span data-ttu-id="4473b-103">按照本主题介绍的指导原则，可以提高应用程序和网络上的所有复制类型的常规性能。</span><span class="sxs-lookup"><span data-stu-id="4473b-103">You can enhance the general performance for all types of replication in your application and on your network by using the guidelines described in this topic.</span></span>  
  
## <a name="server-and-network"></a><span data-ttu-id="4473b-104">服务器和网络</span><span class="sxs-lookup"><span data-stu-id="4473b-104">Server and Network</span></span>  
  
-   <span data-ttu-id="4473b-105">设置分配给 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)] 的最小和最大内存量。</span><span class="sxs-lookup"><span data-stu-id="4473b-105">Set the minimum and maximum amount of memory allocated to [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)].</span></span>  
  
     <span data-ttu-id="4473b-106">默认情况下， [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 根据可用的系统资源动态改变它的内存要求。</span><span class="sxs-lookup"><span data-stu-id="4473b-106">By default, the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] changes its memory requirements dynamically based on available system resources.</span></span> <span data-ttu-id="4473b-107">为避免在复制活动期间出现低内存可用性的问题，请使用 **min server memory** 选项设置最小可用内存。</span><span class="sxs-lookup"><span data-stu-id="4473b-107">To avoid low memory availability during replication activities, use the **min server memory** option to set the minimum available memory.</span></span> <span data-ttu-id="4473b-108">为避免将操作系统页写入磁盘以节省内存，也可以使用 **max server memory** 选项设置最大内存量。</span><span class="sxs-lookup"><span data-stu-id="4473b-108">To avoid having the operating system page to disc for memory, you can also set a maximum amount of memory with the **max server memory** option.</span></span> <span data-ttu-id="4473b-109">有关详细信息，请参阅[服务器内存服务器配置选项](../../../database-engine/configure-windows/server-memory-server-configuration-options.md)。</span><span class="sxs-lookup"><span data-stu-id="4473b-109">For more information, see [Server Memory Server Configuration Options](../../../database-engine/configure-windows/server-memory-server-configuration-options.md).</span></span>  
  
-   <span data-ttu-id="4473b-110">确保正确分配数据库数据文件和日志文件。</span><span class="sxs-lookup"><span data-stu-id="4473b-110">Ensure proper allocation of database data files and log files.</span></span> <span data-ttu-id="4473b-111">使用单独的磁盘驱动器存放复制过程中所涉及的所有数据库的事务日志。</span><span class="sxs-lookup"><span data-stu-id="4473b-111">Use a separate disk drive for the transaction log for all databases involved in replication.</span></span>  
  
     <span data-ttu-id="4473b-112">通过将日志文件与数据库存储在不同的磁盘驱动器上，可以减少写入事务所需的时间。</span><span class="sxs-lookup"><span data-stu-id="4473b-112">You can decrease the time it takes to write transactions by storing the log files on a disk drive different than the one used to store the database.</span></span> <span data-ttu-id="4473b-113">如果需要容错，可以使用独立冗余磁盘阵列 (RAID)-1 镜像该驱动器。</span><span class="sxs-lookup"><span data-stu-id="4473b-113">You can mirror that drive, using a Redundant Array of Inexpensive Disks (RAID)-1, if you require fault tolerance.</span></span> <span data-ttu-id="4473b-114">其他数据库文件使用 RAID 0 或 0+1（取决于容错需要）。</span><span class="sxs-lookup"><span data-stu-id="4473b-114">Use RAID 0 or 0+1 (depending on your need for fault tolerance) for other database files.</span></span> <span data-ttu-id="4473b-115">不管是否正在使用复制，这都是一个很好的做法。</span><span class="sxs-lookup"><span data-stu-id="4473b-115">This is a good practice regardless of whether or not replication is being used.</span></span>  
  
-   <span data-ttu-id="4473b-116">考虑增加复制所用的服务器的内存，尤其是分发服务器的内存。</span><span class="sxs-lookup"><span data-stu-id="4473b-116">Consider adding memory to servers used in replication, particularly the Distributor.</span></span>  
  
-   <span data-ttu-id="4473b-117">使用多处理器计算机。</span><span class="sxs-lookup"><span data-stu-id="4473b-117">Use multiprocessor computers.</span></span>  
  
     <span data-ttu-id="4473b-118">复制代理可以利用服务器中的附加处理器。</span><span class="sxs-lookup"><span data-stu-id="4473b-118">Replication agents can take advantage of additional processors on the server.</span></span> <span data-ttu-id="4473b-119">如果运行时 CPU 使用很高，请考虑安装更快的 CPU 或多个 CPU。</span><span class="sxs-lookup"><span data-stu-id="4473b-119">If you are running at high CPU usage, consider installing a faster CPU or multiple CPUs.</span></span>  
  
-   <span data-ttu-id="4473b-120">使用快速网络。</span><span class="sxs-lookup"><span data-stu-id="4473b-120">Use a fast network.</span></span>  
  
     <span data-ttu-id="4473b-121">网络可能是一个重要的性能瓶颈，尤其是对于事务复制而言。</span><span class="sxs-lookup"><span data-stu-id="4473b-121">The network can be a significant performance bottleneck, particularly for transactional replication.</span></span> <span data-ttu-id="4473b-122">通过使用每秒 100 兆位 (Mbps) 或更快的网络，可以显著提高将更改传播到订阅服务器的速度。</span><span class="sxs-lookup"><span data-stu-id="4473b-122">The propagation of changes to Subscribers can be significantly enhanced by using a fast network of 100 megabits per second (Mbps) or faster.</span></span> <span data-ttu-id="4473b-123">如果网络速度比较慢，请指定合适的网络设置和代理参数。</span><span class="sxs-lookup"><span data-stu-id="4473b-123">If the network is slow, specify appropriate network settings and agent parameters.</span></span>  
  
## <a name="database-design"></a><span data-ttu-id="4473b-124">数据库设计</span><span class="sxs-lookup"><span data-stu-id="4473b-124">Database Design</span></span>  
  
-   <span data-ttu-id="4473b-125">遵循数据库设计最佳实践。</span><span class="sxs-lookup"><span data-stu-id="4473b-125">Follow best practices for database design.</span></span>  
  
     <span data-ttu-id="4473b-126">复制数据库通常能够从性能优化中获得与非复制数据库一样的好处。</span><span class="sxs-lookup"><span data-stu-id="4473b-126">A replicated database generally benefits from the same performance optimizations as a non-replicated database.</span></span> <span data-ttu-id="4473b-127">但是，在订阅服务器中使用索引时应谨慎：应为订阅服务器中的主键列建立索引，但附加的索引可能影响插入、更新和删除操作的性能。</span><span class="sxs-lookup"><span data-stu-id="4473b-127">However, indexes should be used with caution at the Subscriber: the primary key column at the Subscriber should be indexed, but additional indexes can affect insert, update, and delete performance.</span></span>  
  
-   <span data-ttu-id="4473b-128">考虑设置 READ_COMMITTED_SNAPSHOT 数据库选项。</span><span class="sxs-lookup"><span data-stu-id="4473b-128">Consider setting the READ_COMMITTED_SNAPSHOT database option.</span></span>  
  
     <span data-ttu-id="4473b-129">为帮助减少用户活动与复制代理活动之间的争用，请为发布和订阅数据库设置下列选项：</span><span class="sxs-lookup"><span data-stu-id="4473b-129">To help reduce contention between user activity and replication agent activity, set this option for the publication and subscription databases:</span></span>  
  
    ```  
    ALTER DATABASE AdventureWorks  
    SET READ_COMMITTED_SNAPSHOT ON  
    ```  
  
     <span data-ttu-id="4473b-130">有关详细信息，请参阅 [ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="4473b-130">For more information, see [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
-   <span data-ttu-id="4473b-131">在触发器中慎用应用程序逻辑。</span><span class="sxs-lookup"><span data-stu-id="4473b-131">Be cautious with application logic in triggers.</span></span>  
  
     <span data-ttu-id="4473b-132">在订阅服务器中的用户定义触发器中使用业务逻辑可能会降低将更改复制到订阅服务器的速度：</span><span class="sxs-lookup"><span data-stu-id="4473b-132">Business logic in user-defined triggers at the Subscriber can slow down the replication of changes to the Subscriber:</span></span>  
  
    -   <span data-ttu-id="4473b-133">对于事务复制，将这种逻辑包含在用来应用复制命令的自定义存储过程中会更有效。</span><span class="sxs-lookup"><span data-stu-id="4473b-133">For transactional replication, it can be more efficient to include this logic in custom stored procedures used to apply the replicated commands.</span></span> <span data-ttu-id="4473b-134">有关详细信息，请参阅[指定如何传播事务项目的更改](../transactional/transactional-articles-specify-how-changes-are-propagated.md)。</span><span class="sxs-lookup"><span data-stu-id="4473b-134">For more information, see [Specify How Changes Are Propagated for Transactional Articles](../transactional/transactional-articles-specify-how-changes-are-propagated.md).</span></span>  
  
    -   <span data-ttu-id="4473b-135">对于合并复制，使用业务逻辑处理程序会更有效。</span><span class="sxs-lookup"><span data-stu-id="4473b-135">For merge replication, it can be more efficient to use business logic handlers.</span></span> <span data-ttu-id="4473b-136">有关详细信息，请参阅[合并同步期间执行业务逻辑](../merge/execute-business-logic-during-merge-synchronization.md)。</span><span class="sxs-lookup"><span data-stu-id="4473b-136">For more information, see [Execute Business Logic During Merge Synchronization](../merge/execute-business-logic-during-merge-synchronization.md).</span></span>  
  
     <span data-ttu-id="4473b-137">如果在为合并复制发布的表中使用触发器来维护引用完整性，请指定表的处理顺序，以减少合并代理所需的重试次数。</span><span class="sxs-lookup"><span data-stu-id="4473b-137">If you use triggers to maintain referential integrity in tables published for merge replication, specify the processing order of tables to reduce the number of retries required for the Merge Agent.</span></span> <span data-ttu-id="4473b-138">有关详细信息，请参阅[指定合并复制属性](../publish/specify-merge-replication-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="4473b-138">For more information, see [Specify Merge Replication properties](../publish/specify-merge-replication-properties.md).</span></span>  
  
-   <span data-ttu-id="4473b-139">限制使用大型对象 (LOB) 数据类型。</span><span class="sxs-lookup"><span data-stu-id="4473b-139">Limit the use of Large Object (LOB) data types.</span></span>  
  
     <span data-ttu-id="4473b-140">LOB 比其他列数据类型需要更多的存储空间和处理。</span><span class="sxs-lookup"><span data-stu-id="4473b-140">LOBs require more storage space and processing than other column data types.</span></span> <span data-ttu-id="4473b-141">除非应用程序需要，否则不要在项目中包括这些列。</span><span class="sxs-lookup"><span data-stu-id="4473b-141">Do not include these columns in articles unless necessary for your application.</span></span> <span data-ttu-id="4473b-142">不推荐使用数据类型 `text`、`ntext` 和 `image`。</span><span class="sxs-lookup"><span data-stu-id="4473b-142">The data types `text`, `ntext`, and `image` are deprecated.</span></span> <span data-ttu-id="4473b-143">如果确实要包括 LOB，建议分别使用数据类型 `varchar(max)`、`nvarchar(max)` 和 `varbinary(max)`。</span><span class="sxs-lookup"><span data-stu-id="4473b-143">If you do include LOBs, we recommend that you use the data types `varchar(max)`, `nvarchar(max)`, `varbinary(max)`, respectively.</span></span>  
  
     <span data-ttu-id="4473b-144">对于事务复制，请考虑使用名为“用于 OLEDB 流式处理的分发配置文件”  的分发代理配置文件。</span><span class="sxs-lookup"><span data-stu-id="4473b-144">For transactional replication, consider using the Distribution Agent profile called **Distribution Profile for OLEDB streaming**.</span></span> <span data-ttu-id="4473b-145">有关详细信息，请参阅 [Replication Agent Profiles](../agents/replication-agent-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="4473b-145">For more information, see [Replication Agent Profiles](../agents/replication-agent-profiles.md).</span></span>  
  
## <a name="publication-design"></a><span data-ttu-id="4473b-146">发布设计</span><span class="sxs-lookup"><span data-stu-id="4473b-146">Publication Design</span></span>  
  
-   <span data-ttu-id="4473b-147">仅发布所需的数据。</span><span class="sxs-lookup"><span data-stu-id="4473b-147">Publish only the data required.</span></span>  
  
     <span data-ttu-id="4473b-148">由于复制易于设置，所以有一种趋势是发布比实际需要量更多的数据。</span><span class="sxs-lookup"><span data-stu-id="4473b-148">Because replication is easy to set up, there is a tendency to publish more data than is actually required.</span></span> <span data-ttu-id="4473b-149">这会在分发数据库和快照文件中耗费额外资源，并降低所需数据的吞吐量。</span><span class="sxs-lookup"><span data-stu-id="4473b-149">This can consume additional resources within the distribution databases and snapshot files, and can lower the throughput for required data.</span></span> <span data-ttu-id="4473b-150">应避免发布不必要的表，并考虑不要过于频繁地更新发布。</span><span class="sxs-lookup"><span data-stu-id="4473b-150">Avoid publishing unnecessary tables and consider updating publications less frequently.</span></span>  
  
-   <span data-ttu-id="4473b-151">通过发布设计和应用程序行为最大限度地减少冲突。</span><span class="sxs-lookup"><span data-stu-id="4473b-151">Minimize conflicts through publication design and application behavior.</span></span>  
  
     <span data-ttu-id="4473b-152">以下类型的复制允许在订阅服务器中更改数据：合并复制、具有可更新订阅的事务复制和对等事务复制。</span><span class="sxs-lookup"><span data-stu-id="4473b-152">The following types of replication allow data to be changed at Subscribers: merge replication, transactional replication with updatable subscriptions, and peer-to-peer transactional replication.</span></span> <span data-ttu-id="4473b-153">如果在同步之间的多个节点上更新给定的行，合并复制以及具有可更新订阅的事务复制支持数据冲突。</span><span class="sxs-lookup"><span data-stu-id="4473b-153">Merge replication and transactional replication with updatable subscriptions support data conflicts if a given row is updated at more than one node between synchronizations.</span></span> <span data-ttu-id="4473b-154">对等复制不支持数据冲突，必须对数据更改进行分区。</span><span class="sxs-lookup"><span data-stu-id="4473b-154">Peer-to-peer replication does not support data conflicts; data changes must be partitioned.</span></span> <span data-ttu-id="4473b-155">不管使用哪种类型的复制，我们都建议您尽可能地对更改进行分区，因为这可以减少冲突检测和解决所需的处理操作。</span><span class="sxs-lookup"><span data-stu-id="4473b-155">Regardless of the type of replication used, we recommend that you partition changes whenever possible, because this reduces the processing required for conflict detection and resolution.</span></span>  
  
     <span data-ttu-id="4473b-156">通过将数据子集发布到每个订阅服务器或者让应用程序将给定行的更改定向到给定的节点，可以对更改进行分区：</span><span class="sxs-lookup"><span data-stu-id="4473b-156">Changes can be partitioned by publishing subsets of data to each Subscriber or by having an application direct changes for a given row to a given node:</span></span>  
  
    -   <span data-ttu-id="4473b-157">合并复制支持对单个发布使用参数化筛选器发布数据子集。</span><span class="sxs-lookup"><span data-stu-id="4473b-157">Merge replication supports publishing subsets of data using parameterized filters with a single publication.</span></span> <span data-ttu-id="4473b-158">有关详细信息，请参阅 [参数化行筛选器](../merge/parameterized-filters-parameterized-row-filters.md)。</span><span class="sxs-lookup"><span data-stu-id="4473b-158">For more information, see [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
    -   <span data-ttu-id="4473b-159">事务复制支持对多个发布使用静态筛选器发布数据子集。</span><span class="sxs-lookup"><span data-stu-id="4473b-159">Transactional replication supports publishing subsets of data using static filters with multiple publications.</span></span> <span data-ttu-id="4473b-160">有关详细信息，请参阅[筛选已发布数据](../publish/filter-published-data.md)。</span><span class="sxs-lookup"><span data-stu-id="4473b-160">For more information, see [Filter Published Data](../publish/filter-published-data.md).</span></span>  
  
-   <span data-ttu-id="4473b-161">灵活地使用行筛选器。</span><span class="sxs-lookup"><span data-stu-id="4473b-161">Use row filters judiciously.</span></span>  
  
     <span data-ttu-id="4473b-162">当事务发布包括一个或多个使用行筛选器的项目时，日志读取器代理在扫描事务日志时，必须将该筛选器应用到受表更新影响的每一行。</span><span class="sxs-lookup"><span data-stu-id="4473b-162">When a transactional publication includes one or more articles that use row filters, the Log Reader Agent must apply the filter to each row affected by an update to the table as it scans the transaction log.</span></span> <span data-ttu-id="4473b-163">日志读取器代理的吞吐量因此受到影响。</span><span class="sxs-lookup"><span data-stu-id="4473b-163">The throughput of the Log Reader Agent is therefore affected.</span></span>  
  
     <span data-ttu-id="4473b-164">同样，合并复制必须计算已更改或删除的行，以确定哪些订阅服务器应接收这些行。</span><span class="sxs-lookup"><span data-stu-id="4473b-164">Similarly, merge replication must evaluate changed or deleted rows to determine which Subscribers should receive those rows.</span></span> <span data-ttu-id="4473b-165">当利用行筛选器减少订阅服务器中要求的数据时，此处理更加复杂，并且比发布表中的所有行时更慢。</span><span class="sxs-lookup"><span data-stu-id="4473b-165">When row filters are employed to reduce the data required at a Subscriber, this processing is more complex and can be slower than when you publish all rows in a table.</span></span> <span data-ttu-id="4473b-166">应仔细考虑降低每个订阅服务器的存储要求与获得最大吞吐量的需求之间的平衡点。</span><span class="sxs-lookup"><span data-stu-id="4473b-166">Consider carefully the tradeoff between reduced storage requirements at each Subscriber and the need for achieving maximum throughput.</span></span> <span data-ttu-id="4473b-167">有关筛选的详细信息，请参阅[筛选已发布数据](../publish/filter-published-data.md)。</span><span class="sxs-lookup"><span data-stu-id="4473b-167">For more information on filtering, see [Filter Published Data](../publish/filter-published-data.md).</span></span>  
  
## <a name="subscription-considerations"></a><span data-ttu-id="4473b-168">订阅注意事项</span><span class="sxs-lookup"><span data-stu-id="4473b-168">Subscription Considerations</span></span>  
  
-   <span data-ttu-id="4473b-169">当存在大量订阅服务器时，应使用请求订阅。</span><span class="sxs-lookup"><span data-stu-id="4473b-169">Use pull subscriptions when there are a large number of Subscribers.</span></span>  
  
     <span data-ttu-id="4473b-170">分发代理和合并代理在分发服务器中运行以实现推送订阅，在订阅服务器中运行以实现请求订阅。</span><span class="sxs-lookup"><span data-stu-id="4473b-170">The Distribution Agent and Merge Agent run at the Distributor for push subscriptions, and at Subscribers for pull subscriptions.</span></span> <span data-ttu-id="4473b-171">使用请求订阅可以提高性能，因为它将代理处理从分发服务器移到了订阅服务器中。</span><span class="sxs-lookup"><span data-stu-id="4473b-171">Using pull subscriptions can improve performance by moving agent processing from the Distributor to Subscribers.</span></span> <span data-ttu-id="4473b-172">有关详细信息，请参阅[订阅发布](../subscribe-to-publications.md)。</span><span class="sxs-lookup"><span data-stu-id="4473b-172">For more information, see [Subscribe to Publications](../subscribe-to-publications.md).</span></span>  
  
-   <span data-ttu-id="4473b-173">如果订阅服务器滞后太多，请考虑重新初始化订阅。</span><span class="sxs-lookup"><span data-stu-id="4473b-173">Consider reinitialization of the subscription if Subscribers are too far behind.</span></span>  
  
     <span data-ttu-id="4473b-174">当需要将大量更改发送到订阅服务器时，用新快照重新初始化这些更改可能比使用复制分别移动每个更改要快。</span><span class="sxs-lookup"><span data-stu-id="4473b-174">When large amounts of changes need to be sent to Subscribers, reinitializing them with a new snapshot might be faster than using replication to move the individual changes.</span></span> <span data-ttu-id="4473b-175">有关详细信息，请参阅 [重新初始化订阅](../reinitialize-subscriptions.md)。</span><span class="sxs-lookup"><span data-stu-id="4473b-175">For more information, see [Reinitialize Subscriptions](../reinitialize-subscriptions.md).</span></span>  
  
     <span data-ttu-id="4473b-176">对于事务复制，复制监视器在 **“未分发的命令”** 选项卡上显示下列信息：分发数据库中尚未分发到订阅服务器的事务数，以及预计分发这些事务所需的时间。</span><span class="sxs-lookup"><span data-stu-id="4473b-176">For transactional replication, Replication Monitor displays on the **Undistributed Commands** tab information about: the number of transactions in the distribution database that have not yet been distributed to a Subscriber; and the estimated time for distributing these transactions.</span></span> <span data-ttu-id="4473b-177">有关详细信息，请参阅[使用复制监视器查看信息和执行任务](../monitor/view-information-and-perform-tasks-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="4473b-177">For more information, see [View Information and Perform Tasks using Replication Monitor](../monitor/view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
## <a name="snapshot-considerations"></a><span data-ttu-id="4473b-178">快照注意事项</span><span class="sxs-lookup"><span data-stu-id="4473b-178">Snapshot Considerations</span></span>  
  
-   <span data-ttu-id="4473b-179">仅在必要时和非高峰时段运行快照代理。</span><span class="sxs-lookup"><span data-stu-id="4473b-179">Run the Snapshot Agent only when necessary and at off-peak times.</span></span>  
  
     <span data-ttu-id="4473b-180">快照代理将发布服务器中已发布表中的数据大容量复制到分发服务器中的快照文件夹的一个文件中。</span><span class="sxs-lookup"><span data-stu-id="4473b-180">The Snapshot Agent bulk copies data from the published table on the Publisher to a file in the snapshot folder on the Distributor.</span></span> <span data-ttu-id="4473b-181">生成快照可能是一个占用大量资源的过程，最好安排在非高峰时段进行。</span><span class="sxs-lookup"><span data-stu-id="4473b-181">Generating a snapshot can be a resource intensive process and is best scheduled during off-peak times.</span></span>  
  
-   <span data-ttu-id="4473b-182">除非要求使用字符模式快照，否则请使用本机模式快照。</span><span class="sxs-lookup"><span data-stu-id="4473b-182">Use a native mode snapshot unless a character mode snapshot is required.</span></span>  
  
     <span data-ttu-id="4473b-183">除了非[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 订阅服务器和运行 [!INCLUDE[ssEW](../../../includes/ssew-md.md)]的订阅服务器（它们要求使用字符模式快照）外，请为其他所有订阅服务器使用默认的本机模式快照。</span><span class="sxs-lookup"><span data-stu-id="4473b-183">Use the default native mode snapshot for all Subscribers except non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers and Subscribers running [!INCLUDE[ssEW](../../../includes/ssew-md.md)], which require a character mode snapshot.</span></span>  
  
-   <span data-ttu-id="4473b-184">为一个发布使用一个快照文件夹。</span><span class="sxs-lookup"><span data-stu-id="4473b-184">Use a single snapshot folder for a publication.</span></span>  
  
     <span data-ttu-id="4473b-185">当指定与快照位置有关的发布属性时，可选择在默认的快照文件夹、备用快照文件夹或同时在这两个文件夹中生成快照文件。</span><span class="sxs-lookup"><span data-stu-id="4473b-185">When specifying the publication properties related to snapshot location, you can choose to generate snapshot files to the default snapshot folder, to an alternate snapshot folder, or to both.</span></span> <span data-ttu-id="4473b-186">当快照代理运行时，同时在这两个位置生成快照需要额外的磁盘空间和更多的处理。</span><span class="sxs-lookup"><span data-stu-id="4473b-186">Generating snapshot files in both locations requires additional disk space and more processing when the Snapshot Agent runs.</span></span>  
  
-   <span data-ttu-id="4473b-187">将快照文件夹放在分发服务器上未用于存储数据库或日志文件的本地驱动器中。</span><span class="sxs-lookup"><span data-stu-id="4473b-187">Place the snapshot folder on a drive local to the Distributor that is not used to store database or log files.</span></span>  
  
     <span data-ttu-id="4473b-188">快照代理将按顺序将数据写入快照文件夹。</span><span class="sxs-lookup"><span data-stu-id="4473b-188">The Snapshot Agent performs a sequential write of data to the snapshot folder.</span></span> <span data-ttu-id="4473b-189">将快照文件夹放在与数据库或日志文件分开的驱动器上可以减少磁盘间的争用，并有助于快照进程更快地完成。</span><span class="sxs-lookup"><span data-stu-id="4473b-189">Placing the snapshot folder on a separate drive from any database or log files reduces contention among the disks and helps the snapshot process complete faster.</span></span>  
  
-   <span data-ttu-id="4473b-190">在订阅服务器上创建订阅数据库时，考虑指定简单恢复模式或大容量日志恢复模式。</span><span class="sxs-lookup"><span data-stu-id="4473b-190">When you create the subscription database at the Subscriber, consider specifying a recovery model of simple or bulk-logged.</span></span> <span data-ttu-id="4473b-191">这允许在订阅服务器中应用快照时执行最少的大容量插入日志记录。</span><span class="sxs-lookup"><span data-stu-id="4473b-191">This allows minimal logging of the bulk inserts performed during the application of the snapshot at the Subscriber.</span></span> <span data-ttu-id="4473b-192">将快照应用于订阅数据库后，如有必要，可以更改为不同的恢复模式（复制的数据库可以使用任何恢复模式）。</span><span class="sxs-lookup"><span data-stu-id="4473b-192">After the snapshot has been applied to the subscription database, you can change to a different recovery model if necessary (replicated databases can use any of the recovery models).</span></span> <span data-ttu-id="4473b-193">有关选择恢复模式的详细信息，请参阅[还原和恢复概述 (SQL Server)](../../backup-restore/restore-and-recovery-overview-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="4473b-193">For more information about selecting a recovery model, see [Restore and Recovery Overview &#40;SQL Server&#41;](../../backup-restore/restore-and-recovery-overview-sql-server.md).</span></span>  
  
-   <span data-ttu-id="4473b-194">对于低带宽网络，考虑在可移动介质上使用备用快照文件夹和压缩的快照。</span><span class="sxs-lookup"><span data-stu-id="4473b-194">Consider using the alternate snapshot folder and compressed snapshots on removable media for low-bandwidth networks.</span></span>  
  
     <span data-ttu-id="4473b-195">压缩备用快照文件夹中的快照文件可以减少快照的磁盘存储空间要求，使快照文件更容易在可移动介质上传输。</span><span class="sxs-lookup"><span data-stu-id="4473b-195">Compressing snapshot files in the alternate snapshot folder can reduce snapshot disk storage requirements and make it easier to transfer snapshot files on removable media.</span></span>  
  
     <span data-ttu-id="4473b-196">在某些情况下，压缩的快照可以提高通过网络传输快照文件的性能。</span><span class="sxs-lookup"><span data-stu-id="4473b-196">Compressed snapshots can, in some cases, improve the performance of transferring snapshot files across the network.</span></span> <span data-ttu-id="4473b-197">但是，如果压缩快照，则在生成快照文件时需要通过快照代理进行额外处理，而在应用快照文件时需要通过分发代理或合并代理进行额外处理。</span><span class="sxs-lookup"><span data-stu-id="4473b-197">However, compressing the snapshot requires additional processing by the Snapshot Agent when generating the snapshot files, and by the Distribution Agent or Merge Agent when applying the snapshot files.</span></span> <span data-ttu-id="4473b-198">在某些情况下，这可能会降低生成快照的速度，并增加应用快照所需的时间。</span><span class="sxs-lookup"><span data-stu-id="4473b-198">This may slow down snapshot generation and increase the time it takes to apply a snapshot in some cases.</span></span> <span data-ttu-id="4473b-199">此外，如果发生网络故障，压缩的快照将无法恢复，因此不适用于不可靠的网络。</span><span class="sxs-lookup"><span data-stu-id="4473b-199">Additionally, compressed snapshots cannot be resumed if a network failure occurs; therefore they are not suitable for unreliable networks.</span></span> <span data-ttu-id="4473b-200">在网络中使用压缩的快照时，应仔细权衡这些利弊。</span><span class="sxs-lookup"><span data-stu-id="4473b-200">Consider these tradeoffs carefully when using compressed snapshots across a network.</span></span> <span data-ttu-id="4473b-201">有关详细信息，请参阅 [Alternate Snapshot Folder Locations](../alternate-snapshot-folder-locations.md) 和 [Compressed Snapshots](../compressed-snapshots.md)。</span><span class="sxs-lookup"><span data-stu-id="4473b-201">For more information, see [Alternate Snapshot Folder Locations](../alternate-snapshot-folder-locations.md) and [Compressed Snapshots](../compressed-snapshots.md).</span></span>  
  
-   <span data-ttu-id="4473b-202">考虑手动初始化订阅。</span><span class="sxs-lookup"><span data-stu-id="4473b-202">Consider initializing a subscription manually.</span></span>  
  
     <span data-ttu-id="4473b-203">在某些方案中，如涉及大型初始数据集的方案，使用快照以外的其他方法来初始化订阅更可取。</span><span class="sxs-lookup"><span data-stu-id="4473b-203">In some scenarios, such as those involving large initial datasets, it is preferable to initialize a subscription using a method other than a snapshot.</span></span> <span data-ttu-id="4473b-204">有关详细信息，请参阅 [初始化事务订阅（不使用快照）](../initialize-a-transactional-subscription-without-a-snapshot.md)中手动初始化订阅。</span><span class="sxs-lookup"><span data-stu-id="4473b-204">For more information, see [Initialize a Transactional Subscription Without a Snapshot](../initialize-a-transactional-subscription-without-a-snapshot.md).</span></span>  
  
## <a name="agent-parameters"></a><span data-ttu-id="4473b-205">代理参数</span><span class="sxs-lookup"><span data-stu-id="4473b-205">Agent Parameters</span></span>  
  
-   <span data-ttu-id="4473b-206">降低复制代理的详细级别，在初始测试、监视或调试期间除外。</span><span class="sxs-lookup"><span data-stu-id="4473b-206">Reduce the verbose levels of replication agents except during initial testing, monitoring, or debugging.</span></span>  
  
     <span data-ttu-id="4473b-207">降低分发代理或合并代理的 –HistoryVerboseLevel 参数和 –OutputVerboseLevel 参数\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4473b-207">Reduce the **-HistoryVerboseLevel** parameter and the **-OutputVerboseLevel** parameter of the Distribution Agents or Merge Agents.</span></span> <span data-ttu-id="4473b-208">这样可以减少为跟踪代理历史记录和输出而插入的新行数。</span><span class="sxs-lookup"><span data-stu-id="4473b-208">This reduces the number of new rows inserted to track agent history and output.</span></span> <span data-ttu-id="4473b-209">相反，具有相同状态的以前的历史记录消息将更新为新的历史记录信息。</span><span class="sxs-lookup"><span data-stu-id="4473b-209">Instead, previous history messages with the same status are updated to the new history information.</span></span> <span data-ttu-id="4473b-210">提高测试、监视和调试的详细级别，这样就可以获得有关代理活动的尽可能多的信息。</span><span class="sxs-lookup"><span data-stu-id="4473b-210">Increase the verbose levels for testing, monitoring, and debugging so that you have as much information about agent activity as possible.</span></span>  
  
-   <span data-ttu-id="4473b-211">使用快照代理、合并代理和分发代理的 –MaxBCPThreads 参数（指定的线程数不应超过计算机上的处理器数）\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4473b-211">Use the **-MaxBCPThreads** parameter of the Snapshot Agent, Merge Agent, and Distribution Agent (the number of threads specified should not exceed the number of processors on the computer).</span></span> <span data-ttu-id="4473b-212">此参数指定创建和应用快照时可以并行执行的大容量复制操作的数目。</span><span class="sxs-lookup"><span data-stu-id="4473b-212">This parameter specifies the number of bulk copy operations that can be performed in parallel when the snapshot is created and applied.</span></span>  
  
-   <span data-ttu-id="4473b-213">使用分发代理和合并代理的 –UseInprocLoader 参数（如果已发布表中包含 XML 列，则无法使用此参数）\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4473b-213">Use the **-UseInprocLoader** parameter of the Distribution Agent and the Merge Agent (this parameter cannot be used if published tables include XML columns).</span></span> <span data-ttu-id="4473b-214">此参数使代理在应用快照时使用 BULK INSERT 命令。</span><span class="sxs-lookup"><span data-stu-id="4473b-214">This parameter causes the agent to use the BULK INSERT command when the snapshot is applied.</span></span>  
  
 <span data-ttu-id="4473b-215">代理参数可以在代理配置文件和命令行中指定。</span><span class="sxs-lookup"><span data-stu-id="4473b-215">Agent parameters can be specified in agent profiles and on the command line.</span></span> <span data-ttu-id="4473b-216">有关详细信息，请参阅：</span><span class="sxs-lookup"><span data-stu-id="4473b-216">For more information, see:</span></span>  
  
-   [<span data-ttu-id="4473b-217">处理复制代理配置文件</span><span class="sxs-lookup"><span data-stu-id="4473b-217">Work with Replication Agent Profiles</span></span>](../agents/work-with-replication-agent-profiles.md)  
  
-   [<span data-ttu-id="4473b-218">查看和修改复制代理命令提示符参数 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="4473b-218">View and Modify Replication Agent Command Prompt Parameters &#40;SQL Server Management Studio&#41;</span></span>](../agents/view-and-modify-replication-agent-command-prompt-parameters.md)  
  
-   <span data-ttu-id="4473b-219">[Replication Agent Executables Concepts](../concepts/replication-agent-executables-concepts.md)的最小和最大内存量。</span><span class="sxs-lookup"><span data-stu-id="4473b-219">[Replication Agent Executables Concepts](../concepts/replication-agent-executables-concepts.md).</span></span>  
  
  
