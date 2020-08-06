---
title: 事务复制的可更新订阅 | Microsoft Docs
ms.custom: ''
ms.date: 03/31/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- transactional replication, updatable subscriptions
- updatable subscriptions, about updatable subscriptions
- queued updating subscriptions [SQL Server replication]
- immediate updating subscriptions
- subscriptions [SQL Server replication], updatable
- updatable subscriptions
ms.assetid: 8eec95cb-3a11-436e-bcee-bdcd05aa5c5a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e0b739ffe34a14519ff5290c406805ff7715edce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591234"
---
# <a name="updatable-subscriptions-for-transactional-replication"></a><span data-ttu-id="85fdf-102">Updatable Subscriptions for Transactional Replication</span><span class="sxs-lookup"><span data-stu-id="85fdf-102">Updatable Subscriptions for Transactional Replication</span></span>

<span data-ttu-id="85fdf-103">**适用于：** SQL Server 2008 (和更高版本) </span><span class="sxs-lookup"><span data-stu-id="85fdf-103">**Applies to:** SQL Server 2008 (and later)</span></span>

    
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
<span data-ttu-id="85fdf-104">在 SQL Server 2014 中，事务复制通过可更新订阅和对等复制来支持订阅服务器上的更新。</span><span class="sxs-lookup"><span data-stu-id="85fdf-104">In SQL Server 2014, transactional replication supports updates at Subscribers through updatable subscriptions and peer-to-peer replication.</span></span> <span data-ttu-id="85fdf-105">下面介绍两种可更新订阅：</span><span class="sxs-lookup"><span data-stu-id="85fdf-105">The following are the two types of updatable subscriptions:</span></span>  
  
-   <span data-ttu-id="85fdf-106">立即更新。</span><span class="sxs-lookup"><span data-stu-id="85fdf-106">Immediate updating.</span></span> <span data-ttu-id="85fdf-107">必须连接发布服务器和订阅服务器才能在订阅服务器中更新数据。</span><span class="sxs-lookup"><span data-stu-id="85fdf-107">The Publisher and Subscriber must be connected to update data at the Subscriber.</span></span>  
  
