---
title: 为事务复制测量滞后时间和验证连接 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Replication Monitor, performance
- tracer tokens [SQL Server replication]
- latency [SQL Server replication]
- transactional replication, tracer tokens
- monitoring performance [SQL Server replication], tracer tokens
ms.assetid: 4addd426-7523-4067-8d7d-ca6bae4c9e34
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3ba1e5eddfdcffa5fbefdea323f110ba9d15ca8c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580133"
---
# <a name="measure-latency-and-validate-connections-for-transactional-replication"></a><span data-ttu-id="12304-102">为事务复制测量滞后时间和验证连接</span><span class="sxs-lookup"><span data-stu-id="12304-102">Measure Latency and Validate Connections for Transactional Replication</span></span>
  <span data-ttu-id="12304-103">本主题说明如何使用复制监视器、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 或复制管理对象 (RMO) 在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中为事务复制测量滞后时间和验证连接。</span><span class="sxs-lookup"><span data-stu-id="12304-103">This topic describes how to measure latency and validate connections for transactional replication in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using Replication Monitor, [!INCLUDE[tsql](../../../includes/tsql-md.md)], or Replication Management Objects (RMO).</span></span> <span data-ttu-id="12304-104">事务复制提供了跟踪令牌功能，可以方便地测量事务复制拓扑中的滞后时间和验证发布服务器、分发服务器及订阅服务器之间的连接。</span><span class="sxs-lookup"><span data-stu-id="12304-104">Transactional replication provides the tracer token feature, which provides a convenient way to measure latency in transactional replication topologies and to validate the connections between the Publisher, Distributor and Subscribers.</span></span> <span data-ttu-id="12304-105">将令牌（少量数据）写入发布数据库的事务日志中，就像标记典型的复制事务一样对其进行标记，使用令牌可以执行以下计算：</span><span class="sxs-lookup"><span data-stu-id="12304-105">A token (a small amount of data) is written to the transaction log of the publication database, marked as though it were a typical replicated transaction, and sent through the system, allowing a calculation of:</span></span>  
  
-   <span data-ttu-id="12304-106">计算在发布服务器上提交事务和在分发服务器上将相应命令插入分发数据库之间所间隔的时间。</span><span class="sxs-lookup"><span data-stu-id="12304-106">How much time elapses between a transaction being committed at the Publisher and the corresponding command being inserted in the distribution database at the Distributor.</span></span>  
  
-   <span data-ttu-id="12304-107">计算在分发数据库中插入命令和在订阅服务器上提交相应事务之间所间隔的时间。</span><span class="sxs-lookup"><span data-stu-id="12304-107">How much time elapses between a command being inserted in the distribution database and the corresponding transaction being committed at a Subscriber.</span></span>  
  
 <span data-ttu-id="12304-108">通过这些计算可以回答许多问题，包括：</span><span class="sxs-lookup"><span data-stu-id="12304-108">From these calculations, you can answer a number of questions, including:</span></span>  
  
-   <span data-ttu-id="12304-109">哪个订阅服务器在从发布服务器接收更改时所需的时间最长？</span><span class="sxs-lookup"><span data-stu-id="12304-109">Which Subscribers take the longest to receive a change from the Publisher?</span></span>  
  
-   <span data-ttu-id="12304-110">在应当收到跟踪令牌的订阅服务器中，哪些订阅服务器（如果有）没有收到跟踪令牌？</span><span class="sxs-lookup"><span data-stu-id="12304-110">Of the Subscribers expected to receive the tracer token, which, if any, have not received it?</span></span>  
  
 <span data-ttu-id="12304-111">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="12304-111">**In This Topic**</span></span>  
  
