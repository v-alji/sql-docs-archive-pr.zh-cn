---
title: 排队更新冲突的检测和解决 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- conflict resolution [SQL Server replication], queued updating subscriptions
- viewing queued updating conflicts
- conflict resolution [SQL Server replication]
- queued updating subscriptions [SQL Server replication]
- articles [SQL Server replication], conflict resolution
ms.assetid: 084ac587-25e7-4bd0-a385-556bbe07d02f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8c4608347ab119e25caa45b0ee4a592a953e34a4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591233"
---
# <a name="queued-updating-conflict-detection-and-resolution"></a><span data-ttu-id="4cd43-102">Queued Updating Conflict Detection and Resolution</span><span class="sxs-lookup"><span data-stu-id="4cd43-102">Queued Updating Conflict Detection and Resolution</span></span>
  <span data-ttu-id="4cd43-103">由于排队更新订阅允许对多个位置上的相同数据进行修改，因此，在发布服务器中同步数据时可能会发生冲突。</span><span class="sxs-lookup"><span data-stu-id="4cd43-103">Because queued updating subscriptions allow modifications to the same data at multiple locations, there may be conflicts when data is synchronized at the Publisher.</span></span> <span data-ttu-id="4cd43-104">复制在将更改与发布服务器同步时检测冲突，并使用在创建发布时所选择的解决策略来解决那些冲突。</span><span class="sxs-lookup"><span data-stu-id="4cd43-104">Replication detects any conflicts when changes are synchronized with the Publisher and resolves those conflicts using the resolution policy you selected when creating the publication.</span></span> <span data-ttu-id="4cd43-105">可能会发生下列冲突：</span><span class="sxs-lookup"><span data-stu-id="4cd43-105">The following conflicts can occur:</span></span>  
  
-   <span data-ttu-id="4cd43-106">更新和插入冲突。</span><span class="sxs-lookup"><span data-stu-id="4cd43-106">Update and insert conflicts.</span></span> <span data-ttu-id="4cd43-107">在两个位置更改相同的数据时会发生此冲突。</span><span class="sxs-lookup"><span data-stu-id="4cd43-107">This conflict happens when the same data is changed at two locations.</span></span> <span data-ttu-id="4cd43-108">一个更改入选，而另一个更改落选。</span><span class="sxs-lookup"><span data-stu-id="4cd43-108">One change wins, and the other one loses.</span></span>  
  
-   <span data-ttu-id="4cd43-109">删除冲突。</span><span class="sxs-lookup"><span data-stu-id="4cd43-109">Delete conflicts.</span></span> <span data-ttu-id="4cd43-110">当在一个位置删除某行而在另一个位置更改同一行时，则会发生此冲突。</span><span class="sxs-lookup"><span data-stu-id="4cd43-110">This conflict occurs when the same row is deleted at one location and changed at the other.</span></span>  
  
 <span data-ttu-id="4cd43-111">冲突检测和解决可能是十分耗时并占用大量资源的过程，因此，减少应用程序中的冲突的最好方法是：创建数据分区以便不同的订阅服务器修改不同的数据子集。</span><span class="sxs-lookup"><span data-stu-id="4cd43-111">Conflict detection and resolution can be a time-consuming and resource-intensive process; therefore, it is best to minimize conflicts in the application by creating data partitions so that different Subscribers modify different subsets of data.</span></span>  
  