-   <span data-ttu-id="85fdf-108">排队更新。不必连接发布服务器和订阅服务器即可在订阅服务器中更新数据。</span><span class="sxs-lookup"><span data-stu-id="85fdf-108">Queued updating The Publisher and Subscriber do not have to be connected to update data at the Subscriber.</span></span> <span data-ttu-id="85fdf-109">可以在订阅服务器或发布服务器脱机时进行更新。</span><span class="sxs-lookup"><span data-stu-id="85fdf-109">Updates can be made while the Subscriber or Publisher is offline.</span></span>  
  
 <span data-ttu-id="85fdf-110">在订阅服务器中更新数据时，首先将数据传播到发布服务器，然后再传播到其他订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="85fdf-110">When data is updated at a Subscriber, it is first propagated to the Publisher and then propagated to other Subscribers.</span></span> <span data-ttu-id="85fdf-111">如果使用立即更新，将使用两阶段提交协议立即传播更改。</span><span class="sxs-lookup"><span data-stu-id="85fdf-111">If immediate updating is used, the changes are propagated immediately using the two-phase commit protocol.</span></span> <span data-ttu-id="85fdf-112">如果使用排队更新，更改将存储在队列中；当网络连接可用时，再在发布服务器中异步应用排队事务。</span><span class="sxs-lookup"><span data-stu-id="85fdf-112">If queued updating is used, the changes are stored in a queue; the queued transactions are then applied asynchronously at the Publisher whenever network connectivity is available.</span></span> <span data-ttu-id="85fdf-113">由于更新异步传播至发布服务器，所以发布服务器或另一台订阅服务器有可能更新同一数据，而在应用更新时会发生冲突。</span><span class="sxs-lookup"><span data-stu-id="85fdf-113">Because the updates are propagated asynchronously to the Publisher, the same data may have been updated by the Publisher or by another Subscriber and conflicts can occur when applying the updates.</span></span> <span data-ttu-id="85fdf-114">将根据创建发布时设置的冲突解决策略检测和解决冲突。</span><span class="sxs-lookup"><span data-stu-id="85fdf-114">Conflicts are detected and resolved according to a conflict resolution policy that is set when creating the publication.</span></span>  
  
 <span data-ttu-id="85fdf-115">如果在新建发布向导中创建具有可更新订阅的事务发布，将同时启用立即更新和排队更新。</span><span class="sxs-lookup"><span data-stu-id="85fdf-115">If you create a transactional publication with updatable subscriptions in the New Publication Wizard, both immediate updating and queued updating are enabled.</span></span> <span data-ttu-id="85fdf-116">如果使用存储过程创建发布，则可以启用一个或两个选项。</span><span class="sxs-lookup"><span data-stu-id="85fdf-116">If you create a publication with stored procedures, you can enable one or both options.</span></span> <span data-ttu-id="85fdf-117">创建发布的订阅时，可以指定要使用的更新模式。</span><span class="sxs-lookup"><span data-stu-id="85fdf-117">When you create a subscription to the publication, you specify which update mode to use.</span></span> <span data-ttu-id="85fdf-118">如有必要，以后可以在两种更新模式之间切换。</span><span class="sxs-lookup"><span data-stu-id="85fdf-118">You can then switch between update modes if necessary.</span></span> <span data-ttu-id="85fdf-119">有关详细信息，请参阅下面的“在更新模式之间切换”部分。</span><span class="sxs-lookup"><span data-stu-id="85fdf-119">For more information, see the following section "Switching between Update Modes".</span></span>  
  
 <span data-ttu-id="85fdf-120">若要启用事务发布的可更新订阅，请参阅 [Enable Updating Subscriptions for Transactional Publications](../publish/enable-updating-subscriptions-for-transactional-publications.md)。</span><span class="sxs-lookup"><span data-stu-id="85fdf-120">To enable updatable subscriptions for transactional publications, [Enable Updating Subscriptions for Transactional Publications](../publish/enable-updating-subscriptions-for-transactional-publications.md)</span></span>  
  
 <span data-ttu-id="85fdf-121">若要创建事务发布的可更新订阅，请参阅 [Create an Updatable Subscription to a Transactional Publication](../publish/create-an-updatable-subscription-to-a-transactional-publication.md)。</span><span class="sxs-lookup"><span data-stu-id="85fdf-121">To create updatable subscriptions for transactional publications, see [Create an Updatable Subscription to a Transactional Publication](../publish/create-an-updatable-subscription-to-a-transactional-publication.md)</span></span>  
  
## <a name="switching-between-update-modes"></a><span data-ttu-id="85fdf-122">在更新模式之间切换</span><span class="sxs-lookup"><span data-stu-id="85fdf-122">Switching Between Update Modes</span></span>  
 <span data-ttu-id="85fdf-123">使用可更新订阅时，可以指定订阅使用一种更新模式，然后在应用程序需要时再切换到另一种更新模式。</span><span class="sxs-lookup"><span data-stu-id="85fdf-123">When using updatable subscriptions you can specify that a subscription should use one update mode and then switch to the other if the application requires it.</span></span> <span data-ttu-id="85fdf-124">例如，可以指定订阅使用立即更新，但如果因系统故障而导致网络连接断开，则切换到排队更新。</span><span class="sxs-lookup"><span data-stu-id="85fdf-124">For example, you can specify that a subscription should use immediate updating, but switch to queued updating if a system failure results in the loss of network connectivity.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="85fdf-125">复制不会自动切换更新模式。</span><span class="sxs-lookup"><span data-stu-id="85fdf-125">Replication does not switch automatically between update modes.</span></span> <span data-ttu-id="85fdf-126">必须通过 SQL Server Management Studio 设置更新模式，否则你的应用程序必须调用 [sp_setreplfailovermode &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-setreplfailovermode-transact-sql) 来切换更新模式。</span><span class="sxs-lookup"><span data-stu-id="85fdf-126">You must set the update mode through SQL Server Management Studio or your application must call [sp_setreplfailovermode &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-setreplfailovermode-transact-sql) to switch between modes.</span></span>  
  
 <span data-ttu-id="85fdf-127">如果从立即更新切换到排队更新，只有在连接了订阅服务器和发布服务器，且队列读取器代理已将队列中所有挂起消息应用到发布服务器后，才能切换回立即更新。</span><span class="sxs-lookup"><span data-stu-id="85fdf-127">If you switch from immediate updating to queued updating, you cannot switch back to immediate updating until the Subscriber and Publisher are connected and the Queue Reader Agent has applied all pending messages in the queue to the Publisher.</span></span>  
  
 <span data-ttu-id="85fdf-128">**切换更新模式**</span><span class="sxs-lookup"><span data-stu-id="85fdf-128">**To switch between update modes**</span></span>  
  
 <span data-ttu-id="85fdf-129">若要切换更新模式，必须为这两种更新模式都启用发布和订阅，然后再根据需要进行切换。</span><span class="sxs-lookup"><span data-stu-id="85fdf-129">To switch between updating modes, you must enable the publication and subscription for both update modes, and then switch between them if necessary.</span></span> <span data-ttu-id="85fdf-130">有关详细信息，请参阅</span><span class="sxs-lookup"><span data-stu-id="85fdf-130">For more information, see</span></span>  
