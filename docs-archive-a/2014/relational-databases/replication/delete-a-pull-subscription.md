---
title: 删除请求订阅 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- removing subscriptions
- deleting subscriptions
- pull subscriptions [SQL Server replication], deleting
- subscriptions [SQL Server replication], pull
ms.assetid: 997c0b8e-d8d9-4eed-85b1-6baa1f8594ce
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f869e26075bb837b2110e9db3ac5ac7220659525
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578128"
---
# <a name="delete-a-pull-subscription"></a><span data-ttu-id="ffded-102">删除请求订阅</span><span class="sxs-lookup"><span data-stu-id="ffded-102">Delete a Pull Subscription</span></span>
  <span data-ttu-id="ffded-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]或复制管理对象 (RMO) 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中删除请求订阅。</span><span class="sxs-lookup"><span data-stu-id="ffded-103">This topic describes how to delete a pull subscription in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or Replication Management Objects (RMO).</span></span>  
  
 <span data-ttu-id="ffded-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="ffded-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="ffded-105">**删除请求订阅，使用：**</span><span class="sxs-lookup"><span data-stu-id="ffded-105">**To delete a pull subscription, using:**</span></span>  
  
     [<span data-ttu-id="ffded-106">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ffded-106">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="ffded-107">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ffded-107">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="ffded-108">复制管理对象 (RMO)</span><span class="sxs-lookup"><span data-stu-id="ffded-108">Replication Management Objects (RMO)</span></span>](#RMOProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="ffded-109">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ffded-109">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="ffded-110">在发布服务器上删除请求订阅（从 **的** “本地发布” [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]文件夹中），或在订阅服务器上删除请求订阅（从 **“本地订阅”** 文件夹中）。</span><span class="sxs-lookup"><span data-stu-id="ffded-110">Delete a pull subscription at the Publisher (from the **Local Publications** folder in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]) or the Subscriber (from the **Local Subscriptions** folder).</span></span> <span data-ttu-id="ffded-111">删除订阅不会从订阅中删除对象或数据，必须对其手动删除。</span><span class="sxs-lookup"><span data-stu-id="ffded-111">Deleting a subscription does not remove objects or data from the subscription; they must be removed manually.</span></span>  
  
#### <a name="to-delete-a-pull-subscription-at-the-publisher"></a><span data-ttu-id="ffded-112">在发布服务器上删除请求订阅</span><span class="sxs-lookup"><span data-stu-id="ffded-112">To delete a pull subscription at the Publisher</span></span>  
  
1.  <span data-ttu-id="ffded-113">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中连接到发布服务器，然后展开服务器节点。</span><span class="sxs-lookup"><span data-stu-id="ffded-113">Connect to the Publisher in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="ffded-114">展开 **“复制”** 文件夹，再展开 **“本地发布”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="ffded-114">Expand the **Replication** folder, and then expand the **Local Publications** folder.</span></span>  
  
3.  <span data-ttu-id="ffded-115">展开与要删除的订阅关联的发布。</span><span class="sxs-lookup"><span data-stu-id="ffded-115">Expand the publication associated with the subscription you want to delete.</span></span>  
  
4.  <span data-ttu-id="ffded-116">右键单击该订阅，再单击 **“删除”** 。</span><span class="sxs-lookup"><span data-stu-id="ffded-116">Right-click the subscription, and then click **Delete**.</span></span>  
  
5.  <span data-ttu-id="ffded-117">在确认对话框中，选择是否连接到订阅服务器以删除订阅信息。</span><span class="sxs-lookup"><span data-stu-id="ffded-117">In the confirmation dialog box, select whether to connect to the Subscriber to delete subscription information.</span></span> <span data-ttu-id="ffded-118">如果清除 **“连接到订阅服务器”** 复选框，则应在以后连接到订阅服务器以删除订阅信息。</span><span class="sxs-lookup"><span data-stu-id="ffded-118">If you clear the **Connect to Subscriber** check box, you should connect to the Subscriber later to delete the information.</span></span>  
  
#### <a name="to-delete-a-pull-subscription-at-the-subscriber"></a><span data-ttu-id="ffded-119">在订阅服务器上删除请求订阅</span><span class="sxs-lookup"><span data-stu-id="ffded-119">To delete a pull subscription at the Subscriber</span></span>  
  
1.  <span data-ttu-id="ffded-120">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中连接到订阅服务器，然后展开服务器节点。</span><span class="sxs-lookup"><span data-stu-id="ffded-120">Connect to the Subscriber in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="ffded-121">展开 **“复制”** 文件夹，再展开 **“本地订阅”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="ffded-121">Expand the **Replication** folder, and then expand the **Local Subscriptions** folder.</span></span>  
  
3.  <span data-ttu-id="ffded-122">右键单击要删除的订阅，再单击 **“删除”** 。</span><span class="sxs-lookup"><span data-stu-id="ffded-122">Right-click the subscription you want to delete, and then click **Delete**.</span></span>  
  
4.  <span data-ttu-id="ffded-123">在确认对话框中，选择是否连接到发布服务器以删除订阅信息。</span><span class="sxs-lookup"><span data-stu-id="ffded-123">In the confirmation dialog box, select whether to connect to the Publisher to delete subscription information.</span></span> <span data-ttu-id="ffded-124">如果清除 **“连接到发布服务器”** 复选框，则应在以后连接到发布服务器以删除订阅信息。</span><span class="sxs-lookup"><span data-stu-id="ffded-124">If you clear the **Connect to Publisher** check box, you should connect to the Publisher later to delete the information.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="ffded-125">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ffded-125">Using Transact-SQL</span></span>  
 <span data-ttu-id="ffded-126">可以使用复制存储过程以编程方式删除请求订阅。</span><span class="sxs-lookup"><span data-stu-id="ffded-126">Pull subscriptions can be deleted programmatically using replication stored procedures.</span></span> <span data-ttu-id="ffded-127">所用的存储过程取决于订阅所属的发布的类型。</span><span class="sxs-lookup"><span data-stu-id="ffded-127">The stored procedures used will depend on the type of publication to which the subscription belongs.</span></span>  
  
#### <a name="to-delete-a-pull-subscription-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="ffded-128">删除对快照发布或事务发布的请求订阅</span><span class="sxs-lookup"><span data-stu-id="ffded-128">To delete a pull subscription to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="ffded-129">在订阅服务器上，对订阅数据库执行 [sp_droppullsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-droppullsubscription-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="ffded-129">At the Subscriber on the subscription database, execute [sp_droppullsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-droppullsubscription-transact-sql).</span></span> <span data-ttu-id="ffded-130">指定 **@publication** 、 **@publisher** 和 **@publisher_db** 。</span><span class="sxs-lookup"><span data-stu-id="ffded-130">Specify **@publication**, **@publisher**, and **@publisher_db**.</span></span>  
  
2.  <span data-ttu-id="ffded-131">在发布服务器上，对发布数据库执行 [sp_dropsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="ffded-131">At the Publisher on the publication database, execute [sp_dropsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql).</span></span> <span data-ttu-id="ffded-132">指定 **@publication** 和 **@subscriber** 。</span><span class="sxs-lookup"><span data-stu-id="ffded-132">Specify **@publication** and **@subscriber**.</span></span> <span data-ttu-id="ffded-133">将 **@article** 的值指定为 **@article**。</span><span class="sxs-lookup"><span data-stu-id="ffded-133">Specify a value of **all** for **@article**.</span></span> <span data-ttu-id="ffded-134">（可选）如果无法访问分发服务器，将 **@ignore_distributor** 的值指定为 **@ignore_distributor** ，以便在不删除分发服务器上相关对象的情况下删除订阅。</span><span class="sxs-lookup"><span data-stu-id="ffded-134">(Optional) If the Distributor cannot be accessed, specify a value of **1** for **@ignore_distributor** to delete the subscription without removing related objects at the Distributor.</span></span>  
  
#### <a name="to-delete-a-pull-subscription-to-a-merge-publication"></a><span data-ttu-id="ffded-135">删除对合并发布的请求订阅</span><span class="sxs-lookup"><span data-stu-id="ffded-135">To delete a pull subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="ffded-136">在订阅服务器上，对订阅数据库执行 [sp_dropmergepullsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropmergepullsubscription-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="ffded-136">At the Subscriber on the subscription database, execute [sp_dropmergepullsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropmergepullsubscription-transact-sql).</span></span> <span data-ttu-id="ffded-137">指定 **@publication** 、 **@publisher** 和 **@publisher_db** 。</span><span class="sxs-lookup"><span data-stu-id="ffded-137">Specify **@publication**, **@publisher**, and **@publisher_db**.</span></span>  
  
2.  <span data-ttu-id="ffded-138">在发布服务器上，对发布数据库执行 [sp_dropmergesubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropmergesubscription-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="ffded-138">At the Publisher on the publication database, execute [sp_dropmergesubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropmergesubscription-transact-sql).</span></span> <span data-ttu-id="ffded-139">指定 **@publication** 、 **@subscriber** 和 **@subscriber_db** 。</span><span class="sxs-lookup"><span data-stu-id="ffded-139">Specify **@publication**, **@subscriber**, and **@subscriber_db**.</span></span> <span data-ttu-id="ffded-140">将 **@subscription_type** 指定为 **@subscription_type**。</span><span class="sxs-lookup"><span data-stu-id="ffded-140">Specify a value of **pull** for **@subscription_type**.</span></span> <span data-ttu-id="ffded-141">（可选）如果无法访问分发服务器，将 **@ignore_distributor** 的值指定为 **@ignore_distributor** ，以便在不删除分发服务器上相关对象的情况下删除订阅。</span><span class="sxs-lookup"><span data-stu-id="ffded-141">(Optional) If the Distributor cannot be accessed, specify a value of **1** for **@ignore_distributor** to delete the subscription without removing related objects at the Distributor.</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="ffded-142">示例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="ffded-142">Examples (Transact-SQL)</span></span>  
 <span data-ttu-id="ffded-143">以下示例删除对事务发布的请求订阅。</span><span class="sxs-lookup"><span data-stu-id="ffded-143">The following example deletes a pull subscription to a transactional publication.</span></span> <span data-ttu-id="ffded-144">第一个批处理在订阅服务器上执行，第二个批处理在发布服务器上执行。</span><span class="sxs-lookup"><span data-stu-id="ffded-144">The first batch is executed at the Subscriber and the second is executed at the Publisher.</span></span>  
  
 [!code-sql[HowTo#sp_droptranpullsubscription](../../snippets/tsql/SQL15/replication/howto/tsql/droptranpullsub.sql#sp_droptranpullsubscription)]  
  
 [!code-sql[HowTo#sp_droptransubscription](../../snippets/tsql/SQL15/replication/howto/tsql/droptranpullsub.sql#sp_droptransubscription)]  
  
 <span data-ttu-id="ffded-145">以下示例删除对合并发布的请求订阅。</span><span class="sxs-lookup"><span data-stu-id="ffded-145">The following example deletes a pull subscription to a merge publication.</span></span> <span data-ttu-id="ffded-146">第一个批处理在订阅服务器上执行，第二个批处理在发布服务器上执行。</span><span class="sxs-lookup"><span data-stu-id="ffded-146">The first batch is executed at the Subscriber and the second is executed at the Publisher.</span></span>  
  
 [!code-sql[HowTo#sp_dropmergepullsubscription](../../snippets/tsql/SQL15/replication/howto/tsql/dropmergepullsub.sql#sp_dropmergepullsubscription)]  
  
 [!code-sql[HowTo#sp_dropmergesubscription](../../snippets/tsql/SQL15/replication/howto/tsql/dropmergepullsub.sql#sp_dropmergesubscription)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="ffded-147">使用复制管理对象 (RMO)</span><span class="sxs-lookup"><span data-stu-id="ffded-147">Using Replication Management Objects (RMO)</span></span>  
 <span data-ttu-id="ffded-148">可通过使用复制管理对象 (RMO) 以编程方式删除请求订阅。</span><span class="sxs-lookup"><span data-stu-id="ffded-148">You can delete pull subscriptions programmatically by using Replication Management Objects (RMO).</span></span> <span data-ttu-id="ffded-149">用于删除请求订阅的 RMO 类由该请求订阅所订阅的发布类型决定。</span><span class="sxs-lookup"><span data-stu-id="ffded-149">The RMO classes that you use to delete a pull subscription depend on the type of publication to which the pull subscription is subscribed.</span></span>  
  
#### <a name="to-delete-a-pull-subscription-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="ffded-150">删除对快照发布或事务发布的请求订阅</span><span class="sxs-lookup"><span data-stu-id="ffded-150">To delete a pull subscription to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="ffded-151">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 类创建与订阅服务器和发布服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="ffded-151">Create connections to both the Subscriber and Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> Class.</span></span>  
  
2.  <span data-ttu-id="ffded-152">创建 <xref:Microsoft.SqlServer.Replication.TransPullSubscription> 类的一个实例，并设置 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>、 <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>、 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>以及 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="ffded-152">Create an instance of the <xref:Microsoft.SqlServer.Replication.TransPullSubscription> class, and set the <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>, and <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A> properties.</span></span> <span data-ttu-id="ffded-153">使用步骤 1 中的订阅服务器连接来设置 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="ffded-153">Use the Subscriber connection from step 1 to set the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property.</span></span>  
  
3.  <span data-ttu-id="ffded-154">检查 <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> 属性以确保该订阅存在。</span><span class="sxs-lookup"><span data-stu-id="ffded-154">Check the <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> property to verify that the subscription exists.</span></span> <span data-ttu-id="ffded-155">如果此属性的值为 `false`，则步骤 2 中所定义的订阅属性不正确或者该订阅不存在。</span><span class="sxs-lookup"><span data-stu-id="ffded-155">If the value of this property is `false`, either the subscription properties in step 2 were defined incorrectly or the subscription does not exist.</span></span>  
  
4.  <span data-ttu-id="ffded-156">调用 <xref:Microsoft.SqlServer.Replication.PullSubscription.Remove%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="ffded-156">Call the <xref:Microsoft.SqlServer.Replication.PullSubscription.Remove%2A> method.</span></span>  
  
5.  <span data-ttu-id="ffded-157">使用步骤 1 中的发布服务器连接，创建 <xref:Microsoft.SqlServer.Replication.TransPublication> 类的实例。</span><span class="sxs-lookup"><span data-stu-id="ffded-157">Create an instance of the <xref:Microsoft.SqlServer.Replication.TransPublication> class by using the Publisher connection from step 1.</span></span> <span data-ttu-id="ffded-158">指定 <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>、 <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> 和 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>。</span><span class="sxs-lookup"><span data-stu-id="ffded-158">Specify <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>, <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> and <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.</span></span>  
  
6.  <span data-ttu-id="ffded-159">调用 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="ffded-159">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method.</span></span> <span data-ttu-id="ffded-160">如果该方法返回 `false`，则表示步骤 5 中指定的属性不正确，或者服务器中不存在发布。</span><span class="sxs-lookup"><span data-stu-id="ffded-160">If this method returns `false`, either the properties specified in step 5 are incorrect or the publication does not exist on the server.</span></span>  
  
7.  <span data-ttu-id="ffded-161">调用 <xref:Microsoft.SqlServer.Replication.TransPublication.RemovePullSubscription%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="ffded-161">Call the <xref:Microsoft.SqlServer.Replication.TransPublication.RemovePullSubscription%2A> method.</span></span> <span data-ttu-id="ffded-162">将订阅服务器和订阅数据库的名称分别指定给 *subscriber* 和 *subscriberDB* 参数。</span><span class="sxs-lookup"><span data-stu-id="ffded-162">Specify the name of the Subscriber and the subscription database for the *subscriber* and *subscriberDB* parameters.</span></span>  
  
#### <a name="to-delete-a-pull-subscription-to-a-merge-publication"></a><span data-ttu-id="ffded-163">删除对合并发布的请求订阅</span><span class="sxs-lookup"><span data-stu-id="ffded-163">To delete a pull subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="ffded-164">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 类创建与订阅服务器和发布服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="ffded-164">Create connections to both the Subscriber and Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> Class.</span></span>  
  
2.  <span data-ttu-id="ffded-165">创建 <xref:Microsoft.SqlServer.Replication.MergePullSubscription> 类的一个实例，并设置 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>、 <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>、 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>以及 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="ffded-165">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergePullSubscription> class, and set the <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>, and <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A> properties.</span></span> <span data-ttu-id="ffded-166">使用步骤 1 中的连接来设置 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="ffded-166">Use the connection from step 1 to set the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property.</span></span>  
  
3.  <span data-ttu-id="ffded-167">检查 <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> 属性以确保该订阅存在。</span><span class="sxs-lookup"><span data-stu-id="ffded-167">Check the <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> property to verify that the subscription exists.</span></span> <span data-ttu-id="ffded-168">如果此属性的值为 `false`，则步骤 2 中所定义的订阅属性不正确或者该订阅不存在。</span><span class="sxs-lookup"><span data-stu-id="ffded-168">If the value of this property is `false`, either the subscription properties in step 2 were defined incorrectly or the subscription does not exist.</span></span>  
  
4.  <span data-ttu-id="ffded-169">调用 <xref:Microsoft.SqlServer.Replication.PullSubscription.Remove%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="ffded-169">Call the <xref:Microsoft.SqlServer.Replication.PullSubscription.Remove%2A> method.</span></span>  
  
5.  <span data-ttu-id="ffded-170">使用步骤 1 中的发布服务器连接，创建 <xref:Microsoft.SqlServer.Replication.MergePublication> 类的实例。</span><span class="sxs-lookup"><span data-stu-id="ffded-170">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergePublication> class by using the Publisher connection from step 1.</span></span> <span data-ttu-id="ffded-171">指定 <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>、 <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> 和 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>。</span><span class="sxs-lookup"><span data-stu-id="ffded-171">Specify <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>, <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> and <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.</span></span>  
  
6.  <span data-ttu-id="ffded-172">调用 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="ffded-172">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method.</span></span> <span data-ttu-id="ffded-173">如果该方法返回 `false`，则表示步骤 5 中指定的属性不正确，或者服务器中不存在发布。</span><span class="sxs-lookup"><span data-stu-id="ffded-173">If this method returns `false`, either the properties specified in step 5 are incorrect or the publication does not exist on the server.</span></span>  
  
7.  <span data-ttu-id="ffded-174">调用 <xref:Microsoft.SqlServer.Replication.MergePublication.RemovePullSubscription%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="ffded-174">Call the <xref:Microsoft.SqlServer.Replication.MergePublication.RemovePullSubscription%2A> method.</span></span> <span data-ttu-id="ffded-175">将订阅服务器和订阅数据库的名称分别指定给 *subscriber* 和 *subscriberDB* 参数。</span><span class="sxs-lookup"><span data-stu-id="ffded-175">Specify the name of the Subscriber and the subscription database for the *subscriber* and *subscriberDB* parameters.</span></span>  
  
###  <a name="examples-rmo"></a><a name="PShellExample"></a> <span data-ttu-id="ffded-176">示例 (RMO)</span><span class="sxs-lookup"><span data-stu-id="ffded-176">Examples (RMO)</span></span>  
 <span data-ttu-id="ffded-177">本示例将删除对事务发布的请求订阅并删除发布服务器上的订阅注册。</span><span class="sxs-lookup"><span data-stu-id="ffded-177">This example deletes a pull subscription to a transactional publication and removes the subscription registration at the Publisher.</span></span>  
  
 [!code-csharp[HowTo#rmo_DropTranPullSub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_droptranpullsub)]  
  
 [!code-vb[HowTo#rmo_vb_DropTranPullSub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_droptranpullsub)]  
  
 <span data-ttu-id="ffded-178">本示例将删除对合并发布的请求订阅并删除发布服务器上的订阅注册。</span><span class="sxs-lookup"><span data-stu-id="ffded-178">This example deletes a pull subscription to a merge publication and removes the subscription registration at the Publisher.</span></span>  
  
 [!code-csharp[HowTo#rmo_DropMergePullSub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_dropmergepullsub)]  
  
 [!code-vb[HowTo#rmo_vb_DropMergePullSub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_dropmergepullsub)]  
  
## <a name="see-also"></a><span data-ttu-id="ffded-179">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ffded-179">See Also</span></span>  
 <span data-ttu-id="ffded-180">[Subscribe to Publications](subscribe-to-publications.md) </span><span class="sxs-lookup"><span data-stu-id="ffded-180">[Subscribe to Publications](subscribe-to-publications.md) </span></span>  
 [<span data-ttu-id="ffded-181">复制安全最佳做法</span><span class="sxs-lookup"><span data-stu-id="ffded-181">Replication Security Best Practices</span></span>](security/replication-security-best-practices.md)  
  
  
