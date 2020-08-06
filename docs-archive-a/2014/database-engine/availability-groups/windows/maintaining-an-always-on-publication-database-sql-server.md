---
title: 维护 AlwaysOn 发布数据库 (SQL Server) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], interoperability
- replication [SQL Server], AlwaysOn Availability Groups
ms.assetid: 55b345fe-2eb9-4b04-a900-63d858eec360
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e8f36d29049140b6e5bbdfc1a4e716d41a766a06
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585963"
---
# <a name="maintaining-an-alwayson-publication-database-sql-server"></a><span data-ttu-id="48a21-102">维护 AlwaysOn 发布数据库 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="48a21-102">Maintaining an AlwaysOn Publication Database (SQL Server)</span></span>
  <span data-ttu-id="48a21-103">本主题讨论了在使用 AlwaysOn 可用性组时维护发布数据库的特殊注意事项。</span><span class="sxs-lookup"><span data-stu-id="48a21-103">This topic discusses special considerations for maintaining a publication database when you use AlwaysOn availability groups.</span></span>  
  
 
  
##  <a name="maintaining-a-published-database-in-an-availability-group"></a><a name="MaintainPublDb"></a><span data-ttu-id="48a21-104">在可用性组中维护已发布的数据库</span><span class="sxs-lookup"><span data-stu-id="48a21-104">Maintaining a Published Database in an Availability Group</span></span>  
 <span data-ttu-id="48a21-105">维护 AlwaysOn 发布数据库与维护标准的发布数据库基本相同，但需要注意以下事项：</span><span class="sxs-lookup"><span data-stu-id="48a21-105">Maintaining an AlwaysOn publication database is basically the same as maintaining a standard publication database, with the following considerations:</span></span>  
  
-   <span data-ttu-id="48a21-106">必须在主副本主机上进行管理。</span><span class="sxs-lookup"><span data-stu-id="48a21-106">Administration must occur at the primary replica host.</span></span> <span data-ttu-id="48a21-107">在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]中，发布显示在主副本主机以及可读辅助副本的 **“本地发布”** 文件夹下。</span><span class="sxs-lookup"><span data-stu-id="48a21-107">In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], publications appear under the **Local Publications** folder for the primary replica host and also for readable secondary replicas.</span></span> <span data-ttu-id="48a21-108">在故障转移后，如果无法读取已提升为主副本的辅助副本，则您可能必须手动刷新 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] 以反映更改。</span><span class="sxs-lookup"><span data-stu-id="48a21-108">After failover, you might have to manually refresh [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] for the change to be reflected if the secondary that was promoted to primary was not readable.</span></span>  
  
-   <span data-ttu-id="48a21-109">复制监视器将始终在原始发布服务器下显示发布信息。</span><span class="sxs-lookup"><span data-stu-id="48a21-109">Replication Monitor always displays publication information under the original publisher.</span></span> <span data-ttu-id="48a21-110">但是，通过将原始发布服务器添加为服务器，可以使用复制监视器从任意副本查看此信息。</span><span class="sxs-lookup"><span data-stu-id="48a21-110">However, this information can be viewed in Replication Monitor from any replica by adding the original publisher as a server.</span></span>  
  
