---
title: 删除发布 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- removing publications
- publications [SQL Server replication], deleting
- articles [SQL Server replication], deleting
- deleting publications
ms.assetid: 408a1360-12ee-4896-ac94-482ae839593b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5d2b39a326d59333868b4f8015eb9a2e59d59e44
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693728"
---
# <a name="delete-a-publication"></a><span data-ttu-id="2d95a-102">删除发布</span><span class="sxs-lookup"><span data-stu-id="2d95a-102">Delete a Publication</span></span>
  <span data-ttu-id="2d95a-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]或复制管理对象 (RMO) 在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中删除发布。</span><span class="sxs-lookup"><span data-stu-id="2d95a-103">This topic describes how to delete a publication in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or Replication Management Objects (RMO).</span></span>  
  
 <span data-ttu-id="2d95a-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="2d95a-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="2d95a-105">**删除发布，使用：**</span><span class="sxs-lookup"><span data-stu-id="2d95a-105">**To delete a publication, using:**</span></span>  
  
     [<span data-ttu-id="2d95a-106">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2d95a-106">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="2d95a-107">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2d95a-107">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="2d95a-108">复制管理对象 (RMO)</span><span class="sxs-lookup"><span data-stu-id="2d95a-108">Replication Management Objects (RMO)</span></span>](#RMOProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="2d95a-109">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2d95a-109">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="2d95a-110">从 **中的** “本地发布” [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]文件夹中删除发布。</span><span class="sxs-lookup"><span data-stu-id="2d95a-110">Delete publications from the **Local Publications** folder in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].</span></span>  
  
#### <a name="to-delete-a-publication"></a><span data-ttu-id="2d95a-111">删除发布</span><span class="sxs-lookup"><span data-stu-id="2d95a-111">To delete a publication</span></span>  
  
1.  <span data-ttu-id="2d95a-112">在 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]中连接到发布服务器，然后展开服务器节点。</span><span class="sxs-lookup"><span data-stu-id="2d95a-112">Connect to the Publisher in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="2d95a-113">展开 **“复制”** 文件夹，再展开 **“本地发布”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="2d95a-113">Expand the **Replication** folder, and then expand the **Local Publications** folder.</span></span>  
  
3.  <span data-ttu-id="2d95a-114">右键单击要删除的发布，然后单击 **“删除”** 。</span><span class="sxs-lookup"><span data-stu-id="2d95a-114">Right-click the publication you want to delete, and then click **Delete**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="2d95a-115">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2d95a-115">Using Transact-SQL</span></span>  
 <span data-ttu-id="2d95a-116">可以使用复制存储过程以编程方式删除发布。</span><span class="sxs-lookup"><span data-stu-id="2d95a-116">Publications can be deleted programmatically using replication stored procedures.</span></span> <span data-ttu-id="2d95a-117">使用的存储过程取决于要删除的发布的类型。</span><span class="sxs-lookup"><span data-stu-id="2d95a-117">The stored procedures that you use depend on the type of publication being deleted.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2d95a-118">删除发布并不会删除发布数据库中的已发布对象，也不会删除订阅数据库中的相应对象。</span><span class="sxs-lookup"><span data-stu-id="2d95a-118">Deleting a publication does not remove published objects from the publication database or the corresponding objects from the subscription database.</span></span> <span data-ttu-id="2d95a-119">如有必要，使用 `DROP <object>` 命令手动删除这些对象。</span><span class="sxs-lookup"><span data-stu-id="2d95a-119">Use the `DROP <object>` command to manually remove these objects if necessary.</span></span>  
  
