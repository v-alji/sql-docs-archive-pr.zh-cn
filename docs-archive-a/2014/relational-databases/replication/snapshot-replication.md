---
title: 快照复制 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- snapshot replication [SQL Server], about snapshot replication
- snapshot replication [SQL Server]
ms.assetid: 5d745f22-9c6b-4e11-8c62-bc50e9a8bf38
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6192c196e31c4c5772099074c79b3c6c4ca7aeed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694450"
---
# <a name="snapshot-replication"></a><span data-ttu-id="ab589-102">快照复制</span><span class="sxs-lookup"><span data-stu-id="ab589-102">Snapshot Replication</span></span>
  <span data-ttu-id="ab589-103">快照复制完全按照数据在特定时刻的状态分发数据，而不监视数据是否更新。</span><span class="sxs-lookup"><span data-stu-id="ab589-103">Snapshot replication distributes data exactly as it appears at a specific moment in time and does not monitor for updates to the data.</span></span> <span data-ttu-id="ab589-104">发生同步时，将生成完整的快照并将其发送到订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="ab589-104">When synchronization occurs, the entire snapshot is generated and sent to Subscribers.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ab589-105">快照复制可由其自身使用，但是快照处理（负责创建由发布所指定的所有对象和数据的副本）通常还用于为事务发布与合并发布提供初始的数据和数据库对象集。</span><span class="sxs-lookup"><span data-stu-id="ab589-105">Snapshot replication can be used by itself, but the snapshot process (which creates a copy of all of the objects and data specified by a publication) is also commonly used to provide the initial set of data and database objects for transactional and merge publications.</span></span>  
  
 <span data-ttu-id="ab589-106">当符合以下一个或多个条件时，使用快照复制本身是最合适的：</span><span class="sxs-lookup"><span data-stu-id="ab589-106">Using snapshot replication by itself is most appropriate when one or more of the following is true:</span></span>  
  
-   <span data-ttu-id="ab589-107">很少更改数据。</span><span class="sxs-lookup"><span data-stu-id="ab589-107">Data changes infrequently.</span></span>  
  
-   <span data-ttu-id="ab589-108">在一段时间内允许具有相对发布服务器已过时的数据副本。</span><span class="sxs-lookup"><span data-stu-id="ab589-108">It is acceptable to have copies of data that are out of date with respect to the Publisher for a period of time.</span></span>  
  
-   <span data-ttu-id="ab589-109">复制少量数据。</span><span class="sxs-lookup"><span data-stu-id="ab589-109">Replicating small volumes of data.</span></span>  
  
