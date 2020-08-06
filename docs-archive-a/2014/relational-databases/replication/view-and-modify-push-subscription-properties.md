---
title: 查看和修改推送订阅属性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- viewing replication properties
- push subscriptions [SQL Server replication], properties
- subscriptions [SQL Server replication], push
- push subscriptions [SQL Server replication], modifying
- modifying replication properties, push subscriptions
- modifying subscriptions, SQL Server Management Studio
ms.assetid: 801d2995-7aa5-4626-906e-c8190758ec71
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c1506d4f83fcfb94d62efd01c4d6447048fecfd6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692338"
---
# <a name="view-and-modify-push-subscription-properties"></a><span data-ttu-id="dafd8-102">查看和修改推送订阅属性</span><span class="sxs-lookup"><span data-stu-id="dafd8-102">View and Modify Push Subscription Properties</span></span>
  <span data-ttu-id="dafd8-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]或复制管理对象 (RMO) 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中查看和修改推送订阅属性。</span><span class="sxs-lookup"><span data-stu-id="dafd8-103">This topic describes how to view and modify push subscription properties in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or Replication Management Objects (RMO).</span></span>  
  
 <span data-ttu-id="dafd8-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="dafd8-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="dafd8-105">**查看和修改推送订阅属性，使用：**</span><span class="sxs-lookup"><span data-stu-id="dafd8-105">**To view and modify push subscription properties, using:**</span></span>  
  
     [<span data-ttu-id="dafd8-106">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="dafd8-106">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="dafd8-107">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="dafd8-107">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="dafd8-108">复制管理对象 (RMO)</span><span class="sxs-lookup"><span data-stu-id="dafd8-108">Replication Management Objects (RMO)</span></span>](#RMOProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="dafd8-109">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="dafd8-109">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="dafd8-110">可以从下列位置查看和修改发布服务器的推送订阅属性：</span><span class="sxs-lookup"><span data-stu-id="dafd8-110">View and modify push subscription properties from the Publisher in:</span></span>  
  
-   <span data-ttu-id="dafd8-111">“订阅属性 - \<Publisher>：\<PublicationDatabase>”对话框，可从 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中获取。</span><span class="sxs-lookup"><span data-stu-id="dafd8-111">The **Subscription Properties - \<Publisher>: \<PublicationDatabase>** dialog box, which is available from [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
-   <span data-ttu-id="dafd8-112">**“所有订阅”** 选项卡，该选项卡可以从复制监视器中找到。</span><span class="sxs-lookup"><span data-stu-id="dafd8-112">The **All Subscriptions** tab, which is available in Replication Monitor.</span></span> <span data-ttu-id="dafd8-113">有关启动复制监视器的信息，请参阅[启动复制监视器](monitor/start-the-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="dafd8-113">For information about starting Replication Monitor, see [Start the Replication Monitor](monitor/start-the-replication-monitor.md).</span></span>  
  
#### <a name="to-view-and-modify-push-subscription-properties-in-management-studio"></a><span data-ttu-id="dafd8-114">在 Management Studio 中查看和修改推送订阅属性</span><span class="sxs-lookup"><span data-stu-id="dafd8-114">To view and modify push subscription properties in Management Studio</span></span>  
  
1.  <span data-ttu-id="dafd8-115">在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中连接到发布服务器，然后展开服务器节点。</span><span class="sxs-lookup"><span data-stu-id="dafd8-115">Connect to the Publisher in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="dafd8-116">展开 **“复制”** 文件夹，再展开 **“本地发布”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="dafd8-116">Expand the **Replication** folder, and then expand the **Local Publications** folder.</span></span>  
  
3.  <span data-ttu-id="dafd8-117">展开相应的发布，右键单击订阅，然后单击 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="dafd8-117">Expand the appropriate publication, right-click a subscription, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="dafd8-118">根据需要修改属性，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="dafd8-118">Modify any properties if necessary, and then click **OK**.</span></span>  
  
#### <a name="to-view-and-modify-push-subscription-properties-in-replication-monitor"></a><span data-ttu-id="dafd8-119">在复制监视器中查看和修改推送订阅属性</span><span class="sxs-lookup"><span data-stu-id="dafd8-119">To view and modify push subscription properties in Replication Monitor</span></span>  
  
1.  <span data-ttu-id="dafd8-120">在复制监视器的左窗格中依次展开发布服务器组、发布服务器，然后单击某个发布。</span><span class="sxs-lookup"><span data-stu-id="dafd8-120">Expand a Publisher group in the left pane of Replication Monitor, expand a Publisher, and then click a publication.</span></span>  
  
2.  <span data-ttu-id="dafd8-121">单击 **“所有订阅”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="dafd8-121">Click the **All Subscriptions** tab.</span></span>  
  
3.  <span data-ttu-id="dafd8-122">右键单击订阅，然后单击 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="dafd8-122">Right-click a subscription, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="dafd8-123">根据需要修改属性，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="dafd8-123">Modify any properties if necessary, and then click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="dafd8-124">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="dafd8-124">Using Transact-SQL</span></span>  
 <span data-ttu-id="dafd8-125">可以使用复制存储过程以编程方式修改推送订阅和访问其属性。</span><span class="sxs-lookup"><span data-stu-id="dafd8-125">Push subscriptions can be modified and their properties accessed programmatically using replication stored procedures.</span></span> <span data-ttu-id="dafd8-126">所用的存储过程取决于订阅所属的发布的类型。</span><span class="sxs-lookup"><span data-stu-id="dafd8-126">The stored procedures used depend on the type of publication to which the subscription belongs.</span></span>  
  
#### <a name="to-view-the-properties-of-a-push-subscription-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="dafd8-127">查看快照或事务发布的推送订阅的属性</span><span class="sxs-lookup"><span data-stu-id="dafd8-127">To view the properties of a push subscription to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="dafd8-128">在发布服务器上，对发布数据库执行 [sp_helpsubscription](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="dafd8-128">At the Publisher on the publication database, execute [sp_helpsubscription](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql).</span></span> <span data-ttu-id="dafd8-129">**@publication**将、 **@subscriber** 和的值指定为**all** **@article** 。</span><span class="sxs-lookup"><span data-stu-id="dafd8-129">Specify **@publication**, **@subscriber**, and a value of **all** for **@article**.</span></span>  
  
2.  <span data-ttu-id="dafd8-130">在发布服务器上，对发布数据库执行 [sp_helpsubscriberinfo](/sql/relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql)，同时指定 **@subscriber**中获取。</span><span class="sxs-lookup"><span data-stu-id="dafd8-130">At the Publisher on the publication database, execute [sp_helpsubscriberinfo](/sql/relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql), specifying **@subscriber**.</span></span>  
  
#### <a name="to-change-the-properties-of-a-push-subscription-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="dafd8-131">更改快照或事务发布的推送订阅的属性</span><span class="sxs-lookup"><span data-stu-id="dafd8-131">To change the properties of a push subscription to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="dafd8-132">在发布服务器上，对发布数据库执行 [sp_changesubscriber](/sql/relational-databases/system-stored-procedures/sp-changesubscriber-transact-sql)，同时指定 **@subscriber** 及任何参数。</span><span class="sxs-lookup"><span data-stu-id="dafd8-132">At the Publisher on the publication database, execute [sp_changesubscriber](/sql/relational-databases/system-stored-procedures/sp-changesubscriber-transact-sql), specifying **@subscriber** and any parameters for the Subscriber properties being changed.</span></span>  
  
2.  <span data-ttu-id="dafd8-133">在发布服务器上，对发布数据库执行 [sp_changesubscription](/sql/relational-databases/system-stored-procedures/sp-changesubscription-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="dafd8-133">At the Publisher on the publication database, execute [sp_changesubscription](/sql/relational-databases/system-stored-procedures/sp-changesubscription-transact-sql).</span></span> <span data-ttu-id="dafd8-134">将、、、的值指定为， **@publication** **@subscriber** **@destination_db** **all** **@article** 将订阅属性更改为 **@property** ，并将新值指定为 **@value** 。</span><span class="sxs-lookup"><span data-stu-id="dafd8-134">Specify **@publication**, **@subscriber**, **@destination_db**, a value of **all** for **@article**, the subscription property being changed as **@property**, and the new value as **@value**.</span></span> <span data-ttu-id="dafd8-135">这将更改推送订阅的安全设置。</span><span class="sxs-lookup"><span data-stu-id="dafd8-135">This changes security settings for the push subscription.</span></span>  
  
3.  <span data-ttu-id="dafd8-136">（可选）若要更改订阅的 Data Transformation Services (DTS) 包属性，请在订阅服务器上，对订阅数据库执行 [sp_changesubscriptiondtsinfo](/sql/relational-databases/system-stored-procedures/sp-changesubscriptiondtsinfo-transact-sql) 。</span><span class="sxs-lookup"><span data-stu-id="dafd8-136">(Optional) To change the Data Transformation Services (DTS) package properties of a subscription, execute [sp_changesubscriptiondtsinfo](/sql/relational-databases/system-stored-procedures/sp-changesubscriptiondtsinfo-transact-sql) at the Subscriber on the subscription database.</span></span> <span data-ttu-id="dafd8-137">为指定分发代理作业的 ID **@jobid** ，并指定以下 DTS 包属性：</span><span class="sxs-lookup"><span data-stu-id="dafd8-137">Specify the ID of the Distribution Agent job for **@jobid** and the following DTS package properties:</span></span>  
  
    -   **@dts_package_name**  
  
    -   **@dts_package_password**  
  
    -   **@dts_package_location**  
  
     <span data-ttu-id="dafd8-138">此操作将更改订阅的 DTS 包属性。</span><span class="sxs-lookup"><span data-stu-id="dafd8-138">This changes the DTS package properties of a subscription.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="dafd8-139">可以通过执行 [sp_helpsubscription](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql)来获得作业 ID。</span><span class="sxs-lookup"><span data-stu-id="dafd8-139">The job ID can be obtained by executing [sp_helpsubscription](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql).</span></span>  
  
#### <a name="to-view-the-properties-of-a-push-subscription-to-a-merge-publication"></a><span data-ttu-id="dafd8-140">查看合并发布的推送订阅的属性</span><span class="sxs-lookup"><span data-stu-id="dafd8-140">To view the properties of a push subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="dafd8-141">在发布服务器上，对发布数据库执行 [sp_helpmergesubscription](/sql/relational-databases/system-stored-procedures/sp-helpmergesubscription-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="dafd8-141">At the Publisher on the publication database, execute [sp_helpmergesubscription](/sql/relational-databases/system-stored-procedures/sp-helpmergesubscription-transact-sql).</span></span> <span data-ttu-id="dafd8-142">指定 **@publication** 和 **@subscriber** 。</span><span class="sxs-lookup"><span data-stu-id="dafd8-142">Specify **@publication** and **@subscriber**.</span></span>  
  
2.  <span data-ttu-id="dafd8-143">在发布服务器上，执行[sp_helpsubscriberinfo](/sql/relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql)，并指定 **@subscriber** 。</span><span class="sxs-lookup"><span data-stu-id="dafd8-143">At the Publisher, execute [sp_helpsubscriberinfo](/sql/relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql), specifying **@subscriber**.</span></span>  
  
#### <a name="to-change-the-properties-of-a-push-subscription-to-a-merge-publication"></a><span data-ttu-id="dafd8-144">更改合并发布的推送订阅的属性</span><span class="sxs-lookup"><span data-stu-id="dafd8-144">To change the properties of a push subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="dafd8-145">在发布服务器上，对发布数据库执行 [sp_changemergesubscription](/sql/relational-databases/system-stored-procedures/sp-changemergesubscription-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="dafd8-145">At the Publisher on the publication database, execute [sp_changemergesubscription](/sql/relational-databases/system-stored-procedures/sp-changemergesubscription-transact-sql).</span></span> <span data-ttu-id="dafd8-146">指定 **@publication** 、 **@subscriber** 、 **@subscriber_db** 、要更改为的订阅属性 **@property** ，并将新值指定为 **@value** 。</span><span class="sxs-lookup"><span data-stu-id="dafd8-146">Specify **@publication**, **@subscriber**, **@subscriber_db**, the subscription property being changed as **@property**, and the new value as **@value**.</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="dafd8-147">示例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="dafd8-147">Example (Transact-SQL)</span></span>  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="dafd8-148">使用复制管理对象 (RMO)</span><span class="sxs-lookup"><span data-stu-id="dafd8-148">Using Replication Management Objects (RMO)</span></span>  
 <span data-ttu-id="dafd8-149">用于查看或修改推送订阅属性的 RMO 类取决于订阅推送订阅的发布的类型。</span><span class="sxs-lookup"><span data-stu-id="dafd8-149">The RMO classes you use to view or modify push subscription properties depend on the type of publication to which the push subscription is subscribed.</span></span>  
  
#### <a name="to-view-or-modify-properties-of-a-push-subscription-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="dafd8-150">查看或修改快照发布或事务发布的推送订阅的属性</span><span class="sxs-lookup"><span data-stu-id="dafd8-150">To view or modify properties of a push subscription to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="dafd8-151">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 类创建与发布服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="dafd8-151">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="dafd8-152">创建的 <xref:Microsoft.SqlServer.Replication.TransSubscription> 类的实例。</span><span class="sxs-lookup"><span data-stu-id="dafd8-152">Create an instance of the <xref:Microsoft.SqlServer.Replication.TransSubscription> class.</span></span>  
  
3.  <span data-ttu-id="dafd8-153">设置 <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>、 <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>、 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>和 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="dafd8-153">Set the <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>, and <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A> properties.</span></span>  
  
4.  <span data-ttu-id="dafd8-154">将 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 属性设置为步骤 1 中的 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 。</span><span class="sxs-lookup"><span data-stu-id="dafd8-154">Set the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> from step 1 for the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property setting.</span></span>  
  
5.  <span data-ttu-id="dafd8-155">调用 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法获取该对象的属性。</span><span class="sxs-lookup"><span data-stu-id="dafd8-155">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span> <span data-ttu-id="dafd8-156">如果此方法返回 `false`，则说明步骤 3 中的订阅属性没有正确定义或该订阅不存在。</span><span class="sxs-lookup"><span data-stu-id="dafd8-156">If this method returns `false`, either the subscription properties in step 3 were defined incorrectly or the subscription does not exist.</span></span>  
  
6.  <span data-ttu-id="dafd8-157">（可选）若要更改属性，请为可以设置的 <xref:Microsoft.SqlServer.Replication.TransSubscription> 属性中的一个设置新值，然后再调用 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="dafd8-157">(Optional) To change properties, set a new value for one of the <xref:Microsoft.SqlServer.Replication.TransSubscription> properties that can be set, and then call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> method.</span></span>  
  
7.  <span data-ttu-id="dafd8-158">（可选）若要查看新设置，请调用 <xref:Microsoft.SqlServer.Replication.ReplicationObject.Refresh%2A> 方法重新加载此订阅的属性。</span><span class="sxs-lookup"><span data-stu-id="dafd8-158">(Optional) To view the new settings, call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.Refresh%2A> method to reload the properties for the subscription.</span></span>  
  
#### <a name="to-view-or-modify-properties-of-a-push-subscription-to-a-merge-publication"></a><span data-ttu-id="dafd8-159">查看或修改合并发布的推送订阅的属性</span><span class="sxs-lookup"><span data-stu-id="dafd8-159">To view or modify properties of a push subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="dafd8-160">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 类创建与订阅服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="dafd8-160">Create a connection to the Subscriber by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="dafd8-161">创建的 <xref:Microsoft.SqlServer.Replication.MergeSubscription> 类的实例。</span><span class="sxs-lookup"><span data-stu-id="dafd8-161">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergeSubscription> class.</span></span>  
  
3.  <span data-ttu-id="dafd8-162">设置 <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>、 <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>、 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>和 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="dafd8-162">Set the <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>, and <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A> properties.</span></span>  
  
4.  <span data-ttu-id="dafd8-163">将 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 属性设置为步骤 1 中的 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 。</span><span class="sxs-lookup"><span data-stu-id="dafd8-163">Set the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> from step 1 for the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property setting.</span></span>  
  
5.  <span data-ttu-id="dafd8-164">调用 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法获取该对象的属性。</span><span class="sxs-lookup"><span data-stu-id="dafd8-164">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span> <span data-ttu-id="dafd8-165">如果此方法返回 `false`，则说明步骤 3 中的订阅属性没有正确定义或该订阅不存在。</span><span class="sxs-lookup"><span data-stu-id="dafd8-165">If this method returns `false`, either the subscription properties in step 3 were defined incorrectly or the subscription does not exist.</span></span>  
  
6.  <span data-ttu-id="dafd8-166">（可选）若要更改属性，请为可以设置的 <xref:Microsoft.SqlServer.Replication.MergeSubscription> 属性中的一个设置新值，然后再调用 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="dafd8-166">(Optional) To change properties, set a new value for one of the <xref:Microsoft.SqlServer.Replication.MergeSubscription> properties that can be set, and then call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> method.</span></span>  
  
7.  <span data-ttu-id="dafd8-167">（可选）若要查看新设置，请调用 <xref:Microsoft.SqlServer.Replication.ReplicationObject.Refresh%2A> 方法重新加载此订阅的属性。</span><span class="sxs-lookup"><span data-stu-id="dafd8-167">(Optional) To view the new settings, call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.Refresh%2A> method to reload the properties for the subscription.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dafd8-168">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dafd8-168">See Also</span></span>  
 <span data-ttu-id="dafd8-169">[使用复制监视器查看信息和执行任务](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="dafd8-169">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 <span data-ttu-id="dafd8-170">[Replication Security Best Practices](security/replication-security-best-practices.md) </span><span class="sxs-lookup"><span data-stu-id="dafd8-170">[Replication Security Best Practices](security/replication-security-best-practices.md) </span></span>  
 [<span data-ttu-id="dafd8-171">订阅发布</span><span class="sxs-lookup"><span data-stu-id="dafd8-171">Subscribe to Publications</span></span>](subscribe-to-publications.md)  
  
  
