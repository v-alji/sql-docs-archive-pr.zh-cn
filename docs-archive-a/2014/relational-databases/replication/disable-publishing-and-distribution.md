---
title: 禁用发布和分发 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- disabling publishing
- publishing [SQL Server replication], disabling
- distribution disabling [SQL Server replication]
- removing replication
- replication [SQL Server], removing
- disabling replication
- disabling distribution
ms.assetid: 6d4a1474-4d13-4826-8be2-80050fafa8a5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8843dac310d1e023fe7ce63eded02c9e1bed3731
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578120"
---
# <a name="disable-publishing-and-distribution"></a><span data-ttu-id="4d170-102">禁用发布和分发</span><span class="sxs-lookup"><span data-stu-id="4d170-102">Disable Publishing and Distribution</span></span>
  <span data-ttu-id="4d170-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]或复制管理对象 (RMO) 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中禁用发布和分发。</span><span class="sxs-lookup"><span data-stu-id="4d170-103">This topic describes how to disable publishing and distribution in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or Replication Management Objects (RMO).</span></span>  
  
 <span data-ttu-id="4d170-104">您可以执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="4d170-104">You can do the following:</span></span>  
  
-   <span data-ttu-id="4d170-105">删除分发服务器上的所有分发数据库。</span><span class="sxs-lookup"><span data-stu-id="4d170-105">Delete all distribution databases on the Distributor.</span></span>  
  
-   <span data-ttu-id="4d170-106">禁用使用分发服务器的所有发布服务器并删除这些发布服务器上的所有发布。</span><span class="sxs-lookup"><span data-stu-id="4d170-106">Disable all Publishers that use the Distributor and delete all publications on those Publishers.</span></span>  
  
-   <span data-ttu-id="4d170-107">删除对这些发布的所有订阅。</span><span class="sxs-lookup"><span data-stu-id="4d170-107">Delete all subscriptions to the publications.</span></span> <span data-ttu-id="4d170-108">发布和订阅数据库中的数据不会被删除，但它将失去与任何发布数据库的同步关系。</span><span class="sxs-lookup"><span data-stu-id="4d170-108">Data in the publication and subscription databases will not be deleted; however, it loses its synchronization relationship to any publication databases.</span></span> <span data-ttu-id="4d170-109">如果要删除订阅服务器上的数据，则必须手动删除。</span><span class="sxs-lookup"><span data-stu-id="4d170-109">If you want the data at the Subscriber to be deleted, you must delete it manually.</span></span>  
  
 <span data-ttu-id="4d170-110">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="4d170-110">**In This Topic**</span></span>  
  
