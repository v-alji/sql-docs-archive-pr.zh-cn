---
title: 订阅发布 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.conc.subtopubs.f1
helpviewer_keywords:
- subscriptions [SQL Server replication], about subscriptions
- pull subscriptions [SQL Server replication]
- subscriptions [SQL Server replication]
- push subscriptions [SQL Server replication], about push subscriptions
- merge replication subscribing [SQL Server replication]
- merge replication subscribing [SQL Server replication], about subscribing
- publications [SQL Server replication], subscribing
- push subscriptions [SQL Server replication]
- pull subscriptions [SQL Server replication], about pull subscriptions
- snapshot replication [SQL Server], subscribing
- transactional replication, subscribing
ms.assetid: 088ee30a-05ab-47c4-92ed-316b93e12445
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c565aae26c6d549eb67043168797d5fb059c8e2a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577503"
---
# <a name="subscribe-to-publications"></a><span data-ttu-id="f044f-102">订阅发布</span><span class="sxs-lookup"><span data-stu-id="f044f-102">Subscribe to Publications</span></span>
  <span data-ttu-id="f044f-103">订阅是对发布中的数据和数据库对象的副本的请求。</span><span class="sxs-lookup"><span data-stu-id="f044f-103">A subscription is a request for a copy of the data and database objects in a publication.</span></span> <span data-ttu-id="f044f-104">订阅定义将接收哪个发布以及接收的时间和位置。</span><span class="sxs-lookup"><span data-stu-id="f044f-104">A subscription defines which publication will be received, and where and when it will be received.</span></span> <span data-ttu-id="f044f-105">在计划订阅时，请考虑代理处理发生的位置。</span><span class="sxs-lookup"><span data-stu-id="f044f-105">When planning for subscriptions, consider where you want agent processing to occur.</span></span> <span data-ttu-id="f044f-106">所选择的订阅类型将控制代理运行的位置。</span><span class="sxs-lookup"><span data-stu-id="f044f-106">The type of subscription you choose controls where the agent runs.</span></span> <span data-ttu-id="f044f-107">对于推送订阅，合并代理或分发代理在分发服务器上运行；对于请求订阅，代理在订阅服务器上运行。</span><span class="sxs-lookup"><span data-stu-id="f044f-107">With a push subscription, the Merge Agent or Distribution Agent runs at the Distributor, whereas with a pull subscription, agents run at the Subscribers.</span></span> <span data-ttu-id="f044f-108">创建订阅后，将无法更改其类型。</span><span class="sxs-lookup"><span data-stu-id="f044f-108">After a subscription is created, it cannot be changed from one type to another.</span></span>  
  
|<span data-ttu-id="f044f-109">订阅</span><span class="sxs-lookup"><span data-stu-id="f044f-109">Subscription</span></span>|<span data-ttu-id="f044f-110">特征</span><span class="sxs-lookup"><span data-stu-id="f044f-110">Characteristics</span></span>|<span data-ttu-id="f044f-111">使用时间</span><span class="sxs-lookup"><span data-stu-id="f044f-111">Use When</span></span>|  
|------------------|---------------------|--------------|  
|<span data-ttu-id="f044f-112">推送订阅</span><span class="sxs-lookup"><span data-stu-id="f044f-112">Push Subscription</span></span>|<span data-ttu-id="f044f-113">对于推送订阅，发布服务器将更改传播到订阅服务器，而无需订阅服务器发出请求。</span><span class="sxs-lookup"><span data-stu-id="f044f-113">With a push subscription, the Publisher propagates changes to a Subscriber without a request from the Subscriber.</span></span> <span data-ttu-id="f044f-114">更改可以按需、连续地或按照计划推送到订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="f044f-114">Changes can be pushed to Subscribers on demand, continuously, or on a scheduled basis.</span></span> <span data-ttu-id="f044f-115">分发代理或合并代理在分发服务器上运行。</span><span class="sxs-lookup"><span data-stu-id="f044f-115">The Distribution Agent or Merge Agent runs at the Distributor.</span></span>|<span data-ttu-id="f044f-116">通常，数据将连续同步或按照经常重复执行的计划同步。</span><span class="sxs-lookup"><span data-stu-id="f044f-116">Data will typically be synchronized continuously or on a frequently recurring schedule.</span></span><br /><br /> <span data-ttu-id="f044f-117">发布要求数据近似实时地移动。</span><span class="sxs-lookup"><span data-stu-id="f044f-117">Publications require near real-time movement of data.</span></span><br /><br /> <span data-ttu-id="f044f-118">分发服务器上较高的处理器开销不会影响性能。</span><span class="sxs-lookup"><span data-stu-id="f044f-118">The higher processor overhead at the Distributor does not affect performance.</span></span><br /><br /> <span data-ttu-id="f044f-119">通常与快照和事务复制一起使用。</span><span class="sxs-lookup"><span data-stu-id="f044f-119">Most often used with snapshot and transactional replication.</span></span>|  
|<span data-ttu-id="f044f-120">请求订阅</span><span class="sxs-lookup"><span data-stu-id="f044f-120">Pull Subscription</span></span>|<span data-ttu-id="f044f-121">对于请求订阅，订阅服务器请求在发布服务器上所做的更改。</span><span class="sxs-lookup"><span data-stu-id="f044f-121">With a pull subscription, the Subscriber requests changes made at the Publisher.</span></span> <span data-ttu-id="f044f-122">请求订阅允许订阅服务器上的用户确定同步数据更改的时间。</span><span class="sxs-lookup"><span data-stu-id="f044f-122">Pull subscriptions allow the user at the Subscriber to determine when the data changes are synchronized.</span></span> <span data-ttu-id="f044f-123">分发代理或合并代理在订阅服务器上运行。</span><span class="sxs-lookup"><span data-stu-id="f044f-123">The Distribution Agent or the Merge Agent runs at the Subscriber.</span></span>|<span data-ttu-id="f044f-124">数据通常按需或按计划同步，而非连续同步。</span><span class="sxs-lookup"><span data-stu-id="f044f-124">Data will typically be synchronized on demand or on a schedule rather than continuously.</span></span><br /><br /> <span data-ttu-id="f044f-125">发布具有大量订阅服务器，并且/或在分发服务器上运行所有代理会消耗大量资源。</span><span class="sxs-lookup"><span data-stu-id="f044f-125">The publication has a large number of Subscribers, and/or it would be too resource-intensive to run all the agents at the Distributor.</span></span><br /><br /> <span data-ttu-id="f044f-126">订阅服务器是自主的、断开连接的和/或移动的。</span><span class="sxs-lookup"><span data-stu-id="f044f-126">Subscribers are autonomous, disconnected, and/or mobile.</span></span> <span data-ttu-id="f044f-127">订阅服务器将确定连接和同步更改的时间。</span><span class="sxs-lookup"><span data-stu-id="f044f-127">Subscribers will determine when they will connect and synchronize changes.</span></span><br /><br /> <span data-ttu-id="f044f-128">通常与合并复制一起使用。</span><span class="sxs-lookup"><span data-stu-id="f044f-128">Most often used with merge replication.</span></span>|  
  
