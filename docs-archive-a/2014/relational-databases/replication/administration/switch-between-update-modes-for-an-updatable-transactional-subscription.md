---
title: 切换可更新事务订阅的更新模式 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- transactional replication, updatable subscriptions
- updatable subscriptions, update modes
- subscriptions [SQL Server replication], updatable
ms.assetid: ab5ebab1-7ee4-41f4-999b-b4f0c420c921
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c31814d1e2ab6fac64ffcde883f3cac2439828a1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591875"
---
# <a name="switch-between-update-modes-for-an-updatable-transactional-subscription"></a><span data-ttu-id="f6cc5-102">切换可更新事务性订阅的更新模式</span><span class="sxs-lookup"><span data-stu-id="f6cc5-102">Switch Between Update Modes for an Updatable Transactional Subscription</span></span>
  <span data-ttu-id="f6cc5-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中切换可更新事务订阅的更新模式。</span><span class="sxs-lookup"><span data-stu-id="f6cc5-103">This topic describes how to switch between update modes for an updatable transaction subscription in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="f6cc5-104">可以使用新建订阅向导，为可更新的订阅指定模式。</span><span class="sxs-lookup"><span data-stu-id="f6cc5-104">Specify the mode for updatable subscriptions using the New Subscription Wizard.</span></span> <span data-ttu-id="f6cc5-105">有关使用此向导时设置模式的信息，请参阅[查看和修改请求订阅属性](../view-and-modify-pull-subscription-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="f6cc5-105">For information about setting the mode when using this wizard, see [View and Modify Pull Subscription Properties](../view-and-modify-pull-subscription-properties.md).</span></span>  
  
  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f6cc5-106">开始之前</span><span class="sxs-lookup"><span data-stu-id="f6cc5-106">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="f6cc5-107">限制和局限</span><span class="sxs-lookup"><span data-stu-id="f6cc5-107">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="f6cc5-108">可以随时从立即更新向排队更新进行故障转移。</span><span class="sxs-lookup"><span data-stu-id="f6cc5-108">You can fail over from immediate to queued updating at any time.</span></span> <span data-ttu-id="f6cc5-109">但执行该操作后，只有在已连接订阅服务器和发布服务器且队列读取器代理已将队列中的所有挂起消息应用到发布服务器后，才能恢复立即更新。</span><span class="sxs-lookup"><span data-stu-id="f6cc5-109">After you do, however, you cannot return to immediate updating until the Subscriber and Publisher are connected and the Queue Reader Agent has applied all pending messages in the queue to the Publisher.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="f6cc5-110">建议</span><span class="sxs-lookup"><span data-stu-id="f6cc5-110">Recommendations</span></span>  
  