-   <span data-ttu-id="ab589-110">在短期内出现大量更改。</span><span class="sxs-lookup"><span data-stu-id="ab589-110">A large volume of changes occurs over a short period of time.</span></span>  
  
 <span data-ttu-id="ab589-111">在数据更改量很大，但很少发生更改时，快照复制是最合适的。</span><span class="sxs-lookup"><span data-stu-id="ab589-111">Snapshot replication is most appropriate when data changes are substantial but infrequent.</span></span> <span data-ttu-id="ab589-112">例如，如果某销售组织维护一个产品价格列表且这些价格每年要在固定时间进行一两次完全更新，那么建议在数据更改后复制完整的数据快照。</span><span class="sxs-lookup"><span data-stu-id="ab589-112">For example, if a sales organization maintains a product price list and the prices are all updated at the same time once or twice each year, replicating the entire snapshot of data after it has changed is recommended.</span></span> <span data-ttu-id="ab589-113">对于给定的某些类型的数据，更频繁的快照可能也比较适合。</span><span class="sxs-lookup"><span data-stu-id="ab589-113">Given certain types of data, more frequent snapshots may also be appropriate.</span></span> <span data-ttu-id="ab589-114">例如，如果一天中在发布服务器上更新相对小的表，但可以接受一定的滞后时间，则可以在夜间以快照形式传递更改。</span><span class="sxs-lookup"><span data-stu-id="ab589-114">For example, if a relatively small table is updated at the Publisher during the day, but some latency is acceptable, changes can be delivered nightly as a snapshot.</span></span>  
  
 <span data-ttu-id="ab589-115">发布服务器上快照复制的连续开销低于事务复制的开销，因为不用跟踪增量更改。</span><span class="sxs-lookup"><span data-stu-id="ab589-115">Snapshot replication has a lower continuous overhead on the Publisher than transactional replication, because incremental changes are not tracked.</span></span> <span data-ttu-id="ab589-116">但是，如果要复制的数据集非常大，那么若要生成和应用快照，将需要使用大量资源。</span><span class="sxs-lookup"><span data-stu-id="ab589-116">However, if the dataset set being replicated is very large, it will require substantial resources to generate and apply the snapshot.</span></span> <span data-ttu-id="ab589-117">评估是否使用快照复制时，需要考虑整个数据集的大小以及数据的更改频率。</span><span class="sxs-lookup"><span data-stu-id="ab589-117">Consider the size of the entire data set and the frequency of changes to the data when evaluating whether to utilize snapshot replication.</span></span>  
  
 <span data-ttu-id="ab589-118">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="ab589-118">**In this topic**</span></span>  
  
 [<span data-ttu-id="ab589-119">快照复制的工作机制</span><span class="sxs-lookup"><span data-stu-id="ab589-119">How Snapshot Replication Works</span></span>](#HowWorks)  
  
 [<span data-ttu-id="ab589-120">快照代理</span><span class="sxs-lookup"><span data-stu-id="ab589-120">Snapshot Agent</span></span>](#SnapshotAgent)  
  
 [<span data-ttu-id="ab589-121">分发代理和合并代理</span><span class="sxs-lookup"><span data-stu-id="ab589-121">Distribution and Merge Agents</span></span>](#DistAgent)  
  
##  <a name="how-snapshot-replication-works"></a><a name="HowWorks"></a> <span data-ttu-id="ab589-122">快照复制的工作机制</span><span class="sxs-lookup"><span data-stu-id="ab589-122">How Snapshot Replication Works</span></span>  
 <span data-ttu-id="ab589-123">默认情况下，所有三种复制都使用快照初始化订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="ab589-123">By default, all three types of replication use a snapshot to initialize Subscribers.</span></span> <span data-ttu-id="ab589-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 快照代理始终生成快照文件，但传递文件的代理因使用的复制类型而异。</span><span class="sxs-lookup"><span data-stu-id="ab589-124">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Snapshot Agent always generates the snapshot files, but the agent that delivers the files differs depending on the type of replication being used.</span></span> <span data-ttu-id="ab589-125">快照复制和事务复制使用分发代理传递文件，而合并复制使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 合并代理。</span><span class="sxs-lookup"><span data-stu-id="ab589-125">Snapshot replication and transactional replication use the Distribution Agent to deliver the files, whereas merge replication uses the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Merge Agent.</span></span> <span data-ttu-id="ab589-126">快照代理在分发服务器上运行。</span><span class="sxs-lookup"><span data-stu-id="ab589-126">The Snapshot Agent runs at the Distributor.</span></span> <span data-ttu-id="ab589-127">对于推送订阅，分发代理和合并代理在分发服务器上运行；对于请求订阅，则在订阅服务器上运行。</span><span class="sxs-lookup"><span data-stu-id="ab589-127">The Distribution Agent and Merge Agent run at the Distributor for push subscriptions, or at Subscribers for pull subscriptions.</span></span>  
  
 <span data-ttu-id="ab589-128">可以在创建订阅后立即生成和应用快照，也可以按照创建发布时制定的计划进行。</span><span class="sxs-lookup"><span data-stu-id="ab589-128">Snapshots can be generated and applied either immediately after the subscription is created or according to a schedule set at the time the publication is created.</span></span> <span data-ttu-id="ab589-129">快照代理准备快照文件（其中包含已发布表和数据库对象的架构和数据），然后将这些文件存储在发布服务器的快照文件夹中，并在分发服务器上的分发数据库中记录跟踪信息。</span><span class="sxs-lookup"><span data-stu-id="ab589-129">The Snapshot Agent prepares snapshot files containing the schema and data of published tables and database objects, stores the files in the snapshot folder for the Publisher, and records tracking information in the distribution database on the Distributor.</span></span> <span data-ttu-id="ab589-130">配置分发服务器时，可以指定一个默认的快照文件夹，也可以为发布指定一个备用位置，以替代默认位置或与之并存。</span><span class="sxs-lookup"><span data-stu-id="ab589-130">You specify a default snapshot folder when you configure a Distributor, but you can specify an alternate location for a publication instead of or in addition to the default.</span></span>  
  
 <span data-ttu-id="ab589-131">除了本主题中描述的标准快照过程外，使用参数化筛选器的合并发布还使用一个由两部分组成的快照过程。</span><span class="sxs-lookup"><span data-stu-id="ab589-131">In addition to the standard snapshot process described in this topic, a two-part snapshot process is used for merge publications with parameterized filters.</span></span>  
  
 <span data-ttu-id="ab589-132">下图显示了快照复制的主要组件。</span><span class="sxs-lookup"><span data-stu-id="ab589-132">The following illustration shows the principal components of snapshot replication.</span></span>  
  
 <span data-ttu-id="ab589-133">![快照复制组件和数据流](media/snapshot.gif "快照复制组件和数据流")</span><span class="sxs-lookup"><span data-stu-id="ab589-133">![Snapshot replication components and data flow](media/snapshot.gif "Snapshot replication components and data flow")</span></span>  
  
##  <a name="snapshot-agent"></a><a name="SnapshotAgent"></a> <span data-ttu-id="ab589-134">快照代理</span><span class="sxs-lookup"><span data-stu-id="ab589-134">Snapshot Agent</span></span>  
 <span data-ttu-id="ab589-135">对于合并复制，每当运行快照代理时都会生成快照。</span><span class="sxs-lookup"><span data-stu-id="ab589-135">For merge replication, a snapshot is generated every time the Snapshot Agent runs.</span></span> <span data-ttu-id="ab589-136">对于事务复制，是否生成快照取决于发布属性 **immediate_sync**的设置。</span><span class="sxs-lookup"><span data-stu-id="ab589-136">For transactional replication, snapshot generation depends on the setting of the publication property **immediate_sync**.</span></span> <span data-ttu-id="ab589-137">如果该属性设置为 TRUE（使用新建发布向导时的默认设置），则每当运行快照代理时都会生成快照，而且可以随时将其应用到订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="ab589-137">If the property is set to TRUE (the default when using the New Publication Wizard), a snapshot is generated every time the Snapshot Agent runs, and it can be applied to a Subscriber at any time.</span></span> <span data-ttu-id="ab589-138">如果该属性设置为 FALSE（使用 **sp_addpublication**时的默认设置），则仅当自上次快照代理运行以来添加了新订阅时，才会生成快照；订阅服务器必须等待快照代理完成，才能实现同步。</span><span class="sxs-lookup"><span data-stu-id="ab589-138">If the property is set to FALSE (the default when using **sp_addpublication**), the snapshot is generated only if a new subscription has been added since the last Snapshot Agent run; Subscribers must wait for the Snapshot Agent to complete before they can synchronize.</span></span>  
  
 <span data-ttu-id="ab589-139">快照代理执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="ab589-139">The Snapshot Agent performs the following steps:</span></span>  
  
1.  <span data-ttu-id="ab589-140">在分发服务器到发布服务器之间建立连接，然后根据需要在已发布表上使用锁：</span><span class="sxs-lookup"><span data-stu-id="ab589-140">Establishes a connection from the Distributor to the Publisher, and then takes locks on published tables if necessary:</span></span>  
  
    -   <span data-ttu-id="ab589-141">对于合并发布，快照代理不使用任何锁。</span><span class="sxs-lookup"><span data-stu-id="ab589-141">For merge publications, the Snapshot Agent does not take any locks.</span></span>  
  
    -   <span data-ttu-id="ab589-142">对于事务发布，默认情况下快照代理只在快照生成的初始阶段使用锁。</span><span class="sxs-lookup"><span data-stu-id="ab589-142">For transactional publications, by default the Snapshot Agent take locks only during the initial phase of snapshot generation.</span></span>  
  
    -   <span data-ttu-id="ab589-143">对于快照发布，整个快照生成过程中都使用锁。</span><span class="sxs-lookup"><span data-stu-id="ab589-143">For snapshot publications, locks are held during the entire snapshot generation process.</span></span>  
  
2.  <span data-ttu-id="ab589-144">将每个项目的表架构副本写入一个 .sch 文件。</span><span class="sxs-lookup"><span data-stu-id="ab589-144">Writes a copy of the table schema for each article to a .sch file.</span></span> <span data-ttu-id="ab589-145">如果发布其他数据库对象（如索引、约束、存储过程、视图、用户定义函数等），则生成其他脚本文件。</span><span class="sxs-lookup"><span data-stu-id="ab589-145">If other database objects are published, such as indexes, constraints, stored procedures, views, user-defined functions, and so on, additional script files are generated.</span></span>  
  
3.  <span data-ttu-id="ab589-146">从发布服务器上已发布的表中复制数据，然后将数据写入快照文件夹。</span><span class="sxs-lookup"><span data-stu-id="ab589-146">Copies the data from the published table at the Publisher and writes the data to the snapshot folder.</span></span> <span data-ttu-id="ab589-147">快照将以一组大容量复制程序 (BCP) 文件的形式生成。</span><span class="sxs-lookup"><span data-stu-id="ab589-147">The snapshot is generated as a set of bulk copy program (BCP) files.</span></span>  
  
4.  <span data-ttu-id="ab589-148">对于快照发布和事务发布，快照代理将向分发数据库的 **MSrepl_commands** 表和 **MSrepl_transactions** 表中追加行。</span><span class="sxs-lookup"><span data-stu-id="ab589-148">For snapshot and transactional publications, the Snapshot Agent appends rows to the **MSrepl_commands** and **MSrepl_transactions** tables in the distribution database.</span></span> <span data-ttu-id="ab589-149">**MSrepl_commands** 表中包含的是命令，这些命令指示 .sch 和 .bcp 文件、其他快照文件以及对快照前或快照后脚本的引用的位置。</span><span class="sxs-lookup"><span data-stu-id="ab589-149">The entries in the **MSrepl_commands** table are commands indicating the location of .sch and .bcp files, any other snapshot files, and references to any pre- or post-snapshot scripts.</span></span> <span data-ttu-id="ab589-150">**MSrepl_transactions** 表中包含的是与同步订阅服务器相关的命令。</span><span class="sxs-lookup"><span data-stu-id="ab589-150">The entries in the **MSrepl_transactions** table are commands relevant to synchronizing the Subscriber.</span></span>  
  
     <span data-ttu-id="ab589-151">对于合并发布，快照代理还执行其他操作。</span><span class="sxs-lookup"><span data-stu-id="ab589-151">For merge publications, the Snapshot Agent performs additional steps.</span></span>  
  
5.  <span data-ttu-id="ab589-152">释放已发布表上的所有锁。</span><span class="sxs-lookup"><span data-stu-id="ab589-152">Releases any locks on published tables.</span></span>  
  
 <span data-ttu-id="ab589-153">在快照生成过程中，不能对已发布表进行构架更改。</span><span class="sxs-lookup"><span data-stu-id="ab589-153">During snapshot generation, you cannot make schema changes on published tables.</span></span> <span data-ttu-id="ab589-154">生成快照文件后，可以使用 Windows 资源管理器在快照文件夹中查看这些快照文件。</span><span class="sxs-lookup"><span data-stu-id="ab589-154">After the snapshot files are generated, you can view them in the snapshot folder using Windows Explorer.</span></span>  
  
##  <a name="distribution-agent-and-merge-agent"></a><a name="DistAgent"></a> <span data-ttu-id="ab589-155">分发代理和合并代理</span><span class="sxs-lookup"><span data-stu-id="ab589-155">Distribution Agent and Merge Agent</span></span>  
 <span data-ttu-id="ab589-156">对于快照发布，分发代理每次运行发布时，都会将一个新快照移动到每个尚未同步但已标记为重新初始化或者包含新项目的订阅服务器中。</span><span class="sxs-lookup"><span data-stu-id="ab589-156">For snapshot publications, each time the Distribution Agent runs for the publication, it moves a new snapshot to each Subscriber that has not yet been synchronized, has been marked for reinitialization, or includes new articles.</span></span>  
  
 <span data-ttu-id="ab589-157">对于快照复制和事务复制，分发代理执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="ab589-157">For snapshot and transactional replication, the Distribution Agent performs the following steps:</span></span>  
  
1.  <span data-ttu-id="ab589-158">与分发服务器建立连接。</span><span class="sxs-lookup"><span data-stu-id="ab589-158">Establishes a connection to the Distributor.</span></span>  
  
2.  <span data-ttu-id="ab589-159">检查分发服务器上分发数据库中的 **MSrepl_commands** 和 **MSrepl_transactions** 表。</span><span class="sxs-lookup"><span data-stu-id="ab589-159">Examines the **MSrepl_commands** and **MSrepl_transactions** tables in the distribution database on the Distributor.</span></span> <span data-ttu-id="ab589-160">代理从第一个表中读取快照文件的位置，并从这两个表中读取订阅服务器同步命令。</span><span class="sxs-lookup"><span data-stu-id="ab589-160">The agent reads the location of the snapshot files from the first table and Subscriber synchronization commands from both tables.</span></span>  
  
3.  <span data-ttu-id="ab589-161">将架构和命令应用于订阅数据库。</span><span class="sxs-lookup"><span data-stu-id="ab589-161">Applies the schema and commands to the subscription database.</span></span>  
  
 <span data-ttu-id="ab589-162">对于未筛选的合并复制发布，合并代理将执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="ab589-162">For an unfiltered merge replication publication, the Merge Agent performs the following steps:</span></span>  
  
1.  <span data-ttu-id="ab589-163">与发布服务器建立连接。</span><span class="sxs-lookup"><span data-stu-id="ab589-163">Establishes a connection to the Publisher.</span></span>  
  
2.  <span data-ttu-id="ab589-164">检查发布服务器上的 **sysmergeschemachange** 表，确定是否存在应该应用于订阅服务器的新快照。</span><span class="sxs-lookup"><span data-stu-id="ab589-164">Examines the **sysmergeschemachange** table on the Publisher and determines whether there is a new snapshot that should be applied at the Subscriber.</span></span>  
  
3.  <span data-ttu-id="ab589-165">如果存在新快照，合并代理则将 **sysmergeschemachange**所指定位置处的快照文件应用于订阅数据库。</span><span class="sxs-lookup"><span data-stu-id="ab589-165">If a new snapshot is available, the Merge Agent applies to the subscription database the snapshot files from the location specified in **sysmergeschemachange**.</span></span>  
  
  
