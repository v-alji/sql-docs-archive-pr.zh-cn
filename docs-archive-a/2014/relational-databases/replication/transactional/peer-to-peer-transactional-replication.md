---
title: 对等事务复制 | Microsoft Docs
ms.custom: ''
ms.date: 08/29/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- bidirectional replication
- transactional replication, bidirectional replication
- bidirectional transactional replication
- transactional replication, peer-to-peer replication
- peer-to-peer transactional replication
ms.assetid: 23e7e8c1-002f-4e69-8c99-d63e4100de64
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f61db9a8e7cecb107fd1b27fae966d133e043c8b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587329"
---
# <a name="peer-to-peer-transactional-replication"></a><span data-ttu-id="199eb-102">@loopback_detection</span><span class="sxs-lookup"><span data-stu-id="199eb-102">Peer-to-Peer Transactional Replication</span></span>
  <span data-ttu-id="199eb-103">对等复制通过在多个服务器实例（又称为“节点” ）上维护数据副本，提供了一种扩展的高可用性解决方案。</span><span class="sxs-lookup"><span data-stu-id="199eb-103">Peer-to-peer replication provides a scale-out and high-availability solution by maintaining copies of data across multiple server instances, also referred to as *nodes*.</span></span> <span data-ttu-id="199eb-104">对等复制建立在事务复制的基础之上，以事务方式近乎实时地传播一致的更改。</span><span class="sxs-lookup"><span data-stu-id="199eb-104">Built on the foundation of transactional replication, peer-to-peer replication propagates transactionally consistent changes in near real-time.</span></span> <span data-ttu-id="199eb-105">这样，需要扩展读取操作的应用程序就可以将来自客户端的读取操作分布到多个节点上。</span><span class="sxs-lookup"><span data-stu-id="199eb-105">This enables applications that require scale-out of read operations to distribute the reads from clients across multiple nodes.</span></span> <span data-ttu-id="199eb-106">由于对等复制以近乎实时的方式维护节点上的数据，从而提供了数据冗余，提高了数据的可用性。</span><span class="sxs-lookup"><span data-stu-id="199eb-106">Because data is maintained across the nodes in near real-time, peer-to-peer replication provides data redundancy, which increases the availability of data.</span></span>  
  
 <span data-ttu-id="199eb-107">请考虑 Web 应用程序的情况。</span><span class="sxs-lookup"><span data-stu-id="199eb-107">Consider a Web application.</span></span> <span data-ttu-id="199eb-108">它可以通过以下方式从对等复制中获益：</span><span class="sxs-lookup"><span data-stu-id="199eb-108">This can benefit from peer-to-peer replication in the following ways:</span></span>  
  
-   <span data-ttu-id="199eb-109">目录查询和其他读取操作被分散到多个节点上。</span><span class="sxs-lookup"><span data-stu-id="199eb-109">Catalog queries and other reads are spread across multiple nodes.</span></span> <span data-ttu-id="199eb-110">这样，当读取操作增多时，仍能够保持原有的性能。</span><span class="sxs-lookup"><span data-stu-id="199eb-110">This enables performance to remain consistent as reads increase.</span></span>  
  
-   <span data-ttu-id="199eb-111">如果系统中的某个节点失效，应用层可将该节点的写入操作重定向到其他节点。</span><span class="sxs-lookup"><span data-stu-id="199eb-111">If one of the nodes in the system fails, an application layer can redirect the writes for that node to another node.</span></span> <span data-ttu-id="199eb-112">这样便可保持可用性。</span><span class="sxs-lookup"><span data-stu-id="199eb-112">This maintains availability.</span></span>  
  