-   <span data-ttu-id="48a21-111">当使用存储过程或复制管理对象 (RMO) 在当前主副本上管理复制时，对于需要指定发布服务器名称的情况，您必须指定已经启用了数据库复制的实例（原始发布服务器）的名称。</span><span class="sxs-lookup"><span data-stu-id="48a21-111">When using stored procedures or Replication Management Objects (RMO) to administer replication at the current primary, for cases in which you specify the Publisher name, you must specify the name of the instance on which the database was enabled for replication (the original publisher).</span></span> <span data-ttu-id="48a21-112">若要确定相应的名称，请使用 `PUBLISHINGSERVERNAME` 函数。</span><span class="sxs-lookup"><span data-stu-id="48a21-112">To determine the appropriate name, use the `PUBLISHINGSERVERNAME` function.</span></span> <span data-ttu-id="48a21-113">当发布数据库联接一个可用性组时，存储在辅助数据库副本中的复制元数据将与主副本上的相同。</span><span class="sxs-lookup"><span data-stu-id="48a21-113">When a publishing database joins an availability group, the replication metadata stored in the secondary database replicas is identical to that at the primary.</span></span> <span data-ttu-id="48a21-114">因此，对于主副本上已启用复制的发布数据库而言，辅助副本上的系统表中存储的发布服务器实例名称将是主副本的名称，而不是辅助副本的名称。</span><span class="sxs-lookup"><span data-stu-id="48a21-114">Consequently, for publication databases enabled for replication at the primary, the publisher instance name stored in system tables at the secondary is the name of the primary, not the secondary.</span></span> <span data-ttu-id="48a21-115">如果将发布数据库故障转移到辅助副本，则这种情况会影响复制的配置和维护。</span><span class="sxs-lookup"><span data-stu-id="48a21-115">This affects replication configuration and maintenance if the publication database fails over to a secondary.</span></span> <span data-ttu-id="48a21-116">例如，如果你要在故障转移后在辅助副本上使用存储过程配置复制，并且你希望对在不同副本上启用的发布数据库的请求订阅，则必须将原始发布服务器的名称（而非当前发布服务器的名称）指定为 *@publisher* 或的参数 `sp_addpullsubscription` `sp_addmergepulllsubscription` 。</span><span class="sxs-lookup"><span data-stu-id="48a21-116">For example, if you are configuring replication with stored procedures at a secondary after failover, and you want a pull subscription to a publication database that was enabled at a different replica, you must specify the name of the original publisher instead of the current publisher as the *@publisher* parameter of `sp_addpullsubscription` or `sp_addmergepulllsubscription`.</span></span> <span data-ttu-id="48a21-117">但是，如果您在故障转移之后启用一个发布数据库，则存储在系统表中的发布服务器实例名称将为当前主副本主机的名称。</span><span class="sxs-lookup"><span data-stu-id="48a21-117">However, if you enable a publication database after failover, the publisher instance name stored in the system tables is the name of the current primary host.</span></span> <span data-ttu-id="48a21-118">在这种情况下，将使用参数的当前主副本的主机名 *@publisher* 。</span><span class="sxs-lookup"><span data-stu-id="48a21-118">In this case, you would use the host name of the current primary replica for the *@publisher* parameter.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="48a21-119">对于某些过程（如 `sp_addpublication` ）， *@publisher* 只有不是的实例的发布服务器才支持参数 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ; 在这种情况下，该参数与 AlwaysOn 无关 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="48a21-119">For some procedures, such as `sp_addpublication`, the *@publisher* parameter is supported only for publishers that are not instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]; in these cases, it is not relevant for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] AlwaysOn.</span></span>  
  
-   <span data-ttu-id="48a21-120">若要在故障转移后在 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] 中同步订阅，应将来自订阅服务器的请求订阅与来自活动发布服务器的推送订阅进行同步。</span><span class="sxs-lookup"><span data-stu-id="48a21-120">To synchronize a subscription in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] after a failover, synchronize pull subscriptions from the subscriber and synchronize push subscriptions from the active publisher.</span></span>  
  
##  <a name="removing-a-published-database-from-an-availability-group"></a><a name="RemovePublDb"></a> <span data-ttu-id="48a21-121">从可用性组中删除已发布的数据库</span><span class="sxs-lookup"><span data-stu-id="48a21-121">Removing a Published Database from an Availability Group</span></span>  
 <span data-ttu-id="48a21-122">如果从可用性组中删除了已发布的数据库，或者删除了包含已发布的成员数据库的可用性组，则应考虑以下问题。</span><span class="sxs-lookup"><span data-stu-id="48a21-122">Consider the following issues if a published database is removed from an availability group, or if an availability group that has a published member database is dropped.</span></span>  
  
-   <span data-ttu-id="48a21-123">如果从可用性组主要副本中删除原始发布服务器上的发布数据库，则必须 `sp_redirect_publisher` 在不指定参数值的情况下运行， *@redirected_publisher* 以便删除发布服务器/数据库对的重定向。</span><span class="sxs-lookup"><span data-stu-id="48a21-123">If the publication database at the original publisher is removed from an availability group primary replica, you must run `sp_redirect_publisher` without specifying a value for the *@redirected_publisher* parameter in order to remove the redirection for the publisher/database pair.</span></span>  
  
    ```  
    EXEC sys.sp_redirect_publisher   
        @original_publisher = 'MyPublisher',  
        @published_database = 'MyPublishedDB';  
    ```  
  
     <span data-ttu-id="48a21-124">该数据库将在主副本上处于“正在恢复”状态，且必须还原。</span><span class="sxs-lookup"><span data-stu-id="48a21-124">The database will be left in the recovering state at the primary and must be restored.</span></span> <span data-ttu-id="48a21-125">在执行还原操作之后，针对原始发布服务器的复制工作应保持不变。</span><span class="sxs-lookup"><span data-stu-id="48a21-125">Once you do this, replication should work unchanged against the original Publisher.</span></span>  
  
