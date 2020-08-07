---
title: '&lt;AgentName&gt; 代理位置 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.agentlocation.f1
ms.assetid: dc664d80-fbe3-4586-aba8-a71fa62d14f0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7fc39541915b43abd024e1b02022f8a9e61580b2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580152"
---
# <a name="ltagentnamegt-agent-location"></a><span data-ttu-id="4d18a-102">&lt;AgentName&gt; 代理位置</span><span class="sxs-lookup"><span data-stu-id="4d18a-102">&lt;AgentName&gt; Agent Location</span></span>
  <span data-ttu-id="4d18a-103">合并代理（对于合并订阅）和分发代理（对于事务订阅和快照订阅）运行在分发服务器或订阅服务器上。</span><span class="sxs-lookup"><span data-stu-id="4d18a-103">The Merge Agent (for merge subscriptions) and the Distribution Agent (for transactional and snapshot subscriptions) run at the Distributor or at the Subscriber.</span></span> <span data-ttu-id="4d18a-104">如果代理运行在分发服务器上，则订阅称为推送订阅；如果代理运行在订阅服务器上，则订阅称为请求订阅。</span><span class="sxs-lookup"><span data-stu-id="4d18a-104">If the agent runs at the Distributor, the subscription is referred to as a push subscription; if the agent runs at the Subscriber, it is referred to as a pull subscription.</span></span> <span data-ttu-id="4d18a-105">有关推送订阅和请求订阅的详细信息，请参阅[订阅发布](subscribe-to-publications.md)。</span><span class="sxs-lookup"><span data-stu-id="4d18a-105">For more information about push and pull subscriptions, see [Subscribe to Publications](subscribe-to-publications.md).</span></span> <span data-ttu-id="4d18a-106">通过执行向导创建的所有订阅，其类型均为在向导中所选择的类型。</span><span class="sxs-lookup"><span data-stu-id="4d18a-106">All subscriptions created in this pass through the wizard will be of the selected type.</span></span> <span data-ttu-id="4d18a-107">若要创建两种类型的订阅，必须运行两次向导。</span><span class="sxs-lookup"><span data-stu-id="4d18a-107">To create subscriptions of both types, you must run the wizard twice.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4d18a-108">创建订阅之后，不能更改订阅类型。</span><span class="sxs-lookup"><span data-stu-id="4d18a-108">Subscription type cannot be changed after a subscription is created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d18a-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4d18a-109">See Also</span></span>  
 <span data-ttu-id="4d18a-110">[Create a Pull Subscription](create-a-pull-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="4d18a-110">[Create a Pull Subscription](create-a-pull-subscription.md) </span></span>  
 <span data-ttu-id="4d18a-111">[ssSDSFull](create-a-push-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="4d18a-111">[Create a Push Subscription](create-a-push-subscription.md) </span></span>  
 [<span data-ttu-id="4d18a-112">复制代理概述</span><span class="sxs-lookup"><span data-stu-id="4d18a-112">Replication Agents Overview</span></span>](agents/replication-agents-overview.md)  
  
  
