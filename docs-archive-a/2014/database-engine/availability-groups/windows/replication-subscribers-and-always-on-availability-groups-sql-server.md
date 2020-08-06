---
title: 复制订阅服务器和 AlwaysOn 可用性组 (SQL Server) |Microsoft Docs
ms.custom: ''
ms.date: 01/16/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- failover subscribers with AlwaysOn
- Availability Groups [SQL Server], interoperability
- replication [SQL Server], AlwaysOn Availability Groups
ms.assetid: 0995f269-0580-43ed-b8bf-02b9ad2d7ee6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 449b5ac416f2ae86395c40a984678ed4258b3b85
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587605"
---
# <a name="replication-subscribers-and-alwayson-availability-groups-sql-server"></a><span data-ttu-id="63c3b-102">复制订阅服务器和 AlwaysOn 可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="63c3b-102">Replication Subscribers and AlwaysOn Availability Groups (SQL Server)</span></span>
  <span data-ttu-id="63c3b-103">当包含作为复制订阅服务器的数据库的 AlwaysOn 可用性组发生故障转移时，复制订阅可能会失败。</span><span class="sxs-lookup"><span data-stu-id="63c3b-103">When an AlwaysOn availability group containing a database that is a replication subscriber fails over, the replication subscription might fail.</span></span> <span data-ttu-id="63c3b-104">对于事务复制推送订阅服务器，如果订阅是使用 AG 侦听器名称创建的，则在故障转移后，分发代理会自动继续复制。</span><span class="sxs-lookup"><span data-stu-id="63c3b-104">For transactional replication push subscribers, the distribution agent will continue to replicate automatically after a failover if the subscription was created using the AG listener name.</span></span> <span data-ttu-id="63c3b-105">对于事务复制拉取订阅服务器，如果订阅是使用 AG 侦听器名称创建的，且原始订阅服务器已启动并正在运行，则在故障转移后，分发代理会自动继续复制。</span><span class="sxs-lookup"><span data-stu-id="63c3b-105">For transactional replication pull subscribers, the distribution agent will continue to replicate automatically after a failover, if the subscription was created using the AG listener name and the original subscriber server is up and running.</span></span> <span data-ttu-id="63c3b-106">这是因为仅在原始订阅服务器（AG 的主要副本）上创建分发代理作业。</span><span class="sxs-lookup"><span data-stu-id="63c3b-106">This is because the distribution agent jobs only get created on the original subscriber (primary replica of the AG).</span></span> <span data-ttu-id="63c3b-107">对于合并订阅服务器，复制管理员必须通过重新创建订阅手动重新配置订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="63c3b-107">For merge subscribers, a replication administrator must manually reconfigure the subscriber, by recreating the subscription.</span></span>  
  
## <a name="what-is-supported"></a><span data-ttu-id="63c3b-108">支持的操作</span><span class="sxs-lookup"><span data-stu-id="63c3b-108">What is Supported</span></span>  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="63c3b-109">复制支持订阅服务器的自动故障转移、事务订阅服务器的自动故障转移以及合并订阅服务器的手动故障转移。</span><span class="sxs-lookup"><span data-stu-id="63c3b-109">replication supports the automatic failover of the publisher, the automatic failover of transactional subscribers, and the manual failover of merge subscribers.</span></span> <span data-ttu-id="63c3b-110">不支持可用性数据库上分发服务器的故障转移。</span><span class="sxs-lookup"><span data-stu-id="63c3b-110">The failover of a distributor on an availability database is not supported.</span></span> <span data-ttu-id="63c3b-111">AlwaysOn 不能与 Websync 和[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Compact 应用场景结合使用。</span><span class="sxs-lookup"><span data-stu-id="63c3b-111">AlwaysOn cannot be combined with Websync and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Compact scenarios.</span></span>  
  
 <span data-ttu-id="63c3b-112">**合并请求订阅的故障转移**</span><span class="sxs-lookup"><span data-stu-id="63c3b-112">**Failover of a Merge Pull Subscription**</span></span>  
  
 <span data-ttu-id="63c3b-113">进行可用性组故障转移时请求订阅失败，因为请求代理找不到承载主副本的服务器实例的 **msdb** 数据库中存储的作业；由于服务器实例失败该作业不可用。</span><span class="sxs-lookup"><span data-stu-id="63c3b-113">A pull subscription fails upon availability group failover, because pull agent cannot find the jobs stored in the **msdb** database of the server instance that hosts the primary replica; which is not available because the server instance has failed.</span></span>  
  
 <span data-ttu-id="63c3b-114">**合并推送订阅的故障转移**</span><span class="sxs-lookup"><span data-stu-id="63c3b-114">**Failover of a Merge Push Subscription**</span></span>  
  
 <span data-ttu-id="63c3b-115">进行可用性组故障转移时推送订阅失败，因为推送代理无法连接到原始订阅服务器上的原始订阅数据库。</span><span class="sxs-lookup"><span data-stu-id="63c3b-115">A push subscription fails upon availability group failover, because the push agent can no longer connect to original subscription database on original subscriber.</span></span>  
  
