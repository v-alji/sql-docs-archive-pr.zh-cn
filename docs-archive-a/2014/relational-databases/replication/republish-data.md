---
title: 重新发布数据 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- republishing data
- publishing [SQL Server replication], Subscribers
- Subscribers [SQL Server replication], republishing data
ms.assetid: a1485cf4-b1c4-49e9-ab06-8ccfaad998f3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f1e4213266121b3bf55bf2857e15f71f1e94e301
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577510"
---
# <a name="republish-data"></a><span data-ttu-id="a8d54-102">重新发布数据</span><span class="sxs-lookup"><span data-stu-id="a8d54-102">Republish Data</span></span>
  <span data-ttu-id="a8d54-103">在重新发布模式中，发布服务器将数据发送到订阅服务器，后者将数据重新发布到任意数目的其他订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="a8d54-103">In a republishing model, the Publisher sends data to a Subscriber, which then republishes the data to any number of other Subscribers.</span></span> <span data-ttu-id="a8d54-104">当发布服务器必须通过低速或昂贵的通信链接向订阅服务器发送数据时，这很有用。</span><span class="sxs-lookup"><span data-stu-id="a8d54-104">This is useful when a Publisher must send data to Subscribers over a slow or expensive communications link.</span></span> <span data-ttu-id="a8d54-105">如果在链接的远端有许多订阅服务器，那么使用重新发布服务器可将大量分发负荷转移到链接的远端。</span><span class="sxs-lookup"><span data-stu-id="a8d54-105">If there are a number of Subscribers on the far side of that link, using a republisher shifts the bulk of the distribution load to that side of the link.</span></span>  
  
 <span data-ttu-id="a8d54-106">重新发布数据分为下列几个步骤：</span><span class="sxs-lookup"><span data-stu-id="a8d54-106">Republishing data involves the following steps:</span></span>  
  
1.  <span data-ttu-id="a8d54-107">在发布服务器上创建发布。</span><span class="sxs-lookup"><span data-stu-id="a8d54-107">Create a publication at the Publisher.</span></span>  
  
2.  <span data-ttu-id="a8d54-108">为重新发布的订阅服务器创建对发布的订阅。</span><span class="sxs-lookup"><span data-stu-id="a8d54-108">Create a subscription to the publication for the republishing Subscriber.</span></span>  
  
3.  <span data-ttu-id="a8d54-109">初始化订阅。</span><span class="sxs-lookup"><span data-stu-id="a8d54-109">Initialize the subscription.</span></span> <span data-ttu-id="a8d54-110">必须先初始化订阅，才可在重新发布的订阅服务器上创建发布，否则复制将失败。</span><span class="sxs-lookup"><span data-stu-id="a8d54-110">The subscription must be initialized before the publication is created at the republishing Subscriber, or replication will fail.</span></span>  
  
4.  <span data-ttu-id="a8d54-111">在重新发布的订阅服务器上的订阅数据库中创建发布。</span><span class="sxs-lookup"><span data-stu-id="a8d54-111">Create a publication in the subscription database at the republishing Subscriber.</span></span>  
  
5.  <span data-ttu-id="a8d54-112">在重新发布的订阅服务器上为其他订阅服务器创建对发布的订阅。</span><span class="sxs-lookup"><span data-stu-id="a8d54-112">Create subscriptions to the publication at the republishing Subscriber for the other Subscribers.</span></span>  
  