-   <span data-ttu-id="199eb-113">如果节点需要维护或整个系统需要升级，则可以将各个节点脱机并在完成操作后再将其重新添加回系统中，而不影响到应用程序的可用性。</span><span class="sxs-lookup"><span data-stu-id="199eb-113">If a node requires maintenance or the whole system requires an upgrade, each node can be taken offline and added back to the system without affecting the availability of the application.</span></span>  
  
 <span data-ttu-id="199eb-114">虽然对等复制可扩展读取操作，但对于单个节点而言，该拓扑的写入性能也同样出色。</span><span class="sxs-lookup"><span data-stu-id="199eb-114">Although peer-to-peer replication enables scaling out of read operations, write performance for the topology is like that for a single node.</span></span> <span data-ttu-id="199eb-115">这是因为所有的插入、更新和删除操作最终都会传播到所有节点上。</span><span class="sxs-lookup"><span data-stu-id="199eb-115">This is because ultimately all inserts, updates, and deletes are propagated to all nodes.</span></span> <span data-ttu-id="199eb-116">复制可识别出更改已应用于给定节点这一情况，避免在节点间多次循环应用更改。</span><span class="sxs-lookup"><span data-stu-id="199eb-116">Replication recognizes when a change has been applied to a given node and prevents changes from cycling through the nodes more than one time.</span></span> <span data-ttu-id="199eb-117">强烈建议仅在节点上执行每一行的写入操作，理由如下：</span><span class="sxs-lookup"><span data-stu-id="199eb-117">We strongly recommend that write operations for each row be performed at only node, for the following reasons:</span></span>  
  
-   <span data-ttu-id="199eb-118">如果在多个节点上修改了某一行，则将该行传播给其他节点时会导致冲突甚至丢失更新。</span><span class="sxs-lookup"><span data-stu-id="199eb-118">If a row is modified at more than one node, it can cause a conflict or even a lost update when the row is propagated to other nodes.</span></span>  
  
