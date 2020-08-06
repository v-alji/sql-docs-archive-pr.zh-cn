---
title: MSSQL_REPL027183 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_REPL027183 error
ms.assetid: 52c271ac-1a0e-43d5-85d4-35886d1efd32
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4484318cd6ec6ff4f0b201be69dc9b7544dd2c2f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693735"
---
# <a name="mssql_repl027183"></a><span data-ttu-id="cccca-102">MSSQL_REPL027183</span><span class="sxs-lookup"><span data-stu-id="cccca-102">MSSQL_REPL027183</span></span>
    
## <a name="message-details"></a><span data-ttu-id="cccca-103">消息详细信息</span><span class="sxs-lookup"><span data-stu-id="cccca-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cccca-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="cccca-104">Product Name</span></span>|<span data-ttu-id="cccca-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="cccca-105">SQL Server</span></span>|  
|<span data-ttu-id="cccca-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="cccca-106">Event ID</span></span>|<span data-ttu-id="cccca-107">27183</span><span class="sxs-lookup"><span data-stu-id="cccca-107">27183</span></span>|  
|<span data-ttu-id="cccca-108">事件源</span><span class="sxs-lookup"><span data-stu-id="cccca-108">Event Source</span></span>|<span data-ttu-id="cccca-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="cccca-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="cccca-110">组件</span><span class="sxs-lookup"><span data-stu-id="cccca-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="cccca-111">符号名称</span><span class="sxs-lookup"><span data-stu-id="cccca-111">Symbolic Name</span></span>||  
|<span data-ttu-id="cccca-112">消息正文</span><span class="sxs-lookup"><span data-stu-id="cccca-112">Message Text</span></span>|<span data-ttu-id="cccca-113">合并进程未能使用参数化的行筛选器来枚举项目中的更改。</span><span class="sxs-lookup"><span data-stu-id="cccca-113">The merge process failed to enumerate changes in articles with parameterized row filters.</span></span> <span data-ttu-id="cccca-114">如果此操作仍失败，请增大该进程的查询超时值，缩短发布的保持期，并改进对已发布表的索引。</span><span class="sxs-lookup"><span data-stu-id="cccca-114">If this failure continues, increase the query timeout for this process, reduce the retention period for the publication, and improve indexes on published tables.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="cccca-115">说明</span><span class="sxs-lookup"><span data-stu-id="cccca-115">Explanation</span></span>  
 <span data-ttu-id="cccca-116">在已筛选发布中处理更改时，如果出现合并代理超时，则会引发该错误。</span><span class="sxs-lookup"><span data-stu-id="cccca-116">This error is raised if a Merge Agent timeout occurs while processing changes in a filtered publication.</span></span> <span data-ttu-id="cccca-117">超时可能由下列一种原因引起：</span><span class="sxs-lookup"><span data-stu-id="cccca-117">The timeout might be caused by one of the following issues:</span></span>  
  
-   <span data-ttu-id="cccca-118">没有使用预计算分区优化。</span><span class="sxs-lookup"><span data-stu-id="cccca-118">Not using the precomputed partitions optimization.</span></span>  
  
-   <span data-ttu-id="cccca-119">用于筛选的列上存在索引碎片。</span><span class="sxs-lookup"><span data-stu-id="cccca-119">Index fragmentation on columns used for filtering.</span></span>  
  
-   <span data-ttu-id="cccca-120">大型合并元数据表，如 **MSmerge_tombstone**、 **MSmerge_contents**和 **MSmerge_genhistory**。</span><span class="sxs-lookup"><span data-stu-id="cccca-120">Large merge metadata tables, such as **MSmerge_tombstone**, **MSmerge_contents**, and **MSmerge_genhistory**.</span></span>  
  
-   <span data-ttu-id="cccca-121">未基于唯一键联接的已筛选表和涉及大量表的联接筛选器。</span><span class="sxs-lookup"><span data-stu-id="cccca-121">Filtered tables that are not joined on a unique key and join filters that involve a large number of tables.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="cccca-122">用户操作</span><span class="sxs-lookup"><span data-stu-id="cccca-122">User Action</span></span>  
 <span data-ttu-id="cccca-123">若要解决问题，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="cccca-123">To resolve the issue:</span></span>  
  