-   <span data-ttu-id="4d170-111">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="4d170-111">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="4d170-112">先决条件</span><span class="sxs-lookup"><span data-stu-id="4d170-112">Prerequisites</span></span>](#Prerequisites)  
  
-   <span data-ttu-id="4d170-113">**禁用发布和分发，使用：**</span><span class="sxs-lookup"><span data-stu-id="4d170-113">**To disable publishing and distribution, using:**</span></span>  
  
     [<span data-ttu-id="4d170-114">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4d170-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="4d170-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4d170-115">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="4d170-116">复制管理对象 (RMO)</span><span class="sxs-lookup"><span data-stu-id="4d170-116">Replication Management Objects (RMO)</span></span>](#RMOProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="4d170-117">开始之前</span><span class="sxs-lookup"><span data-stu-id="4d170-117">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="4d170-118">先决条件</span><span class="sxs-lookup"><span data-stu-id="4d170-118">Prerequisites</span></span>  
  
-   <span data-ttu-id="4d170-119">若要禁用发布和分发，所有分发数据库和发布数据库都必须联机。</span><span class="sxs-lookup"><span data-stu-id="4d170-119">To disable publishing and distribution, all distribution and publication databases must be online.</span></span> <span data-ttu-id="4d170-120">如果存在分发数据库或发布数据库的“数据库快照”  ，则在禁用发布和分发前，必须先删除这些数据库快照。</span><span class="sxs-lookup"><span data-stu-id="4d170-120">If any *database snapshots* exist for distribution or publication databases, they must be dropped before disabling publishing and distribution.</span></span> <span data-ttu-id="4d170-121">数据库快照是数据库的只读脱机副本，与复制快照无关。</span><span class="sxs-lookup"><span data-stu-id="4d170-121">A database snapshot is a read-only offline copy of a database and is not related to a replication snapshot.</span></span> <span data-ttu-id="4d170-122">有关详细信息，请参阅[数据库快照 (SQL Server)](../databases/database-snapshots-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="4d170-122">For more information, see [Database Snapshots &#40;SQL Server&#41;](../databases/database-snapshots-sql-server.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="4d170-123">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4d170-123">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="4d170-124">使用禁用发布和分发向导禁用发布和分发。</span><span class="sxs-lookup"><span data-stu-id="4d170-124">Disable publishing and distribution by using the Disable Publishing and Distribution Wizard.</span></span>  
  
#### <a name="to-disable-publishing-and-distribution"></a><span data-ttu-id="4d170-125">禁用发布和分发</span><span class="sxs-lookup"><span data-stu-id="4d170-125">To disable publishing and distribution</span></span>  
  
1.  <span data-ttu-id="4d170-126">在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中连接到要禁用的发布服务器或分发服务器，然后展开该服务器节点。</span><span class="sxs-lookup"><span data-stu-id="4d170-126">Connect to the Publisher or Distributor you want to disable in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="4d170-127">右键单击 **“复制”** 文件夹，再单击 **“禁用发布和分发”** 。</span><span class="sxs-lookup"><span data-stu-id="4d170-127">Right-click the **Replication** folder, and then click **Disable Publishing and Distribution**.</span></span>  
  
3.  <span data-ttu-id="4d170-128">完成禁用发布和分发向导中的步骤。</span><span class="sxs-lookup"><span data-stu-id="4d170-128">Complete the steps in the Disable Publishing and Distribution Wizard.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="4d170-129">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4d170-129">Using Transact-SQL</span></span>  
 <span data-ttu-id="4d170-130">可以使用复制存储过程以编程方式禁用发布和分发。</span><span class="sxs-lookup"><span data-stu-id="4d170-130">Publishing and distributing can be disabled programmatically using replication stored procedures.</span></span>  
  
#### <a name="to-disable-publishing-and-distribution"></a><span data-ttu-id="4d170-131">禁用发布和分发</span><span class="sxs-lookup"><span data-stu-id="4d170-131">To disable publishing and distribution</span></span>  
  
1.  <span data-ttu-id="4d170-132">停止所有与复制相关的作业。</span><span class="sxs-lookup"><span data-stu-id="4d170-132">Stop all replication-related jobs.</span></span> <span data-ttu-id="4d170-133">有关作业名称列表，请参阅 [复制代理安全模式](security/replication-agent-security-model.md)的“SQL Server 代理下的代理安全性”部分。</span><span class="sxs-lookup"><span data-stu-id="4d170-133">For a list of job names, see the "Agent Security Under SQL Server Agent" section of [Replication Agent Security Model](security/replication-agent-security-model.md).</span></span>  
  
2.  <span data-ttu-id="4d170-134">在每个订阅服务器上，对订阅数据库执行 [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) 以从该数据库删除复制对象。</span><span class="sxs-lookup"><span data-stu-id="4d170-134">At each Subscriber on the subscription database, execute [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) to remove replication objects from the database.</span></span> <span data-ttu-id="4d170-135">此存储过程不会删除分发服务器上的复制作业。</span><span class="sxs-lookup"><span data-stu-id="4d170-135">This stored procedure will not remove replication jobs at the Distributor.</span></span>  
  
3.  <span data-ttu-id="4d170-136">在发布服务器上，对发布数据库执行 [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) 以从该数据库删除复制对象。</span><span class="sxs-lookup"><span data-stu-id="4d170-136">At the Publisher on the publication database, execute [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) to remove replication objects from the database.</span></span>  
  
4.  <span data-ttu-id="4d170-137">如果发布服务器使用远程分发服务器，则执行 [sp_dropdistributor](/sql/relational-databases/system-stored-procedures/sp-dropdistributor-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="4d170-137">If the Publisher uses a remote Distributor, execute [sp_dropdistributor](/sql/relational-databases/system-stored-procedures/sp-dropdistributor-transact-sql).</span></span>  
  
5.  <span data-ttu-id="4d170-138">在分发服务器上，执行 [sp_dropdistpublisher](/sql/relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="4d170-138">At the Distributor, execute [sp_dropdistpublisher](/sql/relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql).</span></span> <span data-ttu-id="4d170-139">应为在分发服务器上注册的每个发布服务器运行一次此存储过程。</span><span class="sxs-lookup"><span data-stu-id="4d170-139">This stored procedure should be run once for each Publisher registered at the Distributor.</span></span>  
  
6.  <span data-ttu-id="4d170-140">在分发服务器上，执行 [sp_dropdistributiondb](/sql/relational-databases/system-stored-procedures/sp-dropdistributiondb-transact-sql) 以删除分发数据库。</span><span class="sxs-lookup"><span data-stu-id="4d170-140">At the Distributor, execute [sp_dropdistributiondb](/sql/relational-databases/system-stored-procedures/sp-dropdistributiondb-transact-sql) to delete the distribution database.</span></span> <span data-ttu-id="4d170-141">应为在分发服务器上注册的每个分发数据库运行一次此存储过程。</span><span class="sxs-lookup"><span data-stu-id="4d170-141">This stored procedure should be run once for each distribution database at the Distributor.</span></span> <span data-ttu-id="4d170-142">此操作还将删除与分发数据库关联的任何队列读取器代理作业。</span><span class="sxs-lookup"><span data-stu-id="4d170-142">This also removes any Queue Reader Agent jobs associated with the distribution database.</span></span>  
  
7.  <span data-ttu-id="4d170-143">在分发服务器上，执行 [sp_dropdistributor](/sql/relational-databases/system-stored-procedures/sp-dropdistributor-transact-sql) 以从该服务器删除分发服务器指定。</span><span class="sxs-lookup"><span data-stu-id="4d170-143">At the Distributor, execute [sp_dropdistributor](/sql/relational-databases/system-stored-procedures/sp-dropdistributor-transact-sql) to remove the Distributor designation from the server.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4d170-144">如果在您执行 [sp_dropdistpublisher](/sql/relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql) 和 [sp_dropdistributor](/sql/relational-databases/system-stored-procedures/sp-dropdistributor-transact-sql)之前并未删除所有复制发布和分发对象，这些过程将返回错误。</span><span class="sxs-lookup"><span data-stu-id="4d170-144">If all replication publishing and distribution objects are not dropped before you execute [sp_dropdistpublisher](/sql/relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql) and [sp_dropdistributor](/sql/relational-databases/system-stored-procedures/sp-dropdistributor-transact-sql), these procedures will return an error.</span></span> <span data-ttu-id="4d170-145">若要在删除发布服务器或分发服务器时删除所有与复制相关的对象，必须将\*\* \@ no_checks**参数设置为**1\*\*。</span><span class="sxs-lookup"><span data-stu-id="4d170-145">To drop all replication-related objects when a Publisher or Distributor is dropped, the **\@no_checks** parameter must be set to **1**.</span></span> <span data-ttu-id="4d170-146">如果发布服务器或分发服务器脱机或无法访问，则可以将\*\* \@ ignore_distributor**参数设置为**1\*\* ，以便能够删除它们; 不过，必须手动删除任何保留的发布和分发对象。</span><span class="sxs-lookup"><span data-stu-id="4d170-146">If a Publisher or Distributor is offline or unreachable, the **\@ignore_distributor** parameter can be set to **1** so that they can be dropped; however, any publishing and distributing objects left behind must be removed manually.</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="4d170-147">示例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4d170-147">Examples (Transact-SQL)</span></span>  
 <span data-ttu-id="4d170-148">此示例脚本从订阅数据库删除复制对象。</span><span class="sxs-lookup"><span data-stu-id="4d170-148">This example script removes replication objects from the subscription database.</span></span>  
  
 [!code-sql[HowTo#sp_removedbreplication](../../snippets/tsql/SQL15/replication/howto/tsql/dropdistpub.sql#sp_removedbreplication)]  
  
 <span data-ttu-id="4d170-149">此示例脚本在既是发布服务器又是分发服务器的服务器上禁用发布和分发，并删除分发数据库。</span><span class="sxs-lookup"><span data-stu-id="4d170-149">This example script disables publishing and distribution on a server that is a Publisher and Distributor and drops the distribution database.</span></span>  
  
 [!code-sql[HowTo#sp_DropDistPub](../../snippets/tsql/SQL15/replication/howto/tsql/dropdistpub.sql#sp_dropdistpub)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="4d170-150">使用复制管理对象 (RMO)</span><span class="sxs-lookup"><span data-stu-id="4d170-150">Using Replication Management Objects (RMO)</span></span>  
  
#### <a name="to-disable-publishing-and-distribution"></a><span data-ttu-id="4d170-151">禁用发布和分发</span><span class="sxs-lookup"><span data-stu-id="4d170-151">To disable publishing and distribution</span></span>  
  
1.  <span data-ttu-id="4d170-152">删除所有使用分发服务器的发布订阅。</span><span class="sxs-lookup"><span data-stu-id="4d170-152">Remove all subscriptions to publications that use the Distributor.</span></span> <span data-ttu-id="4d170-153">有关详细信息，请参阅 [Delete a Pull Subscription](delete-a-pull-subscription.md) 和 [Delete a Push Subscription](delete-a-push-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="4d170-153">For more information, see [Delete a Pull Subscription](delete-a-pull-subscription.md) and [Delete a Push Subscription](delete-a-push-subscription.md).</span></span>  
  
2.  <span data-ttu-id="4d170-154">如果发布服务器和分发服务器在相同的服务器上，则删除所有使用分发服务器的发布，并禁用发布所有数据库。</span><span class="sxs-lookup"><span data-stu-id="4d170-154">Remove all publications that use the Distributor, and disable publishing for all databases if the Publisher and Distributor are on the same server.</span></span> <span data-ttu-id="4d170-155">有关详细信息，请参阅 [Delete a Publication](publish/delete-a-publication.md)。</span><span class="sxs-lookup"><span data-stu-id="4d170-155">For more information, see [Delete a Publication](publish/delete-a-publication.md).</span></span>  
  
3.  <span data-ttu-id="4d170-156">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 类创建与分发服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="4d170-156">Create a connection to the Distributor by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
4.  <span data-ttu-id="4d170-157">创建的 <xref:Microsoft.SqlServer.Replication.DistributionPublisher> 类的实例。</span><span class="sxs-lookup"><span data-stu-id="4d170-157">Create an instance of the <xref:Microsoft.SqlServer.Replication.DistributionPublisher> class.</span></span> <span data-ttu-id="4d170-158">指定 <xref:Microsoft.SqlServer.Replication.DistributionPublisher.Name%2A> 属性，并传递步骤 3 中的 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 对象。</span><span class="sxs-lookup"><span data-stu-id="4d170-158">Specify the <xref:Microsoft.SqlServer.Replication.DistributionPublisher.Name%2A> property, and pass the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object from step 3.</span></span>  
  
5.  <span data-ttu-id="4d170-159">（可选）调用 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法以获取对象的属性，并验证发布服务器是否存在。</span><span class="sxs-lookup"><span data-stu-id="4d170-159">(Optional) Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object and verify that the Publisher exists.</span></span> <span data-ttu-id="4d170-160">如果此方法返回 `false`，则步骤 4 中设置的发布服务器名称不正确，或者此分发服务器未使用该发布服务器。</span><span class="sxs-lookup"><span data-stu-id="4d170-160">If this method returns `false`, the Publisher name set in step 4 was incorrect or the Publisher is not used by this Distributor.</span></span>  
  
6.  <span data-ttu-id="4d170-161">调用 <xref:Microsoft.SqlServer.Replication.DistributionPublisher.Remove%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="4d170-161">Call the <xref:Microsoft.SqlServer.Replication.DistributionPublisher.Remove%2A> method.</span></span> <span data-ttu-id="4d170-162">`true`如果发布服务器和分发服务器位于不同的服务器上，并且应在分发服务器上卸载发布服务器，而不首先验证发布服务器上是否不再存在发布，请为 "*强制*" 传递值。</span><span class="sxs-lookup"><span data-stu-id="4d170-162">Pass a value of `true` for *force* if the Publisher and Distributor are on different servers, and when the Publisher should be uninstalled at the Distributor without first verifying that publications no longer exist at the Publisher.</span></span>  
  
7.  <span data-ttu-id="4d170-163">创建的 <xref:Microsoft.SqlServer.Replication.ReplicationServer> 类的实例。</span><span class="sxs-lookup"><span data-stu-id="4d170-163">Create an instance of the <xref:Microsoft.SqlServer.Replication.ReplicationServer> class.</span></span> <span data-ttu-id="4d170-164">传递步骤 3 中的 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 对象。</span><span class="sxs-lookup"><span data-stu-id="4d170-164">Pass the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object from step 3.</span></span>  
  
8.  <span data-ttu-id="4d170-165">调用 <xref:Microsoft.SqlServer.Replication.ReplicationServer.UninstallDistributor%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="4d170-165">Call the <xref:Microsoft.SqlServer.Replication.ReplicationServer.UninstallDistributor%2A> method.</span></span> <span data-ttu-id="4d170-166">将的值 " `true` *强制*" 传递到分发服务器上的所有复制对象，而不首先验证所有本地发布数据库是否已禁用以及分发数据库是否已卸载。</span><span class="sxs-lookup"><span data-stu-id="4d170-166">Pass a value of `true` for *force* to remove all replication objects at the Distributor without first verifying that all local publication databases have been disabled, and distribution databases have been uninstalled.</span></span>  
  
###  <a name="examples-rmo"></a><a name="PShellExample"></a> <span data-ttu-id="4d170-167">示例 (RMO)</span><span class="sxs-lookup"><span data-stu-id="4d170-167">Examples (RMO)</span></span>  
 <span data-ttu-id="4d170-168">此示例将删除分发服务器上的发布服务器注册，删除分发数据库并卸载分发服务器。</span><span class="sxs-lookup"><span data-stu-id="4d170-168">This example removes the Publisher registration at the Distributor, drops the distribution database, and uninstalls the Distributor.</span></span>  
  
 [!code-csharp[HowTo#rmo_DropDistPub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_dropdistpub)]  
  
 [!code-vb[HowTo#rmo_vb_DropDistPub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_dropdistpub)]  
  
 <span data-ttu-id="4d170-169">此示例在没有首先禁用本地发布数据库或删除分发数据库的情况下，卸载分发服务器。</span><span class="sxs-lookup"><span data-stu-id="4d170-169">This example uninstalls the Distributor without first disabling local publication databases or dropping the distribution database.</span></span>  
  
 [!code-csharp[HowTo#rmo_DropDistPubForce](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_dropdistpubforce)]  
  
 [!code-vb[HowTo#rmo_vb_DropDistPubForce](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_dropdistpubforce)]  
  
## <a name="see-also"></a><span data-ttu-id="4d170-170">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4d170-170">See Also</span></span>  
 <span data-ttu-id="4d170-171">[Replication Management Objects Concepts](concepts/replication-management-objects-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="4d170-171">[Replication Management Objects Concepts](concepts/replication-management-objects-concepts.md) </span></span>  
 [<span data-ttu-id="4d170-172">Replication System Stored Procedures Concepts</span><span class="sxs-lookup"><span data-stu-id="4d170-172">Replication System Stored Procedures Concepts</span></span>](concepts/replication-system-stored-procedures-concepts.md)  
  
  
