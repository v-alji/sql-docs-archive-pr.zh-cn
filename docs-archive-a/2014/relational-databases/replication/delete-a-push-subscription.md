---
title: 删除推送订阅 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- removing subscriptions
- push subscriptions [SQL Server replication], deleting
- deleting subscriptions
- subscriptions [SQL Server replication], push
ms.assetid: 3c4847e2-aed9-4488-b45d-8164422bdb10
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 912958e00d117f51c5dc95c0dc1247d278acb0ff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578124"
---
# <a name="delete-a-push-subscription"></a><span data-ttu-id="96136-102">删除推送订阅</span><span class="sxs-lookup"><span data-stu-id="96136-102">Delete a Push Subscription</span></span>
  <span data-ttu-id="96136-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]或复制管理对象 (RMO) 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中删除推送订阅。</span><span class="sxs-lookup"><span data-stu-id="96136-103">This topic describes how to delete a push subscription in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or Replication Management Objects (RMO).</span></span>  
  
 <span data-ttu-id="96136-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="96136-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="96136-105">**删除推送订阅，使用：**</span><span class="sxs-lookup"><span data-stu-id="96136-105">**To delete a push subscription, using:**</span></span>  
  
     [<span data-ttu-id="96136-106">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="96136-106">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="96136-107">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="96136-107">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="96136-108">复制管理对象 (RMO)</span><span class="sxs-lookup"><span data-stu-id="96136-108">Replication Management Objects (RMO)</span></span>](#RMOProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="96136-109">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="96136-109">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="96136-110">删除发布服务器（从 **的** “本地发布” [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]文件夹）或订阅服务器（从 **“本地订阅”** 文件夹）上的推送订阅。</span><span class="sxs-lookup"><span data-stu-id="96136-110">Delete a push subscription at the Publisher (from the **Local Publications** folder in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]) or the Subscriber (from the **Local Subscriptions** folder).</span></span> <span data-ttu-id="96136-111">删除订阅不会从订阅中删除对象或数据，必须对其手动删除。</span><span class="sxs-lookup"><span data-stu-id="96136-111">Deleting a subscription does not remove objects or data from the subscription; they must be removed manually.</span></span>  
  
#### <a name="to-delete-a-push-subscription-at-the-publisher"></a><span data-ttu-id="96136-112">删除发布服务器上的推送订阅</span><span class="sxs-lookup"><span data-stu-id="96136-112">To delete a push subscription at the Publisher</span></span>  
  
1.  <span data-ttu-id="96136-113">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中连接到发布服务器，然后展开服务器节点。</span><span class="sxs-lookup"><span data-stu-id="96136-113">Connect to the Publisher in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="96136-114">展开 **“复制”** 文件夹，再展开 **“本地发布”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="96136-114">Expand the **Replication** folder, and then expand the **Local Publications** folder.</span></span>  
  
3.  <span data-ttu-id="96136-115">展开与要删除的订阅关联的发布。</span><span class="sxs-lookup"><span data-stu-id="96136-115">Expand the publication associated with the subscription you want to delete.</span></span>  
  
4.  <span data-ttu-id="96136-116">右键单击该订阅，再单击 **“删除”** 。</span><span class="sxs-lookup"><span data-stu-id="96136-116">Right-click the subscription, and then click **Delete**.</span></span>  
  
5.  <span data-ttu-id="96136-117">在确认对话框中，选择是否连接到订阅服务器以删除订阅信息。</span><span class="sxs-lookup"><span data-stu-id="96136-117">In the confirmation dialog box, select whether to connect to the Subscriber to delete subscription information.</span></span> <span data-ttu-id="96136-118">如果清除了 **“连接到订阅服务器”** 复选框，则应以后连接到订阅服务器删除信息。</span><span class="sxs-lookup"><span data-stu-id="96136-118">If you clear the **Connect to Subscriber** checkbox, you should connect to the Subscriber later to delete the information.</span></span>  
  
#### <a name="to-delete-a-push-subscription-at-the-subscriber"></a><span data-ttu-id="96136-119">删除订阅服务器上的推送订阅</span><span class="sxs-lookup"><span data-stu-id="96136-119">To delete a push subscription at the Subscriber</span></span>  
  
1.  <span data-ttu-id="96136-120">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中连接到订阅服务器，然后展开服务器节点。</span><span class="sxs-lookup"><span data-stu-id="96136-120">Connect to the Subscriber in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="96136-121">展开 **“复制”** 文件夹，再展开 **“本地订阅”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="96136-121">Expand the **Replication** folder, and then expand the **Local Subscriptions** folder.</span></span>  
  
3.  <span data-ttu-id="96136-122">右键单击要删除的订阅，再单击 **“删除”** 。</span><span class="sxs-lookup"><span data-stu-id="96136-122">Right-click the subscription you want to delete, and then click **Delete**.</span></span>  
  
4.  <span data-ttu-id="96136-123">在确认对话框中，选择是否连接到发布服务器以删除订阅信息。</span><span class="sxs-lookup"><span data-stu-id="96136-123">In the confirmation dialog box, select whether to connect to the Publisher to delete subscription information.</span></span> <span data-ttu-id="96136-124">如果清除 **“连接到发布服务器”** 复选框，则应在以后连接到发布服务器以删除订阅信息。</span><span class="sxs-lookup"><span data-stu-id="96136-124">If you clear the **Connect to Publisher** check box, you should connect to the Publisher later to delete the information.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="96136-125">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="96136-125">Using Transact-SQL</span></span>  
 <span data-ttu-id="96136-126">可以使用复制存储过程以编程方式删除推送订阅。</span><span class="sxs-lookup"><span data-stu-id="96136-126">Push subscriptions can be deleted programmatically using replication stored procedures.</span></span> <span data-ttu-id="96136-127">所用的存储过程取决于订阅所属的发布的类型。</span><span class="sxs-lookup"><span data-stu-id="96136-127">The stored procedures used depend on the type of publication to which the subscription belongs.</span></span>  
  
#### <a name="to-delete-a-push-subscription-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="96136-128">删除快照发布或事务发布的推送订阅</span><span class="sxs-lookup"><span data-stu-id="96136-128">To delete a push subscription to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="96136-129">在发布服务器上，对发布数据库执行 [sp_dropsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="96136-129">At the Publisher on the publication database, execute [sp_dropsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql).</span></span> <span data-ttu-id="96136-130">指定 **@publication** 和 **@subscriber** 。</span><span class="sxs-lookup"><span data-stu-id="96136-130">Specify **@publication** and **@subscriber**.</span></span> <span data-ttu-id="96136-131">将 **@article** 的值指定为 **@article**。</span><span class="sxs-lookup"><span data-stu-id="96136-131">Specify a value of **all** for **@article**.</span></span> <span data-ttu-id="96136-132">（可选）如果无法访问分发服务器，将 **@ignore_distributor** 的值指定为 **@ignore_distributor** ，以便在不删除分发服务器上相关对象的情况下删除订阅。</span><span class="sxs-lookup"><span data-stu-id="96136-132">(Optional) If the Distributor cannot be accessed, specify a value of **1** for **@ignore_distributor** to delete the subscription without removing related objects at the Distributor.</span></span>  
  
2.  <span data-ttu-id="96136-133">在订阅服务器上，对订阅数据库执行 [sp_subscription_cleanup &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-subscription-cleanup-transact-sql) 以删除订阅数据库中的复制元数据。</span><span class="sxs-lookup"><span data-stu-id="96136-133">At the Subscriber on the subscription database, execute [sp_subscription_cleanup &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-subscription-cleanup-transact-sql) to remove replication metadata in the subscription database.</span></span>  
  
#### <a name="to-delete-a-push-subscription-to-a-merge-publication"></a><span data-ttu-id="96136-134">删除合并发布的推送订阅</span><span class="sxs-lookup"><span data-stu-id="96136-134">To delete a push subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="96136-135">在发布服务器上，执行[&#40;transact-sql&#41;sp_dropmergesubscription ](/sql/relational-databases/system-stored-procedures/sp-dropmergesubscription-transact-sql)，同时指定 **@publication** **@subscriber** 和 **@subscriber_db** 。</span><span class="sxs-lookup"><span data-stu-id="96136-135">At the Publisher, execute [sp_dropmergesubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropmergesubscription-transact-sql), specifying **@publication**, **@subscriber** and **@subscriber_db**.</span></span> <span data-ttu-id="96136-136">（可选）如果无法访问分发服务器，将 **@ignore_distributor** 的值指定为 **@ignore_distributor** ，以便在不删除分发服务器上相关对象的情况下删除订阅。</span><span class="sxs-lookup"><span data-stu-id="96136-136">(Optional) If the Distributor cannot be accessed, specify a value of **1** for **@ignore_distributor** to delete the subscription without removing related objects at the Distributor.</span></span>  
  
2.  <span data-ttu-id="96136-137">在订阅服务器上，对订阅数据库执行 [sp_mergesubscription_cleanup &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-mergesubscription-cleanup-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="96136-137">At the Subscriber on the subscription database, execute [sp_mergesubscription_cleanup &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-mergesubscription-cleanup-transact-sql).</span></span> <span data-ttu-id="96136-138">指定 **@publisher** 、 **@publisher_db** 和 **@publication** 。</span><span class="sxs-lookup"><span data-stu-id="96136-138">Specify **@publisher**, **@publisher_db**, and **@publication**.</span></span> <span data-ttu-id="96136-139">这将会删除订阅数据库中的合并元数据。</span><span class="sxs-lookup"><span data-stu-id="96136-139">This removes merge metadata from the subscription database.</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="96136-140">示例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="96136-140">Examples (Transact-SQL)</span></span>  
 <span data-ttu-id="96136-141">该示例删除对事务发布的推送订阅。</span><span class="sxs-lookup"><span data-stu-id="96136-141">This example deletes a push subscription to a transactional publication.</span></span>  
  
 [!code-sql[HowTo#sp_droptransubscription](../../snippets/tsql/SQL15/replication/howto/tsql/droptranpullsub.sql#sp_droptransubscription)]  
  
 <span data-ttu-id="96136-142">该示例删除对合并发布的推送订阅。</span><span class="sxs-lookup"><span data-stu-id="96136-142">This example deletes a push subscription to a merge publication.</span></span>  
  
 [!code-sql[HowTo#sp_dropmergesubscription](../../snippets/tsql/SQL15/replication/howto/tsql/dropmergepullsub.sql#sp_dropmergesubscription)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="96136-143">使用复制管理对象 (RMO)</span><span class="sxs-lookup"><span data-stu-id="96136-143">Using Replication Management Objects (RMO)</span></span>  
 <span data-ttu-id="96136-144">用于删除推送订阅的 RMO 类取决于订阅推送订阅的发布的类型。</span><span class="sxs-lookup"><span data-stu-id="96136-144">The RMO classes that you use to delete a push subscription depend on the type of publication to which the push subscription is subscribed.</span></span>  
  
#### <a name="to-delete-a-push-subscription-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="96136-145">删除快照发布或事务发布的推送订阅</span><span class="sxs-lookup"><span data-stu-id="96136-145">To delete a push subscription to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="96136-146">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 类创建与订阅服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="96136-146">Create a connection to the Subscriber by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="96136-147">创建的 <xref:Microsoft.SqlServer.Replication.TransSubscription> 类的实例。</span><span class="sxs-lookup"><span data-stu-id="96136-147">Create an instance of the <xref:Microsoft.SqlServer.Replication.TransSubscription> class.</span></span>  
  
3.  <span data-ttu-id="96136-148">设置 <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>、 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>、 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>和 <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="96136-148">Set the <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>, and <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A> properties.</span></span>  
  
4.  <span data-ttu-id="96136-149">将 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 属性设置为步骤 1 中的 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 。</span><span class="sxs-lookup"><span data-stu-id="96136-149">Set the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> from step 1 for the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property.</span></span>  
  
5.  <span data-ttu-id="96136-150">检查 <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> 属性以确保该订阅存在。</span><span class="sxs-lookup"><span data-stu-id="96136-150">Check the <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> property to verify that the subscription exists.</span></span> <span data-ttu-id="96136-151">如果此属性的值为 `false`，则步骤 2 中所定义的订阅属性不正确或者该订阅不存在。</span><span class="sxs-lookup"><span data-stu-id="96136-151">If the value of this property is `false`, either the subscription properties in step 2 were defined incorrectly or the subscription does not exist.</span></span>  
  
6.  <span data-ttu-id="96136-152">调用 <xref:Microsoft.SqlServer.Replication.Subscription.Remove%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="96136-152">Call the <xref:Microsoft.SqlServer.Replication.Subscription.Remove%2A> method.</span></span>  
  
#### <a name="to-delete-a-push-subscription-to-a-merge-publication"></a><span data-ttu-id="96136-153">删除合并发布的推送订阅</span><span class="sxs-lookup"><span data-stu-id="96136-153">To delete a push subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="96136-154">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 类创建与订阅服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="96136-154">Create a connection to the Subscriber by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="96136-155">创建的 <xref:Microsoft.SqlServer.Replication.MergeSubscription> 类的实例。</span><span class="sxs-lookup"><span data-stu-id="96136-155">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergeSubscription> class.</span></span>  
  
3.  <span data-ttu-id="96136-156">设置 <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>、 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>、 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>和 <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="96136-156">Set the <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>, and <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A> properties.</span></span>  
  
4.  <span data-ttu-id="96136-157">将 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 属性设置为步骤 1 中的 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 。</span><span class="sxs-lookup"><span data-stu-id="96136-157">Set the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> from step 1 for the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property.</span></span>  
  
5.  <span data-ttu-id="96136-158">检查 <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> 属性以确保该订阅存在。</span><span class="sxs-lookup"><span data-stu-id="96136-158">Check the <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> property to verify that the subscription exists.</span></span> <span data-ttu-id="96136-159">如果此属性的值为 `false`，则步骤 2 中所定义的订阅属性不正确或者该订阅不存在。</span><span class="sxs-lookup"><span data-stu-id="96136-159">If the value of this property is `false`, either the subscription properties in step 2 were defined incorrectly or the subscription does not exist.</span></span>  
  
6.  <span data-ttu-id="96136-160">调用 <xref:Microsoft.SqlServer.Replication.Subscription.Remove%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="96136-160">Call the <xref:Microsoft.SqlServer.Replication.Subscription.Remove%2A> method.</span></span>  
  
###  <a name="examples-rmo"></a><a name="PShellExample"></a> <span data-ttu-id="96136-161">示例 (RMO)</span><span class="sxs-lookup"><span data-stu-id="96136-161">Examples (RMO)</span></span>  
 <span data-ttu-id="96136-162">可通过使用复制管理对象 (RMO) 以编程方式删除推送订阅。</span><span class="sxs-lookup"><span data-stu-id="96136-162">You can delete push subscriptions programmatically by using Replication Management Objects (RMO).</span></span>  
  
 [!code-csharp[HowTo#rmo_DropTranPushSub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_droptranpushsub)]  
  
 [!code-vb[HowTo#rmo_vb_DropTranPushSub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_droptranpushsub)]  
  
## <a name="see-also"></a><span data-ttu-id="96136-163">另请参阅</span><span class="sxs-lookup"><span data-stu-id="96136-163">See Also</span></span>  
 <span data-ttu-id="96136-164">[Subscribe to Publications](subscribe-to-publications.md) </span><span class="sxs-lookup"><span data-stu-id="96136-164">[Subscribe to Publications](subscribe-to-publications.md) </span></span>  
 [<span data-ttu-id="96136-165">复制安全最佳做法</span><span class="sxs-lookup"><span data-stu-id="96136-165">Replication Security Best Practices</span></span>](security/replication-security-best-practices.md)  
  
  
