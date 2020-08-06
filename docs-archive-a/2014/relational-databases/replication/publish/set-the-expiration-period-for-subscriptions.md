---
title: 设置订阅的过期期限 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [SQL Server replication], expiration
- expiration [SQL Server replication]
- retention periods [SQL Server replication]
- deactivating subscriptions
ms.assetid: 542f0613-5817-42d0-b841-fb2c94010665
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: bc0ecb449af64b88cf3ded032c78c2e399dd4234
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587347"
---
# <a name="set-the-expiration-period-for-subscriptions"></a><span data-ttu-id="567fe-102">设置订阅的过期期限</span><span class="sxs-lookup"><span data-stu-id="567fe-102">Set the Expiration Period for Subscriptions</span></span>
  <span data-ttu-id="567fe-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中设置订阅的过期期限。</span><span class="sxs-lookup"><span data-stu-id="567fe-103">This topic describes how to set the expiration period for subscriptions in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="567fe-104">订阅的过期期限决定了订阅在经过多长时间后过期并被删除。</span><span class="sxs-lookup"><span data-stu-id="567fe-104">The expiration period for subscriptions determines the period of time before a subscription expires and is removed.</span></span> <span data-ttu-id="567fe-105">有关详细信息，请参阅 [Subscription Expiration and Deactivation](../subscription-expiration-and-deactivation.md)。</span><span class="sxs-lookup"><span data-stu-id="567fe-105">For more information, see [Subscription Expiration and Deactivation](../subscription-expiration-and-deactivation.md).</span></span>  
  
 <span data-ttu-id="567fe-106">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="567fe-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="567fe-107">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="567fe-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="567fe-108">建议</span><span class="sxs-lookup"><span data-stu-id="567fe-108">Recommendations</span></span>](#Recommendations)  
  
-   <span data-ttu-id="567fe-109">**设置订阅的过期期限，使用：**</span><span class="sxs-lookup"><span data-stu-id="567fe-109">**To set the expiration period for subscriptions, using:**</span></span>  
  
     [<span data-ttu-id="567fe-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="567fe-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="567fe-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="567fe-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="567fe-112">开始之前</span><span class="sxs-lookup"><span data-stu-id="567fe-112">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="567fe-113">建议</span><span class="sxs-lookup"><span data-stu-id="567fe-113">Recommendations</span></span>  
  
-   <span data-ttu-id="567fe-114">订阅过期期限也称为“发布保持期” 。</span><span class="sxs-lookup"><span data-stu-id="567fe-114">The subscription expiration period is also referred to as the *publication retention period*.</span></span> <span data-ttu-id="567fe-115">合并复制元数据的清除依赖于此设置：</span><span class="sxs-lookup"><span data-stu-id="567fe-115">Cleanup of merge replication metadata is dependent on this setting:</span></span>  
  
    -   <span data-ttu-id="567fe-116">在到达保持期之前，复制无法清除发布数据库和订阅数据库中的元数据。</span><span class="sxs-lookup"><span data-stu-id="567fe-116">Replication cannot clean up metadata in the publication and subscription databases until the retention period is reached.</span></span> <span data-ttu-id="567fe-117">在为保持期指定较大值时务必谨慎，因为这可能对复制性能产生负面影响。</span><span class="sxs-lookup"><span data-stu-id="567fe-117">Use caution in specifying a high value for the retention period, because it can negatively impact replication performance.</span></span> <span data-ttu-id="567fe-118">如果能很有把握地预测出所有订阅服务器都将在该时间段内定期同步，则建议使用较低的设置。</span><span class="sxs-lookup"><span data-stu-id="567fe-118">It is recommended that you use a lower setting if you can reliably predict that all Subscribers will synchronize regularly within that time period.</span></span>  
  
         <span data-ttu-id="567fe-119">合并发布的保持期具有 24 小时的宽限期，以适应处于不同时区中的订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="567fe-119">The retention period for merge publications has a 24-hour grace period to accommodate Subscribers in different time zones.</span></span> <span data-ttu-id="567fe-120">例如，如果将保持期设置为 1 天，则实际的保持期为 48 小时。</span><span class="sxs-lookup"><span data-stu-id="567fe-120">If, for example, you set a retention period of one day, the actual retention period is 48 hours.</span></span>  
  
    -   <span data-ttu-id="567fe-121">可以指定订阅永不过期，但是强烈建议您不要使用此值，因为这样将无法清除元数据。</span><span class="sxs-lookup"><span data-stu-id="567fe-121">It is possible to specify that subscriptions never expire, but it is strongly recommended that you do not use this value, because metadata cannot be cleaned up.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="567fe-122">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="567fe-122">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="567fe-123">可在“发布属性 - \<Publication>”对话框的“常规”页面上设置订阅的过期期限 。</span><span class="sxs-lookup"><span data-stu-id="567fe-123">Set the expiration period for subscriptions on the **General** page of the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="567fe-124">有关访问此对话框的详细信息，请参阅 [View and Modify Publication Properties](view-and-modify-publication-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="567fe-124">For more information about accessing this dialog box, see [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span>  
  
#### <a name="to-set-the-expiration-period-for-subscriptions"></a><span data-ttu-id="567fe-125">设置订阅的过期期限</span><span class="sxs-lookup"><span data-stu-id="567fe-125">To set the expiration period for subscriptions</span></span>  
  
1.  <span data-ttu-id="567fe-126">在“发布属性 - \<Publication>”对话框的“常规”页面上的“订阅过期”部分中，指定订阅是否应过期  。</span><span class="sxs-lookup"><span data-stu-id="567fe-126">In the **Subscription expiration** section on the **General** page of the **Publication Properties - \<Publication>** dialog box, specify whether subscriptions should expire.</span></span>  
  
2.  <span data-ttu-id="567fe-127">如果它们应该过期，请指定一个过期时间段。</span><span class="sxs-lookup"><span data-stu-id="567fe-127">If they should expire, specify an expiration time period.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="567fe-128">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="567fe-128">Using Transact-SQL</span></span>  
 <span data-ttu-id="567fe-129">您可以使用复制存储过程在创建发布时设置此值或以后修改此值。</span><span class="sxs-lookup"><span data-stu-id="567fe-129">You can use replication stored procedures to either set this value when a publication is created or modify this value at a later time.</span></span>  
  
#### <a name="to-set-the-expiration-period-for-a-subscription-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="567fe-130">为快照或事务发布设置订阅过期时间</span><span class="sxs-lookup"><span data-stu-id="567fe-130">To set the expiration period for a subscription to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="567fe-131">在发布服务器上，执行 [sp_addpublication](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="567fe-131">At the Publisher, execute [sp_addpublication](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql).</span></span> <span data-ttu-id="567fe-132">以小时为单位为 \@retention 指定所需的订阅过期时间。</span><span class="sxs-lookup"><span data-stu-id="567fe-132">Specify the desired subscription expiration period, in hours, for **\@retention**.</span></span> <span data-ttu-id="567fe-133">默认的过期时间为 336 个小时。</span><span class="sxs-lookup"><span data-stu-id="567fe-133">The default expiration period is 336 hours.</span></span> <span data-ttu-id="567fe-134">有关详细信息，请参阅 [Create a Publication](create-a-publication.md)。</span><span class="sxs-lookup"><span data-stu-id="567fe-134">For more information, see [Create a Publication](create-a-publication.md).</span></span>  
  
#### <a name="to-set-the-expiration-period-for-a-subscription-to-a-merge-publication"></a><span data-ttu-id="567fe-135">为合并发布设置订阅过期时间</span><span class="sxs-lookup"><span data-stu-id="567fe-135">To set the expiration period for a subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="567fe-136">在发布服务器上，执行 [sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="567fe-136">At the Publisher, execute [sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql).</span></span> <span data-ttu-id="567fe-137">为 \@retention 指定所需的订阅过期时间值。</span><span class="sxs-lookup"><span data-stu-id="567fe-137">Specify the desired value for the subscription expiration period for **\@retention**.</span></span> <span data-ttu-id="567fe-138">为 \@retention_period_unit 指定此过期时间的表示单位，此单位可以是以下单位之一：</span><span class="sxs-lookup"><span data-stu-id="567fe-138">Specify the units in which the expiration period is expressed for **\@retention_period_unit**, which can be one of the following:</span></span>  
  
    -   <span data-ttu-id="567fe-139">**1** = 周</span><span class="sxs-lookup"><span data-stu-id="567fe-139">**1** = week</span></span>  
  
    -   <span data-ttu-id="567fe-140">**2** = 月</span><span class="sxs-lookup"><span data-stu-id="567fe-140">**2** = month</span></span>  
  
    -   <span data-ttu-id="567fe-141">**3** = 年</span><span class="sxs-lookup"><span data-stu-id="567fe-141">**3** = year</span></span>  
  
     <span data-ttu-id="567fe-142">默认的过期时间为 14 天。</span><span class="sxs-lookup"><span data-stu-id="567fe-142">The default expiration period is 14 days.</span></span> <span data-ttu-id="567fe-143">有关详细信息，请参阅 [Create a Publication](create-a-publication.md)。</span><span class="sxs-lookup"><span data-stu-id="567fe-143">For more information, see [Create a Publication](create-a-publication.md).</span></span>  
  
#### <a name="to-change-the-expiration-period-for-a-subscription-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="567fe-144">更改快照或事务发布的订阅过期时间</span><span class="sxs-lookup"><span data-stu-id="567fe-144">To change the expiration period for a subscription to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="567fe-145">在发布服务器上，执行 [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="567fe-145">At the Publisher, execute [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql).</span></span> <span data-ttu-id="567fe-146">为 \@property 指定保留期，并以小时为单位为 \@value 指定新的订阅过期时间  。</span><span class="sxs-lookup"><span data-stu-id="567fe-146">Specify **retention** for **\@property** and the new subscription expiration period, in hours, for **\@value**.</span></span>  
  
#### <a name="to-change-the-expiration-period-for-a-subscription-to-a-merge-publication"></a><span data-ttu-id="567fe-147">更改合并发布的订阅过期时间</span><span class="sxs-lookup"><span data-stu-id="567fe-147">To change the expiration period for a subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="567fe-148">在发布服务器上，执行 [sp_helpmergepublication](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql)，并指定 \@publication 和 \@publisher 。</span><span class="sxs-lookup"><span data-stu-id="567fe-148">At the Publisher, execute [sp_helpmergepublication](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql), specifying **\@publication** and **\@publisher**.</span></span> <span data-ttu-id="567fe-149">记下结果集中的 **retention_period_unit** 值，此值可能为以下值之一：</span><span class="sxs-lookup"><span data-stu-id="567fe-149">Note the value of **retention_period_unit** in the result set, which can be one of the following:</span></span>  
  
    -   <span data-ttu-id="567fe-150">**0** = 天</span><span class="sxs-lookup"><span data-stu-id="567fe-150">**0** = day</span></span>  
  
    -   <span data-ttu-id="567fe-151">**1** = 周</span><span class="sxs-lookup"><span data-stu-id="567fe-151">**1** = week</span></span>  
  
    -   <span data-ttu-id="567fe-152">**2** = 月</span><span class="sxs-lookup"><span data-stu-id="567fe-152">**2** = month</span></span>  
  
    -   <span data-ttu-id="567fe-153">**3** = 年</span><span class="sxs-lookup"><span data-stu-id="567fe-153">**3** = year</span></span>  
  
2.  <span data-ttu-id="567fe-154">在发布服务器上，执行 [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="567fe-154">At the Publisher, execute [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql).</span></span> <span data-ttu-id="567fe-155">为 \@property 指定保留期，并以步骤 1 中的保持期单位为 \@value 指定新的订阅过期时间  。</span><span class="sxs-lookup"><span data-stu-id="567fe-155">Specify **retention** for **\@property** and the new subscription expiration period, as text based on the retention period unit from step 1, for **\@value**.</span></span>  
  
3.  <span data-ttu-id="567fe-156">（可选）在发布服务器上，执行 [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="567fe-156">(Optional) At the Publisher, execute [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql).</span></span> <span data-ttu-id="567fe-157">为 \@property 指定 retention_period_unit，并为 \@value 指定新的订阅过期时间单位  。</span><span class="sxs-lookup"><span data-stu-id="567fe-157">Specify **retention_period_unit** for **\@property** and a new unit for the subscription expiration period for **\@value**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="567fe-158">另请参阅</span><span class="sxs-lookup"><span data-stu-id="567fe-158">See Also</span></span>  
 <span data-ttu-id="567fe-159">[Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="567fe-159">[Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md) </span></span>  
 [<span data-ttu-id="567fe-160">订阅过期和停用</span><span class="sxs-lookup"><span data-stu-id="567fe-160">Subscription Expiration and Deactivation</span></span>](../subscription-expiration-and-deactivation.md)  
  
  
