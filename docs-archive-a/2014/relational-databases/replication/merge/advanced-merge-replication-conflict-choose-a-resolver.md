---
title: 选择冲突解决程序 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- default conflict resolver
- articles [SQL Server replication], conflict resolution
- conflict resolution [SQL Server replication], merge replication
ms.assetid: b7dec3fa-d9d9-409d-b946-f9b9a3202829
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0db289e923cab72bf175b172f039ea228c991110
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578821"
---
# <a name="choose-a-resolver"></a><span data-ttu-id="e58f1-102">选择冲突解决程序</span><span class="sxs-lookup"><span data-stu-id="e58f1-102">Choose a Resolver</span></span>
  <span data-ttu-id="e58f1-103">在选择冲突解决程序时，请考虑冲突解决在您的应用程序中的重要性，以及是否可以使用基于优先级的默认冲突解决程序或是否需要使用项目冲突解决程序。</span><span class="sxs-lookup"><span data-stu-id="e58f1-103">When choosing a resolver, consider the importance of conflict resolution in your application and whether you can use the default priority-based conflict resolver or need to use an article resolver.</span></span>  
  
 <span data-ttu-id="e58f1-104">如果数据是分区的，没有多用户写入相同的分区，并且复制拓扑也相对简单（一个发布服务器和几个订阅服务器），则冲突将极少发生或根本不存在冲突。</span><span class="sxs-lookup"><span data-stu-id="e58f1-104">If your data is partitioned without multiple users writing to the same partitions, and your replication topology is relatively basic (one Publisher and a few Subscribers), conflicts should be rare or nonexistent.</span></span> <span data-ttu-id="e58f1-105">在这些环境中，可能不需要复杂的冲突解决策略。</span><span class="sxs-lookup"><span data-stu-id="e58f1-105">In these environments, you probably do not need a complex conflict resolution strategy.</span></span> <span data-ttu-id="e58f1-106">推荐使用默认冲突解决设置，即使用客户端订阅和首次更改入选的策略。</span><span class="sxs-lookup"><span data-stu-id="e58f1-106">A strategy using the default settings for conflict resolution, using client subscriptions and a first change in wins policy, is recommended.</span></span> <span data-ttu-id="e58f1-107">如果拓扑较复杂（例如，使用重新发布订阅服务器），则具有特定优先级的服务器订阅可能比较合适。</span><span class="sxs-lookup"><span data-stu-id="e58f1-107">If the topology is more complex (using republishing Subscribers, for example), server subscriptions with specific priorities might be more appropriate.</span></span>  
  
 <span data-ttu-id="e58f1-108">如果业务需求所要求比默认冲突解决程序更精细优化的解决方案，则建议使用项目冲突解决程序。</span><span class="sxs-lookup"><span data-stu-id="e58f1-108">An article resolver is recommended if your business needs require a more finely tuned solution than is available with the default resolver.</span></span> <span data-ttu-id="e58f1-109">如果选择使用项目冲突解决程序，则建议使用业务逻辑处理程序。</span><span class="sxs-lookup"><span data-stu-id="e58f1-109">If you choose to use an article resolver, it is recommended that you use a business logic handler.</span></span> <span data-ttu-id="e58f1-110">有关详细信息，请参阅[合并同步期间执行业务逻辑](execute-business-logic-during-merge-synchronization.md)。</span><span class="sxs-lookup"><span data-stu-id="e58f1-110">For more information, see [Execute Business Logic During Merge Synchronization](execute-business-logic-during-merge-synchronization.md).</span></span>  
  
 <span data-ttu-id="e58f1-111">总之，要根据数据和应用程序的业务逻辑需要来选择使用默认冲突解决程序还是使用项目冲突解决程序。</span><span class="sxs-lookup"><span data-stu-id="e58f1-111">Ultimately, choosing whether to use the default resolver or an article resolver should be based on the data and the business logic needs of the application.</span></span> <span data-ttu-id="e58f1-112">例如，假设雇员向不同订阅服务器上的一组未分区表输入客户排名数据，雇员跨多个工作类别（分公司经理、产品经理、销售人员），并且工作类别决定谁的数据具有优先级。</span><span class="sxs-lookup"><span data-stu-id="e58f1-112">For example, consider employees who enter customer ranking data into a set of non-partitioned tables at different Subscribers; the employees span various job categories (branch managers, line managers, sales staff), and job category determines whose data should be given priority.</span></span> <span data-ttu-id="e58f1-113">这种情况下，可以生成一个项目冲突解决程序，使用项目的工作类别数据确定发生冲突时的入选方。</span><span class="sxs-lookup"><span data-stu-id="e58f1-113">In this case, an article resolver can be built that uses job category data from the article to determine the winner if a conflict occurs.</span></span>  
  
 <span data-ttu-id="e58f1-114">如果冲突有可能频繁发生，下面列出了实施冲突解决策略时应考虑的最重要的决定。</span><span class="sxs-lookup"><span data-stu-id="e58f1-114">If conflicts are likely to occur with some frequency, here are the most important decisions you should consider when implementing a conflict resolution strategy.</span></span>  
  