## <a name="how-to-create-transactional-subscription-in-an-alwayson-environment"></a><span data-ttu-id="63c3b-116">如何在 AlwaysOn 环境中创建事务订阅</span><span class="sxs-lookup"><span data-stu-id="63c3b-116">How to Create Transactional Subscription in an AlwaysOn Environment</span></span>  
 <span data-ttu-id="63c3b-117">对于事务复制，请执行以下步骤配置订阅服务器可用性组并对其进行故障转移：</span><span class="sxs-lookup"><span data-stu-id="63c3b-117">For transactional replication, use the following steps to configure and failover a subscriber availability group:</span></span>  
  
1.  <span data-ttu-id="63c3b-118">在创建订阅之前，请将订阅服务器数据库添加到相应的 AlwaysOn 可用性组。</span><span class="sxs-lookup"><span data-stu-id="63c3b-118">Before creating the subscription, add the subscriber database to the appropriate AlwaysOn availability group.</span></span>  
  
2.  <span data-ttu-id="63c3b-119">将订阅服务器的可用性组侦听器作为链接服务器添加到可用性组的所有节点。</span><span class="sxs-lookup"><span data-stu-id="63c3b-119">Add the subscriber's availability group Listener as a linked server to all nodes of the availability group.</span></span> <span data-ttu-id="63c3b-120">此步骤可确保所有潜在故障转移伙伴能够知道并连接到侦听器。</span><span class="sxs-lookup"><span data-stu-id="63c3b-120">This step ensures that all potential failover partners are aware of and can connect to the listener.</span></span>  
  
3.  <span data-ttu-id="63c3b-121">使用下列 **创建事务复制推送订阅** 部分中的脚本，并使用订阅服务器的可用性组侦听器的名称创建订阅。</span><span class="sxs-lookup"><span data-stu-id="63c3b-121">Using the script in the **Creating a Transactional Replication Push Subscription** section below, create the subscription using the name of the availability group listener of the subscriber.</span></span> <span data-ttu-id="63c3b-122">在进行故障转移后，侦听器名称将始终有效，并且订阅服务器的实际服务器名称将取决于成为新的主节点的实际节点。</span><span class="sxs-lookup"><span data-stu-id="63c3b-122">After a failover, the listener name will always remain valid, whereas the actual server name of the subscriber will depend on the actual node that became the new primary.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="63c3b-123">订阅必须通过使用 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 脚本创建，不能使用 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]创建。</span><span class="sxs-lookup"><span data-stu-id="63c3b-123">The subscription must be created by using a [!INCLUDE[tsql](../../../includes/tsql-md.md)] script and cannot be created using [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)].</span></span>  
  