-   <span data-ttu-id="f6cc5-111">当对事务发布的更新订阅支持从一种更新模式故障转移到另一种更新模式时，可通过编程方式切换更新模式以应对连接发生短暂变化的情况。</span><span class="sxs-lookup"><span data-stu-id="f6cc5-111">When an updating subscription to a transactional publication supports failover from one updating mode to another, you can programmatically switch update modes to handle situations when connectivity changes for a short period of time.</span></span> <span data-ttu-id="f6cc5-112">可以使用复制存储过程，以编程方式并根据需要设置更新模式。</span><span class="sxs-lookup"><span data-stu-id="f6cc5-112">The update mode can be set programmatically and on demand using replication stored procedures.</span></span> <span data-ttu-id="f6cc5-113">有关详细信息，请参阅 [Updatable Subscriptions for Transactional Replication](../transactional/updatable-subscriptions-for-transactional-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="f6cc5-113">For more information, see [Updatable Subscriptions for Transactional Replication](../transactional/updatable-subscriptions-for-transactional-replication.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="f6cc5-114">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f6cc5-114">Using SQL Server Management Studio</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f6cc5-115">若要在创建订阅后更改更新模式，必须在创建订阅时将 **update_mode** 属性设置为 **failover** （允许从立即更新切换到排队更新）或 **queued failover** （允许从排队更新切换到立即更新）。</span><span class="sxs-lookup"><span data-stu-id="f6cc5-115">To change the update mode after the subscription is created, the **update_mode** property must be set to **failover** (which allows a switch from immediate updating to queued updating) or **queued failover** (which allows a switch from queued updating to immediate updating) when the subscription is created.</span></span> <span data-ttu-id="f6cc5-116">在新建订阅向导中，这些属性是自动设置的。</span><span class="sxs-lookup"><span data-stu-id="f6cc5-116">These properties are set automatically in the New Subscription Wizard.</span></span>  
  
#### <a name="to-set-the-updating-mode-for-a-push-subscription"></a><span data-ttu-id="f6cc5-117">设置推送订阅的更新模式</span><span class="sxs-lookup"><span data-stu-id="f6cc5-117">To set the updating mode for a push subscription</span></span>  
  
1.  <span data-ttu-id="f6cc5-118">在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]中连接到订阅服务器，然后展开服务器节点。</span><span class="sxs-lookup"><span data-stu-id="f6cc5-118">Connect to the Subscriber in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="f6cc5-119">展开 **“复制”** 文件夹，再展开 **“本地订阅”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="f6cc5-119">Expand the **Replication** folder, and then expand the **Local Subscriptions** folder.</span></span>  
  
3.  <span data-ttu-id="f6cc5-120">右键单击要为其设置更新模式的订阅，然后单击 **“设置更新方法”** 。</span><span class="sxs-lookup"><span data-stu-id="f6cc5-120">Right-click the subscription for which you want to set the update mode, and then click **Set Update Method**.</span></span>  
  
4.  <span data-ttu-id="f6cc5-121">在“设置更新方法 - \<Subscriber>: \<SubscriptionDatabase>”对话框中，选择“立即更新”或“排队更新”  。</span><span class="sxs-lookup"><span data-stu-id="f6cc5-121">In the **Set Update Method - \<Subscriber>: \<SubscriptionDatabase>** dialog box, select **Immediate updating** or **Queued updating**.</span></span>  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### <a name="to-set-the-updating-mode-for-a-pull-subscription"></a><span data-ttu-id="f6cc5-122">设置请求订阅的更新模式</span><span class="sxs-lookup"><span data-stu-id="f6cc5-122">To set the updating mode for a pull subscription</span></span>  
  
1.  <span data-ttu-id="f6cc5-123">在“订阅属性 - \<Publisher>: \<PublicationDatabase>”对话框中，为“订阅服务器更新方法”选项选择“立即复制所做的更改”或“排队更改”的值   。</span><span class="sxs-lookup"><span data-stu-id="f6cc5-123">In the **Subscription Properties - \<Publisher>: \<PublicationDatabase>** dialog box, select a value of **Immediately replicate changes** or **Queue changes** for the **Subscriber update method** option.</span></span>  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
 <span data-ttu-id="f6cc5-124">有关访问“订阅属性 - \<Publisher>: \<PublicationDatabase>”对话框的详细信息，请参阅[查看和修改推送订阅属性](../view-and-modify-pull-subscription-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="f6cc5-124">For more information about accessing the **Subscription Properties - \<Publisher>: \<PublicationDatabase>** dialog box, see [View and Modify Pull Subscription Properties](../view-and-modify-pull-subscription-properties.md).</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="f6cc5-125">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f6cc5-125">Using Transact-SQL</span></span>  
  
#### <a name="to-switch-between-update-modes"></a><span data-ttu-id="f6cc5-126">切换更新模式</span><span class="sxs-lookup"><span data-stu-id="f6cc5-126">To switch between update modes</span></span>  
  
1.  <span data-ttu-id="f6cc5-127">通过对请求订阅执行 [sp_helppullsubscription](/sql/relational-databases/system-stored-procedures/sp-helppullsubscription-transact-sql) 或对推送订阅执行 [sp_helpsubscription](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql) ，验证订阅是否支持故障转移。</span><span class="sxs-lookup"><span data-stu-id="f6cc5-127">Verify that the subscription supports failover by executing [sp_helppullsubscription](/sql/relational-databases/system-stored-procedures/sp-helppullsubscription-transact-sql) for a pull subscription or [sp_helpsubscription](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql) for a push subscription.</span></span> <span data-ttu-id="f6cc5-128">如果结果集中 **update mode** 的值为 **3** 或 **4**，则支持故障转移。</span><span class="sxs-lookup"><span data-stu-id="f6cc5-128">If the value of **update mode** in the result set is **3** or **4**, failover is supported.</span></span>  
  
2.  <span data-ttu-id="f6cc5-129">在订阅服务器上，对订阅数据库执行 [sp_setreplfailovermode](/sql/relational-databases/system-stored-procedures/sp-setreplfailovermode-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="f6cc5-129">At the Subscriber on the subscription database, execute [sp_setreplfailovermode](/sql/relational-databases/system-stored-procedures/sp-setreplfailovermode-transact-sql).</span></span> <span data-ttu-id="f6cc5-130">**@publisher**为指定、 **@publisher_db** 、 **@publication** 和以下值之一 **@failover_mode** ：</span><span class="sxs-lookup"><span data-stu-id="f6cc5-130">Specify **@publisher**, **@publisher_db**, **@publication**, and one of the following values for **@failover_mode**:</span></span>  
  
    -   <span data-ttu-id="f6cc5-131">**queued** - 在短暂断开连接时将故障转移到排队更新。</span><span class="sxs-lookup"><span data-stu-id="f6cc5-131">**queued** - fail over to queued updating when connectivity has been temporarily lost.</span></span>  
  
    -   <span data-ttu-id="f6cc5-132">**immediate** - 在恢复连接后将故障转移到立即更新。</span><span class="sxs-lookup"><span data-stu-id="f6cc5-132">**immediate** - fail over to immediate updating when connectivity has been restored.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6cc5-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f6cc5-133">See Also</span></span>  
 [<span data-ttu-id="f6cc5-134">Updatable Subscriptions for Transactional Replication</span><span class="sxs-lookup"><span data-stu-id="f6cc5-134">Updatable Subscriptions for Transactional Replication</span></span>](../transactional/updatable-subscriptions-for-transactional-replication.md)  
  
  
