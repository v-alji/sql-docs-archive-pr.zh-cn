---
title: 重新初始化订阅 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- initializing subscriptions [SQL Server replication], reinitializing
- subscriptions [SQL Server replication], reinitializing
- reinitializing subscriptions
ms.assetid: ca3625c5-c62e-4ab7-9829-d511f838e385
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f751928c05caa5c4acdcc6c667dc59bb7824021b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693724"
---
# <a name="reinitialize-a-subscription"></a><span data-ttu-id="e51f2-102">重新初始化订阅</span><span class="sxs-lookup"><span data-stu-id="e51f2-102">Reinitialize a Subscription</span></span>
  <span data-ttu-id="e51f2-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]或复制管理对象 (RMO) 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中重新初始化订阅。</span><span class="sxs-lookup"><span data-stu-id="e51f2-103">This topic describes how to reinitialize a subscription in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or Replication Management Objects (RMO).</span></span> <span data-ttu-id="e51f2-104">可以将各个订阅标记为重新初始化，以便在下次同步期间应用新快照。</span><span class="sxs-lookup"><span data-stu-id="e51f2-104">Individual subscriptions can be marked for reinitialization so that a new snapshot is applied during the next synchronization.</span></span>  
  
 <span data-ttu-id="e51f2-105">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="e51f2-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="e51f2-106">**重新初始化订阅，使用：**</span><span class="sxs-lookup"><span data-stu-id="e51f2-106">**To reinitialize a subscription, using:**</span></span>  
  
     [<span data-ttu-id="e51f2-107">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e51f2-107">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="e51f2-108">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e51f2-108">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="e51f2-109">复制管理对象 (RMO)</span><span class="sxs-lookup"><span data-stu-id="e51f2-109">Replication Management Objects (RMO)</span></span>](#RMOProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="e51f2-110">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e51f2-110">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="e51f2-111">重新初始化订阅的过程由两个部分组成：</span><span class="sxs-lookup"><span data-stu-id="e51f2-111">Reinitializing a subscription is a two-part process:</span></span>  
  
1.  <span data-ttu-id="e51f2-112">将对发布的单个或所有订阅“标记”  为重新初始化。</span><span class="sxs-lookup"><span data-stu-id="e51f2-112">A single subscription or all subscriptions to a publication are *marked* for reinitialization.</span></span> <span data-ttu-id="e51f2-113">在“重新初始化订阅”对话框中将订阅标记为重新初始化，该对话框可从 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中的“本地发布”文件夹和“本地订阅”文件夹中获取  。</span><span class="sxs-lookup"><span data-stu-id="e51f2-113">Mark subscriptions for reinitialization in the **Reinitialize Subscription(s)** dialog box, which is available from the **Local Publications** folder and the **Local Subscriptions** folder in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="e51f2-114">也可以从 **“所有订阅”** 选项卡和复制监视器中的发布节点中对订阅进行标记。</span><span class="sxs-lookup"><span data-stu-id="e51f2-114">You can also mark subscriptions from the **All Subscriptions** tab and the publications node in Replication Monitor.</span></span> <span data-ttu-id="e51f2-115">有关启动复制监视器的信息，请参阅[启动复制监视器](monitor/start-the-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="e51f2-115">For information about starting Replication Monitor, see [Start the Replication Monitor](monitor/start-the-replication-monitor.md).</span></span> <span data-ttu-id="e51f2-116">将订阅标记为要重新初始化时，可以选择下列选项之一：</span><span class="sxs-lookup"><span data-stu-id="e51f2-116">When you mark a subscription for reinitialization, you have the following options:</span></span>  
  
     <span data-ttu-id="e51f2-117">**使用当前快照**</span><span class="sxs-lookup"><span data-stu-id="e51f2-117">**Use the current snapshot**</span></span>  
     <span data-ttu-id="e51f2-118">选择此项可以在分发代理或合并代理下一次运行时将当前快照应用于订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="e51f2-118">Select to apply the current snapshot to the Subscriber the next time the Distribution Agent or Merge Agent runs.</span></span> <span data-ttu-id="e51f2-119">如果无法获得有效快照，将无法选定此选项。</span><span class="sxs-lookup"><span data-stu-id="e51f2-119">If there is no valid snapshot available, this option cannot be selected.</span></span>  
  
     <span data-ttu-id="e51f2-120">**使用新快照**</span><span class="sxs-lookup"><span data-stu-id="e51f2-120">**Use a new snapshot**</span></span>  
     <span data-ttu-id="e51f2-121">选择此项可以用新的快照来重新初始化订阅。</span><span class="sxs-lookup"><span data-stu-id="e51f2-121">Select to reinitialize the subscription with a new snapshot.</span></span> <span data-ttu-id="e51f2-122">只有在快照代理已经生成新快照之后，才能将其应用于订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="e51f2-122">The snapshot can be applied to the Subscriber only after it has been generated by the Snapshot Agent.</span></span> <span data-ttu-id="e51f2-123">如果快照代理设置为按计划运行，则直到下一个计划的快照代理运行后才能重新初始化订阅。</span><span class="sxs-lookup"><span data-stu-id="e51f2-123">If the Snapshot Agent is set to run on a schedule, the subscription is not reinitialized until after the next scheduled Snapshot Agent run.</span></span> <span data-ttu-id="e51f2-124">选择 **“立即生成新快照”** 可以立即启动快照代理。</span><span class="sxs-lookup"><span data-stu-id="e51f2-124">Select **Generate the new snapshot now** to start the Snapshot Agent immediately.</span></span>  
  
     <span data-ttu-id="e51f2-125">**在重新初始化之前上载未同步的更改**</span><span class="sxs-lookup"><span data-stu-id="e51f2-125">**Upload unsynchronized changes before reinitialization**</span></span>  
     <span data-ttu-id="e51f2-126">仅限合并复制。</span><span class="sxs-lookup"><span data-stu-id="e51f2-126">Merge replication only.</span></span> <span data-ttu-id="e51f2-127">选择此项可以在用快照覆盖订阅服务器上的数据之前，从订阅数据库上载任何挂起的更改。</span><span class="sxs-lookup"><span data-stu-id="e51f2-127">Select to upload any pending changes from the subscription database before the data at the Subscriber is overwritten with a snapshot.</span></span>  
  
     <span data-ttu-id="e51f2-128">如果添加、删除或更改参数化筛选器，则订阅服务器上挂起的更改在重新初始化期间将无法上载到发布服务器。</span><span class="sxs-lookup"><span data-stu-id="e51f2-128">If you add, drop, or change a parameterized filter, pending changes at the Subscriber cannot be uploaded to the Publisher during reinitialization.</span></span> <span data-ttu-id="e51f2-129">若要上载挂起的更改，请在更改筛选器前同步所有订阅。</span><span class="sxs-lookup"><span data-stu-id="e51f2-129">If you want to upload pending changes, synchronize all subscriptions before changing the filter.</span></span>  
  
2.  <span data-ttu-id="e51f2-130">在下次同步订阅时将重新初始化订阅：分发代理（用于事务复制）或合并代理（用于合并复制）将最近的快照应用于每个包含有标记为要重新初始化的订阅的订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="e51f2-130">A subscription is reinitialized the next time it is synchronized: the Distribution Agent (for transactional replication) or Merge Agent (for merge replication) applies the most recent snapshot to each Subscriber that has a subscription marked for reinitialization.</span></span> <span data-ttu-id="e51f2-131">有关同步订阅的详细信息，请参阅 [Synchronize a Push Subscription](synchronize-a-push-subscription.md) 和 [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md)文件夹中打开。</span><span class="sxs-lookup"><span data-stu-id="e51f2-131">For more information about synchronizing subscriptions, see [Synchronize a Push Subscription](synchronize-a-push-subscription.md) and [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md).</span></span>  
  
#### <a name="to-mark-a-single-push-or-pull-subscription-for-reinitialization-in-management-studio-at-the-publisher"></a><span data-ttu-id="e51f2-132">在 Management Studio 中将单个推送订阅或单个请求订阅（位于发布服务器上）标记为要重新初始化</span><span class="sxs-lookup"><span data-stu-id="e51f2-132">To mark a single push or pull subscription for reinitialization in Management Studio (at the Publisher)</span></span>  
  
1.  <span data-ttu-id="e51f2-133">在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中连接到发布服务器，然后展开服务器节点。</span><span class="sxs-lookup"><span data-stu-id="e51f2-133">Connect to the Publisher in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="e51f2-134">展开 **“复制”** 文件夹，再展开 **“本地发布”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="e51f2-134">Expand the **Replication** folder, and then expand the **Local Publications** folder.</span></span>  
  
3.  <span data-ttu-id="e51f2-135">展开包含要重新初始化的订阅的发布。</span><span class="sxs-lookup"><span data-stu-id="e51f2-135">Expand the publication that has the subscription you want to reinitialize.</span></span>  
  
4.  <span data-ttu-id="e51f2-136">右键单击订阅，再单击 **“重新初始化”** 。</span><span class="sxs-lookup"><span data-stu-id="e51f2-136">Right-click the subscription, and then click **Reinitialize**.</span></span>  
  
5.  <span data-ttu-id="e51f2-137">在 **“重新初始化订阅”** 对话框中，选择选项，然后单击 **“标记为要重新初始化”** 。</span><span class="sxs-lookup"><span data-stu-id="e51f2-137">In the **Reinitialize Subscription(s)** dialog box, select options, and then click **Mark for Reinitialization**.</span></span>  
  
#### <a name="to-mark-a-single-pull-subscription-for-reinitialization-in-management-studio-at-the-subscriber"></a><span data-ttu-id="e51f2-138">在 Management Studio 中将单个请求订阅（位于订阅服务器）标记为要重新初始化</span><span class="sxs-lookup"><span data-stu-id="e51f2-138">To mark a single pull subscription for reinitialization in Management Studio (at the Subscriber)</span></span>  
  
1.  <span data-ttu-id="e51f2-139">在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中连接到订阅服务器，然后展开服务器节点。</span><span class="sxs-lookup"><span data-stu-id="e51f2-139">Connect to the Subscriber in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="e51f2-140">展开 **“复制”** 文件夹，再展开 **“本地订阅”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="e51f2-140">Expand the **Replication** folder, and then expand the **Local Subscriptions** folder.</span></span>  
  
3.  <span data-ttu-id="e51f2-141">右键单击订阅，再单击 **“重新初始化”** 。</span><span class="sxs-lookup"><span data-stu-id="e51f2-141">Right-click the subscription, and then click **Reinitialize**.</span></span>  
  
4.  <span data-ttu-id="e51f2-142">在显示的确认对话框中，单击 **“是”** 。</span><span class="sxs-lookup"><span data-stu-id="e51f2-142">In the confirmation dialog box that is displayed, click **Yes**.</span></span>  
  
#### <a name="to-mark-all-subscriptions-for-reinitialization-in-management-studio"></a><span data-ttu-id="e51f2-143">在 Management Studio 中将所有订阅标记为要重新初始化</span><span class="sxs-lookup"><span data-stu-id="e51f2-143">To mark all subscriptions for reinitialization in Management Studio</span></span>  
  
1.  <span data-ttu-id="e51f2-144">在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中连接到发布服务器，然后展开服务器节点。</span><span class="sxs-lookup"><span data-stu-id="e51f2-144">Connect to the Publisher in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="e51f2-145">展开 **“复制”** 文件夹，再展开 **“本地发布”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="e51f2-145">Expand the **Replication** folder, and then expand the **Local Publications** folder.</span></span>  
  
3.  <span data-ttu-id="e51f2-146">右键单击具有要重新初始化的订阅的发布，再单击 **“重新初始化所有订阅”** 。</span><span class="sxs-lookup"><span data-stu-id="e51f2-146">Right-click the publication with subscriptions you want to reinitialize, and then click **Reinitialize All Subscriptions**.</span></span>  
  
4.  <span data-ttu-id="e51f2-147">在 **“重新初始化订阅”** 对话框中，选择选项，然后单击 **“标记为要重新初始化”** 。</span><span class="sxs-lookup"><span data-stu-id="e51f2-147">In the **Reinitialize Subscription(s)** dialog box, select options, and then click **Mark for Reinitialization**.</span></span>  
  
#### <a name="to-mark-a-single-push-or-pull-subscription-for-reinitialization-in-replication-monitor"></a><span data-ttu-id="e51f2-148">在复制监视器中将单个推送订阅或单个请求订阅标记为要重新初始化</span><span class="sxs-lookup"><span data-stu-id="e51f2-148">To mark a single push or pull subscription for reinitialization in Replication Monitor</span></span>  
  
1.  <span data-ttu-id="e51f2-149">在复制监视器的左窗格中依次展开发布服务器组、发布服务器，再单击一个发布。</span><span class="sxs-lookup"><span data-stu-id="e51f2-149">In Replication Monitor, expand a Publisher group in the left pane, expand a Publisher, and then click a publication.</span></span>  
  
2.  <span data-ttu-id="e51f2-150">单击 **“所有订阅”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="e51f2-150">Click the **All Subscriptions** tab.</span></span>  
  
3.  <span data-ttu-id="e51f2-151">右键单击要重新初始化的订阅，然后单击 **“重新初始化订阅”** 。</span><span class="sxs-lookup"><span data-stu-id="e51f2-151">Right-click the subscription you want to reinitialize, and then click **Reinitialize Subscription**.</span></span>  
  
4.  <span data-ttu-id="e51f2-152">在 **“重新初始化订阅”** 对话框中，选择选项，然后单击 **“标记为要重新初始化”** 。</span><span class="sxs-lookup"><span data-stu-id="e51f2-152">In the **Reinitialize Subscription(s)** dialog box, select options, and then click **Mark for Reinitialization**.</span></span>  
  
#### <a name="to-mark-all-subscriptions-for-reinitialization-in-replication-monitor"></a><span data-ttu-id="e51f2-153">在复制监视器中将所有订阅标记为要重新初始化</span><span class="sxs-lookup"><span data-stu-id="e51f2-153">To mark all subscriptions for reinitialization in Replication Monitor</span></span>  
  
1.  <span data-ttu-id="e51f2-154">在复制监视器的左窗格中依次展开发布服务器组、发布服务器。</span><span class="sxs-lookup"><span data-stu-id="e51f2-154">In Replication Monitor, expand a Publisher group in the left pane, and then expand a Publisher.</span></span>  
  
2.  <span data-ttu-id="e51f2-155">右键单击具有要重新初始化的订阅的发布，再单击 **“重新初始化所有订阅”** 。</span><span class="sxs-lookup"><span data-stu-id="e51f2-155">Right-click the publication with subscriptions you want to reinitialize, and then click **Reinitialize All Subscriptions**.</span></span>  
  
3.  <span data-ttu-id="e51f2-156">在 **“重新初始化订阅”** 对话框中，选择选项，然后单击 **“标记为要重新初始化”** 。</span><span class="sxs-lookup"><span data-stu-id="e51f2-156">In the **Reinitialize Subscription(s)** dialog box, select options, and then click **Mark for Reinitialization**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="e51f2-157">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e51f2-157">Using Transact-SQL</span></span>  
 <span data-ttu-id="e51f2-158">可以使用复制存储过程以编程方式重新初始化订阅。</span><span class="sxs-lookup"><span data-stu-id="e51f2-158">Subscriptions can be reinitialized programmatically using replication stored procedures.</span></span> <span data-ttu-id="e51f2-159">使用的存储过程取决于订阅的类型（推送或请求）以及订阅所属的发布的类型。</span><span class="sxs-lookup"><span data-stu-id="e51f2-159">The stored procedure that is used depends on the type of subscription (push or pull) and the type of publication to which the subscription belongs.</span></span>  
  
#### <a name="to-reinitialize-a-pull-subscription-to-a-transactional-publication"></a><span data-ttu-id="e51f2-160">重新初始化对事务发布的请求订阅</span><span class="sxs-lookup"><span data-stu-id="e51f2-160">To reinitialize a pull subscription to a transactional publication</span></span>  
  
1.  <span data-ttu-id="e51f2-161">在订阅服务器上，对订阅数据库执行 [sp_reinitpullsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-reinitpullsubscription-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="e51f2-161">At the Subscriber on the subscription database, execute [sp_reinitpullsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-reinitpullsubscription-transact-sql).</span></span> <span data-ttu-id="e51f2-162">指定 **@publisher** 、 **@publisher_db** 和 **@publication** 。</span><span class="sxs-lookup"><span data-stu-id="e51f2-162">Specify **@publisher**, **@publisher_db**, and **@publication**.</span></span> <span data-ttu-id="e51f2-163">这会将订阅标记为在下一次运行分发代理时将要重新初始化。</span><span class="sxs-lookup"><span data-stu-id="e51f2-163">This marks the subscription for reinitialization the next time the Distribution Agent runs.</span></span>  
  
2.  <span data-ttu-id="e51f2-164">（可选）在订阅服务器上启动分发代理，以使订阅同步。</span><span class="sxs-lookup"><span data-stu-id="e51f2-164">(Optional) Start the Distribution Agent at the Subscriber to synchronize the subscription.</span></span> <span data-ttu-id="e51f2-165">有关详细信息，请参阅 [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="e51f2-165">For more information, see [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md).</span></span>  
  
#### <a name="to-reinitialize-a-push-subscription-to-a-transactional-publication"></a><span data-ttu-id="e51f2-166">重新初始化对事务发布的推送订阅</span><span class="sxs-lookup"><span data-stu-id="e51f2-166">To reinitialize a push subscription to a transactional publication</span></span>  
  
1.  <span data-ttu-id="e51f2-167">在发布服务器上，执行 [sp_reinitsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-reinitsubscription-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="e51f2-167">At the Publisher, execute [sp_reinitsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-reinitsubscription-transact-sql).</span></span> <span data-ttu-id="e51f2-168">指定 **@publication** 、 **@subscriber** 和 **@destination_db** 。</span><span class="sxs-lookup"><span data-stu-id="e51f2-168">Specify **@publication**, **@subscriber**, and **@destination_db**.</span></span> <span data-ttu-id="e51f2-169">这会将订阅标记为在下一次运行分发代理时将要重新初始化。</span><span class="sxs-lookup"><span data-stu-id="e51f2-169">This marks the subscription for reinitialization the next time the Distribution Agent runs.</span></span>  
  
2.  <span data-ttu-id="e51f2-170">（可选）在分发服务器上启动分发代理，以使订阅同步。</span><span class="sxs-lookup"><span data-stu-id="e51f2-170">(Optional) Start the Distribution Agent at the Distributor to synchronize the subscription.</span></span> <span data-ttu-id="e51f2-171">有关详细信息，请参阅 [同步推送订阅](synchronize-a-push-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="e51f2-171">For more information, see [Synchronize a Push Subscription](synchronize-a-push-subscription.md).</span></span>  
  
#### <a name="to-reinitialize-a-pull-subscription-to-a-merge-publication"></a><span data-ttu-id="e51f2-172">重新初始化对合并发布的请求订阅</span><span class="sxs-lookup"><span data-stu-id="e51f2-172">To reinitialize a pull subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="e51f2-173">在订阅服务器上，对订阅数据库执行 [sp_reinitmergepullsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-reinitmergepullsubscription-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="e51f2-173">At the Subscriber on the subscription database, execute [sp_reinitmergepullsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-reinitmergepullsubscription-transact-sql).</span></span> <span data-ttu-id="e51f2-174">指定 **@publisher** 、 **@publisher_db** 和 **@publication** 。</span><span class="sxs-lookup"><span data-stu-id="e51f2-174">Specify **@publisher**, **@publisher_db**, and **@publication**.</span></span> <span data-ttu-id="e51f2-175">若要在进行重新初始化之前从订阅服务器上载更改，请将的值指定 `true` 为 **@upload_first** 。</span><span class="sxs-lookup"><span data-stu-id="e51f2-175">To upload changes from the Subscriber before reinitialization occurs, specify a value of `true` for **@upload_first**.</span></span> <span data-ttu-id="e51f2-176">这会将订阅标记为在下一次运行合并代理时将要重新初始化。</span><span class="sxs-lookup"><span data-stu-id="e51f2-176">This marks the subscription for reinitialization the next time the Merge Agent runs.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="e51f2-177">如果添加、删除或更改参数化筛选器，则订阅服务器上挂起的更改在重新初始化期间将无法上载到发布服务器。</span><span class="sxs-lookup"><span data-stu-id="e51f2-177">If you add, drop, or change a parameterized filter, pending changes at the Subscriber cannot be uploaded to the Publisher during reinitialization.</span></span> <span data-ttu-id="e51f2-178">若要上载挂起的更改，请在更改筛选器前同步所有订阅。</span><span class="sxs-lookup"><span data-stu-id="e51f2-178">If you want to upload pending changes, synchronize all subscriptions before changing the filter.</span></span>  
  
2.  <span data-ttu-id="e51f2-179">（可选）在订阅服务器上启动合并代理，以使订阅同步。</span><span class="sxs-lookup"><span data-stu-id="e51f2-179">(Optional) Start the Merge Agent at the Subscriber to synchronize the subscription.</span></span> <span data-ttu-id="e51f2-180">有关详细信息，请参阅 [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="e51f2-180">For more information, see [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md).</span></span>  
  
#### <a name="to-reinitialize-a-push-subscription-to-a-merge-publication"></a><span data-ttu-id="e51f2-181">重新初始化对合并发布的推送订阅</span><span class="sxs-lookup"><span data-stu-id="e51f2-181">To reinitialize a push subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="e51f2-182">在发布服务器上，执行 [sp_reinitmergesubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-reinitmergesubscription-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="e51f2-182">At the Publisher, execute [sp_reinitmergesubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-reinitmergesubscription-transact-sql).</span></span> <span data-ttu-id="e51f2-183">指定 **@publication** 、 **@subscriber** 和 **@subscriber_db** 。</span><span class="sxs-lookup"><span data-stu-id="e51f2-183">Specify **@publication**, **@subscriber**, and **@subscriber_db**.</span></span> <span data-ttu-id="e51f2-184">若要在进行重新初始化之前从订阅服务器上载更改，请将的值指定 `true` 为 **@upload_first** 。</span><span class="sxs-lookup"><span data-stu-id="e51f2-184">To upload changes from the Subscriber before reinitialization occurs, specify a value of `true` for **@upload_first**.</span></span> <span data-ttu-id="e51f2-185">这会将订阅标记为在下一次运行分发代理时将要重新初始化。</span><span class="sxs-lookup"><span data-stu-id="e51f2-185">This marks the subscription for reinitialization the next time the Distribution Agent runs.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="e51f2-186">如果添加、删除或更改参数化筛选器，则订阅服务器上挂起的更改在重新初始化期间将无法上载到发布服务器。</span><span class="sxs-lookup"><span data-stu-id="e51f2-186">If you add, drop, or change a parameterized filter, pending changes at the Subscriber cannot be uploaded to the Publisher during reinitialization.</span></span> <span data-ttu-id="e51f2-187">若要上载挂起的更改，请在更改筛选器前同步所有订阅。</span><span class="sxs-lookup"><span data-stu-id="e51f2-187">If you want to upload pending changes, synchronize all subscriptions before changing the filter.</span></span>  
  
2.  <span data-ttu-id="e51f2-188">（可选）在分发服务器上启动合并代理，以使订阅同步。</span><span class="sxs-lookup"><span data-stu-id="e51f2-188">(Optional) Start the Merge Agent at the Distributor to synchronize the subscription.</span></span> <span data-ttu-id="e51f2-189">有关详细信息，请参阅 [同步推送订阅](synchronize-a-push-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="e51f2-189">For more information, see [Synchronize a Push Subscription](synchronize-a-push-subscription.md).</span></span>  
  
#### <a name="to-set-the-reinitialization-policy-when-creating-a-new-merge-publication"></a><span data-ttu-id="e51f2-190">创建新的合并发布时设置重新初始化策略</span><span class="sxs-lookup"><span data-stu-id="e51f2-190">To set the reinitialization policy when creating a new merge publication</span></span>  
  
1.  <span data-ttu-id="e51f2-191">在发布服务器上，对发布数据库执行 [sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)，同时为 **@automatic_reinitialization_policy**指定下列值之一：</span><span class="sxs-lookup"><span data-stu-id="e51f2-191">At the Publisher on the publication database, execute [sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql), specifying one of the following values for **@automatic_reinitialization_policy**:</span></span>  
  
    -   <span data-ttu-id="e51f2-192">**1** - 在对订阅执行更改所要求的自动重新初始化操作之前，从订阅服务器上载更改。</span><span class="sxs-lookup"><span data-stu-id="e51f2-192">**1** - changes are uploaded from the Subscriber before a subscription is automatically reinitialized as required by a change to the publication.</span></span>  
  
    -   <span data-ttu-id="e51f2-193">**0** - 在对订阅执行发布更改所要求的自动重新初始化操作时，放弃订阅服务器上的更改。</span><span class="sxs-lookup"><span data-stu-id="e51f2-193">**0** - changes at the Subscriber are discarded when a subscription is automatically reinitialized as required by a change to the publication.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="e51f2-194">如果添加、删除或更改参数化筛选器，则订阅服务器上挂起的更改在重新初始化期间将无法上载到发布服务器。</span><span class="sxs-lookup"><span data-stu-id="e51f2-194">If you add, drop, or change a parameterized filter, pending changes at the Subscriber cannot be uploaded to the Publisher during reinitialization.</span></span> <span data-ttu-id="e51f2-195">若要上载挂起的更改，请在更改筛选器前同步所有订阅。</span><span class="sxs-lookup"><span data-stu-id="e51f2-195">If you want to upload pending changes, synchronize all subscriptions before changing the filter.</span></span>  
  
     <span data-ttu-id="e51f2-196">有关详细信息，请参阅 [Create a Publication](publish/create-a-publication.md)。</span><span class="sxs-lookup"><span data-stu-id="e51f2-196">For more information, see [Create a Publication](publish/create-a-publication.md).</span></span>  
  
#### <a name="to-change-the-reinitialization-policy-for-an-existing-merge-publication"></a><span data-ttu-id="e51f2-197">更改现有合并发布的重新初始化策略</span><span class="sxs-lookup"><span data-stu-id="e51f2-197">To change the reinitialization policy for an existing merge publication</span></span>  
  
1.  <span data-ttu-id="e51f2-198">在发布服务器上，对发布数据库执行 [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)，同时将 **@property** @upload_first **@property** 并为 **@value**指定下列值之一：</span><span class="sxs-lookup"><span data-stu-id="e51f2-198">At the Publisher on the publication database, execute [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql), specifying **automatic_reinitialization_policy** for **@property** and one of the following values for **@value**:</span></span>  
  
    -   <span data-ttu-id="e51f2-199">**1** - 在对订阅执行更改所要求的自动重新初始化操作之前，从订阅服务器上载更改。</span><span class="sxs-lookup"><span data-stu-id="e51f2-199">**1** - changes are uploaded from the Subscriber before a subscription is automatically reinitialized as required by a change to the publication.</span></span>  
  
    -   <span data-ttu-id="e51f2-200">**0** - 在对订阅执行发布更改所要求的自动重新初始化操作时，放弃订阅服务器上的更改。</span><span class="sxs-lookup"><span data-stu-id="e51f2-200">**0** - changes at the Subscriber are discarded when a subscription is automatically reinitialized as required by a change to the publication.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="e51f2-201">如果添加、删除或更改参数化筛选器，则订阅服务器上挂起的更改在重新初始化期间将无法上载到发布服务器。</span><span class="sxs-lookup"><span data-stu-id="e51f2-201">If you add, drop, or change a parameterized filter, pending changes at the Subscriber cannot be uploaded to the Publisher during reinitialization.</span></span> <span data-ttu-id="e51f2-202">若要上载挂起的更改，请在更改筛选器前同步所有订阅。</span><span class="sxs-lookup"><span data-stu-id="e51f2-202">If you want to upload pending changes, synchronize all subscriptions before changing the filter.</span></span>  
  
     <span data-ttu-id="e51f2-203">有关详细信息，请参阅 [View and Modify Publication Properties](publish/view-and-modify-publication-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="e51f2-203">For more information, see [View and Modify Publication Properties](publish/view-and-modify-publication-properties.md).</span></span>  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="e51f2-204">使用复制管理对象 (RMO)</span><span class="sxs-lookup"><span data-stu-id="e51f2-204">Using Replication Management Objects (RMO)</span></span>  
 <span data-ttu-id="e51f2-205">可以将各个订阅标记为重新初始化，以便在下次同步期间应用新的快照。</span><span class="sxs-lookup"><span data-stu-id="e51f2-205">Individual subscriptions can be marked for reinitialization so that during the next synchronization, a new snapshot is applied.</span></span> <span data-ttu-id="e51f2-206">可以使用复制管理对象 (RMO) 以编程的方式重新初始化订阅。</span><span class="sxs-lookup"><span data-stu-id="e51f2-206">Subscriptions can be reinitialized programmatically by using Replication Management Objects (RMO).</span></span> <span data-ttu-id="e51f2-207">所用的类取决于订阅所属的发布类型以及订阅类型（即推送订阅或请求订阅）。</span><span class="sxs-lookup"><span data-stu-id="e51f2-207">The classes you use depend on the type of publication to which the subscription belongs and the type of subscription (that is, a push or pull subscription).</span></span>  
  
#### <a name="to-reinitialize-a-pull-subscription-to-a-transactional-publication"></a><span data-ttu-id="e51f2-208">重新初始化对事务发布的请求订阅</span><span class="sxs-lookup"><span data-stu-id="e51f2-208">To reinitialize a pull subscription to a transactional publication</span></span>  
  
1.  <span data-ttu-id="e51f2-209">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 类创建与订阅服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="e51f2-209">Create a connection to the Subscriber by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="e51f2-210">创建 <xref:Microsoft.SqlServer.Replication.TransPullSubscription> 类的实例，并设置 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>、 <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>、 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>、 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A>以及步骤 1 中 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>的连接。</span><span class="sxs-lookup"><span data-stu-id="e51f2-210">Create an instance of the <xref:Microsoft.SqlServer.Replication.TransPullSubscription> class, and set <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A>, and the connection from step 1 for <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.</span></span>  
  
3.  <span data-ttu-id="e51f2-211">调用 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法获取该对象的属性。</span><span class="sxs-lookup"><span data-stu-id="e51f2-211">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e51f2-212">如果此方法返回 `false`，则步骤 2 中对订阅属性的定义不正确，或者请求订阅不存在。</span><span class="sxs-lookup"><span data-stu-id="e51f2-212">If this method returns `false`, either the subscription properties in step 2 were defined incorrectly or the pull subscription does not exist.</span></span>  
  
4.  <span data-ttu-id="e51f2-213">调用 <xref:Microsoft.SqlServer.Replication.TransPullSubscription.Reinitialize%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="e51f2-213">Call the <xref:Microsoft.SqlServer.Replication.TransPullSubscription.Reinitialize%2A> method.</span></span> <span data-ttu-id="e51f2-214">此方法将订阅标记为要重新初始化。</span><span class="sxs-lookup"><span data-stu-id="e51f2-214">This method marks the subscription for reinitialization.</span></span>  
  
5.  <span data-ttu-id="e51f2-215">同步请求订阅。</span><span class="sxs-lookup"><span data-stu-id="e51f2-215">Synchronize the pull subscription.</span></span> <span data-ttu-id="e51f2-216">有关详细信息，请参阅 [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="e51f2-216">For more information, see [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md).</span></span>  
  
#### <a name="to-reinitialize-a-push-subscription-to-a-transactional-publication"></a><span data-ttu-id="e51f2-217">重新初始化对事务发布的推送订阅</span><span class="sxs-lookup"><span data-stu-id="e51f2-217">To reinitialize a push subscription to a transactional publication</span></span>  
  
1.  <span data-ttu-id="e51f2-218">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 类创建与发布服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="e51f2-218">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="e51f2-219">创建 <xref:Microsoft.SqlServer.Replication.TransSubscription> 类的实例，并设置 <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>、 <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>、 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>、 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>以及步骤 1 中 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>的连接。</span><span class="sxs-lookup"><span data-stu-id="e51f2-219">Create an instance of the <xref:Microsoft.SqlServer.Replication.TransSubscription> class, and set <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>, and the connection from step 1 for <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.</span></span>  
  
3.  <span data-ttu-id="e51f2-220">调用 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法获取该对象的属性。</span><span class="sxs-lookup"><span data-stu-id="e51f2-220">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e51f2-221">如果此方法返回 `false`，则步骤 2 中对订阅属性的定义不正确，或者推送订阅不存在。</span><span class="sxs-lookup"><span data-stu-id="e51f2-221">If this method returns `false`, either the subscription properties in step 2 were defined incorrectly or the push subscription does not exist.</span></span>  
  
4.  <span data-ttu-id="e51f2-222">调用 <xref:Microsoft.SqlServer.Replication.TransSubscription.Reinitialize%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="e51f2-222">Call the <xref:Microsoft.SqlServer.Replication.TransSubscription.Reinitialize%2A> method.</span></span> <span data-ttu-id="e51f2-223">此方法将订阅标记为要重新初始化。</span><span class="sxs-lookup"><span data-stu-id="e51f2-223">This method marks the subscription for reinitialization.</span></span>  
  
5.  <span data-ttu-id="e51f2-224">同步推送订阅。</span><span class="sxs-lookup"><span data-stu-id="e51f2-224">Synchronize the push subscription.</span></span> <span data-ttu-id="e51f2-225">有关详细信息，请参阅 [同步推送订阅](synchronize-a-push-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="e51f2-225">For more information, see [Synchronize a Push Subscription](synchronize-a-push-subscription.md).</span></span>  
  
#### <a name="to-reinitialize-a-pull-subscription-to-a-merge-publication"></a><span data-ttu-id="e51f2-226">重新初始化对合并发布的请求订阅</span><span class="sxs-lookup"><span data-stu-id="e51f2-226">To reinitialize a pull subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="e51f2-227">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 类创建与订阅服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="e51f2-227">Create a connection to the Subscriber by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="e51f2-228">创建 <xref:Microsoft.SqlServer.Replication.MergePullSubscription> 类的实例，并设置 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>、 <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>、 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>、 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A>以及步骤 1 中 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>的连接。</span><span class="sxs-lookup"><span data-stu-id="e51f2-228">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergePullSubscription> class, and set <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A>, and the connection from step 1 for <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.</span></span>  
  
3.  <span data-ttu-id="e51f2-229">调用 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法获取该对象的属性。</span><span class="sxs-lookup"><span data-stu-id="e51f2-229">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e51f2-230">如果此方法返回 `false`，则步骤 2 中对订阅属性的定义不正确，或者请求订阅不存在。</span><span class="sxs-lookup"><span data-stu-id="e51f2-230">If this method returns `false`, either the subscription properties in step 2 were defined incorrectly or the pull subscription does not exist.</span></span>  
  
4.  <span data-ttu-id="e51f2-231">调用 <xref:Microsoft.SqlServer.Replication.MergePullSubscription.Reinitialize%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="e51f2-231">Call the <xref:Microsoft.SqlServer.Replication.MergePullSubscription.Reinitialize%2A> method.</span></span> <span data-ttu-id="e51f2-232">传递 `true` 值以在重新初始化之前上载订阅服务器上的更改，或者传递 `false` 值以重新初始化并丢失订阅服务器上任何挂起的更改。</span><span class="sxs-lookup"><span data-stu-id="e51f2-232">Pass a value of `true` to upload changes at the Subscriber before reinitialization or a value of `false` to reinitialize and lose any pending changes at the Subscriber.</span></span> <span data-ttu-id="e51f2-233">此方法将订阅标记为要重新初始化。</span><span class="sxs-lookup"><span data-stu-id="e51f2-233">This method marks the subscription for reinitialization.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e51f2-234">如果订阅过期，则无法上载更改。</span><span class="sxs-lookup"><span data-stu-id="e51f2-234">Changes cannot be uploaded if the subscription is expired.</span></span> <span data-ttu-id="e51f2-235">有关详细信息，请参阅 [Set the Expiration Period for Subscriptions](publish/set-the-expiration-period-for-subscriptions.md)。</span><span class="sxs-lookup"><span data-stu-id="e51f2-235">For more information, see [Set the Expiration Period for Subscriptions](publish/set-the-expiration-period-for-subscriptions.md).</span></span>  
  
5.  <span data-ttu-id="e51f2-236">同步请求订阅。</span><span class="sxs-lookup"><span data-stu-id="e51f2-236">Synchronize the pull subscription.</span></span> <span data-ttu-id="e51f2-237">有关详细信息，请参阅 [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="e51f2-237">For more information, see [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md).</span></span>  
  
#### <a name="to-reinitialize-a-push-subscription-to-a-merge-publication"></a><span data-ttu-id="e51f2-238">重新初始化对合并发布的推送订阅</span><span class="sxs-lookup"><span data-stu-id="e51f2-238">To reinitialize a push subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="e51f2-239">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 类创建与发布服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="e51f2-239">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="e51f2-240">创建 <xref:Microsoft.SqlServer.Replication.MergeSubscription> 类的实例，并设置 <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>、 <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>、 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>、 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>以及步骤 1 中 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>的连接。</span><span class="sxs-lookup"><span data-stu-id="e51f2-240">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergeSubscription> class, and set <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>, and the connection from step 1 for <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.</span></span>  
  
3.  <span data-ttu-id="e51f2-241">调用 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法获取该对象的属性。</span><span class="sxs-lookup"><span data-stu-id="e51f2-241">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e51f2-242">如果此方法返回 `false`，则步骤 2 中对订阅属性的定义不正确，或者推送订阅不存在。</span><span class="sxs-lookup"><span data-stu-id="e51f2-242">If this method returns `false`, either the subscription properties in step 2 were defined incorrectly or the push subscription does not exist.</span></span>  
  
4.  <span data-ttu-id="e51f2-243">调用 <xref:Microsoft.SqlServer.Replication.MergeSubscription.Reinitialize%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="e51f2-243">Call the <xref:Microsoft.SqlServer.Replication.MergeSubscription.Reinitialize%2A> method.</span></span> <span data-ttu-id="e51f2-244">传递 `true` 值以在重新初始化之前上载订阅服务器上的更改，或者传递 `false` 值以重新初始化并丢失订阅服务器上任何挂起的更改。</span><span class="sxs-lookup"><span data-stu-id="e51f2-244">Pass a value of `true` to upload changes at the Subscriber before reinitialization or a value of `false` to reinitialize and lose any pending changes at the Subscriber.</span></span> <span data-ttu-id="e51f2-245">此方法将订阅标记为要重新初始化。</span><span class="sxs-lookup"><span data-stu-id="e51f2-245">This method marks the subscription for reinitialization.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e51f2-246">如果订阅过期，则无法上载更改。</span><span class="sxs-lookup"><span data-stu-id="e51f2-246">Changes cannot be uploaded if the subscription is expired.</span></span> <span data-ttu-id="e51f2-247">有关详细信息，请参阅 [Set the Expiration Period for Subscriptions](publish/set-the-expiration-period-for-subscriptions.md)。</span><span class="sxs-lookup"><span data-stu-id="e51f2-247">For more information, see [Set the Expiration Period for Subscriptions](publish/set-the-expiration-period-for-subscriptions.md).</span></span>  
  
5.  <span data-ttu-id="e51f2-248">同步推送订阅。</span><span class="sxs-lookup"><span data-stu-id="e51f2-248">Synchronize the push subscription.</span></span> <span data-ttu-id="e51f2-249">有关详细信息，请参阅 [同步推送订阅](synchronize-a-push-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="e51f2-249">For more information, see [Synchronize a Push Subscription](synchronize-a-push-subscription.md).</span></span>  
  
###  <a name="examples-rmo"></a><a name="PShellExample"></a> <span data-ttu-id="e51f2-250">示例 (RMO)</span><span class="sxs-lookup"><span data-stu-id="e51f2-250">Examples (RMO)</span></span>  
 <span data-ttu-id="e51f2-251">此示例将重新初始化事务发布的请求订阅。</span><span class="sxs-lookup"><span data-stu-id="e51f2-251">This example reinitializes a pull subscription to a transactional publication.</span></span>  
  
 [!code-csharp[HowTo#rmo_ReinitTranPullSub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_reinittranpullsub)]  
  
 [!code-vb[HowTo#rmo_vb_ReinitTranPullSub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_reinittranpullsub)]  
  
 <span data-ttu-id="e51f2-252">此示例将在第一次上载订阅服务器上挂起的更改后，重新初始化合并发布的请求订阅。</span><span class="sxs-lookup"><span data-stu-id="e51f2-252">This example reinitializes a pull subscription to a merge publication after first uploading pending changes at the Subscriber.</span></span>  
  
 [!code-csharp[HowTo#rmo_ReinitMergePullSub_WithUpload](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_reinitmergepullsub_withupload)]  
  
 [!code-vb[HowTo#rmo_vb_ReinitMergePullSub_WithUpload](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_reinitmergepullsub_withupload)]  
  
## <a name="see-also"></a><span data-ttu-id="e51f2-253">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e51f2-253">See Also</span></span>  
 <span data-ttu-id="e51f2-254">[重新初始化订阅](reinitialize-subscriptions.md) </span><span class="sxs-lookup"><span data-stu-id="e51f2-254">[Reinitialize Subscriptions](reinitialize-subscriptions.md) </span></span>  
 <span data-ttu-id="e51f2-255">[Replication Management Objects Concepts](concepts/replication-management-objects-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="e51f2-255">[Replication Management Objects Concepts](concepts/replication-management-objects-concepts.md) </span></span>  
 [<span data-ttu-id="e51f2-256">复制安全最佳做法</span><span class="sxs-lookup"><span data-stu-id="e51f2-256">Replication Security Best Practices</span></span>](security/replication-security-best-practices.md)  
  
  