#### <a name="to-delete-a-snapshot-or-transactional-publication"></a><span data-ttu-id="2d95a-120">删除快照发布或事务发布</span><span class="sxs-lookup"><span data-stu-id="2d95a-120">To delete a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="2d95a-121">执行下列操作之一：</span><span class="sxs-lookup"><span data-stu-id="2d95a-121">Do one of the following:</span></span>  
  
    -   <span data-ttu-id="2d95a-122">若要删除单个发布，请在发布服务器上，对发布数据库执行 [sp_droppublication](/sql/relational-databases/system-stored-procedures/sp-droppublication-transact-sql) 。</span><span class="sxs-lookup"><span data-stu-id="2d95a-122">To delete a single publication, execute [sp_droppublication](/sql/relational-databases/system-stored-procedures/sp-droppublication-transact-sql) at the Publisher on the publication database.</span></span>  
  
    -   <span data-ttu-id="2d95a-123">若要删除发布数据库中的所有发布并删除其中的所有复制对象，请在发布服务器上执行 [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) 。</span><span class="sxs-lookup"><span data-stu-id="2d95a-123">To delete all publications in and remove all replication objects from a published database, execute [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) at the Publisher.</span></span> <span data-ttu-id="2d95a-124">将类型的值 `tran` 指定\*\* \@ \*\*为。</span><span class="sxs-lookup"><span data-stu-id="2d95a-124">Specify a value of `tran` for **\@type**.</span></span> <span data-ttu-id="2d95a-125">（可选）如果无法访问分发服务器，或者数据库的状态为可疑或脱机，则将 \@force 的值指定为 1 。</span><span class="sxs-lookup"><span data-stu-id="2d95a-125">(Optional) If the Distributor cannot be accessed or if the status of the database is suspect or offline, specify a value of **1** for **\@force**.</span></span> <span data-ttu-id="2d95a-126">（可选）如果未对发布数据库执行 [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql)，请为 \@dbname 指定数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="2d95a-126">(Optional) Specify the name of the database for **\@dbname** if [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) is not executed on the publication database.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="2d95a-127">将 \@force 的值指定为 1 可能会使与复制相关的发布对象保留在数据库中 。</span><span class="sxs-lookup"><span data-stu-id="2d95a-127">Specifying a value of **1** for **\@force** may leave replication-related publishing objects in the database.</span></span>  
  
2.  <span data-ttu-id="2d95a-128">如果此数据库中没有任何其他发布，则执行 [sp_replicationdboption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql) 以禁止当前数据库使用快照复制或事务复制进行发布。</span><span class="sxs-lookup"><span data-stu-id="2d95a-128">(Optional) If this database has no other publications, execute [sp_replicationdboption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql) to disable publication of the current database using snapshot or transactional replication.</span></span>  
  
3.  <span data-ttu-id="2d95a-129">（可选）在订阅服务器上，对订阅数据库执行 [sp_subscription_cleanup](/sql/relational-databases/system-stored-procedures/sp-subscription-cleanup-transact-sql) 以删除订阅数据库中的任何剩余复制元数据。</span><span class="sxs-lookup"><span data-stu-id="2d95a-129">(Optional) At the Subscriber on the subscription database, execute [sp_subscription_cleanup](/sql/relational-databases/system-stored-procedures/sp-subscription-cleanup-transact-sql) to remove any remaining replication metadata in the subscription database.</span></span>  
  
#### <a name="to-delete-a-merge-publication"></a><span data-ttu-id="2d95a-130">删除合并发布</span><span class="sxs-lookup"><span data-stu-id="2d95a-130">To delete a merge publication</span></span>  
  
