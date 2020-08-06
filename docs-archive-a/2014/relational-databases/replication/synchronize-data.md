---
title: 同步数据 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- synchronization [SQL Server replication], about synchronization
- merge replication synchronization [SQL Server replication]
- scripts [SQL Server replication], synchronization and
- synchronization [SQL Server replication]
- snapshot replication [SQL Server], synchronization
- transactional replication, synchronization
- subscriptions [SQL Server replication], synchronizing
- on demand script execution
- replication [SQL Server], synchronization
- scripts [SQL Server replication]
ms.assetid: 724802f7-7d69-46d3-a330-bd8aa7f53114
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c92cc4d1ae8e836f169a731ecf3c37c81f3dbf10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689849"
---
# <a name="synchronize-data"></a><span data-ttu-id="98124-102">同步数据</span><span class="sxs-lookup"><span data-stu-id="98124-102">Synchronize Data</span></span>
  <span data-ttu-id="98124-103">同步数据是指在订阅服务器上应用初始快照后，在发布服务器和订阅服务器之间传播数据和架构更改的过程。</span><span class="sxs-lookup"><span data-stu-id="98124-103">Synchronizing data refers to the process of data and schema changes being propagated between the Publisher and Subscribers after the initial snapshot has been applied at the Subscriber.</span></span> <span data-ttu-id="98124-104">同步可按下列方式发生：</span><span class="sxs-lookup"><span data-stu-id="98124-104">Synchronization can occur:</span></span>  
  
-   <span data-ttu-id="98124-105">连续，这是事务复制的典型方式。</span><span class="sxs-lookup"><span data-stu-id="98124-105">Continuously, which is typical for transactional replication.</span></span>  
  
-   <span data-ttu-id="98124-106">按需，这是合并复制的典型方式。</span><span class="sxs-lookup"><span data-stu-id="98124-106">On demand, which is typical for merge replication.</span></span>  
  
-   <span data-ttu-id="98124-107">根据计划，这是快照复制的典型方式。</span><span class="sxs-lookup"><span data-stu-id="98124-107">On a schedule, which is typical for snapshot replication.</span></span>  
  
 <span data-ttu-id="98124-108">同步订阅时，根据您所使用的复制类型的不同，将发生不同的过程。</span><span class="sxs-lookup"><span data-stu-id="98124-108">When a subscription is synchronized, different processes occur based on the type of replication you are using:</span></span>  
  
-   <span data-ttu-id="98124-109">快照复制。</span><span class="sxs-lookup"><span data-stu-id="98124-109">Snapshot replication.</span></span> <span data-ttu-id="98124-110">同步是指分发代理在订阅服务器上重新应用快照，以便订阅数据库与发布数据库上的架构和数据一致。</span><span class="sxs-lookup"><span data-stu-id="98124-110">Synchronization means that the Distribution Agent reapplies the snapshot at the Subscriber so that schema and data at the subscription database is consistent with the publication database.</span></span>  
  
     <span data-ttu-id="98124-111">如果在发布服务器上修改了数据或架构，则必须生成一个新快照，以便将修改传播到订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="98124-111">If modifications to data or schema have been made at the Publisher, a new snapshot must be generated in order to propagate modifications to the Subscriber.</span></span>  
  
-   <span data-ttu-id="98124-112">事务复制。</span><span class="sxs-lookup"><span data-stu-id="98124-112">Transactional replication.</span></span> <span data-ttu-id="98124-113">同步是指分发代理将更新、插入、删除及其他更改从分发数据库传输到订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="98124-113">Synchronization means that the Distribution Agent transfers updates, inserts, deletes, and any other changes from the distribution database to the Subscriber.</span></span>  
  
