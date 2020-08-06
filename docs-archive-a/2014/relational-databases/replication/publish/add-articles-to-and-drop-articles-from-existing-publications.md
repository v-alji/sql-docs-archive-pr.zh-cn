---
title: 在现有发布中添加和删除项目 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- articles [SQL Server replication], dropping
- deleting articles
- removing articles
- dropping articles
- adding articles
- administering replication, articles
- publications [SQL Server replication], adding and dropping articles
- articles [SQL Server replication], adding
ms.assetid: b148e907-e1f2-483b-bdb2-59ea596efceb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f72f15886e7105dde8d0e15dd0598a7474ed7e39
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591261"
---
# <a name="add-articles-to-and-drop-articles-from-existing-publications"></a><span data-ttu-id="a1e59-102">向现有发布添加项目和从中删除项目</span><span class="sxs-lookup"><span data-stu-id="a1e59-102">Add Articles to and Drop Articles from Existing Publications</span></span>
  <span data-ttu-id="a1e59-103">在创建发布后，可以添加和删除项目。</span><span class="sxs-lookup"><span data-stu-id="a1e59-103">After a publication is created, it is possible to add and drop articles.</span></span> <span data-ttu-id="a1e59-104">可以随时添加项目，但删除项目所需的操作取决于复制的类型和删除项目的时间。</span><span class="sxs-lookup"><span data-stu-id="a1e59-104">Articles can be added at any time, but the actions required for dropping articles depend on the type of replication and when the article is dropped.</span></span>  
  
## <a name="adding-articles"></a><span data-ttu-id="a1e59-105">添加项目</span><span class="sxs-lookup"><span data-stu-id="a1e59-105">Adding Articles</span></span>  
 <span data-ttu-id="a1e59-106">添加项目涉及的操作有：将项目添加到发布、为发布创建新的快照、同步订阅以应用新项目的架构和数据。</span><span class="sxs-lookup"><span data-stu-id="a1e59-106">Adding an article involves: adding the article to the publication; creating a new snapshot for the publication; synchronizing the subscription to apply the schema and data for the new article.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a1e59-107">如果向合并发布中添加一个项目和一个依赖于此新项目的现有项目，则必须使用 [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) 和 [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql) 的 \@processing_order 参数指定两个项目的处理顺序。</span><span class="sxs-lookup"><span data-stu-id="a1e59-107">If you add an article to a merge publication and an existing article depends on the new article, you must specify a processing order for both articles using the **\@processing_order** parameter of [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) and [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql).</span></span> <span data-ttu-id="a1e59-108">请考虑以下情况：您要发布一个表，但不发布该表引用的函数。</span><span class="sxs-lookup"><span data-stu-id="a1e59-108">Consider the following scenario: you publish a table but you do not publish a function that the table references.</span></span> <span data-ttu-id="a1e59-109">如果不发布该函数，则无法在订阅服务器中创建相应的表。</span><span class="sxs-lookup"><span data-stu-id="a1e59-109">If you do not publish the function, the table cannot be created at the Subscriber.</span></span> <span data-ttu-id="a1e59-110">将此函数添加到发布时：为 sp_addmergearticle 的 \@processing_order 参数指定值 1；为 sp_changemergearticle 的 \@processing_order 参数指定值 2，为参数 \@article 指定表名称。</span><span class="sxs-lookup"><span data-stu-id="a1e59-110">When you add the function to the publication: specify a value of **1** for the **\@processing_order** parameter of **sp_addmergearticle**; and specify a value of **2** for the **\@processing_order** parameter of **sp_changemergearticle**, specifying the table name for the parameter **\@article**.</span></span> <span data-ttu-id="a1e59-111">此处理顺序可确保在创建依赖于某函数的表之前在订阅服务器上创建该函数。</span><span class="sxs-lookup"><span data-stu-id="a1e59-111">This processing order ensures that you create the function at the Subscriber before the table that depends on it.</span></span> <span data-ttu-id="a1e59-112">每个项目可以使用不同的数字，只要函数的数字小于表的数字即可。</span><span class="sxs-lookup"><span data-stu-id="a1e59-112">You can use different numbers for each article, as long as the number for the function is lower than the number for the table.</span></span>  
  