## <a name="merge-replication-subscription-types"></a><span data-ttu-id="f044f-129">合并复制订阅类型</span><span class="sxs-lookup"><span data-stu-id="f044f-129">Merge Replication Subscription Types</span></span>  
 <span data-ttu-id="f044f-130">所有复制类型都允许推送订阅和请求订阅。</span><span class="sxs-lookup"><span data-stu-id="f044f-130">All replication types allow push and pull subscriptions.</span></span> <span data-ttu-id="f044f-131">合并复制使用另外两个术语来区分订阅：客户端订阅和服务器订阅。</span><span class="sxs-lookup"><span data-stu-id="f044f-131">Merge replication uses two additional terms to distinguish subscriptions: client subscriptions and server subscriptions.</span></span> <span data-ttu-id="f044f-132">客户端订阅和服务器订阅类型都可用于推送订阅和请求订阅。</span><span class="sxs-lookup"><span data-stu-id="f044f-132">Both client and server subscription types can be used with push and pull subscriptions.</span></span> <span data-ttu-id="f044f-133">客户端订阅适合于大多数订阅服务器，而服务器订阅通常用于向其他订阅服务器重新发布数据的订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="f044f-133">Client subscriptions are appropriate for most Subscribers, whereas server subscriptions are typically used for Subscribers that republish data to other Subscribers.</span></span> <span data-ttu-id="f044f-134">订阅选择还会影响冲突解决。</span><span class="sxs-lookup"><span data-stu-id="f044f-134">Subscription choice also affects conflict resolution.</span></span>  
  
## <a name="non-sql-server-subscribers"></a><span data-ttu-id="f044f-135">Non-SQL Server Subscribers</span><span class="sxs-lookup"><span data-stu-id="f044f-135">Non-SQL Server Subscribers</span></span>  
 <span data-ttu-id="f044f-136">Oracle 和 IBM DB2 可以使用推送订阅来订阅快照和事务发布。</span><span class="sxs-lookup"><span data-stu-id="f044f-136">Oracle and IBM DB2 can subscribe to snapshot and transactional publications using push subscriptions.</span></span> <span data-ttu-id="f044f-137">有关详细信息，请参阅 [Non-SQL Server Subscribers](non-sql/non-sql-server-subscribers.md)。</span><span class="sxs-lookup"><span data-stu-id="f044f-137">For more information, see [Non-SQL Server Subscribers](non-sql/non-sql-server-subscribers.md).</span></span>  
  
## <a name="creating-subscriptions"></a><span data-ttu-id="f044f-138">创建订阅</span><span class="sxs-lookup"><span data-stu-id="f044f-138">Creating Subscriptions</span></span>  
 <span data-ttu-id="f044f-139">若要创建订阅，请提供下列信息：</span><span class="sxs-lookup"><span data-stu-id="f044f-139">To create a subscription, you supply the following information:</span></span>  
  
-   <span data-ttu-id="f044f-140">发布的名称。</span><span class="sxs-lookup"><span data-stu-id="f044f-140">The name of the publication.</span></span>  
  