## <a name="detecting-conflicts"></a><span data-ttu-id="4cd43-112">检测冲突</span><span class="sxs-lookup"><span data-stu-id="4cd43-112">Detecting Conflicts</span></span>  
 <span data-ttu-id="4cd43-113">创建发布并启用排队更新时，复制将向基础表添加一个带有默认值 **newid()** 的**uniqueidentifier**列 ( **msrepl_tran_version** )。</span><span class="sxs-lookup"><span data-stu-id="4cd43-113">When creating a publication and enabling queued updating, replication adds a **uniqueidentifier** column (**msrepl_tran_version**) with the default of **newid()** to the underlying table.</span></span> <span data-ttu-id="4cd43-114">在发布服务器或订阅服务器中更改已发布的数据后，行将收到一个新的全局唯一标识符 (GUID)，指示存在新的行版本。</span><span class="sxs-lookup"><span data-stu-id="4cd43-114">When published data is changed at either the Publisher or the Subscriber, the row receives a new globally unique identifier (GUID) to indicate that a new row version exists.</span></span> <span data-ttu-id="4cd43-115">队列读取器代理在同步过程中用此列来确定是否存在冲突。</span><span class="sxs-lookup"><span data-stu-id="4cd43-115">The Queue Reader Agent uses this column during synchronization to determine if a conflict exists.</span></span>  
  
 <span data-ttu-id="4cd43-116">队列中的事务将保留新旧两个行版本值。</span><span class="sxs-lookup"><span data-stu-id="4cd43-116">A transaction in a queue maintains the old and new row version values.</span></span> <span data-ttu-id="4cd43-117">在发布服务器中应用事务时，该事务的 GUID 将与发布中的 GUID 进行比较。</span><span class="sxs-lookup"><span data-stu-id="4cd43-117">When the transaction is applied at the Publisher, the GUIDs from the transaction and the GUID in the publication are compared.</span></span> <span data-ttu-id="4cd43-118">如果事务中存储的旧 GUID 与发布中的 GUID 相匹配，则将更新发布并将订阅服务器生成的新 GUID 分配给行。</span><span class="sxs-lookup"><span data-stu-id="4cd43-118">If the old GUID stored in the transaction matches the GUID in the publication, the publication is updated and the row is assigned the new GUID that was generated by the Subscriber.</span></span> <span data-ttu-id="4cd43-119">通过用事务的 GUID 更新发布，可以使发布与事务中的行版本相匹配。</span><span class="sxs-lookup"><span data-stu-id="4cd43-119">By updating the publication with the GUID from the transaction, you have matching row versions in the publication and in the transaction.</span></span>  
  
 <span data-ttu-id="4cd43-120">如果事务中存储的旧 GUID 与发布中的 GUID 不匹配，便检测到了冲突。</span><span class="sxs-lookup"><span data-stu-id="4cd43-120">If the old GUID stored in the transaction does not match the GUID in the publication, a conflict is detected.</span></span> <span data-ttu-id="4cd43-121">发布中的新 GUID 指示存在两个不同的行版本：一个版本位于订阅服务器正在提交的事务中，较新版本位于发布服务器中。</span><span class="sxs-lookup"><span data-stu-id="4cd43-121">The new GUID in the publication indicates that two different row versions exist: one in the transaction being submitted by the Subscriber and a newer one that exists on the Publisher.</span></span> <span data-ttu-id="4cd43-122">在这种情况下，在本订阅服务器事务同步之前，另一个订阅服务器或发布服务器更新了发布中的同一行。</span><span class="sxs-lookup"><span data-stu-id="4cd43-122">In this case, another Subscriber or the Publisher updated the same row in the publication before this Subscriber transaction was synchronized.</span></span>  
  
 <span data-ttu-id="4cd43-123">与合并复制不同，使用 GUID 列的目的不是标识行本身，而是检查行是否已更改。</span><span class="sxs-lookup"><span data-stu-id="4cd43-123">Unlike merge replication, the use of a GUID column is not used to identify the row itself, but is used to check if the row has changed.</span></span>  
  
## <a name="resolving-conflicts"></a><span data-ttu-id="4cd43-124">解决冲突</span><span class="sxs-lookup"><span data-stu-id="4cd43-124">Resolving Conflicts</span></span>  
 <span data-ttu-id="4cd43-125">使用排队更新创建发布时，请选择在检测到任何冲突时要使用的冲突解决程序。</span><span class="sxs-lookup"><span data-stu-id="4cd43-125">When you create a publication using queued updating, you select a conflict resolver to be used if any conflicts are detected.</span></span> <span data-ttu-id="4cd43-126">冲突解决程序控制队列读取器代理如何处理在同步过程中遇到的相同行的不同版本。</span><span class="sxs-lookup"><span data-stu-id="4cd43-126">The conflict resolver governs how the Queue Reader Agent handles different versions of the same row encountered during synchronization.</span></span> <span data-ttu-id="4cd43-127">创建发布后，只要该发布未被订阅，就可以更改冲突解决策略。</span><span class="sxs-lookup"><span data-stu-id="4cd43-127">You can change the conflict resolution policy after the publication is created as long as there are no subscriptions to the publication.</span></span> <span data-ttu-id="4cd43-128">可以选择下列冲突解决程序：</span><span class="sxs-lookup"><span data-stu-id="4cd43-128">The conflict resolver choices are the following:</span></span>  
  