1.  <span data-ttu-id="2d95a-131">执行下列操作之一：</span><span class="sxs-lookup"><span data-stu-id="2d95a-131">Do one of the following:</span></span>  
  
    -   <span data-ttu-id="2d95a-132">若要删除单个发布，请在发布服务器上对发布数据库执行 [sp_dropmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropmergepublication-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2d95a-132">To delete a single publication, execute [sp_dropmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropmergepublication-transact-sql) at the Publisher on the publication database.</span></span>  
  
    -   <span data-ttu-id="2d95a-133">若要删除发布数据库中的所有发布并删除其中的所有复制对象，请在发布服务器上执行 [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) 。</span><span class="sxs-lookup"><span data-stu-id="2d95a-133">To delete all publications in and remove all replication objects from a published database, execute [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) at the Publisher.</span></span> <span data-ttu-id="2d95a-134">将类型的值 `merge` 指定\*\* \@ \*\*为。</span><span class="sxs-lookup"><span data-stu-id="2d95a-134">Specify a value of `merge` for **\@type**.</span></span> <span data-ttu-id="2d95a-135">（可选）如果无法访问分发服务器，或者数据库的状态为可疑或脱机，则将 \@force 的值指定为 1 。</span><span class="sxs-lookup"><span data-stu-id="2d95a-135">(Optional) If the Distributor cannot be accessed or if the status of the database is suspect or offline, specify a value of **1** for **\@force**.</span></span> <span data-ttu-id="2d95a-136">（可选）如果未对发布数据库执行 [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql)，请为 \@dbname 指定数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="2d95a-136">(Optional) Specify the name of the database for **\@dbname** if [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) is not executed on the publication database.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="2d95a-137">将 \@force 的值指定为 1 可能会使与复制相关的发布对象保留在数据库中 。</span><span class="sxs-lookup"><span data-stu-id="2d95a-137">Specifying a value of **1** for **\@force** may leave replication-related publishing objects in the database.</span></span>  
  
2.  <span data-ttu-id="2d95a-138">如果此数据库中没有任何其他发布，则执行 [sp_replicationdboption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql) 以禁止当前数据库使用合并复制进行发布。</span><span class="sxs-lookup"><span data-stu-id="2d95a-138">(Optional) If this database has no other publications, execute [sp_replicationdboption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql) to disable publication of the current database using merge replication.</span></span>  
  
3.  <span data-ttu-id="2d95a-139">在订阅服务器上，对订阅数据库执行 [sp_mergesubscription_cleanup &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-mergesubscription-cleanup-transact-sql) 以删除订阅数据库中的任何剩余复制元数据。</span><span class="sxs-lookup"><span data-stu-id="2d95a-139">(Optional) At the Subscriber on the subscription database, execute [sp_mergesubscription_cleanup &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-mergesubscription-cleanup-transact-sql) to remove any remaining replication metadata in the subscription database.</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="2d95a-140">示例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="2d95a-140">Examples (Transact-SQL)</span></span>  
 <span data-ttu-id="2d95a-141">该示例演示如何删除事务发布并禁用数据库的事务发布。</span><span class="sxs-lookup"><span data-stu-id="2d95a-141">This example shows how to remove a transactional publication and disable transactional publishing for a database.</span></span> <span data-ttu-id="2d95a-142">该示例假定以前删除了所有订阅。</span><span class="sxs-lookup"><span data-stu-id="2d95a-142">This example assumes that all subscriptions were previously removed.</span></span> <span data-ttu-id="2d95a-143">有关详细信息，请参阅 [Delete a Pull Subscription](../delete-a-pull-subscription.md) 或 [Delete a Push Subscription](../delete-a-push-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="2d95a-143">For more information, see [Delete a Pull Subscription](../delete-a-pull-subscription.md) or [Delete a Push Subscription](../delete-a-push-subscription.md).</span></span>  
  
 [!code-sql[HowTo#sp_droppublication](../../../snippets/tsql/SQL15/replication/howto/tsql/droptranpub.sql#sp_droppublication)]  
  
 <span data-ttu-id="2d95a-144">该示例演示如何删除合并发布并禁用数据库的合并发布。</span><span class="sxs-lookup"><span data-stu-id="2d95a-144">This example shows how to remove a merge publication and disable merge publishing for a database.</span></span> <span data-ttu-id="2d95a-145">该示例假定以前删除了所有订阅。</span><span class="sxs-lookup"><span data-stu-id="2d95a-145">This example assumes that all subscriptions were previously removed.</span></span> <span data-ttu-id="2d95a-146">有关详细信息，请参阅 [Delete a Pull Subscription](../delete-a-pull-subscription.md) 或 [Delete a Push Subscription](../delete-a-push-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="2d95a-146">For more information, see [Delete a Pull Subscription](../delete-a-pull-subscription.md) or [Delete a Push Subscription](../delete-a-push-subscription.md).</span></span>  
  
 [!code-sql[HowTo#sp_dropmergepublication](../../../snippets/tsql/SQL15/replication/howto/tsql/dropmergepub.sql#sp_dropmergepublication)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="2d95a-147">使用复制管理对象 (RMO)</span><span class="sxs-lookup"><span data-stu-id="2d95a-147">Using Replication Management Objects (RMO)</span></span>  
 <span data-ttu-id="2d95a-148">可以使用复制管理对象 (RMO) 以编程方式删除发布。</span><span class="sxs-lookup"><span data-stu-id="2d95a-148">You can delete publications programmatically by using Replication Management Objects (RMO).</span></span> <span data-ttu-id="2d95a-149">用于删除发布的 RMO 类取决于要删除的发布的类型。</span><span class="sxs-lookup"><span data-stu-id="2d95a-149">The RMO classes that you use to remove a publication depend on the type of publication you remove.</span></span>  
  
#### <a name="to-remove-a-snapshot-or-transactional-publication"></a><span data-ttu-id="2d95a-150">删除快照发布或事务发布</span><span class="sxs-lookup"><span data-stu-id="2d95a-150">To remove a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="2d95a-151">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 类创建与发布服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="2d95a-151">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="2d95a-152">创建的 <xref:Microsoft.SqlServer.Replication.TransPublication> 类的实例。</span><span class="sxs-lookup"><span data-stu-id="2d95a-152">Create an instance of the <xref:Microsoft.SqlServer.Replication.TransPublication> class.</span></span>  
  
3.  <span data-ttu-id="2d95a-153">设置发布的 <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> 和 <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> 属性，并将 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 属性设置为步骤 1 中创建的连接。</span><span class="sxs-lookup"><span data-stu-id="2d95a-153">Set the <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> and <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> properties for the publication, and set the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property to the connection created in step 1.</span></span>  
  
4.  <span data-ttu-id="2d95a-154">请检查 <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> 属性以验证发布是否存在。</span><span class="sxs-lookup"><span data-stu-id="2d95a-154">Check the <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> property to verify that the publication exists.</span></span> <span data-ttu-id="2d95a-155">如果此属性的值为 `false`，则步骤 3 中的发布属性定义不正确，或者发布不存在。</span><span class="sxs-lookup"><span data-stu-id="2d95a-155">If the value of this property is `false`, either the publication properties in step 3 were defined incorrectly or the publication does not exist.</span></span>  
  
5.  <span data-ttu-id="2d95a-156">调用 <xref:Microsoft.SqlServer.Replication.Publication.Remove%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="2d95a-156">Call the <xref:Microsoft.SqlServer.Replication.Publication.Remove%2A> method.</span></span>  
  
6.  <span data-ttu-id="2d95a-157">（可选）如果此数据库中不存在其他事务发布，则可按照下面的步骤为事务发布禁用此数据库：</span><span class="sxs-lookup"><span data-stu-id="2d95a-157">(Optional) If no other transactional publications exist for this database, the database can be disabled for transactional publishing as follows:</span></span>  
  
    1.  <span data-ttu-id="2d95a-158">创建的 <xref:Microsoft.SqlServer.Replication.ReplicationDatabase> 类的实例。</span><span class="sxs-lookup"><span data-stu-id="2d95a-158">Create an instance of the <xref:Microsoft.SqlServer.Replication.ReplicationDatabase> class.</span></span> <span data-ttu-id="2d95a-159">将 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 属性设置为步骤 1 中的 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 实例。</span><span class="sxs-lookup"><span data-stu-id="2d95a-159">Set the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property to the instance of <xref:Microsoft.SqlServer.Management.Common.ServerConnection> from step 1.</span></span>  
  
    2.  <span data-ttu-id="2d95a-160">调用 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="2d95a-160">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method.</span></span> <span data-ttu-id="2d95a-161">如果该方法返回 `false`，请确认数据库是否存在。</span><span class="sxs-lookup"><span data-stu-id="2d95a-161">If this method returns `false`, confirm that the database exists.</span></span>  
  
    3.  <span data-ttu-id="2d95a-162">将 <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.EnabledTransPublishing%2A> 属性设置为 `false`。</span><span class="sxs-lookup"><span data-stu-id="2d95a-162">Set the <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.EnabledTransPublishing%2A> property to `false`.</span></span>  
  
    4.  <span data-ttu-id="2d95a-163">调用 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="2d95a-163">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> method.</span></span>  
  
7.  <span data-ttu-id="2d95a-164">关闭连接。</span><span class="sxs-lookup"><span data-stu-id="2d95a-164">Close the connections.</span></span>  
  
#### <a name="to-remove-a-merge-publication"></a><span data-ttu-id="2d95a-165">删除合并发布</span><span class="sxs-lookup"><span data-stu-id="2d95a-165">To remove a merge publication</span></span>  
  
1.  <span data-ttu-id="2d95a-166">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 类创建与发布服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="2d95a-166">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="2d95a-167">创建的 <xref:Microsoft.SqlServer.Replication.MergePublication> 类的实例。</span><span class="sxs-lookup"><span data-stu-id="2d95a-167">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergePublication> class.</span></span>  
  
3.  <span data-ttu-id="2d95a-168">设置发布的 <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> 和 <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> 属性，并将 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 属性设置为步骤 1 中创建的连接。</span><span class="sxs-lookup"><span data-stu-id="2d95a-168">Set the <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> and <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> properties for the publication, and set the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property to the connection created in step 1.</span></span>  
  
4.  <span data-ttu-id="2d95a-169">请检查 <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> 属性以验证发布是否存在。</span><span class="sxs-lookup"><span data-stu-id="2d95a-169">Check the <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> property to verify that the publication exists.</span></span> <span data-ttu-id="2d95a-170">如果此属性的值为 `false`，则步骤 3 中的发布属性定义不正确，或者发布不存在。</span><span class="sxs-lookup"><span data-stu-id="2d95a-170">If the value of this property is `false`, either the publication properties in step 3 were defined incorrectly or the publication does not exist.</span></span>  
  
5.  <span data-ttu-id="2d95a-171">调用 <xref:Microsoft.SqlServer.Replication.Publication.Remove%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="2d95a-171">Call the <xref:Microsoft.SqlServer.Replication.Publication.Remove%2A> method.</span></span>  
  
6.  <span data-ttu-id="2d95a-172">（可选）如果此数据库中不存在其他合并发布，则可按照下面的步骤为合并发布禁用此数据库：</span><span class="sxs-lookup"><span data-stu-id="2d95a-172">(Optional) If no other merge publications exist for this database, the database can be disabled for merge publishing as follows:</span></span>  
  
    1.  <span data-ttu-id="2d95a-173">创建的 <xref:Microsoft.SqlServer.Replication.ReplicationDatabase> 类的实例。</span><span class="sxs-lookup"><span data-stu-id="2d95a-173">Create an instance of the <xref:Microsoft.SqlServer.Replication.ReplicationDatabase> class.</span></span> <span data-ttu-id="2d95a-174">将 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 属性设置为步骤 1 中的 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 实例。</span><span class="sxs-lookup"><span data-stu-id="2d95a-174">Set the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property to the instance of <xref:Microsoft.SqlServer.Management.Common.ServerConnection> from Step 1.</span></span>  
  
    2.  <span data-ttu-id="2d95a-175">调用 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="2d95a-175">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method.</span></span> <span data-ttu-id="2d95a-176">如果该方法返回 `false`，请验证数据库是否存在。</span><span class="sxs-lookup"><span data-stu-id="2d95a-176">If this method returns `false`, verify that the database exists.</span></span>  
  
    3.  <span data-ttu-id="2d95a-177">将 <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.EnabledMergePublishing%2A> 属性设置为 `false`。</span><span class="sxs-lookup"><span data-stu-id="2d95a-177">Set the <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.EnabledMergePublishing%2A> property to `false`.</span></span>  
  
    4.  <span data-ttu-id="2d95a-178">调用 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="2d95a-178">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> method.</span></span>  
  
7.  <span data-ttu-id="2d95a-179">关闭连接。</span><span class="sxs-lookup"><span data-stu-id="2d95a-179">Close the connections.</span></span>  
  
###  <a name="examples-rmo"></a><a name="PShellExample"></a> <span data-ttu-id="2d95a-180">示例 (RMO)</span><span class="sxs-lookup"><span data-stu-id="2d95a-180">Examples (RMO)</span></span>  
 <span data-ttu-id="2d95a-181">下面的示例删除事务发布。</span><span class="sxs-lookup"><span data-stu-id="2d95a-181">The following example deletes a transactional publication.</span></span> <span data-ttu-id="2d95a-182">如果此数据库不存在其他事务发布，则事务发布也被禁用。</span><span class="sxs-lookup"><span data-stu-id="2d95a-182">If no other transactional publications exist for this database, transactional publishing is also disabled.</span></span>  
  
 [!code-csharp[HowTo#rmo_DropTranPub](../../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_droptranpub)]  
  
 [!code-vb[HowTo#rmo_vb_DropTranPub](../../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_droptranpub)]  
  
 <span data-ttu-id="2d95a-183">下面的示例删除合并发布。</span><span class="sxs-lookup"><span data-stu-id="2d95a-183">The following example deletes a merge publication.</span></span> <span data-ttu-id="2d95a-184">如果此数据库不存在其他合并发布，则合并发布也被禁用。</span><span class="sxs-lookup"><span data-stu-id="2d95a-184">If no other merge publications exist for this database, merge publishing is also disabled.</span></span>  
  
 [!code-csharp[HowTo#rmo_DropMergePub](../../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_dropmergepub)]  
  
 [!code-vb[HowTo#rmo_vb_DropMergePub](../../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_dropmergepub)]  
  
## <a name="see-also"></a><span data-ttu-id="2d95a-185">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2d95a-185">See Also</span></span>  
 <span data-ttu-id="2d95a-186">[Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="2d95a-186">[Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md) </span></span>  
 [<span data-ttu-id="2d95a-187">发布数据和数据库对象</span><span class="sxs-lookup"><span data-stu-id="2d95a-187">Publish Data and Database Objects</span></span>](publish-data-and-database-objects.md)  
  
  