-   <span data-ttu-id="f044f-141">订阅服务器和订阅数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="f044f-141">The name of the Subscriber and the subscription database.</span></span>  
  
-   <span data-ttu-id="f044f-142">分发代理或合并代理是在分发服务器上运行还是在订阅服务器上运行。</span><span class="sxs-lookup"><span data-stu-id="f044f-142">Whether the Distribution Agent or Merge Agent runs at the Distributor or at the Subscriber.</span></span>  
  
-   <span data-ttu-id="f044f-143">分发代理或合并代理是连续运行、按照计划运行，还是仅按需运行。</span><span class="sxs-lookup"><span data-stu-id="f044f-143">Whether the Distribution Agent or Merge Agent runs continuously, on a scheduled basis, or on demand only.</span></span>  
  
-   <span data-ttu-id="f044f-144">快照代理是否应为订阅创建初始快照，以及分发代理或合并代理是否应在订阅服务器上应用该快照。</span><span class="sxs-lookup"><span data-stu-id="f044f-144">Whether the Snapshot Agent should create an initial snapshot for the subscription and whether the Distribution Agent or Merge Agent should apply that snapshot at the Subscriber.</span></span>  
  
-   <span data-ttu-id="f044f-145">将运行分发代理或合并代理的帐户。</span><span class="sxs-lookup"><span data-stu-id="f044f-145">Accounts under which the Distribution Agent or Merge Agent will run.</span></span>  
  
-   <span data-ttu-id="f044f-146">对于合并复制，还要提供订阅类型：服务器或客户端。</span><span class="sxs-lookup"><span data-stu-id="f044f-146">For merge replication, the type of subscription: server or client.</span></span>  
  
 <span data-ttu-id="f044f-147">**创建推送订阅**</span><span class="sxs-lookup"><span data-stu-id="f044f-147">**To create a push subscription**</span></span>  
  
 [<span data-ttu-id="f044f-148">创建推送订阅</span><span class="sxs-lookup"><span data-stu-id="f044f-148">Create a Push Subscription</span></span>](create-a-push-subscription.md)  
  
 <span data-ttu-id="f044f-149">**查看或修改推送订阅属性**</span><span class="sxs-lookup"><span data-stu-id="f044f-149">**To view or modify push subscription properties**</span></span>  
  
 [<span data-ttu-id="f044f-150">查看和修改推送订阅属性</span><span class="sxs-lookup"><span data-stu-id="f044f-150">View and Modify Push Subscription Properties</span></span>](view-and-modify-push-subscription-properties.md)  
  
 <span data-ttu-id="f044f-151">**删除推送订阅**</span><span class="sxs-lookup"><span data-stu-id="f044f-151">**To delete a push subscription**</span></span>  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]<span data-ttu-id="f044f-152">：[删除推送订阅](delete-a-push-subscription.md)</span><span class="sxs-lookup"><span data-stu-id="f044f-152">: [Delete a Push Subscription](delete-a-push-subscription.md)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f044f-153">删除订阅不会从订阅服务器中删除已发布的对象。</span><span class="sxs-lookup"><span data-stu-id="f044f-153">Deleting a subscription does not remove published objects from the Subscriber.</span></span>  
  
 <span data-ttu-id="f044f-154">**创建请求订阅**</span><span class="sxs-lookup"><span data-stu-id="f044f-154">**To create a pull subscription**</span></span>  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]<span data-ttu-id="f044f-155">：[创建请求订阅](create-a-pull-subscription.md)</span><span class="sxs-lookup"><span data-stu-id="f044f-155">: [Create a Pull Subscription](create-a-pull-subscription.md)</span></span>  
  
 <span data-ttu-id="f044f-156">**查看或修改请求订阅属性**</span><span class="sxs-lookup"><span data-stu-id="f044f-156">**To view or modify pull subscription properties**</span></span>  
  
 [<span data-ttu-id="f044f-157">查看和修改请求订阅属性</span><span class="sxs-lookup"><span data-stu-id="f044f-157">View and Modify Pull Subscription Properties</span></span>](view-and-modify-pull-subscription-properties.md)  
  
 <span data-ttu-id="f044f-158">**删除请求订阅**</span><span class="sxs-lookup"><span data-stu-id="f044f-158">**To delete a pull subscription**</span></span>  
  
 [<span data-ttu-id="f044f-159">删除请求订阅</span><span class="sxs-lookup"><span data-stu-id="f044f-159">Delete a Pull Subscription</span></span>](delete-a-pull-subscription.md)  
  
## <a name="see-also"></a><span data-ttu-id="f044f-160">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f044f-160">See Also</span></span>  
 <span data-ttu-id="f044f-161">[保护订阅服务器](security/secure-the-subscriber.md) </span><span class="sxs-lookup"><span data-stu-id="f044f-161">[Secure the Subscriber](security/secure-the-subscriber.md) </span></span>  
 [<span data-ttu-id="f044f-162">订阅过期和停用</span><span class="sxs-lookup"><span data-stu-id="f044f-162">Subscription Expiration and Deactivation</span></span>](subscription-expiration-and-deactivation.md)  
  
  