<span data-ttu-id="85fdf-131">[切换可更新事务订阅的更新模式](../administration/switch-between-update-modes-for-an-updatable-transactional-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="85fdf-131">[Switch Between Update Modes for an Updatable Transactional Subscription](../administration/switch-between-update-modes-for-an-updatable-transactional-subscription.md).</span></span>  
  
### <a name="considerations-for-using-updatable-subscriptions"></a><span data-ttu-id="85fdf-132">使用可更新订阅的注意事项</span><span class="sxs-lookup"><span data-stu-id="85fdf-132">Considerations for Using Updatable Subscriptions</span></span>  
  
-   <span data-ttu-id="85fdf-133">为更新订阅或排队更新订阅启用发布后，不能再为发布禁用该选项（即使订阅不需要使用它）。</span><span class="sxs-lookup"><span data-stu-id="85fdf-133">After a publication is enabled for updating subscriptions or queued updating subscriptions, the option cannot be disabled for the publication (although subscriptions do not need to use it).</span></span> <span data-ttu-id="85fdf-134">若要禁用该选项，必须删除发布并创建一个新发布。</span><span class="sxs-lookup"><span data-stu-id="85fdf-134">To disable the option, the publication must be deleted and a new one created.</span></span>  
  
-   <span data-ttu-id="85fdf-135">不支持重新发布数据。</span><span class="sxs-lookup"><span data-stu-id="85fdf-135">Republishing data is not supported.</span></span>  
  
-   <span data-ttu-id="85fdf-136">出于跟踪的目的，复制将在已发布的表中添加 **msrepl_tran_version** 列。</span><span class="sxs-lookup"><span data-stu-id="85fdf-136">Replication adds the **msrepl_tran_version** column to published tables for tracking purposes.</span></span> <span data-ttu-id="85fdf-137">由于添加的这个列，所有 `INSERT` 语句都应包括一个列列表。</span><span class="sxs-lookup"><span data-stu-id="85fdf-137">Because of this additional column, all `INSERT` statements should include a column list.</span></span>  
  
-   <span data-ttu-id="85fdf-138">若要在支持更新订阅的发布中的表上进行架构更改，必须在发布服务器和订阅服务器中停止该表上的所有活动，还必须将挂起的数据更改传播到所有节点，然后才能进行架构更改。</span><span class="sxs-lookup"><span data-stu-id="85fdf-138">To make schema changes on a table in a publication that supports updating subscriptions, all activity on the table must be stopped at the Publisher and Subscribers, and pending data changes must be propagated to all nodes before making any schema changes.</span></span> <span data-ttu-id="85fdf-139">这可以确保未完成的事务不会与挂起的架构更改发生冲突。</span><span class="sxs-lookup"><span data-stu-id="85fdf-139">This ensures that outstanding transactions do not conflict with the pending schema change.</span></span> <span data-ttu-id="85fdf-140">架构更改传播到所有节点后，可以在已发布的表上恢复活动。</span><span class="sxs-lookup"><span data-stu-id="85fdf-140">After the schema changes have propagated to all nodes, activity can resume on the published tables.</span></span> <span data-ttu-id="85fdf-141">有关详细信息，请参阅[停止复制拓扑（复制 Transact-SQL 编程）](../administration/quiesce-a-replication-topology-replication-transact-sql-programming.md)。</span><span class="sxs-lookup"><span data-stu-id="85fdf-141">For more information, see [Quiesce a Replication Topology &#40;Replication Transact-SQL Programming&#41;](../administration/quiesce-a-replication-topology-replication-transact-sql-programming.md).</span></span>  
  
-   <span data-ttu-id="85fdf-142">如果计划切换更新模式，则在初始化订阅后，队列读取器代理必须至少运行一次（默认情况下，队列读取器代理连续运行）。</span><span class="sxs-lookup"><span data-stu-id="85fdf-142">If you plan to switch between update modes, the Queue Reader Agent must run at least once after the subscription has been initialized (by default, the Queue Reader Agent runs continuously).</span></span>  
  
-   <span data-ttu-id="85fdf-143">如果订阅服务器数据库进行了水平分区，且分区中有在订阅服务器上存在而在发布服务器中不存在的行，那么订阅服务器将无法更新这些预先存在的行。</span><span class="sxs-lookup"><span data-stu-id="85fdf-143">If the Subscriber database is partitioned horizontally and there are rows in the partition that exist at the Subscriber, but not at the Publisher, the Subscriber cannot update the preexisting rows.</span></span> <span data-ttu-id="85fdf-144">试图更新这些行将返回错误。</span><span class="sxs-lookup"><span data-stu-id="85fdf-144">Attempting to update these rows returns an error.</span></span> <span data-ttu-id="85fdf-145">应先从表中删除这些行，然后再在发布服务器中添加这些行。</span><span class="sxs-lookup"><span data-stu-id="85fdf-145">The rows should be deleted from the table and then added at the Publisher.</span></span>  
  
### <a name="updates-at-the-subscriber"></a><span data-ttu-id="85fdf-146">订阅服务器中的更新</span><span class="sxs-lookup"><span data-stu-id="85fdf-146">Updates at the Subscriber</span></span>  
  
-   <span data-ttu-id="85fdf-147">即使订阅过期或处于不活动状态，订阅服务器中的更新仍会传播到发布服务器中。</span><span class="sxs-lookup"><span data-stu-id="85fdf-147">Updates at the Subscriber are propagated to the Publisher even if a subscription is expired or is inactive.</span></span> <span data-ttu-id="85fdf-148">请确保删除或重新初始化此类订阅。</span><span class="sxs-lookup"><span data-stu-id="85fdf-148">Ensure that any such subscriptions are either dropped or reinitialized.</span></span>  
  
-   <span data-ttu-id="85fdf-149">如果使用 `TIMESTAMP` 或 `IDENTITY` 列，且将这些列按其基本数据类型进行复制，则不应在订阅服务器中更新这些列中的值。</span><span class="sxs-lookup"><span data-stu-id="85fdf-149">If `TIMESTAMP` or `IDENTITY` columns are used, and they are replicated as their base data types, values in these columns should not be updated at the Subscriber.</span></span>  
  
-   <span data-ttu-id="85fdf-150">订阅服务器不能更新或插入 `text`、`ntext` 或 `image` 值，因为不能在复制更改跟踪触发器中从插入或删除的表中读取数据。</span><span class="sxs-lookup"><span data-stu-id="85fdf-150">Subscribers cannot update or insert `text`, `ntext` or `image` values because it is not possible to read from the inserted or deleted tables inside the replication change-tracking triggers.</span></span> <span data-ttu-id="85fdf-151">同样，订阅服务器不能使用 `WRITETEXT` 或 `UPDATETEXT` 更新或插入 `text` 或 `image` 值，因为这些数据会被发布服务器覆盖。</span><span class="sxs-lookup"><span data-stu-id="85fdf-151">Similarly, Subscribers cannot update or insert `text` or `image` values using `WRITETEXT` or `UPDATETEXT` because the data is overwritten by the Publisher.</span></span> <span data-ttu-id="85fdf-152">但可以将 `text` 和 `image` 列分区到单独的表中，并在一个事务中修改这两个表。</span><span class="sxs-lookup"><span data-stu-id="85fdf-152">Instead, you could partition the `text` and `image` columns into a separate table and modify the two tables within a transaction.</span></span>  
  
     <span data-ttu-id="85fdf-153">若要更新订阅服务器上的大型对象，请分别使用数据类型 `varchar(max)`、`nvarchar(max)`、`varbinary(max)`，而不要使用 `text`、`ntext` 和 `image` 数据类型。</span><span class="sxs-lookup"><span data-stu-id="85fdf-153">To update large objects at a Subscriber, use the data types `varchar(max)`, `nvarchar(max)`, `varbinary(max)` instead of `text`, `ntext`, and `image` data types, respectively.</span></span>  
  
-   <span data-ttu-id="85fdf-154">不允许对唯一键（包括主键）进行生成重复项的更新（例如，格式为 `UPDATE <column> SET <column> =<column>+1` 的更新），这些更新将因为违反唯一性而被拒绝。</span><span class="sxs-lookup"><span data-stu-id="85fdf-154">Updates to unique keys (including primary keys) that generate duplicates (for example, an update of the form `UPDATE <column> SET <column> =<column>+1` are not allowed and will be rejected because of a uniqueness violation.</span></span> <span data-ttu-id="85fdf-155">这是因为复制会将订阅服务器中所做的设置更新作为单独的 `UPDATE` 语句为每个受影响的行进行传播。</span><span class="sxs-lookup"><span data-stu-id="85fdf-155">This is because set updates made at the Subscriber are propagated by replication as individual `UPDATE` statements for each row affected.</span></span>  
  
-   <span data-ttu-id="85fdf-156">如果订阅服务器数据库进行了水平分区，且分区中有在订阅服务器上存在而在发布服务器中不存在的行，那么订阅服务器将无法更新这些预先存在的行。</span><span class="sxs-lookup"><span data-stu-id="85fdf-156">If the Subscriber database is partitioned horizontally and there are rows in the partition that exist at the Subscriber but not at the Publisher, the Subscriber cannot update the pre-existing rows.</span></span> <span data-ttu-id="85fdf-157">试图更新这些行将返回错误。</span><span class="sxs-lookup"><span data-stu-id="85fdf-157">Attempting to update these rows returns an error.</span></span> <span data-ttu-id="85fdf-158">应当先从表中删除这些行，然后再插入这些行。</span><span class="sxs-lookup"><span data-stu-id="85fdf-158">The rows should be deleted from the table and inserted again.</span></span>  
  
### <a name="user-defined-triggers"></a><span data-ttu-id="85fdf-159">用户定义的触发器</span><span class="sxs-lookup"><span data-stu-id="85fdf-159">User-defined Triggers</span></span>  
  
-   <span data-ttu-id="85fdf-160">如果应用程序需要在订阅服务器中使用触发器，则应在发布服务器和订阅服务器中使用 `NOT FOR REPLICATION` 选项来定义触发器。</span><span class="sxs-lookup"><span data-stu-id="85fdf-160">If the application requires triggers at the Subscriber, the triggers should be defined with the `NOT FOR REPLICATION` option at the Publisher and Subscriber.</span></span> <span data-ttu-id="85fdf-161">这可以确保触发器只在原始数据更改时激发，而在复制更改时不激发。</span><span class="sxs-lookup"><span data-stu-id="85fdf-161">This ensures that triggers fire only for the original data change, but not when that change is replicated.</span></span>  
  
     <span data-ttu-id="85fdf-162">确保复制触发器更新表时不会激发用户定义的触发器。</span><span class="sxs-lookup"><span data-stu-id="85fdf-162">Ensure that the user-defined trigger does not fire when the replication trigger updates the table.</span></span> <span data-ttu-id="85fdf-163">这可以通过在用户定义的触发器的正文中调用 `sp_check_for_sync_trigger` 过程来实现。</span><span class="sxs-lookup"><span data-stu-id="85fdf-163">This is accomplished by calling the procedure `sp_check_for_sync_trigger` in the body of the user-defined trigger.</span></span> <span data-ttu-id="85fdf-164">有关详细信息，请参阅 [sp_check_for_sync_trigger &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-check-for-sync-trigger-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="85fdf-164">For more information, see [sp_check_for_sync_trigger &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-check-for-sync-trigger-transact-sql).</span></span>  
  
### <a name="immediate-updating"></a><span data-ttu-id="85fdf-165">立即更新</span><span class="sxs-lookup"><span data-stu-id="85fdf-165">Immediate Updating</span></span>  
  
-   <span data-ttu-id="85fdf-166">对于立即更新订阅，订阅服务器中的更改是使用 Microsoft 分布式事务处理协调器 (MS DTC) 传播到订阅服务器上并进行应用的。</span><span class="sxs-lookup"><span data-stu-id="85fdf-166">For immediate updating subscriptions, changes at the Subscriber are propagated to the Publisher and applied using Microsoft Distributed Transaction Coordinator (MS DTC).</span></span> <span data-ttu-id="85fdf-167">请确保发布服务器和订阅服务器中安装并配置了 MS DTC。</span><span class="sxs-lookup"><span data-stu-id="85fdf-167">Ensure that MS DTC is installed and configured at the Publisher and Subscriber.</span></span> <span data-ttu-id="85fdf-168">有关详细信息，请参阅 Windows 文档。</span><span class="sxs-lookup"><span data-stu-id="85fdf-168">For more information, see the Windows documentation.</span></span>  
  
-   <span data-ttu-id="85fdf-169">立即更新订阅使用的触发器需要连接到发布服务器才能复制更改。</span><span class="sxs-lookup"><span data-stu-id="85fdf-169">The triggers used by immediate updating subscriptions require a connection to the Publisher to replicate changes.</span></span>  
  
-   <span data-ttu-id="85fdf-170">如果发布允许立即更新订阅，且发布中的项目具有列筛选器，则无法筛选出无默认值的不可为 Null 的列。</span><span class="sxs-lookup"><span data-stu-id="85fdf-170">If the publication allows immediate updating subscriptions and an article in the publication has a column filter, you cannot filter out non-nullable columns without defaults.</span></span>  
  
### <a name="queued-updating"></a><span data-ttu-id="85fdf-171">排队更新</span><span class="sxs-lookup"><span data-stu-id="85fdf-171">Queued Updating</span></span>  
  
-   <span data-ttu-id="85fdf-172">合并发布中包含的表也不能作为允许排队更新订阅的事务发布的一部分进行发布。</span><span class="sxs-lookup"><span data-stu-id="85fdf-172">Tables included in a merge publication cannot also be published as part of a transactional publication that allows queued updating subscriptions.</span></span>  
  
-   <span data-ttu-id="85fdf-173">使用排队更新时，建议不要对主键列进行更新，因为主键被用作所有查询的记录定位器。</span><span class="sxs-lookup"><span data-stu-id="85fdf-173">Updates made to primary key columns are not recommended when using queued updating because the primary key is used as a record locator for all queries.</span></span> <span data-ttu-id="85fdf-174">当冲突解决策略设置为“订阅服务器入选”时，更新主键时应小心。</span><span class="sxs-lookup"><span data-stu-id="85fdf-174">When the conflict resolution policy is set to Subscriber Wins, updates to primary keys should be made with caution.</span></span> <span data-ttu-id="85fdf-175">如果同时在发布服务器和订阅服务器中更新主键，将获得具有不同主键的两行。</span><span class="sxs-lookup"><span data-stu-id="85fdf-175">If updates to the primary key are made at both the Publisher and at the Subscriber, the result will be two rows with different primary keys.</span></span>  
  
-   <span data-ttu-id="85fdf-176">对于 `SQL_VARIANT` 数据类型的列：在订阅服务器中插入或更新数据时，队列读取器代理在将数据从订阅服务器复制到队列时，将按下列方式映射数据：</span><span class="sxs-lookup"><span data-stu-id="85fdf-176">For columns of data type `SQL_VARIANT`: when data is inserted or updated at the Subscriber, it is mapped in the following way by the Queue Reader Agent when it is copied from the Subscriber to the queue:</span></span>  
  
    -   <span data-ttu-id="85fdf-177">将 `BIGINT`、`DECIMAL`、`NUMERIC`、`MONEY` 和 `SMALLMONEY` 映射到 `NUMERIC`。</span><span class="sxs-lookup"><span data-stu-id="85fdf-177">`BIGINT`, `DECIMAL`, `NUMERIC`, `MONEY`, and `SMALLMONEY` are mapped to `NUMERIC`.</span></span>  
  
    -   <span data-ttu-id="85fdf-178">将 `BINARY` 和 `VARBINARY` 映射到 `VARBINARY` 数据。</span><span class="sxs-lookup"><span data-stu-id="85fdf-178">`BINARY` and `VARBINARY` are mapped to `VARBINARY` data.</span></span>  
  
### <a name="conflict-detection-and-resolution"></a><span data-ttu-id="85fdf-179">冲突检测和解决</span><span class="sxs-lookup"><span data-stu-id="85fdf-179">Conflict Detection and Resolution</span></span>  
  
-   <span data-ttu-id="85fdf-180">对于“订阅服务器入选”冲突策略：不支持对主键列的更新应用冲突解决。</span><span class="sxs-lookup"><span data-stu-id="85fdf-180">For the Subscriber Wins conflict policy: conflict resolution is not supported for updates to primary key columns.</span></span>  
  
-   <span data-ttu-id="85fdf-181">复制并不会解决由于外键约束失败而引起的冲突。</span><span class="sxs-lookup"><span data-stu-id="85fdf-181">Conflicts due to foreign key constraint failures are not resolved by replication:</span></span>  
  
    -   <span data-ttu-id="85fdf-182">如果出现意外冲突，而数据又分区良好（订阅服务器不更新相同的列），则可以在发布服务器和订阅服务器中使用外键约束。</span><span class="sxs-lookup"><span data-stu-id="85fdf-182">If conflicts are not expected and data is well partitioned (Subscribers do not update the same rows), you can use foreign key constraints on the Publisher and Subscribers.</span></span>  
  
    -   <span data-ttu-id="85fdf-183">如果出现预料中的冲突：如果使用“订阅服务器入选”冲突解决，则不应在发布服务器或订阅服务器中使用外键约束；如果使用“发布服务器入选”冲突解决，则不应在订阅服务器中使用外键约束。</span><span class="sxs-lookup"><span data-stu-id="85fdf-183">If conflicts are expected: you should not use foreign key constraints at the Publisher or Subscriber if you use "Subscriber wins" conflict resolution; you should not use foreign key constraints at the Subscriber if you use "Publisher wins" conflict resolution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85fdf-184">另请参阅</span><span class="sxs-lookup"><span data-stu-id="85fdf-184">See Also</span></span>  
 <span data-ttu-id="85fdf-185">[Peer-to-Peer Transactional Replication](peer-to-peer-transactional-replication.md) </span><span class="sxs-lookup"><span data-stu-id="85fdf-185">[Peer-to-Peer Transactional Replication](peer-to-peer-transactional-replication.md) </span></span>  
 <span data-ttu-id="85fdf-186">[事务复制](transactional-replication.md) </span><span class="sxs-lookup"><span data-stu-id="85fdf-186">[Transactional Replication](transactional-replication.md) </span></span>  
 <span data-ttu-id="85fdf-187">[发布数据和数据库对象](../publish/publish-data-and-database-objects.md) </span><span class="sxs-lookup"><span data-stu-id="85fdf-187">[Publish Data and Database Objects](../publish/publish-data-and-database-objects.md) </span></span>  
 [<span data-ttu-id="85fdf-188">订阅发布</span><span class="sxs-lookup"><span data-stu-id="85fdf-188">Subscribe to Publications</span></span>](../subscribe-to-publications.md)  
  
  