-   <span data-ttu-id="12304-112">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="12304-112">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="12304-113">限制和局限</span><span class="sxs-lookup"><span data-stu-id="12304-113">Limitations and Restrictions</span></span>](#Restrictions)  
  
-   <span data-ttu-id="12304-114">**测量滞后时间和验证连接，使用：**</span><span class="sxs-lookup"><span data-stu-id="12304-114">**To measure latency and validate connections, using:**</span></span>  
  
     [<span data-ttu-id="12304-115">SQL Server 复制监视器</span><span class="sxs-lookup"><span data-stu-id="12304-115">SQL Server Replication Monitor</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="12304-116">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="12304-116">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="12304-117">复制管理对象</span><span class="sxs-lookup"><span data-stu-id="12304-117">Replication Management Objects</span></span>](#RMOProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="12304-118">开始之前</span><span class="sxs-lookup"><span data-stu-id="12304-118">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="12304-119">限制和局限</span><span class="sxs-lookup"><span data-stu-id="12304-119">Limitations and Restrictions</span></span>  
 <span data-ttu-id="12304-120">停止系统时跟踪令牌也很有用，停止系统的过程涉及停止所有活动并验证所有节点均已收到所有尚未完成的更改。</span><span class="sxs-lookup"><span data-stu-id="12304-120">Tracer tokens can also be useful when quiescing a system, which involves stopping all activity and verifying that all nodes have received all outstanding changes.</span></span> <span data-ttu-id="12304-121">有关详细信息，请参阅[停止复制拓扑（复制 Transact-SQL 编程）](../administration/quiesce-a-replication-topology-replication-transact-sql-programming.md)。</span><span class="sxs-lookup"><span data-stu-id="12304-121">For more information, see [Quiesce a Replication Topology &#40;Replication Transact-SQL Programming&#41;](../administration/quiesce-a-replication-topology-replication-transact-sql-programming.md).</span></span>  
  
 <span data-ttu-id="12304-122">若要使用跟踪令牌，必须使用特定版本的 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ：</span><span class="sxs-lookup"><span data-stu-id="12304-122">To use tracer tokens, you must use certain versions of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="12304-123">分发服务器必须是 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="12304-123">The Distributor must be [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] or later.</span></span>  
  
-   <span data-ttu-id="12304-124">发布服务器必须是 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 或更高版本，或者是 Oracle 发布服务器。</span><span class="sxs-lookup"><span data-stu-id="12304-124">The Publisher must be [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] or later or be an Oracle Publisher.</span></span>  
  
-   <span data-ttu-id="12304-125">对于推送订阅，如果订阅服务器为 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 7.0 或更高版本，则从发布服务器、分发服务器和订阅服务器收集跟踪令牌统计信息。</span><span class="sxs-lookup"><span data-stu-id="12304-125">For push subscriptions, tracer token statistics are gathered from the Publisher, Distributor, and Subscribers if the Subscriber is [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 7.0 or later.</span></span>  
  
-   <span data-ttu-id="12304-126">对于请求订阅，仅当订阅服务器为 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 或更高版本时才从订阅服务器收集跟踪令牌统计信息。</span><span class="sxs-lookup"><span data-stu-id="12304-126">For pull subscriptions, tracer token statistics are gathered from Subscribers only if the Subscriber is [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] or later.</span></span> <span data-ttu-id="12304-127">如果订阅服务器为 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 7.0 或 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] ，将仅从发布服务器和分发服务器收集统计信息。</span><span class="sxs-lookup"><span data-stu-id="12304-127">If the Subscriber is [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 7.0 or [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)], statistics are gathered only from the Publisher and Distributor.</span></span>  
  
 <span data-ttu-id="12304-128">还有一些需要注意的问题和限制：</span><span class="sxs-lookup"><span data-stu-id="12304-128">There are also a number of other issues and restrictions to be aware of:</span></span>  
  
-   <span data-ttu-id="12304-129">订阅必须处于活动状态才能接收跟踪令牌。</span><span class="sxs-lookup"><span data-stu-id="12304-129">Subscriptions must be active to receive a tracer token.</span></span> <span data-ttu-id="12304-130">订阅如果已经初始化就会处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="12304-130">A subscription is active if it has been initialized.</span></span>  
  
-   <span data-ttu-id="12304-131">重新初始化会删除相关订阅的所有挂起的跟踪令牌。</span><span class="sxs-lookup"><span data-stu-id="12304-131">Reinitialization removes any pending tracer tokens for the relevant subscriptions.</span></span>  
  
-   <span data-ttu-id="12304-132">订阅服务器仅接收在其初始同步之后创建的跟踪令牌。</span><span class="sxs-lookup"><span data-stu-id="12304-132">Subscribers only receive tracer tokens that were created after their initial synchronization.</span></span>  
  
-   <span data-ttu-id="12304-133">重新发布订阅服务器不转发跟踪令牌。</span><span class="sxs-lookup"><span data-stu-id="12304-133">Tracer tokens are not forwarded by republishing Subscribers.</span></span>  
  
-   <span data-ttu-id="12304-134">故障转移到辅助实例后，复制监视器无法调整 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的发布实例的名称，将继续在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]的原始主实例名称下显示复制信息。</span><span class="sxs-lookup"><span data-stu-id="12304-134">After failover to a secondary, Replication Monitor is unable to adjust the name of the publishing instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] and will continue to display replication information under the name of the original primary instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="12304-135">在故障转移之后，无法使用复制监视器输入跟踪令牌，但是可以在复制监视器中显示使用 [!INCLUDE[tsql](../../../includes/tsql-md.md)]在新发布服务器上输入的跟踪令牌。</span><span class="sxs-lookup"><span data-stu-id="12304-135">After failover, a tracer token cannot be entered by using the Replication Monitor, however a tracer token entered on the new publisher by using [!INCLUDE[tsql](../../../includes/tsql-md.md)], is visible in Replication Monitor.</span></span>  
  
##  <a name="using-sql-server-replication-monitor"></a><a name="SSMSProcedure"></a><span data-ttu-id="12304-136">使用 SQL Server 复制监视器</span><span class="sxs-lookup"><span data-stu-id="12304-136">Using SQL Server Replication Monitor</span></span>  
 <span data-ttu-id="12304-137">有关启动复制监视器的信息，请参阅[启动复制监视器](start-the-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="12304-137">For information about starting Replication Monitor, see [Start the Replication Monitor](start-the-replication-monitor.md).</span></span>  
  
#### <a name="to-insert-a-tracer-token-and-view-information-on-the-token"></a><span data-ttu-id="12304-138">插入跟踪令牌并查看有关令牌的信息</span><span class="sxs-lookup"><span data-stu-id="12304-138">To insert a tracer token and view information on the token</span></span>  
  
1.  <span data-ttu-id="12304-139">在左窗格中展开发布服务器组，再展开其中的一个发布服务器，然后单击其中的一个发布。</span><span class="sxs-lookup"><span data-stu-id="12304-139">Expand a Publisher group in the left pane, expand a Publisher, and then click a publication.</span></span>  
  
2.  <span data-ttu-id="12304-140">单击 **“跟踪令牌”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="12304-140">Click the **Tracer Tokens** tab.</span></span>  
  
3.  <span data-ttu-id="12304-141">单击 **“插入跟踪器”**。</span><span class="sxs-lookup"><span data-stu-id="12304-141">Click **Insert Tracer**.</span></span>  
  
4.  <span data-ttu-id="12304-142">在以下列中查看跟踪令牌的运行时间： **“发布服务器到分发服务器”**、 **“分发服务器到订阅服务器”**、 **“总滞后时间”**。</span><span class="sxs-lookup"><span data-stu-id="12304-142">View elapsed time for the tracer token in the following columns: **Publisher to Distributor**, **Distributor to Subscriber**, **Total Latency**.</span></span> <span data-ttu-id="12304-143">值为 "**挂起**" 表示令牌尚未到达给定点。</span><span class="sxs-lookup"><span data-stu-id="12304-143">A value of **Pending** indicates that the token has not reached a given point.</span></span>  
  
#### <a name="to-view-information-on-a-tracer-token-inserted-previously"></a><span data-ttu-id="12304-144">查看有关以前插入的跟踪令牌的信息</span><span class="sxs-lookup"><span data-stu-id="12304-144">To view information on a tracer token inserted previously</span></span>  
  
1.  <span data-ttu-id="12304-145">在左窗格中展开发布服务器组，再展开其中的一个发布服务器，然后单击其中的一个发布。</span><span class="sxs-lookup"><span data-stu-id="12304-145">Expand a Publisher group in the left pane, expand a Publisher, and then click a publication.</span></span>  
  
2.  <span data-ttu-id="12304-146">单击 **“跟踪令牌”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="12304-146">Click the **Tracer Tokens** tab.</span></span>  
  
3.  <span data-ttu-id="12304-147">从 **“插入时间”** 下拉列表中选择时间。</span><span class="sxs-lookup"><span data-stu-id="12304-147">Select a time from the **Time inserted** drop-down list.</span></span>  
  
4.  <span data-ttu-id="12304-148">在以下列中查看跟踪令牌的运行时间： **“发布服务器到分发服务器”**、 **“分发服务器到订阅服务器”**、 **“总滞后时间”**。</span><span class="sxs-lookup"><span data-stu-id="12304-148">View elapsed time for the tracer token in the following columns: **Publisher to Distributor**, **Distributor to Subscriber**, **Total Latency**.</span></span> <span data-ttu-id="12304-149">值为 "**挂起**" 表示令牌尚未到达给定点。</span><span class="sxs-lookup"><span data-stu-id="12304-149">A value of **Pending** indicates that the token has not reached a given point.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="12304-150">跟踪令牌信息的保留时间与其他历史数据的保留时间一样长，该时间由分发数据库的历史记录保持期来控制。</span><span class="sxs-lookup"><span data-stu-id="12304-150">Tracer token information is retained for the same time period as other historical data, which is governed by the history retention period of the distribution database.</span></span> <span data-ttu-id="12304-151">若要了解如何更改分发数据库属性，请参阅[查看和修改分发服务器和发布服务器属性](../view-and-modify-distributor-and-publisher-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="12304-151">For information about changing distribution database properties, see [View and Modify Distributor and Publisher Properties](../view-and-modify-distributor-and-publisher-properties.md).</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="12304-152">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="12304-152">Using Transact-SQL</span></span>  
  
#### <a name="to-post-a-tracer-token-to-a-transactional-publication"></a><span data-ttu-id="12304-153">若要将跟踪令牌发布到事务发布</span><span class="sxs-lookup"><span data-stu-id="12304-153">To post a tracer token to a transactional publication</span></span>  
  
1.  <span data-ttu-id="12304-154">（可选）在发布服务器上，对发布数据库执行 [sp_helppublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="12304-154">(Optional) At the Publisher on the publication database, execute [sp_helppublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql).</span></span> <span data-ttu-id="12304-155">请验证发布是否存在且状态是否处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="12304-155">Verify that the publication exists and that the status is active.</span></span>  
  
2.  <span data-ttu-id="12304-156">（可选）在发布服务器上，对发布数据库执行 [sp_helpsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="12304-156">(Optional) At the Publisher on the publication database, execute [sp_helpsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql).</span></span> <span data-ttu-id="12304-157">请验证订阅是否存在且状态是否处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="12304-157">Verify that the subscription exists and that the status is active.</span></span>  
  
3.  <span data-ttu-id="12304-158">在发布服务器的发布数据库中，执行 [sp_posttracertoken &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-posttracertoken-transact-sql)，指定 **@publication**。</span><span class="sxs-lookup"><span data-stu-id="12304-158">At the Publisher on the publication database, execute [sp_posttracertoken &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-posttracertoken-transact-sql), specifying **@publication**.</span></span> <span data-ttu-id="12304-159">请注意 **@tracer_token_id** output 参数的值。</span><span class="sxs-lookup"><span data-stu-id="12304-159">Note the value of the **@tracer_token_id** output parameter.</span></span>  
  
#### <a name="to-determine-latency-and-validate-connections-for-a-transactional-publication"></a><span data-ttu-id="12304-160">确定事务发布的滞后时间并验证连接</span><span class="sxs-lookup"><span data-stu-id="12304-160">To determine latency and validate connections for a transactional publication</span></span>  
  
1.  <span data-ttu-id="12304-161">使用前一过程将跟踪令牌发送到发布。</span><span class="sxs-lookup"><span data-stu-id="12304-161">Post a tracer token to the publication using the previous procedure.</span></span>  
  
2.  <span data-ttu-id="12304-162">在发布服务器上，对发布数据库执行 [sp_helptracertokens &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptracertokens-transact-sql)，指定 **@publication**。</span><span class="sxs-lookup"><span data-stu-id="12304-162">At the Publisher on the publication database, execute [sp_helptracertokens &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptracertokens-transact-sql), specifying **@publication**.</span></span> <span data-ttu-id="12304-163">这会返回发布到此发布的所有跟踪令牌的列表。</span><span class="sxs-lookup"><span data-stu-id="12304-163">This returns a list of all tracer tokens posted to the publication.</span></span> <span data-ttu-id="12304-164">请记录结果集中所需的 **tracer_id** 。</span><span class="sxs-lookup"><span data-stu-id="12304-164">Note the desired **tracer_id** in the result set.</span></span>  
  
3.  <span data-ttu-id="12304-165">在发布服务器上，对发布数据库执行 [sp_helptracertokenhistory &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql)，指定 **@publication** 以及步骤 2 提供的针对 **@tracer_id** 的跟踪令牌 ID。</span><span class="sxs-lookup"><span data-stu-id="12304-165">At the Publisher on the publication database, execute [sp_helptracertokenhistory &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql), specifying **@publication** and the tracer token ID from step 2 for **@tracer_id**.</span></span> <span data-ttu-id="12304-166">这会返回所选跟踪令牌的滞后时间信息。</span><span class="sxs-lookup"><span data-stu-id="12304-166">This returns latency information for the selected tracer token.</span></span>  
  
#### <a name="to-remove-tracer-tokens"></a><span data-ttu-id="12304-167">删除跟踪令牌</span><span class="sxs-lookup"><span data-stu-id="12304-167">To remove tracer tokens</span></span>  
  
1.  <span data-ttu-id="12304-168">在发布服务器上，对发布数据库执行 [sp_helptracertokens &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptracertokens-transact-sql)，指定 **@publication**。</span><span class="sxs-lookup"><span data-stu-id="12304-168">At the Publisher on the publication database, execute [sp_helptracertokens &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptracertokens-transact-sql), specifying **@publication**.</span></span> <span data-ttu-id="12304-169">这会返回发布到此发布的所有跟踪令牌的列表。</span><span class="sxs-lookup"><span data-stu-id="12304-169">This returns a list of all tracer tokens posted to the publication.</span></span> <span data-ttu-id="12304-170">请记录结果集中要删除的跟踪令牌的 **tracer_id** 。</span><span class="sxs-lookup"><span data-stu-id="12304-170">Note the **tracer_id** for the tracer token to delete in the result set.</span></span>  
  
2.  <span data-ttu-id="12304-171">在发布服务器上，对发布数据库执行 [sp_deletetracertokenhistory &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-deletetracertokenhistory-transact-sql)，指定 **@publication** 以及步骤 2 中要删除的针对 **@tracer_id** 的跟踪 ID。</span><span class="sxs-lookup"><span data-stu-id="12304-171">At the Publisher on the publication database, execute [sp_deletetracertokenhistory &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-deletetracertokenhistory-transact-sql), specifying **@publication** and the ID of the tracer to delete from step 2 for **@tracer_id**.</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="12304-172">示例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="12304-172">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="12304-173">本示例发送一个跟踪令牌记录并使用返回的已发送跟踪令牌的 ID 来查看滞后时间信息。</span><span class="sxs-lookup"><span data-stu-id="12304-173">This example posts a tracer token record and uses the returned ID of the posted tracer token to view latency information.</span></span>  
  
 [!code-sql[HowTo#sp_tracertokens](../../../snippets/tsql/SQL15/replication/howto/tsql/createtracertokens.sql#sp_tracertokens)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="12304-174">使用复制管理对象 (RMO)</span><span class="sxs-lookup"><span data-stu-id="12304-174">Using Replication Management Objects (RMO)</span></span>  
  
#### <a name="to-post-a-tracer-token-to-a-transactional-publication"></a><span data-ttu-id="12304-175">若要将跟踪令牌发布到事务发布</span><span class="sxs-lookup"><span data-stu-id="12304-175">To post a tracer token to a transactional publication</span></span>  
  
1.  <span data-ttu-id="12304-176">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 类创建与发布服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="12304-176">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="12304-177">创建的 <xref:Microsoft.SqlServer.Replication.TransPublication> 类的实例。</span><span class="sxs-lookup"><span data-stu-id="12304-177">Create an instance of the <xref:Microsoft.SqlServer.Replication.TransPublication> class.</span></span>  
  
3.  <span data-ttu-id="12304-178">设置发布的 <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> 和 <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> 属性，并将 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 属性设置为步骤 1 中创建的连接。</span><span class="sxs-lookup"><span data-stu-id="12304-178">Set the <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> and <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> properties for the publication, and set the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property to the connection created in step 1.</span></span>  
  
4.  <span data-ttu-id="12304-179">调用 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法获取该对象的属性。</span><span class="sxs-lookup"><span data-stu-id="12304-179">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span> <span data-ttu-id="12304-180">如果此方法返回 `false`，则说明步骤 3 中的发布属性定义不正确，或者此发布不存在。</span><span class="sxs-lookup"><span data-stu-id="12304-180">If this method returns `false`, either the publication properties in step 3 were defined incorrectly or the publication does not exist.</span></span>  
  
5.  <span data-ttu-id="12304-181">调用 <xref:Microsoft.SqlServer.Replication.TransPublication.PostTracerToken%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="12304-181">Call the <xref:Microsoft.SqlServer.Replication.TransPublication.PostTracerToken%2A> method.</span></span> <span data-ttu-id="12304-182">此方法将跟踪令牌插入到发布的事务日志中。</span><span class="sxs-lookup"><span data-stu-id="12304-182">This method inserts a tracer token into the publication's transaction log.</span></span>  
  
#### <a name="to-determine-latency-and-validate-connections-for-a-transactional-publication"></a><span data-ttu-id="12304-183">确定事务发布的滞后时间并验证连接</span><span class="sxs-lookup"><span data-stu-id="12304-183">To determine latency and validate connections for a transactional publication</span></span>  
  
1.  <span data-ttu-id="12304-184">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 类创建与分发服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="12304-184">Create a connection to the Distributor by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="12304-185">创建的 <xref:Microsoft.SqlServer.Replication.PublicationMonitor> 类的实例。</span><span class="sxs-lookup"><span data-stu-id="12304-185">Create an instance of the <xref:Microsoft.SqlServer.Replication.PublicationMonitor> class.</span></span>  
  
3.  <span data-ttu-id="12304-186">设置 <xref:Microsoft.SqlServer.Replication.PublicationMonitor.Name%2A>、 <xref:Microsoft.SqlServer.Replication.PublicationMonitor.DistributionDBName%2A>、 <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublisherName%2A>和 <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublicationDBName%2A> 属性，并将 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 属性设置为步骤 1 中创建的连接。</span><span class="sxs-lookup"><span data-stu-id="12304-186">Set the <xref:Microsoft.SqlServer.Replication.PublicationMonitor.Name%2A>, <xref:Microsoft.SqlServer.Replication.PublicationMonitor.DistributionDBName%2A>, <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublisherName%2A>, and <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublicationDBName%2A> properties, and set the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property to the connection created in step 1.</span></span>  
  
4.  <span data-ttu-id="12304-187">调用 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法获取该对象的属性。</span><span class="sxs-lookup"><span data-stu-id="12304-187">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span> <span data-ttu-id="12304-188">如果此方法返回 `false`，则说明步骤 3 中发布监视器的属性定义错误或此发布不存在。</span><span class="sxs-lookup"><span data-stu-id="12304-188">If this method returns `false`, either the publication monitor properties in step 3 were defined incorrectly or the publication does not exist.</span></span>  
  
5.  <span data-ttu-id="12304-189">调用 <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumTracerTokens%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="12304-189">Call the <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumTracerTokens%2A> method.</span></span> <span data-ttu-id="12304-190">将返回的 <xref:System.Collections.ArrayList> 对象转换为 <xref:Microsoft.SqlServer.Replication.TracerToken> 对象数组。</span><span class="sxs-lookup"><span data-stu-id="12304-190">Cast the returned <xref:System.Collections.ArrayList> object to an array of <xref:Microsoft.SqlServer.Replication.TracerToken> objects.</span></span>  
  
6.  <span data-ttu-id="12304-191">调用 <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumTracerTokenHistory%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="12304-191">Call the <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumTracerTokenHistory%2A> method.</span></span> <span data-ttu-id="12304-192">为步骤 5 中的跟踪令牌传递 <xref:Microsoft.SqlServer.Replication.TracerToken.TracerTokenId%2A> 的值。</span><span class="sxs-lookup"><span data-stu-id="12304-192">Pass a value of <xref:Microsoft.SqlServer.Replication.TracerToken.TracerTokenId%2A> for a tracer token from step 5.</span></span> <span data-ttu-id="12304-193">这样会将所选跟踪令牌的滞后信息作为 <xref:System.Data.DataSet> 对象返回。</span><span class="sxs-lookup"><span data-stu-id="12304-193">This returns latency information for the selected tracer token as a <xref:System.Data.DataSet> object.</span></span> <span data-ttu-id="12304-194">如果返回了所有跟踪令牌信息，则发布服务器与分发服务器之间的连接和分发服务器与订阅服务器之间的连接同时存在，并且复制拓扑工作正常。</span><span class="sxs-lookup"><span data-stu-id="12304-194">If all tracer token information is returned, the connection between the Publisher and Distributor and the connection between the Distributor and the Subscriber both exist and the replication topology is functioning.</span></span>  
  
#### <a name="to-remove-tracer-tokens"></a><span data-ttu-id="12304-195">删除跟踪令牌</span><span class="sxs-lookup"><span data-stu-id="12304-195">To remove tracer tokens</span></span>  
  
1.  <span data-ttu-id="12304-196">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 类创建与分发服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="12304-196">Create a connection to the Distributor by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="12304-197">创建的 <xref:Microsoft.SqlServer.Replication.PublicationMonitor> 类的实例。</span><span class="sxs-lookup"><span data-stu-id="12304-197">Create an instance of the <xref:Microsoft.SqlServer.Replication.PublicationMonitor> class.</span></span>  
  
3.  <span data-ttu-id="12304-198">设置 <xref:Microsoft.SqlServer.Replication.PublicationMonitor.Name%2A>、 <xref:Microsoft.SqlServer.Replication.PublicationMonitor.DistributionDBName%2A>、 <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublisherName%2A>和 <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublicationDBName%2A> 属性，并将 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 属性设置为步骤 1 中创建的连接。</span><span class="sxs-lookup"><span data-stu-id="12304-198">Set the <xref:Microsoft.SqlServer.Replication.PublicationMonitor.Name%2A>, <xref:Microsoft.SqlServer.Replication.PublicationMonitor.DistributionDBName%2A>, <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublisherName%2A>, and <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublicationDBName%2A> properties, and set the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property to the connection created in step 1.</span></span>  
  
4.  <span data-ttu-id="12304-199">调用 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法获取该对象的属性。</span><span class="sxs-lookup"><span data-stu-id="12304-199">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span> <span data-ttu-id="12304-200">如果此方法返回 `false`，则说明步骤 3 中发布监视器的属性定义错误或此发布不存在。</span><span class="sxs-lookup"><span data-stu-id="12304-200">If this method returns `false`, either the publication monitor properties in step 3 were defined incorrectly or the publication does not exist.</span></span>  
  
5.  <span data-ttu-id="12304-201">调用 <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumTracerTokens%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="12304-201">Call the <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumTracerTokens%2A> method.</span></span> <span data-ttu-id="12304-202">将返回的 <xref:System.Collections.ArrayList> 对象转换为 <xref:Microsoft.SqlServer.Replication.TracerToken> 对象数组。</span><span class="sxs-lookup"><span data-stu-id="12304-202">Cast the returned <xref:System.Collections.ArrayList> object to an array of <xref:Microsoft.SqlServer.Replication.TracerToken> objects.</span></span>  
  
6.  <span data-ttu-id="12304-203">调用 <xref:Microsoft.SqlServer.Replication.PublicationMonitor.CleanUpTracerTokenHistory%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="12304-203">Call the <xref:Microsoft.SqlServer.Replication.PublicationMonitor.CleanUpTracerTokenHistory%2A> method.</span></span> <span data-ttu-id="12304-204">传递以下值之一：</span><span class="sxs-lookup"><span data-stu-id="12304-204">Pass one of the following values:</span></span>  
  
    -   <span data-ttu-id="12304-205">步骤 5 中跟踪令牌的 <xref:Microsoft.SqlServer.Replication.TracerToken.TracerTokenId%2A> 。</span><span class="sxs-lookup"><span data-stu-id="12304-205">The <xref:Microsoft.SqlServer.Replication.TracerToken.TracerTokenId%2A> for a tracer token from step 5.</span></span> <span data-ttu-id="12304-206">这将删除选定令牌的信息。</span><span class="sxs-lookup"><span data-stu-id="12304-206">This deletes information for a selected token.</span></span>  
  
    -   <span data-ttu-id="12304-207"><xref:System.DateTime> 对象。</span><span class="sxs-lookup"><span data-stu-id="12304-207">A <xref:System.DateTime> object.</span></span> <span data-ttu-id="12304-208">这会删除早于指定日期和时间的所有令牌的信息。</span><span class="sxs-lookup"><span data-stu-id="12304-208">This deletes information for all tokens older than the specified date and time.</span></span>  
  
###  <a name="PShellExample"></a>  