6.  <span data-ttu-id="a8d54-113">初始化订阅。</span><span class="sxs-lookup"><span data-stu-id="a8d54-113">Initialize the subscriptions.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a8d54-114">如果在重新发布拓扑中使用合并复制，则所有重新发布的订阅服务器都必须使用服务器订阅。</span><span class="sxs-lookup"><span data-stu-id="a8d54-114">If you use merge replication in a republishing topology, all republishing Subscribers must use server subscriptions.</span></span> <span data-ttu-id="a8d54-115">有关订阅类型的详细信息，请参阅[订阅发布](subscribe-to-publications.md)。</span><span class="sxs-lookup"><span data-stu-id="a8d54-115">For more information about subscription types, see [Subscribe to Publications](subscribe-to-publications.md).</span></span>  
  
 <span data-ttu-id="a8d54-116">在下图中，发布服务器和重新发布服务器都作为其自身的本地分发服务器。</span><span class="sxs-lookup"><span data-stu-id="a8d54-116">In the following illustration, both the Publisher and the republisher are acting as their own local Distributors.</span></span> <span data-ttu-id="a8d54-117">如果将它们都设置为使用远程分发服务器，则各分发服务器需要与其发布服务器位于低速或昂贵的通信链接的同一端。</span><span class="sxs-lookup"><span data-stu-id="a8d54-117">If each were set up to use a remote Distributor, each Distributor would need to be on the same side of the slow or expensive communications link as its Publisher.</span></span> <span data-ttu-id="a8d54-118">发布服务器必须通过可靠、高速的通信链接连接到远程分发服务器。</span><span class="sxs-lookup"><span data-stu-id="a8d54-118">Publishers must be connected to remote Distributors by reliable, high-speed communications links.</span></span>  
  
 <span data-ttu-id="a8d54-119">![重新发布数据](media/repl-06a.gif "重新发布数据")</span><span class="sxs-lookup"><span data-stu-id="a8d54-119">![Republishing data](media/repl-06a.gif "Republishing data")</span></span>  
  
 <span data-ttu-id="a8d54-120">任何服务器都既可用作发布服务器又可用作订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="a8d54-120">Any server can act as both a Publisher and Subscriber.</span></span> <span data-ttu-id="a8d54-121">例如，考虑一下下面这个关系图：表的发布位于伦敦，且必须分发到美国四个不同的城市，即芝加哥、纽约、圣地亚哥和西雅图。</span><span class="sxs-lookup"><span data-stu-id="a8d54-121">For example, consider the following diagram in which a publication of a table exists in London and must be distributed to four different cities in the United States: Chicago, New York, San Diego, and Seattle.</span></span> <span data-ttu-id="a8d54-122">之所以选择位于纽约的服务器来订阅源于伦敦的已发布表，是因为纽约的站点满足下列条件：</span><span class="sxs-lookup"><span data-stu-id="a8d54-122">The server in New York is chosen to subscribe to the published table originating in London, because the New York site meets these conditions:</span></span>  
  
-   <span data-ttu-id="a8d54-123">返回伦敦的网络链接相对可靠。</span><span class="sxs-lookup"><span data-stu-id="a8d54-123">The network link back to London is relatively reliable.</span></span>  
  
-   <span data-ttu-id="a8d54-124">伦敦到纽约的通信成本可以接受。</span><span class="sxs-lookup"><span data-stu-id="a8d54-124">The London-to-New York communication costs are acceptable.</span></span>  
  
-   <span data-ttu-id="a8d54-125">从纽约到美国所有其他订阅服务器站点都有很好的网络通信线路。</span><span class="sxs-lookup"><span data-stu-id="a8d54-125">There are good network communications lines from New York to all other Subscriber sites in the United States.</span></span>  
  
     <span data-ttu-id="a8d54-126">![将数据重新发布到分散位置](media/repl-06.gif "将数据重新发布到分散位置")</span><span class="sxs-lookup"><span data-stu-id="a8d54-126">![Republishing data to dispersed locations](media/repl-06.gif "Republishing data to dispersed locations")</span></span>  
  
 <span data-ttu-id="a8d54-127">复制支持下表中显示的重新发布方案。</span><span class="sxs-lookup"><span data-stu-id="a8d54-127">Replication supports the republishing scenarios shown in the following table.</span></span>  
  