4.  <span data-ttu-id="63c3b-124">如果创建请求订阅：</span><span class="sxs-lookup"><span data-stu-id="63c3b-124">If creating a pull subscription:</span></span>  
  
    1.  <span data-ttu-id="63c3b-125">在 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]中的主订阅服务器节点上，打开 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 代理树。</span><span class="sxs-lookup"><span data-stu-id="63c3b-125">In [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], on the primary subscriber node, open the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent tree.</span></span>  
  
    2.  <span data-ttu-id="63c3b-126">确定 **“请求分发代理”** 作业并编辑该作业。</span><span class="sxs-lookup"><span data-stu-id="63c3b-126">Identify the **Pull Distribution Agent** job and edit the job.</span></span>  
  
    3.  <span data-ttu-id="63c3b-127">在 **“运行代理”** 作业步骤中，检查 `-Publisher` 和 `-Distributor` 参数。</span><span class="sxs-lookup"><span data-stu-id="63c3b-127">On the **Run Agent** job step, check the `-Publisher` and `-Distributor` parameters.</span></span> <span data-ttu-id="63c3b-128">确保这些参数包含发布服务器和分发服务器的正确的直接服务器和实例名称。</span><span class="sxs-lookup"><span data-stu-id="63c3b-128">Make sure that these parameters contain the correct direct server and instance names of the publisher and distributor server.</span></span>  
  
    4.  <span data-ttu-id="63c3b-129">将 `-Subscriber` 参数更改为订阅服务器的可用性组侦听器名称。</span><span class="sxs-lookup"><span data-stu-id="63c3b-129">Change the `-Subscriber` parameter to the subscriber's availability group listener name.</span></span>  
  
 <span data-ttu-id="63c3b-130">如果按照这些步骤创建订阅，则无需在故障转移后执行任何操作。</span><span class="sxs-lookup"><span data-stu-id="63c3b-130">When you create your subscription following these steps, then you won't have to do anything after a failover.</span></span>  
  
## <a name="creating-a-transactional-replication-push-subscription"></a><span data-ttu-id="63c3b-131">创建事务复制推送订阅</span><span class="sxs-lookup"><span data-stu-id="63c3b-131">Creating a Transactional Replication Push Subscription</span></span>  
  
```  
-- commands to execute at the publisher, in the publisher database:  
use [<publisher database name>]  
EXEC sp_addsubscription @publication = N'<publication name>',   
       @subscriber = N'<availability group listener name>',   
       @destination_db = N'<subscriber database name>',   
       @subscription_type = N'Push',   
       @sync_type = N'automatic', @article = N'all', @update_mode = N'read only', @subscriber_type = 0;  
GO  
  
EXEC sp_addpushsubscription_agent @publication = N'<publication name>',   
       @subscriber = N'<availability group listener name>',   
       @subscriber_db = N'<subscriber database name>',   
       @job_login = null, @job_password = null, @subscriber_security_mode = 1;  
GO  
```  
  
## <a name="to-resume-the-merge-agents-after-the-availability-group-of-the-subscriber-fails-over"></a><span data-ttu-id="63c3b-132">在订阅服务器可用性组发生故障转移后恢复合并代理</span><span class="sxs-lookup"><span data-stu-id="63c3b-132">To Resume the Merge Agents After the Availability Group of the Subscriber Fails Over</span></span>  
 <span data-ttu-id="63c3b-133">进行合并复制时，复制管理员必须手动重新配置订阅服务器，步骤如下：</span><span class="sxs-lookup"><span data-stu-id="63c3b-133">For merge replication, a replication administrator must manually reconfigure the subscriber with the following steps:</span></span>  
  
1.  <span data-ttu-id="63c3b-134">执行 `sp_subscription_cleanup` 删除订阅服务器的旧订阅。</span><span class="sxs-lookup"><span data-stu-id="63c3b-134">Execute `sp_subscription_cleanup` to remove the old subscription for the subscriber.</span></span> <span data-ttu-id="63c3b-135">在新的主副本（以前为辅助副本）上执行此操作。</span><span class="sxs-lookup"><span data-stu-id="63c3b-135">Perform this action on the new primary replica (which was formerly the secondary replica).</span></span>  
  
2.  <span data-ttu-id="63c3b-136">通过从新快照开始创建新订阅来重新创建订阅。</span><span class="sxs-lookup"><span data-stu-id="63c3b-136">Recreate the subscription by creating a new subscription, beginning with a new snapshot.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="63c3b-137">当前过程对于合并复制订阅服务器是不方便的，不过，合并复制的主要应用场景是断开连接的用户（台式机、笔记本电脑、手机设备），它们不使用订阅服务器上的 AlwaysOn 可用性组。</span><span class="sxs-lookup"><span data-stu-id="63c3b-137">The current process is inconvenient for merge replication subscribers, however the main scenario for merge replication is disconnected users (desktops, laptops, handset devices) which will not use AlwaysOn availability groups on the subscriber.</span></span>  
  
  