-   <span data-ttu-id="cccca-124">增大合并代理 **-QueryTimeOut** 参数的值，以在解决导致错误的基本问题后，仍可继续进行处理。</span><span class="sxs-lookup"><span data-stu-id="cccca-124">Increase the value of the **-QueryTimeOut** parameter for the Merge Agent to allow processing to continue while you address the underlying issues causing the error.</span></span> <span data-ttu-id="cccca-125">代理参数可以在代理配置文件和命令行中指定。</span><span class="sxs-lookup"><span data-stu-id="cccca-125">Agent parameters can be specified in agent profiles and on the command line.</span></span> <span data-ttu-id="cccca-126">有关详细信息，请参阅：</span><span class="sxs-lookup"><span data-stu-id="cccca-126">For more information, see:</span></span>  
  
    -   [<span data-ttu-id="cccca-127">处理复制代理配置文件</span><span class="sxs-lookup"><span data-stu-id="cccca-127">Work with Replication Agent Profiles</span></span>](agents/replication-agent-profiles.md)  
  
    -   [<span data-ttu-id="cccca-128">查看和修改复制代理命令提示符参数 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="cccca-128">View and Modify Replication Agent Command Prompt Parameters &#40;SQL Server Management Studio&#41;</span></span>](agents/view-and-modify-replication-agent-command-prompt-parameters.md)  
  
    -   <span data-ttu-id="cccca-129">[Replication Agent Executables Concepts](concepts/replication-agent-executables-concepts.md)的最小和最大内存量。</span><span class="sxs-lookup"><span data-stu-id="cccca-129">[Replication Agent Executables Concepts](concepts/replication-agent-executables-concepts.md).</span></span>  
  
-   <span data-ttu-id="cccca-130">请尽可能使用预计算分区优化。</span><span class="sxs-lookup"><span data-stu-id="cccca-130">Use the precomputed partitions optimization if possible.</span></span> <span data-ttu-id="cccca-131">如果许多发布要求都得到满足，则默认使用此优化。</span><span class="sxs-lookup"><span data-stu-id="cccca-131">This optimization is used by default if a number of publication requirements are met.</span></span> <span data-ttu-id="cccca-132">有关这些要求的详细信息，请参阅[使用预计算分区优化参数化筛选器性能](merge/parameterized-filters-optimize-for-precomputed-partitions.md)。</span><span class="sxs-lookup"><span data-stu-id="cccca-132">For more information about these requirements, see [Optimize Parameterized Filter Performance with Precomputed Partitions](merge/parameterized-filters-optimize-for-precomputed-partitions.md).</span></span> <span data-ttu-id="cccca-133">如果发布不满足这些要求，则请考虑重新设计发布。</span><span class="sxs-lookup"><span data-stu-id="cccca-133">If the publication does not meet these requirements, consider redesigning the publication.</span></span>  
  
-   <span data-ttu-id="cccca-134">指定发布保持期可能的最低设置，因为只有在达到保持期时，复制才会清除发布数据库和订阅数据库中的元数据。</span><span class="sxs-lookup"><span data-stu-id="cccca-134">Specify the lowest setting possible for the publication retention period, because replication cannot clean up metadata in the publication and subscription databases until the retention period is reached.</span></span> <span data-ttu-id="cccca-135">有关详细信息，请参阅 [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md)。</span><span class="sxs-lookup"><span data-stu-id="cccca-135">For more information, see [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md).</span></span>  
  
-   <span data-ttu-id="cccca-136">在合并复制维护过程中，应不定期检查以下与合并复制相关联的系统表的增长情况： **MSmerge_contents**、 **MSmerge_genhistory**、 **MSmerge_tombstone**、 **MSmerge_current_partition_mappings**、 **MSmerge_past_partition_mappings**。</span><span class="sxs-lookup"><span data-stu-id="cccca-136">As part of maintenance for merge replication, occasionally check the growth of the system tables associated with merge replication: **MSmerge_contents**, **MSmerge_genhistory**, and **MSmerge_tombstone**, **MSmerge_current_partition_mappings**, and **MSmerge_past_partition_mappings**.</span></span> <span data-ttu-id="cccca-137">定期对这些表重建索引。</span><span class="sxs-lookup"><span data-stu-id="cccca-137">Periodically re-index these tables.</span></span> <span data-ttu-id="cccca-138">有关详细信息，请参阅 [重新组织和重新生成索引](../indexes/indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="cccca-138">For more information, see [Reorganize and Rebuild Indexes](../indexes/indexes.md).</span></span>  
  
-   <span data-ttu-id="cccca-139">请确保用于筛选的列已建立了适当的索引，并根据需要重新生成这些索引。</span><span class="sxs-lookup"><span data-stu-id="cccca-139">Ensure that columns used for filtering are properly indexed and rebuild such indexes if necessary.</span></span> <span data-ttu-id="cccca-140">有关详细信息，请参阅 [重新组织和重新生成索引](../indexes/indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="cccca-140">For more information, see [Reorganize and Rebuild Indexes](../indexes/indexes.md).</span></span>  
  
-   <span data-ttu-id="cccca-141">设置基于唯一列的联接筛选器的 **join_unique_key** 属性。</span><span class="sxs-lookup"><span data-stu-id="cccca-141">Set the **join_unique_key** property for join filters that are based on unique columns.</span></span> <span data-ttu-id="cccca-142">有关详细信息，请参阅 [Join Filters](merge/join-filters.md)。</span><span class="sxs-lookup"><span data-stu-id="cccca-142">For more information, see [Join Filters](merge/join-filters.md).</span></span>  
  
-   <span data-ttu-id="cccca-143">限制联接筛选器层次结构中的表数。</span><span class="sxs-lookup"><span data-stu-id="cccca-143">Limit the number of tables in the join filter hierarchy.</span></span> <span data-ttu-id="cccca-144">如果要生成五个或更多表的联接筛选器，请考虑其他解决方案：不筛选小表、不会发生更改的表或主要是查找表的表。</span><span class="sxs-lookup"><span data-stu-id="cccca-144">If you are generating join filters of five or more tables, consider other solutions: do not filter tables that are small, not subject to change, or are primarily lookup tables.</span></span> <span data-ttu-id="cccca-145">仅在必须在订阅中分区的表之间使用联接筛选器。</span><span class="sxs-lookup"><span data-stu-id="cccca-145">Use join filters only between tables that must be partitioned among subscriptions.</span></span>  
  
-   <span data-ttu-id="cccca-146">在同步之间的筛选表上进行较少量的更改，或更加频繁地运行合并代理。</span><span class="sxs-lookup"><span data-stu-id="cccca-146">Make a smaller number of changes on filtered tables between synchronizations, or run the Merge Agent more frequently.</span></span> <span data-ttu-id="cccca-147">有关如何设置同步计划的详细信息，请参阅 [Specify Synchronization Schedules](specify-synchronization-schedules.md)。</span><span class="sxs-lookup"><span data-stu-id="cccca-147">For more information about setting synchronization schedules, see [Specify Synchronization Schedules](specify-synchronization-schedules.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cccca-148">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cccca-148">See Also</span></span>  
 [<span data-ttu-id="cccca-149">错误和事件参考（复制）</span><span class="sxs-lookup"><span data-stu-id="cccca-149">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