-   <span data-ttu-id="48a21-126">如果发布数据库从原始发布服务器故障转移到某个副本，并且从可用性组主副本中删除了该数据库，则使用存储过程 `sp_redirect_publisher` 将原始发布服务器显式重定向到新的发布服务器。</span><span class="sxs-lookup"><span data-stu-id="48a21-126">If the publication database fails over from the original publisher to a replica and the database is removed from the availability group primary replica, use the stored procedure `sp_redirect_publisher` to explicitly redirect the original publisher to the new publisher.</span></span> <span data-ttu-id="48a21-127">该数据库将处于“正在恢复”状态，且必须还原。</span><span class="sxs-lookup"><span data-stu-id="48a21-127">The database will be left in the recovering state and must be restored.</span></span> <span data-ttu-id="48a21-128">在执行还原操作之后，复制应会继续按照其在可用性组下的方式工作。</span><span class="sxs-lookup"><span data-stu-id="48a21-128">Once you do this, replication should continue to work as it did under the availability group.</span></span>  
  
    ```  
    EXEC sys.sp_redirect_publisher   
        @original_publisher = 'MyPublisher',  
        @published_database = 'MyPublishedDB',  
        @redirected_publisher = 'MyNewPublisher';  
    ```  
  
     <span data-ttu-id="48a21-129">不要从分发服务器中删除原始发布服务器的远程服务器，即使无法再访问该服务器也是如此。</span><span class="sxs-lookup"><span data-stu-id="48a21-129">Do not remove the remote server for the original publisher from the distributor, even if the server can no longer be accessed.</span></span> <span data-ttu-id="48a21-130">在分发服务器上需要原始发布服务器的服务器元数据来满足发布元数据查询。</span><span class="sxs-lookup"><span data-stu-id="48a21-130">The server metadata for the original publisher is needed at the distributor to satisfy publication metadata queries.</span></span>  
  