-   <span data-ttu-id="4cd43-129">发布服务器入选（默认）</span><span class="sxs-lookup"><span data-stu-id="4cd43-129">Publisher wins (the default)</span></span>  
  
-   <span data-ttu-id="4cd43-130">发布服务器入选并且重新初始化订阅</span><span class="sxs-lookup"><span data-stu-id="4cd43-130">Publisher wins and the subscription is reinitialized</span></span>  
  
-   <span data-ttu-id="4cd43-131">订阅服务器入选</span><span class="sxs-lookup"><span data-stu-id="4cd43-131">Subscriber wins</span></span>  
  
 <span data-ttu-id="4cd43-132">将记录冲突并可使用冲突查看器进行查看。</span><span class="sxs-lookup"><span data-stu-id="4cd43-132">Conflicts are recorded and can be viewed using the Conflict Viewer.</span></span>  
  
 <span data-ttu-id="4cd43-133">**设置排队更新冲突解决策略**</span><span class="sxs-lookup"><span data-stu-id="4cd43-133">**To set the queued updating conflict resolution policy**</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]<span data-ttu-id="4cd43-134">：[设置排队更新冲突解决选项 (SQL Server Management Studio)](../publish/create-an-updatable-subscription-to-a-transactional-publication.md)</span><span class="sxs-lookup"><span data-stu-id="4cd43-134">: [Set Queued Updating Conflict Resolution Options &#40;SQL Server Management Studio&#41;](../publish/create-an-updatable-subscription-to-a-transactional-publication.md)</span></span>  
  
-   <span data-ttu-id="4cd43-135">复制 Transact-SQL 编程： [允许更新事务发布的订阅](../publish/enable-updating-subscriptions-for-transactional-publications.md)。</span><span class="sxs-lookup"><span data-stu-id="4cd43-135">Replication Transact-SQL programming: [Enable Updating Subscriptions for Transactional Publications](../publish/enable-updating-subscriptions-for-transactional-publications.md)</span></span>  
  
 <span data-ttu-id="4cd43-136">**查看数据冲突**</span><span class="sxs-lookup"><span data-stu-id="4cd43-136">**To view data conflicts**</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]<span data-ttu-id="4cd43-137">：[查看事务发布的数据冲突 (SQL Server Management Studio)](../view-data-conflicts-for-transactional-publications-sql-server-management-studio.md)</span><span class="sxs-lookup"><span data-stu-id="4cd43-137">: [View Data Conflicts for Transactional Publications &#40;SQL Server Management Studio&#41;](../view-data-conflicts-for-transactional-publications-sql-server-management-studio.md)</span></span>  
  
### <a name="publisher-wins"></a><span data-ttu-id="4cd43-138">发布服务器入选</span><span class="sxs-lookup"><span data-stu-id="4cd43-138">Publisher Wins</span></span>  
 <span data-ttu-id="4cd43-139">如果将冲突解决设置为服务器入选，将根据发布服务器中的数据保持事务的一致性。</span><span class="sxs-lookup"><span data-stu-id="4cd43-139">When the conflict resolution is set to the Publisher wins, transactional consistency is maintained based on the data at the Publisher.</span></span> <span data-ttu-id="4cd43-140">冲突的事务将回滚到启动该事务的订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="4cd43-140">The conflicting transaction is rolled back at the Subscriber that initiated it.</span></span>  
  
 <span data-ttu-id="4cd43-141">队列读取器代理检测冲突，生成补偿命令并通过在分发数据库中发布这些命令来将其传播到订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="4cd43-141">The Queue Reader Agent detects a conflict and compensating commands are generated and propagated to the Subscriber by posting them in the distribution database.</span></span> <span data-ttu-id="4cd43-142">然后，分发代理将补偿命令应用到引起冲突事务的订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="4cd43-142">The Distribution Agent then applies the compensating commands to the Subscriber that originated the conflicting transaction.</span></span> <span data-ttu-id="4cd43-143">补偿操作更新订阅服务器中的行，使其与发布服务器中的行相匹配。</span><span class="sxs-lookup"><span data-stu-id="4cd43-143">The compensating actions update the rows on the Subscriber to match the rows on the Publisher.</span></span>  
  
 <span data-ttu-id="4cd43-144">在应用补偿命令之前，可以读取最终将回滚到订阅服务器的事务结果。</span><span class="sxs-lookup"><span data-stu-id="4cd43-144">Until the compensating commands are applied, it is possible to read the results of a transaction that will eventually be rolled back at the Subscriber.</span></span> <span data-ttu-id="4cd43-145">这相当于脏读（未提交读隔离级别）。</span><span class="sxs-lookup"><span data-stu-id="4cd43-145">This is equivalent to a dirty read (read uncommitted isolation level).</span></span> <span data-ttu-id="4cd43-146">可能发生的后续相关事务无补偿。</span><span class="sxs-lookup"><span data-stu-id="4cd43-146">There is no compensation for the subsequent dependent transactions that can occur.</span></span> <span data-ttu-id="4cd43-147">但是，事务边界将得到遵守，并且事务中的所有操作都将提交，或者在发生冲突时回滚。</span><span class="sxs-lookup"><span data-stu-id="4cd43-147">However, transaction boundaries are honored and all the actions within a transaction are either committed, or in the case of a conflict, rolled back.</span></span>  
  
### <a name="publisher-wins-and-the-subscription-is-reinitialized"></a><span data-ttu-id="4cd43-148">发布服务器入选并且重新初始化订阅</span><span class="sxs-lookup"><span data-stu-id="4cd43-148">Publisher Wins and the Subscription Is Reinitialized</span></span>  
 <span data-ttu-id="4cd43-149">通过重新初始化订阅服务器来解决冲突可以保持订阅服务器中严格的事务一致性，但如果发布包含大量数据，则这一操作会十分耗时。</span><span class="sxs-lookup"><span data-stu-id="4cd43-149">Reinitializing the Subscriber to resolve conflicts maintains strict transactional consistency at the Subscriber, but it can be time consuming if the publication contains large amounts of data.</span></span>  
  
 <span data-ttu-id="4cd43-150">如果队列读取器代理检测到冲突，将拒绝队列中所有剩余的事务（包括冲突中的事务），并将订阅服务器标记为要重新初始化。</span><span class="sxs-lookup"><span data-stu-id="4cd43-150">When the Queue Reader Agent detects a conflict, all remaining transactions in the queue (including the transaction in conflict) are rejected, and the Subscriber is marked for reinitialization.</span></span> <span data-ttu-id="4cd43-151">为发布生成的下一个快照将由分发代理应用到订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="4cd43-151">The next snapshot generated for the publication is applied by the Distribution Agent to the Subscriber.</span></span>  
  
### <a name="subscriber-wins"></a><span data-ttu-id="4cd43-152">订阅服务器入选</span><span class="sxs-lookup"><span data-stu-id="4cd43-152">Subscriber Wins</span></span>  
 <span data-ttu-id="4cd43-153">使用订阅服务器入选策略下的冲突检测意味着要更新发布服务器的最后一项订阅服务器事务入选。</span><span class="sxs-lookup"><span data-stu-id="4cd43-153">Conflict detection under the Subscriber wins policy means the last Subscriber transaction to update the Publisher wins.</span></span> <span data-ttu-id="4cd43-154">在这种情况下，如果检测到冲突，将仍使用订阅服务器发送的事务，并更新发布服务器。</span><span class="sxs-lookup"><span data-stu-id="4cd43-154">In this case, when a conflict is detected, the transaction sent by the Subscriber is still used and the Publisher is updated.</span></span> <span data-ttu-id="4cd43-155">此策略适用于此类更改不会危及数据完整性的应用程序。</span><span class="sxs-lookup"><span data-stu-id="4cd43-155">This policy is suitable for applications where such changes do not compromise data integrity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cd43-156">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4cd43-156">See Also</span></span>  
 [<span data-ttu-id="4cd43-157">Updatable Subscriptions for Transactional Replication</span><span class="sxs-lookup"><span data-stu-id="4cd43-157">Updatable Subscriptions for Transactional Replication</span></span>](updatable-subscriptions-for-transactional-replication.md)  
  
  