1.  <span data-ttu-id="a1e59-113">用以下方法之一添加一个或多个项目：</span><span class="sxs-lookup"><span data-stu-id="a1e59-113">Add one or more articles through one of the following methods:</span></span>  
  
    -   [<span data-ttu-id="a1e59-114">在发布中添加和删除项目 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="a1e59-114">Add Articles to and Drop Articles from a Publication &#40;SQL Server Management Studio&#41;</span></span>](add-articles-to-and-drop-articles-from-a-publication.md)  
  
    -   [<span data-ttu-id="a1e59-115">定义项目</span><span class="sxs-lookup"><span data-stu-id="a1e59-115">Define an Article</span></span>](define-an-article.md)  
  
2.  <span data-ttu-id="a1e59-116">将项目添加到发布后，必须为发布（和所有分区，如果发布是带有参数化筛选器的合并发布）创建新的快照。</span><span class="sxs-lookup"><span data-stu-id="a1e59-116">After adding an article to a publication, you must create a new snapshot for the publication (and all partitions if it is a merge publication with parameterized filters).</span></span> <span data-ttu-id="a1e59-117">然后，分发代理或合并代理将新项目的架构和数据复制到订阅服务器（并不重新初始化整个发布）。</span><span class="sxs-lookup"><span data-stu-id="a1e59-117">The Distribution Agent or Merge Agent then copies the schema and data for the new article to the Subscriber (it does not reinitialize the entire publication).</span></span>  
  
    -   <span data-ttu-id="a1e59-118">若要创建新快照，请参阅 [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md)。</span><span class="sxs-lookup"><span data-stu-id="a1e59-118">To create a new snapshot, see [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md).</span></span>  
  
    -   <span data-ttu-id="a1e59-119">若要为包含参数化筛选器的合并发布创建新快照，请参阅[为包含参数化筛选器的合并发布创建快照](../create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)。</span><span class="sxs-lookup"><span data-stu-id="a1e59-119">To create a new snapshot for a merge publication with parameterized filters, see [Create a Snapshot for a Merge Publication with Parameterized Filters](../create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md).</span></span>  
  
3.  <span data-ttu-id="a1e59-120">创建快照后，同步订阅以复制新项目的架构和数据。</span><span class="sxs-lookup"><span data-stu-id="a1e59-120">After the snapshot is created, synchronize the subscription to copy the schema and data for the new article.</span></span>  
  
    -   <span data-ttu-id="a1e59-121">若要同步推送订阅，请参阅 [Synchronize a Push Subscription](../synchronize-a-push-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="a1e59-121">To synchronize a push subscription, see [Synchronize a Push Subscription](../synchronize-a-push-subscription.md).</span></span>  
  
    -   <span data-ttu-id="a1e59-122">若要同步请求订阅，请参阅 [Synchronize a Pull Subscription](../synchronize-a-pull-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="a1e59-122">To synchronize a pull subscription, see [Synchronize a Pull Subscription](../synchronize-a-pull-subscription.md).</span></span>  
  
## <a name="dropping-articles"></a><span data-ttu-id="a1e59-123">删除项目</span><span class="sxs-lookup"><span data-stu-id="a1e59-123">Dropping Articles</span></span>  
 <span data-ttu-id="a1e59-124">可以随时从发布中删除项目，但必须考虑以下行为：</span><span class="sxs-lookup"><span data-stu-id="a1e59-124">Articles can be dropped from a publication at any time, but you must take into account the following behaviors:</span></span>  
  
-   <span data-ttu-id="a1e59-125">从发布中删除项目并不会将对象从发布数据库中删除，也不会将相应对象从订阅数据库中删除。</span><span class="sxs-lookup"><span data-stu-id="a1e59-125">Dropping an article from a publication does not remove the object from the publication database or the corresponding object from the subscription database.</span></span> <span data-ttu-id="a1e59-126">必要时，使用 DROP \<Object> 删除这些对象。</span><span class="sxs-lookup"><span data-stu-id="a1e59-126">Use DROP \<Object> to remove these objects if necessary.</span></span> <span data-ttu-id="a1e59-127">在删除通过外键约束与其他已发布项目相关的项目时，建议手动或使用按需脚本执行在订阅服务器上删除表：指定包含相应 DROP \<Object> 语句的脚本。</span><span class="sxs-lookup"><span data-stu-id="a1e59-127">When you drop an article that is related to other published articles through foreign key constraints, we recommend that you drop the table at the Subscriber manually or by using on-demand script execution: specify a script that includes the appropriate DROP \<Object> statements.</span></span> <span data-ttu-id="a1e59-128">有关详细信息，请参阅[在同步期间执行脚本（复制 Transact-SQL 编程）](../execute-scripts-during-synchronization-replication-transact-sql-programming.md)。</span><span class="sxs-lookup"><span data-stu-id="a1e59-128">For more information, see [Execute Scripts During Synchronization &#40;Replication Transact-SQL Programming&#41;](../execute-scripts-during-synchronization-replication-transact-sql-programming.md).</span></span>  
  
-   <span data-ttu-id="a1e59-129">对于兼容级别为 90RTM 或更高的合并发布，可以随时删除项目，但需要创建一个新的快照。</span><span class="sxs-lookup"><span data-stu-id="a1e59-129">For merge publications with a compatibility level of 90RTM or higher, articles can be dropped at any time, but a new snapshot is required.</span></span> <span data-ttu-id="a1e59-130">此外：</span><span class="sxs-lookup"><span data-stu-id="a1e59-130">Additionally:</span></span>  
  
    -   <span data-ttu-id="a1e59-131">如果项目在联接筛选器或逻辑记录关系中是父项目，就必须先删除关系，这需要重新初始化。</span><span class="sxs-lookup"><span data-stu-id="a1e59-131">If an article is a parent article in a join filter or logical record relationship, the relationships must be dropped first, which requires reinitialization.</span></span>  
  
    -   <span data-ttu-id="a1e59-132">如果项目具有发布中的最后一个参数化筛选器，就必须重新初始化订阅。</span><span class="sxs-lookup"><span data-stu-id="a1e59-132">If an article has the last parameterized filter in a publication, subscriptions must be reinitialized.</span></span>  
  
-   <span data-ttu-id="a1e59-133">对于兼容级别低于 90RTM 的合并发布，可以在初始同步订阅之前删除项目，而无需特别考虑。</span><span class="sxs-lookup"><span data-stu-id="a1e59-133">For merge publications with a compatibility level lower than 90RTM, articles can be dropped with no special considerations prior to the initial synchronization of subscriptions.</span></span> <span data-ttu-id="a1e59-134">如果在同步一个或多个订阅之后删除项目，则必须删除、重新创建和同步订阅。</span><span class="sxs-lookup"><span data-stu-id="a1e59-134">If an article is dropped after one or more subscriptions is synchronized, the subscriptions must be dropped, re-created, and synchronized.</span></span>  
  
-   <span data-ttu-id="a1e59-135">对于快照发布或事务发布，可以在创建订阅之前删除项目，而无需特别考虑。</span><span class="sxs-lookup"><span data-stu-id="a1e59-135">For snapshot or transactional publications, articles can be dropped with no special considerations prior to subscriptions being created.</span></span> <span data-ttu-id="a1e59-136">如果在创建一个或多个订阅之后删除项目，则必须删除、重新创建和同步订阅。</span><span class="sxs-lookup"><span data-stu-id="a1e59-136">If an article is dropped after one or more subscriptions is created, the subscriptions must be dropped, recreated, and synchronized.</span></span> <span data-ttu-id="a1e59-137">有关删除订阅的详细信息，请参阅[订阅发布](../subscribe-to-publications.md)和 [sp_dropsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="a1e59-137">For more information about dropping subscriptions, see [Subscribe to Publications](../subscribe-to-publications.md) and [sp_dropsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql).</span></span> <span data-ttu-id="a1e59-138">使用**sp_dropsubscription** 可以删除订阅中的单个项目，而不是删除整个订阅。</span><span class="sxs-lookup"><span data-stu-id="a1e59-138">**sp_dropsubscription** allows you to drop a single article from the subscription rather than the entire subscription.</span></span>  
  
1.  <span data-ttu-id="a1e59-139">从发布中删除项目涉及的操作有：删除项目并为发布创建新的快照。</span><span class="sxs-lookup"><span data-stu-id="a1e59-139">Dropping an article from a publication involves dropping the article and creating a new snapshot for the publication.</span></span> <span data-ttu-id="a1e59-140">删除项目会使当前快照失效，因此必须创建新的快照。</span><span class="sxs-lookup"><span data-stu-id="a1e59-140">Dropping an article invalidates the current snapshot; therefore a new snapshot must be created.</span></span>  
  
    -   <span data-ttu-id="a1e59-141">若要从发布中删除项目，请参阅[在发布中添加和删除项目 &#40;SQL Server Management Studio&#41;](add-articles-to-and-drop-articles-from-a-publication.md) 或[删除项目](delete-an-article.md)。</span><span class="sxs-lookup"><span data-stu-id="a1e59-141">To drop an article from a publication, see [Add Articles to and Drop Articles from a Publication &#40;SQL Server Management Studio&#41;](add-articles-to-and-drop-articles-from-a-publication.md) or [Delete an Article](delete-an-article.md).</span></span>  
  
2.  <span data-ttu-id="a1e59-142">从发布中删除项目后，必须为发布（和所有分区，如果发布是带有参数化筛选器的合并发布）创建新的快照。</span><span class="sxs-lookup"><span data-stu-id="a1e59-142">After dropping an article from a publication, you must create a new snapshot for the publication (and all partitions if it is a merge publication with parameterized filters).</span></span>  
  
    -   <span data-ttu-id="a1e59-143">若要创建新快照，请参阅 [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md)。</span><span class="sxs-lookup"><span data-stu-id="a1e59-143">To create a new snapshot, see [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md).</span></span>  
  
    -   <span data-ttu-id="a1e59-144">若要为包含参数化筛选器的合并发布创建新快照，请参阅[为包含参数化筛选器的合并发布创建快照](../create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)。</span><span class="sxs-lookup"><span data-stu-id="a1e59-144">To create a new snapshot for a merge publication with parameterized filters, see [Create a Snapshot for a Merge Publication with Parameterized Filters](../create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md).</span></span>  
  
 <span data-ttu-id="a1e59-145">如上所述，在某些情况下删除项目需要删除、重新创建及同步订阅。</span><span class="sxs-lookup"><span data-stu-id="a1e59-145">As noted above, in some cases dropping an article requires subscriptions to be dropped, recreated, and then synchronized.</span></span> <span data-ttu-id="a1e59-146">有关详细信息，请参阅[订阅发布](../subscribe-to-publications.md)和[同步数据](../synchronize-data.md)。</span><span class="sxs-lookup"><span data-stu-id="a1e59-146">For more information, see [Subscribe to Publications](../subscribe-to-publications.md) and [Synchronize Data](../synchronize-data.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1e59-147">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a1e59-147">See Also</span></span>  
 <span data-ttu-id="a1e59-148">[发布数据和数据库对象](publish-data-and-database-objects.md) </span><span class="sxs-lookup"><span data-stu-id="a1e59-148">[Publish Data and Database Objects](publish-data-and-database-objects.md) </span></span>  
 <span data-ttu-id="a1e59-149">[重新初始化订阅](../reinitialize-subscriptions.md) </span><span class="sxs-lookup"><span data-stu-id="a1e59-149">[Reinitialize Subscriptions](../reinitialize-subscriptions.md) </span></span>  
 [<span data-ttu-id="a1e59-150">对发布数据库进行架构更改</span><span class="sxs-lookup"><span data-stu-id="a1e59-150">Make Schema Changes on Publication Databases</span></span>](make-schema-changes-on-publication-databases.md)  
  
  
