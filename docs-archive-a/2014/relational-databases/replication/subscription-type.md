---
title: 订阅类型 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.subscriptiontype.f1
ms.assetid: 9a50f588-ee45-4a87-826f-372ff0798587
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 614ff910b13706485ee9466c884243ff1c9027ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689327"
---
# <a name="subscription-type"></a><span data-ttu-id="98a43-102">订阅类型</span><span class="sxs-lookup"><span data-stu-id="98a43-102">Subscription Type</span></span>
  <span data-ttu-id="98a43-103">合并复制提供了两种订阅类型：服务器和客户端（以前的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本分别称为全局和本地）。</span><span class="sxs-lookup"><span data-stu-id="98a43-103">Merge replication offers two subscription types: server and client (referred to in previous versions of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] as global and local, respectively).</span></span> <span data-ttu-id="98a43-104">使用服务器订阅的订阅服务器可以：</span><span class="sxs-lookup"><span data-stu-id="98a43-104">Subscribers with a server subscription can:</span></span>  
  
-   <span data-ttu-id="98a43-105">将数据重新发布到其他订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="98a43-105">Republish data to other Subscribers.</span></span>  
  
-   <span data-ttu-id="98a43-106">作为备用同步伙伴。</span><span class="sxs-lookup"><span data-stu-id="98a43-106">Serve as alternate synchronization partners.</span></span>  
  
-   <span data-ttu-id="98a43-107">按照您设置的优先级解决冲突。</span><span class="sxs-lookup"><span data-stu-id="98a43-107">Resolve conflicts according to a priority you set.</span></span>  
  
 <span data-ttu-id="98a43-108">大多数订阅服务器不需要此功能，可以使用客户端订阅。</span><span class="sxs-lookup"><span data-stu-id="98a43-108">Most Subscribers do not require this functionality and can use a client subscription.</span></span> <span data-ttu-id="98a43-109">客户端订阅仍然允许进行冲突检测和解决，但不为订阅服务器分配优先级：第一个将更改提交到发布服务器的订阅服务器将在该更改引起的任意冲突中获胜。</span><span class="sxs-lookup"><span data-stu-id="98a43-109">Client subscriptions still allow conflict detection and resolution, but Subscribers are not assigned a priority: the first Subscriber to submit a change to the Publisher wins any conflicts that might arise from that change.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="98a43-110">创建订阅之后，不能更改订阅类型。</span><span class="sxs-lookup"><span data-stu-id="98a43-110">Subscription type cannot be changed after a subscription is created.</span></span>  
  
## <a name="options"></a><span data-ttu-id="98a43-111">选项</span><span class="sxs-lookup"><span data-stu-id="98a43-111">Options</span></span>  
 <span data-ttu-id="98a43-112">**订阅属性**</span><span class="sxs-lookup"><span data-stu-id="98a43-112">**Subscription properties**</span></span>  
 <span data-ttu-id="98a43-113">对于每个订阅服务器，请从 **“订阅类型”** 列的下拉列表框中选择 **“客户端”** 或 **“服务器”** 。</span><span class="sxs-lookup"><span data-stu-id="98a43-113">For each Subscriber, select **Client** or **Server** from the drop-down list box in the **Subscription Type** column.</span></span> <span data-ttu-id="98a43-114">对于使用服务器订阅的订阅服务器，请在 **“冲突解决的优先级”** 列中输入 0 和 99.99 之间的数字（数字越大，订阅服务器的优先级越高）。</span><span class="sxs-lookup"><span data-stu-id="98a43-114">For Subscribers with server subscriptions, enter a number between 0 and 99.99 in the **Priority for Conflict Resolution** column (the higher the number, the higher the priority for the Subscriber).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98a43-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="98a43-115">See Also</span></span>  
 <span data-ttu-id="98a43-116">[Create a Pull Subscription](create-a-pull-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="98a43-116">[Create a Pull Subscription](create-a-pull-subscription.md) </span></span>  
 <span data-ttu-id="98a43-117">[ssSDSFull](create-a-push-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="98a43-117">[Create a Push Subscription](create-a-push-subscription.md) </span></span>  
 [<span data-ttu-id="98a43-118">订阅发布</span><span class="sxs-lookup"><span data-stu-id="98a43-118">Subscribe to Publications</span></span>](subscribe-to-publications.md)  
  
  