-   <span data-ttu-id="98124-114">合并复制。</span><span class="sxs-lookup"><span data-stu-id="98124-114">Merge replication.</span></span> <span data-ttu-id="98124-115">同步是指合并代理从订阅服务器向发布服务器上载更改，然后再从发布服务器向订阅服务器下载更改。</span><span class="sxs-lookup"><span data-stu-id="98124-115">Synchronization means that the Merge Agent uploads changes from the Subscriber to the Publisher and then downloads changes from the Publisher to the Subscriber.</span></span> <span data-ttu-id="98124-116">将检测并解决冲突（如果有）。</span><span class="sxs-lookup"><span data-stu-id="98124-116">Conflicts, if any, are detected and resolved.</span></span> <span data-ttu-id="98124-117">数据被收敛，发布服务器和所有订阅服务器将最终达到相同的数据值。</span><span class="sxs-lookup"><span data-stu-id="98124-117">Data is converged, and the Publisher and all Subscribers eventually end up with the same data values.</span></span> <span data-ttu-id="98124-118">如果检测到冲突并解决了冲突，则一些用户已提交的工作将更改为根据您定义的策略来解决冲突。</span><span class="sxs-lookup"><span data-stu-id="98124-118">If conflicts were detected and resolved, work that was committed by some of the users is changed to resolve the conflict according to policies you define.</span></span>  
  
 <span data-ttu-id="98124-119">每次发生同步时，快照发布都会彻底刷新订阅服务器上的架构，因此所有架构更改都会应用到订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="98124-119">Snapshot publications completely refresh the schema at the Subscriber every time synchronization occurs, so all schema changes are applied to the Subscriber.</span></span> <span data-ttu-id="98124-120">事务复制和合并复制还支持最常见的架构更改。</span><span class="sxs-lookup"><span data-stu-id="98124-120">Transactional replication and merge replication also support the most common schema changes.</span></span> <span data-ttu-id="98124-121">有关详细信息，请参阅[对发布数据库进行架构更改](publish/make-schema-changes-on-publication-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="98124-121">For more information, see [Make Schema Changes on Publication Databases](publish/make-schema-changes-on-publication-databases.md).</span></span>  
  
 <span data-ttu-id="98124-122">若要同步推送订阅，请参阅 [Synchronize a Push Subscription](synchronize-a-push-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="98124-122">To synchronize a push subscription, see [Synchronize a Push Subscription](synchronize-a-push-subscription.md).</span></span>  
  
 <span data-ttu-id="98124-123">若要同步请求订阅，请参阅 [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="98124-123">To synchronize a pull subscription, see [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md).</span></span>  
  
 <span data-ttu-id="98124-124">若要设置同步计划，请参阅 [Specify Synchronization Schedules](specify-synchronization-schedules.md)。</span><span class="sxs-lookup"><span data-stu-id="98124-124">To set synchronization schedules, see [Specify Synchronization Schedules](specify-synchronization-schedules.md).</span></span>  
  
 <span data-ttu-id="98124-125">**查看和解决同步冲突**</span><span class="sxs-lookup"><span data-stu-id="98124-125">**To view and resolve synchronization conflicts**</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]<span data-ttu-id="98124-126">：[查看和解决合并发布的数据冲突 &#40;SQL Server Management Studio&#41;](view-and-resolve-data-conflicts-for-merge-publications.md)</span><span class="sxs-lookup"><span data-stu-id="98124-126">: [View and Resolve Data Conflicts for Merge Publications &#40;SQL Server Management Studio&#41;](view-and-resolve-data-conflicts-for-merge-publications.md)</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]<span data-ttu-id="98124-127">：[查看事务发布的数据冲突 &#40;SQL Server Management Studio&#41;](view-data-conflicts-for-transactional-publications-sql-server-management-studio.md)</span><span class="sxs-lookup"><span data-stu-id="98124-127">: [View Data Conflicts for Transactional Publications &#40;SQL Server Management Studio&#41;](view-data-conflicts-for-transactional-publications-sql-server-management-studio.md)</span></span>  
  
## <a name="executing-code-during-synchronization"></a><span data-ttu-id="98124-128">在同步过程中执行代码</span><span class="sxs-lookup"><span data-stu-id="98124-128">Executing Code During Synchronization</span></span>  
 <span data-ttu-id="98124-129">复制支持两种在同步过程中执行代码的方法</span><span class="sxs-lookup"><span data-stu-id="98124-129">Replication supports two methods of executing code during synchronization</span></span>  
  
-   <span data-ttu-id="98124-130">事务复制和合并复制支持按需脚本执行。</span><span class="sxs-lookup"><span data-stu-id="98124-130">On demand script execution is supported for transactional replication and merge replication.</span></span> <span data-ttu-id="98124-131">使用按需脚本执行，可以指定要在同步过程中运行的 SQL 脚本。</span><span class="sxs-lookup"><span data-stu-id="98124-131">Using on demand script execution you can specify a SQL script to run during synchronization.</span></span> <span data-ttu-id="98124-132">将该脚本复制到订阅服务器，并在同步进程开始时用 **sqlcmd** 执行该脚本。</span><span class="sxs-lookup"><span data-stu-id="98124-132">The script is copied to the Subscriber and executed using **sqlcmd** at the beginning of the synchronization process.</span></span> <span data-ttu-id="98124-133">在将复制的更改应用到订阅服务器时，该脚本不能访问这些复制的更改。</span><span class="sxs-lookup"><span data-stu-id="98124-133">The script does not have access to the replicated changes as they are applied to the Subscriber.</span></span> <span data-ttu-id="98124-134">有关详细信息，请参阅[在同步期间执行脚本（复制 Transact-SQL 编程）](execute-scripts-during-synchronization-replication-transact-sql-programming.md)。</span><span class="sxs-lookup"><span data-stu-id="98124-134">For more information, see [Execute Scripts During Synchronization &#40;Replication Transact-SQL Programming&#41;](execute-scripts-during-synchronization-replication-transact-sql-programming.md).</span></span>  
  
-   <span data-ttu-id="98124-135">合并复制支持业务逻辑处理程序。</span><span class="sxs-lookup"><span data-stu-id="98124-135">Business logic handlers are supported for merge replication.</span></span> <span data-ttu-id="98124-136">使用业务逻辑处理程序框架，可以编写一个在合并同步过程中调用的托管代码程序集。</span><span class="sxs-lookup"><span data-stu-id="98124-136">Using the business logic handler framework you can write a managed code assembly that is called during the merge synchronization process.</span></span> <span data-ttu-id="98124-137">程序集包括可以响应同步过程中的许多状况的业务逻辑：数据更改、冲突和错误。</span><span class="sxs-lookup"><span data-stu-id="98124-137">The assembly includes business logic that can respond to a number of conditions during synchronization: data changes, conflicts, and errors.</span></span> <span data-ttu-id="98124-138">有关详细信息，请参阅[合并同步期间执行业务逻辑](merge/execute-business-logic-during-merge-synchronization.md)。</span><span class="sxs-lookup"><span data-stu-id="98124-138">For more information, see [Execute Business Logic During Merge Synchronization](merge/execute-business-logic-during-merge-synchronization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98124-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="98124-139">See Also</span></span>  
 [<span data-ttu-id="98124-140">检测并解决合并复制冲突</span><span class="sxs-lookup"><span data-stu-id="98124-140">Detect and Resolve Merge Replication Conflicts</span></span>](merge/advanced-merge-replication-conflict-detection-and-resolution.md)  
  
  