|<span data-ttu-id="a8d54-128">发布者</span><span class="sxs-lookup"><span data-stu-id="a8d54-128">Publisher</span></span>|<span data-ttu-id="a8d54-129">发布订阅服务器</span><span class="sxs-lookup"><span data-stu-id="a8d54-129">Publishing Subscriber</span></span>|<span data-ttu-id="a8d54-130">订阅者</span><span class="sxs-lookup"><span data-stu-id="a8d54-130">Subscriber</span></span>|  
|---------------|---------------------------|----------------|  
|<span data-ttu-id="a8d54-131">事务发布</span><span class="sxs-lookup"><span data-stu-id="a8d54-131">Transactional publication</span></span>|<span data-ttu-id="a8d54-132">事务订阅/事务发布</span><span class="sxs-lookup"><span data-stu-id="a8d54-132">Transactional subscription/transactional publication</span></span>|<span data-ttu-id="a8d54-133">事务订阅</span><span class="sxs-lookup"><span data-stu-id="a8d54-133">Transactional subscription</span></span>|  
|<span data-ttu-id="a8d54-134">事务发布</span><span class="sxs-lookup"><span data-stu-id="a8d54-134">Transactional publication</span></span>|<span data-ttu-id="a8d54-135">事务订阅/合并发布<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="a8d54-135">Transactional subscription/merge publication<sup>1</sup></span></span>|<span data-ttu-id="a8d54-136">合并订阅</span><span class="sxs-lookup"><span data-stu-id="a8d54-136">Merge subscription</span></span>|  
|<span data-ttu-id="a8d54-137">合并发布</span><span class="sxs-lookup"><span data-stu-id="a8d54-137">Merge publication</span></span>|<span data-ttu-id="a8d54-138">合并订阅/合并发布</span><span class="sxs-lookup"><span data-stu-id="a8d54-138">Merge subscription/merge publication</span></span>|<span data-ttu-id="a8d54-139">合并订阅</span><span class="sxs-lookup"><span data-stu-id="a8d54-139">Merge subscription</span></span>|  
|<span data-ttu-id="a8d54-140">合并发布</span><span class="sxs-lookup"><span data-stu-id="a8d54-140">Merge publication</span></span>|<span data-ttu-id="a8d54-141">合并订阅/事务发布</span><span class="sxs-lookup"><span data-stu-id="a8d54-141">Merge subscription/transactional publication</span></span>|<span data-ttu-id="a8d54-142">事务订阅</span><span class="sxs-lookup"><span data-stu-id="a8d54-142">Transactional subscription</span></span>|  
  
 <span data-ttu-id="a8d54-143"><sup>1</sup>应在 `@published_in_tran_pub` 合并发布上设置属性。</span><span class="sxs-lookup"><span data-stu-id="a8d54-143"><sup>1</sup>You should set the `@published_in_tran_pub` property on the merge publication.</span></span> <span data-ttu-id="a8d54-144">默认情况下，事务复制将订阅服务器上的表视为只读。</span><span class="sxs-lookup"><span data-stu-id="a8d54-144">By default, transactional replication expects tables at the Subscriber to be treated as read-only.</span></span> <span data-ttu-id="a8d54-145">如果合并复制对事务订阅中的表进行了数据更改，则可能发生数据无法收敛的情况。</span><span class="sxs-lookup"><span data-stu-id="a8d54-145">If merge replication makes data changes to a table in a transactional subscription, non-convergence of data can occur.</span></span> <span data-ttu-id="a8d54-146">为避免这种风险，建议您在合并发布中将所有此类表都指定为仅供下载。</span><span class="sxs-lookup"><span data-stu-id="a8d54-146">To avoid this risk, we recommend that any such table be specified as download-only in the merge publication.</span></span> <span data-ttu-id="a8d54-147">这样可以防止合并订阅服务器向表中上载数据更改。</span><span class="sxs-lookup"><span data-stu-id="a8d54-147">This prevents a merge Subscriber from uploading data changes to the table.</span></span> <span data-ttu-id="a8d54-148">有关详细信息，请参阅[使用仅下载项目优化合并复制性能](merge/optimize-merge-replication-performance-with-download-only-articles.md)。</span><span class="sxs-lookup"><span data-stu-id="a8d54-148">For more information, see [Optimize Merge Replication Performance with Download-Only Articles](merge/optimize-merge-replication-performance-with-download-only-articles.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8d54-149">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a8d54-149">See Also</span></span>  
 <span data-ttu-id="a8d54-150">[“配置分发”](configure-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="a8d54-150">[Configure Distribution](configure-distribution.md) </span></span>  
 <span data-ttu-id="a8d54-151">[发布数据和数据库对象](publish/publish-data-and-database-objects.md) </span><span class="sxs-lookup"><span data-stu-id="a8d54-151">[Publish Data and Database Objects](publish/publish-data-and-database-objects.md) </span></span>  
 <span data-ttu-id="a8d54-152">[Subscribe to Publications](subscribe-to-publications.md) </span><span class="sxs-lookup"><span data-stu-id="a8d54-152">[Subscribe to Publications](subscribe-to-publications.md) </span></span>  
 <span data-ttu-id="a8d54-153">[初始化订阅](initialize-a-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="a8d54-153">[Initialize a Subscription](initialize-a-subscription.md) </span></span>  
 [<span data-ttu-id="a8d54-154">同步数据</span><span class="sxs-lookup"><span data-stu-id="a8d54-154">Synchronize Data</span></span>](synchronize-data.md)  
  
  