-   <span data-ttu-id="48a21-131">如果删除了整个可用性组，则有关成员复制数据库的行为与从可用性组中删除某个已发布的数据库时的行为相同。</span><span class="sxs-lookup"><span data-stu-id="48a21-131">If a complete availability group is removed, the behavior with regard to a member replicated database is the same as when a published database is removed from an availability group.</span></span> <span data-ttu-id="48a21-132">在已经还原数据库并且已经修改重定向之后，即可从最后的主副本中恢复复制。</span><span class="sxs-lookup"><span data-stu-id="48a21-132">Replication can be resumed from the last primary as soon as the database has been restored and the redirection has been modified.</span></span> <span data-ttu-id="48a21-133">如果在数据库的原始发布服务器上还原数据库，则应删除重定向。</span><span class="sxs-lookup"><span data-stu-id="48a21-133">If the database is restored at its original publisher, redirection should be removed.</span></span> <span data-ttu-id="48a21-134">如果在其他主机上还原数据库，则应将重定向显式定向到新的主机。</span><span class="sxs-lookup"><span data-stu-id="48a21-134">If the database is restored at a different host, redirection should be explicitly directed to the new host.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="48a21-135">在删除包含已发布的成员数据库的可用性组时，或在删除可用性组中的已发布的数据库时，已发布的数据库的所有副本都将处于“正在恢复”状态。</span><span class="sxs-lookup"><span data-stu-id="48a21-135">When an availability group is removed that has published member databases, or a published database is removed from an availability group, all copies of the published databases will be left in the recovering state.</span></span> <span data-ttu-id="48a21-136">这些副本在还原之后都将显示为已发布的数据库。</span><span class="sxs-lookup"><span data-stu-id="48a21-136">If restored, each will appear as a published database.</span></span> <span data-ttu-id="48a21-137">只应与发布元数据一起保留一份副本。</span><span class="sxs-lookup"><span data-stu-id="48a21-137">Only one copy should be retained with publication metadata.</span></span> <span data-ttu-id="48a21-138">若要对已发布的数据库副本禁用复制，首先应删除该数据库中的所有订阅和发布。</span><span class="sxs-lookup"><span data-stu-id="48a21-138">To disable replication for a published database copy, first remove all subscriptions and publications from the database.</span></span>  
  
     <span data-ttu-id="48a21-139">运行 `sp_dropsubscription` 以删除发布订阅。</span><span class="sxs-lookup"><span data-stu-id="48a21-139">Run `sp_dropsubscription` to remove publication subscriptions.</span></span> <span data-ttu-id="48a21-140">请确保将参数设置 *@ignore_distributributor* 为1，以便为分发服务器上的活动发布数据库保留元数据。</span><span class="sxs-lookup"><span data-stu-id="48a21-140">Make sure to set the parameter *@ignore_distributributor* to 1 to preserve the metadata for the active publishing database at the distributor.</span></span>  
  
    ```  
    USE MyDBName;  
    GO  
  
    EXEC sys.sp_dropsubscription   
        @subscriber = 'MySubscriber',  
        @publication = 'MyPublication',  
        @article = 'all',  
        @ignore_distributor = 1;  
    ```  
  
     <span data-ttu-id="48a21-141">运行 `sp_droppublication` 以删除所有发布。</span><span class="sxs-lookup"><span data-stu-id="48a21-141">Run `sp_droppublication` to remove all publications.</span></span> <span data-ttu-id="48a21-142">同样，将参数设置 *@ignore_distributor* 为1，以便为分发服务器上的活动发布数据库保留元数据。</span><span class="sxs-lookup"><span data-stu-id="48a21-142">Again, set the parameter *@ignore_distributor* to 1 to preserve the metadata for the active publishing database at the distributor.</span></span>  
  
    ```  
    EXEC sys.sp_droppublication   
        @publication = 'MyPublication',  
        @ignore_distributor = 1;  
    ```  
  
     <span data-ttu-id="48a21-143">运行 `sp_replicationdboption` 以禁用该数据库的复制。</span><span class="sxs-lookup"><span data-stu-id="48a21-143">Run `sp_replicationdboption` to disable replication for the database.</span></span>  
  
    ```  
    EXEC sys.sp_replicationdboption  
        @dbname = 'MyDBName',  
        @optname = 'publish',  
        @value = 'false';  
    ```  
  
     <span data-ttu-id="48a21-144">此时，可保留或删除已发布的数据库的副本。</span><span class="sxs-lookup"><span data-stu-id="48a21-144">At this point, the copy of the published database can be retained or dropped.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="48a21-145">相关任务</span><span class="sxs-lookup"><span data-stu-id="48a21-145">Related Tasks</span></span>  
  
-   [<span data-ttu-id="48a21-146">为 AlwaysOn 可用性组配置复制 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="48a21-146">Configure Replication for AlwaysOn Availability Groups (SQL Server)</span></span>](always-on-availability-groups-sql-server.md)  
  
-   [<span data-ttu-id="48a21-147">复制、更改跟踪、更改数据捕获和 AlwaysOn 可用性组 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="48a21-147">Replication, Change Tracking, Change Data Capture, and AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](replicate-track-change-data-capture-always-on-availability.md)  
  
-   [<span data-ttu-id="48a21-148">复制管理常见问题解答</span><span class="sxs-lookup"><span data-stu-id="48a21-148">Replication Administration FAQ</span></span>](../../../relational-databases/replication/administration/frequently-asked-questions-for-replication-administrators.md)  
  
-   [<span data-ttu-id="48a21-149">复制订阅服务器和 AlwaysOn 可用性组 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="48a21-149">Replication Subscribers and AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](replication-subscribers-and-always-on-availability-groups-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="48a21-150">另请参阅</span><span class="sxs-lookup"><span data-stu-id="48a21-150">See Also</span></span>  
 <span data-ttu-id="48a21-151">[AlwaysOn 可用性组 &#40;SQL Server 的先决条件、限制和建议&#41;](prereqs-restrictions-recommendations-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="48a21-151">[Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md) </span></span>  
 <span data-ttu-id="48a21-152">[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="48a21-152">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="48a21-153">[AlwaysOn 可用性组：互操作性 (SQL Server) ](always-on-availability-groups-interoperability-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="48a21-153">[AlwaysOn Availability Groups: Interoperability (SQL Server)](always-on-availability-groups-interoperability-sql-server.md) </span></span>  
 [<span data-ttu-id="48a21-154">SQL Server 复制</span><span class="sxs-lookup"><span data-stu-id="48a21-154">SQL Server Replication</span></span>](../../../relational-databases/replication/sql-server-replication.md)  
  
  