|<span data-ttu-id="e58f1-115">冲突解决问题</span><span class="sxs-lookup"><span data-stu-id="e58f1-115">Conflict resolution issue</span></span>|<span data-ttu-id="e58f1-116">建议</span><span class="sxs-lookup"><span data-stu-id="e58f1-116">Recommendation</span></span>|  
|-------------------------------|--------------------|  
|<span data-ttu-id="e58f1-117">不同类别的用户要求不同的优先级值。</span><span class="sxs-lookup"><span data-stu-id="e58f1-117">Different categories of users require different priority values.</span></span>|<span data-ttu-id="e58f1-118">使用默认冲突解决程序并创建具有不同优先级值的服务器订阅。</span><span class="sxs-lookup"><span data-stu-id="e58f1-118">Use the default resolver and create server subscriptions with different priority values.</span></span><br /><br /> <span data-ttu-id="e58f1-119">-或-</span><span class="sxs-lookup"><span data-stu-id="e58f1-119">-Or-</span></span><br /><br /> <span data-ttu-id="e58f1-120">使用可以识别项目中授权值列的项目冲突解决程序帮助解决冲突。</span><span class="sxs-lookup"><span data-stu-id="e58f1-120">Use an article resolver that recognizes an authority value column in the article to help resolve a conflict.</span></span>|  
|<span data-ttu-id="e58f1-121">要求首次更改入选冲突解决方案。</span><span class="sxs-lookup"><span data-stu-id="e58f1-121">First change in wins conflict solution wanted.</span></span>|<span data-ttu-id="e58f1-122">使用默认冲突解决程序并创建客户端订阅。</span><span class="sxs-lookup"><span data-stu-id="e58f1-122">Use the default resolver and create client subscriptions.</span></span>|  
|<span data-ttu-id="e58f1-123">允许多个用户更改同一数据行，条件是不对同一列进行有冲突的更改。</span><span class="sxs-lookup"><span data-stu-id="e58f1-123">Multiple users changing the same data row is acceptable, as long as no conflicting changes are made to the same column.</span></span>|<span data-ttu-id="e58f1-124">使用启用了列级跟踪的默认冲突解决程序或项目冲突解决程序。</span><span class="sxs-lookup"><span data-stu-id="e58f1-124">Use either the default resolver or an article resolver with column-level tracking enabled.</span></span>|  
|<span data-ttu-id="e58f1-125">将对行内任意值的多次更改标记为冲突。</span><span class="sxs-lookup"><span data-stu-id="e58f1-125">Flag multiple changes to any value in a row as a conflict.</span></span>|<span data-ttu-id="e58f1-126">使用具有行级跟踪的默认冲突解决程序或项目冲突解决程序。</span><span class="sxs-lookup"><span data-stu-id="e58f1-126">Use either the default resolver or an article resolver with row-level tracking.</span></span>|  
|<span data-ttu-id="e58f1-127">将对逻辑记录中任意值的多次更改标记为冲突。</span><span class="sxs-lookup"><span data-stu-id="e58f1-127">Flag multiple changes to any value in a logical record as a conflict.</span></span>|<span data-ttu-id="e58f1-128">使用具有逻辑记录级跟踪的默认冲突解决程序（逻辑记录功能不支持自定义冲突解决程序或业务逻辑处理程序）。</span><span class="sxs-lookup"><span data-stu-id="e58f1-128">Use the default resolver with logical record-level tracking (the logical records feature does not support custom resolvers or business logic handlers).</span></span>|  
|<span data-ttu-id="e58f1-129">冲突解决结果数据应该与原始冲突数据不同。</span><span class="sxs-lookup"><span data-stu-id="e58f1-129">Conflict outcome data needs to be different from original conflict data.</span></span>|<span data-ttu-id="e58f1-130">使用计算新值的项目冲突解决程序。</span><span class="sxs-lookup"><span data-stu-id="e58f1-130">Use an article resolver that calculates new values.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e58f1-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e58f1-131">See Also</span></span>  
 <span data-ttu-id="e58f1-132">[Detecting and Resolving Conflicts in Logical Records](advanced-merge-replication-conflict-resolving-in-logical-record.md) </span><span class="sxs-lookup"><span data-stu-id="e58f1-132">[Detecting and Resolving Conflicts in Logical Records](advanced-merge-replication-conflict-resolving-in-logical-record.md) </span></span>  
 <span data-ttu-id="e58f1-133">[Advanced Merge Replication Conflict Detection and Resolution](advanced-merge-replication-conflict-detection-and-resolution.md) </span><span class="sxs-lookup"><span data-stu-id="e58f1-133">[Advanced Merge Replication Conflict Detection and Resolution](advanced-merge-replication-conflict-detection-and-resolution.md) </span></span>  
 [<span data-ttu-id="e58f1-134">重新发布数据</span><span class="sxs-lookup"><span data-stu-id="e58f1-134">Republish Data</span></span>](../republish-data.md)  
  
  
