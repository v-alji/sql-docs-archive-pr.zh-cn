---
title: 查看和修改请求订阅属性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- modifying subscriptions
- viewing replication properties
- modifying replication properties, pull subscriptions
- pull subscriptions [SQL Server replication], modifying
- subscriptions [SQL Server replication], pull
- pull subscriptions [SQL Server replication], properties
- modifying subscriptions, SQL Server Management Studio
ms.assetid: 1601e54f-86f0-49e8-b023-87a5d1def033
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1b847a22d31bbf3ea7540c55339fe27531134125
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577498"
---
# <a name="view-and-modify-pull-subscription-properties"></a><span data-ttu-id="0ef02-102">查看和修改请求订阅属性</span><span class="sxs-lookup"><span data-stu-id="0ef02-102">View and Modify Pull Subscription Properties</span></span>
  <span data-ttu-id="0ef02-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]或复制管理对象 (RMO) 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中查看和修改请求订阅属性。</span><span class="sxs-lookup"><span data-stu-id="0ef02-103">This topic describes how to view and modify pull subscription properties in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or Replication Management Objects (RMO).</span></span>  
  
 <span data-ttu-id="0ef02-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="0ef02-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="0ef02-105">**查看和修改请求订阅属性，使用：**</span><span class="sxs-lookup"><span data-stu-id="0ef02-105">**To view and modify pull subscription properties, using:**</span></span>  
  
     [<span data-ttu-id="0ef02-106">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0ef02-106">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="0ef02-107">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="0ef02-107">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="0ef02-108">复制管理对象 (RMO)</span><span class="sxs-lookup"><span data-stu-id="0ef02-108">Replication Management Objects (RMO)</span></span>](#RMOProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="0ef02-109">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0ef02-109">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="0ef02-110">在“订阅属性 - \<Publisher>: \<PublicationDatabase>”对话框中，查看发布服务器或订阅服务器的请求订阅属性，可通过 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 访问此对话框。</span><span class="sxs-lookup"><span data-stu-id="0ef02-110">View pull subscription properties from the Publisher or the Subscriber in the **Subscription Properties - \<Publisher>: \<PublicationDatabase>** dialog box, which is available from [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="0ef02-111">可以从订阅服务器中查看更多属性，并且可以在订阅服务器上修改属性。</span><span class="sxs-lookup"><span data-stu-id="0ef02-111">More properties are visible from the Subscriber, and properties can be modified at the Subscriber.</span></span> <span data-ttu-id="0ef02-112">也可以从发布服务器的 **“所有订阅”** 选项卡上查看属性信息，此选项卡可以通过复制监视器访问。</span><span class="sxs-lookup"><span data-stu-id="0ef02-112">You can also view properties from the Publisher on the **All Subscriptions** tab, which is available in Replication Monitor.</span></span> <span data-ttu-id="0ef02-113">有关启动复制监视器的信息，请参阅[启动复制监视器](monitor/start-the-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="0ef02-113">For information about starting Replication Monitor, see [Start the Replication Monitor](monitor/start-the-replication-monitor.md).</span></span>  
  
#### <a name="to-view-pull-subscription-properties-from-the-publisher-in-management-studio"></a><span data-ttu-id="0ef02-114">从 Management Studio 中的发布服务器查看请求订阅属性</span><span class="sxs-lookup"><span data-stu-id="0ef02-114">To view pull subscription properties from the Publisher in Management Studio</span></span>  
  
1.  <span data-ttu-id="0ef02-115">在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中连接到发布服务器，然后展开服务器节点。</span><span class="sxs-lookup"><span data-stu-id="0ef02-115">Connect to the Publisher in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="0ef02-116">展开 **“复制”** 文件夹，再展开 **“本地发布”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="0ef02-116">Expand the **Replication** folder, and then expand the **Local Publications** folder.</span></span>  
  
3.  <span data-ttu-id="0ef02-117">展开相应的发布，右键单击订阅，然后单击 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="0ef02-117">Expand the appropriate publication, right-click a subscription, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="0ef02-118">查看属性，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="0ef02-118">View properties, and then click **OK**.</span></span>  
  
#### <a name="to-view-and-modify-pull-subscription-properties-from-the-subscriber-in-management-studio"></a><span data-ttu-id="0ef02-119">从 Management Studio 中的订阅服务器查看和修改请求订阅属性</span><span class="sxs-lookup"><span data-stu-id="0ef02-119">To view and modify pull subscription properties from the Subscriber in Management Studio</span></span>  
  
1.  <span data-ttu-id="0ef02-120">在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中连接到订阅服务器，然后展开服务器节点。</span><span class="sxs-lookup"><span data-stu-id="0ef02-120">Connect to the Subscriber in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="0ef02-121">展开 **“复制”** 文件夹，再展开 **“本地订阅”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="0ef02-121">Expand the **Replication** folder, and then expand the **Local Subscriptions** folder.</span></span>  
  
3.  <span data-ttu-id="0ef02-122">右键单击订阅，然后单击 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="0ef02-122">Right-click a subscription, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="0ef02-123">根据需要修改属性，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="0ef02-123">Modify any properties if necessary, and then click **OK**.</span></span>  
  
#### <a name="to-view-pull-subscription-properties-from-the-publisher-in-replication-monitor"></a><span data-ttu-id="0ef02-124">从复制监视器的发布服务器查看请求订阅属性</span><span class="sxs-lookup"><span data-stu-id="0ef02-124">To view pull subscription properties from the Publisher in Replication Monitor</span></span>  
  
1.  <span data-ttu-id="0ef02-125">在复制监视器的左窗格中依次展开发布服务器组、发布服务器，然后单击某个发布。</span><span class="sxs-lookup"><span data-stu-id="0ef02-125">Expand a Publisher group in the left pane of Replication Monitor, expand a Publisher, and then click a publication.</span></span>  
  
2.  <span data-ttu-id="0ef02-126">单击 **“所有订阅”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="0ef02-126">Click the **All Subscriptions** tab.</span></span>  
  
3.  <span data-ttu-id="0ef02-127">右键单击订阅，然后单击 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="0ef02-127">Right-click a subscription, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="0ef02-128">查看属性，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="0ef02-128">View properties, and then click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="0ef02-129">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="0ef02-129">Using Transact-SQL</span></span>  
 <span data-ttu-id="0ef02-130">可以使用复制存储过程以编程方式修改请求订阅以及访问其属性。</span><span class="sxs-lookup"><span data-stu-id="0ef02-130">Pull subscriptions can be modified and their properties accessed programmatically using replication stored procedures.</span></span> <span data-ttu-id="0ef02-131">所用的存储过程取决于订阅所属的发布的类型。</span><span class="sxs-lookup"><span data-stu-id="0ef02-131">The stored procedures used depend on the type of publication to which the subscription belongs.</span></span>  
  
#### <a name="to-view-the-properties-of-a-pull-subscription-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="0ef02-132">查看对快照发布或事务发布的请求订阅的属性</span><span class="sxs-lookup"><span data-stu-id="0ef02-132">To view the properties of a pull subscription to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="0ef02-133">在订阅服务器上，执行 [sp_helppullsubscription](/sql/relational-databases/system-stored-procedures/sp-helppullsubscription-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="0ef02-133">At the Subscriber, execute [sp_helppullsubscription](/sql/relational-databases/system-stored-procedures/sp-helppullsubscription-transact-sql).</span></span> <span data-ttu-id="0ef02-134">指定 **@publisher** 、 **@publisher_db** 和 **@publication** 。</span><span class="sxs-lookup"><span data-stu-id="0ef02-134">Specify **@publisher**, **@publisher_db**, and **@publication**.</span></span> <span data-ttu-id="0ef02-135">此操作将返回关于存储在订阅服务器上系统表中的订阅的信息。</span><span class="sxs-lookup"><span data-stu-id="0ef02-135">This returns information about the subscription that is stored in system tables at the Subscriber.</span></span>  
  
2.  <span data-ttu-id="0ef02-136">在订阅服务器上，执行 [sp_helpsubscription_properties](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="0ef02-136">At the Subscriber, execute [sp_helpsubscription_properties](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql).</span></span> <span data-ttu-id="0ef02-137">**@publisher**为指定、 **@publisher_db** 、 **@publication** 和以下值之一 **@publication_type** ：</span><span class="sxs-lookup"><span data-stu-id="0ef02-137">Specify **@publisher**, **@publisher_db**, **@publication**, and one of the following values for **@publication_type**:</span></span>  
  
    -   <span data-ttu-id="0ef02-138">**0** - 订阅属于事务发布。</span><span class="sxs-lookup"><span data-stu-id="0ef02-138">**0** - Subscription belongs to a transactional publication.</span></span>  
  
    -   <span data-ttu-id="0ef02-139">**1** - 订阅属于快照发布。</span><span class="sxs-lookup"><span data-stu-id="0ef02-139">**1** - Subscription belongs to a snapshot publication.</span></span>  
  
3.  <span data-ttu-id="0ef02-140">在发布服务器上，执行 [sp_helpsubscription](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="0ef02-140">At the Publisher, execute [sp_helpsubscription](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql).</span></span> <span data-ttu-id="0ef02-141">指定 **@publication** 和 **@subscriber** 。</span><span class="sxs-lookup"><span data-stu-id="0ef02-141">Specify **@publication** and **@subscriber**.</span></span>  
  
4.  <span data-ttu-id="0ef02-142">在发布服务器上，执行[sp_helpsubscriberinfo](/sql/relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql)，并指定 **@subscriber** 。</span><span class="sxs-lookup"><span data-stu-id="0ef02-142">At the Publisher, execute [sp_helpsubscriberinfo](/sql/relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql), specifying **@subscriber**.</span></span> <span data-ttu-id="0ef02-143">此操作将显示关于订阅服务器的信息。</span><span class="sxs-lookup"><span data-stu-id="0ef02-143">This displays information about the Subscriber.</span></span>  
  
#### <a name="to-change-the-properties-of-a-pull-subscription-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="0ef02-144">更改对快照发布或事务发布的请求订阅的属性</span><span class="sxs-lookup"><span data-stu-id="0ef02-144">To change the properties of a pull subscription to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="0ef02-145">在订阅服务器上，执行[sp_change_subscription_properties](/sql/relational-databases/system-stored-procedures/sp-change-subscription-properties-transact-sql)，同时指定 **@publisher** 、、、值为 **@publisher_db** **@publication** **0** (事务性) 或**1** (快照) **@publication_type** ，将更改为的订阅属性 **@property** ，并将新值指定为 **@value** 。</span><span class="sxs-lookup"><span data-stu-id="0ef02-145">At the Subscriber, execute [sp_change_subscription_properties](/sql/relational-databases/system-stored-procedures/sp-change-subscription-properties-transact-sql), specifying **@publisher**, **@publisher_db**, **@publication**, a value of either **0** (transactional) or **1** (snapshot) for **@publication_type**, the subscription property being changed as **@property**, and the new value as **@value**.</span></span>  
  
2.  <span data-ttu-id="0ef02-146">（可选）在订阅服务器上，对订阅数据库执行 [sp_changesubscriptiondtsinfo](/sql/relational-databases/system-stored-procedures/sp-changesubscriptiondtsinfo-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="0ef02-146">(Optional) At the Subscriber on the subscription database, execute [sp_changesubscriptiondtsinfo](/sql/relational-databases/system-stored-procedures/sp-changesubscriptiondtsinfo-transact-sql).</span></span> <span data-ttu-id="0ef02-147">为指定分发代理作业的 ID **@jobid** ，并将以下数据转换服务 (DTS) 包属性：</span><span class="sxs-lookup"><span data-stu-id="0ef02-147">Specify the ID of the Distribution Agent job for **@jobid**, and the following Data Transformation Services (DTS) package properties:</span></span>  
  
    -   **@dts_package_name**  
  
    -   **@dts_package_password**  
  
    -   **@dts_package_location**  
  
     <span data-ttu-id="0ef02-148">此操作将更改订阅的 DTS 包属性。</span><span class="sxs-lookup"><span data-stu-id="0ef02-148">This changes the DTS package properties of a subscription.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0ef02-149">可以通过执行 [sp_helpsubscription](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql)来获得作业 ID。</span><span class="sxs-lookup"><span data-stu-id="0ef02-149">The job ID can be obtained by executing [sp_helpsubscription](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql).</span></span>  
  
#### <a name="to-view-the-properties-of-a-pull-subscription-to-a-merge-publication"></a><span data-ttu-id="0ef02-150">查看对合并发布的请求订阅的属性</span><span class="sxs-lookup"><span data-stu-id="0ef02-150">To view the properties of a pull subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="0ef02-151">在订阅服务器上，执行 [sp_helpmergepullsubscription](/sql/relational-databases/system-stored-procedures/sp-helpmergepullsubscription-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="0ef02-151">At the Subscriber, execute [sp_helpmergepullsubscription](/sql/relational-databases/system-stored-procedures/sp-helpmergepullsubscription-transact-sql).</span></span> <span data-ttu-id="0ef02-152">指定 **@publisher** 、 **@publisher_db** 和 **@publication** 。</span><span class="sxs-lookup"><span data-stu-id="0ef02-152">Specify **@publisher**, **@publisher_db**, and **@publication**.</span></span>  
  
2.  <span data-ttu-id="0ef02-153">在订阅服务器上，执行 [sp_helpsubscription_properties](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="0ef02-153">At the Subscriber, execute [sp_helpsubscription_properties](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql).</span></span> <span data-ttu-id="0ef02-154">**@publisher**将、 **@publisher_db** 、 **@publication** 和的值指定为 2 **@publication_type** 。</span><span class="sxs-lookup"><span data-stu-id="0ef02-154">Specify **@publisher**, **@publisher_db**, **@publication**, and a value of 2 for **@publication_type**.</span></span>  
  
3.  <span data-ttu-id="0ef02-155">在发布服务器上，执行 [sp_helpmergesubscription](/sql/relational-databases/system-stored-procedures/sp-helpmergesubscription-transact-sql) 以显示订阅信息。</span><span class="sxs-lookup"><span data-stu-id="0ef02-155">At the Publisher, execute [sp_helpmergesubscription](/sql/relational-databases/system-stored-procedures/sp-helpmergesubscription-transact-sql) to display subscription information.</span></span> <span data-ttu-id="0ef02-156">若要返回有关特定订阅的信息，您必须 **@publication** **@subscriber** 为、和的值指定**pull** **@subscription_type** 。</span><span class="sxs-lookup"><span data-stu-id="0ef02-156">To return information on a specific subscription, you must specify **@publication**, **@subscriber**, and a value of **pull** for **@subscription_type**.</span></span>  
  
4.  <span data-ttu-id="0ef02-157">在发布服务器上，执行[sp_helpsubscriberinfo](/sql/relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql)，并指定 **@subscriber** 。</span><span class="sxs-lookup"><span data-stu-id="0ef02-157">At the Publisher, execute [sp_helpsubscriberinfo](/sql/relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql), specifying **@subscriber**.</span></span> <span data-ttu-id="0ef02-158">此操作将显示关于订阅服务器的信息。</span><span class="sxs-lookup"><span data-stu-id="0ef02-158">This displays information about the Subscriber.</span></span>  
  
#### <a name="to-change-the-properties-of-a-pull-subscription-to-a-merge-publication"></a><span data-ttu-id="0ef02-159">更改对合并发布的请求订阅的属性</span><span class="sxs-lookup"><span data-stu-id="0ef02-159">To change the properties of a pull subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="0ef02-160">在订阅服务器上，执行 [sp_changemergepullsubscription](/sql/relational-databases/system-stored-procedures/sp-changemergepullsubscription-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="0ef02-160">At the Subscriber, execute [sp_changemergepullsubscription](/sql/relational-databases/system-stored-procedures/sp-changemergepullsubscription-transact-sql).</span></span> <span data-ttu-id="0ef02-161">指定 **@publication** 、 **@publisher** 、 **@publisher_db** 、要更改为的订阅属性 **@property** ，并将新值指定为 **@value** 。</span><span class="sxs-lookup"><span data-stu-id="0ef02-161">Specify **@publication**, **@publisher**, **@publisher_db**, the subscription property being changed as **@property**, and the new value as **@value**.</span></span>  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="0ef02-162">使用复制管理对象 (RMO)</span><span class="sxs-lookup"><span data-stu-id="0ef02-162">Using Replication Management Objects (RMO)</span></span>  
 <span data-ttu-id="0ef02-163">用于查看或修改请求订阅属性的 RMO 类取决于订阅请求订阅的发布类型。</span><span class="sxs-lookup"><span data-stu-id="0ef02-163">The RMO classes you use to view or modify pull subscription properties depend on the type of publication to which the pull subscription is subscribed.</span></span>  
  
#### <a name="to-view-or-modify-properties-of-a-pull-subscription-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="0ef02-164">查看或修改对快照发布或事务发布的请求订阅的属性</span><span class="sxs-lookup"><span data-stu-id="0ef02-164">To view or modify properties of a pull subscription to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="0ef02-165">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 类创建与订阅服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="0ef02-165">Create a connection to the Subscriber by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="0ef02-166">创建的 <xref:Microsoft.SqlServer.Replication.TransPullSubscription> 类的实例。</span><span class="sxs-lookup"><span data-stu-id="0ef02-166">Create an instance of the <xref:Microsoft.SqlServer.Replication.TransPullSubscription> class.</span></span>  
  
3.  <span data-ttu-id="0ef02-167">设置 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>、 <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>、 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>和 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="0ef02-167">Set the <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>, and <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A> properties.</span></span>  
  
4.  <span data-ttu-id="0ef02-168">为 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 属性设置步骤 1 中的连接。</span><span class="sxs-lookup"><span data-stu-id="0ef02-168">Set the connection from step 1 for the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property.</span></span>  
  
5.  <span data-ttu-id="0ef02-169">调用 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法获取该对象的属性。</span><span class="sxs-lookup"><span data-stu-id="0ef02-169">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span> <span data-ttu-id="0ef02-170">如果此方法返回 `false`，则说明步骤 3 中的订阅属性定义不正确或服务器上不存在此订阅。</span><span class="sxs-lookup"><span data-stu-id="0ef02-170">If this method returns `false`, either the subscription properties in step 3 were defined incorrectly or the subscription does not exist on the server.</span></span>  
  
6.  <span data-ttu-id="0ef02-171">（可选）若要更改属性，请为可以设置的 <xref:Microsoft.SqlServer.Replication.TransPullSubscription> 属性中的一个设置新值，然后再调用 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="0ef02-171">(Optional) To change properties, set a new value for one of the <xref:Microsoft.SqlServer.Replication.TransPullSubscription> properties that can be set, and then call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> method.</span></span>  
  
7.  <span data-ttu-id="0ef02-172">（可选）若要查看新设置，请调用 <xref:Microsoft.SqlServer.Replication.ReplicationObject.Refresh%2A> 方法以重新加载该项目的属性。</span><span class="sxs-lookup"><span data-stu-id="0ef02-172">(Optional) To view the new settings, call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.Refresh%2A> method to reload the properties for the article.</span></span>  
  
8.  <span data-ttu-id="0ef02-173">关闭所有连接。</span><span class="sxs-lookup"><span data-stu-id="0ef02-173">Close all connections.</span></span>  
  
#### <a name="to-view-or-modify-properties-of-a-pull-subscription-to-a-merge-publication"></a><span data-ttu-id="0ef02-174">查看或修改对合并发布的请求订阅的属性</span><span class="sxs-lookup"><span data-stu-id="0ef02-174">To view or modify properties of a pull subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="0ef02-175">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 类创建与订阅服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="0ef02-175">Create a connection to the Subscriber by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="0ef02-176">创建的 <xref:Microsoft.SqlServer.Replication.MergePullSubscription> 类的实例。</span><span class="sxs-lookup"><span data-stu-id="0ef02-176">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergePullSubscription> class.</span></span>  
  
3.  <span data-ttu-id="0ef02-177">设置 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>、 <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>、 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>和 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="0ef02-177">Set the <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>, and <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A> properties.</span></span>  
  
4.  <span data-ttu-id="0ef02-178">为 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 属性设置步骤 1 中的连接。</span><span class="sxs-lookup"><span data-stu-id="0ef02-178">Set the connection from step 1 for the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property.</span></span>  
  
5.  <span data-ttu-id="0ef02-179">调用 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法获取该对象的属性。</span><span class="sxs-lookup"><span data-stu-id="0ef02-179">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span> <span data-ttu-id="0ef02-180">如果此方法返回 `false`，则说明步骤 3 中的订阅属性定义不正确或服务器上不存在此订阅。</span><span class="sxs-lookup"><span data-stu-id="0ef02-180">If this method returns `false`, either the subscription properties in step 3 were defined incorrectly or the subscription does not exist on the server.</span></span>  
  
6.  <span data-ttu-id="0ef02-181">（可选）若要更改属性，请为可以设置的 <xref:Microsoft.SqlServer.Replication.MergePullSubscription> 属性中的一个设置新值，然后再调用 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="0ef02-181">(Optional) To change properties, set a new value for one of the <xref:Microsoft.SqlServer.Replication.MergePullSubscription> properties that can be set, and then call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> method.</span></span>  
  
7.  <span data-ttu-id="0ef02-182">（可选）若要查看新设置，请调用 <xref:Microsoft.SqlServer.Replication.ReplicationObject.Refresh%2A> 方法以重新加载该项目的属性。</span><span class="sxs-lookup"><span data-stu-id="0ef02-182">(Optional) To view the new settings, call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.Refresh%2A> method to reload the properties for the article.</span></span>  
  
8.  <span data-ttu-id="0ef02-183">关闭所有连接。</span><span class="sxs-lookup"><span data-stu-id="0ef02-183">Close all connections.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ef02-184">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0ef02-184">See Also</span></span>  
 <span data-ttu-id="0ef02-185">[使用复制监视器查看信息和执行任务](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="0ef02-185">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 <span data-ttu-id="0ef02-186">[Replication Security Best Practices](security/replication-security-best-practices.md) </span><span class="sxs-lookup"><span data-stu-id="0ef02-186">[Replication Security Best Practices](security/replication-security-best-practices.md) </span></span>  
 [<span data-ttu-id="0ef02-187">订阅发布</span><span class="sxs-lookup"><span data-stu-id="0ef02-187">Subscribe to Publications</span></span>](subscribe-to-publications.md)  
  
  
