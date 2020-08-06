---
title: 订阅过期和停用 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Distributors [SQL Server replication], distribution retention period
- subscriptions [SQL Server replication], expiration
- publications [SQL Server replication], publication retention periods
- expiration [SQL Server replication]
- retention periods [SQL Server replication]
- publication retention periods
- distribution retention period
- subscriptions [SQL Server replication], deactivation
- deactivating subscriptions
ms.assetid: 4d03f5ab-e721-4f56-aebc-60f6a56c1e07
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6d81e8b5c02fcfe5399be9e63c8160036a999547
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693234"
---
# <a name="subscription-expiration-and-deactivation"></a><span data-ttu-id="92174-102">订阅过期和停用</span><span class="sxs-lookup"><span data-stu-id="92174-102">Subscription Expiration and Deactivation</span></span>
  <span data-ttu-id="92174-103">如果在指定的“保持期”  内未同步订阅，订阅可能会停用或过期。</span><span class="sxs-lookup"><span data-stu-id="92174-103">Subscriptions can be deactivated or can expire if they are not synchronized within a specified *retention period*.</span></span> <span data-ttu-id="92174-104">发生什么操作取决于复制的类型和所超过的保持期。</span><span class="sxs-lookup"><span data-stu-id="92174-104">The action that occurs depends on the type of replication and the retention period that is exceeded.</span></span>  
  
 <span data-ttu-id="92174-105">若要设置保持期，请参阅[设置订阅的过期期限](publish/set-the-expiration-period-for-subscriptions.md)、[设置事务发布的分发保持期 &#40;SQL Server Management Studio&#41;](set-distribution-retention-period-for-transactional-publications.md) 以及[配置发布和分发](configure-publishing-and-distribution.md)。</span><span class="sxs-lookup"><span data-stu-id="92174-105">To set retention periods, see [Set the Expiration Period for Subscriptions](publish/set-the-expiration-period-for-subscriptions.md), [Set the Distribution Retention Period for Transactional Publications &#40;SQL Server Management Studio&#41;](set-distribution-retention-period-for-transactional-publications.md), and [Configure Publishing and Distribution](configure-publishing-and-distribution.md).</span></span>  
  
## <a name="transactional-replication"></a><span data-ttu-id="92174-106">事务复制</span><span class="sxs-lookup"><span data-stu-id="92174-106">Transactional Replication</span></span>  
 <span data-ttu-id="92174-107">事务复制使用最大的分发保持期 (**@max_distretention** [Sp_adddistributiondb &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-adddistributiondb-transact-sql)) 的参数和发布保持期 (sp_addpublication **@retention** [transact-sql &#40;](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql)&#41;的参数) ：</span><span class="sxs-lookup"><span data-stu-id="92174-107">Transactional replication uses the maximum distribution retention period (the **@max_distretention** parameter of [sp_adddistributiondb &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-adddistributiondb-transact-sql)) and the publication retention period (the **@retention** parameter of [sp_addpublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql)):</span></span>  
  
-   <span data-ttu-id="92174-108">如果订阅未能在最大分发保持期（默认为 72 小时）内同步，而且分发数据库中还存在尚未传递到订阅服务器的更改，则订阅将会被分发服务器上运行的 **“清除分发”** 作业标记为停用。</span><span class="sxs-lookup"><span data-stu-id="92174-108">If a subscription is not synchronized within the maximum distribution retention period (default of 72 hours) and there are changes in the distribution database that have not been delivered to the Subscriber, the subscription will be marked deactivated by the **Distribution clean up** job that runs on the Distributor.</span></span> <span data-ttu-id="92174-109">必须重新初始化订阅。</span><span class="sxs-lookup"><span data-stu-id="92174-109">The subscription must be reinitialized.</span></span>  
  
-   <span data-ttu-id="92174-110">如果订阅未能在发布保持期（默认为 336 小时）内同步，订阅便会过期，而被发布服务器上运行的 **“过期的订阅清除”** 作业删除。</span><span class="sxs-lookup"><span data-stu-id="92174-110">If a subscription is not synchronized within the publication retention period (default of 336 hours), the subscription will expire and be dropped by the **Expired subscription clean up** job that runs on the Publisher.</span></span> <span data-ttu-id="92174-111">必须重新创建和同步订阅。</span><span class="sxs-lookup"><span data-stu-id="92174-111">The subscription must be recreated and synchronized.</span></span>  
  
     <span data-ttu-id="92174-112">如果推送订阅过期，则会彻底删除该订阅，但是请求订阅则不同。</span><span class="sxs-lookup"><span data-stu-id="92174-112">If a push subscription expires, it is completely removed, but pull subscriptions are not.</span></span> <span data-ttu-id="92174-113">您必须清除订阅服务器上的请求订阅。</span><span class="sxs-lookup"><span data-stu-id="92174-113">You must clean up pull subscriptions at the Subscriber.</span></span> <span data-ttu-id="92174-114">有关详细信息，请参阅 [Delete a Pull Subscription](delete-a-pull-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="92174-114">For more information, see [Delete a Pull Subscription](delete-a-pull-subscription.md).</span></span>  
  
## <a name="merge-replication"></a><span data-ttu-id="92174-115">合并复制</span><span class="sxs-lookup"><span data-stu-id="92174-115">Merge Replication</span></span>  
 <span data-ttu-id="92174-116">合并复制使用发布保持期 (**@retention** **@retention_period_unit** [&#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)) 的 sp_addmergepublication 和参数。</span><span class="sxs-lookup"><span data-stu-id="92174-116">Merge replication uses the publication retention period (the **@retention** and **@retention_period_unit** parameters of [sp_addmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)).</span></span> <span data-ttu-id="92174-117">订阅过期后必须将其重新初始化，因为订阅的元数据已被删除。</span><span class="sxs-lookup"><span data-stu-id="92174-117">When a subscription expires, it must be reinitialized, because metadata for the subscription is removed.</span></span> <span data-ttu-id="92174-118">未重新初始化的订阅将由运行在发布服务器上的 **“过期的订阅清除”** 作业删除。</span><span class="sxs-lookup"><span data-stu-id="92174-118">Subscriptions that are not reinitialized are dropped by the **Expired subscription clean up** job that runs on the Publisher.</span></span> <span data-ttu-id="92174-119">默认情况下，此作业每天运行；它删除在两倍的发布保持期内尚未同步的所有推送订阅。</span><span class="sxs-lookup"><span data-stu-id="92174-119">By default, this job runs daily; it removes all push subscriptions that have not synchronized for double the length of the publication retention period.</span></span> <span data-ttu-id="92174-120">例如：</span><span class="sxs-lookup"><span data-stu-id="92174-120">For example:</span></span>  
  
-   <span data-ttu-id="92174-121">如果某发布的保持期为 14 天，则订阅如果在 14 天内尚未同步就会过期。</span><span class="sxs-lookup"><span data-stu-id="92174-121">If a publication has a retention period of 14 days, a subscription can expire if it has not synchronized within 14 days.</span></span>  
  
     <span data-ttu-id="92174-122">如果发布服务器运行的是 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 或更高版本，并且订阅的代理来自 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 或更高版本，则仅当对该订阅分区中的数据进行更改时，该订阅才会过期。</span><span class="sxs-lookup"><span data-stu-id="92174-122">If the Publisher is running [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] or a later version and the agent for the subscription is from [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] or a later version, a subscription only expires if there have been changes to the data in that subscription's partition.</span></span> <span data-ttu-id="92174-123">例如，假定订阅服务器仅接收德国客户的客户数据。</span><span class="sxs-lookup"><span data-stu-id="92174-123">For example, suppose a Subscriber receives customer data only for customers in Germany.</span></span> <span data-ttu-id="92174-124">如果将保持期设置为 14 天，则只有在最近 14 天内更改了德国客户的数据时，该订阅才会在第 14 天过期。</span><span class="sxs-lookup"><span data-stu-id="92174-124">If the retention period is set to 14 days, the subscription expires on day 14 only if there have been changes to the German customer data in the last 14 days.</span></span>  
  
-   <span data-ttu-id="92174-125">在上次同步后的第 14 天到第 27 天，可以重新初始化该订阅。</span><span class="sxs-lookup"><span data-stu-id="92174-125">From 14 days to 27 days after the last synchronization, the subscription can be reinitialized.</span></span>  
  
-   <span data-ttu-id="92174-126">在上次同步后的第 28 天，该订阅由 **“过期的订阅清除”** 作业删除。</span><span class="sxs-lookup"><span data-stu-id="92174-126">At 28 days after the last synchronization, the subscription is dropped by the **Expired subscription clean up** job.</span></span> <span data-ttu-id="92174-127">如果推送订阅过期，则会彻底删除该订阅，但是请求订阅则不同。</span><span class="sxs-lookup"><span data-stu-id="92174-127">If a push subscription expires, it is completely removed, but pull subscriptions are not.</span></span> <span data-ttu-id="92174-128">您必须清除订阅服务器上的请求订阅。</span><span class="sxs-lookup"><span data-stu-id="92174-128">You must clean up pull subscriptions at the Subscriber.</span></span> <span data-ttu-id="92174-129">有关详细信息，请参阅 [Delete a Pull Subscription](delete-a-pull-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="92174-129">For more information, see [Delete a Pull Subscription](delete-a-pull-subscription.md).</span></span>  
  
### <a name="considerations-for-setting-the-publication-retention-period-for-merge-publications"></a><span data-ttu-id="92174-130">设置合并发布的发布保持期时的注意事项</span><span class="sxs-lookup"><span data-stu-id="92174-130">Considerations for Setting the Publication Retention Period for Merge Publications</span></span>  
 <span data-ttu-id="92174-131">在设置合并发布的保持期时，请谨记下列注意事项：</span><span class="sxs-lookup"><span data-stu-id="92174-131">Keep the following considerations in mind when setting the retention period for merge publications:</span></span>  
  
-   <span data-ttu-id="92174-132">合并发布的保持期具有 24 小时的宽限期，以适应处于不同时区中的订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="92174-132">The retention period for merge publications has a 24-hour grace period to accommodate Subscribers in different time zones.</span></span> <span data-ttu-id="92174-133">例如，如果将保持期设置为 1 天，则实际的保持期为 48 小时。</span><span class="sxs-lookup"><span data-stu-id="92174-133">If, for example, you set a retention period of one day, the actual retention period is 48 hours.</span></span>  
  
-   <span data-ttu-id="92174-134">合并复制元数据的清除取决于发布保持期：</span><span class="sxs-lookup"><span data-stu-id="92174-134">Cleanup of merge replication metadata is dependent on the publication retention period:</span></span>  
  
    -   <span data-ttu-id="92174-135">在到达保持期之前，复制无法清除发布数据库和订阅数据库中的元数据。</span><span class="sxs-lookup"><span data-stu-id="92174-135">Replication cannot clean up metadata in the publication and subscription databases until the retention period is reached.</span></span> <span data-ttu-id="92174-136">在为保持期指定较大值时务必谨慎，因为这可能对复制性能产生负面影响。</span><span class="sxs-lookup"><span data-stu-id="92174-136">Use caution in specifying a high value for the retention period, because it can negatively impact replication performance.</span></span> <span data-ttu-id="92174-137">如果能很有把握地预测出所有订阅服务器都将在该时间段内定期同步，则建议使用较低的设置。</span><span class="sxs-lookup"><span data-stu-id="92174-137">It is recommended that you use a lower setting if you can reliably predict that all Subscribers will synchronize regularly within that time period.</span></span>  
  
    -   <span data-ttu-id="92174-138">可以指定订阅永不过期 (值为 0 **@retention**) ，但强烈建议您不要使用此值，因为不能清除元数据。</span><span class="sxs-lookup"><span data-stu-id="92174-138">It is possible to specify that subscriptions never expire (a value of 0 for **@retention**), but it is strongly recommended that you do not use this value, because metadata cannot be cleaned up.</span></span>  
  
-   <span data-ttu-id="92174-139">任何重新发布服务器的保持期都必须设置为等于或小于在原始发布服务器上设置的保持期。</span><span class="sxs-lookup"><span data-stu-id="92174-139">The retention period for any republisher must be set to a value equal to or less than the retention period set at the original Publisher.</span></span> <span data-ttu-id="92174-140">对于所有发布服务器和它们的备用同步伙伴，应该使用相同的发布保持期。</span><span class="sxs-lookup"><span data-stu-id="92174-140">You should also use the same publication retention values for all Publishers and their alternate synchronization partners.</span></span> <span data-ttu-id="92174-141">使用不同的值可能会导致无法收敛。</span><span class="sxs-lookup"><span data-stu-id="92174-141">Using different values may lead to non-convergence.</span></span> <span data-ttu-id="92174-142">如果需要更改发布保持期的值，请重新初始化订阅服务器，以免数据无法收敛。</span><span class="sxs-lookup"><span data-stu-id="92174-142">If you need to change the publication retention value, reinitialize the Subscriber to avoid the non-convergence of data.</span></span>  
  
-   <span data-ttu-id="92174-143">如果在清除之后增大发布保持期，而且订阅尝试与发布服务器（已删除元数据）合并，则订阅将由于增大了保持期值而不会过期。</span><span class="sxs-lookup"><span data-stu-id="92174-143">If, after a clean up, the publication retention period is increased and a subscription tries to merge with the Publisher (which has already deleted the metadata), the subscription will not expire because of the increased retention value.</span></span> <span data-ttu-id="92174-144">但是，发布服务器没有足够的元数据来下载对订阅服务器所做的更改，这会导致无法收敛。</span><span class="sxs-lookup"><span data-stu-id="92174-144">However, the Publisher does not have enough metadata to download changes to the Subscriber, which leads to non-convergence.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92174-145">另请参阅</span><span class="sxs-lookup"><span data-stu-id="92174-145">See Also</span></span>  
 <span data-ttu-id="92174-146">[重新初始化订阅](reinitialize-subscriptions.md) </span><span class="sxs-lookup"><span data-stu-id="92174-146">[Reinitialize Subscriptions](reinitialize-subscriptions.md) </span></span>  
 <span data-ttu-id="92174-147">[复制代理管理](agents/replication-agent-administration.md) </span><span class="sxs-lookup"><span data-stu-id="92174-147">[Replication Agent Administration](agents/replication-agent-administration.md) </span></span>  
 [<span data-ttu-id="92174-148">订阅发布</span><span class="sxs-lookup"><span data-stu-id="92174-148">Subscribe to Publications</span></span>](subscribe-to-publications.md)  
  
  
