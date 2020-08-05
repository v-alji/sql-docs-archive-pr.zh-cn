---
title: MSSQL_ENG014157 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014157 error
ms.assetid: 1a0890cf-d977-43e0-a2ba-9c5ff1a8f856
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0682d740d82c995d64427f56aabce24b8a48ca65
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580690"
---
# <a name="mssql_eng014157"></a><span data-ttu-id="03f8d-102">MSSQL_ENG014157</span><span class="sxs-lookup"><span data-stu-id="03f8d-102">MSSQL_ENG014157</span></span>
    
## <a name="message-details"></a><span data-ttu-id="03f8d-103">消息详细信息</span><span class="sxs-lookup"><span data-stu-id="03f8d-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="03f8d-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="03f8d-104">Product Name</span></span>|<span data-ttu-id="03f8d-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="03f8d-105">SQL Server</span></span>|  
|<span data-ttu-id="03f8d-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="03f8d-106">Event ID</span></span>|<span data-ttu-id="03f8d-107">14157</span><span class="sxs-lookup"><span data-stu-id="03f8d-107">14157</span></span>|  
|<span data-ttu-id="03f8d-108">事件源</span><span class="sxs-lookup"><span data-stu-id="03f8d-108">Event Source</span></span>|<span data-ttu-id="03f8d-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="03f8d-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="03f8d-110">组件</span><span class="sxs-lookup"><span data-stu-id="03f8d-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="03f8d-111">符号名称</span><span class="sxs-lookup"><span data-stu-id="03f8d-111">Symbolic Name</span></span>||  
|<span data-ttu-id="03f8d-112">消息正文</span><span class="sxs-lookup"><span data-stu-id="03f8d-112">Message Text</span></span>|<span data-ttu-id="03f8d-113">由发布 '%s' 的订阅服务器 '%s' 创建的订阅已过期，且已停止。</span><span class="sxs-lookup"><span data-stu-id="03f8d-113">The subscription created by Subscriber '%s' to publication '%s' has expired and has been dropped.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="03f8d-114">说明</span><span class="sxs-lookup"><span data-stu-id="03f8d-114">Explanation</span></span>  
 <span data-ttu-id="03f8d-115">订阅服务器在指定的发布保持期内必须与发布服务器同步。</span><span class="sxs-lookup"><span data-stu-id="03f8d-115">A Subscriber must synchronize with the Publisher within the time specified in the publication retention period.</span></span> <span data-ttu-id="03f8d-116">如果订阅服务器在此期间内没有同步，则该订阅将过期。</span><span class="sxs-lookup"><span data-stu-id="03f8d-116">If a Subscriber does not synchronize within this period, the subscription expires.</span></span> <span data-ttu-id="03f8d-117">有关详细信息，请参阅 [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md)。</span><span class="sxs-lookup"><span data-stu-id="03f8d-117">For more information, see [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="03f8d-118">用户操作</span><span class="sxs-lookup"><span data-stu-id="03f8d-118">User Action</span></span>  
 <span data-ttu-id="03f8d-119">必须先重新创建和初始化订阅，订阅服务器才可以再次接收数据更改：</span><span class="sxs-lookup"><span data-stu-id="03f8d-119">The subscription must be re-created and initialized before the Subscriber can begin receiving data changes again:</span></span>  
  
-   <span data-ttu-id="03f8d-120">有关创建订阅的信息，请参阅[订阅发布](subscribe-to-publications.md)。</span><span class="sxs-lookup"><span data-stu-id="03f8d-120">For information about creating subscriptions, see [Subscribe to Publications](subscribe-to-publications.md).</span></span>  
  
-   <span data-ttu-id="03f8d-121">有关初始化订阅的信息，请参阅[初始化订阅](initialize-a-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="03f8d-121">For information about initializing subscriptions, see [Initialize a Subscription](initialize-a-subscription.md).</span></span>  
  
 <span data-ttu-id="03f8d-122">如果订阅数据库包含尚未与发布服务器同步的更改，则可以使用 [tablediff Utility](../../tools/tablediff-utility.md) 来确定发布和订阅数据库中的哪些行不同。</span><span class="sxs-lookup"><span data-stu-id="03f8d-122">If the subscription database contains changes that have not been synchronized with the Publisher, you can use the [tablediff Utility](../../tools/tablediff-utility.md) to determine which rows are different in the publication and subscription databases.</span></span>  
  
 <span data-ttu-id="03f8d-123">可以延长发布保持期来避免订阅过期。</span><span class="sxs-lookup"><span data-stu-id="03f8d-123">You can increase the publication retention period to avoid having subscriptions expire.</span></span> <span data-ttu-id="03f8d-124">请谨慎设置较高的值，因为这可能导致存储更多的数据和元数据，从而影响性能。</span><span class="sxs-lookup"><span data-stu-id="03f8d-124">Use caution in setting a high value, because this can result in more data and metadata being stored, which affects performance.</span></span> <span data-ttu-id="03f8d-125">有关详细信息，请参阅 [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md)。</span><span class="sxs-lookup"><span data-stu-id="03f8d-125">For more information, see [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03f8d-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="03f8d-126">See Also</span></span>  
 [<span data-ttu-id="03f8d-127">错误和事件参考（复制）</span><span class="sxs-lookup"><span data-stu-id="03f8d-127">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