-   <span data-ttu-id="199eb-119">复制更改时总是存在一定的延迟。</span><span class="sxs-lookup"><span data-stu-id="199eb-119">There is always some latency involved when changes are replicated.</span></span> <span data-ttu-id="199eb-120">对于要求立即显示最新更改的应用程序而言，在多个节点上对应用程序执行动态负载平衡可能会出现问题。</span><span class="sxs-lookup"><span data-stu-id="199eb-120">For applications that require the latest change to be seen immediately, dynamically load balancing the application across multiple nodes can be problematic.</span></span>  
  
 <span data-ttu-id="199eb-121">对等复制包括了在对等拓扑中启用冲突检测的选项。</span><span class="sxs-lookup"><span data-stu-id="199eb-121">Peer-to-peer replication includes the option to enable conflict detection across a peer-to-peer topology.</span></span> <span data-ttu-id="199eb-122">此选项有助于防止因未检测到的冲突引起的各种问题，包括不一致的应用程序行为和丢失更新。</span><span class="sxs-lookup"><span data-stu-id="199eb-122">This option helps prevent the issues that are caused from undetected conflicts, including inconsistent application behavior and lost updates.</span></span> <span data-ttu-id="199eb-123">启用该选项后，默认情况下，发生冲突的更改被视为导致分发代理失败的关键错误。</span><span class="sxs-lookup"><span data-stu-id="199eb-123">By enabling this option, by default a conflicting change is treated as a critical error that causes the failure of the Distribution Agent.</span></span> <span data-ttu-id="199eb-124">发生冲突时，拓扑将始终处于不一致的状态，直至手动解决冲突并使拓扑中的数据一致。</span><span class="sxs-lookup"><span data-stu-id="199eb-124">In the event of a conflict, the topology remains in an inconsistent state until the conflict is resolved manually and the data is made consistent across the topology.</span></span> <span data-ttu-id="199eb-125">有关详细信息，请参阅 [Conflict Detection in Peer-to-Peer Replication](peer-to-peer-conflict-detection-in-peer-to-peer-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="199eb-125">For more information, see [Conflict Detection in Peer-to-Peer Replication](peer-to-peer-conflict-detection-in-peer-to-peer-replication.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="199eb-126">为了避免潜在的数据不一致性，即便已经启用了冲突检测功能，也应尽力避免对等拓扑中发生冲突。</span><span class="sxs-lookup"><span data-stu-id="199eb-126">To avoid potential data inconsistency, make sure that you avoid conflicts in a peer-to-peer topology, even with conflict detection enabled.</span></span> <span data-ttu-id="199eb-127">为了确保仅在某一个节点上执行特定行的写入操作，访问并更改数据的应用程序必须对其插入、更新和删除操作进行分区。</span><span class="sxs-lookup"><span data-stu-id="199eb-127">To ensure that write operations for a particular row are performed at only one node, applications that access and change data must partition insert, update, and delete operations.</span></span> <span data-ttu-id="199eb-128">分区可确保在一个节点上对给定行的修改可以在其他节点修改该行之前，与拓扑中所有其他节点同步。</span><span class="sxs-lookup"><span data-stu-id="199eb-128">This partitioning ensures that modifications to a given row originating at one node are synchronized with all other nodes in the topology before the row is modified by a different node.</span></span> <span data-ttu-id="199eb-129">如果应用程序需要完善的冲突检测与解决功能，请使用合并复制。</span><span class="sxs-lookup"><span data-stu-id="199eb-129">If an application requires sophisticated conflict detection and resolution capabilities, use merge replication.</span></span> <span data-ttu-id="199eb-130">有关详细信息，请参阅[合并复制](../merge/merge-replication.md)和[检测并解决合并复制冲突](../merge/advanced-merge-replication-conflict-detection-and-resolution.md)。</span><span class="sxs-lookup"><span data-stu-id="199eb-130">For more information, see [Merge Replication](../merge/merge-replication.md) and [Detect and Resolve Merge Replication Conflicts](../merge/advanced-merge-replication-conflict-detection-and-resolution.md).</span></span>  
  
## <a name="peer-to-peer-topologies"></a><span data-ttu-id="199eb-131">对等拓扑</span><span class="sxs-lookup"><span data-stu-id="199eb-131">Peer-to-Peer Topologies</span></span>  
 <span data-ttu-id="199eb-132">下列方案说明了对等复制的典型应用。</span><span class="sxs-lookup"><span data-stu-id="199eb-132">The following scenarios illustrate typical uses for peer-to-peer replication.</span></span>  
  
### <a name="topology-that-has-two-participating-databases"></a><span data-ttu-id="199eb-133">包含两个参与数据库的拓扑</span><span class="sxs-lookup"><span data-stu-id="199eb-133">Topology That Has Two Participating Databases</span></span>  
 <span data-ttu-id="199eb-134">![对等复制，双节点](../media/repl-multinode-01.gif "对等复制，双节点")</span><span class="sxs-lookup"><span data-stu-id="199eb-134">![Peer-to-peer replication, two nodes](../media/repl-multinode-01.gif "Peer-to-peer replication, two nodes")</span></span>  
  
 <span data-ttu-id="199eb-135">上面两张图均显示了两个参与数据库，其中通过应用程序服务器将用户流量定向到数据库。</span><span class="sxs-lookup"><span data-stu-id="199eb-135">Both of the preceding illustrations show two participating databases, with user traffic directed to the databases through an application server.</span></span> <span data-ttu-id="199eb-136">此配置可用于从网站到工作组应用程序等多种应用程序，并具有下列优点：</span><span class="sxs-lookup"><span data-stu-id="199eb-136">This configuration can be used for a variety of applications, from Web sites to workgroup applications, and provides the following benefits:</span></span>  
  
-   <span data-ttu-id="199eb-137">由于将读取操作分散到两台服务器上，因此提高了读取的性能。</span><span class="sxs-lookup"><span data-stu-id="199eb-137">Improved read performance, because reads are spread out over two servers.</span></span>  
  
-   <span data-ttu-id="199eb-138">当需要维护或某一节点出现故障时，可以提供更高的可用性。</span><span class="sxs-lookup"><span data-stu-id="199eb-138">Higher availability if maintenance is required or in case of failure at one node.</span></span>  
  
 <span data-ttu-id="199eb-139">从这两张图中可以看到，读取活动在参与数据库间进行负载平衡，但更新的处理方式则有所不同：</span><span class="sxs-lookup"><span data-stu-id="199eb-139">In both illustrations, read activity is load-balanced between the participating databases, but updates are handled differently:</span></span>  
  
-   <span data-ttu-id="199eb-140">在左图中，在两台服务器间对更新进行了分区。</span><span class="sxs-lookup"><span data-stu-id="199eb-140">On the left, updates are partitioned between the two servers.</span></span> <span data-ttu-id="199eb-141">例如，如果数据库包含产品目录，则可以令自定义应用程序把对名称以 A-M 开头的产品进行的更新定向到节点 **A** ，把对名称以 N-Z 开头的产品进行的更新定向到节点 **B** 。然后将更新复制到另一个节点。</span><span class="sxs-lookup"><span data-stu-id="199eb-141">If the database contained a product catalog, you could, for example, have a custom application direct updates to node **A** for product names that start with A through M, and direct updates to node **B** for product names that start with N through Z. Updates are then replicated to the other node.</span></span>  
  
-   <span data-ttu-id="199eb-142">在右侧，所有更新都定向到节点 **B**。从那里，更新被复制到节点 **A**。如果节点 **B** 脱机（例如，进行维护），则应用程序服务器可以将所有活动定向到节点 **A**。当节点 **B** 恢复联机状态后，更新便可流向 B，并且应用程序服务器可以将所有更新移动回节点 **B**，也可以继续将更新定向到节点 **A**。</span><span class="sxs-lookup"><span data-stu-id="199eb-142">On the right, all updates are directed to node **B**. From there, updates are replicated to node **A**. If **B** is offline (for example, for maintenance), the application server can direct all activity to **A**. When **B** is back online, updates can flow to it, and the application server can move all updates back to **B** or keep directing them to **A**.</span></span>  
  
 <span data-ttu-id="199eb-143">对等复制对这两种方法均支持，但右图中的中心更新示例也经常同标准事务复制一起使用。</span><span class="sxs-lookup"><span data-stu-id="199eb-143">Peer-to-peer replication can support either approach, but the central update example on the right is also often used with standard transactional replication.</span></span>  
  
### <a name="topologies-that-have-three-or-more-participating-databases"></a><span data-ttu-id="199eb-144">包含三个或三个以上参与数据库的拓扑</span><span class="sxs-lookup"><span data-stu-id="199eb-144">Topologies That Have Three or More Participating Databases</span></span>  
 <span data-ttu-id="199eb-145">![向分散位置的对等复制](../media/repl-multinode-02.gif "向分散位置的对等复制")</span><span class="sxs-lookup"><span data-stu-id="199eb-145">![Peer-to-peer replication to dispersed locations](../media/repl-multinode-02.gif "Peer-to-peer replication to dispersed locations")</span></span>  
  
 <span data-ttu-id="199eb-146">上图显示了三个参与数据库，它们为一家在洛杉矶、伦敦和台北均设有办事处的国际软件支持机构提供数据。</span><span class="sxs-lookup"><span data-stu-id="199eb-146">The preceding illustration shows three participating databases that provide data for a worldwide software support organization, with offices in Los Angeles, London, and Taipei.</span></span> <span data-ttu-id="199eb-147">每个办事处的支持工程师接听客户电话，并输入和更新每个客户电话的相关信息。</span><span class="sxs-lookup"><span data-stu-id="199eb-147">The support engineers at each office take customer calls and enter and update information about each customer call.</span></span> <span data-ttu-id="199eb-148">三个办事处的时区各相差八小时，因此不会出现工作日的重叠。</span><span class="sxs-lookup"><span data-stu-id="199eb-148">The time zones for the three offices are eight hours apart, so there is no overlap in the workday.</span></span> <span data-ttu-id="199eb-149">台北办事处下班时，伦敦办事处正开始一天的工作。</span><span class="sxs-lookup"><span data-stu-id="199eb-149">As the Taipei office closes, the London office is opening for the day.</span></span> <span data-ttu-id="199eb-150">如果办事处下班时电话仍在进行中，则电话将被转接到下一个开始办公的办事处的代表。</span><span class="sxs-lookup"><span data-stu-id="199eb-150">If a call is still in progress as one office is closing, the call is transferred to a representative at the next office to open.</span></span>  
  
 <span data-ttu-id="199eb-151">每个地点都有一台数据库服务器和一台应用程序服务器，供支持工程师在输入和更新客户电话的相关信息时使用。</span><span class="sxs-lookup"><span data-stu-id="199eb-151">Each location has a database and an application server, which are used by the support engineers as they enter and update information about customer calls.</span></span> <span data-ttu-id="199eb-152">拓扑按时间进行分区。</span><span class="sxs-lookup"><span data-stu-id="199eb-152">The topology is partitioned by time.</span></span> <span data-ttu-id="199eb-153">因此更新只发生在正在办公的节点，然后更新会流动到其他参与数据库。</span><span class="sxs-lookup"><span data-stu-id="199eb-153">Therefore, updates occur only at the node that is currently open for business, and then the updates flow to the other participating databases.</span></span> <span data-ttu-id="199eb-154">此拓扑具有下列优点：</span><span class="sxs-lookup"><span data-stu-id="199eb-154">This topology provides the following benefits:</span></span>  
  
-   <span data-ttu-id="199eb-155">独立但不孤立：每个办事处都可以独立插入、更新或删除数据，但还可以共享数据，因为数据会复制到其他所有参与数据库。</span><span class="sxs-lookup"><span data-stu-id="199eb-155">Independence without isolation: Each office can insert, update, or delete data independently but can also share the data because it is replicated to all other participating databases.</span></span>  
  
-   <span data-ttu-id="199eb-156">在出现故障或需要维护一个或多个参与数据库时可提供更高的可用性。</span><span class="sxs-lookup"><span data-stu-id="199eb-156">Higher availability in case of failure or to allow maintenance at one or more of the participating databases.</span></span>  
  
     <span data-ttu-id="199eb-157">![对等复制，三节点和四节点](../media/repl-multinode-04.gif "对等复制，三节点和四节点")</span><span class="sxs-lookup"><span data-stu-id="199eb-157">![Peer-to-peer replication, three and four nodes](../media/repl-multinode-04.gif "Peer-to-peer replication, three and four nodes")</span></span>  
  
 <span data-ttu-id="199eb-158">上图显示了向三节点拓扑添加节点的过程。</span><span class="sxs-lookup"><span data-stu-id="199eb-158">The preceding illustration shows the addition of a node to the three-node topology.</span></span> <span data-ttu-id="199eb-159">在此应用情景中，可能会由于以下原因再添加一个节点：</span><span class="sxs-lookup"><span data-stu-id="199eb-159">A node could be added in this scenario for the following reasons:</span></span>  
  
-   <span data-ttu-id="199eb-160">因为又开设了一家办事处。</span><span class="sxs-lookup"><span data-stu-id="199eb-160">Because another office is opened.</span></span>  
  
-   <span data-ttu-id="199eb-161">为了提供更高的可用性以支持维护或提高发生磁盘故障或其他重大故障时的容错能力。</span><span class="sxs-lookup"><span data-stu-id="199eb-161">To provide higher availability to support maintenance or increase fault tolerance if a disk failure or other major failure occurs.</span></span>  
  
 <span data-ttu-id="199eb-162">请注意，在三节点拓扑和四节点拓扑中，所有的数据库都向其他数据库发布和订阅数据。</span><span class="sxs-lookup"><span data-stu-id="199eb-162">Notice that in both the three- and four-node topologies, all databases publish and subscribe to all other databases.</span></span> <span data-ttu-id="199eb-163">在需要进行维护或者一个或多个节点发生故障时，这样可提供最大的可用性。</span><span class="sxs-lookup"><span data-stu-id="199eb-163">This provides maximum availability in case of maintenance needs or failure of one or more nodes.</span></span> <span data-ttu-id="199eb-164">添加节点后，必须针对性能以及部署和管理的复杂性来权衡可用性和可伸缩性的需要。</span><span class="sxs-lookup"><span data-stu-id="199eb-164">As nodes are added, you must balance availability and scalability needs against performance and the complexity of deployment and administration.</span></span>  
  
## <a name="configuring-peer-to-peer-replication"></a><span data-ttu-id="199eb-165">配置对等复制</span><span class="sxs-lookup"><span data-stu-id="199eb-165">Configuring Peer-to-Peer Replication</span></span>  
 <span data-ttu-id="199eb-166">配置对等复制拓扑的过程与配置一系列标准事务发布和订阅的过程非常类似。</span><span class="sxs-lookup"><span data-stu-id="199eb-166">Configuring a peer-to-peer replication topology is very similar to configuring a series of standard transactional publications and subscriptions.</span></span> <span data-ttu-id="199eb-167">下列主题中介绍的步骤演示一个三节点系统的配置过程，该系统类似于上面显示对等拓扑的左图中的配置。</span><span class="sxs-lookup"><span data-stu-id="199eb-167">The steps described in the following topics show the configuration of a three-node system, similar to the configuration shown on the left in the previous illustration that shows peer-to-peer topology.</span></span>  
  
## <a name="considerations-for-using-peer-to-peer-replication"></a><span data-ttu-id="199eb-168">使用对等复制的注意事项</span><span class="sxs-lookup"><span data-stu-id="199eb-168">Considerations for Using Peer-to-Peer Replication</span></span>  
 <span data-ttu-id="199eb-169">本节提供在使用对等复制时要考虑的信息和指导原则。</span><span class="sxs-lookup"><span data-stu-id="199eb-169">This section provides information and guidelines to consider when you use peer-to-peer replication.</span></span>  
  
### <a name="general-considerations"></a><span data-ttu-id="199eb-170">一般注意事项</span><span class="sxs-lookup"><span data-stu-id="199eb-170">General Considerations</span></span>  
  
-   <span data-ttu-id="199eb-171">对等复制仅在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]的 Enterprise 版本中提供。</span><span class="sxs-lookup"><span data-stu-id="199eb-171">Peer-to-peer replication is available only in Enterprise versions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="199eb-172">所有参与对等复制的数据库都应包含相同的架构和数据：</span><span class="sxs-lookup"><span data-stu-id="199eb-172">All databases that participate in peer-to-peer replication should contain identical schema and data:</span></span>  
  
    -   <span data-ttu-id="199eb-173">对象名称、对象架构和发布名称都应相同。</span><span class="sxs-lookup"><span data-stu-id="199eb-173">Object names, object schema, and publication names should be identical.</span></span>  
  
    -   <span data-ttu-id="199eb-174">发布必须允许复制架构更改。</span><span class="sxs-lookup"><span data-stu-id="199eb-174">Publications must allow schema changes to be replicated.</span></span> <span data-ttu-id="199eb-175">（这相当于发布属性**replicate_ddl** 设置为 **1**，这是默认设置）。有关详细信息，请参阅[对发布数据库进行架构更改](../publish/make-schema-changes-on-publication-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="199eb-175">(This is a setting of **1** for the publication property **replicate_ddl**, which is the default setting.) For more information, see [Make Schema Changes on Publication Databases](../publish/make-schema-changes-on-publication-databases.md).</span></span>  
  
    -   <span data-ttu-id="199eb-176">不支持行筛选和列筛选。</span><span class="sxs-lookup"><span data-stu-id="199eb-176">Row and column filtering are not supported.</span></span>  
  
-   <span data-ttu-id="199eb-177">建议每个节点都使用自己的分发数据库。</span><span class="sxs-lookup"><span data-stu-id="199eb-177">We recommend that each node use its own distribution database.</span></span> <span data-ttu-id="199eb-178">这样将消除出现单点故障的可能性。</span><span class="sxs-lookup"><span data-stu-id="199eb-178">This eliminates the potential of having a single point of failure.</span></span>  
  
-   <span data-ttu-id="199eb-179">表和其他对象不能包含在一个发布数据库内的多个对等发布中。</span><span class="sxs-lookup"><span data-stu-id="199eb-179">Tables and other objects cannot be included in multiple peer-to-peer publications in a single publication database.</span></span>  
  
-   <span data-ttu-id="199eb-180">必须为对等复制启用发布后，才能创建订阅。</span><span class="sxs-lookup"><span data-stu-id="199eb-180">A publication must be enabled for peer-to-peer replication before any subscriptions are created.</span></span>  
  
-   <span data-ttu-id="199eb-181">必须使用备份或 **replication support only** 选项对订阅进行初始化。</span><span class="sxs-lookup"><span data-stu-id="199eb-181">Subscriptions must be initialized by using a backup or with the **'replication support only'** option.</span></span> <span data-ttu-id="199eb-182">有关详细信息，请参阅 [初始化事务订阅（不使用快照）](../initialize-a-transactional-subscription-without-a-snapshot.md)中手动初始化订阅。</span><span class="sxs-lookup"><span data-stu-id="199eb-182">For more information, see [Initialize a Transactional Subscription Without a Snapshot](../initialize-a-transactional-subscription-without-a-snapshot.md).</span></span>  
  
-   <span data-ttu-id="199eb-183">建议不要使用标识列。</span><span class="sxs-lookup"><span data-stu-id="199eb-183">We do not recommend the use of identity columns.</span></span> <span data-ttu-id="199eb-184">使用标识时，必须手动管理所分配的每个参与数据库中表的范围。</span><span class="sxs-lookup"><span data-stu-id="199eb-184">When using identities, you must manually manage the ranges assigned to the tables at each participating database.</span></span> <span data-ttu-id="199eb-185">有关详细信息，请参阅[复制标识列](../publish/replicate-identity-columns.md)中的“为手动标识范围管理分配范围”部分。</span><span class="sxs-lookup"><span data-stu-id="199eb-185">For more information, see the section "Assigning Ranges for Manual Identity Range Management" in [Replicate Identity Columns](../publish/replicate-identity-columns.md).</span></span>  
  
### <a name="feature-restrictions"></a><span data-ttu-id="199eb-186">功能限制</span><span class="sxs-lookup"><span data-stu-id="199eb-186">Feature Restrictions</span></span>  
 <span data-ttu-id="199eb-187">对等复制支持事务复制的核心功能，但不支持以下选项：</span><span class="sxs-lookup"><span data-stu-id="199eb-187">Peer-to-peer replication supports the core features of transactional replication, but does not support the following options:</span></span>  
  
-   <span data-ttu-id="199eb-188">使用快照进行初始化和重新初始化。</span><span class="sxs-lookup"><span data-stu-id="199eb-188">Initialization and reinitialization with a snapshot.</span></span>  
  
-   <span data-ttu-id="199eb-189">行筛选器和列筛选器。</span><span class="sxs-lookup"><span data-stu-id="199eb-189">Row and column filters.</span></span>  
  
-   <span data-ttu-id="199eb-190">时间戳列。</span><span class="sxs-lookup"><span data-stu-id="199eb-190">Timestamp columns.</span></span>  
  
-   <span data-ttu-id="199eb-191">非[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的发布服务器和订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="199eb-191">Non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Publishers and Subscribers.</span></span>  
  
-   <span data-ttu-id="199eb-192">立即更新订阅和排队更新订阅。</span><span class="sxs-lookup"><span data-stu-id="199eb-192">Immediate updating and queued updating subscriptions.</span></span>  
  
-   <span data-ttu-id="199eb-193">匿名订阅。</span><span class="sxs-lookup"><span data-stu-id="199eb-193">Anonymous subscriptions.</span></span>  
  
-   <span data-ttu-id="199eb-194">部分订阅。</span><span class="sxs-lookup"><span data-stu-id="199eb-194">Partial subscriptions.</span></span>  
  
-   <span data-ttu-id="199eb-195">可附加的订阅和可转换的订阅。</span><span class="sxs-lookup"><span data-stu-id="199eb-195">Attachable subscriptions and transformable subscriptions.</span></span> <span data-ttu-id="199eb-196">（在 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]中不推荐使用这两个选项。）</span><span class="sxs-lookup"><span data-stu-id="199eb-196">(Both of these options were deprecated in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].)</span></span>  
  
-   <span data-ttu-id="199eb-197">共享分发代理。</span><span class="sxs-lookup"><span data-stu-id="199eb-197">Shared Distribution Agents.</span></span>  
  
-   <span data-ttu-id="199eb-198">分发代理参数 **-SubscriptionStreams** 和日志读取器代理参数 **-MaxCmdsInTran**。</span><span class="sxs-lookup"><span data-stu-id="199eb-198">The Distribution Agent parameter **-SubscriptionStreams** and the Log Reader Agent parameter **-MaxCmdsInTran**.</span></span>  
  
-   <span data-ttu-id="199eb-199">项目属性\*\* \@ destination_owner**和** \@ destination_table\*\*。</span><span class="sxs-lookup"><span data-stu-id="199eb-199">The article properties **\@destination_owner** and **\@destination_table**.</span></span>  

-   <span data-ttu-id="199eb-200">对等事务复制不支持创建针对对等发布的单向事务订阅</span><span class="sxs-lookup"><span data-stu-id="199eb-200">Peer-to-Peer transactional replication does not support creating a one-way transactional subscription to a Peer-to-Peer publication</span></span>
  
 <span data-ttu-id="199eb-201">以下属性具有特殊的注意事项：</span><span class="sxs-lookup"><span data-stu-id="199eb-201">The following properties have special considerations:</span></span>  
  
-   <span data-ttu-id="199eb-202">发布属性\*\* \@ allow_initialize_from_backup\*\*需要值 `true` 。</span><span class="sxs-lookup"><span data-stu-id="199eb-202">The publication property **\@allow_initialize_from_backup** requires a value of `true`.</span></span>  
  
-   <span data-ttu-id="199eb-203">项目属性\*\* \@ replicate_ddl**需要值 `true` 为;** \@ identityrangemanagementoption**需要值 `manual` 为;和** \@ 状态**要求设置选项**24\*\* 。</span><span class="sxs-lookup"><span data-stu-id="199eb-203">The article property **\@replicate_ddl** requires a value of `true`; **\@identityrangemanagementoption** requires a value of `manual`; and **\@status** requires that option **24** is set.</span></span>  
  
-   <span data-ttu-id="199eb-204">项目属性\*\* \@ ins_cmd**、 \*\* \@ del_cmd**和\*\* \@ upd_cmd\*\*的值不能设置为 `SQL` 。</span><span class="sxs-lookup"><span data-stu-id="199eb-204">The value for article properties **\@ins_cmd**, **\@del_cmd**, and **\@upd_cmd** cannot be set to `SQL`.</span></span>  
  
-   <span data-ttu-id="199eb-205">订阅属性\*\* \@ sync_type\*\*需要值为 `none` 或 `automatic` 。</span><span class="sxs-lookup"><span data-stu-id="199eb-205">The subscription property **\@sync_type** requires a value of `none` or `automatic`.</span></span>  
  
### <a name="maintenance-considerations"></a><span data-ttu-id="199eb-206">维护注意事项</span><span class="sxs-lookup"><span data-stu-id="199eb-206">Maintenance Considerations</span></span>  
 <span data-ttu-id="199eb-207">下列操作需要让系统静止。</span><span class="sxs-lookup"><span data-stu-id="199eb-207">The following actions require the system to be quiesced.</span></span> <span data-ttu-id="199eb-208">也就是说，停止所有节点上已发布表中的活动，并确保每个节点都已收到来自所有其他节点的更改。</span><span class="sxs-lookup"><span data-stu-id="199eb-208">This means stopping activity on published tables at all nodes and making sure that each node has received all changes from all other nodes.</span></span>  
  
-   <span data-ttu-id="199eb-209">[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]向现有拓扑添加节点</span><span class="sxs-lookup"><span data-stu-id="199eb-209">Adding a [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] node to an existing topology</span></span>  
  
-   <span data-ttu-id="199eb-210">将项目添加到现有发布</span><span class="sxs-lookup"><span data-stu-id="199eb-210">Adding an article to an existing publication</span></span>  
  
-   <span data-ttu-id="199eb-211">进行架构更改</span><span class="sxs-lookup"><span data-stu-id="199eb-211">Making schema changes</span></span>  
  
-   <span data-ttu-id="199eb-212">从备份还原节点</span><span class="sxs-lookup"><span data-stu-id="199eb-212">Restoring a node from a backup</span></span>  
  
 <span data-ttu-id="199eb-213">有关详细信息，请参阅[停止复制拓扑（复制 Transact-SQL 编程）](../administration/quiesce-a-replication-topology-replication-transact-sql-programming.md)和[管理对等拓扑（复制 Transact-SQL 编程）](../administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md)。</span><span class="sxs-lookup"><span data-stu-id="199eb-213">For more information, see [Quiesce a Replication Topology &#40;Replication Transact-SQL Programming&#41;](../administration/quiesce-a-replication-topology-replication-transact-sql-programming.md) and [Administer a Peer-to-Peer Topology &#40;Replication Transact-SQL Programming&#41;](../administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md).</span></span>  
  
-   <span data-ttu-id="199eb-214">如果要将新节点添加到对等拓扑中，只应从在添加新节点后创建的备份中进行还原。</span><span class="sxs-lookup"><span data-stu-id="199eb-214">If you add a new node to a peer-to-peer topology, you should restore only from backups that were created after the new node was added.</span></span>  
  
-   <span data-ttu-id="199eb-215">无法重新初始化对等拓扑中的订阅。</span><span class="sxs-lookup"><span data-stu-id="199eb-215">You cannot reinitialize subscriptions in a peer-to-peer topology.</span></span> <span data-ttu-id="199eb-216">如果需要确保节点有新的数据副本，请在该节点上还原备份。</span><span class="sxs-lookup"><span data-stu-id="199eb-216">If you have to ensure that a node has a new copy of the data, restore a backup at the node.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="199eb-217">另请参阅</span><span class="sxs-lookup"><span data-stu-id="199eb-217">See Also</span></span>  
 <span data-ttu-id="199eb-218">[管理对等拓扑（复制 Transact-SQL 编程）](../administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md) </span><span class="sxs-lookup"><span data-stu-id="199eb-218">[Administer a Peer-to-Peer Topology &#40;Replication Transact-SQL Programming&#41;](../administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md) </span></span>  
 <span data-ttu-id="199eb-219">[快照复制和事务复制的备份和还原策略](../administration/strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md) </span><span class="sxs-lookup"><span data-stu-id="199eb-219">[Strategies for Backing Up and Restoring Snapshot and Transactional Replication](../administration/strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md) </span></span>  
 [<span data-ttu-id="199eb-220">事务复制的发布类型</span><span class="sxs-lookup"><span data-stu-id="199eb-220">Publication Types for Transactional Replication</span></span>](transactional-replication.md)  
  
  
